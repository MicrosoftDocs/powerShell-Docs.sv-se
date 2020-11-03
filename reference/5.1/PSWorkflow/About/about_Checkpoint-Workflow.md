---
description: Beskriver Checkpoint-Workflow aktivitet, som tar en kontroll punkt i ett arbets flöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_checkpoint-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Checkpoint arbets flöde
ms.openlocfilehash: 223deb07ff6ed387cf04736116ea0ce3f998bb59
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270957"
---
# <a name="about-checkpoint-workflow"></a><span data-ttu-id="e056e-104">Om Checkpoint-Workflow</span><span class="sxs-lookup"><span data-stu-id="e056e-104">About Checkpoint-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="e056e-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e056e-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e056e-106">Beskriver Checkpoint-Workflow aktivitet, som tar en kontroll punkt i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="e056e-106">Describes the Checkpoint-Workflow activity, which takes a checkpoint in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="e056e-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e056e-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e056e-108">Checkpoint-Workflow-aktiviteten tar en kontroll punkt, vilket sparar tillstånd och data i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="e056e-108">The Checkpoint-Workflow activity takes a checkpoint, which saves state and data in the workflow.</span></span> <span data-ttu-id="e056e-109">Om arbets flödet pausas eller avbryts kan det återupptas från den senaste kontroll punkten, i stället för att behöva startas om.</span><span class="sxs-lookup"><span data-stu-id="e056e-109">If the workflow is suspended or interrupted, it can be resumed from the most recent checkpoint, rather than having to be restarted.</span></span>

<span data-ttu-id="e056e-110">Checkpoint-Workflow-aktiviteten är bara giltig i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="e056e-110">The Checkpoint-Workflow activity is valid only in a workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="e056e-111">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e056e-111">SYNTAX</span></span>

```
Workflow <Verb-Noun>
{
    Checkpoint-Workflow
}
```

<span data-ttu-id="e056e-112">Checkpoint-Workflow aktiviteten accepterar inte några parametrar, inklusive vanliga parametrar och gemensamma parametrar för arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="e056e-112">The Checkpoint-Workflow activity does not accept any parameters, including common parameters and workflow common parameters.</span></span>

<span data-ttu-id="e056e-113">Du kan placera Checkpoint-Activity kontroll punkt var som helst i ett arbets flöde efter instruktionen CmdletBinding eller param.</span><span class="sxs-lookup"><span data-stu-id="e056e-113">You can place the Checkpoint-Activity checkpoint anywhere in a workflow after the CmdletBinding or Param statement.</span></span> <span data-ttu-id="e056e-114">Men när du placerar kontroll punkter bör du överväga prestanda kostnaden för insamling av data och skrivning till disk på den dator som kör arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="e056e-114">However, when placing checkpoints, consider the performance cost of collecting the data and writing it to disk on the computer that is running the workflow.</span></span>

<span data-ttu-id="e056e-115">Se till att tiden det tar att köra en del av arbets flödet igen om det avbryts är större än tiden det tar att skriva kontroll punkts tillstånd och data till disk.</span><span class="sxs-lookup"><span data-stu-id="e056e-115">Be sure that the time it takes to rerun a section of the workflow if it is interrupted is greater than the time it takes to write the checkpoint state and data to disk.</span></span>

<span data-ttu-id="e056e-116">Överväg att ta kontroll punkter efter viktiga steg så att arbets flödet kan återupptas i stället för att starta om.</span><span class="sxs-lookup"><span data-stu-id="e056e-116">Consider taking checkpoints after critical steps so the workflow can be resumed rather than restarted.</span></span> <span data-ttu-id="e056e-117">Ta till exempel en kontroll punkt efter kommandon som inte är idempotenta.</span><span class="sxs-lookup"><span data-stu-id="e056e-117">For example, take a checkpoint after commands that are not idempotent.</span></span>

### <a name="about-checkpoints"></a><span data-ttu-id="e056e-118">OM KONTROLL PUNKTER</span><span class="sxs-lookup"><span data-stu-id="e056e-118">ABOUT CHECKPOINTS</span></span>

