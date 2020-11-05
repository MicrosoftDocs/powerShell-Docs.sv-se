---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: 19ed71c2571a6cd343adf622a8cf71d6e5589aff
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354991"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="6f494-103">Om numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-103">About numeric literals</span></span>

<span data-ttu-id="6f494-104">Det finns två typer av numeriska litteraler: heltal och verklig.</span><span class="sxs-lookup"><span data-stu-id="6f494-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="6f494-105">Båda kan ha Type-och multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="6f494-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="6f494-106">Heltals strängar</span><span class="sxs-lookup"><span data-stu-id="6f494-106">Integer literals</span></span>

<span data-ttu-id="6f494-107">Heltals-litteraler kan skrivas i decimal-, hexadecimal-eller binär notation.</span><span class="sxs-lookup"><span data-stu-id="6f494-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="6f494-108">Hexadecimala litteraler föregås av `0x` och binära litteraler föregås av `0b` för att skilja dem från decimal tal.</span><span class="sxs-lookup"><span data-stu-id="6f494-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="6f494-109">Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="6f494-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="6f494-110">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="6f494-110">Suffix</span></span> |            <span data-ttu-id="6f494-111">Innebörd</span><span class="sxs-lookup"><span data-stu-id="6f494-111">Meaning</span></span>             |          <span data-ttu-id="6f494-112">Anteckning</span><span class="sxs-lookup"><span data-stu-id="6f494-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="6f494-113">y</span><span class="sxs-lookup"><span data-stu-id="6f494-113">y</span></span>      | <span data-ttu-id="6f494-114">datatyp för signerad byte</span><span class="sxs-lookup"><span data-stu-id="6f494-114">signed byte data type</span></span>          | <span data-ttu-id="6f494-115">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-116">uy</span><span class="sxs-lookup"><span data-stu-id="6f494-116">uy</span></span>     | <span data-ttu-id="6f494-117">datatyp för osignerad byte</span><span class="sxs-lookup"><span data-stu-id="6f494-117">unsigned byte data type</span></span>        | <span data-ttu-id="6f494-118">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-119">s</span><span class="sxs-lookup"><span data-stu-id="6f494-119">s</span></span>      | <span data-ttu-id="6f494-120">kort datatyp</span><span class="sxs-lookup"><span data-stu-id="6f494-120">short data type</span></span>                | <span data-ttu-id="6f494-121">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-122">USA</span><span class="sxs-lookup"><span data-stu-id="6f494-122">us</span></span>     | <span data-ttu-id="6f494-123">osignerad kort data typ</span><span class="sxs-lookup"><span data-stu-id="6f494-123">unsigned short data type</span></span>       | <span data-ttu-id="6f494-124">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-125">l</span><span class="sxs-lookup"><span data-stu-id="6f494-125">l</span></span>      | <span data-ttu-id="6f494-126">lång datatyp</span><span class="sxs-lookup"><span data-stu-id="6f494-126">long data type</span></span>                 |                         |
| <span data-ttu-id="6f494-127">ä</span><span class="sxs-lookup"><span data-stu-id="6f494-127">u</span></span>      | <span data-ttu-id="6f494-128">osignerad int-eller Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="6f494-128">unsigned int or long data type</span></span> | <span data-ttu-id="6f494-129">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-130">UL</span><span class="sxs-lookup"><span data-stu-id="6f494-130">ul</span></span>     | <span data-ttu-id="6f494-131">osignerad Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="6f494-131">unsigned long data type</span></span>        | <span data-ttu-id="6f494-132">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="6f494-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="6f494-133">n</span><span class="sxs-lookup"><span data-stu-id="6f494-133">n</span></span>      | <span data-ttu-id="6f494-134">Data typen BigInteger</span><span class="sxs-lookup"><span data-stu-id="6f494-134">BigInteger data type</span></span>           | <span data-ttu-id="6f494-135">Tillagt i PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="6f494-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="6f494-136">kunskap</span><span class="sxs-lookup"><span data-stu-id="6f494-136">kb</span></span>     | <span data-ttu-id="6f494-137">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="6f494-138">MB</span><span class="sxs-lookup"><span data-stu-id="6f494-138">mb</span></span>     | <span data-ttu-id="6f494-139">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="6f494-140">minst</span><span class="sxs-lookup"><span data-stu-id="6f494-140">gb</span></span>     | <span data-ttu-id="6f494-141">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="6f494-142">TB</span><span class="sxs-lookup"><span data-stu-id="6f494-142">tb</span></span>     | <span data-ttu-id="6f494-143">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="6f494-144">PT</span><span class="sxs-lookup"><span data-stu-id="6f494-144">pb</span></span>     | <span data-ttu-id="6f494-145">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="6f494-146">Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.</span><span class="sxs-lookup"><span data-stu-id="6f494-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="6f494-147">För en heltals sträng utan typ suffix:</span><span class="sxs-lookup"><span data-stu-id="6f494-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="6f494-148">Om värdet kan representeras av typ `[int]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="6f494-149">Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="6f494-150">Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="6f494-151">Annars representeras det av typen `[double]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="6f494-152">För en heltals sträng med ett Type-suffix:</span><span class="sxs-lookup"><span data-stu-id="6f494-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="6f494-153">Om Type-suffixet är `u` och värdet kan representeras av typ, `[uint]` är dess typ `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="6f494-154">Om Type-suffixet är `u` och värdet kan representeras av typ, `[ulong]` är dess typ `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="6f494-155">Om dess värde kan representeras av en typ som anges, är det dess typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="6f494-156">Annars är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="6f494-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="6f494-157">Riktiga litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-157">Real literals</span></span>

