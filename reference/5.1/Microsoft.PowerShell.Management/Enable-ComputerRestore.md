---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/enable-computerrestore?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ComputerRestore
ms.openlocfilehash: f9616a7f9af4dd2fa45e150bb64eef65427b4947
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266180"
---
# Enable-ComputerRestore

## SAMMANFATTNING
Aktiverar funktionen system återställning på den angivna fil system enheten.

## SYNTAX

```
Enable-ComputerRestore [-Drive] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Enable-ComputerRestore** aktiverar system återställnings funktionen på en eller flera fil system enheter.
Därför kan du använda verktyg som Restore-Computer-cmdlet för att återställa datorn till ett tidigare tillstånd.

Som standard aktive ras system återställning på alla kvalificerade enheter, men du kan inaktivera det, till exempel genom att använda Disable-ComputerRestore-cmdlet.
Om du vill aktivera (eller återaktivera) system återställning på valfri enhet måste den vara aktive rad på system enheten, antingen första eller samtidigt.
Använd Rstrui.exe för att hitta status för system återställning för varje enhet.

System återställnings punkter och ComputerRestore-cmdlets stöds endast på klient operativ system, till exempel Windows 7, Windows Vista och Windows XP.

## EXEMPEL

### Exempel 1: Aktivera system återställning på den angivna enheten

```
PS C:\> Enable-ComputerRestore -Drive "C:\"
```

Det här kommandot aktiverar system återställning på enhet C: på den lokala datorn.

### Exempel 2: Aktivera system återställning på flera enheter

```
PS C:\> Enable-ComputerRestore -Drive "C:\", "D:\"
```

Det här kommandot aktiverar system återställning på enhetarna C: och D: på den lokala datorn.

## PARAMETRAR

### – Enhet
Anger fil systemets enheter.
Ange en eller flera enhets beteckningar för fil systemet, varje följt av ett kolon och ett omvänt snedstreck som omges av citat tecken, t. ex. C:\ eller D:\.
Den här parametern är obligatorisk.

Du kan inte använda denna cmdlet för att aktivera system återställning på en fjärran sluten nätverks enhet, även om enheten är mappad till den lokala datorn och du inte kan aktivera system återställning på enheter som inte är berättigade till system återställning, t. ex. externa enheter.

Om du vill aktivera system återställning på valfri enhet måste system återställning vara aktiverat på system enheten, antingen före eller samtidigt.

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
Det går inte att skicka pipe-objekt till denna cmdlet.

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

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Starta om datorn](Restart-Computer.md)

[Återställa-dator](Restore-Computer.md)
