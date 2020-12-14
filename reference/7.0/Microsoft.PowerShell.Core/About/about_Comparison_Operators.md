---
description: Beskriver de operatorer som jämför värden i PowerShell.
Locale: en-US
ms.date: 12/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: dbda5371224345a2e22dd281c17ae0d7c928aad6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090234"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="98053-103">Om jämförelse operatorer</span><span class="sxs-lookup"><span data-stu-id="98053-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="98053-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="98053-104">Short description</span></span>
<span data-ttu-id="98053-105">Beskriver de operatorer som jämför värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98053-105">Describes the operators that compare values in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="98053-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="98053-106">Long description</span></span>

<span data-ttu-id="98053-107">Med jämförelse operatorer kan du ange villkor för jämförelse av värden och hitta värden som matchar angivna mönster.</span><span class="sxs-lookup"><span data-stu-id="98053-107">Comparison operators let you specify conditions for comparing values and finding values that match specified patterns.</span></span> <span data-ttu-id="98053-108">Om du vill använda en jämförelse operator anger du de värden som du vill jämföra tillsammans med en operator som särskiljer dessa värden.</span><span class="sxs-lookup"><span data-stu-id="98053-108">To use a comparison operator, specify the values that you want to compare together with an operator that separates these values.</span></span>

<span data-ttu-id="98053-109">PowerShell innehåller följande jämförelse operatorer:</span><span class="sxs-lookup"><span data-stu-id="98053-109">PowerShell includes the following comparison operators:</span></span>

