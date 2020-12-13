---
ms.date: 09/13/2016
ms.topic: reference
title: Lägga till filterparametrar
description: Lägga till filterparametrar
ms.openlocfilehash: 419ffea2afb4aa534a3e19ecdfce6d6af1da46a6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648532"
---
# <a name="input-filter-parameters"></a><span data-ttu-id="27f75-103">Lägga till filterparametrar</span><span class="sxs-lookup"><span data-stu-id="27f75-103">Input Filter Parameters</span></span>

<span data-ttu-id="27f75-104">En cmdlet kan definiera `Filter` , `Include` , och `Exclude` parametrar som filtrerar uppsättningen med inobjekt som cmdleten påverkar.</span><span class="sxs-lookup"><span data-stu-id="27f75-104">A cmdlet can define `Filter`, `Include`, and `Exclude` parameters that filter the set of input objects that the cmdlet affects.</span></span>

<span data-ttu-id="27f75-105">Normalt anges insamlings objekt av en `InputObject` , `Path` -eller- `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="27f75-105">Typically, the set of input objects is specified by an `InputObject`, `Path`, or `Name` parameter.</span></span> <span data-ttu-id="27f75-106">En cmdlet kan till exempel ha en `Path` parameter som accepterar flera sökvägar med hjälp av jokertecken och varje sökväg pekar på ett inobjekt.</span><span class="sxs-lookup"><span data-stu-id="27f75-106">For example, a cmdlet can have a `Path` parameter that accepts multiple paths by using wildcard characters, and each path points to an input object.</span></span> <span data-ttu-id="27f75-107">Används tillsammans, `Filter` parametrarna, `Include` och för `Exclude` att ytterligare kvalificera Sök vägarna som cmdleten fungerar vid varje gång den anropas.</span><span class="sxs-lookup"><span data-stu-id="27f75-107">Used together, the `Filter`, `Include`, and `Exclude` parameters further qualify the paths the cmdlet works on each time it is invoked.</span></span>

## <a name="include-and-exclude-parameters"></a><span data-ttu-id="27f75-108">Inkludera och exkludera parametrar</span><span class="sxs-lookup"><span data-stu-id="27f75-108">Include and Exclude Parameters</span></span>

<span data-ttu-id="27f75-109">`Include`Parametrarna och `Exclude` identifierar de objekt som ingår i eller undantas från den uppsättning indataportar som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="27f75-109">The `Include` and `Exclude` parameters identify the objects that are included or excluded from the set of input objects passed to the cmdlet.</span></span> <span data-ttu-id="27f75-110">Använd de här parametrarna när filtret kan uttryckas i standard språket jokertecken.</span><span class="sxs-lookup"><span data-stu-id="27f75-110">Use these parameters when the filter can be expressed in the standard wildcard language.</span></span> <span data-ttu-id="27f75-111">(Mer information om jokertecken finns i [stödjande jokertecken i cmdlet-parametrar](./supporting-wildcard-characters-in-cmdlet-parameters.md).) `Include` Parametern innehåller alla objekt vars namn matchar inkluderings filtret.</span><span class="sxs-lookup"><span data-stu-id="27f75-111">(For more information about wildcard characters, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).) The `Include` parameter includes all the objects whose names match the inclusion filter.</span></span> <span data-ttu-id="27f75-112">`Exclude`Parametern utesluter alla objekt vars namn matchar filtret.</span><span class="sxs-lookup"><span data-stu-id="27f75-112">The `Exclude` parameter excludes all the objects whose names match the filter.</span></span>

## <a name="filter-parameter"></a><span data-ttu-id="27f75-113">Filter parameter</span><span class="sxs-lookup"><span data-stu-id="27f75-113">Filter Parameter</span></span>

<span data-ttu-id="27f75-114">`Filter`Parametern anger ett filter som inte uttrycks i standard språket jokertecken.</span><span class="sxs-lookup"><span data-stu-id="27f75-114">The `Filter` parameter specifies a filter that is not expressed in the standard wildcard language.</span></span> <span data-ttu-id="27f75-115">Till exempel kan Active Directory Service Interfaces (ADSI) eller SQL-filter skickas till cmdleten via dess `Filter` parameter.</span><span class="sxs-lookup"><span data-stu-id="27f75-115">For example, Active Directory Service Interfaces (ADSI) or SQL filters might be passed to the cmdlet through its `Filter` parameter.</span></span> <span data-ttu-id="27f75-116">I de cmdlets som tillhandahålls av Windows PowerShell anges dessa filter av de Windows PowerShell-leverantörer som använder cmdleten för att få åtkomst till ett data lager.</span><span class="sxs-lookup"><span data-stu-id="27f75-116">In the cmdlets provided by Windows PowerShell, these filters are specified by the Windows PowerShell providers that use the cmdlet to access a data store.</span></span> <span data-ttu-id="27f75-117">Varje provider definierar vanligt vis sitt eget filter.</span><span class="sxs-lookup"><span data-stu-id="27f75-117">Each provider typically defines its own filter.</span></span>

## <a name="filtering-if-no-set-of-input-objects-is-specified"></a><span data-ttu-id="27f75-118">Filtrera om ingen uppsättning med inmatade objekt har angetts</span><span class="sxs-lookup"><span data-stu-id="27f75-118">Filtering If No Set of Input Objects Is Specified</span></span>

<span data-ttu-id="27f75-119">Om ingen uppsättning med inobjekt har angetts innebär det vanligt vis att filtrera mot alla objekt.</span><span class="sxs-lookup"><span data-stu-id="27f75-119">If no set of input objects is specified, this typically means to filter against all objects.</span></span> <span data-ttu-id="27f75-120">Mer information finns i[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span><span class="sxs-lookup"><span data-stu-id="27f75-120">For more information, see[Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process).</span></span>

## <a name="see-also"></a><span data-ttu-id="27f75-121">Se även</span><span class="sxs-lookup"><span data-stu-id="27f75-121">See Also</span></span>

[<span data-ttu-id="27f75-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="27f75-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
