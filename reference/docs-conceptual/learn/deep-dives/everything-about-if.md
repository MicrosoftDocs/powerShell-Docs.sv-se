---
title: Allt du ville veta om instruktionen IF
description: Precis som många andra språk har PowerShell instruktioner för att villkorligt köra kod i dina skript.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6ffb70af694e80430d31991045b9fadc1a2cc3f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149868"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a><span data-ttu-id="41497-103">Allt du ville veta om instruktionen IF</span><span class="sxs-lookup"><span data-stu-id="41497-103">Everything you wanted to know about the IF statement</span></span>

<span data-ttu-id="41497-104">Precis som många andra språk har PowerShell instruktioner för att villkorligt köra kod i dina skript.</span><span class="sxs-lookup"><span data-stu-id="41497-104">Like many other languages, PowerShell has statements for conditionally executing code in your scripts.</span></span> <span data-ttu-id="41497-105">En av dessa uttryck är [IF][] -instruktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-105">One of those statements is the [if][] statement.</span></span> <span data-ttu-id="41497-106">Idag tar vi en djupare inblick i ett av de mest grundläggande kommandona i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-106">Today we will take a deep dive into one of the most fundamental commands in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="41497-107">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="41497-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="41497-108">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="41497-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="41497-109">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="41497-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="conditional-execution"></a><span data-ttu-id="41497-110">Villkorlig körning</span><span class="sxs-lookup"><span data-stu-id="41497-110">Conditional execution</span></span>

<span data-ttu-id="41497-111">Dina skript behöver ofta fatta beslut och utföra en annan logik utifrån dessa beslut.</span><span class="sxs-lookup"><span data-stu-id="41497-111">Your scripts often need to make decisions and perform different logic based on those decisions.</span></span>
<span data-ttu-id="41497-112">Detta är vad jag menar vid villkorlig körning.</span><span class="sxs-lookup"><span data-stu-id="41497-112">This is what I mean by conditional execution.</span></span> <span data-ttu-id="41497-113">Du har ett uttryck eller ett värde att utvärdera och kör sedan ett annat avsnitt av kod baserat på den utvärderingen.</span><span class="sxs-lookup"><span data-stu-id="41497-113">You have one statement or value to evaluate, then execute a different section of code based on that evaluation.</span></span> <span data-ttu-id="41497-114">Detta är exakt vad `if` instruktionen gör.</span><span class="sxs-lookup"><span data-stu-id="41497-114">This is exactly what the `if` statement does.</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="41497-115">Instruktionen IF</span><span class="sxs-lookup"><span data-stu-id="41497-115">The if statement</span></span>

<span data-ttu-id="41497-116">Här är ett grundläggande exempel på `if` instruktionen:</span><span class="sxs-lookup"><span data-stu-id="41497-116">Here is a basic example of the `if` statement:</span></span>

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

<span data-ttu-id="41497-117">Det första `if` instruktionen är att utvärdera uttrycket inom parentes.</span><span class="sxs-lookup"><span data-stu-id="41497-117">The first thing the `if` statement does is evaluate the expression in parentheses.</span></span> <span data-ttu-id="41497-118">Om den utvärderas till `$true` kör den `scriptblock` på klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="41497-118">If it evaluates to `$true`, then it executes the `scriptblock` in the braces.</span></span> <span data-ttu-id="41497-119">Om värdet var `$false` hoppar det över det script block.</span><span class="sxs-lookup"><span data-stu-id="41497-119">If the value was `$false`, then it would skip over that scriptblock.</span></span>

<span data-ttu-id="41497-120">I föregående exempel `if` utvärderar uttrycket bara `$condition` variabeln.</span><span class="sxs-lookup"><span data-stu-id="41497-120">In the previous example, the `if` statement was just evaluating the `$condition` variable.</span></span> <span data-ttu-id="41497-121">Det var `$true` och skulle ha kört `Write-Output` kommandot inuti script block.</span><span class="sxs-lookup"><span data-stu-id="41497-121">It was `$true` and would have executed the `Write-Output` command inside the scriptblock.</span></span>

<span data-ttu-id="41497-122">På vissa språk kan du placera en enda kodrad efter `if` instruktionen och den körs.</span><span class="sxs-lookup"><span data-stu-id="41497-122">In some languages, you can place a single line of code after the `if` statement and it gets executed.</span></span> <span data-ttu-id="41497-123">Det är inte fallet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-123">That isn't the case in PowerShell.</span></span> <span data-ttu-id="41497-124">Du måste ange en fullständig `scriptblock` klammerparentes för att den ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="41497-124">You must provide a full `scriptblock` with braces for it to work correctly.</span></span>

## <a name="comparison-operators"></a><span data-ttu-id="41497-125">Jämförelseoperatorer</span><span class="sxs-lookup"><span data-stu-id="41497-125">Comparison operators</span></span>

<span data-ttu-id="41497-126">Den vanligaste användningen av `if` instruktionen för är att jämföra två objekt med varandra.</span><span class="sxs-lookup"><span data-stu-id="41497-126">The most common use of the `if` statement for is comparing two items with each other.</span></span> <span data-ttu-id="41497-127">PowerShell har särskilda operatorer för olika jämförelse scenarier.</span><span class="sxs-lookup"><span data-stu-id="41497-127">PowerShell has special operators for different comparison scenarios.</span></span> <span data-ttu-id="41497-128">När du använder en jämförelse operator jämförs värdet till vänster sida med värdet på den högra sidan.</span><span class="sxs-lookup"><span data-stu-id="41497-128">When you use a comparison operator, the value on the left-hand side is compared to the value on the right-hand side.</span></span>

### <a name="-eq-for-equality"></a><span data-ttu-id="41497-129">-EQ för likhet</span><span class="sxs-lookup"><span data-stu-id="41497-129">-eq for equality</span></span>

<span data-ttu-id="41497-130">`-eq`Gör en likhets kontroll mellan två värden för att se till att de är lika med varandra.</span><span class="sxs-lookup"><span data-stu-id="41497-130">The `-eq` does an equality check between two values to make sure they're equal to each other.</span></span>

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

<span data-ttu-id="41497-131">I det här exemplet tar jag ett känt värde `5` och jämför det med mitt `$value` för att se om de matchar.</span><span class="sxs-lookup"><span data-stu-id="41497-131">In this example, I'm taking a known value of `5` and comparing it to my `$value` to see if they match.</span></span>

<span data-ttu-id="41497-132">Ett möjligt användnings fall är att kontrol lera status för ett värde innan du vidtar en åtgärd på den.</span><span class="sxs-lookup"><span data-stu-id="41497-132">One possible use case is to check the status of a value before you take an action on it.</span></span> <span data-ttu-id="41497-133">Du kan få en tjänst och kontrol lera att statusen kördes innan du anropade `Restart-Service` den.</span><span class="sxs-lookup"><span data-stu-id="41497-133">You could get a service and check that the status was running before you called `Restart-Service` on it.</span></span>

<span data-ttu-id="41497-134">Det är vanligt på andra språk `==` , t. ex. C#, som används för likheter (t. ex.: `5 == $value` ) men som inte fungerar med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-134">It's common in other languages like C# to use `==` for equality (ex: `5 == $value`) but that doesn't work with PowerShell.</span></span> <span data-ttu-id="41497-135">Ett annat vanligt misstag är att använda likhets tecknet (t. ex. `5 = $value` ) som är reserverat för att tilldela värden till variabler.</span><span class="sxs-lookup"><span data-stu-id="41497-135">Another common mistake that people make is to use the equals sign (ex: `5 = $value`) that is reserved for assigning values to variables.</span></span> <span data-ttu-id="41497-136">Genom att placera ditt kända värde till vänster gör det att förskrivet mer olämpligt att göra.</span><span class="sxs-lookup"><span data-stu-id="41497-136">By placing your known value on the left, it makes that mistaken more awkward to make.</span></span>

<span data-ttu-id="41497-137">Den här operatorn (och andra) har några varianter.</span><span class="sxs-lookup"><span data-stu-id="41497-137">This operator (and others) has a few variations.</span></span>

