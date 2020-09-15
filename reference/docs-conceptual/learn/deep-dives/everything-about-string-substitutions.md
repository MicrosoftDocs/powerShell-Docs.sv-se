---
title: Allt du ville veta om variabel ersättning i strängar
description: Det finns många sätt att använda variabler i strängar för att skapa formaterad text.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 786526fb98dbf1b3ec7c5c6c985ac95b85a96259
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301326"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a><span data-ttu-id="e75fd-103">Allt du ville veta om variabel ersättning i strängar</span><span class="sxs-lookup"><span data-stu-id="e75fd-103">Everything you wanted to know about variable substitution in strings</span></span>

<span data-ttu-id="e75fd-104">Det finns många sätt att använda variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="e75fd-104">There are many ways to use variables in strings.</span></span> <span data-ttu-id="e75fd-105">Jag anropar den här variabeln ersättningen men jag refererar till den tid som du vill formatera en sträng för att ta med värden från variabler.</span><span class="sxs-lookup"><span data-stu-id="e75fd-105">I'm calling this variable substitution but I'm referring to any time you want to format a string to include values from variables.</span></span> <span data-ttu-id="e75fd-106">Det här är något som jag ofta upptäcker för nya skript.</span><span class="sxs-lookup"><span data-stu-id="e75fd-106">This is something that I often find myself explaining to new scripters.</span></span>

> [!NOTE]
> <span data-ttu-id="e75fd-107">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="e75fd-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="e75fd-108">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="e75fd-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="e75fd-109">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="e75fd-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="concatenation"></a><span data-ttu-id="e75fd-110">Sammanlänkning</span><span class="sxs-lookup"><span data-stu-id="e75fd-110">Concatenation</span></span>

<span data-ttu-id="e75fd-111">Den första klass metoden kan kallas för sammanfogning.</span><span class="sxs-lookup"><span data-stu-id="e75fd-111">The first class of methods can be referred to as concatenation.</span></span> <span data-ttu-id="e75fd-112">Det är i princip att ta flera strängar och koppla ihop dem.</span><span class="sxs-lookup"><span data-stu-id="e75fd-112">It's basically taking several strings and joining them together.</span></span> <span data-ttu-id="e75fd-113">Det finns en lång historik för att använda sammanfogning för att bygga formaterade strängar.</span><span class="sxs-lookup"><span data-stu-id="e75fd-113">There's a long history of using concatenation to build formatted strings.</span></span>

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

<span data-ttu-id="e75fd-114">Sammanfogningen fungerar OK när det bara finns några värden att lägga till.</span><span class="sxs-lookup"><span data-stu-id="e75fd-114">Concatenation works out OK when there are only a few values to add.</span></span> <span data-ttu-id="e75fd-115">Men det kan enkelt bli krångligt.</span><span class="sxs-lookup"><span data-stu-id="e75fd-115">But this can get complicated quickly.</span></span>

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

<span data-ttu-id="e75fd-116">Det här enkla exemplet kan redan bli svårare att läsa.</span><span class="sxs-lookup"><span data-stu-id="e75fd-116">This simple example is already getting harder to read.</span></span>

## <a name="variable-substitution"></a><span data-ttu-id="e75fd-117">Variabel ersättning</span><span class="sxs-lookup"><span data-stu-id="e75fd-117">Variable substitution</span></span>

<span data-ttu-id="e75fd-118">PowerShell har ett annat alternativ som är enklare.</span><span class="sxs-lookup"><span data-stu-id="e75fd-118">PowerShell has another option that is easier.</span></span> <span data-ttu-id="e75fd-119">Du kan ange variablerna direkt i strängarna.</span><span class="sxs-lookup"><span data-stu-id="e75fd-119">You can specify your variables directly in the strings.</span></span>

```powershell
$message = "Hello, $first $last."
```

