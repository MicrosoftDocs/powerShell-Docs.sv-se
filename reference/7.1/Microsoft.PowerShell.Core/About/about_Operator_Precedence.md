---
description: Visar PowerShell-operatörer i prioritetsordning.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d8b0b3f339739186825b5cb041adba5e06e5d702
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271730"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="8ffe8-104">Om operator prioritet</span><span class="sxs-lookup"><span data-stu-id="8ffe8-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="8ffe8-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8ffe8-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8ffe8-106">Visar PowerShell-operatörer i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="8ffe8-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8ffe8-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="8ffe8-108">Med PowerShell-operatörer kan du skapa enkla, men kraftfulla uttryck.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="8ffe8-109">I det här avsnittet visas operatorerna i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="8ffe8-110">Prioritetsordning är i vilken ordning som PowerShell utvärderar operatorer när flera operatorer visas i samma uttryck.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="8ffe8-111">När operatorer har samma prioritet utvärderar PowerShell dem från vänster till höger som de visas i uttrycket.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="8ffe8-112">Undantagen är tilldelnings operatorer, omvandlings operatorer och negation operatorer ( `!` , `-not` , `-bnot` ) som utvärderas från höger till vänster.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="8ffe8-113">Du kan använda-höljen, till exempel parenteser, för att åsidosätta standard prioritets ordningen och tvinga PowerShell att utvärdera den inneslutna delen av ett uttryck före en icke omsluten del.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="8ffe8-114">I följande lista visas operatörerna i den ordning som de utvärderas.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="8ffe8-115">Operatorer på samma rad eller i samma grupp har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="8ffe8-116">Operator-kolumnen visar operatorerna.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-116">The Operator column lists the operators.</span></span> <span data-ttu-id="8ffe8-117">Referens kolumnen visar PowerShell-hjälp avsnittet där operatorn beskrivs.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="8ffe8-118">Om du vill visa avsnittet skriver du `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="8ffe8-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="8ffe8-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="8ffe8-119">OPERATOR</span></span>         |           <span data-ttu-id="8ffe8-120">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="8ffe8-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | <span data-ttu-id="8ffe8-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-122">`. ?.` (medlems åtkomst)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-122">`. ?.` (member access)</span></span>   | <span data-ttu-id="8ffe8-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-124">`::` oföränderlig</span><span class="sxs-lookup"><span data-stu-id="8ffe8-124">`::` (static)</span></span>            | <span data-ttu-id="8ffe8-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-126">`[0] ?[0]` (index operator)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-126">`[0] ?[0]` (index operator)</span></span> | <span data-ttu-id="8ffe8-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-127">[about_Operators][]</span></span>         |
| <span data-ttu-id="8ffe8-128">`[int]` (Cast-operatorer)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="8ffe8-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-130">`-split` Operator</span><span class="sxs-lookup"><span data-stu-id="8ffe8-130">`-split` (unary)</span></span>         | <span data-ttu-id="8ffe8-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-131">[about_Split][]</span></span>                |
| <span data-ttu-id="8ffe8-132">`-join` Operator</span><span class="sxs-lookup"><span data-stu-id="8ffe8-132">`-join` (unary)</span></span>          | <span data-ttu-id="8ffe8-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="8ffe8-134">`,` (komma operator)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-134">`,` (comma operator)</span></span>     | <span data-ttu-id="8ffe8-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="8ffe8-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="8ffe8-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="8ffe8-138">`..` (intervall operator)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-138">`..` (range operator)</span></span>    | <span data-ttu-id="8ffe8-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-140">`-f` (format operator)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-140">`-f` (format operator)</span></span>   | <span data-ttu-id="8ffe8-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-142">`-` (enställig/negativ)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="8ffe8-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="8ffe8-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="8ffe8-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="8ffe8-146">Följande grupp med operatorer har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="8ffe8-147">De Skift läges känsliga och Skift läges känsliga varianterna har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="8ffe8-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="8ffe8-148">OPERATOR</span></span>          |           <span data-ttu-id="8ffe8-149">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="8ffe8-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="8ffe8-150">`-split` binär</span><span class="sxs-lookup"><span data-stu-id="8ffe8-150">`-split` (binary)</span></span>         | <span data-ttu-id="8ffe8-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-151">[about_Split][]</span></span>                |
| <span data-ttu-id="8ffe8-152">`-join` binär</span><span class="sxs-lookup"><span data-stu-id="8ffe8-152">`-join` (binary)</span></span>          | <span data-ttu-id="8ffe8-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="8ffe8-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="8ffe8-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="8ffe8-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="8ffe8-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="8ffe8-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="8ffe8-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="8ffe8-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="8ffe8-161">Listan återupptas här med följande operatorer i prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="8ffe8-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="8ffe8-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="8ffe8-162">OPERATOR</span></span>                 |           <span data-ttu-id="8ffe8-163">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="8ffe8-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="8ffe8-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="8ffe8-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="8ffe8-166">Följande objekt är inte sanna operatorer.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-166">The following items are not true operators.</span></span> <span data-ttu-id="8ffe8-167">De är en del av PowerShell-kommandosyntaxen, inte uttrycks syntax.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="8ffe8-168">Tilldelning är alltid den senaste åtgärd som inträffar.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="8ffe8-169">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ffe8-169">SYNTAX</span></span>                   |           <span data-ttu-id="8ffe8-170">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="8ffe8-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="8ffe8-171">`.` (punkt-källa)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="8ffe8-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-173">`&` kontakt</span><span class="sxs-lookup"><span data-stu-id="8ffe8-173">`&` (call)</span></span>                              | <span data-ttu-id="8ffe8-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-175">`? <if-true> : <if-false>` (Ternär operatör)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-175">`? <if-true> : <if-false>` (Ternary operator)</span></span> | <span data-ttu-id="8ffe8-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-176">[about_Operators][]</span></span>      |
| <span data-ttu-id="8ffe8-177">`??` (null-operatorer)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-177">`??` (null-coalese operator)</span></span>            | <span data-ttu-id="8ffe8-178">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-178">[about_Operators][]</span></span>            |
| <span data-ttu-id="8ffe8-179"><code>&#124;</code> (pipeline-operator)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-179"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="8ffe8-180">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-180">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="8ffe8-181">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-181">[about_Redirection][]</span></span>          |
| <span data-ttu-id="8ffe8-182"><code>&& &#124;&#124;</code> (pipelines kedje operatorer)</span><span class="sxs-lookup"><span data-stu-id="8ffe8-182"><code>&& &#124;&#124;</code> (pipeline chain operators)</span></span> | <span data-ttu-id="8ffe8-183">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-183">[about_Operators][]</span></span> |
| `= += -= *= /= %= ??=`                  | <span data-ttu-id="8ffe8-184">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-184">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="8ffe8-185">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8ffe8-185">EXAMPLES</span></span>

<span data-ttu-id="8ffe8-186">Följande två kommandon visar de aritmetiska operatorerna och effekterna av att använda parenteser för att tvinga PowerShell att utvärdera den omslutna delen av uttrycket först.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-186">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="8ffe8-187">I följande exempel hämtas de skrivskyddade textfilerna från den lokala katalogen och sparas i `$read_only` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-187">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="8ffe8-188">Det motsvarar följande exempel.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-188">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="8ffe8-189">Eftersom pipeline-operatorn ( `|` ) har högre prioritet än tilldelnings operatorn ( `=` ) skickas filerna som `Get-ChildItem` cmdleten hämtar till `Where-Object` cmdleten för filtrering innan de tilldelas till `$read_only` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-189">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="8ffe8-190">Följande exempel visar att index operatorn har företräde framför omvandlings operatorn.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-190">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="8ffe8-191">Det här uttrycket skapar en matris med tre strängar.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-191">This expression creates an array of three strings.</span></span> <span data-ttu-id="8ffe8-192">Sedan använder den index operatorn med värdet 0 för att välja det första objektet i matrisen, som är den första strängen.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-192">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="8ffe8-193">Slutligen skickar den det valda objektet som en sträng.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-193">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="8ffe8-194">I det här fallet har Casten ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-194">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="8ffe8-195">Det här uttrycket använder parenteser för att tvinga Cast-åtgärden att ske före index valet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-195">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="8ffe8-196">Därför omvandlas hela matrisen som en (enkel) sträng.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-196">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="8ffe8-197">Sedan väljer index operatorn det första objektet i sträng mat ris, vilket är det första tecken.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-197">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="8ffe8-198">I följande exempel, eftersom `-gt` operatorn (större än) har en högre prioritet än `-and` operatorn (logisk och), är resultatet av uttrycket falskt.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-198">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="8ffe8-199">Det motsvarar följande uttryck.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-199">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="8ffe8-200">Om-och-operatorn har högre prioritet skulle svaret vara sant.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-200">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="8ffe8-201">Det här exemplet visar dock en viktig princip för att hantera operatörs prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-201">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="8ffe8-202">När ett uttryck är svårt för användare att tolka, använder du parenteser för att tvinga fram utvärderings ordningen, även om den tvingar standard operatorn prioritet.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-202">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="8ffe8-203">Parenteserna gör dina avsikter tydliga för personer som läser och underhåller dina skript.</span><span class="sxs-lookup"><span data-stu-id="8ffe8-203">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ffe8-204">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="8ffe8-204">SEE ALSO</span></span>

<span data-ttu-id="8ffe8-205">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-205">[about_Operators][]</span></span>

<span data-ttu-id="8ffe8-206">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-206">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="8ffe8-207">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-207">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="8ffe8-208">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-208">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="8ffe8-209">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-209">[about_Join][]</span></span>

<span data-ttu-id="8ffe8-210">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-210">[about_Redirection][]</span></span>

<span data-ttu-id="8ffe8-211">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-211">[about_Scopes][]</span></span>

<span data-ttu-id="8ffe8-212">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-212">[about_Split][]</span></span>

<span data-ttu-id="8ffe8-213">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="8ffe8-213">[about_Type_Operators][]</span></span>

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
