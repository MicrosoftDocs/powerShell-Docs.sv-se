---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 312e3b9900a67e294ec5052cb05b4ee989d4c3ad
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265863"
---
# <span data-ttu-id="65871-103">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="65871-103">Debug-Job</span></span>

## <span data-ttu-id="65871-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="65871-104">SYNOPSIS</span></span>
<span data-ttu-id="65871-105">Fel vid körning av ett arbets flödes jobb i bakgrunden, fjärr-eller PowerShell.</span><span class="sxs-lookup"><span data-stu-id="65871-105">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="65871-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="65871-106">SYNTAX</span></span>

### <span data-ttu-id="65871-107">JobParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="65871-107">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="65871-108">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="65871-108">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="65871-109">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="65871-109">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="65871-110">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="65871-110">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="65871-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="65871-111">DESCRIPTION</span></span>
<span data-ttu-id="65871-112">Med cmdleten **Debug-Job** kan du felsöka skript som körs i jobb.</span><span class="sxs-lookup"><span data-stu-id="65871-112">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="65871-113">Cmdleten är utformad för att felsöka PowerShell Workflow-jobb, bakgrunds jobb och jobb som körs i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="65871-113">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="65871-114">**Felsök – jobb** accepterar ett jobb objekt, namn, ID eller instans-ID som körs och startar en felsökningssession i skriptet som körs.</span><span class="sxs-lookup"><span data-stu-id="65871-114">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="65871-115">Fel söknings programmet **avslutar** kommandot stoppar jobbet och kör skriptet.</span><span class="sxs-lookup"><span data-stu-id="65871-115">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="65871-116">Från och med Windows PowerShell 5,0 kopplar kommandot **exit** bort fel söknings programmet och tillåter att jobbet fortsätter att köras.</span><span class="sxs-lookup"><span data-stu-id="65871-116">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="65871-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="65871-117">EXAMPLES</span></span>

### <span data-ttu-id="65871-118">Exempel 1: Felsöka ett jobb efter jobb-ID</span><span class="sxs-lookup"><span data-stu-id="65871-118">Example 1: Debug a job by job ID</span></span>

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

<span data-ttu-id="65871-119">Det här kommandot delar in i ett jobb som körs med ID 3.</span><span class="sxs-lookup"><span data-stu-id="65871-119">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="65871-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="65871-120">PARAMETERS</span></span>

### <span data-ttu-id="65871-121">-ID</span><span class="sxs-lookup"><span data-stu-id="65871-121">-Id</span></span>
<span data-ttu-id="65871-122">Anger ID-numret för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="65871-122">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="65871-123">Kör cmdleten Get-Job om du vill hämta ID-numret för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="65871-123">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

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

### <span data-ttu-id="65871-124">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="65871-124">-InstanceId</span></span>
<span data-ttu-id="65871-125">Anger instans-ID-GUID för ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="65871-125">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="65871-126">Om du vill ta *reda på ett jobb med* hjälp av cmdleten **Get-Job** kan du skicka resultatet till en **format-\*-** cmdlet, som visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="65871-126">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** \* cmdlet, as shown in the following example:</span></span>

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

### <span data-ttu-id="65871-127">– Jobb</span><span class="sxs-lookup"><span data-stu-id="65871-127">-Job</span></span>
<span data-ttu-id="65871-128">Anger ett jobb objekt som körs.</span><span class="sxs-lookup"><span data-stu-id="65871-128">Specifies a running job object.</span></span>
<span data-ttu-id="65871-129">Det enklaste sättet att använda den här parametern är att spara resultatet av ett **Get-Job-** kommando som returnerar det jobb som du vill felsöka i en variabel och sedan ange variabeln som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="65871-129">The simplest way to use this parameter is to save the results of a **Get-Job** command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="65871-130">-Name</span><span class="sxs-lookup"><span data-stu-id="65871-130">-Name</span></span>
<span data-ttu-id="65871-131">Anger ett jobb efter det egna namnet på jobbet.</span><span class="sxs-lookup"><span data-stu-id="65871-131">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="65871-132">När du startar ett jobb kan du ange ett jobb namn genom att lägga till parametern *JobName* i cmdlets som Invoke-Command och start jobb.</span><span class="sxs-lookup"><span data-stu-id="65871-132">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

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

### <span data-ttu-id="65871-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="65871-133">-Confirm</span></span>
<span data-ttu-id="65871-134">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="65871-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="65871-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="65871-135">-WhatIf</span></span>
<span data-ttu-id="65871-136">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="65871-136">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="65871-137">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="65871-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="65871-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="65871-138">CommonParameters</span></span>
<span data-ttu-id="65871-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="65871-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="65871-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="65871-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="65871-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="65871-141">INPUTS</span></span>

### <span data-ttu-id="65871-142">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="65871-142">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="65871-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="65871-143">OUTPUTS</span></span>

## <span data-ttu-id="65871-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="65871-144">NOTES</span></span>

## <span data-ttu-id="65871-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="65871-145">RELATED LINKS</span></span>

[<span data-ttu-id="65871-146">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="65871-146">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="65871-147">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="65871-147">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="65871-148">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="65871-148">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="65871-149">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="65871-149">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="65871-150">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="65871-150">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="65871-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="65871-151">Wait-Job</span></span>](Wait-Job.md)
