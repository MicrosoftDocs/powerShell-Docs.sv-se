---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264609"
---
# Set-ScheduledJobOption

## SAMMANFATTNING
Ändrar jobb alternativen för ett schemalagt jobb.

## SYNTAX

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Set-ScheduledJobOptions** ändrar jobb alternativen för schemalagda jobb.

Om du vill ändra alternativen för ett schemalagt jobb börjar du med att använda Get-ScheduledJobOption-cmdlet för att hämta jobb alternativen för ett schemalagt jobb.
Sedan kan du ange alternativen för **set-ScheduledJobOption** eller spara alternativen i en variabel och använda *InputObject* -parametern för cmdleten **set-ScheduledJobOption** för att identifiera alternativen.
Använd de återstående parametrarna för **set-ScheduledJobOption** för att ändra jobb alternativen.

Om du vill aktivera ett jobb alternativ använder du parametern som anger det alternativet.
Om du vill inaktivera ett alternativ skriver du parameter namnet, ett kolon (:) och $False.
Om du till exempel vill inaktivera alternativet *RunElevated* skriver du `-RunElevated:$False` .

Varje jobb alternativ-objekt innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så associationen med det schemalagda jobbet bevaras när jobb alternativen ändras.

Alternativen för schemalagda jobb avgör hur jobbet körs när Schemaläggaren startas.
Dessa alternativ gäller inte när du använder Start-Job-cmdlet för att starta ett schemalagt jobb.

**Set-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Ändra jobb alternativ

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
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
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

Det här exemplet visar hur du ändrar alternativen för ett schemalagt jobb på den lokala datorn.

Det första kommandot använder cmdleten Get-ScheduledJobOption för att hämta jobb alternativen för det schemalagda jobbet DeployPackage.
Utdata visar att egenskaperna WakeToRun och RunElevated har angetts till $False.

Det här kommandot krävs inte. den ingår bara för att Visa effekterna av alternativ ändringen.

### Exempel 2: ändra ett alternativ för alla schemalagda Fjärrjobb

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

Det här kommandot ändrar värdet för *idleTimeout* från en timme (standardvärdet) till två timmar för alla schemalagda jobb på den Server01 datorn.

Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.

Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.
De schemalagda jobben är skickas till Get-ScheduledJobOption-cmdleten, som hämtar jobb alternativen för de schemalagda jobben.
Varje jobb alternativ-objekt innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så objektets alternativ förblir kopplade till det schemalagda jobbet även om det ändras.

Jobb utlösarna är skickas till cmdleten **set-ScheduledJobOption** , som ändrar värdet för alternativet *idleTimeout* till två timmar (2:00:00).

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

Även om en aktivitet är dold kan användarna Visa uppgiften genom att välja Visa **dolda aktiviteter** i Schemaläggaren.

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

Ange ett TimeSpan-objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.

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
Anger hur länge datorn måste vara inaktiv innan jobbet startas.
Standardvärdet är 10 minuter.
Om datorn inte är inaktiv under den angivna tiden innan värdet för **idleTimeout** går ut, körs inte det schemalagda jobbet förrän nästa schemalagda tid, om det finns.

Ange ett TimeSpan-objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.

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

### – InputObject
Anger jobb alternativen.
Ange en variabel som innehåller **ScheduledJobOptions** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobOptions** -objekt, till exempel ett Get-ScheduledJobOption-kommando.
Du kan också skicka ett **ScheduledJobOptions** -objekt till **set-ScheduledJobOption**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -MultipleInstancePolicy
Fastställer hur systemet svarar på en begäran om att starta en instans av ett schemalagt jobb medan en annan instans av jobbet körs.
De acceptabla värdena för den här parametern är:

- IgnoreNew.
Den nya jobb instansen ignoreras.
Detta är standardvärdet.
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

### – PassThru
Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

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

Parametern **RunElevated** anger värdet för egenskapen **RunElevated** för schemalagda jobb till true.

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
Startar det schemalagda jobbet om datorn har varit inaktiv under den tid som anges av parametern **IdleDuration** innan den tid som anges av parametern *idleTimeout* upphör att gälla.

Som standard ignoreras parametrarna *IdleDuration* och *idleTimeout* och jobbet startar vid den schemalagda start tiden även om datorn är upptagen.

Om du anger den här parametern och datorn är upptagen (inte inaktiv) vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om det finns någon.

Parametern *StartIfIdle* anger värdet för egenskapen **StartIfNotIdle** för schemalagda jobb till false.

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
Standardvärdet är false.

Parametern *StartIfOnBattery* anger värdet för egenskapen **StartIfOnBatteries** för schemalagda jobb till $true.

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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions
Du kan skicka ett objekt med alternativ för schemalagda jobb till **set-ScheduledJobOption**.

## UTDATA

### Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions
När du använder parametern *Passthru* returnerar **set-ScheduledJobOption** de jobb alternativ som ändrades.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

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
