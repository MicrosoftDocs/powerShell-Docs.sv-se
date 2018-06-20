---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Galleriet Söksyntax
ms.openlocfilehash: 52fca21a00bcc6e3789bceb331acf5bc771bb0f2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188419"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="69a3c-103">Galleriet Söksyntax</span><span class="sxs-lookup"><span data-stu-id="69a3c-103">Gallery Search Syntax</span></span>

<span data-ttu-id="69a3c-104">PowerShell-galleriet erbjuder en text searchbox där du kan använda ord och fraser nyckelordet uttryck för att begränsa sökresultatet.</span><span class="sxs-lookup"><span data-stu-id="69a3c-104">PowerShell Gallery offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="69a3c-105">Sök efter nyckelord</span><span class="sxs-lookup"><span data-stu-id="69a3c-105">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="69a3c-106">Sök gör sitt bästa för att hitta relevanta dokument som innehåller alla 3 nyckelord och returnera matchande dokument.</span><span class="sxs-lookup"><span data-stu-id="69a3c-106">Search will do its best effort to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="69a3c-107">Sökningen med fraser och nyckelord</span><span class="sxs-lookup"><span data-stu-id="69a3c-107">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="69a3c-108">Ange en fras inom citattecken (””) Ändra söker efter en viss fras i stället för separata nyckelord.</span><span class="sxs-lookup"><span data-stu-id="69a3c-108">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="69a3c-109">Matchande dokument ska vanligtvis innehålla frasen ”azure sql”, inklusive på versaler t.ex. ”Azure SQL”, och även vanligtvis innehåller ordet ”distribution”.</span><span class="sxs-lookup"><span data-stu-id="69a3c-109">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="69a3c-110">Filtrering på fält</span><span class="sxs-lookup"><span data-stu-id="69a3c-110">Filtering on fields</span></span>

<span data-ttu-id="69a3c-111">Du kan söka efter ett specifikt objekt-ID (eller ”Id” eller ”id”) eller vissa fält med Sök villkor med fältnamnet.</span><span class="sxs-lookup"><span data-stu-id="69a3c-111">You can search for a specific item ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="69a3c-112">Sökbara fält är för närvarande ”Id”, ”Version”, ”-taggar', 'Författare',” ägare ”,” funktioner', 'Cmdlets', 'DscResources' och 'PowerShellVersion'.</span><span class="sxs-lookup"><span data-stu-id="69a3c-112">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="69a3c-113">[Vad är skillnaden mellan ID och titel?</span><span class="sxs-lookup"><span data-stu-id="69a3c-113">[What's the difference between ID and Title?</span></span> <span data-ttu-id="69a3c-114">ID: T är det namn som du använder i konsolen.</span><span class="sxs-lookup"><span data-stu-id="69a3c-114">ID is the name you use in the console.</span></span> <span data-ttu-id="69a3c-115">Rubriken är vad som visas överst på sidan objektet i sökresultaten.]</span><span class="sxs-lookup"><span data-stu-id="69a3c-115">Title is what is shown at the top of the item page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="69a3c-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="69a3c-116">Examples</span></span>

    ID:"PSReadline"
    id:"AzureRM.Profile"

<span data-ttu-id="69a3c-117">Sök efter objekt med ”PSReadline” eller ”AzureRM.Profile” i ID-fältet respektive.</span><span class="sxs-lookup"><span data-stu-id="69a3c-117">finds items with "PSReadline" or "AzureRM.Profile" in their ID field respectively.</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="69a3c-118">är ett annat sätt att hitta objekt med ”AzureRM.Profile” i ID-fältet.</span><span class="sxs-lookup"><span data-stu-id="69a3c-118">is another way to find items with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="69a3c-119">”Id”-filtret är en understräng matchar, så om du söker efter följande:</span><span class="sxs-lookup"><span data-stu-id="69a3c-119">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="69a3c-120">Du får resultat som 'AzureRM.Profile' och 'Azure.Storage'.</span><span class="sxs-lookup"><span data-stu-id="69a3c-120">You'll get results like 'AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="69a3c-121">Du kan också söka efter flera nyckelord i ett enda fält.</span><span class="sxs-lookup"><span data-stu-id="69a3c-121">You can also search for multiple keywords in a single field.</span></span> <span data-ttu-id="69a3c-122">Eller blanda och matcha fält.</span><span class="sxs-lookup"><span data-stu-id="69a3c-122">Or mix and match fields.</span></span>

    id:azure tags:intellisense
    id:azure id:storage

<span data-ttu-id="69a3c-123">Och du kan utföra sökningar fras:</span><span class="sxs-lookup"><span data-stu-id="69a3c-123">And you can perform phrase searches:</span></span>

    id:"azure.storage"


<span data-ttu-id="69a3c-124">För att söka alla objekt med DSC-tagg.</span><span class="sxs-lookup"><span data-stu-id="69a3c-124">To search all items with DSC tag.</span></span>

    Tags:"DSC"

<span data-ttu-id="69a3c-125">För att söka alla objekt med angiven funktion.</span><span class="sxs-lookup"><span data-stu-id="69a3c-125">To search all items with the specified function.</span></span>

    Functions:"Update-AzureRM"

<span data-ttu-id="69a3c-126">För att söka alla objekt med den angivna cmdleten.</span><span class="sxs-lookup"><span data-stu-id="69a3c-126">To search all items with the specified cmdlet.</span></span>

    Cmdlets:"Get-AzureRmEnvironment"

<span data-ttu-id="69a3c-127">För att söka alla objekt med det angivna namnet för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="69a3c-127">To search all items with the specified DSC Resource name.</span></span>

    DscResources:"xArchive"

<span data-ttu-id="69a3c-128">Att söka efter alla objekt med den angivna PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="69a3c-128">To search all items with the specified PowerShellVersion</span></span>

    PowerShellVersion:"5.0"
    PowerShellVersion:"3.0"
    PowerShellVersion:"2.0"


<span data-ttu-id="69a3c-129">Slutligen, om du använder ett fält inte stöds, till exempel kommandon, vi bara ignorera det och söka i alla fält.</span><span class="sxs-lookup"><span data-stu-id="69a3c-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="69a3c-130">Därför följande fråga</span><span class="sxs-lookup"><span data-stu-id="69a3c-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="69a3c-131">Är tolkas exakt samma sätt som den här frågan:</span><span class="sxs-lookup"><span data-stu-id="69a3c-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage