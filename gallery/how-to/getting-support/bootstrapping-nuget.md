---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Start av NuGet
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683970"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="a74ed-103">Bootstrap NuGet-providern och NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="a74ed-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="a74ed-104">NuGet.exe ingår inte i den senaste NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="a74ed-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="a74ed-105">För att publicera driften av en modul eller ett skript, PowerShellGet kräver binära körbara NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="a74ed-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="a74ed-106">Endast NuGet-providern krävs för alla andra åtgärder, inklusive *hitta*, *installera*, *spara*, och *avinstallera*.</span><span class="sxs-lookup"><span data-stu-id="a74ed-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="a74ed-107">PowerShellGet innehåller logik för att hantera antingen en kombinerad bootstrap av NuGet-providern och NuGet.exe eller bootstrap av endast NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="a74ed-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="a74ed-108">I båda fallen görs bara en enda fråga meddelande.</span><span class="sxs-lookup"><span data-stu-id="a74ed-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="a74ed-109">Om datorn inte är ansluten till Internet, måste användaren eller en administratör kopiera en betrodd instans av NuGet-providern och/eller NuGet.exe-filen till den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="a74ed-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="a74ed-110">Från och med version 6, ingår NuGet-providern i installationen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a74ed-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a74ed-111">Matcha fel när NuGet-providern inte har installerats på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="a74ed-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a74ed-112">Matcha fel när finns NuGet-providern och NuGet.exe är inte tillgängligt under publiceringsåtgärden på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="a74ed-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

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

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="a74ed-113">Matcha fel när både NuGet-providern och NuGet.exe inte är tillgängliga under publiceringsåtgärden på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="a74ed-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

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

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="a74ed-114">Manuellt start av NuGet-providern på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a74ed-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="a74ed-115">De processer som visas ovan förutsätter att datorn är ansluten till Internet och kan ladda ned filer från en allmän plats.</span><span class="sxs-lookup"><span data-stu-id="a74ed-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="a74ed-116">Om detta inte är möjligt är det enda alternativet att kunna starta en virtuell dator med de processer som anges ovan och manuellt kopiera providern till isolerad nod via en betrodd offlineprocess.</span><span class="sxs-lookup"><span data-stu-id="a74ed-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="a74ed-117">När ett privat galleri är tillgänglig som stöder en isolerad miljö är det vanligaste användningsfallet för det här scenariot.</span><span class="sxs-lookup"><span data-stu-id="a74ed-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="a74ed-118">När du har genomfört processen ovan för att kunna starta en Internetansluten dator hittar du providern filer på plats:</span><span class="sxs-lookup"><span data-stu-id="a74ed-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="a74ed-119">Mappen/filen strukturen för NuGet-providern blir (eventuellt med ett annat versionsnummer):</span><span class="sxs-lookup"><span data-stu-id="a74ed-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="a74ed-120">Kopiera dessa mappar och en fil med hjälp av en betrodd process till offline-datorer.</span><span class="sxs-lookup"><span data-stu-id="a74ed-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="a74ed-121">Manuellt bootstrapping NuGet.exe för publicera åtgärder på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="a74ed-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="a74ed-122">Förutom att processen ska kunna starta NuGet-providern manuellt om datorn som ska användas för att publicera moduler eller skript till en privat galleri med hjälp av den `Publish-Module` eller `Publish-Script` cmdlet: ar, NuGet.exe binära körbara filen måste utföras.</span><span class="sxs-lookup"><span data-stu-id="a74ed-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="a74ed-123">När ett privat galleri är tillgänglig som stöder en isolerad miljö är det vanligaste användningsfallet för det här scenariot.</span><span class="sxs-lookup"><span data-stu-id="a74ed-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="a74ed-124">Det finns två alternativ för att hämta NuGet.exe-filen.</span><span class="sxs-lookup"><span data-stu-id="a74ed-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="a74ed-125">Ett alternativ är att kunna starta en dator som är Internet-anslutna och kopiera filer till offline-datorer med hjälp av en betrodd process.</span><span class="sxs-lookup"><span data-stu-id="a74ed-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="a74ed-126">Efter start av den Internetansluten datorn placeras NuGet.exe binärfilen i en av två mappar:</span><span class="sxs-lookup"><span data-stu-id="a74ed-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="a74ed-127">Om den `Publish-Module` eller `Publish-Script` cmdlets har körts med förhöjd behörighet (som administratör):</span><span class="sxs-lookup"><span data-stu-id="a74ed-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="a74ed-128">Om cmdletarna utfördes som en användare utan administratörsbehörighet:</span><span class="sxs-lookup"><span data-stu-id="a74ed-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="a74ed-129">Ett andra alternativ är att hämta NuGet.exe från webbplatsen NuGet.Org: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) När du väljer en NugGet version för produktion-datorer, se till att det är senare än 2.8.5.208 och identifiera den version som har fått en etikett ”rekommenderade”.</span><span class="sxs-lookup"><span data-stu-id="a74ed-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="a74ed-130">Kom ihåg att avblockera filen om den har hämtats med hjälp av en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="a74ed-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="a74ed-131">Detta kan utföras med hjälp av den `Unblock-File` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a74ed-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="a74ed-132">I båda fallen NuGet.exe-filen kan kopieras till valfri plats i `$env:path`, men platserna som standard är:</span><span class="sxs-lookup"><span data-stu-id="a74ed-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="a74ed-133">Att göra den körbara filen tillgänglig så att alla användare kan använda `Publish-Module` och `Publish-Script` cmdletar:</span><span class="sxs-lookup"><span data-stu-id="a74ed-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="a74ed-134">Frigör den körbara filen till endast en specifik användare genom att kopiera till plats inom endast användarens profil:</span><span class="sxs-lookup"><span data-stu-id="a74ed-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
