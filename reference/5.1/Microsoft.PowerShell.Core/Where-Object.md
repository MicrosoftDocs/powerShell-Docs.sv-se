---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: aaee09926c93bb8c8e72efb5fd4ea34e2fc67391
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264099"
---
# <span data-ttu-id="8c519-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="8c519-103">Where-Object</span></span>

## <span data-ttu-id="8c519-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8c519-104">SYNOPSIS</span></span>
<span data-ttu-id="8c519-105">Väljer objekt från en samling baserat på deras egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="8c519-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="8c519-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c519-106">SYNTAX</span></span>

### <span data-ttu-id="8c519-107">EqualSet (standard)</span><span class="sxs-lookup"><span data-stu-id="8c519-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ] [<CommonParameters>]
```

### <span data-ttu-id="8c519-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="8c519-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="8c519-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="8c519-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Match]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CEQ] [<CommonParameters>]
```

### <span data-ttu-id="8c519-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="8c519-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GT] [<CommonParameters>]
```

### <span data-ttu-id="8c519-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="8c519-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGT] [<CommonParameters>]
```

### <span data-ttu-id="8c519-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="8c519-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LT] [<CommonParameters>]
```

### <span data-ttu-id="8c519-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="8c519-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLT] [<CommonParameters>]
```

### <span data-ttu-id="8c519-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-GE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CGE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-LE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="8c519-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLE] [<CommonParameters>]
```

### <span data-ttu-id="8c519-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="8c519-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Like] [<CommonParameters>]
```

### <span data-ttu-id="8c519-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c519-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CLike] [<CommonParameters>]
```

### <span data-ttu-id="8c519-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c519-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotLike] [<CommonParameters>]
```

### <span data-ttu-id="8c519-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="8c519-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotLike]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c519-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CMatch] [<CommonParameters>]
```

### <span data-ttu-id="8c519-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c519-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="8c519-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotMatch]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c519-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Contains]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c519-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CContains]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c519-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="8c519-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotContains]
 [<CommonParameters>]
```

### <span data-ttu-id="8c519-132">Luta</span><span class="sxs-lookup"><span data-stu-id="8c519-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-In] [<CommonParameters>]
```

### <span data-ttu-id="8c519-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="8c519-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CIn] [<CommonParameters>]
```

### <span data-ttu-id="8c519-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="8c519-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-NotIn] [<CommonParameters>]
```

### <span data-ttu-id="8c519-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="8c519-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-CNotIn] [<CommonParameters>]
```

### <span data-ttu-id="8c519-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="8c519-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-Is] [<CommonParameters>]
```

### <span data-ttu-id="8c519-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="8c519-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-IsNot] [<CommonParameters>]
```

## <span data-ttu-id="8c519-138">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8c519-138">DESCRIPTION</span></span>

