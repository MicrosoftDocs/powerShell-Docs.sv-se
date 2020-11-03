---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264686"
---
# Disable-ScheduledJob

## SAMMANFATTNING
Inaktiverar ett schemalagt jobb.

## SYNTAX

### Definition (standard)

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### DefinitionId

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DefinitionName

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Disable-ScheduledJob** inaktiverar tillfälligt schemalagda jobb.
Om du inaktiverar bevaras alla jobb egenskaper och jobb utlösarna inaktive ras inte, men de schemalagda jobben startas automatiskt när de utlöses.
Du kan starta ett inaktiverat schemalagt jobb med hjälp av Start-Job-cmdlet eller använda ett inaktiverat schemalagt jobb som mall.

Om du vill inaktivera ett schemalagt jobb anger cmdleten **disable-ScheduledJob** egenskapen **Enabled** för det schemalagda jobbet till falskt ($false).
Använd Enable-ScheduledJob-cmdleten för att återaktivera det schemalagda jobbet.

**Disable-ScheduledJob** är en samling jobb schemaläggnings-cmdletar i **PSScheduledJob** -modulen som ingår i Windows PowerShell.

Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.
Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: inaktivera ett schemalagt jobb

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

Detta kommando inaktiverar det schemalagda jobbet med ID 2 på den lokala datorn.
Utdata visar kommandoets effekt.

### Exempel 2: inaktivera alla schemalagda jobb

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

Detta kommando inaktiverar alla schemalagda jobb på den lokala datorn.
Den använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb och cmdleten **disable-ScheduledJob** för att inaktivera dem.

Du kan återaktivera schemalagt jobb genom att använda Enable-ScheduledJob-cmdlet och köra ett inaktiverat schemalagt jobb med hjälp av Start-Job-cmdleten.

**Disable-ScheduledJob** genererar inte varningar eller fel om du inaktiverar ett schemalagt jobb som redan har inaktiverats, så att du kan inaktivera alla schemalagda jobb utan villkor.

### Exempel 3: inaktivera valda schemalagda jobb

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

Det här kommandot inaktiverar schemalagt jobb innehåller inte någon autentiseringsuppgift.
Jobb utan autentiseringsuppgifter körs med behörigheten för den användare som skapade dem.

Kommandot använder Get-ScheduledJob-cmdlet för att hämta alla schemalagda jobb på datorn.
En pipeline-operator skickar schemalagda jobb till Where-Object-cmdlet, som väljer schemalagda jobb som saknar autentiseringsuppgifter.
Kommandot använder operatorn not (!) och refererar till egenskapen Credential för det schemalagda jobbet.
En annan pipeline-operator skickar de valda schemalagda jobben till cmdleten **disable-ScheduledJob** , vilket inaktiverar dem.

### Exempel 4: Inaktivera schemalagda jobb på en fjärrdator

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

Detta kommando inaktiverar det schemalagda TestJob-jobbet på två fjärranslutna datorer, SRV01 och Srv10.

Kommandot använder Invoke-Command cmdlet för att köra kommandot **disable-ScheduledJob** på datorerna SRV01 och Srv10.
Kommandot använder *Name* -parametern för **disable-ScheduledJob** för att välja det schemalagda TestJob-jobbet på varje dator.

### Exempel 5: inaktivera ett schemalagt jobb med dess globala ID

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

I det här exemplet visas hur du inaktiverar ett schemalagt jobb genom att använda dess globala identifierare.
Värdet för egenskapen GlobalID för ett schemalagt jobb är en unik identifierare (GUID).
Använd värdet GlobalID när precision krävs, till exempel när du inaktiverar schemalagda jobb på flera datorer.

## PARAMETRAR

### -ID
Inaktiverar det schemalagda jobbet med angivet ID-nummer (ID).
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
Anger det schemalagda jobbet som ska inaktive ras.
Ange en variabel som innehåller  **ScheduledJobDefinition** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobDefinition** -objekt, till exempel ett Get-ScheduledJob-kommando.
Du kan också skicka ett **ScheduledJobDefinition** -objekt till **disable-ScheduledJob**.

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
Inaktiverar de schemalagda jobben med de angivna namnen.
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
Du kan skicka vidare ett schemalagt jobb för att **inaktivera-ScheduledJob**.

## UTDATA

### Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobDefinition
Om du använder parametern **Passthru** , **disable-ScheduledJob** returnerar det schemalagda jobbet som inaktiverades.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* **Disable-ScheduledJob** genererar inte varningar eller fel om du använder den för att inaktivera ett schemalagt jobb som redan har inaktiverats.

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
