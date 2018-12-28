---
title: WS-Management-fjärrkommunikation (WSMan) i PowerShell Core
description: Fjärrkommunikation i PowerShell Core med WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406018"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a>WS-Management-fjärrkommunikation (WSMan) i PowerShell Core

## <a name="instructions-to-create-a-remoting-endpoint"></a>Instruktioner för att skapa en slutpunkt för fjärrkommunikation

PowerShell Core-paket för Windows innehåller ett plugin-programmet WinRM (`pwrshplugin.dll`) och ett installationsskript (`Install-PowerShellRemoting.ps1`) i `$PSHome`.
De här filerna aktivera PowerShell för att acceptera inkommande fjärranslutningar i PowerShell när dess slutpunkt har angetts.

### <a name="motivation"></a>Motivation

En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession`.
Användaren måste skapa en slutpunkt för WinRM-fjärrkommunikation för att aktivera den för att acceptera inkommande fjärranslutningar med PowerShell.
Detta är en explicit opt i scenariot där användaren kör Install-PowerShellRemoting.ps1 skapa WinRM-slutpunkt.
Installationsskriptet är en kortsiktig lösning tills vi lägger till ytterligare funktioner `Enable-PSRemoting` att utföra samma åtgärd.
Mer information finns på problemet [#1193](https://github.com/PowerShell/PowerShell/issues/1193).

### <a name="script-actions"></a>Skriptåtgärder

Skriptet

1. Skapar en katalog för plugin-programmet i %windir%\System32\PowerShell
1. Kopierar pwrshplugin.dll dit
1. Genererar en konfigurationsfil
1. Registrerar som plugin-programmet med WinRM

### <a name="registration"></a>Registrering

Skriptet måste köras i en behörighet på PowerShell-session och körs i två lägen.

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a>Körs av instansen av PowerShell som den registreras

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a>Körs av en annan instans av PowerShell för den instans som den registreras

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

Till exempel:

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

**OBS:** Fjärrkommunikation registrering skriptet startar om WinRM, så att alla befintliga PSRP sessioner avslutas omedelbart när skriptet har körts. Om under en fjärrsession, kommer detta avslutar anslutningen.

## <a name="how-to-connect-to-the-new-endpoint"></a>Hur du ansluter till den nya slutpunkten

Skapa en PowerShell-session till den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"`. Använd antingen när du ansluter till PowerShell-instansen i exemplet ovan:

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anger `-ConfigurationName` rikta in dig på PowerShell standardslutpunkten `microsoft.powershell`.