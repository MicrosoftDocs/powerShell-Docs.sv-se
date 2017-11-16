---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Installera modulen
ms.openlocfilehash: 37e07cd32e7b2fd4a7a8e6cab179aecc3251baf3
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="install-module"></a><span data-ttu-id="f7b3d-103">Installera modulen</span><span class="sxs-lookup"><span data-stu-id="f7b3d-103">Install-Module</span></span>

<span data-ttu-id="f7b3d-104">Installerar PowerShell-moduler från online databaser till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-104">Installs the PowerShell modules from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="f7b3d-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f7b3d-105">Description</span></span>

<span data-ttu-id="f7b3d-106">Installera modulen cmdlet hämtar en eller flera moduler från en online-galleriet, validerar och installerar dem på den lokala datorn till den angivna omfattningen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-106">Install-Module cmdlet downloads one or more modules from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="f7b3d-107">Cmdleten Install-modulen får en eller flera moduler som uppfyller angivna villkor från en online-galleriet, verifierar att sökresultaten är giltig moduler och kopior modulen mappar till installationsplatsen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-107">The Install-Module cmdlet gets one or more modules that meet specified criteria from an online gallery, verifies that search results are valid modules, and copies module folders to the installation location.</span></span>

<span data-ttu-id="f7b3d-108">Om ingen omfattning har definierats, eller när värdet för parametern Scope är AllUsers, installeras modulen %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-108">When no scope is defined, or when the value of the Scope parameter is AllUsers, the module is installed to %systemdrive%:\Program Files\WindowsPowerShell\Modules.</span></span> <span data-ttu-id="f7b3d-109">När värdet för Scope är CurrentUser, installeras modulen $home\Documents\WindowsPowerShell\Modules.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-109">When the value of Scope is CurrentUser, the module is installed to $home\Documents\WindowsPowerShell\Modules.</span></span>

<span data-ttu-id="f7b3d-110">Du kan filtrera resultatet baserat på lägsta och det exakta versioner av angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-110">You can filter your results based on minimum and exact versions of specified modules.</span></span>

- <span data-ttu-id="f7b3d-111">Stöd för sida-vid-sida-version på Windows PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="f7b3d-111">Side-by-side version support on Windows PowerShell 5.0 or newer</span></span>
- <span data-ttu-id="f7b3d-112">Stöd för modulen beroende installation</span><span class="sxs-lookup"><span data-stu-id="f7b3d-112">Module dependency installation support</span></span>
- <span data-ttu-id="f7b3d-113">**Betrodd kommandoprompt:**användaren godkännande krävs för att installera modulerna från en ej betrodd lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-113">**Untrusted prompt:**User acceptance is required for installing the modules from an untrusted repository.</span></span>
- <span data-ttu-id="f7b3d-114">-Force ominstallerar installerad modul</span><span class="sxs-lookup"><span data-stu-id="f7b3d-114">-Force reinstalls the installed module</span></span>
- <span data-ttu-id="f7b3d-115">RequiredVersion installerar den angivna versionen i SxS med befintliga versioner på PowerShell version 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

### <a name="scope"></a><span data-ttu-id="f7b3d-116">Omfång</span><span class="sxs-lookup"><span data-stu-id="f7b3d-116">Scope</span></span>
<span data-ttu-id="f7b3d-117">Anger installationen omfånget för modulen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-117">Specifies the installation scope of the module.</span></span> <span data-ttu-id="f7b3d-118">Godkända värden för den här parametern är: AllUsers och CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-118">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="f7b3d-119">Standard installationen scope är AllUsers.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-119">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="f7b3d-120">AllUsers omfattningen kan moduler installeras på en plats som är tillgänglig för alla användare av datorn, det vill säga ”$env: SystemDrive\Program Files\WindowsPowerShell\Modules”.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-120">The AllUsers scope lets modules be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\Modules".</span></span>

<span data-ttu-id="f7b3d-121">Området CurrentUser kan moduler installeras endast på ”$home\Documents\WindowsPowerShell\Modules”, så att modulen är bara tillgänglig för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-121">The CurrentUser scope lets modules be installed only to "$home\Documents\WindowsPowerShell\Modules", so that the module is available only to the current user.</span></span>

## <a name="notes"></a><span data-ttu-id="f7b3d-122">Obs!</span><span class="sxs-lookup"><span data-stu-id="f7b3d-122">Notes</span></span>

<span data-ttu-id="f7b3d-123">Denna cmdlet körs på Windows PowerShell 3.0 eller senare versioner av Windows PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-123">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="f7b3d-124">Om en installerad modul inte kan importeras (om den inte har en .psm1, .psd1 eller .dll med samma namn i mappen), misslyckas installationen om du lägger till Force-parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-124">If an installed module cannot be imported (that is, if it does not have a .psm1, .psd1, or .dll of the same name within the folder), installation fails unless you add the Force parameter to your command.</span></span>

