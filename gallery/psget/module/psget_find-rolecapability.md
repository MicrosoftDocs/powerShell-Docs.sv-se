---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Hitta RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a><span data-ttu-id="a5fa4-103">Hitta RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a5fa4-103">Find-RoleCapability</span></span>

<span data-ttu-id="a5fa4-104">Söker efter roll funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-104">Finds role capabilities in modules.</span></span>

## <a name="description"></a><span data-ttu-id="a5fa4-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a5fa4-105">Description</span></span>
<span data-ttu-id="a5fa4-106">Hitta RoleCapability cmdleten hittar PowerShell rollen funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-106">The Find-RoleCapability cmdlet finds PowerShell role capabilities in modules.</span></span> <span data-ttu-id="a5fa4-107">Hitta RoleCapability söker moduler i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-107">Find-RoleCapability searches modules in registered repositories.</span></span> <span data-ttu-id="a5fa4-108">För varje roll-funktion som söker efter denna cmdlet returnerar den ett PSGetRoleCapabilityInfo-objekt.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-108">For each role capability that this cmdlet finds, it returns a PSGetRoleCapabilityInfo object.</span></span> <span data-ttu-id="a5fa4-109">Du kan överföra ett PSGetRoleCapabilityInfo-objekt till cmdleten Install-Module så här installerar du den modul som innehåller den roll kapaciteten.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-109">You can pass a PSGetRoleCapabilityInfo object to the Install-Module cmdlet to install the module that contains the role capability.</span></span>
<span data-ttu-id="a5fa4-110">PowerShell rollen funktioner definierar vilka kommandon, program och så vidare är tillgängliga för en användare i en precis tillräckligt Administration JEA ()-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-110">PowerShell role capabilities define which commands, applications, and so on are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="a5fa4-111">Rollen funktioner definieras av filer med filnamnstillägget .psrc.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-111">Role capabilities are defined by files with a .psrc extension.</span></span>

- <span data-ttu-id="a5fa4-112">Hitta RoleCapability kan filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-112">Find-RoleCapability can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="a5fa4-113">Dessa parametrar kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-113">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="a5fa4-114">De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-114">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="a5fa4-115">Om parametern RequiredVersion inte anges returnerar hitta RoleCapability den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-115">If the RequiredVersion parameter is not specified, Find-RoleCapability returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="a5fa4-116">Om parametern RequiredVersion har angetts returnerar hitta RoleCapability endast versionen av den modul som exakt matchar den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-116">If the RequiredVersion parameter is specified, Find-RoleCapability only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="a5fa4-117">Hitta RoleCapability kan filtrera efter modulens med parametern - tagg</span><span class="sxs-lookup"><span data-stu-id="a5fa4-117">Find-RoleCapability can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="a5fa4-118">Hitta RoleCapability kan filtrera på databas-specifika sökspråk med parametern - Filter.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-118">Find-RoleCapability can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="a5fa4-119">Hitta RoleCapability kan filtrera efter moduler från alla eller fåtal registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-119">Find-RoleCapability can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="a5fa4-120">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="a5fa4-120">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="a5fa4-121">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="a5fa4-121">Cmdlet online help reference</span></span>

[<span data-ttu-id="a5fa4-122">Hitta RoleCapability</span><span class="sxs-lookup"><span data-stu-id="a5fa4-122">Find-RoleCapability</span></span>](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a><span data-ttu-id="a5fa4-123">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="a5fa4-123">Example commands</span></span>
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

