# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="a7d91-101">Installera PowerShell Core i macOS och Linux</span><span class="sxs-lookup"><span data-stu-id="a7d91-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="a7d91-102">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu nr 17.04 från] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25 ] [ fed25], [Fedora 26][fed26], [båge Linux][arch], och [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="a7d91-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="a7d91-103">Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="a7d91-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="a7d91-104">Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.</span><span class="sxs-lookup"><span data-stu-id="a7d91-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="a7d91-105">Alla paket är tillgängliga på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="a7d91-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="a7d91-106">När paketet har installerats kör `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="a7d91-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="a7d91-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="a7d91-108">Installation via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="a7d91-109">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="a7d91-110">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="a7d91-110">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d91-111">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="a7d91-112">Installation via direkt hämta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="a7d91-113">Hämta Debian-paket `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="a7d91-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="a7d91-114">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="a7d91-115">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="a7d91-116">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="a7d91-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="a7d91-118">Installation via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="a7d91-119">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d91-120">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="a7d91-120">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d91-121">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="a7d91-122">Installation via direkt hämta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="a7d91-123">Hämta Debian-paket `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="a7d91-124">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="a7d91-125">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="a7d91-126">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="a7d91-127">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="a7d91-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="a7d91-128">Installation via Paketdatabasen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="a7d91-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="a7d91-129">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d91-130">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="a7d91-130">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d91-131">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="a7d91-132">Installation via direkt hämta - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="a7d91-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="a7d91-133">Hämta Debian-paket `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="a7d91-134">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="a7d91-135">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="a7d91-136">Avinstallationen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="a7d91-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="a7d91-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d91-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="a7d91-138">Installation via Paketdatabasen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d91-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="a7d91-139">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d91-140">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="a7d91-140">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d91-141">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="a7d91-142">Installation via direkt hämta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d91-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="a7d91-143">Hämta Debian-paket `powershell_6.0.0-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="a7d91-144">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="a7d91-145">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="a7d91-146">Avinstallationen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="a7d91-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="a7d91-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d91-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="a7d91-148">Installation via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d91-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="a7d91-149">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="a7d91-150">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="a7d91-150">This is the preferred method.</span></span>

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

<span data-ttu-id="a7d91-151">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="a7d91-152">Installation via direkt hämta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d91-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="a7d91-153">Hämta Debian-paket `powershell_6.0.0-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="a7d91-154">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="a7d91-155">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="a7d91-156">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="a7d91-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="a7d91-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-157">CentOS 7</span></span>

> <span data-ttu-id="a7d91-158">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="a7d91-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="a7d91-159">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="a7d91-160">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d91-161">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d91-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="a7d91-162">Installation via direkt hämta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="a7d91-163">Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-164">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-165">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="a7d91-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="a7d91-166">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d91-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d91-169">Installationen via Paketdatabasen (rekommenderas) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a7d91-170">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="a7d91-171">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d91-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d91-172">Installation via direkt hämta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="a7d91-173">Hämta RPM-paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` från den [släpper][] sida på Red Hat Enterprise Linux-dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="a7d91-174">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-175">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="a7d91-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="a7d91-176">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="a7d91-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a7d91-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="a7d91-178">**Obs:** när du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="a7d91-178">**Note:** When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```text
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="a7d91-179">I det här fallet kontrollerar du att en kompatibel `libcurl` bibliotek finns genom att kontrollera att följande kommando visar den `libcurl4` paketet som installerade:</span><span class="sxs-lookup"><span data-stu-id="a7d91-179">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="a7d91-180">Välj den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar den `powershell` paketet.</span><span class="sxs-lookup"><span data-stu-id="a7d91-180">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the `powershell` package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="a7d91-181">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a7d91-181">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="a7d91-182">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-182">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="a7d91-183">Installation via direkt hämta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a7d91-183">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="a7d91-184">Hämta RPM-paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` från den [släpper][] sida på OpenSUSE dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-184">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-185">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="a7d91-185">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="a7d91-186">Avinstallationen - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a7d91-186">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="a7d91-187">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="a7d91-187">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="a7d91-188">Installationen via Paketdatabasen (rekommenderas) - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="a7d91-188">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="a7d91-189">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="a7d91-190">Installation via direkt hämta - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="a7d91-190">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="a7d91-191">Hämta RPM-paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-191">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-192">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-192">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-193">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="a7d91-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="a7d91-194">Avinstallationen - Fedora 25</span><span class="sxs-lookup"><span data-stu-id="a7d91-194">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="a7d91-195">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="a7d91-195">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="a7d91-196">Installationen via Paketdatabasen (rekommenderas) - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="a7d91-196">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="a7d91-197">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="a7d91-197">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="a7d91-198">Installation via direkt hämta - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="a7d91-198">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="a7d91-199">Hämta RPM-paket `powershell-6.0.0-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator:</span><span class="sxs-lookup"><span data-stu-id="a7d91-199">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-200">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-200">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="a7d91-201">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="a7d91-201">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="a7d91-202">Avinstallationen - Fedora 26</span><span class="sxs-lookup"><span data-stu-id="a7d91-202">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="a7d91-203">Arkitektur Linux</span><span class="sxs-lookup"><span data-stu-id="a7d91-203">Arch Linux</span></span>

