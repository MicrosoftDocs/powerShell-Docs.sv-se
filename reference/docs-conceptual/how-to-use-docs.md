---
ms.date: 09/25/2019
keywords: PowerShell, cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 9e3d5828d6bdb4ef14701994f146354a041efaea
ms.sourcegitcommit: a80bb79b85deab8ae3c21de56d1ee432fdd92628
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72281645"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="8a680-103">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="8a680-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="8a680-104">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="8a680-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="8a680-105">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8a680-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="8a680-106">PowerShell 7 (för hands version)</span><span class="sxs-lookup"><span data-stu-id="8a680-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="8a680-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="8a680-107">PowerShell 6</span></span>
- <span data-ttu-id="8a680-108">PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="8a680-108">PowerShell 5.1</span></span>
- <span data-ttu-id="8a680-109">PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="8a680-109">PowerShell 5.0</span></span>
- <span data-ttu-id="8a680-110">PowerShell 4,0</span><span class="sxs-lookup"><span data-stu-id="8a680-110">PowerShell 4.0</span></span>
- <span data-ttu-id="8a680-111">PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="8a680-111">PowerShell 3.0</span></span>

## <a name="selecting-your-version"></a><span data-ttu-id="8a680-112">Välja din version</span><span class="sxs-lookup"><span data-stu-id="8a680-112">Selecting your version</span></span>

<span data-ttu-id="8a680-113">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a680-113">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="8a680-114">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8a680-114">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="8a680-115">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="8a680-115">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="8a680-116">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="8a680-116">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![versions väljare](images/how-to-use-docs/picker-vall.gif)

<span data-ttu-id="8a680-118">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion`-värdet.</span><span class="sxs-lookup"><span data-stu-id="8a680-118">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="8a680-119">I följande exempel visas utdata för Windows PowerShell v 5.1.</span><span class="sxs-lookup"><span data-stu-id="8a680-119">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```

## <a name="searching-for-articles"></a><span data-ttu-id="8a680-120">Söker efter artiklar</span><span class="sxs-lookup"><span data-stu-id="8a680-120">Searching for articles</span></span>

<span data-ttu-id="8a680-121">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="8a680-121">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="8a680-122">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="8a680-122">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="8a680-123">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="8a680-123">The page displays a list of matching articles.</span></span> <span data-ttu-id="8a680-124">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="8a680-124">You can also select the option to search the entire site from that list.</span></span>

![filter ruta](images/how-to-use-docs/filter-search.gif)
