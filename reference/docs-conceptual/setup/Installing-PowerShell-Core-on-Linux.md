# <a name="installing-powershell-core-on-linux"></a>Installera PowerShell Core i Linux

Supports <bpt id="p1">[</bpt>Ubuntu 14.04<ept id="p1">]</ept><bpt id="p2">[</bpt><ept id="p2">u14]</ept>, <bpt id="p3">[</bpt>Ubuntu 16.04<ept id="p3">]</ept><bpt id="p4">[</bpt><ept id="p4">u16]</ept>, <bpt id="p5">[</bpt>Ubuntu 17.04<ept id="p5">]</ept><bpt id="p6">[</bpt><ept id="p6">u17]</ept>, <bpt id="p7">[</bpt>Debian 8<ept id="p7">]</ept><bpt id="p8">[</bpt><ept id="p8">deb8]</ept>, <bpt id="p9">[</bpt>Debian 9<ept id="p9">]</ept><bpt id="p10">[</bpt><ept id="p10">deb9]</ept>, <bpt id="p11">[</bpt>CentOS 7<ept id="p11">]</ept><bpt id="p12">[</bpt><ept id="p12">cos]</ept>, <bpt id="p13">[</bpt>Red Hat Enterprise Linux (RHEL) 7<ept id="p13">]</ept><bpt id="p14">[</bpt><ept id="p14">rhel7]</ept>, <bpt id="p15">[</bpt>OpenSUSE 42.2<ept id="p15">]</ept><bpt id="p16">[</bpt><ept id="p16">opensuse]</ept>, <bpt id="p17">[</bpt>Fedora 27<ept id="p17">]</ept><bpt id="p18">[</bpt><ept id="p18">fedora]</ept>, <bpt id="p19">[</bpt>Fedora 28<ept id="p19">]</ept><bpt id="p20">[</bpt><ept id="p20">fedora]</ept>, and <bpt id="p21">[</bpt>Arch Linux<ept id="p21">]</ept><bpt id="p22">[</bpt><ept id="p22">arch]</ept>.

Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].
Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.

Alla paket är tillgängliga på vår GitHub [Versioner][] sidan.
När paketet har installerats kör `pwsh` från en terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
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

Som superanvändare, registrera Microsoft-databasen.
Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Installation via direkt hämta - Ubuntu 14.04

Hämta Debian-paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installation via direkt hämta - Ubuntu 16.04

Hämta Debian-paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
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
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.

### <a name="installation-via-direct-download---ubuntu-1704"></a>Installation via direkt hämta - Ubuntu nr 17.04 från

Hämta Debian-paket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
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

Hämta Debian-paket `powershell_6.0.2-1.debian.8_amd64.deb` från den [Versioner][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Observera att `dpkg -i` misslyckas med unmet beroenden.
> Nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

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

Hämta Debian-paket `powershell_6.0.2-1.debian.9_amd64.deb` från den [Versioner][] sidan på Debian dator.

Kör sedan följande i terminalen:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Observera att `dpkg -i` misslyckas med unmet beroenden.
> Nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.

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

Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sidan på CentOS dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sida på Red Hat Enterprise Linux-dator.

Kör sedan följande i terminalen:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Avinstallationen - Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

> [!NOTE]
> När du installerar PowerShell Core `zypper` kan rapportera följande fel:
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> I det här fallet kontrollerar du att en kompatibel `libcurl` bibliotek finns genom att kontrollera att följande kommando visar den `libcurl4` paketet som installerade:
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> Välj den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.

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

Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sida på OpenSUSE-dator.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Avinstallationen - OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installationen via Paketdatabasen (rekommenderas) - Fedora 27 Fedora 28

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installation via direkt hämta - Fedora 27, Fedora 28

Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sidan på Fedora dator.

Kör sedan följande i terminalen:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

Du kan också installera RPM utan mellanliggande steg för att hämta den:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Avinstallationen - Fedora 27, Fedora 28

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

[Arkitektur Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>Linux AppImage

Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.1-x86_64.AppImage` från den [Versioner][] sida på Linux-dator.

Kör sedan följande i terminalen:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

Den [AppImage][] kan du köra PowerShell utan att installera den.
Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.
Det här paketet är ett enda Binärvärde som fungerar oberoende av användarens Linux-distribution.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

### <a name="installation"></a>Installation

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Avinstallationen - Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

För närvarande stöds endast PowerShell på Raspbian Stretch.

Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och 3 Pi enheter som andra enheter som [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.

Hämta [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta till din Pi.

### <a name="installation"></a>Installation

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binär

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

PowerShell binär `tar.gz` Arkiv som har angetts för Linux-plattformar för att aktivera avancerade distribueringsscenarier.

### <a name="dependencies"></a>Beroenden

PowerShell skapar bärbara binärfiler för alla Linux-distributioner.
Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.

Följande diagram visar .NET Core 2.0 beroenden som stöds officiellt i olika Linux-distributioner.

| Operativsystem                 | Beroenden |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu nr 17.04 från       | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Debian 8 (Jessie)  | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6 <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, openssl-bibliotek, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10 |

Du måste installera de nödvändiga beroendena för målet OS i separata steg för att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt.
Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Installation – binära Arkiv

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Avinstallera binära Arkiv

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Sökvägar

* `$PSHOME` Är `/opt/microsoft/powershell/6.0.2/`
* Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`
* Standardprofiler kommer att läsas från `$PSHOME/profile.ps1`
* Moduler som användare kommer att läsas från `~/.local/share/powershell/Modules`
* Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`
* Standardmoduler ska läsas från `$PSHOME/Modules`
* PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.

PowerShell respekterar den [XDG Base Directory specifikationen] [ xdg-bds] på Linux.

[Versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
