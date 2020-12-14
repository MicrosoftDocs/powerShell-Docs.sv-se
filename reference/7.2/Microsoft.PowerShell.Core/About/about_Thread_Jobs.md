---
description: Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 88880a6c58ddc02d7b35a44af7169f6c5af19a10
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710212"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="8a791-104">Om tråd jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-104">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="8a791-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="8a791-105">Short description</span></span>

<span data-ttu-id="8a791-106">Innehåller information om PowerShell Thread-baserade jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-106">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="8a791-107">Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8a791-107">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="8a791-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="8a791-108">Long description</span></span>

<span data-ttu-id="8a791-109">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="8a791-109">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="8a791-110">Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="8a791-110">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="8a791-111">`RemoteJob` -Kommandon och skript körs i en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="8a791-111">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="8a791-112">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8a791-112">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="8a791-113">`BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8a791-113">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="8a791-114">Mer information finns i artikeln [om jobb](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8a791-114">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="8a791-115">`PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8a791-115">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="8a791-116">Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar.</span><span class="sxs-lookup"><span data-stu-id="8a791-116">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="8a791-117">Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.</span><span class="sxs-lookup"><span data-stu-id="8a791-117">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="8a791-118">Trådbaserade jobb kräver dock mindre kostnader.</span><span class="sxs-lookup"><span data-stu-id="8a791-118">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="8a791-119">De använder inte Remoting-skiktet eller serialiseringen.</span><span class="sxs-lookup"><span data-stu-id="8a791-119">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="8a791-120">Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8a791-120">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="8a791-121">Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.</span><span class="sxs-lookup"><span data-stu-id="8a791-121">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a791-122">Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data.</span><span class="sxs-lookup"><span data-stu-id="8a791-122">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="8a791-123">Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="8a791-123">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="8a791-124">Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="8a791-124">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="8a791-125">Det finns två sätt att komma runt den här situationen:</span><span class="sxs-lookup"><span data-stu-id="8a791-125">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="8a791-126">Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="8a791-126">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="8a791-127">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="8a791-127">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="8a791-128">Använd `Start-Process` för att skapa en ny process i stället för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-128">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="8a791-129">Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="8a791-129">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="8a791-130">Starta och hantera trådbaserade jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-130">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="8a791-131">Det finns två sätt att starta trådbaserade jobb:</span><span class="sxs-lookup"><span data-stu-id="8a791-131">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="8a791-132">`Start-ThreadJob` – från **ThreadJob** -modulen</span><span class="sxs-lookup"><span data-stu-id="8a791-132">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="8a791-133">`ForEach-Object -Parallel -AsJob` -Parallel-funktionen har lagts till i PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="8a791-133">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="8a791-134">Använd samma **jobb** -cmdlets som beskrivs i [about_Jobs](about_Jobs.md) för att hantera trådbaserade jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-134">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="8a791-135">Använda `Start-ThreadJob`</span><span class="sxs-lookup"><span data-stu-id="8a791-135">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="8a791-136">**ThreadJob** -modulen levererades först med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="8a791-136">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="8a791-137">Den kan också installeras från PowerShell-galleriet för Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="8a791-137">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="8a791-138">Om du vill starta ett tråd jobb på den lokala datorn använder du `Start-ThreadJob` cmdleten med ett kommando eller ett skript som omges av klammerparenteser ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="8a791-138">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="8a791-139">I följande exempel startar ett tråd jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8a791-139">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="8a791-140">`Start-ThreadJob`Kommandot returnerar ett `ThreadJob` objekt som representerar det jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="8a791-140">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="8a791-141">Jobbobjektet innehåller användbar information om jobbet, inklusive dess aktuella status för körning.</span><span class="sxs-lookup"><span data-stu-id="8a791-141">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="8a791-142">Resultatet av jobbet samlas in när resultatet genereras.</span><span class="sxs-lookup"><span data-stu-id="8a791-142">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="8a791-143">Använda `ForEach-Object -Parallel -AsJob`</span><span class="sxs-lookup"><span data-stu-id="8a791-143">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="8a791-144">PowerShell 7,0 har lagt till en ny parameter uppsättning till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8a791-144">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="8a791-145">Med de nya parametrarna kan du köra skript block i parallella trådar som PowerShell-jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-145">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="8a791-146">Du kan skicka pipe-data till `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="8a791-146">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="8a791-147">Data skickas till skript blocket som körs parallellt.</span><span class="sxs-lookup"><span data-stu-id="8a791-147">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="8a791-148">`-AsJob`Parametern skapar jobb objekt för var och en av de parallella trådarna.</span><span class="sxs-lookup"><span data-stu-id="8a791-148">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="8a791-149">Följande kommando startar ett jobb som innehåller underordnade jobb för varje indatavärde skickas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="8a791-149">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="8a791-150">Varje underordnat jobb kör `Write-Output` kommandot med ett skickas-indatavärde som argument.</span><span class="sxs-lookup"><span data-stu-id="8a791-150">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="8a791-151">`ForEach-Object -Parallel`Kommandot returnerar ett `PSTaskJob` objekt som innehåller underordnade jobb för varje skickas-indatavärde.</span><span class="sxs-lookup"><span data-stu-id="8a791-151">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="8a791-152">Jobbobjektet innehåller användbar information om de underordnade jobb som kör status.</span><span class="sxs-lookup"><span data-stu-id="8a791-152">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="8a791-153">Resultatet av de underordnade jobben samlas in när resultaten genereras.</span><span class="sxs-lookup"><span data-stu-id="8a791-153">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="8a791-154">Vänta tills ett jobb har slutförts och hämta jobb resultat</span><span class="sxs-lookup"><span data-stu-id="8a791-154">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="8a791-155">Du kan använda PowerShell-jobbets cmdlets, till exempel `Wait-Job` och `Receive-Job` för att vänta tills ett jobb har slutförts och sedan returnera alla resultat som genereras av jobbet.</span><span class="sxs-lookup"><span data-stu-id="8a791-155">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="8a791-156">Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando och väntar sedan på att kommandot ska slutföras och returnerar slutligen alla data resultat som genereras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="8a791-156">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="8a791-157">Följande kommando startar ett jobb som kör ett `Write-Output` kommando för varje skickas-indata och väntar sedan på att alla underordnade jobb ska slutföras och returnerar slutligen alla data resultat som har genererats av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="8a791-157">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="8a791-158">`Receive-Job`Cmdleten returnerar resultatet av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="8a791-158">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="8a791-159">Eftersom varje underordnat jobb körs parallellt, garanteras inte ordningen på de genererade resultaten.</span><span class="sxs-lookup"><span data-stu-id="8a791-159">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="8a791-160">Prestanda för tråd jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-160">Thread job performance</span></span>

<span data-ttu-id="8a791-161">Tråd jobb är snabbare och lättare att få högre vikt än andra typer av jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-161">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="8a791-162">Men de har fortfarande överkapaciteter som kan vara stora jämfört med arbete som utförs av jobbet.</span><span class="sxs-lookup"><span data-stu-id="8a791-162">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="8a791-163">PowerShell kör kommandon och skript i en session.</span><span class="sxs-lookup"><span data-stu-id="8a791-163">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="8a791-164">Endast ett kommando eller skript kan köras i taget i en session.</span><span class="sxs-lookup"><span data-stu-id="8a791-164">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="8a791-165">När du kör flera jobb körs varje jobb i en separat session.</span><span class="sxs-lookup"><span data-stu-id="8a791-165">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="8a791-166">Varje session bidrar till omkostnaderna.</span><span class="sxs-lookup"><span data-stu-id="8a791-166">Each session contributes to the overhead.</span></span>

<span data-ttu-id="8a791-167">Tråd jobb ger bästa möjliga prestanda när det arbete de utför är större än omkostnaderna för den session som används för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="8a791-167">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="8a791-168">Det finns två fall som uppfyller det här kriteriet.</span><span class="sxs-lookup"><span data-stu-id="8a791-168">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="8a791-169">Arbetet är en beräknings intensiv körning av ett skript på flera tråd jobb kan dra nytta av flera processor kärnor och bli snabbare.</span><span class="sxs-lookup"><span data-stu-id="8a791-169">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="8a791-170">Arbetet består av betydande vänte läge – ett skript som lägger tid på att vänta på I/O-eller fjärran rop-resultat.</span><span class="sxs-lookup"><span data-stu-id="8a791-170">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="8a791-171">Att köra parallellt är vanligt vis snabbare än om de körs sekventiellt.</span><span class="sxs-lookup"><span data-stu-id="8a791-171">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

<span data-ttu-id="8a791-172">I det första exemplet ovan visas en förgrunds slinga som skapar 1000 tråd jobb för att göra en enkel sträng skrivning.</span><span class="sxs-lookup"><span data-stu-id="8a791-172">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="8a791-173">På grund av jobb omkostnader tar det över 36 sekunder att slutföra.</span><span class="sxs-lookup"><span data-stu-id="8a791-173">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="8a791-174">Det andra exemplet kör `ForEach` cmdleten för att utföra samma 1000-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="8a791-174">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="8a791-175">Den här gången `ForEach-Object` körs i tur och ordning på en enda tråd, utan någon jobb kostnad.</span><span class="sxs-lookup"><span data-stu-id="8a791-175">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="8a791-176">Den slutförs på bara 7 millisekunder.</span><span class="sxs-lookup"><span data-stu-id="8a791-176">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="8a791-177">I följande exempel samlas upp till 5000 poster upp för 10 separata system loggar.</span><span class="sxs-lookup"><span data-stu-id="8a791-177">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="8a791-178">Eftersom skriptet kräver läsning av ett antal loggar, är det klokt att utföra åtgärderna parallellt.</span><span class="sxs-lookup"><span data-stu-id="8a791-178">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

<span data-ttu-id="8a791-179">Skriptet slutförs på hälften av den tidpunkt då jobben körs parallellt.</span><span class="sxs-lookup"><span data-stu-id="8a791-179">The script completes in half the time when the jobs are run in parallel.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="8a791-180">Tråd jobb och variabler</span><span class="sxs-lookup"><span data-stu-id="8a791-180">Thread jobs and variables</span></span>

<span data-ttu-id="8a791-181">Det finns flera sätt att skicka värden till trådbaserade jobb.</span><span class="sxs-lookup"><span data-stu-id="8a791-181">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="8a791-182">`Start-ThreadJob` kan acceptera variabler som är skickas till cmdleten, skickas till-skript blocket via `$using` nyckelordet eller skickas via parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="8a791-182">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="8a791-183">`ForEach-Object -Parallel` accepterar skickas i variabler och variabler som skickas direkt till-skript blocket via `$using` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="8a791-183">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="8a791-184">Eftersom tråd jobb körs i samma process, måste alla typer av variabel referenser som skickas till jobbet behandlas noggrant.</span><span class="sxs-lookup"><span data-stu-id="8a791-184">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="8a791-185">Om det inte är ett tråd säkert objekt ska det aldrig tilldelas, och metod och egenskaper ska aldrig anropas på den.</span><span class="sxs-lookup"><span data-stu-id="8a791-185">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="8a791-186">I följande exempel skickas ett tråd säkert .NET- `ConcurrentDictionary` objekt till alla underordnade jobb för att samla in unika namngivna process objekt.</span><span class="sxs-lookup"><span data-stu-id="8a791-186">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="8a791-187">Eftersom det är ett tråd säkert objekt kan det användas på ett säkert sätt medan jobben körs samtidigt i processen.</span><span class="sxs-lookup"><span data-stu-id="8a791-187">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a><span data-ttu-id="8a791-188">Se även</span><span class="sxs-lookup"><span data-stu-id="8a791-188">See also</span></span>

- [<span data-ttu-id="8a791-189">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="8a791-189">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="8a791-190">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="8a791-190">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="8a791-191">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="8a791-191">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="8a791-192">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8a791-192">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="8a791-193">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="8a791-193">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="8a791-194">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-194">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="8a791-195">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-195">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="8a791-196">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-196">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="8a791-197">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-197">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="8a791-198">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="8a791-198">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="8a791-199">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="8a791-199">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
