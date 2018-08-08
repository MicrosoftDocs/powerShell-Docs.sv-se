---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a96a4a58dafa01fb43f5bdffb52ef833816148e7
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587303"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="e1fc5-102">Nya språkfunktioner i PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e1fc5-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="e1fc5-103">PowerShell 5.0 innehåller följande nya språkelement i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e1fc5-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="e1fc5-104">Nyckelord för klass</span><span class="sxs-lookup"><span data-stu-id="e1fc5-104">Class keyword</span></span>

<span data-ttu-id="e1fc5-105">Den **klass** nyckelordet definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="e1fc5-106">Det här är en äkta .NET Framework-typen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="e1fc5-107">Klassmedlemmar är offentliga men endast allmänna inom omfånget för modulen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="e1fc5-108">Du kan inte referera till namnet på som en sträng (till exempel `New-Object` inte fungerar), och i den här versionen kan du inte använda en literal typ (till exempel `[MyClass]`) utanför skriptmodul/filen som klassen definierats.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="e1fc5-109">Nyckelordet enum och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="e1fc5-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="e1fc5-110">Stöd för den **enum** nyckelordet har lagts till, som använder ny rad som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="e1fc5-111">Aktuella begränsningar: du kan inte definiera en uppräknare när det gäller själva, men du kan initiera en uppräkning när det gäller en annan uppräkning som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="e1fc5-112">Dessutom kan bastypen för närvarande inte anges; Det är alltid [int].</span><span class="sxs-lookup"><span data-stu-id="e1fc5-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="e1fc5-113">En uppräknarvärdets måste vara en konstant för parsa tid; Du kan inte ange den till resultatet av en anropade kommandot.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="e1fc5-114">Uppräkningar stöder aritmetiska åtgärder som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="e1fc5-115">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="e1fc5-115">Import-DscResource</span></span>

<span data-ttu-id="e1fc5-116">**Import-DscResource** är nu ett sant dynamisk nyckelord.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="e1fc5-117">PowerShell Parsar rotmodul för den angivna modulen, söker efter klasser som innehåller den **DscResource** attribut.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="e1fc5-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="e1fc5-118">ImplementingAssembly</span></span>

<span data-ttu-id="e1fc5-119">Ett nytt fält, **ImplementingAssembly**, har lagts till ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="e1fc5-120">Den är inställd på dynamisk sammansättning som skapats för en skriptmodul om skriptet definierar klasser eller läsa in sammansättningen för binära moduler.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="e1fc5-121">Det har inte angetts när ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="e1fc5-122">Reflektion på den **ImplementingAssembly** fältet har identifierat resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="e1fc5-123">Det innebär att du kan identifiera resurser som skrivits i PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="e1fc5-124">Fält med fältparameterbindningar:</span><span class="sxs-lookup"><span data-stu-id="e1fc5-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="e1fc5-125">Statisk stöds. den fungerar som ett attribut som göra Typbegränsningar, så att den kan anges i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="e1fc5-126">En typ är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="e1fc5-127">Alla medlemmar är offentliga.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="e1fc5-128">Konstruktorerna och instansiering</span><span class="sxs-lookup"><span data-stu-id="e1fc5-128">Constructors and instantiation</span></span>

<span data-ttu-id="e1fc5-129">Windows PowerShell-klasser kan ha konstruktorer; de har samma namn som deras klass.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="e1fc5-130">Konstruktorer kan vara överbelastad.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-130">Constructors can be overloaded.</span></span> <span data-ttu-id="e1fc5-131">Statiska konstruktörer stöds.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-131">Static constructors are supported.</span></span> <span data-ttu-id="e1fc5-132">Egenskaper med initieringen uttryck initieras innan du kör kod i en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="e1fc5-133">Statiska egenskaper initieras innan innehållet i en statisk konstruktor och instansegenskaperna initieras innan innehållet i konstruktorn icke-statisk.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="e1fc5-134">För närvarande finns ingen syntax för att anropa en konstruktor från en annan konstruktor (som C\# syntax ”: this()").</span><span class="sxs-lookup"><span data-stu-id="e1fc5-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="e1fc5-135">Lösningen är att definiera en vanlig Init-metod.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="e1fc5-136">Här följer några sätt att initierar klasser i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="e1fc5-137">Instansiera genom att använda Standardkonstruktorn.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="e1fc5-138">Observera att New-Object inte stöds i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="e1fc5-139">Anropa en konstruktör med en parameter</span><span class="sxs-lookup"><span data-stu-id="e1fc5-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="e1fc5-140">Skicka en matris till en konstruktör med flera parametrar</span><span class="sxs-lookup"><span data-stu-id="e1fc5-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="e1fc5-141">I den här versionen fungerar inte New-Object med klasser som definierats i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="e1fc5-142">Även den här versionen är visas namnet på bara lexically, vilket innebär att det inte är synligt utanför modulen eller skript som definierar klassen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="e1fc5-143">Funktioner kan returnera instanser av en klass som definierats i Windows PowerShell och instanser som fungerar bra utanför modulen eller skript.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="e1fc5-144">`Get-Member -Static` Visar en lista över konstruktorer, så att du kan visa överlagringar som någon annan metod.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="e1fc5-145">Prestanda för den här syntaxen är också betydligt snabbare än New-Object.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="e1fc5-146">Pseudo statisk metod som heter **nya** fungerar med .NET-typer, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="e1fc5-147">Du kan nu se konstruktor överlagringar med Get-Member eller som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="e1fc5-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="e1fc5-148">Metoder</span><span class="sxs-lookup"><span data-stu-id="e1fc5-148">Methods</span></span>

<span data-ttu-id="e1fc5-149">En Windows PowerShell-klassmetod implementeras som en ScriptBlock med endast ett end-block.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="e1fc5-150">Alla metoder är offentliga.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-150">All methods are public.</span></span> <span data-ttu-id="e1fc5-151">Följande visar ett exempel på att definiera en metod med namnet **EnMetod**.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="e1fc5-152">Metodanropet:</span><span class="sxs-lookup"><span data-stu-id="e1fc5-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="e1fc5-153">Överlagrade metoder – det vill säga de som är samma namn som en befintlig metod, men hjälp av deras angivna värden--stöds också.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="e1fc5-154">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="e1fc5-154">Properties</span></span>

<span data-ttu-id="e1fc5-155">Alla egenskaper är offentliga.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-155">All properties are public.</span></span> <span data-ttu-id="e1fc5-156">Egenskaper för kräver en ny rad eller semikolon.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="e1fc5-157">Om ingen typ har angetts är egenskapstypen objekt.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="e1fc5-158">Egenskaper som använder verifiering attribut eller argumentet omvandling attribut (t.ex. `[ValidateSet("aaa")]`) fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="e1fc5-159">Dold</span><span class="sxs-lookup"><span data-stu-id="e1fc5-159">Hidden</span></span>

<span data-ttu-id="e1fc5-160">Ett nytt nyckelord, **Hidden**, har lagts till.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="e1fc5-161">**Dolda** kan tillämpas på Egenskaper och metoder (inklusive konstruktorer).</span><span class="sxs-lookup"><span data-stu-id="e1fc5-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="e1fc5-162">Dolda medlemmar är offentliga men inte visas i utdata från Get-Member såvida inte-Force parameter har lagts till.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="e1fc5-163">Dolda medlemmar ingår inte när fliken slutföra eller med Intellisense såvida inte slutförs som uppstår i den klass som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="e1fc5-164">Ett nytt attribut, **System.Management.Automation.HiddenAttribute** har lagts till så att C#-kod kan ha samma semantik i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="e1fc5-165">Returnera typer</span><span class="sxs-lookup"><span data-stu-id="e1fc5-165">Return types</span></span>

<span data-ttu-id="e1fc5-166">Returtypen är ett kontrakt; Det returnera värdet konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="e1fc5-167">Om ingen returtyp anges är returtypen ogiltiga.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="e1fc5-168">Det finns ingen strömning av objekt. objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="e1fc5-169">Attribut</span><span class="sxs-lookup"><span data-stu-id="e1fc5-169">Attributes</span></span>

<span data-ttu-id="e1fc5-170">Två nya attribut **DscResource** och **DscProperty** har lagts till.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="e1fc5-171">Lexikal ange omfång för variabler</span><span class="sxs-lookup"><span data-stu-id="e1fc5-171">Lexical scoping of variables</span></span>

<span data-ttu-id="e1fc5-172">Nedan visas ett exempel på hur lexikal målgrupp fungerar i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="e1fc5-173">Slutpunkt till slutpunkt-exempel</span><span class="sxs-lookup"><span data-stu-id="e1fc5-173">End-to-End Example</span></span>

<span data-ttu-id="e1fc5-174">I följande exempel skapas flera nya, anpassade klasser för att implementera en HTML-dynamiska språk (DSL).</span><span class="sxs-lookup"><span data-stu-id="e1fc5-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="e1fc5-175">I exempel läggs sedan hjälpfunktioner för att skapa specifika elementtyper som en del av elementklassen, till exempel rubrik och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.</span><span class="sxs-lookup"><span data-stu-id="e1fc5-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
