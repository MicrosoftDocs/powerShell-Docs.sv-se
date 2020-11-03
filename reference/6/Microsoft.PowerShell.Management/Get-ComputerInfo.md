---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: 55e7831112d6385b6d449123973ca4b877faa7fd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266811"
---
# Get-ComputerInfo

## SAMMANFATTNING
Hämtar ett konsoliderat objekt av system-och operativ system egenskaper.

## SYNTAX

```
Get-ComputerInfo [[-Property] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-ComputerInfo`Cmdlet: en hämtar ett konsoliderat objekt av system-och operativ system egenskaper.
Den här cmdleten introducerades i Windows PowerShell 5,1.

## EXEMPEL

### Exempel 1: Hämta alla dator egenskaper

```powershell
Get-ComputerInfo
```

Det här kommandot hämtar alla system-och operativ system egenskaper från datorn.

### Exempel 2: Hämta alla egenskaper för datorns operativ system

```powershell
Get-ComputerInfo -Property "os*"
```

Det här kommandot hämtar alla egenskaper för operativ systemet från datorn.

## PARAMETRAR

### – Egenskap

Anger, som en sträng mat ris, de dator egenskaper som denna cmdlet visar.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System.String[]

## UTDATA

### Microsoft. PowerShell. Management. ComputerInfo

## ANTECKNINGAR

## RELATERADE LÄNKAR
