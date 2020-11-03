---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restore-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-Computer
ms.openlocfilehash: 824e9a24693c7a7de01358a048a0df55be333263
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265424"
---
# Restore-Computer

## SAMMANFATTNING
Startar en system återställning på den lokala datorn.

## SYNTAX

```
Restore-Computer [-RestorePoint] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **restore-Computer** återställer den lokala datorn till den angivna system återställnings punkten.

**Restore-Computer** startar om datorn.
Återställningen slutförs under omstarten.

System återställnings punkter och **återställning – datorn** stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.

## EXEMPEL

### Exempel 1: Återställ den lokala datorn

```
PS C:\> Restore-Computer -RestorePoint 253
```

Det här kommandot återställer den lokala datorn till återställnings punkten med sekvensnummer 253.

### Exempel 2: Återställ den lokala datorn med bekräftelse

```
PS C:\> Restore-Computer -RestorePoint 255 -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Restore-Computer" .
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Det här kommandot återställer den lokala datorn till återställnings punkten med sekvensnummer 255.
Parametern *Confirm* används för att fråga användaren innan åtgärden utförs.

### Exempel 3: återställa en dator och kontrol lera statusen

```
PS C:\> Get-ComputerRestorePoint
PS C:\> Restore-Computer -RestorePoint 255
PS C:\> Get-ComputerRestorePoint -LastStatus
```

Kommandona kör en system återställning och kontrollerar sedan dess status.

Det första kommandot använder **Get-ComputerRestorePoint** för att hämta återställnings punkterna på den lokala datorn.

Det andra kommandot återställer datorn till återställnings punkten med sekvensnumret 255.

Det tredje kommandot använder parametern *LastStatus* för *Get-ComputerRestorePoint* -cmdlet: en för att kontrol lera status för återställnings åtgärden.
Eftersom **restore-Computer** tvingar fram en omstart skulle det här kommandot anges efter att datorn startats om.

## PARAMETRAR

### -RestorePoint
Anger återställnings punktens ordnings nummer.
Använd Get-ComputerRestorePoint-cmdleten för att hitta sekvensnumret.
Den här parametern är obligatorisk.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: SequenceNumber, SN, RP

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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Om du vill köra ett Restore-Computer kommando i Windows Vista och senare versioner av Windows-operativsystemet öppnar du Windows PowerShell med alternativet Kör som administratör.
* Denna cmdlet använder klassen Windows Management Instrumentation (WMI) **SystemRestore** .

## RELATERADE LÄNKAR

[Checkpoint-Computer](Checkpoint-Computer.md)

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Aktivera – ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Starta om datorn](Restart-Computer.md)
