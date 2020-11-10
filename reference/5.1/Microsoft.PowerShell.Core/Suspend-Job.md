---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388475"
---
# <span data-ttu-id="055f3-103">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="055f3-103">Suspend-Job</span></span>

## <span data-ttu-id="055f3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="055f3-104">SYNOPSIS</span></span>
<span data-ttu-id="055f3-105">Stoppar tillfälligt arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-105">Temporarily stops workflow jobs.</span></span>

## <span data-ttu-id="055f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="055f3-106">SYNTAX</span></span>

### <span data-ttu-id="055f3-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="055f3-107">SessionIdParameterSet (Default)</span></span>

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="055f3-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="055f3-108">JobParameterSet</span></span>

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="055f3-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="055f3-109">NameParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="055f3-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="055f3-110">InstanceIdParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="055f3-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="055f3-111">FilterParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="055f3-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="055f3-112">StateParameterSet</span></span>

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="055f3-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="055f3-113">DESCRIPTION</span></span>

<span data-ttu-id="055f3-114">`Suspend-Job`Cmdleten pausar arbets flödes jobben.</span><span class="sxs-lookup"><span data-stu-id="055f3-114">The `Suspend-Job` cmdlet suspends workflow jobs.</span></span> <span data-ttu-id="055f3-115">Suspend innebär att tillfälligt avbryta eller pausa ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-115">Suspend means to temporarily interrupt or pause a workflow job.</span></span> <span data-ttu-id="055f3-116">Med den här cmdleten kan användare som kör arbets flöden pausa arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="055f3-116">This cmdlet allows users who are running workflows to suspend the workflow.</span></span> <span data-ttu-id="055f3-117">Den kompletterar aktiviteten pausa – arbets flöde https://go.microsoft.com/fwlink/?LinkId=267141 , som är ett kommando i arbets flödet som gör uppehåll i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="055f3-117">It complements the Suspend-Workflowhttps://go.microsoft.com/fwlink/?LinkId=267141 activity, which is a command in the workflow that suspends the workflow.</span></span>

<span data-ttu-id="055f3-118">`Suspend-Job`Cmdleten fungerar bara för arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-118">The `Suspend-Job` cmdlet works only on workflow jobs.</span></span> <span data-ttu-id="055f3-119">Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="055f3-119">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="055f3-120">Du identifierar ett arbets flödes jobb genom att leta efter värdet PSWorkflowJob i **PSJobTypeName** -egenskapen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-120">To identify a workflow job, look for a value of PSWorkflowJob in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="055f3-121">Information om hur du avgör om en viss anpassad Jobbtyp stöder `Suspend-Job` cmdleten finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="055f3-121">To determine whether a particular custom job type supports the `Suspend-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="055f3-122">När du pausar ett arbets flödes jobb körs arbets flödes jobbet till nästa kontroll punkt, pausar och returnerar omedelbart ett arbets flödes jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="055f3-122">When you suspend a workflow job, the workflow job runs to the next checkpoint, suspends, and immediately returns a workflow job object.</span></span> <span data-ttu-id="055f3-123">Om du vill vänta tills SUS pensionen har slutförts innan du hämtar jobbet använder du parametern **wait** i `Suspend-Job` eller `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="055f3-123">To wait for the suspension to complete before getting the job, use the **Wait** parameter of `Suspend-Job` or the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="055f3-124">När arbets flödes jobbet har pausats pausas värdet för jobbets **tillstånds** egenskap.</span><span class="sxs-lookup"><span data-stu-id="055f3-124">When the workflow job is suspended, the value of the **State** property of the job is Suspended.</span></span>

