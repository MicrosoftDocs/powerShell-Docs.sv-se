---
description: Beskriver hur du använder objekt egenskaper i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_properties?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Properties
ms.openlocfilehash: 5c4efd3f94d8ce8fbb7c66db1cc5f91eebd0756e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270531"
---
# <a name="about-properties"></a><span data-ttu-id="798f3-104">Om egenskaper</span><span class="sxs-lookup"><span data-stu-id="798f3-104">About Properties</span></span>

## <a name="short-description"></a><span data-ttu-id="798f3-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="798f3-105">Short description</span></span>
<span data-ttu-id="798f3-106">Beskriver hur du använder objekt egenskaper i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798f3-106">Describes how to use object properties in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="798f3-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="798f3-107">Long description</span></span>

<span data-ttu-id="798f3-108">PowerShell använder strukturerade samlingar med information som kallas objekt för att representera objekten i data lager eller datorns tillstånd.</span><span class="sxs-lookup"><span data-stu-id="798f3-108">PowerShell uses structured collections of information called objects to represent the items in data stores or the state of the computer.</span></span> <span data-ttu-id="798f3-109">Normalt arbetar du med objekt som ingår i Microsoft .NET Framework, men du kan också skapa anpassade objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798f3-109">Typically, you work with object that are part of the Microsoft .NET Framework, but you can also create custom objects in PowerShell.</span></span>

<span data-ttu-id="798f3-110">Associationen mellan ett objekt och dess objekt är mycket nära.</span><span class="sxs-lookup"><span data-stu-id="798f3-110">The association between an item and its object is very close.</span></span> <span data-ttu-id="798f3-111">När du ändrar ett objekt ändrar du vanligt vis objektet som det representerar.</span><span class="sxs-lookup"><span data-stu-id="798f3-111">When you change an object, you usually change the item that it represents.</span></span> <span data-ttu-id="798f3-112">Om du till exempel får en fil i PowerShell får du inte den faktiska filen.</span><span class="sxs-lookup"><span data-stu-id="798f3-112">For example, when you get a file in PowerShell, you do not get the actual file.</span></span> <span data-ttu-id="798f3-113">I stället får du ett FileInfo-objekt som representerar filen.</span><span class="sxs-lookup"><span data-stu-id="798f3-113">Instead, you get a FileInfo object that represents the file.</span></span> <span data-ttu-id="798f3-114">När du ändrar FileInfo-objektet ändras filen också.</span><span class="sxs-lookup"><span data-stu-id="798f3-114">When you change the FileInfo object, the file changes too.</span></span>

<span data-ttu-id="798f3-115">De flesta objekt har egenskaper.</span><span class="sxs-lookup"><span data-stu-id="798f3-115">Most objects have properties.</span></span> <span data-ttu-id="798f3-116">Egenskaper är de data som är associerade med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="798f3-116">Properties are the data that is associated with an object.</span></span> <span data-ttu-id="798f3-117">Olika typer av objekt har olika egenskaper.</span><span class="sxs-lookup"><span data-stu-id="798f3-117">Different types of object have different properties.</span></span> <span data-ttu-id="798f3-118">Ett FileInfo-objekt som representerar en fil har till exempel en **IsReadOnly** -egenskap som innehåller $True om filen är skrivskyddad och $false om den inte gör det.</span><span class="sxs-lookup"><span data-stu-id="798f3-118">For example, a FileInfo object, which represents a file, has an **IsReadOnly** property that contains $True if the file the read-only attribute and $False if it does not.</span></span>
<span data-ttu-id="798f3-119">Ett DirectoryInfo-objekt som representerar en fil system katalog har en överordnad egenskap som innehåller sökvägen till den överordnade katalogen.</span><span class="sxs-lookup"><span data-stu-id="798f3-119">A DirectoryInfo object, which represents a file system directory, has a Parent property that contains the path to the parent directory.</span></span>

### <a name="object-properties"></a><span data-ttu-id="798f3-120">Objekt egenskaper</span><span class="sxs-lookup"><span data-stu-id="798f3-120">Object properties</span></span>

