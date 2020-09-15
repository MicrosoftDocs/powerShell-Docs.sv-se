---
title: Allt du ville veta mer om $null
description: PowerShell-$null verkar ofta vara enkelt men det har många olika delarna. Låt oss ta en närmare titt på $null så att du vet vad som händer när du plötsligt kör ett null-värde.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2020
ms.locfileid: "84149833"
---
# <a name="everything-you-wanted-to-know-about-null"></a><span data-ttu-id="eecad-104">Allt du ville veta mer om $null</span><span class="sxs-lookup"><span data-stu-id="eecad-104">Everything you wanted to know about $null</span></span>

<span data-ttu-id="eecad-105">PowerShell `$null` verkar ofta vara enkelt men det har många olika delarna.</span><span class="sxs-lookup"><span data-stu-id="eecad-105">The PowerShell `$null` often appears to be simple but it has a lot of nuances.</span></span> <span data-ttu-id="eecad-106">Låt oss ta en närmare titt på `$null` så att du vet vad som händer när du har råkat ut för ett `$null` värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-106">Let's take a close look at `$null` so you know what happens when you unexpectedly run into a `$null` value.</span></span>

> [!NOTE]
> <span data-ttu-id="eecad-107">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="eecad-107">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="eecad-108">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="eecad-108">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="eecad-109">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="eecad-109">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="what-is-null"></a><span data-ttu-id="eecad-110">Vad är NULL?</span><span class="sxs-lookup"><span data-stu-id="eecad-110">What is NULL?</span></span>

<span data-ttu-id="eecad-111">Du kan tänka på NULL som ett okänt eller tomt värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-111">You can think of NULL as an unknown or empty value.</span></span> <span data-ttu-id="eecad-112">En variabel är NULL tills du tilldelar ett värde eller ett objekt till det.</span><span class="sxs-lookup"><span data-stu-id="eecad-112">A variable is NULL until you assign a value or an object to it.</span></span> <span data-ttu-id="eecad-113">Detta kan vara viktigt eftersom det finns vissa kommandon som kräver ett värde och genererar fel om värdet är NULL.</span><span class="sxs-lookup"><span data-stu-id="eecad-113">This can be important because there are some commands that require a value and generate errors if the value is NULL.</span></span>

### <a name="powershell-null"></a><span data-ttu-id="eecad-114">PowerShell-$null</span><span class="sxs-lookup"><span data-stu-id="eecad-114">PowerShell $null</span></span>

<span data-ttu-id="eecad-115">`$null` är en automatisk variabel i PowerShell som används för att representera NULL.</span><span class="sxs-lookup"><span data-stu-id="eecad-115">`$null` is an automatic variable in PowerShell used to represent NULL.</span></span> <span data-ttu-id="eecad-116">Du kan tilldela den till variabler, använda den i jämförelser och använda den som plats hållare för NULL i en samling.</span><span class="sxs-lookup"><span data-stu-id="eecad-116">You can assign it to variables, use it in comparisons and use it as a place holder for NULL in a collection.</span></span>

<span data-ttu-id="eecad-117">PowerShell behandlar `$null` som ett objekt med värdet null.</span><span class="sxs-lookup"><span data-stu-id="eecad-117">PowerShell treats `$null` as an object with a value of NULL.</span></span> <span data-ttu-id="eecad-118">Detta skiljer sig från vad du kan förväntar dig om du kommer från ett annat språk.</span><span class="sxs-lookup"><span data-stu-id="eecad-118">This is different than what you may expect if you come from another language.</span></span>

## <a name="examples-of-null"></a><span data-ttu-id="eecad-119">Exempel på $null</span><span class="sxs-lookup"><span data-stu-id="eecad-119">Examples of $null</span></span>

<span data-ttu-id="eecad-120">När du försöker använda en variabel som du inte har initierat är värdet `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-120">Anytime you try to use a variable that you have not initialized, the value is `$null`.</span></span> <span data-ttu-id="eecad-121">Detta är ett av de vanligaste sätten att `$null` använda värden i koden.</span><span class="sxs-lookup"><span data-stu-id="eecad-121">This is one of the most common ways that `$null` values sneak into your code.</span></span>

```powershell
PS> $null -eq $undefinedVariable
True
```

<span data-ttu-id="eecad-122">Om du råkar skriva ett variabel namn, ser PowerShell det som en annan variabel och värdet är `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-122">If you happen to mistype a variable name then PowerShell sees it as a different variable and the value is `$null`.</span></span>

<span data-ttu-id="eecad-123">Det andra sättet att hitta `$null` värden är när de kommer från andra kommandon som inte ger dig några resultat.</span><span class="sxs-lookup"><span data-stu-id="eecad-123">The other way you find `$null` values is when they come from other commands that don't give you any results.</span></span>

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a><span data-ttu-id="eecad-124">Effekt av $null</span><span class="sxs-lookup"><span data-stu-id="eecad-124">Impact of $null</span></span>

<span data-ttu-id="eecad-125">`$null` värdena påverkar koden på olika sätt beroende på var de visas.</span><span class="sxs-lookup"><span data-stu-id="eecad-125">`$null` values impact your code differently depending on where they show up.</span></span>

### <a name="in-strings"></a><span data-ttu-id="eecad-126">I strängar</span><span class="sxs-lookup"><span data-stu-id="eecad-126">In strings</span></span>

<span data-ttu-id="eecad-127">Om du använder `$null` i en sträng är det ett tomt värde (eller en tom sträng).</span><span class="sxs-lookup"><span data-stu-id="eecad-127">If you use `$null` in a string, then it's a blank value (or empty string).</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

<span data-ttu-id="eecad-128">Detta är en av orsakerna till att jag vill placera hakparenteser runt variabler när de använder dem i logg meddelanden.</span><span class="sxs-lookup"><span data-stu-id="eecad-128">This is one of the reasons that I like to place brackets around variables when using them in log messages.</span></span> <span data-ttu-id="eecad-129">Det är ännu mer viktigt att identifiera kanterna på dina variabel värden när värdet är i slutet av strängen.</span><span class="sxs-lookup"><span data-stu-id="eecad-129">It's even more important to identify the edges of your variable values when the value is at the end of the string.</span></span>

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

