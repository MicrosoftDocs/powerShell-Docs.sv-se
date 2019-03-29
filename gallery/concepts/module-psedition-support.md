---
ms.date: 03/28/2019
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Moduler med kompatibla PowerShell-utgåvor
ms.openlocfilehash: 425588c168a4f864fdc0c52aa53cfd748b80dc98
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623848"
---
# <a name="modules-with-compatible-powershell-editions"></a>Moduler med kompatibla PowerShell-utgåvor

Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** Bygger på .NET Framework, gäller för Windows PowerShell v4.0 och nedan samt Windows PowerShell 5.1 på Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-versioner.
- **Core Edition:** Bygger på .NET Core, gäller för PowerShell Core 6.0 och senare samt Windows PowerShell 5.1 på begränsade utgåvor av Windows, till exempel IoT för Windows och Windows Nanoserver.

Mer information om PowerShell-utgåvor finns [about_PowerShell_Editions][].

## <a name="declaring-compatible-editions"></a>Deklarera kompatibla versioner

Modulskapare kan fastställa om deras moduler är kompatibla med en eller flera PowerShell-utgåvor med hjälp av CompatiblePSEditions-modulens manifestnyckel. Den här nyckeln stöds bara på PowerShell 5.1 eller senare.

> [!NOTE]
> När ett modulmanifest anges med CompatiblePSEditions-nyckel, kan det inte importeras på PowerShell-versioner 4 och nedan.

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

## <a name="targeting-multiple-editions"></a>Riktar in sig på flera versioner

Modulskapare kan publicera en enda modulen riktar in sig på att ena eller båda PowerShell-utgåvor (Desktop och Core).

En enda modul fungerar på både Desktop- och Core-utgåvor, i modulen författare har att lägga till nödvändig kod i antingen RootModule eller i modulmanifestet med $PSEdition variabeln. Moduler kan ha två uppsättningar kompilerade DLL: er som både på CoreCLR och FullCLR. Här följer några av alternativ för att paketera din modul med logik för att läsa in rätt DLL-filer.

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a>Alternativ 1: Paketera en modul för flera versioner och flera versioner av PowerShell

Modulen mappinnehåll

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

Innehållet i filen PSScriptAnalyzer.psd1

```powershell
@{

# Author of this module
Author = 'Microsoft Corporation'

# Script module or binary module file associated with this manifest.
RootModule = 'PSScriptAnalyzer.psm1'

# Version number of this module.
ModuleVersion = '1.6.1'

# ---
}
```

Läser in de nödvändiga sammansättningarna beroende på den aktuella utgåvan eller versionen nedan logik.

Innehållet i PSScriptAnalyzer.psm1-filen:

```powershell
#
# Script module for module 'PSScriptAnalyzer'
#
Set-StrictMode -Version Latest

# Set up some helper variables to make it easier to work with the module
$PSModule = $ExecutionContext.SessionState.Module
$PSModuleRoot = $PSModule.ModuleBase

# Import the appropriate nested binary module based on the current PowerShell version
$binaryModuleRoot = $PSModuleRoot


if (($PSVersionTable.Keys -contains "PSEdition") -and ($PSVersionTable.PSEdition -ne 'Desktop')) {
    $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'coreclr'
}
else
{
    if ($PSVersionTable.PSVersion -lt [Version]'5.0')
    {
        $binaryModuleRoot = Join-Path -Path $PSModuleRoot -ChildPath 'PSv3'
    }
}

$binaryModulePath = Join-Path -Path $binaryModuleRoot -ChildPath 'Microsoft.Windows.PowerShell.ScriptAnalyzer.dll'
$binaryModule = Import-Module -Name $binaryModulePath -PassThru

# When the module is unloaded, remove the nested binary module that was loaded with it
$PSModule.OnRemove = {
    Remove-Module -ModuleInfo $binaryModule
}
```

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a>Alternativ 2: Använd $PSEdition variabeln i PSD1-fil för att läsa in rätt DLL: er och kapslade/krävs moduler

I PS 5.1 eller senare tillåts $PSEdition global variabel i modulen manifestfilen. Med den här variabeln kan anger modulägaren villkorlig värden i modulen manifestfilen. $PSEdition variabeln kan refereras i begränsade språkläge eller ett Data-avsnitt.

> [!NOTE]
> När ett modulmanifest anges med CompatiblePSEditions-nyckel eller använder `$PSEdition` variabel, det går inte att importera på lägre versioner av PowerShell.

Exemplet modulen manifestfilen med CompatiblePSEditions-nyckel

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

### <a name="module-contents"></a>Modulen innehållet

```powershell
dir -Recurse
```

```Output
    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
d-----    7/5/2016   1:37 PM          clr
d-----    7/5/2016   1:36 PM          coreclr
-a----    7/5/2016   1:34 PM     4906 ModuleWithEditions.psd1

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\clr

Mode           LastWriteTime    Length Name
----           -------------    ------ ----
-a----    7/5/2016   1:35 PM         0 MyFullClrNM1.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrNM2.dll
-a----    7/5/2016   1:35 PM         0 MyFullClrRM.dl

    Directory: C:\Users\manikb\Documents\WindowsPowerShell\Modules\ModuleWithEditions\coreclr

Mode           LastWriteTime   Length Name
----           -------------   ------ ----
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM1.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrNM2.dll
-a----    7/5/2016   1:35 PM        0 MyCoreClrRM.dl
```

PowerShell-galleriet användare kan hitta listan över moduler som stöds på en viss version av PowerShell med hjälp av taggar PSEdition_Desktop och PSEdition_Core.

Moduler utan PSEdition_Desktop och PSEdition_Core taggar anses fungera på PowerShell Desktop-versioner.

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a>Mer information

[Skript med PSEditions](script-psedition-support.md)

[Stöd för PSEditions på PowerShellGallery](../how-to/finding-packages/searching-by-compatibility.md)

[Uppdatera modulmanifestet](/powershell/module/powershellget/update-modulemanifest)

[about_PowerShell_Editions][]

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