<span data-ttu-id="e75fd-120">Den typ av offerter som du använder runt strängen är en skillnad.</span><span class="sxs-lookup"><span data-stu-id="e75fd-120">The type of quotes you use around the string makes a difference.</span></span> <span data-ttu-id="e75fd-121">En dubbel citat tecken sträng tillåter ersättning men en sträng med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e75fd-121">A double quoted string allows the substitution but a single quoted string doesn't.</span></span> <span data-ttu-id="e75fd-122">Det finns flera gånger då du vill ha ett alternativ.</span><span class="sxs-lookup"><span data-stu-id="e75fd-122">There are times you want one or the other so you have an option.</span></span>

## <a name="command-substitution"></a><span data-ttu-id="e75fd-123">Kommando ersättning</span><span class="sxs-lookup"><span data-stu-id="e75fd-123">Command substitution</span></span>

<span data-ttu-id="e75fd-124">Det får ingen aning när du börjar försöka hämta värdena för egenskaperna i en sträng.</span><span class="sxs-lookup"><span data-stu-id="e75fd-124">Things get a little tricky when you start trying to get the values of properties into a string.</span></span> <span data-ttu-id="e75fd-125">Det är här som många nya personer får utlöst.</span><span class="sxs-lookup"><span data-stu-id="e75fd-125">This is where many new people get tripped up.</span></span> <span data-ttu-id="e75fd-126">Börja med att visa dig vad de tror bör fungera (och värdet för ansikts värde nästan ser ut ungefär som det borde).</span><span class="sxs-lookup"><span data-stu-id="e75fd-126">First let me show you what they think should work (and at face value almost looks like it should).</span></span>

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

<span data-ttu-id="e75fd-127">Du förväntar dig att få `CreationTime` bort `$directory` , men i stället får du detta `Time: c:\windows.CreationTime` som värde.</span><span class="sxs-lookup"><span data-stu-id="e75fd-127">You would be expecting to get the `CreationTime` off of the `$directory`, but instead you get this `Time: c:\windows.CreationTime` as your value.</span></span> <span data-ttu-id="e75fd-128">Orsaken är att den här typen av ersättning endast ser bas variabeln.</span><span class="sxs-lookup"><span data-stu-id="e75fd-128">The reason is that this type of substitution only sees the base variable.</span></span> <span data-ttu-id="e75fd-129">Den tar perioden som en del av strängen, så att den slutar att lösa värdet djupare.</span><span class="sxs-lookup"><span data-stu-id="e75fd-129">It considers the period as part of the string so it stops resolving the value any deeper.</span></span>

<span data-ttu-id="e75fd-130">Det innebär bara att det här objektet ger en sträng som standardvärde när den placeras i en sträng.</span><span class="sxs-lookup"><span data-stu-id="e75fd-130">It just so happens that this object gives a string as a default value when placed into a string.</span></span>
<span data-ttu-id="e75fd-131">Vissa objekt ger dig typ namnet i stället `System.Collections.Hashtable` .</span><span class="sxs-lookup"><span data-stu-id="e75fd-131">Some objects give you the type name instead like `System.Collections.Hashtable`.</span></span> <span data-ttu-id="e75fd-132">Bara något att titta efter.</span><span class="sxs-lookup"><span data-stu-id="e75fd-132">Just something to watch for.</span></span>

<span data-ttu-id="e75fd-133">Med PowerShell kan du utföra kommando körning inuti strängen med en speciell syntax.</span><span class="sxs-lookup"><span data-stu-id="e75fd-133">PowerShell allows you to do command execution inside the string with a special syntax.</span></span> <span data-ttu-id="e75fd-134">Detta gör att vi kan hämta egenskaperna för dessa objekt och köra andra kommandon för att få ett värde.</span><span class="sxs-lookup"><span data-stu-id="e75fd-134">This allows us to get the properties of these objects and run any other command to get a value.</span></span>

```powershell
$message = "Time: $($directory.CreationTime)"
```

