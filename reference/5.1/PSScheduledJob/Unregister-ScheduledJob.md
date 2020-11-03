---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264608"
---
# <span data-ttu-id="66cf1-103">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-103">Unregister-ScheduledJob</span></span>

## <span data-ttu-id="66cf1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="66cf1-104">SYNOPSIS</span></span>
<span data-ttu-id="66cf1-105">Tar bort schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-105">Deletes scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="66cf1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="66cf1-106">SYNTAX</span></span>

### <span data-ttu-id="66cf1-107">Definition (standard)</span><span class="sxs-lookup"><span data-stu-id="66cf1-107">Definition (Default)</span></span>

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="66cf1-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="66cf1-108">DefinitionId</span></span>

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="66cf1-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="66cf1-109">DefinitionName</span></span>

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="66cf1-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="66cf1-110">DESCRIPTION</span></span>
<span data-ttu-id="66cf1-111">**Unregister-ScheduledJob-cmdlet:** en tar bort schemalagda jobb från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-111">The **Unregister-ScheduledJob** cmdlet deletes scheduled jobs from the local computer.</span></span>

<span data-ttu-id="66cf1-112">När ett schemalagt jobb tas bort eller avregistreras, tar **unregister-ScheduledJob** bort katalogen för det schemalagda jobbet (i katalogen $Home \appdata\local\microsoft\windows\powershell\scheduledjobs), som innehåller XML-filen som definierar det schemalagda jobbet, jobb körnings historiken och alla jobb resultat.</span><span class="sxs-lookup"><span data-stu-id="66cf1-112">When it deletes or unregisters a scheduled job, **Unregister-ScheduledJob** deletes the directory for the scheduled job (in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory), which contains the XML file that defines the scheduled job, the job execution history, and all job results.</span></span>
<span data-ttu-id="66cf1-113">Med den här åtgärden tas även jobbet bort från Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="66cf1-113">This action also deletes the job from Task Scheduler.</span></span>

<span data-ttu-id="66cf1-114">**Unregister-ScheduledJob** tar bara bort de schemalagda jobb som skapats med hjälp av Register-ScheduledJob-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="66cf1-114">**Unregister-ScheduledJob** deletes only the scheduled jobs that are created by using the Register-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="66cf1-115">Schemalagda jobb tas inte bort som skapas i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="66cf1-115">It does not delete scheduled jobs that are created in Task Scheduler.</span></span>

<span data-ttu-id="66cf1-116">Du kan använda parametrarna **unregister-ScheduledJob** för att ta bort schemalagda jobb efter ID eller namn, eller skicka en pipe schemalagda jobb från Get-ScheduledJob till **unregister-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="66cf1-116">You can use the parameters of **Unregister-ScheduledJob** to delete scheduled jobs by ID or name, or pipe scheduled jobs from Get-ScheduledJob to **Unregister-ScheduledJob**.</span></span>

<span data-ttu-id="66cf1-117">**Unregister-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66cf1-117">**Unregister-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="66cf1-118">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="66cf1-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="66cf1-119">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="66cf1-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="66cf1-120">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="66cf1-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="66cf1-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="66cf1-121">EXAMPLES</span></span>

### <span data-ttu-id="66cf1-122">Exempel 1: ta bort ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="66cf1-122">Example 1: Delete a scheduled job</span></span>

```
PS C:\> Unregister-ScheduledJob TestJob
```

<span data-ttu-id="66cf1-123">Det här kommandot tar bort det schemalagda TestJob-jobbet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-123">This command deletes the TestJob scheduled job on the local computer.</span></span>

### <span data-ttu-id="66cf1-124">Exempel 2: ta bort alla schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="66cf1-124">Example 2: Delete all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

<span data-ttu-id="66cf1-125">I det här exemplet visas två olika kommandon som tar bort alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-125">This example shows two different commands that delete all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="66cf1-126">Det första kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-126">The first command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="66cf1-127">En pipeline-operator (|) skickar de schemalagda jobben till **unregister-ScheduleJob** , som tar bort dem.</span><span class="sxs-lookup"><span data-stu-id="66cf1-127">A pipeline operator (|) sends the scheduled jobs to **Unregister-ScheduleJob** , which deletes them.</span></span>

<span data-ttu-id="66cf1-128">Det andra kommandot använder parametern *Name* i **unregister-ScheduledJob** med värdet alla (\*) för att ta bort alla schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="66cf1-128">The second command uses the *Name* parameter of **Unregister-ScheduledJob** with a value of all (\*) to delete all scheduled jobs.</span></span>

<span data-ttu-id="66cf1-129">Båda kommandona använder *Force* -parametern, som tar bort ett schemalagt jobb även om en instans av jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="66cf1-129">Both commands use the *Force* parameter, which deletes a scheduled job even if an instance of the job is running.</span></span>

