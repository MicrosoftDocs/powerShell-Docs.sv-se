---
description: Beskriver hur du kör bakgrunds jobb på fjärrdatorer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: ad0400c4b4c25c9b0c7133bd916af5056dab1430
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270476"
---
# <a name="about-remote-jobs"></a><span data-ttu-id="330b4-104">Om Fjärrjobb</span><span class="sxs-lookup"><span data-stu-id="330b4-104">About Remote Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="330b4-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="330b4-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="330b4-106">Beskriver hur du kör bakgrunds jobb på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="330b4-106">Describes how to run background jobs on remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="330b4-107">DETALJERAD BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="330b4-107">DETAILED DESCRIPTION</span></span>

<span data-ttu-id="330b4-108">Ett bakgrunds jobb är ett kommando som körs asynkront utan att interagera med den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-108">A background job is a command that runs asynchronously without interacting with the current session.</span></span> <span data-ttu-id="330b4-109">Kommando tolken returnerar omedelbart och du kan fortsätta att använda sessionen medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="330b4-109">The command prompt returns immediately, and you can continue to use the session while the job runs.</span></span>

<span data-ttu-id="330b4-110">Som standard körs bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-110">By default, background jobs run on the local computer.</span></span> <span data-ttu-id="330b4-111">Du kan dock använda flera olika procedurer för att köra bakgrunds jobb på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="330b4-111">However, you can use several different procedures to run background jobs on remote computers.</span></span>

