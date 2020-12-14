---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 7df3375d547b696d67c44462142d592e6047ac63
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709186"
---
# <span data-ttu-id="6ea5c-102">Get-Job</span><span class="sxs-lookup"><span data-stu-id="6ea5c-102">Get-Job</span></span>

## <span data-ttu-id="6ea5c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6ea5c-103">SYNOPSIS</span></span>
<span data-ttu-id="6ea5c-104">Hämtar PowerShell-bakgrunds jobb som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-104">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="6ea5c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ea5c-105">SYNTAX</span></span>

### <span data-ttu-id="6ea5c-106">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6ea5c-106">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="6ea5c-107">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ea5c-107">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="6ea5c-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ea5c-108">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6ea5c-109">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ea5c-109">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="6ea5c-110">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ea5c-110">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="6ea5c-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ea5c-111">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="6ea5c-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6ea5c-112">DESCRIPTION</span></span>

<span data-ttu-id="6ea5c-113">`Get-Job`Cmdleten hämtar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-113">The `Get-Job` cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="6ea5c-114">Du kan använda `Get-Job` för att hämta jobb som har startats med hjälp av `Start-Job` cmdleten, eller genom att använda parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-114">You can use `Get-Job` to get jobs that were started by using the `Start-Job` cmdlet, or by using the **AsJob** parameter of any cmdlet.</span></span>

<span data-ttu-id="6ea5c-115">Utan parametrar hämtar ett- `Get-Job` kommando alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-115">Without parameters, a `Get-Job` command gets all jobs in the current session.</span></span> <span data-ttu-id="6ea5c-116">Du kan använda parametrarna för `Get-Job` för att hämta specifika jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-116">You can use the parameters of `Get-Job` to get particular jobs.</span></span>

<span data-ttu-id="6ea5c-117">Jobbobjektet som `Get-Job` returnerar innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-117">The job object that `Get-Job` returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="6ea5c-118">Använd cmdleten för att hämta resultatet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-118">To get the results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="6ea5c-119">Ett Windows PowerShell-bakgrunds jobb är ett kommando som körs i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-119">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="6ea5c-120">Normalt använder du ett bakgrunds jobb för att köra ett komplicerat kommando som tar lång tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-120">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="6ea5c-121">Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-121">For more information about background jobs in Windows PowerShell, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="6ea5c-122">Från och med Windows PowerShell 3,0 `Get-Job` hämtar cmdlet: en även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-122">Beginning in Windows PowerShell 3.0, the `Get-Job` cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="6ea5c-123">Om du vill hitta jobb typen för ett jobb använder du jobbets egenskap **PSJobTypeName** .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-123">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="6ea5c-124">Om du vill aktivera `Get-Job` en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Get-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-124">To enable `Get-Job` to get a custom job type, import the module that supports the custom job type into the session before you run a `Get-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="6ea5c-125">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-125">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="6ea5c-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6ea5c-126">EXAMPLES</span></span>

### <span data-ttu-id="6ea5c-127">Exempel 1: Hämta alla bakgrunds jobb som startats i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="6ea5c-127">Example 1: Get all background jobs started in the current session</span></span>

<span data-ttu-id="6ea5c-128">Det här kommandot hämtar alla bakgrunds jobb som startats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-128">This command gets all background jobs started in the current session.</span></span> <span data-ttu-id="6ea5c-129">Den omfattar inte jobb som skapats i andra sessioner, även om jobben körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-129">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

```
PS C:\> Get-Job
```

### <span data-ttu-id="6ea5c-130">Exempel 2: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="6ea5c-130">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="6ea5c-131">De här kommandona visar hur du hämtar instans-ID för ett jobb och sedan använder det för att stoppa ett jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-131">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span> <span data-ttu-id="6ea5c-132">Till skillnad från namnet på ett jobb, som inte är unikt, är instans-ID: t unikt.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-132">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

<span data-ttu-id="6ea5c-133">Det första kommandot använder `Get-Job` cmdleten för att hämta ett jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-133">The first command uses the `Get-Job` cmdlet to get a job.</span></span> <span data-ttu-id="6ea5c-134">Parametern **Name** används för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-134">It uses the **Name** parameter to identify the job.</span></span> <span data-ttu-id="6ea5c-135">Kommandot lagrar jobbobjektet som `Get-Job` returneras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-135">The command stores the job object that `Get-Job` returns in the `$j` variable.</span></span> <span data-ttu-id="6ea5c-136">I det här exemplet finns det bara ett jobb med det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-136">In this example, there is only one job with the specified name.</span></span> <span data-ttu-id="6ea5c-137">Det andra kommandot hämtar **InstanceID** -egenskapen för objektet i `$j` variabeln och lagrar det i `$ID` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-137">The second command gets the **InstanceId** property of the object in the `$j` variable and stores it in the `$ID` variable.</span></span> <span data-ttu-id="6ea5c-138">Det tredje kommandot visar värdet för `$ID` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-138">The third command displays the value of the `$ID` variable.</span></span> <span data-ttu-id="6ea5c-139">Det fjärde kommandot använder `Stop-Job` cmdleten för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-139">The fourth command uses `Stop-Job` cmdlet to stop the job.</span></span>
<span data-ttu-id="6ea5c-140">Parametern **InstanceID** används för att identifiera jobbet och `$ID` variabeln som representerar JOBBETS instans-ID.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-140">It uses the **InstanceId** parameter to identify the job and `$ID` variable to represent the instance ID of the job.</span></span>

```
PS C:\> $j = Get-Job -Name Job1
PS C:\> $ID = $j.InstanceID
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

