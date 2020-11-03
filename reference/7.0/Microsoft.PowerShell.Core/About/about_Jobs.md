---
description: Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Jobs
ms.openlocfilehash: 838e142fe39260b759e9a44c6d69b80d3c5b293e
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2020
ms.locfileid: "93272997"
---
# <a name="about-jobs"></a><span data-ttu-id="1c898-104">Om jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-104">About Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="1c898-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c898-105">Short description</span></span>
<span data-ttu-id="1c898-106">Ger information om hur PowerShell-arbetsjobb kör ett kommando eller uttryck i bakgrunden utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-106">Provides information about how PowerShell background jobs run a command or expression in the background without interacting with the current session.</span></span>

## <a name="long-description"></a><span data-ttu-id="1c898-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c898-107">Long description</span></span>

<span data-ttu-id="1c898-108">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="1c898-108">PowerShell concurrently runs commands and script through jobs.</span></span> <span data-ttu-id="1c898-109">Det finns tre jobbbaserade lösningar som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="1c898-109">There are three jobs-based solutions provided by PowerShell to support concurrency.</span></span>

|<span data-ttu-id="1c898-110">Jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-110">Job</span></span>            |<span data-ttu-id="1c898-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c898-111">Description</span></span>                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |<span data-ttu-id="1c898-112">Kommando och skript körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="1c898-112">Command and script run on a remote computer.</span></span>                 |
|`BackgroundJob`|<span data-ttu-id="1c898-113">Kommando och skript körs i en separat process på den lokala</span><span class="sxs-lookup"><span data-stu-id="1c898-113">Command and script run in a separate process on the local</span></span>    |
|               |<span data-ttu-id="1c898-114">datorspecifika.</span><span class="sxs-lookup"><span data-stu-id="1c898-114">machine.</span></span>                                                     |
|`ThreadJob`    |<span data-ttu-id="1c898-115">Kommando och skript körs i en separat tråd inom samma</span><span class="sxs-lookup"><span data-stu-id="1c898-115">Command and script run in a separate thread within the same</span></span>  |
|               |<span data-ttu-id="1c898-116">processen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1c898-116">process on the local machine.</span></span>                                |

<span data-ttu-id="1c898-117">Varje typ av jobb har fördelar och nack delar.</span><span class="sxs-lookup"><span data-stu-id="1c898-117">Each type of job has benefits and drawbacks.</span></span> <span data-ttu-id="1c898-118">Att köra skript på en annan dator eller i en separat process har en bra isolering.</span><span class="sxs-lookup"><span data-stu-id="1c898-118">Running script remotely on a separate machine or in a separate process has great isolation.</span></span> <span data-ttu-id="1c898-119">Eventuella fel påverkar inte andra jobb som körs eller klienten som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-119">Any errors won't affect other running jobs or the client that started the job.</span></span> <span data-ttu-id="1c898-120">Men Remoting-lagret lägger till overhead, inklusive objekt serialisering.</span><span class="sxs-lookup"><span data-stu-id="1c898-120">But the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="1c898-121">Alla objekt som skickas till och från fjärrsessionen måste serialiseras och sedan avserialiseras i takt med att den passerar mellan klienten och mål sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-121">All objects passed to and from the remote session must be serialized and then deserialized as it passes between the client and the target session.</span></span> <span data-ttu-id="1c898-122">Serialiserings åtgärden kan använda många beräknings-och minnes resurser för stora komplexa data objekt.</span><span class="sxs-lookup"><span data-stu-id="1c898-122">The serialization operation can use many compute and memory resources for large complex data objects.</span></span>

