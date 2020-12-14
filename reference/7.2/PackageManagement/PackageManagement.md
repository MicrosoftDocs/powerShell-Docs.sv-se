---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 4ae9fd46-338a-459c-8186-07f910774cb8
Module Name: PackageManagement
ms.date: 06/09/2017
schema: 2.0.0
title: PackageManagement
ms.openlocfilehash: 86e6f37f6f7f0527c5dcca309cf581cb6f1b4de5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889333"
---
# <span data-ttu-id="ecd3f-102">PackageManagement-modul</span><span class="sxs-lookup"><span data-stu-id="ecd3f-102">PackageManagement Module</span></span>

## <span data-ttu-id="ecd3f-103">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ecd3f-103">Description</span></span>

<span data-ttu-id="ecd3f-104">I det här avsnittet visas hjälp avsnitt för Package Management-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-104">This topic displays help topics for the Package Management Cmdlets.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ecd3f-105">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="ecd3f-106">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="ecd3f-107">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="ecd3f-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="ecd3f-108">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="ecd3f-109">PackageManagement-cmdletar</span><span class="sxs-lookup"><span data-stu-id="ecd3f-109">PackageManagement Cmdlets</span></span>

### [<span data-ttu-id="ecd3f-110">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="ecd3f-110">Find-Package</span></span>](Find-Package.md)
<span data-ttu-id="ecd3f-111">Söker efter program varu paket i tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-111">Finds software packages in available package sources.</span></span>

### [<span data-ttu-id="ecd3f-112">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ecd3f-112">Find-PackageProvider</span></span>](Find-PackageProvider.md)
<span data-ttu-id="ecd3f-113">Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-113">Returns a list of Package Management package providers available for installation.</span></span>

### [<span data-ttu-id="ecd3f-114">Get-Package</span><span class="sxs-lookup"><span data-stu-id="ecd3f-114">Get-Package</span></span>](Get-Package.md)
<span data-ttu-id="ecd3f-115">Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-115">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

### [<span data-ttu-id="ecd3f-116">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ecd3f-116">Get-PackageProvider</span></span>](Get-PackageProvider.md)
<span data-ttu-id="ecd3f-117">Returnerar en lista med paket leverantörer som är anslutna till paket hantering.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-117">Returns a list of package providers that are connected to Package Management.</span></span>

### [<span data-ttu-id="ecd3f-118">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ecd3f-118">Get-PackageSource</span></span>](Get-PackageSource.md)
<span data-ttu-id="ecd3f-119">Hämtar en lista med paket källor som har registrerats för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-119">Gets a list of package sources that are registered for a package provider.</span></span>

### [<span data-ttu-id="ecd3f-120">Importera – PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ecd3f-120">Import-PackageProvider</span></span>](Import-PackageProvider.md)
<span data-ttu-id="ecd3f-121">Lägger till leverantörer av paket hanterings paket i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-121">Adds Package Management package providers to the current session.</span></span>

### [<span data-ttu-id="ecd3f-122">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="ecd3f-122">Install-Package</span></span>](Install-Package.md)
<span data-ttu-id="ecd3f-123">Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-123">Installs one or more software packages.</span></span>

### [<span data-ttu-id="ecd3f-124">Installera-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="ecd3f-124">Install-PackageProvider</span></span>](Install-PackageProvider.md)
<span data-ttu-id="ecd3f-125">Installerar en eller flera leverantörer av paket hanterings paket.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-125">Installs one or more Package Management package providers.</span></span>

### [<span data-ttu-id="ecd3f-126">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="ecd3f-126">Register-PackageSource</span></span>](Register-PackageSource.md)
<span data-ttu-id="ecd3f-127">Lägger till en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-127">Adds a package source for a specified package provider.</span></span>

### [<span data-ttu-id="ecd3f-128">Spara paket</span><span class="sxs-lookup"><span data-stu-id="ecd3f-128">Save-Package</span></span>](Save-Package.md)
<span data-ttu-id="ecd3f-129">Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-129">Saves packages to the local computer without installing them.</span></span>

### [<span data-ttu-id="ecd3f-130">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ecd3f-130">Set-PackageSource</span></span>](Set-PackageSource.md)
<span data-ttu-id="ecd3f-131">Ersätter en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-131">Replaces a package source for a specified package provider.</span></span>

### [<span data-ttu-id="ecd3f-132">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="ecd3f-132">Uninstall-Package</span></span>](Uninstall-Package.md)
<span data-ttu-id="ecd3f-133">Avinstallerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-133">Uninstalls one or more software packages.</span></span>

### [<span data-ttu-id="ecd3f-134">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="ecd3f-134">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
<span data-ttu-id="ecd3f-135">Tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="ecd3f-135">Removes a registered package source.</span></span>
