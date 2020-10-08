---
title: Allt du ville veta om matriser
description: Matriser är en grundläggande språk funktion för de flesta programmeringsspråk.
ms.date: 07/07/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 016c978a00d202a466610c7eaf4a09b9b69f29b2
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91814726"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a><span data-ttu-id="2af84-103">Allt du ville veta om matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-103">Everything you wanted to know about arrays</span></span>

<span data-ttu-id="2af84-104">[Matriser][] är en grundläggande språk funktion för de flesta programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="2af84-104">[Arrays][] are a fundamental language feature of most programming languages.</span></span> <span data-ttu-id="2af84-105">De är en samling med värden eller objekt som är svåra att undvika.</span><span class="sxs-lookup"><span data-stu-id="2af84-105">They're a collection of values or objects that are difficult to avoid.</span></span> <span data-ttu-id="2af84-106">Låt oss ta en närmare titt på matriser och allt de behöver för att erbjuda.</span><span class="sxs-lookup"><span data-stu-id="2af84-106">Let's take a close look at arrays and everything they have to offer.</span></span>

> [!NOTE]
> <span data-ttu-id="2af84-107">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="2af84-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="2af84-108">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="2af84-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="2af84-109">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="2af84-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="2af84-110">Vad är en matris?</span><span class="sxs-lookup"><span data-stu-id="2af84-110">What is an array?</span></span>

<span data-ttu-id="2af84-111">Jag ska börja med en grundläggande teknisk beskrivning av vilka matriser som är och hur de används av de flesta programmeringsspråk innan jag växlar till andra sätt som PowerShell använder dem.</span><span class="sxs-lookup"><span data-stu-id="2af84-111">I'm going to start with a basic technical description of what arrays are and how they are used by most programming languages before I shift into the other ways PowerShell makes use of them.</span></span>

<span data-ttu-id="2af84-112">En matris är en data struktur som fungerar som en samling av flera objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-112">An array is a data structure that serves as a collection of multiple items.</span></span> <span data-ttu-id="2af84-113">Du kan iterera över matrisen eller komma åt enskilda objekt med ett index.</span><span class="sxs-lookup"><span data-stu-id="2af84-113">You can iterate over the array or access individual items using an index.</span></span> <span data-ttu-id="2af84-114">Matrisen skapas som ett sekventiellt segment av minne där varje värde lagras direkt bredvid det andra.</span><span class="sxs-lookup"><span data-stu-id="2af84-114">The array is created as a sequential chunk of memory where each value is stored right next to the other.</span></span>

<span data-ttu-id="2af84-115">Jag tittar på var och en av de här detaljerna.</span><span class="sxs-lookup"><span data-stu-id="2af84-115">I'll touch on each of those details as we go.</span></span>

## <a name="basic-usage"></a><span data-ttu-id="2af84-116">Grundläggande användning</span><span class="sxs-lookup"><span data-stu-id="2af84-116">Basic usage</span></span>

<span data-ttu-id="2af84-117">Eftersom matriser är en sådan grundläggande funktion i PowerShell finns det en enkel syntax för att arbeta med dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2af84-117">Because arrays are such a basic feature of PowerShell, there is a simple syntax for working with them in PowerShell.</span></span>

### <a name="create-an-array"></a><span data-ttu-id="2af84-118">Skapa en matris</span><span class="sxs-lookup"><span data-stu-id="2af84-118">Create an array</span></span>

<span data-ttu-id="2af84-119">En tom matris kan skapas med hjälp av `@()`</span><span class="sxs-lookup"><span data-stu-id="2af84-119">An empty array can be created by using `@()`</span></span>

```powershell
PS> $data = @()
PS> $data.count
0
```

<span data-ttu-id="2af84-120">Vi kan skapa en matris och dirigera den med värden genom att placera dem inom `@()` parentesen.</span><span class="sxs-lookup"><span data-stu-id="2af84-120">We can create an array and seed it with values just by placing them in the `@()` parentheses.</span></span>

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

<span data-ttu-id="2af84-121">Den här matrisen innehåller 4 objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-121">This array has 4 items.</span></span> <span data-ttu-id="2af84-122">När vi kallar `$data` variabeln visas en lista över våra objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-122">When we call the `$data` variable, we see the list of our items.</span></span> <span data-ttu-id="2af84-123">Om det är en sträng mat ris, får vi en rad per sträng.</span><span class="sxs-lookup"><span data-stu-id="2af84-123">If it's an array of strings, then we get one line per string.</span></span>

<span data-ttu-id="2af84-124">Vi kan deklarera en matris på flera rader.</span><span class="sxs-lookup"><span data-stu-id="2af84-124">We can declare an array on multiple lines.</span></span> <span data-ttu-id="2af84-125">Kommatecken är valfri i det här fallet och skrivs vanligt vis ut.</span><span class="sxs-lookup"><span data-stu-id="2af84-125">The comma is optional in this case and generally left out.</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

<span data-ttu-id="2af84-126">Jag vill deklarera mina matriser på flera rader som.</span><span class="sxs-lookup"><span data-stu-id="2af84-126">I prefer to declare my arrays on multiple lines like that.</span></span> <span data-ttu-id="2af84-127">Det blir inte bara lättare att läsa när du har flera objekt, men det gör det också enklare att jämföra med tidigare versioner när du använder käll kontroll.</span><span class="sxs-lookup"><span data-stu-id="2af84-127">Not only does it get easier to read when you have multiple items, it also makes it easier to compare to previous versions when using source control.</span></span>

#### <a name="other-syntax"></a><span data-ttu-id="2af84-128">Annan syntax</span><span class="sxs-lookup"><span data-stu-id="2af84-128">Other syntax</span></span>

<span data-ttu-id="2af84-129">Det är vanligt att du `@()` använder syntaxen för att skapa en matris, men i kommaavgränsade listor fungerar det mesta av tiden.</span><span class="sxs-lookup"><span data-stu-id="2af84-129">It's commonly understood that `@()` is the syntax for creating an array, but comma-separated lists work most of the time.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a><span data-ttu-id="2af84-130">Skriva utdata för att skapa matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-130">Write-Output to create arrays</span></span>

<span data-ttu-id="2af84-131">Ett häftigt svårt att nämna är att du kan använda `Write-Output` för att snabbt skapa strängar i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2af84-131">One cool little trick worth mentioning is that you can use `Write-Output` to quickly create strings at the console.</span></span>

```powershell
$data = Write-Output Zero One Two Three
```

<span data-ttu-id="2af84-132">Detta är praktiskt eftersom du inte behöver ange citat tecken runt strängarna när parametern accepterar strängar.</span><span class="sxs-lookup"><span data-stu-id="2af84-132">This is handy because you don't have to put quotes around the strings when the parameter accepts strings.</span></span> <span data-ttu-id="2af84-133">Jag skulle aldrig göra detta i ett skript, men det är ett rättvist spel i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2af84-133">I would never do this in a script but it's fair game in the console.</span></span>

### <a name="accessing-items"></a><span data-ttu-id="2af84-134">Åtkomst till objekt</span><span class="sxs-lookup"><span data-stu-id="2af84-134">Accessing items</span></span>

<span data-ttu-id="2af84-135">Nu när du har en matris med objekt i den, kanske du vill komma åt och uppdatera dessa objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-135">Now that you have an array with items in it, you may want to access and update those items.</span></span>

#### <a name="offset"></a><span data-ttu-id="2af84-136">Offset</span><span class="sxs-lookup"><span data-stu-id="2af84-136">Offset</span></span>

<span data-ttu-id="2af84-137">För att få åtkomst till enskilda objekt använder vi hakparenteserna `[]` med ett förskjutnings värde som börjar vid 0.</span><span class="sxs-lookup"><span data-stu-id="2af84-137">To access individual items, we use the brackets `[]` with an offset value starting at 0.</span></span> <span data-ttu-id="2af84-138">Så här får vi det första objektet i vår matris:</span><span class="sxs-lookup"><span data-stu-id="2af84-138">This is how we get the first item in our array:</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

<span data-ttu-id="2af84-139">Anledningen till varför vi använder noll här är att det första objektet är i början av listan, så vi använder en förskjutning på 0 objekt för att komma till den.</span><span class="sxs-lookup"><span data-stu-id="2af84-139">The reason why we use zero here is because the first item is at the beginning of the list so we use an offset of 0 items to get to it.</span></span> <span data-ttu-id="2af84-140">För att komma till det andra objektet måste vi använda en förskjutning på 1 för att hoppa över det första objektet.</span><span class="sxs-lookup"><span data-stu-id="2af84-140">To get to the second item, we would need to use an offset of 1 to skip the first item.</span></span>

```powershell
PS> $data[1]
One
```

<span data-ttu-id="2af84-141">Detta innebär att det sista objektet finns vid förskjutning 3.</span><span class="sxs-lookup"><span data-stu-id="2af84-141">This would mean that the last item is at offset 3.</span></span>

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a><span data-ttu-id="2af84-142">Index</span><span class="sxs-lookup"><span data-stu-id="2af84-142">Index</span></span>

<span data-ttu-id="2af84-143">Nu kan du se varför jag har valt de värden som jag gjorde för det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="2af84-143">Now you can see why I picked the values that I did for this example.</span></span> <span data-ttu-id="2af84-144">Jag introducerade detta som en förskjutning eftersom det är det som är det som egentligen är, men den här förskjutningen kallas ofta för ett index.</span><span class="sxs-lookup"><span data-stu-id="2af84-144">I introduced this as an offset because that is what it really is, but this offset is more commonly referred to as an index.</span></span> <span data-ttu-id="2af84-145">Ett index som startar vid `0` .</span><span class="sxs-lookup"><span data-stu-id="2af84-145">An index that starts at `0`.</span></span> <span data-ttu-id="2af84-146">För resten av den här artikeln anropar du förskjutningen av ett index.</span><span class="sxs-lookup"><span data-stu-id="2af84-146">For the rest of this article I will call the offset an index.</span></span>

