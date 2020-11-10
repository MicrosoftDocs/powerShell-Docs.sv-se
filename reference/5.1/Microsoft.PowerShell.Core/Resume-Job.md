---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 6d08d9053e100cb53d37a6e4931d118f90c35a6a
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388543"
---
# <span data-ttu-id="4d823-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="4d823-103">Resume-Job</span></span>

## <span data-ttu-id="4d823-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4d823-104">SYNOPSIS</span></span>
<span data-ttu-id="4d823-105">Startar om ett pausat jobb.</span><span class="sxs-lookup"><span data-stu-id="4d823-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="4d823-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4d823-106">SYNTAX</span></span>

### <span data-ttu-id="4d823-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="4d823-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d823-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="4d823-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d823-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="4d823-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d823-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="4d823-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d823-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="4d823-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4d823-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="4d823-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4d823-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4d823-113">DESCRIPTION</span></span>

<span data-ttu-id="4d823-114">`Resume-Job`Cmdleten återupptar ett arbets flödes jobb som har pausats, till exempel med hjälp av `Suspend-Job` cmdleten eller aktiviteten [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) .</span><span class="sxs-lookup"><span data-stu-id="4d823-114">The `Resume-Job` cmdlet resumes a workflow job that was suspended, such as by using the `Suspend-Job` cmdlet or the [about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md) activity.</span></span> <span data-ttu-id="4d823-115">När ett arbets flödes jobb återupptas konstruerar jobb motorn om status, metadata och utdata från sparade resurser, t. ex. kontroll punkter.</span><span class="sxs-lookup"><span data-stu-id="4d823-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span> <span data-ttu-id="4d823-116">Jobbet startas om utan att tillstånd eller data går förlorade.</span><span class="sxs-lookup"><span data-stu-id="4d823-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="4d823-117">Jobb tillståndet har ändrats från **pausad** till att **köras**.</span><span class="sxs-lookup"><span data-stu-id="4d823-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="4d823-118">Använd parametrarna för `Resume-Job` för att välja jobb efter namn, ID, instans-ID eller pipe ett jobb objekt, till exempel ett som returneras av `Get-Job` cmdleten, till `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d823-118">Use the parameters of `Resume-Job` to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the `Get-Job` cmdlet, to `Resume-Job`.</span></span> <span data-ttu-id="4d823-119">Du kan också använda ett egenskaps filter för att välja ett jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="4d823-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="4d823-120">Som standard `Resume-Job` returneras omedelbart, även om alla jobb kanske inte återupptas ännu.</span><span class="sxs-lookup"><span data-stu-id="4d823-120">By default, `Resume-Job` returns immediately, even though all jobs might not yet be resumed.</span></span> <span data-ttu-id="4d823-121">Om du vill ignorera kommando tolken tills alla angivna jobb har återupptagits, använder du parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="4d823-121">To suppress the command prompt until all specified jobs are resumed, use the **Wait** parameter.</span></span>

<span data-ttu-id="4d823-122">`Resume-Job`Cmdleten fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="4d823-122">The `Resume-Job` cmdlet works only on custom job types, such as workflow jobs.</span></span> <span data-ttu-id="4d823-123">Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d823-123">It does not work on standard background jobs, such as those that are started by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="4d823-124">Om du skickar ett jobb av en typ som inte stöds `Resume-Job` genererar ett avslutande fel och slutar att köras.</span><span class="sxs-lookup"><span data-stu-id="4d823-124">If you submit a job of an unsupported type, `Resume-Job` generates a terminating error and stops running.</span></span>

<span data-ttu-id="4d823-125">Du identifierar ett arbets flödes jobb genom att leta efter värdet **PSWorkflowJob** i **PSJobTypeName** -egenskapen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="4d823-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span> <span data-ttu-id="4d823-126">Information om hur du avgör om en viss anpassad Jobbtyp stöder `Resume-Job` cmdleten finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="4d823-126">To determine whether a particular custom job type supports the `Resume-Job` cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="4d823-127">Innan du använder en jobb-cmdlet på en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen, antingen med hjälp av `Import-Module` cmdleten eller hämtar eller använder en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="4d823-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the `Import-Module` cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="4d823-128">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4d823-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="4d823-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4d823-129">EXAMPLES</span></span>

