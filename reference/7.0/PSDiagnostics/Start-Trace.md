---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: 646d186b34e31aa2572aeefa12cc73d941076a13
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262281"
---
# <span data-ttu-id="de91c-103">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="de91c-103">Start-Trace</span></span>

## <span data-ttu-id="de91c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="de91c-104">SYNOPSIS</span></span>
<span data-ttu-id="de91c-105">Starta en Logging-session för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="de91c-105">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="de91c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="de91c-106">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="de91c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="de91c-107">DESCRIPTION</span></span>
<span data-ttu-id="de91c-108">Den här cmdleten startar en loggning av Windows Event trace-sessionen.</span><span class="sxs-lookup"><span data-stu-id="de91c-108">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="de91c-109">Denna cmdlet används av följande cmdlets:</span><span class="sxs-lookup"><span data-stu-id="de91c-109">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="de91c-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="de91c-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="de91c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="de91c-111">EXAMPLES</span></span>

### <span data-ttu-id="de91c-112">Exempel 1: starta en WSMan-spårningssession för spårning av loggar</span><span class="sxs-lookup"><span data-stu-id="de91c-112">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="de91c-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="de91c-113">PARAMETERS</span></span>

### <span data-ttu-id="de91c-114">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="de91c-114">-BufferSizeInKB</span></span>
<span data-ttu-id="de91c-115">Buffertstorleken för händelsespårningssessionen i kilobyte (KB).</span><span class="sxs-lookup"><span data-stu-id="de91c-115">Event Trace Session buffer size in kilobytes (KB).</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-116">-ETS</span><span class="sxs-lookup"><span data-stu-id="de91c-116">-ETS</span></span>
<span data-ttu-id="de91c-117">Skicka kommandon till Event trace-sessioner direkt utan att spara eller schemalägga.</span><span class="sxs-lookup"><span data-stu-id="de91c-117">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="de91c-118">– Format</span><span class="sxs-lookup"><span data-stu-id="de91c-118">-Format</span></span>
<span data-ttu-id="de91c-119">Anger logg formatet för data insamlaren.</span><span class="sxs-lookup"><span data-stu-id="de91c-119">Specifies the log format for the data collector.</span></span> <span data-ttu-id="de91c-120">För SQL Database-format måste du använda alternativet **OutputFilePath** på kommando raden med `dsn!log` värdet.</span><span class="sxs-lookup"><span data-stu-id="de91c-120">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="de91c-121">Standardvärdet är Binary (bin).</span><span class="sxs-lookup"><span data-stu-id="de91c-121">The default is binary (bin).</span></span> <span data-ttu-id="de91c-122">Möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="de91c-122">The possible values are:</span></span>

- <span data-ttu-id="de91c-123">bin-binär</span><span class="sxs-lookup"><span data-stu-id="de91c-123">bin - binary</span></span>
- <span data-ttu-id="de91c-124">bincirc – binär med cirkulär loggning</span><span class="sxs-lookup"><span data-stu-id="de91c-124">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="de91c-125">CSV – kommaavgränsade värden</span><span class="sxs-lookup"><span data-stu-id="de91c-125">csv - Comma-separated values</span></span>
- <span data-ttu-id="de91c-126">TSV-Tabbavgränsade värden</span><span class="sxs-lookup"><span data-stu-id="de91c-126">tsv - Tab-separated values</span></span>
- <span data-ttu-id="de91c-127">SQL-SQL-databas</span><span class="sxs-lookup"><span data-stu-id="de91c-127">sql - SQL database</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:
Accepted values: bin, bincirc, csv, tsv, sql

Required: False
Position: Named
Default value: bin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-128">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="de91c-128">-MaxBuffers</span></span>
<span data-ttu-id="de91c-129">Anger det maximala antalet buffertar för Event trace-sessioner.</span><span class="sxs-lookup"><span data-stu-id="de91c-129">Sets the maximum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-130">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="de91c-130">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="de91c-131">Anger den maximala logg fils storleken i megabyte (MB) eller antal poster för SQL-loggar.</span><span class="sxs-lookup"><span data-stu-id="de91c-131">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0 (no limit)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-132">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="de91c-132">-MinBuffers</span></span>
<span data-ttu-id="de91c-133">Anger det minsta antalet sessioner för Event Trace-Session.</span><span class="sxs-lookup"><span data-stu-id="de91c-133">Sets the minimum number of Event Trace Session buffers.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-134">– OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="de91c-134">-OutputFilePath</span></span>
<span data-ttu-id="de91c-135">Sökväg till logg filen för utdata eller DSN-och logg uppsättnings namnet i en SQL-databas.</span><span class="sxs-lookup"><span data-stu-id="de91c-135">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="de91c-136">Standard Sök vägen är `$env:systemdrive\PerfLogs\Admin` .</span><span class="sxs-lookup"><span data-stu-id="de91c-136">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: $env:systemdrive\PerfLogs\Admin
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-137">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="de91c-137">-ProviderFilePath</span></span>
<span data-ttu-id="de91c-138">Fil som visar flera providers för händelse spårning att aktivera.</span><span class="sxs-lookup"><span data-stu-id="de91c-138">File listing multiple Event Trace providers to enable.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-139">-Sessionsnamn</span><span class="sxs-lookup"><span data-stu-id="de91c-139">-SessionName</span></span>
<span data-ttu-id="de91c-140">Namnet på händelse spårnings sessionen.</span><span class="sxs-lookup"><span data-stu-id="de91c-140">The name of the Event Trace session.</span></span> <span data-ttu-id="de91c-141">Om du vill stoppa en spårningssession måste du känna till sessionens namn.</span><span class="sxs-lookup"><span data-stu-id="de91c-141">To stop a trace session you must know the session name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="de91c-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="de91c-142">CommonParameters</span></span>

<span data-ttu-id="de91c-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="de91c-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="de91c-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="de91c-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="de91c-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="de91c-145">INPUTS</span></span>

### <span data-ttu-id="de91c-146">Inget</span><span class="sxs-lookup"><span data-stu-id="de91c-146">None</span></span>

## <span data-ttu-id="de91c-147">UTDATA</span><span class="sxs-lookup"><span data-stu-id="de91c-147">OUTPUTS</span></span>

### <span data-ttu-id="de91c-148">Inget</span><span class="sxs-lookup"><span data-stu-id="de91c-148">None</span></span>

## <span data-ttu-id="de91c-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="de91c-149">NOTES</span></span>

## <span data-ttu-id="de91c-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="de91c-150">RELATED LINKS</span></span>

[<span data-ttu-id="de91c-151">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="de91c-151">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="de91c-152">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="de91c-152">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="de91c-153">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="de91c-153">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="de91c-154">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="de91c-154">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="de91c-155">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="de91c-155">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="de91c-156">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="de91c-156">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
