---
ms.date: 07/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
description: Den här artikeln innehåller en översikt över hur du utvecklar resurser och länkar till artiklar med detaljerad information och exempel.
ms.openlocfilehash: ff9a0c8ae10583155217fbeccc62e6e1c94f9a11
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656410"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="9bc92-104">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bc92-104">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="9bc92-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="9bc92-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="9bc92-106">Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="9bc92-106">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="9bc92-107">Den här artikeln innehåller en översikt över hur du utvecklar resurser och länkar till artiklar med detaljerad information och exempel.</span><span class="sxs-lookup"><span data-stu-id="9bc92-107">This article provides an overview of developing resources and links to articles with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="9bc92-108">DSC-resurs komponenter</span><span class="sxs-lookup"><span data-stu-id="9bc92-108">DSC resource components</span></span>

<span data-ttu-id="9bc92-109">En DSC-resurs är en Windows PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="9bc92-109">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="9bc92-110">Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="9bc92-110">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="9bc92-111">Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="9bc92-111">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="9bc92-112">Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass.</span><span class="sxs-lookup"><span data-stu-id="9bc92-112">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="9bc92-113">I följande artiklar beskrivs mer information om hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="9bc92-113">The following articles describe in more detail how to create DSC resources.</span></span>

- [<span data-ttu-id="9bc92-114">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="9bc92-114">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
- [<span data-ttu-id="9bc92-115">Implementera en DSC-resurs i C #</span><span class="sxs-lookup"><span data-stu-id="9bc92-115">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
- [<span data-ttu-id="9bc92-116">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="9bc92-116">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="9bc92-117">Sammansatta resurser: använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="9bc92-117">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
- [<span data-ttu-id="9bc92-118">Använda Resource designer-verktyget</span><span class="sxs-lookup"><span data-stu-id="9bc92-118">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
