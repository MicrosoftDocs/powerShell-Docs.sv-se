---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Skapa anpassade typer med hjälp av PowerShell-klasser
ms.openlocfilehash: c2c50fb65ce4931fcf6ae529b4146df391c831c4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810437"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="74703-103">Skapa anpassade typer med hjälp av PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="74703-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="74703-104">PowerShell 5,0 har lagt till möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantiska objekt som andra objektorienterade programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="74703-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="74703-105">Målet är att göra det möjligt för utvecklare och IT-proffs att använda PowerShell för ett bredare utbud av användnings fall, förenkla utvecklingen av PowerShell-artefakter (till exempel DSC-resurser) och påskynda täckning av hanterings ytor.</span><span class="sxs-lookup"><span data-stu-id="74703-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="74703-106">Scenarier som stöds i den här versionen</span><span class="sxs-lookup"><span data-stu-id="74703-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="74703-107">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="74703-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="74703-108">Definiera anpassade typer i PowerShell med välbekanta objektorienterade programmerings konstruktioner, till exempel klasser, egenskaper, metoder osv.</span><span class="sxs-lookup"><span data-stu-id="74703-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="74703-109">Stöd för arv med klassen i PowerShell-och klass bas DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="74703-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="74703-110">Fel söknings typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="74703-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="74703-111">Generera och hantera undantag med hjälp av formella mekanismer och på rätt nivå</span><span class="sxs-lookup"><span data-stu-id="74703-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="74703-112">Deklarera basklass</span><span class="sxs-lookup"><span data-stu-id="74703-112">Declare Base Class</span></span>

<span data-ttu-id="74703-113">Du kan deklarera en PowerShell-klass som bastyp för en annan PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="74703-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="74703-114">Du kan också använda befintliga .NET Framework typer som bas klasser:</span><span class="sxs-lookup"><span data-stu-id="74703-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="74703-115">Anropa basklasskonstruktorn</span><span class="sxs-lookup"><span data-stu-id="74703-115">Call Base Class Constructor</span></span>

<span data-ttu-id="74703-116">Om du vill anropa en konstruktor för basklass från en underordnad klass använder du nyckelords **basen**:</span><span class="sxs-lookup"><span data-stu-id="74703-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="74703-117">Om en basklass har en standardkonstruktor (ingen parameter) kan du utelämna ett explicit anrop till konstruktorn:</span><span class="sxs-lookup"><span data-stu-id="74703-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="74703-118">Anropa basklassmetoden</span><span class="sxs-lookup"><span data-stu-id="74703-118">Call Base Class Method</span></span>

<span data-ttu-id="74703-119">Du kan åsidosätta befintliga metoder i underklasser.</span><span class="sxs-lookup"><span data-stu-id="74703-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="74703-120">Gör detta genom att deklarera metoder med samma namn och signatur:</span><span class="sxs-lookup"><span data-stu-id="74703-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="74703-121">För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen ( `[baseClass]$this` ) vid anrop:</span><span class="sxs-lookup"><span data-stu-id="74703-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="74703-122">Alla PowerShell-metoder är virtuella.</span><span class="sxs-lookup"><span data-stu-id="74703-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="74703-123">Du kan dölja icke-virtuella .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning genom att deklarera metoder med samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="74703-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="74703-124">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="74703-124">Declare Implemented Interface</span></span>

<span data-ttu-id="74703-125">Du kan deklarera implementerade gränssnitt efter grund typer, eller omedelbart efter ett kolon (:), om det inte finns någon bastyp angiven.</span><span class="sxs-lookup"><span data-stu-id="74703-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="74703-126">Avgränsa alla typnamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="74703-126">Separate all type names by using commas.</span></span> <span data-ttu-id="74703-127">Det liknar C#-syntax.</span><span class="sxs-lookup"><span data-stu-id="74703-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="74703-128">Nya språk funktioner i PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="74703-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="74703-129">PowerShell 5,0 introducerar följande nya språk element i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="74703-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="74703-130">Klass nyckelord</span><span class="sxs-lookup"><span data-stu-id="74703-130">Class keyword</span></span>

<span data-ttu-id="74703-131">`class`Nyckelordet definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="74703-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="74703-132">Detta är en True .NET Framework-typ.</span><span class="sxs-lookup"><span data-stu-id="74703-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="74703-133">Klass medlemmar är offentliga, men endast offentliga inom modulens omfattning.</span><span class="sxs-lookup"><span data-stu-id="74703-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="74703-134">Det går inte att referera till typnamn som en sträng (till exempel `New-Object` fungerar inte) och i den här versionen kan du inte använda en typ literal (till exempel `[MyClass]` ) utanför skriptet eller modulens fil som klassen är definierad i.</span><span class="sxs-lookup"><span data-stu-id="74703-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="74703-135">Räkna upp nyckelord och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="74703-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="74703-136">Stöd för `enum` nyckelordet har lagts till, vilket använder ny rad som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="74703-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="74703-137">För närvarande kan du inte definiera en uppräknare i termer av sig själv.</span><span class="sxs-lookup"><span data-stu-id="74703-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="74703-138">Du kan dock initiera en uppräkning i termer av en annan uppräkning, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="74703-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="74703-139">Bastypen kan inte heller anges. Det är alltid `[int]` .</span><span class="sxs-lookup"><span data-stu-id="74703-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="74703-140">Ett uppräknings värde måste vara en konstant för en parse.</span><span class="sxs-lookup"><span data-stu-id="74703-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="74703-141">Det går inte att ställa in det till resultatet av ett anropat kommando.</span><span class="sxs-lookup"><span data-stu-id="74703-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="74703-142">Uppräkningar stöder aritmetiska åtgärder, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="74703-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="74703-143">Importera – Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="74703-143">Import-DscResource</span></span>

