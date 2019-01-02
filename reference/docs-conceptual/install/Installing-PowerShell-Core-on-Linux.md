---
title: Installera PowerShell Core i Linux
description: Information om att installera PowerShell Core på olika Linux-distributioner
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405033"
---
# <a name="installing-powershell-core-on-linux"></a>Installera PowerShell Core i Linux

Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9] [ deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [ Fedora 28][fedora], och [båge Linux][arch].

För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell Fäst paketet][snap].
Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.

Alla paket finns på vår GitHub [versioner][] sidan.
När paketet har installerats kan du köra `pwsh` från en terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Installera förhandsversioner

När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.

Installerar via direct hämtning ändras inte, än namnet på filen.

Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:

|Distribution(s)|Stabil kommando | Förhandsgranskningskommandot |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, Red Hat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Installationen via Paketdatabasen - Ubuntu 14.04

PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Som superanvändare, registrera Microsoft-databasen.
Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installationen via Direct hämtning - Ubuntu 14.04

Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
från den [versioner][] sidan på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.
> Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1404"></a>Avinstallationen - Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Installationen via Paketdatabasen - Ubuntu 16.04

PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).
Detta är föredragen metod.

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

När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installationen via Direct hämtning - Ubuntu 16.04

Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
från den [versioner][] sidan på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.
> Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1604"></a>Avinstallationen - Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Stöd för Ubuntu 18.04 har lagts till efter `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Installationen via Paketdatabasen - Ubuntu 18.04

PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Installationen via Direct hämtning - Ubuntu 18.04

Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
från den [versioner][] sidan på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.
> Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.

### <a name="uninstallation---ubuntu-1804"></a>Avinstallationen - Ubuntu 18.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Stöd för Ubuntu 18.10 har lagts till efter `6.1.0-preview.3`.
> Eftersom 18.10 är en daglig version, är det bara community stöds.

Installera på 18.10 stöds via `snapd`. Se [Fäst paketet] [ snap] fullständiga instruktioner;

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Installationen via Paketdatabasen – Debian 8

PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).
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

När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---debian-8"></a>Installationen via Direct hämtning – Debian 8

Ladda ned Debian-paket `powershell_6.1.0-1.debian.8_amd64.deb`
från den [versioner][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.
> Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.

### <a name="uninstallation---debian-8"></a>Avinstallationen – Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Installationen via Paketdatabasen - Debian 9

PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).
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

När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---debian-9"></a>Installationen via Direct hämtning - Debian 9

Ladda ned Debian-paket `powershell_6.1.0-1.debian.9_amd64.deb`
från den [versioner][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Avinstallationen - Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Det här paketet fungerar även på Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Installationen via Paketdatabasen (rekommenderas) - CentOS 7

PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Installationen via Direct hämtning - CentOS 7

Med hjälp av [CentOS 7][], ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
från den [versioner][] sidan på CentOS-dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Avinstallationen - CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7

PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7

Ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
från den [versioner][] sidan på Red Hat Enterprise Linux-dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Avinstallationen - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>OpenSUSE

### <a name="installation---opensuse-423"></a>Installation - openSUSE 42.3

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a>Installation - openSUSE Leap 15

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Avinstallationen - openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 stöds bara i PowerShell Core 6.1 och senare.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28

PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installationen via Direct hämtning - Fedora 27, Fedora 28

Ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`
från den [versioner][] sidan på Fedora-dator.

Kör sedan följande i terminalen:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Avinstallationen - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Stöd för arch är experimentella.

PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).

* Den kan sammanställas med den [senaste taggade versionen][arch-release]
* Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]
* Den kan installeras med den [senaste versionen binär][arch-bin]

Paket i AUR är community underhålls - stöds inte officiellt.

Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Fäst paket

### <a name="getting-snapd"></a>Hämta snapd

`snapd` krävs för att köra fäster.
Använd [instruktionerna](https://docs.snapcraft.io/core/install) att kontrollera att du har `snapd` installerad.

### <a name="installation-via-snap"></a>Installationen via snapin

PowerShell Core för Linux, publiceras till den [snapin store](https://snapcraft.io/store) för enkel installation (och uppdateringar).
Detta är föredragen metod.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Om du vill installera förhandsversionen kan du använda följande metod.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

När du installerar snapin uppgraderar automatiskt, men du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Avinstallation

```sh
sudo snap remove powershell
```

eller

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Installation - Kali

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a>Avinstallationen - Kali

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Stöd för Raspbian är experimentella.

För närvarande stöds endast PowerShell på Raspbian Stretch.

Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.

Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.

### <a name="installation---raspbian"></a>Installation - Raspbian

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Avinstallationen - Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Binär Arkiv

PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.

### <a name="dependencies"></a>Beroenden

PowerShell skapar bärbar binärfiler för alla Linux-distributioner.
Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.

Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.

| Operativsystem                 | Beroenden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-bibliotek, libicu |
| OpenSUSE 42.3 | libcurl4 libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4 libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10 |

Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.
Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation - binär Arkiv

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Avinstallera binära Arkiv

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Sökvägar

* `$PSHOME` är `/opt/microsoft/powershell/6.1.0/`
* Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`
* Standardprofiler ska läsas från `$PSHOME/profile.ps1`
* Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`
* Delade moduler ska läsas från `/usr/local/share/powershell/Modules`
* Standardmoduler ska läsas från `$PSHOME/Modules`
* PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.

[versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
