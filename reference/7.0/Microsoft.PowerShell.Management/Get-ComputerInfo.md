---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-computerinfo?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ComputerInfo
ms.openlocfilehash: 876ce5ff32863281ba9bc1ae94ece8b0a12c9efd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262400"
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
