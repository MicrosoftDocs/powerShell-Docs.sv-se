---
description: Förklarar hur du skapar objekt i PowerShell.
Locale: en-US
ms.date: 09/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_object_creation?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Object_Creation
ms.openlocfilehash: 72c0d763fe7f3838c8b2ca68930521e24d0e6139
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710573"
---
# <a name="about-object-creation"></a><span data-ttu-id="3701f-103">Om att skapa objekt</span><span class="sxs-lookup"><span data-stu-id="3701f-103">About Object Creation</span></span>

## <a name="short-description"></a><span data-ttu-id="3701f-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="3701f-104">Short description</span></span>

<span data-ttu-id="3701f-105">Förklarar hur du skapar objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3701f-105">Explains how to create objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3701f-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="3701f-106">Long description</span></span>

<span data-ttu-id="3701f-107">Du kan skapa objekt i PowerShell och använda de objekt som du skapar i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="3701f-107">You can create objects in PowerShell and use the objects that you create in commands and scripts.</span></span>

<span data-ttu-id="3701f-108">Det finns många sätt att skapa objekt, den här listan är inte slutgiltig:</span><span class="sxs-lookup"><span data-stu-id="3701f-108">There are many ways to create objects, this list is not definitive:</span></span>

- <span data-ttu-id="3701f-109">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): skapar en instans av ett .NET Framework-objekt eller com-objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-109">[New-Object](xref:Microsoft.PowerShell.Utility.New-Object): Creates an instance of a .NET Framework object or COM object.</span></span>
- <span data-ttu-id="3701f-110">[Importera – CSV](xref:Microsoft.PowerShell.Utility.Import-Csv) /
   [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): skapar anpassade objekt (**PSCustomObject**) från objekt som definieras som kommaavgränsade värden.</span><span class="sxs-lookup"><span data-stu-id="3701f-110">[Import-Csv](xref:Microsoft.PowerShell.Utility.Import-Csv)/
  [ConvertFrom-CSV](xref:Microsoft.PowerShell.Utility.ConvertFrom-Csv): Creates custom objects (**PSCustomObject**) from the items defined as comma separated values.</span></span>
