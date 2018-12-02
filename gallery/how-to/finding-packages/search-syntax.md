---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Gallerisökning
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e24525046dd37166b9d83eeecdc534726316f429
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/01/2018
ms.locfileid: "52742864"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="f33cf-103">Gallerisökning</span><span class="sxs-lookup"><span data-stu-id="f33cf-103">Gallery Search Syntax</span></span>

<span data-ttu-id="f33cf-104">Du kan söka i PowerShell-galleriet med hjälp av den [PowerShell-galleriet webbplats](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="f33cf-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="f33cf-105">Webbplats för PowerShell-galleriet erbjuder en text searchbox där du kan använda ord och fraser nyckelordet uttryck för att begränsa sökresultaten.</span><span class="sxs-lookup"><span data-stu-id="f33cf-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="f33cf-106">Sök efter nyckelord</span><span class="sxs-lookup"><span data-stu-id="f33cf-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="f33cf-107">Sök försöker hitta relevant dokument som innehåller alla 3 nyckelord och returnera matchande dokument.</span><span class="sxs-lookup"><span data-stu-id="f33cf-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="f33cf-108">Söka med fraser och nyckelord</span><span class="sxs-lookup"><span data-stu-id="f33cf-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="f33cf-109">Att ange en fras mellan citattecken (””) Ändra söker efter en viss fras i stället för separata nyckelord.</span><span class="sxs-lookup"><span data-stu-id="f33cf-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="f33cf-110">Matchande dokument ska vanligtvis innehålla exakt fras ”azure sql”, inklusive varianter på förtroendeingivande t.ex. ”Azure SQL”, och även vanligtvis innehåller ordet ”distribution”.</span><span class="sxs-lookup"><span data-stu-id="f33cf-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="f33cf-111">Filtrering på fält</span><span class="sxs-lookup"><span data-stu-id="f33cf-111">Filtering on fields</span></span>

<span data-ttu-id="f33cf-112">Du kan söka efter en viss paket-ID (eller ”Id” eller ”id”) eller vissa andra fält genom Sök villkor med fältnamnet.</span><span class="sxs-lookup"><span data-stu-id="f33cf-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="f33cf-113">De sökbara fälten är för närvarande ”Id”, ”Version”, ”-taggar”, ”författare”, 'Owner', 'Funktioner', 'Cmdletar', 'DscResources' och 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="f33cf-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="f33cf-114">[Vad är skillnaden mellan ID och rubrik?</span><span class="sxs-lookup"><span data-stu-id="f33cf-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="f33cf-115">ID: T är det namn som du använder i konsolen.</span><span class="sxs-lookup"><span data-stu-id="f33cf-115">ID is the name you use in the console.</span></span> <span data-ttu-id="f33cf-116">Rubriken är vad som ska visas överst på sidan package i sökresultaten.]</span><span class="sxs-lookup"><span data-stu-id="f33cf-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="f33cf-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="f33cf-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="f33cf-118">söker efter paket med ett ID som innehåller ”PSReadline”.</span><span class="sxs-lookup"><span data-stu-id="f33cf-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="f33cf-119">är ett annat sätt att hitta paket med ”AzureRM.Profile” i ID-fältet.</span><span class="sxs-lookup"><span data-stu-id="f33cf-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="f33cf-120">”Id”-filtret är en understräng matchar, så om du söker efter följande:</span><span class="sxs-lookup"><span data-stu-id="f33cf-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="f33cf-121">Detta ger resultat som innehåller AzureRM.Profile' och 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="f33cf-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="f33cf-122">Du kan också söka efter flera nyckelord i ett enda fält.</span><span class="sxs-lookup"><span data-stu-id="f33cf-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="f33cf-123">Och du kan utföra frasen sökningar med dubbla citattecken:</span><span class="sxs-lookup"><span data-stu-id="f33cf-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="f33cf-124">Att söka efter alla paket med DSC-tagg.</span><span class="sxs-lookup"><span data-stu-id="f33cf-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="f33cf-125">Att söka efter alla paket med den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="f33cf-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="f33cf-126">Att söka efter alla paket med angivna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f33cf-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="f33cf-127">Att söka efter alla paket med det angivna namnet för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="f33cf-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="f33cf-128">Att söka efter alla paket med den angivna PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="f33cf-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="f33cf-129">Slutligen, om du använder ett fält som inte stöds, till exempel kommandon, vi bara ignorera det och söka i alla fält.</span><span class="sxs-lookup"><span data-stu-id="f33cf-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="f33cf-130">Så följande fråga</span><span class="sxs-lookup"><span data-stu-id="f33cf-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="f33cf-131">Är tolkas exakt samma som den här frågan:</span><span class="sxs-lookup"><span data-stu-id="f33cf-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
