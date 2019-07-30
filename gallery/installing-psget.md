---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601413"
---
# <a name="installing-powershellget"></a><span data-ttu-id="0ecf2-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="0ecf2-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="0ecf2-104">PowerShellGet är en modul i box i följande versioner</span><span class="sxs-lookup"><span data-stu-id="0ecf2-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="0ecf2-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="0ecf2-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="0ecf2-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="0ecf2-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="0ecf2-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="0ecf2-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="0ecf2-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="0ecf2-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="0ecf2-109">Hämta PowerShellGet-modul för PowerShell-versionerna 3,0 och 4,0</span><span class="sxs-lookup"><span data-stu-id="0ecf2-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="0ecf2-110">PackageManagement-MSI</span><span class="sxs-lookup"><span data-stu-id="0ecf2-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="0ecf2-111">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="0ecf2-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="0ecf2-112">Innan du uppdaterar PowerShellGet bör du alltid installera den senaste NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="0ecf2-113">Det gör du genom att köra följande i en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="0ecf2-114">För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="0ecf2-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="0ecf2-115">Om du vill göra detta på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerade, eller ett system med PowerShell 6, kör du följande kommandon från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- <span data-ttu-id="0ecf2-116">Använd `Update-Module` för att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="0ecf2-117">För system som kör PowerShell 3 eller PowerShell 4, som har installerat [PACKAGEMANAGEMENT MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="0ecf2-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="0ecf2-118">Använd nedanstående PowerShellGet-cmdlet från en upphöjd PowerShell-session för att spara modulerna i en lokal katalog</span><span class="sxs-lookup"><span data-stu-id="0ecf2-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="0ecf2-119">Se till att PowerShellGet-och PackageManagement-modulerna inte har lästs in i någon annan process.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-119">Ensure that PowerShellGet and PackageManagement modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="0ecf2-120">Ta bort innehåll `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` och mappar.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="0ecf2-121">Öppna PS-konsolen igen med utökade behörigheter och kör sedan följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="0ecf2-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
