---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 76644dbf15d2bdabd7a365f4bd5910a50502e17d
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263091"
---
# <span data-ttu-id="9133b-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="9133b-103">Get-Job</span></span>

## <span data-ttu-id="9133b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9133b-104">SYNOPSIS</span></span>
<span data-ttu-id="9133b-105">Hämtar PowerShell-bakgrunds jobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="9133b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9133b-106">SYNTAX</span></span>

### <span data-ttu-id="9133b-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="9133b-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="9133b-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="9133b-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="9133b-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="9133b-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="9133b-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="9133b-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="9133b-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="9133b-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="9133b-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="9133b-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="9133b-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9133b-113">DESCRIPTION</span></span>

<span data-ttu-id="9133b-114">Cmdleten **Get-Job** hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="9133b-115">Du kan använda **Get-Job** för att hämta jobb som har startats med hjälp av Start-Job-cmdlet, eller genom att använda parametern *AsJob* för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9133b-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="9133b-116">Utan parametrar hämtar kommandot **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="9133b-117">Du kan använda parametrarna för **Get-Job** för att hämta specifika jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="9133b-118">Jobbobjektet som returnerar jobb innehåller användbar information **om jobbet,** men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="9133b-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="9133b-119">Använd Receive-Job-cmdleten för att hämta resultatet.</span><span class="sxs-lookup"><span data-stu-id="9133b-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="9133b-120">Ett PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-120">A PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="9133b-121">Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="9133b-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="9133b-122">Mer information om bakgrunds jobb i PowerShell finns about_Jobs.</span><span class="sxs-lookup"><span data-stu-id="9133b-122">For more information about background jobs in PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="9133b-123">Från och med Windows PowerShell 3,0 hämtar cmdleten **Get-Job** även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="9133b-124">Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .</span><span class="sxs-lookup"><span data-stu-id="9133b-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="9133b-125">Om du vill aktivera **Get-Job** för att hämta en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör kommandot **Get-Job** , antingen genom att använda Import-Module cmdlet eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="9133b-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="9133b-126">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="9133b-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9133b-127">EXAMPLES</span></span>

### <span data-ttu-id="9133b-128">Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="9133b-128">Example 1: Get all background jobs started in the current session</span></span>

```powershell
Get-Job
```

<span data-ttu-id="9133b-129">Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="9133b-130">Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="9133b-131">Exempel 2: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="9133b-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="9133b-132">De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="9133b-133">Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.</span><span class="sxs-lookup"><span data-stu-id="9133b-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

<span data-ttu-id="9133b-134">Det första kommandot använder cmdleten **Get-Job** för att hämta ett jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-134">The first command uses the **Get-Job** cmdlet to get a job.</span></span> <span data-ttu-id="9133b-135">Parametern *Name* används för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-135">It uses the *Name* parameter to identify the job.</span></span> <span data-ttu-id="9133b-136">Kommandot lagrar jobbobjektet som **Get-Job** returnerar i $j-variabeln.</span><span class="sxs-lookup"><span data-stu-id="9133b-136">The command stores the job object that **Get-Job** returns in the $j variable.</span></span> <span data-ttu-id="9133b-137">I det här exemplet finns det bara ett jobb med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="9133b-137">In this example, there is only one job with the specified name.</span></span>

<span data-ttu-id="9133b-138">Det andra kommandot hämtar egenskapen **InstanceID** för objektet i variabeln $j och lagrar det i variabeln $ID.</span><span class="sxs-lookup"><span data-stu-id="9133b-138">The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.</span></span>

<span data-ttu-id="9133b-139">Det tredje kommandot visar värdet för variabeln $ID.</span><span class="sxs-lookup"><span data-stu-id="9133b-139">The third command displays the value of the $ID variable.</span></span>

<span data-ttu-id="9133b-140">Det fjärde kommandot använder Stop-Job cmdlet för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-140">The fourth command uses Stop-Job cmdlet to stop the job.</span></span> <span data-ttu-id="9133b-141">Parametern *InstanceID* används för att identifiera jobb-och $ID-variabeln som representerar jobbets instans-ID.</span><span class="sxs-lookup"><span data-stu-id="9133b-141">It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.</span></span>