<span data-ttu-id="a7d91-204">PowerShell är tillgänglig från den [arkitektur Linux][] användaren databasen (AUR).</span><span class="sxs-lookup"><span data-stu-id="a7d91-204">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="a7d91-205">Det kan vara kompilerat med den [senaste märkta versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="a7d91-205">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="a7d91-206">Det kan sammanställas från den [senaste bekräftelse master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="a7d91-206">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="a7d91-207">Den kan installeras med hjälp av den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="a7d91-207">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="a7d91-208">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="a7d91-208">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="a7d91-209">Mer information om hur du installerar paket från AUR finns i [arkitektur Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller gemenskapen [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="a7d91-209">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[arkitektur Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="a7d91-211">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="a7d91-211">Linux AppImage</span></span>

<span data-ttu-id="a7d91-212">Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.0-x86_64.AppImage` från den [släpper][] sida på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="a7d91-212">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="a7d91-213">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-213">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="a7d91-214">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="a7d91-214">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="a7d91-215">Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="a7d91-215">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="a7d91-216">Det här paketet fungerar oberoende av användarens Linux-distribution och är ett enda binärvärde.</span><span class="sxs-lookup"><span data-stu-id="a7d91-216">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="a7d91-218">macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="a7d91-218">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="a7d91-219">Installationen via Homebrew (rekommenderas) - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="a7d91-219">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="a7d91-220">[Homebrew] [ brew] är saknas package manager för macOS.</span><span class="sxs-lookup"><span data-stu-id="a7d91-220">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="a7d91-221">Om den `brew` kommando inte hittas, måste du installera följande Homebrew [instruktionerna][brew].</span><span class="sxs-lookup"><span data-stu-id="a7d91-221">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="a7d91-222">När du har installerat Homebrew, är det enkelt att installera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7d91-222">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="a7d91-223">Installera först [Homebrew Cask][cask], så kan du installera flera paket:</span><span class="sxs-lookup"><span data-stu-id="a7d91-223">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="a7d91-224">Du kan nu installera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d91-224">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="a7d91-225">När nya versioner av PowerShell släpps uppdatera Homebrews formler och uppgradera PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7d91-225">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> <span data-ttu-id="a7d91-226">Obs: Kommandona ovan kan anropas från en värd med PowerShell (pwsh), men sedan PowerShell-gränssnittet måste avslutades och angavs igen för att slutföra uppgraderingen och uppdatera värdena som visas i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="a7d91-226">Note: The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and re-entered to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="a7d91-227">Installationen via direkt hämta - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="a7d91-227">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="a7d91-228">Använder macOS 10.12 kan hämta paketet PKG `powershell-6.0.0-osx.10.12-x64.pkg` från den [släpper][] sida på macOS-dator.</span><span class="sxs-lookup"><span data-stu-id="a7d91-228">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="a7d91-229">Dubbelklicka på filen och följ anvisningarna för, eller installera det från terminalen:</span><span class="sxs-lookup"><span data-stu-id="a7d91-229">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="a7d91-230">Avinstallationen - macOS 10.12</span><span class="sxs-lookup"><span data-stu-id="a7d91-230">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="a7d91-231">Om du har installerat PowerShell med Homebrew är avinstallationen enkel:</span><span class="sxs-lookup"><span data-stu-id="a7d91-231">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="a7d91-232">Om du har installerat PowerShell via direkt hämtning måste PowerShell tas bort manuellt:</span><span class="sxs-lookup"><span data-stu-id="a7d91-232">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="a7d91-233">Så här avinstallerar du ytterligare PowerShell-sökvägar (till exempel sökvägen till användarprofilen) finns på [sökvägar] [ paths] nedan i det här dokumentet och ta bort den önskade sökvägar med `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="a7d91-233">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="a7d91-234">(Observera: Detta är inte nödvändigt om du har installerat med Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="a7d91-234">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="a7d91-235">Kali</span><span class="sxs-lookup"><span data-stu-id="a7d91-235">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="a7d91-236">Installation</span><span class="sxs-lookup"><span data-stu-id="a7d91-236">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="a7d91-237">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.</span><span class="sxs-lookup"><span data-stu-id="a7d91-237">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="a7d91-238">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="a7d91-238">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="a7d91-239">Raspbian</span><span class="sxs-lookup"><span data-stu-id="a7d91-239">Raspbian</span></span>

<span data-ttu-id="a7d91-240">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="a7d91-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="a7d91-241">Installation</span><span class="sxs-lookup"><span data-stu-id="a7d91-241">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="a7d91-242">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="a7d91-242">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="a7d91-243">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="a7d91-243">Binary Archives</span></span>

<span data-ttu-id="a7d91-244">PowerShell binär `tar.gz` Arkiv som har angetts för macOS- och Linux-plattformar för att aktivera avancerade distribueringsscenarier.</span><span class="sxs-lookup"><span data-stu-id="a7d91-244">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="a7d91-245">Beroenden</span><span class="sxs-lookup"><span data-stu-id="a7d91-245">Dependencies</span></span>

<span data-ttu-id="a7d91-246">För Linux bygger PowerShell bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="a7d91-246">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="a7d91-247">Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.</span><span class="sxs-lookup"><span data-stu-id="a7d91-247">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="a7d91-248">Följande diagram visar beroenden för .NET Core 2.0 på olika Linux-distributioner som stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="a7d91-248">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="a7d91-249">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="a7d91-249">OS</span></span>                 | <span data-ttu-id="a7d91-250">Beroenden</span><span class="sxs-lookup"><span data-stu-id="a7d91-250">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="a7d91-251">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-251">Ubuntu 14.04</span></span>       | <span data-ttu-id="a7d91-252">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d91-252">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d91-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a7d91-253">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a7d91-254">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="a7d91-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="a7d91-255">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d91-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d91-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="a7d91-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="a7d91-257">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="a7d91-257">Ubuntu 17.04</span></span>       | <span data-ttu-id="a7d91-258">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d91-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d91-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="a7d91-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="a7d91-260">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="a7d91-260">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="a7d91-261">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d91-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d91-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="a7d91-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="a7d91-263">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="a7d91-263">Debian 9 (Stretch)</span></span> | <span data-ttu-id="a7d91-264">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="a7d91-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="a7d91-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="a7d91-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="a7d91-266">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-266">CentOS 7</span></span> <br> <span data-ttu-id="a7d91-267">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-267">Oracle Linux 7</span></span> <br> <span data-ttu-id="a7d91-268">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="a7d91-268">RHEL 7</span></span> <br> <span data-ttu-id="a7d91-269">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="a7d91-269">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="a7d91-270">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="a7d91-270">Fedora 25</span></span> | <span data-ttu-id="a7d91-271">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="a7d91-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="a7d91-272">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="a7d91-272">Fedora 26</span></span>          | <span data-ttu-id="a7d91-273">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="a7d91-273">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="a7d91-274">För att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt, skulle du behöva installera de nödvändiga beroendena för målet OS i separata steg.</span><span class="sxs-lookup"><span data-stu-id="a7d91-274">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="a7d91-275">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="a7d91-275">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="a7d91-276">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="a7d91-276">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="a7d91-277">Linux</span><span class="sxs-lookup"><span data-stu-id="a7d91-277">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="a7d91-278">macOS</span><span class="sxs-lookup"><span data-stu-id="a7d91-278">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="a7d91-279">Avinstallationen - binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="a7d91-279">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="a7d91-280">Linux</span><span class="sxs-lookup"><span data-stu-id="a7d91-280">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="a7d91-281">macOS</span><span class="sxs-lookup"><span data-stu-id="a7d91-281">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="a7d91-282">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="a7d91-282">Paths</span></span>

* <span data-ttu-id="a7d91-283">`$PSHOME` Är `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="a7d91-283">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="a7d91-284">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d91-284">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="a7d91-285">Standardprofiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="a7d91-285">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="a7d91-286">Moduler som användare kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d91-286">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d91-287">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d91-287">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="a7d91-288">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="a7d91-288">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="a7d91-289">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="a7d91-289">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="a7d91-290">Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="a7d91-290">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="a7d91-291">På Linux- och macOS, den [XDG Base Directory specifikationen] [ xdg-bds] följs.</span><span class="sxs-lookup"><span data-stu-id="a7d91-291">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="a7d91-292">Observera att eftersom macOS är en härledning av BSD, i stället för `/opt`, prefix som används är `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="a7d91-292">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="a7d91-293">Därför `$PSHOME` är `/usr/local/microsoft/powershell/6.0.0/`, och symlink är placerad på `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="a7d91-293">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
