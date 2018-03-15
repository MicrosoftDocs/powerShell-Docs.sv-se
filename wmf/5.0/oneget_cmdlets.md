---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 134c22efe4fb86045ffb326e109dfbcc741bcf2f
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="7ce48-102">PackageManagement-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="7ce48-102">PackageManagement Cmdlets</span></span>
<span data-ttu-id="7ce48-103">Detta är kärnan i PackageManagement som stöd för identifiering av programvara, installation och lager (SDII).</span><span class="sxs-lookup"><span data-stu-id="7ce48-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="7ce48-104">Prova att använda cmdlets för dessa åtgärder:</span><span class="sxs-lookup"><span data-stu-id="7ce48-104">Try out the cmdlets for these operations:</span></span>
-   <span data-ttu-id="7ce48-105">Find-Package</span><span class="sxs-lookup"><span data-stu-id="7ce48-105">Find-Package</span></span>
-   <span data-ttu-id="7ce48-106">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ce48-106">Find-PackageProvider</span></span>
-   <span data-ttu-id="7ce48-107">Get-Package</span><span class="sxs-lookup"><span data-stu-id="7ce48-107">Get-Package</span></span>
-   <span data-ttu-id="7ce48-108">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ce48-108">Get-PackageProvider</span></span>
-   <span data-ttu-id="7ce48-109">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="7ce48-109">Get-PackageSource</span></span>
-   <span data-ttu-id="7ce48-110">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ce48-110">Import-PackageProvider</span></span>
-   <span data-ttu-id="7ce48-111">Install-Package</span><span class="sxs-lookup"><span data-stu-id="7ce48-111">Install-Package</span></span>
-   <span data-ttu-id="7ce48-112">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ce48-112">Install-PackageProvider</span></span>
-   <span data-ttu-id="7ce48-113">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="7ce48-113">Register-PackageSource</span></span>
-   <span data-ttu-id="7ce48-114">Spara paketet</span><span class="sxs-lookup"><span data-stu-id="7ce48-114">Save-Package</span></span>
-   <span data-ttu-id="7ce48-115">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="7ce48-115">Set-PackageSource</span></span>
-   <span data-ttu-id="7ce48-116">Avinstallera paketet</span><span class="sxs-lookup"><span data-stu-id="7ce48-116">Uninstall-Package</span></span>
-   <span data-ttu-id="7ce48-117">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="7ce48-117">Unregister-PackageSource</span></span>