<span data-ttu-id="1c898-123">I det här avsnittet beskrivs hur du kör bakgrunds jobb i PowerShell på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="1c898-123">This topic explains how to run background jobs in PowerShell on a local computer.</span></span> <span data-ttu-id="1c898-124">Information om hur du kör bakgrunds jobb på fjärrdatorer finns [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1c898-124">For information about running background jobs on remote computers, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span> <span data-ttu-id="1c898-125">Mer information om tråd jobb finns i [about_Thread_Jobs](about_Thread_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="1c898-125">For more information about thread jobs, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="1c898-126">När du startar ett bakgrunds jobb returnerar kommando tolken omedelbart, även om jobbet tar en längre tid att slutföra.</span><span class="sxs-lookup"><span data-stu-id="1c898-126">When you start a background job, the command prompt returns immediately, even if the job takes an extended time to complete.</span></span> <span data-ttu-id="1c898-127">Du kan fortsätta att arbeta i sessionen utan avbrott medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="1c898-127">You can continue to work in the session without interruption while the job runs.</span></span>

## <a name="the-job-cmdlets"></a><span data-ttu-id="1c898-128">Jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="1c898-128">The job cmdlets</span></span>

|<span data-ttu-id="1c898-129">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c898-129">Cmdlet</span></span>          |<span data-ttu-id="1c898-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c898-130">Description</span></span>                                            |
|----------------|-------------------------------------------------------|
|`Start-Job`     |<span data-ttu-id="1c898-131">Startar ett bakgrunds jobb på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="1c898-131">Starts a background job on a local computer.</span></span>           |
|`Get-Job`       |<span data-ttu-id="1c898-132">Hämtar bakgrunds jobben som startades i</span><span class="sxs-lookup"><span data-stu-id="1c898-132">Gets the background jobs that were started in the</span></span>      |
|                |<span data-ttu-id="1c898-133">aktuell session.</span><span class="sxs-lookup"><span data-stu-id="1c898-133">current session.</span></span>                                       |
|`Receive-Job`   |<span data-ttu-id="1c898-134">Hämtar resultatet av bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-134">Gets the results of background jobs.</span></span>                   |
|`Stop-Job`      |<span data-ttu-id="1c898-135">Stoppar ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-135">Stops a background job.</span></span>                                |
|`Wait-Job`      |<span data-ttu-id="1c898-136">Ignorerar kommando tolken tills ett eller flera jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-136">Suppresses the command prompt until one or all jobs are</span></span>|
|                |<span data-ttu-id="1c898-137">full.</span><span class="sxs-lookup"><span data-stu-id="1c898-137">complete.</span></span>                                              |
|`Remove-Job`    |<span data-ttu-id="1c898-138">Tar bort ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-138">Deletes a background job.</span></span>                              |
|`Invoke-Command`|<span data-ttu-id="1c898-139">Parametern **AsJob** skapar ett bakgrunds jobb på en</span><span class="sxs-lookup"><span data-stu-id="1c898-139">The **AsJob** parameter creates a background job on a</span></span>  |
|                |<span data-ttu-id="1c898-140">Fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="1c898-140">remote computer.</span></span> <span data-ttu-id="1c898-141">Du kan använda `Invoke-Command` för att köra</span><span class="sxs-lookup"><span data-stu-id="1c898-141">You can use `Invoke-Command` to run</span></span>   |
|                |<span data-ttu-id="1c898-142">valfritt jobb kommando, inklusive `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="1c898-142">any job command remotely, including `Start-Job`.</span></span>       |

## <a name="how-to-start-a-job-on-the-local-computer"></a><span data-ttu-id="1c898-143">Starta ett jobb på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="1c898-143">How to start a job on the local computer</span></span>

<span data-ttu-id="1c898-144">Om du vill starta ett bakgrunds jobb på den lokala datorn använder du `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c898-144">To start a background job on the local computer, use the `Start-Job` cmdlet.</span></span>

<span data-ttu-id="1c898-145">Om du vill skriva ett `Start-Job` kommando omger du kommandot som jobbet kör inom klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="1c898-145">To write a `Start-Job` command, enclose the command that the job runs in curly braces (`{}`).</span></span> <span data-ttu-id="1c898-146">Använd parametern **script block** för att ange kommandot.</span><span class="sxs-lookup"><span data-stu-id="1c898-146">Use the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="1c898-147">Följande kommando startar ett bakgrunds jobb som kör ett `Get-Process` kommando på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1c898-147">The following command starts a background job that runs a `Get-Process` command on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="1c898-148">`Start-Job`Kommandot returnerar ett objekt som representerar jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-148">The `Start-Job` command returns an object that represents the job.</span></span> <span data-ttu-id="1c898-149">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="1c898-149">The job object contains useful information about the job, but it does not contain the job results.</span></span>

<span data-ttu-id="1c898-150">Spara jobbobjektet i en variabel och Använd sedan det med andra jobb-cmdletar för att hantera bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-150">Save the job object in a variable, and then use it with the other Job cmdlets to manage the background job.</span></span> <span data-ttu-id="1c898-151">Följande kommando startar ett jobb objekt och sparar det resulterande jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-151">The following command starts a job object and saves the resulting job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
```

<span data-ttu-id="1c898-152">Från och med PowerShell 6,0 kan du använda en amersand ( `&` ) i slutet av en pipeline för att starta ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-152">Beginning in PowerShell 6.0, you can use an amersand (`&`) at the end of a pipeline to start a background job.</span></span> <span data-ttu-id="1c898-153">Följande kommando fungerar som likvärdigt med kommandot ovan.</span><span class="sxs-lookup"><span data-stu-id="1c898-153">The following command is functionally equivalent to the command above.</span></span>

```powershell
$job = Get-Process &
```

<span data-ttu-id="1c898-154">Et-tecknet ( `&` ) kallas för bakgrunds operatorn.</span><span class="sxs-lookup"><span data-stu-id="1c898-154">The ampersand (`&`) is called the background operator.</span></span> <span data-ttu-id="1c898-155">Mer information finns i [bakgrunds operator](about_Operators.md#background-operator-).</span><span class="sxs-lookup"><span data-stu-id="1c898-155">For more information, see [background operator](about_Operators.md#background-operator-).</span></span>

<span data-ttu-id="1c898-156">Du kan också använda `Get-Job` cmdleten för att hämta objekt som representerar de jobb som startats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-156">You can also use the `Get-Job` cmdlet to get objects that represent the jobs started in the current session.</span></span> <span data-ttu-id="1c898-157">`Get-Job` returnerar samma jobb objekt som `Start-Job` returnerar.</span><span class="sxs-lookup"><span data-stu-id="1c898-157">`Get-Job` returns the same job object that `Start-Job` returns.</span></span>

## <a name="getting-job-objects"></a><span data-ttu-id="1c898-158">Hämtar jobb objekt</span><span class="sxs-lookup"><span data-stu-id="1c898-158">Getting job objects</span></span>

<span data-ttu-id="1c898-159">Använd cmdleten för att hämta objektet som representerar bakgrunds jobben som startades i den aktuella sessionen `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="1c898-159">To get object that represent the background jobs that were started in the current session, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="1c898-160">Utan parametrar `Get-Job` returnerar alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-160">Without parameters, `Get-Job` returns all of the jobs that were started in the current session.</span></span>

<span data-ttu-id="1c898-161">Följande kommando hämtar till exempel jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-161">For example, the following command gets the jobs in the current session.</span></span>

```powershell
PS C:> Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Running    True         localhost  Get-Process
```

<span data-ttu-id="1c898-162">Du kan också spara jobbobjektet i en variabel och använda det för att representera jobbet i ett senare kommando.</span><span class="sxs-lookup"><span data-stu-id="1c898-162">You can also save the job object in a variable and use it to represent the job in a later command.</span></span> <span data-ttu-id="1c898-163">Följande kommando hämtar jobbet med ID 1 och sparar det i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-163">The following command gets the job with ID 1 and saves it in the `$job` variable.</span></span>

```powershell
$job = Get-Job -Id 1
```

<span data-ttu-id="1c898-164">Jobbobjektet innehåller jobbets tillstånd, vilket indikerar om jobbet har avslut ATS.</span><span class="sxs-lookup"><span data-stu-id="1c898-164">The job object contains the state of the job, which indicates whether the job has finished.</span></span> <span data-ttu-id="1c898-165">Ett slutfört jobb har statusen **slutförd** eller **misslyckad**.</span><span class="sxs-lookup"><span data-stu-id="1c898-165">A finished job has a state of **Complete** or **Failed**.</span></span> <span data-ttu-id="1c898-166">Ett jobb kan också **blockeras** eller **köras**.</span><span class="sxs-lookup"><span data-stu-id="1c898-166">A job might also be **blocked** or **running**.</span></span>

```powershell
Get-Job

Id  Name  PSJobTypeName State      HasMoreData  Location   Command
--  ----  ------------- -----      -----------  --------   -------
1   Job1  BackgroundJob Complete   True         localhost  Get-Process
```

## <a name="getting-the-results-of-a-job"></a><span data-ttu-id="1c898-167">Hämta resultatet av ett jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-167">Getting the results of a job</span></span>

<span data-ttu-id="1c898-168">När du kör ett bakgrunds jobb visas inte resultaten direkt.</span><span class="sxs-lookup"><span data-stu-id="1c898-168">When you run a background job, the results do not appear immediately.</span></span> <span data-ttu-id="1c898-169">I stället `Start-Job` returnerar cmdleten ett jobb objekt som representerar jobbet, men det innehåller inte resultatet.</span><span class="sxs-lookup"><span data-stu-id="1c898-169">Instead, the `Start-Job` cmdlet returns a job object that represents the job, but it does not contain the results.</span></span> <span data-ttu-id="1c898-170">Använd cmdleten för att hämta resultatet av ett bakgrunds jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="1c898-170">To get the results of a background job, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="1c898-171">Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-171">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="1c898-172">Det använder ett jobb objekt som sparats i `$job` variabeln för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-172">It uses a job object saved in the `$job` variable to identify the job.</span></span>

```powershell
Receive-Job -Job $job
```

<span data-ttu-id="1c898-173">`Receive-Job`Cmdleten returnerar resultatet från jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-173">The `Receive-Job` cmdlet returns the results of the job.</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
    103       4    11328       9692    56           1176 audiodg
    804      14    12228      14108   100   101.74  1740 CcmExec
    668       7     2672       6168   104    32.26   488 csrss
# ...
```

<span data-ttu-id="1c898-174">Du kan också spara resultatet av ett jobb i en variabel.</span><span class="sxs-lookup"><span data-stu-id="1c898-174">You can also save the results of a job in a variable.</span></span> <span data-ttu-id="1c898-175">Följande kommando sparar resultatet av jobbet i `$job` variabeln till `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-175">The following command saves the results of the job in the `$job` variable to the `$results` variable.</span></span>

```powershell
$results = Receive-Job -Job $job
```

<span data-ttu-id="1c898-176">Du kan också spara resultatet av jobbet i en fil med hjälp av omdirigerings operatorn ( `>` ) eller `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c898-176">And, you can save the results of the job in a file by using the redirection operator (`>`) or the `Out-File` cmdlet.</span></span> <span data-ttu-id="1c898-177">Följande kommando använder operatorn för omdirigering för att spara resultatet av jobbet i `$job` variabeln i `Results.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="1c898-177">The following command uses the redirection operator to save the results of the job in the `$job` variable in the `Results.txt` file.</span></span>

```powershell
Receive-Job -Job $job > results.txt
```

## <a name="getting-and-keeping-partial-job-results"></a><span data-ttu-id="1c898-178">Hämta och behålla del jobbs resultat</span><span class="sxs-lookup"><span data-stu-id="1c898-178">Getting and keeping partial job results</span></span>

<span data-ttu-id="1c898-179">`Receive-Job`Cmdlet: en hämtar resultatet av ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-179">The `Receive-Job` cmdlet gets the results of a background job.</span></span> <span data-ttu-id="1c898-180">Om jobbet har slutförts, `Receive-Job` hämtas alla jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="1c898-180">If the job is complete, `Receive-Job` gets all job results.</span></span> <span data-ttu-id="1c898-181">Om jobbet fortfarande körs `Receive-Job` hämtar de resultat som har genererats hittills.</span><span class="sxs-lookup"><span data-stu-id="1c898-181">If the job is still running, `Receive-Job` gets the results that have been generated thus far.</span></span> <span data-ttu-id="1c898-182">Du kan köra `Receive-Job` kommandon igen för att få återstående resultat.</span><span class="sxs-lookup"><span data-stu-id="1c898-182">You can run `Receive-Job` commands again to get the remaining results.</span></span>

<span data-ttu-id="1c898-183">När `Receive-Job` returnerar resultat tas dessa resultat som standard bort från cachen där jobb resultat lagras.</span><span class="sxs-lookup"><span data-stu-id="1c898-183">When `Receive-Job` returns results, by default, it deletes those results from the cache where job results are stored.</span></span> <span data-ttu-id="1c898-184">Om du kör ett annat `Receive-Job` kommando får du bara de resultat som ännu inte har tagits emot.</span><span class="sxs-lookup"><span data-stu-id="1c898-184">If you run another `Receive-Job` command, you get only the results that are not yet received.</span></span>

<span data-ttu-id="1c898-185">Följande kommandon visar resultatet av kommandon som `Receive-Job` körs innan jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="1c898-185">The following commands show the results of `Receive-Job` commands run before the job is complete.</span></span>

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

<span data-ttu-id="1c898-186">Om du inte vill `Receive-Job` ta bort jobb resultatet som det har returnerat använder du parametern **Keep** .</span><span class="sxs-lookup"><span data-stu-id="1c898-186">To prevent `Receive-Job` from deleting the job results that it has returned, use the **Keep** parameter.</span></span> <span data-ttu-id="1c898-187">Därför `Receive-Job` returneras alla resultat som har genererats fram till den tiden.</span><span class="sxs-lookup"><span data-stu-id="1c898-187">As a result, `Receive-Job` returns all of the results that have been generated until that time.</span></span>

<span data-ttu-id="1c898-188">Följande kommandon visar effekterna av att använda parametern **Keep** i ett jobb som inte har slutförts än.</span><span class="sxs-lookup"><span data-stu-id="1c898-188">The following commands show the effect of using the **Keep** parameter on a job that is not yet complete.</span></span>

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

## <a name="waiting-for-the-results"></a><span data-ttu-id="1c898-189">Väntar på resultaten</span><span class="sxs-lookup"><span data-stu-id="1c898-189">Waiting for the results</span></span>

<span data-ttu-id="1c898-190">Om du kör ett kommando som tar lång tid att slutföra kan du använda egenskaperna för jobbobjektet för att fastställa när jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="1c898-190">If you run a command that takes a long time to complete, you can use the properties of the job object to determine when the job is complete.</span></span> <span data-ttu-id="1c898-191">Följande kommando använder `Get-Job` objektet för att hämta alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1c898-191">The following command uses the `Get-Job` object to get all of the background jobs in the current session.</span></span>

```powershell
Get-Job
```

<span data-ttu-id="1c898-192">Resultaten visas i en tabell.</span><span class="sxs-lookup"><span data-stu-id="1c898-192">The results appear in a table.</span></span> <span data-ttu-id="1c898-193">Jobbets status visas i kolumnen **status** .</span><span class="sxs-lookup"><span data-stu-id="1c898-193">The status of the job appears in the **State** column.</span></span>

```
Id Name  PSJobTypeName State    HasMoreData Location  Command
-- ----  ------------- -----    ----------- --------  -------
1  Job1  BackgroundJob Complete True        localhost Get-Process
2  Job2  BackgroundJob Running  True        localhost Get-EventLog -Log ...
3  Job3  BackgroundJob Complete True        localhost dir -Path C:\* -Re...
```

<span data-ttu-id="1c898-194">I det här fallet visar egenskapen State att jobb 2 fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="1c898-194">In this case, the State property reveals that Job 2 is still running.</span></span> <span data-ttu-id="1c898-195">Om du vill använda `Receive-Job` cmdleten för att hämta jobb resultaten nu skulle resultaten vara ofullständiga.</span><span class="sxs-lookup"><span data-stu-id="1c898-195">If you were to use the `Receive-Job` cmdlet to get the job results now, the results would be incomplete.</span></span> <span data-ttu-id="1c898-196">Du kan använda `Receive-Job` cmdleten upprepade gånger för att hämta alla resultat.</span><span class="sxs-lookup"><span data-stu-id="1c898-196">You can use the `Receive-Job` cmdlet repeatedly to get all of the results.</span></span> <span data-ttu-id="1c898-197">Som standard får du bara de resultat som inte redan tagits emot, varje gång du använder den, men du kan använda parametern **Keep** för `Receive-Job` cmdlet: en för att behålla resultaten, även om de redan har tagits emot.</span><span class="sxs-lookup"><span data-stu-id="1c898-197">By default, each time you use it, you get only the results that were not already received, but you can use the **Keep** parameter of the `Receive-Job` cmdlet to retain the results, even though they were already received.</span></span>

<span data-ttu-id="1c898-198">Du kan skriva de partiella resultaten till en fil och sedan lägga till nya resultat när de tas emot eller vänta och kontrol lera jobbets tillstånd senare.</span><span class="sxs-lookup"><span data-stu-id="1c898-198">You can write the partial results to a file and then append newer results as they arrive or you can wait and check the state of the job later.</span></span>

<span data-ttu-id="1c898-199">Du kan använda parametern **wait** för `Receive-Job` cmdleten, som inte returnerar kommando tolken förrän jobbet har slutförts och alla resultat är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="1c898-199">You can use the **Wait** parameter of the `Receive-Job` cmdlet, which does not return the command prompt until the job is complete and all results are available.</span></span>

<span data-ttu-id="1c898-200">Du kan också använda `Wait-Job` cmdleten för att vänta på ett eller alla resultat av jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-200">You can also use the `Wait-Job` cmdlet to wait for any or all of the results of the job.</span></span> <span data-ttu-id="1c898-201">`Wait-Job` Du kan vänta på ett visst jobb, för alla jobb eller för att utföra slutförda jobb.</span><span class="sxs-lookup"><span data-stu-id="1c898-201">`Wait-Job` lets you wait for a particular job, for all jobs, or for any of the jobs to be completed.</span></span>

<span data-ttu-id="1c898-202">Följande kommando använder `Wait-Job` cmdleten för att vänta på ett jobb med **ID**</span><span class="sxs-lookup"><span data-stu-id="1c898-202">The following command uses the `Wait-Job` cmdlet to wait for a job with **ID**</span></span>
10.

```powershell
Wait-Job -ID 10
```

<span data-ttu-id="1c898-203">Därför ignoreras PowerShell-prompten tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="1c898-203">As a result, the PowerShell prompt is suppressed until the job is completed.</span></span>

<span data-ttu-id="1c898-204">Du kan också vänta en fördefinierad tids period.</span><span class="sxs-lookup"><span data-stu-id="1c898-204">You can also wait for a predetermined period of time.</span></span> <span data-ttu-id="1c898-205">Det här kommandot använder **timeout** -parametern för att begränsa vänte tiden till 120 sekunder.</span><span class="sxs-lookup"><span data-stu-id="1c898-205">This command uses the **Timeout** parameter to limit the wait to 120 seconds.</span></span> <span data-ttu-id="1c898-206">När tiden går ut returneras kommando tolken, men jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="1c898-206">When the time expires, the command prompt returns, but the job continues to run in the background.</span></span>

```powershell
Wait-Job -ID 10 -Timeout 120
```

## <a name="stopping-a-job"></a><span data-ttu-id="1c898-207">Stoppa ett jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-207">Stopping a job</span></span>

<span data-ttu-id="1c898-208">Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c898-208">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="1c898-209">Följande kommando startar ett jobb för att hämta varje post i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="1c898-209">The following command starts a job to get every entry in the System event log.</span></span> <span data-ttu-id="1c898-210">Objektet sparas i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-210">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-EventLog -Log System}
```

<span data-ttu-id="1c898-211">Följande kommando stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="1c898-211">The following command stops the job.</span></span> <span data-ttu-id="1c898-212">En pipeline-operator () används `|` för att skicka jobbet i `$job` variabeln till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="1c898-212">It uses a pipeline operator (`|`) to send the job in the `$job` variable to `Stop-Job`.</span></span>

```powershell
$job | Stop-Job
```

## <a name="deleting-a-job"></a><span data-ttu-id="1c898-213">Ta bort ett jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-213">Deleting a job</span></span>

<span data-ttu-id="1c898-214">Om du vill ta bort ett bakgrunds jobb använder du `Remove-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c898-214">To delete a background job, use the `Remove-Job` cmdlet.</span></span> <span data-ttu-id="1c898-215">Följande kommando tar bort jobbet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-215">The following command deletes the job in the `$job` variable.</span></span>

