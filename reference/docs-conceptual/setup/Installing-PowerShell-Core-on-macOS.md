---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587473"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="0f5a3-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="0f5a3-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="0f5a3-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="0f5a3-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0f5a3-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-via-homebrew-on-macos-1012"></a><span data-ttu-id="0f5a3-107">Installation via Homebrew på macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="0f5a3-107">Installation via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0f5a3-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0f5a3-109">Ange från ett terminalfönster `brew` att köra Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-109">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0f5a3-110">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="0f5a3-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0f5a3-111">Om du har installerat Homebrew tidigare är det alltid en bra idé att köra 'brew uppdatera återställa ”& &” brew update ”.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-111">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

> <span data-ttu-id="0f5a3-112">Äldre versioner av Homebrew används den trycker du på ”caskroom/cask”, som har inaktuella och migreras till 'homebrew/cask ”.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-112">Older versions of Homebrew used the tap 'caskroom/cask', which has been deprecated, and migrated into 'homebrew/cask'.</span></span>  <span data-ttu-id="0f5a3-113">Mer information finns på [Homebrew cask][cask].</span><span class="sxs-lookup"><span data-stu-id="0f5a3-113">More information can be found at [Homebrew-cask][cask].</span></span> <span data-ttu-id="0f5a3-114">Använd kommandot ”brew trycker du på” Visa en lista över dina aktuella TAP.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-114">Use the 'brew tap' command to list your current taps.</span></span>  <span data-ttu-id="0f5a3-115">Om du ser ”caskroom/cask, kan du använda 'brew update' har Homebrew migrera TAP.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-115">If you see 'caskroom/cask' you can use 'brew update' to have Homebrew migrate the taps.</span></span>

```sh
brew tap
brew update
```

<span data-ttu-id="0f5a3-116">När du har installerat/uppdaterat Homebrew, är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-116">Once you've installed/updated Homebrew, installing PowerShell is easy.</span></span>

<span data-ttu-id="0f5a3-117">Installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-117">To install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0f5a3-118">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-118">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="0f5a3-119">För att avsluta PowerShell och återgå till bash, använder du avslutningskommandot.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-119">To exit PowerShell, and return to bash, use the 'exit' command.</span></span>
```sh
exit
```

<span data-ttu-id="0f5a3-120">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-120">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="0f5a3-121">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-121">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installing-preview-via-homebrew-on-macos-1012"></a><span data-ttu-id="0f5a3-122">Installera förhandsversionen via Homebrew på macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="0f5a3-122">Installing Preview via Homebrew on macOS 10.12+</span></span>

<span data-ttu-id="0f5a3-123">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-123">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="0f5a3-124">Ange från ett terminalfönster `brew` att köra Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-124">From a terminal window, type `brew` to run Homebrew.</span></span>  <span data-ttu-id="0f5a3-125">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="0f5a3-125">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

> [!NOTE]
> <span data-ttu-id="0f5a3-126">Om du har installerat Homebrew tidigare är det alltid en bra idé att köra 'brew uppdatera återställa ”& &” brew update ”.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-126">If you installed Homebrew in the past, it's always a good idea to run 'brew update-reset' && 'brew update'.</span></span>
```sh
brew update-reset
brew update
```

<span data-ttu-id="0f5a3-127">Sedan måste du trycker på den `versions` slags lagringsplatsen för att hämta preview-paketet:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-127">Then, you must tap the `versions` casks repository to get the preview package:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="0f5a3-128">Så här installerar förhandsversionen av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-128">To install PowerShell Preview:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="0f5a3-129">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="0f5a3-130">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera förhandsversionen av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-130">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell Preview:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="0f5a3-131">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

### <a name="installation-via-direct-download"></a><span data-ttu-id="0f5a3-132">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="0f5a3-132">Installation via Direct Download</span></span>

<span data-ttu-id="0f5a3-133">Hämtningspaketet PKG `powershell-6.0.2-osx.10.12-x64.pkg` från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-133">Download the PKG package `powershell-6.0.2-osx.10.12-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="0f5a3-134">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-134">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="0f5a3-135">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="0f5a3-135">Binary Archives</span></span>

<span data-ttu-id="0f5a3-136">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS och Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-136">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="0f5a3-137">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="0f5a3-137">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="0f5a3-138">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="0f5a3-138">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="0f5a3-139">Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-139">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0f5a3-140">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="0f5a3-140">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0f5a3-141">Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar][] avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-141">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="0f5a3-142">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-142">This is not necessary if you installed with Homebrew.</span></span>

[Sökvägar]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="0f5a3-144">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="0f5a3-144">Paths</span></span>

* <span data-ttu-id="0f5a3-145">`$PSHOME` är `/usr/local/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-145">`$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="0f5a3-146">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-146">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0f5a3-147">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-147">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0f5a3-148">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-148">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0f5a3-149">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-149">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0f5a3-150">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-150">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0f5a3-151">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0f5a3-151">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0f5a3-152">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-152">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="0f5a3-153">Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-153">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0f5a3-154">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-154">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="0f5a3-155">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-155">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="0f5a3-156">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.2/`, och symlink placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0f5a3-156">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.2/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0f5a3-157">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="0f5a3-157">Additional Resources</span></span>

* <span data-ttu-id="0f5a3-158">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="0f5a3-158">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="0f5a3-159">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="0f5a3-159">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="0f5a3-160">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="0f5a3-160">[Homebrew-Cask][cask]</span></span>


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
