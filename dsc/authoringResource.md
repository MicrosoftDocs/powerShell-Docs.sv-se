---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skapa anpassade Windows PowerShell Desired State Configuration-resurser
ms.openlocfilehash: 4751bcaab1996ee3164bd2a2f430c3b188712860
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="abd51-103">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="abd51-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="abd51-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="abd51-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="abd51-105">Windows PowerShell önskad tillstånd Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="abd51-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="abd51-106">(Mer information finns i [inbyggda Windows PowerShell önskad tillstånd Configuration resurser](builtInResource.md).) Det här avsnittet innehåller en översikt över hur du utvecklar resurserna och länkarna till avsnitt med specifik information och exempel.</span><span class="sxs-lookup"><span data-stu-id="abd51-106">(For more information, see [Built-In Windows PowerShell Desired State Configuration Resources](builtInResource.md).) This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="abd51-107">Komponenter för DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="abd51-107">DSC resource components</span></span>

<span data-ttu-id="abd51-108">En DSC-resurs är en Windows PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="abd51-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="abd51-109">Modulen innehåller både schema (definition av konfigurerbara egenskaper) och implementering (den kod som utför det faktiska arbetet som anges av en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="abd51-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="abd51-110">Ett schema för DSC-resursen kan definieras i en MOF-fil och implementeringen utförs av en skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="abd51-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="abd51-111">Från och med stöd för PowerShell klasser i version 5, kan schemat och implementering både definieras i en klass.</span><span class="sxs-lookup"><span data-stu-id="abd51-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="abd51-112">I följande avsnitt beskrivs i detalj hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="abd51-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="abd51-113">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="abd51-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="abd51-114">Implementera en DSC-resurs i C#</span><span class="sxs-lookup"><span data-stu-id="abd51-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="abd51-115">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="abd51-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="abd51-116">Sammansatta resurser: med hjälp av DSC-konfigurationen som en resurs</span><span class="sxs-lookup"><span data-stu-id="abd51-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="abd51-117">Med hjälp av verktyget resurs Designer</span><span class="sxs-lookup"><span data-stu-id="abd51-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)

