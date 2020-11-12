---
description: Beskriver hur du kör jobb på fjärrdatorer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 71f59fcb8e656e4ac439028507f15cf36b8402f6
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524934"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="20ec0-104">Om Fjärrjobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="20ec0-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="20ec0-105">Short Description</span></span>
<span data-ttu-id="20ec0-106">Beskriver hur du kör jobb på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="20ec0-106">Describes how to run jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="20ec0-107">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="20ec0-107">Detailed Description</span></span>

<span data-ttu-id="20ec0-108">PowerShell kör kommandon och skript via jobb samtidigt.</span><span class="sxs-lookup"><span data-stu-id="20ec0-108">PowerShell concurrently runs commands and scripts through jobs.</span></span> <span data-ttu-id="20ec0-109">Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-109">There are three jobs types provided by PowerShell to support concurrency.</span></span>

- <span data-ttu-id="20ec0-110">`RemoteJob` -Kommandon och skript körs i en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="20ec0-110">`RemoteJob` - Commands and scripts run in a remote session.</span></span>
- <span data-ttu-id="20ec0-111">`BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-111">`BackgroundJob` - Commands and scripts run in a separate process on the local machine.</span></span> <span data-ttu-id="20ec0-112">Mer information finns i artikeln [om jobb](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="20ec0-112">For more information, see [about_Jobs](about_Jobs.md).</span></span>
- <span data-ttu-id="20ec0-113">`PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-113">`PSTaskJob` or `ThreadJob` - Commands and scripts run in a separate thread within the same process on the local machine.</span></span> <span data-ttu-id="20ec0-114">Mer information finns i [about_Thread_Jobs](about_Thread_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="20ec0-114">For more information, see [about_Thread_Jobs](about_Thread_Jobs.md).</span></span>

<span data-ttu-id="20ec0-115">Att köra skript på distans, på en separat dator eller i en separat process, ger bra isolering.</span><span class="sxs-lookup"><span data-stu-id="20ec0-115">Running scripts remotely, on a separate machine or in a separate process, provide great isolation.</span></span> <span data-ttu-id="20ec0-116">Eventuella fel som inträffar i fjärrjobbet påverkar inte andra jobb som körs eller den överordnade sessionen som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-116">Any errors that occur in the remote job do not affect other running jobs or the parent session that started the job.</span></span> <span data-ttu-id="20ec0-117">Dock lägger dataremoting till overhead, inklusive objekt serialisering.</span><span class="sxs-lookup"><span data-stu-id="20ec0-117">However, the remoting layer adds overhead, including object serialization.</span></span> <span data-ttu-id="20ec0-118">Alla objekt serialiseras och avserialiseras när de skickas mellan den överordnade sessionen och fjärrsessionen (Job).</span><span class="sxs-lookup"><span data-stu-id="20ec0-118">All objects are serialized and deserialized as they are passed between the parent session and the remote (job) session.</span></span> <span data-ttu-id="20ec0-119">Serialisering av stora komplexa data objekt kan förbruka stora mängder beräknings-och minnes resurser och överföra stora mängder data i nätverket.</span><span class="sxs-lookup"><span data-stu-id="20ec0-119">Serialization of large complex data objects can consume large amounts of compute and memory resources and transfer large amounts of data across the network.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="20ec0-120">Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data.</span><span class="sxs-lookup"><span data-stu-id="20ec0-120">The parent session that created the job also monitors the job status and collects pipeline data.</span></span> <span data-ttu-id="20ec0-121">Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd.</span><span class="sxs-lookup"><span data-stu-id="20ec0-121">The job child process is terminated by the parent process once the job reaches a finished state.</span></span> <span data-ttu-id="20ec0-122">Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.</span><span class="sxs-lookup"><span data-stu-id="20ec0-122">If the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span>