PS C:\> Stop-Job -InstanceId $ID
```

### <span data-ttu-id="6ea5c-141">Exempel 3: Hämta jobb som innehåller ett speciellt kommando</span><span class="sxs-lookup"><span data-stu-id="6ea5c-141">Example 3: Get jobs that include a specific command</span></span>

<span data-ttu-id="6ea5c-142">Det här kommandot hämtar jobben i systemet som innehåller ett `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-142">This command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="6ea5c-143">Kommandot använder **kommando** parametern för `Get-Job` att begränsa de hämtade jobben.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-143">The command uses the **Command** parameter of `Get-Job` to limit the jobs retrieved.</span></span> <span data-ttu-id="6ea5c-144">Kommandot använder jokertecken ( `*` ) för att hämta jobb som innehåller ett `Get-Process` kommando var som helst i kommando strängen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-144">The command uses wildcard characters (`*`) to get jobs that include a `Get-Process` command anywhere in the command string.</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

### <span data-ttu-id="6ea5c-145">Exempel 4: Hämta jobb som innehåller ett speciellt kommando med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="6ea5c-145">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

<span data-ttu-id="6ea5c-146">Precis som kommandot i föregående exempel hämtar det här kommandot jobben i systemet som innehåller ett `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-146">Like the command in the previous example, this command gets the jobs on the system that include a `Get-Process` command.</span></span> <span data-ttu-id="6ea5c-147">Kommandot använder en pipeline-operator ( `|` ) för att skicka en sträng, inom citat tecken, till `Get-Job` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-147">The command uses a pipeline operator (`|`) to send a string, in quotation marks, to the `Get-Job` cmdlet.</span></span> <span data-ttu-id="6ea5c-148">Det motsvarar föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-148">It is the equivalent of the previous command.</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

### <span data-ttu-id="6ea5c-149">Exempel 5: Hämta jobb som inte har startats</span><span class="sxs-lookup"><span data-stu-id="6ea5c-149">Example 5: Get jobs that have not been started</span></span>

<span data-ttu-id="6ea5c-150">Det här kommandot hämtar bara de jobb som har skapats men som ännu inte har startats.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-150">This command gets only those jobs that have been created but have not yet been started.</span></span> <span data-ttu-id="6ea5c-151">Detta inkluderar jobb som är schemalagda att köras i framtiden och som ännu inte har schemalagts.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-151">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

```
PS C:\> Get-Job -State NotStarted
```

### <span data-ttu-id="6ea5c-152">Exempel 6: Hämta jobb som inte har tilldelats ett namn</span><span class="sxs-lookup"><span data-stu-id="6ea5c-152">Example 6: Get jobs that have not been assigned a name</span></span>

<span data-ttu-id="6ea5c-153">Det här kommandot hämtar alla jobb som har jobb namn som börjar med jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-153">This command gets all jobs that have job names that begin with job.</span></span> <span data-ttu-id="6ea5c-154">Eftersom `job<number>` är standard namnet för ett jobb, hämtar det här kommandot alla jobb som inte har något uttryckligen tilldelat namn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-154">Because `job<number>` is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

```
PS C:\> Get-Job -Name Job*
```

### <span data-ttu-id="6ea5c-155">Exempel 7: Använd ett jobb objekt för att representera jobbet i ett kommando</span><span class="sxs-lookup"><span data-stu-id="6ea5c-155">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="6ea5c-156">Det här exemplet visar hur du använder `Get-Job` för att hämta ett jobb objekt, och sedan visar det hur du använder jobbobjektet för att representera jobbet i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-156">This example shows how to use `Get-Job` to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

<span data-ttu-id="6ea5c-157">Det första kommandot använder `Start-Job` cmdleten för att starta ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-157">The first command uses the `Start-Job` cmdlet to start a background job that runs a `Get-Process` command on the local computer.</span></span> <span data-ttu-id="6ea5c-158">Kommandot använder **Name** -parametern för `Start-Job` att tilldela jobbet ett eget namn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-158">The command uses the **Name** parameter of `Start-Job` to assign a friendly name to the job.</span></span> <span data-ttu-id="6ea5c-159">Det andra kommandot använder `Get-Job` för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-159">The second command uses `Get-Job` to get the job.</span></span> <span data-ttu-id="6ea5c-160">Den använder **Name** -parametern för `Get-Job` att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-160">It uses the **Name** parameter of `Get-Job` to identify the job.</span></span> <span data-ttu-id="6ea5c-161">Kommandot sparar det resulterande jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-161">The command saves the resulting job object in the `$j` variable.</span></span> <span data-ttu-id="6ea5c-162">Det tredje kommandot visar värdet för jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-162">The third command displays the value of the job object in the `$j` variable.</span></span> <span data-ttu-id="6ea5c-163">Värdet för egenskapen **State** visar att jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-163">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="6ea5c-164">Värdet för egenskapen **HasMoreData** visar att det finns resultat som är tillgängliga från jobbet som ännu inte har hämtats.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-164">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span> <span data-ttu-id="6ea5c-165">Det fjärde kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-165">The fourth command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="6ea5c-166">Objektet används i `$j` variabeln för att representera jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-166">It uses the job object in the `$j` variable to represent the job.</span></span> <span data-ttu-id="6ea5c-167">Du kan också använda en pipeline-operator för att skicka ett jobb objekt till `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-167">You can also use a pipeline operator to send a job object to `Receive-Job`.</span></span>

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


