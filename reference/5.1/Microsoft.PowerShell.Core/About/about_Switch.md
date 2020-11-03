---
description: Förklarar hur du använder en växel för att hantera flera `If` instruktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_switch?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Switch
ms.openlocfilehash: 1cb0e95aa942af4aa29f449da0c7cbbaf15d7dc5
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271394"
---
# <a name="about-switch"></a><span data-ttu-id="32cd0-104">Om-växel</span><span class="sxs-lookup"><span data-stu-id="32cd0-104">About Switch</span></span>

## <a name="short-description"></a><span data-ttu-id="32cd0-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="32cd0-105">Short description</span></span>
<span data-ttu-id="32cd0-106">Förklarar hur du använder en växel för att hantera flera `If` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="32cd0-106">Explains how to use a switch to handle multiple `If` statements.</span></span>

## <a name="long-description"></a><span data-ttu-id="32cd0-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="32cd0-107">Long description</span></span>

<span data-ttu-id="32cd0-108">Om du vill kontrol lera ett villkor i ett skript eller en funktion använder du en `If` instruktion.</span><span class="sxs-lookup"><span data-stu-id="32cd0-108">To check a condition in a script or function, use an `If` statement.</span></span> <span data-ttu-id="32cd0-109">`If`Instruktionen kan kontrol lera många typer av villkor, inklusive värdet för variabler och egenskaper för objekt.</span><span class="sxs-lookup"><span data-stu-id="32cd0-109">The `If` statement can check many types of conditions, including the value of variables and the properties of objects.</span></span>

<span data-ttu-id="32cd0-110">Använd en instruktion för att kontrol lera flera villkor `Switch` .</span><span class="sxs-lookup"><span data-stu-id="32cd0-110">To check multiple conditions, use a `Switch` statement.</span></span> <span data-ttu-id="32cd0-111">`Switch`Instruktionen motsvarar en serie `If` instruktioner, men det är enklare.</span><span class="sxs-lookup"><span data-stu-id="32cd0-111">The `Switch` statement is equivalent to a series of `If` statements, but it is simpler.</span></span> <span data-ttu-id="32cd0-112">`Switch`Instruktionen visar varje villkor och en valfri åtgärd.</span><span class="sxs-lookup"><span data-stu-id="32cd0-112">The `Switch` statement lists each condition and an optional action.</span></span> <span data-ttu-id="32cd0-113">Om ett villkor hämtas utförs åtgärden.</span><span class="sxs-lookup"><span data-stu-id="32cd0-113">If a condition obtains, the action is performed.</span></span>

<span data-ttu-id="32cd0-114">`Switch`Instruktionen kan använda `$_` `$switch` Automatiska variabler och.</span><span class="sxs-lookup"><span data-stu-id="32cd0-114">The `Switch` statement can use the `$_` and `$switch` automatic variables.</span></span> <span data-ttu-id="32cd0-115">Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="32cd0-115">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="32cd0-116">En Basic- `Switch` instruktion har följande format:</span><span class="sxs-lookup"><span data-stu-id="32cd0-116">A basic `Switch` statement has the following format:</span></span>

```powershell
Switch (<test-value>)
{
    <condition> {<action>}
    <condition> {<action>}
}
```

<span data-ttu-id="32cd0-117">Följande `Switch` uttryck jämför exempelvis testvärdet, 3, för var och en av villkoren.</span><span class="sxs-lookup"><span data-stu-id="32cd0-117">For example, the following `Switch` statement compares the test value, 3, to each of the conditions.</span></span> <span data-ttu-id="32cd0-118">När testvärdet matchar villkoret utförs åtgärden.</span><span class="sxs-lookup"><span data-stu-id="32cd0-118">When the test value matches the condition, the action is performed.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
}
```

```Output
It is three.
```

<span data-ttu-id="32cd0-119">I det här enkla exemplet jämförs värdet med varje villkor i listan, även om det finns en matchning för värdet 3.</span><span class="sxs-lookup"><span data-stu-id="32cd0-119">In this simple example, the value is compared to each condition in the list, even though there is a match for the value 3.</span></span> <span data-ttu-id="32cd0-120">Följande `Switch` instruktion har två villkor för värdet 3.</span><span class="sxs-lookup"><span data-stu-id="32cd0-120">The following `Switch` statement has two conditions for a value of 3.</span></span> <span data-ttu-id="32cd0-121">Det visar att alla villkor testas som standard.</span><span class="sxs-lookup"><span data-stu-id="32cd0-121">It demonstrates that, by default, all conditions are tested.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
Three again.
```

