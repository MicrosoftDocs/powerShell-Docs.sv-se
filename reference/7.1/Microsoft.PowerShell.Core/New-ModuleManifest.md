---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 11/02/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-modulemanifest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ModuleManifest
ms.openlocfilehash: 21d9f21414eec761fbab77ffcc35a9f57706263a
ms.sourcegitcommit: 04faa7dc1122bce839295d4891bd8b2f0ecb06ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/05/2021
ms.locfileid: "97879277"
---
# <span data-ttu-id="bcf2e-103">New-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="bcf2e-103">New-ModuleManifest</span></span>

## <span data-ttu-id="bcf2e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bcf2e-104">SYNOPSIS</span></span>
<span data-ttu-id="bcf2e-105">Skapar ett nytt modul manifest.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-105">Creates a new module manifest.</span></span>

## <span data-ttu-id="bcf2e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bcf2e-106">SYNTAX</span></span>

### <span data-ttu-id="bcf2e-107">Alla</span><span class="sxs-lookup"><span data-stu-id="bcf2e-107">All</span></span>

```
New-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-PowerShellVersion <Version>] [-CLRVersion <Version>] [-DotNetFrameworkVersion <Version>]
 [-PowerShellHostName <String>] [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>]
 [-TypesToProcess <String[]>] [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>]
 [-RequiredAssemblies <String[]>] [-FileList <String[]>] [-ModuleList <Object[]>]
 [-FunctionsToExport <String[]>] [-AliasesToExport <String[]>] [-VariablesToExport <String[]>]
 [-CmdletsToExport <String[]>] [-DscResourcesToExport <String[]>] [-CompatiblePSEditions <String[]>]
 [-PrivateData <Object>] [-Tags <String[]>] [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ReleaseNotes <String>] [-Prerelease <String>] [-RequireLicenseAcceptance]
 [-ExternalModuleDependencies <String[]>] [-HelpInfoUri <String>] [-PassThru]
 [-DefaultCommandPrefix <String>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="bcf2e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bcf2e-108">DESCRIPTION</span></span>

<span data-ttu-id="bcf2e-109">`New-ModuleManifest`Cmdleten skapar en ny modul manifest `.psd1` fil (), fyller i sina värden och sparar manifest filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-109">The `New-ModuleManifest` cmdlet creates a new module manifest (`.psd1`) file, populates its values, and saves the manifest file in the specified path.</span></span>

<span data-ttu-id="bcf2e-110">Module-författare kan använda denna cmdlet för att skapa ett manifest för sin modul.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-110">Module authors can use this cmdlet to create a manifest for their module.</span></span> <span data-ttu-id="bcf2e-111">Ett modul manifest är en `.psd1` fil som innehåller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-111">A module manifest is a `.psd1` file that contains a hash table.</span></span> <span data-ttu-id="bcf2e-112">Nycklar och värden i hash-tabellen beskriver modulens innehåll och attribut, definierar förutsättningarna och avgör hur komponenterna bearbetas.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-112">The keys and values in the hash table describe the contents and attributes of the module, define the prerequisites, and determine how the components are processed.</span></span> <span data-ttu-id="bcf2e-113">Manifest krävs inte för en modul.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-113">Manifests aren't required for a module.</span></span>

<span data-ttu-id="bcf2e-114">`New-ModuleManifest` skapar ett manifest som innehåller alla ofta använda manifest nycklar, så att du kan använda standardutdata som en manifest mall.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-114">`New-ModuleManifest` creates a manifest that includes all the commonly used manifest keys, so you can use the default output as a manifest template.</span></span> <span data-ttu-id="bcf2e-115">Om du vill lägga till eller ändra värden eller lägga till Modulnamn som denna cmdlet inte lägger till, öppnar du den resulterande filen i en text redigerare.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-115">To add or change values, or to add module keys that this cmdlet doesn't add, open the resulting file in a text editor.</span></span>

<span data-ttu-id="bcf2e-116">Varje parameter, förutom **sökväg** och **Passthru**, skapar en modul manifest nyckel och dess värde.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-116">Each parameter, except for **Path** and **PassThru**, creates a module manifest key and its value.</span></span>
<span data-ttu-id="bcf2e-117">I ett modul manifest krävs bara nyckeln **ModuleVersion** .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-117">In a module manifest, only the **ModuleVersion** key is required.</span></span> <span data-ttu-id="bcf2e-118">Om du utelämnar en parameter från kommandot, om du inte anger någon parameter från kommandot, `New-ModuleManifest` skapas en kommentar sträng för det associerade värdet som inte har någon påverkan.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-118">Unless specified in the parameter description, if you omit a parameter from the command, `New-ModuleManifest` creates a comment string for the associated value that has no effect.</span></span>

<span data-ttu-id="bcf2e-119">I PowerShell 2,0 `New-ModuleManifest` uppmanas du att ange värdena för de vanligaste parametrarna som inte anges i kommandot, förutom de parameter värden som krävs.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-119">In PowerShell 2.0, `New-ModuleManifest` prompts you for the values of commonly used parameters that aren't specified in the command, in addition to required parameter values.</span></span> <span data-ttu-id="bcf2e-120">Från och med PowerShell 3,0 visas `New-ModuleManifest` endast när obligatoriska parameter värden inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-120">Beginning in PowerShell 3.0, `New-ModuleManifest` prompts only when required parameter values aren't specified.</span></span>

<span data-ttu-id="bcf2e-121">Om du planerar att publicera modulen i PowerShell-galleriet måste manifestet innehålla värden för vissa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-121">If you are planning to publish your module in the PowerShell Gallery, the manifest must contain values for certain properties.</span></span> <span data-ttu-id="bcf2e-122">Mer information finns i [obligatoriska metadata för objekt som publicerats till PowerShell-galleriet](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) i Galleri dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-122">For more information, see [Required metadata for items published to the PowerShell Gallery](/powershell/scripting/gallery/how-to/publishing-packages/publishing-a-package#required-metadata-for-items-published-to-the-powershell-gallery) in the Gallery documentation.</span></span>

## <span data-ttu-id="bcf2e-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bcf2e-123">EXAMPLES</span></span>

### <span data-ttu-id="bcf2e-124">Exempel 1 – Skapa ett nytt modul manifest</span><span class="sxs-lookup"><span data-stu-id="bcf2e-124">Example 1 - Create a new module manifest</span></span>

<span data-ttu-id="bcf2e-125">Det här exemplet skapar ett nytt modul-manifest i filen som anges av parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-125">This example creates a new module manifest in the file that is specified by the **Path** parameter.</span></span>
<span data-ttu-id="bcf2e-126">Parametern **Passthru** skickar utdata till pipelinen och till filen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-126">The **PassThru** parameter sends the output to the pipeline and to the file.</span></span>

<span data-ttu-id="bcf2e-127">Utdata visar standardvärden för alla nycklar i manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-127">The output shows the default values of all keys in the manifest.</span></span>

```powershell
New-ModuleManifest -Path C:\ps-test\Test-Module\Test-Module.psd1 -PassThru
```

```Output
#
# Module manifest for module 'Test-Module'
#
# Generated by: ContosoAdmin
#
# Generated on: 7/12/2019
#

