---
description: Beskriver de operatorer som utför aritmetiska i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 3ece7464198ff52fe6c22ccc54ceede84288bd7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270237"
---
# <a name="about-arithmetic-operators"></a><span data-ttu-id="12bfd-104">Om aritmetiska operatorer</span><span class="sxs-lookup"><span data-stu-id="12bfd-104">About Arithmetic Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="12bfd-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="12bfd-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="12bfd-106">Beskriver de operatorer som utför aritmetiska i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12bfd-106">Describes the operators that perform arithmetic in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="12bfd-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="12bfd-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="12bfd-108">Aritmetiska operatorer beräknar numeriska värden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-108">Arithmetic operators calculate numeric values.</span></span> <span data-ttu-id="12bfd-109">Du kan använda en eller flera aritmetiska operatorer för att lägga till, subtrahera, multiplicera och dividera värden och för att beräkna resten (Modulus) av en divisions åtgärd.</span><span class="sxs-lookup"><span data-stu-id="12bfd-109">You can use one or more arithmetic operators to add, subtract, multiply, and divide values, and to calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="12bfd-110">Dessutom körs operatorn addition ( `+` ) och multiplikation ( `*` ) även på strängar, matriser och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="12bfd-110">In addition, the addition operator (`+`) and multiplication operator (`*`) also operate on strings, arrays, and hash tables.</span></span> <span data-ttu-id="12bfd-111">Operatorn addition sammanfogar indatamängden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-111">The addition operator concatenates the input.</span></span> <span data-ttu-id="12bfd-112">Operatorn multiplikation returnerar flera kopior av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-112">The multiplication operator returns multiple copies of the input.</span></span> <span data-ttu-id="12bfd-113">Du kan till och med blanda objekt typer i en aritmetisk instruktion.</span><span class="sxs-lookup"><span data-stu-id="12bfd-113">You can even mix object types in an arithmetic statement.</span></span> <span data-ttu-id="12bfd-114">Metoden som används för att utvärdera uttrycket bestäms av typen för objektet längst till vänster i uttrycket.</span><span class="sxs-lookup"><span data-stu-id="12bfd-114">The method that is used to evaluate the statement is determined by the type of the leftmost object in the expression.</span></span>

<span data-ttu-id="12bfd-115">Från och med PowerShell 2,0 fungerar alla aritmetiska operatorer på 64-bitars nummer.</span><span class="sxs-lookup"><span data-stu-id="12bfd-115">Beginning in PowerShell 2.0, all arithmetic operators work on 64-bit numbers.</span></span>

<span data-ttu-id="12bfd-116">Från och med PowerShell 3,0 `-shr` läggs (Shift-höger) och `-shl` (Shift-Left) till som stöd för bitvisa aritmetiska i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12bfd-116">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are added to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="12bfd-117">PowerShell stöder följande aritmetiska operatorer:</span><span class="sxs-lookup"><span data-stu-id="12bfd-117">PowerShell supports the following arithmetic operators:</span></span>

|<span data-ttu-id="12bfd-118">Operator</span><span class="sxs-lookup"><span data-stu-id="12bfd-118">Operator</span></span>|<span data-ttu-id="12bfd-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12bfd-119">Description</span></span>                       |<span data-ttu-id="12bfd-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="12bfd-120">Example</span></span>                      |
|--------|----------------------------------|-----------------------------|
| +      |<span data-ttu-id="12bfd-121">Lägger till heltal; sammanfogar</span><span class="sxs-lookup"><span data-stu-id="12bfd-121">Adds integers; concatenates</span></span>       |`6 + 2`                      |
|        |<span data-ttu-id="12bfd-122">strängar, matriser och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="12bfd-122">strings, arrays, and hash tables.</span></span> |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |<span data-ttu-id="12bfd-123">Subtraherar ett värde från ett annat</span><span class="sxs-lookup"><span data-stu-id="12bfd-123">Subtracts one value from another</span></span>  |`6 - 2`                      |
|        |<span data-ttu-id="12bfd-124">värde</span><span class="sxs-lookup"><span data-stu-id="12bfd-124">value</span></span>                             |                             |
| -      |<span data-ttu-id="12bfd-125">Gör ett tal till ett negativt tal</span><span class="sxs-lookup"><span data-stu-id="12bfd-125">Makes a number a negative number</span></span>  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |<span data-ttu-id="12bfd-126">Multiplicera tal eller kopiera strängar</span><span class="sxs-lookup"><span data-stu-id="12bfd-126">Multiply numbers or copy strings</span></span>  |`6 * 2`                      |
|        |<span data-ttu-id="12bfd-127">och matriser det angivna talet</span><span class="sxs-lookup"><span data-stu-id="12bfd-127">and arrays the specified number</span></span>   |`@("!") * 4`                 |
|        |<span data-ttu-id="12bfd-128">av gånger.</span><span class="sxs-lookup"><span data-stu-id="12bfd-128">of times.</span></span>                         |`"!" * 3`                    |
| /      |<span data-ttu-id="12bfd-129">Dividerar två värden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-129">Divides two values.</span></span>               |`6 / 2`                      |
| %      |<span data-ttu-id="12bfd-130">Modulus-returnerar resten av</span><span class="sxs-lookup"><span data-stu-id="12bfd-130">Modulus - returns the remainder of</span></span>|`7 % 2`                      |
|        |<span data-ttu-id="12bfd-131">en divisions åtgärd.</span><span class="sxs-lookup"><span data-stu-id="12bfd-131">a division operation.</span></span>             |                             |
|<span data-ttu-id="12bfd-132">-band</span><span class="sxs-lookup"><span data-stu-id="12bfd-132">-band</span></span>   |<span data-ttu-id="12bfd-133">Bitvis och</span><span class="sxs-lookup"><span data-stu-id="12bfd-133">Bitwise AND</span></span>                       |`5 -band 3`                  |
|<span data-ttu-id="12bfd-134">-bnot</span><span class="sxs-lookup"><span data-stu-id="12bfd-134">-bnot</span></span>   |<span data-ttu-id="12bfd-135">Bitvis NOT</span><span class="sxs-lookup"><span data-stu-id="12bfd-135">Bitwise NOT</span></span>                       |`-bnot 5`                    |
|<span data-ttu-id="12bfd-136">– bor</span><span class="sxs-lookup"><span data-stu-id="12bfd-136">-bor</span></span>    |<span data-ttu-id="12bfd-137">Bitvis eller</span><span class="sxs-lookup"><span data-stu-id="12bfd-137">Bitwise OR</span></span>                        |`5 -bor 0x03`                |
|<span data-ttu-id="12bfd-138">-bxor</span><span class="sxs-lookup"><span data-stu-id="12bfd-138">-bxor</span></span>   |<span data-ttu-id="12bfd-139">Bitvis XOR</span><span class="sxs-lookup"><span data-stu-id="12bfd-139">Bitwise XOR</span></span>                       |`5 -bxor 3`                  |
|<span data-ttu-id="12bfd-140">-shl</span><span class="sxs-lookup"><span data-stu-id="12bfd-140">-shl</span></span>    |<span data-ttu-id="12bfd-141">Flyttar bitar till vänster</span><span class="sxs-lookup"><span data-stu-id="12bfd-141">Shifts bits to the left</span></span>           |`102 -shl 2`                 |
|<span data-ttu-id="12bfd-142">-shr</span><span class="sxs-lookup"><span data-stu-id="12bfd-142">-shr</span></span>    |<span data-ttu-id="12bfd-143">Flyttar bitar till höger</span><span class="sxs-lookup"><span data-stu-id="12bfd-143">Shifts bits to the right</span></span>          |`102 -shr 2`                 |