- <span data-ttu-id="41497-138">`-eq`Skift läges okänsligt likhet</span><span class="sxs-lookup"><span data-stu-id="41497-138">`-eq` case-insensitive equality</span></span>
- <span data-ttu-id="41497-139">`-ieq`Skift läges okänsligt likhet</span><span class="sxs-lookup"><span data-stu-id="41497-139">`-ieq` case-insensitive equality</span></span>
- <span data-ttu-id="41497-140">`-ceq`Skift läges känslig likhet</span><span class="sxs-lookup"><span data-stu-id="41497-140">`-ceq` case-sensitive equality</span></span>

### <a name="-ne-not-equal"></a><span data-ttu-id="41497-141">-Ne inte lika med</span><span class="sxs-lookup"><span data-stu-id="41497-141">-ne not equal</span></span>

<span data-ttu-id="41497-142">Många operatorer har en relaterad operator som söker efter motsatt resultat.</span><span class="sxs-lookup"><span data-stu-id="41497-142">Many operators have a related operator that is checking for the opposite result.</span></span> <span data-ttu-id="41497-143">`-ne`kontrollerar att värdena inte motsvarar varandra.</span><span class="sxs-lookup"><span data-stu-id="41497-143">`-ne` verifies that the values don't equal each other.</span></span>

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

<span data-ttu-id="41497-144">Använd den här för att se till att åtgärden endast körs om värdet inte är det `5` .</span><span class="sxs-lookup"><span data-stu-id="41497-144">Use this to make sure that the action only executes if the value isn't `5`.</span></span> <span data-ttu-id="41497-145">En lämplig användning – fall där du bör kontrol lera om en tjänst var i körnings tillstånd innan du försöker starta den.</span><span class="sxs-lookup"><span data-stu-id="41497-145">A good use-cases where would be to check if a service was in the running state before you try to start it.</span></span>

<span data-ttu-id="41497-146">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-146">**Variations:**</span></span>

- <span data-ttu-id="41497-147">`-ne`Skift läges okänsligt är inte lika med</span><span class="sxs-lookup"><span data-stu-id="41497-147">`-ne` case-insensitive not equal</span></span>
- <span data-ttu-id="41497-148">`-ine`Skift läges okänsligt är inte lika med</span><span class="sxs-lookup"><span data-stu-id="41497-148">`-ine` case-insensitive not equal</span></span>
- <span data-ttu-id="41497-149">`-cne`Skift läges känsligt är inte lika med</span><span class="sxs-lookup"><span data-stu-id="41497-149">`-cne` case-sensitive not equal</span></span>

<span data-ttu-id="41497-150">Detta är inverterade variationer av `-eq` .</span><span class="sxs-lookup"><span data-stu-id="41497-150">These are inverse variations of `-eq`.</span></span> <span data-ttu-id="41497-151">Jag grupperar de här typerna tillsammans när jag listar varianter för andra operatorer.</span><span class="sxs-lookup"><span data-stu-id="41497-151">I'll group these types together when I list variations for other operators.</span></span>

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a><span data-ttu-id="41497-152">-gt-ge-lt-Le för större än eller mindre än</span><span class="sxs-lookup"><span data-stu-id="41497-152">-gt -ge -lt -le for greater than or less than</span></span>

<span data-ttu-id="41497-153">Dessa operatorer används vid kontroll för att se om ett värde är större eller mindre än ett annat värde.</span><span class="sxs-lookup"><span data-stu-id="41497-153">These operators are used when checking to see if a value is larger or smaller than another value.</span></span>
<span data-ttu-id="41497-154">`-gt -ge -lt -le`Stativ för GreaterThan, GreaterThanOrEqual, LessThan och LessThanOrEqual.</span><span class="sxs-lookup"><span data-stu-id="41497-154">The `-gt -ge -lt -le` stand for GreaterThan, GreaterThanOrEqual, LessThan, and LessThanOrEqual.</span></span>

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

<span data-ttu-id="41497-155">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-155">**Variations:**</span></span>

- <span data-ttu-id="41497-156">`-gt`större än</span><span class="sxs-lookup"><span data-stu-id="41497-156">`-gt` greater than</span></span>
- <span data-ttu-id="41497-157">`-igt`större än, SKIFT läges okänsligt</span><span class="sxs-lookup"><span data-stu-id="41497-157">`-igt` greater than, case-insensitive</span></span>
- <span data-ttu-id="41497-158">`-cgt`större än, SKIFT läges känsligt</span><span class="sxs-lookup"><span data-stu-id="41497-158">`-cgt` greater than, case-sensitive</span></span>
- <span data-ttu-id="41497-159">`-ge`större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="41497-159">`-ge` greater than or equal</span></span>
- <span data-ttu-id="41497-160">`-ige`större än eller lika med Skift läges okänslig</span><span class="sxs-lookup"><span data-stu-id="41497-160">`-ige` greater than or equal, case-insensitive</span></span>
- <span data-ttu-id="41497-161">`-cge`större än eller lika med Skift läges känslig</span><span class="sxs-lookup"><span data-stu-id="41497-161">`-cge` greater than or equal, case-sensitive</span></span>
- <span data-ttu-id="41497-162">`-lt`mindre än</span><span class="sxs-lookup"><span data-stu-id="41497-162">`-lt` less than</span></span>
- <span data-ttu-id="41497-163">`-ilt`mindre än, SKIFT läges okänsligt</span><span class="sxs-lookup"><span data-stu-id="41497-163">`-ilt` less than, case-insensitive</span></span>
- <span data-ttu-id="41497-164">`-clt`mindre än, SKIFT läges känsligt</span><span class="sxs-lookup"><span data-stu-id="41497-164">`-clt` less than, case-sensitive</span></span>
- <span data-ttu-id="41497-165">`-le`mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="41497-165">`-le` less than or equal</span></span>
- <span data-ttu-id="41497-166">`-ile`mindre än eller lika med Skift läges okänslig</span><span class="sxs-lookup"><span data-stu-id="41497-166">`-ile` less than or equal, case-insensitive</span></span>
- <span data-ttu-id="41497-167">`-cle`mindre än eller lika med Skift läges känslig</span><span class="sxs-lookup"><span data-stu-id="41497-167">`-cle` less than or equal, case-sensitive</span></span>

<span data-ttu-id="41497-168">Jag vet inte varför du skulle använda Skift läges känsliga och inkänsliga alternativ för dessa operatörer.</span><span class="sxs-lookup"><span data-stu-id="41497-168">I don't know why you would use case-sensitive and insensitive options for these operators.</span></span>

### <a name="-like-wildcard-matches"></a><span data-ttu-id="41497-169">– som jokertecken matchar</span><span class="sxs-lookup"><span data-stu-id="41497-169">-like wildcard matches</span></span>

<span data-ttu-id="41497-170">PowerShell har en egen syntax för jokertecken, och du kan använda den med `-like` operatorn.</span><span class="sxs-lookup"><span data-stu-id="41497-170">PowerShell has its own wildcard-based pattern matching syntax and you can use it with the `-like` operator.</span></span> <span data-ttu-id="41497-171">Dessa mönster för jokertecken är ganska enkla.</span><span class="sxs-lookup"><span data-stu-id="41497-171">These wildcard patterns are fairly basic.</span></span>

- <span data-ttu-id="41497-172">`?`matchar alla enskilda bokstäver</span><span class="sxs-lookup"><span data-stu-id="41497-172">`?` matches any single character</span></span>
- <span data-ttu-id="41497-173">`*`matchar valfritt antal tecken</span><span class="sxs-lookup"><span data-stu-id="41497-173">`*` matches any number of characters</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

<span data-ttu-id="41497-174">Det är viktigt att peka på att mönstret matchar hela strängen.</span><span class="sxs-lookup"><span data-stu-id="41497-174">It's important to point out that the pattern matches the whole string.</span></span> <span data-ttu-id="41497-175">Om du behöver matcha något i mitten av strängen måste du placera i `*` båda ändarna av strängen.</span><span class="sxs-lookup"><span data-stu-id="41497-175">If you need to match something in the middle of the string, you need to place the `*` on both ends of the string.</span></span>

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

<span data-ttu-id="41497-176">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-176">**Variations:**</span></span>

