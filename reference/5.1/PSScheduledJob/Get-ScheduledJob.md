---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264656"
---
# <span data-ttu-id="55df4-103">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-103">Get-ScheduledJob</span></span>

## <span data-ttu-id="55df4-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="55df4-104">SYNOPSIS</span></span>
<span data-ttu-id="55df4-105">Hämtar schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-105">Gets scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="55df4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="55df4-106">SYNTAX</span></span>

### <span data-ttu-id="55df4-107">DefinitionId (standard)</span><span class="sxs-lookup"><span data-stu-id="55df4-107">DefinitionId (Default)</span></span>

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="55df4-108">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="55df4-108">DefinitionName</span></span>

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="55df4-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="55df4-109">DESCRIPTION</span></span>
<span data-ttu-id="55df4-110">**Get-ScheduledJob** -cmdlet: en hämtar schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-110">The **Get-ScheduledJob** cmdlet gets scheduled jobs on the local computer.</span></span>
<span data-ttu-id="55df4-111">**Get-ScheduledJob** hämtar endast schemalagda jobb som skapats av den aktuella användaren med hjälp av Register-ScheduledJob-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="55df4-111">**Get-ScheduledJob** gets only scheduled jobs that are created by the current user using the Register-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="55df4-112">Även om jobb som har skapats med hjälp av **register-ScheduledJob** -cmdleten visas i Schemaläggaren, får **Get-ScheduledJob** endast schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="55df4-112">Although jobs that are created by using the **Register-ScheduledJob** cmdlet appear in Task Scheduler, **Get-ScheduledJob** gets only scheduled jobs.</span></span>
<span data-ttu-id="55df4-113">Det går inte att skapa schemalagda aktiviteter som har skapats i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="55df4-113">It does not get scheduled tasks created in Task Scheduler.</span></span>

<span data-ttu-id="55df4-114">Utan parametrar hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-114">Without parameters, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="55df4-115">Du kan använda parametrarna för **Get-ScheduledJob** för att hämta schemalagda jobb efter ID eller namn och granska dem eller skicka vidare till andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="55df4-115">You can use the parameters of **Get-ScheduledJob** to get scheduled jobs by ID or name and examine them or pipe them to other cmdlets.</span></span>

<span data-ttu-id="55df4-116">**Get-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="55df4-116">**Get-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="55df4-117">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="55df4-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="55df4-118">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="55df4-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="55df4-119">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="55df4-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="55df4-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="55df4-120">EXAMPLES</span></span>