- <span data-ttu-id="3701f-111">[ConvertFrom-JSON](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): skapar anpassade objekt som definieras i JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="3701f-111">[ConvertFrom-Json](xref:Microsoft.PowerShell.Utility.ConvertFrom-Json): Creates custom objects defined in JavaScript Object Notation (JSON).</span></span>
- <span data-ttu-id="3701f-112">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): skapar anpassade objekt som definieras som nyckel värdes par.</span><span class="sxs-lookup"><span data-stu-id="3701f-112">[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData): Creates custom objects defined as key value pairs.</span></span>
- <span data-ttu-id="3701f-113">[Tilläggs typ](xref:Microsoft.PowerShell.Utility.Add-Type): gör att du kan definiera en klass i din PowerShell-session som du kan instansiera med `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="3701f-113">[Add-Type](xref:Microsoft.PowerShell.Utility.Add-Type): Allows you to define a class in your PowerShell session that you can instantiate with `New-Object`.</span></span>
- <span data-ttu-id="3701f-114">[Ny modul](xref:Microsoft.PowerShell.Core.New-Module): parametern **AsCustomObject** skapar ett anpassat objekt som du definierar med hjälp av skript block.</span><span class="sxs-lookup"><span data-stu-id="3701f-114">[New-Module](xref:Microsoft.PowerShell.Core.New-Module): The **AsCustomObject** parameter creates a custom object you define using script block.</span></span>
- <span data-ttu-id="3701f-115">[Lägg till medlem](xref:Microsoft.PowerShell.Utility.Add-Member): lägger till egenskaper i befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-115">[Add-Member](xref:Microsoft.PowerShell.Utility.Add-Member): Adds properties to existing objects.</span></span> <span data-ttu-id="3701f-116">Du kan använda `Add-Member` för att skapa ett anpassat objekt av en enkel typ, t `[System.Int32]` . ex..</span><span class="sxs-lookup"><span data-stu-id="3701f-116">You can use `Add-Member` to create a custom object out of a simple type, like `[System.Int32]`.</span></span>
- <span data-ttu-id="3701f-117">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): väljer Egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-117">[Select-Object](xref:Microsoft.PowerShell.Utility.Select-Object): Selects properties on an object.</span></span> <span data-ttu-id="3701f-118">Du kan använda `Select-Object` för att skapa anpassade och beräknade egenskaper för ett redan instansierat objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-118">You can use `Select-Object` to create custom and calculated properties on an already instantiated object.</span></span>

<span data-ttu-id="3701f-119">Följande ytterligare metoder beskrivs i den här artikeln:</span><span class="sxs-lookup"><span data-stu-id="3701f-119">The following additional methods are covered in this article:</span></span>

- <span data-ttu-id="3701f-120">Genom att anropa en bastyps konstruktor med en statisk `new()` metod</span><span class="sxs-lookup"><span data-stu-id="3701f-120">By calling a type's constructor using a static `new()` method</span></span>
- <span data-ttu-id="3701f-121">Av Typecasting hash-tabeller för egenskaps namn och egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="3701f-121">By typecasting hash tables of property names and property values</span></span>

## <a name="static-new-method"></a><span data-ttu-id="3701f-122">Statisk ny ()-metod</span><span class="sxs-lookup"><span data-stu-id="3701f-122">Static new() method</span></span>

<span data-ttu-id="3701f-123">Alla .NET-typer har en `new()` metod som gör att du enkelt kan skapa instanser.</span><span class="sxs-lookup"><span data-stu-id="3701f-123">All .NET types have a `new()` method that allows you to construct instances more easily.</span></span> <span data-ttu-id="3701f-124">Du kan också se alla tillgängliga konstruktorer för en specifik typ.</span><span class="sxs-lookup"><span data-stu-id="3701f-124">You can also see all the available constructors for a given type.</span></span>

<span data-ttu-id="3701f-125">Om du vill se konstruktörer för en typ anger du `new` metod namnet efter typ namnet och trycker på `<ENTER>` .</span><span class="sxs-lookup"><span data-stu-id="3701f-125">To see the constructors for a type, specify the `new` method name after the type name and press `<ENTER>`.</span></span>

```powershell
[System.Uri]::new
```

```Output
OverloadDefinitions
-------------------
uri new(string uriString)
uri new(string uriString, bool dontEscape)
uri new(uri baseUri, string relativeUri, bool dontEscape)
uri new(string uriString, System.UriKind uriKind)
uri new(uri baseUri, string relativeUri)
uri new(uri baseUri, uri relativeUri)
```

<span data-ttu-id="3701f-126">Nu kan du skapa en **system. URI** genom att ange lämplig konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3701f-126">Now, you can create a **System.Uri** by specifying the appropriate constructor.</span></span>

```powershell
[System.Uri]::new("https://www.bing.com")
```

```Output
AbsolutePath   : /
AbsoluteUri    : https://www.bing.com/
LocalPath      : /
Authority      : www.bing.com
...
```

<span data-ttu-id="3701f-127">Du kan använda följande exempel för att avgöra vilka .NET-typer som för närvarande läses in för att skapa en instans.</span><span class="sxs-lookup"><span data-stu-id="3701f-127">You can use the following sample to determine what .NET types are currently loaded for you to instantiate.</span></span>

```powershell
[AppDomain]::CurrentDomain.GetAssemblies() |
  ForEach-Object {
    $_.GetExportedTypes() |
      ForEach-Object { $_.FullName }
  }
```

<span data-ttu-id="3701f-128">Objekt som har skapats med `new()` metoden kanske inte har samma egenskaper som objekt av samma typ som skapas av PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="3701f-128">Objects created using the `new()` method may not have the same properties as objects of the same type that are created by PowerShell cmdlets.</span></span> <span data-ttu-id="3701f-129">PowerShell-cmdletar, providers och utökat typ system kan lägga till extra egenskaper till instansen.</span><span class="sxs-lookup"><span data-stu-id="3701f-129">PowerShell cmdlets, providers, and Extended Type System can add extra properties to the instance.</span></span>

<span data-ttu-id="3701f-130">Till exempel lägger fil Systems leverantören i PowerShell sex **NoteProperty** -värden till **DirectoryInfo** -objektet som returnerades av `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="3701f-130">For example, the FileSystem provider in PowerShell adds six **NoteProperty** values to the **DirectoryInfo** object returned by `Get-Item`.</span></span>

```powershell
$PSDirInfo = Get-Item /
$PSDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    6 NoteProperty
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="3701f-131">När du skapar ett **DirectoryInfo** -objekt direkt har det inte dessa sex **NoteProperty** -värden.</span><span class="sxs-lookup"><span data-stu-id="3701f-131">When you create a **DirectoryInfo** object directly, it does not have those six **NoteProperty** values.</span></span>

```powershell
$NewDirInfo = [System.IO.DirectoryInfo]::new('/')
$NewDirInfo | Get-Member | Group-Object MemberType | Select-Object Count, Name
```

```Output
Count Name
----- ----
    4 CodeProperty
   13 Property
    1 ScriptProperty
   18 Method