<span data-ttu-id="eecad-130">Detta gör tomma strängar och `$null` värden enkla att upptäcka.</span><span class="sxs-lookup"><span data-stu-id="eecad-130">This makes empty strings and `$null` values easy to spot.</span></span>

### <a name="in-numeric-equation"></a><span data-ttu-id="eecad-131">I numerisk ekvation</span><span class="sxs-lookup"><span data-stu-id="eecad-131">In numeric equation</span></span>

<span data-ttu-id="eecad-132">När ett `$null` värde används i en numerisk ekvation är resultatet ogiltigt om det inte ger ett fel.</span><span class="sxs-lookup"><span data-stu-id="eecad-132">When a `$null` value is used in a numeric equation then your results are invalid if they don't give an error.</span></span> <span data-ttu-id="eecad-133">Ibland `$null` utvärderas `0` resultatet och andra gånger det blir hela resultatet `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-133">Sometimes the `$null` evaluates to `0` and other times it makes the whole result `$null`.</span></span>
<span data-ttu-id="eecad-134">Här är ett exempel med multiplikation som ger 0 eller `$null` beroende på ordningen för värdena.</span><span class="sxs-lookup"><span data-stu-id="eecad-134">Here is an example with multiplication that gives 0 or `$null` depending on the order of the values.</span></span>

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a><span data-ttu-id="eecad-135">I stället för en samling</span><span class="sxs-lookup"><span data-stu-id="eecad-135">In place of a collection</span></span>

<span data-ttu-id="eecad-136">Med en samling kan du använda ett index för att få åtkomst till värden.</span><span class="sxs-lookup"><span data-stu-id="eecad-136">A collection allow you use an index to access values.</span></span> <span data-ttu-id="eecad-137">Om du försöker indexera i en samling som faktiskt används `null` får du följande fel meddelande: `Cannot index into a null array` .</span><span class="sxs-lookup"><span data-stu-id="eecad-137">If you try to index into a collection that is actually `null`, you get this error: `Cannot index into a null array`.</span></span>

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

<span data-ttu-id="eecad-138">Om du har en samling men försöker komma åt ett element som inte finns i samlingen får du ett `$null` resultat.</span><span class="sxs-lookup"><span data-stu-id="eecad-138">If you have a collection but try to access an element that is not in the collection, you get a `$null` result.</span></span>

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a><span data-ttu-id="eecad-139">I stället för ett objekt</span><span class="sxs-lookup"><span data-stu-id="eecad-139">In place of an object</span></span>

<span data-ttu-id="eecad-140">Om du försöker komma åt en egenskap eller under egenskap för ett objekt som inte har den angivna egenskapen får du ett `$null` värde som du skulle göra för en odefinierad variabel.</span><span class="sxs-lookup"><span data-stu-id="eecad-140">If you try to access a property or sub property of an object that doesn't have the specified property, you get a `$null` value like you would for an undefined variable.</span></span> <span data-ttu-id="eecad-141">Det spelar ingen roll om variabeln är `$null` eller ett faktiskt objekt i det här fallet.</span><span class="sxs-lookup"><span data-stu-id="eecad-141">It doesn't matter if the variable is `$null` or an actual object in this case.</span></span>

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a><span data-ttu-id="eecad-142">Metod i ett null-värde-uttryck</span><span class="sxs-lookup"><span data-stu-id="eecad-142">Method on a null-valued expression</span></span>

<span data-ttu-id="eecad-143">Anropa en metod på ett `$null` objekt genererar en `RuntimeException` .</span><span class="sxs-lookup"><span data-stu-id="eecad-143">Calling a method on a `$null` object throws a `RuntimeException`.</span></span>

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

<span data-ttu-id="eecad-144">När jag ser frasen `You cannot call a method on a null-valued expression` är det första du letar efter platser där jag anropar en metod i en variabel utan att först kontrol lera den `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-144">Whenever I see the phrase `You cannot call a method on a null-valued expression` then the first thing I look for are places where I am calling a method on a variable without first checking it for `$null`.</span></span>

## <a name="checking-for-null"></a><span data-ttu-id="eecad-145">Söker efter $null</span><span class="sxs-lookup"><span data-stu-id="eecad-145">Checking for $null</span></span>

<span data-ttu-id="eecad-146">Du kanske har märkt att jag alltid placerar den till `$null` vänster när jag söker efter `$null` i mina exempel.</span><span class="sxs-lookup"><span data-stu-id="eecad-146">You may have noticed that I always place the `$null` on the left when checking for `$null` in my examples.</span></span> <span data-ttu-id="eecad-147">Detta är avsiktligt och accepterat som en PowerShell-metod.</span><span class="sxs-lookup"><span data-stu-id="eecad-147">This is intentional and accepted as a PowerShell best practice.</span></span> <span data-ttu-id="eecad-148">Det finns vissa scenarier där det inte ger det förväntade resultatet.</span><span class="sxs-lookup"><span data-stu-id="eecad-148">There are some scenarios where placing it on the right doesn't give you the expected result.</span></span>

<span data-ttu-id="eecad-149">Titta på följande exempel och försök att förutsäga resultaten:</span><span class="sxs-lookup"><span data-stu-id="eecad-149">Look at this next example and try to predict the results:</span></span>

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

<span data-ttu-id="eecad-150">Om jag inte definierar `$value` , kommer den första uppgiften att utvärderas till `$true` och vårt meddelande är `The array is $null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-150">If I do not define `$value`, the first one evaluates to `$true` and our message is `The array is $null`.</span></span> <span data-ttu-id="eecad-151">Trap här är att det är möjligt att skapa en `$value` som låter båda `$false`</span><span class="sxs-lookup"><span data-stu-id="eecad-151">The trap here is that it's possible to create a `$value` that allows both of them to be `$false`</span></span>

