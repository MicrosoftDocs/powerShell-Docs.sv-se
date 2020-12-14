---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 83a8cb444c20db8f7dd2181cac13e56d54d5d986
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709817"
---
# ConvertTo-Json

## SAMMANFATTNING
Konverterar ett objekt till en JSON-formaterad sträng.

## SYNTAX

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-Json`Cmdleten konverterar alla .net-objekt till ett sträng i JavaScript Object Notation (JSON)-format. Egenskaperna konverteras till fält namn, fältvärdena konverteras till egenskaps värden och metoderna tas bort.

Du kan sedan använda `ConvertFrom-Json` cmdleten för att konvertera en JSON-formaterad sträng till ett JSON-objekt, som är enkelt att hantera i PowerShell.

Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

Det här kommandot använder `ConvertTo-Json` cmdleten för att konvertera ett GregorianCalendar-objekt till en JSON-formaterad sträng.

### Exempel 2

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

I det här exemplet visas utdata från `ConvertTo-Json` cmdlet med och utan växlings parametern för **ommatrisen** . Du kan se att den andra delen av utdata är omsluten med vinkelparenteser.

### Exempel 3

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Det här kommandot visar effekterna av att använda **komprimerings** parametern i `ConvertTo-Json` . Komprimeringen påverkar bara utseendet på strängen, inte dess giltighet.

### Exempel 4

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

I det här exemplet används `ConvertTo-Json` cmdleten för att konvertera ett **system. DateTime** -objekt från `Get-Date` cmdlet till en JSON-formaterad sträng. Kommandot använder `Select-Object` cmdleten för att hämta alla ( `*` ) för egenskaperna för **datetime** -objektet. Utdata visar den JSON-sträng som `ConvertTo-Json` returnerades.

### Exempel 5

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

Det här exemplet visar hur du använder- `ConvertTo-Json` och- `ConvertFrom-Json` cmdletarna för att konvertera ett objekt till en JSON-sträng och ett JSON-objekt.

## PARAMETRAR

### -Matris

Matar ut objektet i vinkelparenteser, även om indatan är ett enda objekt.

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

### – Komprimera

Utelämnar blank steg och formatering med indrag i den utgående strängen.

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

### -Djup

Anger hur många nivåer med objekt som ingår i JSON-representationen. Standardvärdet är 2.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnumsAsStrings

Tillhandahåller ett alternativt alternativ för serialisering som konverterar alla uppräkningar till deras sträng representation.

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

### -EscapeHandling

Styr hur vissa tecken är undantagna i det resulterande JSON-resultatet. Som standard är endast kontroll tecken (t. ex. rad matning) som är undantagna.

Godkända värden är:

- Standard kontroll tecken är undantagna.
- EscapeNonAscii-alla icke-ASCII-och kontroll tecken är undantagna.
- EscapeHtml-HTML ( `<` ,,, `>` `&` `'` , `"` ) och kontroll tecken är undantagna.

Den här parametern introducerades i PowerShell 6,2.

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger de objekt som ska konverteras till JSON-format. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka ett objekt till `ConvertTo-Json` .

Parametern **InputObject** är obligatorisk, men dess värde kan vara null ( `$null` ) eller en tom sträng.
När indata-objektet är `$null` , `ConvertTo-Json` genererar inga utdata. Returnerar en tom sträng när inobjektet är en tom sträng `ConvertTo-Json` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Object

Du kan skicka vidare alla objekt till `ConvertTo-Json` .

## UTDATA

### System. String

## ANTECKNINGAR

`ConvertTo-Json`Cmdleten implementeras med hjälp av [Newtonsoft JSON.net](https://www.newtonsoft.com/json).

## RELATERADE LÄNKAR

[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom – JSON](ConvertFrom-Json.md)

[Hämta innehåll](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-värdet](Get-UICulture.md)

[Anropa-webbegäran](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)

[NewtonSoft.Jspå. StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
