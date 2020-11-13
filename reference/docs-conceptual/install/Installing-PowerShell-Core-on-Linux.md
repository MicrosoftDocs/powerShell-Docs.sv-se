---
title: Installera PowerShell i Linux
description: Information om hur du installerar PowerShell på olika Linux-distributioner
ms.date: 11/11/2020
ms.openlocfilehash: c56708ab930a7285de92d657ed12182fc298fb73
ms.sourcegitcommit: e85e56d6614cbd30e01965a5cf03fb3f5ca78103
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2020
ms.locfileid: "94589116"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="1bd5d-103">Installera PowerShell i Linux</span><span class="sxs-lookup"><span data-stu-id="1bd5d-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="1bd5d-104">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="1bd5d-105">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="1bd5d-106">Kör `pwsh-preview` om du har installerat en för [hands version](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="1bd5d-108">`/usr/local/microsoft/powershell/6`Mappen ersätts av `/usr/local/microsoft/powershell/7` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="1bd5d-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="1bd5d-110">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="1bd5d-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="1bd5d-111">Du kan också prova att distribuera PowerShell-binärfiler direkt med Linux- [ `tar.gz` arkivet][tar], men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<!-- TODO: Update for supported releases v7.0 & v7.1 -->

<span data-ttu-id="1bd5d-112">Officiellt stödda plattforms utgåvor för PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1bd5d-112">Officially supported platform releases for PowerShell 7.1</span></span>

- <span data-ttu-id="1bd5d-113">Ubuntu 16.04/18.04/20.04 (inklusive ARM64)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-113">Ubuntu 16.04/18.04/20.04 (including ARM64)</span></span>
- <span data-ttu-id="1bd5d-114">Ubuntu 19,10 (via Snap-paket)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-114">Ubuntu 19.10 (via Snap package)</span></span>
- <span data-ttu-id="1bd5d-115">Debian 9/10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-115">Debian 9/10</span></span>
- <span data-ttu-id="1bd5d-116">CentOS och RHEL 7/8</span><span class="sxs-lookup"><span data-stu-id="1bd5d-116">CentOS and RHEL 7/8</span></span>
- <span data-ttu-id="1bd5d-117">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="1bd5d-117">Fedora 30</span></span>
- <span data-ttu-id="1bd5d-118">Alpine 3.11 + (inklusive ARM64)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-118">Alpine 3.11+ (including ARM64)</span></span>

<span data-ttu-id="1bd5d-119">Officiellt stödda plattforms utgåvor för PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="1bd5d-119">Officially supported platform releases for PowerShell 7.0</span></span>

- <span data-ttu-id="1bd5d-120">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-120">Ubuntu 16.04</span></span>
- <span data-ttu-id="1bd5d-121">Ubuntu 18,04 och 20,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-121">Ubuntu 18.04 and 20.04</span></span>
- <span data-ttu-id="1bd5d-122">Debian 8</span><span class="sxs-lookup"><span data-stu-id="1bd5d-122">Debian 8</span></span>
- <span data-ttu-id="1bd5d-123">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1bd5d-123">Debian 9</span></span>
- <span data-ttu-id="1bd5d-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-124">Debian 10</span></span>
- <span data-ttu-id="1bd5d-125">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-125">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="1bd5d-126">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-126">CentOS 7</span></span>
- <span data-ttu-id="1bd5d-127">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-127">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="1bd5d-128">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1bd5d-128">Fedora 28</span></span>
- <span data-ttu-id="1bd5d-129">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="1bd5d-129">Fedora 29</span></span>
- <span data-ttu-id="1bd5d-130">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="1bd5d-130">Fedora 30</span></span>
- <span data-ttu-id="1bd5d-131">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="1bd5d-131">openSUSE 42.3</span></span>
- <span data-ttu-id="1bd5d-132">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="1bd5d-132">openSUSE Leap 15</span></span>

<span data-ttu-id="1bd5d-133">Versioner som stöds av community</span><span class="sxs-lookup"><span data-stu-id="1bd5d-133">Community supported releases</span></span>

