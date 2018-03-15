---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: 7389ce8286c515b0bfc25f32634a482b060cb74c
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="384a8-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="384a8-103">The PowerShell Gallery</span></span>

<span data-ttu-id="384a8-104">PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="384a8-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="384a8-105">Du hittar nya PowerShell-kommandon eller önskas tillstånd Configuration DSC ()-resurser i galleriet.</span><span class="sxs-lookup"><span data-stu-id="384a8-105">You can find new PowerShell commands or Desired State Configuration (DSC) resources in the Gallery.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="384a8-106">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="384a8-106">PowerShellGet Overview</span></span>

<span data-ttu-id="384a8-107">Modulen PowerShellGet innehåller cmdlets för identifiering, installera, uppdatera och publicera PowerShell artefakter, till exempel moduler, DSC-resurser, roll funktioner och skript från den [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.</span><span class="sxs-lookup"><span data-stu-id="384a8-107">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="384a8-108">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="384a8-108">Getting Started with the Gallery</span></span>

<span data-ttu-id="384a8-109">Installationen av objekt från galleriet kräver den senaste versionen av modulen PowerShellGet som är tillgänglig i Windows 10, i Windows Management Framework (WMF) 5.0 eller i MSI-baserade installationsprogrammet (för PowerShell 3 och 4).</span><span class="sxs-lookup"><span data-stu-id="384a8-109">Installing items from the Gallery requires the latest version of the PowerShellGet module, which is available in Windows 10, in Windows Management Framework (WMF) 5.0, or in the MSI-based installer (for PowerShell 3 and 4).</span></span>

- <span data-ttu-id="384a8-110">[**Hämta Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span><span class="sxs-lookup"><span data-stu-id="384a8-110">[**Get Windows 10**](http://go.microsoft.com/fwlink/?LinkID=624830&clcid=0x409),</span></span>
- <span data-ttu-id="384a8-111">[**Hämta WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), eller</span><span class="sxs-lookup"><span data-stu-id="384a8-111">[**Get WMF 5.0**](http://go.microsoft.com/fwlink/?LinkId=398175), or</span></span>
- [<span data-ttu-id="384a8-112">**Hämta MSI Installer**</span><span class="sxs-lookup"><span data-stu-id="384a8-112">**Get MSI Installer**</span></span>](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

<span data-ttu-id="384a8-113">Med senast [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) modulen, kan du:</span><span class="sxs-lookup"><span data-stu-id="384a8-113">With the latest [PowerShellGet](http://go.microsoft.com/fwlink/?LinkID=760387&clcid=0x409) module, you can:</span></span>

-   <span data-ttu-id="384a8-114">Sök igenom objekt i galleriet med [hitta modulen](https://go.microsoft.com/fwlink/?LinkId=821658) och [Sök-skript](https://go.microsoft.com/fwlink/?LinkId=822322)</span><span class="sxs-lookup"><span data-stu-id="384a8-114">Search through items in the Gallery with [Find-Module](https://go.microsoft.com/fwlink/?LinkId=821658) and [Find-Script](https://go.microsoft.com/fwlink/?LinkId=822322)</span></span>
-   <span data-ttu-id="384a8-115">Spara objekt till systemet från galleriet med [spara modulen](https://go.microsoft.com/fwlink/?LinkId=821669) och [spara skriptet](https://go.microsoft.com/fwlink/?LinkId=822334)</span><span class="sxs-lookup"><span data-stu-id="384a8-115">Save items to your system from the Gallery with [Save-Module](https://go.microsoft.com/fwlink/?LinkId=821669) and [Save-Script](https://go.microsoft.com/fwlink/?LinkId=822334)</span></span>
-   <span data-ttu-id="384a8-116">Installera objekt från galleriet med [installera modulen](https://go.microsoft.com/fwlink/?LinkId=821663) och [installationsskriptet](https://go.microsoft.com/fwlink/?LinkId=822327)</span><span class="sxs-lookup"><span data-stu-id="384a8-116">Install items from the Gallery with [Install-Module](https://go.microsoft.com/fwlink/?LinkId=821663) and [Install-Script](https://go.microsoft.com/fwlink/?LinkId=822327)</span></span>
-   <span data-ttu-id="384a8-117">Överföra objekt i galleriet med [publicera modulen](https://go.microsoft.com/fwlink/?LinkId=821666) och [publicera-skript](https://go.microsoft.com/fwlink/?LinkId=822331)</span><span class="sxs-lookup"><span data-stu-id="384a8-117">Upload items to the Gallery with [Publish-Module](https://go.microsoft.com/fwlink/?LinkId=821666) and [Publish-Script](https://go.microsoft.com/fwlink/?LinkId=822331)</span></span>
-   <span data-ttu-id="384a8-118">Lägg till anpassade databasen med [registrera PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span><span class="sxs-lookup"><span data-stu-id="384a8-118">Add your own custom repository with [Register-PSRepository](https://go.microsoft.com/fwlink/?LinkId=821668)</span></span>

<span data-ttu-id="384a8-119">Kolla in den [komma igång](psgallery/psgallery_gettingstarted.md) för mer information om hur du använder PowerShellGet kommandon med Gallery.</span><span class="sxs-lookup"><span data-stu-id="384a8-119">Check out the [Getting Started](psgallery/psgallery_gettingstarted.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="384a8-120">Du kan också köra *Update-Help-modulen PowerShellGet* att installera lokal hjälp för att dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="384a8-120">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="384a8-121">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="384a8-121">Supported Operating Systems</span></span>

<span data-ttu-id="384a8-122">Den **PowerShellGet** module kräver **PowerShell 3.0 eller senare**.</span><span class="sxs-lookup"><span data-stu-id="384a8-122">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="384a8-123">Därför **PowerShellGet** kräver en av följande operativsystem:</span><span class="sxs-lookup"><span data-stu-id="384a8-123">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="384a8-124">Windows 10</span><span class="sxs-lookup"><span data-stu-id="384a8-124">Windows 10</span></span>
- <span data-ttu-id="384a8-125">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="384a8-125">Windows 8.1 Pro</span></span>
- <span data-ttu-id="384a8-126">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="384a8-126">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="384a8-127">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="384a8-127">Windows 7 SP1</span></span>
- <span data-ttu-id="384a8-128">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="384a8-128">Windows Server 2016</span></span>
- <span data-ttu-id="384a8-129">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="384a8-129">Windows Server 2012 R2</span></span>
- <span data-ttu-id="384a8-130">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="384a8-130">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="384a8-131">**PowerShellGet** kräver .NET Framework 4.5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="384a8-131">**PowerShellGet** also  requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="384a8-132">Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="384a8-132">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>


## <a name="got-a-question-have-feedback"></a><span data-ttu-id="384a8-133">En fråga?</span><span class="sxs-lookup"><span data-stu-id="384a8-133">Got a question?</span></span> <span data-ttu-id="384a8-134">Ge feedback?</span><span class="sxs-lookup"><span data-stu-id="384a8-134">Have feedback?</span></span>

<span data-ttu-id="384a8-135">Mer information om PowerShell-galleriet och PowerShellGet kan hittas i den [komma igång](psgallery/psgallery_gettingstarted.md) sidan.</span><span class="sxs-lookup"><span data-stu-id="384a8-135">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](psgallery/psgallery_gettingstarted.md) page.</span></span> <span data-ttu-id="384a8-136">Lämna feedback och rapportera problem med att använda [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="384a8-136">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>

