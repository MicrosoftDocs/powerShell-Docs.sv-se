---
description: Beskriver hur du skriver kommentarer baserade hjälp avsnitt för funktioner och skript.
Locale: en-US
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: cc19b11322e8b2062f9659c3fbce92ad5c6eded0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194219"
---
# <a name="about-comment-based-help"></a>Om kommenterings-baserad hjälp

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du skriver kommentarer baserade hjälp avsnitt för funktioner och skript.

## <a name="long-description"></a>Lång beskrivning

Du kan skriva kommentarer baserade hjälp avsnitt för funktioner och skript genom att använda särskilda nyckelord för hjälp kommentarer.

Cmdleten [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) visar kommenterad hjälp i samma format som den visar cmdlet-hjälpen som genereras från XML-filer. Användarna kan använda alla parametrar i `Get-Help` , till exempel **detaljerade**, **fullständiga**, **exempel** och **online**, för att visa innehållet i den kommenterade hjälpen.

Du kan också skriva XML-baserade hjälpfiler för funktioner och skript. Om du vill aktivera `Get-Help` cmdleten för att hitta den XML-baserade hjälp filen för en funktion eller ett skript, använder du `.ExternalHelp` nyckelordet. Utan det här nyckelordet kan du `Get-Help` inte hitta XML-baserade hjälp avsnitt för funktioner eller skript.

I det här avsnittet beskrivs hur du skriver hjälp ämnen för funktioner och skript. Information om hur du visar hjälp avsnitt för funktioner och skript finns i [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).

Cmdletarna [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) och [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) fungerar bara på XML-filer. Uppdaterings bara hjälp har inte stöd för kommentarer baserade hjälp avsnitt.

## <a name="syntax-for-comment-based-help"></a>Syntax för kommenterings-baserad hjälp

Syntaxen för kommenterings-baserad hjälp är följande:

```
# .<help keyword>
# <help content>
```

eller

```
<#
.<help keyword>
<help content>
#>
```

Kommenterad hjälp skrivs som en rad kommentarer. Du kan skriva en kommentars symbol `#` före varje rad med kommentarer, eller så kan du använda- `<#` och- `#>` symbolerna för att skapa ett kommentar block. Alla rader i kommentars blocket tolkas som kommentarer.

Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande. Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.

Nyckelord definierar varje avsnitt i en kommenterings-baserad hjälp. Varje comment-baserat hjälp nyckelord föregås av en punkt `.` . Nyckelorden kan visas i vilken ordning som helst. Nyckelords namnen är inte Skift läges känsliga.

Nyckelordet kan till exempel `.Description` föregå en beskrivning av en funktion eller ett skript.

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

Kommentar blocket måste innehålla minst ett nyckelord. Några av nyckelorden, till exempel `.EXAMPLE` , kan visas många gånger i samma kommentars block. Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.

## <a name="syntax-for-comment-based-help-in-functions"></a>Syntax för kommenterings-baserad hjälp i functions

Den kommenterade hjälpen för en funktion kan visas på tre platser:

- I början av funktions texten.
- I slutet av funktions texten.
- Före `function` nyckelordet. Det får inte finnas mer än en tom rad mellan den sista raden i funktions hjälpen och `function` nyckelordet.

Exempel:

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

eller

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

eller

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a>Syntax för kommenterings-baserad hjälp i skript

Kommentera-baserad hjälp för ett skript kan visas på någon av följande två platser i skriptet.

- I början av skript filen. Skript hjälpen kan bara föregås av kommentarer och tomma rader.

  Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen. Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.

- I slutet av skript filen. Men om skriptet är signerat placerar du en kommenterings-baserad hjälp i början av skript filen. Slutet på skriptet används av signerings blocket.

Exempel:

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

eller

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a>Syntax för kommenterings-baserad hjälp i skript moduler

I en skript `.psm1` -modul använder den kommenterade hjälpen syntaxen för functions, inte syntaxen för skript. Du kan inte använda kommandosyntaxen för att ge hjälp för alla funktioner som definierats i en-modul.

