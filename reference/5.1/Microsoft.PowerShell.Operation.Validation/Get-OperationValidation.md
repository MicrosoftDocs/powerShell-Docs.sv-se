---
external help file: Microsoft.PowerShell.Operation.Validation-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Operation.Validation
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.operation.validation/get-operationvalidation?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-OperationValidation
ms.openlocfilehash: 22ff12848fb7aefaa7f684ee5d8723cc723a5879
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265281"
---
# Get-OperationValidation

## SAMMANFATTNING
Hämtar tester för åtgärds validerings ramverk.

## SYNTAX

```
Get-OperationValidation [[-ModuleName] <String[]>] [-TestType <String[]>] [<CommonParameters>]
```

## BESKRIVNING
**Get-OperationValidation** -cmdlet: en hämtar ett åtgärds validerings Ramverks test för installerade moduler.

Moduler som innehåller en diagnostik-mapp inspekteras för pester-tester i den enkla eller fullständiga undermappen, eller både och.

## EXEMPEL

### Exempel 1: Hämta verifierings test för åtgärd

```
PS C:\> Get-OperationValidation -ModuleName "C:\temp\modules\AddNumbers"
    Type:     Simple
    File:     addnum.tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Simple\addnum.tests.ps1
    Name:
        Add-Em
        Subtract em
        Add-Numbers
    Type:     Comprehensive
    File:     Comp.Adding.Tests.ps1
    FilePath: C:\temp\modules\AddNumbers\Diagnostics\Comprehensive\Comp.Adding.Tests.ps1
    Name:
        Comprehensive Adding Tests
        Comprehensive Subtracting Tests
        Comprehensive Examples
```

Med det här kommandot får du verifieringstester från modulen med namnet AddNumbers i mappen C:\temp\modules.

## PARAMETRAR

### -Modulnamn
Anger en matris med namn på moduler.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TestType
Anger en matris med test typer.
Giltiga värden är enkel, fullständig eller både och.
Standardvärdet är "enkel, fullständig".

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Simple, Comprehensive

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka någon indatamängd till denna cmdlet.

## UTDATA

### PSCustomObject
**PSCustomObject** beskriver verifieringen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Invoke-OperationValidation](Invoke-OperationValidation.md)