### <span data-ttu-id="9133b-142">Exempel 3: Hämta jobb som innehåller ett speciellt kommando</span><span class="sxs-lookup"><span data-stu-id="9133b-142">Example 3: Get jobs that include a specific command</span></span>

```powershell
Get-Job -Command "*get-process*"
```

<span data-ttu-id="9133b-143">Det här kommandot hämtar jobben på systemet som innehåller ett Get-Process-kommando.</span><span class="sxs-lookup"><span data-stu-id="9133b-143">This command gets the jobs on the system that include a Get-Process command.</span></span> <span data-ttu-id="9133b-144">Kommandot använder *kommando* parametern för **Get-Job** för att begränsa de jobb som hämtas.</span><span class="sxs-lookup"><span data-stu-id="9133b-144">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span> <span data-ttu-id="9133b-145">Kommandot använder jokertecken (\*) för att hämta jobb som innehåller kommandot **Get-process** var som helst i kommando strängen.</span><span class="sxs-lookup"><span data-stu-id="9133b-145">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="9133b-146">Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="9133b-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```powershell
"*get-process*" | Get-Job
```

<span data-ttu-id="9133b-147">Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller kommandot **Get-process** .</span><span class="sxs-lookup"><span data-stu-id="9133b-147">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span> <span data-ttu-id="9133b-148">Kommandot använder en pipeline-operator (|) för att skicka en sträng, inom citat tecken, till cmdleten **Get-Job** .</span><span class="sxs-lookup"><span data-stu-id="9133b-148">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span> <span data-ttu-id="9133b-149">Det motsvarar föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="9133b-149">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="9133b-150">Exempel 5: Hämta jobb som inte har startats</span><span class="sxs-lookup"><span data-stu-id="9133b-150">Example 5: Get jobs that have not been started</span></span>

```powershell
Get-Job -State NotStarted
```

<span data-ttu-id="9133b-151">Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats.</span><span class="sxs-lookup"><span data-stu-id="9133b-151">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="9133b-152">Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.</span><span class="sxs-lookup"><span data-stu-id="9133b-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="9133b-153">Exempel 6: Hämta jobb som inte har tilldelats ett namn</span><span class="sxs-lookup"><span data-stu-id="9133b-153">Example 6: Get jobs that have not been assigned a name</span></span>

```powershell
Get-Job -Name Job*
```

<span data-ttu-id="9133b-154">Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-154">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="9133b-155">Eftersom jobbet \<number\> är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.</span><span class="sxs-lookup"><span data-stu-id="9133b-155">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="9133b-156">Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando</span><span class="sxs-lookup"><span data-stu-id="9133b-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="9133b-157">Det här exemplet visar hur du använder **Get-Job** för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="9133b-157">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="9133b-158">Det första kommandot använder cmdleten **Start-Job** för att starta ett bakgrunds jobb som kör kommandot **Get-process** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-158">The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer.</span></span> <span data-ttu-id="9133b-159">Kommandot använder *Name* -parametern för **Start-Job** för att tilldela ett eget namn till jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-159">The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.</span></span>

<span data-ttu-id="9133b-160">Det andra kommandot använder Get-Job för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-160">The second command uses Get-Job to get the job.</span></span> <span data-ttu-id="9133b-161">Den använder *namn* parametern för **Get-Job** för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-161">It uses the *Name* parameter of **Get-Job** to identify the job.</span></span> <span data-ttu-id="9133b-162">Kommandot sparar det resulterande jobbobjektet i $j variabeln.</span><span class="sxs-lookup"><span data-stu-id="9133b-162">The command saves the resulting job object in the $j variable.</span></span>

<span data-ttu-id="9133b-163">Det tredje kommandot visar värdet för jobbobjektet i variabeln $j.</span><span class="sxs-lookup"><span data-stu-id="9133b-163">The third command displays the value of the job object in the $j variable.</span></span> <span data-ttu-id="9133b-164">Värdet för egenskapen **State** visar att jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="9133b-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="9133b-165">Värdet för egenskapen **HasMoreData** visar att det finns resultat som är tillgängliga från jobbet som ännu inte har hämtats.</span><span class="sxs-lookup"><span data-stu-id="9133b-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span>

<span data-ttu-id="9133b-166">Det fjärde kommandot använder cmdleten **Receive-Job** för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-166">The fourth command uses the **Receive-Job** cmdlet to get the results of the job.</span></span> <span data-ttu-id="9133b-167">Objektet används i $j-variabeln för att representera jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-167">It uses the job object in the $j variable to represent the job.</span></span> <span data-ttu-id="9133b-168">Du kan också använda en pipeline-operator för att skicka ett jobb objekt till **Receive-Job**.</span><span class="sxs-lookup"><span data-stu-id="9133b-168">You can also use a pipeline operator to send a job object to **Receive-Job**.</span></span>

### <span data-ttu-id="9133b-169">Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod</span><span class="sxs-lookup"><span data-stu-id="9133b-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="9133b-170">Det här exemplet visar att cmdleten **Get-Job** kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.</span><span class="sxs-lookup"><span data-stu-id="9133b-170">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="9133b-171">Det första kommandot använder cmdleten **Start-Job** för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-171">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span>

<span data-ttu-id="9133b-172">Det andra kommandot använder parametern *AsJob* i cmdleten **Invoke-Command** för att starta ett jobb på S1-datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-172">The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="9133b-173">Även om kommandona i jobbet körs på fjärrdatorn skapas jobbobjektet på den lokala datorn, så du kan använda lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span>

<span data-ttu-id="9133b-174">Det tredje kommandot använder cmdleten **Invoke-Command** för att köra ett **Start jobb** kommando på S2-datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-174">The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer.</span></span> <span data-ttu-id="9133b-175">Med den här metoden skapas jobbobjektet på fjärrdatorn, så du kan använda fjärrkommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span>

<span data-ttu-id="9133b-176">Det fjärde kommandot använder **Get-Job** för att hämta jobben som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-176">The fourth command uses **Get-Job** to get the jobs stored on the local computer.</span></span> <span data-ttu-id="9133b-177">Egenskapen **PSJobTypeName** för jobb, som introducerades i Windows PowerShell 3,0, visar att det lokala jobbet som startades med hjälp av cmdleten **Start-Job** är ett bakgrunds jobb och att jobbet startade i en fjärrsession med hjälp av cmdleten **Invoke-Command** är ett Fjärrjobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.</span></span>

<span data-ttu-id="9133b-178">Det femte kommandot använder **Invoke-Command** för att köra ett **Get-Job-** kommando på datorn S2. Exempel resultatet visar resultatet av kommandot Get-Job.</span><span class="sxs-lookup"><span data-stu-id="9133b-178">The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command.</span></span> <span data-ttu-id="9133b-179">På S2-datorn verkar jobbet vara ett lokalt jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="9133b-180">Dator namnet är localhost och jobb typen är ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-180">The computer name is localhost and the job type is a background job.</span></span>

<span data-ttu-id="9133b-181">Mer information om hur du kör bakgrunds jobb på fjärrdatorer finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="9133b-181">For more information about how to run background jobs on remote computers, see about_Remote_Jobs.</span></span>

### <span data-ttu-id="9133b-182">Exempel 9: Undersök ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-182">Example 9: Investigate a failed job</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
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
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

<span data-ttu-id="9133b-183">Det här kommandot visar hur du använder jobbobjektet som **Get-Job-** returer för att undersöka varför ett jobb har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="9133b-183">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="9133b-184">Det visar också hur du hämtar de underordnade jobben för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-184">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="9133b-185">Det första kommandot använder cmdleten **Start-Job** för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-185">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="9133b-186">Jobbobjektet som **startar jobb** returnerar visar att jobbet misslyckades.</span><span class="sxs-lookup"><span data-stu-id="9133b-186">The job object that **Start-Job** returns shows that the job failed.</span></span> <span data-ttu-id="9133b-187">Det gick inte att **Ange värdet för tillstånds** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9133b-187">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="9133b-188">Det andra kommandot använder cmdleten **Get-Job** för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-188">The second command uses the **Get-Job** cmdlet to get the job.</span></span> <span data-ttu-id="9133b-189">Kommandot använder punkt metoden för att hämta värdet för objektets **JobStateInfo** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="9133b-189">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="9133b-190">Den använder en pipeline-operator för att skicka objektet i egenskapen **JobStateInfo** till Format-List-cmdlet, som formaterar alla egenskaper för objektet (\*) i en lista. Resultatet av kommandot **format-List** visar att värdet för jobbets **orsaks** egenskap är tomt.</span><span class="sxs-lookup"><span data-stu-id="9133b-190">It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (\*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="9133b-191">Det tredje kommandot undersöker mer.</span><span class="sxs-lookup"><span data-stu-id="9133b-191">The third command investigates more.</span></span> <span data-ttu-id="9133b-192">Det använder kommandot **Get-Job** för att hämta jobbet och använder sedan en pipeline-operator för att skicka hela jobbobjektet till cmdleten **format-List** , som visar alla egenskaper för jobbet i en lista. Visningen av alla egenskaper i jobbobjektet visar att jobbet innehåller ett underordnat jobb med namnet Job2.</span><span class="sxs-lookup"><span data-stu-id="9133b-192">It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="9133b-193">Det fjärde kommandot använder **Get-Job** för att hämta jobbobjektet som representerar det underordnade Job2-jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-193">The fourth command uses **Get-Job** to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="9133b-194">Det här är det jobb där kommandot faktiskt kördes.</span><span class="sxs-lookup"><span data-stu-id="9133b-194">This is the job in which the command actually ran.</span></span> <span data-ttu-id="9133b-195">Metoden dot används för att hämta egenskapen **orsak** för egenskapen **JobStateInfo** . Resultatet visar att jobbet misslyckades på grund av ett nekat åtkomst fel.</span><span class="sxs-lookup"><span data-stu-id="9133b-195">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="9133b-196">I det här fallet har användaren glömt att använda alternativet Kör som administratör när de startade PowerShell. eftersom bakgrunds jobb använder funktionerna i PowerShell måste datorn konfigureras för fjärr kommunikation för att köra ett jobb, även när jobbet körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-196">In this case, the user forgot to use the Run as administrator option when starting PowerShell.Because background jobs use the remoting features of PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.</span></span>

### <span data-ttu-id="9133b-197">Exempel 10: hämta filtrerade resultat</span><span class="sxs-lookup"><span data-stu-id="9133b-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="9133b-198">Det här exemplet visar hur du använder *filter* parametern för att hämta ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-198">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="9133b-199">*Filter* parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-199">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="9133b-200">Det första kommandot använder **arbets flödets** nyckelord för att skapa WFProcess-arbetsflödet.</span><span class="sxs-lookup"><span data-stu-id="9133b-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span>

<span data-ttu-id="9133b-201">Det andra kommandot använder parametern *AsJob* i WFProcess-arbetsflödet för att köra arbets flödet som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-201">The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="9133b-202">Den använder parametern *JobName* i arbets flödet för att ange ett namn för jobbet och parametern *PSPrivateMetadata* för arbets flödet för att ange ett anpassat ID.</span><span class="sxs-lookup"><span data-stu-id="9133b-202">It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.</span></span>

<span data-ttu-id="9133b-203">Det tredje kommandot använder *filter* parametern för **Get-Job** för att hämta jobbet efter anpassat ID som angavs i parametern *PSPrivateMetadata* .</span><span class="sxs-lookup"><span data-stu-id="9133b-203">The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.</span></span>

### <span data-ttu-id="9133b-204">Exempel 11: Hämta information om underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="9133b-205">I det här exemplet visas effekterna av att använda parametrarna *IncludeChildJob* och *ChildJobState* för **Get-Job-** cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9133b-205">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
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
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="9133b-206">Det första kommandot hämtar jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="9133b-207">Utdata innehåller ett bakgrunds jobb, ett Fjärrjobb och flera instanser av ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="9133b-208">Fjärrjobbet, Job4, verkar ha misslyckats.</span><span class="sxs-lookup"><span data-stu-id="9133b-208">The remote job, Job4, appears to have failed.</span></span>

<span data-ttu-id="9133b-209">Det andra kommandot använder *IncludeChildJob* -parametern för **Get-Job**.</span><span class="sxs-lookup"><span data-stu-id="9133b-209">The second command uses the *IncludeChildJob* parameter of **Get-Job**.</span></span> <span data-ttu-id="9133b-210">Utdata lägger till de underordnade jobben för alla jobb som har underordnade jobb. I det här fallet visar den ändrade utmatningen att endast det Job5 underordnade jobbet för Job4 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="9133b-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span>

<span data-ttu-id="9133b-211">Det tredje kommandot använder parametern *ChildJobState* med värdet misslyckades. utdata innehåller alla överordnade jobb och endast de underordnade jobb som misslyckades.</span><span class="sxs-lookup"><span data-stu-id="9133b-211">The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span>

<span data-ttu-id="9133b-212">Det fjärde kommandot använder egenskapen **JobStateInfo** för jobb och dess **orsaks** egenskap för att upptäcka varför Job5 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="9133b-212">The fourth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

## <span data-ttu-id="9133b-213">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9133b-213">PARAMETERS</span></span>

### <span data-ttu-id="9133b-214">– Efter</span><span class="sxs-lookup"><span data-stu-id="9133b-214">-After</span></span>

<span data-ttu-id="9133b-215">Hämtar slutförda jobb som avslutas efter angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="9133b-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="9133b-216">Ange ett **datetime** -objekt, till exempel ett som returneras av Get-Date-cmdlet eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .</span><span class="sxs-lookup"><span data-stu-id="9133b-216">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="9133b-217">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="9133b-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="9133b-218">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="9133b-218">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="9133b-219">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="9133b-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="9133b-220">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-221">– Före</span><span class="sxs-lookup"><span data-stu-id="9133b-221">-Before</span></span>

<span data-ttu-id="9133b-222">Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden.</span><span class="sxs-lookup"><span data-stu-id="9133b-222">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="9133b-223">Ange ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9133b-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="9133b-224">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="9133b-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="9133b-225">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="9133b-225">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="9133b-226">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="9133b-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="9133b-227">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="9133b-228">-ChildJobState</span></span>

<span data-ttu-id="9133b-229">Hämtar endast de underordnade jobb som har det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="9133b-229">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="9133b-230">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="9133b-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9133b-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="9133b-231">NotStarted</span></span>
- <span data-ttu-id="9133b-232">Körs</span><span class="sxs-lookup"><span data-stu-id="9133b-232">Running</span></span>
- <span data-ttu-id="9133b-233">Slutförd</span><span class="sxs-lookup"><span data-stu-id="9133b-233">Completed</span></span>
- <span data-ttu-id="9133b-234">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="9133b-234">Failed</span></span>
- <span data-ttu-id="9133b-235">Stoppad</span><span class="sxs-lookup"><span data-stu-id="9133b-235">Stopped</span></span>
- <span data-ttu-id="9133b-236">Blockerad</span><span class="sxs-lookup"><span data-stu-id="9133b-236">Blocked</span></span>
- <span data-ttu-id="9133b-237">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="9133b-237">Suspended</span></span>
- <span data-ttu-id="9133b-238">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="9133b-238">Disconnected</span></span>
- <span data-ttu-id="9133b-239">Pausar</span><span class="sxs-lookup"><span data-stu-id="9133b-239">Suspending</span></span>
- <span data-ttu-id="9133b-240">Stoppas</span><span class="sxs-lookup"><span data-stu-id="9133b-240">Stopping</span></span>

<span data-ttu-id="9133b-241">Som standard får **Get-Job** inte underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-241">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="9133b-242">Genom att använda *IncludeChildJob* -parametern hämtar **Get-Job** alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-242">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="9133b-243">Om du använder parametern *ChildJobState* har parametern *IncludeChildJob* ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="9133b-243">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="9133b-244">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-245">-Kommando</span><span class="sxs-lookup"><span data-stu-id="9133b-245">-Command</span></span>

<span data-ttu-id="9133b-246">Anger en matris med kommandon som strängar.</span><span class="sxs-lookup"><span data-stu-id="9133b-246">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="9133b-247">Denna cmdlet hämtar de jobb som innehåller de angivna kommandona.</span><span class="sxs-lookup"><span data-stu-id="9133b-247">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="9133b-248">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-248">The default is all jobs.</span></span>
<span data-ttu-id="9133b-249">Du kan använda jokertecken för att ange ett kommando mönster.</span><span class="sxs-lookup"><span data-stu-id="9133b-249">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="9133b-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="9133b-250">-Filter</span></span>

<span data-ttu-id="9133b-251">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="9133b-251">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="9133b-252">Denna cmdlet hämtar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="9133b-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="9133b-253">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="9133b-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="9133b-254">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="9133b-255">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="9133b-255">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="9133b-256">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="9133b-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="9133b-257">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="9133b-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="9133b-258">-HasMoreData</span></span>

<span data-ttu-id="9133b-259">Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="9133b-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="9133b-260">Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="9133b-261">Ange ett värde för $True för att hämta jobb som har fler resultat.</span><span class="sxs-lookup"><span data-stu-id="9133b-261">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="9133b-262">Ange ett värde för $False om du vill hämta jobb som inte har fler resultat.</span><span class="sxs-lookup"><span data-stu-id="9133b-262">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="9133b-263">Om du vill hämta resultatet av ett jobb använder du cmdleten Receive-Job.</span><span class="sxs-lookup"><span data-stu-id="9133b-263">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="9133b-264">När du använder cmdleten **Receive-Job** , tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras.</span><span class="sxs-lookup"><span data-stu-id="9133b-264">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="9133b-265">När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till $false) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="9133b-266">Använd parametern *Behåll* för **Receive-Job** för att förhindra **mottagning – jobb** från att ta bort resultat och ändra värdet för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="9133b-266">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span> <span data-ttu-id="9133b-267">För mer information ange `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="9133b-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="9133b-268">Egenskapen **HasMoreData** är unik för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="9133b-269">Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda cmdleten **Receive-Job** i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är $false.</span><span class="sxs-lookup"><span data-stu-id="9133b-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span> <span data-ttu-id="9133b-270">Mer information finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="9133b-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="9133b-271">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-272">-ID</span><span class="sxs-lookup"><span data-stu-id="9133b-272">-Id</span></span>

