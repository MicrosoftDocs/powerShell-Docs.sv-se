---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/import-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Counter
ms.openlocfilehash: 837f6b4b3b2869c6f74b3b02904dd43b73f6bcd5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264093"
---
# <span data-ttu-id="1d68e-103">Import-Counter</span><span class="sxs-lookup"><span data-stu-id="1d68e-103">Import-Counter</span></span>

## <span data-ttu-id="1d68e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1d68e-104">SYNOPSIS</span></span>
<span data-ttu-id="1d68e-105">Importerar loggfiler för prestanda räknare och skapar de objekt som representerar varje räknar exempel i loggen.</span><span class="sxs-lookup"><span data-stu-id="1d68e-105">Imports performance counter log files and creates the objects that represent each counter sample in the log.</span></span>

## <span data-ttu-id="1d68e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1d68e-106">SYNTAX</span></span>

### <span data-ttu-id="1d68e-107">GetCounterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="1d68e-107">GetCounterSet (Default)</span></span>

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### <span data-ttu-id="1d68e-108">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="1d68e-108">ListSetSet</span></span>

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### <span data-ttu-id="1d68e-109">SummarySet</span><span class="sxs-lookup"><span data-stu-id="1d68e-109">SummarySet</span></span>

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## <span data-ttu-id="1d68e-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1d68e-110">DESCRIPTION</span></span>

<span data-ttu-id="1d68e-111">Cmdleten **import-Counter** importerar prestanda räknar data från loggfiler för prestanda räknare och skapar objekt för varje räknar exempel i filen.</span><span class="sxs-lookup"><span data-stu-id="1d68e-111">The **Import-Counter** cmdlet imports performance counter data from performance counter log files and creates objects for each counter sample in the file.</span></span>
<span data-ttu-id="1d68e-112">**PerformanceCounterSampleSet** -objekten som den skapar är identiska med de objekt som **erhåller Counter** returnerar när de samlar in prestanda räknar data.</span><span class="sxs-lookup"><span data-stu-id="1d68e-112">The **PerformanceCounterSampleSet** objects that it creates are identical to the objects that **Get-Counter** returns when it collects performance counter data.</span></span>

<span data-ttu-id="1d68e-113">Du kan importera data från filer med kommaavgränsade värden (. csv), tabbavgränsade värde (. tsv) och prestanda logg för binär prestanda logg (. blg).</span><span class="sxs-lookup"><span data-stu-id="1d68e-113">You can import data from comma-separated value (.csv), tab-separated value ( .tsv), and binary performance log (.blg) performance log files.</span></span>
<span data-ttu-id="1d68e-114">Om du använder. BLG-filer kan du importera upp till 32 filer i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="1d68e-114">If you are using .blg files, you can import up to 32 files in each command.</span></span>
<span data-ttu-id="1d68e-115">Du kan använda parametrarna för **import-Counter** för att filtrera de data som du importerar.</span><span class="sxs-lookup"><span data-stu-id="1d68e-115">You can use the parameters of **Import-Counter** to filter the data that you import.</span></span>

<span data-ttu-id="1d68e-116">Tillsammans med Get-Counter-och Export-Counter-cmdletar kan du använda den här funktionen för att samla in, exportera, importera, kombinera, filtrera, ändra och exportera prestanda räknar data på nytt i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1d68e-116">Along with the Get-Counter and Export-Counter cmdlets, this feature lets you collect, export, import, combine, filter, manipulate, and re-export performance counter data within Windows PowerShell.</span></span>

## <span data-ttu-id="1d68e-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1d68e-117">EXAMPLES</span></span>

### <span data-ttu-id="1d68e-118">Exempel 1: importera alla räknar data från en fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-118">Example 1: Import all counter data from a file</span></span>

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

<span data-ttu-id="1d68e-119">Det här kommandot importerar alla räknar data från ProcessorData.csv-filen till $Data-variabeln.</span><span class="sxs-lookup"><span data-stu-id="1d68e-119">This command imports all counter data from the ProcessorData.csv file into the $Data variable.</span></span>

