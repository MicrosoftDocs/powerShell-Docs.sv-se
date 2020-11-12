---
title: Installera PowerShell i macOS
description: Information om hur du installerar PowerShell på macOS
ms.date: 11/11/2020
ms.openlocfilehash: c64edd202de90cb4e7a335376c60a0bba0633baa
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524402"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="86050-103">Installera PowerShell i macOS</span><span class="sxs-lookup"><span data-stu-id="86050-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="86050-104">PowerShell 7,0 eller högre kräver macOS 10,13 och högre.</span><span class="sxs-lookup"><span data-stu-id="86050-104">PowerShell 7.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="86050-105">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="86050-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="86050-106">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="86050-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="86050-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="86050-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="86050-108">`/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="86050-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="86050-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="86050-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="86050-110">Det finns flera sätt att installera PowerShell på macOS.</span><span class="sxs-lookup"><span data-stu-id="86050-110">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="86050-111">Använd någon av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="86050-111">Choose one of the following methods:</span></span>

- <span data-ttu-id="86050-112">Installera med homebrew.</span><span class="sxs-lookup"><span data-stu-id="86050-112">Install using Homebrew.</span></span> <span data-ttu-id="86050-113">Homebrew är den föredragna paket hanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="86050-113">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="86050-114">Installera PowerShell via [direkt hämtning](#installation-via-direct-download)</span><span class="sxs-lookup"><span data-stu-id="86050-114">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="86050-115">Installera från [binära Arkiv](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="86050-115">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="86050-116">När du har installerat PowerShell bör du installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="86050-116">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="86050-117">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="86050-117">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="86050-118">Installation av den senaste stabila versionen via homebrew på macOS 10,13 eller senare</span><span class="sxs-lookup"><span data-stu-id="86050-118">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="86050-119">Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew].</span><span class="sxs-lookup"><span data-stu-id="86050-119">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="86050-120">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="86050-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="86050-121">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="86050-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="86050-122">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="86050-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell --cask
```

> [!NOTE]
> <span data-ttu-id="86050-123">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="86050-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="86050-124">Installation av den senaste för hands versionen via homebrew på macOS 10,13 eller senare</span><span class="sxs-lookup"><span data-stu-id="86050-124">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="86050-125">När du har installerat homebrew kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86050-125">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="86050-126">Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:</span><span class="sxs-lookup"><span data-stu-id="86050-126">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="86050-127">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="86050-127">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="86050-128">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="86050-128">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="86050-129">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="86050-129">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew upgrade powershell-preview --cask
```

> [!NOTE]
> <span data-ttu-id="86050-130">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="86050-130">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="86050-131">och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="86050-131">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="86050-132">Det finns också stöd för att installera PowerShell med metoden homebrew knackning för stabila och LTS-versioner.</span><span class="sxs-lookup"><span data-stu-id="86050-132">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="86050-133">Nu kan du kontrol lera installationen</span><span class="sxs-lookup"><span data-stu-id="86050-133">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="86050-134">När nya versioner av PowerShell släpps kör du bara följande kommando.</span><span class="sxs-lookup"><span data-stu-id="86050-134">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="86050-135">Oavsett om du använder Cask eller metoden tryck, när du uppdaterar till en senare version av PowerShell, använder du samma metod som du använde för att först installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86050-135">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="86050-136">Om du använder en annan metod fortsätter att öppna en ny pwsh-session med den äldre versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="86050-136">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="86050-137">Om du väljer att använda olika metoder finns det olika sätt att åtgärda problemet med hjälp av [länk metoden homebrew](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="86050-137">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="86050-138">Installation via direkt hämtning</span><span class="sxs-lookup"><span data-stu-id="86050-138">Installation via Direct Download</span></span>

<span data-ttu-id="86050-139">Hämta PKG-paketet `powershell-lts-7.1.0-osx-x64.pkg` från sidan [versioner][] på din MacOS-dator.</span><span class="sxs-lookup"><span data-stu-id="86050-139">Download the PKG package `powershell-lts-7.1.0-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="86050-140">Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:</span><span class="sxs-lookup"><span data-stu-id="86050-140">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="86050-141">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="86050-141">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="86050-142">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="86050-142">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="86050-143">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="86050-143">Install as a .NET Global tool</span></span>

<span data-ttu-id="86050-144">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="86050-144">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="86050-145">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="86050-145">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="86050-146">Men det gränssnitt som körs har inte uppdaterats `PATH` .</span><span class="sxs-lookup"><span data-stu-id="86050-146">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="86050-147">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="86050-147">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="86050-148">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="86050-148">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="86050-149">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="86050-149">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="86050-150">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="86050-150">Binary Archives</span></span>