<span data-ttu-id="330b4-112">I det här avsnittet beskrivs hur du kör ett bakgrunds jobb på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="330b4-112">This topic explains how to run a background job on a remote computer.</span></span> <span data-ttu-id="330b4-113">Information om hur du kör bakgrunds jobb på en lokal dator finns [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="330b4-113">For information about how to run background jobs on a local computer, see [about_Jobs](about_Jobs.md).</span></span> <span data-ttu-id="330b4-114">Mer information om bakgrunds jobb finns [about_Job_Details](about_Job_Details.md).</span><span class="sxs-lookup"><span data-stu-id="330b4-114">For more information about background jobs, see [about_Job_Details](about_Job_Details.md).</span></span>

## <a name="remote-background-jobs"></a><span data-ttu-id="330b4-115">FJÄRRAN SLUTEN BAKGRUNDS JOBB</span><span class="sxs-lookup"><span data-stu-id="330b4-115">REMOTE BACKGROUND JOBS</span></span>

<span data-ttu-id="330b4-116">Du kan köra bakgrunds jobb på fjärrdatorer genom att använda tre olika metoder.</span><span class="sxs-lookup"><span data-stu-id="330b4-116">You can run background jobs on remote computers by using three different methods.</span></span>

- <span data-ttu-id="330b4-117">Starta en interaktiv session med en fjärran sluten dator och starta ett jobb i den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-117">Start an interactive session with a remote computer, and start a job in the interactive session.</span></span> <span data-ttu-id="330b4-118">Procedurerna är desamma som att köra ett lokalt jobb, även om alla åtgärder utförs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-118">The procedures are the same as running a local job, although all actions are performed on the remote computer.</span></span>

- <span data-ttu-id="330b4-119">Kör ett bakgrunds jobb på en fjärrdator som returnerar sina resultat till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-119">Run a background job on a remote computer that returns its results to the local computer.</span></span> <span data-ttu-id="330b4-120">Använd den här metoden när du vill samla in resultaten av bakgrunds jobb och underhålla dem på en central plats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-120">Use this method when you want to collect the results of background jobs and maintain them in a central location on the local computer.</span></span>

- <span data-ttu-id="330b4-121">Kör ett bakgrunds jobb på en fjärrdator som underhåller sina resultat på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-121">Run a background job on a remote computer that maintains its results on the remote computer.</span></span> <span data-ttu-id="330b4-122">Använd den här metoden när jobb data är säkrare att behållas på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-122">Use this method when the job data is more securely maintained on the originating computer.</span></span>

### <a name="start-a-background-job-in-an-interactive-session"></a><span data-ttu-id="330b4-123">STARTA ETT BAKGRUNDS JOBB I EN INTERAKTIV SESSION</span><span class="sxs-lookup"><span data-stu-id="330b4-123">START A BACKGROUND JOB IN AN INTERACTIVE SESSION</span></span>

<span data-ttu-id="330b4-124">Du kan starta en interaktiv session med en fjärrdator och sedan starta ett bakgrunds jobb under den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-124">You can start an interactive session with a remote computer and then start a background job during the interactive session.</span></span> <span data-ttu-id="330b4-125">Mer information om interaktiva sessioner finns about_Remote och se Enter-PSSession.</span><span class="sxs-lookup"><span data-stu-id="330b4-125">For more information about interactive sessions, see about_Remote, and see Enter-PSSession.</span></span>

<span data-ttu-id="330b4-126">Proceduren för att starta ett bakgrunds jobb i en interaktiv session är nästan identisk med proceduren för att starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-126">The procedure for starting a background job in an interactive session is almost identical to the procedure for starting a background job on the local computer.</span></span> <span data-ttu-id="330b4-127">Alla åtgärder sker dock på fjärrdatorn, inte på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-127">However, all of the operations occur on the remote computer, not the local computer.</span></span>

#### <a name="step-1-enter-pssession"></a><span data-ttu-id="330b4-128">STEG 1: ANGE-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="330b4-128">STEP 1: ENTER-PSSESSION</span></span>

<span data-ttu-id="330b4-129">Använd Enter-PSSession-cmdleten för att starta en interaktiv session med en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="330b4-129">Use the Enter-PSSession cmdlet to start an interactive session with a remote computer.</span></span> <span data-ttu-id="330b4-130">Du kan använda parametern ComputerName i Enter-PSSession för att upprätta en tillfällig anslutning för den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-130">You can use the ComputerName parameter of Enter-PSSession to establish a temporary connection for the interactive session.</span></span> <span data-ttu-id="330b4-131">Du kan också använda parametern session för att köra den interaktiva sessionen i en PowerShell-session (PSSession).</span><span class="sxs-lookup"><span data-stu-id="330b4-131">Or, you can use the Session parameter to run the interactive session in a PowerShell session (PSSession).</span></span>

<span data-ttu-id="330b4-132">Följande kommando startar en interaktiv session på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-132">The following command starts an interactive session on the Server01 computer.</span></span>

```powershell
C:\PS> Enter-PSSession -computername Server01
```

<span data-ttu-id="330b4-133">Kommando tolken ändras för att visa att du nu är ansluten till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-133">The command prompt changes to show that you are now connected to the Server01 computer.</span></span>

```
Server01\C:>
```

#### <a name="step-2-start-job"></a><span data-ttu-id="330b4-134">STEG 2: START-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-134">STEP 2: START-JOB</span></span>

<span data-ttu-id="330b4-135">Om du vill starta ett bakgrunds jobb i sessionen använder du Start-Job cmdlet.</span><span class="sxs-lookup"><span data-stu-id="330b4-135">To start a background job in the session, use the Start-Job cmdlet.</span></span>

<span data-ttu-id="330b4-136">Följande kommando kör ett bakgrunds jobb som hämtar händelserna i händelse loggen för Windows PowerShell på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-136">The following command runs a background job that gets the events in the Windows PowerShell event log on the Server01 computer.</span></span> <span data-ttu-id="330b4-137">Cmdleten Start-Job returnerar ett objekt som representerar jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-137">The Start-Job cmdlet returns an object that represents the job.</span></span>

<span data-ttu-id="330b4-138">Det här kommandot sparar jobbobjektet i jobb- \$ variabeln.</span><span class="sxs-lookup"><span data-stu-id="330b4-138">This command saves the job object in the \$job variable.</span></span>

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

<span data-ttu-id="330b4-139">När jobbet körs kan du använda den interaktiva sessionen för att köra andra kommandon, inklusive andra bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="330b4-139">While the job runs, you can use the interactive session to run other commands, including other background jobs.</span></span> <span data-ttu-id="330b4-140">Du måste dock låta den interaktiva sessionen vara öppen tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="330b4-140">However, you must keep the interactive session open until the job is completed.</span></span> <span data-ttu-id="330b4-141">Om du slutar sessionen avbryts jobbet och resultaten går förlorade.</span><span class="sxs-lookup"><span data-stu-id="330b4-141">If you end the session, the job is interrupted, and the results are lost.</span></span>

#### <a name="step-3-get-job"></a><span data-ttu-id="330b4-142">STEG 3: HÄMTA JOBB</span><span class="sxs-lookup"><span data-stu-id="330b4-142">STEP 3: GET-JOB</span></span>

<span data-ttu-id="330b4-143">Om du vill ta reda på om jobbet har slutförts, visar du värdet för \$ jobb variabeln eller använder cmdleten Get-Job för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-143">To find out if the job is complete, display the value of the \$job variable, or use the Get-Job cmdlet to get the job.</span></span> <span data-ttu-id="330b4-144">Följande kommando använder cmdleten Get-Job för att Visa jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-144">The following command uses the Get-Job cmdlet to display the job.</span></span>

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

<span data-ttu-id="330b4-145">Get-Job utdata visar att jobbet körs på "localhost"-datorn eftersom jobbet startade och körs på samma dator (i det här fallet Server01).</span><span class="sxs-lookup"><span data-stu-id="330b4-145">The Get-Job output shows that job is running on the "localhost" computer because the job was started on and is running on the same computer (in this case, Server01).</span></span>

#### <a name="step-4-receive-job"></a><span data-ttu-id="330b4-146">STEG 4: RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-146">STEP 4: RECEIVE-JOB</span></span>

<span data-ttu-id="330b4-147">Använd Receive-Job-cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-147">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="330b4-148">Du kan visa resultaten i den interaktiva sessionen eller spara dem till en fil på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-148">You can display the results in the interactive session or save them to a file on the remote computer.</span></span> <span data-ttu-id="330b4-149">Följande kommando hämtar resultatet av jobbet i variabeln $job.</span><span class="sxs-lookup"><span data-stu-id="330b4-149">The following command gets the results of the job in the $job variable.</span></span> <span data-ttu-id="330b4-150">Kommandot använder operatorn för omdirigering (>) för att spara resultatet av jobbet i PsLog.txt-filen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-150">The command uses the redirection operator (>) to save the results of the job in the PsLog.txt file on the Server01 computer.</span></span>

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a><span data-ttu-id="330b4-151">STEG 5: EXIT-PSSESSION</span><span class="sxs-lookup"><span data-stu-id="330b4-151">STEP 5: EXIT-PSSESSION</span></span>

<span data-ttu-id="330b4-152">Använd Exit-PSSession-cmdleten om du vill avsluta den interaktiva sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-152">To end the interactive session, use the Exit-PSSession cmdlet.</span></span> <span data-ttu-id="330b4-153">Kommando tolken ändras för att visa att du är tillbaka i den ursprungliga sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-153">The command prompt changes to show that you are back in the original session on the local computer.</span></span>

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a><span data-ttu-id="330b4-154">STEG 6: INVOKE-COMMAND: GET-CONTENT</span><span class="sxs-lookup"><span data-stu-id="330b4-154">STEP 6: INVOKE-COMMAND: GET-CONTENT</span></span>

<span data-ttu-id="330b4-155">Om du vill visa innehållet i PsLog.txt-filen på Server01-datorn när som helst startar du en annan interaktiv session eller kör ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="330b4-155">To view the contents of the PsLog.txt file on the Server01 computer at any time, start another interactive session, or run a remote command.</span></span> <span data-ttu-id="330b4-156">Den här typen av kommando körs bäst i en PSSession (en permanent anslutning) om du vill använda flera kommandon för att undersöka och hantera data i PsLog.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="330b4-156">This type of command is best run in a PSSession (a persistent connection) in case you want to use several commands to investigate and manage the data in the PsLog.txt file.</span></span> <span data-ttu-id="330b4-157">Mer information om PSSessions finns i about_PSSessions.</span><span class="sxs-lookup"><span data-stu-id="330b4-157">For more information about PSSessions, see about_PSSessions.</span></span>

<span data-ttu-id="330b4-158">Följande kommandon använder New-PSSession cmdlet för att skapa en PSSession som är ansluten till Server01-datorn, och de använder cmdleten Invoke-Command för att köra ett Get-Content kommando i PSSession för att visa innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="330b4-158">The following commands use the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer, and they use the Invoke-Command cmdlet to run a Get-Content command in the PSSession to view the contents of the file.</span></span>

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a><span data-ttu-id="330b4-159">Starta ett Fjärrjobb som returnerar resultaten till den lokala datorn \( ASJOB\)</span><span class="sxs-lookup"><span data-stu-id="330b4-159">START A REMOTE JOB THAT RETURNS THE RESULTS TO THE LOCAL COMPUTER \(ASJOB\)</span></span>

<span data-ttu-id="330b4-160">Om du vill starta ett bakgrunds jobb på en fjärrdator som returnerar kommando resultatet till den lokala datorn använder du parametern AsJob för en cmdlet som Invoke-Command-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="330b4-160">To start a background job on a remote computer that returns the command results to the local computer, use the AsJob parameter of a cmdlet such as the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="330b4-161">När du använder AsJob-parametern skapas jobbobjektet faktiskt på den lokala datorn även om jobbet körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-161">When you use the AsJob parameter, the job object is actually created on the local computer even though the job runs on the remote computer.</span></span> <span data-ttu-id="330b4-162">När jobbet har slutförts returneras resultatet till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-162">When the job is completed, the results are returned to the local computer.</span></span>

<span data-ttu-id="330b4-163">Du kan använda de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletar) för att hantera alla jobb som skapats av en valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="330b4-163">You can use the cmdlets that contain the Job noun (the Job cmdlets) to manage any job created by any cmdlet.</span></span> <span data-ttu-id="330b4-164">Många av cmdletarna som har AsJob-parametrar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation och som inte uppfyller kraven för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="330b4-164">Many of the cmdlets that have AsJob parameters do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting and that do not meet the requirements for remoting.</span></span>

