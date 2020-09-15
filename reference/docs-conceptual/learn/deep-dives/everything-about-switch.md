---
title: Allt du ville veta om switch-instruktionen
description: Switch-instruktionen i PowerShell erbjuder funktioner som inte finns på andra språk.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 685a5691599408a0d54ca99bf383bcd7702322a6
ms.sourcegitcommit: 0afff6edbe560e88372dd5f1cdf51d77f9349972
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86469726"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a><span data-ttu-id="d526b-103">Allt du ville veta om switch-instruktionen</span><span class="sxs-lookup"><span data-stu-id="d526b-103">Everything you ever wanted to know about the switch statement</span></span>

<span data-ttu-id="d526b-104">Precis som många andra språk har PowerShell kommandon för att kontrol lera körnings flödet i dina skript.</span><span class="sxs-lookup"><span data-stu-id="d526b-104">Like many other languages, PowerShell has commands for controlling the flow of execution within your scripts.</span></span> <span data-ttu-id="d526b-105">En av dessa uttryck är [switch][] -instruktionen och i PowerShell finns funktioner som inte finns på andra språk.</span><span class="sxs-lookup"><span data-stu-id="d526b-105">One of those statements is the [switch][] statement and in PowerShell, it offers features that aren't found in other languages.</span></span> <span data-ttu-id="d526b-106">Idag tar vi en djupare erfarenhet av att arbeta med PowerShell `switch` .</span><span class="sxs-lookup"><span data-stu-id="d526b-106">Today, we take a deep dive into working with the PowerShell `switch`.</span></span>

> [!NOTE]
> <span data-ttu-id="d526b-107">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="d526b-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="d526b-108">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="d526b-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="d526b-109">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="d526b-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="the-if-statement"></a><span data-ttu-id="d526b-110">`if`Instruktionen</span><span class="sxs-lookup"><span data-stu-id="d526b-110">The `if` statement</span></span>

<span data-ttu-id="d526b-111">En av de första satserna som du lär dig är- `if` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="d526b-111">One of the first statements that you learn is the `if` statement.</span></span> <span data-ttu-id="d526b-112">Du kan köra ett skript block om en instruktion är `$true` .</span><span class="sxs-lookup"><span data-stu-id="d526b-112">It lets you execute a script block if a statement is `$true`.</span></span>

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

<span data-ttu-id="d526b-113">Du kan ha mycket mer komplicerad logik genom att använda `elseif` och- `else` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="d526b-113">You can have much more complicated logic by using `elseif` and `else` statements.</span></span> <span data-ttu-id="d526b-114">Här är ett exempel där jag har ett numeriskt värde för veckodag och jag vill hämta namnet som en sträng.</span><span class="sxs-lookup"><span data-stu-id="d526b-114">Here is an example where I have a numeric value for day of the week and I want to get the name as a string.</span></span>

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

<span data-ttu-id="d526b-115">Det gör att det här är ett vanligt mönster och det finns många sätt att hantera detta på.</span><span class="sxs-lookup"><span data-stu-id="d526b-115">It turns out that this is a common pattern and there are many ways to deal with this.</span></span> <span data-ttu-id="d526b-116">En av dem är med en `switch` .</span><span class="sxs-lookup"><span data-stu-id="d526b-116">One of them is with a `switch`.</span></span>

## <a name="switch-statement"></a><span data-ttu-id="d526b-117">Switch-instruktion</span><span class="sxs-lookup"><span data-stu-id="d526b-117">Switch statement</span></span>

<span data-ttu-id="d526b-118">Med `switch` instruktionen kan du ange en variabel och en lista över möjliga värden.</span><span class="sxs-lookup"><span data-stu-id="d526b-118">The `switch` statement allows you to provide a variable and a list of possible values.</span></span> <span data-ttu-id="d526b-119">Om värdet matchar variabeln körs dess script block.</span><span class="sxs-lookup"><span data-stu-id="d526b-119">If the value matches the variable, then its scriptblock is executed.</span></span>

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

<span data-ttu-id="d526b-120">I det här exemplet är värdet för att `$day` matcha ett av de numeriska värdena, och sedan tilldelas rätt namn `$result` .</span><span class="sxs-lookup"><span data-stu-id="d526b-120">For this example, the value of `$day` matches one of the numeric values, then the correct name is assigned to `$result`.</span></span> <span data-ttu-id="d526b-121">Vi utför bara en variabel tilldelning i det här exemplet, men alla PowerShell kan köras i dessa skript block.</span><span class="sxs-lookup"><span data-stu-id="d526b-121">We are only doing a variable assignment in this example, but any PowerShell can be executed in those script blocks.</span></span>