<span data-ttu-id="e75fd-135">Detta fungerar bra för vissa situationer, men det kan komma precis som galna som sammanfogning om du bara har några få variabler.</span><span class="sxs-lookup"><span data-stu-id="e75fd-135">This works great for some situations but it can get just as crazy as concatenation if you have just a few variables.</span></span>

### <a name="command-execution"></a><span data-ttu-id="e75fd-136">Kommandokörning</span><span class="sxs-lookup"><span data-stu-id="e75fd-136">Command execution</span></span>

<span data-ttu-id="e75fd-137">Du kan köra kommandon inuti en sträng.</span><span class="sxs-lookup"><span data-stu-id="e75fd-137">You can run commands inside a string.</span></span> <span data-ttu-id="e75fd-138">Trots att jag har det här alternativet, jag vill inte.</span><span class="sxs-lookup"><span data-stu-id="e75fd-138">Even though I have this option, I don't like it.</span></span> <span data-ttu-id="e75fd-139">Den får en snabb och svår fel sökning.</span><span class="sxs-lookup"><span data-stu-id="e75fd-139">It gets cluttered quickly and hard to debug.</span></span> <span data-ttu-id="e75fd-140">Antingen kör du kommandot och sparar till en variabel eller använder en format sträng.</span><span class="sxs-lookup"><span data-stu-id="e75fd-140">I either run the command and save to a variable or use a format string.</span></span>

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a><span data-ttu-id="e75fd-141">Format sträng</span><span class="sxs-lookup"><span data-stu-id="e75fd-141">Format string</span></span>

<span data-ttu-id="e75fd-142">.NET har ett sätt att formatera strängar som jag tycker är ganska enkla att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="e75fd-142">.NET has a way to format strings that I find fairly easy to work with.</span></span> <span data-ttu-id="e75fd-143">Låt oss först visa dig den statiska metoden för den innan jag visar PowerShell-genvägen för att göra samma sak.</span><span class="sxs-lookup"><span data-stu-id="e75fd-143">First let me show you the static method for it before I show you the PowerShell shortcut to do the same thing.</span></span>

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

<span data-ttu-id="e75fd-144">Vad som händer här är att strängen tolkas för token `{0}` och `{1}` sedan används den siffran för att välja från de angivna värdena.</span><span class="sxs-lookup"><span data-stu-id="e75fd-144">What is happening here is that the string is parsed for the tokens `{0}` and `{1}`, then it uses that number to pick from the values provided.</span></span> <span data-ttu-id="e75fd-145">Om du vill upprepa ett visst värde på en viss plats i strängen kan du återanvända det värde numret.</span><span class="sxs-lookup"><span data-stu-id="e75fd-145">If you want to repeat one value some place in the string, you can reuse that values number.</span></span>

<span data-ttu-id="e75fd-146">Desto mer komplicerade strängen får, desto mer värde får du av den här metoden.</span><span class="sxs-lookup"><span data-stu-id="e75fd-146">The more complicated the string gets, the more value you get out of this approach.</span></span>

### <a name="format-values-as-arrays"></a><span data-ttu-id="e75fd-147">Formatera värden som matriser</span><span class="sxs-lookup"><span data-stu-id="e75fd-147">Format values as arrays</span></span>

<span data-ttu-id="e75fd-148">Om din format rad är för lång kan du placera värdena i en matris först.</span><span class="sxs-lookup"><span data-stu-id="e75fd-148">If your format line gets too long, you can place your values into an array first.</span></span>

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

<span data-ttu-id="e75fd-149">Detta är inte ihopbuntning eftersom jag skickar hela matrisen i, men idén är liknande.</span><span class="sxs-lookup"><span data-stu-id="e75fd-149">This is not splatting because I'm passing the whole array in, but the idea is similar.</span></span>

## <a name="advanced-formatting"></a><span data-ttu-id="e75fd-150">Avancerad formatering</span><span class="sxs-lookup"><span data-stu-id="e75fd-150">Advanced formatting</span></span>

