---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 7d399661e4514c0a39ad00601d554c41c2897ff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265167"
---
# ConvertTo-Csv

## SAMMANFATTNING
Konverterar .NET-objekt till en serie kommaavgränsade värde strängar (CSV).

## SYNTAX

### Avgränsare (standard)

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### UseCulture

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-CSV`Cmdleten returnerar en serie kommaavgränsade värden (CSV) som representerar de objekt som du skickar. Du kan sedan använda `ConvertFrom-Csv` cmdleten för att återskapa objekt från CSV-strängarna. De objekt som konverteras från CSV är sträng värden för de ursprungliga objekt som innehåller egenskaps värden och inga metoder.

Du kan använda `Export-Csv` cmdleten för att konvertera objekt till CSV-strängar. `Export-CSV` liknar `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.

`ConvertTo-CSV`Cmdleten har parametrar för att ange en annan avgränsare än ett kommatecken eller använda den aktuella kulturen som avgränsare.

## EXEMPEL

### Exempel 1: konvertera ett objekt till CSV

I det här exemplet konverteras ett **process** objekt till en CSV-sträng.

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

`Get-Process`Cmdleten hämtar objektet **process** och använder parametern **Name** för att ange PowerShell-processen. Processobjektet skickas till `ConvertTo-CSV` cmdlet: en. `ConvertTo-CSV`Cmdleten konverterar objektet till CSV-strängar. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.

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

`Get-Date`Cmdleten hämtar **datetime** -objektet och sparar det i `$Date` variabeln. `ConvertTo-Csv`Cmdleten konverterar **datetime** -objektet till strängar. Parametern **InputObject** använder **datetime** -objektet som lagras i `$Date` variabeln. Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.

### Exempel 3: konvertera PowerShell-händelseloggen till CSV

I det här exemplet konverteras Windows-händelseloggen för PowerShell till en serie med CSV-strängar.

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare. `Get-WinEvent`Cmdleten hämtar händelse loggs objekt och använder parametern **LogName** för att ange namnet på logg filen. Händelse loggs objekt skickas ned pipelinen till `ConvertTo-Csv` cmdleten. `ConvertTo-Csv`Cmdleten konverterar händelse loggs objekt till en serie CSV-strängar. Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare. Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.

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

- Den första strängen innehåller som standard den **#TYPE** informations rubriken följt av objekt typens fullständigt kvalificerade namn. Till exempel **#TYPE system. Diagnostics. process**.
- Om **NoTypeInformation** används, innehåller den första strängen kolumn rubrikerna. Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.
- De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.

När du skickar flera objekt till `ConvertTo-CSV` , `ConvertTo-CSV` sorterar strängarna efter egenskaperna för det första objekt som du skickar. Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd. Om de återstående objekten har ytterligare egenskaper ignoreras dessa egenskaps värden.

## RELATERADE LÄNKAR

[ConvertFrom-CSV](ConvertFrom-Csv.md)

[Exportera-CSV](Export-Csv.md)

[Import-Csv](Import-Csv.md)
