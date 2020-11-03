---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273243"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="3170d-103">Om numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="3170d-103">About numeric literals</span></span>

<span data-ttu-id="3170d-104">Det finns två typer av numeriska litteraler: heltal och verklig.</span><span class="sxs-lookup"><span data-stu-id="3170d-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="3170d-105">Båda kan ha Type-och multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="3170d-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="3170d-106">Heltals strängar</span><span class="sxs-lookup"><span data-stu-id="3170d-106">Integer literals</span></span>

<span data-ttu-id="3170d-107">Heltals-litteraler kan skrivas i decimal-eller hexadecimal notation.</span><span class="sxs-lookup"><span data-stu-id="3170d-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="3170d-108">Hexadecimala litteraler föregås av `0x` för att skilja dem från decimal tal.</span><span class="sxs-lookup"><span data-stu-id="3170d-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="3170d-109">Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="3170d-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="3170d-110">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="3170d-110">Suffix</span></span> |       <span data-ttu-id="3170d-111">Innebörd</span><span class="sxs-lookup"><span data-stu-id="3170d-111">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="3170d-112">l</span><span class="sxs-lookup"><span data-stu-id="3170d-112">l</span></span>      | <span data-ttu-id="3170d-113">lång datatyp</span><span class="sxs-lookup"><span data-stu-id="3170d-113">long data type</span></span>      |
| <span data-ttu-id="3170d-114">kunskap</span><span class="sxs-lookup"><span data-stu-id="3170d-114">kb</span></span>     | <span data-ttu-id="3170d-115">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-115">kilobyte multiplier</span></span> |
| <span data-ttu-id="3170d-116">MB</span><span class="sxs-lookup"><span data-stu-id="3170d-116">mb</span></span>     | <span data-ttu-id="3170d-117">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-117">megabyte multiplier</span></span> |
| <span data-ttu-id="3170d-118">minst</span><span class="sxs-lookup"><span data-stu-id="3170d-118">gb</span></span>     | <span data-ttu-id="3170d-119">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-119">gigabyte multiplier</span></span> |
| <span data-ttu-id="3170d-120">TB</span><span class="sxs-lookup"><span data-stu-id="3170d-120">tb</span></span>     | <span data-ttu-id="3170d-121">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-121">terabyte multiplier</span></span> |
| <span data-ttu-id="3170d-122">PT</span><span class="sxs-lookup"><span data-stu-id="3170d-122">pb</span></span>     | <span data-ttu-id="3170d-123">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-123">petabyte multiplier</span></span> |

