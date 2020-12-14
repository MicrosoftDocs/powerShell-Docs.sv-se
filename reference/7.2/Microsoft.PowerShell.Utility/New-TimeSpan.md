---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 5808685a5560d1cbf91c6705b90643c35702b28a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710086"
---
# New-TimeSpan

## SAMMANFATTNING
Skapar ett TimeSpan-objekt.

## SYNTAX

### Datum (standard)

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### Tid

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`New-TimeSpan`Cmdleten skapar ett **TimeSpan** -objekt som representerar ett tidsintervall.
Du kan använda ett **TimeSpan** -objekt för att lägga till eller ta bort tid från **datetime** -objekt.

Utan parametrar returnerar ett- `New-TimeSpan` kommando ett **TimeSpan** -objekt som representerar ett tidsintervall som är noll.

## EXEMPEL

### Exempel 1: skapa ett TimeSpan-objekt för en angiven varaktighet

Det här kommandot skapar ett **TimeSpan** -objekt med en varaktighet på 1 timme och 25 minuter och lagrar det i en variabel med namnet `$TimeSpan` . Den visar en representation av **TimeSpan** -objektet.

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### Exempel 2: skapa ett TimeSpan-objekt för ett tidsintervall

Det här exemplet skapar ett nytt **TimeSpan** -objekt som representerar intervallet mellan tidpunkten då kommandot körs och 1 januari 2010.

Det här kommandot kräver inte **Start** parametern eftersom standardvärdet för **Start** parametern är aktuellt datum och aktuell tid.

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### Exempel 3: Hämta datumet 90 dagar från det aktuella datumet

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

De här kommandona returnerar det datum som är 90 dagar efter det aktuella datumet.

### Exempel 4: identifiera TimeSpan sedan en fil uppdaterades

Det här kommandot anger hur lång tid det har sedan den [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) hjälp filen senast uppdaterades.
Du kan använda det här kommando formatet på alla filer eller andra objekt som har en **LastWriteTime** -egenskap.

Det här kommandot fungerar eftersom **Start** parametern för `New-TimeSpan` har ett alias för **LastWriteTime**. När du rör ett objekt som har en **LastWriteTime** -egenskap till `New-TimeSpan` , använder PowerShell värdet för egenskapen **LastWriteTime** som värdet för **Start** parametern.

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETRAR

### -Dagar

Anger dagar i tidsintervallet.
Standardvärdet är 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Slut

Anger slutet på ett tidsintervall.
Standardvärdet är aktuellt datum och aktuell tid.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timmar

Anger timmarna i tidsintervallet.
Standardvärdet är noll.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Minuter

Anger minuterna i tidsintervallet.
Standardvärdet är 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sekunder

Anger tids periodens längd i sekunder.
Standardvärdet är 0.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Start

Anger början på ett tidsintervall.
Ange en sträng som representerar datum och tid, till exempel "3/15/09" eller ett **datetime** -objekt, till exempel ett från ett `Get-Date` kommando. Standardvärdet är aktuellt datum och aktuell tid.

Du kan använda **Start** eller dess alias, **LastWriteTime**.
Med **LastWriteTime** -aliaset kan du skicka pipe-objekt som har en **LastWriteTime** -egenskap, till exempel filer i fil systemet `[System.Io.FileIO]` , till **Start** parametern för `New-TimeSpan` .

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. DateTime

Du kan skicka vidare ett **datetime** -objekt som representerar start tiden till `New-TimeSpan` .

## UTDATA

### System. TimeSpan

`New-TimeSpan` Returnerar ett objekt som representerar tidsintervallet.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta datum](Get-Date.md)

[Ange datum](Set-Date.md)

