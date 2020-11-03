---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 7d57e7cff0dc3ca0eff36dbe38e240efdd324060
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265016"
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