```powershell
$value = @( $null )
```

<span data-ttu-id="eecad-152">I det här fallet `$value` är en matris som innehåller en `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-152">In this case, the `$value` is an array that contains a `$null`.</span></span> <span data-ttu-id="eecad-153">`-eq`Kontrollerar varje värde i matrisen och returnerar det `$null` som matchar.</span><span class="sxs-lookup"><span data-stu-id="eecad-153">The `-eq` checks every value in the array and returns the `$null` that is matched.</span></span> <span data-ttu-id="eecad-154">Detta utvärderas till `$false` .</span><span class="sxs-lookup"><span data-stu-id="eecad-154">This evaluates to `$false`.</span></span> <span data-ttu-id="eecad-155">`-ne`Returnerar allt som inte matchar `$null` och i det här fallet finns det inga resultat (detta utvärderas även till `$false` ).</span><span class="sxs-lookup"><span data-stu-id="eecad-155">The `-ne` returns everything that doesn't match `$null` and in this case there are no results (This also evaluates to `$false`).</span></span> <span data-ttu-id="eecad-156">Varken en är `$true` trots att den ser ut som en av dem.</span><span class="sxs-lookup"><span data-stu-id="eecad-156">Neither one is `$true` even though it looks like one of them should be.</span></span>

<span data-ttu-id="eecad-157">Det går inte bara att skapa ett värde som gör att båda utvärderas till `$false` . det är möjligt att skapa ett värde där de båda utvärderas `$true` .</span><span class="sxs-lookup"><span data-stu-id="eecad-157">Not only can we create a value that makes both of them evaluate to `$false`, it's possible to create a value where they both evaluate to `$true`.</span></span> <span data-ttu-id="eecad-158">Mathias Jessen ( @IISResetMe ) har ett [lämpligt inlägg][] som dykningar i det scenariot.</span><span class="sxs-lookup"><span data-stu-id="eecad-158">Mathias Jessen (@IISResetMe) has a [good post][] that dives into that scenario.</span></span>

### <a name="psscriptanalyzer-and-vscode"></a><span data-ttu-id="eecad-159">PSScriptAnalyzer och VSCode</span><span class="sxs-lookup"><span data-stu-id="eecad-159">PSScriptAnalyzer and VSCode</span></span>

<span data-ttu-id="eecad-160">[PSScriptAnalyzer][] -modulen har en regel som söker efter det här problemet som kallas `PSPossibleIncorrectComparisonWithNull` .</span><span class="sxs-lookup"><span data-stu-id="eecad-160">The [PSScriptAnalyzer][] module has a rule that checks for this issue called `PSPossibleIncorrectComparisonWithNull`.</span></span>

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

<span data-ttu-id="eecad-161">Eftersom VS Code använder PSScriptAnalyser-reglerna också, markerar den eller identifierar det som ett problem i skriptet.</span><span class="sxs-lookup"><span data-stu-id="eecad-161">Because VS Code uses the PSScriptAnalyser rules too, it also highlights or identifies this as a problem in your script.</span></span>

### <a name="simple-if-check"></a><span data-ttu-id="eecad-162">Enkel om-kontroll</span><span class="sxs-lookup"><span data-stu-id="eecad-162">Simple if check</span></span>

<span data-ttu-id="eecad-163">Ett vanligt sätt att söka efter ett värde som inte är $null är att använda en enkel `if()` instruktion utan jämförelse.</span><span class="sxs-lookup"><span data-stu-id="eecad-163">A common way that people check for a non-$null value is to use a simple `if()` statement without the comparison.</span></span>

```powershell
if ( $value )
{
    Do-Something
}
```

<span data-ttu-id="eecad-164">Om värdet är `$null` , utvärderas detta till `$false` .</span><span class="sxs-lookup"><span data-stu-id="eecad-164">If the value is `$null`, this evaluates to `$false`.</span></span> <span data-ttu-id="eecad-165">Detta är enkelt att läsa, men var noga med att leta efter exakt det du förväntar dig att söka efter.</span><span class="sxs-lookup"><span data-stu-id="eecad-165">This is easy to read, but be careful that it's looking for exactly what you're expecting it to look for.</span></span> <span data-ttu-id="eecad-166">Jag läser den raden med kod som:</span><span class="sxs-lookup"><span data-stu-id="eecad-166">I read that line of code as:</span></span>

> <span data-ttu-id="eecad-167">Om `$value` har ett värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-167">If `$value` has a value.</span></span>

<span data-ttu-id="eecad-168">Men det är inte hela berättelsen.</span><span class="sxs-lookup"><span data-stu-id="eecad-168">But that's not the whole story.</span></span> <span data-ttu-id="eecad-169">Den raden säger egentligen:</span><span class="sxs-lookup"><span data-stu-id="eecad-169">That line is actually saying:</span></span>

> <span data-ttu-id="eecad-170">Om `$value` inte är `$null` eller `0` eller `$false``empty string`</span><span class="sxs-lookup"><span data-stu-id="eecad-170">If `$value` is not `$null` or `0` or `$false` or an `empty string`</span></span>

<span data-ttu-id="eecad-171">Här är ett mer komplett exempel på den här instruktionen.</span><span class="sxs-lookup"><span data-stu-id="eecad-171">Here is a more complete sample of that statement.</span></span>

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

<span data-ttu-id="eecad-172">Det är perfekt att använda en grundläggande `if` kontroll så länge du minns att de andra värdena räknas som `$false` och inte bara att en variabel har ett värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-172">It's perfectly OK to use a basic `if` check as long as you remember those other values count as `$false` and not just that a variable has a value.</span></span>

<span data-ttu-id="eecad-173">Jag har stött på det här problemet vid omstrukturering av några få dagar sedan.</span><span class="sxs-lookup"><span data-stu-id="eecad-173">I ran into this issue when refactoring some code a few days ago.</span></span> <span data-ttu-id="eecad-174">Den hade en grundläggande egenskaps kontroll som detta.</span><span class="sxs-lookup"><span data-stu-id="eecad-174">It had a basic property check like this.</span></span>

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="eecad-175">Jag ville bara tilldela ett värde till egenskapen objekt om det fanns.</span><span class="sxs-lookup"><span data-stu-id="eecad-175">I wanted to assign a value to the object property only if it existed.</span></span> <span data-ttu-id="eecad-176">I de flesta fall hade det ursprungliga objektet ett värde som skulle utvärderas `$true` i `if` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="eecad-176">In most cases, the original object had a value that would evaluate to `$true` in the `if` statement.</span></span> <span data-ttu-id="eecad-177">Men jag stötte på ett problem där värdet ibland inte skulle hämtas.</span><span class="sxs-lookup"><span data-stu-id="eecad-177">But I ran into an issue where the value was occasionally not getting set.</span></span> <span data-ttu-id="eecad-178">Jag har felsökt koden och upptäckt att objektet hade egenskapen men det var ett tomt sträng värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-178">I debugged the code and found that the object had the property but it was a blank string value.</span></span> <span data-ttu-id="eecad-179">Detta förhindrade att det någonsin uppdaterades med föregående logik.</span><span class="sxs-lookup"><span data-stu-id="eecad-179">This prevented it from ever getting updated with the previous logic.</span></span> <span data-ttu-id="eecad-180">Jag har nu lagt till en korrekt `$null` kontroll och allt arbete.</span><span class="sxs-lookup"><span data-stu-id="eecad-180">So I added a proper `$null` check and everything worked.</span></span>

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

<span data-ttu-id="eecad-181">Det är en liten del buggar som är svår att upptäcka och gör så att du kan kontrol lera värdena på ett aggressivt sätt `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-181">It's little bugs like these that are hard to spot and make me aggressively check values for `$null`.</span></span>

