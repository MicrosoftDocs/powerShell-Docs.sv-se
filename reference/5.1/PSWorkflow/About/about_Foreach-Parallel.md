---
description: Beskriver `ForEach -Parallel` språk konstruktion i Windows PowerShell-arbetsflöde.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/10/2019
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_foreach-parallel?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Foreach parallell
ms.openlocfilehash: 1012b45396b65d424dacac067c2af8d3b6823f92
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270956"
---
# <a name="about-foreach-parallel"></a><span data-ttu-id="a495a-104">Om Foreach-Parallel</span><span class="sxs-lookup"><span data-stu-id="a495a-104">About Foreach-Parallel</span></span>

## <a name="short-description"></a><span data-ttu-id="a495a-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a495a-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a495a-106">Beskriver `ForEach -Parallel` språk konstruktion i Windows PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="a495a-106">Describes the `ForEach -Parallel` language construct in Windows PowerShell Workflow.</span></span>

## <a name="long-description"></a><span data-ttu-id="a495a-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a495a-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a495a-108">Den **parallella** parametern för `ForEach` nyckelordet kör kommandona i ett `ForEach` skript block en gång för varje objekt i en angiven samling.</span><span class="sxs-lookup"><span data-stu-id="a495a-108">The **Parallel** parameter of the `ForEach` keyword runs the commands in a `ForEach` script block once for each item in a specified collection.</span></span>

<span data-ttu-id="a495a-109">Objekten i samlingen, till exempel en disk i en samling diskar, bearbetas parallellt.</span><span class="sxs-lookup"><span data-stu-id="a495a-109">The items in the collection, such as a disk in a collection of disks, are processed in parallel.</span></span> <span data-ttu-id="a495a-110">Kommandona i skript blocket körs sekventiellt på varje objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="a495a-110">The commands in the script block run sequentially on each item in the collection.</span></span>

<span data-ttu-id="a495a-111">`ForEach -Parallel` är endast giltig i ett Windows PowerShell-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="a495a-111">`ForEach -Parallel` is valid only in a Windows PowerShell Workflow.</span></span>

### <a name="syntax"></a><span data-ttu-id="a495a-112">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a495a-112">SYNTAX</span></span>

```
ForEach -Parallel ($<item> in $<collection>)
{
    [<Activity1>]
    [<Activity2>]
    ...
}
```

### <a name="detailed-description"></a><span data-ttu-id="a495a-113">DETALJERAD BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a495a-113">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="a495a-114">Precis som i Windows PowerShell måste variabeln som innehåller samling `$<collection>` definieras före `ForEach -Parallel` instruktionen, men variabeln som representerar det aktuella objektet `$<item>` definieras i `ForEach -Parallel` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="a495a-114">Like the ForEach statement in Windows PowerShell, the variable that contains collection `$<collection>` must be defined before the `ForEach -Parallel` statement, but the variable that represents the current item `$<item>` is defined in the `ForEach -Parallel` statement.</span></span>

<span data-ttu-id="a495a-115">`ForEach -Parallel`Konstruktionen skiljer sig från `ForEach` nyckelordet och den **parallella** parametern.</span><span class="sxs-lookup"><span data-stu-id="a495a-115">The `ForEach -Parallel` construct is different from the `ForEach` keyword and the **Parallel** parameter.</span></span> <span data-ttu-id="a495a-116">`ForEach`Nyckelordet bearbetar objekten i insamlingen i sekvensen.</span><span class="sxs-lookup"><span data-stu-id="a495a-116">The `ForEach` keyword processes the items in the collection in sequence.</span></span> <span data-ttu-id="a495a-117">Den **parallella** parametern kör kommandon i ett skript block parallellt.</span><span class="sxs-lookup"><span data-stu-id="a495a-117">The **Parallel** parameter runs commands in a script block in parallel.</span></span> <span data-ttu-id="a495a-118">Du kan sätta ett parallellt skript block i ett- `ForEach -Parallel` skript block.</span><span class="sxs-lookup"><span data-stu-id="a495a-118">You can enclose a Parallel script block in a `ForEach -Parallel` script block.</span></span>

<span data-ttu-id="a495a-119">Mål datorerna i ett arbets flöde, till exempel de som anges av den gemensamma parametern för **PSComputerName** -arbetsflöde, bearbetas alltid parallellt.</span><span class="sxs-lookup"><span data-stu-id="a495a-119">The target computers in a workflow, such as those specified by the **PSComputerName** workflow common parameter, are always processed in parallel.</span></span>
<span data-ttu-id="a495a-120">Du behöver inte ange `ForEach -Parallel` nyckelordet för det här ändamålet.</span><span class="sxs-lookup"><span data-stu-id="a495a-120">You do not need to specify the `ForEach -Parallel` keyword for this purpose.</span></span>

### <a name="examples"></a><span data-ttu-id="a495a-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a495a-121">EXAMPLES</span></span>

<span data-ttu-id="a495a-122">Följande arbets flöde innehåller en `ForEach -Parallel` instruktion som bearbetar de diskar som `Get-Disk` aktiviteten hämtar.</span><span class="sxs-lookup"><span data-stu-id="a495a-122">The following workflow contains a `ForEach -Parallel` statement that processes the disks that the `Get-Disk` activity gets.</span></span> <span data-ttu-id="a495a-123">Kommandona i `ForEach -Parallel` skript blocket körs sekventiellt, men de körs på diskarna parallellt.</span><span class="sxs-lookup"><span data-stu-id="a495a-123">The commands in the `ForEach -Parallel` script block run sequentially, but they run on the disks in parallel.</span></span> <span data-ttu-id="a495a-124">Diskarna kan bearbetas samtidigt och i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="a495a-124">The disks might be processed concurrently and in any order.</span></span>

```powershell
workflow Test-Workflow
{
    $Disks = Get-Disk

    # The disks are processed in parallel.
    ForEach -Parallel ($Disk in $Disks)
    {
        # The commands run sequentially on each disk.
        $DiskPath = $Disk.Path
        $Disk | Initialize-Disk
        Set-Disk -Path $DiskPath
    }
}

workflow Test-Workflow
{
    #Run commands in parallel.
    Parallel
    {
        Get-Process
        Get-Service
    }

   $Disks = Get-Disk

   # The disks are processed in parallel.
   ForEach -Parallel ($Disk in $Disks)
   {
       # The commands run in parallel on each disk.
       Parallel
       {
           Initialize-Disk
           InlineScript {.\Get-DiskInventory}
       }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="a495a-125">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a495a-125">SEE ALSO</span></span>

[<span data-ttu-id="a495a-126">Skriva ett skript arbets flöde</span><span class="sxs-lookup"><span data-stu-id="a495a-126">Writing a Script Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)

[<span data-ttu-id="a495a-127">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="a495a-127">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_ForEach.md)

[<span data-ttu-id="a495a-128">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="a495a-128">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="a495a-129">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="a495a-129">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="a495a-130">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="a495a-130">about_Workflows</span></span>](about_Workflows.md)