| <span data-ttu-id="98053-110">Typ</span><span class="sxs-lookup"><span data-stu-id="98053-110">Type</span></span>        | <span data-ttu-id="98053-111">Operatorer</span><span class="sxs-lookup"><span data-stu-id="98053-111">Operators</span></span>    | <span data-ttu-id="98053-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98053-112">Description</span></span>                                 |
| ----------- | ------------ | --------------------------------------------|
| <span data-ttu-id="98053-113">Likhet</span><span class="sxs-lookup"><span data-stu-id="98053-113">Equality</span></span>    | <span data-ttu-id="98053-114">-EQ</span><span class="sxs-lookup"><span data-stu-id="98053-114">-eq</span></span>          | <span data-ttu-id="98053-115">lika med</span><span class="sxs-lookup"><span data-stu-id="98053-115">equals</span></span>                                      |
|             | <span data-ttu-id="98053-116">-Ne</span><span class="sxs-lookup"><span data-stu-id="98053-116">-ne</span></span>          | <span data-ttu-id="98053-117">inte lika med</span><span class="sxs-lookup"><span data-stu-id="98053-117">not equals</span></span>                                  |
|             | <span data-ttu-id="98053-118">-gt</span><span class="sxs-lookup"><span data-stu-id="98053-118">-gt</span></span>          | <span data-ttu-id="98053-119">större än</span><span class="sxs-lookup"><span data-stu-id="98053-119">greater than</span></span>                                |
|             | <span data-ttu-id="98053-120">-ge</span><span class="sxs-lookup"><span data-stu-id="98053-120">-ge</span></span>          | <span data-ttu-id="98053-121">större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="98053-121">greater than or equal</span></span>                       |
|             | <span data-ttu-id="98053-122">-lt</span><span class="sxs-lookup"><span data-stu-id="98053-122">-lt</span></span>          | <span data-ttu-id="98053-123">mindre än</span><span class="sxs-lookup"><span data-stu-id="98053-123">less than</span></span>                                   |
|             | <span data-ttu-id="98053-124">-Le</span><span class="sxs-lookup"><span data-stu-id="98053-124">-le</span></span>          | <span data-ttu-id="98053-125">mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="98053-125">less than or equal</span></span>                          |
|             |              |                                             |
| <span data-ttu-id="98053-126">Matching</span><span class="sxs-lookup"><span data-stu-id="98053-126">Matching</span></span>    | <span data-ttu-id="98053-127">– som</span><span class="sxs-lookup"><span data-stu-id="98053-127">-like</span></span>        | <span data-ttu-id="98053-128">Returnerar true när strängen matchar jokertecken</span><span class="sxs-lookup"><span data-stu-id="98053-128">Returns true when string matches wildcard</span></span>   |
|             |              | <span data-ttu-id="98053-129">ofta</span><span class="sxs-lookup"><span data-stu-id="98053-129">pattern</span></span>                                     |
|             | <span data-ttu-id="98053-130">-notlike</span><span class="sxs-lookup"><span data-stu-id="98053-130">-notlike</span></span>     | <span data-ttu-id="98053-131">Returnerar sant när strängen inte matchar</span><span class="sxs-lookup"><span data-stu-id="98053-131">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="98053-132">mönster för jokertecken</span><span class="sxs-lookup"><span data-stu-id="98053-132">wildcard pattern</span></span>                            |
|             | <span data-ttu-id="98053-133">-matcha</span><span class="sxs-lookup"><span data-stu-id="98053-133">-match</span></span>       | <span data-ttu-id="98053-134">Returnerar sant när strängen matchar regex</span><span class="sxs-lookup"><span data-stu-id="98053-134">Returns true when string matches regex</span></span>      |
|             |              | <span data-ttu-id="98053-135">ofta $matches innehåller matchande strängar</span><span class="sxs-lookup"><span data-stu-id="98053-135">pattern; $matches contains matching strings</span></span> |
|             | <span data-ttu-id="98053-136">-notmatch</span><span class="sxs-lookup"><span data-stu-id="98053-136">-notmatch</span></span>    | <span data-ttu-id="98053-137">Returnerar sant när strängen inte matchar</span><span class="sxs-lookup"><span data-stu-id="98053-137">Returns true when string does not match</span></span>     |
|             |              | <span data-ttu-id="98053-138">regex-mönster; $matches innehåller matchande</span><span class="sxs-lookup"><span data-stu-id="98053-138">regex pattern; $matches contains matching</span></span>   |
|             |              | <span data-ttu-id="98053-139">strängar</span><span class="sxs-lookup"><span data-stu-id="98053-139">strings</span></span>                                     |
|             |              |                                             |
| <span data-ttu-id="98053-140">Behållare</span><span class="sxs-lookup"><span data-stu-id="98053-140">Containment</span></span> | <span data-ttu-id="98053-141">– innehåller</span><span class="sxs-lookup"><span data-stu-id="98053-141">-contains</span></span>    | <span data-ttu-id="98053-142">Returnerar sant när referensvärdet finns</span><span class="sxs-lookup"><span data-stu-id="98053-142">Returns true when reference value contained</span></span> |
|             |              | <span data-ttu-id="98053-143">i en samling</span><span class="sxs-lookup"><span data-stu-id="98053-143">in a collection</span></span>                             |
|             | <span data-ttu-id="98053-144">-notcontains</span><span class="sxs-lookup"><span data-stu-id="98053-144">-notcontains</span></span> | <span data-ttu-id="98053-145">Returnerar värdet true när referensvärdet inte</span><span class="sxs-lookup"><span data-stu-id="98053-145">Returns true when reference value not</span></span>       |
|             |              | <span data-ttu-id="98053-146">ingår i en samling</span><span class="sxs-lookup"><span data-stu-id="98053-146">contained in a collection</span></span>                   |
|             | <span data-ttu-id="98053-147">– in</span><span class="sxs-lookup"><span data-stu-id="98053-147">-in</span></span>          | <span data-ttu-id="98053-148">Returnerar sant när test värde i en</span><span class="sxs-lookup"><span data-stu-id="98053-148">Returns true when test value contained in a</span></span> |
|             |              | <span data-ttu-id="98053-149">samling</span><span class="sxs-lookup"><span data-stu-id="98053-149">collection</span></span>                                  |
|             | <span data-ttu-id="98053-150">-notin</span><span class="sxs-lookup"><span data-stu-id="98053-150">-notin</span></span>       | <span data-ttu-id="98053-151">Returnerar sant när test värde inte ingår</span><span class="sxs-lookup"><span data-stu-id="98053-151">Returns true when test value not contained</span></span>  |
|             |              | <span data-ttu-id="98053-152">i en samling</span><span class="sxs-lookup"><span data-stu-id="98053-152">in a collection</span></span>                             |
|             |              |                                             |
| <span data-ttu-id="98053-153">Ny funktion</span><span class="sxs-lookup"><span data-stu-id="98053-153">Replacement</span></span> | <span data-ttu-id="98053-154">-Ersätt</span><span class="sxs-lookup"><span data-stu-id="98053-154">-replace</span></span>     | <span data-ttu-id="98053-155">Ersätter ett sträng mönster</span><span class="sxs-lookup"><span data-stu-id="98053-155">Replaces a string pattern</span></span>                   |
|             |              |                                             |
| <span data-ttu-id="98053-156">Typ</span><span class="sxs-lookup"><span data-stu-id="98053-156">Type</span></span>        | <span data-ttu-id="98053-157">-är</span><span class="sxs-lookup"><span data-stu-id="98053-157">-is</span></span>          | <span data-ttu-id="98053-158">Returnerar true om båda objekten är identiska</span><span class="sxs-lookup"><span data-stu-id="98053-158">Returns true if both object are the same</span></span>    |
|             |              | <span data-ttu-id="98053-159">typ</span><span class="sxs-lookup"><span data-stu-id="98053-159">type</span></span>                                        |
|             | <span data-ttu-id="98053-160">– IsNot</span><span class="sxs-lookup"><span data-stu-id="98053-160">-isnot</span></span>       | <span data-ttu-id="98053-161">Returnerar sant om objekten inte är samma</span><span class="sxs-lookup"><span data-stu-id="98053-161">Returns true if the objects are not the same</span></span>|
|             |              | <span data-ttu-id="98053-162">typ</span><span class="sxs-lookup"><span data-stu-id="98053-162">type</span></span>                                        |