- <span data-ttu-id="41497-177">`-like`Skift läges okänsligt jokertecken</span><span class="sxs-lookup"><span data-stu-id="41497-177">`-like` case-insensitive wildcard</span></span>
- <span data-ttu-id="41497-178">`-ilike`Skift läges okänsligt jokertecken</span><span class="sxs-lookup"><span data-stu-id="41497-178">`-ilike` case-insensitive wildcard</span></span>
- <span data-ttu-id="41497-179">`-clike`Skift läges känsligt jokertecken</span><span class="sxs-lookup"><span data-stu-id="41497-179">`-clike` case-sensitive wildcard</span></span>
- <span data-ttu-id="41497-180">`-notlike`Skift läges okänsligt jokertecken matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-180">`-notlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="41497-181">`-inotlike`Skift läges okänsligt jokertecken matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-181">`-inotlike` case-insensitive wildcard not matched</span></span>
- <span data-ttu-id="41497-182">`-cnotlike`Skift läges känsligt jokertecken matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-182">`-cnotlike` case-sensitive wildcard not matched</span></span>

### <a name="-match-regular-expression"></a><span data-ttu-id="41497-183">– matcha reguljärt uttryck</span><span class="sxs-lookup"><span data-stu-id="41497-183">-match regular expression</span></span>

<span data-ttu-id="41497-184">Med `-match` operatorn kan du kontrol lera en sträng för en reguljär-uttrycks matchning.</span><span class="sxs-lookup"><span data-stu-id="41497-184">The `-match` operator allows you to check a string for a regular-expression-based match.</span></span> <span data-ttu-id="41497-185">Använd det här när mönster mönster inte är tillräckligt flexibla.</span><span class="sxs-lookup"><span data-stu-id="41497-185">Use this when the wildcard patterns aren't flexible enough for you.</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

<span data-ttu-id="41497-186">Ett regex-mönster matchar var som helst i strängen.</span><span class="sxs-lookup"><span data-stu-id="41497-186">A regex pattern matches anywhere in the string by default.</span></span> <span data-ttu-id="41497-187">Så du kan ange en under sträng som du vill matcha så här:</span><span class="sxs-lookup"><span data-stu-id="41497-187">So you can specify a substring that you want matched like this:</span></span>

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

<span data-ttu-id="41497-188">Regex är ett komplext språk som är eget och som är värt att titta på.</span><span class="sxs-lookup"><span data-stu-id="41497-188">Regex is a complex language of its own and worth looking into.</span></span> <span data-ttu-id="41497-189">Jag pratar mer om `-match` och [många sätt att använda regex][] i en annan artikel.</span><span class="sxs-lookup"><span data-stu-id="41497-189">I talk more about `-match` and [the many ways to use regex][] in another article.</span></span>

<span data-ttu-id="41497-190">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-190">**Variations:**</span></span>

- <span data-ttu-id="41497-191">`-match`Skift läges okänsligt regex</span><span class="sxs-lookup"><span data-stu-id="41497-191">`-match` case-insensitive regex</span></span>
- <span data-ttu-id="41497-192">`-imatch`Skift läges okänsligt regex</span><span class="sxs-lookup"><span data-stu-id="41497-192">`-imatch` case-insensitive regex</span></span>
- <span data-ttu-id="41497-193">`-cmatch`Skift läges känsligt regex</span><span class="sxs-lookup"><span data-stu-id="41497-193">`-cmatch` case-sensitive regex</span></span>
- <span data-ttu-id="41497-194">`-notmatch`Skift läges okänsligt regex matchade inte</span><span class="sxs-lookup"><span data-stu-id="41497-194">`-notmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="41497-195">`-inotmatch`Skift läges okänsligt regex matchade inte</span><span class="sxs-lookup"><span data-stu-id="41497-195">`-inotmatch` case-insensitive regex not matched</span></span>
- <span data-ttu-id="41497-196">`-cnotmatch`Skift läges känsligt regex matchas inte</span><span class="sxs-lookup"><span data-stu-id="41497-196">`-cnotmatch` case-sensitive regex not matched</span></span>

### <a name="-is-of-type"></a><span data-ttu-id="41497-197">-är av typen</span><span class="sxs-lookup"><span data-stu-id="41497-197">-is of type</span></span>

<span data-ttu-id="41497-198">Du kan kontrol lera ett värdes typ med `-is` operatorn.</span><span class="sxs-lookup"><span data-stu-id="41497-198">You can check a value's type with the `-is` operator.</span></span>

```powershell
if ( $value -is [string] )
{
    # do something
}
```

<span data-ttu-id="41497-199">Du kan använda det här om du arbetar med klasser eller accepterar olika objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="41497-199">You may use this if you're working with classes or accepting various objects over the pipeline.</span></span> <span data-ttu-id="41497-200">Du kan antingen ha en tjänst eller ett tjänst namn som inmatade.</span><span class="sxs-lookup"><span data-stu-id="41497-200">You could have either a service or a service name as your input.</span></span> <span data-ttu-id="41497-201">Kontrol lera sedan för att se om du har en tjänst och hämtar tjänsten om du bara har namnet.</span><span class="sxs-lookup"><span data-stu-id="41497-201">Then check to see if you have a service and fetch the service if you only have the name.</span></span>

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

<span data-ttu-id="41497-202">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-202">**Variations:**</span></span>

- <span data-ttu-id="41497-203">`-is`av typen</span><span class="sxs-lookup"><span data-stu-id="41497-203">`-is` of type</span></span>
- <span data-ttu-id="41497-204">`-isnot`inte av typen</span><span class="sxs-lookup"><span data-stu-id="41497-204">`-isnot` not of type</span></span>

## <a name="collection-operators"></a><span data-ttu-id="41497-205">Samlings operatörer</span><span class="sxs-lookup"><span data-stu-id="41497-205">Collection operators</span></span>

<span data-ttu-id="41497-206">När du använder föregående operatorer med ett enda värde är resultatet `$true` eller `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-206">When you use the previous operators with a single value, the result is `$true` or `$false`.</span></span> <span data-ttu-id="41497-207">Detta hanteras något annorlunda när du arbetar med en samling.</span><span class="sxs-lookup"><span data-stu-id="41497-207">This is handled slightly differently when working with a collection.</span></span> <span data-ttu-id="41497-208">Varje objekt i samlingen utvärderas och operatorn returnerar varje värde som utvärderas till `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-208">Each item in the collection gets evaluated and the operator returns every value that evaluates to `$true`.</span></span>

```powershell
PS> 1,2,3,4 -eq 3
3
```

<span data-ttu-id="41497-209">Detta fungerar fortfarande korrekt i en `if` instruktion.</span><span class="sxs-lookup"><span data-stu-id="41497-209">This still works correctly in a `if` statement.</span></span> <span data-ttu-id="41497-210">Ett värde returneras av operatören och sedan är hela instruktionen `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-210">So a value is returned by your operator, then the whole statement is `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

<span data-ttu-id="41497-211">Det finns en liten svällning som döljs i den information som jag behöver för att peka. När du använder `-ne` operatorn på det här sättet, är det lätt att titta närmare på logiken baklänges.</span><span class="sxs-lookup"><span data-stu-id="41497-211">There's one small trap hiding in the details here that I need to point out. When using the `-ne` operator this way, it's easy to mistakenly look at the logic backwards.</span></span> <span data-ttu-id="41497-212">`-ne` `$true` Om ett objekt i samlingen inte matchar ditt värde med hjälp av med en samling returneras det.</span><span class="sxs-lookup"><span data-stu-id="41497-212">Using `-ne` with a collection returns `$true` if any item in the collection doesn't match your value.</span></span>

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

<span data-ttu-id="41497-213">Detta kan se ut som ett smarta-stick, men vi har operatörer `-contains` och kan `-in` hantera detta mer effektivt.</span><span class="sxs-lookup"><span data-stu-id="41497-213">This may look like a clever trick, but we have operators `-contains` and `-in` that handle this more efficiently.</span></span> <span data-ttu-id="41497-214">Och `-notcontains` vad du förväntar dig.</span><span class="sxs-lookup"><span data-stu-id="41497-214">And `-notcontains` does what you expect.</span></span>

