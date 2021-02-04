---
title: Allt du ville veta om hash
description: Hash är verkligen viktiga i PowerShell så det är bra att ha en solid förståelse för dem.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e386e2aa2f7b85bee4bf622fd9251ef7642cf16a
ms.sourcegitcommit: 57e577097085dc621bd797ef4a7e2854ea7d4e29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2021
ms.locfileid: "97980509"
---
# <a name="everything-you-wanted-to-know-about-hashtables"></a><span data-ttu-id="aacda-103">Allt du ville veta om hash</span><span class="sxs-lookup"><span data-stu-id="aacda-103">Everything you wanted to know about hashtables</span></span>

<span data-ttu-id="aacda-104">Jag vill göra ett steg tillbaka och prata om [hash][].</span><span class="sxs-lookup"><span data-stu-id="aacda-104">I want to take a step back and talk about [hashtables][].</span></span> <span data-ttu-id="aacda-105">Jag använder dem nu.</span><span class="sxs-lookup"><span data-stu-id="aacda-105">I use them all the time now.</span></span> <span data-ttu-id="aacda-106">Jag har undervisat någon om dem efter vårt användar grupp möte förra natten och jag realiserade att jag hade samma förvirring om dem som han hade.</span><span class="sxs-lookup"><span data-stu-id="aacda-106">I was teaching someone about them after our user group meeting last night and I realized I had the same confusion about them as he had.</span></span> <span data-ttu-id="aacda-107">Hash är verkligen viktiga i PowerShell så det är bra att ha en solid förståelse för dem.</span><span class="sxs-lookup"><span data-stu-id="aacda-107">Hashtables are really important in PowerShell so it's good to have a solid understanding of them.</span></span>

> [!NOTE]
> <span data-ttu-id="aacda-108">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="aacda-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="aacda-109">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="aacda-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="aacda-110">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="aacda-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="hashtable-as-a-collection-of-things"></a><span data-ttu-id="aacda-111">Hash-objekt som en samling saker</span><span class="sxs-lookup"><span data-stu-id="aacda-111">Hashtable as a collection of things</span></span>

<span data-ttu-id="aacda-112">Jag vill först se en hash- **hash** som en samling i den traditionella definitionen av en hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="aacda-112">I want you to first see a **Hashtable** as a collection in the traditional definition of a hashtable.</span></span> <span data-ttu-id="aacda-113">Den här definitionen ger dig en grundläggande förståelse för hur de fungerar när de används för mer avancerade saker senare.</span><span class="sxs-lookup"><span data-stu-id="aacda-113">This definition gives you a fundamental understanding of how they work when they get used for more advanced stuff later.</span></span> <span data-ttu-id="aacda-114">Att hoppa över den här förståelsen är ofta en källa för förvirring.</span><span class="sxs-lookup"><span data-stu-id="aacda-114">Skipping this understanding is often a source of confusion.</span></span>

## <a name="what-is-an-array"></a><span data-ttu-id="aacda-115">Vad är en matris?</span><span class="sxs-lookup"><span data-stu-id="aacda-115">What is an array?</span></span>

<span data-ttu-id="aacda-116">Innan jag hoppar till vad en **hash** -tabell är måste jag nämna [matriser][] först.</span><span class="sxs-lookup"><span data-stu-id="aacda-116">Before I jump into what a **Hashtable** is, I need to mention [arrays][] first.</span></span> <span data-ttu-id="aacda-117">I den här diskussionen är en matris en lista eller samling med värden eller objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-117">For the purpose of this discussion, an array is a list or collection of values or objects.</span></span>

```powershell
$array = @(1,2,3,5,7,11)
```

<span data-ttu-id="aacda-118">När du har dina objekt i en matris kan du antingen använda `foreach` för att iterera över listan eller använda ett index för att komma åt enskilda element i matrisen.</span><span class="sxs-lookup"><span data-stu-id="aacda-118">Once you have your items into an array, you can either use `foreach` to iterate over the list or use an index to access individual elements in the array.</span></span>

```powershell
foreach($item in $array)
{
    Write-Output $item
}

Write-Output $array[3]
```

<span data-ttu-id="aacda-119">Du kan också uppdatera värden med hjälp av ett index på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="aacda-119">You can also update values using an index in the same way.</span></span>

```powershell
$array[2] = 13
```

<span data-ttu-id="aacda-120">Jag har precis skapat ytan på matriser, men den bör placera dem i rätt sammanhang när jag flyttar till hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-120">I just scratched the surface on arrays but that should put them into the right context as I move onto hashtables.</span></span>

## <a name="what-is-a-hashtable"></a><span data-ttu-id="aacda-121">Vad är en hash-information?</span><span class="sxs-lookup"><span data-stu-id="aacda-121">What is a hashtable?</span></span>

<span data-ttu-id="aacda-122">Jag ska börja med en grundläggande teknisk beskrivning av vad hash är, i den allmänna meningen, innan jag växlar till andra sätt som PowerShell använder dem.</span><span class="sxs-lookup"><span data-stu-id="aacda-122">I'm going to start with a basic technical description of what hashtables are, in the general sense, before I shift into the other ways PowerShell uses them.</span></span>

<span data-ttu-id="aacda-123">En hash-tabell är en data struktur, ungefär som en matris, förutom att du lagrar varje värde (objekt) med hjälp av en nyckel.</span><span class="sxs-lookup"><span data-stu-id="aacda-123">A hashtable is a data structure, much like an array, except you store each value (object) using a key.</span></span> <span data-ttu-id="aacda-124">Det är ett grundläggande nyckel/värde-lager.</span><span class="sxs-lookup"><span data-stu-id="aacda-124">It's a basic key/value store.</span></span> <span data-ttu-id="aacda-125">Först skapar vi en tom hash-sträng.</span><span class="sxs-lookup"><span data-stu-id="aacda-125">First, we create an empty hashtable.</span></span>

```powershell
$ageList = @{}
```

<span data-ttu-id="aacda-126">Observera att klammerparenteser, i stället för parenteser, används för att definiera en hash-hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-126">Notice that braces, instead of parentheses, are used to define a hashtable.</span></span> <span data-ttu-id="aacda-127">Sedan lägger vi till ett objekt med en nyckel som detta:</span><span class="sxs-lookup"><span data-stu-id="aacda-127">Then we add an item using a key like this:</span></span>

```powershell
$key = 'Kevin'
$value = 36
$ageList.add( $key, $value )

$ageList.add( 'Alex', 9 )
```

<span data-ttu-id="aacda-128">Personens namn är nyckeln och deras ålder är det värde som jag vill spara.</span><span class="sxs-lookup"><span data-stu-id="aacda-128">The person's name is the key and their age is the value that I want to save.</span></span>

## <a name="using-the-brackets-for-access"></a><span data-ttu-id="aacda-129">Använda hakparenteser för åtkomst</span><span class="sxs-lookup"><span data-stu-id="aacda-129">Using the brackets for access</span></span>

<span data-ttu-id="aacda-130">När du har lagt till värdena i hash-tabellen kan du dra tillbaka dem med samma nyckel (i stället för att använda ett numeriskt index som du skulle ha för en matris).</span><span class="sxs-lookup"><span data-stu-id="aacda-130">Once you add your values to the hashtable, you can pull them back out using that same key (instead of using a numeric index like you would have for an array).</span></span>

```powershell
$ageList['Kevin']
$ageList['Alex']
```

<span data-ttu-id="aacda-131">När jag vill att Kevins ålder ska jag använda sitt namn för att komma åt det.</span><span class="sxs-lookup"><span data-stu-id="aacda-131">When I want Kevin's age, I use his name to access it.</span></span> <span data-ttu-id="aacda-132">Vi kan använda den här metoden för att lägga till eller uppdatera värden i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="aacda-132">We can use this approach to add or update values into the hashtable too.</span></span> <span data-ttu-id="aacda-133">Detta är precis som att använda `add()` funktionen ovan.</span><span class="sxs-lookup"><span data-stu-id="aacda-133">This is just like using the `add()` function above.</span></span>

```powershell
$ageList = @{}

$key = 'Kevin'
$value = 36
$ageList[$key] = $value

$ageList['Alex'] = 9
```

<span data-ttu-id="aacda-134">Det finns en annan syntax som du kan använda för att komma åt och uppdatera värden som jag får i ett senare avsnitt.</span><span class="sxs-lookup"><span data-stu-id="aacda-134">There's another syntax you can use for accessing and updating values that I'll cover in a later section.</span></span> <span data-ttu-id="aacda-135">Om du kommer till PowerShell från ett annat språk bör dessa exempel anpassas i med hur du kan använda hash tidigare.</span><span class="sxs-lookup"><span data-stu-id="aacda-135">If you're coming to PowerShell from another language, these examples should fit in with how you may have used hashtables before.</span></span>

### <a name="creating-hashtables-with-values"></a><span data-ttu-id="aacda-136">Skapa hash med värden</span><span class="sxs-lookup"><span data-stu-id="aacda-136">Creating hashtables with values</span></span>

<span data-ttu-id="aacda-137">Hittills har jag skapat en tom hash-hash för de här exemplen.</span><span class="sxs-lookup"><span data-stu-id="aacda-137">So far I've created an empty hashtable for these examples.</span></span> <span data-ttu-id="aacda-138">Du kan fylla i nycklar och värden i förväg när du skapar dem.</span><span class="sxs-lookup"><span data-stu-id="aacda-138">You can pre-populate the keys and values when you create them.</span></span>

```powershell
$ageList = @{
    Kevin = 36
    Alex  = 9
}
```

### <a name="as-a-lookup-table"></a><span data-ttu-id="aacda-139">Som en uppslags tabell</span><span class="sxs-lookup"><span data-stu-id="aacda-139">As a lookup table</span></span>

<span data-ttu-id="aacda-140">Det verkliga värdet för den här typen av hash-tabell är att du kan använda dem som en uppslags tabell.</span><span class="sxs-lookup"><span data-stu-id="aacda-140">The real value of this type of a hashtable is that you can use them as a lookup table.</span></span> <span data-ttu-id="aacda-141">Här är ett enkelt exempel.</span><span class="sxs-lookup"><span data-stu-id="aacda-141">Here is a simple example.</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}

