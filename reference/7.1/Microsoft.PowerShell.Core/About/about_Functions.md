---
description: Beskriver hur du skapar och använder funktioner i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: bef1f9f0b672f45c30626a1bbe4f2c6a7dfa540b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272589"
---
# <a name="about-functions"></a>Om Functions

## <a name="short-description"></a>Kort beskrivning

Beskriver hur du skapar och använder funktioner i PowerShell.

## <a name="long-description"></a>Lång beskrivning

En funktion är en lista med PowerShell-instruktioner som har ett namn som du tilldelar. När du kör en funktion skriver du funktions namnet. Instruktionerna i listan körs som om du hade skrivit dem i kommando tolken.

Funktioner kan vara så enkla som möjligt:

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

En funktion kan också vara så komplex som en cmdlet eller ett program program.

Precis som-cmdlets kan funktioner ha parametrar. Parametrarna kan vara namngivna, positions-, växlings-eller dynamiska parametrar. Funktions parametrar kan läsas från kommando raden eller från pipelinen.

Funktioner kan returnera värden som kan visas, tilldelas variabler eller skickas till andra funktioner eller cmdletar. Du kan också ange ett retur värde med hjälp av `return` nyckelordet. `return`Nyckelordet påverkar eller utelämnar inte andra utdata som returneras från din funktion. `return`Nyckelordet avslutar dock funktionen på raden. Mer information finns i [about_Return](about_Return.md).

Funktionens instruktions lista kan innehålla olika typer av uttrycks listor med nyckelorden `Begin` , `Process` och `End` . De här instruktions listorna hanterar inmatade från pipelinen på olika sätt.

Ett filter är en särskild typ av funktion som använder `Filter` nyckelordet.

Funktioner kan också fungera som cmdlets. Du kan skapa en funktion som fungerar precis som en cmdlet utan att använda `C#` programmering. Mer information finns i [about_Functions_Advanced](about_Functions_Advanced.md).

## <a name="syntax"></a>Syntax

Följande är syntaxen för en funktion:

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

En funktion innehåller följande objekt:

- Ett `Function` nyckelord
- Ett omfång (valfritt)
- Ett namn som du väljer
- Valfritt antal namngivna parametrar (valfritt)
- Ett eller flera PowerShell-kommandon inom klammerparentes `{}`

Mer information om `Dynamicparam` nyckelordet och dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

## <a name="simple-functions"></a>Enkla funktioner

Funktionerna behöver inte vara komplicerade för att vara användbara. De enklaste funktionerna har följande format:

```
function <function-name> {statements}
```

Följande funktion startar till exempel PowerShell med alternativet Kör som administratör.

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

Om du vill använda funktionen skriver du: `Start-PSAdmin`

Om du vill lägga till instruktioner till funktionen skriver du varje instruktion på en separat rad eller använder ett semikolon `;` för att avgränsa satserna.

Följande funktion hittar till exempel alla `.jpg` filer i den aktuella användarens kataloger som har ändrats efter start datumet.

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

Du kan skapa en verktygs låda med användbara små funktioner. Lägg till dessa funktioner i din PowerShell-profil, enligt beskrivningen i [about_Profiles](about_Profiles.md) och senare i det här avsnittet.

## <a name="function-names"></a>Funktions namn

Du kan tilldela ett namn till en funktion, men funktioner som du delar med andra bör följa de namngivnings regler som har upprättats för alla PowerShell-kommandon.

Funktions namn ska bestå av ett verb-Substantiv-par där verbet identifierar den åtgärd som funktionen utför och Substantiv identifierar objektet som cmdleten utför åtgärden på.

Funktioner bör använda standardverb som har godkänts för alla PowerShell-kommandon. De här verben hjälper oss att hålla våra kommando namn enkla, konsekventa och enkla för användare att förstå.

Mer information om standard PowerShell-verben finns i [godkända verb](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) i Microsoft docs.