<span data-ttu-id="32cd0-122">Använd instruktionen om du vill leda `Switch` till att jämförelsen avbryts efter en matchning `Break` .</span><span class="sxs-lookup"><span data-stu-id="32cd0-122">To direct the `Switch` to stop comparing after a match, use the `Break` statement.</span></span> <span data-ttu-id="32cd0-123">Instruktionen `Break` avslutar `Switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="32cd0-123">The `Break` statement terminates the `Switch` statement.</span></span>

```powershell
switch (3)
{
    1 {"It is one."}
    2 {"It is two."}
    3 {"It is three."; Break}
    4 {"It is four."}
    3 {"Three again."}
}
```

```Output
It is three.
```

<span data-ttu-id="32cd0-124">Om testvärdet är en samling, till exempel en matris, utvärderas varje objekt i samlingen i den ordning som den visas.</span><span class="sxs-lookup"><span data-stu-id="32cd0-124">If the test value is a collection, such as an array, each item in the collection is evaluated in the order in which it appears.</span></span> <span data-ttu-id="32cd0-125">I följande exempel utvärderas 4 och sedan 2.</span><span class="sxs-lookup"><span data-stu-id="32cd0-125">The following examples evaluates 4 and then 2.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one." }
    2 {"It is two." }
    3 {"It is three." }
    4 {"It is four." }
    3 {"Three again."}
}
```

```Output
It is four.
It is two.
```

<span data-ttu-id="32cd0-126">Alla `Break` instruktioner gäller för samlingen, inte för varje värde, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="32cd0-126">Any `Break` statements apply to the collection, not to each value, as shown in the following example.</span></span> <span data-ttu-id="32cd0-127">`Switch`Instruktionen avslutas med `Break` instruktionen i villkoret för värdet 4.</span><span class="sxs-lookup"><span data-stu-id="32cd0-127">The `Switch` statement is terminated by the `Break` statement in the condition of value 4.</span></span>

```powershell
switch (4, 2)
{
    1 {"It is one."; Break}
    2 {"It is two." ; Break }
    3 {"It is three." ; Break }
    4 {"It is four." ; Break }
    3 {"Three again."}
}
```

```Output
It is four.
```

### <a name="syntax"></a><span data-ttu-id="32cd0-128">Syntax</span><span class="sxs-lookup"><span data-stu-id="32cd0-128">Syntax</span></span>

<span data-ttu-id="32cd0-129">Den fullständiga `Switch` syntaxen för uttrycket är följande:</span><span class="sxs-lookup"><span data-stu-id="32cd0-129">The complete `Switch` statement syntax is as follows:</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] (<value>)
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="32cd0-130">eller</span><span class="sxs-lookup"><span data-stu-id="32cd0-130">or</span></span>

```
switch [-regex|-wildcard|-exact][-casesensitive] -file filename
{
    "string"|number|variable|{ expression } { statementlist }
    default { statementlist }
}
```

<span data-ttu-id="32cd0-131">Om inga parametrar används, `Switch` fungerar samma sak som att använda den **exakta** parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-131">If no parameters are used, `Switch` behaves the same as using the **Exact** parameter.</span></span> <span data-ttu-id="32cd0-132">En Skift läges okänslig matchning för värdet utförs.</span><span class="sxs-lookup"><span data-stu-id="32cd0-132">It performs a case-insensitive match for the value.</span></span> <span data-ttu-id="32cd0-133">Om värdet är en samling utvärderas varje element i den ordning som det visas.</span><span class="sxs-lookup"><span data-stu-id="32cd0-133">If the value is a collection, each element is evaluated in the order in which it appears.</span></span>

<span data-ttu-id="32cd0-134">`Switch`Instruktionen måste innehålla minst en villkors instruktion.</span><span class="sxs-lookup"><span data-stu-id="32cd0-134">The `Switch` statement must include at least one condition statement.</span></span>