### <span data-ttu-id="55df4-121">Exempel 1: Hämta alla schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="55df4-121">Example 1: Get all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob
```

<span data-ttu-id="55df4-122">Det här kommandot hämtar alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-122">This command gets all scheduled jobs on the local computer.</span></span>

### <span data-ttu-id="55df4-123">Exempel 2: Hämta schemalagda jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="55df4-123">Example 2: Get scheduled jobs by name</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

<span data-ttu-id="55df4-124">Det här kommandot hämtar alla schemalagda jobb på datorn som har namn som innehåller säkerhets kopiering eller arkiv.</span><span class="sxs-lookup"><span data-stu-id="55df4-124">This command gets all scheduled jobs on the computer that have names that include Backup or Archive.</span></span>
<span data-ttu-id="55df4-125">Med det här kommando formatet kan du söka efter specifika jobb.</span><span class="sxs-lookup"><span data-stu-id="55df4-125">This command format lets you search for particular jobs.</span></span>

### <span data-ttu-id="55df4-126">Exempel 3: Hämta schemalagda jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="55df4-126">Example 3: Get scheduled jobs on remote computers</span></span>

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

<span data-ttu-id="55df4-127">Det här kommandot hämtar alla schemalagda jobb på de datorer som anges i Servers.txt-filen.</span><span class="sxs-lookup"><span data-stu-id="55df4-127">This command gets all scheduled jobs on the computers that are listed in the Servers.txt file.</span></span>
<span data-ttu-id="55df4-128">Kommandot använder cmdleten Invoke-Command för att köra kommandot **Get-ScheduleJob** på varje dator.</span><span class="sxs-lookup"><span data-stu-id="55df4-128">The command uses the Invoke-Command cmdlet to run a **Get-ScheduleJob** command on each computer.</span></span>

### <span data-ttu-id="55df4-129">Exempel 4: skicka schemalagda jobb till andra cmdletar för pipe</span><span class="sxs-lookup"><span data-stu-id="55df4-129">Example 4: Pipe scheduled jobs to other cmdlets</span></span>

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

<span data-ttu-id="55df4-130">Med det här kommandot hämtas jobb utlösare för de schemalagda jobben DailyBackup och WeeklyBackup.</span><span class="sxs-lookup"><span data-stu-id="55df4-130">This command gets the job triggers of the DailyBackup and WeeklyBackup scheduled jobs.</span></span>
<span data-ttu-id="55df4-131">Den använder cmdleten **Get-ScheduledJob** för att hämta de schemalagda jobben och Get-JobTrigger-cmdleten för att hämta jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="55df4-131">It uses the **Get-ScheduledJob** cmdlet to get the scheduled jobs and the Get-JobTrigger cmdlet to get the job triggers of the scheduled jobs.</span></span>

## <span data-ttu-id="55df4-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="55df4-132">PARAMETERS</span></span>

### <span data-ttu-id="55df4-133">-ID</span><span class="sxs-lookup"><span data-stu-id="55df4-133">-Id</span></span>
<span data-ttu-id="55df4-134">Hämtar bara de schemalagda jobben med det angivna ID-numret (ID).</span><span class="sxs-lookup"><span data-stu-id="55df4-134">Gets only the scheduled jobs with the specified identification number (ID).</span></span>
<span data-ttu-id="55df4-135">Ange ett eller flera ID: n för schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-135">Enter one or more IDs of scheduled jobs on the computer.</span></span>
<span data-ttu-id="55df4-136">Som standard hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-136">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55df4-137">-Name</span><span class="sxs-lookup"><span data-stu-id="55df4-137">-Name</span></span>
<span data-ttu-id="55df4-138">Hämtar bara de schemalagda jobben med de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="55df4-138">Gets only the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="55df4-139">Ange ett eller flera namn för schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-139">Enter one or more names of scheduled jobs on the computer.</span></span>
<span data-ttu-id="55df4-140">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="55df4-140">Wildcards are supported.</span></span>
<span data-ttu-id="55df4-141">Som standard hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-141">By default, **Get-ScheduledJob** gets all scheduled jobs on the computer.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55df4-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55df4-142">CommonParameters</span></span>
<span data-ttu-id="55df4-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="55df4-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55df4-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="55df4-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="55df4-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="55df4-145">INPUTS</span></span>

### <span data-ttu-id="55df4-146">Inget</span><span class="sxs-lookup"><span data-stu-id="55df4-146">None</span></span>
<span data-ttu-id="55df4-147">Du kan inte skicka pipe-ininformation till **Get-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="55df4-147">You cannot pipe input to **Get-ScheduledJob**.</span></span>

## <span data-ttu-id="55df4-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="55df4-148">OUTPUTS</span></span>

### <span data-ttu-id="55df4-149">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="55df4-149">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="55df4-150">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="55df4-150">NOTES</span></span>

* <span data-ttu-id="55df4-151">Varje schemalagt jobb sparas i en under katalog till katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="55df4-151">Each scheduled job is saved in a subdirectory of the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory on the local computer.</span></span> <span data-ttu-id="55df4-152">Under katalogen är namngiven för det schemalagda jobbet och innehåller XML-filen för det schemalagda jobbet och poster i körnings historiken.</span><span class="sxs-lookup"><span data-stu-id="55df4-152">The subdirectory is named for the scheduled job and contains the XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="55df4-153">Mer information om schemalagda jobb på disk finns about_Scheduled_Jobs_Advanced.</span><span class="sxs-lookup"><span data-stu-id="55df4-153">For more information about scheduled jobs on disk, see about_Scheduled_Jobs_Advanced.</span></span>
* <span data-ttu-id="55df4-154">Schemalagda jobb som du skapar i Windows PowerShell visas i Schemaläggaren i Library\Microsoft\Windows\PowerShell\ScheduledJobs-mappen Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="55df4-154">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs folder.</span></span> <span data-ttu-id="55df4-155">Du kan använda Schemaläggaren för att visa och redigera det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="55df4-155">You can use Task Scheduler to view and edit the scheduled job.</span></span>
* <span data-ttu-id="55df4-156">Du kan använda Schemaläggaren, SchTasks.exe kommando rads verktyget och Schemaläggaren-cmdletar för att hantera schemalagda jobb som du skapar med de schemalagda jobb-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="55df4-156">You can use Task Scheduler, the SchTasks.exe command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="55df4-157">Du kan dock inte använda de schemalagda jobb-cmdletarna för att hantera aktiviteter som du skapar i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="55df4-157">However, you cannot use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

## <span data-ttu-id="55df4-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="55df4-158">RELATED LINKS</span></span>

[<span data-ttu-id="55df4-159">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-159">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="55df4-160">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-160">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="55df4-161">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-161">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="55df4-162">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-162">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="55df4-163">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-163">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="55df4-164">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-164">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="55df4-165">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-165">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="55df4-166">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="55df4-166">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="55df4-167">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-167">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="55df4-168">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="55df4-168">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="55df4-169">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-169">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="55df4-170">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-170">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="55df4-171">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="55df4-171">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="55df4-172">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-172">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="55df4-173">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="55df4-173">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="55df4-174">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="55df4-174">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
