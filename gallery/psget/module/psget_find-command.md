---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Kommandot Sök
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a><span data-ttu-id="3bdfd-103">Kommandot Sök</span><span class="sxs-lookup"><span data-stu-id="3bdfd-103">Find-Command</span></span>

<span data-ttu-id="3bdfd-104">Söker efter PowerShell-kommandon i moduler.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-104">Finds PowerShell commands in modules.</span></span>

## <a name="description"></a><span data-ttu-id="3bdfd-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3bdfd-105">Description</span></span>
<span data-ttu-id="3bdfd-106">Kommandot Sök cmdleten hittar PowerShell-kommandon, till exempel-cmdlet: ar, alias, funktioner och arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-106">The Find-Command cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="3bdfd-107">Kommandot Sök söker moduler i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-107">Find-Command searches modules in registered repositories.</span></span>
<span data-ttu-id="3bdfd-108">För varje kommando som den här cmdleten söker efter, returneras ett PSGetCommandInfo-objekt.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-108">For each command that this cmdlet finds, it returns a PSGetCommandInfo object.</span></span> <span data-ttu-id="3bdfd-109">Du kan överföra ett PSGetCommandInfo-objekt till cmdleten Install-Module så här installerar du den modul som innehåller kommandot.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-109">You can pass a PSGetCommandInfo object to the Install-Module cmdlet to install the module that contains the command.</span></span>

- <span data-ttu-id="3bdfd-110">Sök-kommandot kan du filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-110">Find-Command can filter with version parameters: MinimumVersion, RequiredVersion, AllVersions.</span></span>
  - <span data-ttu-id="3bdfd-111">Dessa parametrar kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-111">These parameters are mutually exclusive.</span></span>
  - <span data-ttu-id="3bdfd-112">De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-112">These version parameters are allowed only with the single module name without any wildcards.</span></span>
  - <span data-ttu-id="3bdfd-113">Om parametern RequiredVersion inte anges returnerar kommandot Sök den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-113">If the RequiredVersion parameter is not specified, Find-Command returns the latest version of the module that is equal to or greater than the minimum version specified or the latest version of the module if no minimum version is specified.</span></span>
  - <span data-ttu-id="3bdfd-114">Om parametern RequiredVersion har angetts returnerar kommandot Sök endast versionen av den modul som exakt matchar den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-114">If the RequiredVersion parameter is specified, Find-Command only returns the version of the module that exactly matches the specified version.</span></span>
- <span data-ttu-id="3bdfd-115">Sök-kommandot kan du filtrera på modulen metadata med parametern - tagg</span><span class="sxs-lookup"><span data-stu-id="3bdfd-115">Find-Command can filter on module metadata with the -Tag parameter</span></span>
- <span data-ttu-id="3bdfd-116">Sök-kommandot kan du filtrera på databas-specifika sökspråk med parametern - Filter.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-116">Find-Command can filter on repository-specific search language with the -Filter parameter.</span></span>
- <span data-ttu-id="3bdfd-117">Sök-kommandot kan du filtrera på moduler från alla eller fåtal registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="3bdfd-117">Find-Command can filter on modules from all or few of the registered repositories.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="3bdfd-118">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="3bdfd-118">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="3bdfd-119">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="3bdfd-119">Cmdlet online help reference</span></span>

[<span data-ttu-id="3bdfd-120">Kommandot Sök</span><span class="sxs-lookup"><span data-stu-id="3bdfd-120">Find-Command</span></span>](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a><span data-ttu-id="3bdfd-121">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="3bdfd-121">Example commands</span></span>
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```