---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 10/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/export-counter?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Counter
ms.openlocfilehash: 54498eb504a1d13a5b96a2583b5e5d6e4c08735e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270105"
---
# <span data-ttu-id="ef7ca-103">Export-Counter</span><span class="sxs-lookup"><span data-stu-id="ef7ca-103">Export-Counter</span></span>

## <span data-ttu-id="ef7ca-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ef7ca-104">SYNOPSIS</span></span>
<span data-ttu-id="ef7ca-105">Exporterar prestanda räknar data till loggfiler.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-105">Exports performance counter data to log files.</span></span>

## <span data-ttu-id="ef7ca-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ef7ca-106">SYNTAX</span></span>

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## <span data-ttu-id="ef7ca-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ef7ca-107">DESCRIPTION</span></span>

<span data-ttu-id="ef7ca-108">`Export-Counter`Cmdleten exporterar prestanda räknar data (PerformanceCounterSampleSet-objekt) till loggfiler i binär prestanda logg (. blg), kommaavgränsade värden (. csv) eller tabbavgränsade värde format (. tsv).</span><span class="sxs-lookup"><span data-stu-id="ef7ca-108">The `Export-Counter` cmdlet exports performance counter data (PerformanceCounterSampleSet objects) to log files in binary performance log (.blg), comma-separated value (.csv), or tab-separated value (.tsv) format.</span></span> <span data-ttu-id="ef7ca-109">Du kan använda den här cmdleten för att logga prestanda räknar data.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-109">You use this cmdlet to log performance counter data.</span></span>

<span data-ttu-id="ef7ca-110">`Export-Counter`Cmdlet: en är utformad för att exportera data som returneras av `Get-Counter` `Import-Counter` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-110">The `Export-Counter` cmdlet is designed to export data that is returned by the `Get-Counter` and `Import-Counter` cmdlets.</span></span>

<span data-ttu-id="ef7ca-111">Denna cmdlet körs bara på Windows 7, Windows Server 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-111">This cmdlet runs only on Windows 7, Windows Server 2008 R2, and later versions of Windows.</span></span>

## <span data-ttu-id="ef7ca-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ef7ca-112">EXAMPLES</span></span>

### <span data-ttu-id="ef7ca-113">EXEMPEL 1: exportera räknar data till en fil</span><span class="sxs-lookup"><span data-stu-id="ef7ca-113">EXAMPLE 1: Export counter data to a file</span></span>

<span data-ttu-id="ef7ca-114">I det här exemplet exporteras räknar data till en BLG-fil.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-114">This example exports counter data to a BLG file.</span></span>

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

<span data-ttu-id="ef7ca-115">Kommandot använder `Get-Counter` cmdleten för att samla in processor tids data.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-115">The command uses the `Get-Counter` cmdlet to collect processor time data.</span></span> <span data-ttu-id="ef7ca-116">En pipeline-operator (|) används för att skicka data till `Export-Counter` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-116">It uses a pipeline operator (|) to send the data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="ef7ca-117">`Export-Counter`Kommandot använder **Path** -variabeln för att ange utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-117">The `Export-Counter` command uses the **Path** variable to specify the output file.</span></span>

<span data-ttu-id="ef7ca-118">Eftersom data uppsättningen kan vara mycket stor skickar det här exemplet data till `Export-Counter` via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-118">Because the data set might be very large, this example sends the data to `Export-Counter` through the pipeline.</span></span> <span data-ttu-id="ef7ca-119">Om data har sparats i en variabel kan du använda en oproportionerlig mängd minne.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-119">If the data were saved in a variable, you might use a disproportionate amount of memory.</span></span>

### <span data-ttu-id="ef7ca-120">Exempel 2: exportera en fil till ett räknar fil format</span><span class="sxs-lookup"><span data-stu-id="ef7ca-120">Example 2: Export a file to a counter file format</span></span>

<span data-ttu-id="ef7ca-121">I det här exemplet konverteras en CSV-fil till ett räknar data BLG-format.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-121">This example converts a CSV file to a counter data BLG format.</span></span>