<span data-ttu-id="32cd0-135">`Default`Satsen utlöses när värdet inte matchar något av villkoren.</span><span class="sxs-lookup"><span data-stu-id="32cd0-135">The `Default` clause is triggered when the value does not match any of the conditions.</span></span> <span data-ttu-id="32cd0-136">Den motsvarar en `Else` sats i en `If` instruktion.</span><span class="sxs-lookup"><span data-stu-id="32cd0-136">It is equivalent to an `Else` clause in an `If` statement.</span></span> <span data-ttu-id="32cd0-137">Endast en `Default` sats tillåts i varje `Switch` instruktion.</span><span class="sxs-lookup"><span data-stu-id="32cd0-137">Only one `Default` clause is permitted in each `Switch` statement.</span></span>

<span data-ttu-id="32cd0-138">`Switch` har följande parametrar:</span><span class="sxs-lookup"><span data-stu-id="32cd0-138">`Switch` has the following parameters:</span></span>

- <span data-ttu-id="32cd0-139">**Jokertecken** – anger att villkoret är en jokertecken.</span><span class="sxs-lookup"><span data-stu-id="32cd0-139">**Wildcard** - Indicates that the condition is a wildcard string.</span></span> <span data-ttu-id="32cd0-140">Om match-satsen inte är en sträng ignoreras parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-140">If the match clause is not a string, the parameter is ignored.</span></span> <span data-ttu-id="32cd0-141">Jämförelsen är inte Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="32cd0-141">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="32cd0-142">**Exakt** -visar att match-satsen, om det är en sträng, måste matcha exakt.</span><span class="sxs-lookup"><span data-stu-id="32cd0-142">**Exact** - Indicates that the match clause, if it is a string, must match exactly.</span></span> <span data-ttu-id="32cd0-143">Om match-satsen inte är en sträng ignoreras den här parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-143">If the match clause is not a string, this parameter is ignored.</span></span> <span data-ttu-id="32cd0-144">Jämförelsen är inte Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="32cd0-144">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="32cd0-145">**CaseSensitive** – utför en Skift läges känslig matchning.</span><span class="sxs-lookup"><span data-stu-id="32cd0-145">**CaseSensitive** - Performs a case-sensitive match.</span></span> <span data-ttu-id="32cd0-146">Om match-satsen inte är en sträng ignoreras den här parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-146">If the match clause is not a string, this parameter is ignored.</span></span>
- <span data-ttu-id="32cd0-147">**File** – tar emot indata från en fil i stället för en värde instruktion.</span><span class="sxs-lookup"><span data-stu-id="32cd0-147">**File** - Takes input from a file rather than a value statement.</span></span> <span data-ttu-id="32cd0-148">Om flera **fil** parametrar ingår, används bara den sista.</span><span class="sxs-lookup"><span data-stu-id="32cd0-148">If multiple **File** parameters are included, only the last one is used.</span></span> <span data-ttu-id="32cd0-149">Varje rad i filen läses och utvärderas av `Switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="32cd0-149">Each line of the file is read and evaluated by the `Switch` statement.</span></span> <span data-ttu-id="32cd0-150">Jämförelsen är inte Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="32cd0-150">The comparison is case-insensitive.</span></span>
- <span data-ttu-id="32cd0-151">**Regex** – utför matchning av reguljära uttryck för värdet på villkoret.</span><span class="sxs-lookup"><span data-stu-id="32cd0-151">**Regex** - Performs regular expression matching of the value to the condition.</span></span> <span data-ttu-id="32cd0-152">Om match-satsen inte är en sträng ignoreras den här parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-152">If the match clause is not a string, this parameter is ignored.</span></span>
  <span data-ttu-id="32cd0-153">Jämförelsen är inte Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="32cd0-153">The comparison is case-insensitive.</span></span> <span data-ttu-id="32cd0-154">Den `$matches` automatiska variabeln är tillgänglig för användning i det matchande instruktions blocket.</span><span class="sxs-lookup"><span data-stu-id="32cd0-154">The `$matches` automatic variable is available for use within the matching statement block.</span></span>

> [!NOTE]
> <span data-ttu-id="32cd0-155">När du anger motstridiga värden, t. ex. **regex** och **jokertecken** , har den senast angivna parametern företräde och alla motstridiga parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="32cd0-155">When specifying conflicting values, like **Regex** and **Wildcard** , the last parameter specified takes precedence, and all conflicting parameters are ignored.</span></span> <span data-ttu-id="32cd0-156">Flera instanser av parametrar tillåts också.</span><span class="sxs-lookup"><span data-stu-id="32cd0-156">Multiple instances of parameters are also permitted.</span></span> <span data-ttu-id="32cd0-157">Men endast den sista parametern som används är giltig.</span><span class="sxs-lookup"><span data-stu-id="32cd0-157">However, only the last parameter used is effective.</span></span>

<span data-ttu-id="32cd0-158">I det här exemplet skickas ett objekt som inte är en sträng eller numeriska data till `Switch` .</span><span class="sxs-lookup"><span data-stu-id="32cd0-158">In this example, an object that's not a string or numerical data is passed to the `Switch`.</span></span> <span data-ttu-id="32cd0-159">Den `Switch` utför en sträng som tvingas på objektet och utvärderar resultatet.</span><span class="sxs-lookup"><span data-stu-id="32cd0-159">The `Switch` performs a string coercion on the object and evaluates the outcome.</span></span>

```powershell
$test = @{
    Test  = 'test'
    Test2 = 'test2'
}