## <a name="nullcount"></a><span data-ttu-id="eecad-182">$null. Reparationer</span><span class="sxs-lookup"><span data-stu-id="eecad-182">$null.Count</span></span>

<span data-ttu-id="eecad-183">Om du försöker få åtkomst till en egenskap för ett `$null` värde är egenskapen också `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-183">If you try to access a property on a `$null` value, that the property is also `$null`.</span></span> <span data-ttu-id="eecad-184">`count`Egenskapen är undantags felet för den här regeln.</span><span class="sxs-lookup"><span data-stu-id="eecad-184">The `count` property is the exception to this rule.</span></span>

```powershell
PS> $value = $null
PS> $value.count
0
```

<span data-ttu-id="eecad-185">När du har ett `$null` värde `count` är det `0` .</span><span class="sxs-lookup"><span data-stu-id="eecad-185">When you have a `$null` value, then the `count` is `0`.</span></span> <span data-ttu-id="eecad-186">Den här särskilda egenskapen läggs till av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eecad-186">This special property is added by PowerShell.</span></span>

### <a name="pscustomobject-count"></a><span data-ttu-id="eecad-187">PSCustomObject Reparationer</span><span class="sxs-lookup"><span data-stu-id="eecad-187">[PSCustomObject] Count</span></span>

<span data-ttu-id="eecad-188">Nästan alla objekt i PowerShell har denna egenskap Count.</span><span class="sxs-lookup"><span data-stu-id="eecad-188">Almost all objects in PowerShell have that count property.</span></span> <span data-ttu-id="eecad-189">Ett viktigt undantag är `[PSCustomObject]` i Windows PowerShell 5,1 (detta åtgärdas i PowerShell 6,0).</span><span class="sxs-lookup"><span data-stu-id="eecad-189">One important exception is the `[PSCustomObject]` in Windows PowerShell 5.1 (This is fixed in PowerShell 6.0).</span></span> <span data-ttu-id="eecad-190">Det finns ingen Count-egenskap så du får ett `$null` värde om du försöker använda det.</span><span class="sxs-lookup"><span data-stu-id="eecad-190">It doesn't have a count property so you get a `$null` value if you try to use it.</span></span> <span data-ttu-id="eecad-191">Jag kallar det här så att du inte försöker använda `.Count` i stället för en `$null` kontroll.</span><span class="sxs-lookup"><span data-stu-id="eecad-191">I call this out here so that you don't try to use `.Count` instead of a `$null` check.</span></span>

<span data-ttu-id="eecad-192">Genom att köra det här exemplet på Windows PowerShell 5,1 och PowerShell 6,0 får du olika resultat.</span><span class="sxs-lookup"><span data-stu-id="eecad-192">Running this example on Windows PowerShell 5.1 and PowerShell 6.0 gives you different results.</span></span>

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a><span data-ttu-id="eecad-193">Tomt null</span><span class="sxs-lookup"><span data-stu-id="eecad-193">Empty null</span></span>

<span data-ttu-id="eecad-194">Det finns en speciell typ av `$null` som fungerar annorlunda än de andra.</span><span class="sxs-lookup"><span data-stu-id="eecad-194">There is one special type of `$null` that acts differently than the others.</span></span> <span data-ttu-id="eecad-195">Jag kommer att anropa det tomt, `$null` men det är verkligen en [system. Management. Automation. Internal. AutomationNull][].</span><span class="sxs-lookup"><span data-stu-id="eecad-195">I am going to call it the empty `$null` but it's really a [System.Management.Automation.Internal.AutomationNull][].</span></span> <span data-ttu-id="eecad-196">Detta tomt `$null` är det som du får som ett resultat av en funktion eller ett skript block som returnerar inget (ett void-resultat).</span><span class="sxs-lookup"><span data-stu-id="eecad-196">This empty `$null` is the one you get as the result of a function or script block that returns nothing (a void result).</span></span>

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

<span data-ttu-id="eecad-197">Om du jämför den med får `$null` du ett `$null` värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-197">If you compare it with `$null`, you get a `$null` value.</span></span> <span data-ttu-id="eecad-198">När det används i en utvärdering där ett värde krävs är värdet alltid `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-198">When used in an evaluation where a value is required, the value is always `$null`.</span></span> <span data-ttu-id="eecad-199">Men om du placerar det inuti en matris behandlas det på samma sätt som en tom matris.</span><span class="sxs-lookup"><span data-stu-id="eecad-199">But if you place it inside an array, it's treated the same as an empty array.</span></span>

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

