---
external help file: Microsoft.PowerShell.ScheduledJob.dll-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/add-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-JobTrigger
ms.openlocfilehash: 6066b8f91c99830fefb09a8bea13fac6ddf958e9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264699"
---
# Add-JobTrigger

## SAMMANFATTNING
Lägger till jobb utlösare i schemalagda jobb.

## SYNTAX

### Jobb definitionen (standard)

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-InputObject] <ScheduledJobDefinition[]>
 [<CommonParameters>]
```

### JobDefinitionId

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Id] <Int32[]> [<CommonParameters>]
```

### JobDefinitionName

```
Add-JobTrigger [-Trigger] <ScheduledJobTrigger[]> [-Name] <String[]> [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Add-JobTrigger** lägger till jobb utlösare i schemalagda jobb.
Du kan använda den för att lägga till flera utlösare till flera schemalagda jobb.

En jobb utlösare startar ett schemalagt jobb vid ett engångs-eller återkommande schema eller när en händelse inträffar.

Använd *Utlösar* -parametern för **Add-JobTrigger** för att identifiera de jobb utlösare som ska läggas till.
Använd parametrarna *Name* , *ID* eller *InputObject* för **Add-JobTrigger** för att identifiera det schemalagda jobbet som utlösarna läggs till i.

Om du vill skapa jobb utlösare för värdet för parametern *trigger* använder du New-JobTrigger cmdlet eller använder en hash-tabell för att ange jobb utlösaren.

**Add-JobTrigger** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: Lägg till en jobb utlösare i ett schemalagt jobb

```
PS C:\> $Daily = New-JobTrigger -Daily -At 3AMPS
PS C:\> Add-JobTrigger -Trigger $Daily -Name "TestJob"
```

Dessa kommandon lägger till den dagliga jobb utlösaren i det schemalagda TestJob-jobbet.

Det första kommandot använder cmdleten New-JobTrigger för att skapa en jobb utlösare som startar ett schemalagt jobb varje dag kl. 3:00 a.m.
Kommandot sparar jobb utlösaren i variabeln $Daily.

Det andra kommandot använder cmdleten **Add-JobTrigger** för att lägga till jobb utlösaren i variabeln $Startup till det schemalagda TestJob-jobbet.

### Exempel 2: Lägg till en jobb utlösare till flera schemalagda jobb

```
PS C:\> Get-ScheduledJob | Add-JobTrigger -Trigger (New-JobTrigger -AtStartup)
```

Det här kommandot lägger till en AtStartup jobb utlösare för alla schemalagda jobb på den lokala datorn.
Den använder Get-ScheduledJob för att hämta alla schemalagda jobb på datorn.
Den använder en pipeline-operator (|) för att skicka jobben till cmdleten **Add-JobTrigger** , som lägger till jobb utlösaren i vart och ett av de schemalagda jobben.
Värdet för *Utlösar* -parametern är ett New-JobTrigger-kommando som skapar jobb utlösaren AtStartup.

### Exempel 3: kopiera en jobb utlösare

```
PS C:\> $T = Get-JobTrigger -Name "BackupArchives"
PS C:\> Add-JobTrigger -Name "TestBackup,BackupLogs" -Trigger $T
```

De här kommandona kopierar jobb utlösaren från det schemalagda BackupArchives-jobbet och lägger till det i de schemalagda jobben TestBackup och BackupLogs.

Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda BackupArchives-jobbet.
Kommandot sparar utlösaren i variabeln $t.

Det andra kommandot använder cmdleten **Add-JobTrigger** för att lägga till jobb utlösaren i $t till de schemalagda jobben TestBackup och BackupLogs.

## PARAMETRAR

### -ID
Anger ID-numren för de schemalagda jobben.
**Add-JobTrigger** lägger till jobb utlösaren till de angivna schemalagda jobben.

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
Du kan också skicka pipe- **ScheduledJob** objekt till **Add-JobTrigger**.

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
**Add-JobTrigger** lägger till jobb utlösare till de angivna schemalagda jobben.
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

### – Utlös
Anger vilka jobb utlösare som ska läggas till.
Ange en hash-tabell som anger jobb utlösare eller en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.
Du kan också skicka pipe- **ScheduledJobTrigger** objekt till **Add-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger, Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka pipe-jobb eller schemalagda jobb till **Add-JobTrigger**.

## UTDATA

### Inget
Denna cmdlet returnerar inga utdata.

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