### <span data-ttu-id="4d823-130">Exempel 1: återuppta ett jobb efter ID</span><span class="sxs-lookup"><span data-stu-id="4d823-130">Example 1: Resume a job by ID</span></span>

<span data-ttu-id="4d823-131">Kommandona i det här exemplet kontrollerar att jobbet är ett pausat arbets flödes jobb och sedan återupptar jobbet.</span><span class="sxs-lookup"><span data-stu-id="4d823-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span> <span data-ttu-id="4d823-132">Det första kommandot använder `Get-Job` cmdleten för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="4d823-132">The first command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="4d823-133">Utdata visar att jobbet är ett pausat arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="4d823-133">The output shows that the job is a suspended workflow job.</span></span> <span data-ttu-id="4d823-134">Det andra kommandot använder cmdlet **:** en för cmdlet: en för `Resume-Job` att återuppta jobbet med **ID-** värdet 4.</span><span class="sxs-lookup"><span data-stu-id="4d823-134">The second command uses the **Id** parameter of the `Resume-Job` cmdlet to resume the job with an **Id** value of 4.</span></span>

```
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

PS C:\> Resume-Job -Id 4
```

### <span data-ttu-id="4d823-135">Exempel 2: återuppta ett jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="4d823-135">Example 2: Resume a job by name</span></span>

<span data-ttu-id="4d823-136">Det här kommandot använder parametern **Name** för att återuppta flera arbets flödes jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4d823-136">This command uses the **Name** parameter to resume several workflow jobs on the local computer.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

### <span data-ttu-id="4d823-137">Exempel 3: Använd anpassade egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="4d823-137">Example 3: Use custom property values</span></span>

<span data-ttu-id="4d823-138">Det här kommandot använder värdet för en anpassad egenskap för att identifiera det arbets flödes jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="4d823-138">This command uses the value of a custom property to identify the workflow job to resume.</span></span> <span data-ttu-id="4d823-139">Den använder **filter** parametern för att identifiera arbets flödes jobbet med egenskapen **CustomID** .</span><span class="sxs-lookup"><span data-stu-id="4d823-139">It uses the **Filter** parameter to identify the workflow job by its **CustomID** property.</span></span> <span data-ttu-id="4d823-140">Den använder också parametern **State** för att kontrol lera att arbets flödes jobbet har pausats innan det försöker återuppta det.</span><span class="sxs-lookup"><span data-stu-id="4d823-140">It also uses the **State** parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

### <span data-ttu-id="4d823-141">Exempel 4: återuppta alla pausade jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="4d823-141">Example 4: Resume all suspended jobs on a remote computer</span></span>

<span data-ttu-id="4d823-142">Det här kommandot återupptar alla pausade jobb på den fjärranslutna SRV01-datorn.</span><span class="sxs-lookup"><span data-stu-id="4d823-142">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="4d823-143">Kommandot använder `Invoke-Command` cmdleten för att köra ett kommando på datorn SRV01.</span><span class="sxs-lookup"><span data-stu-id="4d823-143">The command uses the `Invoke-Command` cmdlet to run a command on the Srv01 computer.</span></span> <span data-ttu-id="4d823-144">Fjärrkommandot använder cmdleten **State** för `Get-Job` cmdleten för att hämta alla pausade jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="4d823-144">The remote command uses the **State** parameter of the `Get-Job` cmdlet to get all suspended jobs on the computer.</span></span> <span data-ttu-id="4d823-145">En pipeline-operator ( `|` ) skickar de pausade jobben till `Resume-Job` cmdleten, som återupptar dem.</span><span class="sxs-lookup"><span data-stu-id="4d823-145">A pipeline operator (`|`) sends the suspended jobs to the `Resume-Job` cmdlet, which resumes them.</span></span>

### <span data-ttu-id="4d823-146">Exempel 5: vänta tills jobben återupptas</span><span class="sxs-lookup"><span data-stu-id="4d823-146">Example 5: Wait for jobs to resume</span></span>