### <a name="assign-to-a-variable"></a><span data-ttu-id="d526b-122">Tilldela till en variabel</span><span class="sxs-lookup"><span data-stu-id="d526b-122">Assign to a variable</span></span>

<span data-ttu-id="d526b-123">Vi kan skriva det senaste exemplet på ett annat sätt.</span><span class="sxs-lookup"><span data-stu-id="d526b-123">We can write that last example in another way.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

<span data-ttu-id="d526b-124">Vi placerar värdet på PowerShell-pipeline och tilldelar det till `$result` .</span><span class="sxs-lookup"><span data-stu-id="d526b-124">We are placing the value on the PowerShell pipeline and assigning it to the `$result`.</span></span> <span data-ttu-id="d526b-125">Du kan göra samma sak med- `if` och- `foreach` satserna.</span><span class="sxs-lookup"><span data-stu-id="d526b-125">You can do this same thing with the `if` and `foreach` statements.</span></span>

### <a name="default"></a><span data-ttu-id="d526b-126">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="d526b-126">Default</span></span>

<span data-ttu-id="d526b-127">Vi kan använda `default` nyckelordet för att identifiera vad som ska hända om det inte finns någon matchning.</span><span class="sxs-lookup"><span data-stu-id="d526b-127">We can use the `default` keyword to identify the what should happen if there is no match.</span></span>

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

<span data-ttu-id="d526b-128">Här returnerar vi värdet `Unknown` i standard fallet.</span><span class="sxs-lookup"><span data-stu-id="d526b-128">Here we return the value `Unknown` in the default case.</span></span>

### <a name="strings"></a><span data-ttu-id="d526b-129">Strängar</span><span class="sxs-lookup"><span data-stu-id="d526b-129">Strings</span></span>

<span data-ttu-id="d526b-130">Jag matchade talen i de senaste exemplen, men du kan också matcha strängar.</span><span class="sxs-lookup"><span data-stu-id="d526b-130">I was matching numbers in those last examples, but you can also match strings.</span></span>

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="d526b-131">Jag beslutade att inte omsluta `Component` , `Role` och `Location` matchar citat tecken här för att markera att de är valfria.</span><span class="sxs-lookup"><span data-stu-id="d526b-131">I decided not to wrap the `Component`,`Role` and `Location` matches in quotes here to highlight that they're optional.</span></span> <span data-ttu-id="d526b-132">`switch`I de flesta fall behandlas de som en sträng.</span><span class="sxs-lookup"><span data-stu-id="d526b-132">The `switch` treats those as a string in most cases.</span></span>

## <a name="arrays"></a><span data-ttu-id="d526b-133">Matriser</span><span class="sxs-lookup"><span data-stu-id="d526b-133">Arrays</span></span>

<span data-ttu-id="d526b-134">En av de häftiga funktionerna i PowerShell `switch` är hur den hanterar matriser.</span><span class="sxs-lookup"><span data-stu-id="d526b-134">One of the cool features of the PowerShell `switch` is the way it handles arrays.</span></span> <span data-ttu-id="d526b-135">Om du anger en `switch` matris bearbetar den varje element i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d526b-135">If you give a `switch` an array, it processes each element in that collection.</span></span>

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

<span data-ttu-id="d526b-136">Om du har upprepade objekt i matrisen matchas de flera gånger av lämpligt avsnitt.</span><span class="sxs-lookup"><span data-stu-id="d526b-136">If you have repeated items in your array, then they're matched multiple times by the appropriate section.</span></span>

### <a name="psitem"></a><span data-ttu-id="d526b-137">PSItem</span><span class="sxs-lookup"><span data-stu-id="d526b-137">PSItem</span></span>

<span data-ttu-id="d526b-138">Du kan använda `$PSItem` eller `$_` för att referera till det aktuella objektet som bearbetades.</span><span class="sxs-lookup"><span data-stu-id="d526b-138">You can use the `$PSItem` or `$_` to reference the current item that was processed.</span></span> <span data-ttu-id="d526b-139">När vi gör en enkel matchning `$PSItem` är det värde som vi matchar.</span><span class="sxs-lookup"><span data-stu-id="d526b-139">When we do a simple match, `$PSItem` is the value that we are matching.</span></span> <span data-ttu-id="d526b-140">Jag utför några avancerade matchningar i nästa avsnitt där denna variabel används.</span><span class="sxs-lookup"><span data-stu-id="d526b-140">I'll be performing some advanced matches in the next section where this variable is used.</span></span>

