---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: 8e26e8c67b1acadc75a67cd51bd6adb07fb7daf3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270261"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="493d6-103">Om numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-103">About numeric literals</span></span>

<span data-ttu-id="493d6-104">Det finns två typer av numeriska litteraler: heltal och verklig.</span><span class="sxs-lookup"><span data-stu-id="493d6-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="493d6-105">Båda kan ha Type-och multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="493d6-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="493d6-106">Heltals strängar</span><span class="sxs-lookup"><span data-stu-id="493d6-106">Integer literals</span></span>

<span data-ttu-id="493d6-107">Heltals-litteraler kan skrivas i decimal-, hexadecimal-eller binär notation.</span><span class="sxs-lookup"><span data-stu-id="493d6-107">Integer literals can be written in decimal, hexadecimal, or binary notation.</span></span>
<span data-ttu-id="493d6-108">Hexadecimala litteraler föregås av `0x` och binära litteraler föregås av `0b` för att skilja dem från decimal tal.</span><span class="sxs-lookup"><span data-stu-id="493d6-108">Hexadecimal literals are prefixed with `0x` and binary literals are prefixed with `0b` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="493d6-109">Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="493d6-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="493d6-110">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="493d6-110">Suffix</span></span> |            <span data-ttu-id="493d6-111">Innebörd</span><span class="sxs-lookup"><span data-stu-id="493d6-111">Meaning</span></span>             |          <span data-ttu-id="493d6-112">Anteckning</span><span class="sxs-lookup"><span data-stu-id="493d6-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="493d6-113">y</span><span class="sxs-lookup"><span data-stu-id="493d6-113">y</span></span>      | <span data-ttu-id="493d6-114">datatyp för signerad byte</span><span class="sxs-lookup"><span data-stu-id="493d6-114">signed byte data type</span></span>          | <span data-ttu-id="493d6-115">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-116">uy</span><span class="sxs-lookup"><span data-stu-id="493d6-116">uy</span></span>     | <span data-ttu-id="493d6-117">datatyp för osignerad byte</span><span class="sxs-lookup"><span data-stu-id="493d6-117">unsigned byte data type</span></span>        | <span data-ttu-id="493d6-118">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-119">s</span><span class="sxs-lookup"><span data-stu-id="493d6-119">s</span></span>      | <span data-ttu-id="493d6-120">kort datatyp</span><span class="sxs-lookup"><span data-stu-id="493d6-120">short data type</span></span>                | <span data-ttu-id="493d6-121">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-122">USA</span><span class="sxs-lookup"><span data-stu-id="493d6-122">us</span></span>     | <span data-ttu-id="493d6-123">osignerad kort data typ</span><span class="sxs-lookup"><span data-stu-id="493d6-123">unsigned short data type</span></span>       | <span data-ttu-id="493d6-124">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-125">l</span><span class="sxs-lookup"><span data-stu-id="493d6-125">l</span></span>      | <span data-ttu-id="493d6-126">lång datatyp</span><span class="sxs-lookup"><span data-stu-id="493d6-126">long data type</span></span>                 |                         |
| <span data-ttu-id="493d6-127">ä</span><span class="sxs-lookup"><span data-stu-id="493d6-127">u</span></span>      | <span data-ttu-id="493d6-128">osignerad int-eller Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="493d6-128">unsigned int or long data type</span></span> | <span data-ttu-id="493d6-129">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-130">UL</span><span class="sxs-lookup"><span data-stu-id="493d6-130">ul</span></span>     | <span data-ttu-id="493d6-131">osignerad Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="493d6-131">unsigned long data type</span></span>        | <span data-ttu-id="493d6-132">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="493d6-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="493d6-133">n</span><span class="sxs-lookup"><span data-stu-id="493d6-133">n</span></span>      | <span data-ttu-id="493d6-134">Data typen BigInteger</span><span class="sxs-lookup"><span data-stu-id="493d6-134">BigInteger data type</span></span>           | <span data-ttu-id="493d6-135">Tillagt i PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="493d6-135">Added in PowerShell 7.0</span></span> |
| <span data-ttu-id="493d6-136">kunskap</span><span class="sxs-lookup"><span data-stu-id="493d6-136">kb</span></span>     | <span data-ttu-id="493d6-137">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-137">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="493d6-138">MB</span><span class="sxs-lookup"><span data-stu-id="493d6-138">mb</span></span>     | <span data-ttu-id="493d6-139">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-139">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="493d6-140">minst</span><span class="sxs-lookup"><span data-stu-id="493d6-140">gb</span></span>     | <span data-ttu-id="493d6-141">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-141">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="493d6-142">TB</span><span class="sxs-lookup"><span data-stu-id="493d6-142">tb</span></span>     | <span data-ttu-id="493d6-143">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-143">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="493d6-144">PT</span><span class="sxs-lookup"><span data-stu-id="493d6-144">pb</span></span>     | <span data-ttu-id="493d6-145">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-145">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="493d6-146">Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.</span><span class="sxs-lookup"><span data-stu-id="493d6-146">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="493d6-147">För en heltals sträng utan typ suffix:</span><span class="sxs-lookup"><span data-stu-id="493d6-147">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="493d6-148">Om värdet kan representeras av typ `[int]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-148">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="493d6-149">Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-149">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="493d6-150">Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-150">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="493d6-151">Annars representeras det av typen `[double]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-151">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="493d6-152">För en heltals sträng med ett Type-suffix:</span><span class="sxs-lookup"><span data-stu-id="493d6-152">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="493d6-153">Om Type-suffixet är `u` och värdet kan representeras av typ, `[uint]` är dess typ `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-153">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="493d6-154">Om Type-suffixet är `u` och värdet kan representeras av typ, `[ulong]` är dess typ `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-154">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="493d6-155">Om dess värde kan representeras av en typ som anges, är det dess typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-155">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="493d6-156">Annars är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="493d6-156">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="493d6-157">Riktiga litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-157">Real literals</span></span>

