---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: fc58e0bcfdd0b4ee7c7ee383b44f7d7f428c34c0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264752"
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
