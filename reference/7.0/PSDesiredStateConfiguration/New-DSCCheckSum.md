---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/new-dscchecksum?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-DscChecksum
ms.openlocfilehash: 2a66f906025f7a25609080e0b8da7f01755cd2fa
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262185"
---
# New-DscChecksum

## SAMMANFATTNING
Skapar kontroll Summa filer för DSC-dokument och DSC-resurser.

## SYNTAX

```
New-DscChecksum [-Path] <String[]> [[-OutPath] <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **New-DSCCheckSum** genererar en kontroll Summa filer för DSC-dokument (Desired State Configuration) och komprimerade DSC-resurser.
Denna cmdlet skapar en kontroll Summa fil för varje konfiguration och resurs som ska användas i pull-läge.
DSC-tjänsten använder kontroll summorna för att kontrol lera att rätt konfiguration och resurser finns på målnoden.
Placera kontroll summorna tillsammans med tillhör ande DSC-dokument och komprimerade DSC-resurser i DSC-tjänstens arkiv.

## EXEMPEL

### Exempel 1: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\"
```

Det här kommandot skapar en kontroll Summa filer för alla konfigurationer i sökvägen C:\DSC\Configurations.
Alla filer för kontroll summor som redan finns hoppas över.

### Exempel 2: skapa kontroll Summa filer för alla konfigurationer i en angiven sökväg och skriv över de befintliga kontroll summor filerna

```
PS C:\> New-DscCheckSum -Path "C:\DSC\Configurations\" -Force
```

Det här kommandot skapar nya kontroll summor filer för alla konfigurationer i sökvägen C:\DSC\Configurations.
Om du anger *Force* -parametern kommer kommandot att skriva över alla eventuella kontroll Summa filer som redan finns.

## PARAMETRAR

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

### -Force

Anger att cmdleten skriver över den angivna utdatafilen om den redan finns.

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

### -Sökväg

Anger sökväg och fil namn för filen med utgångs kontroll.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till indatafilen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ConfigurationPath

Required: True
Position: 0
Default value: None
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

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)