## <a name="functions-with-parameters"></a>Funktioner med parametrar

Du kan använda parametrar med Functions, inklusive namngivna parametrar, positions parametrar, växel parametrar och dynamiska parametrar. Mer information om dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="named-parameters"></a>Namngivna parametrar

Du kan definiera valfritt antal namngivna parametrar. Du kan inkludera ett standardvärde för namngivna parametrar, enligt beskrivningen längre fram i det här avsnittet.

Du kan definiera parametrar inom klammerparenteserna med hjälp av `Param` nyckelordet, som du ser i följande exempel-syntax:

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

Du kan också definiera parametrar utanför klamrarna utan `Param` nyckelord, som du ser i följande exempel-syntax:

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

Nedan visas ett exempel på den här alternativa syntaxen.

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

Den första metoden är att föredra, men det finns ingen skillnad mellan dessa två metoder.

När du kör funktionen tilldelas värdet som du anger för en parameter en variabel som innehåller parameter namnet. Värdet för variabeln kan användas i-funktionen.

Följande exempel är en funktion som kallas `Get-SmallFiles` . Den här funktionen har en `$Size` parameter. Funktionen visar alla filer som är mindre än värdet för `$Size` parametern och undantar kataloger:

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

I funktionen kan du använda `$Size` variabeln, som är det namn som definierats för parametern.

Om du vill använda den här funktionen skriver du följande kommando:

```powershell
Get-SmallFiles -Size 50
```

Du kan också ange ett värde för en namngiven parameter utan parameter namnet.
Till exempel ger följande kommando samma resultat som ett kommando som namnger **storleks** parametern:

```powershell
Get-SmallFiles 50
```

Om du vill definiera ett standardvärde för en parameter skriver du ett likhets tecken och värdet efter parameter namnet, som du ser i följande variant av `Get-SmallFiles` exemplet:

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

Om du skriver `Get-SmallFiles` utan ett värde tilldelar funktionen 100 till `$size` . Om du anger ett värde använder funktionen det värdet.

Alternativt kan du ange en kort hjälp sträng som beskriver standardvärdet för din parameter genom att lägga till attributet **PSDefaultValue** i beskrivningen av parametern och ange egenskapen **Help** för **PSDefaultValue**. Om du vill ange en hjälp sträng som beskriver standardvärdet (100) för **storleks** parametern i `Get-SmallFiles` funktionen, lägger du till attributet **PSDefaultValue** som visas i följande exempel.

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

Mer information om klassen **PSDefaultValue** finns i [PSDefaultValue-attribut medlemmar](/dotnet/api/system.management.automation.psdefaultvalueattribute).

### <a name="positional-parameters"></a>Positions parametrar

En positions parameter är en parameter utan parameter namn. PowerShell använder parameter värde ordningen för att koppla varje parameter värde till en parameter i funktionen.

När du använder positions parametrar, anger du ett eller flera värden efter funktions namnet. Positions parameter värden tilldelas till `$args` mat ris variabeln.
Värdet som följer funktions namnet tilldelas till den första positionen i `$args` matrisen `$args[0]` .

Följande `Get-Extension` funktion lägger till `.txt` fil namns tillägget i ett fil namn som du anger:

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a>Växla parametrar

En växel är en parameter som inte kräver något värde. I stället skriver du funktions namnet följt av namnet på växel parametern.

Definiera en växlings parameter genom att ange typen `[switch]` före parameter namnet, som du ser i följande exempel:

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

När du skriver `On` parametern switch efter funktions namnet visar funktionen "växla på". Utan parametern switch visas "Inaktivera".

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

Du kan också tilldela ett **booleskt** värde till en växel när du kör funktionen, som du ser i följande exempel:

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a>Använda Ihopbuntning för att representera kommando parametrar

Du kan använda ihopbuntning för att representera parametrarna för ett kommando. Den här funktionen introduceras i Windows PowerShell 3,0.

