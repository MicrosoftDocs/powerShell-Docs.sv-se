---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/where-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Where-Object
ms.openlocfilehash: 0d9101c751e9ebc0b0c6fe80564bb76524de8bb6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262004"
---
# <span data-ttu-id="aafbe-103">Where-Object</span><span class="sxs-lookup"><span data-stu-id="aafbe-103">Where-Object</span></span>

## <span data-ttu-id="aafbe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aafbe-104">SYNOPSIS</span></span>
<span data-ttu-id="aafbe-105">Väljer objekt från en samling baserat på deras egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="aafbe-105">Selects objects from a collection based on their property values.</span></span>

## <span data-ttu-id="aafbe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aafbe-106">SYNTAX</span></span>

### <span data-ttu-id="aafbe-107">EqualSet (standard)</span><span class="sxs-lookup"><span data-stu-id="aafbe-107">EqualSet (Default)</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] [-EQ]
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-108">ScriptBlockSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-108">ScriptBlockSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-FilterScript] <ScriptBlock> [<CommonParameters>]
```

### <span data-ttu-id="aafbe-109">MatchSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-109">MatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Match
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-110">CaseSensitiveEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-110">CaseSensitiveEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CEQ
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-111">NotEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-111">NotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-112">CaseSensitiveNotEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-112">CaseSensitiveNotEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-113">GreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-113">GreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GT
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-114">CaseSensitiveGreaterThanSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-114">CaseSensitiveGreaterThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGT
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-115">LessThanSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-115">LessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LT
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-116">CaseSensitiveLessThanSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-116">CaseSensitiveLessThanSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLT
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-117">GreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-117">GreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -GE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-118">CaseSensitiveGreaterOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-118">CaseSensitiveGreaterOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CGE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-119">LessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-119">LessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -LE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-120">CaseSensitiveLessOrEqualSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-120">CaseSensitiveLessOrEqualSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLE
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-121">LikeSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-121">LikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Like
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-122">CaseSensitiveLikeSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-122">CaseSensitiveLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CLike
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-123">NotLikeSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-123">NotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotLike
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-124">CaseSensitiveNotLikeSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-124">CaseSensitiveNotLikeSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotLike
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-125">CaseSensitiveMatchSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-125">CaseSensitiveMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CMatch
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-126">NotMatchSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-126">NotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-127">CaseSensitiveNotMatchSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-127">CaseSensitiveNotMatchSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotMatch
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-128">ContainsSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-128">ContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Contains
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-129">CaseSensitiveContainsSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-129">CaseSensitiveContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CContains
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-130">NotContainsSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-130">NotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotContains
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-131">CaseSensitiveNotContainsSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-131">CaseSensitiveNotContainsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotContains
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-132">Luta</span><span class="sxs-lookup"><span data-stu-id="aafbe-132">InSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -In
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-133">CaseSensitiveInSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-133">CaseSensitiveInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CIn
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-134">NotInSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-134">NotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -NotIn
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-135">CaseSensitiveNotInSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-135">CaseSensitiveNotInSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -CNotIn
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-136">IsSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-136">IsSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -Is
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-137">IsNotSet</span><span class="sxs-lookup"><span data-stu-id="aafbe-137">IsNotSet</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> [[-Value] <Object>] -IsNot
 [<CommonParameters>]
```

### <span data-ttu-id="aafbe-138">Inte</span><span class="sxs-lookup"><span data-stu-id="aafbe-138">Not</span></span>

```
Where-Object [-InputObject <PSObject>] [-Property] <String> -Not [<CommonParameters>]
```

## <span data-ttu-id="aafbe-139">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aafbe-139">DESCRIPTION</span></span>

<span data-ttu-id="aafbe-140">`Where-Object`Cmdleten väljer objekt som har särskilda egenskaps värden från objekt samlingen som skickas till den.</span><span class="sxs-lookup"><span data-stu-id="aafbe-140">The `Where-Object` cmdlet selects objects that have particular property values from the collection of objects that are passed to it.</span></span> <span data-ttu-id="aafbe-141">Du kan till exempel använda `Where-Object` cmdleten för att välja filer som har skapats efter ett visst datum, händelser med ett visst ID eller datorer som använder en viss version av Windows.</span><span class="sxs-lookup"><span data-stu-id="aafbe-141">For example, you can use the `Where-Object` cmdlet to select files that were created after a certain date, events with a particular ID, or computers that use a particular version of Windows.</span></span>

<span data-ttu-id="aafbe-142">Från och med Windows PowerShell 3,0 finns det två olika sätt att skapa ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="aafbe-142">Starting in Windows PowerShell 3.0, there are two different ways to construct a `Where-Object` command.</span></span>

- <span data-ttu-id="aafbe-143">**Skript block**.</span><span class="sxs-lookup"><span data-stu-id="aafbe-143">**Script block**.</span></span> <span data-ttu-id="aafbe-144">Du kan använda ett-skript block för att ange egenskaps namn, en jämförelse operator och ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="aafbe-144">You can use a script block to specify the property name, a comparison operator, and a property value.</span></span> <span data-ttu-id="aafbe-145">`Where-Object` returnerar alla objekt som skript block instruktionen är sann för.</span><span class="sxs-lookup"><span data-stu-id="aafbe-145">`Where-Object` returns all objects for which the script block statement is true.</span></span>

  <span data-ttu-id="aafbe-146">Följande kommando hämtar till exempel processer i normal prioritets klass, det vill säga processer där värdet för egenskapen **priorityClass** är lika med normal.</span><span class="sxs-lookup"><span data-stu-id="aafbe-146">For example, the following command gets processes in the Normal priority class, that is, processes where the value of the **PriorityClass** property equals Normal.</span></span>

  `Get-Process | Where-Object {$_.PriorityClass -eq "Normal"}`

  <span data-ttu-id="aafbe-147">Alla PowerShell-jämförelse operatorer är giltiga i skript block formatet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-147">All PowerShell comparison operators are valid in the script block format.</span></span> <span data-ttu-id="aafbe-148">Mer information om jämförelse operatorer finns [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="aafbe-148">For more information about comparison operators, see [about_Comparison_Operators](./About/about_Comparison_Operators.md).</span></span>

