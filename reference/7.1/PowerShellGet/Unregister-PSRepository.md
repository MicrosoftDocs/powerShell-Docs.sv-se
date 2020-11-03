---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 769d1ac91cbbc580b3488ba84d14a759b6ef65d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265580"
---
# Unregister-PSRepository

## SAMMANFATTNING
Avregistrerar en lagrings plats.

## SYNTAX

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## BESKRIVNING

`Unregister-PSRepository`Cmdleten avregistrerar en lagrings plats för den aktuella användaren.

## EXEMPEL

### Exempel 1: avregistrera en lagrings plats

Det här exemplet avregistrerar lagrings platsen med namnet myNuGetSource.

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### Exempel 2: avregistrera alla databaser

Det här exemplet använder `Get-PSRepository` för att hämta alla registrerade databaser och använder pipelinen för att skicka dem till `Unregister-PSRepository` avregistrera dem.

```powershell
Get-PSRepository | Unregister-PSRepository
```

## PARAMETRAR

### -Name

Anger en matris med namnen på de databaser som ska tas bort.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

## UTDATA

### System. Object

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-PSRepository](Get-PSRepository.md)

[Registrera – PSRepository](Register-PSRepository.md)

[Set-PSRepository](Set-PSRepository.md)
