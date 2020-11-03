---
description: Beskriver de avancerade ämnena för schemalagda jobb, inklusive fil strukturen som är beroende av de schemalagda jobben.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_advanced?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Advanced
ms.openlocfilehash: 7b09a72e8ad7e68641c73d2f7e59065dbf8f889b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270975"
---
# <a name="about-scheduled-jobs-advanced"></a><span data-ttu-id="2cfff-104">Om schemalagda uppgifter avancerade</span><span class="sxs-lookup"><span data-stu-id="2cfff-104">About Scheduled Jobs Advanced</span></span>

## <a name="short-description"></a><span data-ttu-id="2cfff-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cfff-105">Short description</span></span>

<span data-ttu-id="2cfff-106">Beskriver de avancerade ämnena för schemalagda jobb, inklusive fil strukturen som är beroende av de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2cfff-106">Explains advanced scheduled job topics, including the file structure that underlies scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="2cfff-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="2cfff-107">Long description</span></span>

<span data-ttu-id="2cfff-108">Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="2cfff-108">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="scheduled-job-directories-and-files"></a><span data-ttu-id="2cfff-109">Schemalagda jobb kataloger och filer</span><span class="sxs-lookup"><span data-stu-id="2cfff-109">Scheduled job directories and files</span></span>

<span data-ttu-id="2cfff-110">Schemalagda PowerShell-jobb är både PowerShell-jobb och Task Scheduler-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="2cfff-110">PowerShell scheduled jobs are both PowerShell jobs and Task Scheduler tasks.</span></span>
<span data-ttu-id="2cfff-111">Varje schemalagt jobb registreras i Schemaläggaren och sparas på disken i Microsoft .NET Framework serialisera XML-format.</span><span class="sxs-lookup"><span data-stu-id="2cfff-111">Each scheduled job is registered in Task Scheduler and saved on disk in Microsoft .NET Framework Serialization XML format.</span></span>

<span data-ttu-id="2cfff-112">När du skapar ett schemalagt jobb skapar PowerShell en katalog för det schemalagda jobbet i `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` katalogen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2cfff-112">When you create a scheduled job, PowerShell creates a directory for the scheduled job in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span> <span data-ttu-id="2cfff-113">Katalog namnet är detsamma som jobb namnet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-113">The directory name is the same as the job name.</span></span>

<span data-ttu-id="2cfff-114">Följande är ett exempel på en **ScheduledJobs** -katalog.</span><span class="sxs-lookup"><span data-stu-id="2cfff-114">The following is a sample **ScheduledJobs** directory.</span></span>

```powershell
Get-ChildItem $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs
```

```Output
Directory: C:\Users\User01\AppData\Local
               \Microsoft\Windows\PowerShell\ScheduledJobs

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         9/29/2011  10:03 AM            ArchiveProjects
d----         9/30/2011   1:18 PM            Inventory
d----        10/20/2011   9:15 AM            Backup-Scripts
d----         11/7/2011  10:40 AM            ProcessJob
d----         11/2/2011  10:25 AM            SecureJob
d----         9/27/2011   1:29 PM            Test-HelpFiles
d----         9/26/2011   4:22 PM            DeployPackage
```

<span data-ttu-id="2cfff-115">Varje schemalagt jobb har sin egen katalog.</span><span class="sxs-lookup"><span data-stu-id="2cfff-115">Each scheduled job has its own directory.</span></span> <span data-ttu-id="2cfff-116">Katalogen innehåller den schemalagda XML-filen och en under katalog för **utdata** .</span><span class="sxs-lookup"><span data-stu-id="2cfff-116">The directory contains the scheduled job XML file and an **Output** subdirectory.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell"
$Path += "\ScheduledJobs\ProcessJob"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/1/2011   3:00 PM            Output
-a---         11/1/2011   3:43 PM       7281 ScheduledJobDefinition.xml
```

<span data-ttu-id="2cfff-117">Den **resulterande** katalogen för ett schemalagt jobb innehåller dess körnings historik.</span><span class="sxs-lookup"><span data-stu-id="2cfff-117">The **Output** directory for a scheduled job contains its execution history.</span></span>
<span data-ttu-id="2cfff-118">Varje gång en jobb utlöses startar ett schemalagt jobb skapar PowerShell en tidsstämpel-namngiven katalog i utdatakatalogen.</span><span class="sxs-lookup"><span data-stu-id="2cfff-118">Each time a job trigger starts a scheduled job, PowerShell creates a timestamp-named directory in the output directory.</span></span> <span data-ttu-id="2cfff-119">Katalogen timestamp innehåller resultatet av jobbet i en **Results.xml** -fil och jobb status i en **Status.xml** -fil.</span><span class="sxs-lookup"><span data-stu-id="2cfff-119">The timestamp directory contains the results of the job in a **Results.xml** file and the job status in a **Status.xml** file.</span></span>

<span data-ttu-id="2cfff-120">Följande kommando visar katalogerna för körnings historik för det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-120">The following command shows the execution history directories for the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = "$home\AppData\Local\Microsoft"
$Path += "\Windows\PowerShell\ScheduledJobs\ProcessJob\Output"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft
               \Windows\PowerShell\ScheduledJobs\ProcessJob\Output

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         11/2/2011   3:00 AM            20111102-030002-260
d----         11/3/2011   3:00 AM            20111103-030002-277
d----         11/4/2011   3:00 AM            20111104-030002-209
d----         11/5/2011   3:00 AM            20111105-030002-251
d----         11/6/2011   3:00 AM            20111106-030002-174
d----         11/7/2011  12:00 AM            20111107-000001-914
d----         11/7/2011   3:00 AM            20111107-030002-376
```

