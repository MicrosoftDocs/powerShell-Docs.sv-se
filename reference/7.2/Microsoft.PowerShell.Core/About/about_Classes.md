---
description: Beskriver hur du kan använda klasser för att skapa dina egna anpassade typer.
Locale: en-US
ms.date: 09/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_classes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes
ms.openlocfilehash: 15e56d00d607f7129be4ffd0a515bd237951f512
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710669"
---
# <a name="about-classes"></a><span data-ttu-id="b0fed-103">Om klasser</span><span class="sxs-lookup"><span data-stu-id="b0fed-103">About Classes</span></span>

## <a name="short-description"></a><span data-ttu-id="b0fed-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0fed-104">Short description</span></span>
<span data-ttu-id="b0fed-105">Beskriver hur du kan använda klasser för att skapa dina egna anpassade typer.</span><span class="sxs-lookup"><span data-stu-id="b0fed-105">Describes how you can use classes to create your own custom types.</span></span>

## <a name="long-description"></a><span data-ttu-id="b0fed-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0fed-106">Long description</span></span>

<span data-ttu-id="b0fed-107">PowerShell 5,0 lägger till en formell syntax för att definiera klasser och andra användardefinierade typer.</span><span class="sxs-lookup"><span data-stu-id="b0fed-107">PowerShell 5.0 adds a formal syntax to define classes and other user-defined types.</span></span> <span data-ttu-id="b0fed-108">Genom att lägga till klasser kan utvecklare och IT-proffs använda PowerShell för en större mängd användnings fall.</span><span class="sxs-lookup"><span data-stu-id="b0fed-108">The addition of classes enables developers and IT professionals to embrace PowerShell for a wider range of use cases.</span></span> <span data-ttu-id="b0fed-109">Det fören klar utvecklingen av PowerShell-artefakter och påskyndar täckningen av hanterings ytor.</span><span class="sxs-lookup"><span data-stu-id="b0fed-109">It simplifies development of PowerShell artifacts and accelerates coverage of management surfaces.</span></span>

<span data-ttu-id="b0fed-110">En klass deklaration är en skiss som används för att skapa instanser av objekt vid körning.</span><span class="sxs-lookup"><span data-stu-id="b0fed-110">A class declaration is a blueprint used to create instances of objects at run time.</span></span> <span data-ttu-id="b0fed-111">När du definierar en klass är klass namnet namnet på typen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-111">When you define a class, the class name is the name of the type.</span></span> <span data-ttu-id="b0fed-112">Om du till exempel deklarerar en klass med namnet **Device** och initierar en variabel `$dev` till en ny instans av **enhet**, `$dev` är ett objekt eller en instans av typen **enhet**.</span><span class="sxs-lookup"><span data-stu-id="b0fed-112">For example, if you declare a class named **Device** and initialize a variable `$dev` to a new instance of **Device**, `$dev` is an object or instance of type **Device**.</span></span> <span data-ttu-id="b0fed-113">Varje instans av **enheten** kan ha olika värden i egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="b0fed-113">Each instance of **Device** can have different values in its properties.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="b0fed-114">Scenarier som stöds</span><span class="sxs-lookup"><span data-stu-id="b0fed-114">Supported scenarios</span></span>

- <span data-ttu-id="b0fed-115">Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterade programmerings semantik som klasser, egenskaper, metoder, arv osv.</span><span class="sxs-lookup"><span data-stu-id="b0fed-115">Define custom types in PowerShell using familiar object-oriented programming semantics like classes, properties, methods, inheritance, etc.</span></span>
- <span data-ttu-id="b0fed-116">Fel söknings typer med PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="b0fed-116">Debug types using the PowerShell language.</span></span>
- <span data-ttu-id="b0fed-117">Generera och hantera undantag med hjälp av formella mekanismer.</span><span class="sxs-lookup"><span data-stu-id="b0fed-117">Generate and handle exceptions using formal mechanisms.</span></span>
- <span data-ttu-id="b0fed-118">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="b0fed-118">Define DSC resources and their associated types by using the PowerShell language.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0fed-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0fed-119">Syntax</span></span>

<span data-ttu-id="b0fed-120">Klasser deklareras med hjälp av följande syntax:</span><span class="sxs-lookup"><span data-stu-id="b0fed-120">Classes are declared using the following syntax:</span></span>

```syntax
class <class-name> [: [<base-class>][,<interface-list]] {
    [[<attribute>] [hidden] [static] <property-definition> ...]
    [<class-name>([<constructor-argument-list>])
      {<constructor-statement-list>} ...]
    [[<attribute>] [hidden] [static] <method-definition> ...]
}
```

<span data-ttu-id="b0fed-121">Klasser instansieras med hjälp av någon av följande syntaxer:</span><span class="sxs-lookup"><span data-stu-id="b0fed-121">Classes are instantiated using either of the following syntaxes:</span></span>

```syntax
[$<variable-name> =] New-Object -TypeName <class-name> [
  [-ArgumentList] <constructor-argument-list>]
```

```syntax
[$<variable-name> =] [<class-name>]::new([<constructor-argument-list>])
```

> [!NOTE]
> <span data-ttu-id="b0fed-122">När du använder `[<class-name>]::new()` syntaxen är hakparenteser runt klass namnet obligatoriska.</span><span class="sxs-lookup"><span data-stu-id="b0fed-122">When using the `[<class-name>]::new()` syntax, brackets around the class name are mandatory.</span></span> <span data-ttu-id="b0fed-123">Hakparenteserna signalerar en typ definition för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0fed-123">The brackets signal a type definition for PowerShell.</span></span>

