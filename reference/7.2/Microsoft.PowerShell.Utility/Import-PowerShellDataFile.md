---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-powershelldatafile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-PowerShellDataFile
ms.openlocfilehash: 2853c5757b12e75e50948192e5a9e29889553b8e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708614"
---
# Import-PowerShellDataFile

## SAMMANFATTNING
Importerar värden från en `.PSD1` fil utan att anropa dess innehåll.

## SYNTAX

### ByPath (standard)

```
Import-PowerShellDataFile [-Path] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Import-PowerShellDataFile [-LiteralPath] <String[]> [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en på `Import-PowerShellDataFile` ett säkert sätt importerar nyckel/värde-par från hash som definierats i en `.PSD1` fil. Värdena kan importeras med hjälp av `Invoke-Expression` filens innehåll.
Kör dock `Invoke-Expression` eventuell kod som finns i filen. Detta kan producera oönskade resultat eller köra osäker kod. `Import-PowerShellDataFile` importerar data utan att anropa koden.

## EXEMPEL

### Exempel 1: Hämta värden från PSD1

I det här exemplet hämtas de nyckel/värde-par som lagras i den hash-tabellen som behålls i `Configuration.psd1` filen. `Get-Content` används för att visa innehållet i `Configuration.psd1` filen.

```powershell
Get-Content .\Configuration.psd1
$config = Import-PowerShellDataFile .\Configuration.psd1
$config.AllNodes
```

```Output
@{
    AllNodes = @(
        @{
            NodeName = 'DSC-01'
        }
        @{
            NodeName = 'DSC-02'
        }
    )
}

Name                           Value
----                           -----
NodeName                       DSC-01
NodeName                       DSC-02
```

## PARAMETRAR

### -LiteralPath

Sökvägen till filen som importeras. Alla tecken i sökvägen behandlas som litterala värden.
Jokertecken bearbetas inte.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Sökvägen till filen som importeras. Jokertecken är tillåtna, men endast den första matchande filen importeras.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

## UTDATA

### System. Collections. hash

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Invoke-uttryck](Invoke-Expression.md)

[Importera – LocalizedData](Import-LocalizedData.md)

