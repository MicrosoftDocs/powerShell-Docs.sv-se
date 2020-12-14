---
description: Innehåller viktig information om objekt i PowerShell.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_objects?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Objects
ms.openlocfilehash: bfb66e72a74d20379123558b85047097dc801e9d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710572"
---
# <a name="about-objects"></a><span data-ttu-id="96a56-103">Om objekt</span><span class="sxs-lookup"><span data-stu-id="96a56-103">About Objects</span></span>

## <a name="short-description"></a><span data-ttu-id="96a56-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="96a56-104">Short Description</span></span>
<span data-ttu-id="96a56-105">Innehåller viktig information om objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96a56-105">Provides essential information about objects in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="96a56-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="96a56-106">Long Description</span></span>

<span data-ttu-id="96a56-107">Varje åtgärd som du utför i PowerShell sker inom kontexten för objekt.</span><span class="sxs-lookup"><span data-stu-id="96a56-107">Every action you take in PowerShell occurs within the context of objects.</span></span> <span data-ttu-id="96a56-108">När data flyttas från ett kommando till nästa, flyttas det som ett eller flera identifierbara objekt.</span><span class="sxs-lookup"><span data-stu-id="96a56-108">As data moves from one command to the next, it moves as one or more identifiable objects.</span></span> <span data-ttu-id="96a56-109">Ett objekt är en samling data som representerar ett objekt.</span><span class="sxs-lookup"><span data-stu-id="96a56-109">An object, then, is a collection of data that represents an item.</span></span> <span data-ttu-id="96a56-110">Ett objekt består av tre typer av data: objekt typ, dess metoder och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="96a56-110">An object is made up of three types of data: the objects type, its methods, and its properties.</span></span>

## <a name="types-methods-and-properties"></a><span data-ttu-id="96a56-111">Typer, metoder och egenskaper</span><span class="sxs-lookup"><span data-stu-id="96a56-111">Types, Methods, and Properties</span></span>

<span data-ttu-id="96a56-112">Objekt typen visar vilken typ av objekt den är.</span><span class="sxs-lookup"><span data-stu-id="96a56-112">The object type tells what kind of object it is.</span></span> <span data-ttu-id="96a56-113">Ett objekt som representerar en fil är till exempel ett FileInfo-objekt.</span><span class="sxs-lookup"><span data-stu-id="96a56-113">For example, an object that represents a file is a FileInfo object.</span></span>

<span data-ttu-id="96a56-114">Objekt metoderna är åtgärder som du kan utföra på objektet.</span><span class="sxs-lookup"><span data-stu-id="96a56-114">The object methods are actions that you can perform on the object.</span></span>
<span data-ttu-id="96a56-115">FileInfo-objekt har till exempel en CopyTo-metod som du kan använda för att kopiera filen.</span><span class="sxs-lookup"><span data-stu-id="96a56-115">For example, FileInfo objects have a CopyTo method that you can use to copy the file.</span></span>

<span data-ttu-id="96a56-116">Objekt egenskaper lagrar information om objektet.</span><span class="sxs-lookup"><span data-stu-id="96a56-116">Object properties store information about the object.</span></span> <span data-ttu-id="96a56-117">FileInfo-objekt har till exempel en LastWriteTime-egenskap som lagrar datum och tid då filen senast öppnades.</span><span class="sxs-lookup"><span data-stu-id="96a56-117">For example, FileInfo objects have a LastWriteTime property that stores the date and time that the file was most recently accessed.</span></span>

<span data-ttu-id="96a56-118">När du arbetar med objekt kan du använda deras metoder och egenskaper i kommandon för att vidta åtgärder och hantera data.</span><span class="sxs-lookup"><span data-stu-id="96a56-118">When working with objects, you can use their methods and properties in commands to take action and manage data.</span></span>

## <a name="objects-in-pipelines"></a><span data-ttu-id="96a56-119">Objekt i pipelines</span><span class="sxs-lookup"><span data-stu-id="96a56-119">Objects in Pipelines</span></span>

