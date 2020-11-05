---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: dc1a55dbec1f0de99e06011645e6884b37480233
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354837"
---
# <a name="about-numeric-literals"></a><span data-ttu-id="c9d54-103">Om numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="c9d54-103">About numeric literals</span></span>

<span data-ttu-id="c9d54-104">Det finns två typer av numeriska litteraler: heltal och verklig.</span><span class="sxs-lookup"><span data-stu-id="c9d54-104">There are two kinds of numeric literals: integer and real.</span></span> <span data-ttu-id="c9d54-105">Båda kan ha Type-och multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="c9d54-105">Both can have type and multiplier suffixes.</span></span>

## <a name="integer-literals"></a><span data-ttu-id="c9d54-106">Heltals strängar</span><span class="sxs-lookup"><span data-stu-id="c9d54-106">Integer literals</span></span>

<span data-ttu-id="c9d54-107">Heltals-litteraler kan skrivas i decimal-eller hexadecimal notation.</span><span class="sxs-lookup"><span data-stu-id="c9d54-107">Integer literals can be written in decimal or hexadecimal notation.</span></span> <span data-ttu-id="c9d54-108">Hexadecimala litteraler föregås av `0x` för att skilja dem från decimal tal.</span><span class="sxs-lookup"><span data-stu-id="c9d54-108">Hexadecimal literals are prefixed with `0x` to distinguish them from decimal numbers.</span></span>

<span data-ttu-id="c9d54-109">Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="c9d54-109">Integer literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c9d54-110">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="c9d54-110">Suffix</span></span> |            <span data-ttu-id="c9d54-111">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c9d54-111">Meaning</span></span>             |          <span data-ttu-id="c9d54-112">Anteckning</span><span class="sxs-lookup"><span data-stu-id="c9d54-112">Note</span></span>           |
| ------ | ------------------------------ | ----------------------- |
| <span data-ttu-id="c9d54-113">y</span><span class="sxs-lookup"><span data-stu-id="c9d54-113">y</span></span>      | <span data-ttu-id="c9d54-114">datatyp för signerad byte</span><span class="sxs-lookup"><span data-stu-id="c9d54-114">signed byte data type</span></span>          | <span data-ttu-id="c9d54-115">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-115">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-116">uy</span><span class="sxs-lookup"><span data-stu-id="c9d54-116">uy</span></span>     | <span data-ttu-id="c9d54-117">datatyp för osignerad byte</span><span class="sxs-lookup"><span data-stu-id="c9d54-117">unsigned byte data type</span></span>        | <span data-ttu-id="c9d54-118">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-118">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-119">s</span><span class="sxs-lookup"><span data-stu-id="c9d54-119">s</span></span>      | <span data-ttu-id="c9d54-120">kort datatyp</span><span class="sxs-lookup"><span data-stu-id="c9d54-120">short data type</span></span>                | <span data-ttu-id="c9d54-121">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-121">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-122">USA</span><span class="sxs-lookup"><span data-stu-id="c9d54-122">us</span></span>     | <span data-ttu-id="c9d54-123">osignerad kort data typ</span><span class="sxs-lookup"><span data-stu-id="c9d54-123">unsigned short data type</span></span>       | <span data-ttu-id="c9d54-124">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-124">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-125">l</span><span class="sxs-lookup"><span data-stu-id="c9d54-125">l</span></span>      | <span data-ttu-id="c9d54-126">lång datatyp</span><span class="sxs-lookup"><span data-stu-id="c9d54-126">long data type</span></span>                 |                         |
| <span data-ttu-id="c9d54-127">ä</span><span class="sxs-lookup"><span data-stu-id="c9d54-127">u</span></span>      | <span data-ttu-id="c9d54-128">osignerad int-eller Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="c9d54-128">unsigned int or long data type</span></span> | <span data-ttu-id="c9d54-129">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-129">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-130">UL</span><span class="sxs-lookup"><span data-stu-id="c9d54-130">ul</span></span>     | <span data-ttu-id="c9d54-131">osignerad Long-datatyp</span><span class="sxs-lookup"><span data-stu-id="c9d54-131">unsigned long data type</span></span>        | <span data-ttu-id="c9d54-132">Tillagt i PowerShell 6,2</span><span class="sxs-lookup"><span data-stu-id="c9d54-132">Added in PowerShell 6.2</span></span> |
| <span data-ttu-id="c9d54-133">kunskap</span><span class="sxs-lookup"><span data-stu-id="c9d54-133">kb</span></span>     | <span data-ttu-id="c9d54-134">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-134">kilobyte multiplier</span></span>            |                         |
| <span data-ttu-id="c9d54-135">MB</span><span class="sxs-lookup"><span data-stu-id="c9d54-135">mb</span></span>     | <span data-ttu-id="c9d54-136">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-136">megabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c9d54-137">minst</span><span class="sxs-lookup"><span data-stu-id="c9d54-137">gb</span></span>     | <span data-ttu-id="c9d54-138">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-138">gigabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c9d54-139">TB</span><span class="sxs-lookup"><span data-stu-id="c9d54-139">tb</span></span>     | <span data-ttu-id="c9d54-140">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-140">terabyte multiplier</span></span>            |                         |
| <span data-ttu-id="c9d54-141">PT</span><span class="sxs-lookup"><span data-stu-id="c9d54-141">pb</span></span>     | <span data-ttu-id="c9d54-142">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-142">petabyte multiplier</span></span>            |                         |

