---
description: Beskriver `InlineScript` aktiviteten som kör PowerShell-kommandon i ett arbets flöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_inlinescript?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_InlineScript
ms.openlocfilehash: 2eaeb02c6441865551b586e27a39c4000826752b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270951"
---
# <a name="about-inlinescript"></a><span data-ttu-id="0e851-104">Om InlineScript</span><span class="sxs-lookup"><span data-stu-id="0e851-104">About InlineScript</span></span>

## <a name="short-description"></a><span data-ttu-id="0e851-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="0e851-105">Short description</span></span>

<span data-ttu-id="0e851-106">Beskriver `InlineScript` aktiviteten som kör PowerShell-kommandon i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="0e851-106">Describes the `InlineScript` activity, that runs PowerShell commands in a workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="0e851-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="0e851-107">Long description</span></span>

<span data-ttu-id="0e851-108">`InlineScript`Aktiviteten Kör kommandon i en delad PowerShell-sessions arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="0e851-108">The `InlineScript` activity runs commands in a shared PowerShell session's workflow.</span></span> <span data-ttu-id="0e851-109">`InlineScript` är bara giltig i arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="0e851-109">`InlineScript` is only valid in workflows.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e851-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="0e851-110">Syntax</span></span>

```
InlineScript {<script block>} <ActivityCommonParameters>
```

## <a name="detailed-description"></a><span data-ttu-id="0e851-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="0e851-111">Detailed description</span></span>

<span data-ttu-id="0e851-112">`InlineScript`Aktiviteten Kör kommandon i en delad PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="0e851-112">The `InlineScript` activity runs commands in a shared PowerShell session.</span></span> <span data-ttu-id="0e851-113">Du kan inkludera det i ett arbets flöde för att köra kommandon som delar data och kommandon som inte annars är giltiga i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="0e851-113">You can include it in a workflow to run commands that share data and commands that aren't otherwise valid in a workflow.</span></span>

<span data-ttu-id="0e851-114">`InlineScript`Skript blocket kan innehålla alla giltiga PowerShell-kommandon och-uttryck.</span><span class="sxs-lookup"><span data-stu-id="0e851-114">The `InlineScript` script block can include all valid PowerShell commands and expressions.</span></span> <span data-ttu-id="0e851-115">Eftersom kommandon och uttryck i ett `InlineScript` skript block körs i samma session, delar de alla tillstånd och data, inklusive importerade moduler och värden för variabler.</span><span class="sxs-lookup"><span data-stu-id="0e851-115">Because the commands and expressions in an `InlineScript` script block run in the same session, they share all state and data, including imported modules and the values of variables.</span></span>

<span data-ttu-id="0e851-116">Du kan placera en `InlineScript` aktivitet var som helst i ett arbets flöde eller ett kapslat arbets flöde, inklusive i en loop eller kontroll-instruktion eller ett parallell-eller sekvens-skript block.</span><span class="sxs-lookup"><span data-stu-id="0e851-116">You can place an `InlineScript` activity anywhere in a workflow or nested workflow, including inside a loop or control statement or a Parallel or Sequence script block.</span></span>

<span data-ttu-id="0e851-117">`InlineScript`Aktiviteten har gemensamma aktivitets parametrar, inklusive **PSPersist**.</span><span class="sxs-lookup"><span data-stu-id="0e851-117">The `InlineScript` activity has the activity common parameters, including **PSPersist**.</span></span> <span data-ttu-id="0e851-118">Kommandona och uttrycken i ett- `InlineScript` skript block har dock inte de arbets flödes funktioner som kontroll punkter, eller beständighet, och gemensamma parametrar för arbets flöde eller aktivitet.</span><span class="sxs-lookup"><span data-stu-id="0e851-118">However, the commands and expressions in an `InlineScript` script block don't have the workflow features such as checkpointing, or persistence, and workflow or activity common parameters.</span></span> <span data-ttu-id="0e851-119">Mer information finns i [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0e851-119">For more information, see [about_ActivityCommonParameters](about_ActivityCommonParameters.md).</span></span>

## <a name="inlinescript-variables"></a><span data-ttu-id="0e851-120">InlineScript-variabler</span><span class="sxs-lookup"><span data-stu-id="0e851-120">InlineScript Variables</span></span>

<span data-ttu-id="0e851-121">Som standard är variablerna som definieras i ett arbets flöde inte synliga för kommandona i `InlineScript` skript blocket.</span><span class="sxs-lookup"><span data-stu-id="0e851-121">By default, the variables that are defined in a workflow aren't visible to the commands in the `InlineScript` script block.</span></span> <span data-ttu-id="0e851-122">`InlineScript`Använd omfångs modifieraren för att göra variabler för arbets flöden synliga för `$Using` .</span><span class="sxs-lookup"><span data-stu-id="0e851-122">To make workflow variables visible to the `InlineScript`, use the `$Using` scope modifier.</span></span> <span data-ttu-id="0e851-123">`$Using`Omfångs modifieraren krävs bara en gång för varje variabel i `InlineScript` .</span><span class="sxs-lookup"><span data-stu-id="0e851-123">The `$Using` scope modifier is required only once for each variable in the `InlineScript`.</span></span>

