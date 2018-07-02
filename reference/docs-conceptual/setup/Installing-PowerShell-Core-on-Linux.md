# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="96eb1-101">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="96eb1-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="96eb1-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="96eb1-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="96eb1-103">Linux-distributioner som inte stöds officiellt, kan du använda den [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="96eb1-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="96eb1-104">Du kan också försöka distribuera PowerShell binärfiler direkt med Linux [ `tar.gz` Arkiv][tar], men måste du ställa in de nödvändiga beroenden baserat på enhetens operativsystem i separata steg.</span><span class="sxs-lookup"><span data-stu-id="96eb1-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="96eb1-105">Alla paket är tillgängliga på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="96eb1-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="96eb1-106">När paketet har installerats kör `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="96eb1-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="96eb1-107">Installera förhandsvisningarna</span><span class="sxs-lookup"><span data-stu-id="96eb1-107">Installing Preview Releases</span></span>

<span data-ttu-id="96eb1-108">När du installerar ett PowerShell Core förhandsversionen för Linux via en Paketdatabasen paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="96eb1-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="96eb1-109">Installerar via direkt hämtning ändras inte, än filnamnet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="96eb1-110">Här är en tabell med kommandona för att installera stabilt och preview-paket med hjälp av de olika paket cheferna:</span><span class="sxs-lookup"><span data-stu-id="96eb1-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="96eb1-111">Distrobution(s)</span><span class="sxs-lookup"><span data-stu-id="96eb1-111">Distrobution(s)</span></span>|<span data-ttu-id="96eb1-112">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="96eb1-112">Stable Command</span></span> | <span data-ttu-id="96eb1-113">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="96eb1-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="96eb1-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="96eb1-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="96eb1-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="96eb1-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="96eb1-116">openSUSE</span><span class="sxs-lookup"><span data-stu-id="96eb1-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="96eb1-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="96eb1-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="96eb1-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="96eb1-119">Installation via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="96eb1-120">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-121">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-121">This is the preferred method.</span></span>

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

<span data-ttu-id="96eb1-122">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="96eb1-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="96eb1-123">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="96eb1-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="96eb1-124">Installation via direkt hämta - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="96eb1-125">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96eb1-126">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96eb1-127">Den `dpkg -i` kommandot misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="96eb1-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96eb1-128">Nästa kommando `apt-get install -f` löser dessa problem och slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="96eb1-129">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="96eb1-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="96eb1-131">Installation via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="96eb1-132">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-133">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-133">This is the preferred method.</span></span>

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

<span data-ttu-id="96eb1-134">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="96eb1-135">Installation via direkt hämta - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="96eb1-136">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96eb1-137">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96eb1-138">Den `dpkg -i` kommandot misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="96eb1-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96eb1-139">Nästa kommando `apt-get install -f` löser dessa problem och slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="96eb1-140">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="96eb1-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-142">Stöd för Ubuntu nr 17.04 från lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="96eb1-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="96eb1-143">Installation via Paketdatabasen - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="96eb1-144">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-145">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96eb1-146">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="96eb1-147">Installation via direkt hämta - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="96eb1-148">Hämta Debian-paket `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96eb1-149">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96eb1-150">Den `dpkg -i` kommandot misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="96eb1-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96eb1-151">Nästa kommando `apt-get install -f` löser dessa problem och slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="96eb1-152">Avinstallationen - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="96eb1-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-154">Stöd för Ubuntu 18.04 lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="96eb1-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="96eb1-155">Installation via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="96eb1-156">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-157">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96eb1-158">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="96eb1-159">Installation via direkt hämta - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="96eb1-160">Hämta Debian-paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` från den [släpper][] sida på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96eb1-161">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96eb1-162">Den `dpkg -i` kommandot misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="96eb1-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96eb1-163">Nästa kommando `apt-get install -f` löser dessa problem och slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="96eb1-164">Avinstallationen - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="96eb1-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="96eb1-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="96eb1-166">Installation via Paketdatabasen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="96eb1-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="96eb1-167">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-168">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-168">This is the preferred method.</span></span>

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

<span data-ttu-id="96eb1-169">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="96eb1-170">Installation via direkt hämta - Debian 8</span><span class="sxs-lookup"><span data-stu-id="96eb1-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="96eb1-171">Hämta Debian-paket `powershell_6.0.2-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="96eb1-172">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96eb1-173">Den `dpkg -i` kommandot misslyckas med unmet beroenden.</span><span class="sxs-lookup"><span data-stu-id="96eb1-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96eb1-174">Nästa kommando `apt-get install -f` löser dessa problem och slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="96eb1-175">Avinstallationen - Debian 8</span><span class="sxs-lookup"><span data-stu-id="96eb1-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="96eb1-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="96eb1-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="96eb1-177">Installation via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96eb1-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="96eb1-178">PowerShell-kärna för Linux, publiceras till paketet databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96eb1-179">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96eb1-179">This is the preferred method.</span></span>

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

