---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_items_tab
ms.openlocfilehash: 8704091542de5c19817ab0b4f77fd98987084b5d
ms.sourcegitcommit: 1a0a0928c1e3cae4e8df8d79b0737bd7ed6b4e47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/21/2017
---
# <a name="items-tab"></a><span data-ttu-id="8b922-103">Fliken objekt</span><span class="sxs-lookup"><span data-stu-id="8b922-103">Items Tab</span></span>

<span data-ttu-id="8b922-104">Den [fliken poster](https://www.powershellgallery.com/items) visar alla tillgängliga objekt i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8b922-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="8b922-105">Det finns flera sätt att filtrera, sortera och söka efter objekt.</span><span class="sxs-lookup"><span data-stu-id="8b922-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="8b922-106">Om du vill ha mer information om ett visst objekt, klickar du på objektet.</span><span class="sxs-lookup"><span data-stu-id="8b922-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="8b922-107">Filtrera efter</span><span class="sxs-lookup"><span data-stu-id="8b922-107">Filter By</span></span>

<span data-ttu-id="8b922-108">I listrutan under ”filtrera efter” tillåter användare att filtrera resultaten genom att:</span><span class="sxs-lookup"><span data-stu-id="8b922-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
* <span data-ttu-id="8b922-109">Inkludera förhandsversion</span><span class="sxs-lookup"><span data-stu-id="8b922-109">Include Prerelease</span></span>
* <span data-ttu-id="8b922-110">Stabil endast</span><span class="sxs-lookup"><span data-stu-id="8b922-110">Stable Only</span></span>

<span data-ttu-id="8b922-111">Information om ”förhandsversion” och ”stabil” finns [förhandsversion versionshantering lagts till PowerShellGet och PowerShell-galleriet](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.</span><span class="sxs-lookup"><span data-stu-id="8b922-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="8b922-112">Kryssrutorna under listrutan Tillåt användare att filtrera resultaten genom att:</span><span class="sxs-lookup"><span data-stu-id="8b922-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
* <span data-ttu-id="8b922-113">Typer av objekt</span><span class="sxs-lookup"><span data-stu-id="8b922-113">Item Types</span></span>
  - <span data-ttu-id="8b922-114">Modul</span><span class="sxs-lookup"><span data-stu-id="8b922-114">Module</span></span>
  - <span data-ttu-id="8b922-115">Skript</span><span class="sxs-lookup"><span data-stu-id="8b922-115">Script</span></span>
* <span data-ttu-id="8b922-116">Kategorier</span><span class="sxs-lookup"><span data-stu-id="8b922-116">Categories</span></span>
  - <span data-ttu-id="8b922-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b922-117">Cmdlet</span></span>
  - <span data-ttu-id="8b922-118">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="8b922-118">DSC Resource</span></span>
  - <span data-ttu-id="8b922-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="8b922-119">Function</span></span>
  - <span data-ttu-id="8b922-120">Kapaciteten för rollen</span><span class="sxs-lookup"><span data-stu-id="8b922-120">Role Capability</span></span>
  - <span data-ttu-id="8b922-121">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="8b922-121">Workflow</span></span>

<span data-ttu-id="8b922-122">Kontrollera modul i vilka typer av objekt om du vill visa endast moduler i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8b922-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="8b922-123">På samma sätt för att se endast skript i PowerShell-galleriet, kontrollera skriptet i vilka typer av objekt.</span><span class="sxs-lookup"><span data-stu-id="8b922-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="8b922-124">Filter är inklusiva.</span><span class="sxs-lookup"><span data-stu-id="8b922-124">Filters are inclusive.</span></span>
> <span data-ttu-id="8b922-125">Exempel: Ett objekt som innehåller både cmdletar och funktioner visas om antingen Cmdlet eller funktionen (eller båda) är markerade.</span><span class="sxs-lookup"><span data-stu-id="8b922-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="8b922-126">Om ingen väljs visas inte objektet.</span><span class="sxs-lookup"><span data-stu-id="8b922-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="8b922-127">Om alla kategorier har valts visas och endast objekt som innehåller en av dessa kategorier.</span><span class="sxs-lookup"><span data-stu-id="8b922-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="8b922-128">**Objekt som inte tillhör någon av dessa kategorier visas inte.**</span><span class="sxs-lookup"><span data-stu-id="8b922-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="8b922-129">Sortera efter</span><span class="sxs-lookup"><span data-stu-id="8b922-129">Sort By</span></span>

<span data-ttu-id="8b922-130">Sortera efter listrutan tillåter användare att sortera resultaten efter:</span><span class="sxs-lookup"><span data-stu-id="8b922-130">The Sort By drop-down allows users to sort the results by:</span></span>
* <span data-ttu-id="8b922-131">Popularitet - popularitet bestäms genom att hämta antalet</span><span class="sxs-lookup"><span data-stu-id="8b922-131">Popularity - Popularity is determined by Download Count</span></span>
* <span data-ttu-id="8b922-132">A-Z - alfabetiskt efter namn</span><span class="sxs-lookup"><span data-stu-id="8b922-132">A-Z - Alphabetically by item name</span></span>
* <span data-ttu-id="8b922-133">Senaste - objekt som visas i den ordning de publicera datum</span><span class="sxs-lookup"><span data-stu-id="8b922-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="8b922-134">Sökrutan</span><span class="sxs-lookup"><span data-stu-id="8b922-134">Search Box</span></span>

<span data-ttu-id="8b922-135">Sökrutan tillåter användare att söka efter objekt på nyckelord.</span><span class="sxs-lookup"><span data-stu-id="8b922-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="8b922-136">Mer information finns i [galleriet Söksyntax](psgallery_search_syntax.md).</span><span class="sxs-lookup"><span data-stu-id="8b922-136">For more information, see [Gallery Search Syntax](psgallery_search_syntax.md).</span></span>