<span data-ttu-id="20ec0-123">Det finns två sätt att komma runt den här situationen:</span><span class="sxs-lookup"><span data-stu-id="20ec0-123">There are two ways work around this situation:</span></span>

1. <span data-ttu-id="20ec0-124">Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner.</span><span class="sxs-lookup"><span data-stu-id="20ec0-124">Use `Invoke-Command` to create jobs that run in disconnected sessions.</span></span> <span data-ttu-id="20ec0-125">Se avsnittet [frånkopplade processer](#how-to-run-as-a-detached-process) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="20ec0-125">See the [detached processes](#how-to-run-as-a-detached-process) section of this article.</span></span>
1. <span data-ttu-id="20ec0-126">Använd `Start-Process` för att skapa en ny process i stället för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="20ec0-126">Use `Start-Process` to create a new process rather than a job.</span></span> <span data-ttu-id="20ec0-127">Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).</span><span class="sxs-lookup"><span data-stu-id="20ec0-127">For more information, see [Start-Process](xref:Microsoft.PowerShell.Management.Start-Process).</span></span>

## <a name="remote-jobs"></a><span data-ttu-id="20ec0-128">Fjärrjobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-128">Remote Jobs</span></span>

<span data-ttu-id="20ec0-129">Du kan köra jobb på fjärrdatorer genom att använda tre olika metoder.</span><span class="sxs-lookup"><span data-stu-id="20ec0-129">You can run jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="20ec0-130">Starta en interaktiv session på en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="20ec0-130">Start an interactive session on a remote computer.</span></span> <span data-ttu-id="20ec0-131">Starta sedan ett jobb i den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-131">Then start a job in the interactive session.</span></span> <span data-ttu-id="20ec0-132">Procedurerna är desamma som att köra ett lokalt jobb, även om alla åtgärder utförs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-132">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="20ec0-133">Kör ett jobb på en fjärrdator som returnerar sina resultat till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-133">Run a job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="20ec0-134">Använd den här metoden om du vill samla in resultatet av jobb och underhålla dem på en central plats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-134">Use this method when you want to collect the results of jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="20ec0-135">Kör ett jobb på en fjärrdator som underhåller sina resultat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-135">Run a job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="20ec0-136">Använd den här metoden när jobb data är säkrare att behållas på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-136">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-job-in-an-interactive-session"></a><span data-ttu-id="20ec0-137">Starta ett jobb i en interaktiv session</span><span class="sxs-lookup"><span data-stu-id="20ec0-137">Start a job in an interactive session</span></span>

<span data-ttu-id="20ec0-138">Du kan starta en interaktiv session med en fjärrdator och sedan starta ett jobb under den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-138">You can start an interactive session with a remote computer and then start a job during the interactive session.</span></span> <span data-ttu-id="20ec0-139">Mer information om interaktiva sessioner finns about_Remote och se `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20ec0-139">For more information about interactive sessions, see about_Remote, and see `Enter-PSSession`.</span></span>

<span data-ttu-id="20ec0-140">Proceduren för att starta ett jobb i en interaktiv session är nästan identisk med proceduren för att starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-140">The procedure for starting a job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="20ec0-141">Alla åtgärder sker dock på fjärrdatorn, inte på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-141">However, all of the operations occur on the remote computer, not the local computer.</span></span>

1. <span data-ttu-id="20ec0-142">Använd `Enter-PSSession` cmdleten för att starta en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="20ec0-142">Use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="20ec0-143">Du kan använda parametern ComputerName för `Enter-PSSession` för att upprätta en tillfällig anslutning för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-143">You can use the ComputerName parameter of `Enter-PSSession` to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="20ec0-144">Du kan också använda parametern session för att köra den interaktiva sessionen i en PowerShell-session (PSSession).</span><span class="sxs-lookup"><span data-stu-id="20ec0-144">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

   <span data-ttu-id="20ec0-145">Följande kommando startar en interaktiv session på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-145">The following command starts an interactive session on the Server01 computer.</span></span>

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   <span data-ttu-id="20ec0-146">Kommando tolken ändras för att visa att du nu är ansluten till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-146">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

   ```
   Server01\C:>
   ```

