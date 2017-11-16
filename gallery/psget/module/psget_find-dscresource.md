---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Hitta DscResource
ms.openlocfilehash: 37ba7925d6f73c453126f25e0818b3f8839d3b3b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="find-dscresource"></a><span data-ttu-id="2dd5a-103">Hitta DscResource</span><span class="sxs-lookup"><span data-stu-id="2dd5a-103">Find-DscResource</span></span>

<span data-ttu-id="2dd5a-104">Söker efter DSC-resurser i moduler.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-104">Finds DSC Resources in modules.</span></span>

## <a name="description"></a><span data-ttu-id="2dd5a-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2dd5a-105">Description</span></span>

<span data-ttu-id="2dd5a-106">Hitta DscResource cmdleten hittar [önskade tillstånd Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resurser som ingår i moduler som matchar de angivna villkoren från registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-106">The Find-DscResource cmdlet finds [Desired State Configuration (DSC)](https://msdn.microsoft.com/en-us/PowerShell/dsc/overview) resources contained in modules that match the specified criteria from registered repositories.</span></span>
<span data-ttu-id="2dd5a-107">För varje modul som söker efter denna cmdlet returnerar hitta DscResource ett PSGetDscResourceInfo-objekt som du kan skicka vidare till Install-modulen för att installera modulerna som innehåller de resurser som denna cmdlet returnerar.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-107">For each module that this cmdlet finds, Find-DscResource returns a PSGetDscResourceInfo object that you can pipe to Install-Module to install the modules containing the resources that this cmdlet returns.</span></span>

<span data-ttu-id="2dd5a-108">DSC är en ny plattform i Windows PowerShell som gör att distribuera och hantera konfigurationsdata för programtjänster och hantera miljön där tjänsterna körs.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-108">DSC is a new management platform in Windows PowerShell that enables deploying and managing configuration data for software services and managing the environment in which these services run.</span></span>

<span data-ttu-id="2dd5a-109">Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-109">Desired State Configuration (DSC) Resources provide the building blocks for a DSC configuration.</span></span> <span data-ttu-id="2dd5a-110">En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-110">A resource exposes properties that can be configured (schema) and contains the PowerShell script functions that the Local Configuration Manager (LCM) calls to "make it so".</span></span>

<span data-ttu-id="2dd5a-111">En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-111">A resource can model something as generic as a file or as specific as an IIS server setting.</span></span> <span data-ttu-id="2dd5a-112">Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-112">Groups of like resources are combined in to a DSC Module, which organizes all the required files in to a structure that is portable and includes metadata to identify how the resources are intended to be used.</span></span>

- <span data-ttu-id="2dd5a-113">Hitta DscResource kan filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-113">Find-DscResource can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="2dd5a-114">Dessa parametrar kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-114">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="2dd5a-115">De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-115">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="2dd5a-116">Om parametern RequiredVersion inte anges returnerar hitta DscResource den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-116">If the RequiredVersion parameter is not specified, Find-DscResource returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="2dd5a-117">Om parametern RequiredVersion har angetts returnerar hitta DscResource endast versionen av den modul som exakt matchar den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-117">If the RequiredVersion parameter is specified, Find-DscResource only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="2dd5a-118">Hitta DscResource kan filtrera efter modulens med parametern - tagg</span><span class="sxs-lookup"><span data-stu-id="2dd5a-118">Find-DscResource can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="2dd5a-119">Hitta DscResource kan filtrera på databas-specifika sökspråk med parametern - Filter.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-119">Find-DscResource can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="2dd5a-120">Hitta DscResource kan filtrera efter moduler från alla eller fåtal registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="2dd5a-120">Find-DscResource can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="2dd5a-121">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="2dd5a-121">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="2dd5a-122">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="2dd5a-122">Cmdlet online help reference</span></span>

[<span data-ttu-id="2dd5a-123">Hitta DscResource</span><span class="sxs-lookup"><span data-stu-id="2dd5a-123">Find-DscResource</span></span>](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a><span data-ttu-id="2dd5a-124">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="2dd5a-124">Example commands</span></span>
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

