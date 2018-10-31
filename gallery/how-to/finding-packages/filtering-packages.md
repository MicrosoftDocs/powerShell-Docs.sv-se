---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Filtrera sökresultaten
ms.openlocfilehash: 13270a310613a974e1588a9f56d443a936cfebb8
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004213"
---
# <a name="filtering-search-results"></a><span data-ttu-id="957e4-103">Filtrera sökresultaten</span><span class="sxs-lookup"><span data-stu-id="957e4-103">Filtering search results</span></span>

<span data-ttu-id="957e4-104">Den [paket fliken](https://www.powershellgallery.com/packages) visar alla tillgängliga paket i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="957e4-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="957e4-105">Det finns flera sätt att filtrera, sortera och söka paketen.</span><span class="sxs-lookup"><span data-stu-id="957e4-105">There are several ways to filter, sort, and search the packages.</span></span>
<span data-ttu-id="957e4-106">Om du vill se mer information om ett visst paket, klickar du på paketet.</span><span class="sxs-lookup"><span data-stu-id="957e4-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="957e4-107">Filtrera efter</span><span class="sxs-lookup"><span data-stu-id="957e4-107">Filter By</span></span>

<span data-ttu-id="957e4-108">I listrutan under ”filtrera efter” tillåter användare att filtrera resultatet efter:</span><span class="sxs-lookup"><span data-stu-id="957e4-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="957e4-109">Inkludera förhandsversion</span><span class="sxs-lookup"><span data-stu-id="957e4-109">Include Prerelease</span></span>
- <span data-ttu-id="957e4-110">Stabil endast</span><span class="sxs-lookup"><span data-stu-id="957e4-110">Stable Only</span></span>

<span data-ttu-id="957e4-111">Läs om hur ”förhandsversion” och ”stabil” [förhandsversion versionshantering som har lagts till i PowerShellGet och PowerShell-galleriet](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.</span><span class="sxs-lookup"><span data-stu-id="957e4-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="957e4-112">Kryssrutorna under listrutan kan du filtrera resultatet efter:</span><span class="sxs-lookup"><span data-stu-id="957e4-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="957e4-113">Pakettyper</span><span class="sxs-lookup"><span data-stu-id="957e4-113">Package Types</span></span>
  - <span data-ttu-id="957e4-114">Modul</span><span class="sxs-lookup"><span data-stu-id="957e4-114">Module</span></span>
  - <span data-ttu-id="957e4-115">Skript</span><span class="sxs-lookup"><span data-stu-id="957e4-115">Script</span></span>
- <span data-ttu-id="957e4-116">Kategorier</span><span class="sxs-lookup"><span data-stu-id="957e4-116">Categories</span></span>
  - <span data-ttu-id="957e4-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="957e4-117">Cmdlet</span></span>
  - <span data-ttu-id="957e4-118">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="957e4-118">DSC Resource</span></span>
  - <span data-ttu-id="957e4-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="957e4-119">Function</span></span>
  - <span data-ttu-id="957e4-120">Kapaciteten för rollen</span><span class="sxs-lookup"><span data-stu-id="957e4-120">Role Capability</span></span>
  - <span data-ttu-id="957e4-121">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="957e4-121">Workflow</span></span>

<span data-ttu-id="957e4-122">Kontrollera modul i den pakettyper endast moduler i PowerShell-galleriet visas.</span><span class="sxs-lookup"><span data-stu-id="957e4-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span>
<span data-ttu-id="957e4-123">På samma sätt för att visa endast skript i PowerShell-galleriet, kontrollera skriptet i den pakettyper.</span><span class="sxs-lookup"><span data-stu-id="957e4-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="957e4-124">Filter är inkluderande.</span><span class="sxs-lookup"><span data-stu-id="957e4-124">Filters are inclusive.</span></span>
> <span data-ttu-id="957e4-125">Exempel: Ett paket som innehåller både cmdletar och funktioner visas om antingen Cmdlet eller funktion (eller båda) är markerade.</span><span class="sxs-lookup"><span data-stu-id="957e4-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="957e4-126">Om ingen av dem har valts, visas inte paketet.</span><span class="sxs-lookup"><span data-stu-id="957e4-126">If neither are selected, the package will not appear.</span></span>
> <span data-ttu-id="957e4-127">Om alla kategorier har valts visas på samma sätt kan endast paket som innehåller en av dessa kategorier.</span><span class="sxs-lookup"><span data-stu-id="957e4-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span>
> <span data-ttu-id="957e4-128">**Paket som inte tillhör någon av dessa kategorier visas inte.**</span><span class="sxs-lookup"><span data-stu-id="957e4-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="957e4-129">Sortera efter</span><span class="sxs-lookup"><span data-stu-id="957e4-129">Sort By</span></span>

<span data-ttu-id="957e4-130">Sortera efter listrutan kan du sortera resultaten efter:</span><span class="sxs-lookup"><span data-stu-id="957e4-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="957e4-131">Popularitet - popularitet bestäms genom att hämta antal</span><span class="sxs-lookup"><span data-stu-id="957e4-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="957e4-132">A-Z - alfabetiskt efter paketnamn</span><span class="sxs-lookup"><span data-stu-id="957e4-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="957e4-133">Senaste - paket som visas i ordningen för publiceringsdatum</span><span class="sxs-lookup"><span data-stu-id="957e4-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="957e4-134">Sökrutan</span><span class="sxs-lookup"><span data-stu-id="957e4-134">Search Box</span></span>

<span data-ttu-id="957e4-135">Sökrutan tillåter användare att söka i paketen på nyckelord.</span><span class="sxs-lookup"><span data-stu-id="957e4-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="957e4-136">Mer information finns i [Gallerisökning](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="957e4-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