<span data-ttu-id="e75fd-151">Jag har avsiktligt anropat dessa från .NET eftersom det finns många formateringsalternativ som redan är väl [dokumenterade][] på det.</span><span class="sxs-lookup"><span data-stu-id="e75fd-151">I intentionally called these out as coming from .NET because there are lots of formatting options already well [documented][] on it.</span></span> <span data-ttu-id="e75fd-152">Det finns inbyggda sätt att formatera olika data typer.</span><span class="sxs-lookup"><span data-stu-id="e75fd-152">There are built in ways to format various data types.</span></span>

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

<span data-ttu-id="e75fd-153">Jag kommer inte att gå till dem, men jag ville bara meddela att det här är en mycket kraftfull format motor om du behöver den.</span><span class="sxs-lookup"><span data-stu-id="e75fd-153">I'm not going to go into them but I just wanted to let you know that this is a very powerful formatting engine if you need it.</span></span>

## <a name="joining-strings"></a><span data-ttu-id="e75fd-154">Ansluta till strängar</span><span class="sxs-lookup"><span data-stu-id="e75fd-154">Joining strings</span></span>

<span data-ttu-id="e75fd-155">Ibland vill du verkligen sammanfoga en lista med värden.</span><span class="sxs-lookup"><span data-stu-id="e75fd-155">Sometimes you actually do want to concatenate a list of values together.</span></span> <span data-ttu-id="e75fd-156">Det finns en `-join` operatör som kan göra det åt dig.</span><span class="sxs-lookup"><span data-stu-id="e75fd-156">There's a `-join` operator that can do that for you.</span></span> <span data-ttu-id="e75fd-157">Det innebär även att du kan ange ett tangent att koppla mellan strängarna.</span><span class="sxs-lookup"><span data-stu-id="e75fd-157">It even lets you specify a character to join between the strings.</span></span>

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

<span data-ttu-id="e75fd-158">Om du vill använda en `-join` del strängar utan avgränsare måste du ange en tom sträng `''` .</span><span class="sxs-lookup"><span data-stu-id="e75fd-158">If you want to `-join` some strings without a separator, you need to specify an empty string `''`.</span></span>
<span data-ttu-id="e75fd-159">Men om det är allt du behöver finns det ett snabbare alternativ.</span><span class="sxs-lookup"><span data-stu-id="e75fd-159">But if that is all you need, there's a faster option.</span></span>

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

<span data-ttu-id="e75fd-160">Det är också värt att peka på att du även kan `-split` strängar.</span><span class="sxs-lookup"><span data-stu-id="e75fd-160">It's also worth pointing out that you can also `-split` strings too.</span></span>

## <a name="join-path"></a><span data-ttu-id="e75fd-161">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="e75fd-161">Join-Path</span></span>

<span data-ttu-id="e75fd-162">Detta är ofta överblickat men en bra cmdlet för att skapa en fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="e75fd-162">This is often overlooked but a great cmdlet for building a file path.</span></span>

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

<span data-ttu-id="e75fd-163">Det här är ett bra tips om att det fungerar som det ska när du placerar värdena tillsammans.</span><span class="sxs-lookup"><span data-stu-id="e75fd-163">The great thing about this is it works out the backslashes correctly when it puts the values together.</span></span> <span data-ttu-id="e75fd-164">Detta är särskilt viktigt om du tar värden från användare eller konfigurationsfiler.</span><span class="sxs-lookup"><span data-stu-id="e75fd-164">This is especially important if you are taking values from users or config files.</span></span>

<span data-ttu-id="e75fd-165">Detta går också bra med `Split-Path` och `Test-Path` .</span><span class="sxs-lookup"><span data-stu-id="e75fd-165">This also goes well with `Split-Path` and `Test-Path`.</span></span> <span data-ttu-id="e75fd-166">Jag lägger också till dessa i mitt inlägg om [att läsa och spara filer][].</span><span class="sxs-lookup"><span data-stu-id="e75fd-166">I also cover these in my post about [reading and saving to files][].</span></span>

