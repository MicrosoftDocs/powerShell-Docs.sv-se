---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSnapin
ms.openlocfilehash: 472a4c8fbb9eb0d37827aff4fcfd6bb9a67f4743
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263589"
---
# Get-PSSnapin

## SAMMANFATTNING
Hämtar snapin-moduler för Windows PowerShell på datorn.

## SYNTAX

```
Get-PSSnapin [[-Name] <String[]>] [-Registered] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en get-PSSnapin** hämtar Windows PowerShell-snapin-modulerna som har lagts till i den aktuella sessionen eller som har registrerats i systemet.
Denna cmdlet listar snapin-modulerna i den ordning som de identifieras.

**Get-PSSnapin** hämtar bara registrerade snapin-moduler. Om du vill registrera en Windows PowerShell-snapin-modul använder du InstallUtil-verktyget som ingår i Microsoft .NET Framework 2,0.
Mer information finns i [så här registrerar du cmdlets, providers och värd program](https://go.microsoft.com/fwlink/?LinkID=143619) i MSDN-biblioteket.

Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som ingår i Windows PowerShell i moduler.
Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul (PSSnapin).
Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.
Moduler importeras automatiskt vid första användningen och du kan använda Import-Module-cmdlet för att importera dem.

## EXEMPEL

### Exempel 1: Hämta snapin-moduler som är inlästa för tillfället

```
PS C:\> Get-PSSnapIn
```

Det här kommandot hämtar Windows PowerShell-snapin-modulerna som för närvarande läses in i sessionen.
Detta inkluderar snapin-modulerna som installeras med Windows PowerShell och de som har lagts till i sessionen.

### Exempel 2: Hämta snapin-moduler som har registrerats

```
PS C:\> get-PSSnapIn -Registered
```

Det här kommandot hämtar Windows PowerShell-snapin-modulerna som har registrerats på datorn, inklusive de som redan har lagts till i sessionen.
Utdata inkluderar inte snapin-moduler som installeras med Windows PowerShell eller Windows PowerShell-snapin-modulen dll: er (Dynamic-Link Libraries) som ännu inte har registrerats i systemet.

### Exempel 3: hämta aktuella snapin-moduler som matchar en sträng

```
PS C:\> Get-PSSnapIn -Name smp*
```

Det här kommandot hämtar Windows PowerShell-snapin-modulerna i den aktuella sessionen med namn som börjar med SMP.

## PARAMETRAR

### -Name
Anger en matris med namn på snapin-modulen.
Denna cmdlet hämtar bara de angivna Windows PowerShell-snapin-modulerna. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Registrerad
Anger att den här cmdlet: en hämtar Windows PowerShell-snapin-modulerna som har registrerats i systemet även om de ännu inte har lagts till i sessionen.

Snapin-modulerna som installeras med Windows PowerShell visas inte i den här listan.

Utan den här parametern hämtar **Get-PSSnapin** de Windows PowerShell-snapin-moduler som har lagts till i sessionen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSSnapInInfo
Get-PSSnapin returnerar ett objekt för varje snapin-modul som det får.

## ANTECKNINGAR

* Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med Windows PowerShell i moduler. I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av Windows PowerShell är huvud kommandona förpackade i snapin-moduler ( **PSSnapin** ). Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul. Fjärrsessioner, till exempel de som startas av New-PSSession-cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.

  Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](https://msdn.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.createdefault2) i MSDN-biblioteket.

## RELATERADE LÄNKAR

[Add-PSSnapin](Add-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
