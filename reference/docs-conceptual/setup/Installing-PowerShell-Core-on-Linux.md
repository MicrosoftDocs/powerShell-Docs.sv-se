---
title: Installera PowerShell Core i Linux
description: Information om att installera PowerShell Core på olika Linux-distributioner
ms.date: 08/06/2018
ms.openlocfilehash: d60e1d5a89b6907b67c19b8cfcde969be156bd60
ms.sourcegitcommit: 6749f67c32e05999e10deb9d45f90f45ac21a599
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851297"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="96cd4-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="96cd4-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="96cd4-104">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="96cd4-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="96cd4-105">För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell Fäst paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="96cd4-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="96cd4-106">Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="96cd4-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="96cd4-107">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="96cd4-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="96cd4-108">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="96cd4-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="96cd4-109">Installera förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="96cd4-109">Installing Preview Releases</span></span>

<span data-ttu-id="96cd4-110">När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="96cd4-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="96cd4-111">Installerar via direct hämtning ändras inte, än namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="96cd4-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="96cd4-112">Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:</span><span class="sxs-lookup"><span data-stu-id="96cd4-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="96cd4-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="96cd4-113">Distribution(s)</span></span>|<span data-ttu-id="96cd4-114">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="96cd4-114">Stable Command</span></span> | <span data-ttu-id="96cd4-115">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="96cd4-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="96cd4-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="96cd4-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="96cd4-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="96cd4-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="96cd4-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="96cd4-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="96cd4-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="96cd4-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="96cd4-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="96cd4-121">Installationen via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="96cd4-122">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-123">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-123">This is the preferred method.</span></span>

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

<span data-ttu-id="96cd4-124">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="96cd4-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="96cd4-125">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="96cd4-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="96cd4-126">Installationen via Direct hämtning - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="96cd4-127">Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="96cd4-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="96cd4-128">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96cd4-129">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96cd4-130">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="96cd4-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96cd4-131">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96cd4-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="96cd4-132">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="96cd4-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="96cd4-134">Installationen via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="96cd4-135">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-136">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-136">This is the preferred method.</span></span>

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

<span data-ttu-id="96cd4-137">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96cd4-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="96cd4-138">Installationen via Direct hämtning - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="96cd4-139">Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="96cd4-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="96cd4-140">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96cd4-141">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96cd4-142">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="96cd4-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96cd4-143">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96cd4-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="96cd4-144">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="96cd4-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-146">Stöd för Ubuntu 18.04 har lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="96cd4-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="96cd4-147">Installationen via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="96cd4-148">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-149">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-149">This is the preferred method.</span></span>

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

<span data-ttu-id="96cd4-150">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96cd4-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="96cd4-151">Installationen via Direct hämtning - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="96cd4-152">Ladda ned Debian-paket `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="96cd4-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="96cd4-153">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="96cd4-154">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96cd4-155">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="96cd4-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96cd4-156">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96cd4-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="96cd4-157">Avinstallationen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="96cd4-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="96cd4-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-159">Stöd för Ubuntu 18.10 har lagts till efter `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="96cd4-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="96cd4-160">Eftersom 18.10 är en daglig version, är det bara community stöds.</span><span class="sxs-lookup"><span data-stu-id="96cd4-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="96cd4-161">Installera på 18.10 stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="96cd4-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="96cd4-162">Se [Fäst paketet] [ snap] fullständiga instruktioner;</span><span class="sxs-lookup"><span data-stu-id="96cd4-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="96cd4-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="96cd4-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="96cd4-164">Installationen via Paketdatabasen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="96cd4-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="96cd4-165">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-166">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-166">This is the preferred method.</span></span>

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

<span data-ttu-id="96cd4-167">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96cd4-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="96cd4-168">Installationen via Direct hämtning – Debian 8</span><span class="sxs-lookup"><span data-stu-id="96cd4-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="96cd4-169">Ladda ned Debian-paket `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="96cd4-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="96cd4-170">från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="96cd4-171">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="96cd4-172">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="96cd4-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="96cd4-173">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96cd4-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="96cd4-174">Avinstallationen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="96cd4-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="96cd4-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="96cd4-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="96cd4-176">Installationen via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96cd4-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="96cd4-177">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-178">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-178">This is the preferred method.</span></span>

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

