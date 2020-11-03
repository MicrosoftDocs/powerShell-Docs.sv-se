---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: cf7236d31ccd248701a0464c84e94d0d910cc26f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266601"
---
# Remove-Event

## SAMMANFATTNING
Tar bort händelser från händelse kön.

## SYNTAX

### BySource (standard)

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByIdentifier

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Remove-Event** tar bort händelser från händelse kön i den aktuella sessionen.

Den här cmdleten tar bara bort de händelser som för närvarande finns i kön.
Om du vill avbryta händelse registreringar eller avbryta prenumerationen använder du cmdleten Unregister-Event.

## EXEMPEL

### Exempel 1: ta bort en händelse efter käll-ID

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

Det här kommandot tar bort händelser med käll-ID för processen som startades från händelse kön.

### Exempel 2: ta bort en händelse efter händelse identifierare

```
PS C:\> Remove-Event -EventIdentifier 30
```

Det här kommandot tar bort händelsen med händelse-ID 30 från händelse kön.

### Exempel 3: ta bort alla händelser

```
PS C:\> Get-Event | Remove-Event
```

Det här kommandot tar bort alla händelser från händelse kön.

## PARAMETRAR

### -EventIdentifier
Anger händelse-ID: t som cmdleten tar bort.
En *EventIdentifier* -eller *SourceIdentifier* -parameter krävs i varje kommando.

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier
Anger käll-ID: t som denna cmdlet tar bort händelser från.
Jokertecken är inte tillåtna.
En *EventIdentifier* -eller *SourceIdentifier* -parameter krävs i varje kommando.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
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

### System. Management. Automation. PSEventArgs
Du kan skicka vidare händelser från Get-Event för att **ta bort** händelser.

## UTDATA

### Inget
Cmdleten genererar inga utdata.

## ANTECKNINGAR

* Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

*

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
