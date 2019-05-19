---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: PowerShell-motorn förbättringar i WMF 5.1
ms.openlocfilehash: a0af702832c0a90c994650e25918ecacdc33fc4b
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856184"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="d2c4e-103">Förbättringar av PowerShell-motorn</span><span class="sxs-lookup"><span data-stu-id="d2c4e-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="d2c4e-104">Följande förbättringar i PowerShell core-motorn har införts i WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="d2c4e-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="d2c4e-105">Prestanda</span><span class="sxs-lookup"><span data-stu-id="d2c4e-105">Performance</span></span>

<span data-ttu-id="d2c4e-106">Prestanda har förbättrats i vissa viktiga områden:</span><span class="sxs-lookup"><span data-stu-id="d2c4e-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="d2c4e-107">Start</span><span class="sxs-lookup"><span data-stu-id="d2c4e-107">Startup</span></span>
- <span data-ttu-id="d2c4e-108">Pipelining i cmdletar som `ForEach-Object` och `Where-Object` är ungefär 50% snabbare</span><span class="sxs-lookup"><span data-stu-id="d2c4e-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="d2c4e-109">Några exempel förbättringar (dina resultat kan variera beroende på din maskinvara):</span><span class="sxs-lookup"><span data-stu-id="d2c4e-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="d2c4e-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="d2c4e-110">Scenario</span></span> | <span data-ttu-id="d2c4e-111">5.0 tid (ms)</span><span class="sxs-lookup"><span data-stu-id="d2c4e-111">5.0 Time (ms)</span></span> | <span data-ttu-id="d2c4e-112">5.1-tid (ms)</span><span class="sxs-lookup"><span data-stu-id="d2c4e-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="d2c4e-113">900</span><span class="sxs-lookup"><span data-stu-id="d2c4e-113">900</span></span> | <span data-ttu-id="d2c4e-114">250</span><span class="sxs-lookup"><span data-stu-id="d2c4e-114">250</span></span> |
| <span data-ttu-id="d2c4e-115">Första någonsin PowerShell kör: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="d2c4e-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="d2c4e-116">30000</span><span class="sxs-lookup"><span data-stu-id="d2c4e-116">30000</span></span> | <span data-ttu-id="d2c4e-117">13000</span><span class="sxs-lookup"><span data-stu-id="d2c4e-117">13000</span></span> |
| <span data-ttu-id="d2c4e-118">Kommandot analysis cache som skapats: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="d2c4e-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="d2c4e-119">7000</span><span class="sxs-lookup"><span data-stu-id="d2c4e-119">7000</span></span> | <span data-ttu-id="d2c4e-120">520</span><span class="sxs-lookup"><span data-stu-id="d2c4e-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="d2c4e-121">1400</span><span class="sxs-lookup"><span data-stu-id="d2c4e-121">1400</span></span> | <span data-ttu-id="d2c4e-122">750</span><span class="sxs-lookup"><span data-stu-id="d2c4e-122">750</span></span> |

> [!NOTE]
> <span data-ttu-id="d2c4e-123">En ändring som rör start kan påverka vissa scenarier som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-123">One change related to startup might impact some unsupported scenarios.</span></span> <span data-ttu-id="d2c4e-124">PowerShell läser inte längre filerna `$pshome\*.ps1xml` – de här filerna har konverterats till C# att undvika att vissa fil- och CPU-belastning som bearbeta XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span> <span data-ttu-id="d2c4e-125">Filerna som finns kvar till support V2 sida vid sida, så om du ändrar filens innehåll, men inte har någon effekt till V5, endast V2.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span> <span data-ttu-id="d2c4e-126">Observera att ändra innehållet i filerna har aldrig ett scenario som stöds.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="d2c4e-127">En annan synbar förändring är hur PowerShell cachelagrar de exporterade kommandona och annan information för moduler som är installerade på ett system.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span> <span data-ttu-id="d2c4e-128">Tidigare var det här cacheminnet har lagrats i katalogen `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span> <span data-ttu-id="d2c4e-129">I WMF 5.1 cacheminnet är en enskild fil `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="d2c4e-130">Se [modulen Analysis Cache](release-notes.md#module-analysis-cache) för mer information.</span><span class="sxs-lookup"><span data-stu-id="d2c4e-130">See [Module Analysis Cache](release-notes.md#module-analysis-cache) for more details.</span></span>