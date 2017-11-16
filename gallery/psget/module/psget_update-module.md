---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Update-modul
ms.openlocfilehash: 343c296dad2a3df35f13393b3796a1d484f5f535
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="update-module"></a><span data-ttu-id="06d78-103">Update-modul</span><span class="sxs-lookup"><span data-stu-id="06d78-103">Update-Module</span></span>

<span data-ttu-id="06d78-104">Hämtar och installerar den senaste versionen av angivna modulerna från en online-galleriet till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="06d78-104">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

## <a name="description"></a><span data-ttu-id="06d78-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="06d78-105">Description</span></span>

<span data-ttu-id="06d78-106">Uppdatera modulen installerar en nyare version av Windows PowerShell-modulen som har installerats från galleriet online genom att köra Install-modulen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="06d78-106">The Update-Module cmdlet installs a newer version of a Windows PowerShell module that was installed from the online gallery by running Install-Module on the local computer.</span></span>

<span data-ttu-id="06d78-107">Som standard installeras den senaste versionen av angiven modul i online-galleriet, såvida du inte anger en version som krävs.</span><span class="sxs-lookup"><span data-stu-id="06d78-107">By default, the newest version of the specified module available in online gallery is installed, unless you specify a required version.</span></span> <span data-ttu-id="06d78-108">Du kan uppdatera en befintlig, installerad modul genom att ange namnet på modulen. Update-Module söker $env: PSModulePath för den modul som du vill uppdatera.</span><span class="sxs-lookup"><span data-stu-id="06d78-108">You can update an existing, installed module by specifying the name of the module; Update-Module searches $env:PSModulePath for the module that you want to update.</span></span>

<span data-ttu-id="06d78-109">Kör Update-modulen utan parametern Name uppdaterar alla moduler som kan uppdateras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="06d78-109">Running Update-Module without the Name parameter updates all modules that can be updated on the local computer.</span></span>

### <a name="notes"></a><span data-ttu-id="06d78-110">Obs!</span><span class="sxs-lookup"><span data-stu-id="06d78-110">Notes</span></span>

- <span data-ttu-id="06d78-111">Denna cmdlet körs på Windows PowerShell 3.0 eller senare versioner av Windows PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="06d78-111">This cmdlet runs on Windows PowerShell 3.0 or later releases of Windows PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>
- <span data-ttu-id="06d78-112">Om den modul som du anger med parametern namn inte har installerats med hjälp av Install-Module, uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="06d78-112">If the module that you specify with the Name parameter was not installed by using Install-Module, an error occurs.</span></span> <span data-ttu-id="06d78-113">Du kan bara köra Update-modulen på moduler som du installerat från galleriet online genom att köra Install-modulen.</span><span class="sxs-lookup"><span data-stu-id="06d78-113">You can only run Update-Module on modules that you installed from the online gallery by running Install-Module.</span></span>
- <span data-ttu-id="06d78-114">Om uppdateringen modulen försöker uppdatera binärfiler som används, returnerar Update-modulen ett fel som identifierar problemet processer och informerar användaren om du vill försöka uppdatera modulen när du har stoppat processer.</span><span class="sxs-lookup"><span data-stu-id="06d78-114">If Update-Module attempts to update binaries that are in use, Update-Module returns an error that identifies the problem processes, and informs the user to retry Update-Module after stopping the processes.</span></span>
- <span data-ttu-id="06d78-115">På PowerShell 5.0 eller senare versioner när uppdateringen modulen uppdaterar en modul, läggs den senaste (eller angivna) versionen av modulen, så att äldre och nyare versioner är nu sida vid sida i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="06d78-115">On PowerShell 5.0 or newer versions, when Update-Module updates a module, it adds the latest (or specified) version of the module, so the older and newer versions are now side-by-side in the same directory.</span></span> <span data-ttu-id="06d78-116">Det kan vara användbart att säga så och visar ett exempel på utdata från de här kommandona.</span><span class="sxs-lookup"><span data-stu-id="06d78-116">It would be useful to say so and to show an example of the output from these commands.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="06d78-117">Cmdlet-syntax</span><span class="sxs-lookup"><span data-stu-id="06d78-117">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-Module -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="06d78-118">Cmdlet-referens för onlinehjälp</span><span class="sxs-lookup"><span data-stu-id="06d78-118">Cmdlet online help reference</span></span>

[<span data-ttu-id="06d78-119">Update-modul</span><span class="sxs-lookup"><span data-stu-id="06d78-119">Update-Module</span></span>](http://go.microsoft.com/fwlink/?LinkID=398576)


## <a name="example-commands"></a><span data-ttu-id="06d78-120">Exempel på kommandon</span><span class="sxs-lookup"><span data-stu-id="06d78-120">Example commands</span></span>

```powershell
PS C:\\windows\\system32> Update-Module -Name ContosoServer -RequiredVersion 1.5
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
PS C:\\windows\\system32> Update-Module -Name ContosoServer
PS C:\\windows\\system32> Get-Module -ListAvailable -Name ContosoServer | Format-List Name,Version,ModuleBase
Name : ContosoServer
Version : 2.8.1
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.8.1
Name : ContosoServer
Version : 2.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\2.0
Name : ContosoServer
Version : 1.5
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.5
Name : ContosoServer
Version : 1.0
ModuleBase : C:\\Program Files\\WindowsPowerShell\\Modules\\ContosoServer\\1.0
PS C:\\windows\\system32> Get-InstalledModule
Version Name Repository Description
------- ---- ---------- -----------
1.0 ContosoServer MSPSGallery ContosoServer module
1.5 ContosoServer MSPSGallery ContosoServer module
2.0 ContosoServer MSPSGallery ContosoServer module
2.8.1 ContosoServer MSPSGallery ContosoServer module
```


###  <a name="update-the-testdepwithnestedrequiredmodules1-module-with-dependencies"></a><span data-ttu-id="06d78-121">Uppdatera modulen TestDepWithNestedRequiredModules1 med beroenden.</span><span class="sxs-lookup"><span data-stu-id="06d78-121">Update the TestDepWithNestedRequiredModules1 module with dependencies.</span></span>
```powershell
Find-Module -Name TestDepWithNestedRequiredModules1 -Repository LocalRepo -AllVersions

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module

Update-Module -Name TestDepWithNestedRequiredModules1 -RequiredVersion 2.0
Get-InstalledModule

Version    Name                                Repository  Description
-------    ----                                ----------  -----------
1.0        NestedRequiredModule1               LocalRepo   NestedRequiredModule1 module
2.5        NestedRequiredModule2               LocalRepo   NestedRequiredModule2 module
2.0        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
2.5        NestedRequiredModule3               LocalRepo   NestedRequiredModule3 module
1.0        RequiredModule1                     LocalRepo   RequiredModule1 module
2.5        RequiredModule2                     LocalRepo   RequiredModule2 module
2.0        RequiredModule3                     LocalRepo   RequiredModule3 module
2.5        RequiredModule3                     LocalRepo   RequiredModule3 module
1.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
2.0        TestDepWithNestedRequiredModules1   LocalRepo   TestDepWithNestedRequiredModules1 module
```

