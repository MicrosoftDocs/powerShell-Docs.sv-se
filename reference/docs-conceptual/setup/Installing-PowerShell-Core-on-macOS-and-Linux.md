# <a name="installing-powershell-core-on-macos-and-linux"></a>Installera PowerShell Core på macOS- och Linux

Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu nr 17.04 från] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [båge Linux][arch], och [macOS 10.12][mac].

Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].
Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.

Alla paket är tillgängliga på vår GitHub [släpper][] sidan.
När paketet har installerats kör `pwsh` från en terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installation via Paketdatabasen - Ubuntu 14.04

PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installation via direkt hämta - Ubuntu 14.04

Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1404"></a>Avinstallationen - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installation via Paketdatabasen - Ubuntu 16.04

PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation via direkt hämta - Ubuntu 16.04

Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1604"></a>Avinstallationen - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a>Ubuntu nr 17.04 från

### <a name="installation-via-package-repository---ubuntu-1704"></a>Installation via Paketdatabasen - Ubuntu nr 17.04 från

PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Installation via direkt hämta - Ubuntu nr 17.04 från

Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1704"></a>Avinstallationen - Ubuntu nr 17.04 från

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installation via Paketdatabasen - Debian 8

PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---debian-8"></a>Installation via direkt hämta - Debian 8

Hämta Debian-paket `powershell_6.0.0-rc-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

### <a name="uninstallation---debian-8"></a>Avinstallationen - Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installation via Paketdatabasen - Debian 9

PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---debian-9"></a>Installation via direkt hämta - Debian 9

Hämta Debian-paket `powershell_6.0.0-rc-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

### <a name="uninstallation---debian-9"></a>Avinstallationen - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> Det här paketet fungerar även på Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installationen via Paketdatabasen (rekommenderas) - CentOS 7

PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Installation via direkt hämta - CentOS 7

Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Avinstallationen - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installationen via Paketdatabasen (rekommenderas) - Red Hat Enterprise Linux (RHEL) 7

PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installation via direkt hämta - Red Hat Enterprise Linux (RHEL) 7

Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sida på Red Hat Enterprise Linux-dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Avinstallationen - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> **Obs:** när du installerar PowerShell Core, OpenSUSE kan rapportera att ingenting tillhandahåller `libcurl`.
`libcurl`bör vara installerad på versioner av OpenSUSE stöds.
Kör `zypper search libcurl` att bekräfta.
Felet presenterar 2 lösningar. Välj lösning 2 fortsätta installera PowerShell Core.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.2

PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Installation via direkt hämta - OpenSUSE 42.2

Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sida på OpenSUSE-dator.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Avinstallationen - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a>Fedora 25

### <a name="installation-via-package-repository-preferred---fedora-25"></a>Installationen via Paketdatabasen (rekommenderas) - Fedora 25

PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a>Installation via direkt hämta - Fedora 25

Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator.

Kör sedan följande i terminalen:

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a>Avinstallationen - Fedora 25

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a>Fedora 26

### <a name="installation-via-package-repository-preferred---fedora-26"></a>Installationen via Paketdatabasen (rekommenderas) - Fedora 26

PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-26"></a>Installation via direkt hämta - Fedora 26

Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator.

Kör sedan följande i terminalen:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a>Avinstallationen - Fedora 26

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arkitektur Linux

PowerShell är tillgänglig från den [arkitektur Linux][] användaren databasen (AUR).

* Det kan vara kompilerat med den [senaste märkta versionen][arch-release]
* Det kan sammanställas från den [senaste bekräftelse master][arch-git]
* Den kan installeras med hjälp av den [senaste versionen binär][arch-bin]

Paket i AUR är community underhålls - stöds inte officiellt.

Mer information om hur du installerar paket från AUR finns i [arkitektur Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller gemenskapen [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[arkitektur Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.0-rc-x86_64.AppImage` från den [släpper][] sida på Linux-dator.

Kör sedan följande i terminalen:

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

Den [AppImage][] kan du köra PowerShell utan att installera den.
Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.
Det här paketet fungerar oberoende av användarens Linux-distribution och är ett enda binärvärde.

[appimage]: http://appimage.org/

## <a name="macos-1012"></a>macOS 10.12

### <a name="installation-via-homebrew-preferred---macos-1012"></a>Installationen via Homebrew (rekommenderas) - macOS 10.12

[Homebrew] [ brew] är saknas package manager för macOS.
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

När nya versioner av PowerShell släpps uppdatera Homebrews formler och uppgradera PowerShell:

```sh
brew update
brew cask reinstall powershell
```

> Obs: grund av [problemet i Cask](https://github.com/caskroom/homebrew-cask/issues/29301), du har för närvarande att göra en ominstallation att uppgradera.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a>Installationen via direkt hämta - macOS 10.12

Använder macOS 10.12 kan hämta paketet PKG `powershell-6.0.0-rc-osx.10.12-x64.pkg` från den [släpper][] sida på macOS-dator.

Dubbelklicka på filen och följ anvisningarna för, eller installera det från terminalen:

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a>Avinstallationen - macOS 10.12

Om du har installerat PowerShell med Homebrew är avinstallationen enkel:

```sh
brew cask uninstall powershell
```

Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Så här avinstallerar du ytterligare PowerShell-sökvägar (till exempel sökvägen till användarprofilen) finns på [sökvägar] [ paths] nedan i det här dokumentet och ta bort den önskade sökvägar med `sudo rm`.
(Observera: Detta är inte nödvändigt om du har installerat med Homebrew.)

[paths]:#paths

## <a name="kali"></a>Kali

### <a name="installation"></a>Installation

```sh
# Install prerequisites
apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Avinstallationen - Kali

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

För närvarande stöds endast PowerShell på Raspbian Stretch.

### <a name="installation"></a>Installation

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-rc-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a>Avinstallationen - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binär Arkiv

PowerShell binär `tar.gz` Arkiv som har angetts för macOS- och Linux-plattformar för att aktivera avancerade distribueringsscenarier.

### <a name="dependencies"></a>Beroenden

För Linux bygger PowerShell bärbara binärfiler för alla Linux-distributioner.
Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.

Följande diagram visar beroenden för .NET Core 2.0 på olika Linux-distributioner som stöds officiellt.

| Operativsystem                 | Beroenden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu nr 17.04 från       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 <br> Fedora 25 | libunwind, libcurl, openssl-bibliotek, libicu |
| Fedora 26          | libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10 |

För att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt, skulle du behöva installera de nödvändiga beroendena för målet OS i separata steg.
Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation – binära Arkiv

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0-rc/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a>macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0-rc

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0-rc

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0-rc/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0-rc/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a>Avinstallationen - binära Arkiv

#### <a name="linux"></a>Linux

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a>macOS

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a>Sökvägar

* `$PSHOME`är`/opt/microsoft/powershell/6.0.0-rc/`
* Användarprofiler som ska läsas från`~/.config/powershell/profile.ps1`
* Standardprofiler kommer att läsas från`$PSHOME/profile.ps1`
* Moduler som användare kommer att läsas från`~/.local/share/powershell/Modules`
* Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`
* Standardmoduler ska läsas från`$PSHOME/Modules`
* PSReadline historik kommer att läggas till`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

På Linux- och macOS, den [XDG Base Directory specifikationen] [ xdg-bds] följs.

Observera att eftersom macOS är en härledning av BSD, i stället för `/opt`, prefix som används är `/usr/local`.
Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.0-rc/`, och symlink är placerad på `/usr/local/bin/pwsh`.

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
