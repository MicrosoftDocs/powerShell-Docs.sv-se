---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293409"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="11196-103">Installera PowerShell Core i macOS</span><span class="sxs-lookup"><span data-stu-id="11196-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="11196-104">PowerShell Core stöder macOS 10.12 och högre.</span><span class="sxs-lookup"><span data-stu-id="11196-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="11196-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="11196-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="11196-106">När paketet har installerats, köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="11196-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="11196-107">Om Brew</span><span class="sxs-lookup"><span data-stu-id="11196-107">About Brew</span></span>

<span data-ttu-id="11196-108">[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="11196-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="11196-109">Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="11196-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="11196-110">Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="11196-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="11196-111">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="11196-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="11196-112">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="11196-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="11196-113">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="11196-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="11196-114">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="11196-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="11196-115">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="11196-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="11196-116">Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre</span><span class="sxs-lookup"><span data-stu-id="11196-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="11196-117">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="11196-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="11196-118">När du har installerat Homebrew, kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="11196-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="11196-119">Installera först den [Cask versioner] [ cask-versions] paket som hjälper dig att installera alternativa versioner av cask paket:</span><span class="sxs-lookup"><span data-stu-id="11196-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="11196-120">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="11196-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="11196-121">Slutligen kan du kontrollera att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="11196-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="11196-122">När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="11196-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="11196-123">Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.</span><span class="sxs-lookup"><span data-stu-id="11196-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="11196-124">och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="11196-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="11196-125">Installationen via Direct hämtning</span><span class="sxs-lookup"><span data-stu-id="11196-125">Installation via Direct Download</span></span>

<span data-ttu-id="11196-126">Ladda ned PKG-paketet</span><span class="sxs-lookup"><span data-stu-id="11196-126">Download the PKG package</span></span>
`powershell-6.2.0-osx-x64.pkg`
<span data-ttu-id="11196-127">från den [släpper][] sida på din macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="11196-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="11196-128">Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="11196-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="11196-129">Installera [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="11196-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="11196-130">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="11196-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="11196-131">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="11196-131">Binary Archives</span></span>

<span data-ttu-id="11196-132">PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS-plattformen att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="11196-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="11196-133">Installera binär Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="11196-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="11196-134">Installera [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="11196-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="11196-135">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="11196-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="11196-136">Installation av beroenden</span><span class="sxs-lookup"><span data-stu-id="11196-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="11196-137">Installera XCode-kommandoradsverktyg</span><span class="sxs-lookup"><span data-stu-id="11196-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="11196-138">Installera OpenSSL</span><span class="sxs-lookup"><span data-stu-id="11196-138">Install OpenSSL</span></span>

<span data-ttu-id="11196-139">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="11196-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="11196-140">Du kan installera via MacPorts eller Brew.</span><span class="sxs-lookup"><span data-stu-id="11196-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="11196-141">Installera OpenSSL, via Brew</span><span class="sxs-lookup"><span data-stu-id="11196-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="11196-142">Se [om Brew](#about-brew) information om Brew.</span><span class="sxs-lookup"><span data-stu-id="11196-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="11196-143">Om du vill installera OpenSSL, kör `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="11196-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="11196-144">Installera OpenSSL, via MacPorts</span><span class="sxs-lookup"><span data-stu-id="11196-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="11196-145">Installera den [XCode kommandoradsverktyg](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="11196-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="11196-146">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="11196-146">Install MacPorts.</span></span>
   <span data-ttu-id="11196-147">Om du behöver mer information, referera till den [installationsguide](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="11196-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="11196-148">Uppdatera MacPorts genom att köra `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="11196-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="11196-149">Uppgradera MacPorts paket genom att köra `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="11196-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="11196-150">Installera OpenSSL, genom att köra `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="11196-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="11196-151">Länka bibliotek för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="11196-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="11196-152">Avinstallera PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="11196-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="11196-153">Om du har installerat PowerShell med Homebrew kan du använda följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="11196-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="11196-154">Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="11196-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="11196-155">Om du vill ta bort ytterligare PowerShell-sökvägar, referera till den [sökvägar](#paths) i det här dokumentet och ta bort sökvägar med hjälp av `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="11196-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="11196-156">Detta är inte nödvändigt om du installerade med Homebrew.</span><span class="sxs-lookup"><span data-stu-id="11196-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="11196-157">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="11196-157">Paths</span></span>

* `$PSHOME` <span data-ttu-id="11196-158">is</span><span class="sxs-lookup"><span data-stu-id="11196-158">is</span></span> `/usr/local/microsoft/powershell/6.2.0/`
* <span data-ttu-id="11196-159">Användarprofiler som ska läsas från</span><span class="sxs-lookup"><span data-stu-id="11196-159">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="11196-160">Standardprofiler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="11196-160">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="11196-161">Moduler som användaren kommer att läsas från</span><span class="sxs-lookup"><span data-stu-id="11196-161">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="11196-162">Delade moduler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="11196-162">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="11196-163">Standardmoduler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="11196-163">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="11196-164">PSReadline historik kommer att läggas till</span><span class="sxs-lookup"><span data-stu-id="11196-164">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="11196-165">Profilerna respekterar konfiguration för PowerShell-per värd.</span><span class="sxs-lookup"><span data-stu-id="11196-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="11196-166">Så värdspecifika standardprofilen finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="11196-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="11196-167">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.</span><span class="sxs-lookup"><span data-stu-id="11196-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="11196-168">Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="11196-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="11196-169">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.2.0/`, och den symboliska länken är placerad på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="11196-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="11196-170">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="11196-170">Additional Resources</span></span>

* <span data-ttu-id="11196-171">[Homebrew Web][brew]</span><span class="sxs-lookup"><span data-stu-id="11196-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="11196-172">[Homebrew Github-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="11196-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="11196-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="11196-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[<span data-ttu-id="11196-174">Versioner</span><span class="sxs-lookup"><span data-stu-id="11196-174">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
