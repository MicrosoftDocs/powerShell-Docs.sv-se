---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143600"
---
# <a name="installing-powershellget"></a><span data-ttu-id="c84be-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c84be-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="c84be-104">PowerShellGet är en modul i box i följande versioner</span><span class="sxs-lookup"><span data-stu-id="c84be-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="c84be-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="c84be-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="c84be-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="c84be-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="c84be-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="c84be-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="c84be-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="c84be-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="c84be-109">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="c84be-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="c84be-110">Innan du uppdaterar **PowerShellGet**bör du alltid installera den senaste **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="c84be-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="c84be-111">Kör följande kommando från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c84be-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="c84be-112">För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="c84be-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="c84be-113">Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c84be-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="c84be-114">Använd `Update-Module` för att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="c84be-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a><span data-ttu-id="c84be-115">För system som kör PowerShell 3 eller PowerShell 4, som har installerat PackageManagement Preview</span><span class="sxs-lookup"><span data-stu-id="c84be-115">For systems running PowerShell 3 or PowerShell 4, that have installed the PackageManagement Preview</span></span>

1. <span data-ttu-id="c84be-116">Använd `Save-Module` för att spara modulerna till en lokal katalog från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c84be-116">From an elevated PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. <span data-ttu-id="c84be-117">Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.</span><span class="sxs-lookup"><span data-stu-id="c84be-117">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="c84be-118">Ta bort innehållet i mapparna: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="c84be-118">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="c84be-119">Öppna PowerShell-konsolen med förhöjd behörighet och kör följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="c84be-119">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
