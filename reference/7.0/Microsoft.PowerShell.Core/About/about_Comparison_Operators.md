---
description: Beskriver de operatorer som jämför värden i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: d6096de14d0bb8c7ba86c0585806b86cf3bb921a
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272930"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="e606b-104">Om jämförelse operatorer</span><span class="sxs-lookup"><span data-stu-id="e606b-104">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="e606b-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e606b-105">Short description</span></span>
<span data-ttu-id="e606b-106">Beskriver de operatorer som jämför värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e606b-106">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e606b-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e606b-107">Long description</span></span>

<span data-ttu-id="e606b-108">Med jämförelse operatorer kan du ange villkor för jämförelse av värden och hitta värden som matchar angivna mönster.</span><span class="sxs-lookup"><span data-stu-id="e606b-108">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="e606b-109">Om du vill använda en jämförelse operator anger du de värden som du vill jämföra tillsammans med en operator som särskiljer dessa värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-109">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="e606b-110">PowerShell innehåller följande jämförelse operatorer:</span><span class="sxs-lookup"><span data-stu-id="e606b-110">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="e606b-111">Typ</span><span class="sxs-lookup"><span data-stu-id="e606b-111">Type</span></span>        | <span data-ttu-id="e606b-112">Operatorer</span><span class="sxs-lookup"><span data-stu-id="e606b-112">Operators</span></span>    | <span data-ttu-id="e606b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e606b-113">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="e606b-114">Likhet</span><span class="sxs-lookup"><span data-stu-id="e606b-114">Equality</span></span>    | <span data-ttu-id="e606b-115">-EQ</span><span class="sxs-lookup"><span data-stu-id="e606b-115">-eq</span></span>          | <span data-ttu-id="e606b-116">är lika med</span><span class="sxs-lookup"><span data-stu-id="e606b-116">equals</span></span>                                      |
|             | <span data-ttu-id="e606b-117">-Ne</span><span class="sxs-lookup"><span data-stu-id="e606b-117">-ne</span></span>          | <span data-ttu-id="e606b-118">inte lika med</span><span class="sxs-lookup"><span data-stu-id="e606b-118">not equals</span></span>                                  |
|             | <span data-ttu-id="e606b-119">-gt</span><span class="sxs-lookup"><span data-stu-id="e606b-119">-gt</span></span>          | <span data-ttu-id="e606b-120">större än</span><span class="sxs-lookup"><span data-stu-id="e606b-120">greater than</span></span>                                |
|             | <span data-ttu-id="e606b-121">-ge</span><span class="sxs-lookup"><span data-stu-id="e606b-121">-ge</span></span>          | <span data-ttu-id="e606b-122">större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="e606b-122">greater than or equal</span></span>                       |
|             | <span data-ttu-id="e606b-123">-lt</span><span class="sxs-lookup"><span data-stu-id="e606b-123">-lt</span></span>          | <span data-ttu-id="e606b-124">mindre än</span><span class="sxs-lookup"><span data-stu-id="e606b-124">less than</span></span>                                   |
|             | <span data-ttu-id="e606b-125">-Le</span><span class="sxs-lookup"><span data-stu-id="e606b-125">-le</span></span>          | <span data-ttu-id="e606b-126">mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="e606b-126">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="e606b-127">Matching</span><span class="sxs-lookup"><span data-stu-id="e606b-127">Matching</span></span>    | <span data-ttu-id="e606b-128">– som</span><span class="sxs-lookup"><span data-stu-id="e606b-128">-like</span></span>        | <span data-ttu-id="e606b-129">Returnerar true när strängen matchar jokertecken</span><span class="sxs-lookup"><span data-stu-id="e606b-129">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="e606b-130">ofta</span><span class="sxs-lookup"><span data-stu-id="e606b-130">pattern</span></span>                                     |
|             | <span data-ttu-id="e606b-131">-notlike</span><span class="sxs-lookup"><span data-stu-id="e606b-131">-notlike</span></span>     | <span data-ttu-id="e606b-132">Returnerar sant när strängen inte matchar</span><span class="sxs-lookup"><span data-stu-id="e606b-132">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="e606b-133">mönster för jokertecken</span><span class="sxs-lookup"><span data-stu-id="e606b-133">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="e606b-134">-matcha</span><span class="sxs-lookup"><span data-stu-id="e606b-134">-match</span></span>       | <span data-ttu-id="e606b-135">Returnerar sant när strängen matchar regex</span><span class="sxs-lookup"><span data-stu-id="e606b-135">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="e606b-136">ofta $matches innehåller matchande strängar</span><span class="sxs-lookup"><span data-stu-id="e606b-136">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="e606b-137">-notmatch</span><span class="sxs-lookup"><span data-stu-id="e606b-137">-notmatch</span></span>    | <span data-ttu-id="e606b-138">Returnerar sant när strängen inte matchar</span><span class="sxs-lookup"><span data-stu-id="e606b-138">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="e606b-139">regex-mönster; $matches innehåller matchande</span><span class="sxs-lookup"><span data-stu-id="e606b-139">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="e606b-140">strängar</span><span class="sxs-lookup"><span data-stu-id="e606b-140">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="e606b-141">Behållare</span><span class="sxs-lookup"><span data-stu-id="e606b-141">Containment</span></span> | <span data-ttu-id="e606b-142">– innehåller</span><span class="sxs-lookup"><span data-stu-id="e606b-142">-contains</span></span>    | <span data-ttu-id="e606b-143">Returnerar sant när referensvärdet finns</span><span class="sxs-lookup"><span data-stu-id="e606b-143">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="e606b-144">i en samling</span><span class="sxs-lookup"><span data-stu-id="e606b-144">in a collection</span></span>                             |
|             | <span data-ttu-id="e606b-145">-notcontains</span><span class="sxs-lookup"><span data-stu-id="e606b-145">-notcontains</span></span> | <span data-ttu-id="e606b-146">Returnerar värdet true när referensvärdet inte</span><span class="sxs-lookup"><span data-stu-id="e606b-146">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="e606b-147">ingår i en samling</span><span class="sxs-lookup"><span data-stu-id="e606b-147">contained in a collection</span></span>                   |
|             | <span data-ttu-id="e606b-148">– in</span><span class="sxs-lookup"><span data-stu-id="e606b-148">-in</span></span>          | <span data-ttu-id="e606b-149">Returnerar sant när test värde i en</span><span class="sxs-lookup"><span data-stu-id="e606b-149">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="e606b-150">samling</span><span class="sxs-lookup"><span data-stu-id="e606b-150">collection</span></span>                                  |
|             | <span data-ttu-id="e606b-151">-notin</span><span class="sxs-lookup"><span data-stu-id="e606b-151">-notin</span></span>       | <span data-ttu-id="e606b-152">Returnerar sant när test värde inte ingår</span><span class="sxs-lookup"><span data-stu-id="e606b-152">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="e606b-153">i en samling</span><span class="sxs-lookup"><span data-stu-id="e606b-153">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="e606b-154">Ny funktion</span><span class="sxs-lookup"><span data-stu-id="e606b-154">Replacement</span></span> | <span data-ttu-id="e606b-155">-Ersätt</span><span class="sxs-lookup"><span data-stu-id="e606b-155">-replace</span></span>     | <span data-ttu-id="e606b-156">Ersätter ett sträng mönster</span><span class="sxs-lookup"><span data-stu-id="e606b-156">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="e606b-157">Typ</span><span class="sxs-lookup"><span data-stu-id="e606b-157">Type</span></span>        | <span data-ttu-id="e606b-158">-är</span><span class="sxs-lookup"><span data-stu-id="e606b-158">-is</span></span>          | <span data-ttu-id="e606b-159">Returnerar true om båda objekten är identiska</span><span class="sxs-lookup"><span data-stu-id="e606b-159">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="e606b-160">typ</span><span class="sxs-lookup"><span data-stu-id="e606b-160">type</span></span>                                        |
|             | <span data-ttu-id="e606b-161">– IsNot</span><span class="sxs-lookup"><span data-stu-id="e606b-161">-isnot</span></span>       | <span data-ttu-id="e606b-162">Returnerar sant om objekten inte är samma</span><span class="sxs-lookup"><span data-stu-id="e606b-162">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="e606b-163">typ</span><span class="sxs-lookup"><span data-stu-id="e606b-163">type</span></span>                                        |

