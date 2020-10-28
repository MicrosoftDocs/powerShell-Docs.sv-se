---
ms.date: 06/12/2017
title: Syntax för Galleri sökning
description: I den här artikeln beskrivs användar gränssnittet som används för att söka efter innehåll i PowerShell-galleriet.
ms.openlocfilehash: 7ad486095647f99056b37c2ca1a50db099a166c0
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661371"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="a305c-103">Syntax för Galleri sökning</span><span class="sxs-lookup"><span data-stu-id="a305c-103">Gallery Search Syntax</span></span>

<span data-ttu-id="a305c-104">Du kan söka i PowerShell-galleriet med hjälp av [PowerShell-galleriets webbplats](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="a305c-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span> <span data-ttu-id="a305c-105">PowerShell-galleriet webbplats innehåller en text Sök ruta där du kan använda uttryck för ord, fraser och nyckelord för att begränsa Sök resultaten.</span><span class="sxs-lookup"><span data-stu-id="a305c-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="a305c-106">Sök med nyckelord</span><span class="sxs-lookup"><span data-stu-id="a305c-106">Search by Keywords</span></span>

```Syntax
dsc azure sql
```

<span data-ttu-id="a305c-107">Sök försöker hitta relevanta dokument som innehåller alla tre nyckelord och returnera matchande dokument.</span><span class="sxs-lookup"><span data-stu-id="a305c-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="a305c-108">Sök med fraser och nyckelord</span><span class="sxs-lookup"><span data-stu-id="a305c-108">Search using Phrases and keywords</span></span>

```Syntax
"azure sql" deployment
```

<span data-ttu-id="a305c-109">Ange en fras mellan citat tecken ("") ändra sökningen så att den söker efter den specifika frasen i stället för separata nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a305c-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span> <span data-ttu-id="a305c-110">Matchning av dokument bör vanligt vis innehålla den exakta frasen "Azure SQL", inklusive variationer i versaler, t. ex. "Azure SQL" och innehåller vanligt vis ordet "Deployment".</span><span class="sxs-lookup"><span data-stu-id="a305c-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="a305c-111">Filtrera på fält</span><span class="sxs-lookup"><span data-stu-id="a305c-111">Filtering on fields</span></span>

<span data-ttu-id="a305c-112">Du kan söka efter ett visst paket-ID (eller "ID" eller "ID") eller vissa andra fält genom att förkorrigera Sök termer med fält namnet.</span><span class="sxs-lookup"><span data-stu-id="a305c-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="a305c-113">För närvarande är de sökbara fälten "ID", "version", "Tags", "author", "Owner", "Functions", "cmdlets", "DscResources" och "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="a305c-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

- <span data-ttu-id="a305c-114">ID är det namn som du använder i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="a305c-114">ID is the name you use in the console.</span></span>
- <span data-ttu-id="a305c-115">Rubriken är vad som visas överst på sidan paket i Sök resultaten.</span><span class="sxs-lookup"><span data-stu-id="a305c-115">Title is what is shown at the top of the package page in search results.</span></span>

## <a name="examples"></a><span data-ttu-id="a305c-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="a305c-116">Examples</span></span>

```Syntax
ID:PSReadline
```

<span data-ttu-id="a305c-117">söker efter paket med ett ID som innehåller "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="a305c-117">finds packages with an ID containing "PSReadline".</span></span>

```Syntax
Id:"AzureRM.Profile"
```

<span data-ttu-id="a305c-118">är ett annat sätt att hitta paket med "AzureRM. profile" i sitt ID-fält.</span><span class="sxs-lookup"><span data-stu-id="a305c-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="a305c-119">Filtret "ID" är en del Strängs matchning, så om du söker efter följande:</span><span class="sxs-lookup"><span data-stu-id="a305c-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

```Syntax
Id:"azure"
```

<span data-ttu-id="a305c-120">Detta ger resultat som inkluderar AzureRM. Profile och Azure. Storage.</span><span class="sxs-lookup"><span data-stu-id="a305c-120">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="a305c-121">Du kan också söka efter flera nyckelord i ett enda fält.</span><span class="sxs-lookup"><span data-stu-id="a305c-121">You can also search for multiple keywords in a single field.</span></span>

```Syntax
id:azure tags:intellisense
```

<span data-ttu-id="a305c-122">Och du kan utföra fras sökningar med dubbla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="a305c-122">And you can perform phrase searches using double quotes:</span></span>

```Syntax
id:"azure.storage"
```

<span data-ttu-id="a305c-123">Om du vill söka i alla paket med DSC-tagg.</span><span class="sxs-lookup"><span data-stu-id="a305c-123">To search all packages with DSC tag.</span></span>

```Syntax
Tags:DSC
```

<span data-ttu-id="a305c-124">Om du vill söka igenom alla paket med den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="a305c-124">To search all packages with the specified function.</span></span>

```Syntax
Functions:Get-TreeSize
```

<span data-ttu-id="a305c-125">Om du vill söka igenom alla paket med angiven cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a305c-125">To search all packages with the specified cmdlet.</span></span>

```Syntax
Cmdlets:Get-AzureRmEnvironment
```

<span data-ttu-id="a305c-126">Om du vill söka igenom alla paket med det angivna DSC-resursnamnet.</span><span class="sxs-lookup"><span data-stu-id="a305c-126">To search all packages with the specified DSC Resource name.</span></span>

```Syntax
DscResources:xArchive
```

<span data-ttu-id="a305c-127">Söka igenom alla paket med den angivna PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="a305c-127">To search all packages with the specified PowerShellVersion</span></span>

```Syntax
PowerShellVersion:2.0
```

<span data-ttu-id="a305c-128">Slutligen, om du använder ett fält som vi inte stöder, till exempel "kommandon", så ignorerar vi bara det och söker i alla fält.</span><span class="sxs-lookup"><span data-stu-id="a305c-128">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="a305c-129">Så följande fråga</span><span class="sxs-lookup"><span data-stu-id="a305c-129">So the following query</span></span>

```Syntax
commands:blobs storage
```

<span data-ttu-id="a305c-130">Tolkas exakt på samma sätt som den här frågan:</span><span class="sxs-lookup"><span data-stu-id="a305c-130">Is interpreted exactly the same as this query:</span></span>

```Syntax
blobs storage
```