<span data-ttu-id="12bfd-144">De bitvisa operatorerna fungerar bara på heltals typer.</span><span class="sxs-lookup"><span data-stu-id="12bfd-144">The bitwise operators only work on integer types.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="12bfd-145">PRIORITET FÖR OPERATOR</span><span class="sxs-lookup"><span data-stu-id="12bfd-145">OPERATOR PRECEDENCE</span></span>

<span data-ttu-id="12bfd-146">PowerShell bearbetar aritmetiska operatorer i följande ordning:</span><span class="sxs-lookup"><span data-stu-id="12bfd-146">PowerShell processes arithmetic operators in the following order:</span></span>

|<span data-ttu-id="12bfd-147">Prioritet</span><span class="sxs-lookup"><span data-stu-id="12bfd-147">Precedence</span></span>|<span data-ttu-id="12bfd-148">Operator</span><span class="sxs-lookup"><span data-stu-id="12bfd-148">Operator</span></span>          |<span data-ttu-id="12bfd-149">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12bfd-149">Description</span></span>                            |
|----------|------------------|---------------------------------------|
|<span data-ttu-id="12bfd-150">1</span><span class="sxs-lookup"><span data-stu-id="12bfd-150">1</span></span>         | `()`             |<span data-ttu-id="12bfd-151">Parentes</span><span class="sxs-lookup"><span data-stu-id="12bfd-151">Parentheses</span></span>                            |
|<span data-ttu-id="12bfd-152">2</span><span class="sxs-lookup"><span data-stu-id="12bfd-152">2</span></span>         | `-`              |<span data-ttu-id="12bfd-153">För en negativ siffra eller enställig operator</span><span class="sxs-lookup"><span data-stu-id="12bfd-153">For a negative number or unary operator</span></span>|
|<span data-ttu-id="12bfd-154">3</span><span class="sxs-lookup"><span data-stu-id="12bfd-154">3</span></span>         | <span data-ttu-id="12bfd-155">`*`, `/`, `%`</span><span class="sxs-lookup"><span data-stu-id="12bfd-155">`*`, `/`, `%`</span></span>    |<span data-ttu-id="12bfd-156">För multiplikation och division</span><span class="sxs-lookup"><span data-stu-id="12bfd-156">For multiplication and division</span></span>        |
|<span data-ttu-id="12bfd-157">4</span><span class="sxs-lookup"><span data-stu-id="12bfd-157">4</span></span>         | <span data-ttu-id="12bfd-158">`+`, `-`</span><span class="sxs-lookup"><span data-stu-id="12bfd-158">`+`, `-`</span></span>         |<span data-ttu-id="12bfd-159">För addition och subtraktion</span><span class="sxs-lookup"><span data-stu-id="12bfd-159">For addition and subtraction</span></span>           |
|<span data-ttu-id="12bfd-160">5</span><span class="sxs-lookup"><span data-stu-id="12bfd-160">5</span></span>         | <span data-ttu-id="12bfd-161">`-band`, `-bnot`</span><span class="sxs-lookup"><span data-stu-id="12bfd-161">`-band`, `-bnot`</span></span> |<span data-ttu-id="12bfd-162">För bitvisa åtgärder</span><span class="sxs-lookup"><span data-stu-id="12bfd-162">For bitwise operations</span></span>                 |
|<span data-ttu-id="12bfd-163">5</span><span class="sxs-lookup"><span data-stu-id="12bfd-163">5</span></span>         | <span data-ttu-id="12bfd-164">`-bor`, `-bxor`</span><span class="sxs-lookup"><span data-stu-id="12bfd-164">`-bor`, `-bxor`</span></span>  |<span data-ttu-id="12bfd-165">För bitvisa åtgärder</span><span class="sxs-lookup"><span data-stu-id="12bfd-165">For bitwise operations</span></span>                 |
|<span data-ttu-id="12bfd-166">5</span><span class="sxs-lookup"><span data-stu-id="12bfd-166">5</span></span>         | <span data-ttu-id="12bfd-167">`-shr`, `-shl`</span><span class="sxs-lookup"><span data-stu-id="12bfd-167">`-shr`, `-shl`</span></span>   |<span data-ttu-id="12bfd-168">För bitvisa åtgärder</span><span class="sxs-lookup"><span data-stu-id="12bfd-168">For bitwise operations</span></span>                 |

