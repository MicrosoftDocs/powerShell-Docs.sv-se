---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998511"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="45de7-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="45de7-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="45de7-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="45de7-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="45de7-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="45de7-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="45de7-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="45de7-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="45de7-107">Om Brew</span><span class="sxs-lookup"><span data-stu-id="45de7-107">About Brew</span></span>

<span data-ttu-id="45de7-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="45de7-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="45de7-109">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="45de7-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="45de7-110">Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="45de7-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="45de7-111">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="45de7-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="45de7-112">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45de7-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="45de7-113">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="45de7-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="45de7-114">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45de7-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="45de7-115">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="45de7-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="45de7-116">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="45de7-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="45de7-117">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="45de7-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="45de7-118">När du har installerat Homebrew är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="45de7-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="45de7-119">Installera först [Cask versioner] [ cask-versions] som hjälper dig att installera alternativa versioner av cask paket:</span><span class="sxs-lookup"><span data-stu-id="45de7-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="45de7-120">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45de7-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="45de7-121">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="45de7-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="45de7-122">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="45de7-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="45de7-123">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="45de7-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="45de7-124">och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="45de7-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="45de7-125">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="45de7-125">Installation via Direct Download</span></span>

<span data-ttu-id="45de7-126">Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="45de7-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="45de7-127">från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="45de7-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="45de7-128">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="45de7-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="45de7-129">Installera [OpenSSL](#install-openssl) som krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="45de7-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="45de7-130">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="45de7-130">Binary Archives</span></span>

<span data-ttu-id="45de7-131">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS-plattformen att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="45de7-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="45de7-132">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="45de7-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="45de7-133">Installera [OpenSSL](#install-openssl) som krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="45de7-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="45de7-134">Installation av beroenden</span><span class="sxs-lookup"><span data-stu-id="45de7-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="45de7-135">Installera XCode kommandoradsverktyg</span><span class="sxs-lookup"><span data-stu-id="45de7-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="45de7-136">Installera OpenSSL</span><span class="sxs-lookup"><span data-stu-id="45de7-136">Install OpenSSL</span></span>

<span data-ttu-id="45de7-137">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="45de7-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="45de7-138">Du kan installera via MacPorts eller Brew.</span><span class="sxs-lookup"><span data-stu-id="45de7-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="45de7-139">Installera OpenSSL, via Brew</span><span class="sxs-lookup"><span data-stu-id="45de7-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="45de7-140">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="45de7-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="45de7-141">Kör `brew install openssl` installera OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="45de7-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="45de7-142">Installera OpenSSL, via MacPorts</span><span class="sxs-lookup"><span data-stu-id="45de7-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="45de7-143">Installera den [XCode kommandoradsverktyg](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="45de7-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="45de7-144">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="45de7-144">Install MacPorts.</span></span>
   <span data-ttu-id="45de7-145">Se den [installationsguide](https://guide.macports.org/chunked/installing.macports.html) om du behöver mer information.</span><span class="sxs-lookup"><span data-stu-id="45de7-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="45de7-146">Uppdatera MacPorts genom att köra `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="45de7-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="45de7-147">Uppgradera MacPorts paket genom att köra `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="45de7-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="45de7-148">Installera OpenSSL, genom att köra genom att köra `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="45de7-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="45de7-149">Länka biblioteken så att PowerShell kan använda den.</span><span class="sxs-lookup"><span data-stu-id="45de7-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="45de7-150">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="45de7-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="45de7-151">Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:</span><span class="sxs-lookup"><span data-stu-id="45de7-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="45de7-152">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="45de7-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="45de7-153">Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar](#paths) avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="45de7-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="45de7-154">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="45de7-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="45de7-155">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="45de7-155">Paths</span></span>

* <span data-ttu-id="45de7-156">`$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="45de7-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="45de7-157">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="45de7-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="45de7-158">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="45de7-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="45de7-159">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="45de7-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45de7-160">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="45de7-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="45de7-161">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="45de7-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="45de7-162">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="45de7-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="45de7-163">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="45de7-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="45de7-164">Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="45de7-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="45de7-165">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="45de7-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="45de7-166">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="45de7-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="45de7-167">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och den symboliska länken är placerad på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="45de7-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="45de7-168">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="45de7-168">Additional Resources</span></span>

* <span data-ttu-id="45de7-169">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="45de7-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="45de7-170">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="45de7-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="45de7-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="45de7-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
