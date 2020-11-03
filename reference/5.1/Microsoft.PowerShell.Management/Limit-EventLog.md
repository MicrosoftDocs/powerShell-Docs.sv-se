---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/limit-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Limit-EventLog
ms.openlocfilehash: 3ec3214103dc6151e148f7482b0be8b821871e3c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265563"
---
# Limit-EventLog

## SAMMANFATTNING
Anger egenskaperna för händelse loggen som begränsar storleken på händelse loggen och ålder på dess poster.

## SYNTAX

```
Limit-EventLog [-LogName] <String[]> [-ComputerName <String[]>] [-RetentionDays <Int32>]
 [-OverflowAction <OverflowAction>] [-MaximumSize <Int64>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Limit-EventLog** anger den maximala storleken för en klassisk händelse logg, hur länge varje händelse måste behållas och vad som händer när loggen når sin maximala storlek.
Du kan använda den för att begränsa händelse loggarna på lokala eller fjärranslutna datorer.

De cmdletar som innehåller EventLog-händelsen Substantiv (EventLog-cmdletar) fungerar bara på klassiska händelse loggar.
Använd Get-WinEvent för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows.

## EXEMPEL

### Exempel 1: öka storleken på en händelse logg

```
PS C:\> Limit-EventLog -LogName "Windows PowerShell" -MaximumSize 20KB
```

Det här kommandot ökar den maximala storleken för Windows PowerShell-händelseloggen på den lokala datorn till 20480 byte (20 KB).

### Exempel 2: Behåll en händelse logg under en angiven varaktighet

```
PS C:\> Limit-EventLog -LogName Security -ComputerName "Server01", "Server02" -RetentionDays 7
```

Det här kommandot säkerställer att händelser i säkerhets loggen på Server01-och Server02-datorerna bevaras i minst 7 dagar.

### Exempel 3: ändra overflow-åtgärden för alla händelse loggar

```
PS C:\> $Logs = Get-EventLog -List | ForEach {$_.log}
PS C:\> Limit-EventLog -OverflowAction OverwriteOlder -LogName $Logs
PS C:\> Get-EventLog -List

Max(K) Retain OverflowAction     Entries  Log
------ ------ --------------     -------  ---
15,168      0 OverwriteOlder       3,412  Application
512         0 OverwriteOlder           0  DFS Replication
512         0 OverwriteOlder          17  DxStudio
10,240      7 OverwriteOlder           0  HardwareEvents
512         0 OverwriteOlder           0  Internet Explorer
512         0 OverwriteOlder           0  Key Management Service
16,384      0 OverwriteOlder           4  ODiag
16,384      0 OverwriteOlder         389  OSession Security
15,168      0 OverwriteOlder      19,360  System
15,360      0 OverwriteOlder      15,828  Windows PowerShell
```

Det här exemplet ändrar overflow-åtgärden för alla händelse loggar på den lokala datorn till OverwriteOlder.

Det första kommandot hämtar logg namnen för alla loggar på den lokala datorn.
Det andra kommandot anger spill åtgärden.
Det tredje kommandot visar resultatet.

## PARAMETRAR

### -ComputerName
Anger fjärrdatorer.
Standard är den lokala datorn.

Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en fjärran sluten dator.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* för **Limit-EventLog** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Anger händelse loggarna.
Ange logg namnet (värdet för logg egenskapen, inte LogDisplayName) för en eller flera händelse loggar, avgränsade med kommatecken.
Jokertecken tillåts inte.
Den här parametern är obligatorisk.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Högsta
Anger den maximala storleken på händelse loggarna i byte.
Ange ett värde mellan 64 KB (KB) och 4 GB.
Värdet måste vara delbar med 64 KB (65536).

Den här parametern anger värdet för egenskapen **MaximumKilobytes** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OverflowAction
Anger vad som händer när händelse loggen når den maximala storleken.

De acceptabla värdena för den här parametern är:

- DoNotOverwrite: befintliga poster bevaras och nya poster tas bort.
- OverwriteAsNeeded: varje ny post skriver över den äldsta posten.
- OverwriteOlder: nya händelser skriver över händelser som är äldre än värdet som anges i egenskapen **MinimumRetentionDays** . Om det inte finns några händelser som är äldre än vad som anges i egenskap svärdet **MinimumRetentionDays** , ignoreras nya händelser.

Den här parametern anger värdet för egenskapen **OverflowAction** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.

```yaml
Type: System.Diagnostics.OverflowAction
Parameter Sets: (All)
Aliases: OFA
Accepted values: OverwriteOlder, OverwriteAsNeeded, DoNotOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RetentionDays
Anger det minsta antalet dagar som en händelse måste finnas i händelse loggen.

Den här parametern anger värdet för egenskapen **MinimumRetentionDays** för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: MRD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Om du vill använda denna cmdlet i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet Kör som administratör.

  Den här cmdleten ändrar egenskaperna för objektet **system. Diagnostics. EventLog** som representerar en klassisk händelse logg.
Om du vill se de aktuella inställningarna för händelse loggens egenskaper skriver du `Get-EventLog -List` .

*

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
