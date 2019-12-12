---
ms.date: 10/17/2017
contributor: keithb
keywords: Galleri, PowerShell, cmdlet, psget
title: För hands versioner av skript
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329178"
---
# <a name="prerelease-versions-of-scripts"></a><span data-ttu-id="603d9-103">För hands versioner av skript</span><span class="sxs-lookup"><span data-stu-id="603d9-103">Prerelease versions of scripts</span></span>

<span data-ttu-id="603d9-104">Från och med version 1.6.0, PowerShellGet och PowerShell-galleriet ge stöd för taggning av versioner som är större än 1.0.0 som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="603d9-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="603d9-105">Innan den här funktionen var för hands versions paket begränsade till att ha en version som börjar med 0.</span><span class="sxs-lookup"><span data-stu-id="603d9-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="603d9-106">Syftet med dessa funktioner är att ge bättre stöd för [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) -versioner utan att bryta mot bakåtkompatibilitet med PowerShell-versionerna 3 och senare, eller befintliga versioner av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="603d9-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="603d9-107">Det här avsnittet fokuserar på de skriptbaserade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="603d9-107">This topic focuses on the script-specific features.</span></span> <span data-ttu-id="603d9-108">Motsvarande funktioner för moduler finns i avsnittet versioner av för [hands versions](module-prerelease-support.md) moduler.</span><span class="sxs-lookup"><span data-stu-id="603d9-108">The equivalent features for modules are in the [Prerelease Module Versions](module-prerelease-support.md) topic.</span></span> <span data-ttu-id="603d9-109">Med hjälp av dessa funktioner kan utgivare identifiera ett skript som version 2.5.0-alpha och senare släppa en produktions klar versions 2.5.0 som ersätter för hands versionen.</span><span class="sxs-lookup"><span data-stu-id="603d9-109">Using these features, publishers can identify a script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="603d9-110">På en hög nivå omfattar för hands versions skript funktionerna:</span><span class="sxs-lookup"><span data-stu-id="603d9-110">At a high level, the prerelease script features include:</span></span>

- <span data-ttu-id="603d9-111">Lägger till ett PrereleaseString-suffix till versions strängen i skript manifestet.</span><span class="sxs-lookup"><span data-stu-id="603d9-111">Adding a PrereleaseString suffix to the version string in the script manifest.</span></span> <span data-ttu-id="603d9-112">När skripten publiceras till PowerShell-galleriet extraheras dessa data från manifestet och används för att identifiera för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="603d9-112">When the scripts is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="603d9-113">Hämtning av för hands paket kräver att AllowPrerelease-flaggan läggs till i PowerShellGet-kommandona find-script, install-script, Update-script och Save-script.</span><span class="sxs-lookup"><span data-stu-id="603d9-113">Acquiring prerelease packages requires adding -AllowPrerelease flag to the PowerShellGet commands Find-Script, Install-Script, Update-Script, and Save-Script.</span></span> <span data-ttu-id="603d9-114">Om ingen flagga anges visas inte för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="603d9-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="603d9-115">Skript versioner som visas med find-script, get-InstalledScript och i PowerShell-galleriet kommer att visas med PrereleaseString, som i 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="603d9-115">Script versions displayed by Find-Script, Get-InstalledScript, and in the PowerShell Gallery will be displayed with the PrereleaseString, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="603d9-116">Information om funktionerna finns nedan.</span><span class="sxs-lookup"><span data-stu-id="603d9-116">Details for the features are included below.</span></span>

## <a name="identifying-a-script-version-as-a-prerelease"></a><span data-ttu-id="603d9-117">Identifiera en skript version som en för hands version</span><span class="sxs-lookup"><span data-stu-id="603d9-117">Identifying a script version as a prerelease</span></span>

<span data-ttu-id="603d9-118">PowerShellGet-stöd för för hands versioner är enklare för skript än moduler.</span><span class="sxs-lookup"><span data-stu-id="603d9-118">PowerShellGet support for prerelease versions is easier for scripts than modules.</span></span> <span data-ttu-id="603d9-119">Skript versions hantering stöds endast av PowerShellGet, så det finns inga kompatibilitetsproblem som orsakas om du lägger till för hands versions strängen.</span><span class="sxs-lookup"><span data-stu-id="603d9-119">Script versioning is only supported by PowerShellGet, so there are no compatibility issues caused by adding the prerelease string.</span></span> <span data-ttu-id="603d9-120">Om du vill identifiera ett skript i PowerShell-galleriet som en för hands version lägger du till ett för hands versions-suffix till en korrekt formaterad versions sträng i skriptets metadata.</span><span class="sxs-lookup"><span data-stu-id="603d9-120">To identify a script in the PowerShell Gallery as a prerelease, add a prerelease suffix to a properly-formatted version string in the script metadata.</span></span>

