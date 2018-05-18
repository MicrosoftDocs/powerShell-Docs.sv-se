---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="dd765-102">Klassbaserade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="dd765-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="dd765-103">Definiera DSC-resurser med klasser</span><span class="sxs-lookup"><span data-stu-id="dd765-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="dd765-104">Utifrån feedback har vi gjort redigering DSC klass-baserade resurser enklare och lättare att förstå.</span><span class="sxs-lookup"><span data-stu-id="dd765-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span>
<span data-ttu-id="dd765-105">De viktiga skillnaderna mellan en klass-baserade DSC-resurs och en cmdlet DSC-resursprovidern är:</span><span class="sxs-lookup"><span data-stu-id="dd765-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="dd765-106">Det krävs inte en MOF-fil för schemat.</span><span class="sxs-lookup"><span data-stu-id="dd765-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="dd765-107">En **DSCResource** undermapp i mappen modul krävs inte.</span><span class="sxs-lookup"><span data-stu-id="dd765-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="dd765-108">En PowerShell-modulen fil kan innehålla flera klasser i DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="dd765-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="dd765-109">Mer information finns i [skriva en anpassad DSC-resurs med PowerShell klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="dd765-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>
