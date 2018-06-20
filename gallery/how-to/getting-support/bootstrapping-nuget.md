---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Startprogram för NuGet
ms.openlocfilehash: f707e23737361ee7f82a16150402c9e719ee0ae1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221807"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="de9d0-103">Bootstrap NuGet-providern och NuGet.exe</span><span class="sxs-lookup"><span data-stu-id="de9d0-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="de9d0-104">NuGet.exe ingår inte i den senaste NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="de9d0-104">NuGet.exe is not included in the latest NuGet provider.</span></span>
<span data-ttu-id="de9d0-105">För att publicera driften av en modul eller ett skript, PowerShellGet kräver binära körbara NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="de9d0-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span>
<span data-ttu-id="de9d0-106">Endast NuGet-providern krävs för alla andra åtgärder, inklusive *hitta*, *installera*, *spara*, och *avinstallera*.</span><span class="sxs-lookup"><span data-stu-id="de9d0-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="de9d0-107">PowerShellGet innehåller logik för att hantera antingen en kombinerad bootstrap NuGet-providern och NuGet.exe eller bootstrap av NuGet providern.</span><span class="sxs-lookup"><span data-stu-id="de9d0-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span>
<span data-ttu-id="de9d0-108">I båda fallen kan ska endast en fråga meddelandet ske.</span><span class="sxs-lookup"><span data-stu-id="de9d0-108">In either case, only a single prompt message should occur.</span></span>
<span data-ttu-id="de9d0-109">Om datorn inte är ansluten till Internet, måste användaren eller en administratör kopiera en betrodd instans av providern NuGet och/eller NuGet.exe-filen till den frånkopplade datorn.</span><span class="sxs-lookup"><span data-stu-id="de9d0-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

><span data-ttu-id="de9d0-110">**Obs**: från och med version 6, NuGet-providern ingår i installationen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de9d0-110">**Note**: Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span> [http://github.com/powershell/powershell](http://github.com/powershell/powershell)

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="de9d0-111">Hur du löser när NuGet-providern inte har installerats på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="de9d0-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

PS> Find-Module -Repository PSGallery -Verbose -Name Contoso

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

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="de9d0-112">Hur du löser när NuGet-providern är tillgänglig och NuGet.exe är inte tillgänglig under publiceringsåtgärden på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="de9d0-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="de9d0-113">Hur du löser när både NuGet-providern och NuGet.exe inte är tillgängliga under publiceringsåtgärden på en dator som är Internet-ansluten</span><span class="sxs-lookup"><span data-stu-id="de9d0-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

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

PS> Publish-Module -Name Contoso -Repository PSGallery -Verbose

NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="de9d0-114">Manuellt startprogram NuGet-providern på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="de9d0-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="de9d0-115">Processer som visas ovan förutsätter att datorn är ansluten till Internet och kan hämta filer från en allmän plats.</span><span class="sxs-lookup"><span data-stu-id="de9d0-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span>
<span data-ttu-id="de9d0-116">Om detta inte är möjligt, är det enda alternativet att starta en dator med de processer som anges ovan och manuellt kopiera providern till noden isolerade via en betrodd offlineprocess.</span><span class="sxs-lookup"><span data-stu-id="de9d0-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span>
<span data-ttu-id="de9d0-117">I de flesta användningsfall för det här scenariot är när ett privat galleri är tillgängliga till stöd för en isolerad miljö.</span><span class="sxs-lookup"><span data-stu-id="de9d0-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="de9d0-118">När du har följt processen ovan för att starta en Internet-ansluten dator hittar du provider-filer på plats:</span><span class="sxs-lookup"><span data-stu-id="de9d0-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

```
C:\Program Files\PackageManagement\ProviderAssemblies\
```

<span data-ttu-id="de9d0-119">Mappen/filen strukturen för NuGet-providern kommer att (eventuellt med ett annat versionsnummer):</span><span class="sxs-lookup"><span data-stu-id="de9d0-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

<span data-ttu-id="de9d0-120">NuGet</span><span class="sxs-lookup"><span data-stu-id="de9d0-120">NuGet</span></span><br>
<span data-ttu-id="de9d0-121">--2.8.5.208</span><span class="sxs-lookup"><span data-stu-id="de9d0-121">--2.8.5.208</span></span><br>
<span data-ttu-id="de9d0-122">---Microsoft.PackageManagement.NuGetProvider.dll</span><span class="sxs-lookup"><span data-stu-id="de9d0-122">----Microsoft.PackageManagement.NuGetProvider.dll</span></span>

