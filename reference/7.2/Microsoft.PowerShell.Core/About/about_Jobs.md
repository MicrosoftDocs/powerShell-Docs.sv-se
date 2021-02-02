---
description: Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 862fbf54b927bb70c68e4b3cc43c564f178f9db5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708510"
---
# <a name="about-jobs"></a><span data-ttu-id="a455d-103">Om jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-103">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="a455d-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a455d-104">Short description</span></span>
<span data-ttu-id="a455d-105">Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a455d-105">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="a455d-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="a455d-106">Long description</span></span>

<span data-ttu-id="a455d-107">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="a455d-107">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="a455d-108">Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="a455d-108">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="a455d-109">`RemoteJob` -Kommandon och skript körs på en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="a455d-109">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="a455d-110">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="a455d-110">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="a455d-111">`BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a455d-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="a455d-112">`PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a455d-112">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="a455d-113">Mer information finns i [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span><span class="sxs-lookup"><span data-stu-id="a455d-113">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="a455d-114">Att köra skript på distans, på en separat dator eller i en separat process, ger bra isolering.</span><span class="sxs-lookup"><span data-stu-id="a455d-114">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="a455d-115">Eventuella fel som inträffar i fjärrjobbet påverkar inte andra jobb som körs eller den överordnade sessionen som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="a455d-115">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="a455d-116">Dock lägger dataremoting till overhead, inklusive objekt serialisering.</span><span class="sxs-lookup"><span data-stu-id="a455d-116">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="a455d-117">Alla objekt serialiseras och avserialiseras när de skickas mellan den överordnade sessionen och fjärrsessionen (Job).</span><span class="sxs-lookup"><span data-stu-id="a455d-117">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="a455d-118">Serialisering av stora komplexa data objekt kan förbruka stora mängder beräknings-och minnes resurser och överföra stora mängder data i nätverket.</span><span class="sxs-lookup"><span data-stu-id="a455d-118">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="a455d-119">Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar.</span><span class="sxs-lookup"><span data-stu-id="a455d-119">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="a455d-120">Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.</span><span class="sxs-lookup"><span data-stu-id="a455d-120">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="a455d-121">Trådbaserade jobb kräver dock mindre kostnader.</span><span class="sxs-lookup"><span data-stu-id="a455d-121">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="a455d-122">De använder inte Remoting-skiktet eller serialiseringen.</span><span class="sxs-lookup"><span data-stu-id="a455d-122">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="a455d-123">Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a455d-123">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="a455d-124">Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.</span><span class="sxs-lookup"><span data-stu-id="a455d-124">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a455d-125">Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data.</span><span class="sxs-lookup"><span data-stu-id="a455d-125">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="a455d-126">Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a455d-126">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="a455d-127">Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="a455d-127">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="a455d-128">Det finns två sätt att komma runt den här situationen:</span><span class="sxs-lookup"><span data-stu-id="a455d-128">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="a455d-129">Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="a455d-129">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="a455d-130">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="a455d-130">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="a455d-131">Använd `Start-Process` för att skapa en ny process i stället för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-131">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="a455d-132">Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="a455d-132">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="a455d-133">Jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="a455d-133">The job cmdlets</span></span>

