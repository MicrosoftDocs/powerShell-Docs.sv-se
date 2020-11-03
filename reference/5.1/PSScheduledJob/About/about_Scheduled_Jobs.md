---
description: Beskriver schemalagda jobb och förklarar hur du använder och hanterar schemalagda jobb i PowerShell och i Schemaläggaren.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs
ms.openlocfilehash: 4d4e86957a584bb4deb47cadcd8588c1236455ac
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270980"
---
# <a name="about-scheduled-jobs"></a><span data-ttu-id="9df5f-104">Om schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="9df5f-104">About Scheduled Jobs</span></span>

## <a name="short-description"></a><span data-ttu-id="9df5f-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="9df5f-105">Short description</span></span>

<span data-ttu-id="9df5f-106">Beskriver schemalagda jobb och förklarar hur du använder och hanterar schemalagda jobb i PowerShell och i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="9df5f-106">Describes scheduled jobs and explains how to use and manage scheduled jobs in PowerShell and in Task Scheduler.</span></span>

## <a name="long-description"></a><span data-ttu-id="9df5f-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="9df5f-107">Long description</span></span>

<span data-ttu-id="9df5f-108">Schemalagda PowerShell-jobb är en användbar hybrid av PowerShell-arbetsjobb och Schemaläggaren-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="9df5f-108">PowerShell scheduled jobs are a useful hybrid of PowerShell background jobs and Task Scheduler tasks.</span></span>