<span data-ttu-id="de9d0-123">Kopiera dessa mappar och en fil med en betrodd process för offline-datorer.</span><span class="sxs-lookup"><span data-stu-id="de9d0-123">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="de9d0-124">Manuellt startprogram NuGet.exe att stödja publicera åtgärder på en dator som inte är ansluten till Internet</span><span class="sxs-lookup"><span data-stu-id="de9d0-124">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="de9d0-125">Förutom processen för att manuellt bootstrap NuGet-providern, om datorn används för att publicera moduler eller skript till en privat galleriet med hjälp av den *publicera modulen* eller *publicera skriptet* cmdlets NuGet.exe binära körbara filen kommer att krävas.</span><span class="sxs-lookup"><span data-stu-id="de9d0-125">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the *Publish-Module* or *Publish-Script* cmdlets, the NuGet.exe binary executable file will be required.</span></span>
<span data-ttu-id="de9d0-126">I de flesta användningsfall för det här scenariot är när ett privat galleri är tillgängliga till stöd för en isolerad miljö.</span><span class="sxs-lookup"><span data-stu-id="de9d0-126">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>
<span data-ttu-id="de9d0-127">Det finns två alternativ för att hämta filen NuGet.exe.</span><span class="sxs-lookup"><span data-stu-id="de9d0-127">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="de9d0-128">Ett alternativ är att starta en dator som är Internet-anslutna och kopiera filer till offline datorer med hjälp av en betrodd process.</span><span class="sxs-lookup"><span data-stu-id="de9d0-128">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span>
<span data-ttu-id="de9d0-129">Efter startprogram den Internet-anslutna datorn placeras NuGet.exe binärfilen i ett av två mappar:</span><span class="sxs-lookup"><span data-stu-id="de9d0-129">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="de9d0-130">Om den *publicera modulen* eller *publicera skriptet* cmdlets utfördes med förhöjda behörigheter (som en administratör):</span><span class="sxs-lookup"><span data-stu-id="de9d0-130">If the *Publish-Module* or *Publish-Script* cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="de9d0-131">Om cmdletarna utfördes som en användare utan förhöjd behörighet:</span><span class="sxs-lookup"><span data-stu-id="de9d0-131">If the cmdlets were executed as a user without elevated permissions:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="de9d0-132">Ett andra alternativ är att hämta NuGet.exe från NuGet.Org webbplats: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span><span class="sxs-lookup"><span data-stu-id="de9d0-132">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html)</span></span><br>
<span data-ttu-id="de9d0-133">När du väljer en NugGet version för produktion datorer, kontrollera att den är senare än 2.8.5.208 och identifiera den version som har tagits med etiketten ”rekommenderade”.</span><span class="sxs-lookup"><span data-stu-id="de9d0-133">When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span>
<span data-ttu-id="de9d0-134">Kom ihåg att avblockera filen om den har hämtats med en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="de9d0-134">Remember to unblock the file if it was downloaded using a browser.</span></span>
<span data-ttu-id="de9d0-135">Detta kan utföras med hjälp av den *avblockera filen* cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de9d0-135">This can be performed by using the *Unblock-File* cmdlet.</span></span>

<span data-ttu-id="de9d0-136">I båda fallen kan NuGet.exe filen kopieras till valfri plats i *$env: sökvägen*, men standardplatserna är:</span><span class="sxs-lookup"><span data-stu-id="de9d0-136">In either case, the NuGet.exe file can be copied to any location in *$env:path*, but the standard locations are:</span></span>

<span data-ttu-id="de9d0-137">Att den körbara filen så att alla användare kan använda *publicera modulen* och *publicera skriptet* cmdlets:</span><span class="sxs-lookup"><span data-stu-id="de9d0-137">To make the executable available so that all users can use *Publish-Module* and *Publish-Script* cmdlets:</span></span>

```
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="de9d0-138">Frigör den körbara filen till endast en specifik användare genom att kopiera till platsen i endast användarens profil:</span><span class="sxs-lookup"><span data-stu-id="de9d0-138">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```