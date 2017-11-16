---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a><span data-ttu-id="1f82f-102">Klass-baserade DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="1f82f-102">Class-based DSC Resources</span></span>

## <a name="defining-dsc-resources-with-classes"></a><span data-ttu-id="1f82f-103">Definiera DSC-resurser med klasser</span><span class="sxs-lookup"><span data-stu-id="1f82f-103">Defining DSC resources with classes</span></span>

<span data-ttu-id="1f82f-104">Utifrån feedback har vi gjort redigering DSC klass-baserade resurser enklare och lättare att förstå.</span><span class="sxs-lookup"><span data-stu-id="1f82f-104">Based on feedback, we’ve made authoring class-based DSC resources simpler and easier to understand.</span></span> <span data-ttu-id="1f82f-105">De viktiga skillnaderna mellan en klass-baserade DSC-resurs och en cmdlet DSC-resursprovidern är:</span><span class="sxs-lookup"><span data-stu-id="1f82f-105">The major differences between a class-based DSC resource and a cmdlet DSC resource provider are:</span></span>

* <span data-ttu-id="1f82f-106">Det krävs inte en MOF-fil för schemat.</span><span class="sxs-lookup"><span data-stu-id="1f82f-106">A MOF file for the schema is not required.</span></span>
* <span data-ttu-id="1f82f-107">En **DSCResource** undermapp i mappen modul krävs inte.</span><span class="sxs-lookup"><span data-stu-id="1f82f-107">A **DSCResource** subfolder in the module folder is not required.</span></span>
* <span data-ttu-id="1f82f-108">En PowerShell-modulen fil kan innehålla flera klasser i DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="1f82f-108">A PowerShell module file can contain multiple DSC resource classes.</span></span>

<span data-ttu-id="1f82f-109">Mer information finns i [skriva en anpassad DSC-resurs med PowerShell klasser](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span><span class="sxs-lookup"><span data-stu-id="1f82f-109">For more information, see [Writing a custom DSC resource with PowerShell classes](https://msdn.microsoft.com/powershell/dsc/authoringresource).</span></span>

