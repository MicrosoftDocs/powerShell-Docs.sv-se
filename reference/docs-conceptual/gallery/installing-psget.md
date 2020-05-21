---
ms.date: 09/19/2019
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: f42eb0df101eb63a5dc267196fa9f666747b8e35
ms.sourcegitcommit: 23ea4a36ee85f923684657de5313a5adf0b6b094
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83727803"
---
# <a name="installing-powershellget"></a><span data-ttu-id="e7be0-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e7be0-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="e7be0-104">PowerShellGet är en modul i box i följande versioner</span><span class="sxs-lookup"><span data-stu-id="e7be0-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="e7be0-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="e7be0-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="e7be0-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="e7be0-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="e7be0-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="e7be0-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="e7be0-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="e7be0-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="e7be0-109">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="e7be0-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="e7be0-110">Innan du uppdaterar **PowerShellGet**bör du alltid installera den senaste **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="e7be0-110">Before updating **PowerShellGet**, you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="e7be0-111">Kör följande kommando från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e7be0-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="e7be0-112">För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e7be0-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="e7be0-113">Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="e7be0-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

<span data-ttu-id="e7be0-114">Använd `Update-Module` för att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="e7be0-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="e7be0-115">För datorer som kör PowerShell 3,0 eller PowerShell 4,0</span><span class="sxs-lookup"><span data-stu-id="e7be0-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="e7be0-116">Dessa anvisningar gäller för datorer där **PackageManagement Preview** är installerat eller inte har någon version av **PowerShellGet** installerad.</span><span class="sxs-lookup"><span data-stu-id="e7be0-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="e7be0-117">`Save-Module`Cmdleten används i båda uppsättningarna med instruktioner.</span><span class="sxs-lookup"><span data-stu-id="e7be0-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="e7be0-118">`Save-Module`hämtar och sparar en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="e7be0-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="e7be0-119">Modulens senaste version sparas till en angiven sökväg på den lokala datorn, men är inte installerad.</span><span class="sxs-lookup"><span data-stu-id="e7be0-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="e7be0-120">Om du vill installera modulerna i PowerShell 3,0 eller 4,0 kopierar du modulen sparade mappar till `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="e7be0-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="e7be0-121">Mer information finns i [Save-module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="e7be0-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="e7be0-122">PowerShell 3,0 och PowerShell 4,0 har endast stöd för en version av en modul.</span><span class="sxs-lookup"><span data-stu-id="e7be0-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="e7be0-123">Moduler som börjar i PowerShell 5,0 installeras i `<modulename>\<version>` .</span><span class="sxs-lookup"><span data-stu-id="e7be0-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="e7be0-124">Detta kan du installera flera versioner sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="e7be0-124">This allowed you to install multiple versions side-by-side.</span></span> <span data-ttu-id="e7be0-125">När du har laddat ned modulen med `Save-Module` måste du kopiera filerna från `<modulename>\<version>` till- `<modulename>` mappen på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="e7be0-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine.</span></span>

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="e7be0-126">Datorer med PackageManagement-förhands granskning installerad</span><span class="sxs-lookup"><span data-stu-id="e7be0-126">Computers with the PackageManagement Preview installed</span></span>

1. <span data-ttu-id="e7be0-127">Använd `Save-Module` för att spara modulerna till en lokal katalog från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="e7be0-127">From a PowerShell session, use `Save-Module` to save the modules to a local directory.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="e7be0-128">Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.</span><span class="sxs-lookup"><span data-stu-id="e7be0-128">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>
1. <span data-ttu-id="e7be0-129">Ta bort innehållet i mapparna: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` .</span><span class="sxs-lookup"><span data-stu-id="e7be0-129">Delete the contents of the folders: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.</span></span>
1. <span data-ttu-id="e7be0-130">Öppna PowerShell-konsolen med förhöjd behörighet och kör följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="e7be0-130">Reopen the PowerShell console with elevated permissions and run the following commands.</span></span>

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\<version>\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="e7be0-131">Datorer utan PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e7be0-131">Computers without PowerShellGet</span></span>

<span data-ttu-id="e7be0-132">För datorer utan någon version av **PowerShellGet** installerat krävs en dator med **PowerShellGet** installerat för att ladda ned modulerna.</span><span class="sxs-lookup"><span data-stu-id="e7be0-132">For computer's without any version of **PowerShellGet** installed, a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="e7be0-133">Använd **PowerShellGet** `Save-Module` för att hämta den aktuella versionen av **PowerShellGet**från den dator som har installerat PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="e7be0-133">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet**.</span></span> <span data-ttu-id="e7be0-134">Två mappar hämtas: **PowerShellGet** och **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="e7be0-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement**.</span></span> <span data-ttu-id="e7be0-135">Varje mapp innehåller en undermapp med ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="e7be0-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="e7be0-136">Kopiera mapparna **PowerShellGet** och **PackageManagement** till datorn som inte har **PowerShellGet** installerat.</span><span class="sxs-lookup"><span data-stu-id="e7be0-136">Copy the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed.</span></span>

   <span data-ttu-id="e7be0-137">Mål katalogen är:`$env:ProgramFiles\WindowsPowerShell\Modules`</span><span class="sxs-lookup"><span data-stu-id="e7be0-137">The destination directory is: `$env:ProgramFiles\WindowsPowerShell\Modules`</span></span>