#### <a name="step-1-invoke-command--asjob"></a><span data-ttu-id="330b4-165">STEG 1: ANROPA-COMMAND-ASJOB</span><span class="sxs-lookup"><span data-stu-id="330b4-165">STEP 1: INVOKE-COMMAND -ASJOB</span></span>

<span data-ttu-id="330b4-166">Följande kommando använder AsJob-parametern för Invoke-Command för att starta ett bakgrunds jobb på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-166">The following command uses the AsJob parameter of Invoke-Command to start a background job on the Server01 computer.</span></span> <span data-ttu-id="330b4-167">Jobbet kör ett Get-Eventlog-kommando som hämtar händelserna i system loggen.</span><span class="sxs-lookup"><span data-stu-id="330b4-167">The job runs a Get-Eventlog command that gets the events in the System log.</span></span> <span data-ttu-id="330b4-168">Du kan använda parametern JobName för att tilldela ett visnings namn till jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-168">You can use the JobName parameter to assign a display name to the job.</span></span>

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

<span data-ttu-id="330b4-169">Resultatet av kommandot liknar följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="330b4-169">The results of the command resemble the following sample output.</span></span>

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

<span data-ttu-id="330b4-170">När parametern AsJob används returnerar Invoke-Command samma typ av jobb objekt som Start-Job returnerar.</span><span class="sxs-lookup"><span data-stu-id="330b4-170">When the AsJob parameter is used, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="330b4-171">Du kan spara jobbobjektet i en variabel, eller så kan du använda ett Get-Job-kommando för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-171">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="330b4-172">Observera att värdet för egenskapen location visar att jobbet kördes på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-172">Note that the value of the Location property shows that the job ran on the Server01 computer.</span></span>

