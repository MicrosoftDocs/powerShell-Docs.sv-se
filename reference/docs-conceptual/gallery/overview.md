---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery, psget
title: PowerShell-galleriet
ms.openlocfilehash: e489d2dd4db087b53eb07d2a8793c8f586c9b210
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500568"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="85a82-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="85a82-103">The PowerShell Gallery</span></span>

<span data-ttu-id="85a82-104">PowerShell-galleriet är den centrala lagrings platsen för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="85a82-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="85a82-105">I det kan du hitta användbara PowerShell-moduler som innehåller PowerShell-kommandon och DSC-resurser (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="85a82-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="85a82-106">Du kan också hitta PowerShell-skript, varav vissa kan innehålla PowerShell-arbetsflöden och en uppsättning aktiviteter och tillhandahålla sekvenseringen för dessa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="85a82-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="85a82-107">Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="85a82-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="85a82-108">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="85a82-108">PowerShellGet Overview</span></span>

<span data-ttu-id="85a82-109">Modulen PowerShellGet innehåller cmdlets för att upptäcka, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter som moduler, DSC-resurser, roll funktioner och skript från [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.</span><span class="sxs-lookup"><span data-stu-id="85a82-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="85a82-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="85a82-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="85a82-111">Den senaste versionen av PowerShellGet-modulen kräver att du installerar paket från galleriet.</span><span class="sxs-lookup"><span data-stu-id="85a82-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="85a82-112">Fullständiga instruktioner finns i [Installera PowerShellGet](installing-psget.md) .</span><span class="sxs-lookup"><span data-stu-id="85a82-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="85a82-113">Se [Komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med galleriet.</span><span class="sxs-lookup"><span data-stu-id="85a82-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="85a82-114">Du kan också köra *Update-Help -Module PowerShellGet* om du vill installera lokal hjälp för dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="85a82-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="85a82-115">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="85a82-115">Supported Operating Systems</span></span>

<span data-ttu-id="85a82-116">För **PowerShellGet**-modulen krävs **PowerShell version 3.0 eller senare**.</span><span class="sxs-lookup"><span data-stu-id="85a82-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="85a82-117">**PowerShellGet** kräver .NET Framework 4,5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="85a82-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="85a82-118">Du kan installera .NET Framework 4.5 eller senare [här](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span><span class="sxs-lookup"><span data-stu-id="85a82-118">You can install .NET Framework 4.5 or above from [here](https://msdn.microsoft.com/library/5a4x27ek.aspx).</span></span>

<span data-ttu-id="85a82-119">Eftersom **PowerShell Core** är plattforms oberoende och innebär det att den fungerar på Windows, Linux och MacOS, vilket även gör **PowerShellGet** tillgängliga på dessa system.</span><span class="sxs-lookup"><span data-stu-id="85a82-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="85a82-120">En fullständig lista över system som stöds av **PowerShell Core** finns i [Installera PowerShell](/powershell/scripting/install/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="85a82-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="85a82-121">Många moduler som finns i galleriet har stöd för olika operativ system och har ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="85a82-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="85a82-122">Mer information finns i dokumentationen för modulerna.</span><span class="sxs-lookup"><span data-stu-id="85a82-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="85a82-123">Fick du en fråga?</span><span class="sxs-lookup"><span data-stu-id="85a82-123">Got a question?</span></span> <span data-ttu-id="85a82-124">Har du feedback till oss?</span><span class="sxs-lookup"><span data-stu-id="85a82-124">Have feedback?</span></span>

<span data-ttu-id="85a82-125">Mer information om PowerShell-galleriet-och PowerShellGet finns på sidan [komma igång](getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="85a82-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span> <span data-ttu-id="85a82-126">Ge feedback och rapportera problem med [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span><span class="sxs-lookup"><span data-stu-id="85a82-126">Please provide feedback and report issues using [UserVoice](http://windowsserver.uservoice.com/forums/301869-powershell).</span></span>
