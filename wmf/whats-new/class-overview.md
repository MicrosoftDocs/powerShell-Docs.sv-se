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
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="08175-103">Skapa anpassade typer med hjälp av PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="08175-103">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="08175-104">PowerShell 5.0 har lagts till med möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formella syntax och semantik som andra objektorienterat programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="08175-104">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="08175-105">Målet är så att utvecklare och IT-proffs kan använda PowerShell för ett bredare spektrum av användningsfall, förenkla utvecklingen av PowerShell-artefakter (t.ex DSC-resurser) och påskynda täckning av hantering av Surface-enheter.</span><span class="sxs-lookup"><span data-stu-id="08175-105">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="08175-106">Scenarier som stöds i den här versionen</span><span class="sxs-lookup"><span data-stu-id="08175-106">Supported scenarios in this release</span></span>

- <span data-ttu-id="08175-107">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="08175-107">Define DSC resources and their associated types by using the PowerShell language</span></span>
- <span data-ttu-id="08175-108">Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterad programming konstruktioner som klasser, egenskaper, metoder, osv.</span><span class="sxs-lookup"><span data-stu-id="08175-108">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
- <span data-ttu-id="08175-109">Arv support med klassen i PowerShell och klassen grundläggande DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="08175-109">Inheritance support with class in PowerShell and class base DSC resource</span></span>
- <span data-ttu-id="08175-110">Felsöka typer med hjälp av PowerShell-språket</span><span class="sxs-lookup"><span data-stu-id="08175-110">Debug types by using the PowerShell language</span></span>
- <span data-ttu-id="08175-111">Skapa och hantera undantag genom att använda formella mekanismer och på rätt nivå</span><span class="sxs-lookup"><span data-stu-id="08175-111">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

## <a name="declare-base-class"></a><span data-ttu-id="08175-112">Deklarera basklass</span><span class="sxs-lookup"><span data-stu-id="08175-112">Declare Base Class</span></span>

<span data-ttu-id="08175-113">Du kan deklarera en PowerShell-klass som bastyp för en annan PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="08175-113">You can declare a PowerShell class as a base type for another PowerShell class.</span></span>

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

<span data-ttu-id="08175-114">Du kan också använda befintliga .NET Framework-typer som basklasser:</span><span class="sxs-lookup"><span data-stu-id="08175-114">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

### <a name="call-base-class-constructor"></a><span data-ttu-id="08175-115">Anropa basklasskonstruktorn</span><span class="sxs-lookup"><span data-stu-id="08175-115">Call Base Class Constructor</span></span>

<span data-ttu-id="08175-116">För att anropa en Basklasskonstruktorn från en underklass, använder du nyckelordet **grundläggande**:</span><span class="sxs-lookup"><span data-stu-id="08175-116">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="08175-117">Om en basklass har en standardkonstruktor (ingen parameter), kan du utesluta ett explicit konstruktorsanrop:</span><span class="sxs-lookup"><span data-stu-id="08175-117">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-method"></a><span data-ttu-id="08175-118">Anropa basklassmetoden</span><span class="sxs-lookup"><span data-stu-id="08175-118">Call Base Class Method</span></span>

<span data-ttu-id="08175-119">Du kan åsidosätta befintliga metoder i underklasser.</span><span class="sxs-lookup"><span data-stu-id="08175-119">You can override existing methods in subclasses.</span></span> <span data-ttu-id="08175-120">Gör detta genom att deklarera metoder med samma namn och signatur:</span><span class="sxs-lookup"><span data-stu-id="08175-120">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="08175-121">För att anropa basklass från åsidosatt implementeringar, konvertera till basklassen (`[baseClass]$this`) på anrop:</span><span class="sxs-lookup"><span data-stu-id="08175-121">To call base class methods from overridden implementations, cast to the base class (`[baseClass]$this`) on invocation:</span></span>

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

<span data-ttu-id="08175-122">Alla PowerShell-metoder är virtuella.</span><span class="sxs-lookup"><span data-stu-id="08175-122">All PowerShell methods are virtual.</span></span> <span data-ttu-id="08175-123">Du kan dölja icke-virtuell .NET-metoder i en underklass med hjälp av samma syntax som du gör en åsidosättning genom att deklarera metoder med samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="08175-123">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override, by declaring methods with same name and signature.</span></span>

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

