---
ms.date: 07/29/2020
keywords: powershell,cmdlet
ms.topic: how-to
title: Använda PowerShell-dokumentationen
description: I den här artikeln beskrivs hur du använder funktionerna i den här webbplatsen, inklusive Sök filtrering och versions val.
ms.openlocfilehash: 4779e6e4b17c461d71e9d613d1184b9ce2e7ab7b
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216090"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="3b6b1-104">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="3b6b1-104">How to use the PowerShell documentation</span></span>

<span data-ttu-id="3b6b1-105">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-105">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="3b6b1-106">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="3b6b1-106">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="3b6b1-107">PowerShell 7,2 (för hands version)</span><span class="sxs-lookup"><span data-stu-id="3b6b1-107">PowerShell 7.2 (prerelease)</span></span>
- <span data-ttu-id="3b6b1-108">PowerShell 7,1 (aktuell)</span><span class="sxs-lookup"><span data-stu-id="3b6b1-108">PowerShell 7.1 (current)</span></span>
- <span data-ttu-id="3b6b1-109">PowerShell 7,0 (LTS)</span><span class="sxs-lookup"><span data-stu-id="3b6b1-109">PowerShell 7.0 (LTS)</span></span>
- <span data-ttu-id="3b6b1-110">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="3b6b1-110">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="3b6b1-111">Hitta artiklar och välja en version</span><span class="sxs-lookup"><span data-stu-id="3b6b1-111">Finding articles and selecting a version</span></span>

<span data-ttu-id="3b6b1-112">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-112">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="3b6b1-113">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-113">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="3b6b1-114">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-114">The page displays a list of matching articles.</span></span> <span data-ttu-id="3b6b1-115">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-115">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="3b6b1-116">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-116">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="3b6b1-117">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-117">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="3b6b1-118">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-118">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="3b6b1-119">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-119">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Använda versions väljaren](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="3b6b1-121">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion` värdet.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-121">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="3b6b1-122">I följande exempel visas utdata för Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-122">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="3b6b1-123">Om du inte har använt PowerShell igen och behöver hjälp med att förstå kommandosyntaxen, se [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span><span class="sxs-lookup"><span data-stu-id="3b6b1-123">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="3b6b1-124">Hitta artiklar för tidigare versioner</span><span class="sxs-lookup"><span data-stu-id="3b6b1-124">Finding articles for previous versions</span></span>

<span data-ttu-id="3b6b1-125">Dokumentationen för äldre versioner av PowerShell har arkiverats på vår [tidigare versions](https://aka.ms/PSLegacyDocs) webbplats.</span><span class="sxs-lookup"><span data-stu-id="3b6b1-125">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="3b6b1-126">Den här platsen innehåller dokumentation för följande ämnen:</span><span class="sxs-lookup"><span data-stu-id="3b6b1-126">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="3b6b1-127">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="3b6b1-127">PowerShell 3.0</span></span>
- <span data-ttu-id="3b6b1-128">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="3b6b1-128">PowerShell 4.0</span></span>
- <span data-ttu-id="3b6b1-129">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3b6b1-129">PowerShell 5.0</span></span>
- <span data-ttu-id="3b6b1-130">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="3b6b1-130">PowerShell 6</span></span>
- <span data-ttu-id="3b6b1-131">PowerShell-arbetsflöden</span><span class="sxs-lookup"><span data-stu-id="3b6b1-131">PowerShell Workflows</span></span>
- <span data-ttu-id="3b6b1-132">PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="3b6b1-132">PowerShell Web Access</span></span>
