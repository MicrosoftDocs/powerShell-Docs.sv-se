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
# <a name="installing-powershell-on-macos"></a>Installera PowerShell i macOS

PowerShell stöder macOS 10,12 och högre. PowerShell 7.0.3 eller högre och PowerShell Preview 7.1.0 eller högre kräver macOS 10,13 och högre. Alla paket är tillgängliga på vår GitHub- [releases][] -sida. När paketet har installerats kör du `pwsh` från en Terminal.

> [!NOTE]
> PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.
>
> `/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .
>
> Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .

Det finns flera sätt att installera PowerShell på macOS. Använd någon av följande metoder:

- Installera med homebrew. Homebrew är den föredragna paket hanteraren för macOS.
- Installera PowerShell via [direkt hämtning](#installation-via-direct-download)
- Installera från [binära Arkiv](#binary-archives).

När du har installerat PowerShell bör du installera [openssl](#installing-dependencies). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1013-or-higher"></a>Installation av den senaste stabila versionen via homebrew på macOS 10,13 eller senare

Om `brew` kommandot inte hittas måste du installera homebrew enligt [deras instruktioner][brew].

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
> Kommandona ovan kan anropas inifrån en PowerShell-värd (pwsh), men PowerShell-gränssnittet måste avslutas och startas om för att slutföra uppgraderingen och uppdatera värdena som visas i `$PSVersionTable` .

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1013-or-higher"></a>Installation av den senaste för hands versionen via homebrew på macOS 10,13 eller senare

När du har installerat homebrew kan du installera PowerShell. Installera först [Cask-versioner-][cask-versions] paketet som låter dig installera alternativa versioner av Cask-paket:

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
> och uppdatera värdena som visas i `$PSVersionTable` .

Det finns också stöd för att installera PowerShell med metoden homebrew knackning för stabila och LTS-versioner.

```sh
brew install powershell/tap/powershell
```

Nu kan du kontrol lera installationen

```sh
pwsh
```

När nya versioner av PowerShell släpps kör du bara följande kommando.

```sh
brew upgrade powershell
```

> [!NOTE]
> Oavsett om du använder Cask eller metoden tryck, när du uppdaterar till en senare version av PowerShell, använder du samma metod som du använde för att först installera PowerShell. Om du använder en annan metod fortsätter att öppna en ny pwsh-session med den äldre versionen av PowerShell.
>
> Om du väljer att använda olika metoder finns det olika sätt att åtgärda problemet med hjälp av [länk metoden homebrew](https://docs.brew.sh/Manpage#link-ln-options-formula).

## <a name="installation-via-direct-download"></a>Installation via direkt hämtning

Hämta PKG-paketet `powershell-lts-7.0.3-osx-x64.pkg` från sidan [versioner][] på din MacOS-dator.

Du kan dubbelklicka på filen och följa anvisningarna eller installera den från terminalen:

```sh
sudo installer -pkg powershell-lts-7.0.3-osx-x64.pkg -target /
```

Installera [openssl](#installing-dependencies). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="install-as-a-net-global-tool"></a>Installera som ett globalt .NET-verktyg

Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel. Men det gränssnitt som körs har inte uppdaterats `PATH` . Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .

Installera [openssl](#installing-dependencies). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

## <a name="binary-archives"></a>Binära Arkiv

PowerShell-binärfiler `tar.gz` tillhandahålls för MacOS-plattformen för att aktivera avancerade distributions scenarier. När du installerar med den här metoden måste du också installera eventuella beroenden manuellt.

Installera [openssl](#installing-dependencies). OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder.

### <a name="installing-binary-archives-on-macos"></a>Installera binära Arkiv på macOS

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

## <a name="installing-dependencies"></a>Installerar beroenden

OpenSSL krävs för PowerShell-fjärrkommunikation och CIM-åtgärder. Du kan installera OpenSSL via MacPorts om det behövs.

> [!NOTE]
> MacPorts och homebrew kan ha problem när de används tillsammans på samma system. Homebrew har dock inget paket för OpenSSL 1,0. Mer information finns i [vanliga frågor och svar om MacPorts](https://trac.macports.org/wiki/FAQ).

1. Installera kommando rads verktygen för Xcode. Xcode-verktygen krävs av MacPorts.

   ```sh
   xcode-select --install
   ```

1. Installera MacPorts. Om du behöver instruktioner kan du läsa mer i [installations guiden](https://www.macports.org/install.php)för.
1. Uppdatera MacPorts genom att köra `sudo port selfupdate` .
1. Uppgradera MacPorts-paket genom att köra `sudo port upgrade outdated` .
1. Installera OpenSSL genom att köra `sudo port install openssl10` .
1. Länka biblioteken för att göra dem tillgängliga för PowerShell:

   ```sh
   sudo mkdir -p /usr/local/opt/openssl
   sudo ln -s /opt/local/lib/openssl-1.0 /usr/local/opt/openssl/lib
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

Om du vill ta bort ytterligare PowerShell-sökvägar läser du avsnittet [sökvägar](#paths) i det här dokumentet och tar bort Sök vägarna med `sudo rm` .

> [!NOTE]
> Detta är inte nödvändigt om du har installerat med homebrew.

## <a name="paths"></a>Sökvägar

- `$PSHOME` är `/usr/local/microsoft/powershell/7.0.3/`
- Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`
- Standard profiler kommer att läsas från `$PSHOME/profile.ps1`
- Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`
- Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`
- Standardmoduler kommer att läsas från `$PSHOME/Modules`
- PSReadline historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respekterar PowerShell-konfigurationen per värd. Så att den standardinställda värdbaserade profilen finns på `Microsoft.PowerShell_profile.ps1` samma platser.

PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] på MacOS.

Eftersom macOS är en härledning av BSD används prefixet `/usr/local` i stället för `/opt` . Så, `$PSHOME` är `/usr/local/microsoft/powershell/7.0.3/` och den symboliska länken placeras på `/usr/local/bin/pwsh` .

## <a name="installation-support"></a>Installations stöd

Microsoft stöder installations metoderna i det här dokumentet. Det kan finnas andra installations metoder som är tillgängliga från andra källor. Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.

## <a name="additional-resources"></a>Ytterligare resurser

- [Homebrew-webb][brew]
- [Homebrew GitHub-lagringsplats][GitHub]
- [Homebrew – Cask][cask]

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