<span data-ttu-id="96cd4-179">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="96cd4-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="96cd4-180">Installationen via Direct hämtning - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96cd4-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="96cd4-181">Ladda ned Debian-paket `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="96cd4-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="96cd4-182">från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="96cd4-183">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="96cd4-184">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="96cd4-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="96cd4-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-186">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="96cd4-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="96cd4-187">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="96cd4-188">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96cd4-189">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96cd4-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="96cd4-190">Installationen via Direct hämtning - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="96cd4-191">Med hjälp av [CentOS 7][], ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="96cd4-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="96cd4-192">från den [släpper][] sidan på CentOS-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="96cd4-193">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96cd4-194">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96cd4-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="96cd4-195">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96cd4-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96cd4-198">Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="96cd4-199">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="96cd4-200">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96cd4-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96cd4-201">Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="96cd4-202">Ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="96cd4-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="96cd4-203">från den [släpper][] sidan på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="96cd4-204">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96cd4-205">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96cd4-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="96cd4-206">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="96cd4-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="96cd4-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="96cd4-208">När du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="96cd4-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="96cd4-209">I det här fallet kontrollerar du att en kompatibel `libcurl` biblioteket finns genom att kontrollera att följande kommando visar den `libcurl4` paketera som installerade:</span><span class="sxs-lookup"><span data-stu-id="96cd4-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="96cd4-210">Välj sedan den `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="96cd4-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="96cd4-211">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="96cd4-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="96cd4-212">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="96cd4-213">Installationen via Direct hämtning - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="96cd4-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="96cd4-214">Ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96cd4-215">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96cd4-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="96cd4-216">Avinstallationen - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="96cd4-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="96cd4-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="96cd4-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-218">Fedora 28 stöds bara i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="96cd4-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="96cd4-219">Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96cd4-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="96cd4-220">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="96cd4-221">Installationen via Direct hämtning - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96cd4-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="96cd4-222">Ladda ned RPM-paket `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="96cd4-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="96cd4-223">från den [släpper][] sidan på Fedora-dator.</span><span class="sxs-lookup"><span data-stu-id="96cd4-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="96cd4-224">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="96cd4-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="96cd4-225">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="96cd4-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="96cd4-226">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96cd4-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="96cd4-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="96cd4-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-228">Stöd för arch är experimentella.</span><span class="sxs-lookup"><span data-stu-id="96cd4-228">Arch support is experimental.</span></span>

<span data-ttu-id="96cd4-229">PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).</span><span class="sxs-lookup"><span data-stu-id="96cd4-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="96cd4-230">Den kan sammanställas med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="96cd4-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="96cd4-231">Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]</span><span class="sxs-lookup"><span data-stu-id="96cd4-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="96cd4-232">Den kan installeras med den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="96cd4-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="96cd4-233">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="96cd4-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="96cd4-234">Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="96cd4-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="96cd4-236">Fäst paket</span><span class="sxs-lookup"><span data-stu-id="96cd4-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="96cd4-237">Hämta snapd</span><span class="sxs-lookup"><span data-stu-id="96cd4-237">Getting snapd</span></span>

<span data-ttu-id="96cd4-238">`snapd` krävs för att köra fäster.</span><span class="sxs-lookup"><span data-stu-id="96cd4-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="96cd4-239">Använd [instruktionerna](https://docs.snapcraft.io/core/install) att kontrollera att du har `snapd` installerad.</span><span class="sxs-lookup"><span data-stu-id="96cd4-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="96cd4-240">Installationen via snapin</span><span class="sxs-lookup"><span data-stu-id="96cd4-240">Installation via Snap</span></span>

<span data-ttu-id="96cd4-241">PowerShell Core för Linux, publiceras till den [snapin store](https://snapcraft.io/store) för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="96cd4-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="96cd4-242">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="96cd4-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="96cd4-243">När du installerar snapin uppgraderar automatiskt, men du kan utlösa en uppgradering med `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="96cd4-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="96cd4-244">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="96cd4-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="96cd4-245">Kali</span><span class="sxs-lookup"><span data-stu-id="96cd4-245">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="96cd4-246">Installation</span><span class="sxs-lookup"><span data-stu-id="96cd4-246">Installation</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="96cd4-247">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="96cd4-247">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="96cd4-248">Raspbian</span><span class="sxs-lookup"><span data-stu-id="96cd4-248">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="96cd4-249">Stöd för Raspbian är experimentella.</span><span class="sxs-lookup"><span data-stu-id="96cd4-249">Raspbian support is experimental.</span></span>