## <a name="strings-are-arrays"></a><span data-ttu-id="e75fd-167">Strängar är matriser</span><span class="sxs-lookup"><span data-stu-id="e75fd-167">Strings are arrays</span></span>

<span data-ttu-id="e75fd-168">Jag behöver nämna att lägga till strängar här innan jag går vidare.</span><span class="sxs-lookup"><span data-stu-id="e75fd-168">I do need to mention adding strings here before I go on.</span></span> <span data-ttu-id="e75fd-169">Kom ihåg att en sträng bara är en matris med tecken.</span><span class="sxs-lookup"><span data-stu-id="e75fd-169">Remember that a string is just an array of characters.</span></span> <span data-ttu-id="e75fd-170">När du lägger till flera strängar tillsammans skapas en ny matris varje gång.</span><span class="sxs-lookup"><span data-stu-id="e75fd-170">When you add multiple strings together, a new array is created each time.</span></span>

<span data-ttu-id="e75fd-171">Titta på det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="e75fd-171">Look at this example:</span></span>

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

<span data-ttu-id="e75fd-172">Det verkar mycket grundläggande men det som du inte ser är att varje gången en sträng läggs till i `$message` en ny sträng skapas.</span><span class="sxs-lookup"><span data-stu-id="e75fd-172">It looks very basic but what you don't see is that each time a string is added to `$message` that a whole new string is created.</span></span> <span data-ttu-id="e75fd-173">Minnet allokeras, data kopieras och det gamla det ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e75fd-173">Memory gets allocated, data gets copied and the old one is discarded.</span></span>
<span data-ttu-id="e75fd-174">Inte ett stort avtal när det bara är ett par gånger, men en slinga som detta skulle innebära problemet.</span><span class="sxs-lookup"><span data-stu-id="e75fd-174">Not a big deal when it's only done a few times, but a loop like this would really expose the issue.</span></span>

### <a name="stringbuilder"></a><span data-ttu-id="e75fd-175">StringBuilder</span><span class="sxs-lookup"><span data-stu-id="e75fd-175">StringBuilder</span></span>

<span data-ttu-id="e75fd-176">StringBuilder är också mycket populär för att skapa stora strängar från massor av mindre strängar.</span><span class="sxs-lookup"><span data-stu-id="e75fd-176">StringBuilder is also very popular for building large strings from lots of smaller strings.</span></span> <span data-ttu-id="e75fd-177">Orsaken till detta är att den bara samlar in alla strängar som du lägger till i den och bara sammanfogar alla dem i slutet när du hämtar värdet.</span><span class="sxs-lookup"><span data-stu-id="e75fd-177">The reason why is because it just collects all the strings you add to it and only concatenates all of them at the end when you retrieve the value.</span></span>

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

<span data-ttu-id="e75fd-178">Återigen är det något som jag når till .NET för.</span><span class="sxs-lookup"><span data-stu-id="e75fd-178">Again, this is something that I'm reaching out to .NET for.</span></span> <span data-ttu-id="e75fd-179">Jag använder det inte ofta längre, men det är bra att känna till det.</span><span class="sxs-lookup"><span data-stu-id="e75fd-179">I don't use it often anymore but it's good to know it's there.</span></span>

## <a name="delineation-with-braces"></a><span data-ttu-id="e75fd-180">Delinjärt med klammerparenteser</span><span class="sxs-lookup"><span data-stu-id="e75fd-180">Delineation with braces</span></span>

<span data-ttu-id="e75fd-181">Detta används för kombination av suffix i strängen.</span><span class="sxs-lookup"><span data-stu-id="e75fd-181">This is used for suffix concatenation within the string.</span></span> <span data-ttu-id="e75fd-182">Ibland har din variabel inte en ren ord-gränser.</span><span class="sxs-lookup"><span data-stu-id="e75fd-182">Sometimes your variable doesn't have a clean word boundary.</span></span>

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

