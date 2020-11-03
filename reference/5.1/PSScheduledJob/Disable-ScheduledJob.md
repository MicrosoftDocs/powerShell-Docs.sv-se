---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264686"
---
# <span data-ttu-id="5a5ad-103">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-103">Disable-ScheduledJob</span></span>

## <span data-ttu-id="5a5ad-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5a5ad-104">SYNOPSIS</span></span>
<span data-ttu-id="5a5ad-105">Inaktiverar ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-105">Disables a scheduled job.</span></span>

## <span data-ttu-id="5a5ad-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5a5ad-106">SYNTAX</span></span>

### <span data-ttu-id="5a5ad-107">Definition (standard)</span><span class="sxs-lookup"><span data-stu-id="5a5ad-107">Definition (Default)</span></span>

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="5a5ad-108">DefinitionId</span><span class="sxs-lookup"><span data-stu-id="5a5ad-108">DefinitionId</span></span>

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5a5ad-109">DefinitionName</span><span class="sxs-lookup"><span data-stu-id="5a5ad-109">DefinitionName</span></span>

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5a5ad-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5a5ad-110">DESCRIPTION</span></span>
<span data-ttu-id="5a5ad-111">Cmdlet **: en Disable-ScheduledJob** inaktiverar tillfälligt schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-111">The **Disable-ScheduledJob** cmdlet temporarily disables scheduled jobs.</span></span>
<span data-ttu-id="5a5ad-112">Om du inaktiverar bevaras alla jobb egenskaper och jobb utlösarna inaktive ras inte, men de schemalagda jobben startas automatiskt när de utlöses.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-112">Disabling preserves all job properties and does not disable the job triggers, but it prevents the scheduled jobs from starting automatically when triggered.</span></span>
<span data-ttu-id="5a5ad-113">Du kan starta ett inaktiverat schemalagt jobb med hjälp av Start-Job-cmdlet eller använda ett inaktiverat schemalagt jobb som mall.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-113">You can start a disabled scheduled job by using the Start-Job cmdlet or use a disabled scheduled job as a template.</span></span>

<span data-ttu-id="5a5ad-114">Om du vill inaktivera ett schemalagt jobb anger cmdleten **disable-ScheduledJob** egenskapen **Enabled** för det schemalagda jobbet till falskt ($false).</span><span class="sxs-lookup"><span data-stu-id="5a5ad-114">To disable a scheduled job, the **Disable-ScheduledJob** cmdlet sets the **Enabled** property of the scheduled job to False ($false).</span></span>
<span data-ttu-id="5a5ad-115">Använd Enable-ScheduledJob-cmdleten för att återaktivera det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-115">To re-enable the scheduled job, use the Enable-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="5a5ad-116">**Disable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="5a5ad-117">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="5a5ad-118">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="5a5ad-119">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5a5ad-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5a5ad-120">EXAMPLES</span></span>

### <span data-ttu-id="5a5ad-121">Exempel 1: inaktivera ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="5a5ad-121">Example 1: Disable a scheduled job</span></span>

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

<span data-ttu-id="5a5ad-122">Detta kommando inaktiverar det schemalagda jobbet med ID 2 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-122">This command disables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="5a5ad-123">Utdata visar kommandoets effekt.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-123">The output shows the effect of the command.</span></span>

### <span data-ttu-id="5a5ad-124">Exempel 2: inaktivera alla schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="5a5ad-124">Example 2: Disable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

<span data-ttu-id="5a5ad-125">Detta kommando inaktiverar alla schemalagda jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-125">This command disables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="5a5ad-126">Den använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb och cmdleten **disable-ScheduledJob** för att inaktivera dem.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-126">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Disable-ScheduledJob** cmdlet to disable them.</span></span>