<span data-ttu-id="3170d-124">Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.</span><span class="sxs-lookup"><span data-stu-id="3170d-124">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="3170d-125">För en heltals sträng utan typ suffix:</span><span class="sxs-lookup"><span data-stu-id="3170d-125">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="3170d-126">Om värdet kan representeras av typ `[int]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-126">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="3170d-127">Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-127">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="3170d-128">Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-128">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="3170d-129">Annars representeras det av typen `[double]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-129">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="3170d-130">För en heltals sträng med ett Type-suffix:</span><span class="sxs-lookup"><span data-stu-id="3170d-130">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="3170d-131">Om Type-suffixet är `u` och värdet kan representeras av typ, `[int]` är dess typ `[int]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-131">If the type suffix is `u` and the value can be represented by type `[int]` then its type is `[int]`.</span></span>
- <span data-ttu-id="3170d-132">Om Type-suffixet är `u` och värdet kan representeras av typ, `[long]` är dess typ `[long]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-132">If the type suffix is `u` and the value can be represented by type `[long]` then its type is `[long]`.</span></span>
- <span data-ttu-id="3170d-133">Om dess värde kan representeras av en typ som anges, är det dess typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-133">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="3170d-134">Annars är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="3170d-134">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="3170d-135">Riktiga litteraler</span><span class="sxs-lookup"><span data-stu-id="3170d-135">Real literals</span></span>

<span data-ttu-id="3170d-136">Det går bara att skriva reella litteraler i decimal format.</span><span class="sxs-lookup"><span data-stu-id="3170d-136">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="3170d-137">Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.</span><span class="sxs-lookup"><span data-stu-id="3170d-137">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="3170d-138">Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten.</span><span class="sxs-lookup"><span data-stu-id="3170d-138">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="3170d-139">Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.</span><span class="sxs-lookup"><span data-stu-id="3170d-139">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="3170d-140">Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="3170d-140">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="3170d-141">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="3170d-141">Suffix</span></span> |       <span data-ttu-id="3170d-142">Innebörd</span><span class="sxs-lookup"><span data-stu-id="3170d-142">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="3170d-143">d</span><span class="sxs-lookup"><span data-stu-id="3170d-143">d</span></span>      | <span data-ttu-id="3170d-144">decimal data typ</span><span class="sxs-lookup"><span data-stu-id="3170d-144">decimal data type</span></span>   |
| <span data-ttu-id="3170d-145">kunskap</span><span class="sxs-lookup"><span data-stu-id="3170d-145">kb</span></span>     | <span data-ttu-id="3170d-146">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-146">kilobyte multiplier</span></span> |
| <span data-ttu-id="3170d-147">MB</span><span class="sxs-lookup"><span data-stu-id="3170d-147">mb</span></span>     | <span data-ttu-id="3170d-148">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-148">megabyte multiplier</span></span> |
| <span data-ttu-id="3170d-149">minst</span><span class="sxs-lookup"><span data-stu-id="3170d-149">gb</span></span>     | <span data-ttu-id="3170d-150">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-150">gigabyte multiplier</span></span> |
| <span data-ttu-id="3170d-151">TB</span><span class="sxs-lookup"><span data-stu-id="3170d-151">tb</span></span>     | <span data-ttu-id="3170d-152">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-152">terabyte multiplier</span></span> |
| <span data-ttu-id="3170d-153">PT</span><span class="sxs-lookup"><span data-stu-id="3170d-153">pb</span></span>     | <span data-ttu-id="3170d-154">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="3170d-154">petabyte multiplier</span></span> |

<span data-ttu-id="3170d-155">Det finns två typer av verklig literal: dubbel och decimal.</span><span class="sxs-lookup"><span data-stu-id="3170d-155">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="3170d-156">Dessa anges av frånvaron eller närvaron av typen decimal-typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-156">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="3170d-157">PowerShell har inte stöd för en litteral representation av ett `[float]` värde.</span><span class="sxs-lookup"><span data-stu-id="3170d-157">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="3170d-158">En dubbel verklig literal har en typ `[double]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-158">A double real literal has type `[double]`.</span></span> <span data-ttu-id="3170d-159">En riktig decimal literal har en typ `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-159">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="3170d-160">Efterföljande nollor i bråk delen av en decimal verklig literal är signifikanta.</span><span class="sxs-lookup"><span data-stu-id="3170d-160">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="3170d-161">Om värdet för exponentens siffror i en `[double]` riktig literal är mindre än det lägsta stödda värdet är värdet för den `[double]` verkliga literalen 0.</span><span class="sxs-lookup"><span data-stu-id="3170d-161">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="3170d-162">Om värdet för exponentens siffror i en `[decimal]` riktig literal är mindre än det lägsta stödda värdet är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="3170d-162">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="3170d-163">Om värdet för exponentens siffror i en `[double]` eller `[decimal]` reella litteraler är större än det högsta tillåtna värdet, är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="3170d-163">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="3170d-164">Syntaxen tillåter en dubbel verklig literal att ha ett suffix med lång typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-164">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="3170d-165">PowerShell behandlar det här fallet som en heltals sträng vars värde representeras av Type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="3170d-165">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="3170d-166">Den här funktionen har behållits för bakåtkompatibilitet med tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3170d-166">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="3170d-167">Programmerare rekommenderas dock inte att använda heltals strängar i det här formuläret eftersom de lätt kan dölja litteralens faktiska värde.</span><span class="sxs-lookup"><span data-stu-id="3170d-167">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="3170d-168">Har t. ex. `1.2L` värdet 1, `1.2345e1L` värdet 12 och `1.2345e-5L` värdet 0, ingen av som är direkt uppenbara.</span><span class="sxs-lookup"><span data-stu-id="3170d-168">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="3170d-169">Numeriska multiplikatorer</span><span class="sxs-lookup"><span data-stu-id="3170d-169">Numeric multipliers</span></span>

<span data-ttu-id="3170d-170">För enkelhetens skull kan heltal och reella litteraler innehålla en numerisk multiplikator som visar en uppsättning vanliga befogenheter på 2.</span><span class="sxs-lookup"><span data-stu-id="3170d-170">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="3170d-171">Den numeriska multiplikatorn kan skrivas i valfri kombination av versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="3170d-171">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="3170d-172">Utkombinations-suffixen kan användas i kombination med `u` , `ul` och `l` skriver suffix.</span><span class="sxs-lookup"><span data-stu-id="3170d-172">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="3170d-173">Multiplikator exempel</span><span class="sxs-lookup"><span data-stu-id="3170d-173">Multiplier examples</span></span>

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a><span data-ttu-id="3170d-174">Numeriska typ acceleratorer</span><span class="sxs-lookup"><span data-stu-id="3170d-174">Numeric type accelerators</span></span>