<span data-ttu-id="055f3-125">Att pausa är korrekt beroende av kontroll punkter.</span><span class="sxs-lookup"><span data-stu-id="055f3-125">Suspending correctly relies on checkpoints.</span></span> <span data-ttu-id="055f3-126">Det aktuella jobbets tillstånd, metadata och utdata sparas i kontroll punkten så att arbets flödes jobbet kan återupptas utan att tillstånd eller data går förlorade.</span><span class="sxs-lookup"><span data-stu-id="055f3-126">The current job state, metadata, and output are saved in the checkpoint so the workflow job can be resumed without loss of state or data.</span></span> <span data-ttu-id="055f3-127">Om arbets flödes jobbet inte har kontroll punkter, kan det inte inaktive ras på rätt sätt.</span><span class="sxs-lookup"><span data-stu-id="055f3-127">If the workflow job does not have checkpoints, it cannot be suspended correctly.</span></span> <span data-ttu-id="055f3-128">Om du vill lägga till kontroll punkter till ett arbets flöde som du kör använder du arbets flödets gemensamma parameter i **PSPersist** .</span><span class="sxs-lookup"><span data-stu-id="055f3-128">To add checkpoints to a workflow that you are running, use the **PSPersist** workflow common parameter.</span></span> <span data-ttu-id="055f3-129">Du kan använda **Force** -parametern för att pausa eventuella arbets flödes jobb omedelbart och pausa ett arbets flödes jobb som inte har några kontroll punkter, men åtgärden kan orsaka förlust av tillstånd och data.</span><span class="sxs-lookup"><span data-stu-id="055f3-129">You can use the **Force** parameter to suspend any workflow job immediately and to suspend a workflow job that does not have checkpoints, but the action could cause loss of state and data.</span></span>

<span data-ttu-id="055f3-130">Innan du använder en jobb-cmdlet på en anpassad Jobbtyp, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), importerar du modulen som stöder den anpassade jobb typen, antingen genom att använda `Import-Module` cmdleten eller använda eller använda en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="055f3-130">Before you use a Job cmdlet on a custom job type, such as a workflow job ( **PSWorkflowJob** ) import the module that supports the custom job type, either by using the `Import-Module` cmdlet or using or using a cmdlet in the module.</span></span>

<span data-ttu-id="055f3-131">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="055f3-131">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="055f3-132">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="055f3-132">EXAMPLES</span></span>

### <span data-ttu-id="055f3-133">Exempel 1: pausa ett arbets flödes jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="055f3-133">Example 1: Suspend a workflow job by name</span></span>

<span data-ttu-id="055f3-134">Det här exemplet visar hur du pausar ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-134">This example shows how to suspend a workflow job.</span></span>

<span data-ttu-id="055f3-135">Det första kommandot skapar `Get-SystemLog` arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="055f3-135">The first command creates the `Get-SystemLog` workflow.</span></span> <span data-ttu-id="055f3-136">Arbets flödet använder `CheckPoint-Workflow` aktiviteten för att definiera en kontroll punkt i arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="055f3-136">The workflow uses the `CheckPoint-Workflow` activity to define a checkpoint in the workflow.</span></span>

<span data-ttu-id="055f3-137">Det andra kommandot använder parametern **AsJob** som är gemensam för alla arbets flöden för att köra `Get-SystemLog` arbets flödet som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-137">The second command uses the **AsJob** parameter that is common to all workflows to run the `Get-SystemLog` workflow as a background job.</span></span> <span data-ttu-id="055f3-138">Kommandot använder den gemensamma parametern **JobName** Workflow för att ange ett eget namn för arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-138">The command uses the **JobName** workflow common parameter to specify a friendly name for the workflow job.</span></span>

<span data-ttu-id="055f3-139">Det tredje kommandot använder `Get-Job` cmdleten för att hämta `Get-SystemLogJob` arbets flödes jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-139">The third command uses the `Get-Job` cmdlet to get the `Get-SystemLogJob` workflow job.</span></span> <span data-ttu-id="055f3-140">Utdata visar att värdet för egenskapen **PSJobTypeName** är PSWorkflowJob.</span><span class="sxs-lookup"><span data-stu-id="055f3-140">The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.</span></span>

