---
description: Förklarar hur du löser problem med schemalagda jobb
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_troubleshooting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Troubleshooting
ms.openlocfilehash: aac2133cee4abdd7e50e7b433104b9578d74b0a8
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685858"
---
# <a name="about-scheduled-jobs-troubleshooting"></a><span data-ttu-id="b0b1d-104">Om fel sökning av schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="b0b1d-104">About Scheduled Jobs Troubleshooting</span></span>

## <a name="short-description"></a><span data-ttu-id="b0b1d-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0b1d-105">Short description</span></span>

<span data-ttu-id="b0b1d-106">Förklarar hur du löser problem med schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="b0b1d-106">Explains how to resolve problems with scheduled jobs</span></span>

## <a name="long-description"></a><span data-ttu-id="b0b1d-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0b1d-107">Long description</span></span>

<span data-ttu-id="b0b1d-108">I det här dokumentet beskrivs några av de problem som kan uppstå när du använder funktionerna för schemalagda jobb i PowerShell och det föreslår lösningar på dessa problem.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-108">This document describes some of the problems that you might experience when using the scheduled job features of PowerShell and it suggests solutions to these problems.</span></span>

<span data-ttu-id="b0b1d-109">Innan du använder schemalagda PowerShell-jobb kan du läsa mer i [about_Scheduled_Jobs](about_Scheduled_Jobs.md) och relaterade schemalagda uppgifter om ämnen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-109">Before using PowerShell scheduled jobs, see [about_Scheduled_Jobs](about_Scheduled_Jobs.md) and the related scheduled jobs about topics.</span></span>

<span data-ttu-id="b0b1d-110">Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="b0b1d-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="cant-find-job-results"></a><span data-ttu-id="b0b1d-111">Det går inte att hitta jobb resultaten</span><span class="sxs-lookup"><span data-stu-id="b0b1d-111">Can't find job results</span></span>

### <a name="basic-method-for-getting-job-results-in-powershell"></a><span data-ttu-id="b0b1d-112">Grundläggande metod för att hämta jobb resultat i PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0b1d-112">Basic method for getting job results in PowerShell</span></span>

<span data-ttu-id="b0b1d-113">När ett schemalagt jobb körs skapas en instans av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-113">When a scheduled job runs, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="b0b1d-114">Om du vill visa, hantera och hämta resultatet av schemalagda jobb instanser använder du jobb-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-114">To view, manage, and get the results of scheduled job instances, use the Job cmdlets.</span></span>

> [!NOTE]
> <span data-ttu-id="b0b1d-115">Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-115">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="b0b1d-116">Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-116">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="b0b1d-117">Om du vill hämta en lista över alla instanser av ett schemalagt jobb använder du `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-117">To get a list of all instances of a scheduled job, use the `Get-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State         HasMoreData     Location
--     ----         -------------   -----         -----------     --------
43     ProcessJob   PSScheduledJob  Completed     False           localhost
44     ProcessJob   PSScheduledJob  Completed     False           localhost
45     ProcessJob   PSScheduledJob  Completed     False           localhost
46     ProcessJob   PSScheduledJob  Completed     False           localhost
47     ProcessJob   PSScheduledJob  Completed     False           localhost
48     ProcessJob   PSScheduledJob  Completed     False           localhost
49     ProcessJob   PSScheduledJob  Completed     False           localhost
50     ProcessJob   PSScheduledJob  Completed     False           localhost
```

<span data-ttu-id="b0b1d-118">`Get-Job`Cmdleten skickar **ProcessJob** -objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-118">The `Get-Job` cmdlet sends **ProcessJob** objects down the pipeline.</span></span> <span data-ttu-id="b0b1d-119">`Format-Table`Cmdleten visar egenskaperna **Name**, **ID** och **PSBeginTime** för en schemalagd jobb instans i en tabell.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-119">The `Format-Table` cmdlet displays the **Name**, **ID**, and **PSBeginTime** properties of a scheduled job instance in a table.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, PSBeginTime -Auto
```

