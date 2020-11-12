---
description: Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 51409a124363d21f540459d49eb7e08a7c70d39a
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524866"
---
# <a name="about-jobs"></a><span data-ttu-id="39e68-104">Om jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="39e68-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="39e68-105">Short description</span></span>
<span data-ttu-id="39e68-106">Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="39e68-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="39e68-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="39e68-107">Long description</span></span>

<span data-ttu-id="39e68-108">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="39e68-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="39e68-109">Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="39e68-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="39e68-110">`RemoteJob` -Kommandon och skript körs på en fjärrsession.</span><span class="sxs-lookup"><span data-stu-id="39e68-110">`RemoteJob` - Commands and scripts run on a remote session.</span></span> <span data-ttu-id="39e68-111">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="39e68-111">For information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
- <span data-ttu-id="39e68-112">`BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="39e68-112">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span>
- <span data-ttu-id="39e68-113">`PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="39e68-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="39e68-114">Mer information finns i [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span><span class="sxs-lookup"><span data-stu-id="39e68-114">For more information, see [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).</span></span>

<span data-ttu-id="39e68-115">Att köra skript på distans, på en separat dator eller i en separat process, ger bra isolering.</span><span class="sxs-lookup"><span data-stu-id="39e68-115">Running scripts remotely, on a separate machine or in a separate process, provides great isolation.</span></span> <span data-ttu-id="39e68-116">Eventuella fel som inträffar i fjärrjobbet påverkar inte andra jobb som körs eller den överordnade sessionen som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="39e68-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="39e68-117">Dock lägger dataremoting till overhead, inklusive objekt serialisering.</span><span class="sxs-lookup"><span data-stu-id="39e68-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="39e68-118">Alla objekt serialiseras och avserialiseras när de skickas mellan den överordnade sessionen och fjärrsessionen (Job).</span><span class="sxs-lookup"><span data-stu-id="39e68-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="39e68-119">Serialisering av stora komplexa data objekt kan förbruka stora mängder beräknings-och minnes resurser och överföra stora mängder data i nätverket.</span><span class="sxs-lookup"><span data-stu-id="39e68-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

<span data-ttu-id="39e68-120">Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar.</span><span class="sxs-lookup"><span data-stu-id="39e68-120">Thread-based jobs are not as robust as remote and background jobs, because they run in the same process on different threads.</span></span> <span data-ttu-id="39e68-121">Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.</span><span class="sxs-lookup"><span data-stu-id="39e68-121">If one job has a critical error that crashes the process, then all other jobs in the process are terminated.</span></span>

<span data-ttu-id="39e68-122">Trådbaserade jobb kräver dock mindre kostnader.</span><span class="sxs-lookup"><span data-stu-id="39e68-122">However, thread-based jobs require less overhead.</span></span> <span data-ttu-id="39e68-123">De använder inte Remoting-skiktet eller serialiseringen.</span><span class="sxs-lookup"><span data-stu-id="39e68-123">They don't use the remoting layer or serialization.</span></span> <span data-ttu-id="39e68-124">Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="39e68-124">The result objects are returned as references to live objects in the current session.</span></span> <span data-ttu-id="39e68-125">Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.</span><span class="sxs-lookup"><span data-stu-id="39e68-125">Without this overhead, thread-based jobs run faster and use fewer resources than the other job types.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39e68-126">Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data.</span><span class="sxs-lookup"><span data-stu-id="39e68-126">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="39e68-127">Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="39e68-127">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="39e68-128">Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="39e68-128">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="39e68-129">Det finns två sätt att komma runt den här situationen:</span><span class="sxs-lookup"><span data-stu-id="39e68-129">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="39e68-130">Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="39e68-130">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="39e68-131">Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="39e68-131">For more information, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>
1. <span data-ttu-id="39e68-132">Använd `Start-Process` för att skapa en ny process i stället för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-132">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="39e68-133">Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="39e68-133">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="39e68-134">Jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="39e68-134">The job cmdlets</span></span>