- <span data-ttu-id="1bd5d-134">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-134">Ubuntu 18.10</span></span>
- <span data-ttu-id="1bd5d-135">Ubuntu 19,10 och 20,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-135">Ubuntu 19.10 and 20.10</span></span>
- <span data-ttu-id="1bd5d-136">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="1bd5d-136">Arch Linux</span></span>
- <span data-ttu-id="1bd5d-137">Kali</span><span class="sxs-lookup"><span data-stu-id="1bd5d-137">Kali</span></span>
- <span data-ttu-id="1bd5d-138">Raspbian (experimentell)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-138">Raspbian (experimental)</span></span>

<span data-ttu-id="1bd5d-139">Alternativa installations metoder</span><span class="sxs-lookup"><span data-stu-id="1bd5d-139">Alternate install methods</span></span>

- <span data-ttu-id="1bd5d-140">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="1bd5d-140">Snap Package</span></span>
- <span data-ttu-id="1bd5d-141">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="1bd5d-141">Binary Archives</span></span>
- <span data-ttu-id="1bd5d-142">Globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="1bd5d-142">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="1bd5d-143">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-143">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="1bd5d-144">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-144">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="1bd5d-145">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-145">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-146">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-146">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1bd5d-147">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-147">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-148">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-148">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="1bd5d-149">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-149">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="1bd5d-150">Ladda ned Debian-paketet `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-150">Download the Debian package `powershell_7.1.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1bd5d-151">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-151">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1bd5d-152">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-152">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="1bd5d-153">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="1bd5d-154">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-154">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="1bd5d-155">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-155">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="1bd5d-156">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-156">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="1bd5d-157">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-158">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1bd5d-159">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-160">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-160">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="1bd5d-161">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-161">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="1bd5d-162">Ladda ned Debian-paketet `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-162">Download the Debian package `powershell_7.1.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1bd5d-163">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-163">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1bd5d-164">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-164">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="1bd5d-165">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-165">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="1bd5d-166">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-166">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-2004"></a><span data-ttu-id="1bd5d-167">Ubuntu 20.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-167">Ubuntu 20.04</span></span>

### <a name="installation-via-package-repository---ubuntu-2004"></a><span data-ttu-id="1bd5d-168">Installation via paket lagring – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-168">Installation via Package Repository - Ubuntu 20.04</span></span>

<span data-ttu-id="1bd5d-169">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-169">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-170">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-170">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1bd5d-171">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-171">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-172">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-172">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-2004"></a><span data-ttu-id="1bd5d-173">Installation via direkt hämtning – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-173">Installation via Direct Download - Ubuntu 20.04</span></span>

<span data-ttu-id="1bd5d-174">Ladda ned Debian-paketet `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-174">Download the Debian package `powershell_7.1.0-1.ubuntu.20.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1bd5d-175">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.ubuntu.20.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1bd5d-176">Kommandot kan inte utföras `dpkg -i` med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-176">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="1bd5d-177">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-177">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-2004"></a><span data-ttu-id="1bd5d-178">Avinstallation – Ubuntu 20,04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-178">Uninstallation - Ubuntu 20.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="1bd5d-179">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-179">Ubuntu 18.10</span></span>

<span data-ttu-id="1bd5d-180">Installationen stöds via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-180">Installation is supported via `snapd`.</span></span> <span data-ttu-id="1bd5d-181">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="1bd5d-181">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-182">Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-182">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1910-and-2010"></a><span data-ttu-id="1bd5d-183">Ubuntu 19,10 och 20,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-183">Ubuntu 19.10 and 20.10</span></span>

