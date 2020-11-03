---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-command?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Command
ms.openlocfilehash: 0cf5ac4df506b5882dd2dbf87ce6ad05845e0c94
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264290"
---
# Measure-Command

## SAMMANFATTNING
Mäter den tid det tar att köra skript block och cmdlets.

## SYNTAX

```
Measure-Command [-InputObject <PSObject>] [-Expression] <ScriptBlock> [<CommonParameters>]
```

## BESKRIVNING

`Measure-Command`Cmdlet: en kör ett skript block eller en cmdlet internt, gånger körningen av åtgärden och returnerar körnings tiden.

> [!NOTE]
> Skript block körs genom `Measure-Command` körning i det aktuella omfånget, inte en underordnad omfattning.

## EXEMPEL

### Exempel 1: mäta ett kommando

Det här exemplet mäter hur lång tid det tar att köra ett `Get-EventLog` kommando som hämtar händelser i händelse loggen i Windows PowerShell.

```powershell
Measure-Command { Get-EventLog "windows powershell" }
```

### Exempel 2: Jämför två utdata från Measure-Command

Det första kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder parametern **Path** för att bara hämta `.txt` filer i `C:\Windows` katalogen och dess under kataloger.

Det andra kommandot mäter den tid det tar att bearbeta ett rekursivt `Get-ChildItem` kommando som använder den providerspecifika parametern.

Dessa kommandon visar värdet för att använda ett providerspecifik filter i PowerShell-kommandon.

```powershell
Measure-Command { Get-ChildItem -Path C:\Windows\*.txt -Recurse }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 8
Milliseconds      : 618
Ticks             : 86182763
TotalDays         : 9.9748568287037E-05
TotalHours        : 0.00239396563888889
TotalMinutes      : 0.143637938333333
TotalSeconds      : 8.6182763
TotalMilliseconds : 8618.2763
```

```powershell
Measure-Command {Get-ChildItem C:\Windows -Filter "*.txt" -Recurse}
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 1
Milliseconds      : 140
Ticks             : 11409189
TotalDays         : 1.32050798611111E-05
TotalHours        : 0.000316921916666667
TotalMinutes      : 0.019015315
TotalSeconds      : 1.1409189
TotalMilliseconds : 1140.9189
```

### Exempel 3: rör inström till Measure-Command

Objekt som skickas till `Measure-Command` är tillgängliga för det skript block som skickas till **uttrycks** parametern. Skript blocket körs en gång för varje objekt i pipelinen.

```powershell
# Perform a simple operation to demonstrate the InputObject parameter
# Note that no output is displayed.
10, 20, 50 | Measure-Command -Expression { for ($i=0; $i -lt $_ i++) {$i} }
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 12
Ticks             : 122672
TotalDays         : 1.41981481481481E-07
TotalHours        : 3.40755555555556E-06
TotalMinutes      : 0.000204453333333333
TotalSeconds      : 0.0122672
TotalMilliseconds : 12.2672
```

### Exempel 4: Visa utdata från kommandot mätt

Om du vill visa utmatningar av uttryck i `Measure-Command` kan du använda en pipe till `Out-Default` .

```powershell
# Perform the same operation as above adding Out-Default to every execution.
# This will show that the ScriptBlock is in fact executing for every item.
10, 20, 50 | Measure-Command -Expression {for ($i=0; $i -lt $_; $i++) {$i}; "$($_)" | Out-Default }
```

```Output
10
20
50


Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 11
Ticks             : 113745
TotalDays         : 1.31649305555556E-07
TotalHours        : 3.15958333333333E-06
TotalMinutes      : 0.000189575
TotalSeconds      : 0.0113745
TotalMilliseconds : 11.3745
```

### Exempel 5: mäta körning i ett underordnat omfång

`Measure-Command` Kör skript blocket i det aktuella omfånget, så att skript blocket kan ändra värden i det aktuella omfånget. För att undvika ändringar i det aktuella omfånget måste du omsluta skript blocket inom klammerparenteser ( `{}` ) och använda anrops operatorn ( `&` ) för att köra blocket i en underordnad omfattning.

```powershell
$foo = 'Value 1'
$null = Measure-Command { $foo = 'Value 2' }
$foo
$null = Measure-Command { & { $foo = 'Value 3' } }
$foo
```

```Output
Value 2
Value 2
```

Mer information om anrops operatorn finns [about_Operators](../Microsoft.PowerShell.Core/About/about_Operators.md#call-operator-).

## PARAMETRAR

### – Uttryck

Anger det uttryck som är tids gräns. Omge uttrycket med klammerparenteser ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Objekt som är kopplade till **InputObject** -parametern är valfria indatatyper för det skript block som skickas till **uttrycks** parametern. Inuti-skript blocket `$_` kan användas för att referera till det aktuella objektet i pipelinen.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare ett objekt till `Measure-Command` .

## UTDATA

### System. TimeSpan

`Measure-Command` Returnerar ett tidsintervall objekt som representerar resultatet.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Invoke-kommando](../Microsoft.PowerShell.Core/Invoke-Command.md)

[Spåra-kommando](Trace-Command.md)

