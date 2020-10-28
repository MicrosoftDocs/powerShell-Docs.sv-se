---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med PowerShell-klasser
description: Den här artikeln visar hur du skapar en enkel resurs som hanterar en fil i en angiven sökväg.
ms.openlocfilehash: 72a828795c29e10ff66f164b8871b0fea7a1e0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667325"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="fed32-104">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="fed32-104">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="fed32-105">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="fed32-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fed32-106">Med introduktionen av PowerShell-klasser i Windows PowerShell 5,0 kan du nu definiera en DSC-resurs genom att skapa en klass.</span><span class="sxs-lookup"><span data-stu-id="fed32-106">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="fed32-107">Klassen definierar både schemat och implementeringen av resursen, så det finns inget behov av att skapa en separat MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="fed32-107">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="fed32-108">Mappstrukturen för en klass baserad resurs är också enklare eftersom det inte behövs någon **DSCResources** -mapp.</span><span class="sxs-lookup"><span data-stu-id="fed32-108">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="fed32-109">I en klass-baserad DSC-resurs definieras schemat som egenskaper för klassen som kan ändras med attribut för att ange egenskaps typen.</span><span class="sxs-lookup"><span data-stu-id="fed32-109">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="fed32-110">Resursen implementeras av `Get()` , `Set()` -och `Test()` -metoder (motsvarar `Get-TargetResource` funktionerna, `Set-TargetResource` och `Test-TargetResource` i en skript resurs.</span><span class="sxs-lookup"><span data-stu-id="fed32-110">The resource is implemented by `Get()`, `Set()`, and `Test()` methods (equivalent to the `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions in a script resource.</span></span>

