---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 6e8903d6ee1b9bb38c42abd866a1657e86d2f3ac
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261535"
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
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

## UTDATA

### System. GUID
Denna cmdlet returnerar ett GUID.

## ANTECKNINGAR

## RELATERADE LÄNKAR
