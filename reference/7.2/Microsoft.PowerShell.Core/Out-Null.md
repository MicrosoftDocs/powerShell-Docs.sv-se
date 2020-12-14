---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: fe28f52088a82b93799724de7a7a3f20ce42e36b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710489"
---
# Out-Null

## SAMMANFATTNING
Döljer utdata i stället för att skicka den till pipelinen eller genom att visa den.

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **out-null** skickar utdata till null, i praktiken, tar bort den från pipelinen och förhindrar att utdata visas på skärmen.

## EXEMPEL

### Exempel 1: ta bort utdata

```powershell
Get-ChildItem | Out-Null
```

Detta kommando hämtar objekt på den aktuella platsen/katalogen, men utdata skickas inte via pipelinen eller visas inte på kommando raden.
Detta är användbart för att dölja utdata som du inte behöver.

## PARAMETRAR

### – InputObject

Anger det objekt som ska skickas till NULL (tas bort från pipelinen).
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka alla objekt till denna cmdlet.

## UTDATA

### Inga

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* De cmdletar som **innehåller verbet** ( **out** -cmdletarna) har inga parametrar för namn eller fil Sök vägar. Om du vill skicka data till en **out** -cmdlet använder du en pipeline-operator (|) för att skicka utdata från ett PowerShell-kommando till cmdlet: en. Du kan också lagra data i en variabel och använda parametern *InputObject* för att skicka data till cmdleten. Mer information finns i exemplen.
* **Out-null** returnerar inga utdata-objekt. Om du skickar utdata från **out-null** till Get-Member-cmdlet: en **får** du rapporter om att inga objekt har angetts.

## RELATERADE LÄNKAR

[Ut-standard](Out-Default.md)

[Ut-värd](Out-Host.md)

