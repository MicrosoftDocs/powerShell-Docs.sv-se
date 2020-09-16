---
title: Installera PowerShell i macOS
description: Information om hur du installerar PowerShell på macOS
ms.date: 08/24/2020
ms.openlocfilehash: 8f38d573d9d67276dbc95cfb70f1fde80af62bb6
ms.sourcegitcommit: ea9270bacee7dd1b9df2519384de277576357ce2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88857893"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="10fb7-103">Installera PowerShell i macOS</span><span class="sxs-lookup"><span data-stu-id="10fb7-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="10fb7-104">PowerShell stöder macOS 10,12 och högre.</span><span class="sxs-lookup"><span data-stu-id="10fb7-104">PowerShell supports macOS 10.12 and higher.</span></span> <span data-ttu-id="10fb7-105">PowerShell 7.0.3 eller högre och PowerShell Preview 7.1.0 eller högre kräver macOS 10,13 och högre.</span><span class="sxs-lookup"><span data-stu-id="10fb7-105">PowerShell 7.0.3 or higher and PowerShell Preview 7.1.0 or higher require macOS 10.13 and higher.</span></span> <span data-ttu-id="10fb7-106">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="10fb7-106">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="10fb7-107">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="10fb7-107">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="10fb7-108">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="10fb7-108">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="10fb7-109">`/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-109">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="10fb7-110">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="10fb7-110">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="10fb7-111">Det finns flera sätt att installera PowerShell på macOS.</span><span class="sxs-lookup"><span data-stu-id="10fb7-111">There are several ways to install PowerShell on macOS.</span></span> <span data-ttu-id="10fb7-112">Använd någon av följande metoder:</span><span class="sxs-lookup"><span data-stu-id="10fb7-112">Choose one of the following methods:</span></span>

- <span data-ttu-id="10fb7-113">Installera med homebrew.</span><span class="sxs-lookup"><span data-stu-id="10fb7-113">Install using Homebrew.</span></span> <span data-ttu-id="10fb7-114">Homebrew är den föredragna paket hanteraren för macOS.</span><span class="sxs-lookup"><span data-stu-id="10fb7-114">Homebrew is the preferred package manager for macOS.</span></span>
- <span data-ttu-id="10fb7-115">Installera PowerShell via [direkt hämtning](#installation-via-direct-download)</span><span class="sxs-lookup"><span data-stu-id="10fb7-115">Install PowerShell via [Direct Download](#installation-via-direct-download)</span></span>
- <span data-ttu-id="10fb7-116">Installera från [binära Arkiv](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="10fb7-116">Install from [binary archives](#binary-archives).</span></span>

<span data-ttu-id="10fb7-117">När du har installerat PowerShell bör du installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="10fb7-117">After installing PowerShell, you should install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="10fb7-118">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-118">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="10fb7-119">Installation av den senaste stabila versionen via homebrew på macOS 10,13 eller senare</span><span class="sxs-lookup"><span data-stu-id="10fb7-119">Installation of latest stable release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="10fb7-120">Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew].</span><span class="sxs-lookup"><span data-stu-id="10fb7-120">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="10fb7-121">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="10fb7-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="10fb7-122">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="10fb7-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="10fb7-123">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="10fb7-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="10fb7-124">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a><span data-ttu-id="10fb7-125">Installation av den senaste för hands versionen via homebrew på macOS 10,13 eller senare</span><span class="sxs-lookup"><span data-stu-id="10fb7-125">Installation of latest preview release via Homebrew on macOS 10.13 or higher</span></span>

<span data-ttu-id="10fb7-126">När du har installerat homebrew kan du installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10fb7-126">After you've installed Homebrew, you can install PowerShell.</span></span> <span data-ttu-id="10fb7-127">Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:</span><span class="sxs-lookup"><span data-stu-id="10fb7-127">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="10fb7-128">Nu kan du installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="10fb7-128">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="10fb7-129">Till sist kontrollerar du att installationen fungerar korrekt:</span><span class="sxs-lookup"><span data-stu-id="10fb7-129">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="10fb7-130">Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:</span><span class="sxs-lookup"><span data-stu-id="10fb7-130">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="10fb7-131">Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="10fb7-131">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="10fb7-132">och uppdatera värdena som visas i `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-132">and refresh the values shown in `$PSVersionTable`.</span></span>

<span data-ttu-id="10fb7-133">Det finns också stöd för att installera PowerShell med metoden homebrew knackning för stabila och LTS-versioner.</span><span class="sxs-lookup"><span data-stu-id="10fb7-133">Installing PowerShell using the Homebrew tap method is also supported for stable and LTS versions.</span></span>

```sh
brew install powershell/tap/powershell
```