<span data-ttu-id="5a5ad-127">Du kan återaktivera schemalagt jobb genom att använda Enable-ScheduledJob-cmdlet och köra ett inaktiverat schemalagt jobb med hjälp av Start-Job-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-127">You can re-enable scheduled job by using the Enable-ScheduledJob cmdlet and run a disabled scheduled job by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="5a5ad-128">**Disable-ScheduledJob** genererar inte varningar eller fel om du inaktiverar ett schemalagt jobb som redan har inaktiverats, så att du kan inaktivera alla schemalagda jobb utan villkor.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-128">**Disable-ScheduledJob** does not generate warnings or errors if you disable a scheduled job that is already disabled, so you can disable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="5a5ad-129">Exempel 3: inaktivera valda schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="5a5ad-129">Example 3: Disable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

<span data-ttu-id="5a5ad-130">Det här kommandot inaktiverar schemalagt jobb innehåller inte någon autentiseringsuppgift.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-130">This command disables scheduled job do not include a credential.</span></span>
<span data-ttu-id="5a5ad-131">Jobb utan autentiseringsuppgifter körs med behörigheten för den användare som skapade dem.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-131">Jobs without credentials run with the permission of the user who created them.</span></span>

<span data-ttu-id="5a5ad-132">Kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-132">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="5a5ad-133">En pipeline-operator skickar schemalagda jobb till Where-Object-cmdlet, som väljer schemalagda jobb som saknar autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-133">A pipeline operator sends the scheduled jobs to the Where-Object cmdlet, which selects scheduled jobs that do not have credentials.</span></span>
<span data-ttu-id="5a5ad-134">Kommandot använder operatorn not (!) och refererar till egenskapen Credential för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-134">The command uses the not (!) operator and references the Credential property of the scheduled job.</span></span>
<span data-ttu-id="5a5ad-135">En annan pipeline-operator skickar de valda schemalagda jobben till cmdleten **disable-ScheduledJob** , vilket inaktiverar dem.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-135">Another pipeline operator sends the selected scheduled jobs to the **Disable-ScheduledJob** cmdlet, which disables them.</span></span>

### <span data-ttu-id="5a5ad-136">Exempel 4: Inaktivera schemalagda jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="5a5ad-136">Example 4: Disable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

<span data-ttu-id="5a5ad-137">Detta kommando inaktiverar det schemalagda TestJob-jobbet på två fjärranslutna datorer, SRV01 och Srv10.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-137">This command disables the TestJob scheduled job on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="5a5ad-138">Kommandot använder Invoke-Command cmdlet för att köra kommandot **disable-ScheduledJob** på datorerna SRV01 och Srv10.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-138">The command uses the Invoke-Command cmdlet to run a **Disable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="5a5ad-139">Kommandot använder *Name* -parametern för **disable-ScheduledJob** för att välja det schemalagda TestJob-jobbet på varje dator.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-139">The command uses the *Name* parameter of **Disable-ScheduledJob** to select the TestJob scheduled job on each computer.</span></span>

### <span data-ttu-id="5a5ad-140">Exempel 5: inaktivera ett schemalagt jobb med dess globala ID</span><span class="sxs-lookup"><span data-stu-id="5a5ad-140">Example 5: Disable a scheduled job by its global ID</span></span>

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

<span data-ttu-id="5a5ad-141">I det här exemplet visas hur du inaktiverar ett schemalagt jobb genom att använda dess globala identifierare.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-141">This examples shows how to disable a scheduled job by using its global identifier.</span></span>
<span data-ttu-id="5a5ad-142">Värdet för egenskapen GlobalID för ett schemalagt jobb är en unik identifierare (GUID).</span><span class="sxs-lookup"><span data-stu-id="5a5ad-142">The value of the GlobalID property of a scheduled job is a unique identifier (GUID).</span></span>
<span data-ttu-id="5a5ad-143">Använd värdet GlobalID när precision krävs, till exempel när du inaktiverar schemalagda jobb på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-143">Use the GlobalID value when precision is required, such as when you are disabling scheduled jobs on multiple computers.</span></span>

## <span data-ttu-id="5a5ad-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5a5ad-144">PARAMETERS</span></span>