<span data-ttu-id="603d9-121">Ett exempel avsnitt i ett skript manifest med en för hands version ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="603d9-121">An example section of a script manifest with a prerelease version would look like the following:</span></span>

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

<span data-ttu-id="603d9-122">Om du vill använda ett för hands-suffix måste versions strängen uppfylla följande krav:</span><span class="sxs-lookup"><span data-stu-id="603d9-122">To use a prerelease suffix, the version string must meet the following requirements:</span></span>

- <span data-ttu-id="603d9-123">Det går bara att ange ett för hands suffix när versionen är 3 segment för Major. minor. Build.</span><span class="sxs-lookup"><span data-stu-id="603d9-123">A prerelease suffix may only be specified when the Version is 3 segments for Major.Minor.Build.</span></span>
  <span data-ttu-id="603d9-124">Detta justeras med SemVer v-1.0.0</span><span class="sxs-lookup"><span data-stu-id="603d9-124">This aligns with SemVer v1.0.0</span></span>
- <span data-ttu-id="603d9-125">För hands versionen av suffixet är en sträng som börjar med ett bindestreck och som kan innehålla ASCII-alfanumeriska tecken [0 – 9A-za-z-]</span><span class="sxs-lookup"><span data-stu-id="603d9-125">The prerelease suffix is a string which begins with a hyphen, and may contain ASCII alphanumerics [0-9A-Za-z-]</span></span>
- <span data-ttu-id="603d9-126">Det finns bara stöd för SemVer v 1.0.0 för hands versions strängar för tillfället, så att för hands versionen **inte får** innehålla någon av perioderna eller + [. +], som tillåts i SemVer 2,0</span><span class="sxs-lookup"><span data-stu-id="603d9-126">Only SemVer v1.0.0 prerelease strings are supported at this time, so the prerelease suffix **must not** contain either period or + [.+], which are allowed in SemVer 2.0</span></span>
- <span data-ttu-id="603d9-127">Exempel på PrereleaseString-strängar som stöds är:-alpha,-alpha1,-BETA,-update20171020</span><span class="sxs-lookup"><span data-stu-id="603d9-127">Examples of supported PrereleaseString strings are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="603d9-128">För hands versions påverkan på sorterings ordning och installationsfiler</span><span class="sxs-lookup"><span data-stu-id="603d9-128">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="603d9-129">Sorterings ordningen ändras när du använder en för hands version, vilket är viktigt när du publicerar till PowerShell-galleriet och när du installerar skript med PowerShellGet-kommandon.</span><span class="sxs-lookup"><span data-stu-id="603d9-129">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing scripts using PowerShellGet commands.</span></span> <span data-ttu-id="603d9-130">Om det finns två skript versioner med versions numret, baseras sorterings ordningen på sträng delen efter bindestrecket.</span><span class="sxs-lookup"><span data-stu-id="603d9-130">If two scripts versions with the version number exist, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="603d9-131">Därför är version 2.5.0-alpha mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="603d9-131">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="603d9-132">Om två skript har samma versions nummer, och endast en har en PrereleaseString, antas skriptet **utan** för hands versionen av suffixet vara produktions klara versionen och kommer att sorteras som en högre version än för hands versionen.</span><span class="sxs-lookup"><span data-stu-id="603d9-132">If two scripts have the same version number, and only one has a PrereleaseString, the script **without** the prerelease suffix is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version.</span></span> <span data-ttu-id="603d9-133">Exempel: när du jämför releases 2.5.0 och 2.5.0 beta, betraktas 2.5.0-versionen som den större av de två.</span><span class="sxs-lookup"><span data-stu-id="603d9-133">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="603d9-134">När du publicerar till PowerShell-galleriet måste versionen av skriptet som publiceras ha en högre version än den tidigare publicerade versionen som finns i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="603d9-134">When publishing to the PowerShell Gallery, by default the version of the script being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span> <span data-ttu-id="603d9-135">En utgivare kan uppdatera version 2.5.0-alpha med 2.5.0-beta eller med 2.5.0 (utan för hands suffix).</span><span class="sxs-lookup"><span data-stu-id="603d9-135">A publisher may update version 2.5.0-alpha with 2.5.0-beta, or with 2.5.0 (with no prerelease suffix).</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="603d9-136">Hitta och hämta för hands versions paket med PowerShellGet-kommandon</span><span class="sxs-lookup"><span data-stu-id="603d9-136">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="603d9-137">Hantering av för hands versioner av paket med PowerShellGet find-skript, install-skript, Update-script och Save-script-kommandon kräver att flaggan-AllowPrerelease läggs till.</span><span class="sxs-lookup"><span data-stu-id="603d9-137">Dealing with prerelease packages using PowerShellGet Find-Script, Install-Script, Update-Script, and Save-Script commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="603d9-138">Om-AllowPrerelease har angetts inkluderas för hands paketen om de finns.</span><span class="sxs-lookup"><span data-stu-id="603d9-138">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="603d9-139">Om-AllowPrerelease-flaggan inte anges visas inte för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="603d9-139">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="603d9-140">De enda undantagen till detta i PowerShellGet-skript kommandon är get-InstalledScript och vissa fall med Uninstall-script.</span><span class="sxs-lookup"><span data-stu-id="603d9-140">The only exceptions to this in the PowerShellGet script commands are Get-InstalledScript, and some cases with Uninstall-Script.</span></span>

