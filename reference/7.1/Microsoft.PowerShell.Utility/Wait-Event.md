---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: ee613dd78cbb30dce37c07297411c2d8bf9d832d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265611"
---
# Wait-Event

## SAMMANFATTNING
Väntar tills en viss händelse utlöses innan körningen fortsätter att köras.

## SYNTAX

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Wait-Event`Cmdleten pausar körningen av ett skript eller en funktion tills en viss händelse har Aktiver ATS. Körningen återupptas när händelsen identifieras. Tryck på <kbd>CTRL</kbd>C om du vill avbryta väntan + <kbd>C</kbd>.

Den här funktionen är ett alternativ till att söka efter en händelse. Du kan också bestämma svar på en händelse på två olika sätt:

- använda **Åtgärds** parametern för händelse prenumerationen
- väntar på att en händelse ska returneras och svara sedan med en åtgärd

## EXEMPEL

### Exempel 1: vänta på nästa händelse

Det här exemplet väntar på nästa händelse som aktive ras.

```powershell
Wait-Event
```

### Exempel 2: vänta på en händelse med en angiven käll-ID

Det här exemplet väntar på nästa händelse som aktive ras och har en käll-ID för ProcessStarted.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### Exempel 3: vänta tills en timer har gått ut

I det här exemplet används `Wait-Event` cmdleten för att vänta på en timer-händelse på en timer som är inställd på 2000 millisekunder.

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### Exempel 4: vänta på en händelse efter en angiven tids gräns

Det här exemplet väntar upp till 90 sekunder för nästa händelse som aktive ras och har en käll-ID för **ProcessStarted**. Om den angivna tiden går ut avslutas vänte tiden.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETRAR

### -SourceIdentifier

Anger käll-ID: t som denna cmdlet väntar på händelser.
Som standard `Wait-Event` väntar alla händelser.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

Anger den maximala tiden, i sekunder, som `Wait-Event` väntar på att händelsen ska inträffa. Standardvärdet,-1, väntar på obestämd tid. Tids inställningen startar när du skickar `Wait-Event` kommandot.

Om den angivna tiden överskrids, avslutas vänte tiden och kommando tolken returnerar, även om händelsen inte har Aktiver ATS. Inget fel meddelande visas.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

## UTDATA

### System. Management. Automation. PSEventArgs

## ANTECKNINGAR

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)

