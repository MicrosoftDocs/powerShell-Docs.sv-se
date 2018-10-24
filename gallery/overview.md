---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: dc7e8dd7e4d96d8424a62cb3256c3164b63a3684
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482938"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="fe259-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="fe259-103">The PowerShell Gallery</span></span>

<span data-ttu-id="fe259-104">PowerShell-galleriet är en central lagringsplats för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="fe259-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="fe259-105">I den hittar du användbara PowerShell-moduler som innehåller PowerShell-kommandon och DSC-resurser (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="fe259-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="fe259-106">Du kan också hitta PowerShell-skript. Vissa av dessa kan innehålla PowerShell-arbetsflöden som beskriver en uppsättning uppgifter och anger ordningsföljd för dessa.</span><span class="sxs-lookup"><span data-stu-id="fe259-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="fe259-107">Vissa av dessa objekt har skapats av Microsoft och andra har skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="fe259-107">Some of these items are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="fe259-108">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="fe259-108">PowerShellGet Overview</span></span>

<span data-ttu-id="fe259-109">Modulen PowerShellGet innehåller cmdlets för identifiering, installation, uppdatering och publicering av PowerShell-artefakter, till exempel moduler, DSC-resurser, rollfunktioner och skript från  [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.</span><span class="sxs-lookup"><span data-stu-id="fe259-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="fe259-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="fe259-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="fe259-111">Installationen av objekt från galleriet kräver den senaste versionen av modulen PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="fe259-111">Installing items from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="fe259-112">Se [installerar PowerShellGet](installing-psget.md) för fullständiga instruktioner.</span><span class="sxs-lookup"><span data-stu-id="fe259-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="fe259-113">Se [komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med Gallery.</span><span class="sxs-lookup"><span data-stu-id="fe259-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="fe259-114">Du kan också köra *Update-Help -module PowerShellGet* för att installera lokal hjälp för att dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="fe259-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="fe259-115">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="fe259-115">Supported Operating Systems</span></span>

<span data-ttu-id="fe259-116">**PowerShellGet**-modulen kräver **Windows PowerShell 3.0 eller nyare**, eller **PowerShell Core 6.0 eller nyare**.</span><span class="sxs-lookup"><span data-stu-id="fe259-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="fe259-117">En lämplig version av **Windows PowerShell** är tillgänglig för dessa operativsystem:</span><span class="sxs-lookup"><span data-stu-id="fe259-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="fe259-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="fe259-118">Windows 10</span></span>
- <span data-ttu-id="fe259-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="fe259-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="fe259-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="fe259-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="fe259-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="fe259-121">Windows 7 SP1</span></span>
- <span data-ttu-id="fe259-122">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fe259-122">Windows Server 2016</span></span>
- <span data-ttu-id="fe259-123">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fe259-123">Windows Server 2012 R2</span></span>
- <span data-ttu-id="fe259-124">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="fe259-124">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="fe259-125">**PowerShellGet** kräver .NET Framework 4.5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="fe259-125">**PowerShellGet** also requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="fe259-126">Du kan installera .NET Framework 4.5 eller senare [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="fe259-126">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="fe259-127">**PowerShell Core** stöder många operativsystem.</span><span class="sxs-lookup"><span data-stu-id="fe259-127">**PowerShell Core** supports many operating systems.</span></span> <span data-ttu-id="fe259-128">Se [i den här artikeln](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) för en fullständig lista.</span><span class="sxs-lookup"><span data-stu-id="fe259-128">See [this article](https://blogs.msdn.microsoft.com/powershell/2018/01/10/powershell-core-6-0-generally-available-ga-and-supported/) for a full list.</span></span>

<span data-ttu-id="fe259-129">Många moduler som finns i galleriet stöder olika operativsystem och har ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="fe259-129">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="fe259-130">Se dokumentationen för moduler för mer information.</span><span class="sxs-lookup"><span data-stu-id="fe259-130">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="fe259-131">En fråga?</span><span class="sxs-lookup"><span data-stu-id="fe259-131">Got a question?</span></span> <span data-ttu-id="fe259-132">Ge feedback?</span><span class="sxs-lookup"><span data-stu-id="fe259-132">Have feedback?</span></span>

<span data-ttu-id="fe259-133">Mer information om PowerShell-galleriet och PowerShellGet finns på sidan[komma igång](getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="fe259-133">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="fe259-134">Lämna feedback och rapportera problem genom att använda [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="fe259-134">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
