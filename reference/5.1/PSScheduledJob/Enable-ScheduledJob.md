---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264663"
---
# <span data-ttu-id="c219b-103">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-103">Enable-ScheduledJob</span></span>

## <span data-ttu-id="c219b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c219b-104">SYNOPSIS</span></span>
<span data-ttu-id="c219b-105">Aktiverar ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="c219b-105">Enables a scheduled job.</span></span>

## <span data-ttu-id="c219b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c219b-106">SYNTAX</span></span>

### <span data-ttu-id="c219b-107">Definition (standard)</span><span class="sxs-lookup"><span data-stu-id="c219b-107">Definition (Default)</span></span>

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="c219b-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="c219b-108">DefinitionId</span></span>

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c219b-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="c219b-109">DefinitionName</span></span>

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c219b-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c219b-110">DESCRIPTION</span></span>
<span data-ttu-id="c219b-111">Cmdlet: en **Enable-ScheduledJob** aktiverar schemalagda jobb som är inaktiverade, till exempel de som har inaktiverats med hjälp av Disable-ScheduledJob-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c219b-111">The **Enable-ScheduledJob** cmdlet re-enables scheduled jobs that are disabled, such as those that are disabled by using the Disable-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="c219b-112">Aktiverade jobb körs automatiskt när de utlöses.</span><span class="sxs-lookup"><span data-stu-id="c219b-112">Enabled jobs run automatically when triggered.</span></span>

<span data-ttu-id="c219b-113">Om du vill aktivera ett schemalagt jobb anger cmdleten **Enable-ScheduledJob** egenskapen Enabled för det schemalagda jobbet till $true.</span><span class="sxs-lookup"><span data-stu-id="c219b-113">To enable a scheduled job, the **Enable-ScheduledJob** cmdlet sets the Enabled property of the scheduled job to $True.</span></span>

<span data-ttu-id="c219b-114">**Enabled-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c219b-114">**Enabled-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="c219b-115">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="c219b-115">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="c219b-116">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="c219b-116">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="c219b-117">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c219b-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="c219b-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c219b-118">EXAMPLES</span></span>

### <span data-ttu-id="c219b-119">Exempel 1: aktivera ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="c219b-119">Example 1: Enable a scheduled job</span></span>

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

<span data-ttu-id="c219b-120">Det här kommandot aktiverar det schemalagda jobbet med ID 2 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c219b-120">This command enables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="c219b-121">Utdata visar kommandoets effekt.</span><span class="sxs-lookup"><span data-stu-id="c219b-121">The output shows the effect of the command.</span></span>

### <span data-ttu-id="c219b-122">Exempel 2: Aktivera alla schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="c219b-122">Example 2: Enable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

<span data-ttu-id="c219b-123">Detta kommando aktiverar alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c219b-123">This command enables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="c219b-124">Den använder Get-ScheduledJob-cmdlet för att hämta allt schemalagt jobb och cmdleten **Enable-ScheduledJob** för att aktivera dem.</span><span class="sxs-lookup"><span data-stu-id="c219b-124">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Enable-ScheduledJob** cmdlet to enable them.</span></span>

<span data-ttu-id="c219b-125">**Enable-ScheduledJob** genererar inte varningar eller fel om du aktiverar ett schemalagt jobb som redan har Aktiver ATS, så att du kan aktivera alla schemalagda jobb utan villkor.</span><span class="sxs-lookup"><span data-stu-id="c219b-125">**Enable-ScheduledJob** does not generate warnings or errors if you enable a scheduled job that is already enabled, so you can enable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="c219b-126">Exempel 3: Aktivera valda schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="c219b-126">Example 3: Enable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

<span data-ttu-id="c219b-127">Det här kommandot aktiverar schemalagda jobb som inte kräver någon nätverks anslutning.</span><span class="sxs-lookup"><span data-stu-id="c219b-127">This command enables scheduled jobs that do not require a network connection.</span></span>

<span data-ttu-id="c219b-128">Kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="c219b-128">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="c219b-129">En pipeline-operator skickar schemalagda jobb till Get-ScheduledJobOption-cmdlet, som hämtar jobb alternativen för varje schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="c219b-129">A pipeline operator sends the scheduled jobs to the Get-ScheduledJobOption cmdlet, which gets the job options of each scheduled job.</span></span>
<span data-ttu-id="c219b-130">Varje jobb alternativ objekt har en jobb definitionen-egenskap som innehåller det associerade schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="c219b-130">Each job options object has a JobDefinition property that contains the associated scheduled job.</span></span>
<span data-ttu-id="c219b-131">Egenskapen jobb definitionen används för att slutföra kommandot.</span><span class="sxs-lookup"><span data-stu-id="c219b-131">The JobDefinition property is used to complete the command.</span></span>

<span data-ttu-id="c219b-132">Kommandot använder en pipeline-operator (|) för att skicka jobb alternativen till Where-Object-cmdleten, som väljer alternativ för schemalagda jobb där egenskapen **RunWithoutNetwork** har värdet True ($true).</span><span class="sxs-lookup"><span data-stu-id="c219b-132">The command uses a pipeline operator (|) to send the job options to the Where-Object cmdlet, which selects scheduled job option objects in which the **RunWithoutNetwork** property has a value of True ($true).</span></span>
<span data-ttu-id="c219b-133">En annan pipeline-operator skickar de valda alternativen för schemalagda jobb till ForEach-Object-cmdleten som kör ett **Enable-ScheduledJob-** kommando på det schemalagda jobbet i värdet för egenskapen jobb definitionen för varje jobb alternativ objekt.</span><span class="sxs-lookup"><span data-stu-id="c219b-133">Another pipeline operator sends the selected scheduled job options objects to the ForEach-Object cmdlet which runs an **Enable-ScheduledJob** command on the scheduled job in the value of the JobDefinition property of each job options object.</span></span>

