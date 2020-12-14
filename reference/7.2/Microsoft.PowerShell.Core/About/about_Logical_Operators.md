---
description: Beskriver de operatorer som ansluter instruktioner i PowerShell.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 8602551f3ecf74027b59715e1f47aab1b10bea92
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708474"
---
# <a name="about_logical_operators"></a><span data-ttu-id="91adb-103">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="91adb-103">about_Logical_Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="91adb-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="91adb-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="91adb-105">Beskriver de operatorer som ansluter instruktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="91adb-105">Describes the operators that connect statements in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="91adb-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="91adb-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="91adb-107">De logiska PowerShell-operatörerna ansluter uttryck och uttryck, så att du kan använda ett enda uttryck för att testa flera villkor.</span><span class="sxs-lookup"><span data-stu-id="91adb-107">The PowerShell logical operators connect expressions and statements, allowing you to use a single expression to test for multiple conditions.</span></span>

<span data-ttu-id="91adb-108">Följande uttryck använder till exempel operatorn och och för att ansluta tre villkors satser.</span><span class="sxs-lookup"><span data-stu-id="91adb-108">For example, the following statement uses the and operator and the or operator to connect three conditional statements.</span></span> <span data-ttu-id="91adb-109">Instruktionen är endast sann när värdet för $a är större än värdet för $b och antingen $a eller $b är mindre än</span><span class="sxs-lookup"><span data-stu-id="91adb-109">The statement is true only when the value of $a is greater than the value of $b, and either $a or $b is less than</span></span>
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

<span data-ttu-id="91adb-110">PowerShell stöder följande logiska operatorer.</span><span class="sxs-lookup"><span data-stu-id="91adb-110">PowerShell supports the following logical operators.</span></span>

|<span data-ttu-id="91adb-111">Operator</span><span class="sxs-lookup"><span data-stu-id="91adb-111">Operator</span></span>|<span data-ttu-id="91adb-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="91adb-112">Description</span></span>                        |<span data-ttu-id="91adb-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="91adb-113">Example</span></span>                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |<span data-ttu-id="91adb-114">Logiska och.</span><span class="sxs-lookup"><span data-stu-id="91adb-114">Logical AND.</span></span> <span data-ttu-id="91adb-115">SANT när båda</span><span class="sxs-lookup"><span data-stu-id="91adb-115">TRUE when both</span></span>        |`(1 -eq 1) -and (1 -eq 2)`|
|        |<span data-ttu-id="91adb-116">-instruktioner är sanna.</span><span class="sxs-lookup"><span data-stu-id="91adb-116">statements are TRUE.</span></span>               |`False`                   |
|`-or`   |<span data-ttu-id="91adb-117">Logiskt eller.</span><span class="sxs-lookup"><span data-stu-id="91adb-117">Logical OR.</span></span> <span data-ttu-id="91adb-118">SANT när antingen</span><span class="sxs-lookup"><span data-stu-id="91adb-118">TRUE when either</span></span>       |`(1 -eq 1) -or (1 -eq 2)` |
|        |<span data-ttu-id="91adb-119">instruktionen är TRUE.</span><span class="sxs-lookup"><span data-stu-id="91adb-119">statement is TRUE.</span></span>                 |`True`                    |
|`-xor`  |<span data-ttu-id="91adb-120">Logisk exklusiv eller.</span><span class="sxs-lookup"><span data-stu-id="91adb-120">Logical EXCLUSIVE OR.</span></span> <span data-ttu-id="91adb-121">SANT när</span><span class="sxs-lookup"><span data-stu-id="91adb-121">TRUE when</span></span>    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |<span data-ttu-id="91adb-122">endast en instruktion är sann</span><span class="sxs-lookup"><span data-stu-id="91adb-122">only one statement is TRUE</span></span>         |`False`                   |
|`-not`  |<span data-ttu-id="91adb-123">Logiskt not.</span><span class="sxs-lookup"><span data-stu-id="91adb-123">Logical not.</span></span> <span data-ttu-id="91adb-124">Negerar instruktionen</span><span class="sxs-lookup"><span data-stu-id="91adb-124">Negates the statement</span></span> |`-not (1 -eq 1)`          |
|        |<span data-ttu-id="91adb-125">som följer.</span><span class="sxs-lookup"><span data-stu-id="91adb-125">that follows.</span></span>                      |`False`                   |
|`!`     |<span data-ttu-id="91adb-126">Samma som `-not`</span><span class="sxs-lookup"><span data-stu-id="91adb-126">Same as `-not`</span></span>                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 <span data-ttu-id="91adb-127">Obs!</span><span class="sxs-lookup"><span data-stu-id="91adb-127">Note:</span></span>