|<span data-ttu-id="39e68-135">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="39e68-135">Cmdlet</span></span>          |<span data-ttu-id="39e68-136">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="39e68-136">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="39e68-137">Startar ett bakgrunds jobb på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="39e68-137">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="39e68-138">Hämtar bakgrunds jobben som startades i</span><span class="sxs-lookup"><span data-stu-id="39e68-138">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="39e68-139">aktuell session.</span><span class="sxs-lookup"><span data-stu-id="39e68-139">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="39e68-140">Hämtar resultatet av bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-140">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="39e68-141">Stoppar ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-141">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="39e68-142">Ignorerar kommando tolken tills ett eller flera jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-142">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="39e68-143">full.</span><span class="sxs-lookup"><span data-stu-id="39e68-143">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="39e68-144">Tar bort ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-144">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="39e68-145">Parametern **AsJob** skapar ett bakgrunds jobb på en</span><span class="sxs-lookup"><span data-stu-id="39e68-145">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="39e68-146">Fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="39e68-146">remote computer.</span></span> <span data-ttu-id="39e68-147">Du kan använda `Invoke-Command` för att köra</span><span class="sxs-lookup"><span data-stu-id="39e68-147">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="39e68-148">valfritt jobb kommando, inklusive `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="39e68-148">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="39e68-149">Starta ett jobb på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="39e68-149">How to start a job on the local computer</span></span>

<span data-ttu-id="39e68-150">Om du vill starta ett bakgrunds jobb på den lokala datorn använder du `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39e68-150">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="39e68-151">Om du vill skriva ett `Start-Job` kommando omger du kommandot som jobbet kör inom klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="39e68-151">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="39e68-152">Använd parametern **script block** för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="39e68-152">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="39e68-153">Följande kommando startar ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="39e68-153">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="39e68-154">När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart, även om jobbet tar en längre tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="39e68-154">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="39e68-155">Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="39e68-155">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="39e68-156">`Start-Job`Kommandot returnerar ett objekt som representerar jobbet.</span><span class="sxs-lookup"><span data-stu-id="39e68-156">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="39e68-157">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="39e68-157">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="39e68-158">Du kan spara jobbobjektet i en variabel och sedan använda det med andra **jobb** -cmdletar för att hantera bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="39e68-158">You can save the job object in a variable and then use it with the other **Job** cmdlets to manage the background job.</span></span> <span data-ttu-id="39e68-159">Följande kommando startar ett jobb objekt och sparar det resulterande jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-159">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="39e68-160">Från och med PowerShell 6,0 kan du använda bakgrunds operatorn ( `&` ) i slutet av en pipeline för att starta ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-160">Beginning in PowerShell 6.0, you can use the background operator (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="39e68-161">Mer information finns i [bakgrunds operator](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="39e68-161">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="39e68-162">Att använda bakgrunds operatören är detsamma som att använda `Start-Job` cmdleten i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="39e68-162">Using the background operator is functionally equivalent to using the `Start-Job` cmdlet in the previous example.</span></span>

```powershell
$job = Get-Process &
```

## <a name="getting-job-objects"></a><span data-ttu-id="39e68-163">Hämtar jobb objekt</span><span class="sxs-lookup"><span data-stu-id="39e68-163">Getting job objects</span></span>

<span data-ttu-id="39e68-164">`Get-Job`Cmdleten returnerar objekt som representerar bakgrunds jobben som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="39e68-164">The `Get-Job` cmdlet returns objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="39e68-165">Utan parametrar `Get-Job` returnerar alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="39e68-165">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="39e68-166">Jobbobjektet innehåller jobbets tillstånd, vilket indikerar om jobbet har avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="39e68-166">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="39e68-167">Ett slutfört jobb har statusen **slutförd** eller **misslyckad**.</span><span class="sxs-lookup"><span data-stu-id="39e68-167">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="39e68-168">Ett jobb kan också **blockeras** eller **köras**.</span><span class="sxs-lookup"><span data-stu-id="39e68-168">A job might also be **Blocked** or **Running**.</span></span>

```Output
Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

<span data-ttu-id="39e68-169">Du kan spara jobbobjektet i en variabel och använda det för att representera jobbet i ett senare kommando.</span><span class="sxs-lookup"><span data-stu-id="39e68-169">You can save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="39e68-170">Följande kommando hämtar jobbet med ID 1 och sparar det i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-170">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="39e68-171">Hämta resultatet av ett jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-171">Getting the results of a job</span></span>

<span data-ttu-id="39e68-172">När du kör ett bakgrunds jobb visas inte resultaten direkt.</span><span class="sxs-lookup"><span data-stu-id="39e68-172">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="39e68-173">Använd cmdleten för att hämta resultatet av ett bakgrunds jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="39e68-173">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="39e68-174">I följande exempel `Receive-Job` hämtar cmdlet resultatet från jobbet med jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-174">The following example, the `Receive-Job` cmdlet gets the results of the job using job object in the `$job` variable.</span></span>

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

<span data-ttu-id="39e68-175">Du kan spara resultatet av ett jobb i en variabel.</span><span class="sxs-lookup"><span data-stu-id="39e68-175">You can save the results of a job in a variable.</span></span> <span data-ttu-id="39e68-176">Följande kommando sparar resultatet av jobbet i `$job` variabeln till `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-176">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