```Output
Name       Id PSBeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

<span data-ttu-id="b0b1d-120">Använd cmdleten för att hämta resultatet av en instans av ett schemalagt jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-120">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="b0b1d-121">Följande kommando hämtar resultatet från den senaste instansen av ProcessJob (ID = 50).</span><span class="sxs-lookup"><span data-stu-id="b0b1d-121">The following command gets the results of the newest instance of the ProcessJob (ID = 50).</span></span>

```powershell
Receive-Job -ID 50
```

### <a name="basic-method-for-finding-job-results-on-disk"></a><span data-ttu-id="b0b1d-122">Grundläggande metod för att hitta jobb resultat på disk</span><span class="sxs-lookup"><span data-stu-id="b0b1d-122">Basic method for finding job results on disk</span></span>

<span data-ttu-id="b0b1d-123">Om du vill hantera schemalagda jobb använder du jobb-cmdletarna, till exempel `Get-Job` och `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-123">To manage scheduled jobs, use the job cmdlets, such as `Get-Job` and `Receive-Job`.</span></span>

<span data-ttu-id="b0b1d-124">Om inte `Get-Job` hämtar jobb instansen eller `Receive-Job` inte hämtar jobb resultaten kan du söka igenom körnings historiken för jobbet på disk.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-124">If `Get-Job` does not get the job instance or `Receive-Job` does not get the job results, you can search the execution history files for the job on disk.</span></span>
<span data-ttu-id="b0b1d-125">Körnings historiken innehåller en post för alla Utlös ande jobb instanser.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-125">The execution history contains a record of all triggered job instances.</span></span>

<span data-ttu-id="b0b1d-126">Kontrol lera att det finns en tidsstämpel-namngiven katalog i katalogen för ett schemalagt jobb på följande sökväg:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-126">Verify that there is a timestamp-named directory in the directory for a scheduled job in the following path:</span></span>

`$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="b0b1d-127">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-127">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJob\<ScheduledJobName>\Output`

<span data-ttu-id="b0b1d-128">Till exempel `Get-ChildItem` hämtar cmdleten körnings historiken på disk för det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-128">For example, the `Get-ChildItem` cmdlet gets the on-disk execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\AppData\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output

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

<span data-ttu-id="b0b1d-129">Varje timestamp-namngiven katalog representerar en jobb instans.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-129">Each timestamp-named directory represents a job instance.</span></span> <span data-ttu-id="b0b1d-130">Resultaten för varje jobb instans sparas i en **Results.xml** -fil i katalogen timestamp-named.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-130">The results of each job instance are saved in a **Results.xml** file in the timestamp-named directory.</span></span>

<span data-ttu-id="b0b1d-131">Följande kommando hämtar till exempel **Results.xml** filer för varje Sparad instans av det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-131">For example, the following command gets the **Results.xml** files for every saved instance of the **ProcessJob** scheduled job.</span></span> <span data-ttu-id="b0b1d-132">Om **Results.xml** -filen saknas kan inte PowerShell returnera eller Visa jobb resultaten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-132">If the **Results.xml** file is missing, PowerShell cannot return or display the job results.</span></span>

```powershell
$Path = '$home\AppData\Local\Microsoft\Windows\PowerShell'
$Path += '\ScheduledJobs\ProcessJob\Output\*\Results.xml'
Get-ChildItem $Path
```

```Output
Directory: C:\Users\User01\Appdata\Local\Microsoft\Windows\PowerShell
               \ScheduledJobs\ProcessJob\Output
```

<span data-ttu-id="b0b1d-133">Jobb-cmdleten kanske inte kan hämta schemalagda jobb instanser eller deras resultat eftersom modulen **PSScheduledJob** inte har importer ATS till sessionen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-133">The job cmdlet might not be able to get scheduled job instances or their results because the **PSScheduledJob** module is not imported into the session.</span></span>

> [!NOTE]
> <span data-ttu-id="b0b1d-134">Innan du använder en jobb-cmdlet på schemalagda jobb instanser måste du kontrol lera att modulen **PSScheduledJob** ingår i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-134">Before using a job cmdlet on scheduled job instances, verify that the **PSScheduledJob** module is included in the session.</span></span> <span data-ttu-id="b0b1d-135">Utan modulen **PSScheduledJob** kan inte jobb-cmdlet: ar Hämta schemalagda jobb instanser eller deras resultat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-135">Without the **PSScheduledJob** module, the job cmdlets cannot get scheduled job instances or their results.</span></span>