<span data-ttu-id="96cd4-250">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="96cd4-250">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="96cd4-251">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="96cd4-251">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="96cd4-252">Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.</span><span class="sxs-lookup"><span data-stu-id="96cd4-252">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="96cd4-253">Installation</span><span class="sxs-lookup"><span data-stu-id="96cd4-253">Installation</span></span>

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

<span data-ttu-id="96cd4-254">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära</span><span class="sxs-lookup"><span data-stu-id="96cd4-254">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="96cd4-255">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="96cd4-255">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="96cd4-256">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="96cd4-256">Binary Archives</span></span>

<span data-ttu-id="96cd4-257">PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="96cd4-257">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="96cd4-258">Beroenden</span><span class="sxs-lookup"><span data-stu-id="96cd4-258">Dependencies</span></span>

<span data-ttu-id="96cd4-259">PowerShell skapar bärbar binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="96cd4-259">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="96cd4-260">Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="96cd4-260">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="96cd4-261">Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="96cd4-261">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="96cd4-262">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="96cd4-262">OS</span></span>                 | <span data-ttu-id="96cd4-263">Beroenden</span><span class="sxs-lookup"><span data-stu-id="96cd4-263">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="96cd4-264">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-264">Ubuntu 14.04</span></span>       | <span data-ttu-id="96cd4-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-265">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="96cd4-266">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="96cd4-267">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-267">Ubuntu 16.04</span></span>       | <span data-ttu-id="96cd4-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-268">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="96cd4-269">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="96cd4-270">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="96cd4-270">Ubuntu 17.10</span></span>       | <span data-ttu-id="96cd4-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-271">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="96cd4-272">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="96cd4-273">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="96cd4-273">Ubuntu 18.04</span></span>       | <span data-ttu-id="96cd4-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-274">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="96cd4-275">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="96cd4-276">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="96cd4-276">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="96cd4-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-277">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="96cd4-278">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="96cd4-279">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="96cd4-279">Debian 9 (Stretch)</span></span> | <span data-ttu-id="96cd4-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="96cd4-280">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="96cd4-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="96cd4-281">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="96cd4-282">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-282">CentOS 7</span></span> <br> <span data-ttu-id="96cd4-283">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-283">Oracle Linux 7</span></span> <br> <span data-ttu-id="96cd4-284">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="96cd4-284">RHEL 7</span></span> <br> <span data-ttu-id="96cd4-285">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="96cd4-285">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="96cd4-286">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="96cd4-286">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="96cd4-287">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="96cd4-287">Fedora 27</span></span> <br> <span data-ttu-id="96cd4-288">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="96cd4-288">Fedora 28</span></span> | <span data-ttu-id="96cd4-289">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="96cd4-289">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="96cd4-290">Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="96cd4-290">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="96cd4-291">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="96cd4-291">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="96cd4-292">Installation - binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="96cd4-292">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="96cd4-293">Linux</span><span class="sxs-lookup"><span data-stu-id="96cd4-293">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="96cd4-294">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="96cd4-294">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="96cd4-295">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="96cd4-295">Paths</span></span>

* <span data-ttu-id="96cd4-296">`$PSHOME` är `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="96cd4-296">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="96cd4-297">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="96cd4-297">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="96cd4-298">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="96cd4-298">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="96cd4-299">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="96cd4-299">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="96cd4-300">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="96cd4-300">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="96cd4-301">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="96cd4-301">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="96cd4-302">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="96cd4-302">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="96cd4-303">Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="96cd4-303">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="96cd4-304">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="96cd4-304">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