- <span data-ttu-id="aafbe-149">**Jämförelse uttryck**.</span><span class="sxs-lookup"><span data-stu-id="aafbe-149">**Comparison statement**.</span></span> <span data-ttu-id="aafbe-150">Du kan också skriva en jämförelse instruktion, som är mycket mer likt naturligt språk.</span><span class="sxs-lookup"><span data-stu-id="aafbe-150">You can also write a comparison statement, which is much more like natural language.</span></span> <span data-ttu-id="aafbe-151">Jämförelse uttryck introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-151">Comparison statements were introduced in Windows PowerShell 3.0.</span></span>

  <span data-ttu-id="aafbe-152">Följande kommandon får till exempel också processer som har prioritets klassen normal.</span><span class="sxs-lookup"><span data-stu-id="aafbe-152">For example, the following commands also get processes that have a priority class of Normal.</span></span> <span data-ttu-id="aafbe-153">Dessa kommandon är likvärdiga och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="aafbe-153">These commands are equivalent and can be used interchangeably.</span></span>

  `Get-Process | Where-Object -Property PriorityClass -eq -Value "Normal"`

  `Get-Process | Where-Object PriorityClass -eq "Normal"`

  <span data-ttu-id="aafbe-154">Från och med Windows PowerShell 3,0 `Where-Object` lägger till jämförelse operatorer som parametrar i ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="aafbe-154">Starting in Windows PowerShell 3.0, `Where-Object` adds comparison operators as parameters in a `Where-Object` command.</span></span> <span data-ttu-id="aafbe-155">Om inget annat anges är alla operatorer Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="aafbe-155">Unless specified, all operators are case-insensitive.</span></span> <span data-ttu-id="aafbe-156">Före Windows PowerShell 3,0 kan jämförelse operatorerna i PowerShell-språket endast användas i skript block.</span><span class="sxs-lookup"><span data-stu-id="aafbe-156">Prior to Windows PowerShell 3.0, the comparison operators in the PowerShell language could be used only in script blocks.</span></span>

<span data-ttu-id="aafbe-157">När du anger en enskild **egenskap** till `Where-Object` , behandlas värdet för egenskapen som ett booleskt uttryck.</span><span class="sxs-lookup"><span data-stu-id="aafbe-157">When you provide a single **Property** to `Where-Object`, the value of the property is treated as a boolean expression.</span></span> <span data-ttu-id="aafbe-158">Om värdet för **längd** inte är noll utvärderas uttrycket till **Sant**.</span><span class="sxs-lookup"><span data-stu-id="aafbe-158">When the value of **Length** is not zero, the expression evaluates to **True**.</span></span> <span data-ttu-id="aafbe-159">Exempelvis: `('hi', '', 'there') | Where-Object Length`</span><span class="sxs-lookup"><span data-stu-id="aafbe-159">For example: `('hi', '', 'there') | Where-Object Length`</span></span>

<span data-ttu-id="aafbe-160">Det tidigare exemplet fungerar som en motsvarighet till:</span><span class="sxs-lookup"><span data-stu-id="aafbe-160">The previous example is functionally equivalent to:</span></span>

- `('hi', '', 'there') | Where-Object Length -GT 0`
- `('hi', '', 'there') | Where-Object {$_.Length -gt 0}`

## <span data-ttu-id="aafbe-161">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aafbe-161">EXAMPLES</span></span>

### <span data-ttu-id="aafbe-162">Exempel 1: Hämta stoppade tjänster</span><span class="sxs-lookup"><span data-stu-id="aafbe-162">Example 1: Get stopped services</span></span>

<span data-ttu-id="aafbe-163">De här kommandona hämtar en lista över alla tjänster som för närvarande är stoppade.</span><span class="sxs-lookup"><span data-stu-id="aafbe-163">These commands get a list of all services that are currently stopped.</span></span> <span data-ttu-id="aafbe-164">Den `$_` automatiska variabeln representerar varje objekt som skickas till `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aafbe-164">The `$_` automatic variable represents each object that is passed to the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="aafbe-165">Det första kommandot använder skript block formatet, det andra kommandot använder jämförelse uttryck formatet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-165">The first command uses the script block format, the second command uses the comparison statement format.</span></span> <span data-ttu-id="aafbe-166">Kommandona är likvärdiga och kan användas utbytbara.</span><span class="sxs-lookup"><span data-stu-id="aafbe-166">The commands are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Service | Where-Object {$_.Status -eq "Stopped"}
Get-Service | where Status -eq "Stopped"
```

### <span data-ttu-id="aafbe-167">Exempel 2: Hämta processer baserat på arbets minnet</span><span class="sxs-lookup"><span data-stu-id="aafbe-167">Example 2: Get processes based on working set</span></span>

