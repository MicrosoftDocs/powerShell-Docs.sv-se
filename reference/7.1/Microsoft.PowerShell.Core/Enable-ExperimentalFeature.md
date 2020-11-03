---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ExperimentalFeature
ms.openlocfilehash: 8a2a3a6be58f056b894890fdba4e923e13657c29
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267849"
---
# Enable-ExperimentalFeature

## SAMMANFATTNING
Aktivera en experimentell funktion när du startar en ny instans av PowerShell.

## SYNTAX

```
Enable-ExperimentalFeature [-Name] <String[]> [-Scope <ConfigScope>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Enable-ExperimentalFeature`Cmdleten aktiverar experimentella funktioner genom att lägga till de namngivna experimentella funktionerna i `powershell.config.json` inställnings filen Läs på PowerShell-start.

Denna cmdlet introducerades i PowerShell 6,2.

> [!NOTE]
> Alla ändringar av experiment funktions läget börjar bara gälla vid omstart av PowerShell

## EXEMPEL

### Exempel 1: Aktivera en experimentell funktion

I det här exemplet, om den här experimentella funktionen tidigare har inaktiverats, `powershell.config.json` uppdateras filen för att användaren ska kunna aktivera funktionen när PowerShell startas om.
När inget är klart skickas utdata till pipelinen och endast ett varnings meddelande visas.

```powershell
Enable-ExperimentalFeature PSImplicitRemotingBatching
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

Namn eller namn på de experimentella funktioner som ska aktive ras.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### ExperimentalFeature

Pipe-instanser av ExperimentalFeature från `Get-ExperimentalFeature` cmdlet för att aktivera.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

Ändringar av status för en experimentell funktion börjar bara gälla vid omstart av PowerShell.

## RELATERADE LÄNKAR

[Disable-ExperimentalFeature](Disable-ExperimentalFeature.md)

[Get-ExperimentalFeature](Get-ExperimentalFeature.md)

