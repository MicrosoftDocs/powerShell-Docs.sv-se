---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/wait-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Process
ms.openlocfilehash: 6fe942f98183a3b185adf5781699bf41d03db920
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343375"
---
# Wait-Process

## SAMMANFATTNING
Väntar på att processerna ska stoppas innan du accepterar mer information.

## SYNTAX

### Namn (standard)

```
Wait-Process [-Name] <String[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### Id

```
Wait-Process [-Id] <Int32[]> [[-Timeout] <Int32>] [<CommonParameters>]
```

### InputObject

```
Wait-Process [[-Timeout] <Int32>] -InputObject <Process[]> [<CommonParameters>]
```

## BESKRIVNING

`Wait-Process`Cmdleten väntar på att en eller flera processer som körs ska stoppas innan indatamängden accepteras. I PowerShell-konsolen ignorerar denna cmdlet kommando tolken tills processerna har stoppats. Du kan ange en process efter process namn eller process-ID (PID) eller skicka ett process objekt till `Wait-Process` .

`Wait-Process` fungerar bara på processer som körs på den lokala datorn.

## EXEMPEL

### Exempel 1: stoppa en process och vänta

```
PS C:\> $nid = (Get-Process notepad).id
PS C:\> Stop-Process -Id $nid
PS C:\> Wait-Process -Id $nid
```

Det här exemplet stoppar anteckningar-processen och väntar sedan på att processen ska stoppas innan nästa kommando fortsätter.

Det första kommandot använder `Get-Process` cmdleten för att hämta ID: t för anteckningar-processen. Den lagrar ID: t i `$nid` variabeln.

Det andra kommandot använder `Stop-Process` cmdleten för att stoppa processen med ID: t som lagras i `$nid` .

Det tredje kommandot använder `Wait-Process` för att vänta tills anteckningar-processen har stoppats. Den använder **ID-** parametern för `Wait-Process` för att identifiera processen.

### Exempel 2: Ange en process

```
PS C:\> $p = Get-Process notepad
PS C:\> Wait-Process -Id $p.id
PS C:\> Wait-Process -Name "notepad"
PS C:\> Wait-Process -InputObject $p
```

Dessa kommandon visar tre olika metoder för att ange en process för `Wait-Process` . Det första kommandot hämtar anteckningar-processen och lagrar dem i `$p` variabeln.

Det andra kommandot använder **ID-** parametern, det tredje kommandot använder parametern **Name** och det fjärde kommandot använder parametern **InputObject** .

Dessa kommandon har samma resultat och kan användas utbytbart.

### Exempel 3: vänta på processer under en angiven tid

```
PS C:\> Wait-Process -Name outlook, winword -Timeout 30
```

Det här kommandot väntar 30 sekunder på att Outlook-och Winword-processerna ska stoppas. Om båda processerna inte har stoppats visar cmdleten ett icke-avslutande fel och kommando tolken.

## PARAMETRAR

### -ID

Anger process-ID: n för processerna. Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.
Om du vill hitta ett process-ID skriver du `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases: PID, ProcessId

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – InputObject

Anger processerna genom att skicka process objekt. Ange en variabel som innehåller process objekt, eller Skriv ett kommando eller uttryck som hämtar process objekt, t `Get-Process` . ex. cmdleten.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger processernas process namn. Om du vill ange flera namn använder du kommatecken för att avgränsa namnen. Jokertecken stöds inte.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Timeout

Anger den maximala tiden, i sekunder, som denna cmdlet väntar på att de angivna processerna ska stoppas.
När det här intervallet går ut visar kommandot ett icke-avslutande fel som visar de processer som fortfarande körs och slutar vänta. Som standard finns det ingen tids gräns.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Diagnostics. process

Du kan skicka vidare ett process objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

Denna cmdlet använder metoden **WaitForExit** i klassen **system. Diagnostics. process** .

## RELATERADE LÄNKAR

[Fel sökning – process](Debug-Process.md)

[Hämta process](Get-Process.md)

[Start process](Start-Process.md)

[Stoppa – process](Stop-Process.md)

[Vänta-process](Wait-Process.md)
