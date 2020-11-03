---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/get-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-JobTrigger
ms.openlocfilehash: 7a75a5a7e6875ed88fd31ea0f385c19f1991f8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264657"
---
# Get-JobTrigger

## SAMMANFATTNING
Hämtar jobb utlösare för schemalagda jobb.

## SYNTAX

### Jobb definitionen (standard)

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-InputObject] <ScheduledJobDefinition> [<CommonParameters>]
```

### JobDefinitionId

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Id] <Int32> [<CommonParameters>]
```

### JobDefinitionName

```
Get-JobTrigger [[-TriggerId] <Int32[]>] [-Name] <String> [<CommonParameters>]
```

## BESKRIVNING
**Get-JobTrigger** -cmdlet: en hämtar jobb utlösare för schemalagda jobb.
Du kan använda det här kommandot för att undersöka jobb utlösare eller för att skicka jobb utlösare till andra cmdletar.

En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.
Jobb utlösare sparas inte på disken oberoende av varandra. de ingår i ett schemalagt jobb.
Om du vill hämta en jobb utlösare anger du det schemalagda jobbet som utlösaren startar.

Använd parametrarna för **Get-JobTrigger** -cmdlet: en för att identifiera de schemalagda jobben.
Du kan identifiera de schemalagda jobben med hjälp av namn eller identifierings nummer, eller genom att ange eller dirigera **ScheduledJob** objekt, till exempel de som returneras av Get-ScheduledJob cmdlet, för att **Hämta-JobTrigger**.

**Get-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Hämta en jobb utlösare efter schemalagt jobbnamn

```
PS C:\> Get-JobTrigger -Name "BackupJob"
```

Kommandot använder *Name* -parametern för **Get-JobTrigger** för att hämta jobb utlösare för det schemalagda BackupJob-jobbet.

### Exempel 2: Hämta en jobb utlösare efter ID

```
The first command uses the Get-ScheduledJob cmdlet to display the scheduled jobs on the local computer. The display includes the IDs of the scheduled jobs.
PS C:\> Get-ScheduledJob
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProjects {1}             \\Server\Share\Archive-Projects.ps1      True
2          Backup          {1,2}           \\Server\Share\Run-Backup.ps1            True
3          Test-HelpFiles  {1}             \\Server\Share\Test-HelpFiles.ps1        True
4          TestJob         {}              \\Server\Share\Run-AllTests.ps1          True

The second command uses the **Get-JobTrigger** cmdlet to get the job trigger for the Test-HelpFiles job (ID = 3)
PS C:\> Get-JobTrigger -ID 3
```

Exemplet använder *ID-* parametern för **Get-JobTrigger** för att hämta jobb utlösare för ett schemalagt jobb.

### Exempel 3: Hämta jobb utlösare genom att skicka ett jobb

```
PS C:\> Get-ScheduledJob -Name *Backup*, *Archive* | Get-JobTrigger
```

Det här kommandot hämtar jobb utlösare för alla jobb som har säkerhets kopierings-eller Arkiv namn.

### Exempel 4: Hämta jobb utlösaren för ett jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Server01 { Get-ScheduledJob Backup | Get-JobTrigger -TriggerID 2 }
```

Det här kommandot hämtar en av de två jobb utlösarna för ett schemalagt jobb på en fjärrdator.

Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.
Den använder Get-ScheduledJob-cmdlet för att hämta det schemalagda säkerhets kopierings jobbet, som den rör till cmdleten **Get-JobTrigger** .
Parametern *TriggerID* används för att bara hämta den andra utlösaren.

### Exempel 5: Hämta alla jobb utlösare

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="ScheduledJob";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                    DaysOfWeek Enabled ScheduledJob
-- --------- --                    ---------- ------- ------------
1    Weekly  9/28/2011 3:00:00 AM  {Monday}   True    Backup
1    Daily   9/27/2011 11:00:00 PM            True    Test-HelpFiles
```

Det här kommandot hämtar alla jobb utlösare för alla schemalagda jobb på den lokala datorn.

