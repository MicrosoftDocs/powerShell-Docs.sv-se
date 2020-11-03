---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJobOption
ms.openlocfilehash: 5c317be9add0898137aceed6c39032f3e271bac1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264650"
---
# Get-ScheduledJobOption

## SAMMANFATTNING
Hämtar jobb alternativen för schemalagda jobb.

## SYNTAX

### Jobb definitionen (standard)

```
Get-ScheduledJobOption [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-ScheduledJobOption [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-ScheduledJobOption [-Name] <String> [<CommonParameters>]
```

## BESKRIVNING
**Get-ScheduledJobOption** -cmdlet: en hämtar jobb alternativen för schemalagda jobb.
Du kan använda det här kommandot för att undersöka jobb alternativen eller för att skicka vidare jobb alternativen till andra cmdletar.

Jobb alternativen sparas inte på disken oberoende av varandra. de ingår i ett schemalagt jobb.
Om du vill hämta jobb alternativen för ett schemalagt jobb anger du det schemalagda jobbet.

Använd parametrarna för **Get-ScheduledJobOption** -cmdlet: en för att identifiera det schemalagda jobbet.
Du kan identifiera schemalagda jobb baserat på namn eller identifikations nummer, eller genom att ange eller dirigera **ScheduledJob** -objekt, till exempel de som returneras av Get-ScheduledJob cmdlet, för att **Hämta-ScheduledJobOption**.

**Get-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Hämta jobb alternativ

```
PS C:\> Get-ScheduledJobOption -Name "*Backup*"
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

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

Det här kommandot hämtar jobb alternativen för schemalagda jobb som har säkerhets kopia i sina namn.
Resultaten visar objektet jobb alternativ som returnerar **-ScheduledJobOption** .

### Exempel 2: Hämta alla jobb alternativ

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption
```

Det här kommandot hämtar jobb alternativen för alla schemalagda jobb på den lokala datorn.

Den använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.
En pipeline-operator (|) skickar de schemalagda jobben till **Get-ScheduledJobOption** -cmdleten, som hämtar jobb alternativen för varje schemalagt jobb.

### Exempel 3: Hämta valda jobb alternativ

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun}
StartIfOnBatteries     : False

StopIfGoingOnBatteries : True

WakeToRun              : True

StartIfNotIdle         : True

StopIfGoingOffIdle     : False

RestartOnIdleResume    : False

IdleDuration           : 00:10:00

IdleTimeout            : 01:00:00

ShowInTaskScheduler    : True

RunElevated            : True

RunWithoutNetwork      : True

DoNotAllowDemandStart  : False

MultipleInstancePolicy : Ignore

NewJobDefinition       : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The second command shows how to find to which scheduled job the job options belong. This command uses a pipeline operator (|) to send the selected job options to the ForEach-Object cmdlet, which gets the JobDefinition property of each options object. The JobDefinition property contains the originating job object. The results show that the selected options came from the DeployPkg scheduled job.
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where {$_.RunElevated -and !$_.WaketoRun} | ForEach-Object {$_.JobDefinition}
Id         Name            Triggers        Command                                  Enabled

--         ----            --------        -------                                  -------

2          DeployPkg         {1, 2}        DeployPackage.ps1                        True
```

Det här exemplet visar hur du hittar jobb alternativ objekt med specifika värden.

Det första kommandot hämtar jobb alternativ där egenskapen RunElevated har värdet $True och egenskapen RunWithoutNetwork har värdet $False.
Utdata visar det valda **JobOptions** -objektet.

### Exempel 4: Använd jobb alternativ för att skapa ett nytt jobb

```
PS C:\> $Opts = Get-ScheduledJobOption -Name "BackupTestLogs"
PS C:\> Register-ScheduledJob -Name "Archive-Scripts" -FilePath "\\Srv01\Scripts\ArchiveScripts.ps1" -ScheduledJobOption $Opts
```

Det här exemplet visar hur du använder de jobb alternativ som Get-ScheduledJobOption får i ett nytt schemalagt jobb.

Det första kommandot använder **Get-ScheduledJobOption** för att hämta jobb alternativen för det schemalagda BackupTestLogs-jobbet.
Kommandot sparar alternativen i variabeln $Opts.

Det andra kommandot använder Register-ScheduledJob cmdlet för att skapa ett nytt schemalagt jobb.
Värdet för parametern *ScheduledJobOption* är Options-objektet i variabeln $opts.

### Exempel 5: Hämta jobb alternativ från en fjärran sluten dator

```
PS C:\> $O = Invoke-Command -ComputerName "Srv01" -ScriptBlock {Get-ScheduledJob -Name "DataDemon" }
```

Detta kommando använder cmdleten Invoke-Command för att hämta de schemalagda jobb alternativen för DataDemon-jobbet på datorn SRV01.
Kommandot sparar alternativen i variabeln $O.

## PARAMETRAR

### -ID
Anger identifikations numret för ett schemalagt jobb.
**Get-ScheduledJobOption** hämtar jobb alternativen för det angivna schemalagda jobbet.

Använd Get-ScheduledJob-cmdleten om du vill hämta ID-numren för schemalagda jobb på den lokala datorn eller en fjärrdator.

```yaml
Type: System.Int32
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger ett schemalagt jobb.
Ange en variabel som innehåller ett **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar ett **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka ett **ScheduledJob** -objekt till **Get-ScheduledJobOption**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: JobDefinition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Anger namnen på de schemalagda jobben.
**Get-ScheduledJobOption** hämtar jobb alternativen för det angivna schemalagda jobbet.
Jokertecken stöds.

Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka vidare ett schemalagt jobb från Get-ScheduledJob till **Get-ScheduledJobOption**.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions

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