### <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="39e68-177">Hämta och behålla del jobbs resultat</span><span class="sxs-lookup"><span data-stu-id="39e68-177">Getting and keeping partial job results</span></span>

<span data-ttu-id="39e68-178">`Receive-Job`Cmdlet: en hämtar resultatet av ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-178">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="39e68-179">Om jobbet har slutförts, `Receive-Job` hämtas alla jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="39e68-179">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="39e68-180">Om jobbet fortfarande körs `Receive-Job` hämtar de resultat som har genererats hittills.</span><span class="sxs-lookup"><span data-stu-id="39e68-180">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="39e68-181">Du kan köra `Receive-Job` kommandon igen för att få återstående resultat.</span><span class="sxs-lookup"><span data-stu-id="39e68-181">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="39e68-182">Som standard `Receive-Job` tar bort resultaten från cachen där jobb resultat lagras.</span><span class="sxs-lookup"><span data-stu-id="39e68-182">By default, `Receive-Job` deletes the results from the cache where job results are stored.</span></span> <span data-ttu-id="39e68-183">När du kör `Receive-Job` igen får du bara de nya resultaten som kom efter den första körningen.</span><span class="sxs-lookup"><span data-stu-id="39e68-183">When you run `Receive-Job` again, you get only the new results that arrived after the first run.</span></span>

<span data-ttu-id="39e68-184">Följande kommandon visar resultatet av kommandon som `Receive-Job` körs innan jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="39e68-184">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="39e68-185">Använd parametern **Keep** för att förhindra `Receive-Job` borttagning av jobb resultat som returneras.</span><span class="sxs-lookup"><span data-stu-id="39e68-185">Use the **Keep** parameter to prevent `Receive-Job` from deleting the job results that are returned.</span></span> <span data-ttu-id="39e68-186">Följande kommandon visar effekterna av att använda parametern **Keep** i ett jobb som inte har slutförts än.</span><span class="sxs-lookup"><span data-stu-id="39e68-186">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

### <a name="waiting-for-the-results"></a><span data-ttu-id="39e68-187">Väntar på resultaten</span><span class="sxs-lookup"><span data-stu-id="39e68-187">Waiting for the results</span></span>

<span data-ttu-id="39e68-188">Om du kör ett kommando som tar lång tid att slutföra kan du använda egenskaperna för jobbobjektet för att fastställa när jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="39e68-188">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="39e68-189">Följande kommando använder `Get-Job` objektet för att hämta alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="39e68-189">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="39e68-190">Resultaten visas i en tabell.</span><span class="sxs-lookup"><span data-stu-id="39e68-190">The results appear in a table.</span></span> <span data-ttu-id="39e68-191">Jobbets status visas i kolumnen **status** .</span><span class="sxs-lookup"><span data-stu-id="39e68-191">The status of the job appears in the **State** column.</span></span>

```Output
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="39e68-192">I det här fallet visar egenskapen **State** att jobb 2 fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="39e68-192">In this case, the **State** property reveals that Job 2 is still running.</span></span> <span data-ttu-id="39e68-193">Om du vill använda `Receive-Job` cmdleten för att hämta jobb resultaten nu skulle resultaten vara ofullständiga.</span><span class="sxs-lookup"><span data-stu-id="39e68-193">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="39e68-194">Du kan använda `Receive-Job` cmdleten upprepade gånger för att hämta alla resultat.</span><span class="sxs-lookup"><span data-stu-id="39e68-194">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="39e68-195">Använd egenskapen **State** för att fastställa när jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="39e68-195">Use the **State** property to determine when the job is complete.</span></span>

<span data-ttu-id="39e68-196">Du kan också använda parametern **wait** i `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39e68-196">You can also use the **Wait** parameter of the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="39e68-197">Vid användning av den här parametern returnerar cmdleten inte kommando tolken förrän jobbet har slutförts och alla resultat är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="39e68-197">When use use this parameter, the cmdlet does not return the command prompt until the job is completed and all results are available.</span></span>