<span data-ttu-id="74703-144">`Import-DscResource`är nu ett faktiskt dynamiskt nyckelord.</span><span class="sxs-lookup"><span data-stu-id="74703-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="74703-145">PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet **dscresource Keyword Supports** .</span><span class="sxs-lookup"><span data-stu-id="74703-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="74703-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="74703-146">ImplementingAssembly</span></span>

<span data-ttu-id="74703-147">Ett nytt fält, **ImplementingAssembly**, har lagts till i **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="74703-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="74703-148">Den är inställd på den dynamiska sammansättning som skapats för en skript-modul om skriptet definierar klasser eller den inlästa sammansättningen för binära moduler.</span><span class="sxs-lookup"><span data-stu-id="74703-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="74703-149">Den anges inte när **ModuleType** är **manifest**.</span><span class="sxs-lookup"><span data-stu-id="74703-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="74703-150">Reflektion i fältet **ImplementingAssembly** identifierar resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="74703-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="74703-151">Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="74703-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="74703-152">Fält med initierare:</span><span class="sxs-lookup"><span data-stu-id="74703-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="74703-153">`Static`stöds.</span><span class="sxs-lookup"><span data-stu-id="74703-153">`Static` is supported.</span></span> <span data-ttu-id="74703-154">Det fungerar som ett attribut, precis som med typ begränsningar.</span><span class="sxs-lookup"><span data-stu-id="74703-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="74703-155">Det kan anges i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="74703-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="74703-156">En typ är valfri.</span><span class="sxs-lookup"><span data-stu-id="74703-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="74703-157">Alla medlemmar är offentliga.</span><span class="sxs-lookup"><span data-stu-id="74703-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="74703-158">Konstruktörer och instansiering</span><span class="sxs-lookup"><span data-stu-id="74703-158">Constructors and instantiation</span></span>

<span data-ttu-id="74703-159">PowerShell-klasser kan ha konstruktorer.</span><span class="sxs-lookup"><span data-stu-id="74703-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="74703-160">De har samma namn som klassen.</span><span class="sxs-lookup"><span data-stu-id="74703-160">They have the same name as their class.</span></span> <span data-ttu-id="74703-161">Konstruktörer kan vara överbelastade.</span><span class="sxs-lookup"><span data-stu-id="74703-161">Constructors can be overloaded.</span></span> <span data-ttu-id="74703-162">Statiska konstruktorer stöds.</span><span class="sxs-lookup"><span data-stu-id="74703-162">Static constructors are supported.</span></span> <span data-ttu-id="74703-163">Egenskaper med initierings uttryck initieras innan all kod körs i en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="74703-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="74703-164">Statiska egenskaper initieras före bröd texten i en statisk konstruktor och instans egenskaper initieras före bröd texten i den icke-statiska konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="74703-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="74703-165">För närvarande finns det ingen syntax för att anropa en konstruktor från en annan konstruktor (t \# . ex. C-syntaxen ": den här ()").</span><span class="sxs-lookup"><span data-stu-id="74703-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="74703-166">Lösningen är att definiera en gemensam `Init()` metod.</span><span class="sxs-lookup"><span data-stu-id="74703-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="74703-167">Skapa instanser</span><span class="sxs-lookup"><span data-stu-id="74703-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="74703-168">I PowerShell 5,0 `New-Object` fungerar inte med klasser som definierats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74703-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="74703-169">Dessutom är typ namnet bara synligt i lexikalt, vilket innebär att det inte är synligt utanför modulen eller skriptet som definierar klassen.</span><span class="sxs-lookup"><span data-stu-id="74703-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="74703-170">Funktioner kan returnera instanser av en klass som definierats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74703-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="74703-171">Dessa instanser fungerar utanför modulen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="74703-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="74703-172">Instansieras med hjälp av Standardkonstruktorn.</span><span class="sxs-lookup"><span data-stu-id="74703-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="74703-173">Anropa en konstruktor med en parameter</span><span class="sxs-lookup"><span data-stu-id="74703-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="74703-174">Skicka en matris till en konstruktor med flera parametrar.</span><span class="sxs-lookup"><span data-stu-id="74703-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="74703-175">Metoden pseudo-static `new()` fungerar med .net-typer, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="74703-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="74703-176">Identifiera konstruktörer</span><span class="sxs-lookup"><span data-stu-id="74703-176">Discovering constructors</span></span>

