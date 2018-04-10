---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Startprogram för NuGet-providern och EXE
ms.openlocfilehash: 1c8d99491aec6d2a598facb909c1f36f4bb979e7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="bootstrap-both-nuget-provider-and-nugetexe-or-bootstrap-only-nuget-provider"></a>Bootstrap både NuGet-providern och NuGet.exe eller bootstrap NuGet-providern

NuGet.exe ingår inte i den senaste NuGet-providern.
För att publicera driften av en modul eller ett skript, PowerShellGet kräver binära körbara NuGet.exe.
Endast NuGet-providern krävs för alla andra åtgärder, inklusive *hitta*, *installera*, *spara*, och *avinstallera*.
PowerShellGet innehåller logik för att hantera antingen en kombinerad bootstrap NuGet-providern och NuGet.exe eller bootstrap av NuGet providern.
I båda fallen kan ska endast en fråga meddelandet ske.
Om datorn inte är ansluten till Internet, måste användaren eller en administratör kopiera en betrodd instans av providern NuGet och/eller NuGet.exe-filen till den frånkopplade datorn.

>**Obs**: från och med version 6, NuGet-providern ingår i installationen av PowerShell. [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Hur du löser när NuGet-providern inte har installerats på en dator som är Internet-ansluten

```powershell
PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module

PS C:\> Find-Module -Repository PSGallery -Verbose -Name Contoso

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```
## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Hur du löser när NuGet-providern är tillgänglig och NuGet.exe är inte tillgänglig under publiceringsåtgärden på en dator som är Internet-ansluten

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Hur du löser när både NuGet-providern och NuGet.exe inte är tillgängliga under publiceringsåtgärden på en dator som är Internet-ansluten

```powershell
PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module

PS C:\> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuellt startprogram NuGet-providern på en dator som inte är ansluten till Internet

Processer som visas ovan förutsätter att datorn är ansluten till Internet och kan hämta filer från en allmän plats.
Om detta inte är möjligt, är det enda alternativet att starta en dator med de processer som anges ovan och manuellt kopiera providern till noden isolerade via en betrodd offlineprocess.
I de flesta användningsfall för det här scenariot är när ett privat galleri är tillgängliga till stöd för en isolerad miljö.

När du har följt processen ovan för att starta en Internet-ansluten dator hittar du provider-filer på plats:
```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

Mappen/filen strukturen för NuGet-providern kommer att (eventuellt med ett annat versionsnummer):

NuGet<br>
--2.8.5.208<br>
----Microsoft.PackageManagement.NuGetProvider.dll

Kopiera dessa mappar och en fil med en betrodd process för offline-datorer.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuellt startprogram NuGet.exe att stödja publicera åtgärder på en dator som inte är ansluten till Internet

Förutom processen för att manuellt bootstrap NuGet-providern, om datorn används för att publicera moduler eller skript till en privat galleriet med hjälp av den *publicera modulen* eller *publicera skriptet* cmdlets NuGet.exe binära körbara filen kommer att krävas.
I de flesta användningsfall för det här scenariot är när ett privat galleri är tillgängliga till stöd för en isolerad miljö.
Det finns två alternativ för att hämta filen NuGet.exe.

Ett alternativ är att starta en dator som är Internet-anslutna och kopiera filer till offline datorer med hjälp av en betrodd process.
Efter startprogram den Internet-anslutna datorn placeras NuGet.exe binärfilen i ett av två mappar:

Om den *publicera modulen* eller *publicera skriptet* cmdlets utfördes med förhöjda behörigheter (som en administratör):
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Om cmdletarna utfördes som en användare utan förhöjd behörighet:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Ett andra alternativ är att hämta NuGet.exe från NuGet.Org webbplats: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)<br>
När du väljer en NugGet version för produktion datorer, kontrollera att den är senare än 2.8.5.208 och identifiera den version som har tagits med etiketten ”rekommenderade”.
Kom ihåg att avblockera filen om den har hämtats med en webbläsare.
Detta kan utföras med hjälp av den *avblockera filen* cmdlet.

I båda fallen kan NuGet.exe filen kopieras till valfri plats i *$env: sökvägen*, men standardplatserna är:

Att den körbara filen så att alla användare kan använda *publicera modulen* och *publicera skriptet* cmdlets:
```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Frigör den körbara filen till endast en specifik användare genom att kopiera till platsen i endast användarens profil:
```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```