<span data-ttu-id="eecad-200">Du kan ha en matris som innehåller ett `$null` värde och dess `count` är `1` .</span><span class="sxs-lookup"><span data-stu-id="eecad-200">You can have an array that contains one `$null` value and its `count` is `1`.</span></span> <span data-ttu-id="eecad-201">Men om du placerar ett tomt resultat i en matris räknas det inte som ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eecad-201">But if you place an empty result inside an array then it's not counted as an item.</span></span> <span data-ttu-id="eecad-202">Antalet är `0` .</span><span class="sxs-lookup"><span data-stu-id="eecad-202">The count is `0`.</span></span>

<span data-ttu-id="eecad-203">Om du behandlar det tomma `$null` objektet som en samling är det tomt.</span><span class="sxs-lookup"><span data-stu-id="eecad-203">If you treat the empty `$null` like a collection, then it's empty.</span></span>

### <a name="pipeline"></a><span data-ttu-id="eecad-204">Pipeline</span><span class="sxs-lookup"><span data-stu-id="eecad-204">Pipeline</span></span>

<span data-ttu-id="eecad-205">Den primära plats som du ser är skillnaden när du använder pipelinen.</span><span class="sxs-lookup"><span data-stu-id="eecad-205">The primary place you see the difference is when using the pipeline.</span></span> <span data-ttu-id="eecad-206">Du kan skicka ett `$null` värde, men inte ett tomt `$null` värde.</span><span class="sxs-lookup"><span data-stu-id="eecad-206">You can pipe a `$null` value but not an empty `$null` value.</span></span>

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

<span data-ttu-id="eecad-207">Beroende på din kod bör du ha ett konto för `$null` i din logik.</span><span class="sxs-lookup"><span data-stu-id="eecad-207">Depending on your code, you should account for the `$null` in your logic.</span></span>

<span data-ttu-id="eecad-208">Sök antingen efter `$null` första</span><span class="sxs-lookup"><span data-stu-id="eecad-208">Either check for `$null` first</span></span>

- <span data-ttu-id="eecad-209">Filtrera bort null i pipelinen ( `... | Where {$null -ne $_} | ...` )</span><span class="sxs-lookup"><span data-stu-id="eecad-209">Filter out null on the pipeline (`... | Where {$null -ne $_} | ...`)</span></span>
- <span data-ttu-id="eecad-210">Hantera den i pipeline-funktionen</span><span class="sxs-lookup"><span data-stu-id="eecad-210">Handle it in the pipeline function</span></span>

## <a name="foreach"></a><span data-ttu-id="eecad-211">foreach</span><span class="sxs-lookup"><span data-stu-id="eecad-211">foreach</span></span>

<span data-ttu-id="eecad-212">En av mina favorit funktioner i `foreach` är att den inte räknar upp över en `$null` samling.</span><span class="sxs-lookup"><span data-stu-id="eecad-212">One of my favorite features of `foreach` is that it doesn't enumerate over a `$null` collection.</span></span>

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

<span data-ttu-id="eecad-213">Detta sparar mig från att behöva `$null` kontrol lera samlingen innan jag räknar upp den.</span><span class="sxs-lookup"><span data-stu-id="eecad-213">This saves me from having to `$null` check the collection before I enumerate it.</span></span> <span data-ttu-id="eecad-214">Om du har en samling med `$null` värden kan det `$node` fortfarande vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-214">If you have a collection of `$null` values, the `$node` can still be `$null`.</span></span>

<span data-ttu-id="eecad-215">Den här metoden började arbeta på det här sättet med PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eecad-215">The foreach started working this way with PowerShell 3.0.</span></span> <span data-ttu-id="eecad-216">Om du råkar vara på en äldre version är detta inte fallet.</span><span class="sxs-lookup"><span data-stu-id="eecad-216">If you happen to be on an older version, then this is not the case.</span></span> <span data-ttu-id="eecad-217">Detta är en av de viktiga ändringarna som du bör känna till när du säkerhetskopierar kod för 2,0-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="eecad-217">This is one of the important changes to be aware of when back-porting code for 2.0 compatibility.</span></span>

## <a name="value-types"></a><span data-ttu-id="eecad-218">Värde typer</span><span class="sxs-lookup"><span data-stu-id="eecad-218">Value types</span></span>

<span data-ttu-id="eecad-219">Tekniskt sett kan endast referens typer användas `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-219">Technically, only reference types can be `$null`.</span></span> <span data-ttu-id="eecad-220">Men PowerShell är mycket generöst och gör det möjligt för variabler att vara vilken typ som helst.</span><span class="sxs-lookup"><span data-stu-id="eecad-220">But PowerShell is very generous and allows for variables to be any type.</span></span> <span data-ttu-id="eecad-221">Om du bestämmer dig för att ange en värdetyp som är absolut, kan det inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-221">If you decide to strongly type a value type, it cannot be `$null`.</span></span>
<span data-ttu-id="eecad-222">PowerShell konverterar `$null` till ett standardvärde för många typer.</span><span class="sxs-lookup"><span data-stu-id="eecad-222">PowerShell converts `$null` to a default value for many types.</span></span>

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

<span data-ttu-id="eecad-223">Det finns vissa typer som inte har någon giltig konvertering från `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-223">There are some types that do not have a valid conversion from `$null`.</span></span> <span data-ttu-id="eecad-224">De här typerna genererar ett `Cannot convert null to type` fel.</span><span class="sxs-lookup"><span data-stu-id="eecad-224">These types generate a `Cannot convert null to type` error.</span></span>

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a><span data-ttu-id="eecad-225">Funktions parametrar</span><span class="sxs-lookup"><span data-stu-id="eecad-225">Function parameters</span></span>