#### <a name="special-index-tricks"></a><span data-ttu-id="2af84-147">Särskilda index trick</span><span class="sxs-lookup"><span data-stu-id="2af84-147">Special index tricks</span></span>

<span data-ttu-id="2af84-148">På de flesta språk kan du bara ange ett enda tal som index och få ett enda objekt tillbaka.</span><span class="sxs-lookup"><span data-stu-id="2af84-148">In most languages, you can only specify a single number as the index and you get a single item back.</span></span>
<span data-ttu-id="2af84-149">PowerShell är mycket mer flexibelt.</span><span class="sxs-lookup"><span data-stu-id="2af84-149">PowerShell is much more flexible.</span></span> <span data-ttu-id="2af84-150">Du kan använda flera index samtidigt.</span><span class="sxs-lookup"><span data-stu-id="2af84-150">You can use multiple indexes at once.</span></span> <span data-ttu-id="2af84-151">Genom att tillhandahålla en lista över index kan vi välja flera objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-151">By providing a list of indexes, we can select several items.</span></span>

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

<span data-ttu-id="2af84-152">Objekten returneras baserat på ordningen på de index som tillhandahålls.</span><span class="sxs-lookup"><span data-stu-id="2af84-152">The items are returned based on the order of the indexes provided.</span></span> <span data-ttu-id="2af84-153">Om du duplicerar ett index får du objektet båda gånger.</span><span class="sxs-lookup"><span data-stu-id="2af84-153">If you duplicate an index, you get that item both times.</span></span>

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

<span data-ttu-id="2af84-154">Vi kan ange en sekvens med siffror med den inbyggda `..` operatorn.</span><span class="sxs-lookup"><span data-stu-id="2af84-154">We can specify a sequence of numbers with the built-in `..` operator.</span></span>

```powershell
PS> $data[1..3]
One
Two
Three
```

<span data-ttu-id="2af84-155">Detta fungerar även i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="2af84-155">This works in reverse too.</span></span>

```powershell
PS> $data[3..1]
Three
Two
One
```

<span data-ttu-id="2af84-156">Du kan använda negativa index värden för att räkna från slutet.</span><span class="sxs-lookup"><span data-stu-id="2af84-156">You can use negative index values to offset from the end.</span></span> <span data-ttu-id="2af84-157">Så om du behöver det sista objektet i listan kan du använda `-1` .</span><span class="sxs-lookup"><span data-stu-id="2af84-157">So if you need the last item in the list, you can use `-1`.</span></span>

```powershell
PS> $data[-1]
Three
```

<span data-ttu-id="2af84-158">Ett ord med varnings meddelande här med `..` operatorn.</span><span class="sxs-lookup"><span data-stu-id="2af84-158">One word of caution here with the `..` operator.</span></span> <span data-ttu-id="2af84-159">Sekvensen `0..-1` och `-1..0` utvärdera till värdena `0,-1` och `-1,0` .</span><span class="sxs-lookup"><span data-stu-id="2af84-159">The sequence `0..-1` and `-1..0` evaluate to the values `0,-1` and `-1,0`.</span></span> <span data-ttu-id="2af84-160">Det är enkelt att se `$data[0..-1]` och fundera på att räkna upp alla objekt om du glömmer den här informationen.</span><span class="sxs-lookup"><span data-stu-id="2af84-160">It's easy to see `$data[0..-1]` and think it would enumerate all items if you forget this detail.</span></span> <span data-ttu-id="2af84-161">`$data[0..-1]` ger dig samma värde som när `$data[0,-1]` du ger det första och sista objektet i matrisen (och inget av de andra värdena).</span><span class="sxs-lookup"><span data-stu-id="2af84-161">`$data[0..-1]` gives you the same value as `$data[0,-1]` by giving you the first and last item in the array (and none of the other values).</span></span>

#### <a name="out-of-bounds"></a><span data-ttu-id="2af84-162">Utanför intervallet</span><span class="sxs-lookup"><span data-stu-id="2af84-162">Out of bounds</span></span>

<span data-ttu-id="2af84-163">Om du försöker komma åt ett index för ett objekt som är i slutet av matrisen på de flesta språk får du någon typ av fel eller ett undantag.</span><span class="sxs-lookup"><span data-stu-id="2af84-163">In most languages, if you try to access an index of an item that is past the end of the array, you would get some type of error or an exception.</span></span> <span data-ttu-id="2af84-164">PowerShell returnerar ingenting i tysthet.</span><span class="sxs-lookup"><span data-stu-id="2af84-164">PowerShell silently returns nothing.</span></span>

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a><span data-ttu-id="2af84-165">Det går inte att indexera till en null-matris</span><span class="sxs-lookup"><span data-stu-id="2af84-165">Cannot index into a null array</span></span>

<span data-ttu-id="2af84-166">Om din variabel är `$null` och du försöker indexera den som en matris får du ett `System.Management.Automation.RuntimeException` undantag med meddelandet `Cannot index into a null array` .</span><span class="sxs-lookup"><span data-stu-id="2af84-166">If your variable is `$null` and you try to index it like an array, you get a `System.Management.Automation.RuntimeException` exception with the message `Cannot index into a null array`.</span></span>

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

<span data-ttu-id="2af84-167">Se därför till att matriserna inte är `$null` innan du försöker komma åt element i dem.</span><span class="sxs-lookup"><span data-stu-id="2af84-167">So make sure your arrays are not `$null` before you try to access elements inside them.</span></span>

#### <a name="count"></a><span data-ttu-id="2af84-168">Antal</span><span class="sxs-lookup"><span data-stu-id="2af84-168">Count</span></span>

<span data-ttu-id="2af84-169">Matriser och andra samlingar har en Count-egenskap som visar hur många objekt som finns i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-169">Arrays and other collections have a count property that tells you how many items are in the array.</span></span>

```powershell
PS> $data.count
4
```

<span data-ttu-id="2af84-170">PowerShell 3,0 har lagt till en Count-egenskap på de flesta objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-170">PowerShell 3.0 added a count property to most objects.</span></span> <span data-ttu-id="2af84-171">Du kan ha ett enda objekt och det bör ge dig ett antal `1` .</span><span class="sxs-lookup"><span data-stu-id="2af84-171">you can have a single object and it should give you a count of `1`.</span></span>

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

<span data-ttu-id="2af84-172">`$null`Det finns även en Count-egenskap förutom den returnerar `0` .</span><span class="sxs-lookup"><span data-stu-id="2af84-172">Even `$null` has a count property except it returns `0`.</span></span>

```powershell
PS> $null.count
0
```

<span data-ttu-id="2af84-173">Det finns vissa traps som jag ska gå tillbaka när jag söker efter `$null` eller tomma matriser senare i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="2af84-173">There are some traps here that I will revisit when I cover checking for `$null` or empty arrays later on in this article.</span></span>

#### <a name="off-by-one-errors"></a><span data-ttu-id="2af84-174">Av-ett fel</span><span class="sxs-lookup"><span data-stu-id="2af84-174">Off-by-one errors</span></span>

<span data-ttu-id="2af84-175">Ett vanligt programmerings fel har skapats eftersom matriser börjar vid index 0.</span><span class="sxs-lookup"><span data-stu-id="2af84-175">A common programming error is created because arrays start at index 0.</span></span> <span data-ttu-id="2af84-176">Andra fel kan införas på två sätt.</span><span class="sxs-lookup"><span data-stu-id="2af84-176">Off-by-one errors can be introduced in two ways.</span></span>

<span data-ttu-id="2af84-177">Det första är att tänka på att du vill ha det andra objektet och använda ett index för `2` och verkligen hämtar det tredje objektet.</span><span class="sxs-lookup"><span data-stu-id="2af84-177">The first is by mentally thinking you want the second item and using an index of `2` and really getting the third item.</span></span> <span data-ttu-id="2af84-178">Eller genom att fundera på att du har fyra objekt och du vill ha det sista objektet så använder du antalet för att komma åt det sista objektet.</span><span class="sxs-lookup"><span data-stu-id="2af84-178">Or by thinking that you have four items and you want last item, so you use the count to access the last item.</span></span>

```powershell
$data[ $data.count ]
```

<span data-ttu-id="2af84-179">PowerShell är perfekt glad att låta dig göra det och ge dig exakt det objekt som finns vid index 4: `$null` .</span><span class="sxs-lookup"><span data-stu-id="2af84-179">PowerShell is perfectly happy to let you do that and give you exactly what item exists at index 4: `$null`.</span></span> <span data-ttu-id="2af84-180">Du bör använda `$data.count - 1` eller det `-1` som vi har lärt dig ovan.</span><span class="sxs-lookup"><span data-stu-id="2af84-180">You should be using `$data.count - 1` or the `-1` that we learned about above.</span></span>

```powershell
PS> $data[ $data.count - 1 ]
Three
```

<span data-ttu-id="2af84-181">Det är här du kan använda `-1` indexet för att hämta det sista elementet.</span><span class="sxs-lookup"><span data-stu-id="2af84-181">This is where you can use the `-1` index to get the last element.</span></span>

```powershell
PS> $data[ -1 ]
Three
```

<span data-ttu-id="2af84-182">Pettersson Dailey pekar också ut till mig som vi kan använda `$data.GetUpperBound(0)` för att hämta det högsta index numret.</span><span class="sxs-lookup"><span data-stu-id="2af84-182">Lee Dailey also pointed out to me that we can use `$data.GetUpperBound(0)` to get the max index number.</span></span>

```powershell
PS> $data.GetUpperBound(0)
3
PS> $data[ $data.GetUpperBound(0) ]
Three
```

