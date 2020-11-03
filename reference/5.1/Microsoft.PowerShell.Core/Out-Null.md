---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-null?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Null
ms.openlocfilehash: 5a949629cdf0f0822866863822e82e70fc38d8c2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264224"
---
# Out-Null

## SAMMANFATTNING
Döljer utdata i stället för att skicka den till pipelinen eller genom att visa den.

## SYNTAX

```
Out-Null [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **out-null** skickar utdata till null, i praktiken, tar bort den från pipelinen och förhindrar att utdata visas på skärmen. Detta påverkar bara standardutdata-dataströmmen.
Andra utgående strömmar, t. ex. fel strömmen, påverkas inte. Undantag visas. Detta gör det enklare att testa kommandot för eventuella fel.

## EXEMPEL

### Exempel 1: ta bort utdata

```
PS C:\> Get-ChildItem | Out-Null
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

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* De cmdletar som **innehåller verbet** ( **out** -cmdletarna) har inga parametrar för namn eller fil Sök vägar. Om du vill skicka data till en **out** -cmdlet använder du en pipeline-operator (|) för att skicka utdata från ett Windows PowerShell-kommando till-cmdlet: en. Du kan också lagra data i en variabel och använda parametern *InputObject* för att skicka data till cmdleten. Mer information finns i exemplen.
* **Out-null** returnerar inga utdata-objekt. Om du skickar utdata från **out-null** till Get-Member-cmdlet: en **får** du rapporter om att inga objekt har angetts.

## RELATERADE LÄNKAR

[Ut-standard](Out-Default.md)

[Ut-värd](Out-Host.md)