### <a name="example-syntax-and-usage"></a><span data-ttu-id="b0fed-124">Exempel på syntax och användning</span><span class="sxs-lookup"><span data-stu-id="b0fed-124">Example syntax and usage</span></span>

<span data-ttu-id="b0fed-125">I det här exemplet visas den minsta syntax som krävs för att skapa en användbar klass.</span><span class="sxs-lookup"><span data-stu-id="b0fed-125">This example shows the minimum syntax needed to create a usable class.</span></span>

```powershell
class Device {
    [string]$Brand
}

$dev = [Device]::new()
$dev.Brand = "Microsoft"
$dev
```

```Output
Brand
-----
Microsoft
```

## <a name="class-properties"></a><span data-ttu-id="b0fed-126">Klass egenskaper</span><span class="sxs-lookup"><span data-stu-id="b0fed-126">Class properties</span></span>

<span data-ttu-id="b0fed-127">Egenskaper är variabler som deklareras i klass omfånget.</span><span class="sxs-lookup"><span data-stu-id="b0fed-127">Properties are variables declared at class scope.</span></span> <span data-ttu-id="b0fed-128">En egenskap kan vara av valfri inbyggd typ eller instans av en annan klass.</span><span class="sxs-lookup"><span data-stu-id="b0fed-128">A property may be of any built-in type or an instance of another class.</span></span> <span data-ttu-id="b0fed-129">Klasser har ingen begränsning i antalet egenskaper som de har.</span><span class="sxs-lookup"><span data-stu-id="b0fed-129">Classes have no restriction in the number of properties they have.</span></span>

### <a name="example-class-with-simple-properties"></a><span data-ttu-id="b0fed-130">Exempel klass med enkla egenskaper</span><span class="sxs-lookup"><span data-stu-id="b0fed-130">Example class with simple properties</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

$device = [Device]::new()
$device.Brand = "Microsoft"
$device.Model = "Surface Pro 4"
$device.VendorSku = "5072641000"

$device
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-complex-types-in-class-properties"></a><span data-ttu-id="b0fed-131">Exempel på komplexa typer i klass egenskaper</span><span class="sxs-lookup"><span data-stu-id="b0fed-131">Example complex types in class properties</span></span>

<span data-ttu-id="b0fed-132">I det här exemplet definieras en tom **rack** klass med hjälp av **enhets** klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-132">This example defines an empty **Rack** class using the **Device** class.</span></span> <span data-ttu-id="b0fed-133">I exemplen nedan visas hur du lägger till enheter i racket och hur du börjar med ett förinställt rack.</span><span class="sxs-lookup"><span data-stu-id="b0fed-133">The examples, following this one, show how to add devices to the rack and how to start with a pre-loaded rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
}

class Rack {
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new(8)

}

$rack = [Rack]::new()

$rack
```

```Output

Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, $null, $null...}


```

## <a name="class-methods"></a><span data-ttu-id="b0fed-134">Klass metoder</span><span class="sxs-lookup"><span data-stu-id="b0fed-134">Class methods</span></span>

<span data-ttu-id="b0fed-135">Metoder definierar de åtgärder som en klass kan utföra.</span><span class="sxs-lookup"><span data-stu-id="b0fed-135">Methods define the actions that a class can perform.</span></span> <span data-ttu-id="b0fed-136">Metoder kan ta parametrar som tillhandahåller indata.</span><span class="sxs-lookup"><span data-stu-id="b0fed-136">Methods may take parameters that provide input data.</span></span> <span data-ttu-id="b0fed-137">Metoder kan returnera utdata.</span><span class="sxs-lookup"><span data-stu-id="b0fed-137">Methods can return output.</span></span> <span data-ttu-id="b0fed-138">Data som returneras av en metod kan vara alla definierade data typer.</span><span class="sxs-lookup"><span data-stu-id="b0fed-138">Data returned by a method can be any defined data type.</span></span>

<span data-ttu-id="b0fed-139">När du definierar en metod för en klass refererar du till det aktuella Class-objektet med hjälp av den `$this` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="b0fed-139">When defining a method for a class, you reference the current class object by using the `$this` automatic variable.</span></span> <span data-ttu-id="b0fed-140">På så sätt kan du få åtkomst till egenskaper och andra metoder som definierats i den aktuella klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-140">This allows you to access properties and other methods defined in the current class.</span></span>

### <a name="example-simple-class-with-properties-and-methods"></a><span data-ttu-id="b0fed-141">Exempel på en enkel klass med egenskaper och metoder</span><span class="sxs-lookup"><span data-stu-id="b0fed-141">Example simple class with properties and methods</span></span>

<span data-ttu-id="b0fed-142">Utöka **rack** klassen för att lägga till och ta bort enheter i eller från den.</span><span class="sxs-lookup"><span data-stu-id="b0fed-142">Extending the **Rack** class to add and remove devices to or from it.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    [string]ToString(){
        return ("{0}|{1}|{2}" -f $this.Brand, $this.Model, $this.VendorSku)
    }
}

class Rack {
    [int]$Slots = 8
    [string]$Brand
    [string]$Model
    [string]$VendorSku
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void]RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }

    [int[]] GetAvailableSlots(){
        [int]$i = 0
        return @($this.Devices.foreach{ if($_ -eq $null){$i}; $i++})
    }
}

$rack = [Rack]::new()

$surface = [Device]::new()
$surface.Brand = "Microsoft"
$surface.Model = "Surface Pro 4"
$surface.VendorSku = "5072641000"

$rack.AddDevice($surface, 2)

$rack
$rack.GetAvailableSlots()
```

