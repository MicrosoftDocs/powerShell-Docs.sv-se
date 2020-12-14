---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: 64d927907f995613d3e2260e5476b406949bc1aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710368"
---
# Register-EngineEvent

## SAMMANFATTNING
Prenumererar på händelser som genereras av PowerShell-motorn och av `New-Event` cmdleten.

## SYNTAX

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Register-EngineEvent`Cmdleten prenumererar på händelser som genereras av PowerShell-motorn och `New-Event` cmdlet: en. Använd parametern **SourceIdentifier** för att ange händelsen.

Du kan använda den här cmdleten för att **Prenumerera på den händelse och de händelser** som genereras av `New-Event` cmdleten. Dessa händelser läggs automatiskt till i händelse kön i sessionen utan att behöva prenumerera. Men när du prenumererar kan du vidarebefordra händelserna, ange en åtgärd för att svara på händelserna och avbryta prenumerationen.

När den prenumererade händelsen höjs, läggs den till i händelse kön i sessionen. Använd cmdleten för att hämta händelser i händelse kön `Get-Event` .

När du prenumererar på en händelse läggs en händelse prenumerant till i sessionen. Använd cmdleten för att hämta händelse prenumeranterna i sessionen `Get-EventSubscriber` . Om du vill avbryta prenumerationen använder du `Unregister-Event` cmdleten, som tar bort händelse prenumeranten från sessionen.

## EXEMPEL

### Exempel 1: registrera en PowerShell-motor-händelse på fjärrdatorer

Det här exemplet registrerar en PowerShell-motor-händelse på två fjärrdatorer.

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S {
Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward
}
```

`New-PSSession` skapar en PSSession (User-Managed session) på varje fjärran sluten dator. `Invoke-Command` Cmdleten kör `Register-EngineEvent` kommandot i fjärrsessionerna.
`Register-EngineEvent` använder parametern **SourceIdentifier** för att identifiera händelsen. Parametern **Forward** instruerar motorn att vidarebefordra händelserna från fjärrsessionen till den lokala sessionen.

### Exempel 2: utför en viss åtgärd när händelsen avslut inträffar

Det här exemplet visar hur du kör `Register-EngineEvent` för att vidta en speciell åtgärd när händelsen **PowerShell. Exiting** inträffar.

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

**SupportEvent** -parametern läggs till för att dölja händelse prenumerationen. När PowerShell avslutas, exporteras i så fall kommando historiken från den avslutande sessionen till en XML-fil i användarens `$Home` katalog.

### Exempel 3: skapa och prenumerera på en användardefinierad händelse

I det här exemplet skapas en prenumeration för händelser från käll- **MyEventSource**. Det här är en godtycklig källa som vi ska använda för att övervaka förloppet för ett jobb. `Register-EngineEvent` används för att skapa prenumerationen. Skript blocket för **Åtgärds** parametern loggar händelse data till en textfil.

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` skapat jobb-ID 18. `Start-Job` skapat jobb-ID 19. I exemplet #4 tar vi bort händelse prenumerationen och jobben och kontrollerar sedan logg filen.

### Exempel 4: avregistrera händelser och rensa jobb

Detta är en fortsättning på exempel 3. I det här exemplet väntar vi i 10 sekunder på att flera händelser ska uppstå. Sedan avregistrerar vi händelse prenumerationen.

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

`Unregister-Event`Cmdleten stoppar jobbet som associeras med händelse prenumerationen (jobb-ID 18). Jobb-ID 19 körs fortfarande och skapar nya händelser. Vi använder **jobb** -cmdlets för att stoppa jobbet och ta bort de onödiga jobb objekten. `Get-Content` visar innehållet i logg filen.

## PARAMETRAR

### -Åtgärd

Anger kommandon för att hantera händelser. Kommandona i **åtgärden** körs när en händelse höjs, i stället för att skicka händelsen till händelse kön. Omge kommandoen med klammerparenteser ({}) för att skapa ett skript block.

Värdet för **Åtgärds** parametern kan innehålla `$Event` `$EventSubscriber` variablerna,, `$Sender` , `$EventArgs` och för `$Args` Automatiska variabler, som innehåller information om händelsen till **Åtgärds** skript blocket. Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

När du anger en åtgärd `Register-EngineEvent` returnerar ett händelse jobb objekt som representerar den åtgärden. Du kan använda jobb-cmdletar för att hantera händelse jobbet.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

Anger att cmdleten skickar händelser för den här prenumerationen till sessionen på den lokala datorn.
Använd den här parametern när du registrerar händelser på en fjärrdator eller i en fjärran sluten session.

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

### -MaxTriggerCount

Anger det maximala antalet gånger som åtgärden ska utföras för händelse prenumerationen.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Anger ytterligare data som är associerade med händelsen. Värdet för den här parametern visas i egenskapen **MessageData** för objektet event.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Anger käll-ID för händelsen som du prenumererar på. Käll identifieraren måste vara unik i den aktuella sessionen. Den här parametern är obligatorisk.

Värdet för den här parametern visas i värdet för egenskapen **SourceIdentifier** för Subscriber-objektet och för alla händelse objekt som är associerade med den här prenumerationen.

Värdet är speciellt för händelsens källa. Detta kan vara ett godtyckligt värde som du har skapat för att använda med `New-Event` cmdleten. PowerShell-motorn stöder **EngineEvent** -värdena **PowerShell. avslutar** och **PowerShell. OnIdle**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Anger att cmdleten döljer händelse prenumerationen. Lägg till den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och den bör inte identifieras separat.

Om du vill visa eller avbryta en prenumeration som har skapats med parametern **SupportEvent** lägger du till **Force** -parametern `Get-EventSubscriber` i `Unregister-Event` cmdletarna eller.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Du kan inte skicka pipe-ininformation till `Register-EngineEvent` .

## UTDATA

### Ingen eller system. Management. Automation. PSEventJob

Om du använder **Åtgärds** parametern `Register-EngineEvent` returnerar objektet **system. Management. Automation. PSEventJob** . Annars genererar den inga utdata.

## ANTECKNINGAR

Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Ny händelse](New-Event.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
