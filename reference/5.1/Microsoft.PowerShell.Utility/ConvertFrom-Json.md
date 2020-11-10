---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: e1bab9250269dadf0d899f9e172e8a4a8387271d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388135"
---
# ConvertFrom-Json

## SAMMANFATTNING
Konverterar en JSON-formaterad sträng till ett anpassat objekt.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## BESKRIVNING

`ConvertFrom-Json`Cmdleten konverterar en JavaScript Object Notation (JSON) formaterad sträng till ett anpassat **PSCustomObject** -objekt som har en egenskap för varje fält i JSON-strängen. JSON används ofta av webbplatser för att tillhandahålla en text representation av objekt. JSON-standarden förhindrar inte användning som är förbjuden med en **PSCustomObject**. Om JSON-strängen t. ex. innehåller dubbla nycklar används bara den sista nyckeln av denna cmdlet. Se andra exempel nedan.

Använd cmdleten om du vill generera en JSON-sträng från ett objekt `ConvertTo-Json` .

Denna cmdlet introducerades i PowerShell 3,0.

> [!NOTE]
> Denna cmdlet stöder inte JSON med kommentarer.

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

## PARAMETRAR

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

## ANTECKNINGAR

`ConvertFrom-Json`Cmdleten implementeras med hjälp av [klassen JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).

## RELATERADE LÄNKAR

[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Anropa-webbegäran](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
