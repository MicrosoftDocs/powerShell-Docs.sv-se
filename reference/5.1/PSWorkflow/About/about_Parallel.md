---
description: Beskriver det parallella nyckelordet, som kör aktiviteterna i ett arbets flöde parallellt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parallel
ms.openlocfilehash: 402e93672bbea4ec9b6bfda8d608f266f6c40a21
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270944"
---
# <a name="about-parallel"></a><span data-ttu-id="a0a29-104">Om parallell</span><span class="sxs-lookup"><span data-stu-id="a0a29-104">About Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="a0a29-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0a29-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a0a29-106">Beskriver det parallella nyckelordet, som kör aktiviteterna i ett arbets flöde parallellt.</span><span class="sxs-lookup"><span data-stu-id="a0a29-106">Describes the Parallel keyword, which runs the activities in a workflow in parallel.</span></span>

## <a name="long-description"></a><span data-ttu-id="a0a29-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0a29-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a0a29-108">Det parallella nyckelordet kör arbets flödes aktiviteter parallellt.</span><span class="sxs-lookup"><span data-stu-id="a0a29-108">The Parallel keyword runs workflow activities in parallel.</span></span> <span data-ttu-id="a0a29-109">Det här nyckelordet är endast giltigt i Windows PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="a0a29-109">This keyword is valid only in  Windows PowerShell  Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="a0a29-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0a29-110">SYNTAX</span></span>

```
workflow <Verb-Noun>
{
     Parallel
     {
          [<Activity>]
          [<Activity>]
        ...
     }
 }
```

## <a name="detailed-description"></a><span data-ttu-id="a0a29-111">DETALJERAD BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0a29-111">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="a0a29-112">Kommandona i ett parallellt skript block kan köras samtidigt.</span><span class="sxs-lookup"><span data-stu-id="a0a29-112">The commands in a Parallel script block can run concurrently.</span></span> <span data-ttu-id="a0a29-113">Ordningen som de körs i avgörs inte.</span><span class="sxs-lookup"><span data-stu-id="a0a29-113">The order in which they run is not determined.</span></span>

<span data-ttu-id="a0a29-114">Följande arbets flöde innehåller till exempel ett parallellt skript block som kör aktiviteter som får processer och tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="a0a29-114">For example, the following workflow includes a Parallel script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="a0a29-115">Eftersom Get-Process-och Get-Service-kommandona är oberoende av varandra, kan de köras samtidigt och i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="a0a29-115">Because the Get-Process and Get-Service commands are independent of each other, they can run concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
         Get-Process
         Get-Service
    }
}
```

<span data-ttu-id="a0a29-116">Att köra kommandon parallellt är mycket effektivt och minskar den tid det tar att slutföra ett arbets flöde avsevärt.</span><span class="sxs-lookup"><span data-stu-id="a0a29-116">Running commands in parallel is very efficient and reduces the time it takes to complete a workflow significantly.</span></span>

<span data-ttu-id="a0a29-117">Om du vill köra markerade kommandon i ett parallellt skript block i sekventiell ordning använder du nyckelordet Sequence.</span><span class="sxs-lookup"><span data-stu-id="a0a29-117">To run selected commands in a Parallel script block in sequential order, use the Sequence keyword.</span></span> <span data-ttu-id="a0a29-118">Mer information finns i about_Sequence.</span><span class="sxs-lookup"><span data-stu-id="a0a29-118">For more information, see about_Sequence.</span></span>

<span data-ttu-id="a0a29-119">Om du vill köra ett parallellt skript block för objekt i en samling, använder du förtagnings-eller förgrunds-Parallel-nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a0a29-119">To run a Parallel script block on items in a collection, use the ForEach or ForEach -Parallel keywords.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0a29-120">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a0a29-120">SEE ALSO</span></span>

<span data-ttu-id="a0a29-121">["Skriva ett skript arbets flöde"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span><span class="sxs-lookup"><span data-stu-id="a0a29-121">["Writing a Script Workflow"](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/jj574157(v=ws.11))</span></span>

[<span data-ttu-id="a0a29-122">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="a0a29-122">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="a0a29-123">about_ForEach – parallell</span><span class="sxs-lookup"><span data-stu-id="a0a29-123">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="a0a29-124">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="a0a29-124">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="a0a29-125">about_Sequence</span><span class="sxs-lookup"><span data-stu-id="a0a29-125">about_Sequence</span></span>](about_Sequence.md)

[<span data-ttu-id="a0a29-126">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="a0a29-126">about_Workflows</span></span>](about_workflows.md)
