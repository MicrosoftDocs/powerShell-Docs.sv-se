---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263613"
---
# <span data-ttu-id="c1105-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="c1105-103">Get-Job</span></span>

## <span data-ttu-id="c1105-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c1105-104">SYNOPSIS</span></span>
<span data-ttu-id="c1105-105">Hämtar PowerShell-bakgrunds jobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="c1105-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c1105-106">SYNTAX</span></span>

### <span data-ttu-id="c1105-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="c1105-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="c1105-108">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="c1105-108">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="c1105-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="c1105-109">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="c1105-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="c1105-110">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c1105-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="c1105-111">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="c1105-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="c1105-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="c1105-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c1105-113">DESCRIPTION</span></span>

<span data-ttu-id="c1105-114">Cmdleten **Get-Job** hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span>
<span data-ttu-id="c1105-115">Du kan använda **Get-Job** för att hämta jobb som har startats med hjälp av Start-Job-cmdlet, eller genom att använda parametern *AsJob* för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1105-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="c1105-116">Utan parametrar hämtar kommandot **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="c1105-117">Du kan använda parametrarna för **Get-Job** för att hämta specifika jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="c1105-118">Jobbobjektet som returnerar jobb innehåller användbar information **om jobbet,** men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="c1105-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span>
<span data-ttu-id="c1105-119">Använd Receive-Job-cmdleten för att hämta resultatet.</span><span class="sxs-lookup"><span data-stu-id="c1105-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="c1105-120">Ett Windows PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span>
<span data-ttu-id="c1105-121">Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="c1105-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span>
<span data-ttu-id="c1105-122">Mer information om bakgrunds jobb i Windows PowerShell finns about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="c1105-122">For more information about background jobs in Windows PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="c1105-123">Från och med Windows PowerShell 3,0 hämtar cmdleten **Get-Job** även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="c1105-124">Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .</span><span class="sxs-lookup"><span data-stu-id="c1105-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="c1105-125">Om du vill aktivera **Get-Job** för att hämta en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör kommandot **Get-Job** , antingen genom att använda Import-Module cmdlet eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="c1105-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="c1105-126">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="c1105-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c1105-127">EXAMPLES</span></span>

### <span data-ttu-id="c1105-128">Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="c1105-128">Example 1: Get all background jobs started in the current session</span></span>

```
PS C:\> Get-Job
```

<span data-ttu-id="c1105-129">Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="c1105-130">Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c1105-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="c1105-131">Exempel 2: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="c1105-131">Example 2: Stop a job by using an instance ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

<span data-ttu-id="c1105-132">De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="c1105-133">Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.</span><span class="sxs-lookup"><span data-stu-id="c1105-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

### <span data-ttu-id="c1105-134">Exempel 3: Hämta jobb som innehåller ett speciellt kommando</span><span class="sxs-lookup"><span data-stu-id="c1105-134">Example 3: Get jobs that include a specific command</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

<span data-ttu-id="c1105-135">Det här kommandot hämtar jobben på systemet som innehåller ett Get-Process-kommando.</span><span class="sxs-lookup"><span data-stu-id="c1105-135">This command gets the jobs on the system that include a Get-Process command.</span></span>
<span data-ttu-id="c1105-136">Kommandot använder *kommando* parametern för **Get-Job** för att begränsa de jobb som hämtas.</span><span class="sxs-lookup"><span data-stu-id="c1105-136">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span>
<span data-ttu-id="c1105-137">Kommandot använder jokertecken (\*) för att hämta jobb som innehåller kommandot **Get-process** var som helst i kommando strängen.</span><span class="sxs-lookup"><span data-stu-id="c1105-137">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="c1105-138">Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="c1105-138">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

<span data-ttu-id="c1105-139">Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller kommandot **Get-process** .</span><span class="sxs-lookup"><span data-stu-id="c1105-139">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span>
<span data-ttu-id="c1105-140">Kommandot använder en pipeline-operator (|) för att skicka en sträng, inom citat tecken, till cmdleten **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="c1105-140">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span>
<span data-ttu-id="c1105-141">Det motsvarar föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="c1105-141">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="c1105-142">Exempel 5: Hämta jobb som inte har startats</span><span class="sxs-lookup"><span data-stu-id="c1105-142">Example 5: Get jobs that have not been started</span></span>

```
PS C:\> Get-Job -State NotStarted
```

<span data-ttu-id="c1105-143">Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats.</span><span class="sxs-lookup"><span data-stu-id="c1105-143">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="c1105-144">Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.</span><span class="sxs-lookup"><span data-stu-id="c1105-144">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="c1105-145">Exempel 6: Hämta jobb som inte har tilldelats ett namn</span><span class="sxs-lookup"><span data-stu-id="c1105-145">Example 6: Get jobs that have not been assigned a name</span></span>