<span data-ttu-id="798f3-121">Använd cmdleten för att hämta egenskaperna för ett objekt `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="798f3-121">To get the properties of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="798f3-122">Om du till exempel vill hämta egenskaperna för ett **fileinfo** -objekt använder du `Get-ChildItem` cmdleten för att hämta fileinfo-objektet som representerar en fil.</span><span class="sxs-lookup"><span data-stu-id="798f3-122">For example, to get the properties of a **FileInfo** object, use the `Get-ChildItem` cmdlet to get the FileInfo object that represents a file.</span></span> <span data-ttu-id="798f3-123">Använd sedan en pipeline-operatör (&#124;) för att skicka **fileinfo** -objektet till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="798f3-123">Then, use a pipeline operator (&#124;) to send the **FileInfo** object to `Get-Member`.</span></span> <span data-ttu-id="798f3-124">Följande kommando hämtar PowerShell.exe-filen och skickar den till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="798f3-124">The following command gets the PowerShell.exe file and sends it to `Get-Member`.</span></span>
<span data-ttu-id="798f3-125">Den \$ automatiska variabeln Pshome innehåller sökvägen till PowerShell-katalogen för installationen.</span><span class="sxs-lookup"><span data-stu-id="798f3-125">The \$Pshome automatic variable contains the path of the PowerShell installation directory.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member
```

<span data-ttu-id="798f3-126">Kommandots utdata visar medlemmar i **fileinfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="798f3-126">The output of the command lists the members of the **FileInfo** object.</span></span>
<span data-ttu-id="798f3-127">Medlemmarna inkluderar både egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="798f3-127">Members include both properties and methods.</span></span> <span data-ttu-id="798f3-128">När du arbetar i PowerShell har du åtkomst till alla medlemmar i objekten.</span><span class="sxs-lookup"><span data-stu-id="798f3-128">When you work in PowerShell, you have access to all the members of the objects.</span></span>

<span data-ttu-id="798f3-129">Om du bara vill hämta egenskaperna för ett objekt och inte metoderna använder du parametern MemberType i `Get-Member` cmdleten med värdet "Property", som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="798f3-129">To get only the properties of an object and not the methods, use the MemberType parameter of the `Get-Member` cmdlet with a value of "property", as shown in the following example.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Get-Member -MemberType property
```

```Output
TypeName: System.IO.FileInfo

