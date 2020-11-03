---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264698"
---
# <span data-ttu-id="308f3-103">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-103">Disable-JobTrigger</span></span>

## <span data-ttu-id="308f3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="308f3-104">SYNOPSIS</span></span>
<span data-ttu-id="308f3-105">Inaktiverar jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="308f3-105">Disables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="308f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="308f3-106">SYNTAX</span></span>

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="308f3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="308f3-107">DESCRIPTION</span></span>
<span data-ttu-id="308f3-108">Cmdlet **: en Disable-JobTrigger** inaktiverar tillfälligt jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="308f3-108">The **Disable-JobTrigger** cmdlet temporarily disables the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="308f3-109">Om du inaktiverar bevaras alla egenskaper för jobb utlösare, men jobb utlösaren förhindras från att starta det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="308f3-109">Disabling preserves all job trigger properties, but it prevents the job trigger from starting the scheduled job.</span></span>

<span data-ttu-id="308f3-110">Använd cmdleten Get-JobTrigger för att hämta jobb utlösare för att använda denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="308f3-110">To use this cmdlet, use the Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="308f3-111">Sedan kan du skicka in jobb utlösarna för att **inaktivera-JobTrigger** eller använda dess *InputObject* -parameter.</span><span class="sxs-lookup"><span data-stu-id="308f3-111">Then pipe the job triggers to **Disable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="308f3-112">Om du vill inaktivera en jobb utlösare anger cmdleten **disable-JobTrigger** egenskapen Enabled för jobb utlösaren till $false.</span><span class="sxs-lookup"><span data-stu-id="308f3-112">To disable a job trigger, the **Disable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $False.</span></span>
<span data-ttu-id="308f3-113">Om du vill aktivera jobb utlösaren igen använder du cmdleten Enable-JobTrigger, som anger egenskapen **Enabled** för jobb utlösaren till $true.</span><span class="sxs-lookup"><span data-stu-id="308f3-113">To re-enable the job trigger, use the Enable-JobTrigger cmdlet, which sets the **Enabled** property of the job trigger to $True.</span></span>
<span data-ttu-id="308f3-114">Om du inaktiverar en jobb utlösare inaktive ras inte det schemalagda jobbet, som görs av Disable-ScheduledJob cmdleten, men om du inaktiverar alla jobb utlösare är resultatet detsamma som att inaktivera det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="308f3-114">Disabling a job trigger does not disable the scheduled job, such as is done by the Disable-ScheduledJob cmdlet, but if you disable all job triggers, the effect is the same as disabling the scheduled job.</span></span>

<span data-ttu-id="308f3-115">Om du inaktiverar ett schemalagt jobb eller inaktiverar alla jobb utlösare för ett schemalagt jobb kan du fortfarande starta jobbet med hjälp av Start-Job-cmdlet eller använda det inaktiverade schemalagda jobbet som en mall.</span><span class="sxs-lookup"><span data-stu-id="308f3-115">If you disable a scheduled job or disable all job triggers of a scheduled job, you can still start the job by using the Start-Job cmdlet or use the disabled scheduled job as a template.</span></span>

<span data-ttu-id="308f3-116">**Disable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="308f3-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="308f3-117">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="308f3-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="308f3-118">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="308f3-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="308f3-119">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="308f3-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="308f3-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="308f3-120">EXAMPLES</span></span>

### <span data-ttu-id="308f3-121">Exempel 1: inaktivera en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="308f3-121">Example 1: Disable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

<span data-ttu-id="308f3-122">Detta kommando inaktiverar den första utlösaren (ID = 1) för det schemalagda Backup-Archives jobbet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="308f3-122">This command disables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="308f3-123">Kommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="308f3-123">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="308f3-124">En pipeline-operator skickar jobb utlösaren till cmdleten **disable-JobTrigger** , vilket inaktiverar den.</span><span class="sxs-lookup"><span data-stu-id="308f3-124">A pipeline operator sends the job trigger to the **Disable-JobTrigger** cmdlet, which disables it.</span></span>

### <span data-ttu-id="308f3-125">Exempel 2: inaktivera alla jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="308f3-125">Example 2: Disable all job triggers</span></span>

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="308f3-126">Dessa kommandon inaktiverar alla jobb utlösare på två schemalagda jobb och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="308f3-126">These commands disable all job triggers on two scheduled jobs and display the results.</span></span>

