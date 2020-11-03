---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264638"
---
# <span data-ttu-id="9dda1-103">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-103">Remove-JobTrigger</span></span>

## <span data-ttu-id="9dda1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9dda1-104">SYNOPSIS</span></span>
<span data-ttu-id="9dda1-105">Ta bort jobb utlösare från schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-105">Delete job triggers from scheduled jobs.</span></span>

## <span data-ttu-id="9dda1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9dda1-106">SYNTAX</span></span>

### <span data-ttu-id="9dda1-107">Jobb definitionen (standard)</span><span class="sxs-lookup"><span data-stu-id="9dda1-107">JobDefinition (Default)</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### <span data-ttu-id="9dda1-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="9dda1-108">JobDefinitionId</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="9dda1-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="9dda1-109">JobDefinitionName</span></span>

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="9dda1-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9dda1-110">DESCRIPTION</span></span>
<span data-ttu-id="9dda1-111">Cmdlet: en **Remove-JobTrigger** tar bort jobb utlösare från schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-111">The **Remove-JobTrigger** cmdlet deletes job triggers from scheduled jobs.</span></span>

<span data-ttu-id="9dda1-112">En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-112">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="9dda1-113">Om du vill hantera jobb utlösare använder du cmdletarna New-JobTrigger, Add-JobTrigger, set-JobTrigger och Set-ScheduledJob.</span><span class="sxs-lookup"><span data-stu-id="9dda1-113">To manage job triggers, use the New-JobTrigger, Add-JobTrigger, Set-JobTrigger, and Set-ScheduledJob cmdlets.</span></span>

<span data-ttu-id="9dda1-114">Använd *namnen* , *ID* eller *InputObject* -parametrarna för **Remove-JobTrigger** för att identifiera de schemalagda jobb som utlösarna tas bort från.</span><span class="sxs-lookup"><span data-stu-id="9dda1-114">Use the *Name* , *ID* , or *InputObject* parameters of **Remove-JobTrigger** to identify the scheduled jobs from which the triggers are removed.</span></span>
<span data-ttu-id="9dda1-115">Använd parametern *TriggerID* för att identifiera de jobb utlösare som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="9dda1-115">Use the *TriggerID* parameter to identify the job triggers to delete.</span></span>
<span data-ttu-id="9dda1-116">Som standard tar **Remove-JobTrigger** bort alla jobb utlösare för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-116">By default, **Remove-JobTrigger** deletes all job triggers of a scheduled job.</span></span>

<span data-ttu-id="9dda1-117">**Remove-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9dda1-117">**Remove-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="9dda1-118">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="9dda1-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="9dda1-119">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="9dda1-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="9dda1-120">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="9dda1-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="9dda1-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9dda1-121">EXAMPLES</span></span>

### <span data-ttu-id="9dda1-122">Exempel 1: ta bort alla jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="9dda1-122">Example 1: Delete all job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

<span data-ttu-id="9dda1-123">Det här kommandot tar bort alla jobb utlösare från schemalagt jobb som har namn som börjar med test.</span><span class="sxs-lookup"><span data-stu-id="9dda1-123">This command deletes all job triggers from scheduled job that have names that begin with Test.</span></span>

### <span data-ttu-id="9dda1-124">Exempel 2: ta bort valda jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="9dda1-124">Example 2: Delete selected job triggers</span></span>

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

<span data-ttu-id="9dda1-125">Det här kommandot tar bara bort den tredje utlösaren (ID = 3) från det schemalagda BackupArchive-jobbet.</span><span class="sxs-lookup"><span data-stu-id="9dda1-125">This command deletes only the third trigger (ID = 3) from the BackupArchive scheduled job.</span></span>

### <span data-ttu-id="9dda1-126">Exempel 3: ta bort AtStartup jobb-utlösare från alla schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="9dda1-126">Example 3: Delete AtStartup job triggers from all scheduled jobs</span></span>

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

<span data-ttu-id="9dda1-127">Den här funktionen tar bort alla AtStartup jobb-utlösare från alla jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9dda1-127">This function deletes all AtStartup job triggers from all jobs on the local computer.</span></span>
<span data-ttu-id="9dda1-128">Om du vill använda funktionen kör du funktionen i sessionen och skriver sedan `Delete-AtStartup` .</span><span class="sxs-lookup"><span data-stu-id="9dda1-128">To use the function, run the function in your session and then type `Delete-AtStartup`.</span></span>

