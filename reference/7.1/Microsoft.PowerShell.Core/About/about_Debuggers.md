---
description: Beskriver PowerShell-felsökaren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 6765c33e4508e19dfca7f291f8452f1bb4730747
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271112"
---
# <a name="about-debuggers"></a>Om fel söknings program

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver PowerShell-felsökaren.

## <a name="long-description"></a>LÅNG BESKRIVNING

Fel sökning är en process för att undersöka ett skript när det körs för att identifiera och korrigera fel i skript instruktionerna. PowerShell-felsökaren kan hjälpa dig att undersöka och identifiera fel och ineffektiv i skript, funktioner, kommandon, DSC-konfigurationer (Desired State Configuration) eller uttryck.

Från och med PowerShell 5,0 har PowerShell-felsökaren uppdaterats för att felsöka skript, funktioner, kommandon, konfigurationer eller uttryck som körs i antingen-konsolen eller Windows PowerShell ISE på fjärrdatorer. Du kan köra `Enter-PSSession` för att starta en interaktiv fjärran sluten PowerShell-session där du kan ange Bryt punkter och felsöka skriptfiler och kommandon på fjärrdatorn. `Enter-PSSession` funktionen har uppdaterats så att du kan återansluta till och ange en frånkopplad session som kör ett skript eller kommando på en fjärrdator. Om skriptet som körs träffar en Bryt punkt startar klient sessionen automatiskt fel söknings programmet. Om den frånkopplade sessionen som kör ett skript redan har nått en Bryt punkt och har stoppats vid Bryt punkten, `Enter-PSSession` startar automatiskt kommando rads fel söknings programmet när du återansluter till sessionen.

Du kan använda funktionerna i PowerShell-felsökaren för att undersöka ett PowerShell-skript, funktion, kommando eller uttryck när den körs. PowerShell-felsökaren innehåller en uppsättning cmdletar som gör att du kan ange Bryt punkter, hantera Bryt punkter och Visa anrops stacken.

## <a name="debugger-cmdlets"></a>Fel söknings-cmdletar

PowerShell-felsökaren innehåller följande uppsättning cmdletar:

- `Set-PSBreakpoint`: Anger Bryt punkter för linjer, variabler och kommandon.
- `Get-PSBreakpoint`: Hämtar Bryt punkter i den aktuella sessionen.
- `Disable-PSBreakpoint`: Stänger av Bryt punkter i den aktuella sessionen.
- `Enable-PSBreakpoint`: Aktiverar Bryt punkter i den aktuella sessionen igen.
- `Remove-PSBreakpoint`: Tar bort Bryt punkter från den aktuella sessionen.
- `Get-PSCallStack`: Visar den aktuella anrops stacken.

## <a name="starting-and-stopping-the-debugger"></a>Starta och stoppa fel söknings programmet

Ange en eller flera Bryt punkter för att starta fel söknings programmet. Kör sedan skriptet, kommandot eller funktionen som du vill felsöka.

När du når en Bryt punkt, stoppas körningen och kontroll sker över till fel söknings programmet.

Stoppa fel söknings programmet genom att köra skriptet, kommandot eller funktionen tills det är klart. Eller Skriv `stop` eller `t` .

### <a name="debugger-commands"></a>Fel söknings kommandon

När du använder fel sökaren i PowerShell-konsolen, använder du följande kommandon för att kontrol lera körningen. I Windows PowerShell ISE använder du kommandon på fel söknings menyn.

Obs! information om hur du använder fel sökaren i andra värd program finns i dokumentationen för värd programmet.

- `s`, `StepInto` : Kör nästa instruktion och stoppar sedan.

- `v`, `StepOver` : Kör nästa instruktion, men hoppar över funktioner och anrop. De överhoppade instruktionerna körs, men är inte stegvisa.

- `Ctrl+Break`: (Break all i ISE) bryts i ett skript som körs antingen i PowerShell-konsolen eller Windows PowerShell ISE. Observera att <kbd>CTRL</kbd> + <kbd>Break</kbd> i Windows PowerShell 2,0, 3,0 och 4,0 stänger programmet. Bryt alla arbeten på både lokala och fjärranslutna skript som körs interaktivt.

- `o`, `StepOut` : Steg ut ur den aktuella funktionen, upp till en nivå om den är kapslad. Om den finns i huvud texten fortsätter den till slutet eller nästa Bryt punkt. De överhoppade instruktionerna körs, men är inte stegvisa.

- `c`, `Continue` : Fortsätter att köras tills skriptet har slutförts eller tills nästa Bryt punkt har nåtts. De överhoppade instruktionerna körs, men är inte stegvisa.

- `l`, `List` : Visar den del av skriptet som körs. Som standard visas den aktuella raden, fem föregående rader och 10 efterföljande rader.
  Tryck på RETUR för att fortsätta att lista skriptet.