```Output

Slots     : 8
Brand     :
Model     :
VendorSku :
AssetId   :
Devices   : {$null, $null, Microsoft|Surface Pro 4|5072641000, $null...}

0
1
3
4
5
6
7

```

## <a name="output-in-class-methods"></a><span data-ttu-id="b0fed-143">Utdata i klass metoder</span><span class="sxs-lookup"><span data-stu-id="b0fed-143">Output in class methods</span></span>

<span data-ttu-id="b0fed-144">Metoder bör ha en definierad returtyp.</span><span class="sxs-lookup"><span data-stu-id="b0fed-144">Methods should have a return type defined.</span></span> <span data-ttu-id="b0fed-145">Om en metod inte returnerar utdata ska utdatatypen vara `[void]` .</span><span class="sxs-lookup"><span data-stu-id="b0fed-145">If a method doesn't return output, then the output type should be `[void]`.</span></span>

<span data-ttu-id="b0fed-146">I klass metoder skickas inga objekt till pipelinen förutom de som nämns i `return` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-146">In class methods, no objects get sent to the pipeline except those mentioned in the `return` statement.</span></span> <span data-ttu-id="b0fed-147">Det finns inga oavsiktliga utdata till pipelinen från koden.</span><span class="sxs-lookup"><span data-stu-id="b0fed-147">There's no accidental output to the pipeline from the code.</span></span>

> [!NOTE]
> <span data-ttu-id="b0fed-148">Detta är i grunden annorlunda än hur PowerShell-funktioner hanterar utdata, där allt går till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-148">This is fundamentally different from how PowerShell functions handle output, where everything goes to the pipeline.</span></span>

<span data-ttu-id="b0fed-149">Icke-avslutande fel som skrivs till fel strömmen inifrån en klass metod skickas inte genom.</span><span class="sxs-lookup"><span data-stu-id="b0fed-149">Non-terminating errors written to the error stream from inside a class method are not passed through.</span></span> <span data-ttu-id="b0fed-150">Du måste använda `throw` för att visa ett avslutande fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="b0fed-150">You must use `throw` to surface a terminating error.</span></span>
<span data-ttu-id="b0fed-151">Med hjälp av `Write-*` cmdletarna kan du fortfarande skriva till PowerShell: s utgående strömmar från en klass metod.</span><span class="sxs-lookup"><span data-stu-id="b0fed-151">Using the `Write-*` cmdlets, you can still write to PowerShell's output streams from within a class method.</span></span> <span data-ttu-id="b0fed-152">Detta bör dock undvikas så att metoden avger objekt med endast `return` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-152">However, this should be avoided so that the method emits objects using only the `return` statement.</span></span>

### <a name="method-output"></a><span data-ttu-id="b0fed-153">Metodens utdata</span><span class="sxs-lookup"><span data-stu-id="b0fed-153">Method output</span></span>

<span data-ttu-id="b0fed-154">Det här exemplet visar inga oavsiktliga utdata till pipelinen från klass metoder, förutom i `return` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-154">This example demonstrates no accidental output to the pipeline from class methods, except on the `return` statement.</span></span>

```powershell
class FunWithIntegers
{
    [int[]]$Integers = 0..10

    [int[]]GetOddIntegers(){
        return $this.Integers.Where({ ($_ % 2) })
    }

    [void] GetEvenIntegers(){
        # this following line doesn't go to the pipeline
        $this.Integers.Where({ ($_ % 2) -eq 0})
    }

    [string]SayHello(){
        # this following line doesn't go to the pipeline
        "Good Morning"

        # this line goes to the pipeline
        return "Hello World"
    }
}

$ints = [FunWithIntegers]::new()
$ints.GetOddIntegers()
$ints.GetEvenIntegers()
$ints.SayHello()
```

```Output
1
3
5
7
9
Hello World

```

## <a name="constructor"></a><span data-ttu-id="b0fed-155">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="b0fed-155">Constructor</span></span>

<span data-ttu-id="b0fed-156">Med konstruktorer kan du ange standardvärden och validera objekt logik när du skapar instansen av klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-156">Constructors enable you to set default values and validate object logic at the moment of creating the instance of the class.</span></span> <span data-ttu-id="b0fed-157">Konstruktörer har samma namn som klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-157">Constructors have the same name as the class.</span></span> <span data-ttu-id="b0fed-158">Konstruktörer kan ha argument för att initiera data medlemmar för det nya objektet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-158">Constructors might have arguments, to initialize the data members of the new object.</span></span>