```
PS C:\> Get-Job -Name Job*
```

<span data-ttu-id="c1105-146">Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet.</span><span class="sxs-lookup"><span data-stu-id="c1105-146">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="c1105-147">Eftersom jobbet \<number\> är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.</span><span class="sxs-lookup"><span data-stu-id="c1105-147">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="c1105-148">Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando</span><span class="sxs-lookup"><span data-stu-id="c1105-148">Example 7: Use a job object to represent the job in a command</span></span>

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="c1105-149">Det här exemplet visar hur du använder **Get-Job** för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="c1105-149">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

### <span data-ttu-id="c1105-150">Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod</span><span class="sxs-lookup"><span data-stu-id="c1105-150">Example 8: Get all jobs including jobs started by a different method</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="c1105-151">Det här exemplet visar att cmdleten **Get-Job** kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.</span><span class="sxs-lookup"><span data-stu-id="c1105-151">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

### <span data-ttu-id="c1105-152">Exempel 9: Undersök ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-152">Example 9: Investigate a failed job</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

<span data-ttu-id="c1105-153">Det här kommandot visar hur du använder jobbobjektet som **Get-Job-** returer för att undersöka varför ett jobb har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="c1105-153">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="c1105-154">Det visar också hur du hämtar de underordnade jobben för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-154">It also shows how to get the child jobs of each job.</span></span>

### <span data-ttu-id="c1105-155">Exempel 10: hämta filtrerade resultat</span><span class="sxs-lookup"><span data-stu-id="c1105-155">Example 10: Get filtered results</span></span>

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="c1105-156">Det här exemplet visar hur du använder *filter* parametern för att hämta ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-156">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="c1105-157">*Filter* parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-157">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

### <span data-ttu-id="c1105-158">Exempel 11: Hämta information om underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-158">Example 11: Get information about child jobs</span></span>

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="c1105-159">I det här exemplet visas effekterna av att använda parametrarna *IncludeChildJob* och *ChildJobState* för **Get-Job-** cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c1105-159">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

## <span data-ttu-id="c1105-160">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c1105-160">PARAMETERS</span></span>

### <span data-ttu-id="c1105-161">– Efter</span><span class="sxs-lookup"><span data-stu-id="c1105-161">-After</span></span>

<span data-ttu-id="c1105-162">Hämtar slutförda jobb som avslutas efter angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="c1105-162">Gets completed jobs that ended after the specified date and time.</span></span>
<span data-ttu-id="c1105-163">Ange ett **datetime** -objekt, till exempel ett som returneras av Get-Date-cmdlet eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .</span><span class="sxs-lookup"><span data-stu-id="c1105-163">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="c1105-164">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="c1105-164">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="c1105-165">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c1105-165">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c1105-166">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="c1105-166">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c1105-167">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-167">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-168">– Före</span><span class="sxs-lookup"><span data-stu-id="c1105-168">-Before</span></span>

<span data-ttu-id="c1105-169">Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden.</span><span class="sxs-lookup"><span data-stu-id="c1105-169">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="c1105-170">Ange ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c1105-170">Enter a **DateTime** object.</span></span>

<span data-ttu-id="c1105-171">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="c1105-171">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="c1105-172">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c1105-172">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c1105-173">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="c1105-173">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c1105-174">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-175">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="c1105-175">-ChildJobState</span></span>

<span data-ttu-id="c1105-176">Hämtar endast de underordnade jobb som har det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="c1105-176">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="c1105-177">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c1105-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c1105-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="c1105-178">NotStarted</span></span>
- <span data-ttu-id="c1105-179">Körs</span><span class="sxs-lookup"><span data-stu-id="c1105-179">Running</span></span>
- <span data-ttu-id="c1105-180">Slutförd</span><span class="sxs-lookup"><span data-stu-id="c1105-180">Completed</span></span>
- <span data-ttu-id="c1105-181">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="c1105-181">Failed</span></span>
- <span data-ttu-id="c1105-182">Stoppad</span><span class="sxs-lookup"><span data-stu-id="c1105-182">Stopped</span></span>
- <span data-ttu-id="c1105-183">Blockerad</span><span class="sxs-lookup"><span data-stu-id="c1105-183">Blocked</span></span>
- <span data-ttu-id="c1105-184">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="c1105-184">Suspended</span></span>
- <span data-ttu-id="c1105-185">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="c1105-185">Disconnected</span></span>
- <span data-ttu-id="c1105-186">Pausar</span><span class="sxs-lookup"><span data-stu-id="c1105-186">Suspending</span></span>
- <span data-ttu-id="c1105-187">Stoppas</span><span class="sxs-lookup"><span data-stu-id="c1105-187">Stopping</span></span>