<span data-ttu-id="aafbe-168">Kommandona visar en lista över processer som har en arbets mängd som är större än 250 megabyte (KB).</span><span class="sxs-lookup"><span data-stu-id="aafbe-168">These commands list processes that have a working set greater than 250 megabytes (KB).</span></span> <span data-ttu-id="aafbe-169">Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="aafbe-169">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.WorkingSet -GT 250MB}
Get-Process | Where-Object WorkingSet -GT (250MB)
```

### <span data-ttu-id="aafbe-170">Exempel 3: Hämta processer baserat på process namn</span><span class="sxs-lookup"><span data-stu-id="aafbe-170">Example 3: Get processes based on process name</span></span>

<span data-ttu-id="aafbe-171">De här kommandona hämtar de processer som har ett värde för egenskapen **processname** som börjar med bokstaven `p` .</span><span class="sxs-lookup"><span data-stu-id="aafbe-171">These commands get the processes that have a **ProcessName** property value that begins with the letter `p`.</span></span> <span data-ttu-id="aafbe-172">Med operatorn **match** kan du använda reguljära uttryck matchningar.</span><span class="sxs-lookup"><span data-stu-id="aafbe-172">The **Match** operator lets you use regular expression matches.</span></span>

<span data-ttu-id="aafbe-173">Syntaxen för script block och-satsen är likvärdig och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="aafbe-173">The scriptblock and statement syntax are equivalent and can be used interchangeably.</span></span>

```powershell
Get-Process | Where-Object {$_.ProcessName -Match "^p.*"}
Get-Process | Where-Object ProcessName -Match "^p.*"
```

### <span data-ttu-id="aafbe-174">Exempel 4: Använd formatet jämförelse uttryck</span><span class="sxs-lookup"><span data-stu-id="aafbe-174">Example 4: Use the comparison statement format</span></span>

<span data-ttu-id="aafbe-175">Det här exemplet visar hur du använder det nya jämförelse instruktions formatet för `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aafbe-175">This example shows how to use the new comparison statement format of the `Where-Object` cmdlet.</span></span>

<span data-ttu-id="aafbe-176">Det första kommandot använder jämförelse instruktions formatet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-176">The first command uses the comparison statement format.</span></span>
<span data-ttu-id="aafbe-177">I det här kommandot används inga alias och alla parametrar inkluderar parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-177">In this command, no aliases are used and all parameters include the parameter name.</span></span>

<span data-ttu-id="aafbe-178">Det andra kommandot är den mer naturliga användningen av jämförelse kommando formatet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-178">The second command is the more natural use of the comparison command format.</span></span> <span data-ttu-id="aafbe-179">`where`Aliaset ersätts med cmdlet- `Where-Object` namnet och alla valfria parameter namn utelämnas.</span><span class="sxs-lookup"><span data-stu-id="aafbe-179">The `where` alias is substituted for the `Where-Object` cmdlet name and all optional parameter names are omitted.</span></span>

```powershell
Get-Process | Where-Object -Property Handles -GE -Value 1000
Get-Process | where Handles -GE 1000
```

### <span data-ttu-id="aafbe-180">Exempel 5: Hämta kommandon baserat på egenskaper</span><span class="sxs-lookup"><span data-stu-id="aafbe-180">Example 5: Get commands based on properties</span></span>

<span data-ttu-id="aafbe-181">Det här exemplet visar hur du skriver kommandon som returnerar objekt som är true eller false eller som har ett värde för en angiven egenskap.</span><span class="sxs-lookup"><span data-stu-id="aafbe-181">This example shows how to write commands that return items that are true or false or have any value for a specified property.</span></span> <span data-ttu-id="aafbe-182">I varje exempel visas formatet skript block och jämförelse uttryck för kommandot.</span><span class="sxs-lookup"><span data-stu-id="aafbe-182">Each example shows both the script block and comparison statement formats for the command.</span></span>

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

### <span data-ttu-id="aafbe-183">Exempel 6: Använd flera villkor</span><span class="sxs-lookup"><span data-stu-id="aafbe-183">Example 6: Use multiple conditions</span></span>

```powershell
Get-Module -ListAvailable | where {($_.Name -notlike "Microsoft*" -and $_.Name -notlike "PS*") -and $_.HelpInfoUri}
```

<span data-ttu-id="aafbe-184">Det här exemplet visar hur du skapar ett `Where-Object` kommando med flera villkor.</span><span class="sxs-lookup"><span data-stu-id="aafbe-184">This example shows how to create a `Where-Object` command with multiple conditions.</span></span>

<span data-ttu-id="aafbe-185">Det här kommandot hämtar moduler som inte är kärnan och som har stöd för den uppdaterbara hjälp funktionen.</span><span class="sxs-lookup"><span data-stu-id="aafbe-185">This command gets non-core modules that support the Updatable Help feature.</span></span> <span data-ttu-id="aafbe-186">Kommandot använder **ListAvailable** -parametern för `Get-Module` cmdleten för att hämta alla moduler på datorn.</span><span class="sxs-lookup"><span data-stu-id="aafbe-186">The command uses the **ListAvailable** parameter of the `Get-Module` cmdlet to get all modules on the computer.</span></span> <span data-ttu-id="aafbe-187">En pipeline-operator ( `|` ) skickar modulerna till `Where-Object` cmdleten, som hämtar moduler vars namn inte börjar med Microsoft eller PS, och har ett värde för egenskapen **HelpInfoURI** , som talar om för PowerShell var du hittar uppdaterade hjälpfiler för modulen.</span><span class="sxs-lookup"><span data-stu-id="aafbe-187">A pipeline operator (`|`) sends the modules to the `Where-Object` cmdlet, which gets modules whose names do not begin with Microsoft or PS, and have a value for the **HelpInfoURI** property, which tells PowerShell where to find updated help files for the module.</span></span> <span data-ttu-id="aafbe-188">Jämförelse instruktionerna är anslutna med operatorn **och** den logiska operatorn.</span><span class="sxs-lookup"><span data-stu-id="aafbe-188">The comparison statements are connected by the **And** logical operator.</span></span>

