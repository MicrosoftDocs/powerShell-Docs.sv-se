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
# Import-Counter

## SAMMANFATTNING
Importerar loggfiler för prestanda räknare och skapar de objekt som representerar varje räknar exempel i loggen.

## SYNTAX

### GetCounterSet (standard)

```
Import-Counter [-Path] <String[]> [-StartTime <DateTime>] [-EndTime <DateTime>] [-Counter <String[]>]
 [-MaxSamples <Int64>] [<CommonParameters>]
```

### ListSetSet

```
Import-Counter [-Path] <String[]> -ListSet <String[]> [<CommonParameters>]
```

### SummarySet

```
Import-Counter [-Path] <String[]> [-Summary] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **import-Counter** importerar prestanda räknar data från loggfiler för prestanda räknare och skapar objekt för varje räknar exempel i filen.
**PerformanceCounterSampleSet** -objekten som den skapar är identiska med de objekt som **erhåller Counter** returnerar när de samlar in prestanda räknar data.

Du kan importera data från filer med kommaavgränsade värden (. csv), tabbavgränsade värde (. tsv) och prestanda logg för binär prestanda logg (. blg).
Om du använder. BLG-filer kan du importera upp till 32 filer i varje kommando.
Du kan använda parametrarna för **import-Counter** för att filtrera de data som du importerar.

Tillsammans med Get-Counter-och Export-Counter-cmdletar kan du använda den här funktionen för att samla in, exportera, importera, kombinera, filtrera, ändra och exportera prestanda räknar data på nytt i Windows PowerShell.

## EXEMPEL

### Exempel 1: importera alla räknar data från en fil

```powershell
$Data = Import-Counter -Path ProcessorData.csv
```

Det här kommandot importerar alla räknar data från ProcessorData.csv-filen till $Data-variabeln.

### Exempel 2: importera vissa räknar data från en fil

```
PS C:\> $I = Import-Counter -Path "ProcessorData.blg" -Counter "\\SERVER01\Processor(_Total)\Interrupts/sec"
```

Det här kommandot importerar bara räknar data för **"processor (_Total) \ avbrott/s"** från ProcessorData. blg-filen till $I-variabeln.

### Exempel 3: Välj data från en prestanda räknare och exportera den till en fil

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

Det här exemplet visar hur du väljer data från en prestanda räknar logg fil (. blg) och sedan exporterar de markerade data till en. csv-fil.
De första fyra kommandona hämtar räknar Sök vägarna från filen och sparar dem i variabeln med namnet $Data.
De två sista kommandona importerar markerade data och exporterar bara de valda data.

### Exempel 4: Visa alla räknar Sök vägar i en grupp med importerade räknar uppsättningar

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

Det här exemplet visar hur du visar alla räknar Sök vägar i en grupp med importerade räknar uppsättningar.

### Exempel 5: importera räknar data från ett intervall med tidsstämplar

```
The first command lists in a table the time stamps of all of the data in the ProcessorData.blg file.
PS C:\> Import-Counter -Path ".\disk.blg" | Format-Table -Property Timestamp

The second command saves particular time stamps in the $Start and $End variables. The strings are cast to **DateTime** objects.
PS C:\> $Start = [datetime]"7/9/2008 3:47:00 PM"; $End = [datetime]"7/9/2008 3:47:59 PM"

The third command uses the **Import-Counter** cmdlet to get only counter data that has a time stamp between the start and end times (inclusive). The command uses the *StartTime* and *EndTime* parameters of **Import-Counter** to specify the range.
PS C:\> Import-Counter -Path Disk.blg -StartTime $start -EndTime $end
```

I det här exemplet importeras bara räknar data som har en tidsstämpel mellan de start intervall som anges i kommandot.

### Exempel 6: importera ett angivet antal av de äldsta exemplen från en prestanda räknar logg fil

```
The first command uses the **Import-Counter** cmdlet to import the first (oldest) five samples from the Disk.blg file. The command uses the *MaxSamples* parameter to limit the import to five counter samples.
PS C:\> Import-Counter -Path "Disk.blg" -MaxSamples 5

The second command uses array notation and the Windows PowerShell range operator (..) to get the last five counter samples from the file. These are the five newest samples.
PS C:\> (Import-Counter -Path Disk.blg)[-1 .. -5]
```

I det här exemplet visas hur du importerar de fem äldsta och fem senaste exemplen från en prestanda räknar logg fil.

### Exempel 7: Hämta en sammanfattning av räknar data från en fil

```
PS C:\> Import-Counter "D:\Samples\Memory.blg" -Summary