<span data-ttu-id="b0fed-159">Klassen kan ha noll eller flera definierade konstruktorer.</span><span class="sxs-lookup"><span data-stu-id="b0fed-159">The class can have zero or more constructors defined.</span></span> <span data-ttu-id="b0fed-160">Om ingen konstruktor har definierats tilldelas klassen en standardkonstruktor utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="b0fed-160">If no constructor is defined, the class is given a default parameterless constructor.</span></span> <span data-ttu-id="b0fed-161">Den här konstruktorn initierar alla medlemmar till sina standardvärden.</span><span class="sxs-lookup"><span data-stu-id="b0fed-161">This constructor initializes all members to their default values.</span></span> <span data-ttu-id="b0fed-162">Objekt typer och strängar får null-värden.</span><span class="sxs-lookup"><span data-stu-id="b0fed-162">Object types and strings are given null values.</span></span> <span data-ttu-id="b0fed-163">När du definierar konstruktorn skapas ingen standardkonstruktor utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="b0fed-163">When you define constructor, no default parameterless constructor is created.</span></span> <span data-ttu-id="b0fed-164">Skapa en parameter lös konstruktor om en sådan krävs.</span><span class="sxs-lookup"><span data-stu-id="b0fed-164">Create a parameterless constructor if one is needed.</span></span>

### <a name="constructor-basic-syntax"></a><span data-ttu-id="b0fed-165">Grundläggande syntax för konstruktor</span><span class="sxs-lookup"><span data-stu-id="b0fed-165">Constructor basic syntax</span></span>

<span data-ttu-id="b0fed-166">I det här exemplet definieras enhets klassen med egenskaper och en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="b0fed-166">In this example, the Device class is defined with properties and a constructor.</span></span>
<span data-ttu-id="b0fed-167">Om du vill använda den här klassen måste användaren ange värden för parametrarna som anges i konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="b0fed-167">To use this class, the user is required to provide values for the parameters listed in the constructor.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$surface
```

```Output
Brand     Model         VendorSku
-----     -----         ---------
Microsoft Surface Pro 4 5072641000
```

### <a name="example-with-multiple-constructors"></a><span data-ttu-id="b0fed-168">Exempel med flera konstruktorer</span><span class="sxs-lookup"><span data-stu-id="b0fed-168">Example with multiple constructors</span></span>

<span data-ttu-id="b0fed-169">I det här exemplet definieras **enhets** klassen med egenskaper, en standardkonstruktor och en konstruktor för att initiera instansen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-169">In this example, the **Device** class is defined with properties, a default constructor, and a constructor to initialize the instance.</span></span>

<span data-ttu-id="b0fed-170">Standardkonstruktorn anger **varumärket** **Odefinierad** och lämnar **modell** och **leverantörs-SKU** med null-värden.</span><span class="sxs-lookup"><span data-stu-id="b0fed-170">The default constructor sets the **brand** to **Undefined**, and leaves **model** and **vendor-sku** with null values.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
    [string]$VendorSku

    Device(){
        $this.Brand = 'Undefined'
    }

    Device(
        [string]$b,
        [string]$m,
        [string]$vsk
    ){
        $this.Brand = $b
        $this.Model = $m
        $this.VendorSku = $vsk
    }
}

[Device]$somedevice = [Device]::new()
[Device]$surface = [Device]::new("Microsoft", "Surface Pro 4", "5072641000")

$somedevice
$surface
```

```Output
Brand       Model           VendorSku
-----       -----           ---------
Undefined
Microsoft   Surface Pro 4   5072641000
```

## <a name="hidden-attribute"></a><span data-ttu-id="b0fed-171">Dolt attribut</span><span class="sxs-lookup"><span data-stu-id="b0fed-171">Hidden attribute</span></span>

<span data-ttu-id="b0fed-172">`hidden`Attributet döljer en egenskap eller metod.</span><span class="sxs-lookup"><span data-stu-id="b0fed-172">The `hidden` attribute hides a property or method.</span></span> <span data-ttu-id="b0fed-173">Egenskapen eller metoden är fortfarande tillgänglig för användaren och är tillgänglig i alla omfattningar där objektet är tillgängligt.</span><span class="sxs-lookup"><span data-stu-id="b0fed-173">The property or method is still accessible to the user and is available in all scopes in which the object is available.</span></span> <span data-ttu-id="b0fed-174">Dolda medlemmar är dolda från `Get-Member` cmdleten och kan inte visas med hjälp av tabb-slutförande eller IntelliSense utanför klass definitionen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-174">Hidden members are hidden from the `Get-Member` cmdlet and can't be displayed using tab completion or IntelliSense outside the class definition.</span></span>

<span data-ttu-id="b0fed-175">Mer information finns i [About_hidden](About_hidden.md).</span><span class="sxs-lookup"><span data-stu-id="b0fed-175">For more information, see [About_hidden](About_hidden.md).</span></span>

### <a name="example-using-hidden-attributes"></a><span data-ttu-id="b0fed-176">Exempel med dolda attribut</span><span class="sxs-lookup"><span data-stu-id="b0fed-176">Example using hidden attributes</span></span>

<span data-ttu-id="b0fed-177">När ett **rack** objekt skapas, är antalet platser för enheter ett fast värde som inte ska ändras när som helst.</span><span class="sxs-lookup"><span data-stu-id="b0fed-177">When a **Rack** object is created, the number of slots for devices is a fixed value that shouldn't be changed at any time.</span></span> <span data-ttu-id="b0fed-178">Det här värdet är känt vid skapande tillfället.</span><span class="sxs-lookup"><span data-stu-id="b0fed-178">This value is known at creation time.</span></span>