### <a name="-contains"></a><span data-ttu-id="41497-215">– innehåller</span><span class="sxs-lookup"><span data-stu-id="41497-215">-contains</span></span>

<span data-ttu-id="41497-216">`-contains`Operatorn kontrollerar insamlingen för ditt värde.</span><span class="sxs-lookup"><span data-stu-id="41497-216">The `-contains` operator checks the collection for your value.</span></span> <span data-ttu-id="41497-217">Så fort en matchning hittas returneras `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-217">As soon as it finds a match, it returns `$true`.</span></span>

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

<span data-ttu-id="41497-218">Detta är det bästa sättet att se om en samling innehåller ditt värde.</span><span class="sxs-lookup"><span data-stu-id="41497-218">This is the preferred way to see if a collection contains your value.</span></span> <span data-ttu-id="41497-219">`Where-Object`Om du använder (eller `-eq` ) guidas hela listan varje gång och är betydligt långsammare.</span><span class="sxs-lookup"><span data-stu-id="41497-219">Using `Where-Object` (or `-eq`) walks the entire list every time and is significantly slower.</span></span>

<span data-ttu-id="41497-220">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-220">**Variations:**</span></span>

- <span data-ttu-id="41497-221">`-contains`Skift läges okänslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-221">`-contains` case-insensitive match</span></span>
- <span data-ttu-id="41497-222">`-icontains`Skift läges okänslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-222">`-icontains` case-insensitive match</span></span>
- <span data-ttu-id="41497-223">`-ccontains`Skift läges känslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-223">`-ccontains` case-sensitive match</span></span>
- <span data-ttu-id="41497-224">`-notcontains`Skift läges känsligt matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-224">`-notcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="41497-225">`-inotcontains`Skift läges känsligt matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-225">`-inotcontains` case-insensitive not matched</span></span>
- <span data-ttu-id="41497-226">`-cnotcontains`Skift läges känsligt matchade inte</span><span class="sxs-lookup"><span data-stu-id="41497-226">`-cnotcontains` case-sensitive not matched</span></span>

### <a name="-in"></a><span data-ttu-id="41497-227">– in</span><span class="sxs-lookup"><span data-stu-id="41497-227">-in</span></span>

<span data-ttu-id="41497-228">`-in`Operatorn är precis som `-contains` operatorn, förutom att samlingen är på den högra sidan.</span><span class="sxs-lookup"><span data-stu-id="41497-228">The `-in` operator is just like the `-contains` operator except the collection is on the right-hand side.</span></span>

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

<span data-ttu-id="41497-229">**Olika**</span><span class="sxs-lookup"><span data-stu-id="41497-229">**Variations:**</span></span>

- <span data-ttu-id="41497-230">`-in`Skift läges okänslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-230">`-in` case-insensitive match</span></span>
- <span data-ttu-id="41497-231">`-iin`Skift läges okänslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-231">`-iin` case-insensitive match</span></span>
- <span data-ttu-id="41497-232">`-cin`Skift läges känslig matchning</span><span class="sxs-lookup"><span data-stu-id="41497-232">`-cin` case-sensitive match</span></span>
- <span data-ttu-id="41497-233">`-notin`Skift läges känsligt matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-233">`-notin` case-insensitive not matched</span></span>
- <span data-ttu-id="41497-234">`-inotin`Skift läges känsligt matchar inte</span><span class="sxs-lookup"><span data-stu-id="41497-234">`-inotin` case-insensitive not matched</span></span>
- <span data-ttu-id="41497-235">`-cnotin`Skift läges känsligt matchade inte</span><span class="sxs-lookup"><span data-stu-id="41497-235">`-cnotin` case-sensitive not matched</span></span>

## <a name="logical-operators"></a><span data-ttu-id="41497-236">Logiska operatorer</span><span class="sxs-lookup"><span data-stu-id="41497-236">Logical operators</span></span>

<span data-ttu-id="41497-237">Logiska operatorer används för att invertera eller kombinera andra uttryck.</span><span class="sxs-lookup"><span data-stu-id="41497-237">Logical operators are used to invert or combine other expressions.</span></span>

### <a name="-not"></a><span data-ttu-id="41497-238">– inte</span><span class="sxs-lookup"><span data-stu-id="41497-238">-not</span></span>

<span data-ttu-id="41497-239">`-not`Operatorn vänder ett uttryck från `$false` till `$true` eller från `$true` till `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-239">The `-not` operator flips an expression from `$false` to `$true` or from `$true` to `$false`.</span></span> <span data-ttu-id="41497-240">Här är ett exempel där vi vill utföra en åtgärd när `Test-Path` är `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-240">Here is an example where we want to perform an action when `Test-Path` is `$false`.</span></span>

```powershell
if ( -not ( Test-Path -Path $path ) )
```

<span data-ttu-id="41497-241">De flesta operatörer har vi talat med en variation där du inte behöver använda `-not` operatorn.</span><span class="sxs-lookup"><span data-stu-id="41497-241">Most of the operators we talked about do have a variation where you do not need to use the `-not` operator.</span></span> <span data-ttu-id="41497-242">Men det finns fortfarande tillfällen då det är användbart.</span><span class="sxs-lookup"><span data-stu-id="41497-242">But there are still times it is useful.</span></span>

### <a name="-operator"></a><span data-ttu-id="41497-243">!</span><span class="sxs-lookup"><span data-stu-id="41497-243">!</span></span> <span data-ttu-id="41497-244">operator</span><span class="sxs-lookup"><span data-stu-id="41497-244">operator</span></span>

<span data-ttu-id="41497-245">Du kan använda `!` som alias för `-not` .</span><span class="sxs-lookup"><span data-stu-id="41497-245">You can use `!` as an alias for `-not`.</span></span>

```powershell
if ( -not $value ){}
if ( !$value ){}
```

<span data-ttu-id="41497-246">Du kan se `!` använda mer av personer som kommer från ett annat språk, till exempel C#.</span><span class="sxs-lookup"><span data-stu-id="41497-246">You may see `!` used more by people that come from another languages like C#.</span></span> <span data-ttu-id="41497-247">Jag vill skriva ut den eftersom jag tycker att det är svårt att se när jag tittar på mina skript.</span><span class="sxs-lookup"><span data-stu-id="41497-247">I prefer to type it out because I find it hard to see when quickly looking at my scripts.</span></span>

### <a name="-and"></a><span data-ttu-id="41497-248">-och</span><span class="sxs-lookup"><span data-stu-id="41497-248">-and</span></span>

<span data-ttu-id="41497-249">Du kan kombinera uttryck med `-and` operatorn.</span><span class="sxs-lookup"><span data-stu-id="41497-249">You can combine expressions with the `-and` operator.</span></span> <span data-ttu-id="41497-250">När du gör det måste båda sidorna vara för att `$true` hela uttrycket ska vara `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-250">When you do that, both sides need to be `$true` for the whole expression to be `$true`.</span></span>

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

<span data-ttu-id="41497-251">I det exemplet `$age` måste vara 13 eller äldre för vänster sida och mindre än 55 för den högra sidan.</span><span class="sxs-lookup"><span data-stu-id="41497-251">In that example, `$age` must be 13 or older for the left side and less than 55 for the right side.</span></span> <span data-ttu-id="41497-252">Jag har lagt till extra parenteser för att göra det tydligare i det exemplet, men de är valfria så länge uttrycket är enkelt.</span><span class="sxs-lookup"><span data-stu-id="41497-252">I added extra parentheses to make it clearer in that example but they're optional as long as the expression is simple.</span></span> <span data-ttu-id="41497-253">Här är samma exempel utan dem.</span><span class="sxs-lookup"><span data-stu-id="41497-253">Here is the same example without them.</span></span>

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

<span data-ttu-id="41497-254">Utvärderingen sker från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="41497-254">Evaluation happens from left to right.</span></span> <span data-ttu-id="41497-255">Om det första objektet utvärderas till `$false` avslutas det tidigt och det utför inte rätt jämförelse.</span><span class="sxs-lookup"><span data-stu-id="41497-255">If the first item evaluates to `$false`, it exits early and doesn't perform the right comparison.</span></span> <span data-ttu-id="41497-256">Detta är praktiskt när du behöver kontrol lera att det finns ett värde innan du använder det.</span><span class="sxs-lookup"><span data-stu-id="41497-256">This is handy when you need to make sure a value exists before you use it.</span></span> <span data-ttu-id="41497-257">Genererar till exempel `Test-Path` ett fel om du ger den en `$null` sökväg.</span><span class="sxs-lookup"><span data-stu-id="41497-257">For example, `Test-Path` throws an error if you give it a `$null` path.</span></span>

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a><span data-ttu-id="41497-258">-eller</span><span class="sxs-lookup"><span data-stu-id="41497-258">-or</span></span>

<span data-ttu-id="41497-259">Med `-or` kan du ange två uttryck och returnerar `$true` om något av dem är `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-259">The `-or` allows for you to specify two expressions and returns `$true` if either one of them is `$true`.</span></span>

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