<span data-ttu-id="86050-151">PowerShell-binärfiler `tar.gz` tillhandahålls för MacOS-plattformen för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="86050-151">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="86050-152">När du installerar med den här metoden måste du också installera eventuella beroenden manuellt.</span><span class="sxs-lookup"><span data-stu-id="86050-152">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="86050-153">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="86050-153">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="86050-154">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="86050-154">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="86050-155">Installera binära Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="86050-155">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="86050-156">Installerar beroenden</span><span class="sxs-lookup"><span data-stu-id="86050-156">Installing dependencies</span></span>

<span data-ttu-id="86050-157">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="86050-157">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="86050-158">Du kan installera OpenSSL via MacPorts om det behövs.</span><span class="sxs-lookup"><span data-stu-id="86050-158">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="86050-159">MacPorts och homebrew kan ha problem när de används tillsammans på samma system.</span><span class="sxs-lookup"><span data-stu-id="86050-159">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="86050-160">Homebrew har dock inget paket för OpenSSL 1,0.</span><span class="sxs-lookup"><span data-stu-id="86050-160">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="86050-161">Mer information finns i [vanliga frågor och svar om MacPorts](https://trac.macports.org/wiki/FAQ).</span><span class="sxs-lookup"><span data-stu-id="86050-161">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="86050-162">Installera kommando rads verktygen för Xcode.</span><span class="sxs-lookup"><span data-stu-id="86050-162">Install the Xcode command-line tools.</span></span> <span data-ttu-id="86050-163">Xcode-verktygen krävs av MacPorts.</span><span class="sxs-lookup"><span data-stu-id="86050-163">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="86050-164">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="86050-164">Install MacPorts.</span></span> <span data-ttu-id="86050-165">Om du behöver instruktioner kan du läsa mer i [installations guiden](https://www.macports.org/install.php)för.</span><span class="sxs-lookup"><span data-stu-id="86050-165">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="86050-166">Uppdatera MacPorts genom att köra `sudo port selfupdate` .</span><span class="sxs-lookup"><span data-stu-id="86050-166">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="86050-167">Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated` .</span><span class="sxs-lookup"><span data-stu-id="86050-167">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="86050-168">Installera OpenSSL genom att köra `sudo port install openssl10` .</span><span class="sxs-lookup"><span data-stu-id="86050-168">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="86050-169">Länka biblioteken för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="86050-169">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="86050-170">Avinstallera PowerShell</span><span class="sxs-lookup"><span data-stu-id="86050-170">Uninstalling PowerShell</span></span>

<span data-ttu-id="86050-171">Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="86050-171">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="86050-172">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="86050-172">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="86050-173">Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="86050-173">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="86050-174">Detta är inte nödvändigt om du har installerat med homebrew.</span><span class="sxs-lookup"><span data-stu-id="86050-174">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="86050-175">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="86050-175">Paths</span></span>

- <span data-ttu-id="86050-176">`$PSHOME` är `/usr/local/microsoft/powershell/7.1.0/`</span><span class="sxs-lookup"><span data-stu-id="86050-176">`$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`</span></span>
- <span data-ttu-id="86050-177">Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="86050-177">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="86050-178">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="86050-178">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="86050-179">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="86050-179">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="86050-180">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="86050-180">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="86050-181">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="86050-181">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="86050-182">PSReadline historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="86050-182">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="86050-183">Profilerna respekterar PowerShell-konfigurationen per värd.</span><span class="sxs-lookup"><span data-stu-id="86050-183">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="86050-184">Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` samma platser.</span><span class="sxs-lookup"><span data-stu-id="86050-184">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="86050-185">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.</span><span class="sxs-lookup"><span data-stu-id="86050-185">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="86050-186">Eftersom macOS är en härledning av BSD används prefixet `/usr/local` i stället för `/opt` .</span><span class="sxs-lookup"><span data-stu-id="86050-186">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="86050-187">Så, `$PSHOME` är `/usr/local/microsoft/powershell/7.1.0/` och den symboliska länken placeras på `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="86050-187">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="86050-188">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="86050-188">Installation support</span></span>

<span data-ttu-id="86050-189">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="86050-189">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="86050-190">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="86050-190">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="86050-191">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="86050-191">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="86050-192">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="86050-192">Additional Resources</span></span>

- <span data-ttu-id="86050-193">[Homebrew-webb][brew]</span><span class="sxs-lookup"><span data-stu-id="86050-193">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="86050-194">[Homebrew GitHub-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="86050-194">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="86050-195">[Homebrew – Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="86050-195">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
