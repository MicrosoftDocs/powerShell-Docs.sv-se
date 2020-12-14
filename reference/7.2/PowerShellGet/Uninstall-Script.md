---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/uninstall-script?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Script
ms.openlocfilehash: 2cd8b51e1d4ef11a0a5f9e3542ff89e094854d8c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710033"
---
# Uninstall-Script

## SAMMANFATTNING
Avinstallerar ett skript.

## SYNTAX

### NameParameterSet (standard)

```
Uninstall-Script [-Name] <String[]> [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-Force] [-AllowPrerelease] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Uninstall-Script [-InputObject] <PSObject[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Uninstall-Script`Cmdleten avinstallerar ett angivet skript från den lokala datorn.

## EXEMPEL

### Exempel 1: Avinstallera ett skript

I det här exemplet avinstalleras ett skript.

```powershell
Uninstall-Script -Name UpdateManagement-Template
```

`Uninstall-Script` använder parametern **Name** för att ange det skript som ska avinstalleras från den lokala datorn.

### Exempel 2: Använd pipelinen för att avinstallera ett skript

I det här exemplet används pipelinen för att avinstallera ett skript.

```powershell
Get-InstalledScript -Name UpdateManagement-Template | Uninstall-Script
```

`Get-InstalledScript` använder parametern **Name** för att ange skriptet. Objektet skickas ned i pipeline till `Uninstall-Script` och skriptet avinstalleras.

## PARAMETRAR

### -AllowPrerelease

Gör att du kan avinstallera ett skript som marker ATS som en för hands version.

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

Du uppmanas att bekräfta innan du kör `Uninstall-Script` .

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

Tvingar `Uninstall-Script` körning utan att fråga användaren om bekräftelse.

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

Accepterar ett **PSRepositoryItemInfo** -objekt. Till exempel, utdata `Get-InstalledScript` till en variabel och Använd variabeln som **InputObject** -argument.

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

Anger den maximala eller nyaste versionen av skriptet som ska avinstalleras. Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

Anger den lägsta versionen av skriptet som ska avinstalleras. Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.

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

Anger en matris med skript namn att avinstallera.

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

Anger det exakta versions numret för det skript som ska avinstalleras.

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

Visar vad som händer om `Uninstall-Script` körs. Cmdleten körs inte.

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

[Sök – skript](Find-Script.md)

[Installera – skript](Install-Script.md)

[Publicera – skript](Publish-Script.md)

[Spara – skript](Save-Script.md)

[Uppdatera skript](Update-Script.md)