### <span data-ttu-id="6ea5c-168">Exempel 8: Hämta alla jobb inklusive jobb som har startats med en annan metod</span><span class="sxs-lookup"><span data-stu-id="6ea5c-168">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="6ea5c-169">Det här exemplet visar att `Get-Job` cmdleten kan hämta alla jobb som startades i den aktuella sessionen, även om de startades med hjälp av olika metoder.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-169">This example demonstrates that the `Get-Job` cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

<span data-ttu-id="6ea5c-170">Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-170">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="6ea5c-171">Det andra kommandot använder **AsJob** -parametern för `Invoke-Command` cmdleten för att starta ett jobb på S1-datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-171">The second command uses the **AsJob** parameter of the `Invoke-Command` cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="6ea5c-172">Även om kommandona i jobbet körs på fjärrdatorn skapas jobbobjektet på den lokala datorn, så du kan använda lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-172">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span> <span data-ttu-id="6ea5c-173">Det tredje kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på S2-datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-173">The third command uses the `Invoke-Command` cmdlet to run a `Start-Job` command on the S2 computer.</span></span> <span data-ttu-id="6ea5c-174">Med den här metoden skapas jobbobjektet på fjärrdatorn, så du kan använda fjärrkommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-174">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span> <span data-ttu-id="6ea5c-175">Det fjärde kommandot använder `Get-Job` för att hämta jobb som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-175">The fourth command uses `Get-Job` to get the jobs stored on the local computer.</span></span> <span data-ttu-id="6ea5c-176">Egenskapen **PSJobTypeName** för jobb, som introducerades i Windows PowerShell 3,0, visar att det lokala jobbet som startades med hjälp av `Start-Job` cmdleten är ett bakgrunds jobb och att jobbet startade i en fjärrsession med hjälp av `Invoke-Command` cmdleten är ett Fjärrjobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-176">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the `Start-Job` cmdlet is a background job and the job started in a remote session by using the `Invoke-Command` cmdlet is a remote job.</span></span> <span data-ttu-id="6ea5c-177">Det femte kommandot använder `Invoke-Command` för att köra ett `Get-Job` kommando på S2-datorn. Exempel resultatet visar resultatet av `Get-Job` kommandot.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-177">The fifth command uses `Invoke-Command` to run a `Get-Job` command on the S2 computer.The sample output shows the results of the `Get-Job` command.</span></span> <span data-ttu-id="6ea5c-178">På S2-datorn verkar jobbet vara ett lokalt jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-178">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="6ea5c-179">Dator namnet är localhost och jobb typen är ett bakgrunds jobb. Mer information om hur du kör bakgrunds jobb på fjärrdatorer finns [about_Remote_Jobs](./about/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-179">The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see [about_Remote_Jobs](./about/about_Remote_Jobs.md).</span></span>

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

