# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="36437-101">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="36437-101">Installing PowerShell Core on Linux</span></span>

Supports <bpt id="p1">[</bpt>Ubuntu 14.04<ept id="p1">]</ept><bpt id="p2">[</bpt><ept id="p2">u14]</ept>, <bpt id="p3">[</bpt>Ubuntu 16.04<ept id="p3">]</ept><bpt id="p4">[</bpt><ept id="p4">u16]</ept>, <bpt id="p5">[</bpt>Ubuntu 17.04<ept id="p5">]</ept><bpt id="p6">[</bpt><ept id="p6">u17]</ept>, <bpt id="p7">[</bpt>Debian 8<ept id="p7">]</ept><bpt id="p8">[</bpt><ept id="p8">deb8]</ept>, <bpt id="p9">[</bpt>Debian 9<ept id="p9">]</ept><bpt id="p10">[</bpt><ept id="p10">deb9]</ept>, <bpt id="p11">[</bpt>CentOS 7<ept id="p11">]</ept><bpt id="p12">[</bpt><ept id="p12">cos]</ept>, <bpt id="p13">[</bpt>Red Hat Enterprise Linux (RHEL) 7<ept id="p13">]</ept><bpt id="p14">[</bpt><ept id="p14">rhel7]</ept>, <bpt id="p15">[</bpt>OpenSUSE 42.2<ept id="p15">]</ept><bpt id="p16">[</bpt><ept id="p16">opensuse]</ept>, <bpt id="p17">[</bpt>Fedora 27<ept id="p17">]</ept><bpt id="p18">[</bpt><ept id="p18">fedora]</ept>, <bpt id="p19">[</bpt>Fedora 28<ept id="p19">]</ept><bpt id="p20">[</bpt><ept id="p20">fedora]</ept>, and <bpt id="p21">[</bpt>Arch Linux<ept id="p21">]</ept><bpt id="p22">[</bpt><ept id="p22">arch]</ept>.

<span data-ttu-id="36437-103">Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="36437-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="36437-104">Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.</span><span class="sxs-lookup"><span data-stu-id="36437-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="36437-105">Alla paket är tillgängliga på vår GitHub [Versioner][] sidan.</span><span class="sxs-lookup"><span data-stu-id="36437-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="36437-106">När paketet har installerats kör `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="36437-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="ubuntu-1404"></a><span data-ttu-id="36437-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="36437-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="36437-108">Installation via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="36437-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="36437-109">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="36437-110">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="36437-110">This is the preferred method.</span></span>

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

<span data-ttu-id="36437-111">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="36437-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="36437-112">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="36437-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="36437-113">Installation via direkt hämta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="36437-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="36437-114">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="36437-115">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="36437-116">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="36437-117">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="36437-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="36437-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="36437-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="36437-119">Installation via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="36437-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="36437-120">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="36437-121">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="36437-121">This is the preferred method.</span></span>

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

<span data-ttu-id="36437-122">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="36437-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="36437-123">Installation via direkt hämta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="36437-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="36437-124">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="36437-125">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="36437-126">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="36437-127">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="36437-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="36437-128">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="36437-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="36437-129">Installation via Paketdatabasen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="36437-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="36437-130">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="36437-131">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="36437-131">This is the preferred method.</span></span>

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