<span data-ttu-id="1bd5d-184">Installationen stöds via `snapd` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-184">Installation is supported via `snapd`.</span></span> <span data-ttu-id="1bd5d-185">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="1bd5d-185">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-186">Ubuntu 19,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-186">Ubuntu 19.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="1bd5d-187">Debian 8</span><span class="sxs-lookup"><span data-stu-id="1bd5d-187">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="1bd5d-188">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="1bd5d-188">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="1bd5d-189">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-189">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-190">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-190">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1bd5d-191">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-191">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-192">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-192">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="1bd5d-193">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1bd5d-193">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="1bd5d-194">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="1bd5d-194">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="1bd5d-195">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-195">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-196">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-196">The preferred method is as follows:</span></span>

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

<span data-ttu-id="1bd5d-197">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-197">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-198">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get install powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-198">After registration, you can update PowerShell with `sudo apt-get install powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="1bd5d-199">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="1bd5d-199">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="1bd5d-200">Ladda ned Debian-paketet `powershell_7.1.0-1.debian.9_amd64.deb` från sidan [releases][] på Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-200">Download the Debian package `powershell_7.1.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1bd5d-201">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-201">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="1bd5d-202">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="1bd5d-202">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="1bd5d-203">Debian 10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-203">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-204">Debian 10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-204">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="1bd5d-205">Installation via paket lagring – Debian 10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-205">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="1bd5d-206">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-206">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-207">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-207">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="1bd5d-208">Installation via direkt hämtning – Debian 10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-208">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="1bd5d-209">Hämta paketet tar. gz `powershell-7.1.0-linux-x64.tar.gz` från sidan [utgåvor][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-209">Download the tar.gz package `powershell-7.1.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1bd5d-210">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-210">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="1bd5d-211">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-211">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-212">Alpine 3,9 och 3,10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-212">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="1bd5d-213">Installation via direkt hämtning – Alpine 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-213">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="1bd5d-214">Hämta paketet tar. gz `powershell-7.1.0-linux-alpine-x64.tar.gz` från sidan [utgåvor][] till Alpine Machine.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-214">Download the tar.gz package `powershell-7.1.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="1bd5d-215">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-215">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="1bd5d-216">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-216">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-217">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-217">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="1bd5d-218">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-218">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="1bd5d-219">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-219">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1bd5d-220">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-220">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-221">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-221">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="1bd5d-222">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-222">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="1bd5d-223">Med [CentOS 7][]laddar du ned rpm-paketet `powershell-7.1.0-1.rhel.7.x86_64.rpm` från sidan [utgåvor][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-223">Using [CentOS 7][], download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="1bd5d-224">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-224">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1bd5d-225">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-225">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="1bd5d-226">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-226">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1bd5d-228">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-228">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1bd5d-229">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-229">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1bd5d-230">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-230">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1bd5d-231">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-231">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="1bd5d-232">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-232">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1bd5d-233">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-233">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1bd5d-234">Hämta RPM-paketet `powershell-7.1.0-1.rhel.7.x86_64.rpm` från sidan [versioner][] till Red Hat Enterprise Linux datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-234">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="1bd5d-235">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-235">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1bd5d-236">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-236">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1bd5d-237">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-237">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="1bd5d-238">openSUSE</span><span class="sxs-lookup"><span data-stu-id="1bd5d-238">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="1bd5d-239">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="1bd5d-239">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="1bd5d-240">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="1bd5d-240">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="1bd5d-241">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="1bd5d-241">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="1bd5d-242">Fedora</span><span class="sxs-lookup"><span data-stu-id="1bd5d-242">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-243">Fedora 28 stöds endast i PowerShell 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-243">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-244">Fedora 29 och 30 stöds bara i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-244">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="1bd5d-245">Installation via paketets lagrings plats (prioriterad)-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="1bd5d-245">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="1bd5d-246">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-246">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="1bd5d-247">Installation via direkt hämtning-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="1bd5d-247">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="1bd5d-248">Hämta RPM-paketet `powershell-7.1.0-1.rhel.7.x86_64.rpm` från sidan [releases][] på Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-248">Download the RPM package `powershell-7.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="1bd5d-249">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-249">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1bd5d-250">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-250">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.1.0/powershell-7.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="1bd5d-251">Avinstallation-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="1bd5d-251">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="1bd5d-252">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="1bd5d-252">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-253">Stöd för båge stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-253">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="1bd5d-254">PowerShell är tillgängligt från användar lagrings platsen för [Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-254">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="1bd5d-255">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="1bd5d-255">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="1bd5d-256">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="1bd5d-256">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="1bd5d-257">Den kan installeras med den [senaste versionen av binärfilen][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="1bd5d-257">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="1bd5d-258">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-258">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="1bd5d-259">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller [använda PowerShell i Docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-259">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="1bd5d-261">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="1bd5d-261">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="1bd5d-262">Fäst</span><span class="sxs-lookup"><span data-stu-id="1bd5d-262">Getting snapd</span></span>

<span data-ttu-id="1bd5d-263">`snapd` krävs för att köra fäst.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-263">`snapd` is required to run snaps.</span></span> <span data-ttu-id="1bd5d-264">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att du har `snapd` installerat.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-264">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="1bd5d-265">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="1bd5d-265">Installation via Snap</span></span>

<span data-ttu-id="1bd5d-266">PowerShell för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-266">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="1bd5d-267">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-267">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="1bd5d-268">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-268">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="1bd5d-269">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-269">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="1bd5d-270">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-270">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="1bd5d-271">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="1bd5d-271">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="1bd5d-272">eller</span><span class="sxs-lookup"><span data-stu-id="1bd5d-272">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="1bd5d-273">Kali</span><span class="sxs-lookup"><span data-stu-id="1bd5d-273">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-274">Kali-support stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-274">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="1bd5d-275">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="1bd5d-275">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="1bd5d-276">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="1bd5d-276">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="1bd5d-277">Raspbian</span><span class="sxs-lookup"><span data-stu-id="1bd5d-277">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="1bd5d-278">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-278">Raspbian support is experimental.</span></span>

<span data-ttu-id="1bd5d-279">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-279">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="1bd5d-280">CoreCLR och PowerShell fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-280">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="1bd5d-281">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-281">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="1bd5d-282">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="1bd5d-282">Installation - Raspbian</span></span>

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

<span data-ttu-id="1bd5d-283">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till den `pwsh` binära filen.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-283">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="1bd5d-284">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="1bd5d-284">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="1bd5d-285">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="1bd5d-285">Installing Preview Releases</span></span>

<span data-ttu-id="1bd5d-286">När du installerar en PowerShell Preview-version för Linux via en paket lagrings plats ändras paket namnet från `powershell` till `powershell-preview` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-286">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="1bd5d-287">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-287">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="1bd5d-288">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="1bd5d-288">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="1bd5d-289">Distribution</span><span class="sxs-lookup"><span data-stu-id="1bd5d-289">Distribution(s)</span></span> |            <span data-ttu-id="1bd5d-290">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="1bd5d-290">Stable Command</span></span>            |               <span data-ttu-id="1bd5d-291">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="1bd5d-291">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="1bd5d-292">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="1bd5d-292">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="1bd5d-293">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="1bd5d-293">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="1bd5d-294">Fedora</span><span class="sxs-lookup"><span data-stu-id="1bd5d-294">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="1bd5d-295">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="1bd5d-295">Install as a .NET Global tool</span></span>

<span data-ttu-id="1bd5d-296">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="1bd5d-296">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="1bd5d-297">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-297">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="1bd5d-298">Men det gränssnitt som körs har inte uppdaterats `PATH` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-298">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="1bd5d-299">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="1bd5d-299">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="1bd5d-300">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="1bd5d-300">Binary Archives</span></span>

<span data-ttu-id="1bd5d-301">PowerShell-binärfiler `tar.gz` finns för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-301">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="1bd5d-302">Beroenden</span><span class="sxs-lookup"><span data-stu-id="1bd5d-302">Dependencies</span></span>

<span data-ttu-id="1bd5d-303">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-303">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="1bd5d-304">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-304">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="1bd5d-305">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-305">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="1bd5d-306">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="1bd5d-306">OS</span></span>                 | <span data-ttu-id="1bd5d-307">Beroenden</span><span class="sxs-lookup"><span data-stu-id="1bd5d-307">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="1bd5d-308">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-308">Ubuntu 16.04</span></span>       | <span data-ttu-id="1bd5d-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1bd5d-309">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1bd5d-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="1bd5d-310">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="1bd5d-311">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-311">Ubuntu 17.10</span></span>       | <span data-ttu-id="1bd5d-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1bd5d-312">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1bd5d-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="1bd5d-313">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="1bd5d-314">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="1bd5d-314">Ubuntu 18.04</span></span>       | <span data-ttu-id="1bd5d-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1bd5d-315">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1bd5d-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="1bd5d-316">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="1bd5d-317">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-317">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="1bd5d-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1bd5d-318">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1bd5d-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1bd5d-319">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1bd5d-320">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="1bd5d-320">Debian 9 (Stretch)</span></span> | <span data-ttu-id="1bd5d-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1bd5d-321">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1bd5d-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="1bd5d-322">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="1bd5d-323">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-323">CentOS 7</span></span> <br> <span data-ttu-id="1bd5d-324">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-324">Oracle Linux 7</span></span> <br> <span data-ttu-id="1bd5d-325">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="1bd5d-325">RHEL 7</span></span> | <span data-ttu-id="1bd5d-326">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="1bd5d-326">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="1bd5d-327">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="1bd5d-327">openSUSE 42.3</span></span> | <span data-ttu-id="1bd5d-328">libcurl4, libopenssl1_0_0 libicu52_1</span><span class="sxs-lookup"><span data-stu-id="1bd5d-328">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="1bd5d-329">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="1bd5d-329">openSUSE Leap 15</span></span> | <span data-ttu-id="1bd5d-330">libcurl4, libopenssl1_0_0 libicu60_2</span><span class="sxs-lookup"><span data-stu-id="1bd5d-330">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="1bd5d-331">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="1bd5d-331">Fedora 27</span></span> <br> <span data-ttu-id="1bd5d-332">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1bd5d-332">Fedora 28</span></span> | <span data-ttu-id="1bd5d-333">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="1bd5d-333">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="1bd5d-334">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-334">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="1bd5d-335">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux- `tar.gz` arkivet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-335">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="1bd5d-336">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="1bd5d-336">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="1bd5d-337">Linux</span><span class="sxs-lookup"><span data-stu-id="1bd5d-337">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="1bd5d-338">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="1bd5d-338">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="1bd5d-339">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="1bd5d-339">Paths</span></span>

- <span data-ttu-id="1bd5d-340">`$PSHOME` är `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-340">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="1bd5d-341">Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-341">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="1bd5d-342">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-342">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="1bd5d-343">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-343">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="1bd5d-344">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-344">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="1bd5d-345">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-345">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="1bd5d-346">PSReadLine historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="1bd5d-346">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="1bd5d-347">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade profilerna finns på `Microsoft.PowerShell_profile.ps1` samma platser.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-347">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="1bd5d-348">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-348">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

## <a name="installation-support"></a><span data-ttu-id="1bd5d-349">Installations stöd</span><span class="sxs-lookup"><span data-stu-id="1bd5d-349">Installation support</span></span>

<span data-ttu-id="1bd5d-350">Microsoft stöder installations metoderna i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-350">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="1bd5d-351">Det kan finnas andra installations metoder som är tillgängliga från andra källor.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-351">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="1bd5d-352">Dessa verktyg och metoder kan fungera, men Microsoft stöder inte dessa metoder.</span><span class="sxs-lookup"><span data-stu-id="1bd5d-352">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->
[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
[distros]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md#linux
[Distribution Support Request]: https://github.com/PowerShell/PowerShell/issues/new?assignees=&labels=Distribution-Request&template=Distribution_Request.md&title=Distribution+Support+Request
