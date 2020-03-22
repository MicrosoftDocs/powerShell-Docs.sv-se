---
title: Installera PowerShell på macOS
description: Information om hur du installerar PowerShell på macOS
ms.date: 12/12/2018
ms.openlocfilehash: 2233bc01ee8c53087f79d83ca936c5a3800cfdba
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082761"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="0bbd9-103">Installera PowerShell på macOS</span><span class="sxs-lookup"><span data-stu-id="0bbd9-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="0bbd9-104">PowerShell stöder macOS 10,12 och högre.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="0bbd9-105">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="0bbd9-106">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="0bbd9-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="0bbd9-108">Mappen `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="0bbd9-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="0bbd9-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="0bbd9-110">Om Brew</span><span class="sxs-lookup"><span data-stu-id="0bbd9-110">About Brew</span></span>

<span data-ttu-id="0bbd9-111">[Homebrew][brew] är den föredragna paket hanteraren för MacOS.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="0bbd9-112">Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew].</span><span class="sxs-lookup"><span data-stu-id="0bbd9-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="0bbd9-113">Annars kan du installera PowerShell via [direkt hämtning](#installation-via-direct-download) eller från [binära Arkiv](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="0bbd9-114">Installation av den senaste stabila versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="0bbd9-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="0bbd9-115">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="0bbd9-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0bbd9-116">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="0bbd9-117">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="0bbd9-118">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="0bbd9-119">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="0bbd9-120">Installation av den senaste för hands versionen via homebrew på macOS 10,12 eller senare</span><span class="sxs-lookup"><span data-stu-id="0bbd9-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="0bbd9-121">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="0bbd9-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0bbd9-122">När du har installerat homebrew kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="0bbd9-123">Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="0bbd9-124">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="0bbd9-125">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="0bbd9-126">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="0bbd9-127">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="0bbd9-128">och uppdatera värdena som visas i `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="0bbd9-129">Installation via direkt hämtning</span><span class="sxs-lookup"><span data-stu-id="0bbd9-129">Installation via Direct Download</span></span>

<span data-ttu-id="0bbd9-130">Ladda ned PKG-paketet `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-130">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="0bbd9-131">från sidan [releases][] till din MacOS-dator.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="0bbd9-132">Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="0bbd9-133">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="0bbd9-134">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="0bbd9-135">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="0bbd9-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="0bbd9-136">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="0bbd9-137">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="0bbd9-138">Men det gränssnitt som körs har inte den uppdaterade `PATH`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="0bbd9-139">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="0bbd9-140">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="0bbd9-140">Binary Archives</span></span>

<span data-ttu-id="0bbd9-141">PowerShell Binary `tar.gz`-Arkiv tillhandahålls för macOS-plattformen för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="0bbd9-142">Installera binära Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="0bbd9-142">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="0bbd9-143">Installera [openssl](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="0bbd9-144">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="0bbd9-145">Installerar beroenden</span><span class="sxs-lookup"><span data-stu-id="0bbd9-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="0bbd9-146">Installera XCode kommando rads verktyg</span><span class="sxs-lookup"><span data-stu-id="0bbd9-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="0bbd9-147">Installera OpenSSL</span><span class="sxs-lookup"><span data-stu-id="0bbd9-147">Install OpenSSL</span></span>

<span data-ttu-id="0bbd9-148">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="0bbd9-149">Du kan installera via MacPorts eller Brew.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="0bbd9-150">Installera OpenSSL via Brew</span><span class="sxs-lookup"><span data-stu-id="0bbd9-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="0bbd9-151">Mer information om Brew finns i [About Brew](#about-brew) .</span><span class="sxs-lookup"><span data-stu-id="0bbd9-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="0bbd9-152">Kör `brew install openssl`för att installera OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="0bbd9-153">Installera OpenSSL via MacPorts</span><span class="sxs-lookup"><span data-stu-id="0bbd9-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="0bbd9-154">Installera [kommando rads verktygen för Xcode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="0bbd9-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="0bbd9-155">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-155">Install MacPorts.</span></span>
   <span data-ttu-id="0bbd9-156">Om du behöver instruktioner kan du läsa mer i [installations guiden](https://guide.macports.org/chunked/installing.macports.html)för.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="0bbd9-157">Uppdatera MacPorts genom att köra `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="0bbd9-158">Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="0bbd9-159">Installera OpenSSL genom att köra `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="0bbd9-160">Länka biblioteken för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="0bbd9-161">Avinstallera PowerShell</span><span class="sxs-lookup"><span data-stu-id="0bbd9-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="0bbd9-162">Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="0bbd9-163">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="0bbd9-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="0bbd9-164">Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="0bbd9-165">Detta är inte nödvändigt om du har installerat med homebrew.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="0bbd9-166">Mappar</span><span class="sxs-lookup"><span data-stu-id="0bbd9-166">Paths</span></span>

* <span data-ttu-id="0bbd9-167">`$PSHOME` är `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-167">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="0bbd9-168">Användar profiler kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="0bbd9-169">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="0bbd9-170">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0bbd9-171">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="0bbd9-172">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="0bbd9-173">PSReadline-historik registreras för `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="0bbd9-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="0bbd9-174">Profilerna respekterar PowerShell-konfigurationen per värd.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="0bbd9-175">Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="0bbd9-176">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="0bbd9-177">Eftersom macOS är en härledning av BSD, används prefixet `/usr/local` i stället för `/opt`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="0bbd9-178">Därför är `$PSHOME` `/usr/local/microsoft/powershell/6.2.0/`och den symboliska länken placeras på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="0bbd9-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0bbd9-179">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="0bbd9-179">Additional Resources</span></span>

* <span data-ttu-id="0bbd9-180">[Homebrew-webb][brew]</span><span class="sxs-lookup"><span data-stu-id="0bbd9-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="0bbd9-181">[Homebrew GitHub-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="0bbd9-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="0bbd9-182">[Homebrew – Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="0bbd9-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
