---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892900"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="8647d-103">Förbättringar av PowerShell-motorn</span><span class="sxs-lookup"><span data-stu-id="8647d-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="8647d-104">Följande förbättringar i PowerShell core-motorn har införts i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="8647d-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="8647d-105">Prestanda</span><span class="sxs-lookup"><span data-stu-id="8647d-105">Performance</span></span>

<span data-ttu-id="8647d-106">Prestanda har förbättrats i vissa viktiga områden:</span><span class="sxs-lookup"><span data-stu-id="8647d-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="8647d-107">Start</span><span class="sxs-lookup"><span data-stu-id="8647d-107">Startup</span></span>
- <span data-ttu-id="8647d-108">Pipelining i cmdletar som `ForEach-Object` och `Where-Object` är ungefär 50% snabbare</span><span class="sxs-lookup"><span data-stu-id="8647d-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="8647d-109">Några exempel förbättringar (dina resultat kan variera beroende på din maskinvara):</span><span class="sxs-lookup"><span data-stu-id="8647d-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="8647d-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="8647d-110">Scenario</span></span> | <span data-ttu-id="8647d-111">5.0 tid (ms)</span><span class="sxs-lookup"><span data-stu-id="8647d-111">5.0 Time (ms)</span></span> | <span data-ttu-id="8647d-112">5.1-tid (ms)</span><span class="sxs-lookup"><span data-stu-id="8647d-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="8647d-113">900</span><span class="sxs-lookup"><span data-stu-id="8647d-113">900</span></span> | <span data-ttu-id="8647d-114">250</span><span class="sxs-lookup"><span data-stu-id="8647d-114">250</span></span> |
| <span data-ttu-id="8647d-115">Första någonsin PowerShell kör: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="8647d-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="8647d-116">30000</span><span class="sxs-lookup"><span data-stu-id="8647d-116">30000</span></span> | <span data-ttu-id="8647d-117">13000</span><span class="sxs-lookup"><span data-stu-id="8647d-117">13000</span></span> |
| <span data-ttu-id="8647d-118">Kommandot analysis cache som skapats: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="8647d-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="8647d-119">7000</span><span class="sxs-lookup"><span data-stu-id="8647d-119">7000</span></span> | <span data-ttu-id="8647d-120">520</span><span class="sxs-lookup"><span data-stu-id="8647d-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="8647d-121">1400</span><span class="sxs-lookup"><span data-stu-id="8647d-121">1400</span></span> | <span data-ttu-id="8647d-122">750</span><span class="sxs-lookup"><span data-stu-id="8647d-122">750</span></span> |

> [!Note]
> <span data-ttu-id="8647d-123">En ändring som rör start kan påverka vissa scenarier som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="8647d-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="8647d-124">PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# för att undvika att vissa fil och CPU overhead bearbeta XML-filer.</span><span class="sxs-lookup"><span data-stu-id="8647d-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="8647d-125">Filerna som finns kvar till support V2 sida vid sida, så om du ändrar filens innehåll, men inte har någon effekt till V5, endast V2.</span><span class="sxs-lookup"><span data-stu-id="8647d-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="8647d-126">Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="8647d-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="8647d-127">En annan synbar förändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system.</span><span class="sxs-lookup"><span data-stu-id="8647d-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="8647d-128">Tidigare var det här cacheminnet har lagrats i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="8647d-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="8647d-129">I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="8647d-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="8647d-130">Se [modulen Analysis Cache](scenarios-features.md#module-analysis-cache) för mer information.</span><span class="sxs-lookup"><span data-stu-id="8647d-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>