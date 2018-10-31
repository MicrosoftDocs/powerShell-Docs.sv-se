---
ms.date: 09/26/2017
contributor: keithb
keywords: galleriet, powershell, cmdlet, psget
title: Förhandsversioner modulversioner
ms.openlocfilehash: f58b5adfeba7ed06d231c76accbd52508c7d67d6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002777"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="a3e1a-103">Förhandsversioner modulversioner</span><span class="sxs-lookup"><span data-stu-id="a3e1a-103">Prerelease Module Versions</span></span>

<span data-ttu-id="a3e1a-104">Från och med version 1.6.0 eller senare, ger PowerShellGet och PowerShell-galleriet stöd för taggning versioner som är större än 1.0.0 som en förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="a3e1a-105">Innan den här funktionen var förhandsversioner paket begränsade till att ha en version som börjar med 0.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="a3e1a-106">Målet med de här funktionerna är att ge bättre support för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konvention utan att spräcka bakåtkompatibilitet kompatibilitet med PowerShell versioner 3 och senare, eller befintliga versioner av PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="a3e1a-107">Det här avsnittet fokuserar på modulen-specifika funktioner.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="a3e1a-108">Motsvarande funktioner för skript finns i den [förhandsversion versioner av skript](script-prerelease-support.md) avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="a3e1a-109">Med dessa funktioner kan kan utgivare identifiera en modul eller ett skript som version 2.5.0-alpha och senare använda en produktionsklar version 2.5.0 som ersätter förhandsversionen.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="a3e1a-110">På en hög nivå omfattar förhandsversioner modulfunktioner:</span><span class="sxs-lookup"><span data-stu-id="a3e1a-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="a3e1a-111">Att lägga till en sträng som förhandsversion i avsnittet PSData i modulmanifestet identifierar modulen som en förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="a3e1a-112">Om modulen har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversioner paket.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="a3e1a-113">Hämta förhandsversionen paket kräver att lägga till `-AllowPrerelease` flaggan för PowerShellGet-kommandon `Find-Module`, `Install-Module`, `Update-Module`, och `Save-Module`.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="a3e1a-114">Om flaggan inte anges, visas inte förhandsversioner paket.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="a3e1a-115">Modulversionerna som visas av `Find-Module`, `Get-InstalledModule`, och i PowerShell-galleriet visas som en sträng med förhandsversioner strängen läggs, som i 2.5.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="a3e1a-116">Information om funktionerna som ingår nedan.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-116">Details for the features are included below.</span></span>

<span data-ttu-id="a3e1a-117">De här ändringarna påverkar inte stöd för policymodul-version som är inbyggd i PowerShell och är kompatibla med PowerShell 3.0 och 4.0 5.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="a3e1a-118">Identifierar en Modulversion som en förhandsversion</span><span class="sxs-lookup"><span data-stu-id="a3e1a-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="a3e1a-119">PowerShellGet-stöd för förhandsversioner kräver användning av två fält i modulen Manifest:</span><span class="sxs-lookup"><span data-stu-id="a3e1a-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="a3e1a-120">ModuleVersion som ingår i modulmanifestet måste vara en 3 delar om en förhandsversion används och måste vara kompatibel med befintliga PowerShell-versionshantering.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="a3e1a-121">Formatet version är A.B.C, där A, B och C är alla heltal.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="a3e1a-122">Förhandsversioner strängen har angetts i modulmanifestet i avsnittet PSData i PrivateData.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="a3e1a-123">Detaljerade krav på förhandsversioner strängen finns nedan.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="a3e1a-124">En exempel-avsnitt i ett modulmanifest som definierar en modul som en förhandsversion skulle se ut så här:</span><span class="sxs-lookup"><span data-stu-id="a3e1a-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

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

