---
title: Skriva ett Windows PowerShell-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229347"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="cc22c-102">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="cc22c-103">Det här dokumentet är avsedd för administratörer, skript utvecklare och cmdlet-utvecklare som måste du paketera och distribuera sina Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="cc22c-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="cc22c-104">Genom att använda Windows PowerShell-moduler kan du paketera och distribuera dina Windows PowerShell-lösningar utan att använda ett kompilerade språk.</span><span class="sxs-lookup"><span data-stu-id="cc22c-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="cc22c-105">Windows PowerShell-moduler som gör det möjligt att partitionen, ordna och abstrahera dina Windows PowerShell-kod i självständig, återanvändbara enheter.</span><span class="sxs-lookup"><span data-stu-id="cc22c-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="cc22c-106">Med dessa återanvändbara enheter, kan du enkelt dela dina moduler direkt med andra.</span><span class="sxs-lookup"><span data-stu-id="cc22c-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="cc22c-107">Om du är skriptutvecklare kan du paketera om moduler från tredje part för att skapa anpassade skript-baserade program.</span><span class="sxs-lookup"><span data-stu-id="cc22c-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="cc22c-108">Moduler, liknar moduler i andra skriptspråk som Perl och Python, aktivera produktionsklara scripting lösningar som använder återanvändningsbara, omdistribuerbara komponenter, med den ytterligare fördelen med att du kan paketera om och ett utkast av flera komponenter att Skapa anpassade lösningar.</span><span class="sxs-lookup"><span data-stu-id="cc22c-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="cc22c-109">I sina mest grundläggande Windows PowerShell behandlar alla giltiga Windows PowerShell-skriptkod som sparas i en .psm1-fil som en modul.</span><span class="sxs-lookup"><span data-stu-id="cc22c-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="cc22c-110">PowerShell behandlar också automatiskt alla binära cmdlet-sammansättningen som en modul.</span><span class="sxs-lookup"><span data-stu-id="cc22c-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="cc22c-111">Du kan dock också använda en modul (eller mer specifikt ett modulmanifest) om du vill slå samman en hel lösning.</span><span class="sxs-lookup"><span data-stu-id="cc22c-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="cc22c-112">Följande scenarier beskriver vanliga användningsområden för Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="cc22c-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="cc22c-113">Bibliotek</span><span class="sxs-lookup"><span data-stu-id="cc22c-113">Libraries</span></span>

<span data-ttu-id="cc22c-114">Moduler kan användas för att paketera och distribuera sammanhängande bibliotek med funktioner som utför vanliga uppgifter.</span><span class="sxs-lookup"><span data-stu-id="cc22c-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="cc22c-115">Namnen på dessa funktioner delar vanligtvis en eller flera substantiv som motsvarar vanliga uppgiften som de ska användas för.</span><span class="sxs-lookup"><span data-stu-id="cc22c-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="cc22c-116">Dessa funktioner kan också vara liknar .NET Framework-klasser i att de kan ha offentliga och privata medlemmar.</span><span class="sxs-lookup"><span data-stu-id="cc22c-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="cc22c-117">Till exempel ett bibliotek som kan innehålla en uppsättning funktioner för filöverföringar.</span><span class="sxs-lookup"><span data-stu-id="cc22c-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="cc22c-118">I det här fallet kan substantiv återger vanliga aktiviteten vara ”fil”.</span><span class="sxs-lookup"><span data-stu-id="cc22c-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="cc22c-119">Konfiguration</span><span class="sxs-lookup"><span data-stu-id="cc22c-119">Configuration</span></span>

<span data-ttu-id="cc22c-120">Moduler kan användas för att anpassa din miljö genom att lägga till specifika cmdletar, providers, funktioner och variabler.</span><span class="sxs-lookup"><span data-stu-id="cc22c-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="cc22c-121">Kompilerad Kodutveckling och Distribution</span><span class="sxs-lookup"><span data-stu-id="cc22c-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="cc22c-122">Cmdlet och providern utvecklare kan använda moduler för att testa och distribuera sina kompilerad kod utan att behöva skapa snapin-moduler. De kan importera den sammansättning som innehåller den kompilerade koden som en modul (en binär modul) utan att behöva skapa och registrera snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="cc22c-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc22c-123">Se även</span><span class="sxs-lookup"><span data-stu-id="cc22c-123">See Also</span></span>

[<span data-ttu-id="cc22c-124">Förstå en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="cc22c-125">Hur du skriver en PowerShell-skript-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="cc22c-126">Hur du skriver en binär PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="cc22c-127">Så här skriver du ett PowerShell-modulen Manifest</span><span class="sxs-lookup"><span data-stu-id="cc22c-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="cc22c-128">Ändra installationssökvägen PSModulePath</span><span class="sxs-lookup"><span data-stu-id="cc22c-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="cc22c-129">Importera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="cc22c-130">Installera en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="cc22c-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