<span data-ttu-id="98053-163">Som standard är alla jämförelse operatorer Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="98053-163">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="98053-164">Om du vill göra en jämförelse operator Skift läges känslig, måste du före operator namnet med en `c` .</span><span class="sxs-lookup"><span data-stu-id="98053-164">To make a comparison operator case-sensitive, precede the operator name with a `c`.</span></span> <span data-ttu-id="98053-165">Till exempel är den Skift läges känsliga versionen av `-eq` är `-ceq` .</span><span class="sxs-lookup"><span data-stu-id="98053-165">For example, the case-sensitive version of `-eq` is `-ceq`.</span></span> <span data-ttu-id="98053-166">Om du vill göra Skift läges känsligheten explicit måste du föregå operatorn med en `i` .</span><span class="sxs-lookup"><span data-stu-id="98053-166">To make the case-insensitivity explicit, precede the operator with an `i`.</span></span> <span data-ttu-id="98053-167">Till exempel är den explicita Skift läges känsliga versionen `-eq` av `-ieq` .</span><span class="sxs-lookup"><span data-stu-id="98053-167">For example, the explicitly case-insensitive version of `-eq` is `-ieq`.</span></span>

<span data-ttu-id="98053-168">När indatamängden till en operator är ett skalärt värde returnerar jämförelse operatorer ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-168">When the input to an operator is a scalar value, comparison operators return a Boolean value.</span></span> <span data-ttu-id="98053-169">När indatatypen är en samling med värden returnerar jämförelse operatorer alla matchande värden.</span><span class="sxs-lookup"><span data-stu-id="98053-169">When the input is a collection of values, the comparison operators return any matching values.</span></span> <span data-ttu-id="98053-170">Om det inte finns några matchningar i en samling returnerar jämförelse operatorer en tom matris.</span><span class="sxs-lookup"><span data-stu-id="98053-170">If there are no matches in a collection, comparison operators return an empty array.</span></span>

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

<span data-ttu-id="98053-171">Undantagen är operatorerna för inne slutning, operatorerna och typ operatorerna, som alltid returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="98053-171">The exceptions are the containment operators, the In operators, and the type operators, which always return a **Boolean** value.</span></span>

> [!NOTE]
> <span data-ttu-id="98053-172">Om du behöver jämföra ett värde med till `$null` `$null` vänster i jämförelsen.</span><span class="sxs-lookup"><span data-stu-id="98053-172">If you need to compare a value to `$null` you should put `$null` on the left-hand side of the comparison.</span></span> <span data-ttu-id="98053-173">När du jämför `$null` med ett **objekt []** är resultatet **falskt** eftersom jämförelse objektet är en matris.</span><span class="sxs-lookup"><span data-stu-id="98053-173">When you compare `$null` to an **Object[]** the result is **False** because the comparison object is an array.</span></span> <span data-ttu-id="98053-174">När du jämför en matris med `$null` filtrerar jämförelser alla `$null` värden som lagras i matrisen.</span><span class="sxs-lookup"><span data-stu-id="98053-174">When you compare an array to `$null`, the comparison filters out any `$null` values stored in the array.</span></span> <span data-ttu-id="98053-175">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-175">For example:</span></span>
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

## <a name="equality-operators"></a><span data-ttu-id="98053-176">Likhetsoperatorer</span><span class="sxs-lookup"><span data-stu-id="98053-176">Equality operators</span></span>

<span data-ttu-id="98053-177">Likhets operatorerna ( `-eq` , `-ne` ) returnerar värdet true eller matchar när ett eller flera indatavärden är identiska med det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="98053-177">The equality operators (`-eq`, `-ne`) return a value of TRUE or the matches when one or more of the input values is identical to the specified pattern.</span></span> <span data-ttu-id="98053-178">Hela mönstret måste matcha ett helt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-178">The entire pattern must match an entire value.</span></span>

<span data-ttu-id="98053-179">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-179">Example:</span></span>

### <a name="-eq"></a><span data-ttu-id="98053-180">-EQ</span><span class="sxs-lookup"><span data-stu-id="98053-180">-eq</span></span>

<span data-ttu-id="98053-181">Beskrivning: lika med.</span><span class="sxs-lookup"><span data-stu-id="98053-181">Description: Equal to.</span></span> <span data-ttu-id="98053-182">Innehåller ett identiskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-182">Includes an identical value.</span></span>

<span data-ttu-id="98053-183">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-183">Example:</span></span>

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

### <a name="-ne"></a><span data-ttu-id="98053-184">-Ne</span><span class="sxs-lookup"><span data-stu-id="98053-184">-ne</span></span>

<span data-ttu-id="98053-185">Beskrivning: inte lika med.</span><span class="sxs-lookup"><span data-stu-id="98053-185">Description: Not equal to.</span></span> <span data-ttu-id="98053-186">Innehåller ett annat värde.</span><span class="sxs-lookup"><span data-stu-id="98053-186">Includes a different value.</span></span>

<span data-ttu-id="98053-187">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-187">Example:</span></span>

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

