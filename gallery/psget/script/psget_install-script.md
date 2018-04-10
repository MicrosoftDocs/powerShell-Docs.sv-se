---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Install-Script
ms.openlocfilehash: 3d5b3a3076a11fbf452eb1b968decf217d9bace0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="install-script"></a><span data-ttu-id="88089-103">Install-Script</span><span class="sxs-lookup"><span data-stu-id="88089-103">Install-Script</span></span>

<span data-ttu-id="88089-104">Installerar filer för PowerShell-skriptet från online databaser till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="88089-104">Installs the PowerShell script files from online repositories to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="88089-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88089-105">Description</span></span>

<span data-ttu-id="88089-106">Installationsskriptet cmdleten hittar och hämtar en eller flera skript från en online-galleriet, validerar och installerar dem på den lokala datorn till den angivna omfattningen.</span><span class="sxs-lookup"><span data-stu-id="88089-106">The Install-Script cmdlet finds and downloads one or more scripts from an online gallery, validates and installs them on the local computer to the specified installation scope.</span></span>

<span data-ttu-id="88089-107">Om ingen omfattning har definierats, eller när värdet för parametern Scope är AllUsers, installeras skriptet %systemdrive%:\Program Files\WindowsPowerShell\scripts.</span><span class="sxs-lookup"><span data-stu-id="88089-107">When no scope is defined, or when the value of the Scope parameter is AllUsers, the script is installed to %systemdrive%:\Program Files\WindowsPowerShell\scripts.</span></span> <span data-ttu-id="88089-108">När värdet för Scope är CurrentUser, installeras skriptet $home\Documents\WindowsPowerShell\scripts.</span><span class="sxs-lookup"><span data-stu-id="88089-108">When the value of Scope is CurrentUser, the script is installed to $home\Documents\WindowsPowerShell\scripts.</span></span>

<span data-ttu-id="88089-109">Du kan filtrera resultatet baserat på lägsta och det exakta versioner av angivet skript.</span><span class="sxs-lookup"><span data-stu-id="88089-109">You can filter your results based on minimum and exact versions of specified scripts.</span></span>

<span data-ttu-id="88089-110">Vissa viktiga information:</span><span class="sxs-lookup"><span data-stu-id="88089-110">Some important notes:</span></span>
- <span data-ttu-id="88089-111">Skript är installerade enskilda filer.</span><span class="sxs-lookup"><span data-stu-id="88089-111">Scripts are installed single files.</span></span> <span data-ttu-id="88089-112">Därför bara en kopia av ett skript som är installerad och flera versioner av skript kan inte vara installerade sida-vid-sida på ett system.</span><span class="sxs-lookup"><span data-stu-id="88089-112">As a result, only one copy of a script is installed, and multiple versions of scripts cannot be installed side-by-side on a system.</span></span>
- <span data-ttu-id="88089-113">Skript kan definiera beroenden i externa moduler som kommer att installeras när du kör skriptet för installationen.</span><span class="sxs-lookup"><span data-stu-id="88089-113">Scripts may define dependencies on external modules, which will  be installed when Install-Script is run.</span></span>
- <span data-ttu-id="88089-114">**Betrodd kommandoprompt:** användaren godkännande krävs för att installera skript från en ej betrodd lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="88089-114">**Untrusted prompt:** User acceptance is required for installing the scripts from an untrusted repository.</span></span>
- <span data-ttu-id="88089-115">RequiredVersion installerar den angivna versionen i SxS med befintliga versioner på PowerShell version 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="88089-115">RequiredVersion installs the specified version in SxS with existing versions on PowerShell version 5.0 or newer.</span></span>

<span data-ttu-id="88089-116">Jokertecken stöds inte i - namnet på installationsskriptet, spara skriptet och Avinstallationsskriptet cmdlets.</span><span class="sxs-lookup"><span data-stu-id="88089-116">Wildcards are not supported in -Name on Install-Script, Save-Script, and Uninstall-Script cmdlets.</span></span>

### <a name="scope"></a><span data-ttu-id="88089-117">Omfång</span><span class="sxs-lookup"><span data-stu-id="88089-117">Scope</span></span>
<span data-ttu-id="88089-118">Anger installationen omfånget för skriptet.</span><span class="sxs-lookup"><span data-stu-id="88089-118">Specifies the installation scope of the script.</span></span> <span data-ttu-id="88089-119">Godkända värden för den här parametern är: AllUsers och CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="88089-119">The acceptable values for this parameter are: AllUsers and CurrentUser.</span></span>