- `l <m>`, `List` : Visar 16 rader i skriptet som börjar med rad numret som anges av `<m>` .

- `l <m> <n>`, `List` : Visar `<n>` rader i skriptet, som börjar med rad numret som anges av `<m>` .

- `q`, `Stop` , `Exit` : Stoppar körningen av skriptet och avslutar fel söknings programmet. Om du felsöker ett jobb genom att köra `Debug-Job` cmdleten `Exit` kopplar kommandot av fel söknings programmet och gör att jobbet kan fortsätta att köras.

- `k`, `Get-PsCallStack` : Visar den aktuella anrops stacken.

- `<Enter>`: Upprepar det senaste kommandot om det var steg, StepOver (v) eller List (l). Annars representerar en skicka-åtgärd.

- `?`, `h` : Visar hjälp om fel söknings kommandot.

Om du vill avsluta fel söknings programmet kan du använda stop (q).

Från och med PowerShell 5,0 kan du köra Exit-kommandot för att avsluta en kapslad felsökningssession som du startade genom att köra antingen `Debug-Job` eller `Debug-Runspace` .

Genom att använda de här fel söknings kommandona kan du köra ett skript, stoppa en viss angelägenhet, undersöka värdena för variabler och systemets tillstånd och fortsätta köra skriptet tills du har identifierat ett problem.

Obs! Om du stegar i en instruktion med en omdirigerings Operator, t. ex. ">", PowerShell fel söknings stegen över alla återstående instruktioner i skriptet.

Visar värdena för skript-variabler

Medan du är i fel söknings programmet kan du också ange kommandon, Visa värdet för variabler, använda cmdlets och köra skript på kommando raden.

Du kan visa det aktuella värdet för alla variabler i skriptet som felsöks, förutom följande automatiska variabler:

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

Om du försöker visa värdet för någon av dessa variabler får du värdet för den variabeln för i en intern pipeline som fel sökaren använder, inte värdet för variabeln i skriptet.

Om du vill visa värdet för de variabler som ska felsökas i skriptet, tilldelar du värdet för den automatiska variabeln till en ny variabel i skriptet. Sedan kan du Visa värdet för den nya variabeln.

Exempel:

```powershell
$scriptArgs = $Args
$scriptArgs
```

I exemplet i det här avsnittet `$MyInvocation` omtilldelas värdet för variabeln enligt följande:

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>Fel söknings miljön

När du når en Bryt punkt anger du fel söknings miljön. Kommando tolken ändras så att den börjar med "[DBG]:".

Mer information om hur du anpassar meddelandet finns i [about_Prompts](about_prompts.md).

I vissa värd program, t. ex. PowerShell-konsolen, (men inte i Windows PowerShell Integrated Scripting Environment [ISE]) öppnas en kapslad prompt för fel sökning. Du kan identifiera den kapslade frågan genom att upprepa större än-tecken (ASCII 62) som visas i kommando tolken.

Följande är till exempel standard fel söknings frågan i PowerShell-konsolen:

```
[DBG]: PS (get-location)>>>
```

Du kan hitta kapslings nivån genom att använda den `$NestedPromptLevel` automatiska variabeln.

Dessutom definieras en automatisk variabel, `$PSDebugContext` , i det lokala omfånget. Du kan använda `$PsDebugContext` variabeln för att avgöra om du befinner dig i fel söknings programmet.

Ett exempel:

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

Du kan använda värdet för `$PSDebugContext` variabeln i fel sökningen.

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>Fel sökning och omfång

Om du bryter ned i fel söknings programmet ändras inte omfattningen som du arbetar i, men när du når en Bryt punkt i ett skript, flyttas du till skript omfånget. Skript omfånget är underordnat det omfång i vilket du körde fel söknings programmet.

Om du vill hitta variabler och alias som har definierats i skript omfånget använder du omfattnings parametern `Get-Alias` för `Get-Variable` cmdletarna eller.

Följande kommando hämtar till exempel variablerna i den lokala (skript) omfattningen:

```powershell
Get-Variable -scope 0
```

Du kan förkorta kommandot som:

```powershell
gv -s 0
```

Det här är ett användbart sätt att bara se de variabler som du har definierat i skriptet och som du definierade vid fel sökning.

Fel sökning på kommando raden

När du anger en variabel Bryt punkt eller en kommando Bryt punkt kan du bara ange Bryt punkten i en skript fil. Som standard anges Bryt punkten för allt som körs i den aktuella sessionen.

Om du till exempel ställer in en Bryt punkt på `$name` variabeln, bryts fel söknings verktyget på valfri `$name` variabel i skript, kommando, funktion, skript-cmdlet eller uttryck som du kör tills du inaktiverar eller tar bort Bryt punkten.

