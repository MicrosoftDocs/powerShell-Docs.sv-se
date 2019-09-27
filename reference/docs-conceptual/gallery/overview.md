---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: d3e3b9d8bb3d6cefd3a3bfe79b012bb1dc1d8a2d
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328744"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="756b1-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="756b1-103">The PowerShell Gallery</span></span>

<span data-ttu-id="756b1-104">PowerShell-galleriet är den centrala lagrings platsen för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="756b1-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="756b1-105">I det kan du hitta användbara PowerShell-moduler som innehåller PowerShell-kommandon och DSC-resurser (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="756b1-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="756b1-106">Du kan också hitta PowerShell-skript, varav vissa kan innehålla PowerShell-arbetsflöden och en uppsättning aktiviteter och tillhandahålla sekvenseringen för dessa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="756b1-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="756b1-107">Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="756b1-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="756b1-108">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="756b1-108">PowerShellGet Overview</span></span>

<span data-ttu-id="756b1-109">PowerShellGet-modulen innehåller cmdletar för att upptäcka, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter, till exempel moduler, DSC-resurser, roll funktioner och skript från [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata 5.3.</span><span class="sxs-lookup"><span data-stu-id="756b1-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="756b1-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="756b1-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="756b1-111">Den senaste versionen av PowerShellGet-modulen kräver att du installerar paket från galleriet.</span><span class="sxs-lookup"><span data-stu-id="756b1-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span>
<span data-ttu-id="756b1-112">Fullständiga instruktioner finns i [Installera PowerShellGet](installing-psget.md) .</span><span class="sxs-lookup"><span data-stu-id="756b1-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="756b1-113">Mer information om hur du använder PowerShellGet-kommandon med galleriet finns på sidan [komma igång](getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="756b1-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="756b1-114">Du kan också köra *Update-Help-Module PowerShellGet* för att installera den lokala hjälpen för dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="756b1-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="756b1-115">Operativ system som stöds</span><span class="sxs-lookup"><span data-stu-id="756b1-115">Supported Operating Systems</span></span>

<span data-ttu-id="756b1-116">**PowerShellGet** -modulen kräver **Windows PowerShell 3,0 eller senare**, eller **PowerShell Core 6,0 eller senare**.</span><span class="sxs-lookup"><span data-stu-id="756b1-116">The **PowerShellGet** module requires **Windows PowerShell 3.0 or newer**, or **PowerShell Core 6.0 or newer**.</span></span>

<span data-ttu-id="756b1-117">En lämplig version av **Windows PowerShell** är tillgänglig för följande operativ system:</span><span class="sxs-lookup"><span data-stu-id="756b1-117">A suitable version of **Windows PowerShell** is available for these operating systems:</span></span>

- <span data-ttu-id="756b1-118">Windows 10</span><span class="sxs-lookup"><span data-stu-id="756b1-118">Windows 10</span></span>
- <span data-ttu-id="756b1-119">Windows 8.1 Pro</span><span class="sxs-lookup"><span data-stu-id="756b1-119">Windows 8.1 Pro</span></span>
- <span data-ttu-id="756b1-120">Windows 8.1 Enterprise</span><span class="sxs-lookup"><span data-stu-id="756b1-120">Windows 8.1 Enterprise</span></span>
- <span data-ttu-id="756b1-121">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="756b1-121">Windows 7 SP1</span></span>
- <span data-ttu-id="756b1-122">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="756b1-122">Windows Server 2019</span></span>
- <span data-ttu-id="756b1-123">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="756b1-123">Windows Server 2016</span></span>
- <span data-ttu-id="756b1-124">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="756b1-124">Windows Server 2012 R2</span></span>
- <span data-ttu-id="756b1-125">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="756b1-125">Windows Server 2008 R2 SP1</span></span>

<span data-ttu-id="756b1-126">**PowerShellGet** kräver .NET Framework 4,5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="756b1-126">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="756b1-127">Du kan installera .NET Framework 4,5 eller senare [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="756b1-127">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="756b1-128">Eftersom **PowerShell Core** är plattforms oberoende och innebär det att den fungerar på Windows, Linux och MacOS, vilket även gör **PowerShellGet** tillgängliga på dessa system.</span><span class="sxs-lookup"><span data-stu-id="756b1-128">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="756b1-129">En fullständig lista över system som stöds av **PowerShell Core** finns i [Installera PowerShell](/powershell/scripting/setup/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="756b1-129">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/setup/installing-powershell).</span></span>

<span data-ttu-id="756b1-130">Många moduler som finns i galleriet har stöd för olika operativ system och har ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="756b1-130">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span> <span data-ttu-id="756b1-131">Mer information finns i dokumentationen för modulerna.</span><span class="sxs-lookup"><span data-stu-id="756b1-131">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="756b1-132">Fick du en fråga?</span><span class="sxs-lookup"><span data-stu-id="756b1-132">Got a question?</span></span> <span data-ttu-id="756b1-133">Har du feedback?</span><span class="sxs-lookup"><span data-stu-id="756b1-133">Have feedback?</span></span>

<span data-ttu-id="756b1-134">Mer information om PowerShell-galleriet-och PowerShellGet finns på sidan [komma igång](getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="756b1-134">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="756b1-135">Ge feedback och rapportera problem med [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="756b1-135">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>