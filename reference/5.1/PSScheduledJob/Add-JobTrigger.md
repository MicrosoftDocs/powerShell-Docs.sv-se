---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264699"
---
# <span data-ttu-id="2afdc-103">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-103">Add-JobTrigger</span></span>

## <span data-ttu-id="2afdc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2afdc-104">SYNOPSIS</span></span>
<span data-ttu-id="2afdc-105">Lägger till jobb utlösare i schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2afdc-105">Adds job triggers to scheduled jobs.</span></span>

## <span data-ttu-id="2afdc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2afdc-106">SYNTAX</span></span>

### <span data-ttu-id="2afdc-107">Jobb definitionen (standard)</span><span class="sxs-lookup"><span data-stu-id="2afdc-107">JobDefinition (Default)</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### <span data-ttu-id="2afdc-108">JobDefinitionId</span><span class="sxs-lookup"><span data-stu-id="2afdc-108">JobDefinitionId</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="2afdc-109">JobDefinitionName</span><span class="sxs-lookup"><span data-stu-id="2afdc-109">JobDefinitionName</span></span>

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="2afdc-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2afdc-110">DESCRIPTION</span></span>
<span data-ttu-id="2afdc-111">Cmdleten **Add-JobTrigger** lägger till jobb utlösare i schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2afdc-111">The **Add-JobTrigger** cmdlet adds job triggers to scheduled jobs.</span></span>
<span data-ttu-id="2afdc-112">Du kan använda den för att lägga till flera utlösare till flera schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="2afdc-112">You can use it to add multiple triggers to multiple scheduled jobs.</span></span>

<span data-ttu-id="2afdc-113">En jobb utlösare startar ett schemalagt jobb vid ett engångs-eller återkommande schema eller när en händelse inträffar.</span><span class="sxs-lookup"><span data-stu-id="2afdc-113">A job trigger starts a scheduled job on a one-time or recurring schedule or when an event occurs.</span></span>

<span data-ttu-id="2afdc-114">Använd *Utlösar* -parametern för **Add-JobTrigger** för att identifiera de jobb utlösare som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="2afdc-114">Use the *Trigger* parameter of **Add-JobTrigger** to identify the job triggers to add.</span></span>
<span data-ttu-id="2afdc-115">Använd parametrarna *Name* , *ID* eller *InputObject* för **Add-JobTrigger** för att identifiera det schemalagda jobbet som utlösarna läggs till i.</span><span class="sxs-lookup"><span data-stu-id="2afdc-115">Use the *Name* , *ID* , or *InputObject* parameters of **Add-JobTrigger** to identify the scheduled job to which the triggers are added.</span></span>

<span data-ttu-id="2afdc-116">Om du vill skapa jobb utlösare för värdet för parametern *trigger* använder du New-JobTrigger cmdlet eller använder en hash-tabell för att ange jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="2afdc-116">To create job triggers for the value of the *Trigger* parameter, use the New-JobTrigger cmdlet or use a hash table to specify the job trigger.</span></span>

<span data-ttu-id="2afdc-117">**Add-JobTrigger** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2afdc-117">**Add-JobTrigger** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="2afdc-118">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="2afdc-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="2afdc-119">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="2afdc-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="2afdc-120">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2afdc-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="2afdc-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2afdc-121">EXAMPLES</span></span>

### <span data-ttu-id="2afdc-122">Exempel 1: Lägg till en jobb utlösare i ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="2afdc-122">Example 1: Add a job trigger to a scheduled job</span></span>

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

<span data-ttu-id="2afdc-123">Dessa kommandon lägger till den dagliga jobb utlösaren i det schemalagda TestJob-jobbet.</span><span class="sxs-lookup"><span data-stu-id="2afdc-123">These commands add the Daily job trigger to the TestJob scheduled job.</span></span>

