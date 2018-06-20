---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9aa7e92632c671751020687ddbfc374eeda7148b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189422"
---
# <a name="new-language-features-in-powershell-50"></a>Funktioner för nya språk i PowerShell 5.0

PowerShell 5.0 innehåller följande nya språkelement i Windows PowerShell:

## <a name="class-keyword"></a>Nyckelordet class

Den **klassen** nyckelordet definierar en ny klass. Detta är sant .NET Framework-typen.
Klassmedlemmar är offentlig men bara offentliga inom omfånget för modulen.
Du kan inte referera till typnamn som en sträng (till exempel `New-Object` fungerar inte), och i den här versionen kan du inte använda en literal typ (till exempel `[MyClass]`) utanför filen skript-modul som klassen definierats.

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a>Nyckelordet enum och uppräkningar

Stöd för den **enum** nyckelordet har lagts till, som använder ny rad som avgränsare.
Aktuella begränsningar: du kan inte definiera en uppräknare i sig själv, men du kan initiera en uppräkning i en annan uppräkning, som visas i följande exempel.
Dessutom kan bastypen för närvarande inte anges; Det är alltid [int].

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

En Uppräkningsvärdet måste vara en konstant för parsa tid; Du kan inte ange den till resultatet för ett anropade kommando.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Uppräkningar stöder beräkningar, som visas i följande exempel.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a>Importera DscResource

**Importera DscResource** är nu ett true dynamiska nyckelord.
PowerShell Parsar angiven modul rotmodul söker efter klasser som innehåller den **DscResource** attribut.

## <a name="implementingassembly"></a>ImplementingAssembly

Ett nytt fält **ImplementingAssembly**, har lagts till ModuleInfo. Den är inställd på dynamisk sammansättning för en skriptmodul skapas om skriptet definierar klasser eller läsa in sammansättningen för binära moduler. Den är inte inställd när ModuleType = Manifest.

Reflektion på den **ImplementingAssembly** fältet identifierar resurser i en modul. Det innebär att du kan identifiera resurser som skrivits i PowerShell eller andra hanterade språk.

Fält med initierare:

```powershell
[int] $i = 5
```

Statiskt stöds. den fungerar som ett attribut som gör Typbegränsningar, så den kan anges i valfri ordning.

```powershell
static [int] $count = 0
```

En typ är valfritt.

```powershell
$s = "hello"
```

Alla medlemmar är offentlig.

## <a name="constructors-and-instantiation"></a>Konstruktorer och instansiering

Windows PowerShell-klasser kan ha konstruktorer; de har samma namn som sin klass. Konstruktorer kan vara överbelastad. Statiska konstruktörer stöds. Egenskaper med initiering uttryck initieras innan du kör någon kod i en konstruktor. Statiska egenskaper initieras innan innehållet i en statisk konstruktor och instans egenskaper initieras innan innehållet i icke-statisk konstruktor. För närvarande finns ingen syntax för att anropa en konstruktor från en annan konstruktor (t.ex. C\# syntaxen ”: this()"). Lösningen är att definiera en vanlig Init-metod.

Följande är sätt initierar klasser i den här versionen.

En instans skapades av genom att använda Standardkonstruktorn. Observera att New-Object inte stöds i den här versionen.

```powershell
$a = [MyClass]::new()
```

Anropar en konstruktor med en parameter

```powershell
$b = [MyClass]::new(42)
```

Skicka en matris till en konstruktor med flera parametrar
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

I den här versionen fungerar inte New-Object med klasser som definierats i Windows PowerShell. Även för den här versionen visas typnamnet bara lexically, vilket innebär att den inte är synlig utanför modul eller skript som definierar klassen. Funktioner som kan returnera instanser av en klass som definieras i Windows PowerShell och instanser fungerar bra utanför modul eller skript.

`Get-Member -Static` Visar en lista över konstruktorer, så att du kan visa överlagringar som någon annan metod. Prestanda för den här syntaxen är också betydligt snabbare än New-Object.

Startvärden statisk metod med namnet **nya** fungerar med .NET-typer som visas i följande exempel.

```powershell
[hashtable]::new()
```

Du kan nu se konstruktorn överlagringar med Get-medlem eller som visas i det här exemplet:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a>Metoder

En metod för Windows PowerShell-klass implementeras som en ScriptBlock som har endast ett end-block. Alla metoder är offentlig. Följande är ett exempel på att definiera en metod med namnet **EnMetod**.

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x) # method syntax
    }
    private _doSomething($a) {}
}
```

Metodanropet:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Överlagrade metoder – det vill säga de som har samma namn som en befintlig metod men hjälp av de angivna värdena--stöds också.

## <a name="properties"></a>Egenskaper

Alla egenskaper är offentlig. Egenskaper för kräver en ny rad eller semikolon. Om ingen objekttyp har angetts är egenskapstypen-objekt.

Egenskaper som använder verifiering attribut eller argumentet omvandling attribut (t.ex. `[ValidateSet("aaa")]`) fungerar som förväntat.

## <a name="hidden"></a>Dolda

Ett nytt nyckelord **Hidden**, har lagts till. **Dolda** kan tillämpas på Egenskaper och metoder (inklusive konstruktorer).

Dolda medlemmar är offentlig men visas inte i utdata för Get-medlem om-Force läggs till.

Dolda medlemmar ingår inte när fliken slutföra eller med Intellisense om inte slutförs uppstår i den klass som definierar den dolda medlemmen.

Ett nytt attribut **System.Management.Automation.HiddenAttribute** har lagts till så att C#-kod kan ha samma semantik i Windows PowerShell.

## <a name="return-types"></a>Returtyper

Returtypen är kontraktet. Returvärdet konverteras till den förväntade typen. Om ingen returtyp anges är returtypen void. Det finns ingen strömning av objekt. objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.

## <a name="attributes"></a>Attribut

Två nya attribut **DscResource** och **DscProperty** har lagts till.

## <a name="lexical-scoping-of-variables"></a>Lexikaliskt omfattningen för variabler

Nedan visas ett exempel på hur lexikala målgrupp fungerar i den här versionen.

```powershell
$d = 42 # Script scope

