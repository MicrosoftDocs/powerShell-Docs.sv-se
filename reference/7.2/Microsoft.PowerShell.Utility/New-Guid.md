---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: df7f9000cf66cebce83e3146cd5c95a7d1a78bf8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710087"
---
# New-Guid

## SAMMANFATTNING
Skapar ett GUID.

## SYNTAX

```
New-Guid [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **New-GUID** skapar en slumpmässig globalt unik IDENTIFIERARE (GUID).
Om du behöver ett unikt ID i ett skript kan du skapa ett GUID om det behövs.

## EXEMPEL

### Exempel 1: skapa en GUID

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

Det här kommandot skapar ett slumpmässigt GUID.
Alternativt kan du lagra utdata från denna cmdlet i en variabel som ska användas någon annan stans i ett skript.

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### System. GUID

Denna cmdlet returnerar ett GUID.

## ANTECKNINGAR

## RELATERADE LÄNKAR