<span data-ttu-id="8c519-139">`Where-Object`Cmdleten väljer objekt som har särskilda egenskaps värden från objekt samlingen som skickas till den.</span><span class="sxs-lookup"><span data-stu-id="8c519-139">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="8c519-140">Du kan till exempel använda `Where-Object` cmdleten för att välja filer som har skapats efter ett visst datum, händelser med ett visst ID eller datorer som använder en viss version av Windows.</span><span class="sxs-lookup"><span data-stu-id="8c519-140">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="8c519-141">Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="8c519-141">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="8c519-142">**Skript block**.</span><span class="sxs-lookup"><span data-stu-id="8c519-142">**Script block**.</span></span> <span data-ttu-id="8c519-143">Du kan använda ett-skript block för att ange egenskaps namn, en jämförelse operator och ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="8c519-143">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="8c519-144">`Where-Object` returnerar alla objekt som skript block instruktionen är sann för.</span><span class="sxs-lookup"><span data-stu-id="8c519-144">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="8c519-145">Följande kommando hämtar till exempel processer i normal prioritets klass, det vill säga processer där värdet för egenskapen **priorityClass** är lika med normal.</span><span class="sxs-lookup"><span data-stu-id="8c519-145">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="8c519-146">Alla PowerShell-jämförelse operatorer är giltiga i skript block formatet.</span><span class="sxs-lookup"><span data-stu-id="8c519-146">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="8c519-147">Mer information om jämförelse operatorer finns [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="8c519-147">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="8c519-148">**Jämförelse uttryck**.</span><span class="sxs-lookup"><span data-stu-id="8c519-148">**Comparison statement**.</span></span> <span data-ttu-id="8c519-149">Du kan också skriva en jämförelse instruktion, som är mycket mer likt naturligt språk.</span><span class="sxs-lookup"><span data-stu-id="8c519-149">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="8c519-150">Jämförelse uttryck introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-150">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="8c519-151">Följande kommandon får till exempel också processer som har prioritets klassen normal.</span><span class="sxs-lookup"><span data-stu-id="8c519-151">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="8c519-152">Dessa kommandon är likvärdiga och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="8c519-152">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="8c519-153">Från och med Windows PowerShell 3,0 `Where-Object` lägger till jämförelse operatorer som parametrar i ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="8c519-153">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="8c519-154">Om inget annat anges är alla operatorer Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="8c519-154">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="8c519-155">Före Windows PowerShell 3,0 kan jämförelse operatorerna i PowerShell-språket endast användas i skript block.</span><span class="sxs-lookup"><span data-stu-id="8c519-155">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="8c519-156">När du anger en enskild **egenskap** till `Where-Object` , behandlas värdet för egenskapen som ett booleskt uttryck.</span><span class="sxs-lookup"><span data-stu-id="8c519-156">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="8c519-157">Om värdet för **längd** inte är noll utvärderas uttrycket till **Sant**.</span><span class="sxs-lookup"><span data-stu-id="8c519-157">When the value of **Length** is not zero, the expression evaluates to **True**.</span></span> <span data-ttu-id="8c519-158">Exempelvis: `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="8c519-158">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="8c519-159">Det tidigare exemplet fungerar som en motsvarighet till:</span><span class="sxs-lookup"><span data-stu-id="8c519-159">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="8c519-160">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8c519-160">EXAMPLES</span></span>

### <span data-ttu-id="8c519-161">Exempel 1: Hämta stoppade tjänster</span><span class="sxs-lookup"><span data-stu-id="8c519-161">Example 1: Get stopped services</span></span>

<span data-ttu-id="8c519-162">De här kommandona hämtar en lista över alla tjänster som för närvarande är stoppade.</span><span class="sxs-lookup"><span data-stu-id="8c519-162">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="8c519-163">Den `$_` automatiska variabeln representerar varje objekt som skickas till `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8c519-163">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="8c519-164">Det första kommandot använder skript block formatet, det andra kommandot använder jämförelse uttryck formatet.</span><span class="sxs-lookup"><span data-stu-id="8c519-164">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="8c519-165">Kommandona är likvärdiga och kan användas utbytbara.</span><span class="sxs-lookup"><span data-stu-id="8c519-165">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="8c519-166">Exempel 2: Hämta processer baserat på arbets minnet</span><span class="sxs-lookup"><span data-stu-id="8c519-166">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="8c519-167">Kommandona visar en lista över processer som har en arbets mängd som är större än 250 megabyte (KB).</span><span class="sxs-lookup"><span data-stu-id="8c519-167">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="8c519-168">Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="8c519-168">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="8c519-169">Exempel 3: Hämta processer baserat på process namn</span><span class="sxs-lookup"><span data-stu-id="8c519-169">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="8c519-170">De här kommandona hämtar de processer som har ett värde för egenskapen **processname** som börjar med bokstaven `p` .</span><span class="sxs-lookup"><span data-stu-id="8c519-170">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="8c519-171">Med operatorn **match** kan du använda reguljära uttryck matchningar.</span><span class="sxs-lookup"><span data-stu-id="8c519-171">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="8c519-172">Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="8c519-172">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="8c519-173">Exempel 4: Använd formatet jämförelse uttryck</span><span class="sxs-lookup"><span data-stu-id="8c519-173">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="8c519-174">Det här exemplet visar hur du använder det nya jämförelse instruktions formatet för `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8c519-174">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="8c519-175">Det första kommandot använder jämförelse instruktions formatet.</span><span class="sxs-lookup"><span data-stu-id="8c519-175">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="8c519-176">I det här kommandot används inga alias och alla parametrar inkluderar parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="8c519-176">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="8c519-177">Det andra kommandot är den mer naturliga användningen av jämförelse kommando formatet.</span><span class="sxs-lookup"><span data-stu-id="8c519-177">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="8c519-178">`where`Aliaset ersätts med cmdlet- `Where-Object` namnet och alla valfria parameter namn utelämnas.</span><span class="sxs-lookup"><span data-stu-id="8c519-178">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="8c519-179">Exempel 5: Hämta kommandon baserat på egenskaper</span><span class="sxs-lookup"><span data-stu-id="8c519-179">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="8c519-180">Det här exemplet visar hur du skriver kommandon som returnerar objekt som är true eller false eller som har ett värde för en angiven egenskap.</span><span class="sxs-lookup"><span data-stu-id="8c519-180">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="8c519-181">I varje exempel visas formatet skript block och jämförelse uttryck för kommandot.</span><span class="sxs-lookup"><span data-stu-id="8c519-181">Each example shows both the script block and comparison statement formats for the command.</span></span>

```powershell
# Use Where-Object to get commands that have any value for the OutputType property of the command.
# This omits commands that do not have an OutputType property and those that have an OutputType property, but no property value.
Get-Command | where OutputType
Get-Command | where {$_.OutputType}
```

```powershell
# Use Where-Object to get objects that are containers.
# This gets objects that have the **PSIsContainer** property with a value of $True and excludes all others.
Get-ChildItem | where PSIsContainer
Get-ChildItem | where {$_.PSIsContainer}
```

```powershell
# Finally, use the Not operator (!) to get objects that are not containers.
# This gets objects that do have the **PSIsContainer** property and those that have a value of $False for the **PSIsContainer** property.
Get-ChildItem | where {!$_.PSIsContainer}
# You cannot use the Not operator (!) in the comparison statement format of the command.
Get-ChildItem | where PSIsContainer -eq $False
```

### <span data-ttu-id="8c519-182">Exempel 6: Använd flera villkor</span><span class="sxs-lookup"><span data-stu-id="8c519-182">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="8c519-183">Det här exemplet visar hur du skapar ett `Where-Object` kommando med flera villkor.</span><span class="sxs-lookup"><span data-stu-id="8c519-183">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="8c519-184">Det här kommandot hämtar moduler som inte är kärnan och som har stöd för den uppdaterbara hjälp funktionen.</span><span class="sxs-lookup"><span data-stu-id="8c519-184">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="8c519-185">Kommandot använder **ListAvailable** -parametern för `Get-Module` cmdleten för att hämta alla moduler på datorn.</span><span class="sxs-lookup"><span data-stu-id="8c519-185">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="8c519-186">En pipeline-operator ( `|` ) skickar modulerna till `Where-Object` cmdleten, som hämtar moduler vars namn inte börjar med Microsoft eller PS, och har ett värde för egenskapen **HelpInfoURI** , som talar om för PowerShell var du hittar uppdaterade hjälpfiler för modulen.</span><span class="sxs-lookup"><span data-stu-id="8c519-186">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="8c519-187">Jämförelse instruktionerna är anslutna med operatorn **och** den logiska operatorn.</span><span class="sxs-lookup"><span data-stu-id="8c519-187">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="8c519-188">I exemplet används skript blockets kommando format.</span><span class="sxs-lookup"><span data-stu-id="8c519-188">The example uses the script block command format.</span></span> <span data-ttu-id="8c519-189">Logiska operatorer, till **And** exempel och **och, är** bara giltiga i skript block.</span><span class="sxs-lookup"><span data-stu-id="8c519-189">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="8c519-190">Du kan inte använda dem i jämförelse instruktions formatet för ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="8c519-190">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="8c519-191">Mer information om logiska PowerShell-operatörer finns [about_Logical_Operators](./About/about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="8c519-191">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="8c519-192">Mer information om den uppdaterbara hjälp funktionen finns [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="8c519-192">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="8c519-193">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8c519-193">PARAMETERS</span></span>

### <span data-ttu-id="8c519-194">-CContains</span><span class="sxs-lookup"><span data-stu-id="8c519-194">-CContains</span></span>

<span data-ttu-id="8c519-195">Anger att denna cmdlet hämtar objekt från en samling om objektets egenskaps värde är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-195">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="8c519-196">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-196">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-197">Exempelvis: `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c519-197">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="8c519-198">**CContains** refererar till en samling värden och är true om samlingen innehåller ett objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-198">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="8c519-199">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-199">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-200">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-200">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-201">-CEQ</span><span class="sxs-lookup"><span data-stu-id="8c519-201">-CEQ</span></span>

<span data-ttu-id="8c519-202">Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-202">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="8c519-203">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-203">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-204">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-205">-CGE</span><span class="sxs-lookup"><span data-stu-id="8c519-205">-CGE</span></span>

<span data-ttu-id="8c519-206">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-206">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="8c519-207">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-207">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-208">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-209">-CGT</span><span class="sxs-lookup"><span data-stu-id="8c519-209">-CGT</span></span>

<span data-ttu-id="8c519-210">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-210">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="8c519-211">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-211">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-212">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-212">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveGreaterThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-213">-CIn</span><span class="sxs-lookup"><span data-stu-id="8c519-213">-CIn</span></span>

<span data-ttu-id="8c519-214">Anger att denna cmdlet hämtar objekt om egenskap svärdet innehåller det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-214">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="8c519-215">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-215">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-216">Exempelvis: `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c519-216">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="8c519-217">**CIn** liknar **CContains** , förutom att egenskaps-och värde positionerna är omvända.</span><span class="sxs-lookup"><span data-stu-id="8c519-217">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="8c519-218">Följande uttryck är till exempel båda sanna.</span><span class="sxs-lookup"><span data-stu-id="8c519-218">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="8c519-219">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-219">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-220">-CLE</span><span class="sxs-lookup"><span data-stu-id="8c519-220">-CLE</span></span>

<span data-ttu-id="8c519-221">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-221">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="8c519-222">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-222">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-223">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-223">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessOrEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-224">-CLike</span><span class="sxs-lookup"><span data-stu-id="8c519-224">-CLike</span></span>

<span data-ttu-id="8c519-225">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8c519-225">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="8c519-226">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-226">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-227">Exempelvis: `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c519-227">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="8c519-228">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-229">-CLT</span><span class="sxs-lookup"><span data-stu-id="8c519-229">-CLT</span></span>

<span data-ttu-id="8c519-230">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-230">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="8c519-231">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-231">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-232">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveLessThanSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-233">-CMatch</span><span class="sxs-lookup"><span data-stu-id="8c519-233">-CMatch</span></span>

<span data-ttu-id="8c519-234">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="8c519-234">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="8c519-235">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-235">This operation is case-sensitive.</span></span> <span data-ttu-id="8c519-236">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8c519-236">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c519-237">Exempelvis: `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="8c519-237">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="8c519-238">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-238">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-239">-CNE</span><span class="sxs-lookup"><span data-stu-id="8c519-239">-CNE</span></span>

<span data-ttu-id="8c519-240">Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-240">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="8c519-241">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-241">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-242">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotEqualSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-243">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="8c519-243">-CNotContains</span></span>

<span data-ttu-id="8c519-244">Anger att denna cmdlet hämtar objekt om objektets egenskaps värde inte är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-244">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="8c519-245">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-245">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-246">Exempelvis: `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c519-246">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="8c519-247">**NotContains** och **CNotContains** refererar till en samling värden och är sanna när samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-247">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="8c519-248">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-248">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-249">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotContainsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-250">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="8c519-250">-CNotIn</span></span>

<span data-ttu-id="8c519-251">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-251">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="8c519-252">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-252">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-253">Exempelvis: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c519-253">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="8c519-254">**NotIn** -och **CNotIn** -operatörer liknar **NotContains** och **CNotContains** , förutom att egenskaps-och värde positionerna är omvända.</span><span class="sxs-lookup"><span data-stu-id="8c519-254">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="8c519-255">Följande påståenden är till exempel sanna.</span><span class="sxs-lookup"><span data-stu-id="8c519-255">For example, the following statements are true.</span></span>

`"abc", "def" -CNotContains "Abc"`

`"abc" -CNotIn "Abc", "def"`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotInSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-256">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="8c519-256">-CNotLike</span></span>

<span data-ttu-id="8c519-257">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8c519-257">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="8c519-258">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-258">This operation is case-sensitive.</span></span>

<span data-ttu-id="8c519-259">Exempelvis: `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c519-259">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="8c519-260">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotLikeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-261">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="8c519-261">-CNotMatch</span></span>

<span data-ttu-id="8c519-262">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="8c519-262">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="8c519-263">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="8c519-263">This operation is case-sensitive.</span></span> <span data-ttu-id="8c519-264">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8c519-264">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c519-265">Exempelvis: `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="8c519-265">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="8c519-266">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-266">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CaseSensitiveNotMatchSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-267">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="8c519-267">-Contains</span></span>

<span data-ttu-id="8c519-268">Anger att denna cmdlet hämtar objekt om något objekt i objektets egenskaps värde är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-268">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="8c519-269">Exempelvis: `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c519-269">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="8c519-270">Om egenskap svärdet innehåller ett enda objekt konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-270">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-271">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainsSet
Aliases: IContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-272">-EQ</span><span class="sxs-lookup"><span data-stu-id="8c519-272">-EQ</span></span>

<span data-ttu-id="8c519-273">Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-273">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="8c519-274">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: EqualSet
Aliases: IEQ

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-275">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="8c519-275">-FilterScript</span></span>

<span data-ttu-id="8c519-276">Anger det skript block som används för att filtrera objekten.</span><span class="sxs-lookup"><span data-stu-id="8c519-276">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="8c519-277">Omge skript blocket med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="8c519-277">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="8c519-278">Parameter namnet, **FilterScript** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8c519-278">The parameter name, **FilterScript** , is optional.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlockSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-279">-GE</span><span class="sxs-lookup"><span data-stu-id="8c519-279">-GE</span></span>

<span data-ttu-id="8c519-280">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-280">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="8c519-281">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterOrEqualSet
Aliases: IGE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-282">-GT</span><span class="sxs-lookup"><span data-stu-id="8c519-282">-GT</span></span>

<span data-ttu-id="8c519-283">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-283">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="8c519-284">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-284">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GreaterThanSet
Aliases: IGT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-285">– In</span><span class="sxs-lookup"><span data-stu-id="8c519-285">-In</span></span>

<span data-ttu-id="8c519-286">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar något av de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="8c519-286">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="8c519-287">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="8c519-287">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="8c519-288">Om värdet för **Value** -parametern är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-288">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-289">Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning.</span><span class="sxs-lookup"><span data-stu-id="8c519-289">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="8c519-290">`Where-Object` returnerar objektet endast om värdet för **egenskaps** parametern och **värdet för värdet är samma** instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-290">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="8c519-291">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-291">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: InSet
Aliases: IIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-292">– InputObject</span><span class="sxs-lookup"><span data-stu-id="8c519-292">-InputObject</span></span>

<span data-ttu-id="8c519-293">Anger de objekt som ska filtreras.</span><span class="sxs-lookup"><span data-stu-id="8c519-293">Specifies the objects to be filtered.</span></span> <span data-ttu-id="8c519-294">Du kan också skicka objekt till `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="8c519-294">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="8c519-295">När du använder parametern **InputObject** i `Where-Object` , i stället för Skicka kommando resultat till `Where-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-295">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="8c519-296">Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="8c519-296">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="8c519-297">Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `Where-Object` för att filtrera en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `Where-Object` i pipelinen, som du ser i exemplen i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="8c519-297">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-298">-Är</span><span class="sxs-lookup"><span data-stu-id="8c519-298">-Is</span></span>

<span data-ttu-id="8c519-299">Anger att denna cmdlet hämtar objekt om egenskap svärdet är en instans av den angivna .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="8c519-299">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="8c519-300">Sätt typnamn i hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="8c519-300">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="8c519-301">Till exempel `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="8c519-301">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="8c519-302">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-302">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-303">– IsNot</span><span class="sxs-lookup"><span data-stu-id="8c519-303">-IsNot</span></span>

<span data-ttu-id="8c519-304">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en instans av den angivna .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="8c519-304">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="8c519-305">Till exempel `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="8c519-305">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="8c519-306">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-306">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsNotSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-307">-LE</span><span class="sxs-lookup"><span data-stu-id="8c519-307">-LE</span></span>

<span data-ttu-id="8c519-308">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-308">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="8c519-309">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-309">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessOrEqualSet
Aliases: ILE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-310">– Som</span><span class="sxs-lookup"><span data-stu-id="8c519-310">-Like</span></span>

<span data-ttu-id="8c519-311">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8c519-311">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="8c519-312">Exempelvis: `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c519-312">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="8c519-313">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-313">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LikeSet
Aliases: ILike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-314">-LT</span><span class="sxs-lookup"><span data-stu-id="8c519-314">-LT</span></span>

<span data-ttu-id="8c519-315">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-315">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="8c519-316">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-316">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LessThanSet
Aliases: ILT

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-317">-Matcha</span><span class="sxs-lookup"><span data-stu-id="8c519-317">-Match</span></span>

<span data-ttu-id="8c519-318">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="8c519-318">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="8c519-319">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8c519-319">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c519-320">Exempelvis: `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="8c519-320">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="8c519-321">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-321">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MatchSet
Aliases: IMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-322">-NE</span><span class="sxs-lookup"><span data-stu-id="8c519-322">-NE</span></span>

<span data-ttu-id="8c519-323">Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-323">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="8c519-324">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotEqualSet
Aliases: INE

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-325">-NotContains</span><span class="sxs-lookup"><span data-stu-id="8c519-325">-NotContains</span></span>

<span data-ttu-id="8c519-326">Anger att denna cmdlet hämtar objekt om inget av objekten i egenskap svärdet är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-326">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="8c519-327">Exempelvis: `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="8c519-327">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="8c519-328">**NotContains** refererar till en samling värden och är true om samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="8c519-328">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="8c519-329">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-329">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-330">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-330">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotContainsSet
Aliases: INotContains

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-331">-NotIn</span><span class="sxs-lookup"><span data-stu-id="8c519-331">-NotIn</span></span>

<span data-ttu-id="8c519-332">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för något av de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="8c519-332">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="8c519-333">Exempelvis: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="8c519-333">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="8c519-334">Om värdet för **värde** är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-334">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="8c519-335">Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning.</span><span class="sxs-lookup"><span data-stu-id="8c519-335">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="8c519-336">`Where-Object` returnerar objektet endast om värdet för **egenskapen** och värdet **för värdet inte är samma** instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="8c519-336">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="8c519-337">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-337">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotInSet
Aliases: INotIn

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-338">-NotLike</span><span class="sxs-lookup"><span data-stu-id="8c519-338">-NotLike</span></span>

<span data-ttu-id="8c519-339">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8c519-339">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="8c519-340">Exempelvis: `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="8c519-340">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="8c519-341">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-341">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotLikeSet
Aliases: INotLike

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-342">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="8c519-342">-NotMatch</span></span>

<span data-ttu-id="8c519-343">Anger att denna cmdlet hämtar objekt när egenskap svärdet inte matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="8c519-343">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="8c519-344">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="8c519-344">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="8c519-345">Exempelvis: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="8c519-345">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="8c519-346">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NotMatchSet
Aliases: INotMatch

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-347">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="8c519-347">-Property</span></span>

<span data-ttu-id="8c519-348">Anger namnet på en objekt egenskap.</span><span class="sxs-lookup"><span data-stu-id="8c519-348">Specifies the name of an object property.</span></span> <span data-ttu-id="8c519-349">Parameter namnet, **Property** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8c519-349">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="8c519-350">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-350">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c519-351">-Värde</span><span class="sxs-lookup"><span data-stu-id="8c519-351">-Value</span></span>

<span data-ttu-id="8c519-352">Anger ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="8c519-352">Specifies a property value.</span></span> <span data-ttu-id="8c519-353">Parameter namn, **värde** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8c519-353">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="8c519-354">Den här parametern accepterar jokertecken när de används med följande jämförelse parametrar:</span><span class="sxs-lookup"><span data-stu-id="8c519-354">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="8c519-355">**CLike**</span><span class="sxs-lookup"><span data-stu-id="8c519-355">**CLike**</span></span>
- <span data-ttu-id="8c519-356">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="8c519-356">**CNotLike**</span></span>
- <span data-ttu-id="8c519-357">**Likadan**</span><span class="sxs-lookup"><span data-stu-id="8c519-357">**Like**</span></span>
- <span data-ttu-id="8c519-358">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="8c519-358">**NotLike**</span></span>

<span data-ttu-id="8c519-359">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8c519-359">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Object
Parameter Sets: EqualSet, MatchSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="8c519-360">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c519-360">CommonParameters</span></span>

<span data-ttu-id="8c519-361">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c519-361">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c519-362">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c519-362">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c519-363">INDATA</span><span class="sxs-lookup"><span data-stu-id="8c519-363">INPUTS</span></span>

### <span data-ttu-id="8c519-364">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="8c519-364">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8c519-365">Du kan skicka vidare objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8c519-365">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="8c519-366">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8c519-366">OUTPUTS</span></span>

### <span data-ttu-id="8c519-367">Objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-367">Object</span></span>

<span data-ttu-id="8c519-368">Den här cmdleten returnerar valda objekt från den angivna insamlings objekt uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="8c519-368">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="8c519-369">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8c519-369">NOTES</span></span>

<span data-ttu-id="8c519-370">Startar i Windows PowerShell 4,0 `Where` och `ForEach` metoder lades till för användning med samlingar.</span><span class="sxs-lookup"><span data-stu-id="8c519-370">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="8c519-371">Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="8c519-371">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="8c519-372">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8c519-372">RELATED LINKS</span></span>

[<span data-ttu-id="8c519-373">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-373">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="8c519-374">-Objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-374">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="8c519-375">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-375">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="8c519-376">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-376">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="8c519-377">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-377">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="8c519-378">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8c519-378">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="8c519-379">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-379">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="8c519-380">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="8c519-380">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
