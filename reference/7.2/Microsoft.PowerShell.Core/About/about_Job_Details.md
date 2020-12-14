---
description: Innehåller information om bakgrunds jobb på lokala datorer och fjärrdatorer.
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 1ceb0be9cc140b69afdebaaf336dad75e482aa22
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94711004"
---
# <a name="about-job-details"></a><span data-ttu-id="01e3d-103">Om jobb information</span><span class="sxs-lookup"><span data-stu-id="01e3d-103">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="01e3d-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="01e3d-104">Short description</span></span>
<span data-ttu-id="01e3d-105">Innehåller information om bakgrunds jobb på lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="01e3d-105">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="01e3d-106">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="01e3d-106">Detailed description</span></span>

<span data-ttu-id="01e3d-107">Det här avsnittet beskriver konceptet med ett bakgrunds jobb och ger teknisk information om hur bakgrunds jobb fungerar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01e3d-107">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="01e3d-108">Det här avsnittet är ett tillägg till avsnitten [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md)och [about_Remote_Jobs](about_Remote_Jobs.md) .</span><span class="sxs-lookup"><span data-stu-id="01e3d-108">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="01e3d-109">Om bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-109">About background jobs</span></span>

<span data-ttu-id="01e3d-110">Ett bakgrunds jobb kör ett kommando eller uttryck asynkront.</span><span class="sxs-lookup"><span data-stu-id="01e3d-110">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="01e3d-111">Det kan köra en cmdlet, en funktion, ett skript eller någon annan kommando-baserad uppgift.</span><span class="sxs-lookup"><span data-stu-id="01e3d-111">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="01e3d-112">Den är utformad för att köra kommandon som tar en längre tid, men du kan använda det för att köra alla kommandon i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="01e3d-112">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="01e3d-113">När ett synkront kommando körs, ignoreras PowerShell-Kommandotolken tills kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="01e3d-113">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="01e3d-114">Men ett bakgrunds jobb förhindrar inte PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="01e3d-114">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="01e3d-115">Ett kommando för att starta ett bakgrunds jobb returnerar ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="01e3d-115">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="01e3d-116">Prompten återgår direkt så att du kan arbeta med andra uppgifter medan bakgrunds jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="01e3d-116">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="01e3d-117">När du startar ett bakgrunds jobb får du dock inte resultaten direkt även om jobbet körs mycket snabbt.</span><span class="sxs-lookup"><span data-stu-id="01e3d-117">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="01e3d-118">Jobbobjektet som returneras innehåller användbar information om jobbet, men det innehåller inte jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-118">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="01e3d-119">Du måste köra ett separat kommando för att hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-119">You must run a separate command to get the job results.</span></span> <span data-ttu-id="01e3d-120">Du kan också köra kommandon för att stoppa jobbet, vänta tills jobbet har slutförts och ta bort jobbet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-120">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="01e3d-121">För att göra tids inställningen för ett bakgrunds jobb oberoende av andra kommandon körs varje bakgrunds jobb i en egen PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="01e3d-121">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="01e3d-122">Det kan dock vara en tillfällig anslutning som bara skapas för att köra jobbet och sedan destrueras, eller så kan det vara en permanent **PSSession** som du kan använda för att köra flera relaterade jobb eller kommandon.</span><span class="sxs-lookup"><span data-stu-id="01e3d-122">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="01e3d-123">Använda jobb-cmdletar</span><span class="sxs-lookup"><span data-stu-id="01e3d-123">Using the job cmdlets</span></span>

