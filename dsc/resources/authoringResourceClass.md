---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skriva en anpassad DSC-resurs med PowerShell-klasser
ms.openlocfilehash: 0759685b04688f574d72b62a15833832ad19e816
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405188"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="1473c-103">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="1473c-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="1473c-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1473c-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="1473c-105">Med introduktionen av PowerShell-klasser i Windows PowerShell 5.0, kan du nu ange en DSC-resurs genom att skapa en klass.</span><span class="sxs-lookup"><span data-stu-id="1473c-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="1473c-106">Klassen definierar både schemat och implementeringen av resurs, så du behöver inte skapa en separat MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="1473c-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="1473c-107">Mappstrukturen för en MOF-baserade resurs är också enklare eftersom en **DSCResources** mappen är inte nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="1473c-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="1473c-108">I en klassbaserade DSC resursen definieras schemat som egenskaper för klassen som kan ändras med attribut som ska ange typen av egenskap...</span><span class="sxs-lookup"><span data-stu-id="1473c-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="1473c-109">Resursen har implementerats av **Get()**, **Set()**, och **Test()** metoder (motsvarar den **Get-TargetResource**, **Set-TargetResource**, och **Test TargetResource** funktioner i en resurs för skript.</span><span class="sxs-lookup"><span data-stu-id="1473c-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="1473c-110">I det här avsnittet skapar vi en enkel resurs med namnet **FileResource** som hanterar en fil i en angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="1473c-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="1473c-111">Mer information om DSC-resurser finns i [skapa anpassade Windows PowerShell Desired State Configuration resurser](authoringResource.md)</span><span class="sxs-lookup"><span data-stu-id="1473c-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="1473c-112">**Obs:** Allmän samlingar stöds inte i MOF-baserade resurser.</span><span class="sxs-lookup"><span data-stu-id="1473c-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="1473c-113">Mappstruktur för en resurs för klass</span><span class="sxs-lookup"><span data-stu-id="1473c-113">Folder structure for a class resource</span></span>

<span data-ttu-id="1473c-114">Skapa följande mappstruktur för att implementera en anpassad DSC-resurs med en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="1473c-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="1473c-115">Klassen är definierad i **MyDscResource.psm1** och modulmanifestet har definierats i **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="1473c-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        |- MyDscResource.psm1
           MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="1473c-116">Skapa klassen</span><span class="sxs-lookup"><span data-stu-id="1473c-116">Create the class</span></span>

<span data-ttu-id="1473c-117">Du kan använda nyckelordet class för att skapa en PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="1473c-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="1473c-118">Om du vill ange att en klass är en DSC-resurs, använda den **DscResource()** attribut.</span><span class="sxs-lookup"><span data-stu-id="1473c-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="1473c-119">Namnet på klassen är namnet på den DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="1473c-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="1473c-120">Deklarera egenskaper</span><span class="sxs-lookup"><span data-stu-id="1473c-120">Declare properties</span></span>

<span data-ttu-id="1473c-121">Schema för DSC-resurs har definierats som egenskaper i klassen.</span><span class="sxs-lookup"><span data-stu-id="1473c-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="1473c-122">Vi deklarera tre egenskaper enligt följande.</span><span class="sxs-lookup"><span data-stu-id="1473c-122">We declare three properties as follows.</span></span>

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

<span data-ttu-id="1473c-123">Observera att egenskaperna ändras av attribut.</span><span class="sxs-lookup"><span data-stu-id="1473c-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="1473c-124">Enligt attribut är följande:</span><span class="sxs-lookup"><span data-stu-id="1473c-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="1473c-125">**DscProperty(Key)**: Egenskapen krävs.</span><span class="sxs-lookup"><span data-stu-id="1473c-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="1473c-126">Egenskapen är en nyckel.</span><span class="sxs-lookup"><span data-stu-id="1473c-126">The property is a key.</span></span> <span data-ttu-id="1473c-127">Värdena för alla egenskaper markerats som nycklar måste kombineras för att unikt identifiera en resursinstans i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1473c-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="1473c-128">**DscProperty(Mandatory)**: Egenskapen krävs.</span><span class="sxs-lookup"><span data-stu-id="1473c-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="1473c-129">**DscProperty(NotConfigurable)**: Egenskapen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="1473c-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="1473c-130">Egenskaper som är markerade med det här attributet kan inte anges av en konfiguration, men fylls med den **Get()** metod när det finns.</span><span class="sxs-lookup"><span data-stu-id="1473c-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="1473c-131">**DscProperty()**: Egenskapen kan konfigureras, men det är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="1473c-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="1473c-132">Den **$Path** och **$SourcePath** egenskaper är båda strängar.</span><span class="sxs-lookup"><span data-stu-id="1473c-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="1473c-133">Den **$CreationTime** är en [DateTime](/dotnet/api/system.datetime) egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1473c-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="1473c-134">Den **$Ensure** egenskapen är en uppräkningstyp definieras enligt följande.</span><span class="sxs-lookup"><span data-stu-id="1473c-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="1473c-135">Implementera metoderna</span><span class="sxs-lookup"><span data-stu-id="1473c-135">Implementing the methods</span></span>