<span data-ttu-id="b0b1d-136">Så här importerar du **PSScheduledJob** -modulen:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-136">To import the **PSScheduledJob** module:</span></span>

```powershell
Import-Module PSScheduledJob
```

### <a name="receive-job-cmdlet-might-already-have-returned-the-results"></a><span data-ttu-id="b0b1d-137">Receive-Job cmdlet kanske redan returnerade resultaten</span><span class="sxs-lookup"><span data-stu-id="b0b1d-137">Receive-Job cmdlet might already have returned the results</span></span>

<span data-ttu-id="b0b1d-138">Om `Receive-Job` resultat för jobb instans inte returneras kan det bero på att ett `Receive-Job` kommando har körts för jobb instansen i den aktuella sessionen utan parametern **Keep** .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-138">If `Receive-Job` does not return job instance results, it might be because a `Receive-Job` command has been run for that job instance in the current session without the **Keep** parameter.</span></span>

<span data-ttu-id="b0b1d-139">Om du använder `Receive-Job` utan parametern **Keep** `Receive-Job` returnerar jobb resultatet och anger **HasMoreData** -egenskapen för jobb instansen till **false**.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-139">When you use `Receive-Job` without the **Keep** parameter, `Receive-Job` returns the job results and sets the job instance's **HasMoreData** property to **False**.</span></span> <span data-ttu-id="b0b1d-140">Värdet **false** innebär att resultatet `Receive-Job` returnerade jobbets resultat och att instansen inte har fler resultat att returnera.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-140">The **False** value means that `Receive-Job` returned the job's results and the instance has no more results to return.</span></span> <span data-ttu-id="b0b1d-141">Den här inställningen är lämplig för vanliga bakgrunds jobb, men inte för instanser av schemalagda jobb som sparas på disk.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-141">This setting is appropriate for standard background jobs, but not for instances of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="b0b1d-142">Starta en ny PowerShell-session genom att skriva för att hämta jobb instans resultatet igen `PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-142">To get the job instance results again, start a new PowerShell session by typing `PowerShell`.</span></span> <span data-ttu-id="b0b1d-143">Importera modulen **PSScheduledJob** och försök att utföra `Receive-Job` kommandot igen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-143">Import the **PSScheduledJob** module, and try the `Receive-Job` command again.</span></span>

```powershell
Receive-Job -ID 50
```

```Output
#No results
```

```powershell
PowerShell.exe
```

```Output
Windows PowerShell
Copyright (C) 2012 Microsoft Corporation. All rights reserved.
```

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="using-keep-parameter-to-get-results-more-than-one-time-in-a-session"></a><span data-ttu-id="b0b1d-144">Använda parametern Keep för att få resultat mer än en gång i en session</span><span class="sxs-lookup"><span data-stu-id="b0b1d-144">Using Keep parameter to get results more than one time in a session</span></span>