<span data-ttu-id="c1105-188">Som standard får **Get-Job** inte underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-188">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="c1105-189">Genom att använda *IncludeChildJob* -parametern hämtar **Get-Job** alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-189">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="c1105-190">Om du använder parametern *ChildJobState* har parametern *IncludeChildJob* ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="c1105-190">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="c1105-191">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-192">-Kommando</span><span class="sxs-lookup"><span data-stu-id="c1105-192">-Command</span></span>

<span data-ttu-id="c1105-193">Anger en matris med kommandon som strängar.</span><span class="sxs-lookup"><span data-stu-id="c1105-193">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="c1105-194">Denna cmdlet hämtar de jobb som innehåller de angivna kommandona.</span><span class="sxs-lookup"><span data-stu-id="c1105-194">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="c1105-195">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-195">The default is all jobs.</span></span>
<span data-ttu-id="c1105-196">Du kan använda jokertecken för att ange ett kommando mönster.</span><span class="sxs-lookup"><span data-stu-id="c1105-196">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c1105-197">-Filter</span><span class="sxs-lookup"><span data-stu-id="c1105-197">-Filter</span></span>

<span data-ttu-id="c1105-198">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="c1105-198">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="c1105-199">Denna cmdlet hämtar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="c1105-199">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="c1105-200">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c1105-200">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="c1105-201">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-201">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="c1105-202">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="c1105-202">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="c1105-203">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="c1105-203">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="c1105-204">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c1105-205">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="c1105-205">-HasMoreData</span></span>

