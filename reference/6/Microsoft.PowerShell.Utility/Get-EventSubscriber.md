---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: 8f36d2af0fe03685e44070a0b0db86b8a276c4ca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267050"
---
# Get-EventSubscriber

## SAMMANFATTNING
Hämtar händelse prenumeranterna i den aktuella sessionen.

## SYNTAX

### BySource (standard)

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### ById

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## BESKRIVNING

**Get-EventSubscriber** -cmdlet: en hämtar händelse prenumeranterna i den aktuella sessionen.

När du prenumererar på en händelse genom att använda en register händelse-cmdlet läggs en händelse prenumerant till i din PowerShell-session och de händelser som du har prenumererat på läggs till i händelse kön när de utlöses.
Om du vill avbryta en händelse prenumeration tar du bort händelse prenumeranten med hjälp av Unregister-Event-cmdleten.

## EXEMPEL

### Exempel 1: Hämta händelse prenumeranten för en timer-händelse

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

I det här exemplet används kommandot **Get-EventSubscriber** för att hämta händelse prenumeranten för en timer-händelse.

Det första kommandot använder cmdleten New-Object för att skapa en instans av ett Timer-objekt.
Det sparar det nya timer-objektet i $Timer-variabeln.

Det andra kommandot använder cmdleten Get-Member för att visa de händelser som är tillgängliga för Timer-objekt.
Kommandot använder typ parametern för cmdleten **Get-Member** med värdet event.

Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera för den förflutna händelsen för det tidsinställda objektet.

Det fjärde kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för den förflutna händelsen.

### Exempel 2: Använd den dynamiska modulen i PSEventJob i egenskapen Action för händelse prenumeranten

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

Det här exemplet visar hur du använder den dynamiska modulen i **PSEventJob** -objektet i egenskapen Action för händelse prenumeranten.

Det första kommandot använder cmdleten New-Object för att skapa ett Timer-objekt.
Det andra kommandot anger intervallet för timer till 500 (millisekunder).

Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera den förflutna händelsen för objektet timer.
Kommandot innehåller en åtgärd som hanterar händelsen.
När tidsintervallet förflyter, utlöses en händelse och kommandona i åtgärden körs.
I det här fallet genererar Get-Random-cmdleten ett slumpmässigt nummer mellan 0 och 100 och sparar det i variabeln $Random.
Händelsens käll-ID är timer. Random.

När du använder en *Åtgärds* parameter i ett **register-ObjectEvent** -kommando returnerar kommandot ett **PSEventJob** -objekt som representerar åtgärden.

Det fjärde kommandot aktiverar timern.

Det femte kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för timern. slumpmässig händelse.
Objektet för händelse prenumerationer sparas i variabeln $Subscriber.

Det sjätte kommandot visar att egenskapen Action för Event Subscriber-objektet innehåller ett **PSEventJob** -objekt.
I själva verket innehåller det samma **PSEventJob** -objekt som kommandot **register-ObjectEvent** returnerade.

Det sjunde kommandot använder Format-List-cmdleten för att visa alla egenskaper för **PSEventJob** -objektet i åtgärds egenskapen i en lista.
Resultatet visar att **PSEventJob** -objektet har en modul-egenskap som innehåller en dynamisk skript-modul som implementerar åtgärden.

Återstående kommandon använder anrops operatorn (&) för att anropa kommandot i modulen och Visa värdet för $Random-variabeln.
Du kan använda anrops operatorn för att anropa alla kommandon i en modul, inklusive kommandon som inte exporteras.
I det här fallet visar kommandona det slumpmässiga talet som genereras när den förflutna händelsen inträffar.

Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

## PARAMETRAR

### -Force

Anger att denna cmdlet hämtar alla händelse prenumeranter, inklusive prenumeranter av händelser som är dolda med hjälp av parametern *SupportEvent* i register-ObjectEvent, register-WmiEvent och register-EngineEvent.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Anger egenskap svärdet för **SourceIdentifier** som endast hämtar händelse prenumeranter.
Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.
Jokertecken är inte tillåtna.
Den här parametern är Skift läges känslig.

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

### -SubscriptionId

Anger prenumerations-ID: n som denna cmdlet hämtar.
Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSEventSubscriber

**Get-EventSubscriber** returnerar ett objekt som representerar varje händelse prenumerant.

## ANTECKNINGAR

* New-Event-cmdleten, som skapar en anpassad händelse, genererar ingen prenumerant. Därför kommer **Get-EventSubscriber** -cmdlet: en inte hitta ett Subscriber-objekt för dessa händelser. Om du använder Register-EngineEvent-cmdlet: en för att prenumerera på en anpassad händelse (för att vidarebefordra händelsen eller för att ange en åtgärd), kommer **Get-EventSubscriber** att hitta den prenumerant som **Registrera-EngineEvent** genererar.

  Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.
Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

*

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
