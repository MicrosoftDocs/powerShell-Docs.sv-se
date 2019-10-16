---
title: Installera PowerShell Core i Linux
description: Information om hur du installerar PowerShell Core på olika Linux-distributioner
ms.date: 07/19/2019
ms.openlocfilehash: fc5a278f0fc10733a0d60fb856d0400332ba2719
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350196"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="353fc-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="353fc-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="353fc-104">Stöder [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE skottår 15 ][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="353fc-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="353fc-105">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="353fc-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="353fc-106">Du kan också prova att distribuera PowerShell-binärfiler direkt med hjälp av Linux [-`tar.gz`-arkivet][tar], men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="353fc-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="353fc-107">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="353fc-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="353fc-108">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="353fc-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="353fc-109">Kör `pwsh-preview` om du har installerat en för [hands version](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="353fc-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="353fc-110">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="353fc-110">Installing Preview Releases</span></span>

<span data-ttu-id="353fc-111">När du installerar en PowerShell Core Preview-version för Linux via en paket lagrings plats ändras paket namnet från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="353fc-111">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="353fc-112">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="353fc-112">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="353fc-113">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="353fc-113">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="353fc-114">Distribution (er)</span><span class="sxs-lookup"><span data-stu-id="353fc-114">Distribution(s)</span></span>|<span data-ttu-id="353fc-115">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="353fc-115">Stable Command</span></span> | <span data-ttu-id="353fc-116">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="353fc-116">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="353fc-117">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="353fc-117">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="353fc-118">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="353fc-118">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="353fc-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="353fc-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="353fc-120">Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="353fc-120">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="353fc-121">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="353fc-121">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="353fc-122">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-122">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="353fc-123">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="353fc-123">The preferred method is as follows:</span></span>

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

<span data-ttu-id="353fc-124">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-124">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-125">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-125">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="353fc-126">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="353fc-126">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="353fc-127">Ladda ned Debian-paketet `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` från sidan [releases][] till Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-127">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="353fc-128">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-128">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="353fc-129">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="353fc-129">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="353fc-130">Nästa kommando `apt-get install -f` löser problemen och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="353fc-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="353fc-131">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="353fc-131">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="353fc-132">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="353fc-132">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="353fc-133">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="353fc-133">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="353fc-134">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-134">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="353fc-135">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="353fc-135">The preferred method is as follows:</span></span>

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

<span data-ttu-id="353fc-136">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-136">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-137">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-137">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="353fc-138">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="353fc-138">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="353fc-139">Ladda ned Debian-paketet `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` från sidan [releases][] till Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-139">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="353fc-140">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-140">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="353fc-141">Kommandot `dpkg -i` kan inte utföras med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="353fc-141">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="353fc-142">Nästa kommando `apt-get install -f` löser problemen och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="353fc-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="353fc-143">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="353fc-143">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="353fc-144">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="353fc-144">Ubuntu 18.10</span></span>

<span data-ttu-id="353fc-145">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="353fc-145">Installation is supported via `snapd`.</span></span> <span data-ttu-id="353fc-146">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="353fc-146">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-147">Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="353fc-147">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="353fc-148">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="353fc-148">Ubuntu 19.04</span></span>

<span data-ttu-id="353fc-149">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="353fc-149">Installation is supported via `snapd`.</span></span> <span data-ttu-id="353fc-150">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="353fc-150">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-151">Ubuntu 19,04 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="353fc-151">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="353fc-152">Debian 8</span><span class="sxs-lookup"><span data-stu-id="353fc-152">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="353fc-153">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="353fc-153">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="353fc-154">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-154">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="353fc-155">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="353fc-155">The preferred method is as follows:</span></span>

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

<span data-ttu-id="353fc-156">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-156">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-157">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-157">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="353fc-158">Debian 9</span><span class="sxs-lookup"><span data-stu-id="353fc-158">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="353fc-159">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="353fc-159">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="353fc-160">PowerShell Core för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-160">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="353fc-161">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="353fc-161">The preferred method is as follows:</span></span>

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

<span data-ttu-id="353fc-162">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-162">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-163">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-163">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="353fc-164">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="353fc-164">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="353fc-165">Ladda ned Debian-paketet `powershell_6.2.0-1.debian.9_amd64.deb` från sidan [releases][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-165">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="353fc-166">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-166">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="353fc-167">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="353fc-167">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="353fc-168">Debian 10</span><span class="sxs-lookup"><span data-stu-id="353fc-168">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-169">Debian 10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="353fc-169">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="353fc-170">Installation via direkt hämtning – Debian 10</span><span class="sxs-lookup"><span data-stu-id="353fc-170">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="353fc-171">Ladda ned tar. gz-paketet `powershell_7.0.0-preview-7-linux-x64.tar.gz` från sidan [releases][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-171">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="353fc-172">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-172">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="353fc-173">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="353fc-173">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-174">Alpine 3,9 och 3,10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="353fc-174">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="353fc-175">Installation via direkt hämtning – Alpine 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="353fc-175">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="353fc-176">Ladda ned tar. gz-paketet `powershell_7.0.0-preview-7-linux-x64.tar.gz` från sidan [releases][] till Alpine Machine.</span><span class="sxs-lookup"><span data-stu-id="353fc-176">Download the tar.gz package `powershell_7.0.0-preview-7-linux-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="353fc-177">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-177">Then, in the terminal, execute the following commands:</span></span>

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
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0-preview.4/powershell-7.0.0-preview.4-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7-preview

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7-preview

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7-preview/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7-preview/pwsh /usr/bin/pwsh-preview

# Start PowerShell
pwsh-preview
```

## <a name="centos-7"></a><span data-ttu-id="353fc-178">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="353fc-178">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-179">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="353fc-179">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="353fc-180">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="353fc-180">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="353fc-181">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-181">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="353fc-182">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-182">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-183">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-183">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="353fc-184">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="353fc-184">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="353fc-185">Med [CentOS 7][]laddar du ned rpm-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-185">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="353fc-186">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-186">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="353fc-187">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="353fc-187">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="353fc-188">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="353fc-188">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="353fc-190">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="353fc-190">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="353fc-191">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="353fc-191">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="353fc-192">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="353fc-193">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="353fc-193">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="353fc-194">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="353fc-194">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="353fc-195">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="353fc-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="353fc-196">Ladda ned RPM-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till datorn Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="353fc-196">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="353fc-197">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-197">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="353fc-198">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="353fc-198">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="353fc-199">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="353fc-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="353fc-200">openSUSE</span><span class="sxs-lookup"><span data-stu-id="353fc-200">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="353fc-201">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="353fc-201">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="353fc-202">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="353fc-202">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="353fc-203">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="353fc-203">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="353fc-204">Fedora</span><span class="sxs-lookup"><span data-stu-id="353fc-204">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-205">Fedora 28 stöds endast i PowerShell Core 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="353fc-205">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-206">Fedora 29 och 30 stöds bara i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="353fc-206">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="353fc-207">Installation via paketets lagrings plats (prioriterad)-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="353fc-207">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="353fc-208">PowerShell Core för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-208">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="353fc-209">Installation via direkt hämtning-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="353fc-209">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="353fc-210">Ladda ned RPM-paketet `powershell-6.2.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="353fc-210">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="353fc-211">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="353fc-211">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="353fc-212">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="353fc-212">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="353fc-213">Avinstallation-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="353fc-213">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="353fc-214">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="353fc-214">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-215">Stöd för båge är experimentellt.</span><span class="sxs-lookup"><span data-stu-id="353fc-215">Arch support is experimental.</span></span>

<span data-ttu-id="353fc-216">PowerShell är tillgängligt från användar lagrings platsen för [Båge Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="353fc-216">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="353fc-217">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="353fc-217">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="353fc-218">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="353fc-218">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="353fc-219">Den kan installeras med den [senaste versionen av binärfilen][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="353fc-219">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="353fc-220">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="353fc-220">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="353fc-221">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller community- [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="353fc-221">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="353fc-223">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="353fc-223">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="353fc-224">Fäst</span><span class="sxs-lookup"><span data-stu-id="353fc-224">Getting snapd</span></span>

<span data-ttu-id="353fc-225">`snapd` krävs för att köra fäster.</span><span class="sxs-lookup"><span data-stu-id="353fc-225">`snapd` is required to run snaps.</span></span> <span data-ttu-id="353fc-226">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att du har installerat `snapd`.</span><span class="sxs-lookup"><span data-stu-id="353fc-226">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="353fc-227">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="353fc-227">Installation via Snap</span></span>

<span data-ttu-id="353fc-228">PowerShell Core för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="353fc-228">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="353fc-229">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="353fc-229">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="353fc-230">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="353fc-230">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="353fc-231">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="353fc-231">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="353fc-232">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="353fc-232">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="353fc-233">Avinstallationen</span><span class="sxs-lookup"><span data-stu-id="353fc-233">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="353fc-234">eller</span><span class="sxs-lookup"><span data-stu-id="353fc-234">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="353fc-235">Kali</span><span class="sxs-lookup"><span data-stu-id="353fc-235">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="353fc-236">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="353fc-236">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="353fc-237">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="353fc-237">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="353fc-238">Raspbian</span><span class="sxs-lookup"><span data-stu-id="353fc-238">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="353fc-239">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="353fc-239">Raspbian support is experimental.</span></span>

<span data-ttu-id="353fc-240">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="353fc-240">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="353fc-241">CoreCLR och PowerShell-kärnan fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="353fc-241">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="353fc-242">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="353fc-242">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="353fc-243">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="353fc-243">Installation - Raspbian</span></span>

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

<span data-ttu-id="353fc-244">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till `pwsh`-binärfilen.</span><span class="sxs-lookup"><span data-stu-id="353fc-244">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="353fc-245">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="353fc-245">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="353fc-246">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="353fc-246">Binary Archives</span></span>

<span data-ttu-id="353fc-247">PowerShell Binary `tar.gz`-Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="353fc-247">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="353fc-248">Relation</span><span class="sxs-lookup"><span data-stu-id="353fc-248">Dependencies</span></span>

<span data-ttu-id="353fc-249">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="353fc-249">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="353fc-250">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="353fc-250">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="353fc-251">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="353fc-251">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="353fc-252">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="353fc-252">OS</span></span>                 | <span data-ttu-id="353fc-253">Relation</span><span class="sxs-lookup"><span data-stu-id="353fc-253">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="353fc-254">Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="353fc-254">Ubuntu 16.04</span></span>       | <span data-ttu-id="353fc-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="353fc-255">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="353fc-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="353fc-256">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="353fc-257">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="353fc-257">Ubuntu 17.10</span></span>       | <span data-ttu-id="353fc-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="353fc-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="353fc-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="353fc-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="353fc-260">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="353fc-260">Ubuntu 18.04</span></span>       | <span data-ttu-id="353fc-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="353fc-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="353fc-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="353fc-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="353fc-263">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="353fc-263">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="353fc-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="353fc-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="353fc-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="353fc-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="353fc-266">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="353fc-266">Debian 9 (Stretch)</span></span> | <span data-ttu-id="353fc-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="353fc-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="353fc-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="353fc-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="353fc-269">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="353fc-269">CentOS 7</span></span> <br> <span data-ttu-id="353fc-270">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="353fc-270">Oracle Linux 7</span></span> <br> <span data-ttu-id="353fc-271">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="353fc-271">RHEL 7</span></span> | <span data-ttu-id="353fc-272">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="353fc-272">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="353fc-273">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="353fc-273">openSUSE 42.3</span></span> | <span data-ttu-id="353fc-274">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="353fc-274">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="353fc-275">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="353fc-275">openSUSE Leap 15</span></span> | <span data-ttu-id="353fc-276">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="353fc-276">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="353fc-277">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="353fc-277">Fedora 27</span></span> <br> <span data-ttu-id="353fc-278">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="353fc-278">Fedora 28</span></span> | <span data-ttu-id="353fc-279">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="353fc-279">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="353fc-280">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="353fc-280">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="353fc-281">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux-`tar.gz`-arkivet.</span><span class="sxs-lookup"><span data-stu-id="353fc-281">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="353fc-282">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="353fc-282">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="353fc-283">Linux</span><span class="sxs-lookup"><span data-stu-id="353fc-283">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="353fc-284">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="353fc-284">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="353fc-285">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="353fc-285">Paths</span></span>

* <span data-ttu-id="353fc-286">`$PSHOME` är `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="353fc-286">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="353fc-287">Användar profilerna kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="353fc-287">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="353fc-288">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="353fc-288">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="353fc-289">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="353fc-289">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="353fc-290">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="353fc-290">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="353fc-291">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="353fc-291">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="353fc-292">PSReadline-historik registreras i `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="353fc-292">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="353fc-293">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda standardspecifika Profilerna finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="353fc-293">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="353fc-294">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="353fc-294">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