### <span data-ttu-id="308f3-127">Exempel 3: inaktivera jobb utlösare för schemalagda jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="308f3-127">Example 3: Disable job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

<span data-ttu-id="308f3-128">Med det här kommandot inaktive ras de dagliga jobb utlösarna på det schemalagda DeployPackage-jobbet på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="308f3-128">This command disables the daily job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="308f3-129">Kommandot använder cmdleten Invoke-Command för att köra kommandona på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="308f3-129">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="308f3-130">Fjärrkommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösare för det schemalagda jobbet DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="308f3-130">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="308f3-131">En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som endast returnerar dagliga jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="308f3-131">A pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only daily job triggers.</span></span>
<span data-ttu-id="308f3-132">En pipeline-operator skickar dagliga jobb utlösare till cmdleten **disable-JobTrigger** , vilket inaktiverar dem.</span><span class="sxs-lookup"><span data-stu-id="308f3-132">A pipeline operator sends the daily job triggers to the **Disable-JobTrigger** cmdlet, which disables them.</span></span>

## <span data-ttu-id="308f3-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="308f3-133">PARAMETERS</span></span>

### <span data-ttu-id="308f3-134">– InputObject</span><span class="sxs-lookup"><span data-stu-id="308f3-134">-InputObject</span></span>
<span data-ttu-id="308f3-135">Anger den jobb utlösare som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="308f3-135">Specifies the job trigger to be disabled.</span></span>
<span data-ttu-id="308f3-136">Ange en variabel som innehåller  **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.</span><span class="sxs-lookup"><span data-stu-id="308f3-136">Enter a variable that contains  **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="308f3-137">Du kan också skicka ett **ScheduledJobTrigger** -objekt till **disable-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="308f3-137">You can also pipe a **ScheduledJobTrigger** object to **Disable-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="308f3-138">– PassThru</span><span class="sxs-lookup"><span data-stu-id="308f3-138">-PassThru</span></span>
<span data-ttu-id="308f3-139">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="308f3-139">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="308f3-140">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="308f3-140">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="308f3-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="308f3-141">-Confirm</span></span>
<span data-ttu-id="308f3-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="308f3-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="308f3-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="308f3-143">-WhatIf</span></span>
<span data-ttu-id="308f3-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="308f3-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="308f3-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="308f3-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="308f3-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="308f3-146">CommonParameters</span></span>
<span data-ttu-id="308f3-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="308f3-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="308f3-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="308f3-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="308f3-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="308f3-149">INPUTS</span></span>

### <span data-ttu-id="308f3-150">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-150">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="308f3-151">Du kan skicka pipe-utlösare för att **inaktivera-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="308f3-151">You can pipe job triggers to **Disable-JobTrigger**.</span></span>

## <span data-ttu-id="308f3-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="308f3-152">OUTPUTS</span></span>

### <span data-ttu-id="308f3-153">Inget</span><span class="sxs-lookup"><span data-stu-id="308f3-153">None</span></span>
<span data-ttu-id="308f3-154">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="308f3-154">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="308f3-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="308f3-155">NOTES</span></span>

* <span data-ttu-id="308f3-156">**Disable-JobTrigger** genererar inte fel eller varningar om du inaktiverar en jobb utlösare som redan är inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="308f3-156">**Disable-JobTrigger** does not generate errors or warnings if you disable a job trigger that is already disabled.</span></span>

## <span data-ttu-id="308f3-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="308f3-157">RELATED LINKS</span></span>

[<span data-ttu-id="308f3-158">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-158">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="308f3-159">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-159">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="308f3-160">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-160">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="308f3-161">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-161">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="308f3-162">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-162">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="308f3-163">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-163">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="308f3-164">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-164">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="308f3-165">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="308f3-165">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="308f3-166">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-166">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="308f3-167">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="308f3-167">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="308f3-168">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-168">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="308f3-169">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-169">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="308f3-170">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="308f3-170">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="308f3-171">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-171">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="308f3-172">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="308f3-172">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="308f3-173">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="308f3-173">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
