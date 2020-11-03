---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/21/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Csv
ms.openlocfilehash: b2ef2f069c6b5527e2425e3d8adc96d707c65553
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267512"
---
# ConvertFrom-Csv

## SAMMANFATTNING
Konverterar objekt egenskaper i CSV-format (kommaavgränsat värde) till CSV-versioner av de ursprungliga objekten.

## SYNTAX

### Avgränsare (standard)

```
ConvertFrom-Csv [[-Delimiter] <Char>] [-InputObject] <PSObject[]> [-Header <String[]>]
 [<CommonParameters>]
```

### UseCulture

```
ConvertFrom-Csv -UseCulture [-InputObject] <PSObject[]> [-Header <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertFrom-Csv`Cmdleten skapar objekt från CSV-strängar med varierande längd som genereras av `ConvertTo-Csv` cmdleten.

Du kan använda parametrarna för denna cmdlet för att ange kolumn rubrik raden, som bestämmer de resulterande objektens egenskaps namn, för att ange objekt avgränsare eller för att dirigera denna cmdlet till att använda List avgränsaren för den aktuella kulturen som avgränsare.

De objekt som `ConvertFrom-Csv` skapar är CSV-versioner av de ursprungliga objekten. Egenskaps värden för CSV-objekten är sträng versioner av egenskapsvärdena för de ursprungliga objekten. CSV-versionerna av objekten har inga metoder.

Du kan också använda `Export-Csv` `Import-Csv` cmdletarna och för att konvertera objekt till CSV-strängar i en fil (och tillbaka). Dessa cmdletar är desamma som `ConvertTo-Csv` -och `ConvertFrom-Csv` -cmdletarna, förutom att de sparar CSV-strängarna i en fil.

## EXEMPEL

### Exempel 1: konvertera processer på den lokala datorn till CSV-format

Det här exemplet visar hur du konverterar processerna på den lokala datorn till CSV-format och sedan återställer dem till objekt formulär.

```powershell
$P = Get-Process | ConvertTo-Csv
$P | ConvertFrom-Csv
```

`Get-Process`Cmdlet: en skickar de processer som ligger i pipeline till `ConvertTo-Csv` . `ConvertTo-Csv`Cmdleten konverterar process objekt till en serie CSV-strängar. `ConvertFrom-Csv`Cmdleten KONVERTERAR CSV-strängarna till CSV-versioner av de ursprungliga process objekt. CSV-strängarna sparas i `$P` variabeln.

### Exempel 2: konvertera ett data objekt till CSV-format och sedan till CSV-objekt format

Det här exemplet visar hur du konverterar ett data objekt till CSV-format och sedan till CSV-format.

```powershell
$Date = Get-Date | ConvertTo-Csv -Delimiter ';'
ConvertFrom-Csv -InputObject $Date -Delimiter ';'
```

Det första kommandot använder `Get-Date` för att skicka aktuellt datum och tid nedåt i pipeline till `ConvertTo-Csv` . `ConvertTo-Csv`Cmdleten konverterar date-objektet till en serie CSV-strängar.
Parametern **delimiter** används för att ange en semikolone-avgränsare. Strängarna sparas i `$Date` variabeln.

### Exempel 3: Använd parametern header för att ändra namn på egenskaper

Det här exemplet visar hur du använder parametern **header** i `ConvertFrom-Csv` för att ändra namn på egenskaper i det resulterande importerade objektet.

```powershell
$J = Start-Job -ScriptBlock { Get-Process } | ConvertTo-Csv  -NoTypeInformation
$Header = 'State', 'MoreData', 'StatusMessage', 'Location', 'Command', 'StateInfo', 'Finished', 'InstanceId', 'Id', 'Name', 'ChildJobs', 'BeginTime', 'EndTime', 'JobType', 'Output', 'Error', 'Progress', 'Verbose', 'Debug', 'Warning', 'Information'
# Delete the default header from $J
$J = $J[1..($J.count - 1)]
$J | ConvertFrom-Csv -Header $Header
```

```Output
State         : Running
MoreData      : True
StatusMessage :
Location      : localhost
Command       : Get-Process
StateInfo     : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : a259eb63-6824-4b97-a033-305108ae1c2e
Id            : 1
Name          : Job1
ChildJobs     : System.Collections.Generic.List`1[System.Management.Automation.Job]
BeginTime     : 12/20/2018 18:59:57
EndTime       :
JobType       : BackgroundJob
Output        : System.Management.Automation.PSDataCollection`1[System.Management.Automation.PSObject]
Error         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ErrorRecord]
Progress      : System.Management.Automation.PSDataCollection`1[System.Management.Automation.ProgressRecord]
Verbose       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.VerboseRecord]
Debug         : System.Management.Automation.PSDataCollection`1[System.Management.Automation.DebugRecord]
Warning       : System.Management.Automation.PSDataCollection`1[System.Management.Automation.WarningRecord]
Information   : System.Management.Automation.PSDataCollection`1[System.Management.Automation.InformationRecord]
```

