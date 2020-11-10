---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 167f56964bbdb675c2dd85e2803fdee2d308ee4f
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389580"
---
# <span data-ttu-id="3de88-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="3de88-103">Get-Job</span></span>

## <span data-ttu-id="3de88-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3de88-104">SYNOPSIS</span></span>
<span data-ttu-id="3de88-105">Hämtar PowerShell-bakgrunds jobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="3de88-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3de88-106">SYNTAX</span></span>

### <span data-ttu-id="3de88-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="3de88-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="3de88-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="3de88-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="3de88-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="3de88-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3de88-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="3de88-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="3de88-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="3de88-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3de88-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="3de88-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="3de88-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3de88-113">DESCRIPTION</span></span>

<span data-ttu-id="3de88-114">`Get-Job`Cmdleten hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-114">The `Get-Job` cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="3de88-115">Du kan använda `Get-Job` för att hämta jobb som har startats med hjälp av `Start-Job` cmdleten, eller genom att använda parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3de88-115">You can use `Get-Job` to get jobs that were started by using the `Start-Job` cmdlet, or by using the **AsJob** parameter of any cmdlet.</span></span>

<span data-ttu-id="3de88-116">Utan parametrar hämtar ett- `Get-Job` kommando alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-116">Without parameters, a `Get-Job` command gets all jobs in the current session.</span></span> <span data-ttu-id="3de88-117">Du kan använda parametrarna för `Get-Job` för att hämta specifika jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-117">You can use the parameters of `Get-Job` to get particular jobs.</span></span>

<span data-ttu-id="3de88-118">Jobbobjektet som `Get-Job` returnerar innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="3de88-118">The job object that `Get-Job` returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="3de88-119">Använd cmdleten för att hämta resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-119">To get the results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="3de88-120">Ett Windows PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="3de88-121">Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="3de88-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="3de88-122">Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="3de88-122">For more information about background jobs in Windows PowerShell, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="3de88-123">Från och med Windows PowerShell 3,0 `Get-Job` hämtar cmdlet: en även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-123">Beginning in Windows PowerShell 3.0, the `Get-Job` cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="3de88-124">Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .</span><span class="sxs-lookup"><span data-stu-id="3de88-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="3de88-125">Om du vill aktivera `Get-Job` en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Get-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="3de88-125">To enable `Get-Job` to get a custom job type, import the module that supports the custom job type into the session before you run a `Get-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="3de88-126">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="3de88-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3de88-127">EXAMPLES</span></span>

### <span data-ttu-id="3de88-128">Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="3de88-128">Example 1: Get all background jobs started in the current session</span></span>

<span data-ttu-id="3de88-129">Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-129">This command gets all background jobs started in the current session.</span></span> <span data-ttu-id="3de88-130">Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

```
PS C:\> Get-Job
```

### <span data-ttu-id="3de88-131">Exempel 2: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="3de88-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="3de88-132">De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span> <span data-ttu-id="3de88-133">Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.</span><span class="sxs-lookup"><span data-stu-id="3de88-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

<span data-ttu-id="3de88-134">Det första kommandot använder `Get-Job` cmdleten för att hämta ett jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-134">The first command uses the `Get-Job` cmdlet to get a job.</span></span> <span data-ttu-id="3de88-135">Parametern **Name** används för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-135">It uses the **Name** parameter to identify the job.</span></span> <span data-ttu-id="3de88-136">Kommandot lagrar jobbobjektet som `Get-Job` returneras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3de88-136">The command stores the job object that `Get-Job` returns in the `$j` variable.</span></span> <span data-ttu-id="3de88-137">I det här exemplet finns det bara ett jobb med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="3de88-137">In this example, there is only one job with the specified name.</span></span> <span data-ttu-id="3de88-138">Det andra kommandot hämtar **InstanceID** -egenskapen för objektet i `$j` variabeln och lagrar det i `$ID` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3de88-138">The second command gets the **InstanceId** property of the object in the `$j` variable and stores it in the `$ID` variable.</span></span> <span data-ttu-id="3de88-139">Det tredje kommandot visar värdet för `$ID` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3de88-139">The third command displays the value of the `$ID` variable.</span></span> <span data-ttu-id="3de88-140">Det fjärde kommandot använder `Stop-Job` cmdleten för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-140">The fourth command uses `Stop-Job` cmdlet to stop the job.</span></span>
<span data-ttu-id="3de88-141">Parametern **InstanceID** används för att identifiera jobbet och `$ID` variabeln som representerar JOBBETS instans-ID.</span><span class="sxs-lookup"><span data-stu-id="3de88-141">It uses the **InstanceId** parameter to identify the job and `$ID` variable to represent the instance ID of the job.</span></span>

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### <span data-ttu-id="3de88-142">Exempel 3: Hämta jobb som innehåller ett speciellt kommando</span><span class="sxs-lookup"><span data-stu-id="3de88-142">Example 3: Get jobs that include a specific command</span></span>

<span data-ttu-id="3de88-143">Det här kommandot hämtar jobben i systemet som innehåller ett `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="3de88-143">This command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="3de88-144">Kommandot använder **kommando** parametern för `Get-Job` att begränsa de hämtade jobben.</span><span class="sxs-lookup"><span data-stu-id="3de88-144">The command uses the **Command** parameter of `Get-Job` to limit the jobs retrieved.</span></span> <span data-ttu-id="3de88-145">Kommandot använder jokertecken ( `*` ) för att hämta jobb som innehåller ett `Get-Process` kommando var som helst i kommando strängen.</span><span class="sxs-lookup"><span data-stu-id="3de88-145">The command uses wildcard characters (`*`) to get jobs that include a `Get-Process` command anywhere in the command string.</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

