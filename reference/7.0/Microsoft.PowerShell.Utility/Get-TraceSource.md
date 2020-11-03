---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 024fa690ff9ddd4eae2d7fd6203e83f56fef6cd7
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262676"
---
# Get-TraceSource

## SAMMANFATTNING
Hämtar PowerShell-komponenter som instrumenteras för spårning.

## SYNTAX

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

**Get-TraceSource** -cmdlet: en hämtar spårnings källorna för PowerShell-komponenter som används för närvarande.
Du kan använda data för att avgöra vilka PowerShell-komponenter du kan spåra.
Vid spårning genererar komponenten detaljerade meddelanden om varje steg i den interna bearbetningen.
Utvecklare använder spårnings data för att övervaka data flöde, program körning och fel.

Spårnings-cmdletarna har utformats för PowerShell-utvecklare, men de är tillgängliga för alla användare.

## EXEMPEL

### Exempel 1: Hämta spårnings källor efter namn

```
PS C:\> Get-TraceSource -Name "*provider*"
```

Det här kommandot hämtar alla spårnings källor som har namn som inkluderar providern.

### Exempel 2: Hämta alla spårnings källor

```
PS C:\> Get-TraceSource
```

Det här kommandot hämtar alla PowerShell-komponenter som kan spåras.

## PARAMETRAR

### -Name

Anger spårnings källorna som ska hämtas.
Jokertecken är tillåtna.
Parameter namnets *namn* är valfritt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller namnet på en spårnings källa till **Get-TraceSource**.

## UTDATA

### System. Management. Automation. PSTraceSource

**Get-TraceSource** returnerar objekt som representerar spårnings källorna.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Set-TraceSource](Set-TraceSource.md)

[Spåra-kommando](Trace-Command.md)