<span data-ttu-id="88089-120">Standard installationen scope är AllUsers.</span><span class="sxs-lookup"><span data-stu-id="88089-120">The default installation scope is AllUsers.</span></span>

<span data-ttu-id="88089-121">AllUsers omfång tillåter skript som installeras på en plats som är tillgänglig för alla användare av datorn, det vill säga ”$env: SystemDrive\Program Files\WindowsPowerShell\scripts”.</span><span class="sxs-lookup"><span data-stu-id="88089-121">The AllUsers scope lets scripts be installed in a location that is accessible to all users of the computer, that is, "$env:SystemDrive\Program Files\WindowsPowerShell\scripts".</span></span>

<span data-ttu-id="88089-122">Området CurrentUser tillåter skript installeras endast på ”$home\Documents\WindowsPowerShell\scripts”, så att skriptet är bara tillgänglig för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88089-122">The CurrentUser scope lets scripts be installed only to "$home\Documents\WindowsPowerShell\scripts", so that the script is available only to the current user.</span></span>


<span data-ttu-id="88089-123">Anger installationen omfånget för skriptet.</span><span class="sxs-lookup"><span data-stu-id="88089-123">Specifies the installation scope of the script.</span></span> <span data-ttu-id="88089-124">Giltiga värden är: AllUsers och CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="88089-124">Valid values are: AllUsers and CurrentUser.</span></span> <span data-ttu-id="88089-125">Standardvärdet är CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="88089-125">The default is CurrentUser.</span></span>

<span data-ttu-id="88089-126">AllUsers omfattningen anger att installera ett skript på %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts så att skriptet är tillgängliga för alla användare.</span><span class="sxs-lookup"><span data-stu-id="88089-126">The AllUsers scope specifies to install a script to %systemdrive%:\ProgramFiles\WindowsPowerShell\Scripts so that the script is available to all users.</span></span> <span data-ttu-id="88089-127">Området CurrentUser anger om du vill installera skriptet i $home\Documents\WindowsPowerShell\Scripts så att skriptet är bara tillgänglig för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="88089-127">The CurrentUser scope specifies to install the script in $home\Documents\WindowsPowerShell\Scripts so that the script is available only to the current user.</span></span>


## <a name="nopathupdate"></a><span data-ttu-id="88089-128">NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="88089-128">NoPathUpdate</span></span>

- <span data-ttu-id="88089-129">NoPathUpdate switchparametern på installationsskriptet cmdlet kringgår tolken för att lägga till installationsplatsen skript i PATH-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="88089-129">NoPathUpdate switch parameter on Install-Script cmdlet bypasses the prompt for adding the script install location to the PATH environment variable.</span></span>
- <span data-ttu-id="88089-130">All användning av kommandot – NoPathUpdate angetts leder ingen fråga och den sökväg inte uppdateras (force är kan ignoreras här).</span><span class="sxs-lookup"><span data-stu-id="88089-130">Any use of the command WITH –NoPathUpdate specified will result in no prompt and the PATH NOT being updated (force is ignorable here).</span></span>
- <span data-ttu-id="88089-131">-Force utan – NoPathUpdate leder till att ingen fråga och SÖKVÄGEN kommer att uppdateras.</span><span class="sxs-lookup"><span data-stu-id="88089-131">-Force without –NoPathUpdate will result in no prompt and the PATH will be updated.</span></span>
- <span data-ttu-id="88089-132">Om varken – Force eller – NoPathUpdate har angetts visas prompten.</span><span class="sxs-lookup"><span data-stu-id="88089-132">If neither –Force or –NoPathUpdate are specified, the user will see the prompt.</span></span>
- <span data-ttu-id="88089-133">Allt detta gäller bara den första gången installationsskriptet används i ett givet omfång.</span><span class="sxs-lookup"><span data-stu-id="88089-133">All of this only applies the first time Install-Script is used in a given scope.</span></span>


## <a name="notes"></a><span data-ttu-id="88089-134">Obs!</span><span class="sxs-lookup"><span data-stu-id="88089-134">Notes</span></span>

