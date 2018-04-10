---
ms.date: 09/26/2017
contributor: keithb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: PrereleaseModule
ms.openlocfilehash: 1fc08cbba90e3eb8ca7d280e4d279af1d8aa279f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="prerelease-module-versions"></a>Förhandsversionen modulversioner
Från och med version 1.6.0 PowerShellGet och PowerShell-galleriet ger stöd för märkning versioner som är större än 1.0.0 som en förhandsversion. Innan den här funktionen har förhandsversionen begränsad till att ha en version som börjar med 0. Syftet med dessa funktioner är att ger större stöd för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konventionen utan att bryta bakåtkompatibilitet kompatibilitet med PowerShell version 3 och senare, eller befintliga versioner av PowerShellGet. Det här avsnittet fokuserar på modul-specifika funktioner. Motsvarande funktionerna för skript är i den [förhandsversion versioner av skript](../script/PrereleaseScript.md) avsnittet. Med hjälp av dessa funktioner, kan utgivare identifiera en modul eller ett skript som version 2.5.0-alpha och senare använda en produktionsklara version 2.5.0 som ersätter förhandsversionen.

På en hög nivå förhandsversionen modulen bland annat:

* Lägga till en förhandsversion sträng i avsnittet PSData i modulmanifestet identifierar modulen som en förhandsversion.
Om modulen har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversionen objekt.
* Hämta förhandsversionen objekt kräver att lägga till AllowPrerelease - flaggan i PowerShellGet kommandona Sök-modulen, installera modulen Update-modulen och spara modulen.
Om flaggan inte anges visas inte förhandsversionen objekt.
* Modulversioner som visas av Sök-modulen, Get-InstalledModule och i PowerShell-galleriet visas som en sträng med förhandsversionen strängen läggs som 2.5.0-alpha.

Information om funktionerna finns nedan.

De här ändringarna påverkar inte stöd för modulen-version som är inbyggd i PowerShell och är kompatibla med PowerShell 3.0 och 4.0 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identifierar en Modulversion som en förhandsversion

PowerShellGet stöd för förhandsversioner kräver användning av två fält i modulen Manifest:

* ModuleVersion som ingår i modulmanifestet måste vara en del 3 version om en förhandsversion används och måste vara kompatibel med befintliga PowerShell versionshantering. Formatet för version är A.B.C, där A, B och C är alla heltal.
* Förhandsversionen sträng har angetts i modulmanifestet i avsnittet PSData i PrivateData.
Detaljerade krav på förhandsversionen strängen är lägre än.

En exempel-avsnitt i en modulmanifest som definierar en modul som en förhandsversion skulle se ut ungefär så här:
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

Detaljerade krav för förhandsversionen sträng är:

* Förhandsversionen sträng kan endast anges när ModuleVersion är 3 segment för Major.Minor.Build. Detta justerar med SemVer v1.0.0.
* Ett bindestreck är avgränsaren mellan Build-nummer och förhandsversionen strängen. Ett bindestreck kan ingå som det första tecknet, endast i förhandsversionen strängen.
* Förhandsversionen strängen kan innehålla endast ASCII alfanumeriska tecken [0-9A-a - z-]. Det är bäst att börja förhandsutgåvan sträng med en bokstav, eftersom det är lättare att identifiera att det här är en förhandsversion när du skannar en lista med objekt.
* Endast SemVer v1.0.0 förhandsversionen strängar stöds just nu. Förhandsversionen sträng __får inte__ innehålla någon punkt eller + [. +], som är tillåtna i SemVer 2.0.
* Exempel på stöds förhandsversionen sträng är:-alfa, -á1,-BETA, -update20171020

__Förhandsversionen versionshantering inverkan på Sortera ordning och installation mappar__

Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar till PowerShell-galleriet, och när du installerar moduler med PowerShellGet kommandon.
Om förhandsversionen sträng har angetts för två moduler, utifrån sorteringsordning strängdelen följande bindestreck. Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma.
Om två moduler har samma ModuleVersion och bara har en förhandsversion sträng, modul utan förhandsversionen strängen antas vara klar för produktion-version och kommer att sorteras som en högre version än förhandsversionen (som inkluderar förhandsutgåvan sträng).
Exempelvis när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas större av båda.

När du publicerar till PowerShell-galleriet som standard måste versionen av modulen publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet.

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Söka efter och hämta förhandsversionen objekt med PowerShellGet kommandon

Om förhandsversionen objekt med PowerShellGet Sök-modulen, installera modulen Update-modulen och spara modulen kommandon kräver att lägga till flaggan - AllowPrerelease.
Om - AllowPrerelease anges inkluderas förhandsversionen objekt om de finns.
Om AllowPrerelease - flaggan inte anges visas inte förhandsversionen objekt.

De enda undantagen till den här i PowerShellGet modulen kommandon är Get-InstalledModule och ibland med Uninstall-modulen.

* Get-InstalledModule visas alltid automatiskt informationen om förhandsversionen i versionssträng för moduler.
* Avinstallera modulen som standard avinstalleras den senaste versionen av en modul om __ingen version__ har angetts. Att problemet inte har ändrats. Men om en förhandsversion anges med - RequiredVersion, måste - AllowPrerelease utföras.

## <a name="examples"></a>Exempel
```powershell
# Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha. If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> find-module TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

# To install a prerelease, always specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Sida-vid-sida-installation av versioner av en modul som skiljer sig bara på grund av förhandsversion som angetts stöds inte.
När du installerar en modul med PowerShellGet finns installerade sida-vid-sida genom att skapa en mapp med namnet med hjälp av ModuleVersion i olika versioner av samma modul.
ModuleVersion utan förhandsversionen strängen används för mappnamnet.
Om en användare installerar MyModule version 2.5.0-alpha, kommer att installeras i mappen MyModule\2.5.0.
Om användarna installerar sedan 2.5.0-beta, 2.5.0-beta version kommer __över skrivåtgärder__ innehållet i mappen MyModule\2.5.0.
En fördel med denna metod är att det finns inget behov av att avinstallera förhandsversionen när du har installerat versionen som klar för produktion.
Exemplet nedan visar vad som händer:


``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-beta     TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

```

Avinstallera modulen tar bort den senaste versionen av en modul när - RequiredVersion inte har angetts.
Om - RequiredVersion anges, och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

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

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
2.0.0-alpha1    TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.8.0           TestPackage                         PSGallery            Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage                         PSGallery            Package used to validate changes to the PowerShe...


```



## <a name="more-details"></a>Mer information
### <a name="prerelease-script-versionsscriptprereleasescriptmd"></a>[Förhandsversionen skript versioner](../script/PrereleaseScript.md)
### <a name="find-modulepsgetfind-modulemd"></a>[Sök-modul](./psget_find-module.md)
### <a name="install-modulepsgetinstall-modulemd"></a>[Installera modulen](./psget_install-module.md)
### <a name="save-modulepsgetsave-modulemd"></a>[Spara-modul](./psget_save-module.md)
### <a name="update-modulepsgetupdate-modulemd"></a>[Update-modul](./psget_update-module.md)
### <a name="get-installedmodulepsgetget-installedmodulemd"></a>[Get-InstalledModule](./psget_get-installedmodule.md)
### <a name="uninstall-modulepsgetuninstall-modulemd"></a>[UnInstall-Module](./psget_uninstall-module.md)