1. <span data-ttu-id="20ec0-147">Om du vill starta ett Fjärrjobb i sessionen använder du `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20ec0-147">To start a remote job in the session, use the `Start-Job` cmdlet.</span></span> <span data-ttu-id="20ec0-148">Följande kommando kör ett Fjärrjobb som hämtar händelserna i händelse loggen för Windows PowerShell på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-148">The following command runs a remote job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="20ec0-149">`Start-Job`Cmdleten returnerar ett objekt som representerar jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-149">The `Start-Job` cmdlet returns an object that represents the job.</span></span>

   <span data-ttu-id="20ec0-150">Det här kommandot sparar jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20ec0-150">This command saves the job object in the `$job` variable.</span></span>

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   <span data-ttu-id="20ec0-151">När jobbet körs kan du använda den interaktiva sessionen för att köra andra kommandon, inklusive andra jobb.</span><span class="sxs-lookup"><span data-stu-id="20ec0-151">While the job runs, you can use the interactive session to run other commands, including other jobs.</span></span> <span data-ttu-id="20ec0-152">Du måste dock låta den interaktiva sessionen vara öppen tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="20ec0-152">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="20ec0-153">Om du slutar sessionen avbryts jobbet och resultaten går förlorade.</span><span class="sxs-lookup"><span data-stu-id="20ec0-153">If you end the session, the job is interrupted, and the results are lost.</span></span>

1. <span data-ttu-id="20ec0-154">Om du vill ta reda på om jobbet är klart kan du Visa värdet för `$job` variabeln eller använda `Get-Job` cmdleten för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-154">To find out if the job is complete, display the value of the `$job` variable, or use the `Get-Job` cmdlet to get the job.</span></span> <span data-ttu-id="20ec0-155">Följande kommando använder `Get-Job` cmdleten för att Visa jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-155">The following command uses the `Get-Job` cmdlet to display the job.</span></span>

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   <span data-ttu-id="20ec0-156">`Get-Job`Utdata visar att jobbet körs på "localhost"-datorn eftersom jobbet startade och körs på samma dator (i det här fallet Server01).</span><span class="sxs-lookup"><span data-stu-id="20ec0-156">The `Get-Job` output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

1. <span data-ttu-id="20ec0-157">Använd cmdleten för att hämta resultatet av jobbet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="20ec0-157">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="20ec0-158">Du kan visa resultaten i den interaktiva sessionen eller spara dem till en fil på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-158">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="20ec0-159">Följande kommando hämtar resultatet av jobbet i variabeln $job.</span><span class="sxs-lookup"><span data-stu-id="20ec0-159">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="20ec0-160">Kommandot använder operatorn för omdirigering ( `>` ) för att spara resultatet av jobbet i PsLog.txt-filen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-160">The command uses the redirection operator (`>`) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. <span data-ttu-id="20ec0-161">Använd cmdleten för att avsluta den interaktiva sessionen `Exit-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="20ec0-161">To end the interactive session, use the `Exit-PSSession` cmdlet.</span></span> <span data-ttu-id="20ec0-162">Kommando tolken ändras för att visa att du är tillbaka i den ursprungliga sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-162">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. <span data-ttu-id="20ec0-163">Du kan visa innehållet i `PsLog.txt` filen på Server01-datorn när som helst genom att starta en annan interaktiv session eller köra ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="20ec0-163">To view the contents of the `PsLog.txt` file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="20ec0-164">Den här typen av kommando körs bäst i en PSSession (en permanent anslutning) om du vill använda flera kommandon för att undersöka och hantera data i `PsLog.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-164">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the `PsLog.txt` file.</span></span> <span data-ttu-id="20ec0-165">Mer information om PSSessions finns i [about_PSSessions](about_PSSessions.md).</span><span class="sxs-lookup"><span data-stu-id="20ec0-165">For more information about PSSessions, see [about_PSSessions](about_PSSessions.md).</span></span>

   <span data-ttu-id="20ec0-166">Följande kommandon använder `New-PSSession` cmdleten för att skapa en **PSSession** som är ansluten till Server01-datorn, och de använder `Invoke-Command` cmdleten för att köra `Get-Content` ett kommando i PSSession för att visa innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-166">The following commands use the `New-PSSession` cmdlet to create a **PSSession** that is connected to the Server01 computer, and they use the `Invoke-Command` cmdlet to run a `Get-Content` command in the PSSession to view the contents of the file.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="20ec0-167">Starta ett Fjärrjobb som returnerar resultatet till den lokala datorn (AsJob)</span><span class="sxs-lookup"><span data-stu-id="20ec0-167">Start a remote job that returns the results to the local computer (AsJob)</span></span>

