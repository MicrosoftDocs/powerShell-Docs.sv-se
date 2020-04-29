---
ms.date: 09/26/2017
contributor: keithb
keywords: Galleri, PowerShell, cmdlet, psget
title: Versioner av för hands versions modul
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328940"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="2381b-103">Versioner av för hands versions modul</span><span class="sxs-lookup"><span data-stu-id="2381b-103">Prerelease Module Versions</span></span>

<span data-ttu-id="2381b-104">Från och med version 1.6.0, PowerShellGet och PowerShell-galleriet ge stöd för taggning av versioner som är större än 1.0.0 som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="2381b-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="2381b-105">Innan den här funktionen var för hands versions paket begränsade till att ha en version som börjar med 0.</span><span class="sxs-lookup"><span data-stu-id="2381b-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="2381b-106">Syftet med dessa funktioner är att ge bättre stöd för [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) -versioner utan att bryta mot bakåtkompatibilitet med PowerShell-versionerna 3 och senare, eller befintliga versioner av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="2381b-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="2381b-107">Det här avsnittet fokuserar på de modulerbaserade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="2381b-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="2381b-108">Motsvarande funktioner för skript finns i avsnittet [för hands versioner av skript](script-prerelease-support.md) .</span><span class="sxs-lookup"><span data-stu-id="2381b-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="2381b-109">Med hjälp av dessa funktioner kan utgivare identifiera en modul eller ett skript som version 2.5.0-alpha och senare släppa en produktions klar versions 2.5.0 som ersätter för hands versionen.</span><span class="sxs-lookup"><span data-stu-id="2381b-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="2381b-110">På en hög nivå inkluderar funktionerna för för hands versions modulen:</span><span class="sxs-lookup"><span data-stu-id="2381b-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="2381b-111">Om du lägger till en för hands versions sträng i avsnittet PSData i modulen manifest identifieras modulen som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="2381b-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="2381b-112">När modulen publiceras till PowerShell-galleriet extraheras dessa data från manifestet och används för att identifiera för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="2381b-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="2381b-113">För att hämta för hands paket måste `-AllowPrerelease` du lägga till flaggan i `Find-Module`PowerShellGet `Install-Module`- `Update-Module`kommandona `Save-Module`,, och.</span><span class="sxs-lookup"><span data-stu-id="2381b-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="2381b-114">Om ingen flagga anges visas inte för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="2381b-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="2381b-115">Modul versioner som visas `Find-Module`av `Get-InstalledModule`, och i PowerShell-galleriet, visas som en enskild sträng med för hands versions strängen, som i 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="2381b-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="2381b-116">Information om funktionerna finns nedan.</span><span class="sxs-lookup"><span data-stu-id="2381b-116">Details for the features are included below.</span></span>

