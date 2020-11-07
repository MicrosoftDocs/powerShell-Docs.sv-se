---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 51327224b2522d0da680adfeffbcc6eeb12ddb00
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342685"
---
# Get-TimeZone

## SAMMANFATTNING
Hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.

## SYNTAX

### Namn (standard)

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### Id

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### ListAvailable

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Get-timezone** hämtar den aktuella tids zonen eller en lista över tillgängliga tids zoner.

## EXEMPEL

### Exempel 1: Hämta aktuell tidszon

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

Det här kommandot hämtar den aktuella tids zonen.

### Exempel 2: Hämta tids zoner som matchar en angiven sträng

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

Det här kommandot hämtar alla tids zoner som matchar det angivna jokertecknet.

### Exempel 3: Hämta alla tillgängliga tids zoner

```
PS C:\> Get-TimeZone -ListAvailable
```

Det här kommandot hämtar alla tillgängliga tids zoner.

## PARAMETRAR

### -ID

Anger, som en sträng mat ris, ID eller ID för de tids zoner som denna cmdlet hämtar.

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – ListAvailable

Anger att denna cmdlet hämtar alla tillgängliga tids zoner.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger, som en sträng mat ris, namn eller namn på de tids zoner som denna cmdlet hämtar.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

## UTDATA

### System. TimeZoneInfo []

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Ange-TimeZone](Set-TimeZone.md)