<span data-ttu-id="01e3d-124">Använd ett `Start-Job` kommando för att starta ett bakgrunds jobb på en lokal dator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-124">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="01e3d-125">`Start-Job` Returnerar ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="01e3d-125">`Start-Job` returns a job object.</span></span> <span data-ttu-id="01e3d-126">Du kan också hämta objekt som representerar de jobb som startades på den lokala datorn med hjälp av `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01e3d-126">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="01e3d-127">Hämta jobb resultaten med hjälp av ett `Receive-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="01e3d-127">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="01e3d-128">Om jobbet inte är klart `Receive-Job` returneras delvis resultat.</span><span class="sxs-lookup"><span data-stu-id="01e3d-128">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="01e3d-129">Du kan också använda `Wait-Job` cmdleten för att ignorera kommando tolken tills ett eller flera av jobben som startades i sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="01e3d-129">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="01e3d-130">Om du vill stoppa ett bakgrunds jobb använder du `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01e3d-130">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="01e3d-131">Använd cmdleten om du vill ta bort ett jobb `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-131">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="01e3d-132">Mer information om hur cmdletarna fungerar finns i hjälp avsnittet för varje cmdlet och se [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="01e3d-132">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="01e3d-133">Starta bakgrunds jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="01e3d-133">Starting background jobs on remote computers</span></span>

<span data-ttu-id="01e3d-134">Du kan skapa och hantera bakgrunds jobb på en lokal dator eller fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-134">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="01e3d-135">Om du vill köra ett bakgrunds jobb via en fjärr anslutning använder du parametern **AsJob** för en cmdlet, till exempel `Invoke-Command` eller använder `Invoke-Command` cmdleten för att fjärrköra ett `Start-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="01e3d-135">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="01e3d-136">Du kan också starta ett bakgrunds jobb i en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="01e3d-136">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="01e3d-137">Mer information om fjärran sluten bakgrunds jobb finns [about_Remote_Jobs](about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="01e3d-137">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="01e3d-138">Underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-138">Child jobs</span></span>

<span data-ttu-id="01e3d-139">Varje bakgrunds jobb består av ett överordnat jobb och ett eller flera underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-139">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="01e3d-140">I jobb som har startats med `Start-Job` eller **AsJob** -parametern för `Invoke-Command` är det överordnade jobbet en chef.</span><span class="sxs-lookup"><span data-stu-id="01e3d-140">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="01e3d-141">Inga kommandon körs eller inga resultat returneras.</span><span class="sxs-lookup"><span data-stu-id="01e3d-141">It does not run any commands or return any results.</span></span> <span data-ttu-id="01e3d-142">Kommandona körs faktiskt av de underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="01e3d-142">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="01e3d-143">Jobb som startas med andra cmdlets kan fungera annorlunda.</span><span class="sxs-lookup"><span data-stu-id="01e3d-143">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="01e3d-144">De underordnade jobben lagras i egenskapen **ChildJobs** för objektet överordnat jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-144">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="01e3d-145">Egenskapen **ChildJobs** kan innehålla ett eller flera underordnade jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="01e3d-145">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="01e3d-146">De underordnade jobb objekten har ett **namn**, **ID** och **InstanceID** som skiljer sig från det överordnade jobbet så att du kan hantera de överordnade och underordnade jobben individuellt eller som en enhet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-146">The child job objects have a **Name**, **ID**, and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="01e3d-147">Om du vill hämta de överordnade och underordnade jobben för ett jobb använder du parametern **IncludeChildJobs** för `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01e3d-147">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="01e3d-148">**IncludeChildJob** -parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="01e3d-148">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="01e3d-149">Använd parametern **ChildJobState** för cmdleten om du vill hämta det överordnade jobbet och bara de underordnade jobben med ett visst **tillstånds** värde `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-149">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="01e3d-150">**ChildJobState** -parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="01e3d-150">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="01e3d-151">Använd egenskapen **ChildJob** för det överordnade jobbet för att hämta de underordnade jobben för ett jobb i alla versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01e3d-151">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="01e3d-152">Du kan också använda ett `Get-Job` kommando på det underordnade jobbet, som du ser i följande kommando:</span><span class="sxs-lookup"><span data-stu-id="01e3d-152">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="01e3d-153">Konfigurationen av det underordnade jobbet beror på vilket kommando du använder för att starta jobbet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-153">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="01e3d-154">När du använder `Start-Job` för att starta ett jobb på en lokal dator består jobbet av ett överordnat överordnat jobb och ett underordnat jobb som kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="01e3d-154">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="01e3d-155">När du använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb på en eller flera datorer består jobbet av ett överordnat överordnat jobb och ett underordnat jobb för varje jobb körning på varje dator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-155">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="01e3d-156">När du använder `Invoke-Command` för att köra ett `Start-Job` kommando på en eller flera fjärrdatorer är resultatet detsamma som en lokal kommando körning på varje fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-156">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="01e3d-157">Kommandot returnerar ett jobb objekt för varje dator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-157">The command returns a job object for each computer.</span></span> <span data-ttu-id="01e3d-158">Jobbobjektet består av ett överordnat överordnat jobb och ett underordnat jobb som kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="01e3d-158">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="01e3d-159">Det överordnade jobbet representerar alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-159">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="01e3d-160">När du hanterar ett överordnat jobb hanterar du även de associerade underordnade jobben.</span><span class="sxs-lookup"><span data-stu-id="01e3d-160">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="01e3d-161">Om du till exempel stoppar ett överordnat jobb stoppas alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-161">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="01e3d-162">Om du får resultatet av ett överordnat jobb får du resultatet av alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-162">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="01e3d-163">Du kan dock även hantera underordnade jobb individuellt.</span><span class="sxs-lookup"><span data-stu-id="01e3d-163">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="01e3d-164">Detta är mest användbart när du vill undersöka ett problem med ett jobb eller hämta resultatet av ett antal underordnade jobb som har startats med hjälp av parametern **AsJob** i `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-164">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="01e3d-165">Följande kommando använder **AsJob** -parametern för `Invoke-Command` för att starta bakgrunds jobb på den lokala datorn och två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="01e3d-165">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="01e3d-166">Kommandot sparar jobbet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="01e3d-166">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="01e3d-167">När du visar egenskaperna för namn och **ChildJob** för jobbet i `$j` , visar det att kommandot returnerade ett jobb objekt med tre underordnade jobb, ett för varje dator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-167">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="01e3d-168">När du visar det överordnade jobbet visar det att jobbet misslyckades.</span><span class="sxs-lookup"><span data-stu-id="01e3d-168">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="01e3d-169">Men när du kör ett `Get-Job` kommando som hämtar underordnade jobb, visar utdata att det bara finns ett underordnat jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-169">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="01e3d-170">Om du vill hämta resultatet av alla underordnade jobb använder du `Receive-Job` cmdleten för att hämta resultatet från det överordnade jobbet.</span><span class="sxs-lookup"><span data-stu-id="01e3d-170">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="01e3d-171">Men du kan också hämta resultatet av ett visst underordnat jobb, som du ser i följande kommando.</span><span class="sxs-lookup"><span data-stu-id="01e3d-171">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="01e3d-172">Med de underordnade jobben i PowerShell bakgrunds jobb får du mer kontroll över de jobb som du kör.</span><span class="sxs-lookup"><span data-stu-id="01e3d-172">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="01e3d-173">Jobbtyper</span><span class="sxs-lookup"><span data-stu-id="01e3d-173">Job types</span></span>

<span data-ttu-id="01e3d-174">PowerShell stöder olika typer av jobb för olika aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="01e3d-174">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="01e3d-175">Från och med Windows PowerShell 3,0 kan utvecklare skriva "jobb käll kort" som lägger till nya jobb typer till PowerShell och inkluderar jobb käll korten i moduler.</span><span class="sxs-lookup"><span data-stu-id="01e3d-175">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="01e3d-176">När du importerar modulen kan du använda den nya jobb typen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-176">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="01e3d-177">PSScheduledJob-modulen lägger till exempel till schemalagda jobb och modulen PSWorkflow lägger till arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-177">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="01e3d-178">Anpassade jobb typer kan variera avsevärt från vanliga PowerShell-standardjobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-178">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="01e3d-179">Schemalagda jobb sparas till exempel på disk. de finns inte bara i en viss session.</span><span class="sxs-lookup"><span data-stu-id="01e3d-179">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="01e3d-180">Arbets flödes jobb kan pausas och återupptas.</span><span class="sxs-lookup"><span data-stu-id="01e3d-180">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="01e3d-181">De cmdletar som du använder för att hantera anpassade jobb beror på jobb typen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-181">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="01e3d-182">För vissa, använder du standard jobb-cmdlet: ar, till exempel `Get-Job` och `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-182">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="01e3d-183">Andra har särskilda cmdletar som endast hanterar en viss typ av jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-183">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="01e3d-184">Detaljerad information om anpassade jobb typer finns i hjälp avsnitten om jobb typen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-184">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="01e3d-185">Använd cmdleten för att hitta jobb typen för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-185">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="01e3d-186">`Get-Job` returnerar olika jobb objekt för olika typer av jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-186">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="01e3d-187">Värdet för egenskapen **PSJobTypeName** för de jobb objekt som `Get-Job` returnerar anger jobb typen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-187">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="01e3d-188">I följande tabell visas de jobb typer som ingår i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="01e3d-188">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="01e3d-189">Jobbtyp</span><span class="sxs-lookup"><span data-stu-id="01e3d-189">Job Type</span></span>    |                       <span data-ttu-id="01e3d-190">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="01e3d-190">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="01e3d-191">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-191">BackgroundJob</span></span>  | <span data-ttu-id="01e3d-192">Startade med `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01e3d-192">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="01e3d-193">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-193">RemoteJob</span></span>      | <span data-ttu-id="01e3d-194">Startade med **AsJob** -parametern för</span><span class="sxs-lookup"><span data-stu-id="01e3d-194">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="01e3d-195">`Invoke-Command` kommandon.</span><span class="sxs-lookup"><span data-stu-id="01e3d-195">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="01e3d-196">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-196">PSWorkflowJob</span></span>  | <span data-ttu-id="01e3d-197">Startade med **AsJob** -parametern för ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="01e3d-197">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="01e3d-198">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-198">PSScheduledJob</span></span> | <span data-ttu-id="01e3d-199">En instans av ett schemalagt jobb startades av en jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="01e3d-199">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="01e3d-200">CIMJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-200">CIMJob</span></span>         | <span data-ttu-id="01e3d-201">Startade med **AsJob** -parametern för en cmdlet från en</span><span class="sxs-lookup"><span data-stu-id="01e3d-201">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="01e3d-202">CDXLM-modul.</span><span class="sxs-lookup"><span data-stu-id="01e3d-202">CDXML module.</span></span>                                            |
| <span data-ttu-id="01e3d-203">WMIJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-203">WMIJob</span></span>         | <span data-ttu-id="01e3d-204">Startade med **AsJob** -parametern för en cmdlet från en</span><span class="sxs-lookup"><span data-stu-id="01e3d-204">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="01e3d-205">WMI-modul.</span><span class="sxs-lookup"><span data-stu-id="01e3d-205">WMI module.</span></span>                                              |
| <span data-ttu-id="01e3d-206">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="01e3d-206">PSEventJob</span></span>     | <span data-ttu-id="01e3d-207">Skapad med `Register-ObjectEvent` och ange en</span><span class="sxs-lookup"><span data-stu-id="01e3d-207">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="01e3d-208">åtgärd med **Åtgärds** parametern.</span><span class="sxs-lookup"><span data-stu-id="01e3d-208">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="01e3d-209">Obs: innan du använder `Get-Job` cmdleten för att hämta jobb av en viss typ, kontrollerar du att modulen som lägger till jobb typen importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-209">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="01e3d-210">Annars `Get-Job` kommer inte jobb av den typen.</span><span class="sxs-lookup"><span data-stu-id="01e3d-210">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="01e3d-211">Exempel</span><span class="sxs-lookup"><span data-stu-id="01e3d-211">Examples</span></span>

<span data-ttu-id="01e3d-212">Följande kommandon skapar ett lokalt bakgrunds jobb, ett fjärran slutet bakgrunds jobb, ett arbets flödes jobb och ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-212">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="01e3d-213">Sedan använder den `Get-Job` cmdleten för att hämta jobben.</span><span class="sxs-lookup"><span data-stu-id="01e3d-213">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="01e3d-214">`Get-Job` får inte det schemalagda jobbet, men alla startade instanser av det schemalagda jobbet hämtas.</span><span class="sxs-lookup"><span data-stu-id="01e3d-214">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="01e3d-215">Starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="01e3d-215">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="01e3d-216">Starta ett bakgrunds jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="01e3d-216">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="01e3d-217">Skapa ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-217">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="01e3d-218">Skapa ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="01e3d-218">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="01e3d-219">Kör arbets flödet som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="01e3d-219">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="01e3d-220">Hämta jobben.</span><span class="sxs-lookup"><span data-stu-id="01e3d-220">Get the jobs.</span></span> <span data-ttu-id="01e3d-221">`Get-Job`Kommandot kan inte utföra schemalagda jobb, men det hämtar instanser av det schemalagda jobbet som har startats.</span><span class="sxs-lookup"><span data-stu-id="01e3d-221">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="01e3d-222">Använd cmdleten för att hämta schemalagda jobb `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="01e3d-222">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="01e3d-223">Se även</span><span class="sxs-lookup"><span data-stu-id="01e3d-223">See also</span></span>

- [<span data-ttu-id="01e3d-224">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="01e3d-224">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="01e3d-225">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="01e3d-225">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="01e3d-226">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="01e3d-226">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="01e3d-227">about_Remote</span><span class="sxs-lookup"><span data-stu-id="01e3d-227">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="01e3d-228">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="01e3d-228">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="01e3d-229">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-229">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="01e3d-230">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-230">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="01e3d-231">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="01e3d-231">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="01e3d-232">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-232">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="01e3d-233">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="01e3d-233">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="01e3d-234">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="01e3d-234">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="01e3d-235">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="01e3d-235">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="01e3d-236">Avsluta-PSSession</span><span class="sxs-lookup"><span data-stu-id="01e3d-236">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