<span data-ttu-id="2af84-183">Det andra vanligaste sättet är när du går igenom listan och inte stoppar vid rätt tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="2af84-183">The second most common way is when iterating the list and not stopping at the right time.</span></span> <span data-ttu-id="2af84-184">Jag går igenom detta när vi pratar om att använda `for` slingan.</span><span class="sxs-lookup"><span data-stu-id="2af84-184">I'll revisit this when we talk about using the `for` loop.</span></span>

### <a name="updating-items"></a><span data-ttu-id="2af84-185">Uppdaterar objekt</span><span class="sxs-lookup"><span data-stu-id="2af84-185">Updating items</span></span>

<span data-ttu-id="2af84-186">Vi kan använda samma index för att uppdatera befintliga objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-186">We can use the same index to update existing items in the array.</span></span> <span data-ttu-id="2af84-187">Detta ger oss direkt åtkomst till uppdatering av enskilda objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-187">This gives us direct access to update individual items.</span></span>

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

<span data-ttu-id="2af84-188">Om vi försöker uppdatera ett objekt som har passerat det sista elementet får vi ett `Index was outside the bounds of the array.` fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="2af84-188">If we try to update an item that is past the last element, then we get an `Index was outside the bounds of the array.` error.</span></span>

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

<span data-ttu-id="2af84-189">Jag går tillbaka senare när jag pratar om hur man gör en matris större.</span><span class="sxs-lookup"><span data-stu-id="2af84-189">I'll revisit this later when I talk about how to make an array larger.</span></span>

### <a name="iteration"></a><span data-ttu-id="2af84-190">Iteration</span><span class="sxs-lookup"><span data-stu-id="2af84-190">Iteration</span></span>

<span data-ttu-id="2af84-191">Ibland kan du behöva gå igenom hela listan och utföra en åtgärd för varje objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-191">At some point, you might need to walk or iterate the entire list and perform some action for each item in the array.</span></span>

#### <a name="pipeline"></a><span data-ttu-id="2af84-192">Pipeline</span><span class="sxs-lookup"><span data-stu-id="2af84-192">Pipeline</span></span>

<span data-ttu-id="2af84-193">Matriser och PowerShell-pipeline är avsedda för varandra.</span><span class="sxs-lookup"><span data-stu-id="2af84-193">Arrays and the PowerShell pipeline are meant for each other.</span></span> <span data-ttu-id="2af84-194">Detta är ett av de enklaste sätten att bearbeta dessa värden.</span><span class="sxs-lookup"><span data-stu-id="2af84-194">This is one of the simplest ways to process over those values.</span></span> <span data-ttu-id="2af84-195">När du skickar en matris till en pipeline bearbetas varje objekt i matrisen separat.</span><span class="sxs-lookup"><span data-stu-id="2af84-195">When you pass an array to a pipeline, each item inside the array is processed individually.</span></span>

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

<span data-ttu-id="2af84-196">Om du inte har sett `$PSItem` tidigare vet du att det är samma sak som `$_` .</span><span class="sxs-lookup"><span data-stu-id="2af84-196">If you have not seen `$PSItem` before, just know that it's the same thing as `$_`.</span></span> <span data-ttu-id="2af84-197">Du kan använda antingen en, eftersom de båda representerar det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2af84-197">You can use either one because they both represent the current object in the pipeline.</span></span>

#### <a name="foreach-loop"></a><span data-ttu-id="2af84-198">Förgrunds slinga</span><span class="sxs-lookup"><span data-stu-id="2af84-198">ForEach loop</span></span>

<span data-ttu-id="2af84-199">`ForEach`Slingan fungerar bra med samlingar.</span><span class="sxs-lookup"><span data-stu-id="2af84-199">The `ForEach` loop works well with collections.</span></span> <span data-ttu-id="2af84-200">Använda syntaxen: `foreach ( <variable> in <collection> )`</span><span class="sxs-lookup"><span data-stu-id="2af84-200">Using the syntax: `foreach ( <variable> in <collection> )`</span></span>

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a><span data-ttu-id="2af84-201">Förgrunds metod</span><span class="sxs-lookup"><span data-stu-id="2af84-201">ForEach method</span></span>

<span data-ttu-id="2af84-202">Jag vill glömma bort det här, men det fungerar bra för enkla åtgärder.</span><span class="sxs-lookup"><span data-stu-id="2af84-202">I tend to forget about this one but it works well for simple operations.</span></span> <span data-ttu-id="2af84-203">Med PowerShell kan du anropa `.ForEach()` en samling.</span><span class="sxs-lookup"><span data-stu-id="2af84-203">PowerShell allows you to call `.ForEach()` on a collection.</span></span>

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

<span data-ttu-id="2af84-204">`.foreach()`Tar en parameter som är ett skript block.</span><span class="sxs-lookup"><span data-stu-id="2af84-204">The `.foreach()` takes a parameter that is a script block.</span></span> <span data-ttu-id="2af84-205">Du kan ta bort parenteserna och bara ange skript blocket.</span><span class="sxs-lookup"><span data-stu-id="2af84-205">You can drop the parentheses and just provide the script block.</span></span>

```powershell
$data.foreach{"Item [$PSItem]"}
```

<span data-ttu-id="2af84-206">Detta är en mindre känd syntax, men den fungerar precis på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="2af84-206">This is a lesser known syntax but it works just the same.</span></span> <span data-ttu-id="2af84-207">Den här `foreach` metoden har lagts till i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="2af84-207">This `foreach` method was added in PowerShell 4.0.</span></span>

#### <a name="for-loop"></a><span data-ttu-id="2af84-208">For-loop</span><span class="sxs-lookup"><span data-stu-id="2af84-208">For loop</span></span>

<span data-ttu-id="2af84-209">`for`Slingan används kraftigt på de flesta andra språk, men du ser det inte mycket i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2af84-209">The `for` loop is used heavily in most other languages but you don't see it much in PowerShell.</span></span> <span data-ttu-id="2af84-210">När du gör det är det ofta i sammanhanget att gå en matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-210">When you do see it, it's often in the context of walking an array.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="2af84-211">Det första vi gör är att initiera en `$index` till `0` .</span><span class="sxs-lookup"><span data-stu-id="2af84-211">The first thing we do is initialize an `$index` to `0`.</span></span> <span data-ttu-id="2af84-212">Sedan lägger vi till villkoret som `$index` måste vara mindre än `$data.count` .</span><span class="sxs-lookup"><span data-stu-id="2af84-212">Then we add the condition that `$index` must be less than `$data.count`.</span></span> <span data-ttu-id="2af84-213">Slutligen anger vi att det ska gå att öka indexet genom att varje gång vi loopar `1` .</span><span class="sxs-lookup"><span data-stu-id="2af84-213">Finally, we specify that every time we loop that me must increase the index by `1`.</span></span> <span data-ttu-id="2af84-214">I det här fallet `$index++` är det kort för `$index = $index + 1` .</span><span class="sxs-lookup"><span data-stu-id="2af84-214">In this case `$index++` is short for `$index = $index + 1`.</span></span>

<span data-ttu-id="2af84-215">När du använder en `for` slinga bör du ägna särskild uppmärksamhet åt villkoret.</span><span class="sxs-lookup"><span data-stu-id="2af84-215">Whenever you're using a `for` loop, pay special attention to the condition.</span></span> <span data-ttu-id="2af84-216">Jag använde `$index -lt $data.count` detta.</span><span class="sxs-lookup"><span data-stu-id="2af84-216">I used `$index -lt $data.count` here.</span></span> <span data-ttu-id="2af84-217">Det är enkelt att få tillståndet något fel för att få ett fel i din logik.</span><span class="sxs-lookup"><span data-stu-id="2af84-217">It's easy to get the condition slightly wrong to get an off-by-one error in your logic.</span></span> <span data-ttu-id="2af84-218">`$index -le $data.count` `$index -lt ($data.count - 1)` Det kan vara något fel att använda eller.</span><span class="sxs-lookup"><span data-stu-id="2af84-218">Using `$index -le $data.count` or `$index -lt ($data.count - 1)` are ever so slightly wrong.</span></span> <span data-ttu-id="2af84-219">Detta skulle leda till att du bearbetar för många eller för få objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-219">That would cause your result to process too many or too few items.</span></span> <span data-ttu-id="2af84-220">Detta är det klassiska fel meddelandet.</span><span class="sxs-lookup"><span data-stu-id="2af84-220">This is the classic off-by-one error.</span></span>

#### <a name="switch-loop"></a><span data-ttu-id="2af84-221">Växel slinga</span><span class="sxs-lookup"><span data-stu-id="2af84-221">Switch loop</span></span>

<span data-ttu-id="2af84-222">Det här är en som är lätt att förbise.</span><span class="sxs-lookup"><span data-stu-id="2af84-222">This is one that is easy to overlook.</span></span> <span data-ttu-id="2af84-223">Om du anger en matris till en [switch-instruktion][], kontrollerar den varje objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-223">If you provide an array to a [switch statement][], it checks each item in the array.</span></span>

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

<span data-ttu-id="2af84-224">Det finns många häftiga saker som vi kan göra med Switch-instruktionen.</span><span class="sxs-lookup"><span data-stu-id="2af84-224">There are a lot of cool things that we can do with the switch statement.</span></span> <span data-ttu-id="2af84-225">Jag har en annan artikel som är engagerad i detta.</span><span class="sxs-lookup"><span data-stu-id="2af84-225">I have another article dedicated to this.</span></span>

- <span data-ttu-id="2af84-226">[Allt du ville veta om switch-instruktionen][switch] -sats</span><span class="sxs-lookup"><span data-stu-id="2af84-226">[Everything you ever wanted to know about the switch statement][switch statement]</span></span>