<span data-ttu-id="b0b1d-145">Om du vill få resultatet av en jobb instans mer än en gång i en session använder du parametern **Keep** för `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-145">To get the result of a job instance more than one time in a session, use the **Keep** parameter of the `Receive-Job` cmdlet.</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

```powershell
Receive-Job -ID 50 -Keep
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id  ProcessName
-------  ------    -----      ----- -----   ------     --  -----------
1213         33    12348      21676    88    25.71   1608  CcmExec
29            4     1168       2920    43     0.02    748  conhost
46            6     2208       4612    45     0.03   1640  conhost
```

### <a name="the-scheduled-job-might-be-corrupted"></a><span data-ttu-id="b0b1d-146">Det schemalagda jobbet kan vara skadat</span><span class="sxs-lookup"><span data-stu-id="b0b1d-146">The scheduled job might be corrupted</span></span>

<span data-ttu-id="b0b1d-147">Om ett schemalagt jobb skadas tar PowerShell bort det skadade schemalagda jobbet och dess resultat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-147">If a scheduled job becomes corrupted, PowerShell deletes the corrupted scheduled job and its results.</span></span> <span data-ttu-id="b0b1d-148">Det går inte att återställa resultatet av ett skadat schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-148">You cannot recover the results of a corrupted scheduled job.</span></span>

<span data-ttu-id="b0b1d-149">Använd cmdleten för att avgöra om ett schemalagt jobb fortfarande finns `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="b0b1d-149">To determine if a scheduled job still exists, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
Get-ScheduledJob
```

### <a name="the-number-of-results-might-have-exceeded-the-executionhistorylength"></a><span data-ttu-id="b0b1d-150">Antalet resultat kan ha överskridit ExecutionHistoryLength</span><span class="sxs-lookup"><span data-stu-id="b0b1d-150">The number of results might have exceeded the ExecutionHistoryLength</span></span>

<span data-ttu-id="b0b1d-151">**ExecutionHistoryLength** -egenskapen för ett schemalagt jobb fastställer hur många jobb instanser och deras resultat som sparas på disk.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-151">The **ExecutionHistoryLength** property of a scheduled job determines how many job instances, and their results, are saved to disk.</span></span> <span data-ttu-id="b0b1d-152">Standardvärdet är 32.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-152">The default value is 32.</span></span>
<span data-ttu-id="b0b1d-153">När antalet instanser av ett schemalagt jobb överstiger detta värde, tar PowerShell bort den äldsta jobb instansen för att göra plats för varje ny jobb instans.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-153">When the number of instances of a scheduled job exceeds this value, PowerShell deletes the oldest job instance to make room for each new job instance.</span></span>

<span data-ttu-id="b0b1d-154">Om du vill hämta värdet för egenskapen **ExecutionHistoryLength** för ett schemalagt jobb använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-154">To get the value of the **ExecutionHistoryLength** property of a scheduled job, use the following command format:</span></span>

```powershell
(Get-ScheduledJob <JobName>).ExecutionHistoryLength
```

<span data-ttu-id="b0b1d-155">Till exempel hämtar följande kommando värdet för egenskapen **ExecutionHistoryLength** för det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-155">For example, the following command gets the value of the **ExecutionHistoryLength** property of the **ProcessJob** scheduled job.</span></span>

```powershell
(Get-ScheduledJob ProcessJob).ExecutionHistoryLength
```

<span data-ttu-id="b0b1d-156">Om du vill ange eller ändra värdet för egenskapen **ExecutionHistoryLength** använder du parametern **MaxResultCount** för `Register-ScheduledJob` `Set-ScheduledJob` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-156">To set or change the value of the **ExecutionHistoryLength** property, use the **MaxResultCount** parameter of the `Register-ScheduledJob` and `Set-ScheduledJob` cmdlets.</span></span>

<span data-ttu-id="b0b1d-157">Följande kommando ökar värdet för egenskapen **ExecutionHistoryLength** till 50.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-157">The following command increases the value of the **ExecutionHistoryLength** property to 50.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -MaxResultCount 50
```

### <a name="the-job-instance-results-might-have-been-deleted"></a><span data-ttu-id="b0b1d-158">Resultatet av jobb instansen kan ha tagits bort</span><span class="sxs-lookup"><span data-stu-id="b0b1d-158">The job instance results might have been deleted</span></span>

<span data-ttu-id="b0b1d-159">Parametern **ClearExecutionHistory** för `Set-ScheduledJob` cmdleten tar bort körnings historiken för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-159">The **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet deletes the execution history of a job.</span></span> <span data-ttu-id="b0b1d-160">Du kan använda den här funktionen för att frigöra disk utrymme eller ta bort resultat som inte behövs, eller som redan används, analyseras eller sparas på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-160">You can use this feature to free up disk space or delete results that are not needed, or already used, analyzed or saved in a different location.</span></span>

<span data-ttu-id="b0b1d-161">Om du vill ta bort körnings historiken för ett schemalagt jobb använder du parametern **ClearExecutionHistory** för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-161">To delete the execution history of a scheduled job, use the **ClearExecutionHistory** parameter of the scheduled job.</span></span>