<span data-ttu-id="9dda1-129">Funktionen Delete-AtStartup innehåller ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="9dda1-129">The Delete-AtStartup function contains a single command.</span></span>
<span data-ttu-id="9dda1-130">Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9dda1-130">The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the local computer.</span></span>
<span data-ttu-id="9dda1-131">En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare från var och en av de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-131">A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all of the job triggers from each of the scheduled jobs.</span></span>
<span data-ttu-id="9dda1-132">En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som väljer jobb utlösare där värdet för egenskapen frekvens för jobb utlösaren är lika med AtStartup.</span><span class="sxs-lookup"><span data-stu-id="9dda1-132">A pipeline operator sends the job triggers to the Where-Object cmdlet, which selects job triggers where the value of the Frequency property of the job trigger equals AtStartup.</span></span>

<span data-ttu-id="9dda1-133">**JobTrigger** -objekt har en **jobb definitionen** -egenskap som innehåller det schemalagda jobbet som de utlöser.</span><span class="sxs-lookup"><span data-stu-id="9dda1-133">**JobTrigger** objects have a **JobDefinition** property that contains the scheduled job that they trigger.</span></span>
<span data-ttu-id="9dda1-134">Resten av kommandot använder den värdefulla funktionen.</span><span class="sxs-lookup"><span data-stu-id="9dda1-134">The remainder of the command uses that valuable feature.</span></span>

<span data-ttu-id="9dda1-135">En pipeline-operator skickar AtStartup-jobbet till ForEach-Object-cmdleten, som kör ett **Remove-JobTrigger-** kommando på varje AtStartup-utlösare.</span><span class="sxs-lookup"><span data-stu-id="9dda1-135">A pipeline operator sends the AtStartup job triggers to the ForEach-Object cmdlet, which runs a **Remove-JobTrigger** command on each AtStartup trigger.</span></span>
<span data-ttu-id="9dda1-136">Värdet för parametern *InputObject* i **Remove-JobTrigger** är det schemalagda jobbet i egenskapen jobb definitionen för jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="9dda1-136">The value of the *InputObject* parameter of **Remove-JobTrigger** is the scheduled job in the JobDefinition property of the job trigger.</span></span>
<span data-ttu-id="9dda1-137">Värdet för parametern *TriggerID* är identifieraren i jobb utlösaren ID-egenskap.</span><span class="sxs-lookup"><span data-stu-id="9dda1-137">The value of the *TriggerID* parameter is the identifier in the ID property of the job trigger.</span></span>

### <span data-ttu-id="9dda1-138">Exempel 4: ta bort en jobb utlösare från ett fjärrschemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="9dda1-138">Example 4: Delete a job trigger from a remote scheduled job</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

<span data-ttu-id="9dda1-139">Det här kommandot tar bort den första jobb utlösaren från inventerings jobbet på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="9dda1-139">This command deletes the first job trigger from the Inventory job on the Server01 computer.</span></span>

<span data-ttu-id="9dda1-140">Kommandot använder cmdleten **Invoke-Command** för att köra cmdleten **Remove-JobTrigger** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="9dda1-140">The command uses the **Invoke-Command** cmdlet to run the **Remove-JobTrigger** cmdlet on the Server01 computer.</span></span>
<span data-ttu-id="9dda1-141">Cmdlet: en **Remove-JobTrigger** använder *ID-* parametern för att identifiera det schemalagda jobbet för inventering och parametern *TriggerID* för att ange den första utlösaren.</span><span class="sxs-lookup"><span data-stu-id="9dda1-141">The **Remove-JobTrigger** cmdlet uses the *ID* parameter to identify the Inventory scheduled job and the *TriggerID* parameter to specify the first trigger.</span></span>
<span data-ttu-id="9dda1-142">*ID-* parametern är särskilt användbar när flera schemalagda jobb har samma eller liknande namn.</span><span class="sxs-lookup"><span data-stu-id="9dda1-142">The *ID* parameter is especially useful when multiple scheduled jobs have the same or similar names.</span></span>

## <span data-ttu-id="9dda1-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9dda1-143">PARAMETERS</span></span>