### <a name="-gt"></a><span data-ttu-id="98053-188">-gt</span><span class="sxs-lookup"><span data-stu-id="98053-188">-gt</span></span>

<span data-ttu-id="98053-189">Beskrivning: större än.</span><span class="sxs-lookup"><span data-stu-id="98053-189">Description: Greater-than.</span></span>

<span data-ttu-id="98053-190">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-190">Example:</span></span>

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> <span data-ttu-id="98053-191">Detta bör inte förväxlas med `>` operatorn större än i många andra programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="98053-191">This should not to be confused with `>`, the greater-than operator in many other programming languages.</span></span> <span data-ttu-id="98053-192">I PowerShell `>` används för omdirigering.</span><span class="sxs-lookup"><span data-stu-id="98053-192">In PowerShell, `>` is used for redirection.</span></span> <span data-ttu-id="98053-193">Mer information finns i [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span><span class="sxs-lookup"><span data-stu-id="98053-193">For more information, see [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).</span></span>

### <a name="-ge"></a><span data-ttu-id="98053-194">-ge</span><span class="sxs-lookup"><span data-stu-id="98053-194">-ge</span></span>

<span data-ttu-id="98053-195">Beskrivning: större än eller lika med.</span><span class="sxs-lookup"><span data-stu-id="98053-195">Description: Greater-than or equal to.</span></span>

<span data-ttu-id="98053-196">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-196">Example:</span></span>

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

### <a name="-lt"></a><span data-ttu-id="98053-197">-lt</span><span class="sxs-lookup"><span data-stu-id="98053-197">-lt</span></span>

<span data-ttu-id="98053-198">Beskrivning: mindre än.</span><span class="sxs-lookup"><span data-stu-id="98053-198">Description: Less-than.</span></span>

<span data-ttu-id="98053-199">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-199">Example:</span></span>

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

### <a name="-le"></a><span data-ttu-id="98053-200">-Le</span><span class="sxs-lookup"><span data-stu-id="98053-200">-le</span></span>

<span data-ttu-id="98053-201">Beskrivning: mindre än eller lika med.</span><span class="sxs-lookup"><span data-stu-id="98053-201">Description: Less-than or equal to.</span></span>

<span data-ttu-id="98053-202">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-202">Example:</span></span>

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

## <a name="matching-operators"></a><span data-ttu-id="98053-203">Matchande operatorer</span><span class="sxs-lookup"><span data-stu-id="98053-203">Matching operators</span></span>

<span data-ttu-id="98053-204">Operatorerna like ( `-like` och `-notlike` ) hittar element som matchar eller inte matchar ett angivet mönster med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="98053-204">The like operators (`-like` and `-notlike`) find elements that match or do not match a specified pattern using wildcard expressions.</span></span>

<span data-ttu-id="98053-205">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-205">The syntax is:</span></span>

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

<span data-ttu-id="98053-206">Matchnings operatorerna ( `-match` och `-notmatch` ) söker efter element som matchar eller inte matchar ett angivet mönster med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="98053-206">The match operators (`-match` and `-notmatch`) find elements that match or do not match a specified pattern using regular expressions.</span></span>

<span data-ttu-id="98053-207">Match operatorerna fyller den `$Matches` automatiska variabeln när indatamängden (det vänstra argumentet) till operatorn är ett enda skalärt objekt.</span><span class="sxs-lookup"><span data-stu-id="98053-207">The match operators populate the `$Matches` automatic variable when the input (the left-side argument) to the operator is a single scalar object.</span></span> <span data-ttu-id="98053-208">När invärdet är skalärt `-match` , `-notmatch` returnerar operatorn och det booleska värdet och anger värdet för den `$Matches` automatiska variabeln till de matchade komponenterna i argumentet.</span><span class="sxs-lookup"><span data-stu-id="98053-208">When the input is scalar, the `-match` and `-notmatch` operators return a Boolean value and set the value of the `$Matches` automatic variable to the matched components of the argument.</span></span>

<span data-ttu-id="98053-209">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-209">The syntax is:</span></span>

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

### <a name="-like"></a><span data-ttu-id="98053-210">– som</span><span class="sxs-lookup"><span data-stu-id="98053-210">-like</span></span>

<span data-ttu-id="98053-211">Beskrivning: matcha med jokertecknet ( \* ).</span><span class="sxs-lookup"><span data-stu-id="98053-211">Description: Match using the wildcard character (\*).</span></span>

<span data-ttu-id="98053-212">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-212">Example:</span></span>

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

### <a name="-notlike"></a><span data-ttu-id="98053-213">-notlike</span><span class="sxs-lookup"><span data-stu-id="98053-213">-notlike</span></span>

<span data-ttu-id="98053-214">Beskrivning: överensstämmer inte med jokertecknet ( \* ).</span><span class="sxs-lookup"><span data-stu-id="98053-214">Description: Does not match using the wildcard character (\*).</span></span>

<span data-ttu-id="98053-215">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-215">Example:</span></span>

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a><span data-ttu-id="98053-216">-matcha</span><span class="sxs-lookup"><span data-stu-id="98053-216">-match</span></span>

<span data-ttu-id="98053-217">Beskrivning: matchar en sträng med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="98053-217">Description: Matches a string using regular expressions.</span></span> <span data-ttu-id="98053-218">När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.</span><span class="sxs-lookup"><span data-stu-id="98053-218">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="98053-219">Om indatamängden är en samling, `-match` `-notmatch` returnerar operatorn och de matchande medlemmarna i samlingen, men operatorn fyller inte `$Matches` variabeln.</span><span class="sxs-lookup"><span data-stu-id="98053-219">If the input is a collection, the `-match` and `-notmatch` operators return the matching members of that collection, but the operator does not populate the `$Matches` variable.</span></span>

<span data-ttu-id="98053-220">Följande kommando skickar till exempel en samling med strängar till `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="98053-220">For example, the following command submits a collection of strings to the `-match` operator.</span></span> <span data-ttu-id="98053-221">`-match`Operatorn returnerar objekten i den samling som matchar.</span><span class="sxs-lookup"><span data-stu-id="98053-221">The `-match` operator returns the items in the collection that match.</span></span> <span data-ttu-id="98053-222">Den automatiska variabeln fylls inte i `$Matches` .</span><span class="sxs-lookup"><span data-stu-id="98053-222">It does not populate the `$Matches` automatic variable.</span></span>

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

<span data-ttu-id="98053-223">Följande kommando skickar däremot en enskild sträng till `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="98053-223">In contrast, the following command submits a single string to the `-match` operator.</span></span> <span data-ttu-id="98053-224">`-match`Operatorn returnerar ett booleskt värde och fyller den `$Matches` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="98053-224">The `-match` operator returns a Boolean value and populates the `$Matches` automatic variable.</span></span> <span data-ttu-id="98053-225">Den `$Matches` automatiska variabeln är en **hash**-variabel.</span><span class="sxs-lookup"><span data-stu-id="98053-225">The `$Matches` automatic variable is a **Hashtable**.</span></span> <span data-ttu-id="98053-226">Om ingen gruppering eller hämtning används, fylls bara en nyckel i.</span><span class="sxs-lookup"><span data-stu-id="98053-226">If no grouping or capturing is used, only one key is populated.</span></span>
<span data-ttu-id="98053-227">`0`Nyckeln representerar all text som matchades.</span><span class="sxs-lookup"><span data-stu-id="98053-227">The `0` key represents all text that was matched.</span></span> <span data-ttu-id="98053-228">Mer information om gruppering och insamling av reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="98053-228">For more information about grouping and capturing using regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

<span data-ttu-id="98053-229">Det är viktigt att notera att hash-tabellen `$Matches` bara innehåller den första förekomsten av eventuella matchande mönster.</span><span class="sxs-lookup"><span data-stu-id="98053-229">It is important to note that the `$Matches` hashtable will only contain the first occurrence of any matching pattern.</span></span>

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> <span data-ttu-id="98053-230">`0`Nyckeln är ett **heltal**.</span><span class="sxs-lookup"><span data-stu-id="98053-230">The `0` key is an **Integer**.</span></span> <span data-ttu-id="98053-231">Du kan använda valfri **hash** -Metod för att komma åt värdet som lagras.</span><span class="sxs-lookup"><span data-stu-id="98053-231">You can use any **Hashtable** method to access the value stored.</span></span>
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

<span data-ttu-id="98053-232">`-notmatch`Operatorn fyller den `$Matches` automatiska variabeln när indatatypen är skalär och resultatet är falskt, det vill säga när en matchning upptäcks.</span><span class="sxs-lookup"><span data-stu-id="98053-232">The `-notmatch` operator populates the `$Matches` automatic variable when the input is scalar and the result is False, that it, when it detects a match.</span></span>

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

### <a name="-notmatch"></a><span data-ttu-id="98053-233">-notmatch</span><span class="sxs-lookup"><span data-stu-id="98053-233">-notmatch</span></span>

<span data-ttu-id="98053-234">Beskrivning: matchar inte en sträng.</span><span class="sxs-lookup"><span data-stu-id="98053-234">Description: Does not match a string.</span></span> <span data-ttu-id="98053-235">Använder reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="98053-235">Uses regular expressions.</span></span> <span data-ttu-id="98053-236">När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.</span><span class="sxs-lookup"><span data-stu-id="98053-236">When the input is scalar, it populates the `$Matches` automatic variable.</span></span>

<span data-ttu-id="98053-237">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-237">Example:</span></span>

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

## <a name="containment-operators"></a><span data-ttu-id="98053-238">Inne slutnings operatorer</span><span class="sxs-lookup"><span data-stu-id="98053-238">Containment operators</span></span>

<span data-ttu-id="98053-239">Inne slutnings operatorerna ( `-contains` och `-notcontains` ) liknar likhets operatorerna.</span><span class="sxs-lookup"><span data-stu-id="98053-239">The containment operators (`-contains` and `-notcontains`) are similar to the equality operators.</span></span> <span data-ttu-id="98053-240">Däremot returnerar inne slutnings operatorer alltid ett booleskt värde, även om indatatypen är en samling.</span><span class="sxs-lookup"><span data-stu-id="98053-240">However, the containment operators always return a Boolean value, even when the input is a collection.</span></span>

<span data-ttu-id="98053-241">Till skillnad från likhets operatorerna returnerar inne slutnings operatorerna ett värde så fort de identifierar den första matchningen.</span><span class="sxs-lookup"><span data-stu-id="98053-241">Also, unlike the equality operators, the containment operators return a value as soon as they detect the first match.</span></span> <span data-ttu-id="98053-242">Likhets operatorerna utvärderar alla indatatyper och returnerar sedan alla träffar i samlingen.</span><span class="sxs-lookup"><span data-stu-id="98053-242">The equality operators evaluate all input and then return all the matches in the collection.</span></span>

### <a name="-contains"></a><span data-ttu-id="98053-243">– innehåller</span><span class="sxs-lookup"><span data-stu-id="98053-243">-contains</span></span>

<span data-ttu-id="98053-244">Beskrivning: inne slutnings operator.</span><span class="sxs-lookup"><span data-stu-id="98053-244">Description: Containment operator.</span></span> <span data-ttu-id="98053-245">Anger om en samling med referens värden innehåller ett enda testvärde.</span><span class="sxs-lookup"><span data-stu-id="98053-245">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="98053-246">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-246">Always returns a Boolean value.</span></span> <span data-ttu-id="98053-247">Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.</span><span class="sxs-lookup"><span data-stu-id="98053-247">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="98053-248">När testvärdet är en samling använder operatorn referens likhet.</span><span class="sxs-lookup"><span data-stu-id="98053-248">When the test value is a collection, the Contains operator uses reference equality.</span></span> <span data-ttu-id="98053-249">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="98053-249">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="98053-250">I en mycket stor samling `-contains` returnerar operatorn snabbare resultat än operatorn lika med.</span><span class="sxs-lookup"><span data-stu-id="98053-250">In a very large collection, the `-contains` operator returns results quicker than the equal to operator.</span></span>

<span data-ttu-id="98053-251">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-251">Syntax:</span></span>

`<Reference-values> -contains <Test-value>`

<span data-ttu-id="98053-252">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-252">Examples:</span></span>

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

### <a name="-notcontains"></a><span data-ttu-id="98053-253">-notcontains</span><span class="sxs-lookup"><span data-stu-id="98053-253">-notcontains</span></span>

<span data-ttu-id="98053-254">Beskrivning: inne slutnings operator.</span><span class="sxs-lookup"><span data-stu-id="98053-254">Description: Containment operator.</span></span> <span data-ttu-id="98053-255">Anger om en samling med referens värden innehåller ett enda testvärde.</span><span class="sxs-lookup"><span data-stu-id="98053-255">Tells whether a collection of reference values includes a single test value.</span></span> <span data-ttu-id="98053-256">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-256">Always returns a Boolean value.</span></span> <span data-ttu-id="98053-257">Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.</span><span class="sxs-lookup"><span data-stu-id="98053-257">Returns TRUE when the test value is not an exact matches for at least one of the reference values.</span></span>

<span data-ttu-id="98053-258">När testvärdet är en samling använder NotContains-operatorn referens likhet.</span><span class="sxs-lookup"><span data-stu-id="98053-258">When the test value is a collection, the NotContains operator uses reference equality.</span></span>

<span data-ttu-id="98053-259">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-259">Syntax:</span></span>

`<Reference-values> -notcontains <Test-value>`

<span data-ttu-id="98053-260">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-260">Examples:</span></span>

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

### <a name="-in"></a><span data-ttu-id="98053-261">– in</span><span class="sxs-lookup"><span data-stu-id="98053-261">-in</span></span>

<span data-ttu-id="98053-262">Beskrivning: i-Operator.</span><span class="sxs-lookup"><span data-stu-id="98053-262">Description: In operator.</span></span> <span data-ttu-id="98053-263">Anger om ett testvärde visas i en samling med referens värden.</span><span class="sxs-lookup"><span data-stu-id="98053-263">Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="98053-264">Returnera alltid som booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-264">Always return as Boolean value.</span></span> <span data-ttu-id="98053-265">Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.</span><span class="sxs-lookup"><span data-stu-id="98053-265">Returns TRUE only when the test value exactly matches at least one of the reference values.</span></span>

<span data-ttu-id="98053-266">När testvärdet är en samling använder operatorn i referens likhet.</span><span class="sxs-lookup"><span data-stu-id="98053-266">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="98053-267">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="98053-267">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="98053-268">`-in`Operatorn introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="98053-268">The `-in` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="98053-269">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-269">Syntax:</span></span>

`<Test-value> -in <Reference-values>`

<span data-ttu-id="98053-270">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-270">Examples:</span></span>

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

### <a name="-notin"></a><span data-ttu-id="98053-271">-notin</span><span class="sxs-lookup"><span data-stu-id="98053-271">-notin</span></span>

<span data-ttu-id="98053-272">Beskrivning: anger om ett testvärde visas i en samling med referens värden.</span><span class="sxs-lookup"><span data-stu-id="98053-272">Description: Tells whether a test value appears in a collection of reference values.</span></span> <span data-ttu-id="98053-273">Returnerar alltid ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="98053-273">Always returns a Boolean value.</span></span> <span data-ttu-id="98053-274">Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.</span><span class="sxs-lookup"><span data-stu-id="98053-274">Returns TRUE when the test value is not an exact match for at least one of the reference values.</span></span>

<span data-ttu-id="98053-275">När testvärdet är en samling använder operatorn i referens likhet.</span><span class="sxs-lookup"><span data-stu-id="98053-275">When the test value is a collection, the In operator uses reference equality.</span></span>
<span data-ttu-id="98053-276">Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.</span><span class="sxs-lookup"><span data-stu-id="98053-276">It returns TRUE only when one of the reference values is the same instance of the test value object.</span></span>

<span data-ttu-id="98053-277">`-notin`Operatorn introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="98053-277">The `-notin` operator was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="98053-278">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-278">Syntax:</span></span>

`<Test-value> -notin <Reference-values>`

<span data-ttu-id="98053-279">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-279">Examples:</span></span>

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

## <a name="replacement-operator"></a><span data-ttu-id="98053-280">Ersättnings operatör</span><span class="sxs-lookup"><span data-stu-id="98053-280">Replacement Operator</span></span>

<span data-ttu-id="98053-281">`-replace`Operatorn har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-281">The `-replace` operator has the following syntax:</span></span>

`<input> -replace <original>, <substitute>`

<span data-ttu-id="98053-282">`<original>`Plats hållaren är ett reguljärt uttryck som matchar de tecken som ska ersättas.</span><span class="sxs-lookup"><span data-stu-id="98053-282">The `<original>` placeholder is a regular expression matching the characters to be replaced.</span></span> <span data-ttu-id="98053-283">`<substitute>`Plats hållaren är en tecken sträng som ersätter dem.</span><span class="sxs-lookup"><span data-stu-id="98053-283">The `<substitute>` placeholder is a literal string that replaces them.</span></span>

<span data-ttu-id="98053-284">Operatorn ersätter hela eller delar av ett värde med det angivna värdet med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="98053-284">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="98053-285">Du kan använda operatorn för många administrativa uppgifter, till exempel att byta namn på filer.</span><span class="sxs-lookup"><span data-stu-id="98053-285">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="98053-286">Följande kommando ändrar till exempel fil namns tilläggen för alla `.txt` filer till `.log` :</span><span class="sxs-lookup"><span data-stu-id="98053-286">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

### <a name="case-sensitive-matches"></a><span data-ttu-id="98053-287">Skift läges känsliga matchningar</span><span class="sxs-lookup"><span data-stu-id="98053-287">Case-sensitive matches</span></span>

<span data-ttu-id="98053-288">Som standard `-replace` är operatorn Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="98053-288">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="98053-289">Använd för att göra det Skift läges känsligt `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="98053-289">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="98053-290">Använd om du vill göra det uttryckligen Skift läges okänsligt `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="98053-290">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="98053-291">Överväg följande exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-291">Consider the following examples:</span></span>

```powershell
PS> "book" -replace "B", "C"
Cook
```

```powershell
PS> "book" -ireplace "B", "C"
Cook
```

```powershell
PS> "book" -creplace "B", "C"
book
```

### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="98053-292">Ersättningar i reguljära uttryck</span><span class="sxs-lookup"><span data-stu-id="98053-292">Substitutions in regular expressions</span></span>

<span data-ttu-id="98053-293">Det går också att använda reguljära uttryck för att dynamiskt ersätta text med hjälp av insamlings grupper och ersättningar.</span><span class="sxs-lookup"><span data-stu-id="98053-293">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="98053-294">Det går att referera till infångnings grupper i `<substitute>` strängen med dollar tecknet ( `$` ) före grupp-ID: n.</span><span class="sxs-lookup"><span data-stu-id="98053-294">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="98053-295">Det går att referera till infångnings grupper med hjälp av **nummer** eller **namn**</span><span class="sxs-lookup"><span data-stu-id="98053-295">Capture groups can be referenced by **Number** or **Name**</span></span>

- <span data-ttu-id="98053-296">Per **nummer** – fångar grupper numreras från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="98053-296">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  PS> "John D. Smith" -replace "(\w+) (\w+)\. (\w+)", '$1.$2.$3@contoso.com'
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="98053-297">Efter **namn** -hämtade grupper kan också refereras till med hjälp av namn.</span><span class="sxs-lookup"><span data-stu-id="98053-297">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  PS> "CONTOSO\Administrator" -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  FABRIKAM\Administrator
  ```

> [!WARNING]
> <span data-ttu-id="98053-298">Eftersom det `$` används i sträng expansion måste du använda literala strängar eller Escape- `$` tecken.</span><span class="sxs-lookup"><span data-stu-id="98053-298">Since the `$` character is used in string expansion, you will must use literal strings or escape the `$` character.</span></span>
>
> ```powershell
> PS> 'Hello World' -replace '(\w+) \w+', "`$1 Universe"
> Hello Universe
> ```
>
> <span data-ttu-id="98053-299">Eftersom ett `$` tecken används i ersättningen måste du dessutom undanta eventuella instanser i strängen.</span><span class="sxs-lookup"><span data-stu-id="98053-299">Additionally, since the `$` character is used in substitution, you must escape any instances in your string.</span></span>
>
> ```powershell
> PS> '5.72' -replace '(.+)', '$$$1'
> $5.72
> ```

<span data-ttu-id="98053-300">Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md) och [ersättningar i reguljära uttryck](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span><span class="sxs-lookup"><span data-stu-id="98053-300">To learn more see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions)</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="98053-301">Ersätta i en samling</span><span class="sxs-lookup"><span data-stu-id="98053-301">Substituting in a collection</span></span>

<span data-ttu-id="98053-302">När `<input>` `-replace` operatorn till är en samling, tillämpar PowerShell ersättningen på alla värden i samlingen.</span><span class="sxs-lookup"><span data-stu-id="98053-302">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="98053-303">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-303">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="scriptblock-substitutions"></a><span data-ttu-id="98053-304">Script block ersättningar</span><span class="sxs-lookup"><span data-stu-id="98053-304">ScriptBlock substitutions</span></span>

<span data-ttu-id="98053-305">Från och med PowerShell 6 kan du använda ett **script block** -argument för _ersättnings_ texten.</span><span class="sxs-lookup"><span data-stu-id="98053-305">Beginning in PowerShell 6, you can use a **ScriptBlock** argument for the _Substitution_ text.</span></span> <span data-ttu-id="98053-306">**Script block** körs för varje matchning som hittades i _Indatasträngen_ .</span><span class="sxs-lookup"><span data-stu-id="98053-306">The **ScriptBlock** will execute for each match found in the _input_ string.</span></span>

<span data-ttu-id="98053-307">I **script block** använder du den `$_` automatiska variabeln för att referera till det aktuella **systemet. text. RegularExpressions. match** -objektet.</span><span class="sxs-lookup"><span data-stu-id="98053-307">Within the **ScriptBlock**, use the `$_` automatic variable to refer to the current **System.Text.RegularExpressions.Match** object.</span></span> <span data-ttu-id="98053-308">**Match** -objektet ger dig åtkomst till den aktuella inmatade texten som ersätts samt annan användbar information.</span><span class="sxs-lookup"><span data-stu-id="98053-308">The **Match** object gives you access to the current input text being replaced, as well as other useful information.</span></span>

<span data-ttu-id="98053-309">Det här exemplet ersätter varje sekvens med tre decimaler med motsvarande tecken.</span><span class="sxs-lookup"><span data-stu-id="98053-309">This example replaces each sequence of three decimals with the character equivalent.</span></span> <span data-ttu-id="98053-310">**Script block** körs för varje uppsättning av tre decimaler som måste ersättas.</span><span class="sxs-lookup"><span data-stu-id="98053-310">The **ScriptBlock** is run for each set of three decimals that needs to be replaced.</span></span>

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

## <a name="type-comparison"></a><span data-ttu-id="98053-311">Typ jämförelse</span><span class="sxs-lookup"><span data-stu-id="98053-311">Type comparison</span></span>

<span data-ttu-id="98053-312">Typ jämförelse operatorer ( `-is` och `-isnot` ) används för att avgöra om ett objekt är en speciell typ.</span><span class="sxs-lookup"><span data-stu-id="98053-312">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

### <a name="-is"></a><span data-ttu-id="98053-313">-är</span><span class="sxs-lookup"><span data-stu-id="98053-313">-is</span></span>

<span data-ttu-id="98053-314">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-314">Syntax:</span></span>

`<object> -is <type reference>`

<span data-ttu-id="98053-315">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-315">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

### <a name="-isnot"></a><span data-ttu-id="98053-316">– IsNot</span><span class="sxs-lookup"><span data-stu-id="98053-316">-isnot</span></span>

<span data-ttu-id="98053-317">Syntax:</span><span class="sxs-lookup"><span data-stu-id="98053-317">Syntax:</span></span>

`<object> -isnot <type reference>`

<span data-ttu-id="98053-318">Exempel:</span><span class="sxs-lookup"><span data-stu-id="98053-318">Example:</span></span>

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a><span data-ttu-id="98053-319">Se även</span><span class="sxs-lookup"><span data-stu-id="98053-319">See also</span></span>

- [<span data-ttu-id="98053-320">about_Operators</span><span class="sxs-lookup"><span data-stu-id="98053-320">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="98053-321">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="98053-321">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="98053-322">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="98053-322">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="98053-323">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="98053-323">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="98053-324">-Objekt</span><span class="sxs-lookup"><span data-stu-id="98053-324">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="98053-325">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="98053-325">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)
