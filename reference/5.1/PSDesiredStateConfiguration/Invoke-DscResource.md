---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-DscResource
ms.openlocfilehash: d73d8d6a30e6b7c08b5a0b7988ea2327be34002a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266043"
---
# Invoke-DscResource

## SAMMANFATTNING
Kör en metod för en angiven DSC-resurs.

## SYNTAX

```
Invoke-DscResource [-Name] <String> [-Method] <String> -ModuleName <ModuleSpecification> -Property <Hashtable>
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Invoke-dscresource Keyword Supports** kör en metod för en angiven DSC-resurs (Desired State Configuration) för Windows PowerShell.
Innan du kör den här cmdleten ställer du in uppdaterings läget för den lokala Configuration Manager (LCM) på inaktive rad.

Den här cmdleten anropar en DSC-resurs direkt utan att skapa ett konfigurations dokument.
Med den här cmdleten kan konfigurations hanterings produkter hantera Windows med hjälp av DSC-resurser.
Den här cmdleten aktiverar även fel sökning av resurser när DSC-motorn eller LCM körs med fel sökning aktiverat.

## EXEMPEL

### Exempel 1: anropa set-metoden för en resurs genom att ange dess obligatoriska egenskaper

```
PS C:\> Invoke-DscResource -Name Log -Method Set -Property @{Message = 'Hello World'} -ModuleName PSDesiredStateConfiguration
```

Det här kommandot anropar **set** -metoden för en resurs med namnet log och anger en **meddelande** egenskap för den.

### Exempel 2: anropa test metoden för en resurs för en angiven modul

```
PS C:\> Invoke-DscResource -Name WindowsProcess -Method Test -Property @{Path = 'C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe'; Arguments = ''} -ModuleName PSDesiredStateConfiguration
```

Det här kommandot anropar **test** metoden för en resurs med namnet WindowsProcess, som finns i modulen med namnet PSDesiredStateConfiguration.

## PARAMETRAR

### -Metod
Anger metoden för den resurs som denna cmdlet anropar. De acceptabla värdena för den här parametern är: get, set och test.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Get, Set, Test

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Modulnamn
Anger namnet på den modul från vilken denna cmdlet anropar den angivna resursen.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Egenskap
Anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel respektive värde. Använd cmdleten **Get-dscresource Keyword Supports** för att identifiera resurs egenskaper och deras typer.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### Microsoft. Management. Infrastructure. CimInstance, system. Boolean

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Get-Dscresource Keyword Supports](Get-DscResource.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Set-DscLocalConfigurationManager](Set-DscLocalConfigurationManager.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
