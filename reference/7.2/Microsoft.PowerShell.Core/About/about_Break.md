---
description: Beskriver ett uttryck som du kan använda för att omedelbart avsluta,,,, `foreach` `for` `while` `do` `switch` eller- `trap` instruktioner.
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 3c418f5bae11f957880c8b53ee0bcf2fb44515ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710686"
---
# <a name="about-break"></a><span data-ttu-id="e740c-103">Om avbrott</span><span class="sxs-lookup"><span data-stu-id="e740c-103">About Break</span></span>

## <a name="short-description"></a><span data-ttu-id="e740c-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e740c-104">Short description</span></span>

<span data-ttu-id="e740c-105">Beskriver ett uttryck som du kan använda för att omedelbart avsluta,,,, `foreach` `for` `while` `do` `switch` eller- `trap` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="e740c-105">Describes a statement you can use to immediately exit `foreach`, `for`, `while`, `do`, `switch`, or `trap` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="e740c-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e740c-106">Long description</span></span>

<span data-ttu-id="e740c-107">`break`Instruktionen gör det möjligt att avsluta det aktuella kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="e740c-107">The `break` statement provides a way to exit the current control block.</span></span>
<span data-ttu-id="e740c-108">Körningen fortsätter vid nästa instruktion efter kontroll blocket.</span><span class="sxs-lookup"><span data-stu-id="e740c-108">Execution continues at the next statement after the control block.</span></span> <span data-ttu-id="e740c-109">Instruktionen stöder etiketter.</span><span class="sxs-lookup"><span data-stu-id="e740c-109">The statement supports labels.</span></span> <span data-ttu-id="e740c-110">En etikett är ett namn som du tilldelar till en instruktion i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e740c-110">A label is a name you assign to a statement in a script.</span></span>

## <a name="using-break-in-loops"></a><span data-ttu-id="e740c-111">Använda avbrott i slingor</span><span class="sxs-lookup"><span data-stu-id="e740c-111">Using break in loops</span></span>

<span data-ttu-id="e740c-112">När en `break` instruktion visas i en slinga, till exempel en `foreach` , `for` , `do` eller `while` loop, avslutar PowerShell omedelbart loopen.</span><span class="sxs-lookup"><span data-stu-id="e740c-112">When a `break` statement appears in a loop, such as a `foreach`, `for`, `do`, or `while` loop, PowerShell immediately exits the loop.</span></span>

<span data-ttu-id="e740c-113">En `break` instruktion kan innehålla en etikett som låter dig avsluta inbäddade slingor.</span><span class="sxs-lookup"><span data-stu-id="e740c-113">A `break` statement can include a label that lets you exit embedded loops.</span></span> <span data-ttu-id="e740c-114">En etikett kan ange valfritt loop-nyckelord, till exempel, `foreach` `for` eller `while` , i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e740c-114">A label can specify any loop keyword, such as `foreach`, `for`, or `while`, in a script.</span></span>

<span data-ttu-id="e740c-115">Följande exempel visar hur du använder en `break` instruktion för att avsluta en `for` instruktion:</span><span class="sxs-lookup"><span data-stu-id="e740c-115">The following example shows how to use a `break` statement to exit a `for` statement:</span></span>

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

<span data-ttu-id="e740c-116">I det här exemplet `break` avslutar instruktionen `for` loopen när `$i` variabeln är lika med 1.</span><span class="sxs-lookup"><span data-stu-id="e740c-116">In this example, the `break` statement exits the `for` loop when the `$i` variable equals 1.</span></span> <span data-ttu-id="e740c-117">Även om `for` instruktionen utvärderas till **True** tills `$i` är större än 10, kommer PowerShell att nå break-instruktionen första `for` gången slingan körs.</span><span class="sxs-lookup"><span data-stu-id="e740c-117">Even though the `for` statement evaluates to **True** until `$i` is greater than 10, PowerShell reaches the break statement the first time the `for` loop is run.</span></span>

<span data-ttu-id="e740c-118">Det är vanligare att använda `break` instruktionen i en slinga där ett inre villkor måste uppfyllas.</span><span class="sxs-lookup"><span data-stu-id="e740c-118">It is more common to use the `break` statement in a loop where an inner condition must be met.</span></span> <span data-ttu-id="e740c-119">Tänk på följande `foreach` exempel:</span><span class="sxs-lookup"><span data-stu-id="e740c-119">Consider the following `foreach` statement example:</span></span>

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

