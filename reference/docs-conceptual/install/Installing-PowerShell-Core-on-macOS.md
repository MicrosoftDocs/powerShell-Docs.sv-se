---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 12/12/2018
ms.openlocfilehash: 91e64cace7d4ed988da56109dde9bf2a80528eb4
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404954"
---
# <a name="installing-powershell-core-on-macos"></a>Installera PowerShell Core i macOS

PowerShell Core stöder macOS 10.12 och högre.
Alla paket finns på vår GitHub [versioner][] sidan.
När paketet har installerats, köra `pwsh` från en terminal.

## <a name="about-brew"></a>Om Brew

[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.
Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre

Se [om Brew](#about-brew) information om Brew.

Du kan nu installera PowerShell:

```sh
brew cask install powershell
```

Slutligen kan du kontrollera att installationen fungerar korrekt:

```sh
pwsh
```

När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable`.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre

Se [om Brew](#about-brew) information om Brew.

När du har installerat Homebrew, kan du installera PowerShell.
Installera först den [Cask versioner] [ cask-versions] paket som hjälper dig att installera alternativa versioner av cask paket:

```sh
brew tap homebrew/cask-versions
```

Du kan nu installera PowerShell:

```sh
brew cask install powershell-preview
```

Slutligen kan du kontrollera att installationen fungerar korrekt:

```sh
pwsh-preview
```

När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen.
> och uppdatera värdena som visas i `$PSVersionTable`.

## <a name="installation-via-direct-download"></a>Installationen via Direct hämtning

Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`
från den [versioner][] sida på din macOS-dator.

Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

Installera [OpenSSL](#install-openssl). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="binary-archives"></a>Binär Arkiv

PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS-plattformen att aktivera avancerade scenarier.

### <a name="installing-binary-archives-on-macos"></a>Installera binär Arkiv på macOS

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

Installera [OpenSSL](#install-openssl). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="installing-dependencies"></a>Installation av beroenden

### <a name="install-xcode-command-line-tools"></a>Installera XCode-kommandoradsverktyg

```sh
xcode-select --install
```

### <a name="install-openssl"></a>Installera OpenSSL

OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder. Du kan installera via MacPorts eller Brew.

#### <a name="install-openssl-via-brew"></a>Installera OpenSSL, via Brew

Se [om Brew](#about-brew) information om Brew.

Om du vill installera OpenSSL, kör `brew install openssl`.

#### <a name="install-openssl-via-macports"></a>Installera OpenSSL, via MacPorts

1. Installera den [XCode kommandoradsverktyg](#install-xcode-command-line-tools).
1. Installera MacPorts.
   Om du behöver mer information, referera till den [installationsguide](https://guide.macports.org/chunked/installing.macports.html).
1. Uppdatera MacPorts genom att köra `sudo port selfupdate`.
1. Uppgradera MacPorts paket genom att köra `sudo port upgrade outdated`.
1. Installera OpenSSL, genom att köra `sudo port install openssl`.
1. Länka bibliotek för att göra dem tillgängliga för PowerShell:

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a>Avinstallera PowerShell Core

Om du har installerat PowerShell med Homebrew kan du använda följande kommando för att avinstallera:

```sh
brew cask uninstall powershell
```

Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Om du vill ta bort ytterligare PowerShell-sökvägar, referera till den [sökvägar](#paths) i det här dokumentet och ta bort sökvägar med hjälp av `sudo rm`.

> [!NOTE]
> Detta är inte nödvändigt om du installerade med Homebrew.

## <a name="paths"></a>Sökvägar

* `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`
* Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`
* Standardprofiler ska läsas från `$PSHOME/profile.ps1`
* Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`
* Delade moduler ska läsas från `/usr/local/share/powershell/Modules`
* Standardmoduler ska läsas från `$PSHOME/Modules`
* PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respekterar konfiguration för PowerShell-per värd.
Så värdspecifika standardprofilen finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.

Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.
Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och den symboliska länken är placerad på `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ytterligare resurser

* [Homebrew Web][brew]
* [Homebrew Github-lagringsplats][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
