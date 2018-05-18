---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 35be7d02ea856ea39218f05d32b43c60fa1bd53e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="installing-powershellget"></a><span data-ttu-id="c1ad7-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c1ad7-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c1ad7-104">PowerShellGet är en modul i rutan i följande versioner</span><span class="sxs-lookup"><span data-stu-id="c1ad7-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c1ad7-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) eller senare</span><span class="sxs-lookup"><span data-stu-id="c1ad7-105">[Windows 10](https://www.microsoft.com/windows/get-windows-10) or newer</span></span>
- <span data-ttu-id="c1ad7-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) eller senare</span><span class="sxs-lookup"><span data-stu-id="c1ad7-106">[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/windows-server-2016) or newer</span></span>
- <span data-ttu-id="c1ad7-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="c1ad7-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c1ad7-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c1ad7-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="c1ad7-109">Hämta PowerShellGet modul för PowerShell version 3.0 och 4.0</span><span class="sxs-lookup"><span data-stu-id="c1ad7-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="c1ad7-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="c1ad7-110">PackageManagement MSI</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c1ad7-111">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="c1ad7-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="c1ad7-112">Innan du uppdaterar PowerShellGet, bör du alltid installera den senaste Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="c1ad7-113">Om du vill göra det kör du följande i en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-113">To do that, run the following in an elevated PowerShell session.</span></span>

```powershell
Install-PackageProvider Nuget –Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c1ad7-114">Du kan installera den senaste PowerShellGet för system med PowerShell 5.0 (eller senare)</span><span class="sxs-lookup"><span data-stu-id="c1ad7-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="c1ad7-115">Om du vill göra detta på Windows 10, kör Windows Server 2016, alla system med WMF 5.0 eller 5.1 installerat eller alla system med PowerShell 6, du följande kommandon från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- <span data-ttu-id="c1ad7-116">Använda Update-modulen för att få nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-116">Use Update-Module to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a><span data-ttu-id="c1ad7-117">För datorer som kör PowerShell 3 eller 4 för PowerShell, som har installerat den [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="c1ad7-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)</span></span>

- <span data-ttu-id="c1ad7-118">Använd nedan PowerShellGet cmdlet från en upphöjd PowerShell-session för att spara modulerna till en lokal katalog</span><span class="sxs-lookup"><span data-stu-id="c1ad7-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- <span data-ttu-id="c1ad7-119">Se till att PowerShellGet och PackageManagment-moduler inte har lästs in i andra processer.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="c1ad7-120">Ta bort innehållet i `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappar.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="c1ad7-121">Öppna igen PS-konsolen med förhöjd behörighet och kör sedan följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="c1ad7-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
```