#### <a name="step-2-get-job"></a><span data-ttu-id="330b4-173">STEG 2: GET-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-173">STEP 2: GET-JOB</span></span>

<span data-ttu-id="330b4-174">Använd jobb-cmdletarna för att hantera ett jobb som har startats med hjälp av parametern AsJob i cmdleten Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="330b4-174">To manage a job started by using the AsJob parameter of the Invoke-Command cmdlet, use the Job cmdlets.</span></span> <span data-ttu-id="330b4-175">Eftersom jobbobjektet som representerar fjärrjobbet finns på den lokala datorn behöver du inte köra fjärrkommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-175">Because the job object that represents the remote job is on the local computer, you do not need to run remote commands to manage the job.</span></span>

<span data-ttu-id="330b4-176">Använd ett Get-Job-kommando för att avgöra om jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="330b4-176">To determine whether the job is complete, use a Get-Job command.</span></span> <span data-ttu-id="330b4-177">Följande kommando hämtar alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="330b4-177">The following command gets all of the jobs that were started in the current session.</span></span>

```powershell
get-job
```

<span data-ttu-id="330b4-178">Eftersom fjärrjobbet startade i den aktuella sessionen hämtar ett lokalt Get-Job-kommando jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-178">Because the remote job was started in the current session, a local Get-Job command gets the job.</span></span> <span data-ttu-id="330b4-179">Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.</span><span class="sxs-lookup"><span data-stu-id="330b4-179">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a><span data-ttu-id="330b4-180">STEG 3: RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-180">STEP 3: RECEIVE-JOB</span></span>

