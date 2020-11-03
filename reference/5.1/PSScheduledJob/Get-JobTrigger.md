---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264657"
---
# <span data-ttu-id="e4df7-103">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-103">Get-JobTrigger</span></span>

## <span data-ttu-id="e4df7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e4df7-104">SYNOPSIS</span></span>
<span data-ttu-id="e4df7-105">Hämtar jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-105">Gets the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="e4df7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4df7-106">SYNTAX</span></span>

### <span data-ttu-id="e4df7-107">Jobb definitionen (standard)</span><span class="sxs-lookup"><span data-stu-id="e4df7-107">JobDefinition (Default)</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="e4df7-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="e4df7-108">JobDefinitionId</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="e4df7-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="e4df7-109">JobDefinitionName</span></span>

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="e4df7-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e4df7-110">DESCRIPTION</span></span>
<span data-ttu-id="e4df7-111">**Get-JobTrigger** -cmdlet: en hämtar jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-111">The **Get-JobTrigger** cmdlet gets the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="e4df7-112">Du kan använda det här kommandot för att undersöka jobb utlösare eller för att skicka jobb utlösare till andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e4df7-112">You can use this command to examine the job triggers or to pipe the job triggers to other cmdlets.</span></span>

<span data-ttu-id="e4df7-113">En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-113">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="e4df7-114">Jobb utlösare sparas inte på disken oberoende av varandra. de ingår i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-114">Job triggers are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="e4df7-115">Om du vill hämta en jobb utlösare anger du det schemalagda jobbet som utlösaren startar.</span><span class="sxs-lookup"><span data-stu-id="e4df7-115">To get a job trigger, specify the scheduled job that the trigger starts.</span></span>

<span data-ttu-id="e4df7-116">Använd parametrarna för **Get-JobTrigger** -cmdlet: en för att identifiera de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="e4df7-116">Use the parameters of the **Get-JobTrigger** cmdlet to identify the scheduled jobs.</span></span>
<span data-ttu-id="e4df7-117">Du kan identifiera de schemalagda jobben med hjälp av namn eller identifierings nummer, eller genom att ange eller dirigera **ScheduledJob** objekt, till exempel de som returneras av Get-ScheduledJob cmdlet, för att **Hämta-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="e4df7-117">You can identify the scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-JobTrigger**.</span></span>

<span data-ttu-id="e4df7-118">**Get-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4df7-118">**Get-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="e4df7-119">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="e4df7-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="e4df7-120">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="e4df7-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="e4df7-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e4df7-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="e4df7-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e4df7-122">EXAMPLES</span></span>

### <span data-ttu-id="e4df7-123">Exempel 1: Hämta en jobb utlösare efter schemalagt jobbnamn</span><span class="sxs-lookup"><span data-stu-id="e4df7-123">Example 1: Get a job trigger by scheduled job name</span></span>

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

<span data-ttu-id="e4df7-124">Kommandot använder *Name* -parametern för **Get-JobTrigger** för att hämta jobb utlösare för det schemalagda BackupJob-jobbet.</span><span class="sxs-lookup"><span data-stu-id="e4df7-124">The command uses the *Name* parameter of **Get-JobTrigger** to get the job triggers of the BackupJob scheduled job.</span></span>

### <span data-ttu-id="e4df7-125">Exempel 2: Hämta en jobb utlösare efter ID</span><span class="sxs-lookup"><span data-stu-id="e4df7-125">Example 2: Get a job trigger by ID</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

<span data-ttu-id="e4df7-126">Exemplet använder *ID-* parametern för **Get-JobTrigger** för att hämta jobb utlösare för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-126">The example uses the *ID* parameter of **Get-JobTrigger** to get the job triggers of a scheduled job.</span></span>

### <span data-ttu-id="e4df7-127">Exempel 3: Hämta jobb utlösare genom att skicka ett jobb</span><span class="sxs-lookup"><span data-stu-id="e4df7-127">Example 3: Get job triggers by piping a job</span></span>

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

