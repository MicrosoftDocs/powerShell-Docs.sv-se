---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Start av NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002146"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Bootstrap NuGet-providern och NuGet.exe

NuGet.exe ingår inte i den senaste NuGet-providern. För att publicera driften av en modul eller ett skript, PowerShellGet kräver binära körbara NuGet.exe. Endast NuGet-providern krävs för alla andra åtgärder, inklusive *hitta*, *installera*, *spara*, och *avinstallera*.
PowerShellGet innehåller logik för att hantera antingen en kombinerad bootstrap av NuGet-providern och NuGet.exe eller bootstrap av endast NuGet-providern. I båda fallen görs bara en enda fråga meddelande. Om datorn inte är ansluten till Internet, måste användaren eller en administratör kopiera en betrodd instans av NuGet-providern och/eller NuGet.exe-filen till den frånkopplade datorn.

> [!NOTE]
> Från och med version 6, ingår NuGet-providern i installationen av PowerShell.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Matcha fel när NuGet-providern inte har installerats på en dator som är Internet-ansluten

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Matcha fel när finns NuGet-providern och NuGet.exe är inte tillgängligt under publiceringsåtgärden på en dator som är Internet-ansluten

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Matcha fel när både NuGet-providern och NuGet.exe inte är tillgängliga under publiceringsåtgärden på en dator som är Internet-ansluten

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
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
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuellt start av NuGet-providern på en dator som inte är ansluten till Internet

De processer som visas ovan förutsätter att datorn är ansluten till Internet och kan ladda ned filer från en allmän plats. Om detta inte är möjligt är det enda alternativet att kunna starta en virtuell dator med de processer som anges ovan och manuellt kopiera providern till isolerad nod via en betrodd offlineprocess. När ett privat galleri är tillgänglig som stöder en isolerad miljö är det vanligaste användningsfallet för det här scenariot.

När du har genomfört processen ovan för att kunna starta en Internetansluten dator hittar du providern filer på plats:

`C:\Program Files\PackageManagement\ProviderAssemblies\`

Mappen/filen strukturen för NuGet-providern blir (eventuellt med ett annat versionsnummer):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Kopiera dessa mappar och en fil med hjälp av en betrodd process till offline-datorer.

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Manuellt bootstrapping NuGet.exe för publicera åtgärder på en dator som inte är ansluten till Internet

Förutom att processen ska kunna starta NuGet-providern manuellt om datorn som ska användas för att publicera moduler eller skript till en privat galleri med hjälp av den `Publish-Module` eller `Publish-Script` cmdlet: ar, NuGet.exe binära körbara filen måste utföras.

När ett privat galleri är tillgänglig som stöder en isolerad miljö är det vanligaste användningsfallet för det här scenariot. Det finns två alternativ för att hämta NuGet.exe-filen.

Ett alternativ är att kunna starta en dator som är Internet-anslutna och kopiera filer till offline-datorer med hjälp av en betrodd process. Efter start av den Internetansluten datorn placeras NuGet.exe binärfilen i en av två mappar:

Om den `Publish-Module` eller `Publish-Script` cmdlets har körts med förhöjd behörighet (som administratör):

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Om cmdletarna utfördes som en användare utan administratörsbehörighet:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

Ett andra alternativ är att hämta NuGet.exe från webbplatsen NuGet.Org: [ https://dist.nuget.org/index.html ](https://www.nuget.org/downloads) när du väljer en NugGet version för produktion-datorer, se till att det är senare än 2.8.5.208 och identifiera den version som har fått en etikett ” rekommenderade ”. Kom ihåg att avblockera filen om den har hämtats med hjälp av en webbläsare. Detta kan utföras med hjälp av den `Unblock-File` cmdlet.

I båda fallen NuGet.exe-filen kan kopieras till valfri plats i `$env:path`, men platserna som standard är:

Att göra den körbara filen tillgänglig så att alla användare kan använda `Publish-Module` och `Publish-Script` cmdletar:

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

Frigör den körbara filen till endast en specifik användare genom att kopiera till plats inom endast användarens profil:

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