### <a name="declare-implemented-interface"></a><span data-ttu-id="08175-124">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="08175-124">Declare Implemented Interface</span></span>

<span data-ttu-id="08175-125">Du kan deklarera implementerade gränssnitt efter bastyper eller omedelbart efter ett kolon (:), om det finns inga bastypen som angetts.</span><span class="sxs-lookup"><span data-stu-id="08175-125">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="08175-126">Separera namn för alla med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="08175-126">Separate all type names by using commas.</span></span> <span data-ttu-id="08175-127">Den liknar C# syntax.</span><span class="sxs-lookup"><span data-stu-id="08175-127">It's similar to C# syntax.</span></span>

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

## <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="08175-128">Nya språkfunktioner i PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="08175-128">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="08175-129">PowerShell 5.0 innehåller följande nya språkliga elementen i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="08175-129">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="08175-130">Nyckelord för klass</span><span class="sxs-lookup"><span data-stu-id="08175-130">Class keyword</span></span>

<span data-ttu-id="08175-131">Den `class` nyckelordet definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="08175-131">The `class` keyword defines a new class.</span></span> <span data-ttu-id="08175-132">Det här är en äkta .NET Framework-typen.</span><span class="sxs-lookup"><span data-stu-id="08175-132">This is a true .NET Framework type.</span></span> <span data-ttu-id="08175-133">Klassmedlemmar är offentliga men endast allmänna inom omfånget för modulen.</span><span class="sxs-lookup"><span data-stu-id="08175-133">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="08175-134">Du kan inte referera till namnet på som en sträng (till exempel `New-Object` inte fungerar), och i den här versionen kan du inte använda en literal typ (till exempel `[MyClass]`) utanför filen skript eller modulen som klassen definierats.</span><span class="sxs-lookup"><span data-stu-id="08175-134">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="08175-135">Nyckelordet enum och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="08175-135">Enum keyword and enumerations</span></span>

<span data-ttu-id="08175-136">Stöd för den `enum` nyckelordet har lagts till, som använder ny rad som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="08175-136">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="08175-137">Du kan inte för närvarande kan definiera en uppräknare när det gäller själva.</span><span class="sxs-lookup"><span data-stu-id="08175-137">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="08175-138">Dock kan du initiera en uppräkning när det gäller en annan uppräkning som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="08175-138">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="08175-139">Bastypen kan inte anges; Det är alltid `[int]`.</span><span class="sxs-lookup"><span data-stu-id="08175-139">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="08175-140">En uppräknare-värdet måste vara en konstant för parsa tid.</span><span class="sxs-lookup"><span data-stu-id="08175-140">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="08175-141">Du kan inte ange den till resultatet av en anropade kommandot.</span><span class="sxs-lookup"><span data-stu-id="08175-141">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="08175-142">Uppräkningar stöder aritmetiska åtgärder som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="08175-142">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="08175-143">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="08175-143">Import-DscResource</span></span>

<span data-ttu-id="08175-144">`Import-DscResource` är nu ett sant dynamisk nyckelord.</span><span class="sxs-lookup"><span data-stu-id="08175-144">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="08175-145">PowerShell Parsar rotmodul för den angivna modulen, söker efter klasser som innehåller den **DscResource** attribut.</span><span class="sxs-lookup"><span data-stu-id="08175-145">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="08175-146">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="08175-146">ImplementingAssembly</span></span>

<span data-ttu-id="08175-147">Ett nytt fält, **ImplementingAssembly**, har lagts till **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="08175-147">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="08175-148">Den är inställd på dynamisk sammansättning som skapats för en skriptmodul om skriptet definierar klasser eller läsa in sammansättningen för binära moduler.</span><span class="sxs-lookup"><span data-stu-id="08175-148">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="08175-149">Det har inte angetts när **ModuleType** är **Manifest**.</span><span class="sxs-lookup"><span data-stu-id="08175-149">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="08175-150">Reflektion på den **ImplementingAssembly** fältet har identifierat resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="08175-150">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="08175-151">Det innebär att du kan identifiera resurser som skrivits i PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="08175-151">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="08175-152">Fält med fältparameterbindningar:</span><span class="sxs-lookup"><span data-stu-id="08175-152">Fields with initializers:</span></span>