### <span data-ttu-id="3de88-146">Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="3de88-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

<span data-ttu-id="3de88-147">Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller ett `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="3de88-147">Like the command in the previous example, this command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="3de88-148">Kommandot använder en pipeline-operator ( `|` ) för att skicka en sträng, inom citat tecken, till `Get-Job` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="3de88-148">The command uses a pipeline operator (`|`) to send a string, in quotation marks, to the `Get-Job` cmdlet.</span></span> <span data-ttu-id="3de88-149">Det motsvarar föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="3de88-149">It is the equivalent of the previous command.</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

### <span data-ttu-id="3de88-150">Exempel 5: Hämta jobb som inte har startats</span><span class="sxs-lookup"><span data-stu-id="3de88-150">Example 5: Get jobs that have not been started</span></span>

<span data-ttu-id="3de88-151">Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats.</span><span class="sxs-lookup"><span data-stu-id="3de88-151">This command gets only those jobs that have been created but have not yet been started.</span></span> <span data-ttu-id="3de88-152">Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.</span><span class="sxs-lookup"><span data-stu-id="3de88-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

```
PS C:\> Get-Job -State NotStarted
```

### <span data-ttu-id="3de88-153">Exempel 6: Hämta jobb som inte har tilldelats ett namn</span><span class="sxs-lookup"><span data-stu-id="3de88-153">Example 6: Get jobs that have not been assigned a name</span></span>

<span data-ttu-id="3de88-154">Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-154">This command gets all jobs that have job names that begin with job.</span></span> <span data-ttu-id="3de88-155">Eftersom `job<number>` är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.</span><span class="sxs-lookup"><span data-stu-id="3de88-155">Because `job<number>` is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

```
PS C:\> Get-Job -Name Job*
```

### <span data-ttu-id="3de88-156">Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando</span><span class="sxs-lookup"><span data-stu-id="3de88-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="3de88-157">Det här exemplet visar hur du använder `Get-Job` för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="3de88-157">This example shows how to use `Get-Job` to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

<span data-ttu-id="3de88-158">Det första kommandot använder `Start-Job` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-158">The first command uses the `Start-Job` cmdlet to start a background job that runs a `Get-Process` command on the local computer.</span></span> <span data-ttu-id="3de88-159">Kommandot använder **Name** -parametern för `Start-Job` att tilldela jobbet ett eget namn.</span><span class="sxs-lookup"><span data-stu-id="3de88-159">The command uses the **Name** parameter of `Start-Job` to assign a friendly name to the job.</span></span> <span data-ttu-id="3de88-160">Det andra kommandot använder `Get-Job` för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-160">The second command uses `Get-Job` to get the job.</span></span> <span data-ttu-id="3de88-161">Den använder **Name** -parametern för `Get-Job` att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-161">It uses the **Name** parameter of `Get-Job` to identify the job.</span></span> <span data-ttu-id="3de88-162">Kommandot sparar det resulterande jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3de88-162">The command saves the resulting job object in the `$j` variable.</span></span> <span data-ttu-id="3de88-163">Det tredje kommandot visar värdet för jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3de88-163">The third command displays the value of the job object in the `$j` variable.</span></span> <span data-ttu-id="3de88-164">Värdet för egenskapen **State** visar att jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="3de88-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="3de88-165">Värdet för egenskapen **HasMoreData** visar att det finns resultat som är tillgängliga från jobbet som ännu inte har hämtats.</span><span class="sxs-lookup"><span data-stu-id="3de88-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span> <span data-ttu-id="3de88-166">Det fjärde kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-166">The fourth command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="3de88-167">Objektet används i `$j` variabeln för att representera jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-167">It uses the job object in the `$j` variable to represent the job.</span></span> <span data-ttu-id="3de88-168">Du kan också använda en pipeline-operator för att skicka ett jobb objekt till `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-168">You can also use a pipeline operator to send a job object to `Receive-Job`.</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob
PS C:\> $j = Get-Job -Name MyJob
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```


### <span data-ttu-id="3de88-169">Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod</span><span class="sxs-lookup"><span data-stu-id="3de88-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="3de88-170">Det här exemplet visar att `Get-Job` cmdleten kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.</span><span class="sxs-lookup"><span data-stu-id="3de88-170">This example demonstrates that the `Get-Job` cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

<span data-ttu-id="3de88-171">Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-171">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="3de88-172">Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett jobb på S1-datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-172">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="3de88-173">Även om kommandona i jobbet körs på fjärrdatorn skapas jobbobjektet på den lokala datorn, så du kan använda lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span> <span data-ttu-id="3de88-174">Det tredje kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på S2-datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-174">The third command uses the `Invoke-Command` cmdlet to run a `Start-Job` command on the S2 computer.</span></span> <span data-ttu-id="3de88-175">Med den här metoden skapas jobbobjektet på fjärrdatorn, så du kan använda fjärrkommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span> <span data-ttu-id="3de88-176">Det fjärde kommandot använder `Get-Job` för att hämta jobb som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-176">The fourth command uses `Get-Job` to get the jobs stored on the local computer.</span></span> <span data-ttu-id="3de88-177">Egenskapen **PSJobTypeName** för jobb, som introducerades i Windows PowerShell 3,0, visar att det lokala jobbet som startades med hjälp av `Start-Job` cmdleten är ett bakgrunds jobb och att jobbet startade i en fjärrsession med hjälp av `Invoke-Command` cmdleten är ett Fjärrjobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the `Start-Job` cmdlet is a background job and the job started in a remote session by using the `Invoke-Command` cmdlet is a remote job.</span></span> <span data-ttu-id="3de88-178">Det femte kommandot använder `Invoke-Command` för att köra ett `Get-Job` kommando på S2-datorn. Exempel resultatet visar resultatet av `Get-Job` kommandot.</span><span class="sxs-lookup"><span data-stu-id="3de88-178">The fifth command uses `Invoke-Command` to run a `Get-Job` command on the S2 computer.The sample output shows the results of the `Get-Job` command.</span></span> <span data-ttu-id="3de88-179">På S2-datorn verkar jobbet vara ett lokalt jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="3de88-180">Dator namnet är localhost och jobb typen är ett bakgrunds jobb. Mer information om hur du kör bakgrunds jobb på fjärrdatorer finns [about_Remote_Jobs](./about/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="3de88-180">The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see [about_Remote_Jobs](./about/about_Remote_Jobs.md).</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

### <span data-ttu-id="3de88-181">Exempel 9: Undersök ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-181">Example 9: Investigate a failed job</span></span>

<span data-ttu-id="3de88-182">Det här kommandot visar hur du använder jobbobjektet som `Get-Job` returnerar för att undersöka varför ett jobb har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="3de88-182">This command shows how to use the job object that `Get-Job` returns to investigate why a job failed.</span></span>
<span data-ttu-id="3de88-183">Det visar också hur du hämtar de underordnade jobben för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-183">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="3de88-184">Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-184">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="3de88-185">Jobbobjektet som `Start-Job` returnerar visar att jobbet misslyckades.</span><span class="sxs-lookup"><span data-stu-id="3de88-185">The job object that `Start-Job` returns shows that the job failed.</span></span> <span data-ttu-id="3de88-186">Det gick inte att **Ange värdet för tillstånds** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="3de88-186">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="3de88-187">Det andra kommandot använder `Get-Job` cmdleten för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-187">The second command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="3de88-188">Kommandot använder punkt metoden för att hämta värdet för objektets **JobStateInfo** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="3de88-188">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="3de88-189">Den använder en pipeline-operator för att skicka objektet i egenskapen **JobStateInfo** till `Format-List` cmdleten, som formaterar alla egenskaper för objektet ( `*` ) i en lista. Resultatet av `Format-List` kommandot visar att värdet för jobbets **orsaks** egenskap är tomt.</span><span class="sxs-lookup"><span data-stu-id="3de88-189">It uses a pipeline operator to send the object in the **JobStateInfo** property to the `Format-List` cmdlet, which formats all of the properties of the object (`*`) in a list.The result of the `Format-List` command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="3de88-190">Det tredje kommandot undersöker mer.</span><span class="sxs-lookup"><span data-stu-id="3de88-190">The third command investigates more.</span></span> <span data-ttu-id="3de88-191">Det använder ett `Get-Job` kommando för att hämta jobbet och använder sedan en pipeline-operator för att skicka hela jobbobjektet till `Format-List` cmdleten, som visar alla egenskaper för jobbet i en lista. Visningen av alla egenskaper i jobbobjektet visar att jobbet innehåller ett underordnat jobb med namnet Job2.</span><span class="sxs-lookup"><span data-stu-id="3de88-191">It uses a `Get-Job` command to get the job and then uses a pipeline operator to send the whole job object to the `Format-List` cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="3de88-192">Det fjärde kommandot använder `Get-Job` för att hämta jobbobjektet som representerar det underordnade Job2-jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-192">The fourth command uses `Get-Job` to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="3de88-193">Det här är det jobb där kommandot faktiskt kördes.</span><span class="sxs-lookup"><span data-stu-id="3de88-193">This is the job in which the command actually ran.</span></span> <span data-ttu-id="3de88-194">Metoden dot används för att hämta egenskapen **orsak** för egenskapen **JobStateInfo** . Resultatet visar att jobbet misslyckades på grund av ett nekat åtkomst fel.</span><span class="sxs-lookup"><span data-stu-id="3de88-194">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="3de88-195">I det här fallet har användaren glömt att använda alternativet Kör som administratör när Windows PowerShell startades. eftersom bakgrunds jobb använder funktionerna för fjärr kommunikation i Windows PowerShell måste datorn konfigureras för fjärr kommunikation för att köra ett jobb, även när jobbet körs på den lokala datorn. Information om krav för fjärr kommunikation i Windows PowerShell finns [about_Remote_Requirements](./about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de88-195">In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see [about_Remote_Requirements](./about/about_Remote_Requirements.md).</span></span> <span data-ttu-id="3de88-196">Fel söknings tips finns i [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3de88-196">For troubleshooting tips, see [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).</span></span>

```
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

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

PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the
following error message: Access is denied.
```

### <span data-ttu-id="3de88-197">Exempel 10: hämta filtrerade resultat</span><span class="sxs-lookup"><span data-stu-id="3de88-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="3de88-198">Det här exemplet visar hur du använder **filter** parametern för att hämta ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-198">This example shows how to use the **Filter** parameter to get a workflow job.</span></span> <span data-ttu-id="3de88-199">**Filter** parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-199">The **Filter** parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

<span data-ttu-id="3de88-200">Det första kommandot använder **arbets flödets** nyckelord för att skapa WFProcess-arbetsflödet.</span><span class="sxs-lookup"><span data-stu-id="3de88-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span> <span data-ttu-id="3de88-201">Det andra kommandot använder parametern **AsJob** i WFProcess-arbetsflödet för att köra arbets flödet som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-201">The second command uses the **AsJob** parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="3de88-202">Den använder parametern **JobName** i arbets flödet för att ange ett namn för jobbet och parametern **PSPrivateMetadata** för arbets flödet för att ange ett anpassat ID.</span><span class="sxs-lookup"><span data-stu-id="3de88-202">It uses the **JobName** parameter of the workflow to specify a name for the job, and the **PSPrivateMetadata** parameter of the workflow to specify a custom ID.</span></span> <span data-ttu-id="3de88-203">Det tredje kommandot använder **filter** parametern för `Get-Job` för att hämta jobbet efter anpassat ID som angavs i parametern **PSPrivateMetadata** .</span><span class="sxs-lookup"><span data-stu-id="3de88-203">The third command uses the **Filter** parameter of `Get-Job` to get the job by custom ID that was specified in the **PSPrivateMetadata** parameter.</span></span>

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### <span data-ttu-id="3de88-204">Exempel 11: Hämta information om underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="3de88-205">I det här exemplet visas effekterna av att använda parametrarna **IncludeChildJob** och **ChildJobState** för `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3de88-205">This example shows the effect of using the **IncludeChildJob** and **ChildJobState** parameters of the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="3de88-206">Det första kommandot hämtar jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="3de88-207">Utdata innehåller ett bakgrunds jobb, ett Fjärrjobb och flera instanser av ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="3de88-208">Fjärrjobbet, Job4, verkar ha misslyckats.</span><span class="sxs-lookup"><span data-stu-id="3de88-208">The remote job, Job4, appears to have failed.</span></span>
<span data-ttu-id="3de88-209">Det andra kommandot använder parametern **IncludeChildJob** i `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-209">The second command uses the **IncludeChildJob** parameter of `Get-Job`.</span></span> <span data-ttu-id="3de88-210">Utdata lägger till de underordnade jobben för alla jobb som har underordnade jobb. I det här fallet visar den ändrade utmatningen att endast det Job5 underordnade jobbet för Job4 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="3de88-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span> <span data-ttu-id="3de88-211">Det tredje kommandot använder parametern **ChildJobState** med värdet misslyckades. utdata innehåller alla överordnade jobb och endast de underordnade jobb som misslyckades.</span><span class="sxs-lookup"><span data-stu-id="3de88-211">The third command uses the **ChildJobState** parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span> <span data-ttu-id="3de88-212">Det femte kommandot använder egenskapen **JobStateInfo** för jobb och dess **orsaks** egenskap för att upptäcka varför Job5 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="3de88-212">The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

```
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

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

PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
```

<span data-ttu-id="3de88-213">Mer information finns i hjälp avsnittet för [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) .</span><span class="sxs-lookup"><span data-stu-id="3de88-213">For more information, see the [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) Help topic.</span></span>

## <span data-ttu-id="3de88-214">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3de88-214">PARAMETERS</span></span>

### <span data-ttu-id="3de88-215">– Efter</span><span class="sxs-lookup"><span data-stu-id="3de88-215">-After</span></span>

<span data-ttu-id="3de88-216">Hämtar slutförda jobb som avslutas efter angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="3de88-216">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="3de88-217">Ange ett **datetime** -objekt, till exempel ett som returneras av `Get-Date` cmdleten eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .</span><span class="sxs-lookup"><span data-stu-id="3de88-217">Enter a **DateTime** object, such as one returned by the `Get-Date` cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="3de88-218">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="3de88-218">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="3de88-219">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3de88-219">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3de88-220">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="3de88-220">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3de88-221">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-222">– Före</span><span class="sxs-lookup"><span data-stu-id="3de88-222">-Before</span></span>

<span data-ttu-id="3de88-223">Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden.</span><span class="sxs-lookup"><span data-stu-id="3de88-223">Gets completed jobs that ended before the specified date and time.</span></span> <span data-ttu-id="3de88-224">Ange ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3de88-224">Enter a **DateTime** object.</span></span>

<span data-ttu-id="3de88-225">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="3de88-225">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="3de88-226">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3de88-226">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3de88-227">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="3de88-227">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3de88-228">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-229">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="3de88-229">-ChildJobState</span></span>

<span data-ttu-id="3de88-230">Hämtar endast de underordnade jobb som har det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="3de88-230">Gets only the child jobs that have the specified state.</span></span> <span data-ttu-id="3de88-231">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="3de88-231">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3de88-232">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3de88-232">NotStarted</span></span>
- <span data-ttu-id="3de88-233">Körs</span><span class="sxs-lookup"><span data-stu-id="3de88-233">Running</span></span>
- <span data-ttu-id="3de88-234">Slutförd</span><span class="sxs-lookup"><span data-stu-id="3de88-234">Completed</span></span>
- <span data-ttu-id="3de88-235">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="3de88-235">Failed</span></span>
- <span data-ttu-id="3de88-236">Stoppad</span><span class="sxs-lookup"><span data-stu-id="3de88-236">Stopped</span></span>
- <span data-ttu-id="3de88-237">Blockerad</span><span class="sxs-lookup"><span data-stu-id="3de88-237">Blocked</span></span>
- <span data-ttu-id="3de88-238">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="3de88-238">Suspended</span></span>
- <span data-ttu-id="3de88-239">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="3de88-239">Disconnected</span></span>
- <span data-ttu-id="3de88-240">Pausar</span><span class="sxs-lookup"><span data-stu-id="3de88-240">Suspending</span></span>
- <span data-ttu-id="3de88-241">Stoppas</span><span class="sxs-lookup"><span data-stu-id="3de88-241">Stopping</span></span>

<span data-ttu-id="3de88-242">Som standard `Get-Job` får inte underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-242">By default, `Get-Job` does not get child jobs.</span></span> <span data-ttu-id="3de88-243">Med hjälp av parametern **IncludeChildJob** `Get-Job` hämtar du alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-243">By using the **IncludeChildJob** parameter, `Get-Job` gets all child jobs.</span></span> <span data-ttu-id="3de88-244">Om du använder parametern **ChildJobState** har parametern **IncludeChildJob** ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="3de88-244">If you use the **ChildJobState** parameter, the **IncludeChildJob** parameter has no effect.</span></span>

<span data-ttu-id="3de88-245">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-245">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-246">-Kommando</span><span class="sxs-lookup"><span data-stu-id="3de88-246">-Command</span></span>

<span data-ttu-id="3de88-247">Anger en matris med kommandon som strängar.</span><span class="sxs-lookup"><span data-stu-id="3de88-247">Specifies an array of commands as strings.</span></span> <span data-ttu-id="3de88-248">Denna cmdlet hämtar de jobb som innehåller de angivna kommandona.</span><span class="sxs-lookup"><span data-stu-id="3de88-248">This cmdlet gets the jobs that include the specified commands.</span></span> <span data-ttu-id="3de88-249">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-249">The default is all jobs.</span></span> <span data-ttu-id="3de88-250">Du kan använda jokertecken för att ange ett kommando mönster.</span><span class="sxs-lookup"><span data-stu-id="3de88-250">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="3de88-251">-Filter</span><span class="sxs-lookup"><span data-stu-id="3de88-251">-Filter</span></span>

<span data-ttu-id="3de88-252">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="3de88-252">Specifies a hash table of conditions.</span></span> <span data-ttu-id="3de88-253">Denna cmdlet hämtar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="3de88-253">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="3de88-254">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="3de88-254">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="3de88-255">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-255">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="3de88-256">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3de88-256">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="3de88-257">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="3de88-257">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="3de88-258">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-258">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-259">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="3de88-259">-HasMoreData</span></span>

<span data-ttu-id="3de88-260">Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="3de88-260">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="3de88-261">Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-261">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span> <span data-ttu-id="3de88-262">Ange ett värde för om du vill hämta jobb som har fler resultat `$True` .</span><span class="sxs-lookup"><span data-stu-id="3de88-262">To get jobs that have more results, specify a value of `$True`.</span></span> <span data-ttu-id="3de88-263">Ange ett värde för om du vill hämta jobb som inte har fler resultat `$False` .</span><span class="sxs-lookup"><span data-stu-id="3de88-263">To get jobs that do not have more results, specify a value of `$False`.</span></span>

<span data-ttu-id="3de88-264">Använd cmdleten för att hämta resultatet av ett jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-264">To get the results of a job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="3de88-265">När du använder `Receive-Job` cmdleten tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras.</span><span class="sxs-lookup"><span data-stu-id="3de88-265">When you use the `Receive-Job` cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="3de88-266">När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till `$False` ) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-266">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to `$False`) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="3de88-267">Använd parametern **Behåll** för `Receive-Job` att förhindra `Receive-Job` borttagning av resultat och ändra värdet för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="3de88-267">Use the **Keep** parameter of `Receive-Job` to prevent `Receive-Job` from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="3de88-268">För mer information ange `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="3de88-268">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="3de88-269">Egenskapen **HasMoreData** är unik för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-269">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="3de88-270">Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda `Receive-Job` cmdleten i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är `$False` .</span><span class="sxs-lookup"><span data-stu-id="3de88-270">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the `Receive-Job` cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is `$False`.</span></span> <span data-ttu-id="3de88-271">Mer information finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="3de88-271">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="3de88-272">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-273">-ID</span><span class="sxs-lookup"><span data-stu-id="3de88-273">-Id</span></span>

