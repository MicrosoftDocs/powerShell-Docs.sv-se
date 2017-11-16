---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Använda variabler för att lagra objekt"
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a>Använda variabler för att lagra objekt
PowerShell fungerar med objekt. PowerShell kan du skapa variabler som i stort sett heter objekt att bevara utdata för senare användning. Om du har använt för att arbeta med variabler i andra tankar Kom ihåg att PowerShell variabler objekt, inte text.

Variabler anges alltid med det första tecknet $ och kan innehålla alfanumeriska tecken eller understreck i sina namn.

### <a name="creating-a-variable"></a>Skapa en variabel
Du kan skapa en variabel genom att ange ett giltigt namn på variabel:

```
PS> $loc
PS>
```

Inga resultat returneras eftersom **$loc** saknar ett värde. Du kan skapa en variabel och tilldela den ett värde i samma steg. PowerShell skapar endast variabeln om det inte finns; Annars tilldelar det angivna värdet till en befintlig variabel. Att lagra din aktuella plats i variabeln **$loc**, typ:

```
$loc = Get-Location
```

Det finns inga utdata som visas när du anger det här kommandot eftersom utdata skickas till $ lagerst. I PowerShell är visas utdata en sidoeffekt av det faktum att informationen som inte annars dirigeras, skickas alltid till skärmen. Att skriva $loc visar din aktuella plats:

```
PS> $loc

Path
----
C:\temp
```

Du kan använda **Get-medlemmen** att visa information om innehållet för variabler. Skicka $loc till Get-medlemmen visar att det är en **PathInfo** objektet, precis som utdata från Get-plats:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Ändra variabler
PowerShell innehåller flera kommandon för att ändra variabler. Du kan se en fullständig lista i ett läsbart formulär genom att skriva:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Förutom de variabler som du skapar i den aktuella PowerShell-sessionen finns flera systemdefinierade variabler. Du kan använda den **ta bort variabeln** cmdlet för att rensa alla variabler som inte kontrolleras av PowerShell. Skriv följande kommando för att rensa alla variabler:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Detta genererar tillfrågas om du ser nedan.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Om du kör den **Get-Variable** cmdlet, visas de återstående PowerShell-variablerna. Eftersom det inte finns en variabel PowerShell-enhet, kan du också visa alla PowerShell variabler genom att skriva:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Använda Cmd.exe variabler
Även om PowerShell inte är Cmd.exe körs i en miljö med kommandot shell och kan använda samma variabler som är tillgängliga i alla miljöer i Windows. Dessa variabler är tillgängliga via en enhet med namnet **env**:. Du kan visa dessa variabler genom att skriva:

```
Get-ChildItem env:
```

Även om standard variabel cmdlets inte är avsedda att fungera med **env:** variabler, du kan fortfarande använda dem genom att ange den **env:** prefix. Till exempel om du vill se rotkatalogen operativsystem du kan använda kommandotolken- **% SystemRoot %** variabel från i PowerShell genom att skriva:

```
PS> $env:SystemRoot
C:\WINDOWS
```

Du kan också skapa och ändra miljövariabler i PowerShell. Miljövariabler som nås från Windows PowerShell stämmer överens med de vanliga reglerna för miljövariabler någon annanstans i Windows.