<span data-ttu-id="4d823-147">Det här kommandot använder parametern **wait** för att `Resume-Job` endast returnera när alla angivna jobb har återupptagits.</span><span class="sxs-lookup"><span data-stu-id="4d823-147">This command uses the **Wait** parameter to direct `Resume-Job` to return only after all specified jobs are resumed.</span></span> <span data-ttu-id="4d823-148">Parametern **wait** är särskilt användbar i skript som förutsätter att jobb återupptas innan skriptet fortsätter.</span><span class="sxs-lookup"><span data-stu-id="4d823-148">The **Wait** parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

### <span data-ttu-id="4d823-149">Exempel 6: återuppta ett arbets flöde som pausar sig själv</span><span class="sxs-lookup"><span data-stu-id="4d823-149">Example 6: Resume a workflow that suspends itself</span></span>

<span data-ttu-id="4d823-150">I det här kod exemplet visas `Suspend-Workflow` aktiviteten i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="4d823-150">This code sample shows the `Suspend-Workflow` activity in a workflow.</span></span>

<span data-ttu-id="4d823-151">`Test-Suspend`Arbets flödet på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="4d823-151">The `Test-Suspend` workflow on the Server01 computer.</span></span> <span data-ttu-id="4d823-152">När du kör arbets flödet kör arbets flödet `Get-Date` aktiviteten och lagrar resultatet i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4d823-152">When you run the workflow, the workflow runs the `Get-Date` activity and stores the result in the `$a` variable.</span></span> <span data-ttu-id="4d823-153">Sedan körs `Suspend-Workflow` aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="4d823-153">Then it runs the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="4d823-154">Som svar tar det en kontroll punkt, pausar arbets flödet och returnerar ett arbets flödes jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="4d823-154">In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.</span></span> <span data-ttu-id="4d823-155">`Suspend-Workflow` Returnerar ett arbets flödes jobb objekt även om arbets flödet inte körs explicit som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="4d823-155">`Suspend-Workflow` returns a workflow job object even if the workflow is not explicitly run as a job.</span></span>

<span data-ttu-id="4d823-156">`Resume-Job` återupptar `Test-Suspend` arbets flödet i Job8.</span><span class="sxs-lookup"><span data-stu-id="4d823-156">`Resume-Job` resumes the `Test-Suspend` workflow in Job8.</span></span> <span data-ttu-id="4d823-157">Parametern **wait** används för att lagra kommando tolken tills jobbet återupptas.</span><span class="sxs-lookup"><span data-stu-id="4d823-157">It uses the **Wait** parameter to hold the command prompt until the job is resumed.</span></span>

<span data-ttu-id="4d823-158">`Receive-Job`Cmdlet: en hämtar resultatet av `Test-Suspend` arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="4d823-158">The `Receive-Job` cmdlet gets the results of the `Test-Suspend` workflow.</span></span> <span data-ttu-id="4d823-159">Det sista kommandot i arbets flödet returnerar ett **TimeSpan** -objekt som representerar den förflutna tiden mellan aktuellt datum och tid och datum och tid som sparades i `$a` variabeln innan arbets flödet pausades.</span><span class="sxs-lookup"><span data-stu-id="4d823-159">The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the `$a` variable before the workflow was suspended.</span></span>

```
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

PS C:\> Receive-Job -Name Job8
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
        PSComputerName    : Server01
```

<span data-ttu-id="4d823-160">Med `Resume-Job` cmdleten kan du återuppta ett arbets flödes jobb som har pausats med hjälp av `Suspend-Workflow` aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="4d823-160">The `Resume-Job` cmdlet lets you resume a workflow job that was suspend by using the `Suspend-Workflow` activity.</span></span> <span data-ttu-id="4d823-161">Den här aktiviteten pausar ett arbets flöde i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="4d823-161">This activity suspends a workflow from within a workflow.</span></span> <span data-ttu-id="4d823-162">Den är endast giltig i arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="4d823-162">It is valid only in workflows.</span></span>

<span data-ttu-id="4d823-163">Information om finns `Suspend-Workflow` i about_Suspend-Workflow] (.. /PSWorkflow/about/about_Suspend-Workflow. MD).</span><span class="sxs-lookup"><span data-stu-id="4d823-163">For information about the `Suspend-Workflow`, see about_Suspend-Workflow](../PSWorkflow/about/about_Suspend-Workflow.md).</span></span>

## <span data-ttu-id="4d823-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4d823-164">PARAMETERS</span></span>