<span data-ttu-id="e740c-120">I det här exemplet `foreach` upprepar instruktionen `$varB` matrisen.</span><span class="sxs-lookup"><span data-stu-id="e740c-120">In this example, the `foreach` statement iterates the `$varB` array.</span></span> <span data-ttu-id="e740c-121">`if`Instruktionen utvärderar till falskt de första två gånger som loopen körs och variabeln `$i` ökas med 1.</span><span class="sxs-lookup"><span data-stu-id="e740c-121">The `if` statement evaluates to False the first two times the loop is run and the variable `$i` is incremented by 1.</span></span> <span data-ttu-id="e740c-122">Den tredje gången slingan körs, `$i` är lika med 2 och `$val` variabeln är lika med 30.</span><span class="sxs-lookup"><span data-stu-id="e740c-122">The third time the loop is run, `$i` equals 2, and the `$val` variable equals 30.</span></span> <span data-ttu-id="e740c-123">Nu `break` körs instruktionen och `foreach` loopen avslutas.</span><span class="sxs-lookup"><span data-stu-id="e740c-123">At this point, the `break` statement runs, and the `foreach` loop exits.</span></span>

### <a name="using-a-labeled-break-in-a-loop"></a><span data-ttu-id="e740c-124">Använda en etikettad rast i en slinga</span><span class="sxs-lookup"><span data-stu-id="e740c-124">Using a labeled break in a loop</span></span>

<span data-ttu-id="e740c-125">En `break` instruktion kan innehålla en etikett.</span><span class="sxs-lookup"><span data-stu-id="e740c-125">A `break` statement can include a label.</span></span> <span data-ttu-id="e740c-126">Om du använder `break` nyckelordet med en etikett, avslutar PowerShell den märkta loopen i stället för att avsluta den aktuella slingan.</span><span class="sxs-lookup"><span data-stu-id="e740c-126">If you use the `break` keyword with a label, PowerShell exits the labeled loop instead of exiting the current loop.</span></span>
<span data-ttu-id="e740c-127">Etiketten är ett kolon följt av ett namn som du tilldelar.</span><span class="sxs-lookup"><span data-stu-id="e740c-127">The label is a colon followed by a name that you assign.</span></span> <span data-ttu-id="e740c-128">Etiketten måste vara den första token i en instruktion, och den måste följas av nyckelordet loop, till exempel `while` .</span><span class="sxs-lookup"><span data-stu-id="e740c-128">The label must be the first token in a statement, and it must be followed by the looping keyword, such as `while`.</span></span>

<span data-ttu-id="e740c-129">`break` flyttar körningen från den märkta slingan.</span><span class="sxs-lookup"><span data-stu-id="e740c-129">`break` moves execution out of the labeled loop.</span></span> <span data-ttu-id="e740c-130">I inbäddade slingor har detta ett annat resultat än `break` nyckelordet när det används av sig självt.</span><span class="sxs-lookup"><span data-stu-id="e740c-130">In embedded loops, this has a different result than the `break` keyword has when it is used by itself.</span></span> <span data-ttu-id="e740c-131">Det här exemplet har en `while` instruktion med en `for` instruktion:</span><span class="sxs-lookup"><span data-stu-id="e740c-131">This example has a `while` statement with a `for` statement:</span></span>

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

<span data-ttu-id="e740c-132">Om villkoret 2 utvärderas till **Sant**, hoppar körningen av skriptet ned till instruktionen efter den märkta loopen.</span><span class="sxs-lookup"><span data-stu-id="e740c-132">If condition 2 evaluates to **True**, the execution of the script skips down to the statement after the labeled loop.</span></span> <span data-ttu-id="e740c-133">I exemplet börjar körningen igen med instruktionen `$a = $c` .</span><span class="sxs-lookup"><span data-stu-id="e740c-133">In the example, execution starts again with the statement `$a = $c`.</span></span>

<span data-ttu-id="e740c-134">Du kan kapsla många etiketterade slingor, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="e740c-134">You can nest many labeled loops, as shown in the following example.</span></span>

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