<span data-ttu-id="41497-260">Precis som med `-and` operatorn sker utvärderingen från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="41497-260">Just like with the `-and` operator, the evaluation happens from left to right.</span></span> <span data-ttu-id="41497-261">Förutom att om den första delen är `$true` , är hela instruktionen `$true` och bearbetar inte resten av uttrycket.</span><span class="sxs-lookup"><span data-stu-id="41497-261">Except that if the first part is `$true`, then the whole statement is `$true` and it doesn't process the rest of the expression.</span></span>

<span data-ttu-id="41497-262">Notera också hur syntaxen fungerar för de här operatorerna.</span><span class="sxs-lookup"><span data-stu-id="41497-262">Also make note of how the syntax works for these operators.</span></span> <span data-ttu-id="41497-263">Du behöver två separata uttryck.</span><span class="sxs-lookup"><span data-stu-id="41497-263">You need two separate expressions.</span></span> <span data-ttu-id="41497-264">Jag har sett att användare försöker göra något som liknar detta `$value -eq 5 -or 6` utan att realisera sitt misstag.</span><span class="sxs-lookup"><span data-stu-id="41497-264">I have seen users try to do something like this `$value -eq 5 -or 6` without realizing their mistake.</span></span>

### <a name="-xor-exclusive-or"></a><span data-ttu-id="41497-265">– XOR exklusivt eller</span><span class="sxs-lookup"><span data-stu-id="41497-265">-xor exclusive or</span></span>

<span data-ttu-id="41497-266">Det här är lite ovanligt.</span><span class="sxs-lookup"><span data-stu-id="41497-266">This one is a little unusual.</span></span> <span data-ttu-id="41497-267">`-xor`tillåter endast ett uttryck att utvärdera till `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-267">`-xor` allows only one expression to evaluate to `$true`.</span></span> <span data-ttu-id="41497-268">Så om båda elementen är `$false` eller båda elementen `$true` är hela uttrycket `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-268">So if both items are `$false` or both items are `$true`, then the whole expression is `$false`.</span></span> <span data-ttu-id="41497-269">Ett annat sätt att titta på det här är att uttrycket bara är `$true` om resultatet av uttrycket är olika.</span><span class="sxs-lookup"><span data-stu-id="41497-269">Another way to look at this is the expression is only `$true` when the results of the expression are different.</span></span>

<span data-ttu-id="41497-270">Det är ovanligt att vem som helst skulle använda den logiska operatorn och jag kan inte se ett användbart exempel på varför jag skulle använda den.</span><span class="sxs-lookup"><span data-stu-id="41497-270">It's rare that anyone would ever use this logical operator and I can't think up a good example as to why I would ever use it.</span></span>

## <a name="bitwise-operators"></a><span data-ttu-id="41497-271">Bitvisa operatorer</span><span class="sxs-lookup"><span data-stu-id="41497-271">Bitwise operators</span></span>

<span data-ttu-id="41497-272">Bitvisa operatorer utför beräkningar på bitarna i värdena och genererar ett nytt värde som resultat.</span><span class="sxs-lookup"><span data-stu-id="41497-272">Bitwise operators perform calculations on the bits within the values and produce a new value as the result.</span></span> <span data-ttu-id="41497-273">Andra undervisnings [operatorer][] ligger utanför den här artikelns omfång, men här är listan över dem.</span><span class="sxs-lookup"><span data-stu-id="41497-273">Teaching [bitwise operators][] is beyond the scope of this article, but here is the list the them.</span></span>

- <span data-ttu-id="41497-274">`-band`binär och</span><span class="sxs-lookup"><span data-stu-id="41497-274">`-band` binary AND</span></span>
- <span data-ttu-id="41497-275">`-bor`binär eller</span><span class="sxs-lookup"><span data-stu-id="41497-275">`-bor` binary OR</span></span>
- <span data-ttu-id="41497-276">`-bxor`binärt exklusivt eller</span><span class="sxs-lookup"><span data-stu-id="41497-276">`-bxor` binary exclusive OR</span></span>
- <span data-ttu-id="41497-277">`-bnot`binär NOT</span><span class="sxs-lookup"><span data-stu-id="41497-277">`-bnot` binary NOT</span></span>
- <span data-ttu-id="41497-278">`-shl`Skift vänster</span><span class="sxs-lookup"><span data-stu-id="41497-278">`-shl` shift left</span></span>
- <span data-ttu-id="41497-279">`-shr`Shift, höger</span><span class="sxs-lookup"><span data-stu-id="41497-279">`-shr` shift right</span></span>

## <a name="powershell-expressions"></a><span data-ttu-id="41497-280">PowerShell-uttryck</span><span class="sxs-lookup"><span data-stu-id="41497-280">PowerShell expressions</span></span>

<span data-ttu-id="41497-281">Vi kan använda normal PowerShell i villkors instruktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-281">We can use normal PowerShell inside the condition statement.</span></span>

```powershell
if ( Test-Path -Path $Path )
```

<span data-ttu-id="41497-282">`Test-Path`Returnerar `$true` eller `$false` när den körs.</span><span class="sxs-lookup"><span data-stu-id="41497-282">`Test-Path` returns `$true` or `$false` when it executes.</span></span> <span data-ttu-id="41497-283">Detta gäller även för kommandon som returnerar andra värden.</span><span class="sxs-lookup"><span data-stu-id="41497-283">This also applies to commands that return other values.</span></span>

```powershell
if ( Get-Process Notepad* )
```

<span data-ttu-id="41497-284">Den utvärderas till `$true` om det finns en returnerad process och `$false` om there'sn'thing.</span><span class="sxs-lookup"><span data-stu-id="41497-284">It evaluates to `$true` if there's a returned process and `$false` if there'sn'thing.</span></span> <span data-ttu-id="41497-285">Den är perfekt giltig att använda pipeline-uttryck eller andra PowerShell-uttryck som detta:</span><span class="sxs-lookup"><span data-stu-id="41497-285">It's perfectly valid to use pipeline expressions or other PowerShell statements like this:</span></span>

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

<span data-ttu-id="41497-286">Dessa uttryck kan kombineras med `-and` `-or` -och-operatorer, men du kan behöva använda parenteser för att dela upp dem i under uttryck.</span><span class="sxs-lookup"><span data-stu-id="41497-286">These expressions can be combined with each other with the `-and` and `-or` operators, but you may have to use parenthesis to break them into subexpressions.</span></span>

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a><span data-ttu-id="41497-287">Söker efter $null</span><span class="sxs-lookup"><span data-stu-id="41497-287">Checking for $null</span></span>

<span data-ttu-id="41497-288">Inget resultat eller ett `$null` värde utvärderas `$false` i `if` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-288">Having a no result or a `$null` value evaluates to `$false` in the `if` statement.</span></span> <span data-ttu-id="41497-289">När du kontrollerar specifikt för är `$null` det bäst att placera `$null` på den vänstra sidan.</span><span class="sxs-lookup"><span data-stu-id="41497-289">When checking specifically for `$null`, it's a best practice to place the `$null` on the left-hand side.</span></span>

```powershell
if ( $null -eq $value )
```