#### <a name="updating-values"></a><span data-ttu-id="2af84-227">Uppdaterar värden</span><span class="sxs-lookup"><span data-stu-id="2af84-227">Updating values</span></span>

<span data-ttu-id="2af84-228">Om matrisen är en samling strängar eller heltal (värde typer) kan ibland det hända att du vill uppdatera värdena i matrisen när du loopar.</span><span class="sxs-lookup"><span data-stu-id="2af84-228">When your array is a collection of string or integers (value types), sometimes you may want to update the values in the array as you loop over them.</span></span> <span data-ttu-id="2af84-229">De flesta av slingarna ovan använder en variabel i slingan som innehåller en kopia av värdet.</span><span class="sxs-lookup"><span data-stu-id="2af84-229">Most of the loops above use a variable in the loop that holds a copy of the value.</span></span> <span data-ttu-id="2af84-230">Om du uppdaterar variabeln, uppdateras inte det ursprungliga värdet i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-230">If you update that variable, the original value in the array is not updated.</span></span>

<span data-ttu-id="2af84-231">Undantaget till den instruktionen är `for` slingan.</span><span class="sxs-lookup"><span data-stu-id="2af84-231">The exception to that statement is the `for` loop.</span></span> <span data-ttu-id="2af84-232">Om du vill visa en matris och uppdatera värden inuti den, `for` är loopen det du söker.</span><span class="sxs-lookup"><span data-stu-id="2af84-232">If you want to walk an array and update values inside it, then the `for` loop is what you're looking for.</span></span>

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

<span data-ttu-id="2af84-233">Det här exemplet tar ett värde av indexet, gör några ändringar och använder sedan samma index för att tilldela det igen.</span><span class="sxs-lookup"><span data-stu-id="2af84-233">This example takes a value by index, makes a few changes, and then uses that same index to assign it back.</span></span>

## <a name="arrays-of-objects"></a><span data-ttu-id="2af84-234">Matriser med objekt</span><span class="sxs-lookup"><span data-stu-id="2af84-234">Arrays of Objects</span></span>

<span data-ttu-id="2af84-235">Hittills har vi placerat i en matris som värde typ, men matriser kan också innehålla objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-235">So far, the only thing we've placed in an array is a value type, but arrays can also contain objects.</span></span>

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

<span data-ttu-id="2af84-236">Många cmdlets returnerar samlingar av objekt som matriser när du tilldelar dem till en variabel.</span><span class="sxs-lookup"><span data-stu-id="2af84-236">Many cmdlets return collections of objects as arrays when you assign them to a variable.</span></span>

```powershell
$processList = Get-Process
```

<span data-ttu-id="2af84-237">Alla grundläggande funktioner som vi redan har talat om fortfarande gäller för matriser med objekt med lite information som pekar på.</span><span class="sxs-lookup"><span data-stu-id="2af84-237">All of the basic features we already talked about still apply to arrays of objects with a few details worth pointing out.</span></span>

### <a name="accessing-properties"></a><span data-ttu-id="2af84-238">Åtkomst till egenskaper</span><span class="sxs-lookup"><span data-stu-id="2af84-238">Accessing properties</span></span>

<span data-ttu-id="2af84-239">Vi kan använda ett index för att komma åt ett enskilt objekt i en samling, precis som med värde typerna.</span><span class="sxs-lookup"><span data-stu-id="2af84-239">We can use an index to access an individual item in a collection just like with value types.</span></span>

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="2af84-240">Vi kan komma åt och uppdatera egenskaper direkt.</span><span class="sxs-lookup"><span data-stu-id="2af84-240">We can access and update properties directly.</span></span>

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a><span data-ttu-id="2af84-241">Mat ris egenskaper</span><span class="sxs-lookup"><span data-stu-id="2af84-241">Array properties</span></span>

<span data-ttu-id="2af84-242">Normalt skulle du behöva räkna upp hela listan som detta för att få åtkomst till alla egenskaper:</span><span class="sxs-lookup"><span data-stu-id="2af84-242">Normally you would have to enumerate the whole list like this to access all the properties:</span></span>

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

<span data-ttu-id="2af84-243">Eller med hjälp av `Select-Object -ExpandProperty` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2af84-243">Or by using the `Select-Object -ExpandProperty` cmdlet.</span></span>

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

<span data-ttu-id="2af84-244">Men PowerShell ger oss möjlighet att begära `LastName` direkt.</span><span class="sxs-lookup"><span data-stu-id="2af84-244">But PowerShell offers us the ability to request `LastName` directly.</span></span> <span data-ttu-id="2af84-245">PowerShell räknar upp dem för oss och returnerar en rensad lista.</span><span class="sxs-lookup"><span data-stu-id="2af84-245">PowerShell enumerates them all for us and returns a clean list.</span></span>

```powershell
PS> $data.LastName

Marquette
Doe
```

<span data-ttu-id="2af84-246">Uppräkningen utförs fortfarande men vi ser inte komplexiteten bakom den.</span><span class="sxs-lookup"><span data-stu-id="2af84-246">The enumeration still happens but we don't see the complexity behind it.</span></span>

### <a name="where-object-filtering"></a><span data-ttu-id="2af84-247">Where-objekt filtrering</span><span class="sxs-lookup"><span data-stu-id="2af84-247">Where-Object filtering</span></span>

<span data-ttu-id="2af84-248">`Where-Object`I så fall kan vi filtrera och välja vad du vill ha i matrisen baserat på egenskaperna för objektet.</span><span class="sxs-lookup"><span data-stu-id="2af84-248">This is where `Where-Object` comes in so we can filter and select what we want out of the array based on the properties of the object.</span></span>

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

<span data-ttu-id="2af84-249">Vi kan skriva samma fråga för att få din `FirstName` sökning.</span><span class="sxs-lookup"><span data-stu-id="2af84-249">We can write that same query to get the `FirstName` we are looking for.</span></span>

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a><span data-ttu-id="2af84-250">Where ()</span><span class="sxs-lookup"><span data-stu-id="2af84-250">Where()</span></span>

<span data-ttu-id="2af84-251">Matriser har en `Where()` metod för dem som gör att du kan ange en `scriptblock` för filtret.</span><span class="sxs-lookup"><span data-stu-id="2af84-251">Arrays have a `Where()` method on them that allows you to specify a `scriptblock` for the filter.</span></span>

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

<span data-ttu-id="2af84-252">Den här funktionen lades till i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="2af84-252">This feature was added in PowerShell 4.0.</span></span>

### <a name="updating-objects-in-loops"></a><span data-ttu-id="2af84-253">Uppdatera objekt i slingor</span><span class="sxs-lookup"><span data-stu-id="2af84-253">Updating objects in loops</span></span>

<span data-ttu-id="2af84-254">Med värde typer är det enda sättet att uppdatera matrisen att använda en for-loop eftersom vi måste känna till indexet för att ersätta värdet.</span><span class="sxs-lookup"><span data-stu-id="2af84-254">With value types, the only way to update the array is to use a for loop because we need to know the index to replace the value.</span></span> <span data-ttu-id="2af84-255">Vi har fler alternativ med objekt eftersom de är referens typer.</span><span class="sxs-lookup"><span data-stu-id="2af84-255">We have more options with objects because they are reference types.</span></span> <span data-ttu-id="2af84-256">Här är ett snabbt exempel:</span><span class="sxs-lookup"><span data-stu-id="2af84-256">Here is a quick example:</span></span>

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

<span data-ttu-id="2af84-257">Den här slingen går igenom varje objekt i `$data` matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-257">This loop is walking every object in the `$data` array.</span></span> <span data-ttu-id="2af84-258">Eftersom objekt är referens typer `$person` refererar variabeln exakt samma objekt som finns i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-258">Because objects are reference types, the `$person` variable references the exact same object that is in the array.</span></span> <span data-ttu-id="2af84-259">Så uppdateringar av dess egenskaper uppdaterar du originalet.</span><span class="sxs-lookup"><span data-stu-id="2af84-259">So updates to its properties do update the original.</span></span>

<span data-ttu-id="2af84-260">Du kan fortfarande inte ersätta hela objektet på det här sättet.</span><span class="sxs-lookup"><span data-stu-id="2af84-260">You still can't replace the whole object this way.</span></span> <span data-ttu-id="2af84-261">Om du försöker tilldela ett nytt objekt till `$person` variabeln uppdaterar du variabel referensen till något annat som inte längre pekar på det ursprungliga objektet i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-261">If you try to assign a new object to the `$person` variable, you're updating the variable reference to something else that no longer points to the original object in the array.</span></span> <span data-ttu-id="2af84-262">Detta fungerar som du förväntar dig:</span><span class="sxs-lookup"><span data-stu-id="2af84-262">This doesn't work like you would expect:</span></span>

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a><span data-ttu-id="2af84-263">Operatorer</span><span class="sxs-lookup"><span data-stu-id="2af84-263">Operators</span></span>

<span data-ttu-id="2af84-264">Operatorerna i PowerShell fungerar också på matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-264">The operators in PowerShell also work on arrays.</span></span> <span data-ttu-id="2af84-265">Några av dem fungerar något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="2af84-265">Some of them work slightly differently.</span></span>

### <a name="-join"></a><span data-ttu-id="2af84-266">– Anslut</span><span class="sxs-lookup"><span data-stu-id="2af84-266">-join</span></span>

<span data-ttu-id="2af84-267">`-join`Operatören är den mest uppenbara, så låt oss titta på den först.</span><span class="sxs-lookup"><span data-stu-id="2af84-267">The `-join` operator is the most obvious one so let's look at it first.</span></span> <span data-ttu-id="2af84-268">Jag gillar `-join` operatorn och använder den ofta.</span><span class="sxs-lookup"><span data-stu-id="2af84-268">I like the `-join` operator and use it often.</span></span> <span data-ttu-id="2af84-269">Den kopplar ihop alla element i matrisen med det tecken eller den sträng som du anger.</span><span class="sxs-lookup"><span data-stu-id="2af84-269">It joins all elements in the array with the character or string that you specify.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