<span data-ttu-id="055f3-141">Det fjärde kommandot använder `Suspend-Job` cmdleten för att pausa `Get-SystemLogJob` jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-141">The fourth command uses the `Suspend-Job` cmdlet to suspend the `Get-SystemLogJob` job.</span></span> <span data-ttu-id="055f3-142">Jobbet körs till kontroll punkten och pausar sedan.</span><span class="sxs-lookup"><span data-stu-id="055f3-142">The job runs to the checkpoint and then suspends.</span></span>

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### <span data-ttu-id="055f3-143">Exempel 2: pausa och återuppta ett arbets flödes jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-143">Example 2: Suspend and resume a workflow job</span></span>

<span data-ttu-id="055f3-144">Det här exemplet visar hur du pausar och återupptar ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-144">This example shows how to suspend and resume a workflow job.</span></span>

<span data-ttu-id="055f3-145">Det första kommandot pausar LogWorkflowJob-jobbet. Kommandot returnerar omedelbart.</span><span class="sxs-lookup"><span data-stu-id="055f3-145">The first command suspends the LogWorkflowJob job.The command returns immediately.</span></span> <span data-ttu-id="055f3-146">Utdata visar att arbets flödes jobbet fortfarande körs, även om det har pausats.</span><span class="sxs-lookup"><span data-stu-id="055f3-146">The output shows that the workflow job is still running, even though it is being suspended.</span></span>

<span data-ttu-id="055f3-147">Det andra kommandot använder `Get-Job` cmdleten för att hämta LogWorkflowJob-jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-147">The second command uses the `Get-Job` cmdlet to get the LogWorkflowJob job.</span></span> <span data-ttu-id="055f3-148">Utdata visar att arbets flödes jobbet har pausats.</span><span class="sxs-lookup"><span data-stu-id="055f3-148">The output shows that the workflow job suspended successfully.</span></span>

<span data-ttu-id="055f3-149">Det tredje kommandot använder `Get-Job` cmdleten för att hämta LogWorkflowJob-jobbet och `Resume-Job` cmdleten för att återuppta det.</span><span class="sxs-lookup"><span data-stu-id="055f3-149">The third command uses the `Get-Job` cmdlet to get the LogWorkflowJob job and the `Resume-Job` cmdlet to resume it.</span></span> <span data-ttu-id="055f3-150">Utdata visar att arbets flödes jobbet har återupptagits och körs nu.</span><span class="sxs-lookup"><span data-stu-id="055f3-150">The output shows that the workflow job resumed successfully and is now running.</span></span>

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### <span data-ttu-id="055f3-151">Exempel 3: pausa ett arbets flödes jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="055f3-151">Example 3: Suspend a workflow job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

<span data-ttu-id="055f3-152">Det här kommandot använder `Invoke-Command` cmdleten för att pausa ett arbets flödes jobb på fjärrdatorn SRV01.</span><span class="sxs-lookup"><span data-stu-id="055f3-152">This command uses the `Invoke-Command` cmdlet to suspend a workflow job on the Srv01 remote computer.</span></span> <span data-ttu-id="055f3-153">Värdet för **filter** parametern är en hash-tabell som anger ett CustomID-värde.</span><span class="sxs-lookup"><span data-stu-id="055f3-153">The value of the **Filter** parameter is a hash table that specifies a CustomID value.</span></span>
<span data-ttu-id="055f3-154">Den här **CustomID** är jobb-metadata ( **PSPrivateMetadata** ).</span><span class="sxs-lookup"><span data-stu-id="055f3-154">This **CustomID** is job metadata ( **PSPrivateMetadata** ).</span></span>

### <span data-ttu-id="055f3-155">Exempel 4: vänta tills arbets flödes jobbet har pausats</span><span class="sxs-lookup"><span data-stu-id="055f3-155">Example 4: Wait for the workflow job to suspend</span></span>

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

