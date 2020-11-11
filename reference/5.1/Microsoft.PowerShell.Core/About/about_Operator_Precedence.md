---
description: Visar PowerShell-operatörer i prioritetsordning.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: 27cc1be95067a38e6c210b37a3398416d0845846
ms.sourcegitcommit: 768816a5c05cc2d07ffd84bed95b0499f4b49f2d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483051"
---
# <a name="about-operator-precedence"></a><span data-ttu-id="b8ff9-104">Om operator prioritet</span><span class="sxs-lookup"><span data-stu-id="b8ff9-104">About Operator Precedence</span></span>

## <a name="short-description"></a><span data-ttu-id="b8ff9-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8ff9-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b8ff9-106">Visar PowerShell-operatörer i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-106">Lists the PowerShell operators in precedence order.</span></span>

## <a name="long-description"></a><span data-ttu-id="b8ff9-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b8ff9-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b8ff9-108">Med PowerShell-operatörer kan du skapa enkla, men kraftfulla uttryck.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-108">PowerShell operators let you construct simple, but powerful expressions.</span></span> <span data-ttu-id="b8ff9-109">I det här avsnittet visas operatorerna i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-109">This topic lists the operators in precedence order.</span></span> <span data-ttu-id="b8ff9-110">Prioritetsordning är i vilken ordning som PowerShell utvärderar operatorer när flera operatorer visas i samma uttryck.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-110">Precedence order is the order in which PowerShell evaluates the operators when multiple operators appear in the same expression.</span></span>

<span data-ttu-id="b8ff9-111">När operatorer har samma prioritet utvärderar PowerShell dem från vänster till höger som de visas i uttrycket.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-111">When operators have equal precedence, PowerShell evaluates them from left to right as they appear within the expression.</span></span> <span data-ttu-id="b8ff9-112">Undantagen är tilldelnings operatorer, omvandlings operatorer och negation operatorer ( `!` , `-not` , `-bnot` ) som utvärderas från höger till vänster.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-112">The exceptions are the assignment operators, the cast operators, and the negation operators (`!`, `-not`, `-bnot`), which are evaluated from right to left.</span></span>

<span data-ttu-id="b8ff9-113">Du kan använda-höljen, till exempel parenteser, för att åsidosätta standard prioritets ordningen och tvinga PowerShell att utvärdera den inneslutna delen av ett uttryck före en icke omsluten del.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-113">You can use enclosures, such as parentheses, to override the standard precedence order and force PowerShell to evaluate the enclosed part of an expression before an unenclosed part.</span></span>

<span data-ttu-id="b8ff9-114">I följande lista visas operatörerna i den ordning som de utvärderas.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-114">In the following list, operators are listed in the order that they are evaluated.</span></span> <span data-ttu-id="b8ff9-115">Operatorer på samma rad eller i samma grupp har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-115">Operators on the same line, or in the same group, have equal precedence.</span></span>

<span data-ttu-id="b8ff9-116">Operator-kolumnen visar operatorerna.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-116">The Operator column lists the operators.</span></span> <span data-ttu-id="b8ff9-117">Referens kolumnen visar PowerShell-hjälp avsnittet där operatorn beskrivs.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-117">The Reference column lists the PowerShell Help topic in which the operator is described.</span></span> <span data-ttu-id="b8ff9-118">Om du vill visa avsnittet skriver du `get-help <topic-name>` .</span><span class="sxs-lookup"><span data-stu-id="b8ff9-118">To display the topic, type `get-help <topic-name>`.</span></span>