<span data-ttu-id="493d6-158">Det går bara att skriva reella litteraler i decimal format.</span><span class="sxs-lookup"><span data-stu-id="493d6-158">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="493d6-159">Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.</span><span class="sxs-lookup"><span data-stu-id="493d6-159">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="493d6-160">Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten.</span><span class="sxs-lookup"><span data-stu-id="493d6-160">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="493d6-161">Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.</span><span class="sxs-lookup"><span data-stu-id="493d6-161">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="493d6-162">Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="493d6-162">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="493d6-163">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="493d6-163">Suffix</span></span> |       <span data-ttu-id="493d6-164">Innebörd</span><span class="sxs-lookup"><span data-stu-id="493d6-164">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="493d6-165">d</span><span class="sxs-lookup"><span data-stu-id="493d6-165">d</span></span>      | <span data-ttu-id="493d6-166">decimal data typ</span><span class="sxs-lookup"><span data-stu-id="493d6-166">decimal data type</span></span>   |
| <span data-ttu-id="493d6-167">kunskap</span><span class="sxs-lookup"><span data-stu-id="493d6-167">kb</span></span>     | <span data-ttu-id="493d6-168">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-168">kilobyte multiplier</span></span> |
| <span data-ttu-id="493d6-169">MB</span><span class="sxs-lookup"><span data-stu-id="493d6-169">mb</span></span>     | <span data-ttu-id="493d6-170">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-170">megabyte multiplier</span></span> |
| <span data-ttu-id="493d6-171">minst</span><span class="sxs-lookup"><span data-stu-id="493d6-171">gb</span></span>     | <span data-ttu-id="493d6-172">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-172">gigabyte multiplier</span></span> |
| <span data-ttu-id="493d6-173">TB</span><span class="sxs-lookup"><span data-stu-id="493d6-173">tb</span></span>     | <span data-ttu-id="493d6-174">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-174">terabyte multiplier</span></span> |
| <span data-ttu-id="493d6-175">PT</span><span class="sxs-lookup"><span data-stu-id="493d6-175">pb</span></span>     | <span data-ttu-id="493d6-176">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="493d6-176">petabyte multiplier</span></span> |

