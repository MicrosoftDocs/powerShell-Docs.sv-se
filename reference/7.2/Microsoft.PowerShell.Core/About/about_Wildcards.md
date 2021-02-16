---
description: Beskriver hur du använder jokertecken i PowerShell.
Locale: en-US
ms.date: 02/13/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wildcards?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Wildcards
ms.openlocfilehash: 40620e54bb889d683192b346f3ba1c139895e4d0
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529982"
---
# <a name="about-wildcards"></a><span data-ttu-id="eb1c0-103">Om jokertecken</span><span class="sxs-lookup"><span data-stu-id="eb1c0-103">About Wildcards</span></span>

## <a name="short-description"></a><span data-ttu-id="eb1c0-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eb1c0-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="eb1c0-105">Beskriver hur du använder jokertecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-105">Describes how to use wildcard characters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="eb1c0-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eb1c0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="eb1c0-107">Jokertecken representerar ett eller flera tecken.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-107">Wildcard characters represent one or many characters.</span></span> <span data-ttu-id="eb1c0-108">Du kan använda dem för att skapa ord mönster i kommandon.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-108">You can use them to create word patterns in commands.</span></span> <span data-ttu-id="eb1c0-109">Jokertecken används med `-like` operatorn eller med en parameter som accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-109">Wildcard expressions are used with the `-like` operator or with any parameter that accepts wildcards.</span></span>

