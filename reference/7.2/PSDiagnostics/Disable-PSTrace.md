---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 0e246a0e3737f4ed693ed31096fc76e878a4af54
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710747"
---
# Disable-PSTrace

## SAMMANFATTNING
Inaktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.

## SYNTAX

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten inaktiverar händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: inaktivera analys händelse loggen för PowerShell

I följande exempel inaktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.

```powershell
Disable-PSTrace -AnalyticOnly
```

## PARAMETRAR

### -AnalyticOnly

När den här parametern används inaktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern. Den operativa händelse loggen har inte ändrats.

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
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

## UTDATA

### Inga

## ANTECKNINGAR

Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## RELATERADE LÄNKAR

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Aktivera – PSTrace](Enable-PSTrace.md)

