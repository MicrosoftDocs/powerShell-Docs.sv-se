---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: f545461fd325049d0de4c651d7aa7d50d475eaca
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221962"
---
# <a name="packagemanagement-cmdlets"></a>PackageManagement-cmdletar
Detta är kärnan i PackageManagement som stöd för identifiering av programvara, installation och lager (SDII). Prova att använda cmdlets för dessa åtgärder:
-   Sök-paket
-   Find-PackageProvider
-   Get-Package
-   Get-PackageProvider
-   Get-PackageSource
-   Importera PackageProvider
-   Install-Package
-   Installera PackageProvider
-   Registrera PackageSource
-   Spara paketet
-   Set-PackageSource
-   Avinstallera paketet
-   Unregister-PackageSource

Du kan göra följande för att uppdatera PackageManagement sig själv som PackageManagement en PowerShell-modul:
```powershell
PS C:\> Install-Module PackageManagement –Force
```
I det här fallet behöver du ange nytt PowerShell-session växla till den nya versionen av PackageManagement.

## <a name="find-package-cmdlethttpstechnetmicrosoftcomlibrarydn890709aspx"></a>[Hitta paket-Cmdlet](https://technet.microsoft.com/library/dn890709.aspx)
Denna cmdlet kan identifiering av programvarupaket i tillgängliga paket källor med hjälp av läsa in paketet providers.
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

## <a name="find-packageprovider-cmdlethttpstechnetmicrosoftcomlibrarymt676544aspx"></a>[Hitta PackageProvider Cmdlet](https://technet.microsoft.com/library/mt676544.aspx)
Hitta PackageProvider cmdleten hittar matchande PackageManagement leverantörer som är tillgängliga i paketet datakällor som har registrerats med PowerShellGet. Detta är paketet leverantörer som är tillgängliga för installation med cmdleten Install-PackageProvider. Som standard innehåller detta moduler som är tillgängliga i PowerShell-galleriet med 'PackageManagement' och 'Provider-taggar.

Hitta PackageProvider hittar matchande PackageManagement leverantörer som är tillgängliga i PackageManagement azure blobstore där vi använder PackageManagement boostrapper providern för att söka efter och installera dem också.
```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdlethttpstechnetmicrosoftcomlibrarydn890704aspx"></a>[Cmdlet Get-paket](https://technet.microsoft.com/library/dn890704.aspx)
Denna cmdlet returnerar en lista över alla programvarupaket som har installerats med hjälp av PackageManagement.
```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890703aspx"></a>[Get-PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/dn890703.aspx)
Paketet leverantörer som är inlästa och redo att användas på den lokala datorn kan inventeras med hjälp av cmdleten.
```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890705aspx"></a>[Get-PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890705.aspx)
Denna cmdlet hämtar en lista över paket datakällor som är registrerade för en paket-provider.
```powershelll
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676545aspx"></a>[Importera PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676545.aspx)
Denna cmdlet lägger till paketet Management paketet providers till den aktuella sessionen.
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

##<a name="-install-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890711aspx"></a>[ Install-Package Cmdlet](https://technet.microsoft.com/en-us/library/dn890711.aspx)

Denna cmdlet kan installation av programvarupaket i tillgängliga paket källor med hjälp av läsa in paketet providers.
```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdlethttpstechnetmicrosoftcomen-uslibrarymt676543aspx"></a>[Installera PackageProvider Cmdlet](https://technet.microsoft.com/en-us/library/mt676543.aspx)
Denna cmdlet installerar en eller flera paket Management paketet providers.
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

## <a name="register-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890701aspx"></a>[Registrera PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890701.aspx)
Denna cmdlet lägger till en paketkälla för en angiven paket-provider.
Varje PackageManagement provider kan ha en eller flera källor för programvara eller databaser. PackageManagement innehåller PowerShell-cmdletar för att lägga till/ta bort/fråga källan. Exempelvis kan du registrera en paketkälla för NuGet-providern:
```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890708aspx"></a>[Spara paketet Cmdlet](https://technet.microsoft.com/en-us/library/dn890708.aspx)
Denna cmdlet sparar paket på den lokala datorn utan att installera dem.
```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -source c:\test
```

## <a name="set-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890710aspx"></a>[Cmdlet set-PackageSource](https://technet.microsoft.com/en-us/library/dn890710.aspx)
Denna cmdlet ändrar information om en befintlig datakälla för paketet.
```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890702aspx"></a>[Avinstallera paketet Cmdlet](https://technet.microsoft.com/en-us/library/dn890702.aspx)
Denna cmdlet avinstallerar paket som är installerade på den lokala datorn.
```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdlethttpstechnetmicrosoftcomen-uslibrarydn890707aspx"></a>[Avregistrera PackageSource Cmdlet](https://technet.microsoft.com/en-us/library/dn890707.aspx)
```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```