<span data-ttu-id="eecad-226">Att använda ett starkt angivet värde i funktions parametrar är mycket vanligt.</span><span class="sxs-lookup"><span data-stu-id="eecad-226">Using a strongly typed values in function parameters is very common.</span></span> <span data-ttu-id="eecad-227">Vi lär dig vanligt vis att definiera typerna av parametrar även om vi inte brukar definiera typerna av andra variabler i våra skript.</span><span class="sxs-lookup"><span data-stu-id="eecad-227">We generally learn to define the types of our parameters even if we tend not to define the types of other variables in our scripts.</span></span> <span data-ttu-id="eecad-228">Du kanske redan har några starkt skrivna variabler i dina funktioner och inte ens inser det.</span><span class="sxs-lookup"><span data-stu-id="eecad-228">You may already have some strongly typed variables in your functions and not even realize it.</span></span>

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

<span data-ttu-id="eecad-229">När du anger typen för parametern som en `string` , kan värdet aldrig vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-229">As soon as you set the type of the parameter as a `string`, the value can never be `$null`.</span></span> <span data-ttu-id="eecad-230">Det är vanligt att kontrol lera om ett värde är `$null` att se om användaren har angett ett värde eller inte.</span><span class="sxs-lookup"><span data-stu-id="eecad-230">It's common to check if a value is `$null` to see if the user provided a value or not.</span></span>

```powershell
if ( $null -ne $Value ){...}
```

<span data-ttu-id="eecad-231">`$Value` är en tom sträng `''` när inget värde har angetts.</span><span class="sxs-lookup"><span data-stu-id="eecad-231">`$Value` is an empty string `''` when no value is provided.</span></span> <span data-ttu-id="eecad-232">Använd den automatiska variabeln `$PSBoundParameters.Value` i stället.</span><span class="sxs-lookup"><span data-stu-id="eecad-232">Use the automatic variable `$PSBoundParameters.Value` instead.</span></span>

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

<span data-ttu-id="eecad-233">`$PSBoundParameters` innehåller bara de parametrar som angavs när funktionen anropades.</span><span class="sxs-lookup"><span data-stu-id="eecad-233">`$PSBoundParameters` only contains the parameters that were specified when the function was called.</span></span>
<span data-ttu-id="eecad-234">Du kan också använda- `ContainsKey` metoden för att kontrol lera egenskapen.</span><span class="sxs-lookup"><span data-stu-id="eecad-234">You can also use the `ContainsKey` method to check for the property.</span></span>

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a><span data-ttu-id="eecad-235">IsNotNullOrEmpty</span><span class="sxs-lookup"><span data-stu-id="eecad-235">IsNotNullOrEmpty</span></span>

<span data-ttu-id="eecad-236">Om värdet är en sträng kan du använda en statisk sträng funktion för att kontrol lera om värdet är `$null` eller en tom sträng på samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="eecad-236">If the value is a string, you can use a static string function to check if the value is `$null` or an empty string at the same time.</span></span>

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

<span data-ttu-id="eecad-237">Jag hittar mig själv med hjälp av det här ofta när jag vet att värde typen ska vara en sträng.</span><span class="sxs-lookup"><span data-stu-id="eecad-237">I find myself using this often when I know the value type should be a string.</span></span>

## <a name="when-i-null-check"></a><span data-ttu-id="eecad-238">När jag $null check</span><span class="sxs-lookup"><span data-stu-id="eecad-238">When I $null check</span></span>