<span data-ttu-id="e606b-164">Som standard är alla jämförelse operatorer Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="e606b-164">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="e606b-165">Om du vill göra en jämförelse operator Skift läges känslig, måste du före operator namnet med en `c` .</span><span class="sxs-lookup"><span data-stu-id="e606b-165">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="e606b-166">Till exempel är den Skift läges känsliga versionen av `-eq` är `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="e606b-166">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="e606b-167">Om du vill göra Skift läges känsligheten explicit måste du föregå operatorn med en `i` .</span><span class="sxs-lookup"><span data-stu-id="e606b-167">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="e606b-168">Till exempel är den explicita Skift läges känsliga versionen `-eq` av `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="e606b-168">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="e606b-169">När indatamängden till en operator är ett skalärt värde returnerar jämförelse operatorer ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-169">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="e606b-170">När indatatypen är en samling med värden returnerar jämförelse operatorer alla matchande värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-170">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="e606b-171">Om det inte finns några matchningar i en samling returnerar jämförelse operatorer en tom matris.</span><span class="sxs-lookup"><span data-stu-id="e606b-171">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="e606b-172">Undantagen är operatorerna för inne slutning, operatorerna och typ operatorerna, som alltid returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-172">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="e606b-173">Om du behöver jämföra ett värde med till `$null` `$null` vänster i jämförelsen.</span><span class="sxs-lookup"><span data-stu-id="e606b-173">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="e606b-174">När du jämför `$null` med ett **objekt []** är resultatet **falskt** eftersom jämförelse objektet är en matris.</span><span class="sxs-lookup"><span data-stu-id="e606b-174">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="e606b-175">När du jämför en matris med `$null` filtrerar jämförelser alla `$null` värden som lagras i matrisen.</span><span class="sxs-lookup"><span data-stu-id="e606b-175">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="e606b-176">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-176">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a><span data-ttu-id="e606b-177">Likhets operatorer</span><span class="sxs-lookup"><span data-stu-id="e606b-177">Equality Operators</span></span>

