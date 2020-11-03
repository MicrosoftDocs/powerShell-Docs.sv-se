---
description: Beskriver `Sequence` nyckelordet som kör markerade aktiviteter sekventiellt.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270938"
---
# <a name="about-sequence"></a><span data-ttu-id="d931e-104">Om sekvenser</span><span class="sxs-lookup"><span data-stu-id="d931e-104">About Sequence</span></span>

## <a name="short-description"></a><span data-ttu-id="d931e-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="d931e-105">Short description</span></span>

<span data-ttu-id="d931e-106">Beskriver `Sequence` nyckelordet som kör markerade aktiviteter sekventiellt.</span><span class="sxs-lookup"><span data-stu-id="d931e-106">Describes the `Sequence` keyword that runs selected activities sequentially.</span></span>

## <a name="long-description"></a><span data-ttu-id="d931e-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="d931e-107">Long description</span></span>

<span data-ttu-id="d931e-108">`Sequence`Nyckelordet kör markerade arbets flödes aktiviteter i tur och ordning.</span><span class="sxs-lookup"><span data-stu-id="d931e-108">The `Sequence` keyword runs selected workflow activities sequentially.</span></span> <span data-ttu-id="d931e-109">Arbets flödes aktiviteter körs i den ordning som de visas och körs inte samtidigt.</span><span class="sxs-lookup"><span data-stu-id="d931e-109">Workflow activities run in the order that they appear and do not run concurrently.</span></span> <span data-ttu-id="d931e-110">`Sequence`Nyckelordet är endast giltigt i ett PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="d931e-110">The `Sequence` keyword is only valid in a PowerShell Workflow.</span></span>

<span data-ttu-id="d931e-111">`Sequence`Nyckelordet används i ett- `Parallel` skript block för att köra markerade kommandon i tur och ordning.</span><span class="sxs-lookup"><span data-stu-id="d931e-111">The `Sequence` keyword is used in a `Parallel` script block to run selected commands sequentially.</span></span>

<span data-ttu-id="d931e-112">Eftersom arbets flödes aktiviteter körs sekventiellt som standard `Sequence` är nyckelordet endast effektivt i ett- `Parallel` skript block.</span><span class="sxs-lookup"><span data-stu-id="d931e-112">Because workflow activities run sequentially by default, the `Sequence` keyword is only effective in a `Parallel` script block.</span></span> <span data-ttu-id="d931e-113">Om `Sequence` nyckelordet inte ingår i ett `Parallel` -skript block, är det giltigt men ineffektiv.</span><span class="sxs-lookup"><span data-stu-id="d931e-113">If the `Sequence` keyword isn't included in a `Parallel` script block, it's valid but ineffective.</span></span>

<span data-ttu-id="d931e-114">Med `Sequence` skript blocket kan du köra fler kommandon parallellt genom att köra beroende kommandon i tur och ordning.</span><span class="sxs-lookup"><span data-stu-id="d931e-114">The `Sequence` script block lets you run more commands in parallel by allowing you to run dependent commands sequentially.</span></span>

## <a name="syntax"></a><span data-ttu-id="d931e-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="d931e-115">Syntax</span></span>

### <a name="workflow-using-sequence"></a><span data-ttu-id="d931e-116">Arbets flöde med sekvens</span><span class="sxs-lookup"><span data-stu-id="d931e-116">Workflow using Sequence</span></span>

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a><span data-ttu-id="d931e-117">Arbets flöde med parallell och sekvens</span><span class="sxs-lookup"><span data-stu-id="d931e-117">Workflow using Parallel and Sequence</span></span>

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a><span data-ttu-id="d931e-118">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="d931e-118">Detailed description</span></span>

<span data-ttu-id="d931e-119">Kommandona i ett- `Parallel` skript block kan köras samtidigt.</span><span class="sxs-lookup"><span data-stu-id="d931e-119">The commands in a `Parallel` script block can run concurrently.</span></span> <span data-ttu-id="d931e-120">Ordningen som de körs i avgörs inte.</span><span class="sxs-lookup"><span data-stu-id="d931e-120">The order in which they run is not determined.</span></span> <span data-ttu-id="d931e-121">Den här funktionen förbättrar prestanda för ett skript arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="d931e-121">This feature improves the performance of a script workflow.</span></span>

<span data-ttu-id="d931e-122">Du kan använda ett- `Sequence` skript block för att köra valda aktiviteter sekventiellt, även om aktiviteterna visas i ett- `Parallel` skript block.</span><span class="sxs-lookup"><span data-stu-id="d931e-122">You can use a `Sequence` script block to run selected activities sequentially, even though the activities appear in a `Parallel` script block.</span></span>

<span data-ttu-id="d931e-123">Aktiviteterna i ett `Sequence` skript block körs löpande i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="d931e-123">The activities in a `Sequence` script block run consecutively in the order that they are listed.</span></span> <span data-ttu-id="d931e-124">En aktivitet i ett- `Sequence` skript block startar först efter att föregående aktivitet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="d931e-124">An activity in a `Sequence` script block starts only after the previous activity completes.</span></span>

<span data-ttu-id="d931e-125">Men när skript blocket `Sequence` visas i ett `Parallel` -skript block, bestäms i vilken ordning `Sequence` skript blocket körs.</span><span class="sxs-lookup"><span data-stu-id="d931e-125">However, when the `Sequence` script block appears in a `Parallel` script block, the order in which the `Sequence` script block runs isn't determined.</span></span> <span data-ttu-id="d931e-126">Det kan köras före, efter eller samtidigt med andra aktiviteter i `Parallel` skript blocket.</span><span class="sxs-lookup"><span data-stu-id="d931e-126">It might run before, after, or concurrent with other activities in the `Parallel` script block.</span></span>

<span data-ttu-id="d931e-127">Följande arbets flöde innehåller till exempel ett- `Parallel` skript block som kör aktiviteter som får processer och tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="d931e-127">For example, the following workflow includes a `Parallel` script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="d931e-128">`Parallel`Skript blocket innehåller ett `Sequence` skript block som hämtar information från en fil och använder informationen som indata till ett skript.</span><span class="sxs-lookup"><span data-stu-id="d931e-128">The `Parallel` script block contains a `Sequence` script block that gets information from a file and uses the information as input to a script.</span></span>

<span data-ttu-id="d931e-129">`Get-Process` `Get-Service` Kommandona, och som hör till Hotfix är oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="d931e-129">The `Get-Process`, `Get-Service`, and hotfix-related commands are independent of each other.</span></span> <span data-ttu-id="d931e-130">Kommandona kan köras samtidigt eller i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="d931e-130">The commands can run concurrently or in any order.</span></span> <span data-ttu-id="d931e-131">Men kommandot som hämtar information om snabb korrigeringar måste köras före det kommando som använder det.</span><span class="sxs-lookup"><span data-stu-id="d931e-131">But, the command that gets the hotfix information must run before the command that uses it.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d931e-132">Se även</span><span class="sxs-lookup"><span data-stu-id="d931e-132">See also</span></span>

[<span data-ttu-id="d931e-133">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="d931e-133">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="d931e-134">about_ForEach – parallell</span><span class="sxs-lookup"><span data-stu-id="d931e-134">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="d931e-135">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d931e-135">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="d931e-136">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="d931e-136">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="d931e-137">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="d931e-137">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="d931e-138">Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="d931e-138">Creating a Workflow by Using a Windows PowerShell Script</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