<span data-ttu-id="aafbe-189">I exemplet används skript blockets kommando format.</span><span class="sxs-lookup"><span data-stu-id="aafbe-189">The example uses the script block command format.</span></span> <span data-ttu-id="aafbe-190">Logiska operatorer, till **And** exempel och **och, är** bara giltiga i skript block.</span><span class="sxs-lookup"><span data-stu-id="aafbe-190">Logical operators, such as **And** and **Or** , are valid only in script blocks.</span></span> <span data-ttu-id="aafbe-191">Du kan inte använda dem i jämförelse instruktions formatet för ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="aafbe-191">You cannot use them in the comparison statement format of a `Where-Object` command.</span></span>

- <span data-ttu-id="aafbe-192">Mer information om logiska PowerShell-operatörer finns [about_Logical_Operators](./About/about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="aafbe-192">For more information about PowerShell logical operators, see [about_Logical_Operators](./About/about_logical_operators.md).</span></span>
- <span data-ttu-id="aafbe-193">Mer information om den uppdaterbara hjälp funktionen finns [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="aafbe-193">For more information about the Updatable Help feature, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

## <span data-ttu-id="aafbe-194">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aafbe-194">PARAMETERS</span></span>

### <span data-ttu-id="aafbe-195">-CContains</span><span class="sxs-lookup"><span data-stu-id="aafbe-195">-CContains</span></span>

<span data-ttu-id="aafbe-196">Anger att denna cmdlet hämtar objekt från en samling om objektets egenskaps värde är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-196">Indicates that this cmdlet gets objects from a collection if the property value of the object is an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-197">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-197">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-198">Exempelvis: `Get-Process | where ProcessName -CContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-198">For example: `Get-Process | where ProcessName -CContains "svchost"`</span></span>

<span data-ttu-id="aafbe-199">**CContains** refererar till en samling värden och är true om samlingen innehåller ett objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-199">**CContains** refers to a collection of values and is true if the collection contains an item that is an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-200">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-200">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-201">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-201">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-202">-CEQ</span><span class="sxs-lookup"><span data-stu-id="aafbe-202">-CEQ</span></span>

<span data-ttu-id="aafbe-203">Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-203">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>
<span data-ttu-id="aafbe-204">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-204">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-205">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-206">-CGE</span><span class="sxs-lookup"><span data-stu-id="aafbe-206">-CGE</span></span>

<span data-ttu-id="aafbe-207">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-207">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span> <span data-ttu-id="aafbe-208">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-208">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-209">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-209">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-210">-CGT</span><span class="sxs-lookup"><span data-stu-id="aafbe-210">-CGT</span></span>

<span data-ttu-id="aafbe-211">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-211">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>
<span data-ttu-id="aafbe-212">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-212">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-213">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-213">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-214">-CIn</span><span class="sxs-lookup"><span data-stu-id="aafbe-214">-CIn</span></span>

<span data-ttu-id="aafbe-215">Anger att denna cmdlet hämtar objekt om egenskap svärdet innehåller det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-215">Indicates that this cmdlet gets objects if the property value includes the specified value.</span></span> <span data-ttu-id="aafbe-216">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-216">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-217">Exempelvis: `Get-Process | where -Value "svchost" -CIn ProcessName`</span><span class="sxs-lookup"><span data-stu-id="aafbe-217">For example: `Get-Process | where -Value "svchost" -CIn ProcessName`</span></span>

<span data-ttu-id="aafbe-218">**CIn** liknar **CContains** , förutom att egenskaps-och värde positionerna är omvända.</span><span class="sxs-lookup"><span data-stu-id="aafbe-218">**CIn** resembles **CContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="aafbe-219">Följande uttryck är till exempel båda sanna.</span><span class="sxs-lookup"><span data-stu-id="aafbe-219">For example, the following statements are both true.</span></span>

`"abc", "def" -CContains "abc"`

`"abc" -CIn "abc", "def"`

<span data-ttu-id="aafbe-220">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-221">-CLE</span><span class="sxs-lookup"><span data-stu-id="aafbe-221">-CLE</span></span>

<span data-ttu-id="aafbe-222">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-222">Indicates that this cmdlet gets objects if the property value is less-than or equal to the specified value.</span></span> <span data-ttu-id="aafbe-223">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-223">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-224">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-225">-CLike</span><span class="sxs-lookup"><span data-stu-id="aafbe-225">-CLike</span></span>

<span data-ttu-id="aafbe-226">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aafbe-226">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span> <span data-ttu-id="aafbe-227">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-227">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-228">Exempelvis: `Get-Process | where ProcessName -CLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-228">For example: `Get-Process | where ProcessName -CLike "*host"`</span></span>

<span data-ttu-id="aafbe-229">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-230">-CLT</span><span class="sxs-lookup"><span data-stu-id="aafbe-230">-CLT</span></span>

<span data-ttu-id="aafbe-231">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-231">Indicates that this cmdlet gets objects if the property value is less-than the specified value.</span></span> <span data-ttu-id="aafbe-232">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-232">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-233">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-233">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-234">-CMatch</span><span class="sxs-lookup"><span data-stu-id="aafbe-234">-CMatch</span></span>

<span data-ttu-id="aafbe-235">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="aafbe-235">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="aafbe-236">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-236">This operation is case-sensitive.</span></span> <span data-ttu-id="aafbe-237">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="aafbe-237">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="aafbe-238">Exempelvis: `Get-Process | where ProcessName -CMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-238">For example: `Get-Process | where ProcessName -CMatch "Shell"`</span></span>

<span data-ttu-id="aafbe-239">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-239">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-240">-CNE</span><span class="sxs-lookup"><span data-stu-id="aafbe-240">-CNE</span></span>

<span data-ttu-id="aafbe-241">Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-241">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>
<span data-ttu-id="aafbe-242">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-242">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-243">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-244">-CNotContains</span><span class="sxs-lookup"><span data-stu-id="aafbe-244">-CNotContains</span></span>

<span data-ttu-id="aafbe-245">Anger att denna cmdlet hämtar objekt om objektets egenskaps värde inte är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-245">Indicates that this cmdlet gets objects if the property value of the object is not an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-246">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-246">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-247">Exempelvis: `Get-Process | where ProcessName -CNotContains "svchost"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-247">For example: `Get-Process | where ProcessName -CNotContains "svchost"`</span></span>

<span data-ttu-id="aafbe-248">**NotContains** och **CNotContains** refererar till en samling värden och är sanna när samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-248">**NotContains** and **CNotContains** refer to a collection of values and are true when the collection does not contains any items that are an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-249">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-249">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-250">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-250">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-251">-CNotIn</span><span class="sxs-lookup"><span data-stu-id="aafbe-251">-CNotIn</span></span>

<span data-ttu-id="aafbe-252">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-252">Indicates that this cmdlet gets objects if the property value is not an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-253">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-253">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-254">Exempelvis: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="aafbe-254">For example: `Get-Process | where -Value "svchost" -CNotIn -Property ProcessName`</span></span>

<span data-ttu-id="aafbe-255">**NotIn** -och **CNotIn** -operatörer liknar **NotContains** och **CNotContains** , förutom att egenskaps-och värde positionerna är omvända.</span><span class="sxs-lookup"><span data-stu-id="aafbe-255">**NotIn** and **CNotIn** operators resemble **NotContains** and **CNotContains** , except that the property and value positions are reversed.</span></span> <span data-ttu-id="aafbe-256">Följande påståenden är till exempel sanna.</span><span class="sxs-lookup"><span data-stu-id="aafbe-256">For example, the following statements are true.</span></span>

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

### <span data-ttu-id="aafbe-257">-CNotLike</span><span class="sxs-lookup"><span data-stu-id="aafbe-257">-CNotLike</span></span>

<span data-ttu-id="aafbe-258">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aafbe-258">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span> <span data-ttu-id="aafbe-259">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-259">This operation is case-sensitive.</span></span>

<span data-ttu-id="aafbe-260">Exempelvis: `Get-Process | where ProcessName -CNotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-260">For example: `Get-Process | where ProcessName -CNotLike "*host"`</span></span>

<span data-ttu-id="aafbe-261">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-261">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-262">-CNotMatch</span><span class="sxs-lookup"><span data-stu-id="aafbe-262">-CNotMatch</span></span>

<span data-ttu-id="aafbe-263">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="aafbe-263">Indicates that this cmdlet gets objects if the property value does not match the specified regular expression.</span></span> <span data-ttu-id="aafbe-264">Den här åtgärden är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="aafbe-264">This operation is case-sensitive.</span></span> <span data-ttu-id="aafbe-265">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="aafbe-265">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="aafbe-266">Exempelvis: `Get-Process | where ProcessName -CNotMatch "Shell"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-266">For example: `Get-Process | where ProcessName -CNotMatch "Shell"`</span></span>

<span data-ttu-id="aafbe-267">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-268">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="aafbe-268">-Contains</span></span>

<span data-ttu-id="aafbe-269">Anger att denna cmdlet hämtar objekt om något objekt i objektets egenskaps värde är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-269">Indicates that this cmdlet gets objects if any item in the property value of the object is an exact match for the specified value.</span></span>

<span data-ttu-id="aafbe-270">Exempelvis: `Get-Process | where ProcessName -Contains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-270">For example: `Get-Process | where ProcessName -Contains "Svchost"`</span></span>

<span data-ttu-id="aafbe-271">Om egenskap svärdet innehåller ett enda objekt konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-271">If the property value contains a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-272">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-273">-EQ</span><span class="sxs-lookup"><span data-stu-id="aafbe-273">-EQ</span></span>

<span data-ttu-id="aafbe-274">Anger att denna cmdlet hämtar objekt om egenskap svärdet är samma som det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-274">Indicates that this cmdlet gets objects if the property value is the same as the specified value.</span></span>

<span data-ttu-id="aafbe-275">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-275">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-276">-FilterScript</span><span class="sxs-lookup"><span data-stu-id="aafbe-276">-FilterScript</span></span>

<span data-ttu-id="aafbe-277">Anger det skript block som används för att filtrera objekten.</span><span class="sxs-lookup"><span data-stu-id="aafbe-277">Specifies the script block that is used to filter the objects.</span></span> <span data-ttu-id="aafbe-278">Omge skript blocket med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="aafbe-278">Enclose the script block in braces (`{}`).</span></span>

<span data-ttu-id="aafbe-279">Parameter namnet, **FilterScript** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-279">The parameter name, **FilterScript** , is optional.</span></span>

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

### <span data-ttu-id="aafbe-280">-GE</span><span class="sxs-lookup"><span data-stu-id="aafbe-280">-GE</span></span>

<span data-ttu-id="aafbe-281">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-281">Indicates that this cmdlet gets objects if the property value is greater than or equal to the specified value.</span></span>

<span data-ttu-id="aafbe-282">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-282">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-283">-GT</span><span class="sxs-lookup"><span data-stu-id="aafbe-283">-GT</span></span>

<span data-ttu-id="aafbe-284">Anger att denna cmdlet hämtar objekt om egenskapens värde är större än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-284">Indicates that this cmdlet gets objects if the property value is greater than the specified value.</span></span>

<span data-ttu-id="aafbe-285">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-285">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-286">– In</span><span class="sxs-lookup"><span data-stu-id="aafbe-286">-In</span></span>

<span data-ttu-id="aafbe-287">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar något av de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="aafbe-287">Indicates that this cmdlet gets objects if the property value matches any of the specified values.</span></span>
<span data-ttu-id="aafbe-288">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="aafbe-288">For example:</span></span>

`Get-Process | where -Property ProcessName -in -Value "Svchost", "TaskHost", "WsmProvHost"`

<span data-ttu-id="aafbe-289">Om värdet för **Value** -parametern är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-289">If the value of the **Value** parameter is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-290">Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning.</span><span class="sxs-lookup"><span data-stu-id="aafbe-290">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="aafbe-291">`Where-Object` returnerar objektet endast om värdet för **egenskaps** parametern och **värdet för värdet är samma** instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-291">`Where-Object` returns the object only if the value of the **Property** parameter and any value of **Value** are the same instance of an object.</span></span>

<span data-ttu-id="aafbe-292">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-292">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-293">– InputObject</span><span class="sxs-lookup"><span data-stu-id="aafbe-293">-InputObject</span></span>

<span data-ttu-id="aafbe-294">Anger de objekt som ska filtreras.</span><span class="sxs-lookup"><span data-stu-id="aafbe-294">Specifies the objects to be filtered.</span></span> <span data-ttu-id="aafbe-295">Du kan också skicka objekt till `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="aafbe-295">You can also pipe the objects to `Where-Object`.</span></span>

<span data-ttu-id="aafbe-296">När du använder parametern **InputObject** i `Where-Object` , i stället för Skicka kommando resultat till `Where-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-296">When you use the **InputObject** parameter with `Where-Object`, instead of piping command results to `Where-Object`, the **InputObject** value is treated as a single object.</span></span> <span data-ttu-id="aafbe-297">Detta gäller även om värdet är en samling som är resultatet av ett kommando, till exempel `-InputObject (Get-Process)` .</span><span class="sxs-lookup"><span data-stu-id="aafbe-297">This is true even if the value is a collection that is the result of a command, such as `-InputObject (Get-Process)`.</span></span> <span data-ttu-id="aafbe-298">Eftersom **InputObject** inte kan returnera enskilda egenskaper från en matris eller samling objekt, rekommenderar vi att om du använder `Where-Object` för att filtrera en samling objekt för de objekt som har specifika värden i definierade egenskaper, använder du `Where-Object` i pipelinen, som du ser i exemplen i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-298">Because **InputObject** cannot return individual properties from an array or collection of objects, we recommend that, if you use `Where-Object` to filter a collection of objects for those objects that have specific values in defined properties, you use `Where-Object` in the pipeline, as shown in the examples in this topic.</span></span>

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

### <span data-ttu-id="aafbe-299">-Är</span><span class="sxs-lookup"><span data-stu-id="aafbe-299">-Is</span></span>

<span data-ttu-id="aafbe-300">Anger att denna cmdlet hämtar objekt om egenskap svärdet är en instans av den angivna .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="aafbe-300">Indicates that this cmdlet gets objects if the property value is an instance of the specified .NET type.</span></span> <span data-ttu-id="aafbe-301">Sätt typnamn i hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="aafbe-301">Enclose the type name in square brackets.</span></span>

<span data-ttu-id="aafbe-302">Till exempel `Get-Process | where StartTime -Is [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="aafbe-302">For example, `Get-Process | where StartTime -Is [DateTime]`</span></span>

<span data-ttu-id="aafbe-303">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-303">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-304">– IsNot</span><span class="sxs-lookup"><span data-stu-id="aafbe-304">-IsNot</span></span>

<span data-ttu-id="aafbe-305">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en instans av den angivna .NET-typen.</span><span class="sxs-lookup"><span data-stu-id="aafbe-305">Indicates that this cmdlet gets objects if the property value is not an instance of the specified .NET type.</span></span>

<span data-ttu-id="aafbe-306">Till exempel `Get-Process | where StartTime -IsNot [DateTime]`</span><span class="sxs-lookup"><span data-stu-id="aafbe-306">For example, `Get-Process | where StartTime -IsNot [DateTime]`</span></span>

<span data-ttu-id="aafbe-307">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-307">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-308">-LE</span><span class="sxs-lookup"><span data-stu-id="aafbe-308">-LE</span></span>

<span data-ttu-id="aafbe-309">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-309">Indicates that this cmdlet gets objects if the property value is less than or equal to the specified value.</span></span>

<span data-ttu-id="aafbe-310">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-310">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-311">– Som</span><span class="sxs-lookup"><span data-stu-id="aafbe-311">-Like</span></span>

<span data-ttu-id="aafbe-312">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aafbe-312">Indicates that this cmdlet gets objects if the property value matches a value that includes wildcard characters.</span></span>

<span data-ttu-id="aafbe-313">Exempelvis: `Get-Process | where ProcessName -Like "*host"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-313">For example: `Get-Process | where ProcessName -Like "*host"`</span></span>

<span data-ttu-id="aafbe-314">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-314">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-315">-LT</span><span class="sxs-lookup"><span data-stu-id="aafbe-315">-LT</span></span>

<span data-ttu-id="aafbe-316">Anger att denna cmdlet hämtar objekt om egenskapens värde är mindre än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-316">Indicates that this cmdlet gets objects if the property value is less than the specified value.</span></span>

<span data-ttu-id="aafbe-317">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-317">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-318">-Matcha</span><span class="sxs-lookup"><span data-stu-id="aafbe-318">-Match</span></span>

<span data-ttu-id="aafbe-319">Anger att denna cmdlet hämtar objekt om egenskap svärdet matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="aafbe-319">Indicates that this cmdlet gets objects if the property value matches the specified regular expression.</span></span> <span data-ttu-id="aafbe-320">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="aafbe-320">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="aafbe-321">Exempelvis: `Get-Process | where ProcessName -Match "shell"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-321">For example: `Get-Process | where ProcessName -Match "shell"`</span></span>

<span data-ttu-id="aafbe-322">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-322">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-323">-NE</span><span class="sxs-lookup"><span data-stu-id="aafbe-323">-NE</span></span>

<span data-ttu-id="aafbe-324">Anger att denna cmdlet hämtar objekt om egenskap svärdet skiljer sig från det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-324">Indicates that this cmdlet gets objects if the property value is different than the specified value.</span></span>

<span data-ttu-id="aafbe-325">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-325">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-326">– Inte</span><span class="sxs-lookup"><span data-stu-id="aafbe-326">-Not</span></span>

<span data-ttu-id="aafbe-327">Anger att denna cmdlet hämtar objekt om egenskapen inte finns eller har värdet null eller false.</span><span class="sxs-lookup"><span data-stu-id="aafbe-327">Indicates that this cmdlet gets objects if the property does not exist or has a value of null or false.</span></span>

<span data-ttu-id="aafbe-328">Exempelvis: `Get-Service | where -Not "DependentServices"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-328">For example: `Get-Service | where -Not "DependentServices"`</span></span>

<span data-ttu-id="aafbe-329">Den här parametern introducerades i Windows PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="aafbe-329">This parameter was introduced in Windows PowerShell 6.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Not
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aafbe-330">-NotContains</span><span class="sxs-lookup"><span data-stu-id="aafbe-330">-NotContains</span></span>

<span data-ttu-id="aafbe-331">Anger att denna cmdlet hämtar objekt om inget av objekten i egenskap svärdet är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-331">Indicates that this cmdlet gets objects if none of the items in the property value is an exact match for the specified value.</span></span>

<span data-ttu-id="aafbe-332">Exempelvis: `Get-Process | where ProcessName -NotContains "Svchost"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-332">For example: `Get-Process | where ProcessName -NotContains "Svchost"`</span></span>

<span data-ttu-id="aafbe-333">**NotContains** refererar till en samling värden och är true om samlingen inte innehåller några objekt som är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-333">**NotContains** refers to a collection of values and is true if the collection does not contain any items that are an exact match for the specified value.</span></span> <span data-ttu-id="aafbe-334">Om indatatypen är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-334">If the input is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-335">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-335">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-336">-NotIn</span><span class="sxs-lookup"><span data-stu-id="aafbe-336">-NotIn</span></span>

<span data-ttu-id="aafbe-337">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte är en exakt matchning för något av de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="aafbe-337">Indicates that this cmdlet gets objects if the property value is not an exact match for any of the specified values.</span></span>

<span data-ttu-id="aafbe-338">Exempelvis: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span><span class="sxs-lookup"><span data-stu-id="aafbe-338">For example: `Get-Process | where -Value "svchost" -NotIn -Property ProcessName`</span></span>

<span data-ttu-id="aafbe-339">Om värdet för **värde** är ett enda objekt, konverterar PowerShell det till en samling med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-339">If the value of **Value** is a single object, PowerShell converts it to a collection of one object.</span></span>

<span data-ttu-id="aafbe-340">Om egenskap svärdet för ett objekt är en matris använder PowerShell referens likhet för att fastställa en matchning.</span><span class="sxs-lookup"><span data-stu-id="aafbe-340">If the property value of an object is an array, PowerShell uses reference equality to determine a match.</span></span> <span data-ttu-id="aafbe-341">`Where-Object` returnerar objektet endast om värdet för **egenskapen** och värdet **för värdet inte är samma** instans av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-341">`Where-Object` returns the object only if the value of **Property** and any value of **Value** are not the same instance of an object.</span></span>

<span data-ttu-id="aafbe-342">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-342">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-343">-NotLike</span><span class="sxs-lookup"><span data-stu-id="aafbe-343">-NotLike</span></span>

<span data-ttu-id="aafbe-344">Anger att denna cmdlet hämtar objekt om egenskap svärdet inte matchar ett värde som innehåller jokertecken.</span><span class="sxs-lookup"><span data-stu-id="aafbe-344">Indicates that this cmdlet gets objects if the property value does not match a value that includes wildcard characters.</span></span>

<span data-ttu-id="aafbe-345">Exempelvis: `Get-Process | where ProcessName -NotLike "*host"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-345">For example: `Get-Process | where ProcessName -NotLike "*host"`</span></span>

<span data-ttu-id="aafbe-346">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-346">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-347">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="aafbe-347">-NotMatch</span></span>

<span data-ttu-id="aafbe-348">Anger att denna cmdlet hämtar objekt när egenskap svärdet inte matchar det angivna reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="aafbe-348">Indicates that this cmdlet gets objects when the property value does not match the specified regular expression.</span></span> <span data-ttu-id="aafbe-349">När indatatypen är skalär, sparas det matchande värdet i den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="aafbe-349">When the input is scalar, the matched value is saved in `$Matches` automatic variable.</span></span>

<span data-ttu-id="aafbe-350">Exempelvis: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span><span class="sxs-lookup"><span data-stu-id="aafbe-350">For example: `Get-Process | where ProcessName -NotMatch "PowerShell"`</span></span>

<span data-ttu-id="aafbe-351">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-351">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="aafbe-352">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="aafbe-352">-Property</span></span>

<span data-ttu-id="aafbe-353">Anger namnet på en objekt egenskap.</span><span class="sxs-lookup"><span data-stu-id="aafbe-353">Specifies the name of an object property.</span></span> <span data-ttu-id="aafbe-354">Parameter namnet, **Property** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-354">The parameter name, **Property** , is optional.</span></span>

<span data-ttu-id="aafbe-355">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-355">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: EqualSet, CaseSensitiveNotLikeSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, CaseSensitiveGreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet, Not
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aafbe-356">-Värde</span><span class="sxs-lookup"><span data-stu-id="aafbe-356">-Value</span></span>

<span data-ttu-id="aafbe-357">Anger ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="aafbe-357">Specifies a property value.</span></span> <span data-ttu-id="aafbe-358">Parameter namn, **värde** , är valfritt.</span><span class="sxs-lookup"><span data-stu-id="aafbe-358">The parameter name, **Value** , is optional.</span></span> <span data-ttu-id="aafbe-359">Den här parametern accepterar jokertecken när de används med följande jämförelse parametrar:</span><span class="sxs-lookup"><span data-stu-id="aafbe-359">This parameter accepts wildcard characters when used with the following comparison parameters:</span></span>

- <span data-ttu-id="aafbe-360">**CLike**</span><span class="sxs-lookup"><span data-stu-id="aafbe-360">**CLike**</span></span>
- <span data-ttu-id="aafbe-361">**CNotLike**</span><span class="sxs-lookup"><span data-stu-id="aafbe-361">**CNotLike**</span></span>
- <span data-ttu-id="aafbe-362">**Likadan**</span><span class="sxs-lookup"><span data-stu-id="aafbe-362">**Like**</span></span>
- <span data-ttu-id="aafbe-363">**NotLike**</span><span class="sxs-lookup"><span data-stu-id="aafbe-363">**NotLike**</span></span>

<span data-ttu-id="aafbe-364">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="aafbe-364">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Object
Parameter Sets: EqualSet, CaseSensitiveGreaterOrEqualSet, CaseSensitiveEqualSet, NotEqualSet, CaseSensitiveNotEqualSet, GreaterThanSet, CaseSensitiveGreaterThanSet, LessThanSet, CaseSensitiveLessThanSet, GreaterOrEqualSet, LessOrEqualSet, CaseSensitiveLessOrEqualSet, LikeSet, CaseSensitiveLikeSet, NotLikeSet, CaseSensitiveNotLikeSet, MatchSet, CaseSensitiveMatchSet, NotMatchSet, CaseSensitiveNotMatchSet, ContainsSet, CaseSensitiveContainsSet, NotContainsSet, CaseSensitiveNotContainsSet, InSet, CaseSensitiveInSet, NotInSet, CaseSensitiveNotInSet, IsSet, IsNotSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aafbe-365">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aafbe-365">CommonParameters</span></span>

<span data-ttu-id="aafbe-366">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aafbe-366">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aafbe-367">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aafbe-367">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aafbe-368">INDATA</span><span class="sxs-lookup"><span data-stu-id="aafbe-368">INPUTS</span></span>

### <span data-ttu-id="aafbe-369">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="aafbe-369">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="aafbe-370">Du kan skicka vidare objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aafbe-370">You can pipe the objects to this cmdlet.</span></span>

## <span data-ttu-id="aafbe-371">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aafbe-371">OUTPUTS</span></span>

### <span data-ttu-id="aafbe-372">Objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-372">Object</span></span>

<span data-ttu-id="aafbe-373">Den här cmdleten returnerar valda objekt från den angivna insamlings objekt uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="aafbe-373">This cmdlet returns selected items from the input object set.</span></span>

## <span data-ttu-id="aafbe-374">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aafbe-374">NOTES</span></span>

<span data-ttu-id="aafbe-375">Startar i Windows PowerShell 4,0 `Where` och `ForEach` metoder lades till för användning med samlingar.</span><span class="sxs-lookup"><span data-stu-id="aafbe-375">Starting in Windows PowerShell 4.0, `Where` and `ForEach` methods were added for use with collections.</span></span>

<span data-ttu-id="aafbe-376">Du kan läsa mer om de här nya metoderna här [about_arrays](./About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="aafbe-376">You can read more about these new methods here [about_arrays](./About/about_Arrays.md)</span></span>

## <span data-ttu-id="aafbe-377">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aafbe-377">RELATED LINKS</span></span>

[<span data-ttu-id="aafbe-378">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-378">Compare-Object</span></span>](../Microsoft.PowerShell.Utility/Compare-Object.md)

[<span data-ttu-id="aafbe-379">-Objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-379">ForEach-Object</span></span>](ForEach-Object.md)

[<span data-ttu-id="aafbe-380">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-380">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="aafbe-381">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-381">Measure-Object</span></span>](../Microsoft.PowerShell.Utility/Measure-Object.md)

[<span data-ttu-id="aafbe-382">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-382">New-Object</span></span>](../Microsoft.PowerShell.Utility/New-Object.md)

[<span data-ttu-id="aafbe-383">Select-Object</span><span class="sxs-lookup"><span data-stu-id="aafbe-383">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="aafbe-384">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-384">Sort-Object</span></span>](../Microsoft.PowerShell.Utility/Sort-Object.md)

[<span data-ttu-id="aafbe-385">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="aafbe-385">Tee-Object</span></span>](../Microsoft.PowerShell.Utility/Tee-Object.md)
