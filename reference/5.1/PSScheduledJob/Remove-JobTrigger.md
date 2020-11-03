---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/remove-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-JobTrigger
ms.openlocfilehash: adcd74361b1a045a57c7db2f15996f4ea53d6d5b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264638"
---
# Remove-JobTrigger

## SAMMANFATTNING
Ta bort jobb utlösare från schemalagda jobb.

## SYNTAX

### Jobb definitionen (standard)

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-InputObject] <ScheduledJobDefinition[]> [<CommonParameters>]
```

### JobDefinitionId

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Remove-JobTrigger [-TriggerId <Int32[]>] [-Name] <String[]> [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Remove-JobTrigger** tar bort jobb utlösare från schemalagda jobb.

En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.
Om du vill hantera jobb utlösare använder du cmdletarna New-JobTrigger, Add-JobTrigger, set-JobTrigger och Set-ScheduledJob.

Använd *namnen* , *ID* eller *InputObject* -parametrarna för **Remove-JobTrigger** för att identifiera de schemalagda jobb som utlösarna tas bort från.
Använd parametern *TriggerID* för att identifiera de jobb utlösare som ska tas bort.
Som standard tar **Remove-JobTrigger** bort alla jobb utlösare för ett schemalagt jobb.

**Remove-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: ta bort alla jobb utlösare

```
PS C:\> Remove-JobTrigger -Name "Test*"
```

Det här kommandot tar bort alla jobb utlösare från schemalagt jobb som har namn som börjar med test.

### Exempel 2: ta bort valda jobb utlösare

```
PS C:\> Remove-JobTrigger -Name "BackupArchive" -TriggerID 3
```

Det här kommandot tar bara bort den tredje utlösaren (ID = 3) från det schemalagda BackupArchive-jobbet.

### Exempel 3: ta bort AtStartup jobb-utlösare från alla schemalagda jobb

```
PS C:\> function Delete-AtStartup
{
    Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.Frequency -eq "AtStartup"} | ForEach-Object { Remove-JobTrigger -InputObject $_.JobDefinition -TriggerID $_.ID}
}
```

Den här funktionen tar bort alla AtStartup jobb-utlösare från alla jobb på den lokala datorn.
Om du vill använda funktionen kör du funktionen i sessionen och skriver sedan `Delete-AtStartup` .

Funktionen Delete-AtStartup innehåller ett enda kommando.
Kommandot använder Get-ScheduledJob-cmdlet för att hämta de schemalagda jobben på den lokala datorn.
En pipeline-operator (|) skickar de schemalagda jobben till Get-JobTrigger-cmdlet, som hämtar alla jobb utlösare från var och en av de schemalagda jobben.
En pipeline-operator skickar jobb utlösare till Where-Object-cmdlet, som väljer jobb utlösare där värdet för egenskapen frekvens för jobb utlösaren är lika med AtStartup.

**JobTrigger** -objekt har en **jobb definitionen** -egenskap som innehåller det schemalagda jobbet som de utlöser.
Resten av kommandot använder den värdefulla funktionen.

En pipeline-operator skickar AtStartup-jobbet till ForEach-Object-cmdleten, som kör ett **Remove-JobTrigger-** kommando på varje AtStartup-utlösare.
Värdet för parametern *InputObject* i **Remove-JobTrigger** är det schemalagda jobbet i egenskapen jobb definitionen för jobb utlösaren.
Värdet för parametern *TriggerID* är identifieraren i jobb utlösaren ID-egenskap.

### Exempel 4: ta bort en jobb utlösare från ett fjärrschemalagt jobb

```
PS C:\> Invoke-Command -ComputerName "Server01" { Remove-JobTrigger -ID 38 -TriggerID 1 }
```

Det här kommandot tar bort den första jobb utlösaren från inventerings jobbet på Server01-datorn.

Kommandot använder cmdleten **Invoke-Command** för att köra cmdleten **Remove-JobTrigger** på Server01-datorn.
Cmdlet: en **Remove-JobTrigger** använder *ID-* parametern för att identifiera det schemalagda jobbet för inventering och parametern *TriggerID* för att ange den första utlösaren.
*ID-* parametern är särskilt användbar när flera schemalagda jobb har samma eller liknande namn.

## PARAMETRAR

### -ID
Anger ID-numren för de schemalagda jobben.
**Remove-JobTrigger** tar bort jobb utlösare från de angivna schemalagda jobben.

Använd Get-ScheduledJob-cmdlet för att hämta identifikations antalet schemalagda jobb på den lokala datorn eller en fjärrdator.

```yaml
Type: System.Int32[]
Parameter Sets: JobDefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger de schemalagda jobben.
Ange en variabel som innehåller **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka pipe- **ScheduledJob** objekt till **Remove-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
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
**Remove-JobTrigger** tar bort jobb utlösarna från de angivna schemalagda jobben.
Jokertecken stöds.

Använd Get-ScheduledJob-cmdleten för att hämta namnen på schemalagda jobb på den lokala datorn eller en fjärrdator.

```yaml
Type: System.String[]
Parameter Sets: JobDefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TriggerId
Tar bara bort de angivna jobb utlösarna.
Som standard tar **Remove-JobTrigger** bort alla utlösare från de schemalagda jobben.
Använd den här parametern när de schemalagda jobben har flera jobb utlösare.

Ange utlösar-ID: n för en eller flera jobb utlösare för ett schemalagt jobb.
Om du anger flera schemalagda jobb tar **Remove-JobTrigger** bort jobb utlösaren med angivet ID från alla schemalagda jobb.

```yaml
Type: System.Int32[]
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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka vidare schemalagda jobb till **Remove-JobTrigger-** cmdlet: en.

## UTDATA

### Inget
Cmdleten genererar inga utdata.

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
