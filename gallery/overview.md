---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076029"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="d544c-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d544c-103">The PowerShell Gallery</span></span>

<span data-ttu-id="d544c-104">PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="d544c-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="d544c-105">Du kan hitta användbar PowerShell-moduler som innehåller PowerShell-kommandon och Desired State Configuration (DSC) resurser i den.</span><span class="sxs-lookup"><span data-stu-id="d544c-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="d544c-106">Du kan också hitta PowerShell-skript, vilket kan innehålla PowerShell-arbetsflöden och som beskriver en uppsättning aktiviteter och ange ordningsföljd för dessa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="d544c-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="d544c-107">Vissa av dessa paket skapats av Microsoft och andra skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="d544c-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="d544c-108">PowerShellGet-översikt</span><span class="sxs-lookup"><span data-stu-id="d544c-108">PowerShellGet Overview</span></span>

<span data-ttu-id="d544c-109">PowerShellGet-modulen innehåller cmdlets för identifiering, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter som moduler, DSC-resurser, rollfunktioner och skript från den [PowerShell-galleriet](https://www.PowerShellGallery.com)och andra privata lagringsplatser.</span><span class="sxs-lookup"><span data-stu-id="d544c-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="d544c-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="d544c-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="d544c-111">Installera paket från galleriet krävs den senaste versionen av modulen PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d544c-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="d544c-112">Se [installera PowerShellGet](installing-psget.md) fullständiga anvisningar.</span><span class="sxs-lookup"><span data-stu-id="d544c-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="d544c-113">Kolla in den [komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med galleriet.</span><span class="sxs-lookup"><span data-stu-id="d544c-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="d544c-114">Du kan också köra *Update-Help-Module PowerShellGet* att installera lokal hjälp för dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="d544c-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d544c-115">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="d544c-115">Supported Operating Systems</span></span>

<span data-ttu-id="d544c-116">Den **PowerShellGet** modulen kräver **Windows PowerShell version 3.0 eller senare**, eller **PowerShell Core 6.0 eller nyare**.</span><span class="sxs-lookup"><span data-stu-id="d544c-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="d544c-117">En lämplig version av **Windows PowerShell** är tillgänglig för dessa operativsystem:</span><span class="sxs-lookup"><span data-stu-id="d544c-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="d544c-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d544c-118">Windows 10</span></span>
- <span data-ttu-id="d544c-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="d544c-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="d544c-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d544c-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="d544c-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d544c-121">Windows 7 SP1</span></span>
- <span data-ttu-id="d544c-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="d544c-122">Windows Server 2019</span></span>
- <span data-ttu-id="d544c-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d544c-123">Windows Server 2016</span></span>
- <span data-ttu-id="d544c-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d544c-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="d544c-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d544c-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="d544c-126">**PowerShellGet** kräver .NET Framework 4.5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="d544c-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="d544c-127">Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="d544c-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="d544c-128">Eftersom **PowerShell Core** är plattformsoberoende och som innebär att det fungerar på Windows, Linux och MacOS, även gör **PowerShellGet** tillgänglig på dessa system.</span><span class="sxs-lookup"><span data-stu-id="d544c-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="d544c-129">En fullständig lista över system som stöds av **PowerShell Core** Se [installera PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="d544c-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="d544c-130">Många moduler i galleriet stöder olika operativsystem och har ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="d544c-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="d544c-131">Läs dokumentationen för moduler för mer information.</span><span class="sxs-lookup"><span data-stu-id="d544c-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="d544c-132">En fråga?</span><span class="sxs-lookup"><span data-stu-id="d544c-132">Got a question?</span></span> <span data-ttu-id="d544c-133">Har du feedback?</span><span class="sxs-lookup"><span data-stu-id="d544c-133">Have feedback?</span></span>

<span data-ttu-id="d544c-134">Mer information om PowerShell-galleriet och PowerShellGet finns i den [komma igång](getting-started.md) sidan.</span><span class="sxs-lookup"><span data-stu-id="d544c-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="d544c-135">Ge feedback och rapportera problem med hjälp av [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="d544c-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
