---
description: Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 973d0ddf18b63cd7462817cf68f7c5d7466f4724
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2020
ms.locfileid: "93273008"
---
# <a name="about-thread-jobs"></a><span data-ttu-id="db91b-105">Om tråd jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-105">About Thread Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="db91b-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="db91b-106">Short description</span></span>

<span data-ttu-id="db91b-107">Innehåller information om PowerShell Thread-baserade jobb.</span><span class="sxs-lookup"><span data-stu-id="db91b-107">Provides information about PowerShell thread-based jobs.</span></span> <span data-ttu-id="db91b-108">Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="db91b-108">A thread job is a type of background job that runs a command or expression in a separate thread within the current session process.</span></span>

## <a name="long-description"></a><span data-ttu-id="db91b-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="db91b-109">Long description</span></span>

<span data-ttu-id="db91b-110">Den här artikeln beskriver hur du kör tråd jobb i PowerShell på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="db91b-110">This article explains how to run thread jobs in PowerShell on a local computer.</span></span>
<span data-ttu-id="db91b-111">Information om hur du kör bakgrunds jobb på en lokal dator finns [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="db91b-111">For information about running background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span>

<span data-ttu-id="db91b-112">Starta ett tråd jobb med hjälp av `Start-ThreadJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="db91b-112">Start a thread job by using the `Start-ThreadJob` cmdlet.</span></span> <span data-ttu-id="db91b-113">Denna cmdlet är tillgänglig i **ThreadJob** -modulen som levereras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="db91b-113">This cmdlet is available in the **ThreadJob** module that ships with PowerShell.</span></span>
<span data-ttu-id="db91b-114">`Start-ThreadJob` Returnerar ett enskilt jobb objekt som kapslar in kommandot eller skriptet som körs och kan användas med alla PowerShell-jobb som manipulerar-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="db91b-114">`Start-ThreadJob` returns a single job object that encapsulates the running command or script, and can be used with all PowerShell job manipulating cmdlets.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="db91b-115">Jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="db91b-115">The job cmdlets</span></span>

|<span data-ttu-id="db91b-116">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="db91b-116">Cmdlet</span></span>           |<span data-ttu-id="db91b-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="db91b-117">Description</span></span>                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|<span data-ttu-id="db91b-118">Startar ett tråd jobb på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="db91b-118">Starts a thread job on a local computer.</span></span>               |
|`Get-Job`        |<span data-ttu-id="db91b-119">Hämtar de jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="db91b-119">Gets the jobs that were started in the current session.</span></span>|
|`Receive-Job`    |<span data-ttu-id="db91b-120">Hämtar resultatet av jobb.</span><span class="sxs-lookup"><span data-stu-id="db91b-120">Gets the results of jobs.</span></span>                              |
|`Stop-Job`       |<span data-ttu-id="db91b-121">Stoppar ett pågående jobb.</span><span class="sxs-lookup"><span data-stu-id="db91b-121">Stops a running job.</span></span>                                   |
|`Wait-Job`       |<span data-ttu-id="db91b-122">Ignorerar kommando tolken tills ett eller flera jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-122">Suppresses the command prompt until one or all jobs are</span></span>|
|                 |<span data-ttu-id="db91b-123">full.</span><span class="sxs-lookup"><span data-stu-id="db91b-123">complete.</span></span>                                              |
|`Remove-Job`     |<span data-ttu-id="db91b-124">Tar bort ett jobb.</span><span class="sxs-lookup"><span data-stu-id="db91b-124">Deletes a job.</span></span>                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a><span data-ttu-id="db91b-125">Så här startar du ett tråd jobb på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="db91b-125">How to start a thread job on the local computer</span></span>

<span data-ttu-id="db91b-126">Om du vill starta ett tråd jobb på den lokala datorn använder du `Start-ThreadJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="db91b-126">To start a thread job on the local computer, use the `Start-ThreadJob` cmdlet.</span></span>

<span data-ttu-id="db91b-127">Om du vill skriva ett `Start-ThreadJob` kommando, omger du kommandot eller skriptet som jobbet körs inom klammerparenteser ( `{ }` ).</span><span class="sxs-lookup"><span data-stu-id="db91b-127">To write a `Start-ThreadJob` command, enclose the command or script the job runs in curly braces (`{ }`).</span></span>

<span data-ttu-id="db91b-128">Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="db91b-128">The following command starts a thread job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

<span data-ttu-id="db91b-129">`Start-ThreadJob`Kommandot returnerar ett `ThreadJob` objekt som representerar det jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="db91b-129">The `Start-ThreadJob` command returns a `ThreadJob` object that represents the running job.</span></span> <span data-ttu-id="db91b-130">Jobbobjektet innehåller användbar information om jobbet, inklusive dess aktuella status för körning.</span><span class="sxs-lookup"><span data-stu-id="db91b-130">The job object contains useful information about the job including its current running status.</span></span> <span data-ttu-id="db91b-131">Resultatet av jobbet samlas in när resultatet genereras.</span><span class="sxs-lookup"><span data-stu-id="db91b-131">It collects the results of the job as the results are being generated.</span></span>

<span data-ttu-id="db91b-132">Om du vill skriva ett `ForEach-Object -Parallel` kommando, pipe-data till kommandot och omger kommandot eller skriptet som jobbet körs inom klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="db91b-132">To write a `ForEach-Object -Parallel` command, pipe data to the command and enclose the command or script the job runs in curly braces(`{}`).</span></span> <span data-ttu-id="db91b-133">Använd `-AsJob` parameter växeln så att ett jobb objekt returneras.</span><span class="sxs-lookup"><span data-stu-id="db91b-133">Use the `-AsJob` parameter switch so that a job object is returned.</span></span>

<span data-ttu-id="db91b-134">Följande kommando startar ett jobb som innehåller underordnade jobb för varje indatavärde skickas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="db91b-134">The following command starts a job that contains child jobs for each input value piped to the command.</span></span> <span data-ttu-id="db91b-135">Varje underordnat jobb kör `Write-Output` kommandot med ett skickas-indatavärde som argument.</span><span class="sxs-lookup"><span data-stu-id="db91b-135">Each child job runs the `Write-Output` command with a piped input value as the argument.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

<span data-ttu-id="db91b-136">`ForEach-Object -Parallel`Kommandot returnerar ett `PSTaskJob` objekt som innehåller underordnade jobb för varje skickas-indatavärde.</span><span class="sxs-lookup"><span data-stu-id="db91b-136">The `ForEach-Object -Parallel` command returns a `PSTaskJob` object that contains child jobs for each piped input value.</span></span> <span data-ttu-id="db91b-137">Jobbobjektet innehåller användbar information om de underordnade jobb som kör status.</span><span class="sxs-lookup"><span data-stu-id="db91b-137">The job object contains useful information about the child jobs running status.</span></span> <span data-ttu-id="db91b-138">Resultatet av de underordnade jobben samlas in när resultaten genereras.</span><span class="sxs-lookup"><span data-stu-id="db91b-138">It collects the results of the child jobs as the results are being generated.</span></span>

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a><span data-ttu-id="db91b-139">Vänta tills ett jobb har slutförts och hämta jobb resultat</span><span class="sxs-lookup"><span data-stu-id="db91b-139">How to wait for a job to complete and retrieve job results</span></span>

<span data-ttu-id="db91b-140">Du kan använda PowerShell-jobbets cmdlets, till exempel `Wait-Job` och `Receive-Job` för att vänta tills ett jobb har slutförts och sedan returnera alla resultat som genereras av jobbet.</span><span class="sxs-lookup"><span data-stu-id="db91b-140">You can use PowerShell job cmdlets, such as `Wait-Job` and `Receive-Job` to wait for a job to complete and then return all results generated by the job.</span></span>

<span data-ttu-id="db91b-141">Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando och väntar sedan på att kommandot ska slutföras och returnerar slutligen alla data resultat som genereras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="db91b-141">The following command starts a thread job that runs a `Get-Process` command, then waits for the command to complete, and finally returns all data results generated by the command.</span></span>

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

<span data-ttu-id="db91b-142">Följande kommando startar ett jobb som kör ett `Write-Output` kommando för varje skickas-indata och väntar sedan på att alla underordnade jobb ska slutföras och returnerar slutligen alla data resultat som har genererats av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="db91b-142">The following command starts a job that runs a `Write-Output` command for each piped input, then waits for all child jobs to complete, and finally returns all data results generated by the child jobs.</span></span>

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="db91b-143">`Receive-Job`Cmdleten returnerar resultatet av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="db91b-143">The `Receive-Job` cmdlet returns the results of the child jobs.</span></span>

```powershell
1
3
2
4
5
```

<span data-ttu-id="db91b-144">Eftersom varje underordnat jobb körs parallellt, garanteras inte ordningen på de genererade resultaten.</span><span class="sxs-lookup"><span data-stu-id="db91b-144">Because each child job runs parallel, the order of the generated results is not guaranteed.</span></span>

## <a name="powershell-concurrency-and-jobs"></a><span data-ttu-id="db91b-145">PowerShell-samtidighet och jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-145">PowerShell concurrency and jobs</span></span>

<span data-ttu-id="db91b-146">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="db91b-146">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="db91b-147">Det finns tre jobbbaserade lösningar som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="db91b-147">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="db91b-148">Jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-148">Job</span></span>            |<span data-ttu-id="db91b-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="db91b-149">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="db91b-150">Kommando och skript körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="db91b-150">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="db91b-151">Kommando och skript körs i en separat process på den lokala</span><span class="sxs-lookup"><span data-stu-id="db91b-151">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="db91b-152">datorspecifika.</span><span class="sxs-lookup"><span data-stu-id="db91b-152">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="db91b-153">Kommando och skript körs i en separat tråd inom samma</span><span class="sxs-lookup"><span data-stu-id="db91b-153">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="db91b-154">processen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="db91b-154">process on the local machine.</span></span>                                |

<span data-ttu-id="db91b-155">Varje typ av jobb har fördelar och nack delar.</span><span class="sxs-lookup"><span data-stu-id="db91b-155">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="db91b-156">Att köra skript på en annan dator eller i en separat process har en bra isolering.</span><span class="sxs-lookup"><span data-stu-id="db91b-156">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="db91b-157">Eventuella fel påverkar inte andra jobb som körs eller klienten som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="db91b-157">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="db91b-158">Men Remoting-lagret lägger till overhead, inklusive objekt serialisering.</span><span class="sxs-lookup"><span data-stu-id="db91b-158">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="db91b-159">Alla objekt som skickas till och från fjärrsessionen måste serialiseras och sedan avserialiseras i takt med att den passerar mellan klienten och mål sessionen.</span><span class="sxs-lookup"><span data-stu-id="db91b-159">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="db91b-160">Serialiserings åtgärden kan använda många beräknings-och minnes resurser för stora komplexa data objekt.</span><span class="sxs-lookup"><span data-stu-id="db91b-160">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

## <a name="powershell-thread-based-jobs"></a><span data-ttu-id="db91b-161">PowerShell Thread-baserade jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-161">PowerShell thread based jobs</span></span>

<span data-ttu-id="db91b-162">Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar.</span><span class="sxs-lookup"><span data-stu-id="db91b-162">Thread based jobs are not as robust as Remote and Background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="db91b-163">Om ett jobb har ett kritiskt fel som gör att processen kraschar, kommer alla andra jobb i processen också att Miss sen.</span><span class="sxs-lookup"><span data-stu-id="db91b-163">If one job has a critical error that crashes the process, then all other jobs in the process will also fail.</span></span>

<span data-ttu-id="db91b-164">Trådbaserade jobb har dock mycket mindre kostnader.</span><span class="sxs-lookup"><span data-stu-id="db91b-164">However, thread-based jobs have much less overhead.</span></span> <span data-ttu-id="db91b-165">De behöver inte använda Remoting-lagret eller serialiseringen.</span><span class="sxs-lookup"><span data-stu-id="db91b-165">They don't need to use the remoting layer or serialization.</span></span> <span data-ttu-id="db91b-166">Resultatet är att trådbaserade jobb ofta körs mycket snabbare och använder mycket mindre resurser än andra jobb typer.</span><span class="sxs-lookup"><span data-stu-id="db91b-166">The result is that thread-based jobs tend to run much faster and use far less resources than the other job types.</span></span>

## <a name="thread-job-performance"></a><span data-ttu-id="db91b-167">Prestanda för tråd jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-167">Thread job performance</span></span>

<span data-ttu-id="db91b-168">Tråd jobb är snabbare och lättare att få högre vikt än andra typer av jobb.</span><span class="sxs-lookup"><span data-stu-id="db91b-168">Thread jobs are faster and lighter weight than other types of jobs.</span></span> <span data-ttu-id="db91b-169">Men de har fortfarande överkapaciteter som kan vara stora jämfört med arbete som utförs av jobbet.</span><span class="sxs-lookup"><span data-stu-id="db91b-169">But they still have overhead that can be large when compared to work the job is doing.</span></span>

<span data-ttu-id="db91b-170">PowerShell kör kommandon och skript i en session.</span><span class="sxs-lookup"><span data-stu-id="db91b-170">PowerShell runs commands and script in a session.</span></span> <span data-ttu-id="db91b-171">Endast ett kommando eller skript kan köras i taget i en session.</span><span class="sxs-lookup"><span data-stu-id="db91b-171">Only one command or script can run at a time in a session.</span></span> <span data-ttu-id="db91b-172">När du kör flera jobb körs varje jobb i en separat session.</span><span class="sxs-lookup"><span data-stu-id="db91b-172">So when running multiple jobs, each job runs in a separate session.</span></span> <span data-ttu-id="db91b-173">Varje session bidrar till omkostnaderna.</span><span class="sxs-lookup"><span data-stu-id="db91b-173">Each session contributes to the overhead.</span></span>

<span data-ttu-id="db91b-174">Tråd jobb ger bästa möjliga prestanda när det arbete de utför är större än omkostnaderna för den session som används för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="db91b-174">Thread jobs provide the best performance when the work they perform is greater than the overhead of the session used to run the job.</span></span> <span data-ttu-id="db91b-175">Det finns två fall som uppfyller det här kriteriet.</span><span class="sxs-lookup"><span data-stu-id="db91b-175">There are two cases for that meet this criteria.</span></span>

- <span data-ttu-id="db91b-176">Arbetet är en beräknings intensiv körning av ett skript på flera tråd jobb kan dra nytta av flera processor kärnor och bli snabbare.</span><span class="sxs-lookup"><span data-stu-id="db91b-176">Work is compute intensive - Running a script on multiple thread jobs can take advantage of multiple processor cores and complete faster.</span></span>

- <span data-ttu-id="db91b-177">Arbetet består av betydande vänte läge – ett skript som lägger tid på att vänta på I/O-eller fjärran rop-resultat.</span><span class="sxs-lookup"><span data-stu-id="db91b-177">Work consists of significant waiting - A script that spends time waiting for I/O or remote call results.</span></span> <span data-ttu-id="db91b-178">Att köra parallellt är vanligt vis snabbare än om de körs sekventiellt.</span><span class="sxs-lookup"><span data-stu-id="db91b-178">Running in parallel usually completes quicker than if run sequentially.</span></span>

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

<span data-ttu-id="db91b-179">I det första exemplet ovan visas en förgrunds slinga som skapar 1000 tråd jobb för att göra en enkel sträng skrivning.</span><span class="sxs-lookup"><span data-stu-id="db91b-179">The first example above shows a foreach loop that creates 1000 thread jobs to do a simple string write.</span></span> <span data-ttu-id="db91b-180">På grund av jobb omkostnader tar det över 33 sekunder att slutföra.</span><span class="sxs-lookup"><span data-stu-id="db91b-180">Due to job overhead, it takes over 33 seconds to complete.</span></span>

<span data-ttu-id="db91b-181">Det andra exemplet kör `ForEach` cmdleten för att utföra samma 1000-åtgärder och varje sträng skrivning körs sekventiellt utan någon jobb kostnad.</span><span class="sxs-lookup"><span data-stu-id="db91b-181">The second example runs the `ForEach` cmdlet to do the same 1000 operations and each string write is executed sequentially without any job overhead.</span></span> <span data-ttu-id="db91b-182">Det slutförs med 25 millisekunder.</span><span class="sxs-lookup"><span data-stu-id="db91b-182">It completes in a mere 25 milliseconds.</span></span>

```powershell
$logNames.count
10

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

<span data-ttu-id="db91b-183">I exemplet ovan samlas upp till 5000 poster upp för 10 separata system loggar.</span><span class="sxs-lookup"><span data-stu-id="db91b-183">In the above example, up to 5000 entries are collected for 10 separate system logs.</span></span> <span data-ttu-id="db91b-184">Eftersom skriptet kräver läsning av ett antal loggar, är det klokt att utföra åtgärderna parallellt.</span><span class="sxs-lookup"><span data-stu-id="db91b-184">Since the script involves reading a number of logs, it makes sense to do the operations in parallel.</span></span> <span data-ttu-id="db91b-185">Och jobbet slutförs över två gånger så snabbt som när skriptet körs sekventiellt.</span><span class="sxs-lookup"><span data-stu-id="db91b-185">And the job completes over twice as fast as when the script is run sequentially.</span></span>

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a><span data-ttu-id="db91b-186">Tråd jobb och variabler</span><span class="sxs-lookup"><span data-stu-id="db91b-186">Thread jobs and variables</span></span>

<span data-ttu-id="db91b-187">Variabler överförs till tråd jobb på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="db91b-187">Variables are passed into thread jobs in various ways.</span></span>

<span data-ttu-id="db91b-188">`Start-ThreadJob` kan acceptera variabler som är skickas till cmdleten, skickas till-skript blocket via `$using` nyckelordet eller skickas via parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="db91b-188">`Start-ThreadJob` can accept variables that are piped to the cmdlet, passed in to the script block via the `$using` keyword, or passed in via the **ArgumentList** parameter.</span></span>

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job

`ForEach-Object -Parallel` accepts piped in variables, and variables passed
directly to the script block via the `$using` keyword.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

<span data-ttu-id="db91b-189">Eftersom tråd jobb körs i samma process, måste alla typer av variabel referenser som skickas till jobbet behandlas noggrant.</span><span class="sxs-lookup"><span data-stu-id="db91b-189">Since thread jobs run in the same process, any variable reference type passed into the job has to be treated carefully.</span></span> <span data-ttu-id="db91b-190">Om det inte är ett tråd säkert objekt ska det aldrig tilldelas, och metod och egenskaper ska aldrig anropas på den.</span><span class="sxs-lookup"><span data-stu-id="db91b-190">If it is not a thread safe object, then it should never be assigned to, and method and properties should never be invoked on it.</span></span>

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

<span data-ttu-id="db91b-191">Exemplet ovan skickar ett tråd säkert dotNet- `ConcurrentDictionary` objekt till alla underordnade jobb för att samla in unika namngivna process objekt.</span><span class="sxs-lookup"><span data-stu-id="db91b-191">The above example passes a thread safe dotNet `ConcurrentDictionary` object to all child jobs to collect uniquely named process objects.</span></span> <span data-ttu-id="db91b-192">Eftersom det är ett tråd säkert objekt kan det användas på ett säkert sätt medan jobben körs samtidigt i processen.</span><span class="sxs-lookup"><span data-stu-id="db91b-192">Since it is a thread safe object, it can be safely used while the jobs run concurrently in the process.</span></span>

## <a name="see-also"></a><span data-ttu-id="db91b-193">Se även</span><span class="sxs-lookup"><span data-stu-id="db91b-193">See also</span></span>

- [<span data-ttu-id="db91b-194">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="db91b-194">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="db91b-195">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="db91b-195">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="db91b-196">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="db91b-196">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="db91b-197">about_Remote</span><span class="sxs-lookup"><span data-stu-id="db91b-197">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="db91b-198">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="db91b-198">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="db91b-199">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-199">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="db91b-200">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-200">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="db91b-201">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-201">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="db91b-202">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-202">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="db91b-203">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="db91b-203">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="db91b-204">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="db91b-204">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
