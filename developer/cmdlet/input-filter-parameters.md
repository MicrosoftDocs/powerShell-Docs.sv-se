---
title: Ange filterparametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e45929d1-bbb4-4dc6-892f-f9eacdb1c84c
caps.latest.revision: 8
ms.openlocfilehash: 553878c34e74129f9876cca25a5393cb0d53445a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067696"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="06a94-102">Lägga till filterparametrar</span><span class="sxs-lookup"><span data-stu-id="06a94-102">Input Filter Parameters</span></span>

<span data-ttu-id="06a94-103">En cmdlet kan definiera `Filter`, `Include`, och `Exclude` parametrar som filtrera en uppsättning inkommande objekt som påverkas av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="06a94-103">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="06a94-104">Normalt en uppsättning inkommande objekt anges av en `InputObject`, `Path`, eller `Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="06a94-104">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="06a94-105">En cmdlet kan till exempel ha en `Path` parameter som accepterar flera sökvägar genom att använda jokertecken och varje sökväg pekar på ett inkommande objekt.</span><span class="sxs-lookup"><span data-stu-id="06a94-105">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="06a94-106">Används tillsammans, den `Filter`, `Include`, och `Exclude` ytterligare parametrar kvalificera sökvägarna cmdlet fungerar på varje gång den anropas.</span><span class="sxs-lookup"><span data-stu-id="06a94-106">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="06a94-107">Inkludera och exkludera parametrar</span><span class="sxs-lookup"><span data-stu-id="06a94-107">Include and Exclude Parameters</span></span>

<span data-ttu-id="06a94-108">Den `Include` och `Exclude` parametrar definieras objekt som inkluderas eller uteslutas från uppsättningen med inkommande objekt som överförs till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="06a94-108">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="06a94-109">Använd dessa parametrar när filtret kan uttryckas på språket som standard med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="06a94-109">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="06a94-110">(Läs mer om jokertecken [stöd för jokertecken i Cmdlet-parametrarna](./supporting-wildcard-characters-in-cmdlet-parameters.md).) Den `Include` parametern innehåller de objekt vars namn matchar filtret inkludering.</span><span class="sxs-lookup"><span data-stu-id="06a94-110">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="06a94-111">Den `Exclude` parametern omfattar inte de objekt vars namn matchar filtret.</span><span class="sxs-lookup"><span data-stu-id="06a94-111">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="06a94-112">Filter-parametern</span><span class="sxs-lookup"><span data-stu-id="06a94-112">Filter Parameter</span></span>

<span data-ttu-id="06a94-113">Den `Filter` parametern anger ett filter som inte uttrycks på språket som standard med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="06a94-113">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="06a94-114">Till exempel tjänsten gränssnitt ADSI (Active Directory) eller SQL-filter kan skickas till cmdleten via dess `Filter` parametern.</span><span class="sxs-lookup"><span data-stu-id="06a94-114">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="06a94-115">I dessa cmdlets som tillhandahålls av Windows PowerShell, anges filtren av Windows PowerShell-providrarna som använder cmdlet: en för att få åtkomst till ett datalager.</span><span class="sxs-lookup"><span data-stu-id="06a94-115">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="06a94-116">Varje leverantör definierar vanligtvis sitt eget filter.</span><span class="sxs-lookup"><span data-stu-id="06a94-116">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="06a94-117">Filtrering om ingen uppsättning inkommande objekt har angetts</span><span class="sxs-lookup"><span data-stu-id="06a94-117">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="06a94-118">Om ingen uppsättning inkommande objekt anges innebär detta oftast att filtrera mot alla objekt.</span><span class="sxs-lookup"><span data-stu-id="06a94-118">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="06a94-119">Mer information finns i[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="06a94-119">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="06a94-120">Se även</span><span class="sxs-lookup"><span data-stu-id="06a94-120">See Also</span></span>

[<span data-ttu-id="06a94-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="06a94-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)