<span data-ttu-id="b0b1d-162">Följande kommando tar bort körnings historiken för det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-162">The following command deletes the execution history of the **ProcessJob** scheduled job.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Set-ScheduledJob -ClearExecutionHistory
```

<span data-ttu-id="b0b1d-163">Dessutom `Remove-Job` tar cmdleten bort jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-163">Also, the `Remove-Job` cmdlet deletes job results.</span></span> <span data-ttu-id="b0b1d-164">När du använder `Remove-Job` för att ta bort ett schemalagt jobb raderas alla instanser av jobbet på disken, inklusive körnings historik och alla jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-164">When you use `Remove-Job` to delete a scheduled job, it deletes all instances of the job on disk, including the execution history and all job results.</span></span>

### <a name="jobs-started-by-using-the-start-job-cmdlet-are-not-saved-to-disk"></a><span data-ttu-id="b0b1d-165">Jobb som har startats med hjälp av Start-Job cmdlet sparas inte på disken</span><span class="sxs-lookup"><span data-stu-id="b0b1d-165">Jobs started by using the Start-Job cmdlet are not saved to disk</span></span>

<span data-ttu-id="b0b1d-166">När du använder `Start-Job` för att starta ett schemalagt jobb `Start-Job` startar ett standard bakgrunds jobb i stället för att använda en jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-166">When you use `Start-Job` to start a scheduled job, instead of using a job trigger, `Start-Job` starts a standard background job.</span></span> <span data-ttu-id="b0b1d-167">Bakgrunds jobbet och dess resultat lagras inte i körnings historiken för jobbet på disken.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-167">The background job and its results are not stored in the execution history of the job on disk.</span></span>

<span data-ttu-id="b0b1d-168">Du kan använda `Get-Job` cmdleten för att hämta jobbet och `Receive-Job` cmdleten för att hämta jobb resultatet, men resultaten är bara tillgängliga tills du får dem, om du inte använder parametern Keep för `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-168">You can use the `Get-Job` cmdlet to get the job and the `Receive-Job` cmdlet to get the job results, but the results are available only until you receive them, unless you use the Keep parameter of the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="b0b1d-169">Bakgrunds jobb och deras resultat är också sessionsbaserade. de finns bara i den session där de skapas.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-169">Also, background jobs and their results are session-specific; they exist only in the session in which they are created.</span></span> <span data-ttu-id="b0b1d-170">Om du tar bort jobbet med `Remove-Job` , stänger sessionen eller stänger PowerShell, tas jobb instansen och dess resultat bort.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-170">If you delete the job with `Remove-Job`, close the session or close PowerShell, the job instance and its results are deleted.</span></span>

## <a name="scheduled-job-doesnt-run"></a><span data-ttu-id="b0b1d-171">Schemalagt jobb körs inte</span><span class="sxs-lookup"><span data-stu-id="b0b1d-171">Scheduled job doesn't run</span></span>

<span data-ttu-id="b0b1d-172">Schemalagda jobb körs inte automatiskt om jobbet utlöses eller om det schemalagda jobbet är inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-172">Scheduled jobs don't run automatically if the job triggers or the scheduled job are disabled.</span></span>