$server = $environments[$env]
```

<span data-ttu-id="aacda-142">I det här exemplet anger du en miljö för `$env` variabeln och den kommer att välja rätt server.</span><span class="sxs-lookup"><span data-stu-id="aacda-142">In this example, you specify an environment for the `$env` variable and it will pick the correct server.</span></span> <span data-ttu-id="aacda-143">Du kan använda en `switch($env){...}` för ett val som detta, men en hash-hash är ett bra alternativ.</span><span class="sxs-lookup"><span data-stu-id="aacda-143">You could use a `switch($env){...}` for a selection like this but a hashtable is a nice option.</span></span>

<span data-ttu-id="aacda-144">Detta blir ännu bättre när du skapar uppslags tabellen dynamiskt för att använda den senare.</span><span class="sxs-lookup"><span data-stu-id="aacda-144">This gets even better when you dynamically build the lookup table to use it later.</span></span> <span data-ttu-id="aacda-145">Tänk på att använda den här metoden när du behöver referera något.</span><span class="sxs-lookup"><span data-stu-id="aacda-145">So think about using this approach when you need to cross reference something.</span></span> <span data-ttu-id="aacda-146">Jag tror att vi ser detta ännu mer om PowerShell inte var så användbart vid filtrering av pipe med `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="aacda-146">I think we would see this even more if PowerShell wasn't so good at filtering on the pipe with `Where-Object`.</span></span> <span data-ttu-id="aacda-147">Om du någonsin är i en situation där prestanda är viktigt måste den här metoden beaktas.</span><span class="sxs-lookup"><span data-stu-id="aacda-147">If you're ever in a situation where performance matters, this approach needs to be considered.</span></span>

<span data-ttu-id="aacda-148">Jag säger inte att det går snabbare, men det passar i regeln [om prestanda, testa det][].</span><span class="sxs-lookup"><span data-stu-id="aacda-148">I won't say that it's faster, but it does fit into the rule of [If performance matters, test it][].</span></span>

#### <a name="multiselection"></a><span data-ttu-id="aacda-149">Multimarkering</span><span class="sxs-lookup"><span data-stu-id="aacda-149">Multiselection</span></span>

<span data-ttu-id="aacda-150">I allmänhet tänker du på en hash som ett nyckel/värde-par, där du anger en nyckel och får ett värde.</span><span class="sxs-lookup"><span data-stu-id="aacda-150">Generally, you think of a hashtable as a key/value pair, where you provide one key and get one value.</span></span> <span data-ttu-id="aacda-151">Med PowerShell kan du ange en matris med nycklar för att hämta flera värden.</span><span class="sxs-lookup"><span data-stu-id="aacda-151">PowerShell allows you to provide an array of keys to get multiple values.</span></span>

```powershell
$environments[@('QA','DEV')]
$environments[('QA','DEV')]
$environments['QA','DEV']
```

<span data-ttu-id="aacda-152">I det här exemplet använder jag samma uppslags-hash från ovanstående och ger tre olika mat ris format för att hämta matchningarna.</span><span class="sxs-lookup"><span data-stu-id="aacda-152">In this example, I use the same lookup hashtable from above and provide three different array styles to get the matches.</span></span> <span data-ttu-id="aacda-153">Det här är en dold gem i PowerShell som de flesta inte känner till.</span><span class="sxs-lookup"><span data-stu-id="aacda-153">This is a hidden gem in PowerShell that most people aren't aware of.</span></span>

## <a name="iterating-hashtables"></a><span data-ttu-id="aacda-154">Iterera hash</span><span class="sxs-lookup"><span data-stu-id="aacda-154">Iterating hashtables</span></span>

<span data-ttu-id="aacda-155">Eftersom en hash-tabell är en samling nyckel/värde-par itererar du över den på ett annat sätt än för en matris eller en normal lista med objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-155">Because a hashtable is a collection of key/value pairs, you iterate over it differently than you do for an array or a normal list of items.</span></span>

<span data-ttu-id="aacda-156">Det första du ska märka är att om du rör din hash-post behandlar pipe det som ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-156">The first thing to notice is that if you pipe your hashtable, the pipe treats it like one object.</span></span>

```powershell
PS> $ageList | Measure-Object
count : 1
```

<span data-ttu-id="aacda-157">Även om `.count` egenskapen visar hur många värden den innehåller.</span><span class="sxs-lookup"><span data-stu-id="aacda-157">Even though the `.count` property tells you how many values it contains.</span></span>

```powershell
PS> $ageList.count
2
```

<span data-ttu-id="aacda-158">Du kommer runt det här problemet genom att använda- `.values` egenskapen om allt du behöver är bara värdena.</span><span class="sxs-lookup"><span data-stu-id="aacda-158">You get around this issue by using the `.values` property if all you need is just the values.</span></span>

```powershell
PS> $ageList.values | Measure-Object -Average
Count   : 2
Average : 22.5
```

<span data-ttu-id="aacda-159">Det är ofta mer användbart att räkna upp nycklar och använda dem för att få åtkomst till värdena.</span><span class="sxs-lookup"><span data-stu-id="aacda-159">It's often more useful to enumerate the keys and use them to access the values.</span></span>

```powershell
PS> $ageList.keys | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_, $ageList[$_]
    Write-Output $message
}
Kevin is 36 years old
Alex is 9 years old
```

<span data-ttu-id="aacda-160">Här är samma exempel med en `foreach(){...}` slinga.</span><span class="sxs-lookup"><span data-stu-id="aacda-160">Here is the same example with a `foreach(){...}` loop.</span></span>

```powershell
foreach($key in $ageList.keys)
{
    $message = '{0} is {1} years old' -f $key, $ageList[$key]
    Write-Output $message
}
```

<span data-ttu-id="aacda-161">Vi använder varje nyckel i hash-tabellen och använder den för att få åtkomst till värdet.</span><span class="sxs-lookup"><span data-stu-id="aacda-161">We are walking each key in the hashtable and then using it to access the value.</span></span> <span data-ttu-id="aacda-162">Det här är ett vanligt mönster när du arbetar med hash som en samling.</span><span class="sxs-lookup"><span data-stu-id="aacda-162">This is a common pattern when working with hashtables as a collection.</span></span>

### <a name="getenumerator"></a><span data-ttu-id="aacda-163">GetEnumerator ()</span><span class="sxs-lookup"><span data-stu-id="aacda-163">GetEnumerator()</span></span>

<span data-ttu-id="aacda-164">Det gör att vi kan `GetEnumerator()` iterera över vår hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-164">That brings us to `GetEnumerator()` for iterating over our hashtable.</span></span>

```powershell
$ageList.GetEnumerator() | ForEach-Object{
    $message = '{0} is {1} years old!' -f $_.key, $_.value
    Write-Output $message
}
```