## <a name="parameters"></a><span data-ttu-id="d526b-141">Parametrar</span><span class="sxs-lookup"><span data-stu-id="d526b-141">Parameters</span></span>

<span data-ttu-id="d526b-142">En unik funktion i PowerShell `switch` är att den har ett antal [växel parametrar][] som ändrar hur det fungerar.</span><span class="sxs-lookup"><span data-stu-id="d526b-142">A unique feature of the PowerShell `switch` is that it has a number of [switch parameters][] that change how it performs.</span></span>

### <a name="-casesensitive"></a><span data-ttu-id="d526b-143">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="d526b-143">-CaseSensitive</span></span>

<span data-ttu-id="d526b-144">Matchningarna är inte Skift läges känsliga som standard.</span><span class="sxs-lookup"><span data-stu-id="d526b-144">The matches aren't case-sensitive by default.</span></span> <span data-ttu-id="d526b-145">Om du behöver vara Skift läges känslig kan du använda `-CaseSensitive` .</span><span class="sxs-lookup"><span data-stu-id="d526b-145">If you need to be case-sensitive, you can use `-CaseSensitive`.</span></span> <span data-ttu-id="d526b-146">Detta kan användas tillsammans med andra växel parametrar.</span><span class="sxs-lookup"><span data-stu-id="d526b-146">This can be used in combination with the other switch parameters.</span></span>

### <a name="-wildcard"></a><span data-ttu-id="d526b-147">– Jokertecken</span><span class="sxs-lookup"><span data-stu-id="d526b-147">-Wildcard</span></span>

<span data-ttu-id="d526b-148">Vi kan aktivera stöd för jokertecken med `-wildcard` växeln.</span><span class="sxs-lookup"><span data-stu-id="d526b-148">We can enable wildcard support with the `-wildcard` switch.</span></span> <span data-ttu-id="d526b-149">Detta använder samma logik för jokertecken som `-like` operatorn för att göra varje matchning.</span><span class="sxs-lookup"><span data-stu-id="d526b-149">This uses the same wildcard logic as the `-like` operator to do each match.</span></span>

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

<span data-ttu-id="d526b-150">Här bearbetar vi ett meddelande och placerar det på olika strömmar baserat på innehållet.</span><span class="sxs-lookup"><span data-stu-id="d526b-150">Here we are processing a message and then outputting it on different streams based on the contents.</span></span>

### <a name="-regex"></a><span data-ttu-id="d526b-151">– Regex</span><span class="sxs-lookup"><span data-stu-id="d526b-151">-Regex</span></span>

<span data-ttu-id="d526b-152">Switch-instruktionen stöder regex matchar precis som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d526b-152">The switch statement supports regex matches just like it does wildcards.</span></span>

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

<span data-ttu-id="d526b-153">Jag har fler exempel på att använda regex i en annan artikel som jag skrev: [på många sätt att använda regex][].</span><span class="sxs-lookup"><span data-stu-id="d526b-153">I have more examples of using regex in another article I wrote: [The many ways to use regex][].</span></span>

### <a name="-file"></a><span data-ttu-id="d526b-154">– Fil</span><span class="sxs-lookup"><span data-stu-id="d526b-154">-File</span></span>

