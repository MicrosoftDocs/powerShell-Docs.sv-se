---
ms.date: 06/12/2017
keywords: Galleri, PowerShell, cmdlet, psget
title: Starta NuGet
ms.openlocfilehash: 70403006c7a48ac70a6766de3aa52d80cebbd86a
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78935167"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a>Starta NuGet-providern och NuGet. exe

NuGet. exe ingår inte i den senaste NuGet-providern. För publicerings åtgärder för antingen en modul eller ett skript, kräver PowerShellGet den binära körbara filen **NuGet. exe**. Endast NuGet-providern krävs för alla andra åtgärder, inklusive **Sök**, **Installera**, **Spara**och **Avinstallera**.
PowerShellGet innehåller logik för att hantera antingen en kombinerad start av NuGet-providern och NuGet. exe eller endast start av NuGet-providern. I båda fallen bör bara ett enda varnings meddelande visas. Om datorn inte är ansluten till Internet måste användaren eller administratören kopiera en betrodd instans av NuGet-providern och/eller NuGet. exe-filen till den frånkopplade datorn.

> [!NOTE]
> Från och med version 6 ingår NuGet-providern i installationen av PowerShell.

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a>Lösa fel när NuGet-providern inte har installerats på en dator som är ansluten till Internet

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
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

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Lösa fel när NuGet-providern är tillgänglig och NuGet. exe inte är tillgänglig under publicerings åtgärden på en dator som är ansluten till Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
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

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a>Lösa fel när både NuGet-providern och NuGet. exe inte är tillgängliga under publicerings åtgärden på en dator som är ansluten till Internet

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
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

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a>Starta NuGet-providern manuellt på en dator som inte är ansluten till Internet

De processer som visas ovan förutsätter att datorn är ansluten till Internet och kan ladda ned filer från en offentlig plats. Om detta inte är möjligt är det enda alternativet att starta en dator med de processer som anges ovan och manuellt kopiera providern till den isolerade noden via en betrodd offline-process. Det vanligaste användnings fallet för det här scenariot är när ett privat galleri är tillgängligt för att stödja en isolerad miljö.

Efter att ha följa processen ovan för att starta en ansluten Internet-dator hittar du filer på platsen:

`C:\Program Files\PackageManagement\ProviderAssemblies\`

Mappstrukturen för NuGet-providern kommer att vara (eventuellt med ett annat versions nummer):

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

Kopiera de här mapparna och filen med en betrodd process till offline-datorerna. Om du vill använda providern på den frånkopplade datorn måste den importeras. Kör följande kommando på den frånkopplade datorn:

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a>Starta NuGet. exe manuellt för att stödja publicerings åtgärder på en dator som inte är ansluten till Internet

Förutom processen att manuellt starta NuGet-providern, om datorn ska användas för att publicera moduler eller skript till ett privat galleri med hjälp av `Publish-Module` eller `Publish-Script` -cmdletar, krävs den binära körbara filen NuGet. exe.

Det vanligaste användnings fallet för det här scenariot är när ett privat galleri är tillgängligt för att stödja en isolerad miljö. Det finns två alternativ för att hämta filen NuGet. exe.

Ett alternativ är att starta en dator som är ansluten till Internet och kopiera filerna till de frånkopplade datorerna med en betrodd process. När den anslutna Internet-datorn har startats finns NuGet. exe-binärfilen i en av två mappar:

 - Om `Publish-Module` cmdletarna `Publish-Script` eller kördes med förhöjd behörighet (som administratör):

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- Om cmdletarna kördes som en användare utan förhöjd behörighet:

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

Ett andra alternativ är att ladda ned NuGet. exe från NuGet.Org-webbplatsen [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) : när du väljer en liten mängd-version för produktions datorer kontrollerar du att den är senare än 2.8.5.208 och identifierar den version som har etiketten "rekommenderas". Kom ihåg att avblockera filen om den hämtades med hjälp av en webbläsare. Detta kan utföras med hjälp av `Unblock-File` cmdleten.

I båda fallen kan filen NuGet. exe kopieras till vilken plats som helst i `$env:path`, men standard platserna är:

- Så här gör du den körbara filen tillgänglig så att `Publish-Module` alla `Publish-Script` användare kan använda och cmdlet: ar:

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- Om du vill att den körbara filen bara ska vara tillgänglig för en speciell användare kopierar du till platsen inom endast den användar profilen:

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