<span data-ttu-id="9133b-273">Anger en matris med ID: n för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="9133b-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="9133b-274">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-274">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="9133b-275">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="9133b-276">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="9133b-276">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="9133b-277">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="9133b-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="9133b-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="9133b-278">-IncludeChildJob</span></span>

<span data-ttu-id="9133b-279">Anger att den här cmdleten Returnerar underordnade jobb, förutom överordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="9133b-280">Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, för vilka **Get-Job** returnerar ett överordnat behållar jobb och jobb haverier, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-280">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="9133b-281">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="9133b-282">-InstanceId</span></span>

<span data-ttu-id="9133b-283">Anger en matris med instans-ID för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="9133b-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="9133b-284">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-284">The default is all jobs.</span></span>

<span data-ttu-id="9133b-285">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="9133b-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="9133b-286">Använd **Get-Job** för att hitta instans-ID för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="9133b-286">To find the instance ID of a job, use **Get-Job**.</span></span>

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

### <span data-ttu-id="9133b-287">-Name</span><span class="sxs-lookup"><span data-stu-id="9133b-287">-Name</span></span>

<span data-ttu-id="9133b-288">Anger en matris med informativa namn på jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="9133b-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="9133b-289">Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="9133b-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="9133b-290">Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-290">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="9133b-291">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="9133b-291">-Newest</span></span>