<span data-ttu-id="330b4-181">Använd Receive-Job-cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-181">To get the results of the job, use the Receive-Job cmdlet.</span></span> <span data-ttu-id="330b4-182">Eftersom jobb resultaten automatiskt returneras till datorn där jobbobjektet finns kan du hämta resultatet med ett lokalt Receive-Job-kommando.</span><span class="sxs-lookup"><span data-stu-id="330b4-182">Because the job results are automatically returned to the computer where the job object resides, you can get the results with a local Receive-Job command.</span></span>

<span data-ttu-id="330b4-183">Följande kommando använder cmdleten Receive-Job för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-183">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="330b4-184">Den använder sessions-ID: t för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-184">It uses the session ID to identify the job.</span></span> <span data-ttu-id="330b4-185">Det här kommandot sparar jobb resultaten i variabeln $results.</span><span class="sxs-lookup"><span data-stu-id="330b4-185">This command saves the job results in the $results variable.</span></span> <span data-ttu-id="330b4-186">Du kan också omdirigera resultaten till en fil.</span><span class="sxs-lookup"><span data-stu-id="330b4-186">You can also redirect the results to a file.</span></span>

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a><span data-ttu-id="330b4-187">STARTA ETT FJÄRRJOBB SOM BEHÅLLER RESULTATET PÅ FJÄRRDATORN</span><span class="sxs-lookup"><span data-stu-id="330b4-187">START A REMOTE JOB THAT KEEPS THE RESULTS ON THE REMOTE COMPUTER</span></span>

<span data-ttu-id="330b4-188">Om du vill starta ett bakgrunds jobb på en fjärrdator som behåller kommando resultatet på fjärrdatorn, använder du Invoke-Command cmdlet för att köra ett Start-Job kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="330b4-188">To start a background job on a remote computer that keeps the command results on the remote computer, use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span> <span data-ttu-id="330b4-189">Du kan använda den här metoden för att köra bakgrunds jobb på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="330b4-189">You can use this method to run background jobs on multiple computers.</span></span>

<span data-ttu-id="330b4-190">När du kör ett Start-Job-kommando via fjärr anslutning skapas jobbobjektet på fjärrdatorn och jobb resultaten bevaras på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-190">When you run a Start-Job command remotely, the job object is created on the remote computer, and the job results are maintained on the remote computer.</span></span>
<span data-ttu-id="330b4-191">Alla åtgärder är lokala, från jobbets perspektiv.</span><span class="sxs-lookup"><span data-stu-id="330b4-191">From the perspective of the job, all operations are local.</span></span> <span data-ttu-id="330b4-192">Du kör bara kommandon via fjärr anslutning för att hantera ett lokalt jobb på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-192">You are just running commands remotely to manage a local job on the remote computer.</span></span>

