# <a name="installing-powershell-core-on-macos"></a>Installera PowerShell Core i macOS

PowerShell Core stöder macOS 10.12 och högre.
Alla paket är tillgängliga på vår GitHub [Versioner][] sidan.
När paketet har installerats kör `pwsh` från en terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Installation via Homebrew på macOS 10.12

[Homebrew] [ brew] är prioriterade package manager för macOS.
Om den `brew` kommando inte hittas, måste du installera följande Homebrew [instruktionerna][brew].

När du har installerat Homebrew, är det enkelt att installera PowerShell.
Installera först [Homebrew Cask][cask], så kan du installera flera paket:

```sh
brew tap caskroom/cask
```

Du kan nu installera PowerShell:

```sh
brew cask install powershell
```

Kontrollera slutligen att din installera fungerar:

```sh
pwsh
```

När nya versioner av PowerShell släpps uppdatera Homebrews formler och uppgradera PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Installationen via direkt hämtning

Hämta PKG `powershell-6.0.2-osx.10.12-x64.pkg` från den [Versioner][] sidan på din dator macOS.

Du kan dubbelklicka på filen och följ anvisningarna eller installera det från terminalen:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Binär Arkiv

PowerShell binär `tar.gz` Arkiv som har angetts för macOS- och Linux-plattformar för att aktivera avancerade distribueringsscenarier.

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

Om du har installerat PowerShell med Homebrew är avinstallationen enkel:

```sh
brew cask uninstall powershell
```

Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Om du vill ta bort de ytterligare PowerShell-sökvägarna finns på [sökvägar][] avsnittet i det här dokumentet och ta bort den önskade sökvägar med `sudo rm`.

> [!NOTE]
> Detta är inte nödvändigt om du har installerat med Homebrew.

[Sökvägar]:#paths

## <a name="paths"></a>Sökvägar

* `$PSHOME` Är `/usr/local/microsoft/powershell/6.0.2/`
* Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`
* Standardprofiler kommer att läsas från `$PSHOME/profile.ps1`
* Moduler som användare kommer att läsas från `~/.local/share/powershell/Modules`
* Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`
* Standardmoduler ska läsas från `$PSHOME/Modules`
* PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna ta hänsyn till konfiguration av PowerShells per värd.
Så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar den [XDG Base Directory specifikationen] [ xdg-bds] på macOS.

Eftersom macOS är en härledning av BSD prefixet `/usr/local` används i stället för `/opt`.
Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.2/`, och symlink är placerad på `/usr/local/bin/pwsh`.

[Versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
