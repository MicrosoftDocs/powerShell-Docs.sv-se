---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 50372f0b938a1f8b051ec799ecfa94498b72dbc5
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273033"
---
# ConvertFrom-Json

## SAMMANFATTNING
Konverterar en JSON-formaterad sträng till ett anpassat objekt eller en hash-tabell.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertFrom-Json`Cmdleten konverterar en JavaScript Object Notation (JSON) formaterad sträng till ett anpassat **PSCustomObject** -objekt som har en egenskap för varje fält i JSON-strängen. JSON används ofta av webbplatser för att tillhandahålla en text representation av objekt. JSON-standarden förhindrar inte användning som är förbjuden med en **PSCustomObject**. Om JSON-strängen t. ex. innehåller dubbla nycklar används bara den sista nyckeln av denna cmdlet. Se andra exempel nedan.

Använd cmdleten om du vill generera en JSON-sträng från ett objekt `ConvertTo-Json` .

Denna cmdlet introducerades i PowerShell 3,0.

> [!NOTE]
> Från och med PowerShell 6 stöder denna cmdlet JSON med kommentarer. Accepterade kommentarer startas med två snedstreck ( `//` ). Kommentaren visas inte i data och kan skrivas i filen utan att skada data eller orsaka ett fel som det gjorde i PowerShell 5,1.

## EXEMPEL

### Exempel 1: konvertera ett DateTime-objekt till ett JSON-objekt

Detta kommando använder `ConvertTo-Json` `ConvertFrom-Json` cmdletarna och för att konvertera ett **datetime** -objekt från `Get-Date` cmdleten till ett JSON-objekt till en **PSCustomObject**.

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

Exemplet använder `Select-Object` cmdleten för att hämta alla egenskaper för **datetime** -objektet. Den använder `ConvertTo-Json` cmdleten för att konvertera **datetime** -objektet till en sträng FORMATERAD som ett JSON-objekt och `ConvertFrom-Json` cmdleten för att konvertera den JSON-formaterade strängen till ett **PSCustomObject** -objekt.

### Exempel 2: Hämta JSON-strängar från en webb tjänst och konvertera dem till PowerShell-objekt

Detta kommando använder `Invoke-WebRequest` cmdleten för att hämta JSON-strängar från en webb tjänst och använder sedan `ConvertFrom-Json` cmdleten för att konvertera JSON-innehåll till objekt som kan hanteras i PowerShell.

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

Du kan också använda `Invoke-RestMethod` cmdleten, som automatiskt KONVERTERAR JSON-innehåll till objekt.

### Exempel 3: konvertera en JSON-sträng till ett anpassat objekt

Det här exemplet visar hur du använder `ConvertFrom-Json` cmdleten för att konvertera en JSON-fil till ett anpassat PowerShell-objekt.

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

Kommandot använder Get-Content cmdlet för att hämta strängarna i en JSON-fil. Sedan använder den pipeline-operatorn för att skicka den avgränsade strängen till `ConvertFrom-Json` cmdleten, som konverterar den till ett anpassat objekt.

### Exempel 4: konvertera en JSON-sträng till en hash-tabell

Det här kommandot visar ett exempel där `-AsHashtable` växeln kan kringgå begränsningar för kommandot.

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

JSON-strängen innehåller två nyckel värde par med nycklar som bara skiljer sig i skift läge. Utan växeln skulle kommandot ha utlöst ett fel.

## PARAMETRAR

### -AsHashtable

Konverterar JSON till ett hash-tabell-objekt. Den här växeln introducerades i PowerShell 6,0. Det finns flera scenarier där den kan kringgå vissa begränsningar för `ConvertFrom-Json` cmdleten.

- Om JSON innehåller en lista med nycklar som bara skiljer sig i skift läge. Utan växeln visas nycklarna som identiska nycklar och det är därför bara den sista som används.
- Om JSON innehåller en nyckel som är en tom sträng. Utan växeln skulle cmdleten utlösa ett fel eftersom en inte `PSCustomObject` tillåter att en hash-tabell gör det. Ett exempel på användnings fall där detta kan inträffa är `project.lock.json` filer.
- Hash-tabeller kan bearbetas snabbare för vissa data strukturer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Djup

Hämtar eller anger det maximala djup som JSON-indatatypen får ha. Som standard är det 1024.

Den här parametern introducerades i PowerShell 6,2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger JSON-strängarna som ska konverteras till JSON-objekt. Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen. Du kan också skicka en sträng till `ConvertFrom-Json` .

Parametern **InputObject** är obligatorisk, men dess värde kan vara en tom sträng. När indata-objektet är en tom sträng `ConvertFrom-Json` genererar inga utdata. Värdet för **InputObject** får inte vara `$null` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en JSON-sträng till `ConvertFrom-Json` .

## UTDATA

### PSCustomObject

### System. Collections. hash

## ANTECKNINGAR

Denna cmdlet implementeras med hjälp av [Newtonsoft JSON.net](https://www.newtonsoft.com/json).

Från och med PowerShell 6 `ConvertTo-Json` försöker konvertera strängar som formaterats som tidsstämplar till **datetime** -värden. Det konverterade värdet är en `[datetime]` instans med en `Kind` egenskaps uppsättning som följer:

- `Unspecified`, om det inte finns någon tids zons information i Indatasträngen.
- `Utc`, om tids zons informationen är ett avslutande `Z` .
- `Local`, om tids zons informationen anges som en avslutande UTC- _förskjutning_ som `+02:00` . Förskjutningen konverteras korrekt till anroparens konfigurerade tidszon. Standardformateringen för utdata indikerar inte den ursprungliga tids zons förskjutningen.

## RELATERADE LÄNKAR

[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Anropa-webbegäran](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
