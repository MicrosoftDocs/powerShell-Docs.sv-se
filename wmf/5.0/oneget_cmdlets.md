---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 042e9a30068d32dc5860255bdec960371121d866
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085311"
---
# <a name="packagemanagement-cmdlets"></a>PackageManagement-cmdletar

Det här är kärnan i PackageManagement för identifiering av programvara, installationen och inventeringen (SDII). Prova att använda cmdletarna för dessa åtgärder:

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

Eftersom PackageManagement är en PowerShell-modul, kan du göra följande för att uppdatera PackageManagement själva:

```powershell
Install-Module PackageManagement –Force
```

I det här fallet kommer du behöva ange nytt PowerShell-session att växla till den nya versionen av PackageManagement.

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[Sök-Package-Cmdlet](/powershell/module/PackageManagement/Find-Package)

Denna cmdlet kan identifiering av programvarupaket i paketkällor med hjälp av läsa in paketet providers.

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[Hitta PackageProvider Cmdlet](/powershell/module/PackageManagement/Find-PackageProvider)

Den `Find-PackageProvider` cmdleten hittar matchar PackageManagement-leverantörer som är tillgängliga i paketkällorna registrerad med PowerShellGet. Det här är paketet leverantörer som är tillgängliga för installation med den `Install-PackageProvider` cmdlet. Som standard innehåller detta moduler som är tillgängliga i PowerShell-galleriet med 'PackageManagement' och 'Providern' taggar.

`Find-PackageProvider` söker efter matchande PackageManagement-providers som är tillgängliga i PackageManagement azure blob store där vi använder providern för PackageManagement boostrapper för att hitta och installera dem också.

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[Cmdlet Get-Package](/powershell/module/PackageManagement/Get-Package)

Denna cmdlet returnerar en lista över alla programvarupaket som har installerats med PackageManagement.

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[Cmdlet Get-PackageProvider](/powershell/module/PackageManagement/Get-PackageProvider)

Paket-leverantörer som är inläst och klar att användas på den lokala datorn kan inventeras med hjälp av cmdleten.

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[Get-PackageSource Cmdlet](/powershell/module/PackageManagement/Get-PackageSource)

Denna cmdlet hämtar en lista över paketkällorna som är registrerade för en paket-provider.

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[Importera PackageProvider Cmdlet](/powershell/module/PackageManagement/Import-PackageProvider)

Denna cmdlet lägger till pakethantering paketet providers i den aktuella sessionen.

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

## <a name="install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[Cmdlet: en Install-Package](/powershell/module/PackageManagement/Install-Package)

Denna cmdlet kan installation av programvarupaket i paketkällor med hjälp av läsa in paketet providers.

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[Installera PackageProvider Cmdlet](/powershell/module/PackageManagement/Install-PackageProvider)

Denna cmdlet installerar en eller flera pakethantering paketet providers.

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

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[Register-PackageSource Cmdlet](/powershell/module/PackageManagement/Register-PackageSource)

Denna cmdlet lägger till en paketkälla för en angiven paket-provider.
Varje PackageManagement-provider kan ha en eller flera källor för programvara eller databaser. PackageManagement innehåller PowerShell-cmdletar för att lägga till/ta bort/fråga källan. Exempelvis kan du registrera en paketkälla för NuGet-providern:

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[Spara-Package-Cmdlet](/powershell/module/PackageManagement/Save-Package)

Denna cmdlet sparar paket till den lokala datorn utan att installera dem.

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[Set-PackageSource Cmdlet](/powershell/module/PackageManagement/Set-PackageSource)

Denna cmdlet ändrar information om en befintlig datakälla för paketet.

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[Uninstall-Package Cmdlet](/powershell/module/PackageManagement/Uninstall-Package)

Denna cmdlet avinstallerar paket som är installerade på den lokala datorn.

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[Unregister-PackageSource Cmdlet](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```