<span data-ttu-id="9133b-292">Anger ett antal jobb som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="9133b-292">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="9133b-293">Denna cmdlet hämtar de jobb som avslutades senast.</span><span class="sxs-lookup"><span data-stu-id="9133b-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="9133b-294">Den *senaste* parametern kan inte sortera eller returnera de senaste jobben i slut tid.</span><span class="sxs-lookup"><span data-stu-id="9133b-294">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="9133b-295">Om du vill sortera utdata använder du Sort-Object cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9133b-295">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="9133b-296">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9133b-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9133b-297">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="9133b-297">-State</span></span>

<span data-ttu-id="9133b-298">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="9133b-298">Specifies a job state.</span></span>
<span data-ttu-id="9133b-299">Denna cmdlet hämtar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="9133b-299">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="9133b-300">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="9133b-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="9133b-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="9133b-301">NotStarted</span></span>
- <span data-ttu-id="9133b-302">Körs</span><span class="sxs-lookup"><span data-stu-id="9133b-302">Running</span></span>
- <span data-ttu-id="9133b-303">Slutförd</span><span class="sxs-lookup"><span data-stu-id="9133b-303">Completed</span></span>
- <span data-ttu-id="9133b-304">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="9133b-304">Failed</span></span>
- <span data-ttu-id="9133b-305">Stoppad</span><span class="sxs-lookup"><span data-stu-id="9133b-305">Stopped</span></span>
- <span data-ttu-id="9133b-306">Blockerad</span><span class="sxs-lookup"><span data-stu-id="9133b-306">Blocked</span></span>
- <span data-ttu-id="9133b-307">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="9133b-307">Suspended</span></span>
- <span data-ttu-id="9133b-308">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="9133b-308">Disconnected</span></span>
- <span data-ttu-id="9133b-309">Pausar</span><span class="sxs-lookup"><span data-stu-id="9133b-309">Suspending</span></span>
- <span data-ttu-id="9133b-310">Stoppas</span><span class="sxs-lookup"><span data-stu-id="9133b-310">Stopping</span></span>

