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
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="d6ea8-102">Funktioner för nya språk i PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d6ea8-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="d6ea8-103">PowerShell 5.0 innehåller följande nya språkelement i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d6ea8-103">PowerShell 5.0 introduces the following new language elements in Windows PowerShell:</span></span>

## <a name="class-keyword"></a><span data-ttu-id="d6ea8-104">Nyckelordet class</span><span class="sxs-lookup"><span data-stu-id="d6ea8-104">Class keyword</span></span>

<span data-ttu-id="d6ea8-105">Den **klassen** nyckelordet definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-105">The **class** keyword defines a new class.</span></span> <span data-ttu-id="d6ea8-106">Detta är sant .NET Framework-typen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-106">This is a true .NET Framework type.</span></span>
<span data-ttu-id="d6ea8-107">Klassmedlemmar är offentlig men bara offentliga inom omfånget för modulen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-107">Class members are public, but only public within the module scope.</span></span>
<span data-ttu-id="d6ea8-108">Du kan inte referera till typnamn som en sträng (till exempel `New-Object` fungerar inte), och i den här versionen kan du inte använda en literal typ (till exempel `[MyClass]`) utanför filen skript-modul som klassen definierats.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-108">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script/module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

## <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="d6ea8-109">Nyckelordet enum och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="d6ea8-109">Enum keyword and enumerations</span></span>

<span data-ttu-id="d6ea8-110">Stöd för den **enum** nyckelordet har lagts till, som använder ny rad som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-110">Support for the **enum** keyword has been added, which uses newline as the delimiter.</span></span>
<span data-ttu-id="d6ea8-111">Aktuella begränsningar: du kan inte definiera en uppräknare i sig själv, men du kan initiera en uppräkning i en annan uppräkning, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-111">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize an enum in terms of another enum, as shown in the following example.</span></span>
<span data-ttu-id="d6ea8-112">Dessutom kan bastypen för närvarande inte anges; Det är alltid [int].</span><span class="sxs-lookup"><span data-stu-id="d6ea8-112">Also, the base type cannot currently be specified; it is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="d6ea8-113">En Uppräkningsvärdet måste vara en konstant för parsa tid; Du kan inte ange den till resultatet för ett anropade kommando.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-113">An enumerator value must be a parse time constant; you cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="d6ea8-114">Uppräkningar stöder beräkningar, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-114">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

## <a name="import-dscresource"></a><span data-ttu-id="d6ea8-115">Importera DscResource</span><span class="sxs-lookup"><span data-stu-id="d6ea8-115">Import-DscResource</span></span>

<span data-ttu-id="d6ea8-116">**Importera DscResource** är nu ett true dynamiska nyckelord.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-116">**Import-DscResource** is now a true dynamic keyword.</span></span>
<span data-ttu-id="d6ea8-117">PowerShell Parsar angiven modul rotmodul söker efter klasser som innehåller den **DscResource** attribut.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-117">PowerShell parses the specified module’s root module, searching for classes that contain the **DscResource** attribute.</span></span>

## <a name="implementingassembly"></a><span data-ttu-id="d6ea8-118">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="d6ea8-118">ImplementingAssembly</span></span>

<span data-ttu-id="d6ea8-119">Ett nytt fält **ImplementingAssembly**, har lagts till ModuleInfo.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-119">A new field, **ImplementingAssembly**, has been added to ModuleInfo.</span></span> <span data-ttu-id="d6ea8-120">Den är inställd på dynamisk sammansättning för en skriptmodul skapas om skriptet definierar klasser eller läsa in sammansättningen för binära moduler.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-120">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="d6ea8-121">Den är inte inställd när ModuleType = Manifest.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-121">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="d6ea8-122">Reflektion på den **ImplementingAssembly** fältet identifierar resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-122">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="d6ea8-123">Det innebär att du kan identifiera resurser som skrivits i PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-123">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="d6ea8-124">Fält med initierare:</span><span class="sxs-lookup"><span data-stu-id="d6ea8-124">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="d6ea8-125">Statiskt stöds. den fungerar som ett attribut som gör Typbegränsningar, så den kan anges i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-125">Static is supported; it works like an attribute, as do the type constraints, so it can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="d6ea8-126">En typ är valfritt.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-126">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="d6ea8-127">Alla medlemmar är offentlig.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-127">All members are public.</span></span>

