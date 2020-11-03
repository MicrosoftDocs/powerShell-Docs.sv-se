---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: c5e3cb677a736595d1acd98c6f4be4d43b2151ba
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266900"
---
# Get-PSSessionCapability

## SAMMANFATTNING
Hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.

## SYNTAX

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **Get-PSSessionCapability** hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.
Använd denna cmdlet för att granska anpassade sessionsinställningar för användare.

Från och med Windows PowerShell 5,0 kan du använda egenskapen **RoleDefinitions** i en session konfigurations fil (. PSSC).
Med den här egenskapen kan du ge användarna olika funktioner på en begränsad slut punkt baserat på grupp medlemskap.
Cmdleten **Get-PSSessionCapability** minskar komplexiteten när du granskar de här slut punkterna genom att låta dig bestämma de exakta funktioner som beviljas en användare.

Som standard returnerar cmdleten **Get-PSSessionCapability** en lista med kommandon som den angivna användaren kan köra i den angivna slut punkten.
Detta motsvarar användaren som kör **Get-Command** i den angivna slut punkten.
Vid körning med *fullständig* parameter returnerar denna cmdlet ett **InitialSessionState** -objekt.
Det här objektet innehåller information om PowerShell-körnings utrymme som den angivna användaren skulle interagera med för den angivna slut punkten.
Den innehåller information som språk läge, körnings princip och miljövariabler.

## EXEMPEL

### Exempel 1: Hämta kommandon som är tillgängliga för en användare

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

Det här exemplet returnerar de kommandon som är tillgängliga för användaren CONTOSO\User vid anslutning till Endpoint1-begränsade slut punkter på den lokala datorn.

### Exempel 2: Hämta information om en körnings utrymme för en användare

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

Det här exemplet returnerar information om körnings utrymme som användaren CONTOSO\User skulle interagera med vid anslutning till Endpoint1-begränsad slut punkt.

## PARAMETRAR

### – ConfigurationName

Anger den begränsade sessionen som du inspekterar (slut punkt).

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

### – Fullständig

Anger att denna cmdlet returnerar hela det första sessionstillståndet för den angivna användaren vid den angivna begränsade slut punkten.

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

### -Username

Anger den användare vars funktioner du undersöker.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### System. Management. Automation. AliasInfo

### System. Management. Automation. FunctionInfo

### System.Management.Automation.Runspaces.InitialSessionState

## ANTECKNINGAR

## RELATERADE LÄNKAR

[New-PSRoleCapabilityFile](New-PSRoleCapabilityFile.md)