<span data-ttu-id="39e68-198">Du kan också använda `Wait-Job` cmdleten för att vänta på ett eller alla resultat av jobbet.</span><span class="sxs-lookup"><span data-stu-id="39e68-198">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="39e68-199">`Wait-Job` låter dig vänta på ett eller flera jobb eller för alla jobb.</span><span class="sxs-lookup"><span data-stu-id="39e68-199">`Wait-Job` lets you wait for one or more specific job or for all jobs.</span></span>
<span data-ttu-id="39e68-200">Följande kommando använder `Wait-Job` cmdleten för att vänta på ett jobb med **ID**</span><span class="sxs-lookup"><span data-stu-id="39e68-200">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="39e68-201">Därför ignoreras PowerShell-prompten tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="39e68-201">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="39e68-202">Du kan också vänta en fördefinierad tids period.</span><span class="sxs-lookup"><span data-stu-id="39e68-202">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="39e68-203">Det här kommandot använder **timeout** -parametern för att begränsa vänte tiden till 120 sekunder.</span><span class="sxs-lookup"><span data-stu-id="39e68-203">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="39e68-204">När tiden går ut returneras kommando tolken, men jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="39e68-204">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="39e68-205">Stoppa ett jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-205">Stopping a job</span></span>

<span data-ttu-id="39e68-206">Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39e68-206">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="39e68-207">Följande kommando startar ett jobb för att hämta varje post i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="39e68-207">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="39e68-208">Objektet sparas i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-208">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="39e68-209">Följande kommando stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="39e68-209">The following command stops the job.</span></span> <span data-ttu-id="39e68-210">En pipeline-operator () används `|` för att skicka jobbet i `$job` variabeln till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="39e68-210">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="39e68-211">Ta bort ett jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-211">Deleting a job</span></span>

<span data-ttu-id="39e68-212">Om du vill ta bort ett bakgrunds jobb använder du `Remove-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39e68-212">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="39e68-213">Följande kommando tar bort jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39e68-213">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="39e68-214">Undersöka ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-214">Investigating a failed job</span></span>

<span data-ttu-id="39e68-215">Jobb kan inte utföras av många olika orsaker.</span><span class="sxs-lookup"><span data-stu-id="39e68-215">Jobs can fail for many reasons.</span></span> <span data-ttu-id="39e68-216">jobbobjektet innehåller en **orsaks** egenskap som innehåller information om orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="39e68-216">the job object contains a **Reason** property that contains information about the cause of the failure.</span></span>

<span data-ttu-id="39e68-217">I följande exempel startas ett jobb utan de autentiseringsuppgifter som krävs.</span><span class="sxs-lookup"><span data-stu-id="39e68-217">The following example starts a job without the required credentials.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}
Get-Job $job

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="39e68-218">Granska **orsaks** egenskapen för att hitta det fel som gjorde att jobbet inte kunde köras.</span><span class="sxs-lookup"><span data-stu-id="39e68-218">Inspect the **Reason** property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="39e68-219">I det här fallet misslyckades jobbet eftersom fjärrdatorn krävde explicita autentiseringsuppgifter för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="39e68-219">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="39e68-220">Egenskapen **orsak** innehåller följande meddelande:</span><span class="sxs-lookup"><span data-stu-id="39e68-220">The **Reason** property contains the following message:</span></span>

> <span data-ttu-id="39e68-221">Det gick inte att ansluta till fjärrservern. följande fel meddelande visas: "åtkomst nekad".</span><span class="sxs-lookup"><span data-stu-id="39e68-221">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="39e68-222">Se även</span><span class="sxs-lookup"><span data-stu-id="39e68-222">See also</span></span>

- [<span data-ttu-id="39e68-223">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="39e68-223">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="39e68-224">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="39e68-224">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="39e68-225">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="39e68-225">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="39e68-226">about_Remote</span><span class="sxs-lookup"><span data-stu-id="39e68-226">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="39e68-227">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="39e68-227">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="39e68-228">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-228">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="39e68-229">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-229">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="39e68-230">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-230">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="39e68-231">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-231">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="39e68-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="39e68-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="39e68-233">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="39e68-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="39e68-234">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="39e68-234">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