<span data-ttu-id="e740c-135">Om `$b` variabeln utvärderas till True återupptas körningen av skriptet efter loopen med etiketten "Red".</span><span class="sxs-lookup"><span data-stu-id="e740c-135">If the `$b` variable evaluates to True, execution of the script resumes after the loop that is labeled "red".</span></span> <span data-ttu-id="e740c-136">Om `$c` variabeln utvärderas till True återupptas körningen av skript kontrollen efter loopen med etiketten "gul".</span><span class="sxs-lookup"><span data-stu-id="e740c-136">If the `$c` variable evaluates to True, execution of the script control resumes after the loop that is labeled "yellow".</span></span>

<span data-ttu-id="e740c-137">Om `$a` variabeln utvärderas till True återupptas körningen efter den innersta slingan.</span><span class="sxs-lookup"><span data-stu-id="e740c-137">If the `$a` variable evaluates to True, execution resumes after the innermost loop.</span></span> <span data-ttu-id="e740c-138">Ingen etikett krävs.</span><span class="sxs-lookup"><span data-stu-id="e740c-138">No label is needed.</span></span>

<span data-ttu-id="e740c-139">PowerShell begränsar inte hur långt etiketter kan återuppta körningen.</span><span class="sxs-lookup"><span data-stu-id="e740c-139">PowerShell does not limit how far labels can resume execution.</span></span> <span data-ttu-id="e740c-140">Etiketten kan till och med överföra kontroll över skript-och funktions anrops gränser.</span><span class="sxs-lookup"><span data-stu-id="e740c-140">The label can even pass control across script and function call boundaries.</span></span>

## <a name="using-break-in-a-switch-statement"></a><span data-ttu-id="e740c-141">Använda Break i en switch-instruktion</span><span class="sxs-lookup"><span data-stu-id="e740c-141">Using break in a switch statement</span></span>

<span data-ttu-id="e740c-142">I en `switch` konstruktion kommer `break` PowerShell att avsluta `switch` kod blocket.</span><span class="sxs-lookup"><span data-stu-id="e740c-142">In a `switch`construct, `break` causes PowerShell to exit the `switch` code block.</span></span>

<span data-ttu-id="e740c-143">`break`Nyckelordet används för att lämna `switch` konstruktionen.</span><span class="sxs-lookup"><span data-stu-id="e740c-143">The `break` keyword is used to leave the `switch` construct.</span></span> <span data-ttu-id="e740c-144">Till exempel använder följande uttryck `switch` `break` för att testa för det mest aktuella villkoret:</span><span class="sxs-lookup"><span data-stu-id="e740c-144">For example, the following `switch` statement uses `break` statements to test for the most specific condition:</span></span>

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

<span data-ttu-id="e740c-145">I det här exemplet `$var` skapas variabeln och initieras till ett sträng värde för `word2` .</span><span class="sxs-lookup"><span data-stu-id="e740c-145">In this example, the `$var` variable is created and initialized to a string value of `word2`.</span></span> <span data-ttu-id="e740c-146">`switch`Instruktionen använder **regex** -klassen för att matcha variabelns värde först med termen `word2` .</span><span class="sxs-lookup"><span data-stu-id="e740c-146">The `switch` statement uses the **Regex** class to match the variable value first with the term `word2`.</span></span> <span data-ttu-id="e740c-147">Eftersom variabelvärdet och det första testet i `switch` instruktionen matchar, körs det första kod blocket i `switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e740c-147">Because the variable value and the first test in the `switch` statement match, the first code block in the `switch` statement runs.</span></span>

<span data-ttu-id="e740c-148">När PowerShell når den första `break` instruktionen `switch` avslutas instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e740c-148">When PowerShell reaches the first `break` statement, the `switch` statement exits.</span></span> <span data-ttu-id="e740c-149">Om de fyra `break` satserna tas bort från exemplet är alla fyra villkor uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="e740c-149">If the four `break` statements are removed from the example, all four conditions are met.</span></span> <span data-ttu-id="e740c-150">I det här exemplet används `break` instruktionen för att visa resultaten när det mest aktuella villkoret är uppfyllt.</span><span class="sxs-lookup"><span data-stu-id="e740c-150">This example uses the `break` statement to display results when the most specific condition is met.</span></span>

## <a name="using-break-in-a-trap-statement"></a><span data-ttu-id="e740c-151">Använda Break i en trap-instruktion</span><span class="sxs-lookup"><span data-stu-id="e740c-151">Using break in a trap statement</span></span>

<span data-ttu-id="e740c-152">Om den slutliga instruktionen som körs i bröd texten i en `trap` instruktion är `break` , ignoreras felobjektet och undantags felet återskapas.</span><span class="sxs-lookup"><span data-stu-id="e740c-152">If the final statement executed in the body of a `trap` statement is `break`, the error object is suppressed and the exception is re-thrown.</span></span>

<span data-ttu-id="e740c-153">I följande exempel skapas ett **DivideByZeroException** -undantag som fångas med `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e740c-153">The following example create a **DivideByZeroException** exception that is trapped using the `trap` statement.</span></span>

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

