---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Syntax för Galleri sökning
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71329157"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="556fa-103">Syntax för Galleri sökning</span><span class="sxs-lookup"><span data-stu-id="556fa-103">Gallery Search Syntax</span></span>

<span data-ttu-id="556fa-104">Du kan söka i PowerShell-galleriet med hjälp av [PowerShell-galleriets webbplats](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="556fa-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="556fa-105">PowerShell-galleriet webbplats innehåller en text Sök ruta där du kan använda uttryck för ord, fraser och nyckelord för att begränsa Sök resultaten.</span><span class="sxs-lookup"><span data-stu-id="556fa-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="556fa-106">Sök med nyckelord</span><span class="sxs-lookup"><span data-stu-id="556fa-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="556fa-107">Sök försöker hitta relevanta dokument som innehåller alla tre nyckelord och returnera matchande dokument.</span><span class="sxs-lookup"><span data-stu-id="556fa-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="556fa-108">Sök med fraser och nyckelord</span><span class="sxs-lookup"><span data-stu-id="556fa-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="556fa-109">Ange en fras mellan citat tecken ("") ändra sökningen så att den söker efter den specifika frasen i stället för separata nyckelord.</span><span class="sxs-lookup"><span data-stu-id="556fa-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="556fa-110">Matchning av dokument bör vanligt vis innehålla den exakta frasen "Azure SQL", inklusive variationer på versaler, t. ex. "Azure SQL" och innehåller vanligt vis ordet "Deployment".</span><span class="sxs-lookup"><span data-stu-id="556fa-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="556fa-111">Filtrera på fält</span><span class="sxs-lookup"><span data-stu-id="556fa-111">Filtering on fields</span></span>

<span data-ttu-id="556fa-112">Du kan söka efter ett visst paket-ID (eller "ID" eller "ID") eller vissa andra fält genom att förkorrigera Sök termer med fält namnet.</span><span class="sxs-lookup"><span data-stu-id="556fa-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="556fa-113">För närvarande är de sökbara fälten "ID", "version", "Tags", "author", "Owner", "Functions", "cmdlets", "DscResources" och "PowerShellVersion".</span><span class="sxs-lookup"><span data-stu-id="556fa-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="556fa-114">[Vad är skillnaden mellan ID och rubrik?</span><span class="sxs-lookup"><span data-stu-id="556fa-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="556fa-115">ID är det namn som du använder i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="556fa-115">ID is the name you use in the console.</span></span> <span data-ttu-id="556fa-116">Rubriken är vad som visas överst på sidan paket i Sök resultaten.]</span><span class="sxs-lookup"><span data-stu-id="556fa-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="556fa-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="556fa-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="556fa-118">söker efter paket med ett ID som innehåller "PSReadline".</span><span class="sxs-lookup"><span data-stu-id="556fa-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="556fa-119">är ett annat sätt att hitta paket med "AzureRM. profile" i sitt ID-fält.</span><span class="sxs-lookup"><span data-stu-id="556fa-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="556fa-120">Filtret "ID" är en del Strängs matchning, så om du söker efter följande:</span><span class="sxs-lookup"><span data-stu-id="556fa-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="556fa-121">Detta ger resultat som inkluderar AzureRM. Profile och Azure. Storage.</span><span class="sxs-lookup"><span data-stu-id="556fa-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="556fa-122">Du kan också söka efter flera nyckelord i ett enda fält.</span><span class="sxs-lookup"><span data-stu-id="556fa-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="556fa-123">Och du kan utföra fras sökningar med dubbla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="556fa-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="556fa-124">Om du vill söka i alla paket med DSC-tagg.</span><span class="sxs-lookup"><span data-stu-id="556fa-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="556fa-125">Om du vill söka igenom alla paket med den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="556fa-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="556fa-126">Om du vill söka igenom alla paket med angiven cmdlet.</span><span class="sxs-lookup"><span data-stu-id="556fa-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="556fa-127">Om du vill söka igenom alla paket med det angivna DSC-resursnamnet.</span><span class="sxs-lookup"><span data-stu-id="556fa-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="556fa-128">Söka igenom alla paket med den angivna PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="556fa-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="556fa-129">Slutligen, om du använder ett fält som vi inte stöder, till exempel "kommandon", så ignorerar vi bara det och söker i alla fält.</span><span class="sxs-lookup"><span data-stu-id="556fa-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="556fa-130">Så följande fråga</span><span class="sxs-lookup"><span data-stu-id="556fa-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="556fa-131">Tolkas exakt på samma sätt som den här frågan:</span><span class="sxs-lookup"><span data-stu-id="556fa-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
