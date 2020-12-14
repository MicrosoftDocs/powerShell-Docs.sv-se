---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709697"
---
# Enable-PSWSManCombinedTrace

## SAMMANFATTNING
Starta en loggningsmodul med aktiverade WSMan-och PowerShell-leverantörer.

## SYNTAX

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten startar en loggningsmodul med följande PowerShell-leverantörer aktiverade:

- Microsoft-Windows-PowerShell
- Microsoft-Windows-WinRM

Sessionen heter "PSTrace".

Denna cmdlet använder `Start-Trace` cmdleten.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: starta en kombinerad Logging-session

```powershell
Enable-PSWSManCombinedTrace
```

## PARAMETRAR

### -DoNotOverwriteExistingTrace

Som standard skrivs händelserna till "$pshome \Traces\PSTrace.etl". När den här parametern används skapar cmdleten ett unikt fil namn: "$pshome \Traces\ PSTrace_ {GUID}. etl"

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

## UTDATA

### Inga

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Händelse spårning](/windows/desktop/ETW/event-tracing-portal)

[Starta spårning](start-trace.md)

[Disable-PSWSManCombinedTrace](Disable-PSWSManCombinedTrace.md)