```powershell
Remove-Job -Job $job
```

## <a name="investigating-a-failed-job"></a><span data-ttu-id="1c898-216">Undersöka ett misslyckat jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-216">Investigating a failed job</span></span>

<span data-ttu-id="1c898-217">Om du vill ta reda på varför ett jobb misslyckades, Använd egenskapen **orsak** för jobbobjektet.</span><span class="sxs-lookup"><span data-stu-id="1c898-217">To find out why a job failed, use the **Reason** property of the job object.</span></span>

<span data-ttu-id="1c898-218">Följande kommando startar ett jobb utan de autentiseringsuppgifter som krävs.</span><span class="sxs-lookup"><span data-stu-id="1c898-218">The following command starts a job without the required credentials.</span></span> <span data-ttu-id="1c898-219">Objektet sparas i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c898-219">It saves the job object in the `$job` variable.</span></span>

```powershell
$job = Start-Job -ScriptBlock {New-Item -Path HKLM:\Software\MyCompany}

Id Name  PSJobTypeName State  HasMoreData  Location  Command
-- ----  ------------- -----  -----------  --------  -------
1  Job1  BackgroundJob Failed False        localhost New-Item -Path HKLM:...
```

<span data-ttu-id="1c898-220">Följande kommando använder egenskapen orsak för att hitta felet som gjorde att jobbet inte kunde köras.</span><span class="sxs-lookup"><span data-stu-id="1c898-220">The following command uses the Reason property to find the error that caused the job to fail.</span></span>

