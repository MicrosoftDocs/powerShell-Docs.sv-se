---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264650"
---
# <span data-ttu-id="92d38-103">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="92d38-103">Get-ScheduledJobOption</span></span>

## <span data-ttu-id="92d38-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="92d38-104">SYNOPSIS</span></span>
<span data-ttu-id="92d38-105">Hämtar jobb alternativen för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-105">Gets the job options of scheduled jobs.</span></span>

## <span data-ttu-id="92d38-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92d38-106">SYNTAX</span></span>

### <span data-ttu-id="92d38-107">Jobb definitionen (standard)</span><span class="sxs-lookup"><span data-stu-id="92d38-107">JobDefinition (Default)</span></span>

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### <span data-ttu-id="92d38-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="92d38-108">JobDefinitionId</span></span>

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### <span data-ttu-id="92d38-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="92d38-109">JobDefinitionName</span></span>

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## <span data-ttu-id="92d38-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="92d38-110">DESCRIPTION</span></span>
<span data-ttu-id="92d38-111">**Get-ScheduledJobOption** -cmdlet: en hämtar jobb alternativen för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-111">The **Get-ScheduledJobOption** cmdlet gets the job options of scheduled jobs.</span></span>
<span data-ttu-id="92d38-112">Du kan använda det här kommandot för att undersöka jobb alternativen eller för att skicka vidare jobb alternativen till andra cmdletar.</span><span class="sxs-lookup"><span data-stu-id="92d38-112">You can use this command to examine the job options or to pipe the job options to other cmdlets.</span></span>

<span data-ttu-id="92d38-113">Jobb alternativen sparas inte på disken oberoende av varandra. de ingår i ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-113">Job options are not saved to disk independently; they are part of a scheduled job.</span></span>
<span data-ttu-id="92d38-114">Om du vill hämta jobb alternativen för ett schemalagt jobb anger du det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="92d38-114">To get the job options of a scheduled job, specify the scheduled job.</span></span>

<span data-ttu-id="92d38-115">Använd parametrarna för **Get-ScheduledJobOption** -cmdlet: en för att identifiera det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="92d38-115">Use the parameters of the **Get-ScheduledJobOption** cmdlet to identify the scheduled job.</span></span>
<span data-ttu-id="92d38-116">Du kan identifiera schemalagda jobb baserat på namn eller identifikations nummer, eller genom att ange eller dirigera **ScheduledJob** -objekt, till exempel de som returneras av Get-ScheduledJob cmdlet, för att **Hämta-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="92d38-116">You can identify scheduled jobs by their names or identification numbers, or by entering or piping **ScheduledJob** objects, such as those that are returned by the Get-ScheduledJob cmdlet, to **Get-ScheduledJobOption**.</span></span>

<span data-ttu-id="92d38-117">**Get-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92d38-117">**Get-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="92d38-118">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="92d38-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="92d38-119">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="92d38-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="92d38-120">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="92d38-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="92d38-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="92d38-121">EXAMPLES</span></span>

### <span data-ttu-id="92d38-122">Exempel 1: Hämta jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="92d38-122">Example 1: Get job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : False

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="92d38-123">Det här kommandot hämtar jobb alternativen för schemalagda jobb som har säkerhets kopia i sina namn.</span><span class="sxs-lookup"><span data-stu-id="92d38-123">This command gets the job options of scheduled jobs that have BackUp in their names.</span></span>
<span data-ttu-id="92d38-124">Resultaten visar objektet jobb alternativ som returnerar **-ScheduledJobOption** .</span><span class="sxs-lookup"><span data-stu-id="92d38-124">The results show the job options object that **Get-ScheduledJobOption** returned.</span></span>

### <span data-ttu-id="92d38-125">Exempel 2: Hämta alla jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="92d38-125">Example 2: Get all job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

<span data-ttu-id="92d38-126">Det här kommandot hämtar jobb alternativen för alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="92d38-126">This command gets the job options of all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="92d38-127">Den använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="92d38-127">It uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="92d38-128">En pipeline-operator (|) skickar de schemalagda jobben till **Get-ScheduledJobOption** -cmdleten, som hämtar jobb alternativen för varje schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-128">A pipeline operator (|) sends the scheduled jobs to the **Get-ScheduledJobOption** cmdlet, which gets the job options of each scheduled job.</span></span>

### <span data-ttu-id="92d38-129">Exempel 3: Hämta valda jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="92d38-129">Example 3: Get selected job options</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

<span data-ttu-id="92d38-130">Det här exemplet visar hur du hittar jobb alternativ objekt med specifika värden.</span><span class="sxs-lookup"><span data-stu-id="92d38-130">This example shows how to find job options object with particular values.</span></span>

<span data-ttu-id="92d38-131">Det första kommandot hämtar jobb alternativ där egenskapen RunElevated har värdet $True och egenskapen RunWithoutNetwork har värdet $False.</span><span class="sxs-lookup"><span data-stu-id="92d38-131">The first command gets job options in which the RunElevated property has a value of $True and the RunWithoutNetwork property has a value of $False.</span></span>
<span data-ttu-id="92d38-132">Utdata visar det valda **JobOptions** -objektet.</span><span class="sxs-lookup"><span data-stu-id="92d38-132">The output shows the **JobOptions** object that was selected.</span></span>

### <span data-ttu-id="92d38-133">Exempel 4: Använd jobb alternativ för att skapa ett nytt jobb</span><span class="sxs-lookup"><span data-stu-id="92d38-133">Example 4: Use job options to create a new job</span></span>

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

