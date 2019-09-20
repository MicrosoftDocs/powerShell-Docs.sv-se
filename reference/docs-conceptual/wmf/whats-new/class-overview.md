---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skapa anpassade typer med hjälp av PowerShell-klasser
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71145203"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Skapa anpassade typer med hjälp av PowerShell-klasser

PowerShell 5,0 har lagt till möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantiska objekt som andra objektorienterade programmeringsspråk. Målet är att göra det möjligt för utvecklare och IT-proffs att använda PowerShell för ett bredare utbud av användnings fall, förenkla utvecklingen av PowerShell-artefakter (till exempel DSC-resurser) och påskynda täckning av hanterings ytor.

## <a name="supported-scenarios-in-this-release"></a>Scenarier som stöds i den här versionen

- Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket
- Definiera anpassade typer i PowerShell med välbekanta objektorienterade programmerings konstruktioner, till exempel klasser, egenskaper, metoder osv.
- Stöd för arv med klassen i PowerShell-och klass bas DSC-resurs
- Fel söknings typer med hjälp av PowerShell-språket
- Generera och hantera undantag med hjälp av formella mekanismer och på rätt nivå

## <a name="declare-base-class"></a>Deklarera basklass

Du kan deklarera en PowerShell-klass som bastyp för en annan PowerShell-klass.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Du kan också använda befintliga .NET Framework typer som bas klasser:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Anropa basklasskonstruktorn

Om du vill anropa en konstruktor för basklass från en underordnad klass använder du nyckelords **basen**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Om en basklass har en standardkonstruktor (ingen parameter) kan du utelämna ett explicit anrop till konstruktorn:

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a>Anropa basklassmetoden

Du kan åsidosätta befintliga metoder i underklasser. Gör detta genom att deklarera metoder med samma namn och signatur:

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen (`[baseClass]$this`) vid anrop:

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

Alla PowerShell-metoder är virtuella. Du kan dölja icke-virtuella .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning genom att deklarera metoder med samma namn och signatur.

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```

### <a name="declare-implemented-interface"></a>Deklarera implementerat gränssnitt

Du kan deklarera implementerade gränssnitt efter grund typer, eller omedelbart efter ett kolon (:), om det inte finns någon bastyp angiven. Avgränsa alla typnamn med kommatecken. Den liknar C# syntax.

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="new-language-features-in-powershell-50"></a>Nya språk funktioner i PowerShell 5,0

PowerShell 5,0 introducerar följande nya språk element i PowerShell:

### <a name="class-keyword"></a>Klass nyckelord

`class` Nyckelordet definierar en ny klass. Detta är en True .NET Framework-typ. Klass medlemmar är offentliga, men endast offentliga inom modulens omfattning. Det går inte att referera till typnamn som en sträng (till exempel `New-Object` fungerar inte) och i den här versionen kan du inte använda en typ literal ( `[MyClass]`till exempel) utanför skriptet eller modulens fil som klassen är definierad i.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Räkna upp nyckelord och uppräkningar

Stöd för `enum` nyckelordet har lagts till, vilket använder ny rad som avgränsare. För närvarande kan du inte definiera en uppräknare i termer av sig själv. Du kan dock initiera en uppräkning i termer av en annan uppräkning, som du ser i följande exempel. Bastypen kan inte heller anges. Det är alltid `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Ett uppräknings värde måste vara en konstant för en parse. Det går inte att ställa in det till resultatet av ett anropat kommando.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Uppräkningar stöder aritmetiska åtgärder, som du ser i följande exempel.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Importera – Dscresource Keyword Supports

`Import-DscResource`är nu ett faktiskt dynamiskt nyckelord. PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet **dscresource Keyword Supports** .

### <a name="implementingassembly"></a>ImplementingAssembly

Ett nytt fält, **ImplementingAssembly**, har lagts till i **ModuleInfo**. Den är inställd på den dynamiska sammansättning som skapats för en skript-modul om skriptet definierar klasser eller den inlästa sammansättningen för binära moduler. Den anges inte när **ModuleType** är **manifest**.

Reflektion i fältet **ImplementingAssembly** identifierar resurser i en modul. Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.

Fält med initierare:

```powershell
[int] $i = 5
```

`Static`stöds. Det fungerar som ett attribut, precis som med typ begränsningar. Det kan anges i valfri ordning.