```powershell
$job.ChildJobs[0].JobStateInfo.Reason
```

<span data-ttu-id="1c898-221">I det här fallet misslyckades jobbet eftersom fjärrdatorn krävde explicita autentiseringsuppgifter för att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="1c898-221">In this case, the job failed because the remote computer required explicit credentials to run the command.</span></span> <span data-ttu-id="1c898-222">Värdet för egenskapen **orsak** är:</span><span class="sxs-lookup"><span data-stu-id="1c898-222">The value of the **Reason** property is:</span></span>

<span data-ttu-id="1c898-223">Det gick inte att ansluta till fjärrservern. följande fel meddelande visas: "åtkomst nekad".</span><span class="sxs-lookup"><span data-stu-id="1c898-223">Connecting to remote server failed with the following error message: "Access is denied".</span></span>

## <a name="see-also"></a><span data-ttu-id="1c898-224">Se även</span><span class="sxs-lookup"><span data-stu-id="1c898-224">See also</span></span>

- [<span data-ttu-id="1c898-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="1c898-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="1c898-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="1c898-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="1c898-227">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="1c898-227">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="1c898-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1c898-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="1c898-229">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1c898-229">about_PSSessions</span></span>](about_PSSessions.md)
- [<span data-ttu-id="1c898-230">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="1c898-231">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="1c898-232">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-232">Receive-Job</span></span>](xref:Microsoft.PowerShell.Core.Receive-Job)
- [<span data-ttu-id="1c898-233">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="1c898-234">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="1c898-234">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="1c898-235">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="1c898-235">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="1c898-236">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="1c898-236">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
