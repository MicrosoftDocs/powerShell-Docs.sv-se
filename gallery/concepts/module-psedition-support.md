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
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="3f53d-103">Moduler med kompatibla PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="3f53d-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="3f53d-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="3f53d-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="3f53d-105">**Desktop Edition:** Bygger på .NET Framework, gäller för Windows PowerShell v4.0 och nedan samt Windows PowerShell 5.1 på Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-versioner.</span><span class="sxs-lookup"><span data-stu-id="3f53d-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="3f53d-106">**Core Edition:** Bygger på .NET Core, gäller för PowerShell Core 6.0 och senare samt Windows PowerShell 5.1 på begränsade utgåvor av Windows, till exempel IoT för Windows och Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="3f53d-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="3f53d-107">Mer information om PowerShell-utgåvor finns [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="3f53d-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="3f53d-108">Deklarera kompatibla versioner</span><span class="sxs-lookup"><span data-stu-id="3f53d-108">Declaring compatible editions</span></span>

<span data-ttu-id="3f53d-109">Modulskapare kan fastställa om deras moduler är kompatibla med en eller flera PowerShell-utgåvor med hjälp av CompatiblePSEditions-modulens manifestnyckel.</span><span class="sxs-lookup"><span data-stu-id="3f53d-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the CompatiblePSEditions module manifest key.</span></span> <span data-ttu-id="3f53d-110">Den här nyckeln stöds bara på PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3f53d-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="3f53d-111">När ett modulmanifest anges med CompatiblePSEditions-nyckel, kan det inte importeras på PowerShell-versioner 4 och nedan.</span><span class="sxs-lookup"><span data-stu-id="3f53d-111">Once a module manifest is specified with the CompatiblePSEditions key, it can not be imported on PowerShell versions 4 and below.</span></span>

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

<span data-ttu-id="3f53d-112">När du hämtar en lista över tillgängliga moduler kan du filtrera listan efter PowerShell-utgåva.</span><span class="sxs-lookup"><span data-stu-id="3f53d-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

## <a name="targeting-multiple-editions"></a><span data-ttu-id="3f53d-113">Riktar in sig på flera versioner</span><span class="sxs-lookup"><span data-stu-id="3f53d-113">Targeting multiple editions</span></span>

<span data-ttu-id="3f53d-114">Modulskapare kan publicera en enda modulen riktar in sig på att ena eller båda PowerShell-utgåvor (Desktop och Core).</span><span class="sxs-lookup"><span data-stu-id="3f53d-114">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="3f53d-115">En enda modul fungerar på både Desktop- och Core-utgåvor, i modulen författare har att lägga till nödvändig kod i antingen RootModule eller i modulmanifestet med $PSEdition variabeln.</span><span class="sxs-lookup"><span data-stu-id="3f53d-115">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using $PSEdition variable.</span></span> <span data-ttu-id="3f53d-116">Moduler kan ha två uppsättningar kompilerade DLL: er som både på CoreCLR och FullCLR.</span><span class="sxs-lookup"><span data-stu-id="3f53d-116">Modules can have two sets of compiled DLLs targeting both CoreCLR and FullCLR.</span></span> <span data-ttu-id="3f53d-117">Här följer några av alternativ för att paketera din modul med logik för att läsa in rätt DLL-filer.</span><span class="sxs-lookup"><span data-stu-id="3f53d-117">Here are the couple of options to package your module with logic for loading proper dlls.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="3f53d-118">Alternativ 1: Paketera en modul för flera versioner och flera versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="3f53d-118">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="3f53d-119">Modulen mappinnehåll</span><span class="sxs-lookup"><span data-stu-id="3f53d-119">Module folder contents</span></span>

