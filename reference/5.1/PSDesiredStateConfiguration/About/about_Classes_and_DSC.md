---
description: Beskriver hur du kan använda klasser för att utveckla i PowerShell med önskad tillstånds konfiguration (DSC).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 1/11/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Classes_and_DSC
ms.openlocfilehash: 21a013bb817367dd2a11cc0826263d0f3203796b
ms.sourcegitcommit: cc72c40315fd2981d3009b335accbfa52d57640c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96349837"
---
# <a name="about-classes-and-desired-state-configuration"></a><span data-ttu-id="a79a9-104">Om klasser och önskad tillstånds konfiguration</span><span class="sxs-lookup"><span data-stu-id="a79a9-104">About Classes and Desired State Configuration</span></span>

## <a name="short-description"></a><span data-ttu-id="a79a9-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a79a9-105">Short description</span></span>

<span data-ttu-id="a79a9-106">Beskriver hur du kan använda klasser för att utveckla i PowerShell med önskad tillstånds konfiguration (DSC).</span><span class="sxs-lookup"><span data-stu-id="a79a9-106">Describes how you can use classes to develop in PowerShell with Desired State Configuration (DSC).</span></span>

## <a name="long-description"></a><span data-ttu-id="a79a9-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="a79a9-107">Long description</span></span>

<span data-ttu-id="a79a9-108">Från och med Windows PowerShell 5,0 lades språk till för att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantik som liknar andra objektorienterade programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="a79a9-108">Starting in Windows PowerShell 5.0, language was added to define classes and other user-defined types, by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="a79a9-109">Målet är att göra det möjligt för utvecklare och IT-proffs att använda Windows PowerShell för en större mängd användnings fall, förenkla utvecklingen av PowerShell-artefakter som DSC-resurser och påskynda täckning av hanterings ytor.</span><span class="sxs-lookup"><span data-stu-id="a79a9-109">The goal is to enable developers and IT professionals to embrace Windows PowerShell for a wider range of use cases, simplify development of PowerShell artifacts such as DSC resources, and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios"></a><span data-ttu-id="a79a9-110">Scenarier som stöds</span><span class="sxs-lookup"><span data-stu-id="a79a9-110">Supported scenarios</span></span>

<span data-ttu-id="a79a9-111">Följande scenarier stöds:</span><span class="sxs-lookup"><span data-stu-id="a79a9-111">The following scenarios are supported:</span></span>

- <span data-ttu-id="a79a9-112">Definiera DSC-resurser och deras associerade typer med hjälp av PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="a79a9-112">Define DSC resources and their associated types by using the PowerShell language.</span></span>
- <span data-ttu-id="a79a9-113">Definiera anpassade typer i PowerShell med hjälp av välbekanta objektorienterade programmerings konstruktioner, till exempel klasser, egenskaper, metoder och arv.</span><span class="sxs-lookup"><span data-stu-id="a79a9-113">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, and inheritance.</span></span>
- <span data-ttu-id="a79a9-114">Fel söknings typer med hjälp av PowerShell-språket.</span><span class="sxs-lookup"><span data-stu-id="a79a9-114">Debug types by using the PowerShell language.</span></span>
- <span data-ttu-id="a79a9-115">Generera och hantera undantag med hjälp av formella mekanismer och på rätt nivå.</span><span class="sxs-lookup"><span data-stu-id="a79a9-115">Generate and handle exceptions by using formal mechanisms, and at the right level.</span></span>

## <a name="define-dsc-resources-with-classes"></a><span data-ttu-id="a79a9-116">Definiera DSC-resurser med klasser</span><span class="sxs-lookup"><span data-stu-id="a79a9-116">Define DSC resources with classes</span></span>

<span data-ttu-id="a79a9-117">Utöver ändringar i syntaxen är de större skillnaderna mellan en klass definierad DSC-resurs och en cmdlet DSC-resurs leverantör följande objekt:</span><span class="sxs-lookup"><span data-stu-id="a79a9-117">Apart from syntax changes, the major differences between a class-defined DSC resource and a cmdlet DSC resource provider are the following items:</span></span>

- <span data-ttu-id="a79a9-118">Det krävs ingen MOF-fil (Management Object Format).</span><span class="sxs-lookup"><span data-stu-id="a79a9-118">A Management Object Format (MOF) file is not required.</span></span>
- <span data-ttu-id="a79a9-119">En Dscresource Keyword Supports-undermapp i mappen module krävs inte.</span><span class="sxs-lookup"><span data-stu-id="a79a9-119">A DSCResource subfolder in the module folder is not required.</span></span>
- <span data-ttu-id="a79a9-120">En PowerShell-modul kan innehålla flera DSC-resurs klasser.</span><span class="sxs-lookup"><span data-stu-id="a79a9-120">A PowerShell module file can contain multiple DSC resource classes.</span></span>

