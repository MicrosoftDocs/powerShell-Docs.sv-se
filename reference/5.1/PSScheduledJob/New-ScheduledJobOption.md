---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264644"
---
# New-ScheduledJobOption

## SAMMANFATTNING
Skapar ett objekt som innehåller avancerade alternativ för ett schemalagt jobb.

## SYNTAX

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **New-ScheduledJobOption** skapar ett objekt som innehåller avancerade alternativ för ett schemalagt jobb.

Du kan använda **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** returnerar för att ange jobb alternativ för ett nytt eller befintligt schemalagt jobb.
Du kan också ange jobb alternativ genom att använda Get-ScheduledJobOption cmdlet för att hämta jobb alternativen för ett befintligt schemalagt jobb eller genom att använda ett värde för hash-tabellen för att representera jobb alternativen.

Utan parametrar genererar **New-ScheduledJobOption** ett objekt som innehåller standardvärdena för alla alternativ.
Eftersom alla egenskaper utom jobb definitionen-egenskapen kan redige ras kan du använda det resulterande objektet som mall och skapa standard alternativ objekt för ditt företag.

När du skapar schemalagda jobb och anger alternativ för schemalagda jobb granskar du standardvärdena för alla alternativ för schemalagda jobb.
Schemalagda jobb körs bara när alla villkor som har angetts för körningen är uppfyllda.

**New-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: skapa ett alternativ objekt för schemalagda jobb med standardvärden

