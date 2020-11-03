---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265563"
---
# <span data-ttu-id="98832-103">Limit-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-103">Limit-EventLog</span></span>

## <span data-ttu-id="98832-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="98832-104">SYNOPSIS</span></span>
<span data-ttu-id="98832-105">Anger egenskaperna för händelse loggen som begränsar storleken på händelse loggen och ålder på dess poster.</span><span class="sxs-lookup"><span data-stu-id="98832-105">Sets the event log properties that limit the size of the event log and the age of its entries.</span></span>

## <span data-ttu-id="98832-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="98832-106">SYNTAX</span></span>

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="98832-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="98832-107">DESCRIPTION</span></span>
<span data-ttu-id="98832-108">Cmdleten **Limit-EventLog** anger den maximala storleken för en klassisk händelse logg, hur länge varje händelse måste behållas och vad som händer när loggen når sin maximala storlek.</span><span class="sxs-lookup"><span data-stu-id="98832-108">The **Limit-EventLog** cmdlet sets the maximum size of a classic event log, how long each event must be retained, and what happens when the log reaches its maximum size.</span></span>
<span data-ttu-id="98832-109">Du kan använda den för att begränsa händelse loggarna på lokala eller fjärranslutna datorer.</span><span class="sxs-lookup"><span data-stu-id="98832-109">You can use it to limit the event logs on local or remote computers.</span></span>