## <a name="create-a-class-defined-dsc-resource-provider"></a><span data-ttu-id="a79a9-121">Skapa en klass definierad DSC-resurs leverantör</span><span class="sxs-lookup"><span data-stu-id="a79a9-121">Create a class-defined DSC resource provider</span></span>

<span data-ttu-id="a79a9-122">Följande exempel är en klass-definierad DSC-resurs-Provider som sparas som en modul, MyDSCResource. psm1.</span><span class="sxs-lookup"><span data-stu-id="a79a9-122">The following example is a class-defined DSC resource provider that is saved as a module, MyDSCResource.psm1.</span></span> <span data-ttu-id="a79a9-123">Du måste alltid ta med en nyckel egenskap i en klass definierad DSC-resurs leverantör.</span><span class="sxs-lookup"><span data-stu-id="a79a9-123">You must always include a key property in a class-defined DSC resource provider.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
    This resource manages the file in a specific path.
    [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
        This property is the fully qualified path to the file that is
        expected to be present or absent.

        The [DscProperty(Key)] attribute indicates the property is a
        key and its value uniquely identifies a resource instance.
        Defining this attribute also means the property is required
        and DSC will ensure a value is set before calling the resource.

        A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
        This property defines the fully qualified path to a file that will
        be placed on the system if $Ensure = Present and $Path does not
        exist.

        NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
        This property reports the file's create timestamp.

        [DscProperty(NotConfigurable)] attribute indicates the property is
        not configurable in DSC configuration.  Properties marked this way
        are populated by the Get() method to report additional details
        about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#

        This method is equivalent of the Test-TargetResource script
        function. It should return True or False, showing whether the
        resource is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
{
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate
        resources. This method returns an instance of this class with the
        updated key properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }
        return $this
    }

    <#
        Helper method to check if the file exists and it is correct file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($null -eq $item)
        {
            $present = $false
        }
        elseif( $item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }
        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if(-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo]
        $destFileInfo = new-object System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            $FullName = $destFileInfo.Directory.FullName
            $Message = "Creating directory $FullName"

            Write-Verbose -Message $Message

            #use CreateDirectory instead of New-Item to avoid code
            # to handle the non-terminating error
            [System.IO.Directory]::CreateDirectory($FullName)
        }

        if(Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $this.SourcePath to $this.Path"

        #DSC engine catches and reports any error that occurs
        Copy-Item -Path $this.SourcePath -Destination $this.Path -Force
    }
}
```

## <a name="create-a-module-manifest"></a><span data-ttu-id="a79a9-124">Skapa ett modul manifest</span><span class="sxs-lookup"><span data-stu-id="a79a9-124">Create a module manifest</span></span>

<span data-ttu-id="a79a9-125">När du har skapat den Class-definierade DSC-adressresursen och sparat den som en modul, skapar du ett modul manifest för modulen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-125">After creating the class-defined DSC resource provider, and saving it as a module, create a module manifest for the module.</span></span> <span data-ttu-id="a79a9-126">Om du vill göra en klass baserad resurs tillgänglig för DSC-motorn måste du inkludera en `DscResourcesToExport` instruktion i manifest filen som instruerar modulen att exportera resursen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-126">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="a79a9-127">I det här exemplet sparas följande modul-manifest som MyDscResource.psd1.</span><span class="sxs-lookup"><span data-stu-id="a79a9-127">In this example, the following module manifest is saved as MyDscResource.psd1.</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

}
```

## <a name="deploy-a-dsc-resource-provider"></a><span data-ttu-id="a79a9-128">Distribuera en DSC-resurs-Provider</span><span class="sxs-lookup"><span data-stu-id="a79a9-128">Deploy a DSC resource provider</span></span>

<span data-ttu-id="a79a9-129">Distribuera den nya DSC-resurs leverantören genom att skapa en MyDscResource-mapp i `$pshome\Modules` eller `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-129">Deploy the new DSC resource provider by creating a MyDscResource folder in `$pshome\Modules` or `$env:SystemDrive\ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="a79a9-130">Du behöver inte skapa en undermapp för Dscresource Keyword Supports.</span><span class="sxs-lookup"><span data-stu-id="a79a9-130">You do not need to create a DSCResource subfolder.</span></span> <span data-ttu-id="a79a9-131">Kopiera modul-och modul manifest-filerna (MyDscResource. psm1 och MyDscResource.psd1) till mappen MyDscResource.</span><span class="sxs-lookup"><span data-stu-id="a79a9-131">Copy the module and module manifest files (MyDscResource.psm1 and MyDscResource.psd1) to the MyDscResource folder.</span></span>

<span data-ttu-id="a79a9-132">Nu skapar du och kör ett konfigurations skript som du skulle ha med valfri DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="a79a9-132">From this point, you create and run a configuration script as you would with any DSC resource.</span></span>