<span data-ttu-id="e4df7-128">Det här kommandot hämtar jobb utlösare för alla jobb som har säkerhets kopierings-eller Arkiv namn.</span><span class="sxs-lookup"><span data-stu-id="e4df7-128">This command gets the job triggers of all jobs that have Backup or Archive in their names.</span></span>

### <span data-ttu-id="e4df7-129">Exempel 4: Hämta jobb utlösaren för ett jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="e4df7-129">Example 4: Get the job trigger of a job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

<span data-ttu-id="e4df7-130">Det här kommandot hämtar en av de två jobb utlösarna för ett schemalagt jobb på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e4df7-130">This command gets one of the two job triggers of a scheduled job on a remote computer.</span></span>

<span data-ttu-id="e4df7-131">Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="e4df7-131">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>
<span data-ttu-id="e4df7-132">Den använder Get-ScheduledJob-cmdlet för att hämta det schemalagda säkerhets kopierings jobbet, som den rör till cmdleten **Get-JobTrigger** .</span><span class="sxs-lookup"><span data-stu-id="e4df7-132">It uses the Get-ScheduledJob cmdlet to get the Backup scheduled job, which it pipes to the **Get-JobTrigger** cmdlet.</span></span>
<span data-ttu-id="e4df7-133">Parametern *TriggerID* används för att bara hämta den andra utlösaren.</span><span class="sxs-lookup"><span data-stu-id="e4df7-133">It uses the *TriggerID* parameter to get only the second trigger.</span></span>

### <span data-ttu-id="e4df7-134">Exempel 5: Hämta alla jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="e4df7-134">Example 5: Get all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

<span data-ttu-id="e4df7-135">Det här kommandot hämtar alla jobb utlösare för alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e4df7-135">This command gets all job triggers of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="e4df7-136">Kommandot använder Get-ScheduledJob för att hämta de schemalagda jobben på den lokala datorn och rör dem för att **Hämta-JobTrigger** , som hämtar jobb utlösaren för varje schemalagt jobb (om det finns några).</span><span class="sxs-lookup"><span data-stu-id="e4df7-136">The command uses the Get-ScheduledJob to get the scheduled jobs on the local computer and pipes them to **Get-JobTrigger** , which gets the job trigger of each scheduled job (if any).</span></span>

<span data-ttu-id="e4df7-137">Om du vill lägga till namnet på det schemalagda jobbet i jobb utlösaren, använder kommandot funktionen för beräknade egenskaper i Format-Table-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e4df7-137">To add the name of the scheduled job to the job trigger display, the command uses the calculated property feature of the Format-Table cmdlet.</span></span>
<span data-ttu-id="e4df7-138">Utöver de egenskaper för jobb utlösare som visas som standard skapar kommandot en ny ScheduledJob-egenskap som visar namnet på det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="e4df7-138">In addition to the job trigger properties that are displayed by default, the command creates a new ScheduledJob property that displays the name of the scheduled job.</span></span>

### <span data-ttu-id="e4df7-139">Exempel 6: Hämta jobb utlösarens egenskap för ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="e4df7-139">Example 6: Get the job trigger property of a scheduled job</span></span>

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

<span data-ttu-id="e4df7-140">Jobb utlösare för ett schemalagt jobb lagras i jobbets egenskap JobTriggers.</span><span class="sxs-lookup"><span data-stu-id="e4df7-140">The job triggers of a scheduled job are stored in the JobTriggers property of the job.</span></span>
<span data-ttu-id="e4df7-141">I det här exemplet visas alternativ för att använda cmdleten **Get-JobTrigger** för att hämta jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="e4df7-141">This example shows alternatives to using the **Get-JobTrigger** cmdlet to get job triggers.</span></span>
<span data-ttu-id="e4df7-142">Resultaten är identiska med att använda cmdleten **Get-JobTrigger** och teknikerna kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="e4df7-142">The results are identical to using the **Get-JobTrigger** cmdlet and the techniques can be used interchangeably.</span></span>

### <span data-ttu-id="e4df7-143">Exempel 7: jämför jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="e4df7-143">Example 7: Compare job triggers</span></span>

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