```powershell
$Path = "$home\AppData\Local\Microsoft\Windows\PowerShell\"
$Path += "ScheduledJobs\ProcessJob\Output\20111102-030002-260"
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output\20111102-030002-260

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         11/2/2011   3:00 AM     581106 Results.xml
-a---         11/2/2011   3:00 AM       9451 Status.xml
```

<span data-ttu-id="2cfff-121">Du kan öppna och granska **ScheduledJobDefinition.xml** , **Results.xml** och **Status.xml** filer eller använda `Select-XML` cmdleten för att parsa filerna.</span><span class="sxs-lookup"><span data-stu-id="2cfff-121">You can open and examine the **ScheduledJobDefinition.xml** , **Results.xml** and **Status.xml** files or use the `Select-XML` cmdlet to parse the files.</span></span>

> [!WARNING]
> <span data-ttu-id="2cfff-122">Redigera inte XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="2cfff-122">Do not edit the XML files.</span></span> <span data-ttu-id="2cfff-123">Om en XML-fil innehåller ogiltig XML, tar PowerShell bort det schemalagda jobbet och dess körnings historik, inklusive jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="2cfff-123">If any XML file contains invalid XML, PowerShell deletes the scheduled job and its execution history, including job results.</span></span>

## <a name="start-a-scheduled-job-immediately"></a><span data-ttu-id="2cfff-124">Starta ett schemalagt jobb omedelbart</span><span class="sxs-lookup"><span data-stu-id="2cfff-124">Start a scheduled job immediately</span></span>

<span data-ttu-id="2cfff-125">Du kan starta ett schemalagt jobb direkt på något av två sätt:</span><span class="sxs-lookup"><span data-stu-id="2cfff-125">You can start a scheduled job immediately in one of two ways:</span></span>

- <span data-ttu-id="2cfff-126">Kör `Start-Job` cmdleten för att starta ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="2cfff-126">Run the `Start-Job` cmdlet to start any scheduled job.</span></span>
- <span data-ttu-id="2cfff-127">Lägg till parametern **RunNow** i `Register-ScheduledJob` kommandot för att starta jobbet så snart kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="2cfff-127">Add the **RunNow** parameter to your `Register-ScheduledJob` command to start the job as soon as the command is run.</span></span>

<span data-ttu-id="2cfff-128">Jobb som har startats med hjälp av `Start-Job` cmdleten är vanliga PowerShell-bakgrunds jobb, inte instanser av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-128">Jobs that are started by using the `Start-Job` cmdlet are standard PowerShell background jobs, not instances of the scheduled job.</span></span> <span data-ttu-id="2cfff-129">Precis som alla bakgrunds jobb startar de här jobben omedelbart, de omfattas inte av jobb alternativ eller påverkas av jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="2cfff-129">Like all background jobs, these jobs start immediately, they aren't subject to job options or affected by job triggers.</span></span> <span data-ttu-id="2cfff-130">Jobbets utdata sparas inte i katalogen **utdata** i katalogen för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2cfff-130">The job output isn't saved in the **Output** directory of the scheduled job directory.</span></span>

