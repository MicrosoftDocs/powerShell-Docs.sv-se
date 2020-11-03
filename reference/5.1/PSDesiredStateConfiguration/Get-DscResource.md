---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscResource
ms.openlocfilehash: 4a46e3b78ae9db4ea58f97daf37dca399c925549
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/24/2020
ms.locfileid: "93268731"
---
# Get-DscResource

## SAMMANFATTNING
Hämtar DSC-resurser (Desired State Configuration) som finns på datorn.

## SYNTAX

```
Get-DscResource [[-Name] <String[]>] [[-Module] <Object>] [-Syntax] [<CommonParameters>]
```

## BESKRIVNING

`Get-DscResource`Cmdlet: en hämtar de POWERSHELL DSC-resurser som finns på datorn. Den här cmdleten identifierar bara de resurser som är installerade i PSModulePath. Den visar information om inbyggda och anpassade providers som skapas av användaren. Denna cmdlet visar också information om sammansatta resurser, som är andra konfigurationer som paketeras som moduler eller som skapas vid körning i sessionen.

## EXEMPEL

### Exempel 1: Hämta alla resurser på den lokala datorn

```powershell
Get-DscResource
```

Det här kommandot hämtar alla resurser på den lokala datorn.

### Exempel 2: Hämta en resurs genom att ange namnet

```powershell
Get-DscResource -Name "WindowsFeature"
```

Det här kommandot hämtar WindowsFeature-resursen.

### Exempel 3: Hämta alla resurser från en modul

```powershell
Get-DscResource -Module "xHyper-V"
```

Det här kommandot hämtar alla resurser från xHyper-V-modulen.

### Exempel 4: Hämta en resurs med hjälp av jokertecken

```powershell
Get-DscResource -Name P*,r*
```

Det här kommandot hämtar alla resurser som matchar jokertecknet som anges av **namn** parametern.

### Exempel 5: Hämta en resurs-syntax

```powershell
Get-DscResource -Name "WindowsFeature" -Syntax
```

Det här kommandot hämtar WindowsFeature-resursen och visar syntaxen för resursen.

### Exempel 6: Hämta alla egenskaper för en resurs

```powershell
Get-DscResource -Name "User" | Select-Object -ExpandProperty Properties
```

Det här kommandot hämtar användar resursen och använder sedan pipeline-operatorn för att returnera alla egenskaper för användar resursen.

### Exempel 7: Hämta alla resurser från en angiven modul med en angiven version

```powershell
Get-DscResource -Module @{ModuleName='xHyper-V';RequiredVersion='3.0.0.0'}
```

Det här kommandot hämtar alla resurser från xHyper-V-modulen med version 3.0.0.0.

## PARAMETRAR

### – Modul

Anger namnet eller det fullständigt kvalificerade namnet på den modul som du vill visa DSC-resursen för.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger en matris med namnen på den DSC-resurs som ska visas.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Syntax

Anger att cmdleten returnerar kommandosyntaxen för de angivna DSC-resurserna. Den returnerade syntaxen visar hur du använder resurserna i ett PowerShell-skript.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

### System. Object

## UTDATA

### Microsoft. PowerShell. DesiredStateConfiguration. DscResourceInfo []

### sträng []

## ANTECKNINGAR

- `Get-DscResource` hittar inte klassbaserade DSC-resurser i PowerShell-versioner under 7,0.

## RELATERADE LÄNKAR

[Översikt över Desired State Configuration för PowerShell](/powershell/scripting/dsc/overview/overview)

[Invoke-Dscresource Keyword Supports](Invoke-DscResource.md)
