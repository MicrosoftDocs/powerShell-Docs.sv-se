---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/start-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Trace
ms.openlocfilehash: b1c6a596f3dc35028b928c3a6b5459a805bc2512
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709055"
---
# <span data-ttu-id="f2101-102">Start-Trace</span><span class="sxs-lookup"><span data-stu-id="f2101-102">Start-Trace</span></span>

## <span data-ttu-id="f2101-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f2101-103">SYNOPSIS</span></span>
<span data-ttu-id="f2101-104">Starta en Logging-session för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="f2101-104">Start an Event Trace logging session.</span></span>

## <span data-ttu-id="f2101-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2101-105">SYNTAX</span></span>

```
Start-Trace [-SessionName] <String> [[-OutputFilePath] <String>] [[-ProviderFilePath] <String>]
 [-ETS] [-Format <String>] [-MinBuffers <Int32>] [-MaxBuffers <Int32>]
 [-BufferSizeInKB <Int32>] [-MaxLogFileSizeInMB <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="f2101-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f2101-106">DESCRIPTION</span></span>
<span data-ttu-id="f2101-107">Den här cmdleten startar en loggning av Windows Event trace-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2101-107">This cmdlet starts a Windows Event Trace logging session.</span></span>

<span data-ttu-id="f2101-108">Denna cmdlet används av följande cmdlets:</span><span class="sxs-lookup"><span data-stu-id="f2101-108">This cmdlet is used by the following cmdlets:</span></span>

- `Enable-PSWSManCombinedTrace`
- `Enable-WSManTrace`

<span data-ttu-id="f2101-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="f2101-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="f2101-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f2101-110">EXAMPLES</span></span>

### <span data-ttu-id="f2101-111">Exempel 1: starta en WSMan-spårningssession för spårning av loggar</span><span class="sxs-lookup"><span data-stu-id="f2101-111">Example 1: Start a WSMan Trace logging session</span></span>

```powershell
Start-Trace -SessionName 'wsmlog' -ETS -OutputFilePath "$env:windir\system32\wsmtraces.log" -Format 'bincirc' -MinBuffers 16 -MaxBuffers 256 -BufferSizeInKb 64 -MaxLogFileSizeInMB 256 -ProviderFilePath "$env:windir\system32\wsmtraceproviders.txt"
```

## <span data-ttu-id="f2101-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f2101-112">PARAMETERS</span></span>

### <span data-ttu-id="f2101-113">-BufferSizeInKB</span><span class="sxs-lookup"><span data-stu-id="f2101-113">-BufferSizeInKB</span></span>
<span data-ttu-id="f2101-114">Buffertstorleken för händelsespårningssessionen i kilobyte (KB).</span><span class="sxs-lookup"><span data-stu-id="f2101-114">Event Trace Session buffer size in kilobytes (KB).</span></span>

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

### <span data-ttu-id="f2101-115">-ETS</span><span class="sxs-lookup"><span data-stu-id="f2101-115">-ETS</span></span>
<span data-ttu-id="f2101-116">Skicka kommandon till Event trace-sessioner direkt utan att spara eller schemalägga.</span><span class="sxs-lookup"><span data-stu-id="f2101-116">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="f2101-117">– Format</span><span class="sxs-lookup"><span data-stu-id="f2101-117">-Format</span></span>
<span data-ttu-id="f2101-118">Anger logg formatet för data insamlaren.</span><span class="sxs-lookup"><span data-stu-id="f2101-118">Specifies the log format for the data collector.</span></span> <span data-ttu-id="f2101-119">För SQL Database-format måste du använda alternativet **OutputFilePath** på kommando raden med `dsn!log` värdet.</span><span class="sxs-lookup"><span data-stu-id="f2101-119">For SQL database format, you must use the **OutputFilePath** option in the command line with the `dsn!log` value.</span></span> <span data-ttu-id="f2101-120">Standardvärdet är Binary (bin).</span><span class="sxs-lookup"><span data-stu-id="f2101-120">The default is binary (bin).</span></span> <span data-ttu-id="f2101-121">Möjliga värden är:</span><span class="sxs-lookup"><span data-stu-id="f2101-121">The possible values are:</span></span>

- <span data-ttu-id="f2101-122">bin-binär</span><span class="sxs-lookup"><span data-stu-id="f2101-122">bin - binary</span></span>
- <span data-ttu-id="f2101-123">bincirc – binär med cirkulär loggning</span><span class="sxs-lookup"><span data-stu-id="f2101-123">bincirc - binary with circular logging</span></span>
- <span data-ttu-id="f2101-124">CSV – kommaavgränsade värden</span><span class="sxs-lookup"><span data-stu-id="f2101-124">csv - Comma-separated values</span></span>
- <span data-ttu-id="f2101-125">TSV-Tabbavgränsade värden</span><span class="sxs-lookup"><span data-stu-id="f2101-125">tsv - Tab-separated values</span></span>
- <span data-ttu-id="f2101-126">SQL-SQL-databas</span><span class="sxs-lookup"><span data-stu-id="f2101-126">sql - SQL database</span></span>

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

### <span data-ttu-id="f2101-127">-MaxBuffers</span><span class="sxs-lookup"><span data-stu-id="f2101-127">-MaxBuffers</span></span>
<span data-ttu-id="f2101-128">Anger det maximala antalet buffertar för Event trace-sessioner.</span><span class="sxs-lookup"><span data-stu-id="f2101-128">Sets the maximum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="f2101-129">-MaxLogFileSizeInMB</span><span class="sxs-lookup"><span data-stu-id="f2101-129">-MaxLogFileSizeInMB</span></span>
<span data-ttu-id="f2101-130">Anger den maximala logg fils storleken i megabyte (MB) eller antal poster för SQL-loggar.</span><span class="sxs-lookup"><span data-stu-id="f2101-130">Sets the maximum log file size in megabytes (MB) or number of records for SQL logs.</span></span>

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

### <span data-ttu-id="f2101-131">-MinBuffers</span><span class="sxs-lookup"><span data-stu-id="f2101-131">-MinBuffers</span></span>
<span data-ttu-id="f2101-132">Anger det minsta antalet sessioner för Event Trace-Session.</span><span class="sxs-lookup"><span data-stu-id="f2101-132">Sets the minimum number of Event Trace Session buffers.</span></span>

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

### <span data-ttu-id="f2101-133">– OutputFilePath</span><span class="sxs-lookup"><span data-stu-id="f2101-133">-OutputFilePath</span></span>
<span data-ttu-id="f2101-134">Sökväg till logg filen för utdata eller DSN-och logg uppsättnings namnet i en SQL-databas.</span><span class="sxs-lookup"><span data-stu-id="f2101-134">Path of the output log file or the DSN and log set name in a SQL database.</span></span> <span data-ttu-id="f2101-135">Standard Sök vägen är `$env:systemdrive\PerfLogs\Admin` .</span><span class="sxs-lookup"><span data-stu-id="f2101-135">The default path is `$env:systemdrive\PerfLogs\Admin`.</span></span>

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

### <span data-ttu-id="f2101-136">-ProviderFilePath</span><span class="sxs-lookup"><span data-stu-id="f2101-136">-ProviderFilePath</span></span>
<span data-ttu-id="f2101-137">Fil som visar flera providers för händelse spårning att aktivera.</span><span class="sxs-lookup"><span data-stu-id="f2101-137">File listing multiple Event Trace providers to enable.</span></span>

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

### <span data-ttu-id="f2101-138">-Sessionsnamn</span><span class="sxs-lookup"><span data-stu-id="f2101-138">-SessionName</span></span>
<span data-ttu-id="f2101-139">Namnet på händelse spårnings sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2101-139">The name of the Event Trace session.</span></span> <span data-ttu-id="f2101-140">Om du vill stoppa en spårningssession måste du känna till sessionens namn.</span><span class="sxs-lookup"><span data-stu-id="f2101-140">To stop a trace session you must know the session name.</span></span>

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

### <span data-ttu-id="f2101-141">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2101-141">CommonParameters</span></span>

<span data-ttu-id="f2101-142">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2101-142">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2101-143">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2101-143">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2101-144">INDATA</span><span class="sxs-lookup"><span data-stu-id="f2101-144">INPUTS</span></span>

### <span data-ttu-id="f2101-145">Inga</span><span class="sxs-lookup"><span data-stu-id="f2101-145">None</span></span>

## <span data-ttu-id="f2101-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f2101-146">OUTPUTS</span></span>

### <span data-ttu-id="f2101-147">Inga</span><span class="sxs-lookup"><span data-stu-id="f2101-147">None</span></span>

## <span data-ttu-id="f2101-148">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f2101-148">NOTES</span></span>

## <span data-ttu-id="f2101-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f2101-149">RELATED LINKS</span></span>

[<span data-ttu-id="f2101-150">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="f2101-150">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="f2101-151">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="f2101-151">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="f2101-152">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="f2101-152">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="f2101-153">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f2101-153">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="f2101-154">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="f2101-154">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="f2101-155">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="f2101-155">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

