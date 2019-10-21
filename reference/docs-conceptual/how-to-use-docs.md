---
ms.date: 10/20/2019
keywords: PowerShell, cmdlet
title: Använda PowerShell-dokumentationen
ms.openlocfilehash: 80f72bb89b3bb82ee7c4d16b8969395f02d7d4ca
ms.sourcegitcommit: ac1ccdd826f112a11db09af9c628cae013f947ab
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/20/2019
ms.locfileid: "72676177"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="9ae16-103">Använda PowerShell-dokumentationen</span><span class="sxs-lookup"><span data-stu-id="9ae16-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="9ae16-104">Välkommen till PowerShell-onlinedokumentationen.</span><span class="sxs-lookup"><span data-stu-id="9ae16-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="9ae16-105">Den här platsen innehåller cmdlet-referens för följande versioner av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9ae16-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="9ae16-106">PowerShell 7 (för hands version)</span><span class="sxs-lookup"><span data-stu-id="9ae16-106">PowerShell 7 (preview)</span></span>
- <span data-ttu-id="9ae16-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="9ae16-107">PowerShell 6</span></span>
- <span data-ttu-id="9ae16-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="9ae16-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="9ae16-109">Hitta artiklar och välja en version</span><span class="sxs-lookup"><span data-stu-id="9ae16-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="9ae16-110">Det finns två sätt att söka efter innehåll i dokument. Det enklaste sättet är att använda filter rutan under versions väljaren.</span><span class="sxs-lookup"><span data-stu-id="9ae16-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="9ae16-111">Skriv bara ett ord som visas i rubriken för en artikel.</span><span class="sxs-lookup"><span data-stu-id="9ae16-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="9ae16-112">Sidan visar en lista över matchande artiklar.</span><span class="sxs-lookup"><span data-stu-id="9ae16-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="9ae16-113">Du kan också välja alternativet att söka igenom hela webbplatsen från listan.</span><span class="sxs-lookup"><span data-stu-id="9ae16-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="9ae16-114">Som standard visar den här webbplatsen dokumentationen för den senaste utgivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ae16-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="9ae16-115">Vissa cmdletar fungerar annorlunda i olika versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ae16-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="9ae16-116">Se till att du läser dokumentationen för den version av PowerShell som du använder.</span><span class="sxs-lookup"><span data-stu-id="9ae16-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="9ae16-117">Använd versions väljaren överst på sidan för att välja den version av PowerShell som du vill använda.</span><span class="sxs-lookup"><span data-stu-id="9ae16-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![versions väljare](images/how-to-use-docs/version-search.gif)

<span data-ttu-id="9ae16-119">Du kan kontrol lera vilken version av PowerShell du använder genom att kontrol lera `$PSversionTable.PSVersion`-värdet.</span><span class="sxs-lookup"><span data-stu-id="9ae16-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="9ae16-120">I följande exempel visas utdata för Windows PowerShell v 5.1.</span><span class="sxs-lookup"><span data-stu-id="9ae16-120">The following example shows the output for Windows PowerShell v5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      18362  145
```