Name              MemberType Definition
----              ---------- ----------
Attributes        Property   System.IO.FileAttributes Attributes {get;set;}
CreationTime      Property   System.DateTime CreationTime {get;set;}
CreationTimeUtc   Property   System.DateTime CreationTimeUtc {get;set;}
Directory         Property   System.IO.DirectoryInfo Directory {get;}
DirectoryName     Property   System.String DirectoryName {get;}
Exists            Property   System.Boolean Exists {get;}
Extension         Property   System.String Extension {get;}
FullName          Property   System.String FullName {get;}
IsReadOnly        Property   System.Boolean IsReadOnly {get;set;}
LastAccessTime    Property   System.DateTime LastAccessTime {get;set;}
LastAccessTimeUtc Property   System.DateTime LastAccessTimeUtc {get;set;}
LastWriteTime     Property   System.DateTime LastWriteTime {get;set;}
LastWriteTimeUtc  Property   System.DateTime LastWriteTimeUtc {get;set;}
Length            Property   System.Int64 Length {get;}
Name              Property   System.String Name {get;}
```

<span data-ttu-id="798f3-130">När du har hittat egenskaperna kan du använda dem i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="798f3-130">After you find the properties, you can use them in your PowerShell commands.</span></span>

## <a name="property-values"></a><span data-ttu-id="798f3-131">Egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="798f3-131">Property values</span></span>

<span data-ttu-id="798f3-132">Även om varje objekt av en viss typ har samma egenskaper, beskriver värdena för dessa egenskaper det specifika objektet.</span><span class="sxs-lookup"><span data-stu-id="798f3-132">Although every object of a specific type has the same properties, the values of those properties describe the particular object.</span></span> <span data-ttu-id="798f3-133">Till exempel har varje FileInfo-objekt en CreationTime-egenskap, men värdet för egenskapen skiljer sig åt för varje fil.</span><span class="sxs-lookup"><span data-stu-id="798f3-133">For example, every FileInfo object has a CreationTime property, but the value of that property differs for each file.</span></span>

<span data-ttu-id="798f3-134">Det vanligaste sättet att hämta värdena i egenskaperna för ett objekt är att använda punkt-metoden.</span><span class="sxs-lookup"><span data-stu-id="798f3-134">The most common way to get the values of the properties of an object is to use the dot method.</span></span> <span data-ttu-id="798f3-135">Skriv en referens till objektet, till exempel en variabel som innehåller objektet, eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="798f3-135">Type a reference to the object, such as a variable that contains the object, or a command that gets the object.</span></span> <span data-ttu-id="798f3-136">Skriv sedan en punkt (.) följt av egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="798f3-136">Then, type a dot (.) followed by the property name.</span></span>

<span data-ttu-id="798f3-137">Till exempel visar följande kommando värdet för egenskapen CreationTime i PowerShell.exe-filen.</span><span class="sxs-lookup"><span data-stu-id="798f3-137">For example, the following command displays the value of the CreationTime property of the PowerShell.exe file.</span></span> <span data-ttu-id="798f3-138">`Get-ChildItem`Kommandot returnerar ett fileinfo-objekt som representerar PowerShell.exes filen.</span><span class="sxs-lookup"><span data-stu-id="798f3-138">The `Get-ChildItem` command returns a FileInfo object that represents the PowerShell.exe file.</span></span> <span data-ttu-id="798f3-139">Kommandot omges av parenteser för att kontrol lera att det körs innan det går att komma åt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="798f3-139">The command is enclosed in parentheses to make sure that it is executed before any properties are accessed.</span></span> <span data-ttu-id="798f3-140">`Get-ChildItem`Kommandot följs av en punkt och namnet på egenskapen CreationTime, enligt följande:</span><span class="sxs-lookup"><span data-stu-id="798f3-140">The `Get-ChildItem` command is followed by a dot and the name of the CreationTime property, as follows:</span></span>

```powershell
(Get-ChildItem $pshome\PowerShell.exe).creationtime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="798f3-141">Du kan också spara ett objekt i en variabel och sedan hämta dess egenskaper med hjälp av punkt metoden, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="798f3-141">You can also save an object in a variable and then get its properties by using the dot method, as shown in the following example:</span></span>

```powershell
$a = Get-ChildItem $pshome\PowerShell.exe
$a.CreationTime
```

```output
Tuesday, March 18, 2008 12:07:52 AM
```

<span data-ttu-id="798f3-142">Du kan också använda `Select-Object` `Format-List` cmdletarna och för att Visa egenskaps värden för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="798f3-142">You can also use the `Select-Object` and `Format-List` cmdlets to display the property values of an object.</span></span> <span data-ttu-id="798f3-143">`Select-Object` och `Format-List` var och en har en **egenskaps** parameter.</span><span class="sxs-lookup"><span data-stu-id="798f3-143">`Select-Object` and `Format-List` each have a **Property** parameter.</span></span> <span data-ttu-id="798f3-144">Du kan använda **egenskaps** parametern för att ange en eller flera egenskaper och deras värden.</span><span class="sxs-lookup"><span data-stu-id="798f3-144">You can use the **Property** parameter to specify one or more properties and their values.</span></span> <span data-ttu-id="798f3-145">Eller så kan du använda jokertecknet ( \* ) för att representera alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="798f3-145">Or, you can use the wildcard character (\*) to represent all the properties.</span></span>

<span data-ttu-id="798f3-146">Följande kommando visar till exempel värdena för alla egenskaper för PowerShell.exe-filen.</span><span class="sxs-lookup"><span data-stu-id="798f3-146">For example, the following command displays the values of all the properties of the PowerShell.exe file.</span></span>

```powershell
Get-ChildItem $pshome\PowerShell.exe | Format-List -Property *
```

