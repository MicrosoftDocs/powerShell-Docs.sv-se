---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 4044453cb46b407344619f1edd3227213bf67250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388254"
---
# <span data-ttu-id="e749e-103">Write-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-103">Write-EventLog</span></span>

## <span data-ttu-id="e749e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e749e-104">SYNOPSIS</span></span>
<span data-ttu-id="e749e-105">Skriver en händelse i en händelse logg.</span><span class="sxs-lookup"><span data-stu-id="e749e-105">Writes an event to an event log.</span></span>

## <span data-ttu-id="e749e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e749e-106">SYNTAX</span></span>

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## <span data-ttu-id="e749e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e749e-107">DESCRIPTION</span></span>
<span data-ttu-id="e749e-108">`Write-EventLog`Cmdleten skriver en händelse till en händelse logg.</span><span class="sxs-lookup"><span data-stu-id="e749e-108">The `Write-EventLog` cmdlet writes an event to an event log.</span></span>

<span data-ttu-id="e749e-109">Om du vill skriva en händelse i en händelse logg måste händelse loggen finnas på datorn och källan måste vara registrerad för händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="e749e-109">To write an event to an event log, the event log must exist on the computer and the source must be registered for the event log.</span></span>

<span data-ttu-id="e749e-110">De cmdletar som innehåller **EventLog** -händelsen Substantiv ( **EventLog** -cmdletar) fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="e749e-110">The cmdlets that contain the **EventLog** noun (the **EventLog** cmdlets) work only on classic event logs.</span></span> <span data-ttu-id="e749e-111">Använd cmdleten för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows-operativsystemet `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="e749e-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of the Windows operating system, use the `Get-WinEvent` cmdlet.</span></span>

## <span data-ttu-id="e749e-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e749e-112">EXAMPLES</span></span>

### <span data-ttu-id="e749e-113">Exempel 1: skriva en händelse i program händelse loggen</span><span class="sxs-lookup"><span data-stu-id="e749e-113">Example 1: Write an event to the Application event log</span></span>

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

<span data-ttu-id="e749e-114">Det här kommandot skriver en händelse från Mittprog-källan till program händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="e749e-114">This command writes an event from the MyApp source to the Application event log.</span></span>

### <span data-ttu-id="e749e-115">Exempel 2: skriva en händelse i program händelse loggen på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="e749e-115">Example 2: Write an event to the Application event log of a remote computer</span></span>

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

<span data-ttu-id="e749e-116">Det här kommandot skriver en händelse från en Mittprog-källa till program händelse loggen på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="e749e-116">This command writes an event from the MyApp source to the Application event log on the Server01 remote computer.</span></span>

## <span data-ttu-id="e749e-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e749e-117">PARAMETERS</span></span>

### <span data-ttu-id="e749e-118">– Kategori</span><span class="sxs-lookup"><span data-stu-id="e749e-118">-Category</span></span>

<span data-ttu-id="e749e-119">Anger en aktivitets kategori för händelsen.</span><span class="sxs-lookup"><span data-stu-id="e749e-119">Specifies a task category for the event.</span></span> <span data-ttu-id="e749e-120">Ange ett heltal som är associerat med strängarna i kategori meddelande filen för händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="e749e-120">Enter an integer that is associated with the strings in the category message file for the event log.</span></span>

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-121">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="e749e-121">-ComputerName</span></span>

<span data-ttu-id="e749e-122">Anger en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e749e-122">Specifies a remote computer.</span></span> <span data-ttu-id="e749e-123">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e749e-123">The default is the local computer.</span></span>

<span data-ttu-id="e749e-124">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="e749e-124">Type the NetBIOS name, an IP address, or a fully qualified domain name of a remote computer.</span></span>

<span data-ttu-id="e749e-125">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="e749e-125">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="e749e-126">Du kan använda parametern **computername** för `Get-EventLog` cmdleten även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="e749e-126">You can use the **ComputerName** parameter of the `Get-EventLog` cmdlet even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-127">– EntryType</span><span class="sxs-lookup"><span data-stu-id="e749e-127">-EntryType</span></span>

<span data-ttu-id="e749e-128">Anger händelsens post typ.</span><span class="sxs-lookup"><span data-stu-id="e749e-128">Specifies the entry type of the event.</span></span> <span data-ttu-id="e749e-129">De acceptabla värdena för den här parametern är: error, Warning, information, SuccessAudit och FailureAudit.</span><span class="sxs-lookup"><span data-stu-id="e749e-129">The acceptable values for this parameter are: Error, Warning, Information, SuccessAudit, and FailureAudit.</span></span> <span data-ttu-id="e749e-130">Standardvärdet är information.</span><span class="sxs-lookup"><span data-stu-id="e749e-130">The default value is Information.</span></span>

<span data-ttu-id="e749e-131">En beskrivning av värdena finns i EventLogEntryType- [uppräkning](/dotnet/api/system.diagnostics.eventlogentrytype).</span><span class="sxs-lookup"><span data-stu-id="e749e-131">For a description of the values, see [EventLogEntryType Enumeration](/dotnet/api/system.diagnostics.eventlogentrytype).</span></span>

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-132">– EventId</span><span class="sxs-lookup"><span data-stu-id="e749e-132">-EventId</span></span>

<span data-ttu-id="e749e-133">Anger händelse-ID.</span><span class="sxs-lookup"><span data-stu-id="e749e-133">Specifies the event identifier.</span></span> <span data-ttu-id="e749e-134">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e749e-134">This parameter is required.</span></span> <span data-ttu-id="e749e-135">Det maximala värdet för parametern **EventId** är 65535.</span><span class="sxs-lookup"><span data-stu-id="e749e-135">The maximum value for the **EventId** parameter is 65535.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-136">-LogName</span><span class="sxs-lookup"><span data-stu-id="e749e-136">-LogName</span></span>

<span data-ttu-id="e749e-137">Anger namnet på den logg som händelsen skrivs till.</span><span class="sxs-lookup"><span data-stu-id="e749e-137">Specifies the name of the log to which the event is written.</span></span> <span data-ttu-id="e749e-138">Ange namnet på loggen.</span><span class="sxs-lookup"><span data-stu-id="e749e-138">Enter the log name.</span></span> <span data-ttu-id="e749e-139">Logg namnet är värdet för **logg** egenskapen, inte **LogDisplayName**.</span><span class="sxs-lookup"><span data-stu-id="e749e-139">The log name is the value of the **Log** property, not the **LogDisplayName**.</span></span> <span data-ttu-id="e749e-140">Jokertecken tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="e749e-140">Wildcard characters are not permitted.</span></span>
<span data-ttu-id="e749e-141">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e749e-141">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-142">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="e749e-142">-Message</span></span>

<span data-ttu-id="e749e-143">Anger händelse meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e749e-143">Specifies the event message.</span></span> <span data-ttu-id="e749e-144">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="e749e-144">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-145">-RawData</span><span class="sxs-lookup"><span data-stu-id="e749e-145">-RawData</span></span>

<span data-ttu-id="e749e-146">Anger de binära data som är associerade med händelsen, i byte.</span><span class="sxs-lookup"><span data-stu-id="e749e-146">Specifies the binary data that is associated with the event, in bytes.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-147">-Source</span><span class="sxs-lookup"><span data-stu-id="e749e-147">-Source</span></span>

<span data-ttu-id="e749e-148">Anger händelse källan, som vanligt vis är namnet på det program som skriver händelsen till loggen.</span><span class="sxs-lookup"><span data-stu-id="e749e-148">Specifies the event source, which is typically the name of the application that is writing the event to the log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e749e-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e749e-149">CommonParameters</span></span>

<span data-ttu-id="e749e-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e749e-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e749e-151">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e749e-151">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e749e-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="e749e-152">INPUTS</span></span>

### <span data-ttu-id="e749e-153">Inget</span><span class="sxs-lookup"><span data-stu-id="e749e-153">None</span></span>
<span data-ttu-id="e749e-154">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e749e-154">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e749e-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e749e-155">OUTPUTS</span></span>

### <span data-ttu-id="e749e-156">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="e749e-156">System.Diagnostics.EventLogEntry</span></span>
<span data-ttu-id="e749e-157">Denna cmdlet returnerar objekt som representerar händelserna i loggarna.</span><span class="sxs-lookup"><span data-stu-id="e749e-157">This cmdlet returns objects that represents the events in the logs.</span></span>

## <span data-ttu-id="e749e-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e749e-158">NOTES</span></span>

<span data-ttu-id="e749e-159">`Write-EventLog`Starta Windows PowerShell med alternativet Kör som administratör när du vill använda.</span><span class="sxs-lookup"><span data-stu-id="e749e-159">To use `Write-EventLog`, start Windows PowerShell by using the Run as administrator option.</span></span>

## <span data-ttu-id="e749e-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e749e-160">RELATED LINKS</span></span>

[<span data-ttu-id="e749e-161">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-161">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="e749e-162">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-162">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="e749e-163">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-163">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="e749e-164">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-164">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="e749e-165">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-165">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="e749e-166">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-166">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="e749e-167">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="e749e-167">Write-EventLog</span></span>](Write-EventLog.md)
