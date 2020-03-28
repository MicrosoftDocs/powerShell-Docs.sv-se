---
title: Installera PowerShell i Linux
description: Information om hur du installerar PowerShell på olika Linux-distributioner
ms.date: 03/09/2020
ms.openlocfilehash: 0b15f3de5eba8f4f399f9be27b74469c8c5d1b67
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374916"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="11f87-103">Installera PowerShell i Linux</span><span class="sxs-lookup"><span data-stu-id="11f87-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="11f87-104">Stöder [Ubuntu 16,04][u16], [Ubuntu 18,04][u1804], [Ubuntu 18,10][u1810], [Ubuntu 19,04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42,3][opensuse], [openSUSE skottår 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora]och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="11f87-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="11f87-105">För Linux-distributioner som inte stöds officiellt kan du försöka installera PowerShell med hjälp av [PowerShell-Snap-paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="11f87-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="11f87-106">Du kan också prova att distribuera PowerShell-binärfiler direkt med hjälp av Linux [`tar.gz` arkivet][tar], men du måste konfigurera de nödvändiga beroendena baserat på operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="11f87-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="11f87-107">Alla paket är tillgängliga på vår GitHub- [releases][] -sida.</span><span class="sxs-lookup"><span data-stu-id="11f87-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="11f87-108">När paketet har installerats kör du `pwsh` från en Terminal.</span><span class="sxs-lookup"><span data-stu-id="11f87-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="11f87-109">Kör `pwsh-preview` om du har installerat en för [hands version](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="11f87-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-110">PowerShell 7 är en uppgradering på plats som tar bort PowerShell Core 6. x.</span><span class="sxs-lookup"><span data-stu-id="11f87-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="11f87-111">Mappen `/usr/local/microsoft/powershell/6` ersätts av `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="11f87-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="11f87-112">Om du behöver köra PowerShell 6 sida vid sida med PowerShell 7 installerar du om PowerShell 6 med hjälp av metoden för [binärt Arkiv](#binary-archives) .</span><span class="sxs-lookup"><span data-stu-id="11f87-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="11f87-113">Installera för hands versioner</span><span class="sxs-lookup"><span data-stu-id="11f87-113">Installing Preview Releases</span></span>

<span data-ttu-id="11f87-114">När du installerar en PowerShell Preview-version för Linux via en paket lagrings plats ändras paket namnet från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="11f87-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="11f87-115">Installation via direkt hämtning ändras inte, förutom fil namnet.</span><span class="sxs-lookup"><span data-stu-id="11f87-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="11f87-116">Följande tabell innehåller kommandon för att installera stabila och förhands gransknings paket med hjälp av de olika paket ansvariga:</span><span class="sxs-lookup"><span data-stu-id="11f87-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="11f87-117">Distribution (er)</span><span class="sxs-lookup"><span data-stu-id="11f87-117">Distribution(s)</span></span> |            <span data-ttu-id="11f87-118">Stabilt kommando</span><span class="sxs-lookup"><span data-stu-id="11f87-118">Stable Command</span></span>            |               <span data-ttu-id="11f87-119">Förhandsgranska kommando</span><span class="sxs-lookup"><span data-stu-id="11f87-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="11f87-120">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="11f87-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="11f87-121">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="11f87-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="11f87-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="11f87-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="11f87-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11f87-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="11f87-124">Installation via paket lagring – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="11f87-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="11f87-125">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11f87-126">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-126">The preferred method is as follows:</span></span>

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

<span data-ttu-id="11f87-127">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-128">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="11f87-129">Installation via direkt hämtning – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="11f87-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="11f87-130">Ladda ned Debian-paketet `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` från sidan [releases][] till Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-130">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="11f87-131">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="11f87-132">`dpkg -i` kommandot Miss lyckas med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="11f87-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="11f87-133">Nästa kommando, `apt-get install -f` löser problemen och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="11f87-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="11f87-134">Avinstallation – Ubuntu 16,04</span><span class="sxs-lookup"><span data-stu-id="11f87-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="11f87-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11f87-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="11f87-136">Installation via paket lagring – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="11f87-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="11f87-137">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11f87-138">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-138">The preferred method is as follows:</span></span>

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

<span data-ttu-id="11f87-139">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-140">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="11f87-141">Installation via direkt hämtning – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="11f87-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="11f87-142">Ladda ned Debian-paketet `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` från sidan [releases][] till Ubuntu-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-142">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="11f87-143">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="11f87-144">`dpkg -i` kommandot Miss lyckas med ouppfyllda-beroenden.</span><span class="sxs-lookup"><span data-stu-id="11f87-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="11f87-145">Nästa kommando, `apt-get install -f` löser problemen och Slutför konfigurationen av PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="11f87-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="11f87-146">Avinstallation – Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="11f87-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="11f87-147">Ubuntu 18,10</span><span class="sxs-lookup"><span data-stu-id="11f87-147">Ubuntu 18.10</span></span>

<span data-ttu-id="11f87-148">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="11f87-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="11f87-149">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="11f87-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-150">Ubuntu 18,10 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="11f87-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="11f87-151">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="11f87-151">Ubuntu 19.04</span></span>

<span data-ttu-id="11f87-152">Installationen stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="11f87-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="11f87-153">Instruktioner finns i [snapin-paket][snap].</span><span class="sxs-lookup"><span data-stu-id="11f87-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-154">Ubuntu 19,04 är en [tillfällig version](https://www.ubuntu.com/about/release-cycle) som [stöds av communityn](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="11f87-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="11f87-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="11f87-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="11f87-156">Installation via paket lagring – Debian 8</span><span class="sxs-lookup"><span data-stu-id="11f87-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="11f87-157">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11f87-158">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-158">The preferred method is as follows:</span></span>

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

<span data-ttu-id="11f87-159">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-160">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="11f87-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="11f87-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="11f87-162">Installation via paket lagring – Debian 9</span><span class="sxs-lookup"><span data-stu-id="11f87-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="11f87-163">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11f87-164">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-164">The preferred method is as follows:</span></span>

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

<span data-ttu-id="11f87-165">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-166">Efter registreringen kan du uppdatera PowerShell med `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="11f87-167">Installation via direkt hämtning – Debian 9</span><span class="sxs-lookup"><span data-stu-id="11f87-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="11f87-168">Ladda ned Debian-paketet `powershell_7.0.0-1.debian.9_amd64.deb` från sidan [releases][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-168">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="11f87-169">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="11f87-170">Avinstallation-Debian 9</span><span class="sxs-lookup"><span data-stu-id="11f87-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="11f87-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="11f87-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-172">Debian 10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="11f87-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository---debian-10"></a><span data-ttu-id="11f87-173">Installation via paket lagring – Debian 10</span><span class="sxs-lookup"><span data-stu-id="11f87-173">Installation via Package Repository - Debian 10</span></span>