<span data-ttu-id="12bfd-169">PowerShell bearbetar uttrycken från vänster till höger enligt prioritets reglerna.</span><span class="sxs-lookup"><span data-stu-id="12bfd-169">PowerShell processes the expressions from left to right according to the precedence rules.</span></span> <span data-ttu-id="12bfd-170">I följande exempel visas resultatet av prioritets reglerna:</span><span class="sxs-lookup"><span data-stu-id="12bfd-170">The following examples show the effect of the precedence rules:</span></span>

|<span data-ttu-id="12bfd-171">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-171">Expression</span></span> |<span data-ttu-id="12bfd-172">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-172">Result</span></span>|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

<span data-ttu-id="12bfd-173">Den ordning i vilken PowerShell utvärderar uttryck kan skilja sig från andra programmerings-och skript språk som du har använt.</span><span class="sxs-lookup"><span data-stu-id="12bfd-173">The order in which PowerShell evaluates expressions might differ from other programming and scripting languages that you have used.</span></span> <span data-ttu-id="12bfd-174">I följande exempel visas en komplicerad tilldelnings instruktion.</span><span class="sxs-lookup"><span data-stu-id="12bfd-174">The following example shows a complicated assignment statement.</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

<span data-ttu-id="12bfd-175">I det här exemplet `$a++` utvärderas uttrycket före `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="12bfd-175">In this example, the expression `$a++` is evaluated before `$b[$a]`.</span></span>
<span data-ttu-id="12bfd-176">Utvärdering av `$a++` ändringar av värdet `$a` efter det används i instruktionen, `$c[$a++]` men innan det används i `$b[$a]` .</span><span class="sxs-lookup"><span data-stu-id="12bfd-176">Evaluating `$a++` changes the value of `$a` after it is used in the statement `$c[$a++]`; but, before it is used in `$b[$a]`.</span></span> <span data-ttu-id="12bfd-177">Variabeln `$a` i `$b[$a]` är lika med `1` , `0` så tilldelar instruktionen ett värde till `$b[1]` , inte `$b[0]` .</span><span class="sxs-lookup"><span data-stu-id="12bfd-177">The variable `$a` in `$b[$a]` equals `1`, not `0`; so, the statement assigns a value to `$b[1]`, not `$b[0]`.</span></span>

<span data-ttu-id="12bfd-178">Ovanstående kod motsvarar:</span><span class="sxs-lookup"><span data-stu-id="12bfd-178">The above code is equivalent to:</span></span>

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a><span data-ttu-id="12bfd-179">DIVISION OCH AVRUNDNING</span><span class="sxs-lookup"><span data-stu-id="12bfd-179">DIVISION AND ROUNDING</span></span>

<span data-ttu-id="12bfd-180">När kvoten för en divisions åtgärd är ett heltal, avrundar PowerShell värdet till närmaste heltal.</span><span class="sxs-lookup"><span data-stu-id="12bfd-180">When the quotient of a division operation is an integer, PowerShell rounds the value to the nearest integer.</span></span> <span data-ttu-id="12bfd-181">När värdet är `.5` , avrundas det till närmaste jämna heltal.</span><span class="sxs-lookup"><span data-stu-id="12bfd-181">When the value is `.5`, it rounds to the nearest even integer.</span></span>

<span data-ttu-id="12bfd-182">I följande exempel visas effekterna av avrundning till närmaste jämna heltal.</span><span class="sxs-lookup"><span data-stu-id="12bfd-182">The following example shows the effect of rounding to the nearest even integer.</span></span>

|<span data-ttu-id="12bfd-183">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-183">Expression</span></span>      |<span data-ttu-id="12bfd-184">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-184">Result</span></span>|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

<span data-ttu-id="12bfd-185">Observera hur **_5/2_ = 2,5** rundas av till **2**.</span><span class="sxs-lookup"><span data-stu-id="12bfd-185">Notice how **_5/2_ = 2.5** gets rounded to **2**.</span></span> <span data-ttu-id="12bfd-186">Men **_7/2_ = 3,5** rundas av till **4**.</span><span class="sxs-lookup"><span data-stu-id="12bfd-186">But, **_7/2_ = 3.5** gets rounded to **4**.</span></span>

<span data-ttu-id="12bfd-187">Du kan använda- `[Math]` klassen för att få olika avrundnings sätt.</span><span class="sxs-lookup"><span data-stu-id="12bfd-187">You can use the `[Math]` class to get different rounding behavior.</span></span>

|                          <span data-ttu-id="12bfd-188">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-188">Expression</span></span>                          | <span data-ttu-id="12bfd-189">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-189">Result</span></span> |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

<span data-ttu-id="12bfd-190">Mer information finns i metoden [Math. Round](/dotnet/api/system.math.round) .</span><span class="sxs-lookup"><span data-stu-id="12bfd-190">For more information, see the [Math.Round](/dotnet/api/system.math.round) method.</span></span>

## <a name="adding-and-multiplying-non-numeric-types"></a><span data-ttu-id="12bfd-191">LÄGGA TILL OCH MULTIPLICERA ICKE-NUMERISKA TYPER</span><span class="sxs-lookup"><span data-stu-id="12bfd-191">ADDING AND MULTIPLYING NON-NUMERIC TYPES</span></span>

<span data-ttu-id="12bfd-192">Du kan lägga till siffror, strängar, matriser och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="12bfd-192">You can add numbers, strings, arrays, and hash tables.</span></span> <span data-ttu-id="12bfd-193">Du kan också multiplicera siffror, strängar och matriser.</span><span class="sxs-lookup"><span data-stu-id="12bfd-193">And, you can multiply numbers, strings, and arrays.</span></span> <span data-ttu-id="12bfd-194">Du kan dock inte multiplicera hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="12bfd-194">However, you cannot multiply hash tables.</span></span>

<span data-ttu-id="12bfd-195">När du lägger till strängar, matriser eller hash-tabeller sammanfogas elementen.</span><span class="sxs-lookup"><span data-stu-id="12bfd-195">When you add strings, arrays, or hash tables, the elements are concatenated.</span></span> <span data-ttu-id="12bfd-196">När du sammanfogar samlingar, till exempel matriser eller hash-tabeller, skapas ett nytt objekt som innehåller objekten från båda samlingarna.</span><span class="sxs-lookup"><span data-stu-id="12bfd-196">When you concatenate collections, such as arrays or hash tables, a new object is created that contains the objects from both collections.</span></span> <span data-ttu-id="12bfd-197">Om du försöker sammanfoga hash-tabeller som har samma nyckel, Miss lyckas åtgärden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-197">If you try to concatenate hash tables that have the same key, the operation fails.</span></span>

<span data-ttu-id="12bfd-198">Följande kommandon skapar till exempel två matriser och lägger till dem:</span><span class="sxs-lookup"><span data-stu-id="12bfd-198">For example, the following commands create two arrays and then add them:</span></span>

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

<span data-ttu-id="12bfd-199">Du kan också utföra aritmetiska åtgärder på objekt av olika typer.</span><span class="sxs-lookup"><span data-stu-id="12bfd-199">You can also perform arithmetic operations on objects of different types.</span></span>
<span data-ttu-id="12bfd-200">Den åtgärd som PowerShell utför bestäms av Microsoft .NET Framework-typen för objektet längst till vänster i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-200">The operation that PowerShell performs is determined by the Microsoft .NET Framework type of the leftmost object in the operation.</span></span> <span data-ttu-id="12bfd-201">PowerShell försöker konvertera alla objekt i åtgärden till den .NET Framework typen för det första objektet.</span><span class="sxs-lookup"><span data-stu-id="12bfd-201">PowerShell tries to convert all the objects in the operation to the .NET Framework type of the first object.</span></span> <span data-ttu-id="12bfd-202">Om det lyckas med att konvertera objekten utför den åtgärden som är lämplig för den .NET Framework typen för det första objektet.</span><span class="sxs-lookup"><span data-stu-id="12bfd-202">If it succeeds in converting the objects, it performs the operation appropriate to the .NET Framework type of the first object.</span></span> <span data-ttu-id="12bfd-203">Åtgärden Miss lyckas om det inte går att konvertera något av objekten.</span><span class="sxs-lookup"><span data-stu-id="12bfd-203">If it fails to convert any of the objects, the operation fails.</span></span>

<span data-ttu-id="12bfd-204">I följande exempel demonstreras användningen av operatorerna addition och multiplikation. i åtgärder som innehåller olika objekt typer.</span><span class="sxs-lookup"><span data-stu-id="12bfd-204">The following examples demonstrate the use of the addition and multiplication operators; in operations that include different object types.</span></span> <span data-ttu-id="12bfd-205">Antag `$array = 1,2,3` :</span><span class="sxs-lookup"><span data-stu-id="12bfd-205">Assume `$array = 1,2,3`:</span></span>

|<span data-ttu-id="12bfd-206">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-206">Expression</span></span>       |<span data-ttu-id="12bfd-207">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-207">Result</span></span>                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |<span data-ttu-id="12bfd-208">`1`,`2`,`3`,`16`</span><span class="sxs-lookup"><span data-stu-id="12bfd-208">`1`,`2`,`3`,`16`</span></span>       |
|`$array + "file"`|<span data-ttu-id="12bfd-209">`1`,`2`,`3`,`file`</span><span class="sxs-lookup"><span data-stu-id="12bfd-209">`1`,`2`,`3`,`file`</span></span>     |
|`$array * 2`     |<span data-ttu-id="12bfd-210">`1`,`2`,`3`,`1`,`2`,`3`</span><span class="sxs-lookup"><span data-stu-id="12bfd-210">`1`,`2`,`3`,`1`,`2`,`3`</span></span>|
|`"file" * 3`     |`filefilefile`         |

<span data-ttu-id="12bfd-211">Eftersom metoden som används för att utvärdera instruktioner bestäms av objektet längst till vänster, är addition och multiplikation i PowerShell inte strikt commutative.</span><span class="sxs-lookup"><span data-stu-id="12bfd-211">Because the method that is used to evaluate statements is determined by the leftmost object, addition and multiplication in PowerShell are not strictly commutative.</span></span> <span data-ttu-id="12bfd-212">Till exempel är `(a + b)` inte alltid lika med `(b + a)` , och `(ab)` är inte alltid lika med `(ba)` .</span><span class="sxs-lookup"><span data-stu-id="12bfd-212">For example, `(a + b)` does not always equal `(b + a)`, and `(ab)` does not always equal `(ba)`.</span></span>

<span data-ttu-id="12bfd-213">Följande exempel visar den här principen:</span><span class="sxs-lookup"><span data-stu-id="12bfd-213">The following examples demonstrate this principle:</span></span>

|<span data-ttu-id="12bfd-214">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-214">Expression</span></span>   |<span data-ttu-id="12bfd-215">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-215">Result</span></span>                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |<span data-ttu-id="12bfd-216">+ 16 + "fil" "</span><span class="sxs-lookup"><span data-stu-id="12bfd-216">+ 16 + "file"\`</span></span>                                       |

<span data-ttu-id="12bfd-217">Hash-tabeller skiljer sig något från versaler.</span><span class="sxs-lookup"><span data-stu-id="12bfd-217">Hash tables are a slightly different case.</span></span> <span data-ttu-id="12bfd-218">Du kan lägga till hash-tabeller i en annan hash-tabell, så länge som de tillagda hash-tabellerna inte har dubbla nycklar.</span><span class="sxs-lookup"><span data-stu-id="12bfd-218">You can add hash tables to another hash table, as long as, the added hash tables don't have duplicate keys.</span></span>

<span data-ttu-id="12bfd-219">I följande exempel visas hur du lägger till hash-tabeller till varandra.</span><span class="sxs-lookup"><span data-stu-id="12bfd-219">The following example show how to add hash tables to each other.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

<span data-ttu-id="12bfd-220">I följande exempel utlöses ett fel eftersom en av nycklarna dupliceras i båda hash-tabellerna.</span><span class="sxs-lookup"><span data-stu-id="12bfd-220">The following example throws an error because one of the keys is duplicated in both hash tables.</span></span>

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

<span data-ttu-id="12bfd-221">Du kan också lägga till en hash-tabell i en matris. Dessutom blir hela hash-tabellen ett objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="12bfd-221">Also, you can add a hash table to an array; and, the entire hash table becomes an item in the array.</span></span>

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

<span data-ttu-id="12bfd-222">Du kan dock inte lägga till någon annan typ i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="12bfd-222">However, you cannot add any other type to a hash table.</span></span>

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

<span data-ttu-id="12bfd-223">Även om addition-operatörerna är mycket användbara använder du tilldelnings operatörerna för att lägga till element i hash-tabeller och matriser.</span><span class="sxs-lookup"><span data-stu-id="12bfd-223">Although the addition operators are very useful, use the assignment operators to add elements to hash tables and arrays.</span></span> <span data-ttu-id="12bfd-224">Mer information finns i [about_assignment_operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="12bfd-224">For more information see [about_assignment_operators](about_Assignment_Operators.md).</span></span> <span data-ttu-id="12bfd-225">I följande exempel används `+=` tilldelnings operatorn för att lägga till objekt i en matris:</span><span class="sxs-lookup"><span data-stu-id="12bfd-225">The following examples use the `+=` assignment operator to add items to an array:</span></span>

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a><span data-ttu-id="12bfd-226">SKRIV KONVERTERING FÖR ATT HANTERA RESULTATET</span><span class="sxs-lookup"><span data-stu-id="12bfd-226">TYPE CONVERSION TO ACCOMMODATE RESULT</span></span>

<span data-ttu-id="12bfd-227">PowerShell väljer automatiskt den .NET Framework numeriska typ som bäst uttrycker resultatet utan att förlora precisionen.</span><span class="sxs-lookup"><span data-stu-id="12bfd-227">PowerShell automatically selects the .NET Framework numeric type that best expresses the result without losing precision.</span></span> <span data-ttu-id="12bfd-228">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="12bfd-228">For example:</span></span>

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

<span data-ttu-id="12bfd-229">Om resultatet av en åtgärd är för stort för typen, utvidgas typen av resultat för att hantera resultatet, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="12bfd-229">If the result of an operation is too large for the type, the type of the result is widened to accommodate the result, as in the following example:</span></span>

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

<span data-ttu-id="12bfd-230">Resultat typen behöver inte nödvändigt vis vara samma som en av operanderna.</span><span class="sxs-lookup"><span data-stu-id="12bfd-230">The type of the result will not necessarily be the same as one of the operands.</span></span> <span data-ttu-id="12bfd-231">I följande exempel kan det negativa värdet inte omvandlas till ett osignerat heltal, och det osignerade heltalet är för stort för att kunna omvandlas till `Int32` :</span><span class="sxs-lookup"><span data-stu-id="12bfd-231">In the following example, the negative value cannot be cast to an unsigned integer, and the unsigned integer is too large to be cast to `Int32`:</span></span>

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

<span data-ttu-id="12bfd-232">I det här exemplet `Int64` kan hantera båda typerna.</span><span class="sxs-lookup"><span data-stu-id="12bfd-232">In this example, `Int64` can accommodate both types.</span></span>

<span data-ttu-id="12bfd-233">`System.Decimal`Typen är ett undantag.</span><span class="sxs-lookup"><span data-stu-id="12bfd-233">The `System.Decimal` type is an exception.</span></span> <span data-ttu-id="12bfd-234">Om någon av operanderna har decimal typen, blir resultatet av decimal typen.</span><span class="sxs-lookup"><span data-stu-id="12bfd-234">If either operand has the Decimal type, the result will be of the Decimal type.</span></span> <span data-ttu-id="12bfd-235">Om resultatet är för stort för decimal typen, kommer det inte att omvandlas till Double.</span><span class="sxs-lookup"><span data-stu-id="12bfd-235">If the result is too large for the Decimal type, it will not be cast to Double.</span></span> <span data-ttu-id="12bfd-236">I stället ett fel resultat.</span><span class="sxs-lookup"><span data-stu-id="12bfd-236">Instead, an error results.</span></span>

|<span data-ttu-id="12bfd-237">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-237">Expression</span></span>               |<span data-ttu-id="12bfd-238">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-238">Result</span></span>                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a><span data-ttu-id="12bfd-239">ARITMETISKA OPERATORER OCH VARIABLER</span><span class="sxs-lookup"><span data-stu-id="12bfd-239">ARITHMETIC OPERATORS AND VARIABLES</span></span>

<span data-ttu-id="12bfd-240">Du kan också använda aritmetiska operatorer med variabler.</span><span class="sxs-lookup"><span data-stu-id="12bfd-240">You can also use arithmetic operators with variables.</span></span> <span data-ttu-id="12bfd-241">Operatorerna fungerar på Variablernas värden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-241">The operators act on the values of the variables.</span></span> <span data-ttu-id="12bfd-242">I följande exempel demonstreras användningen av aritmetiska operatorer med variabler:</span><span class="sxs-lookup"><span data-stu-id="12bfd-242">The following examples demonstrate the use of arithmetic operators with variables:</span></span>

| <span data-ttu-id="12bfd-243">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-243">Expression</span></span>                                    |<span data-ttu-id="12bfd-244">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-244">Result</span></span>      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a><span data-ttu-id="12bfd-245">ARITMETISKA OPERATORER OCH KOMMANDON</span><span class="sxs-lookup"><span data-stu-id="12bfd-245">ARITHMETIC OPERATORS AND COMMANDS</span></span>

<span data-ttu-id="12bfd-246">Normalt använder du aritmetiska operatorer i uttryck med siffror, strängar och matriser.</span><span class="sxs-lookup"><span data-stu-id="12bfd-246">Typically, you use the arithmetic operators in expressions with numbers, strings, and arrays.</span></span> <span data-ttu-id="12bfd-247">Du kan dock också använda aritmetiska operatorer med de objekt som kommandona returnerar och med egenskaperna för dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="12bfd-247">However, you can also use arithmetic operators with the objects that commands return and with the properties of those objects.</span></span>

<span data-ttu-id="12bfd-248">I följande exempel visas hur du använder de aritmetiska operatorerna i uttryck med PowerShell-kommandon:</span><span class="sxs-lookup"><span data-stu-id="12bfd-248">The following examples show how to use the arithmetic operators in expressions with PowerShell commands:</span></span>

```powershell
(get-date) + (new-timespan -day 1)
```

<span data-ttu-id="12bfd-249">Parentes operatorn tvingar fram utvärderingen av `get-date` cmdleten och utvärderingen av `new-timespan -day 1` cmdlet-uttrycket i den ordningen.</span><span class="sxs-lookup"><span data-stu-id="12bfd-249">The parenthesis operator forces the evaluation of the `get-date` cmdlet and the evaluation of the `new-timespan -day 1` cmdlet expression, in that order.</span></span> <span data-ttu-id="12bfd-250">Båda resultaten läggs sedan till med `+` operatorn.</span><span class="sxs-lookup"><span data-stu-id="12bfd-250">Both results are then added using the `+` operator.</span></span>

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

<span data-ttu-id="12bfd-251">I uttrycket ovan multipliceras varje process arbets utrymme ( `$_.ws` ) av `2` och resultatet jämförs med `50mb` för att se om det är större än.</span><span class="sxs-lookup"><span data-stu-id="12bfd-251">In the above expression, each process working space (`$_.ws`) is multiplied by `2`; and, the result, compared against `50mb` to see if it is greater than that.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="12bfd-252">Bitvisa operatorer</span><span class="sxs-lookup"><span data-stu-id="12bfd-252">Bitwise Operators</span></span>

<span data-ttu-id="12bfd-253">PowerShell stöder bitvisa standardoperatorer, inklusive bitvis-AND ( `-bAnd` ), inkluderings-och Exclusive-eller operatorerna ( `-bOr` och `-bXor` ) och bitvis-not ( `-bNot` ).</span><span class="sxs-lookup"><span data-stu-id="12bfd-253">PowerShell supports the standard bitwise operators, including bitwise-AND (`-bAnd`), the inclusive and exclusive bitwise-OR operators (`-bOr` and `-bXor`), and bitwise-NOT (`-bNot`).</span></span>

<span data-ttu-id="12bfd-254">Från och med PowerShell 2,0 fungerar alla bitvisa operatorer med 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="12bfd-254">Beginning in PowerShell 2.0, all bitwise operators work with 64-bit integers.</span></span>

<span data-ttu-id="12bfd-255">Från och med PowerShell 3,0 `-shr` introduceras (Shift-höger) och `-shl` (Shift-Left) för att stödja bitvisa beräkningar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12bfd-255">Beginning in PowerShell 3.0, the `-shr` (shift-right) and `-shl` (shift-left) are introduced to support bitwise arithmetic in PowerShell.</span></span>

<span data-ttu-id="12bfd-256">PowerShell stöder följande bitvisa operatorer.</span><span class="sxs-lookup"><span data-stu-id="12bfd-256">PowerShell supports the following bitwise operators.</span></span>

| <span data-ttu-id="12bfd-257">Operator</span><span class="sxs-lookup"><span data-stu-id="12bfd-257">Operator</span></span> | <span data-ttu-id="12bfd-258">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="12bfd-258">Description</span></span>            | <span data-ttu-id="12bfd-259">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-259">Expression</span></span>   | <span data-ttu-id="12bfd-260">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-260">Result</span></span> |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | <span data-ttu-id="12bfd-261">Bitvis och</span><span class="sxs-lookup"><span data-stu-id="12bfd-261">Bitwise AND</span></span>            | `10 -band 3` | <span data-ttu-id="12bfd-262">2</span><span class="sxs-lookup"><span data-stu-id="12bfd-262">2</span></span>      |
| `-bor`   | <span data-ttu-id="12bfd-263">Bitvis eller (inklusiv)</span><span class="sxs-lookup"><span data-stu-id="12bfd-263">Bitwise OR (inclusive)</span></span> | `10 -bor 3`  | <span data-ttu-id="12bfd-264">11</span><span class="sxs-lookup"><span data-stu-id="12bfd-264">11</span></span>     |
| `-bxor`  | <span data-ttu-id="12bfd-265">Bitvis eller (exklusiv)</span><span class="sxs-lookup"><span data-stu-id="12bfd-265">Bitwise OR (exclusive)</span></span> | `10 -bxor 3` | <span data-ttu-id="12bfd-266">9</span><span class="sxs-lookup"><span data-stu-id="12bfd-266">9</span></span>      |
| `-bnot`  | <span data-ttu-id="12bfd-267">Bitvis NOT</span><span class="sxs-lookup"><span data-stu-id="12bfd-267">Bitwise NOT</span></span>            | `-bNot 10`   | <span data-ttu-id="12bfd-268">-11</span><span class="sxs-lookup"><span data-stu-id="12bfd-268">-11</span></span>    |
| `-shl`   | <span data-ttu-id="12bfd-269">Shift-vänster</span><span class="sxs-lookup"><span data-stu-id="12bfd-269">Shift-left</span></span>             | `102 -shl 2` | <span data-ttu-id="12bfd-270">408</span><span class="sxs-lookup"><span data-stu-id="12bfd-270">408</span></span>    |
| `-shr`   | <span data-ttu-id="12bfd-271">Shift-höger</span><span class="sxs-lookup"><span data-stu-id="12bfd-271">Shift-right</span></span>            | `102 -shr 1` | <span data-ttu-id="12bfd-272">51</span><span class="sxs-lookup"><span data-stu-id="12bfd-272">51</span></span>     |

<span data-ttu-id="12bfd-273">Bitvisa operatorer fungerar som ett värde i binärformat.</span><span class="sxs-lookup"><span data-stu-id="12bfd-273">Bitwise operators act on the binary format of a value.</span></span> <span data-ttu-id="12bfd-274">Bit strukturen för nummer 10 är till exempel 00001010 (baserat på 1 byte) och bit strukturen för talet 3 är 00000011.</span><span class="sxs-lookup"><span data-stu-id="12bfd-274">For example, the bit structure for the number 10 is 00001010 (based on 1 byte), and the bit structure for the number 3 is 00000011.</span></span> <span data-ttu-id="12bfd-275">När du använder en bitvis operator för att jämföra 10 och 3 jämförs de enskilda bitarna i varje byte.</span><span class="sxs-lookup"><span data-stu-id="12bfd-275">When you use a bitwise operator to compare 10 to 3, the individual bits in each byte are compared.</span></span>

<span data-ttu-id="12bfd-276">I en bitvis och-åtgärd anges den resulterande biten till 1 endast när båda indataportarna är 1.</span><span class="sxs-lookup"><span data-stu-id="12bfd-276">In a bitwise AND operation, the resulting bit is set to 1 only when both input bits are 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

<span data-ttu-id="12bfd-277">I en bitvis eller (inklusiv) åtgärd anges den resulterande biten till 1 när antingen eller båda indataportarna är 1.</span><span class="sxs-lookup"><span data-stu-id="12bfd-277">In a bitwise OR (inclusive) operation, the resulting bit is set to 1 when either or both input bits are 1.</span></span> <span data-ttu-id="12bfd-278">Den resulterande biten anges till 0 endast när båda indataportarna anges till 0.</span><span class="sxs-lookup"><span data-stu-id="12bfd-278">The resulting bit is set to 0 only when both input bits are set to 0.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

<span data-ttu-id="12bfd-279">I en bitvis eller (exklusiv) åtgärd anges den resulterande biten till 1 endast när en indataport är 1.</span><span class="sxs-lookup"><span data-stu-id="12bfd-279">In a bitwise OR (exclusive) operation, the resulting bit is set to 1 only when one input bit is 1.</span></span>

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

<span data-ttu-id="12bfd-280">Den bitvis NOT-operatorn är en unär operator som producerar det binära komplettering svärdet.</span><span class="sxs-lookup"><span data-stu-id="12bfd-280">The bitwise NOT operator is a unary operator that produces the binary complement of the value.</span></span> <span data-ttu-id="12bfd-281">Bit-bit 1 är inställd på 0 och biten 0 har värdet 1.</span><span class="sxs-lookup"><span data-stu-id="12bfd-281">A bit of 1 is set to 0 and a bit of 0 is set to 1.</span></span>

<span data-ttu-id="12bfd-282">Till exempel binära komplementet 0 är-1, det maximala osignerade heltalet (0xFFFFFFFF) och det binära komplementet på-1 är 0.</span><span class="sxs-lookup"><span data-stu-id="12bfd-282">For example, the binary complement of 0 is -1, the maximum unsigned integer (0xffffffff), and the binary complement of -1 is 0.</span></span>

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

<span data-ttu-id="12bfd-283">I en bitvis Shift-Left-åtgärd flyttas alla bitar "n" dit till vänster, där "n" är värdet för den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-283">In a bitwise shift-left operation, all bits are moved "n" places to the left, where "n" is the value of the right operand.</span></span> <span data-ttu-id="12bfd-284">En nolla infogas på den plats där de finns.</span><span class="sxs-lookup"><span data-stu-id="12bfd-284">A zero is inserted in the ones place.</span></span>

<span data-ttu-id="12bfd-285">När den vänstra operanden är ett heltals värde (32-bitars) avgör de nedre 5 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.</span><span class="sxs-lookup"><span data-stu-id="12bfd-285">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="12bfd-286">När den vänstra operanden är ett Long (64-bitars) värde, bestämmer de nedre 6 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.</span><span class="sxs-lookup"><span data-stu-id="12bfd-286">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="12bfd-287">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-287">Expression</span></span> |<span data-ttu-id="12bfd-288">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-288">Result</span></span>|<span data-ttu-id="12bfd-289">Binära resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-289">Binary Result</span></span>|
|-----------|------|-------------|
|`21 -shl 0`|<span data-ttu-id="12bfd-290">21</span><span class="sxs-lookup"><span data-stu-id="12bfd-290">21</span></span>    |<span data-ttu-id="12bfd-291">0001 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-291">0001 0101</span></span>    |
|`21 -shl 1`|<span data-ttu-id="12bfd-292">42</span><span class="sxs-lookup"><span data-stu-id="12bfd-292">42</span></span>    |<span data-ttu-id="12bfd-293">0010 1010</span><span class="sxs-lookup"><span data-stu-id="12bfd-293">0010 1010</span></span>    |
|`21 -shl 2`|<span data-ttu-id="12bfd-294">84</span><span class="sxs-lookup"><span data-stu-id="12bfd-294">84</span></span>    |<span data-ttu-id="12bfd-295">0101 0100</span><span class="sxs-lookup"><span data-stu-id="12bfd-295">0101 0100</span></span>    |

<span data-ttu-id="12bfd-296">I en bitvis Shift-höger-åtgärd flyttas alla bitar "n" åt höger, där "n" anges av den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="12bfd-296">In a bitwise shift-right operation, all bits are moved "n" places to the right, where "n" is specified by the right operand.</span></span> <span data-ttu-id="12bfd-297">Shift-höger-operatorn (-SHR) infogar en nolla på platsen längst till vänster när ett positivt eller osignerat värde flyttas till höger.</span><span class="sxs-lookup"><span data-stu-id="12bfd-297">The shift-right operator (-shr) inserts a zero in the left-most place when shifting a positive or unsigned value to the right.</span></span>

<span data-ttu-id="12bfd-298">När den vänstra operanden är ett heltals värde (32-bitars) avgör de nedre 5 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.</span><span class="sxs-lookup"><span data-stu-id="12bfd-298">When the left operand is an Integer (32-bit) value, the lower 5 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

<span data-ttu-id="12bfd-299">När den vänstra operanden är ett Long (64-bitars) värde, bestämmer de nedre 6 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.</span><span class="sxs-lookup"><span data-stu-id="12bfd-299">When the left operand is a Long (64-bit) value, the lower 6 bits of the right operand determine how many bits of the left operand are shifted.</span></span>

|<span data-ttu-id="12bfd-300">Uttryck</span><span class="sxs-lookup"><span data-stu-id="12bfd-300">Expression</span></span>              |<span data-ttu-id="12bfd-301">Resultat</span><span class="sxs-lookup"><span data-stu-id="12bfd-301">Result</span></span>      |<span data-ttu-id="12bfd-302">Binär</span><span class="sxs-lookup"><span data-stu-id="12bfd-302">Binary</span></span>     |<span data-ttu-id="12bfd-303">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="12bfd-303">Hex</span></span>         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | <span data-ttu-id="12bfd-304">21</span><span class="sxs-lookup"><span data-stu-id="12bfd-304">21</span></span>         | <span data-ttu-id="12bfd-305">0001 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-305">0001 0101</span></span> | <span data-ttu-id="12bfd-306">0x15</span><span class="sxs-lookup"><span data-stu-id="12bfd-306">0x15</span></span>       |
|`21 -shr 1`             | <span data-ttu-id="12bfd-307">10</span><span class="sxs-lookup"><span data-stu-id="12bfd-307">10</span></span>         | <span data-ttu-id="12bfd-308">0000 1010</span><span class="sxs-lookup"><span data-stu-id="12bfd-308">0000 1010</span></span> | <span data-ttu-id="12bfd-309">0x0A</span><span class="sxs-lookup"><span data-stu-id="12bfd-309">0x0A</span></span>       |
|`21 -shr 2`             | <span data-ttu-id="12bfd-310">5</span><span class="sxs-lookup"><span data-stu-id="12bfd-310">5</span></span>          | <span data-ttu-id="12bfd-311">0000 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-311">0000 0101</span></span> | <span data-ttu-id="12bfd-312">0x05</span><span class="sxs-lookup"><span data-stu-id="12bfd-312">0x05</span></span>       |
|`21 -shr 31`            | <span data-ttu-id="12bfd-313">0</span><span class="sxs-lookup"><span data-stu-id="12bfd-313">0</span></span>          | <span data-ttu-id="12bfd-314">0000 0000</span><span class="sxs-lookup"><span data-stu-id="12bfd-314">0000 0000</span></span> | <span data-ttu-id="12bfd-315">0x00</span><span class="sxs-lookup"><span data-stu-id="12bfd-315">0x00</span></span>       |
|`21 -shr 32`            | <span data-ttu-id="12bfd-316">21</span><span class="sxs-lookup"><span data-stu-id="12bfd-316">21</span></span>         | <span data-ttu-id="12bfd-317">0001 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-317">0001 0101</span></span> | <span data-ttu-id="12bfd-318">0x15</span><span class="sxs-lookup"><span data-stu-id="12bfd-318">0x15</span></span>       |
|`21 -shr 64`            | <span data-ttu-id="12bfd-319">21</span><span class="sxs-lookup"><span data-stu-id="12bfd-319">21</span></span>         | <span data-ttu-id="12bfd-320">0001 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-320">0001 0101</span></span> | <span data-ttu-id="12bfd-321">0x15</span><span class="sxs-lookup"><span data-stu-id="12bfd-321">0x15</span></span>       |
|`21 -shr 65`            | <span data-ttu-id="12bfd-322">10</span><span class="sxs-lookup"><span data-stu-id="12bfd-322">10</span></span>         | <span data-ttu-id="12bfd-323">0000 1010</span><span class="sxs-lookup"><span data-stu-id="12bfd-323">0000 1010</span></span> | <span data-ttu-id="12bfd-324">0x0A</span><span class="sxs-lookup"><span data-stu-id="12bfd-324">0x0A</span></span>       |
|`21 -shr 66`            | <span data-ttu-id="12bfd-325">5</span><span class="sxs-lookup"><span data-stu-id="12bfd-325">5</span></span>          | <span data-ttu-id="12bfd-326">0000 0101</span><span class="sxs-lookup"><span data-stu-id="12bfd-326">0000 0101</span></span> | <span data-ttu-id="12bfd-327">0x05</span><span class="sxs-lookup"><span data-stu-id="12bfd-327">0x05</span></span>       |
|`[int]::MaxValue -shr 1`| <span data-ttu-id="12bfd-328">1073741823</span><span class="sxs-lookup"><span data-stu-id="12bfd-328">1073741823</span></span> |           | <span data-ttu-id="12bfd-329">0x3FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="12bfd-329">0x3FFFFFFF</span></span> |
|`[int]::MinValue -shr 1`| <span data-ttu-id="12bfd-330">– 1073741824</span><span class="sxs-lookup"><span data-stu-id="12bfd-330">-1073741824</span></span>|           | <span data-ttu-id="12bfd-331">0xC0000000</span><span class="sxs-lookup"><span data-stu-id="12bfd-331">0xC0000000</span></span> |
|`-1 -shr 1`             | <span data-ttu-id="12bfd-332">-1</span><span class="sxs-lookup"><span data-stu-id="12bfd-332">-1</span></span>         |           | <span data-ttu-id="12bfd-333">0xFFFFFFFF</span><span class="sxs-lookup"><span data-stu-id="12bfd-333">0xFFFFFFFF</span></span> |

## <a name="see-also"></a><span data-ttu-id="12bfd-334">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="12bfd-334">SEE ALSO</span></span>

- [<span data-ttu-id="12bfd-335">about_arrays</span><span class="sxs-lookup"><span data-stu-id="12bfd-335">about_arrays</span></span>](about_Arrays.md)
- [<span data-ttu-id="12bfd-336">about_assignment_operators</span><span class="sxs-lookup"><span data-stu-id="12bfd-336">about_assignment_operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="12bfd-337">about_comparison_operators</span><span class="sxs-lookup"><span data-stu-id="12bfd-337">about_comparison_operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="12bfd-338">about_hash_tables</span><span class="sxs-lookup"><span data-stu-id="12bfd-338">about_hash_tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="12bfd-339">about_operators</span><span class="sxs-lookup"><span data-stu-id="12bfd-339">about_operators</span></span>](about_Operators.md)
- [<span data-ttu-id="12bfd-340">about_variables</span><span class="sxs-lookup"><span data-stu-id="12bfd-340">about_variables</span></span>](about_Variables.md)
- [<span data-ttu-id="12bfd-341">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="12bfd-341">Get-Date</span></span>](xref:Microsoft.PowerShell.Utility.Get-Date)
- [<span data-ttu-id="12bfd-342">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="12bfd-342">New-TimeSpan</span></span>](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