<span data-ttu-id="20ec0-168">Om du vill starta ett jobb på en fjärrdator som returnerar kommando resultatet till den lokala datorn använder du parametern **AsJob** för en cmdlet, till exempel `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20ec0-168">To start a job on a remote computer that returns the command results to the local computer, use the **AsJob** parameter of a cmdlet such as the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="20ec0-169">När du använder **AsJob** -parametern skapas jobbobjektet faktiskt på den lokala datorn även om jobbet körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-169">When you use the **AsJob** parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="20ec0-170">När jobbet har slutförts returneras resultatet till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-170">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="20ec0-171">Du kan använda de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletar) för att hantera alla jobb som skapats av en valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-171">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="20ec0-172">Många av cmdletarna som har **AsJob** -parametrar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation och som inte uppfyller kraven för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="20ec0-172">Many of the cmdlets that have **AsJob** parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

1. <span data-ttu-id="20ec0-173">Följande kommando använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-173">The following command uses the **AsJob** parameter of `Invoke-Command` to start a job on the Server01 computer.</span></span> <span data-ttu-id="20ec0-174">Jobbet kör ett `Get-Eventlog` kommando som hämtar händelserna i system loggen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-174">The job runs a `Get-Eventlog` command that gets the events in the System log.</span></span> <span data-ttu-id="20ec0-175">Du kan använda parametern JobName för att tilldela ett visnings namn till jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-175">You can use the JobName parameter to assign a display name to the job.</span></span>

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   <span data-ttu-id="20ec0-176">Resultatet av kommandot liknar följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="20ec0-176">The results of the command resemble the following sample output.</span></span>

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   <span data-ttu-id="20ec0-177">När parametern **AsJob** används `Invoke-Command` returnerar samma typ av jobb objekt som `Start-Job` returneras.</span><span class="sxs-lookup"><span data-stu-id="20ec0-177">When the **AsJob** parameter is used, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="20ec0-178">Du kan spara jobbobjektet i en variabel, eller så kan du använda ett `Get-Job` kommando för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-178">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="20ec0-179">Observera att värdet för egenskapen location visar att jobbet kördes på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-179">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

1. <span data-ttu-id="20ec0-180">Använd jobb-cmdletarna om du vill hantera ett jobb som har startats med hjälp av **AsJob** -parametern för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20ec0-180">To manage a job started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="20ec0-181">Eftersom jobbobjektet som representerar fjärrjobbet finns på den lokala datorn behöver du inte köra fjärrkommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-181">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

   <span data-ttu-id="20ec0-182">Ta reda på om jobbet har slutförts genom att använda ett `Get-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="20ec0-182">To determine whether the job is complete, use a `Get-Job` command.</span></span> <span data-ttu-id="20ec0-183">Följande kommando hämtar alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-183">The following command gets all of the jobs that were started in the current session.</span></span>

   ```powershell
   Get-Job
   ```

   <span data-ttu-id="20ec0-184">Eftersom fjärrjobbet startade i den aktuella sessionen hämtar ett lokalt `Get-Job` kommando jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-184">Because the remote job was started in the current session, a local `Get-Job` command gets the job.</span></span> <span data-ttu-id="20ec0-185">Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.</span><span class="sxs-lookup"><span data-stu-id="20ec0-185">The State property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. <span data-ttu-id="20ec0-186">Använd cmdleten för att hämta resultatet av jobbet `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="20ec0-186">To get the results of the job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="20ec0-187">Eftersom jobb resultaten automatiskt returneras till datorn där jobbobjektet finns kan du få resultatet med ett lokalt `Receive-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="20ec0-187">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local `Receive-Job` command.</span></span>

   <span data-ttu-id="20ec0-188">Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-188">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="20ec0-189">Den använder sessions-ID: t för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-189">It uses the session ID to identify the job.</span></span> <span data-ttu-id="20ec0-190">Det här kommandot sparar jobb resultaten i variabeln $results.</span><span class="sxs-lookup"><span data-stu-id="20ec0-190">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="20ec0-191">Du kan också omdirigera resultaten till en fil.</span><span class="sxs-lookup"><span data-stu-id="20ec0-191">You can also redirect the results to a file.</span></span>

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="20ec0-192">Starta ett Fjärrjobb som behåller resultatet på fjärrdatorn</span><span class="sxs-lookup"><span data-stu-id="20ec0-192">Start a remote job that keeps the results on the remote computer</span></span>