<span data-ttu-id="41497-290">Det finns ganska några olika delarna när du hanterar `$null` värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-290">There are quite a few nuances when dealing with `$null` values in PowerShell.</span></span> <span data-ttu-id="41497-291">Om du är intresse rad av simhopp djupare har jag en artikel om [allt du ville veta mer om $null][].</span><span class="sxs-lookup"><span data-stu-id="41497-291">If you're interested in diving deeper, I have an article about [everything you wanted to know about $null][].</span></span>

### <a name="variable-assignment"></a><span data-ttu-id="41497-292">Variabeltilldelning</span><span class="sxs-lookup"><span data-stu-id="41497-292">Variable assignment</span></span>

<span data-ttu-id="41497-293">Jag har nästan glömt att lägga till det här felet förrän [Prasoon Karunan V][] har beminnas mig.</span><span class="sxs-lookup"><span data-stu-id="41497-293">I almost forgot to add this one until [Prasoon Karunan V][] reminded me of it.</span></span>

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

<span data-ttu-id="41497-294">Normalt när du tilldelar ett värde till en variabel, skickas värdet inte till pipelinen eller konsolen.</span><span class="sxs-lookup"><span data-stu-id="41497-294">Normally when you assign a value to a variable, the value isn't passed onto the pipeline or console.</span></span> <span data-ttu-id="41497-295">När du gör en variabel tilldelning i ett under uttryck skickas den vidare till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="41497-295">When you do a variable assignment in a sub expression, it does get passed on to the pipeline.</span></span>

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

<span data-ttu-id="41497-296">Se hur `$first` tilldelningen inte har några utdata och `$second` tilldelningen gör?</span><span class="sxs-lookup"><span data-stu-id="41497-296">See how the `$first` assignment has no output and the `$second` assignment does?</span></span> <span data-ttu-id="41497-297">När en tilldelning görs i en `if` instruktion körs den precis som `$second` tilldelningen ovan.</span><span class="sxs-lookup"><span data-stu-id="41497-297">When an assignment is done in an `if` statement, it executes just like the `$second` assignment above.</span></span> <span data-ttu-id="41497-298">Här är ett rent exempel på hur du kan använda det:</span><span class="sxs-lookup"><span data-stu-id="41497-298">Here is a clean example on how you could use it:</span></span>

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

<span data-ttu-id="41497-299">Om `$process` tilldelas ett värde `$true` stoppas instruktionen och `$process` stoppas.</span><span class="sxs-lookup"><span data-stu-id="41497-299">If `$process` gets assigned a value, then the statement is `$true` and `$process` gets stopped.</span></span>

<span data-ttu-id="41497-300">Se till att du inte förväxla detta med `-eq` eftersom det inte är en likhets kontroll.</span><span class="sxs-lookup"><span data-stu-id="41497-300">Make sure you don't confuse this with `-eq` because this isn't an equality check.</span></span> <span data-ttu-id="41497-301">Detta är en mer skymd funktion som de flesta inte inser fungerar på det här sättet.</span><span class="sxs-lookup"><span data-stu-id="41497-301">This is a more obscure feature that most people don't realize works this way.</span></span>

## <a name="alternate-execution-path"></a><span data-ttu-id="41497-302">Sökväg för alternativ körning</span><span class="sxs-lookup"><span data-stu-id="41497-302">Alternate execution path</span></span>

