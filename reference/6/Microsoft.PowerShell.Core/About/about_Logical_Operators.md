---
description: Beskriver de operatorer som ansluter instruktioner i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 483217e929d55097b56eade801682ea4484d2624
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273021"
---
# <a name="about_logical_operators"></a><span data-ttu-id="f5277-104">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="f5277-104">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="f5277-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f5277-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f5277-106">Beskriver de operatorer som ansluter instruktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5277-106">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f5277-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f5277-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f5277-108">De logiska PowerShell-operatörerna ansluter uttryck och uttryck, så att du kan använda ett enda uttryck för att testa flera villkor.</span><span class="sxs-lookup"><span data-stu-id="f5277-108">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="f5277-109">Följande uttryck använder till exempel operatorn och och för att ansluta tre villkors satser.</span><span class="sxs-lookup"><span data-stu-id="f5277-109">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="f5277-110">Instruktionen är endast sann när värdet för $a är större än värdet för $b och antingen $a eller $b är mindre än</span><span class="sxs-lookup"><span data-stu-id="f5277-110">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="f5277-111">PowerShell stöder följande logiska operatorer.</span><span class="sxs-lookup"><span data-stu-id="f5277-111">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="f5277-112">Operator</span><span class="sxs-lookup"><span data-stu-id="f5277-112">Operator</span></span>|<span data-ttu-id="f5277-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f5277-113">Description</span></span>                        |<span data-ttu-id="f5277-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="f5277-114">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="f5277-115">Logiska och.</span><span class="sxs-lookup"><span data-stu-id="f5277-115">Logical AND.</span></span> <span data-ttu-id="f5277-116">SANT när båda</span><span class="sxs-lookup"><span data-stu-id="f5277-116">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="f5277-117">-instruktioner är sanna.</span><span class="sxs-lookup"><span data-stu-id="f5277-117">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="f5277-118">Logiskt eller.</span><span class="sxs-lookup"><span data-stu-id="f5277-118">Logical OR.</span></span> <span data-ttu-id="f5277-119">SANT när antingen</span><span class="sxs-lookup"><span data-stu-id="f5277-119">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="f5277-120">instruktionen är TRUE.</span><span class="sxs-lookup"><span data-stu-id="f5277-120">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="f5277-121">Logisk exklusiv eller.</span><span class="sxs-lookup"><span data-stu-id="f5277-121">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="f5277-122">SANT när</span><span class="sxs-lookup"><span data-stu-id="f5277-122">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="f5277-123">endast en instruktion är sann</span><span class="sxs-lookup"><span data-stu-id="f5277-123">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="f5277-124">Logiskt not.</span><span class="sxs-lookup"><span data-stu-id="f5277-124">Logical not.</span></span> <span data-ttu-id="f5277-125">Negerar instruktionen</span><span class="sxs-lookup"><span data-stu-id="f5277-125">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="f5277-126">som följer.</span><span class="sxs-lookup"><span data-stu-id="f5277-126">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="f5277-127">Samma som `-not`</span><span class="sxs-lookup"><span data-stu-id="f5277-127">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="f5277-128">Obs!</span><span class="sxs-lookup"><span data-stu-id="f5277-128">Note:</span></span>

<span data-ttu-id="f5277-129">I de föregående exemplen används även operatorn Equal to `-eq` .</span><span class="sxs-lookup"><span data-stu-id="f5277-129">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="f5277-130">Mer information finns i [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="f5277-130">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="f5277-131">Exemplen använder också booleska värden för heltal.</span><span class="sxs-lookup"><span data-stu-id="f5277-131">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="f5277-132">Heltalet 0 har värdet FALSe.</span><span class="sxs-lookup"><span data-stu-id="f5277-132">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="f5277-133">Alla andra heltal har värdet sant.</span><span class="sxs-lookup"><span data-stu-id="f5277-133">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="f5277-134">De logiska operatorernas syntax är följande:</span><span class="sxs-lookup"><span data-stu-id="f5277-134">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="f5277-135">Instruktioner som använder logiska operatorer returnerar booleska värden (TRUE eller FALSe).</span><span class="sxs-lookup"><span data-stu-id="f5277-135">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="f5277-136">Logiska operatorer för PowerShell utvärderar bara de instruktioner som krävs för att fastställa sanningen-värdet för instruktionen.</span><span class="sxs-lookup"><span data-stu-id="f5277-136">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="f5277-137">Om den vänstra operanden i en instruktion som innehåller operatorn och är FALSe, utvärderas inte den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="f5277-137">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="f5277-138">Om den vänstra operanden i en instruktion som innehåller instruktionen or är TRUE utvärderas inte den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="f5277-138">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="f5277-139">Därför kan du använda dessa instruktioner på samma sätt som du använder `If` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="f5277-139">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5277-140">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="f5277-140">SEE ALSO</span></span>

[<span data-ttu-id="f5277-141">about_Operators</span><span class="sxs-lookup"><span data-stu-id="f5277-141">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="f5277-142">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="f5277-142">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="f5277-143">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="f5277-143">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="f5277-144">about_If</span><span class="sxs-lookup"><span data-stu-id="f5277-144">about_If</span></span>](about_If.md)
