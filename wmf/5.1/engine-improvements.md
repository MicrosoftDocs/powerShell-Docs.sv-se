---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
title: "PowerShell-motorn förbättringar i WMF 5.1"
ms.openlocfilehash: 6c8000ccfc59ab46de95dc4f67161e12a5a41199
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
#<a name="powershell-engine-improvements"></a><span data-ttu-id="64f67-103">Förbättringar av PowerShell-motorn</span><span class="sxs-lookup"><span data-stu-id="64f67-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="64f67-104">Följande förbättringar i PowerShell kärnmotor har implementerats i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="64f67-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>


## <a name="performance"></a><span data-ttu-id="64f67-105">Prestanda</span><span class="sxs-lookup"><span data-stu-id="64f67-105">Performance</span></span> ##

<span data-ttu-id="64f67-106">Prestanda har förbättrats i vissa viktiga områden:</span><span class="sxs-lookup"><span data-stu-id="64f67-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="64f67-107">Start</span><span class="sxs-lookup"><span data-stu-id="64f67-107">Startup</span></span>
- <span data-ttu-id="64f67-108">Pipelining till cmdletar som ForEach-Object och Where-Object är ungefär 50% snabbare</span><span class="sxs-lookup"><span data-stu-id="64f67-108">Pipelining to cmdlets like ForEach-Object and Where-Object is approximately 50% faster</span></span> 

<span data-ttu-id="64f67-109">Vissa exempel förbättringar (resultat kan variera beroende på din maskinvara):</span><span class="sxs-lookup"><span data-stu-id="64f67-109">Some example improvements (your results may vary depending on your hardware):</span></span> 

| <span data-ttu-id="64f67-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="64f67-110">Scenario</span></span> | <span data-ttu-id="64f67-111">5.0 tid (ms)</span><span class="sxs-lookup"><span data-stu-id="64f67-111">5.0 Time (ms)</span></span> | <span data-ttu-id="64f67-112">5.1-tid (ms)</span><span class="sxs-lookup"><span data-stu-id="64f67-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="64f67-113">900</span><span class="sxs-lookup"><span data-stu-id="64f67-113">900</span></span> | <span data-ttu-id="64f67-114">250</span><span class="sxs-lookup"><span data-stu-id="64f67-114">250</span></span> |
| <span data-ttu-id="64f67-115">Första någonsin PowerShell kör:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="64f67-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="64f67-116">30000</span><span class="sxs-lookup"><span data-stu-id="64f67-116">30000</span></span> | <span data-ttu-id="64f67-117">13000</span><span class="sxs-lookup"><span data-stu-id="64f67-117">13000</span></span> |
| <span data-ttu-id="64f67-118">Kommandot analysis cache har skapats:`powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="64f67-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="64f67-119">7000</span><span class="sxs-lookup"><span data-stu-id="64f67-119">7000</span></span> | <span data-ttu-id="64f67-120">520</span><span class="sxs-lookup"><span data-stu-id="64f67-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="64f67-121">1400</span><span class="sxs-lookup"><span data-stu-id="64f67-121">1400</span></span> | <span data-ttu-id="64f67-122">750</span><span class="sxs-lookup"><span data-stu-id="64f67-122">750</span></span> |
  
> <span data-ttu-id="64f67-123">Obs en ändring som rör start kan påverka vissa som inte stöds av scenarier.</span><span class="sxs-lookup"><span data-stu-id="64f67-123">Note One change related to startup might impact some unsupported scenarios.</span></span> 
> <span data-ttu-id="64f67-124">PowerShell läser inte längre filerna `$pshome\*.ps1xml` --filerna har konverterats till C# för att undvika vissa fil- och CPU omkostnader för bearbetning av XML-filer.</span><span class="sxs-lookup"><span data-stu-id="64f67-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> 
<span data-ttu-id="64f67-125">Filerna som finns kvar V2-stöd sida vid sida, så om du ändrar filens innehåll kan den inte har någon effekt till V5 endast V2.</span><span class="sxs-lookup"><span data-stu-id="64f67-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> 
<span data-ttu-id="64f67-126">Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="64f67-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="64f67-127">En annan synbar förändring är hur PowerShell cachelagrar exporterade kommandon och annan information för moduler som är installerade på en dator.</span><span class="sxs-lookup"><span data-stu-id="64f67-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="64f67-128">Det här cacheminnet har tidigare lagras i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="64f67-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="64f67-129">I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="64f67-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="64f67-130">Se [modulen analys Cache](scenarios-features.md#module-analysis-cache) för mer information.</span><span class="sxs-lookup"><span data-stu-id="64f67-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>