<span data-ttu-id="e606b-178">Likhets operatorerna ( `-eq` , `-ne` ) returnerar värdet true eller matchar när ett eller flera indatavärden är identiska med det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="e606b-178">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="e606b-179">Hela mönstret måste matcha ett helt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-179">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="e606b-180">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-180">Example:</span></span>

#### <a name="-eq"></a><span data-ttu-id="e606b-181">-EQ</span><span class="sxs-lookup"><span data-stu-id="e606b-181">-eq</span></span>

<span data-ttu-id="e606b-182">Beskrivning: lika med.</span><span class="sxs-lookup"><span data-stu-id="e606b-182">Description: Equal to.</span></span> <span data-ttu-id="e606b-183">Innehåller ett identiskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-183">Includes an identical value.</span></span>

<span data-ttu-id="e606b-184">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-184">Example:</span></span>

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

#### <a name="-ne"></a><span data-ttu-id="e606b-185">-Ne</span><span class="sxs-lookup"><span data-stu-id="e606b-185">-ne</span></span>

<span data-ttu-id="e606b-186">Beskrivning: inte lika med.</span><span class="sxs-lookup"><span data-stu-id="e606b-186">Description: Not equal to.</span></span> <span data-ttu-id="e606b-187">Innehåller ett annat värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-187">Includes a different value.</span></span>

<span data-ttu-id="e606b-188">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-188">Example:</span></span>

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

#### <a name="-gt"></a><span data-ttu-id="e606b-189">-gt</span><span class="sxs-lookup"><span data-stu-id="e606b-189">-gt</span></span>

<span data-ttu-id="e606b-190">Beskrivning: större än.</span><span class="sxs-lookup"><span data-stu-id="e606b-190">Description: Greater-than.</span></span>