<span data-ttu-id="493d6-177">Det finns två typer av verklig literal: dubbel och decimal.</span><span class="sxs-lookup"><span data-stu-id="493d6-177">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="493d6-178">Dessa anges av frånvaron eller närvaron av typen decimal-typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-178">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="493d6-179">PowerShell har inte stöd för en litteral representation av ett `[float]` värde.</span><span class="sxs-lookup"><span data-stu-id="493d6-179">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="493d6-180">En dubbel verklig literal har en typ `[double]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-180">A double real literal has type `[double]`.</span></span> <span data-ttu-id="493d6-181">En riktig decimal literal har en typ `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-181">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="493d6-182">Efterföljande nollor i bråk delen av en decimal verklig literal är signifikanta.</span><span class="sxs-lookup"><span data-stu-id="493d6-182">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="493d6-183">Om värdet för exponentens siffror i en `[double]` riktig literal är mindre än det lägsta stödda värdet är värdet för den `[double]` verkliga literalen 0.</span><span class="sxs-lookup"><span data-stu-id="493d6-183">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="493d6-184">Om värdet för exponentens siffror i en `[decimal]` riktig literal är mindre än det lägsta stödda värdet är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="493d6-184">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="493d6-185">Om värdet för exponentens siffror i en `[double]` eller `[decimal]` reella litteraler är större än det högsta tillåtna värdet, är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="493d6-185">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="493d6-186">Syntaxen tillåter en dubbel verklig literal att ha ett suffix med lång typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-186">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="493d6-187">PowerShell behandlar det här fallet som en heltals sträng vars värde representeras av Type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-187">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="493d6-188">Den här funktionen har behållits för bakåtkompatibilitet med tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="493d6-188">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="493d6-189">Programmerare rekommenderas dock inte att använda heltals strängar i det här formuläret eftersom de lätt kan dölja litteralens faktiska värde.</span><span class="sxs-lookup"><span data-stu-id="493d6-189">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="493d6-190">Har t. ex. `1.2L` värdet 1, `1.2345e1L` värdet 12 och `1.2345e-5L` värdet 0, ingen av som är direkt uppenbara.</span><span class="sxs-lookup"><span data-stu-id="493d6-190">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="493d6-191">Numeriska multiplikatorer</span><span class="sxs-lookup"><span data-stu-id="493d6-191">Numeric multipliers</span></span>

<span data-ttu-id="493d6-192">För enkelhetens skull kan heltal och reella litteraler innehålla en numerisk multiplikator som visar en uppsättning vanliga befogenheter på 2.</span><span class="sxs-lookup"><span data-stu-id="493d6-192">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="493d6-193">Den numeriska multiplikatorn kan skrivas i valfri kombination av versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="493d6-193">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="493d6-194">Multiplikatorns suffix kan användas i kombination med alla typer av suffix, men måste finnas efter typ-suffixet.</span><span class="sxs-lookup"><span data-stu-id="493d6-194">The multiplier suffixes can be used in combination with any type suffixes, but must be present after the type suffix.</span></span> <span data-ttu-id="493d6-195">Literalen är till exempel `100gbL` felaktig, men litteralen `100Lgb` är giltig.</span><span class="sxs-lookup"><span data-stu-id="493d6-195">For example, the literal `100gbL` is malformed, but the literal `100Lgb` is valid.</span></span>

<span data-ttu-id="493d6-196">Om en multiplikator skapar ett värde som överskrider de möjliga värdena för den numeriska typ som suffixet anger, är literalen felaktig.</span><span class="sxs-lookup"><span data-stu-id="493d6-196">If a multiplier creates a value that exceeds the possible values for the numeric type that the suffix specifies, the literal is malformed.</span></span> <span data-ttu-id="493d6-197">Litteralen är till exempel `1usgb` felaktig eftersom värdet `1gb` är större än vad som tillåts för den `[ushort]` typ som anges av `us` suffixet.</span><span class="sxs-lookup"><span data-stu-id="493d6-197">For example, the literal `1usgb` is malformed, because the value `1gb` is larger than what is permitted for the `[ushort]` type specified by the `us` suffix.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="493d6-198">Multiplikator exempel</span><span class="sxs-lookup"><span data-stu-id="493d6-198">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="493d6-199">Numeriska typ acceleratorer</span><span class="sxs-lookup"><span data-stu-id="493d6-199">Numeric type accelerators</span></span>

<span data-ttu-id="493d6-200">PowerShell stöder följande typ acceleratorer:</span><span class="sxs-lookup"><span data-stu-id="493d6-200">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="493d6-201">Gas</span><span class="sxs-lookup"><span data-stu-id="493d6-201">Accelerator</span></span> |         <span data-ttu-id="493d6-202">Anteckning</span><span class="sxs-lookup"><span data-stu-id="493d6-202">Note</span></span>         |           <span data-ttu-id="493d6-203">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="493d6-203">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="493d6-204">Byte (ej signerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-204">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="493d6-205">Byte (signerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-205">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="493d6-206">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-206">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="493d6-207">alias för `[int16]`</span><span class="sxs-lookup"><span data-stu-id="493d6-207">alias for `[int16]`</span></span>  | <span data-ttu-id="493d6-208">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-208">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="493d6-209">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-209">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="493d6-210">alias för `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="493d6-210">alias for `[uint16]`</span></span> | <span data-ttu-id="493d6-211">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-211">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="493d6-212">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-212">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="493d6-213">alias för `[int32]`</span><span class="sxs-lookup"><span data-stu-id="493d6-213">alias for `[int32]`</span></span>  | <span data-ttu-id="493d6-214">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-214">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="493d6-215">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-215">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="493d6-216">alias för `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="493d6-216">alias for `[uint32]`</span></span> | <span data-ttu-id="493d6-217">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-217">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="493d6-218">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-218">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="493d6-219">alias för `[int64]`</span><span class="sxs-lookup"><span data-stu-id="493d6-219">alias for `[int64]`</span></span>  | <span data-ttu-id="493d6-220">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="493d6-220">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="493d6-221">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-221">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="493d6-222">alias för `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="493d6-222">alias for `[uint64]`</span></span> | <span data-ttu-id="493d6-223">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="493d6-223">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="493d6-224">Se [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="493d6-224">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="493d6-225">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="493d6-225">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="493d6-226">alias för `[single]`</span><span class="sxs-lookup"><span data-stu-id="493d6-226">alias for `[single]`</span></span> | <span data-ttu-id="493d6-227">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="493d6-227">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="493d6-228">Dubbel precision, flytande punkt</span><span class="sxs-lookup"><span data-stu-id="493d6-228">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="493d6-229">128-bitars svävande punkt</span><span class="sxs-lookup"><span data-stu-id="493d6-229">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="493d6-230">Följande typ acceleratorer har lagts till i PowerShell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-230">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

## <a name="examples"></a><span data-ttu-id="493d6-231">Exempel</span><span class="sxs-lookup"><span data-stu-id="493d6-231">Examples</span></span>

<span data-ttu-id="493d6-232">Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:</span><span class="sxs-lookup"><span data-stu-id="493d6-232">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|   <span data-ttu-id="493d6-233">Antal</span><span class="sxs-lookup"><span data-stu-id="493d6-233">Number</span></span>     |  <span data-ttu-id="493d6-234">Typ</span><span class="sxs-lookup"><span data-stu-id="493d6-234">Type</span></span>      |    <span data-ttu-id="493d6-235">Värde</span><span class="sxs-lookup"><span data-stu-id="493d6-235">Value</span></span>     |
| -----------: | ---------- | -----------: |
|         <span data-ttu-id="493d6-236">100</span><span class="sxs-lookup"><span data-stu-id="493d6-236">100</span></span>  | <span data-ttu-id="493d6-237">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-237">Int32</span></span>      |          <span data-ttu-id="493d6-238">100</span><span class="sxs-lookup"><span data-stu-id="493d6-238">100</span></span> |
|        <span data-ttu-id="493d6-239">100u</span><span class="sxs-lookup"><span data-stu-id="493d6-239">100u</span></span>  | <span data-ttu-id="493d6-240">UInt32</span><span class="sxs-lookup"><span data-stu-id="493d6-240">UInt32</span></span>     |          <span data-ttu-id="493d6-241">100</span><span class="sxs-lookup"><span data-stu-id="493d6-241">100</span></span> |
|        <span data-ttu-id="493d6-242">100D</span><span class="sxs-lookup"><span data-stu-id="493d6-242">100D</span></span>  | <span data-ttu-id="493d6-243">Decimal</span><span class="sxs-lookup"><span data-stu-id="493d6-243">Decimal</span></span>    |          <span data-ttu-id="493d6-244">100</span><span class="sxs-lookup"><span data-stu-id="493d6-244">100</span></span> |
|        <span data-ttu-id="493d6-245">100l</span><span class="sxs-lookup"><span data-stu-id="493d6-245">100l</span></span>  | <span data-ttu-id="493d6-246">Int64</span><span class="sxs-lookup"><span data-stu-id="493d6-246">Int64</span></span>      |          <span data-ttu-id="493d6-247">100</span><span class="sxs-lookup"><span data-stu-id="493d6-247">100</span></span> |
|       <span data-ttu-id="493d6-248">100uL</span><span class="sxs-lookup"><span data-stu-id="493d6-248">100uL</span></span>  | <span data-ttu-id="493d6-249">UInt64</span><span class="sxs-lookup"><span data-stu-id="493d6-249">UInt64</span></span>     |          <span data-ttu-id="493d6-250">100</span><span class="sxs-lookup"><span data-stu-id="493d6-250">100</span></span> |
|       <span data-ttu-id="493d6-251">100us</span><span class="sxs-lookup"><span data-stu-id="493d6-251">100us</span></span>  | <span data-ttu-id="493d6-252">UInt16</span><span class="sxs-lookup"><span data-stu-id="493d6-252">UInt16</span></span>     |          <span data-ttu-id="493d6-253">100</span><span class="sxs-lookup"><span data-stu-id="493d6-253">100</span></span> |
|       <span data-ttu-id="493d6-254">100uy</span><span class="sxs-lookup"><span data-stu-id="493d6-254">100uy</span></span>  | <span data-ttu-id="493d6-255">Byte</span><span class="sxs-lookup"><span data-stu-id="493d6-255">Byte</span></span>       |          <span data-ttu-id="493d6-256">100</span><span class="sxs-lookup"><span data-stu-id="493d6-256">100</span></span> |
|        <span data-ttu-id="493d6-257">100y</span><span class="sxs-lookup"><span data-stu-id="493d6-257">100y</span></span>  | <span data-ttu-id="493d6-258">SByte</span><span class="sxs-lookup"><span data-stu-id="493d6-258">SByte</span></span>      |          <span data-ttu-id="493d6-259">100</span><span class="sxs-lookup"><span data-stu-id="493d6-259">100</span></span> |
|         <span data-ttu-id="493d6-260">1e2</span><span class="sxs-lookup"><span data-stu-id="493d6-260">1e2</span></span>  | <span data-ttu-id="493d6-261">Double</span><span class="sxs-lookup"><span data-stu-id="493d6-261">Double</span></span>     |          <span data-ttu-id="493d6-262">100</span><span class="sxs-lookup"><span data-stu-id="493d6-262">100</span></span> |
|        <span data-ttu-id="493d6-263">1. E2</span><span class="sxs-lookup"><span data-stu-id="493d6-263">1.e2</span></span>  | <span data-ttu-id="493d6-264">Double</span><span class="sxs-lookup"><span data-stu-id="493d6-264">Double</span></span>     |          <span data-ttu-id="493d6-265">100</span><span class="sxs-lookup"><span data-stu-id="493d6-265">100</span></span> |
|       <span data-ttu-id="493d6-266">0x1e2</span><span class="sxs-lookup"><span data-stu-id="493d6-266">0x1e2</span></span>  | <span data-ttu-id="493d6-267">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-267">Int32</span></span>      |          <span data-ttu-id="493d6-268">482</span><span class="sxs-lookup"><span data-stu-id="493d6-268">482</span></span> |
|      <span data-ttu-id="493d6-269">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="493d6-269">0x1e2L</span></span>  | <span data-ttu-id="493d6-270">Int64</span><span class="sxs-lookup"><span data-stu-id="493d6-270">Int64</span></span>      |          <span data-ttu-id="493d6-271">482</span><span class="sxs-lookup"><span data-stu-id="493d6-271">482</span></span> |
|      <span data-ttu-id="493d6-272">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="493d6-272">0x1e2D</span></span>  | <span data-ttu-id="493d6-273">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-273">Int32</span></span>      |         <span data-ttu-id="493d6-274">7725</span><span class="sxs-lookup"><span data-stu-id="493d6-274">7725</span></span> |
|        <span data-ttu-id="493d6-275">482D</span><span class="sxs-lookup"><span data-stu-id="493d6-275">482D</span></span>  | <span data-ttu-id="493d6-276">Decimal</span><span class="sxs-lookup"><span data-stu-id="493d6-276">Decimal</span></span>    |          <span data-ttu-id="493d6-277">482</span><span class="sxs-lookup"><span data-stu-id="493d6-277">482</span></span> |
|       <span data-ttu-id="493d6-278">482gb</span><span class="sxs-lookup"><span data-stu-id="493d6-278">482gb</span></span>  | <span data-ttu-id="493d6-279">Int64</span><span class="sxs-lookup"><span data-stu-id="493d6-279">Int64</span></span>      | <span data-ttu-id="493d6-280">517543559168</span><span class="sxs-lookup"><span data-stu-id="493d6-280">517543559168</span></span> |
|       <span data-ttu-id="493d6-281">482ngb</span><span class="sxs-lookup"><span data-stu-id="493d6-281">482ngb</span></span> | <span data-ttu-id="493d6-282">BigInteger</span><span class="sxs-lookup"><span data-stu-id="493d6-282">BigInteger</span></span> | <span data-ttu-id="493d6-283">517543559168</span><span class="sxs-lookup"><span data-stu-id="493d6-283">517543559168</span></span> |
|    <span data-ttu-id="493d6-284">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="493d6-284">0x1e2lgb</span></span>  | <span data-ttu-id="493d6-285">Int64</span><span class="sxs-lookup"><span data-stu-id="493d6-285">Int64</span></span>      | <span data-ttu-id="493d6-286">517543559168</span><span class="sxs-lookup"><span data-stu-id="493d6-286">517543559168</span></span> |
|   <span data-ttu-id="493d6-287">0b1011011</span><span class="sxs-lookup"><span data-stu-id="493d6-287">0b1011011</span></span>  | <span data-ttu-id="493d6-288">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-288">Int32</span></span>      |           <span data-ttu-id="493d6-289">91</span><span class="sxs-lookup"><span data-stu-id="493d6-289">91</span></span> |
|  <span data-ttu-id="493d6-290">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="493d6-290">0xFFFFFFFF</span></span>  | <span data-ttu-id="493d6-291">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-291">Int32</span></span>      |           <span data-ttu-id="493d6-292">-1</span><span class="sxs-lookup"><span data-stu-id="493d6-292">-1</span></span> |
| <span data-ttu-id="493d6-293">-0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="493d6-293">-0xFFFFFFFF</span></span>  | <span data-ttu-id="493d6-294">Int32</span><span class="sxs-lookup"><span data-stu-id="493d6-294">Int32</span></span>      |            <span data-ttu-id="493d6-295">1</span><span class="sxs-lookup"><span data-stu-id="493d6-295">1</span></span> |
| <span data-ttu-id="493d6-296">0xFFFFFFFFu</span><span class="sxs-lookup"><span data-stu-id="493d6-296">0xFFFFFFFFu</span></span>  | <span data-ttu-id="493d6-297">UInt32</span><span class="sxs-lookup"><span data-stu-id="493d6-297">UInt32</span></span>     |   <span data-ttu-id="493d6-298">4294967295</span><span class="sxs-lookup"><span data-stu-id="493d6-298">4294967295</span></span> |

### <a name="working-with-binary-or-hexadecimal-numbers"></a><span data-ttu-id="493d6-299">Arbeta med binära eller hexadecimala tal</span><span class="sxs-lookup"><span data-stu-id="493d6-299">Working with binary or hexadecimal numbers</span></span>

<span data-ttu-id="493d6-300">Alltför stora binära eller hexadecimala litteraler kan returneras som `[bigint]` i stället för att parsa, om och endast om `n` suffixet har angetts.</span><span class="sxs-lookup"><span data-stu-id="493d6-300">Overly large binary or hexadecimal literals can return as `[bigint]` rather than failing the parse, if and only if the `n` suffix is specified.</span></span> <span data-ttu-id="493d6-301">Signerade bitar respekteras fortfarande över jämna `[decimal]` intervall, men:</span><span class="sxs-lookup"><span data-stu-id="493d6-301">Sign bits are still respected above even `[decimal]` ranges, however:</span></span>

- <span data-ttu-id="493d6-302">Om en binär sträng är en multipel av 8 bitar, behandlas den högsta biten som Sign-biten.</span><span class="sxs-lookup"><span data-stu-id="493d6-302">If a binary string is some multiple of 8 bits long, the highest bit is treated as the sign bit.</span></span>
- <span data-ttu-id="493d6-303">Om en hex-sträng, som har en längd som är delbar med 8, har den första siffran med 8 eller högre, behandlas siffror som negativt.</span><span class="sxs-lookup"><span data-stu-id="493d6-303">If a hex string, which has a length that is a multiple of 8, has the first digit with 8 or higher, the numeral is treated as negative.</span></span>

<span data-ttu-id="493d6-304">Om du anger ett osignerat suffix för binär-och hex-litteraler ignoreras tecken bitar.</span><span class="sxs-lookup"><span data-stu-id="493d6-304">Specifying an unsigned suffix on binary and hex literals ignores sign bits.</span></span> <span data-ttu-id="493d6-305">Returnerar till exempel `0xFFFFFFFF` `-1` , men `0xFFFFFFFFu` returnerar `[uint]::MaxValue` 4294967295.</span><span class="sxs-lookup"><span data-stu-id="493d6-305">For example, `0xFFFFFFFF` returns `-1`, but `0xFFFFFFFFu` returns the `[uint]::MaxValue` of 4294967295.</span></span>

<span data-ttu-id="493d6-306">Genom att prefixet med en sträng `0` kringgås detta och behandlas som osignerat.</span><span class="sxs-lookup"><span data-stu-id="493d6-306">Prefixing the literal with a `0` will bypass this and be treated as unsigned.</span></span>
<span data-ttu-id="493d6-307">Till exempel: `0b011111111`.</span><span class="sxs-lookup"><span data-stu-id="493d6-307">For example: `0b011111111`.</span></span> <span data-ttu-id="493d6-308">Detta kan vara nödvändigt när du arbetar med litteraler i `[bigint]` intervallet, eftersom `u` `n` suffixen inte kan kombineras.</span><span class="sxs-lookup"><span data-stu-id="493d6-308">This can be necessary when working with literals in the `[bigint]` range, as the `u` and `n` suffixes cannot be combined.</span></span>

<span data-ttu-id="493d6-309">Du kan också negera binär och hex-litteraler med `-` prefixet.</span><span class="sxs-lookup"><span data-stu-id="493d6-309">You can also negate binary and hex literals using the `-` prefix.</span></span> <span data-ttu-id="493d6-310">Detta kan resultera i ett positivt tal eftersom inloggnings bitar är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="493d6-310">This can result in a positive number since sign bits are permitted.</span></span>

<span data-ttu-id="493d6-311">Signerade bitar accepteras för BigInteger-suffix:</span><span class="sxs-lookup"><span data-stu-id="493d6-311">Sign bits are accepted for BigInteger-suffixed numerals:</span></span>

- <span data-ttu-id="493d6-312">BigInteger-suffixet hex behandlar den höga biten av en literal med en längd på flera av 8 tecken som tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="493d6-312">BigInteger-suffixed hex treats the high bit of any literal with a length multiple of 8 characters as the sign bit.</span></span> <span data-ttu-id="493d6-313">Längden inkluderar inte `0x` prefixet eller några suffix.</span><span class="sxs-lookup"><span data-stu-id="493d6-313">The length does not include the `0x` prefix or any suffixes.</span></span>
- <span data-ttu-id="493d6-314">Binär BigInteger accepterar tecken med tecken på 96 och 128 tecken, och var 8 tecken efter.</span><span class="sxs-lookup"><span data-stu-id="493d6-314">BigInteger-suffixed binary accepts sign bits at 96 and 128 characters, and at every 8 characters after.</span></span>

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="493d6-315">Kommandon som ser ut som numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-315">Commands that look like numeric literals</span></span>

<span data-ttu-id="493d6-316">Alla kommandon som ser ut som en giltig numerisk literal måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal.</span><span class="sxs-lookup"><span data-stu-id="493d6-316">Any command that looks like a valid numeric literal must be executed using the call operator (`&`), otherwise it is interpreted as a number.</span></span> <span data-ttu-id="493d6-317">Felaktiga litteraler med giltig syntax som `1usgb` leder till följande fel:</span><span class="sxs-lookup"><span data-stu-id="493d6-317">Malformed literals with valid syntax like `1usgb` will result in the following error:</span></span>

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

<span data-ttu-id="493d6-318">Felaktiga litteraler med ogiltig syntax som `1gbus` kommer att tolkas som en vanlig standard sträng och kan tolkas som ett giltigt kommando namn i kontexter där kommandon kan anropas.</span><span class="sxs-lookup"><span data-stu-id="493d6-318">However, malformed literals with invalid syntax like `1gbus` will be interpreted as a standard bare string, and can be interpreted as a valid command name in contexts where commands may be called.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="493d6-319">Åtkomst egenskaper och metoder för numeriska objekt</span><span class="sxs-lookup"><span data-stu-id="493d6-319">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="493d6-320">Om du vill ha åtkomst till en medlem med en numerisk literal, finns det fall när du behöver omsluta literalen inom parentes.</span><span class="sxs-lookup"><span data-stu-id="493d6-320">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="493d6-321">Literalen har inget decimal tecken</span><span class="sxs-lookup"><span data-stu-id="493d6-321">The literal does not have a decimal point</span></span>
- <span data-ttu-id="493d6-322">Literalen saknar siffror efter decimal tecknet</span><span class="sxs-lookup"><span data-stu-id="493d6-322">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="493d6-323">Literalen har inget suffix</span><span class="sxs-lookup"><span data-stu-id="493d6-323">The literal does not have a suffix</span></span>

<span data-ttu-id="493d6-324">Till exempel Miss lyckas följande exempel:</span><span class="sxs-lookup"><span data-stu-id="493d6-324">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="493d6-325">Följande exempel fungerar:</span><span class="sxs-lookup"><span data-stu-id="493d6-325">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="493d6-326">De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.</span><span class="sxs-lookup"><span data-stu-id="493d6-326">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

## <a name="how-powershell-parses-numeric-literals"></a><span data-ttu-id="493d6-327">Hur PowerShell tolkar numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-327">How PowerShell parses numeric literals</span></span>

<span data-ttu-id="493d6-328">PowerShell v 7.0 har ändrat hur numeriska litteraler tolkas för att aktivera de nya funktionerna.</span><span class="sxs-lookup"><span data-stu-id="493d6-328">PowerShell v7.0 changed the way numeric literals are parsed to enable the new features.</span></span>

### <a name="parsing-real-numeric-literals"></a><span data-ttu-id="493d6-329">Parsa reella numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-329">Parsing real numeric literals</span></span>

<span data-ttu-id="493d6-330">Om literalen innehåller ett decimal tecken eller e-postnotationen tolkas strängen som ett reellt tal.</span><span class="sxs-lookup"><span data-stu-id="493d6-330">If the literal contains a decimal point or the e-notation, the literal string is parsed a real number.</span></span>

- <span data-ttu-id="493d6-331">Om decimal-suffixet är tillgängligt direkt i `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-331">If the decimal-suffix is present then directly into `[decimal]`.</span></span>
- <span data-ttu-id="493d6-332">Annars kan du parsa `[Double]` och tillämpa multiplikatorn till värdet.</span><span class="sxs-lookup"><span data-stu-id="493d6-332">Else, parse as `[Double]` and apply multiplier to the value.</span></span> <span data-ttu-id="493d6-333">Kontrol lera sedan Skriv suffixen och försök att omvandla till lämplig typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-333">Then check the type suffixes and attempt to cast into appropriate type.</span></span>
- <span data-ttu-id="493d6-334">Om strängen inte har något typ-suffix tolkar du som `[Double]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-334">If the string has no type suffix, then parse as `[Double]`.</span></span>

### <a name="paring-integer-numeric-literals"></a><span data-ttu-id="493d6-335">Paring heltal för numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="493d6-335">Paring integer numeric literals</span></span>

<span data-ttu-id="493d6-336">Heltals typ strängar parsas med hjälp av följande steg:</span><span class="sxs-lookup"><span data-stu-id="493d6-336">Integer type literals are parsed using the following steps:</span></span>

1. <span data-ttu-id="493d6-337">Fastställa bas-formatet</span><span class="sxs-lookup"><span data-stu-id="493d6-337">Determine the radix format</span></span>
   - <span data-ttu-id="493d6-338">För binära format, parsa till `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-338">For binary formats, parse into `[BigInteger]`.</span></span>
   - <span data-ttu-id="493d6-339">För hexadecimala format kan du analysera i `[BigInteger]` att använda särskilda Casies för att behålla ursprungliga beteenden när värdet är i `[int]` `[long]` intervallet eller.</span><span class="sxs-lookup"><span data-stu-id="493d6-339">For hexidecimal formats, parse into `[BigInteger]` using special casies to retain original behaviours when the value is in the `[int]` or `[long]` range.</span></span>
   - <span data-ttu-id="493d6-340">Om varken binärt eller hex tolkas normalt som en `[BigInteger]` .</span><span class="sxs-lookup"><span data-stu-id="493d6-340">If neither binary nor hex, parse normally as a `[BigInteger]`.</span></span>
2. <span data-ttu-id="493d6-341">Använd multiplikator värdet innan du försöker utföra några sändningar för att säkerställa att typ gränser kan kontrol leras på lämpligt sätt utan att flöda över.</span><span class="sxs-lookup"><span data-stu-id="493d6-341">Apply the multiplier value before attempting any casts to ensure type bounds can be appropriately checked without overflows.</span></span>
3. <span data-ttu-id="493d6-342">Kontrol lera Skriv suffix.</span><span class="sxs-lookup"><span data-stu-id="493d6-342">Check type suffixes.</span></span>
   - <span data-ttu-id="493d6-343">Kontrol lera typ gränser och försök att parsa till den typen.</span><span class="sxs-lookup"><span data-stu-id="493d6-343">Check type bounds and attempt to parse into that type.</span></span>
   - <span data-ttu-id="493d6-344">Om inget suffix används, begränsas värdet – kontrol leras i följande ordning, vilket resulterar i det första lyckade testet som avgör typen av nummer.</span><span class="sxs-lookup"><span data-stu-id="493d6-344">If no suffix is used, then the value is bounds-checked in the following order, resulting in the first successful test determining the type of the number.</span></span>
     - `[int]`
     - `[long]`
     - <span data-ttu-id="493d6-345">`[decimal]` (endast bas-10-litteraler)</span><span class="sxs-lookup"><span data-stu-id="493d6-345">`[decimal]` (base-10 literals only)</span></span>
     - <span data-ttu-id="493d6-346">`[double]` (endast bas-10-litteraler)</span><span class="sxs-lookup"><span data-stu-id="493d6-346">`[double]` (base-10 literals only)</span></span>
   - <span data-ttu-id="493d6-347">Om värdet ligger utanför `[long]` intervallet för hex och Binary Number, Miss lyckas parsningen.</span><span class="sxs-lookup"><span data-stu-id="493d6-347">If the value is outside the `[long]` range for hex and binary numbers, the parse fails.</span></span>
   - <span data-ttu-id="493d6-348">Om värdet ligger utanför `[double]` intervallet för bas 10-nummer, Miss lyckas parsningen.</span><span class="sxs-lookup"><span data-stu-id="493d6-348">If the value is outside the `[double]` range for base 10 number, the parse fails.</span></span>
   - <span data-ttu-id="493d6-349">Högre värden måste uttryckligen skrivas med hjälp av `n` suffixet för att parsa literalen som en `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="493d6-349">Higher values must be explicitly written using the `n` suffix to parse the literal as a `BigInteger`.</span></span>

### <a name="parsing-large-value-literals"></a><span data-ttu-id="493d6-350">Parsa stora värdes strängar</span><span class="sxs-lookup"><span data-stu-id="493d6-350">Parsing large value literals</span></span>

<span data-ttu-id="493d6-351">Tidigare parsades högre heltals värden som Double innan de omvandlades till någon annan typ.</span><span class="sxs-lookup"><span data-stu-id="493d6-351">Previously, higher integer values were parsed as double before being cast to any other type.</span></span> <span data-ttu-id="493d6-352">Detta resulterar i en förlust av precision i de högre intervallen.</span><span class="sxs-lookup"><span data-stu-id="493d6-352">This results in a loss of precision in the higher ranges.</span></span> <span data-ttu-id="493d6-353">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="493d6-353">For example:</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="493d6-354">Undvik det här problemet genom att skriva värden som strängar och sedan konvertera dem:</span><span class="sxs-lookup"><span data-stu-id="493d6-354">To avoid this problem you had to write values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="493d6-355">I PowerShell 7,0 måste du använda `N` suffixet.</span><span class="sxs-lookup"><span data-stu-id="493d6-355">In PowerShell 7.0 you must use the `N` suffix.</span></span>

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

<span data-ttu-id="493d6-356">Värden mellan `[ulong]::MaxValue` och `[decimal]::MaxValue` bör också anges med decimal-suffixet `D` för att bibehålla noggrannhet.</span><span class="sxs-lookup"><span data-stu-id="493d6-356">Also values between `[ulong]::MaxValue` and `[decimal]::MaxValue` should be denoted using the decimal-suffix `D` to maintain accuracy.</span></span> <span data-ttu-id="493d6-357">Utan suffixet tolkas dessa värden som att `[Double]` använda det verkliga tolknings läget.</span><span class="sxs-lookup"><span data-stu-id="493d6-357">Without the suffix, these values are parsed as `[Double]` using the real-parsing mode.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger?view=netcore-2.2