<span data-ttu-id="2af84-270">En av de funktioner som jag gillar om `-join` operatorn är att den hanterar enskilda objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-270">One of the features that I like about the `-join` operator is that it handles single items.</span></span>

```powershell
PS> 1 -join '-'
1
```

<span data-ttu-id="2af84-271">Jag använder det här i loggnings-och utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="2af84-271">I use this inside logging and verbose messages.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a><span data-ttu-id="2af84-272">– Anslut $array</span><span class="sxs-lookup"><span data-stu-id="2af84-272">-join $array</span></span>

<span data-ttu-id="2af84-273">Här är ett smarta-stick som Pettersson Dailey påpekade till mig.</span><span class="sxs-lookup"><span data-stu-id="2af84-273">Here is a clever trick that Lee Dailey pointed out to me.</span></span> <span data-ttu-id="2af84-274">I stället för att göra detta, om du vill koppla allt utan en avgränsare:</span><span class="sxs-lookup"><span data-stu-id="2af84-274">If you ever want to join everything without a delimiter, instead of doing this:</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

<span data-ttu-id="2af84-275">Du kan använda `-join` med matrisen som parameter utan prefix.</span><span class="sxs-lookup"><span data-stu-id="2af84-275">You can use `-join` with the array as the parameter with no prefix.</span></span> <span data-ttu-id="2af84-276">Ta en titt på det här exemplet för att se att jag pratar om.</span><span class="sxs-lookup"><span data-stu-id="2af84-276">Take a look at this example to see that I'm talking about.</span></span>

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a><span data-ttu-id="2af84-277">-Ersätt och-dela</span><span class="sxs-lookup"><span data-stu-id="2af84-277">-replace and -split</span></span>

<span data-ttu-id="2af84-278">De andra operatorerna som `-replace` och `-split` körs på varje objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-278">The other operators like `-replace` and `-split` execute on each item in the array.</span></span> <span data-ttu-id="2af84-279">Jag kan inte säga att jag någonsin har använt dem på det här sättet, men här är ett exempel.</span><span class="sxs-lookup"><span data-stu-id="2af84-279">I can't say that I have ever used them this way but here is an example.</span></span>

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a><span data-ttu-id="2af84-280">– innehåller</span><span class="sxs-lookup"><span data-stu-id="2af84-280">-contains</span></span>

<span data-ttu-id="2af84-281">Med `-contains` operatorn kan du kontrol lera en matris med värden för att se om den innehåller ett angivet värde.</span><span class="sxs-lookup"><span data-stu-id="2af84-281">The `-contains` operator allows you to check an array of values to see if it contains a specified value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a><span data-ttu-id="2af84-282">– in</span><span class="sxs-lookup"><span data-stu-id="2af84-282">-in</span></span>

<span data-ttu-id="2af84-283">Om du har ett enda värde som du vill verifiera matchar ett av flera värden kan du använda `-in` operatorn.</span><span class="sxs-lookup"><span data-stu-id="2af84-283">When you have a single value that you would like to verify matches one of several values, you can use the `-in` operator.</span></span> <span data-ttu-id="2af84-284">Värdet är till vänster och matrisen på höger sida av operatorn.</span><span class="sxs-lookup"><span data-stu-id="2af84-284">The value would be on the left and the array on the right-hand side of the operator.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

<span data-ttu-id="2af84-285">Detta kan bli dyrt om listan är stor.</span><span class="sxs-lookup"><span data-stu-id="2af84-285">This can get expensive if the list is large.</span></span> <span data-ttu-id="2af84-286">Jag använder ofta ett regex-mönster om jag söker efter fler än några värden.</span><span class="sxs-lookup"><span data-stu-id="2af84-286">I often use a regex pattern if I'm checking more than a few values.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a><span data-ttu-id="2af84-287">-EQ och-Ne</span><span class="sxs-lookup"><span data-stu-id="2af84-287">-eq and -ne</span></span>

<span data-ttu-id="2af84-288">Likheter och matriser kan bli komplicerade.</span><span class="sxs-lookup"><span data-stu-id="2af84-288">Equality and arrays can get complicated.</span></span> <span data-ttu-id="2af84-289">När matrisen är på vänster sida jämförs varje objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-289">When the array is on the left side, every item gets compared.</span></span> <span data-ttu-id="2af84-290">I stället för att returnera returneras `True` det objekt som matchar.</span><span class="sxs-lookup"><span data-stu-id="2af84-290">Instead of returning `True`, it returns the object that matches.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

<span data-ttu-id="2af84-291">När du använder `-ne` operatorn får vi alla värden som inte är lika med vårt värde.</span><span class="sxs-lookup"><span data-stu-id="2af84-291">When you use the `-ne` operator, we get all the values that are not equal to our value.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

<span data-ttu-id="2af84-292">När du använder det här i en `if()` instruktion är ett värde som returneras ett `True` värde.</span><span class="sxs-lookup"><span data-stu-id="2af84-292">When you use this in an `if()` statement, a value that is returned is a `True` value.</span></span> <span data-ttu-id="2af84-293">Om inget värde returneras är det ett `False` värde.</span><span class="sxs-lookup"><span data-stu-id="2af84-293">If no value is returned, then it's a `False` value.</span></span> <span data-ttu-id="2af84-294">Båda dessa Next-instruktioner utvärderas till `True` .</span><span class="sxs-lookup"><span data-stu-id="2af84-294">Both of these next statements evaluate to `True`.</span></span>

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

<span data-ttu-id="2af84-295">Jag går tillbaka så snart vi pratar om testningen av `$null` .</span><span class="sxs-lookup"><span data-stu-id="2af84-295">I'll revisit this in a moment when we talk about testing for `$null`.</span></span>

### <a name="-match"></a><span data-ttu-id="2af84-296">-matcha</span><span class="sxs-lookup"><span data-stu-id="2af84-296">-match</span></span>

<span data-ttu-id="2af84-297">`-match`Operatorn försöker matcha varje objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2af84-297">The `-match` operator tries to match each item in the collection.</span></span>

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

<span data-ttu-id="2af84-298">När du använder `-match` med ett enda värde fylls en speciell variabel `$Matches` med matchnings information.</span><span class="sxs-lookup"><span data-stu-id="2af84-298">When you use `-match` with a single value, a special variable `$Matches` gets populated with match info.</span></span> <span data-ttu-id="2af84-299">Detta är inte fallet när en matris behandlas på det här sättet.</span><span class="sxs-lookup"><span data-stu-id="2af84-299">This isn't the case when an array is processed this way.</span></span>

<span data-ttu-id="2af84-300">Vi kan utföra samma tillvägagångs sätt med `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="2af84-300">We can take the same approach with `Select-String`.</span></span>

```powershell
$servers | Select-String SQL
```

<span data-ttu-id="2af84-301">Jag tar en närmare titt på `Select-String` , `-match` och `$matches` variabeln i ett annat inlägg som kallas [för många sätt att använda regex][].</span><span class="sxs-lookup"><span data-stu-id="2af84-301">I take a closer look at `Select-String`,`-match` and the `$matches` variable in another post called [The many ways to use regex][].</span></span>

### <a name="null-or-empty"></a><span data-ttu-id="2af84-302">$null eller tomt</span><span class="sxs-lookup"><span data-stu-id="2af84-302">$null or empty</span></span>

<span data-ttu-id="2af84-303">`$null`Det kan vara svårt att testa för eller tomma matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-303">Testing for `$null` or empty arrays can be tricky.</span></span> <span data-ttu-id="2af84-304">Här är vanliga traps med matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-304">Here are the common traps with arrays.</span></span>

<span data-ttu-id="2af84-305">Den här instruktionen ser ut ungefär som den ska fungera.</span><span class="sxs-lookup"><span data-stu-id="2af84-305">At a glance, this statement looks like it should work.</span></span>

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

<span data-ttu-id="2af84-306">Men jag gick bara igenom hur `-eq` kontrollerar varje objekt i matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-306">But I just went over how `-eq` checks each item in the array.</span></span> <span data-ttu-id="2af84-307">Vi kan därför ha en matris med flera objekt med ett enda $null värde och det skulle utvärderas till `$true`</span><span class="sxs-lookup"><span data-stu-id="2af84-307">So we can have an array of several items with a single $null value and it would evaluate to `$true`</span></span>

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

<span data-ttu-id="2af84-308">Det är därför det bästa sättet att placera `$null` på den vänstra sidan av operatören.</span><span class="sxs-lookup"><span data-stu-id="2af84-308">This is why it's a best practice to place the `$null` on the left side of the operator.</span></span> <span data-ttu-id="2af84-309">Detta gör att det här scenariot inte är ett problem.</span><span class="sxs-lookup"><span data-stu-id="2af84-309">This makes this scenario a non-issue.</span></span>

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

<span data-ttu-id="2af84-310">En `$null` matris är inte samma sak som en tom matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-310">A `$null` array isn't the same thing as an empty array.</span></span> <span data-ttu-id="2af84-311">Om du vet att du har en matris kontrollerar du antalet objekt i den.</span><span class="sxs-lookup"><span data-stu-id="2af84-311">If you know you have an array, check the count of objects in it.</span></span> <span data-ttu-id="2af84-312">Om matrisen är är `$null` antalet `0` .</span><span class="sxs-lookup"><span data-stu-id="2af84-312">If the array is `$null`, the count is `0`.</span></span>

```powershell
if ( $array.count -gt 0 )
{
    "Array isn't empty"
}
```

<span data-ttu-id="2af84-313">Det finns ytterligare en svällning att titta närmare på.</span><span class="sxs-lookup"><span data-stu-id="2af84-313">There is one more trap to watch out for here.</span></span> <span data-ttu-id="2af84-314">Du kan använda `count` även om du har ett enda objekt, om inte objektet är ett `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="2af84-314">You can use the `count` even if you have a single object, unless that object is a `PSCustomObject`.</span></span> <span data-ttu-id="2af84-315">Detta är ett fel som korrigeras i PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="2af84-315">This is a bug that is fixed in PowerShell 6.1.</span></span>
<span data-ttu-id="2af84-316">Det är goda nyheter, men många människor är kvar på 5,1 och behöver titta på det.</span><span class="sxs-lookup"><span data-stu-id="2af84-316">That's good news, but a lot of people are still on 5.1 and need to watch out for it.</span></span>

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