På så sätt kan du felsöka skript i en mer realistisk kontext där de kan påverkas av funktioner, variabler och andra skript i sessionen och i användarens profil.

Rad Bryt punkter är specifika för skriptfiler, så de anges bara i skriptfiler.

## <a name="debugging-functions"></a>Fel söknings funktioner

När du anger en Bryt punkt för en funktion som har `Begin` , `Process` , och `End` avsnitt, bryts fel söknings verktyget på den första raden i varje avsnitt.

Ett exempel:

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a>Felsöka fjärrskript

Från och med PowerShell 5,0 kan du köra PowerShell-felsökning i en fjärrsession, antingen i-konsolen eller Windows PowerShell ISE.
`Enter-PSSession` funktionen har uppdaterats så att du kan återansluta till och ange en frånkopplad session som körs på en fjärrdator och som kör ett skript. Om skriptet som körs träffar en Bryt punkt startar klient sessionen automatiskt fel söknings programmet.

Följande är ett exempel som visar hur det fungerar, med Bryt punkter som anges i ett skript på rad 6, 11, 22 och 25. Observera att i exemplet, när fel söknings programmet startar, finns det två identifierande prompter: namnet på den dator där sessionen körs och DBG-prompten där du vet att du är i fel söknings läge.

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a>Exempel

Det här test skriptet identifierar operativ systemets version och visar ett system-lämpligt meddelande. Den innehåller en funktion, ett funktions anrop och en variabel.

Följande kommando visar innehållet i test skript filen:

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

Starta genom att ange en Bryt punkt i en orienterings punkt i skriptet, till exempel en linje, ett kommando, en variabel eller en funktion.

Börja med att skapa en rad Bryt punkt på den första raden i Test.ps1-skriptet i den aktuella katalogen.

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

Du kan förkorta det här kommandot som:

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

Kommandot returnerar ett rad brytnings objekt ( **system. Management. Automation. LineBreakpoint** ).

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

Starta nu skriptet.

```powershell
PS C:\ps-test> .\test.ps1
```

När skriptet når den första Bryt punkten, anger Bryt punkts meddelandet att fel söknings programmet är aktivt. Den beskriver Bryt punkten och för hands versionerna av den första raden i skriptet, som är en funktions deklaration. Kommando tolken ändras också för att indikera att fel söknings programmet har kontroll.

För hands versions raden ingår skript namnet och rad numret för det förvisade kommandot.

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

Använd steg-kommandona för att köra den första instruktionen i skriptet och för att förhandsgranska nästa instruktion. I nästa instruktion används den `$MyInvocation` automatiska variabeln för att ange värdet för `$scriptName` variabeln till sökvägen och fil namnet för skript filen.

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

`$scriptName`Variabeln är nu inte ifylld, men du kan kontrol lera värdet för variabeln genom att visa dess värde. I det här fallet är värdet `$null` .

```powershell
DBG> $scriptname
# DBG>
```

Använd ett annat steg för att köra den aktuella instruktionen och för att förhandsgranska nästa instruktion i skriptet. Next-instruktionen anropar funktionen PsVersion.

```powershell
DBG> s
test.ps1:12  psversion
```

I det här läget `$scriptName` fylls variabeln i, men du verifierar värdet för variabeln genom att visa dess värde. I det här fallet anges värdet för skript Sök vägen.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

Använd ett annat steg-kommando för att köra funktions anropet. Tryck på RETUR eller skriv "s" för steg.

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

Fel söknings meddelandet innehåller en förhands granskning av instruktionen i funktionen. Om du vill köra den här instruktionen och för att förhandsgranska nästa instruktion i funktionen kan du använda ett `Step` kommando. Men i det här fallet använder du ett utgångs kommando (o). Körningen av funktionen slutförs (såvida den inte når en Bryt punkt) och steg till nästa instruktion i skriptet.

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

Eftersom vi är på den sista instruktionen i skriptet, har steget, steget och kommandot Continue samma resultat. I det här fallet använder du stega (o).

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

Kommandot stega kör det sista kommandot. Standard kommando tolken anger att fel söknings programmet har avslutat och returnerat kontroll till kommando processorn.

Kör nu fel söknings programmet igen. Ta först bort den aktuella Bryt punkten genom att använda `Get-PsBreakpoint` `Remove-PsBreakpoint` cmdletarna och. (Om du tror att du kan återanvända Bryt punkten använder du `Disable-PsBreakpoint` cmdleten i stället för `Remove-PsBreakpoint` .)

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

Du kan förkorta det här kommandot som:

```powershell
PS C:\ps-test> gbp | rbp
```

Eller kör kommandot genom att skriva en funktion, till exempel följande funktion:

```powershell
function delbr { gbp | rbp }
```

Nu ska du skapa en Bryt punkt för `$scriptname` variabeln.

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

Du kan förkorta kommandot som:

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