<span data-ttu-id="36437-132">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="36437-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="36437-133">Installation via direkt hämta - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="36437-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="36437-134">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` från den [Versioner][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="36437-135">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="36437-136">Observera att `dpkg -i` misslyckas med unmet beroenden; nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="36437-137">Avinstallationen - Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="36437-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="36437-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="36437-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="36437-139">Installation via Paketdatabasen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="36437-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="36437-140">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="36437-141">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="36437-141">This is the preferred method.</span></span>

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

<span data-ttu-id="36437-142">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="36437-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="36437-143">Installation via direkt hämta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="36437-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="36437-144">Hämta Debian-paket `powershell_6.0.2-1.debian.8_amd64.deb` från den [Versioner][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="36437-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="36437-145">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="36437-146">Observera att `dpkg -i` misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="36437-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="36437-147">Nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="36437-148">Avinstallationen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="36437-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="36437-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="36437-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="36437-150">Installation via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="36437-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="36437-151">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="36437-152">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="36437-152">This is the preferred method.</span></span>

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

<span data-ttu-id="36437-153">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="36437-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="36437-154">Installation via direkt hämta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="36437-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="36437-155">Hämta Debian-paket `powershell_6.0.2-1.debian.9_amd64.deb` från den [Versioner][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="36437-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="36437-156">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="36437-157">Observera att `dpkg -i` misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="36437-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="36437-158">Nästa kommando `apt-get install -f` matchar dessa och sedan Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="36437-159">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="36437-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="36437-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36437-160">CentOS 7</span></span>

> <span data-ttu-id="36437-161">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="36437-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="36437-162">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36437-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="36437-163">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="36437-164">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36437-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="36437-165">Installation via direkt hämta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36437-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="36437-166">Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sidan på CentOS dator.</span><span class="sxs-lookup"><span data-stu-id="36437-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="36437-167">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="36437-168">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="36437-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="36437-169">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36437-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="36437-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="36437-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="36437-172">Installationen via Paketdatabasen (rekommenderas) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="36437-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="36437-173">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="36437-174">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36437-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="36437-175">Installation via direkt hämta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="36437-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="36437-176">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sida på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="36437-177">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="36437-178">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="36437-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="36437-179">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="36437-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="36437-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="36437-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="36437-181">När du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="36437-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="36437-182">I det här fallet kontrollerar du att en kompatibel `libcurl` bibliotek finns genom att kontrollera att följande kommando visar den `libcurl4` paketet som installerade:</span><span class="sxs-lookup"><span data-stu-id="36437-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="36437-183">Välj den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="36437-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="36437-184">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="36437-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="36437-185">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="36437-186">Installation via direkt hämta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="36437-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="36437-187">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sida på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="36437-188">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="36437-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="36437-189">Avinstallationen - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="36437-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="36437-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="36437-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="36437-191">Installationen via Paketdatabasen (rekommenderas) - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="36437-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="36437-192">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="36437-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="36437-193">Installation via direkt hämta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="36437-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="36437-194">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [Versioner][] sidan på Fedora dator.</span><span class="sxs-lookup"><span data-stu-id="36437-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="36437-195">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="36437-196">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="36437-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="36437-197">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="36437-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="36437-198">Arkitektur Linux</span><span class="sxs-lookup"><span data-stu-id="36437-198">Arch Linux</span></span>

<span data-ttu-id="36437-199">PowerShell är tillgänglig från den [arkitektur Linux][] användaren databasen (AUR).</span><span class="sxs-lookup"><span data-stu-id="36437-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="36437-200">Det kan vara kompilerat med den [senaste märkta versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="36437-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="36437-201">Det kan sammanställas från den [senaste bekräftelse master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="36437-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="36437-202">Den kan installeras med hjälp av den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="36437-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="36437-203">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="36437-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="36437-204">Mer information om hur du installerar paket från AUR finns i [arkitektur Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller gemenskapen [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="36437-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arkitektur Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="36437-206">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="36437-206">Linux AppImage</span></span>

<span data-ttu-id="36437-207">Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.1-x86_64.AppImage` från den [Versioner][] sida på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="36437-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="36437-208">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="36437-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="36437-209">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="36437-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="36437-210">Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="36437-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="36437-211">Det här paketet är ett enda Binärvärde som fungerar oberoende av användarens Linux-distribution.</span><span class="sxs-lookup"><span data-stu-id="36437-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="36437-213">Kali</span><span class="sxs-lookup"><span data-stu-id="36437-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="36437-214">Installation</span><span class="sxs-lookup"><span data-stu-id="36437-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="36437-215">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.</span><span class="sxs-lookup"><span data-stu-id="36437-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="36437-216">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="36437-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="36437-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="36437-217">Raspbian</span></span>

<span data-ttu-id="36437-218">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="36437-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="36437-219">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och 3 Pi enheter som andra enheter som [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="36437-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="36437-220">Hämta [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta till din Pi.</span><span class="sxs-lookup"><span data-stu-id="36437-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="36437-221">Installation</span><span class="sxs-lookup"><span data-stu-id="36437-221">Installation</span></span>

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

<span data-ttu-id="36437-222">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binär</span><span class="sxs-lookup"><span data-stu-id="36437-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="36437-223">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="36437-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="36437-224">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="36437-224">Binary Archives</span></span>

<span data-ttu-id="36437-225">PowerShell binär `tar.gz` Arkiv som har angetts för Linux-plattformar för att aktivera avancerade distribueringsscenarier.</span><span class="sxs-lookup"><span data-stu-id="36437-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="36437-226">Beroenden</span><span class="sxs-lookup"><span data-stu-id="36437-226">Dependencies</span></span>

<span data-ttu-id="36437-227">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="36437-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="36437-228">Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.</span><span class="sxs-lookup"><span data-stu-id="36437-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="36437-229">Följande diagram visar .NET Core 2.0 beroenden som stöds officiellt i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="36437-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="36437-230">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="36437-230">OS</span></span>                 | <span data-ttu-id="36437-231">Beroenden</span><span class="sxs-lookup"><span data-stu-id="36437-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="36437-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="36437-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="36437-233">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="36437-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="36437-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="36437-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="36437-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="36437-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="36437-236">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="36437-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="36437-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="36437-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="36437-238">Ubuntu nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="36437-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="36437-239">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="36437-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="36437-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="36437-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="36437-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="36437-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="36437-242">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="36437-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="36437-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="36437-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="36437-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="36437-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="36437-245">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="36437-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="36437-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="36437-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="36437-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="36437-247">CentOS 7</span></span> <br> <span data-ttu-id="36437-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="36437-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="36437-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="36437-249">RHEL 7</span></span> <br> <span data-ttu-id="36437-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="36437-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="36437-251">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="36437-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="36437-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="36437-252">Fedora 27</span></span> <br> <span data-ttu-id="36437-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="36437-253">Fedora 28</span></span> | <span data-ttu-id="36437-254">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="36437-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="36437-255">Du måste installera de nödvändiga beroendena för målet OS i separata steg för att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="36437-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="36437-256">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="36437-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="36437-257">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="36437-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="36437-258">Linux</span><span class="sxs-lookup"><span data-stu-id="36437-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="36437-259">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="36437-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="36437-260">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="36437-260">Paths</span></span>

* <span data-ttu-id="36437-261">`$PSHOME` Är `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="36437-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="36437-262">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="36437-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="36437-263">Standardprofiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="36437-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="36437-264">Moduler som användare kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="36437-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="36437-265">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="36437-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="36437-266">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="36437-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="36437-267">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="36437-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="36437-268">Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="36437-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="36437-269">PowerShell respekterar den [XDG Base Directory specifikationen] [ xdg-bds] på Linux.</span><span class="sxs-lookup"><span data-stu-id="36437-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
