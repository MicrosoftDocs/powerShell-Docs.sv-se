---
description: Beskriver hur du använder jokertecken i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 4778de5022f35f354e7783cedc5019198d11604b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272493"
---
# <a name="about-wildcards"></a><span data-ttu-id="84419-104">Om jokertecken</span><span class="sxs-lookup"><span data-stu-id="84419-104">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="84419-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="84419-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="84419-106">Beskriver hur du använder jokertecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84419-106">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="84419-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="84419-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="84419-108">Jokertecken representerar ett eller flera tecken.</span><span class="sxs-lookup"><span data-stu-id="84419-108">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="84419-109">Du kan använda dem för att skapa ord mönster i kommandon.</span><span class="sxs-lookup"><span data-stu-id="84419-109">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="84419-110">Om du till exempel vill hämta alla filer i `C:\Techdocs` katalogen med ett `.ppt` fil namns tillägg skriver du:</span><span class="sxs-lookup"><span data-stu-id="84419-110">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="84419-111">I det här fallet representerar asterisken ( `*` ) jokertecknet alla tecken som visas före `.ppt` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="84419-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="84419-112">PowerShell har stöd för följande jokertecken:</span><span class="sxs-lookup"><span data-stu-id="84419-112">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="84419-113">Användning</span><span class="sxs-lookup"><span data-stu-id="84419-113">Wildcard</span></span>|<span data-ttu-id="84419-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84419-114">Description</span></span>               |<span data-ttu-id="84419-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="84419-115">Example</span></span> |<span data-ttu-id="84419-116">Matchning</span><span class="sxs-lookup"><span data-stu-id="84419-116">Match</span></span>        |<span data-ttu-id="84419-117">Ingen matchning</span><span class="sxs-lookup"><span data-stu-id="84419-117">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="84419-118">Matcha inga eller flera tecken</span><span class="sxs-lookup"><span data-stu-id="84419-118">Match zero or more characters</span></span> | <span data-ttu-id="84419-119">en\*</span><span class="sxs-lookup"><span data-stu-id="84419-119">a\*</span></span>  | <span data-ttu-id="84419-120">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="84419-120">aA, ag, Apple</span></span> | <span data-ttu-id="84419-121">banan</span><span class="sxs-lookup"><span data-stu-id="84419-121">banana</span></span> |
|<span data-ttu-id="84419-122">?</span><span class="sxs-lookup"><span data-stu-id="84419-122">?</span></span>       |<span data-ttu-id="84419-123">Matcha ett Character i den positionen</span><span class="sxs-lookup"><span data-stu-id="84419-123">Match one character in that position</span></span> | <span data-ttu-id="84419-124">? n</span><span class="sxs-lookup"><span data-stu-id="84419-124">?n</span></span> | <span data-ttu-id="84419-125">en, i, på</span><span class="sxs-lookup"><span data-stu-id="84419-125">an, in, on</span></span> | <span data-ttu-id="84419-126">kördes</span><span class="sxs-lookup"><span data-stu-id="84419-126">ran</span></span> |
|<span data-ttu-id="84419-127">\[ \]</span><span class="sxs-lookup"><span data-stu-id="84419-127">\[ \]</span></span>   |<span data-ttu-id="84419-128">Matcha ett tecken intervall</span><span class="sxs-lookup"><span data-stu-id="84419-128">Match a range of characters</span></span> | <span data-ttu-id="84419-129">\[a-l- \] ook</span><span class="sxs-lookup"><span data-stu-id="84419-129">\[a-l\]ook</span></span> | <span data-ttu-id="84419-130">bok, Cook, utseende</span><span class="sxs-lookup"><span data-stu-id="84419-130">book, cook, look</span></span> | <span data-ttu-id="84419-131">skrev</span><span class="sxs-lookup"><span data-stu-id="84419-131">took</span></span> |
|<span data-ttu-id="84419-132">\[ \]</span><span class="sxs-lookup"><span data-stu-id="84419-132">\[ \]</span></span>   |<span data-ttu-id="84419-133">Matcha vissa tecken</span><span class="sxs-lookup"><span data-stu-id="84419-133">Match specific characters</span></span> | <span data-ttu-id="84419-134">\[BC- \] ook</span><span class="sxs-lookup"><span data-stu-id="84419-134">\[bc\]ook</span></span> | <span data-ttu-id="84419-135">bok, Cook</span><span class="sxs-lookup"><span data-stu-id="84419-135">book, cook</span></span> | <span data-ttu-id="84419-136">uttryckt</span><span class="sxs-lookup"><span data-stu-id="84419-136">hook</span></span> |

<span data-ttu-id="84419-137">Du kan inkludera flera jokertecken i samma ord mönster.</span><span class="sxs-lookup"><span data-stu-id="84419-137">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="84419-138">Om du till exempel vill söka efter textfiler med namn som börjar med bokstäverna **a** till **l** , skriver du:</span><span class="sxs-lookup"><span data-stu-id="84419-138">For example, to find text files with names that begin with the letters **a** through **l** , type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="84419-139">Många cmdlets accepterar jokertecken i parameter värden.</span><span class="sxs-lookup"><span data-stu-id="84419-139">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="84419-140">I hjälp avsnittet för varje cmdlet beskrivs vilka parametrar som accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="84419-140">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="84419-141">För parametrar som accepterar jokertecken är deras användning Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="84419-141">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="84419-142">Du kan använda jokertecken i kommandon och skript block, till exempel för att skapa ett ord mönster som representerar egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="84419-142">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="84419-143">Följande kommando hämtar till exempel tjänster där egenskap svärdet **ServiceType** inkluderar **Interactive**.</span><span class="sxs-lookup"><span data-stu-id="84419-143">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="84419-144">I följande exempel `If` innehåller instruktionen ett villkor som använder jokertecken för att hitta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="84419-144">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="84419-145">Om återställnings punktens **Beskrivning** innehåller **PowerShell** lägger kommandot till värdet för återställnings punktens **CreationTime** -egenskap till en loggfil.</span><span class="sxs-lookup"><span data-stu-id="84419-145">If the restore point's **Description** includes **PowerShell** , the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="84419-146">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="84419-146">SEE ALSO</span></span>

[<span data-ttu-id="84419-147">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="84419-147">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="84419-148">about_If</span><span class="sxs-lookup"><span data-stu-id="84419-148">about_If</span></span>](about_If.md)

[<span data-ttu-id="84419-149">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="84419-149">about_Script_Blocks</span></span>](about_Script_Blocks.md)