<span data-ttu-id="9133b-311">Som standard hämtar **Get-Job** alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-311">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="9133b-312">Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="9133b-312">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="9133b-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9133b-313">CommonParameters</span></span>

<span data-ttu-id="9133b-314">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9133b-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9133b-315">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9133b-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9133b-316">INDATA</span><span class="sxs-lookup"><span data-stu-id="9133b-316">INPUTS</span></span>

### <span data-ttu-id="9133b-317">Inget</span><span class="sxs-lookup"><span data-stu-id="9133b-317">None</span></span>

<span data-ttu-id="9133b-318">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9133b-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="9133b-319">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9133b-319">OUTPUTS</span></span>

### <span data-ttu-id="9133b-320">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="9133b-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="9133b-321">Denna cmdlet returnerar objekt som representerar jobben i sessionen.</span><span class="sxs-lookup"><span data-stu-id="9133b-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="9133b-322">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9133b-322">NOTES</span></span>

* <span data-ttu-id="9133b-323">**PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="9133b-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="9133b-324">Egenskap svärdet bestäms av jobb typ författaren.</span><span class="sxs-lookup"><span data-stu-id="9133b-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="9133b-325">I följande lista visas vanliga jobb typer.</span><span class="sxs-lookup"><span data-stu-id="9133b-325">The following list shows common job types.</span></span>

  - <span data-ttu-id="9133b-326">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="9133b-326">**BackgroundJob**.</span></span>
<span data-ttu-id="9133b-327">Ett lokalt jobb har startats med hjälp av **Start-Job**.</span><span class="sxs-lookup"><span data-stu-id="9133b-327">Local job started by using **Start-Job**.</span></span>

  - <span data-ttu-id="9133b-328">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="9133b-328">**RemoteJob**.</span></span>
<span data-ttu-id="9133b-329">Jobbet startades i en **PSSession** med hjälp av parametern *AsJob* i Invoke-Command-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9133b-329">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="9133b-330">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="9133b-330">**PSWorkflowJob**.</span></span>
<span data-ttu-id="9133b-331">Jobbet startades med *AsJob* gemensamma parameter för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="9133b-331">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="9133b-332">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9133b-332">RELATED LINKS</span></span>

[<span data-ttu-id="9133b-333">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="9133b-333">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="9133b-334">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-334">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="9133b-335">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-335">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="9133b-336">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-336">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="9133b-337">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="9133b-337">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="9133b-338">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="9133b-338">Wait-Job</span></span>](Wait-Job.md)
