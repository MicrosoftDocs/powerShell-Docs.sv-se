---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 12c44f8663017ec13ad135cc37cb076f999e3587
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709618"
---
# <span data-ttu-id="56f24-102">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="56f24-102">Debug-Job</span></span>

## <span data-ttu-id="56f24-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="56f24-103">SYNOPSIS</span></span>
<span data-ttu-id="56f24-104">Fel vid körning av ett arbets flödes jobb i bakgrunden, fjärr-eller PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56f24-104">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="56f24-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56f24-105">SYNTAX</span></span>

### <span data-ttu-id="56f24-106">JobParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="56f24-106">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56f24-107">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="56f24-107">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56f24-108">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="56f24-108">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="56f24-109">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="56f24-109">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="56f24-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="56f24-110">DESCRIPTION</span></span>
<span data-ttu-id="56f24-111">Med cmdleten **Debug-Job** kan du felsöka skript som körs i jobb.</span><span class="sxs-lookup"><span data-stu-id="56f24-111">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="56f24-112">Cmdleten är utformad för att felsöka PowerShell Workflow-jobb, bakgrunds jobb och jobb som körs i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="56f24-112">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="56f24-113">**Felsök – jobb** accepterar ett jobb objekt, namn, ID eller instans-ID som körs och startar en felsökningssession i skriptet som körs.</span><span class="sxs-lookup"><span data-stu-id="56f24-113">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="56f24-114">Fel söknings programmet **avslutar** kommandot stoppar jobbet och kör skriptet.</span><span class="sxs-lookup"><span data-stu-id="56f24-114">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="56f24-115">Från och med Windows PowerShell 5,0 kopplar kommandot **exit** bort fel söknings programmet och tillåter att jobbet fortsätter att köras.</span><span class="sxs-lookup"><span data-stu-id="56f24-115">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="56f24-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="56f24-116">EXAMPLES</span></span>

### <span data-ttu-id="56f24-117">Exempel 1: Felsöka ett jobb efter jobb-ID</span><span class="sxs-lookup"><span data-stu-id="56f24-117">Example 1: Debug a job by job ID</span></span>

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

<span data-ttu-id="56f24-118">Det här kommandot delar in i ett jobb som körs med ID 3.</span><span class="sxs-lookup"><span data-stu-id="56f24-118">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="56f24-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="56f24-119">PARAMETERS</span></span>

### <span data-ttu-id="56f24-120">-ID</span><span class="sxs-lookup"><span data-stu-id="56f24-120">-Id</span></span>
<span data-ttu-id="56f24-121">Anger ID-numret för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="56f24-121">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="56f24-122">Kör cmdleten Get-Job om du vill hämta ID-numret för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="56f24-122">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56f24-123">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="56f24-123">-InstanceId</span></span>
<span data-ttu-id="56f24-124">Anger instans-ID-GUID för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="56f24-124">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="56f24-125">Om du vill ta reda på ett jobbs *InstanceID* kör du cmdleten **Get-Job** , översätter resultaten till en **format-_-** cmdlet, som visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="56f24-125">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** _ cmdlet, as shown in the following example:</span></span>

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56f24-126">– Jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-126">-Job</span></span>
<span data-ttu-id="56f24-127">Anger ett jobb objekt som körs.</span><span class="sxs-lookup"><span data-stu-id="56f24-127">Specifies a running job object.</span></span>
<span data-ttu-id="56f24-128">Det enklaste sättet att använda den här parametern är att spara resultatet av ett _ \*Get-Job *-* kommando som returnerar det jobb som du vill felsöka i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="56f24-128">The simplest way to use this parameter is to save the results of a _ *Get-Job*\* command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="56f24-129">-Name</span><span class="sxs-lookup"><span data-stu-id="56f24-129">-Name</span></span>
<span data-ttu-id="56f24-130">Anger ett jobb efter det egna namnet på jobbet.</span><span class="sxs-lookup"><span data-stu-id="56f24-130">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="56f24-131">När du startar ett jobb kan du ange ett jobb namn genom att lägga till parametern *JobName* i cmdlets som Invoke-Command och start jobb.</span><span class="sxs-lookup"><span data-stu-id="56f24-131">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="56f24-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="56f24-132">-Confirm</span></span>
<span data-ttu-id="56f24-133">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="56f24-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="56f24-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="56f24-134">-WhatIf</span></span>
<span data-ttu-id="56f24-135">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="56f24-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="56f24-136">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="56f24-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="56f24-137">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="56f24-137">-BreakAll</span></span>

<span data-ttu-id="56f24-138">{{Fill BreakAll-Beskrivning}}</span><span class="sxs-lookup"><span data-stu-id="56f24-138">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="56f24-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="56f24-139">CommonParameters</span></span>
<span data-ttu-id="56f24-140">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="56f24-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="56f24-141">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="56f24-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="56f24-142">INDATA</span><span class="sxs-lookup"><span data-stu-id="56f24-142">INPUTS</span></span>

### <span data-ttu-id="56f24-143">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="56f24-143">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="56f24-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="56f24-144">OUTPUTS</span></span>

## <span data-ttu-id="56f24-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="56f24-145">NOTES</span></span>

## <span data-ttu-id="56f24-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="56f24-146">RELATED LINKS</span></span>

[<span data-ttu-id="56f24-147">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-147">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="56f24-148">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-148">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="56f24-149">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-149">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="56f24-150">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-150">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="56f24-151">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="56f24-151">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="56f24-152">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="56f24-152">Wait-Job</span></span>](Wait-Job.md)