<span data-ttu-id="6f494-158">Det går bara att skriva reella litteraler i decimal format.</span><span class="sxs-lookup"><span data-stu-id="6f494-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="6f494-159">Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.</span><span class="sxs-lookup"><span data-stu-id="6f494-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="6f494-160">Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten.</span><span class="sxs-lookup"><span data-stu-id="6f494-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="6f494-161">Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.</span><span class="sxs-lookup"><span data-stu-id="6f494-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="6f494-162">Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="6f494-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="6f494-163">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="6f494-163">Suffix</span></span> |       <span data-ttu-id="6f494-164">Innebörd</span><span class="sxs-lookup"><span data-stu-id="6f494-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="6f494-165">d</span><span class="sxs-lookup"><span data-stu-id="6f494-165">d</span></span>      | <span data-ttu-id="6f494-166">decimal data typ</span><span class="sxs-lookup"><span data-stu-id="6f494-166">decimal data type</span></span>   |
| <span data-ttu-id="6f494-167">kunskap</span><span class="sxs-lookup"><span data-stu-id="6f494-167">kb</span></span>     | <span data-ttu-id="6f494-168">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="6f494-169">MB</span><span class="sxs-lookup"><span data-stu-id="6f494-169">mb</span></span>     | <span data-ttu-id="6f494-170">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-170">megabyte multiplier</span></span> |
| <span data-ttu-id="6f494-171">minst</span><span class="sxs-lookup"><span data-stu-id="6f494-171">gb</span></span>     | <span data-ttu-id="6f494-172">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="6f494-173">TB</span><span class="sxs-lookup"><span data-stu-id="6f494-173">tb</span></span>     | <span data-ttu-id="6f494-174">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-174">terabyte multiplier</span></span> |
| <span data-ttu-id="6f494-175">PT</span><span class="sxs-lookup"><span data-stu-id="6f494-175">pb</span></span>     | <span data-ttu-id="6f494-176">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="6f494-176">petabyte multiplier</span></span> |

