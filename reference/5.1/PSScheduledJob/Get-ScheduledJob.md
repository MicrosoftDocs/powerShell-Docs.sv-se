---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ScheduledJob
ms.openlocfilehash: 40224432c208ee45efc20f556312fa250e9bb7a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264656"
---
# Get-ScheduledJob

## SAMMANFATTNING
Hämtar schemalagda jobb på den lokala datorn.

## SYNTAX

### DefinitionId (standard)

```
Get-ScheduledJob [[-Id] <Int32[]>] [<CommonParameters>]
```

### DefinitionName

```
Get-ScheduledJob [-Name] <String[]> [<CommonParameters>]
```

## BESKRIVNING
**Get-ScheduledJob** -cmdlet: en hämtar schemalagda jobb på den lokala datorn.
**Get-ScheduledJob** hämtar endast schemalagda jobb som skapats av den aktuella användaren med hjälp av Register-ScheduledJob-cmdleten.

Även om jobb som har skapats med hjälp av **register-ScheduledJob** -cmdleten visas i Schemaläggaren, får **Get-ScheduledJob** endast schemalagda jobb.
Det går inte att skapa schemalagda aktiviteter som har skapats i Schemaläggaren.

Utan parametrar hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.
Du kan använda parametrarna för **Get-ScheduledJob** för att hämta schemalagda jobb efter ID eller namn och granska dem eller skicka vidare till andra cmdletar.

**Get-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Hämta alla schemalagda jobb

```
PS C:\> Get-ScheduledJob
```

Det här kommandot hämtar alla schemalagda jobb på den lokala datorn.

### Exempel 2: Hämta schemalagda jobb efter namn

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive*
```

Det här kommandot hämtar alla schemalagda jobb på datorn som har namn som innehåller säkerhets kopiering eller arkiv.
Med det här kommando formatet kan du söka efter specifika jobb.

### Exempel 3: Hämta schemalagda jobb på fjärrdatorer

```
PS C:\> Invoke-Command -ComputerName (Get-Content Servers.txt) {Get-ScheduledJob}
```

Det här kommandot hämtar alla schemalagda jobb på de datorer som anges i Servers.txt-filen.
Kommandot använder cmdleten Invoke-Command för att köra kommandot **Get-ScheduleJob** på varje dator.

### Exempel 4: skicka schemalagda jobb till andra cmdletar för pipe

```
PS C:\> Get-ScheduledJob DailyBackup, WeeklyBackup | Get-JobTrigger
```

Med det här kommandot hämtas jobb utlösare för de schemalagda jobben DailyBackup och WeeklyBackup.
Den använder cmdleten **Get-ScheduledJob** för att hämta de schemalagda jobben och Get-JobTrigger-cmdleten för att hämta jobb utlösare för schemalagda jobb.

## PARAMETRAR

### -ID
Hämtar bara de schemalagda jobben med det angivna ID-numret (ID).
Ange ett eller flera ID: n för schemalagda jobb på datorn.
Som standard hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name
Hämtar bara de schemalagda jobben med de angivna namnen.
Ange ett eller flera namn för schemalagda jobb på datorn.
Jokertecken stöds.
Som standard hämtar **Get-ScheduledJob** alla schemalagda jobb på datorn.

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
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
Du kan inte skicka pipe-ininformation till **Get-ScheduledJob**.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition

## ANTECKNINGAR

* Varje schemalagt jobb sparas i en under katalog till katalogen $home \AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs på den lokala datorn. Under katalogen är namngiven för det schemalagda jobbet och innehåller XML-filen för det schemalagda jobbet och poster i körnings historiken. Mer information om schemalagda jobb på disk finns about_Scheduled_Jobs_Advanced.
* Schemalagda jobb som du skapar i Windows PowerShell visas i Schemaläggaren i Library\Microsoft\Windows\PowerShell\ScheduledJobs-mappen Schemaläggaren. Du kan använda Schemaläggaren för att visa och redigera det schemalagda jobbet.
* Du kan använda Schemaläggaren, SchTasks.exe kommando rads verktyget och Schemaläggaren-cmdletar för att hantera schemalagda jobb som du skapar med de schemalagda jobb-cmdletarna. Du kan dock inte använda de schemalagda jobb-cmdletarna för att hantera aktiviteter som du skapar i Schemaläggaren.

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