<span data-ttu-id="eecad-239">Jag är en försvars skript.</span><span class="sxs-lookup"><span data-stu-id="eecad-239">I am a defensive scripter.</span></span> <span data-ttu-id="eecad-240">När jag anropar en funktion och tilldelar den till en variabel, kontrollerar jag den för `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-240">Anytime I call a function and assign it to a variable, I check it for `$null`.</span></span>

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

<span data-ttu-id="eecad-241">Jag föredrar att använda `if` eller `foreach` via användning `try/catch` .</span><span class="sxs-lookup"><span data-stu-id="eecad-241">I much prefer using `if` or `foreach` over using `try/catch`.</span></span> <span data-ttu-id="eecad-242">Jag vill inte ha fel, jag använder fortfarande `try/catch` mycket.</span><span class="sxs-lookup"><span data-stu-id="eecad-242">Don't get me wrong, I still use `try/catch` a lot.</span></span> <span data-ttu-id="eecad-243">Men om jag kan testa ett fel tillstånd eller en tom uppsättning resultat, kan jag tillåta min undantags hantering för sanna undantag.</span><span class="sxs-lookup"><span data-stu-id="eecad-243">But if I can test for an error condition or an empty set of results, I can allow my exception handling be for true exceptions.</span></span>

<span data-ttu-id="eecad-244">Jag tenderar också att söka efter `$null` innan jag indexerar till ett värde eller anropar metoder för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="eecad-244">I also tend to check for `$null` before I index into a value or call methods on an object.</span></span> <span data-ttu-id="eecad-245">De här två åtgärderna kan inte utföras för ett `$null` objekt så jag tycker att det är viktigt att validera dem först.</span><span class="sxs-lookup"><span data-stu-id="eecad-245">These two actions fail for a `$null` object so I find it important to validate them first.</span></span> <span data-ttu-id="eecad-246">Jag har redan täckt de scenarierna tidigare i det här inlägget.</span><span class="sxs-lookup"><span data-stu-id="eecad-246">I already covered those scenarios earlier in this post.</span></span>

### <a name="no-results-scenario"></a><span data-ttu-id="eecad-247">Inget resultat scenario</span><span class="sxs-lookup"><span data-stu-id="eecad-247">No results scenario</span></span>

<span data-ttu-id="eecad-248">Det är viktigt att veta att olika funktioner och kommandon hanterar scenariot för inga resultat annorlunda.</span><span class="sxs-lookup"><span data-stu-id="eecad-248">It's important to know that different functions and commands handle the no results scenario differently.</span></span> <span data-ttu-id="eecad-249">Många PowerShell-kommandon Returnerar tom `$null` och ett fel i fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="eecad-249">Many PowerShell commands return the empty `$null` and an error in the error stream.</span></span> <span data-ttu-id="eecad-250">Men andra genererar undantag eller ger dig ett status objekt.</span><span class="sxs-lookup"><span data-stu-id="eecad-250">But others throw exceptions or give you a status object.</span></span> <span data-ttu-id="eecad-251">Det är fortfarande upp till dig att veta hur de kommandon som du använder hanterar med inga resultat och fel scenarier.</span><span class="sxs-lookup"><span data-stu-id="eecad-251">It's still up to you to know how the commands you use deal with the no results and error scenarios.</span></span>

## <a name="initializing-to-null"></a><span data-ttu-id="eecad-252">Initierar till $null</span><span class="sxs-lookup"><span data-stu-id="eecad-252">Initializing to $null</span></span>

<span data-ttu-id="eecad-253">En jag har valt att initiera alla mina variabler innan jag använder dem.</span><span class="sxs-lookup"><span data-stu-id="eecad-253">One habit that I have picked up is initializing all my variables before I use them.</span></span> <span data-ttu-id="eecad-254">Du måste göra detta på andra språk.</span><span class="sxs-lookup"><span data-stu-id="eecad-254">You are required to do this in other languages.</span></span> <span data-ttu-id="eecad-255">Överst i min funktion eller när jag anger en förgrunds slinga definierar jag alla värden som jag använder.</span><span class="sxs-lookup"><span data-stu-id="eecad-255">At the top of my function or as I enter a foreach loop, I define all the values that I'm using.</span></span>

<span data-ttu-id="eecad-256">Här är ett scenario som jag vill ta en nära titt på.</span><span class="sxs-lookup"><span data-stu-id="eecad-256">Here is a scenario that I want you to take a close look at.</span></span> <span data-ttu-id="eecad-257">Det är ett exempel på ett fel som jag hade kunnat spåra innan.</span><span class="sxs-lookup"><span data-stu-id="eecad-257">It's an example of a bug I had to chase down before.</span></span>

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

<span data-ttu-id="eecad-258">Förväntat här är att `Get-Something` returnerar antingen ett resultat eller en tom `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-258">The expectation here is that `Get-Something` returns either a result or an empty `$null`.</span></span> <span data-ttu-id="eecad-259">Om det uppstår ett fel loggar vi det.</span><span class="sxs-lookup"><span data-stu-id="eecad-259">If there is an error, we log it.</span></span> <span data-ttu-id="eecad-260">Sedan kontrollerar vi att vi fick ett giltigt resultat innan du bearbetar det.</span><span class="sxs-lookup"><span data-stu-id="eecad-260">Then we check to make sure we got a valid result before processing it.</span></span>

<span data-ttu-id="eecad-261">Fel som döljer i den här koden är när `Get-Something` ett undantag utlöses och inget värde tilldelas `$result` .</span><span class="sxs-lookup"><span data-stu-id="eecad-261">The bug hiding in this code is when `Get-Something` throws an exception and doesn't assign a value to `$result`.</span></span> <span data-ttu-id="eecad-262">Det Miss lyckas före tilldelningen så att vi inte ens tilldelar `$null` `$result` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eecad-262">It fails before the assignment so we don't even assign `$null` to the `$result` variable.</span></span> <span data-ttu-id="eecad-263">`$result` innehåller fortfarande föregående giltig `$result` från andra iterationer.</span><span class="sxs-lookup"><span data-stu-id="eecad-263">`$result` still contains the previous valid `$result` from other iterations.</span></span>
<span data-ttu-id="eecad-264">`Update-Something` för att köra flera gånger på samma objekt i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="eecad-264">`Update-Something` to execute multiple times on the same object in this example.</span></span>

<span data-ttu-id="eecad-265">Jag har ställt in `$result` till `$null` höger i förgrunds-slingan innan jag använder den för att undvika det här problemet.</span><span class="sxs-lookup"><span data-stu-id="eecad-265">I set `$result` to `$null` right inside the foreach loop before I use it to mitigate this issue.</span></span>

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a><span data-ttu-id="eecad-266">Omfattnings problem</span><span class="sxs-lookup"><span data-stu-id="eecad-266">Scope issues</span></span>

<span data-ttu-id="eecad-267">Detta hjälper också till att minska omfattnings problem.</span><span class="sxs-lookup"><span data-stu-id="eecad-267">This also helps mitigate scoping issues.</span></span> <span data-ttu-id="eecad-268">I det exemplet tilldelar vi värden till `$result` över och över i en slinga.</span><span class="sxs-lookup"><span data-stu-id="eecad-268">In that example, we assign values to `$result` over and over in a loop.</span></span> <span data-ttu-id="eecad-269">Men eftersom PowerShell tillåter variabel värden utanför funktionen att utlösas i omfånget för den aktuella funktionen, minimerar de fel som kan introduceras på det sättet genom att initiera dem i funktionen.</span><span class="sxs-lookup"><span data-stu-id="eecad-269">But because PowerShell allows variable values from outside the function to bleed into the scope of the current function, initializing them inside your function mitigates bugs that can be introduced that way.</span></span>

<span data-ttu-id="eecad-270">En oinitierad variabel i funktionen är inte `$null` om den har angetts till ett värde i en överordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="eecad-270">An uninitialized variable in your function is not `$null` if it's set to a value in a parent scope.</span></span>
<span data-ttu-id="eecad-271">Det överordnade omfånget kan vara en annan funktion som anropar din funktion och använder samma variabel namn.</span><span class="sxs-lookup"><span data-stu-id="eecad-271">The parent scope could be another function that calls your function and uses the same variable names.</span></span>

<span data-ttu-id="eecad-272">Om jag `Do-something` använder samma exempel och tar bort slingan så skulle jag få något som ser ut som i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="eecad-272">If I take that same `Do-something` example and remove the loop, I would end up with something that looks like this example:</span></span>

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