<span data-ttu-id="20ec0-193">Om du vill starta ett jobb på en fjärrdator som behåller kommando resultatet på fjärrdatorn använder du `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="20ec0-193">To start a job on a remote computer that keeps the command results on the remote computer, use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span> <span data-ttu-id="20ec0-194">Du kan använda den här metoden för att köra jobb på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="20ec0-194">You can use this method to run jobs on multiple computers.</span></span>

<span data-ttu-id="20ec0-195">När du kör ett `Start-Job` kommando via fjärr anslutning skapas jobbobjektet på fjärrdatorn och jobb resultaten bevaras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-195">When you run a `Start-Job` command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="20ec0-196">Alla åtgärder är lokala, från jobbets perspektiv.</span><span class="sxs-lookup"><span data-stu-id="20ec0-196">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="20ec0-197">Du kör bara kommandon via fjärr anslutning för att hantera ett lokalt jobb på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-197">You are just running commands remotely to manage a local job on the remote computer.</span></span>

1. <span data-ttu-id="20ec0-198">Använd `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="20ec0-198">Use the `Invoke-Command` cmdlet to run a `Start-Job` command on a remote computer.</span></span>

   <span data-ttu-id="20ec0-199">Det här kommandot kräver en PSSession (en permanent anslutning).</span><span class="sxs-lookup"><span data-stu-id="20ec0-199">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="20ec0-200">Om du använder parametern ComputerName för `Invoke-Command` att upprätta en tillfällig anslutning `Invoke-Command` anses kommandot vara slutfört när jobbobjektet returneras.</span><span class="sxs-lookup"><span data-stu-id="20ec0-200">If you use the ComputerName parameter of `Invoke-Command` to establish a temporary connection, the `Invoke-Command` command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="20ec0-201">Därför stängs den tillfälliga anslutningen och jobbet avbryts.</span><span class="sxs-lookup"><span data-stu-id="20ec0-201">As a result, the temporary connection is closed, and the job is canceled.</span></span>

   <span data-ttu-id="20ec0-202">Följande kommando använder `New-PSSession` cmdleten för att skapa en PSSession som är ansluten till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-202">The following command uses the `New-PSSession` cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="20ec0-203">Kommandot sparar PSSession i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20ec0-203">The command saves the PSSession in the `$s` variable.</span></span>

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   <span data-ttu-id="20ec0-204">Nästa kommando använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="20ec0-204">The next command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the PSSession.</span></span> <span data-ttu-id="20ec0-205">`Start-Job`Kommandot och `Get-Eventlog` kommandot omges av klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="20ec0-205">The `Start-Job` command and the `Get-Eventlog` command are enclosed in braces.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   <span data-ttu-id="20ec0-206">Resultatet liknar följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="20ec0-206">The results resemble the following sample output.</span></span>

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   <span data-ttu-id="20ec0-207">När du kör ett `Start-Job` fjärrkommando, `Invoke-Command` returnerar samma typ av jobb objekt som `Start-Job` returneras.</span><span class="sxs-lookup"><span data-stu-id="20ec0-207">When you run a `Start-Job` command remotely, `Invoke-Command` returns the same type of job object that `Start-Job` returns.</span></span> <span data-ttu-id="20ec0-208">Du kan spara jobbobjektet i en variabel, eller så kan du använda ett `Get-Job` kommando för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-208">You can save the job object in a variable, or you can use a `Get-Job` command to get the job.</span></span>

   <span data-ttu-id="20ec0-209">Observera att värdet för egenskapen **location** visar att jobbet kördes på den lokala datorn, vilket kallas "localhost", även om jobbet kördes på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-209">Note that the value of the **Location** property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="20ec0-210">Eftersom jobbobjektet skapas på den Server01 datorn och jobbet körs på samma dator betraktas det som ett lokalt bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="20ec0-210">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