### <span data-ttu-id="9dda1-144">-ID</span><span class="sxs-lookup"><span data-stu-id="9dda1-144">-Id</span></span>
<span data-ttu-id="9dda1-145">Anger ID-numren för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-145">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="9dda1-146">**Remove-JobTrigger** tar bort jobb utlösare från de angivna schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-146">**Remove-JobTrigger** deletes job triggers from the specified scheduled jobs.</span></span>

<span data-ttu-id="9dda1-147">Använd Get-ScheduledJob-cmdlet för att hämta identifikations antalet schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dda1-147">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dda1-148">– InputObject</span><span class="sxs-lookup"><span data-stu-id="9dda1-148">-InputObject</span></span>
<span data-ttu-id="9dda1-149">Anger de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-149">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="9dda1-150">Ange en variabel som innehåller **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="9dda1-150">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="9dda1-151">Du kan också skicka pipe- **ScheduledJob** objekt till **Remove-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="9dda1-151">You can also pipe **ScheduledJob** objects to **Remove-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9dda1-152">-Name</span><span class="sxs-lookup"><span data-stu-id="9dda1-152">-Name</span></span>
<span data-ttu-id="9dda1-153">Anger namnen på de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-153">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="9dda1-154">**Remove-JobTrigger** tar bort jobb utlösarna från de angivna schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-154">**Remove-JobTrigger** deletes the job triggers from the specified scheduled jobs.</span></span>
<span data-ttu-id="9dda1-155">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="9dda1-155">Wildcards are supported.</span></span>

<span data-ttu-id="9dda1-156">Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9dda1-156">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dda1-157">-TriggerId</span><span class="sxs-lookup"><span data-stu-id="9dda1-157">-TriggerId</span></span>
<span data-ttu-id="9dda1-158">Tar bara bort de angivna jobb utlösarna.</span><span class="sxs-lookup"><span data-stu-id="9dda1-158">Deletes only the specified job triggers.</span></span>
<span data-ttu-id="9dda1-159">Som standard tar **Remove-JobTrigger** bort alla utlösare från de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="9dda1-159">By default, **Remove-JobTrigger** deletes all triggers from the scheduled jobs.</span></span>
<span data-ttu-id="9dda1-160">Använd den här parametern när de schemalagda jobben har flera jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="9dda1-160">Use this parameter when the scheduled jobs have multiple job triggers.</span></span>

<span data-ttu-id="9dda1-161">Ange utlösar-ID: n för en eller flera jobb utlösare för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-161">Enter the trigger IDs of one or more job triggers of a scheduled job.</span></span>
<span data-ttu-id="9dda1-162">Om du anger flera schemalagda jobb tar **Remove-JobTrigger** bort jobb utlösaren med angivet ID från alla schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="9dda1-162">If you specify multiple scheduled jobs, **Remove-JobTrigger** deletes the job trigger with the specified ID from all scheduled jobs.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9dda1-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9dda1-163">CommonParameters</span></span>
<span data-ttu-id="9dda1-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9dda1-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9dda1-165">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9dda1-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9dda1-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="9dda1-166">INPUTS</span></span>

### <span data-ttu-id="9dda1-167">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="9dda1-167">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="9dda1-168">Du kan skicka vidare schemalagda jobb till **Remove-JobTrigger-** cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="9dda1-168">You can pipe scheduled jobs to the **Remove-JobTrigger** cmdlet.</span></span>

## <span data-ttu-id="9dda1-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9dda1-169">OUTPUTS</span></span>

### <span data-ttu-id="9dda1-170">Inget</span><span class="sxs-lookup"><span data-stu-id="9dda1-170">None</span></span>
<span data-ttu-id="9dda1-171">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="9dda1-171">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9dda1-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9dda1-172">NOTES</span></span>

## <span data-ttu-id="9dda1-173">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9dda1-173">RELATED LINKS</span></span>

[<span data-ttu-id="9dda1-174">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-174">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="9dda1-175">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-175">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="9dda1-176">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-176">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="9dda1-177">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-177">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="9dda1-178">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-178">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="9dda1-179">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-179">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="9dda1-180">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-180">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="9dda1-181">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9dda1-181">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="9dda1-182">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-182">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="9dda1-183">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9dda1-183">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="9dda1-184">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-184">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="9dda1-185">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-185">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="9dda1-186">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="9dda1-186">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="9dda1-187">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-187">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="9dda1-188">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="9dda1-188">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="9dda1-189">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="9dda1-189">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
