---
ms.date: 06/10/2020
title: Moduler med kompatibla PowerShell-versioner
description: Den här artikeln förklarar hur PowerShellGet-cmdlets stöder Desktop-och Core-versioner av PowerShell-moduler.
ms.openlocfilehash: 530101590cf83a1f43cbb9ce32d07a7e0ec79253
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661485"
---
# <a name="modules-with-compatible-powershell-editions"></a>Moduler med kompatibla PowerShell-versioner

Från och med version 5,1 är PowerShell tillgängligt i olika versioner, vilket kännetecknar varierande funktions uppsättningar och plattformens kompatibilitet.

- **Desktop Edition:** Byggd på .NET Framework gäller för Windows PowerShell v 4.0 och tidigare samt Windows PowerShell 5,1 på Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-versioner.
- **Core-utgåva:** Bygger på .NET Core som gäller för PowerShell Core 6,0 och senare samt Windows PowerShell 5,1 på mindre Windows-versioner som Windows IoT och Windows Nanoserver.

Mer information om PowerShell-versioner finns [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Deklarera kompatibla utgåvor

Modulens författare kan deklarera att deras moduler är kompatibla med en eller flera PowerShell-versioner med hjälp av `CompatiblePSEditions` modulens manifest nyckel. Den här nyckeln stöds bara på PowerShell 5.1 eller senare.

> [!NOTE]
> När ett modul-manifest har angetts med `CompatiblePSEditions` nyckeln eller använder `$PSEdition` variabeln, kan den inte importeras på PowerShell v4 eller lägre.

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion 5.1
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

```powershell
$ModuleInfo | Get-Member CompatiblePSEditions
```

```Output
   TypeName: System.Management.Automation.PSModuleInfo

Name                 MemberType Definition
----                 ---------- ----------
CompatiblePSEditions Property   System.Collections.Generic.IEnumerable[string] CompatiblePSEditions {get;}
```

När du hämtar en lista över tillgängliga moduler kan du filtrera listan efter PowerShell-utgåva.

```powershell
Get-Module -ListAvailable -PSEdition Desktop
```

```Output
    Directory: C:\Program Files\WindowsPowerShell\Modules

ModuleType Version    Name                                ExportedCommands
---------- -------    ----                                ----------------
Manifest   1.0        ModuleWithPSEditions
```

```powershell
Get-Module -ListAvailable -PSEdition Core | % CompatiblePSEditions
```

```Output
Desktop
Core
```

Från och med PowerShell 6 `CompatiblePSEditions` används värdet för att bestämma om en modul är kompatibel när moduler importeras från `$env:windir\System32\WindowsPowerShell\v1.0\Modules` .
Detta beteende gäller endast för Windows. Utanför det här scenariot används värdet bara som metadata.

## <a name="finding-compatible-modules"></a>Söker efter kompatibla moduler

PowerShell-galleriet användare kan hitta listan över moduler som stöds på en angiven PowerShell-version med hjälp av Taggar **PSEdition_Desktop** och **PSEdition_Core** .

Moduler utan **PSEdition_Desktop** -och **PSEdition_Core** -Taggar anses fungera bra på PowerShell Desktop-versioner.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a>Rikta in sig på flera utgåvor

-Modulen författare kan publicera en enskild modul som riktar sig till antingen eller båda PowerShell-versionerna (Desktop och Core).

En enda modul kan fungera både i Desktop-och Core-versioner, i den här modulen måste författaren lägga till nödvändig logik i antingen RootModule eller i modulens manifest med `$PSEdition` variabeln. Moduler kan ha två uppsättningar med kompilerade dll: er riktade till både **CoreCLR** och **FullCLR** . Här är förpacknings alternativen med logik för att läsa in rätt DLL-filer.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Alternativ 1: paketera en modul för att rikta in dig på flera versioner och flera utgåvor av PowerShell

Mappinnehåll i moduler

- Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- PSScriptAnalyzer.psd1
- PSScriptAnalyzer.psm1
- ScriptAnalyzer.format.ps1xml
- ScriptAnalyzer.types.ps1xml
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- en-US\about_PSScriptAnalyzer.help.txt
- en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll
- PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll
- Settings\CmdletDesign.psd1
- Settings\DSC.psd1
- Settings\ScriptFunctions.psd1
- Settings\ScriptingStyle.psd1
- Settings\ScriptSecurity.psd1

Fil innehåll `PSScriptAnalyzer.psd1`

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Nedan följer logiken inläsning av de nödvändiga sammansättningarna beroende på aktuell version eller version.

Fil innehåll `PSScriptAnalyzer.psm1` :

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a>Alternativ 2: Använd $PSEdition variabel i PSD1-filen för att läsa in rätt DLL-filer

I PS 5,1 eller senare `$PSEdition` tillåts global variabel i manifest filen för modulen. Med den här variabeln kan modulen författare ange de villkorliga värdena i manifest filen för modulen. `$PSEdition` Det går att referera till variabeln i begränsat språk läge eller i ett data avsnitt.

Manifest fil för exempel modul med `CompatiblePSEditions` nyckel.

```powershell
@{
    # Script module or binary module file associated with this manifest.
    RootModule = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrRM.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrRM.dll'
    }

    # Supported PSEditions
    CompatiblePSEditions = 'Desktop', 'Core'

    # Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
    NestedModules = if($PSEdition -eq 'Core')
    {
        'coreclr\MyCoreClrNM1.dll',
        'coreclr\MyCoreClrNM2.dll'
    }
    else # Desktop
    {
        'clr\MyFullClrNM1.dll',
        'clr\MyFullClrNM2.dll'
    }
}
```

Modulens innehåll

- ModuleWithEditions\ModuleWithEditions.psd1
- ModuleWithEditions\clr\MyFullClrNM1.dll
- ModuleWithEditions\clr\MyFullClrNM2.dll
- ModuleWithEditions\clr\MyFullClrRM.dll
- ModuleWithEditions\coreclr\MyCoreClrNM1.dll
- ModuleWithEditions\coreclr\MyCoreClrNM2.dll
- ModuleWithEditions\coreclr\MyCoreClrRM.dll

## <a name="more-details"></a>Mer information

[Skript med PSEditions](script-psedition-support.md)

[PSEditions-stöd för PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Uppdatera modulmanifestet](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
