---
description: Beskriver hur `continue` instruktionen omedelbart returnerar program flödet överst i en program slinga, en `switch` instruktion eller en `trap` instruktion.
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 96758fb110ec1496ebbc073cdacfd3dcc15ae486
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614089"
---
# <a name="about-continue"></a><span data-ttu-id="04972-104">Om Fortsätt</span><span class="sxs-lookup"><span data-stu-id="04972-104">About Continue</span></span>

## <a name="short-description"></a><span data-ttu-id="04972-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="04972-105">Short description</span></span>

<span data-ttu-id="04972-106">Beskriver hur `continue` instruktionen omedelbart returnerar program flödet överst i en program slinga, en `switch` instruktion eller en `trap` instruktion.</span><span class="sxs-lookup"><span data-stu-id="04972-106">Describes how the `continue` statement immediately returns the program flow to the top of a program loop, a `switch` statement, or a `trap` statement.</span></span>

## <a name="long-description"></a><span data-ttu-id="04972-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="04972-107">Long description</span></span>

<span data-ttu-id="04972-108">`continue`Instruktionen gör det möjligt att avsluta det aktuella kontroll blocket, men fortsätta att köra, i stället för att avsluta helt.</span><span class="sxs-lookup"><span data-stu-id="04972-108">The `continue` statement provides a way to exit the current control block but continue execution, rather than exit completely.</span></span> <span data-ttu-id="04972-109">Instruktionen stöder etiketter.</span><span class="sxs-lookup"><span data-stu-id="04972-109">The statement supports labels.</span></span>
<span data-ttu-id="04972-110">En etikett är ett namn som du tilldelar till en instruktion i ett skript.</span><span class="sxs-lookup"><span data-stu-id="04972-110">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-continue-in-loops"></a><span data-ttu-id="04972-111">Använda Fortsätt i slingor</span><span class="sxs-lookup"><span data-stu-id="04972-111">Using continue in loops</span></span>

<span data-ttu-id="04972-112">En omärkt `continue` instruktion returnerar omedelbart program flödet överst i den innersta slingan som styrs av en `for` , `foreach` -, `do` -eller- `while` instruktion.</span><span class="sxs-lookup"><span data-stu-id="04972-112">An unlabeled `continue` statement immediately returns the program flow to the top of the innermost loop that is controlled by a `for`, `foreach`, `do`, or `while` statement.</span></span> <span data-ttu-id="04972-113">Den aktuella iterationen av loopen avslutas och loopen fortsätter med nästa iteration.</span><span class="sxs-lookup"><span data-stu-id="04972-113">The current iteration of the loop is terminated and the loop continues with the next iteration.</span></span>

<span data-ttu-id="04972-114">I följande exempel returnerar program Flow överst i `while` slingan om `$ctr` variabeln är lika med 5.</span><span class="sxs-lookup"><span data-stu-id="04972-114">In the following example, program flow returns to the top of the `while` loop if the `$ctr` variable is equal to 5.</span></span> <span data-ttu-id="04972-115">Därför visas alla tal mellan 1 och 10 förutom 5:</span><span class="sxs-lookup"><span data-stu-id="04972-115">As a result, all the numbers between 1 and 10 are displayed except for 5:</span></span>

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

<span data-ttu-id="04972-116">När du använder en `for` loop fortsätter körningen vid `<Repeat>` instruktionen, följt av `<Condition>` testet.</span><span class="sxs-lookup"><span data-stu-id="04972-116">When using a `for` loop, execution continues at the `<Repeat>` statement, followed by the `<Condition>` test.</span></span> <span data-ttu-id="04972-117">I exemplet nedan inträffar inte en oändlig slinga eftersom minskningen av `$i` inträffar efter `continue` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="04972-117">In the example below, an infinite loop will not occur because the decrement of `$i` occurs after the `continue` keyword.</span></span>

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a><span data-ttu-id="04972-118">Använda en etikett med etiketten Fortsätt i en slinga</span><span class="sxs-lookup"><span data-stu-id="04972-118">Using a labeled continue in a loop</span></span>

<span data-ttu-id="04972-119">En märkt `continue` instruktion avslutar körningen av upprepnings-och överförings kontrollen till den riktade omslutande upprepnings-eller `switch` instruktions etiketten.</span><span class="sxs-lookup"><span data-stu-id="04972-119">A labeled `continue` statement terminates execution of the iteration and transfers control to the targeted enclosing iteration or `switch` statement label.</span></span>

