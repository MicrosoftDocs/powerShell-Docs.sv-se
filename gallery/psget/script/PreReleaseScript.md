---
ms.date: 10/17/2017
contributor: keithb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: PrereleaseScript
ms.openlocfilehash: 575babd6bc373e99a4e924fafef6e9edeec972d4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="47083-103">Förhandsversioner av skript</span><span class="sxs-lookup"><span data-stu-id="47083-103">Prerelease Versions of Scripts</span></span>

<span data-ttu-id="47083-104">Från och med version 1.6.0 PowerShellGet och PowerShell-galleriet ger stöd för märkning versioner som är större än 1.0.0 som en förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="47083-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="47083-105">Innan den här funktionen har förhandsversionen begränsad till att ha en version som börjar med 0.</span><span class="sxs-lookup"><span data-stu-id="47083-105">Prior to this feature, prerelease items were limited to having a version beginning with 0.</span></span> <span data-ttu-id="47083-106">Syftet med dessa funktioner är att ger större stöd för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konventionen utan att bryta bakåtkompatibilitet kompatibilitet med PowerShell version 3 och senare, eller befintliga versioner av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="47083-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span>
<span data-ttu-id="47083-107">Det här avsnittet fokuserar på skript-specifika funktioner.</span><span class="sxs-lookup"><span data-stu-id="47083-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="47083-108">Motsvarande funktionerna för moduler är i den [förhandsversion modulversioner](../module/PrereleaseModule.md) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="47083-108">The equivalent features for modules are in the [Prerelease Module Versions](../module/PrereleaseModule.md) topic.</span></span> <span data-ttu-id="47083-109">Med hjälp av dessa funktioner, kan utgivare identifiera ett skript som version 2.5.0-alpha och senare använda en produktionsklara version 2.5.0 som ersätter förhandsversionen.</span><span class="sxs-lookup"><span data-stu-id="47083-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="47083-110">På en hög nivå förhandsversionen skript bland annat:</span><span class="sxs-lookup"><span data-stu-id="47083-110">At a high level, the prerelease script features include:</span></span>

* <span data-ttu-id="47083-111">Lägger till ett PrereleaseString suffix Versionsträngen i manifestet skript.</span><span class="sxs-lookup"><span data-stu-id="47083-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span>
<span data-ttu-id="47083-112">Om skripten har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversionen objekt.</span><span class="sxs-lookup"><span data-stu-id="47083-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease items.</span></span>
* <span data-ttu-id="47083-113">Hämta förhandsversionen objekt kräver att lägga till AllowPrerelease - flaggan i PowerShellGet kommandona Sök-skript, installationsskriptet, Update-skript och spara-skript.</span><span class="sxs-lookup"><span data-stu-id="47083-113">Acquiring prerelease items requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span>
<span data-ttu-id="47083-114">Om flaggan inte anges visas inte förhandsversionen objekt.</span><span class="sxs-lookup"><span data-stu-id="47083-114">If the flag is not specified, prerelease items will not be shown.</span></span>
* <span data-ttu-id="47083-115">Skript-versioner som visas av Sök-skriptet, Get-InstalledScript och i PowerShell-galleriet visas med PrereleaseString som 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="47083-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="47083-116">Information om funktionerna finns nedan.</span><span class="sxs-lookup"><span data-stu-id="47083-116">Details for the features are included below.</span></span>


## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="47083-117">Identifierar en skriptversion som en förhandsversion</span><span class="sxs-lookup"><span data-stu-id="47083-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="47083-118">PowerShellGet stöd för förhandsversioner är enklare än moduler för skript.</span><span class="sxs-lookup"><span data-stu-id="47083-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span>
<span data-ttu-id="47083-119">Skriptet versionshantering stöds endast av PowerShellGet, så att det finns inga problem på grund av att lägga till förhandsversionen strängen.</span><span class="sxs-lookup"><span data-stu-id="47083-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span>
<span data-ttu-id="47083-120">Lägga till ett förhandsversionen suffix till en korrekt formaterad versionssträng i skriptmetadata för för att identifiera ett skript i PowerShell-galleriet som en förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="47083-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="47083-121">En exempeldelen av ett manifest för skript med en förhandsversion ser ut som följande:</span><span class="sxs-lookup"><span data-stu-id="47083-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

<span data-ttu-id="47083-122">Om du vill använda förhandsversionen suffix måste Versionsträngen uppfylla följande krav:</span><span class="sxs-lookup"><span data-stu-id="47083-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

* <span data-ttu-id="47083-123">Ett förhandsversionen suffix kan endast anges när versionen är 3 segment för Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="47083-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="47083-124">Detta justerar med SemVer v1.0.0</span><span class="sxs-lookup"><span data-stu-id="47083-124">This aligns with SemVer v1.0.0</span></span>
* <span data-ttu-id="47083-125">Suffixet förhandsversionen är en sträng som börjar med ett bindestreck och får bestå av alfanumeriska ASCII-tecken [0-9A-a - z-]</span><span class="sxs-lookup"><span data-stu-id="47083-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
* <span data-ttu-id="47083-126">Endast SemVer v1.0.0 förhandsversionen strängar stöds just nu, så suffixet förhandsversionen __får inte__ innehålla någon punkt eller + [. +], som är tillåtna i SemVer 2.0</span><span class="sxs-lookup"><span data-stu-id="47083-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix __must not__ contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
* <span data-ttu-id="47083-127">Exempel på PrereleaseString strängar som stöds är:-alfa, -á1,-BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="47083-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