<span data-ttu-id="c1105-206">Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="c1105-206">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="c1105-207">Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-207">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="c1105-208">Ange ett värde för $True för att hämta jobb som har fler resultat.</span><span class="sxs-lookup"><span data-stu-id="c1105-208">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="c1105-209">Ange ett värde för $False om du vill hämta jobb som inte har fler resultat.</span><span class="sxs-lookup"><span data-stu-id="c1105-209">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="c1105-210">Om du vill hämta resultatet av ett jobb använder du cmdleten Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="c1105-210">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="c1105-211">När du använder cmdleten **Receive-Job** , tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras.</span><span class="sxs-lookup"><span data-stu-id="c1105-211">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span>
<span data-ttu-id="c1105-212">När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till $false) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-212">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span>
<span data-ttu-id="c1105-213">Använd parametern *Behåll* för **Receive-Job** för att förhindra **mottagning – jobb** från att ta bort resultat och ändra värdet för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="c1105-213">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="c1105-214">För mer information ange `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="c1105-214">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="c1105-215">Egenskapen **HasMoreData** är unik för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-215">The **HasMoreData** property is specific to the current session.</span></span>
<span data-ttu-id="c1105-216">Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda cmdleten **Receive-Job** i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är $false.</span><span class="sxs-lookup"><span data-stu-id="c1105-216">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span>
<span data-ttu-id="c1105-217">Mer information finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="c1105-217">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="c1105-218">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-218">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-219">-ID</span><span class="sxs-lookup"><span data-stu-id="c1105-219">-Id</span></span>

<span data-ttu-id="c1105-220">Anger en matris med ID: n för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="c1105-220">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="c1105-221">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-221">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="c1105-222">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-222">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="c1105-223">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="c1105-223">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="c1105-224">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="c1105-224">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-225">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="c1105-225">-IncludeChildJob</span></span>

<span data-ttu-id="c1105-226">Anger att den här cmdleten Returnerar underordnade jobb, förutom överordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-226">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="c1105-227">Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, för vilka **Get-Job** returnerar ett överordnat behållar jobb och jobb haverier, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.</span><span class="sxs-lookup"><span data-stu-id="c1105-227">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="c1105-228">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-229">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="c1105-229">-InstanceId</span></span>

<span data-ttu-id="c1105-230">Anger en matris med instans-ID för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="c1105-230">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="c1105-231">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-231">The default is all jobs.</span></span>

<span data-ttu-id="c1105-232">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="c1105-232">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="c1105-233">Använd **Get-Job** för att hitta instans-ID för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="c1105-233">To find the instance ID of a job, use **Get-Job**.</span></span>

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

### <span data-ttu-id="c1105-234">-Name</span><span class="sxs-lookup"><span data-stu-id="c1105-234">-Name</span></span>

<span data-ttu-id="c1105-235">Anger en matris med informativa namn på jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="c1105-235">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="c1105-236">Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="c1105-236">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="c1105-237">Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-237">By default, **Get-Job** gets all jobs in the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="c1105-238">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="c1105-238">-Newest</span></span>

<span data-ttu-id="c1105-239">Anger ett antal jobb som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="c1105-239">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="c1105-240">Denna cmdlet hämtar de jobb som avslutades senast.</span><span class="sxs-lookup"><span data-stu-id="c1105-240">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="c1105-241">Den *senaste* parametern kan inte sortera eller returnera de senaste jobben i slut tid.</span><span class="sxs-lookup"><span data-stu-id="c1105-241">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="c1105-242">Om du vill sortera utdata använder du Sort-Object cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1105-242">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="c1105-243">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c1105-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c1105-244">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="c1105-244">-State</span></span>

<span data-ttu-id="c1105-245">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="c1105-245">Specifies a job state.</span></span>
<span data-ttu-id="c1105-246">Denna cmdlet hämtar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="c1105-246">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="c1105-247">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c1105-247">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c1105-248">NotStarted</span><span class="sxs-lookup"><span data-stu-id="c1105-248">NotStarted</span></span>
- <span data-ttu-id="c1105-249">Körs</span><span class="sxs-lookup"><span data-stu-id="c1105-249">Running</span></span>
- <span data-ttu-id="c1105-250">Slutförd</span><span class="sxs-lookup"><span data-stu-id="c1105-250">Completed</span></span>
- <span data-ttu-id="c1105-251">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="c1105-251">Failed</span></span>
- <span data-ttu-id="c1105-252">Stoppad</span><span class="sxs-lookup"><span data-stu-id="c1105-252">Stopped</span></span>
- <span data-ttu-id="c1105-253">Blockerad</span><span class="sxs-lookup"><span data-stu-id="c1105-253">Blocked</span></span>
- <span data-ttu-id="c1105-254">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="c1105-254">Suspended</span></span>
- <span data-ttu-id="c1105-255">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="c1105-255">Disconnected</span></span>
- <span data-ttu-id="c1105-256">Pausar</span><span class="sxs-lookup"><span data-stu-id="c1105-256">Suspending</span></span>
- <span data-ttu-id="c1105-257">Stoppas</span><span class="sxs-lookup"><span data-stu-id="c1105-257">Stopping</span></span>

<span data-ttu-id="c1105-258">Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-258">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="c1105-259">Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="c1105-259">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="c1105-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c1105-260">CommonParameters</span></span>

<span data-ttu-id="c1105-261">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c1105-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c1105-262">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c1105-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c1105-263">INDATA</span><span class="sxs-lookup"><span data-stu-id="c1105-263">INPUTS</span></span>

### <span data-ttu-id="c1105-264">Inget</span><span class="sxs-lookup"><span data-stu-id="c1105-264">None</span></span>

<span data-ttu-id="c1105-265">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c1105-265">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c1105-266">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c1105-266">OUTPUTS</span></span>

### <span data-ttu-id="c1105-267">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="c1105-267">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="c1105-268">Denna cmdlet returnerar objekt som representerar jobben i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c1105-268">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="c1105-269">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c1105-269">NOTES</span></span>

* <span data-ttu-id="c1105-270">**PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="c1105-270">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="c1105-271">Egenskap svärdet bestäms av jobb typ författaren.</span><span class="sxs-lookup"><span data-stu-id="c1105-271">The property value is determined by the job type author.</span></span> <span data-ttu-id="c1105-272">I följande lista visas vanliga jobb typer.</span><span class="sxs-lookup"><span data-stu-id="c1105-272">The following list shows common job types.</span></span>

  - <span data-ttu-id="c1105-273">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="c1105-273">**BackgroundJob**.</span></span>
<span data-ttu-id="c1105-274">Ett lokalt jobb har startats med hjälp av **Start-Job**.</span><span class="sxs-lookup"><span data-stu-id="c1105-274">Local job started by using **Start-Job**.</span></span>

  - <span data-ttu-id="c1105-275">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="c1105-275">**RemoteJob**.</span></span>
<span data-ttu-id="c1105-276">Jobbet startades i en **PSSession** med hjälp av parametern *AsJob* i Invoke-Command-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c1105-276">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="c1105-277">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="c1105-277">**PSWorkflowJob**.</span></span>
<span data-ttu-id="c1105-278">Jobbet startades med *AsJob* gemensamma parameter för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="c1105-278">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="c1105-279">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c1105-279">RELATED LINKS</span></span>

[<span data-ttu-id="c1105-280">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="c1105-280">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="c1105-281">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-281">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="c1105-282">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-282">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="c1105-283">Återuppta – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-283">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="c1105-284">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-284">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="c1105-285">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-285">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="c1105-286">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="c1105-286">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="c1105-287">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="c1105-287">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="c1105-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="c1105-288">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="c1105-289">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="c1105-289">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="c1105-290">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="c1105-290">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="c1105-291">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="c1105-291">about_Scheduled_Jobs</span></span>](../PSScheduledJob/About/about_Scheduled_Jobs.md)