Använd den här metoden i functions som anropar kommandon i sessionen. Du behöver inte deklarera eller räkna upp kommando parametrarna eller ändra funktionen när kommando parametrar ändras.

Följande exempel funktion anropar `Get-Command` cmdleten. Kommandot används `@Args` för att representera parametrarna för `Get-Command` .

```powershell
function Get-MyCommand { Get-Command @Args }
```

Du kan använda alla parametrar `Get-Command` när du anropar `Get-MyCommand` funktionen. Parametrar och parameter värden skickas till kommandot med hjälp av `@Args` .

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

`@Args`Funktionen använder den `$Args` automatiska parametern som representerar odeklarerade cmdlet-parametrar och värden från återstående argument.

Mer information om ihopbuntning finns i [about_Splatting](about_Splatting.md).

## <a name="piping-objects-to-functions"></a>Rör objekt till Functions

Alla funktioner kan ta inmatade från pipelinen. Du kan styra hur en funktion bearbetar inmatade värden från pipelinen med hjälp av `Begin` , `Process` och `End` . Följande exempel-syntax visar de tre nyckelorden:

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

`Begin`Instruktions listan körs bara en gång, i början av funktionen.

> [!IMPORTANT]
> Om din funktion definierar ett `Begin` , `Process` eller ett `End` block, måste all kod finnas inuti dessa block. Ingen kod kommer att identifieras utanför blocken om *något* av blocken har definierats.

`Process`Instruktions listan körs en gången för varje objekt i pipelinen.
Även om `Process` blocket körs, tilldelas varje pipeline-objekt den `$_` automatiska variabeln, ett pipeline-objekt i taget.

När funktionen tar emot alla objekt i pipelinen `End` körs instruktions listan en enda gången. Om nej `Begin` , `Process` eller `End` nyckelord används, behandlas alla instruktioner som en `End` instruktions lista.

Följande funktion använder `Process` nyckelordet. Funktionen visar exempel från pipelinen:

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

Visa den här funktionen genom att ange en lista med siffror avgränsade med kommatecken, som du ser i följande exempel:

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

När du använder en funktion i en pipeline, tilldelas de objekt som skickas till funktionen den `$input` automatiska variabeln. Funktionen kör instruktioner med `Begin` nyckelordet innan några objekt kommer från pipelinen. Funktionen kör instruktioner med `End` nyckelordet när alla objekt har tagits emot från pipelinen.

I följande exempel visas den `$input` automatiska variabeln med `Begin` och `End` nyckelord.

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

Om den här funktionen körs med hjälp av pipelinen visas följande resultat:

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

När `Begin` instruktionen körs har funktionen inte inmatade värden från pipelinen. `End`Instruktionen körs när funktionen har värden.

Om funktionen har ett `Process` nyckelord tas varje objekt i som `$input` tas bort från `$input` och tilldelas `$_` . I följande exempel finns en `Process` instruktions lista:

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

I det här exemplet skickas varje objekt som är skickas till funktionen till `Process` instruktions listan. De `Process` instruktioner som körs för varje objekt, ett objekt i taget. Den `$input` automatiska variabeln är tom när funktionen når `End` nyckelordet.

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