<span data-ttu-id="88089-135">Denna cmdlet körs på Windows PowerShell 3.0 eller senare versioner av Windows PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="88089-135">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="88089-136">Om en version av skriptet på datorn matchar det angivna värdet för parametern namn, och du har inte lagt till parametern MinimumVersion eller RequiredVersion, fortsätter installationsskriptet tyst utan att installera skriptet.</span><span class="sxs-lookup"><span data-stu-id="88089-136">If a version of the script on the computer matches the value specified for the Name parameter, and you have not added the MinimumVersion or RequiredVersion parameter, Install-Script silently continues without installing that script.</span></span> <span data-ttu-id="88089-137">Om MinimumVersion eller RequiredVersion parametrar har angetts, och det befintliga skriptet överensstämmer inte med värdena i parametern, uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="88089-137">If the MinimumVersion or RequiredVersion parameters are specified, and the existing script does not match the values in that parameter, then an error occurs.</span></span> <span data-ttu-id="88089-138">Vara mer specifika: om versionen av skriptet installerade är lägre än värdet för parametern MinimumVersion, eller inte lika med värdet för parametern RequiredVersion, ett fel uppstår.</span><span class="sxs-lookup"><span data-stu-id="88089-138">To be more specific: if the version of the currently-installed script is either lower than the value of the MinimumVersion parameter, or not equal to the value of the RequiredVersion parameter, an error occurs.</span></span> <span data-ttu-id="88089-139">Om versionen av skriptet installerade är större än värdet för parametern MinimumVersion eller lika med värdet för parametern RequiredVersion, fortsätter installationsskriptet tyst utan att installera skriptet.</span><span class="sxs-lookup"><span data-stu-id="88089-139">If the version of the installed script is greater than the value of the MinimumVersion parameter, or equal to the value of the RequiredVersion parameter, Install-Script silently continues without installing that script.</span></span>

<span data-ttu-id="88089-140">Installera skriptet returnerar ett fel om det inte finns några skript i online-galleriet som matchar det angivna namnet.</span><span class="sxs-lookup"><span data-stu-id="88089-140">Install-Script returns an error if no script exists in the online gallery that matches the specified name.</span></span>

<span data-ttu-id="88089-141">Ange en matris med skriptet namnen, avgränsade med kommatecken om du vill installera flera skript.</span><span class="sxs-lookup"><span data-stu-id="88089-141">To install multiple scripts, specify an array of the script names, separated by commas.</span></span> <span data-ttu-id="88089-142">Du kan inte lägga till MinimumVersion eller RequiredVersion om du anger flera Skriptnamn.</span><span class="sxs-lookup"><span data-stu-id="88089-142">You cannot add MinimumVersion or RequiredVersion if you specify multiple script names.</span></span>

<span data-ttu-id="88089-143">Som standard installeras skript till mappen Program.</span><span class="sxs-lookup"><span data-stu-id="88089-143">By default, scripts are installed to the Program Files folder.</span></span> <span data-ttu-id="88089-144">Du kan skicka vidare flera PSGetItemInfo objekt till installationsskriptet; Detta är ett annat sätt för att ange flera skript ska installeras i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="88089-144">You can pipe multiple PSGetItemInfo objects to Install-Script; this is another way of specifying multiple scripts to install in a single command.</span></span>

<span data-ttu-id="88089-145">För att förhindra att köra skript som innehåller skadlig kod som installerats importeras skript automatiskt inte under installationen.</span><span class="sxs-lookup"><span data-stu-id="88089-145">To help prevent running scripts that contain malicious code, installed scripts are not automatically imported by installation.</span></span> <span data-ttu-id="88089-146">Som bästa säkerhetspraxis bör du utvärdera skriptkod innan du kör alla cmdletar eller funktioner i ett skript för första gången.</span><span class="sxs-lookup"><span data-stu-id="88089-146">As a security best practice, evaluate script code before running any cmdlets or functions in a script for the first time.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="88089-147">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="88089-147">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Install-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="88089-148">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="88089-148">Cmdlet online help reference</span></span>

[<span data-ttu-id="88089-149">Install-Script</span><span class="sxs-lookup"><span data-stu-id="88089-149">Install-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619784)

## <a name="example-commands"></a><span data-ttu-id="88089-150">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="88089-150">Example commands</span></span>