<span data-ttu-id="a3e1a-125">Villkoren för förhandsversioner sträng är:</span><span class="sxs-lookup"><span data-stu-id="a3e1a-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="a3e1a-126">Förhandsversioner sträng kan bara anges när ModuleVersion är 3 segment för Major.Minor.Build.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="a3e1a-127">Detta ligger i linje med SemVer v1.0.0.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="a3e1a-128">Ett bindestreck är avgränsare mellan Build-nummer och förhandsversioner strängen.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="a3e1a-129">Ett bindestreck kan ingå i förhandsversioner strängen som det första tecknet, endast.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="a3e1a-130">Förhandsversioner strängen kan innehålla endast ASCII alfanumeriska tecken [0-9A-a - z-].</span><span class="sxs-lookup"><span data-stu-id="a3e1a-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="a3e1a-131">Det är en bra idé att börja förhandsutgåvan sträng med en bokstav, eftersom det är lättare att identifiera att detta är en förhandsversion när du skannar en lista över paket.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="a3e1a-132">Endast SemVer v1.0.0 förhandsversioner strängar stöds just nu.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="a3e1a-133">Förhandsversioner sträng **får inte** innehålla antingen punkt eller + [. +], som är tillåtna i SemVer 2.0.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="a3e1a-134">Exempel på stöds förhandsversioner sträng är:-alfa, -á1,-BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="a3e1a-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="a3e1a-135">Förhandsversioner versionshantering påverkan på sortera ordningen och installationen mappar</span><span class="sxs-lookup"><span data-stu-id="a3e1a-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="a3e1a-136">Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar PowerShell-galleriet, och när du installerar moduler med PowerShellGet-kommandon.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="a3e1a-137">Om förhandsversioner strängen har angetts för två moduler, utifrån sorteringsordningen strängdelen följa bindestreck.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="a3e1a-138">Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="a3e1a-139">Om två moduler som har samma ModuleVersion och bara har en förhandsversion sträng, modul utan förhandsversioner strängen antas vara produktionsklar version och kommer att sorteras som en högre version än förhandsversionen (som innehåller förhandsutgåvan sträng).</span><span class="sxs-lookup"><span data-stu-id="a3e1a-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="a3e1a-140">Till exempel när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas det som är störst av två.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="a3e1a-141">När du publicerar PowerShell-galleriet, som standard måste versionen av modulen publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="a3e1a-142">Att söka efter och hämta förhandsversioner paket med PowerShellGet-kommandon</span><span class="sxs-lookup"><span data-stu-id="a3e1a-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="a3e1a-143">Behandlar förhandsversioner paket med hjälp av Sök-modulen PowerShellGet i Install-Module, Update-modulen och Save-Module kommandon kräver att lägga till flaggan - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="a3e1a-144">Om - AllowPrerelease anges ska förhandsversioner paket inkluderas om de finns.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="a3e1a-145">Om - AllowPrerelease flaggan inte anges, visas inte förhandsversioner paket.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="a3e1a-146">De enda undantagen till den här i modulen PowerShellGet-kommandon är Get-InstalledModule och ibland med Uninstall-modulen.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="a3e1a-147">Get-InstalledModule Visa alltid automatiskt informationen om förhandsversionen i versionssträng för moduler.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="a3e1a-148">Avinstallera modulen som standard avinstalleras den senaste versionen av en modul om __ingen version__ har angetts.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="a3e1a-149">Som standard har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-149">That behavior has not changed.</span></span> <span data-ttu-id="a3e1a-150">Men om en förhandsversion kan anges med - RequiredVersion, måste - AllowPrerelease utföras.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="a3e1a-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="a3e1a-151">Examples</span></span>

<span data-ttu-id="a3e1a-152">Anta att PowerShell-galleriet har TestPackage modulversionerna 1.8.0 och 1.9.0-alpha.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="a3e1a-153">Om `-AllowPrerelease` är inte anges endast version 1.8.0 ska returneras.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

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

<span data-ttu-id="a3e1a-154">Om du vill installera en förhandsversion, alltid ange - AllowPrerelease.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="a3e1a-155">Det räcker inte att ange en sträng i förhandsversion.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-155">Specifying a prerelease version string is not sufficient.</span></span>

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

<span data-ttu-id="a3e1a-156">Det föregående kommandot misslyckades eftersom - AllowPrerelease inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="a3e1a-157">Att lägga till `-AllowPrerelease` leder till framgång.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="a3e1a-158">Sida-vid-sida-installation av av en modul som skiljer sig bara på grund av förhandsutgåvan angetts stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="a3e1a-159">När du installerar en modul med PowerShellGet, finns olika versioner av samma modul installerade sida-vid-sida genom att skapa en mapp med namnet med hjälp av ModuleVersion.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="a3e1a-160">ModuleVersion utan förhandsversioner strängen används för mappnamnet.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="a3e1a-161">Om en användare installerar MyModule version 2.5.0-alpha, installeras den till den `MyModule\2.5.0` mapp.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="a3e1a-162">Om användaren installerar sedan 2.5.0-beta, 2.5.0-beta version kommer **skriva över** innehållet i mappen `MyModule\2.5.0`.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="a3e1a-163">En fördel med den här metoden är att det finns inget behov av att avinstallera förhandsversionen när du har installerat produktionsklar version.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="a3e1a-164">Exemplet nedan visar vad som händer:</span><span class="sxs-lookup"><span data-stu-id="a3e1a-164">The example below shows what to expect:</span></span>

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

<span data-ttu-id="a3e1a-165">Avinstallera modulen tar bort den senaste versionen av en modul när - RequiredVersion inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="a3e1a-166">Om - RequiredVersion har angetts och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

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
+ Unnstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-Module

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

## <a name="more-details"></a><span data-ttu-id="a3e1a-167">Mer information</span><span class="sxs-lookup"><span data-stu-id="a3e1a-167">More details</span></span>

- [<span data-ttu-id="a3e1a-168">Förhandsversioner skriptet versioner</span><span class="sxs-lookup"><span data-stu-id="a3e1a-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="a3e1a-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="a3e1a-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="a3e1a-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="a3e1a-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="a3e1a-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="a3e1a-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="a3e1a-172">Uppdatera modulen</span><span class="sxs-lookup"><span data-stu-id="a3e1a-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="a3e1a-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a3e1a-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="a3e1a-174">Avinstallera modulen</span><span class="sxs-lookup"><span data-stu-id="a3e1a-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