<span data-ttu-id="c9d54-143">Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.</span><span class="sxs-lookup"><span data-stu-id="c9d54-143">The type of an integer literal is determined by its value, the type suffix, and the numeric multiplier suffix.</span></span>

<span data-ttu-id="c9d54-144">För en heltals sträng utan typ suffix:</span><span class="sxs-lookup"><span data-stu-id="c9d54-144">For an integer literal with no type suffix:</span></span>

- <span data-ttu-id="c9d54-145">Om värdet kan representeras av typ `[int]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-145">If the value can be represented by type `[int]`, that is its type.</span></span>
- <span data-ttu-id="c9d54-146">Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-146">Otherwise, if the value can be represented by type `[long]`, that is its type.</span></span>
- <span data-ttu-id="c9d54-147">Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-147">Otherwise, if the value can be represented by type `[decimal]`, that is its type.</span></span>
- <span data-ttu-id="c9d54-148">Annars representeras det av typen `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-148">Otherwise, it is represented by type `[double]`.</span></span>

<span data-ttu-id="c9d54-149">För en heltals sträng med ett Type-suffix:</span><span class="sxs-lookup"><span data-stu-id="c9d54-149">For an integer literal with a type suffix:</span></span>

- <span data-ttu-id="c9d54-150">Om Type-suffixet är `u` och värdet kan representeras av typ, `[uint]` är dess typ `[uint]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-150">If the type suffix is `u` and the value can be represented by type `[uint]` then its type is `[uint]`.</span></span>
- <span data-ttu-id="c9d54-151">Om Type-suffixet är `u` och värdet kan representeras av typ, `[ulong]` är dess typ `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-151">If the type suffix is `u` and the value can be represented by type `[ulong]` then its type is `[ulong]`.</span></span>
- <span data-ttu-id="c9d54-152">Om dess värde kan representeras av en typ som anges, är det dess typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-152">If its value can be represented by type specified then that is its type.</span></span>
- <span data-ttu-id="c9d54-153">Annars är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="c9d54-153">Otherwise, that literal is malformed.</span></span>

## <a name="real-literals"></a><span data-ttu-id="c9d54-154">Riktiga litteraler</span><span class="sxs-lookup"><span data-stu-id="c9d54-154">Real literals</span></span>

<span data-ttu-id="c9d54-155">Det går bara att skriva reella litteraler i decimal format.</span><span class="sxs-lookup"><span data-stu-id="c9d54-155">Real literals can only be written in decimal notation.</span></span> <span data-ttu-id="c9d54-156">Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.</span><span class="sxs-lookup"><span data-stu-id="c9d54-156">This notation can include fractional values following a decimal point and scientific notation using an exponential part.</span></span>

