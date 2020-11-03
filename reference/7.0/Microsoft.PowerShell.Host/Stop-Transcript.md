---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/stop-transcript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Transcript
ms.openlocfilehash: d5856ead8fa3f0f30e7509c43aeeb73013b7a801
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261615"
---
# Stop-Transcript

## SAMMANFATTNING
Stoppar en avskrift.

## SYNTAX

```
Stop-Transcript [<CommonParameters>]
```

## BESKRIVNING

`Stop-Transcript`Cmdleten stoppar en avskrift som startades av `Start-Transcript` cmdleten.
Du kan också avsluta en session för att stoppa avskriften.

## EXEMPEL

### Exempel 1: stoppa alla avskrifter

```powershell
Stop-Transcript
```

Det här kommandot stoppar alla avskrifter.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. String

Denna cmdlet returnerar en sträng som innehåller ett status meddelande och sökvägen till utdatafilen.

## ANTECKNINGAR

* Om en avskrift inte har startats Miss lyckas kommandot.

*

## RELATERADE LÄNKAR

[Start-avskrift](Start-Transcript.md)
