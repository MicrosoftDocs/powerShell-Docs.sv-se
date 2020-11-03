---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265484"
---
# <span data-ttu-id="46eb1-103">Remove-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-103">Remove-EventLog</span></span>

## <span data-ttu-id="46eb1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="46eb1-104">SYNOPSIS</span></span>
<span data-ttu-id="46eb1-105">Tar bort en händelse logg eller avregistrerar en händelse källa.</span><span class="sxs-lookup"><span data-stu-id="46eb1-105">Deletes an event log or unregisters an event source.</span></span>

## <span data-ttu-id="46eb1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="46eb1-106">SYNTAX</span></span>

### <span data-ttu-id="46eb1-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="46eb1-107">Default (Default)</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="46eb1-108">Källa</span><span class="sxs-lookup"><span data-stu-id="46eb1-108">Source</span></span>

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="46eb1-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="46eb1-109">DESCRIPTION</span></span>
<span data-ttu-id="46eb1-110">Cmdleten **Remove-EventLog** tar bort en händelse logg fil från en lokal dator eller fjärrdator och avregistrerar alla händelse källor för loggen.</span><span class="sxs-lookup"><span data-stu-id="46eb1-110">The **Remove-EventLog** cmdlet deletes an event log file from a local or remote computer and unregisters all its event sources for the log.</span></span>
<span data-ttu-id="46eb1-111">Du kan också använda denna cmdlet för att avregistrera händelse källor utan att ta bort några händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-111">You can also use this cmdlet to unregister event sources without deleting any event logs.</span></span>

<span data-ttu-id="46eb1-112">Cmdlet: arna som innehåller **EventLog** substantiv, **EventLog** -cmdletar fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-112">The cmdlets that contain the **EventLog** noun, the **EventLog** cmdlets, work only on classic event logs.</span></span>
<span data-ttu-id="46eb1-113">Använd Get-WinEvent för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="46eb1-113">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use Get-WinEvent.</span></span>

<span data-ttu-id="46eb1-114">Varning! den här cmdleten kan ta bort händelse loggar för operativ systemet, vilket kan orsaka program fel och oväntade system beteenden.</span><span class="sxs-lookup"><span data-stu-id="46eb1-114">CAUTION: This cmdlet can delete operating system event logs, which might cause application failures and unexpected system behavior.</span></span>

## <span data-ttu-id="46eb1-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="46eb1-115">EXAMPLES</span></span>

### <span data-ttu-id="46eb1-116">Exempel 1: ta bort en händelse logg från den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="46eb1-116">Example 1: Remove an event log from the local computer</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

<span data-ttu-id="46eb1-117">Det här kommandot tar bort händelse loggen MyLog från den lokala datorn och avregistrerar dess händelse källor.</span><span class="sxs-lookup"><span data-stu-id="46eb1-117">This command deletes the MyLog event log from the local computer and unregisters its event sources.</span></span>

### <span data-ttu-id="46eb1-118">Exempel 2: ta bort en händelse logg från flera datorer</span><span class="sxs-lookup"><span data-stu-id="46eb1-118">Example 2: Remove an event log from several computers</span></span>

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

<span data-ttu-id="46eb1-119">Det här kommandot tar bort händelse loggarna MyLog och TestLog från den lokala datorn och Server01-och Server02-fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="46eb1-119">This command deletes the MyLog and TestLog event logs from the local computer and the Server01 and Server02 remote computers.</span></span>
<span data-ttu-id="46eb1-120">Kommandot avregistrerar också händelse källorna för dessa loggar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-120">The command also unregisters the event sources for these logs.</span></span>

### <span data-ttu-id="46eb1-121">Exempel 3: ta bort en händelse källa</span><span class="sxs-lookup"><span data-stu-id="46eb1-121">Example 3: Delete an event source</span></span>

```
PS C:\> Remove-EventLog -Source "MyApp"
```

<span data-ttu-id="46eb1-122">Det här kommandot tar bort händelse källan för MyApp från loggarna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="46eb1-122">This command deletes the MyApp event source from the logs on the local computer.</span></span>
<span data-ttu-id="46eb1-123">När kommandot har slutförts kan inte programmet Mittprog skriva till några händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-123">When the command finishes, the MyApp program cannot write to any event logs.</span></span>

### <span data-ttu-id="46eb1-124">Exempel 4: ta bort en händelse logg och bekräfta åtgärden</span><span class="sxs-lookup"><span data-stu-id="46eb1-124">Example 4: Remove an event log and confirm the action</span></span>

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

<span data-ttu-id="46eb1-125">De här kommandona visar hur du listar händelse loggarna på en dator och kontrollerar att kommandot **Remove-EventLog** har slutförts.</span><span class="sxs-lookup"><span data-stu-id="46eb1-125">These commands show how to list the event logs on a computer and verify that a **Remove-EventLog** command was successful.</span></span>

### <span data-ttu-id="46eb1-126">Exempel 5: ta bort en händelse källa och bekräfta åtgärden</span><span class="sxs-lookup"><span data-stu-id="46eb1-126">Example 5: Remove an event source and confirm the action</span></span>

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

<span data-ttu-id="46eb1-127">Dessa kommandon använder Get-WmiObject-cmdleten för att visa händelse källorna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="46eb1-127">These commands use the Get-WmiObject cmdlet to list the event sources on the local computer.</span></span>
<span data-ttu-id="46eb1-128">Du kan kontrol lera att ett kommando är klart eller ta bort en händelse källa.</span><span class="sxs-lookup"><span data-stu-id="46eb1-128">You can these commands to verify the success of a command or to delete an event source.</span></span>

<span data-ttu-id="46eb1-129">Det första kommandot hämtar händelse källorna för händelse loggen TestLog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="46eb1-129">The first command gets the event sources of the TestLog event log on the local computer.</span></span>
<span data-ttu-id="46eb1-130">MyApp är en av källorna.</span><span class="sxs-lookup"><span data-stu-id="46eb1-130">MyApp is one of the sources.</span></span>

<span data-ttu-id="46eb1-131">Det andra kommandot använder *käll* parametern för **Remove-EventLog** för att ta bort händelse källan för MyApp.</span><span class="sxs-lookup"><span data-stu-id="46eb1-131">The second command uses the *Source* parameter of **Remove-EventLog** to delete the MyApp event source.</span></span>

<span data-ttu-id="46eb1-132">Det tredje kommandot är identiskt med det första.</span><span class="sxs-lookup"><span data-stu-id="46eb1-132">The third command is identical to the first.</span></span>
<span data-ttu-id="46eb1-133">Det visar att händelse källan för MyApp har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="46eb1-133">It shows that the MyApp event source was deleted.</span></span>

## <span data-ttu-id="46eb1-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="46eb1-134">PARAMETERS</span></span>

### <span data-ttu-id="46eb1-135">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="46eb1-135">-ComputerName</span></span>
<span data-ttu-id="46eb1-136">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="46eb1-136">Specifies a remote computer.</span></span>
<span data-ttu-id="46eb1-137">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="46eb1-137">The default is the local computer.</span></span>

<span data-ttu-id="46eb1-138">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="46eb1-138">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="46eb1-139">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="46eb1-139">To specify the local computer, type the computer name, a dot (.), or localhost.</span></span>

