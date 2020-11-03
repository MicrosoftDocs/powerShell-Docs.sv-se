---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a98941de072b9b57b89a25bc180c0ee391d8b63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264747"
---
# Disable-PSWSManCombinedTrace

## SAMMANFATTNING
Stoppa inloggningssessionen som startats av Enable-PSWSManCombinedTrace.

## SYNTAX

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet stoppar inloggningssessionen som startats av `Enable-PSWSManCombinedTrace` .

Denna cmdlet använder `Stop-Trace` cmdleten.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: inaktivera den kombinerade inloggningssessionen

```powershell
Disable-PSWSManCombinedTrace
```

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Händelse spårning](/windows/desktop/ETW/event-tracing-portal)

[Stoppa – spåra](stop-trace.md)

[Aktivera – PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)
