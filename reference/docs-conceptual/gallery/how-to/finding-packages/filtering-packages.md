---
ms.date: 06/12/2017
title: Filtrera Sök Resultat
description: I den här artikeln beskrivs användar gränssnittet som används för att filtrera innehåll i PowerShell-galleriet.
ms.openlocfilehash: a769daae903e614b96be1056e3ff14eca41970bd
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389835"
---
# <a name="filtering-search-results"></a><span data-ttu-id="e6b9a-103">Filtrera Sök Resultat</span><span class="sxs-lookup"><span data-stu-id="e6b9a-103">Filtering search results</span></span>

<span data-ttu-id="e6b9a-104">[Fliken paket](https://www.powershellgallery.com/packages) visar alla tillgängliga paket i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="e6b9a-105">Det finns flera sätt att filtrera, sortera och söka i paketen.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-105">There are several ways to filter, sort, and search the packages.</span></span> <span data-ttu-id="e6b9a-106">Klicka på paketet om du vill se mer information om ett visst paket.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="e6b9a-107">Filtrera efter</span><span class="sxs-lookup"><span data-stu-id="e6b9a-107">Filter By</span></span>

<span data-ttu-id="e6b9a-108">Med list rutan filtrera efter kan användare filtrera resultaten genom att:</span><span class="sxs-lookup"><span data-stu-id="e6b9a-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>

- <span data-ttu-id="e6b9a-109">Inkludera för hands version</span><span class="sxs-lookup"><span data-stu-id="e6b9a-109">Include Prerelease</span></span>
- <span data-ttu-id="e6b9a-110">Endast stabilt</span><span class="sxs-lookup"><span data-stu-id="e6b9a-110">Stable Only</span></span>

<span data-ttu-id="e6b9a-111">Information om "för hands version" och "stabil" finns i [för hands versions tillägg som läggs till i PowerShellGet och PowerShell-galleriet](https://devblogs.microsoft.com/powershell/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) i PowerShell-teamets blogg.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://devblogs.microsoft.com/powershell/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="e6b9a-112">Med kryss rutorna under List rutan kan användarna filtrera resultaten genom att:</span><span class="sxs-lookup"><span data-stu-id="e6b9a-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>

- <span data-ttu-id="e6b9a-113">Paket typer</span><span class="sxs-lookup"><span data-stu-id="e6b9a-113">Package Types</span></span>
  - <span data-ttu-id="e6b9a-114">Modul</span><span class="sxs-lookup"><span data-stu-id="e6b9a-114">Module</span></span>
  - <span data-ttu-id="e6b9a-115">Skript</span><span class="sxs-lookup"><span data-stu-id="e6b9a-115">Script</span></span>
- <span data-ttu-id="e6b9a-116">Kategorier</span><span class="sxs-lookup"><span data-stu-id="e6b9a-116">Categories</span></span>
  - <span data-ttu-id="e6b9a-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e6b9a-117">Cmdlet</span></span>
  - <span data-ttu-id="e6b9a-118">DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="e6b9a-118">DSC Resource</span></span>
  - <span data-ttu-id="e6b9a-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="e6b9a-119">Function</span></span>
  - <span data-ttu-id="e6b9a-120">Roll kapacitet</span><span class="sxs-lookup"><span data-stu-id="e6b9a-120">Role Capability</span></span>
  - <span data-ttu-id="e6b9a-121">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="e6b9a-121">Workflow</span></span>

<span data-ttu-id="e6b9a-122">Om du bara vill se moduler i PowerShell-galleriet kontrollerar du modulen i paket typerna.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span> <span data-ttu-id="e6b9a-123">På samma sätt kan du kontrol lera skriptet i paket typerna om du bara vill se skript i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b9a-124">Filtren är inkluderade.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-124">Filters are inclusive.</span></span> <span data-ttu-id="e6b9a-125">Exempel: ett paket som innehåller båda cmdletar och funktioner visas om antingen cmdlet eller function (eller båda) är markerade.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span> <span data-ttu-id="e6b9a-126">Om ingen väljs visas inte paketet.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-126">If neither are selected, the package will not appear.</span></span> <span data-ttu-id="e6b9a-127">På samma sätt visas bara paket som innehåller en av dessa kategorier om du väljer alla kategorier.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span> <span data-ttu-id="e6b9a-128">**Paket som inte tillhör någon av dessa kategorier visas inte.**</span><span class="sxs-lookup"><span data-stu-id="e6b9a-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="e6b9a-129">Sortera efter</span><span class="sxs-lookup"><span data-stu-id="e6b9a-129">Sort By</span></span>

<span data-ttu-id="e6b9a-130">I list rutan Sortera enligt kan användarna sortera resultaten genom att:</span><span class="sxs-lookup"><span data-stu-id="e6b9a-130">The Sort By drop-down allows users to sort the results by:</span></span>

- <span data-ttu-id="e6b9a-131">Popularitet – populariteten bestäms av antalet hämtningar</span><span class="sxs-lookup"><span data-stu-id="e6b9a-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="e6b9a-132">A-Z-alfabetiskt efter paket namn</span><span class="sxs-lookup"><span data-stu-id="e6b9a-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="e6b9a-133">Senaste-paket visas i ordning av Publicerings datum</span><span class="sxs-lookup"><span data-stu-id="e6b9a-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="e6b9a-134">Sökruta</span><span class="sxs-lookup"><span data-stu-id="e6b9a-134">Search Box</span></span>

<span data-ttu-id="e6b9a-135">Med sökrutan kan användarna söka igenom paketen efter nyckelord.</span><span class="sxs-lookup"><span data-stu-id="e6b9a-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="e6b9a-136">Mer information finns i [syntax för Galleri sökning](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="e6b9a-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
