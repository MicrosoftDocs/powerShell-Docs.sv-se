---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/31/2020
ms.locfileid: "93268821"
---
# Register-WmiEvent

## SAMMANFATTNING
Prenumererar på en Windows Management Instrumentation (WMI)-händelse.

## SYNTAX

### klass (standard)

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### DocumentDB

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Register-WmiEvent`Cmdleten prenumererar på Windows Management Instrumentation (WMI)-händelser på den lokala datorn eller på en fjärrdator.

När den prenumererade WMI-händelsen höjs, läggs den till i händelse kön i din lokala session även om händelsen inträffar på en fjärrdator. Använd cmdleten för att hämta händelser i händelse kön `Get-Event` .

Du kan använda parametrarna för `Register-WmiEvent` för att prenumerera på händelser på fjärrdatorer och ange egenskaps värden för de händelser som kan hjälpa dig att identifiera händelsen i kön. Du kan också använda **Åtgärds** parametern för att ange åtgärder som ska vidtas när en prenumeration aktive ras.

När du prenumererar på en händelse läggs en händelse prenumerant till i sessionen. Använd cmdleten för att hämta händelse prenumeranterna i sessionen `Get-EventSubscriber` . Om du vill avbryta prenumerationen använder du `Unregister-Event` cmdleten, som tar bort händelse prenumeranten från sessionen.

Nya Common Information Model-cmdlet: ar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets. CIM-cmdlets följer WS-Management (WSMan)-standarder och med CIM-standarden, som gör att cmdlets kan använda samma metoder för att hantera datorer som kör Windows-operativsystemet och de som kör andra operativ system. I stället för att använda bör `Register-WmiEvent` du överväga att använda cmdleten [register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) .

## EXEMPEL

### Exempel 1: prenumerera på händelser som genererats av en klass

Det här kommandot prenumererar på händelser som genererats av klassen **Win32_ProcessStartTrace** . Den här klassen aktiverar en händelse när en process startar.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### Exempel 2: prenumerera på skapande händelser för en process

Det här kommandot använder en fråga för att prenumerera på händelser för Win32_process instans skapande.

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### Exempel 3: Använd en åtgärd för att svara på en händelse

Det här exemplet visar hur du använder en åtgärd för att svara på en händelse. I det här fallet `Start-Process` skrivs alla kommandon i den aktuella sessionen till en XML-fil när en process startar.

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

När du använder **Åtgärds** parametern, `Register-WmiEvent` returnerar ett bakgrunds jobb som representerar händelse åtgärden. Du kan använda **jobb** -cmdletar, till exempel `Get-Job` och `Receive-Job` , för att hantera händelse jobbet.

Mer information finns i artikeln om jobb.

### Exempel 4: registrera dig för händelser på en fjärrdator

Det här exemplet registrerar händelser på fjärrdatorn Server01.

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

WMI returnerar händelserna till den lokala datorn och lagrar dem i händelse kön i den aktuella sessionen. Hämta händelserna genom att köra ett lokalt `Get-Event` kommando.

## PARAMETRAR

### -Åtgärd

Anger kommandon som hanterar händelser. Kommandona i **Åtgärds** parametern körs när en händelse höjs i stället för att skicka händelsen till händelse kön. Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.

Värdet för **åtgärden** kan omfatta `$Event` `$EventSubscriber` variablerna,, `$Sender` , `$EventArgs` och för `$Args` Automatiska variabler, som innehåller information om händelsen till **Åtgärds** skript blocket. Mer information finns i about_Automatic_Variables.

När du anger en åtgärd `Register-WmiEvent` returnerar ett händelse jobb objekt som representerar den åtgärden. Du kan använda de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletar) för att hantera händelse jobbet.

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

### – Klass

Anger händelsen som du prenumererar på. Ange den WMI-klass som genererar händelserna. Det krävs en **klass** -eller **frågeparameter** -parameter i varje kommando.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger namnet på den dator där kommandot körs. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för datorn. Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Forward

Anger att denna cmdlet skickar händelser för den här prenumerationen till sessionen på den lokala datorn.
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

Anger maximalt antal utlösare.

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

Anger eventuella ytterligare data som ska associeras med den här händelse prenumerationen. Värdet för den här parametern visas i egenskapen **MessageData** för alla händelser som är associerade med den här prenumerationen.

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

### – Namnrymd

Anger namn området för WMI-klassen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fråga

Anger en fråga i WMI Query Language (WQL) som identifierar händelse klassen WMI, t `select * from __InstanceDeletionEvent` . ex.:.

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

Anger ett namn som du väljer för prenumerationen. Det namn du väljer måste vara unikt i den aktuella sessionen. Standardvärdet är det GUID som Windows PowerShell tilldelar.

Värdet för den här parametern visas i värdet för egenskapen **SourceIdentifier** för Subscriber-objektet och för alla händelse objekt som är associerade med den här prenumerationen.

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

Anger att denna cmdlet döljer händelse prenumerationen. Använd den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och den bör inte identifieras separat.

Om du vill visa eller avbryta en prenumeration som har skapats med hjälp av parametern **SupportEvent** anger du **Force** -parametern `Get-EventSubscriber` för `Unregister-Event` cmdletarna och.

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

### -Timeout

Anger hur lång tid Windows PowerShell väntar på att kommandot ska slutföras.

Standardvärdet, 0 (noll), innebär att det inte finns någon tids gräns och det gör att Windows PowerShell väntar oändligt.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Om du vill använda den här cmdleten i Windows Vista eller en senare version av operativ systemet Windows startar du Windows PowerShell med alternativet Kör som administratör.

Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen. Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.

## RELATERADE LÄNKAR