### <span data-ttu-id="1d68e-120">Exempel 2: importera vissa räknar data från en fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-120">Example 2: Import specific counter data from a file</span></span>

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

<span data-ttu-id="1d68e-121">Det här kommandot importerar bara räknar data för **"processor (_Total) \ avbrott/s"** från ProcessorData. blg-filen till $I-variabeln.</span><span class="sxs-lookup"><span data-stu-id="1d68e-121">This command imports only the **"Processor(_total)\Interrupts/sec"** counter data from the ProcessorData.blg file into the $I variable.</span></span>

### <span data-ttu-id="1d68e-122">Exempel 3: Välj data från en prestanda räknare och exportera den till en fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-122">Example 3: Select data from a performance counter then export it to a file</span></span>

```
The first command uses **Import-Counter** to import all of the performance counter data from the ProcessorData.blg files. The command saves the data in the $Data variable.
PS C:\> $Data = Import-Counter .\ProcessorData.blg

The second command displays the counter paths in the $Data variable. To get the display shown in the command output, the example uses the Format-Table cmdlet to format as a table the counter paths of the first counter in the $Data variable.
PS C:\> $Data[0].CounterSamples | Format-Table -Property Path

Path
----
\\SERVER01\Processor(_Total)\DPC Rate
\\SERVER01\Processor(1)\DPC Rate
\\SERVER01\Processor(0)\DPC Rate
\\SERVER01\Processor(_Total)\% Idle Time
\\SERVER01\Processor(1)\% Idle Time
\\SERVER01\Processor(0)\% Idle Time
\\SERVER01\Processor(_Total)\% C3 Time
\\SERVER01\Processor(1)\% C3 Time

The third command gets the counter paths that end in "Interrupts/sec" and saves the paths in the $IntCtrs variable. It uses the Where-Object cmdlet to filter the counter paths and the ForEach-Object cmdlet to get only the value of the **Path** property of each selected path object.
PS C:\> $IntCtrs = $Data[0].Countersamples | Where-Object {$_.Path -like "*Interrupts/sec"} | ForEach-Object {$_.Path}

The fourth command displays the selected counter paths in the $IntCtrs variable.
PS C:\> $IntCtrs

\\SERVER01\Processor(_Total)\Interrupts/sec
\\SERVER01\Processor(1)\Interrupts/sec
\\SERVER01\Processor(0)\Interrupts/sec

The fifth command uses the **Import-Counter** cmdlet to import the data. It uses the $IntCtrs variable as the value of the *Counter* parameter to import only data for the counter paths in $IntCtrs.
PS C:\> $I = Import-Counter -Path .\ProcessorData.blg -Counter $intCtrs

The sixth command uses the Export-Counter cmdlet to export the data to the Interrupts.csv file.
PS C:\> $I | Export-Counter -Path .\Interrupts.csv -Format CSV
```

<span data-ttu-id="1d68e-123">Det här exemplet visar hur du väljer data från en prestanda räknar logg fil (. blg) och sedan exporterar de markerade data till en. csv-fil.</span><span class="sxs-lookup"><span data-stu-id="1d68e-123">This example shows how to select data from a performance counter log file (.blg) and then export the selected data to a .csv file.</span></span>
<span data-ttu-id="1d68e-124">De första fyra kommandona hämtar räknar Sök vägarna från filen och sparar dem i variabeln med namnet $Data.</span><span class="sxs-lookup"><span data-stu-id="1d68e-124">The first four commands get the counter paths from the file and save them in the variable named $Data.</span></span>
<span data-ttu-id="1d68e-125">De två sista kommandona importerar markerade data och exporterar bara de valda data.</span><span class="sxs-lookup"><span data-stu-id="1d68e-125">The last two commands import selected data and then export only the selected data.</span></span>