<span data-ttu-id="41497-303">Med `if` instruktionen kan du ange en åtgärd för inte bara när instruktionen är `$true` , utan även för när den är `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-303">The `if` statement allows you to specify an action for not only when the statement is `$true`, but also for when it's `$false`.</span></span> <span data-ttu-id="41497-304">Det är här som `else` instruktionen kommer att spelas upp.</span><span class="sxs-lookup"><span data-stu-id="41497-304">This is where the `else` statement comes into play.</span></span>

### <a name="else"></a><span data-ttu-id="41497-305">else</span><span class="sxs-lookup"><span data-stu-id="41497-305">else</span></span>

<span data-ttu-id="41497-306">`else`Instruktionen är alltid den sista delen av `if` instruktionen när den används.</span><span class="sxs-lookup"><span data-stu-id="41497-306">The `else` statement is always the last part of the `if` statement when used.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

<span data-ttu-id="41497-307">I det här exemplet kontrollerar vi `$path` för att se till att det är en fil.</span><span class="sxs-lookup"><span data-stu-id="41497-307">In this example, we check the `$path` to make sure it's a file.</span></span> <span data-ttu-id="41497-308">Om vi hittar filen flyttar vi den.</span><span class="sxs-lookup"><span data-stu-id="41497-308">If we find the file, we move it.</span></span> <span data-ttu-id="41497-309">Annars skriver vi en varning.</span><span class="sxs-lookup"><span data-stu-id="41497-309">If not, we write a warning.</span></span> <span data-ttu-id="41497-310">Den här typen av branchningslogik är mycket vanlig.</span><span class="sxs-lookup"><span data-stu-id="41497-310">This type of branching logic is very common.</span></span>

### <a name="nested-if"></a><span data-ttu-id="41497-311">Kapslad om</span><span class="sxs-lookup"><span data-stu-id="41497-311">Nested if</span></span>

<span data-ttu-id="41497-312">`if` `else` Instruktionen och tar ett skript block, så vi kan placera alla PowerShell-kommandon i dem, inklusive en annan `if` instruktion.</span><span class="sxs-lookup"><span data-stu-id="41497-312">The `if` and `else` statements take a script block, so we can place any PowerShell command inside them, including another `if` statement.</span></span> <span data-ttu-id="41497-313">Detta gör att du kan använda mycket mer komplicerad logik.</span><span class="sxs-lookup"><span data-stu-id="41497-313">This allows you to make use of much more complicated logic.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

<span data-ttu-id="41497-314">I det här exemplet testar vi den glad sökvägen först och gör sedan en åtgärd på den.</span><span class="sxs-lookup"><span data-stu-id="41497-314">In this example, we test the happy path first and then take action on it.</span></span> <span data-ttu-id="41497-315">Om detta Miss lyckas gör vi en annan kontroll och ger mer detaljerad information till användaren.</span><span class="sxs-lookup"><span data-stu-id="41497-315">If that fails, we do another check and to provide more detailed information to the user.</span></span>

### <a name="elseif"></a><span data-ttu-id="41497-316">ElseIf</span><span class="sxs-lookup"><span data-stu-id="41497-316">elseif</span></span>

<span data-ttu-id="41497-317">Vi är inte begränsade till bara en enda villkorlig kontroll.</span><span class="sxs-lookup"><span data-stu-id="41497-317">We aren't limited to just a single conditional check.</span></span> <span data-ttu-id="41497-318">Vi kan kedja `if` och `else` uttryck tillsammans i stället för att kapsla dem med hjälp av `elseif` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-318">We can chain `if` and `else` statements together instead of nesting them by using the `elseif` statement.</span></span>

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

<span data-ttu-id="41497-319">Körningen sker uppifrån och ned.</span><span class="sxs-lookup"><span data-stu-id="41497-319">The execution happens from the top to the bottom.</span></span> <span data-ttu-id="41497-320">Den översta `if` instruktionen utvärderas först.</span><span class="sxs-lookup"><span data-stu-id="41497-320">The top `if` statement is evaluated first.</span></span> <span data-ttu-id="41497-321">Om det är `$false` det flyttas det nedåt till nästa `elseif` eller `else` i listan.</span><span class="sxs-lookup"><span data-stu-id="41497-321">If that is `$false`, then it moves down to the next `elseif` or `else` in the list.</span></span> <span data-ttu-id="41497-322">Det sista `else` är den standard åtgärd som ska vidtas om ingen av de andra returneras `$true` .</span><span class="sxs-lookup"><span data-stu-id="41497-322">That last `else` is the default action to take if none of the others return `$true`.</span></span>

### <a name="switch"></a><span data-ttu-id="41497-323">växla</span><span class="sxs-lookup"><span data-stu-id="41497-323">switch</span></span>

<span data-ttu-id="41497-324">Nu måste jag nämna `switch` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-324">At this point, I need to mention the `switch` statement.</span></span> <span data-ttu-id="41497-325">Den innehåller en alternativ syntax för att utföra flera jämförelser med ett värde.</span><span class="sxs-lookup"><span data-stu-id="41497-325">It provides an alternate syntax for doing multiple comparisons with a value.</span></span> <span data-ttu-id="41497-326">Med `switch` kan du ange ett uttryck och resultatet jämförs med flera olika värden.</span><span class="sxs-lookup"><span data-stu-id="41497-326">With the `switch`, you specify an expression and that result gets compared with several different values.</span></span> <span data-ttu-id="41497-327">Om något av dessa värden matchar, körs det matchande kod blocket.</span><span class="sxs-lookup"><span data-stu-id="41497-327">If one of those values match, the matching code block is executed.</span></span> <span data-ttu-id="41497-328">Ta en titt på det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="41497-328">Take a look at this example:</span></span>

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

<span data-ttu-id="41497-329">Det finns tre möjliga värden som kan matcha `$itemType` .</span><span class="sxs-lookup"><span data-stu-id="41497-329">There three possible values that can match the `$itemType`.</span></span> <span data-ttu-id="41497-330">I det här fallet matchar den med `Role` .</span><span class="sxs-lookup"><span data-stu-id="41497-330">In this case, it matches with `Role`.</span></span> <span data-ttu-id="41497-331">Jag använde ett enkelt exempel bara för att ge dig viss exponering för `switch` operatorn.</span><span class="sxs-lookup"><span data-stu-id="41497-331">I used a simple example just to give you some exposure to the `switch` operator.</span></span> <span data-ttu-id="41497-332">Jag pratar mer om [allt du ville veta om switch-satsen][] i en annan artikel.</span><span class="sxs-lookup"><span data-stu-id="41497-332">I talk more about [everything you ever wanted to know about the switch statement][] in another article.</span></span>

## <a name="pipeline"></a><span data-ttu-id="41497-333">Pipeline</span><span class="sxs-lookup"><span data-stu-id="41497-333">Pipeline</span></span>

<span data-ttu-id="41497-334">Pipelinen är en unik och viktig funktion i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-334">The pipeline is a unique and important feature of PowerShell.</span></span> <span data-ttu-id="41497-335">Ett värde som inte är undertryckt eller som har tilldelats en variabel placeras i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="41497-335">Any value that isn't suppressed or assigned to a variable gets placed in the pipeline.</span></span> <span data-ttu-id="41497-336">På ett sätt kan `if` vi dra nytta av pipelinen på ett sätt som inte alltid är uppenbart.</span><span class="sxs-lookup"><span data-stu-id="41497-336">The `if` provides us a way to take advantage of the pipeline in a way that isn't always obvious.</span></span>

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

<span data-ttu-id="41497-337">Varje skript block placerar resultatet av kommandona eller värdet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="41497-337">Each script block is placing the results the commands or the value into the pipeline.</span></span> <span data-ttu-id="41497-338">Sedan tilldelar vi resultatet av IF-instruktionen till `$discount` variabeln.</span><span class="sxs-lookup"><span data-stu-id="41497-338">Then we assign the result of the if statement to the `$discount` variable.</span></span> <span data-ttu-id="41497-339">Det här exemplet kan ha lika enkelt tilldelat dessa värden till `$discount` variabeln direkt i varje script block.</span><span class="sxs-lookup"><span data-stu-id="41497-339">That example could have just as easily assigned those values to the `$discount` variable directly in each scriptblock.</span></span> <span data-ttu-id="41497-340">Jag kan inte säga att jag använder detta med `if` instruktionen ofta, men jag har ett exempel där jag använde detta nyligen.</span><span class="sxs-lookup"><span data-stu-id="41497-340">I can't say that I use this with the `if` statement often, but I do have an example where I used this recently.</span></span>

### <a name="array-inline"></a><span data-ttu-id="41497-341">Infoga matris</span><span class="sxs-lookup"><span data-stu-id="41497-341">Array inline</span></span>

<span data-ttu-id="41497-342">Jag har en funktion som kallas [Invoke-SnowSql][] som startar en körbar fil med flera kommando rads argument.</span><span class="sxs-lookup"><span data-stu-id="41497-342">I have a function called [Invoke-SnowSql][] that launches an executable with several command-line arguments.</span></span> <span data-ttu-id="41497-343">Här är ett klipp från funktionen där jag skapar en argument mat ris.</span><span class="sxs-lookup"><span data-stu-id="41497-343">Here is a clip from that function where I build the array of arguments.</span></span>

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

<span data-ttu-id="41497-344">`$Debug` `$Path` Variablerna och är parametrar för den funktion som slutanvändaren tillhandahåller.</span><span class="sxs-lookup"><span data-stu-id="41497-344">The `$Debug` and `$Path` variables are parameters on the function that are provided by the end user.</span></span>
<span data-ttu-id="41497-345">Jag utvärderar dem inuti initieringen av min matris.</span><span class="sxs-lookup"><span data-stu-id="41497-345">I evaluate them inline inside the initialization of my array.</span></span> <span data-ttu-id="41497-346">Om `$Debug` är sant hamnar dessa värden på `$snowSqlParam` rätt plats.</span><span class="sxs-lookup"><span data-stu-id="41497-346">If `$Debug` is true, then those values fall into the `$snowSqlParam` in the correct place.</span></span> <span data-ttu-id="41497-347">Samma gäller för `$Path` variabeln.</span><span class="sxs-lookup"><span data-stu-id="41497-347">Same holds true for the `$Path` variable.</span></span>

## <a name="simplify-complex-operations"></a><span data-ttu-id="41497-348">Förenkla komplexa åtgärder</span><span class="sxs-lookup"><span data-stu-id="41497-348">Simplify complex operations</span></span>

<span data-ttu-id="41497-349">Det är ofrånkomligt att du stöter på en situation som har för många jämförelser för att kontrol lera och instruktionen IF rullar ut på skärmens högra sida.</span><span class="sxs-lookup"><span data-stu-id="41497-349">It's inevitable that you run into a situation that has way too many comparisons to check and your if statement scrolls way off the right side of the screen.</span></span>

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

<span data-ttu-id="41497-350">De kan vara svåra att läsa och det gör det svårare att göra misstag.</span><span class="sxs-lookup"><span data-stu-id="41497-350">They can be hard to read and that make you more prone to make mistakes.</span></span> <span data-ttu-id="41497-351">Det finns några saker som vi kan göra med det.</span><span class="sxs-lookup"><span data-stu-id="41497-351">There are a few things we can do about that.</span></span>

### <a name="line-continuation"></a><span data-ttu-id="41497-352">Rad fortsättning</span><span class="sxs-lookup"><span data-stu-id="41497-352">Line continuation</span></span>

<span data-ttu-id="41497-353">Det finns några operatörer i PowerShell som låter dig figursätta kommandot till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="41497-353">There some operators in PowerShell that let you wrap you command to the next line.</span></span> <span data-ttu-id="41497-354">De logiska operatörerna `-and` och `-or` är bra operatörer att använda om du vill dela upp uttrycket i flera rader.</span><span class="sxs-lookup"><span data-stu-id="41497-354">The logical operators `-and` and `-or` are good operators to use if you want to break your expression into multiple lines.</span></span>

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

<span data-ttu-id="41497-355">Det finns fortfarande mycket som finns där, men att placera varje del på en egen linje gör stor skillnad.</span><span class="sxs-lookup"><span data-stu-id="41497-355">There's still a lot going on there, but placing each piece on its own line makes a big difference.</span></span>
<span data-ttu-id="41497-356">Jag använder vanligt vis det här när jag får fler än två jämförelser eller om jag måste bläddra till höger för att läsa någon av logiken.</span><span class="sxs-lookup"><span data-stu-id="41497-356">I generally use this when I get more than two comparisons or if I have to scroll to the right to read any of the logic.</span></span>

### <a name="pre-calculating-results"></a><span data-ttu-id="41497-357">För beräknings resultat</span><span class="sxs-lookup"><span data-stu-id="41497-357">Pre-calculating results</span></span>

<span data-ttu-id="41497-358">Vi kan ta den instruktionen från IF-instruktionen och bara kontrol lera resultatet.</span><span class="sxs-lookup"><span data-stu-id="41497-358">We can take that statement out of the if statement and only check the result.</span></span>

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

<span data-ttu-id="41497-359">Det här är bara att ha mycket renare än det föregående exemplet.</span><span class="sxs-lookup"><span data-stu-id="41497-359">This just feels much cleaner than the previous example.</span></span> <span data-ttu-id="41497-360">Du får också möjlighet att använda ett variabel namn som förklarar vad det är som du verkligen kontrollerar.</span><span class="sxs-lookup"><span data-stu-id="41497-360">You also are given an opportunity to use a variable name that explains what it's that you're really checking.</span></span> <span data-ttu-id="41497-361">Detta är även ett exempel på självdokumenterande kod som sparar onödiga kommentarer.</span><span class="sxs-lookup"><span data-stu-id="41497-361">This is also and example of self-documenting code that saves unnecessary comments.</span></span>

### <a name="multiple-if-statements"></a><span data-ttu-id="41497-362">Multiple IF-instruktioner</span><span class="sxs-lookup"><span data-stu-id="41497-362">Multiple if statements</span></span>

<span data-ttu-id="41497-363">Vi kan dela upp det i flera instruktioner och kontrol lera dem en i taget.</span><span class="sxs-lookup"><span data-stu-id="41497-363">We can break this up into multiple statements and check them one at a time.</span></span> <span data-ttu-id="41497-364">I det här fallet använder vi en flagga eller en spårnings variabel för att kombinera resultaten.</span><span class="sxs-lookup"><span data-stu-id="41497-364">In this case, we use a flag or a tracking variable to combine the results.</span></span>

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

<span data-ttu-id="41497-365">Jag måste invertera logiken för att flagga logiken ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="41497-365">I did have to invert the logic to make the flag logic work correctly.</span></span> <span data-ttu-id="41497-366">Varje utvärdering är en enskild `if` instruktion.</span><span class="sxs-lookup"><span data-stu-id="41497-366">Each evaluation is an individual `if` statement.</span></span> <span data-ttu-id="41497-367">Fördelen med detta är att när du felsöker kan du se exakt vad logiken gör.</span><span class="sxs-lookup"><span data-stu-id="41497-367">The advantage of this is that when you're debugging, you can tell exactly what the logic is doing.</span></span> <span data-ttu-id="41497-368">Jag har kunnat lägga till mycket bättre utförlighet på samma tid.</span><span class="sxs-lookup"><span data-stu-id="41497-368">I was able to add much better verbosity at the same time.</span></span>

<span data-ttu-id="41497-369">Den uppenbara nack delen är att det är så mycket mer kod att skriva.</span><span class="sxs-lookup"><span data-stu-id="41497-369">The obvious downside is that it's so much more code to write.</span></span> <span data-ttu-id="41497-370">Koden är mer komplex att titta på när den tar en enda rad logik och expanderar den till 25 eller fler rader.</span><span class="sxs-lookup"><span data-stu-id="41497-370">The code is more complex to look at as it takes a single line of logic and explodes it into 25 or more lines.</span></span>

### <a name="using-functions"></a><span data-ttu-id="41497-371">Använda funktioner</span><span class="sxs-lookup"><span data-stu-id="41497-371">Using functions</span></span>

<span data-ttu-id="41497-372">Vi kan också flytta alla validerings logiken till en funktion.</span><span class="sxs-lookup"><span data-stu-id="41497-372">We can also move all that validation logic into a function.</span></span> <span data-ttu-id="41497-373">Titta på hur det här ser ut snabbt.</span><span class="sxs-lookup"><span data-stu-id="41497-373">Look at how clean this looks at a glance.</span></span>

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

<span data-ttu-id="41497-374">Du måste fortfarande skapa funktionen för att utföra verifieringen, men den gör den här koden mycket enklare att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="41497-374">You still have to create the function to do the validation, but it makes this code much easier to work with.</span></span> <span data-ttu-id="41497-375">Det gör det enklare att testa den här koden.</span><span class="sxs-lookup"><span data-stu-id="41497-375">It makes this code easier to test.</span></span> <span data-ttu-id="41497-376">I dina tester kan du modellera samtalet `Test-ADDriveConfiguration` och du behöver bara två test för den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="41497-376">In your tests, you can mock the call to `Test-ADDriveConfiguration` and you only need two tests for this function.</span></span> <span data-ttu-id="41497-377">En där den returnerar `$true` och en där den returnerar `$false` .</span><span class="sxs-lookup"><span data-stu-id="41497-377">One where it returns `$true` and one where it returns `$false`.</span></span> <span data-ttu-id="41497-378">Testning av den andra funktionen är enklare eftersom det är så litet.</span><span class="sxs-lookup"><span data-stu-id="41497-378">Testing the other function is simpler because it's so small.</span></span>

<span data-ttu-id="41497-379">Bröd texten i den funktionen kan fortfarande vara att en-liner som vi startade med eller den nedbrutena logiken som vi använde i det sista avsnittet.</span><span class="sxs-lookup"><span data-stu-id="41497-379">The body of that function could still be that one-liner we started with or the exploded logic that we used in the last section.</span></span> <span data-ttu-id="41497-380">Detta fungerar bra för båda scenarierna och gör att du enkelt kan ändra implementeringen senare.</span><span class="sxs-lookup"><span data-stu-id="41497-380">This works well for both scenarios and allows you to easily change that implementation later.</span></span>

## <a name="error-handling"></a><span data-ttu-id="41497-381">Felhantering</span><span class="sxs-lookup"><span data-stu-id="41497-381">Error handling</span></span>

<span data-ttu-id="41497-382">En viktig användning av `if` instruktionen är att söka efter fel villkor innan du stöter på fel.</span><span class="sxs-lookup"><span data-stu-id="41497-382">One important use of the `if` statement is to check for error conditions before you run into errors.</span></span> <span data-ttu-id="41497-383">Ett exempel är att kontrol lera om det redan finns en mapp innan du försöker skapa den.</span><span class="sxs-lookup"><span data-stu-id="41497-383">A good example is to check if a folder already exists before you try to create it.</span></span>

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

<span data-ttu-id="41497-384">Jag vill säga att om du förväntar dig att ett undantag inträffar är det egentligen inget undantag.</span><span class="sxs-lookup"><span data-stu-id="41497-384">I like to say that if you expect an exception to happen, then it's not really an exception.</span></span> <span data-ttu-id="41497-385">Kontrol lera värdena och kontrol lera dina villkor där du kan.</span><span class="sxs-lookup"><span data-stu-id="41497-385">So check your values and validate your conditions where you can.</span></span>

<span data-ttu-id="41497-386">Om du vill få lite mer om faktisk undantags hantering har jag en artikel om [allt du någonsin ville veta om undantag][].</span><span class="sxs-lookup"><span data-stu-id="41497-386">If you want to dive a little more into actual exception handling, I have an article on [everything you ever wanted to know about exceptions][].</span></span>

## <a name="final-words"></a><span data-ttu-id="41497-387">Sista ord</span><span class="sxs-lookup"><span data-stu-id="41497-387">Final words</span></span>

<span data-ttu-id="41497-388">`if`Instruktionen är en enkel instruktion men är en grundläggande del av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41497-388">The `if` statement is such a simple statement but is a fundamental piece of PowerShell.</span></span> <span data-ttu-id="41497-389">Du kommer att se hur du använder det här flera gånger i nästan alla skript som du skriver.</span><span class="sxs-lookup"><span data-stu-id="41497-389">You will find yourself using this multiple times in almost every script you write.</span></span> <span data-ttu-id="41497-390">Jag hoppas att du har en bättre förståelse än du hade tidigare.</span><span class="sxs-lookup"><span data-stu-id="41497-390">I hope you have a better understanding than you had before.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[original version]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[eventuella]: /powershell/module/microsoft.powershell.core/about/about_if
[if]: /powershell/module/microsoft.powershell.core/about/about_if
[bitvisa operatorer]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[bitwise operators]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[the many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[allt du ville veta mer om undantag]: everything-about-exceptions.md
[everything you ever wanted to know about exceptions]: everything-about-exceptions.md
[allt du ville veta mer om $null]: everything-about-null.md
[everything you wanted to know about $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[allt du ville veta om switch-instruktionen]: everything-about-switch.md
[everything you ever wanted to know about the switch statement]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