- <span data-ttu-id="603d9-141">Get-InstalledScript visar alltid för hands versions informationen automatiskt i versions strängen om den finns.</span><span class="sxs-lookup"><span data-stu-id="603d9-141">Get-InstalledScript always will automatically show the prerelease information in the version string if it is present.</span></span>
- <span data-ttu-id="603d9-142">Uninstall-skriptet avinstallerar som standard den senaste versionen av ett skript om **ingen version** har angetts.</span><span class="sxs-lookup"><span data-stu-id="603d9-142">Uninstall-Script will by default uninstall the most recent version of a script, if **no version** is specified.</span></span> <span data-ttu-id="603d9-143">Beteendet har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="603d9-143">That behavior has not changed.</span></span> <span data-ttu-id="603d9-144">Men om en för hands version anges med `-RequiredVersion`, krävs `-AllowPrerelease`.</span><span class="sxs-lookup"><span data-stu-id="603d9-144">However, if a prerelease version is specified using `-RequiredVersion`, `-AllowPrerelease` will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="603d9-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="603d9-145">Examples</span></span>

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
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
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage)[Find-Package], Exception
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

<span data-ttu-id="603d9-146">Uninstall-skript tar bort den aktuella versionen av ett skript när-RequiredVersion inte anges.</span><span class="sxs-lookup"><span data-stu-id="603d9-146">Uninstall-Script will remove the current version of a script when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="603d9-147">IF-RequiredVersion anges, och är en för hands version,-AllowPrerelease måste läggas till i kommandot.</span><span class="sxs-lookup"><span data-stu-id="603d9-147">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-script


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

## <a name="more-details"></a><span data-ttu-id="603d9-148">Mer information</span><span class="sxs-lookup"><span data-stu-id="603d9-148">More details</span></span>

- [<span data-ttu-id="603d9-149">Versioner av för hands versions modul</span><span class="sxs-lookup"><span data-stu-id="603d9-149">Prerelease Module Versions</span></span>](module-prerelease-support.md)
- [<span data-ttu-id="603d9-150">Sök – skript</span><span class="sxs-lookup"><span data-stu-id="603d9-150">Find-script</span></span>](/powershell/module/powershellget/find-script)
- [<span data-ttu-id="603d9-151">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="603d9-151">Install-script</span></span>](/powershell/module/powershellget/install-script)
- [<span data-ttu-id="603d9-152">Spara – skript</span><span class="sxs-lookup"><span data-stu-id="603d9-152">Save-script</span></span>](/powershell/module/powershellget/save-script)
- [<span data-ttu-id="603d9-153">Uppdatera skript</span><span class="sxs-lookup"><span data-stu-id="603d9-153">Update-script</span></span>](/powershell/module/powershellget/update-script)
- [<span data-ttu-id="603d9-154">Get-Installedscript</span><span class="sxs-lookup"><span data-stu-id="603d9-154">Get-Installedscript</span></span>](/powershell/module/powershellget/get-installedscript)
- [<span data-ttu-id="603d9-155">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="603d9-155">UnInstall-script</span></span>](/powershell/module/powershellget/uninstall-script)