<span data-ttu-id="b0fed-179">Genom att använda attributet dold kan utvecklaren hålla antalet platser dolda och förhindra oavsiktliga ändringar av rackets storlek.</span><span class="sxs-lookup"><span data-stu-id="b0fed-179">Using the hidden attribute allows the developer to keep the number of slots hidden and prevents unintentional changes the size of the rack.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    [int] hidden $Slots = 8
    [string]$Brand
    [string]$Model
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)
    }
}

[Rack]$r1 = [Rack]::new("Microsoft", "Surface Pro 4", 16)

$r1
$r1.Devices.Length
$r1.Slots
```

```Output
Brand     Model         Devices
-----     -----         -------
Microsoft Surface Pro 4 {$null, $null, $null, $null...}
16
16
```

<span data-ttu-id="b0fed-180">Egenskapen anslags **platser** visas inte i `$r1` utdata.</span><span class="sxs-lookup"><span data-stu-id="b0fed-180">Notice **Slots** property isn't shown in `$r1` output.</span></span> <span data-ttu-id="b0fed-181">Storleken ändrades dock av konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="b0fed-181">However, the size was changed by the constructor.</span></span>

## <a name="static-attribute"></a><span data-ttu-id="b0fed-182">Statiskt attribut</span><span class="sxs-lookup"><span data-stu-id="b0fed-182">Static attribute</span></span>

<span data-ttu-id="b0fed-183">`static`Attributet definierar en egenskap eller en metod som finns i klassen och behöver ingen instans.</span><span class="sxs-lookup"><span data-stu-id="b0fed-183">The `static` attribute defines a property or a method that exists in the class and needs no instance.</span></span>

<span data-ttu-id="b0fed-184">En statisk egenskap är alltid tillgänglig, oberoende av klass instansiering.</span><span class="sxs-lookup"><span data-stu-id="b0fed-184">A static property is always available, independent of class instantiation.</span></span> <span data-ttu-id="b0fed-185">En statisk egenskap delas över alla instanser av klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-185">A static property is shared across all instances of the class.</span></span> <span data-ttu-id="b0fed-186">En statisk metod är alltid tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="b0fed-186">A static method is available always.</span></span> <span data-ttu-id="b0fed-187">Alla statiska egenskaper som är aktiva för hela sessions intervallet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-187">All static properties live for the entire session span.</span></span>

### <a name="example-using-static-attributes-and-methods"></a><span data-ttu-id="b0fed-188">Exempel med statiska attribut och metoder</span><span class="sxs-lookup"><span data-stu-id="b0fed-188">Example using static attributes and methods</span></span>

<span data-ttu-id="b0fed-189">Anta att de rack som instansieras här finns i ditt data Center.</span><span class="sxs-lookup"><span data-stu-id="b0fed-189">Assume the racks instantiated here exist in your data center.</span></span> <span data-ttu-id="b0fed-190">Så du vill hålla koll på racken i din kod.</span><span class="sxs-lookup"><span data-stu-id="b0fed-190">So, you would like to keep track of the racks in your code.</span></span>

```powershell
class Device {
    [string]$Brand
    [string]$Model
}

class Rack {
    hidden [int] $Slots = 8
    static [Rack[]]$InstalledRacks = @()
    [string]$Brand
    [string]$Model
    [string]$AssetId
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack ([string]$b, [string]$m, [string]$id, [int]$capacity){
        ## argument validation here

        $this.Brand = $b
        $this.Model = $m
        $this.AssetId = $id
        $this.Slots = $capacity

        ## reset rack size to new capacity
        $this.Devices = [Device[]]::new($this.Slots)

        ## add rack to installed racks
        [Rack]::InstalledRacks += $this
    }

    static [void]PowerOffRacks(){
        foreach ($rack in [Rack]::InstalledRacks) {
            Write-Warning ("Turning off rack: " + ($rack.AssetId))
        }
    }
}
```

### <a name="testing-static-property-and-method-exist"></a><span data-ttu-id="b0fed-191">Testning av statisk egenskap och metod finns</span><span class="sxs-lookup"><span data-stu-id="b0fed-191">Testing static property and method exist</span></span>

```
PS> [Rack]::InstalledRacks.Length
0

PS> [Rack]::PowerOffRacks()

PS> (1..10) | ForEach-Object {
>>   [Rack]::new("Adatum Corporation", "Standard-16",
>>     $_.ToString("Std0000"), 16)
>> } > $null

PS> [Rack]::InstalledRacks.Length
10

PS> [Rack]::InstalledRacks[3]
Brand              Model       AssetId Devices
-----              -----       ------- -------
Adatum Corporation Standard-16 Std0004 {$null, $null, $null, $null...}

