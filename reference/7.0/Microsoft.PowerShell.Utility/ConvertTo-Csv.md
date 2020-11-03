---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 858ae1098d271d28fd9b758855f0952a6307eb95
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262916"
---
# ConvertTo-Csv

## SAMMANFATTNING
Konverterar .NET-objekt till en serie med strängar med Character-separerade värden (CSV).

## SYNTAX

### Avgränsare (standard)

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-CSV`Cmdleten returnerar en serie kommaavgränsade värden (CSV) som representerar de objekt som du skickar. Du kan sedan använda `ConvertFrom-Csv` cmdleten för att återskapa objekt från CSV-strängarna. De objekt som konverteras från CSV är sträng värden för de ursprungliga objekt som innehåller egenskaps värden och inga metoder.

Du kan använda `Export-Csv` cmdleten för att konvertera objekt till CSV-strängar. `Export-CSV` liknar `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.

`ConvertTo-CSV`Cmdleten har parametrar för att ange en annan avgränsare än ett kommatecken eller använda den aktuella kulturen som avgränsare.

## EXEMPEL

### Exempel 1: konvertera ett objekt till CSV

I det här exemplet konverteras ett **process** objekt till en CSV-sträng.

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

`Get-Process`Cmdleten hämtar objektet **process** och använder parametern **Name** för att ange PowerShell-processen. Processobjektet skickas till `ConvertTo-CSV` cmdlet: en. `ConvertTo-CSV`Cmdleten konverterar objektet till CSV-strängar. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.

### Exempel 2: konvertera ett DateTime-objekt till CSV

I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

`Get-Date`Cmdleten hämtar **datetime** -objektet och sparar det i `$Date` variabeln. `ConvertTo-Csv`Cmdleten konverterar **datetime** -objektet till strängar. Parametern **InputObject** använder **datetime** -objektet som lagras i `$Date` variabeln. Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.

### Exempel 3: konvertera PowerShell-händelseloggen till CSV

I det här exemplet konverteras Windows-händelseloggen för PowerShell till en serie med CSV-strängar.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare. `Get-WinEvent`Cmdleten hämtar händelse loggs objekt och använder parametern **LogName** för att ange namnet på logg filen. Händelse loggs objekt skickas ned pipelinen till `ConvertTo-Csv` cmdleten. `ConvertTo-Csv`Cmdleten konverterar händelse loggs objekt till en serie CSV-strängar. Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.

### Exempel 4: konvertera till CSV med citat tecken runt två kolumner

I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### Exempel 4: konvertera till CSV med enbart offerter vid behov

I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## PARAMETRAR

### -Avgränsare

Anger avgränsaren för att avgränsa egenskaps värden i CSV-strängar. Standardvärdet är ett kommatecken ( `,` ). Ange ett tecken, till exempel ett kolon ( `:` ). Om du vill ange ett semikolon ( `;` ) omger du det med enkla citat tecken.

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

### -IncludeTypeInformation

När den här parametern används, innehåller den första raden i utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn. Till exempel **#TYPE system. Diagnostics. process**.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som konverteras till CSV-strängar. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka pipe-objekt till `ConvertTo-CSV` .

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -NoTypeInformation

Tar bort **#TYPE** informations huvud från utdata. Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Använder list avgränsaren för den aktuella kulturen som objekt avgränsare. Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -QuoteFields

Anger namnen på de kolumner som ska vara citerade. När den här parametern används är de angivna kolumnerna citerade.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseQuotes

Anger när offerter används i CSV-filerna. Möjliga värden:

- Aldrig – citera ingenting
- Always quote all (standard beteende)
- Endast fält med en avgränsning som innehåller ett avgränsnings tecken

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt som har ett ETS-kort (Extended Type System) till `ConvertTo-CSV` .

## UTDATA

### System. String

CSV-utdata returneras som en samling med strängar.

## ANTECKNINGAR

I CSV-format representeras varje objekt av en kommaavgränsad lista över dess egenskaps värde. Egenskaps värden konverteras till strängar med hjälp av objektets **toString ()-** metod. Strängarna representeras av egenskaps värde namnet. `ConvertTo-CSV` exporterar inte objektets metoder.

CSV-strängarna matas ut enligt följande:

- Om **IncludeTypeInformation** används, består den första strängen av **#TYPE** följt av objekt typens fullständigt kvalificerade namn. Till exempel **#TYPE system. Diagnostics. process**.
- Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna. Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.
- De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.

Från och med PowerShell 6,0 är standard beteendet för `ConvertTo-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd. **IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `ConvertTo-CSV` före PowerShell 6,0.

När du skickar flera objekt till `ConvertTo-CSV` , `ConvertTo-CSV` sorterar strängarna efter egenskaperna för det första objekt som du skickar. Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd. Om de återstående objekten har ytterligare egenskaper ignoreras dessa egenskaps värden.

## RELATERADE LÄNKAR

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[Exportera-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)
