---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skapa anpassade typer med hjälp av PowerShell-klasser
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470928"
---
# <a name="creating-custom-types-using-powershell-classes"></a>Skapa anpassade typer med hjälp av PowerShell-klasser

PowerShell 5.0 har lagts till med möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formella syntax och semantik som andra objektorienterat programmeringsspråk. Målet är så att utvecklare och IT-proffs kan använda PowerShell för ett bredare spektrum av användningsfall, förenkla utvecklingen av PowerShell-artefakter (t.ex DSC-resurser) och påskynda täckning av hantering av Surface-enheter.

## <a name="supported-scenarios-in-this-release"></a>Scenarier som stöds i den här versionen

- Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket
- Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterad programming konstruktioner som klasser, egenskaper, metoder, osv.
- Arv support med klassen i PowerShell och klassen grundläggande DSC-resurs
- Felsöka typer med hjälp av PowerShell-språket
- Skapa och hantera undantag genom att använda formella mekanismer och på rätt nivå

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

Du kan också använda befintliga .NET Framework-typer som basklasser:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a>Anropa basklasskonstruktorn

För att anropa en Basklasskonstruktorn från en underklass, använder du nyckelordet **grundläggande**:

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

Om en basklass har en standardkonstruktor (ingen parameter), kan du utesluta ett explicit konstruktorsanrop:

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

För att anropa basklass från åsidosatt implementeringar, konvertera till basklassen (`[baseClass]$this`) på anrop:

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

Alla PowerShell-metoder är virtuella. Du kan dölja icke-virtuell .NET-metoder i en underklass med hjälp av samma syntax som du gör en åsidosättning genom att deklarera metoder med samma namn och signatur.

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

Du kan deklarera implementerade gränssnitt efter bastyper eller omedelbart efter ett kolon (:), om det finns inga bastypen som angetts. Separera namn för alla med kommatecken. Den liknar C# syntax.

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

## <a name="new-language-features-in-powershell-50"></a>Nya språkfunktioner i PowerShell 5.0

PowerShell 5.0 innehåller följande nya språkliga elementen i PowerShell:

### <a name="class-keyword"></a>Nyckelord för klass

Den `class` nyckelordet definierar en ny klass. Det här är en äkta .NET Framework-typen. Klassmedlemmar är offentliga men endast allmänna inom omfånget för modulen. Du kan inte referera till namnet på som en sträng (till exempel `New-Object` inte fungerar), och i den här versionen kan du inte använda en literal typ (till exempel `[MyClass]`) utanför filen skript eller modulen som klassen definierats.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Nyckelordet enum och uppräkningar

Stöd för den `enum` nyckelordet har lagts till, som använder ny rad som avgränsare. Du kan inte för närvarande kan definiera en uppräknare när det gäller själva. Dock kan du initiera en uppräkning när det gäller en annan uppräkning som visas i följande exempel. Bastypen kan inte anges; Det är alltid `[int]`.

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

En uppräknare-värdet måste vara en konstant för parsa tid. Du kan inte ange den till resultatet av en anropade kommandot.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Uppräkningar stöder aritmetiska åtgärder som visas i följande exempel.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Import-DscResource

`Import-DscResource` är nu ett sant dynamisk nyckelord. PowerShell Parsar rotmodul för den angivna modulen, söker efter klasser som innehåller den **DscResource** attribut.

### <a name="implementingassembly"></a>ImplementingAssembly

Ett nytt fält, **ImplementingAssembly**, har lagts till **ModuleInfo**. Den är inställd på dynamisk sammansättning som skapats för en skriptmodul om skriptet definierar klasser eller läsa in sammansättningen för binära moduler. Det har inte angetts när **ModuleType** är **Manifest**.

Reflektion på den **ImplementingAssembly** fältet har identifierat resurser i en modul. Det innebär att du kan identifiera resurser som skrivits i PowerShell eller andra hanterade språk.

Fält med fältparameterbindningar:

```powershell
[int] $i = 5
```

