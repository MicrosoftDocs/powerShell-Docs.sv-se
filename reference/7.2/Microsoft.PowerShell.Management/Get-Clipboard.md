---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: b0a9e5d1707e0d2f46c25991ddceff27d1b85287
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710435"
---
# Get-Clipboard

## SAMMANFATTNING
Hämtar innehållet i Urklipp.

## SYNTAX

```
Get-Clipboard [-Raw] [<CommonParameters>]
```

## BESKRIVNING

`Get-Clipboard`Cmdleten hämtar innehållet i Urklipp som text. Flera rader med text returneras som en sträng mat ris som liknar `Get-Content` .

> [!NOTE]
> I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen. Denna cmdlet stöds inte på macOS.

## EXEMPEL

### Exempel 1: hämta innehållet i Urklipp och visa det på kommando raden

I det här exemplet har vi kopierat texten "Hej" till Urklipp.

```powershell
Get-Clipboard
```

```Output
hello
```

## PARAMETRAR

### – RAW

Hämtar hela innehållet i Urklipp. Flerradig text returneras som en enskild Multiline-sträng i stället för en sträng mat ris.

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

## UTDATA

### System. String

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Ange Urklipp](Set-Clipboard.md)