<span data-ttu-id="47083-128">__Förhandsversionen versionshantering inverkan på Sortera ordning och installation mappar__</span><span class="sxs-lookup"><span data-stu-id="47083-128">__Prerelease versioning impact on sort order and installation folders__</span></span>

<span data-ttu-id="47083-129">Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar till PowerShell-galleriet, och när du installerar skript med hjälp av PowerShellGet kommandon.</span><span class="sxs-lookup"><span data-stu-id="47083-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span>
<span data-ttu-id="47083-130">Om två skript versioner med versionsnumret finns, sorteringsordningen är baserad på strängdelen efter bindestreck.</span><span class="sxs-lookup"><span data-stu-id="47083-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="47083-131">Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="47083-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span>
<span data-ttu-id="47083-132">Om två skript har samma versionsnummer och bara har en PrereleaseString skriptet __utan__ suffixet förhandsversionen antas vara klar för produktion-version och sorteras som en högre version än förhandsutgåvan version.</span><span class="sxs-lookup"><span data-stu-id="47083-132">If two scripts have the same version number, and only one has a PrereleaseString, the script __without__ the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span>
<span data-ttu-id="47083-133">Exempelvis när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas större av båda.</span><span class="sxs-lookup"><span data-stu-id="47083-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="47083-134">När du publicerar till PowerShell-galleriet som standard måste versionen av skriptet publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="47083-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>
<span data-ttu-id="47083-135">En utgivare kan uppdatera version 2.5.0-alpha 2.5.0-beta eller med 2.5.0 (med inga förhandsversionen suffix).</span><span class="sxs-lookup"><span data-stu-id="47083-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a><span data-ttu-id="47083-136">Söka efter och hämta förhandsversionen objekt med PowerShellGet kommandon</span><span class="sxs-lookup"><span data-stu-id="47083-136">Finding and acquiring prerelease items using PowerShellGet commands</span></span>

<span data-ttu-id="47083-137">Om förhandsversionen objekt med hjälp av PowerShellGet Sök-skript, installationsskriptet, Update-skript och spara skriptkommandon kräver att lägga till flaggan - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="47083-137">Dealing with prerelease items using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span>
<span data-ttu-id="47083-138">Om - AllowPrerelease anges inkluderas förhandsversionen objekt om de finns.</span><span class="sxs-lookup"><span data-stu-id="47083-138">If -AllowPrerelease is specified, prerelease items will be included if they are present.</span></span>
<span data-ttu-id="47083-139">Om AllowPrerelease - flaggan inte anges visas inte förhandsversionen objekt.</span><span class="sxs-lookup"><span data-stu-id="47083-139">If -AllowPrerelease flag is not specified, prerelease items will not be shown.</span></span>

<span data-ttu-id="47083-140">De enda undantagen till den här i skriptkommandon PowerShellGet är Get-InstalledScript och ibland med Uninstall-skript.</span><span class="sxs-lookup"><span data-stu-id="47083-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

* <span data-ttu-id="47083-141">Get-InstalledScript visas alltid automatiskt informationen om förhandsversionen i Versionsträngen om den finns.</span><span class="sxs-lookup"><span data-stu-id="47083-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
* <span data-ttu-id="47083-142">Avinstallera skript som standard avinstalleras den senaste versionen av ett skript om __ingen version__ har angetts.</span><span class="sxs-lookup"><span data-stu-id="47083-142">Uninstall-Script will by default uninstall the most recent version of a script, if __no version__ is specified.</span></span> <span data-ttu-id="47083-143">Att problemet inte har ändrats.</span><span class="sxs-lookup"><span data-stu-id="47083-143">That behavior has not changed.</span></span> <span data-ttu-id="47083-144">Men om en förhandsversion anges med - RequiredVersion, måste - AllowPrerelease utföras.</span><span class="sxs-lookup"><span data-stu-id="47083-144">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="47083-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="47083-145">Examples</span></span>
```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

<span data-ttu-id="47083-146">Avinstallera skriptet tar bort den aktuella versionen av ett skript när - RequiredVersion inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="47083-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="47083-147">Om - RequiredVersion anges, och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="47083-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage


```



## <a name="more-details"></a><span data-ttu-id="47083-148">Mer information</span><span class="sxs-lookup"><span data-stu-id="47083-148">More details</span></span>
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[<span data-ttu-id="47083-149">Förhandsversionen modulversioner</span><span class="sxs-lookup"><span data-stu-id="47083-149">Prerelease Module Versions</span></span>](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[<span data-ttu-id="47083-150">Sök-skript</span><span class="sxs-lookup"><span data-stu-id="47083-150">Find-script</span></span>](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[<span data-ttu-id="47083-151">Skriptet för installationen</span><span class="sxs-lookup"><span data-stu-id="47083-151">Install-script</span></span>](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[<span data-ttu-id="47083-152">Spara skriptet</span><span class="sxs-lookup"><span data-stu-id="47083-152">Save-script</span></span>](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[<span data-ttu-id="47083-153">Skript för uppdatering</span><span class="sxs-lookup"><span data-stu-id="47083-153">Update-script</span></span>](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[<span data-ttu-id="47083-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="47083-154">Get-Installedscript</span></span>](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[<span data-ttu-id="47083-155">UnInstall-script</span><span class="sxs-lookup"><span data-stu-id="47083-155">UnInstall-script</span></span>](./psget_uninstall-script.md)