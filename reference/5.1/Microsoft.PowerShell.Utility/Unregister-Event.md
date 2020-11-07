---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 3cc2983def049e705a67bad05ee39bdbd71d3888
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344430"
---
# Unregister-Event

## SAMMANFATTNING
Avbryter en händelse prenumeration.

## SYNTAX

### BySource (standard)

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ById

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Unregister-Event`Cmdleten avbryter en händelse prenumeration som har skapats med hjälp av `Register-EngineEvent` `Register-ObjectEvent` cmdleten,, eller `Register-WmiEvent` .

När en händelse prenumeration avbryts tas händelse prenumeranten bort från sessionen och de prenumererade händelserna läggs inte längre till i händelse kön. När du avbryter en prenumeration på en händelse som skapats med hjälp av `New-Event` cmdleten, tas den nya händelsen också bort från sessionen.

`Unregister-Event` tar inte bort händelser från händelse kön. Använd cmdleten om du vill ta bort händelser `Remove-Event` .

## EXEMPEL

### Exempel 1: Avbryt en händelse prenumeration efter käll-ID

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

Med det här kommandot avbryts händelse prenumerationen som har käll-ID: n för ProcessStarted.

Använd cmdleten för att hitta käll-ID för en händelse `Get-Event` . Använd cmdleten för att hitta käll identifieraren för en händelse prenumeration `Get-EventSubscriber` .

### Exempel 2: Avbryt en händelse prenumeration efter prenumerations-ID

```
PS C:\> Unregister-Event -SubscriptionId 2
```

Med det här kommandot avbryts händelse prenumerationen som har ett prenumerations-ID på 2.

Använd cmdleten för att hitta prenumerations-ID för en händelse prenumeration `Get-EventSubscriber` .

### Exempel 3: Avbryt alla händelse prenumerationer

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

Detta kommando avbryter alla händelse prenumerationer i sessionen.

Kommandot använder `Get-EventSubscriber` cmdleten för att hämta alla Event Subscriber-objekt i sessionen, inklusive de prenumeranter som är dolda med hjälp av parametern **SupportEvent** för cmdletarna för händelse registrering.

Den använder en pipeline-operator ( `|` ) för att skicka prenumerantens objekt till `Unregister-Event` , vilket tar bort dem från sessionen. För att slutföra uppgiften krävs även **Force** -parametern på `Unregister-Event` .

## PARAMETRAR

### -Force

Avbryter alla händelse prenumerationer, inklusive prenumerationer som har dolts med hjälp av parametern **SupportEvent** i `Register-ObjectEvent` , `Register-WmiEvent` och `Register-EngineEvent` .

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

### -SourceIdentifier

Anger ett käll-ID som den här cmdleten avbryter händelse prenumerationer.

En **SourceIdentifier** -eller **SubscriptionId** -parameter måste inkluderas i varje kommando.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SubscriptionId

Anger ett ID för käll-ID som den här cmdleten avbryter händelse prenumerationer.

En **SourceIdentifier** -eller **SubscriptionId** -parameter måste inkluderas i varje kommando.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### System. Management. Automation. PSEventSubscriber

Du kan skicka vidare utdata från `Get-EventSubscriber` till `Unregister-Event` .

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR


Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

`Unregister-Event` Det går inte att ta bort händelser som skapats med `New-Event` cmdleten om du inte har prenumererat på händelsen med hjälp av `Register-EngineEvent` cmdleten. Om du vill ta bort en anpassad händelse från sessionen måste du ta bort den program mässigt eller stänga sessionen.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