### <span data-ttu-id="6ea5c-180">Exempel 9: Undersök ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-180">Example 9: Investigate a failed job</span></span>

<span data-ttu-id="6ea5c-181">Det här kommandot visar hur du använder jobbobjektet som `Get-Job` returnerar för att undersöka varför ett jobb har misslyckats.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-181">This command shows how to use the job object that `Get-Job` returns to investigate why a job failed.</span></span>
<span data-ttu-id="6ea5c-182">Det visar också hur du hämtar de underordnade jobben för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-182">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="6ea5c-183">Det första kommandot använder `Start-Job` cmdleten för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-183">The first command uses the `Start-Job` cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="6ea5c-184">Jobbobjektet som `Start-Job` returnerar visar att jobbet misslyckades.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-184">The job object that `Start-Job` returns shows that the job failed.</span></span> <span data-ttu-id="6ea5c-185">Det gick inte att **Ange värdet för tillstånds** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-185">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="6ea5c-186">Det andra kommandot använder `Get-Job` cmdleten för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-186">The second command uses the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="6ea5c-187">Kommandot använder punkt metoden för att hämta värdet för objektets **JobStateInfo** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-187">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="6ea5c-188">Den använder en pipeline-operator för att skicka objektet i egenskapen **JobStateInfo** till `Format-List` cmdleten, som formaterar alla egenskaper för objektet ( `*` ) i en lista. Resultatet av `Format-List` kommandot visar att värdet för jobbets **orsaks** egenskap är tomt.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-188">It uses a pipeline operator to send the object in the **JobStateInfo** property to the `Format-List` cmdlet, which formats all of the properties of the object (`*`) in a list.The result of the `Format-List` command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="6ea5c-189">Det tredje kommandot undersöker mer.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-189">The third command investigates more.</span></span> <span data-ttu-id="6ea5c-190">Det använder ett `Get-Job` kommando för att hämta jobbet och använder sedan en pipeline-operator för att skicka hela jobbobjektet till `Format-List` cmdleten, som visar alla egenskaper för jobbet i en lista. Visningen av alla egenskaper i jobbobjektet visar att jobbet innehåller ett underordnat jobb med namnet Job2.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-190">It uses a `Get-Job` command to get the job and then uses a pipeline operator to send the whole job object to the `Format-List` cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="6ea5c-191">Det fjärde kommandot använder `Get-Job` för att hämta jobbobjektet som representerar det underordnade Job2-jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-191">The fourth command uses `Get-Job` to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="6ea5c-192">Det här är det jobb där kommandot faktiskt kördes.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-192">This is the job in which the command actually ran.</span></span> <span data-ttu-id="6ea5c-193">Metoden dot används för att hämta egenskapen **orsak** för egenskapen **JobStateInfo** . Resultatet visar att jobbet misslyckades på grund av ett nekat åtkomst fel.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-193">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="6ea5c-194">I det här fallet har användaren glömt att använda alternativet Kör som administratör när Windows PowerShell startades. eftersom bakgrunds jobb använder funktionerna för fjärr kommunikation i Windows PowerShell måste datorn konfigureras för fjärr kommunikation för att köra ett jobb, även när jobbet körs på den lokala datorn. Information om krav för fjärr kommunikation i Windows PowerShell finns [about_Remote_Requirements](./about/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-194">In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see [about_Remote_Requirements](./about/about_Remote_Requirements.md).</span></span> <span data-ttu-id="6ea5c-195">Fel söknings tips finns i [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-195">For troubleshooting tips, see [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md).</span></span>

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

### <span data-ttu-id="6ea5c-196">Exempel 10: hämta filtrerade resultat</span><span class="sxs-lookup"><span data-stu-id="6ea5c-196">Example 10: Get filtered results</span></span>

<span data-ttu-id="6ea5c-197">Det här exemplet visar hur du använder **filter** parametern för att hämta ett arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-197">This example shows how to use the **Filter** parameter to get a workflow job.</span></span> <span data-ttu-id="6ea5c-198">**Filter** parametern, som introducerades i Windows PowerShell 3,0, är bara giltig för anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-198">The **Filter** parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

<span data-ttu-id="6ea5c-199">Det första kommandot använder **arbets flödets** nyckelord för att skapa WFProcess-arbetsflödet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-199">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span> <span data-ttu-id="6ea5c-200">Det andra kommandot använder parametern **AsJob** i WFProcess-arbetsflödet för att köra arbets flödet som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-200">The second command uses the **AsJob** parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="6ea5c-201">Den använder parametern **JobName** i arbets flödet för att ange ett namn för jobbet och parametern **PSPrivateMetadata** för arbets flödet för att ange ett anpassat ID.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-201">It uses the **JobName** parameter of the workflow to specify a name for the job, and the **PSPrivateMetadata** parameter of the workflow to specify a custom ID.</span></span> <span data-ttu-id="6ea5c-202">Det tredje kommandot använder **filter** parametern för `Get-Job` för att hämta jobbet efter anpassat ID som angavs i parametern **PSPrivateMetadata** .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-202">The third command uses the **Filter** parameter of `Get-Job` to get the job by custom ID that was specified in the **PSPrivateMetadata** parameter.</span></span>

```
PS C:\> Workflow WFProcess {Get-Process}
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

### <span data-ttu-id="6ea5c-203">Exempel 11: Hämta information om underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-203">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="6ea5c-204">I det här exemplet visas effekterna av att använda parametrarna **IncludeChildJob** och **ChildJobState** för `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-204">This example shows the effect of using the **IncludeChildJob** and **ChildJobState** parameters of the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="6ea5c-205">Det första kommandot hämtar jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-205">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="6ea5c-206">Utdata innehåller ett bakgrunds jobb, ett Fjärrjobb och flera instanser av ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-206">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="6ea5c-207">Fjärrjobbet, Job4, verkar ha misslyckats.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-207">The remote job, Job4, appears to have failed.</span></span>
<span data-ttu-id="6ea5c-208">Det andra kommandot använder parametern **IncludeChildJob** i `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-208">The second command uses the **IncludeChildJob** parameter of `Get-Job`.</span></span> <span data-ttu-id="6ea5c-209">Utdata lägger till de underordnade jobben för alla jobb som har underordnade jobb. I det här fallet visar den ändrade utmatningen att endast det Job5 underordnade jobbet för Job4 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-209">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span> <span data-ttu-id="6ea5c-210">Det tredje kommandot använder parametern **ChildJobState** med värdet misslyckades. utdata innehåller alla överordnade jobb och endast de underordnade jobb som misslyckades.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-210">The third command uses the **ChildJobState** parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span> <span data-ttu-id="6ea5c-211">Det femte kommandot använder egenskapen **JobStateInfo** för jobb och dess **orsaks** egenskap för att upptäcka varför Job5 misslyckades.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-211">The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

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

<span data-ttu-id="6ea5c-212">Mer information finns i hjälp avsnittet för [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-212">For more information, see the [about_Remote_Troubleshooting](./about/about_Remote_Troubleshooting.md) Help topic.</span></span>

## <span data-ttu-id="6ea5c-213">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6ea5c-213">PARAMETERS</span></span>

### <span data-ttu-id="6ea5c-214">– Efter</span><span class="sxs-lookup"><span data-stu-id="6ea5c-214">-After</span></span>

<span data-ttu-id="6ea5c-215">Hämtar slutförda jobb som avslutas efter angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="6ea5c-216">Ange ett **datetime** -objekt, till exempel ett som returneras av `Get-Date` cmdleten eller en sträng som kan konverteras till ett **datetime** -objekt, till exempel `Dec 1, 2012 2:00 AM` eller `11/06` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-216">Enter a **DateTime** object, such as one returned by the `Get-Date` cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="6ea5c-217">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="6ea5c-218">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-218">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6ea5c-219">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="6ea5c-220">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-221">– Före</span><span class="sxs-lookup"><span data-stu-id="6ea5c-221">-Before</span></span>

<span data-ttu-id="6ea5c-222">Hämtar slutförda jobb som slutade före det angivna datumet och den angivna tiden.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-222">Gets completed jobs that ended before the specified date and time.</span></span> <span data-ttu-id="6ea5c-223">Ange ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="6ea5c-224">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb som **har en slut** tid-egenskap.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="6ea5c-225">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-225">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6ea5c-226">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="6ea5c-227">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="6ea5c-228">-ChildJobState</span></span>

<span data-ttu-id="6ea5c-229">Hämtar endast de underordnade jobb som har det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-229">Gets only the child jobs that have the specified state.</span></span> <span data-ttu-id="6ea5c-230">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6ea5c-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6ea5c-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6ea5c-231">NotStarted</span></span>
- <span data-ttu-id="6ea5c-232">Körs</span><span class="sxs-lookup"><span data-stu-id="6ea5c-232">Running</span></span>
- <span data-ttu-id="6ea5c-233">Slutförd</span><span class="sxs-lookup"><span data-stu-id="6ea5c-233">Completed</span></span>
- <span data-ttu-id="6ea5c-234">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-234">Failed</span></span>
- <span data-ttu-id="6ea5c-235">Stoppad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-235">Stopped</span></span>
- <span data-ttu-id="6ea5c-236">Blockerad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-236">Blocked</span></span>
- <span data-ttu-id="6ea5c-237">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-237">Suspended</span></span>
- <span data-ttu-id="6ea5c-238">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-238">Disconnected</span></span>
- <span data-ttu-id="6ea5c-239">Pausar</span><span class="sxs-lookup"><span data-stu-id="6ea5c-239">Suspending</span></span>
- <span data-ttu-id="6ea5c-240">Stoppas</span><span class="sxs-lookup"><span data-stu-id="6ea5c-240">Stopping</span></span>

<span data-ttu-id="6ea5c-241">Som standard `Get-Job` får inte underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-241">By default, `Get-Job` does not get child jobs.</span></span> <span data-ttu-id="6ea5c-242">Med hjälp av parametern **IncludeChildJob** `Get-Job` hämtar du alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-242">By using the **IncludeChildJob** parameter, `Get-Job` gets all child jobs.</span></span> <span data-ttu-id="6ea5c-243">Om du använder parametern **ChildJobState** har parametern **IncludeChildJob** ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-243">If you use the **ChildJobState** parameter, the **IncludeChildJob** parameter has no effect.</span></span>

<span data-ttu-id="6ea5c-244">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-245">-Kommando</span><span class="sxs-lookup"><span data-stu-id="6ea5c-245">-Command</span></span>

<span data-ttu-id="6ea5c-246">Anger en matris med kommandon som strängar.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-246">Specifies an array of commands as strings.</span></span> <span data-ttu-id="6ea5c-247">Denna cmdlet hämtar de jobb som innehåller de angivna kommandona.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-247">This cmdlet gets the jobs that include the specified commands.</span></span> <span data-ttu-id="6ea5c-248">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-248">The default is all jobs.</span></span> <span data-ttu-id="6ea5c-249">Du kan använda jokertecken för att ange ett kommando mönster.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-249">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="6ea5c-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="6ea5c-250">-Filter</span></span>

<span data-ttu-id="6ea5c-251">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-251">Specifies a hash table of conditions.</span></span> <span data-ttu-id="6ea5c-252">Denna cmdlet hämtar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="6ea5c-253">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="6ea5c-254">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="6ea5c-255">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-255">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6ea5c-256">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="6ea5c-257">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="6ea5c-258">-HasMoreData</span></span>

<span data-ttu-id="6ea5c-259">Indikerar om denna cmdlet endast hämtar jobb som har angivet värde för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="6ea5c-260">Egenskapen **HasMoreData** anger om alla jobb resultat har tagits emot i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span> <span data-ttu-id="6ea5c-261">Ange ett värde för om du vill hämta jobb som har fler resultat `$True` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-261">To get jobs that have more results, specify a value of `$True`.</span></span> <span data-ttu-id="6ea5c-262">Ange ett värde för om du vill hämta jobb som inte har fler resultat `$False` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-262">To get jobs that do not have more results, specify a value of `$False`.</span></span>

<span data-ttu-id="6ea5c-263">Använd cmdleten för att hämta resultatet av ett jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-263">To get the results of a job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="6ea5c-264">När du använder `Receive-Job` cmdleten tas den bort från dess minnes intern, sessionsbaserade lagrings utrymme som returneras.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-264">When you use the `Receive-Job` cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="6ea5c-265">När det har returnerat alla resultat från jobbet i den aktuella sessionen anges värdet för **HasMoreData** -egenskapen för jobbet till `$False` ) för att indikera att det inte har några fler resultat för jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to `$False`) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="6ea5c-266">Använd parametern **Behåll** för `Receive-Job` att förhindra `Receive-Job` borttagning av resultat och ändra värdet för egenskapen **HasMoreData** .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-266">Use the **Keep** parameter of `Receive-Job` to prevent `Receive-Job` from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="6ea5c-267">För mer information ange `Get-Help Receive-Job`.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="6ea5c-268">Egenskapen **HasMoreData** är unik för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="6ea5c-269">Om resultat för en anpassad Jobbtyp sparas utanför sessionen, till exempel den schemalagda jobbtyp som sparar jobb resultat på disk, kan du använda `Receive-Job` cmdleten i en annan session för att hämta jobb resultatet igen, även om värdet för **HasMoreData** är `$False` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the `Receive-Job` cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is `$False`.</span></span> <span data-ttu-id="6ea5c-270">Mer information finns i hjälp avsnitten för den anpassade jobb typen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="6ea5c-271">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-272">-ID</span><span class="sxs-lookup"><span data-stu-id="6ea5c-272">-Id</span></span>

<span data-ttu-id="6ea5c-273">Anger en matris med ID: n för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="6ea5c-274">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-274">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="6ea5c-275">Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="6ea5c-276">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-276">You can type one or more IDs separated by commas.</span></span> <span data-ttu-id="6ea5c-277">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="6ea5c-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="6ea5c-278">-IncludeChildJob</span></span>

<span data-ttu-id="6ea5c-279">Anger att den här cmdleten Returnerar underordnade jobb, förutom överordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="6ea5c-280">Den här parametern är särskilt användbar för att undersöka arbets flödes jobb, som `Get-Job` returnerar ett överordnat jobb och jobb haveri, eftersom orsaken till felet har sparats i en egenskap för det underordnade jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-280">This parameter is especially useful for investigating workflow jobs, for which `Get-Job` returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="6ea5c-281">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6ea5c-282">-InstanceId</span></span>

<span data-ttu-id="6ea5c-283">Anger en matris med instans-ID för jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span> <span data-ttu-id="6ea5c-284">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-284">The default is all jobs.</span></span>

<span data-ttu-id="6ea5c-285">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="6ea5c-286">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-286">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="6ea5c-287">-Name</span><span class="sxs-lookup"><span data-stu-id="6ea5c-287">-Name</span></span>

<span data-ttu-id="6ea5c-288">Anger en matris med informativa namn på jobb som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span> <span data-ttu-id="6ea5c-289">Ange ett jobbnamn eller Använd jokertecken för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span> <span data-ttu-id="6ea5c-290">Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-290">By default, `Get-Job` gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="6ea5c-291">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="6ea5c-291">-Newest</span></span>

<span data-ttu-id="6ea5c-292">Anger ett antal jobb som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-292">Specifies a number of jobs to get.</span></span> <span data-ttu-id="6ea5c-293">Denna cmdlet hämtar de jobb som avslutades senast.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="6ea5c-294">Den **senaste** parametern kan inte sortera eller returnera de senaste jobben i slut tid.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-294">The **Newest** parameter does not sort or return the newest jobs in end-time order.</span></span> <span data-ttu-id="6ea5c-295">Använd cmdleten för att sortera utdata `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-295">To sort the output, use the `Sort-Object` cmdlet.</span></span>

<span data-ttu-id="6ea5c-296">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6ea5c-297">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="6ea5c-297">-State</span></span>

<span data-ttu-id="6ea5c-298">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-298">Specifies a job state.</span></span> <span data-ttu-id="6ea5c-299">Denna cmdlet hämtar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-299">This cmdlet gets only jobs in the specified state.</span></span> <span data-ttu-id="6ea5c-300">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6ea5c-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6ea5c-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6ea5c-301">NotStarted</span></span>
- <span data-ttu-id="6ea5c-302">Körs</span><span class="sxs-lookup"><span data-stu-id="6ea5c-302">Running</span></span>
- <span data-ttu-id="6ea5c-303">Slutförd</span><span class="sxs-lookup"><span data-stu-id="6ea5c-303">Completed</span></span>
- <span data-ttu-id="6ea5c-304">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-304">Failed</span></span>
- <span data-ttu-id="6ea5c-305">Stoppad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-305">Stopped</span></span>
- <span data-ttu-id="6ea5c-306">Blockerad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-306">Blocked</span></span>
- <span data-ttu-id="6ea5c-307">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-307">Suspended</span></span>
- <span data-ttu-id="6ea5c-308">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="6ea5c-308">Disconnected</span></span>
- <span data-ttu-id="6ea5c-309">Pausar</span><span class="sxs-lookup"><span data-stu-id="6ea5c-309">Suspending</span></span>
- <span data-ttu-id="6ea5c-310">Stoppas</span><span class="sxs-lookup"><span data-stu-id="6ea5c-310">Stopping</span></span>

<span data-ttu-id="6ea5c-311">Som standard `Get-Job` hämtar alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-311">By default, `Get-Job` gets all the jobs in the current session.</span></span>

<span data-ttu-id="6ea5c-312">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-312">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="6ea5c-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ea5c-313">CommonParameters</span></span>

<span data-ttu-id="6ea5c-314">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ea5c-315">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6ea5c-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ea5c-316">INDATA</span><span class="sxs-lookup"><span data-stu-id="6ea5c-316">INPUTS</span></span>

### <span data-ttu-id="6ea5c-317">Inga</span><span class="sxs-lookup"><span data-stu-id="6ea5c-317">None</span></span>

<span data-ttu-id="6ea5c-318">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6ea5c-319">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6ea5c-319">OUTPUTS</span></span>

### <span data-ttu-id="6ea5c-320">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="6ea5c-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="6ea5c-321">Denna cmdlet returnerar objekt som representerar jobben i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="6ea5c-322">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6ea5c-322">NOTES</span></span>

<span data-ttu-id="6ea5c-323">**PSJobTypeName** -egenskapen för jobb anger jobb typen för jobbet.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="6ea5c-324">Egenskap svärdet bestäms av jobb typ författaren.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="6ea5c-325">I följande lista visas vanliga jobb typer.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-325">The following list shows common job types.</span></span>

- <span data-ttu-id="6ea5c-326">**BackgroundJob**.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-326">**BackgroundJob**.</span></span> <span data-ttu-id="6ea5c-327">Lokalt jobb har startats med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ea5c-327">Local job started by using `Start-Job`.</span></span>
- <span data-ttu-id="6ea5c-328">**RemoteJob**.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-328">**RemoteJob**.</span></span> <span data-ttu-id="6ea5c-329">Jobbet startade i en **PSSession** med hjälp av parametern **AsJob** för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-329">Job started in a **PSSession** by using the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span>
- <span data-ttu-id="6ea5c-330">**PSWorkflowJob**.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-330">**PSWorkflowJob**.</span></span> <span data-ttu-id="6ea5c-331">Jobbet startades med **AsJob** gemensamma parameter för arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="6ea5c-331">Job started by using the **AsJob** common parameter of workflows.</span></span>

## <span data-ttu-id="6ea5c-332">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6ea5c-332">RELATED LINKS</span></span>

[<span data-ttu-id="6ea5c-333">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="6ea5c-333">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6ea5c-334">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-334">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="6ea5c-335">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-335">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="6ea5c-336">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-336">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="6ea5c-337">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="6ea5c-337">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="6ea5c-338">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="6ea5c-338">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="6ea5c-339">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="6ea5c-339">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="6ea5c-340">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="6ea5c-340">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="6ea5c-341">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="6ea5c-341">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)
