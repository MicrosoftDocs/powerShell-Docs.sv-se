---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264663"
---
# Enable-ScheduledJob

## SAMMANFATTNING
Aktiverar ett schemalagt jobb.

## SYNTAX

### Definition (standard)

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Enable-ScheduledJob** aktiverar schemalagda jobb som är inaktiverade, till exempel de som har inaktiverats med hjälp av Disable-ScheduledJob-cmdleten.
Aktiverade jobb körs automatiskt när de utlöses.

Om du vill aktivera ett schemalagt jobb anger cmdleten **Enable-ScheduledJob** egenskapen Enabled för det schemalagda jobbet till $true.

**Enabled-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: aktivera ett schemalagt jobb

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

Det här kommandot aktiverar det schemalagda jobbet med ID 2 på den lokala datorn.
Utdata visar kommandoets effekt.

### Exempel 2: Aktivera alla schemalagda jobb

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

Detta kommando aktiverar alla schemalagda jobb på den lokala datorn.
Den använder Get-ScheduledJob-cmdlet för att hämta allt schemalagt jobb och cmdleten **Enable-ScheduledJob** för att aktivera dem.

**Enable-ScheduledJob** genererar inte varningar eller fel om du aktiverar ett schemalagt jobb som redan har Aktiver ATS, så att du kan aktivera alla schemalagda jobb utan villkor.

### Exempel 3: Aktivera valda schemalagda jobb

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

Det här kommandot aktiverar schemalagda jobb som inte kräver någon nätverks anslutning.

Kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på datorn.
En pipeline-operator skickar schemalagda jobb till Get-ScheduledJobOption-cmdlet, som hämtar jobb alternativen för varje schemalagt jobb.
Varje jobb alternativ objekt har en jobb definitionen-egenskap som innehåller det associerade schemalagda jobbet.
Egenskapen jobb definitionen används för att slutföra kommandot.

Kommandot använder en pipeline-operator (|) för att skicka jobb alternativen till Where-Object-cmdleten, som väljer alternativ för schemalagda jobb där egenskapen **RunWithoutNetwork** har värdet True ($true).
En annan pipeline-operator skickar de valda alternativen för schemalagda jobb till ForEach-Object-cmdleten som kör ett **Enable-ScheduledJob-** kommando på det schemalagda jobbet i värdet för egenskapen jobb definitionen för varje jobb alternativ objekt.

### Exempel 4: Aktivera schemalagda jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

Det här kommandot aktiverar schemalagda jobb som har "test" i sina namn på två fjärrdatorer, SRV01 och Srv10.

Kommandot använder Invoke-Command cmdlet för att köra kommandot **Enable-ScheduledJob** på datorerna SRV01 och Srv10.
Kommandot använder *Name* -parametern för **Enable-ScheduledJob** för att aktivera det schemalagda inventerings jobbet på varje dator.

## PARAMETRAR

### -ID
Aktiverar det schemalagda jobbet med angivet ID-nummer (ID).
Ange ID för ett schemalagt jobb.

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger det schemalagda jobbet som ska aktive ras.
Ange en variabel som innehåller **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka ett **ScheduledJobDefinition** -objekt för att **Aktivera-ScheduledJob**.

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name
Aktiverar de schemalagda jobben med de angivna namnen.
Ange namnet på ett schemalagt jobb.
Jokertecken stöds.

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
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
Du kan skicka vidare ett schemalagt jobb till **Enable-ScheduledJob**.

## UTDATA

### Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Om du använder parametern **Passthru** returnerar **Enable-ScheduledJob** det schemalagda jobbet som har Aktiver ATS.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* **Enable-ScheduledJob** genererar inte varningar eller fel om du använder den för att aktivera ett schemalagt jobb som redan har Aktiver ATS.

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