<span data-ttu-id="d526b-155">En liten känd funktion i Switch-instruktionen är att den kan bearbeta en fil med `-File` parametern.</span><span class="sxs-lookup"><span data-stu-id="d526b-155">A little known feature of the switch statement is that it can process a file with the `-File` parameter.</span></span> <span data-ttu-id="d526b-156">Du använder `-file` med en sökväg till en fil i stället för att ge den ett variabel uttryck.</span><span class="sxs-lookup"><span data-stu-id="d526b-156">You use `-file` with a path to a file instead of giving it a variable expression.</span></span>

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="d526b-157">Det fungerar precis som att bearbeta en matris.</span><span class="sxs-lookup"><span data-stu-id="d526b-157">It works just like processing an array.</span></span> <span data-ttu-id="d526b-158">I det här exemplet kombinerar jag det med matchning av jokertecken och använder `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="d526b-158">In this example, I combine it with wildcard matching and make use of the `$PSItem`.</span></span> <span data-ttu-id="d526b-159">Detta bearbetar en loggfil och konverterar den till varnings-och fel meddelanden beroende på regex-matchningarna.</span><span class="sxs-lookup"><span data-stu-id="d526b-159">This would process a log file and convert it to warning and error messages depending on the regex matches.</span></span>

## <a name="advanced-details"></a><span data-ttu-id="d526b-160">Avancerad information</span><span class="sxs-lookup"><span data-stu-id="d526b-160">Advanced details</span></span>

<span data-ttu-id="d526b-161">Nu när du är medveten om alla dessa dokumenterade funktioner kan vi använda dem i samband med mer avancerad bearbetning.</span><span class="sxs-lookup"><span data-stu-id="d526b-161">Now that you're aware of all these documented features, we can use them in the context of more advanced processing.</span></span>

### <a name="expressions"></a><span data-ttu-id="d526b-162">Uttryck</span><span class="sxs-lookup"><span data-stu-id="d526b-162">Expressions</span></span>

<span data-ttu-id="d526b-163">`switch`Kan finnas i ett uttryck i stället för en variabel.</span><span class="sxs-lookup"><span data-stu-id="d526b-163">The `switch` can be on an expression instead of a variable.</span></span>

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

<span data-ttu-id="d526b-164">Oavsett vilket uttryck som utvärderas till är det värde som används för matchningen.</span><span class="sxs-lookup"><span data-stu-id="d526b-164">Whatever the expression evaluates to is the value used for the match.</span></span>

### <a name="multiple-matches"></a><span data-ttu-id="d526b-165">Flera matchningar</span><span class="sxs-lookup"><span data-stu-id="d526b-165">Multiple matches</span></span>

<span data-ttu-id="d526b-166">Du kanske redan har valt detta, men en `switch` kan matcha flera villkor.</span><span class="sxs-lookup"><span data-stu-id="d526b-166">You may have already picked up on this, but a `switch` can match to multiple conditions.</span></span> <span data-ttu-id="d526b-167">Detta gäller särskilt när du använder `-wildcard` eller `-regex` matchar.</span><span class="sxs-lookup"><span data-stu-id="d526b-167">This is especially true when using `-wildcard` or `-regex` matches.</span></span> <span data-ttu-id="d526b-168">Du kan lägga till samma villkor flera gånger och alla utlöses.</span><span class="sxs-lookup"><span data-stu-id="d526b-168">You can add the same condition multiple times and all of them are triggered.</span></span>

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

<span data-ttu-id="d526b-169">Alla tre dessa uttryck utlöses.</span><span class="sxs-lookup"><span data-stu-id="d526b-169">All three of these statements are fired.</span></span> <span data-ttu-id="d526b-170">Detta visar att varje villkor är markerat (i ordning).</span><span class="sxs-lookup"><span data-stu-id="d526b-170">This shows that every condition is checked (in order).</span></span> <span data-ttu-id="d526b-171">Detta gäller för bearbetning av matriser där varje objekt kontrollerar varje villkor.</span><span class="sxs-lookup"><span data-stu-id="d526b-171">This holds true for processing arrays where each item checks each condition.</span></span>

### <a name="continue"></a><span data-ttu-id="d526b-172">Fortsätt</span><span class="sxs-lookup"><span data-stu-id="d526b-172">Continue</span></span>

<span data-ttu-id="d526b-173">Normalt är det här där jag skulle introducera `break` instruktionen, men det är bättre att vi lär oss att använda den `continue` först.</span><span class="sxs-lookup"><span data-stu-id="d526b-173">Normally, this is where I would introduce the `break` statement, but it's better that we learn how to use `continue` first.</span></span> <span data-ttu-id="d526b-174">Precis som med en `foreach` loop `continue` fortsätter du till nästa objekt i samlingen eller avslutar `switch` om det inte finns några fler objekt.</span><span class="sxs-lookup"><span data-stu-id="d526b-174">Just like with a `foreach` loop, `continue` continues onto the next item in the collection or exits the `switch` if there are no more items.</span></span> <span data-ttu-id="d526b-175">Vi kan skriva om det senaste exemplet med Continue-instruktioner så att endast en sats körs.</span><span class="sxs-lookup"><span data-stu-id="d526b-175">We can rewrite that last example with continue statements so that only one statement executes.</span></span>

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

<span data-ttu-id="d526b-176">I stället för att matcha alla tre objekten matchas det första, och växeln fortsätter till nästa värde.</span><span class="sxs-lookup"><span data-stu-id="d526b-176">Instead of matching all three items, the first one is matched and the switch continues to the next value.</span></span> <span data-ttu-id="d526b-177">Eftersom det inte finns några värden kvar för att bearbeta, avslutas växeln.</span><span class="sxs-lookup"><span data-stu-id="d526b-177">Because there are no values left to process, the switch exits.</span></span> <span data-ttu-id="d526b-178">I nästa exempel visas hur ett jokertecken kan matcha flera objekt.</span><span class="sxs-lookup"><span data-stu-id="d526b-178">This next example is showing how a wildcard could match multiple items.</span></span>

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

<span data-ttu-id="d526b-179">Eftersom en rad i indatafilen kan innehålla både ordet `Error` och `Warning` , vill vi bara att den första är att köra och sedan fortsätta att bearbeta filen.</span><span class="sxs-lookup"><span data-stu-id="d526b-179">Because a line in the input file could contain both the word `Error` and `Warning`, we only want the first one to execute and then continue processing the file.</span></span>

### <a name="break"></a><span data-ttu-id="d526b-180">Bryt ned</span><span class="sxs-lookup"><span data-stu-id="d526b-180">Break</span></span>

<span data-ttu-id="d526b-181">En `break` instruktion avslutar växeln.</span><span class="sxs-lookup"><span data-stu-id="d526b-181">A `break` statement exits the switch.</span></span> <span data-ttu-id="d526b-182">Detta är samma beteende som `continue` visar för enskilda värden.</span><span class="sxs-lookup"><span data-stu-id="d526b-182">This is the same behavior that `continue` presents for single values.</span></span> <span data-ttu-id="d526b-183">Skillnaden visas när du bearbetar en matris.</span><span class="sxs-lookup"><span data-stu-id="d526b-183">The difference is shown when processing an array.</span></span> <span data-ttu-id="d526b-184">`break` stoppar all bearbetning i växeln och `continue` flyttas till nästa objekt.</span><span class="sxs-lookup"><span data-stu-id="d526b-184">`break` stops all processing in the switch and `continue` moves onto the next item.</span></span>

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

<span data-ttu-id="d526b-185">I det här fallet visas ett fel meddelande om vi träffar de rader som börjar med `Error` och växeln stoppas.</span><span class="sxs-lookup"><span data-stu-id="d526b-185">In this case, if we hit any lines that start with `Error` then we get an error and the switch stops.</span></span>
<span data-ttu-id="d526b-186">Detta är vad den här `break` instruktionen gör för oss.</span><span class="sxs-lookup"><span data-stu-id="d526b-186">This is what that `break` statement is doing for us.</span></span> <span data-ttu-id="d526b-187">Om vi hittar `Error` i strängen och inte bara i början skriver vi den som en varning.</span><span class="sxs-lookup"><span data-stu-id="d526b-187">If we find `Error` inside the string and not just at the beginning, we write it as a warning.</span></span> <span data-ttu-id="d526b-188">Vi gör samma sak för `Warning` .</span><span class="sxs-lookup"><span data-stu-id="d526b-188">We do the same thing for `Warning`.</span></span> <span data-ttu-id="d526b-189">Det är möjligt att en rad kan ha både ordet `Error` och `Warning` , men vi behöver bara en att bearbeta.</span><span class="sxs-lookup"><span data-stu-id="d526b-189">It's possible that a line could have both the word `Error` and `Warning`, but we only need one to process.</span></span> <span data-ttu-id="d526b-190">Detta är vad `continue` instruktionen gör för oss.</span><span class="sxs-lookup"><span data-stu-id="d526b-190">This is what the `continue` statement is doing for us.</span></span>

### <a name="break-labels"></a><span data-ttu-id="d526b-191">Bryt etiketter</span><span class="sxs-lookup"><span data-stu-id="d526b-191">Break labels</span></span>

<span data-ttu-id="d526b-192">`switch`Instruktionen stöder `break/continue` Etiketter precis som `foreach` .</span><span class="sxs-lookup"><span data-stu-id="d526b-192">The `switch` statement supports `break/continue` labels just like `foreach`.</span></span>

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

<span data-ttu-id="d526b-193">Jag vill inte använda brytnings etiketter, men jag ville peka ut dem eftersom de är förvirrande om du aldrig har sett dem förut.</span><span class="sxs-lookup"><span data-stu-id="d526b-193">I personally don't like the use of break labels but I wanted to point them out because they're confusing if you've never seen them before.</span></span> <span data-ttu-id="d526b-194">Om du har flera `switch` eller `foreach` -satser som är kapslade kanske du vill dela upp fler än det inre objektet.</span><span class="sxs-lookup"><span data-stu-id="d526b-194">When you have multiple `switch` or `foreach` statements that are nested, you may want to break out of more than the inner most item.</span></span> <span data-ttu-id="d526b-195">Du kan placera en etikett på en `switch` som kan vara målet för din `break` .</span><span class="sxs-lookup"><span data-stu-id="d526b-195">You can place a label on a `switch` that can be the target of your `break`.</span></span>

### <a name="enum"></a><span data-ttu-id="d526b-196">Enum</span><span class="sxs-lookup"><span data-stu-id="d526b-196">Enum</span></span>

<span data-ttu-id="d526b-197">PowerShell 5,0 gav oss Fasttext och vi kan använda dem i en växel.</span><span class="sxs-lookup"><span data-stu-id="d526b-197">PowerShell 5.0 gave us enums and we can use them in a switch.</span></span>

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

<span data-ttu-id="d526b-198">Om du vill behålla allting som starkt skrivna uppräkningar kan du placera dem inom parentes.</span><span class="sxs-lookup"><span data-stu-id="d526b-198">If you want to keep everything as strongly typed enums, then you can place them in parentheses.</span></span>

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

<span data-ttu-id="d526b-199">Parenteserna behövs här så att växeln inte behandlar värdet `[Context]::Location` som en literal sträng.</span><span class="sxs-lookup"><span data-stu-id="d526b-199">The parentheses are needed here so that the switch doesn't treat the value `[Context]::Location` as a literal string.</span></span>

### <a name="scriptblock"></a><span data-ttu-id="d526b-200">Script block</span><span class="sxs-lookup"><span data-stu-id="d526b-200">ScriptBlock</span></span>

<span data-ttu-id="d526b-201">Vi kan använda en script block för att utföra utvärderingen för en matchning om det behövs.</span><span class="sxs-lookup"><span data-stu-id="d526b-201">We can use a scriptblock to perform the evaluation for a match if needed.</span></span>

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

<span data-ttu-id="d526b-202">Detta ökar komplexiteten och kan göra det `switch` svårt att läsa.</span><span class="sxs-lookup"><span data-stu-id="d526b-202">This adds complexity and can make your `switch` hard to read.</span></span> <span data-ttu-id="d526b-203">I de flesta fall där du använder något som liknar det, skulle det vara bättre att använda `if` och `elseif` uttryck.</span><span class="sxs-lookup"><span data-stu-id="d526b-203">In most cases where you would use something like this it would be better to use `if` and `elseif` statements.</span></span> <span data-ttu-id="d526b-204">Jag skulle vilja använda detta om jag redan har en stor växel på plats och jag behövde två objekt för att få samma utvärderings block.</span><span class="sxs-lookup"><span data-stu-id="d526b-204">I would consider using this if I already had a large switch in place and I needed two items to hit the same evaluation block.</span></span>

<span data-ttu-id="d526b-205">Ett bra sätt är att placera script block i parenteser.</span><span class="sxs-lookup"><span data-stu-id="d526b-205">One thing that I think helps with legibility is to place the scriptblock in parentheses.</span></span>

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

<span data-ttu-id="d526b-206">Den körs fortfarande på samma sätt och ger ett bättre visuellt avbrott när du snabbt tittar på det.</span><span class="sxs-lookup"><span data-stu-id="d526b-206">It still executes the same way and gives a better visual break when quickly looking at it.</span></span>

### <a name="regex-matches"></a><span data-ttu-id="d526b-207">Regex $matches</span><span class="sxs-lookup"><span data-stu-id="d526b-207">Regex $matches</span></span>

<span data-ttu-id="d526b-208">Vi behöver gå tillbaka till regex för att vidröra något som inte är uppenbart tydligt.</span><span class="sxs-lookup"><span data-stu-id="d526b-208">We need to revisit regex to touch on something that isn't immediately obvious.</span></span> <span data-ttu-id="d526b-209">Användningen av regex fyller på `$matches` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d526b-209">The use of regex populates the `$matches` variable.</span></span> <span data-ttu-id="d526b-210">Jag går igenom användningen av `$matches` mer när jag pratar om [många sätt att använda regex][].</span><span class="sxs-lookup"><span data-stu-id="d526b-210">I do go into the use of `$matches` more when I talk about [The many ways to use regex][].</span></span> <span data-ttu-id="d526b-211">Här är ett snabbt exempel som visar hur det fungerar med namngivna matchningar.</span><span class="sxs-lookup"><span data-stu-id="d526b-211">Here is a quick sample to show it in action with named matches.</span></span>

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a><span data-ttu-id="d526b-212">$null</span><span class="sxs-lookup"><span data-stu-id="d526b-212">$null</span></span>

<span data-ttu-id="d526b-213">Du kan matcha ett `$null` värde som inte måste vara standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="d526b-213">You can match a `$null` value that doesn't have to be the default.</span></span>

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

<span data-ttu-id="d526b-214">Samma för en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="d526b-214">Same goes for an empty string.</span></span>

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a><span data-ttu-id="d526b-215">Kon stan Tut tryck</span><span class="sxs-lookup"><span data-stu-id="d526b-215">Constant expression</span></span>

<span data-ttu-id="d526b-216">Pettersson Dailey påpekade att vi kan använda ett kon stan Tut `$true` Tryck för att utvärdera `[bool]` objekt.</span><span class="sxs-lookup"><span data-stu-id="d526b-216">Lee Dailey pointed out that we can use a constant `$true` expression to evaluate `[bool]` items.</span></span>
<span data-ttu-id="d526b-217">Tänk dig att vi har flera booleska kontroller som måste utföras.</span><span class="sxs-lookup"><span data-stu-id="d526b-217">Imagine if we have several boolean checks that need to happen.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

<span data-ttu-id="d526b-218">Detta är ett rent sätt att utvärdera och vidta åtgärder för status för flera booleska fält.</span><span class="sxs-lookup"><span data-stu-id="d526b-218">This is a clean way to evaluate and take action on the status of several boolean fields.</span></span> <span data-ttu-id="d526b-219">Det häftiga med detta är att du kan ha en match som vänder statusen för ett värde som ännu inte har utvärderats.</span><span class="sxs-lookup"><span data-stu-id="d526b-219">The cool thing about this is that you can have one match flip the status of a value that hasn't been evaluated yet.</span></span>

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

<span data-ttu-id="d526b-220">Inställningen `$isEnabled` till `$true` i det här exemplet ser till att `$isVisible` också är inställd på `$true` .</span><span class="sxs-lookup"><span data-stu-id="d526b-220">Setting `$isEnabled` to `$true` in this example makes sure that `$isVisible` is also set to `$true`.</span></span> <span data-ttu-id="d526b-221">När `$isVisible` utvärderas, anropas dess script block.</span><span class="sxs-lookup"><span data-stu-id="d526b-221">Then when `$isVisible` gets evaluated, its scriptblock is invoked.</span></span> <span data-ttu-id="d526b-222">Detta är en bit som är intuitiv men som är en smarta användning av Mechanics.</span><span class="sxs-lookup"><span data-stu-id="d526b-222">This is a bit counter-intuitive but is a clever use of the mechanics.</span></span>

### <a name="switch-automatic-variable"></a><span data-ttu-id="d526b-223">$switch automatisk variabel</span><span class="sxs-lookup"><span data-stu-id="d526b-223">$switch automatic variable</span></span>

<span data-ttu-id="d526b-224">När `switch` bearbetar dess värden skapar den en uppräknare och anropar den `$switch` .</span><span class="sxs-lookup"><span data-stu-id="d526b-224">When the `switch` is processing its values, it creates an enumerator and calls it `$switch`.</span></span> <span data-ttu-id="d526b-225">Det här är en automatisk variabel som skapats av PowerShell och du kan ändra den direkt.</span><span class="sxs-lookup"><span data-stu-id="d526b-225">This is an automatic variable created by PowerShell and you can manipulate it directly.</span></span>

<span data-ttu-id="d526b-226">Detta pekade mig av [/u/frmadsen](https://www.reddit.com/user/frmadsen)</span><span class="sxs-lookup"><span data-stu-id="d526b-226">This was pointed out to me by [/u/frmadsen](https://www.reddit.com/user/frmadsen)</span></span>

<div class="reddit-embed" data-embed-media="www.redditmedia.com" data-embed-parent="false" data-embed-live="false" data-embed-uuid="8f6edbf1-abc6-4513-971e-ccd1d202889d" data-embed-created="2018-12-25T22:05:33.986Z"><span data-ttu-id="d526b-227"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Kommentar</a> från diskussionen <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">vad ska jag (IT-Student) lära sig att Master PowerShell?</a>.</span><span class="sxs-lookup"><span data-stu-id="d526b-227"><a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/ecj2kji/">Comment</a> from discussion <a href="https://www.reddit.com/r/PowerShell/comments/a90rx2/what_should_i_it_student_learn_to_master/">What should I (IT student) learn to master PowerShell?</a>.</span></span></div><script async src="https://www.redditstatic.com/comment-embed.js"></script>

<span data-ttu-id="d526b-228">Detta ger dig resultatet av:</span><span class="sxs-lookup"><span data-stu-id="d526b-228">This gives you the results of:</span></span>

```Output
2
4
```

<span data-ttu-id="d526b-229">Genom att flytta uppräkna ren framåt bearbetas inte nästa objekt av, `switch` men du kan komma åt det värdet direkt.</span><span class="sxs-lookup"><span data-stu-id="d526b-229">By moving the enumerator forward, the next item doesn't get processed by the `switch` but you can access that value directly.</span></span> <span data-ttu-id="d526b-230">Jag kallar IT-Madness.</span><span class="sxs-lookup"><span data-stu-id="d526b-230">I would call it madness.</span></span>

## <a name="other-patterns"></a><span data-ttu-id="d526b-231">Andra mönster</span><span class="sxs-lookup"><span data-stu-id="d526b-231">Other patterns</span></span>

### <a name="hashtables"></a><span data-ttu-id="d526b-232">Hash</span><span class="sxs-lookup"><span data-stu-id="d526b-232">Hashtables</span></span>

<span data-ttu-id="d526b-233">Ett av mina populäraste inlägg är det jag gjorde på [hash][].</span><span class="sxs-lookup"><span data-stu-id="d526b-233">One of my most popular posts is the one I did on [hashtables][].</span></span> <span data-ttu-id="d526b-234">En av användnings fallen för en `hashtable` är en uppslags tabell.</span><span class="sxs-lookup"><span data-stu-id="d526b-234">One of the use cases for a `hashtable` is to be a lookup table.</span></span> <span data-ttu-id="d526b-235">Det är en alternativ metod för ett vanligt mönster som en `switch` instruktion ofta riktar sig på.</span><span class="sxs-lookup"><span data-stu-id="d526b-235">That is an alternate approach to a common pattern that a `switch` statement is often addressing.</span></span>

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

<span data-ttu-id="d526b-236">Om jag bara använder en `switch` som sökning, använder jag ofta en `hashtable` i stället.</span><span class="sxs-lookup"><span data-stu-id="d526b-236">If I'm only using a `switch` as a lookup, I often use a `hashtable` instead.</span></span>

### <a name="enum"></a><span data-ttu-id="d526b-237">Enum</span><span class="sxs-lookup"><span data-stu-id="d526b-237">Enum</span></span>

<span data-ttu-id="d526b-238">PowerShell 5,0 introducerade `Enum` och det är också ett alternativ i det här fallet.</span><span class="sxs-lookup"><span data-stu-id="d526b-238">PowerShell 5.0 introduced the `Enum` and it's also an option in this case.</span></span>

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

<span data-ttu-id="d526b-239">Vi kan gå hela dagen och titta på olika sätt för att lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="d526b-239">We could go all day looking at different ways to solve this problem.</span></span> <span data-ttu-id="d526b-240">Jag ville bara se till att du visste att du hade några alternativ.</span><span class="sxs-lookup"><span data-stu-id="d526b-240">I just wanted to make sure you knew you had options.</span></span>

## <a name="final-words"></a><span data-ttu-id="d526b-241">Sista ord</span><span class="sxs-lookup"><span data-stu-id="d526b-241">Final words</span></span>

<span data-ttu-id="d526b-242">Switch-instruktionen är enkel på ytan, men den erbjuder vissa avancerade funktioner som de flesta inte inser är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="d526b-242">The switch statement is simple on the surface but it offers some advanced features that most people don't realize are available.</span></span> <span data-ttu-id="d526b-243">Genom att stränga dessa funktioner är det en kraftfull funktion.</span><span class="sxs-lookup"><span data-stu-id="d526b-243">Stringing those features together makes this a powerful feature.</span></span> <span data-ttu-id="d526b-244">Jag hoppas att du har lärt dig något som du inte hade realiserat tidigare.</span><span class="sxs-lookup"><span data-stu-id="d526b-244">I hope you learned something that you had not realized before.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[original version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[byta]: /powershell/module/microsoft.powershell.core/about/about_switch
[switch]: /powershell/module/microsoft.powershell.core/about/about_switch
[Växla parametrar]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[switch parameters]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[Många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[hash]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