### <span data-ttu-id="66cf1-130">Exempel 3: ta bort ett schemalagt jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="66cf1-130">Example 3: Delete a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

<span data-ttu-id="66cf1-131">Det här kommandot tar bort schemalagda jobb med namn som börjar med test på den fjärranslutna Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-131">This command deletes scheduled jobs with names that begin with Test on the Server01 remote computer.</span></span>
<span data-ttu-id="66cf1-132">Kommandot använder Invoke-Command-cmdlet för att köra kommandot **unregister-ScheduledJob** på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-132">The command uses the Invoke-Command cmdlet to run the **Unregister-ScheduledJob** command on the Server02 computer.</span></span>

## <span data-ttu-id="66cf1-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="66cf1-133">PARAMETERS</span></span>

### <span data-ttu-id="66cf1-134">-Force</span><span class="sxs-lookup"><span data-stu-id="66cf1-134">-Force</span></span>
<span data-ttu-id="66cf1-135">Tar bort det schemalagda jobbet även om en instans av jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="66cf1-135">Deletes the scheduled job even if an instance of the job is running.</span></span>
<span data-ttu-id="66cf1-136">**Avregistrering-ScheduledJob** avbryter som standard inte jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="66cf1-136">By default, **Unregister-ScheduledJob** does not interrupt running jobs.</span></span>

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

### <span data-ttu-id="66cf1-137">-ID</span><span class="sxs-lookup"><span data-stu-id="66cf1-137">-Id</span></span>
<span data-ttu-id="66cf1-138">Tar bort de schemalagda jobben med angivet ID-nummer (ID).</span><span class="sxs-lookup"><span data-stu-id="66cf1-138">Deletes the scheduled jobs with the specified identification numbers (ID).</span></span>
<span data-ttu-id="66cf1-139">Ange ID: na för schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-139">Enter the IDs of scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="66cf1-140">– InputObject</span><span class="sxs-lookup"><span data-stu-id="66cf1-140">-InputObject</span></span>
<span data-ttu-id="66cf1-141">Anger ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="66cf1-141">Specifies a scheduled job.</span></span>
<span data-ttu-id="66cf1-142">Ange en variabel som innehåller **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="66cf1-142">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="66cf1-143">Du kan också skicka pipe- **ScheduledJob** objekt för att **avregistrera-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="66cf1-143">You can also pipe **ScheduledJob** objects to **Unregister-JobTrigger**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="66cf1-144">-Name</span><span class="sxs-lookup"><span data-stu-id="66cf1-144">-Name</span></span>
<span data-ttu-id="66cf1-145">Tar bort de schemalagda jobben med de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="66cf1-145">Deletes the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="66cf1-146">Ange namnen på en eller flera schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="66cf1-146">Enter the names of one or more scheduled jobs on the computer.</span></span>
<span data-ttu-id="66cf1-147">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="66cf1-147">Wildcards are supported.</span></span>

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

### <span data-ttu-id="66cf1-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="66cf1-148">-Confirm</span></span>
<span data-ttu-id="66cf1-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="66cf1-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="66cf1-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="66cf1-150">-WhatIf</span></span>
<span data-ttu-id="66cf1-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="66cf1-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="66cf1-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="66cf1-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="66cf1-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="66cf1-153">CommonParameters</span></span>
<span data-ttu-id="66cf1-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="66cf1-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="66cf1-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="66cf1-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="66cf1-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="66cf1-156">INPUTS</span></span>

### <span data-ttu-id="66cf1-157">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="66cf1-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="66cf1-158">Du kan skicka vidare schemalagda jobb till Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-158">You can pipe scheduled jobs to Unregister-ScheduledJob</span></span>

## <span data-ttu-id="66cf1-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="66cf1-159">OUTPUTS</span></span>

### <span data-ttu-id="66cf1-160">Inget</span><span class="sxs-lookup"><span data-stu-id="66cf1-160">None</span></span>
<span data-ttu-id="66cf1-161">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="66cf1-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="66cf1-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="66cf1-162">NOTES</span></span>

## <span data-ttu-id="66cf1-163">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="66cf1-163">RELATED LINKS</span></span>

[<span data-ttu-id="66cf1-164">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-164">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="66cf1-165">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-165">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="66cf1-166">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-166">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="66cf1-167">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-167">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="66cf1-168">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-168">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="66cf1-169">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-169">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="66cf1-170">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-170">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="66cf1-171">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="66cf1-171">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="66cf1-172">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-172">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="66cf1-173">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="66cf1-173">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="66cf1-174">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-174">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="66cf1-175">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-175">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="66cf1-176">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="66cf1-176">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="66cf1-177">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-177">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="66cf1-178">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="66cf1-178">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="66cf1-179">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="66cf1-179">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