- <span data-ttu-id="3f53d-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-120">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3f53d-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-121">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3f53d-122">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-122">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="3f53d-123">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="3f53d-123">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="3f53d-124">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3f53d-124">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="3f53d-125">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="3f53d-125">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="3f53d-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-126">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3f53d-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-127">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3f53d-128">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="3f53d-128">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="3f53d-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="3f53d-129">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="3f53d-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-130">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="3f53d-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="3f53d-131">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="3f53d-132">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-132">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="3f53d-133">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-133">Settings\DSC.psd1</span></span>
- <span data-ttu-id="3f53d-134">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-134">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="3f53d-135">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-135">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="3f53d-136">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-136">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="3f53d-137">Innehållet i filen PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="3f53d-137">Contents of PSScriptAnalyzer.psd1 file</span></span>

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

<span data-ttu-id="3f53d-138">Läser in de nödvändiga sammansättningarna beroende på den aktuella utgåvan eller versionen nedan logik.</span><span class="sxs-lookup"><span data-stu-id="3f53d-138">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="3f53d-139">Innehållet i PSScriptAnalyzer.psm1-filen:</span><span class="sxs-lookup"><span data-stu-id="3f53d-139">Contents of PSScriptAnalyzer.psm1 file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls-and-nestedrequired-modules"></a><span data-ttu-id="3f53d-140">Alternativ 2: Använd $PSEdition variabeln i PSD1-fil för att läsa in rätt DLL: er och kapslade/krävs moduler</span><span class="sxs-lookup"><span data-stu-id="3f53d-140">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs and Nested/Required modules</span></span>

<span data-ttu-id="3f53d-141">I PS 5.1 eller senare tillåts $PSEdition global variabel i modulen manifestfilen.</span><span class="sxs-lookup"><span data-stu-id="3f53d-141">In PS 5.1 or newer, $PSEdition global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="3f53d-142">Med den här variabeln kan anger modulägaren villkorlig värden i modulen manifestfilen.</span><span class="sxs-lookup"><span data-stu-id="3f53d-142">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="3f53d-143">$PSEdition variabeln kan refereras i begränsade språkläge eller ett Data-avsnitt.</span><span class="sxs-lookup"><span data-stu-id="3f53d-143">$PSEdition variable can be referenced in restricted language mode or a Data section.</span></span>

> [!NOTE]
> <span data-ttu-id="3f53d-144">När ett modulmanifest anges med CompatiblePSEditions-nyckel eller använder `$PSEdition` variabel, det går inte att importera på lägre versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3f53d-144">Once a module manifest is specified with the CompatiblePSEditions key or uses `$PSEdition` variable, it can not be imported on lower versions of PowerShell.</span></span>

<span data-ttu-id="3f53d-145">Exemplet modulen manifestfilen med CompatiblePSEditions-nyckel</span><span class="sxs-lookup"><span data-stu-id="3f53d-145">Sample module manifest file with CompatiblePSEditions key</span></span>

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

### <a name="module-contents"></a><span data-ttu-id="3f53d-146">Modulen innehållet</span><span class="sxs-lookup"><span data-stu-id="3f53d-146">Module contents</span></span>

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

<span data-ttu-id="3f53d-147">PowerShell-galleriet användare kan hitta listan över moduler som stöds på en viss version av PowerShell med hjälp av taggar PSEdition_Desktop och PSEdition_Core.</span><span class="sxs-lookup"><span data-stu-id="3f53d-147">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags PSEdition_Desktop and PSEdition_Core.</span></span>

<span data-ttu-id="3f53d-148">Moduler utan PSEdition_Desktop och PSEdition_Core taggar anses fungera på PowerShell Desktop-versioner.</span><span class="sxs-lookup"><span data-stu-id="3f53d-148">Modules without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="3f53d-149">Mer information</span><span class="sxs-lookup"><span data-stu-id="3f53d-149">More details</span></span>

[<span data-ttu-id="3f53d-150">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="3f53d-150">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="3f53d-151">Stöd för PSEditions på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="3f53d-151">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="3f53d-152">Uppdatera modulmanifestet</span><span class="sxs-lookup"><span data-stu-id="3f53d-152">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="3f53d-153">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="3f53d-153">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