Om du till exempel använder `.ExternalHelp` nyckelordet för att identifiera de XML-baserade hjälpfilerna för funktionerna i en-modul, måste du lägga till en `.ExternalHelp` kommentar till varje funktion.

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a>Kommentera-baserade hjälp nyckelord

Följande är giltiga kommentarer baserade hjälp nyckelord. De visas i den ordning som de normalt visas i ett hjälp avsnitt, tillsammans med deras avsedda användning. Dessa nyckelord kan visas i vilken ordning som helst i den kommenterade hjälpen, och de är inte Skift läges känsliga.

### <a name="synopsis"></a>. Sammanfattning

En kort beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

### <a name="description"></a>. BETECKNING

En detaljerad beskrivning av funktionen eller skriptet. Det här nyckelordet kan bara användas en gång i varje ämne.

### <a name="parameter"></a>. PROFILESERVICEAPPLICATIONPROXY

Beskrivningen av en parameter. Lägg till ett `.PARAMETER` nyckelord för varje parameter i syntaxen Function och script.

Skriv parameter namnet på samma rad som `.PARAMETER` nyckelordet. Ange parameter beskrivningen på raderna som följer `.PARAMETER` nyckelordet. Windows PowerShell tolkar all text mellan `.PARAMETER` raden och nästa nyckelord eller slutet av kommentars blocket som en del av parameter beskrivningen.
Beskrivningen kan innehålla stycke brytningar.

```
.PARAMETER  <Parameter-Name>
```

Parameter nyckelorden kan visas i vilken ordning som helst i kommentars blocket, men funktionen eller skript-syntaxen avgör i vilken ordning parametrarna (och deras beskrivningar) visas i hjälp avsnittet. Om du vill ändra ordningen ändrar du syntaxen.

Du kan också ange en parameter beskrivning genom att placera en kommentar i funktionen eller syntaxen för skriptet omedelbart före parameterns variabel namn. För att detta ska fungera måste du också ha ett kommentar block med minst ett nyckelord.

Om du använder både en syntax-kommentar och ett `.PARAMETER` nyckelord, används beskrivningen som är associerad med `.PARAMETER` nyckelordet och syntax-kommentaren ignoreras.

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a>. EXEMPEL

Ett exempel kommando som använder funktionen eller skriptet, eventuellt följt av exempel på utdata och en beskrivning. Upprepa det här nyckelordet för varje exempel.

### <a name="inputs"></a>. TILLFÖR

.NET-typerna av objekt som kan skickas till funktionen eller skriptet. Du kan också inkludera en beskrivning av inobjekten.

### <a name="outputs"></a>. UTDATA

.NET-typen av objekt som cmdleten returnerar. Du kan också inkludera en beskrivning av de returnerade objekten.

### <a name="notes"></a>. NOTER

Ytterligare information om funktionen eller skriptet.

### <a name="link"></a>. OPERATIONSFÖLJDSLÄNKKOD

Namnet på ett relaterat ämne. Värdet visas på raden under ". LINK "nyckelordet och måste föregås av en kommentar symbol `#` eller ingå i kommentars blocket.

Upprepa `.LINK` nyckelordet för varje relaterat ämne.

Det här innehållet visas i avsnittet relaterade länkar i hjälp avsnittet.

`.Link`Nyckelords innehållet kan också innehålla en Uniform Resource Identifier (URI) till en online-version av samma hjälp avsnitt. Online-versionen öppnas när du använder **online** -parametern för `Get-Help` . URI: n måste börja med http eller https.

### <a name="component"></a>. KOMPONENTFILERNA

Namnet på tekniken eller funktionen som funktionen eller skriptet använder, eller som den är relaterad till. **Komponent** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

### <a name="role"></a>. ROLLINNEHAVAREN

Namnet på användar rollen för hjälp avsnittet. **Roll** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

### <a name="functionality"></a>. FUNKTIONS