<span data-ttu-id="eecad-273">Om anropet `Get-Something` returnerar ett undantag `$null` hittar min kontroll `$result` från `Invoke-Something` .</span><span class="sxs-lookup"><span data-stu-id="eecad-273">If the call to `Get-Something` throws an exception, then my `$null` check finds the `$result` from `Invoke-Something`.</span></span> <span data-ttu-id="eecad-274">Att initiera värdet i funktionen minskar det här problemet.</span><span class="sxs-lookup"><span data-stu-id="eecad-274">Initializing the value inside your function mitigates this issue.</span></span>

<span data-ttu-id="eecad-275">Namngivning av variabler är svårt och det är vanligt att en författare använder samma variabel namn i flera funktioner.</span><span class="sxs-lookup"><span data-stu-id="eecad-275">Naming variables is hard and it's common for an author to use the same variable names in multiple functions.</span></span> <span data-ttu-id="eecad-276">Jag vet att jag använder `$node` , `$result` och `$data` hela tiden.</span><span class="sxs-lookup"><span data-stu-id="eecad-276">I know I use `$node`,`$result`,`$data` all the time.</span></span> <span data-ttu-id="eecad-277">Det skulle då vara mycket enkelt för värden från olika omfattningar att visas på platser där de inte ska vara det.</span><span class="sxs-lookup"><span data-stu-id="eecad-277">So it would be very easy for values from different scopes to show up in places where they should not be.</span></span>

## <a name="redirect-output-to-null"></a><span data-ttu-id="eecad-278">Omdirigera utdata till $null</span><span class="sxs-lookup"><span data-stu-id="eecad-278">Redirect output to $null</span></span>

<span data-ttu-id="eecad-279">Jag har pratat om `$null` värden för hela artikeln men avsnittet är inte klart om jag inte omdirigeringen av utdata till `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-279">I have been talking about `$null` values for this entire article but the topic is not complete if I didn't mention redirecting output to `$null`.</span></span> <span data-ttu-id="eecad-280">Det finns tillfällen när du har kommandon som utvärderar information eller objekt som du vill ignorera.</span><span class="sxs-lookup"><span data-stu-id="eecad-280">There are times when you have commands that output information or objects that you want to suppress.</span></span> <span data-ttu-id="eecad-281">Omdirigerar utdata till `$null` gör det.</span><span class="sxs-lookup"><span data-stu-id="eecad-281">Redirecting output to `$null` does that.</span></span>

### <a name="out-null"></a><span data-ttu-id="eecad-282">Ut-null</span><span class="sxs-lookup"><span data-stu-id="eecad-282">Out-Null</span></span>

<span data-ttu-id="eecad-283">Kommandot out-null är det inbyggda sättet att omdirigera pipeline-data till `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-283">The Out-Null command is the built-in way to redirect pipeline data to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a><span data-ttu-id="eecad-284">Tilldela till $null</span><span class="sxs-lookup"><span data-stu-id="eecad-284">Assign to $null</span></span>

<span data-ttu-id="eecad-285">Du kan tilldela resultatet av ett kommando för att `$null` få samma resultat som med `Out-Null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-285">You can assign the results of a command to `$null` for the same effect as using `Out-Null`.</span></span>

```powershell
$null = New-Item -Type Directory -Path $path
```

<span data-ttu-id="eecad-286">Eftersom `$null` är ett konstant värde kan du aldrig skriva över det.</span><span class="sxs-lookup"><span data-stu-id="eecad-286">Because `$null` is a constant value, you can never overwrite it.</span></span> <span data-ttu-id="eecad-287">Jag vill inte att det ska se ut i koden, men det går ofta snabbare än `Out-Null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-287">I don't like the way it looks in my code but it often performs faster than `Out-Null`.</span></span>

### <a name="redirect-to-null"></a><span data-ttu-id="eecad-288">Omdirigera till $null</span><span class="sxs-lookup"><span data-stu-id="eecad-288">Redirect to $null</span></span>

<span data-ttu-id="eecad-289">Du kan också använda operatorn för omdirigering för att skicka utdata till `$null` .</span><span class="sxs-lookup"><span data-stu-id="eecad-289">You can also use the redirection operator to send output to `$null`.</span></span>

```powershell
New-Item -Type Directory -Path $path > $null
```

<span data-ttu-id="eecad-290">Om du hanterar körbara kommando rads program som utdata på olika strömmar.</span><span class="sxs-lookup"><span data-stu-id="eecad-290">If you're dealing with command-line executables that output on the different streams.</span></span> <span data-ttu-id="eecad-291">Du kan omdirigera alla utdata strömmar till så `$null` här:</span><span class="sxs-lookup"><span data-stu-id="eecad-291">You can redirect all output streams to `$null` like this:</span></span>

```powershell
git status *> $null
```

## <a name="summary"></a><span data-ttu-id="eecad-292">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="eecad-292">Summary</span></span>

<span data-ttu-id="eecad-293">Jag har täckt en stor del av den här artikeln och jag vet att den här artikeln är mer fragmenterad än de flesta av mina djupgående dykningar.</span><span class="sxs-lookup"><span data-stu-id="eecad-293">I covered a lot of ground on this one and I know this article is more fragmented than most of my deep dives.</span></span> <span data-ttu-id="eecad-294">Det beror på att `$null` värden kan visas på många olika platser i PowerShell och alla olika delarna är bara de där du hittar det.</span><span class="sxs-lookup"><span data-stu-id="eecad-294">That is because `$null` values can pop up in many different places in PowerShell and all the nuances are specific to where you find it.</span></span> <span data-ttu-id="eecad-295">Jag hoppas att du får en bättre förståelse för `$null` och en medvetenhet om de mer dolda scenarier som du kan köra i.</span><span class="sxs-lookup"><span data-stu-id="eecad-295">I hope you walk away from this with a better understanding of `$null` and an awareness of the more obscure scenarios you may run into.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[original version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[lämpligt inlägg]: https://blog.iisreset.me/schrodingers-argumentlist
[good post]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System. Management. Automation. Internal. AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
[System.Management.Automation.Internal.AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