```

<span data-ttu-id="3701f-132">Mer information om det utökade typ systemet finns i [about_Types.ps1XML](about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="3701f-132">For more information about the Extended Type System, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

<span data-ttu-id="3701f-133">Den här funktionen lades till i PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="3701f-133">This feature was added in PowerShell 5.0</span></span>

## <a name="create-objects-from-hash-tables"></a><span data-ttu-id="3701f-134">Skapa objekt från hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="3701f-134">Create objects from hash tables</span></span>

<span data-ttu-id="3701f-135">Du kan skapa ett objekt från en hash-tabell med egenskaper och egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="3701f-135">You can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="3701f-136">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="3701f-136">The syntax is as follows:</span></span>

```
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="3701f-137">Den här metoden fungerar bara för klasser som har en parameter lös konstruktor.</span><span class="sxs-lookup"><span data-stu-id="3701f-137">This method works only for classes that have a parameterless constructor.</span></span> <span data-ttu-id="3701f-138">Objekt egenskaperna måste vara offentliga och kan anges.</span><span class="sxs-lookup"><span data-stu-id="3701f-138">The object properties must be public and settable.</span></span>

<span data-ttu-id="3701f-139">Den här funktionen har lagts till i PowerShell version 3,0</span><span class="sxs-lookup"><span data-stu-id="3701f-139">This feature was added in PowerShell version 3.0</span></span>

## <a name="create-custom-objects-from-hash-tables"></a><span data-ttu-id="3701f-140">Skapa anpassade objekt från hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="3701f-140">Create custom objects from hash tables</span></span>

<span data-ttu-id="3701f-141">Anpassade objekt är mycket användbara och är enkla att skapa med hjälp av hash-tabell metoden.</span><span class="sxs-lookup"><span data-stu-id="3701f-141">Custom objects are very useful and are easy to create using the hash table method.</span></span> <span data-ttu-id="3701f-142">**PSCustomObject** -klassen har utformats särskilt för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="3701f-142">The **PSCustomObject** class is designed specifically for this purpose.</span></span>

<span data-ttu-id="3701f-143">Anpassade objekt är ett utmärkt sätt att returnera anpassade utdata från en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="3701f-143">Custom objects are an excellent way to return customized output from a function or script.</span></span> <span data-ttu-id="3701f-144">Detta är mer användbart än att returnera formaterade utdata som inte kan formateras om eller skickas till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="3701f-144">This is more useful than returning formatted output that cannot be reformatted or piped to other commands.</span></span>

<span data-ttu-id="3701f-145">Kommandona i `Test-Object function` anger några variabel värden och använder sedan dessa värden för att skapa ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-145">The commands in the `Test-Object function` set some variable values and then use those values to create a custom object.</span></span> <span data-ttu-id="3701f-146">Du kan se att det här objektet används i avsnittet exempel i `Update-Help` Hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3701f-146">You can see this object in use in the example section of the `Update-Help` cmdlet help topic.</span></span>

```powershell
function Test-Object {
  $ModuleName = "PSScheduledJob"
  $HelpCulture = "en-us"
  $HelpVersion = "3.1.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
  $ModuleName = "PSWorkflow"
  $HelpCulture = "en-us"
  $HelpVersion = "3.0.0.0"
  [PSCustomObject]@{
    "ModuleName"=$ModuleName
    "UICulture"=$HelpCulture
    "Version"=$HelpVersion
  }
}
Test-Object
```

<span data-ttu-id="3701f-147">Resultatet av den här funktionen är en samling anpassade objekt som är formaterade som en tabell som standard.</span><span class="sxs-lookup"><span data-stu-id="3701f-147">The output of this function is a collection of custom objects formatted as a table by default.</span></span>

```Output
ModuleName        UICulture      Version
---------         ---------      -------
PSScheduledJob    en-us          3.1.0.0
PSWorkflow        en-us          3.0.0.0
```

<span data-ttu-id="3701f-148">Användare kan hantera egenskaperna för de anpassade objekten precis som med standard objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-148">Users can manage the properties of the custom objects just as they do with standard objects.</span></span>

```powershell
(Test-Object).ModuleName
```

```Output
 PSScheduledJob
 PSWorkflow
```

## <a name="create-non-custom-objects-from-hash-tables"></a><span data-ttu-id="3701f-149">Skapa icke-anpassade objekt från hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="3701f-149">Create non-custom objects from hash tables</span></span>

<span data-ttu-id="3701f-150">Du kan också använda hash-tabeller för att skapa objekt för klasser som inte är anpassade.</span><span class="sxs-lookup"><span data-stu-id="3701f-150">You can also use hash tables to create objects for non-custom classes.</span></span> <span data-ttu-id="3701f-151">När du skapar ett objekt för en icke-anpassad klass, krävs namn områdets kvalificerade typ, men du kan utesluta eventuella initiala **system** namns komponenter.</span><span class="sxs-lookup"><span data-stu-id="3701f-151">When you create an object for a non-custom class, the namespace-qualified type name is required, although you may omit any initial **System** namespace component.</span></span>