<span data-ttu-id="3170d-175">PowerShell stöder följande typ acceleratorer:</span><span class="sxs-lookup"><span data-stu-id="3170d-175">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="3170d-176">Gas</span><span class="sxs-lookup"><span data-stu-id="3170d-176">Accelerator</span></span> |         <span data-ttu-id="3170d-177">Anteckning</span><span class="sxs-lookup"><span data-stu-id="3170d-177">Note</span></span>         |           <span data-ttu-id="3170d-178">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3170d-178">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="3170d-179">Byte (ej signerat)</span><span class="sxs-lookup"><span data-stu-id="3170d-179">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="3170d-180">Byte (signerat)</span><span class="sxs-lookup"><span data-stu-id="3170d-180">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="3170d-181">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="3170d-181">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="3170d-182">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="3170d-182">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="3170d-183">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="3170d-183">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="3170d-184">alias för `[int32]`</span><span class="sxs-lookup"><span data-stu-id="3170d-184">alias for `[int32]`</span></span>  | <span data-ttu-id="3170d-185">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="3170d-185">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="3170d-186">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="3170d-186">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="3170d-187">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="3170d-187">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="3170d-188">alias för `[int64]`</span><span class="sxs-lookup"><span data-stu-id="3170d-188">alias for `[int64]`</span></span>  | <span data-ttu-id="3170d-189">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="3170d-189">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="3170d-190">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="3170d-190">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="3170d-191">Se [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="3170d-191">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="3170d-192">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="3170d-192">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="3170d-193">alias för `[single]`</span><span class="sxs-lookup"><span data-stu-id="3170d-193">alias for `[single]`</span></span> | <span data-ttu-id="3170d-194">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="3170d-194">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="3170d-195">Dubbel precision, flytande punkt</span><span class="sxs-lookup"><span data-stu-id="3170d-195">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="3170d-196">128-bitars svävande punkt</span><span class="sxs-lookup"><span data-stu-id="3170d-196">128-bit floating point</span></span>           |

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="3170d-197">Arbeta med andra numeriska typer</span><span class="sxs-lookup"><span data-stu-id="3170d-197">Working with other numeric types</span></span>

<span data-ttu-id="3170d-198">Om du vill arbeta med andra numeriska typer måste du använda typ acceleratorer, som inte utan några problem.</span><span class="sxs-lookup"><span data-stu-id="3170d-198">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="3170d-199">Till exempel tolkas alltid höga heltals värden som dubbelt innan de skickas till någon annan typ.</span><span class="sxs-lookup"><span data-stu-id="3170d-199">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="3170d-200">Värdet parsas som en dubbel första och förlorar precisionen i de högre intervallen.</span><span class="sxs-lookup"><span data-stu-id="3170d-200">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="3170d-201">Undvik det här problemet genom att ange värden som strängar och sedan konvertera dem:</span><span class="sxs-lookup"><span data-stu-id="3170d-201">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="3170d-202">Exempel</span><span class="sxs-lookup"><span data-stu-id="3170d-202">Examples</span></span>

