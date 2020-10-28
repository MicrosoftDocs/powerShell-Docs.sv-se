---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en Windows PowerShell-modul
description: Skriva en Windows PowerShell-modul
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659430"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="df97d-103">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="df97d-103">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="df97d-104">Det här dokumentet är skrivet för administratörer, skript utvecklare och cmdlet-utvecklare som behöver paketera och distribuera sina Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="df97d-104">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="df97d-105">Med hjälp av Windows PowerShell-moduler kan du paketera och distribuera dina Windows PowerShell-lösningar utan att använda ett kompilerat språk.</span><span class="sxs-lookup"><span data-stu-id="df97d-105">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="df97d-106">Med Windows PowerShell-moduler kan du partitionera, organisera och abstrakta din Windows PowerShell-kod i självständiga, återanvändbara enheter.</span><span class="sxs-lookup"><span data-stu-id="df97d-106">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="df97d-107">Med dessa åter användnings bara enheter kan du enkelt dela dina moduler direkt med andra.</span><span class="sxs-lookup"><span data-stu-id="df97d-107">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="df97d-108">Om du är en skript utvecklare kan du också paketera om moduler från tredje part för att skapa anpassade skriptbaserade program.</span><span class="sxs-lookup"><span data-stu-id="df97d-108">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="df97d-109">Moduler som liknar moduler i andra skript språk, till exempel perl och python, möjliggör produktions klara skript lösningar som använder återanvändbara, distribuerbara komponenter, med den extra fördelen att du kan paketera och sammanställa flera komponenter för att skapa anpassade lösningar.</span><span class="sxs-lookup"><span data-stu-id="df97d-109">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="df97d-110">Windows PowerShell kommer att behandla alla giltiga Windows PowerShell-skript koder som sparats i en. psm1-fil som en modul.</span><span class="sxs-lookup"><span data-stu-id="df97d-110">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="df97d-111">PowerShell kommer också automatiskt att behandla en binär cmdlet-sammansättning som en modul.</span><span class="sxs-lookup"><span data-stu-id="df97d-111">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="df97d-112">Men du kan också använda en modul (eller mer specifikt ett modul manifest) för att bunta samman en hel lösning.</span><span class="sxs-lookup"><span data-stu-id="df97d-112">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="df97d-113">I följande scenarier beskrivs vanliga användnings områden för Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="df97d-113">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="df97d-114">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="df97d-114">Libraries</span></span>

<span data-ttu-id="df97d-115">Moduler kan användas för att paketera och distribuera sammanhängande bibliotek med funktioner som utför vanliga uppgifter.</span><span class="sxs-lookup"><span data-stu-id="df97d-115">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="df97d-116">Normalt delar namnen på dessa funktioner ett eller flera substantiv som återspeglar den vanliga uppgiften som de används för.</span><span class="sxs-lookup"><span data-stu-id="df97d-116">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="df97d-117">Dessa funktioner kan också likna .NET Framework klasser i att de kan ha offentliga och privata medlemmar.</span><span class="sxs-lookup"><span data-stu-id="df97d-117">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="df97d-118">Ett bibliotek kan till exempel innehålla en uppsättning funktioner för fil överföringar.</span><span class="sxs-lookup"><span data-stu-id="df97d-118">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="df97d-119">I det här fallet kan substantiv som reflekterar den vanliga uppgiften vara "File".</span><span class="sxs-lookup"><span data-stu-id="df97d-119">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="df97d-120">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="df97d-120">Configuration</span></span>

<span data-ttu-id="df97d-121">Moduler kan användas för att anpassa din miljö genom att lägga till vissa cmdlets, providrar, funktioner och variabler.</span><span class="sxs-lookup"><span data-stu-id="df97d-121">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="df97d-122">Kompilerad kod utveckling och distribution</span><span class="sxs-lookup"><span data-stu-id="df97d-122">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="df97d-123">Cmdlet-och Provider-utvecklare kan använda moduler för att testa och distribuera sin kompilerade kod utan att behöva skapa snapin-moduler. De kan importera den sammansättning som innehåller den kompilerade koden som en modul (en binär modul) utan att behöva skapa och registrera snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="df97d-123">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="df97d-124">Se även</span><span class="sxs-lookup"><span data-stu-id="df97d-124">See Also</span></span>

[<span data-ttu-id="df97d-125">Förstå en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="df97d-125">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="df97d-126">Skriva en PowerShell-skriptmodul</span><span class="sxs-lookup"><span data-stu-id="df97d-126">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="df97d-127">Skriva en binär PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="df97d-127">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="df97d-128">Skriva ett PowerShell-modulmanifest</span><span class="sxs-lookup"><span data-stu-id="df97d-128">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="df97d-129">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="df97d-129">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="df97d-130">Importera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="df97d-130">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="df97d-131">Installera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="df97d-131">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