<span data-ttu-id="e606b-191">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-191">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="e606b-192">Detta bör inte förväxlas med `>` operatorn större än i många andra programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="e606b-192">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="e606b-193">I PowerShell `>` används för omdirigering.</span><span class="sxs-lookup"><span data-stu-id="e606b-193">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="e606b-194">Mer information finns i [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span><span class="sxs-lookup"><span data-stu-id="e606b-194">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

#### <a name="-ge"></a><span data-ttu-id="e606b-195">-ge</span><span class="sxs-lookup"><span data-stu-id="e606b-195">-ge</span></span>

<span data-ttu-id="e606b-196">Beskrivning: större än eller lika med.</span><span class="sxs-lookup"><span data-stu-id="e606b-196">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="e606b-197">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-197">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a><span data-ttu-id="e606b-198">-lt</span><span class="sxs-lookup"><span data-stu-id="e606b-198">-lt</span></span>

<span data-ttu-id="e606b-199">Beskrivning: mindre än.</span><span class="sxs-lookup"><span data-stu-id="e606b-199">Description: Less-than.</span></span>

<span data-ttu-id="e606b-200">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-200">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a><span data-ttu-id="e606b-201">-Le</span><span class="sxs-lookup"><span data-stu-id="e606b-201">-le</span></span>

<span data-ttu-id="e606b-202">Beskrivning: mindre än eller lika med.</span><span class="sxs-lookup"><span data-stu-id="e606b-202">Description: Less-than or equal to.</span></span>

<span data-ttu-id="e606b-203">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-203">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a><span data-ttu-id="e606b-204">Matchande operatorer</span><span class="sxs-lookup"><span data-stu-id="e606b-204">Matching Operators</span></span>

<span data-ttu-id="e606b-205">Operatorerna like ( `-like` och `-notlike` ) hittar element som matchar eller inte matchar ett angivet mönster med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="e606b-205">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="e606b-206">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-206">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="e606b-207">Matchnings operatorerna ( `-match` och `-notmatch` ) söker efter element som matchar eller inte matchar ett angivet mönster med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="e606b-207">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="e606b-208">Match operatorerna fyller den `$Matches` automatiska variabeln när indatamängden (det vänstra argumentet) till operatorn är ett enda skalärt objekt.</span><span class="sxs-lookup"><span data-stu-id="e606b-208">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="e606b-209">När invärdet är skalärt `-match` , `-notmatch` returnerar operatorn och det booleska värdet och anger värdet för den `$Matches` automatiska variabeln till de matchade komponenterna i argumentet.</span><span class="sxs-lookup"><span data-stu-id="e606b-209">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="e606b-210">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-210">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a><span data-ttu-id="e606b-211">– som</span><span class="sxs-lookup"><span data-stu-id="e606b-211">-like</span></span>

<span data-ttu-id="e606b-212">Beskrivning: matcha med jokertecknet ( \* ).</span><span class="sxs-lookup"><span data-stu-id="e606b-212">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="e606b-213">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-213">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a><span data-ttu-id="e606b-214">-notlike</span><span class="sxs-lookup"><span data-stu-id="e606b-214">-notlike</span></span>

<span data-ttu-id="e606b-215">Beskrivning: överensstämmer inte med jokertecknet ( \* ).</span><span class="sxs-lookup"><span data-stu-id="e606b-215">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="e606b-216">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-216">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="e606b-217">-matcha</span><span class="sxs-lookup"><span data-stu-id="e606b-217">-match</span></span>