@{

# Script module or binary module file associated with this manifest.
# RootModule = ''

# Version number of this module.
ModuleVersion = '0.0.1'

# Supported PSEditions
# CompatiblePSEditions = @()

# ID used to uniquely identify this module
GUID = 'e1826c6e-c420-4eef-9ac8-185e3669ca6a'

# Author of this module
Author = 'ContosoAdmin'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) ContosoAdmin. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the PowerShell engine required by this module
# PowerShellVersion = ''

# Name of the PowerShell host required by this module
# PowerShellHostName = ''

# Minimum version of the PowerShell host required by this module
# PowerShellHostVersion = ''

# Minimum version of Microsoft .NET Framework required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# DotNetFrameworkVersion = ''

# Minimum version of the common language runtime (CLR) required by this module. This prerequisite is valid for the PowerShell Desktop edition only.
# CLRVersion = ''

# Processor architecture (None, X86, Amd64) required by this module
# ProcessorArchitecture = ''

# Modules that must be imported into the global environment prior to importing this module
# RequiredModules = @()

# Assemblies that must be loaded prior to importing this module
# RequiredAssemblies = @()

# Script files (.ps1) that are run in the caller's environment prior to importing this module.
# ScriptsToProcess = @()

# Type files (.ps1xml) to be loaded when importing this module
# TypesToProcess = @()

# Format files (.ps1xml) to be loaded when importing this module
# FormatsToProcess = @()

# Modules to import as nested modules of the module specified in RootModule/ModuleToProcess
# NestedModules = @()

# Functions to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no functions to export.
FunctionsToExport = @()

# Cmdlets to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no cmdlets to export.
CmdletsToExport = @()

# Variables to export from this module
VariablesToExport = '*'

# Aliases to export from this module, for best performance, do not use wildcards and do not delete the entry, use an empty array if there are no aliases to export.
AliasesToExport = @()

# DSC resources to export from this module
# DscResourcesToExport = @()

# List of all modules packaged with this module
# ModuleList = @()

# List of all files packaged with this module
# FileList = @()

# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{

    PSData = @{

        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # Prerelease string of this module
        # Prerelease = ''

        # Flag to indicate whether the module requires explicit user acceptance for install/update/save
        # RequireLicenseAcceptance = $false

        # External dependent modules of this module
        # ExternalModuleDependencies = @()

    } # End of PSData hashtable

} # End of PrivateData hashtable

# HelpInfo URI of this module
# HelpInfoURI = ''

