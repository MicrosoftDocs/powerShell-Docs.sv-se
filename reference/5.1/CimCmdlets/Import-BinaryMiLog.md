---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: ce5dd31170bc47edaa04ca3c31deab62dc4ec354
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263907"
---
# Import-BinaryMiLog

## SAMMANFATTNING
Används för att återskapa de sparade objekten baserat på innehållet i en export fil.

## SYNTAX

```
Import-BinaryMiLog [-Path] <String> [<CommonParameters>]
```

## BESKRIVNING

Använd denna cmdlet för att återskapa sparade objekt baserat på innehållet i en export fil som skapats av `Export-BinaryMILog` . Denna cmdlet liknar `Import-Clixml` , förutom att `Export-BinaryMILog` lagrar det resulterande objektet i en binär kodad fil.

## EXEMPEL

### Exempel 1 – återställa objekt som har exporter ATS till en fil

```powershell
Import-BinaryMiLog -Path "Processes.bmil"
```

## PARAMETRAR

### -Path

Anger sökvägen till filen där den binära representationen av objektet ska lagras. Parametern **Path** stöder jokertecken och relativa sökvägar. Denna cmdlet genererar ett fel om sökvägen matchar fler än en fil.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR
