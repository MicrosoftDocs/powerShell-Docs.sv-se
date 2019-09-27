---
title: Installera PowerShell Core i macOS
description: Information om hur du installerar PowerShell Core på macOS
ms.date: 12/12/2018
ms.openlocfilehash: a53cb5b7e159635dac45fb9ca3df28e86dffc653
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325264"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="d3fd4-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="d3fd4-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="d3fd4-104">PowerShell Core stöder macOS 10,12 och högre.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="d3fd4-105">Alla paket är tillgängliga på vår GitHub [][] -releases-sida.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="d3fd4-106">När paketet har installerats kör `pwsh` du från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="d3fd4-107">Om Brew</span><span class="sxs-lookup"><span data-stu-id="d3fd4-107">About Brew</span></span>

<span data-ttu-id="d3fd4-108">[Homebrew][brew] är den föredragna paket hanteraren för MacOS.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="d3fd4-109">Om kommandot inte hittas måste du installera homebrew enligt [deras instruktioner.][brew] `brew`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="d3fd4-110">Annars kan du installera PowerShell via [direkt hämtning](#installation-via-direct-download) eller från [binära Arkiv](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="d3fd4-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="d3fd4-111">Installation av den senaste stabila versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="d3fd4-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="d3fd4-112">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="d3fd4-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d3fd4-113">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="d3fd4-114">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="d3fd4-115">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="d3fd4-116">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="d3fd4-117">Installation av den senaste för hands versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="d3fd4-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="d3fd4-118">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="d3fd4-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d3fd4-119">När du har installerat homebrew kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="d3fd4-120">Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="d3fd4-121">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="d3fd4-122">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="d3fd4-123">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="d3fd4-124">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="d3fd4-125">och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="d3fd4-126">Installation via direkt hämtning</span><span class="sxs-lookup"><span data-stu-id="d3fd4-126">Installation via Direct Download</span></span>

<span data-ttu-id="d3fd4-127">Ladda ned PKG-paketet`powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="d3fd4-128">från sidan [utgåvor][] till din MacOS-dator.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="d3fd4-129">Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="d3fd4-130">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="d3fd4-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="d3fd4-131">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="d3fd4-132">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="d3fd4-132">Binary Archives</span></span>

<span data-ttu-id="d3fd4-133">PowerShell- `tar.gz` binärfiler tillhandahålls för MacOS-plattformen för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="d3fd4-134">Installera binära Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="d3fd4-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="d3fd4-135">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="d3fd4-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="d3fd4-136">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="d3fd4-137">Installerar beroenden</span><span class="sxs-lookup"><span data-stu-id="d3fd4-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="d3fd4-138">Installera XCode kommando rads verktyg</span><span class="sxs-lookup"><span data-stu-id="d3fd4-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="d3fd4-139">Installera OpenSSL</span><span class="sxs-lookup"><span data-stu-id="d3fd4-139">Install OpenSSL</span></span>

<span data-ttu-id="d3fd4-140">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="d3fd4-141">Du kan installera via MacPorts eller Brew.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="d3fd4-142">Installera OpenSSL via Brew</span><span class="sxs-lookup"><span data-stu-id="d3fd4-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="d3fd4-143">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="d3fd4-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="d3fd4-144">Kör `brew install openssl`för att installera openssl.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="d3fd4-145">Installera OpenSSL via MacPorts</span><span class="sxs-lookup"><span data-stu-id="d3fd4-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="d3fd4-146">Installera [kommando rads verktygen för Xcode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="d3fd4-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="d3fd4-147">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-147">Install MacPorts.</span></span>
   <span data-ttu-id="d3fd4-148">Om du behöver instruktioner kan du läsa mer i [installations guiden](https://guide.macports.org/chunked/installing.macports.html)för.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="d3fd4-149">Uppdatera MacPorts genom att `sudo port selfupdate`köra.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="d3fd4-150">Uppgradera MacPorts-paket genom `sudo port upgrade outdated`att köra.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="d3fd4-151">Installera OpenSSL genom att `sudo port install openssl`köra.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="d3fd4-152">Länka biblioteken för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="d3fd4-153">PowerShell-kärnan avinstalleras</span><span class="sxs-lookup"><span data-stu-id="d3fd4-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="d3fd4-154">Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="d3fd4-155">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="d3fd4-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="d3fd4-156">Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och `sudo rm`tar bort Sök vägarna med.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="d3fd4-157">Detta är inte nödvändigt om du har installerat med homebrew.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="d3fd4-158">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="d3fd4-158">Paths</span></span>

* <span data-ttu-id="d3fd4-159">`$PSHOME`utgör`/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="d3fd4-160">Användar profilerna kommer att läsas från`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="d3fd4-161">Standard profiler kommer att läsas från`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="d3fd4-162">Användarens moduler kommer att läsas från`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d3fd4-163">Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="d3fd4-164">Standardmoduler kommer att läsas från`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="d3fd4-165">PSReadline historik registreras i`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="d3fd4-166">Profilerna respekterar PowerShell-konfigurationen per värd.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="d3fd4-167">Så att den standardinställda värdbaserade profilen `Microsoft.PowerShell_profile.ps1` finns på samma platser.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="d3fd4-168">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="d3fd4-169">Eftersom MacOS är en härledning av BSD används prefixet `/usr/local` i stället för. `/opt`</span><span class="sxs-lookup"><span data-stu-id="d3fd4-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="d3fd4-170">Så, `$PSHOME` är `/usr/local/microsoft/powershell/6.2.0/`och den symboliska länken placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="d3fd4-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d3fd4-171">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="d3fd4-171">Additional Resources</span></span>

* <span data-ttu-id="d3fd4-172">[Homebrew-webb][brew]</span><span class="sxs-lookup"><span data-stu-id="d3fd4-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="d3fd4-173">[Homebrew GitHub-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="d3fd4-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="d3fd4-174">[Homebrew – Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="d3fd4-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[utgåvor]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