<span data-ttu-id="e75fd-183">Tack [/u/-real_parbold][] för det.</span><span class="sxs-lookup"><span data-stu-id="e75fd-183">Thank you [/u/real_parbold][] for that one.</span></span>

<span data-ttu-id="e75fd-184">Här är ett alternativ till den här metoden:</span><span class="sxs-lookup"><span data-stu-id="e75fd-184">Here is an alternate to this approach:</span></span>

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

<span data-ttu-id="e75fd-185">Jag använder en format sträng för det här, men det är en bättre idé att se om den finns i jokertecken.</span><span class="sxs-lookup"><span data-stu-id="e75fd-185">I personally use format string for this, but this is good to know incase you see it in the wild.</span></span>

## <a name="find-and-replace-tokens"></a><span data-ttu-id="e75fd-186">Sök och ersätt tokens</span><span class="sxs-lookup"><span data-stu-id="e75fd-186">Find and replace tokens</span></span>

<span data-ttu-id="e75fd-187">De flesta av de här funktionerna begränsar ditt behov av att återställa din egen lösning, men det finns tillfällen där du kan ha stora mallfiler där du vill ersätta strängar inuti.</span><span class="sxs-lookup"><span data-stu-id="e75fd-187">While most of these features limit your need to roll your own solution, there are times where you may have large template files where you want to replace strings inside.</span></span>

<span data-ttu-id="e75fd-188">Låt oss anta att du har hämtat en mall från en fil som har mycket text.</span><span class="sxs-lookup"><span data-stu-id="e75fd-188">Let us assume you pulled in a template from a file that has a lot of text.</span></span>

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

<span data-ttu-id="e75fd-189">Du kan ha många token som ska ersättas.</span><span class="sxs-lookup"><span data-stu-id="e75fd-189">You may have lots of tokens to replace.</span></span> <span data-ttu-id="e75fd-190">Ditt Stick är att använda en mycket skild token som är lätt att hitta och ersätta.</span><span class="sxs-lookup"><span data-stu-id="e75fd-190">The trick is to use a very distinct token that is easy to find and replace.</span></span> <span data-ttu-id="e75fd-191">Jag brukar använda ett specialtecken i båda ändar för att hjälpa till att skilja det.</span><span class="sxs-lookup"><span data-stu-id="e75fd-191">I tend to use a special character at both ends to help distinguish it.</span></span>

<span data-ttu-id="e75fd-192">Jag har nyligen hittat ett nytt sätt att närma sig detta.</span><span class="sxs-lookup"><span data-stu-id="e75fd-192">I recently found a new way to approach this.</span></span> <span data-ttu-id="e75fd-193">Jag beslutade att lämna det här avsnittet här eftersom det är ett mönster som används ofta.</span><span class="sxs-lookup"><span data-stu-id="e75fd-193">I decided to leave this section in here because this is a pattern that is commonly used.</span></span>

### <a name="replace-multiple-tokens"></a><span data-ttu-id="e75fd-194">Ersätt flera tokens</span><span class="sxs-lookup"><span data-stu-id="e75fd-194">Replace multiple tokens</span></span>

<span data-ttu-id="e75fd-195">När jag har en lista över tokens som jag behöver ersätta, tar jag en mer allmän metod.</span><span class="sxs-lookup"><span data-stu-id="e75fd-195">When I have a list of tokens that I need to replace, I take a more generic approach.</span></span> <span data-ttu-id="e75fd-196">Jag skulle placera dem i en hash-hash och iterera över dem för att ersätta dem.</span><span class="sxs-lookup"><span data-stu-id="e75fd-196">I would place them in a hashtable and iterate over them to do the replace.</span></span>

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

<span data-ttu-id="e75fd-197">Dessa token kan läsas in från JSON eller CSV om det behövs.</span><span class="sxs-lookup"><span data-stu-id="e75fd-197">Those tokens could be loaded from JSON or CSV if needed.</span></span>

