---
ms.date: 06/10/2020
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Moduler med kompatibla PowerShell-versioner
ms.openlocfilehash: 522493714916e9fd21f67a6e7bc2cfb165041807
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671418"
---
# <a name="modules-with-compatible-powershell-editions"></a><span data-ttu-id="5fd54-103">Moduler med kompatibla PowerShell-versioner</span><span class="sxs-lookup"><span data-stu-id="5fd54-103">Modules with compatible PowerShell Editions</span></span>

<span data-ttu-id="5fd54-104">Från och med version 5,1 är PowerShell tillgängligt i olika versioner, vilket kännetecknar varierande funktions uppsättningar och plattformens kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="5fd54-104">Starting with version 5.1, PowerShell is available in different editions, which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="5fd54-105">**Desktop Edition:** Byggd på .NET Framework gäller för Windows PowerShell v 4.0 och tidigare samt Windows PowerShell 5,1 på Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-versioner.</span><span class="sxs-lookup"><span data-stu-id="5fd54-105">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell v4.0 and below as well as Windows PowerShell 5.1 on Windows Desktop, Windows Server, Windows Server Core and most other Windows editions.</span></span>
- <span data-ttu-id="5fd54-106">**Core-utgåva:** Bygger på .NET Core som gäller för PowerShell Core 6,0 och senare samt Windows PowerShell 5,1 på mindre Windows-versioner som Windows IoT och Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="5fd54-106">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above as well as Windows PowerShell 5.1 on reduced footprint Windows Editions such as Windows IoT and Windows Nanoserver.</span></span>

<span data-ttu-id="5fd54-107">Mer information om PowerShell-versioner finns [about_PowerShell_Editions][].</span><span class="sxs-lookup"><span data-stu-id="5fd54-107">For more information on PowerShell editions, see [about_PowerShell_Editions][].</span></span>

## <a name="declaring-compatible-editions"></a><span data-ttu-id="5fd54-108">Deklarera kompatibla utgåvor</span><span class="sxs-lookup"><span data-stu-id="5fd54-108">Declaring compatible editions</span></span>

<span data-ttu-id="5fd54-109">Modulens författare kan deklarera att deras moduler är kompatibla med en eller flera PowerShell-versioner med hjälp av `CompatiblePSEditions` modulens manifest nyckel.</span><span class="sxs-lookup"><span data-stu-id="5fd54-109">Module authors can declare their modules to be compatible with one or more PowerShell editions using the `CompatiblePSEditions` module manifest key.</span></span> <span data-ttu-id="5fd54-110">Den här nyckeln stöds bara på PowerShell 5.1 eller senare.</span><span class="sxs-lookup"><span data-stu-id="5fd54-110">This key is only supported on PowerShell 5.1 or later.</span></span>

> [!NOTE]
> <span data-ttu-id="5fd54-111">När ett modul-manifest har angetts med `CompatiblePSEditions` nyckeln eller använder `$PSEdition` variabeln, kan den inte importeras på PowerShell v4 eller lägre.</span><span class="sxs-lookup"><span data-stu-id="5fd54-111">Once a module manifest is specified with the `CompatiblePSEditions` key or uses the `$PSEdition` variable, it can not be imported on PowerShell v4 or lower.</span></span>

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

<span data-ttu-id="5fd54-112">När du hämtar en lista över tillgängliga moduler kan du filtrera listan efter PowerShell-utgåva.</span><span class="sxs-lookup"><span data-stu-id="5fd54-112">When getting a list of available modules, you can filter the list by PowerShell edition.</span></span>

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

<span data-ttu-id="5fd54-113">Från och med PowerShell 6 `CompatiblePSEditions` används värdet för att bestämma om en modul är kompatibel när moduler importeras från `$env:windir\System32\WindowsPowerShell\v1.0\Modules` .</span><span class="sxs-lookup"><span data-stu-id="5fd54-113">Beginning in PowerShell 6, the `CompatiblePSEditions` value is used to decide if a module is compatible when modules are imported from `$env:windir\System32\WindowsPowerShell\v1.0\Modules`.</span></span>
<span data-ttu-id="5fd54-114">Detta beteende gäller endast för Windows.</span><span class="sxs-lookup"><span data-stu-id="5fd54-114">This behavior only applies to Windows.</span></span> <span data-ttu-id="5fd54-115">Utanför det här scenariot används värdet bara som metadata.</span><span class="sxs-lookup"><span data-stu-id="5fd54-115">Outside of this scenario, the value is only used as metadata.</span></span>

## <a name="finding-compatible-modules"></a><span data-ttu-id="5fd54-116">Söker efter kompatibla moduler</span><span class="sxs-lookup"><span data-stu-id="5fd54-116">Finding compatible modules</span></span>