<span data-ttu-id="96eb1-180">När du har registrerat en gång Microsoft-databasen som superanvändare, därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="96eb1-181">Installation via direkt hämta - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96eb1-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="96eb1-182">Hämta Debian-paket `powershell_6.0.2-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="96eb1-183">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="96eb1-184">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96eb1-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="96eb1-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-186">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="96eb1-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="96eb1-187">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="96eb1-188">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96eb1-189">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96eb1-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="96eb1-190">Installation via direkt hämta - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="96eb1-191">Med hjälp av [CentOS 7][], hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="96eb1-192">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96eb1-193">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96eb1-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="96eb1-194">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96eb1-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96eb1-197">Installationen via Paketdatabasen (rekommenderas) - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="96eb1-198">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96eb1-199">När du har registrerat en gång Microsoft-databasen som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96eb1-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96eb1-200">Installation via direkt hämta - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="96eb1-201">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sida på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="96eb1-202">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96eb1-203">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96eb1-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96eb1-204">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="96eb1-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="96eb1-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="96eb1-206">När du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="96eb1-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="96eb1-207">I det här fallet kontrollerar du att en kompatibel `libcurl` bibliotek finns genom att kontrollera att följande kommando visar den `libcurl4` paketet som installerade:</span><span class="sxs-lookup"><span data-stu-id="96eb1-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="96eb1-208">Välj den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96eb1-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="96eb1-209">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="96eb1-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="96eb1-210">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="96eb1-211">Installation via direkt hämta - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="96eb1-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="96eb1-212">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sida på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96eb1-213">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96eb1-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="96eb1-214">Avinstallationen - OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="96eb1-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="96eb1-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="96eb1-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-216">Fedora 28 stöds endast i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="96eb1-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="96eb1-217">Installationen via Paketdatabasen (rekommenderas) - Fedora 27 Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96eb1-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="96eb1-218">PowerShell-kärna för Linux publiceras till den officiella Microsoft databaser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96eb1-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="96eb1-219">Installation via direkt hämta - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96eb1-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="96eb1-220">Hämta RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="96eb1-221">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96eb1-222">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96eb1-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="96eb1-223">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96eb1-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="96eb1-224">Arkitektur Linux</span><span class="sxs-lookup"><span data-stu-id="96eb1-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-225">Stöd för arkitektur är experiment.</span><span class="sxs-lookup"><span data-stu-id="96eb1-225">Arch support is experimental.</span></span>

<span data-ttu-id="96eb1-226">PowerShell är tillgänglig från den [arkitektur Linux][] användaren databasen (AUR).</span><span class="sxs-lookup"><span data-stu-id="96eb1-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="96eb1-227">Det kan vara kompilerat med den [senaste märkta versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="96eb1-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="96eb1-228">Det kan sammanställas från den [senaste bekräftelse master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="96eb1-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="96eb1-229">Den kan installeras med hjälp av den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="96eb1-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="96eb1-230">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="96eb1-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="96eb1-231">Mer information om hur du installerar paket från AUR finns i [arkitektur Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller gemenskapen [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="96eb1-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arkitektur Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="96eb1-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="96eb1-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-234">Stöd för AppImage är experiment</span><span class="sxs-lookup"><span data-stu-id="96eb1-234">AppImage support is experimental</span></span>

<span data-ttu-id="96eb1-235">Med hjälp av en senaste Linux-distribution, ladda ned AppImage `powershell-6.0.1-x86_64.AppImage` från den [släpper][] sida på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="96eb1-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="96eb1-236">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96eb1-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="96eb1-237">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="96eb1-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="96eb1-238">Det är en bärbar program som paketerar PowerShell och dess beroenden (inklusive .NET Core system beroenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="96eb1-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="96eb1-239">Det här paketet är ett enda Binärvärde som fungerar oberoende av användarens Linux-distribution.</span><span class="sxs-lookup"><span data-stu-id="96eb1-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="96eb1-241">Kali</span><span class="sxs-lookup"><span data-stu-id="96eb1-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-242">Stöd för kali är experiment.</span><span class="sxs-lookup"><span data-stu-id="96eb1-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="96eb1-243">Installation</span><span class="sxs-lookup"><span data-stu-id="96eb1-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="96eb1-244">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera det.</span><span class="sxs-lookup"><span data-stu-id="96eb1-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="96eb1-245">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="96eb1-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="96eb1-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="96eb1-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="96eb1-247">Stöd för Raspbian är experiment.</span><span class="sxs-lookup"><span data-stu-id="96eb1-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="96eb1-248">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="96eb1-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="96eb1-249">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och 3 Pi enheter som andra enheter som [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="96eb1-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="96eb1-250">Hämta [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta till din Pi.</span><span class="sxs-lookup"><span data-stu-id="96eb1-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="96eb1-251">Installation</span><span class="sxs-lookup"><span data-stu-id="96eb1-251">Installation</span></span>

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

<span data-ttu-id="96eb1-252">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binär</span><span class="sxs-lookup"><span data-stu-id="96eb1-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="96eb1-253">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="96eb1-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="96eb1-254">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="96eb1-254">Binary Archives</span></span>

<span data-ttu-id="96eb1-255">PowerShell binär `tar.gz` Arkiv som har angetts för Linux-plattformar för att aktivera avancerade distribueringsscenarier.</span><span class="sxs-lookup"><span data-stu-id="96eb1-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="96eb1-256">Beroenden</span><span class="sxs-lookup"><span data-stu-id="96eb1-256">Dependencies</span></span>

<span data-ttu-id="96eb1-257">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="96eb1-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="96eb1-258">Men .NET Core runtime kräver olika beroenden på olika distributioner och därför PowerShell har samma funktion.</span><span class="sxs-lookup"><span data-stu-id="96eb1-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="96eb1-259">Följande diagram visar .NET Core 2.0 beroenden som stöds officiellt i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="96eb1-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="96eb1-260">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="96eb1-260">OS</span></span>                 | <span data-ttu-id="96eb1-261">Beroenden</span><span class="sxs-lookup"><span data-stu-id="96eb1-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="96eb1-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="96eb1-263">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="96eb1-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="96eb1-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="96eb1-266">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="96eb1-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="96eb1-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96eb1-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="96eb1-269">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="96eb1-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="96eb1-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96eb1-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="96eb1-272">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="96eb1-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="96eb1-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="96eb1-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="96eb1-275">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="96eb1-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="96eb1-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="96eb1-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="96eb1-278">libc6 ust0-libgcc1, libgssapi-krb5-2, liblttng, libstdc ++ 6</span><span class="sxs-lookup"><span data-stu-id="96eb1-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96eb1-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="96eb1-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="96eb1-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-280">CentOS 7</span></span> <br> <span data-ttu-id="96eb1-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="96eb1-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="96eb1-282">RHEL 7</span></span> <br> <span data-ttu-id="96eb1-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="96eb1-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="96eb1-284">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="96eb1-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="96eb1-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="96eb1-285">Fedora 27</span></span> <br> <span data-ttu-id="96eb1-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96eb1-286">Fedora 28</span></span> | <span data-ttu-id="96eb1-287">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="96eb1-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="96eb1-288">Du måste installera de nödvändiga beroendena för målet OS i separata steg för att distribuera PowerShell binärfiler på Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="96eb1-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="96eb1-289">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="96eb1-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="96eb1-290">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="96eb1-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="96eb1-291">Linux</span><span class="sxs-lookup"><span data-stu-id="96eb1-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="96eb1-292">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="96eb1-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="96eb1-293">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="96eb1-293">Paths</span></span>

* <span data-ttu-id="96eb1-294">`$PSHOME` är `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="96eb1-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="96eb1-295">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="96eb1-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="96eb1-296">Standardprofiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="96eb1-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="96eb1-297">Moduler som användare kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="96eb1-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="96eb1-298">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="96eb1-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="96eb1-299">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="96eb1-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="96eb1-300">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="96eb1-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="96eb1-301">Profilerna respektera PowerShells per värd konfiguration så värd-specifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="96eb1-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="96eb1-302">PowerShell respekterar den [XDG Base Directory specifikationen] [ xdg-bds] på Linux.</span><span class="sxs-lookup"><span data-stu-id="96eb1-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