Mer information finns i [använda uppräknare](about_Automatic_Variables.md#using-enumerators)

## <a name="filters"></a>Filter

Ett filter är en typ av funktion som körs på varje objekt i pipelinen. Ett filter liknar en funktion med alla dess uttryck i ett `Process` block.

Syntaxen för ett filter är följande:

```
filter [<scope:>]<name> {<statement list>}
```

Följande filter använder logg poster från pipelinen och visar sedan antingen hela posten eller bara meddelande delen av posten:

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a>Funktions omfång

Det finns en funktion i omfånget som den skapades i.

Om en funktion är en del av ett skript är funktionen tillgänglig för instruktioner i skriptet. Som standard är en funktion i ett skript inte tillgänglig i kommando tolken.

Du kan ange omfattningen för en funktion. Funktionen läggs till exempel till i det globala omfånget i följande exempel:

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

När en funktion finns i det globala omfånget kan du använda funktionen i skript, i functions och på kommando raden.

Functions skapar vanligt vis ett definitions område. De objekt som skapas i en funktion, till exempel variabler, finns bara i funktions omfånget.

Mer information om omfång i PowerShell finns [about_Scopes](about_Scopes.md).

## <a name="finding-and-managing-functions-using-the-function-drive"></a>Hitta och hantera funktioner med funktionen: enhet

Alla funktioner och filter i PowerShell lagras automatiskt i `Function:` enheten. Enheten exponeras av PowerShell- **funktions** leverantören.

När du refererar till `Function:` enheten skriver du ett kolon efter- **funktionen** , precis som du skulle göra när du refererar `C` till `D` en dators eller datorns enhet.

Följande kommando visar alla funktioner i den aktuella sessionen av PowerShell:

```powershell
Get-ChildItem function:
```

Kommandona i funktionen lagras som ett skript block i funktionens definitions egenskap. Om du till exempel vill visa kommandona i Hjälp funktionen som medföljer PowerShell, skriver du:

```powershell
(Get-ChildItem function:help).Definition
```

Du kan också använda följande syntax.

```powershell
$function:help
```

Mer information om `Function:` enheten finns i hjälp avsnittet för **funktions** leverantören. Skriv `Get-Help Function`.

## <a name="reusing-functions-in-new-sessions"></a>Återanvända funktioner i nya sessioner

När du skriver en funktion i PowerShell-Kommandotolken blir funktionen en del av den aktuella sessionen. Den är tillgänglig tills sessionen avslutas.

Om du vill använda din funktion i alla PowerShell-sessioner lägger du till funktionen i din PowerShell-profil. Mer information om profiler finns [about_Profiles](about_Profiles.md).

Du kan också spara din funktion i en PowerShell-skriptfil. Skriv din funktion i en textfil och spara sedan filen med `.ps1` fil namns tillägget.

## <a name="writing-help-for-functions"></a>Skriver hjälp för functions

Cmdlet: en `Get-Help` får hjälp för funktioner, samt för cmdlets, providers och skript. Om du vill ha hjälp med en funktion skriver du `Get-Help` följt av funktions namnet.

Om du till exempel vill få hjälp med `Get-MyDisks` funktionen skriver du:

```powershell
Get-Help Get-MyDisks
```

Du kan skriva hjälp för en funktion med någon av följande två metoder:

- Comment-Based hjälp för functions

  Skapa ett hjälp avsnitt genom att använda särskilda nyckelord i kommentarerna. Om du vill skapa en kommenterad hjälp för en funktion måste kommentarerna placeras i början eller slutet av funktions texten eller på de rader som föregår nyckelordet function. Mer information om kommenterad hjälp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).

- XML-Based hjälp för functions

  Skapa ett XML-baserat hjälp avsnitt, till exempel den typ som vanligt vis skapas för cmdletar. XML-baserad hjälp krävs om du lokaliserar hjälp ämnen till flera språk.

  Om du vill associera funktionen med det XML-baserade hjälp avsnittet använder du det `.ExternalHelp` kommenterings-baserade hjälp nyckelordet. Utan det här nyckelordet `Get-Help` kan du inte hitta funktions hjälp avsnittet och anropar till `Get-Help` för funktionen returnera endast den automatiskt genererade hjälpen.

  Mer information om `ExternalHelp` nyckelordet finns [about_Comment_Based_Help](about_Comment_Based_Help.md). Mer information om XML-baserad hjälp finns i [så här skriver du cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN-biblioteket.

## <a name="see-also"></a>Se även

[about_Automatic_Variables](about_Automatic_Variables.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Parameters](about_Parameters.md)

[about_Profiles](about_Profiles.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Function_provider](about_Function_provider.md)