<span data-ttu-id="b0b1d-173">Använd `Get-ScheduledJob` cmdleten för att hämta det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-173">Use the `Get-ScheduledJob` cmdlet to get the scheduled job.</span></span> <span data-ttu-id="b0b1d-174">Kontrol lera att värdet för egenskapen **Enabled** för det schemalagda jobbet är **Sant**.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-174">Verify that the value of the **Enabled** property of the scheduled job is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command         Enabled
--         ----            --------        -------         -------
4          ProcessJob      {1, 2}          Get-Process     True
```

```powershell
(Get-ScheduledJob ProcessJob).Enabled
```

```Output
True
```

<span data-ttu-id="b0b1d-175">Använd `Get-JobTrigger` cmdleten för att hämta jobb utlösare för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-175">Use the `Get-JobTrigger` cmdlet to get the job triggers of the scheduled job.</span></span>
<span data-ttu-id="b0b1d-176">Kontrol lera att värdet för den **aktiverade** egenskapen för jobb utlösaren är **Sant**.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-176">Verify that the value of the **Enabled** property of the job trigger is **True**.</span></span>

```powershell
Get-ScheduledJob ProcessJob | Get-JobTrigger
```

```Output
Id      Frequency    Time                   DaysOfWeek            Enabled
--      ---------    ----                   ----------            -------
1       Weekly       11/7/2011 5:00:00 AM   {Monday, Thursday}    True
2       Daily        11/7/2011 3:00:00 PM                         True
```

```powershell
Get-ScheduledJob ProcessJob|Get-JobTrigger|Format-Table ID, Enabled -Auto
```

```Output
Id Enabled
-- -------
1    True
2    True
```

### <a name="scheduled-jobs-dont-run-automatically-if-job-triggers-are-invalid"></a><span data-ttu-id="b0b1d-177">Schemalagda jobb körs inte automatiskt om jobb utlösare är ogiltiga</span><span class="sxs-lookup"><span data-stu-id="b0b1d-177">Scheduled jobs don't run automatically if job triggers are invalid</span></span>

<span data-ttu-id="b0b1d-178">En jobb utlösare kan till exempel ange ett datum tidigare eller ett datum som inte sker, till exempel den femte måndagen i månaden.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-178">For example, a job trigger might specify a date in the past or a date that does not occur, such as the 5th Monday of the month.</span></span>

<span data-ttu-id="b0b1d-179">Schemalagda jobb körs inte automatiskt om villkoren för jobb utlösaren eller jobb alternativen inte är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-179">Scheduled jobs do not run automatically if the conditions of the job trigger or the job options are not satisfied.</span></span>

<span data-ttu-id="b0b1d-180">Till exempel kan ett schemalagt jobb som bara körs när en viss användare loggar in på datorn inte köras om användaren inte loggar in eller endast ansluter via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-180">For example, a scheduled job that runs only when a particular user logs on to the computer will not run if that user does not log on or only connects remotely.</span></span>

<span data-ttu-id="b0b1d-181">Granska alternativen för det schemalagda jobbet och se till att de är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-181">Examine the options of the scheduled job and make sure that they are satisfied.</span></span>
<span data-ttu-id="b0b1d-182">Till exempel ett schemalagt jobb som kräver att datorn är inaktiv eller kräver en nätverks anslutning, eller har en lång **IdleDuration** eller en kort **idleTimeout** kanske aldrig kan köras.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-182">For example, a scheduled job that requires that the computer be idle or requires a network connection, or has a long **IdleDuration** or a brief **IdleTimeout** might never run.</span></span>

<span data-ttu-id="b0b1d-183">Använd `Get-ScheduledJobOption` cmdleten för att undersöka jobb alternativen och deras värden.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-183">Use the `Get-ScheduledJobOption` cmdlet to examine the job options and their values.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
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

<span data-ttu-id="b0b1d-184">Beskrivningar av alternativen för schemalagda jobb finns i [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span><span class="sxs-lookup"><span data-stu-id="b0b1d-184">For descriptions of the scheduled job options, see [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

### <a name="the-scheduled-job-instance-might-have-failed"></a><span data-ttu-id="b0b1d-185">Den schemalagda jobb instansen kan ha misslyckats</span><span class="sxs-lookup"><span data-stu-id="b0b1d-185">The scheduled job instance might have failed</span></span>

<span data-ttu-id="b0b1d-186">Om ett schemalagt jobb-kommando Miss lyckas rapporterar PowerShell direkt genom att generera ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-186">If a scheduled job command fails, PowerShell reports it immediately by generating an error message.</span></span> <span data-ttu-id="b0b1d-187">Men om jobbet Miss lyckas när Schemaläggaren försöker köra det, är felet inte tillgängligt för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-187">However, if the job fails when Task Scheduler tries to run it, the error is not available to PowerShell.</span></span>

<span data-ttu-id="b0b1d-188">Använd följande metoder för att identifiera och korrigera jobb fel:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-188">Use the following methods to detect and correct job failures:</span></span>

<span data-ttu-id="b0b1d-189">Kontrol lera om det finns fel i händelse loggen för Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-189">Check the Task Scheduler event log for errors.</span></span> <span data-ttu-id="b0b1d-190">Om du vill kontrol lera loggen använder Loggboken eller ett PowerShell-kommando, till exempel följande:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-190">To check the log, use Event Viewer or a PowerShell command such as the following:</span></span>

```powershell
Get-WinEvent -LogName Microsoft-Windows-TaskScheduler/Operational |
 Where {$_.Message -like "fail"}