<span data-ttu-id="92d38-134">Det här exemplet visar hur du använder de jobb alternativ som Get-ScheduledJobOption får i ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-134">This example shows how to use the job options that Get-ScheduledJobOption gets in a new scheduled job.</span></span>

<span data-ttu-id="92d38-135">Det första kommandot använder **Get-ScheduledJobOption** för att hämta jobb alternativen för det schemalagda BackupTestLogs-jobbet.</span><span class="sxs-lookup"><span data-stu-id="92d38-135">The first command uses **Get-ScheduledJobOption** to get the jobs options of the BackupTestLogs scheduled job.</span></span>
<span data-ttu-id="92d38-136">Kommandot sparar alternativen i variabeln $Opts.</span><span class="sxs-lookup"><span data-stu-id="92d38-136">The command saves the options in the $Opts variable.</span></span>

<span data-ttu-id="92d38-137">Det andra kommandot använder Register-ScheduledJob cmdlet för att skapa ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-137">The second command uses Register-ScheduledJob cmdlet to create a new scheduled job.</span></span>
<span data-ttu-id="92d38-138">Värdet för parametern *ScheduledJobOption* är Options-objektet i variabeln $opts.</span><span class="sxs-lookup"><span data-stu-id="92d38-138">The value of the *ScheduledJobOption* parameter is the options object in the $Opts variable.</span></span>

### <span data-ttu-id="92d38-139">Exempel 5: Hämta jobb alternativ från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="92d38-139">Example 5: Get job options from a remote computer</span></span>

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

<span data-ttu-id="92d38-140">Detta kommando använder cmdleten Invoke-Command för att hämta de schemalagda jobb alternativen för DataDemon-jobbet på datorn SRV01.</span><span class="sxs-lookup"><span data-stu-id="92d38-140">This command uses the Invoke-Command cmdlet to get the scheduled job options of the DataDemon job on the Srv01 computer.</span></span>
<span data-ttu-id="92d38-141">Kommandot sparar alternativen i variabeln $O.</span><span class="sxs-lookup"><span data-stu-id="92d38-141">The command saves the options in the $O variable.</span></span>

## <span data-ttu-id="92d38-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="92d38-142">PARAMETERS</span></span>

### <span data-ttu-id="92d38-143">-ID</span><span class="sxs-lookup"><span data-stu-id="92d38-143">-Id</span></span>
<span data-ttu-id="92d38-144">Anger identifikations numret för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-144">Specifies the identification number of a scheduled job.</span></span>
<span data-ttu-id="92d38-145">**Get-ScheduledJobOption** hämtar jobb alternativen för det angivna schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="92d38-145">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>

<span data-ttu-id="92d38-146">Använd Get-ScheduledJob-cmdleten om du vill hämta ID-numren för schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="92d38-146">To get the identification numbers of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="92d38-147">– InputObject</span><span class="sxs-lookup"><span data-stu-id="92d38-147">-InputObject</span></span>
<span data-ttu-id="92d38-148">Anger ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="92d38-148">Specifies a scheduled job.</span></span>
<span data-ttu-id="92d38-149">Ange en variabel som innehåller ett **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar ett **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="92d38-149">Enter a variable that contains a **ScheduledJob** object or type a command or expression that gets a **ScheduledJob** object, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="92d38-150">Du kan också skicka ett **ScheduledJob** -objekt till **Get-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="92d38-150">You can also pipe a **ScheduledJob** object to **Get-ScheduledJobOption**.</span></span>

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

### <span data-ttu-id="92d38-151">-Name</span><span class="sxs-lookup"><span data-stu-id="92d38-151">-Name</span></span>
<span data-ttu-id="92d38-152">Anger namnen på de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="92d38-152">Specifies the names of scheduled jobs.</span></span>
<span data-ttu-id="92d38-153">**Get-ScheduledJobOption** hämtar jobb alternativen för det angivna schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="92d38-153">**Get-ScheduledJobOption** gets the job options of the specified scheduled job.</span></span>
<span data-ttu-id="92d38-154">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="92d38-154">Wildcards are supported.</span></span>

<span data-ttu-id="92d38-155">Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="92d38-155">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="92d38-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92d38-156">CommonParameters</span></span>
<span data-ttu-id="92d38-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92d38-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92d38-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="92d38-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92d38-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="92d38-159">INPUTS</span></span>

### <span data-ttu-id="92d38-160">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="92d38-160">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="92d38-161">Du kan skicka vidare ett schemalagt jobb från Get-ScheduledJob till **Get-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="92d38-161">You can pipe a scheduled job from Get-ScheduledJob to **Get-ScheduledJobOption**.</span></span>

## <span data-ttu-id="92d38-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="92d38-162">OUTPUTS</span></span>

### <span data-ttu-id="92d38-163">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="92d38-163">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="92d38-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="92d38-164">NOTES</span></span>

## <span data-ttu-id="92d38-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="92d38-165">RELATED LINKS</span></span>

[<span data-ttu-id="92d38-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="92d38-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="92d38-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="92d38-169">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="92d38-170">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="92d38-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="92d38-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="92d38-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="92d38-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="92d38-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="92d38-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="92d38-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="92d38-176">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="92d38-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="92d38-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="92d38-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="92d38-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="92d38-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="92d38-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="92d38-181">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="92d38-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