<span data-ttu-id="9df5f-109">Som till exempel PowerShell-bakgrunds jobb körs schemalagda jobb asynkront i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="9df5f-109">Like PowerShell background jobs, scheduled jobs run asynchronously in the background.</span></span> <span data-ttu-id="9df5f-110">Instanser av schemalagda jobb som har körningar kan hanteras med hjälp av jobb-cmdletarna, till exempel,, `Start-Job` `Get-Job` `Stop-Job` och `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="9df5f-110">Instances of scheduled jobs that have run can be managed by using the job cmdlets, such as `Start-Job`, `Get-Job`, `Stop-Job`, and `Receive-Job`.</span></span>

<span data-ttu-id="9df5f-111">Som aktiviteter i Schemaläggaren sparas schemalagda jobb till disk.</span><span class="sxs-lookup"><span data-stu-id="9df5f-111">Like Task Scheduler tasks, scheduled jobs are saved to disk.</span></span> <span data-ttu-id="9df5f-112">Du kan visa och hantera jobben i Schemaläggaren, aktivera och inaktivera dem efter behov, köra dem eller använda dem som mallar, upprätta ett engångs-eller återkommande schema för att starta jobben eller ange under vilka omständigheter jobben ska starta.</span><span class="sxs-lookup"><span data-stu-id="9df5f-112">You can view and manage the jobs in Task Scheduler, enable and disable them as needed, run them or use them as templates, establish a one-time or recurring schedules for starting the jobs, or set conditions under which the jobs start.</span></span>

<span data-ttu-id="9df5f-113">Dessutom sparas resultatet av schemalagda jobb instanser till disk i ett enkelt och lättillgängligt format, vilket ger en pågående logg över jobbets utdata.</span><span class="sxs-lookup"><span data-stu-id="9df5f-113">In addition, the results of scheduled job instances are saved to disk in an easily accessible format, providing a running log of job output.</span></span> <span data-ttu-id="9df5f-114">Schemalagda jobb levereras med en anpassad uppsättning cmdlets för att hantera dem.</span><span class="sxs-lookup"><span data-stu-id="9df5f-114">Scheduled jobs come with a customized set of cmdlets for managing them.</span></span> <span data-ttu-id="9df5f-115">Med cmdletarna kan du skapa, redigera, hantera, inaktivera och återaktivera schemalagda jobb, jobb utlösare och jobb alternativ.</span><span class="sxs-lookup"><span data-stu-id="9df5f-115">The cmdlets let you create, edit, manage, disable, and re-enable scheduled jobs, job triggers and job options.</span></span>

<span data-ttu-id="9df5f-116">Den här omfattande och flexibla uppsättningen verktyg gör schemalagda jobb till en viktig komponent i många IT-lösningar för Professional PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9df5f-116">This comprehensive and flexible set of tools make scheduled jobs an essential component of many professional PowerShell IT solutions.</span></span>

<span data-ttu-id="9df5f-117">De schemalagda jobb-cmdletarna ingår i **PSScheduledJob** -modulen som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9df5f-117">The scheduled job cmdlets are included in the **PSScheduledJob** module that is installed with PowerShell.</span></span> <span data-ttu-id="9df5f-118">Den här modulen introducerades i PowerShell 3,0 och fungerar i PowerShell 3,0 och senare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9df5f-118">This module was introduced in PowerShell 3.0 and works in PowerShell 3.0 and later versions of PowerShell.</span></span> <span data-ttu-id="9df5f-119">Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="9df5f-119">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

<span data-ttu-id="9df5f-120">Mer information om PowerShell-bakgrunds jobb finns [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="9df5f-120">For more information about PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

<span data-ttu-id="9df5f-121">Mer information [om Schemaläggaren finns i](/windows/desktop/TaskSchd/task-scheduler-reference)Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="9df5f-121">For more information about Task Scheduler, see [Task Scheduler](/windows/desktop/TaskSchd/task-scheduler-reference).</span></span>

> [!NOTE]
> <span data-ttu-id="9df5f-122">Du kan visa och hantera schemalagda PowerShell-jobb i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="9df5f-122">You can view and manage PowerShell scheduled jobs in Task Scheduler.</span></span> <span data-ttu-id="9df5f-123">PowerShell-jobben och de schemalagda jobb-cmdletarna fungerar bara för schemalagda jobb som skapas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9df5f-123">The PowerShell jobs and scheduled job cmdlets work only on scheduled jobs that are created in PowerShell.</span></span>

## <a name="quick-start"></a><span data-ttu-id="9df5f-124">Snabbstart</span><span class="sxs-lookup"><span data-stu-id="9df5f-124">Quick start</span></span>

<span data-ttu-id="9df5f-125">I det här exemplet skapas ett schemalagt jobb som börjar varje dag kl. 3:00 och kör `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9df5f-125">This example creates a scheduled job that starts every day at 3:00 AM and runs the `Get-Process` cmdlet.</span></span> <span data-ttu-id="9df5f-126">Jobbet startar även om datorn körs på batterier.</span><span class="sxs-lookup"><span data-stu-id="9df5f-126">The job starts even if the computer is running on batteries.</span></span>

```powershell
$trigger = New-JobTrigger -Daily -At 3AM
$options = New-ScheduledJobOption -StartIfOnBattery
Register-ScheduledJob -Name ProcessJob -ScriptBlock {Get-Process} `
-Trigger $trigger -ScheduledJobOption $options
```

<span data-ttu-id="9df5f-127">`Get-ScheduledJob`Cmdlet: en hämtar de schemalagda jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9df5f-127">The `Get-ScheduledJob` cmdlet gets the scheduled jobs on the local computer.</span></span>

```powershell
Get-ScheduledJob
```

```Output
Id         Name            Triggers        Command            Enabled
--         ----            --------        -------            -------
7          ProcessJob      {1}             Get-Process        True
```

<span data-ttu-id="9df5f-128">`Get-JobTrigger` hämtar jobb utlösare för **ProcessJob**.</span><span class="sxs-lookup"><span data-stu-id="9df5f-128">`Get-JobTrigger` gets the job triggers of **ProcessJob**.</span></span> <span data-ttu-id="9df5f-129">Indataparametrarna anger det schemalagda jobbet, inte utlösaren, eftersom utlösare sparas i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9df5f-129">The input parameters specify the scheduled job, not the trigger, because triggers are saved in a scheduled job.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id         Frequency       Time                   DaysOfWeek        Enabled
--         ---------       ----                   ----------        -------
1          Daily           11/5/2011 3:00:00 AM                     True
```