|         <span data-ttu-id="b8ff9-119">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="b8ff9-119">OPERATOR</span></span>         |           <span data-ttu-id="b8ff9-120">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="b8ff9-120">REFERENCE</span></span>            |
| ------------------------ | ------------------------------ |
| `$() @() () @{}`         | <span data-ttu-id="b8ff9-121">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-121">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-122">`.` (medlems åtkomst)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-122">`.` (member access)</span></span>      | <span data-ttu-id="b8ff9-123">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-123">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-124">`::` oföränderlig</span><span class="sxs-lookup"><span data-stu-id="b8ff9-124">`::` (static)</span></span>            | <span data-ttu-id="b8ff9-125">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-125">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-126">`[0]` (index operator)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-126">`[0]` (index operator)</span></span>   | <span data-ttu-id="b8ff9-127">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-127">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-128">`[int]` (Cast-operatorer)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-128">`[int]` (cast operators)</span></span> | <span data-ttu-id="b8ff9-129">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-129">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-130">`-split` Operator</span><span class="sxs-lookup"><span data-stu-id="b8ff9-130">`-split` (unary)</span></span>         | <span data-ttu-id="b8ff9-131">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-131">[about_Split][]</span></span>                |
| <span data-ttu-id="b8ff9-132">`-join` Operator</span><span class="sxs-lookup"><span data-stu-id="b8ff9-132">`-join` (unary)</span></span>          | <span data-ttu-id="b8ff9-133">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-133">[about_Join][]</span></span>                 |
| <span data-ttu-id="b8ff9-134">`,` (komma operator)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-134">`,` (comma operator)</span></span>     | <span data-ttu-id="b8ff9-135">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-135">[about_Operators][]</span></span>            |
| `++ --`                  | <span data-ttu-id="b8ff9-136">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-136">[about_Assignment_Operators][]</span></span> |
| `! -not`                 | <span data-ttu-id="b8ff9-137">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-137">[about_Logical_Operators][]</span></span>    |
| <span data-ttu-id="b8ff9-138">`..` (intervall operator)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-138">`..` (range operator)</span></span>    | <span data-ttu-id="b8ff9-139">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-139">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-140">`-f` (format operator)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-140">`-f` (format operator)</span></span>   | <span data-ttu-id="b8ff9-141">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-141">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-142">`-` (enställig/negativ)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-142">`-` (unary/negative)</span></span>     | <span data-ttu-id="b8ff9-143">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-143">[about_Arithmetic_Operators][]</span></span> |
| `* / %`                  | <span data-ttu-id="b8ff9-144">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-144">[about_Arithmetic_Operators][]</span></span> |
| `+ -`                    | <span data-ttu-id="b8ff9-145">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-145">[about_Arithmetic_Operators][]</span></span> |

<span data-ttu-id="b8ff9-146">Följande grupp med operatorer har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-146">The following group of operators have equal precedence.</span></span> <span data-ttu-id="b8ff9-147">De Skift läges känsliga och Skift läges känsliga varianterna har samma prioritet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-147">Their case-sensitive and explicitly case-insensitive variants have the same precedence.</span></span>

|         <span data-ttu-id="b8ff9-148">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="b8ff9-148">OPERATOR</span></span>          |           <span data-ttu-id="b8ff9-149">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="b8ff9-149">REFERENCE</span></span>            |
| ------------------------- | ------------------------------ |
| <span data-ttu-id="b8ff9-150">`-split` binär</span><span class="sxs-lookup"><span data-stu-id="b8ff9-150">`-split` (binary)</span></span>         | <span data-ttu-id="b8ff9-151">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-151">[about_Split][]</span></span>                |
| <span data-ttu-id="b8ff9-152">`-join` binär</span><span class="sxs-lookup"><span data-stu-id="b8ff9-152">`-join` (binary)</span></span>          | <span data-ttu-id="b8ff9-153">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-153">[about_Join][]</span></span>                 |
| `-is -isnot -as`          | <span data-ttu-id="b8ff9-154">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-154">[about_Type_Operators][]</span></span>       |
| `-eq -ne -gt -gt -lt -le` | <span data-ttu-id="b8ff9-155">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-155">[about_Comparison_Operators][]</span></span> |
| `-like -notlike`          | <span data-ttu-id="b8ff9-156">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-156">[about_Comparison_Operators][]</span></span> |
| `-match -notmatch`        | <span data-ttu-id="b8ff9-157">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-157">[about_Comparison_Operators][]</span></span> |
| `-in -notIn`              | <span data-ttu-id="b8ff9-158">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-158">[about_Comparison_Operators][]</span></span> |
| `-contains -notContains`  | <span data-ttu-id="b8ff9-159">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-159">[about_Comparison_Operators][]</span></span> |
| `-replace`                | <span data-ttu-id="b8ff9-160">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-160">[about_Comparison_Operators][]</span></span> |