### <span data-ttu-id="4d823-165">-Filter</span><span class="sxs-lookup"><span data-stu-id="4d823-165">-Filter</span></span>

<span data-ttu-id="4d823-166">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="4d823-166">Specifies a hash table of conditions.</span></span> <span data-ttu-id="4d823-167">Den här cmdleten återupptar jobb som uppfyller alla villkor i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="4d823-167">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="4d823-168">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="4d823-168">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="4d823-169">-ID</span><span class="sxs-lookup"><span data-stu-id="4d823-169">-Id</span></span>

<span data-ttu-id="4d823-170">Anger en matris med ID: n för jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="4d823-170">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="4d823-171">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d823-171">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="4d823-172">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d823-172">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="4d823-173">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="4d823-173">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="4d823-174">Kör för att hitta ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d823-174">To find the ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="4d823-175">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="4d823-175">-InstanceId</span></span>

<span data-ttu-id="4d823-176">Anger en matris med instans-ID: n för jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="4d823-176">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="4d823-177">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="4d823-177">The default is all jobs.</span></span>

<span data-ttu-id="4d823-178">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="4d823-178">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="4d823-179">Kör om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="4d823-179">To find the instance ID of a job, run `Get-Job`.</span></span>

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

### <span data-ttu-id="4d823-180">– Jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-180">-Job</span></span>

