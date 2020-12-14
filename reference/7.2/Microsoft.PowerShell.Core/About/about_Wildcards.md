---
description: Beskriver hur du använder jokertecken i PowerShell.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: b5f13fdbfbc24e19e5ad0b1cd6ecc1b99f68914f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709649"
---
# <a name="about-wildcards"></a><span data-ttu-id="d6adc-103">Om jokertecken</span><span class="sxs-lookup"><span data-stu-id="d6adc-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="d6adc-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d6adc-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d6adc-105">Beskriver hur du använder jokertecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d6adc-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d6adc-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d6adc-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="d6adc-107">Jokertecken representerar ett eller flera tecken.</span><span class="sxs-lookup"><span data-stu-id="d6adc-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="d6adc-108">Du kan använda dem för att skapa ord mönster i kommandon.</span><span class="sxs-lookup"><span data-stu-id="d6adc-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="d6adc-109">Om du till exempel vill hämta alla filer i `C:\Techdocs` katalogen med ett `.ppt` fil namns tillägg skriver du:</span><span class="sxs-lookup"><span data-stu-id="d6adc-109">For example, to get all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="d6adc-110">I det här fallet representerar asterisken ( `*` ) jokertecknet alla tecken som visas före `.ppt` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="d6adc-110">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="d6adc-111">PowerShell har stöd för följande jokertecken:</span><span class="sxs-lookup"><span data-stu-id="d6adc-111">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="d6adc-112">Användning</span><span class="sxs-lookup"><span data-stu-id="d6adc-112">Wildcard</span></span>|<span data-ttu-id="d6adc-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d6adc-113">Description</span></span>               |<span data-ttu-id="d6adc-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="d6adc-114">Example</span></span> |<span data-ttu-id="d6adc-115">Matchning</span><span class="sxs-lookup"><span data-stu-id="d6adc-115">Match</span></span>        |<span data-ttu-id="d6adc-116">Ingen matchning</span><span class="sxs-lookup"><span data-stu-id="d6adc-116">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="d6adc-117">Matcha inga eller flera tecken</span><span class="sxs-lookup"><span data-stu-id="d6adc-117">Match zero or more characters</span></span> | <span data-ttu-id="d6adc-118">en\*</span><span class="sxs-lookup"><span data-stu-id="d6adc-118">a\*</span></span>  | <span data-ttu-id="d6adc-119">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="d6adc-119">aA, ag, Apple</span></span> | <span data-ttu-id="d6adc-120">banan</span><span class="sxs-lookup"><span data-stu-id="d6adc-120">banana</span></span> |
|<span data-ttu-id="d6adc-121">?</span><span class="sxs-lookup"><span data-stu-id="d6adc-121">?</span></span>       |<span data-ttu-id="d6adc-122">Matcha ett Character i den positionen</span><span class="sxs-lookup"><span data-stu-id="d6adc-122">Match one character in that position</span></span> | <span data-ttu-id="d6adc-123">? n</span><span class="sxs-lookup"><span data-stu-id="d6adc-123">?n</span></span> | <span data-ttu-id="d6adc-124">en, i, på</span><span class="sxs-lookup"><span data-stu-id="d6adc-124">an, in, on</span></span> | <span data-ttu-id="d6adc-125">kördes</span><span class="sxs-lookup"><span data-stu-id="d6adc-125">ran</span></span> |
|<span data-ttu-id="d6adc-126">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d6adc-126">\[ \]</span></span>   |<span data-ttu-id="d6adc-127">Matcha ett tecken intervall</span><span class="sxs-lookup"><span data-stu-id="d6adc-127">Match a range of characters</span></span> | <span data-ttu-id="d6adc-128">\[a-l- \] ook</span><span class="sxs-lookup"><span data-stu-id="d6adc-128">\[a-l\]ook</span></span> | <span data-ttu-id="d6adc-129">bok, Cook, utseende</span><span class="sxs-lookup"><span data-stu-id="d6adc-129">book, cook, look</span></span> | <span data-ttu-id="d6adc-130">skrev</span><span class="sxs-lookup"><span data-stu-id="d6adc-130">took</span></span> |
|<span data-ttu-id="d6adc-131">\[ \]</span><span class="sxs-lookup"><span data-stu-id="d6adc-131">\[ \]</span></span>   |<span data-ttu-id="d6adc-132">Matcha vissa tecken</span><span class="sxs-lookup"><span data-stu-id="d6adc-132">Match specific characters</span></span> | <span data-ttu-id="d6adc-133">\[BC- \] ook</span><span class="sxs-lookup"><span data-stu-id="d6adc-133">\[bc\]ook</span></span> | <span data-ttu-id="d6adc-134">bok, Cook</span><span class="sxs-lookup"><span data-stu-id="d6adc-134">book, cook</span></span> | <span data-ttu-id="d6adc-135">uttryckt</span><span class="sxs-lookup"><span data-stu-id="d6adc-135">hook</span></span> |

<span data-ttu-id="d6adc-136">Du kan inkludera flera jokertecken i samma ord mönster.</span><span class="sxs-lookup"><span data-stu-id="d6adc-136">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="d6adc-137">Om du till exempel vill söka efter textfiler med namn som börjar med bokstäverna **a** till **l**, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d6adc-137">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="d6adc-138">Många cmdlets accepterar jokertecken i parameter värden.</span><span class="sxs-lookup"><span data-stu-id="d6adc-138">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="d6adc-139">I hjälp avsnittet för varje cmdlet beskrivs vilka parametrar som accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d6adc-139">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="d6adc-140">För parametrar som accepterar jokertecken är deras användning Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="d6adc-140">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="d6adc-141">Du kan använda jokertecken i kommandon och skript block, till exempel för att skapa ett ord mönster som representerar egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="d6adc-141">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="d6adc-142">Följande kommando hämtar till exempel tjänster där egenskap svärdet **ServiceType** inkluderar **Interactive**.</span><span class="sxs-lookup"><span data-stu-id="d6adc-142">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="d6adc-143">I följande exempel `If` innehåller instruktionen ett villkor som använder jokertecken för att hitta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="d6adc-143">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="d6adc-144">Om återställnings punktens **Beskrivning** innehåller **PowerShell** lägger kommandot till värdet för återställnings punktens **CreationTime** -egenskap till en loggfil.</span><span class="sxs-lookup"><span data-stu-id="d6adc-144">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d6adc-145">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="d6adc-145">SEE ALSO</span></span>

[<span data-ttu-id="d6adc-146">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="d6adc-146">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="d6adc-147">about_If</span><span class="sxs-lookup"><span data-stu-id="d6adc-147">about_If</span></span>](about_If.md)

[<span data-ttu-id="d6adc-148">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="d6adc-148">about_Script_Blocks</span></span>](about_Script_Blocks.md)