<span data-ttu-id="6f494-177">Det finns två typer av verklig literal: dubbel och decimal.</span><span class="sxs-lookup"><span data-stu-id="6f494-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="6f494-178">Dessa anges av frånvaron eller närvaron av typen decimal-typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="6f494-179">PowerShell har inte stöd för en litteral representation av ett `[float]` värde.</span><span class="sxs-lookup"><span data-stu-id="6f494-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="6f494-180">En dubbel verklig literal har en typ `[double]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="6f494-181">En riktig decimal literal har en typ `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="6f494-182">Efterföljande nollor i bråk delen av en decimal verklig literal är signifikanta.</span><span class="sxs-lookup"><span data-stu-id="6f494-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="6f494-183">Om värdet för exponentens siffror i en `[double]` riktig literal är mindre än det lägsta stödda värdet är värdet för den `[double]` verkliga literalen 0.</span><span class="sxs-lookup"><span data-stu-id="6f494-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="6f494-184">Om värdet för exponentens siffror i en `[decimal]` riktig literal är mindre än det lägsta stödda värdet är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="6f494-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="6f494-185">Om värdet för exponentens siffror i en `[double]` eller `[decimal]` reella litteraler är större än det högsta tillåtna värdet, är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="6f494-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="6f494-186">Syntaxen tillåter en dubbel verklig literal att ha ett suffix med lång typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="6f494-187">PowerShell behandlar det här fallet som en heltals sträng vars värde representeras av Type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="6f494-188">Den här funktionen har behållits för bakåtkompatibilitet med tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6f494-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="6f494-189">Programmerare rekommenderas dock inte att använda heltals strängar i det här formuläret eftersom de lätt kan dölja litteralens faktiska värde.</span><span class="sxs-lookup"><span data-stu-id="6f494-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="6f494-190">Har t. ex. `1.2L` värdet 1, `1.2345e1L` värdet 12 och `1.2345e-5L` värdet 0, ingen av som är direkt uppenbara.</span><span class="sxs-lookup"><span data-stu-id="6f494-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="6f494-191">Numeriska multiplikatorer</span><span class="sxs-lookup"><span data-stu-id="6f494-191">Numeric multipliers</span></span>

<span data-ttu-id="6f494-192">För enkelhetens skull kan heltal och reella litteraler innehålla en numerisk multiplikator som visar en uppsättning vanliga befogenheter på 2.</span><span class="sxs-lookup"><span data-stu-id="6f494-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="6f494-193">Den numeriska multiplikatorn kan skrivas i valfri kombination av versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="6f494-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="6f494-194">Multiplikatorns suffix kan användas i kombination med alla typer av suffix, men måste finnas efter typ-suffixet.</span><span class="sxs-lookup"><span data-stu-id="6f494-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="6f494-195">Literalen är till exempel `100gbL` felaktig, men litteralen `100Lgb` är giltig.</span><span class="sxs-lookup"><span data-stu-id="6f494-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="6f494-196">Om en multiplikator skapar ett värde som överskrider de möjliga värdena för den numeriska typ som suffixet anger, är literalen felaktig.</span><span class="sxs-lookup"><span data-stu-id="6f494-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="6f494-197">Litteralen är till exempel `1usgb` felaktig eftersom värdet `1gb` är större än vad som tillåts för den `[ushort]` typ som anges av `us` suffixet.</span><span class="sxs-lookup"><span data-stu-id="6f494-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="6f494-198">Multiplikator exempel</span><span class="sxs-lookup"><span data-stu-id="6f494-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="6f494-199">Numeriska typ acceleratorer</span><span class="sxs-lookup"><span data-stu-id="6f494-199">Numeric type accelerators</span></span>