### <span data-ttu-id="c219b-134">Exempel 4: Aktivera schemalagda jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="c219b-134">Example 4: Enable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

<span data-ttu-id="c219b-135">Det här kommandot aktiverar schemalagda jobb som har "test" i sina namn på två fjärrdatorer, SRV01 och Srv10.</span><span class="sxs-lookup"><span data-stu-id="c219b-135">This command enables scheduled jobs that have "test" in their names on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="c219b-136">Kommandot använder Invoke-Command cmdlet för att köra kommandot **Enable-ScheduledJob** på datorerna SRV01 och Srv10.</span><span class="sxs-lookup"><span data-stu-id="c219b-136">The command uses the Invoke-Command cmdlet to run an **Enable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="c219b-137">Kommandot använder *Name* -parametern för **Enable-ScheduledJob** för att aktivera det schemalagda inventerings jobbet på varje dator.</span><span class="sxs-lookup"><span data-stu-id="c219b-137">The command uses the *Name* parameter of **Enable-ScheduledJob** to enable the Inventory scheduled job on each computer.</span></span>

## <span data-ttu-id="c219b-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c219b-138">PARAMETERS</span></span>

### <span data-ttu-id="c219b-139">-ID</span><span class="sxs-lookup"><span data-stu-id="c219b-139">-Id</span></span>
<span data-ttu-id="c219b-140">Aktiverar det schemalagda jobbet med angivet ID-nummer (ID).</span><span class="sxs-lookup"><span data-stu-id="c219b-140">Enables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="c219b-141">Ange ID för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="c219b-141">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c219b-142">– InputObject</span><span class="sxs-lookup"><span data-stu-id="c219b-142">-InputObject</span></span>
<span data-ttu-id="c219b-143">Anger det schemalagda jobbet som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="c219b-143">Specifies the scheduled job to enable.</span></span>
<span data-ttu-id="c219b-144">Ange en variabel som innehåller **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="c219b-144">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="c219b-145">Du kan också skicka ett **ScheduledJobDefinition** -objekt för att **Aktivera-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="c219b-145">You can also pipe a **ScheduledJobDefinition** object to **Enable-ScheduledJob**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c219b-146">-Name</span><span class="sxs-lookup"><span data-stu-id="c219b-146">-Name</span></span>
<span data-ttu-id="c219b-147">Aktiverar de schemalagda jobben med de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="c219b-147">Enables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="c219b-148">Ange namnet på ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="c219b-148">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="c219b-149">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="c219b-149">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c219b-150">– PassThru</span><span class="sxs-lookup"><span data-stu-id="c219b-150">-PassThru</span></span>
<span data-ttu-id="c219b-151">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="c219b-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="c219b-152">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c219b-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c219b-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c219b-153">-Confirm</span></span>
<span data-ttu-id="c219b-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c219b-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c219b-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c219b-155">-WhatIf</span></span>
<span data-ttu-id="c219b-156">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="c219b-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="c219b-157">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c219b-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c219b-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c219b-158">CommonParameters</span></span>
<span data-ttu-id="c219b-159">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c219b-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c219b-160">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c219b-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c219b-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="c219b-161">INPUTS</span></span>

### <span data-ttu-id="c219b-162">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="c219b-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="c219b-163">Du kan skicka vidare ett schemalagt jobb till **Enable-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="c219b-163">You can pipe a scheduled job to **Enable-ScheduledJob**.</span></span>

## <span data-ttu-id="c219b-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c219b-164">OUTPUTS</span></span>

### <span data-ttu-id="c219b-165">Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="c219b-165">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="c219b-166">Om du använder parametern **Passthru** returnerar **Enable-ScheduledJob** det schemalagda jobbet som har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="c219b-166">If you use the **Passthru** parameter, **Enable-ScheduledJob** returns the scheduled job that was enabled.</span></span>
<span data-ttu-id="c219b-167">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c219b-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="c219b-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c219b-168">NOTES</span></span>

* <span data-ttu-id="c219b-169">**Enable-ScheduledJob** genererar inte varningar eller fel om du använder den för att aktivera ett schemalagt jobb som redan har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="c219b-169">**Enable-ScheduledJob** does not generate warnings or errors if you use it to enable a scheduled job that is already enabled.</span></span>

## <span data-ttu-id="c219b-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c219b-170">RELATED LINKS</span></span>

[<span data-ttu-id="c219b-171">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-171">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="c219b-172">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-172">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="c219b-173">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-173">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="c219b-174">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-174">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="c219b-175">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-175">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="c219b-176">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-176">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="c219b-177">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-177">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="c219b-178">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c219b-178">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="c219b-179">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-179">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="c219b-180">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c219b-180">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="c219b-181">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-181">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="c219b-182">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-182">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="c219b-183">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="c219b-183">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="c219b-184">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-184">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="c219b-185">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="c219b-185">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="c219b-186">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="c219b-186">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