<span data-ttu-id="055f3-156">Det här kommandot pausar arbets flödes jobbet VersionCheck.</span><span class="sxs-lookup"><span data-stu-id="055f3-156">This command suspends the VersionCheck workflow job.</span></span> <span data-ttu-id="055f3-157">Kommandot använder parametern **wait** för att vänta tills arbets flödes jobbet har pausats.</span><span class="sxs-lookup"><span data-stu-id="055f3-157">The command uses the **Wait** parameter to wait until the workflow job is suspended.</span></span> <span data-ttu-id="055f3-158">När arbets flödes jobbet körs till nästa kontroll punkt och har pausats, slutförs kommandot och jobbobjektet returneras.</span><span class="sxs-lookup"><span data-stu-id="055f3-158">When the workflow job runs to the next checkpoint and is suspended, the command finishes and returns the job object.</span></span>

### <span data-ttu-id="055f3-159">Exempel 5: tvinga en arbets flödes uppgift att pausa</span><span class="sxs-lookup"><span data-stu-id="055f3-159">Example 5: Force a workflow job to suspend</span></span>

```
PS C:\> Suspend-Job Maintenance -Force
```

<span data-ttu-id="055f3-160">Det här kommandot pausar jobbets tvingande arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-160">This command suspends the Maintenance workflow job forcibly.</span></span> <span data-ttu-id="055f3-161">Det finns inga kontroll punkter för underhålls jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-161">The Maintenance job does not have checkpoints.</span></span> <span data-ttu-id="055f3-162">Den kan inte inaktive ras korrekt och kanske inte återupptas korrekt.</span><span class="sxs-lookup"><span data-stu-id="055f3-162">It cannot be suspended correctly and might not resume correctly.</span></span>

## <span data-ttu-id="055f3-163">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="055f3-163">PARAMETERS</span></span>

### <span data-ttu-id="055f3-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="055f3-164">-Filter</span></span>

<span data-ttu-id="055f3-165">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="055f3-165">Specifies a hash table of conditions.</span></span> <span data-ttu-id="055f3-166">Denna cmdlet pausar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="055f3-166">This cmdlet suspends jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="055f3-167">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="055f3-167">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-168">-Force</span><span class="sxs-lookup"><span data-stu-id="055f3-168">-Force</span></span>

<span data-ttu-id="055f3-169">Pausar arbets flödes jobbet omedelbart.</span><span class="sxs-lookup"><span data-stu-id="055f3-169">Suspends the workflow job immediately.</span></span> <span data-ttu-id="055f3-170">Den här åtgärden kan leda till förlust av tillstånd och data.</span><span class="sxs-lookup"><span data-stu-id="055f3-170">This action could cause a loss of state and data.</span></span>

<span data-ttu-id="055f3-171">Som standard `Suspend-Job` kan arbets flödes jobbet köras fram till nästa kontroll punkt och sedan Pausa det.</span><span class="sxs-lookup"><span data-stu-id="055f3-171">By default, `Suspend-Job` lets the workflow job run until the next checkpoint and then suspends it.</span></span>
<span data-ttu-id="055f3-172">Du kan också använda den här parametern för att pausa arbets flödes jobb som inte har kontroll punkter.</span><span class="sxs-lookup"><span data-stu-id="055f3-172">You can also use this parameter to suspend workflow jobs that do not have checkpoints.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-173">-ID</span><span class="sxs-lookup"><span data-stu-id="055f3-173">-Id</span></span>

<span data-ttu-id="055f3-174">Anger ID: n för jobb som denna cmdlet pausar.</span><span class="sxs-lookup"><span data-stu-id="055f3-174">Specifies the IDs of jobs that this cmdlet suspends.</span></span>

<span data-ttu-id="055f3-175">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="055f3-175">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="055f3-176">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="055f3-176">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="055f3-177">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="055f3-177">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="055f3-178">Använd cmdleten för att hitta ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="055f3-178">To find the ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-179">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="055f3-179">-InstanceId</span></span>

<span data-ttu-id="055f3-180">Anger instans-ID: n för jobb som denna cmdlet pausar.</span><span class="sxs-lookup"><span data-stu-id="055f3-180">Specifies the instance IDs of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="055f3-181">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="055f3-181">The default is all jobs.</span></span>