1. <span data-ttu-id="20ec0-211">Om du vill hantera ett Fjärrjobb använder du **jobb** -cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="20ec0-211">To manage a remote job, use the **Job** cmdlets.</span></span> <span data-ttu-id="20ec0-212">Eftersom jobbobjektet finns på fjärrdatorn måste du köra fjärrkommandon för att få, stoppa, vänta eller hämta jobb resultaten.</span><span class="sxs-lookup"><span data-stu-id="20ec0-212">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

   <span data-ttu-id="20ec0-213">Om du vill se om jobbet är klart använder du ett `Invoke-Command` kommando för att köra ett `Get-Job` kommando i PSSession som är anslutet till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-213">To see if the job is complete, use an `Invoke-Command` command to run a `Get-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   <span data-ttu-id="20ec0-214">Kommandot returnerar ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="20ec0-214">The command returns a job object.</span></span> <span data-ttu-id="20ec0-215">Egenskapen **State** för jobbobjektet visar att kommandot slutfördes korrekt.</span><span class="sxs-lookup"><span data-stu-id="20ec0-215">The **State** property of the job object shows that the command was completed successfully.</span></span>

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. <span data-ttu-id="20ec0-216">Om du vill hämta resultatet av jobbet använder du `Invoke-Command` cmdleten för att köra ett `Receive-Job` kommando i PSSession som är anslutet till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-216">To get the results of the job, use the `Invoke-Command` cmdlet to run a `Receive-Job` command in the PSSession that is connected to the Server01 computer.</span></span>

   <span data-ttu-id="20ec0-217">Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-217">The following command uses the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="20ec0-218">Den använder sessions-ID: t för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-218">It uses the session ID to identify the job.</span></span> <span data-ttu-id="20ec0-219">Det här kommandot sparar jobb resultatet i `$results` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20ec0-219">This command saves the job results in the `$results` variable.</span></span> <span data-ttu-id="20ec0-220">Parametern Keep to används för `Receive-Job` att behålla resultatet i jobbets cacheminne på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-220">It uses the Keep parameter of `Receive-Job` to keep the result in the job cache on the remote computer.</span></span>

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   <span data-ttu-id="20ec0-221">Du kan också omdirigera resultatet till en fil på den lokala datorn eller fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-221">You can also redirect the results to a file on the local or remote computer.</span></span>
   <span data-ttu-id="20ec0-222">Följande kommando använder en omdirigerings operator för att spara resultatet i en fil på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-222">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a><span data-ttu-id="20ec0-223">Köra som en frånkopplad process</span><span class="sxs-lookup"><span data-stu-id="20ec0-223">How to run as a detached process</span></span>

