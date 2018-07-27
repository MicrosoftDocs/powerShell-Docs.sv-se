# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="16a59-101">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="16a59-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="16a59-102">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10] [ u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="16a59-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="16a59-103">För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="16a59-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="16a59-104">Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="16a59-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="16a59-105">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="16a59-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="16a59-106">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="16a59-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="16a59-107">Installera förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="16a59-107">Installing Preview Releases</span></span>

<span data-ttu-id="16a59-108">När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="16a59-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="16a59-109">Installerar via direct hämtning ändras inte, än namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="16a59-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="16a59-110">Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:</span><span class="sxs-lookup"><span data-stu-id="16a59-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="16a59-111">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="16a59-111">Distribution(s)</span></span>|<span data-ttu-id="16a59-112">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="16a59-112">Stable Command</span></span> | <span data-ttu-id="16a59-113">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="16a59-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="16a59-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="16a59-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="16a59-115">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="16a59-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="16a59-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="16a59-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="16a59-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="16a59-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="16a59-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16a59-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="16a59-119">Installationen via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16a59-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="16a59-120">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-121">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-121">This is the preferred method.</span></span>

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

<span data-ttu-id="16a59-122">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="16a59-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="16a59-123">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="16a59-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="16a59-124">Installationen via Direct hämtning - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16a59-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="16a59-125">Ladda ned Debian-paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16a59-126">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16a59-127">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="16a59-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16a59-128">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="16a59-129">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16a59-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="16a59-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16a59-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="16a59-131">Installationen via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16a59-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="16a59-132">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-133">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-133">This is the preferred method.</span></span>

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

<span data-ttu-id="16a59-134">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="16a59-135">Installationen via Direct hämtning - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16a59-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="16a59-136">Ladda ned Debian-paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16a59-137">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16a59-138">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="16a59-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16a59-139">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="16a59-140">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16a59-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="16a59-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16a59-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-142">Stöd för Ubuntu nr 17.04 från har lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="16a59-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="16a59-143">Installationen via Paketdatabasen - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16a59-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="16a59-144">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-145">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-145">This is the preferred method.</span></span>

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

<span data-ttu-id="16a59-146">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="16a59-147">Installationen via Direct hämtning - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16a59-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="16a59-148">Ladda ned Debian-paket `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16a59-149">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16a59-150">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="16a59-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16a59-151">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="16a59-152">Avinstallationen - Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16a59-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="16a59-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16a59-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-154">Stöd för Ubuntu 18.04 har lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="16a59-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="16a59-155">Installationen via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16a59-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="16a59-156">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-157">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="16a59-158">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="16a59-159">Installationen via Direct hämtning - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16a59-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="16a59-160">Ladda ned Debian-paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="16a59-161">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16a59-162">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="16a59-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16a59-163">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="16a59-164">Avinstallationen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16a59-164">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="16a59-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="16a59-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="16a59-166">Installationen via Paketdatabasen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="16a59-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="16a59-167">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-168">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-168">This is the preferred method.</span></span>

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

<span data-ttu-id="16a59-169">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="16a59-170">Installationen via Direct hämtning – Debian 8</span><span class="sxs-lookup"><span data-stu-id="16a59-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="16a59-171">Ladda ned Debian-paket `powershell_6.0.2-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="16a59-172">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="16a59-173">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="16a59-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="16a59-174">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="16a59-175">Avinstallationen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="16a59-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="16a59-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="16a59-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="16a59-177">Installationen via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16a59-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="16a59-178">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="16a59-179">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="16a59-179">This is the preferred method.</span></span>

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

