---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057476"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a><span data-ttu-id="a5c20-102">PowerShell-Modulidentifiering, installera och inventering med PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a5c20-102">PowerShell Module Discovery, Install and Inventory with PowerShellGet</span></span>

<span data-ttu-id="a5c20-103">PowerShellGet ingår i den här versionen av WMF:</span><span class="sxs-lookup"><span data-stu-id="a5c20-103">PowerShellGet is included in this release of WMF:</span></span>
-   <span data-ttu-id="a5c20-104">Find-Module kan filtrera på modulen metadata med parametern - tagg</span><span class="sxs-lookup"><span data-stu-id="a5c20-104">Find-Module can filter on module metadata with the -Tag parameter</span></span>
-   <span data-ttu-id="a5c20-105">Find-Module kan filtrera på lagringsplatsen sökningar språk med parametern - Filter</span><span class="sxs-lookup"><span data-stu-id="a5c20-105">Find-Module can filter on repository-specific search language with the -Filter parameter</span></span>
-   <span data-ttu-id="a5c20-106">Find-Module kan filter baserat på modulen innehåll med - kommando, - DscResource, och - innehåller parametrar</span><span class="sxs-lookup"><span data-stu-id="a5c20-106">Find-Module can filter based on module contents with the -Command, -DscResource, and -Includes parameters</span></span>
-   <span data-ttu-id="a5c20-107">Sök-DscResource tillåter identifiering av enskilda DSC-resurser i databaser</span><span class="sxs-lookup"><span data-stu-id="a5c20-107">Find-DscResource allows discovery of individual DSC resources in repositories</span></span>
-   <span data-ttu-id="a5c20-108">Stöd för att installera från och publicering till filresurser med NuGet</span><span class="sxs-lookup"><span data-stu-id="a5c20-108">Support for installing from and publishing to file shares with NuGet</span></span>

## <a name="example-commands"></a><span data-ttu-id="a5c20-109">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="a5c20-109">Example commands</span></span>
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a><span data-ttu-id="a5c20-110">Nya funktioner i PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a5c20-110">New features in PowerShellGet</span></span>
-   <span data-ttu-id="a5c20-111">Stöd för sida-vid-sida-version på Windows PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="a5c20-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
-   <span data-ttu-id="a5c20-112">Stöd för policymodul beroende installation</span><span class="sxs-lookup"><span data-stu-id="a5c20-112">Module dependency installation support</span></span>
-   <span data-ttu-id="a5c20-113">Tre nya cmdletar</span><span class="sxs-lookup"><span data-stu-id="a5c20-113">Three new cmdlets</span></span>
    -   <span data-ttu-id="a5c20-114">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a5c20-114">Get-InstalledModule</span></span>
    -   <span data-ttu-id="a5c20-115">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="a5c20-115">Uninstall-Module</span></span>
    -   <span data-ttu-id="a5c20-116">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a5c20-116">Save-Module</span></span>