<span data-ttu-id="2af84-317">Om du fortfarande använder PowerShell 5,1 kan du figursätta objektet i en matris innan du kontrollerar antalet för att få ett korrekt antal.</span><span class="sxs-lookup"><span data-stu-id="2af84-317">If you're still on PowerShell 5.1, you can wrap the object in an array before checking the count to get an accurate count.</span></span>

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

<span data-ttu-id="2af84-318">Kontrol lera och kontrol lera antalet för att kunna spela upp det säkert `$null` .</span><span class="sxs-lookup"><span data-stu-id="2af84-318">To fully play it safe, check for `$null`, then check the count.</span></span>

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a><span data-ttu-id="2af84-319">Alla-EQ</span><span class="sxs-lookup"><span data-stu-id="2af84-319">All -eq</span></span>

<span data-ttu-id="2af84-320">Jag såg nyligen någon fråga om att [kontrol lera att varje värde i en matris matchar ett angivet värde][].</span><span class="sxs-lookup"><span data-stu-id="2af84-320">I recently saw someone ask [how to verify that every value in an array matches a given value][].</span></span>
<span data-ttu-id="2af84-321">Reddit User **/u/BIS** hade denna smarta- [lösning][] som söker efter felaktiga värden och vänder sedan resultatet.</span><span class="sxs-lookup"><span data-stu-id="2af84-321">Reddit user **/u/bis** had this clever [solution][] that checks for any incorrect values and then flips the result.</span></span>

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a><span data-ttu-id="2af84-322">Lägga till i matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-322">Adding to arrays</span></span>