<span data-ttu-id="11f87-174">PowerShell för Linux publiceras till paket Arkiv för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-174">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="11f87-175">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-175">The preferred method is as follows:</span></span>

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

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="11f87-176">Installation via direkt hämtning – Debian 10</span><span class="sxs-lookup"><span data-stu-id="11f87-176">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="11f87-177">Hämta paketet med tar. gz-paketet `powershell_7.0.0-linux-x64.tar.gz` från sidan [releases][] till Debian-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-177">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="11f87-178">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-178">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="alpine-39-and-310"></a><span data-ttu-id="11f87-179">Alpina 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="11f87-179">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-180">Alpine 3,9 och 3,10 stöds endast i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="11f87-180">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="11f87-181">Installation via direkt hämtning – Alpine 3,9 och 3,10</span><span class="sxs-lookup"><span data-stu-id="11f87-181">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="11f87-182">Hämta paketet tar. gz-paketet `powershell-7.0.0-linux-alpine-x64.tar.gz` från sidan [releases][] till Alpine Machine.</span><span class="sxs-lookup"><span data-stu-id="11f87-182">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="11f87-183">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-183">Then, in the terminal, execute the following commands:</span></span>

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

## <a name="centos-7"></a><span data-ttu-id="11f87-184">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11f87-184">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-185">Det här paketet fungerar på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="11f87-185">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="11f87-186">Installation via paketets lagrings plats (prioriterad) – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11f87-186">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="11f87-187">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-187">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11f87-188">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-188">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-189">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-189">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="11f87-190">Installation via direkt hämtning – CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11f87-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="11f87-191">Med [CentOS 7][]laddar du ned rpm-paketet `powershell-7.0.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till CentOS-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-191">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="11f87-192">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-192">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11f87-193">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="11f87-193">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="11f87-194">Avinstallation-CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11f87-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11f87-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11f87-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11f87-197">Installation via paketets lagrings plats (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11f87-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="11f87-198">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-198">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="11f87-199">Som superanvändare registrerar du Microsoft-lagringsplatsen en gång.</span><span class="sxs-lookup"><span data-stu-id="11f87-199">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="11f87-200">Efter registreringen kan du uppdatera PowerShell med `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="11f87-200">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11f87-201">Installation via direkt hämtning – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11f87-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="11f87-202">Hämta RPM-paketet `powershell-7.0.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till datorn Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="11f87-202">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="11f87-203">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-203">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11f87-204">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="11f87-204">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="11f87-205">Avinstallation-Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="11f87-205">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="11f87-206">openSUSE</span><span class="sxs-lookup"><span data-stu-id="11f87-206">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="11f87-207">Installation – openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="11f87-207">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="11f87-208">Installation – openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="11f87-208">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="11f87-209">Avinstallation – openSUSE 42,3, openSUSE skottår 15</span><span class="sxs-lookup"><span data-stu-id="11f87-209">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="11f87-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="11f87-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-211">Fedora 28 stöds endast i PowerShell 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="11f87-211">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-212">Fedora 29 och 30 stöds bara i PowerShell 7,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="11f87-212">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="11f87-213">Installation via paketets lagrings plats (prioriterad)-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="11f87-213">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="11f87-214">PowerShell för Linux publiceras till officiella Microsoft-databaser för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-214">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="11f87-215">Installation via direkt hämtning-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="11f87-215">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="11f87-216">Hämta RPM-paketet `powershell-7.0.0-1.rhel.7.x86_64.rpm` från sidan [releases][] till Fedora-datorn.</span><span class="sxs-lookup"><span data-stu-id="11f87-216">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="11f87-217">Kör sedan följande kommandon i terminalen:</span><span class="sxs-lookup"><span data-stu-id="11f87-217">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="11f87-218">Du kan installera RPM utan det mellanliggande steget i att ladda ned det:</span><span class="sxs-lookup"><span data-stu-id="11f87-218">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="11f87-219">Avinstallation-Fedora 28, 29 och 30</span><span class="sxs-lookup"><span data-stu-id="11f87-219">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="11f87-220">Båge Linux</span><span class="sxs-lookup"><span data-stu-id="11f87-220">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-221">Stöd för båge stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="11f87-221">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="11f87-222">PowerShell är tillgängligt från användar lagrings platsen för [Båge Linux][] (AUR).</span><span class="sxs-lookup"><span data-stu-id="11f87-222">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="11f87-223">Den kan kompileras med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="11f87-223">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="11f87-224">Den kan kompileras från det [senaste genomförandeet till Master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="11f87-224">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="11f87-225">Den kan installeras med den [senaste versionen av binärfilen][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="11f87-225">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="11f87-226">Paketen i AUR är grupperade. Det finns inget statligt stöd.</span><span class="sxs-lookup"><span data-stu-id="11f87-226">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="11f87-227">Mer information om hur du installerar paket från AUR finns i " [båge Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) " eller community- [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="11f87-227">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Båge Linux]: https://www.archlinux.org/download/
[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="11f87-229">Snapin-paket</span><span class="sxs-lookup"><span data-stu-id="11f87-229">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="11f87-230">Fäst</span><span class="sxs-lookup"><span data-stu-id="11f87-230">Getting snapd</span></span>

<span data-ttu-id="11f87-231">`snapd` krävs för att köra fästar.</span><span class="sxs-lookup"><span data-stu-id="11f87-231">`snapd` is required to run snaps.</span></span> <span data-ttu-id="11f87-232">Följ [dessa anvisningar](https://docs.snapcraft.io/core/install) för att kontrol lera att du har `snapd` installerat.</span><span class="sxs-lookup"><span data-stu-id="11f87-232">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="11f87-233">Installation via Snap</span><span class="sxs-lookup"><span data-stu-id="11f87-233">Installation via Snap</span></span>

<span data-ttu-id="11f87-234">PowerShell för Linux publiceras i [Snap Store](https://snapcraft.io/store) för enkel installation och uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="11f87-234">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="11f87-235">Den bästa metoden är följande:</span><span class="sxs-lookup"><span data-stu-id="11f87-235">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="11f87-236">Om du vill installera en för hands version använder du följande metod:</span><span class="sxs-lookup"><span data-stu-id="11f87-236">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="11f87-237">Efter installationen kommer Snap att uppgraderas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="11f87-237">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="11f87-238">Du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="11f87-238">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="11f87-239">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="11f87-239">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="11f87-240">eller</span><span class="sxs-lookup"><span data-stu-id="11f87-240">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="11f87-241">Kali</span><span class="sxs-lookup"><span data-stu-id="11f87-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-242">Kali-support stöds inte officiellt av Microsoft och underhålls av communityn.</span><span class="sxs-lookup"><span data-stu-id="11f87-242">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="11f87-243">Installation – Kali</span><span class="sxs-lookup"><span data-stu-id="11f87-243">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="11f87-244">Avinstallation – Kali</span><span class="sxs-lookup"><span data-stu-id="11f87-244">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="11f87-245">Raspbian</span><span class="sxs-lookup"><span data-stu-id="11f87-245">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="11f87-246">Raspbian-support är experimentell.</span><span class="sxs-lookup"><span data-stu-id="11f87-246">Raspbian support is experimental.</span></span>

<span data-ttu-id="11f87-247">För närvarande stöds PowerShell bara för Raspbian-sträckning.</span><span class="sxs-lookup"><span data-stu-id="11f87-247">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="11f87-248">CoreCLR och PowerShell fungerar bara på Pi 2-och PI 3-enheter som andra enheter, t. ex. [PI noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="11f87-248">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="11f87-249">Ladda ned [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) och följ [installations anvisningarna](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) för att hämta den till din PI.</span><span class="sxs-lookup"><span data-stu-id="11f87-249">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="11f87-250">Installation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="11f87-250">Installation - Raspbian</span></span>

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

<span data-ttu-id="11f87-251">Du kan också skapa en symboliska länk för att starta PowerShell utan att ange sökvägen till `pwsh` Binary.</span><span class="sxs-lookup"><span data-stu-id="11f87-251">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="11f87-252">Avinstallation – Raspbian</span><span class="sxs-lookup"><span data-stu-id="11f87-252">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="11f87-253">Installera som ett globalt .NET-verktyg</span><span class="sxs-lookup"><span data-stu-id="11f87-253">Install as a .NET Global tool</span></span>

<span data-ttu-id="11f87-254">Om du redan har installerat [.net Core SDK](/dotnet/core/sdk) är det enkelt att installera PowerShell som ett [globalt .net-verktyg](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="11f87-254">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="11f87-255">Installations programmet för dotNET-verktyget lägger till `~/.dotnet/tools` i din `PATH` miljö variabel.</span><span class="sxs-lookup"><span data-stu-id="11f87-255">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="11f87-256">Men det gränssnitt som körs har inte den uppdaterade `PATH`.</span><span class="sxs-lookup"><span data-stu-id="11f87-256">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="11f87-257">Du bör kunna starta PowerShell från ett nytt gränssnitt genom att skriva `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="11f87-257">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="11f87-258">Binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="11f87-258">Binary Archives</span></span>

<span data-ttu-id="11f87-259">PowerShell-binärfiler för `tar.gz` tillhandahålls för Linux-plattformar för att aktivera avancerade distributions scenarier.</span><span class="sxs-lookup"><span data-stu-id="11f87-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="11f87-260">Beroenden</span><span class="sxs-lookup"><span data-stu-id="11f87-260">Dependencies</span></span>

<span data-ttu-id="11f87-261">PowerShell skapar bärbara binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="11f87-261">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="11f87-262">.NET Core runtime kräver dock olika beroenden för olika distributioner, och även PowerShell.</span><span class="sxs-lookup"><span data-stu-id="11f87-262">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="11f87-263">Följande diagram visar de .NET Core 2,0-beroenden som stöds officiellt på olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="11f87-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="11f87-264">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="11f87-264">OS</span></span>                 | <span data-ttu-id="11f87-265">Beroenden</span><span class="sxs-lookup"><span data-stu-id="11f87-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="11f87-266">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="11f87-266">Ubuntu 16.04</span></span>       | <span data-ttu-id="11f87-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="11f87-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11f87-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="11f87-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="11f87-269">Ubuntu 17,10</span><span class="sxs-lookup"><span data-stu-id="11f87-269">Ubuntu 17.10</span></span>       | <span data-ttu-id="11f87-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="11f87-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11f87-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="11f87-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="11f87-272">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="11f87-272">Ubuntu 18.04</span></span>       | <span data-ttu-id="11f87-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="11f87-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11f87-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="11f87-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="11f87-275">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="11f87-275">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="11f87-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="11f87-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11f87-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="11f87-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="11f87-278">Debian 9 (sträck ut)</span><span class="sxs-lookup"><span data-stu-id="11f87-278">Debian 9 (Stretch)</span></span> | <span data-ttu-id="11f87-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="11f87-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="11f87-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl 1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="11f87-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="11f87-281">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="11f87-281">CentOS 7</span></span> <br> <span data-ttu-id="11f87-282">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="11f87-282">Oracle Linux 7</span></span> <br> <span data-ttu-id="11f87-283">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="11f87-283">RHEL 7</span></span> | <span data-ttu-id="11f87-284">libunwind, libsväng, OpenSSL-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="11f87-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="11f87-285">openSUSE 42,3</span><span class="sxs-lookup"><span data-stu-id="11f87-285">openSUSE 42.3</span></span> | <span data-ttu-id="11f87-286">libcurl4, libopenssl1_0_0 libicu52_1</span><span class="sxs-lookup"><span data-stu-id="11f87-286">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="11f87-287">openSUSE-skottår 15</span><span class="sxs-lookup"><span data-stu-id="11f87-287">openSUSE Leap 15</span></span> | <span data-ttu-id="11f87-288">libcurl4, libopenssl1_0_0 libicu60_2</span><span class="sxs-lookup"><span data-stu-id="11f87-288">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="11f87-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="11f87-289">Fedora 27</span></span> <br> <span data-ttu-id="11f87-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="11f87-290">Fedora 28</span></span> | <span data-ttu-id="11f87-291">libunwind, libsväng, OpenSSL-libs, libicu, kompatibilitet-openssl10</span><span class="sxs-lookup"><span data-stu-id="11f87-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="11f87-292">Om du vill distribuera PowerShell-binärfiler på Linux-distributioner som inte stöds officiellt måste du installera de nödvändiga beroendena för mål operativ systemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="11f87-292">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="11f87-293">Vårt [Amazon Linux-Dockerfile][amazon-dockerfile] installerar till exempel beroenden först och extraherar sedan Linux `tar.gz`-arkivet.</span><span class="sxs-lookup"><span data-stu-id="11f87-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="11f87-294">Installation – binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="11f87-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="11f87-295">Linux</span><span class="sxs-lookup"><span data-stu-id="11f87-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="11f87-296">Avinstallerar binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="11f87-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="11f87-297">Mappar</span><span class="sxs-lookup"><span data-stu-id="11f87-297">Paths</span></span>

- <span data-ttu-id="11f87-298">`$PSHOME` är `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="11f87-298">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="11f87-299">Användar profiler kommer att läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="11f87-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="11f87-300">Standard profiler kommer att läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="11f87-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="11f87-301">Användarens moduler kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="11f87-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="11f87-302">Delade moduler kommer att läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="11f87-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="11f87-303">Standardmoduler kommer att läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="11f87-303">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="11f87-304">PSReadline-historik registreras för `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="11f87-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="11f87-305">Profilerna respekterar PowerShell: s konfiguration per värd, så att de standardinställda värdbaserade profilerna finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="11f87-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="11f87-306">PowerShell respekterar [xdg-bas katalog specifikationen][xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="11f87-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