<span data-ttu-id="91adb-128">I de föregående exemplen används även operatorn Equal to `-eq` .</span><span class="sxs-lookup"><span data-stu-id="91adb-128">The previous examples also use the equal to comparison operator `-eq`.</span></span> <span data-ttu-id="91adb-129">Mer information finns i [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="91adb-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span> <span data-ttu-id="91adb-130">Exemplen använder också booleska värden för heltal.</span><span class="sxs-lookup"><span data-stu-id="91adb-130">The examples also use the Boolean values of integers.</span></span> <span data-ttu-id="91adb-131">Heltalet 0 har värdet FALSe.</span><span class="sxs-lookup"><span data-stu-id="91adb-131">The integer 0 has a value of FALSE.</span></span> <span data-ttu-id="91adb-132">Alla andra heltal har värdet sant.</span><span class="sxs-lookup"><span data-stu-id="91adb-132">All other integers have a value of TRUE.</span></span>

<span data-ttu-id="91adb-133">De logiska operatorernas syntax är följande:</span><span class="sxs-lookup"><span data-stu-id="91adb-133">The syntax of the logical operators is as follows:</span></span>

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

<span data-ttu-id="91adb-134">Instruktioner som använder logiska operatorer returnerar booleska värden (TRUE eller FALSe).</span><span class="sxs-lookup"><span data-stu-id="91adb-134">Statements that use the logical operators return Boolean (TRUE or FALSE) values.</span></span>

<span data-ttu-id="91adb-135">Logiska operatorer för PowerShell utvärderar bara de instruktioner som krävs för att fastställa sanningen-värdet för instruktionen.</span><span class="sxs-lookup"><span data-stu-id="91adb-135">The PowerShell logical operators evaluate only the statements required to determine the truth value of the statement.</span></span> <span data-ttu-id="91adb-136">Om den vänstra operanden i en instruktion som innehåller operatorn och är FALSe, utvärderas inte den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="91adb-136">If the left operand in a statement that contains the and operator is FALSE, the right operand is not evaluated.</span></span>
<span data-ttu-id="91adb-137">Om den vänstra operanden i en instruktion som innehåller instruktionen or är TRUE utvärderas inte den högra operanden.</span><span class="sxs-lookup"><span data-stu-id="91adb-137">If the left operand in a statement that contains the or statement is TRUE, the right operand is not evaluated.</span></span> <span data-ttu-id="91adb-138">Därför kan du använda dessa instruktioner på samma sätt som du använder `If` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="91adb-138">As a result, you can use these statements in the same way that you would use the `If` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="91adb-139">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="91adb-139">SEE ALSO</span></span>

[<span data-ttu-id="91adb-140">about_Operators</span><span class="sxs-lookup"><span data-stu-id="91adb-140">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="91adb-141">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="91adb-141">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)

[<span data-ttu-id="91adb-142">about_Comparison_operators</span><span class="sxs-lookup"><span data-stu-id="91adb-142">about_Comparison_operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="91adb-143">about_If</span><span class="sxs-lookup"><span data-stu-id="91adb-143">about_If</span></span>](about_If.md)