<span data-ttu-id="aacda-165">Uppräkna ren ger dig varje nyckel/värde-par ett efter ett annat.</span><span class="sxs-lookup"><span data-stu-id="aacda-165">The enumerator gives you each key/value pair one after another.</span></span> <span data-ttu-id="aacda-166">Den har utformats särskilt för detta användnings fall.</span><span class="sxs-lookup"><span data-stu-id="aacda-166">It was designed specifically for this use case.</span></span> <span data-ttu-id="aacda-167">Tack för att du [markerar Kraus](https://get-PowerShellblog.blogspot.com) för att påminna mig om det här.</span><span class="sxs-lookup"><span data-stu-id="aacda-167">Thank you to [Mark Kraus](https://get-PowerShellblog.blogspot.com) for reminding me of this one.</span></span>

### <a name="badenumeration"></a><span data-ttu-id="aacda-168">BadEnumeration</span><span class="sxs-lookup"><span data-stu-id="aacda-168">BadEnumeration</span></span>

<span data-ttu-id="aacda-169">En viktig information är att du inte kan ändra en hash-tabell när den har räknats upp.</span><span class="sxs-lookup"><span data-stu-id="aacda-169">One important detail is that you can't modify a hashtable while it's being enumerated.</span></span> <span data-ttu-id="aacda-170">Om vi börjar med vårt grundläggande `$environments` exempel:</span><span class="sxs-lookup"><span data-stu-id="aacda-170">If we start with our basic `$environments` example:</span></span>

```powershell
$environments = @{
    Prod = 'SrvProd05'
    QA   = 'SrvQA02'
    Dev  = 'SrvDev12'
}
```

<span data-ttu-id="aacda-171">Och försök att ange varje nyckel till samma server värde Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="aacda-171">And trying to set every key to the same server value fails.</span></span>

```powershell
$environments.Keys | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}

An error occurred while enumerating through a collection: Collection was modified; enumeration operation may not execute.
+ CategoryInfo          : InvalidOperation: tableEnumerator:HashtableEnumerator) [], RuntimeException
+ FullyQualifiedErrorId : BadEnumeration
```

<span data-ttu-id="aacda-172">Detta kommer också att Miss Miss förfinat även om det ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="aacda-172">This will also fail even though it looks like it should also be fine:</span></span>

```powershell
foreach($key in $environments.keys) {
    $environments[$key] = 'SrvDev03'
}

Collection was modified; enumeration operation may not execute.
    + CategoryInfo          : OperationStopped: (:) [], InvalidOperationException
    + FullyQualifiedErrorId : System.InvalidOperationException
```

<span data-ttu-id="aacda-173">Den här situationen är att klona nycklarna innan du utför uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="aacda-173">The trick to this situation is to clone the keys before doing the enumeration.</span></span>

```powershell
$environments.Keys.Clone() | ForEach-Object {
    $environments[$_] = 'SrvDev03'
}
```

## <a name="hashtable-as-a-collection-of-properties"></a><span data-ttu-id="aacda-174">Hash-egenskap som en samling egenskaper</span><span class="sxs-lookup"><span data-stu-id="aacda-174">Hashtable as a collection of properties</span></span>

<span data-ttu-id="aacda-175">Hittills var den typ av objekt som vi placerade i vår hash alla samma typ av objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-175">So far the type of objects we placed in our hashtable were all the same type of object.</span></span> <span data-ttu-id="aacda-176">Jag har använt åldrar i alla dessa exempel och nyckeln var personens namn.</span><span class="sxs-lookup"><span data-stu-id="aacda-176">I used ages in all those examples and the key was the person's name.</span></span> <span data-ttu-id="aacda-177">Detta är ett bra sätt att titta på den när din samling objekt har ett namn.</span><span class="sxs-lookup"><span data-stu-id="aacda-177">This is a great way to look at it when your collection of objects each have a name.</span></span> <span data-ttu-id="aacda-178">Ett annat vanligt sätt att använda hash i PowerShell är att lagra en samling egenskaper där nyckeln är namnet på egenskapen.</span><span class="sxs-lookup"><span data-stu-id="aacda-178">Another common way to use hashtables in PowerShell is to hold a collection of properties where the key is the name of the property.</span></span> <span data-ttu-id="aacda-179">Jag kommer att gå igenom den idén i nästa exempel.</span><span class="sxs-lookup"><span data-stu-id="aacda-179">I'll step into that idea in this next example.</span></span>

### <a name="property-based-access"></a><span data-ttu-id="aacda-180">Egenskaps-baserad åtkomst</span><span class="sxs-lookup"><span data-stu-id="aacda-180">Property-based access</span></span>

<span data-ttu-id="aacda-181">Användningen av egenskaps-baserad åtkomst ändrar Dynamics-hash och hur du kan använda dem i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aacda-181">The use of property-based access changes the dynamics of hashtables and how you can use them in PowerShell.</span></span> <span data-ttu-id="aacda-182">Här är vårt vanliga exempel ovan som behandlar nycklarna som egenskaper.</span><span class="sxs-lookup"><span data-stu-id="aacda-182">Here is our usual example from above treating the keys as properties.</span></span>

```powershell
$ageList = @{}
$ageList.Kevin = 35
$ageList.Alex = 9
```

<span data-ttu-id="aacda-183">Precis som i exemplen ovan lägger det här exemplet till dessa nycklar om de inte redan finns i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="aacda-183">Just like the examples above, this example adds those keys if they don't exist in the hashtable already.</span></span> <span data-ttu-id="aacda-184">Beroende på hur du har definierat dina nycklar och vilka värden som är, är detta antingen lite konstigt eller en perfekt anpassning.</span><span class="sxs-lookup"><span data-stu-id="aacda-184">Depending on how you defined your keys and what your values are, this is either a little strange or a perfect fit.</span></span> <span data-ttu-id="aacda-185">Exemplet på ålders listan har fungerat bra fram till den här punkten.</span><span class="sxs-lookup"><span data-stu-id="aacda-185">The age list example has worked great up until this point.</span></span> <span data-ttu-id="aacda-186">Vi behöver ett nytt exempel för att det ska gå att gå vidare.</span><span class="sxs-lookup"><span data-stu-id="aacda-186">We need a new example for this to feel right going forward.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="aacda-187">Och vi kan lägga till och komma åt attribut på `$person` liknande sätt.</span><span class="sxs-lookup"><span data-stu-id="aacda-187">And we can add and access attributes on the `$person` like this.</span></span>

```powershell
$person.city = 'Austin'
$person.state = 'TX'
```

<span data-ttu-id="aacda-188">Alla en plötslig denna hash börjar känna och fungerar som ett-objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-188">All of a sudden this hashtable starts to feel and act like an object.</span></span> <span data-ttu-id="aacda-189">Det är fortfarande en samling saker, så alla exempel ovan gäller fortfarande.</span><span class="sxs-lookup"><span data-stu-id="aacda-189">It's still a collection of things, so all the examples above still apply.</span></span> <span data-ttu-id="aacda-190">Vi är bara på plats från en annan vy.</span><span class="sxs-lookup"><span data-stu-id="aacda-190">We just approach it from a different point of view.</span></span>

### <a name="checking-for-keys-and-values"></a><span data-ttu-id="aacda-191">Söker efter nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="aacda-191">Checking for keys and values</span></span>

<span data-ttu-id="aacda-192">I de flesta fall kan du bara testa för värdet med något som liknar detta:</span><span class="sxs-lookup"><span data-stu-id="aacda-192">In most cases, you can just test for the value with something like this:</span></span>

```powershell
if( $person.age ){...}
```

<span data-ttu-id="aacda-193">Det är enkelt men har varit källan till många buggar för mig eftersom jag skulle se en viktig information i min logik.</span><span class="sxs-lookup"><span data-stu-id="aacda-193">It's simple but has been the source of many bugs for me because I was overlooking one important detail in my logic.</span></span> <span data-ttu-id="aacda-194">Jag började använda den för att testa om en nyckel fanns.</span><span class="sxs-lookup"><span data-stu-id="aacda-194">I started to use it to test if a key was present.</span></span> <span data-ttu-id="aacda-195">När värdet var `$false` eller noll returnerades instruktionen `$false` oväntad.</span><span class="sxs-lookup"><span data-stu-id="aacda-195">When the value was `$false` or zero, that statement would return `$false` unexpectedly.</span></span>

```powershell
if( $person.age -ne $null ){...}
```

<span data-ttu-id="aacda-196">Detta fungerar runt det här problemet för noll värden men inte $null vs-nycklar som inte finns.</span><span class="sxs-lookup"><span data-stu-id="aacda-196">This works around that issue for zero values but not $null vs non-existent keys.</span></span> <span data-ttu-id="aacda-197">I de flesta fall behöver du inte göra åtskillnaden men det finns funktioner för när du gör det.</span><span class="sxs-lookup"><span data-stu-id="aacda-197">Most of the time you don't need to make that distinction but there are functions for when you do.</span></span>

```powershell
if( $person.ContainsKey('age') ){...}
```

<span data-ttu-id="aacda-198">Vi har också en `ContainsValue()` för situation där du behöver testa ett värde utan att känna till nyckeln eller iterera hela samlingen.</span><span class="sxs-lookup"><span data-stu-id="aacda-198">We also have a `ContainsValue()` for the situation where you need to test for a value without knowing the key or iterating the whole collection.</span></span>

### <a name="removing-and-clearing-keys"></a><span data-ttu-id="aacda-199">Ta bort och rensa nycklar</span><span class="sxs-lookup"><span data-stu-id="aacda-199">Removing and clearing keys</span></span>

<span data-ttu-id="aacda-200">Du kan ta bort nycklar med `.Remove()` funktionen.</span><span class="sxs-lookup"><span data-stu-id="aacda-200">You can remove keys with the `.Remove()` function.</span></span>

```powershell
$person.remove('age')
```

<span data-ttu-id="aacda-201">Genom att tilldela dem ett `$null` värde är det bara att ha en nyckel som har ett `$null` värde.</span><span class="sxs-lookup"><span data-stu-id="aacda-201">Assigning them a `$null` value just leaves you with a key that has a `$null` value.</span></span>

<span data-ttu-id="aacda-202">Ett vanligt sätt att rensa en hash-text är att bara initiera den till en tom hash-text.</span><span class="sxs-lookup"><span data-stu-id="aacda-202">A common way to clear a hashtable is to just initialize it to an empty hashtable.</span></span>

```powershell
$person = @{}
```

<span data-ttu-id="aacda-203">Även om det fungerar kan du försöka använda `clear()` funktionen i stället.</span><span class="sxs-lookup"><span data-stu-id="aacda-203">While that does work, try to use the `clear()` function instead.</span></span>

```powershell
$person.clear()
```

<span data-ttu-id="aacda-204">Detta är en av de instanser som använder funktionen för att skapa självdokumenterande kod och det gör avsikter i koden mycket rent.</span><span class="sxs-lookup"><span data-stu-id="aacda-204">This is one of those instances where using the function creates self-documenting code and it makes the intentions of the code very clean.</span></span>

## <a name="all-the-fun-stuff"></a><span data-ttu-id="aacda-205">Alla roliga saker</span><span class="sxs-lookup"><span data-stu-id="aacda-205">All the fun stuff</span></span>

### <a name="ordered-hashtables"></a><span data-ttu-id="aacda-206">Beställda hash</span><span class="sxs-lookup"><span data-stu-id="aacda-206">Ordered hashtables</span></span>

<span data-ttu-id="aacda-207">Som standard beställs hash inte (eller sorteras).</span><span class="sxs-lookup"><span data-stu-id="aacda-207">By default, hashtables aren't ordered (or sorted).</span></span> <span data-ttu-id="aacda-208">I det traditionella sammanhanget spelar det ingen roll när du alltid använder en nyckel för att få åtkomst till värden.</span><span class="sxs-lookup"><span data-stu-id="aacda-208">In the traditional context, the order doesn't matter when you always use a key to access values.</span></span> <span data-ttu-id="aacda-209">Du kanske upptäcker att du vill att egenskaperna ska stanna kvar i den ordning som du definierar dem.</span><span class="sxs-lookup"><span data-stu-id="aacda-209">You may find that you want the properties to stay in the order that you define them.</span></span> <span data-ttu-id="aacda-210">Thankfully finns ett sätt att göra det med `ordered` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="aacda-210">Thankfully, there's a way to do that with the `ordered` keyword.</span></span>

```powershell
$person = [ordered]@{
    name = 'Kevin'
    age  = 36
}
```

<span data-ttu-id="aacda-211">Nu när du räknar upp nycklar och värden finns de kvar i den ordningen.</span><span class="sxs-lookup"><span data-stu-id="aacda-211">Now when you enumerate the keys and values, they stay in that order.</span></span>

### <a name="inline-hashtables"></a><span data-ttu-id="aacda-212">Infogad hash</span><span class="sxs-lookup"><span data-stu-id="aacda-212">Inline hashtables</span></span>

<span data-ttu-id="aacda-213">När du definierar en hash-tabellen på en rad kan du avgränsa nyckel/värde-par med ett semikolon.</span><span class="sxs-lookup"><span data-stu-id="aacda-213">When you're defining a hashtable on one line, you can separate the key/value pairs with a semicolon.</span></span>

```powershell
$person = @{ name = 'kevin'; age = 36; }
```

<span data-ttu-id="aacda-214">Detta är praktiskt om du skapar dem i en pipe.</span><span class="sxs-lookup"><span data-stu-id="aacda-214">This will come in handy if you're creating them on the pipe.</span></span>

### <a name="custom-expressions-in-common-pipeline-commands"></a><span data-ttu-id="aacda-215">Anpassade uttryck i vanliga pipeline-kommandon</span><span class="sxs-lookup"><span data-stu-id="aacda-215">Custom expressions in common pipeline commands</span></span>

<span data-ttu-id="aacda-216">Det finns några cmdletar som stöder användningen av hash för att skapa anpassade eller beräknade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="aacda-216">There are a few cmdlets that support the use of hashtables to create custom or calculated properties.</span></span> <span data-ttu-id="aacda-217">Du ser ofta detta med `Select-Object` och `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="aacda-217">You commonly see this with `Select-Object` and `Format-Table`.</span></span> <span data-ttu-id="aacda-218">Hash har en särskild syntax som ser ut så här när den är helt expanderad.</span><span class="sxs-lookup"><span data-stu-id="aacda-218">The hashtables have a special syntax that looks like this when fully expanded.</span></span>

```powershell
$property = @{
    name = 'totalSpaceGB'
    expression = { ($_.used + $_.free) / 1GB }
}
```

<span data-ttu-id="aacda-219">`name`Är vad cmdleten skulle märka den kolumnen.</span><span class="sxs-lookup"><span data-stu-id="aacda-219">The `name` is what the cmdlet would label that column.</span></span> <span data-ttu-id="aacda-220">`expression`Är ett skript block som körs där `$_` är värdet för objektet i pipe.</span><span class="sxs-lookup"><span data-stu-id="aacda-220">The `expression` is a script block that is executed where `$_` is the value of the object on the pipe.</span></span> <span data-ttu-id="aacda-221">Här är skriptet i praktiken:</span><span class="sxs-lookup"><span data-stu-id="aacda-221">Here is that script in action:</span></span>

```powershell
$drives = Get-PSDrive | Where Used
$drives | Select-Object -Properties name, $property

Name     totalSpaceGB
----     ------------
C    238.472652435303
```

<span data-ttu-id="aacda-222">Jag placerade det i en variabel, men det kan enkelt definieras infogat och du kan förkorta `name` till `n` och `expression` `e` samtidigt när du befinner dig.</span><span class="sxs-lookup"><span data-stu-id="aacda-222">I placed that in a variable but it could easily be defined inline and you can shorten `name` to `n` and `expression` to `e` while you're at it.</span></span>

```powershell
$drives | Select-Object -properties name, @{n='totalSpaceGB';e={($_.used + $_.free) / 1GB}}
```

<span data-ttu-id="aacda-223">Jag vill inte veta hur lång tid det tar för kommandon och ger ofta vissa dåliga beteenden som jag inte kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="aacda-223">I personally don't like how long that makes commands and it often promotes some bad behaviors that I won't get into.</span></span> <span data-ttu-id="aacda-224">Jag vill förmodligen skapa en ny hash-grupp eller `pscustomobject` med alla fält och egenskaper i stället för att använda den här metoden i skript.</span><span class="sxs-lookup"><span data-stu-id="aacda-224">I'm more likely to create a new hashtable or `pscustomobject` with all the fields and properties that I want instead of using this approach in scripts.</span></span> <span data-ttu-id="aacda-225">Men det finns en massa kod som gör det så att du kan vara medveten om det.</span><span class="sxs-lookup"><span data-stu-id="aacda-225">But there's a lot of code out there that does this so I wanted you to be aware of it.</span></span> <span data-ttu-id="aacda-226">Jag pratar om att skapa en `pscustomobject` senare version.</span><span class="sxs-lookup"><span data-stu-id="aacda-226">I talk about creating a `pscustomobject` later on.</span></span>

### <a name="custom-sort-expression"></a><span data-ttu-id="aacda-227">Anpassat sorterings uttryck</span><span class="sxs-lookup"><span data-stu-id="aacda-227">Custom sort expression</span></span>

<span data-ttu-id="aacda-228">Det är enkelt att sortera en samling om objekten har de data som du vill sortera på.</span><span class="sxs-lookup"><span data-stu-id="aacda-228">It's easy to sort a collection if the objects have the data that you want to sort on.</span></span> <span data-ttu-id="aacda-229">Du kan antingen lägga till data i objektet innan du sorterar det eller skapar ett anpassat uttryck för `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="aacda-229">You can either add the data to the object before you sort it or create a custom expression for `Sort-Object`.</span></span>

```powershell
Get-ADUser | Sort-Object -Parameter @{ e={ Get-TotalSales $_.Name } }
```

<span data-ttu-id="aacda-230">I det här exemplet tar du en lista med användare och använder en anpassad cmdlet för att få ytterligare information för sorteringen.</span><span class="sxs-lookup"><span data-stu-id="aacda-230">In this example I'm taking a list of users and using some custom cmdlet to get additional information just for the sort.</span></span>

#### <a name="sort-a-list-of-hashtables"></a><span data-ttu-id="aacda-231">Sortera en lista över hash</span><span class="sxs-lookup"><span data-stu-id="aacda-231">Sort a list of Hashtables</span></span>

<span data-ttu-id="aacda-232">Om du har en lista över hash som du vill sortera, ser du att de `Sort-Object` inte behandlar dina nycklar som egenskaper.</span><span class="sxs-lookup"><span data-stu-id="aacda-232">If you have a list of hashtables that you want to sort, you'll find that the `Sort-Object` doesn't treat your keys as properties.</span></span> <span data-ttu-id="aacda-233">Vi kan få en tur genom att använda ett anpassat sorterings uttryck.</span><span class="sxs-lookup"><span data-stu-id="aacda-233">We can get a round that by using a custom sort expression.</span></span>

```powershell
$data = @(
    @{name='a'}
    @{name='c'}
    @{name='e'}
    @{name='f'}
    @{name='d'}
    @{name='b'}
)

$data | Sort-Object -Property @{e={$_.name}}
```

## <a name="splatting-hashtables-at-cmdlets"></a><span data-ttu-id="aacda-234">Ihopbuntning-hash vid cmdletar</span><span class="sxs-lookup"><span data-stu-id="aacda-234">Splatting hashtables at cmdlets</span></span>

<span data-ttu-id="aacda-235">Det här är en av mina favorit saker om hash som många människor inte kan upptäcka tidigt på.</span><span class="sxs-lookup"><span data-stu-id="aacda-235">This is one of my favorite things about hashtables that many people don't discover early on.</span></span>
<span data-ttu-id="aacda-236">Tanken är att i stället för att tillhandahålla alla egenskaper till en cmdlet på en rad kan du i stället paketera dem i en hash-regel först.</span><span class="sxs-lookup"><span data-stu-id="aacda-236">The idea is that instead of providing all the properties to a cmdlet on one line, you can instead pack them into a hashtable first.</span></span> <span data-ttu-id="aacda-237">Sedan kan du ge hash-tabellen till funktionen på ett särskilt sätt.</span><span class="sxs-lookup"><span data-stu-id="aacda-237">Then you can give the hashtable to the function in a special way.</span></span>
<span data-ttu-id="aacda-238">Här är ett exempel på hur du skapar ett DHCP-scope på vanligt sätt.</span><span class="sxs-lookup"><span data-stu-id="aacda-238">Here is an example of creating a DHCP scope the normal way.</span></span>

```powershell
Add-DhcpServerv4Scope -Name 'TestNetwork' -StartRange'10.0.0.2' -EndRange '10.0.0.254' -SubnetMask '255.255.255.0' -Description 'Network for testlab A' -LeaseDuration (New-TimeSpan -Days 8) -Type "Both"
```

<span data-ttu-id="aacda-239">Utan att använda [ihopbuntning][]måste alla dessa saker definieras på en enda rad.</span><span class="sxs-lookup"><span data-stu-id="aacda-239">Without using [splatting][], all those things need to be defined on a single line.</span></span> <span data-ttu-id="aacda-240">Den rullar antingen bort från skärmen eller kommer att figursättas där det någonsin tycks som det ska.</span><span class="sxs-lookup"><span data-stu-id="aacda-240">It either scrolls off the screen or will wrap where ever it feels like.</span></span> <span data-ttu-id="aacda-241">Jämför nu med ett kommando som använder ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="aacda-241">Now compare that to a command that uses splatting.</span></span>

```powershell
$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    SubnetMask  = '255.255.255.0'
    Description = 'Network for testlab A'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}
Add-DhcpServerv4Scope @DHCPScope
```

<span data-ttu-id="aacda-242">Användningen av- `@` tecknet i stället för `$` är vad som anropar åtgärden splat.</span><span class="sxs-lookup"><span data-stu-id="aacda-242">The use of the `@` sign instead of the `$` is what invokes the splat operation.</span></span>

<span data-ttu-id="aacda-243">Ta en stund till att uppskatta hur enkelt det är att läsa.</span><span class="sxs-lookup"><span data-stu-id="aacda-243">Just take a moment to appreciate how easy that example is to read.</span></span> <span data-ttu-id="aacda-244">De är exakt samma kommando med samma värden.</span><span class="sxs-lookup"><span data-stu-id="aacda-244">They are the exact same command with all the same values.</span></span> <span data-ttu-id="aacda-245">Den andra är enklare att förstå och fortsätta att gå vidare.</span><span class="sxs-lookup"><span data-stu-id="aacda-245">The second one is easier to understand and maintain going forward.</span></span>

<span data-ttu-id="aacda-246">Jag använder ihopbuntning när kommandot är för långt.</span><span class="sxs-lookup"><span data-stu-id="aacda-246">I use splatting anytime the command gets too long.</span></span> <span data-ttu-id="aacda-247">Jag definierar för länge för att det ska gå att rulla åt fönstret.</span><span class="sxs-lookup"><span data-stu-id="aacda-247">I define too long as causing my window to scroll right.</span></span> <span data-ttu-id="aacda-248">Om jag träffar tre egenskaper för en funktion, är strider att jag skriver om den med en splatted-hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-248">If I hit three properties for a function, odds are that I'll rewrite it using a splatted hashtable.</span></span>

### <a name="splatting-for-optional-parameters"></a><span data-ttu-id="aacda-249">Ihopbuntning för valfria parametrar</span><span class="sxs-lookup"><span data-stu-id="aacda-249">Splatting for optional parameters</span></span>

<span data-ttu-id="aacda-250">Ett av de vanligaste sätten att använda ihopbuntning är att hantera valfria parametrar som kommer från någon annan plats i skriptet.</span><span class="sxs-lookup"><span data-stu-id="aacda-250">One of the most common ways I use splatting is to deal with optional parameters that come from some place else in my script.</span></span> <span data-ttu-id="aacda-251">Anta att jag har en funktion som omsluter ett `Get-CIMInstance` samtal som har ett valfritt `$Credential` argument.</span><span class="sxs-lookup"><span data-stu-id="aacda-251">Let's say I have a function that wraps a `Get-CIMInstance` call that has an optional `$Credential` argument.</span></span>

```powershell
$CIMParams = @{
    ClassName = 'Win32_Bios'
    ComputerName = $ComputerName
}

if($Credential)
{
    $CIMParams.Credential = $Credential
}

Get-CIMInstance @CIMParams
```

<span data-ttu-id="aacda-252">Jag börjar genom att skapa min hash-tabell med vanliga parametrar.</span><span class="sxs-lookup"><span data-stu-id="aacda-252">I start by creating my hashtable with common parameters.</span></span> <span data-ttu-id="aacda-253">Sedan lägger jag till den `$Credential` om den finns.</span><span class="sxs-lookup"><span data-stu-id="aacda-253">Then I add the `$Credential` if it exists.</span></span>
<span data-ttu-id="aacda-254">Eftersom jag använder ihopbuntning här behöver jag bara anropa `Get-CIMInstance` i min kod en gång.</span><span class="sxs-lookup"><span data-stu-id="aacda-254">Because I'm using splatting here, I only need to have the call to `Get-CIMInstance` in my code once.</span></span> <span data-ttu-id="aacda-255">Det här design mönstret är mycket rent och kan hantera många valfria parametrar enkelt.</span><span class="sxs-lookup"><span data-stu-id="aacda-255">This design pattern is very clean and can handle lots of optional parameters easily.</span></span>

<span data-ttu-id="aacda-256">För att vara rättvist kan du skriva kommandon för att tillåta `$null` värden för parametrar.</span><span class="sxs-lookup"><span data-stu-id="aacda-256">To be fair, you could write your commands to allow `$null` values for parameters.</span></span> <span data-ttu-id="aacda-257">Du har precis inte alltid kontroll över de andra kommandon som du ringer.</span><span class="sxs-lookup"><span data-stu-id="aacda-257">You just don't always have control over the other commands you're calling.</span></span>

### <a name="multiple-splats"></a><span data-ttu-id="aacda-258">Flera splats</span><span class="sxs-lookup"><span data-stu-id="aacda-258">Multiple splats</span></span>

<span data-ttu-id="aacda-259">Du kan splat flera hash till samma cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aacda-259">You can splat multiple hashtables to the same cmdlet.</span></span> <span data-ttu-id="aacda-260">Om vi besöker vårt ursprungliga ihopbuntning-exempel:</span><span class="sxs-lookup"><span data-stu-id="aacda-260">If we revisit our original splatting example:</span></span>

```powershell
$Common = @{
    SubnetMask  = '255.255.255.0'
    LeaseDuration = (New-TimeSpan -Days 8)
    Type = "Both"
}

$DHCPScope = @{
    Name        = 'TestNetwork'
    StartRange  = '10.0.0.2'
    EndRange    = '10.0.0.254'
    Description = 'Network for testlab A'
}

Add-DhcpServerv4Scope @DHCPScope @Common
```

<span data-ttu-id="aacda-261">Jag använder den här metoden när jag har en gemensam uppsättning parametrar som jag skickar till flera kommandon.</span><span class="sxs-lookup"><span data-stu-id="aacda-261">I'll use this method when I have a common set of parameters that I'm passing to lots of commands.</span></span>

### <a name="splatting-for-clean-code"></a><span data-ttu-id="aacda-262">Ihopbuntning för ren kod</span><span class="sxs-lookup"><span data-stu-id="aacda-262">Splatting for clean code</span></span>

<span data-ttu-id="aacda-263">Det finns inget fel med ihopbuntning en enda parameter om du gör kod rensning.</span><span class="sxs-lookup"><span data-stu-id="aacda-263">There's nothing wrong with splatting a single parameter if makes you code cleaner.</span></span>

```powershell
$log = @{Path = '.\logfile.log'}
Add-Content "logging this command" @log
```

### <a name="splatting-executables"></a><span data-ttu-id="aacda-264">Körbara ihopbuntning</span><span class="sxs-lookup"><span data-stu-id="aacda-264">Splatting executables</span></span>

<span data-ttu-id="aacda-265">Ihopbuntning fungerar även på vissa körbara filer som använder en `/param:value` syntax.</span><span class="sxs-lookup"><span data-stu-id="aacda-265">Splatting also works on some executables that use a `/param:value` syntax.</span></span> <span data-ttu-id="aacda-266">`Robocopy.exe`har till exempel vissa parametrar som detta.</span><span class="sxs-lookup"><span data-stu-id="aacda-266">`Robocopy.exe`, for example, has some parameters like this.</span></span>

```powershell
$robo = @{R=1;W=1;MT=8}
robocopy source destination @robo
```

<span data-ttu-id="aacda-267">Jag vet inte att det är allt som är användbart, men jag hittade det intressant.</span><span class="sxs-lookup"><span data-stu-id="aacda-267">I don't know that this is all that useful, but I found it interesting.</span></span>

## <a name="adding-hashtables"></a><span data-ttu-id="aacda-268">Lägger till hash</span><span class="sxs-lookup"><span data-stu-id="aacda-268">Adding hashtables</span></span>

<span data-ttu-id="aacda-269">Hash stöder addition-operatorn för att kombinera två hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-269">Hashtables support the addition operator to combine two hashtables.</span></span>

```powershell
$person += @{Zip = '78701'}
```

<span data-ttu-id="aacda-270">Detta fungerar bara om de två hash inte delar en nyckel.</span><span class="sxs-lookup"><span data-stu-id="aacda-270">This only works if the two hashtables don't share a key.</span></span>

## <a name="nested-hashtables"></a><span data-ttu-id="aacda-271">Kapslade hash</span><span class="sxs-lookup"><span data-stu-id="aacda-271">Nested hashtables</span></span>

<span data-ttu-id="aacda-272">Vi kan använda hash som värden i en hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-272">We can use hashtables as values inside a hashtable.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}
$person.location = @{}
$person.location.city = 'Austin'
$person.location.state = 'TX'
```

<span data-ttu-id="aacda-273">Jag startade med en grundläggande hash-enhet som innehåller två nycklar.</span><span class="sxs-lookup"><span data-stu-id="aacda-273">I started with a basic hashtable containing two keys.</span></span> <span data-ttu-id="aacda-274">Jag har lagt till en nyckel `location` med namnet med en tom hash-nyckel.</span><span class="sxs-lookup"><span data-stu-id="aacda-274">I added a key called `location` with an empty hashtable.</span></span> <span data-ttu-id="aacda-275">Sedan lade jag till de sista två objekten i den hash-tabellen `location` .</span><span class="sxs-lookup"><span data-stu-id="aacda-275">Then I added the last two items to that `location` hashtable.</span></span> <span data-ttu-id="aacda-276">Vi kan göra detta alla infogade.</span><span class="sxs-lookup"><span data-stu-id="aacda-276">We can do this all inline too.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
    location = @{
        city  = 'Austin'
        state = 'TX'
    }
}
```

<span data-ttu-id="aacda-277">Detta skapar samma hash-typ som vi såg ovan och kan komma åt egenskaperna på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="aacda-277">This creates the same hashtable that we saw above and can access the properties the same way.</span></span>

```powershell
$person.location.city
Austin
```

<span data-ttu-id="aacda-278">Det finns många sätt att närma dig strukturen för dina objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-278">There are many ways to approach the structure of your objects.</span></span> <span data-ttu-id="aacda-279">Här är ett andra sätt att titta på en kapslad hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-279">Here is a second way to look at a nested hashtable.</span></span>

```powershell
$people = @{
    Kevin = @{
        age  = 36
        city = 'Austin'
    }
    Alex = @{
        age  = 9
        city = 'Austin'
    }
}
```

<span data-ttu-id="aacda-280">Detta blandar konceptet med att använda hash som en samling objekt och en samling egenskaper.</span><span class="sxs-lookup"><span data-stu-id="aacda-280">This mixes the concept of using hashtables as a collection of objects and a collection of properties.</span></span> <span data-ttu-id="aacda-281">Värdena är fortfarande lätta att komma åt även när de är kapslade med den metod som du föredrar.</span><span class="sxs-lookup"><span data-stu-id="aacda-281">The values are still easy to access even when they're nested using whatever approach you prefer.</span></span>

```powershell
PS> $people.kevin.age
36
PS> $people.kevin['city']
Austin
PS> $people['Alex'].age
9
PS> $people['Alex']['City']
Austin
```

<span data-ttu-id="aacda-282">Jag brukar använda egenskapen dot när jag behandlar den som en egenskap.</span><span class="sxs-lookup"><span data-stu-id="aacda-282">I tend to use the dot property when I'm treating it like a property.</span></span> <span data-ttu-id="aacda-283">Det är vanligt att jag har definierat statiskt i min kod och jag vet att de inte är på huvud sidan.</span><span class="sxs-lookup"><span data-stu-id="aacda-283">Those are generally things I've defined statically in my code and I know them off the top of my head.</span></span> <span data-ttu-id="aacda-284">Om jag behöver gå igenom listan eller program mässigt komma åt nycklarna använder jag hakparenteser för att ange nyckel namnet.</span><span class="sxs-lookup"><span data-stu-id="aacda-284">If I need to walk the list or programmatically access the keys, I use the brackets to provide the key name.</span></span>

```powershell
foreach($name in $people.keys)
{
    $person = $people[$name]
    '{0}, age {1}, is in {2}' -f $name, $person.age, $person.city
}
```

<span data-ttu-id="aacda-285">Med möjligheten att kapsla hash får du stor flexibilitet och alternativ.</span><span class="sxs-lookup"><span data-stu-id="aacda-285">Having the ability to nest hashtables gives you a lot of flexibility and options.</span></span>

### <a name="looking-at-nested-hashtables"></a><span data-ttu-id="aacda-286">Titta på kapslade hash</span><span class="sxs-lookup"><span data-stu-id="aacda-286">Looking at nested hashtables</span></span>

<span data-ttu-id="aacda-287">Så snart du börjar kapsla in hash kommer du att behöva ett enkelt sätt att titta på dem från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="aacda-287">As soon as you start nesting hashtables, you're going to need an easy way to look at them from the console.</span></span> <span data-ttu-id="aacda-288">Om jag tar den sista hash-enheten får jag en utmatning som ser ut så här och den går bara så djup:</span><span class="sxs-lookup"><span data-stu-id="aacda-288">If I take that last hashtable, I get an output that looks like this and it only goes so deep:</span></span>

```powershell
PS> $people
Name                           Value
----                           -----
Kevin                          {age, city}
Alex                           {age, city}
```

<span data-ttu-id="aacda-289">Kommandot gå till för att titta på dessa saker är att `ConvertTo-JSON` det är mycket rent och jag använder ofta JSON på andra saker.</span><span class="sxs-lookup"><span data-stu-id="aacda-289">My go to command for looking at these things is `ConvertTo-JSON` because it's very clean and I frequently use JSON on other things.</span></span>

```powershell
PS> $people | ConvertTo-Json
{
    "Kevin":  {
                "age":  36,
                "city":  "Austin"
            },
    "Alex":  {
                "age":  9,
                "city":  "Austin"
            }
}
```

<span data-ttu-id="aacda-290">Även om du inte vet JSON bör du kunna se vad du letar efter.</span><span class="sxs-lookup"><span data-stu-id="aacda-290">Even if you don't know JSON, you should be able to see what you're looking for.</span></span> <span data-ttu-id="aacda-291">Det finns ett- `Format-Custom` kommando för strukturerade data, t. ex. om du fortfarande vill ha JSON-vyn bättre.</span><span class="sxs-lookup"><span data-stu-id="aacda-291">There's a `Format-Custom` command for structured data like this but I still like the JSON view better.</span></span>

## <a name="creating-objects"></a><span data-ttu-id="aacda-292">Skapa objekt</span><span class="sxs-lookup"><span data-stu-id="aacda-292">Creating objects</span></span>

<span data-ttu-id="aacda-293">Ibland behöver du bara ha ett objekt och använda en hash-hash för att hålla egenskaper som inte får jobbet gjort.</span><span class="sxs-lookup"><span data-stu-id="aacda-293">Sometimes you just need to have an object and using a hashtable to hold properties just isn't getting the job done.</span></span> <span data-ttu-id="aacda-294">Oftast vill du se nycklarna som kolumn namn.</span><span class="sxs-lookup"><span data-stu-id="aacda-294">Most commonly you want to see the keys as column names.</span></span> <span data-ttu-id="aacda-295">En `pscustomobject` gör det enkelt.</span><span class="sxs-lookup"><span data-stu-id="aacda-295">A `pscustomobject` makes that easy.</span></span>

```powershell
$person = [pscustomobject]@{
    name = 'Kevin'
    age  = 36
}

$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="aacda-296">Även om du inte skapar den `pscustomobject` från början, kan du alltid skicka den senare när det behövs.</span><span class="sxs-lookup"><span data-stu-id="aacda-296">Even if you don't create it as a `pscustomobject` initially, you can always cast it later when needed.</span></span>

```powershell
$person = @{
    name = 'Kevin'
    age  = 36
}

[pscustomobject]$person

name  age
----  ---
Kevin  36
```

<span data-ttu-id="aacda-297">Jag har redan en detaljerad uppskrivning för [PSCustomObject][] som du bör läsa efter det här.</span><span class="sxs-lookup"><span data-stu-id="aacda-297">I already have detailed write-up for [pscustomobject][] that you should go read after this one.</span></span> <span data-ttu-id="aacda-298">Det bygger på en stor mängd saker som du har lärt dig här.</span><span class="sxs-lookup"><span data-stu-id="aacda-298">It builds on a lot of the things learned here.</span></span>

## <a name="reading-and-writing-hashtables-to-file"></a><span data-ttu-id="aacda-299">Läser och skriver hash till fil</span><span class="sxs-lookup"><span data-stu-id="aacda-299">Reading and writing hashtables to file</span></span>

### <a name="saving-to-csv"></a><span data-ttu-id="aacda-300">Sparar till CSV</span><span class="sxs-lookup"><span data-stu-id="aacda-300">Saving to CSV</span></span>

<span data-ttu-id="aacda-301">Kämpar med att hämta en hash-fil för att spara till en CSV-fil är ett av de problem som jag hade refererat till ovan.</span><span class="sxs-lookup"><span data-stu-id="aacda-301">Struggling with getting a hashtable to save to a CSV is one of the difficulties that I was referring to above.</span></span> <span data-ttu-id="aacda-302">Konvertera din hash-post till en så `pscustomobject` sparas den korrekt till CSV.</span><span class="sxs-lookup"><span data-stu-id="aacda-302">Convert your hashtable to a `pscustomobject` and it will save correctly to CSV.</span></span> <span data-ttu-id="aacda-303">Det hjälper om du börjar med en `pscustomobject` så att kolumn ordningen bevaras.</span><span class="sxs-lookup"><span data-stu-id="aacda-303">It helps if you start with a `pscustomobject` so the column order is preserved.</span></span> <span data-ttu-id="aacda-304">Men du kan omvandla det till en `pscustomobject` infogad, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="aacda-304">But you can cast it to a `pscustomobject` inline if needed.</span></span>

```powershell
$person | ForEach-Object{ [pscustomobject]$_ } | Export-CSV -Path $path
```

<span data-ttu-id="aacda-305">Kolla återigen in My Write-in using a [PSCustomObject][].</span><span class="sxs-lookup"><span data-stu-id="aacda-305">Again, check out my write-up on using a [pscustomobject][].</span></span>

### <a name="saving-a-nested-hashtable-to-file"></a><span data-ttu-id="aacda-306">Spara en kapslad hash-fil i filen</span><span class="sxs-lookup"><span data-stu-id="aacda-306">Saving a nested hashtable to file</span></span>

<span data-ttu-id="aacda-307">Om jag behöver spara en kapslad hash-fil till en fil och sedan läsa in den igen, använder jag JSON-cmdletar för att göra det.</span><span class="sxs-lookup"><span data-stu-id="aacda-307">If I need to save a nested hashtable to a file and then read it back in again, I use the JSON cmdlets to do it.</span></span>

```powershell
$people | ConvertTo-JSON | Set-Content -Path $path
$people = Get-Content -Path $path -Raw | ConvertFrom-JSON
```

<span data-ttu-id="aacda-308">Det finns två viktiga punkter om den här metoden.</span><span class="sxs-lookup"><span data-stu-id="aacda-308">There are two important points about this method.</span></span> <span data-ttu-id="aacda-309">Det första är att JSON skrivs ut flera rader så jag måste använda `-Raw` alternativet för att läsa tillbaka det till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="aacda-309">First is that the JSON is written out multiline so I need to use the `-Raw` option to read it back into a single string.</span></span> <span data-ttu-id="aacda-310">Det andra är att det importerade objektet inte längre är ett `[hashtable]` .</span><span class="sxs-lookup"><span data-stu-id="aacda-310">The Second is that the imported object is no longer a `[hashtable]`.</span></span> <span data-ttu-id="aacda-311">Det är nu en `[pscustomobject]` och som kan orsaka problem om du inte förväntar dig.</span><span class="sxs-lookup"><span data-stu-id="aacda-311">It's now a `[pscustomobject]` and that can cause issues if you don't expect it.</span></span>

<span data-ttu-id="aacda-312">Titta efter djupt kapslade hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-312">Watch for deeply-nested hashtables.</span></span> <span data-ttu-id="aacda-313">När du konverterar den till JSON kanske du inte får de resultat du förväntar dig.</span><span class="sxs-lookup"><span data-stu-id="aacda-313">When you convert it to JSON you might not get the results you expect.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json

{
  "a": {
    "b": {
      "c": "System.Collections.Hashtable"
    }
  }
}
```

<span data-ttu-id="aacda-314">Använd **djup** parameter för att se till att du har expanderat alla kapslade hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-314">Use **Depth** parameter to ensure that you have expanded all the nested hashtables.</span></span>

```powershell
@{ a = @{ b = @{ c = @{ d = "e" }}}} | ConvertTo-Json -Depth 3

{
  "a": {
    "b": {
      "c": {
        "d": "e"
      }
    }
  }
}
```

<span data-ttu-id="aacda-315">Om du behöver det för att `[hashtable]` Importera måste du använda- `Export-CliXml` och- `Import-CliXml` kommandona.</span><span class="sxs-lookup"><span data-stu-id="aacda-315">If you need it to be a `[hashtable]` on import, then you need to use the `Export-CliXml` and `Import-CliXml` commands.</span></span>

### <a name="converting-json-to-hashtable"></a><span data-ttu-id="aacda-316">Konvertera JSON till hash-sträng</span><span class="sxs-lookup"><span data-stu-id="aacda-316">Converting JSON to Hashtable</span></span>

<span data-ttu-id="aacda-317">Om du behöver konvertera JSON till en finns `[hashtable]` det ett sätt som jag känner till för att göra det med [JavaScriptSerializer][] i .net.</span><span class="sxs-lookup"><span data-stu-id="aacda-317">If you need to convert JSON to a `[hashtable]`, there's one way that I know of to do it with the [JavaScriptSerializer][] in .NET.</span></span>

```powershell
[Reflection.Assembly]::LoadWithPartialName("System.Web.Script.Serialization")
$JSSerializer = [System.Web.Script.Serialization.JavaScriptSerializer]::new()
$JSSerializer.Deserialize($json,'Hashtable')
```

<span data-ttu-id="aacda-318">Från och med PowerShell V6 använder JSON-stödet NewtonSoft-JSON.NET och lägger till hash-stöd.</span><span class="sxs-lookup"><span data-stu-id="aacda-318">Beginning in PowerShell v6, JSON support uses the NewtonSoft JSON.NET and adds hashtable support.</span></span>

```powershell
'{ "a": "b" }' | ConvertFrom-Json -AsHashtable

Name      Value
----      -----
a         b
```

<span data-ttu-id="aacda-319">PowerShell 6,2 lade till **djup** parametern till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="aacda-319">PowerShell 6.2 added the **Depth** parameter to `ConvertFrom-Json`.</span></span> <span data-ttu-id="aacda-320">Standard **djupet** är 1024.</span><span class="sxs-lookup"><span data-stu-id="aacda-320">The default **Depth** is 1024.</span></span>

### <a name="reading-directly-from-a-file"></a><span data-ttu-id="aacda-321">Läsa direkt från en fil</span><span class="sxs-lookup"><span data-stu-id="aacda-321">Reading directly from a file</span></span>

<span data-ttu-id="aacda-322">Om du har en fil som innehåller en hash-tabell med PowerShell-syntax, finns det ett sätt att importera den direkt.</span><span class="sxs-lookup"><span data-stu-id="aacda-322">If you have a file that contains a hashtable using PowerShell syntax, there's a way to import it directly.</span></span>

```powershell
$content = Get-Content -Path $Path -Raw -ErrorAction Stop
$scriptBlock = [scriptblock]::Create( $content )
$scriptBlock.CheckRestrictedLanguage( $allowedCommands, $allowedVariables, $true )
$hashtable = ( & $scriptBlock )
```

<span data-ttu-id="aacda-323">Innehållet i filen importeras till en `scriptblock` och kontrollerar sedan att det inte finns några andra PowerShell-kommandon i den innan den körs.</span><span class="sxs-lookup"><span data-stu-id="aacda-323">It imports the contents of the file into a `scriptblock`, then checks to make sure it doesn't have any other PowerShell commands in it before it executes it.</span></span>

<span data-ttu-id="aacda-324">Visste du att ett modul manifest (psd1-filen) bara är en hash-modul?</span><span class="sxs-lookup"><span data-stu-id="aacda-324">On that note, did you know that a module manifest (the psd1 file) is just a hashtable?</span></span>

## <a name="keys-can-be-any-object"></a><span data-ttu-id="aacda-325">Nycklar kan vara valfritt objekt</span><span class="sxs-lookup"><span data-stu-id="aacda-325">Keys can be any object</span></span>

<span data-ttu-id="aacda-326">De flesta av tiden är nycklarna bara strängar.</span><span class="sxs-lookup"><span data-stu-id="aacda-326">Most of the time, the keys are just strings.</span></span> <span data-ttu-id="aacda-327">Vi kan lägga till citat tecken runt vad som helst och göra den till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="aacda-327">So we can put quotes around anything and make it a key.</span></span>

```powershell
$person = @{
    'full name' = 'Kevin Marquette'
    '#' = 3978
}
$person['full name']
```

<span data-ttu-id="aacda-328">Du kan göra lite udda saker som du kanske inte har realiserat.</span><span class="sxs-lookup"><span data-stu-id="aacda-328">You can do some odd things that you may not have realized you could do.</span></span>

```powershell
$person.'full name'

$key = 'full name'
$person.$key
```

<span data-ttu-id="aacda-329">Bara för att du ska kunna göra något, betyder det inte att du borde.</span><span class="sxs-lookup"><span data-stu-id="aacda-329">Just because you can do something, it doesn't mean that you should.</span></span> <span data-ttu-id="aacda-330">Det sista ser bara ut som ett fel som väntar på att hända och skulle vara lätt att förstå för alla som läser koden.</span><span class="sxs-lookup"><span data-stu-id="aacda-330">That last one just looks like a bug waiting to happen and would be easily misunderstood by anyone reading your code.</span></span>

<span data-ttu-id="aacda-331">Tekniskt sett behöver din nyckel inte vara en sträng, men de är lättare att tänka på om du bara använder strängar.</span><span class="sxs-lookup"><span data-stu-id="aacda-331">Technically your key doesn't have to be a string but they're easier to think about if you only use strings.</span></span> <span data-ttu-id="aacda-332">Indexeringen fungerar dock inte bra med de komplexa nycklarna.</span><span class="sxs-lookup"><span data-stu-id="aacda-332">However, indexing doesn't work well with the complex keys.</span></span>

```powershell
$ht = @{ @(1,2,3) = "a" }
$ht

Name                           Value
----                           -----
{1, 2, 3}                      a
```

<span data-ttu-id="aacda-333">Att komma åt ett värde i hash-tabellen efter dess nyckel fungerar inte alltid.</span><span class="sxs-lookup"><span data-stu-id="aacda-333">Accessing a value in the hashtable by its key doesn't always work.</span></span> <span data-ttu-id="aacda-334">Exempel:</span><span class="sxs-lookup"><span data-stu-id="aacda-334">For example:</span></span>

```powershell
$key = $ht.keys[0]
$ht.$($key)
a
$ht[$key]
a
```

<span data-ttu-id="aacda-335">När nyckeln är en matris måste du omsluta `$key` variabeln i ett under uttryck så att den kan användas med member Access ()- `.` notation.</span><span class="sxs-lookup"><span data-stu-id="aacda-335">When the key is an array, you must wrap the `$key` variable in a subexpression so that it can be used with member access (`.`) notation.</span></span> <span data-ttu-id="aacda-336">Du kan också använda format för mat ris index ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="aacda-336">Or, you can use array index (`[]`) notation.</span></span>

## <a name="use-in-automatic-variables"></a><span data-ttu-id="aacda-337">Använd i automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="aacda-337">Use in automatic variables</span></span>

### <a name="psboundparameters"></a><span data-ttu-id="aacda-338">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="aacda-338">$PSBoundParameters</span></span>

<span data-ttu-id="aacda-339">[$PSBoundParameters] [] är en automatisk variabel som bara finns inuti kontexten för en funktion.</span><span class="sxs-lookup"><span data-stu-id="aacda-339">[$PSBoundParameters][] is an automatic variable that only exists inside the context of a function.</span></span>
<span data-ttu-id="aacda-340">Den innehåller alla parametrar som funktionen anropades med.</span><span class="sxs-lookup"><span data-stu-id="aacda-340">It contains all the parameters that the function was called with.</span></span> <span data-ttu-id="aacda-341">Detta är inte exakt en hash utan är tillräckligt nära så att du kan behandla den som en.</span><span class="sxs-lookup"><span data-stu-id="aacda-341">This isn't exactly a hashtable but close enough that you can treat it like one.</span></span>

<span data-ttu-id="aacda-342">Detta inkluderar att ta bort nycklar och ihopbuntning den till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="aacda-342">That includes removing keys and splatting it to other functions.</span></span> <span data-ttu-id="aacda-343">Ta en närmare titt på den här om du upptäcker att du skriver proxy-funktioner.</span><span class="sxs-lookup"><span data-stu-id="aacda-343">If you find yourself writing proxy functions, take a closer look at this one.</span></span>

<span data-ttu-id="aacda-344">Se [about_Automatic_Variables][] för mer information.</span><span class="sxs-lookup"><span data-stu-id="aacda-344">See [about_Automatic_Variables][] for more details.</span></span>

### <a name="psboundparameters-gotcha"></a><span data-ttu-id="aacda-345">PSBoundParameters information</span><span class="sxs-lookup"><span data-stu-id="aacda-345">PSBoundParameters gotcha</span></span>

<span data-ttu-id="aacda-346">En viktig sak att komma ihåg är att detta bara innehåller de värden som skickas som parametrar.</span><span class="sxs-lookup"><span data-stu-id="aacda-346">One important thing to remember is that this only includes the values that are passed in as parameters.</span></span> <span data-ttu-id="aacda-347">Om du även har parametrar med standardvärden men som inte skickas in av anroparen, `$PSBoundParameters` innehåller inte dessa värden.</span><span class="sxs-lookup"><span data-stu-id="aacda-347">If you also have parameters with default values but aren't passed in by the caller, `$PSBoundParameters` doesn't contain those values.</span></span> <span data-ttu-id="aacda-348">Detta är vanligt vis överblickat.</span><span class="sxs-lookup"><span data-stu-id="aacda-348">This is commonly overlooked.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="aacda-349">$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="aacda-349">$PSDefaultParameterValues</span></span>

<span data-ttu-id="aacda-350">Med den här automatiska variabeln kan du tilldela standardvärden till alla cmdletar utan att ändra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aacda-350">This automatic variable lets you assign default values to any cmdlet without changing the cmdlet.</span></span>
<span data-ttu-id="aacda-351">Ta en titt på det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="aacda-351">Take a look at this example.</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "UTF8"
```

<span data-ttu-id="aacda-352">Detta lägger till en post i `$PSDefaultParameterValues` hash-tabellen som anger `UTF8` som standardvärdet för `Out-File -Encoding` parametern.</span><span class="sxs-lookup"><span data-stu-id="aacda-352">This adds an entry to the `$PSDefaultParameterValues` hashtable that sets `UTF8` as the default value for the `Out-File -Encoding` parameter.</span></span> <span data-ttu-id="aacda-353">Detta är sessionsläge så att du kan placera den i din `$profile` .</span><span class="sxs-lookup"><span data-stu-id="aacda-353">This is session-specific so you should place it in your `$profile`.</span></span>

<span data-ttu-id="aacda-354">Jag använder det ofta för att före tilldela värden som jag anger ofta.</span><span class="sxs-lookup"><span data-stu-id="aacda-354">I use this often to pre-assign values that I type quite often.</span></span>

```powershell
$PSDefaultParameterValues[ "Connect-VIServer:Server" ] = 'VCENTER01.contoso.local'
```

<span data-ttu-id="aacda-355">Detta accepterar även jokertecken så att du kan ange värden i bulk.</span><span class="sxs-lookup"><span data-stu-id="aacda-355">This also accepts wildcards so you can set values in bulk.</span></span> <span data-ttu-id="aacda-356">Här följer några exempel på hur du kan använda det:</span><span class="sxs-lookup"><span data-stu-id="aacda-356">Here are some ways you can use that:</span></span>

```powershell
$PSDefaultParameterValues[ "Get-*:Verbose" ] = $true
$PSDefaultParameterValues[ "*:Credential" ] = Get-Credential
```

<span data-ttu-id="aacda-357">En mer djupgående analys finns i den här fantastiska artikeln om [automatiska standardinställningar][] av [Michael Sorens][].</span><span class="sxs-lookup"><span data-stu-id="aacda-357">For a more in-depth breakdown, see this great article on [Automatic Defaults][] by [Michael Sorens][].</span></span>

## <a name="regex-matches"></a><span data-ttu-id="aacda-358">Regex $Matches</span><span class="sxs-lookup"><span data-stu-id="aacda-358">Regex $Matches</span></span>

<span data-ttu-id="aacda-359">När du använder `-match` operatorn skapas en automatisk variabel `$matches` som heter med resultatet av matchningen.</span><span class="sxs-lookup"><span data-stu-id="aacda-359">When you use the `-match` operator, an automatic variable called `$matches` is created with the results of the match.</span></span> <span data-ttu-id="aacda-360">Om du har ett under uttryck i ditt regex visas även dessa underordnade matchningar.</span><span class="sxs-lookup"><span data-stu-id="aacda-360">If you have any sub expressions in your regex, those sub matches are also listed.</span></span>

```powershell
$message = 'My SSN is 123-45-6789.'

$message -match 'My SSN is (.+)\.'
$Matches[0]
$Matches[1]
```

### <a name="named-matches"></a><span data-ttu-id="aacda-361">Namngivna matchningar</span><span class="sxs-lookup"><span data-stu-id="aacda-361">Named matches</span></span>

<span data-ttu-id="aacda-362">Det här är en av mina favorit funktioner som de flesta personer inte känner till.</span><span class="sxs-lookup"><span data-stu-id="aacda-362">This is one of my favorite features that most people don't know about.</span></span> <span data-ttu-id="aacda-363">Om du använder en namngiven regex-matchning, kan du komma åt matchning efter namn på matchningarna.</span><span class="sxs-lookup"><span data-stu-id="aacda-363">If you use a named regex match, then you can access that match by name on the matches.</span></span>

```powershell
$message = 'My Name is Kevin and my SSN is 123-45-6789.'

if($message -match 'My Name is (?<Name>.+) and my SSN is (?<SSN>.+)\.')
{
    $Matches.Name
    $Matches.SSN
}
```

<span data-ttu-id="aacda-364">I exemplet ovan `(?<Name>.*)` är ett namngivet under uttryck.</span><span class="sxs-lookup"><span data-stu-id="aacda-364">In the example above, the `(?<Name>.*)` is a named sub expression.</span></span> <span data-ttu-id="aacda-365">Värdet placeras sedan i `$Matches.Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="aacda-365">This value is then placed in the `$Matches.Name` property.</span></span>

## <a name="group-object--ashashtable"></a><span data-ttu-id="aacda-366">Group-Object-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="aacda-366">Group-Object -AsHashtable</span></span>

<span data-ttu-id="aacda-367">En liten känd funktion i `Group-Object` är att den kan omvandla vissa data uppsättningar till en hash-mängd.</span><span class="sxs-lookup"><span data-stu-id="aacda-367">One little known feature of `Group-Object` is that it can turn some datasets into a hashtable for you.</span></span>

```powershell
Import-CSV $Path | Group-Object -AsHashtable -Property email
```

<span data-ttu-id="aacda-368">Varje rad läggs till i en hash-tabell och den angivna egenskapen används som nyckel för att komma åt den.</span><span class="sxs-lookup"><span data-stu-id="aacda-368">This will add each row into a hashtable and use the specified property as the key to access it.</span></span>

## <a name="copying-hashtables"></a><span data-ttu-id="aacda-369">Kopierar hash</span><span class="sxs-lookup"><span data-stu-id="aacda-369">Copying Hashtables</span></span>

<span data-ttu-id="aacda-370">En viktig sak att veta är att hash är objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-370">One important thing to know is that hashtables are objects.</span></span> <span data-ttu-id="aacda-371">Och varje variabel är bara en referens till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aacda-371">And each variable is just a reference to an object.</span></span> <span data-ttu-id="aacda-372">Det innebär att det tar mer arbete att skapa en giltig kopia av en hash-hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-372">This means that it takes more work to make a valid copy of a hashtable.</span></span>

### <a name="assigning-reference-types"></a><span data-ttu-id="aacda-373">Tilldela referens typer</span><span class="sxs-lookup"><span data-stu-id="aacda-373">Assigning reference types</span></span>

<span data-ttu-id="aacda-374">När du har en hash-adress och tilldelar den till en andra variabel pekar båda variablerna på samma hash.</span><span class="sxs-lookup"><span data-stu-id="aacda-374">When you have one hashtable and assign it to a second variable, both variables point to the same hashtable.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="aacda-375">Det innebär att de är desamma eftersom ändringar av värdena i samma ändrar även värdena i den andra.</span><span class="sxs-lookup"><span data-stu-id="aacda-375">This highlights that they're the same because altering the values in one will also alter the values in the other.</span></span> <span data-ttu-id="aacda-376">Detta gäller även när du skickar hash till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="aacda-376">This also applies when passing hashtables into other functions.</span></span> <span data-ttu-id="aacda-377">Om dessa funktioner gör ändringar i denna hash ändras även originalet.</span><span class="sxs-lookup"><span data-stu-id="aacda-377">If those functions make changes to that hashtable, your original is also altered.</span></span>

### <a name="shallow-copies-single-level"></a><span data-ttu-id="aacda-378">Ytliga kopior, en nivå</span><span class="sxs-lookup"><span data-stu-id="aacda-378">Shallow copies, single level</span></span>

<span data-ttu-id="aacda-379">Om vi har en enkel datahash som exemplet ovan kan vi använda `.Clone()` för att skapa en ytlig kopia.</span><span class="sxs-lookup"><span data-stu-id="aacda-379">If we have a simple hashtable like our example above, we can use `.Clone()` to make a shallow copy.</span></span>

```powershell
PS> $orig = @{name='orig'}
PS> $copy = $orig.Clone()
PS> $copy.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.name
PS> 'Orig: [{0}]' -f $orig.name

Copy: [copy]
Orig: [orig]
```

<span data-ttu-id="aacda-380">På så sätt kan vi göra några grundläggande ändringar av en som inte påverkar den andra.</span><span class="sxs-lookup"><span data-stu-id="aacda-380">This will allow us to make some basic changes to one that don't impact the other.</span></span>

### <a name="shallow-copies-nested"></a><span data-ttu-id="aacda-381">Ytliga kopior, kapslade</span><span class="sxs-lookup"><span data-stu-id="aacda-381">Shallow copies, nested</span></span>

<span data-ttu-id="aacda-382">Anledningen till att det kallas en ytlig kopia är att den bara kopierar bas nivå egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="aacda-382">The reason why it's called a shallow copy is because it only copies the base level properties.</span></span> <span data-ttu-id="aacda-383">Om en av dessa egenskaper är en referens typ (t. ex. en annan hash-adress) pekar dessa kapslade objekt fortfarande på varandra.</span><span class="sxs-lookup"><span data-stu-id="aacda-383">If one of those properties is a reference type (like another hashtable), then those nested objects will still point to each other.</span></span>

```powershell
PS> $orig = @{
        person=@{
            name='orig'
        }
    }
PS> $copy = $orig.Clone()
PS> $copy.person.name = 'copy'
PS> 'Copy: [{0}]' -f $copy.person.name
PS> 'Orig: [{0}]' -f $orig.person.name

Copy: [copy]
Orig: [copy]
```

<span data-ttu-id="aacda-384">Så du kan se att även om jag har klonat en hash-tabellen `person` .</span><span class="sxs-lookup"><span data-stu-id="aacda-384">So you can see that even though I cloned the hashtable, the reference to `person` wasn't cloned.</span></span> <span data-ttu-id="aacda-385">Vi behöver göra en djup kopia för att verkligen ha en andra hash som inte är länkad till den första.</span><span class="sxs-lookup"><span data-stu-id="aacda-385">We need to make a deep copy to truly have a second hashtable that isn't linked to the first.</span></span>

### <a name="deep-copies"></a><span data-ttu-id="aacda-386">Djupgående kopior</span><span class="sxs-lookup"><span data-stu-id="aacda-386">Deep copies</span></span>

<span data-ttu-id="aacda-387">Det finns ett par olika sätt att skapa en djup kopia av en hash-hash (och behålla den som en hash-hash).</span><span class="sxs-lookup"><span data-stu-id="aacda-387">There are a couple of ways to make a deep copy of a hashtable (and keep it as a hashtable).</span></span> <span data-ttu-id="aacda-388">Här är en funktion som använder PowerShell för att rekursivt skapa en djup kopia:</span><span class="sxs-lookup"><span data-stu-id="aacda-388">Here's a function using PowerShell to recursively create a deep copy:</span></span>

```powershell
function Get-DeepClone
{
    [CmdletBinding()]
    param(
        $InputObject
    )
    process
    {
        if($InputObject -is [hashtable]) {
            $clone = @{}
            foreach($key in $InputObject.keys)
            {
                $clone[$key] = Get-DeepClone $InputObject[$key]
            }
            return $clone
        } else {
            return $InputObject
        }
    }
}
```

<span data-ttu-id="aacda-389">Den hanterar inte andra referens typer eller matriser, men det är en lämplig start punkt.</span><span class="sxs-lookup"><span data-stu-id="aacda-389">It doesn't handle any other reference types or arrays, but it's a good starting point.</span></span>

<span data-ttu-id="aacda-390">Ett annat sätt är att använda .net för att deserialisera den med hjälp av **CliXml** som i den här funktionen:</span><span class="sxs-lookup"><span data-stu-id="aacda-390">Another way is to use .Net to deserialize it using **CliXml** like in this function:</span></span>

```powershell
function Get-DeepClone
{
    param(
        $InputObject
    )
    $TempCliXmlString = [System.Management.Automation.PSSerializer]::Serialize($obj, [int32]::MaxValue)
    return [System.Management.Automation.PSSerializer]::Deserialize($TempCliXmlString)
}
```

<span data-ttu-id="aacda-391">För mycket stora hash är avserialiserings funktionen snabbare när den skalas ut. Det finns dock några saker att tänka på när du använder den här metoden.</span><span class="sxs-lookup"><span data-stu-id="aacda-391">For extremely large hashtables, the deserializing function is faster as it scales out. However, there are some things to consider when using this method.</span></span> <span data-ttu-id="aacda-392">Eftersom den använder **CliXml** är det minnes intensivt och om du klonar enorma hash kan det vara ett problem.</span><span class="sxs-lookup"><span data-stu-id="aacda-392">Since it uses **CliXml**, it's memory intensive and if you are cloning huge hashtables, that might be a problem.</span></span> <span data-ttu-id="aacda-393">En annan begränsning av **CliXml** är att det finns en djup begränsning på 48.</span><span class="sxs-lookup"><span data-stu-id="aacda-393">Another limitation of the **CliXml** is there is a depth limitation of 48.</span></span> <span data-ttu-id="aacda-394">Om du har en hash-datahash med 48 lager av kapslade hash, kommer kloningen att Miss Miss och ingen hash-tabellen kommer att matas ut alls.</span><span class="sxs-lookup"><span data-stu-id="aacda-394">Meaning, if you have a hashtable with 48 layers of nested hashtables, the cloning will fail and no hashtable will be output at all.</span></span>

## <a name="anything-else"></a><span data-ttu-id="aacda-395">Något mer?</span><span class="sxs-lookup"><span data-stu-id="aacda-395">Anything else?</span></span>

<span data-ttu-id="aacda-396">Jag täckte mycket jord snabbt.</span><span class="sxs-lookup"><span data-stu-id="aacda-396">I covered a lot of ground quickly.</span></span> <span data-ttu-id="aacda-397">Min idé är att du kan sätta en ny eller förståelse för det bättre varje gång du läser det.</span><span class="sxs-lookup"><span data-stu-id="aacda-397">My hope is that you walk away leaning something new or understanding it better every time you read this.</span></span> <span data-ttu-id="aacda-398">Eftersom jag täckte det fullständiga spektrumet av den här funktionen finns det aspekter som bara kan gälla just nu.</span><span class="sxs-lookup"><span data-stu-id="aacda-398">Because I covered the full spectrum of this feature, there are aspects that just may not apply to you right now.</span></span> <span data-ttu-id="aacda-399">Det är perfekt OK och är en typ av förväntat beroende på hur mycket du arbetar med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aacda-399">That is perfectly OK and is kind of expected depending on how much you work with PowerShell.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[original version]: https://powershellexplained.com/2016-11-06-powershell-hashtable-everything-you-wanted-to-know-about/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[hash]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[hashtables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[lagringsmatriser]: /powershell/module/microsoft.powershell.core/about/about_arrays
[arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Testa det om prestanda är viktigt]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[If performance matters, test it]: https://github.com/PoshCode/PowerShellPracticeAndStyle/blob/master/Best-Practices/Performance.md
[ihopbuntning]: /powershell/module/microsoft.powershell.core/about/about_splatting
[splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[PSCustomObject]: everything-about-pscustomobject.md
[pscustomobject]: everything-about-pscustomobject.md
[JavaScriptSerializer]: /dotnet/api/system.web.script.serialization.javascriptserializer?view=netframework-4.8&preserve-view=true
[PSBoundParameters]: https://tommymaynard.com/the-psboundparameters-automatic-variable-2016/
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[Automatiska standardinställningar]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Automatic Defaults]: https://www.simple-talk.com/sysadmin/PowerShell/PowerShell-time-saver-automatic-defaults/
[Michael Sorens]: http://cleancode.sourceforge.net/wwwdoc/about.html