#### <a name="step-1-invoke-command-start-job"></a><span data-ttu-id="330b4-193">STEG 1: INVOKE-KOMMANDOT START-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-193">STEP 1: INVOKE-COMMAND START-JOB</span></span>

<span data-ttu-id="330b4-194">Använd Invoke-Command cmdlet för att köra ett Start-Job kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="330b4-194">Use the Invoke-Command cmdlet to run a Start-Job command on a remote computer.</span></span>

<span data-ttu-id="330b4-195">Det här kommandot kräver en PSSession (en permanent anslutning).</span><span class="sxs-lookup"><span data-stu-id="330b4-195">This command requires a PSSession (a persistent connection).</span></span> <span data-ttu-id="330b4-196">Om du använder parametern ComputerName för Invoke-Command för att upprätta en tillfällig anslutning anses Invoke-Command-kommandot vara slutfört när jobbobjektet returneras.</span><span class="sxs-lookup"><span data-stu-id="330b4-196">If you use the ComputerName parameter of Invoke-Command to establish a temporary connection, the Invoke-Command command is considered to be complete when the job object is returned.</span></span> <span data-ttu-id="330b4-197">Därför stängs den tillfälliga anslutningen och jobbet avbryts.</span><span class="sxs-lookup"><span data-stu-id="330b4-197">As a result, the temporary connection is closed, and the job is canceled.</span></span>

<span data-ttu-id="330b4-198">Följande kommando använder cmdleten New-PSSession för att skapa en PSSession som är ansluten till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-198">The following command uses the New-PSSession cmdlet to create a PSSession that is connected to the Server01 computer.</span></span> <span data-ttu-id="330b4-199">Kommandot sparar PSSession i \$ s-variabeln.</span><span class="sxs-lookup"><span data-stu-id="330b4-199">The command saves the PSSession in the \$s variable.</span></span>

```powershell
$s = new-pssession -computername Server01
```

<span data-ttu-id="330b4-200">Nästa kommando använder cmdleten Invoke-Command för att köra ett Start-Job-kommando i PSSession.</span><span class="sxs-lookup"><span data-stu-id="330b4-200">The next command uses the Invoke-Command cmdlet to run a Start-Job command in the PSSession.</span></span> <span data-ttu-id="330b4-201">Kommandot Start-Job och kommandot Get-Eventlog omges av klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="330b4-201">The Start-Job command and the Get-Eventlog command are enclosed in braces.</span></span>

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

<span data-ttu-id="330b4-202">Resultatet liknar följande exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="330b4-202">The results resemble the following sample output.</span></span>

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

<span data-ttu-id="330b4-203">När du kör ett Start-Job kommando på distans, returnerar Invoke-Command samma typ av jobb objekt som Start-Job returnerar.</span><span class="sxs-lookup"><span data-stu-id="330b4-203">When you run a Start-Job command remotely, Invoke-Command returns the same type of job object that Start-Job returns.</span></span> <span data-ttu-id="330b4-204">Du kan spara jobbobjektet i en variabel, eller så kan du använda ett Get-Job-kommando för att hämta jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-204">You can save the job object in a variable, or you can use a Get-Job command to get the job.</span></span>

<span data-ttu-id="330b4-205">Observera att värdet för egenskapen location visar att jobbet kördes på den lokala datorn, vilket kallas "LocalHost", även om jobbet kördes på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-205">Note that the value of the Location property shows that the job ran on the local computer, known as "LocalHost", even though the job ran on the Server01 computer.</span></span> <span data-ttu-id="330b4-206">Eftersom jobbobjektet skapas på den Server01 datorn och jobbet körs på samma dator betraktas det som ett lokalt bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="330b4-206">Because the job object is created on the Server01 computer and the job runs on the same computer, it is considered to be a local background job.</span></span>

#### <a name="step-2-invoke-command-get-job"></a><span data-ttu-id="330b4-207">STEG 2: ANROPA-KOMMANDO GET-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-207">STEP 2: INVOKE-COMMAND GET-JOB</span></span>

