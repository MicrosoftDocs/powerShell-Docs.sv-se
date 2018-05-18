---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: 65e0c427310ac20621109a6620e926a7894cf8f8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="d8237-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="d8237-103">The PowerShell Gallery</span></span>

<span data-ttu-id="d8237-104">PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="d8237-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="d8237-105">I den hittar du användbar PowerShell-moduler som innehåller PowerShell-kommandon och önskade tillstånd Configuration DSC ()-resurser.</span><span class="sxs-lookup"><span data-stu-id="d8237-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="d8237-106">Du kan också hitta PowerShell-skript, vilket kan innehålla PowerShell-arbetsflöden och som beskriver en uppsättning uppgifter och ange ordningsföljd för dessa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="d8237-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="d8237-107">Vissa av dessa element skapats av Microsoft och andra skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="d8237-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="d8237-108">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d8237-108">PowerShellGet Overview</span></span>

<span data-ttu-id="d8237-109">Modulen PowerShellGet innehåller cmdlets för identifiering, installera, uppdatera och publicera PowerShell artefakter, till exempel moduler, DSC-resurser, roll funktioner och skript från den [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.</span><span class="sxs-lookup"><span data-stu-id="d8237-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="d8237-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="d8237-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="d8237-111">Installationen av objekt från galleriet kräver den senaste versionen av modulen PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="d8237-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="d8237-112">Se [installerar PowerShellGet](installing-psget.md) fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="d8237-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="d8237-113">Kolla in den [komma igång](getting-started.md) för mer information om hur du använder PowerShellGet kommandon med Gallery.</span><span class="sxs-lookup"><span data-stu-id="d8237-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="d8237-114">Du kan också köra *Update-Help-modulen PowerShellGet* att installera lokal hjälp för att dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="d8237-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="d8237-115">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="d8237-115">Supported Operating Systems</span></span>

<span data-ttu-id="d8237-116">Den **PowerShellGet** module kräver **PowerShell 3.0 eller senare**.</span><span class="sxs-lookup"><span data-stu-id="d8237-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="d8237-117">Därför **PowerShellGet** kräver en av följande operativsystem:</span><span class="sxs-lookup"><span data-stu-id="d8237-117">Therefore, **PowerShellGet** requires one of the following operating systems:</span></span>

- <span data-ttu-id="d8237-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="d8237-118">Windows 10</span></span>
- <span data-ttu-id="d8237-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="d8237-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="d8237-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="d8237-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="d8237-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="d8237-121">Windows 7 SP1</span></span>
- <span data-ttu-id="d8237-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="d8237-122">Windows Server 2016</span></span>
- <span data-ttu-id="d8237-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="d8237-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="d8237-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="d8237-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="d8237-125">**PowerShellGet** kräver .NET Framework 4.5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="d8237-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="d8237-126">Du kan installera .NET Framework 4.5 eller senare från [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="d8237-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="d8237-127">En fråga?</span><span class="sxs-lookup"><span data-stu-id="d8237-127">Got a question?</span></span> <span data-ttu-id="d8237-128">Ge feedback?</span><span class="sxs-lookup"><span data-stu-id="d8237-128">Have feedback?</span></span>

<span data-ttu-id="d8237-129">Mer information om PowerShell-galleriet och PowerShellGet kan hittas i den [komma igång](getting-started.md) sidan.</span><span class="sxs-lookup"><span data-stu-id="d8237-129">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="d8237-130">Lämna feedback och rapportera problem med att använda [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="d8237-130">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>