<span data-ttu-id="055f3-182">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="055f3-182">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="055f3-183">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="055f3-183">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-184">– Jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-184">-Job</span></span>

<span data-ttu-id="055f3-185">Anger de arbets flödes jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="055f3-185">Specifies the workflow jobs that this cmdlet stops.</span></span> <span data-ttu-id="055f3-186">Ange en variabel som innehåller arbets flödes jobben eller ett kommando som hämtar arbets flödes jobben.</span><span class="sxs-lookup"><span data-stu-id="055f3-186">Enter a variable that contains the workflow jobs or a command that gets the workflow jobs.</span></span> <span data-ttu-id="055f3-187">Du kan också skicka ett arbets flödes jobb till `Suspend-Job` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="055f3-187">You can also pipe workflow jobs to the `Suspend-Job` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-188">-Name</span><span class="sxs-lookup"><span data-stu-id="055f3-188">-Name</span></span>

<span data-ttu-id="055f3-189">Anger egna namn på jobb som denna cmdlet pausar.</span><span class="sxs-lookup"><span data-stu-id="055f3-189">Specifies friendly names of jobs that this cmdlet suspends.</span></span> <span data-ttu-id="055f3-190">Ange ett eller flera arbets flödes jobb namn.</span><span class="sxs-lookup"><span data-stu-id="055f3-190">Enter one or more workflow job names.</span></span>
<span data-ttu-id="055f3-191">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="055f3-191">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-192">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="055f3-192">-State</span></span>

<span data-ttu-id="055f3-193">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="055f3-193">Specifies a job state.</span></span> <span data-ttu-id="055f3-194">Denna cmdlet stoppar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="055f3-194">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="055f3-195">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="055f3-195">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="055f3-196">NotStarted</span><span class="sxs-lookup"><span data-stu-id="055f3-196">NotStarted</span></span>
- <span data-ttu-id="055f3-197">Körs</span><span class="sxs-lookup"><span data-stu-id="055f3-197">Running</span></span>
- <span data-ttu-id="055f3-198">Slutförd</span><span class="sxs-lookup"><span data-stu-id="055f3-198">Completed</span></span>
- <span data-ttu-id="055f3-199">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="055f3-199">Failed</span></span>
- <span data-ttu-id="055f3-200">Stoppad</span><span class="sxs-lookup"><span data-stu-id="055f3-200">Stopped</span></span>
- <span data-ttu-id="055f3-201">Blockerad</span><span class="sxs-lookup"><span data-stu-id="055f3-201">Blocked</span></span>
- <span data-ttu-id="055f3-202">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="055f3-202">Suspended</span></span>
- <span data-ttu-id="055f3-203">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="055f3-203">Disconnected</span></span>
- <span data-ttu-id="055f3-204">Pausar</span><span class="sxs-lookup"><span data-stu-id="055f3-204">Suspending</span></span>
- <span data-ttu-id="055f3-205">Stoppas</span><span class="sxs-lookup"><span data-stu-id="055f3-205">Stopping</span></span>

<span data-ttu-id="055f3-206">`Suspend-Job` pausar endast arbets flödes jobb i **körnings** läge.</span><span class="sxs-lookup"><span data-stu-id="055f3-206">`Suspend-Job` suspends only workflow jobs in the **Running** state.</span></span>

<span data-ttu-id="055f3-207">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="055f3-207">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-208">– Vänta</span><span class="sxs-lookup"><span data-stu-id="055f3-208">-Wait</span></span>

<span data-ttu-id="055f3-209">Anger att denna cmdlet förhindrar kommando tolken tills arbets flödes jobbet har tillståndet Suspended.</span><span class="sxs-lookup"><span data-stu-id="055f3-209">Indicates that this cmdlet suppresses the command prompt until the workflow job is in the suspended state.</span></span> <span data-ttu-id="055f3-210">Som standard `Suspend-Job` returneras omedelbart, även om arbets flödes jobbet ännu inte har pausats.</span><span class="sxs-lookup"><span data-stu-id="055f3-210">By default, `Suspend-Job` returns immediately, even if the workflow job is not yet in the suspended state.</span></span>

