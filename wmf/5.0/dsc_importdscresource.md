---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 46a278b83edb9d8e3d75b0874603710d416be3b5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085754"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="94790-102">Import-DscResource nyckelordet stöder - ModuleVersion-parametern</span><span class="sxs-lookup"><span data-stu-id="94790-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="94790-103">Vi har lagt till en ny parameter till den `Import-DscResource` dynamiska nyckelord som är tillgängliga vid redigering av DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="94790-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="94790-104">Konfiguration av författarna kan nu ange exakt vilka Modulversion för att läsa in DSC-resurser från.</span><span class="sxs-lookup"><span data-stu-id="94790-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="94790-105">Den nya syntaxen för nyckelordet är:</span><span class="sxs-lookup"><span data-stu-id="94790-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="94790-106">**Namn på**: Namn på en eller flera resurser som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="94790-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="94790-107">**ModuleName**: Modulnamnen eller ModuleSpecification objekt i en eller flera moduler att importera.</span><span class="sxs-lookup"><span data-stu-id="94790-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="94790-108">**ModuleVersion**: Version av modulen att importera.</span><span class="sxs-lookup"><span data-stu-id="94790-108">**ModuleVersion**: Version of module to import.</span></span> <span data-ttu-id="94790-109">Om används, måste ModuleName representera bara en modul med namnet.</span><span class="sxs-lookup"><span data-stu-id="94790-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="94790-110">I Windows PowerShell ISE visas så den med IntelliSense-stöd:</span><span class="sxs-lookup"><span data-stu-id="94790-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="94790-111">**Obs**: den `–ModuleVersion` parametern kan bara användas i kombination med den `–ModuleName` parametern.</span><span class="sxs-lookup"><span data-stu-id="94790-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="94790-112">Den kan inte användas med resursnamn endast med den `–Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="94790-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="94790-113">Tidigare var det enda sättet att ange modulversionen vid inläsning av DSC-resurser med hjälp av modulen specifikationen objektet t.ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="94790-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
