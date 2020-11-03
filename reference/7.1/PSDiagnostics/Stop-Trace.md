---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 7331c7ca1ece02757859e75eefddd5a662353beb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263367"
---
# Stop-Trace

## SAMMANFATTNING
Stoppa en loggnings session för händelse spårning.

## SYNTAX

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet stoppar en loggnings session för Windows Event trace.

Denna cmdlet används av följande cmdlets:

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: stoppa en WSMan-spårningssession för spårning av loggar

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## PARAMETRAR

### -ETS
Skicka kommandon till Event trace-sessioner direkt utan att spara eller schemalägga.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sessionsnamn
Namnet på händelsespårningssessionen som ska stoppas.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### Inget

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Händelse spårning](/windows/desktop/ETW/event-tracing-portal)

[Starta spårning](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

[Disable-WSManTrace](Disable-WSManTrace.md)

[Aktivera – PSWSManCombinedTrace](Enable-PSWSManCombinedTrace.md)

[Aktivera – WSManTrace](Enable-WSManTrace.md)

