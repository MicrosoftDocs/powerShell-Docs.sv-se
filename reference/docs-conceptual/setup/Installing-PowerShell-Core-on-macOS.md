---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611495"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="fed6a-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="fed6a-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="fed6a-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="fed6a-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="fed6a-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="fed6a-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="fed6a-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="fed6a-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="fed6a-107">Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="fed6a-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="fed6a-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="fed6a-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="fed6a-109">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="fed6a-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="fed6a-110">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fed6a-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="fed6a-111">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="fed6a-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="fed6a-112">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fed6a-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="fed6a-113">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="fed6a-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="fed6a-114">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fed6a-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="fed6a-115">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="fed6a-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="fed6a-116">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="fed6a-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="fed6a-117">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="fed6a-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="fed6a-118">När du har installerat Homebrew är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fed6a-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="fed6a-119">Installera först [Cask versioner] [ cask-versions] som hjälper dig att installera alternativa versioner av cask paket:</span><span class="sxs-lookup"><span data-stu-id="fed6a-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="fed6a-120">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fed6a-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="fed6a-121">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="fed6a-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="fed6a-122">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fed6a-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="fed6a-123">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="fed6a-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="fed6a-124">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="fed6a-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="fed6a-125">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="fed6a-125">Installation via Direct Download</span></span>

<span data-ttu-id="fed6a-126">Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="fed6a-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="fed6a-127">från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="fed6a-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="fed6a-128">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="fed6a-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="fed6a-129">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="fed6a-129">Binary Archives</span></span>

<span data-ttu-id="fed6a-130">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS-plattformen att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="fed6a-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="fed6a-131">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="fed6a-131">Installing binary archives on macOS</span></span>

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

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="fed6a-132">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="fed6a-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="fed6a-133">Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:</span><span class="sxs-lookup"><span data-stu-id="fed6a-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="fed6a-134">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="fed6a-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="fed6a-135">Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar](#paths) avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="fed6a-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="fed6a-136">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="fed6a-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="fed6a-137">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="fed6a-137">Paths</span></span>

* <span data-ttu-id="fed6a-138">`$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="fed6a-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="fed6a-139">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fed6a-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="fed6a-140">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="fed6a-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="fed6a-141">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fed6a-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fed6a-142">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="fed6a-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="fed6a-143">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="fed6a-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="fed6a-144">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="fed6a-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="fed6a-145">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="fed6a-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="fed6a-146">Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="fed6a-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="fed6a-147">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="fed6a-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="fed6a-148">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="fed6a-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="fed6a-149">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och symlink placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="fed6a-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fed6a-150">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="fed6a-150">Additional Resources</span></span>

* <span data-ttu-id="fed6a-151">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="fed6a-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="fed6a-152">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="fed6a-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="fed6a-153">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="fed6a-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
