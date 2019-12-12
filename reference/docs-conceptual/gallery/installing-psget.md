---
ms.date: 09/19/2019
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328982"
---
# <a name="installing-powershellget"></a><span data-ttu-id="f65d6-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f65d6-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="f65d6-104">PowerShellGet är en modul i box i följande versioner</span><span class="sxs-lookup"><span data-stu-id="f65d6-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="f65d6-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="f65d6-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="f65d6-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="f65d6-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="f65d6-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="f65d6-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="f65d6-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="f65d6-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="f65d6-109">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="f65d6-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="f65d6-110">Innan du uppdaterar **PowerShellGet**bör du alltid installera den senaste **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="f65d6-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="f65d6-111">Kör följande kommando från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="f65d6-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="f65d6-112">För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f65d6-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="f65d6-113">Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f65d6-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="f65d6-114">Använd `Update-Module` för att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="f65d6-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="f65d6-115">För datorer som kör PowerShell 3,0 eller PowerShell 4,0</span><span class="sxs-lookup"><span data-stu-id="f65d6-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="f65d6-116">Dessa anvisningar gäller för datorer där **PackageManagement Preview** är installerat eller inte har någon version av **PowerShellGet** installerad.</span><span class="sxs-lookup"><span data-stu-id="f65d6-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="f65d6-117">`Save-Module`-cmdleten används i båda uppsättningarna med instruktioner.</span><span class="sxs-lookup"><span data-stu-id="f65d6-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="f65d6-118">`Save-Module` hämtar och sparar en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="f65d6-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="f65d6-119">Modulens senaste version sparas till en angiven sökväg på den lokala datorn, men är inte installerad.</span><span class="sxs-lookup"><span data-stu-id="f65d6-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="f65d6-120">Mer information finns i [Save-module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="f65d6-120">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="f65d6-121">Datorer med PackageManagement-förhands granskning installerad</span><span class="sxs-lookup"><span data-stu-id="f65d6-121">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="f65d6-122">Använd `Save-Module` för att spara modulerna till en lokal katalog från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="f65d6-122">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="f65d6-123">Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.</span><span class="sxs-lookup"><span data-stu-id="f65d6-123">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="f65d6-124">Ta bort innehållet i mapparna: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span><span class="sxs-lookup"><span data-stu-id="f65d6-124">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="f65d6-125">Öppna PowerShell-konsolen med förhöjd behörighet och kör följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="f65d6-125">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="f65d6-126">Datorer utan PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f65d6-126">Computers without PowerShellGet</span></span>

<span data-ttu-id="f65d6-127">För datorer utan någon version av **PowerShellGet** installerat krävs en dator med **PowerShellGet** installerat för att ladda ned modulerna.</span><span class="sxs-lookup"><span data-stu-id="f65d6-127">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="f65d6-128">Använd `Save-Module` för att hämta den aktuella versionen av **PowerShellGet**från den dator där **PowerShellGet** är installerad.</span><span class="sxs-lookup"><span data-stu-id="f65d6-128">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="f65d6-129">Två mappar hämtas: **PowerShellGet** och **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="f65d6-129">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="f65d6-130">Varje mapp innehåller en undermapp med ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="f65d6-130">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="f65d6-131">Kopiera mapparna **PowerShellGet** och **PackageManagement** till datorn som inte har **PowerShellGet** installerat.</span><span class="sxs-lookup"><span data-stu-id="f65d6-131">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="f65d6-132">Mål katalogen är: `$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="f65d6-132">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
