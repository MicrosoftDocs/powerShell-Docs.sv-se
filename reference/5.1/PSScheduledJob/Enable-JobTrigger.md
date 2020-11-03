---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-JobTrigger
ms.openlocfilehash: d08b55f4ba78af69608ac74c097fc6851164093b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264662"
---
# Enable-JobTrigger

## SAMMANFATTNING
Aktiverar jobb utlösare för schemalagda jobb.

## SYNTAX

```
Enable-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Enable-JobTrigger** aktiverar jobb utlösare för schemalagda jobb, t. ex. de som har inaktiverats med hjälp av Disable-JobTrigger-cmdleten.
Aktiverade och återaktiverade jobb utlösare kan starta schemalagda jobb omedelbart; du behöver inte starta om Windows eller Windows PowerShell.

Använd cmdleten Get-JobTrigger för att hämta jobb utlösare för att använda denna cmdlet.
Sedan kan du skicka in jobbet triggers för att **Aktivera-JobTrigger** eller använda dess *InputObject* -parameter.

Om du vill aktivera en jobb utlösare anger cmdleten **Enable-JobTrigger** egenskapen Enabled för jobb utlösaren till $true.

**Enable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Aktivera en jobb utlösare

```
PS C:\> Get-JobTrigger -Name Backup-Archives -TriggerID 1 | Enable-JobTrigger
```

Detta kommando aktiverar den första utlösaren (ID = 1) för det schemalagda Backup-Archives jobbet på den lokala datorn.

Kommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösaren.
En pipeline-operator skickar jobb utlösaren till cmdleten **Enable-JobTrigger** , vilket gör det möjligt.

### Exempel 2: Aktivera alla jobb utlösare

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | Enable-JobTrigger
```

Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.
En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare för de schemalagda jobben.
En annan pipeline-operator skickar jobb utlösare till cmdleten **Enable-JobTrigger** , vilket gör att de kan användas.

### Exempel 3: Aktivera jobb utlösaren för ett schemalagt jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Server01 {Get-JobTrigger -Name DeployPackage | Where-Object {$_.Frequency -eq "AtLogon"} | Enable-JobTrigger}
```

Med det här kommandot aktive ras AtLogon-jobbet på det schemalagda DeployPackage-jobbet på Server01-fjärrdatorn.

Kommandot använder cmdleten Invoke-Command för att köra kommandona på den Server01 datorn.
Fjärrkommandot använder cmdleten Get-JobTrigger för att hämta jobb utlösare för det schemalagda jobbet DeployPackage.
En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet som bara returnerar AtLogon-jobb-utlösare.
En pipeline-operator skickar AtLogon-jobbet utlösare till cmdleten **Enable-JobTrigger** , vilket gör att de kan användas.

### Exempel 4: Visa inaktiverade jobb utlösare

```
PS C:\> Get-ScheduledJob | Get-JobTrigger | where {!$_.Enabled} | Format-Table Id, Frequency, At, DaysOfWeek, Enabled, @{Label="JobName";Expression={$_.JobDefinition.Name}}
Id Frequency At                     DaysOfWeek Enabled JobName
-- --------- --                     ---------- ------- -------
 1    Weekly 9/28/2011 3:00:00 AM   {Monday}   False   Backup-Archive
 2    Daily  9/29/2011 1:00:00 AM              False   Backup-Archive
 1    Weekly 10/20/2011 11:00:00 PM {Friday}   False   Inventory
 1    Weekly 11/2/2011 2:00:00 PM   {Monday}   False   Inventory
```

Det här kommandot visar alla inaktiverade jobb utlösare för alla schemalagda jobb i en tabell.
Du kan använda ett kommando som det här för att identifiera jobb utlösare som kan behöva aktive ras.

Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.
En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare för de schemalagda jobben.
En annan pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som endast returnerar jobb utlösare som är inaktiverade, det vill säga där värdet för den aktiverade egenskapen för jobb utlösaren inte (!) är sant.

En annan pipeline-operator skickar inaktiverade jobb utlösare till Format-Table-cmdlet, som visar de valda egenskaperna för jobb utlösare i en tabell.
Egenskaperna innehåller en ny JobName-egenskap som visar namnet på det schemalagda jobbet i jobb definitionen-egenskapen för jobb utlösaren.

## PARAMETRAR

### – InputObject
Anger den jobb utlösare som ska aktive ras.
Ange en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.
Du kan också skicka ett **ScheduledJobTrigger** -objekt för att **Aktivera-JobTrigger**.

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
Du kan skicka pipe-utlösare för att **Aktivera-JobTrigger**.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* **Enable-JobTrigger** genererar inte fel eller varningar om du aktiverar en jobb utlösare som redan är aktive rad.

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