<span data-ttu-id="055f3-211">Parametern **wait** motsvarar att skicka ett `Suspend-Job` kommando till `Wait-Job` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="055f3-211">The **Wait** parameter is equivalent to piping a `Suspend-Job` command to the `Wait-Job` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-212">-Confirm</span><span class="sxs-lookup"><span data-stu-id="055f3-212">-Confirm</span></span>

<span data-ttu-id="055f3-213">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="055f3-213">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-214">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="055f3-214">-WhatIf</span></span>

<span data-ttu-id="055f3-215">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="055f3-215">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="055f3-216">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="055f3-216">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="055f3-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="055f3-217">CommonParameters</span></span>

<span data-ttu-id="055f3-218">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="055f3-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="055f3-219">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="055f3-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="055f3-220">INDATA</span><span class="sxs-lookup"><span data-stu-id="055f3-220">INPUTS</span></span>

### <span data-ttu-id="055f3-221">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="055f3-221">System.Management.Automation.Job</span></span>

<span data-ttu-id="055f3-222">Du kan skicka vidare alla typer av jobb till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="055f3-222">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="055f3-223">Men om `Suspend-Job` hämtar ett jobb av en typ som inte stöds returneras ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="055f3-223">However, if `Suspend-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="055f3-224">UTDATA</span><span class="sxs-lookup"><span data-stu-id="055f3-224">OUTPUTS</span></span>

### <span data-ttu-id="055f3-225">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="055f3-225">System.Management.Automation.Job</span></span>
<span data-ttu-id="055f3-226">Denna cmdlet returnerar de jobb som den pausade.</span><span class="sxs-lookup"><span data-stu-id="055f3-226">This cmdlet returns the jobs that it suspended.</span></span>

## <span data-ttu-id="055f3-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="055f3-227">NOTES</span></span>

- <span data-ttu-id="055f3-228">Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen.</span><span class="sxs-lookup"><span data-stu-id="055f3-228">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="055f3-229">Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en databas.</span><span class="sxs-lookup"><span data-stu-id="055f3-229">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a database.</span></span>
- <span data-ttu-id="055f3-230">Om du skickar ett arbets flödes jobb som inte är i körnings tillstånd `Suspend-Job` visas ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="055f3-230">If you submit a workflow job that is not in the Running state, `Suspend-Job` displays a warning message.</span></span> <span data-ttu-id="055f3-231">Om du vill utelämna varningen använder du den gemensamma parametern **WarningAction** med värdet SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="055f3-231">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="055f3-232">Om ett jobb inte är av en typ som har stöd för att pausa, `Suspend-Job` returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="055f3-232">If a job is not of a type that supports suspending, `Suspend-Job` returns a terminating error.</span></span>

- <span data-ttu-id="055f3-233">Om du vill hitta de arbets flödes jobb som har pausats, inklusive de som har avbrutits med denna cmdlet, använder du cmdleten **State** för `Get-Job` cmdleten för att hämta arbets flödes jobb i tillståndet Suspended.</span><span class="sxs-lookup"><span data-stu-id="055f3-233">To find the workflow jobs that are suspended, including those that were suspended by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get workflow jobs in the Suspended state.</span></span>
- <span data-ttu-id="055f3-234">Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet.</span><span class="sxs-lookup"><span data-stu-id="055f3-234">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="055f3-235">Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="055f3-235">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="055f3-236">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="055f3-236">RELATED LINKS</span></span>

[<span data-ttu-id="055f3-237">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-237">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="055f3-238">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-238">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="055f3-239">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-239">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="055f3-240">Återuppta – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-240">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="055f3-241">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-241">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="055f3-242">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-242">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="055f3-243">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="055f3-243">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="055f3-244">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="055f3-244">Wait-Job</span></span>](Wait-Job.md)
