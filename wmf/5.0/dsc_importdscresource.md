---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: ce5afc2f90f78433b64bf5b41946fc7506c43504
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219658"
---
# <a name="import-dscresource-keyword-supports--moduleversion-parameter"></a><span data-ttu-id="e143a-102">Importera DscResource nyckelordet stöder ModuleVersion - parameter</span><span class="sxs-lookup"><span data-stu-id="e143a-102">Import-DscResource keyword supports -ModuleVersion parameter</span></span>

<span data-ttu-id="e143a-103">Vi har lagt till en ny parameter till den `Import-DscResource` dynamiska nyckelord som är tillgänglig vid redigering av DSC-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="e143a-103">We have added a new parameter to the `Import-DscResource` dynamic keyword available when authoring DSC configurations.</span></span> <span data-ttu-id="e143a-104">Konfiguration av författarna kan nu ange exakt vilka Modulversion för att läsa in DSC-resurser från.</span><span class="sxs-lookup"><span data-stu-id="e143a-104">Configuration authors can now specify exactly which module version to load the DSC resources from.</span></span> <span data-ttu-id="e143a-105">Den nya syntaxen för nyckelordet är:</span><span class="sxs-lookup"><span data-stu-id="e143a-105">The new syntax of the keyword is:</span></span>

```powershell
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName(s)>] [-ModuleVersion <ModuleVersion>]
```

* <span data-ttu-id="e143a-106">**Namnet**: namnen på en eller flera resurser för att importera.</span><span class="sxs-lookup"><span data-stu-id="e143a-106">**Name**: Names of one or more resources to import.</span></span>
* <span data-ttu-id="e143a-107">**Modulnamn**: Modulnamnen eller ModuleSpecification objekt av en eller flera moduler att importera.</span><span class="sxs-lookup"><span data-stu-id="e143a-107">**ModuleName**: Module names or ModuleSpecification objects of one or more modules to import.</span></span>
* <span data-ttu-id="e143a-108">**ModuleVersion**: versionen för modulen av import.</span><span class="sxs-lookup"><span data-stu-id="e143a-108">**ModuleVersion**: Version of module ot import.</span></span> <span data-ttu-id="e143a-109">Om används, måste Modulnamn representera bara en modul med namnet.</span><span class="sxs-lookup"><span data-stu-id="e143a-109">If used, ModuleName must represent only one module by name.</span></span>

<span data-ttu-id="e143a-110">I Windows PowerShell ISE visas den med IntelliSense:</span><span class="sxs-lookup"><span data-stu-id="e143a-110">In the Windows PowerShell ISE, it shows up with IntelliSense:</span></span>

![](../images/Import-DscResource-Modversion.jpg)

<span data-ttu-id="e143a-111">**Obs**: den `–ModuleVersion` parametern kan bara användas i kombination med den `–ModuleName` parameter.</span><span class="sxs-lookup"><span data-stu-id="e143a-111">**Note**: the `–ModuleVersion` parameter can only be used in combination with the `–ModuleName` parameter.</span></span> <span data-ttu-id="e143a-112">Den kan inte användas med resursnamn endast med den `–Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="e143a-112">It cannot be used with resource names using only the `–Name` parameter.</span></span>

<span data-ttu-id="e143a-113">Innan var det enda sättet att ange modulversionen vid inläsning av DSC-resurser med hjälp av specifikationen Modulobjekt t.ex.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span><span class="sxs-lookup"><span data-stu-id="e143a-113">Before this, the only way to specify the module version when loading DSC resources was by using the Module specification object e.g.: `–ModuleName @{ModuleName="UserConfigProvider";ModuleVersion="3.0"}`</span></span>