<span data-ttu-id="20ec0-224">Som tidigare nämnts avslutas alla pågående underordnade jobb tillsammans med sina underordnade processer när den överordnade sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="20ec0-224">As previously mentioned, when the parent session is terminated, all running child jobs are terminated along with their child processes.</span></span> <span data-ttu-id="20ec0-225">Du kan använda fjärr kommunikation på den lokala datorn för att köra jobb som inte är kopplade till den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-225">You can use remoting on the local machine to run jobs that are not attached to the current PowerShell session.</span></span>

<span data-ttu-id="20ec0-226">Skapa en ny PowerShell-session på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="20ec0-226">Create a new PowerShell session on the local machine.</span></span> <span data-ttu-id="20ec0-227">Används `Invoke-Command` för att starta ett jobb i den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-227">The use `Invoke-Command` to start a job in this session.</span></span> <span data-ttu-id="20ec0-228">`Invoke-Command` gör att du kan koppla från en fjärran sluten session och avsluta den överordnade sessionen.</span><span class="sxs-lookup"><span data-stu-id="20ec0-228">`Invoke-Command` allows you to disconnect a remote session and terminate the parent session.</span></span> <span data-ttu-id="20ec0-229">Senare kan du starta en ny PowerShell-session och ansluta till den tidigare frånkopplade sessionen för att återuppta övervakningen av jobbet.</span><span class="sxs-lookup"><span data-stu-id="20ec0-229">Later, you can start a new PowerShell session and connect to the previously disconnected session to resume monitoring the job.</span></span> <span data-ttu-id="20ec0-230">Alla data som returnerades till den ursprungliga PowerShell-sessionen försvinner dock när sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="20ec0-230">However, any data that was returned to the original PowerShell session is lost when that session is terminated.</span></span> <span data-ttu-id="20ec0-231">Det är bara nya data objekt som genereras efter från kopplingen som returneras vid åter anslutning.</span><span class="sxs-lookup"><span data-stu-id="20ec0-231">Only new data objects generated after the disconnect are returned when re-connected.</span></span>

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

<span data-ttu-id="20ec0-232">I det här exemplet är jobben fortfarande kopplade till en överordnad PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="20ec0-232">For this example, the jobs are still attached to a parent PowerShell session.</span></span>
<span data-ttu-id="20ec0-233">Den överordnade sessionen är dock inte den ursprungliga PowerShell-sessionen där `Invoke-Command` kördes.</span><span class="sxs-lookup"><span data-stu-id="20ec0-233">However, the parent session is not the original PowerShell session where `Invoke-Command` was run.</span></span>

## <a name="see-also"></a><span data-ttu-id="20ec0-234">Se även</span><span class="sxs-lookup"><span data-stu-id="20ec0-234">See also</span></span>

- [<span data-ttu-id="20ec0-235">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="20ec0-235">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="20ec0-236">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="20ec0-236">about_Job_Details</span></span>](about_Job_Details.md)
- [<span data-ttu-id="20ec0-237">about_Remote</span><span class="sxs-lookup"><span data-stu-id="20ec0-237">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="20ec0-238">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="20ec0-238">about_Remote_Variables</span></span>](about_Remote_Variables.md)
- [<span data-ttu-id="20ec0-239">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="20ec0-239">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="20ec0-240">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-240">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="20ec0-241">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-241">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="20ec0-242">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="20ec0-242">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="20ec0-243">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-243">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="20ec0-244">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="20ec0-244">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="20ec0-245">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="20ec0-245">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="20ec0-246">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="20ec0-246">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="20ec0-247">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="20ec0-247">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
