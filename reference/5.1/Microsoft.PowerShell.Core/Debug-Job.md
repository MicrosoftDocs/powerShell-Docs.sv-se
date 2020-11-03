---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: d36d15194ce1d4a48a59ad8bb8621b3c9c1a74ac
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263673"
---
# Debug-Job

## SAMMANFATTNING
Fel vid körning av ett arbets flödes jobb i bakgrunden, fjärrdatorn eller Windows PowerShell.

## SYNTAX

### JobParameterSet (standard)

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobNameParameterSet

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobIdParameterSet

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### JobInstanceIdParameterSet

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Med cmdleten **Debug-Job** kan du felsöka skript som körs i jobb.
Cmdleten är utformad för att felsöka Windows PowerShell Workflow-jobb, bakgrunds jobb och jobb som körs i fjärrsessioner.
**Felsök – jobb** accepterar ett jobb objekt, namn, ID eller instans-ID som körs och startar en felsökningssession i skriptet som körs.
Fel söknings programmet **avslutar** kommandot stoppar jobbet och kör skriptet.
Från och med Windows PowerShell 5,0 kopplar kommandot **exit** bort fel söknings programmet och tillåter att jobbet fortsätter att köras.

## EXEMPEL

### Exempel 1: Felsöka ett jobb efter jobb-ID

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

Det här kommandot delar in i ett jobb som körs med ID 3.

## PARAMETRAR

### -ID
Anger ID-numret för ett jobb som körs.
Kör cmdleten Get-Job om du vill hämta ID-numret för ett jobb.

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId
Anger instans-ID-GUID för ett jobb som körs.
Om du vill ta *reda på ett jobb med* hjälp av cmdleten **Get-Job** kan du skicka resultatet till en **format-*-** cmdlet, som visas i följande exempel:

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Jobb
Anger ett jobb objekt som körs.
Det enklaste sättet att använda den här parametern är att spara resultatet av ett **Get-Job-** kommando som returnerar det jobb som du vill felsöka i en variabel och sedan ange variabeln som värde för den här parametern.

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name
Anger ett jobb efter det egna namnet på jobbet.
När du startar ett jobb kan du ange ett jobb namn genom att lägga till parametern *JobName* i cmdlets som Invoke-Command och start jobb.

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
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

### System. Management. Automation. RemotingJob

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta jobb](Get-Job.md)

[Mottagning – jobb](Receive-Job.md)

[Ta bort – jobb](Remove-Job.md)

[Återuppta – jobb](Resume-Job.md)

[Start – jobb](Start-Job.md)

[Stoppa – jobb](Stop-Job.md)

[Pausa – jobb](Suspend-Job.md)

[Wait-Job](Wait-Job.md)
