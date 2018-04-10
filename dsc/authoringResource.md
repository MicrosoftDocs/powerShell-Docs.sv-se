---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skapa anpassade Windows PowerShell Desired State Configuration-resurser
ms.openlocfilehash: 7da4741a773d40da75c6ef667c35f86e1bae74bf
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="b562d-103">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="b562d-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="b562d-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b562d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b562d-105">Windows PowerShell önskad tillstånd Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="b562d-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="b562d-106">(Mer information finns i [inbyggda Windows PowerShell önskad tillstånd Configuration resurser](builtInResource.md).) Det här avsnittet innehåller en översikt över hur du utvecklar resurserna och länkarna till avsnitt med specifik information och exempel.</span><span class="sxs-lookup"><span data-stu-id="b562d-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="b562d-107">Komponenter för DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="b562d-107">DSC resource components</span></span>

<span data-ttu-id="b562d-108">En DSC-resurs är en Windows PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="b562d-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="b562d-109">Modulen innehåller både schema (definition av konfigurerbara egenskaper) och implementering (den kod som utför det faktiska arbetet som anges av en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="b562d-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="b562d-110">Ett schema för DSC-resursen kan definieras i en MOF-fil och implementeringen utförs av en skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="b562d-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="b562d-111">Från och med stöd för PowerShell klasser i version 5, kan schemat och implementering både definieras i en klass.</span><span class="sxs-lookup"><span data-stu-id="b562d-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="b562d-112">I följande avsnitt beskrivs i detalj hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="b562d-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="b562d-113">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="b562d-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="b562d-114">Implementera en DSC-resurs i C#</span><span class="sxs-lookup"><span data-stu-id="b562d-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="b562d-115">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="b562d-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="b562d-116">Sammansatta resurser: med hjälp av DSC-konfigurationen som en resurs</span><span class="sxs-lookup"><span data-stu-id="b562d-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="b562d-117">Med hjälp av verktyget resurs Designer</span><span class="sxs-lookup"><span data-stu-id="b562d-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)