## <a name="create-a-dsc-configuration-script"></a><span data-ttu-id="a79a9-133">Skapa ett DSC-konfigurationsskript</span><span class="sxs-lookup"><span data-stu-id="a79a9-133">Create a DSC configuration script</span></span>

<span data-ttu-id="a79a9-134">När du har sparat klass-och manifest filerna i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-134">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="a79a9-135">Följande konfiguration refererar till MyDSCResource-modulen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-135">The following configuration references the MyDSCResource module.</span></span> <span data-ttu-id="a79a9-136">Spara konfigurationen som ett skript MyResource.ps1.</span><span class="sxs-lookup"><span data-stu-id="a79a9-136">Save the configuration as a script, MyResource.ps1.</span></span>

<span data-ttu-id="a79a9-137">Information om hur du kör en DSC-konfiguration finns i [Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers).</span><span class="sxs-lookup"><span data-stu-id="a79a9-137">For information about how to run a DSC configuration, see [Windows PowerShell Desired State Configuration Overview](/powershell/scripting/dsc/overview/dscforengineers).</span></span>

<span data-ttu-id="a79a9-138">Innan du kör konfigurationen skapar du `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-138">Before you run the configuration, create `C:\test.txt`.</span></span> <span data-ttu-id="a79a9-139">Konfigurationen kontrollerar om filen finns på `c:\test\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-139">The configuration checks if the file exists at `c:\test\test.txt`.</span></span> <span data-ttu-id="a79a9-140">Om filen inte finns kopierar konfigurationen filen från `C:\test.txt` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-140">If the file does not exist, the configuration copies the file from `C:\test.txt`.</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "C:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

<span data-ttu-id="a79a9-141">Kör det här skriptet som valfritt DSC-konfigurations skript.</span><span class="sxs-lookup"><span data-stu-id="a79a9-141">Run this script as you would any DSC configuration script.</span></span> <span data-ttu-id="a79a9-142">Starta konfigurationen genom att köra följande i en upphöjd PowerShell-konsol:</span><span class="sxs-lookup"><span data-stu-id="a79a9-142">To start the configuration, in an elevated PowerShell console, run the following:</span></span>

`PS C:\test> .\MyResource.ps1`

## <a name="inheritance-in-powershell-classes"></a><span data-ttu-id="a79a9-143">Arv i PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="a79a9-143">Inheritance in PowerShell classes</span></span>

### <a name="declare-base-classes-for-powershell-classes"></a><span data-ttu-id="a79a9-144">Deklarera bas klasser för PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="a79a9-144">Declare base classes for PowerShell classes</span></span>

<span data-ttu-id="a79a9-145">Du kan deklarera en PowerShell-klass som bastyp för en annan PowerShell-klass, som du ser i följande exempel där **frukten** är en bastyp för **Apple**.</span><span class="sxs-lookup"><span data-stu-id="a79a9-145">You can declare a PowerShell class as a base type for another PowerShell class, as shown in the following example, in which **fruit** is a base type for **apple**.</span></span>

```powershell
class fruit
{
    [int]sold() {return 100500}
}

class apple : fruit {}
    [apple]::new().sold() # return 100500
```

### <a name="declare-implemented-interfaces-for-powershell-classes"></a><span data-ttu-id="a79a9-146">Deklarera implementerade gränssnitt för PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="a79a9-146">Declare implemented interfaces for PowerShell classes</span></span>

<span data-ttu-id="a79a9-147">Du kan deklarera implementerade gränssnitt efter grund typer, eller omedelbart efter ett kolon ( `:` ) om det inte finns någon bastyp angiven.</span><span class="sxs-lookup"><span data-stu-id="a79a9-147">You can declare implemented interfaces after base types, or immediately after a colon (`:`) if there is no base type specified.</span></span> <span data-ttu-id="a79a9-148">Avgränsa alla typnamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="a79a9-148">Separate all type names by using commas.</span></span> <span data-ttu-id="a79a9-149">Detta liknar C#-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-149">This is similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableTest : test, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

### <a name="call-base-class-constructors"></a><span data-ttu-id="a79a9-150">Anropa Bask lass konstruktörer</span><span class="sxs-lookup"><span data-stu-id="a79a9-150">Call base class constructors</span></span>

<span data-ttu-id="a79a9-151">Om du vill anropa en konstruktor för Bask Lassen från en underklass lägger du till `base` nyckelordet, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a79a9-151">To call a base class constructor from a subclass, add the `base` keyword, as shown in the following example:</span></span>

```powershell
class A {
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

<span data-ttu-id="a79a9-152">Om en basklass har en standardkonstruktor (inga parametrar) kan du utelämna ett explicit konstruktor-anrop, som visas.</span><span class="sxs-lookup"><span data-stu-id="a79a9-152">If a base class has a default constructor (no parameters), you can omit an explicit constructor call, as shown.</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```