<span data-ttu-id="c9d54-157">Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten.</span><span class="sxs-lookup"><span data-stu-id="c9d54-157">The exponential part includes an 'e' followed by an optional sign (+/-) and a number representing the exponent.</span></span> <span data-ttu-id="c9d54-158">Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.</span><span class="sxs-lookup"><span data-stu-id="c9d54-158">For example, the literal value `1e2` equals the numeric value 100.</span></span>

<span data-ttu-id="c9d54-159">Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.</span><span class="sxs-lookup"><span data-stu-id="c9d54-159">Real literals can have a type suffix and a multiplier suffix.</span></span>

| <span data-ttu-id="c9d54-160">Huvudnamnssuffix</span><span class="sxs-lookup"><span data-stu-id="c9d54-160">Suffix</span></span> |       <span data-ttu-id="c9d54-161">Innebörd</span><span class="sxs-lookup"><span data-stu-id="c9d54-161">Meaning</span></span>       |
| ------ | ------------------- |
| <span data-ttu-id="c9d54-162">d</span><span class="sxs-lookup"><span data-stu-id="c9d54-162">d</span></span>      | <span data-ttu-id="c9d54-163">decimal data typ</span><span class="sxs-lookup"><span data-stu-id="c9d54-163">decimal data type</span></span>   |
| <span data-ttu-id="c9d54-164">kunskap</span><span class="sxs-lookup"><span data-stu-id="c9d54-164">kb</span></span>     | <span data-ttu-id="c9d54-165">KB-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-165">kilobyte multiplier</span></span> |
| <span data-ttu-id="c9d54-166">MB</span><span class="sxs-lookup"><span data-stu-id="c9d54-166">mb</span></span>     | <span data-ttu-id="c9d54-167">MB multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-167">megabyte multiplier</span></span> |
| <span data-ttu-id="c9d54-168">minst</span><span class="sxs-lookup"><span data-stu-id="c9d54-168">gb</span></span>     | <span data-ttu-id="c9d54-169">GB multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-169">gigabyte multiplier</span></span> |
| <span data-ttu-id="c9d54-170">TB</span><span class="sxs-lookup"><span data-stu-id="c9d54-170">tb</span></span>     | <span data-ttu-id="c9d54-171">terabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-171">terabyte multiplier</span></span> |
| <span data-ttu-id="c9d54-172">PT</span><span class="sxs-lookup"><span data-stu-id="c9d54-172">pb</span></span>     | <span data-ttu-id="c9d54-173">petabyte-multiplikator</span><span class="sxs-lookup"><span data-stu-id="c9d54-173">petabyte multiplier</span></span> |