<span data-ttu-id="0e851-124">Mer information om `$Using` omfångs modifieraren finns i [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="0e851-124">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

<span data-ttu-id="0e851-125">I följande exempel visas att `$Using` omfångs modifieraren gör värdet för den `$a` översta arbets flödes variabeln som är tillgänglig för kommandona i `InlineScript` skript blocket.</span><span class="sxs-lookup"><span data-stu-id="0e851-125">The following example shows that the `$Using` scope modifier makes the value of the `$a` top-level workflow variable available to the commands in the `InlineScript` script block.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ## Without $Using, the $a workflow variable isn't visible
  ## in inline script.
  InlineScript {"Inline A0 = $a"}

  ## $Using imports the variable and its current value.
  InlineScript {"Inline A1 = $Using:a"}
}

Test-Workflow
```

```output
Inline A0 =
Inline A1 = 3
```

## <a name="returning-variables-in-inlinescript"></a><span data-ttu-id="0e851-126">Returnera variabler i InlineScript</span><span class="sxs-lookup"><span data-stu-id="0e851-126">Returning variables in InlineScript</span></span>

<span data-ttu-id="0e851-127">`InlineScript` kommandon kan ändra värdet för variabeln som har importer ATS från arbets flödets omfattning, men ändringarna visas inte i arbets flödes omfånget.</span><span class="sxs-lookup"><span data-stu-id="0e851-127">`InlineScript` commands can change the value of the variable that was imported from workflow scope, but the changes aren't visible in workflow scope.</span></span> <span data-ttu-id="0e851-128">Om du vill göra dem synliga returnerar du det ändrade värdet till arbets flödes omfånget, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="0e851-128">To make them visible, return the changed value to the workflow scope, as shown in the following example.</span></span>

```powershell
workflow Test-Workflow {
  $a = 3

  ##  Changes to the InlineScript variable value don't
  ##  change the workflow variable.
  InlineScript {
    $a = $Using:a+1;
    "Inline A = $a"
  }
  "Workflow A = $a"

  ##  To change the variable in workflow scope, return the
  ##  new value.
  $a = InlineScript {$b = $Using:a+1; $b}
  "Workflow New A = $a"
}

Test-Workflow
```

```output
Inline A = 4
Workflow A = 3
Workflow New A = 4
```

> [!NOTE]
> <span data-ttu-id="0e851-129">En instruktion med `$Using` omfångs modifieraren bör visas innan variabeln används i- `InlineScript` skript blocket.</span><span class="sxs-lookup"><span data-stu-id="0e851-129">A statement with the `$Using` scope modifier should appear before any use of the variable in the `InlineScript` script block.</span></span>

## <a name="running-in-process"></a><span data-ttu-id="0e851-130">Körs i processen</span><span class="sxs-lookup"><span data-stu-id="0e851-130">Running in-process</span></span>

<span data-ttu-id="0e851-131">För att förbättra tillförlitligheten körs kommandona i `InlineScript` skript blocket i sin egen process, separerade från processen där arbets flödet körs, och returnerar sedan utdata till arbets flödes processen.</span><span class="sxs-lookup"><span data-stu-id="0e851-131">To improve reliability, the commands in the `InlineScript` script block run in their own process, separate from the process in which the workflow runs, and then return their output to the workflow process.</span></span>

<span data-ttu-id="0e851-132">Om du vill Direct PowerShell för att köra `InlineScript` aktiviteten i arbets flödes processen tar du bort `InlineScript` värdet från **OutOfProcessActivity** -egenskapen i sessionen, till exempel genom att använda `New-PSWorkflowExecutionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0e851-132">To direct PowerShell to run the `InlineScript` activity in the workflow process, remove the `InlineScript` value from the **OutOfProcessActivity** property of the session configuration, such as by using the `New-PSWorkflowExecutionOption` cmdlet.</span></span>

### <a name="example"></a><span data-ttu-id="0e851-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="0e851-133">Example</span></span>

<span data-ttu-id="0e851-134">`InlineScript`I följande arbets flöde innehåller kommandon som är giltiga i PowerShell, men som inte är giltiga i arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="0e851-134">The `InlineScript` in the following workflow includes commands that are valid in PowerShell but aren't valid in workflows.</span></span> <span data-ttu-id="0e851-135">Till exempel `New-Object` cmdleten med parametern **ComObject** .</span><span class="sxs-lookup"><span data-stu-id="0e851-135">For example, the `New-Object` cmdlet with the **ComObject** parameter.</span></span>

```powershell
workflow Test-Workflow
{
  $ie = InlineScript {
    $ie = New-Object -ComObject InternetExplorer.Application -Property @{navigate2="www.microsoft.com"}

    $ie.Visible = $true
  }

  $ie
}

Test-Workflow
```

## <a name="see-also"></a><span data-ttu-id="0e851-136">Se även</span><span class="sxs-lookup"><span data-stu-id="0e851-136">See also</span></span>

[<span data-ttu-id="0e851-137">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e851-137">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)

[<span data-ttu-id="0e851-138">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="0e851-138">about_Remote_Variables</span></span>](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)

[<span data-ttu-id="0e851-139">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="0e851-139">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="0e851-140">[PSWorkflow](xref:PSWorkflow) -cmdletar</span><span class="sxs-lookup"><span data-stu-id="0e851-140">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="0e851-141">Arbetsflödesguiden</span><span class="sxs-lookup"><span data-stu-id="0e851-141">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="0e851-142">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="0e851-142">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
