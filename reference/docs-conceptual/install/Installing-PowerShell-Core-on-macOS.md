---
title: Installera PowerShell i macOS
description: Information om hur du installerar PowerShell på macOS
ms.date: 05/21/2020
ms.openlocfilehash: 32b3ebf3eb4017af41fc1a062f2f0a2e08629a58
ms.sourcegitcommit: fd6a33b9fac973b3554fecfea7f51475e650a606
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83791463"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="15263-103">Installera PowerShell i macOS</span><span class="sxs-lookup"><span data-stu-id="15263-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="15263-104">PowerShell stöder macOS 10,12 och högre.</span><span class="sxs-lookup"><span data-stu-id="15263-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="15263-105">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="15263-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="15263-106">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="15263-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="15263-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="15263-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="15263-108">`/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="15263-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="15263-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="15263-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="15263-110">Om Brew</span><span class="sxs-lookup"><span data-stu-id="15263-110">About Brew</span></span>

<span data-ttu-id="15263-111">[Homebrew][brew] är den föredragna paket hanteraren för MacOS.</span><span class="sxs-lookup"><span data-stu-id="15263-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="15263-112">Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew].</span><span class="sxs-lookup"><span data-stu-id="15263-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="15263-113">Annars kan du installera PowerShell via [direkt hämtning](#installation-via-direct-download) eller från [binära Arkiv](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="15263-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="15263-114">Installation av den senaste stabila versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="15263-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="15263-115">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="15263-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="15263-116">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="15263-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="15263-117">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="15263-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="15263-118">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="15263-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="15263-119">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="15263-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="15263-120">Installation av den senaste för hands versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="15263-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="15263-121">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="15263-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="15263-122">När du har installerat homebrew kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="15263-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="15263-123">Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:</span><span class="sxs-lookup"><span data-stu-id="15263-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="15263-124">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="15263-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="15263-125">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="15263-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="15263-126">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="15263-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="15263-127">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="15263-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="15263-128">och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="15263-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="15263-129">Installation via direkt hämtning</span><span class="sxs-lookup"><span data-stu-id="15263-129">Installation via Direct Download</span></span>

<span data-ttu-id="15263-130">Ladda ned PKG-paketet`powershell-lts-7.0.1-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="15263-130">Download the PKG package `powershell-lts-7.0.1-osx-x64.pkg`</span></span>
<span data-ttu-id="15263-131">från sidan [utgåvor][] till din MacOS-dator.</span><span class="sxs-lookup"><span data-stu-id="15263-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="15263-132">Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:</span><span class="sxs-lookup"><span data-stu-id="15263-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.1-osx-x64.pkg -target /
```

<span data-ttu-id="15263-133">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="15263-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="15263-134">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="15263-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="15263-135">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="15263-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="15263-136">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="15263-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="15263-137">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="15263-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="15263-138">Men det gränssnitt som körs har inte uppdaterats `PATH` .</span><span class="sxs-lookup"><span data-stu-id="15263-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="15263-139">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="15263-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="15263-140">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="15263-140">Binary Archives</span></span>

<span data-ttu-id="15263-141">PowerShell-binärfiler `tar.gz` tillhandahålls för MacOS-plattformen för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="15263-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="15263-142">Installera binära Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="15263-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.1/powershell-7.0.1-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.1

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.1

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.1/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.1/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="15263-143">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="15263-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="15263-144">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="15263-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="15263-145">Installerar beroenden</span><span class="sxs-lookup"><span data-stu-id="15263-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="15263-146">Installera XCode kommando rads verktyg</span><span class="sxs-lookup"><span data-stu-id="15263-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="15263-147">Installera OpenSSL</span><span class="sxs-lookup"><span data-stu-id="15263-147">Install OpenSSL</span></span>

<span data-ttu-id="15263-148">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="15263-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="15263-149">Du kan installera via MacPorts.</span><span class="sxs-lookup"><span data-stu-id="15263-149">You can install via MacPorts.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="15263-150">Installera OpenSSL via MacPorts</span><span class="sxs-lookup"><span data-stu-id="15263-150">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="15263-151">Installera [kommando rads verktygen för Xcode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="15263-151">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="15263-152">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="15263-152">Install MacPorts.</span></span>
   <span data-ttu-id="15263-153">Om du behöver instruktioner kan du läsa mer i [installations guiden](https://guide.macports.org/chunked/installing.macports.html)för.</span><span class="sxs-lookup"><span data-stu-id="15263-153">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="15263-154">Uppdatera MacPorts genom att köra `sudo port selfupdate` .</span><span class="sxs-lookup"><span data-stu-id="15263-154">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="15263-155">Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated` .</span><span class="sxs-lookup"><span data-stu-id="15263-155">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="15263-156">Installera OpenSSL genom att köra `sudo port install openssl10` .</span><span class="sxs-lookup"><span data-stu-id="15263-156">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="15263-157">Länka biblioteken för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="15263-157">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="15263-158">Avinstallera PowerShell</span><span class="sxs-lookup"><span data-stu-id="15263-158">Uninstalling PowerShell</span></span>

<span data-ttu-id="15263-159">Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="15263-159">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="15263-160">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="15263-160">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="15263-161">Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="15263-161">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="15263-162">Detta är inte nödvändigt om du har installerat med homebrew.</span><span class="sxs-lookup"><span data-stu-id="15263-162">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="15263-163">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="15263-163">Paths</span></span>

* <span data-ttu-id="15263-164">`$PSHOME` är `/usr/local/microsoft/powershell/7.0.1/`</span><span class="sxs-lookup"><span data-stu-id="15263-164">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.1/`</span></span>
* <span data-ttu-id="15263-165">Användar profilerna kommer att läsas från`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="15263-165">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="15263-166">Standard profiler kommer att läsas från`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="15263-166">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="15263-167">Användarens moduler kommer att läsas från`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="15263-167">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="15263-168">Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="15263-168">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="15263-169">Standardmoduler kommer att läsas från`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="15263-169">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="15263-170">PSReadline historik registreras i`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="15263-170">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="15263-171">Profilerna respekterar PowerShell-konfigurationen per värd.</span><span class="sxs-lookup"><span data-stu-id="15263-171">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="15263-172">Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` samma platser.</span><span class="sxs-lookup"><span data-stu-id="15263-172">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="15263-173">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.</span><span class="sxs-lookup"><span data-stu-id="15263-173">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="15263-174">Eftersom macOS är en härledning av BSD används prefixet `/usr/local` i stället för `/opt` .</span><span class="sxs-lookup"><span data-stu-id="15263-174">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="15263-175">Så, `$PSHOME` är `/usr/local/microsoft/powershell/7.0.1/` och den symboliska länken placeras på `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="15263-175">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.1/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="15263-176">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="15263-176">Additional Resources</span></span>

* <span data-ttu-id="15263-177">[Homebrew-webb][brew]</span><span class="sxs-lookup"><span data-stu-id="15263-177">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="15263-178">[Homebrew GitHub-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="15263-178">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="15263-179">[Homebrew – Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="15263-179">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