### <span data-ttu-id="1d68e-126">Exempel 4: Visa alla räknar Sök vägar i en grupp med importerade räknar uppsättningar</span><span class="sxs-lookup"><span data-stu-id="1d68e-126">Example 4: Display all counter paths in a group of imported counter sets</span></span>

```
The first command uses the *ListSet* parameter of the **Import-Counter** cmdlet to get all of the counter sets that are represented in a counter data file.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet *

CounterSetName     : Processor
MachineName        : \\SERVER01
CounterSetType     : MultiInstance
Description        :
Paths              : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}
PathsWithInstances : {\\SERVER01\Processor(_Total)\DPC Rate, \\SERVER01\Processor(1)\DPC Rate, \\SERVER01
\Processor(0)\DPC Rate, \\SERVER01\Processor(_Total)\% Idle Time...}
Counter            : {\\SERVER01\Processor(*)\DPC Rate, \\SERVER01\Processor(*)\% Idle Time, \\SERVER01
\Processor(*)\% C3 Time, \\SERVER01\Processor(*)\% Interrupt Time...}

The second command gets all of the counter paths from the list set.
PS C:\> Import-Counter -Path ProcessorData.csv -ListSet * | ForEach-Object {$_.Paths}

\\SERVER01\Processor(*)\DPC Rate
\\SERVER01\Processor(*)\% Idle Time
\\SERVER01\Processor(*)\% C3 Time
\\SERVER01\Processor(*)\% Interrupt Time
\\SERVER01\Processor(*)\% C2 Time
\\SERVER01\Processor(*)\% User Time
\\SERVER01\Processor(*)\% C1 Time
\\SERVER01\Processor(*)\% Processor Time
\\SERVER01\Processor(*)\C1 Transitions/sec
\\SERVER01\Processor(*)\% DPC Time
\\SERVER01\Processor(*)\C2 Transitions/sec
\\SERVER01\Processor(*)\% Privileged Time
\\SERVER01\Processor(*)\C3 Transitions/sec
\\SERVER01\Processor(*)\DPCs Queued/sec
\\SERVER01\Processor(*)\Interrupts/sec
```

<span data-ttu-id="1d68e-127">Det här exemplet visar hur du visar alla räknar Sök vägar i en grupp med importerade räknar uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="1d68e-127">This example shows how to display all the counter paths in a group of imported counter sets.</span></span>

### <span data-ttu-id="1d68e-128">Exempel 5: importera räknar data från ett intervall med tidsstämplar</span><span class="sxs-lookup"><span data-stu-id="1d68e-128">Example 5: Import counter data from a range of time stamps</span></span>

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

<span data-ttu-id="1d68e-129">I det här exemplet importeras bara räknar data som har en tidsstämpel mellan de start intervall som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="1d68e-129">This example imports only the counter data that has a time stamp between the starting an ending ranges specified in the command.</span></span>

### <span data-ttu-id="1d68e-130">Exempel 6: importera ett angivet antal av de äldsta exemplen från en prestanda räknar logg fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-130">Example 6: Import a specified number of the oldest samples from a performance counter log file</span></span>

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

<span data-ttu-id="1d68e-131">I det här exemplet visas hur du importerar de fem äldsta och fem senaste exemplen från en prestanda räknar logg fil.</span><span class="sxs-lookup"><span data-stu-id="1d68e-131">This example shows how to import the five oldest and five newest samples from a performance counter log file.</span></span>

### <span data-ttu-id="1d68e-132">Exempel 7: Hämta en sammanfattning av räknar data från en fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-132">Example 7: Get a summary of counter data from a file</span></span>

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

<span data-ttu-id="1d68e-133">Detta kommando använder *sammanfattnings* parametern för cmdleten **import-Counter** för att få en översikt över räknar data i filen Memory. blg.</span><span class="sxs-lookup"><span data-stu-id="1d68e-133">This command uses the *Summary* parameter of the **Import-Counter** cmdlet to get a summary of the counter data in the Memory.blg file.</span></span>

