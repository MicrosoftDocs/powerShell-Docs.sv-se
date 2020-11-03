---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Module
ms.openlocfilehash: a1052c357f19fd8f06eb39a14f8e8eded0c881a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264182"
---
# Remove-Module

## SAMMANFATTNING
Tar bort moduler från den aktuella sessionen.

## SYNTAX

### name

```
Remove-Module [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### FullyQualifiedName

```
Remove-Module [-FullyQualifiedName] <ModuleSpecification[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ModuleInfo

```
Remove-Module [-ModuleInfo] <PSModuleInfo[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Remove-module** tar bort medlemmarna i en modul, till exempel cmdlets och functions, från den aktuella sessionen.

Om modulen innehåller en sammansättning (. dll) tas alla medlemmar som implementeras av sammansättningen bort, men sammansättningen tas inte bort från minnet.

Denna cmdlet avinstallerar inte modulen eller tar bort den från datorn.
Den påverkar endast den aktuella PowerShell-sessionen.

## EXEMPEL

### Exempel 1: ta bort en modul

```powershell
Remove-Module -Name "BitsTransfer"
```

Det här kommandot tar bort BitsTransfer-modulen från den aktuella sessionen.

### Exempel 2: ta bort alla moduler

```powershell
Get-Module | Remove-Module
```

Det här kommandot tar bort alla moduler från den aktuella sessionen.

### Exempel 3: ta bort moduler med hjälp av pipelinen

```powershell
"FileTransfer", "PSDiagnostics" | Remove-Module -Verbose
```

```Output
VERBOSE: Performing operation "Remove-Module" on Target "filetransfer (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\filetransfer\filetransfer.psd1')".
VERBOSE: Performing operation "Remove-Module" on Target "Microsoft.BackgroundIntelligentTransfer.Management (Path: 'C:\Windows\assembly\GAC_MSIL\Microsoft.BackgroundIntelligentTransfer.Management\1.0.0.0__31bf3856ad364e35\Microsoft.BackgroundIntelligentTransfe
r.Management.dll')".
VERBOSE: Performing operation "Remove-Module" on Target "psdiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\psdiagnostics.psd1')".
VERBOSE: Removing imported function 'Start-Trace'.
VERBOSE: Removing imported function 'Stop-Trace'.
VERBOSE: Removing imported function 'Enable-WSManTrace'.
VERBOSE: Removing imported function 'Disable-WSManTrace'.
VERBOSE: Removing imported function 'Enable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Disable-PSWSManCombinedTrace'.
VERBOSE: Removing imported function 'Set-LogProperties'.
VERBOSE: Removing imported function 'Get-LogProperties'.
VERBOSE: Removing imported function 'Enable-PSTrace'.
VERBOSE: Removing imported function 'Disable-PSTrace'.
VERBOSE: Performing operation "Remove-Module" on Target "PSDiagnostics (Path: 'C:\Windows\system32\WindowsPowerShell\v1.0\Modules\psdiagnostics\PSDiagnostics.psm1')".
```

Det här kommandot tar bort BitsTransfer-och PSDiagnostics-modulerna från den aktuella sessionen.

Kommandot använder en pipeline-operator (|) för att skicka modulnamnet till **Remove-module**.
Den använder den *utförliga* gemensamma parametern för att få detaljerad information om de medlemmar som tas bort.

*Utförliga* meddelanden visar de objekt som tas bort.
Meddelandena skiljer sig eftersom BitsTransfer-modulen innehåller en sammansättning som implementerar dess cmdlets och en kapslad modul med sin egen sammansättning.
Modulen PSDiagnostics innehåller en modulens skript fil (. psm1) som exporterar funktioner.

### Exempel 4: ta bort en modul med ModuleInfo

```powershell
$a = Get-Module BitsTransfer
Remove-Module -ModuleInfo $a
```

Det här kommandot använder parametern *ModuleInfo* för att ta bort BitsTransfer-modulen.

## PARAMETRAR

### -Force

Anger att den här cmdleten tar bort skrivskyddade moduler.
Som standard tar **Remove-modulen** bara bort Läs-och skriv moduler.

De **skrivskyddade** och **readwrite** -värdena lagras i egenskapen **AccessMode** för en modul.

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

### -FullyQualifiedName

Anger de fullständigt kvalificerade namnen på de moduler som ska tas bort.

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ModuleInfo

Anger de modul-objekt som ska tas bort.
Ange en variabel som innehåller ett modul objekt ( **PSModuleInfo** ) eller ett kommando som hämtar ett modul-objekt, till exempel ett Get-Module-kommando.
Du kan också ta bort modul objekt för att **ta bort modulen**.

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger namnen på de moduler som ska tas bort.
Jokertecken är tillåtna.
Du kan också ta bort namn strängar för att **ta bort modulen**.

```yaml
Type: System.String[]
Parameter Sets: name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. Management. Automation. PSModuleInfo

Du kan ta bort modul namn och modul-objekt för att **ta bort modulen**.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Hämta modul](Get-Module.md)

[Importera-modul](Import-Module.md)

[about_Modules](About/about_Modules.md)
