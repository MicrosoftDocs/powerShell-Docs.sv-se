---
title: Installera PowerShell Core i Linux
description: Information om hur du installerar PowerShell Core på olika Linux-distributioner
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372197"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="9b5d5-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="9b5d5-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="9b5d5-104">Stöder [Ubuntu 16,04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18,10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE skottår 15][opensuse] , [Fedora 27][fedora], [Fedora 28][Fedora]och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="9b5d5-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9],
 [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="9b5d5-105">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="9b5d5-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="9b5d5-106">Du kan också prova att distribuera PowerShell-binärfiler direkt med [ `tar.gz` ][tar]Linux-arkivet, men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="9b5d5-107">Alla paket är tillgängliga på vår GitHub [releases][] sida.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="9b5d5-108">När paketet har installerats kör `pwsh` du från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-108">After the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="9b5d5-109">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="9b5d5-109">Installing Preview Releases</span></span>

<span data-ttu-id="9b5d5-110">När du installerar en PowerShell Core Preview-version för Linux via en paket lagrings plats ändras paket `powershell` namnet `powershell-preview`från till.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="9b5d5-111">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="9b5d5-112">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="9b5d5-113">Distribution (er)</span><span class="sxs-lookup"><span data-stu-id="9b5d5-113">Distribution(s)</span></span>|<span data-ttu-id="9b5d5-114">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="9b5d5-114">Stable Command</span></span> | <span data-ttu-id="9b5d5-115">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="9b5d5-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="9b5d5-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="9b5d5-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="9b5d5-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="9b5d5-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="9b5d5-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="9b5d5-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="9b5d5-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="9b5d5-120">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="9b5d5-121">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9b5d5-122">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9b5d5-123">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-124">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="9b5d5-125">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="9b5d5-126">Ladda ned Debian- `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9b5d5-127">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b5d5-128">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="9b5d5-129">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="9b5d5-130">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="9b5d5-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="9b5d5-132">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="9b5d5-133">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9b5d5-134">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9b5d5-135">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-136">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="9b5d5-137">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="9b5d5-138">Ladda ned Debian- `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9b5d5-139">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9b5d5-140">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="9b5d5-141">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="9b5d5-142">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="9b5d5-143">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="9b5d5-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="9b5d5-144">Eftersom 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle)stöds den bara av [communityn](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="9b5d5-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="9b5d5-145">Installation på 18,10 stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="9b5d5-146">Se [snapin-paket][snap] för fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="9b5d5-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b5d5-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="9b5d5-148">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="9b5d5-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="9b5d5-149">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9b5d5-150">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-150">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9b5d5-151">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-152">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="9b5d5-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b5d5-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="9b5d5-154">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b5d5-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="9b5d5-155">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9b5d5-156">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-156">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9b5d5-157">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-158">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="9b5d5-159">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b5d5-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="9b5d5-160">Ladda ned Debian- `powershell_6.2.0-1.debian.9_amd64.deb` paketet från sidan [releases][] på Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="9b5d5-161">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="9b5d5-162">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="9b5d5-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="9b5d5-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="9b5d5-164">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="9b5d5-165">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="9b5d5-166">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9b5d5-167">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-168">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="9b5d5-169">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="9b5d5-170">Med [CentOS 7][]laddar du ned rpm- `powershell-6.2.0-1.rhel.7.x86_64.rpm` paketet från sidan [releases][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="9b5d5-171">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b5d5-172">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="9b5d5-173">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b5d5-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b5d5-176">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9b5d5-177">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9b5d5-178">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9b5d5-179">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b5d5-180">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9b5d5-181">Hämta rpm-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till Red Hat Enterprise Linux datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="9b5d5-182">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b5d5-183">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9b5d5-184">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="9b5d5-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9b5d5-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="9b5d5-186">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="9b5d5-186">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="9b5d5-187">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="9b5d5-187">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="9b5d5-188">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="9b5d5-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="9b5d5-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="9b5d5-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="9b5d5-190">Fedora 28 stöds endast i PowerShell Core 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="9b5d5-191">Installation via paketets lagrings plats (rekommenderas) – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b5d5-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="9b5d5-192">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="9b5d5-193">Installation via direkt hämtning – Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b5d5-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="9b5d5-194">Hämta rpm-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] på Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="9b5d5-195">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9b5d5-196">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="9b5d5-197">Avinstallation-Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b5d5-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="9b5d5-198">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="9b5d5-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="9b5d5-199">Stöd för båge är experimentellt.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-199">Arch support is experimental.</span></span>

<span data-ttu-id="9b5d5-200">PowerShell är tillgängligt från användar lagrings platsen för [Båge Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="9b5d5-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="9b5d5-201">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="9b5d5-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="9b5d5-202">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="9b5d5-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="9b5d5-203">Den kan installeras med den [senaste versionen][arch-bin] av binärfilen</span><span class="sxs-lookup"><span data-stu-id="9b5d5-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="9b5d5-204">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="9b5d5-205">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller community- [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="9b5d5-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="9b5d5-207">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="9b5d5-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="9b5d5-208">Fäst</span><span class="sxs-lookup"><span data-stu-id="9b5d5-208">Getting snapd</span></span>

<span data-ttu-id="9b5d5-209">`snapd`krävs för att köra fäst.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="9b5d5-210">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att `snapd` du har installerat.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="9b5d5-211">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="9b5d5-211">Installation via Snap</span></span>

<span data-ttu-id="9b5d5-212">PowerShell Core för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="9b5d5-213">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="9b5d5-214">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="9b5d5-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="9b5d5-215">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="9b5d5-216">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="9b5d5-217">Avinstallationen</span><span class="sxs-lookup"><span data-stu-id="9b5d5-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="9b5d5-218">eller</span><span class="sxs-lookup"><span data-stu-id="9b5d5-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="9b5d5-219">Kali</span><span class="sxs-lookup"><span data-stu-id="9b5d5-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="9b5d5-220">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="9b5d5-220">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="9b5d5-221">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="9b5d5-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="9b5d5-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="9b5d5-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="9b5d5-223">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="9b5d5-224">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="9b5d5-225">CoreCLR och PowerShell-kärnan fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="9b5d5-226">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="9b5d5-227">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="9b5d5-227">Installation - Raspbian</span></span>

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

<span data-ttu-id="9b5d5-228">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till den `pwsh` binära filen.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="9b5d5-229">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="9b5d5-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="9b5d5-230">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9b5d5-230">Binary Archives</span></span>

<span data-ttu-id="9b5d5-231">PowerShell- `tar.gz` binärfiler finns för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="9b5d5-232">Relation</span><span class="sxs-lookup"><span data-stu-id="9b5d5-232">Dependencies</span></span>

<span data-ttu-id="9b5d5-233">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="9b5d5-234">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="9b5d5-235">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="9b5d5-236">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="9b5d5-236">OS</span></span>                 | <span data-ttu-id="9b5d5-237">Relation</span><span class="sxs-lookup"><span data-stu-id="9b5d5-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="9b5d5-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="9b5d5-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9b5d5-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b5d5-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="9b5d5-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="9b5d5-241">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="9b5d5-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="9b5d5-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9b5d5-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b5d5-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="9b5d5-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="9b5d5-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9b5d5-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="9b5d5-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9b5d5-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b5d5-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="9b5d5-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="9b5d5-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="9b5d5-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="9b5d5-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9b5d5-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b5d5-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="9b5d5-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="9b5d5-250">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="9b5d5-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="9b5d5-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9b5d5-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9b5d5-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="9b5d5-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="9b5d5-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-253">CentOS 7</span></span> <br> <span data-ttu-id="9b5d5-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="9b5d5-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="9b5d5-255">RHEL 7</span></span> | <span data-ttu-id="9b5d5-256">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="9b5d5-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="9b5d5-257">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="9b5d5-257">openSUSE 42.3</span></span> | <span data-ttu-id="9b5d5-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="9b5d5-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="9b5d5-259">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="9b5d5-259">openSUSE Leap 15</span></span> | <span data-ttu-id="9b5d5-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="9b5d5-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="9b5d5-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="9b5d5-261">Fedora 27</span></span> <br> <span data-ttu-id="9b5d5-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9b5d5-262">Fedora 28</span></span> | <span data-ttu-id="9b5d5-263">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="9b5d5-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="9b5d5-264">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="9b5d5-265">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux `tar.gz` -arkivet.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="9b5d5-266">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9b5d5-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="9b5d5-267">Linux</span><span class="sxs-lookup"><span data-stu-id="9b5d5-267">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="9b5d5-268">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9b5d5-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="9b5d5-269">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="9b5d5-269">Paths</span></span>

* <span data-ttu-id="9b5d5-270">`$PSHOME`utgör`/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="9b5d5-271">Användar profilerna kommer att läsas från`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="9b5d5-272">Standard profiler kommer att läsas från`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="9b5d5-273">Användarens moduler kommer att läsas från`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9b5d5-274">Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="9b5d5-275">Standardmoduler kommer att läsas från`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="9b5d5-276">PSReadline historik registreras i`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9b5d5-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9b5d5-277">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade `Microsoft.PowerShell_profile.ps1` profilerna finns på samma platser.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9b5d5-278">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="9b5d5-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