### <span data-ttu-id="1d68e-134">Exempel 8: uppdatera en prestanda räknar logg fil</span><span class="sxs-lookup"><span data-stu-id="1d68e-134">Example 8: Update a performance counter log file</span></span>

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

<span data-ttu-id="1d68e-135">Det här exemplet uppdaterar en logg fil för prestanda räknaren.</span><span class="sxs-lookup"><span data-stu-id="1d68e-135">This example updates a performance counter log file.</span></span>

### <span data-ttu-id="1d68e-136">Exempel 9: importera prestanda logg data från flera filer och spara dem</span><span class="sxs-lookup"><span data-stu-id="1d68e-136">Example 9: Import performance log data from multiple files and then save it</span></span>

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

<span data-ttu-id="1d68e-137">Det här kommandot importerar prestanda logg data från två loggar och sparar data i $Counters-variabeln.</span><span class="sxs-lookup"><span data-stu-id="1d68e-137">This command imports performance log data from two logs and saves the data in the $Counters variable.</span></span>
<span data-ttu-id="1d68e-138">Kommandot använder en pipeline-operator för att skicka prestanda logg Sök vägar till import-Counter, som importerar data från angivna sökvägar.</span><span class="sxs-lookup"><span data-stu-id="1d68e-138">The command uses a pipeline operator to send the performance log paths to Import-Counter, which imports the data from the specified paths.</span></span>

<span data-ttu-id="1d68e-139">Observera att varje sökväg omges av citat tecken och att Sök vägarna skiljs från varandra med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="1d68e-139">Notice that each path is enclosed in quotation marks and that the paths are separated from each other by a comma.</span></span>

## <span data-ttu-id="1d68e-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1d68e-140">PARAMETERS</span></span>

### <span data-ttu-id="1d68e-141">-Counter</span><span class="sxs-lookup"><span data-stu-id="1d68e-141">-Counter</span></span>

<span data-ttu-id="1d68e-142">Anger, som en sträng mat ris, prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="1d68e-142">Specifies, as a string array, the performance counters.</span></span>
<span data-ttu-id="1d68e-143">**Import-Counter** importerar som standard alla data från alla räknare i indatafilerna.</span><span class="sxs-lookup"><span data-stu-id="1d68e-143">By default, **Import-Counter** imports all data from all counters in the input files.</span></span>
<span data-ttu-id="1d68e-144">Ange en eller flera räknar Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="1d68e-144">Enter one or more counter paths.</span></span>
<span data-ttu-id="1d68e-145">Jokertecken är tillåtna i instans delen av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1d68e-145">Wildcards are permitted in the Instance part of the path.</span></span>

<span data-ttu-id="1d68e-146">Varje räknar Sök väg har följande format.</span><span class="sxs-lookup"><span data-stu-id="1d68e-146">Each counter path has the following format.</span></span>
<span data-ttu-id="1d68e-147">Värdet ComputerName måste anges i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1d68e-147">The ComputerName value is required in the path.</span></span>
<span data-ttu-id="1d68e-148">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="1d68e-148">For instance:</span></span>

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

<span data-ttu-id="1d68e-149">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="1d68e-149">For example:</span></span>

- `\\Server01\Processor(2)\% User Time`
- `\\Server01\Processor(*)\% Processor Time`

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: All counter
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1d68e-150">-Slut tid</span><span class="sxs-lookup"><span data-stu-id="1d68e-150">-EndTime</span></span>

<span data-ttu-id="1d68e-151">Anger ett slutdatum och en tidpunkt då denna cmdlet importerar räknar data mellan *StartTime* och den här parameterns tidsstämplar.</span><span class="sxs-lookup"><span data-stu-id="1d68e-151">Specifies an end date and time that this cmdlet imports counter data between the *StartTime* and this parameter timestamps.</span></span>
<span data-ttu-id="1d68e-152">Ange ett **datetime** -objekt, till exempel ett som skapats av Get-Date-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1d68e-152">Enter a **DateTime** object, such as one created by the Get-Date cmdlet.</span></span>
<span data-ttu-id="1d68e-153">**Import-Counter** importerar som standard alla räknar data i filerna som anges i parametern *Path* .</span><span class="sxs-lookup"><span data-stu-id="1d68e-153">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No end time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d68e-154">-ListSet</span><span class="sxs-lookup"><span data-stu-id="1d68e-154">-ListSet</span></span>