Observera att körningen stoppas vid undantag. <span data-ttu-id="e740c-155">`After loop`Nås aldrig.</span><span class="sxs-lookup"><span data-stu-id="e740c-155">The `After loop` is never reached.</span></span>
<span data-ttu-id="e740c-156">Undantaget återskapas efter `trap` körningen.</span><span class="sxs-lookup"><span data-stu-id="e740c-156">The exception is re-thrown after the `trap` executes.</span></span>

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a><span data-ttu-id="e740c-157">Använd inte Break utanför en slinga, switch eller trap</span><span class="sxs-lookup"><span data-stu-id="e740c-157">Do not use break outside of a loop, switch, or trap</span></span>

<span data-ttu-id="e740c-158">När `break` används utanför en konstruktion som stöder den direkt (loopar, `switch` , `trap` ), letar PowerShell _upp anrops stacken_ för en omsluten konstruktion.</span><span class="sxs-lookup"><span data-stu-id="e740c-158">When `break` is used outside of a construct that directly supports it (loops, `switch`, `trap`), PowerShell looks _up the call stack_ for an enclosing construct.</span></span> <span data-ttu-id="e740c-159">Om det inte går att hitta en omsluten konstruktion avslutas den aktuella körnings utrymme tyst.</span><span class="sxs-lookup"><span data-stu-id="e740c-159">If it can't find an enclosing construct, the current runspace is quietly terminated.</span></span>

<span data-ttu-id="e740c-160">Det innebär att funktioner och skript som oavsiktligt använder en `break` utanför en omsluten konstruktion som stöder det kan oavsiktligt avsluta sina _anropare_.</span><span class="sxs-lookup"><span data-stu-id="e740c-160">This means that functions and scripts that inadvertently use a `break` outside of an enclosing construct that supports it can inadvertently terminate their _callers_.</span></span>

<span data-ttu-id="e740c-161">Om du använder `break` inuti en pipeline `break` , t. ex. ett `ForEach-Object` skript block, avslutar inte bara pipelinen, utan kan avsluta hela körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e740c-161">Using `break` inside a pipeline `break`, such as a `ForEach-Object` script block, not only exits the pipeline, it potentially terminates the entire runspace.</span></span>

## <a name="see-also"></a><span data-ttu-id="e740c-162">Se även</span><span class="sxs-lookup"><span data-stu-id="e740c-162">See also</span></span>

[<span data-ttu-id="e740c-163">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="e740c-163">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="e740c-164">about_Continue</span><span class="sxs-lookup"><span data-stu-id="e740c-164">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="e740c-165">about_For</span><span class="sxs-lookup"><span data-stu-id="e740c-165">about_For</span></span>](about_For.md)

[<span data-ttu-id="e740c-166">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="e740c-166">about_Foreach</span></span>](about_Foreach.md)

[<span data-ttu-id="e740c-167">about_Switch</span><span class="sxs-lookup"><span data-stu-id="e740c-167">about_Switch</span></span>](about_Switch.md)

[<span data-ttu-id="e740c-168">about_Throw</span><span class="sxs-lookup"><span data-stu-id="e740c-168">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="e740c-169">about_Trap</span><span class="sxs-lookup"><span data-stu-id="e740c-169">about_Trap</span></span>](about_Trap.md)

[<span data-ttu-id="e740c-170">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="e740c-170">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)

[<span data-ttu-id="e740c-171">about_While</span><span class="sxs-lookup"><span data-stu-id="e740c-171">about_While</span></span>](about_While.md)