<span data-ttu-id="2cfff-131">Följande kommando använder **DefinitionName** -parametern för `Start-Job` cmdleten för att starta det schemalagda ProcessJob-jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-131">The following command uses the **DefinitionName** parameter of the `Start-Job` cmdlet to start the ProcessJob scheduled job.</span></span>

```powershell
Start-Job -DefinitionName ProcessJob
```

<span data-ttu-id="2cfff-132">Använd jobb-cmdletar för att hantera jobbet och hämta jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-132">To manage the job and get the job results, use the job cmdlets.</span></span> <span data-ttu-id="2cfff-133">Mer information om jobb-cmdlets finns i [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="2cfff-133">For more information about the job cmdlets, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2cfff-134">Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen.</span><span class="sxs-lookup"><span data-stu-id="2cfff-134">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="2cfff-135">Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="2cfff-135">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

## <a name="rename-a-scheduled-job"></a><span data-ttu-id="2cfff-136">Byta namn på ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="2cfff-136">Rename a scheduled job</span></span>

<span data-ttu-id="2cfff-137">Om du vill byta namn på ett schemalagt jobb använder du parametern name i `Set-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2cfff-137">To rename a scheduled job, use the Name parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="2cfff-138">När du byter namn på ett schemalagt jobb ändrar PowerShell namnet på det schemalagda jobbet och den schemalagda jobb katalogen.</span><span class="sxs-lookup"><span data-stu-id="2cfff-138">When you rename a scheduled job, PowerShell changes the name of the scheduled job and the scheduled job directory.</span></span> <span data-ttu-id="2cfff-139">Den ändrar dock inte namnen på instanser av det schemalagda jobbet som redan har körts.</span><span class="sxs-lookup"><span data-stu-id="2cfff-139">However, it doesn't change the names of instances of the scheduled job that have already run.</span></span>

## <a name="get-start-and-end-times"></a><span data-ttu-id="2cfff-140">Hämta start-och slut tider</span><span class="sxs-lookup"><span data-stu-id="2cfff-140">Get start and end times</span></span>

<span data-ttu-id="2cfff-141">Använd egenskaperna **PSBeginTime** och **PSEndTime** för ScheduledJob-objektet som returnerar schemalagda jobb för att hämta datum och tider då jobb instanser startade och slutar `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="2cfff-141">To get the dates and times that job instances started and ended, use the **PSBeginTime** and **PSEndTime** properties of the ScheduledJob object that `Get-Job` returns for scheduled jobs.</span></span>

<span data-ttu-id="2cfff-142">I följande exempel används **egenskaps** parametern för `Format-Table` cmdleten för att visa egenskaperna **PSBeginTime** och **PSEndTime** för varje jobb instans i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2cfff-142">The following example uses the **Property** parameter of the `Format-Table` cmdlet to display the **PSBeginTime** and **PSEndTime** properties of each job instance in a table.</span></span> <span data-ttu-id="2cfff-143">En beräknad egenskap med namnet **etikett** visar den förflutna tiden för varje jobb instans.</span><span class="sxs-lookup"><span data-stu-id="2cfff-143">A calculated property named **Label** displays the elapsed time of each job instance.</span></span>

```powershell
Get-job -Name UpdateHelpJob | 
  Format-Table -Property ID, PSBeginTime, PSEndTime,
@{Label="Elapsed Time";Expression={$.PsEndTime - $.PSBeginTime}}
```

```Output
Id   PSBeginTime             PSEndTime                Elapsed Time
--   -----------             ---------                ------------
 2   11/3/2011 3:00:01 AM    11/3/2011 3:00:39 AM     00:00:38.0053854
 3   11/4/2011 3:00:02 AM    11/4/2011 3:01:01 AM     00:00:59.1188475
 4   11/5/2011 3:00:02 AM    11/5/2011 3:00:50 AM     00:00:48.3692034
 5   11/6/2011 3:00:01 AM    11/6/2011 3:00:54 AM     00:00:52.8013036
 6   11/7/2011 3:00:01 AM    11/7/2011 3:00:38 AM     00:00:37.1930350
 7   11/8/2011 3:00:01 AM    11/8/2011 3:00:57 AM     00:00:56.2570556
 8   11/9/2011 3:00:03 AM    11/9/2011 3:00:55 AM     00:00:51.8142222
 9   11/10/2011 3:00:02 AM   11/10/2011 3:00:42 AM    00:00:40.7195954
```

## <a name="manage-execution-history"></a><span data-ttu-id="2cfff-144">Hantera körnings historik</span><span class="sxs-lookup"><span data-stu-id="2cfff-144">Manage execution history</span></span>