<span data-ttu-id="1d68e-155">Anger de prestanda räknar uppsättningar som representeras i de exporterade filerna.</span><span class="sxs-lookup"><span data-stu-id="1d68e-155">Specifies the performance counter sets that are represented in the exported files.</span></span>
<span data-ttu-id="1d68e-156">Kommandon med den här parametern importerar inte några data.</span><span class="sxs-lookup"><span data-stu-id="1d68e-156">Commands with this parameter do not import any data.</span></span>

<span data-ttu-id="1d68e-157">Ange en eller flera räknar uppsättnings namn.</span><span class="sxs-lookup"><span data-stu-id="1d68e-157">Enter one or more counter set names.</span></span>
<span data-ttu-id="1d68e-158">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1d68e-158">Wildcards are permitted.</span></span>
<span data-ttu-id="1d68e-159">Om du vill hämta alla räknar uppsättningar i filen skriver du `Import-Counter -ListSet *` .</span><span class="sxs-lookup"><span data-stu-id="1d68e-159">To get all counter sets in the file, type `Import-Counter -ListSet *`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1d68e-160">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="1d68e-160">-MaxSamples</span></span>

<span data-ttu-id="1d68e-161">Anger det maximala antalet prover för varje räknare som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="1d68e-161">Specifies the maximum number of samples of each counter to import.</span></span>
<span data-ttu-id="1d68e-162">Som standard importerar **Get-Counter** alla data i filerna som anges i parametern *Path* .</span><span class="sxs-lookup"><span data-stu-id="1d68e-162">By default, **Get-Counter** imports all of the data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No maximum
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d68e-163">-Path</span><span class="sxs-lookup"><span data-stu-id="1d68e-163">-Path</span></span>

<span data-ttu-id="1d68e-164">Anger fil Sök vägar för de filer som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="1d68e-164">Specifies the file paths of the files to be imported.</span></span>
<span data-ttu-id="1d68e-165">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="1d68e-165">This parameter is required.</span></span>

<span data-ttu-id="1d68e-166">Ange sökvägen och fil namnet för en,. csv,,. tsv-eller. BLG-fil som du exporterade med hjälp av cmdleten **export-Counter** .</span><span class="sxs-lookup"><span data-stu-id="1d68e-166">Enter the path and file name of a, .csv,, .tsv, or .blg file that you exported by using the **Export-Counter** cmdlet.</span></span>
<span data-ttu-id="1d68e-167">Du kan bara ange en CSV-eller TSV-fil, men du kan ange flera. BLG-filer (upp till 32) i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="1d68e-167">You can specify only one .csv or .tsv file, but you can specify multiple .blg files (up to 32) in each command.</span></span>
<span data-ttu-id="1d68e-168">Du kan också använda fil Sök vägs strängar (inom citat tecken) för att **Importera räknare**.</span><span class="sxs-lookup"><span data-stu-id="1d68e-168">You can also pipe file path strings (in quotation marks) to **Import-Counter**.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="1d68e-169">-StartTime</span><span class="sxs-lookup"><span data-stu-id="1d68e-169">-StartTime</span></span>

