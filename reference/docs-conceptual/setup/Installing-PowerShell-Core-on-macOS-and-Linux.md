# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="c659f-101">Installera PowerShell Core på macOS- och Linux</span><span class="sxs-lookup"><span data-stu-id="c659f-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="c659f-102">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu nr 17.04 från] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [båge Linux][arch], och [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="c659f-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="c659f-103">Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="c659f-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="c659f-104">Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.</span><span class="sxs-lookup"><span data-stu-id="c659f-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="c659f-105">Alla paket är tillgängliga på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="c659f-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c659f-106">När paketet har installerats kör `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="c659f-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="c659f-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c659f-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="c659f-108">Installation via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c659f-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="c659f-109">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c659f-110">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="c659f-110">This is the preferred method.</span></span>

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

<span data-ttu-id="c659f-111">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="c659f-112">Installation via direkt hämta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c659f-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="c659f-113">Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-113">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c659f-114">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c659f-115">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="c659f-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="c659f-116">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c659f-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="c659f-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c659f-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="c659f-118">Installation via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c659f-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="c659f-119">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c659f-120">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="c659f-120">This is the preferred method.</span></span>

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

<span data-ttu-id="c659f-121">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="c659f-122">Installation via direkt hämta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c659f-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="c659f-123">Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-123">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c659f-124">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c659f-125">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="c659f-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="c659f-126">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c659f-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="c659f-127">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="c659f-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="c659f-128">Installation via Paketdatabasen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="c659f-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="c659f-129">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c659f-130">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="c659f-130">This is the preferred method.</span></span>

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

<span data-ttu-id="c659f-131">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="c659f-132">Installation via direkt hämta - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="c659f-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="c659f-133">Hämta Debian-paket `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-133">Download the Debian package `powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="c659f-134">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c659f-135">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="c659f-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="c659f-136">Avinstallationen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="c659f-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="c659f-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="c659f-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="c659f-138">Installation via Paketdatabasen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c659f-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="c659f-139">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c659f-140">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="c659f-140">This is the preferred method.</span></span>

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

<span data-ttu-id="c659f-141">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="c659f-142">Installation via direkt hämta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c659f-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="c659f-143">Hämta Debian-paket `powershell_6.0.0-rc-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-143">Download the Debian package `powershell_6.0.0-rc-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c659f-144">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c659f-145">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="c659f-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="c659f-146">Avinstallationen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="c659f-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="c659f-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="c659f-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="c659f-148">Installation via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c659f-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="c659f-149">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="c659f-150">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="c659f-150">This is the preferred method.</span></span>

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

<span data-ttu-id="c659f-151">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="c659f-152">Installation via direkt hämta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c659f-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="c659f-153">Hämta Debian-paket `powershell_6.0.0-rc-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-153">Download the Debian package `powershell_6.0.0-rc-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="c659f-154">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-rc-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="c659f-155">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="c659f-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="c659f-156">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="c659f-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="c659f-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c659f-157">CentOS 7</span></span>

> <span data-ttu-id="c659f-158">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="c659f-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="c659f-159">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c659f-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="c659f-160">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c659f-161">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c659f-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="c659f-162">Installation via direkt hämta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c659f-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="c659f-163">Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="c659f-164">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c659f-165">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="c659f-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="c659f-166">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c659f-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c659f-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c659f-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c659f-169">Installationen via Paketdatabasen (rekommenderas) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c659f-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c659f-170">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="c659f-171">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c659f-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c659f-172">Installation via direkt hämta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c659f-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="c659f-173">Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sida på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-173">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="c659f-174">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c659f-175">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="c659f-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="c659f-176">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="c659f-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="c659f-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c659f-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="c659f-178">**Obs:** när du installerar PowerShell Core, OpenSUSE kan rapportera att ingenting tillhandahåller `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="c659f-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="c659f-179">`libcurl`bör vara installerad på versioner av OpenSUSE stöds.</span><span class="sxs-lookup"><span data-stu-id="c659f-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="c659f-180">Kör `zypper search libcurl` att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="c659f-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="c659f-181">Felet presenterar 2 lösningar.</span><span class="sxs-lookup"><span data-stu-id="c659f-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="c659f-182">Välj lösning 2 fortsätta installera PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="c659f-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="c659f-183">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c659f-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="c659f-184">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="c659f-185">Installation via direkt hämta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c659f-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="c659f-186">Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sida på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-186">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c659f-187">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="c659f-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="c659f-188">Avinstallationen - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c659f-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="c659f-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="c659f-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="c659f-190">Installationen via Paketdatabasen (rekommenderas) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="c659f-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="c659f-191">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="c659f-192">Installation via direkt hämta - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="c659f-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="c659f-193">Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-193">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c659f-194">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c659f-195">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="c659f-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="c659f-196">Avinstallationen - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="c659f-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="c659f-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c659f-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="c659f-198">Installationen via Paketdatabasen (rekommenderas) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c659f-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="c659f-199">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="c659f-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="c659f-200">Installation via direkt hämta - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c659f-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="c659f-201">Hämta RPM-paket `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-201">Download the RPM package `powershell-6.0.0_rc-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="c659f-202">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="c659f-203">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="c659f-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0_rc-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="c659f-204">Avinstallationen - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c659f-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="c659f-205">Arkitektur Linux</span><span class="sxs-lookup"><span data-stu-id="c659f-205">Arch Linux</span></span>

