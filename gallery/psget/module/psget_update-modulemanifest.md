---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Uppdatera ModuleManifest
ms.openlocfilehash: 45f40f753af17e82c83dbf57dea13749ba626503
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="update-modulemanifest"></a><span data-ttu-id="87c3c-103">Uppdatera ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="87c3c-103">Update-ModuleManifest</span></span>
<span data-ttu-id="87c3c-104">Uppdaterar en modul manifestfil.</span><span class="sxs-lookup"><span data-stu-id="87c3c-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="87c3c-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87c3c-105">Description</span></span>

<span data-ttu-id="87c3c-106">Cmdlet Update ModuleManifest uppdaterar en modulfilen manifestet (.psd1).</span><span class="sxs-lookup"><span data-stu-id="87c3c-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="87c3c-107">Obs!</span><span class="sxs-lookup"><span data-stu-id="87c3c-107">Notes</span></span>
    - <span data-ttu-id="87c3c-108">DscResourcesToExport stöds endast på den senaste PowerShell version 5.0.</span><span class="sxs-lookup"><span data-stu-id="87c3c-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="87c3c-109">Vi kan inte uppdatera om du kör på lägre versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87c3c-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="87c3c-110">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="87c3c-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="87c3c-111">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="87c3c-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="87c3c-112">Uppdatera ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="87c3c-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="87c3c-113">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="87c3c-113">Example commands</span></span>

<span data-ttu-id="87c3c-114">Den här nya cmdleten används för att uppdatera manifestfilen med indata egenskapsvärden.</span><span class="sxs-lookup"><span data-stu-id="87c3c-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="87c3c-115">Det tar för alla parametrar som ny ModuleManifest.</span><span class="sxs-lookup"><span data-stu-id="87c3c-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="87c3c-116">Vi upptäcker att modulen författare mycket vill ange ”\*” i exporterade värden, till exempel FunctionsToExport, CmdletsToExport, osv. Under modulen publicering till PowerShell-galleriet fylls Ospecificerad funktioner och kommandon inte korrekt till galleriet.</span><span class="sxs-lookup"><span data-stu-id="87c3c-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="87c3c-117">Därför föreslår vi modulen författare uppdatera sina manifest med rätt värden.</span><span class="sxs-lookup"><span data-stu-id="87c3c-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="87c3c-118">Om du har moduler som har exporterat egenskaper fylls uppdatering ModuleManifest den angivna manifestfilen med information från exporterade funktioner, cmdletar, variabler etc:</span><span class="sxs-lookup"><span data-stu-id="87c3c-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="87c3c-119">Efter uppdateringen ModuleManifest:</span><span class="sxs-lookup"><span data-stu-id="87c3c-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="87c3c-120">För varje modul finns också metadatafält som är kopplade till den.</span><span class="sxs-lookup"><span data-stu-id="87c3c-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="87c3c-121">Du kan använda uppdateringen ModuleManifest att fylla i fälten under PrivateData för att kunna visas korrekt metadata på PowrShell galleriet.</span><span class="sxs-lookup"><span data-stu-id="87c3c-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="87c3c-122">PrivateData hashtable från mallen manifestfilen har följande egenskaper</span><span class="sxs-lookup"><span data-stu-id="87c3c-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```