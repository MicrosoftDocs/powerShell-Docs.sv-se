---
ms.date: 08/27/2018
keywords: PowerShell cmdlet
title: Använd variabler för att lagra objekt
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: d166ec58dc658c1b134030c9a9592249ee40d4f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086552"
---
# <a name="using-variables-to-store-objects"></a>Använd variabler för att lagra objekt

PowerShell fungerar med objekt. PowerShell kan du skapa objekt som kallas variabler.
Variabelnamn kan innehålla understreck och alfanumeriska tecken. När den används i PowerShell, en variabel alltid anges med hjälp av den \$ tecken följt av namnet på variabeln.

## <a name="creating-a-variable"></a>Skapa en variabel

Du kan skapa en variabel genom att skriva ett giltigt variabelnamn:

```
PS> $loc
PS>
```

Det här exemplet returnerar inga resultat eftersom `$loc` saknar ett värde. Du kan skapa en variabel och tilldela den ett värde i samma steg. PowerShell skapar endast variabeln om det inte finns.
Annars tilldelar det angivna värdet till en befintlig variabel. I följande exempel lagrar den aktuella platsen i variabeln `$loc`:

```powershell
$loc = Get-Location
```

PowerShell visar inga utdata när du skriver in det här kommandot. PowerShell skickar utdata från Get-plats till `$loc`. I PowerShell skickas data som inte är tilldelade eller omdirigeras till skärmen. Att skriva `$loc` visar din aktuella plats:

```
PS> $loc

Path
----
C:\temp
```

Du kan använda `Get-Member` att visa information om innehållet för variabler. `Get-Member` Visar att `$loc` är en **PathInfo** objekt, precis som utdata från `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Ändra variabler

PowerShell innehåller flera kommandon för att ändra variabler. Du kan se en fullständig lista i form av en läsbar genom att skriva:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell skapar även flera systemdefinierade variabler. Du kan använda den `Remove-Variable` cmdlet för att ta bort variabler som inte kontrolleras av PowerShell, från den aktuella sessionen. Skriv följande kommando för att rensa alla variabler:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

När du har kört kommandot föregående den `Get-Variable` cmdlet visar systemvariabler PowerShell.

PowerShell skapar även en variabel enhet. Använd följande exempel för att visa alla PowerShell-variabler med hjälp av variabeln drive:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Använda cmd.exe variabler

PowerShell kan använda de samma miljövariablerna som är tillgängliga för alla Windows-processen, inklusive **cmd.exe**. Dessa variabler är tillgängliga via en enhet med namnet `env:`. Du kan visa dessa variabler genom att skriva följande kommando:

```powershell
Get-ChildItem env:
```

Standard `*-Variable` cmdletar är inte avsett att fungera med miljövariabler. Miljövariabler kan nås med hjälp av den `env:` enhetsprefix. Till exempel den **% SystemRoot %** variabel i **cmd.exe** innehåller katalognamnet för operativsystemets rot. I PowerShell kan du använda `$env:SystemRoot` att få åtkomst till samma värde.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Du kan också skapa och ändra miljövariabler i PowerShell. Miljövariabler i PowerShell följer samma regler för miljövariabler används någon annanstans i operativsystemet. I följande exempel skapas en ny miljövariabel:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Även om inte krävs, är det vanligt att miljövariabelnamn att använda enbart versaler.
