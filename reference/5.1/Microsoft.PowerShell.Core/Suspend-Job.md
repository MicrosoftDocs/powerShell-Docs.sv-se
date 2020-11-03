---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/suspend-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Job
ms.openlocfilehash: 6ab50342e963832d89b3dfc4128a22fc16405926
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264134"
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
Cmdleten **suspend-Job** pausar arbets flödes jobben.
Suspend innebär att tillfälligt avbryta eller pausa ett arbets flödes jobb.
Med den här cmdleten kan användare som kör arbets flöden pausa arbets flödet.
Den kompletterar aktiviteten pausa – arbets flöde https://go.microsoft.com/fwlink/?LinkId=267141 , som är ett kommando i arbets flödet som gör uppehåll i arbets flödet.

Cmdleten **suspend-Job** fungerar bara på arbets flödes jobb.
Den fungerar inte på vanliga bakgrunds jobb, t. ex. de som har startats med hjälp av Start-Job-cmdleten.

Du identifierar ett arbets flödes jobb genom att leta efter värdet PSWorkflowJob i **PSJobTypeName** -egenskapen för jobbet.
För att avgöra om en viss anpassad Jobbtyp stöder **PAUSE-Job-** cmdleten, se hjälp avsnitten för den anpassade jobb typen.

När du pausar ett arbets flödes jobb körs arbets flödes jobbet till nästa kontroll punkt, pausar och returnerar omedelbart ett arbets flödes jobb objekt.
Vänta tills SUS pensionen har slutförts innan du hämtar jobbet genom att använda *wait* -parametern i **suspend-Job** eller Wait-Job-cmdleten.
När arbets flödes jobbet har pausats pausas värdet för jobbets **tillstånds** egenskap.

Att pausa är korrekt beroende av kontroll punkter.
Det aktuella jobbets tillstånd, metadata och utdata sparas i kontroll punkten så att arbets flödes jobbet kan återupptas utan att tillstånd eller data går förlorade.
Om arbets flödes jobbet inte har kontroll punkter, kan det inte inaktive ras på rätt sätt.
Om du vill lägga till kontroll punkter till ett arbets flöde som du kör använder du arbets flödets gemensamma parameter i *PSPersist* .
Du kan använda *Force* -parametern för att pausa eventuella arbets flödes jobb omedelbart och pausa ett arbets flödes jobb som inte har några kontroll punkter, men åtgärden kan orsaka förlust av tillstånd och data.

Innan du använder en jobb-cmdlet på en anpassad Jobbtyp, till exempel ett arbets flödes jobb ( **PSWorkflowJob** ), importerar du modulen som stöder den anpassade jobb typen, antingen genom att använda Import-Module-cmdlet eller använda eller använda en cmdlet i modulen.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: pausa ett arbets flödes jobb efter namn

```
The first command creates the Get-SystemLog workflow. The workflow uses the CheckPoint-Workflow activity to define a checkpoint in the workflow.
#Sample WorkflowWorkflow Get-SystemLog
{
    $Events = Get-WinEvent -LogName System
    CheckPoint-Workflow
    InlineScript {\\Server01\Scripts\Analyze-SystemEvents.ps1 -Events $Events}
}

The second command uses the *AsJob* parameter that is common to all workflows to run the Get-SystemLog workflow as a background job. The command uses the *JobName* workflow common parameter to specify a friendly name for the workflow job.
PS C:\> Get-SystemLog -AsJob -JobName "Get-SystemLogJob"

The third command uses the **Get-Job** cmdlet to get the Get-SystemLogJob workflow job. The output shows that the value of the **PSJobTypeName** property is PSWorkflowJob.
PS C:\> Get-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Running     True            localhost   Get-SystemLog

The fourth command uses the **Suspend-Job** cmdlet to suspend the Get-SystemLogJob job. The job runs to the checkpoint and then suspends.
PS C:\> Suspend-Job -Name Get-SystemLogJob
Id     Name              PSJobTypeName   State       HasMoreData     Location   Command
--     ----              -------------   -----       -----------     --------   -------
4      Get-SystemLogJob  PSWorkflowJob   Suspended   True            localhost   Get-SystemLog
```

Det här exemplet visar hur du pausar ett arbets flödes jobb.

### Exempel 2: pausa och återuppta ett arbets flödes jobb

```
The first command suspends the LogWorkflowJob job.The command returns immediately. The output shows that the workflow job is still running, even though it is being suspended.
PS C:\> Suspend-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow

The second command uses the **Get-Job** cmdlet to get the LogWorkflowJob job. The output shows that the workflow job suspended successfully.
PS C:\> Get-Job -Name LogWorkflowJob
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Suspended     True            localhost            LogWorkflow

The third command uses the **Get-Job** cmdlet to get the LogWorkflowJob job and the Resume-Job cmdlet to resume it. The output shows that the workflow job resumed successfully and is now running.
PS C:\> Get-Job -Name LogWorkflowJob | Resume-Job
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
67     LogflowJob    PSWorkflowJob      Running       True            localhost            LogWorkflow
```

