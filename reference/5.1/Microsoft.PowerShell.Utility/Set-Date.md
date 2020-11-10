---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 36e49d36ffe7e4000926cf821767dfb158efcf46
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387982"
---
# Set-Date

## SAMMANFATTNING
Ändrar system klockan på datorn till en tidpunkt som du anger.

## SYNTAX

### Datum (standard)

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Automatiskt

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Date`Cmdleten ändrar system datum och-tid på datorn till ett datum och en tidpunkt som du anger.
Du kan ange ett nytt datum och/eller tid genom att skriva en sträng eller genom att skicka ett **datetime** -eller **TimeSpan** -objekt till `Set-Date` . Om du vill ange ett nytt datum eller en ny tid använder du parametern **date** .
Om du vill ange ett ändrings intervall använder du parametern **Justera** .

## EXEMPEL

### Exempel 1: Lägg till tre dagar till system datumet

Det här kommandot lägger till tre dagar till det aktuella system datumet.
Den påverkar inte tiden.
Kommandot använder **datum** parametern för att ange datumet.

`Get-Date`Cmdleten returnerar det aktuella datumet som ett **datetime** -objekt. **AddDays** -metoden för **datetime** -objektet lägger till ett angivet antal dagar (3) till det aktuella **datetime** -objektet.

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### Exempel 2: Ställ tillbaka system klockan 10 minuter

I det här exemplet anges den aktuella system tiden tillbaka med 10 minuter.

Med **justerings** parametern kan du ange ett ändrings intervall (minus tio minuter) i standard tids formatet för språkvarianten.

Parametern **DisplayHint** anger att PowerShell endast visar tiden, men det påverkar inte det **datetime** -objekt som `Set-Date` returneras.

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### Exempel 3: Ange datum och tid till ett variabel värde

De här kommandona ändrar system datum och-tid på den lokala datorn till datum och tid som sparats i variabeln `$T` . Det första kommandot hämtar datumet och lagrar det i `$T` .

Det andra kommandot använder **datum** parametern för att skicka **datetime** -objektet `$T` till- `Set-Date` cmdleten.

```powershell
$T = Get-Date
Set-Date -Date $T
```

### Exempel 4: Lägg till 90 minuter på system klockan

Dessa kommandon förflyttar system klockan på den lokala datorn med 90 minuter.

Det första kommandot använder `New-TimeSpan` cmdleten för att skapa ett **TimeSpan** -objekt med ett intervall på 90 minuter och sparar det i `$90mins` variabeln.

Det andra kommandot använder parametern **Justera** för `Set-Date` för att justera datumet med värdet för **TimeSpan** -objektet i `$90mins` variabeln.

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMETRAR

### – Justera

Anger värdet för vilket denna cmdlet lägger till eller undervärderar från aktuellt datum och aktuell tid.
kan skriva en justering i standard datum-och tids format för dina nationella inställningar eller använda parametern **Justera** för att skicka ett **TimeSpan** -objekt från `New-TimeSpan` till `Set-Date` .

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Datum

Ändrar datum och tid till de angivna värdena.
Du kan ange ett nytt datum i kort datum format och en tid i standardformatet för ditt språk. Du kan också skicka ett **datetime** -objekt från `Get-Date` .

Om du anger ett datum, men inte en tid, `Set-Date` ändras tiden till midnatt på det angivna datumet. Om du bara anger en tid ändras inte datumet.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

Anger vilka element i datum och tid som visas. De acceptabla värdena för den här parametern är:

- **Datum** – visar endast datumet.
- **Time** – visar endast tiden.
- **Datetime** – visar datum och tid.

Den här parametern påverkar endast visningen.
Det påverkar inte det **datetime** -objekt som `Get-Date` hämtas.

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. DateTime

Du kan skicka vidare ett datum till `Set-Date` .

## UTDATA

### System. DateTime

`Set-Date` Returnerar ett objekt som representerar det datum som angetts.

## ANTECKNINGAR

- Använd denna cmdlet försiktigt när du ändrar datum och tid på datorn. Ändringen kan förhindra att datorn tar emot systemomfattande händelser och uppdateringar som utlöses av ett datum eller en tid. Använd parametrarna **whatIf** och **Confirm** för att undvika fel.
- Du kan använda standard-.NET-metoder med **datetime** -och **TimeSpan** -objekten som används med `Set-Date` , till exempel **AddDays** , **AddMonths** och **FromFileTime**. Mer information finns i [datetime-metoder](/dotnet/api/system.datetime) och

  [TimeSpan-metoder](/dotnet/api/system.timespan) i .NET SDK.

## RELATERADE LÄNKAR

[Hämta datum](Get-Date.md)

[New-TimeSpan](New-TimeSpan.md)