```powershell
[int] $i = 5
```

<span data-ttu-id="08175-153">`Static` stöds.</span><span class="sxs-lookup"><span data-stu-id="08175-153">`Static` is supported.</span></span> <span data-ttu-id="08175-154">Den fungerar som ett attribut som gör Typbegränsningar.</span><span class="sxs-lookup"><span data-stu-id="08175-154">It works like an attribute, as do the type constraints.</span></span> <span data-ttu-id="08175-155">Det kan anges i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="08175-155">It can be specified in any order.</span></span>

```powershell
static [int] $count = 0
```

<span data-ttu-id="08175-156">En typ är valfritt.</span><span class="sxs-lookup"><span data-stu-id="08175-156">A type is optional.</span></span>

```powershell
$s = "hello"
```

<span data-ttu-id="08175-157">Alla medlemmar är offentliga.</span><span class="sxs-lookup"><span data-stu-id="08175-157">All members are public.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="08175-158">Konstruktorerna och instansiering</span><span class="sxs-lookup"><span data-stu-id="08175-158">Constructors and instantiation</span></span>

<span data-ttu-id="08175-159">PowerShell-klasser kan ha konstruktorer.</span><span class="sxs-lookup"><span data-stu-id="08175-159">PowerShell classes can have constructors.</span></span> <span data-ttu-id="08175-160">De har samma namn som deras klass.</span><span class="sxs-lookup"><span data-stu-id="08175-160">They have the same name as their class.</span></span> <span data-ttu-id="08175-161">Konstruktorer kan vara överbelastad.</span><span class="sxs-lookup"><span data-stu-id="08175-161">Constructors can be overloaded.</span></span> <span data-ttu-id="08175-162">Statiska konstruktörer stöds.</span><span class="sxs-lookup"><span data-stu-id="08175-162">Static constructors are supported.</span></span> <span data-ttu-id="08175-163">Egenskaper med initieringen uttryck initieras innan du kör kod i en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="08175-163">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="08175-164">Statiska egenskaper initieras innan innehållet i en statisk konstruktor och instansegenskaperna initieras innan innehållet i konstruktorn icke-statisk.</span><span class="sxs-lookup"><span data-stu-id="08175-164">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="08175-165">För närvarande finns ingen syntax för att anropa en konstruktor från en annan konstruktor (som C\# syntax ”: this()").</span><span class="sxs-lookup"><span data-stu-id="08175-165">Currently, there is no syntax for calling a constructor from another constructor (like the C\# syntax ": this()").</span></span> <span data-ttu-id="08175-166">Lösningen är att definiera ett vanligt `Init()` metod.</span><span class="sxs-lookup"><span data-stu-id="08175-166">The workaround is to define a common `Init()` method.</span></span>

#### <a name="creating-instances"></a><span data-ttu-id="08175-167">Skapa instanser</span><span class="sxs-lookup"><span data-stu-id="08175-167">Creating instances</span></span>

> [!NOTE]
> <span data-ttu-id="08175-168">I PowerShell 5.0 `New-Object` fungerar inte med klasser som definieras i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08175-168">In PowerShell 5.0, `New-Object` does not work with classes defined in PowerShell.</span></span> <span data-ttu-id="08175-169">Dessutom visas typnamnet bara lexically, vilket innebär att det inte är synligt utanför modulen eller skript som definierar klassen.</span><span class="sxs-lookup"><span data-stu-id="08175-169">Also, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="08175-170">Funktioner kan returnera instanser av en klass som definierats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08175-170">Functions can return instances of a class defined in PowerShell.</span></span> <span data-ttu-id="08175-171">Dessa instanser fungerar utanför modulen eller skript.</span><span class="sxs-lookup"><span data-stu-id="08175-171">Those instances work outside of the module or script.</span></span>

1. <span data-ttu-id="08175-172">Instansiera genom att använda Standardkonstruktorn.</span><span class="sxs-lookup"><span data-stu-id="08175-172">Instantiating by using the default constructor.</span></span>

   ```powershell
   $a = [MyClass]::new()
   ```

1. <span data-ttu-id="08175-173">Anropa en konstruktör med en parameter</span><span class="sxs-lookup"><span data-stu-id="08175-173">Calling a constructor with a parameter</span></span>

   ```powershell
   $b = [MyClass]::new(42)
   ```

1. <span data-ttu-id="08175-174">Skicka en matris till en konstruktör med flera parametrar.</span><span class="sxs-lookup"><span data-stu-id="08175-174">Passing an array to a constructor with multiple parameters.</span></span>

   ```powershell
   $c = [MyClass]::new(@(42,43,44), "Hello")
   ```

<span data-ttu-id="08175-175">Metoden pseudo statiska `new()` fungerar med .NET-typer, som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="08175-175">The pseudo-static method `new()` works with .NET types, as shown in the following example.</span></span>

```powershell
[hashtable]::new()
```

#### <a name="discovering-constructors"></a><span data-ttu-id="08175-176">Identifiera konstruktorer</span><span class="sxs-lookup"><span data-stu-id="08175-176">Discovering constructors</span></span>

<span data-ttu-id="08175-177">Du kan nu se konstruktor överlagringar med `Get-Member`, eller som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="08175-177">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
PS> [hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

<span data-ttu-id="08175-178">`Get-Member -Static` Visar en lista över konstruktorer, så att du kan visa överlagringar som någon annan metod.</span><span class="sxs-lookup"><span data-stu-id="08175-178">`Get-Member -Static` lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="08175-179">Prestanda för den här syntaxen är också betydligt snabbare än `New-Object`.</span><span class="sxs-lookup"><span data-stu-id="08175-179">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

### <a name="methods"></a><span data-ttu-id="08175-180">Metoder</span><span class="sxs-lookup"><span data-stu-id="08175-180">Methods</span></span>

<span data-ttu-id="08175-181">En PowerShell-klassmetod implementeras som en **ScriptBlock** som har endast ett end-block.</span><span class="sxs-lookup"><span data-stu-id="08175-181">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="08175-182">Alla metoder är offentliga.</span><span class="sxs-lookup"><span data-stu-id="08175-182">All methods are public.</span></span> <span data-ttu-id="08175-183">Följande visar ett exempel på att definiera en metod med namnet **EnMetod**.</span><span class="sxs-lookup"><span data-stu-id="08175-183">The following shows an example of defining a method named **DoSomething**.</span></span>

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

<span data-ttu-id="08175-184">Metodanropet:</span><span class="sxs-lookup"><span data-stu-id="08175-184">Method invocation:</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

<span data-ttu-id="08175-185">Överlagrade metoder stöds också.</span><span class="sxs-lookup"><span data-stu-id="08175-185">Overloaded methods are also supported.</span></span>

### <a name="properties"></a><span data-ttu-id="08175-186">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="08175-186">Properties</span></span>

<span data-ttu-id="08175-187">Alla egenskaper är offentliga.</span><span class="sxs-lookup"><span data-stu-id="08175-187">All properties are public.</span></span> <span data-ttu-id="08175-188">Egenskaper för kräver en ny rad eller semikolon.</span><span class="sxs-lookup"><span data-stu-id="08175-188">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="08175-189">Om ingen typ har angetts är egenskapstypen objekt.</span><span class="sxs-lookup"><span data-stu-id="08175-189">If no object type is specified, the property type is object.</span></span>

<span data-ttu-id="08175-190">Egenskaper som använder verifiering eller argumentet omvandling attribut (t.ex. `[ValidateSet("aaa")]`) fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="08175-190">Properties that use validation or argument transformation attributes (like `[ValidateSet("aaa")]`) work as expected.</span></span>

### <a name="hidden"></a><span data-ttu-id="08175-191">Hidden</span><span class="sxs-lookup"><span data-stu-id="08175-191">Hidden</span></span>

<span data-ttu-id="08175-192">Ett nytt nyckelord, `Hidden`, har lagts till.</span><span class="sxs-lookup"><span data-stu-id="08175-192">A new keyword, `Hidden`, has been added.</span></span> <span data-ttu-id="08175-193">`Hidden` kan tillämpas på Egenskaper och metoder (inklusive konstruktorer).</span><span class="sxs-lookup"><span data-stu-id="08175-193">`Hidden` can be applied to properties and methods (including constructors).</span></span>

<span data-ttu-id="08175-194">Dolda medlemmar är offentliga men inte visas i utdata från `Get-Member` såvida inte den `-Force` parameter har lagts till.</span><span class="sxs-lookup"><span data-stu-id="08175-194">Hidden members are public, but do not appear in the output of `Get-Member` unless the `-Force` parameter is added.</span></span> <span data-ttu-id="08175-195">Dolda medlemmar ingår inte när fliken slutföra eller med Intellisense såvida inte slutförs som uppstår i den klass som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="08175-195">Hidden members are not included when tab completing or using Intellisense unless the completion occurs in the class defining the hidden member.</span></span>

<span data-ttu-id="08175-196">Ett nytt attribut, **System.Management.Automation.HiddenAttribute** har lagts till så att C\# kod kan ha samma semantik i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="08175-196">A new attribute, **System.Management.Automation.HiddenAttribute** has been added so that C\# code can have the same semantics within PowerShell.</span></span>

### <a name="return-types"></a><span data-ttu-id="08175-197">Returnera typer</span><span class="sxs-lookup"><span data-stu-id="08175-197">Return types</span></span>

<span data-ttu-id="08175-198">Returtypen är ett kontrakt.</span><span class="sxs-lookup"><span data-stu-id="08175-198">Return type is a contract.</span></span> <span data-ttu-id="08175-199">Det returnera värdet konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="08175-199">The return value is converted to the expected type.</span></span> <span data-ttu-id="08175-200">Om ingen returtyp anges returtypen är **void**.</span><span class="sxs-lookup"><span data-stu-id="08175-200">If no return type is specified, the return type is **void**.</span></span> <span data-ttu-id="08175-201">Det finns ingen strömning av objekt.</span><span class="sxs-lookup"><span data-stu-id="08175-201">There is no streaming of objects.</span></span> <span data-ttu-id="08175-202">Objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.</span><span class="sxs-lookup"><span data-stu-id="08175-202">Objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="attributes"></a><span data-ttu-id="08175-203">Attribut</span><span class="sxs-lookup"><span data-stu-id="08175-203">Attributes</span></span>

<span data-ttu-id="08175-204">Två nya attribut **DscResource** och **DscProperty** har lagts till.</span><span class="sxs-lookup"><span data-stu-id="08175-204">Two new attributes, **DscResource** and **DscProperty** have been added.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="08175-205">Lexikal ange omfång för variabler</span><span class="sxs-lookup"><span data-stu-id="08175-205">Lexical scoping of variables</span></span>

<span data-ttu-id="08175-206">Nedan visas ett exempel på hur lexikal målgrupp fungerar i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="08175-206">The following shows an example of how lexical scoping works in this release.</span></span>

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

## <a name="end-to-end-example"></a><span data-ttu-id="08175-207">Slutpunkt till slutpunkt-exempel</span><span class="sxs-lookup"><span data-stu-id="08175-207">End-to-End Example</span></span>

<span data-ttu-id="08175-208">I följande exempel skapar några egna klasser för att implementera en HTML-dynamiska språk (DSL).</span><span class="sxs-lookup"><span data-stu-id="08175-208">The following example creates some custom classes to implement an HTML dynamic style sheet language (DSL).</span></span> <span data-ttu-id="08175-209">I exempel läggs sedan hjälpfunktioner för att skapa specifika elementtyper som en del av elementklassen, till exempel rubrik och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.</span><span class="sxs-lookup"><span data-stu-id="08175-209">Then, the example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