Kommandot använder Get-ScheduledJob för att hämta de schemalagda jobben på den lokala datorn och rör dem för att **Hämta-JobTrigger** , som hämtar jobb utlösaren för varje schemalagt jobb (om det finns några).

Om du vill lägga till namnet på det schemalagda jobbet i jobb utlösaren, använder kommandot funktionen för beräknade egenskaper i Format-Table-cmdleten.
Utöver de egenskaper för jobb utlösare som visas som standard skapar kommandot en ny ScheduledJob-egenskap som visar namnet på det schemalagda jobbet.

### Exempel 6: Hämta jobb utlösarens egenskap för ett schemalagt jobb

```
The command uses the Get-ScheduledJob cmdlet to get the Test-HelpFiles scheduled job. Then it uses the dot method (.) to get the JobTriggers property of the Test-HelpFiles scheduled job.
PS C:\> (Get-ScheduledJob Test-HelpFiles).JobTriggers

The second command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer. It uses the ForEach-Object cmdlet to get the value of the JobTrigger property of each scheduled job.
PS C:\> Get-ScheduledJob | foreach {$_.JobTriggers}
```

Jobb utlösare för ett schemalagt jobb lagras i jobbets egenskap JobTriggers.
I det här exemplet visas alternativ för att använda cmdleten **Get-JobTrigger** för att hämta jobb utlösare.
Resultaten är identiska med att använda cmdleten **Get-JobTrigger** och teknikerna kan användas utbytbart.

### Exempel 7: jämför jobb utlösare

```
The first command gets the job trigger of the ArchiveProjects scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T1 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name ArchiveProjects | Get-JobTrigger | Tee-Object -Variable T1
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The second command gets the job trigger of the Test-HelpFiles scheduled job. The command pipes the job trigger to the Tee-Object cmdlet, which saves the job trigger in the $T2 variable and displays it at the command line.
PS C:\> Get-ScheduledJob -Name "Test-HelpFiles" | Get-JobTrigger | Tee-Object -Variable T2
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/26/2011 3:00:00 AM                           True

The third command compares the job triggers in the $t1 and $t2 variables. It uses the Get-Member cmdlet to get the properties of the job trigger in the $t1 variable. It pipes the properties to the ForEach-Object cmdlet, which compares each property to the properties of the job trigger in the $t2 variable by name. The command then pipes the differing properties to the Format-List cmdlet, which displays them in a list.The output indicates that, although the job triggers appear to be the same, the HelpFiles job trigger includes a random delay of three (3) minutes.
PS C:\> $T1 | Get-Member -Type Property | ForEach-Object { Compare-Object $T1 $T2 -Property $_.Name}
RandomDelay                                                 SideIndicator
-----------                                                 -------------
00:00:00                                                    =>
00:03:00                                                    <=
```

Det här exemplet visar hur du jämför jobb utlösare för två schemalagda jobb.

## PARAMETRAR

### -ID
Anger identifikations numret för ett schemalagt jobb.
**Get-JobTrigger** hämtar jobb utlösaren för det angivna schemalagda jobbet.

Använd Get-ScheduledJob-cmdlet för att hämta identifikations antalet schemalagda jobb på den lokala datorn eller en fjärrdator.

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
Ange en variabel som innehåller  **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka pipe- **ScheduledJob** objekt till **Get-JobTrigger**.

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
Anger namnet på ett schemalagt jobb.
**Get-JobTrigger** hämtar jobb utlösaren för det angivna schemalagda jobbet.
Jokertecken stöds.

Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.

```yaml
Type: System.String
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
Hämtar de angivna jobb utlösarna.
Ange utlösar-ID: n för en eller flera jobb utlösare för ett schemalagt jobb.
Använd den här parametern när det schemalagda jobbet som anges av parametrarna *Name* , *ID* eller *InputObject* har flera jobb utlösare.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka vidare ett schemalagt jobb från Get-ScheduledJob till **Get-JobTrigger**.

## UTDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger

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
