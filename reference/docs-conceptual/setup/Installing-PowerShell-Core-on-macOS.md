---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: e226cd64f8788ae74dc72fdc0cd219923b7a2cd6
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002367"
---
# <a name="installing-powershell-core-on-macos"></a>Installera PowerShell Core i macOS

PowerShell Core stöder macOS 10.12 och högre.
Alla paket finns på vår GitHub [släpper][] sidan.
När paketet har installerats kan du köra `pwsh` från en terminal.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av senaste stabila versionen via Homebrew i macOS 10.12 eller högre

[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.
Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].

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
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a>Installation av senaste förhandsversionen versionen via Homebrew i macOS 10.12 eller högre

[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.
Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].

När du har installerat Homebrew är det enkelt att installera PowerShell.
Installera först [Cask versioner] [ cask-versions] som hjälper dig att installera alternativa versioner av cask paket:

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
> och uppdatera värdena som visas i $PSVersionTable.

## <a name="installation-via-direct-download"></a>Installationen via Direct hämtning

Ladda ned PKG-paketet `powershell-6.1.0-osx-x64.pkg`
från den [släpper][] sida på din macOS-dator.

Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

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

## <a name="uninstalling-powershell-core"></a>Avinstallera PowerShell Core

Om du har installerat PowerShell med Homebrew är avinstallationen enkelt:

```sh
brew cask uninstall powershell
```

Om du har installerat PowerShell via direct hämtning måste PowerShell tas bort manuellt:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar](#paths) avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.

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
Så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] på macOS.

Eftersom macOS är en härledning av BSD, prefixet `/usr/local` används i stället för `/opt`.
Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.1.0/`, och symlink placeras på `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ytterligare resurser

* [Homebrew Web][brew]
* [Homebrew Github-lagringsplats][GitHub]
* [Homebrew-Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
