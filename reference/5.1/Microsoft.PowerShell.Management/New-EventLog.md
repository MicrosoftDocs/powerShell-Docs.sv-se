---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265532"
---
# <span data-ttu-id="3d1b0-103">New-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-103">New-EventLog</span></span>

## <span data-ttu-id="3d1b0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3d1b0-104">SYNOPSIS</span></span>
<span data-ttu-id="3d1b0-105">Skapar en ny händelse logg och en ny händelse källa på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-105">Creates a new event log and a new event source on a local or remote computer.</span></span>

## <span data-ttu-id="3d1b0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d1b0-106">SYNTAX</span></span>

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## <span data-ttu-id="3d1b0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3d1b0-107">DESCRIPTION</span></span>

<span data-ttu-id="3d1b0-108">Denna cmdlet skapar en ny klassisk händelse logg på en lokal eller fjärran sluten dator.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-108">This cmdlet creates a new classic event log on a local or remote computer.</span></span> <span data-ttu-id="3d1b0-109">Det kan också registrera en händelse källa som skriver till den nya loggen eller till en befintlig logg.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-109">It can also register an event source that writes to the new log or to an existing log.</span></span>

<span data-ttu-id="3d1b0-110">De cmdletar som innehåller EventLog-händelsen Substantiv (händelse logg-cmdletar) fungerar bara på klassiska händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-110">The cmdlets that contain the EventLog noun (the Event log cmdlets) work only on classic event logs.</span></span>
<span data-ttu-id="3d1b0-111">Använd för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="3d1b0-111">To get events from logs that use the Windows Event Log technology in Windows Vista and later versions of Windows, use `Get-WinEvent`.</span></span>

## <span data-ttu-id="3d1b0-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3d1b0-112">EXAMPLES</span></span>

### <span data-ttu-id="3d1b0-113">Exempel 1 – Skapa en ny händelse logg</span><span class="sxs-lookup"><span data-stu-id="3d1b0-113">Example 1 - create a new event log</span></span>

<span data-ttu-id="3d1b0-114">Med det här kommandot skapas händelse loggen TestLog på den lokala datorn och en ny källa registreras.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-114">This command creates the TestLog event log on the local computer and registers a new source for it.</span></span>

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### <span data-ttu-id="3d1b0-115">Exempel 2 – lägga till en ny händelse källa i en befintlig logg</span><span class="sxs-lookup"><span data-stu-id="3d1b0-115">Example 2 - add a new event source to an existing log</span></span>

<span data-ttu-id="3d1b0-116">Detta kommando lägger till en ny händelse källa, NewTestApp, i program loggen på Server01-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-116">This command adds a new event source, NewTestApp, to the Application log on the Server01 remote computer.</span></span>

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

<span data-ttu-id="3d1b0-117">Kommandot kräver att NewTestApp.dll-filen finns på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-117">The command requires that the NewTestApp.dll file is located on the Server01 computer.</span></span>

## <span data-ttu-id="3d1b0-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3d1b0-118">PARAMETERS</span></span>

### <span data-ttu-id="3d1b0-119">-CategoryResourceFile</span><span class="sxs-lookup"><span data-stu-id="3d1b0-119">-CategoryResourceFile</span></span>

<span data-ttu-id="3d1b0-120">Anger sökvägen till filen som innehåller kategori strängar för käll händelser.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-120">Specifies the path to the file that contains category strings for the source events.</span></span> <span data-ttu-id="3d1b0-121">Den här filen kallas även för kategori meddelande filen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-121">This file is also known as the Category Message File.</span></span>

<span data-ttu-id="3d1b0-122">Filen måste finnas på den dator där händelse loggen skapas.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-122">The file must be present on the computer on which the event log is being created.</span></span> <span data-ttu-id="3d1b0-123">Den här parametern skapar eller flyttar inte filer.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-123">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-124">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3d1b0-124">-ComputerName</span></span>

<span data-ttu-id="3d1b0-125">Skapar de nya händelse loggarna på de angivna datorerna.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-125">Creates the new event logs on the specified computers.</span></span> <span data-ttu-id="3d1b0-126">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-126">The default is the local computer.</span></span>

<span data-ttu-id="3d1b0-127">NetBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-127">The NetBIOS name, IP address, or fully qualified domain name of a remote computer.</span></span>
<span data-ttu-id="3d1b0-128">Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller "localhost".</span><span class="sxs-lookup"><span data-stu-id="3d1b0-128">To specify the local computer, type the computer name, a dot (.), or "localhost".</span></span>

<span data-ttu-id="3d1b0-129">Den här parametern är inte beroende av PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-129">This parameter does not rely on PowerShell remoting.</span></span> <span data-ttu-id="3d1b0-130">Du kan använda parametern **computername** för `Get-EventLog` även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-130">You can use the **ComputerName** parameter of `Get-EventLog` even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-131">-LogName</span><span class="sxs-lookup"><span data-stu-id="3d1b0-131">-LogName</span></span>

<span data-ttu-id="3d1b0-132">Anger namnet på händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-132">Specifies the name of the event log.</span></span>

