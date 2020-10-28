---
ms.date: 09/19/2019
title: Installera PowerShellGet
description: Den här artikeln beskriver hur du installerar PowerShellGet-modulen i olika versioner av PowerShell.
ms.openlocfilehash: 06ec331446849784bb8464912fbce0e5a940823f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662156"
---
# <a name="installing-powershellget"></a><span data-ttu-id="8d498-103">Installera PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d498-103">Installing PowerShellGet</span></span>

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a><span data-ttu-id="8d498-104">PowerShellGet är en modul i box i följande versioner</span><span class="sxs-lookup"><span data-stu-id="8d498-104">PowerShellGet is an in-box module in the following releases</span></span>

- <span data-ttu-id="8d498-105">[Windows 10](https://www.microsoft.com/windows) eller senare</span><span class="sxs-lookup"><span data-stu-id="8d498-105">[Windows 10](https://www.microsoft.com/windows) or newer</span></span>
- <span data-ttu-id="8d498-106">[Windows Server 2016](/windows-server/windows-server) eller senare</span><span class="sxs-lookup"><span data-stu-id="8d498-106">[Windows Server 2016](/windows-server/windows-server) or newer</span></span>
- <span data-ttu-id="8d498-107">[Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare</span><span class="sxs-lookup"><span data-stu-id="8d498-107">[Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) or newer</span></span>
- [<span data-ttu-id="8d498-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="8d498-108">PowerShell 6</span></span>](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a><span data-ttu-id="8d498-109">Hämta den senaste versionen från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d498-109">Get the latest version from PowerShell Gallery</span></span>

<span data-ttu-id="8d498-110">Innan du uppdaterar **PowerShellGet** bör du alltid installera den senaste **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="8d498-110">Before updating **PowerShellGet** , you should always install the latest **NuGet** provider.</span></span> <span data-ttu-id="8d498-111">Kör följande kommando från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8d498-111">From an elevated PowerShell session, run the following command.</span></span>

```powershell
Install-PackageProvider -Name NuGet -Force
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a><span data-ttu-id="8d498-112">För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d498-112">For systems with PowerShell 5.0 (or newer) you can install the latest PowerShellGet</span></span>

<span data-ttu-id="8d498-113">Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="8d498-113">To install PowerShellGet on Windows 10, Windows Server 2016, any system with WMF 5.0 or 5.1 installed, or any system with PowerShell 6, run the following commands from an elevated PowerShell session.</span></span>

```powershell
Install-Module -Name PowerShellGet -Force
```

<span data-ttu-id="8d498-114">Använd `Update-Module` för att hämta nyare versioner.</span><span class="sxs-lookup"><span data-stu-id="8d498-114">Use `Update-Module` to get newer versions.</span></span>

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a><span data-ttu-id="8d498-115">För datorer som kör PowerShell 3,0 eller PowerShell 4,0</span><span class="sxs-lookup"><span data-stu-id="8d498-115">For computers running PowerShell 3.0 or PowerShell 4.0</span></span>

<span data-ttu-id="8d498-116">Dessa anvisningar gäller för datorer där **PackageManagement Preview** är installerat eller inte har någon version av **PowerShellGet** installerad.</span><span class="sxs-lookup"><span data-stu-id="8d498-116">These instructions apply to computers that have the **PackageManagement Preview** installed or don't have any version of **PowerShellGet** installed.</span></span>

<span data-ttu-id="8d498-117">`Save-Module`Cmdleten används i båda uppsättningarna med instruktioner.</span><span class="sxs-lookup"><span data-stu-id="8d498-117">The `Save-Module` cmdlet is used in both sets of instructions.</span></span> <span data-ttu-id="8d498-118">`Save-Module` hämtar och sparar en modul och eventuella beroenden från en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8d498-118">`Save-Module` downloads and saves a module and any dependencies from a registered repository.</span></span> <span data-ttu-id="8d498-119">Modulens senaste version sparas till en angiven sökväg på den lokala datorn, men är inte installerad.</span><span class="sxs-lookup"><span data-stu-id="8d498-119">The module's most current version is saved to a specified path on the local computer, but isn't installed.</span></span> <span data-ttu-id="8d498-120">Om du vill installera modulerna i PowerShell 3,0 eller 4,0 kopierar du modulen sparade mappar till `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="8d498-120">To install the modules in PowerShell 3.0 or 4.0, copy the module saved folders to `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>

<span data-ttu-id="8d498-121">Mer information finns i [Save-module](/powershell/module/PowershellGet/Save-Module).</span><span class="sxs-lookup"><span data-stu-id="8d498-121">For more information, see [Save-Module](/powershell/module/PowershellGet/Save-Module).</span></span>

> [!NOTE]
> <span data-ttu-id="8d498-122">PowerShell 3,0 och PowerShell 4,0 har endast stöd för en version av en modul.</span><span class="sxs-lookup"><span data-stu-id="8d498-122">PowerShell 3.0 and PowerShell 4.0 only supported one version of a module.</span></span> <span data-ttu-id="8d498-123">Moduler som börjar i PowerShell 5,0 installeras i `<modulename>\<version>` .</span><span class="sxs-lookup"><span data-stu-id="8d498-123">Starting in PowerShell 5.0, modules are installed in `<modulename>\<version>`.</span></span> <span data-ttu-id="8d498-124">På så sätt kan du installera flera versioner sida vid sida.</span><span class="sxs-lookup"><span data-stu-id="8d498-124">This allows you to install multiple versions side-by-side.</span></span> <span data-ttu-id="8d498-125">När du har laddat ned modulen med `Save-Module` måste du kopiera filerna från `<modulename>\<version>` till `<modulename>` -mappen på mål datorn, som du ser i anvisningarna nedan.</span><span class="sxs-lookup"><span data-stu-id="8d498-125">After downloading the module using `Save-Module` you must copy the files from the `<modulename>\<version>` to the `<modulename>` folder on the destination machine, as shown in the instructions below.</span></span>

#### <a name="preparatory-step-on-computers-running-powershell-30"></a><span data-ttu-id="8d498-126">Förberedelse steg för datorer som kör PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="8d498-126">Preparatory Step on computers running PowerShell 3.0</span></span>

<span data-ttu-id="8d498-127">Anvisningarna i avsnitten nedan installerar modulerna i katalogen `$env:ProgramFiles\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="8d498-127">The instructions in the sections below install the modules in directory `$env:ProgramFiles\WindowsPowerShell\Modules`.</span></span>
<span data-ttu-id="8d498-128">I PowerShell 3,0 visas den här katalogen inte i som `$env:PSModulePath` standard, så du måste lägga till den för att modulerna ska kunna läsas in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="8d498-128">In PowerShell 3.0, this directory isn't listed in `$env:PSModulePath` by default, so you'll need to add it in order for the modules to be auto-loaded.</span></span>

<span data-ttu-id="8d498-129">Öppna en upphöjd PowerShell-session och kör följande kommando (som börjar gälla i framtida sessioner):</span><span class="sxs-lookup"><span data-stu-id="8d498-129">Open an elevated PowerShell session and run the following command (which will take effect in future sessions):</span></span>

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a><span data-ttu-id="8d498-130">Datorer med PackageManagement-förhands granskning installerad</span><span class="sxs-lookup"><span data-stu-id="8d498-130">Computers with the PackageManagement Preview installed</span></span>

> [!NOTE]
> <span data-ttu-id="8d498-131">PackageManagement Preview var en nedladdnings bar komponent som gjorde PowerShellGet tillgänglig för PowerShell-versionerna 3 och 4, men den är inte längre tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="8d498-131">PackageManagement Preview was a downloadable component that made PowerShellGet available to PowerShell versions 3 and 4, but it is no longer available.</span></span>
> <span data-ttu-id="8d498-132">Kör om du vill testa om den har installerats på en specifik dator `Get-Module -ListAvailable PowerShellGet` .</span><span class="sxs-lookup"><span data-stu-id="8d498-132">To test if it was installed on a given computer, run `Get-Module -ListAvailable PowerShellGet`.</span></span>

1. <span data-ttu-id="8d498-133">Från en PowerShell-session använder `Save-Module` du för att hämta den aktuella versionen av **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="8d498-133">From a PowerShell session, use `Save-Module` to download the current version of **PowerShellGet** .</span></span> <span data-ttu-id="8d498-134">Två mappar hämtas: **PowerShellGet** och **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="8d498-134">Two folders are downloaded: **PowerShellGet** and **PackageManagement** .</span></span> <span data-ttu-id="8d498-135">Varje mapp innehåller en undermapp med ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="8d498-135">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="8d498-136">Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.</span><span class="sxs-lookup"><span data-stu-id="8d498-136">Ensure that the **PowerShellGet** and **PackageManagement** modules aren't loaded in any other processes.</span></span>

1. <span data-ttu-id="8d498-137">Öppna PowerShell-konsolen igen med utökade behörigheter och kör följande kommando.</span><span class="sxs-lookup"><span data-stu-id="8d498-137">Reopen the PowerShell console with elevated permissions and run the following command.</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a><span data-ttu-id="8d498-138">Datorer utan PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="8d498-138">Computers without PowerShellGet</span></span>

<span data-ttu-id="8d498-139">För datorer utan någon version av **PowerShellGet** installerat (test med `Get-Module -ListAvailable PowerShellGet` ) krävs en dator med **PowerShellGet** installerat för att hämta modulerna.</span><span class="sxs-lookup"><span data-stu-id="8d498-139">For computers without any version of **PowerShellGet** installed (test with `Get-Module -ListAvailable PowerShellGet`), a computer with **PowerShellGet** installed is needed to download the modules.</span></span>

1. <span data-ttu-id="8d498-140">Använd **PowerShellGet** `Save-Module` för att hämta den aktuella versionen av **PowerShellGet** från den dator som har installerat PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="8d498-140">From the computer that has **PowerShellGet** installed, use `Save-Module` to download the current version of **PowerShellGet** .</span></span> <span data-ttu-id="8d498-141">Två mappar hämtas: **PowerShellGet** och **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="8d498-141">Two folders are downloaded: **PowerShellGet** and **PackageManagement** .</span></span> <span data-ttu-id="8d498-142">Varje mapp innehåller en undermapp med ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="8d498-142">Each folder contains a subfolder with a version number.</span></span>

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. <span data-ttu-id="8d498-143">Kopiera respektive `<version>` undermapp i mapparna **PowerShellGet** och **PackageManagement** till datorn som inte har **PowerShellGet** installerad, i mappar `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` som kräver en upphöjd session.</span><span class="sxs-lookup"><span data-stu-id="8d498-143">Copy the respective `<version>` subfolder in the **PowerShellGet** and **PackageManagement** folders to the computer that doesn't have **PowerShellGet** installed, into folders `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` and `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` respectively, which requires an elevated session.</span></span>

1. <span data-ttu-id="8d498-144">Om du till exempel har åtkomst till download-mappen på den andra datorn, t. ex `ws1` . från mål datorn via en UNC-sökväg, så `\\ws1\C$\LocalFolder` öppnar du en PowerShell-konsol med förhöjd behörighet och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="8d498-144">For instance, if you can access the download folder on the other computer, say `ws1`, from the target computer via a UNC path, say `\\ws1\C$\LocalFolder`, open a PowerShell console with elevated permissions and run the following command:</span></span>

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
