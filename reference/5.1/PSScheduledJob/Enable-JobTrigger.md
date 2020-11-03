---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264662"
---
# <span data-ttu-id="8b4c0-103">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-103">Enable-JobTrigger</span></span>

## <span data-ttu-id="8b4c0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8b4c0-104">SYNOPSIS</span></span>
<span data-ttu-id="8b4c0-105">Aktiverar jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-105">Enables the job triggers of scheduled jobs.</span></span>

## <span data-ttu-id="8b4c0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8b4c0-106">SYNTAX</span></span>

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8b4c0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8b4c0-107">DESCRIPTION</span></span>
<span data-ttu-id="8b4c0-108">Cmdlet: en **Enable-JobTrigger** aktiverar jobb utlösare för schemalagda jobb, t. ex. de som har inaktiverats med hjälp av Disable-JobTrigger-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-108">The **Enable-JobTrigger** cmdlet re-enables job triggers of scheduled jobs, such as those that were disabled by using the Disable-JobTrigger cmdlet.</span></span>
<span data-ttu-id="8b4c0-109">Aktiverade och återaktiverade jobb utlösare kan starta schemalagda jobb omedelbart; du behöver inte starta om Windows eller Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-109">Enabled and re-enabled job triggers can start scheduled jobs immediately; there is no need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="8b4c0-110">Använd cmdleten Get-JobTrigger för att hämta jobb utlösare för att använda denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-110">To use this cmdlet, use the  Get-JobTrigger cmdlet to get the job triggers.</span></span>
<span data-ttu-id="8b4c0-111">Sedan kan du skicka in jobbet triggers för att **Aktivera-JobTrigger** eller använda dess *InputObject* -parameter.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-111">Then pipe the job triggers to **Enable-JobTrigger** or use its *InputObject* parameter.</span></span>

<span data-ttu-id="8b4c0-112">Om du vill aktivera en jobb utlösare anger cmdleten **Enable-JobTrigger** egenskapen Enabled för jobb utlösaren till $true.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-112">To enable a job trigger, the **Enable-JobTrigger** cmdlet sets the Enabled property of the job trigger to $True.</span></span>

<span data-ttu-id="8b4c0-113">**Enable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-113">**Enable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="8b4c0-114">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-114">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="8b4c0-115">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-115">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="8b4c0-116">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="8b4c0-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8b4c0-117">EXAMPLES</span></span>

### <span data-ttu-id="8b4c0-118">Exempel 1: Aktivera en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8b4c0-118">Example 1: Enable a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

<span data-ttu-id="8b4c0-119">Detta kommando aktiverar den första utlösaren (ID = 1) för det schemalagda Backup-Archives jobbet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-119">This command enables the first trigger (ID=1) of the Backup-Archives scheduled job on the local computer.</span></span>

<span data-ttu-id="8b4c0-120">Kommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-120">The command uses the Get-JobTrigger cmdlet to get the job trigger.</span></span>
<span data-ttu-id="8b4c0-121">En pipeline-operator skickar jobb utlösaren till cmdleten **Enable-JobTrigger** , vilket gör det möjligt.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-121">A pipeline operator sends the job trigger to the **Enable-JobTrigger** cmdlet, which enables it.</span></span>

### <span data-ttu-id="8b4c0-122">Exempel 2: Aktivera alla jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8b4c0-122">Example 2: Enable all job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

<span data-ttu-id="8b4c0-123">Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-123">The command uses the Get-ScheduledJob cmdlet to get  the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="8b4c0-124">En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-124">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="8b4c0-125">En annan pipeline-operator skickar jobb utlösare till cmdleten **Enable-JobTrigger** , vilket gör att de kan användas.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-125">Another pipeline operator sends the job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="8b4c0-126">Exempel 3: Aktivera jobb utlösaren för ett schemalagt jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="8b4c0-126">Example 3: Enable the job trigger of a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

<span data-ttu-id="8b4c0-127">Med det här kommandot aktive ras AtLogon-jobbet på det schemalagda DeployPackage-jobbet på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-127">This command re-enables the AtLogon job triggers on the DeployPackage scheduled job on the Server01 remote computer.</span></span>

<span data-ttu-id="8b4c0-128">Kommandot använder cmdleten Invoke-Command för att köra kommandona på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-128">The command uses the Invoke-Command cmdlet to run the commands on the Server01 computer.</span></span>
<span data-ttu-id="8b4c0-129">Fjärrkommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösare för det schemalagda jobbet DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-129">The remote command uses the Get-JobTrigger cmdlet to get the job triggers of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="8b4c0-130">En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet som bara returnerar AtLogon-jobb-utlösare.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-130">A pipeline operator sends the job triggers to the Where-Object cmdlet which returns only AtLogon job triggers.</span></span>
<span data-ttu-id="8b4c0-131">En pipeline-operator skickar AtLogon-jobbet utlösare till cmdleten **Enable-JobTrigger** , vilket gör att de kan användas.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-131">A pipeline operator sends the AtLogon job triggers to the **Enable-JobTrigger** cmdlet, which enables them.</span></span>