### <a name="call-base-class-methods"></a><span data-ttu-id="a79a9-153">Anropa Bask lass metoder</span><span class="sxs-lookup"><span data-stu-id="a79a9-153">Call base class methods</span></span>

<span data-ttu-id="a79a9-154">Du kan åsidosätta befintliga metoder i underklasser.</span><span class="sxs-lookup"><span data-stu-id="a79a9-154">You can override existing methods in subclasses.</span></span> <span data-ttu-id="a79a9-155">För att göra åsidosättningen deklarerar du metoder med hjälp av samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="a79a9-155">To do the override, declare methods by using the same name and signature.</span></span>

```powershell
class baseClass
{
    [int]days() {return 100500}
}
class childClass1 : baseClass
{
    [int]days () {return 200600}
}

    [childClass1]::new().days() # return 200600
```

<span data-ttu-id="a79a9-156">För att anropa Bask lass metoder från åsidosatta implementeringar, omvandlas till Bask Lassen `([baseclass]$this)` för anrop.</span><span class="sxs-lookup"><span data-stu-id="a79a9-156">To call base class methods from overridden implementations, cast to the base class `([baseclass]$this)` on invocation.</span></span>

```powershell
class childClass2 : baseClass
{
    [int]days()
    {
        return 3 * ([baseClass]$this).days()
    }
}

    [childClass2]::new().days() # return 301500
```

<span data-ttu-id="a79a9-157">Alla PowerShell-metoder är virtuella.</span><span class="sxs-lookup"><span data-stu-id="a79a9-157">All PowerShell methods are virtual.</span></span> <span data-ttu-id="a79a9-158">Du kan dölja icke-virtuella .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning: deklarera metoder med samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="a79a9-158">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: declare methods with same name and signature.</span></span>

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

### <a name="current-limitations-with-class-inheritance"></a><span data-ttu-id="a79a9-159">Aktuella begränsningar med klass arv</span><span class="sxs-lookup"><span data-stu-id="a79a9-159">Current limitations with class inheritance</span></span>

<span data-ttu-id="a79a9-160">En begränsning av klass arvet är att det inte finns någon syntax för att deklarera gränssnitt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a79a9-160">A limitation with class inheritance is that there is no syntax to declare interfaces in PowerShell.</span></span>

## <a name="defining-custom-types-in-powershell"></a><span data-ttu-id="a79a9-161">Definiera anpassade typer i PowerShell</span><span class="sxs-lookup"><span data-stu-id="a79a9-161">Defining custom types in PowerShell</span></span>

<span data-ttu-id="a79a9-162">Windows PowerShell 5,0 introducerade flera språk element.</span><span class="sxs-lookup"><span data-stu-id="a79a9-162">Windows PowerShell 5.0 introduced several language elements.</span></span>

### <a name="class-keyword"></a><span data-ttu-id="a79a9-163">Klass nyckelord</span><span class="sxs-lookup"><span data-stu-id="a79a9-163">Class keyword</span></span>

<span data-ttu-id="a79a9-164">Definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="a79a9-164">Defines a new class.</span></span>
<span data-ttu-id="a79a9-165">`class`Nyckelordet är av typen true .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a79a9-165">The `class` keyword is a true .NET Framework type.</span></span>
<span data-ttu-id="a79a9-166">Klass medlemmar är offentliga.</span><span class="sxs-lookup"><span data-stu-id="a79a9-166">Class members are public.</span></span>

