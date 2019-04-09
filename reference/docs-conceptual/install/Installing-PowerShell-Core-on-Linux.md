---
title: Installera PowerShell Core i Linux
description: Information om att installera PowerShell Core på olika Linux-distributioner
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293341"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e8903-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="e8903-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e8903-104">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04] [ u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [ openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], och [Båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e8903-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e8903-105">För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell Fäst paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="e8903-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="e8903-106">Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="e8903-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e8903-107">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="e8903-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e8903-108">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="e8903-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="e8903-109">Installera förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="e8903-109">Installing Preview Releases</span></span>

<span data-ttu-id="e8903-110">När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e8903-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e8903-111">Installerar via direct hämtning ändras inte, än namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="e8903-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e8903-112">Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:</span><span class="sxs-lookup"><span data-stu-id="e8903-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e8903-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="e8903-113">Distribution(s)</span></span>|<span data-ttu-id="e8903-114">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="e8903-114">Stable Command</span></span> | <span data-ttu-id="e8903-115">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="e8903-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e8903-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e8903-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e8903-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e8903-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e8903-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8903-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e8903-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8903-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e8903-120">Installationen via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8903-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e8903-121">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-122">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-122">This is the preferred method.</span></span>

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

<span data-ttu-id="e8903-123">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="e8903-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e8903-124">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="e8903-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e8903-125">Installationen via Direct hämtning - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8903-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e8903-126">Ladda ned Debian-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-126">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.14.04_amd64.deb`
<span data-ttu-id="e8903-127">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8903-128">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8903-129">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="e8903-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8903-130">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="e8903-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e8903-131">Uninstallation - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8903-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e8903-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8903-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e8903-133">Installationen via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8903-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e8903-134">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-135">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-135">This is the preferred method.</span></span>

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

<span data-ttu-id="e8903-136">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="e8903-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e8903-137">Installationen via Direct hämtning - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8903-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e8903-138">Ladda ned Debian-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-138">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.16.04_amd64.deb`
<span data-ttu-id="e8903-139">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8903-140">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8903-141">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="e8903-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8903-142">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="e8903-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e8903-143">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8903-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e8903-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8903-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e8903-145">Installationen via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8903-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e8903-146">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-147">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-147">This is the preferred method.</span></span>

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