<span data-ttu-id="3d1b0-133">Om loggen inte finns `New-EventLog` skapar loggen och använder det här värdet för **logg** -och **LogDisplayName** -egenskaperna för den nya händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-133">If the log does not exist, `New-EventLog` creates the log and uses this value for the **Log** and **LogDisplayName** properties of the new event log.</span></span> <span data-ttu-id="3d1b0-134">Om det finns en logg `New-EventLog` registreras en ny källa för händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-134">If the log exists, `New-EventLog` registers a new source for the event log.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-135">-MessageResourceFile</span><span class="sxs-lookup"><span data-stu-id="3d1b0-135">-MessageResourceFile</span></span>

<span data-ttu-id="3d1b0-136">Anger sökvägen till filen som innehåller strängar för meddelande formatering för käll händelser.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-136">Specifies the path to the file that contains message formatting strings for the source events.</span></span>
<span data-ttu-id="3d1b0-137">Den här filen kallas även för händelse meddelande filen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-137">This file is also known as the Event Message File.</span></span>

<span data-ttu-id="3d1b0-138">Filen måste finnas på den dator där händelse loggen skapas.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-138">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="3d1b0-139">Den här parametern skapar eller flyttar inte filer.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-139">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-140">-ParameterResourceFile</span><span class="sxs-lookup"><span data-stu-id="3d1b0-140">-ParameterResourceFile</span></span>

<span data-ttu-id="3d1b0-141">Anger sökvägen till filen som innehåller strängar som används för parameter ersättningar i händelse beskrivningar.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-141">Specifies the path to the file that contains strings used for parameter substitutions in event descriptions.</span></span> <span data-ttu-id="3d1b0-142">Den här filen kallas även för parameter meddelande filen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-142">This file is also known as the Parameter Message File.</span></span>

<span data-ttu-id="3d1b0-143">Filen måste finnas på den dator där händelse loggen skapas.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-143">The file must be present on the computer on which the event log is being created.</span></span>
<span data-ttu-id="3d1b0-144">Den här parametern skapar eller flyttar inte filer.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-144">This parameter does not create or move files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-145">-Source</span><span class="sxs-lookup"><span data-stu-id="3d1b0-145">-Source</span></span>

<span data-ttu-id="3d1b0-146">Anger namnen på händelse logg källorna, till exempel program program som skriver till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-146">Specifies the names of the event log sources, such as application programs that write to the event log.</span></span> <span data-ttu-id="3d1b0-147">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-147">This parameter is required.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3d1b0-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d1b0-148">CommonParameters</span></span>

<span data-ttu-id="3d1b0-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d1b0-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3d1b0-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3d1b0-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="3d1b0-151">INPUTS</span></span>

### <span data-ttu-id="3d1b0-152">Inget</span><span class="sxs-lookup"><span data-stu-id="3d1b0-152">None</span></span>

<span data-ttu-id="3d1b0-153">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-153">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3d1b0-154">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3d1b0-154">OUTPUTS</span></span>

### <span data-ttu-id="3d1b0-155">System. Diagnostics. EventLogEntry</span><span class="sxs-lookup"><span data-stu-id="3d1b0-155">System.Diagnostics.EventLogEntry</span></span>

## <span data-ttu-id="3d1b0-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3d1b0-156">NOTES</span></span>

<span data-ttu-id="3d1b0-157">Om du vill använda `New-EventLog` i Windows Vista och senare versioner av Windows öppnar du PowerShell med alternativet "kör som administratör".</span><span class="sxs-lookup"><span data-stu-id="3d1b0-157">To use `New-EventLog` on Windows Vista and later versions of Windows, open PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="3d1b0-158">Om du vill skapa en händelse källa i Windows Vista, Windows XP Professional eller Windows Server 2003 måste du vara medlem i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-158">To create an event source in Windows Vista, Windows XP Professional, or Windows Server 2003, you must be a member of the Administrators group on the computer.</span></span>

<span data-ttu-id="3d1b0-159">När du skapar en ny händelse logg och en ny händelse källa registrerar systemet den nya källan för den nya loggen, men loggen skapas inte förrän den första posten skrivs till den.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-159">When you create a new event log and a new event source, the system registers the new source for the new log, but the log is not created until the first entry is written to it.</span></span>

<span data-ttu-id="3d1b0-160">Operativ systemet lagrar händelse loggar som filer.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-160">The operating system stores event logs as files.</span></span>

<span data-ttu-id="3d1b0-161">När du skapar en ny händelse logg lagras den tillhör ande filen i `$env:SystemRoot\System32\Config` katalogen på den angivna datorn.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-161">When you create a new event log, the associated file is stored in the `$env:SystemRoot\System32\Config` directory on the specified computer.</span></span>

<span data-ttu-id="3d1b0-162">Fil namnet är de första åtta tecknen i **logg** egenskapen med fil namns tillägget. evt.</span><span class="sxs-lookup"><span data-stu-id="3d1b0-162">The file name is the first eight characters of the **Log** property with an .evt file name extension.</span></span>

## <span data-ttu-id="3d1b0-163">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3d1b0-163">RELATED LINKS</span></span>

[<span data-ttu-id="3d1b0-164">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-164">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="3d1b0-165">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-165">Get-EventLog</span></span>](Get-EventLog.md)

[<span data-ttu-id="3d1b0-166">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="3d1b0-166">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="3d1b0-167">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-167">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="3d1b0-168">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-168">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="3d1b0-169">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-169">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="3d1b0-170">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-170">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="3d1b0-171">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="3d1b0-171">Write-EventLog</span></span>](Write-EventLog.md)
