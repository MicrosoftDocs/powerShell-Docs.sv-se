---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-experimentalfeature?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ExperimentalFeature
ms.openlocfilehash: e35e164f3116304efd52c71c1715ba70711f6253
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709612"
---
# Disable-ExperimentalFeature

## SAMMANFATTNING
Inaktivera en experimentell funktion när du startar en ny instans av PowerShell.

## SYNTAX

```
Disable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Disable-ExperimentalFeature`Cmdleten inaktiverar experimentella funktioner genom att ta bort de namngivna experimentella funktionerna från `powershell.config.json` inställnings filen Läs på PowerShell-start.

Denna cmdlet introducerades i PowerShell 6,2.

> [!NOTE]
> Alla ändringar av experiment funktions läget börjar bara gälla vid omstart av PowerShell

## EXEMPEL

### Exempel 1: inaktivera en experimentell funktion

I det här exemplet, om den här experimentella funktionen tidigare har Aktiver ATS, `powershell.config.json` uppdateras filen så att användaren inte aktiverar funktionen när PowerShell startas om.
När inget är klart skickas utdata till pipelinen och endast ett varnings meddelande visas.

```powershell
PS C:\> Disable-ExperimentalFeature PSImplicitRemotingBatching
```

```Output
WARNING: Enabling and disabling experimental features do not take effect until next start of PowerShell.
```

## PARAMETRAR

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Namn eller namn på de experimentella funktioner som ska inaktive ras.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Omfattning

Bestämmer vilka som `powershell.config.json` ska uppdateras om det påverkar alla användare eller bara den aktuella användaren.

```yaml
Type: System.Management.Automation.Configuration.ConfigScope
Parameter Sets: (All)
Aliases:
Accepted values: AllUsers, CurrentUser

Required: False
Position: Named
Default value: CurrentUser
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
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### ExperimentalFeature

Pipe-instanser av ExperimentalFeature från `Get-ExperimentalFeature` cmdlet för att inaktivera.

## UTDATA

### Inga

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

Ändringar av status för en experimentell funktion börjar bara gälla vid omstart av PowerShell.

## RELATERADE LÄNKAR

[Aktivera – ExperimentalFeature](Enable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