function bar
{
    $d = 0 # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d # error, not found dynamically
        return $script:d # no error
        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="end-to-end-example"></a>Slutpunkt till slutpunkt-exempel

I följande exempel skapar flera nya, anpassade klasser för att implementera en HTML-dynamiska språk (DSL).
I exempel läggs sedan hjälpfunktioner för att skapa specifika elementtyper som en del av elementklassen, till exempel rubrik och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.

```powershell
# Classes that define the structure of the document
#
class Html
{
    [string] $docType
    [HtmlHead] $Head
    [Element[]] $Body

    [string] Render()
    {
        $text = "<html>`n<head>`n"
        $text += $this.Head
        $text += "`n</head>`n<body>`n"
        $text += $this.Body -join "`n" # Render all of the body elements
        $text += "</body>`n</html>"
        return $text
    }
    [string] ToString() { return $this.Render() }
}

class HtmlHead
{
    $Title
    $Base
    $Link
    $Style
    $Meta
    $Script
    [string] Render() { return "<title>$($this.Title)</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($this.Attributes)
        {
            foreach ($attr in $this.Attributes.Keys)
            {
                #BUGBUG - need to validate keys against attribute
                $attributesText += " $attr=`"$($this.Attributes[$attr])\`""
            }
        }
        return "<$($this.tag)${attributesText}>$($this.text)</$($this.tag)>`n"
    }
[string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren’t visible outside of the module.
#

function H1 { [Element] @{ Tag = "H1" ; Text = $args.foreach{$_} -join " " }}
function H2 { [Element] @{ Tag = "H2" ; Text = $args.foreach{$_} -join " " }}
function H3 { [Element] @{ Tag = "H3" ; Text = $args.foreach{$_} -join " " }}
function P { [Element] @{ Tag = "P" ; Text = $args.foreach{$_} -join " " }}
function B { [Element] @{ Tag = "B" ; Text = $args.foreach{$_} -join " " }}
function I { [Element] @{ Tag = "I" ; Text = $args.foreach{$_} -join " " }}
function HREF
{
    param (
        $Name,
        $Link
    )
    return [Element] @{
        Tag = "A"
        Attributes = @{ HREF = $link }
        Text = $name
    }
}
function Table
{
    param (
    [Parameter(Mandatory)]
    [object[]]
        $Data,
    [Parameter()]
    [string[]]
        $Properties = "*",
    [Parameter()]
    [hashtable]
        $Attributes = @{ border=2; cellpadding=2; cellspacing=2 }
    )
$bodyText = ""
# Add the header tags
$bodyText += $Properties.foreach{TH $_}
# Add the rows
$bodyText += foreach ($row in $Data)
    {
        TR (-join $Properties.Foreach{ TD ($row.$\_) } )
    }

    $table = [Element] @{
        Tag = "Table"
        Attributes = $Attributes
        Text = $bodyText
    }
$table
}
function TH { ([Element] @{ Tag = "TH" ; Text = $args.foreach{$_} -join " " }) }
function TR { ([Element] @{ Tag = "TR" ; Text = $args.foreach{$_} -join " " }) }
function TD { ([Element] @{ Tag = "TD" ; Text = $args.foreach{$_} -join " " }) }
function Style

{
    return [Element] @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```