<span data-ttu-id="c9d54-174">Det finns två typer av verklig literal: dubbel och decimal.</span><span class="sxs-lookup"><span data-stu-id="c9d54-174">There are two kinds of real literal: double and decimal.</span></span> <span data-ttu-id="c9d54-175">Dessa anges av frånvaron eller närvaron av typen decimal-typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-175">These are indicated by the absence or presence, respectively, of decimal-type suffix.</span></span> <span data-ttu-id="c9d54-176">PowerShell har inte stöd för en litteral representation av ett `[float]` värde.</span><span class="sxs-lookup"><span data-stu-id="c9d54-176">PowerShell does not support a literal representation of a `[float]` value.</span></span> <span data-ttu-id="c9d54-177">En dubbel verklig literal har en typ `[double]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-177">A double real literal has type `[double]`.</span></span> <span data-ttu-id="c9d54-178">En riktig decimal literal har en typ `[decimal]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-178">A decimal real literal has type `[decimal]`.</span></span>
<span data-ttu-id="c9d54-179">Efterföljande nollor i bråk delen av en decimal verklig literal är signifikanta.</span><span class="sxs-lookup"><span data-stu-id="c9d54-179">Trailing zeros in the fraction part of a decimal real literal are significant.</span></span>

<span data-ttu-id="c9d54-180">Om värdet för exponentens siffror i en `[double]` riktig literal är mindre än det lägsta stödda värdet är värdet för den `[double]` verkliga literalen 0.</span><span class="sxs-lookup"><span data-stu-id="c9d54-180">If the value of exponent-part's digits in a `[double]` real literal is less than the minimum supported, the value of that `[double]` real literal is 0.</span></span> <span data-ttu-id="c9d54-181">Om värdet för exponentens siffror i en `[decimal]` riktig literal är mindre än det lägsta stödda värdet är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="c9d54-181">If the value of exponent-part's digits in a `[decimal]` real literal is less than the minimum supported, that literal is malformed.</span></span> <span data-ttu-id="c9d54-182">Om värdet för exponentens siffror i en `[double]` eller `[decimal]` reella litteraler är större än det högsta tillåtna värdet, är den litteralen felaktig.</span><span class="sxs-lookup"><span data-stu-id="c9d54-182">If the value of exponent-part's digits in a `[double]` or `[decimal]` real literal is greater than the maximum supported, that literal is malformed.</span></span>

> [!NOTE]
> <span data-ttu-id="c9d54-183">Syntaxen tillåter en dubbel verklig literal att ha ett suffix med lång typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-183">The syntax permits a double real literal to have a long-type suffix.</span></span>
> <span data-ttu-id="c9d54-184">PowerShell behandlar det här fallet som en heltals sträng vars värde representeras av Type `[long]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-184">PowerShell treats this case as an integer literal whose value is represented by type `[long]`.</span></span> <span data-ttu-id="c9d54-185">Den här funktionen har behållits för bakåtkompatibilitet med tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c9d54-185">This feature has been retained for backwards compatibility with earlier versions of PowerShell.</span></span> <span data-ttu-id="c9d54-186">Programmerare rekommenderas dock inte att använda heltals strängar i det här formuläret eftersom de lätt kan dölja litteralens faktiska värde.</span><span class="sxs-lookup"><span data-stu-id="c9d54-186">However, programmers are discouraged from using integer literals of this form as they can easily obscure the literal's actual value.</span></span> <span data-ttu-id="c9d54-187">Har t. ex. `1.2L` värdet 1, `1.2345e1L` värdet 12 och `1.2345e-5L` värdet 0, ingen av som är direkt uppenbara.</span><span class="sxs-lookup"><span data-stu-id="c9d54-187">For example, `1.2L` has value 1, `1.2345e1L` has value 12, and `1.2345e-5L` has value 0, none of which are immediately obvious.</span></span>

## <a name="numeric-multipliers"></a><span data-ttu-id="c9d54-188">Numeriska multiplikatorer</span><span class="sxs-lookup"><span data-stu-id="c9d54-188">Numeric multipliers</span></span>

<span data-ttu-id="c9d54-189">För enkelhetens skull kan heltal och reella litteraler innehålla en numerisk multiplikator som visar en uppsättning vanliga befogenheter på 2.</span><span class="sxs-lookup"><span data-stu-id="c9d54-189">For convenience, integer and real literals can contain a numeric multiplier, which indicates one of a set of commonly used powers of 2.</span></span> <span data-ttu-id="c9d54-190">Den numeriska multiplikatorn kan skrivas i valfri kombination av versaler eller gemener.</span><span class="sxs-lookup"><span data-stu-id="c9d54-190">The numeric multiplier can be written in any combination of upper or lowercase letters.</span></span>

<span data-ttu-id="c9d54-191">Utkombinations-suffixen kan användas i kombination med `u` , `ul` och `l` skriver suffix.</span><span class="sxs-lookup"><span data-stu-id="c9d54-191">The multiplier suffixes can be used in combination with the `u`, `ul`, and `l` type suffixes.</span></span>

### <a name="multiplier-examples"></a><span data-ttu-id="c9d54-192">Multiplikator exempel</span><span class="sxs-lookup"><span data-stu-id="c9d54-192">Multiplier examples</span></span>

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