OldestRecord            NewestRecord            SampleCount
------------            ------------            -----------
7/10/2008 2:59:18 PM    7/10/2008 3:00:27 PM    1000
```

Detta kommando använder *sammanfattnings* parametern för cmdleten **import-Counter** för att få en översikt över räknar data i filen Memory. blg.

### Exempel 8: uppdatera en prestanda räknar logg fil

```
The first command uses the *ListSet* parameter of **Import-Counter** to get the counters in OldData.blg, an existing counter log file. The command uses a pipeline operator (|) to send the data to a ForEach-Object command that gets only the values of the **PathsWithInstances** property of each object
PS C:\> $Counters = Import-Counter OldData.blg -ListSet * | ForEach-Object {$_.PathsWithInstances}

The second command gets updated data for the counters in the $Counters variable. It uses the Get-Counter cmdlet to get a current sample, and then export the results to the NewData.blg file.
PS C:\> Get-Counter -Counter $Counters -MaxSamples 20 | Export-Counter C:\Logs\NewData.blg
```

Det här exemplet uppdaterar en logg fil för prestanda räknaren.

### Exempel 9: importera prestanda logg data från flera filer och spara dem

```
PS C:\> $Counters = "D:\test\pdata.blg", "D:\samples\netlog.blg" | Import-Counter
```

Det här kommandot importerar prestanda logg data från två loggar och sparar data i $Counters-variabeln.
Kommandot använder en pipeline-operator för att skicka prestanda logg Sök vägar till import-Counter, som importerar data från angivna sökvägar.

Observera att varje sökväg omges av citat tecken och att Sök vägarna skiljs från varandra med kommatecken.

## PARAMETRAR

### -Counter

Anger, som en sträng mat ris, prestanda räknare.
**Import-Counter** importerar som standard alla data från alla räknare i indatafilerna.
Ange en eller flera räknar Sök vägar.
Jokertecken är tillåtna i instans delen av sökvägen.

Varje räknar Sök väg har följande format.
Värdet ComputerName måste anges i sökvägen.
Till exempel:

- `\\<ComputerName>\<CounterSet>(<Instance>)\<CounterName>`

Ett exempel:

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

### -Slut tid

Anger ett slutdatum och en tidpunkt då denna cmdlet importerar räknar data mellan *StartTime* och den här parameterns tidsstämplar.
Ange ett **datetime** -objekt, till exempel ett som skapats av Get-Date-cmdleten.
**Import-Counter** importerar som standard alla räknar data i filerna som anges i parametern *Path* .

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

### -ListSet

Anger de prestanda räknar uppsättningar som representeras i de exporterade filerna.
Kommandon med den här parametern importerar inte några data.

Ange en eller flera räknar uppsättnings namn.
Jokertecken är tillåtna.
Om du vill hämta alla räknar uppsättningar i filen skriver du `Import-Counter -ListSet *` .

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

### -MaxSamples

Anger det maximala antalet prover för varje räknare som ska importeras.
Som standard importerar **Get-Counter** alla data i filerna som anges i parametern *Path* .

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

### -Path

Anger fil Sök vägar för de filer som ska importeras.
Den här parametern är obligatorisk.

Ange sökvägen och fil namnet för en,. csv,,. tsv-eller. BLG-fil som du exporterade med hjälp av cmdleten **export-Counter** .
Du kan bara ange en CSV-eller TSV-fil, men du kan ange flera. BLG-filer (upp till 32) i varje kommando.
Du kan också använda fil Sök vägs strängar (inom citat tecken) för att **Importera räknare**.

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

### -StartTime

Anger start datum och-tid då denna cmdlet hämtar räknar data.
Ange ett **datetime** -objekt, till exempel ett som skapats av cmdleten **Get-date** .
**Import-Counter** importerar som standard alla räknar data i filerna som anges i parametern *Path* .

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

### – Sammanfattning

Anger att denna cmdlet får en sammanfattning av importerade data, i stället för att hämta enskilda räknar data exempel.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare logg Sök vägar för prestanda räknaren till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. commands. GetCounter. CounterSet, Microsoft. PowerShell. commands. GetCounter. CounterFileInfo

Denna cmdlet returnerar en **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet**.
Om du använder parametern *ListSet* returnerar denna cmdlet ett objekt av **Microsoft. PowerShell. commands. GetCounter. CounterSet** .
Om du använder *sammanfattnings* parametern returnerar denna cmdlet ett **Microsoft. PowerShell. commands. GetCounter. CounterFileInfo** -objekt.

## ANTECKNINGAR

* Denna cmdlet har ingen *computername* -parameter. Men om datorn har kon figurer ATS för Windows PowerShell-fjärrkommunikation kan du använda Invoke-Command-cmdleten för att köra ett **import-Counter-** kommando på en fjärrdator.

## RELATERADE LÄNKAR

[Exportera – räknare](Export-Counter.md)

[Hämta räknare](Get-Counter.md)