## <a name="constructors-and-instantiation"></a><span data-ttu-id="d6ea8-128">Konstruktorer och instansiering</span><span class="sxs-lookup"><span data-stu-id="d6ea8-128">Constructors and instantiation</span></span>

<span data-ttu-id="d6ea8-129">Windows PowerShell-klasser kan ha konstruktorer; de har samma namn som sin klass.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-129">Windows PowerShell classes can have constructors; they have the same name as their class.</span></span> <span data-ttu-id="d6ea8-130">Konstruktorer kan vara överbelastad.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-130">Constructors can be overloaded.</span></span> <span data-ttu-id="d6ea8-131">Statiska konstruktörer stöds.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-131">Static constructors are supported.</span></span> <span data-ttu-id="d6ea8-132">Egenskaper med initiering uttryck initieras innan du kör någon kod i en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-132">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="d6ea8-133">Statiska egenskaper initieras innan innehållet i en statisk konstruktor och instans egenskaper initieras innan innehållet i icke-statisk konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-133">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="d6ea8-134">För närvarande finns ingen syntax för att anropa en konstruktor från en annan konstruktor (t.ex. C\# syntaxen ”: this()").</span><span class="sxs-lookup"><span data-stu-id="d6ea8-134">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="d6ea8-135">Lösningen är att definiera en vanlig Init-metod.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-135">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="d6ea8-136">Följande är sätt initierar klasser i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-136">The following are ways of instantiating classes in this release.</span></span>

<span data-ttu-id="d6ea8-137">En instans skapades av genom att använda Standardkonstruktorn.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-137">Instantiating by using the default constructor.</span></span> <span data-ttu-id="d6ea8-138">Observera att New-Object inte stöds i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-138">Note that New-Object is not supported in this release.</span></span>

```powershell
$a = [MyClass]::new()
```

<span data-ttu-id="d6ea8-139">Anropar en konstruktor med en parameter</span><span class="sxs-lookup"><span data-stu-id="d6ea8-139">Calling a constructor with a parameter</span></span>

```powershell
$b = [MyClass]::new(42)
```

<span data-ttu-id="d6ea8-140">Skicka en matris till en konstruktor med flera parametrar</span><span class="sxs-lookup"><span data-stu-id="d6ea8-140">Passing an array to a constructor with multiple parameters</span></span>
```powershell
$c = [MyClass]::new(@(42,43,44), "Hello")
```

<span data-ttu-id="d6ea8-141">I den här versionen fungerar inte New-Object med klasser som definierats i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-141">In this release, New-Object does not work with classes defined in Windows PowerShell.</span></span> <span data-ttu-id="d6ea8-142">Även för den här versionen visas typnamnet bara lexically, vilket innebär att den inte är synlig utanför modul eller skript som definierar klassen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-142">Also for this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="d6ea8-143">Funktioner som kan returnera instanser av en klass som definieras i Windows PowerShell och instanser fungerar bra utanför modul eller skript.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-143">Functions can return instances of a class defined in Windows PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="d6ea8-144">`Get-Member -Static` Visar en lista över konstruktorer, så att du kan visa överlagringar som någon annan metod.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-144">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="d6ea8-145">Prestanda för den här syntaxen är också betydligt snabbare än New-Object.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-145">The performance of this syntax is also considerably faster than New-Object.</span></span>

<span data-ttu-id="d6ea8-146">Startvärden statisk metod med namnet **nya** fungerar med .NET-typer som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-146">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

<span data-ttu-id="d6ea8-147">Du kan nu se konstruktorn överlagringar med Get-medlem eller som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="d6ea8-147">You can now see constructor overloads with Get-Member, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

## <a name="methods"></a><span data-ttu-id="d6ea8-148">Metoder</span><span class="sxs-lookup"><span data-stu-id="d6ea8-148">Methods</span></span>

<span data-ttu-id="d6ea8-149">En metod för Windows PowerShell-klass implementeras som en ScriptBlock som har endast ett end-block.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-149">A Windows PowerShell class method is implemented as a ScriptBlock that has only an end block.</span></span> <span data-ttu-id="d6ea8-150">Alla metoder är offentlig.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-150">All methods are public.</span></span> <span data-ttu-id="d6ea8-151">Följande är ett exempel på att definiera en metod med namnet **EnMetod**.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-151">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="d6ea8-152">Metodanropet:</span><span class="sxs-lookup"><span data-stu-id="d6ea8-152">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="d6ea8-153">Överlagrade metoder – det vill säga de som har samma namn som en befintlig metod men hjälp av de angivna värdena--stöds också.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-153">Overloaded methods--that is, those that are named the same as an existing method, but differentiated by their specified values--are also supported.</span></span>