<span data-ttu-id="16a59-180">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="16a59-181">Installationen via Direct hämtning - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16a59-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="16a59-182">Ladda ned Debian-paket `powershell_6.0.2-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="16a59-183">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="16a59-184">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="16a59-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="16a59-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16a59-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-186">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="16a59-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="16a59-187">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16a59-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="16a59-188">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="16a59-189">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16a59-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="16a59-190">Installationen via Direct hämtning - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16a59-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="16a59-191">Med hjälp av [CentOS 7][], hämtningspaketet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="16a59-192">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16a59-193">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="16a59-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="16a59-194">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16a59-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16a59-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16a59-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16a59-197">Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16a59-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="16a59-198">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="16a59-199">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16a59-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16a59-200">Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16a59-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="16a59-201">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="16a59-202">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16a59-203">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="16a59-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="16a59-204">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="16a59-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="16a59-205">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16a59-205">OpenSUSE 42.3</span></span>

<span data-ttu-id="16a59-206">När du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="16a59-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="16a59-207">I det här fallet kontrollerar du att en kompatibel `libcurl` biblioteket finns genom att kontrollera att följande kommando visar den `libcurl4` paketera som installerade:</span><span class="sxs-lookup"><span data-stu-id="16a59-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="16a59-208">Välj sedan den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="16a59-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="16a59-209">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16a59-209">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="16a59-210">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="16a59-211">Installationen via Direct hämtning - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16a59-211">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="16a59-212">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16a59-213">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="16a59-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="16a59-214">Avinstallationen - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16a59-214">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="16a59-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="16a59-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-216">Fedora 28 stöds bara i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="16a59-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="16a59-217">Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16a59-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="16a59-218">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="16a59-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="16a59-219">Installationen via Direct hämtning - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16a59-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="16a59-220">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="16a59-221">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="16a59-222">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="16a59-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="16a59-223">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16a59-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="16a59-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="16a59-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-225">Stöd för arch är experimentella.</span><span class="sxs-lookup"><span data-stu-id="16a59-225">Arch support is experimental.</span></span>

<span data-ttu-id="16a59-226">PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).</span><span class="sxs-lookup"><span data-stu-id="16a59-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="16a59-227">Den kan sammanställas med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="16a59-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="16a59-228">Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]</span><span class="sxs-lookup"><span data-stu-id="16a59-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="16a59-229">Den kan installeras med den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="16a59-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="16a59-230">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="16a59-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="16a59-231">Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="16a59-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="16a59-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="16a59-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-234">AppImage support är experimentella</span><span class="sxs-lookup"><span data-stu-id="16a59-234">AppImage support is experimental</span></span>

<span data-ttu-id="16a59-235">Med hjälp av en nyligen Linux-distribution, ladda ned AppImage `powershell-6.0.1-x86_64.AppImage` från den [släpper][] sidan på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="16a59-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="16a59-236">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="16a59-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="16a59-237">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="16a59-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="16a59-238">Det är en bärbar program som samlar PowerShell och dess beroenden (inklusive .NET Core systemberoenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="16a59-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="16a59-239">Det här paketet är ett enda Binärvärde som fungerar oberoende av användarens Linux-distribution.</span><span class="sxs-lookup"><span data-stu-id="16a59-239">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="16a59-241">Kali</span><span class="sxs-lookup"><span data-stu-id="16a59-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-242">Stöd för kali är experimentella.</span><span class="sxs-lookup"><span data-stu-id="16a59-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="16a59-243">Installation</span><span class="sxs-lookup"><span data-stu-id="16a59-243">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="16a59-244">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera den</span><span class="sxs-lookup"><span data-stu-id="16a59-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="16a59-245">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="16a59-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="16a59-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="16a59-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="16a59-247">Stöd för Raspbian är experimentella.</span><span class="sxs-lookup"><span data-stu-id="16a59-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="16a59-248">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="16a59-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="16a59-249">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="16a59-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="16a59-250">Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.</span><span class="sxs-lookup"><span data-stu-id="16a59-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="16a59-251">Installation</span><span class="sxs-lookup"><span data-stu-id="16a59-251">Installation</span></span>

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

<span data-ttu-id="16a59-252">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära</span><span class="sxs-lookup"><span data-stu-id="16a59-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="16a59-253">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="16a59-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="16a59-254">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="16a59-254">Binary Archives</span></span>

<span data-ttu-id="16a59-255">PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="16a59-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="16a59-256">Beroenden</span><span class="sxs-lookup"><span data-stu-id="16a59-256">Dependencies</span></span>

<span data-ttu-id="16a59-257">PowerShell skapar bärbar binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="16a59-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="16a59-258">Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="16a59-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="16a59-259">Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="16a59-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="16a59-260">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="16a59-260">OS</span></span>                 | <span data-ttu-id="16a59-261">Beroenden</span><span class="sxs-lookup"><span data-stu-id="16a59-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="16a59-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="16a59-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="16a59-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="16a59-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="16a59-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="16a59-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="16a59-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="16a59-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="16a59-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="16a59-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="16a59-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="16a59-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="16a59-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="16a59-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="16a59-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="16a59-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="16a59-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="16a59-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="16a59-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="16a59-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="16a59-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="16a59-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="16a59-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="16a59-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="16a59-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="16a59-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="16a59-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="16a59-280">CentOS 7</span></span> <br> <span data-ttu-id="16a59-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="16a59-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="16a59-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="16a59-282">RHEL 7</span></span> <br> <span data-ttu-id="16a59-283">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="16a59-283">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="16a59-284">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="16a59-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="16a59-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="16a59-285">Fedora 27</span></span> <br> <span data-ttu-id="16a59-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="16a59-286">Fedora 28</span></span> | <span data-ttu-id="16a59-287">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="16a59-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="16a59-288">Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="16a59-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="16a59-289">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="16a59-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="16a59-290">Installation - binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="16a59-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="16a59-291">Linux</span><span class="sxs-lookup"><span data-stu-id="16a59-291">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="16a59-292">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="16a59-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="16a59-293">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="16a59-293">Paths</span></span>

* <span data-ttu-id="16a59-294">`$PSHOME` är `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="16a59-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="16a59-295">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="16a59-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="16a59-296">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="16a59-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="16a59-297">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="16a59-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="16a59-298">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="16a59-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="16a59-299">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="16a59-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="16a59-300">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="16a59-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="16a59-301">Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="16a59-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="16a59-302">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="16a59-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
