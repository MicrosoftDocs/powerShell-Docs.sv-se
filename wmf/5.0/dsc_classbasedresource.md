---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058122"
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="84ed6-102">Klassbaserade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="84ed6-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="84ed6-103">Definiera DSC-resurser med klasser</span><span class="sxs-lookup"><span data-stu-id="84ed6-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="84ed6-104">Baserat på feedback, har vi gjort redigera DSC MOF-baserade resurser blir lättare att förstå.</span><span class="sxs-lookup"><span data-stu-id="84ed6-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="84ed6-105">De större skillnaderna mellan en klassbaserade DSC-resurs och en cmdlet DSC-resursprovider är:</span><span class="sxs-lookup"><span data-stu-id="84ed6-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="84ed6-106">Det krävs inte en MOF-fil för schemat.</span><span class="sxs-lookup"><span data-stu-id="84ed6-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="84ed6-107">En **DSCResource** undermapp i modulmappen är inte obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="84ed6-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="84ed6-108">En PowerShell-filen för modulen kan innehålla flera DSC-resursklasser.</span><span class="sxs-lookup"><span data-stu-id="84ed6-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="84ed6-109">Mer information finns i [skriva en anpassad DSC-resurs med PowerShell-klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="84ed6-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
