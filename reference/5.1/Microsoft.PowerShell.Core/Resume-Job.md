---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/resume-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Job
ms.openlocfilehash: 85cbfad2a4866bf18e69fb99afb8698e233c4c80
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264171"
---
# <span data-ttu-id="f608e-103">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="f608e-103">Resume-Job</span></span>

## <span data-ttu-id="f608e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f608e-104">SYNOPSIS</span></span>
<span data-ttu-id="f608e-105">Startar om ett pausat jobb.</span><span class="sxs-lookup"><span data-stu-id="f608e-105">Restarts a suspended job.</span></span>

## <span data-ttu-id="f608e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f608e-106">SYNTAX</span></span>

### <span data-ttu-id="f608e-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f608e-107">SessionIdParameterSet (Default)</span></span>

```
Resume-Job [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f608e-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="f608e-108">JobParameterSet</span></span>

```
Resume-Job [-Job] <Job[]> [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f608e-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f608e-109">NameParameterSet</span></span>

```
Resume-Job [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f608e-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f608e-110">InstanceIdParameterSet</span></span>

```
Resume-Job [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f608e-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="f608e-111">StateParameterSet</span></span>

```
Resume-Job [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f608e-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="f608e-112">FilterParameterSet</span></span>

```
Resume-Job [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f608e-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f608e-113">DESCRIPTION</span></span>
<span data-ttu-id="f608e-114">Cmdleten **Resume-Job** återupptar ett arbets flödes jobb som har pausats, till exempel med hjälp av Suspend-Job-cmdlet eller aktiviteten About_Suspend-arbetsflöde.</span><span class="sxs-lookup"><span data-stu-id="f608e-114">The **Resume-Job** cmdlet resumes a workflow job that was suspended, such as by using the Suspend-Job cmdlet or the about_Suspend-Workflow activity.</span></span>
<span data-ttu-id="f608e-115">När ett arbets flödes jobb återupptas konstruerar jobb motorn om status, metadata och utdata från sparade resurser, t. ex. kontroll punkter.</span><span class="sxs-lookup"><span data-stu-id="f608e-115">When a workflow job resumes, the job engine reconstructs the state, metadata, and output from saved resources, such as checkpoints.</span></span>
<span data-ttu-id="f608e-116">Jobbet startas om utan att tillstånd eller data går förlorade.</span><span class="sxs-lookup"><span data-stu-id="f608e-116">The job is restarted without any loss of state or data.</span></span>
<span data-ttu-id="f608e-117">Jobb tillståndet har ändrats från **pausad** till att **köras**.</span><span class="sxs-lookup"><span data-stu-id="f608e-117">The job state is changed from **Suspended** to **Running**.</span></span>

<span data-ttu-id="f608e-118">Använd parametrarna för **Resume-Job** för att välja jobb efter namn, ID, instans-ID eller pipe ett jobb objekt, till exempel ett som returneras av Get-Job cmdlet, för att **återuppta-jobbet**.</span><span class="sxs-lookup"><span data-stu-id="f608e-118">Use the parameters of **Resume-Job** to select jobs by name, ID, instance ID or pipe a job object, such as one returned by the Get-Job cmdlet, to **Resume-Job**.</span></span>
<span data-ttu-id="f608e-119">Du kan också använda ett egenskaps filter för att välja ett jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="f608e-119">You can also use a property filter to select a job to be resumed.</span></span>

<span data-ttu-id="f608e-120">Som standard returnerar **Resume-Job** omedelbart, även om alla jobb kanske inte återupptas ännu.</span><span class="sxs-lookup"><span data-stu-id="f608e-120">By default, **Resume-Job** returns immediately, even though all jobs might not yet be resumed.</span></span>
<span data-ttu-id="f608e-121">Om du vill ignorera kommando tolken tills alla angivna jobb har återupptagits, använder du parametern *wait* .</span><span class="sxs-lookup"><span data-stu-id="f608e-121">To suppress the command prompt until all specified jobs are resumed, use the *Wait* parameter.</span></span>

<span data-ttu-id="f608e-122">Cmdleten **Resume-Job** fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="f608e-122">The **Resume-Job** cmdlet works only on custom job types, such as workflow jobs.</span></span>
<span data-ttu-id="f608e-123">Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av Start-Job-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f608e-123">It does not work on standard background jobs, such as those that are started by using the Start-Job cmdlet.</span></span>
<span data-ttu-id="f608e-124">Om du skickar ett jobb av en typ som inte stöds genererar **Resume-Job** ett avslutande fel och slutar att köras.</span><span class="sxs-lookup"><span data-stu-id="f608e-124">If you submit a job of an unsupported type, **Resume-Job** generates a terminating error and stops running.</span></span>

<span data-ttu-id="f608e-125">Du identifierar ett arbets flödes jobb genom att leta efter värdet **PSWorkflowJob** i **PSJobTypeName** -egenskapen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="f608e-125">To identify a workflow job, look for a value of **PSWorkflowJob** in the **PSJobTypeName** property of the job.</span></span>
<span data-ttu-id="f608e-126">För att avgöra om en viss anpassad Jobbtyp stöder cmdleten **Resume-Job** , se hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="f608e-126">To determine whether a particular custom job type supports the **Resume-Job** cmdlet, see the help topics for the custom job type.</span></span>

<span data-ttu-id="f608e-127">Innan du använder en jobb-cmdlet på en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen, antingen med hjälp av Import-Module cmdlet eller hämtar eller använder en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="f608e-127">Before using a Job cmdlet on a custom job type, import the module that supports the custom job type, either by using the Import-Module cmdlet or getting or using a cmdlet in the module.</span></span>

<span data-ttu-id="f608e-128">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f608e-128">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f608e-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f608e-129">EXAMPLES</span></span>

### <span data-ttu-id="f608e-130">Exempel 1: återuppta ett jobb efter ID</span><span class="sxs-lookup"><span data-stu-id="f608e-130">Example 1: Resume a job by ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get the job. The output shows that the job is a suspended workflow job.
PS C:\> Get-Job EventJob
Id     Name            PSJobTypeName   State         HasMoreData     Location   Command
--     ----            -------------   -----         -----------     --------   -------
4      EventJob        PSWorkflowJob   Suspended     True            Server01   \\Script\Share\Event.ps1

The second command uses the *Id* parameter of the **Resume-Job** cmdlet to resume the job with an *Id* value of 4.
PS C:\> Resume-Job -Id 4
```

<span data-ttu-id="f608e-131">Kommandona i det här exemplet kontrollerar att jobbet är ett pausat arbets flödes jobb och sedan återupptar jobbet.</span><span class="sxs-lookup"><span data-stu-id="f608e-131">The commands in this example verify that the job is a suspended workflow job and then resume the job.</span></span>

### <span data-ttu-id="f608e-132">Exempel 2: återuppta ett jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="f608e-132">Example 2: Resume a job by name</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest*
```

<span data-ttu-id="f608e-133">Det här kommandot använder parametern *Name* för att återuppta flera arbets flödes jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f608e-133">This command uses the *Name* parameter to resume several workflow jobs on the local computer.</span></span>

### <span data-ttu-id="f608e-134">Exempel 3: Använd anpassade egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="f608e-134">Example 3: Use custom property values</span></span>

```
PS C:\> Resume-Job -Filter @{CustomID="T091291"} -State Suspended
```

<span data-ttu-id="f608e-135">Det här kommandot använder värdet för en anpassad egenskap för att identifiera det arbets flödes jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="f608e-135">This command uses the value of a custom property to identify the workflow job to resume.</span></span>
<span data-ttu-id="f608e-136">Den använder *filter* parametern för att identifiera arbets flödes jobbet med egenskapen **CustomID** .</span><span class="sxs-lookup"><span data-stu-id="f608e-136">It uses the *Filter* parameter to identify the workflow job by its **CustomID** property.</span></span>
<span data-ttu-id="f608e-137">Den använder också parametern *State* för att kontrol lera att arbets flödes jobbet har pausats innan det försöker återuppta det.</span><span class="sxs-lookup"><span data-stu-id="f608e-137">It also uses the *State* parameter to verify that the workflow job is suspended, before it tries to resume it.</span></span>

### <span data-ttu-id="f608e-138">Exempel 4: återuppta alla pausade jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="f608e-138">Example 4: Resume all suspended jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01 -ScriptBlock {Get-Job -State Suspended | Resume-Job}
```

<span data-ttu-id="f608e-139">Det här kommandot återupptar alla pausade jobb på den fjärranslutna SRV01-datorn.</span><span class="sxs-lookup"><span data-stu-id="f608e-139">This command resumes all suspended jobs on the Srv01 remote computer.</span></span>

<span data-ttu-id="f608e-140">Kommandot använder Invoke-Command cmdlet för att köra ett kommando på datorn SRV01.</span><span class="sxs-lookup"><span data-stu-id="f608e-140">The command uses the Invoke-Command cmdlet to run a command on the Srv01 computer.</span></span>
<span data-ttu-id="f608e-141">Fjärrkommandot använder-parametern *State* för cmdleten **Get-Job** för att hämta alla pausade jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="f608e-141">The remote command uses the *State* parameter of the **Get-Job** cmdlet to get all suspended jobs on the computer.</span></span>
<span data-ttu-id="f608e-142">En pipeline-operator (|) skickar de pausade jobben till cmdleten **Resume-Job** , som återupptar dem.</span><span class="sxs-lookup"><span data-stu-id="f608e-142">A pipeline operator (|) sends the suspended jobs to the **Resume-Job** cmdlet, which resumes them.</span></span>

### <span data-ttu-id="f608e-143">Exempel 5: vänta tills jobben återupptas</span><span class="sxs-lookup"><span data-stu-id="f608e-143">Example 5: Wait for jobs to resume</span></span>

```
PS C:\> Resume-Job -Name WorkflowJob, InventoryWorkflow, WFTest* -Wait
```

<span data-ttu-id="f608e-144">Det här kommandot använder parametern *wait* för att dirigera **Resume-Job** för att returnera endast när alla angivna jobb har återupptagits.</span><span class="sxs-lookup"><span data-stu-id="f608e-144">This command uses the *Wait* parameter to direct **Resume-Job** to return only after all specified jobs are resumed.</span></span>
<span data-ttu-id="f608e-145">Parametern *wait* är särskilt användbar i skript som förutsätter att jobb återupptas innan skriptet fortsätter.</span><span class="sxs-lookup"><span data-stu-id="f608e-145">The *Wait* parameter is especially useful in scripts that assume that jobs are resumed before the script continues.</span></span>

### <span data-ttu-id="f608e-146">Exempel 6: återuppta ett arbets flöde som pausar sig själv</span><span class="sxs-lookup"><span data-stu-id="f608e-146">Example 6: Resume a workflow that suspends itself</span></span>

```
This code sample shows the **Suspend-Workflow** activity in a workflow.
#SampleWorkflow
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

The following command runs the Test-Suspend workflow on the Server01 computer.When you run the workflow, the workflow runs the Get-Date activity and stores the result in the $a variable. Then it runs the Suspend-Workflow activity. In response, it takes a checkpoint, suspends the workflow, and returns a workflow job object.  Suspend-Workflow returns a workflow job object even if the workflow is not explicitly run as a job.
PS C:\> Test-Suspend -PSComputerName Server01
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
8      Job8            PSWorkflowJob   Suspended     True            Server01             Test-Suspend

The following command resumes the Test-Suspend workflow in Job8. It uses the *Wait* parameter to hold the command prompt until the job is resumed.
PS C:\> Resume-Job -Name "Job8" -Wait
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command

--     ----            -------------   -----         -----------     --------             -------

8      Job8            PSWorkflowJob   Running       True            Server01             Test-Suspend

This command uses the **Receive-Job** cmdlet to get the results of the Test-Suspend workflow. The final command in the workflow returns a **TimeSpan** object that represents the elapsed time between the current date and time and the date and time that was saved in the $a variable before the workflow was suspended.
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

<span data-ttu-id="f608e-147">Med cmdleten **Resume-Job** kan du återuppta ett arbets flödes jobb som pausas med hjälp av aktiviteten **pausa-Workflow** .</span><span class="sxs-lookup"><span data-stu-id="f608e-147">The **Resume-Job** cmdlet lets you resume a workflow job that was suspend by using the **Suspend-Workflow** activity.</span></span>
<span data-ttu-id="f608e-148">Den här aktiviteten pausar ett arbets flöde i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="f608e-148">This activity suspends a workflow from within a workflow.</span></span>
<span data-ttu-id="f608e-149">Den är endast giltig i arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="f608e-149">It is valid only in workflows.</span></span>

<span data-ttu-id="f608e-150">Information om paus-arbets flödet finns i about_Suspend-Workflow.</span><span class="sxs-lookup"><span data-stu-id="f608e-150">For information about the Suspend-Workflow, see about_Suspend-Workflow.</span></span>

## <span data-ttu-id="f608e-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f608e-151">PARAMETERS</span></span>

### <span data-ttu-id="f608e-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="f608e-152">-Filter</span></span>
<span data-ttu-id="f608e-153">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="f608e-153">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="f608e-154">Den här cmdleten återupptar jobb som uppfyller alla villkor i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="f608e-154">This cmdlet resumes jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="f608e-155">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="f608e-155">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

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

### <span data-ttu-id="f608e-156">-ID</span><span class="sxs-lookup"><span data-stu-id="f608e-156">-Id</span></span>
<span data-ttu-id="f608e-157">Anger en matris med ID: n för jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="f608e-157">Specifies an array of IDs for jobs that this cmdlet resumes.</span></span>

<span data-ttu-id="f608e-158">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f608e-158">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="f608e-159">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f608e-159">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="f608e-160">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="f608e-160">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="f608e-161">Kör **Get-Job** för att hitta ID: t för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="f608e-161">To find the ID of a job, run **Get-Job**.</span></span>

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

### <span data-ttu-id="f608e-162">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f608e-162">-InstanceId</span></span>
<span data-ttu-id="f608e-163">Anger en matris med instans-ID: n för jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="f608e-163">Specifies an array of instance IDs of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="f608e-164">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="f608e-164">The default is all jobs.</span></span>

<span data-ttu-id="f608e-165">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="f608e-165">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="f608e-166">Kör **Get-Job** för att hitta instans-ID för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="f608e-166">To find the instance ID of a job, run **Get-Job**.</span></span>

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

### <span data-ttu-id="f608e-167">– Jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-167">-Job</span></span>
<span data-ttu-id="f608e-168">Anger vilka jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="f608e-168">Specifies the jobs to be resumed.</span></span>
<span data-ttu-id="f608e-169">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="f608e-169">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="f608e-170">Du kan också skicka pipe-jobb till cmdleten **Resume-Job** .</span><span class="sxs-lookup"><span data-stu-id="f608e-170">You can also pipe jobs to the **Resume-Job** cmdlet.</span></span>

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

### <span data-ttu-id="f608e-171">-Name</span><span class="sxs-lookup"><span data-stu-id="f608e-171">-Name</span></span>
<span data-ttu-id="f608e-172">Anger en matris med användarvänliga namn på jobb som denna cmdlet återupptar.</span><span class="sxs-lookup"><span data-stu-id="f608e-172">Specifies an array of friendly names of jobs that this cmdlet resumes.</span></span>
<span data-ttu-id="f608e-173">Ange ett eller flera jobb namn.</span><span class="sxs-lookup"><span data-stu-id="f608e-173">Enter one or more job names.</span></span>
<span data-ttu-id="f608e-174">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f608e-174">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f608e-175">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="f608e-175">-State</span></span>
<span data-ttu-id="f608e-176">Anger tillstånd för jobb som ska återupptas.</span><span class="sxs-lookup"><span data-stu-id="f608e-176">Specifies the state of jobs to resume.</span></span>
<span data-ttu-id="f608e-177">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f608e-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f608e-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f608e-178">NotStarted</span></span>
- <span data-ttu-id="f608e-179">Körs</span><span class="sxs-lookup"><span data-stu-id="f608e-179">Running</span></span>
- <span data-ttu-id="f608e-180">Slutförd</span><span class="sxs-lookup"><span data-stu-id="f608e-180">Completed</span></span>
- <span data-ttu-id="f608e-181">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="f608e-181">Failed</span></span>
- <span data-ttu-id="f608e-182">Stoppad</span><span class="sxs-lookup"><span data-stu-id="f608e-182">Stopped</span></span>
- <span data-ttu-id="f608e-183">Blockerad</span><span class="sxs-lookup"><span data-stu-id="f608e-183">Blocked</span></span>
- <span data-ttu-id="f608e-184">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="f608e-184">Suspended</span></span>
- <span data-ttu-id="f608e-185">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="f608e-185">Disconnected</span></span>
- <span data-ttu-id="f608e-186">Pausar</span><span class="sxs-lookup"><span data-stu-id="f608e-186">Suspending</span></span>
- <span data-ttu-id="f608e-187">Stoppas</span><span class="sxs-lookup"><span data-stu-id="f608e-187">Stopping</span></span>

<span data-ttu-id="f608e-188">Denna cmdlet återupptar bara jobb i tillståndet **Suspended** .</span><span class="sxs-lookup"><span data-stu-id="f608e-188">This cmdlet resumes only jobs in the **Suspended** state.</span></span>

<span data-ttu-id="f608e-189">Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="f608e-189">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="f608e-190">– Vänta</span><span class="sxs-lookup"><span data-stu-id="f608e-190">-Wait</span></span>
<span data-ttu-id="f608e-191">Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat har startats om.</span><span class="sxs-lookup"><span data-stu-id="f608e-191">Indicates that this cmdlet suppresses the command prompt until all job results are restarted.</span></span>
<span data-ttu-id="f608e-192">Som standard returnerar denna cmdlet omedelbart de tillgängliga resultaten.</span><span class="sxs-lookup"><span data-stu-id="f608e-192">By default, this cmdlet immediately returns the available results.</span></span>

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

### <span data-ttu-id="f608e-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f608e-193">-Confirm</span></span>
<span data-ttu-id="f608e-194">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f608e-194">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f608e-195">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f608e-195">-WhatIf</span></span>
<span data-ttu-id="f608e-196">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f608e-196">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f608e-197">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f608e-197">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f608e-198">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f608e-198">CommonParameters</span></span>
<span data-ttu-id="f608e-199">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f608e-199">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f608e-200">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f608e-200">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f608e-201">INDATA</span><span class="sxs-lookup"><span data-stu-id="f608e-201">INPUTS</span></span>

### <span data-ttu-id="f608e-202">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="f608e-202">System.Management.Automation.Job</span></span>
<span data-ttu-id="f608e-203">Du kan skicka vidare alla typer av jobb till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f608e-203">You can pipe all types of jobs to this cmdlet.</span></span>
<span data-ttu-id="f608e-204">Om **Resume-Job** får ett jobb av en typ som inte stöds returneras ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="f608e-204">If **Resume-Job** gets a job of an unsupported type, it returns a terminating error.</span></span>

## <span data-ttu-id="f608e-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f608e-205">OUTPUTS</span></span>

### <span data-ttu-id="f608e-206">Ingen, system. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="f608e-206">None, System.Management.Automation.Job</span></span>
<span data-ttu-id="f608e-207">Den här cmdleten returnerar de jobb som det försöker återuppta, om du använder parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="f608e-207">This cmdlet returns the jobs that it tries to resume, if you use the *PassThru* parameter.</span></span>
<span data-ttu-id="f608e-208">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f608e-208">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f608e-209">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f608e-209">NOTES</span></span>

* <span data-ttu-id="f608e-210">**Resume-Job** kan bara återuppta jobb som har pausats.</span><span class="sxs-lookup"><span data-stu-id="f608e-210">**Resume-Job** can only resume jobs that are suspended.</span></span> <span data-ttu-id="f608e-211">Om du skickar ett jobb till ett annat tillstånd kör **Resume-Job** åtgärden Resume på jobbet, men genererar en varning för att meddela dig om att det inte gick att återuppta jobbet.</span><span class="sxs-lookup"><span data-stu-id="f608e-211">If you submit a job in a different state, **Resume-Job** runs the resume operation on the job, but generates a warning to notify you that the job could not be resumed.</span></span> <span data-ttu-id="f608e-212">Om du vill utelämna varningen använder du den gemensamma parametern *WarningAction* med värdet SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="f608e-212">To suppress the warning, use the *WarningAction* common parameter with a value of SilentlyContinue.</span></span>
* <span data-ttu-id="f608e-213">Om ett jobb inte är av en typ som har stöd för att återuppta, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), **Resume-Job** , returneras ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="f608e-213">If a job is not of a type that supports resuming, such as a workflow job ( **PSWorkflowJob** ), **Resume-Job** returns a terminating error.</span></span>
* <span data-ttu-id="f608e-214">Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen.</span><span class="sxs-lookup"><span data-stu-id="f608e-214">The mechanism and location for saving a suspended job might vary depending on the job type.</span></span> <span data-ttu-id="f608e-215">Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en SQL-databas.</span><span class="sxs-lookup"><span data-stu-id="f608e-215">For example, suspended workflow jobs are saved in a flat file store by default, but can also be saved in a SQL database.</span></span>
* <span data-ttu-id="f608e-216">När du återupptar ett jobb ändras jobb tillståndet från **pausat** till att **köras**.</span><span class="sxs-lookup"><span data-stu-id="f608e-216">When you resume a job, the job state changes from **Suspended** to **Running**.</span></span> <span data-ttu-id="f608e-217">Om du vill hitta jobb som kör, inklusive de som har återupptagits av denna cmdlet, använder du parametern *State* för cmdleten **Get-Job** för att hämta jobb i **körnings** tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f608e-217">To find the jobs that are running, including those that were resumed by this cmdlet, use the *State* parameter of the **Get-Job** cmdlet to get jobs in the **Running** state.</span></span>
* <span data-ttu-id="f608e-218">Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet.</span><span class="sxs-lookup"><span data-stu-id="f608e-218">Some job types have options or properties that prevent Windows PowerShell from suspending the job.</span></span> <span data-ttu-id="f608e-219">Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.</span><span class="sxs-lookup"><span data-stu-id="f608e-219">If attempts to suspend the job fail, verify that the job options and properties allow for suspending.</span></span>

## <span data-ttu-id="f608e-220">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f608e-220">RELATED LINKS</span></span>

[<span data-ttu-id="f608e-221">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-221">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f608e-222">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-222">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f608e-223">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-223">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f608e-224">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-224">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f608e-225">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-225">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="f608e-226">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="f608e-226">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="f608e-227">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f608e-227">Wait-Job</span></span>](Wait-Job.md)
