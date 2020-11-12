---
description: Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: ba6251a195d3efdebd427b3f705386336b069211
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524509"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="47905-105">Om tråd jobb</span><span class="sxs-lookup"><span data-stu-id="47905-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="47905-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="47905-106">Short description</span></span>

<span data-ttu-id="47905-107">Innehåller information om PowerShell Thread-baserade jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="47905-108">Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="47905-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="47905-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="47905-109">Long description</span></span>

<span data-ttu-id="47905-110">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="47905-110">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="47905-111">Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="47905-111">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="47905-112">`RemoteJob` -Kommandon och skript körs i en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="47905-112">`RemoteJob` - Commands and scripts run in a remote session.</span></span> <span data-ttu-id="47905-113">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="47905-113">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="47905-114">`BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="47905-114">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="47905-115">Mer information finns i artikeln [om jobb](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="47905-115">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="47905-116">`PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="47905-116">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span>

<span data-ttu-id="47905-117">Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar.</span><span class="sxs-lookup"><span data-stu-id="47905-117">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="47905-118">Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.</span><span class="sxs-lookup"><span data-stu-id="47905-118">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="47905-119">Trådbaserade jobb kräver dock mindre kostnader.</span><span class="sxs-lookup"><span data-stu-id="47905-119">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="47905-120">De använder inte Remoting-skiktet eller serialiseringen.</span><span class="sxs-lookup"><span data-stu-id="47905-120">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="47905-121">Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="47905-121">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="47905-122">Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.</span><span class="sxs-lookup"><span data-stu-id="47905-122">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47905-123">Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data.</span><span class="sxs-lookup"><span data-stu-id="47905-123">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="47905-124">Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="47905-124">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="47905-125">Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="47905-125">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="47905-126">Det finns två sätt att komma runt den här situationen:</span><span class="sxs-lookup"><span data-stu-id="47905-126">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="47905-127">Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="47905-127">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="47905-128">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="47905-128">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="47905-129">Använd `Start-Process` för att skapa en ny process i stället för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-129">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="47905-130">Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="47905-130">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="how-to-start-and-manage-thread-based-jobs"></a><span data-ttu-id="47905-131">Starta och hantera trådbaserade jobb</span><span class="sxs-lookup"><span data-stu-id="47905-131">How to start and manage thread-based jobs</span></span>

<span data-ttu-id="47905-132">Det finns två sätt att starta trådbaserade jobb:</span><span class="sxs-lookup"><span data-stu-id="47905-132">There are two ways to start thread-based jobs:</span></span>

- <span data-ttu-id="47905-133">`Start-ThreadJob` – från **ThreadJob** -modulen</span><span class="sxs-lookup"><span data-stu-id="47905-133">`Start-ThreadJob` - from the **ThreadJob** module</span></span>
- <span data-ttu-id="47905-134">`ForEach-Object -Parallel -AsJob` -Parallel-funktionen har lagts till i PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="47905-134">`ForEach-Object -Parallel -AsJob` - the parallel feature was added in PowerShell 7.0</span></span>

<span data-ttu-id="47905-135">Använd samma **jobb** -cmdlets som beskrivs i [about_Jobs](about_Jobs.md) för att hantera trådbaserade jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-135">Use the same **Job** cmdlets described in [about_Jobs](about_Jobs.md) to manage thread-based jobs.</span></span>

### <a name="using-start-threadjob"></a><span data-ttu-id="47905-136">Använda `Start-ThreadJob`</span><span class="sxs-lookup"><span data-stu-id="47905-136">Using `Start-ThreadJob`</span></span>

<span data-ttu-id="47905-137">**ThreadJob** -modulen levererades först med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="47905-137">The **ThreadJob** module first shipped with PowerShell 6.</span></span> <span data-ttu-id="47905-138">Den kan också installeras från PowerShell-galleriet för Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="47905-138">It can also be installed from the PowerShell Gallery for Windows PowerShell 5.1.</span></span>

<span data-ttu-id="47905-139">Om du vill starta ett tråd jobb på den lokala datorn använder du `Start-ThreadJob` cmdleten med ett kommando eller ett skript som omges av klammerparenteser ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="47905-139">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet with a command or script enclosed in curly braces (`{ }`).</span></span>

<span data-ttu-id="47905-140">I följande exempel startar ett tråd jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="47905-140">The following example starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="47905-141">`Start-ThreadJob`Kommandot returnerar ett `ThreadJob` objekt som representerar det jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="47905-141">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="47905-142">Jobbobjektet innehåller användbar information om jobbet, inklusive dess aktuella status för körning.</span><span class="sxs-lookup"><span data-stu-id="47905-142">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="47905-143">Resultatet av jobbet samlas in när resultatet genereras.</span><span class="sxs-lookup"><span data-stu-id="47905-143">It collects the results of the job as the results are being generated.</span></span>