<span data-ttu-id="c659f-206">PowerShell är tillgänglig från den [arkitektur Linux][] användaren databasen (AUR).</span><span class="sxs-lookup"><span data-stu-id="c659f-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="c659f-207">Det kan vara kompilerat med den [senaste märkta versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="c659f-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="c659f-208">Det kan sammanställas från den [senaste bekräftelse master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="c659f-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="c659f-209">Den kan installeras med hjälp av den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="c659f-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="c659f-210">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="c659f-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="c659f-211">Mer information om hur du installerar paket från AUR finns i [arkitektur Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller gemenskapen [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="c659f-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[arkitektur Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="c659f-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="c659f-213">Linux AppImage</span></span>

<span data-ttu-id="c659f-214">Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.0-rc-x86_64.AppImage` från den [släpper][] sida på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-rc-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="c659f-215">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-rc-x86_64.AppImage
./powershell-6.0.0-rc-x86_64.AppImage
```

<span data-ttu-id="c659f-216">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="c659f-216">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="c659f-217">Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="c659f-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="c659f-218">Det här paketet fungerar oberoende av användarens Linux-distribution och är ett enda binärvärde.</span><span class="sxs-lookup"><span data-stu-id="c659f-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="c659f-220">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="c659f-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="c659f-221">Installationen via Homebrew (rekommenderas) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="c659f-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="c659f-222">[Homebrew] [ brew] är saknas package manager för macOS.</span><span class="sxs-lookup"><span data-stu-id="c659f-222">[Homebrew][brew] is the missing package manager for macOS.</span></span>
<span data-ttu-id="c659f-223">Om den `brew` kommando inte hittas, måste du installera följande Homebrew [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="c659f-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="c659f-224">När du har installerat Homebrew, är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c659f-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="c659f-225">Installera först [Homebrew Cask][cask], så kan du installera flera paket:</span><span class="sxs-lookup"><span data-stu-id="c659f-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="c659f-226">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c659f-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="c659f-227">När nya versioner av PowerShell släpps uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c659f-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="c659f-228">Obs: grund av [problemet i Cask](https://github.com/caskroom/homebrew-cask/issues/29301), du har för närvarande att göra en ominstallation att uppgradera.</span><span class="sxs-lookup"><span data-stu-id="c659f-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="c659f-229">Installationen via direkt hämta - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="c659f-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="c659f-230">Använder macOS 10.12 kan hämta paketet PKG `powershell-6.0.0-rc-osx.10.12-x64.pkg` från den [släpper][] sida på macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="c659f-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-rc-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="c659f-231">Dubbelklicka på filen och följ anvisningarna för, eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="c659f-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-rc-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="c659f-232">Avinstallationen - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="c659f-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="c659f-233">Om du har installerat PowerShell med Homebrew är avinstallationen enkel:</span><span class="sxs-lookup"><span data-stu-id="c659f-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="c659f-234">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="c659f-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c659f-235">Så här avinstallerar du ytterligare PowerShell-sökvägar (till exempel sökvägen till användarprofilen) finns på [sökvägar] [ paths] nedan i det här dokumentet och ta bort den önskade sökvägar med `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="c659f-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span>
<span data-ttu-id="c659f-236">(Observera: Detta är inte nödvändigt om du har installerat med Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="c659f-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="c659f-237">Kali</span><span class="sxs-lookup"><span data-stu-id="c659f-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="c659f-238">Installation</span><span class="sxs-lookup"><span data-stu-id="c659f-238">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="c659f-239">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.</span><span class="sxs-lookup"><span data-stu-id="c659f-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0-rc/powershell-6.0.0-rc-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-rc-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-rc-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="c659f-240">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="c659f-240">Uninstallation - Kali</span></span>

```sh
dpkg -r powershell_6.0.0-rc-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="c659f-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="c659f-241">Raspbian</span></span>

<span data-ttu-id="c659f-242">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="c659f-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="c659f-243">Installation</span><span class="sxs-lookup"><span data-stu-id="c659f-243">Installation</span></span>

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

### <a name="uninstallation---raspbian"></a><span data-ttu-id="c659f-244">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="c659f-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="c659f-245">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="c659f-245">Binary Archives</span></span>

<span data-ttu-id="c659f-246">PowerShell binär `tar.gz` Arkiv som har angetts för macOS- och Linux-plattformar för att aktivera avancerade distribueringsscenarier.</span><span class="sxs-lookup"><span data-stu-id="c659f-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="c659f-247">Beroenden</span><span class="sxs-lookup"><span data-stu-id="c659f-247">Dependencies</span></span>

<span data-ttu-id="c659f-248">För Linux bygger PowerShell bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="c659f-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="c659f-249">Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.</span><span class="sxs-lookup"><span data-stu-id="c659f-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="c659f-250">Följande diagram visar beroenden för .NET Core 2.0 på olika Linux-distributioner som stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="c659f-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="c659f-251">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="c659f-251">OS</span></span>                 | <span data-ttu-id="c659f-252">Beroenden</span><span class="sxs-lookup"><span data-stu-id="c659f-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="c659f-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="c659f-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="c659f-254">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c659f-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c659f-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c659f-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c659f-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="c659f-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="c659f-257">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c659f-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c659f-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="c659f-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="c659f-259">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="c659f-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="c659f-260">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c659f-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c659f-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="c659f-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="c659f-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="c659f-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="c659f-263">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c659f-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c659f-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="c659f-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="c659f-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="c659f-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="c659f-266">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="c659f-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="c659f-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="c659f-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="c659f-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="c659f-268">CentOS 7</span></span> <br> <span data-ttu-id="c659f-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="c659f-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="c659f-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="c659f-270">RHEL 7</span></span> <br> <span data-ttu-id="c659f-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="c659f-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="c659f-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="c659f-272">Fedora 25</span></span> | <span data-ttu-id="c659f-273">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="c659f-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="c659f-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="c659f-274">Fedora 26</span></span>          | <span data-ttu-id="c659f-275">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="c659f-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="c659f-276">För att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt, skulle du behöva installera de nödvändiga beroendena för målet OS i separata steg.</span><span class="sxs-lookup"><span data-stu-id="c659f-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="c659f-277">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="c659f-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="c659f-278">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="c659f-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c659f-279">Linux</span><span class="sxs-lookup"><span data-stu-id="c659f-279">Linux</span></span>

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

#### <a name="macos"></a><span data-ttu-id="c659f-280">macOS</span><span class="sxs-lookup"><span data-stu-id="c659f-280">macOS</span></span>

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

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="c659f-281">Avinstallationen - binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="c659f-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="c659f-282">Linux</span><span class="sxs-lookup"><span data-stu-id="c659f-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="c659f-283">macOS</span><span class="sxs-lookup"><span data-stu-id="c659f-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="c659f-284">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="c659f-284">Paths</span></span>

* <span data-ttu-id="c659f-285">`$PSHOME`är`/opt/microsoft/powershell/6.0.0-rc/`</span><span class="sxs-lookup"><span data-stu-id="c659f-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0-rc/`</span></span>
* <span data-ttu-id="c659f-286">Användarprofiler som ska läsas från`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c659f-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c659f-287">Standardprofiler kommer att läsas från`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c659f-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c659f-288">Moduler som användare kommer att läsas från`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c659f-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c659f-289">Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c659f-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c659f-290">Standardmoduler ska läsas från`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c659f-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c659f-291">PSReadline historik kommer att läggas till`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c659f-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c659f-292">Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="c659f-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c659f-293">På Linux- och macOS, den [XDG Base Directory specifikationen] [ xdg-bds] följs.</span><span class="sxs-lookup"><span data-stu-id="c659f-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="c659f-294">Observera att eftersom macOS är en härledning av BSD, i stället för `/opt`, prefix som används är `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="c659f-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span>
<span data-ttu-id="c659f-295">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.0-rc/`, och symlink är placerad på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="c659f-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0-rc/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