```powershell


# Piping Find-Script output to Install-Script cmdlet

Find-Script -Repository Local1 -Name Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Find-Script -Repository Local1 -Name Required-Script2 | Install-Script

Get-Command Required-Script2

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
ExternalScript  Required-Script2.ps1                                2.0       C:\Users\manikb\Documents\WindowsPowerShell\Scripts\Required-Script2.ps1


Get-InstalledScript Required-Script2

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script2                    local1               Description for the Required-Script2 script


Get-InstalledScript Required-Script2 | fl * -Force


Name                       : Required-Script2
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script2 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:39 AM
LicenseUri                 : http://required-script2.com/license
ProjectUri                 : http://required-script2.com/
IconUri                    : http://required-script2.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script2 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Users\manikb\Documents\WindowsPowerShell\Scripts


# Installing a script to AllUsers scope

Install-Script -Repository Local1 -Name Required-Script3 -Scope AllUsers
Get-InstalledScript -Name Required-Script3

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Get-InstalledScript -Name Required-Script3  | fl * -Force


Name                       : Required-Script3
Version                    : 2.5
Type                       : Script
Description                : Description for the Required-Script3 script
Author                     : manikb
CompanyName                :
Copyright                  : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate              : 8/15/2015 12:42:45 AM
LicenseUri                 : http://required-script3.com/license
ProjectUri                 : http://required-script3.com/
IconUri                    : http://required-script3.com/icon
Tags                       : {Tag1, Tag2, Tag-Required-Script3-2.5, PSScript...}
Includes                   : {Function, DscResource, Cmdlet, Command}
PowerShellGetFormatVersion :
ReleaseNotes               : Required-Script3 release notes
Dependencies               : {}
RepositorySourceLocation   : http://manikb-dev:8765/api/v2/
Repository                 : local1
PackageManagementProvider  : NuGet
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


# Installing a script with dependent scripts and modules

Find-Script -Repository Local1 -Name Script-WithDependencies2 -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Script-WithDependencies2
Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script
2.0        Script-WithDependencies2            local1               Description for the Script-WithDependencies2 script


Get-InstalledModule

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        RequiredModule1                     local1               RequiredModule1 module
2.5        RequiredModule2                     local1               RequiredModule2 module
2.5        RequiredModule3                     local1               RequiredModule3 module


Find-Script -Repository Local1 -Name Required-Script*

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


Install-Script -Repository Local1 -Name Required-Script*

Get-InstalledScript

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.5        Required-Script1                    local1               Description for the Required-Script1 script
2.5        Required-Script2                    local1               Description for the Required-Script2 script
2.5        Required-Script3                    local1               Description for the Required-Script3 script


# Find a script and install it

# The first command finds the script named Required-Script2 from the Local1 repository and displays the results.
# The second command finds the Required-Script2 script, and then uses the pipeline operator to pass it to the Install-Script cmdlet to install it.
# The third command uses the Get-Command cmdlet to get Required-Script2, and then displays the results.
# The fourth command uses the Get-InstalledScript cmdlet to get Required-Script2 and display the results.
# The fifth command gets RequiredScript2 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Find-Script -Repository "Local1" -Name "Required-Script2"

Find-Script -Repository "Local1" -Name "Required-Script2" | Install-Script
Get-Command -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2"

Get-InstalledScript -Name "Required-Script2" | Format-List *


# Install a script with AllUsers scope

# The first command installs the script named Required-Script3 and assigns it AllUsers scope.
# The second command gets the installed script Required-Script3 and displays information about it.
# The third command gets Required-Script3 and uses the pipeline operator to pass it to the Format-List cmdlet to format the output.

Install-Script -Repository "Local1" -Name "Required-Script3" -Scope "AllUsers"
Get-InstalledScript -Name "Required-Script3"
Get-InstalledScript -Name "Required-Script3" | Format-List *


# Install a script with its dependent scripts and modules

# The first command finds the script named Script-WithDependencies2 and its dependencies in the Local1 repository and displays the results.
# The second command installs Script-WithDependencies2.
# The third command uses the Get-InstalledScript script cmdlet to get installed scripts and display the results.
# The fourth command uses the Get-InstalledModule cmdlet to get installed modules and display the results.
# The fifth command uses the Find-Script cmdlet to find scripts where the name begins with Required-Script and display the results.
# The sixth command installs the scripts where the name begins with Required-Script in the Local1 repository.
# The final command gets installed scripts and displays the results.

Find-Script -Repository "Local1" -Name "Script-WithDependencies2" -IncludeDependencies
Install-Script -Repository "Local1" -Name "Script-WithDependencies2"
Get-InstalledScript
Get-InstalledModule
Find-Script -Repository "Local1" -Name "Required-Script*"
Install-Script -Repository "Local1" -Name "Required-Script*"
Get-InstalledScript

```