```

<span data-ttu-id="b0b1d-191">Kontrol lera jobb posten i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-191">Check the job record in Task Scheduler.</span></span> <span data-ttu-id="b0b1d-192">Schemalagda PowerShell-jobb lagras i följande schemalagda mapp för aktiviteter:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-192">PowerShell scheduled jobs are stored in the following Task Scheduled folder:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`

### <a name="the-scheduled-job-might-not-run-because-of-insufficient-permission"></a><span data-ttu-id="b0b1d-193">Det schemalagda jobbet kanske inte kan köras på grund av otillräcklig behörighet</span><span class="sxs-lookup"><span data-stu-id="b0b1d-193">The scheduled job might not run because of insufficient permission</span></span>

<span data-ttu-id="b0b1d-194">Schemalagda jobb körs med behörigheterna för den användare som skapade jobbet eller behörigheter för den användare som anges av parametern **Credential** i `Register-ScheduledJob` `Set-ScheduledJob` kommandot eller.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-194">Scheduled jobs run with the permissions of the user who created the job or the permissions of the user who is specified by the **Credential** parameter in the `Register-ScheduledJob` or `Set-ScheduledJob` command.</span></span>

<span data-ttu-id="b0b1d-195">Om användaren inte har behörighet att köra kommandona eller skripten Miss lyckas jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-195">If that user does not have permission to run the commands or scripts, the job fails.</span></span>

## <a name="cant-get-scheduled-job-or-scheduled-job-is-corrupted"></a><span data-ttu-id="b0b1d-196">Det går inte att hämta schemalagt jobb eller schemalagt jobb är skadat</span><span class="sxs-lookup"><span data-stu-id="b0b1d-196">Can't get scheduled job or scheduled job is corrupted</span></span>

<span data-ttu-id="b0b1d-197">I sällsynta fall kan schemalagda jobb skadas eller innehålla interna motstridiga händelser som inte kan lösas.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-197">On rare occasions, scheduled jobs can become corrupted or contain internal contradictions that cannot be resolved.</span></span> <span data-ttu-id="b0b1d-198">Detta inträffar vanligt vis när XML-filerna för det schemalagda jobbet redige ras manuellt, vilket resulterar i ogiltig XML.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-198">Typically, this happens when the XML files for the scheduled job are manually edited, resulting in invalid XML.</span></span>

<span data-ttu-id="b0b1d-199">När ett schemalagt jobb skadas försöker PowerShell ta bort det schemalagda jobbet, dess körnings historik och resultatet från disken.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-199">When a scheduled job is corrupted, PowerShell attempts to delete the scheduled job, its execution history, and its results from disk.</span></span>

<span data-ttu-id="b0b1d-200">Om det inte går att ta bort det schemalagda jobbet får du ett skadat jobb fel meddelande varje gång du kör `Get-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-200">If it cannot remove the scheduled job, you will get a corrupted job error message each time you run the `Get-ScheduledJob` cmdlet.</span></span>

<span data-ttu-id="b0b1d-201">Om du vill ta bort ett skadat schemalagt jobb använder du någon av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-201">To remove a corrupted scheduled job, use either one of the following methods:</span></span>

<span data-ttu-id="b0b1d-202">Ta bort `<ScheduledJobName>` katalogen för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-202">Delete the `<ScheduledJobName>` directory for the scheduled job.</span></span> <span data-ttu-id="b0b1d-203">Ta inte bort **ScheduledJob** -katalogen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-203">Don't delete the **ScheduledJob** directory.</span></span>

<span data-ttu-id="b0b1d-204">Katalogens plats:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-204">The directory's location:</span></span>

`$env:UserProfile\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

<span data-ttu-id="b0b1d-205">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-205">For example:</span></span>

`C:\Users<UserName>\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>.`

<span data-ttu-id="b0b1d-206">Använd Schemaläggaren för att ta bort det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-206">Use Task Scheduler to delete the scheduled job.</span></span> <span data-ttu-id="b0b1d-207">Schemalagda aktiviteter för PowerShell visas i följande sökväg för Schemaläggaren:</span><span class="sxs-lookup"><span data-stu-id="b0b1d-207">PowerShell scheduled tasks appear in the following Task Scheduler path:</span></span>

