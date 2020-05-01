---
title: Installera PowerShell i Linux
description: Information om hur du installerar PowerShell på olika Linux-distributioner
ms.date: 03/09/2020
ms.openlocfilehash: 6ad637bd30e5e40ccc9532bae6f1171ecf79734a
ms.sourcegitcommit: e0a737961280026832cff9c658ed1468dc904e80
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82605857"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="9e196-103">Installera PowerShell i Linux</span><span class="sxs-lookup"><span data-stu-id="9e196-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="9e196-104">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="9e196-104">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="9e196-105">När paketet har installerats kör `pwsh` du från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="9e196-105">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="9e196-106">Kör `pwsh-preview` om du har installerat en för [hands version](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="9e196-106">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-107">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="9e196-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="9e196-108">`/usr/local/microsoft/powershell/6` Mappen ersätts av `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="9e196-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="9e196-109">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="9e196-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

<span data-ttu-id="9e196-110">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="9e196-110">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="9e196-111">Du kan också prova att distribuera PowerShell-binärfiler direkt med [ `tar.gz` ][tar]Linux-arkivet, men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="9e196-111">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

[snap]: #snap-package
[tar]: #binary-archives

<span data-ttu-id="9e196-112">Officiellt versioner som stöds</span><span class="sxs-lookup"><span data-stu-id="9e196-112">Officially supported releases</span></span>

- <span data-ttu-id="9e196-113">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9e196-113">Ubuntu 16.04</span></span>
- <span data-ttu-id="9e196-114">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9e196-114">Ubuntu 18.04</span></span>
- <span data-ttu-id="9e196-115">Debian 8</span><span class="sxs-lookup"><span data-stu-id="9e196-115">Debian 8</span></span>
- <span data-ttu-id="9e196-116">Debian 9</span><span class="sxs-lookup"><span data-stu-id="9e196-116">Debian 9</span></span>
- <span data-ttu-id="9e196-117">Debian 10</span><span class="sxs-lookup"><span data-stu-id="9e196-117">Debian 10</span></span>
- <span data-ttu-id="9e196-118">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="9e196-118">Alpine 3.9 and 3.10</span></span>
- <span data-ttu-id="9e196-119">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-119">CentOS 7</span></span>
- <span data-ttu-id="9e196-120">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9e196-120">Red Hat Enterprise Linux (RHEL) 7</span></span>
- <span data-ttu-id="9e196-121">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9e196-121">Fedora 28</span></span>
- <span data-ttu-id="9e196-122">Fedora 29</span><span class="sxs-lookup"><span data-stu-id="9e196-122">Fedora 29</span></span>
- <span data-ttu-id="9e196-123">Fedora 30</span><span class="sxs-lookup"><span data-stu-id="9e196-123">Fedora 30</span></span>
- <span data-ttu-id="9e196-124">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="9e196-124">openSUSE 42.3</span></span>
- <span data-ttu-id="9e196-125">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="9e196-125">openSUSE Leap 15</span></span>

<span data-ttu-id="9e196-126">Versioner som stöds av community</span><span class="sxs-lookup"><span data-stu-id="9e196-126">Community supported releases</span></span>

- <span data-ttu-id="9e196-127">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="9e196-127">Ubuntu 18.10</span></span>
- <span data-ttu-id="9e196-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="9e196-128">Ubuntu 19.04</span></span>
- <span data-ttu-id="9e196-129">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="9e196-129">Arch Linux</span></span>
- <span data-ttu-id="9e196-130">Kali</span><span class="sxs-lookup"><span data-stu-id="9e196-130">Kali</span></span>
- <span data-ttu-id="9e196-131">Raspbian (experimentell)</span><span class="sxs-lookup"><span data-stu-id="9e196-131">Raspbian (experimental)</span></span>

<span data-ttu-id="9e196-132">Alternativa installations metoder</span><span class="sxs-lookup"><span data-stu-id="9e196-132">Alternate install methods</span></span>

- <span data-ttu-id="9e196-133">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="9e196-133">Snap Package</span></span>
- <span data-ttu-id="9e196-134">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9e196-134">Binary Archives</span></span>
- <span data-ttu-id="9e196-135">Globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="9e196-135">.NET Global tool</span></span>

## <a name="ubuntu-1604"></a><span data-ttu-id="9e196-136">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9e196-136">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="9e196-137">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9e196-137">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="9e196-138">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-138">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9e196-139">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-139">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9e196-140">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-140">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-141">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-141">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="9e196-142">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9e196-142">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="9e196-143">Ladda ned Debian- `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-143">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9e196-144">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-144">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9e196-145">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="9e196-145">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="9e196-146">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="9e196-146">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="9e196-147">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="9e196-147">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="9e196-148">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9e196-148">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="9e196-149">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9e196-149">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="9e196-150">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-150">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9e196-151">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-151">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9e196-152">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-152">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-153">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-153">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="9e196-154">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9e196-154">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="9e196-155">Ladda ned Debian- `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` paketet från sidan [releases][] på Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-155">Download the Debian package `powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="9e196-156">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-156">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="9e196-157">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="9e196-157">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="9e196-158">Nästa kommando `apt-get install -f` löser dessa problem och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="9e196-158">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="9e196-159">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="9e196-159">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="9e196-160">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="9e196-160">Ubuntu 18.10</span></span>

<span data-ttu-id="9e196-161">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="9e196-161">Installation is supported via `snapd`.</span></span> <span data-ttu-id="9e196-162">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="9e196-162">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-163">Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="9e196-163">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="9e196-164">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="9e196-164">Ubuntu 19.04</span></span>

<span data-ttu-id="9e196-165">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="9e196-165">Installation is supported via `snapd`.</span></span> <span data-ttu-id="9e196-166">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="9e196-166">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-167">Ubuntu 19,04 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="9e196-167">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="9e196-168">Debian 8</span><span class="sxs-lookup"><span data-stu-id="9e196-168">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="9e196-169">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="9e196-169">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="9e196-170">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-170">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9e196-171">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-171">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9e196-172">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-172">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-173">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-173">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="9e196-174">Debian 9</span><span class="sxs-lookup"><span data-stu-id="9e196-174">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="9e196-175">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="9e196-175">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="9e196-176">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-176">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9e196-177">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-177">The preferred method is as follows:</span></span>

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

<span data-ttu-id="9e196-178">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-179">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-179">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="9e196-180">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="9e196-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="9e196-181">Ladda ned Debian- `powershell-lts_7.0.0-1.debian.9_amd64.deb` paketet från sidan [releases][] på Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-181">Download the Debian package `powershell-lts_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="9e196-182">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell-lts_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="9e196-183">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="9e196-183">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="9e196-184">Debian 10</span><span class="sxs-lookup"><span data-stu-id="9e196-184">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-185">Debian 10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9e196-185">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="9e196-186">Installation via paket lagring – Debian 10</span><span class="sxs-lookup"><span data-stu-id="9e196-186">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="9e196-187">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-187">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="9e196-188">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-188">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="9e196-189">Installation via direkt hämtning – Debian 10</span><span class="sxs-lookup"><span data-stu-id="9e196-189">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="9e196-190">Hämta paketet `powershell_7.0.0-linux-x64.tar.gz` tar. gz från sidan [utgåvor][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-190">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="9e196-191">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-191">Then, in the terminal, execute the following commands:</span></span>

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
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="9e196-192">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="9e196-192">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-193">Alpine 3,9 och 3,10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9e196-193">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="9e196-194">Installation via direkt hämtning – Alpine 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="9e196-194">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="9e196-195">Hämta paketet `powershell-7.0.0-linux-alpine-x64.tar.gz` tar. gz från sidan [utgåvor][] till Alpine Machine.</span><span class="sxs-lookup"><span data-stu-id="9e196-195">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="9e196-196">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-196">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

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

## <a name="centos-7"></a><span data-ttu-id="9e196-197">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-197">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-198">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="9e196-198">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="9e196-199">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-199">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="9e196-200">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-200">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9e196-201">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-201">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-202">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-202">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="9e196-203">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-203">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="9e196-204">Med [CentOS 7][]laddar du ned rpm- `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` paketet från sidan [utgåvor][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-204">Using [CentOS 7][], download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="9e196-205">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-205">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9e196-206">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9e196-206">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="9e196-207">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-207">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9e196-209">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9e196-209">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9e196-210">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9e196-210">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9e196-211">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="9e196-212">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="9e196-212">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="9e196-213">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="9e196-213">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9e196-214">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9e196-214">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="9e196-215">Hämta RPM-paketet `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` från sidan [versioner][] till Red Hat Enterprise Linux datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-215">Download the RPM package `powershell-lts-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="9e196-216">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-216">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9e196-217">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9e196-217">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-lts-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="9e196-218">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="9e196-218">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="9e196-219">openSUSE</span><span class="sxs-lookup"><span data-stu-id="9e196-219">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="9e196-220">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="9e196-220">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="9e196-221">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="9e196-221">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="9e196-222">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="9e196-222">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="9e196-223">Fedora</span><span class="sxs-lookup"><span data-stu-id="9e196-223">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-224">Fedora 28 stöds endast i PowerShell 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="9e196-224">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-225">Fedora 29 och 30 stöds bara i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9e196-225">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="9e196-226">Installation via paketets lagrings plats (prioriterad)-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="9e196-226">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="9e196-227">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-227">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="9e196-228">Installation via direkt hämtning-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="9e196-228">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="9e196-229">Hämta RPM-paketet `powershell-7.0.0-1.rhel.7.x86_64.rpm` från sidan [releases][] på Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="9e196-229">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="9e196-230">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="9e196-230">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="9e196-231">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="9e196-231">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="9e196-232">Avinstallation-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="9e196-232">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="9e196-233">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="9e196-233">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-234">Stöd för båge stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="9e196-234">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="9e196-235">PowerShell är tillgängligt från användar lagrings platsen för [Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="9e196-235">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

- <span data-ttu-id="9e196-236">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="9e196-236">It can be compiled with the [latest tagged release][arch-release]</span></span>
- <span data-ttu-id="9e196-237">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="9e196-237">It can be compiled from the [latest commit to master][arch-git]</span></span>
- <span data-ttu-id="9e196-238">Den kan installeras med den [senaste versionen av binärfilen][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="9e196-238">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="9e196-239">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="9e196-239">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="9e196-240">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller [använda PowerShell i Docker](powershell-in-docker.md).</span><span class="sxs-lookup"><span data-stu-id="9e196-240">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or [Using PowerShell in Docker](powershell-in-docker.md).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="9e196-242">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="9e196-242">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="9e196-243">Fäst</span><span class="sxs-lookup"><span data-stu-id="9e196-243">Getting snapd</span></span>

<span data-ttu-id="9e196-244">`snapd`krävs för att köra fäst.</span><span class="sxs-lookup"><span data-stu-id="9e196-244">`snapd` is required to run snaps.</span></span> <span data-ttu-id="9e196-245">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att `snapd` du har installerat.</span><span class="sxs-lookup"><span data-stu-id="9e196-245">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="9e196-246">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="9e196-246">Installation via Snap</span></span>

<span data-ttu-id="9e196-247">PowerShell för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9e196-247">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="9e196-248">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="9e196-248">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="9e196-249">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="9e196-249">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="9e196-250">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="9e196-250">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="9e196-251">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="9e196-251">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="9e196-252">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="9e196-252">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="9e196-253">eller</span><span class="sxs-lookup"><span data-stu-id="9e196-253">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="9e196-254">Kali</span><span class="sxs-lookup"><span data-stu-id="9e196-254">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-255">Kali-support stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="9e196-255">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="9e196-256">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="9e196-256">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="9e196-257">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="9e196-257">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="9e196-258">Raspbian</span><span class="sxs-lookup"><span data-stu-id="9e196-258">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="9e196-259">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="9e196-259">Raspbian support is experimental.</span></span>

<span data-ttu-id="9e196-260">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="9e196-260">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="9e196-261">CoreCLR och PowerShell fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="9e196-261">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="9e196-262">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="9e196-262">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="9e196-263">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="9e196-263">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="9e196-264">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till den `pwsh` binära filen.</span><span class="sxs-lookup"><span data-stu-id="9e196-264">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="9e196-265">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="9e196-265">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="installing-preview-releases"></a><span data-ttu-id="9e196-266">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="9e196-266">Installing Preview Releases</span></span>

<span data-ttu-id="9e196-267">När du installerar en PowerShell Preview-version för Linux via en paket lagrings plats ändras paket `powershell` namnet `powershell-preview`från till.</span><span class="sxs-lookup"><span data-stu-id="9e196-267">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="9e196-268">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="9e196-268">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="9e196-269">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="9e196-269">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="9e196-270">Distribution</span><span class="sxs-lookup"><span data-stu-id="9e196-270">Distribution(s)</span></span> |            <span data-ttu-id="9e196-271">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="9e196-271">Stable Command</span></span>            |               <span data-ttu-id="9e196-272">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="9e196-272">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="9e196-273">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="9e196-273">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="9e196-274">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="9e196-274">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="9e196-275">Fedora</span><span class="sxs-lookup"><span data-stu-id="9e196-275">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="9e196-276">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="9e196-276">Install as a .NET Global tool</span></span>

<span data-ttu-id="9e196-277">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="9e196-277">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="9e196-278">Installations programmet för dotNET- `~/.dotnet/tools` verktyget lägger `PATH` till i din miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="9e196-278">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="9e196-279">Men det gränssnitt som körs har inte uppdaterats `PATH`.</span><span class="sxs-lookup"><span data-stu-id="9e196-279">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="9e196-280">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="9e196-280">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="9e196-281">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9e196-281">Binary Archives</span></span>

<span data-ttu-id="9e196-282">PowerShell- `tar.gz` binärfiler finns för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="9e196-282">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="9e196-283">Beroenden</span><span class="sxs-lookup"><span data-stu-id="9e196-283">Dependencies</span></span>

<span data-ttu-id="9e196-284">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="9e196-284">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="9e196-285">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9e196-285">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="9e196-286">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="9e196-286">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="9e196-287">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="9e196-287">OS</span></span>                 | <span data-ttu-id="9e196-288">Beroenden</span><span class="sxs-lookup"><span data-stu-id="9e196-288">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="9e196-289">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="9e196-289">Ubuntu 16.04</span></span>       | <span data-ttu-id="9e196-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9e196-290">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9e196-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="9e196-291">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="9e196-292">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="9e196-292">Ubuntu 17.10</span></span>       | <span data-ttu-id="9e196-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9e196-293">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9e196-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="9e196-294">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="9e196-295">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="9e196-295">Ubuntu 18.04</span></span>       | <span data-ttu-id="9e196-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9e196-296">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9e196-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="9e196-297">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="9e196-298">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="9e196-298">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="9e196-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9e196-299">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9e196-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="9e196-300">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="9e196-301">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="9e196-301">Debian 9 (Stretch)</span></span> | <span data-ttu-id="9e196-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="9e196-302">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="9e196-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="9e196-303">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="9e196-304">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="9e196-304">CentOS 7</span></span> <br> <span data-ttu-id="9e196-305">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="9e196-305">Oracle Linux 7</span></span> <br> <span data-ttu-id="9e196-306">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="9e196-306">RHEL 7</span></span> | <span data-ttu-id="9e196-307">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="9e196-307">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="9e196-308">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="9e196-308">openSUSE 42.3</span></span> | <span data-ttu-id="9e196-309">libcurl4, libopenssl1_0_0 libicu52_1</span><span class="sxs-lookup"><span data-stu-id="9e196-309">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="9e196-310">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="9e196-310">openSUSE Leap 15</span></span> | <span data-ttu-id="9e196-311">libcurl4, libopenssl1_0_0 libicu60_2</span><span class="sxs-lookup"><span data-stu-id="9e196-311">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="9e196-312">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="9e196-312">Fedora 27</span></span> <br> <span data-ttu-id="9e196-313">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="9e196-313">Fedora 28</span></span> | <span data-ttu-id="9e196-314">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="9e196-314">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="9e196-315">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="9e196-315">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="9e196-316">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux `tar.gz` -arkivet.</span><span class="sxs-lookup"><span data-stu-id="9e196-316">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="9e196-317">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9e196-317">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="9e196-318">Linux</span><span class="sxs-lookup"><span data-stu-id="9e196-318">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="9e196-319">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="9e196-319">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="9e196-320">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="9e196-320">Paths</span></span>

- <span data-ttu-id="9e196-321">`$PSHOME` är `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="9e196-321">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="9e196-322">Användar profilerna kommer att läsas från`~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9e196-322">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="9e196-323">Standard profiler kommer att läsas från`$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="9e196-323">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="9e196-324">Användarens moduler kommer att läsas från`~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e196-324">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="9e196-325">Delade moduler kommer att läsas från`/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e196-325">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="9e196-326">Standardmoduler kommer att läsas från`$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="9e196-326">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="9e196-327">PSReadLine historik registreras i`~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="9e196-327">PSReadLine history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="9e196-328">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade `Microsoft.PowerShell_profile.ps1` profilerna finns på samma platser.</span><span class="sxs-lookup"><span data-stu-id="9e196-328">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="9e196-329">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="9e196-329">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[exekutiv]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