### <a name="using-foreach-object--parallel--asjob"></a><span data-ttu-id="47905-144">Använda `ForEach-Object -Parallel -AsJob`</span><span class="sxs-lookup"><span data-stu-id="47905-144">Using `ForEach-Object -Parallel -AsJob`</span></span>

<span data-ttu-id="47905-145">PowerShell 7,0 har lagt till en ny parameter uppsättning till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="47905-145">PowerShell 7.0 added a new parameter set to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="47905-146">Med de nya parametrarna kan du köra skript block i parallella trådar som PowerShell-jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-146">The new parameters allow you to run script blocks in parallel threads as PowerShell jobs.</span></span>

<span data-ttu-id="47905-147">Du kan skicka pipe-data till `ForEach-Object -Parallel` .</span><span class="sxs-lookup"><span data-stu-id="47905-147">You can pipe data to `ForEach-Object -Parallel`.</span></span> <span data-ttu-id="47905-148">Data skickas till skript blocket som körs parallellt.</span><span class="sxs-lookup"><span data-stu-id="47905-148">The data is passed to the script block that is run in parallel.</span></span> <span data-ttu-id="47905-149">`-AsJob`Parametern skapar jobb objekt för var och en av de parallella trådarna.</span><span class="sxs-lookup"><span data-stu-id="47905-149">The `-AsJob` parameter creates jobs objects for each of the parallel threads.</span></span>

<span data-ttu-id="47905-150">Följande kommando startar ett jobb som innehåller underordnade jobb för varje indatavärde skickas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="47905-150">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="47905-151">Varje underordnat jobb kör `Write-Output` kommandot med ett skickas-indatavärde som argument.</span><span class="sxs-lookup"><span data-stu-id="47905-151">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="47905-152">`ForEach-Object -Parallel`Kommandot returnerar ett `PSTaskJob` objekt som innehåller underordnade jobb för varje skickas-indatavärde.</span><span class="sxs-lookup"><span data-stu-id="47905-152">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="47905-153">Jobbobjektet innehåller användbar information om de underordnade jobb som kör status.</span><span class="sxs-lookup"><span data-stu-id="47905-153">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="47905-154">Resultatet av de underordnade jobben samlas in när resultaten genereras.</span><span class="sxs-lookup"><span data-stu-id="47905-154">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="47905-155">Vänta tills ett jobb har slutförts och hämta jobb resultat</span><span class="sxs-lookup"><span data-stu-id="47905-155">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="47905-156">Du kan använda PowerShell-jobbets cmdlets, till exempel `Wait-Job` och `Receive-Job` för att vänta tills ett jobb har slutförts och sedan returnera alla resultat som genereras av jobbet.</span><span class="sxs-lookup"><span data-stu-id="47905-156">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="47905-157">Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando och väntar sedan på att kommandot ska slutföras och returnerar slutligen alla data resultat som genereras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="47905-157">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="47905-158">Följande kommando startar ett jobb som kör ett `Write-Output` kommando för varje skickas-indata och väntar sedan på att alla underordnade jobb ska slutföras och returnerar slutligen alla data resultat som har genererats av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="47905-158">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="47905-159">`Receive-Job`Cmdleten returnerar resultatet av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="47905-159">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="47905-160">Eftersom varje underordnat jobb körs parallellt, garanteras inte ordningen på de genererade resultaten.</span><span class="sxs-lookup"><span data-stu-id="47905-160">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="47905-161">Prestanda för tråd jobb</span><span class="sxs-lookup"><span data-stu-id="47905-161">Thread job performance</span></span>

<span data-ttu-id="47905-162">Tråd jobb är snabbare och lättare att få högre vikt än andra typer av jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-162">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="47905-163">Men de har fortfarande överkapaciteter som kan vara stora jämfört med arbete som utförs av jobbet.</span><span class="sxs-lookup"><span data-stu-id="47905-163">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="47905-164">PowerShell kör kommandon och skript i en session.</span><span class="sxs-lookup"><span data-stu-id="47905-164">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="47905-165">Endast ett kommando eller skript kan köras i taget i en session.</span><span class="sxs-lookup"><span data-stu-id="47905-165">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="47905-166">När du kör flera jobb körs varje jobb i en separat session.</span><span class="sxs-lookup"><span data-stu-id="47905-166">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="47905-167">Varje session bidrar till omkostnaderna.</span><span class="sxs-lookup"><span data-stu-id="47905-167">Each session contributes to the overhead.</span></span>