### <a name="executioncontext-expandstring"></a><span data-ttu-id="e75fd-198">ExecutionContext ExpandString</span><span class="sxs-lookup"><span data-stu-id="e75fd-198">ExecutionContext ExpandString</span></span>

<span data-ttu-id="e75fd-199">Det finns ett smarta sätt att definiera en ersättnings sträng med enkla citat tecken och expandera variablerna senare.</span><span class="sxs-lookup"><span data-stu-id="e75fd-199">There's a clever way to define a substitution string with single quotes and expand the variables later.</span></span> <span data-ttu-id="e75fd-200">Titta på det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="e75fd-200">Look at this example:</span></span>

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

<span data-ttu-id="e75fd-201">Anropet till `.InvokeCommand.ExpandString` i den aktuella körnings kontexten använder variablerna i det aktuella omfånget för ersättning.</span><span class="sxs-lookup"><span data-stu-id="e75fd-201">The call to `.InvokeCommand.ExpandString` on the current execution context uses the variables in the current scope for substitution.</span></span> <span data-ttu-id="e75fd-202">Nyckeln här är att `$message` kan definieras tidigt innan variablerna blir kvar.</span><span class="sxs-lookup"><span data-stu-id="e75fd-202">The key thing here is that the `$message` can be defined very early before the variables even exist.</span></span>

<span data-ttu-id="e75fd-203">Om vi expanderar på bara en liten bit kan vi utföra denna ersättning över och över wih olika värden.</span><span class="sxs-lookup"><span data-stu-id="e75fd-203">If we expand on that just a little bit, we can perform this substitution over and over wih different values.</span></span>

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

<span data-ttu-id="e75fd-204">För att fortsätta med den här idén. Du kan importera en stor e-postmall från en textfil för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="e75fd-204">To keep going on this idea; you could be importing a large email template from a text file to do this.</span></span> <span data-ttu-id="e75fd-205">Jag måste tacka [mark Kraus][] för det här [förslaget][].</span><span class="sxs-lookup"><span data-stu-id="e75fd-205">I have to thank [Mark Kraus][] for this [suggestion][].</span></span>

## <a name="whatever-works-the-best-for-you"></a><span data-ttu-id="e75fd-206">Vad som fungerar bäst för dig</span><span class="sxs-lookup"><span data-stu-id="e75fd-206">Whatever works the best for you</span></span>

<span data-ttu-id="e75fd-207">Jag är en fläkt i format Strängs metoden.</span><span class="sxs-lookup"><span data-stu-id="e75fd-207">I'm a fan of the format string approach.</span></span> <span data-ttu-id="e75fd-208">Det gör du definitivt med de mer komplicerade strängarna eller om det finns flera variabler.</span><span class="sxs-lookup"><span data-stu-id="e75fd-208">I definitely do this with the more complicated strings or if there are multiple variables.</span></span> <span data-ttu-id="e75fd-209">På något som är mycket kort kan jag använda något av dessa.</span><span class="sxs-lookup"><span data-stu-id="e75fd-209">On anything that is very short, I may use any one of these.</span></span>

## <a name="anything-else"></a><span data-ttu-id="e75fd-210">Något mer?</span><span class="sxs-lookup"><span data-stu-id="e75fd-210">Anything else?</span></span>

<span data-ttu-id="e75fd-211">Jag har täckt mycket av grunden på det här.</span><span class="sxs-lookup"><span data-stu-id="e75fd-211">I covered a lot of ground on this one.</span></span> <span data-ttu-id="e75fd-212">Mitt hoppas att du kan gå vidare med att lära dig något nytt.</span><span class="sxs-lookup"><span data-stu-id="e75fd-212">My hope is that you walk away learning something new.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[original version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Markera Kraus]: https://get-powershellblog.blogspot.com/
[Mark Kraus]: https://get-powershellblog.blogspot.com/
[lämna]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[suggestion]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[läsa och spara till filer]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[reading and saving to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[dokumenteras]: /dotnet/api/system.string.format#overloads
[documented]: /dotnet/api/system.string.format#overloads