<span data-ttu-id="46eb1-140">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="46eb1-140">This parameter does not rely on Windows PowerShell remoting.</span></span>
<span data-ttu-id="46eb1-141">Du kan använda parametern *computername* för **Remove-EventLog** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="46eb1-141">You can use the *ComputerName* parameter of **Remove-EventLog** even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46eb1-142">-LogName</span><span class="sxs-lookup"><span data-stu-id="46eb1-142">-LogName</span></span>
<span data-ttu-id="46eb1-143">Anger händelse loggarna.</span><span class="sxs-lookup"><span data-stu-id="46eb1-143">Specifies the event logs.</span></span>
<span data-ttu-id="46eb1-144">Ange logg namnet för en eller flera händelse loggar, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="46eb1-144">Enter the log name of one or more event logs, separated by commas.</span></span>
<span data-ttu-id="46eb1-145">Logg namnet är värdet för egenskapen **log** , inte *LogDisplayName* , jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="46eb1-145">The log name is the value of the **Log** property, not the *LogDisplayName* , Wildcard characters are not permitted.</span></span>
<span data-ttu-id="46eb1-146">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="46eb1-146">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46eb1-147">-Source</span><span class="sxs-lookup"><span data-stu-id="46eb1-147">-Source</span></span>
<span data-ttu-id="46eb1-148">Anger händelse källorna som denna cmdlet avregistrerar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-148">Specifies the event sources that this cmdlet unregisters.</span></span>
<span data-ttu-id="46eb1-149">Ange käll namnen, inte namnet på den körbara filen, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="46eb1-149">Enter the source names, not the executable name, separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="46eb1-150">-Confirm</span><span class="sxs-lookup"><span data-stu-id="46eb1-150">-Confirm</span></span>
<span data-ttu-id="46eb1-151">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="46eb1-151">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="46eb1-152">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="46eb1-152">-WhatIf</span></span>
<span data-ttu-id="46eb1-153">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="46eb1-153">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="46eb1-154">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="46eb1-154">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="46eb1-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="46eb1-155">CommonParameters</span></span>
<span data-ttu-id="46eb1-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="46eb1-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="46eb1-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="46eb1-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="46eb1-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="46eb1-158">INPUTS</span></span>

### <span data-ttu-id="46eb1-159">Inget</span><span class="sxs-lookup"><span data-stu-id="46eb1-159">None</span></span>
<span data-ttu-id="46eb1-160">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="46eb1-160">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="46eb1-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="46eb1-161">OUTPUTS</span></span>

### <span data-ttu-id="46eb1-162">Inget</span><span class="sxs-lookup"><span data-stu-id="46eb1-162">None</span></span>
<span data-ttu-id="46eb1-163">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="46eb1-163">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="46eb1-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="46eb1-164">NOTES</span></span>

* <span data-ttu-id="46eb1-165">Om du vill använda **Remove-EventLog** på Windows Vista och senare versioner av operativ systemet Windows startar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="46eb1-165">To use **Remove-EventLog** on Windows Vista and later versions of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

  <span data-ttu-id="46eb1-166">Om du tar bort en händelse logg och sedan skapar loggen igen kommer du inte att kunna registrera samma händelse källor.</span><span class="sxs-lookup"><span data-stu-id="46eb1-166">If you remove an event log and then re-create the log, you will not be able to register the same event sources.</span></span>
<span data-ttu-id="46eb1-167">Program som använde händelse källorna för att skriva poster till den ursprungliga loggen kommer inte att kunna skriva till den nya loggen.</span><span class="sxs-lookup"><span data-stu-id="46eb1-167">Applications that used the events sources to write entries to the original log will not be able to write to the new log.</span></span>

* <span data-ttu-id="46eb1-168">När du avregistrerar en händelse källa för en viss logg kan händelse källan förhindras från att skriva poster i andra händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="46eb1-168">When you unregister an event source for a particular log, the event source might be prevented from writing entries in other event logs.</span></span>

## <span data-ttu-id="46eb1-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="46eb1-169">RELATED LINKS</span></span>

[<span data-ttu-id="46eb1-170">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-170">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="46eb1-171">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-171">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="46eb1-172">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-172">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="46eb1-173">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-173">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="46eb1-174">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-174">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="46eb1-175">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-175">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="46eb1-176">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="46eb1-176">Write-EventLog</span></span>](Write-EventLog.md)
