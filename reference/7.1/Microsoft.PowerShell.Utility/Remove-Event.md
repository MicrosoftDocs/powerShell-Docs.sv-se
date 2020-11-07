---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 101732472611943a52c54e6517f42f523b513cfa
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347660"
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

`Remove-Event`Cmdleten tar bort händelser från händelse kön i den aktuella sessionen.

Den här cmdleten tar bara bort de händelser som för närvarande finns i kön. Använd cmdleten om du vill avbryta händelse registreringar eller avbryta prenumerationer `Unregister-Event` .

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

Anger händelse-ID: t som cmdleten tar bort. En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.

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

Anger käll-ID: t som denna cmdlet tar bort händelser från. Jokertecken är inte tillåtna. En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.

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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

Du kan skicka vidare händelser från `Get-Event` till `Remove-Event` .

## UTDATA

### Inget

Cmdleten genererar inga utdata.

## ANTECKNINGAR

Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