<span data-ttu-id="fed32-111">I den här artikeln ska vi skapa en enkel resurs med namnet **FileResource** som hanterar en fil i en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="fed32-111">In this article, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="fed32-112">Mer information om DSC-resurser finns i avsnittet om att [bygga anpassade konfigurations resurser för önskad tillstånds konfiguration i Windows PowerShell](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="fed32-112">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

> [!Note]
> <span data-ttu-id="fed32-113">Generiska samlingar stöds inte i klassbaserade resurser.</span><span class="sxs-lookup"><span data-stu-id="fed32-113">Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="fed32-114">Mappstruktur för en klass resurs</span><span class="sxs-lookup"><span data-stu-id="fed32-114">Folder structure for a class resource</span></span>

<span data-ttu-id="fed32-115">Skapa följande mappstruktur om du vill implementera en anpassad DSC-resurs med en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="fed32-115">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span>
<span data-ttu-id="fed32-116">Klassen definieras i `MyDscResource.psm1` och modul manifestet definieras i `MyDscResource.psd1` .</span><span class="sxs-lookup"><span data-stu-id="fed32-116">The class is defined in `MyDscResource.psm1` and the module manifest is defined in `MyDscResource.psd1`.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="fed32-117">Skapa klassen</span><span class="sxs-lookup"><span data-stu-id="fed32-117">Create the class</span></span>

<span data-ttu-id="fed32-118">Du kan använda nyckelordet class för att skapa en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="fed32-118">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="fed32-119">Om du vill ange att en klass är en DSC-resurs använder du- `DscResource()` attributet.</span><span class="sxs-lookup"><span data-stu-id="fed32-119">To specify that a class is a DSC resource, use the `DscResource()` attribute.</span></span> <span data-ttu-id="fed32-120">Namnet på klassen är namnet på DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="fed32-120">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="fed32-121">Deklarera egenskaper</span><span class="sxs-lookup"><span data-stu-id="fed32-121">Declare properties</span></span>

<span data-ttu-id="fed32-122">DSC-resursschemat definieras som egenskaper för klassen.</span><span class="sxs-lookup"><span data-stu-id="fed32-122">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="fed32-123">Vi deklarerar tre egenskaper på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="fed32-123">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="fed32-124">Observera att egenskaperna ändras efter attribut.</span><span class="sxs-lookup"><span data-stu-id="fed32-124">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="fed32-125">Innebörden av attributen är följande:</span><span class="sxs-lookup"><span data-stu-id="fed32-125">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="fed32-126">**DscProperty (nyckel)** : egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="fed32-126">**DscProperty(Key)** : The property is required.</span></span> <span data-ttu-id="fed32-127">Egenskapen är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="fed32-127">The property is a key.</span></span> <span data-ttu-id="fed32-128">Värdena för alla egenskaper som har marker ATS som nycklar måste kombineras för att unikt identifiera en resurs instans i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fed32-128">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="fed32-129">**DscProperty (obligatorisk)** : egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="fed32-129">**DscProperty(Mandatory)** : The property is required.</span></span>
- <span data-ttu-id="fed32-130">**DscProperty (NotConfigurable)** : egenskapen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="fed32-130">**DscProperty(NotConfigurable)** : The property is read-only.</span></span> <span data-ttu-id="fed32-131">Egenskaper som marker ATS med det här attributet kan inte ställas in med en konfiguration, men fylls i med `Get()` metoden när de är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="fed32-131">Properties marked with this attribute cannot be set by a configuration, but are populated by the `Get()` method when present.</span></span>
- <span data-ttu-id="fed32-132">**DscProperty ()** : egenskapen kan konfigureras, men det är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="fed32-132">**DscProperty()** : The property is configurable, but it is not required.</span></span>

<span data-ttu-id="fed32-133">`$Path`Egenskaperna och `$SourcePath` är båda strängarna.</span><span class="sxs-lookup"><span data-stu-id="fed32-133">The `$Path` and `$SourcePath` properties are both strings.</span></span> <span data-ttu-id="fed32-134">`$CreationTime`Är en [datetime](/dotnet/api/system.datetime) -egenskap.</span><span class="sxs-lookup"><span data-stu-id="fed32-134">The `$CreationTime` is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="fed32-135">`$Ensure`Egenskapen är en uppräknings typ som definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="fed32-135">The `$Ensure` property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="fed32-136">Implementera metoderna</span><span class="sxs-lookup"><span data-stu-id="fed32-136">Implementing the methods</span></span>

<span data-ttu-id="fed32-137">Metoderna, och `Get()` `Set()` `Test()` är likvärdiga med `Get-TargetResource` `Set-TargetResource` funktionerna, och `Test-TargetResource` i en skript resurs.</span><span class="sxs-lookup"><span data-stu-id="fed32-137">The `Get()`, `Set()`, and `Test()` methods are analogous to the `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions in a script resource.</span></span>

<span data-ttu-id="fed32-138">Den här koden inkluderar även `CopyFile()` funktionen, en hjälp funktion som kopierar filen från `$SourcePath` till `$Path` .</span><span class="sxs-lookup"><span data-stu-id="fed32-138">This code also includes the `CopyFile()` function, a helper function that copies the file from `$SourcePath` to `$Path`.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="fed32-139">Den fullständiga filen</span><span class="sxs-lookup"><span data-stu-id="fed32-139">The complete file</span></span>

<span data-ttu-id="fed32-140">Den fullständiga klass filen följer.</span><span class="sxs-lookup"><span data-stu-id="fed32-140">The complete class file follows.</span></span>

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
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
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
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
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
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
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
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="fed32-141">Skapa ett manifest</span><span class="sxs-lookup"><span data-stu-id="fed32-141">Create a manifest</span></span>

<span data-ttu-id="fed32-142">Om du vill göra en klass baserad resurs tillgänglig för DSC-motorn måste du inkludera en `DscResourcesToExport` instruktion i manifest filen som instruerar modulen att exportera resursen.</span><span class="sxs-lookup"><span data-stu-id="fed32-142">To make a class-based resource available to the DSC engine, you must include a `DscResourcesToExport` statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="fed32-143">Vårt manifest ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="fed32-143">Our manifest looks like this:</span></span>

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

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="fed32-144">Testa resursen</span><span class="sxs-lookup"><span data-stu-id="fed32-144">Test the resource</span></span>

<span data-ttu-id="fed32-145">När du har sparat klass-och manifest filerna i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="fed32-145">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="fed32-146">Information om hur du kör en DSC-konfiguration finns i [Konfigurera konfigurationer](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="fed32-146">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="fed32-147">Följande konfiguration kommer att kontrol lera om filen `c:\test\test.txt` finns och kopierar filen från `c:\test.txt` (du bör skapa `c:\test.txt` innan du kör konfigurationen).</span><span class="sxs-lookup"><span data-stu-id="fed32-147">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="fed32-148">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="fed32-148">Supporting PsDscRunAsCredential</span></span>

> <span data-ttu-id="fed32-149">Lägg **PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fed32-149">[Note] **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="fed32-150">Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="fed32-150">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span> <span data-ttu-id="fed32-151">Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="fed32-151">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="fed32-152">Kräv eller Tillåt inte PsDscRunAsCredential för din resurs</span><span class="sxs-lookup"><span data-stu-id="fed32-152">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="fed32-153">`DscResource()`Attributet använder en valfri parameter **RunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="fed32-153">The `DscResource()` attribute takes an optional parameter **RunAsCredential** .</span></span> <span data-ttu-id="fed32-154">Den här parametern använder ett av tre värden:</span><span class="sxs-lookup"><span data-stu-id="fed32-154">This parameter takes one of three values:</span></span>

- <span data-ttu-id="fed32-155">`Optional`**PsDscRunAsCredential** är valfritt för konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="fed32-155">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="fed32-156">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="fed32-156">This is the default value.</span></span>
- <span data-ttu-id="fed32-157">`Mandatory`**PsDscRunAsCredential** måste användas för alla konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="fed32-157">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="fed32-158">`NotSupported` Konfigurationer som anropar den här resursen kan inte använda **PsDscRunAsCredential** .</span><span class="sxs-lookup"><span data-stu-id="fed32-158">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential** .</span></span>
- <span data-ttu-id="fed32-159">`Default` Samma som `Optional` .</span><span class="sxs-lookup"><span data-stu-id="fed32-159">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="fed32-160">Använd till exempel följande attribut för att ange att den anpassade resursen inte stöder användning av **PsDscRunAsCredential** :</span><span class="sxs-lookup"><span data-stu-id="fed32-160">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential** :</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="fed32-161">Deklarera flera klass resurser i en modul</span><span class="sxs-lookup"><span data-stu-id="fed32-161">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="fed32-162">En modul kan definiera flera klassbaserade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="fed32-162">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="fed32-163">Du kan skapa mappstrukturen på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="fed32-163">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="fed32-164">Definiera den första resursen i `<ModuleName>.psm1` filen och efterföljande resurser under **DSCResources** -mappen.</span><span class="sxs-lookup"><span data-stu-id="fed32-164">Define the first resource in the `<ModuleName>.psm1` file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

1. <span data-ttu-id="fed32-165">Definiera alla resurser under mappen **DSCResources**</span><span class="sxs-lookup"><span data-stu-id="fed32-165">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="fed32-166">I exemplen ovan lägger du till eventuella PSM1-filer under **DSCResources** till **NestedModules** -nyckeln i PSD1-filen.</span><span class="sxs-lookup"><span data-stu-id="fed32-166">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="fed32-167">Komma åt användar kontexten</span><span class="sxs-lookup"><span data-stu-id="fed32-167">Access the user context</span></span>

<span data-ttu-id="fed32-168">Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den automatiska variabeln `$global:PsDscContext` .</span><span class="sxs-lookup"><span data-stu-id="fed32-168">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="fed32-169">Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:</span><span class="sxs-lookup"><span data-stu-id="fed32-169">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="fed32-170">Se även</span><span class="sxs-lookup"><span data-stu-id="fed32-170">See Also</span></span>

[<span data-ttu-id="fed32-171">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fed32-171">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
