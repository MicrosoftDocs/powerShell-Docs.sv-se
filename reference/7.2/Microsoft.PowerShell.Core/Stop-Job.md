---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 479c099d2d5daf1cc50c5c645be053ff4ae02bdc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709979"
---
# Stop-Job

## SAMMANFATTNING
Stoppar ett PowerShell-bakgrunds jobb.

## SYNTAX

### SessionIdParameterSet (standard)

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Stop-Job`Cmdleten stoppar PowerShell-bakgrunds jobb som pågår. Du kan använda den här cmdleten för att stoppa alla jobb eller stoppa valda jobb baserat på namn, ID, instans-ID eller tillstånd, eller genom att skicka ett jobb objekt till `Stop-Job` .

Du kan använda `Stop-Job` för att stoppa bakgrunds jobb, till exempel de som startades med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet. När du stoppar ett bakgrunds jobb Slutför PowerShell alla uppgifter som väntar i jobbkön och avslutar sedan jobbet. Inga nya aktiviteter läggs till i kön när det här kommandot har skickats.

Den här cmdleten tar inte bort bakgrunds jobb. Använd cmdleten om du vill ta bort ett jobb `Remove-Job` .

Från och med Windows PowerShell 3,0 `Stop-Job` stoppas även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb. Om du vill `Stop-Job` stoppa ett jobb med anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Stop-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen. Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.

## EXEMPEL

### Exempel 1: stoppa ett jobb på en fjärrdator med hjälp av Invoke-Command

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.

Eftersom jobbet startades med hjälp av `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på distans, lagras jobbobjektet på fjärrdatorn. Du måste använda ett annat `Invoke-Command` kommando om du vill köra ett `Stop-Job` kommando via fjärr anslutning. Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.

Det första kommandot skapar en PowerShell-session (**PSSession**) på Server01-datorn och lagrar sedan Session-objektet i `$s` variabeln. Kommandot använder autentiseringsuppgifterna för en domän administratör.

Det andra kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i sessionen. Kommandot i jobbet hämtar alla händelser i system händelse loggen. Resulterande jobb objekt lagras i `$j` variabeln.

Det tredje kommandot stoppar jobbet. Den använder `Invoke-Command` cmdleten för att köra ett `Stop-Job` kommando i **PSSession** på Server01. Eftersom jobb objekt lagras i `$j` , vilket är en variabel på den lokala datorn, använder kommandot Använd omfångs modifieraren för att identifiera `$j` som en lokal variabel.
Mer information om hur du använder omfångs modifieraren finns [about_Remote_Variables](about/about_Remote_Variables.md).

När kommandot har slutförts stoppas jobbet och **PSSession** i `$s` är tillgängligt för användning.

### Exempel 2: stoppa ett bakgrunds jobb

```powershell
Stop-Job -Name "Job1"
```

Det här kommandot stoppar bakgrunds jobbet Job1.

### Exempel 3: stoppa flera bakgrunds jobb

```powershell
Stop-Job -Id 1, 3, 4
```

Det här kommandot stoppar tre jobb.
Den identifierar dem med deras ID.

### Exempel 4: stoppa alla bakgrunds jobb

```powershell
Get-Job | Stop-Job
```

Det här kommandot stoppar alla bakgrunds jobb i den aktuella sessionen.

### Exempel 5: stoppa alla blockerade bakgrunds jobb

```powershell
Stop-Job -State Blocked
```

Det här kommandot stoppar alla jobb som blockeras.

### Exempel 6: stoppa ett jobb med hjälp av ett instans-ID

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

Kommandona visar hur du stoppar ett jobb baserat på dess instans-ID.

Det första kommandot använder `Get-Job` cmdleten för att hämta jobben i den aktuella sessionen. Kommandot använder en pipeline-operator ( `|` ) för att skicka jobben till ett `Format-Table` kommando, som visar en tabell med de angivna egenskaperna för varje jobb. Tabellen innehåller instans-ID för varje jobb. Den använder en beräknad egenskap för att visa jobb status.

Det andra kommandot använder ett `Stop-Job` kommando som har **InstanceID** -parametern för att stoppa ett valt jobb.

### Exempel 7: stoppa ett jobb på en fjärrdator

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.

Eftersom jobbet startades med hjälp av parametern **AsJob** i `Invoke-Command` cmdleten, finns jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorn. Därför kan du använda ett lokalt `Stop-Job` kommando för att stoppa jobbet.

Det första kommandot använder `Invoke-Command` cmdleten för att starta ett bakgrunds jobb på Server01-datorn. Kommandot använder parametern **AsJob** för att köra fjärrkommandot som ett bakgrunds jobb.

Det här kommandot returnerar ett jobb objekt, vilket är samma jobb objekt som `Start-Job` cmdleten returnerar.
Kommandot sparar jobbobjektet i `$j` variabeln.

Det andra kommandot använder en pipeline-operator för att skicka jobbet i `$j` variabeln till `Stop-Job` . Kommandot använder parametern **Passthru** för att dirigera `Stop-Job` för att returnera ett jobb objekt. Jobb objekts visningen bekräftar att jobbets tillstånd har stoppats.

Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.

## PARAMETRAR

### -Filter

Anger en hash-tabell med villkor. Denna cmdlet stoppar jobb som uppfyller alla villkor.
Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb. Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten. Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ID

Anger ID: n för jobb som denna cmdlet stoppar. Standardvärdet är alla jobb i den aktuella sessionen.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen. Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n, avgränsade med kommatecken. Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID: n för jobb som denna cmdlet stoppar. Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn. Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Jobb

Anger de jobb som denna cmdlet stoppar. Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben. Du kan också använda en pipeline-operatör för att skicka jobb till `Stop-Job` cmdleten. Som standard `Stop-Job` tar bort alla jobb som startades i den aktuella sessionen.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger egna namn på jobb som denna cmdlet stoppar. Ange jobb namnen i en kommaavgränsad lista eller Använd jokertecken (*) för att ange ett jobb namns mönster. Som standard `Stop-Job` stoppas alla jobb som skapas i den aktuella sessionen.

Eftersom det egna namnet inte garanterat är unikt använder du parametrarna **whatIf** och **Confirm** när du stoppar jobb efter namn.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tillstånd

Anger ett jobb tillstånd. Denna cmdlet stoppar endast jobb i det angivna läget. De acceptabla värdena för den här parametern är:

- NotStarted
- Körs
- Slutförd
- Misslyckad
- Stoppad
- Blockerad
- Inaktiverad
- Frånkopplad
- Pausar
- Stoppas

Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
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

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

### System. Management. Automation. RemotingJob

Du kan skicka vidare ett jobb objekt till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PSRemotingJob

Den här cmdleten returnerar ett jobb objekt, om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Invoke-kommando](Invoke-Command.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Start – jobb](Start-Job.md)

[Wait-Job](Wait-Job.md)

[about_Job_Details](About/about_Job_Details.md)

[about_Remote_Jobs](About/about_Remote_Jobs.md)

[about_Remote_Variables](About/about_Remote_Variables.md)

[about_Jobs](About/about_Jobs.md)

[about_Scopes](About/about_scopes.md)