<span data-ttu-id="1473c-136">Den **Get()**, **Set()**, och **Test()** metoder är detsamma som det **Get-TargetResource**, **Set-TargetResource** , och **Test TargetResource** funktioner i en resurs för skript.</span><span class="sxs-lookup"><span data-stu-id="1473c-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="1473c-137">Den här koden innehåller också funktionen CopyFile() en hjälpfunktionen som kopierar filen från **$SourcePath** till **$Path**.</span><span class="sxs-lookup"><span data-stu-id="1473c-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

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

### <a name="the-complete-file"></a><span data-ttu-id="1473c-138">Den fullständiga filen</span><span class="sxs-lookup"><span data-stu-id="1473c-138">The complete file</span></span>
<span data-ttu-id="1473c-139">Fullständig klassfil följer.</span><span class="sxs-lookup"><span data-stu-id="1473c-139">The complete class file follows.</span></span>

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


## <a name="create-a-manifest"></a><span data-ttu-id="1473c-140">Skapa ett manifest</span><span class="sxs-lookup"><span data-stu-id="1473c-140">Create a manifest</span></span>

<span data-ttu-id="1473c-141">Om du vill göra en MOF-baserade resurs ska vara tillgängliga för DSC-motorn måste du inkludera en **DscResourcesToExport** instruktionen i manifestfilen som instruerar modulen att exportera resursen.</span><span class="sxs-lookup"><span data-stu-id="1473c-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="1473c-142">Vår manifest ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="1473c-142">Our manifest looks like this:</span></span>

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

## <a name="test-the-resource"></a><span data-ttu-id="1473c-143">Testa resursen</span><span class="sxs-lookup"><span data-stu-id="1473c-143">Test the resource</span></span>

<span data-ttu-id="1473c-144">När du har sparat den klass och manifestfiler i mappstrukturen enligt beskrivningen ovan, kan du skapa en konfiguration som använder den nya resursen.</span><span class="sxs-lookup"><span data-stu-id="1473c-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="1473c-145">Information om hur du kör en DSC-konfiguration finns i [tillämpa konfigurationer](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="1473c-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="1473c-146">Följande konfiguration ska kontrollera om filen vid `c:\test\test.txt` finns och, om inte, kopierar du filen från `c:\test.txt` (du bör skapa `c:\test.txt` innan du kör konfigurationen).</span><span class="sxs-lookup"><span data-stu-id="1473c-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

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

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="1473c-147">Stöd för PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1473c-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="1473c-148">**Obs:** **PsDscRunAsCredential** stöds i PowerShell 5.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1473c-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="1473c-149">Den **PsDscRunAsCredential** egenskapen kan användas i [DSC-konfigurationer](../configurations/configurations.md) resource förhindra om du vill ange att resursen ska köras under en angiven uppsättning autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1473c-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="1473c-150">Mer information finns i [kör DSC med autentiseringsuppgifterna för användaren](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1473c-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="1473c-151">Aktivera eller inaktivera PsDscRunAsCredential för din resurs</span><span class="sxs-lookup"><span data-stu-id="1473c-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="1473c-152">Den **DscResource()** attributet tar en valfri parameter **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="1473c-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="1473c-153">Den här parametern antar ett av tre värden:</span><span class="sxs-lookup"><span data-stu-id="1473c-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="1473c-154">`Optional` **PsDscRunAsCredential** är valfritt för konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="1473c-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="1473c-155">Det här är standardkonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1473c-155">This is the default value.</span></span>
- <span data-ttu-id="1473c-156">`Mandatory` **PsDscRunAsCredential** måste användas för alla konfigurationer som anropar den här resursen.</span><span class="sxs-lookup"><span data-stu-id="1473c-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="1473c-157">`NotSupported` Konfigurationer som anropar den här resursen kan inte använda **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="1473c-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="1473c-158">`Default` Samma som `Optional`.</span><span class="sxs-lookup"><span data-stu-id="1473c-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="1473c-159">Till exempel använda följande attribut för att ange att din anpassade resursen inte stöder användning av **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="1473c-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="access-the-user-context"></a><span data-ttu-id="1473c-160">Komma åt användarkontexten</span><span class="sxs-lookup"><span data-stu-id="1473c-160">Access the user context</span></span>

<span data-ttu-id="1473c-161">Du kan använda automatiska variabeln för att komma åt användarkontext från inom en anpassad resurs `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="1473c-161">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="1473c-162">Följande kod skulle till exempel skriva användarkontext där resursen körs till en dataström med utförliga utdata:</span><span class="sxs-lookup"><span data-stu-id="1473c-162">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="1473c-163">Se även</span><span class="sxs-lookup"><span data-stu-id="1473c-163">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="1473c-164">Begrepp</span><span class="sxs-lookup"><span data-stu-id="1473c-164">Concepts</span></span>
[<span data-ttu-id="1473c-165">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="1473c-165">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)