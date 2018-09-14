---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: 50b8dbbf26f02580e4be45978c926d5337da6b63
ms.sourcegitcommit: b235c58b34d23317076540631f5cf83f1f309c0d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45557168"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="eb64b-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="eb64b-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="eb64b-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="eb64b-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="eb64b-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="eb64b-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="eb64b-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="eb64b-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="eb64b-107">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="eb64b-107">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="eb64b-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="eb64b-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="eb64b-109">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="eb64b-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="eb64b-110">När du har installerat Homebrew är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb64b-110">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="eb64b-111">Installera först [Homebrew Cask][cask], så att du kan installera fler paket och installera [Cask-versioner] [cask-version] där du kan installera alternativ version av paket:</span><span class="sxs-lookup"><span data-stu-id="eb64b-111">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="eb64b-112">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb64b-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="eb64b-113">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="eb64b-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="eb64b-114">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb64b-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="eb64b-115">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="eb64b-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="eb64b-116">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="eb64b-116">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="eb64b-117">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="eb64b-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="eb64b-118">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="eb64b-118">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="eb64b-119">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="eb64b-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="eb64b-120">När du har installerat Homebrew är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb64b-120">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="eb64b-121">Installera först [Homebrew Cask][cask], så att du kan installera fler paket och installera [Cask-versioner] [cask-version] där du kan installera alternativ version av paket:</span><span class="sxs-lookup"><span data-stu-id="eb64b-121">First, install [Homebrew-Cask][cask], so you can install more packages and install [Cask-Versions][cask-version] which lets you install alternative versions of packages:</span></span>

```sh
brew tap caskroom/cask
brew tap caskroom/versions
```

<span data-ttu-id="eb64b-122">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb64b-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="eb64b-123">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="eb64b-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="eb64b-124">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="eb64b-124">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="eb64b-125">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="eb64b-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="eb64b-126">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="eb64b-126">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions

### <a name="installation-via-direct-download"></a><span data-ttu-id="eb64b-127">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="eb64b-127">Installation via Direct Download</span></span>

<span data-ttu-id="eb64b-128">Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="eb64b-128">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="eb64b-129">från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="eb64b-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="eb64b-130">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="eb64b-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="eb64b-131">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="eb64b-131">Binary Archives</span></span>

<span data-ttu-id="eb64b-132">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS och Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="eb64b-132">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="eb64b-133">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="eb64b-133">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="eb64b-134">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="eb64b-134">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="eb64b-135">Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:</span><span class="sxs-lookup"><span data-stu-id="eb64b-135">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="eb64b-136">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="eb64b-136">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="eb64b-137">Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar][] avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="eb64b-137">To remove the additional PowerShell paths, please see the [paths][] section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="eb64b-138">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="eb64b-138">This is not necessary if you installed with Homebrew.</span></span>

[Sökvägar]:#paths
[paths]:#paths

## <a name="paths"></a><span data-ttu-id="eb64b-140">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="eb64b-140">Paths</span></span>

* <span data-ttu-id="eb64b-141">`$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="eb64b-141">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="eb64b-142">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="eb64b-142">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="eb64b-143">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="eb64b-143">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="eb64b-144">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="eb64b-144">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="eb64b-145">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="eb64b-145">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="eb64b-146">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="eb64b-146">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="eb64b-147">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="eb64b-147">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="eb64b-148">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="eb64b-148">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="eb64b-149">Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="eb64b-149">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="eb64b-150">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="eb64b-150">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="eb64b-151">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="eb64b-151">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="eb64b-152">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och symlink placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="eb64b-152">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eb64b-153">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="eb64b-153">Additional Resources</span></span>

* <span data-ttu-id="eb64b-154">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="eb64b-154">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="eb64b-155">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="eb64b-155">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="eb64b-156">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="eb64b-156">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