`Static` stöds. Den fungerar som ett attribut som gör Typbegränsningar. Det kan anges i valfri ordning.

```powershell
static [int] $count = 0
```

En typ är valfritt.

```powershell
$s = "hello"
```

Alla medlemmar är offentliga.

### <a name="constructors-and-instantiation"></a>Konstruktorerna och instansiering

PowerShell-klasser kan ha konstruktorer. De har samma namn som deras klass. Konstruktorer kan vara överbelastad. Statiska konstruktörer stöds. Egenskaper med initieringen uttryck initieras innan du kör kod i en konstruktor. Statiska egenskaper initieras innan innehållet i en statisk konstruktor och instansegenskaperna initieras innan innehållet i konstruktorn icke-statisk. För närvarande finns ingen syntax för att anropa en konstruktor från en annan konstruktor (som C\# syntax ”: this()"). Lösningen är att definiera ett vanligt `Init()` metod.

#### <a name="creating-instances"></a>Skapa instanser

> [!NOTE]
> I PowerShell 5.0 `New-Object` fungerar inte med klasser som definieras i PowerShell. Dessutom visas typnamnet bara lexically, vilket innebär att det inte är synligt utanför modulen eller skript som definierar klassen. Funktioner kan returnera instanser av en klass som definierats i PowerShell. Dessa instanser fungerar utanför modulen eller skript.

1. Instansiera genom att använda Standardkonstruktorn.

   ```powershell
   $a = [MyClass]::new()
   ```

1. Anropa en konstruktör med en parameter

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. Skicka en matris till en konstruktör med flera parametrar.

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

Metoden pseudo statiska `new()` fungerar med .NET-typer, som visas i följande exempel.

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a>Identifiera konstruktorer

Du kan nu se konstruktor överlagringar med `Get-Member`, eller som visas i det här exemplet:

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

`Get-Member -Static` Visar en lista över konstruktorer, så att du kan visa överlagringar som någon annan metod. Prestanda för den här syntaxen är också betydligt snabbare än `New-Object`.

### <a name="methods"></a>Metoder

En PowerShell-klassmetod implementeras som en **ScriptBlock** som har endast ett end-block. Alla metoder är offentliga. Följande visar ett exempel på att definiera en metod med namnet **EnMetod**.

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

Överlagrade metoder stöds också.

### <a name="properties"></a>Egenskaper

Alla egenskaper är offentliga. Egenskaper för kräver en ny rad eller semikolon. Om ingen typ har angetts är egenskapstypen objekt.

Egenskaper som använder verifiering eller argumentet omvandling attribut (t.ex. `[ValidateSet("aaa")]`) fungerar som förväntat.

### <a name="hidden"></a>Hidden

Ett nytt nyckelord, `Hidden`, har lagts till. `Hidden` kan tillämpas på Egenskaper och metoder (inklusive konstruktorer).

Dolda medlemmar är offentliga men inte visas i utdata från `Get-Member` såvida inte den `-Force` parameter har lagts till. Dolda medlemmar ingår inte när fliken slutföra eller med Intellisense såvida inte slutförs som uppstår i den klass som definierar den dolda medlemmen.

Ett nytt attribut, **System.Management.Automation.HiddenAttribute** har lagts till så att C\# kod kan ha samma semantik i PowerShell.

### <a name="return-types"></a>Returnera typer

Returtypen är ett kontrakt. Det returnera värdet konverteras till den förväntade typen. Om ingen returtyp anges returtypen är **void**. Det finns ingen strömning av objekt. Objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.

### <a name="attributes"></a>Attribut

Två nya attribut **DscResource** och **DscProperty** har lagts till.

### <a name="lexical-scoping-of-variables"></a>Lexikal ange omfång för variabler

Nedan visas ett exempel på hur lexikal målgrupp fungerar i den här versionen.

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

I följande exempel skapar några egna klasser för att implementera en HTML-dynamiska språk (DSL). I exempel läggs sedan hjälpfunktioner för att skapa specifika elementtyper som en del av elementklassen, till exempel rubrik och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.

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
