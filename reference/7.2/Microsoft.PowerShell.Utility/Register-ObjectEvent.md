---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: 89f4d30df0dbc1b74ba28604ed686cad64a3a594
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708366"
---
# Register-ObjectEvent

## SAMMANFATTNING
Prenumererar på händelser som genereras av ett Microsoft .NET Framework-objekt.

## SYNTAX

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## BESKRIVNING

`Register-ObjectEvent`Cmdleten prenumererar på händelser som genereras av .net-objekt på den lokala datorn eller på en fjärrdator.

När den prenumererade händelsen höjs, läggs den till i händelse kön i sessionen. Använd cmdleten för att hämta händelser i händelse kön `Get-Event` .

Du kan använda parametrarna för `Register-ObjectEvent` för att ange egenskaps värden för de händelser som kan hjälpa dig att identifiera händelsen i kön. Du kan också använda **Åtgärds** parametern för att ange åtgärder som ska vidtas när en prenumerations händelse höjs och parametern **Forward** för att skicka fjärrhändelser till händelse kön i den lokala sessionen.

När du prenumererar på en händelse läggs en händelse prenumerant till i sessionen. Använd cmdleten för att hämta händelse prenumeranterna i sessionen `Get-EventSubscriber` . Om du vill avbryta prenumerationen använder du `Unregister-Event` cmdleten, som tar bort händelse prenumeranten från sessionen.

## EXEMPEL

### Exempel 1: prenumerera på händelser när en ny process startar

Det här exemplet prenumererar på händelser som genereras när en ny process startar.

Kommandot använder **ManagementEventWatcher** -objektet för att hämta **EventArrived** -händelser. Ett Query-objekt anger att händelserna är instans skapande händelser för klassen **Win32_Process** .

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### Exempel 2: Ange en åtgärd för att svara på en händelse

När du anger en åtgärd läggs inte händelser som aktive ras till i händelse kön. I stället svarar åtgärden på händelsen. I det här exemplet utlöses en ny **ProcessCreated** -händelse när en instans skapas, vilket innebär att en ny process startas.

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

Åtgärden använder sig av `$Sender` och `$EventArgs` Automatiska variabler som endast fylls i för händelse åtgärder.

`Register-ObjectEvent`Kommandot returnerar ett jobb objekt som representerar åtgärden, som körs som ett bakgrunds jobb. Du kan använda jobb-cmdletar, till exempel `Get-Job` och `Receive-Job` , för att hantera bakgrunds jobbet. Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/About/about_Jobs.md).

### Exempel 3: prenumerera på objekt händelser på fjärrdatorer

Det här exemplet visar hur du prenumererar på objekt händelser på fjärrdatorer. I det här exemplet används `Enable-ProcessCreationEvent` funktionen som definieras i `ProcessCreationEvent.ps1` skript filen. Det här skriptet är tillgängligt för alla datorer i exemplet.

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

Den första vi skapar **PSSessions** på två fjärrdatorer och sparar dem i `$S` variabeln. Sedan `Invoke-Command` kör cmdleten `ProcessCreationEvent.ps1` skriptet i varje PSSessions i `$S` . Den här åtgärden skapar `Enable-ProcessCreationEvent` funktionen i fjärrsessionerna.
Slutligen kör vi `Enable-ProcessCreationEvent` funktionen i fjärrsessionerna.

 Funktionen innehåller ett- `Register-ObjectEvent` kommando som prenumererar på händelser för att skapa instanser på **Win32_Process** -objektet genom **ManagementEventWatcher** -objektet och dess **EventArrived** -händelse.

### Exempel 4: Använd den dynamiska modulen i PSEventJob-objektet

Det här exemplet visar hur du använder den dynamiska modulen i **PSEventJob** -objektet som skapas när du inkluderar en **åtgärd** i en händelse registrering. Först createand vi och aktiverar ett Timer-objekt och anger sedan intervallet för timer till 500 (millisekunder). `Register-ObjectEvent`Cmdlet: en registrerar händelsen **förfluten tid** för objektet timer. **PSEventJob** -objektet sparas i `$Job` variabeln och finns också i **Åtgärds** egenskapen för händelse prenumeranten. Mer information finns i [Get-EventSubscriber](Get-EventSubscriber.md).

När timer-intervallet förflyter, utlöses en händelse och åtgärden utförs. I det här fallet `Get-Random` genererar cmdleten ett slumpmässigt nummer mellan 0 och 100 och sparar det i `$Random` variabeln.

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

**PSEventJob** har en **modul** -egenskap som innehåller en dynamisk skript-modul som implementerar åtgärden. Med hjälp av anrops operatorn ( `&` ) anropar vi kommandot i modulen för att visa värdet för `$Random` variabeln.

Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).

## PARAMETRAR

### -Åtgärd

Anger kommandon för att hantera händelsen. Kommandona i **åtgärden** körs när en händelse höjs, i stället för att skicka händelsen till händelse kön. Omge kommandoen med klammerparenteser ({}) för att skapa ett skript block.

Värdet för **Åtgärds** parametern kan innehålla `$Event` `$EventSubscriber` variablerna,, `$Sender` , `$EventArgs` och `$Args` . Dessa variabler ger information om händelsen till **Åtgärds** skript blocket. Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

När du anger en åtgärd `Register-ObjectEvent` returnerar ett händelse jobb objekt som representerar den åtgärden. Du kan använda jobb-cmdletar för att hantera händelse jobbet.

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

### – EventName

Anger händelsen som du prenumererar på.

Värdet för den här parametern måste vara namnet på händelsen som .NET-objektet exponerar. Klassen **ManagementEventWatcher** har till exempel händelser som heter **EventArrived** och **stoppats**. Använd cmdleten för att hitta händelse namnet för en händelse `Get-Member` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

Anger att cmdleten skickar händelser för den här prenumerationen till en fjärran sluten session. Använd den här parametern när du registrerar händelser på en fjärrdator eller i en fjärran sluten session.

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

### – InputObject

Anger det .NET-objekt som genererar händelserna. Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

Anger det maximala antalet gånger som en händelse kan utlösas.

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

Anger eventuella ytterligare data som ska associeras med den här händelse prenumerationen. Värdet för den här parametern visas i egenskapen MessageData för alla händelser som är associerade med den här prenumerationen.

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

Anger ett namn som du väljer för prenumerationen. Det namn du väljer måste vara unikt i den aktuella sessionen. Standardvärdet är det GUID som PowerShell tilldelar.

Värdet för den här parametern visas i värdet för egenskapen **SourceIdentifier** för Subscriber-objektet och alla händelse objekt som är associerade med den här prenumerationen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Anger att cmdleten döljer händelse prenumerationen. Använd den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och inte bör identifieras separat.

Om du vill visa eller avbryta en prenumeration som har skapats med parametern **SupportEvent** använder du parametern **Force** i `Get-EventSubscriber` `Unregister-Event` cmdletarna och.

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

Det går inte att skicka pipe-objekt till `Register-ObjectEvent` .

## UTDATA

### Ingen eller system. Management. Automation. PSEventJob

När du använder parametern **åtgärd** `Register-ObjectEvent` returnerar objektet **system. Management. Automation. PSEventJob** . Annars genererar den inga utdata.

## ANTECKNINGAR

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Ny händelse](New-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)

