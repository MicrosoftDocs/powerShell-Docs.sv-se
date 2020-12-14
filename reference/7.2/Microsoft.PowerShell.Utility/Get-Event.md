---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 4b275d489984f85aea401b781e38c80fbc4b2177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709438"
---
# Get-Event

## SAMMANFATTNING
Hämtar händelserna i händelse kön.

## SYNTAX

### BySource (standard)

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### ById

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## BESKRIVNING

`Get-Event`Cmdleten hämtar händelser i händelse kön för PowerShell för den aktuella sessionen. Du kan hämta alla händelser eller använda parametern **EventIdentifier** eller **SourceIdentifier** för att ange händelser.

När en händelse inträffar läggs den till i händelse kön. Händelse kön innehåller händelser som du har registrerat, händelser som skapats med hjälp av `New-Event` cmdleten och händelsen som utlöses när PowerShell avslutas. Du kan använda `Get-Event` eller `Wait-Event` för att hämta händelser.

Denna cmdlet hämtar inte händelser från Loggbokens loggarna. Använd eller för att hämta händelser `Get-WinEvent` `Get-EventLog` .

## EXEMPEL

### Exempel 1: Hämta alla händelser

```
PS C:\> Get-Event
```

Det här kommandot hämtar alla händelser i händelse kön.

### Exempel 2: Hämta händelser efter käll-ID

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

Det här kommandot hämtar händelser där värdet för egenskapen SourceIdentifier är PowerShell. ProcessCreated.

### Exempel 3: Hämta en händelse baserat på den tid det genererades

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

Det här exemplet visar hur du hämtar händelser genom att använda andra egenskaper än SourceIdentifier.

Det första kommandot hämtar alla händelser i händelse kön och sparar dem i `$Events` variabeln.

Det andra kommandot använder mat ris notation för att hämta den första (0-index) händelsen i matrisen i `$Events` variabeln. Kommandot använder en pipeline-operator ( `|` ) för att skicka händelsen till `Format-List` kommandot, som visar alla egenskaper för händelsen i en lista. På så sätt kan du undersöka egenskaperna för händelseobjektet.

Det tredje kommandot visar hur du använder `Where-Object` cmdleten för att hämta en händelse baserat på den tidpunkt då den genererades.

### Exempel 4: Hämta en händelse efter dess identifierare

```
PS C:\> Get-Event -EventIdentifier 2
```

Det här kommandot hämtar händelsen med händelse-ID 2.

## PARAMETRAR

### -EventIdentifier

Anger händelse identifierare som denna cmdlet hämtar händelser för.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

Anger käll identifierare för vilka denna cmdlet hämtar händelser. Standardvärdet är alla händelser i händelse kön. Jokertecken är inte tillåtna.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSEventArgs

`Get-Event` Returnerar ett **PSEventArgs** -objekt för varje händelse. Om du vill se en beskrivning av objektet skriver `Get-Help Get-Event -Full` du och läser avsnittet anteckningar i hjälp avsnittet.

## ANTECKNINGAR

Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

`Get-Event`Cmdleten returnerar ett **PSEventArgs** -objekt (**system. Management. Automation. PSEventArgs**) med följande egenskaper:

- Namnet. Namnet på datorn där händelsen inträffade. Det här egenskap svärdet fylls bara i när händelsen vidarebefordras från en fjärrdator.

- RunspaceId. Ett GUID som unikt identifierar den session där händelsen inträffade. Det här egenskap svärdet fylls bara i när händelsen vidarebefordras från en fjärrdator.

- EventIdentifier. Ett heltal (Int32) som unikt identifierar händelse aviseringen i den aktuella sessionen.

- Ingen. Objektet som genererade händelsen. I värdet för parametern **åtgärd** `$Sender` innehåller den automatiska variabeln objektet Sender.

- SourceEventArgs. Den första parametern som härleds från EventArgs, om den finns. I en tidsinställd händelse där signaturen har skickat av formulär objekt, **timers. ElapsedEventArgs** e, skulle egenskapen **SourceEventArgs** innehålla **timers. ElapsedEventArgs**. I värdet för parametern **åtgärd** `$EventArgs` innehåller den automatiska variabeln det här värdet.

- SourceArgs. Alla parametrar för den ursprungliga händelse under skriften. För en standard Event Signature `$Args[0]` representerar avsändaren och `$Args[1]` representerar **SourceEventArgs**. I värdet för parametern **åtgärd** `$Args` innehåller den automatiska variabeln det här värdet.

- SourceIdentifier. En sträng som identifierar händelse prenumerationen. I värdet för parametern **åtgärd** innehåller egenskapen **SourceIdentifier** för den `$Event` automatiska variabeln det här värdet.

- TimeGenerated. Ett **datetime** -objekt som representerar tiden då händelsen genererades.
  I värdet för parametern **åtgärd** innehåller egenskapen **TimeGenerated** för den `$Event` automatiska variabeln det här värdet.

- MessageData. Data som är associerade med händelse prenumerationen. Användarna anger dessa data när de registrerar en händelse. I värdet för parametern **åtgärd** innehåller egenskapen **MessageData** för den `$Event` automatiska variabeln det här värdet.

## RELATERADE LÄNKAR

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
