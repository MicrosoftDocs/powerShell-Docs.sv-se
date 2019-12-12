---
ms.date: 08/27/2018
keywords: PowerShell, cmdlet
title: Använd variabler för att lagra objekt
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030366"
---
# <a name="using-variables-to-store-objects"></a>Använd variabler för att lagra objekt

PowerShell fungerar med objekt. Med PowerShell kan du skapa namngivna objekt som kallas variabler.
Variabel namn kan innehålla under streck och alfanumeriska tecken. När det används i PowerShell anges alltid en variabel med hjälp av \$-tecknen följt av variabel namnet.

## <a name="creating-a-variable"></a>Skapa en variabel

Du kan skapa en variabel genom att skriva ett giltigt variabel namn:

```
PS> $loc
PS>
```

Det här exemplet returnerar inget resultat eftersom `$loc` inte har något värde. Du kan skapa en variabel och tilldela den ett värde i samma steg. PowerShell skapar bara variabeln om den inte finns.
Annars tilldelar den den befintliga variabeln det angivna värdet. I följande exempel lagras den aktuella platsen i variabeln `$loc`:

```powershell
$loc = Get-Location
```

PowerShell visar inga utdata när du skriver det här kommandot. PowerShell skickar utdata från get-location till `$loc`. I PowerShell skickas data som inte är tilldelade eller omdirigerade till skärmen. När du skriver `$loc` visas din aktuella plats:

```
PS> $loc

Path
----
C:\temp
```

Du kan använda `Get-Member` för att visa information om innehållet i variabler. `Get-Member` visar att `$loc` är ett **PathInfo** -objekt, precis som utdata från `Get-Location`:

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

## <a name="manipulating-variables"></a>Manipulera variabler

PowerShell innehåller flera kommandon för att manipulera variabler. Du kan se en fullständig lista i läsbart format genom att skriva:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell skapar också flera systemdefinierade variabler. Du kan använda `Remove-Variable`-cmdlet för att ta bort variabler, som inte styrs av PowerShell, från den aktuella sessionen. Skriv följande kommando för att rensa alla variabler:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

När du har kört föregående kommando visar `Get-Variable`-cmdleten PowerShell-systemvariablerna.

PowerShell skapar också en variabel enhet. Använd följande exempel för att visa alla PowerShell-variabler med variabeln drive:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Använda CMD. exe-variabler

PowerShell kan använda samma miljövariabler som är tillgängliga för alla Windows-processer, inklusive **cmd. exe**. Dessa variabler exponeras via en enhet med namnet `env:`. Du kan visa dessa variabler genom att skriva följande kommando:

```powershell
Get-ChildItem env:
```

Standard-`*-Variable`-cmdletarna är inte utformade för att fungera med miljövariabler. Miljövariabler nås med hjälp av `env:`-enhetens prefix. Variabeln **% systemroot%** i **cmd. exe** innehåller till exempel operativ systemets rot Katalog namn. I PowerShell använder du `$env:SystemRoot` för att få åtkomst till samma värde.

```
PS> $env:SystemRoot
C:\WINDOWS
```

Du kan också skapa och ändra miljövariabler i PowerShell. Miljövariabler i PowerShell följer samma regler för miljövariabler som används någon annan stans i operativ systemet. I följande exempel skapas en ny miljö variabel:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Även om detta inte krävs är det vanligt att namn på miljö variabel används för alla versaler.