<span data-ttu-id="4d823-181">Anger vilka jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="4d823-181">Specifies the jobs to be resumed.</span></span> <span data-ttu-id="4d823-182">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="4d823-182">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="4d823-183">Du kan också skicka vidare jobb till- `Resume-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d823-183">You can also pipe jobs to the `Resume-Job` cmdlet.</span></span>

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

### <span data-ttu-id="4d823-184">-Name</span><span class="sxs-lookup"><span data-stu-id="4d823-184">-Name</span></span>

<span data-ttu-id="4d823-185">Anger en matris med användarvänliga namn på jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="4d823-185">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span> <span data-ttu-id="4d823-186">Ange ett eller flera jobb namn.</span><span class="sxs-lookup"><span data-stu-id="4d823-186">Enter one or more job names.</span></span>
<span data-ttu-id="4d823-187">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4d823-187">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="4d823-188">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="4d823-188">-State</span></span>

<span data-ttu-id="4d823-189">Anger tillstånd för jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="4d823-189">Specifies the state of jobs to resume.</span></span> <span data-ttu-id="4d823-190">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4d823-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4d823-191">NotStarted</span><span class="sxs-lookup"><span data-stu-id="4d823-191">NotStarted</span></span>
- <span data-ttu-id="4d823-192">Körs</span><span class="sxs-lookup"><span data-stu-id="4d823-192">Running</span></span>
- <span data-ttu-id="4d823-193">Slutförd</span><span class="sxs-lookup"><span data-stu-id="4d823-193">Completed</span></span>
- <span data-ttu-id="4d823-194">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="4d823-194">Failed</span></span>
- <span data-ttu-id="4d823-195">Stoppad</span><span class="sxs-lookup"><span data-stu-id="4d823-195">Stopped</span></span>
- <span data-ttu-id="4d823-196">Blockerad</span><span class="sxs-lookup"><span data-stu-id="4d823-196">Blocked</span></span>
- <span data-ttu-id="4d823-197">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="4d823-197">Suspended</span></span>
- <span data-ttu-id="4d823-198">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="4d823-198">Disconnected</span></span>
- <span data-ttu-id="4d823-199">Pausar</span><span class="sxs-lookup"><span data-stu-id="4d823-199">Suspending</span></span>
- <span data-ttu-id="4d823-200">Stoppas</span><span class="sxs-lookup"><span data-stu-id="4d823-200">Stopping</span></span>

<span data-ttu-id="4d823-201">Denna cmdlet återupptar bara jobb i tillståndet **Suspended** .</span><span class="sxs-lookup"><span data-stu-id="4d823-201">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="4d823-202">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="4d823-202">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="4d823-203">– Vänta</span><span class="sxs-lookup"><span data-stu-id="4d823-203">-Wait</span></span>

<span data-ttu-id="4d823-204">Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat har startats om.</span><span class="sxs-lookup"><span data-stu-id="4d823-204">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span> <span data-ttu-id="4d823-205">Som standard returnerar denna cmdlet omedelbart de tillgängliga resultaten.</span><span class="sxs-lookup"><span data-stu-id="4d823-205">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="4d823-206">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4d823-206">-Confirm</span></span>

<span data-ttu-id="4d823-207">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d823-207">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4d823-208">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4d823-208">-WhatIf</span></span>

<span data-ttu-id="4d823-209">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4d823-209">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4d823-210">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4d823-210">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4d823-211">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4d823-211">CommonParameters</span></span>

<span data-ttu-id="4d823-212">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4d823-212">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4d823-213">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4d823-213">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4d823-214">INDATA</span><span class="sxs-lookup"><span data-stu-id="4d823-214">INPUTS</span></span>

### <span data-ttu-id="4d823-215">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="4d823-215">System.Management.Automation.Job</span></span>

<span data-ttu-id="4d823-216">Du kan skicka vidare alla typer av jobb till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4d823-216">You can pipe all types of jobs to this cmdlet.</span></span> <span data-ttu-id="4d823-217">Om `Resume-Job` hämtar ett jobb av en typ som inte stöds returneras ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="4d823-217">If `Resume-Job` gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="4d823-218">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4d823-218">OUTPUTS</span></span>

### <span data-ttu-id="4d823-219">Ingen, system. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="4d823-219">None, System.Management.Automation.Job</span></span>

<span data-ttu-id="4d823-220">Den här cmdleten returnerar de jobb som det försöker återuppta, om du använder parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="4d823-220">This cmdlet returns the jobs that it tries to resume, if you use the **PassThru** parameter.</span></span>
<span data-ttu-id="4d823-221">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4d823-221">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4d823-222">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4d823-222">NOTES</span></span>

- <span data-ttu-id="4d823-223">`Resume-Job` Det går bara att återuppta jobb som har pausats.</span><span class="sxs-lookup"><span data-stu-id="4d823-223">`Resume-Job` can only resume jobs that are suspended.</span></span> <span data-ttu-id="4d823-224">Om du skickar ett jobb med ett annat tillstånd `Resume-Job` Kör återställnings åtgärden för jobbet, men genererar en varning för att meddela att det inte gick att återuppta jobbet.</span><span class="sxs-lookup"><span data-stu-id="4d823-224">If you submit a job in a different state, `Resume-Job` runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="4d823-225">Om du vill utelämna varningen använder du den gemensamma parametern **WarningAction** med värdet SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="4d823-225">To suppress the warning, use the **WarningAction** common parameter with a value of SilentlyContinue.</span></span>
- <span data-ttu-id="4d823-226">Om ett jobb inte är av en typ som har stöd för att återuppta, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), `Resume-Job` returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="4d823-226">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), `Resume-Job` returns a terminating error.</span></span>
- <span data-ttu-id="4d823-227">Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen.</span><span class="sxs-lookup"><span data-stu-id="4d823-227">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="4d823-228">Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en SQL-databas.</span><span class="sxs-lookup"><span data-stu-id="4d823-228">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
- <span data-ttu-id="4d823-229">När du återupptar ett jobb ändras jobb tillståndet från **pausat** till att **köras**.</span><span class="sxs-lookup"><span data-stu-id="4d823-229">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="4d823-230">Om du vill hitta jobb som kör, inklusive de som har återupptagits av denna cmdlet, använder du parametern **State** för cmdlet: en `Get-Job` för att hämta jobb i **körnings** tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4d823-230">To find the jobs that are running, including those that were resumed by this cmdlet, use the **State** parameter of the `Get-Job` cmdlet to get jobs in the **Running** state.</span></span>
- <span data-ttu-id="4d823-231">Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet.</span><span class="sxs-lookup"><span data-stu-id="4d823-231">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span>
  <span data-ttu-id="4d823-232">Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="4d823-232">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="4d823-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4d823-233">RELATED LINKS</span></span>

[<span data-ttu-id="4d823-234">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="4d823-235">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="4d823-236">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="4d823-237">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="4d823-238">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-238">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="4d823-239">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="4d823-239">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="4d823-240">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="4d823-240">Wait-Job</span></span>](Wait-Job.md)