<span data-ttu-id="e056e-119">En kontroll punkt är en ögonblicks bild av arbets flödets aktuella tillstånd, inklusive de aktuella värdena för variabler och alla utdata som genererats till den punkten och sparar dem på disk.</span><span class="sxs-lookup"><span data-stu-id="e056e-119">A checkpoint is a snapshot of the current state of the workflow, including the current values of variables, and any output generated up to that point, and it saves it to disk.</span></span>

<span data-ttu-id="e056e-120">Om ett arbets flöde avbryts, avsiktligt eller oavsiktligt, använder Windows PowerShell-arbetsflödeet automatiskt data i den senaste kontroll punkten för att återställa och återuppta arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="e056e-120">If a workflow is interrupted, intentionally or unintentionally, Windows PowerShell Workflow automatically uses the data in newest checkpoint to recover and resume the workflow.</span></span>

<span data-ttu-id="e056e-121">När du kör arbets flödet som ett jobb, t. ex. genom att använda den gemensamma AsJob-parametern för arbets flödet, behålls arbets flödets kontroll punkter tills du tar bort jobbet, till exempel med hjälp av Remove-Job cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e056e-121">When you run the workflow as a job, such as by using the AsJob workflow common parameter, the workflow checkpoints are retained until you delete the job, such as by using the Remove-Job cmdlet.</span></span>
<span data-ttu-id="e056e-122">Annars tas kontroll punkter för arbets flöden bort när arbets flödet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e056e-122">Otherwise, workflow checkpoints are deleted when the workflow completes.</span></span>

### <a name="other-checkpointing-techniques"></a><span data-ttu-id="e056e-123">ANDRA METODER FÖR KONTROLL PUNKTER</span><span class="sxs-lookup"><span data-stu-id="e056e-123">OTHER CHECKPOINTING TECHNIQUES</span></span>

<span data-ttu-id="e056e-124">Utöver Checkpoint-Workflow aktivitet stöder Windows PowerShell-arbetsflöde andra kontroll punkter, inklusive följande:</span><span class="sxs-lookup"><span data-stu-id="e056e-124">In addition to the Checkpoint-Workflow activity, Windows PowerShell Workflow supports other checkpointing techniques, including the following:</span></span>

- <span data-ttu-id="e056e-125">Gemensam parameter för PSPersist-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="e056e-125">PSPersist workflow common parameter</span></span>
- <span data-ttu-id="e056e-126">Gemensam parameter för PSPersist-aktivitet</span><span class="sxs-lookup"><span data-stu-id="e056e-126">PSPersist activity common parameter</span></span>
- <span data-ttu-id="e056e-127">PSPersistPreference-variabel (i ett arbets flöde)</span><span class="sxs-lookup"><span data-stu-id="e056e-127">PSPersistPreference variable (in a workflow)</span></span>

<span data-ttu-id="e056e-128">Mer information om hur du lägger till en kontroll punkt i ett arbets flöde finns i "så här lägger du till kontroll punkter i ett arbets flöde".</span><span class="sxs-lookup"><span data-stu-id="e056e-128">For more information about adding a checkpoint to a workflow, see "How to Add Checkpoints to a Workflow."</span></span>

## <a name="examples"></a><span data-ttu-id="e056e-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e056e-129">EXAMPLES</span></span>

<span data-ttu-id="e056e-130">Följande arbets flöde innehåller ett anrop till Checkpoint-Workflow-aktiviteten när en tids krävande funktion har slutförts och ett skript som delar data.</span><span class="sxs-lookup"><span data-stu-id="e056e-130">The following workflow includes a call to the Checkpoint-Workflow activity after completing a long-running function and a script that share data.</span></span>

```powershell
Workflow Test-Workflow
{
    $a = Invoke-LongRunningFunction
    InlineScript { \\Server\Share\Get-DataPacks.ps1 $Using:a}
    Checkpoint-Workflow

    Invoke-LongRunningFunction
    {
        ...
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e056e-131">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="e056e-131">SEE ALSO</span></span>

[<span data-ttu-id="e056e-132">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="e056e-132">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