`Start-Job`Cmdleten startar ett bakgrunds jobb som kör `Get-Process` . Ett jobb objekt skickas ned pipelinen till `ConvertTo-Csv` och konverteras till en CSV-sträng. Parametern **NoTypeInformation** tar bort typ informations huvudet från CSV-utdata och är valfritt i PowerShell Core. `$Header`Variabeln innehåller en anpassad rubrik som ersätter följande standardvärden: **HasMoreData** , **JobStateInfo** , **PSBeginTime** , **PSEndTime** och **PSJobTypeName**. `$J`Variabeln innehåller CSV-strängen och används för att ta bort standard huvudet. `ConvertFrom-Csv`Cmdleten KONVERTERAR CSV-strängen till en **PSCustomObject** och använder parametern **header** för att tillämpa `$Header` variabeln.

### Exempel 4: konvertera CSV-strängar av tjänst objekt

Det här exemplet visar hur du använder `ConvertFrom-Csv` cmdleten med parametern **UseCulture** .

```powershell
(Get-Culture).TextInfo.ListSeparator
$Services = (Get-Service | ConvertTo-Csv)
ConvertFrom-Csv -InputObject $Services -UseCulture
```

`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** för att hämta den aktuella kulturen som är standard för List avgränsare. `Get-Service`Cmdleten skickar tjänst objekt nedåt i pipeline till `ConvertTo-Csv` . `ConvertTo-Csv`Service objekt konverteras till en serie CSV-strängar. CSV-strängarna lagras i `$Services` variabeln. `ConvertFrom-Csv`Cmdleten använder parametern **InputObject** och konverterar CSV-strängarna från `$Services` variabeln. Parametern **UseCulture** använder den aktuella kulturen som standard List avgränsare.

När parametern **UseCulture** används, se till att den aktuella kulturen som är standard för List avgränsare matchar den avgränsare som används i CSV-strängarna. Annars `ConvertFrom-Csv` kan inte generera objekt från CSV-strängarna.

## PARAMETRAR

### -Avgränsare

Anger den avgränsare som separerar egenskapsvärdena i CSV-strängarna.
Standardvärdet är komma (,).

Ange ett tecken, till exempel ett kolon (:).
Ange ett semikolon (;) omge det med enkla citat tecken.

Om du anger ett annat tecken än den faktiska sträng avgränsaren i filen, `ConvertFrom-Csv` kan inte skapa objekten från CSV-strängarna och returnera CSV-strängarna.

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sidhuvud

Anger en alternativ kolumn rubrik rad för den importerade strängen. Kolumn rubriken bestämmer de objekts egenskaps namn som skapats av `ConvertFrom-Csv` .

Ange kolumn rubriker som en kommaavgränsad lista. Ange inte rubrik strängen inom citat tecken. Omge varje kolumn rubrik med enkla citat tecken.

Om du anger färre kolumn rubriker än det finns data kolumner, ignoreras de återstående data kolumnerna. Om du anger fler kolumn rubriker än det finns data kolumner skapas de ytterligare kolumn rubrikerna med tomma data kolumner.

När du använder parametern **header** utelämnar du kolumn rubrik STRÄNGEN från CSV-strängarna. Annars skapar denna cmdlet ett extra objekt från objekten i rubrik raden.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger CSV-strängarna som ska konverteras till objekt. Ange en variabel som innehåller CSV-strängarna eller Skriv ett kommando eller uttryck som hämtar CSV-strängarna. Du kan också skicka CSV-strängarna till `ConvertFrom-Csv` .

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseCulture

Använder list avgränsaren för den aktuella kulturen som objekt avgränsare. Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka en pipe till CSV-strängar till denna cmdlet.

## UTDATA

### System. Management. Automation. PSObject

Denna cmdlet returnerar de objekt som beskrivs av egenskaperna i CSV-strängarna.

## ANTECKNINGAR

Eftersom de importerade objekten är CSV-versioner av objekt typen känns de inte igen och formateras inte av de PowerShell-typer som formaterar icke-CSV-versioner av objekt typen.

I CSV-format representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden. Egenskapsvärdena konverteras till strängar (med hjälp av metoden **toString ()** för objektet), så att de representeras av namnet på egenskap svärdet. Denna cmdlet exporterar inte objektets metoder.

## RELATERADE LÄNKAR

[ConvertTo-Csv](ConvertTo-Csv.md)

[Exportera-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)