<span data-ttu-id="88089-151">Du kan också använda Get-Command – namn <InstalledScriptFileName> att hämta den.</span><span class="sxs-lookup"><span data-stu-id="88089-151">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="88089-152">Installationsplats för två läggs till i PATH-miljövariabeln vid första användning av ett angivet omfång.</span><span class="sxs-lookup"><span data-stu-id="88089-152">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1
```

```powershell

# Install a script by name
Install-Script -Name MyDscscript

# Install multiple scripts
Install-Script ContosoClient,ContosoServer

# Install a script using its minimum version
Install-Script -Name ContosoServer -MinimumVersion 1.0

# Install a specific version of a script
Install-Script -Name ContosoServer -RequiredVersion 1.1.3

# Install a specific prerelease version of a script
Install-Script -Name ContosoServer -RequiredVersion 1.1.3-alpha -AllowPrerelease

# Install the latest version of a script to $home\Documents\WindowsPowerShell\scripts.
Install-Script -Name ContosoServer -Scope CurrentUser

# if a script is already available under $env:PSModulePath, below command fails with 'scriptAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -RequiredVersion 1.5

# if a script is already available under $env:PSModulePath, below command fails with 'scriptAlreadyInstalled,Install-Package,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage'
Install-Script ContosoServer -MinimumVersion 2.5

# Install multiple scripts from multiple registered repositories
Install-Script ContosoClient,ContosoServer -Repository PSGallery, PrivatePSGallery

# Install a script with -WhatIf
Install-Script ContosoClient -WhatIf

# Install a script with -Confirm. A prompt will be displayed to confirm the installation.
Install-Script ContosoClient -WhatIf

# -Force option reinstalls the installed script
Install-Script ContosoClient -Force

# Install a script with dependencies
Install-Script -Name ContosoClient

# Install a script

# Install a script from the registered repository with ScriptSourceLocation
Install-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Install-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Install-Script -Name *Azure*

# Find all versions of a script
Install-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion.
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Install-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Install-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Install-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script from the specified repository
Install-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Install-Script

# Find available scripts from few registered repositories
Install-Script -Repository PSGallery, PrivatePSGallery

```

```powershell
 Added the logic for checking and failing the install script operation when there is a command with same name is already available on the system.
Also updated the prompt message.

 Examples:
PS C:\WINDOWS\system32> install-script get-childitem -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script



 PS C:\WINDOWS\system32> install-script get-childitem,contosos -Repository localrepo
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:1
+ install-script get-childitem,contosos -Repository localrepo
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script

 PackageManagement\Install-Package : No match was found for the specified search criteria and script name 'contosos'. Try Get-ScriptRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\powershellget\1.0.0.1\PSModule.psm1:2891 char:21
+ ...          $null = PackageManagement\Install-Package @PSBoundParameters
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
     + CategoryInfo          : ObjectNotFound: (Microsoft.Power....InstallPackage:InstallPackage) [Install-Package], Exception
     + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage

 PS C:\WINDOWS\system32>



 PS C:\WINDOWS\system32> find-script get-childitem -Repository localrepo | install-script
install-script : A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.
At line:1 char:51
+ find-script get-childitem -Repository localrepo | install-script
+                                                   ~~~~~~~~~~~~~~
     + CategoryInfo          : InvalidOperation: (:) [Write-Error], WriteErrorException
     + FullyQualifiedErrorId : CommandAlreadyAvailableWitScriptName,Install-Script


 PS C:\WINDOWS\system32>

 PS C:\WINDOWS\system32> Install-Package -Name Get-ChildItem -source LocalRepo  -ProviderName powershellget -Type Script
WARNING: A command with name 'get-childitem' is already available on this system. This script 'get-childitem' may override the existing command. If you still want to install this script 'get-childitem', use -Force parameter.

```

```powershell

Prompt ONCE per USER and per SCOPE for adding the script installation location to PATH environment variable.

- Prompt message for CurrentUser scope: (Complete message will be scrubbed later)

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Users\manikb\Documents\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- Prompt message for –AllUsers scope is same as above with $env:ProgramFiles\WindowsPowerShell\Scripts .

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):


- To prompt only once per scope, user acceptance for PATH variable change will be added to the user specific settings file under %localappdata%\Microsoft\windows\PowerShell\PowerShellGet
%localappdata%\Microsoft\windows\PowerShell\PowerShellGet\PowerShellGetSettings.XML.
This settings file will be used to not prompt again.

After prompting for CurrentUser scope:
    true or false for CurrentUserScope_AllowPATHChangeForScripts key based on user input.

