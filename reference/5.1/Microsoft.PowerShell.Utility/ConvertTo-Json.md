---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 9831249a9f1ffcc65fc275e44da04fde9348ae71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388067"
---
# ConvertTo-Json

## SAMMANFATTNING
Konverterar ett objekt till en JSON-formaterad sträng.

## SYNTAX

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
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
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

Det här kommandot använder `ConvertTo-Json` cmdleten för att konvertera ett GregorianCalendar-objekt till en JSON-formaterad sträng.

### Exempel 2

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

Det här kommandot visar effekterna av att använda **komprimerings** parametern i `ConvertTo-Json` . Komprimeringen påverkar bara utseendet på strängen, inte dess giltighet.

### Exempel 3

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

I det här exemplet används `ConvertTo-Json` cmdleten för att konvertera ett **system. DateTime** -objekt från `Get-Date` cmdlet till en JSON-formaterad sträng. Kommandot använder `Select-Object` cmdleten för att hämta alla ( `*` ) för egenskaperna för **datetime** -objektet. Utdata visar den JSON-sträng som `ConvertTo-Json` returnerades.

### Exempel 4

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

`ConvertTo-Json`Cmdleten implementeras med hjälp av [klassen JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).

## RELATERADE LÄNKAR

[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom – JSON](ConvertFrom-Json.md)

[Hämta innehåll](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-värdet](Get-UICulture.md)

[Anropa-webbegäran](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
