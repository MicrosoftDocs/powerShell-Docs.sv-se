---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 1cfeb9eea564e7618062e1b8ada4948bd9e22969
ms.sourcegitcommit: 9f9eb95bc859e9e0fed48101327a602b2ced351d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87821537"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="91d38-103">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="91d38-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="91d38-104">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="91d38-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="91d38-105">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="91d38-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="91d38-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="91d38-106">PowerShell 7</span></span>
- <span data-ttu-id="91d38-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="91d38-107">PowerShell 6</span></span>
- <span data-ttu-id="91d38-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="91d38-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="91d38-109">Hitta artiklar och välja en version</span><span class="sxs-lookup"><span data-stu-id="91d38-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="91d38-110">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="91d38-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="91d38-111">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="91d38-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="91d38-112">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="91d38-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="91d38-113">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="91d38-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="91d38-114">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91d38-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="91d38-115">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91d38-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="91d38-116">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="91d38-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="91d38-117">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="91d38-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![Använda versions väljaren](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="91d38-119">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion` värdet.</span><span class="sxs-lookup"><span data-stu-id="91d38-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="91d38-120">I följande exempel visas utdata för Windows PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="91d38-120">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="91d38-121">Om du inte har använt PowerShell igen och behöver hjälp med att förstå kommandosyntaxen, se [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span><span class="sxs-lookup"><span data-stu-id="91d38-121">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="91d38-122">Hitta artiklar för tidigare versioner</span><span class="sxs-lookup"><span data-stu-id="91d38-122">Finding articles for previous versions</span></span>

<span data-ttu-id="91d38-123">Dokumentationen för äldre versioner av PowerShell har arkiverats på vår [tidigare versions](https://aka.ms/PSLegacyDocs) webbplats.</span><span class="sxs-lookup"><span data-stu-id="91d38-123">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="91d38-124">Den här platsen innehåller dokumentation för följande ämnen:</span><span class="sxs-lookup"><span data-stu-id="91d38-124">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="91d38-125">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="91d38-125">PowerShell 3.0</span></span>
- <span data-ttu-id="91d38-126">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="91d38-126">PowerShell 4.0</span></span>
- <span data-ttu-id="91d38-127">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="91d38-127">PowerShell 5.0</span></span>
- <span data-ttu-id="91d38-128">PowerShell-arbetsflöden</span><span class="sxs-lookup"><span data-stu-id="91d38-128">PowerShell Workflows</span></span>
- <span data-ttu-id="91d38-129">PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="91d38-129">PowerShell Web Access</span></span>
