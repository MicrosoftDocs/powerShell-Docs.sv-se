---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med PowerShell-klasser
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941161"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="a8bdd-103">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="a8bdd-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="a8bdd-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="a8bdd-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="a8bdd-105">Med introduktionen av PowerShell-klasser i Windows PowerShell 5,0 kan du nu definiera en DSC-resurs genom att skapa en klass.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="a8bdd-106">Klassen definierar både schemat och implementeringen av resursen, så det finns inget behov av att skapa en separat MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="a8bdd-107">Mappstrukturen för en klass baserad resurs är också enklare eftersom det inte behövs någon **DSCResources** -mapp.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="a8bdd-108">I en klass-baserad DSC-resurs definieras schemat som egenskaper för klassen som kan ändras med attribut för att ange egenskaps typen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="a8bdd-109">Resursen implementeras av **Get ()**, **set ()** och **test ()** -metoder (motsvarar funktionerna **Get-TargetResource**, **set-TargetResource**och **test-TargetResource** i en skript resurs.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="a8bdd-110">I det här avsnittet ska vi skapa en enkel resurs med namnet **FileResource** som hanterar en fil i en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="a8bdd-111">Mer information om DSC-resurser finns i avsnittet om att [bygga anpassade konfigurations resurser för önskad tillstånds konfiguration i Windows PowerShell](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="a8bdd-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="a8bdd-112">**Obs:** Generiska samlingar stöds inte i klassbaserade resurser.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="a8bdd-113">Mappstruktur för en klass resurs</span><span class="sxs-lookup"><span data-stu-id="a8bdd-113">Folder structure for a class resource</span></span>

<span data-ttu-id="a8bdd-114">Skapa följande mappstruktur om du vill implementera en anpassad DSC-resurs med en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="a8bdd-115">Klassen definieras i **MyDscResource. psm1** och modul manifestet definieras i **MyDscResource. psd1**.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="a8bdd-116">Skapa klassen</span><span class="sxs-lookup"><span data-stu-id="a8bdd-116">Create the class</span></span>

<span data-ttu-id="a8bdd-117">Du kan använda nyckelordet class för att skapa en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="a8bdd-118">Om du vill ange att en klass är en DSC-resurs använder du attributet **dscresource Keyword Supports ()** .</span><span class="sxs-lookup"><span data-stu-id="a8bdd-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="a8bdd-119">Namnet på klassen är namnet på DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="a8bdd-120">Deklarera egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8bdd-120">Declare properties</span></span>

<span data-ttu-id="a8bdd-121">DSC-resursschemat definieras som egenskaper för klassen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="a8bdd-122">Vi deklarerar tre egenskaper på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="a8bdd-123">Observera att egenskaperna ändras efter attribut.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="a8bdd-124">Innebörden av attributen är följande:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="a8bdd-125">**DscProperty (nyckel)**: egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="a8bdd-126">Egenskapen är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-126">The property is a key.</span></span> <span data-ttu-id="a8bdd-127">Värdena för alla egenskaper som har marker ATS som nycklar måste kombineras för att unikt identifiera en resurs instans i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="a8bdd-128">**DscProperty (obligatorisk)**: egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="a8bdd-129">**DscProperty (NotConfigurable)**: egenskapen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="a8bdd-130">Egenskaper som marker ATS med det här attributet kan inte anges med en konfiguration, men de fylls med **Get ()** -metoden när den är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="a8bdd-131">**DscProperty ()**: egenskapen kan konfigureras, men det är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="a8bdd-132">Egenskaperna **$Path** och **$SourcePath** är båda strängarna.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="a8bdd-133">**$CreationTime** är en [datetime](/dotnet/api/system.datetime) -egenskap.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="a8bdd-134">Egenskapen **$ensure** är en uppräknings typ som definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="a8bdd-135">Implementera metoderna</span><span class="sxs-lookup"><span data-stu-id="a8bdd-135">Implementing the methods</span></span>

<span data-ttu-id="a8bdd-136">Metoderna **Get**-TargetResource, set **()** och **test ()** är likvärdiga med funktionerna **Get-**, **set-TargetResource**och **test-TargetResource** i en skript resurs.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="a8bdd-137">Den här koden inkluderar även funktionen CopyFile (), en hjälp funktion som kopierar filen från **$SourcePath** till **$Path**.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="a8bdd-138">Den fullständiga filen</span><span class="sxs-lookup"><span data-stu-id="a8bdd-138">The complete file</span></span>

<span data-ttu-id="a8bdd-139">Den fullständiga klass filen följer.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-139">The complete class file follows.</span></span>

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

## <a name="create-a-manifest"></a><span data-ttu-id="a8bdd-140">Skapa ett manifest</span><span class="sxs-lookup"><span data-stu-id="a8bdd-140">Create a manifest</span></span>

<span data-ttu-id="a8bdd-141">Om du vill göra en klass baserad resurs tillgänglig för DSC-motorn måste du inkludera en **DscResourcesToExport** -instruktion i manifest filen som instruerar modulen att exportera resursen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="a8bdd-142">Vårt manifest ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="a8bdd-143">Testa resursen</span><span class="sxs-lookup"><span data-stu-id="a8bdd-143">Test the resource</span></span>

<span data-ttu-id="a8bdd-144">När du har sparat klass-och manifest filerna i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="a8bdd-145">Information om hur du kör en DSC-konfiguration finns i [Konfigurera konfigurationer](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="a8bdd-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="a8bdd-146">Följande konfiguration kommer att kontrol lera om filen `c:\test\test.txt` finns och kopierar filen från `c:\test.txt` (du bör skapa `c:\test.txt` innan du kör konfigurationen).</span><span class="sxs-lookup"><span data-stu-id="a8bdd-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="a8bdd-147">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a8bdd-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="a8bdd-148">**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="a8bdd-149">Du kan använda egenskapen **PsDscRunAsCredential** i resurs blocket [DSC-konfigurationer](../configurations/configurations.md) för att ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="a8bdd-150">Mer information finns i [köra DSC med](../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="a8bdd-151">Kräv eller Tillåt inte PsDscRunAsCredential för din resurs</span><span class="sxs-lookup"><span data-stu-id="a8bdd-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="a8bdd-152">Attributet **dscresource Keyword Supports ()** använder en valfri parameter **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="a8bdd-153">Den här parametern använder ett av tre värden:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="a8bdd-154">`Optional`**PsDscRunAsCredential** är valfritt för konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="a8bdd-155">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-155">This is the default value.</span></span>
- <span data-ttu-id="a8bdd-156">`Mandatory`**PsDscRunAsCredential** måste användas för alla konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="a8bdd-157">`NotSupported`Konfigurationer som anropar den här resursen kan inte använda **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="a8bdd-158">`Default`Samma som `Optional`.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="a8bdd-159">Använd till exempel följande attribut för att ange att den anpassade resursen inte stöder användning av **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="a8bdd-160">Deklarera flera klass resurser i en modul</span><span class="sxs-lookup"><span data-stu-id="a8bdd-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="a8bdd-161">En modul kan definiera flera klassbaserade DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="a8bdd-162">Du kan skapa mappstrukturen på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="a8bdd-163">Definiera den första resursen i filen "<ModuleName>. psm1" och efterföljande resurser i mappen **DSCResources** .</span><span class="sxs-lookup"><span data-stu-id="a8bdd-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="a8bdd-164">Definiera alla resurser under mappen **DSCResources**</span><span class="sxs-lookup"><span data-stu-id="a8bdd-164">Define all resources under the **DSCResources** folder.</span></span>

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
> <span data-ttu-id="a8bdd-165">I exemplen ovan lägger du till eventuella PSM1-filer under **DSCResources** till **NestedModules** -nyckeln i PSD1-filen.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="a8bdd-166">Komma åt användar kontexten</span><span class="sxs-lookup"><span data-stu-id="a8bdd-166">Access the user context</span></span>

<span data-ttu-id="a8bdd-167">Om du vill komma åt användar kontexten inifrån en anpassad resurs kan du använda den `$global:PsDscContext`automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="a8bdd-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="a8bdd-168">Till exempel kan följande kod skriva användar kontexten som resursen körs till i utförlig utdataström:</span><span class="sxs-lookup"><span data-stu-id="a8bdd-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="a8bdd-169">Se även</span><span class="sxs-lookup"><span data-stu-id="a8bdd-169">See Also</span></span>

[<span data-ttu-id="a8bdd-170">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a8bdd-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