<span data-ttu-id="04972-120">I följande exempel `for` avslutas innersta när `$condition` är **Sant** och upprepningen fortsätter med den andra `for` slingan på `labelB` .</span><span class="sxs-lookup"><span data-stu-id="04972-120">In the following example, the innermost `for` is terminated when `$condition` is **True** and iteration continues with the second `for` loop at `labelB`.</span></span>

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a><span data-ttu-id="04972-121">Använda Continue i en switch-instruktion</span><span class="sxs-lookup"><span data-stu-id="04972-121">Using continue in a switch statement</span></span>

<span data-ttu-id="04972-122">En omärkt `continue` instruktion inom en `switch` avslutar körning av den aktuella `switch` upprepnings-och överförings kontrollen överst i `switch` för att hämta nästa inobjekt.</span><span class="sxs-lookup"><span data-stu-id="04972-122">An unlabeled `continue` statement within a `switch` terminates execution of the current `switch` iteration and transfers control to the top of the `switch` to get the next input item.</span></span>

<span data-ttu-id="04972-123">Om det finns ett enskilt inobjekt `continue` avslutar hela `switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="04972-123">When there is a single input item `continue` exits the entire `switch` statement.</span></span>
<span data-ttu-id="04972-124">När `switch` indatatypen är en samling `switch` testar varje element i samlingen.</span><span class="sxs-lookup"><span data-stu-id="04972-124">When the `switch` input is a collection, the `switch` tests each element of the collection.</span></span> <span data-ttu-id="04972-125">Den `continue` aktuella iterationen avslutas och `switch` fortsätter med nästa element.</span><span class="sxs-lookup"><span data-stu-id="04972-125">The `continue` exits the current iteration and the `switch` continues with the next element.</span></span>

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a><span data-ttu-id="04972-126">Använda Continue i en trap-instruktion</span><span class="sxs-lookup"><span data-stu-id="04972-126">Using continue in a trap statement</span></span>

<span data-ttu-id="04972-127">Om den slutliga instruktionen som körs i brödtext a `trap` -instruktionen är `continue` , ignoreras det fångade felet tyst och körningen fortsätter med instruktionen direkt efter den som orsakade problemet `trap` .</span><span class="sxs-lookup"><span data-stu-id="04972-127">If the final statement executed in the body a `trap` statement is `continue`, the trapped error is silently ignored and execution continues with the statement immediately following the one that caused `trap` to occur.</span></span>

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="04972-128">Använd inte Fortsätt utanför en loop, växel eller trap</span><span class="sxs-lookup"><span data-stu-id="04972-128">Do not use continue outside of a loop, switch, or trap</span></span>

<span data-ttu-id="04972-129">När `continue` används utanför en konstruktion som stöder den direkt (loopar, `switch` , `trap` ), letar PowerShell _upp anrops stacken_ för en omsluten konstruktion.</span><span class="sxs-lookup"><span data-stu-id="04972-129">When `continue` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="04972-130">Om det inte går att hitta en omsluten konstruktion avslutas den aktuella körnings utrymme tyst.</span><span class="sxs-lookup"><span data-stu-id="04972-130">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="04972-131">Det innebär att funktioner och skript som oavsiktligt använder en `continue` utanför en omsluten konstruktion som stöder den, oavsiktligt kan avsluta sina _anropare_.</span><span class="sxs-lookup"><span data-stu-id="04972-131">This means that functions and scripts that inadvertently use a `continue` outside of an enclosing construct that supports it, can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="04972-132">Om du använder `continue` inuti en pipeline, t. ex. ett `ForEach-Object` skript block, avslutar inte bara pipelinen, utan kan avsluta hela körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="04972-132">Using `continue` inside a pipeline, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="04972-133">Se även</span><span class="sxs-lookup"><span data-stu-id="04972-133">See also</span></span>

[<span data-ttu-id="04972-134">about_Break</span><span class="sxs-lookup"><span data-stu-id="04972-134">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="04972-135">about_For</span><span class="sxs-lookup"><span data-stu-id="04972-135">about_For</span></span>](about_For.md)

[<span data-ttu-id="04972-136">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="04972-136">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="04972-137">about_Throw</span><span class="sxs-lookup"><span data-stu-id="04972-137">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="04972-138">about_Trap</span><span class="sxs-lookup"><span data-stu-id="04972-138">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="04972-139">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="04972-139">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
