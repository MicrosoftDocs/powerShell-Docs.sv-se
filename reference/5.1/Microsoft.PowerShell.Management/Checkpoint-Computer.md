---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/checkpoint-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Checkpoint-Computer
ms.openlocfilehash: 61f8d626cd45cfe47f0e65a3043696a01c97ca20
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266265"
---
# Checkpoint-Computer

## SAMMANFATTNING
Skapar en system återställnings punkt på den lokala datorn.

## SYNTAX

```
Checkpoint-Computer [-Description] <String> [[-RestorePointType] <String>] [<CommonParameters>]
```

## BESKRIVNING

`Checkpoint-Computer`Cmdleten skapar en system återställnings punkt på den lokala datorn.

System återställnings punkter och `Checkpoint-Computer` cmdlet stöds endast på klient operativ system, till exempel Windows 8, Windows 7, Windows Vista och Windows XP.

Från och med Windows 8 kan du `Checkpoint-Computer` inte skapa fler än en kontroll punkt varje dag.

## EXEMPEL

### Exempel 1: skapa en system återställnings punkt

```powershell
Checkpoint-Computer -Description "Install MyApp"
```

Det här kommandot skapar en system återställnings punkt som kallas installera MyApp.
Den använder standard typen för APPLICATION_INSTALL återställnings punkt.

### Exempel 2: skapa en återställnings punkt för system MODIFY_SETTINGS

```powershell
Checkpoint-Computer -Description "ChangeNetSettings" -RestorePointType MODIFY_SETTINGS
```

Det här kommandot skapar en MODIFY_SETTINGS system återställnings punkt med namnet "ChangeNetSettings".

## PARAMETRAR

### -Beskrivning

Anger ett beskrivande namn för återställnings punkten.
Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RestorePointType

Anger typen av återställnings punkt.
Standardvärdet är APPLICATION_INSTALL.

De acceptabla värdena för den här parametern är:

- APPLICATION_INSTALL
- APPLICATION_UNINSTALL
- DEVICE_DRIVER_INSTALL
- MODIFY_SETTINGS
- CANCELLED_OPERATION

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RPT
Accepted values: APPLICATION_INSTALL, APPLICATION_UNINSTALL, DEVICE_DRIVER_INSTALL, MODIFY_SETTINGS, CANCELLED_OPERATION

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till `Checkpoint-Computer` .

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

- Denna cmdlet använder **CreateRestorePoint** -metoden för **SystemRestore** -klassen med en **BEGIN_SYSTEM_CHANGE** -händelse.
- Från och med Windows 8 kan du `Checkpoint-Computer` inte skapa fler än en system återställnings punkt varje dag. Om du försöker skapa en ny återställnings punkt innan 24-timmarsperiod har förflutit, genererar Windows PowerShell följande fel:

  `"A new system restore point cannot be created because one has already been created within the past 24 hours.
  Please try again later."`

## RELATERADE LÄNKAR

[Disable-ComputerRestore](Disable-ComputerRestore.md)

[Aktivera – ComputerRestore](Enable-ComputerRestore.md)

[Get-ComputerRestorePoint](Get-ComputerRestorePoint.md)

[Återställa-dator](Restore-Computer.md)
