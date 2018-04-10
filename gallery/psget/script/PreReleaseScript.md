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
# <a name="prerelease-versions-of-scripts"></a>Förhandsversioner av skript

Från och med version 1.6.0 PowerShellGet och PowerShell-galleriet ger stöd för märkning versioner som är större än 1.0.0 som en förhandsversion. Innan den här funktionen har förhandsversionen begränsad till att ha en version som börjar med 0. Syftet med dessa funktioner är att ger större stöd för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konventionen utan att bryta bakåtkompatibilitet kompatibilitet med PowerShell version 3 och senare, eller befintliga versioner av PowerShellGet.
Det här avsnittet fokuserar på skript-specifika funktioner. Motsvarande funktionerna för moduler är i den [förhandsversion modulversioner](../module/PrereleaseModule.md) avsnittet. Med hjälp av dessa funktioner, kan utgivare identifiera ett skript som version 2.5.0-alpha och senare använda en produktionsklara version 2.5.0 som ersätter förhandsversionen.

På en hög nivå förhandsversionen skript bland annat:

* Lägger till ett PrereleaseString suffix Versionsträngen i manifestet skript.
Om skripten har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversionen objekt.
* Hämta förhandsversionen objekt kräver att lägga till AllowPrerelease - flaggan i PowerShellGet kommandona Sök-skript, installationsskriptet, Update-skript och spara-skript.
Om flaggan inte anges visas inte förhandsversionen objekt.
* Skript-versioner som visas av Sök-skriptet, Get-InstalledScript och i PowerShell-galleriet visas med PrereleaseString som 2.5.0-alpha.

Information om funktionerna finns nedan.


## <a name="identifying-a-script-version-as-a-prerelease"></a>Identifierar en skriptversion som en förhandsversion

PowerShellGet stöd för förhandsversioner är enklare än moduler för skript.
Skriptet versionshantering stöds endast av PowerShellGet, så att det finns inga problem på grund av att lägga till förhandsversionen strängen.
Lägga till ett förhandsversionen suffix till en korrekt formaterad versionssträng i skriptmetadata för för att identifiera ett skript i PowerShell-galleriet som en förhandsversion.

En exempeldelen av ett manifest för skript med en förhandsversion ser ut som följande:
```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>

```

Om du vill använda förhandsversionen suffix måste Versionsträngen uppfylla följande krav:

* Ett förhandsversionen suffix kan endast anges när versionen är 3 segment för Major.Minor.Build. Detta justerar med SemVer v1.0.0
* Suffixet förhandsversionen är en sträng som börjar med ett bindestreck och får bestå av alfanumeriska ASCII-tecken [0-9A-a - z-]
* Endast SemVer v1.0.0 förhandsversionen strängar stöds just nu, så suffixet förhandsversionen __får inte__ innehålla någon punkt eller + [. +], som är tillåtna i SemVer 2.0
* Exempel på PrereleaseString strängar som stöds är:-alfa, -á1,-BETA, -update20171020

__Förhandsversionen versionshantering inverkan på Sortera ordning och installation mappar__

Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar till PowerShell-galleriet, och när du installerar skript med hjälp av PowerShellGet kommandon.
Om två skript versioner med versionsnumret finns, sorteringsordningen är baserad på strängdelen efter bindestreck. Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.
Om två skript har samma versionsnummer och bara har en PrereleaseString skriptet __utan__ suffixet förhandsversionen antas vara klar för produktion-version och sorteras som en högre version än förhandsutgåvan version.
Exempelvis när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas större av båda.

När du publicerar till PowerShell-galleriet som standard måste versionen av skriptet publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet.
En utgivare kan uppdatera version 2.5.0-alpha 2.5.0-beta eller med 2.5.0 (med inga förhandsversionen suffix).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Söka efter och hämta förhandsversionen objekt med PowerShellGet kommandon

Om förhandsversionen objekt med hjälp av PowerShellGet Sök-skript, installationsskriptet, Update-skript och spara skriptkommandon kräver att lägga till flaggan - AllowPrerelease.
Om - AllowPrerelease anges inkluderas förhandsversionen objekt om de finns.
Om AllowPrerelease - flaggan inte anges visas inte förhandsversionen objekt.

De enda undantagen till den här i skriptkommandon PowerShellGet är Get-InstalledScript och ibland med Uninstall-skript.

* Get-InstalledScript visas alltid automatiskt informationen om förhandsversionen i Versionsträngen om den finns.
* Avinstallera skript som standard avinstalleras den senaste versionen av ett skript om __ingen version__ har angetts. Att problemet inte har ändrats. Men om en förhandsversion anges med - RequiredVersion, måste - AllowPrerelease utföras.

## <a name="examples"></a>Exempel
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

Avinstallera skriptet tar bort den aktuella versionen av ett skript när - RequiredVersion inte har angetts.
Om - RequiredVersion anges, och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.

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



## <a name="more-details"></a>Mer information
### <a name="prerelease-module-versionsmoduleprereleasemodulemd"></a>[Förhandsversionen modulversioner](../module/PrereleaseModule.md)
### <a name="find-scriptpsgetfind-scriptmd"></a>[Sök-skript](./psget_find-script.md)
### <a name="install-scriptpsgetinstall-scriptmd"></a>[Skriptet för installationen](./psget_install-script.md)
### <a name="save-scriptpsgetsave-scriptmd"></a>[Spara skriptet](./psget_save-script.md)
### <a name="update-scriptpsgetupdate-scriptmd"></a>[Skript för uppdatering](./psget_update-script.md)
### <a name="get-installedscriptpsgetget-installedscriptmd"></a>[Get-Installedscript](./psget_get-installedscript.md)
### <a name="uninstall-scriptpsgetuninstall-scriptmd"></a>[UnInstall-script](./psget_uninstall-script.md)