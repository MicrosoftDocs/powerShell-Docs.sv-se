---
description: Beskriver `Suspend-Workflow` aktiviteten, som pausar arbets flödet där aktiviteten visas.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend arbets flöde
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270921"
---
# <a name="about-suspend-workflow"></a><span data-ttu-id="2fbfd-104">Om Suspend-Workflow</span><span class="sxs-lookup"><span data-stu-id="2fbfd-104">About Suspend-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="2fbfd-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="2fbfd-105">Short description</span></span>

<span data-ttu-id="2fbfd-106">Beskriver `Suspend-Workflow` aktiviteten, som pausar arbets flödet där aktiviteten visas.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-106">Describes the `Suspend-Workflow` activity, which suspends the workflow in which the activity appears.</span></span>

## <a name="long-description"></a><span data-ttu-id="2fbfd-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="2fbfd-107">Long description</span></span>

<span data-ttu-id="2fbfd-108">`Suspend-Workflow`Aktiviteten stoppar tillfälligt arbets flödes bearbetningen inifrån arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-108">The `Suspend-Workflow` activity temporarily stops workflow processing from within the workflow.</span></span> <span data-ttu-id="2fbfd-109">Innan du gör uppehåll, tar Windows PowerShell-arbetsflöde en kontroll punkt så att arbets flödets tillstånd och data bevaras och arbets flödet kan återupptas från uppehålls punkten.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-109">Before suspending, Windows PowerShell Workflow takes a checkpoint so the workflow's state and data are preserved and the workflow can resume from the suspension point.</span></span>

<span data-ttu-id="2fbfd-110">För att återuppta arbets flödet använder användaren som kör arbets flödet `Resume-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-110">To resume the workflow, the user running the workflow uses the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="2fbfd-111">Du kan inte återuppta ett arbets flöde inifrån arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-111">You can't resume a workflow from within the workflow.</span></span>

## <a name="syntax"></a><span data-ttu-id="2fbfd-112">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fbfd-112">Syntax</span></span>

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a><span data-ttu-id="2fbfd-113">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="2fbfd-113">Detailed description</span></span>

<span data-ttu-id="2fbfd-114">`Suspend-Workflow`Arbets flödet stoppas tillfälligt och ett jobb objekt som representerar arbets flödes jobbet returneras.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-114">The `Suspend-Workflow` temporarily stops the workflow and returns a job object that represents the workflow job.</span></span> <span data-ttu-id="2fbfd-115">Ett jobb objekt returneras även om du inte körde arbets flödet som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-115">A job object is returned even if you didn't run the workflow as a job.</span></span> <span data-ttu-id="2fbfd-116">Till exempel med den gemensamma parametern **AsJob** Workflow.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-116">For example, such as by using the **AsJob** workflow common parameter.</span></span> <span data-ttu-id="2fbfd-117">Jobb tillståndet har **pausats**.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-117">The job state is **Suspended**.</span></span>

<span data-ttu-id="2fbfd-118">Du kan använda jobb-cmdletar för att hantera det pausade arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-118">You can use the job cmdlets to manage the suspended workflow job.</span></span> <span data-ttu-id="2fbfd-119">Använd cmdleten för att återuppta arbets flödes jobbet `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="2fbfd-119">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span>

<span data-ttu-id="2fbfd-120">När du återupptar arbets flödes jobbet återupptas arbets flödet vid kommandot som följer efter- `Suspend-Workflow` aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-120">When you resume the workflow job, the workflow resumes at the command that follows the `Suspend-Workflow` activity.</span></span>

<span data-ttu-id="2fbfd-121">Följande arbets flöde innehåller till exempel `Suspend-Workflow` aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-121">For example, the following workflow includes the `Suspend-Workflow` activity.</span></span>
<span data-ttu-id="2fbfd-122">När du kör arbets flödet kör det `Get-Date` aktiviteten, sparar dess utdata i `$a` variabeln och pausar sedan arbets flödet och returnerar ett jobb objekt som representerar det pausade arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-122">When you run the workflow, it runs the `Get-Date` activity, saves its output in the `$a` variable, and then suspends the workflow, and returns a job object that represents the suspended workflow.</span></span> <span data-ttu-id="2fbfd-123">Jobb typen är **PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-123">The job type is **PSWorkflowJob**.</span></span>

<span data-ttu-id="2fbfd-124">Du kan använda jobb-cmdlet: ar, till exempel `Get-Job` för att hantera arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-124">You can use the job cmdlets, such as `Get-Job`, to manage the workflow job.</span></span>

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a><span data-ttu-id="2fbfd-125">Återupptar ett arbets flödes jobb</span><span class="sxs-lookup"><span data-stu-id="2fbfd-125">Resuming a workflow job</span></span>

<span data-ttu-id="2fbfd-126">Använd cmdleten för att återuppta arbets flödes jobbet `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="2fbfd-126">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="2fbfd-127">`Resume-Job`Cmdleten returnerar arbets flödes jobbets objekt omedelbart, även om det inte kan återupptas ännu.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-127">The `Resume-Job` cmdlet returns the workflow job object immediately, even though it might not yet be resumed.</span></span> <span data-ttu-id="2fbfd-128">Om du vill vänta på att jobbet ska återupptas använder du parametern **wait** eller använder `Get-Job` cmdleten för att hämta aktuellt jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-128">To wait for the job to be resumed, use the **Wait** parameter, or use the `Get-Job` cmdlet to get the current job object.</span></span>

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a><span data-ttu-id="2fbfd-129">Hämta utdata för ett arbets flödes jobb</span><span class="sxs-lookup"><span data-stu-id="2fbfd-129">Getting the output of a workflow job</span></span>

<span data-ttu-id="2fbfd-130">Använd cmdleten för att hämta utdata för ett arbets flödes jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="2fbfd-130">To get the output of a workflow job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="2fbfd-131">Utdata visar att arbets flödet har återupptagits vid kommandot som följde `Suspend-Workflow` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-131">The output shows that the workflow resumed at the command that followed the `Suspend-Workflow` cmdlet.</span></span> <span data-ttu-id="2fbfd-132">Värdet för `$a` variabeln, som fylldes före SUS pensionen, är tillgängligt för arbets flödet när det återupptas.</span><span class="sxs-lookup"><span data-stu-id="2fbfd-132">The value of the `$a` variable, which was populated before the suspension, is available to the workflow when it resumes.</span></span>

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a><span data-ttu-id="2fbfd-133">Se även</span><span class="sxs-lookup"><span data-stu-id="2fbfd-133">See also</span></span>

[<span data-ttu-id="2fbfd-134">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="2fbfd-134">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="2fbfd-135">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="2fbfd-135">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="2fbfd-136">[PSWorkflow](xref:PSWorkflow) -cmdletar</span><span class="sxs-lookup"><span data-stu-id="2fbfd-136">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="2fbfd-137">Arbetsflödesguiden</span><span class="sxs-lookup"><span data-stu-id="2fbfd-137">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="2fbfd-138">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="2fbfd-138">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