Starta nu skriptet. Skriptet når den variabla Bryt punkten. Standard läget är Write, så körningen stoppas precis innan instruktionen som ändrar värdet för variabeln.

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

Visar det aktuella värdet för `$scriptName` variabeln, som är `$null` .

```powershell
DBG> $scriptName
# DBG>
```

Använd ett eller flera steg för att köra instruktionen som fyller på variabeln.
Sedan visar du det nya värdet för `$scriptName` variabeln.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

Next-instruktionen är ett anrop till funktionen PsVersion. Om du vill hoppa över funktionen men ändå köra den, använder du ett StepOver-kommando (v). Om du redan har använt funktionen StepOver är det inte effektivt. Funktions anropet visas, men det körs inte.

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

StepOver-kommandot kör funktionen och för hands Grans kar nästa instruktion i skriptet som skriver ut den sista raden.

Använd ett stopp kommando (t) för att avsluta fel söknings programmet. Kommando tolken återgår till standard kommando tolken.

```powershell
C:\ps-test>
```

Om du vill ta bort Bryt punkterna använder `Get-PsBreakpoint` du `Remove-PsBreakpoint` cmdletarna och.

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

Skapa en ny kommando Bryt punkt för funktionen PsVersion.

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

Du kan förkorta det här kommandot för att:

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

Kör nu skriptet.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

Skriptet når Bryt punkten vid funktions anropet. I det här läget har funktionen inte anropats än. Det ger dig möjlighet att använda åtgärds parametern för `Set-PSBreakpoint` för att ange villkor för körning av Bryt punkten eller för att utföra förberedande eller diagnostiska uppgifter, till exempel starta en logg eller anropa ett diagnostik-eller säkerhets skript.

Ange en åtgärd genom att använda ett Continue-kommando (c) för att avsluta skriptet och ett `Remove-PsBreakpoint` kommando för att ta bort den aktuella Bryt punkten. (Bryt punkter är skrivskyddade, så du kan inte lägga till en åtgärd i den aktuella Bryt punkten.)

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

Nu skapar du en ny kommando Bryt punkt med en åtgärd. Följande kommando anger en kommando Bryt punkt med en åtgärd som loggar värdet för `$scriptName` variabeln när funktionen anropas. Eftersom Break-nyckelordet inte används i åtgärden stoppas inte körningen. ("Bakticket (") är ett linje fortsättnings kort.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

Du kan också lägga till åtgärder som anger villkor för Bryt punkten. I följande kommando körs kommando Bryt punkten endast om körnings principen är inställd på RemoteSigned, den mest restriktiva principen som fortfarande tillåter att du kör skript. ("Bakticket (") är det fortsättnings tecknen.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

Nyckelordet Break i åtgärden styr fel söknings verktyget att köra Bryt punkten.
Du kan också använda nyckelordet Continue för att direkt köra fel söknings programmet utan att behöva bryta. Eftersom nyckelordet default är Continue måste du ange Break för att stoppa körningen.

Kör nu skriptet.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

Eftersom körnings principen är inställd på **RemoteSigned** , stoppas körningen vid funktions anropet.

I det här läget kanske du vill kontrol lera anrops stacken. Använd `Get-PsCallStack` cmdleten eller `Get-PsCallStack` fel söknings kommandot (k). Följande kommando hämtar den aktuella anrops stacken.

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

Det här exemplet visar bara några av många sätt att använda PowerShell-felsökaren.

Om du vill ha mer information om fel söknings-cmdletar skriver du följande kommando:

```powershell
help <cmdlet-name> -full
```

Skriv till exempel:

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>Andra fel söknings funktioner i PowerShell

Förutom PowerShell-felsökaren innehåller PowerShell flera andra funktioner som du kan använda för att felsöka skript och funktioner.

- Windows PowerShell ISE innehåller en interaktiv grafisk fel sökare. Om du vill ha mer information startar du Windows PowerShell ISE och trycker på F1.

- `Set-PSDebug`Cmdleten erbjuder mycket grundläggande skript fel söknings funktioner, inklusive steging och spårning.

- Använd `Set-StrictMode` cmdleten för att identifiera referenser till oinitierade variabler, referera till obefintliga egenskaper för ett objekt och för att visa syntaxen som inte är giltig.

- Lägg till diagnostiska uttryck i ett skript, till exempel instruktioner som visar värdet för variabler, instruktioner som läser ininformation från kommando raden eller instruktioner som rapporterar den aktuella instruktionen. Använd de cmdlets som innehåller Skriv verbet för uppgiften, till exempel, `Write-Host` , `Write-Debug` `Write-Warning` och `Write-Verbose` .

## <a name="see-also"></a>SE ÄVEN

- [Disable-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [Aktivera – PsBreakpoint](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [Get-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get-PsCallStack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [Remove-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Skriv-debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Skriv-verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

