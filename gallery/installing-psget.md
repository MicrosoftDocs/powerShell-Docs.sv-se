---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 5c51cb1c7ea2538cc5f8503ce6c5d80edda70e15
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002231"
---
# <a name="installing-powershellget"></a><span data-ttu-id="c5ae8-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c5ae8-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c5ae8-104">PowerShellGet är en nyckelfärdig modul i följande versioner</span><span class="sxs-lookup"><span data-stu-id="c5ae8-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c5ae8-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="c5ae8-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="c5ae8-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="c5ae8-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="c5ae8-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="c5ae8-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c5ae8-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c5ae8-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a><span data-ttu-id="c5ae8-109">Hämta PowerShellGet-modul för PowerShell version 3.0 och 4.0</span><span class="sxs-lookup"><span data-stu-id="c5ae8-109">Get PowerShellGet module for PowerShell versions 3.0 and 4.0</span></span>

- [<span data-ttu-id="c5ae8-110">PackageManagement MSI</span><span class="sxs-lookup"><span data-stu-id="c5ae8-110">PackageManagement MSI</span></span>](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c5ae8-111">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="c5ae8-111">Get the latest version from PowerShell Gallery</span></span>

- <span data-ttu-id="c5ae8-112">Innan du uppdaterar PowerShellGet, bör du alltid installera den senaste Nuget-providern.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-112">Before updating PowerShellGet, you should always install the latest Nuget provider.</span></span> <span data-ttu-id="c5ae8-113">Om du vill göra det, kör du följande i en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-113">To do that, run the following in an elevated PowerShell session.</span></span>

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c5ae8-114">Du kan installera den senaste PowerShellGet för system med PowerShell 5.0 (eller senare)</span><span class="sxs-lookup"><span data-stu-id="c5ae8-114">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

- <span data-ttu-id="c5ae8-115">Om du vill göra detta på Windows 10, kör Windows Server 2016, alla system med WMF 5.0 eller 5.1 installerad eller ett system med PowerShell 6, du följande kommandon från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-115">To do this on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- <span data-ttu-id="c5ae8-116">Använd `Update-Module` att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-116">Use `Update-Module` to get newer versions.</span></span>

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a><span data-ttu-id="c5ae8-117">För system som kör PowerShell 3 eller PowerShell 4, som har installerat den [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span><span class="sxs-lookup"><span data-stu-id="c5ae8-117">For systems running PowerShell 3 or PowerShell 4, that have installed the [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)</span></span>

- <span data-ttu-id="c5ae8-118">Använda PowerShellGet cmdleten från en upphöjd PowerShell-session nedan för att spara modulerna till en lokal katalog</span><span class="sxs-lookup"><span data-stu-id="c5ae8-118">Use below PowerShellGet cmdlet from an elevated PowerShell session to save the modules to a local directory</span></span>

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- <span data-ttu-id="c5ae8-119">Se till att PowerShellGet och PackageManagment moduler inte har lästs in i andra processer.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-119">Ensure that PowerShellGet and PackageManagment modules are not loaded in any other processes.</span></span>
- <span data-ttu-id="c5ae8-120">Ta bort innehållet i `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappar.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-120">Delete contents of `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and  `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` folders.</span></span>
- <span data-ttu-id="c5ae8-121">Öppnar PS-konsolen med förhöjd behörighet och kör sedan följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="c5ae8-121">Re-open the PS Console with elevated permissions then run the following commands.</span></span>

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
