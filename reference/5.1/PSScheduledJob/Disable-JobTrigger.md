---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-JobTrigger
ms.openlocfilehash: 236e6b7e6e450bd1f3f868f889a19cf796890127
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264698"
---
# Disable-JobTrigger

## SAMMANFATTNING
Inaktiverar jobb utlösare för schemalagda jobb.

## SYNTAX

```
Disable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Disable-JobTrigger** inaktiverar tillfälligt jobb utlösare för schemalagda jobb.
Om du inaktiverar bevaras alla egenskaper för jobb utlösare, men jobb utlösaren förhindras från att starta det schemalagda jobbet.

Använd cmdleten Get-JobTrigger för att hämta jobb utlösare för att använda denna cmdlet.
Sedan kan du skicka in jobb utlösarna för att **inaktivera-JobTrigger** eller använda dess *InputObject* -parameter.

Om du vill inaktivera en jobb utlösare anger cmdleten **disable-JobTrigger** egenskapen Enabled för jobb utlösaren till $false.
Om du vill aktivera jobb utlösaren igen använder du cmdleten Enable-JobTrigger, som anger egenskapen **Enabled** för jobb utlösaren till $true.
Om du inaktiverar en jobb utlösare inaktive ras inte det schemalagda jobbet, som görs av Disable-ScheduledJob cmdleten, men om du inaktiverar alla jobb utlösare är resultatet detsamma som att inaktivera det schemalagda jobbet.

Om du inaktiverar ett schemalagt jobb eller inaktiverar alla jobb utlösare för ett schemalagt jobb kan du fortfarande starta jobbet med hjälp av Start-Job-cmdlet eller använda det inaktiverade schemalagda jobbet som en mall.

**Disable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: inaktivera en jobb utlösare

```
PS C:\> Get-JobTrigger -Name "Backup-Archives" -TriggerID 1 | Disable-JobTrigger
```

Detta kommando inaktiverar den första utlösaren (ID = 1) för det schemalagda Backup-Archives jobbet på den lokala datorn.

Kommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösaren.
En pipeline-operator skickar jobb utlösaren till cmdleten **disable-JobTrigger** , vilket inaktiverar den.

### Exempel 2: inaktivera alla jobb utlösare

```
The first command uses the Get-ScheduledJob cmdlet to get the Backup-Archives and Inventory scheduled jobs. A pipeline operator (|) sends the scheduled jobs to the Get-JobTrigger cmdlet, which gets all job triggers of the scheduled jobs. Another pipeline operator sends the job triggers to the **Disable-JobTrigger** cmdlet, which disables them.The first command uses the **Get-ScheduledJob** cmdlet to get the jobs, because its *Name* parameter takes multiple names.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Disable-JobTrigger

The second command displays the results. The command repeats the **Get-ScheduledJob** and **Get-JobTrigger** command. A pipeline operator sends the job triggers to the Format-Table cmdlet, which displays the job triggers in a table. The **Format-Table** command adds a JobName property that displays the value of the Name property of the scheduled job in the JobDefinition property of the job trigger object.
PS C:\> Get-ScheduledJob -Name "Backup-Archives,Inventory" | Get-JobTrigger | Format-Table -Property ID, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}} -AutoSize
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
1  Weekly    9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
2  Daily     9/29/2011 1:00:00 AM              False   Backup-Archive
1  Weekly    10/20/2011 11:00:00 PM {Friday}   False   Inventory
1  Weekly    11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Dessa kommandon inaktiverar alla jobb utlösare på två schemalagda jobb och visar resultatet.

### Exempel 3: inaktivera jobb utlösare för schemalagda jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "Daily"} | Disable-JobTrigger}
```

Med det här kommandot inaktive ras de dagliga jobb utlösarna på det schemalagda DeployPackage-jobbet på Server01-fjärrdatorn.

Kommandot använder cmdleten Invoke-Command för att köra kommandona på den Server01 datorn.
Fjärrkommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösare för det schemalagda jobbet DeployPackage.
En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som endast returnerar dagliga jobb utlösare.
En pipeline-operator skickar dagliga jobb utlösare till cmdleten **disable-JobTrigger** , vilket inaktiverar dem.

## PARAMETRAR

### – InputObject
Anger den jobb utlösare som ska inaktive ras.
Ange en variabel som innehåller  **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.
Du kan också skicka ett **ScheduledJobTrigger** -objekt till **disable-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger
Du kan skicka pipe-utlösare för att **inaktivera-JobTrigger**.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* **Disable-JobTrigger** genererar inte fel eller varningar om du inaktiverar en jobb utlösare som redan är inaktive rad.

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