<span data-ttu-id="6f494-200">PowerShell stöder följande typ acceleratorer:</span><span class="sxs-lookup"><span data-stu-id="6f494-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="6f494-201">Gas</span><span class="sxs-lookup"><span data-stu-id="6f494-201">Accelerator</span></span> |         <span data-ttu-id="6f494-202">Anteckning</span><span class="sxs-lookup"><span data-stu-id="6f494-202">Note</span></span>         |           <span data-ttu-id="6f494-203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6f494-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="6f494-204">Byte (ej signerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="6f494-205">Byte (signerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="6f494-206">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="6f494-207">alias för `[int16]`</span><span class="sxs-lookup"><span data-stu-id="6f494-207">alias for `[int16]`</span></span>  | <span data-ttu-id="6f494-208">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="6f494-209">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="6f494-210">alias för `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="6f494-210">alias for `[uint16]`</span></span> | <span data-ttu-id="6f494-211">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="6f494-212">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="6f494-213">alias för `[int32]`</span><span class="sxs-lookup"><span data-stu-id="6f494-213">alias for `[int32]`</span></span>  | <span data-ttu-id="6f494-214">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="6f494-215">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="6f494-216">alias för `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="6f494-216">alias for `[uint32]`</span></span> | <span data-ttu-id="6f494-217">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="6f494-218">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="6f494-219">alias för `[int64]`</span><span class="sxs-lookup"><span data-stu-id="6f494-219">alias for `[int64]`</span></span>  | <span data-ttu-id="6f494-220">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="6f494-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="6f494-221">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="6f494-222">alias för `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="6f494-222">alias for `[uint64]`</span></span> | <span data-ttu-id="6f494-223">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="6f494-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="6f494-224">Se [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="6f494-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="6f494-225">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="6f494-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="6f494-226">alias för `[single]`</span><span class="sxs-lookup"><span data-stu-id="6f494-226">alias for `[single]`</span></span> | <span data-ttu-id="6f494-227">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="6f494-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="6f494-228">Dubbel precision, flytande punkt</span><span class="sxs-lookup"><span data-stu-id="6f494-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="6f494-229">128-bitars svävande punkt</span><span class="sxs-lookup"><span data-stu-id="6f494-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="6f494-230">Följande typ acceleratorer har lagts till i PowerShell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="6f494-231">Exempel</span><span class="sxs-lookup"><span data-stu-id="6f494-231">Examples</span></span>

<span data-ttu-id="6f494-232">Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:</span><span class="sxs-lookup"><span data-stu-id="6f494-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="6f494-233">Antal</span><span class="sxs-lookup"><span data-stu-id="6f494-233">Number</span></span>    |    <span data-ttu-id="6f494-234">Typ</span><span class="sxs-lookup"><span data-stu-id="6f494-234">Type</span></span>    |    <span data-ttu-id="6f494-235">Värde</span><span class="sxs-lookup"><span data-stu-id="6f494-235">Value</span></span>     |
| ----------: | ---------- | -----------: |
|         <span data-ttu-id="6f494-236">100</span><span class="sxs-lookup"><span data-stu-id="6f494-236">100</span></span> | <span data-ttu-id="6f494-237">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-237">Int32</span></span>      |          <span data-ttu-id="6f494-238">100</span><span class="sxs-lookup"><span data-stu-id="6f494-238">100</span></span> |
|        <span data-ttu-id="6f494-239">100u</span><span class="sxs-lookup"><span data-stu-id="6f494-239">100u</span></span> | <span data-ttu-id="6f494-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="6f494-240">UInt32</span></span>     |          <span data-ttu-id="6f494-241">100</span><span class="sxs-lookup"><span data-stu-id="6f494-241">100</span></span> |
|        <span data-ttu-id="6f494-242">100D</span><span class="sxs-lookup"><span data-stu-id="6f494-242">100D</span></span> | <span data-ttu-id="6f494-243">Decimal</span><span class="sxs-lookup"><span data-stu-id="6f494-243">Decimal</span></span>    |          <span data-ttu-id="6f494-244">100</span><span class="sxs-lookup"><span data-stu-id="6f494-244">100</span></span> |
|        <span data-ttu-id="6f494-245">100l</span><span class="sxs-lookup"><span data-stu-id="6f494-245">100l</span></span> | <span data-ttu-id="6f494-246">Int64</span><span class="sxs-lookup"><span data-stu-id="6f494-246">Int64</span></span>      |          <span data-ttu-id="6f494-247">100</span><span class="sxs-lookup"><span data-stu-id="6f494-247">100</span></span> |
|       <span data-ttu-id="6f494-248">100uL</span><span class="sxs-lookup"><span data-stu-id="6f494-248">100uL</span></span> | <span data-ttu-id="6f494-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="6f494-249">UInt64</span></span>     |          <span data-ttu-id="6f494-250">100</span><span class="sxs-lookup"><span data-stu-id="6f494-250">100</span></span> |
|       <span data-ttu-id="6f494-251">100us</span><span class="sxs-lookup"><span data-stu-id="6f494-251">100us</span></span> | <span data-ttu-id="6f494-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="6f494-252">UInt16</span></span>     |          <span data-ttu-id="6f494-253">100</span><span class="sxs-lookup"><span data-stu-id="6f494-253">100</span></span> |
|       <span data-ttu-id="6f494-254">100uy</span><span class="sxs-lookup"><span data-stu-id="6f494-254">100uy</span></span> | <span data-ttu-id="6f494-255">Byte</span><span class="sxs-lookup"><span data-stu-id="6f494-255">Byte</span></span>       |          <span data-ttu-id="6f494-256">100</span><span class="sxs-lookup"><span data-stu-id="6f494-256">100</span></span> |
|        <span data-ttu-id="6f494-257">100y</span><span class="sxs-lookup"><span data-stu-id="6f494-257">100y</span></span> | <span data-ttu-id="6f494-258">SByte</span><span class="sxs-lookup"><span data-stu-id="6f494-258">SByte</span></span>      |          <span data-ttu-id="6f494-259">100</span><span class="sxs-lookup"><span data-stu-id="6f494-259">100</span></span> |
|         <span data-ttu-id="6f494-260">1e2</span><span class="sxs-lookup"><span data-stu-id="6f494-260">1e2</span></span> | <span data-ttu-id="6f494-261">Double</span><span class="sxs-lookup"><span data-stu-id="6f494-261">Double</span></span>     |          <span data-ttu-id="6f494-262">100</span><span class="sxs-lookup"><span data-stu-id="6f494-262">100</span></span> |
|        <span data-ttu-id="6f494-263">1. E2</span><span class="sxs-lookup"><span data-stu-id="6f494-263">1.e2</span></span> | <span data-ttu-id="6f494-264">Double</span><span class="sxs-lookup"><span data-stu-id="6f494-264">Double</span></span>     |          <span data-ttu-id="6f494-265">100</span><span class="sxs-lookup"><span data-stu-id="6f494-265">100</span></span> |
|       <span data-ttu-id="6f494-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="6f494-266">0x1e2</span></span> | <span data-ttu-id="6f494-267">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-267">Int32</span></span>      |          <span data-ttu-id="6f494-268">482</span><span class="sxs-lookup"><span data-stu-id="6f494-268">482</span></span> |
|      <span data-ttu-id="6f494-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="6f494-269">0x1e2L</span></span> | <span data-ttu-id="6f494-270">Int64</span><span class="sxs-lookup"><span data-stu-id="6f494-270">Int64</span></span>      |          <span data-ttu-id="6f494-271">482</span><span class="sxs-lookup"><span data-stu-id="6f494-271">482</span></span> |
|      <span data-ttu-id="6f494-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="6f494-272">0x1e2D</span></span> | <span data-ttu-id="6f494-273">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-273">Int32</span></span>      |         <span data-ttu-id="6f494-274">7725</span><span class="sxs-lookup"><span data-stu-id="6f494-274">7725</span></span> |
|        <span data-ttu-id="6f494-275">482D</span><span class="sxs-lookup"><span data-stu-id="6f494-275">482D</span></span> | <span data-ttu-id="6f494-276">Decimal</span><span class="sxs-lookup"><span data-stu-id="6f494-276">Decimal</span></span>    |          <span data-ttu-id="6f494-277">482</span><span class="sxs-lookup"><span data-stu-id="6f494-277">482</span></span> |
|       <span data-ttu-id="6f494-278">482gb</span><span class="sxs-lookup"><span data-stu-id="6f494-278">482gb</span></span> | <span data-ttu-id="6f494-279">Int64</span><span class="sxs-lookup"><span data-stu-id="6f494-279">Int64</span></span>      | <span data-ttu-id="6f494-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="6f494-280">517543559168</span></span> |
|      <span data-ttu-id="6f494-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="6f494-281">482ngb</span></span> | <span data-ttu-id="6f494-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="6f494-282">BigInteger</span></span> | <span data-ttu-id="6f494-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="6f494-283">517543559168</span></span> |
|    <span data-ttu-id="6f494-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="6f494-284">0x1e2lgb</span></span> | <span data-ttu-id="6f494-285">Int64</span><span class="sxs-lookup"><span data-stu-id="6f494-285">Int64</span></span>      | <span data-ttu-id="6f494-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="6f494-286">517543559168</span></span> |
|   <span data-ttu-id="6f494-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="6f494-287">0b1011011</span></span> | <span data-ttu-id="6f494-288">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-288">Int32</span></span>      |           <span data-ttu-id="6f494-289">91</span><span class="sxs-lookup"><span data-stu-id="6f494-289">91</span></span> |
|     <span data-ttu-id="6f494-290">0xFFFFs</span><span class="sxs-lookup"><span data-stu-id="6f494-290">0xFFFFs</span></span> | <span data-ttu-id="6f494-291">Int16</span><span class="sxs-lookup"><span data-stu-id="6f494-291">Int16</span></span>      |           <span data-ttu-id="6f494-292">-1</span><span class="sxs-lookup"><span data-stu-id="6f494-292">-1</span></span> |
|  <span data-ttu-id="6f494-293">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="6f494-293">0xFFFFFFFF</span></span> | <span data-ttu-id="6f494-294">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-294">Int32</span></span>      |           <span data-ttu-id="6f494-295">-1</span><span class="sxs-lookup"><span data-stu-id="6f494-295">-1</span></span> |
| <span data-ttu-id="6f494-296">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="6f494-296">-0xFFFFFFFF</span></span> | <span data-ttu-id="6f494-297">Int32</span><span class="sxs-lookup"><span data-stu-id="6f494-297">Int32</span></span>      |            <span data-ttu-id="6f494-298">1</span><span class="sxs-lookup"><span data-stu-id="6f494-298">1</span></span> |
| <span data-ttu-id="6f494-299">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="6f494-299">0xFFFFFFFFu</span></span> | <span data-ttu-id="6f494-300">UInt32</span><span class="sxs-lookup"><span data-stu-id="6f494-300">UInt32</span></span>     |   <span data-ttu-id="6f494-301">4294967295</span><span class="sxs-lookup"><span data-stu-id="6f494-301">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="6f494-302">Arbeta med binära eller hexadecimala tal</span><span class="sxs-lookup"><span data-stu-id="6f494-302">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="6f494-303">Alltför stora binära eller hexadecimala litteraler kan returneras som `[bigint]` i stället för att parsa, om och endast om `n` suffixet har angetts.</span><span class="sxs-lookup"><span data-stu-id="6f494-303">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="6f494-304">Signerade bitar respekteras fortfarande över jämna `[decimal]` intervall, men:</span><span class="sxs-lookup"><span data-stu-id="6f494-304">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="6f494-305">Om en binär sträng är en multipel av 8 bitar, behandlas den högsta biten som Sign-biten.</span><span class="sxs-lookup"><span data-stu-id="6f494-305">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="6f494-306">Om en hex-sträng, som har en längd som är delbar med 8, har den första siffran med 8 eller högre, behandlas siffror som negativt.</span><span class="sxs-lookup"><span data-stu-id="6f494-306">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="6f494-307">Om du anger ett osignerat suffix för binär-och hex-litteraler ignoreras tecken bitar.</span><span class="sxs-lookup"><span data-stu-id="6f494-307">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="6f494-308">Returnerar till exempel `0xFFFFFFFF` `-1` , men `0xFFFFFFFFu` returnerar `[uint]::MaxValue` 4294967295.</span><span class="sxs-lookup"><span data-stu-id="6f494-308">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="6f494-309">I PowerShell 7,1 returnerar nu ett signerat värde av den typen genom att använda ett Type-suffix på en hexadecimal litteral.</span><span class="sxs-lookup"><span data-stu-id="6f494-309">In PowerShell 7.1, using a type suffix on a hex literal now returns a signed value of that type.</span></span> <span data-ttu-id="6f494-310">I PowerShell 7,0 returnerar uttrycket till exempel `0xFFFFs` ett fel eftersom det positiva värdet är för stort för en `[int16]` typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-310">For example, in PowerShell 7.0 the expression `0xFFFFs` returns an error because the positive value is too large for an `[int16]` type.</span></span>
<span data-ttu-id="6f494-311">PowerShell 7,1 tolkar detta som `-1` en `[int16]` typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-311">PowerShell 7.1 interprets this as `-1` that is an `[int16]` type.</span></span>

<span data-ttu-id="6f494-312">Genom att prefixet med en sträng `0` kringgås detta och behandlas som osignerat.</span><span class="sxs-lookup"><span data-stu-id="6f494-312">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="6f494-313">Exempel: `0b011111111`.</span><span class="sxs-lookup"><span data-stu-id="6f494-313">For example: `0b011111111`.</span></span> <span data-ttu-id="6f494-314">Detta kan vara nödvändigt när du arbetar med litteraler i `[bigint]` intervallet, eftersom `u` `n` suffixen inte kan kombineras.</span><span class="sxs-lookup"><span data-stu-id="6f494-314">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="6f494-315">Du kan också negera binär och hex-litteraler med `-` prefixet.</span><span class="sxs-lookup"><span data-stu-id="6f494-315">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="6f494-316">Detta kan resultera i ett positivt tal eftersom inloggnings bitar är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="6f494-316">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="6f494-317">Signerade bitar accepteras för BigInteger-suffix:</span><span class="sxs-lookup"><span data-stu-id="6f494-317">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="6f494-318">BigInteger-suffixet hex behandlar den höga biten av en literal med en längd på flera av 8 tecken som tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="6f494-318">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="6f494-319">Längden inkluderar inte `0x` prefixet eller några suffix.</span><span class="sxs-lookup"><span data-stu-id="6f494-319">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="6f494-320">Binär BigInteger accepterar tecken med tecken på 96 och 128 tecken, och var 8 tecken efter.</span><span class="sxs-lookup"><span data-stu-id="6f494-320">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="6f494-321">Kommandon som ser ut som numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-321">Commands that look like numeric literals</span></span>

<span data-ttu-id="6f494-322">Alla kommandon som ser ut som en giltig numerisk literal måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal.</span><span class="sxs-lookup"><span data-stu-id="6f494-322">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="6f494-323">Felaktiga litteraler med giltig syntax som `1usgb` leder till följande fel:</span><span class="sxs-lookup"><span data-stu-id="6f494-323">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="6f494-324">Felaktiga litteraler med ogiltig syntax som `1gbus` kommer att tolkas som en vanlig standard sträng och kan tolkas som ett giltigt kommando namn i kontexter där kommandon kan anropas.</span><span class="sxs-lookup"><span data-stu-id="6f494-324">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="6f494-325">Åtkomst egenskaper och metoder för numeriska objekt</span><span class="sxs-lookup"><span data-stu-id="6f494-325">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="6f494-326">Om du vill ha åtkomst till en medlem med en numerisk literal, finns det fall när du behöver omsluta literalen inom parentes.</span><span class="sxs-lookup"><span data-stu-id="6f494-326">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="6f494-327">Literalen har inget decimal tecken</span><span class="sxs-lookup"><span data-stu-id="6f494-327">The literal does not have a decimal point</span></span>
- <span data-ttu-id="6f494-328">Literalen saknar siffror efter decimal tecknet</span><span class="sxs-lookup"><span data-stu-id="6f494-328">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="6f494-329">Literalen har inget suffix</span><span class="sxs-lookup"><span data-stu-id="6f494-329">The literal does not have a suffix</span></span>

<span data-ttu-id="6f494-330">Till exempel Miss lyckas följande exempel:</span><span class="sxs-lookup"><span data-stu-id="6f494-330">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="6f494-331">Följande exempel fungerar:</span><span class="sxs-lookup"><span data-stu-id="6f494-331">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="6f494-332">De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.</span><span class="sxs-lookup"><span data-stu-id="6f494-332">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="6f494-333">Hur PowerShell tolkar numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-333">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="6f494-334">PowerShell v 7.0 har ändrat hur numeriska litteraler tolkas för att aktivera de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="6f494-334">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="6f494-335">Parsa reella numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-335">Parsing real numeric literals</span></span>

<span data-ttu-id="6f494-336">Om literalen innehåller ett decimal tecken eller e-postnotationen tolkas strängen som ett reellt tal.</span><span class="sxs-lookup"><span data-stu-id="6f494-336">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="6f494-337">Om decimal-suffixet är tillgängligt direkt i `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-337">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="6f494-338">Annars kan du parsa `[Double]` och tillämpa multiplikatorn till värdet.</span><span class="sxs-lookup"><span data-stu-id="6f494-338">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="6f494-339">Kontrol lera sedan Skriv suffixen och försök att omvandla till lämplig typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-339">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="6f494-340">Om strängen inte har något typ-suffix tolkar du som `[Double]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-340">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="6f494-341">Paring heltal för numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="6f494-341">Paring integer numeric literals</span></span>

<span data-ttu-id="6f494-342">Heltals typ strängar parsas med hjälp av följande steg:</span><span class="sxs-lookup"><span data-stu-id="6f494-342">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="6f494-343">Fastställa bas-formatet</span><span class="sxs-lookup"><span data-stu-id="6f494-343">Determine the radix format</span></span>
   - <span data-ttu-id="6f494-344">För binära format, parsa till `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-344">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="6f494-345">För hexadecimala format kan du analysera i `[BigInteger]` att använda särskilda Casies för att behålla ursprungliga beteenden när värdet är i `[int]` `[long]` intervallet eller.</span><span class="sxs-lookup"><span data-stu-id="6f494-345">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="6f494-346">Om varken binärt eller hex tolkas normalt som en `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="6f494-346">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="6f494-347">Använd multiplikator värdet innan du försöker utföra några sändningar för att säkerställa att typ gränser kan kontrol leras på lämpligt sätt utan att flöda över.</span><span class="sxs-lookup"><span data-stu-id="6f494-347">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="6f494-348">Kontrol lera Skriv suffix.</span><span class="sxs-lookup"><span data-stu-id="6f494-348">Check type suffixes.</span></span>
   - <span data-ttu-id="6f494-349">Kontrol lera typ gränser och försök att parsa till den typen.</span><span class="sxs-lookup"><span data-stu-id="6f494-349">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="6f494-350">Om inget suffix används, begränsas värdet – kontrol leras i följande ordning, vilket resulterar i det första lyckade testet som avgör typen av nummer.</span><span class="sxs-lookup"><span data-stu-id="6f494-350">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="6f494-351">`[decimal]` (endast bas-10-litteraler)</span><span class="sxs-lookup"><span data-stu-id="6f494-351">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="6f494-352">`[double]` (endast bas-10-litteraler)</span><span class="sxs-lookup"><span data-stu-id="6f494-352">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="6f494-353">Om värdet ligger utanför `[long]` intervallet för hex och Binary Number, Miss lyckas parsningen.</span><span class="sxs-lookup"><span data-stu-id="6f494-353">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="6f494-354">Om värdet ligger utanför `[double]` intervallet för bas 10-nummer, Miss lyckas parsningen.</span><span class="sxs-lookup"><span data-stu-id="6f494-354">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="6f494-355">Högre värden måste uttryckligen skrivas med hjälp av `n` suffixet för att parsa literalen som en `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="6f494-355">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="6f494-356">Parsa stora värdes strängar</span><span class="sxs-lookup"><span data-stu-id="6f494-356">Parsing large value literals</span></span>

<span data-ttu-id="6f494-357">Tidigare parsades högre heltals värden som Double innan de omvandlades till någon annan typ.</span><span class="sxs-lookup"><span data-stu-id="6f494-357">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="6f494-358">Detta resulterar i en förlust av precision i de högre intervallen.</span><span class="sxs-lookup"><span data-stu-id="6f494-358">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="6f494-359">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6f494-359">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="6f494-360">Undvik det här problemet genom att skriva värden som strängar och sedan konvertera dem:</span><span class="sxs-lookup"><span data-stu-id="6f494-360">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="6f494-361">I PowerShell 7,0 måste du använda `N` suffixet.</span><span class="sxs-lookup"><span data-stu-id="6f494-361">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="6f494-362">Värden mellan `[ulong]::MaxValue` och `[decimal]::MaxValue` bör också anges med decimal-suffixet `D` för att bibehålla noggrannhet.</span><span class="sxs-lookup"><span data-stu-id="6f494-362">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="6f494-363">Utan suffixet tolkas dessa värden som att `[Double]` använda det verkliga tolknings läget.</span><span class="sxs-lookup"><span data-stu-id="6f494-363">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