<span data-ttu-id="f7b3d-125">Om en version av modulen på datorn matchar det angivna värdet för parametern namn, och du har inte lagt till parametern MinimumVersion eller RequiredVersion, fortsätter installera modulen tyst utan att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-125">If a version of the module on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span> <span data-ttu-id="f7b3d-126">Om modulen befintliga överensstämmer inte med värdena i parametern MinimumVersion eller RequiredVersion parametrar har angetts, uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-126">If the MinimumVersion or RequiredVersion parameters are specified, and the existing module does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="f7b3d-127">Vara mer specifika: om versionen av modulen installerad för närvarande är lägre än värdet för parametern MinimumVersion, eller inte lika med värdet för parametern RequiredVersion, ett fel uppstår.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-127">To be more specific: if the version of the currently-installed module is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="f7b3d-128">Om versionen av installerat modulen är större än värdet för parametern MinimumVersion eller lika med värdet för parametern RequiredVersion, fortsätter installera modulen tyst utan att installera modulen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-128">If the version of the installed module is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Module silently continues without installing that module.</span></span>

<span data-ttu-id="f7b3d-129">Installera modulen returnerar ett fel om ingen modul finns i online-galleriet som matchar det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-129">Install-Module returns an error if no module exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="f7b3d-130">Ange en matris med Modulnamnen, avgränsade med kommatecken om du vill installera flera moduler.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-130">To install multiple modules, specify an array of the module names, separated by commas.</span></span> <span data-ttu-id="f7b3d-131">Du kan inte lägga till MinimumVersion eller RequiredVersion om du anger flera Modulnamnen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-131">You cannot add MinimumVersion or RequiredVersion if you specify multiple module names.</span></span>

<span data-ttu-id="f7b3d-132">Som standard installeras moduler i mappen program för att förhindra förvirring när du installerar Windows PowerShell önskad tillstånd Configuration DSC ()-resurser. Du kan skicka vidare flera PSGetItemInfo objekt för att installera modulen. Detta är ett annat sätt för att ange flera moduler ska installeras i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-132">By default, modules are installed to the Program Files folder, to prevent confusion when you are installing Windows PowerShell Desired State Configuration (DSC) resources.You can pipe multiple PSGetItemInfo objects to Install-Module; this is another way of specifying multiple modules to install in a single command.</span></span>

<span data-ttu-id="f7b3d-133">För att förhindra körs modulerna som innehåller skadlig kod, installeras importeras inte moduler automatiskt under installationen.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-133">To help prevent running modules that contain malicious code, installed modules are not automatically imported by installation.</span></span> <span data-ttu-id="f7b3d-134">Som bästa säkerhetspraxis bör du utvärdera modul kod innan du kör alla cmdletar eller funktioner i en modul för första gången.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-134">As a security best practice, evaluate module code before running any cmdlets or functions in a module for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="f7b3d-135">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="f7b3d-135">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Install-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="f7b3d-136">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="f7b3d-136">Cmdlet online help reference</span></span>

[<span data-ttu-id="f7b3d-137">Installera modulen</span><span class="sxs-lookup"><span data-stu-id="f7b3d-137">Install-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398573)

## <a name="example-commands"></a><span data-ttu-id="f7b3d-138">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="f7b3d-138">Example commands</span></span>

```powershell

# Install a module by name
Install-Module -Name MyDscModule

# Install multiple modules
Install-Module ContosoClient,ContosoServer

# Install a module using its minimum version
Install-Module -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a module
Install-Module -Name ContosoServer -RequiredVersion 1.1.3

# Install the latest version of a module to $home\Documents\WindowsPowerShell\Modules.
Install-Module -Name ContosoServer -Scope CurrentUser

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -RequiredVersion 1.5

# if a module is already available under $env:PSModulePath, below command fails with 'ModuleAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Module ContosoServer -MinimumVersion 2.5

# Install multiple modules from multiple registered repositories
Install-Module ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a module with -WhatIf
Install-Module ContosoClient -WhatIf

# Install a module with -Confirm. A prompt will be displayed to confirm the installation.
Install-Module ContosoClient -WhatIf

# -Force option reinstalls the installed module
Install-Module ContosoClient -Force

# Install a module with dependencies
Install-Module -Name 
```

## <a name="install-module-cmdlet-in-pipeline-operations"></a><span data-ttu-id="f7b3d-139">Installera modulen cmdlet i pipeline-åtgärder</span><span class="sxs-lookup"><span data-stu-id="f7b3d-139">Install-Module cmdlet in pipeline operations</span></span>