<span data-ttu-id="3de88-274">Anger en matris med ID: n för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="3de88-274">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="3de88-275">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-275">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="3de88-276">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-276">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="3de88-277">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="3de88-277">You can type one or more IDs separated by commas.</span></span> <span data-ttu-id="3de88-278">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="3de88-278">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="3de88-279">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="3de88-279">-IncludeChildJob</span></span>

<span data-ttu-id="3de88-280">Anger att den här cmdleten Returnerar underordnade jobb, förutom överordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-280">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="3de88-281">Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, som `Get-Job` returnerar ett överordnat jobb och jobb haveri, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-281">This parameter is especially useful for investigating workflow jobs, for which `Get-Job` returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="3de88-282">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-283">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="3de88-283">-InstanceId</span></span>

<span data-ttu-id="3de88-284">Anger en matris med instans-ID för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="3de88-284">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span> <span data-ttu-id="3de88-285">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="3de88-285">The default is all jobs.</span></span>

<span data-ttu-id="3de88-286">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="3de88-286">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="3de88-287">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-287">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="3de88-288">-Name</span><span class="sxs-lookup"><span data-stu-id="3de88-288">-Name</span></span>

<span data-ttu-id="3de88-289">Anger en matris med informativa namn på jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="3de88-289">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span> <span data-ttu-id="3de88-290">Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="3de88-290">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span> <span data-ttu-id="3de88-291">Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-291">By default, `Get-Job` gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="3de88-292">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="3de88-292">-Newest</span></span>

