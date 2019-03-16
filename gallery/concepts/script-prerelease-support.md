---
ms.date: 10/17/2017
contributor: keithb
keywords: galleriet, powershell, cmdlet, psget
title: Förhandsversioner av skript
ms.openlocfilehash: c0198c2f575d2c004949ccebab49d93ce54716be
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055894"
---
# <a name="prerelease-versions-of-scripts"></a>Förhandsversioner av skript

Från och med version 1.6.0 eller senare, ger PowerShellGet och PowerShell-galleriet stöd för taggning versioner som är större än 1.0.0 som en förhandsversion. Innan den här funktionen var förhandsversioner paket begränsade till att ha en version som börjar med 0. Målet med de här funktionerna är att ge bättre support för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konvention utan att spräcka bakåtkompatibilitet kompatibilitet med PowerShell versioner 3 och senare, eller befintliga versioner av PowerShellGet. Det här avsnittet fokuserar på skript-specifika funktioner. Motsvarande funktioner för moduler finns i den [förhandsversion modulversioner](module-prerelease-support.md) avsnittet. Med dessa funktioner kan kan utgivare identifiera ett skript som version 2.5.0-alpha och senare använda en produktionsklar version 2.5.0 som ersätter förhandsversionen.

På en hög nivå omfattar förhandsversioner skript-funktioner:

- Lägga till ett PrereleaseString suffix till Versionsträngen i skriptet manifestet. Om skripten har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversioner paket.
- Hämta förhandsversionen paket kräver att lägga till AllowPrerelease - flaggan i PowerShellGet-kommandon Find-Script installationsskriptet, Update-skript och spara skriptet. Om flaggan inte anges, visas inte förhandsversioner paket.
- Skript-versioner som visas av Find-Script, Get-InstalledScript, och i PowerShell-galleriet visas med PrereleaseString, som i 2.5.0-alpha.

Information om funktionerna som ingår nedan.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identifierar en skriptversion som en förhandsversion

PowerShellGet-stöd för förhandsversioner är enklare än moduler för skript. Skriptet versionshantering stöds endast av PowerShellGet, så det finns inga kompatibilitetsproblem på grund av att lägga till strängen som förhandsversioner. Lägga till ett förhandsversioner suffix till en korrekt formaterad versionssträng i skriptmetadata för att identifiera ett skript i PowerShell-galleriet som en förhandsversion.

En exempel-avsnittet i ett skript-manifest med en förhandsversion som ser ut så här:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Om du vill använda ett förhandsversioner suffix måste Versionsträngen uppfylla följande krav:

- Förhandsversioner suffix kan bara anges när Version är 3 segment för Major.Minor.Build.
  Detta ligger i linje med SemVer v1.0.0
- Förhandsversioner suffixet är en sträng som börjar med ett bindestreck och får bestå av alfanumeriska ASCII-tecken [0-9A-a - z-]
- Endast SemVer v1.0.0 förhandsversioner strängar som stöds för tillfället så förhandsversioner suffixet **får inte** innehålla antingen punkt eller + [. +], som är tillåtna i SemVer 2.0
- Exempel på PrereleaseString strängar som stöds är:-alfa, -á1,-BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Förhandsversioner versionshantering påverkan på sortera ordningen och installationen mappar

Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar PowerShell-galleriet, och när du installerar skript med hjälp av PowerShellGet-kommandon. Om två skript versioner med versionsnumret finns, sorteringsordningen är baserad på strängdelen följa bindestreck. Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma. Om två skript har samma versionsnummer och bara har en PrereleaseString skriptet **utan** förhandsversioner suffixet antas vara produktionsklar version och kommer att sorteras som en högre version än förhandsutgåvan version. Till exempel när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas det som är störst av två.

När du publicerar PowerShell-galleriet, som standard måste versionen av skriptet publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet. Utgivare kan uppdatera version 2.5.0-alpha 2.5.0-beta eller med 2.5.0 (med inga förhandsversioner suffix).

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Att söka efter och hämta förhandsversioner paket med PowerShellGet-kommandon

Behandlar förhandsversioner paket med hjälp av PowerShellGet Find-Script, installationsskriptet, Update-skript och spara skriptkommandon kräver att lägga till flaggan - AllowPrerelease. Om - AllowPrerelease anges ska förhandsversioner paket inkluderas om de finns. Om - AllowPrerelease flaggan inte anges, visas inte förhandsversioner paket.

De enda undantagen till den här i skriptkommandon PowerShellGet är Get-InstalledScript och ibland med Uninstall-skript.

- Get-InstalledScript Visa alltid automatiskt informationen om förhandsversionen i Versionsträngen om den finns.
- Avinstallera skript som standard avinstalleras den senaste versionen av ett skript, om **ingen version** har angetts. Som standard har inte ändrats. Men om en förhandsversion kan anges med `-RequiredVersion`, `-AllowPrerelease` krävs.

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

Avinstallera skriptet tar bort den aktuella versionen av ett skript när - RequiredVersion inte har angetts.
Om - RequiredVersion har angetts och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.

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

- [Förhandsversioner modulversioner](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)