```powershell

# Find a module and install it
Find-Module -Name "MyDSC*" | Install-Module

# Find a module and install it to the CurrentUser scope
Find-Module -Name "MyDSC*" | Install-Module -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Module to install them.
# The second command uses Get-InstalledModule to verify the modules from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Module
Get-InstalledModule

# This command finds the resource named MyResource and passes it to the Install-Module cmdlet by using the pipeline operator. The Install-Module cmdlet installs the module for the resource. 
# If you pipe multiple resources to the Install-Module cmdlet from the same module, Install-Module attempts to install the module only once. 
Find-DscResource -Name "MyResource" | Install-Module
Get-InstalledModule

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Module
Get-InstalledModule

```

## <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="f7b3d-140">Stöd för sida-vid-sida-Version på PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="f7b3d-140">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="f7b3d-141">PowerShellGet stöder modulen Versionsstöd för sida-vid-sida (SxS) i installera modulen Update-modulen och publicera modul-cmdlet: ar som körs i Windows PowerShell 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="f7b3d-141">PowerShellGet supports the side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>

### <a name="install-module-examples"></a><span data-ttu-id="f7b3d-142">Installera modulen exempel</span><span class="sxs-lookup"><span data-stu-id="f7b3d-142">Install-Module examples</span></span>

```powershell
# Install a version of the module
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Install another version of the module in Side-by-Side with already installed version.
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer 
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

# Get all versions of an installed module
Get-InstalledModule -Name PSScriptAnalyzer -AllVersions
Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.1.0      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis... 
1.1.1      PSScriptAnalyzer                    PSGallery            PSScriptAnalyzer provides script analysis...


```

## <a name="install-module-with-its-dependencies"></a><span data-ttu-id="f7b3d-143">Installera modulen med dess beroenden</span><span class="sxs-lookup"><span data-stu-id="f7b3d-143">Install module with its dependencies</span></span>

```powershell

# Find a module
Find-Module -Name TypePx -Repository PSGallery

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

# Find a module and its dependencies
Find-Module -Name TypePx -Repository PSGallery -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...

# Discover the dependencies list without adding -IncludeDependencies
$result = Find-Module -Name TypePx -Repository PSGallery
$result.Dependencies

Name                           Value
----                           -----
Name                           SnippetPx
CanonicalId                    powershellget:SnippetPx/#https://www.powershellgallery.com/api/v2/


# Now install the module along with its dependencies
Install-Module -Name TypePx -Repository PSGallery -Verbose

VERBOSE: Repository details, Name = 'PSGallery', Location = 'https://www.powershellgallery.com/api/v2/'; IsTrusted =
'False'; IsRegistered = 'True'.
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'PSGallery'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://www.powershellgallery.com/api/v2/' and PackageManagementProvider is
'NuGet'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'TypePx'.
VERBOSE: Performing the operation "Install-Module" on target "Version '2.0.1.20' of module 'TypePx'".

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"): Y
VERBOSE: The installation scope is specified to be 'AllUsers'.
VERBOSE: The specified module will be installed in 'C:\Program Files\WindowsPowerShell\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading module 'TypePx' with version '2.0.1.20' from the repository
'https://www.powershellgallery.com/api/v2/'.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='TypePx'' for ''.
VERBOSE: Searching repository 'https://www.powershellgallery.com/api/v2/FindPackagesById()?id='SnippetPx'' for ''.
VERBOSE: InstallPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\SnippetPx\SnippetPx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/SnippetPx/1.0.5.18'.
VERBOSE: Completed downloading 'SnippetPx'.
VERBOSE: Hash for package 'SnippetPx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='SnippetPx',
version='1.0.5.18',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: InstallPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: DownloadPackage' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896\TypePx\TypePx.nupkg',
uri='https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'
VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/TypePx/2.0.1.20'.
VERBOSE: Completed downloading 'TypePx'.
VERBOSE: Hash for package 'TypePx' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='TypePx',
version='2.0.1.20',destination='C:\Users\manikb\AppData\Local\Temp\1027042896'
VERBOSE: Installing the dependency module 'SnippetPx' with version '1.0.5.18' for the module 'TypePx'.
VERBOSE: Module 'SnippetPx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\SnippetPx\1.0.5.18'.
VERBOSE: Module 'TypePx' was installed successfully to path 'C:\Program
Files\WindowsPowerShell\Modules\TypePx\2.0.1.20'.


# Get the installed modules
Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.5.18   SnippetPx                           PSGallery            The SnippetPx module enhances the snippet experience i...
2.0.1.20   TypePx                              PSGallery            The TypePx module adds properties and methods to the m...

```

## <a name="error-scenarios"></a><span data-ttu-id="f7b3d-144">Fel-scenarier</span><span class="sxs-lookup"><span data-stu-id="f7b3d-144">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Module'
Install-Module ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Module'
Install-Module ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Module'
Install-Module ContosoClient,ContosoServer -MinimumVersion 2.0

```

