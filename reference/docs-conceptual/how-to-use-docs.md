---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 259eb1eea1dc7e8b5ae5730f97c938b838a320bf
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808273"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="f955e-103">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="f955e-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="f955e-104">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="f955e-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="f955e-105">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f955e-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="f955e-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="f955e-106">PowerShell 7</span></span>
- <span data-ttu-id="f955e-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="f955e-107">PowerShell 6</span></span>
- <span data-ttu-id="f955e-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="f955e-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="f955e-109">Hitta artiklar och välja en version</span><span class="sxs-lookup"><span data-stu-id="f955e-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="f955e-110">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="f955e-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="f955e-111">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="f955e-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="f955e-112">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="f955e-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="f955e-113">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="f955e-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="f955e-114">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f955e-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="f955e-115">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f955e-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="f955e-116">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="f955e-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="f955e-117">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="f955e-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![versionsväljare](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="f955e-119">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion` värdet.</span><span class="sxs-lookup"><span data-stu-id="f955e-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="f955e-120">I följande exempel visas utdata för Windows PowerShell v 5.1.</span><span class="sxs-lookup"><span data-stu-id="f955e-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="f955e-121">Hitta artiklar för tidigare versioner</span><span class="sxs-lookup"><span data-stu-id="f955e-121">Finding articles for previous versions</span></span>

<span data-ttu-id="f955e-122">Dokumentationen för äldre versioner av PowerShell har arkiverats på vår [tidigare versions](https://aka.ms/PSLegacyDocs) webbplats.</span><span class="sxs-lookup"><span data-stu-id="f955e-122">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="f955e-123">Den här platsen innehåller dokumentation för följande ämnen:</span><span class="sxs-lookup"><span data-stu-id="f955e-123">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="f955e-124">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="f955e-124">PowerShell 3.0</span></span>
- <span data-ttu-id="f955e-125">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="f955e-125">PowerShell 4.0</span></span>
- <span data-ttu-id="f955e-126">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f955e-126">PowerShell 5.0</span></span>
- <span data-ttu-id="f955e-127">PowerShell-arbetsflöden</span><span class="sxs-lookup"><span data-stu-id="f955e-127">PowerShell Workflows</span></span>
- <span data-ttu-id="f955e-128">PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="f955e-128">PowerShell Web Access</span></span>