Nyckelord som beskriver den avsedda användningen av funktionen. **Funktions** parametern i `Get-Help` använder det här värdet för att filtrera Sök resultaten som returneras av `Get-Help` .

### <a name="forwardhelptargetname"></a>. FORWARDHELPTARGETNAME

Omdirigerar till hjälp avsnittet för det angivna kommandot. Du kan omdirigera användare till valfritt hjälp avsnitt, inklusive hjälp avsnitt för en funktion, ett skript, en cmdlet eller en provider.

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a>. FORWARDHELPCATEGORY

Anger hjälp kategorin för objektet i `.ForwardHelpTargetName` . Giltiga värden är,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` eller `All` . Använd det här nyckelordet för att undvika konflikter när det finns kommandon med samma namn.

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a>. REMOTEHELPRUNSPACE

Anger en session som innehåller hjälp avsnittet. Ange en variabel som innehåller ett **PSSession** -objekt. Det här nyckelordet används av cmdleten [export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) för att hitta hjälp avsnitten för de exporterade kommandona.

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a>. EXTERNALHELP

Anger en XML-baserad hjälpfil för skriptet eller funktionen.

```powershell
# .EXTERNALHELP <XML Help File>
```

`.ExternalHelp`Nyckelordet krävs när en funktion eller ett skript dokumenteras i XML-filer. Utan det här nyckelordet `Get-Help` kan inte hitta den XML-baserade hjälp filen för funktionen eller skriptet.

`.ExternalHelp`Nyckelordet har företräde framför andra kommenterings-baserade hjälp nyckelord. Om `.ExternalHelp` finns visas `Get-Help` inte kommenterad hjälp, även om det inte går att hitta ett hjälp avsnitt som matchar värdet för `.ExternalHelp` nyckelordet.

Om funktionen exporteras av en modul ställer du in värdet för `.ExternalHelp` nyckelordet till ett fil namn utan sökväg. `Get-Help` söker efter det angivna fil namnet i en språkspecifik under katalog i modulens katalog. Det finns inga krav på namnet på den XML-baserade hjälp filen för en funktion, men det är en bra idé att använda följande format:

```
<ScriptModule.psm1>-help.xml
```

Om funktionen inte ingår i en modul inkluderar du en sökväg till den XML-baserade hjälp filen. Om värdet innehåller en sökväg och sökvägen innehåller UI-kultur-specifika under kataloger, `Get-Help` söker igenom under katalogerna rekursivt efter en XML-fil med namnet på skriptet eller funktionen i enlighet med de språk reserv standarder som är etablerade för Windows, precis som i en modul katalog.

Mer information om cmdlet Help XML-baserade hjälp fil format finns i [så här skriver du cmdlet-hjälpen](/powershell/scripting/developer/help/writing-comment-based-help-topics).

## <a name="autogenerated-content"></a>Automatiskt genererat innehåll

Namn, syntax, parameter lista, parameter-Attribute tabell, vanliga parametrar och anmärkningar genereras automatiskt av `Get-Help` cmdleten.

### <a name="name"></a>Name

Avsnittet **Name** i ett funktions hjälp avsnitt tas från funktions namnet i Function-syntaxen. **Namnet** på ett skript hjälp avsnitt tas från skript fil namnet. Om du vill ändra namnet eller dess versaler ändrar du syntaxen för funktionen eller skript fil namnet.

### <a name="syntax"></a>Syntax

Avsnittet **syntax** i hjälp avsnittet genereras från funktionen eller syntaxen i skriptet. Om du vill lägga till information i syntaxen för hjälp ämnet, till exempel .NET-typen för en parameter, lägger du till informationen i syntaxen. Om du inte anger en parameter typ infogas **objekt** typen som standardvärdet.

### <a name="parameter-list"></a>Parameter lista

Parameter listan i hjälp avsnittet genereras från funktionen eller syntaxen för skriptet och från de beskrivningar som du lägger till med hjälp av `.Parameter` nyckelordet. Funktions parametrarna visas i avsnittet **parametrar** i hjälp avsnittet i samma ordning som de visas i funktionen eller syntaxen för skript. Stavning och Skift läge för parameter namn tas också med i syntaxen. Det påverkas inte av det parameter namn som anges av `.Parameter` nyckelordet.

### <a name="common-parameters"></a>Vanliga parametrar

De **gemensamma parametrarna** läggs till i syntax och parameter listan i hjälp avsnittet, även om de inte har någon påverkan. Mer information om de gemensamma parametrarna finns [about_CommonParameters](about_CommonParameters.md).

### <a name="parameter-attribute-table"></a>Parameter egenskaps tabell

`Get-Help` genererar tabellen med parameter-attribut som visas när du använder parametern **fullständig** eller **parameter** i `Get-Help` . Värdet för attributen **required**, **position** och **Standardvärde** tas från funktionen eller syntaxen i skriptet.

Standardvärden och ett värde för **acceptera jokertecken** visas inte i tabellen parameter attribut, även om de definieras i funktionen eller skriptet. För att hjälpa användarna att ange den här informationen i parameter beskrivningen.

### <a name="remarks"></a>Kommentarer

Avsnittet **anmärkningar** i hjälp avsnittet genereras automatiskt från funktionen eller skript namnet. Du kan inte ändra eller påverka dess innehåll.

## <a name="examples"></a>Exempel

### <a name="comment-based-help-for-a-function"></a>Kommenterings-baserad hjälp för en funktion

Följande exempel funktion innehåller kommenterings-baserad hjälp:

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

Resultatet är följande:

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a>Parameter beskrivningar i Function-syntax

Det här exemplet är detsamma som föregående, förutom att parameter beskrivningarna infogas i Function-syntaxen. Det här formatet är mest användbart när beskrivningarna är korta.

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a>Kommenterings-baserad hjälp för ett skript

Följande exempel skript innehåller kommenterings-baserad hjälp. Lägg märke till de tomma raderna mellan stängningen `#>` och `Param` instruktionen. I ett skript som saknar `Param` instruktion måste det finnas minst två tomma rader mellan den sista kommentaren i hjälp avsnittet och den första funktions deklarationen. Utan dessa tomma rader `Get-Help` associeras hjälp avsnittet med funktionen, inte skriptet.

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

