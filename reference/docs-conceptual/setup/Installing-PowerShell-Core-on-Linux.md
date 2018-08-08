---
title: Installera PowerShell Core i Linux
description: Information om att installera PowerShell Core på olika Linux-distributioner
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587456"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="6d127-103">Installera PowerShell Core i Linux</span><span class="sxs-lookup"><span data-stu-id="6d127-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="6d127-104">Stöder [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10] [ u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7] [ cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27 ] [ fedora], [Fedora 28][fedora], och [båge Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="6d127-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="6d127-105">För Linux-distributioner som inte stöds officiellt, kan du försöka använda den [PowerShell Fäst paketet][snap].</span><span class="sxs-lookup"><span data-stu-id="6d127-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="6d127-106">Du kan också prova att distribuera PowerShell binärfiler direkt med hjälp av Linux [ `tar.gz` Arkiv][tar], men du måste ställa in nödvändiga beroenden baserat på Operativsystemet i separata steg.</span><span class="sxs-lookup"><span data-stu-id="6d127-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="6d127-107">Alla paket finns på vår GitHub [släpper][] sidan.</span><span class="sxs-lookup"><span data-stu-id="6d127-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="6d127-108">När paketet har installerats kan du köra `pwsh` från en terminal.</span><span class="sxs-lookup"><span data-stu-id="6d127-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

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

## <a name="installing-preview-releases"></a><span data-ttu-id="6d127-109">Installera förhandsversioner</span><span class="sxs-lookup"><span data-stu-id="6d127-109">Installing Preview Releases</span></span>

<span data-ttu-id="6d127-110">När du installerar en förhandsversionen i PowerShell Core för Linux via en Paketdatabas paketnamnet ändras från `powershell` till `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6d127-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="6d127-111">Installerar via direct hämtning ändras inte, än namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="6d127-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="6d127-112">Här är en tabell med kommandon för att installera de stabila och förhandsversion paketen med olika pakethanterare:</span><span class="sxs-lookup"><span data-stu-id="6d127-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="6d127-113">Distribution(s)</span><span class="sxs-lookup"><span data-stu-id="6d127-113">Distribution(s)</span></span>|<span data-ttu-id="6d127-114">Stabil kommando</span><span class="sxs-lookup"><span data-stu-id="6d127-114">Stable Command</span></span> | <span data-ttu-id="6d127-115">Förhandsgranskningskommandot</span><span class="sxs-lookup"><span data-stu-id="6d127-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="6d127-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="6d127-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="6d127-117">CentOS, Red Hat</span><span class="sxs-lookup"><span data-stu-id="6d127-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="6d127-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6d127-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="6d127-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d127-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="6d127-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d127-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="6d127-121">Installationen via Paketdatabasen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d127-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="6d127-122">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-123">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-123">This is the preferred method.</span></span>

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

<span data-ttu-id="6d127-124">Som superanvändare, registrera Microsoft-databasen.</span><span class="sxs-lookup"><span data-stu-id="6d127-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="6d127-125">Därefter behöver du bara använda `sudo apt-get upgrade powershell` att uppdatera installationen.</span><span class="sxs-lookup"><span data-stu-id="6d127-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="6d127-126">Installationen via Direct hämtning - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d127-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="6d127-127">Ladda ned Debian-paket `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-127">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6d127-128">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6d127-129">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="6d127-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6d127-130">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="6d127-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="6d127-131">Avinstallationen - Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d127-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="6d127-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6d127-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="6d127-133">Installationen via Paketdatabasen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6d127-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="6d127-134">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-135">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-135">This is the preferred method.</span></span>

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

<span data-ttu-id="6d127-136">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="6d127-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="6d127-137">Installationen via Direct hämtning - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6d127-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="6d127-138">Ladda ned Debian-paket `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-138">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6d127-139">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-139">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6d127-140">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="6d127-140">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6d127-141">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="6d127-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="6d127-142">Avinstallationen - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6d127-142">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="6d127-143">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6d127-143">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-144">Stöd för Ubuntu 18.04 har lagts till efter `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="6d127-144">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="6d127-145">Installationen via Paketdatabasen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6d127-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="6d127-146">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-147">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-147">This is the preferred method.</span></span>

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

<span data-ttu-id="6d127-148">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="6d127-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="6d127-149">Installationen via Direct hämtning - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6d127-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="6d127-150">Ladda ned Debian-paket `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` från den [släpper][] sidan på Ubuntu-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-150">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="6d127-151">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-151">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6d127-152">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="6d127-152">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6d127-153">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="6d127-153">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="6d127-154">Avinstallationen - Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6d127-154">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="6d127-155">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="6d127-155">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-156">Stöd för Ubuntu 18.10 har lagts till efter `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="6d127-156">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="6d127-157">Eftersom 18.10 är en daglig version, är det bara community stöds.</span><span class="sxs-lookup"><span data-stu-id="6d127-157">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="6d127-158">Installera på 18.10 stöds via `snapd`.</span><span class="sxs-lookup"><span data-stu-id="6d127-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="6d127-159">Se [Fäst paketet] [ snap] fullständiga instruktioner;</span><span class="sxs-lookup"><span data-stu-id="6d127-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="6d127-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="6d127-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="6d127-161">Installationen via Paketdatabasen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="6d127-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="6d127-162">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-163">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-163">This is the preferred method.</span></span>

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

<span data-ttu-id="6d127-164">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="6d127-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="6d127-165">Installationen via Direct hämtning – Debian 8</span><span class="sxs-lookup"><span data-stu-id="6d127-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="6d127-166">Ladda ned Debian-paket `powershell_6.0.2-1.debian.8_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-166">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6d127-167">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-167">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="6d127-168">Den `dpkg -i` kommandot misslyckas med motsvarar hittills ouppfyllda beroenden.</span><span class="sxs-lookup"><span data-stu-id="6d127-168">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="6d127-169">Nästa kommando `apt-get install -f` löser dessa problem och sedan på Slutför PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="6d127-169">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="6d127-170">Avinstallationen – Debian 8</span><span class="sxs-lookup"><span data-stu-id="6d127-170">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="6d127-171">Debian 9</span><span class="sxs-lookup"><span data-stu-id="6d127-171">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="6d127-172">Installationen via Paketdatabasen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="6d127-172">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="6d127-173">PowerShell Core för Linux, publiceras till paketet lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-173">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-174">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-174">This is the preferred method.</span></span>

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

<span data-ttu-id="6d127-175">När du har registrerat Microsoft-databasen en gång som superanvändare, kommer du bara behöver använda `sudo apt-get upgrade powershell` att uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="6d127-175">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="6d127-176">Installationen via Direct hämtning - Debian 9</span><span class="sxs-lookup"><span data-stu-id="6d127-176">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="6d127-177">Ladda ned Debian-paket `powershell_6.0.2-1.debian.9_amd64.deb` från den [släpper][] sidan på Debian dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-177">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="6d127-178">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-178">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="6d127-179">Avinstallationen - Debian 9</span><span class="sxs-lookup"><span data-stu-id="6d127-179">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="6d127-180">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d127-180">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-181">Det här paketet fungerar även på Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="6d127-181">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="6d127-182">Installationen via Paketdatabasen (rekommenderas) - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d127-182">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="6d127-183">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-183">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6d127-184">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d127-184">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="6d127-185">Installationen via Direct hämtning - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d127-185">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="6d127-186">Med hjälp av [CentOS 7][], hämtningspaketet RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på CentOS-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-186">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="6d127-187">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-187">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6d127-188">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="6d127-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="6d127-189">Avinstallationen - CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d127-189">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6d127-191">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6d127-191">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6d127-192">Installationen via Paketdatabasen (rekommenderas) – Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6d127-192">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6d127-193">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-193">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="6d127-194">När du har registrerat Microsoft-databasen en gång som superanvändare, behöver du bara använda `sudo yum update powershell` att uppdatera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6d127-194">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6d127-195">Installationen via Direct hämtning - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6d127-195">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="6d127-196">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Red Hat Enterprise Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-196">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="6d127-197">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-197">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6d127-198">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="6d127-198">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="6d127-199">Avinstallationen - Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="6d127-199">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="6d127-200">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6d127-200">OpenSUSE 42.3</span></span>

<span data-ttu-id="6d127-201">När du installerar PowerShell Core `zypper` kan rapportera följande fel:</span><span class="sxs-lookup"><span data-stu-id="6d127-201">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="6d127-202">I det här fallet kontrollerar du att en kompatibel `libcurl` biblioteket finns genom att kontrollera att följande kommando visar den `libcurl4` paketera som installerade:</span><span class="sxs-lookup"><span data-stu-id="6d127-202">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="6d127-203">Välj sedan den `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` lösning när du installerar PowerShell-paketet.</span><span class="sxs-lookup"><span data-stu-id="6d127-203">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="6d127-204">Installationen via Paketdatabasen (rekommenderas) - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6d127-204">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="6d127-205">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-205">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="6d127-206">Installationen via Direct hämtning - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6d127-206">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="6d127-207">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på OpenSUSE-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-207">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6d127-208">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="6d127-208">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="6d127-209">Avinstallationen - OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6d127-209">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="6d127-210">Fedora</span><span class="sxs-lookup"><span data-stu-id="6d127-210">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-211">Fedora 28 stöds bara i PowerShell Core 6.1 och senare.</span><span class="sxs-lookup"><span data-stu-id="6d127-211">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="6d127-212">Installationen via Paketdatabasen (rekommenderas) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6d127-212">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="6d127-213">PowerShell Core för Linux publiceras till den officiella Microsoft lagringsplatser för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-213">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="6d127-214">Installationen via Direct hämtning - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6d127-214">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="6d127-215">Ladda ned RPM-paket `powershell-6.0.2-1.rhel.7.x86_64.rpm` från den [släpper][] sidan på Fedora-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-215">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="6d127-216">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-216">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="6d127-217">Du kan också installera RPM utan mellanliggande steg för att hämta den:</span><span class="sxs-lookup"><span data-stu-id="6d127-217">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="6d127-218">Avinstallationen - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6d127-218">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="6d127-219">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="6d127-219">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-220">Stöd för arch är experimentella.</span><span class="sxs-lookup"><span data-stu-id="6d127-220">Arch support is experimental.</span></span>

<span data-ttu-id="6d127-221">PowerShell är tillgänglig från den [Arch Linux][] användaren lagringsplats (AUR).</span><span class="sxs-lookup"><span data-stu-id="6d127-221">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="6d127-222">Den kan sammanställas med den [senaste taggade versionen][arch-release]</span><span class="sxs-lookup"><span data-stu-id="6d127-222">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="6d127-223">Den kan sammanställas från den [den senaste incheckningen till master-databasen][arch-git]</span><span class="sxs-lookup"><span data-stu-id="6d127-223">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="6d127-224">Den kan installeras med den [senaste versionen binär][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="6d127-224">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="6d127-225">Paket i AUR är community underhålls - stöds inte officiellt.</span><span class="sxs-lookup"><span data-stu-id="6d127-225">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="6d127-226">Mer information om hur du installerar paket från AUR finns i den [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) eller communityn [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="6d127-226">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="6d127-228">Fäst paket</span><span class="sxs-lookup"><span data-stu-id="6d127-228">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="6d127-229">Hämta snapd</span><span class="sxs-lookup"><span data-stu-id="6d127-229">Getting snapd</span></span>

<span data-ttu-id="6d127-230">`snapd` krävs för att köra fäster.</span><span class="sxs-lookup"><span data-stu-id="6d127-230">`snapd` is required to run snaps.</span></span>  <span data-ttu-id="6d127-231">Använd [instruktionerna](https://docs.snapcraft.io/core/install) att kontrollera att du har `snapd` installerad.</span><span class="sxs-lookup"><span data-stu-id="6d127-231">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="6d127-232">Installationen via snapin</span><span class="sxs-lookup"><span data-stu-id="6d127-232">Installation via Snap</span></span>

<span data-ttu-id="6d127-233">PowerShell Core för Linux, publiceras till den [snapin store](https://snapcraft.io/store) för enkel installation (och uppdateringar).</span><span class="sxs-lookup"><span data-stu-id="6d127-233">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="6d127-234">Detta är föredragen metod.</span><span class="sxs-lookup"><span data-stu-id="6d127-234">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="6d127-235">När du installerar snapin uppgraderar automatiskt, men du kan utlösa en uppgradering med `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="6d127-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="6d127-236">Avinstallation</span><span class="sxs-lookup"><span data-stu-id="6d127-236">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a><span data-ttu-id="6d127-237">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="6d127-237">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-238">AppImage support är experimentella</span><span class="sxs-lookup"><span data-stu-id="6d127-238">AppImage support is experimental</span></span>

<span data-ttu-id="6d127-239">Med hjälp av en nyligen Linux-distribution, ladda ned AppImage `powershell-6.0.1-x86_64.AppImage` från den [släpper][] sidan på Linux-dator.</span><span class="sxs-lookup"><span data-stu-id="6d127-239">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="6d127-240">Kör sedan följande i terminalen:</span><span class="sxs-lookup"><span data-stu-id="6d127-240">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="6d127-241">Den [AppImage][] kan du köra PowerShell utan att installera den.</span><span class="sxs-lookup"><span data-stu-id="6d127-241">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="6d127-242">Det är en bärbar program som samlar PowerShell och dess beroenden (inklusive .NET Core systemberoenden) till ett sammanhängande paket.</span><span class="sxs-lookup"><span data-stu-id="6d127-242">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="6d127-243">Det här paketet är ett enda Binärvärde som fungerar oberoende av användarens Linux-distribution.</span><span class="sxs-lookup"><span data-stu-id="6d127-243">This package is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="6d127-245">Kali</span><span class="sxs-lookup"><span data-stu-id="6d127-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-246">Stöd för kali är experimentella.</span><span class="sxs-lookup"><span data-stu-id="6d127-246">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="6d127-247">Installation</span><span class="sxs-lookup"><span data-stu-id="6d127-247">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="6d127-248">Kör PowerShell i senaste Kali (Kali GNU/Linux rullande) utan att installera den</span><span class="sxs-lookup"><span data-stu-id="6d127-248">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="6d127-249">Avinstallationen - Kali</span><span class="sxs-lookup"><span data-stu-id="6d127-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="6d127-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="6d127-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="6d127-251">Stöd för Raspbian är experimentella.</span><span class="sxs-lookup"><span data-stu-id="6d127-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="6d127-252">För närvarande stöds endast PowerShell på Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="6d127-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="6d127-253">Även CoreCLR (och därmed PowerShell Core) fungerar bara på Pi 2 och Pi 3-enheter som andra enheter, t.ex [Pi noll](https://github.com/dotnet/coreclr/issues/10605), har en processor som stöds inte.</span><span class="sxs-lookup"><span data-stu-id="6d127-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="6d127-254">Ladda ned [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) och följ de [Installationsinstruktioner](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) att hämta den till din Pi.</span><span class="sxs-lookup"><span data-stu-id="6d127-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="6d127-255">Installation</span><span class="sxs-lookup"><span data-stu-id="6d127-255">Installation</span></span>

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

<span data-ttu-id="6d127-256">Du kan också skapa en symbolisk länk för att kunna starta PowerShell utan att ange sökvägen till den ”pwsh” binära</span><span class="sxs-lookup"><span data-stu-id="6d127-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="6d127-257">Avinstallationen - Raspbian</span><span class="sxs-lookup"><span data-stu-id="6d127-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="6d127-258">Binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="6d127-258">Binary Archives</span></span>

<span data-ttu-id="6d127-259">PowerShell-binär `tar.gz` Arkiv tillhandahålls för Linux-plattformar för att aktivera avancerade scenarier.</span><span class="sxs-lookup"><span data-stu-id="6d127-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="6d127-260">Beroenden</span><span class="sxs-lookup"><span data-stu-id="6d127-260">Dependencies</span></span>

<span data-ttu-id="6d127-261">PowerShell skapar bärbar binärfiler för alla Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="6d127-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="6d127-262">Men .NET Core runtime kräver olika beroenden på olika distributioner och kan därför PowerShell gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="6d127-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="6d127-263">Följande diagram visar de beroenden i .NET Core 2.0 som officiellt stöds i olika Linux-distributioner.</span><span class="sxs-lookup"><span data-stu-id="6d127-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="6d127-264">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="6d127-264">OS</span></span>                 | <span data-ttu-id="6d127-265">Beroenden</span><span class="sxs-lookup"><span data-stu-id="6d127-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="6d127-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="6d127-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="6d127-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="6d127-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="6d127-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="6d127-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="6d127-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="6d127-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="6d127-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="6d127-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="6d127-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="6d127-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="6d127-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="6d127-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="6d127-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="6d127-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="6d127-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="6d127-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="6d127-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="6d127-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="6d127-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="6d127-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="6d127-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc ++ 6,</span><span class="sxs-lookup"><span data-stu-id="6d127-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="6d127-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="6d127-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="6d127-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="6d127-284">CentOS 7</span></span> <br> <span data-ttu-id="6d127-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="6d127-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="6d127-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="6d127-286">RHEL 7</span></span> <br> <span data-ttu-id="6d127-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="6d127-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="6d127-288">libunwind, libcurl, openssl-bibliotek, libicu</span><span class="sxs-lookup"><span data-stu-id="6d127-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="6d127-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="6d127-289">Fedora 27</span></span> <br> <span data-ttu-id="6d127-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="6d127-290">Fedora 28</span></span> | <span data-ttu-id="6d127-291">libunwind, libcurl, openssl-bibliotek, libicu, kompatibilitets-openssl10</span><span class="sxs-lookup"><span data-stu-id="6d127-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="6d127-292">Du måste installera de nödvändiga beroendena för målets OS i separata steg för att distribuera PowerShell-binärfiler i Linux-distributioner som inte stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="6d127-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="6d127-293">Till exempel vår [Amazon Linux dockerfile] [ amazon-dockerfile] installerar beroenden först och sedan extraherar Linux `tar.gz` Arkiv.</span><span class="sxs-lookup"><span data-stu-id="6d127-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="6d127-294">Installation - binär Arkiv</span><span class="sxs-lookup"><span data-stu-id="6d127-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="6d127-295">Linux</span><span class="sxs-lookup"><span data-stu-id="6d127-295">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="6d127-296">Avinstallera binära Arkiv</span><span class="sxs-lookup"><span data-stu-id="6d127-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="6d127-297">Sökvägar</span><span class="sxs-lookup"><span data-stu-id="6d127-297">Paths</span></span>

* <span data-ttu-id="6d127-298">`$PSHOME` är `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="6d127-298">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="6d127-299">Användarprofiler som ska läsas från `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6d127-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="6d127-300">Standardprofiler ska läsas från `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="6d127-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="6d127-301">Moduler som användaren kommer att läsas från `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d127-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6d127-302">Delade moduler ska läsas från `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d127-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="6d127-303">Standardmoduler ska läsas från `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="6d127-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="6d127-304">PSReadline historik kommer att läggas till `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="6d127-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="6d127-305">Profilerna respekterar PowerShell-per-host-konfiguration, så värdspecifika standardprofiler finns på `Microsoft.PowerShell_profile.ps1` på samma platser.</span><span class="sxs-lookup"><span data-stu-id="6d127-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="6d127-306">PowerShell respekterar de [XDG Base Directory specifikationen] [ xdg-bds] i Linux.</span><span class="sxs-lookup"><span data-stu-id="6d127-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[släpper]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
