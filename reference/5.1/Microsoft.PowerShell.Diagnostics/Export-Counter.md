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
# Export-Counter

## SAMMANFATTNING
Exporterar prestanda räknar data till loggfiler.

## SYNTAX

```
Export-Counter [-Path] <String> [-FileFormat <String>] [-MaxSize <UInt32>]
 -InputObject <PerformanceCounterSampleSet[]> [-Force] [-Circular] [<CommonParameters>]
```

## BESKRIVNING

`Export-Counter`Cmdleten exporterar prestanda räknar data (PerformanceCounterSampleSet-objekt) till loggfiler i binär prestanda logg (. blg), kommaavgränsade värden (. csv) eller tabbavgränsade värde format (. tsv). Du kan använda den här cmdleten för att logga prestanda räknar data.

`Export-Counter`Cmdlet: en är utformad för att exportera data som returneras av `Get-Counter` `Import-Counter` cmdletarna och.

Denna cmdlet körs bara på Windows 7, Windows Server 2008 R2 och senare versioner av Windows.

## EXEMPEL

### EXEMPEL 1: exportera räknar data till en fil

I det här exemplet exporteras räknar data till en BLG-fil.

```powershell
Get-Counter "\Processor(*)\% Processor Time" | Export-Counter -Path $home\Counters.blg
```

Kommandot använder `Get-Counter` cmdleten för att samla in processor tids data. En pipeline-operator (|) används för att skicka data till `Export-Counter` cmdlet: en. `Export-Counter`Kommandot använder **Path** -variabeln för att ange utdatafilen.

Eftersom data uppsättningen kan vara mycket stor skickar det här exemplet data till `Export-Counter` via pipelinen. Om data har sparats i en variabel kan du använda en oproportionerlig mängd minne.

### Exempel 2: exportera en fil till ett räknar fil format

I det här exemplet konverteras en CSV-fil till ett räknar data BLG-format.

`Import-Counter`Cmdleten importerar prestanda räknar data från `Threads.csv` filen. Exemplet förutsätter att den här filen har exporter ATS tidigare med hjälp av `Export-Counter` cmdleten. En pipeline-operator ( `|` ) skickar importerade data till `Export-Counter` cmdleten. Kommandot använder parametern **Path** för att ange platsen för utdatafilen. Den använder parametrarna **cirkulär** och **MaxSize** för att dirigera `Export-Counter` cmdleten för att skapa en cirkel logg som bryts vid 1 GB. Parametern **MaxSize** uttrycks i megabyte.

```powershell
$1GBInMB = 1024 # 1GB = 1024MB
Import-Counter Threads.csv | Export-Counter -Path ThreadTest.blg -Circular -MaxSize $1GBInMB
```

### Exempel 3: Hämta räknar data från en fjärrdator och spara data till en fil

Det här exemplet visar hur du hämtar prestanda räknar data från en fjärrdator och sparar data i en fil på fjärrdatorn.

Det första kommandot använder `Get-Counter` cmdleten för att samla in räknar data från Server01, en fjärrdator. Kommandot sparar data i `$C` variabeln.

Det andra kommandot använder en pipeline-operator ( `|` ) för att skicka data `$C` till `Export-Counter` cmdleten, som sparar den i `Workingset.blg` filen i den Server01 datorns prestanda resurs.

```powershell
$C = Get-Counter -ComputerName Server01 -Counter "\Process(*)\Working Set - Private" -MaxSamples $C | Export-Counter -Path \\Server01\Perf\WorkingSet.blg
```

```Output
20
```

### Exempel 4: Logga befintliga data på nytt

Det här exemplet visar hur du använder `Import-Counter` `Export-Counter` -och-cmdletarna för att logga befintliga data på nytt.

Det första kommandot använder `Import-Counter` cmdleten för att importera prestanda räknar data från DiskSpace. blg-loggen. Data i `$All` variabeln sparas. Den här filen innehåller exempel på \% räknaren "logisk disk ledigt utrymme" på fler än 200 fjärrdatorer i företaget.

Det andra kommandot använder `Where-Object` cmdleten för att välja objekt med **CookedValue** på mindre än 15 (procent). Kommandot sparar resultatet i `$LowSpace` variabeln.

Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka data i `$LowSpace` variabeln till `Export-Counter` cmdleten. Kommandot använder parametern **Path** för att ange att de valda data ska loggas i LowDiskSpace. blg-filen.

```powershell
$All = Import-Counter DiskSpace.blg
$LowSpace = $All | Where-Object {$_.CounterSamples.CookedValue -lt 15}
$LowSpace | Export-Counter -Path LowDiskSpace.blg
```

## PARAMETRAR

### – Cirkulär

Anger att utdatafilen är en cirkel logg med FIFO-formatet först in, först ut.
När du tar med den här parametern krävs parametern **MaxSize** .

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

### -FileFormat

Anger utdataformatet för logg filen.

De acceptabla värdena för den här parametern är:

- CSV
- TSV
- BLG

Standardvärdet är BLG.

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

### -Force

Skriver över och ersätter en befintlig fil om en sådan finns på den plats som anges av **Sök vägs** parametern.

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

### – InputObject

Anger, som en matris, de räknar data som ska exporteras. Ange en variabel som innehåller data eller ett kommando som hämtar data, t `Get-Counter` . ex. eller- `Import-Counter` cmdlet.

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

### -MaxSize

Anger den maximala storleken på utdatafilen i megabyte (MB).

Om du anger en **cirkulär** parameter tas de äldsta posterna bort när logg filen når den angivna maximala storleken. Om den **cirkulära** parametern inte anges och logg filen når den angivna maximala storleken, läggs inga nya data till och cmdleten genererar ett icke-avslutande fel.

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

### -Path

Anger sökvägen och fil namnet för utdatafilen. Ange en relativ eller absolut sökväg på den lokala datorn eller en UNC-sökväg (Uniform Naming Convention) till en fjärran sluten dator, till exempel `\\Computer\Share\file.blg` . Den här parametern är obligatorisk.

Fil formatet bestäms av värdet för parametern **FileFormat** , inte av fil namns tillägget i sökvägen.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet

Du kan skicka information om prestanda räknare från `Get-Counter` eller `Import-Counter` till denna cmdlet.

## UTDATA

### Inget

## ANTECKNINGAR

Logg fils generatorn förväntar sig att alla indata-objekt har samma räknar Sök väg och att objekten är ordnade i stigande tids ordning.

Räknar typen och sökvägen för det första indata-objektet avgör vilka egenskaper som registreras i logg filen. Om andra inobjekt inte har något värde för en inspelad egenskap är egenskaps fältet tomt. Om objekten har egenskaps värden som inte har registrerats ignoreras extra egenskaps värden.

Prestanda övervakaren kanske inte kan läsa alla loggar som `Export-Counter` genererar. Till exempel kräver prestanda övervakaren att alla objekt har samma sökväg och att alla objekt skiljs åt av samma tidsintervall.

`Import-Counter`Cmdleten har ingen **computername** -parameter. Om datorn däremot har kon figurer ATS för Windows PowerShell i Windows PowerShell kan du använda `Invoke-Command` cmdleten för att köra ett `Import-Counter` kommando på en fjärrdator.

## RELATERADE LÄNKAR

[Hämta räknare](Get-Counter.md)

[Importera – räknare](Import-Counter.md)