```powershell
class MyClass
{
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="a79a9-167">Räkna upp nyckelord och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="a79a9-167">Enum keyword and enumerations</span></span>

<span data-ttu-id="a79a9-168">Stöd för `enum` nyckelordet har lagts till och är en avbrytande ändring.</span><span class="sxs-lookup"><span data-stu-id="a79a9-168">Support for the `enum` keyword was added and is a breaking change.</span></span> <span data-ttu-id="a79a9-169">`enum`Avgränsaren är för närvarande en ny rad.</span><span class="sxs-lookup"><span data-stu-id="a79a9-169">The `enum` delimiter is currently a newline.</span></span> <span data-ttu-id="a79a9-170">En lösning för de som redan använder `enum` är att infoga ett et-tecken ( `&` ) före ordet.</span><span class="sxs-lookup"><span data-stu-id="a79a9-170">A workaround for those who are already using `enum` is to insert an ampersand (`&`) before the word.</span></span> <span data-ttu-id="a79a9-171">Aktuella begränsningar: du kan inte definiera en uppräknare i själva fallet, men du kan initiera `enum` i villkor för en annan `enum` , som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a79a9-171">Current limitations: you cannot define an enumerator in terms of itself, but you can initialize `enum` in terms of another `enum`, as shown in the following example:</span></span>

<span data-ttu-id="a79a9-172">Det går för närvarande inte att ange bastypen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-172">The base type cannot currently be specified.</span></span> <span data-ttu-id="a79a9-173">Bastypen är alltid [int].</span><span class="sxs-lookup"><span data-stu-id="a79a9-173">The base type is always [int].</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="a79a9-174">Ett uppräknings värde måste vara en konstant för en parse.</span><span class="sxs-lookup"><span data-stu-id="a79a9-174">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="a79a9-175">Uppräkning svärdet kan inte anges till resultatet av ett anropat kommando.</span><span class="sxs-lookup"><span data-stu-id="a79a9-175">The enumerator value cannot be set to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="a79a9-176">`Enum` stöder aritmetiska åtgärder, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a79a9-176">`Enum` supports arithmetic operations, as shown in the following example:</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="hidden-keyword"></a><span data-ttu-id="a79a9-177">Dolt nyckelord</span><span class="sxs-lookup"><span data-stu-id="a79a9-177">Hidden keyword</span></span>

<span data-ttu-id="a79a9-178">`hidden`Nyckelordet, som introducerades i Windows PowerShell 5,0, döljer klass medlemmar från standard `Get-Member` resultat.</span><span class="sxs-lookup"><span data-stu-id="a79a9-178">The `hidden` keyword, introduced in Windows PowerShell 5.0, hides class members from default `Get-Member` results.</span></span> <span data-ttu-id="a79a9-179">Ange den dolda egenskapen som visas på följande rad:</span><span class="sxs-lookup"><span data-stu-id="a79a9-179">Specify the hidden property as shown in the following line:</span></span>

```powershell
hidden [type] $classmember = <value>
```

<span data-ttu-id="a79a9-180">Dolda medlemmar visas inte med hjälp av tabb-slutförande eller IntelliSense, om inte slut för ande sker i den klass som definierar den dolda medlemmen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-180">Hidden members are not displayed by using tab completion or IntelliSense, unless the completion occurs in the class that defines the hidden member.</span></span>

<span data-ttu-id="a79a9-181">Ett nytt attribut, **system. Management. Automation. HiddenAttribute**, har lagts till, så att C#-koden kan ha samma semantik i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a79a9-181">A new attribute, **System.Management.Automation.HiddenAttribute**, was added, so that C# code can have the same semantics within PowerShell.</span></span>

<span data-ttu-id="a79a9-182">Mer information finns i [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span><span class="sxs-lookup"><span data-stu-id="a79a9-182">For more information, see [about_Hidden](../../Microsoft.PowerShell.Core/About/about_hidden.md).</span></span>

### <a name="import-dscresource"></a><span data-ttu-id="a79a9-183">Import-DscResource</span><span class="sxs-lookup"><span data-stu-id="a79a9-183">Import-DscResource</span></span>

<span data-ttu-id="a79a9-184">`Import-DscResource` är nu ett faktiskt dynamiskt nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a79a9-184">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="a79a9-185">PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet Dscresource Keyword Supports.</span><span class="sxs-lookup"><span data-stu-id="a79a9-185">PowerShell parses the specified module's root module, searching for classes that contain the DscResource attribute.</span></span>

### <a name="properties"></a><span data-ttu-id="a79a9-186">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="a79a9-186">Properties</span></span>

<span data-ttu-id="a79a9-187">Ett nytt fält, `ImplementingAssembly` ,, har lagts till i `ModuleInfo` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-187">A new field, `ImplementingAssembly`, was added to `ModuleInfo`.</span></span> <span data-ttu-id="a79a9-188">Om skriptet definierar klasser eller om den inlästa sammansättningen för binära moduler `ImplementingAssembly` är inställd på den dynamiska sammansättning som skapats för en-modul.</span><span class="sxs-lookup"><span data-stu-id="a79a9-188">If the script defines classes, or the loaded assembly for binary modules `ImplementingAssembly` is set to the dynamic assembly created for a script module.</span></span> <span data-ttu-id="a79a9-189">Den anges inte när ModuleType = manifestet har angetts.</span><span class="sxs-lookup"><span data-stu-id="a79a9-189">It is not set when ModuleType = Manifest.</span></span>

<span data-ttu-id="a79a9-190">Reflektion i `ImplementingAssembly` fältet identifierar resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="a79a9-190">Reflection on the `ImplementingAssembly` field discovers resources in a module.</span></span> <span data-ttu-id="a79a9-191">Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="a79a9-191">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

<span data-ttu-id="a79a9-192">Fält med initierare.</span><span class="sxs-lookup"><span data-stu-id="a79a9-192">Fields with initializers.</span></span>

`[int] $i = 5`

<span data-ttu-id="a79a9-193">Statisk stöds och fungerar som ett attribut, liknande typ begränsningar, så att det kan anges i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="a79a9-193">Static is supported and works like an attribute, similar to the type constraints, so it can be specified in any order.</span></span>

`static [int] $count = 0`

<span data-ttu-id="a79a9-194">En typ är valfri.</span><span class="sxs-lookup"><span data-stu-id="a79a9-194">A type is optional.</span></span>

`$s = "hello"`

<span data-ttu-id="a79a9-195">Alla medlemmar är offentliga.</span><span class="sxs-lookup"><span data-stu-id="a79a9-195">All members are public.</span></span> <span data-ttu-id="a79a9-196">Egenskaperna kräver antingen en ny rad eller ett semikolon.</span><span class="sxs-lookup"><span data-stu-id="a79a9-196">Properties require either a newline or semicolon.</span></span> <span data-ttu-id="a79a9-197">Om ingen objekt typ anges är egenskaps typen **objekt**.</span><span class="sxs-lookup"><span data-stu-id="a79a9-197">If no object type is specified, the property type is **Object**.</span></span>

### <a name="constructors-and-instantiation"></a><span data-ttu-id="a79a9-198">Konstruktörer och instansiering</span><span class="sxs-lookup"><span data-stu-id="a79a9-198">Constructors and instantiation</span></span>

<span data-ttu-id="a79a9-199">PowerShell-klasser kan ha konstruktorer som har samma namn som klassen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-199">PowerShell classes can have constructors that have the same name as their class.</span></span> <span data-ttu-id="a79a9-200">Konstruktörer kan vara överbelastade.</span><span class="sxs-lookup"><span data-stu-id="a79a9-200">Constructors can be overloaded.</span></span> <span data-ttu-id="a79a9-201">Statiska konstruktorer stöds.</span><span class="sxs-lookup"><span data-stu-id="a79a9-201">Static constructors are supported.</span></span>
<span data-ttu-id="a79a9-202">Egenskaper med initierings uttryck initieras innan all kod körs i en konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a79a9-202">Properties with initialization expressions are initialized before running any code in a constructor.</span></span> <span data-ttu-id="a79a9-203">Statiska egenskaper initieras före bröd texten i en statisk konstruktor och instans egenskaper initieras före bröd texten i den icke-statiska konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="a79a9-203">Static properties are initialized before the body of a static constructor, and instance properties are initialized before the body of the non-static constructor.</span></span> <span data-ttu-id="a79a9-204">För närvarande finns det ingen syntax för att anropa en konstruktor från en annan konstruktor, till exempel C#-syntax: `": this()")` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-204">Currently, there is no syntax for calling a constructor from another constructor such as the C# syntax: `": this()")`.</span></span> <span data-ttu-id="a79a9-205">Lösningen är att definiera en gemensam init-metod.</span><span class="sxs-lookup"><span data-stu-id="a79a9-205">The workaround is to define a common Init method.</span></span>

<span data-ttu-id="a79a9-206">Följande är sätt att instansiera klasser:</span><span class="sxs-lookup"><span data-stu-id="a79a9-206">The following are ways of instantiating classes:</span></span>

- <span data-ttu-id="a79a9-207">Instansieras med hjälp av Standardkonstruktorn.</span><span class="sxs-lookup"><span data-stu-id="a79a9-207">Instantiating by using the default constructor.</span></span> <span data-ttu-id="a79a9-208">Observera att `New-Object` det inte finns stöd för i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-208">Note that `New-Object` is not supported in this release.</span></span>

  `$a = [MyClass]::new()`

- <span data-ttu-id="a79a9-209">Anropar en konstruktor med en parameter.</span><span class="sxs-lookup"><span data-stu-id="a79a9-209">Calling a constructor with a parameter.</span></span>

  `$b = [MyClass]::new(42)`

- <span data-ttu-id="a79a9-210">Skicka en matris till en konstruktor med flera parametrar</span><span class="sxs-lookup"><span data-stu-id="a79a9-210">Passing an array to a constructor with multiple parameters</span></span>

  `$c = [MyClass]::new(@(42,43,44), "Hello")`

<span data-ttu-id="a79a9-211">I den här versionen är typ namnet bara synligt i lexikalt, vilket innebär att det inte är synligt utanför modulen eller skriptet som definierar klassen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-211">For this release, the type name is only visible lexically, meaning it is not visible outside of the module or script that defines the class.</span></span> <span data-ttu-id="a79a9-212">Funktioner kan returnera instanser av en klass som definierats i PowerShell och instanser fungerar bra utanför modulen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="a79a9-212">Functions can return instances of a class defined in PowerShell, and instances work well outside of the module or script.</span></span>

<span data-ttu-id="a79a9-213">Med den `Get-Member` **statiska** parametern visas konstruktörer, så att du kan visa överlagringar på samma sätt som andra metoder.</span><span class="sxs-lookup"><span data-stu-id="a79a9-213">The `Get-Member` **Static** parameter lists constructors, so you can view overloads like any other method.</span></span> <span data-ttu-id="a79a9-214">Prestanda för den här syntaxen är också avsevärt snabbare än `New-Object` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-214">The performance of this syntax is also considerably faster than `New-Object`.</span></span>

<span data-ttu-id="a79a9-215">Den pseudo-statiska metoden med namnet **New** fungerar med .net-typer, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="a79a9-215">The pseudo-static method named **new** works with .NET types, as shown in the following example.</span></span> `[hashtable]::new()`

<span data-ttu-id="a79a9-216">Du kan nu se överbelastningar i konstruktorn med `Get-Member` eller som visas i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="a79a9-216">You can now see constructor overloads with `Get-Member`, or as shown in this example:</span></span>

```powershell
[hashtable]::new
OverloadDefinitions
-------------------
hashtable new()
hashtable new(int capacity)
hashtable new(int capacity, float loadFactor)
```

### <a name="methods"></a><span data-ttu-id="a79a9-217">Metoder</span><span class="sxs-lookup"><span data-stu-id="a79a9-217">Methods</span></span>

<span data-ttu-id="a79a9-218">En PowerShell-klass metod implementeras som en **script block** som bara har ett slut block.</span><span class="sxs-lookup"><span data-stu-id="a79a9-218">A PowerShell class method is implemented as a **ScriptBlock** that has only an end block.</span></span> <span data-ttu-id="a79a9-219">Alla metoder är offentliga.</span><span class="sxs-lookup"><span data-stu-id="a79a9-219">All methods are public.</span></span> <span data-ttu-id="a79a9-220">Nedan visas ett exempel på hur du definierar en metod med namnet **doSomething**.</span><span class="sxs-lookup"><span data-stu-id="a79a9-220">The following shows an example of defining a method named **DoSomething**.</span></span>

```powershell
class MyClass
{
    DoSomething($x)
    {
        $this._doSomething($x)       # method syntax
    }
    private _doSomething($a) {}
}
```

### <a name="method-invocation"></a><span data-ttu-id="a79a9-221">Metod anrop</span><span class="sxs-lookup"><span data-stu-id="a79a9-221">Method invocation</span></span>

<span data-ttu-id="a79a9-222">Överlagrade metoder stöds.</span><span class="sxs-lookup"><span data-stu-id="a79a9-222">Overloaded methods are supported.</span></span> <span data-ttu-id="a79a9-223">Överlagrade metoder har samma namn som en befintlig metod men åtskiljs av de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="a79a9-223">Overloaded methods are named the same as an existing method but differentiated by their specified values.</span></span>

```powershell
$b = [MyClass]::new()
$b.DoSomething(42)
```

### <a name="invocation"></a><span data-ttu-id="a79a9-224">Anrop</span><span class="sxs-lookup"><span data-stu-id="a79a9-224">Invocation</span></span>

<span data-ttu-id="a79a9-225">Se [metod anrop](#method-invocation).</span><span class="sxs-lookup"><span data-stu-id="a79a9-225">See [Method invocation](#method-invocation).</span></span>

### <a name="attributes"></a><span data-ttu-id="a79a9-226">Attribut</span><span class="sxs-lookup"><span data-stu-id="a79a9-226">Attributes</span></span>

<span data-ttu-id="a79a9-227">Tre nya attribut har lagts till: `DscResource` , `DscResourceKey` och `DscResourceMandatory` .</span><span class="sxs-lookup"><span data-stu-id="a79a9-227">Three new attributes were added: `DscResource`, `DscResourceKey`, and `DscResourceMandatory`.</span></span>

### <a name="return-types"></a><span data-ttu-id="a79a9-228">Retur typer</span><span class="sxs-lookup"><span data-stu-id="a79a9-228">Return types</span></span>

<span data-ttu-id="a79a9-229">Retur typen är ett kontrakt.</span><span class="sxs-lookup"><span data-stu-id="a79a9-229">Return type is a contract.</span></span> <span data-ttu-id="a79a9-230">Returvärdet konverteras till den förväntade typen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-230">The return value is converted to the expected type.</span></span>
<span data-ttu-id="a79a9-231">Om ingen returtyp anges är retur typen Void.</span><span class="sxs-lookup"><span data-stu-id="a79a9-231">If no return type is specified, the return type is void.</span></span> <span data-ttu-id="a79a9-232">Det finns ingen strömning av objekt och objekt kan inte skrivas till pipelinen avsiktligt eller av misstag.</span><span class="sxs-lookup"><span data-stu-id="a79a9-232">There is no streaming of objects and objects cannot be written to the pipeline either intentionally or by accident.</span></span>

### <a name="lexical-scoping-of-variables"></a><span data-ttu-id="a79a9-233">Lexikalt omfång av variabler</span><span class="sxs-lookup"><span data-stu-id="a79a9-233">Lexical scoping of variables</span></span>

<span data-ttu-id="a79a9-234">Nedan visas ett exempel på hur lexikalt scope fungerar i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="a79a9-234">The following shows an example of how lexical scoping works in this release.</span></span>

```powershell
$d = 42  # Script scope

