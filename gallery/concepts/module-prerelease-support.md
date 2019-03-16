---
ms.date: 09/26/2017
contributor: keithb
keywords: galleriet, powershell, cmdlet, psget
title: Förhandsversioner modulversioner
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056255"
---
# <a name="prerelease-module-versions"></a>Förhandsversioner modulversioner

Från och med version 1.6.0 eller senare, ger PowerShellGet och PowerShell-galleriet stöd för taggning versioner som är större än 1.0.0 som en förhandsversion. Innan den här funktionen var förhandsversioner paket begränsade till att ha en version som börjar med 0. Målet med de här funktionerna är att ge bättre support för [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versionshantering konvention utan att spräcka bakåtkompatibilitet kompatibilitet med PowerShell versioner 3 och senare, eller befintliga versioner av PowerShellGet. Det här avsnittet fokuserar på modulen-specifika funktioner. Motsvarande funktioner för skript finns i den [förhandsversion versioner av skript](script-prerelease-support.md) avsnittet. Med dessa funktioner kan kan utgivare identifiera en modul eller ett skript som version 2.5.0-alpha och senare använda en produktionsklar version 2.5.0 som ersätter förhandsversionen.

På en hög nivå omfattar förhandsversioner modulfunktioner:

- Att lägga till en sträng som förhandsversion i avsnittet PSData i modulmanifestet identifierar modulen som en förhandsversion. Om modulen har publicerats till PowerShell-galleriet, dessa data extraheras från manifestet, och används för att identifiera förhandsversioner paket.
- Hämta förhandsversionen paket kräver att lägga till `-AllowPrerelease` flaggan för PowerShellGet-kommandon `Find-Module`, `Install-Module`, `Update-Module`, och `Save-Module`. Om flaggan inte anges, visas inte förhandsversioner paket.
- Modulversionerna som visas av `Find-Module`, `Get-InstalledModule`, och i PowerShell-galleriet visas som en sträng med förhandsversioner strängen läggs, som i 2.5.0-alpha.

Information om funktionerna som ingår nedan.

De här ändringarna påverkar inte stöd för policymodul-version som är inbyggd i PowerShell och är kompatibla med PowerShell 3.0 och 4.0 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identifierar en Modulversion som en förhandsversion

PowerShellGet-stöd för förhandsversioner kräver användning av två fält i modulen Manifest:

- ModuleVersion som ingår i modulmanifestet måste vara en 3 delar om en förhandsversion används och måste vara kompatibel med befintliga PowerShell-versionshantering. Formatet version är A.B.C, där A, B och C är alla heltal.
- Förhandsversioner strängen har angetts i modulmanifestet i avsnittet PSData i PrivateData.

Detaljerade krav på förhandsversioner strängen finns nedan.

En exempel-avsnitt i ett modulmanifest som definierar en modul som en förhandsversion skulle se ut så här:

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

Villkoren för förhandsversioner sträng är:

- Förhandsversioner sträng kan bara anges när ModuleVersion är 3 segment för Major.Minor.Build. Detta ligger i linje med SemVer v1.0.0.
- Ett bindestreck är avgränsare mellan Build-nummer och förhandsversioner strängen. Ett bindestreck kan ingå i förhandsversioner strängen som det första tecknet, endast.
- Förhandsversioner strängen kan innehålla endast ASCII alfanumeriska tecken [0-9A-a - z-]. Det är en bra idé att börja förhandsutgåvan sträng med en bokstav, eftersom det är lättare att identifiera att detta är en förhandsversion när du skannar en lista över paket.
- Endast SemVer v1.0.0 förhandsversioner strängar stöds just nu. Förhandsversioner sträng **får inte** innehålla antingen punkt eller + [. +], som är tillåtna i SemVer 2.0.
- Exempel på stöds förhandsversioner sträng är:-alfa, -á1,-BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Förhandsversioner versionshantering påverkan på sortera ordningen och installationen mappar

Sorteringsordningen ändras när du använder en förhandsversion, vilket är viktigt när du publicerar PowerShell-galleriet, och när du installerar moduler med PowerShellGet-kommandon. Om förhandsversioner strängen har angetts för två moduler, utifrån sorteringsordningen strängdelen följa bindestreck. Så, version 2.5.0-alpha är mindre än 2.5.0-beta, vilket är mindre än 2.5.0-gamma. Om två moduler som har samma ModuleVersion och bara har en förhandsversion sträng, modul utan förhandsversioner strängen antas vara produktionsklar version och kommer att sorteras som en högre version än förhandsversionen (som innehåller förhandsutgåvan sträng). Till exempel när jämföra släpper 2.5.0 och 2.5.0-beta, 2.5.0 version betraktas det som är störst av två.

När du publicerar PowerShell-galleriet, som standard måste versionen av modulen publiceras ha en högre version än tidigare publicerade versionen som finns i PowerShell-galleriet.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Att söka efter och hämta förhandsversioner paket med PowerShellGet-kommandon

Behandlar förhandsversioner paket med hjälp av Sök-modulen PowerShellGet i Install-Module, Update-modulen och Save-Module kommandon kräver att lägga till flaggan - AllowPrerelease. Om - AllowPrerelease anges ska förhandsversioner paket inkluderas om de finns. Om - AllowPrerelease flaggan inte anges, visas inte förhandsversioner paket.

De enda undantagen till den här i modulen PowerShellGet-kommandon är Get-InstalledModule och ibland med Uninstall-modulen.

- Get-InstalledModule Visa alltid automatiskt informationen om förhandsversionen i versionssträng för moduler.
- Avinstallera modulen som standard avinstalleras den senaste versionen av en modul om __ingen version__ har angetts. Som standard har inte ändrats. Men om en förhandsversion kan anges med - RequiredVersion, måste - AllowPrerelease utföras.

## <a name="examples"></a>Exempel

Anta att PowerShell-galleriet har TestPackage modulversionerna 1.8.0 och 1.9.0-alpha. Om `-AllowPrerelease` är inte anges endast version 1.8.0 ska returneras.

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

Om du vill installera en förhandsversion, alltid ange - AllowPrerelease. Det räcker inte att ange en sträng i förhandsversion.

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

Det föregående kommandot misslyckades eftersom - AllowPrerelease inte har angetts. Att lägga till `-AllowPrerelease` leder till framgång.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

Sida-vid-sida-installation av av en modul som skiljer sig bara på grund av förhandsutgåvan angetts stöds inte. När du installerar en modul med PowerShellGet, finns olika versioner av samma modul installerade sida-vid-sida genom att skapa en mapp med namnet med hjälp av ModuleVersion. ModuleVersion utan förhandsversioner strängen används för mappnamnet. Om en användare installerar MyModule version 2.5.0-alpha, installeras den till den `MyModule\2.5.0` mapp. Om användaren installerar sedan 2.5.0-beta, 2.5.0-beta version kommer **skriva över** innehållet i mappen `MyModule\2.5.0`. En fördel med den här metoden är att det finns inget behov av att avinstallera förhandsversionen när du har installerat produktionsklar version. Exemplet nedan visar vad som händer:

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

Avinstallera modulen tar bort den senaste versionen av en modul när - RequiredVersion inte har angetts.
Om - RequiredVersion har angetts och är en förhandsversion, måste - AllowPrerelease läggas till kommandot.

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

- [Förhandsversioner skriptet versioner](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