<span data-ttu-id="96a56-120">När kommandon kombineras i en pipeline skickar de information till varandra som objekt.</span><span class="sxs-lookup"><span data-stu-id="96a56-120">When commands are combined in a pipeline, they pass information to each other as objects.</span></span> <span data-ttu-id="96a56-121">När det första kommandot körs skickar det ett eller flera objekt nedåt i pipelinen till det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="96a56-121">When the first command runs, it sends one or more objects down the pipeline to the second command.</span></span> <span data-ttu-id="96a56-122">Det andra kommandot tar emot objekten från det första kommandot, bearbetar objekten och skickar sedan nya eller ändrade objekt till nästa kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="96a56-122">The second command receives the objects from the first command, processes the objects, and then passes new or revised objects to the next command in the pipeline.</span></span>
<span data-ttu-id="96a56-123">Detta fortsätter tills alla kommandon i pipelinen har körts.</span><span class="sxs-lookup"><span data-stu-id="96a56-123">This continues until all commands in the pipeline run.</span></span>

<span data-ttu-id="96a56-124">Följande exempel visar hur objekt skickas från ett kommando till nästa:</span><span class="sxs-lookup"><span data-stu-id="96a56-124">The following example demonstrates how objects are passed from one command to the next:</span></span>

```powershell
Get-ChildItem C: | where { $_.PsIsContainer -eq $false } | Format-List
```

<span data-ttu-id="96a56-125">Det första kommandot `Get-ChildItem C:` returnerar ett fil-eller katalog objekt för varje objekt i rot katalogen i fil systemet.</span><span class="sxs-lookup"><span data-stu-id="96a56-125">The first command `Get-ChildItem C:` returns a file or directory object for each item in the root directory of the file system.</span></span> <span data-ttu-id="96a56-126">Filen och katalog-objekten har passerat pipelinen till det andra kommandot.</span><span class="sxs-lookup"><span data-stu-id="96a56-126">The file and directory objects are passed down the pipeline to the second command.</span></span>

<span data-ttu-id="96a56-127">Det andra kommandot `where { $_.PsIsContainer -eq $false }` använder egenskapen PsIsContainer för alla fil system objekt för att välja filer, som har värdet FALSKT ( \$ falskt) i sin PsIsContainer-egenskap.</span><span class="sxs-lookup"><span data-stu-id="96a56-127">The second command `where { $_.PsIsContainer -eq $false }` uses the PsIsContainer property of all file system objects to select only files, which have a value of False (\$false) in their PsIsContainer property.</span></span> <span data-ttu-id="96a56-128">Mappar, som är behållare och har därför värdet sant ( \$ sant) i sin PsIsContainer-egenskap, inte markerade.</span><span class="sxs-lookup"><span data-stu-id="96a56-128">Folders, which are containers and, thus, have a value of True (\$true) in their PsIsContainer property, are not selected.</span></span>

<span data-ttu-id="96a56-129">Det andra kommandot skickar bara filobjekten till det tredje kommandot `Format-List` , som visar fil objekt i en lista.</span><span class="sxs-lookup"><span data-stu-id="96a56-129">The second command passes only the file objects to the third command `Format-List`, which displays the file objects in a list.</span></span>

## <a name="see-also"></a><span data-ttu-id="96a56-130">Se även</span><span class="sxs-lookup"><span data-stu-id="96a56-130">See Also</span></span>

[<span data-ttu-id="96a56-131">about_Methods</span><span class="sxs-lookup"><span data-stu-id="96a56-131">about_Methods</span></span>](about_Methods.md)

[<span data-ttu-id="96a56-132">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="96a56-132">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="96a56-133">about_Properties</span><span class="sxs-lookup"><span data-stu-id="96a56-133">about_Properties</span></span>](about_Properties.md)

[<span data-ttu-id="96a56-134">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="96a56-134">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="96a56-135">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="96a56-135">Get-Member</span></span>](xref:Microsoft.PowerShell.Utility.Get-Member)