## <a name="properties"></a><span data-ttu-id="d6ea8-154">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d6ea8-154">Properties</span></span>

<span data-ttu-id="d6ea8-155">Alla egenskaper är offentlig.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-155">All properties are public.</span></span> <span data-ttu-id="d6ea8-156">Egenskaper för kräver en ny rad eller semikolon.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-156">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="d6ea8-157">Om ingen objekttyp har angetts är egenskapstypen-objekt.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-157">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="d6ea8-158">Egenskaper som använder verifiering attribut eller argumentet omvandling attribut (t.ex. `[ValidateSet("aaa")]`) fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-158">Properties that use validation attributes or argument transformation attributes (e.g. `[ValidateSet("aaa")]`) work as expected.</span></span>

## <a name="hidden"></a><span data-ttu-id="d6ea8-159">Dolda</span><span class="sxs-lookup"><span data-stu-id="d6ea8-159">Hidden</span></span>

<span data-ttu-id="d6ea8-160">Ett nytt nyckelord **Hidden**, har lagts till.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-160">A new keyword, **Hidden**, has been added.</span></span> <span data-ttu-id="d6ea8-161">**Dolda** kan tillämpas på Egenskaper och metoder (inklusive konstruktorer).</span><span class="sxs-lookup"><span data-stu-id="d6ea8-161">**Hidden** can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="d6ea8-162">Dolda medlemmar är offentlig men visas inte i utdata för Get-medlem om-Force läggs till.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-162">Hidden members are public, but do not appear in the output of Get-Member unless the -Force parameter is added.</span></span>

<span data-ttu-id="d6ea8-163">Dolda medlemmar ingår inte när fliken slutföra eller med Intellisense om inte slutförs uppstår i den klass som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-163">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="d6ea8-164">Ett nytt attribut **System.Management.Automation.HiddenAttribute** har lagts till så att C#-kod kan ha samma semantik i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-164">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C# code can have the same semantics within Windows PowerShell.</span></span>

## <a name="return-types"></a><span data-ttu-id="d6ea8-165">Returtyper</span><span class="sxs-lookup"><span data-stu-id="d6ea8-165">Return types</span></span>

<span data-ttu-id="d6ea8-166">Returtypen är kontraktet. Returvärdet konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-166">Return type is a contract; the return value is converted to the expected type.</span></span> <span data-ttu-id="d6ea8-167">Om ingen returtyp anges är returtypen void.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-167">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="d6ea8-168">Det finns ingen strömning av objekt. objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-168">There is no streaming of objects; objects cannot be written to the pipeline either intentionally or by accident.</span></span>

## <a name="attributes"></a><span data-ttu-id="d6ea8-169">Attribut</span><span class="sxs-lookup"><span data-stu-id="d6ea8-169">Attributes</span></span>

<span data-ttu-id="d6ea8-170">Två nya attribut **DscResource** och **DscProperty** har lagts till.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-170">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

## <a name="lexical-scoping-of-variables"></a><span data-ttu-id="d6ea8-171">Lexikaliskt omfattningen för variabler</span><span class="sxs-lookup"><span data-stu-id="d6ea8-171">Lexical scoping of variables</span></span>

<span data-ttu-id="d6ea8-172">Nedan visas ett exempel på hur lexikala målgrupp fungerar i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-172">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="d6ea8-173">Slutpunkt till slutpunkt-exempel</span><span class="sxs-lookup"><span data-stu-id="d6ea8-173">End-to-End Example</span></span>

<span data-ttu-id="d6ea8-174">I följande exempel skapar flera nya, anpassade klasser för att implementera en HTML-dynamiska språk (DSL).</span><span class="sxs-lookup"><span data-stu-id="d6ea8-174">The following example creates several new, custom classes to implement an HTML dynamic style sheet language (DSL).</span></span>
<span data-ttu-id="d6ea8-175">I exempel läggs sedan hjälpfunktioner för att skapa specifika elementtyper som en del av elementklassen, till exempel rubrik och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.</span><span class="sxs-lookup"><span data-stu-id="d6ea8-175">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