|<span data-ttu-id="a455d-134">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="a455d-134">Cmdlet</span></span>          |<span data-ttu-id="a455d-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a455d-135">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="a455d-136">Startar ett bakgrunds jobb på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="a455d-136">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="a455d-137">Hämtar bakgrunds jobben som startades i</span><span class="sxs-lookup"><span data-stu-id="a455d-137">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="a455d-138">aktuell session.</span><span class="sxs-lookup"><span data-stu-id="a455d-138">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="a455d-139">Hämtar resultatet av bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-139">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="a455d-140">Stoppar ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-140">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="a455d-141">Ignorerar kommando tolken tills ett eller flera jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-141">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="a455d-142">full.</span><span class="sxs-lookup"><span data-stu-id="a455d-142">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="a455d-143">Tar bort ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-143">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="a455d-144">Parametern **AsJob** skapar ett bakgrunds jobb på en</span><span class="sxs-lookup"><span data-stu-id="a455d-144">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="a455d-145">Fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="a455d-145">remote computer.</span></span> <span data-ttu-id="a455d-146">Du kan använda `Invoke-Command` för att köra</span><span class="sxs-lookup"><span data-stu-id="a455d-146">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="a455d-147">valfritt jobb kommando, inklusive `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="a455d-147">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="a455d-148">Starta ett jobb på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="a455d-148">How to start a job on the local computer</span></span>

<span data-ttu-id="a455d-149">Om du vill starta ett bakgrunds jobb på den lokala datorn använder du `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a455d-149">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="a455d-150">Om du vill skriva ett `Start-Job` kommando omger du kommandot som jobbet kör inom klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="a455d-150">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="a455d-151">Använd parametern **script block** för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="a455d-151">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="a455d-152">Följande kommando startar ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a455d-152">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="a455d-153">När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart, även om jobbet tar en längre tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="a455d-153">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="a455d-154">Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="a455d-154">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="a455d-155">`Start-Job`Kommandot returnerar ett objekt som representerar jobbet.</span><span class="sxs-lookup"><span data-stu-id="a455d-155">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="a455d-156">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="a455d-156">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="a455d-157">Du kan spara jobbobjektet i en variabel och sedan använda det med andra **jobb** -cmdletar för att hantera bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="a455d-157">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="a455d-158">Följande kommando startar ett jobb objekt och sparar det resulterande jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-158">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="a455d-159">Från och med PowerShell 6,0 kan du använda bakgrunds operatorn ( `&` ) i slutet av en pipeline för att starta ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-159">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="a455d-160">Mer information finns i [bakgrunds operator](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="a455d-160">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="a455d-161">Att använda bakgrunds operatören är detsamma som att använda `Start-Job` cmdleten i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="a455d-161">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="a455d-162">Hämtar jobb objekt</span><span class="sxs-lookup"><span data-stu-id="a455d-162">Getting job objects</span></span>

<span data-ttu-id="a455d-163">`Get-Job`Cmdleten returnerar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a455d-163">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="a455d-164">Utan parametrar `Get-Job` returnerar alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a455d-164">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="a455d-165">Jobbobjektet innehåller jobbets tillstånd, vilket indikerar om jobbet har avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="a455d-165">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="a455d-166">Ett slutfört jobb har statusen **slutförd** eller **misslyckad**.</span><span class="sxs-lookup"><span data-stu-id="a455d-166">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="a455d-167">Ett jobb kan också **blockeras** eller **köras**.</span><span class="sxs-lookup"><span data-stu-id="a455d-167">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="a455d-168">Du kan spara jobbobjektet i en variabel och använda det för att representera jobbet i ett senare kommando.</span><span class="sxs-lookup"><span data-stu-id="a455d-168">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="a455d-169">Följande kommando hämtar jobbet med ID 1 och sparar det i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-169">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="a455d-170">Hämta resultatet av ett jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-170">Getting the results of a job</span></span>

<span data-ttu-id="a455d-171">När du kör ett bakgrunds jobb visas inte resultaten direkt.</span><span class="sxs-lookup"><span data-stu-id="a455d-171">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="a455d-172">Använd cmdleten för att hämta resultatet av ett bakgrunds jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="a455d-172">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="a455d-173">I följande exempel `Receive-Job` hämtar cmdlet resultatet från jobbet med jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-173">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

```powershell
Receive-Job -Job $job
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
...
```

<span data-ttu-id="a455d-174">Du kan spara resultatet av ett jobb i en variabel.</span><span class="sxs-lookup"><span data-stu-id="a455d-174">You can save the results of a job in a variable.</span></span> <span data-ttu-id="a455d-175">Följande kommando sparar resultatet av jobbet i `$job` variabeln till `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="a455d-176">Hämta och behålla del jobbs resultat</span><span class="sxs-lookup"><span data-stu-id="a455d-176">Getting and keeping partial job results</span></span>

<span data-ttu-id="a455d-177">`Receive-Job`Cmdlet: en hämtar resultatet av ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-177">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="a455d-178">Om jobbet har slutförts, `Receive-Job` hämtas alla jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="a455d-178">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="a455d-179">Om jobbet fortfarande körs `Receive-Job` hämtar de resultat som har genererats hittills.</span><span class="sxs-lookup"><span data-stu-id="a455d-179">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="a455d-180">Du kan köra `Receive-Job` kommandon igen för att få återstående resultat.</span><span class="sxs-lookup"><span data-stu-id="a455d-180">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="a455d-181">Som standard `Receive-Job` tar bort resultaten från cachen där jobb resultat lagras.</span><span class="sxs-lookup"><span data-stu-id="a455d-181">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="a455d-182">När du kör `Receive-Job` igen får du bara de nya resultaten som kom efter den första körningen.</span><span class="sxs-lookup"><span data-stu-id="a455d-182">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="a455d-183">Följande kommandon visar resultatet av kommandon som `Receive-Job` körs innan jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a455d-183">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    68       3     2632        664    29     0.36   1388 ccmsetup
   749      22    21468      19940   203   122.13   3644 communicator
   905       7     2980       2628    34   197.97    424 csrss
  1121      25    28408      32940   174   430.14   3048 explorer
```

<span data-ttu-id="a455d-184">Använd parametern **Keep** för att förhindra `Receive-Job` borttagning av jobb resultat som returneras.</span><span class="sxs-lookup"><span data-stu-id="a455d-184">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="a455d-185">Följande kommandon visar effekterna av att använda parametern **Keep** i ett jobb som inte har slutförts än.</span><span class="sxs-lookup"><span data-stu-id="a455d-185">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

```powershell
C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec

C:\PS> Receive-Job -Job $job -Keep

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    103       4    11328       9692    56            1176 audiodg
    804      14    12228      14108   100   101.74   1740 CcmExec
     68       3     2632        664    29     0.36   1388 ccmsetup
    749      22    21468      19940   203   122.13   3644 communicator
    905       7     2980       2628    34   197.97    424 csrss
   1121      25    28408      32940   174   430.14   3048 explorer
```

### <a name="waiting-for-the-results"></a><span data-ttu-id="a455d-186">Väntar på resultaten</span><span class="sxs-lookup"><span data-stu-id="a455d-186">Waiting for the results</span></span>

<span data-ttu-id="a455d-187">Om du kör ett kommando som tar lång tid att slutföra kan du använda egenskaperna för jobbobjektet för att fastställa när jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a455d-187">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="a455d-188">Följande kommando använder `Get-Job` objektet för att hämta alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a455d-188">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="a455d-189">Resultaten visas i en tabell.</span><span class="sxs-lookup"><span data-stu-id="a455d-189">The results appear in a table.</span></span> <span data-ttu-id="a455d-190">Jobbets status visas i kolumnen **status** .</span><span class="sxs-lookup"><span data-stu-id="a455d-190">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="a455d-191">I det här fallet visar egenskapen **State** att jobb 2 fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="a455d-191">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="a455d-192">Om du vill använda `Receive-Job` cmdleten för att hämta jobb resultaten nu skulle resultaten vara ofullständiga.</span><span class="sxs-lookup"><span data-stu-id="a455d-192">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="a455d-193">Du kan använda `Receive-Job` cmdleten upprepade gånger för att hämta alla resultat.</span><span class="sxs-lookup"><span data-stu-id="a455d-193">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="a455d-194">Använd egenskapen **State** för att fastställa när jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a455d-194">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="a455d-195">Du kan också använda parametern **wait** i `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a455d-195">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="a455d-196">Vid användning av den här parametern returnerar cmdleten inte kommando tolken förrän jobbet har slutförts och alla resultat är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="a455d-196">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="a455d-197">Du kan också använda `Wait-Job` cmdleten för att vänta på ett eller alla resultat av jobbet.</span><span class="sxs-lookup"><span data-stu-id="a455d-197">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="a455d-198">`Wait-Job` låter dig vänta på ett eller flera jobb eller för alla jobb.</span><span class="sxs-lookup"><span data-stu-id="a455d-198">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="a455d-199">Följande kommando använder `Wait-Job` cmdleten för att vänta på ett jobb med **ID**</span><span class="sxs-lookup"><span data-stu-id="a455d-199">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="a455d-200">Därför ignoreras PowerShell-prompten tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a455d-200">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="a455d-201">Du kan också vänta en fördefinierad tids period.</span><span class="sxs-lookup"><span data-stu-id="a455d-201">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="a455d-202">Det här kommandot använder **timeout** -parametern för att begränsa vänte tiden till 120 sekunder.</span><span class="sxs-lookup"><span data-stu-id="a455d-202">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="a455d-203">När tiden går ut returneras kommando tolken, men jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="a455d-203">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="a455d-204">Stoppa ett jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-204">Stopping a job</span></span>

<span data-ttu-id="a455d-205">Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a455d-205">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="a455d-206">Följande kommando startar ett jobb för att hämta varje post i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="a455d-206">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="a455d-207">Objektet sparas i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-207">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="a455d-208">Följande kommando stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="a455d-208">The following command stops the job.</span></span> <span data-ttu-id="a455d-209">En pipeline-operator () används `|` för att skicka jobbet i `$job` variabeln till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="a455d-209">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="a455d-210">Ta bort ett jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-210">Deleting a job</span></span>

<span data-ttu-id="a455d-211">Om du vill ta bort ett bakgrunds jobb använder du `Remove-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a455d-211">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="a455d-212">Följande kommando tar bort jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a455d-212">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="a455d-213">Undersöka ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-213">Investigating a failed job</span></span>

<span data-ttu-id="a455d-214">Jobb kan inte utföras av många olika orsaker.</span><span class="sxs-lookup"><span data-stu-id="a455d-214">Jobs can fail for many reasons.</span></span> <span data-ttu-id="a455d-215">jobbobjektet innehåller en **orsaks** egenskap som innehåller information om orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="a455d-215">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="a455d-216">I följande exempel startas ett jobb utan de autentiseringsuppgifter som krävs.</span><span class="sxs-lookup"><span data-stu-id="a455d-216">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="a455d-217">Granska **orsaks** egenskapen för att hitta det fel som gjorde att jobbet inte kunde köras.</span><span class="sxs-lookup"><span data-stu-id="a455d-217">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="a455d-218">I det här fallet misslyckades jobbet eftersom fjärrdatorn krävde explicita autentiseringsuppgifter för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="a455d-218">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="a455d-219">Egenskapen **orsak** innehåller följande meddelande:</span><span class="sxs-lookup"><span data-stu-id="a455d-219">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="a455d-220">Det gick inte att ansluta till fjärrservern. följande fel meddelande visas: "åtkomst nekad".</span><span class="sxs-lookup"><span data-stu-id="a455d-220">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="a455d-221">Se även</span><span class="sxs-lookup"><span data-stu-id="a455d-221">See also</span></span>

- [<span data-ttu-id="a455d-222">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="a455d-222">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="a455d-223">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="a455d-223">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="a455d-224">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="a455d-224">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="a455d-225">about_Remote</span><span class="sxs-lookup"><span data-stu-id="a455d-225">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="a455d-226">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a455d-226">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="a455d-227">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="a455d-228">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="a455d-229">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-229">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="a455d-230">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="a455d-231">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a455d-231">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="a455d-232">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="a455d-232">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="a455d-233">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="a455d-233">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)