---
ms.date: 06/12/2017
title: Starta NuGet
description: Den här artikeln beskriver hur du installerar de NuGet-komponenter som krävs för att kunna arbeta med PowerShell-galleriet.
ms.openlocfilehash: eddbe15e7a765ad8b6df2b317a090269f06661d5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661120"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="a2e4c-103">Starta NuGet-providern och NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="a2e4c-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="a2e4c-104">NuGet.exe ingår inte i den senaste NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="a2e4c-105">För publicerings åtgärder för antingen en modul eller ett skript, kräver PowerShellGet den binära körbara filen **NuGet.exe** .</span><span class="sxs-lookup"><span data-stu-id="a2e4c-105">For publish operations of either a module or script, PowerShellGet requires the binary executable **NuGet.exe** .</span></span> <span data-ttu-id="a2e4c-106">Endast NuGet-providern krävs för alla andra åtgärder, inklusive **Sök** , **Installera** , **Spara** och **Avinstallera** .</span><span class="sxs-lookup"><span data-stu-id="a2e4c-106">Only the NuGet provider is required for all other operations, including **find** , **install** , **save** , and **uninstall** .</span></span>
<span data-ttu-id="a2e4c-107">PowerShellGet innehåller logik för att hantera antingen en kombinerad start av NuGet-providern och NuGet.exe, eller endast start av NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="a2e4c-108">I båda fallen bör bara ett enda varnings meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="a2e4c-109">Om datorn inte är ansluten till Internet måste användaren eller administratören kopiera en betrodd instans av NuGet-providern och/eller NuGet.exe-filen till den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="a2e4c-110">Från och med version 6 ingår NuGet-providern i installationen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a2e4c-111">Lösa fel när NuGet-providern inte har installerats på en dator som är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a2e4c-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```Output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure
that '2.8.5.201' or newer version of NuGet provider is installed.
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
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based
repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\user1\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet
provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you
want PowerShellGet to install and import the NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a2e4c-112">Lösa fel när NuGet-providern är tillgänglig och NuGet.exe inte är tillgänglig under publicerings åtgärden på en dator som är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a2e4c-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure
that NuGet.exe is available under one of the paths specified in PATH environment variable value.
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
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must
be available under one of the paths specified in PATH environment variable value. Do you want
PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a2e4c-113">Lösa fel när både NuGet-providern och NuGet.exe inte är tillgängliga under publicerings åtgärden på en dator som är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a2e4c-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```Output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer
to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of
NuGet provider is installed and NuGet.exe is available under one of the paths specified in PATH
environment variable value.
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
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with
the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'.
 Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="a2e4c-114">Starta NuGet-providern manuellt på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a2e4c-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="a2e4c-115">De processer som visas ovan förutsätter att datorn är ansluten till Internet och kan ladda ned filer från en offentlig plats.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="a2e4c-116">Om detta inte är möjligt är det enda alternativet att starta en dator med de processer som anges ovan och manuellt kopiera providern till den isolerade noden via en betrodd offline-process.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="a2e4c-117">Det vanligaste användnings fallet för det här scenariot är när ett privat galleri är tillgängligt för att stödja en isolerad miljö.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="a2e4c-118">Efter att ha följa processen ovan för att starta en ansluten Internet-dator hittar du filer på platsen:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="a2e4c-119">Mappstrukturen för NuGet-providern kommer att vara (eventuellt med ett annat versions nummer):</span><span class="sxs-lookup"><span data-stu-id="a2e4c-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="a2e4c-120">Kopiera de här mapparna och filen med en betrodd process till offline-datorerna.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-120">Copy these folders and file using a trusted process to the offline machines.</span></span> <span data-ttu-id="a2e4c-121">Om du vill använda providern på den frånkopplade datorn måste den importeras.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-121">To use the provider on the offline machine, it must be imported.</span></span> <span data-ttu-id="a2e4c-122">Kör följande kommando på den frånkopplade datorn:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-122">Run the following command on the offline machine:</span></span>

```powershell
Import-PackageProvider -Name NuGet
```

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="a2e4c-123">Starta NuGet.exe manuellt för att stödja publicerings åtgärder på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a2e4c-123">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="a2e4c-124">Förutom processen att manuellt starta NuGet-providern, om datorn ska användas för att publicera moduler eller skript till ett privat galleri med hjälp av `Publish-Module` `Publish-Script` -eller-cmdletar, krävs den körbara filen NuGet.exe Binary.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-124">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="a2e4c-125">Det vanligaste användnings fallet för det här scenariot är när ett privat galleri är tillgängligt för att stödja en isolerad miljö.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-125">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="a2e4c-126">Det finns två alternativ för att hämta NuGet.exe-filen.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-126">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="a2e4c-127">Ett alternativ är att starta en dator som är ansluten till Internet och kopiera filerna till de frånkopplade datorerna med en betrodd process.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-127">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="a2e4c-128">När den anslutna Internet-datorn har startats finns NuGet.exe-binärfilen i en av två mappar:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-128">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

- <span data-ttu-id="a2e4c-129">Om `Publish-Module` `Publish-Script` cmdletarna eller kördes med förhöjd behörighet (som administratör):</span><span class="sxs-lookup"><span data-stu-id="a2e4c-129">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As  an Administrator):</span></span>

   ```powershell
   $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
   ```

- <span data-ttu-id="a2e4c-130">Om cmdletarna kördes som en användare utan förhöjd behörighet:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-130">If the cmdlets were executed as a user without elevated permissions:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```

<span data-ttu-id="a2e4c-131">Ett andra alternativ är att ladda ned NuGet.exe från webbplatsen NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) när du väljer en liten mängd-version för produktions datorer kontrollerar du att den är senare än 2.8.5.208 och identifierar versionen som har märkts som "rekommenderas".</span><span class="sxs-lookup"><span data-stu-id="a2e4c-131">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="a2e4c-132">Kom ihåg att avblockera filen om den hämtades med hjälp av en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-132">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="a2e4c-133">Detta kan utföras med hjälp av `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a2e4c-133">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="a2e4c-134">I båda fallen kan NuGet.exe-filen kopieras till valfri plats i `$env:path` , men standard platserna är:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-134">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

- <span data-ttu-id="a2e4c-135">Så här gör du den körbara filen tillgänglig så att alla användare kan använda `Publish-Module` och `Publish-Script` cmdlet: ar:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-135">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

  ```powershell
  $env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
  ```

- <span data-ttu-id="a2e4c-136">Om du vill att den körbara filen bara ska vara tillgänglig för en speciell användare kopierar du till platsen inom endast den användar profilen:</span><span class="sxs-lookup"><span data-stu-id="a2e4c-136">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

  ```powershell
  $env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
  ```