$test.ToString()

switch -Exact ($test)
{
    'System.Collections.Hashtable'
    {
        'Hashtable string coercion'
    }
    'test'
    {
        'Hashtable value'
    }
}
```

```Output
System.Collections.Hashtable
Hashtable string coercion
```

<span data-ttu-id="32cd0-160">I det här exemplet finns det inget matchande fall, så det finns inga utdata.</span><span class="sxs-lookup"><span data-stu-id="32cd0-160">In this example, there is no matching case so there is no output.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
}
```

<span data-ttu-id="32cd0-161">Genom att lägga till `Default` -satsen kan du utföra en åtgärd när inga andra villkor lyckas.</span><span class="sxs-lookup"><span data-stu-id="32cd0-161">By adding the `Default` clause, you can perform an action when no other conditions succeed.</span></span>

```powershell
switch ("fourteen")
{
    1 {"It is one."; Break}
    2 {"It is two."; Break}
    3 {"It is three."; Break}
    4 {"It is four."; Break}
    "fo*" {"That's too many."}
    Default {
        "No matches"
    }
}
```

```Output
No matches
```

<span data-ttu-id="32cd0-162">För ordet "fjorton" för att matcha ett ärende måste du använda `-Wildcard` parametern eller `-Regex` .</span><span class="sxs-lookup"><span data-stu-id="32cd0-162">For the word "fourteen" to match a case you must use the `-Wildcard` or `-Regex` parameter.</span></span>

```powershell
   PS> switch -Wildcard ("fourteen")
       {
           1 {"It is one."; Break}
           2 {"It is two."; Break}
           3 {"It is three."; Break}
           4 {"It is four."; Break}
           "fo*" {"That's too many."}
       }
 ```

```Output
That's too many.
```

<span data-ttu-id="32cd0-163">I följande exempel används `-Regex` parametern.</span><span class="sxs-lookup"><span data-stu-id="32cd0-163">The following example uses the `-Regex` parameter.</span></span>

```powershell
$target = 'https://bing.com'
switch -Regex ($target)
{
    '^ftp\://.*$' { "$_ is an ftp address"; Break }
    '^\w+@\w+\.com|edu|org$' { "$_ is an email address"; Break }
    '^(http[s]?)\://.*$' { "$_ is a web address that uses $($matches[1])"; Break }
}
```

```Output
https://bing.com is a web address that uses https
```

<span data-ttu-id="32cd0-164">Ett villkor för Switch-satsen kan vara antingen:</span><span class="sxs-lookup"><span data-stu-id="32cd0-164">A Switch statement condition may be either:</span></span>

- <span data-ttu-id="32cd0-165">Ett uttryck vars värde jämförs med indatavärdet</span><span class="sxs-lookup"><span data-stu-id="32cd0-165">An expression whose value is compared to the input value</span></span>
- <span data-ttu-id="32cd0-166">Ett skript block som ska returneras `$true` om ett villkor uppfylls.</span><span class="sxs-lookup"><span data-stu-id="32cd0-166">A script block which should return `$true` if a condition is met.</span></span>