<span data-ttu-id="2af84-323">Nu börjar du med att undrar hur du lägger till objekt i en matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-323">At this point, you're starting to wonder how to add items to an array.</span></span> <span data-ttu-id="2af84-324">Det snabba svaret är att du inte kan.</span><span class="sxs-lookup"><span data-stu-id="2af84-324">The quick answer is that you can't.</span></span> <span data-ttu-id="2af84-325">En matris är en fast storlek i minnet.</span><span class="sxs-lookup"><span data-stu-id="2af84-325">An array is a fixed size in memory.</span></span> <span data-ttu-id="2af84-326">Om du behöver utöka den eller lägga till ett enda objekt i det måste du skapa en ny matris och kopiera alla värden från den gamla matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-326">If you need to grow it or add a single item to it, then you need to create a new array and copy all the values over from the old array.</span></span> <span data-ttu-id="2af84-327">Detta låter till exempel mycket arbete, men PowerShell döljer komplexiteten vid skapandet av den nya matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-327">This sounds like a lot of work, however, PowerShell hides the complexity of creating the new array.</span></span> <span data-ttu-id="2af84-328">I PowerShell implementeras additionsoperatorn ( `+` ) för matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-328">PowerShell implements the addition operator (`+`) for arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="2af84-329">PowerShell implementerar inte en subtraktion-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="2af84-329">PowerShell does not implement a subtraction operation.</span></span> <span data-ttu-id="2af84-330">Om du vill ha ett flexibelt alternativ till en matris måste du använda ett [generiskt `List` ](#generic-list) objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-330">If you want a flexible alternative to an array, you need to use a [generic `List`](#generic-list) object.</span></span>

### <a name="array-addition"></a><span data-ttu-id="2af84-331">Mat ris tillägg</span><span class="sxs-lookup"><span data-stu-id="2af84-331">Array addition</span></span>

<span data-ttu-id="2af84-332">Vi kan använda operatorn addition med arrayer för att skapa en ny matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-332">We can use the addition operator with arrays to create a new array.</span></span> <span data-ttu-id="2af84-333">Vi har fått dessa två matriser:</span><span class="sxs-lookup"><span data-stu-id="2af84-333">So given these two arrays:</span></span>

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

<span data-ttu-id="2af84-334">Vi kan lägga till dem tillsammans för att få en ny matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-334">We can add them together to get a new array.</span></span>

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a><span data-ttu-id="2af84-335">Plus lika med + =</span><span class="sxs-lookup"><span data-stu-id="2af84-335">Plus equals +=</span></span>

<span data-ttu-id="2af84-336">Vi kan skapa en ny matris på plats och lägga till ett objekt i den så här:</span><span class="sxs-lookup"><span data-stu-id="2af84-336">We can create a new array in place and add an item to it like this:</span></span>

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

<span data-ttu-id="2af84-337">Kom bara ihåg att varje gång du använder `+=` som du duplicerar och skapar en ny matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-337">Just remember that every time you use `+=` that you're duplicating and creating a new array.</span></span> <span data-ttu-id="2af84-338">Detta är inte ett problem för små data uppsättningar, men det skalas extremt dåligt.</span><span class="sxs-lookup"><span data-stu-id="2af84-338">This is a not an issue for small datasets but it scales extremely poorly.</span></span>

### <a name="pipeline-assignment"></a><span data-ttu-id="2af84-339">Pipeline-tilldelning</span><span class="sxs-lookup"><span data-stu-id="2af84-339">Pipeline assignment</span></span>

<span data-ttu-id="2af84-340">Du kan tilldela resultatet av en pipeline till en variabel.</span><span class="sxs-lookup"><span data-stu-id="2af84-340">You can assign the results of any pipeline into a variable.</span></span> <span data-ttu-id="2af84-341">Det är en matris om den innehåller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-341">It's an array if it contains multiple items.</span></span>

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

<span data-ttu-id="2af84-342">Normalt när vi tänker på att använda pipelinen kommer vi att tänka på en typisk PowerShell-liners.</span><span class="sxs-lookup"><span data-stu-id="2af84-342">Normally when we think of using the pipeline, we think of the typical PowerShell one-liners.</span></span> <span data-ttu-id="2af84-343">Vi kan utnyttja pipelinen med `foreach()` instruktioner och andra slingor.</span><span class="sxs-lookup"><span data-stu-id="2af84-343">We can leverage the pipeline with `foreach()` statements and other loops.</span></span> <span data-ttu-id="2af84-344">I stället för att lägga till objekt i en matris i en slinga kan vi släppa objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2af84-344">So instead of adding items to an array in a loop, we can drop items onto the pipeline.</span></span>

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

## <a name="array-types"></a><span data-ttu-id="2af84-345">Mat ris typer</span><span class="sxs-lookup"><span data-stu-id="2af84-345">Array Types</span></span>

<span data-ttu-id="2af84-346">Som standard skapas en matris i PowerShell som en `[PSObject[]]` typ.</span><span class="sxs-lookup"><span data-stu-id="2af84-346">By default, an array in PowerShell is created as a `[PSObject[]]` type.</span></span> <span data-ttu-id="2af84-347">Detta gör att den kan innehålla alla typer av objekt eller värden.</span><span class="sxs-lookup"><span data-stu-id="2af84-347">This allows it to contain any type of object or value.</span></span> <span data-ttu-id="2af84-348">Detta fungerar eftersom allt ärvs från `PSObject` typen.</span><span class="sxs-lookup"><span data-stu-id="2af84-348">This works because everything is inherited from the `PSObject` type.</span></span>

### <a name="strongly-typed-arrays"></a><span data-ttu-id="2af84-349">Starkt skrivna matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-349">Strongly typed arrays</span></span>

<span data-ttu-id="2af84-350">Du kan skapa en matris av vilken typ som helst med hjälp av samma syntax.</span><span class="sxs-lookup"><span data-stu-id="2af84-350">You can create an array of any type using a similar syntax.</span></span> <span data-ttu-id="2af84-351">När du skapar en starkt angiven matris får den bara innehålla värden eller objekt av den angivna typen.</span><span class="sxs-lookup"><span data-stu-id="2af84-351">When you create a strongly typed array, it can only contain values or objects the specified type.</span></span>

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a><span data-ttu-id="2af84-352">ArrayList</span><span class="sxs-lookup"><span data-stu-id="2af84-352">ArrayList</span></span>

<span data-ttu-id="2af84-353">Att lägga till objekt i en matris är en av dess största begränsningar, men det finns några andra samlingar som vi kan göra för att lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="2af84-353">Adding items to an array is one of its biggest limitations, but there are a few other collections that we can turn to that solve this problem.</span></span>

<span data-ttu-id="2af84-354">`ArrayList`Är vanligt vis ett av de första saker som vi tänker på när vi behöver en matris som är snabbare att arbeta med.</span><span class="sxs-lookup"><span data-stu-id="2af84-354">The `ArrayList` is commonly one of the first things that we think of when we need an array that is faster to work with.</span></span> <span data-ttu-id="2af84-355">Den fungerar som en objekt mat ris varje plats som vi behöver det, men det hanterar snabbt tillägg av objekt.</span><span class="sxs-lookup"><span data-stu-id="2af84-355">It acts like an object array every place that we need it, but it handles adding items quickly.</span></span>

<span data-ttu-id="2af84-356">Så här skapar vi en `ArrayList` och lägger till objekt i den.</span><span class="sxs-lookup"><span data-stu-id="2af84-356">Here is how we create an `ArrayList` and add items to it.</span></span>

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

<span data-ttu-id="2af84-357">Vi ringer till .NET för att få den här typen.</span><span class="sxs-lookup"><span data-stu-id="2af84-357">We are calling into .NET to get this type.</span></span> <span data-ttu-id="2af84-358">I det här fallet använder vi Standardkonstruktorn för att skapa den.</span><span class="sxs-lookup"><span data-stu-id="2af84-358">In this case, we are using the default constructor to create it.</span></span> <span data-ttu-id="2af84-359">Sedan anropar vi `Add` metoden för att lägga till ett objekt i det.</span><span class="sxs-lookup"><span data-stu-id="2af84-359">Then we call the `Add` method to add an item to it.</span></span>

<span data-ttu-id="2af84-360">Anledningen till att jag använder `[void]` i början av raden är att utelämna retur koden.</span><span class="sxs-lookup"><span data-stu-id="2af84-360">The reason I'm using `[void]` at the beginning of the line is to suppress the return code.</span></span> <span data-ttu-id="2af84-361">Vissa .NET-anrop gör detta och kan skapa oväntade utdata.</span><span class="sxs-lookup"><span data-stu-id="2af84-361">Some .NET calls do this and can create unexpected output.</span></span>

<span data-ttu-id="2af84-362">Om de enda data som du har i matrisen är strängar, tar du också en titt på att använda [StringBuilder][].</span><span class="sxs-lookup"><span data-stu-id="2af84-362">If the only data that you have in your array is strings, then also take a look at using [StringBuilder][].</span></span> <span data-ttu-id="2af84-363">Det är nästan samma sak men har några metoder som bara är för att hantera strängar.</span><span class="sxs-lookup"><span data-stu-id="2af84-363">It's almost the same thing but has some methods that are just for dealing with strings.</span></span> <span data-ttu-id="2af84-364">`StringBuilder`Är särskilt utformad för prestanda.</span><span class="sxs-lookup"><span data-stu-id="2af84-364">The `StringBuilder` is specially designed for performance.</span></span>

<span data-ttu-id="2af84-365">Det är vanligt att du ser att personer flyttas till `ArrayList` från matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-365">It's common to see people move to `ArrayList` from arrays.</span></span> <span data-ttu-id="2af84-366">Men det kommer från en tid där C# inte hade generisk support.</span><span class="sxs-lookup"><span data-stu-id="2af84-366">But it comes from a time where C# didn't have generic support.</span></span> <span data-ttu-id="2af84-367">`ArrayList`Är föråldrad i stöd för den generiska`List[]`</span><span class="sxs-lookup"><span data-stu-id="2af84-367">The `ArrayList` is deprecated in support for the generic `List[]`</span></span>

### <a name="generic-list"></a><span data-ttu-id="2af84-368">Allmän lista</span><span class="sxs-lookup"><span data-stu-id="2af84-368">Generic List</span></span>

<span data-ttu-id="2af84-369">En generisk typ är en särskild typ i C# som definierar en generaliserad klass och användaren anger de data typer som används när den skapas.</span><span class="sxs-lookup"><span data-stu-id="2af84-369">A generic type is a special type in C# that defines a generalized class and the user specifies the data types it uses when created.</span></span> <span data-ttu-id="2af84-370">Så om du vill ha en lista med tal eller strängar definierar du att du vill ha en lista över `int` eller `string` typer.</span><span class="sxs-lookup"><span data-stu-id="2af84-370">So if you want a list of numbers or strings, you would define that you want list of `int` or `string` types.</span></span>

<span data-ttu-id="2af84-371">Så här skapar du en lista med strängar.</span><span class="sxs-lookup"><span data-stu-id="2af84-371">Here is how you create a List for strings.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

<span data-ttu-id="2af84-372">Eller en lista med tal.</span><span class="sxs-lookup"><span data-stu-id="2af84-372">Or a list for numbers.</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

<span data-ttu-id="2af84-373">Vi kan omvandla en befintlig matris till en lista som detta utan att först skapa objektet:</span><span class="sxs-lookup"><span data-stu-id="2af84-373">We can cast an existing array to a list like this without creating the object first:</span></span>

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

<span data-ttu-id="2af84-374">Vi kan förkorta syntaxen med `using namespace` instruktionen i PowerShell 5 och senare.</span><span class="sxs-lookup"><span data-stu-id="2af84-374">We can shorten the syntax with the `using namespace` statement in PowerShell 5 and newer.</span></span> <span data-ttu-id="2af84-375">`using`Instruktionen måste vara den första raden i skriptet.</span><span class="sxs-lookup"><span data-stu-id="2af84-375">The `using` statement needs to be the first line of your script.</span></span> <span data-ttu-id="2af84-376">Genom att deklarera ett namn område kan du använda PowerShell för att lämna det av data typerna när du refererar till dem.</span><span class="sxs-lookup"><span data-stu-id="2af84-376">By declaring a namespace, PowerShell lets you leave it off of the data types when you reference them.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

<span data-ttu-id="2af84-377">Detta gör det `List` mycket mer användbart.</span><span class="sxs-lookup"><span data-stu-id="2af84-377">This makes the `List` much more usable.</span></span>

<span data-ttu-id="2af84-378">Du har en liknande `Add` metod som är tillgänglig för dig.</span><span class="sxs-lookup"><span data-stu-id="2af84-378">You have a similar `Add` method available to you.</span></span> <span data-ttu-id="2af84-379">Till skillnad från ArrayList finns det inget retur värde för metoden, `Add` så vi behöver inte göra `void` det.</span><span class="sxs-lookup"><span data-stu-id="2af84-379">Unlike the ArrayList, there is no return value on the `Add` method so we don't have to `void` it.</span></span>

```powershell
$myList.Add(10)
```

<span data-ttu-id="2af84-380">Och vi har fortfarande åtkomst till elementen som andra matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-380">And we can still access the elements like other arrays.</span></span>

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a><span data-ttu-id="2af84-381">Lista [PSObject]</span><span class="sxs-lookup"><span data-stu-id="2af84-381">List[PSObject]</span></span>

<span data-ttu-id="2af84-382">Du kan ha en lista över vilken typ som helst, men när du inte vet vilken typ av objekt du kan använda `[List[PSObject]]` för att ta med dem.</span><span class="sxs-lookup"><span data-stu-id="2af84-382">You can have a list of any type, but when you don't know the type of objects, you can use `[List[PSObject]]` to contain them.</span></span>

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a><span data-ttu-id="2af84-383">Remove()</span><span class="sxs-lookup"><span data-stu-id="2af84-383">Remove()</span></span>

<span data-ttu-id="2af84-384">`ArrayList`Och generiskt `List[]` stöder borttagning av objekt från samlingen.</span><span class="sxs-lookup"><span data-stu-id="2af84-384">The `ArrayList` and the generic `List[]` both support removing items from the collection.</span></span>

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

<span data-ttu-id="2af84-385">När du arbetar med värde typer tar den bort det första från listan.</span><span class="sxs-lookup"><span data-stu-id="2af84-385">When working with value types, it removes the first one from the list.</span></span> <span data-ttu-id="2af84-386">Du kan anropa det igen om du vill fortsätta att ta bort värdet.</span><span class="sxs-lookup"><span data-stu-id="2af84-386">You can call it over and over again to keep removing that value.</span></span> <span data-ttu-id="2af84-387">Om du har referens typer måste du ange det objekt som du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="2af84-387">If you have reference types, you have to provide the object that you want removed.</span></span>

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

<span data-ttu-id="2af84-388">Metoden Remove returnerar `true` om den kunde hitta och ta bort objektet från samlingen.</span><span class="sxs-lookup"><span data-stu-id="2af84-388">The remove method returns `true` if it was able to find and remove the item from the collection.</span></span>

### <a name="more-collections"></a><span data-ttu-id="2af84-389">Fler samlingar</span><span class="sxs-lookup"><span data-stu-id="2af84-389">More collections</span></span>

<span data-ttu-id="2af84-390">Det finns många andra samlingar som kan användas, men de är bra generiska matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-390">There are many other collections that can be used but these are the good generic array replacements.</span></span>
<span data-ttu-id="2af84-391">Om du är intresse rad av att lära dig mer av de här alternativen kan du ta en titt på det här [registret](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) som [markerar Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) .</span><span class="sxs-lookup"><span data-stu-id="2af84-391">If you're interested in learning about more of these options, take a look at this [Gist](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) that [Mark Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) put together.</span></span>

## <a name="other-nuances"></a><span data-ttu-id="2af84-392">Andra olika delarna</span><span class="sxs-lookup"><span data-stu-id="2af84-392">Other nuances</span></span>

<span data-ttu-id="2af84-393">Nu när jag har täckt alla större funktioner finns här några saker som jag ville nämna innan jag omsluter detta.</span><span class="sxs-lookup"><span data-stu-id="2af84-393">Now that I have covered all the major functionality, here are a few more things that I wanted to mention before I wrap this up.</span></span>

### <a name="pre-sized-arrays"></a><span data-ttu-id="2af84-394">I storleks mat ris</span><span class="sxs-lookup"><span data-stu-id="2af84-394">Pre-sized arrays</span></span>

<span data-ttu-id="2af84-395">Jag nämnde att du inte kan ändra storleken på en matris när den har skapats.</span><span class="sxs-lookup"><span data-stu-id="2af84-395">I mentioned that you can't change the size of an array once it's created.</span></span> <span data-ttu-id="2af84-396">Vi kan skapa en matris med en fördefinierad storlek genom att anropa den med `new($size)` konstruktorn.</span><span class="sxs-lookup"><span data-stu-id="2af84-396">We can create an array of a pre-determined size by calling it with the `new($size)` constructor.</span></span>

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a><span data-ttu-id="2af84-397">Multiplicerar matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-397">Multiplying arrays</span></span>

<span data-ttu-id="2af84-398">Ett intressant litet stick är att du kan multiplicera en matris med ett heltal.</span><span class="sxs-lookup"><span data-stu-id="2af84-398">An interesting little trick is that you can multiply an array by an integer.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a><span data-ttu-id="2af84-399">Initiera med 0</span><span class="sxs-lookup"><span data-stu-id="2af84-399">Initialize with 0</span></span>

<span data-ttu-id="2af84-400">Ett vanligt scenario är att du vill skapa en matris med enbart nollor.</span><span class="sxs-lookup"><span data-stu-id="2af84-400">A common scenario is that you want to create an array with all zeros.</span></span> <span data-ttu-id="2af84-401">Om du bara kommer att använda heltal, är en stark inskriven matris med heltal som standard alla nollor.</span><span class="sxs-lookup"><span data-stu-id="2af84-401">If you're only going to have integers, a strongly typed array of integers defaults to all zeros.</span></span>

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

<span data-ttu-id="2af84-402">Vi kan även använda det multipliceringa sticket för att göra detta.</span><span class="sxs-lookup"><span data-stu-id="2af84-402">We can use the multiplying trick to do this too.</span></span>

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

<span data-ttu-id="2af84-403">Det som är trevligt om att multiplicera sticket är att du kan använda vilket värde som helst.</span><span class="sxs-lookup"><span data-stu-id="2af84-403">The nice thing about the multiplying trick is that you can use any value.</span></span> <span data-ttu-id="2af84-404">Så om du hellre vill ha det `255` som standardvärde, är det ett bra sätt att göra det.</span><span class="sxs-lookup"><span data-stu-id="2af84-404">So if you would rather have `255` as your default value, this would be a good way to do it.</span></span>

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a><span data-ttu-id="2af84-405">Kapslade matriser</span><span class="sxs-lookup"><span data-stu-id="2af84-405">Nested arrays</span></span>

<span data-ttu-id="2af84-406">En matris i en matris kallas för en kapslad matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-406">An array inside an array is called a nested array.</span></span> <span data-ttu-id="2af84-407">Jag använder inte dessa mycket i PowerShell men jag har använt dem på andra språk.</span><span class="sxs-lookup"><span data-stu-id="2af84-407">I don't use these much in PowerShell but I have used them more in other languages.</span></span> <span data-ttu-id="2af84-408">Överväg att använda en matris med matriser när dina data passar i ett rutnät som mönster.</span><span class="sxs-lookup"><span data-stu-id="2af84-408">Consider using an array of arrays when your data fits in a grid like pattern.</span></span>

<span data-ttu-id="2af84-409">Här följer två sätt att skapa en tvådimensionell matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-409">Here are two ways we can create a two-dimensional array.</span></span>

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

<span data-ttu-id="2af84-410">Kommatecknet är mycket viktigt i de här exemplen.</span><span class="sxs-lookup"><span data-stu-id="2af84-410">The comma is very important in those examples.</span></span> <span data-ttu-id="2af84-411">Jag fick ett tidigare exempel på en normal matris på flera rader där kommatecknet var valfritt.</span><span class="sxs-lookup"><span data-stu-id="2af84-411">I gave an earlier example of a normal array on multiple lines where the comma was optional.</span></span> <span data-ttu-id="2af84-412">Det är inte fallet med en flerdimensionell matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-412">That isn't the case with a multi-dimensional array.</span></span>

<span data-ttu-id="2af84-413">Hur vi använder index notation ändras en aning nu när vi har en kapslad matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-413">The way we use the index notation changes slightly now that we've a nested array.</span></span> <span data-ttu-id="2af84-414">Vi använder `$data` ovanstående för att få åtkomst till värdet 3.</span><span class="sxs-lookup"><span data-stu-id="2af84-414">Using the `$data` above, this is how we would access the value 3.</span></span>

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

<span data-ttu-id="2af84-415">Lägg till en uppsättning hakparenteser för varje nivå av mat ris kapsling.</span><span class="sxs-lookup"><span data-stu-id="2af84-415">Add a set of bracket for each level of array nesting.</span></span> <span data-ttu-id="2af84-416">Den första uppsättningen hakparenteser är för den yttre mest matrisen och sedan arbetar du på ditt sätt i därifrån.</span><span class="sxs-lookup"><span data-stu-id="2af84-416">The first set of brackets is for the outer most array and then you work your way in from there.</span></span>

### <a name="write-output--noenumerate"></a><span data-ttu-id="2af84-417">Write-output-noenumeration</span><span class="sxs-lookup"><span data-stu-id="2af84-417">Write-Output -NoEnumerate</span></span>

<span data-ttu-id="2af84-418">PowerShell gillar att packa upp eller räkna upp matriser.</span><span class="sxs-lookup"><span data-stu-id="2af84-418">PowerShell likes to unwrap or enumerate arrays.</span></span> <span data-ttu-id="2af84-419">Detta är en grund aspekt av hur PowerShell använder pipelinen, men det finns tillfällen då du inte vill att det ska hända.</span><span class="sxs-lookup"><span data-stu-id="2af84-419">This is a core aspect of the way PowerShell uses the pipeline but there are times that you don't want that to happen.</span></span>

<span data-ttu-id="2af84-420">Jag rör ofta objekt till `Get-Member` för att lära sig mer om dem.</span><span class="sxs-lookup"><span data-stu-id="2af84-420">I commonly pipe objects to `Get-Member` to learn more about them.</span></span> <span data-ttu-id="2af84-421">När jag rör en matris till den, kommer den att bli figursatt och Get-Member ser medlemmarna i matrisen och inte själva matrisen.</span><span class="sxs-lookup"><span data-stu-id="2af84-421">When I pipe an array to it, it gets unwrapped and Get-Member sees the members of the array and not the actual array.</span></span>

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

<span data-ttu-id="2af84-422">Du kan använda för att förhindra att matrisen bryts av `Write-Object -NoEnumerate` .</span><span class="sxs-lookup"><span data-stu-id="2af84-422">To prevent that unwrap of the array, you can use `Write-Object -NoEnumerate`.</span></span>

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

<span data-ttu-id="2af84-423">Jag har ett andra sätt som är mer av ett Hack (och jag försöker undvika hackningar som detta).</span><span class="sxs-lookup"><span data-stu-id="2af84-423">I have a second way that's more of a hack (and I try to avoid hacks like this).</span></span> <span data-ttu-id="2af84-424">Du kan placera ett kommatecken framför matrisen innan du rör det.</span><span class="sxs-lookup"><span data-stu-id="2af84-424">You can place a comma in front of the array before you pipe it.</span></span>

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a><span data-ttu-id="2af84-425">Returnera en matris</span><span class="sxs-lookup"><span data-stu-id="2af84-425">Return an array</span></span>

<span data-ttu-id="2af84-426">Den här omplaceringen av matriser sker också när du matar ut eller returnerar värden från en funktion.</span><span class="sxs-lookup"><span data-stu-id="2af84-426">This unwrapping of arrays also happens when you output or return values from a function.</span></span> <span data-ttu-id="2af84-427">Du kan fortfarande hämta en matris om du tilldelar utdata till en variabel, så det är inte ofta ett problem.</span><span class="sxs-lookup"><span data-stu-id="2af84-427">You can still get an array if you assign the output to a variable so this isn't commonly an issue.</span></span>

<span data-ttu-id="2af84-428">Fångsten är att du har en ny matris.</span><span class="sxs-lookup"><span data-stu-id="2af84-428">The catch is that you have a new array.</span></span> <span data-ttu-id="2af84-429">Om det skulle uppstå ett problem kan du använda `Write-Output -NoEnumerate $array` eller `return ,$array` för att undvika det.</span><span class="sxs-lookup"><span data-stu-id="2af84-429">If that is ever a problem, you can use `Write-Output -NoEnumerate $array` or `return ,$array` to work around it.</span></span>

## <a name="anything-else"></a><span data-ttu-id="2af84-430">Något mer?</span><span class="sxs-lookup"><span data-stu-id="2af84-430">Anything else?</span></span>

<span data-ttu-id="2af84-431">Jag vet att det är allt du behöver göra i.</span><span class="sxs-lookup"><span data-stu-id="2af84-431">I know this is all a lot to take in.</span></span> <span data-ttu-id="2af84-432">Min idé är att du lär dig något från den här artikeln varje gång du läser det och att det blir en lämplig referens till dig under lång tid att komma.</span><span class="sxs-lookup"><span data-stu-id="2af84-432">My hope is that you learn something from this article every time you read it and that it turns out to be a good reference for you for a long time to come.</span></span> <span data-ttu-id="2af84-433">Om du har hittat detta för att vara till hjälp kan du dela den med andra som du tror kan få ett värde av det.</span><span class="sxs-lookup"><span data-stu-id="2af84-433">If you found this to be helpful, please share it with others you think may get value out of it.</span></span>

<span data-ttu-id="2af84-434">Härifrån rekommenderar vi att du tar en titt på ett liknande inlägg som jag skrev om [hash][].</span><span class="sxs-lookup"><span data-stu-id="2af84-434">From here, I would recommend you check out a similar post that I wrote about [hashtables][].</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Matriser]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Switch-instruktion]: everything-about-switch.md
[switch statement]: everything-about-switch.md
[hash]: everything-about-hashtable.md
[hashtables]: everything-about-hashtable.md
[Många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[The many ways to use regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[så här kontrollerar du att varje värde i en matris matchar ett angivet värde]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[how to verify that every value in an array matches a given value]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[lösa]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[solution]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