<span data-ttu-id="ef7ca-122">`Import-Counter`Cmdleten importerar prestanda räknar data från `Threads.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-122">The `Import-Counter` cmdlet imports performance counter data from the `Threads.csv` file.</span></span> <span data-ttu-id="ef7ca-123">Exemplet förutsätter att den här filen har exporter ATS tidigare med hjälp av `Export-Counter` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-123">The example presumes that this file was previously exported by using the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="ef7ca-124">En pipeline-operator ( `|` ) skickar importerade data till `Export-Counter` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-124">A pipeline operator (`|`) sends the imported data to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="ef7ca-125">Kommandot använder parametern **Path** för att ange platsen för utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-125">The command uses the **Path** parameter to specify the location of the output file.</span></span> <span data-ttu-id="ef7ca-126">Den använder parametrarna **cirkulär** och **MaxSize** för att dirigera `Export-Counter` cmdleten för att skapa en cirkel logg som bryts vid 1 GB.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-126">It uses the **Circular** and **MaxSize** parameters to direct the `Export-Counter` cmdlet to create a circular log that wraps at 1 GB.</span></span> <span data-ttu-id="ef7ca-127">Parametern **MaxSize** uttrycks i megabyte.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-127">The **MaxSize** parameter is expressed in megabytes.</span></span>

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### <span data-ttu-id="ef7ca-128">Exempel 3: Hämta räknar data från en fjärrdator och spara data till en fil</span><span class="sxs-lookup"><span data-stu-id="ef7ca-128">Example 3: Get counter data from a remote computer and save the data to a file</span></span>

<span data-ttu-id="ef7ca-129">Det här exemplet visar hur du hämtar prestanda räknar data från en fjärrdator och sparar data i en fil på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-129">This example shows how to get performance counter data from a remote computer and save the data in a file on the remote computer.</span></span>

<span data-ttu-id="ef7ca-130">Det första kommandot använder `Get-Counter` cmdleten för att samla in räknar data från Server01, en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-130">The first command uses the `Get-Counter` cmdlet to collect working set counter data from Server01, a remote computer.</span></span> <span data-ttu-id="ef7ca-131">Kommandot sparar data i `$C` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-131">The command saves the data in the `$C` variable.</span></span>

<span data-ttu-id="ef7ca-132">Det andra kommandot använder en pipeline-operator ( `|` ) för att skicka data `$C` till `Export-Counter` cmdleten, som sparar den i `Workingset.blg` filen i den Server01 datorns prestanda resurs.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-132">The second command uses a pipeline operator (`|`) to send the data in `$C` to the `Export-Counter` cmdlet, which saves it in the `Workingset.blg` file in the Perf share of the Server01 computer.</span></span>

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### <span data-ttu-id="ef7ca-133">Exempel 4: Logga befintliga data på nytt</span><span class="sxs-lookup"><span data-stu-id="ef7ca-133">Example 4: Re-log existing data</span></span>

<span data-ttu-id="ef7ca-134">Det här exemplet visar hur du använder `Import-Counter` `Export-Counter` -och-cmdletarna för att logga befintliga data på nytt.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-134">This example shows how to use the `Import-Counter` and `Export-Counter` cmdlets to re-log existing data.</span></span>

<span data-ttu-id="ef7ca-135">Det första kommandot använder `Import-Counter` cmdleten för att importera prestanda räknar data från DiskSpace. blg-loggen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-135">The first command uses the `Import-Counter` cmdlet to import performance counter data from the DiskSpace.blg log.</span></span> <span data-ttu-id="ef7ca-136">Data i `$All` variabeln sparas.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-136">It saves the data in the `$All` variable.</span></span> <span data-ttu-id="ef7ca-137">Den här filen innehåller exempel på \% räknaren "logisk disk ledigt utrymme" på fler än 200 fjärrdatorer i företaget.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-137">This file contains samples of the "LogicalDisk\% Free Space" counter on more than 200 remote computers in the enterprise.</span></span>

<span data-ttu-id="ef7ca-138">Det andra kommandot använder `Where-Object` cmdleten för att välja objekt med **CookedValue** på mindre än 15 (procent).</span><span class="sxs-lookup"><span data-stu-id="ef7ca-138">The second command uses the `Where-Object` cmdlet to select objects with **CookedValue** of less than 15 (percent).</span></span> <span data-ttu-id="ef7ca-139">Kommandot sparar resultatet i `$LowSpace` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-139">The command saves the results in the `$LowSpace` variable.</span></span>

<span data-ttu-id="ef7ca-140">Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka data i `$LowSpace` variabeln till `Export-Counter` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-140">The third command uses a pipeline operator (`|`) to send the data in the `$LowSpace` variable to the `Export-Counter` cmdlet.</span></span> <span data-ttu-id="ef7ca-141">Kommandot använder parametern **Path** för att ange att de valda data ska loggas i LowDiskSpace. blg-filen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-141">The command uses the **Path** parameter to indicate that the selected data should be logged in the LowDiskSpace.blg file.</span></span>

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## <span data-ttu-id="ef7ca-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ef7ca-142">PARAMETERS</span></span>

### <span data-ttu-id="ef7ca-143">– Cirkulär</span><span class="sxs-lookup"><span data-stu-id="ef7ca-143">-Circular</span></span>

<span data-ttu-id="ef7ca-144">Anger att utdatafilen är en cirkel logg med FIFO-formatet först in, först ut.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-144">Indicates that the output file is a circular log with first in, first out (FIFO) format.</span></span>
<span data-ttu-id="ef7ca-145">När du tar med den här parametern krävs parametern **MaxSize** .</span><span class="sxs-lookup"><span data-stu-id="ef7ca-145">When you include this parameter, the **MaxSize** parameter is required.</span></span>

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

### <span data-ttu-id="ef7ca-146">-FileFormat</span><span class="sxs-lookup"><span data-stu-id="ef7ca-146">-FileFormat</span></span>

<span data-ttu-id="ef7ca-147">Anger utdataformatet för logg filen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-147">Specifies the output format of the output log file.</span></span>

<span data-ttu-id="ef7ca-148">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ef7ca-148">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ef7ca-149">CSV</span><span class="sxs-lookup"><span data-stu-id="ef7ca-149">CSV</span></span>
- <span data-ttu-id="ef7ca-150">TSV</span><span class="sxs-lookup"><span data-stu-id="ef7ca-150">TSV</span></span>
- <span data-ttu-id="ef7ca-151">BLG</span><span class="sxs-lookup"><span data-stu-id="ef7ca-151">BLG</span></span>

<span data-ttu-id="ef7ca-152">Standardvärdet är BLG.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-152">The default value is BLG.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef7ca-153">-Force</span><span class="sxs-lookup"><span data-stu-id="ef7ca-153">-Force</span></span>

<span data-ttu-id="ef7ca-154">Skriver över och ersätter en befintlig fil om en sådan finns på den plats som anges av **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-154">Overwrites and replaces an existing file if one exists in the location specified by the **Path** parameter.</span></span>

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

### <span data-ttu-id="ef7ca-155">– InputObject</span><span class="sxs-lookup"><span data-stu-id="ef7ca-155">-InputObject</span></span>

<span data-ttu-id="ef7ca-156">Anger, som en matris, de räknar data som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-156">Specifies, as an array, the counter data to export.</span></span> <span data-ttu-id="ef7ca-157">Ange en variabel som innehåller data eller ett kommando som hämtar data, t `Get-Counter` . ex. eller- `Import-Counter` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-157">Enter a variable that contains the data or a command that gets the data, such as the `Get-Counter` or `Import-Counter` cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ef7ca-158">-MaxSize</span><span class="sxs-lookup"><span data-stu-id="ef7ca-158">-MaxSize</span></span>

<span data-ttu-id="ef7ca-159">Anger den maximala storleken på utdatafilen i megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="ef7ca-159">Specifies the maximum size of the output file in megabytes (MB).</span></span>

<span data-ttu-id="ef7ca-160">Om du anger en **cirkulär** parameter tas de äldsta posterna bort när logg filen når den angivna maximala storleken.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-160">If the **Circular** parameter is specified, then when the log file reaches the specified maximum size, the oldest entries are deleted as newer ones are added.</span></span> <span data-ttu-id="ef7ca-161">Om den **cirkulära** parametern inte anges och logg filen når den angivna maximala storleken, läggs inga nya data till och cmdleten genererar ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-161">If the **Circular** parameter is not specified, then when the log file reaches the specified maximum size, no new data is added and the cmdlet generates a non-terminating error.</span></span>

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ef7ca-162">-Path</span><span class="sxs-lookup"><span data-stu-id="ef7ca-162">-Path</span></span>

<span data-ttu-id="ef7ca-163">Anger sökvägen och fil namnet för utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-163">Specifies the path and file name of the output file.</span></span> <span data-ttu-id="ef7ca-164">Ange en relativ eller absolut sökväg på den lokala datorn eller en UNC-sökväg (Uniform Naming Convention) till en fjärran sluten dator, till exempel `\\Computer\Share\file.blg` .</span><span class="sxs-lookup"><span data-stu-id="ef7ca-164">Enter a relative or absolute path on the local computer, or a Uniform Naming Convention (UNC) path to a remote computer, such as `\\Computer\Share\file.blg`.</span></span> <span data-ttu-id="ef7ca-165">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-165">This parameter is required.</span></span>

<span data-ttu-id="ef7ca-166">Fil formatet bestäms av värdet för parametern **FileFormat** , inte av fil namns tillägget i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-166">The file format is determined by the value of the **FileFormat** parameter, not by the file name extension in the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ef7ca-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ef7ca-167">CommonParameters</span></span>

<span data-ttu-id="ef7ca-168">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ef7ca-169">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ef7ca-169">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ef7ca-170">INDATA</span><span class="sxs-lookup"><span data-stu-id="ef7ca-170">INPUTS</span></span>

### <span data-ttu-id="ef7ca-171">Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet</span><span class="sxs-lookup"><span data-stu-id="ef7ca-171">Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet</span></span>

<span data-ttu-id="ef7ca-172">Du kan skicka information om prestanda räknare från `Get-Counter` eller `Import-Counter` till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-172">You can pipe performance counter data from `Get-Counter` or `Import-Counter` to this cmdlet.</span></span>

## <span data-ttu-id="ef7ca-173">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ef7ca-173">OUTPUTS</span></span>

### <span data-ttu-id="ef7ca-174">Inget</span><span class="sxs-lookup"><span data-stu-id="ef7ca-174">None</span></span>

## <span data-ttu-id="ef7ca-175">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ef7ca-175">NOTES</span></span>

<span data-ttu-id="ef7ca-176">Logg fils generatorn förväntar sig att alla indata-objekt har samma räknar Sök väg och att objekten är ordnade i stigande tids ordning.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-176">The log file generator expects that all input objects have the same counter path and that the objects are arranged in ascending time order.</span></span>

<span data-ttu-id="ef7ca-177">Räknar typen och sökvägen för det första indata-objektet avgör vilka egenskaper som registreras i logg filen.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-177">The counter type and path of the first input object determines the properties recorded in the log file.</span></span> <span data-ttu-id="ef7ca-178">Om andra inobjekt inte har något värde för en inspelad egenskap är egenskaps fältet tomt.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-178">If other input objects do not have a value for a recorded property, the property field is empty.</span></span> <span data-ttu-id="ef7ca-179">Om objekten har egenskaps värden som inte har registrerats ignoreras extra egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-179">If the objects have property values that were not recorded, the extra property values are ignored.</span></span>

<span data-ttu-id="ef7ca-180">Prestanda övervakaren kanske inte kan läsa alla loggar som `Export-Counter` genererar.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-180">Performance Monitor might not be able to read all logs that `Export-Counter` generates.</span></span> <span data-ttu-id="ef7ca-181">Till exempel kräver prestanda övervakaren att alla objekt har samma sökväg och att alla objekt skiljs åt av samma tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-181">For instance, Performance Monitor requires that all objects have the same path and that all objects are separated by the same time interval.</span></span>

<span data-ttu-id="ef7ca-182">`Import-Counter`Cmdleten har ingen **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-182">The `Import-Counter` cmdlet does not have a **ComputerName** parameter.</span></span> <span data-ttu-id="ef7ca-183">Om datorn däremot har kon figurer ATS för Windows PowerShell i Windows PowerShell kan du använda `Invoke-Command` cmdleten för att köra ett `Import-Counter` kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="ef7ca-183">However, if the computer is configured for remote Windows PowerShell Windows PowerShell, you can use the `Invoke-Command` cmdlet to run an `Import-Counter` command on a remote computer.</span></span>

## <span data-ttu-id="ef7ca-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ef7ca-184">RELATED LINKS</span></span>

[<span data-ttu-id="ef7ca-185">Hämta räknare</span><span class="sxs-lookup"><span data-stu-id="ef7ca-185">Get-Counter</span></span>](Get-Counter.md)

[<span data-ttu-id="ef7ca-186">Importera – räknare</span><span class="sxs-lookup"><span data-stu-id="ef7ca-186">Import-Counter</span></span>](Import-Counter.md)
