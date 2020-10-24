---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: Använda PowerShell-dokumentationen
description: I den här artikeln beskrivs hur du använder funktionerna i den här webbplatsen, inklusive Sök filtrering och versions val.
ms.openlocfilehash: 32f0c613e10329cc4830386b744e766eeeab0187
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501124"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="1e32e-104">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="1e32e-104">How to use the PowerShell documentation</span></span>

<span data-ttu-id="1e32e-105">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="1e32e-105">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="1e32e-106">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="1e32e-106">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="1e32e-107">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="1e32e-107">PowerShell 7</span></span>
- <span data-ttu-id="1e32e-108">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="1e32e-108">PowerShell 6</span></span>
- <span data-ttu-id="1e32e-109">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="1e32e-109">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="1e32e-110">Hitta artiklar och välja en version</span><span class="sxs-lookup"><span data-stu-id="1e32e-110">Finding articles and selecting a version</span></span>

<span data-ttu-id="1e32e-111">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="1e32e-111">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="1e32e-112">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="1e32e-112">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="1e32e-113">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="1e32e-113">The page displays a list of matching articles.</span></span> <span data-ttu-id="1e32e-114">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="1e32e-114">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="1e32e-115">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e32e-115">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="1e32e-116">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e32e-116">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="1e32e-117">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="1e32e-117">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="1e32e-118">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="1e32e-118">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Använda versions väljaren](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="1e32e-120">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion` värdet.</span><span class="sxs-lookup"><span data-stu-id="1e32e-120">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="1e32e-121">I följande exempel visas utdata för Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="1e32e-121">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="1e32e-122">Om du inte har använt PowerShell igen och behöver hjälp med att förstå kommandosyntaxen, se [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span><span class="sxs-lookup"><span data-stu-id="1e32e-122">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="1e32e-123">Hitta artiklar för tidigare versioner</span><span class="sxs-lookup"><span data-stu-id="1e32e-123">Finding articles for previous versions</span></span>

<span data-ttu-id="1e32e-124">Dokumentationen för äldre versioner av PowerShell har arkiverats på vår [tidigare versions](https://aka.ms/PSLegacyDocs) webbplats.</span><span class="sxs-lookup"><span data-stu-id="1e32e-124">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="1e32e-125">Den här platsen innehåller dokumentation för följande ämnen:</span><span class="sxs-lookup"><span data-stu-id="1e32e-125">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="1e32e-126">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="1e32e-126">PowerShell 3.0</span></span>
- <span data-ttu-id="1e32e-127">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="1e32e-127">PowerShell 4.0</span></span>
- <span data-ttu-id="1e32e-128">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1e32e-128">PowerShell 5.0</span></span>
- <span data-ttu-id="1e32e-129">PowerShell-arbetsflöden</span><span class="sxs-lookup"><span data-stu-id="1e32e-129">PowerShell Workflows</span></span>
- <span data-ttu-id="1e32e-130">PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="1e32e-130">PowerShell Web Access</span></span>