<span data-ttu-id="3170d-203">Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:</span><span class="sxs-lookup"><span data-stu-id="3170d-203">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="3170d-204">Antal</span><span class="sxs-lookup"><span data-stu-id="3170d-204">Number</span></span>  |  <span data-ttu-id="3170d-205">Typ</span><span class="sxs-lookup"><span data-stu-id="3170d-205">Type</span></span>   |    <span data-ttu-id="3170d-206">Värde</span><span class="sxs-lookup"><span data-stu-id="3170d-206">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="3170d-207">100</span><span class="sxs-lookup"><span data-stu-id="3170d-207">100</span></span> | <span data-ttu-id="3170d-208">Int32</span><span class="sxs-lookup"><span data-stu-id="3170d-208">Int32</span></span>   |          <span data-ttu-id="3170d-209">100</span><span class="sxs-lookup"><span data-stu-id="3170d-209">100</span></span> |
|     <span data-ttu-id="3170d-210">100D</span><span class="sxs-lookup"><span data-stu-id="3170d-210">100D</span></span> | <span data-ttu-id="3170d-211">Decimal</span><span class="sxs-lookup"><span data-stu-id="3170d-211">Decimal</span></span> |          <span data-ttu-id="3170d-212">100</span><span class="sxs-lookup"><span data-stu-id="3170d-212">100</span></span> |
|     <span data-ttu-id="3170d-213">100l</span><span class="sxs-lookup"><span data-stu-id="3170d-213">100l</span></span> | <span data-ttu-id="3170d-214">Int64</span><span class="sxs-lookup"><span data-stu-id="3170d-214">Int64</span></span>   |          <span data-ttu-id="3170d-215">100</span><span class="sxs-lookup"><span data-stu-id="3170d-215">100</span></span> |
|      <span data-ttu-id="3170d-216">1e2</span><span class="sxs-lookup"><span data-stu-id="3170d-216">1e2</span></span> | <span data-ttu-id="3170d-217">Double</span><span class="sxs-lookup"><span data-stu-id="3170d-217">Double</span></span>  |          <span data-ttu-id="3170d-218">100</span><span class="sxs-lookup"><span data-stu-id="3170d-218">100</span></span> |
|     <span data-ttu-id="3170d-219">1. E2</span><span class="sxs-lookup"><span data-stu-id="3170d-219">1.e2</span></span> | <span data-ttu-id="3170d-220">Double</span><span class="sxs-lookup"><span data-stu-id="3170d-220">Double</span></span>  |          <span data-ttu-id="3170d-221">100</span><span class="sxs-lookup"><span data-stu-id="3170d-221">100</span></span> |
|    <span data-ttu-id="3170d-222">0x1e2</span><span class="sxs-lookup"><span data-stu-id="3170d-222">0x1e2</span></span> | <span data-ttu-id="3170d-223">Int32</span><span class="sxs-lookup"><span data-stu-id="3170d-223">Int32</span></span>   |          <span data-ttu-id="3170d-224">482</span><span class="sxs-lookup"><span data-stu-id="3170d-224">482</span></span> |
|   <span data-ttu-id="3170d-225">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="3170d-225">0x1e2L</span></span> | <span data-ttu-id="3170d-226">Int64</span><span class="sxs-lookup"><span data-stu-id="3170d-226">Int64</span></span>   |          <span data-ttu-id="3170d-227">482</span><span class="sxs-lookup"><span data-stu-id="3170d-227">482</span></span> |
|   <span data-ttu-id="3170d-228">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="3170d-228">0x1e2D</span></span> | <span data-ttu-id="3170d-229">Int32</span><span class="sxs-lookup"><span data-stu-id="3170d-229">Int32</span></span>   |         <span data-ttu-id="3170d-230">7725</span><span class="sxs-lookup"><span data-stu-id="3170d-230">7725</span></span> |
|     <span data-ttu-id="3170d-231">482D</span><span class="sxs-lookup"><span data-stu-id="3170d-231">482D</span></span> | <span data-ttu-id="3170d-232">Decimal</span><span class="sxs-lookup"><span data-stu-id="3170d-232">Decimal</span></span> |          <span data-ttu-id="3170d-233">482</span><span class="sxs-lookup"><span data-stu-id="3170d-233">482</span></span> |
|    <span data-ttu-id="3170d-234">482gb</span><span class="sxs-lookup"><span data-stu-id="3170d-234">482gb</span></span> | <span data-ttu-id="3170d-235">Int64</span><span class="sxs-lookup"><span data-stu-id="3170d-235">Int64</span></span>   | <span data-ttu-id="3170d-236">517543559168</span><span class="sxs-lookup"><span data-stu-id="3170d-236">517543559168</span></span> |
| <span data-ttu-id="3170d-237">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="3170d-237">0x1e2lgb</span></span> | <span data-ttu-id="3170d-238">Int64</span><span class="sxs-lookup"><span data-stu-id="3170d-238">Int64</span></span>   | <span data-ttu-id="3170d-239">517543559168</span><span class="sxs-lookup"><span data-stu-id="3170d-239">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="3170d-240">Kommandon som ser ut som numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="3170d-240">Commands that look like numeric literals</span></span>

<span data-ttu-id="3170d-241">Alla kommandon som ser ut som en numerisk litteral måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal av den associerade typen.</span><span class="sxs-lookup"><span data-stu-id="3170d-241">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="3170d-242">Åtkomst egenskaper och metoder för numeriska objekt</span><span class="sxs-lookup"><span data-stu-id="3170d-242">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="3170d-243">Om du vill ha åtkomst till en medlem med en numerisk literal, finns det fall när du behöver omsluta literalen inom parentes.</span><span class="sxs-lookup"><span data-stu-id="3170d-243">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="3170d-244">Literalen har inget decimal tecken</span><span class="sxs-lookup"><span data-stu-id="3170d-244">The literal does not have a decimal point</span></span>
- <span data-ttu-id="3170d-245">Literalen saknar siffror efter decimal tecknet</span><span class="sxs-lookup"><span data-stu-id="3170d-245">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="3170d-246">Literalen har inget suffix</span><span class="sxs-lookup"><span data-stu-id="3170d-246">The literal does not have a suffix</span></span>

<span data-ttu-id="3170d-247">Till exempel Miss lyckas följande exempel:</span><span class="sxs-lookup"><span data-stu-id="3170d-247">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="3170d-248">Följande exempel fungerar:</span><span class="sxs-lookup"><span data-stu-id="3170d-248">The following examples work:</span></span>

```
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="3170d-249">De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.</span><span class="sxs-lookup"><span data-stu-id="3170d-249">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
