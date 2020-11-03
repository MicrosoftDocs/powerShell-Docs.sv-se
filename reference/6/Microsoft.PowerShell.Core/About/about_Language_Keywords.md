---
description: Beskriver nyckelorden i PowerShell-skript språket.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_language_keywords?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Language_Keywords
ms.openlocfilehash: 5e624feacd63bf4be4af4b31ae9879c3ab2e54c0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270681"
---
# <a name="about-language-keywords"></a>Om språk nyckelord

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver nyckelorden i PowerShell-skript språket.

## <a name="long-description"></a>LÅNG BESKRIVNING

PowerShell har följande språk nyckelord. Mer information finns i avsnittet om för nyckelordet och den information som följer efter tabellen.

Följt     | Referens
---         | ---
Börja       | [about_Functions](about_Functions.md) [about_Functions_Advanced](about_Functions_Advanced.md)
Bryt ned       | [about_Break](about_Break.md) [about_Trap](about_Trap.md)
Dokumentation       | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Klass       | [about_Classes](about_Classes.md)
Fortsätt    | [about_Continue](about_Continue.md) [about_Trap](about_Trap.md)
Data        | [about_Data_Sections](about_Data_Sections.md)
Definierar      | Reserverad för framtida användning
Gör följande          | [about_Do](about_Do.md) [about_While](about_While.md)
DynamicParam| [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)
Tilläggs        | [about_If](about_If.md)
ElseIf      | [about_If](about_If.md)
Slut         | [about_Functions](about_Functions.md) [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Enum        | [about_Enum](about_Enum.md)
Avsluta        | [Beskrivs i det här avsnittet](#exit)
Filtrera      | [about_Functions](about_Functions.md)
Utväg     | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
För         | [about_For](about_For.md)
ForEach     | [about_ForEach](about_ForEach.md)
Från        | Reserverad för framtida användning
Funktion    | [about_Functions](about_Functions.md) [about_Functions_Advanced](about_Functions_Advanced.md)
Dold      | [about_Hidden](about_Hidden.md)
Om          | [about_If](about_If.md)
I          | [about_ForEach](about_ForEach.md)
Param       | [about_Functions](about_Functions.md)
Process     | [about_Functions](about_Functions.md) [about_Functions_Advanced](about_Functions_Advanced.md)
Returrelaterade      | [about_Return](about_Return.md)
Statisk      | [about_Classes](about_Classes.md)
Switch      | [about_Switch](about_Switch.md)
Genereras       | [about_Throw](about_Throw.md) [about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)
Väll        | [about_Trap](about_Trap.md) [about_Break](about_Break.md) [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Testa         | [about_Try_Catch_Finally](about_Try_Catch_Finally.md)
Tills       | [about_Do](about_Do.md)
Använda       | [about_Using](about_Using.md) [about_Classes](about_Classes.md)
Var         | Reserverad för framtida användning
Tiden       | [about_While](about_While.md) [about_Do](about_Do.md)

Språk nyckelord

### <a name="begin"></a>Börja

Anger en del av bröd texten i en funktion, tillsammans med `DynamicParam` `Process` nyckelorden, och `End` . `Begin`Instruktions listan körs en stund innan alla objekt tas emot från pipelinen.

Syntax:

```Syntax
function <name> {
    DynamicParam {<statement list>}
    begin {<statement list>}
    process {<statement list>}
    end {<statement list>}
}
```

### <a name="break"></a>Bryt ned

Gör att ett skript avslutar en slinga.

Syntax:

```Syntax
while (<condition>) {
   <statements>
   ...

   break
   ...

   <statements>
}
```

### <a name="catch"></a>Dokumentation

Anger en uttrycks lista som ska köras om ett fel inträffar i medföljande instruktions lista. En fel typ kräver hakparenteser. Det andra paret hakparenteser anger att fel typen är valfri.

Syntax:

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
```

### <a name="class"></a>Klass

Anger en ny klass i PowerShell.

Syntax:

```Syntax
class <class-name> {
    [[hidden] [static] <property-definition> ...]
    [<class-name>([argument-list>]) {<constructor-statement-list>} ...]
    [[hidden] [static] <method-definition> ...]
}
```

### <a name="continue"></a>Fortsätt

Gör att ett skript slutar att köra en loop och gå tillbaka till villkoret. Om villkoret är uppfyllt, kommer skriptet att starta loopen igen.

Syntax:

```Syntax
while (<condition>) {
   <statements>
   ...

   continue
   ...

   <statements>
}
```

### <a name="data"></a>Data

I ett skript definierar ett avsnitt som isolerar data från skript logiken. Kan även innehålla `If` instruktioner och vissa begränsade kommandon.

Syntax:

```Syntax
data <variable> [-supportedCommand <cmdlet-name>] {<permitted content>}
```

### <a name="do"></a>Gör följande

Används med `While` `Until` nyckelordet eller som en loop-konstruktion. PowerShell kör instruktions listan minst en gången, till skillnad från en loop som använder `While` .

Syntax för `While` :

```Syntax
do {<statement list>} while (<condition>)
```

Syntax för `Until` :

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="dynamicparam"></a>DynamicParam

Anger en del av bröd texten i en funktion, tillsammans med `Begin` `Process` nyckelorden, och `End` . Dynamiska parametrar läggs till vid körnings tillfället.

Syntax:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="else"></a>Tilläggs

Används med `If` nyckelordet för att ange standard instruktions listan.

Syntax:

```Syntax
if (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="elseif"></a>ElseIf

Används med `If` `Else` nyckelorden och för att ange ytterligare villkor. `Else`Nyckelordet är valfritt.

Syntax:

```Syntax
if (<condition>) {<statement list>}
elseif (<condition>) {<statement list>}
else {<statement list>}
```

### <a name="end"></a>Slut

Anger en del av bröd texten i en funktion, tillsammans med `DynamicParam` `Begin` nyckelorden, och `End` . `End`Instruktions listan körs en gången efter att alla objekt har tagits emot från pipelinen.

Syntax:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="enum"></a>Enum

`enum` används för att deklarera en uppräkning. en distinkt typ som består av en uppsättning namngivna etiketter som kallas Enumerator-lista.

Syntax:

```Syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

### <a name="exit"></a>Avsluta

Gör att PowerShell avslutar ett skript eller en PowerShell-instans.

Syntax:

```Syntax
exit
exit <exitcode>
```

När du använder `pwsh` med **fil** parametern `.ps1` bör (skript filen) innehålla instruktioner för hantering av eventuella fel eller undantag som inträffar när skriptet körs. Du bör endast använda `exit` instruktionen för att ange skriptets efter körnings status.

I Windows är alla siffror mellan `[int]::MinValue` och `[int]::MaxValue` tillåtna.

På UNIX tillåts endast positiva tal mellan `[byte]::MinValue` och `[byte]::MaxValue` . Ett negativt tal i intervallet `-1` genom `-255` översätts automatiskt till ett positivt tal genom att lägga till 256. `-2`Transformera till exempel till `254` .

I PowerShell `exit` anger instruktionen värdet för `$LASTEXITCODE` variabeln. I kommando tolken i Windows (cmd.exe) anger avslutnings instruktionen värdet för `%ERRORLEVEL%` miljövariabeln.

Alla argument som inte är numeriska eller utanför det plattformsspecifika intervallet översätts till värdet `0` .

I följande exempel anger användaren fel nivåns variabel värde till 4 genom att lägga till `exit 4` i skript filen `test.ps1` .

```cmd
C:\scripts\test>type test.ps1
1
2
3
exit 4

C:\scripts\test>pwsh -file ./test.ps1
1
2
3

C:\scripts\test>echo %ERRORLEVEL%
4
```

När du kör `pwsh.exe -File <path to a script>` och skript filen avslutas med ett `exit` kommando, anges avslutnings koden till det numeriska argument som används med `exit` kommandot. Om skriptet saknar `exit` instruktioner är avslutnings koden alltid `0` När skriptet slutförs utan fel eller `1` När skriptet avslutas från ett ohanterat undantag.

### <a name="filter"></a>Filtrera

Anger en funktion i vilken instruktions listan körs en gång för varje inobjekt. Det har samma resultat som en funktion som bara innehåller ett process block.

Syntax:

```Syntax
filter <name> {<statement list>}
```

### <a name="finally"></a>Utväg

Definierar en instruktions lista som körs efter-instruktioner som är associerade med try och catch. En `Finally` instruktions lista körs även om du trycker på `CTRL+C` för att lämna ett skript eller om du använder nyckelordet exit i skriptet.

Syntax:

```Syntax
try {<statement list>}
catch [<error type>] {<statement list>}
finally {<statement list>}
```

### <a name="for"></a>För

Definierar en loop med ett villkor.

Syntax:

```Syntax
for (<initialize>; <condition>; <iterate>) { <statement list> }
```

### <a name="foreach"></a>ForEach

Definierar en loop med varje medlem i en samling.

Syntax:

```Syntax
ForEach (<item> in <collection>) { <statement list> }
```

### <a name="from"></a>Från

Reserverad för framtida användning.

### <a name="function"></a>Funktion

Skapar en namngiven instruktions lista med återanvändbar kod. Du kan namnge omfånget som en funktion tillhör. Du kan också ange en eller flera namngivna parametrar med hjälp av `Param` nyckelordet. I listan funktions uttryck kan du inkludera `DynamicParam` `Begin` listorna,, `Process` och `End` .

Syntax:

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1> [, [type]<$pname2>])
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

Du kan också välja att definiera en eller flera parametrar utanför instruktions listan efter funktions namnet.

Syntax:

```Syntax
function [<scope:>]<name> [([type]<$pname1>, [[type]<$pname2>])] {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="if"></a>Om

Definierar ett villkor.

Syntax:

```Syntax
if (<condition>) {<statement list>}
```

### <a name="hidden"></a>Dold

Döljer klass medlemmar från standard resultaten av `Get-Member` cmdleten och från IntelliSense-och TABB-slutförande-resultat.

Syntax:

```Syntax
Hidden [data type] $member_name
```

### <a name="in"></a>I

Används i en `ForEach` instruktion för att skapa en loop som använder varje medlem i en samling.

Syntax:

```Syntax
ForEach (<item> in <collection>){<statement list>}
```

### <a name="inlinescript"></a>InlineScript

Kör arbets flödes kommandon i en delad PowerShell-session. Det här nyckelordet är endast giltigt i ett PowerShell-arbetsflöde.

Syntax:

```Syntax
workflow <verb>-<noun>
{
   InlineScript
   {
      <Command/Expression>
      ...

   }
}
```

`InlineScript`Nyckelordet anger en `InlineScript` aktivitet, som kör kommandon i en delad standard-session (inte arbets flöde). Du kan använda `InlineScript` nyckelordet för att köra kommandon som inte på annat sätt är giltiga i ett arbets flöde och köra kommandon som delar data. Som standard körs kommandona i ett InlineScript-skript block i en separat process.

Mer information finns i [köra PowerShell-kommandon i ett arbets flöde](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574197(v=ws.11)).

### <a name="param"></a>Param

Definierar parametrarna i en funktion.

Syntax:

```Syntax
function [<scope:>]<name> {
   param ([type]<$pname1>[, [[type]<$pname2>]])
   <statement list>
}
```

### <a name="process"></a>Process

Anger en del av bröd texten i en funktion, tillsammans med `DynamicParam` `Begin` nyckelorden, och `End` . När en `Process` instruktions lista tar emot inmatade objekt från pipelinen `Process` körs instruktions listan en gång för varje element från pipelinen. Om pipelinen inte innehåller några objekt `Process` körs inte instruktions listan. Om kommandot är det första kommandot i pipelinen `Process` körs instruktions listan en enda gången.

Syntax:

```Syntax
function <name> {
   DynamicParam {<statement list>}
   begin {<statement list>}
   process {<statement list>}
   end {<statement list>}
}
```

### <a name="return"></a>Returrelaterade

Gör att PowerShell lämnar det aktuella omfånget, till exempel ett skript eller en funktion, och skriver det valfria uttrycket till utdata.

Syntax:

```Syntax
return [<expression>]
```

### <a name="static"></a>Statisk

Anger att egenskapen eller metoden som definierats är gemensam för alla instanser av klassen i som definieras.

Se `Class` exempel på användnings exempel.

### <a name="switch"></a>Switch

Använd en instruktion för att kontrol lera flera villkor `Switch` . `Switch`Instruktionen motsvarar en serie `If` instruktioner, men det är enklare.

`Switch`Instruktionen visar varje villkor och en valfri åtgärd. Om ett villkor hämtas utförs åtgärden.

Syntax 1:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] ( <value> )
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

Syntax 2:

```Syntax
switch [-regex|-wildcard|-exact][-casesensitive] -file <filename>
{
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   <string>|<number>|<variable>|{ <expression> } {<statement list>}
   ...

   default {<statement list>}
}
```

### <a name="throw"></a>Genereras

Genererar ett objekt som ett fel.

Syntax:

```Syntax
throw [<object>]
```

### <a name="trap"></a>Väll

Definierar en instruktions lista som ska köras om ett fel påträffas. En fel typ kräver hakparenteser. Det andra paret hakparenteser anger att fel typen är valfri.

Syntax:

```Syntax
trap [[<error type>]] {<statement list>}
```

### <a name="try"></a>Testa

Definierar en instruktions lista som ska genomsökas efter fel medan instruktionen körs. Om ett fel inträffar fortsätter PowerShell att köras i a- `Catch` eller- `Finally` instruktionen. En fel typ kräver hakparenteser. Det andra paret hakparenteser anger att fel typen är valfri.

Syntax:

```Syntax
try {<statement list>}
catch [[<error type>]] {<statement list>}
finally {<statement list>}
```

### <a name="until"></a>Tills

Används i en `Do` instruktion som en loop-konstruktion där instruktions listan körs minst en gången.

Syntax:

```Syntax
do {<statement list>} until (<condition>)
```

### <a name="using"></a>Använda

Gör det möjligt att ange vilka namn områden som används i sessionen. Klasser och medlemmar kräver mindre inmatning för att nämna dem. Du kan också ta med klasser från moduler.

Syntax #1:

```Syntax
using namespace <.Net-framework-namespace>
```

Syntax #2:

```Syntax
using module <module-name>
```

### <a name="while"></a>Tiden

`while`Instruktionen är en loop-konstruktion där villkoret testas innan uttrycken utförs. Om villkoret är falskt körs inte satserna.

Syntax för instruktioner:

```Syntax
while (<condition>) {
   <statements>
 }
```

När det används i en `Do` instruktion, `while` är en del av en loop-konstruktion där instruktions listan körs minst en gång.

Syntax för loop:

```Syntax
do {<statement list>} while (<condition>)
```

## <a name="see-also"></a>SE ÄVEN

- [about_Special_Characters](about_Special_Characters.md)
- [about_Wildcards](about_Wildcards.md)
