---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 6056861bc6b472e389939e446d922d2bc4302294
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266978"
---
# New-Event

## SAMMANFATTNING
Skapar en ny händelse.

## SYNTAX

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **New-Event** skapar en ny anpassad händelse.

Du kan använda anpassade händelser för att meddela användare om tillstånds ändringar i programmet och eventuella ändringar som programmet kan identifiera, inklusive maskinvaru-eller system villkor, program status, disk status, nätverks status eller slut för ande av ett bakgrunds jobb.

Anpassade händelser läggs automatiskt till i händelse kön i sessionen när de höjs. du behöver inte prenumerera på dem.
Men om du vill vidarebefordra en händelse till den lokala sessionen eller ange en åtgärd för att svara på händelsen, använder du Register-EngineEvent cmdlet för att prenumerera på den anpassade händelsen.

När du prenumererar på en anpassad händelse läggs händelse prenumeranten till i sessionen.
Om du avbryter händelse prenumerationen med hjälp av Unregister-Event cmdleten, tas händelse prenumeranten och den anpassade händelsen bort från sessionen.
Om du inte prenumererar på den anpassade händelsen måste du ändra programmets villkor eller stänga PowerShell-sessionen för att ta bort händelsen.

## EXEMPEL

### Exempel 1: skapa en ny händelse i händelse kön

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

Det här kommandot skapar en ny händelse i händelse kön i PowerShell.
Ett **Windows. timer** -objekt används för att skicka händelsen.

### Exempel 2: Utlös en händelse som svar på en annan händelse

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

Den här exempel funktionen använder cmdleten **New-Event** för att utlösa en händelse som svar på en annan händelse.
Kommandot använder Register-ObjectEvent-cmdlet för att prenumerera på händelsen Windows Management Instrumentation (WMI) som aktive ras när en ny process skapas.
Kommandot använder parametern *åtgärd* för cmdleten för att anropa cmdleten **New-Event** , som skapar den nya händelsen.

Eftersom händelserna som **nya** händelser aktive ras automatiskt läggs till i PowerShell-händelseloggen behöver du inte registrera dig för den händelsen.

## PARAMETRAR

### -EventArguments

Anger ett objekt som innehåller alternativ för händelsen.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

Anger ytterligare data som är associerade med händelsen.
Värdet för den här parametern visas i egenskapen **MessageData** för objektet event.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sender

Anger det objekt som aktiverar händelsen.
Standardvärdet är PowerShell-motorn.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Anger ett namn för den nya händelsen.
Den här parametern är obligatorisk och måste vara unik i sessionen.

Värdet för den här parametern visas i händelsens **SourceIdentifier** -egenskap.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PSEventArgs

## ANTECKNINGAR

Den nya anpassade händelsen, händelse prenumerationen och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR

[Hämta händelse](Get-Event.md)

[Registrera – EngineEvent](Register-EngineEvent.md)

[Registrera – ObjectEvent](Register-ObjectEvent.md)

[Ta bort händelse](Remove-Event.md)

[Avregistrera-händelse](Unregister-Event.md)

[Vänta-händelse](Wait-Event.md)