```output
PSPath            : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0\PowerShell.exe
PSParentPath      : Microsoft.PowerShell.Core\FileSystem::C:\Windows\System3
                    2\WindowsPowerShell\v1.0
PSChildName       : PowerShell.exe
PSDrive           : C
PSProvider        : Microsoft.PowerShell.Core\FileSystem
PSIsContainer     : False
Mode              : -a----
VersionInfo       : File:             C:\Windows\System32\WindowsPowerShell\
                    v1.0\PowerShell.exe
                    InternalName:     POWERSHELL
                    OriginalFilename: PowerShell.EXE.MUI
                    FileVersion:      10.0.16299.15 (WinBuild.160101.0800)
                    FileDescription:  Windows PowerShell
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.16299.15
                    Debug:            False
                    Patched:          False
                    PreRelease:       False
                    PrivateBuild:     False
                    SpecialBuild:     False
                    Language:         English (United States)

BaseName          : PowerShell
Target            : {C:\Windows\WinSxS\amd64_microsoft-windows-powershell-ex
                    e_31bf3856ad364e35_10.0.16299.15_none_8c022aa6735716ae\p
                    owershell.exe}
LinkType          : HardLink
Name              : PowerShell.exe
Length            : 449024
DirectoryName     : C:\Windows\System32\WindowsPowerShell\v1.0
Directory         : C:\Windows\System32\WindowsPowerShell\v1.0
IsReadOnly        : False
Exists            : True
FullName          : C:\Windows\System32\WindowsPowerShell\v1.0\PowerShell.ex
Extension         : .exe
CreationTime      : 9/29/2017 6:43:19 AM
CreationTimeUtc   : 9/29/2017 1:43:19 PM
LastAccessTime    : 9/29/2017 6:43:19 AM
LastAccessTimeUtc : 9/29/2017 1:43:19 PM
LastWriteTime     : 9/29/2017 6:43:19 AM
LastWriteTimeUtc  : 9/29/2017 1:43:19 PM
Attributes        : Archive
```

### <a name="static-properties"></a><span data-ttu-id="798f3-147">Statiska egenskaper</span><span class="sxs-lookup"><span data-stu-id="798f3-147">Static properties</span></span>

<span data-ttu-id="798f3-148">Du kan använda statiska egenskaper för .NET-klasser i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="798f3-148">You can use the static properties of .NET classes in PowerShell.</span></span> <span data-ttu-id="798f3-149">Statiska egenskaper är egenskaper för klass, till skillnad från standard egenskaper, som är egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="798f3-149">Static properties are properties of class, unlike standard properties, which are properties of an object.</span></span>

<span data-ttu-id="798f3-150">Om du vill hämta statiska egenskaper för en klass använder du den statiska parametern i Get-Member-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="798f3-150">To get the static properties of an class, use the Static parameter of the Get-Member cmdlet.</span></span>

<span data-ttu-id="798f3-151">Följande kommando hämtar till exempel `System.DateTime` klassens statiska egenskaper.</span><span class="sxs-lookup"><span data-stu-id="798f3-151">For example, the following command gets the static properties of the `System.DateTime` class.</span></span>

```powershell
Get-Date | Get-Member -MemberType Property -Static
```

```Output
TypeName: System.DateTime

Name     MemberType Definition
----     ---------- ----------
MaxValue Property   static datetime MaxValue {get;}
MinValue Property   static datetime MinValue {get;}
Now      Property   datetime Now {get;}
Today    Property   datetime Today {get;}
UtcNow   Property   datetime UtcNow {get;}
```

<span data-ttu-id="798f3-152">Använd följande syntax för att hämta värdet för en statisk egenskap.</span><span class="sxs-lookup"><span data-stu-id="798f3-152">To get the value of a static property, use the following syntax.</span></span>

```
[<ClassName>]::<Property>
```

<span data-ttu-id="798f3-153">Till exempel hämtar följande kommando värdet för klassens statiska egenskap UtcNow `System.DateTime` .</span><span class="sxs-lookup"><span data-stu-id="798f3-153">For example, the following command gets the value of the UtcNow static property of the `System.DateTime` class.</span></span>

```powershell
[System.DateTime]::UtcNow
```

### <a name="properties-of-scalar-objects-and-collections"></a><span data-ttu-id="798f3-154">Egenskaper för skalära objekt och samlingar</span><span class="sxs-lookup"><span data-stu-id="798f3-154">Properties of scalar objects and collections</span></span>

<span data-ttu-id="798f3-155">Egenskaperna för ett ("skalär") objekt av en viss typ skiljer sig ofta från egenskaperna för en samling objekt av samma typ.</span><span class="sxs-lookup"><span data-stu-id="798f3-155">The properties of one ("scalar") object of a particular type are often different from the properties of a collection of objects of the same type.</span></span>
<span data-ttu-id="798f3-156">Varje tjänst har till exempel egenskapen **DisplayName** , men en samling tjänster har inte egenskapen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="798f3-156">For example, every service has as **DisplayName** property, but a collection of services does not have a **DisplayName** property.</span></span>

