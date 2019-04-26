---
title: Installera PowerShell Core i Linux
description: Information om att installera PowerShell Core på olika Linux-distributioner
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086569"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="2b9ba-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="2b9ba-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="2b9ba-104">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [ openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], och [Båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="2b9ba-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="2b9ba-105">För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell Fäst paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="2b9ba-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="2b9ba-106">Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="2b9ba-107">Alla paket finns på vår GitHub [Versioner][] sidan.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="2b9ba-108">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="2b9ba-109">Installera förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="2b9ba-109">Installing Preview Releases</span></span>

<span data-ttu-id="2b9ba-110">När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="2b9ba-111">Installerar via direct hämtning ändras inte, än namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="2b9ba-112">Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="2b9ba-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="2b9ba-113">Distribution(s)</span></span>|<span data-ttu-id="2b9ba-114">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="2b9ba-114">Stable Command</span></span> | <span data-ttu-id="2b9ba-115">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="2b9ba-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="2b9ba-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="2b9ba-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="2b9ba-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="2b9ba-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="2b9ba-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="2b9ba-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="2b9ba-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="2b9ba-120">Installationen via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="2b9ba-121">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-122">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-122">This is the preferred method.</span></span>

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

<span data-ttu-id="2b9ba-123">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="2b9ba-124">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="2b9ba-125">Installationen via Direct hämtning - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="2b9ba-126">Ladda ned Debian-paket `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="2b9ba-127">från den [Versioner][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2b9ba-128">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2b9ba-129">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="2b9ba-130">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="2b9ba-131">Uninstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="2b9ba-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="2b9ba-133">Installationen via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="2b9ba-134">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-135">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-135">This is the preferred method.</span></span>

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

<span data-ttu-id="2b9ba-136">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="2b9ba-137">Installationen via Direct hämtning - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="2b9ba-138">Ladda ned Debian-paket `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="2b9ba-139">från den [Versioner][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2b9ba-140">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2b9ba-141">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="2b9ba-142">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="2b9ba-143">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="2b9ba-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="2b9ba-145">Installationen via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="2b9ba-146">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-147">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-147">This is the preferred method.</span></span>

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

<span data-ttu-id="2b9ba-148">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="2b9ba-149">Installationen via Direct hämtning - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="2b9ba-150">Ladda ned Debian-paket `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="2b9ba-151">från den [Versioner][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="2b9ba-152">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="2b9ba-153">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="2b9ba-154">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="2b9ba-155">Avinstallationen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="2b9ba-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="2b9ba-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="2b9ba-157">Eftersom 18.10 är en [tillfälliga versionen](https://www.ubuntu.com/about/release-cycle), det är bara [community stöds](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="2b9ba-158">Installera på 18.10 stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="2b9ba-159">Se [Fäst paketet] [ snap] fullständiga instruktioner;</span><span class="sxs-lookup"><span data-stu-id="2b9ba-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="2b9ba-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="2b9ba-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="2b9ba-161">Installationen via Paketdatabasen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="2b9ba-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="2b9ba-162">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-163">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-163">This is the preferred method.</span></span>

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

<span data-ttu-id="2b9ba-164">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="2b9ba-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="2b9ba-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="2b9ba-166">Installationen via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2b9ba-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="2b9ba-167">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-168">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-168">This is the preferred method.</span></span>

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

<span data-ttu-id="2b9ba-169">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="2b9ba-170">Installationen via Direct hämtning - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2b9ba-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="2b9ba-171">Ladda ned Debian-paket `powershell_6.2.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="2b9ba-172">från den [Versioner][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="2b9ba-173">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="2b9ba-174">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="2b9ba-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="2b9ba-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="2b9ba-176">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="2b9ba-177">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="2b9ba-178">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2b9ba-179">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="2b9ba-180">Installationen via Direct hämtning - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="2b9ba-181">Med hjälp av [CentOS 7][], ladda ned RPM-paket `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="2b9ba-182">från den [Versioner][] sidan på CentOS-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="2b9ba-183">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2b9ba-184">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="2b9ba-185">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2b9ba-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2b9ba-188">Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2b9ba-189">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="2b9ba-190">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2b9ba-191">Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="2b9ba-192">Ladda ned RPM-paket `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="2b9ba-193">från den [Versioner][] sidan på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="2b9ba-194">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2b9ba-195">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="2b9ba-196">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="2b9ba-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2b9ba-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="2b9ba-198">Installation - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2b9ba-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="2b9ba-199">Installation - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2b9ba-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="2b9ba-200">Avinstallationen - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2b9ba-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="2b9ba-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="2b9ba-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="2b9ba-202">Fedora 28 stöds bara i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="2b9ba-203">Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2b9ba-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2b9ba-204">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="2b9ba-205">Installationen via Direct hämtning - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2b9ba-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="2b9ba-206">Ladda ned RPM-paket `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="2b9ba-207">från den [Versioner][] sidan på Fedora-dator.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="2b9ba-208">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="2b9ba-209">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="2b9ba-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="2b9ba-210">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2b9ba-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="2b9ba-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="2b9ba-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="2b9ba-212">Stöd för arch är experimentella.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-212">Arch support is experimental.</span></span>

<span data-ttu-id="2b9ba-213">PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="2b9ba-214">Den kan sammanställas med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="2b9ba-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="2b9ba-215">Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]</span><span class="sxs-lookup"><span data-stu-id="2b9ba-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="2b9ba-216">Den kan installeras med den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="2b9ba-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="2b9ba-217">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="2b9ba-218">Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="2b9ba-220">Fäst paket</span><span class="sxs-lookup"><span data-stu-id="2b9ba-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="2b9ba-221">Hämta snapd</span><span class="sxs-lookup"><span data-stu-id="2b9ba-221">Getting snapd</span></span>

<span data-ttu-id="2b9ba-222">`snapd` krävs för att köra fäster.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="2b9ba-223">Använd [instruktionerna](https://docs.snapcraft.io/core/install) att kontrollera att du har `snapd` installerad.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="2b9ba-224">Installationen via snapin</span><span class="sxs-lookup"><span data-stu-id="2b9ba-224">Installation via Snap</span></span>

<span data-ttu-id="2b9ba-225">PowerShell Core för Linux, publiceras till den [snapin store](https://snapcraft.io/store) för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="2b9ba-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="2b9ba-226">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="2b9ba-227">Om du vill installera förhandsversionen kan du använda följande metod.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="2b9ba-228">När du installerar snapin uppgraderar automatiskt, men du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="2b9ba-229">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="2b9ba-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="2b9ba-230">eller</span><span class="sxs-lookup"><span data-stu-id="2b9ba-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="2b9ba-231">Kali</span><span class="sxs-lookup"><span data-stu-id="2b9ba-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="2b9ba-232">Installation - Kali</span><span class="sxs-lookup"><span data-stu-id="2b9ba-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="2b9ba-233">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="2b9ba-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="2b9ba-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="2b9ba-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="2b9ba-235">Stöd för Raspbian är experimentella.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="2b9ba-236">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="2b9ba-237">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="2b9ba-238">Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="2b9ba-239">Installation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2b9ba-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="2b9ba-240">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära</span><span class="sxs-lookup"><span data-stu-id="2b9ba-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="2b9ba-241">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="2b9ba-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="2b9ba-242">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="2b9ba-242">Binary Archives</span></span>

<span data-ttu-id="2b9ba-243">PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="2b9ba-244">Beroenden</span><span class="sxs-lookup"><span data-stu-id="2b9ba-244">Dependencies</span></span>

<span data-ttu-id="2b9ba-245">PowerShell skapar bärbar binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="2b9ba-246">Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="2b9ba-247">Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="2b9ba-248">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="2b9ba-248">OS</span></span>                 | <span data-ttu-id="2b9ba-249">Beroenden</span><span class="sxs-lookup"><span data-stu-id="2b9ba-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="2b9ba-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="2b9ba-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="2b9ba-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="2b9ba-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="2b9ba-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="2b9ba-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="2b9ba-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="2b9ba-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="2b9ba-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="2b9ba-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="2b9ba-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="2b9ba-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="2b9ba-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="2b9ba-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="2b9ba-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="2b9ba-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="2b9ba-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="2b9ba-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="2b9ba-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="2b9ba-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="2b9ba-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="2b9ba-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="2b9ba-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="2b9ba-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="2b9ba-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-268">CentOS 7</span></span> <br> <span data-ttu-id="2b9ba-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="2b9ba-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="2b9ba-270">RHEL 7</span></span> | <span data-ttu-id="2b9ba-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="2b9ba-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="2b9ba-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="2b9ba-272">openSUSE 42.3</span></span> | <span data-ttu-id="2b9ba-273">libcurl4 libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="2b9ba-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="2b9ba-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="2b9ba-274">openSUSE Leap 15</span></span> | <span data-ttu-id="2b9ba-275">libcurl4 libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="2b9ba-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="2b9ba-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="2b9ba-276">Fedora 27</span></span> <br> <span data-ttu-id="2b9ba-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="2b9ba-277">Fedora 28</span></span> | <span data-ttu-id="2b9ba-278">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="2b9ba-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="2b9ba-279">Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="2b9ba-280">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="2b9ba-281">Installation - binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="2b9ba-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="2b9ba-282">Linux</span><span class="sxs-lookup"><span data-stu-id="2b9ba-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="2b9ba-283">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="2b9ba-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="2b9ba-284">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="2b9ba-284">Paths</span></span>

* <span data-ttu-id="2b9ba-285">`$PSHOME` är `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="2b9ba-286">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="2b9ba-287">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="2b9ba-288">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2b9ba-289">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="2b9ba-290">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="2b9ba-291">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="2b9ba-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="2b9ba-292">Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="2b9ba-293">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="2b9ba-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[Versioner]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