<span data-ttu-id="5fd54-117">PowerShell-galleriet användare kan hitta listan över moduler som stöds på en angiven PowerShell-version med hjälp av Taggar **PSEdition_Desktop** och **PSEdition_Core**.</span><span class="sxs-lookup"><span data-stu-id="5fd54-117">PowerShell Gallery users can find the list of modules supported on a specific PowerShell Edition using tags **PSEdition_Desktop** and **PSEdition_Core**.</span></span>

<span data-ttu-id="5fd54-118">Moduler utan **PSEdition_Desktop** -och **PSEdition_Core** -Taggar anses fungera bra på PowerShell Desktop-versioner.</span><span class="sxs-lookup"><span data-stu-id="5fd54-118">Modules without **PSEdition_Desktop** and **PSEdition_Core** tags are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell
# Find modules supported on PowerShell Desktop edition
Find-Module -Tag PSEdition_Desktop

# Find modules supported on PowerShell Core editions
Find-Module -Tag PSEdition_Core
```

## <a name="targeting-multiple-editions"></a><span data-ttu-id="5fd54-119">Rikta in sig på flera utgåvor</span><span class="sxs-lookup"><span data-stu-id="5fd54-119">Targeting multiple editions</span></span>

<span data-ttu-id="5fd54-120">-Modulen författare kan publicera en enskild modul som riktar sig till antingen eller båda PowerShell-versionerna (Desktop och Core).</span><span class="sxs-lookup"><span data-stu-id="5fd54-120">Module authors can publish a single module targeting to either or both PowerShell editions (Desktop and Core).</span></span>

<span data-ttu-id="5fd54-121">En enda modul kan fungera både i Desktop-och Core-versioner, i den här modulen måste författaren lägga till nödvändig logik i antingen RootModule eller i modulens manifest med `$PSEdition` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5fd54-121">A single module can work on both Desktop and Core editions, in that module author has to add required logic in either RootModule or in the module manifest using `$PSEdition` variable.</span></span> <span data-ttu-id="5fd54-122">Moduler kan ha två uppsättningar med kompilerade dll: er riktade till både **CoreCLR** och **FullCLR**.</span><span class="sxs-lookup"><span data-stu-id="5fd54-122">Modules can have two sets of compiled DLLs targeting both **CoreCLR** and **FullCLR**.</span></span> <span data-ttu-id="5fd54-123">Här är förpacknings alternativen med logik för att läsa in rätt DLL-filer.</span><span class="sxs-lookup"><span data-stu-id="5fd54-123">Here are the packaging options with logic for loading proper DLLs.</span></span>

### <a name="option-1-packaging-a-module-for-targeting-multiple-versions-and-multiple-editions-of-powershell"></a><span data-ttu-id="5fd54-124">Alternativ 1: paketera en modul för att rikta in dig på flera versioner och flera utgåvor av PowerShell</span><span class="sxs-lookup"><span data-stu-id="5fd54-124">Option 1: Packaging a module for targeting multiple versions and multiple editions of PowerShell</span></span>

<span data-ttu-id="5fd54-125">Mappinnehåll i moduler</span><span class="sxs-lookup"><span data-stu-id="5fd54-125">Module folder contents</span></span>

- <span data-ttu-id="5fd54-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-126">Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5fd54-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-127">Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5fd54-128">PSScriptAnalyzer.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-128">PSScriptAnalyzer.psd1</span></span>
- <span data-ttu-id="5fd54-129">PSScriptAnalyzer.psm1</span><span class="sxs-lookup"><span data-stu-id="5fd54-129">PSScriptAnalyzer.psm1</span></span>
- <span data-ttu-id="5fd54-130">ScriptAnalyzer.format.ps1xml</span><span class="sxs-lookup"><span data-stu-id="5fd54-130">ScriptAnalyzer.format.ps1xml</span></span>
- <span data-ttu-id="5fd54-131">ScriptAnalyzer.types.ps1xml</span><span class="sxs-lookup"><span data-stu-id="5fd54-131">ScriptAnalyzer.types.ps1xml</span></span>
- <span data-ttu-id="5fd54-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-132">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5fd54-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-133">coreclr\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5fd54-134">en-US\about_PSScriptAnalyzer.help.txt</span><span class="sxs-lookup"><span data-stu-id="5fd54-134">en-US\about_PSScriptAnalyzer.help.txt</span></span>
- <span data-ttu-id="5fd54-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span><span class="sxs-lookup"><span data-stu-id="5fd54-135">en-US\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll-Help.xml</span></span>
- <span data-ttu-id="5fd54-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-136">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.BuiltinRules.dll</span></span>
- <span data-ttu-id="5fd54-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-137">PSv3\Microsoft.Windows.PowerShell.ScriptAnalyzer.dll</span></span>
- <span data-ttu-id="5fd54-138">Settings\CmdletDesign.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-138">Settings\CmdletDesign.psd1</span></span>
- <span data-ttu-id="5fd54-139">Settings\DSC.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-139">Settings\DSC.psd1</span></span>
- <span data-ttu-id="5fd54-140">Settings\ScriptFunctions.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-140">Settings\ScriptFunctions.psd1</span></span>
- <span data-ttu-id="5fd54-141">Settings\ScriptingStyle.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-141">Settings\ScriptingStyle.psd1</span></span>
- <span data-ttu-id="5fd54-142">Settings\ScriptSecurity.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-142">Settings\ScriptSecurity.psd1</span></span>

<span data-ttu-id="5fd54-143">Fil innehåll `PSScriptAnalyzer.psd1`</span><span class="sxs-lookup"><span data-stu-id="5fd54-143">Contents of `PSScriptAnalyzer.psd1` file</span></span>

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

<span data-ttu-id="5fd54-144">Nedan följer logiken inläsning av de nödvändiga sammansättningarna beroende på aktuell version eller version.</span><span class="sxs-lookup"><span data-stu-id="5fd54-144">Below logic loads the required assemblies depending on the current edition or version.</span></span>

<span data-ttu-id="5fd54-145">Fil innehåll `PSScriptAnalyzer.psm1` :</span><span class="sxs-lookup"><span data-stu-id="5fd54-145">Contents of `PSScriptAnalyzer.psm1` file:</span></span>

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

### <a name="option-2-use-psedition-variable-in-the-psd1-file-to-load-the-proper-dlls"></a><span data-ttu-id="5fd54-146">Alternativ 2: Använd $PSEdition variabel i PSD1-filen för att läsa in rätt DLL-filer</span><span class="sxs-lookup"><span data-stu-id="5fd54-146">Option 2: Use $PSEdition variable in the PSD1 file to load the proper DLLs</span></span>

<span data-ttu-id="5fd54-147">I PS 5,1 eller senare `$PSEdition` tillåts global variabel i manifest filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="5fd54-147">In PS 5.1 or newer, `$PSEdition` global variable is allowed in the module manifest file.</span></span> <span data-ttu-id="5fd54-148">Med den här variabeln kan modulen författare ange de villkorliga värdena i manifest filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="5fd54-148">Using this variable, module author can specify the conditional values in the module manifest file.</span></span> <span data-ttu-id="5fd54-149">`$PSEdition` Det går att referera till variabeln i begränsat språk läge eller i ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5fd54-149">`$PSEdition` variable can be referenced in restricted language mode or a Data section.</span></span>

<span data-ttu-id="5fd54-150">Manifest fil för exempel modul med `CompatiblePSEditions` nyckel.</span><span class="sxs-lookup"><span data-stu-id="5fd54-150">Sample module manifest file with `CompatiblePSEditions` key.</span></span>

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

<span data-ttu-id="5fd54-151">Modulens innehåll</span><span class="sxs-lookup"><span data-stu-id="5fd54-151">Module contents</span></span>

- <span data-ttu-id="5fd54-152">ModuleWithEditions\ModuleWithEditions.psd1</span><span class="sxs-lookup"><span data-stu-id="5fd54-152">ModuleWithEditions\ModuleWithEditions.psd1</span></span>
- <span data-ttu-id="5fd54-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-153">ModuleWithEditions\clr\MyFullClrNM1.dll</span></span>
- <span data-ttu-id="5fd54-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-154">ModuleWithEditions\clr\MyFullClrNM2.dll</span></span>
- <span data-ttu-id="5fd54-155">ModuleWithEditions\clr\MyFullClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-155">ModuleWithEditions\clr\MyFullClrRM.dll</span></span>
- <span data-ttu-id="5fd54-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-156">ModuleWithEditions\coreclr\MyCoreClrNM1.dll</span></span>
- <span data-ttu-id="5fd54-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-157">ModuleWithEditions\coreclr\MyCoreClrNM2.dll</span></span>
- <span data-ttu-id="5fd54-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span><span class="sxs-lookup"><span data-stu-id="5fd54-158">ModuleWithEditions\coreclr\MyCoreClrRM.dll</span></span>

## <a name="more-details"></a><span data-ttu-id="5fd54-159">Mer information</span><span class="sxs-lookup"><span data-stu-id="5fd54-159">More details</span></span>

[<span data-ttu-id="5fd54-160">Skript med PSEditions</span><span class="sxs-lookup"><span data-stu-id="5fd54-160">Scripts with PSEditions</span></span>](script-psedition-support.md)

[<span data-ttu-id="5fd54-161">PSEditions-stöd för PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="5fd54-161">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)

[<span data-ttu-id="5fd54-162">Uppdatera modulmanifestet</span><span class="sxs-lookup"><span data-stu-id="5fd54-162">Update module manifest</span></span>](/powershell/module/powershellget/update-modulemanifest)

<span data-ttu-id="5fd54-163">[about_PowerShell_Editions][]</span><span class="sxs-lookup"><span data-stu-id="5fd54-163">[about_PowerShell_Editions][]</span></span>

[about_PowerShell_Editions]: /powershell/module/Microsoft.PowerShell.Core/About/about_PowerShell_Editions