<span data-ttu-id="e4df7-144">Det här exemplet visar hur du jämför jobb utlösare för två schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-144">This example shows how to compare the job triggers of two scheduled jobs.</span></span>

## <span data-ttu-id="e4df7-145">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e4df7-145">PARAMETERS</span></span>

### <span data-ttu-id="e4df7-146">-ID</span><span class="sxs-lookup"><span data-stu-id="e4df7-146">-Id</span></span>
<span data-ttu-id="e4df7-147">Anger identifikations numret för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-147">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="e4df7-148">**Get-JobTrigger** hämtar jobb utlösaren för det angivna schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="e4df7-148">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>

<span data-ttu-id="e4df7-149">Använd Get-ScheduledJob-cmdlet för att hämta identifikations antalet schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e4df7-149">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4df7-150">– InputObject</span><span class="sxs-lookup"><span data-stu-id="e4df7-150">-InputObject</span></span>
<span data-ttu-id="e4df7-151">Anger ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-151">Specifies a scheduled job.</span></span>
<span data-ttu-id="e4df7-152">Ange en variabel som innehåller  **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="e4df7-152">Enter a variable that contains  **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="e4df7-153">Du kan också skicka pipe- **ScheduledJob** objekt till **Get-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="e4df7-153">You can also pipe **ScheduledJob** objects to **Get-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e4df7-154">-Name</span><span class="sxs-lookup"><span data-stu-id="e4df7-154">-Name</span></span>
<span data-ttu-id="e4df7-155">Anger namnet på ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-155">Specifies the name of a scheduled job.</span></span>
<span data-ttu-id="e4df7-156">**Get-JobTrigger** hämtar jobb utlösaren för det angivna schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="e4df7-156">**Get-JobTrigger** gets the job trigger of the specified scheduled job.</span></span>
<span data-ttu-id="e4df7-157">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="e4df7-157">Wildcards are supported.</span></span>

<span data-ttu-id="e4df7-158">Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e4df7-158">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4df7-159">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="e4df7-159">-TriggerId</span></span>
<span data-ttu-id="e4df7-160">Hämtar de angivna jobb utlösarna.</span><span class="sxs-lookup"><span data-stu-id="e4df7-160">Gets the specified job triggers.</span></span>
<span data-ttu-id="e4df7-161">Ange utlösar-ID: n för en eller flera jobb utlösare för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="e4df7-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="e4df7-162">Använd den här parametern när det schemalagda jobbet som anges av parametrarna *Name* , *ID* eller *InputObject* har flera jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="e4df7-162">Use this parameter when the scheduled job that is specified by the *Name* , *ID* , or *InputObject* parameters has multiple job triggers.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4df7-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4df7-163">CommonParameters</span></span>
<span data-ttu-id="e4df7-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4df7-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4df7-165">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e4df7-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4df7-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="e4df7-166">INPUTS</span></span>

### <span data-ttu-id="e4df7-167">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="e4df7-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="e4df7-168">Du kan skicka vidare ett schemalagt jobb från Get-ScheduledJob till **Get-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="e4df7-168">You can pipe a scheduled job from Get-ScheduledJob to **Get-JobTrigger**.</span></span>

## <span data-ttu-id="e4df7-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e4df7-169">OUTPUTS</span></span>

### <span data-ttu-id="e4df7-170">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-170">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="e4df7-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e4df7-171">NOTES</span></span>

## <span data-ttu-id="e4df7-172">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e4df7-172">RELATED LINKS</span></span>

[<span data-ttu-id="e4df7-173">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-173">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="e4df7-174">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-174">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="e4df7-175">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-175">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="e4df7-176">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-176">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="e4df7-177">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-177">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="e4df7-178">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-178">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="e4df7-179">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-179">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="e4df7-180">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e4df7-180">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="e4df7-181">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-181">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="e4df7-182">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e4df7-182">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="e4df7-183">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-183">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="e4df7-184">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-184">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="e4df7-185">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="e4df7-185">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="e4df7-186">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-186">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="e4df7-187">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="e4df7-187">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="e4df7-188">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="e4df7-188">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
