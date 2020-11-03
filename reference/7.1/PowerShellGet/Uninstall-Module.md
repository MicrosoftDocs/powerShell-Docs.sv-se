---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/02/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Module
ms.openlocfilehash: 77a89a9189d3ae8f7c3450bdddbe9456b4e941c7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264056"
---
# Uninstall-Module

## SAMMANFATTNING
Avinstallerar en modul.

## SYNTAX

### NameParameterSet (standard)

```
Uninstall-Module [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### InputObject

```
Uninstall-Module [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Uninstall-Module`Cmdleten avinstallerar en angiven modul från den lokala datorn. Du kan inte avinstallera en modul om den har andra moduler som beroenden.

## EXEMPEL

### Exempel 1: avinstallera en modul

Det här exemplet avinstallerar en modul.

```powershell
Uninstall-Module -Name SpeculationControl
```

`Uninstall-Module` använder parametern **Name** för att ange den modul som ska avinstalleras från den lokala datorn.

### Exempel 2: Använd pipelinen för att avinstallera en modul

I det här exemplet används pipelinen för att avinstallera en modul.

```powershell
Get-InstalledModule -Name SpeculationControl | Uninstall-Module
```

`Get-InstalledModule` använder **Name** -parametern för att ange modulen. Objektet skickas ned pipelinen till `Uninstall-Module` och avinstalleras.

## PARAMETRAR

### -AllowPrerelease

Gör att du kan avinstallera en modul som är markerad som en för hands version.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AllVersions

Anger att du vill inkludera alla tillgängliga versioner av en modul. Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion** , **MaximumVersion** eller **RequiredVersion** .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan du kör `Uninstall-Module` .

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

Tvingar `Uninstall-Module` körning utan att fråga användaren om bekräftelse.

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

### – InputObject

Accepterar ett **PSRepositoryItemInfo** -objekt. Till exempel, utdata `Get-InstalledModule` till en variabel och Använd variabeln som **InputObject** -argument.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – MaximumVersion

Anger den maximala eller nyaste versionen av modulen som ska avinstalleras. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – MinimumVersion

Anger den lägsta version av modulen som ska avinstalleras. Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger en matris med Modulnamn som ska avinstalleras.

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – RequiredVersion

Anger det exakta versions numret för den modul som ska avinstalleras.

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -WhatIf

Visar vad som händer om `Uninstall-Module` körs. Cmdleten körs inte.

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

### System.String[]

### System. Management. Automation. PSObject []

### System. String

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Sök-modul](Find-Module.md)

[Get-InstalledModule](Get-InstalledModule.md)

[Publicera-modul](Publish-Module.md)

[Spara-modul](Save-Module.md)

[Update-modul](Update-Module.md)