<span data-ttu-id="1d68e-170">Anger start datum och-tid då denna cmdlet hämtar räknar data.</span><span class="sxs-lookup"><span data-stu-id="1d68e-170">Specifies the start date and time in which this cmdlet gets counter data.</span></span>
<span data-ttu-id="1d68e-171">Ange ett **datetime** -objekt, till exempel ett som skapats av cmdleten **Get-date** .</span><span class="sxs-lookup"><span data-stu-id="1d68e-171">Enter a **DateTime** object, such as one created by the **Get-Date** cmdlet.</span></span>
<span data-ttu-id="1d68e-172">**Import-Counter** importerar som standard alla räknar data i filerna som anges i parametern *Path* .</span><span class="sxs-lookup"><span data-stu-id="1d68e-172">By default, **Import-Counter** imports all counter data in the files specified by the *Path* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: No start time
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d68e-173">– Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="1d68e-173">-Summary</span></span>

<span data-ttu-id="1d68e-174">Anger att denna cmdlet får en sammanfattning av importerade data, i stället för att hämta enskilda räknar data exempel.</span><span class="sxs-lookup"><span data-stu-id="1d68e-174">Indicates that this cmdlet gets a summary of the imported data, instead of getting individual counter data samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SummarySet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1d68e-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1d68e-175">CommonParameters</span></span>

<span data-ttu-id="1d68e-176">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1d68e-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1d68e-177">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1d68e-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1d68e-178">INDATA</span><span class="sxs-lookup"><span data-stu-id="1d68e-178">INPUTS</span></span>

### <span data-ttu-id="1d68e-179">System. String</span><span class="sxs-lookup"><span data-stu-id="1d68e-179">System.String</span></span>

<span data-ttu-id="1d68e-180">Du kan skicka vidare logg Sök vägar för prestanda räknaren till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1d68e-180">You can pipe performance counter log paths to this cmdlet.</span></span>

## <span data-ttu-id="1d68e-181">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1d68e-181">OUTPUTS</span></span>

### <span data-ttu-id="1d68e-182">Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. commands. GetCounter. CounterSet, Microsoft. PowerShell. commands. GetCounter. CounterFileInfo</span><span class="sxs-lookup"><span data-stu-id="1d68e-182">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo</span></span>

<span data-ttu-id="1d68e-183">Denna cmdlet returnerar en **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet**.</span><span class="sxs-lookup"><span data-stu-id="1d68e-183">This cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**.</span></span>
<span data-ttu-id="1d68e-184">Om du använder parametern *ListSet* returnerar denna cmdlet ett objekt av **Microsoft. PowerShell. commands. GetCounter. CounterSet** .</span><span class="sxs-lookup"><span data-stu-id="1d68e-184">If you use the *ListSet* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterSet** object.</span></span>
<span data-ttu-id="1d68e-185">Om du använder *sammanfattnings* parametern returnerar denna cmdlet ett **Microsoft. PowerShell. commands. GetCounter. CounterFileInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1d68e-185">If you use the *Summary* parameter, this cmdlet returns a **Microsoft.PowerShell.Commands.GetCounter.CounterFileInfo** object.</span></span>

## <span data-ttu-id="1d68e-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1d68e-186">NOTES</span></span>

* <span data-ttu-id="1d68e-187">Denna cmdlet har ingen *computername* -parameter.</span><span class="sxs-lookup"><span data-stu-id="1d68e-187">This cmdlet does not have a *ComputerName* parameter.</span></span> <span data-ttu-id="1d68e-188">Men om datorn har kon figurer ATS för Windows PowerShell-fjärrkommunikation kan du använda Invoke-Command-cmdleten för att köra ett **import-Counter-** kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="1d68e-188">However, if the computer is configured for Windows PowerShell remoting, you can use the Invoke-Command cmdlet to run an **Import-Counter** command on a remote computer.</span></span>

## <span data-ttu-id="1d68e-189">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1d68e-189">RELATED LINKS</span></span>

[<span data-ttu-id="1d68e-190">Exportera – räknare</span><span class="sxs-lookup"><span data-stu-id="1d68e-190">Export-Counter</span></span>](Export-Counter.md)

[<span data-ttu-id="1d68e-191">Hämta räknare</span><span class="sxs-lookup"><span data-stu-id="1d68e-191">Get-Counter</span></span>](Get-Counter.md)