<span data-ttu-id="798f3-157">Följande kommando hämtar värdet för egenskapen **DisplayName** för tjänsten "audiosrv".</span><span class="sxs-lookup"><span data-stu-id="798f3-157">The following command gets the value of the **DisplayName** property of the 'Audiosrv' service.</span></span>

```powershell
(Get-Service Audiosrv).DisplayName
```

```output
Windows Audio
```

<span data-ttu-id="798f3-158">Från och med PowerShell 3,0 försöker PowerShell förhindra skript fel som orsakas av de olika egenskaperna för skalära objekt och samlingar.</span><span class="sxs-lookup"><span data-stu-id="798f3-158">Beginning in PowerShell 3.0, PowerShell tries to prevent scripting errors that result from the differing properties of scalar objects and collections.</span></span> <span data-ttu-id="798f3-159">Samma kommando returnerar värdet för egenskapen **DisplayName** för varje tjänst som `Get-Service` returneras.</span><span class="sxs-lookup"><span data-stu-id="798f3-159">The same command returns the value of the **DisplayName** property of every service that `Get-Service` returns.</span></span>

```powershell
(Get-Service).DisplayName
```

```output
Application Experience
Application Layer Gateway Service
Windows All-User Install Agent
Application Identity
Application Information
...
```

<span data-ttu-id="798f3-160">När du skickar en samling, men begär en egenskap som bara finns på enstaka ("skalära") objekt, returnerar PowerShell värdet för den egenskapen för varje objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="798f3-160">When you submit a collection, but request a property that exists only on single ("scalar") objects, PowerShell returns the value of that property for every object in the collection.</span></span>

<span data-ttu-id="798f3-161">Alla samlingar har en **Count** -egenskap som returnerar hur många objekt som finns i samlingen.</span><span class="sxs-lookup"><span data-stu-id="798f3-161">All collections have a **Count** property that returns how many objects are in the collection.</span></span>

```powershell
(Get-Service).Count
```

```output
176
```

<span data-ttu-id="798f3-162">Från och med PowerShell 3,0 returnerar PowerShell rätt värde om du begär egenskapen Count eller length för noll objekt eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="798f3-162">Beginning in PowerShell 3.0, if you request the Count or Length property of zero objects or one object, PowerShell returns the correct value.</span></span>

```powershell
(Get-Service Audiosrv).Count
```

```output
1
```

<span data-ttu-id="798f3-163">Om det finns en egenskap för de enskilda objekten och i samlingen returneras bara samlingens egenskap.</span><span class="sxs-lookup"><span data-stu-id="798f3-163">If a property exists on the individual objects and on the collection, only the collection's property is returned.</span></span>

 ```powershell
 $collection = @(
 [pscustomobject]@{length = "foo"}
 [pscustomobject]@{length = "bar"}
 )
 # PowerShell returns the collection's Length.
 $collection.length
 ```

 ```output
 2
 ```

<span data-ttu-id="798f3-164">Den här funktionen fungerar också med metoder för skalära objekt och samlingar.</span><span class="sxs-lookup"><span data-stu-id="798f3-164">This feature also works on methods of scalar objects and collections.</span></span> <span data-ttu-id="798f3-165">Mer information finns i [about_Methods](about_methods.md).</span><span class="sxs-lookup"><span data-stu-id="798f3-165">For more information, see [about_Methods](about_methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="798f3-166">Se även</span><span class="sxs-lookup"><span data-stu-id="798f3-166">See also</span></span>

[<span data-ttu-id="798f3-167">about_Methods</span><span class="sxs-lookup"><span data-stu-id="798f3-167">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="798f3-168">about_Objects</span><span class="sxs-lookup"><span data-stu-id="798f3-168">about_Objects</span></span>](about_Objects.md)

[<span data-ttu-id="798f3-169">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="798f3-169">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

[<span data-ttu-id="798f3-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="798f3-170">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)

[<span data-ttu-id="798f3-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="798f3-171">Format-List</span></span>](xref:Microsoft.PowerShell.Utility.Format-List)