<span data-ttu-id="74703-177">Du kan nu se överbelastningar i konstruktorn med `Get-Member` eller som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="74703-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="74703-178">`Get-Member -Static`visar konstruktorer, så att du kan visa överlagringar på samma sätt som andra metoder.</span><span class="sxs-lookup"><span data-stu-id="74703-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="74703-179">Prestanda för den här syntaxen är också avsevärt snabbare än `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="74703-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="74703-180">Metoder</span><span class="sxs-lookup"><span data-stu-id="74703-180">Methods</span></span>

<span data-ttu-id="74703-181">En PowerShell-klass metod implementeras som en **script block** som bara har ett slut block.</span><span class="sxs-lookup"><span data-stu-id="74703-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="74703-182">Alla metoder är offentliga.</span><span class="sxs-lookup"><span data-stu-id="74703-182">All methods are public.</span></span> <span data-ttu-id="74703-183">Nedan visas ett exempel på hur du definierar en metod med namnet **doSomething**.</span><span class="sxs-lookup"><span data-stu-id="74703-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="74703-184">Metod anrop:</span><span class="sxs-lookup"><span data-stu-id="74703-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="74703-185">Överlagrade metoder stöds också.</span><span class="sxs-lookup"><span data-stu-id="74703-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="74703-186">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="74703-186">Properties</span></span>

<span data-ttu-id="74703-187">Alla egenskaper är offentliga.</span><span class="sxs-lookup"><span data-stu-id="74703-187">All properties are public.</span></span> <span data-ttu-id="74703-188">Egenskaperna kräver antingen en ny rad eller ett semikolon.</span><span class="sxs-lookup"><span data-stu-id="74703-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="74703-189">Om ingen objekt typ anges är egenskaps typen objekt.</span><span class="sxs-lookup"><span data-stu-id="74703-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="74703-190">Egenskaper som använder omvandlings-eller arguments omvandlings attribut (som `[ValidateSet("aaa")]` ) fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="74703-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="74703-191">Dold</span><span class="sxs-lookup"><span data-stu-id="74703-191">Hidden</span></span>

<span data-ttu-id="74703-192">Ett nytt nyckelord, `Hidden` , har lagts till.</span><span class="sxs-lookup"><span data-stu-id="74703-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="74703-193">`Hidden`kan tillämpas på egenskaper och metoder (inklusive konstruktorer).</span><span class="sxs-lookup"><span data-stu-id="74703-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="74703-194">Dolda medlemmar är offentliga, men visas inte i resultatet `Get-Member` om inte `-Force` parametern läggs till.</span><span class="sxs-lookup"><span data-stu-id="74703-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="74703-195">Dolda medlemmar tas inte med när tabbtangenten Slutför eller använder IntelliSense om inte slut för ande sker i klassen som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="74703-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="74703-196">Ett nytt attribut, **system. Management. Automation. HiddenAttribute** har lagts till så att C- \# koden kan ha samma semantik i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="74703-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="74703-197">Retur typer</span><span class="sxs-lookup"><span data-stu-id="74703-197">Return types</span></span>

<span data-ttu-id="74703-198">Retur typen är ett kontrakt.</span><span class="sxs-lookup"><span data-stu-id="74703-198">Return type is a contract.</span></span> <span data-ttu-id="74703-199">Returvärdet konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="74703-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="74703-200">Om ingen returtyp anges är retur typen **void**.</span><span class="sxs-lookup"><span data-stu-id="74703-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="74703-201">Det finns ingen strömning av objekt.</span><span class="sxs-lookup"><span data-stu-id="74703-201">There is no streaming of objects.</span></span> <span data-ttu-id="74703-202">Det går inte att skriva objekt till pipelinen antingen avsiktligt eller av misstag.</span><span class="sxs-lookup"><span data-stu-id="74703-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="74703-203">Attribut</span><span class="sxs-lookup"><span data-stu-id="74703-203">Attributes</span></span>

<span data-ttu-id="74703-204">Två nya attribut, **dscresource Keyword Supports** och **DscProperty** har lagts till.</span><span class="sxs-lookup"><span data-stu-id="74703-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="74703-205">Lexikalt omfång av variabler</span><span class="sxs-lookup"><span data-stu-id="74703-205">Lexical scoping of variables</span></span>

<span data-ttu-id="74703-206">Nedan visas ett exempel på hur lexikalt scope fungerar i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="74703-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="74703-207">Exempel från slut punkt till slut punkt</span><span class="sxs-lookup"><span data-stu-id="74703-207">End-to-End Example</span></span>

<span data-ttu-id="74703-208">I följande exempel skapas vissa anpassade klasser för att implementera ett HTML-dynamiskt Style Sheet-språk (DSL).</span><span class="sxs-lookup"><span data-stu-id="74703-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="74703-209">Sedan lägger exemplet till hjälp funktioner för att skapa olika element typer som en del av klassen element, till exempel rubrik format och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.</span><span class="sxs-lookup"><span data-stu-id="74703-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