<span data-ttu-id="2cfff-145">Du kan bestämma antalet jobb instans resultat som sparas för varje schemalagt jobb och ta bort körnings historiken och de sparade jobb resultaten för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2cfff-145">You can determine the number of job instance results that are saved for each scheduled job and delete the execution history and saved job results of any scheduled job.</span></span>

<span data-ttu-id="2cfff-146">**ExecutionHistoryLength** -egenskapen för ett schemalagt jobb fastställer hur många jobb instans resultat som sparas för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-146">The **ExecutionHistoryLength** property of a scheduled job determines how many job instance results are saved for the scheduled job.</span></span> <span data-ttu-id="2cfff-147">När antalet sparade resultat överskrider värdet för egenskapen **ExecutionHistoryLength** , tar PowerShell bort resultatet från den äldsta instansen för att göra plats för resultatet av den senaste instansen.</span><span class="sxs-lookup"><span data-stu-id="2cfff-147">When the number of saved results exceeds the value of the **ExecutionHistoryLength** property, PowerShell deletes the results of the oldest instance to make room for the results of the newest instance.</span></span>

<span data-ttu-id="2cfff-148">Som standard sparar PowerShell körnings historiken och resultaten av 32 instanser av varje schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="2cfff-148">By default, PowerShell saves the execution history and results of 32 instances of each scheduled job.</span></span> <span data-ttu-id="2cfff-149">Om du vill ändra värdet använder du **MaxResultCount** -parametrarna för `Register-ScheduledJob` `Set-ScheduledJob` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="2cfff-149">To change that value, use the **MaxResultCount** parameters of the `Register-ScheduledJob` or `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="2cfff-150">Om du vill ta bort körnings historiken och alla resultat för ett schemalagt jobb använder du parametern **ClearExecutionHistory** för `Set-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2cfff-150">To delete the execution history and all results for a scheduled job, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="2cfff-151">Om du tar bort den här körnings historiken hindras inte PowerShell från att spara resultaten av nya instanser av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-151">Deleting this execution history does not prevent PowerShell from saving the results of new instances of the scheduled job.</span></span>

<span data-ttu-id="2cfff-152">I följande exempel används ihopbuntning för att skapa `$JobParms` som är parameter värden som skickas till `Register-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2cfff-152">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="2cfff-153">Mer information finns i [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="2cfff-153">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="2cfff-154">`Register-ScheduledJob`Använder `@JobParms` för att skapa ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="2cfff-154">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="2cfff-155">Kommandot använder parametern **MaxResultCount** med värdet 12 för att endast spara de 12 nyaste jobb instans resultaten för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-155">The command uses the **MaxResultCount** parameter with a value of 12 to save only the 12 newest job instance results of the scheduled job.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  MaxResultCount = "12"
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="2cfff-156">Följande kommando använder **MaxResultCount** -parametern för `Set-ScheduledJob` cmdleten för att öka antalet sparade instans resultat till</span><span class="sxs-lookup"><span data-stu-id="2cfff-156">The following command uses the **MaxResultCount** parameter of the `Set-ScheduledJob` cmdlet to increase the number of saved instance results to</span></span>
15.

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 15
```

<span data-ttu-id="2cfff-157">Följande kommando tar bort körnings historiken och de aktuella sparade resultaten för det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="2cfff-157">The following command deletes the execution history and the current saved results of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="2cfff-158">Följande kommando hämtar värdena för namn-och **ExecutionHistoryLength** -egenskaperna för alla schemalagda jobb på datorn och visar dem i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2cfff-158">The following command gets the values of the name and **ExecutionHistoryLength** properties of all scheduled jobs on the computer and displays them in a table.</span></span>

```powershell
Get-ScheduledJob | 
  Format-Table -Property Name, ExecutionHistoryLength -AutoSize
```

## <a name="see-also"></a><span data-ttu-id="2cfff-159">Se även</span><span class="sxs-lookup"><span data-stu-id="2cfff-159">See also</span></span>

[<span data-ttu-id="2cfff-160">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="2cfff-160">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="2cfff-161">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="2cfff-161">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="2cfff-162">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="2cfff-162">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="2cfff-163">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="2cfff-163">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="2cfff-164">Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul</span><span class="sxs-lookup"><span data-stu-id="2cfff-164">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="2cfff-165">Schemaläggaren</span><span class="sxs-lookup"><span data-stu-id="2cfff-165">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
