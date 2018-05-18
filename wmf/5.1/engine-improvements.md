---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: 98095904157a675bbe84616b1d9cbb22689cd059
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="7abd4-103">Förbättringar av PowerShell-motorn</span><span class="sxs-lookup"><span data-stu-id="7abd4-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="7abd4-104">Följande förbättringar i PowerShell kärnmotor har implementerats i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="7abd4-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="7abd4-105">Prestanda</span><span class="sxs-lookup"><span data-stu-id="7abd4-105">Performance</span></span> ##

<span data-ttu-id="7abd4-106">Prestanda har förbättrats i vissa viktiga områden:</span><span class="sxs-lookup"><span data-stu-id="7abd4-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="7abd4-107">Start</span><span class="sxs-lookup"><span data-stu-id="7abd4-107">Startup</span></span>
- <span data-ttu-id="7abd4-108">Pipelining till cmdletar som ForEach-Object och Where-Object är ungefär 50% snabbare</span><span class="sxs-lookup"><span data-stu-id="7abd4-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span>

<span data-ttu-id="7abd4-109">Vissa exempel förbättringar (resultat kan variera beroende på din maskinvara):</span><span class="sxs-lookup"><span data-stu-id="7abd4-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="7abd4-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="7abd4-110">Scenario</span></span> | <span data-ttu-id="7abd4-111">5.0 tid (ms)</span><span class="sxs-lookup"><span data-stu-id="7abd4-111">5.0 Time (ms)</span></span> | <span data-ttu-id="7abd4-112">5.1-tid (ms)</span><span class="sxs-lookup"><span data-stu-id="7abd4-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="7abd4-113">900</span><span class="sxs-lookup"><span data-stu-id="7abd4-113">900</span></span> | <span data-ttu-id="7abd4-114">250</span><span class="sxs-lookup"><span data-stu-id="7abd4-114">250</span></span> |
| <span data-ttu-id="7abd4-115">Första någonsin PowerShell kör: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="7abd4-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="7abd4-116">30000</span><span class="sxs-lookup"><span data-stu-id="7abd4-116">30000</span></span> | <span data-ttu-id="7abd4-117">13000</span><span class="sxs-lookup"><span data-stu-id="7abd4-117">13000</span></span> |
| <span data-ttu-id="7abd4-118">Kommandot analysis cache har skapats: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="7abd4-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="7abd4-119">7000</span><span class="sxs-lookup"><span data-stu-id="7abd4-119">7000</span></span> | <span data-ttu-id="7abd4-120">520</span><span class="sxs-lookup"><span data-stu-id="7abd4-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="7abd4-121">1400</span><span class="sxs-lookup"><span data-stu-id="7abd4-121">1400</span></span> | <span data-ttu-id="7abd4-122">750</span><span class="sxs-lookup"><span data-stu-id="7abd4-122">750</span></span> |

> <span data-ttu-id="7abd4-123">Obs en ändring som rör start kan påverka vissa som inte stöds av scenarier.</span><span class="sxs-lookup"><span data-stu-id="7abd4-123">Note One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="7abd4-124">PowerShell läser inte längre filerna `$pshome\*.ps1xml` --filerna har konverterats till C# för att undvika vissa fil- och CPU omkostnader för bearbetning av XML-filer.</span><span class="sxs-lookup"><span data-stu-id="7abd4-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
<span data-ttu-id="7abd4-125">Filerna som finns kvar V2-stöd sida vid sida, så om du ändrar filens innehåll kan den inte har någon effekt till V5 endast V2.</span><span class="sxs-lookup"><span data-stu-id="7abd4-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
<span data-ttu-id="7abd4-126">Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="7abd4-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="7abd4-127">En annan synbar förändring är hur PowerShell cachelagrar exporterade kommandon och annan information för moduler som är installerade på en dator.</span><span class="sxs-lookup"><span data-stu-id="7abd4-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="7abd4-128">Det här cacheminnet har tidigare lagras i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="7abd4-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="7abd4-129">I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="7abd4-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="7abd4-130">Se [modulen analys Cache](scenarios-features.md#module-analysis-cache) för mer information.</span><span class="sxs-lookup"><span data-stu-id="7abd4-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>