PS> [Rack]::PowerOffRacks()
WARNING: Turning off rack: Std0001
WARNING: Turning off rack: Std0002
WARNING: Turning off rack: Std0003
WARNING: Turning off rack: Std0004
WARNING: Turning off rack: Std0005
WARNING: Turning off rack: Std0006
WARNING: Turning off rack: Std0007
WARNING: Turning off rack: Std0008
WARNING: Turning off rack: Std0009
WARNING: Turning off rack: Std0010
```

<span data-ttu-id="b0fed-192">Observera att antalet rack ökar varje gången du kör det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-192">Notice that the number of racks increases each time you run this example.</span></span>

## <a name="property-validation-attributes"></a><span data-ttu-id="b0fed-193">Attribut för egenskaps verifiering</span><span class="sxs-lookup"><span data-stu-id="b0fed-193">Property validation attributes</span></span>

<span data-ttu-id="b0fed-194">Med verifierings attribut kan du testa att värden som ges till egenskaperna uppfyller definierade krav.</span><span class="sxs-lookup"><span data-stu-id="b0fed-194">Validation attributes allow you to test that values given to properties meet defined requirements.</span></span> <span data-ttu-id="b0fed-195">Verifieringen utlöses så snart värdet tilldelas.</span><span class="sxs-lookup"><span data-stu-id="b0fed-195">Validation is triggered the moment that the value is assigned.</span></span> <span data-ttu-id="b0fed-196">Se [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b0fed-196">See [about_functions_advanced_parameters](about_functions_advanced_parameters.md).</span></span>

### <a name="example-using-validation-attributes"></a><span data-ttu-id="b0fed-197">Exempel som använder verifierings-attribut</span><span class="sxs-lookup"><span data-stu-id="b0fed-197">Example using validation attributes</span></span>

```powershell
class Device {
    [ValidateNotNullOrEmpty()][string]$Brand
    [ValidateNotNullOrEmpty()][string]$Model
}

[Device]$dev = [Device]::new()

Write-Output "Testing dev"
$dev

$dev.Brand = ""
```

```Output
Testing dev

Brand Model
----- -----

Exception setting "Brand": "The argument is null or empty. Provide an
argument that is not null or empty, and then try the command again."
At C:\tmp\Untitled-5.ps1:11 char:1
+ $dev.Brand = ""
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [], SetValueInvocationException
    + FullyQualifiedErrorId : ExceptionWhenSetting
```

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="b0fed-198">Arv i PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="b0fed-198">Inheritance in PowerShell classes</span></span>

<span data-ttu-id="b0fed-199">Du kan utöka en klass genom att skapa en ny klass som härleds från en befintlig klass.</span><span class="sxs-lookup"><span data-stu-id="b0fed-199">You can extend a class by creating a new class that derives from an existing class.</span></span> <span data-ttu-id="b0fed-200">Den härledda klassen ärver egenskaperna för Bask Lassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-200">The derived class inherits the properties of the base class.</span></span> <span data-ttu-id="b0fed-201">Du kan lägga till eller åsidosätta metoder och egenskaper efter behov.</span><span class="sxs-lookup"><span data-stu-id="b0fed-201">You can add or override methods and properties as required.</span></span>

<span data-ttu-id="b0fed-202">PowerShell stöder inte flera arv.</span><span class="sxs-lookup"><span data-stu-id="b0fed-202">PowerShell does not support multiple inheritance.</span></span> <span data-ttu-id="b0fed-203">Klasser kan inte ärva från mer än en klass.</span><span class="sxs-lookup"><span data-stu-id="b0fed-203">Classes cannot inherit from more than one class.</span></span> <span data-ttu-id="b0fed-204">Du kan dock använda gränssnitt för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="b0fed-204">However, you can use interfaces for that purpose.</span></span>

<span data-ttu-id="b0fed-205">Arv implementering definieras av `:` operatorn, vilket innebär att den här klassen utökas eller implementeras dessa gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="b0fed-205">Inheritance implementation is defined by the `:` operator; which means to extend this class or implements these interfaces.</span></span> <span data-ttu-id="b0fed-206">Den härledda klassen ska alltid ligga längst till vänster i klass deklarationen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-206">The derived class should always be leftmost in the class declaration.</span></span>

### <a name="example-using-simple-inheritance-syntax"></a><span data-ttu-id="b0fed-207">Exempel med enkel syntax för arv</span><span class="sxs-lookup"><span data-stu-id="b0fed-207">Example using simple inheritance syntax</span></span>

<span data-ttu-id="b0fed-208">Det här exemplet visar den enkla PowerShell-syntaxen för PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="b0fed-208">This example shows the simple PowerShell class inheritance syntax.</span></span>

```powershell
Class Derived : Base {...}
```

<span data-ttu-id="b0fed-209">Det här exemplet visar arv med en gränssnitts deklaration som kommer efter Bask Lassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-209">This example shows inheritance with an interface declaration coming after the base class.</span></span>

```powershell
Class Derived : Base, Interface {...}
```

### <a name="example-of-simple-inheritance-in-powershell-classes"></a><span data-ttu-id="b0fed-210">Exempel på enkelt arv i PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="b0fed-210">Example of simple inheritance in PowerShell classes</span></span>

<span data-ttu-id="b0fed-211">I det här exemplet är de **rack** -och **enhets** klasser som används i de föregående exemplen bättre definierade för: Undvik egenskaps repetitioner, bättre justera gemensamma egenskaper och återanvänd vanliga affärs logik.</span><span class="sxs-lookup"><span data-stu-id="b0fed-211">In this example the **Rack** and **Device** classes used in the previous examples are better defined to: avoid property repetitions, better align common properties, and reuse common business logic.</span></span>

<span data-ttu-id="b0fed-212">De flesta objekt i data centret är företags till gångar, vilket är meningsfullt att börja spåra dem som till gångar.</span><span class="sxs-lookup"><span data-stu-id="b0fed-212">Most objects in the data center are company assets, which makes sense to start tracking them as assets.</span></span> <span data-ttu-id="b0fed-213">Enhets typer definieras av `DeviceType` uppräkningen, se [about_Enum](about_Enum.md) för information om uppräkningar.</span><span class="sxs-lookup"><span data-stu-id="b0fed-213">Device types are defined by the `DeviceType` enumeration, see [about_Enum](about_Enum.md) for details on enumerations.</span></span>

<span data-ttu-id="b0fed-214">I vårt exempel definierar vi bara `Rack` och `ComputeServer` , båda tilläggen i `Device` klassen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-214">In our example, we're only defining `Rack` and `ComputeServer`; both extensions to the `Device` class.</span></span>

```powershell
enum DeviceType {
    Undefined = 0
    Compute = 1
    Storage = 2
    Networking = 4
    Communications = 8
    Power = 16
    Rack = 32
}