<span data-ttu-id="2381b-117">Dessa ändringar påverkar inte den modulens versions stöd som är inbyggt i PowerShell och är kompatibelt med PowerShell 3,0, 4,0 och 5.</span><span class="sxs-lookup"><span data-stu-id="2381b-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="2381b-118">Identifiera en modulreferens som en för hands version</span><span class="sxs-lookup"><span data-stu-id="2381b-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="2381b-119">PowerShellGet-stöd för för hands versioner kräver att två fält används i manifestet för modulen:</span><span class="sxs-lookup"><span data-stu-id="2381b-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="2381b-120">ModuleVersion som ingår i modulens manifest måste vara en 3-del-version om en för hands version används och måste vara kompatibel med befintliga PowerShell-versioner.</span><span class="sxs-lookup"><span data-stu-id="2381b-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="2381b-121">Versions formatet är A. B. C, där A, B och C är alla heltal.</span><span class="sxs-lookup"><span data-stu-id="2381b-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="2381b-122">För hands versions strängen anges i modulens manifest i avsnittet PSData i PrivateData.</span><span class="sxs-lookup"><span data-stu-id="2381b-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="2381b-123">Detaljerade krav för för hands versions strängen finns nedan.</span><span class="sxs-lookup"><span data-stu-id="2381b-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="2381b-124">Ett exempel avsnitt i ett modul manifest som definierar en modul som en för hands version ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="2381b-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="2381b-125">De detaljerade kraven för för hands versions strängen är:</span><span class="sxs-lookup"><span data-stu-id="2381b-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="2381b-126">För hands versions strängen får bara anges när ModuleVersion är 3 segment för Major. minor. Build.</span><span class="sxs-lookup"><span data-stu-id="2381b-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="2381b-127">Detta justeras med SemVer v-1.0.0.</span><span class="sxs-lookup"><span data-stu-id="2381b-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="2381b-128">Ett bindestreck är avgränsaren mellan build-numret och för hands versions strängen.</span><span class="sxs-lookup"><span data-stu-id="2381b-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="2381b-129">Ett bindestreck kan ingå i för hands versionen-strängen som första tecken.</span><span class="sxs-lookup"><span data-stu-id="2381b-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="2381b-130">För hands versions strängen får bara innehålla ASCII-alfanumeriska tecken [0 – 9A-za-z-].</span><span class="sxs-lookup"><span data-stu-id="2381b-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="2381b-131">Det är en bra idé att starta en för hands versions sträng med ett alfa tecken, eftersom det blir lättare att identifiera att det här är en för hands version när en lista över paket genomsöks.</span><span class="sxs-lookup"><span data-stu-id="2381b-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="2381b-132">Endast SemVer v 1.0.0 för hands versions strängar stöds för tillfället.</span><span class="sxs-lookup"><span data-stu-id="2381b-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="2381b-133">För hands versions strängen **får inte** innehålla någon av perioderna eller + [. +], som tillåts i SemVer 2,0.</span><span class="sxs-lookup"><span data-stu-id="2381b-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="2381b-134">Exempel på en för hands versions sträng som stöds är:-alpha,-alpha1,-BETA,-update20171020</span><span class="sxs-lookup"><span data-stu-id="2381b-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="2381b-135">För hands versions påverkan på sorterings ordning och installationsfiler</span><span class="sxs-lookup"><span data-stu-id="2381b-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="2381b-136">Sorterings ordningen ändras när du använder en för hands version, vilket är viktigt när du publicerar till PowerShell-galleriet och när du installerar moduler med PowerShellGet-kommandon.</span><span class="sxs-lookup"><span data-stu-id="2381b-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="2381b-137">Om för hands versions strängen har angetts för två moduler baseras sorterings ordningen på sträng delen efter bindestrecket.</span><span class="sxs-lookup"><span data-stu-id="2381b-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="2381b-138">Därför är version 2.5.0-alpha mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="2381b-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="2381b-139">Om två moduler har samma ModuleVersion och endast en har en för hands versions sträng antas modulen utan för hands versionen vara den produktions färdiga versionen och kommer att sorteras som en högre version än för hands versionen (som innehåller för hands versions strängen).</span><span class="sxs-lookup"><span data-stu-id="2381b-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="2381b-140">Exempel: när du jämför releases 2.5.0 och 2.5.0 beta, betraktas 2.5.0-versionen som den större av de två.</span><span class="sxs-lookup"><span data-stu-id="2381b-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="2381b-141">När du publicerar till PowerShell-galleriet måste versionen av modulen som publiceras ha en högre version än den tidigare publicerade versionen som finns i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="2381b-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="2381b-142">Hitta och hämta för hands versions paket med PowerShellGet-kommandon</span><span class="sxs-lookup"><span data-stu-id="2381b-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="2381b-143">Hantering av för hands versioner av paket med hjälp av PowerShellGet find-modul, install-module, Update-module och Save-module kräver att flaggan-AllowPrerelease läggs till.</span><span class="sxs-lookup"><span data-stu-id="2381b-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="2381b-144">Om-AllowPrerelease har angetts inkluderas för hands paketen om de finns.</span><span class="sxs-lookup"><span data-stu-id="2381b-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="2381b-145">Om-AllowPrerelease-flaggan inte anges visas inte för hands versions paket.</span><span class="sxs-lookup"><span data-stu-id="2381b-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="2381b-146">De enda undantagen till detta i PowerShellGet-modulens kommandon är get-InstalledModule och vissa fall med Uninstall-module.</span><span class="sxs-lookup"><span data-stu-id="2381b-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="2381b-147">Get-InstalledModule visar alltid för hands versions informationen automatiskt i versions strängen för moduler.</span><span class="sxs-lookup"><span data-stu-id="2381b-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="2381b-148">Avinstallera-modulen avinstallerar som standard den senaste versionen av en modul, om __ingen version__ har angetts.</span><span class="sxs-lookup"><span data-stu-id="2381b-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="2381b-149">Beteendet har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="2381b-149">That behavior has not changed.</span></span> <span data-ttu-id="2381b-150">Men om en för hands version anges med-RequiredVersion, krävs-AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="2381b-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="2381b-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="2381b-151">Examples</span></span>