<span data-ttu-id="9df5f-130">I det här exemplet används parametern **ContinueIfGoingOnBattery** för `Set-ScheduledJob` cmdleten för att ändra egenskapen **StopIfGoingOnBatteries** för **ProcessJob** till **false**.</span><span class="sxs-lookup"><span data-stu-id="9df5f-130">This example uses the **ContinueIfGoingOnBattery** parameter of the `Set-ScheduledJob` cmdlet to change the **StopIfGoingOnBatteries** property of **ProcessJob** to **False**.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Set-ScheduledJobOption `
-ContinueIfGoingOnBattery -Passthru
```

```Output
StartIfOnBatteries     : True
StopIfGoingOnBatteries : False
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="9df5f-131">`Get-ScheduledJob`Cmdlet: en hämtar det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="9df5f-131">The `Get-ScheduledJob` cmdlet gets the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command        Enabled
--         ----            --------        -------        -------
7          ProcessJob      {1}             Get-Process    True
```

<span data-ttu-id="9df5f-132">`Get-Job`Cmdleten hämtar alla instanser av det schemalagda **ProcessJob** -jobbet som har körts hittills.</span><span class="sxs-lookup"><span data-stu-id="9df5f-132">The `Get-Job` cmdlet gets all instances of the **ProcessJob** scheduled job that have run thus far.</span></span> <span data-ttu-id="9df5f-133">`Get-Job`Cmdlet: en hämtar endast schemalagda jobb när **PSScheduledJob** -modulen importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-133">The `Get-Job` cmdlet gets scheduled jobs only when the **PSScheduledJob** module is imported into the current session.</span></span>

