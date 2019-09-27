---
ms.date: 09/26/2017
contributor: keithb
keywords: Galleri, PowerShell, cmdlet, psget
title: Versioner av för hands versions modul
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328940"
---
# <a name="prerelease-module-versions"></a>Versioner av för hands versions modul

Från och med version 1.6.0, PowerShellGet och PowerShell-galleriet ge stöd för taggning av versioner som är större än 1.0.0 som en för hands version. Innan den här funktionen var för hands versions paket begränsade till att ha en version som börjar med 0. Syftet med dessa funktioner är att ge bättre stöd för [SemVer v 1.0.0](http://semver.org/spec/v1.0.0.html) -versioner utan att bryta mot bakåtkompatibilitet med PowerShell-versionerna 3 och senare, eller befintliga versioner av PowerShellGet. Det här avsnittet fokuserar på de modulerbaserade funktionerna. Motsvarande funktioner för skript finns i avsnittet [för hands versioner av skript](script-prerelease-support.md) . Med hjälp av dessa funktioner kan utgivare identifiera en modul eller ett skript som version 2.5.0-alpha och senare släppa en produktions klar versions 2.5.0 som ersätter för hands versionen.

På en hög nivå inkluderar funktionerna för för hands versions modulen:

- Om du lägger till en för hands versions sträng i avsnittet PSData i modulen manifest identifieras modulen som en för hands version. När modulen publiceras till PowerShell-galleriet extraheras dessa data från manifestet och används för att identifiera för hands versions paket.
- För att hämta för hands paket måste `-AllowPrerelease` du lägga till flaggan i `Find-Module`PowerShellGet `Install-Module`- `Update-Module`kommandona `Save-Module`,, och. Om ingen flagga anges visas inte för hands versions paket.
- Modul versioner som visas `Find-Module`av `Get-InstalledModule`, och i PowerShell-galleriet, visas som en enskild sträng med för hands versions strängen, som i 2.5.0-alpha.

Information om funktionerna finns nedan.

Dessa ändringar påverkar inte den modulens versions stöd som är inbyggt i PowerShell och är kompatibelt med PowerShell 3,0, 4,0 och 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identifiera en modulreferens som en för hands version

PowerShellGet-stöd för för hands versioner kräver att två fält används i manifestet för modulen:

- ModuleVersion som ingår i modulens manifest måste vara en 3-del-version om en för hands version används och måste vara kompatibel med befintliga PowerShell-versioner. Versions formatet är A. B. C, där A, B och C är alla heltal.
- För hands versions strängen anges i modulens manifest i avsnittet PSData i PrivateData.

Detaljerade krav för för hands versions strängen finns nedan.

Ett exempel avsnitt i ett modul manifest som definierar en modul som en för hands version ser ut så här:

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

De detaljerade kraven för för hands versions strängen är:

- För hands versions strängen får bara anges när ModuleVersion är 3 segment för Major. minor. Build. Detta justeras med SemVer v-1.0.0.
- Ett bindestreck är avgränsaren mellan build-numret och för hands versions strängen. Ett bindestreck kan ingå i för hands versionen-strängen som första tecken.
- För hands versions strängen får bara innehålla ASCII-alfanumeriska tecken [0 – 9A-za-z-]. Det är en bra idé att starta en för hands versions sträng med ett alfa tecken, eftersom det blir lättare att identifiera att det här är en för hands version när en lista över paket genomsöks.
- Endast SemVer v 1.0.0 för hands versions strängar stöds för tillfället. För hands versions strängen **får inte** innehålla någon av perioderna eller + [. +], som tillåts i SemVer 2,0.
- Exempel på en för hands versions sträng som stöds är:-alpha,-alpha1,-BETA,-update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>För hands versions påverkan på sorterings ordning och installationsfiler

Sorterings ordningen ändras när du använder en för hands version, vilket är viktigt när du publicerar till PowerShell-galleriet och när du installerar moduler med PowerShellGet-kommandon. Om för hands versions strängen har angetts för två moduler baseras sorterings ordningen på sträng delen efter bindestrecket. Därför är version 2.5.0-alpha mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma. Om två moduler har samma ModuleVersion och endast en har en för hands versions sträng antas modulen utan för hands versionen vara den produktions färdiga versionen och kommer att sorteras som en högre version än för hands versionen (som innehåller för hands versionen sträng). Exempel: när du jämför releases 2.5.0 och 2.5.0 beta, betraktas 2.5.0-versionen som den större av de två.

När du publicerar till PowerShell-galleriet måste versionen av modulen som publiceras ha en högre version än den tidigare publicerade versionen som finns i PowerShell-galleriet.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Hitta och hämta för hands versions paket med PowerShellGet-kommandon

Hantering av för hands versioner av paket med hjälp av PowerShellGet find-modul, install-module, Update-module och Save-module kräver att flaggan-AllowPrerelease läggs till. Om-AllowPrerelease har angetts inkluderas för hands paketen om de finns. Om-AllowPrerelease-flaggan inte anges visas inte för hands versions paket.

De enda undantagen till detta i PowerShellGet-modulens kommandon är get-InstalledModule och vissa fall med Uninstall-module.

- Get-InstalledModule visar alltid för hands versions informationen automatiskt i versions strängen för moduler.
- Avinstallera-modulen avinstallerar som standard den senaste versionen av en modul, om __ingen version__ har angetts. Beteendet har inte ändrats. Men om en för hands version anges med-RequiredVersion, krävs-AllowPrerelease.

## <a name="examples"></a>Exempel

Anta att PowerShell-galleriet har TestPackage-1.8.0 och 1.9.0-alpha. Om `-AllowPrerelease` inte anges returneras endast version 1.8.0.

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

Om du vill installera en för hands version ska du alltid ange-AllowPrerelease. Det räcker inte att ange en för hands versions sträng.

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

Föregående kommando misslyckades eftersom-AllowPrerelease inte har angetts. Att `-AllowPrerelease` lägga till leder till att det lyckas.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Installation sida vid sida av versioner av en modul som bara skiljer sig på grund av den angivna för hands versionen stöds inte. När du installerar en modul med PowerShellGet installeras olika versioner av samma modul sida vid sida genom att skapa ett mappnamn med hjälp av ModuleVersion. ModuleVersion, utan för hands versions strängen, används för mappnamnet. Om en användare installerar modulen version 2.5.0-alpha installeras den i `MyModule\2.5.0` mappen. Om användaren sedan installerar 2.5.0-beta kommer 2.5.0-Beta-versionen **skriva över** innehållet i mappen `MyModule\2.5.0`. En fördel med den här metoden är att det inte är nödvändigt att avinstallera för hands versionen när du har installerat produktions klara versioner. Exemplet nedan visar vad som förväntas:

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

Uninstall-modulen tar bort den senaste versionen av en modul när-RequiredVersion inte anges.
IF-RequiredVersion anges, och är en för hands version,-AllowPrerelease måste läggas till i kommandot.

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

## <a name="more-details"></a>Mer information

- [För hands versions skript versioner](script-prerelease-support.md)
- [Sök-modul](/powershell/module/powershellget/find-module)
- [Installera-modul](/powershell/module/powershellget/install-module)
- [Spara-modul](/powershell/module/powershellget/save-module)
- [Update-modul](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [Avinstallera-modul](/powershell/module/powershellget/uninstall-module)
