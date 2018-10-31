---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: e226cd64f8788ae74dc72fdc0cd219923b7a2cd6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002367"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="8351c-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="8351c-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="8351c-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="8351c-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="8351c-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="8351c-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8351c-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="8351c-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8351c-107">Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="8351c-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8351c-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="8351c-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8351c-109">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="8351c-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="8351c-110">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8351c-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="8351c-111">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="8351c-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="8351c-112">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8351c-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="8351c-113">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8351c-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8351c-114">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="8351c-114">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8351c-115">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="8351c-115">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8351c-116">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="8351c-116">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="8351c-117">När du har installerat Homebrew är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8351c-117">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="8351c-118">Installera först [Cask versioner] [ cask-versions] som hjälper dig att installera alternativa versioner av cask paket:</span><span class="sxs-lookup"><span data-stu-id="8351c-118">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="8351c-119">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8351c-119">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="8351c-120">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="8351c-120">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="8351c-121">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8351c-121">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="8351c-122">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="8351c-122">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="8351c-123">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8351c-123">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="8351c-124">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="8351c-124">Installation via Direct Download</span></span>

<span data-ttu-id="8351c-125">Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="8351c-125">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="8351c-126">från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="8351c-126">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="8351c-127">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="8351c-127">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="8351c-128">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="8351c-128">Binary Archives</span></span>

<span data-ttu-id="8351c-129">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS-plattformen att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="8351c-129">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="8351c-130">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="8351c-130">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="8351c-131">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8351c-131">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="8351c-132">Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:</span><span class="sxs-lookup"><span data-stu-id="8351c-132">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="8351c-133">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="8351c-133">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="8351c-134">Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar](#paths) avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="8351c-134">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="8351c-135">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8351c-135">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="8351c-136">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="8351c-136">Paths</span></span>

* <span data-ttu-id="8351c-137">`$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="8351c-137">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="8351c-138">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8351c-138">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8351c-139">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8351c-139">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8351c-140">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8351c-140">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8351c-141">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8351c-141">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8351c-142">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8351c-142">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8351c-143">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8351c-143">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8351c-144">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="8351c-144">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="8351c-145">Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="8351c-145">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8351c-146">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="8351c-146">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="8351c-147">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="8351c-147">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="8351c-148">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och symlink placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="8351c-148">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8351c-149">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="8351c-149">Additional Resources</span></span>

* <span data-ttu-id="8351c-150">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="8351c-150">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="8351c-151">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="8351c-151">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="8351c-152">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="8351c-152">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
