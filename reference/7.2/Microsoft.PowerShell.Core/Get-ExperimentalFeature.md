---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 2b6bbc6e3e0c535d777509a545edfe10fed7d727
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194933"
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

### System. Management. Automation. ExperimentalFeature

Returnerar instanser som matchar de begärda namnen eller alla experimentella funktioner om inget namn har angetts.

## RELATERADE LÄNKAR

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Aktivera – ExperimentalFeature](Enable-ExperimentalFeature.md)