<span data-ttu-id="7ce48-118">Du kan göra följande för att uppdatera PackageManagement sig själv som PackageManagement en PowerShell-modul:</span><span class="sxs-lookup"><span data-stu-id="7ce48-118">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>
```powershell
PS C:\> Install-Module PackageManagement –Force
```
<span data-ttu-id="7ce48-119">I det här fallet behöver du ange nytt PowerShell-session växla till den nya versionen av PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="7ce48-119">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[<span data-ttu-id="7ce48-120">Hitta paket-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-120">Find-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890709.aspx)
<span data-ttu-id="7ce48-121">Denna cmdlet kan identifiering av programvarupaket i tillgängliga paket källor med hjälp av läsa in paketet providers.</span><span class="sxs-lookup"><span data-stu-id="7ce48-121">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -Provider PowerShellGet -Source PSGallery

# Find a package from a provider that is not yet installed
# This will bootstrap NuGet provider and then search for jquery package using NuGet
# with <http://www.nuget.org/api/v2/> as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[<span data-ttu-id="7ce48-122">Hitta PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-122">Find-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/library/mt676544.aspx)
<span data-ttu-id="7ce48-123">Hitta PackageProvider cmdleten hittar matchande PackageManagement leverantörer som är tillgängliga i paketet datakällor som har registrerats med PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="7ce48-123">The Find-PackageProvider cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="7ce48-124">Detta är paketet leverantörer som är tillgängliga för installation med cmdleten Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="7ce48-124">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span> <span data-ttu-id="7ce48-125">Som standard innehåller detta moduler som är tillgängliga i PowerShell-galleriet med 'PackageManagement' och 'Provider-taggar.</span><span class="sxs-lookup"><span data-stu-id="7ce48-125">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span> 

<span data-ttu-id="7ce48-126">Hitta PackageProvider hittar matchande PackageManagement leverantörer som är tillgängliga i PackageManagement azure blobstore där vi använder PackageManagement boostrapper providern för att söka efter och installera dem också.</span><span class="sxs-lookup"><span data-stu-id="7ce48-126">Find-PackageProvider also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[<span data-ttu-id="7ce48-127">Cmdlet Get-paket</span><span class="sxs-lookup"><span data-stu-id="7ce48-127">Get-Package Cmdlet</span></span>](https://technet.microsoft.com/library/dn890704.aspx)
<span data-ttu-id="7ce48-128">Denna cmdlet returnerar en lista över alla programvarupaket som har installerats med hjälp av PackageManagement.</span><span class="sxs-lookup"><span data-stu-id="7ce48-128">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[<span data-ttu-id="7ce48-129">Get-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-129">Get-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890703.aspx)
<span data-ttu-id="7ce48-130">Paketet leverantörer som är inlästa och redo att användas på den lokala datorn kan inventeras med hjälp av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ce48-130">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[<span data-ttu-id="7ce48-131">Get-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-131">Get-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890705.aspx)
<span data-ttu-id="7ce48-132">Denna cmdlet hämtar en lista över paket datakällor som är registrerade för en paket-provider.</span><span class="sxs-lookup"><span data-stu-id="7ce48-132">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[<span data-ttu-id="7ce48-133">Importera PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-133">Import-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676545.aspx)
<span data-ttu-id="7ce48-134">Denna cmdlet lägger till paketet Management paketet providers till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7ce48-134">This cmdlet adds Package Management package providers to the current session.</span></span>
```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[<span data-ttu-id="7ce48-135"> Install-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-135"> Install-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890711.aspx)

<span data-ttu-id="7ce48-136">Denna cmdlet kan installation av programvarupaket i tillgängliga paket källor med hjälp av läsa in paketet providers.</span><span class="sxs-lookup"><span data-stu-id="7ce48-136">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[<span data-ttu-id="7ce48-137">Installera PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-137">Install-PackageProvider Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/mt676543.aspx)
<span data-ttu-id="7ce48-138">Denna cmdlet installerar en eller flera paket Management paketet providers.</span><span class="sxs-lookup"><span data-stu-id="7ce48-138">This cmdlet installs one or more Package Management package providers.</span></span>
```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[<span data-ttu-id="7ce48-139">Register-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-139">Register-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890701.aspx)
<span data-ttu-id="7ce48-140">Denna cmdlet lägger till en paketkälla för en angiven paket-provider.</span><span class="sxs-lookup"><span data-stu-id="7ce48-140">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="7ce48-141">Varje PackageManagement provider kan ha en eller flera källor för programvara eller databaser.</span><span class="sxs-lookup"><span data-stu-id="7ce48-141">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="7ce48-142">PackageManagement innehåller PowerShell-cmdletar för att lägga till/ta bort/fråga källan.</span><span class="sxs-lookup"><span data-stu-id="7ce48-142">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="7ce48-143">Exempelvis kan du registrera en paketkälla för NuGet-providern:</span><span class="sxs-lookup"><span data-stu-id="7ce48-143">For example, you can register a package source for the NuGet provider:</span></span>
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[<span data-ttu-id="7ce48-144">Spara paketet Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-144">Save-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890708.aspx)
<span data-ttu-id="7ce48-145">Denna cmdlet sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="7ce48-145">This cmdlet saves packages to the local computer without installing them.</span></span>
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[<span data-ttu-id="7ce48-146">Set-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-146">Set-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890710.aspx)
<span data-ttu-id="7ce48-147">Denna cmdlet ändrar information om en befintlig datakälla för paketet.</span><span class="sxs-lookup"><span data-stu-id="7ce48-147">This cmdlet changes information about an existing package source.</span></span> 
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2 
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[<span data-ttu-id="7ce48-148">Avinstallera paketet Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-148">Uninstall-Package Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890702.aspx)
<span data-ttu-id="7ce48-149">Denna cmdlet avinstallerar paket som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7ce48-149">This cmdlet uninstalls packages installed on the local computer.</span></span>
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[<span data-ttu-id="7ce48-150">Unregister-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7ce48-150">Unregister-PackageSource Cmdlet</span></span>](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```

