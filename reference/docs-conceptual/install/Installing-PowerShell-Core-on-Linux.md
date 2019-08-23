---
title: Installera PowerShell Core i Linux
description: Information om hur du installerar PowerShell Core på olika Linux-distributioner
ms.date: 07/19/2019
ms.openlocfilehash: be11a2a873af71c193730d0a9e723da2dc70a62d
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986732"
---
# <a name="installing-powershell-core-on-linux"></a>Installera PowerShell Core i Linux

Stöder [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE skottår 15][opensuse], [Fedora 27 ][fedora], [Fedora 28][fedora]och [båge Linux][arch].

För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap]. Du kan också prova att distribuera PowerShell-binärfiler direkt med [ `tar.gz` ][tar]Linux-arkivet, men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.

Alla paket är tillgängliga på vår GitHub [releases][] sida. När paketet har installerats kör `pwsh` du från en Terminal.

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Installera för hands versioner

När du installerar en PowerShell Core Preview-version för Linux via en paket lagrings plats ändras paket `powershell` namnet `powershell-preview`från till.

Installation via direkt hämtning ändras inte, förutom fil namnet.

Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:

|Distribution (er)|Stabilt kommando | Förhandsgranska kommando |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installation via paket lagring – Ubuntu 16,04

PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.

Den bästa metoden är följande:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation via direkt hämtning – Ubuntu 16,04

Ladda ned Debian- `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden. Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.

### <a name="uninstallation---ubuntu-1604"></a>Avinstallation – Ubuntu 16,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installation via paket lagring – Ubuntu 18,04

PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.

Den bästa metoden är följande:

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installation via direkt hämtning – Ubuntu 18,04

Ladda ned Debian- `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden. Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.

### <a name="uninstallation---ubuntu-1804"></a>Avinstallation – Ubuntu 18,04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18,10

Installationen stöds via `snapd`. Instruktioner finns i [snapin-paket][snap].

> [!NOTE]
> Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds](../powershell-support-lifecycle.md)av communityn.

## <a name="ubuntu-1904"></a>Ubuntu 19,04

Installationen stöds via `snapd`. Instruktioner finns i [snapin-paket][snap].

> [!NOTE]
> Ubuntu 19,04 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds](../powershell-support-lifecycle.md)av communityn.

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installation via paket lagring – Debian 8

PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.

Den bästa metoden är följande:

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

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installation via paket lagring – Debian 9

PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.

Den bästa metoden är följande:

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

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---debian-9"></a>Installation via direkt hämtning – Debian 9

Ladda ned Debian- `powershell_6.2.0-1.debian.9_amd64.deb` paketet från sidan [releases][] på Debian-datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Avinstallation-Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Det här paketet fungerar på Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installation via paketets lagrings plats (prioriterad) – CentOS 7

PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.

### <a name="installation-via-direct-download---centos-7"></a>Installation via direkt hämtning – CentOS 7

Med [CentOS 7][]laddar du ned rpm- `powershell-6.2.0-1.rhel.7.x86_64.rpm` paketet från sidan [releases][] till CentOS-datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Du kan installera RPM utan det mellanliggande steget i att ladda ned det:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Avinstallation-CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7

PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Som superanvändare registrerar du Microsoft-lagringsplatsen en gång. Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7

Hämta rpm-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till Red Hat Enterprise Linux datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Du kan installera RPM utan det mellanliggande steget i att ladda ned det:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Avinstallation-Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Installation – openSUSE 42,3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Installation – openSUSE skottår 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Avinstallation – openSUSE 42,3, openSUSE skottår 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 stöds endast i PowerShell Core 6,1 och senare.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installation via paketets lagrings plats (rekommenderas) – Fedora 27, Fedora 28

PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installation via direkt hämtning – Fedora 27, Fedora 28

Hämta rpm-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] på Fedora-datorn.

Kör sedan följande kommandon i terminalen:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

Du kan installera RPM utan det mellanliggande steget i att ladda ned det:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Avinstallation-Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Båge Linux

> [!NOTE]
> Stöd för båge är experimentellt.

PowerShell är tillgängligt från användar lagrings platsen för [Båge Linux][] (AUR).

* Den kan kompileras med den [senaste taggade versionen][arch-release]
* Den kan kompileras från det [senaste genomförandeet till Master][arch-git]
* Den kan installeras med den [senaste versionen][arch-bin] av binärfilen

Paketen i AUR är grupperade. Det finns inget statligt stöd.

Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller community- [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Båge Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Snapin-paket

### <a name="getting-snapd"></a>Fäst

`snapd`krävs för att köra fäst. Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att `snapd` du har installerat.

### <a name="installation-via-snap"></a>Installation via Snap

PowerShell Core för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.

Den bästa metoden är följande:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Om du vill installera en för hands version använder du följande metod:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Efter installationen kommer Snap att uppgraderas automatiskt. Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Avinstallationen

```sh
sudo snap remove powershell
```

eller

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Installation – Kali

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Avinstallation – Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Raspbian-support är experimentell.

För närvarande stöds PowerShell bara för Raspbian-sträckning.

CoreCLR och PowerShell-kärnan fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.

Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.

### <a name="installation---raspbian"></a>Installation – Raspbian

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till den `pwsh` binära filen.

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Avinstallation – Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binära Arkiv

PowerShell- `tar.gz` binärfiler finns för Linux-plattformar för att aktivera avancerade distributions scenarier.

### <a name="dependencies"></a>Relation

PowerShell skapar bärbara binärfiler för alla Linux-distributioner. .NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.

Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.

| Operativsystem                 | Relation |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55 |
| Ubuntu 17,10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52 |
| Debian 9 (sträck ut) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libsväng, OpenSSL-libs, libicu |
| openSUSE 42,3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE-skottår 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10 |

Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg. Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux `tar.gz` -arkivet.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Installation – binära Arkiv

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Avinstallerar binära Arkiv

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Sökvägar

* `$PSHOME`utgör`/opt/microsoft/powershell/6.2.0/`
* Användar profilerna kommer att läsas från`~/.config/powershell/profile.ps1`
* Standard profiler kommer att läsas från`$PSHOME/profile.ps1`
* Användarens moduler kommer att läsas från`~/.local/share/powershell/Modules`
* Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`
* Standardmoduler kommer att läsas från`$PSHOME/Modules`
* PSReadline historik registreras i`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade `Microsoft.PowerShell_profile.ps1` profilerna finns på samma platser.

PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