<span data-ttu-id="b8ff9-161">Listan återupptas här med följande operatorer i prioritetsordning:</span><span class="sxs-lookup"><span data-stu-id="b8ff9-161">The list resumes here with the following operators in precedence order:</span></span>

|                <span data-ttu-id="b8ff9-162">OPERATOR</span><span class="sxs-lookup"><span data-stu-id="b8ff9-162">OPERATOR</span></span>                 |           <span data-ttu-id="b8ff9-163">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="b8ff9-163">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | <span data-ttu-id="b8ff9-164">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-164">[about_Arithmetic_Operators][]</span></span> |
| `-and -or -xor`                         | <span data-ttu-id="b8ff9-165">[about_Logical_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-165">[about_Logical_Operators][]</span></span>    |

<span data-ttu-id="b8ff9-166">Följande objekt är inte sanna operatorer.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-166">The following items are not true operators.</span></span> <span data-ttu-id="b8ff9-167">De är en del av PowerShell-kommandosyntaxen, inte uttrycks syntax.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-167">They are part of PowerShell's command syntax, not expression syntax.</span></span> <span data-ttu-id="b8ff9-168">Tilldelning är alltid den senaste åtgärd som inträffar.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-168">Assignment is always the last action that happens.</span></span>

|                <span data-ttu-id="b8ff9-169">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8ff9-169">SYNTAX</span></span>                   |           <span data-ttu-id="b8ff9-170">FÖRHÅLLANDE</span><span class="sxs-lookup"><span data-stu-id="b8ff9-170">REFERENCE</span></span>            |
| --------------------------------------- | ------------------------------ |
| <span data-ttu-id="b8ff9-171">`.` (punkt-källa)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-171">`.` (dot-source)</span></span>                        | <span data-ttu-id="b8ff9-172">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-172">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-173">`&` kontakt</span><span class="sxs-lookup"><span data-stu-id="b8ff9-173">`&` (call)</span></span>                              | <span data-ttu-id="b8ff9-174">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-174">[about_Operators][]</span></span>            |
| <span data-ttu-id="b8ff9-175"><code>&#124;</code> (pipeline-operator)</span><span class="sxs-lookup"><span data-stu-id="b8ff9-175"><code>&#124;</code> (pipeline operator)</span></span> | <span data-ttu-id="b8ff9-176">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-176">[about_Operators][]</span></span>            |
| `> >> 2> 2>> 2>&1`                      | <span data-ttu-id="b8ff9-177">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-177">[about_Redirection][]</span></span>          |
| `= += -= *= /= %=`                      | <span data-ttu-id="b8ff9-178">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-178">[about_Assignment_Operators][]</span></span> |

## <a name="examples"></a><span data-ttu-id="b8ff9-179">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b8ff9-179">EXAMPLES</span></span>

<span data-ttu-id="b8ff9-180">Följande två kommandon visar de aritmetiska operatorerna och effekterna av att använda parenteser för att tvinga PowerShell att utvärdera den omslutna delen av uttrycket först.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-180">The following two commands show the arithmetic operators and the effect of using parentheses to force PowerShell to evaluate the enclosed part of the expression first.</span></span>

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

<span data-ttu-id="b8ff9-181">I följande exempel hämtas de skrivskyddade textfilerna från den lokala katalogen och sparas i `$read_only` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-181">The following example gets the read-only text files from the local directory and saves them in the `$read_only` variable.</span></span>

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

<span data-ttu-id="b8ff9-182">Det motsvarar följande exempel.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-182">It is equivalent to the following example.</span></span>

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

<span data-ttu-id="b8ff9-183">Eftersom pipeline-operatorn ( `|` ) har högre prioritet än tilldelnings operatorn ( `=` ) skickas filerna som `Get-ChildItem` cmdleten hämtar till `Where-Object` cmdleten för filtrering innan de tilldelas till `$read_only` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-183">Because the pipeline operator (`|`) has a higher precedence than the assignment operator (`=`), the files that the `Get-ChildItem` cmdlet gets are sent to the `Where-Object` cmdlet for filtering before they are assigned to the `$read_only` variable.</span></span>

<span data-ttu-id="b8ff9-184">Följande exempel visar att index operatorn har företräde framför omvandlings operatorn.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-184">The following example demonstrates that the index operator takes precedence over the cast operator.</span></span>

<span data-ttu-id="b8ff9-185">Det här uttrycket skapar en matris med tre strängar.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-185">This expression creates an array of three strings.</span></span> <span data-ttu-id="b8ff9-186">Sedan använder den index operatorn med värdet 0 för att välja det första objektet i matrisen, som är den första strängen.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-186">Then, it uses the index operator with a value of 0 to select the first object in the array, which is the first string.</span></span> <span data-ttu-id="b8ff9-187">Slutligen skickar den det valda objektet som en sträng.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-187">Finally, it casts the selected object as a string.</span></span> <span data-ttu-id="b8ff9-188">I det här fallet har Casten ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-188">In this case, the cast has no effect.</span></span>

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

<span data-ttu-id="b8ff9-189">Det här uttrycket använder parenteser för att tvinga Cast-åtgärden att ske före index valet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-189">This expression uses parentheses to force the cast operation to occur before the index selection.</span></span> <span data-ttu-id="b8ff9-190">Därför omvandlas hela matrisen som en (enkel) sträng.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-190">As a result, the entire array is cast as a (single) string.</span></span> <span data-ttu-id="b8ff9-191">Sedan väljer index operatorn det första objektet i sträng mat ris, vilket är det första tecken.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-191">Then, the index operator selects the first item in the string array, which is the first character.</span></span>

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

<span data-ttu-id="b8ff9-192">I följande exempel, eftersom `-gt` operatorn (större än) har en högre prioritet än `-and` operatorn (logisk och), är resultatet av uttrycket falskt.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-192">In the following example, because the `-gt` (greater-than) operator has a higher precedence than the `-and` (logical AND) operator, the result of the expression is FALSE.</span></span>

```powershell
PS> 2 -gt 4 -and 1
False
```

<span data-ttu-id="b8ff9-193">Det motsvarar följande uttryck.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-193">It is equivalent to the following expression.</span></span>

```powershell
PS> (2 -gt 4) -and 1
False
```

<span data-ttu-id="b8ff9-194">Om-och-operatorn har högre prioritet skulle svaret vara sant.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-194">If the -and operator had higher precedence, the answer would be TRUE.</span></span>

```powershell
PS> 2 -gt (4 -and 1)
True
```

<span data-ttu-id="b8ff9-195">Det här exemplet visar dock en viktig princip för att hantera operatörs prioritet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-195">However, this example demonstrates an important principle of managing operator precedence.</span></span> <span data-ttu-id="b8ff9-196">När ett uttryck är svårt för användare att tolka, använder du parenteser för att tvinga fram utvärderings ordningen, även om den tvingar standard operatorn prioritet.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-196">When an expression is difficult for people to interpret, use parentheses to force the evaluation order, even when it forces the default operator precedence.</span></span> <span data-ttu-id="b8ff9-197">Parenteserna gör dina avsikter tydliga för personer som läser och underhåller dina skript.</span><span class="sxs-lookup"><span data-stu-id="b8ff9-197">The parentheses make your intentions clear to people who are reading and maintaining your scripts.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8ff9-198">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="b8ff9-198">SEE ALSO</span></span>

<span data-ttu-id="b8ff9-199">[about_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-199">[about_Operators][]</span></span>

<span data-ttu-id="b8ff9-200">[about_Assignment_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-200">[about_Assignment_Operators][]</span></span>

<span data-ttu-id="b8ff9-201">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-201">[about_Comparison_Operators][]</span></span>

<span data-ttu-id="b8ff9-202">[about_Arithmetic_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-202">[about_Arithmetic_Operators][]</span></span>

<span data-ttu-id="b8ff9-203">[about_Join][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-203">[about_Join][]</span></span>

<span data-ttu-id="b8ff9-204">[about_Redirection][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-204">[about_Redirection][]</span></span>

<span data-ttu-id="b8ff9-205">[about_Scopes][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-205">[about_Scopes][]</span></span>

<span data-ttu-id="b8ff9-206">[about_Split][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-206">[about_Split][]</span></span>

<span data-ttu-id="b8ff9-207">[about_Type_Operators][]</span><span class="sxs-lookup"><span data-stu-id="b8ff9-207">[about_Type_Operators][]</span></span>

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