`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs<ScheduledJobName>`

## <a name="job-cmdlets-cant-consistently-find-scheduled-jobs"></a><span data-ttu-id="b0b1d-208">Jobb-cmdlets kan inte konsekvent hitta schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="b0b1d-208">Job cmdlets can't consistently find scheduled jobs</span></span>

<span data-ttu-id="b0b1d-209">När modulen **PSScheduledJob** inte finns i den aktuella sessionen kan inte jobb-cmdlet: ar Hämta schemalagda jobb, starta dem eller få sina resultat.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-209">When the **PSScheduledJob** module isn't in the current session, the job cmdlets cannot get scheduled jobs, start them, or get their results.</span></span>

<span data-ttu-id="b0b1d-210">Importera **PSScheduledJob** -modulen genom att skriva `Import-Module PSScheduledJob` eller köra eller hämta en cmdlet i modulen, till exempel `Get-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-210">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or run or get any cmdlet in the module, such as the `Get-ScheduledJob` cmdlet.</span></span>
<span data-ttu-id="b0b1d-211">Från och med PowerShell 3,0 importeras moduler automatiskt när du hämtar eller använder valfri cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-211">Beginning in PowerShell 3.0, modules are imported automatically when you get or use any cmdlet in the module.</span></span>

<span data-ttu-id="b0b1d-212">När **PSScheduledJob** -modulen inte finns i den aktuella sessionen är följande kommando ordning möjlig.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-212">When the **PSScheduledJob** module isn't in the current session, the following command sequence is possible.</span></span>

```powershell
Get-Job ProcessJob
```

```Output
Get-Job : The command cannot find the job because the job name
ProcessJob was not found.
Verify the value of the Name parameter, and then try the command again.
+ CategoryInfo          : ObjectNotFound: (ProcessJob:String) [Get-Job],
PSArgumentException
+ FullyQualifiedErrorId : JobWithSpecifiedNameNotFound,Microsoft.PowerShell.
Commands.GetJobCommand
```

```powershell
Get-Job
Get-ScheduledJob ProcessJob
```

```Output
Id         Name            Triggers        Command      Enabled
--         ----            --------        -------      -------
4          ProcessJob      {1}             Get-Process  True
```

```powershell
Get-Job ProcessJob
```

```Output
Id     Name         PSJobTypeName   State       HasMoreData     Location
--     ----         -------------   -----       -----------     --------
43     ProcessJob   PSScheduledJob  Completed   True            localhost
44     ProcessJob   PSScheduledJob  Completed   True            localhost
45     ProcessJob   PSScheduledJob  Completed   True            localhost
46     ProcessJob   PSScheduledJob  Completed   True            localhost
47     ProcessJob   PSScheduledJob  Completed   True            localhost
48     ProcessJob   PSScheduledJob  Completed   True            localhost
49     ProcessJob   PSScheduledJob  Completed   True            localhost
50     ProcessJob   PSScheduledJob  Completed   True            localhost
```

<span data-ttu-id="b0b1d-213">Det här problemet beror på att `Get-ScheduledJob` kommandot automatiskt importerar **PSScheduledJob** -modulen och sedan kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="b0b1d-213">This behavior occurs because the `Get-ScheduledJob` command automatically imports the **PSScheduledJob** module, and then runs the command.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0b1d-214">Se även</span><span class="sxs-lookup"><span data-stu-id="b0b1d-214">See also</span></span>

[<span data-ttu-id="b0b1d-215">about_Scheduled_Jobs_Basics</span><span class="sxs-lookup"><span data-stu-id="b0b1d-215">about_Scheduled_Jobs_Basics</span></span>](about_Scheduled_Jobs_Basics.md)

[<span data-ttu-id="b0b1d-216">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="b0b1d-216">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="b0b1d-217">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="b0b1d-217">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

<span data-ttu-id="b0b1d-218">Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul</span><span class="sxs-lookup"><span data-stu-id="b0b1d-218">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="b0b1d-219">Schemaläggaren</span><span class="sxs-lookup"><span data-stu-id="b0b1d-219">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