Följande kommando hämtar skript hjälpen. Eftersom skriptet inte finns i en katalog som anges i `$env:Path` miljövariabeln, `Get-Help` måste kommandot som hämtar skript-hjälpen ange skript Sök vägen.

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a>Omdirigerar till en XML-fil

Du kan skriva XML-baserade hjälp avsnitt för funktioner och skript. Även om det är enklare att implementera en kommenterad hjälp, krävs det en XML-baserad hjälp för uppdaterings bara hjälp och för att tillhandahålla hjälp avsnitt på flera språk.

I följande exempel visas de första raderna i Update-Month.ps1-skriptet.
Skriptet använder `.ExternalHelp` nyckelordet för att ange sökvägen till ett XML-baserat hjälp avsnitt för skriptet.

Observera att `.ExternalHelp` nyckelordets värde visas på samma rad som nyckelordet. Andra placeringar är ineffektiva.

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

I följande exempel visas tre giltiga placeringar av `.ExternalHelp` nyckelordet i en funktion.

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a>Omdirigera till ett annat hjälp avsnitt

Följande kod är ett utdrag från början av den inbyggda hjälp funktionen i PowerShell, som visar en skärm med hjälp text i taget.
Eftersom hjälp avsnittet för `Get-Help` cmdlet: en beskriver hjälp funktionen, använder funktionen och för att `.ForwardHelpTargetName` `.ForwardHelpCategory` omdirigera användaren till `Get-Help` cmdlet-hjälp avsnittet.

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

Följande kommando använder den här funktionen:

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a>Se även

[about_Functions](about_Functions.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Scripts](about_Scripts.md)

[Så här skriver du cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415)