class Asset {
    [string]$Brand
    [string]$Model
}

class Device : Asset {
    hidden [DeviceType]$devtype = [DeviceType]::Undefined
    [string]$Status

    [DeviceType] GetDeviceType(){
        return $this.devtype
    }
}

class ComputeServer : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Compute
    [string]$ProcessorIdentifier
    [string]$Hostname
}

class Rack : Device {
    hidden [DeviceType]$devtype = [DeviceType]::Rack
    hidden [int]$Slots = 8

    [string]$Datacenter
    [string]$Location
    [Device[]]$Devices = [Device[]]::new($this.Slots)

    Rack (){
        ## Just create the default rack with 8 slots
    }

    Rack ([int]$s){
        ## Add argument validation logic here
        $this.Devices = [Device[]]::new($s)
    }

    [void] AddDevice([Device]$dev, [int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $dev
    }

    [void] RemoveDevice([int]$slot){
        ## Add argument validation logic here
        $this.Devices[$slot] = $null
    }
}

$FirstRack = [Rack]::new(16)
$FirstRack.Status = "Operational"
$FirstRack.Datacenter = "PNW"
$FirstRack.Location = "F03R02.J10"

(0..15).ForEach({
    $ComputeServer = [ComputeServer]::new()
    $ComputeServer.Brand = "Fabrikam, Inc."       ## Inherited from Asset
    $ComputeServer.Model = "Fbk5040"              ## Inherited from Asset
    $ComputeServer.Status = "Installed"           ## Inherited from Device
    $ComputeServer.ProcessorIdentifier = "x64"    ## ComputeServer
    $ComputeServer.Hostname = ("r1s" + $_.ToString("000")) ## ComputeServer
    $FirstRack.AddDevice($ComputeServer, $_)
  })

$FirstRack
$FirstRack.Devices
```

```Output
Datacenter : PNW
Location   : F03R02.J10
Devices    : {r1s000, r1s001, r1s002, r1s003...}
Status     : Operational
Brand      :
Model      :

ProcessorIdentifier : x64
Hostname            : r1s000
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

ProcessorIdentifier : x64
Hostname            : r1s001
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040

<... content truncated here for brevity ...>

ProcessorIdentifier : x64
Hostname            : r1s015
Status              : Installed
Brand               : Fabrikam, Inc.
Model               : Fbk5040
```

### <a name="calling-base-class-constructors"></a><span data-ttu-id="b0fed-215">Anropa Bask lass konstruktorer</span><span class="sxs-lookup"><span data-stu-id="b0fed-215">Calling base class constructors</span></span>

<span data-ttu-id="b0fed-216">Om du vill anropa en konstruktor för basklass från en underordnad klass lägger du till `base` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-216">To invoke a base class constructor from a subclass, add the `base` keyword.</span></span>

```powershell
class Person {
    [int]$Age

    Person([int]$a)
    {
        $this.Age = $a
    }
}

class Child : Person
{
    [string]$School