<span data-ttu-id="e8903-148">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="e8903-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e8903-149">Installationen via Direct hämtning - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8903-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e8903-150">Ladda ned Debian-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-150">Download the Debian package</span></span>
`powershell_6.2.0-1.ubuntu.18.04_amd64.deb`
<span data-ttu-id="e8903-151">från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e8903-152">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e8903-153">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="e8903-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e8903-154">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="e8903-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e8903-155">Avinstallationen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8903-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e8903-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e8903-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="e8903-157">Eftersom 18.10 är en [tillfälliga versionen](https://www.ubuntu.com/about/release-cycle), det är bara [community stöds](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="e8903-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="e8903-158">Installera på 18.10 stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e8903-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="e8903-159">Se [Fäst paketet] [ snap] fullständiga instruktioner;</span><span class="sxs-lookup"><span data-stu-id="e8903-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="e8903-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8903-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e8903-161">Installationen via Paketdatabasen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="e8903-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e8903-162">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-163">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-163">This is the preferred method.</span></span>

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

<span data-ttu-id="e8903-164">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="e8903-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="e8903-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8903-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e8903-166">Installationen via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8903-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e8903-167">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-168">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-168">This is the preferred method.</span></span>

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

<span data-ttu-id="e8903-169">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="e8903-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e8903-170">Installationen via Direct hämtning - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8903-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e8903-171">Ladda ned Debian-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-171">Download the Debian package</span></span>
`powershell_6.2.0-1.debian.9_amd64.deb`
<span data-ttu-id="e8903-172">från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e8903-173">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e8903-174">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="e8903-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e8903-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e8903-176">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e8903-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e8903-177">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e8903-178">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8903-179">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8903-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e8903-180">Installationen via Direct hämtning - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e8903-181">Med hjälp av [CentOS 7][], ladda ned RPM-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-181">Using [CentOS 7][], download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="e8903-182">från den [släpper][] sidan på CentOS-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e8903-183">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8903-184">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="e8903-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e8903-185">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[<span data-ttu-id="e8903-186">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-186">CentOS 7</span></span>]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8903-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8903-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8903-188">Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8903-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8903-189">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e8903-190">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8903-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8903-191">Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8903-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e8903-192">Ladda ned RPM-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-192">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="e8903-193">från den [släpper][] sidan på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e8903-194">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8903-195">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="e8903-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e8903-196">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e8903-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e8903-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e8903-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e8903-198">Installation - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e8903-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e8903-199">Installation - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8903-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e8903-200">Avinstallationen - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8903-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e8903-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8903-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e8903-202">Fedora 28 stöds bara i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="e8903-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e8903-203">Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8903-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e8903-204">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e8903-205">Installationen via Direct hämtning - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8903-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e8903-206">Ladda ned RPM-paket</span><span class="sxs-lookup"><span data-stu-id="e8903-206">Download the RPM package</span></span>
`powershell-6.2.0-1.rhel.7.x86_64.rpm`
<span data-ttu-id="e8903-207">från den [släpper][] sidan på Fedora-dator.</span><span class="sxs-lookup"><span data-stu-id="e8903-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e8903-208">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="e8903-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e8903-209">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="e8903-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e8903-210">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8903-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e8903-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e8903-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e8903-212">Stöd för arch är experimentella.</span><span class="sxs-lookup"><span data-stu-id="e8903-212">Arch support is experimental.</span></span>

<span data-ttu-id="e8903-213">PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).</span><span class="sxs-lookup"><span data-stu-id="e8903-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e8903-214">Den kan sammanställas med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e8903-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e8903-215">Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e8903-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e8903-216">Den kan installeras med den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e8903-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e8903-217">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="e8903-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e8903-218">Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e8903-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[<span data-ttu-id="e8903-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e8903-219">Arch Linux</span></span>]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e8903-220">Fäst paket</span><span class="sxs-lookup"><span data-stu-id="e8903-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e8903-221">Hämta snapd</span><span class="sxs-lookup"><span data-stu-id="e8903-221">Getting snapd</span></span>

`snapd` <span data-ttu-id="e8903-222">krävs för att köra fäster.</span><span class="sxs-lookup"><span data-stu-id="e8903-222">is required to run snaps.</span></span>
<span data-ttu-id="e8903-223">Använd [instruktionerna](https://docs.snapcraft.io/core/install) att kontrollera att du har `snapd` installerad.</span><span class="sxs-lookup"><span data-stu-id="e8903-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e8903-224">Installationen via snapin</span><span class="sxs-lookup"><span data-stu-id="e8903-224">Installation via Snap</span></span>

<span data-ttu-id="e8903-225">PowerShell Core för Linux, publiceras till den [snapin store](https://snapcraft.io/store) för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="e8903-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="e8903-226">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e8903-227">Om du vill installera förhandsversionen kan du använda följande metod.</span><span class="sxs-lookup"><span data-stu-id="e8903-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e8903-228">När du installerar snapin uppgraderar automatiskt, men du kan utlösa en uppgradering med `sudo snap refresh powershell` eller `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e8903-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e8903-229">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="e8903-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e8903-230">eller</span><span class="sxs-lookup"><span data-stu-id="e8903-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e8903-231">Kali</span><span class="sxs-lookup"><span data-stu-id="e8903-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e8903-232">Installation - Kali</span><span class="sxs-lookup"><span data-stu-id="e8903-232">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="e8903-233">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="e8903-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e8903-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8903-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e8903-235">Stöd för Raspbian är experimentella.</span><span class="sxs-lookup"><span data-stu-id="e8903-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="e8903-236">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e8903-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e8903-237">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="e8903-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e8903-238">Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.</span><span class="sxs-lookup"><span data-stu-id="e8903-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e8903-239">Installation - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8903-239">Installation - Raspbian</span></span>

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

<span data-ttu-id="e8903-240">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära</span><span class="sxs-lookup"><span data-stu-id="e8903-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e8903-241">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="e8903-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e8903-242">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="e8903-242">Binary Archives</span></span>

<span data-ttu-id="e8903-243">PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="e8903-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e8903-244">Beroenden</span><span class="sxs-lookup"><span data-stu-id="e8903-244">Dependencies</span></span>

<span data-ttu-id="e8903-245">PowerShell skapar bärbar binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="e8903-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e8903-246">Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="e8903-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e8903-247">Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="e8903-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e8903-248">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="e8903-248">OS</span></span>                 | <span data-ttu-id="e8903-249">Beroenden</span><span class="sxs-lookup"><span data-stu-id="e8903-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e8903-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e8903-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="e8903-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e8903-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e8903-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e8903-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="e8903-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e8903-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e8903-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e8903-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="e8903-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8903-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e8903-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e8903-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="e8903-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e8903-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e8903-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e8903-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e8903-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e8903-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e8903-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e8903-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e8903-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span><span class="sxs-lookup"><span data-stu-id="e8903-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e8903-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e8903-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e8903-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e8903-268">CentOS 7</span></span> <br> <span data-ttu-id="e8903-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e8903-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="e8903-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e8903-270">RHEL 7</span></span> | <span data-ttu-id="e8903-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e8903-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e8903-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e8903-272">openSUSE 42.3</span></span> | <span data-ttu-id="e8903-273">libcurl4 libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e8903-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e8903-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e8903-274">openSUSE Leap 15</span></span> | <span data-ttu-id="e8903-275">libcurl4 libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e8903-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e8903-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e8903-276">Fedora 27</span></span> <br> <span data-ttu-id="e8903-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e8903-277">Fedora 28</span></span> | <span data-ttu-id="e8903-278">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="e8903-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e8903-279">Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="e8903-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e8903-280">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="e8903-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e8903-281">Installation - binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="e8903-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e8903-282">Linux</span><span class="sxs-lookup"><span data-stu-id="e8903-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e8903-283">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="e8903-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e8903-284">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="e8903-284">Paths</span></span>

* `$PSHOME` <span data-ttu-id="e8903-285">is</span><span class="sxs-lookup"><span data-stu-id="e8903-285">is</span></span> `/opt/microsoft/powershell/6.2.0/`
* <span data-ttu-id="e8903-286">Användarprofiler som ska läsas från</span><span class="sxs-lookup"><span data-stu-id="e8903-286">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="e8903-287">Standardprofiler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="e8903-287">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="e8903-288">Moduler som användaren kommer att läsas från</span><span class="sxs-lookup"><span data-stu-id="e8903-288">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="e8903-289">Delade moduler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="e8903-289">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="e8903-290">Standardmoduler ska läsas från</span><span class="sxs-lookup"><span data-stu-id="e8903-290">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="e8903-291">PSReadline historik kommer att läggas till</span><span class="sxs-lookup"><span data-stu-id="e8903-291">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="e8903-292">Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="e8903-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e8903-293">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="e8903-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[<span data-ttu-id="e8903-294">Versioner</span><span class="sxs-lookup"><span data-stu-id="e8903-294">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