### <span data-ttu-id="5a5ad-145">-ID</span><span class="sxs-lookup"><span data-stu-id="5a5ad-145">-Id</span></span>
<span data-ttu-id="5a5ad-146">Inaktiverar det schemalagda jobbet med angivet ID-nummer (ID).</span><span class="sxs-lookup"><span data-stu-id="5a5ad-146">Disables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="5a5ad-147">Ange ID för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-147">Enter the ID of a scheduled job.</span></span>

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

### <span data-ttu-id="5a5ad-148">– InputObject</span><span class="sxs-lookup"><span data-stu-id="5a5ad-148">-InputObject</span></span>
<span data-ttu-id="5a5ad-149">Anger det schemalagda jobbet som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-149">Specifies the scheduled job to be disabled.</span></span>
<span data-ttu-id="5a5ad-150">Ange en variabel som innehåller  **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-150">Enter a variable that contains  **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="5a5ad-151">Du kan också skicka ett **ScheduledJobDefinition** -objekt till **disable-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-151">You can also pipe a **ScheduledJobDefinition** object to **Disable-ScheduledJob**.</span></span>

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

### <span data-ttu-id="5a5ad-152">-Name</span><span class="sxs-lookup"><span data-stu-id="5a5ad-152">-Name</span></span>
<span data-ttu-id="5a5ad-153">Inaktiverar de schemalagda jobben med de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-153">Disables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="5a5ad-154">Ange namnet på ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-154">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="5a5ad-155">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-155">Wildcards are supported.</span></span>

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

### <span data-ttu-id="5a5ad-156">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5a5ad-156">-PassThru</span></span>
<span data-ttu-id="5a5ad-157">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-157">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5a5ad-158">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5a5ad-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5a5ad-159">-Confirm</span></span>
<span data-ttu-id="5a5ad-160">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5a5ad-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5a5ad-161">-WhatIf</span></span>
<span data-ttu-id="5a5ad-162">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5a5ad-163">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5a5ad-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5a5ad-164">CommonParameters</span></span>
<span data-ttu-id="5a5ad-165">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5a5ad-166">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5a5ad-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5a5ad-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="5a5ad-167">INPUTS</span></span>

### <span data-ttu-id="5a5ad-168">Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="5a5ad-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="5a5ad-169">Du kan skicka vidare ett schemalagt jobb för att **inaktivera-ScheduledJob**.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-169">You can pipe a scheduled job to **Disable-ScheduledJob**.</span></span>

## <span data-ttu-id="5a5ad-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5a5ad-170">OUTPUTS</span></span>

### <span data-ttu-id="5a5ad-171">Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="5a5ad-171">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="5a5ad-172">Om du använder parametern **Passthru** , **disable-ScheduledJob** returnerar det schemalagda jobbet som inaktiverades.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-172">If you use the **Passthru** parameter, **Disable-ScheduledJob** returns the scheduled job that was disabled.</span></span>
<span data-ttu-id="5a5ad-173">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5a5ad-174">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5a5ad-174">NOTES</span></span>

* <span data-ttu-id="5a5ad-175">**Disable-ScheduledJob** genererar inte varningar eller fel om du använder den för att inaktivera ett schemalagt jobb som redan har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="5a5ad-175">**Disable-ScheduledJob** does not generate warnings or errors if you use it to disable a scheduled job that is already disabled.</span></span>

## <span data-ttu-id="5a5ad-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5a5ad-176">RELATED LINKS</span></span>

[<span data-ttu-id="5a5ad-177">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-177">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="5a5ad-178">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-178">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="5a5ad-179">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-179">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="5a5ad-180">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-180">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="5a5ad-181">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-181">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="5a5ad-182">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-182">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="5a5ad-183">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-183">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="5a5ad-184">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5a5ad-184">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="5a5ad-185">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-185">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="5a5ad-186">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5a5ad-186">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="5a5ad-187">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-187">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="5a5ad-188">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-188">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="5a5ad-189">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5a5ad-189">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="5a5ad-190">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-190">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="5a5ad-191">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5a5ad-191">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="5a5ad-192">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5a5ad-192">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