<span data-ttu-id="32cd0-167">Den `$_` automatiska variabeln innehåller det värde som skickas till Switch-instruktionen och är tillgänglig för utvärdering och användning inom villkors satsernas omfattning.</span><span class="sxs-lookup"><span data-stu-id="32cd0-167">The `$_` automatic variable contains the value passed to the switch statement and is available for evaluation and use within the scope of the condition statements.</span></span>

<span data-ttu-id="32cd0-168">Åtgärden för varje villkor är oberoende av åtgärderna i andra villkor.</span><span class="sxs-lookup"><span data-stu-id="32cd0-168">The action for each condition is independent of the actions in other conditions.</span></span>

<span data-ttu-id="32cd0-169">I följande exempel demonstreras användningen av skript block som `Switch` villkor för uttrycket.</span><span class="sxs-lookup"><span data-stu-id="32cd0-169">The following example demonstrates the use of script blocks as `Switch` statement conditions.</span></span>

```powershell
switch ("Test")
{
    {$_ -is [String]} {
        "Found a string"
    }
    "Test" {
        "This $_ executes as well"
    }
}
```

```Output
Found a string
This Test executes as well
```

<span data-ttu-id="32cd0-170">Om värdet matchar flera villkor körs åtgärden för varje villkor.</span><span class="sxs-lookup"><span data-stu-id="32cd0-170">If the value matches multiple conditions, the action for each condition is executed.</span></span> <span data-ttu-id="32cd0-171">Om du vill ändra det här beteendet använder du `Break` `Continue` nyckelorden eller.</span><span class="sxs-lookup"><span data-stu-id="32cd0-171">To change this behavior, use the `Break` or `Continue` keywords.</span></span>

<span data-ttu-id="32cd0-172">`Break`Nyckelordet stoppar bearbetningen och avslutar `Switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="32cd0-172">The `Break` keyword stops processing and exits the `Switch` statement.</span></span>

<span data-ttu-id="32cd0-173">`Continue`Nyckelordet slutar bearbeta det aktuella värdet, men fortsätter att bearbeta eventuella efterföljande värden.</span><span class="sxs-lookup"><span data-stu-id="32cd0-173">The `Continue` keyword stops processing the current value, but continues processing any subsequent values.</span></span>

<span data-ttu-id="32cd0-174">Följande exempel bearbetar en matris med tal och visar om de är udda eller jämna.</span><span class="sxs-lookup"><span data-stu-id="32cd0-174">The following example processes an array of numbers and displays if they are odd or even.</span></span> <span data-ttu-id="32cd0-175">Negativa tal hoppas över med `Continue` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="32cd0-175">Negative numbers are skipped with the `Continue` keyword.</span></span> <span data-ttu-id="32cd0-176">Om ett icke-nummer påträffas avslutas körningen med `Break` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="32cd0-176">If a non-number is encountered, execution is terminated with the `Break` keyword.</span></span>

```powershell
switch (1,4,-1,3,"Hello",2,1)
{
    {$_ -lt 0} { Continue }
    {$_ -isnot [Int32]} { Break }
    {$_ % 2} {
        "$_ is Odd"
    }
    {-not ($_ % 2)} {
        "$_ is Even"
    }
}
```

```Output
1 is Odd
4 is Even
3 is Odd
```

## <a name="see-also"></a><span data-ttu-id="32cd0-177">Se även</span><span class="sxs-lookup"><span data-stu-id="32cd0-177">See also</span></span>

[<span data-ttu-id="32cd0-178">about_Break</span><span class="sxs-lookup"><span data-stu-id="32cd0-178">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="32cd0-179">about_Continue</span><span class="sxs-lookup"><span data-stu-id="32cd0-179">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="32cd0-180">about_If</span><span class="sxs-lookup"><span data-stu-id="32cd0-180">about_If</span></span>](about_If.md)

[<span data-ttu-id="32cd0-181">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="32cd0-181">about_Script_Blocks</span></span>](about_Script_Blocks.md)
