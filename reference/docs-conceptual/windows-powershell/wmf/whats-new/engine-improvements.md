---
ms.date: 06/12/2017
title: Förbättringar i PowerShell-motorn i WMF 5.1
description: Den här artikeln innehåller prestanda förbättringar i Windows PowerShell 5,1
ms.openlocfilehash: 34a4ed1ae4b00f5763848deaf2edad895e70c59a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655855"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="305ad-103">Förbättringar i PowerShell-motorn</span><span class="sxs-lookup"><span data-stu-id="305ad-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="305ad-104">Följande förbättringar av Core PowerShell-motorn har implementerats i WMF 5,1:</span><span class="sxs-lookup"><span data-stu-id="305ad-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="305ad-105">Prestanda</span><span class="sxs-lookup"><span data-stu-id="305ad-105">Performance</span></span>

<span data-ttu-id="305ad-106">Prestanda har förbättrats i vissa viktiga områden:</span><span class="sxs-lookup"><span data-stu-id="305ad-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="305ad-107">Start</span><span class="sxs-lookup"><span data-stu-id="305ad-107">Startup</span></span>
- <span data-ttu-id="305ad-108">Pipelining till-cmdletar som `ForEach-Object` och `Where-Object` är cirka 50% snabbare</span><span class="sxs-lookup"><span data-stu-id="305ad-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="305ad-109">Några exempel på förbättringar (resultatet kan variera beroende på maskin vara):</span><span class="sxs-lookup"><span data-stu-id="305ad-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="305ad-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="305ad-110">Scenario</span></span> | <span data-ttu-id="305ad-111">5,0 tid (MS)</span><span class="sxs-lookup"><span data-stu-id="305ad-111">5.0 Time (ms)</span></span> | <span data-ttu-id="305ad-112">5,1 tid (MS)</span><span class="sxs-lookup"><span data-stu-id="305ad-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="305ad-113">900</span><span class="sxs-lookup"><span data-stu-id="305ad-113">900</span></span> | <span data-ttu-id="305ad-114">250</span><span class="sxs-lookup"><span data-stu-id="305ad-114">250</span></span> |
| <span data-ttu-id="305ad-115">Första gången PowerShell kördes: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="305ad-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="305ad-116">30000</span><span class="sxs-lookup"><span data-stu-id="305ad-116">30000</span></span> | <span data-ttu-id="305ad-117">13000</span><span class="sxs-lookup"><span data-stu-id="305ad-117">13000</span></span> |
| <span data-ttu-id="305ad-118">Kommando analys-cache har skapats: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="305ad-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="305ad-119">7000</span><span class="sxs-lookup"><span data-stu-id="305ad-119">7000</span></span> | <span data-ttu-id="305ad-120">520</span><span class="sxs-lookup"><span data-stu-id="305ad-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="305ad-121">1400</span><span class="sxs-lookup"><span data-stu-id="305ad-121">1400</span></span> | <span data-ttu-id="305ad-122">750</span><span class="sxs-lookup"><span data-stu-id="305ad-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="305ad-123">En ändring som är relaterad till Start kan påverka vissa scenarier som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="305ad-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="305ad-124">PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# för att undvika vissa fil-och processor kostnader för bearbetning av XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="305ad-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="305ad-125">Filerna finns kvar för att stödja v2 sida vid sida, så om du ändrar fil innehållet har den ingen effekt på V5, bara v2.</span><span class="sxs-lookup"><span data-stu-id="305ad-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="305ad-126">Observera att ändringar av innehållet i dessa filer aldrig har ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="305ad-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="305ad-127">En annan synlig ändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system.</span><span class="sxs-lookup"><span data-stu-id="305ad-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="305ad-128">Tidigare lagrades cacheminnet i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis` .</span><span class="sxs-lookup"><span data-stu-id="305ad-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="305ad-129">I WMF 5,1 är cachen en enda fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache` .</span><span class="sxs-lookup"><span data-stu-id="305ad-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="305ad-130">Mer information finns i [modul Analysis cache](release-notes.md#module-analysis-cache) .</span><span class="sxs-lookup"><span data-stu-id="305ad-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>
