---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Gallerisökning
ms.openlocfilehash: 9aadb6771c85845cc3fa05cb56f0194b060d1c1b
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004147"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="1167c-103">Gallerisökning</span><span class="sxs-lookup"><span data-stu-id="1167c-103">Gallery Search Syntax</span></span>

<span data-ttu-id="1167c-104">PowerShell-galleriet erbjuder en text searchbox där du kan använda ord och fraser nyckelordet uttryck för att begränsa sökresultaten.</span><span class="sxs-lookup"><span data-stu-id="1167c-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="1167c-105">Sök efter nyckelord</span><span class="sxs-lookup"><span data-stu-id="1167c-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="1167c-106">Sök gör sitt bästa för att hitta relevant dokument som innehåller alla 3 nyckelord och returnera matchande dokument.</span><span class="sxs-lookup"><span data-stu-id="1167c-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="1167c-107">Söka med fraser och nyckelord</span><span class="sxs-lookup"><span data-stu-id="1167c-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="1167c-108">Att ange en fras mellan citattecken (””) Ändra söker efter en viss fras i stället för separata nyckelord.</span><span class="sxs-lookup"><span data-stu-id="1167c-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="1167c-109">Matchande dokument ska vanligtvis innehålla exakt fras ”azure sql”, inklusive varianter på förtroendeingivande t.ex. ”Azure SQL”, och även vanligtvis innehåller ordet ”distribution”.</span><span class="sxs-lookup"><span data-stu-id="1167c-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="1167c-110">Filtrering på fält</span><span class="sxs-lookup"><span data-stu-id="1167c-110">Filtering on fields</span></span>

<span data-ttu-id="1167c-111">Du kan söka efter en viss paket-ID (eller ”Id” eller ”id”) eller vissa andra fält genom Sök villkor med fältnamnet.</span><span class="sxs-lookup"><span data-stu-id="1167c-111">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="1167c-112">De sökbara fälten är för närvarande ”Id”, ”Version”, ”-taggar”, ”författare”, 'Owner', 'Funktioner', 'Cmdletar', 'DscResources' och 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="1167c-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="1167c-113">[Vad är skillnaden mellan ID och rubrik?</span><span class="sxs-lookup"><span data-stu-id="1167c-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="1167c-114">ID: T är det namn som du använder i konsolen.</span><span class="sxs-lookup"><span data-stu-id="1167c-114">ID is the name you use in the console.</span></span> <span data-ttu-id="1167c-115">Rubriken är vad som ska visas överst på sidan package i sökresultaten.]</span><span class="sxs-lookup"><span data-stu-id="1167c-115">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="1167c-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="1167c-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="1167c-117">söker efter paket med ”PSReadline” eller ”AzureRM.Profile” i ID-fältet respektive.</span><span class="sxs-lookup"><span data-stu-id="1167c-117">finds packages with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="1167c-118">är ett annat sätt att hitta paket med ”AzureRM.Profile” i ID-fältet.</span><span class="sxs-lookup"><span data-stu-id="1167c-118">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="1167c-119">”Id”-filtret är en understräng matchar, så om du söker efter följande:</span><span class="sxs-lookup"><span data-stu-id="1167c-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="1167c-120">Du får resultat som 'AzureRM.Profile' och 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="1167c-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="1167c-121">Du kan också söka efter flera nyckelord i ett enda fält.</span><span class="sxs-lookup"><span data-stu-id="1167c-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="1167c-122">Eller blanda och matcha fält.</span><span class="sxs-lookup"><span data-stu-id="1167c-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="1167c-123">Och du kan utföra frasen sökningar:</span><span class="sxs-lookup"><span data-stu-id="1167c-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="1167c-124">Att söka efter alla paket med DSC-tagg.</span><span class="sxs-lookup"><span data-stu-id="1167c-124">To search all packages with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="1167c-125">Att söka efter alla paket med den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="1167c-125">To search all packages with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="1167c-126">Att söka efter alla paket med angivna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1167c-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="1167c-127">Att söka efter alla paket med det angivna namnet för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="1167c-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="1167c-128">Att söka efter alla paket med den angivna PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="1167c-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="1167c-129">Slutligen, om du använder ett fält som inte stöds, till exempel kommandon, vi bara ignorera det och söka i alla fält.</span><span class="sxs-lookup"><span data-stu-id="1167c-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="1167c-130">Så följande fråga</span><span class="sxs-lookup"><span data-stu-id="1167c-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="1167c-131">Är tolkas exakt samma som den här frågan:</span><span class="sxs-lookup"><span data-stu-id="1167c-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
