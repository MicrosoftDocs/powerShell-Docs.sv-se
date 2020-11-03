---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/get-logproperties?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LogProperties
ms.openlocfilehash: 0f675c2b0bf2b7e5ebfe3a1677f5bc194e8fe844
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264728"
---
# Get-LogProperties

## SAMMANFATTNING
Hämtar egenskaperna för en händelse logg i Windows.

## SYNTAX

```
Get-LogProperties [-Name] <string> [<CommonParameters>]
```

## BESKRIVNING

Den här cmdleten hämtar konfigurations inställningarna för en händelse logg i Windows. Denna cmdlet används av `Enable-PSTrace` `Disable-PSTrace` cmdletarna och.

## EXEMPEL

### Exempel 1: hämta konfigurations inställningarna för händelse loggen i Windows PowerShell

```powershell
Get-LogProperties 'Windows PowerShell'
```

```Output
Name       : Windows PowerShell
Enabled    : True
Type       : Admin
Retention  : False
AutoBackup : False
MaxLogSize : 15728640
```

## PARAMETRAR

### -Name

Namnet på händelse leverantören.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object

## UTDATA

### Microsoft. PowerShell. Diagnostics. LogDetails

**PSDiagnostics** -modulen lägger till **LogDetails** -klassen i `Microsoft.PowerShell.Diagnostics` namn området.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Set-LogProperties](Set-LogProperties.md)

[Aktivera – PSTrace](Enable-PSTrace.md)

[Disable-PSTrace](Disable-PSTrace.md)
