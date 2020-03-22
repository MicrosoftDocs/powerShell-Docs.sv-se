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
# <a name="installing-powershell-on-macos"></a>Installera PowerShell på macOS

PowerShell stöder macOS 10,12 och högre.
Alla paket är tillgängliga på vår GitHub- [releases][] -sida.
När paketet har installerats kör du `pwsh` från en Terminal.

> [!NOTE]
> PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.
>
> Mappen `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`.
>
> Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .

## <a name="about-brew"></a>Om Brew

[Homebrew][brew] är den föredragna paket hanteraren för MacOS. Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew]. Annars kan du installera PowerShell via [direkt hämtning](#installation-via-direct-download) eller från [binära Arkiv](#binary-archives).

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av den senaste stabila versionen via homebrew på macOS 10,12 eller senare

Mer information om Brew finns i [About Brew](#about-brew) .

Nu kan du installera PowerShell:

```sh
brew cask install powershell
```

Till sist kontrollerar du att installationen fungerar korrekt:

```sh
pwsh
```

Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable`.

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av den senaste för hands versionen via homebrew på macOS 10,12 eller senare

Mer information om Brew finns i [About Brew](#about-brew) .

När du har installerat homebrew kan du installera PowerShell.
Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:

```sh
brew tap homebrew/cask-versions
```

Nu kan du installera PowerShell:

```sh
brew cask install powershell-preview
```

Till sist kontrollerar du att installationen fungerar korrekt:

```sh
pwsh-preview
```

Uppdatera homebrew formel och uppgradera PowerShell när nya versioner av PowerShell släpps:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att uppgraderingen ska slutföras.
> och uppdatera värdena som visas i `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installation via direkt hämtning

Ladda ned PKG-paketet `powershell-6.2.0-osx-x64.pkg`
från sidan [releases][] till din MacOS-dator.

Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

Installera [openssl](#install-openssl). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="install-as-a-net-global-tool"></a>Installera som ett globalt .NET-verktyg

Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel. Men det gränssnitt som körs har inte den uppdaterade `PATH`. Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.

## <a name="binary-archives"></a>Binära Arkiv

PowerShell Binary `tar.gz`-Arkiv tillhandahålls för macOS-plattformen för att aktivera avancerade distributions scenarier.

### <a name="installing-binary-archives-on-macos"></a>Installera binära Arkiv på macOS

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

Installera [openssl](#install-openssl). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="installing-dependencies"></a>Installerar beroenden

### <a name="install-xcode-command-line-tools"></a>Installera XCode kommando rads verktyg

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installera OpenSSL

OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder. Du kan installera via MacPorts eller Brew.

#### <a name="install-openssl-via-brew"></a>Installera OpenSSL via Brew

Mer information om Brew finns i [About Brew](#about-brew) .

Kör `brew install openssl`för att installera OpenSSL.

#### <a name="install-openssl-via-macports"></a>Installera OpenSSL via MacPorts

1. Installera [kommando rads verktygen för Xcode](#install-xcode-command-line-tools).
1. Installera MacPorts.
   Om du behöver instruktioner kan du läsa mer i [installations guiden](https://guide.macports.org/chunked/installing.macports.html)för.
1. Uppdatera MacPorts genom att köra `sudo port selfupdate`.
1. Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated`.
1. Installera OpenSSL genom att köra `sudo port install openssl`.
1. Länka biblioteken för att göra dem tillgängliga för PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a>Avinstallera PowerShell

Om du har installerat PowerShell med homebrew, använder du följande kommando för att avinstallera:

```sh
brew cask uninstall powershell
```

Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm`.

> [!NOTE]
> Detta är inte nödvändigt om du har installerat med homebrew.

## <a name="paths"></a>Mappar

* `$PSHOME` är `/usr/local/microsoft/powershell/6.2.0/`
* Användar profiler kommer att läsas från `~/.config/powershell/profile.ps1`
* Standard profiler kommer att läsas från `$PSHOME/profile.ps1`
* Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`
* Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`
* Standardmoduler kommer att läsas från `$PSHOME/Modules`
* PSReadline-historik registreras för `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respekterar PowerShell-konfigurationen per värd.
Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.

Eftersom macOS är en härledning av BSD, används prefixet `/usr/local` i stället för `/opt`.
Därför är `$PSHOME` `/usr/local/microsoft/powershell/6.2.0/`och den symboliska länken placeras på `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ytterligare resurser

* [Homebrew-webb][brew]
* [Homebrew GitHub-lagringsplats][GitHub]
* [Homebrew – Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