### <span data-ttu-id="8b4c0-132">Exempel 4: Visa inaktiverade jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8b4c0-132">Example 4: Display disabled job triggers</span></span>

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

<span data-ttu-id="8b4c0-133">Det här kommandot visar alla inaktiverade jobb utlösare för alla schemalagda jobb i en tabell.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-133">This command displays all disabled job triggers of all scheduled jobs in a table.</span></span>
<span data-ttu-id="8b4c0-134">Du kan använda ett kommando som det här för att identifiera jobb utlösare som kan behöva aktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-134">You can use a command like this one to discover job triggers that might need to be enabled.</span></span>

<span data-ttu-id="8b4c0-135">Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-135">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="8b4c0-136">En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-136">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="8b4c0-137">En annan pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som endast returnerar jobb utlösare som är inaktiverade, det vill säga där värdet för den aktiverade egenskapen för jobb utlösaren inte (!) är sant.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-137">Another pipeline operator sends the job triggers to the Where-Object cmdlet, which returns only job triggers that are disabled, that is, where the value of the Enabled property of the job trigger is not (!) true.</span></span>

<span data-ttu-id="8b4c0-138">En annan pipeline-operator skickar inaktiverade jobb utlösare till Format-Table-cmdlet, som visar de valda egenskaperna för jobb utlösare i en tabell.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-138">Another pipeline operator sends the disabled job triggers to the Format-Table cmdlet, which displays the selected properties of the job triggers in a table.</span></span>
<span data-ttu-id="8b4c0-139">Egenskaperna innehåller en ny JobName-egenskap som visar namnet på det schemalagda jobbet i jobb definitionen-egenskapen för jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-139">The properties include a new JobName property that displays the name of the scheduled job in the JobDefinition property of the job trigger.</span></span>

## <span data-ttu-id="8b4c0-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8b4c0-140">PARAMETERS</span></span>

### <span data-ttu-id="8b4c0-141">– InputObject</span><span class="sxs-lookup"><span data-stu-id="8b4c0-141">-InputObject</span></span>
<span data-ttu-id="8b4c0-142">Anger den jobb utlösare som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-142">Specifies the job trigger to enable.</span></span>
<span data-ttu-id="8b4c0-143">Ange en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-143">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="8b4c0-144">Du kan också skicka ett **ScheduledJobTrigger** -objekt för att **Aktivera-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-144">You can also pipe a **ScheduledJobTrigger** object to **Enable-JobTrigger**.</span></span>

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

### <span data-ttu-id="8b4c0-145">– PassThru</span><span class="sxs-lookup"><span data-stu-id="8b4c0-145">-PassThru</span></span>
<span data-ttu-id="8b4c0-146">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-146">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="8b4c0-147">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="8b4c0-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8b4c0-148">-Confirm</span></span>
<span data-ttu-id="8b4c0-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8b4c0-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8b4c0-150">-WhatIf</span></span>
<span data-ttu-id="8b4c0-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="8b4c0-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8b4c0-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8b4c0-153">CommonParameters</span></span>
<span data-ttu-id="8b4c0-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8b4c0-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8b4c0-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8b4c0-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="8b4c0-156">INPUTS</span></span>

### <span data-ttu-id="8b4c0-157">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="8b4c0-158">Du kan skicka pipe-utlösare för att **Aktivera-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-158">You can pipe job triggers to **Enable-JobTrigger**.</span></span>

## <span data-ttu-id="8b4c0-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8b4c0-159">OUTPUTS</span></span>

### <span data-ttu-id="8b4c0-160">Inget</span><span class="sxs-lookup"><span data-stu-id="8b4c0-160">None</span></span>
<span data-ttu-id="8b4c0-161">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="8b4c0-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8b4c0-162">NOTES</span></span>

* <span data-ttu-id="8b4c0-163">**Enable-JobTrigger** genererar inte fel eller varningar om du aktiverar en jobb utlösare som redan är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8b4c0-163">**Enable-JobTrigger** does not generate errors or warnings if you enable a job trigger that is already enabled.</span></span>

## <span data-ttu-id="8b4c0-164">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8b4c0-164">RELATED LINKS</span></span>

[<span data-ttu-id="8b4c0-165">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-165">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="8b4c0-166">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-166">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="8b4c0-167">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-167">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="8b4c0-168">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-168">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="8b4c0-169">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-169">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="8b4c0-170">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-170">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="8b4c0-171">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-171">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="8b4c0-172">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8b4c0-172">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="8b4c0-173">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-173">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="8b4c0-174">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8b4c0-174">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="8b4c0-175">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-175">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="8b4c0-176">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-176">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="8b4c0-177">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="8b4c0-177">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="8b4c0-178">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-178">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="8b4c0-179">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="8b4c0-179">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="8b4c0-180">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="8b4c0-180">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