<span data-ttu-id="2afdc-124">Det första kommandot använder cmdleten New-JobTrigger för att skapa en jobb utlösare som startar ett schemalagt jobb varje dag kl. 3:00 a.m.</span><span class="sxs-lookup"><span data-stu-id="2afdc-124">The first command uses the New-JobTrigger cmdlet to create a job trigger that starts a scheduled job every day at 3:00 a.m.</span></span>
<span data-ttu-id="2afdc-125">Kommandot sparar jobb utlösaren i variabeln $Daily.</span><span class="sxs-lookup"><span data-stu-id="2afdc-125">The command saves the job trigger in the $Daily variable.</span></span>

<span data-ttu-id="2afdc-126">Det andra kommandot använder cmdleten **Add-JobTrigger** för att lägga till jobb utlösaren i variabeln $Startup till det schemalagda TestJob-jobbet.</span><span class="sxs-lookup"><span data-stu-id="2afdc-126">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in the $Startup variable to the TestJob scheduled job.</span></span>

### <span data-ttu-id="2afdc-127">Exempel 2: Lägg till en jobb utlösare till flera schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="2afdc-127">Example 2: Add a job trigger to several scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

<span data-ttu-id="2afdc-128">Det här kommandot lägger till en AtStartup jobb utlösare för alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2afdc-128">This command adds an AtStartup job trigger to all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="2afdc-129">Den använder Get-ScheduledJob för att hämta alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="2afdc-129">It uses the Get-ScheduledJob to get all of the scheduled jobs on the computer.</span></span>
<span data-ttu-id="2afdc-130">Den använder en pipeline-operator (|) för att skicka jobben till cmdleten **Add-JobTrigger** , som lägger till jobb utlösaren i vart och ett av de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-130">It uses a pipeline operator (|) to send the jobs to the **Add-JobTrigger** cmdlet, which adds the job trigger to each of the scheduled jobs.</span></span>
<span data-ttu-id="2afdc-131">Värdet för *Utlösar* -parametern är ett New-JobTrigger-kommando som skapar jobb utlösaren AtStartup.</span><span class="sxs-lookup"><span data-stu-id="2afdc-131">The value of the *Trigger* parameter is a New-JobTrigger command that creates the AtStartup job trigger.</span></span>

### <span data-ttu-id="2afdc-132">Exempel 3: kopiera en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="2afdc-132">Example 3: Copy a job trigger</span></span>

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

<span data-ttu-id="2afdc-133">De här kommandona kopierar jobb utlösaren från det schemalagda BackupArchives-jobbet och lägger till det i de schemalagda jobben TestBackup och BackupLogs.</span><span class="sxs-lookup"><span data-stu-id="2afdc-133">These commands copy the job trigger from the BackupArchives scheduled job and add it to the TestBackup and BackupLogs scheduled jobs.</span></span>

<span data-ttu-id="2afdc-134">Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda BackupArchives-jobbet.</span><span class="sxs-lookup"><span data-stu-id="2afdc-134">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the BackupArchives scheduled job.</span></span>
<span data-ttu-id="2afdc-135">Kommandot sparar utlösaren i variabeln $t.</span><span class="sxs-lookup"><span data-stu-id="2afdc-135">The command saves the trigger in the $t variable.</span></span>

<span data-ttu-id="2afdc-136">Det andra kommandot använder cmdleten **Add-JobTrigger** för att lägga till jobb utlösaren i $t till de schemalagda jobben TestBackup och BackupLogs.</span><span class="sxs-lookup"><span data-stu-id="2afdc-136">The second command uses the **Add-JobTrigger** cmdlet to add the job trigger in $t to the TestBackup and BackupLogs scheduled jobs.</span></span>

## <span data-ttu-id="2afdc-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2afdc-137">PARAMETERS</span></span>

### <span data-ttu-id="2afdc-138">-ID</span><span class="sxs-lookup"><span data-stu-id="2afdc-138">-Id</span></span>
<span data-ttu-id="2afdc-139">Anger ID-numren för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-139">Specifies the identification numbers of the scheduled jobs.</span></span>
<span data-ttu-id="2afdc-140">**Add-JobTrigger** lägger till jobb utlösaren till de angivna schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-140">**Add-JobTrigger** adds the job trigger to the specified scheduled jobs.</span></span>

