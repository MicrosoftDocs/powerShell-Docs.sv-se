---
external help file: Microsoft.Management.Infrastructure.CimCmdlets.dll-Help.xml
Locale: en-US
Module Name: CimCmdlets
ms.date: 02/20/2019
online version: https://docs.microsoft.com/powershell/module/cimcmdlets/import-binarymilog?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-BinaryMiLog
ms.openlocfilehash: cf85999f01e12dd24fee0ce377f434446218b935
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195236"
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
