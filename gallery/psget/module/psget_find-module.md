---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: "Sök-modul"
ms.openlocfilehash: 5c878a04d186f7f5970fba9e7f3cdb480cef21f6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="find-module"></a><span data-ttu-id="d5c49-103">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="d5c49-103">Find-Module</span></span>
<span data-ttu-id="d5c49-104">Söker efter moduler från en online-galleriet som uppfyller angivna villkor.</span><span class="sxs-lookup"><span data-stu-id="d5c49-104">Finds modules from an online gallery that match specified criteria.</span></span>

## <a name="description"></a><span data-ttu-id="d5c49-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d5c49-105">Description</span></span>
<span data-ttu-id="d5c49-106">Hitta modulen identifierar moduler från registrerade databaser som matchar de angivna kriterierna.</span><span class="sxs-lookup"><span data-stu-id="d5c49-106">Find-Module discovers the modules from registered repositories that matches the specified criteria.</span></span>
<span data-ttu-id="d5c49-107">För varje modul som hittas returnerar hitta modulen ett PSRepositoryItemInfo-objekt som eventuellt kan skickas till installera modulen för att installera modulerna.</span><span class="sxs-lookup"><span data-stu-id="d5c49-107">For each module found, Find-Module returns a PSRepositoryItemInfo object which can optionally be piped to Install-Module for installing the modules.</span></span>

- <span data-ttu-id="d5c49-108">Hitta modulen kan filter baserat på modulen innehåll med-kommandot, - DscResource, - RoleCapability och - innehåller parametrar.</span><span class="sxs-lookup"><span data-stu-id="d5c49-108">Find-Module can filter based on module contents with the -Command, -DscResource, -RoleCapability and -Includes parameters.</span></span>
- <span data-ttu-id="d5c49-109">Hitta modulen kan filtrera med parametrarna: MinimumVersion, MaximumVersion, RequiredVersion, allaversioner.</span><span class="sxs-lookup"><span data-stu-id="d5c49-109">Find-Module can filter with version parameters: MinimumVersion, MaximumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="d5c49-110">Dessa parametrar är ömsesidigt uteslutande, utom MinmimumVersion och MaximumVersion.</span><span class="sxs-lookup"><span data-stu-id="d5c49-110">These parameters are mutually exclusive, except MinmimumVersion and MaximumVersion.</span></span>
  - <span data-ttu-id="d5c49-111">De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d5c49-111">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="d5c49-112">Om parametern RequiredVersion inte anges returnerar hitta modulen den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.</span><span class="sxs-lookup"><span data-stu-id="d5c49-112">If the RequiredVersion parameter is not specified, Find-Module returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span> 
  - <span data-ttu-id="d5c49-113">Om parametern RequiredVersion har angetts returnerar hitta modulen endast version av modulen som exakt matchar den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="d5c49-113">If the RequiredVersion parameter is specified, Find-Module only returns the version of module that exactly matches the specified version.</span></span>
- <span data-ttu-id="d5c49-114">Hitta modulen kan filtrera efter modulens med parametern - tagg</span><span class="sxs-lookup"><span data-stu-id="d5c49-114">Find-Module can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="d5c49-115">Hitta modulen kan filtrera på databas-specifika sökspråk med parametern - Filter.</span><span class="sxs-lookup"><span data-stu-id="d5c49-115">Find-Module can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="d5c49-116">Hitta modulen kan filtrera efter moduler från alla eller fåtal registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="d5c49-116">Find-Module can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="d5c49-117">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="d5c49-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="d5c49-118">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="d5c49-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="d5c49-119">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="d5c49-119">Find-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398574)

## <a name="example-commands"></a><span data-ttu-id="d5c49-120">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="d5c49-120">Example commands</span></span>
```powershell
# Find a specific module
Find-Module Azure

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.3.2      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management

# Find multiple modules
Find-Module Azure,AzureRM

# Find modules with wildcards in -Name
Find-Module -Name AzureRM*

# Find all versions of a module
Find-Module -Name PSReadline -AllVersions

# Find a module with -MinimumVersion. 
# With MinimumVersion we can find a module whose version is greate than or equal to the specified MinimumVersion value.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12

# Find a module with MaximumVersion
Find-Module -Name PSReadline -MaximumVersion 1.0.0.13

# Find a module with both MinimumVersion and MaximumVersion range.
Find-Module -Name PSReadline -MinimumVersion 1.0.0.12 -MaximumVersion 1.0.0.13

# Find a module with exact version
Find-Module -Name AzureRM -RequiredVersion 1.3.2

# Find a module from the specified repository
Find-Module -Name Contoso -Repository MyLocalRepo

# Find available modules from all registered repositories
Find-Module

# Find available modules from few registered repositories
Find-Module -Repository PSGallery,PrivatePSGallery

# Find a module along with its dependencies
Find-Module -Name AzureRM -IncludeDependencies

# Find all modules with Dsc resources
Find-Module -Includes DscResource

# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

# Find all modules with cmdlets
Find-Module -Includes Cmdlet

# Find all modules with functions
Find-Module -Includes Function

# Find all modules with Role Capabilities
Find-Module -Includes RoleCapability

# Find all modules with the specified Role Capability name
Find-Module -RoleCapability RoleCap1
Find-Module -RoleCapability RoleCap2 -Includes RoleCapability

# Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Cmdlet
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer -Includes Function

# Find modules with -Filter based search. -Filter searches in description and names
Find-Module -Filter Cookbook
Find-Module -Filter RBAC
Find-Module -Filter 'App Domain' -Includes 'DscResource'

# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

# Properties of Find-Module returned object
Find-Module AzureRM.Profile | Format-List * -Force

Name                       : AzureRM.profile
Version                    : 1.0.8
Type                       : Module
Description                : Microsoft Azure PowerShell - Profile credential management cmdlets for Azure Resource
                             Manager
Author                     : Microsoft Corporation
CompanyName                : {elogeel, azure-sdk}
Copyright                  : Microsoft Corporation. All rights reserved.
PublishedDate              : 5/4/2016 9:40:33 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 : https://raw.githubusercontent.com/Azure/azure-powershell/dev/LICENSE.txt
ProjectUri                 : https://github.com/Azure/azure-powershell
IconUri                    :
Tags                       : {PSModule}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               : https://github.com/Azure/azure-powershell/blob/dev/ChangeLog.md
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {downloadCount, description, copyright, FileList...}

```