<span data-ttu-id="98832-110">De cmdletar som innehåller EventLog-händelsen Substantiv (EventLog-cmdletar) fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="98832-110">The cmdlets that contain the EventLog noun (the EventLog cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="98832-111">Använd Get-WinEvent för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="98832-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use Get-WinEvent.</span></span>

## <span data-ttu-id="98832-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="98832-112">EXAMPLES</span></span>

### <span data-ttu-id="98832-113">Exempel 1: öka storleken på en händelse logg</span><span class="sxs-lookup"><span data-stu-id="98832-113">Example 1: Increase the size of an event log</span></span>

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

<span data-ttu-id="98832-114">Det här kommandot ökar den maximala storleken för Windows PowerShell-händelseloggen på den lokala datorn till 20480 byte (20 KB).</span><span class="sxs-lookup"><span data-stu-id="98832-114">This command increases the maximum size of the Windows PowerShell event log on the local computer to 20480 bytes (20 KB).</span></span>

### <span data-ttu-id="98832-115">Exempel 2: Behåll en händelse logg under en angiven varaktighet</span><span class="sxs-lookup"><span data-stu-id="98832-115">Example 2: Retain an event log for a specified duration</span></span>

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

<span data-ttu-id="98832-116">Det här kommandot säkerställer att händelser i säkerhets loggen på Server01-och Server02-datorerna bevaras i minst 7 dagar.</span><span class="sxs-lookup"><span data-stu-id="98832-116">This command ensures that events in the Security log on the Server01 and Server02 computers are retained for at least 7 days.</span></span>

### <span data-ttu-id="98832-117">Exempel 3: ändra overflow-åtgärden för alla händelse loggar</span><span class="sxs-lookup"><span data-stu-id="98832-117">Example 3: Change the overflow action of all event logs</span></span>

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

<span data-ttu-id="98832-118">Det här exemplet ändrar overflow-åtgärden för alla händelse loggar på den lokala datorn till OverwriteOlder.</span><span class="sxs-lookup"><span data-stu-id="98832-118">This example changes the overflow action of all event logs on the local computer to OverwriteOlder.</span></span>

<span data-ttu-id="98832-119">Det första kommandot hämtar logg namnen för alla loggar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="98832-119">The first command gets the log names of all of the logs on the local computer.</span></span>
<span data-ttu-id="98832-120">Det andra kommandot anger spill åtgärden.</span><span class="sxs-lookup"><span data-stu-id="98832-120">The second command sets the overflow action.</span></span>
<span data-ttu-id="98832-121">Det tredje kommandot visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="98832-121">The third command displays the results.</span></span>

## <span data-ttu-id="98832-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="98832-122">PARAMETERS</span></span>

### <span data-ttu-id="98832-123">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="98832-123">-ComputerName</span></span>
<span data-ttu-id="98832-124">Anger fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="98832-124">Specifies remote computers.</span></span>
<span data-ttu-id="98832-125">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="98832-125">The default is the local computer.</span></span>

<span data-ttu-id="98832-126">Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="98832-126">Type the NetBIOS name, an Internet Protocol (IP) address, or a fully qualified domain name (FQDN) of a remote computer.</span></span>
<span data-ttu-id="98832-127">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="98832-127">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="98832-128">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="98832-128">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="98832-129">Du kan använda parametern *computername* för **Limit-EventLog** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="98832-129">You can use the *ComputerName* parameter of **Limit-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98832-130">-LogName</span><span class="sxs-lookup"><span data-stu-id="98832-130">-LogName</span></span>
<span data-ttu-id="98832-131">Anger händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="98832-131">Specifies the event logs.</span></span>
<span data-ttu-id="98832-132">Ange logg namnet (värdet för logg egenskapen, inte LogDisplayName) för en eller flera händelse loggar, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="98832-132">Enter the log name (the value of the Log property; not the LogDisplayName) of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="98832-133">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="98832-133">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="98832-134">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="98832-134">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98832-135">-Högsta</span><span class="sxs-lookup"><span data-stu-id="98832-135">-MaximumSize</span></span>
<span data-ttu-id="98832-136">Anger den maximala storleken på händelse loggarna i byte.</span><span class="sxs-lookup"><span data-stu-id="98832-136">Specifies the maximum size of the event logs in bytes.</span></span>
<span data-ttu-id="98832-137">Ange ett värde mellan 64 KB (KB) och 4 GB.</span><span class="sxs-lookup"><span data-stu-id="98832-137">Enter a value between 64 kilobytes (KB) and 4 gigabytes (GB).</span></span>
<span data-ttu-id="98832-138">Värdet måste vara delbar med 64 KB (65536).</span><span class="sxs-lookup"><span data-stu-id="98832-138">The value must be divisible by 64 KB (65536).</span></span>

<span data-ttu-id="98832-139">Den här parametern anger värdet för egenskapen **MaximumKilobytes** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="98832-139">This parameter specifies the value of the **MaximumKilobytes** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98832-140">-OverflowAction</span><span class="sxs-lookup"><span data-stu-id="98832-140">-OverflowAction</span></span>
<span data-ttu-id="98832-141">Anger vad som händer när händelse loggen når den maximala storleken.</span><span class="sxs-lookup"><span data-stu-id="98832-141">Specifies what happens when the event log reaches its maximum size.</span></span>

<span data-ttu-id="98832-142">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="98832-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="98832-143">DoNotOverwrite: befintliga poster bevaras och nya poster tas bort.</span><span class="sxs-lookup"><span data-stu-id="98832-143">DoNotOverwrite:  Existing entries are retained and new entries are discarded.</span></span>
- <span data-ttu-id="98832-144">OverwriteAsNeeded: varje ny post skriver över den äldsta posten.</span><span class="sxs-lookup"><span data-stu-id="98832-144">OverwriteAsNeeded:  Each new entry overwrites the oldest entry.</span></span>
- <span data-ttu-id="98832-145">OverwriteOlder: nya händelser skriver över händelser som är äldre än värdet som anges i egenskapen **MinimumRetentionDays** .</span><span class="sxs-lookup"><span data-stu-id="98832-145">OverwriteOlder:  New events overwrite events older than the value specified by the **MinimumRetentionDays** property.</span></span> <span data-ttu-id="98832-146">Om det inte finns några händelser som är äldre än vad som anges i egenskap svärdet **MinimumRetentionDays** , ignoreras nya händelser.</span><span class="sxs-lookup"><span data-stu-id="98832-146">If there are no events older than specified by the **MinimumRetentionDays** property value, new events are discarded.</span></span>

<span data-ttu-id="98832-147">Den här parametern anger värdet för egenskapen **OverflowAction** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="98832-147">This parameter specifies the value of the **OverflowAction** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98832-148">-RetentionDays</span><span class="sxs-lookup"><span data-stu-id="98832-148">-RetentionDays</span></span>
<span data-ttu-id="98832-149">Anger det minsta antalet dagar som en händelse måste finnas i händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="98832-149">Specifies the minimum number of days that an event must remain in the event log.</span></span>

<span data-ttu-id="98832-150">Den här parametern anger värdet för egenskapen **MinimumRetentionDays** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="98832-150">This parameter specifies the value of the **MinimumRetentionDays** property of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="98832-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="98832-151">-Confirm</span></span>
<span data-ttu-id="98832-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="98832-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="98832-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="98832-153">-WhatIf</span></span>
<span data-ttu-id="98832-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="98832-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="98832-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="98832-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="98832-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="98832-156">CommonParameters</span></span>
<span data-ttu-id="98832-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="98832-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="98832-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="98832-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="98832-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="98832-159">INPUTS</span></span>

### <span data-ttu-id="98832-160">Inget</span><span class="sxs-lookup"><span data-stu-id="98832-160">None</span></span>
<span data-ttu-id="98832-161">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98832-161">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="98832-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="98832-162">OUTPUTS</span></span>

### <span data-ttu-id="98832-163">Inget</span><span class="sxs-lookup"><span data-stu-id="98832-163">None</span></span>
<span data-ttu-id="98832-164">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="98832-164">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="98832-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="98832-165">NOTES</span></span>

* <span data-ttu-id="98832-166">Om du vill använda denna cmdlet i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="98832-166">To use this cmdlet on Windows Vista and later versions of Windows, open Windows PowerShell with the Run as administrator option.</span></span>

  <span data-ttu-id="98832-167">Den här cmdleten ändrar egenskaperna för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.</span><span class="sxs-lookup"><span data-stu-id="98832-167">This cmdlet changes the properties of the **System.Diagnostics.EventLog** object that represents a classic event log.</span></span>
<span data-ttu-id="98832-168">Om du vill se de aktuella inställningarna för händelse loggens egenskaper skriver du `Get-EventLog -List` .</span><span class="sxs-lookup"><span data-stu-id="98832-168">To see the current settings of the event log properties, type `Get-EventLog -List`.</span></span>

*

## <span data-ttu-id="98832-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="98832-169">RELATED LINKS</span></span>

[<span data-ttu-id="98832-170">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="98832-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="98832-172">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="98832-173">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="98832-174">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="98832-175">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="98832-176">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="98832-176">Write-EventLog</span></span>](Write-EventLog.md)
