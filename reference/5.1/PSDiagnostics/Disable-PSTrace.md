---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 50d4118c5805a59d291d8dd17f467e7b47d34b46
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194509"
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

## INDATA

### Inget

## UTDATA

### System. Object

## ANTECKNINGAR

Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## RELATERADE LÄNKAR

[Get-LogProperties](Get-LogProperties.md)

[Set-LogProperties](Set-LogProperties.md)

[Aktivera – PSTrace](Enable-PSTrace.md)