```
PS C:\> New-ScheduledJobOption
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

Det här kommandot skapar ett alternativ objekt för schemalagda jobb som har alla standardvärden.

### Exempel 2: skapa ett alternativ objekt för schemalagda jobb med anpassade värden

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

Följande kommando skapar ett schemalagt jobb objekt som kräver nätverket och kör det schemalagda jobbet även om datorn inte är ansluten till nätström.

Utdata visar att *RequireNetwork* -parametern har ändrat värdet för egenskapen RunWithoutNetwork till $false och *StartIfOnBattery* -parametern ändrade värdet för StartIfOnBatteries-egenskapen till $true.

### Exempel 3: Ange alternativ för ett nytt schemalagt jobb

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Det här exemplet visar hur du använder **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** returnerar för att ange alternativ för ett nytt schemalagt jobb.

### Exempel 4: sortera egenskaperna för ett alternativ objekt för schemalagda jobb

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

Det här exemplet visar hur du sorterar egenskaperna för ett **ScheduledJobOptions** -objekt i alfabetisk ordning för enkel läsning.

Det första kommandot använder cmdleten **New-ScheduledJobOption** för att skapa ett **ScheduledJobOptions** -objekt.
Kommandot använder parametern *WakeToRun* och sparar det resulterande objektet i variabeln $Options.

För att hämta egenskaperna för $Options som objekt använder det andra kommandot egenskapen **PSObject** för alla Windows PowerShell-objekt och dess egenskap egenskaper.
Kommandot rör sedan egenskaps objekt till Sort-Object-cmdlet, som sorterar egenskaperna i bokstavs ordning efter namn och sedan till Format-Table-cmdleten, som visar namn och värden för egenskaperna i en tabell.

Det här formatet gör det mycket enklare att hitta egenskapen WakeToRun för **ScheduledJobOptions** -objektet i $Options och för att kontrol lera att dess värde har ändrats från $False till $true.

## PARAMETRAR

### -ContinueIfGoingOnBattery
Stoppa inte det schemalagda jobbet om datorn växlar till batteri drift (koppla från växel ström) medan jobbet körs.
Schemalagda jobb stoppas som standard när datorn kopplas från växel ström.

Parametern *ContinueIfGoingOnBattery* anger värdet för egenskapen StopIfGoingOnBatteries för schemalagda jobb till $true.

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

### -DoNotAllowDemandStart
Starta bara jobbet när det utlöses.
Användare kan inte starta jobbet manuellt, t. ex. med hjälp av körnings funktionen i Schemaläggaren.

Den här parametern påverkar endast Schemaläggaren.
Den förhindrar inte att användare använder Start-Job cmdlet för att starta jobbet.

Parametern *DoNotAllowDemandStart* anger värdet för egenskapen DoNotAllowDemandStart för schemalagda jobb till $true.

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

### -HideInTaskScheduler
Visa inte jobbet i Schemaläggaren.
Det här värdet påverkar endast den dator där jobbet körs.
Som standard visas schemalagda aktiviteter i Schemaläggaren.

Även om en aktivitet är dold kan användarna Visa uppgiften genom att välja Visa dolda aktiviteter i Schemaläggaren.

Parametern *HideInTaskScheduler* anger värdet för egenskapen ShowInTaskScheduler för schemalagda jobb till $false.

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

### -IdleDuration
Anger hur länge datorn måste vara inaktiv innan jobbet startas.
Standardvärdet är 10 minuter.
Om datorn inte är inaktiv under den angivna tiden innan värdet för *idleTimeout* går ut, körs inte det schemalagda jobbet förrän nästa schemalagda tid, om det finns.

Ange ett **TimeSpan** -objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.

Använd parametern *StartIfIdle* om du vill aktivera det här värdet.
Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout
Anger hur länge det schemalagda jobbet väntar på att datorn ska vara inaktiv.
Om tids gränsen går ut innan datorn förblir inaktiv under den tids period som anges av parametern *IdleDuration* , körs inte jobbet förrän nästa schemalagda tid, om det finns.
Standardvärdet är en timme.

Ange ett **TimeSpan** -objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.

Använd parametern *StartIfIdle* om du vill aktivera det här värdet.
Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MultipleInstancePolicy
Fastställer hur systemet svarar på en begäran om att starta en instans av ett schemalagt jobb medan en annan instans av jobbet körs.
Standardvärdet är IgnoreNew.
De acceptabla värdena för den här parametern är:

- IgnoreNew.
Den nya jobb instansen ignoreras.
- Via.
Den nya jobb instansen startar omedelbart.
- Köjobb.
Den nya jobb instansen startar så snart den aktuella instansen har slutförts.
- StopExisting.
Den aktuella instansen av jobbet stoppas och den nya instansen startar.

För att köra jobbet måste alla villkor för projektschemat uppfyllas.
Om till exempel de villkor som anges av parametrarna *RequireNetwork* , *IdleDuration* och *idleTimeout* inte är uppfyllda, startas inte jobb instansen, oavsett värdet för den här parametern.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RequireNetwork
Kör bara det schemalagda jobbet när nätverks anslutningar är tillgängliga.

Om du anger den här parametern och nätverket inte är tillgängligt vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om något.

Parametern *RequireNetwork* anger värdet för egenskapen RunWithoutNetwork för schemalagda jobb till $false.

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

### -RestartOnIdleResume
Startar om ett schemalagt jobb när datorn blir inaktiv.
Den här parametern fungerar med parametern *StopIfGoingOffIdle* , som pausar ett pågående schemalagt jobb om datorn blir aktiv (lämnar inaktivt läge).

Parametern *RestartOnIdleResume* anger värdet för egenskapen RestartOnIdleResume för schemalagda jobb till $true.

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

### -RunElevated
Kör det schemalagda jobbet med behörigheterna för en medlem i gruppen Administratörer på den dator där jobbet körs.

Om du vill aktivera ett schemalagt jobb som ska köras med administratörs behörighet använder du parametern *Credential* i Register-ScheduledJob för att ange explicita autentiseringsuppgifter för jobbet.

Parametern *RunElevated* anger värdet för egenskapen RunElevated för schemalagda jobb till $true.

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

### -StartIfIdle
Startar det schemalagda jobbet om datorn har varit inaktiv under den tid som anges av parametern *IdleDuration* innan den tid som anges av parametern *idleTimeout* upphör att gälla.

Som standard ignoreras parametrarna *IdleDuration* och *idleTimeout* och jobbet startar vid den schemalagda start tiden även om datorn är upptagen.

Om du anger den här parametern och datorn är upptagen (inte inaktiv) vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om det finns någon.

Parametern *StartIfIdle* anger värdet för egenskapen StartIfNotIdle för schemalagda jobb till $false.

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

### -StartIfOnBattery
Startar det schemalagda jobbet även om datorn körs på batterier vid den schemalagda start tiden.
Standardvärdet är $False.

Parametern *StartIfOnBattery* anger värdet för egenskapen StartIfOnBatteries för schemalagda jobb till $true.

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

### -StopIfGoingOffIdle
Pausar ett pågående schemalagt jobb om datorn blir aktiv (inte inaktiv) medan jobbet körs.

Som standard är ett schemalagt jobb som pausas när datorn aktive ras när datorn blir inaktiv igen.
Om du vill ändra det här standard beteendet använder du parametern *RestartOnIdleResume* .

Parametern *StopIfGoingOffIdle* anger värdet för egenskapen StopIfGoingOffIdle för schemalagda jobb till $true.

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

### -WakeToRun
Aktiverar datorn från vilo läge eller vilo läge vid den schemalagda start tiden så att den kan köra jobbet.
Som standard körs inte jobbet om datorn är i vilo läge eller vilo läge vid den schemalagda start tiden.

Parametern *WakeToRun* anger värdet för egenskapen WakeToRun för schemalagda jobb till $true.

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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions

## ANTECKNINGAR

* Du kan använda **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** skapar som värdet för parametern *ScheduledJobOption* i Register-ScheduledJob-cmdleten. *ScheduledJobOption* -parametern kan dock också ta ett värde för hash-tabell som anger egenskaperna för **ScheduledJobOptions** -objektet och deras värden, till exempel:

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## RELATERADE LÄNKAR

[Add-JobTrigger](Add-JobTrigger.md)

[Disable-JobTrigger](Disable-JobTrigger.md)

[Disable-ScheduledJob](Disable-ScheduledJob.md)

[Aktivera – JobTrigger](Enable-JobTrigger.md)

[Aktivera – ScheduledJob](Enable-ScheduledJob.md)

[Get-JobTrigger](Get-JobTrigger.md)

[Get-ScheduledJob](Get-ScheduledJob.md)

[Get-ScheduledJobOption](Get-ScheduledJobOption.md)

[New-JobTrigger](New-JobTrigger.md)

[New-ScheduledJobOption](New-ScheduledJobOption.md)

[Registrera – ScheduledJob](Register-ScheduledJob.md)

[Remove-JobTrigger](Remove-JobTrigger.md)

[Set-JobTrigger](Set-JobTrigger.md)

[Set-ScheduledJob](Set-ScheduledJob.md)

[Set-ScheduledJobOption](Set-ScheduledJobOption.md)

[Avregistrera-ScheduledJob](Unregister-ScheduledJob.md)