function bar
{
    $d = 0  # Function scope
    [MyClass]::DoSomething()
}

class MyClass
{
    static [object] DoSomething()
    {
        return $d  # error, not found dynamically
        return $script:d # no error

        $d = $script:d
        return $d # no error, found lexically
    }
}

$v = bar
$v -eq $d # true
```

## <a name="example-create-custom-classes"></a><span data-ttu-id="a79a9-235">Exempel: skapa anpassade klasser</span><span class="sxs-lookup"><span data-stu-id="a79a9-235">Example: Create custom classes</span></span>

<span data-ttu-id="a79a9-236">I följande exempel skapas flera nya, anpassade klasser för att implementera ett HTML-dynamiskt StyleSheet-språk (DSL).</span><span class="sxs-lookup"><span data-stu-id="a79a9-236">The following example creates several new, custom classes to implement an HTML Dynamic Stylesheet Language (DSL).</span></span> <span data-ttu-id="a79a9-237">Exemplet lägger till hjälp funktioner för att skapa olika element typer som en del av klassen element, till exempel rubrik format och tabeller, eftersom typer inte kan användas utanför omfånget för en modul.</span><span class="sxs-lookup"><span data-stu-id="a79a9-237">The example adds helper functions to create specific element types as part of the element class, such as heading styles and tables, because types cannot be used outside the scope of a module.</span></span>

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
        $text += $Head
        $text += "`n</head>`n<body>`n"
        $text += $Body -join "`n" # Render all of the body elements
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
    [string] Render() { return "<title>$Title</title>" }
    [string] ToString() { return $this.Render() }
}