    Child([int]$a, [string]$s ) : base($a) {
        $this.School = $s
    }
}

[Child]$littleone = [Child]::new(10, "Silver Fir Elementary School")

$littleone.Age
```

```Output

10
```

### <a name="invoke-base-class-methods"></a><span data-ttu-id="b0fed-217">Anropa Bask lass metoder</span><span class="sxs-lookup"><span data-stu-id="b0fed-217">Invoke base class methods</span></span>

<span data-ttu-id="b0fed-218">Om du vill åsidosätta befintliga metoder i underklasser deklarerar du metoder med samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="b0fed-218">To override existing methods in subclasses, declare methods using the same name and signature.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
}

[ChildClass1]::new().days()
```

```Output

2
```

<span data-ttu-id="b0fed-219">För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen ([BaseClass] $this) vid anrop.</span><span class="sxs-lookup"><span data-stu-id="b0fed-219">To call base class methods from overridden implementations, cast to the base class ([baseclass]$this) on invocation.</span></span>

```powershell
class BaseClass
{
    [int]days() {return 1}
}
class ChildClass1 : BaseClass
{
    [int]days () {return 2}
    [int]basedays() {return ([BaseClass]$this).days()}
}

[ChildClass1]::new().days()
[ChildClass1]::new().basedays()
```

```Output

2
1
```

### <a name="inheriting-from-interfaces"></a><span data-ttu-id="b0fed-220">Ärver från gränssnitt</span><span class="sxs-lookup"><span data-stu-id="b0fed-220">Inheriting from interfaces</span></span>

<span data-ttu-id="b0fed-221">PowerShell-klasser kan implementera ett gränssnitt med samma arvs-syntax som används för att utöka bas klasserna.</span><span class="sxs-lookup"><span data-stu-id="b0fed-221">PowerShell classes can implement an interface using the same inheritance syntax used to extend base classes.</span></span> <span data-ttu-id="b0fed-222">Eftersom gränssnitt tillåter flera arv kan en PowerShell-klass som implementerar ett gränssnitt ärva från flera typer, genom att avgränsa typ namnen efter kolon ( `:` ) med kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="b0fed-222">Because interfaces allow multiple inheritance, a PowerShell class implementing an interface may inherit from multiple types, by separating the type names after the colon (`:`) with commas (`,`).</span></span> <span data-ttu-id="b0fed-223">En PowerShell-klass som implementerar ett gränssnitt måste implementera alla medlemmar i det gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-223">A PowerShell class that implements an interface must implement all the members of that interface.</span></span> <span data-ttu-id="b0fed-224">Att utelämna medlemmar i implementations gränssnittet orsakar ett parsningsfel i skriptet.</span><span class="sxs-lookup"><span data-stu-id="b0fed-224">Omitting the implemention interface members causes a parse-time error in the script.</span></span>

> [!NOTE]
> <span data-ttu-id="b0fed-225">PowerShell stöder för närvarande inte att deklarera nya gränssnitt i PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="b0fed-225">PowerShell does not currently support declaring new interfaces in PowerShell script.</span></span>

```powershell
class MyComparable : System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, System.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

## <a name="importing-classes-from-a-powershell-module"></a><span data-ttu-id="b0fed-226">Importera klasser från en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="b0fed-226">Importing classes from a PowerShell module</span></span>

<span data-ttu-id="b0fed-227">`Import-Module` och `#requires` instruktionen importerar bara modulens funktioner, alias och variabler, som definieras av modulen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-227">`Import-Module` and the `#requires` statement only import the module functions, aliases, and variables, as defined by the module.</span></span> <span data-ttu-id="b0fed-228">Klasser importeras inte.</span><span class="sxs-lookup"><span data-stu-id="b0fed-228">Classes are not imported.</span></span> <span data-ttu-id="b0fed-229">`using module`Instruktionen importerar de klasser som definierats i modulen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-229">The `using module` statement imports the classes defined in the module.</span></span> <span data-ttu-id="b0fed-230">Om modulen inte har lästs in i den aktuella sessionen, `using` Miss lyckas instruktionen.</span><span class="sxs-lookup"><span data-stu-id="b0fed-230">If the module isn't loaded in the current session, the `using` statement fails.</span></span> <span data-ttu-id="b0fed-231">Mer information om `using` instruktionen finns i [about_Using](about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="b0fed-231">For more information about the `using` statement, see [about_Using](about_Using.md).</span></span>

## <a name="the-psreference-type-is-not-supported-with-class-members"></a><span data-ttu-id="b0fed-232">PSReference-typen stöds inte med klass medlemmar</span><span class="sxs-lookup"><span data-stu-id="b0fed-232">The PSReference type is not supported with class members</span></span>

<span data-ttu-id="b0fed-233">Det `[ref]` går inte att använda typen-Cast med en klass medlem tyst.</span><span class="sxs-lookup"><span data-stu-id="b0fed-233">Using the `[ref]` type-cast with a class member silently fails.</span></span> <span data-ttu-id="b0fed-234">Det går inte att använda API: er som använder `[ref]` parametrar med klass medlemmar.</span><span class="sxs-lookup"><span data-stu-id="b0fed-234">APIs that use `[ref]` parameters cannot be used with class members.</span></span> <span data-ttu-id="b0fed-235">**PSReference** har utformats för att stödja com-objekt.</span><span class="sxs-lookup"><span data-stu-id="b0fed-235">The **PSReference** was designed to support COM objects.</span></span> <span data-ttu-id="b0fed-236">COM-objekt har fall där du behöver skicka ett värde i som referens.</span><span class="sxs-lookup"><span data-stu-id="b0fed-236">COM objects have cases where you need to pass a value in by reference.</span></span>

<span data-ttu-id="b0fed-237">Mer information om `[ref]` typen finns i PSReference- [klass](/dotnet/api/system.management.automation.psreference).</span><span class="sxs-lookup"><span data-stu-id="b0fed-237">For more information about the `[ref]` type, see [PSReference Class](/dotnet/api/system.management.automation.psreference).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0fed-238">Se även</span><span class="sxs-lookup"><span data-stu-id="b0fed-238">See also</span></span>

- [<span data-ttu-id="b0fed-239">About_hidden</span><span class="sxs-lookup"><span data-stu-id="b0fed-239">About_hidden</span></span>](About_hidden.md)
- [<span data-ttu-id="b0fed-240">about_Enum</span><span class="sxs-lookup"><span data-stu-id="b0fed-240">about_Enum</span></span>](about_Enum.md)
- [<span data-ttu-id="b0fed-241">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="b0fed-241">about_Language_Keywords</span></span>](about_language_keywords.md)
- [<span data-ttu-id="b0fed-242">about_Methods</span><span class="sxs-lookup"><span data-stu-id="b0fed-242">about_Methods</span></span>](about_methods.md)
- [<span data-ttu-id="b0fed-243">about_Using</span><span class="sxs-lookup"><span data-stu-id="b0fed-243">about_Using</span></span>](about_using.md)