<span data-ttu-id="47905-168">Tråd jobb ger bästa möjliga prestanda när det arbete de utför är större än omkostnaderna för den session som används för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="47905-168">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="47905-169">Det finns två fall som uppfyller det här kriteriet.</span><span class="sxs-lookup"><span data-stu-id="47905-169">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="47905-170">Arbetet är en beräknings intensiv körning av ett skript på flera tråd jobb kan dra nytta av flera processor kärnor och bli snabbare.</span><span class="sxs-lookup"><span data-stu-id="47905-170">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="47905-171">Arbetet består av betydande vänte läge – ett skript som lägger tid på att vänta på I/O-eller fjärran rop-resultat.</span><span class="sxs-lookup"><span data-stu-id="47905-171">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="47905-172">Att köra parallellt är vanligt vis snabbare än om de körs sekventiellt.</span><span class="sxs-lookup"><span data-stu-id="47905-172">Running in parallel usually completes quicker than if run sequentially.</span></span>

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

<span data-ttu-id="47905-173">I det första exemplet ovan visas en förgrunds slinga som skapar 1000 tråd jobb för att göra en enkel sträng skrivning.</span><span class="sxs-lookup"><span data-stu-id="47905-173">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="47905-174">På grund av jobb omkostnader tar det över 36 sekunder att slutföra.</span><span class="sxs-lookup"><span data-stu-id="47905-174">Due to job overhead, it takes over 36 seconds to complete.</span></span>

<span data-ttu-id="47905-175">Det andra exemplet kör `ForEach` cmdleten för att utföra samma 1000-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="47905-175">The second example runs the `ForEach` cmdlet to do the same 1000 operations.</span></span>
<span data-ttu-id="47905-176">Den här gången `ForEach-Object` körs i tur och ordning på en enda tråd, utan någon jobb kostnad.</span><span class="sxs-lookup"><span data-stu-id="47905-176">This time, `ForEach-Object` runs sequentially, on a single thread, without any job overhead.</span></span> <span data-ttu-id="47905-177">Den slutförs på bara 7 millisekunder.</span><span class="sxs-lookup"><span data-stu-id="47905-177">It completes in a mere 7 milliseconds.</span></span>

<span data-ttu-id="47905-178">I följande exempel samlas upp till 5000 poster upp för 10 separata system loggar.</span><span class="sxs-lookup"><span data-stu-id="47905-178">In the following example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="47905-179">Eftersom skriptet kräver läsning av ett antal loggar, är det klokt att utföra åtgärderna parallellt.</span><span class="sxs-lookup"><span data-stu-id="47905-179">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span>

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

<span data-ttu-id="47905-180">Skriptet slutförs på hälften av den tidpunkt då jobben körs parallellt.</span><span class="sxs-lookup"><span data-stu-id="47905-180">The script completes in half the time when the jobs are run in parallel.</span></span>

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

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="47905-181">Tråd jobb och variabler</span><span class="sxs-lookup"><span data-stu-id="47905-181">Thread jobs and variables</span></span>

<span data-ttu-id="47905-182">Det finns flera sätt att skicka värden till trådbaserade jobb.</span><span class="sxs-lookup"><span data-stu-id="47905-182">There are multiple ways to pass values into the thread-based jobs.</span></span>

<span data-ttu-id="47905-183">`Start-ThreadJob` kan acceptera variabler som är skickas till cmdleten, skickas till-skript blocket via `$using` nyckelordet eller skickas via parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="47905-183">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

<span data-ttu-id="47905-184">`ForEach-Object -Parallel` accepterar skickas i variabler och variabler som skickas direkt till-skript blocket via `$using` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="47905-184">`ForEach-Object -Parallel` accepts piped in variables, and variables passed directly to the script block via the `$using` keyword.</span></span>

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="47905-185">Eftersom tråd jobb körs i samma process, måste alla typer av variabel referenser som skickas till jobbet behandlas noggrant.</span><span class="sxs-lookup"><span data-stu-id="47905-185">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="47905-186">Om det inte är ett tråd säkert objekt ska det aldrig tilldelas, och metod och egenskaper ska aldrig anropas på den.</span><span class="sxs-lookup"><span data-stu-id="47905-186">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

<span data-ttu-id="47905-187">I följande exempel skickas ett tråd säkert .NET- `ConcurrentDictionary` objekt till alla underordnade jobb för att samla in unika namngivna process objekt.</span><span class="sxs-lookup"><span data-stu-id="47905-187">The following example passes a thread-safe .NET `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="47905-188">Eftersom det är ett tråd säkert objekt kan det användas på ett säkert sätt medan jobben körs samtidigt i processen.</span><span class="sxs-lookup"><span data-stu-id="47905-188">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="47905-189">Se även</span><span class="sxs-lookup"><span data-stu-id="47905-189">See also</span></span>

- [<span data-ttu-id="47905-190">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="47905-190">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="47905-191">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="47905-191">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="47905-192">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="47905-192">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="47905-193">about_Remote</span><span class="sxs-lookup"><span data-stu-id="47905-193">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="47905-194">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="47905-194">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="47905-195">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="47905-195">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="47905-196">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="47905-196">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="47905-197">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="47905-197">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="47905-198">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="47905-198">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="47905-199">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="47905-199">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="47905-200">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="47905-200">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