<span data-ttu-id="e606b-218">Beskrivning: matchar en sträng med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="e606b-218">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="e606b-219">När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.</span><span class="sxs-lookup"><span data-stu-id="e606b-219">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="e606b-220">Om indatamängden är en samling, `-match` `-notmatch` returnerar operatorn och de matchande medlemmarna i samlingen, men operatorn fyller inte `$Matches` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e606b-220">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="e606b-221">Följande kommando skickar till exempel en samling med strängar till `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="e606b-221">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="e606b-222">`-match`Operatorn returnerar objekten i den samling som matchar.</span><span class="sxs-lookup"><span data-stu-id="e606b-222">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="e606b-223">Den automatiska variabeln fylls inte i `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="e606b-223">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="e606b-224">Följande kommando skickar däremot en enskild sträng till `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="e606b-224">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="e606b-225">`-match`Operatorn returnerar ett booleskt värde och fyller den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="e606b-225">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="e606b-226">Den `$Matches` automatiska variabeln är en **hash** -variabel.</span><span class="sxs-lookup"><span data-stu-id="e606b-226">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="e606b-227">Om ingen gruppering eller hämtning används, fylls bara en nyckel i.</span><span class="sxs-lookup"><span data-stu-id="e606b-227">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="e606b-228">`0`Nyckeln representerar all text som matchades.</span><span class="sxs-lookup"><span data-stu-id="e606b-228">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="e606b-229">Mer information om gruppering och insamling av reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e606b-229">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="e606b-230">Det är viktigt att notera att hash-tabellen `$Matches` bara innehåller den första förekomsten av eventuella matchande mönster.</span><span class="sxs-lookup"><span data-stu-id="e606b-230">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="e606b-231">`0`Nyckeln är ett **heltal**.</span><span class="sxs-lookup"><span data-stu-id="e606b-231">The `0` key is an **Integer**.</span></span> <span data-ttu-id="e606b-232">Du kan använda valfri **hash** -Metod för att komma åt värdet som lagras.</span><span class="sxs-lookup"><span data-stu-id="e606b-232">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```powershell
> PS> "Good Dog" -match "Dog"
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

<span data-ttu-id="e606b-233">`-notmatch`Operatorn fyller den `$Matches` automatiska variabeln när indatatypen är skalär och resultatet är falskt, det vill säga när en matchning upptäcks.</span><span class="sxs-lookup"><span data-stu-id="e606b-233">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

#### <a name="-notmatch"></a><span data-ttu-id="e606b-234">-notmatch</span><span class="sxs-lookup"><span data-stu-id="e606b-234">-notmatch</span></span>

<span data-ttu-id="e606b-235">Beskrivning: matchar inte en sträng.</span><span class="sxs-lookup"><span data-stu-id="e606b-235">Description: Does not match a string.</span></span> <span data-ttu-id="e606b-236">Använder reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="e606b-236">Uses regular expressions.</span></span> <span data-ttu-id="e606b-237">När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.</span><span class="sxs-lookup"><span data-stu-id="e606b-237">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="e606b-238">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-238">Example:</span></span>

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

### <a name="containment-operators"></a><span data-ttu-id="e606b-239">Inne slutnings operatorer</span><span class="sxs-lookup"><span data-stu-id="e606b-239">Containment Operators</span></span>

<span data-ttu-id="e606b-240">Inne slutnings operatorerna ( `-contains` och `-notcontains` ) liknar likhets operatorerna.</span><span class="sxs-lookup"><span data-stu-id="e606b-240">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="e606b-241">Däremot returnerar inne slutnings operatorer alltid ett booleskt värde, även om indatatypen är en samling.</span><span class="sxs-lookup"><span data-stu-id="e606b-241">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="e606b-242">Till skillnad från likhets operatorerna returnerar inne slutnings operatorerna ett värde så fort de identifierar den första matchningen.</span><span class="sxs-lookup"><span data-stu-id="e606b-242">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="e606b-243">Likhets operatorerna utvärderar alla indatatyper och returnerar sedan alla träffar i samlingen.</span><span class="sxs-lookup"><span data-stu-id="e606b-243">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

#### <a name="-contains"></a><span data-ttu-id="e606b-244">– innehåller</span><span class="sxs-lookup"><span data-stu-id="e606b-244">-contains</span></span>

<span data-ttu-id="e606b-245">Beskrivning: inne slutnings operator.</span><span class="sxs-lookup"><span data-stu-id="e606b-245">Description: Containment operator.</span></span> <span data-ttu-id="e606b-246">Anger om en samling med referens värden innehåller ett enda testvärde.</span><span class="sxs-lookup"><span data-stu-id="e606b-246">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="e606b-247">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-247">Always returns a Boolean value.</span></span> <span data-ttu-id="e606b-248">Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.</span><span class="sxs-lookup"><span data-stu-id="e606b-248">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="e606b-249">När testvärdet är en samling använder operatorn referens likhet.</span><span class="sxs-lookup"><span data-stu-id="e606b-249">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="e606b-250">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-250">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="e606b-251">I en mycket stor samling `-contains` returnerar operatorn snabbare resultat än operatorn lika med.</span><span class="sxs-lookup"><span data-stu-id="e606b-251">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="e606b-252">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-252">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="e606b-253">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-253">Examples:</span></span>

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

#### <a name="-notcontains"></a><span data-ttu-id="e606b-254">-notcontains</span><span class="sxs-lookup"><span data-stu-id="e606b-254">-notcontains</span></span>

<span data-ttu-id="e606b-255">Beskrivning: inne slutnings operator.</span><span class="sxs-lookup"><span data-stu-id="e606b-255">Description: Containment operator.</span></span> <span data-ttu-id="e606b-256">Anger om en samling med referens värden innehåller ett enda testvärde.</span><span class="sxs-lookup"><span data-stu-id="e606b-256">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="e606b-257">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-257">Always returns a Boolean value.</span></span> <span data-ttu-id="e606b-258">Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-258">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="e606b-259">När testvärdet är en samling använder NotContains-operatorn referens likhet.</span><span class="sxs-lookup"><span data-stu-id="e606b-259">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="e606b-260">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-260">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="e606b-261">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-261">Examples:</span></span>

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

#### <a name="-in"></a><span data-ttu-id="e606b-262">– in</span><span class="sxs-lookup"><span data-stu-id="e606b-262">-in</span></span>

<span data-ttu-id="e606b-263">Beskrivning: i-Operator.</span><span class="sxs-lookup"><span data-stu-id="e606b-263">Description: In operator.</span></span> <span data-ttu-id="e606b-264">Anger om ett testvärde visas i en samling med referens värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-264">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="e606b-265">Returnera alltid som booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-265">Always return as Boolean value.</span></span> <span data-ttu-id="e606b-266">Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.</span><span class="sxs-lookup"><span data-stu-id="e606b-266">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="e606b-267">När testvärdet är en samling använder operatorn i referens likhet.</span><span class="sxs-lookup"><span data-stu-id="e606b-267">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="e606b-268">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-268">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="e606b-269">`-in`Operatorn introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e606b-269">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="e606b-270">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-270">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="e606b-271">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-271">Examples:</span></span>

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

#### <a name="-notin"></a><span data-ttu-id="e606b-272">-notin</span><span class="sxs-lookup"><span data-stu-id="e606b-272">-notin</span></span>

<span data-ttu-id="e606b-273">Beskrivning: anger om ett testvärde visas i en samling med referens värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-273">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="e606b-274">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-274">Always returns a Boolean value.</span></span> <span data-ttu-id="e606b-275">Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.</span><span class="sxs-lookup"><span data-stu-id="e606b-275">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="e606b-276">När testvärdet är en samling använder operatorn i referens likhet.</span><span class="sxs-lookup"><span data-stu-id="e606b-276">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="e606b-277">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="e606b-277">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="e606b-278">`-notin`Operatorn introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e606b-278">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="e606b-279">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-279">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="e606b-280">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-280">Examples:</span></span>

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

### <a name="replacement-operator"></a><span data-ttu-id="e606b-281">Ersättnings operatör</span><span class="sxs-lookup"><span data-stu-id="e606b-281">Replacement Operator</span></span>

<span data-ttu-id="e606b-282">`-replace`Operatorn ersätter hela eller delar av ett värde med det angivna värdet med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="e606b-282">The `-replace` operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="e606b-283">Du kan använda `-replace` operatorn för många administrativa uppgifter, till exempel att byta namn på filer.</span><span class="sxs-lookup"><span data-stu-id="e606b-283">You can use the `-replace` operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="e606b-284">Följande kommando ändrar till exempel fil namns tilläggen för alla txt-filer till. log:</span><span class="sxs-lookup"><span data-stu-id="e606b-284">For example, the following command changes the file name extensions of all .txt files to .log:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="e606b-285">`-replace`Operatorns syntax är följande, där `<original>` plats hållaren representerar de tecken som ska ersättas och `<substitute>` plats hållaren representerar de tecken som ersätter dem:</span><span class="sxs-lookup"><span data-stu-id="e606b-285">The syntax of the `-replace` operator is as follows, where the `<original>` placeholder represents the characters to be replaced, and the `<substitute>` placeholder represents the characters that will replace them:</span></span>

`<input> <operator> <original>, <substitute>`

<span data-ttu-id="e606b-286">Som standard `-replace` är operatorn Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="e606b-286">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="e606b-287">Använd för att göra det Skift läges känsligt `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="e606b-287">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="e606b-288">Använd om du vill göra det uttryckligen Skift läges okänsligt `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="e606b-288">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="e606b-289">Överväg följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-289">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

<span data-ttu-id="e606b-290">Det går också att använda reguljära uttryck för att dynamiskt ersätta text med hjälp av insamlings grupper och ersättningar.</span><span class="sxs-lookup"><span data-stu-id="e606b-290">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="e606b-291">Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e606b-291">For more information, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="scriptblock-substitutions"></a><span data-ttu-id="e606b-292">Script block ersättningar</span><span class="sxs-lookup"><span data-stu-id="e606b-292">ScriptBlock substitutions</span></span>

<span data-ttu-id="e606b-293">Från och med PowerShell 6 kan du använda ett **script block** -argument för *ersättnings* texten.</span><span class="sxs-lookup"><span data-stu-id="e606b-293">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the *Substitution* text.</span></span> <span data-ttu-id="e606b-294">**Script block** körs för varje matchning som hittades i *Indatasträngen* .</span><span class="sxs-lookup"><span data-stu-id="e606b-294">The **ScriptBlock** will execute for each match found in the *input* string.</span></span>

<span data-ttu-id="e606b-295">I **script block** använder du den `$_` automatiska variabeln för att referera till det aktuella **systemet. text. RegularExpressions. match** -objektet.</span><span class="sxs-lookup"><span data-stu-id="e606b-295">Within the **ScriptBlock** , use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="e606b-296">**Match** -objektet ger dig åtkomst till den aktuella inmatade texten som ersätts samt annan användbar information.</span><span class="sxs-lookup"><span data-stu-id="e606b-296">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="e606b-297">Det här exemplet ersätter varje sekvens med tre decimaler med motsvarande tecken.</span><span class="sxs-lookup"><span data-stu-id="e606b-297">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="e606b-298">**Script block** körs för varje uppsättning av tre decimaler som måste ersättas.</span><span class="sxs-lookup"><span data-stu-id="e606b-298">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

### <a name="type-comparison"></a><span data-ttu-id="e606b-299">Typ jämförelse</span><span class="sxs-lookup"><span data-stu-id="e606b-299">Type comparison</span></span>

<span data-ttu-id="e606b-300">Typ jämförelse operatorer ( `-is` och `-isnot` ) används för att avgöra om ett objekt är en speciell typ.</span><span class="sxs-lookup"><span data-stu-id="e606b-300">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

#### <a name="-is"></a><span data-ttu-id="e606b-301">-är</span><span class="sxs-lookup"><span data-stu-id="e606b-301">-is</span></span>

<span data-ttu-id="e606b-302">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-302">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="e606b-303">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-303">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a><span data-ttu-id="e606b-304">– IsNot</span><span class="sxs-lookup"><span data-stu-id="e606b-304">-isnot</span></span>

<span data-ttu-id="e606b-305">Syntax:</span><span class="sxs-lookup"><span data-stu-id="e606b-305">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="e606b-306">Exempel:</span><span class="sxs-lookup"><span data-stu-id="e606b-306">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="e606b-307">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="e606b-307">SEE ALSO</span></span>

- [<span data-ttu-id="e606b-308">about_Operators</span><span class="sxs-lookup"><span data-stu-id="e606b-308">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="e606b-309">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="e606b-309">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="e606b-310">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="e606b-310">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="e606b-311">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="e606b-311">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="e606b-312">-Objekt</span><span class="sxs-lookup"><span data-stu-id="e606b-312">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="e606b-313">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="e606b-313">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
