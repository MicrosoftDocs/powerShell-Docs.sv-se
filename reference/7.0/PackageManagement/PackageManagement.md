---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113634
Help Version: 7.0.1.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 01b1bce187cd0526e56abc812f91b44a2c022a29
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890863"
---
# <span data-ttu-id="b97c3-103">PackageManagement-modul</span><span class="sxs-lookup"><span data-stu-id="b97c3-103">PackageManagement Module</span></span>

## <span data-ttu-id="b97c3-104">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b97c3-104">Description</span></span>

<span data-ttu-id="b97c3-105">I det här avsnittet visas hjälp avsnitt för Package Management-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b97c3-105">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b97c3-106">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="b97c3-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b97c3-107">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b97c3-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b97c3-108">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="b97c3-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b97c3-109">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="b97c3-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="b97c3-110">PackageManagement-cmdletar</span><span class="sxs-lookup"><span data-stu-id="b97c3-110">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="b97c3-111">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="b97c3-111">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="b97c3-112">Söker efter program varu paket i tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="b97c3-112">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="b97c3-113">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b97c3-113">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="b97c3-114">Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.</span><span class="sxs-lookup"><span data-stu-id="b97c3-114">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="b97c3-115">Get-Package</span><span class="sxs-lookup"><span data-stu-id="b97c3-115">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="b97c3-116">Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="b97c3-116">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="b97c3-117">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b97c3-117">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="b97c3-118">Returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="b97c3-118">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="b97c3-119">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b97c3-119">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="b97c3-120">Hämtar en lista med paket källor som har registrerats för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="b97c3-120">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="b97c3-121">Importera – PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b97c3-121">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="b97c3-122">Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b97c3-122">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="b97c3-123">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="b97c3-123">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="b97c3-124">Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="b97c3-124">Installs one or more software packages.</span></span>

### [<span data-ttu-id="b97c3-125">Installera-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b97c3-125">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="b97c3-126">Installerar en eller flera leverantörer av paket hanterings paket.</span><span class="sxs-lookup"><span data-stu-id="b97c3-126">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="b97c3-127">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="b97c3-127">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="b97c3-128">Lägger till en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="b97c3-128">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="b97c3-129">Spara paket</span><span class="sxs-lookup"><span data-stu-id="b97c3-129">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="b97c3-130">Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="b97c3-130">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="b97c3-131">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b97c3-131">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="b97c3-132">Ersätter en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="b97c3-132">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="b97c3-133">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="b97c3-133">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="b97c3-134">Avinstallerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="b97c3-134">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="b97c3-135">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b97c3-135">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="b97c3-136">Tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="b97c3-136">Removes a registered package source.</span></span>