Det här exemplet visar hur du pausar och återupptar ett arbets flödes jobb.

### Exempel 3: pausa ett arbets flödes jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Srv01 -Scriptblock {Suspend-Job -Filter @{CustomID="031589"}
```

Det här kommandot använder cmdleten Invoke-Command för att pausa ett arbets flödes jobb på fjärrdatorn SRV01.
Värdet för *filter* parametern är en hash-tabell som anger ett CustomID-värde.
Den här **CustomID** är jobb-metadata ( **PSPrivateMetadata** ).

### Exempel 4: vänta tills arbets flödes jobbet har pausats

```
PS C:\> Suspend-Job VersionCheck -Wait
Id     Name          PSJobTypeName      State         HasMoreData     Location             Command
--     ----          -------------      -----         -----------     --------             -------
 5     VersionCheck  PSWorkflowJob      Suspended     True            localhost            LogWorkflow
```

Det här kommandot pausar arbets flödes jobbet VersionCheck.
Kommandot använder parametern *wait* för att vänta tills arbets flödes jobbet har pausats.
När arbets flödes jobbet körs till nästa kontroll punkt och har pausats, slutförs kommandot och jobbobjektet returneras.

### Exempel 5: tvinga en arbets flödes uppgift att pausa

```
PS C:\> Suspend-Job Maintenance -Force
```

Det här kommandot pausar jobbets tvingande arbets flödes jobb.
Det finns inga kontroll punkter för underhålls jobbet.
Den kan inte inaktive ras korrekt och kanske inte återupptas korrekt.

## PARAMETRAR

### -Filter
Anger en hash-tabell med villkor.
Denna cmdlet pausar jobb som uppfyller alla villkor.
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
Pausar arbets flödes jobbet omedelbart.
Den här åtgärden kan leda till förlust av tillstånd och data.

Som standard tillåter **pausa – jobb** att arbets flödes jobbet körs tills nästa kontroll punkt och sedan pausar det.
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

ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.
Det är lättare att komma ihåg och att ange än instans-ID, men det är endast unikt i den aktuella sessionen.
Du kan ange ett eller flera ID: n, avgränsade med kommatecken.
Använd Get-Job-cmdleten för att hitta ID: t för ett jobb.

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
Anger instans-ID: n för jobb som denna cmdlet pausar.
Standardvärdet är alla jobb.

Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.
Använd **Get-Job** för att hitta instans-ID för ett jobb.

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
Anger de arbets flödes jobb som denna cmdlet stoppar.
Ange en variabel som innehåller arbets flödes jobben eller ett kommando som hämtar arbets flödes jobben.
Du kan också skicka arbets flödes jobb till cmdlet: en **suspend-Job** .

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
Anger egna namn på jobb som denna cmdlet pausar.
Ange ett eller flera arbets flödes jobb namn.
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
Anger ett jobb tillstånd.
Denna cmdlet stoppar endast jobb i det angivna läget.
De acceptabla värdena för den här parametern är:

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

**Pausa – jobbet** pausar endast arbets flödes jobb i **körnings** läge.

Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.

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
Anger att denna cmdlet förhindrar kommando tolken tills arbets flödes jobbet har tillståndet Suspended.
Som standard returnerar **suspend-jobbet** omedelbart, även om arbets flödes jobbet ännu inte är i pausat läge.

Parametern *wait* motsvarar ett **suspend-Job-** kommando till **wait-Job** -cmdleten.

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

### System. Management. Automation. job
Du kan skicka vidare alla typer av jobb till denna cmdlet.
Om **PAUSE-jobbet** däremot får ett jobb av en typ som inte stöds returneras ett avslutande fel.

## UTDATA

### System. Management. Automation. job
Denna cmdlet returnerar de jobb som den pausade.

## ANTECKNINGAR

* Mekanismen och platsen för att spara ett pausat jobb kan variera beroende på jobb typen. Till exempel sparas pausade arbets flödes jobb i ett Flat File-Arkiv som standard, men kan också sparas i en databas.
* Om du skickar ett arbets flödes jobb som inte är i körnings tillstånd visas ett varnings meddelande i **suspend-jobbet** . Om du vill utelämna varningen använder du den gemensamma parametern *WarningAction* med värdet SilentlyContinue.

  Om ett jobb inte är av en typ som har stöd för att pausa, returnerar **suspend-jobbet** ett avslutande fel.

* Om du vill hitta de arbets flödes jobb som har pausats, inklusive de som har pausats av denna cmdlet, använder du parametern *State* för cmdleten **Get-Job** för att hämta arbets flödes jobb i tillståndet Suspended.
* Vissa jobb typer har alternativ eller egenskaper som förhindrar att Windows PowerShell pausar jobbet. Om försök att pausa jobbet Miss lyckas, kontrollerar du att alternativen och egenskaperna för jobbet kan avbrytas.

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Återuppta – jobb](Resume-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