After prompting for AllUsers scope:
    true or false for AllUsersScope_AllowPATHChangeForScripts key based on user input.

- If user accepts the prompt
                Check and add $home\Documents\WindowsPowerShell\Scripts to user specific PATH environment variable.
                Check and add $env:ProgramFiles\WindowsPowerShell\Scripts to system specific PATH environment variable only when Install-Script cmdlet is used in an administrator process.
                Check and add above two paths to $env:PATH variable of the current process.

- If user denies the prompt, script installation will be proceeded without making any changes to the PATH environment variable.



Example:
PS C:\windows\system32> Install-Script -Name $scriptName -Repository $repositoryName -Scope $Scope -Verbose

Acceptance required for adding the script installation locations to the PATH environment variable
The scripts install location 'C:\Program Files\WindowsPowerShell\Scripts' is required to be added to the PATH environment variable in order to execute an installed script with only file name along with its script dependencies. If you accept this prompt, 'C:\Program Files\WindowsPowerShell\Scripts' will be added to system specific PATH environment variable and process specific $env:PATH variable, if not already added. Otherwise you will have to use the full file path to  execute an installed script. Alternatively, you can use Save-Script cmdlet to download the script files to your favorite location. This prompt can be avoided and automatically considered as opted-out by adding 'C:\Program Files\WindowsPowerShell\Scripts' install location to the PATH environment variable or to the $env:PATH variable of current process. Do you want to continue?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n


```

## <a name="install-script-cmdlet-in-pipeline-operations"></a><span data-ttu-id="88089-153">Installationsskriptet cmdlet i pipeline-åtgärder</span><span class="sxs-lookup"><span data-stu-id="88089-153">Install-Script cmdlet in pipeline operations</span></span>

```powershell

# Find a script and install it
Find-Script -Name "MyDSC*" | Install-Script

# Find a script and install it to the CurrentUser scope
Find-Script -Name "MyDSC*" | Install-Script -Scope CurrentUser

# Find commands by name and install them
# The first command finds the specified commands in the INT repository, and then uses the pipeline operator to pass them to Install-Script to install them.
# The second command uses Get-Installedscript to verify the scripts from the prior command are installed.
Find-Command -Repository "INT" -Name Get-ContosoClient,Get-ContosoServer | Install-Script
Get-Installedscript

# Find multiple role capabilities and install them
Find-RoleCapability -Name MyJeaRole, Maintenance | Install-Script
Get-Installedscript

```



## <a name="error-scenarios"></a><span data-ttu-id="88089-154">Fel-scenarier</span><span class="sxs-lookup"><span data-stu-id="88089-154">Error scenarios</span></span>

```powershell

# Below command fails with 'NameShouldNotContainWildcardCharacters,Install-Script'
Install-Script ContosoServe*

# Below command fails with 'VersionRangeAndRequiredVersionCannotBeSpecifiedTogether,Install-Script'
Install-Script ContosoServer -MinimumVersion 1.0 -RequiredVersion 5.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -RequiredVersion 2.0

# Below command fails with 'VersionParametersAreAllowedOnlyWithSingleName,Install-Script'
Install-Script ContosoClient,ContosoServer -MinimumVersion 2.0

