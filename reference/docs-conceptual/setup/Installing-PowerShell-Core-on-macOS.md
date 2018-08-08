---
title: Installera PowerShell Core i macOS
description: Information om att installera PowerShell Core på macOS
ms.date: 08/06/2018
ms.openlocfilehash: ff1814d95b3ca3fa8497069dff249fd2ad5576ef
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587473"
---
# <a name="installing-powershell-core-on-macos"></a>Installera PowerShell Core i macOS

PowerShell Core stöder macOS 10.12 och högre.
Alla paket finns på vår GitHub [släpper][] sidan.
När paketet har installerats kan du köra `pwsh` från en terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installation via Homebrew på macOS 10.12 +

[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.
Ange från ett terminalfönster `brew` att köra Homebrew.  Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].

> [!NOTE]
> Om du har installerat Homebrew tidigare är det alltid en bra idé att köra 'brew uppdatera återställa ”& &” brew update ”.
```sh
brew update-reset
brew update
```

> Äldre versioner av Homebrew används den trycker du på ”caskroom/cask”, som har inaktuella och migreras till 'homebrew/cask ”.  Mer information finns på [Homebrew cask][cask]. Använd kommandot ”brew trycker du på” Visa en lista över dina aktuella TAP.  Om du ser ”caskroom/cask, kan du använda 'brew update' har Homebrew migrera TAP.

```sh
brew tap
brew update
```

När du har installerat/uppdaterat Homebrew, är det enkelt att installera PowerShell.

Installera PowerShell:

```sh
brew cask install powershell
```

Slutligen kan du kontrollera att installationen fungerar korrekt:

```sh
pwsh
```

För att avsluta PowerShell och återgå till bash, använder du avslutningskommandot.
```sh
exit
```

När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.

### <a name="installing-preview-via-homebrew-on-macos-1012"></a>Installera förhandsversionen via Homebrew på macOS 10.12 +

[Homebrew] [ brew] är den prioriterade Pakethanteraren för macOS.
Ange från ett terminalfönster `brew` att köra Homebrew.  Om den `brew` kommandot inte finns, måste du installera Homebrew följande [instruktionerna][brew].

> [!NOTE]
> Om du har installerat Homebrew tidigare är det alltid en bra idé att köra 'brew uppdatera återställa ”& &” brew update ”.
```sh
brew update-reset
brew update
```

Sedan måste du trycker på den `versions` slags lagringsplatsen för att hämta preview-paketet:

```sh
brew tap homebrew/cask-versions
```

Så här installerar förhandsversionen av PowerShell:

```sh
brew cask install powershell-preview
```

Slutligen kan du kontrollera att installationen fungerar korrekt:

```sh
pwsh-preview
```

När nya versioner av PowerShell släpps, uppdatera Homebrews formler och uppgradera förhandsversionen av PowerShell:

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.

### <a name="installation-via-direct-download"></a>Installationen via Direct hämtning

Hämtningspaketet PKG `powershell-6.0.2-osx.10.12-x64.pkg` från den [släpper][] sida på din macOS-dator.

Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Binär Arkiv

PowerShell-binär `tar.gz` Arkiv tillhandahålls för macOS och Linux-plattformar för att aktivera avancerade scenarier.

### <a name="installing-binary-archives-on-macos"></a>Installera binär Arkiv på macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
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

Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på den [sökvägar][] avsnittet i det här dokumentet och ta bort en önskad sökvägar med hjälp av `sudo rm`.

> [!NOTE]
> Detta är inte nödvändigt om du installerade med Homebrew.

[Sökvägar]:#paths

## <a name="paths"></a>Sökvägar

* `$PSHOME` är `/usr/local/microsoft/powershell/6.0.2/`
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
Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.2/`, och symlink placeras på `/usr/local/bin/pwsh`.

## <a name="additional-resources"></a>Ytterligare resurser

* [Homebrew Web][brew]
* [Homebrew Github-lagringsplats][GitHub]
* [Homebrew-Cask][cask]


[brew]: http://brew.sh/
[GitHub]: https://github.com/Homebrew
[Cask]: https://github.com/Homebrew/homebrew-cask
[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