<span data-ttu-id="10fb7-134">Nu kan du kontrol lera installationen</span><span class="sxs-lookup"><span data-stu-id="10fb7-134">You can now verify your install</span></span>

```sh
pwsh
```

<span data-ttu-id="10fb7-135">När nya versioner av PowerShell släpps kör du bara följande kommando.</span><span class="sxs-lookup"><span data-stu-id="10fb7-135">When new versions of PowerShell are released, simply run the following command.</span></span>

```sh
brew upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="10fb7-136">Oavsett om du använder Cask eller metoden tryck, när du uppdaterar till en senare version av PowerShell, använder du samma metod som du använde för att först installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10fb7-136">Whether you use the cask or the tap method, when updating to a newer version of PowerShell, use the same method you used to initially install PowerShell.</span></span> <span data-ttu-id="10fb7-137">Om du använder en annan metod fortsätter att öppna en ny pwsh-session med den äldre versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="10fb7-137">If you use a different method, opening a new pwsh session will continue to use the older version of PowerShell.</span></span>
>
> <span data-ttu-id="10fb7-138">Om du väljer att använda olika metoder finns det olika sätt att åtgärda problemet med hjälp av [länk metoden homebrew](https://docs.brew.sh/Manpage#link-ln-options-formula).</span><span class="sxs-lookup"><span data-stu-id="10fb7-138">If you do decide to use different methods, there are ways to correct the issue using the [Homebrew link method](https://docs.brew.sh/Manpage#link-ln-options-formula).</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="10fb7-139">Installation via direkt hämtning</span><span class="sxs-lookup"><span data-stu-id="10fb7-139">Installation via Direct Download</span></span>

<span data-ttu-id="10fb7-140">Hämta PKG-paketet `powershell-lts-7.0.3-osx-x64.pkg` från sidan [versioner][] på din MacOS-dator.</span><span class="sxs-lookup"><span data-stu-id="10fb7-140">Download the PKG package `powershell-lts-7.0.3-osx-x64.pkg` from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="10fb7-141">Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:</span><span class="sxs-lookup"><span data-stu-id="10fb7-141">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.3-osx-x64.pkg -target /
```

<span data-ttu-id="10fb7-142">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="10fb7-142">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="10fb7-143">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-143">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="10fb7-144">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="10fb7-144">Install as a .NET Global tool</span></span>

<span data-ttu-id="10fb7-145">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="10fb7-145">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="10fb7-146">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="10fb7-146">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="10fb7-147">Men det gränssnitt som körs har inte uppdaterats `PATH` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-147">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="10fb7-148">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-148">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

<span data-ttu-id="10fb7-149">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="10fb7-149">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="10fb7-150">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-150">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="10fb7-151">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="10fb7-151">Binary Archives</span></span>

<span data-ttu-id="10fb7-152">PowerShell-binärfiler `tar.gz` tillhandahålls för MacOS-plattformen för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="10fb7-152">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span> <span data-ttu-id="10fb7-153">När du installerar med den här metoden måste du också installera eventuella beroenden manuellt.</span><span class="sxs-lookup"><span data-stu-id="10fb7-153">When you install using this method you must also manually install any dependencies.</span></span>