<span data-ttu-id="330b4-208">Använd jobb-cmdletarna om du vill hantera ett fjärran slutet bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="330b4-208">To manage a remote background job, use the Job cmdlets.</span></span> <span data-ttu-id="330b4-209">Eftersom jobbobjektet finns på fjärrdatorn måste du köra fjärrkommandon för att få, stoppa, vänta eller hämta jobb resultaten.</span><span class="sxs-lookup"><span data-stu-id="330b4-209">Because the job object is on the remote computer, you need to run remote commands to get, stop, wait for, or retrieve the job results.</span></span>

<span data-ttu-id="330b4-210">Om du vill se om jobbet är klart använder du ett Invoke-Command kommando för att köra ett Get-Job kommando i PSSession som är anslutet till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-210">To see if the job is complete, use an Invoke-Command command to run a Get-Job command in the PSSession that is connected to the Server01 computer.</span></span>

```powershell
invoke-command -session $s -scriptblock {get-job}
```

<span data-ttu-id="330b4-211">Kommandot returnerar ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="330b4-211">The command returns a job object.</span></span> <span data-ttu-id="330b4-212">Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.</span><span class="sxs-lookup"><span data-stu-id="330b4-212">The State property of the job object shows that the command was completed successfully.</span></span>

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a><span data-ttu-id="330b4-213">STEG 3: INVOKE-KOMMANDOT RECEIVE-JOB</span><span class="sxs-lookup"><span data-stu-id="330b4-213">STEP 3: INVOKE-COMMAND RECEIVE-JOB</span></span>

<span data-ttu-id="330b4-214">Om du vill hämta resultatet av jobbet använder du cmdleten Invoke-Command för att köra ett Receive-Job kommando i PSSession som är anslutet till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-214">To get the results of the job, use the Invoke-Command cmdlet to run a Receive-Job command in the PSSession that is connected to the Server01 computer.</span></span>

<span data-ttu-id="330b4-215">Följande kommando använder cmdleten Receive-Job för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-215">The following command uses the Receive-Job cmdlet to get the results of the job.</span></span> <span data-ttu-id="330b4-216">Den använder sessions-ID: t för att identifiera jobbet.</span><span class="sxs-lookup"><span data-stu-id="330b4-216">It uses the session ID to identify the job.</span></span> <span data-ttu-id="330b4-217">Det här kommandot sparar jobb resultaten i \$ variabeln Results.</span><span class="sxs-lookup"><span data-stu-id="330b4-217">This command saves the job results in the \$results variable.</span></span> <span data-ttu-id="330b4-218">Parametern Behåll för Receive-Job används för att behålla resultatet i jobbets cacheminne på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-218">It uses the Keep parameter of Receive-Job to keep the result in the job cache on the remote computer.</span></span>

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

<span data-ttu-id="330b4-219">Du kan också omdirigera resultatet till en fil på den lokala datorn eller fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-219">You can also redirect the results to a file on the local or remote computer.</span></span>
<span data-ttu-id="330b4-220">Följande kommando använder en omdirigerings operator för att spara resultatet i en fil på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="330b4-220">The following command uses a redirection operator to save the results in a file on the Server01 computer.</span></span>

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a><span data-ttu-id="330b4-221">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="330b4-221">SEE ALSO</span></span>

[<span data-ttu-id="330b4-222">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="330b4-222">about_Jobs</span></span>](about_Jobs.md)

[<span data-ttu-id="330b4-223">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="330b4-223">about_Job_Details</span></span>](about_Job_Details.md)

[<span data-ttu-id="330b4-224">about_Remote</span><span class="sxs-lookup"><span data-stu-id="330b4-224">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="330b4-225">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="330b4-225">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="330b4-226">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="330b4-226">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="330b4-227">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="330b4-227">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)

[<span data-ttu-id="330b4-228">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="330b4-228">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)

[<span data-ttu-id="330b4-229">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="330b4-229">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)

[<span data-ttu-id="330b4-230">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="330b4-230">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)

[<span data-ttu-id="330b4-231">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="330b4-231">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)

[<span data-ttu-id="330b4-232">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="330b4-232">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="330b4-233">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="330b4-233">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="330b4-234">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="330b4-234">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