<span data-ttu-id="2afdc-141">Använd Get-ScheduledJob-cmdlet för att hämta identifikations antalet schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2afdc-141">To get the identification number of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="2afdc-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2afdc-142">-InputObject</span></span>
<span data-ttu-id="2afdc-143">Anger de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-143">Specifies the scheduled jobs.</span></span>
<span data-ttu-id="2afdc-144">Ange en variabel som innehåller **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="2afdc-144">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="2afdc-145">Du kan också skicka pipe- **ScheduledJob** objekt till **Add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="2afdc-145">You can also pipe **ScheduledJob** objects to **Add-JobTrigger**.</span></span>

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

### <span data-ttu-id="2afdc-146">-Name</span><span class="sxs-lookup"><span data-stu-id="2afdc-146">-Name</span></span>
<span data-ttu-id="2afdc-147">Anger namnen på de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-147">Specifies the names of the scheduled jobs.</span></span>
<span data-ttu-id="2afdc-148">**Add-JobTrigger** lägger till jobb utlösare till de angivna schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="2afdc-148">**Add-JobTrigger** adds the job triggers to the specified scheduled jobs.</span></span>
<span data-ttu-id="2afdc-149">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="2afdc-149">Wildcards are supported.</span></span>

<span data-ttu-id="2afdc-150">Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2afdc-150">To get the names of scheduled jobs on the local computer or a remote computer, use the Get-ScheduledJob cmdlet.</span></span>

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

### <span data-ttu-id="2afdc-151">– Utlös</span><span class="sxs-lookup"><span data-stu-id="2afdc-151">-Trigger</span></span>
<span data-ttu-id="2afdc-152">Anger vilka jobb utlösare som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="2afdc-152">Specifies the job triggers to add.</span></span>
<span data-ttu-id="2afdc-153">Ange en hash-tabell som anger jobb utlösare eller en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.</span><span class="sxs-lookup"><span data-stu-id="2afdc-153">Enter a hash table that specifies job triggers or a variable that contains **ScheduledJobTrigger** objects, or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="2afdc-154">Du kan också skicka pipe- **ScheduledJobTrigger** objekt till **Add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="2afdc-154">You can also pipe **ScheduledJobTrigger** objects to **Add-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2afdc-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2afdc-155">CommonParameters</span></span>
<span data-ttu-id="2afdc-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2afdc-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2afdc-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2afdc-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2afdc-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="2afdc-158">INPUTS</span></span>

### <span data-ttu-id="2afdc-159">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger, Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="2afdc-159">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger, Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="2afdc-160">Du kan skicka pipe-jobb eller schemalagda jobb till **Add-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="2afdc-160">You can pipe job triggers or scheduled jobs to **Add-JobTrigger**.</span></span>

## <span data-ttu-id="2afdc-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2afdc-161">OUTPUTS</span></span>

### <span data-ttu-id="2afdc-162">Inget</span><span class="sxs-lookup"><span data-stu-id="2afdc-162">None</span></span>
<span data-ttu-id="2afdc-163">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2afdc-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="2afdc-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2afdc-164">NOTES</span></span>

## <span data-ttu-id="2afdc-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2afdc-165">RELATED LINKS</span></span>

[<span data-ttu-id="2afdc-166">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-166">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="2afdc-167">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-167">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="2afdc-168">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-168">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="2afdc-169">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-169">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="2afdc-170">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-170">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="2afdc-171">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-171">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="2afdc-172">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-172">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="2afdc-173">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="2afdc-173">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="2afdc-174">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-174">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="2afdc-175">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="2afdc-175">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="2afdc-176">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-176">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="2afdc-177">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-177">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="2afdc-178">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="2afdc-178">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="2afdc-179">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-179">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="2afdc-180">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="2afdc-180">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="2afdc-181">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="2afdc-181">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
