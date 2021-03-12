---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 2ec01393a46de84b59f06995473bdff6bd5b2b4f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195029"
---
# Enable-PSTrace

## SAMMANFATTNING
Aktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.

## SYNTAX

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## BESKRIVNING

Med den här cmdleten kan du använda händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.

Du måste köra denna cmdlet från en upphöjd PowerShell-session.

## EXEMPEL

### Exempel 1: Aktivera analys händelse loggen för PowerShell

I följande exempel aktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.

```powershell
Enable-PSTrace -AnalyticOnly
```

## PARAMETRAR

### -AnalyticOnly

När den här parametern används aktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern. Den operativa händelse loggen har inte ändrats.

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

### -Force

Används för att framtvinga ändringen utan att du behöver göra något.

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

[Disable-PSTrace](Disable-PSTrace.md)