<span data-ttu-id="3701f-152">Till exempel skapar följande kommando ett alternativ för Session-objektet.</span><span class="sxs-lookup"><span data-stu-id="3701f-152">For example, the following command creates a session option object.</span></span>

```powershell
[System.Management.Automation.Remoting.PSSessionOption]@{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
```

<span data-ttu-id="3701f-153">Kraven för hash-tabellens funktion, särskilt parameter lösa krav för konstruktorn, eliminerar många befintliga klasser.</span><span class="sxs-lookup"><span data-stu-id="3701f-153">The requirements of the hash table feature, especially the parameterless constructor requirement, eliminate many existing classes.</span></span> <span data-ttu-id="3701f-154">De _flesta PowerShell-alternativklasser är_ dock utformade för att fungera med den här funktionen, samt andra mycket användbara klasser, t. ex. klassen **ProcessStartInfo** .</span><span class="sxs-lookup"><span data-stu-id="3701f-154">However, most PowerShell _option_ classes are designed to work with this feature, as well as other very useful classes, such as the **ProcessStartInfo** class.</span></span>

```powershell
[System.Diagnostics.ProcessStartInfo]@{
  CreateNoWindow="$true"
  Verb="run as"
}
```

```Output
Arguments               :
ArgumentList            : {}
CreateNoWindow          : True
EnvironmentVariables    : {OneDriveConsumer, PROCESSOR_ARCHITECTURE,
                           CommonProgramFiles(x86), APPDATA...}
Environment             : {[OneDriveConsumer, C:\Users\user1\OneDrive],
                           [PROCESSOR_ARCHITECTURE, AMD64],
                           [CommonProgramFiles(x86),
                           C:\Program Files (x86)\Common Files],
                           [APPDATA, C:\Users\user1\AppData\Roaming]...}
RedirectStandardInput   : False
RedirectStandardOutput  : False
RedirectStandardError   : False
...
```

<span data-ttu-id="3701f-155">Du kan också använda funktionen hash-tabell när du anger parameter värden.</span><span class="sxs-lookup"><span data-stu-id="3701f-155">You can also use the hash table feature when setting parameter values.</span></span> <span data-ttu-id="3701f-156">Till exempel värdet för parametern **SessionOption** för `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3701f-156">For example, the value of the **SessionOption** parameter of the `New-PSSession`.</span></span>
<span data-ttu-id="3701f-157">cmdleten kan vara en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="3701f-157">cmdlet can be a hash table.</span></span>

```powershell
New-PSSession -ComputerName Server01 -SessionOption @{
  IdleTimeout=43200000
  SkipCnCheck=$True
}
Register-ScheduledJob Name Test -FilePath .\Get-Inventory.ps1 -Trigger @{
  Frequency="Daily"
  At="15:00"
}
```

## <a name="generic-objects"></a><span data-ttu-id="3701f-158">Allmänna objekt</span><span class="sxs-lookup"><span data-stu-id="3701f-158">Generic objects</span></span>

<span data-ttu-id="3701f-159">Du kan också skapa generiska objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3701f-159">You can also create generic objects in PowerShell.</span></span> <span data-ttu-id="3701f-160">Generiska klasser är klasser, strukturer, gränssnitt och metoder som har plats hållare (typ parametrar) för en eller flera av de typer som de lagrar eller använder.</span><span class="sxs-lookup"><span data-stu-id="3701f-160">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span>

<span data-ttu-id="3701f-161">I följande exempel skapas ett **Dictionary** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3701f-161">The following example creates a **Dictionary** object.</span></span>

```powershell
$dict = New-Object 'System.Collections.Generic.Dictionary[String,Int]'
$dict.Add("One", 1)
$dict
```

```Output
Key Value
--- -----
One     1
```

<span data-ttu-id="3701f-162">Mer information om generiska finns [i generiska i .net](/dotnet/standard/generics).</span><span class="sxs-lookup"><span data-stu-id="3701f-162">For more information on Generics, see [Generics in .NET](/dotnet/standard/generics).</span></span>

## <a name="see-also"></a><span data-ttu-id="3701f-163">Se även</span><span class="sxs-lookup"><span data-stu-id="3701f-163">See also</span></span>

[<span data-ttu-id="3701f-164">about_Objects</span><span class="sxs-lookup"><span data-stu-id="3701f-164">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="3701f-165">about_Methods</span><span class="sxs-lookup"><span data-stu-id="3701f-165">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="3701f-166">about_Properties</span><span class="sxs-lookup"><span data-stu-id="3701f-166">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="3701f-167">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="3701f-167">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="3701f-168">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="3701f-168">about_Types.ps1xml</span></span>](about_Types.ps1xml.md)