> [!TIP]
> <span data-ttu-id="9df5f-134">Observera att du använder de schemalagda jobb-cmdletarna för att hantera schemalagda jobb, men du använder jobb-cmdletar för att hantera instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9df5f-134">Notice that you use the scheduled job cmdlets to manage scheduled jobs, but you use the job cmdlets to manage instances of scheduled jobs.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="9df5f-135">`Receive-Job`Cmdlet: en hämtar resultatet från den senaste instansen av det schemalagda **ProcessJob** -jobbet (ID = 51).</span><span class="sxs-lookup"><span data-stu-id="9df5f-135">The `Receive-Job` cmdlet gets the results of the most recent instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Receive-Job -ID 51
```

<span data-ttu-id="9df5f-136">Även om `Receive-Job` kommandot inte inkluderade parametern **Behåll** , sparas resultatet av jobbet på disken tills du tar bort dem eller så har det maximala antalet resultat överskridits.</span><span class="sxs-lookup"><span data-stu-id="9df5f-136">Even though the `Receive-Job` command did not include the **Keep** parameter, the results of the job are saved on disk until you delete them or the maximum number of results are exceeded.</span></span>

<span data-ttu-id="9df5f-137">Jobb resultatet är inte längre tillgängligt i den här sessionen, men om du startar en ny session eller öppnar ett nytt PowerShell-fönster är resultatet av jobbet tillgängligt igen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-137">The job results are no longer available in this session, but if you start a new session or open a new PowerShell window, the results of the job are available again.</span></span>

<span data-ttu-id="9df5f-138">Följande kommando använder **DefinitionName** -parametern för `Start-Job` cmdleten för att starta det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="9df5f-138">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the **ProcessJob** scheduled job.</span></span>

<span data-ttu-id="9df5f-139">Jobb som har startats med hjälp av `Start-Job` cmdleten är vanliga PowerShell-bakgrunds jobb, inte instanser av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="9df5f-139">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="9df5f-140">Precis som alla bakgrunds jobb startar de här jobben omedelbart, de omfattas inte av jobb alternativ eller påverkas av jobb utlösare och deras utdata sparas inte i katalogen utdata i den schemalagda jobb katalogen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-140">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers, and their output is not saved in the output directory of the scheduled job directory.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="9df5f-141">`Unregister-ScheduledJob`Cmdleten tar bort det schemalagda **ProcessJob** -jobbet och alla sparade resultat från jobb instanserna.</span><span class="sxs-lookup"><span data-stu-id="9df5f-141">The `Unregister-ScheduledJob` cmdlet deletes the **ProcessJob** scheduled job and all saved results of its job instances.</span></span>

```powershell
Unregister-ScheduledJob ProcessJob
```

## <a name="scheduled-jobs-concepts"></a><span data-ttu-id="9df5f-142">Metoder för schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="9df5f-142">Scheduled jobs concepts</span></span>

<span data-ttu-id="9df5f-143">Ett schemalagt jobb kör kommandon eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="9df5f-143">A scheduled job runs commands or a script.</span></span> <span data-ttu-id="9df5f-144">Ett schemalagt jobb kan innehålla jobb utlösare som startar jobb-och jobb alternativen som anger villkor för körning av jobbet.</span><span class="sxs-lookup"><span data-stu-id="9df5f-144">A scheduled job can include job triggers that start the job and job options that set conditions for running the job.</span></span>

<span data-ttu-id="9df5f-145">En jobb utlösare startar ett schemalagt jobb automatiskt.</span><span class="sxs-lookup"><span data-stu-id="9df5f-145">A job trigger starts a scheduled job automatically.</span></span> <span data-ttu-id="9df5f-146">En jobb utlösare kan inkludera ett engångs schema eller ett återkommande schema eller ange en händelse, till exempel när en användare loggar in eller Windows startas.</span><span class="sxs-lookup"><span data-stu-id="9df5f-146">A job trigger can include a one-time or recurring schedule or specify an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="9df5f-147">Ett schemalagt jobb kan ha en eller flera jobb utlösare, och du kan skapa, lägga till, aktivera, inaktivera och hämta jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="9df5f-147">A scheduled job can have one or more job triggers, and you can create, add, enable, disable, and get job triggers.</span></span>

<span data-ttu-id="9df5f-148">Jobb utlösare är valfria.</span><span class="sxs-lookup"><span data-stu-id="9df5f-148">Job triggers are optional.</span></span> <span data-ttu-id="9df5f-149">Du kan starta schemalagda jobb direkt med hjälp av `Start-Job cmdlet` , eller genom att lägga till **RunNow** -parametern i `Register-ScheduledJob` kommandot.</span><span class="sxs-lookup"><span data-stu-id="9df5f-149">You can start scheduled jobs immediately by using the `Start-Job cmdlet`, or by adding the **RunNow** parameter to your `Register-ScheduledJob` command.</span></span>

<span data-ttu-id="9df5f-150">Jobb alternativ anger villkoren för att köra ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9df5f-150">Job options set the conditions for running a scheduled job.</span></span> <span data-ttu-id="9df5f-151">Varje schemalagt jobb har ett objekt för jobb alternativ.</span><span class="sxs-lookup"><span data-stu-id="9df5f-151">Every scheduled job has one job options object.</span></span> <span data-ttu-id="9df5f-152">Du kan skapa och redigera jobb alternativ objekt och lägga till dem i en eller flera schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9df5f-152">You can create and edit job options objects and add them to one or more scheduled jobs.</span></span>

<span data-ttu-id="9df5f-153">Varje gång ett schemalagt jobb startas skapas en jobb instans.</span><span class="sxs-lookup"><span data-stu-id="9df5f-153">Each time a scheduled job starts, a job instance is created.</span></span> <span data-ttu-id="9df5f-154">Använd cmdletar för PowerShell-jobb för att visa och hantera jobb instansen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-154">Use the PowerShell job cmdlets to view and manage the job instance.</span></span>

<span data-ttu-id="9df5f-155">Schemalagda jobb sparas till disk och använder cmdlet-verbet, `Register` i stället för `New` .</span><span class="sxs-lookup"><span data-stu-id="9df5f-155">Scheduled jobs are saved to disk and use the cmdlet verb, `Register`, instead of `New`.</span></span> <span data-ttu-id="9df5f-156">XML-filerna finns på den lokala datorn i katalogen `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="9df5f-156">The XML files are located on the local computer in the directory `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

<span data-ttu-id="9df5f-157">PowerShell skapar en katalog för varje schemalagt jobb och sparar jobb kommandona, jobb utlösare, jobb alternativ och jobb resultat i den schemalagda jobb katalogen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-157">PowerShell creates a directory for each scheduled job and saves the job commands, job triggers, job options and job results in the scheduled job directory.</span></span> <span data-ttu-id="9df5f-158">Jobb utlösare och jobb alternativ sparas inte på disken oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="9df5f-158">Job triggers and job options aren't saved to disk independently.</span></span>
<span data-ttu-id="9df5f-159">De sparas i XML-koden för schemalagda jobb för varje schemalagt jobb som de är associerade med.</span><span class="sxs-lookup"><span data-stu-id="9df5f-159">They are saved in the scheduled job XML of each scheduled job with which they are associated.</span></span>

<span data-ttu-id="9df5f-160">Schemalagda jobb, jobb utlösare och jobb alternativ visas i PowerShell som objekt.</span><span class="sxs-lookup"><span data-stu-id="9df5f-160">Scheduled jobs, job triggers, and job options appear in PowerShell as objects.</span></span>
<span data-ttu-id="9df5f-161">Objekten är sammanlänkade, vilket gör det enkelt att identifiera och använda i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="9df5f-161">The objects are interlinked, which makes them easy to discover and use in commands and scripts.</span></span>

<span data-ttu-id="9df5f-162">Schemalagda uppgifter visas som **ScheduledJobDefinition** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9df5f-162">Scheduled jobs appear as **ScheduledJobDefinition** objects.</span></span> <span data-ttu-id="9df5f-163">**ScheduledJobDefinition** -objektet har en **JobTriggers** -egenskap som innehåller jobb utlösare för det schemalagda jobbet och en **alternativ** egenskap som innehåller jobb alternativen.</span><span class="sxs-lookup"><span data-stu-id="9df5f-163">The **ScheduledJobDefinition** object has a **JobTriggers** property that contains the job triggers of the scheduled job and an **Options** property that contains the job options.</span></span> <span data-ttu-id="9df5f-164">**ScheduledJobTriggers** -och **ScheduledJobOptions** -objekten som representerar jobb utlösare och jobb alternativ, var och en har en **jobb definitionen** -egenskap som innehåller det schemalagda jobb som de är associerade med.</span><span class="sxs-lookup"><span data-stu-id="9df5f-164">The **ScheduledJobTriggers** and **ScheduledJobOptions** objects that represent job triggers and job options, respectively, each have a **JobDefinition** property that contains the scheduled job with which they are associated.</span></span> <span data-ttu-id="9df5f-165">Den här rekursiva sammanlänkningen gör det enkelt att hitta utlösare och alternativ för ett schemalagt jobb och att söka efter, skripta och visa det schemalagda jobbet som en jobb utlösare eller ett jobb alternativ är associerat med.</span><span class="sxs-lookup"><span data-stu-id="9df5f-165">This recursive interconnection makes it easy to find the triggers and options of a scheduled job and to find, script, and display the scheduled job to which any job trigger or job option is associated.</span></span>

## <a name="see-also"></a><span data-ttu-id="9df5f-166">Se även</span><span class="sxs-lookup"><span data-stu-id="9df5f-166">See also</span></span>

[<span data-ttu-id="9df5f-167">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="9df5f-167">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="9df5f-168">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="9df5f-168">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="9df5f-169">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="9df5f-169">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

<span data-ttu-id="9df5f-170">Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul</span><span class="sxs-lookup"><span data-stu-id="9df5f-170">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="9df5f-171">Schemaläggaren</span><span class="sxs-lookup"><span data-stu-id="9df5f-171">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