<span data-ttu-id="2381b-152">Anta att PowerShell-galleriet har TestPackage-1.8.0 och 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="2381b-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="2381b-153">Om `-AllowPrerelease` inte anges returneras endast version 1.8.0.</span><span class="sxs-lookup"><span data-stu-id="2381b-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="2381b-154">Om du vill installera en för hands version ska du alltid ange-AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="2381b-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="2381b-155">Det räcker inte att ange en för hands versions sträng.</span><span class="sxs-lookup"><span data-stu-id="2381b-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="2381b-156">Föregående kommando misslyckades eftersom-AllowPrerelease inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="2381b-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="2381b-157">Att `-AllowPrerelease` lägga till leder till att det lyckas.</span><span class="sxs-lookup"><span data-stu-id="2381b-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="2381b-158">Installation sida vid sida av versioner av en modul som bara skiljer sig på grund av den angivna för hands versionen stöds inte.</span><span class="sxs-lookup"><span data-stu-id="2381b-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="2381b-159">När du installerar en modul med PowerShellGet installeras olika versioner av samma modul sida vid sida genom att skapa ett mappnamn med hjälp av ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="2381b-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="2381b-160">ModuleVersion, utan för hands versions strängen, används för mappnamnet.</span><span class="sxs-lookup"><span data-stu-id="2381b-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="2381b-161">Om en användare installerar modulen version 2.5.0-alpha installeras den i `MyModule\2.5.0` mappen.</span><span class="sxs-lookup"><span data-stu-id="2381b-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="2381b-162">Om användaren sedan installerar 2.5.0-beta kommer 2.5.0-Beta-versionen **skriva över** innehållet i mappen `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="2381b-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="2381b-163">En fördel med den här metoden är att det inte är nödvändigt att avinstallera för hands versionen när du har installerat produktions klara versioner.</span><span class="sxs-lookup"><span data-stu-id="2381b-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="2381b-164">Exemplet nedan visar vad som förväntas:</span><span class="sxs-lookup"><span data-stu-id="2381b-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="2381b-165">Uninstall-modulen tar bort den senaste versionen av en modul när-RequiredVersion inte anges.</span><span class="sxs-lookup"><span data-stu-id="2381b-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="2381b-166">IF-RequiredVersion anges, och är en för hands version,-AllowPrerelease måste läggas till i kommandot.</span><span class="sxs-lookup"><span data-stu-id="2381b-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="2381b-167">Mer information</span><span class="sxs-lookup"><span data-stu-id="2381b-167">More details</span></span>

- [<span data-ttu-id="2381b-168">För hands versions skript versioner</span><span class="sxs-lookup"><span data-stu-id="2381b-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="2381b-169">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="2381b-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="2381b-170">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="2381b-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="2381b-171">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="2381b-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="2381b-172">Update-modul</span><span class="sxs-lookup"><span data-stu-id="2381b-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="2381b-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="2381b-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="2381b-174">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="2381b-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
