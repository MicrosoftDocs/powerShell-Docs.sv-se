---
title: Installera PowerShell i Linux
description: Information om hur du installerar PowerShell på olika Linux-distributioner
ms.date: 11/11/2020
ms.openlocfilehash: 28f388c63740cf74e56c707aef531a2a220a9468
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524832"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="cfabb-103">Installera PowerShell i Linux</span><span class="sxs-lookup"><span data-stu-id="cfabb-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="cfabb-104">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="cfabb-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="cfabb-105">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="cfabb-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="cfabb-106">Kör `pwsh-preview` om du har installerat en för [hands version](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="cfabb-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="cfabb-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="cfabb-108">`/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="cfabb-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="cfabb-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="cfabb-110">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="cfabb-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="cfabb-111">Du kan också prova att distribuera PowerShell-binärfiler direkt med Linux- [ `tar.gz` arkivet][tar], men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="cfabb-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="cfabb-112">Officiellt versioner som stöds</span><span class="sxs-lookup"><span data-stu-id="cfabb-112">Officially supported releases</span></span>

- <span data-ttu-id="cfabb-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="cfabb-114">Ubuntu 18,04 och 20,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-114">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="cfabb-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cfabb-115">Debian 8</span></span>
- <span data-ttu-id="cfabb-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfabb-116">Debian 9</span></span>
- <span data-ttu-id="cfabb-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfabb-117">Debian 10</span></span>
- <span data-ttu-id="cfabb-118">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="cfabb-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-119">CentOS 7</span></span>
- <span data-ttu-id="cfabb-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="cfabb-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cfabb-121">Fedora 28</span></span>
- <span data-ttu-id="cfabb-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="cfabb-122">Fedora 29</span></span>
- <span data-ttu-id="cfabb-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="cfabb-123">Fedora 30</span></span>
- <span data-ttu-id="cfabb-124">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="cfabb-124">openSUSE 42.3</span></span>
- <span data-ttu-id="cfabb-125">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="cfabb-125">openSUSE Leap 15</span></span>

<span data-ttu-id="cfabb-126">Versioner som stöds av community</span><span class="sxs-lookup"><span data-stu-id="cfabb-126">Community supported releases</span></span>

- <span data-ttu-id="cfabb-127">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="cfabb-128">Ubuntu 19,10 och 20,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-128">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="cfabb-129">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="cfabb-129">Arch Linux</span></span>
- <span data-ttu-id="cfabb-130">Kali</span><span class="sxs-lookup"><span data-stu-id="cfabb-130">Kali</span></span>
- <span data-ttu-id="cfabb-131">Raspbian (experimentell)</span><span class="sxs-lookup"><span data-stu-id="cfabb-131">Raspbian (experimental)</span></span>

<span data-ttu-id="cfabb-132">Alternativa installations metoder</span><span class="sxs-lookup"><span data-stu-id="cfabb-132">Alternate install methods</span></span>

- <span data-ttu-id="cfabb-133">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="cfabb-133">Snap Package</span></span>
- <span data-ttu-id="cfabb-134">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="cfabb-134">Binary Archives</span></span>
- <span data-ttu-id="cfabb-135">Globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="cfabb-135">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="cfabb-136">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-136">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="cfabb-137">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-137">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="cfabb-138">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-138">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-139">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-139">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb
# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb
# Update the list of packages after we added packages.microsoft.com
sudo apt-get update
# Install PowerShell
sudo apt-get install -y powershell
# Start PowerShell
pwsh
```

<span data-ttu-id="cfabb-140">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-140">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-141">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-141">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="cfabb-142">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-142">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="cfabb-143">Ladda ned Debian-paketet `powershell-lts_7.1.0-1.ubuntu.16.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-143">Download the Debian package `powershell-lts_7.1.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cfabb-144">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-144">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cfabb-145">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="cfabb-145">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="cfabb-146">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-146">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="cfabb-147">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-147">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="cfabb-148">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-148">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="cfabb-149">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-149">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="cfabb-150">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-150">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-151">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-151">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
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

<span data-ttu-id="cfabb-152">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-152">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-153">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-153">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="cfabb-154">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-154">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="cfabb-155">Ladda ned Debian-paketet `powershell-lts_7.1.0-1.ubuntu.18.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-155">Download the Debian package `powershell-lts_7.1.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cfabb-156">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-156">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cfabb-157">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="cfabb-157">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="cfabb-158">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-158">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="cfabb-159">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-159">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="cfabb-160">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-160">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="cfabb-161">Installation via paket lagring – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-161">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="cfabb-162">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-162">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-163">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-163">The preferred method is as follows:</span></span>

```sh
# Update the list of packages
sudo apt-get update
# Install pre-requisite packages.
sudo apt-get install -y wget apt-transport-https
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
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

<span data-ttu-id="cfabb-164">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-164">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-165">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-165">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="cfabb-166">Installation via direkt hämtning – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-166">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="cfabb-167">Ladda ned Debian-paketet `powershell-lts_7.1.0-1.ubuntu.20.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-167">Download the Debian package `powershell-lts_7.1.0-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cfabb-168">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-168">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cfabb-169">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="cfabb-169">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="cfabb-170">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-170">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="cfabb-171">Avinstallation – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="cfabb-171">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="cfabb-172">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-172">Ubuntu 18.10</span></span>

<span data-ttu-id="cfabb-173">Installationen stöds via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-173">Installation is supported via `snapd`.</span></span> <span data-ttu-id="cfabb-174">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="cfabb-174">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-175">Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="cfabb-175">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="cfabb-176">Ubuntu 19,10 och 20,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-176">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="cfabb-177">Installationen stöds via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-177">Installation is supported via `snapd`.</span></span> <span data-ttu-id="cfabb-178">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="cfabb-178">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-179">Ubuntu 19,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="cfabb-179">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="cfabb-180">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cfabb-180">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="cfabb-181">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="cfabb-181">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="cfabb-182">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-182">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-183">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-183">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

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

<span data-ttu-id="cfabb-184">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-184">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-185">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-185">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="cfabb-186">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfabb-186">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="cfabb-187">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfabb-187">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="cfabb-188">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-188">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-189">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-189">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

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

<span data-ttu-id="cfabb-190">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-190">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-191">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-191">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="cfabb-192">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfabb-192">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="cfabb-193">Ladda ned Debian-paketet `powershell-lts_7.1.0-1.debian.9_amd64.deb` från sidan [releases][] på Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-193">Download the Debian package `powershell-lts_7.1.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cfabb-194">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-194">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="cfabb-195">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="cfabb-195">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="cfabb-196">Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfabb-196">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-197">Debian 10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cfabb-197">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="cfabb-198">Installation via paket lagring – Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfabb-198">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="cfabb-199">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-199">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-200">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-200">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="cfabb-201">Installation via direkt hämtning – Debian 10</span><span class="sxs-lookup"><span data-stu-id="cfabb-201">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="cfabb-202">Hämta paketet tar. gz `powershell-7.1.0-linux-x64.tar.gz` från sidan [utgåvor][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-202">Download the tar.gz package `powershell-7.1.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cfabb-203">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-203">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="cfabb-204">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-204">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-205">Alpine 3,9 och 3,10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cfabb-205">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="cfabb-206">Installation via direkt hämtning – Alpine 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-206">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="cfabb-207">Hämta paketet tar. gz `powershell-7.1.0-linux-alpine-x64.tar.gz` från sidan [utgåvor][] till Alpine Machine.</span><span class="sxs-lookup"><span data-stu-id="cfabb-207">Download the tar.gz package `powershell-7.1.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="cfabb-208">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-208">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="cfabb-209">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-209">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-210">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="cfabb-210">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="cfabb-211">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-211">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="cfabb-212">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-212">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cfabb-213">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-213">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-214">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-214">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="cfabb-215">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-215">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="cfabb-216">Med [CentOS 7][]laddar du ned rpm-paketet `powershell-lts-7.1.0-1.rhel.7.x86_64.rpm` från sidan [utgåvor][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-216">Using [CentOS 7][], download the RPM package `powershell-lts-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="cfabb-217">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-217">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfabb-218">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="cfabb-218">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-lts-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="cfabb-219">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-219">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfabb-221">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-221">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfabb-222">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-222">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cfabb-223">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-223">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cfabb-224">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="cfabb-224">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="cfabb-225">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-225">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfabb-226">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-226">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cfabb-227">Hämta RPM-paketet `powershell-lts-7.1.0-1.rhel.7.x86_64.rpm` från sidan [versioner][] till Red Hat Enterprise Linux datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-227">Download the RPM package `powershell-lts-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="cfabb-228">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-228">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfabb-229">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="cfabb-229">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-lts-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cfabb-230">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-230">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="cfabb-231">openSUSE</span><span class="sxs-lookup"><span data-stu-id="cfabb-231">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="cfabb-232">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="cfabb-232">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="cfabb-233">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="cfabb-233">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="cfabb-234">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="cfabb-234">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="cfabb-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="cfabb-235">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-236">Fedora 28 stöds endast i PowerShell 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="cfabb-236">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-237">Fedora 29 och 30 stöds bara i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cfabb-237">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="cfabb-238">Installation via paketets lagrings plats (prioriterad)-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="cfabb-238">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="cfabb-239">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-239">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf check-update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="cfabb-240">Installation via direkt hämtning-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="cfabb-240">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="cfabb-241">Hämta RPM-paketet `powershell-7.1.0-1.rhel.7.x86_64.rpm` från sidan [releases][] på Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-241">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cfabb-242">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="cfabb-242">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cfabb-243">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="cfabb-243">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="cfabb-244">Avinstallation-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="cfabb-244">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="cfabb-245">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="cfabb-245">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-246">Stöd för båge stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-246">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="cfabb-247">PowerShell är tillgängligt från användar lagrings platsen för [Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="cfabb-247">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="cfabb-248">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="cfabb-248">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="cfabb-249">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="cfabb-249">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="cfabb-250">Den kan installeras med den [senaste versionen av binärfilen][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="cfabb-250">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="cfabb-251">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="cfabb-251">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="cfabb-252">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller [använda PowerShell i Docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="cfabb-252">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="cfabb-254">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="cfabb-254">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="cfabb-255">Fäst</span><span class="sxs-lookup"><span data-stu-id="cfabb-255">Getting snapd</span></span>

<span data-ttu-id="cfabb-256">`snapd` krävs för att köra fäst.</span><span class="sxs-lookup"><span data-stu-id="cfabb-256">`snapd` is required to run snaps.</span></span> <span data-ttu-id="cfabb-257">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att du har `snapd` installerat.</span><span class="sxs-lookup"><span data-stu-id="cfabb-257">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="cfabb-258">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="cfabb-258">Installation via Snap</span></span>

<span data-ttu-id="cfabb-259">PowerShell för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="cfabb-259">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="cfabb-260">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="cfabb-260">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="cfabb-261">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="cfabb-261">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="cfabb-262">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="cfabb-262">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="cfabb-263">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-263">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="cfabb-264">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="cfabb-264">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="cfabb-265">eller</span><span class="sxs-lookup"><span data-stu-id="cfabb-265">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="cfabb-266">Kali</span><span class="sxs-lookup"><span data-stu-id="cfabb-266">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-267">Kali-support stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="cfabb-267">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="cfabb-268">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="cfabb-268">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="cfabb-269">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="cfabb-269">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="cfabb-270">Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfabb-270">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="cfabb-271">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="cfabb-271">Raspbian support is experimental.</span></span>

<span data-ttu-id="cfabb-272">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="cfabb-272">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="cfabb-273">CoreCLR och PowerShell fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="cfabb-273">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="cfabb-274">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="cfabb-274">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="cfabb-275">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfabb-275">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="cfabb-276">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till den `pwsh` binära filen.</span><span class="sxs-lookup"><span data-stu-id="cfabb-276">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="cfabb-277">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="cfabb-277">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="cfabb-278">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="cfabb-278">Installing Preview Releases</span></span>

<span data-ttu-id="cfabb-279">När du installerar en PowerShell Preview-version för Linux via en paket lagrings plats ändras paket namnet från `powershell` till `powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-279">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="cfabb-280">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-280">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="cfabb-281">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="cfabb-281">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="cfabb-282">Distribution</span><span class="sxs-lookup"><span data-stu-id="cfabb-282">Distribution(s)</span></span> |            <span data-ttu-id="cfabb-283">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="cfabb-283">Stable Command</span></span>            |               <span data-ttu-id="cfabb-284">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="cfabb-284">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="cfabb-285">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="cfabb-285">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="cfabb-286">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="cfabb-286">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="cfabb-287">Fedora</span><span class="sxs-lookup"><span data-stu-id="cfabb-287">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="cfabb-288">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="cfabb-288">Install as a .NET Global tool</span></span>

<span data-ttu-id="cfabb-289">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="cfabb-289">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="cfabb-290">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="cfabb-290">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="cfabb-291">Men det gränssnitt som körs har inte uppdaterats `PATH` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-291">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="cfabb-292">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="cfabb-292">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="cfabb-293">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="cfabb-293">Binary Archives</span></span>

<span data-ttu-id="cfabb-294">PowerShell-binärfiler `tar.gz` finns för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="cfabb-294">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="cfabb-295">Beroenden</span><span class="sxs-lookup"><span data-stu-id="cfabb-295">Dependencies</span></span>

<span data-ttu-id="cfabb-296">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="cfabb-296">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="cfabb-297">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cfabb-297">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="cfabb-298">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="cfabb-298">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="cfabb-299">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="cfabb-299">OS</span></span>                 | <span data-ttu-id="cfabb-300">Beroenden</span><span class="sxs-lookup"><span data-stu-id="cfabb-300">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="cfabb-301">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-301">Ubuntu 16.04</span></span>       | <span data-ttu-id="cfabb-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cfabb-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfabb-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="cfabb-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="cfabb-304">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="cfabb-304">Ubuntu 17.10</span></span>       | <span data-ttu-id="cfabb-305">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cfabb-305">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfabb-306">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="cfabb-306">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="cfabb-307">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cfabb-307">Ubuntu 18.04</span></span>       | <span data-ttu-id="cfabb-308">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cfabb-308">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfabb-309">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="cfabb-309">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="cfabb-310">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="cfabb-310">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="cfabb-311">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cfabb-311">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfabb-312">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cfabb-312">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cfabb-313">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="cfabb-313">Debian 9 (Stretch)</span></span> | <span data-ttu-id="cfabb-314">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cfabb-314">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cfabb-315">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="cfabb-315">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="cfabb-316">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-316">CentOS 7</span></span> <br> <span data-ttu-id="cfabb-317">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-317">Oracle Linux 7</span></span> <br> <span data-ttu-id="cfabb-318">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="cfabb-318">RHEL 7</span></span> | <span data-ttu-id="cfabb-319">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="cfabb-319">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="cfabb-320">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="cfabb-320">openSUSE 42.3</span></span> | <span data-ttu-id="cfabb-321">libcurl4, libopenssl1_0_0 libicu52_1</span><span class="sxs-lookup"><span data-stu-id="cfabb-321">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="cfabb-322">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="cfabb-322">openSUSE Leap 15</span></span> | <span data-ttu-id="cfabb-323">libcurl4, libopenssl1_0_0 libicu60_2</span><span class="sxs-lookup"><span data-stu-id="cfabb-323">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="cfabb-324">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="cfabb-324">Fedora 27</span></span> <br> <span data-ttu-id="cfabb-325">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cfabb-325">Fedora 28</span></span> | <span data-ttu-id="cfabb-326">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="cfabb-326">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="cfabb-327">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="cfabb-327">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="cfabb-328">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux- `tar.gz` arkivet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-328">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="cfabb-329">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="cfabb-329">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cfabb-330">Linux</span><span class="sxs-lookup"><span data-stu-id="cfabb-330">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="cfabb-331">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="cfabb-331">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="cfabb-332">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="cfabb-332">Paths</span></span>

- <span data-ttu-id="cfabb-333">`$PSHOME` är `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="cfabb-333">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="cfabb-334">Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cfabb-334">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="cfabb-335">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cfabb-335">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="cfabb-336">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cfabb-336">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="cfabb-337">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cfabb-337">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="cfabb-338">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="cfabb-338">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="cfabb-339">PSReadLine historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="cfabb-339">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cfabb-340">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade profilerna finns på `Microsoft.PowerShell_profile.ps1` samma platser.</span><span class="sxs-lookup"><span data-stu-id="cfabb-340">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cfabb-341">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="cfabb-341">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="cfabb-342">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="cfabb-342">Installation support</span></span>

<span data-ttu-id="cfabb-343">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="cfabb-343">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="cfabb-344">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="cfabb-344">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="cfabb-345">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="cfabb-345">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
