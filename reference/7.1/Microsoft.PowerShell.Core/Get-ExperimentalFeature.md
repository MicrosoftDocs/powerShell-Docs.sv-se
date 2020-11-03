---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 2d91c36c6fd6d2e1281fdadf95c3b83e27c36f60
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267830"
---
# Get-ExperimentalFeature

## SAMMANFATTNING
Hämtar experimentella funktioner.

## SYNTAX

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-ExperimentalFeature`Cmdleten returnerar alla experimentella funktioner som identifieras av PowerShell.
Experimentella funktioner kan komma från moduler eller PowerShell-motorn. Experimentella funktioner gör det möjligt för användare att på ett säkert sätt testa nya funktioner och ge feedback (vanligt vis via GitHub) innan designen anses vara fullständig och eventuella ändringar kan bli en brytande ändring.

## EXEMPEL

### Exempel 1

Hämtar listan över aktuella registrerade experimentella funktioner och deras aktuella status.

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## PARAMETRAR

### -Name

Namn eller namn på de speciella experimentella funktioner som ska returneras.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

Namn eller namn på experimentella funktioner att returnera.

## UTDATA

### ExperimentalFeature

Returnerar instanser som matchar de begärda namnen eller alla experimentella funktioner om inget namn har angetts.

## RELATERADE LÄNKAR

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Aktivera – ExperimentalFeature](Enable-ExperimentalFeature.md)