<span data-ttu-id="eb1c0-110">Om du till exempel vill matcha alla filer i `C:\Techdocs` katalogen med ett `.ppt` fil namns tillägg skriver du:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-110">For example, to match all the files in the `C:\Techdocs` directory with a `.ppt` file name extension, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\*.ppt
```

<span data-ttu-id="eb1c0-111">I det här fallet representerar asterisken ( `*` ) jokertecknet alla tecken som visas före `.ppt` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-111">In this case, the asterisk (`*`) wildcard character represents any characters that appear before the `.ppt` file name extension.</span></span>

<span data-ttu-id="eb1c0-112">Jokertecken är enklare än vanliga uttryck.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-112">Wildcard expressions are simpler than regular expressions.</span></span> <span data-ttu-id="eb1c0-113">Mer information finns i [about_Regular_Expressions](./about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eb1c0-113">For more information, see [about_Regular_Expressions](./about_Regular_Expressions.md).</span></span>

<span data-ttu-id="eb1c0-114">PowerShell har stöd för följande jokertecken:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-114">PowerShell supports the following wildcard characters:</span></span>

|<span data-ttu-id="eb1c0-115">Användning</span><span class="sxs-lookup"><span data-stu-id="eb1c0-115">Wildcard</span></span>|<span data-ttu-id="eb1c0-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="eb1c0-116">Description</span></span>               |<span data-ttu-id="eb1c0-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="eb1c0-117">Example</span></span> |<span data-ttu-id="eb1c0-118">Matchning</span><span class="sxs-lookup"><span data-stu-id="eb1c0-118">Match</span></span>        |<span data-ttu-id="eb1c0-119">Ingen matchning</span><span class="sxs-lookup"><span data-stu-id="eb1c0-119">No Match</span></span>|
|--------|--------------------------|--------|-------------|--------|
|\*      |<span data-ttu-id="eb1c0-120">Matcha inga eller flera tecken</span><span class="sxs-lookup"><span data-stu-id="eb1c0-120">Match zero or more characters</span></span> | <span data-ttu-id="eb1c0-121">en\*</span><span class="sxs-lookup"><span data-stu-id="eb1c0-121">a\*</span></span>  | <span data-ttu-id="eb1c0-122">aA, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="eb1c0-122">aA, ag, Apple</span></span> | <span data-ttu-id="eb1c0-123">banan</span><span class="sxs-lookup"><span data-stu-id="eb1c0-123">banana</span></span> |
|<span data-ttu-id="eb1c0-124">?</span><span class="sxs-lookup"><span data-stu-id="eb1c0-124">?</span></span>       |<span data-ttu-id="eb1c0-125">Matcha ett Character i den positionen</span><span class="sxs-lookup"><span data-stu-id="eb1c0-125">Match one character in that position</span></span> | <span data-ttu-id="eb1c0-126">? n</span><span class="sxs-lookup"><span data-stu-id="eb1c0-126">?n</span></span> | <span data-ttu-id="eb1c0-127">en, i, på</span><span class="sxs-lookup"><span data-stu-id="eb1c0-127">an, in, on</span></span> | <span data-ttu-id="eb1c0-128">kördes</span><span class="sxs-lookup"><span data-stu-id="eb1c0-128">ran</span></span> |
|<span data-ttu-id="eb1c0-129">\[ \]</span><span class="sxs-lookup"><span data-stu-id="eb1c0-129">\[ \]</span></span>   |<span data-ttu-id="eb1c0-130">Matcha ett tecken intervall</span><span class="sxs-lookup"><span data-stu-id="eb1c0-130">Match a range of characters</span></span> | <span data-ttu-id="eb1c0-131">\[a-l- \] ook</span><span class="sxs-lookup"><span data-stu-id="eb1c0-131">\[a-l\]ook</span></span> | <span data-ttu-id="eb1c0-132">bok, Cook, utseende</span><span class="sxs-lookup"><span data-stu-id="eb1c0-132">book, cook, look</span></span> | <span data-ttu-id="eb1c0-133">skrev</span><span class="sxs-lookup"><span data-stu-id="eb1c0-133">took</span></span> |
|<span data-ttu-id="eb1c0-134">\[ \]</span><span class="sxs-lookup"><span data-stu-id="eb1c0-134">\[ \]</span></span>   |<span data-ttu-id="eb1c0-135">Matcha vissa tecken</span><span class="sxs-lookup"><span data-stu-id="eb1c0-135">Match specific characters</span></span> | <span data-ttu-id="eb1c0-136">\[BC- \] ook</span><span class="sxs-lookup"><span data-stu-id="eb1c0-136">\[bc\]ook</span></span> | <span data-ttu-id="eb1c0-137">bok, Cook</span><span class="sxs-lookup"><span data-stu-id="eb1c0-137">book, cook</span></span> | <span data-ttu-id="eb1c0-138">uttryckt</span><span class="sxs-lookup"><span data-stu-id="eb1c0-138">hook</span></span> |

<span data-ttu-id="eb1c0-139">Du kan inkludera flera jokertecken i samma ord mönster.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-139">You can include multiple wildcard characters in the same word pattern.</span></span> <span data-ttu-id="eb1c0-140">Om du till exempel vill söka efter textfiler med namn som börjar med bokstäverna **a** till **l**, skriver du:</span><span class="sxs-lookup"><span data-stu-id="eb1c0-140">For example, to find text files with names that begin with the letters **a** through **l**, type:</span></span>

```powershell
Get-ChildItem C:\Techdocs\[a-l]*.txt
```

<span data-ttu-id="eb1c0-141">Många cmdlets accepterar jokertecken i parameter värden.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-141">Many cmdlets accept wildcard characters in parameter values.</span></span> <span data-ttu-id="eb1c0-142">I hjälp avsnittet för varje cmdlet beskrivs vilka parametrar som accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-142">The Help topic for each cmdlet describes which parameters accept wildcard characters.</span></span> <span data-ttu-id="eb1c0-143">För parametrar som accepterar jokertecken är deras användning Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-143">For parameters that accept wildcard characters, their use is case-insensitive.</span></span>

<span data-ttu-id="eb1c0-144">Du kan använda jokertecken i kommandon och skript block, till exempel för att skapa ett ord mönster som representerar egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-144">You can use wildcard characters in commands and script blocks, such as to create a word pattern that represents property values.</span></span> <span data-ttu-id="eb1c0-145">Följande kommando hämtar till exempel tjänster där egenskap svärdet **ServiceType** inkluderar **Interactive**.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-145">For example, the following command gets services in which the **ServiceType** property value includes **Interactive**.</span></span>

```powershell
Get-Service | Where-Object {$_.ServiceType -Like "*Interactive*"}
```

<span data-ttu-id="eb1c0-146">I följande exempel `If` innehåller instruktionen ett villkor som använder jokertecken för att hitta egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-146">In the following example, the `If` statement includes a condition that uses wildcard characters to find property values.</span></span> <span data-ttu-id="eb1c0-147">Om återställnings punktens **Beskrivning** innehåller **PowerShell** lägger kommandot till värdet för återställnings punktens **CreationTime** -egenskap till en loggfil.</span><span class="sxs-lookup"><span data-stu-id="eb1c0-147">If the restore point's **Description** includes **PowerShell**, the command adds the value of the restore point's **CreationTime** property to a log file.</span></span>

```powershell
$p = Get-ComputerRestorePoint
foreach ($point in $p) {
  if ($point.description -like "*PowerShell*") {
    Add-Content -Path C:\TechDocs\RestoreLog.txt "$($point.CreationTime)"
  }
}
```

## <a name="see-also"></a><span data-ttu-id="eb1c0-148">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="eb1c0-148">SEE ALSO</span></span>

[<span data-ttu-id="eb1c0-149">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="eb1c0-149">about_Language_Keywords</span></span>](about_Language_Keywords.md)

[<span data-ttu-id="eb1c0-150">about_If</span><span class="sxs-lookup"><span data-stu-id="eb1c0-150">about_If</span></span>](about_If.md)

[<span data-ttu-id="eb1c0-151">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="eb1c0-151">about_Script_Blocks</span></span>](about_Script_Blocks.md)