# Default prefix for commands exported from this module. Override the default prefix using Import-Module -Prefix.
# DefaultCommandPrefix = ''

}
```

### <span data-ttu-id="bcf2e-128">Exempel 2 – Skapa ett nytt manifest med förkonfigurerade inställningar</span><span class="sxs-lookup"><span data-stu-id="bcf2e-128">Example 2 - Create a new manifest with some prepopulated settings</span></span>

<span data-ttu-id="bcf2e-129">Det här exemplet skapar ett nytt modul manifest.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-129">This example creates a new module manifest.</span></span> <span data-ttu-id="bcf2e-130">Den använder parametrarna **PowerShellVersion** och **AliasesToExport** för att lägga till värden i motsvarande manifest nycklar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-130">It uses the **PowerShellVersion** and **AliasesToExport** parameters to add values to the corresponding manifest keys.</span></span>

```powershell
New-ModuleManifest -PowerShellVersion 1.0 -AliasesToExport JKBC, DRC, TAC -Path C:\ps-test\ManifestTest.psd1
```

### <span data-ttu-id="bcf2e-131">Exempel 3 – skapa ett manifest som kräver andra moduler</span><span class="sxs-lookup"><span data-stu-id="bcf2e-131">Example 3 - Create a manifest that requires other modules</span></span>

<span data-ttu-id="bcf2e-132">I det här exemplet används ett sträng format för att ange namnet på **BitsTransfer** -modulen och hash-tabellens format för att ange namn, **GUID** och en version av **PSScheduledJob** -modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-132">This example uses a string format to specify the name of the **BitsTransfer** module and the hash table format to specify the name, a **GUID**, and a version of the **PSScheduledJob** module.</span></span>

```powershell
$moduleSettings = @{
  RequiredModules = ("BitsTransfer", @{
    ModuleName="PSScheduledJob"
    ModuleVersion="1.0.0.0";
    GUID="50cdb55f-5ab7-489f-9e94-4ec21ff51e59"
  })
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="bcf2e-133">Det här exemplet visar hur du använder tabell formaten sträng och hash för parametern **ModuleList**, **RequiredModules** och **NestedModules** .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-133">This example shows how to use the string and hash table formats of the **ModuleList**, **RequiredModules**, and **NestedModules** parameter.</span></span> <span data-ttu-id="bcf2e-134">Du kan kombinera strängar och hash-tabeller i samma parameter värde.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-134">You can combine strings and hash tables in the same parameter value.</span></span>

### <span data-ttu-id="bcf2e-135">Exempel 4 – skapa ett manifest som stöder uppdaterings bara hjälp</span><span class="sxs-lookup"><span data-stu-id="bcf2e-135">Example 4 - Create a manifest that supports updateable help</span></span>

<span data-ttu-id="bcf2e-136">I det här exemplet används parametern **HelpInfoUri** för att skapa en **HelpInfoUri** -nyckel i modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-136">This example uses the **HelpInfoUri** parameter to create a **HelpInfoUri** key in the module manifest.</span></span> <span data-ttu-id="bcf2e-137">Värdet för parametern och nyckeln måste börja med **http** eller **https**.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-137">The value of the parameter and the key must begin with **http** or **https**.</span></span> <span data-ttu-id="bcf2e-138">Det här värdet anger det uppdaterings bara hjälp systemet där du hittar HelpInfo XML-hjälpfil med uppdaterings information för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-138">This value tells the Updatable Help system where to find the HelpInfo XML updatable help information file for the module.</span></span>

```powershell
$moduleSettings = @{
  HelpInfoUri = 'http://https://go.microsoft.com/fwlink/?LinkID=603'
  Path = 'C:\ps-test\ManifestTest.psd1'
}
New-ModuleManifest @moduleSettings
```

<span data-ttu-id="bcf2e-139">Information om uppdaterbar hjälp finns [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-139">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="bcf2e-140">Information om XML-HelpInfo finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-140">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

### <span data-ttu-id="bcf2e-141">Exempel 5 – hämta information om moduler</span><span class="sxs-lookup"><span data-stu-id="bcf2e-141">Example 5 - Getting module information</span></span>

<span data-ttu-id="bcf2e-142">Det här exemplet visar hur du hämtar konfigurations värden för en modul.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-142">This example shows how to get the configuration values of a module.</span></span> <span data-ttu-id="bcf2e-143">Värdena i modulens manifest visas i egenskaperna för objektet module.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-143">The values in the module manifest are reflected in the values of properties of the module object.</span></span>

<span data-ttu-id="bcf2e-144">`Get-Module`Cmdleten används för att hämta **Microsoft. PowerShell. Diagnostics** -modulen med **list** -parametern.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-144">The `Get-Module` cmdlet is used to get the **Microsoft.PowerShell.Diagnostics** module using the **List** parameter.</span></span> <span data-ttu-id="bcf2e-145">Kommandot skickar modulen till `Format-List` cmdlet: en för att visa alla egenskaper och värden för objektet module.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-145">The command sends the module to the `Format-List` cmdlet to display all properties and values of the module object.</span></span>

```powershell
Get-Module Microsoft.PowerShell.Diagnostics -List | Format-List -Property *
```

```Output
LogPipelineExecutionDetails : False
Name                        : Microsoft.PowerShell.Diagnostics
Path                        : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics\Micro
                              soft.PowerShell.Diagnostics.psd1
Definition                  :
Description                 :
Guid                        : ca046f10-ca64-4740-8ff9-2565dba61a4f
HelpInfoUri                 : https://go.microsoft.com/fwlink/?LinkID=210596
ModuleBase                  : C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Microsoft.PowerShell.Diagnostics
PrivateData                 :
Version                     : 3.0.0.0
ModuleType                  : Manifest
Author                      : Microsoft Corporation
AccessMode                  : ReadWrite
ClrVersion                  : 4.0
CompanyName                 : Microsoft Corporation
Copyright                   : Microsoft Corporation. All rights reserved.
DotNetFrameworkVersion      :
ExportedFunctions           : {}
ExportedCmdlets             : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
ExportedCommands            : {[Get-WinEvent, Get-WinEvent], [Get-Counter, Get-Counter], [Import-Counter,
                              Import-Counter], [Export-Counter, Export-Counter]...}
FileList                    : {}
ModuleList                  : {}
NestedModules               : {}
PowerShellHostName          :
PowerShellHostVersion       :
PowerShellVersion           : 3.0
ProcessorArchitecture       : None
Scripts                     : {}
RequiredAssemblies          : {}
RequiredModules             : {}
RootModule                  :
ExportedVariables           : {}
ExportedAliases             : {}
ExportedWorkflows           : {}
SessionState                :
OnRemove                    :
ExportedFormatFiles         : {C:\Windows\system32\WindowsPowerShell\v1.0\Event.format.ps1xml,
                              C:\Windows\system32\WindowsPowerShell\v1.0\Diagnostics.format.ps1xml}
ExportedTypeFiles           : {C:\Windows\system32\WindowsPowerShell\v1.0\GetEvent.types.ps1xml}
```

## <span data-ttu-id="bcf2e-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bcf2e-146">PARAMETERS</span></span>

### <span data-ttu-id="bcf2e-147">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="bcf2e-147">-AliasesToExport</span></span>

<span data-ttu-id="bcf2e-148">Anger de alias som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-148">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="bcf2e-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-149">Wildcards are permitted.</span></span>

<span data-ttu-id="bcf2e-150">Du kan använda den här parametern för att begränsa de alias som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-150">You can use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="bcf2e-151">Det kan ta bort alias från listan över exporterade alias, men det går inte att lägga till alias i listan.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-151">It can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

<span data-ttu-id="bcf2e-152">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **AliasesToExport** -nyckel med värdet `*` (alla), vilket innebär att alla alias som definierats i modulen exporteras av manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-152">If you omit this parameter, `New-ModuleManifest` creates an **AliasesToExport** key with a value of `*` (all), meaning that all aliases defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bcf2e-153">– Författare</span><span class="sxs-lookup"><span data-stu-id="bcf2e-153">-Author</span></span>

<span data-ttu-id="bcf2e-154">Anger modulens författare.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-154">Specifies the module author.</span></span>

<span data-ttu-id="bcf2e-155">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **författar** nyckel med namnet på den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-155">If you omit this parameter, `New-ModuleManifest` creates an **Author** key with the name of the current user.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Name of the current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-156">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="bcf2e-156">-CmdletsToExport</span></span>

<span data-ttu-id="bcf2e-157">Anger de cmdletar som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-157">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="bcf2e-158">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-158">Wildcards are permitted.</span></span>

<span data-ttu-id="bcf2e-159">Du kan använda den här parametern för att begränsa de cmdletar som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-159">You can use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="bcf2e-160">Den kan ta bort cmdletar från listan över exporterade cmdlets, men det går inte att lägga till cmdletar i listan.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-160">It can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

<span data-ttu-id="bcf2e-161">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **CmdletsToExport** -nyckel med värdet `*` (alla), vilket innebär att alla cmdletar som definierats i modulen exporteras av manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-161">If you omit this parameter, `New-ModuleManifest` creates a **CmdletsToExport** key with a value of `*` (all), meaning that all cmdlets defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bcf2e-162">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="bcf2e-162">-CompanyName</span></span>

<span data-ttu-id="bcf2e-163">Identifierar företaget eller leverantören som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-163">Identifies the company or vendor who created the module.</span></span>

<span data-ttu-id="bcf2e-164">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **företags namn** nyckel med värdet "okänd".</span><span class="sxs-lookup"><span data-stu-id="bcf2e-164">If you omit this parameter, `New-ModuleManifest` creates a **CompanyName** key with a value of "Unknown".</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: "Unknown"
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-165">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="bcf2e-165">-CompatiblePSEditions</span></span>

<span data-ttu-id="bcf2e-166">Anger modulens kompatibla PSEditions.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-166">Specifies the module's compatible PSEditions.</span></span> <span data-ttu-id="bcf2e-167">Information om PSEdition finns i [moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-167">For information about PSEdition, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-168">– Copyright</span><span class="sxs-lookup"><span data-stu-id="bcf2e-168">-Copyright</span></span>

<span data-ttu-id="bcf2e-169">Anger en Copyright-instruktion för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-169">Specifies a copyright statement for the module.</span></span>

<span data-ttu-id="bcf2e-170">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **Copyright** -nyckel med värdet `(c) <year> <username>. All rights reserved.` där `<year>` är det aktuella året och `<username>` är värdet för **författar** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-170">If you omit this parameter, `New-ModuleManifest` creates a **Copyright** key with a value of `(c) <year> <username>. All rights reserved.` where `<year>` is the current year and `<username>` is the value of the **Author** key.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: (c) <year> <username>. All rights reserved.
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-171">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="bcf2e-171">-DefaultCommandPrefix</span></span>

<span data-ttu-id="bcf2e-172">Anger ett prefix som är anpassningsprefix till substantiven för alla kommandon i modulen när de importeras till en session.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-172">Specifies a prefix that is prepended to the nouns of all commands in the module when they're imported into a session.</span></span> <span data-ttu-id="bcf2e-173">Ange en prefixlängd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-173">Enter a prefix string.</span></span> <span data-ttu-id="bcf2e-174">Prefix förhindrar att kommando namns konflikter i en användares session.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-174">Prefixes prevent command name conflicts in a user's session.</span></span>

<span data-ttu-id="bcf2e-175">Module-användare kan åsidosätta det här prefixet genom att ange parametern **prefix** för `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-175">Module users can override this prefix by specifying the **Prefix** parameter of the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="bcf2e-176">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-176">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-177">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bcf2e-177">-Description</span></span>

<span data-ttu-id="bcf2e-178">Beskriver innehållet i modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-178">Describes the contents of the module.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-179">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="bcf2e-179">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="bcf2e-180">Anger den lägsta version av Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-180">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-181">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="bcf2e-181">-DscResourcesToExport</span></span>

<span data-ttu-id="bcf2e-182">Anger de DSC-resurser (Desired State Configuration) som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-182">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="bcf2e-183">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-183">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bcf2e-184">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="bcf2e-184">-ExternalModuleDependencies</span></span>

<span data-ttu-id="bcf2e-185">En lista över externa moduler som den här modulen är beroende av.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-185">A list of external modules that this module is depends on.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-186">– FileList</span><span class="sxs-lookup"><span data-stu-id="bcf2e-186">-FileList</span></span>

<span data-ttu-id="bcf2e-187">Anger alla objekt som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-187">Specifies all items that are included in the module.</span></span>

<span data-ttu-id="bcf2e-188">Den här nyckeln är utformad för att fungera som en modul.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-188">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="bcf2e-189">Filerna som anges i nyckeln inkluderas när modulen publiceras, men inga funktioner exporteras automatiskt.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-189">The files listed in the key are included when the module is published, but any functions aren't automatically exported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-190">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="bcf2e-190">-FormatsToProcess</span></span>

<span data-ttu-id="bcf2e-191">Anger de formateringsattribut ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-191">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="bcf2e-192">När du importerar en modul kör PowerShell `Update-FormatData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-192">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="bcf2e-193">Eftersom filer som inte är begränsade påverkar formateringen alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-193">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-194">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="bcf2e-194">-FunctionsToExport</span></span>

<span data-ttu-id="bcf2e-195">Anger de funktioner som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-195">Specifies the functions that the module exports.</span></span> <span data-ttu-id="bcf2e-196">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-196">Wildcards are permitted.</span></span>

<span data-ttu-id="bcf2e-197">Du kan använda den här parametern för att begränsa de funktioner som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-197">You can use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="bcf2e-198">Den kan ta bort funktioner från listan över exporterade alias, men det går inte att lägga till funktioner i listan.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-198">It can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

<span data-ttu-id="bcf2e-199">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **FunctionsToExport** -nyckel med värdet `*` (alla), vilket innebär att alla funktioner som definierats i modulen exporteras av manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-199">If you omit this parameter, `New-ModuleManifest` creates an **FunctionsToExport** key with a value of `*` (all), meaning that all functions defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bcf2e-200">-GUID</span><span class="sxs-lookup"><span data-stu-id="bcf2e-200">-Guid</span></span>

<span data-ttu-id="bcf2e-201">Anger en unik identifierare för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-201">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="bcf2e-202">**GUID** kan användas för att skilja mellan moduler med samma namn.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-202">The **GUID** can be used to distinguish among modules with the same name.</span></span>

<span data-ttu-id="bcf2e-203">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **GUID** -nyckel i manifestet och genererar ett **GUID** för värdet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-203">If you omit this parameter, `New-ModuleManifest` creates a **GUID** key in the manifest and generates a **GUID** for the value.</span></span>

<span data-ttu-id="bcf2e-204">Om du vill skapa ett nytt **GUID** i PowerShell skriver du `[guid]::NewGuid()` .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-204">To create a new **GUID** in PowerShell, type `[guid]::NewGuid()`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A GUID generated for the module
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-205">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="bcf2e-205">-HelpInfoUri</span></span>

<span data-ttu-id="bcf2e-206">Anger Internet adressen för HelpInfo XML-filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-206">Specifies the internet address of the HelpInfo XML file for the module.</span></span> <span data-ttu-id="bcf2e-207">Ange en Uniform Resource Identifier (URI) som börjar med **http** eller **https**.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-207">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="bcf2e-208">XML-filen HelpInfo stöder den uppdaterbara hjälp funktionen som introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-208">The HelpInfo XML file supports the Updatable Help feature that was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="bcf2e-209">Den innehåller information om platsen för nedladdnings bara hjälpfiler för modulen och versions numren för de senaste hjälpfilerna för varje språk som stöds.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-209">It contains information about the location of downloadable help files for the module and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="bcf2e-210">Information om uppdaterbar hjälp finns [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-210">For information about Updatable Help, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="bcf2e-211">Information om XML-HelpInfo finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-211">For information about the HelpInfo XML file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="bcf2e-212">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-212">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-213">– IconUri</span><span class="sxs-lookup"><span data-stu-id="bcf2e-213">-IconUri</span></span>

<span data-ttu-id="bcf2e-214">Anger URL-adressen till en ikon för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-214">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="bcf2e-215">Den angivna ikonen visas på Galleri webb sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-215">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-216">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="bcf2e-216">-LicenseUri</span></span>

<span data-ttu-id="bcf2e-217">Anger URL: en för licens villkoren för modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-217">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-218">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="bcf2e-218">-ModuleList</span></span>

<span data-ttu-id="bcf2e-219">Visar alla moduler som ingår i den här modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-219">Lists all modules that are included in this module.</span></span>

<span data-ttu-id="bcf2e-220">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-220">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="bcf2e-221">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-221">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="bcf2e-222">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-222">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="bcf2e-223">Den här nyckeln är utformad för att fungera som en modul.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-223">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="bcf2e-224">Modulerna som anges i värdet för den här nyckeln bearbetas inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-224">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-225">– ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="bcf2e-225">-ModuleVersion</span></span>

<span data-ttu-id="bcf2e-226">Anger modulens version.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-226">Specifies the module's version.</span></span>

<span data-ttu-id="bcf2e-227">Den här parametern är inte obligatorisk, men en **ModuleVersion** -nyckel krävs i manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-227">This parameter isn't required, but a **ModuleVersion** key is required in the manifest.</span></span> <span data-ttu-id="bcf2e-228">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **ModuleVersion** -nyckel med värdet 1,0.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-228">If you omit this parameter, `New-ModuleManifest` creates a **ModuleVersion** key with a value of 1.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1.0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-229">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="bcf2e-229">-NestedModules</span></span>

<span data-ttu-id="bcf2e-230">Anger skript moduler ( `.psm1` ) och binära moduler ( `.dll` ) som importeras till modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-230">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="bcf2e-231">Filerna i **NestedModules** -nyckeln körs i den ordning som de är listade i värdet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-231">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="bcf2e-232">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-232">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="bcf2e-233">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-233">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="bcf2e-234">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-234">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="bcf2e-235">Kapslade moduler innehåller vanligt vis kommandon som rot modulen behöver för intern bearbetning.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-235">Typically, nested modules contain commands that the root module needs for its internal processing.</span></span>
<span data-ttu-id="bcf2e-236">Som standard exporteras kommandon i kapslade moduler från modulens sessionstillstånd till anroparens sessionstillstånd, men modulen root kan begränsa vilka kommandon som exporteras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-236">By default, the commands in nested modules are exported from the module's session state into the caller's session state, but the root module can restrict the commands that it exports.</span></span> <span data-ttu-id="bcf2e-237">Till exempel genom att använda ett `Export-ModuleMember` kommando.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-237">For example, by using an `Export-ModuleMember` command.</span></span>

<span data-ttu-id="bcf2e-238">Kapslade moduler i sessionens sessionstillstånd är tillgängliga för modulen root, men de returneras inte av ett `Get-Module` kommando i anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-238">Nested modules in the module session state are available to the root module, but they aren't returned by a `Get-Module` command in the caller's session state.</span></span>

<span data-ttu-id="bcf2e-239">Skript ( `.ps1` ) som anges i **NestedModules** -nyckeln körs i modulens sessionstillstånd, inte i anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-239">Scripts (`.ps1`) that are listed in the **NestedModules** key are run in the module's session state, not in the caller's session state.</span></span> <span data-ttu-id="bcf2e-240">Om du vill köra ett skript i anroparens sessionstillstånd, visar du skript filens namn i värdet för nyckeln **ScriptsToProcess** i manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-240">To run a script in the caller's session state, list the script file name in the value of the **ScriptsToProcess** key in the manifest.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-241">– PassThru</span><span class="sxs-lookup"><span data-stu-id="bcf2e-241">-PassThru</span></span>

<span data-ttu-id="bcf2e-242">Skriver manifestet för den resulterande modulen till-konsolen och skapar en `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-242">Writes the resulting module manifest to the console and creates a `.psd1` file.</span></span> <span data-ttu-id="bcf2e-243">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-243">By default, this cmdlet doesn't generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-244">-Path</span><span class="sxs-lookup"><span data-stu-id="bcf2e-244">-Path</span></span>

<span data-ttu-id="bcf2e-245">Anger sökvägen och fil namnet för det nya modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-245">Specifies the path and file name of the new module manifest.</span></span> <span data-ttu-id="bcf2e-246">Ange en sökväg och ett fil namn med ett `.psd1` fil namns tillägg, till exempel `$pshome\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-246">Enter a path and file name with a `.psd1` file name extension, such as `$pshome\Modules\MyModule\MyModule.psd1`.</span></span> <span data-ttu-id="bcf2e-247">Parametern **Path** måste anges.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-247">The **Path** parameter is required.</span></span>

<span data-ttu-id="bcf2e-248">Om du anger sökvägen till en befintlig fil `New-ModuleManifest` ersätts filen utan varning om inte filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-248">If you specify the path to an existing file, `New-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="bcf2e-249">Manifestet ska finnas i modulens katalog och manifest filens namn ska vara samma som modulens katalog namn, men med ett `.psd1` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-249">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` file name extension.</span></span>

> [!NOTE]
> <span data-ttu-id="bcf2e-250">Du kan inte använda variabler, t `$PSHOME` . ex. eller `$HOME` , som svar på en prompt för värdet för en **Sök vägs** parameter.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-250">You cannot use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="bcf2e-251">Om du vill använda en variabel inkluderar du parametern **Path** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-251">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-252">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="bcf2e-252">-PowerShellHostName</span></span>

<span data-ttu-id="bcf2e-253">Anger namnet på PowerShell-värdservern som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-253">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="bcf2e-254">Ange namnet på värd programmet, till exempel **Windows PowerShell ISE värd** eller **ConsoleHost**.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-254">Enter the name of the host program, such as **Windows PowerShell ISE Host** or **ConsoleHost**.</span></span> <span data-ttu-id="bcf2e-255">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-255">Wildcards aren't permitted.</span></span>

<span data-ttu-id="bcf2e-256">Om du vill hitta namnet på ett värd program skriver du i programmet `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-256">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-257">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="bcf2e-257">-PowerShellHostVersion</span></span>

<span data-ttu-id="bcf2e-258">Anger den lägsta versionen av PowerShell-värd programmet som fungerar med modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-258">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="bcf2e-259">Ange ett versions nummer, till exempel 1,1.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-259">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-260">– PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="bcf2e-260">-PowerShellVersion</span></span>

<span data-ttu-id="bcf2e-261">Anger den lägsta version av PowerShell som fungerar med den här modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-261">Specifies the minimum version of PowerShell that works with this module.</span></span> <span data-ttu-id="bcf2e-262">Du kan till exempel ange 1,0, 2,0 eller 3,0 som parameter värde.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-262">For example, you can enter 1.0, 2.0, or 3.0 as the parameter's value.</span></span> <span data-ttu-id="bcf2e-263">Det måste vara i formatet X. X.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-263">It must be in an X.X format.</span></span> <span data-ttu-id="bcf2e-264">Om du till exempel skickar `5` , kommer PowerShell att utlösa ett fel.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-264">For example, if you submit `5`, PowerShell will throw an error.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-265">-För hands version</span><span class="sxs-lookup"><span data-stu-id="bcf2e-265">-Prerelease</span></span>

<span data-ttu-id="bcf2e-266">För hands versions sträng för den här modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-266">Prerelease string of this module.</span></span> <span data-ttu-id="bcf2e-267">Om du lägger till en för hands versions sträng identifieras modulen som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-267">Adding a Prerelease string identifies the module as a prerelease version.</span></span> <span data-ttu-id="bcf2e-268">När modulen publiceras till PowerShell-galleriet används dessa data för att identifiera för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-268">When the module is published to the PowerShell Gallery, this data is used to identify prerelease packages.</span></span> <span data-ttu-id="bcf2e-269">För att hämta för hands paket från galleriet måste du använda parametern **AllowPrerelease** med PowerShellGet-kommandona,, `Find-Module` `Install-Module` `Update-Module` och `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-269">To acquire prerelease packages from the Gallery, you must use the **AllowPrerelease** parameter with the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-270">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="bcf2e-270">-PrivateData</span></span>

<span data-ttu-id="bcf2e-271">Anger data som skickas till modulen när den importeras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-271">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-272">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="bcf2e-272">-ProcessorArchitecture</span></span>

<span data-ttu-id="bcf2e-273">Anger den processor arkitektur som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-273">Specifies the processor architecture that the module requires.</span></span> <span data-ttu-id="bcf2e-274">Giltiga värden är x86, AMD64, IA64, MSIL och None (okänd eller ospecificerad).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-274">Valid values are x86, AMD64, IA64, MSIL, and None (unknown or unspecified).</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-275">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="bcf2e-275">-ProjectUri</span></span>

<span data-ttu-id="bcf2e-276">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-276">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-277">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="bcf2e-277">-ReleaseNotes</span></span>

<span data-ttu-id="bcf2e-278">Anger viktig information.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-278">Specifies release notes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-279">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="bcf2e-279">-RequiredAssemblies</span></span>

<span data-ttu-id="bcf2e-280">Anger de Assembly ( `.dll` )-filer som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-280">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="bcf2e-281">Ange sammansättnings fil namnen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-281">Enter the assembly file names.</span></span>
<span data-ttu-id="bcf2e-282">PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-282">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="bcf2e-283">Använd den här parametern för att visa en lista över alla sammansättningar som modulen kräver, inklusive sammansättningar som måste läsas in för att uppdatera all formatering eller skriva filer som listas i **FormatsToProcess** -eller **TypesToProcess** -nycklarna, även om dessa sammansättningar också visas som binära moduler i **NestedModules** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-283">Use this parameter to list all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-284">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="bcf2e-284">-RequiredModules</span></span>

<span data-ttu-id="bcf2e-285">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-285">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="bcf2e-286">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-286">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="bcf2e-287">Om de moduler som krävs inte är tillgängliga, `Import-Module` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-287">If the required modules aren't available, the `Import-Module` command fails.</span></span>

<span data-ttu-id="bcf2e-288">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-288">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="bcf2e-289">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-289">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="bcf2e-290">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-290">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="bcf2e-291">I PowerShell 2,0 `Import-Module` importerar de nödvändiga modulerna automatiskt.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-291">In PowerShell 2.0, `Import-Module` doesn't import required modules automatically.</span></span> <span data-ttu-id="bcf2e-292">Den verifierar bara att de nödvändiga modulerna är i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-292">It just verifies that the required modules are in the global session state.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-293">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="bcf2e-293">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="bcf2e-294">Flagga för att ange om modulen kräver explicit användar godkännande för installation, uppdatering, orsave.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-294">Flag to indicate whether the module requires explicit user acceptance for install, update, orsave.</span></span>

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

### <span data-ttu-id="bcf2e-295">-RootModule</span><span class="sxs-lookup"><span data-stu-id="bcf2e-295">-RootModule</span></span>

<span data-ttu-id="bcf2e-296">Anger modulens primära eller rot fil.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-296">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="bcf2e-297">Ange fil namnet för ett skript ( `.ps1` ), en skriptbaserad modul ( `.psm1` ), ett modul manifest ( `.psd1` ), en sammansättning ( `.dll` ), en XML-fil () för cmdlet-definition ( `.cdxml` ) eller ett arbets flöde ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-297">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest(`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="bcf2e-298">När modulen importeras importeras medlemmar som exporteras från rot-modul filen till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-298">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="bcf2e-299">Om en modul har en manifest fil och ingen rot fil har angetts i **RootModule** -nyckeln blir manifestet den primära filen för modulen och modulen blir en manifest-modul (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-299">If a module has a manifest file and no root file was designated in the **RootModule** key, the manifest becomes the primary file for the module, and the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="bcf2e-300">För att exportera medlemmar från `.psm1` eller `.dll` filer i en modul som har ett manifest, måste namnen på filerna anges i värdena för **RootModule** -eller **NestedModules** -nycklarna i manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-300">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="bcf2e-301">Annars exporteras inte deras medlemmar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-301">Otherwise, their members aren't exported.</span></span>

> [!NOTE]
> <span data-ttu-id="bcf2e-302">I PowerShell 2,0 kallades den här nyckeln för **ModuleToProcess**.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-302">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span> <span data-ttu-id="bcf2e-303">Du kan använda **RootModule** -parameter namnet eller dess **ModuleToProcess** -alias.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-303">You can use the **RootModule** parameter name or its **ModuleToProcess** alias.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: ModuleToProcess

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-304">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="bcf2e-304">-ScriptsToProcess</span></span>

<span data-ttu-id="bcf2e-305">Anger skript ( `.ps1` )-filer som körs i anroparens sessionstillstånd när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-305">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="bcf2e-306">Du kan använda dessa skript för att förbereda en miljö, precis som du kan använda ett inloggnings skript.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-306">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="bcf2e-307">Använd nyckeln **NestedModules** för att ange skript som körs i modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-307">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-308">– Taggar</span><span class="sxs-lookup"><span data-stu-id="bcf2e-308">-Tags</span></span>

<span data-ttu-id="bcf2e-309">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-309">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-310">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="bcf2e-310">-TypesToProcess</span></span>

<span data-ttu-id="bcf2e-311">Anger de typ filer ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-311">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="bcf2e-312">När du importerar modulen kör PowerShell `Update-TypeData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-312">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="bcf2e-313">Eftersom filtypen inte är begränsad, påverkar de alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-313">Because type files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-314">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="bcf2e-314">-VariablesToExport</span></span>

<span data-ttu-id="bcf2e-315">Anger de variabler som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-315">Specifies the variables that the module exports.</span></span> <span data-ttu-id="bcf2e-316">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-316">Wildcards are permitted.</span></span>

<span data-ttu-id="bcf2e-317">Du kan använda den här parametern för att begränsa de variabler som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-317">You can use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="bcf2e-318">Den kan ta bort variabler från listan över exporterade variabler, men det går inte att lägga till variabler i listan.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-318">It can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

<span data-ttu-id="bcf2e-319">Om du utelämnar den här parametern `New-ModuleManifest` skapar en **VariablesToExport** -nyckel med värdet `*` (alla), vilket innebär att alla variabler som definierats i modulen exporteras av manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-319">If you omit this parameter, `New-ModuleManifest` creates a **VariablesToExport** key with a value of `*` (all), meaning that all variables defined in the module are exported by the manifest.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: * (all)
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bcf2e-320">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bcf2e-320">-Confirm</span></span>

<span data-ttu-id="bcf2e-321">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-321">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bcf2e-322">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bcf2e-322">-WhatIf</span></span>

<span data-ttu-id="bcf2e-323">Visar vad som händer om `New-ModuleManifest` körs.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-323">Shows what would happen if `New-ModuleManifest` runs.</span></span> <span data-ttu-id="bcf2e-324">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-324">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="bcf2e-325">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="bcf2e-325">-ClrVersion</span></span>

<span data-ttu-id="bcf2e-326">Anger den lägsta versionen av CLR (Common Language Runtime) för Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-326">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bcf2e-327">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bcf2e-327">CommonParameters</span></span>
<span data-ttu-id="bcf2e-328">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-328">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bcf2e-329">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bcf2e-329">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bcf2e-330">INDATA</span><span class="sxs-lookup"><span data-stu-id="bcf2e-330">INPUTS</span></span>

### <span data-ttu-id="bcf2e-331">Inget</span><span class="sxs-lookup"><span data-stu-id="bcf2e-331">None</span></span>

<span data-ttu-id="bcf2e-332">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-332">You can't pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bcf2e-333">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bcf2e-333">OUTPUTS</span></span>

### <span data-ttu-id="bcf2e-334">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="bcf2e-334">None or System.String</span></span>

<span data-ttu-id="bcf2e-335">Som standard `New-ModuleManifest` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-335">By default, `New-ModuleManifest` doesn't generate any output.</span></span> <span data-ttu-id="bcf2e-336">Men om du använder parametern **Passthru** genereras ett **system. String** -objekt som representerar modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-336">However, if you use the **PassThru** parameter, it generates a **System.String** object representing the module manifest.</span></span>

## <span data-ttu-id="bcf2e-337">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bcf2e-337">NOTES</span></span>

<span data-ttu-id="bcf2e-338">`New-ModuleManifest` Om du kör på Windows-och icke-Windows-plattformar skapas modul manifest ( `.psd1` )-filer som är kodade som **UTF8NoBOM**.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-338">`New-ModuleManifest` running on Windows and non-Windows platforms creates module manifest (`.psd1`) files encoded as **UTF8NoBOM**.</span></span>

<span data-ttu-id="bcf2e-339">Manifest för moduler är vanligt vis valfria.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-339">Module manifests are usually optional.</span></span> <span data-ttu-id="bcf2e-340">Men ett modul manifest krävs för att exportera en sammansättning som är installerad i Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-340">However, a module manifest is required to export an assembly that is installed in the global assembly cache.</span></span>

<span data-ttu-id="bcf2e-341">Om du vill lägga till eller ändra filer i `$pshome\Modules` katalogen startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="bcf2e-341">To add or change files in the `$pshome\Modules` directory, start PowerShell with the **Run as administrator** option.</span></span>

> [!NOTE]
> <span data-ttu-id="bcf2e-342">Från och med PowerShell 6,2 försöker PowerShell läsa in alla DLL-filer som anges i egenskapen **filelist** för modul manifestet.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-342">Beginning in PowerShell 6.2, PowerShell attempts to load all the DLL files listed in **FileList** property of the module manifest.</span></span> <span data-ttu-id="bcf2e-343">Inbyggda dll: er är i **filelist** som inte kan läsas in i processen och felet ignoreras.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-343">Native DLLs is in the **FileList** fail to load in the process and the error is ignored.</span></span> <span data-ttu-id="bcf2e-344">Alla hanterade DLL-filer läses in i processen.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-344">All managed DLLs are loaded in the process.</span></span> <span data-ttu-id="bcf2e-345">Det här beteendet har tagits bort i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-345">This behavior was removed in PowerShell 7.1.</span></span>

<span data-ttu-id="bcf2e-346">I PowerShell 2,0 var många parametrar i `New-ModuleManifest` obligatoriska, trots att de inte krävdes i ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-346">In PowerShell 2.0, many parameters of `New-ModuleManifest` were mandatory, even though they weren't required in a module manifest.</span></span> <span data-ttu-id="bcf2e-347">Från och med PowerShell 3,0 är bara parametern **Path** obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-347">Beginning in PowerShell 3.0, only the **Path** parameter is mandatory.</span></span>

<span data-ttu-id="bcf2e-348">En session är en instans av PowerShell-körnings miljön.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-348">A session is an instance of the PowerShell execution environment.</span></span> <span data-ttu-id="bcf2e-349">En session kan ha ett eller flera sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-349">A session can have one or more session states.</span></span> <span data-ttu-id="bcf2e-350">Som standard har en session endast ett globalt sessionstillstånd, men varje importerad modul har sitt eget sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-350">By default, a session has only a global session state, but each imported module has its own session state.</span></span> <span data-ttu-id="bcf2e-351">Sessionstillstånd gör att kommandona i en modul kan köras utan att det globala sessionstillståndet påverkas.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-351">Session states allow the commands in a module to run without affecting the global session state.</span></span>

<span data-ttu-id="bcf2e-352">Anroparens sessionstillstånd är det sessionstillstånd som en modul importeras till.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-352">The caller's session state is the session state into which a module is imported.</span></span> <span data-ttu-id="bcf2e-353">Normalt refererar det till det globala sessionstillståndet, men när en modul importerar kapslade moduler, är anroparen modulen och anroparens sessionstillstånd är modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="bcf2e-353">Typically, it refers to the global session state, but when a module imports nested modules, the caller is the module and the caller's session state is the module's session state.</span></span>

## <span data-ttu-id="bcf2e-354">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bcf2e-354">RELATED LINKS</span></span>

[<span data-ttu-id="bcf2e-355">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="bcf2e-355">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="bcf2e-356">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="bcf2e-356">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="bcf2e-357">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="bcf2e-357">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="bcf2e-358">Ny modul</span><span class="sxs-lookup"><span data-stu-id="bcf2e-358">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="bcf2e-359">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="bcf2e-359">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="bcf2e-360">Test-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="bcf2e-360">Test-ModuleManifest</span></span>](Test-ModuleManifest.md)

[<span data-ttu-id="bcf2e-361">about_Modules</span><span class="sxs-lookup"><span data-stu-id="bcf2e-361">about_Modules</span></span>](./About/about_Modules.md)