<span data-ttu-id="10fb7-154">Installera [openssl](#installing-dependencies).</span><span class="sxs-lookup"><span data-stu-id="10fb7-154">Install [OpenSSL](#installing-dependencies).</span></span> <span data-ttu-id="10fb7-155">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-155">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="10fb7-156">Installera binära Arkiv på macOS</span><span class="sxs-lookup"><span data-stu-id="10fb7-156">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.3/powershell-7.0.3-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.3

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.3

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.3/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.3/pwsh /usr/local/bin/pwsh
```

## <a name="installing-dependencies"></a><span data-ttu-id="10fb7-157">Installerar beroenden</span><span class="sxs-lookup"><span data-stu-id="10fb7-157">Installing dependencies</span></span>

<span data-ttu-id="10fb7-158">OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-158">OpenSSL is required for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="10fb7-159">Du kan installera OpenSSL via MacPorts om det behövs.</span><span class="sxs-lookup"><span data-stu-id="10fb7-159">You can install OpenSSL via MacPorts if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="10fb7-160">MacPorts och homebrew kan ha problem när de används tillsammans på samma system.</span><span class="sxs-lookup"><span data-stu-id="10fb7-160">MacPorts and Homebrew can have problems when used to together on the same system.</span></span> <span data-ttu-id="10fb7-161">Homebrew har dock inget paket för OpenSSL 1,0.</span><span class="sxs-lookup"><span data-stu-id="10fb7-161">However, Homebrew does not have a package for OpenSSL 1.0.</span></span> <span data-ttu-id="10fb7-162">Mer information finns i [vanliga frågor och svar om MacPorts](https://trac.macports.org/wiki/FAQ).</span><span class="sxs-lookup"><span data-stu-id="10fb7-162">For more information, see the [MacPorts FAQ](https://trac.macports.org/wiki/FAQ).</span></span>

1. <span data-ttu-id="10fb7-163">Installera kommando rads verktygen för Xcode.</span><span class="sxs-lookup"><span data-stu-id="10fb7-163">Install the Xcode command-line tools.</span></span> <span data-ttu-id="10fb7-164">Xcode-verktygen krävs av MacPorts.</span><span class="sxs-lookup"><span data-stu-id="10fb7-164">The Xcode tools are required by MacPorts.</span></span>

   ```sh
   xcode-select --install
   ```

1. <span data-ttu-id="10fb7-165">Installera MacPorts.</span><span class="sxs-lookup"><span data-stu-id="10fb7-165">Install MacPorts.</span></span> <span data-ttu-id="10fb7-166">Om du behöver instruktioner kan du läsa mer i [installations guiden](https://www.macports.org/install.php)för.</span><span class="sxs-lookup"><span data-stu-id="10fb7-166">If you need instructions, refer to the [installation guide](https://www.macports.org/install.php).</span></span>
1. <span data-ttu-id="10fb7-167">Uppdatera MacPorts genom att köra `sudo port selfupdate` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-167">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="10fb7-168">Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-168">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="10fb7-169">Installera OpenSSL genom att köra `sudo port install openssl10` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-169">Install OpenSSL by running `sudo port install openssl10`.</span></span>
1. <span data-ttu-id="10fb7-170">Länka biblioteken för att göra dem tillgängliga för PowerShell:</span><span class="sxs-lookup"><span data-stu-id="10fb7-170">Link the libraries to make them available to PowerShell:</span></span>

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
   ```

## <a name="uninstalling-powershell"></a><span data-ttu-id="10fb7-171">Avinstallera PowerShell</span><span class="sxs-lookup"><span data-stu-id="10fb7-171">Uninstalling PowerShell</span></span>

<span data-ttu-id="10fb7-172">Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:</span><span class="sxs-lookup"><span data-stu-id="10fb7-172">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="10fb7-173">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="10fb7-173">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="10fb7-174">Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-174">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="10fb7-175">Detta är inte nödvändigt om du har installerat med homebrew.</span><span class="sxs-lookup"><span data-stu-id="10fb7-175">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="10fb7-176">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="10fb7-176">Paths</span></span>

- <span data-ttu-id="10fb7-177">`$PSHOME` är `/usr/local/microsoft/powershell/7.0.3/`</span><span class="sxs-lookup"><span data-stu-id="10fb7-177">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.3/`</span></span>
- <span data-ttu-id="10fb7-178">Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="10fb7-178">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="10fb7-179">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="10fb7-179">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="10fb7-180">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="10fb7-180">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="10fb7-181">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="10fb7-181">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="10fb7-182">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="10fb7-182">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="10fb7-183">PSReadline historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="10fb7-183">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="10fb7-184">Profilerna respekterar PowerShell-konfigurationen per värd.</span><span class="sxs-lookup"><span data-stu-id="10fb7-184">The profiles respect PowerShell's per-host configuration.</span></span> <span data-ttu-id="10fb7-185">Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` samma platser.</span><span class="sxs-lookup"><span data-stu-id="10fb7-185">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="10fb7-186">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.</span><span class="sxs-lookup"><span data-stu-id="10fb7-186">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="10fb7-187">Eftersom macOS är en härledning av BSD används prefixet `/usr/local` i stället för `/opt` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-187">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span> <span data-ttu-id="10fb7-188">Så, `$PSHOME` är `/usr/local/microsoft/powershell/7.0.3/` och den symboliska länken placeras på `/usr/local/bin/pwsh` .</span><span class="sxs-lookup"><span data-stu-id="10fb7-188">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.3/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="installation-support"></a><span data-ttu-id="10fb7-189">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="10fb7-189">Installation support</span></span>

<span data-ttu-id="10fb7-190">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="10fb7-190">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="10fb7-191">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="10fb7-191">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="10fb7-192">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="10fb7-192">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="10fb7-193">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="10fb7-193">Additional Resources</span></span>

- <span data-ttu-id="10fb7-194">[Homebrew-webb][brew]</span><span class="sxs-lookup"><span data-stu-id="10fb7-194">[Homebrew Web][brew]</span></span>
- <span data-ttu-id="10fb7-195">[Homebrew GitHub-lagringsplats][GitHub]</span><span class="sxs-lookup"><span data-stu-id="10fb7-195">[Homebrew Github Repository][GitHub]</span></span>
- <span data-ttu-id="10fb7-196">[Homebrew – Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="10fb7-196">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