```

## <a name="install-script-and-get-installedscript-cmdlets"></a><span data-ttu-id="88089-155">Installationsskriptet och Get-InstalledScript-cmdlets</span><span class="sxs-lookup"><span data-stu-id="88089-155">Install-Script and Get-InstalledScript cmdlets</span></span>
<span data-ttu-id="88089-156">Installationsskriptet cmdlet kan du installera en specifik skriptfil tillsammans med dess beroenden i det specificerade omfånget.</span><span class="sxs-lookup"><span data-stu-id="88089-156">Install-Script cmdlet lets you to install a specific script file along with its dependencies to the specified scope.</span></span> <span data-ttu-id="88089-157">Som standard installeras skript AllUsers omfånget.</span><span class="sxs-lookup"><span data-stu-id="88089-157">By default, scripts are installed to the AllUsers scope.</span></span> <span data-ttu-id="88089-158">Get-InstalledScript cmdlet kan du hämta en lista över filer som installerades med installationsskriptet cmdlet.</span><span class="sxs-lookup"><span data-stu-id="88089-158">Get-InstalledScript cmdlet lets you to get the list of script files which were installed using Install-Script cmdlet.</span></span>

<span data-ttu-id="88089-159">Använd Obs: Om du vill tillåta hantering och lokalisering av skript när de installeras installationsskriptet skapar en standardmappen för lagring av skript på $home\Documents\WindowsPowerShell\Scripts, och lägga till mappen i din miljö för SÖKVÄGEN.</span><span class="sxs-lookup"><span data-stu-id="88089-159">Use note: To allow management and locating of scripts once they are installed, Install-script will create a default folder for storing scripts at $home\Documents\WindowsPowerShell\Scripts, and add that folder to your PATH environment.</span></span> <span data-ttu-id="88089-160">Om du ändrar sökvägen vara ett problem, kan du använda Spara skriptet i stället installationsskriptet.</span><span class="sxs-lookup"><span data-stu-id="88089-160">If modifying the path is a concern, use Save-Script instead of Install-Script.</span></span> <span data-ttu-id="88089-161">Get-InstalledScripts och avinstallera skriptet fungerar bara med skript som placeras i systemet med skriptet för installationen.</span><span class="sxs-lookup"><span data-stu-id="88089-161">Get-InstalledScripts and Uninstall-Script can only work with scripts placed on the system using Install-Script.</span></span>
```powershell
# Install locations for scripts:
# Default scope is AllUsers.
# AllUsers scope --> "$env:ProgramFiles\\WindowsPowerShell\\Scripts"
# CurrentUser scope -->; "$env:USERPROFILE\\Documents\\WindowsPowerShell\\Scripts"

# Piping Find-Script output to Install-Script cmdlet
Find-Script -Repository GalleryINT -Name Required-Script2 | Install-Script -Scope CurrentUser -Verbose
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: Using the provider 'PowerShellGet' for searching packages.
VERBOSE: Using the specified source names : 'GalleryINT'.
VERBOSE: Getting the provider object for the PackageManagement Provider 'NuGet'.
VERBOSE: The specified Location is 'https://customgallery.cloudapp.net/api/v2/items/psscript/' and PackageManagementProvider is 'NuGet'.
VERBOSE: Searching repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/FindPackagesById()?id='Required-Script2'' for ''.
VERBOSE: Total package yield:'1' for the specified package 'Required-Script2'.
VERBOSE: Performing the operation "Install-Script" on target "Version '2.5' of script 'Required-Script2'".
VERBOSE: The installation scope is specified to be 'CurrentUser'.
VERBOSE: The specified script will be installed in 'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts' and its dependent modules will be installed in
'C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Modules'.
VERBOSE: The specified Location is 'NuGet' and PackageManagementProvider is 'NuGet'.
VERBOSE: Downloading script 'Required-Script2' with version '2.5' from the repository 'https://customgallery.cloudapp.net/api/v2/items/psscript/'.
VERBOSE: Script 'Required-Script2' was installed successfully.

Get-InstalledScript Required-Scri\*
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script

Get-InstalledScript Required-Script2 | Format-List \* -Force
Name : Required-Script2
Version : 2.5
Type : Script
Description : Description for the Required-Script2 script
Author : manikb
CompanyName :
Copyright : (c) 2015 Microsoft Corporation. All rights reserved.
PublishedDate : 10/30/2015 1:25:15 AM
LicenseUri : http://required-script2.com/license
ProjectUri : http://required-script2.com/
IconUri : http://required-script2.com/icon
Tags : {Tag1, Tag2, Tag-Required-Script2-2.5, PSScript}
Includes : {Function, DscResource, Cmdlet, Workflow...}
PowerShellGetFormatVersion :
ReleaseNotes : Required-Script2 release notes
Dependencies : {}
RepositorySourceLocation : https://customgallery.cloudapp.net/api/v2/
Repository : GalleryINT
PackageManagementProvider : NuGet
AdditionalMetadata : {Type, releaseNotes, copyright, PackageManagementProvider...}
InstalledLocation : C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Installed script file is immediately available for usage.
```

<span data-ttu-id="88089-162">Du kan också använda Get-Command – namn <InstalledScriptFileName> att hämta den.</span><span class="sxs-lookup"><span data-stu-id="88089-162">You can also use Get-Command –Name <InstalledScriptFileName> to get it.</span></span> <span data-ttu-id="88089-163">Installationsplats för två läggs till i PATH-miljövariabeln vid första användning av ett angivet omfång.</span><span class="sxs-lookup"><span data-stu-id="88089-163">Two install locations are added to the PATH environment variable on first use of a specified scope.</span></span>
```powershell
$env:Path -split ';'| Where-Object {$\_} | Select-Object -Last 2
C:\\Program Files\\WindowsPowerShell\\Scripts
C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts

Get-Command Required-Script2
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script2.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Required-Script2.ps1

Find-Script -Repository LocalRepo1 -Name Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Find-Script -Repository LocalRepo1 -Name Demo-Script | Install-Script -Scope CurrentUser
Untrusted repository
You are installing the scripts from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the scripts from 'C:\\MyLocalRepo'?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"): Y

Get-InstalledScript Demo-Script
Version Name Type Repository Description
------- ---- ---- ---------- -----------
1.0 Demo-Script Script LocalRepo1 Script file description goes here

Get-Command Demo-Script
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Demo-Script.ps1 C:\\Users\\manikb\\Documents\\WindowsPowerShell\\Scripts\\Demo-Script.ps1

# Using the installed script
Demo-Script
Demo-ScriptFunction
Demo-ScriptWorkflow

# Installing a script to default AllUsers scope and with RequiredVersion
Install-Script -Repository GalleryINT -Name Required-Script3 -RequiredVersion 2.0
Get-InstalledScript -Name Required-Script3

Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
Get-InstalledScript -Name Required-Script3 | Format-List Name,InstalledLocation -Force
Name : Required-Script3
InstalledLocation : C:\\Program Files\\WindowsPowerShell\\Scripts

Get-Command Required-Script3
CommandType Name Version Source
----------- ---- ------- ------
ExternalScript Required-Script3.ps1 C:\\Program Files\\WindowsPowerShell\\Scripts\\Required-Script3.ps1

# Installing a script with dependent scripts and modules
Find-Script -Repository GalleryINT -Name Script-WithDependencies2 -IncludeDependencies
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.5 Required-Script3 Script GalleryINT Description for the Required-Script3 script

Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
Get-InstalledModule
Install-Script -Repository GalleryINT -Name Script-WithDependencies2 -Scope CurrentUser
Get-InstalledScript
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.0 Required-Script3 Script GalleryINT Description for the Required-Script3 script
1.0 Demo-Script Script LocalRepo1 Script file description goes here
2.5 Required-Script1 Script GalleryINT Description for the Required-Script1 script
2.5 Required-Script2 Script GalleryINT Description for the Required-Script2 script
2.0 Script-WithDependencies2 Script GalleryINT Description for the Script-WithDependencies2 script
Get-InstalledModule
Version Name Type Repository Description
------- ---- ---- ---------- -----------
2.5 RequiredModule1 Module GalleryINT RequiredModule1 module
2.5 RequiredModule2 Module GalleryINT RequiredModule2 module
2.5 RequiredModule3 Module GalleryINT RequiredModule3 module
2.0 RequiredModule4 Module GalleryINT RequiredModule4 module
1.5 RequiredModule5 Module GalleryINT RequiredModule5 module

# Contents of Script-WithDependencies2 file.
<#PSScriptInfo
.VERSION 2.0
.GUID 90082fa1-0b84-49fb-a00e-0a624fbb6584
.AUTHOR manikb
.COMPANYNAME Microsoft Corporation
.COPYRIGHT (c) 2015 Microsoft Corporation. All rights reserved.
.TAGS Tag1 Tag2 Tag-Script-WithDependencies2-2.0
.LICENSEURI http://script-withdependencies2.com/license
.PROJECTURI http://script-withdependencies2.com/
.ICONURI http://script-withdependencies2.com/icon
.EXTERNALMODULEDEPENDENCIES
.REQUIREDSCRIPTS Required-Script1,Required-Script2,Required-Script3
.EXTERNALSCRIPTDEPENDENCIES
.RELEASENOTES
Script-WithDependencies2 release notes
#>
#Requires -Module RequiredModule1
#Requires -Module @{ModuleName = 'RequiredModule2'; ModuleVersion = '2.0'}
#Requires -Module @{RequiredVersion = '2.5'; ModuleName = 'RequiredModule3'}
#Requires -Module @{ModuleVersion = '1.1'; ModuleName = 'RequiredModule4'; MaximumVersion = '2.0'}
#Requires -Module @{MaximumVersion = '1.5'; ModuleName = 'RequiredModule5'}
<#
.DESCRIPTION
Description for the Script-WithDependencies2 script
#>
Param()
Function Test-FunctionFromScript\_Script-WithDependencies2 { Get-Date }
Workflow Test-WorkflowFromScript\_Script-WithDependencies2 { Get-Date }
```