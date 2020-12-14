---
ms.date: 12/01/2020
title: PowerShell-galleriet
description: PowerShell-galleriet är den centrala lagrings platsen för PowerShell-moduler, skript och DSC-resurser.
ms.openlocfilehash: f1ce6a8e2d5d72ac14cf3e4854626ef612d27891
ms.sourcegitcommit: 62282bb9c36fea3b4290b9263c1cd8e9ac216e29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96470323"
---
# <a name="the-powershell-gallery"></a><span data-ttu-id="a243b-103">PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a243b-103">The PowerShell Gallery</span></span>

<span data-ttu-id="a243b-104">PowerShell-galleriet är den centrala lagrings platsen för PowerShell-innehåll.</span><span class="sxs-lookup"><span data-stu-id="a243b-104">The PowerShell Gallery is the central repository for PowerShell content.</span></span> <span data-ttu-id="a243b-105">I det kan du hitta användbara PowerShell-moduler som innehåller PowerShell-kommandon och DSC-resurser (Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="a243b-105">In it, you can find useful PowerShell modules containing PowerShell commands and Desired State Configuration (DSC) resources.</span></span>
<span data-ttu-id="a243b-106">Du kan också hitta PowerShell-skript, varav vissa kan innehålla PowerShell-arbetsflöden och en uppsättning aktiviteter och tillhandahålla sekvenseringen för dessa aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="a243b-106">You can also find PowerShell scripts, some of which may contain PowerShell workflows, and which outline a set of tasks and provide sequencing for those tasks.</span></span> <span data-ttu-id="a243b-107">Några av de här paketen har skapats av Microsoft och andra har skapats av PowerShell-communityn.</span><span class="sxs-lookup"><span data-stu-id="a243b-107">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>

## <a name="powershellget-overview"></a><span data-ttu-id="a243b-108">Översikt över PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a243b-108">PowerShellGet Overview</span></span>

<span data-ttu-id="a243b-109">Modulen PowerShellGet innehåller cmdlets för att upptäcka, installera, uppdatera och publicera PowerShell-paket som innehåller artefakter som moduler, DSC-resurser, roll funktioner och skript från [PowerShell-galleriet](https://www.PowerShellGallery.com) och andra privata databaser.</span><span class="sxs-lookup"><span data-stu-id="a243b-109">The PowerShellGet module contains cmdlets for discovering, installing, updating and publishing PowerShell packages which contain artifacts such as Modules, DSC Resources, Role Capabilities and Scripts from the [PowerShell Gallery](https://www.PowerShellGallery.com) and other private repositories.</span></span>

## <a name="getting-started-with-the-gallery"></a><span data-ttu-id="a243b-110">Komma igång med galleriet</span><span class="sxs-lookup"><span data-stu-id="a243b-110">Getting Started with the Gallery</span></span>

<span data-ttu-id="a243b-111">Den senaste versionen av PowerShellGet-modulen kräver att du installerar paket från galleriet.</span><span class="sxs-lookup"><span data-stu-id="a243b-111">Installing packages from the Gallery requires the latest version of the PowerShellGet module.</span></span> <span data-ttu-id="a243b-112">Fullständiga instruktioner finns i [Installera PowerShellGet](installing-psget.md) .</span><span class="sxs-lookup"><span data-stu-id="a243b-112">See [Installing PowerShellGet](installing-psget.md) for complete instructions.</span></span>

<span data-ttu-id="a243b-113">Se [Komma igång](getting-started.md) för mer information om hur du använder PowerShellGet-kommandon med galleriet.</span><span class="sxs-lookup"><span data-stu-id="a243b-113">Check out the [Getting Started](getting-started.md) page for more information on how to use PowerShellGet commands with the Gallery.</span></span> <span data-ttu-id="a243b-114">Du kan också köra *Update-Help -Module PowerShellGet* om du vill installera lokal hjälp för dessa kommandon.</span><span class="sxs-lookup"><span data-stu-id="a243b-114">You can also run *Update-Help -Module PowerShellGet* to install local help for these commands.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="a243b-115">Operativsystem som stöds</span><span class="sxs-lookup"><span data-stu-id="a243b-115">Supported Operating Systems</span></span>

<span data-ttu-id="a243b-116">För **PowerShellGet**-modulen krävs **PowerShell version 3.0 eller senare**.</span><span class="sxs-lookup"><span data-stu-id="a243b-116">The **PowerShellGet** module requires **PowerShell 3.0 or newer**.</span></span>

<span data-ttu-id="a243b-117">**PowerShellGet** kräver .NET Framework 4,5 eller senare.</span><span class="sxs-lookup"><span data-stu-id="a243b-117">**PowerShellGet** requires .NET Framework 4.5 or above.</span></span> <span data-ttu-id="a243b-118">Mer information finns i [installera .NET Framework för utvecklare](/dotnet/framework/install/guide-for-developers).</span><span class="sxs-lookup"><span data-stu-id="a243b-118">For more information, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers).</span></span>

<span data-ttu-id="a243b-119">Eftersom **PowerShell Core** är plattforms oberoende och innebär det att den fungerar på Windows, Linux och MacOS, vilket även gör **PowerShellGet** tillgängliga på dessa system.</span><span class="sxs-lookup"><span data-stu-id="a243b-119">Since **PowerShell Core** is cross-platform and that means it works on Windows, Linux and MacOS, that also makes **PowerShellGet** available on those systems.</span></span> <span data-ttu-id="a243b-120">En fullständig lista över system som stöds av **PowerShell Core** finns i [Installera PowerShell](/powershell/scripting/install/installing-powershell).</span><span class="sxs-lookup"><span data-stu-id="a243b-120">For a full list of systems supported by **PowerShell Core** see [Installing PowerShell](/powershell/scripting/install/installing-powershell).</span></span>

<span data-ttu-id="a243b-121">Många moduler som finns i galleriet har stöd för olika operativ system och har ytterligare krav.</span><span class="sxs-lookup"><span data-stu-id="a243b-121">Many modules hosted in the gallery will support different OSes and have additional requirements.</span></span>
<span data-ttu-id="a243b-122">Mer information finns i dokumentationen för modulerna.</span><span class="sxs-lookup"><span data-stu-id="a243b-122">Please refer to the documentation for the modules for more information.</span></span>

## <a name="got-a-question-have-feedback"></a><span data-ttu-id="a243b-123">Fick du en fråga?</span><span class="sxs-lookup"><span data-stu-id="a243b-123">Got a question?</span></span> <span data-ttu-id="a243b-124">Har du feedback till oss?</span><span class="sxs-lookup"><span data-stu-id="a243b-124">Have feedback?</span></span>

<span data-ttu-id="a243b-125">Mer information om PowerShell-galleriet-och PowerShellGet finns på sidan [komma igång](getting-started.md) .</span><span class="sxs-lookup"><span data-stu-id="a243b-125">More information about the PowerShell Gallery and PowerShellGet can be found in the [Getting Started](getting-started.md) page.</span></span>

<span data-ttu-id="a243b-126">För att se aktuell status för PowerShell-galleriet tjänsterna, se sidan [PowerShell-galleriet status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) på GitHub.</span><span class="sxs-lookup"><span data-stu-id="a243b-126">To see the current status of the PowerShell Gallery services, see the [PowerShell Gallery Status](https://github.com/PowerShell/PowerShellGallery/blob/master/psgallery_status.md) page on GitHub.</span></span>

<span data-ttu-id="a243b-127">Ge feedback och rapportera fel i [GitHub-lagringsplatsen](https://github.com/PowerShell/PowerShellGallery/issues).</span><span class="sxs-lookup"><span data-stu-id="a243b-127">Please provide feedback and report issues the [GitHub repository](https://github.com/PowerShell/PowerShellGallery/issues).</span></span>
