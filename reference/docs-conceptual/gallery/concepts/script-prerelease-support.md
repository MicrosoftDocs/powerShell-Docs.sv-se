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
# <a name="prerelease-versions-of-scripts"></a>För hands versioner av skript

Från och med version 1.6.0, PowerShellGet och PowerShell-galleriet ge stöd för taggning av versioner som är större än 1.0.0 som en för hands version. Innan den här funktionen var för hands versions paket begränsade till att ha en version som börjar med 0. Syftet med dessa funktioner är att ge bättre stöd för [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) -versioner utan att bryta mot bakåtkompatibilitet med PowerShell-versionerna 3 och senare, eller befintliga versioner av PowerShellGet. Det här avsnittet fokuserar på de skriptbaserade funktionerna. Motsvarande funktioner för moduler finns i avsnittet versioner av för [hands versions](module-prerelease-support.md) moduler. Med hjälp av dessa funktioner kan utgivare identifiera ett skript som version 2.5.0-alpha och senare släppa en produktions klar versions 2.5.0 som ersätter för hands versionen.

På en hög nivå omfattar för hands versions skript funktionerna:

- Lägger till ett PrereleaseString-suffix till versions strängen i skript manifestet. När skripten publiceras till PowerShell-galleriet extraheras dessa data från manifestet och används för att identifiera för hands versions paket.
- Hämtning av för hands paket kräver att AllowPrerelease-flaggan läggs till i PowerShellGet-kommandona find-script, install-script, Update-script och Save-script. Om ingen flagga anges visas inte för hands versions paket.
- Skript versioner som visas med find-script, get-InstalledScript och i PowerShell-galleriet kommer att visas med PrereleaseString, som i 2.5.0-alpha.

Information om funktionerna finns nedan.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identifiera en skript version som en för hands version

PowerShellGet-stöd för för hands versioner är enklare för skript än moduler. Skript versions hantering stöds endast av PowerShellGet, så det finns inga kompatibilitetsproblem som orsakas om du lägger till för hands versions strängen. Om du vill identifiera ett skript i PowerShell-galleriet som en för hands version lägger du till ett för hands versions-suffix till en korrekt formaterad versions sträng i skriptets metadata.

Ett exempel avsnitt i ett skript manifest med en för hands version ser ut så här:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Om du vill använda ett för hands-suffix måste versions strängen uppfylla följande krav:

- Det går bara att ange ett för hands suffix när versionen är 3 segment för Major. minor. Build.
  Detta justeras med SemVer v-1.0.0
- För hands versionen av suffixet är en sträng som börjar med ett bindestreck och som kan innehålla ASCII-alfanumeriska tecken [0 – 9A-za-z-]
- Det finns bara stöd för SemVer v 1.0.0 för hands versions strängar för tillfället, så att för hands versionen **inte får** innehålla någon av perioderna eller + [. +], som tillåts i SemVer 2,0
- Exempel på PrereleaseString-strängar som stöds är:-alpha,-alpha1,-BETA,-update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>För hands versions påverkan på sorterings ordning och installationsfiler

Sorterings ordningen ändras när du använder en för hands version, vilket är viktigt när du publicerar till PowerShell-galleriet och när du installerar skript med PowerShellGet-kommandon. Om det finns två skript versioner med versions numret, baseras sorterings ordningen på sträng delen efter bindestrecket. Därför är version 2.5.0-alpha mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma. Om två skript har samma versions nummer, och endast en har en PrereleaseString, antas skriptet **utan** för hands versionen av suffixet vara produktions klara versionen och kommer att sorteras som en högre version än för hands versionen. Exempel: när du jämför releases 2.5.0 och 2.5.0 beta, betraktas 2.5.0-versionen som den större av de två.

När du publicerar till PowerShell-galleriet måste versionen av skriptet som publiceras ha en högre version än den tidigare publicerade versionen som finns i PowerShell-galleriet. En utgivare kan uppdatera version 2.5.0-alpha med 2.5.0-beta eller med 2.5.0 (utan för hands suffix).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Hitta och hämta för hands versions paket med PowerShellGet-kommandon

Hantering av för hands versioner av paket med PowerShellGet find-skript, install-skript, Update-script och Save-script-kommandon kräver att flaggan-AllowPrerelease läggs till. Om-AllowPrerelease har angetts inkluderas för hands paketen om de finns. Om-AllowPrerelease-flaggan inte anges visas inte för hands versions paket.

De enda undantagen till detta i PowerShellGet-skript kommandon är get-InstalledScript och vissa fall med Uninstall-script.

- Get-InstalledScript visar alltid för hands versions informationen automatiskt i versions strängen om den finns.
- Uninstall-skriptet avinstallerar som standard den senaste versionen av ett skript om **ingen version** har angetts. Beteendet har inte ändrats. Men om en för hands version anges med `-RequiredVersion`, krävs `-AllowPrerelease`.

## <a name="examples"></a>Exempel

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

Uninstall-skript tar bort den aktuella versionen av ett skript när-RequiredVersion inte anges.
IF-RequiredVersion anges, och är en för hands version,-AllowPrerelease måste läggas till i kommandot.

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

## <a name="more-details"></a>Mer information

- [Versioner av för hands versions modul](module-prerelease-support.md)
- [Sök – skript](/powershell/module/powershellget/find-script)
- [Installera – skript](/powershell/module/powershellget/install-script)
- [Spara – skript](/powershell/module/powershellget/save-script)
- [Uppdatera skript](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [Avinstallera – skript](/powershell/module/powershellget/uninstall-script)