class Element
{
    [string] $Tag
    [string] $Text
    [hashtable] $Attributes
    [string] Render() {
        $attributesText= ""
        if ($Attributes)
        {
            foreach ($attr in $Attributes.Keys)
            {
                $attributesText = " $attr=`"$($Attributes[$attr])`""
            }
        }

        return "<${tag}${attributesText}>$text</$tag>`n"
    }
    [string] ToString() { return $this.Render() }
}

#
# Helper functions for creating specific element types on top of the classes.
# These are required because types aren't visible outside of the module.
#
function H1 {[Element] @{Tag = "H1"; Text = $args.foreach{$_} -join " "}}
function H2 {[Element] @{Tag = "H2"; Text = $args.foreach{$_} -join " "}}
function H3 {[Element] @{Tag = "H3"; Text = $args.foreach{$_} -join " "}}
function P  {[Element] @{Tag = "P" ; Text = $args.foreach{$_} -join " "}}
function B  {[Element] @{Tag = "B" ; Text = $args.foreach{$_} -join " "}}
function I  {[Element] @{Tag = "I" ; Text = $args.foreach{$_} -join " "}}
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
    $bodyText +=  $Properties.foreach{TH $_}
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
function TH  {([Element] @{Tag="TH"; Text=$args.foreach{$_} -join " "})}
function TR  {([Element] @{Tag="TR"; Text=$args.foreach{$_} -join " "})}
function TD  {([Element] @{Tag="TD"; Text=$args.foreach{$_} -join " "})}

function Style
{
    return  [Element]  @{
        Tag = "style"
        Text = "$args"
    }
}

# Takes a hash table, casts it to and HTML document
# and then returns the resulting type.
#
function Html ([HTML] $doc) { return $doc }
```

## <a name="see-also"></a><span data-ttu-id="a79a9-238">Se även</span><span class="sxs-lookup"><span data-stu-id="a79a9-238">See also</span></span>

[<span data-ttu-id="a79a9-239">about_DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a79a9-239">about_DesiredStateConfiguration</span></span>](../../Microsoft.PowerShell.Core/About/about_desiredstateconfiguration.md)

[<span data-ttu-id="a79a9-240">about_Enum</span><span class="sxs-lookup"><span data-stu-id="a79a9-240">about_Enum</span></span>](../../Microsoft.PowerShell.Core/About/about_Enum.md)

[<span data-ttu-id="a79a9-241">about_Hidden</span><span class="sxs-lookup"><span data-stu-id="a79a9-241">about_Hidden</span></span>](../../Microsoft.PowerShell.Core/About/about_hidden.md)

[<span data-ttu-id="a79a9-242">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="a79a9-242">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="a79a9-243">about_Methods</span><span class="sxs-lookup"><span data-stu-id="a79a9-243">about_Methods</span></span>](../../Microsoft.PowerShell.Core/About/about_Methods.md)

[<span data-ttu-id="a79a9-244">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a79a9-244">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](/powershell/scripting/dsc/resources/authoringResource)
