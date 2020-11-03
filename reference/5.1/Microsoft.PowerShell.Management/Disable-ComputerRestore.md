---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/disable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ComputerRestore
ms.openlocfilehash: 941829c3caa0f6bb2f5712dda9eb7d8c36908062
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266181"
---
# Disable-ComputerRestore

## SAMMANFATTNING
Inaktiverar funktionen system återställning på den angivna fil system enheten.

## SYNTAX

```
Disable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Disable-ComputerRestore** inaktiverar funktionen system återställning på en eller flera fil system enheter.
Det innebär att försök att återställa datorn inte påverkar den angivna enheten.

Om du vill inaktivera system återställning på en enhet måste den vara inaktive rad på system enheten, antingen först eller samtidigt.

Använd Enable-ComputerRestore-cmdleten om du vill återaktivera system återställning.
Använd Rstrui.exe för att hitta status för system återställning för varje enhet.

System återställnings punkter och ComputerRestore-cmdlets stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.

## EXEMPEL

### Exempel 1: inaktivera system återställning på den angivna enheten

```
PS C:\> Disable-ComputerRestore -Drive "C:\"
```

Detta kommando inaktiverar system återställning på enheten C:.

### Exempel 2: inaktivera system återställning på flera enheter

```
PS C:\> Disable-ComputerRestore "C:\", "D:\"
```

Detta kommando inaktiverar system återställning på enheterna C: och D:.
Kommandot använder *enhets* parametern, men utelämnar enhets parameterns namn.

## PARAMETRAR

### – Enhet
Anger fil systemets enheter.
Ange en eller flera enhets beteckningar för fil systemet, varje följt av ett kolon och ett omvänt snedstreck som omges av citat tecken, t. ex. C:\ eller D:\.
Den här parametern är obligatorisk.

Du kan inte använda denna cmdlet för att inaktivera system återställning på en fjärran sluten nätverks enhet, även om enheten är mappad till den lokala datorn och du inte kan inaktivera system återställning på enheter som inte är berättigade till system återställning, till exempel externa enheter.

Om du vill inaktivera system återställning på någon enhet måste system återställning vara inaktiverat på system enheten, antingen före eller samtidigt.

```yaml
Type: System.String[]
Parameter Sets: (All)
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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Om du vill köra denna cmdlet på Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet Kör som administratör.

  Om du vill hitta de fil system enheter som är kvalificerade för system återställning går du till fliken System skydd i system på kontroll panelen. Om du vill öppna den här fliken i Windows PowerShell skriver du `SystemPropertiesProtection` .

  Denna cmdlet använder klassen Windows Management Instrumentation (WMI) **SystemRestore** .

*

## RELATERADE LÄNKAR

[Checkpoint-Computer](Checkpoint-Computer.md)

[Aktivera – ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Starta om datorn](Restart-Computer.md)

[Återställa-dator](Restore-Computer.md)
