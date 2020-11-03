---
external help file: PSDesiredStateConfiguration-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: 8425c3e68573fe214ec5de465c8492e0bf99b309
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2020
ms.locfileid: "93269187"
---
# Invoke-DscResource

## SAMMANFATTNING
Kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.

## SYNTAX

```
Invoke-DscResource [-Name] <String> [[-ModuleName] <ModuleSpecification>] [-Method] <String>
 [-Property] <Hashtable> [<CommonParameters>]
```

## BESKRIVNING

`Invoke-DscResource`Cmdleten kör en metod för en angiven DSC-resurs (Desired State Configuration) för PowerShell.

Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument. Med den här cmdleten kan konfigurations hanterings produkter hantera Windows eller Linux med hjälp av DSC-resurser. Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn körs med fel sökning aktiverat.

> [!NOTE]
> `Invoke-DscResource` är en experimentell funktion i PowerShell 7. Om du vill använda cmdleten måste du aktivera den med hjälp av följande kommando.
>
> `Enable-ExperimentalFeature PSDesiredStateConfiguration.InvokeDscResource`

## EXEMPEL

### Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper

Det här exemplet anropar **set** -metoden för en resurs med namnet **WindowsProcess** och ger den obligatoriska **sökvägen** och **argument** egenskaperna för att starta den angivna Windows-processen.

```powershell
Invoke-DscResource -Name WindowsProcess -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'
  Arguments = ''
}
```

### Exempel 2: anropa test metoden för en resurs för en angiven modul

I det här exemplet anropas **test** metoden för en resurs med namnet **WindowsProcess** , som finns i modulen med namnet **PSDesiredStateConfiguration**.

```powershell
$SplatParam = @{
  Name = 'WindowsProcess'
  ModuleName = 'PSDesiredStateConfiguration'
  Property = @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''}
  Method = Test
}

Invoke-DscResource @SplatParam
```

## PARAMETRAR

### -Metod

Anger metoden för den resurs som denna cmdlet anropar. De acceptabla värdena för den här parametern är: **Get** , **set** och **test**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Modulnamn

Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnet på den DSC-resurs som ska startas.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – Egenskap

Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

### Microsoft. PowerShell. commands. ModuleSpecification

## UTDATA

### System. Object

## ANTECKNINGAR

- Tidigare kördes Windows PowerShell 5,1-resurser under system kontext, om inget annat anges med användar kontext med nyckeln **PsDscRunAsCredential**. I PowerShell 7,0, körs resurser i användarens kontext och **PsDscRunAsCredential** stöds inte längre. Tidigare konfigurationer som använder den här nyckeln kommer att utlösa ett undantag.

- Från och med PowerShell 7 `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser. Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration**.

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-Dscresource Keyword Supports](Get-DscResource.md)
