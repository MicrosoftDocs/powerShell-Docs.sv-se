---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264608"
---
# Unregister-ScheduledJob

## SAMMANFATTNING
Tar bort schemalagda jobb på den lokala datorn.

## SYNTAX

### Definition (standard)

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
**Unregister-ScheduledJob-cmdlet:** en tar bort schemalagda jobb från den lokala datorn.

När ett schemalagt jobb tas bort eller avregistreras, tar **unregister-ScheduledJob** bort katalogen för det schemalagda jobbet (i katalogen $Home \appdata\local\microsoft\windows\powershell\scheduledjobs), som innehåller XML-filen som definierar det schemalagda jobbet, jobb körnings historiken och alla jobb resultat.
Med den här åtgärden tas även jobbet bort från Schemaläggaren.

**Unregister-ScheduledJob** tar bara bort de schemalagda jobb som skapats med hjälp av Register-ScheduledJob-cmdleten.
Schemalagda jobb tas inte bort som skapas i Schemaläggaren.

Du kan använda parametrarna **unregister-ScheduledJob** för att ta bort schemalagda jobb efter ID eller namn, eller skicka en pipe schemalagda jobb från Get-ScheduledJob till **unregister-ScheduledJob**.

**Unregister-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: ta bort ett schemalagt jobb

```
PS C:\> Unregister-ScheduledJob TestJob
```

Det här kommandot tar bort det schemalagda TestJob-jobbet på den lokala datorn.

### Exempel 2: ta bort alla schemalagda jobb

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

I det här exemplet visas två olika kommandon som tar bort alla schemalagda jobb på den lokala datorn.

Det första kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på den lokala datorn.
En pipeline-operator (|) skickar de schemalagda jobben till **unregister-ScheduleJob** , som tar bort dem.

Det andra kommandot använder parametern *Name* i **unregister-ScheduledJob** med värdet alla (*) för att ta bort alla schemalagda jobb.

Båda kommandona använder *Force* -parametern, som tar bort ett schemalagt jobb även om en instans av jobbet körs.

### Exempel 3: ta bort ett schemalagt jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

Det här kommandot tar bort schemalagda jobb med namn som börjar med test på den fjärranslutna Server01-datorn.
Kommandot använder Invoke-Command-cmdlet för att köra kommandot **unregister-ScheduledJob** på Server02-datorn.

## PARAMETRAR

### -Force
Tar bort det schemalagda jobbet även om en instans av jobbet körs.
**Avregistrering-ScheduledJob** avbryter som standard inte jobb som körs.

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

### -ID
Tar bort de schemalagda jobben med angivet ID-nummer (ID).
Ange ID: na för schemalagda jobb på datorn.

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger ett schemalagt jobb.
Ange en variabel som innehåller **ScheduledJob** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJob** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka pipe- **ScheduledJob** objekt för att **avregistrera-JobTrigger**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Tar bort de schemalagda jobben med de angivna namnen.
Ange namnen på en eller flera schemalagda jobb på datorn.
Jokertecken stöds.

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

### Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Du kan skicka vidare schemalagda jobb till Unregister-ScheduledJob

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

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