<span data-ttu-id="3de88-293">Anger ett antal jobb som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="3de88-293">Specifies a number of jobs to get.</span></span> <span data-ttu-id="3de88-294">Denna cmdlet hämtar de jobb som avslutades senast.</span><span class="sxs-lookup"><span data-stu-id="3de88-294">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="3de88-295">Den **senaste** parametern kan inte sortera eller returnera de senaste jobben i slut tid.</span><span class="sxs-lookup"><span data-stu-id="3de88-295">The **Newest** parameter does not sort or return the newest jobs in end-time order.</span></span> <span data-ttu-id="3de88-296">Använd cmdleten för att sortera utdata `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="3de88-296">To sort the output, use the `Sort-Object` cmdlet.</span></span>

<span data-ttu-id="3de88-297">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3de88-297">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="3de88-298">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="3de88-298">-State</span></span>

<span data-ttu-id="3de88-299">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="3de88-299">Specifies a job state.</span></span> <span data-ttu-id="3de88-300">Denna cmdlet hämtar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="3de88-300">This cmdlet gets only jobs in the specified state.</span></span> <span data-ttu-id="3de88-301">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="3de88-301">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3de88-302">NotStarted</span><span class="sxs-lookup"><span data-stu-id="3de88-302">NotStarted</span></span>
- <span data-ttu-id="3de88-303">Körs</span><span class="sxs-lookup"><span data-stu-id="3de88-303">Running</span></span>
- <span data-ttu-id="3de88-304">Slutförd</span><span class="sxs-lookup"><span data-stu-id="3de88-304">Completed</span></span>
- <span data-ttu-id="3de88-305">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="3de88-305">Failed</span></span>
- <span data-ttu-id="3de88-306">Stoppad</span><span class="sxs-lookup"><span data-stu-id="3de88-306">Stopped</span></span>
- <span data-ttu-id="3de88-307">Blockerad</span><span class="sxs-lookup"><span data-stu-id="3de88-307">Blocked</span></span>
- <span data-ttu-id="3de88-308">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="3de88-308">Suspended</span></span>
- <span data-ttu-id="3de88-309">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="3de88-309">Disconnected</span></span>
- <span data-ttu-id="3de88-310">Pausar</span><span class="sxs-lookup"><span data-stu-id="3de88-310">Suspending</span></span>
- <span data-ttu-id="3de88-311">Stoppas</span><span class="sxs-lookup"><span data-stu-id="3de88-311">Stopping</span></span>

<span data-ttu-id="3de88-312">Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-312">By default, `Get-Job` gets all the jobs in the current session.</span></span>

<span data-ttu-id="3de88-313">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="3de88-313">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="3de88-314">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3de88-314">CommonParameters</span></span>

<span data-ttu-id="3de88-315">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3de88-315">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3de88-316">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3de88-316">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3de88-317">INDATA</span><span class="sxs-lookup"><span data-stu-id="3de88-317">INPUTS</span></span>

### <span data-ttu-id="3de88-318">Inget</span><span class="sxs-lookup"><span data-stu-id="3de88-318">None</span></span>

<span data-ttu-id="3de88-319">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3de88-319">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3de88-320">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3de88-320">OUTPUTS</span></span>

### <span data-ttu-id="3de88-321">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="3de88-321">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="3de88-322">Denna cmdlet returnerar objekt som representerar jobben i sessionen.</span><span class="sxs-lookup"><span data-stu-id="3de88-322">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="3de88-323">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3de88-323">NOTES</span></span>

<span data-ttu-id="3de88-324">**PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="3de88-324">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="3de88-325">Egenskap svärdet bestäms av jobb typ författaren.</span><span class="sxs-lookup"><span data-stu-id="3de88-325">The property value is determined by the job type author.</span></span> <span data-ttu-id="3de88-326">I följande lista visas vanliga jobb typer.</span><span class="sxs-lookup"><span data-stu-id="3de88-326">The following list shows common job types.</span></span>

- <span data-ttu-id="3de88-327">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="3de88-327">**BackgroundJob**.</span></span> <span data-ttu-id="3de88-328">Lokalt jobb har startats med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="3de88-328">Local job started by using `Start-Job`.</span></span>
- <span data-ttu-id="3de88-329">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="3de88-329">**RemoteJob**.</span></span> <span data-ttu-id="3de88-330">Jobbet startade i en **PSSession** med hjälp av parametern **AsJob** för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3de88-330">Job started in a **PSSession** by using the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span>
- <span data-ttu-id="3de88-331">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="3de88-331">**PSWorkflowJob**.</span></span> <span data-ttu-id="3de88-332">Jobbet startades med **AsJob** gemensamma parameter för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="3de88-332">Job started by using the **AsJob** common parameter of workflows.</span></span>

## <span data-ttu-id="3de88-333">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3de88-333">RELATED LINKS</span></span>

[<span data-ttu-id="3de88-334">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="3de88-334">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="3de88-335">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-335">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="3de88-336">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-336">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="3de88-337">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-337">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="3de88-338">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="3de88-338">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="3de88-339">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="3de88-339">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="3de88-340">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="3de88-340">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="3de88-341">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="3de88-341">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="3de88-342">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="3de88-342">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)