```powershell
static [int] $count = 0
```

En typ är valfri.

```powershell
$s = "hello"
```

Alla medlemmar är offentliga.

### <a name="constructors-and-instantiation"></a>Konstruktörer och instansiering

PowerShell-klasser kan ha konstruktorer. De har samma namn som klassen. Konstruktörer kan vara överbelastade. Statiska konstruktorer stöds. Egenskaper med initierings uttryck initieras innan all kod körs i en konstruktor. Statiska egenskaper initieras före bröd texten i en statisk konstruktor och instans egenskaper initieras före bröd texten i den icke-statiska konstruktorn. För närvarande finns det ingen syntax för att anropa en konstruktor från en annan konstruktor (t\# . ex. C-syntaxen ": den här ()"). Lösningen är att definiera en gemensam `Init()` metod.

#### <a name="creating-instances"></a>Skapa instanser

> [!NOTE]
> I PowerShell 5,0 `New-Object` fungerar inte med klasser som definierats i PowerShell. Dessutom är typ namnet bara synligt i lexikalt, vilket innebär att det inte är synligt utanför modulen eller skriptet som definierar klassen. Funktioner kan returnera instanser av en klass som definierats i PowerShell. Dessa instanser fungerar utanför modulen eller skriptet.

1. Instansieras med hjälp av Standardkonstruktorn.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Anropa en konstruktor med en parameter

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Skicka en matris till en konstruktor med flera parametrar.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Metoden `new()` pseudo-static fungerar med .net-typer, som du ser i följande exempel.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Identifiera konstruktörer

Du kan nu se överbelastningar i konstruktorn med `Get-Member`eller som visas i det här exemplet:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static`visar konstruktorer, så att du kan visa överlagringar på samma sätt som andra metoder. Prestanda för den här syntaxen är också avsevärt snabbare `New-Object`än.

### <a name="methods"></a>Metoder

En PowerShell-klass metod implementeras som en **script block** som bara har ett slut block. Alla metoder är offentliga. Nedan visas ett exempel på hur du definierar en metod med namnet **doSomething**.

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

Metod anrop:

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

Överlagrade metoder stöds också.

### <a name="properties"></a>Egenskaper

Alla egenskaper är offentliga. Egenskaperna kräver antingen en ny rad eller ett semikolon. Om ingen objekt typ anges är egenskaps typen objekt.

Egenskaper som använder omvandlings-eller arguments omvandlings attribut (som `[ValidateSet("aaa")]`) fungerar som förväntat.

### <a name="hidden"></a>Dölja

Ett nytt nyckelord, `Hidden`, har lagts till. `Hidden`kan tillämpas på egenskaper och metoder (inklusive konstruktorer).

Dolda medlemmar är offentliga, men visas inte i resultatet `Get-Member` `-Force` om inte parametern läggs till. Dolda medlemmar tas inte med när tabbtangenten Slutför eller använder IntelliSense om inte slut för ande sker i klassen som definierar den dolda medlemmen.

Ett nytt attribut, **system. Management. Automation. HiddenAttribute** har lagts till så att C\# -koden kan ha samma semantik i PowerShell.

### <a name="return-types"></a>Retur typer

Retur typen är ett kontrakt. Returvärdet konverteras till den förväntade typen. Om ingen returtyp anges är retur typen **void**. Det finns ingen strömning av objekt. Det går inte att skriva objekt till pipelinen antingen avsiktligt eller av misstag.

### <a name="attributes"></a>Attribut

Två nya attribut, **dscresource Keyword Supports** och **DscProperty** har lagts till.

### <a name="lexical-scoping-of-variables"></a>Lexikalt omfång av variabler

Nedan visas ett exempel på hur lexikalt scope fungerar i den här versionen.

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

## <a name="end-to-end-example"></a>Exempel från slut punkt till slut punkt

I följande exempel skapas vissa anpassade klasser för att implementera ett HTML-dynamiskt Style Sheet-språk (DSL). Sedan lägger exemplet till hjälp funktioner för att skapa olika element typer som en del av klassen element, till exempel rubrik format och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.

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
# These are required because types aren't visible outside of the module.
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
        TR (-join $Properties.Foreach{ TD ($row.$_) } )
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
