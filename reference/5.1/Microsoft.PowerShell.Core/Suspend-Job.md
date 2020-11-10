---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 9b18782fae77fa0776aa2cfaa39b74a2292099d9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388475"
---
# Suspend-Job

## SAMMANFATTNING
Stoppar tillfälligt arbets flödes jobb.

## SYNTAX

### SessionIdParameterSet (standard)

```
Suspend-Job [-Force] [-Wait] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobParameterSet

```
Suspend-Job [-Job] <Job[]> [-Force] [-Wait] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### NameParameterSet

```
Suspend-Job [-Force] [-Wait] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceIdParameterSet

```
Suspend-Job [-Force] [-Wait] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FilterParameterSet

```
Suspend-Job [-Force] [-Wait] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### StateParameterSet

```
Suspend-Job [-Force] [-Wait] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Suspend-Job`Cmdleten pausar arbets flödes jobben. Suspend innebär att tillfälligt avbryta eller pausa ett arbets flödes jobb. Med den här cmdleten kan användare som kör arbets flöden pausa arbets flödet. Den kompletterar aktiviteten pausa – arbets flöde https://go.microsoft.com/fwlink/?LinkId=267141 , som är ett kommando i arbets flödet som gör uppehåll i arbets flödet.

`Suspend-Job`Cmdleten fungerar bara för arbets flödes jobb. Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten.

Du identifierar ett arbets flödes jobb genom att leta efter värdet PSWorkflowJob i **PSJobTypeName** -egenskapen för jobbet. Information om hur du avgör om en viss anpassad Jobbtyp stöder `Suspend-Job` cmdleten finns i hjälp avsnitten för den anpassade jobb typen.

När du pausar ett arbets flödes jobb körs arbets flödes jobbet till nästa kontroll punkt, pausar och returnerar omedelbart ett arbets flödes jobb objekt. Om du vill vänta tills SUS pensionen har slutförts innan du hämtar jobbet använder du parametern **wait** i `Suspend-Job` eller `Wait-Job` cmdleten. När arbets flödes jobbet har pausats pausas värdet för jobbets **tillstånds** egenskap.

Att pausa är korrekt beroende av kontroll punkter. Det aktuella jobbets tillstånd, metadata och utdata sparas i kontroll punkten så att arbets flödes jobbet kan återupptas utan att tillstånd eller data går förlorade. Om arbets flödes jobbet inte har kontroll punkter, kan det inte inaktive ras på rätt sätt. Om du vill lägga till kontroll punkter till ett arbets flöde som du kör använder du arbets flödets gemensamma parameter i **PSPersist** . Du kan använda **Force** -parametern för att pausa eventuella arbets flödes jobb omedelbart och pausa ett arbets flödes jobb som inte har några kontroll punkter, men åtgärden kan orsaka förlust av tillstånd och data.

Innan du använder en jobb-cmdlet på en anpassad Jobbtyp, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), importerar du modulen som stöder den anpassade jobb typen, antingen genom att använda `Import-Module` cmdleten eller använda eller använda en cmdlet i modulen.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: pausa ett arbets flödes jobb efter namn

Det här exemplet visar hur du pausar ett arbets flödes jobb.

Det första kommandot skapar `Get-SystemLog` arbets flödet. Arbets flödet använder `CheckPoint-Workflow` aktiviteten för att definiera en kontroll punkt i arbets flödet.

Det andra kommandot använder parametern **AsJob** som är gemensam för alla arbets flöden för att köra `Get-SystemLog` arbets flödet som ett bakgrunds jobb. Kommandot använder den gemensamma parametern **JobName** Workflow för att ange ett eget namn för arbets flödes jobbet.

Det tredje kommandot använder `Get-Job` cmdleten för att hämta `Get-SystemLogJob` arbets flödes jobbet. Utdata visar att värdet för egenskapen **PSJobTypeName** är PSWorkflowJob.

Det fjärde kommandot använder `Suspend-Job` cmdleten för att pausa `Get-SystemLogJob` jobbet. Jobbet körs till kontroll punkten och pausar sedan.

```
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```


### Exempel 2: pausa och återuppta ett arbets flödes jobb

Det här exemplet visar hur du pausar och återupptar ett arbets flödes jobb.

Det första kommandot pausar LogWorkflowJob-jobbet. Kommandot returnerar omedelbart. Utdata visar att arbets flödes jobbet fortfarande körs, även om det har pausats.

Det andra kommandot använder `Get-Job` cmdleten för att hämta LogWorkflowJob-jobbet. Utdata visar att arbets flödes jobbet har pausats.

Det tredje kommandot använder `Get-Job` cmdleten för att hämta LogWorkflowJob-jobbet och `Resume-Job` cmdleten för att återuppta det. Utdata visar att arbets flödes jobbet har återupptagits och körs nu.

```
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```


### Exempel 3: pausa ett arbets flödes jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

Det här kommandot använder `Invoke-Command` cmdleten för att pausa ett arbets flödes jobb på fjärrdatorn SRV01. Värdet för **filter** parametern är en hash-tabell som anger ett CustomID-värde.
Den här **CustomID** är jobb-metadata ( **PSPrivateMetadata** ).

### Exempel 4: vänta tills arbets flödes jobbet har pausats

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

Det här kommandot pausar arbets flödes jobbet VersionCheck. Kommandot använder parametern **wait** för att vänta tills arbets flödes jobbet har pausats. När arbets flödes jobbet körs till nästa kontroll punkt och har pausats, slutförs kommandot och jobbobjektet returneras.

### Exempel 5: tvinga en arbets flödes uppgift att pausa

```
PS C:\> Suspend-Job Maintenance -Force
```

Det här kommandot pausar jobbets tvingande arbets flödes jobb. Det finns inga kontroll punkter för underhålls jobbet. Den kan inte inaktive ras korrekt och kanske inte återupptas korrekt.

## PARAMETRAR

### -Filter

Anger en hash-tabell med villkor. Denna cmdlet pausar jobb som uppfyller alla villkor.
Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.

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

### -Force

Pausar arbets flödes jobbet omedelbart. Den här åtgärden kan leda till förlust av tillstånd och data.

Som standard `Suspend-Job` kan arbets flödes jobbet köras fram till nästa kontroll punkt och sedan Pausa det.
Du kan också använda den här parametern för att pausa arbets flödes jobb som inte har kontroll punkter.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: F

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger ID: n för jobb som denna cmdlet pausar.

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen. Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen. Du kan ange ett eller flera ID: n, avgränsade med kommatecken. Använd cmdleten för att hitta ID: t för ett jobb `Get-Job` .

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InstanceId

Anger instans-ID: n för jobb som denna cmdlet pausar. Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn. Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Jobb

Anger de arbets flödes jobb som denna cmdlet stoppar. Ange en variabel som innehåller arbets flödes jobben eller ett kommando som hämtar arbets flödes jobben. Du kan också skicka ett arbets flödes jobb till `Suspend-Job` cmdlet: en.

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger egna namn på jobb som denna cmdlet pausar. Ange ett eller flera arbets flödes jobb namn.
Jokertecken stöds.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

`Suspend-Job` pausar endast arbets flödes jobb i **körnings** läge.

Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Vänta

Anger att denna cmdlet förhindrar kommando tolken tills arbets flödes jobbet har tillståndet Suspended. Som standard `Suspend-Job` returneras omedelbart, även om arbets flödes jobbet ännu inte har pausats.

Parametern **wait** motsvarar att skicka ett `Suspend-Job` kommando till `Wait-Job` cmdlet: en.

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

### System. Management. Automation. job

Du kan skicka vidare alla typer av jobb till denna cmdlet. Men om `Suspend-Job` hämtar ett jobb av en typ som inte stöds returneras ett avslutande fel.

## UTDATA

### System. Management. Automation. job
Denna cmdlet returnerar de jobb som den pausade.

## ANTECKNINGAR

- Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen. Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en databas.
- Om du skickar ett arbets flödes jobb som inte är i körnings tillstånd `Suspend-Job` visas ett varnings meddelande. Om du vill utelämna varningen använder du den gemensamma parametern **WarningAction** med värdet SilentlyContinue.

  Om ett jobb inte är av en typ som har stöd för att pausa, `Suspend-Job` returnerar ett avslutande fel.

- Om du vill hitta de arbets flödes jobb som har pausats, inklusive de som har avbrutits med denna cmdlet, använder du cmdleten **State** för `Get-Job` cmdleten för att hämta arbets flödes jobb i tillståndet Suspended.
- Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet.
  Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Återuppta – jobb](Resume-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