## <a name="numeric-type-accelerators"></a><span data-ttu-id="c9d54-193">Numeriska typ acceleratorer</span><span class="sxs-lookup"><span data-stu-id="c9d54-193">Numeric type accelerators</span></span>

<span data-ttu-id="c9d54-194">PowerShell stöder följande typ acceleratorer:</span><span class="sxs-lookup"><span data-stu-id="c9d54-194">PowerShell supports the following type accelerators:</span></span>

| <span data-ttu-id="c9d54-195">Gas</span><span class="sxs-lookup"><span data-stu-id="c9d54-195">Accelerator</span></span> |         <span data-ttu-id="c9d54-196">Anteckning</span><span class="sxs-lookup"><span data-stu-id="c9d54-196">Note</span></span>         |           <span data-ttu-id="c9d54-197">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9d54-197">Description</span></span>            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | <span data-ttu-id="c9d54-198">Byte (ej signerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-198">Byte (unsigned)</span></span>                  |
| `[sbyte]`   |                      | <span data-ttu-id="c9d54-199">Byte (signerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-199">Byte (signed)</span></span>                    |
| `[Int16]`   |                      | <span data-ttu-id="c9d54-200">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-200">16-bit integer</span></span>                   |
| `[short]`   | <span data-ttu-id="c9d54-201">alias för `[int16]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-201">alias for `[int16]`</span></span>  | <span data-ttu-id="c9d54-202">16-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-202">16-bit integer</span></span>                   |
| `[UInt16]`  |                      | <span data-ttu-id="c9d54-203">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-203">16-bit integer (unsigned)</span></span>        |
| `[ushort]`  | <span data-ttu-id="c9d54-204">alias för `[uint16]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-204">alias for `[uint16]`</span></span> | <span data-ttu-id="c9d54-205">16-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-205">16-bit integer (unsigned)</span></span>        |
| `[Int32]`   |                      | <span data-ttu-id="c9d54-206">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-206">32-bit integer</span></span>                   |
| `[int]`     | <span data-ttu-id="c9d54-207">alias för `[int32]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-207">alias for `[int32]`</span></span>  | <span data-ttu-id="c9d54-208">32-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-208">32-bit integer</span></span>                   |
| `[UInt32]`  |                      | <span data-ttu-id="c9d54-209">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-209">32-bit integer (unsigned)</span></span>        |
| `[uint]`    | <span data-ttu-id="c9d54-210">alias för `[uint32]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-210">alias for `[uint32]`</span></span> | <span data-ttu-id="c9d54-211">32-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-211">32-bit integer (unsigned)</span></span>        |
| `[Int64]`   |                      | <span data-ttu-id="c9d54-212">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-212">64-bit integer</span></span>                   |
| `[long]`    | <span data-ttu-id="c9d54-213">alias för `[int64]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-213">alias for `[int64]`</span></span>  | <span data-ttu-id="c9d54-214">64-bitars heltal</span><span class="sxs-lookup"><span data-stu-id="c9d54-214">64-bit integer</span></span>                   |
| `[UInt64]`  |                      | <span data-ttu-id="c9d54-215">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-215">64-bit integer (unsigned)</span></span>        |
| `[ulong]`   | <span data-ttu-id="c9d54-216">alias för `[uint64]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-216">alias for `[uint64]`</span></span> | <span data-ttu-id="c9d54-217">64-bitars heltal (osignerat)</span><span class="sxs-lookup"><span data-stu-id="c9d54-217">64-bit integer (unsigned)</span></span>        |
| `[bigint]`  |                      | <span data-ttu-id="c9d54-218">Se [BigInteger struct][bigint]</span><span class="sxs-lookup"><span data-stu-id="c9d54-218">See [BigInteger Struct][bigint]</span></span>  |
| `[single]`  |                      | <span data-ttu-id="c9d54-219">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="c9d54-219">Single precision floating point</span></span>  |
| `[float]`   | <span data-ttu-id="c9d54-220">alias för `[single]`</span><span class="sxs-lookup"><span data-stu-id="c9d54-220">alias for `[single]`</span></span> | <span data-ttu-id="c9d54-221">Flyttal med enkel precision</span><span class="sxs-lookup"><span data-stu-id="c9d54-221">Single precision floating point</span></span>  |
| `[double]`  |                      | <span data-ttu-id="c9d54-222">Dubbel precision, flytande punkt</span><span class="sxs-lookup"><span data-stu-id="c9d54-222">Double precision floating point</span></span>  |
| `[decimal]` |                      | <span data-ttu-id="c9d54-223">128-bitars svävande punkt</span><span class="sxs-lookup"><span data-stu-id="c9d54-223">128-bit floating point</span></span>           |

> [!NOTE]
> <span data-ttu-id="c9d54-224">Följande typ acceleratorer har lagts till i PowerShell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .</span><span class="sxs-lookup"><span data-stu-id="c9d54-224">The following type accelerators were added in PowerShell 6.2: `[short]`, `[ushort]`, `[uint]`, `[ulong]`.</span></span>

### <a name="working-with-other-numeric-types"></a><span data-ttu-id="c9d54-225">Arbeta med andra numeriska typer</span><span class="sxs-lookup"><span data-stu-id="c9d54-225">Working with other numeric types</span></span>

<span data-ttu-id="c9d54-226">Om du vill arbeta med andra numeriska typer måste du använda typ acceleratorer, som inte utan några problem.</span><span class="sxs-lookup"><span data-stu-id="c9d54-226">To work with any other numeric types you must use type accelerators, which is not without some problems.</span></span> <span data-ttu-id="c9d54-227">Till exempel tolkas alltid höga heltals värden som dubbelt innan de skickas till någon annan typ.</span><span class="sxs-lookup"><span data-stu-id="c9d54-227">For example, high integer values are always parsed as double before being cast to any other type.</span></span>

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

<span data-ttu-id="c9d54-228">Värdet parsas som en dubbel första och förlorar precisionen i de högre intervallen.</span><span class="sxs-lookup"><span data-stu-id="c9d54-228">The value is parsed as a double first, losing precision in the higher ranges.</span></span>
<span data-ttu-id="c9d54-229">Undvik det här problemet genom att ange värden som strängar och sedan konvertera dem:</span><span class="sxs-lookup"><span data-stu-id="c9d54-229">To avoid this problem, enter values as strings and then convert them:</span></span>

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a><span data-ttu-id="c9d54-230">Exempel</span><span class="sxs-lookup"><span data-stu-id="c9d54-230">Examples</span></span>

<span data-ttu-id="c9d54-231">Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:</span><span class="sxs-lookup"><span data-stu-id="c9d54-231">The following table contains several examples of numeric literals and lists their type and value:</span></span>

|  <span data-ttu-id="c9d54-232">Antal</span><span class="sxs-lookup"><span data-stu-id="c9d54-232">Number</span></span>  |  <span data-ttu-id="c9d54-233">Typ</span><span class="sxs-lookup"><span data-stu-id="c9d54-233">Type</span></span>   |    <span data-ttu-id="c9d54-234">Värde</span><span class="sxs-lookup"><span data-stu-id="c9d54-234">Value</span></span>     |
| -------: | ------- | -----------: |
|      <span data-ttu-id="c9d54-235">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-235">100</span></span> | <span data-ttu-id="c9d54-236">Int32</span><span class="sxs-lookup"><span data-stu-id="c9d54-236">Int32</span></span>   |          <span data-ttu-id="c9d54-237">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-237">100</span></span> |
|     <span data-ttu-id="c9d54-238">100D</span><span class="sxs-lookup"><span data-stu-id="c9d54-238">100D</span></span> | <span data-ttu-id="c9d54-239">Decimal</span><span class="sxs-lookup"><span data-stu-id="c9d54-239">Decimal</span></span> |          <span data-ttu-id="c9d54-240">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-240">100</span></span> |
|     <span data-ttu-id="c9d54-241">100l</span><span class="sxs-lookup"><span data-stu-id="c9d54-241">100l</span></span> | <span data-ttu-id="c9d54-242">Int64</span><span class="sxs-lookup"><span data-stu-id="c9d54-242">Int64</span></span>   |          <span data-ttu-id="c9d54-243">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-243">100</span></span> |
|    <span data-ttu-id="c9d54-244">100uL</span><span class="sxs-lookup"><span data-stu-id="c9d54-244">100uL</span></span> | <span data-ttu-id="c9d54-245">UInt64</span><span class="sxs-lookup"><span data-stu-id="c9d54-245">UInt64</span></span>  |          <span data-ttu-id="c9d54-246">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-246">100</span></span> |
|    <span data-ttu-id="c9d54-247">100us</span><span class="sxs-lookup"><span data-stu-id="c9d54-247">100us</span></span> | <span data-ttu-id="c9d54-248">UInt16</span><span class="sxs-lookup"><span data-stu-id="c9d54-248">UInt16</span></span>  |          <span data-ttu-id="c9d54-249">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-249">100</span></span> |
|    <span data-ttu-id="c9d54-250">100uy</span><span class="sxs-lookup"><span data-stu-id="c9d54-250">100uy</span></span> | <span data-ttu-id="c9d54-251">Byte</span><span class="sxs-lookup"><span data-stu-id="c9d54-251">Byte</span></span>    |          <span data-ttu-id="c9d54-252">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-252">100</span></span> |
|     <span data-ttu-id="c9d54-253">100y</span><span class="sxs-lookup"><span data-stu-id="c9d54-253">100y</span></span> | <span data-ttu-id="c9d54-254">SByte</span><span class="sxs-lookup"><span data-stu-id="c9d54-254">SByte</span></span>   |          <span data-ttu-id="c9d54-255">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-255">100</span></span> |
|      <span data-ttu-id="c9d54-256">1e2</span><span class="sxs-lookup"><span data-stu-id="c9d54-256">1e2</span></span> | <span data-ttu-id="c9d54-257">Double</span><span class="sxs-lookup"><span data-stu-id="c9d54-257">Double</span></span>  |          <span data-ttu-id="c9d54-258">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-258">100</span></span> |
|     <span data-ttu-id="c9d54-259">1. E2</span><span class="sxs-lookup"><span data-stu-id="c9d54-259">1.e2</span></span> | <span data-ttu-id="c9d54-260">Double</span><span class="sxs-lookup"><span data-stu-id="c9d54-260">Double</span></span>  |          <span data-ttu-id="c9d54-261">100</span><span class="sxs-lookup"><span data-stu-id="c9d54-261">100</span></span> |
|    <span data-ttu-id="c9d54-262">0x1e2</span><span class="sxs-lookup"><span data-stu-id="c9d54-262">0x1e2</span></span> | <span data-ttu-id="c9d54-263">Int32</span><span class="sxs-lookup"><span data-stu-id="c9d54-263">Int32</span></span>   |          <span data-ttu-id="c9d54-264">482</span><span class="sxs-lookup"><span data-stu-id="c9d54-264">482</span></span> |
|   <span data-ttu-id="c9d54-265">0x1e2L</span><span class="sxs-lookup"><span data-stu-id="c9d54-265">0x1e2L</span></span> | <span data-ttu-id="c9d54-266">Int64</span><span class="sxs-lookup"><span data-stu-id="c9d54-266">Int64</span></span>   |          <span data-ttu-id="c9d54-267">482</span><span class="sxs-lookup"><span data-stu-id="c9d54-267">482</span></span> |
|   <span data-ttu-id="c9d54-268">0x1e2D</span><span class="sxs-lookup"><span data-stu-id="c9d54-268">0x1e2D</span></span> | <span data-ttu-id="c9d54-269">Int32</span><span class="sxs-lookup"><span data-stu-id="c9d54-269">Int32</span></span>   |         <span data-ttu-id="c9d54-270">7725</span><span class="sxs-lookup"><span data-stu-id="c9d54-270">7725</span></span> |
|     <span data-ttu-id="c9d54-271">482D</span><span class="sxs-lookup"><span data-stu-id="c9d54-271">482D</span></span> | <span data-ttu-id="c9d54-272">Decimal</span><span class="sxs-lookup"><span data-stu-id="c9d54-272">Decimal</span></span> |          <span data-ttu-id="c9d54-273">482</span><span class="sxs-lookup"><span data-stu-id="c9d54-273">482</span></span> |
|    <span data-ttu-id="c9d54-274">482gb</span><span class="sxs-lookup"><span data-stu-id="c9d54-274">482gb</span></span> | <span data-ttu-id="c9d54-275">Int64</span><span class="sxs-lookup"><span data-stu-id="c9d54-275">Int64</span></span>   | <span data-ttu-id="c9d54-276">517543559168</span><span class="sxs-lookup"><span data-stu-id="c9d54-276">517543559168</span></span> |
| <span data-ttu-id="c9d54-277">0x1e2lgb</span><span class="sxs-lookup"><span data-stu-id="c9d54-277">0x1e2lgb</span></span> | <span data-ttu-id="c9d54-278">Int64</span><span class="sxs-lookup"><span data-stu-id="c9d54-278">Int64</span></span>   | <span data-ttu-id="c9d54-279">517543559168</span><span class="sxs-lookup"><span data-stu-id="c9d54-279">517543559168</span></span> |

### <a name="commands-that-look-like-numeric-literals"></a><span data-ttu-id="c9d54-280">Kommandon som ser ut som numeriska litteraler</span><span class="sxs-lookup"><span data-stu-id="c9d54-280">Commands that look like numeric literals</span></span>

<span data-ttu-id="c9d54-281">Alla kommandon som ser ut som en numerisk litteral måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal av den associerade typen.</span><span class="sxs-lookup"><span data-stu-id="c9d54-281">Any command that looks like a numeric literal must be executed using the the call operator (`&`), otherwise it is interpreted as a number of the associated type.</span></span>

### <a name="access-properties-and-methods-of-numeric-objects"></a><span data-ttu-id="c9d54-282">Åtkomst egenskaper och metoder för numeriska objekt</span><span class="sxs-lookup"><span data-stu-id="c9d54-282">Access properties and methods of numeric objects</span></span>

<span data-ttu-id="c9d54-283">Om du vill ha åtkomst till en medlem med en numerisk literal, finns det fall när du behöver omsluta literalen inom parentes.</span><span class="sxs-lookup"><span data-stu-id="c9d54-283">To access a member of a numeric literal, there are cases when you need to enclose the literal in parentheses.</span></span>

- <span data-ttu-id="c9d54-284">Literalen har inget decimal tecken</span><span class="sxs-lookup"><span data-stu-id="c9d54-284">The literal does not have a decimal point</span></span>
- <span data-ttu-id="c9d54-285">Literalen saknar siffror efter decimal tecknet</span><span class="sxs-lookup"><span data-stu-id="c9d54-285">The literal does not have any digits following the decimal point</span></span>
- <span data-ttu-id="c9d54-286">Literalen har inget suffix</span><span class="sxs-lookup"><span data-stu-id="c9d54-286">The literal does not have a suffix</span></span>

<span data-ttu-id="c9d54-287">Till exempel Miss lyckas följande exempel:</span><span class="sxs-lookup"><span data-stu-id="c9d54-287">For example, the following example fails:</span></span>

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

<span data-ttu-id="c9d54-288">Följande exempel fungerar:</span><span class="sxs-lookup"><span data-stu-id="c9d54-288">The following examples work:</span></span>

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

<span data-ttu-id="c9d54-289">De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.</span><span class="sxs-lookup"><span data-stu-id="c9d54-289">The first two examples work without enclosing the literal value in parentheses because the PowerShell parser can determine where the numeric literal ends and the **GetType** method starts.</span></span>

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
