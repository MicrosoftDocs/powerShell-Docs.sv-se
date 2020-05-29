---
title: Allt du ville veta om PSCustomObject
description: PSCustomObject är ett enkelt sätt att skapa strukturerade data.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: fbc8b5b6d2cfafaa75fa820f420762a1804074ac
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149847"
---
# <a name="everything-you-wanted-to-know-about-pscustomobject"></a><span data-ttu-id="a8f0c-103">Allt du ville veta om PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a8f0c-103">Everything you wanted to know about PSCustomObject</span></span>

<span data-ttu-id="a8f0c-104">`PSCustomObject`s är ett bra verktyg som du kan lägga till i ditt verktyg i PowerShell-verktyget.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-104">`PSCustomObject`s are a great tool to add into your PowerShell tool belt.</span></span> <span data-ttu-id="a8f0c-105">Vi börjar med grunderna och arbetar på vårt sätt i de mer avancerade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-105">Let's start with the basics and work our way into the more advanced features.</span></span> <span data-ttu-id="a8f0c-106">Idén bakom att använda en `PSCustomObject` är att skapa strukturerade data på ett enkelt sätt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-106">The idea behind using a `PSCustomObject` is to have a simple way to create structured data.</span></span> <span data-ttu-id="a8f0c-107">Ta en titt på det första exemplet och du får en bättre uppfattning om vad det innebär.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-107">Take a look at the first example and you'll have a better idea of what that means.</span></span>

> [!NOTE]
> <span data-ttu-id="a8f0c-108">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="a8f0c-109">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="a8f0c-110">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="a8f0c-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

## <a name="creating-a-pscustomobject"></a><span data-ttu-id="a8f0c-111">Skapa en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="a8f0c-111">Creating a PSCustomObject</span></span>

<span data-ttu-id="a8f0c-112">Jag älskar att använda `[PSCustomObject]` i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-112">I love using `[PSCustomObject]` in PowerShell.</span></span> <span data-ttu-id="a8f0c-113">Det har aldrig varit enklare att skapa ett användbart objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-113">Creating a usable object has never been easier.</span></span>
<span data-ttu-id="a8f0c-114">Därför ska jag hoppa över alla andra sätt som du kan skapa ett objekt, men jag behöver nämna att de flesta av dessa exempel är PowerShell v 3.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-114">Because of that, I'm going to skip over all the other ways you can create an object but I need to mention that most of these examples are PowerShell v3.0 and newer.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
```

<span data-ttu-id="a8f0c-115">Den här metoden fungerar bra för mig eftersom jag använder hash för allt du behöver.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-115">This method works well for me because I use hashtables for just about everything.</span></span> <span data-ttu-id="a8f0c-116">Men det finns tillfällen då jag skulle vilja att PowerShell ska behandla hash mer som ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-116">But there are times when I would like PowerShell to treat hashtables more like an object.</span></span> <span data-ttu-id="a8f0c-117">Den första platsen du märker skillnaden är när du vill använda `Format-Table` eller `Export-CSV` och du inser att en hash-tabellen bara är en samling nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-117">The first place you notice the difference is when you want to use `Format-Table` or `Export-CSV` and you realize that a hashtable is just a collection of key/value pairs.</span></span>

<span data-ttu-id="a8f0c-118">Du kan sedan komma åt och använda värdena som du skulle göra med ett vanligt objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-118">You can then access and use the values like you would a normal object.</span></span>

```powershell
$myObject.Name
```

### <a name="converting-a-hashtable"></a><span data-ttu-id="a8f0c-119">Konvertera en hash-hash</span><span class="sxs-lookup"><span data-stu-id="a8f0c-119">Converting a hashtable</span></span>

<span data-ttu-id="a8f0c-120">När jag är på ämnet vet du att du kunde göra detta:</span><span class="sxs-lookup"><span data-stu-id="a8f0c-120">While I am on the topic, did you know you could do this:</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}
$myObject = [pscustomobject]$myHashtable
```

<span data-ttu-id="a8f0c-121">Jag föredrar att skapa objektet från Start, men det finns tillfällen då du måste arbeta med en hash-tabellen först.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-121">I do prefer to create the object from the start but there are times you have to work with a hashtable first.</span></span> <span data-ttu-id="a8f0c-122">Det här exemplet fungerar eftersom konstruktorn tar en hash-tabellen för objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-122">This example works because the constructor takes a hashtable for the object properties.</span></span> <span data-ttu-id="a8f0c-123">En viktig anmärkning är att medan den här metoden fungerar är den inte en exakt motsvarighet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-123">One important note is that while this method works, it isn't an exact equivalent.</span></span> <span data-ttu-id="a8f0c-124">Den största skillnaden är att ordningen på egenskaperna inte bevaras.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-124">The biggest difference is that the order of the properties isn't preserved.</span></span>

### <a name="legacy-approach"></a><span data-ttu-id="a8f0c-125">Äldre metod</span><span class="sxs-lookup"><span data-stu-id="a8f0c-125">Legacy approach</span></span>

<span data-ttu-id="a8f0c-126">Du kanske har sett personer `New-Object` som använder för att skapa anpassade objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-126">You may have seen people use `New-Object` to create custom objects.</span></span>

```powershell
$myHashtable = @{
    Name     = 'Kevin'
    Language = 'PowerShell'
    State    = 'Texas'
}

$myObject = New-Object -TypeName PSObject -Property $myHashtable
```

<span data-ttu-id="a8f0c-127">På så sätt är det ganska lite långsammare, men det kan vara det bästa alternativet i tidiga versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-127">This way is quite a bit slower but it may be your best option on early versions of PowerShell.</span></span>

### <a name="saving-to-a-file"></a><span data-ttu-id="a8f0c-128">Spara till en fil</span><span class="sxs-lookup"><span data-stu-id="a8f0c-128">Saving to a file</span></span>

<span data-ttu-id="a8f0c-129">Jag hittar det bästa sättet att spara en hash-fil i en fil är att spara den som JSON.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-129">I find the best way to save a hashtable to a file is to save it as JSON.</span></span> <span data-ttu-id="a8f0c-130">Du kan importera tillbaka den till en`[PSCusomObject]`</span><span class="sxs-lookup"><span data-stu-id="a8f0c-130">You can import it back into a `[PSCusomObject]`</span></span>

```powershell
$myObject | ConvertTo-Json -depth 1- | Set-Content -Path $Path
$myObject = Get-Content -Path $Path | ConvertFrom-Json
```

<span data-ttu-id="a8f0c-131">Jag ser fler sätt att spara objekt i en fil i min artikel på [många sätt att läsa och skriva till filer][].</span><span class="sxs-lookup"><span data-stu-id="a8f0c-131">I cover more ways to save objects to a file in my article on [The many ways to read and write to files][].</span></span>

## <a name="working-with-properties"></a><span data-ttu-id="a8f0c-132">Arbeta med egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8f0c-132">Working with properties</span></span>

### <a name="adding-properties"></a><span data-ttu-id="a8f0c-133">Lägga till egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8f0c-133">Adding properties</span></span>

<span data-ttu-id="a8f0c-134">Du kan fortfarande lägga till nya egenskaper till din `PSCustomObject` med `Add-Member` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-134">You can still add new properties to your `PSCustomObject` with `Add-Member`.</span></span>

```powershell
$myObject | Add-Member -MemberType NoteProperty -Name `ID` -Value 'KevinMarquette'

$myObject.ID
```

### <a name="remove-properties"></a><span data-ttu-id="a8f0c-135">Ta bort egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8f0c-135">Remove properties</span></span>

<span data-ttu-id="a8f0c-136">Du kan också ta bort egenskaper från ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-136">You can also remove properties off of an object.</span></span>

```powershell
$myObject.psobject.properties.remove('ID')
```

<span data-ttu-id="a8f0c-137">`psobject`Är en dold egenskap som ger dig åtkomst till bas objektets metadata.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-137">The `psobject` is a hidden property that gives you access to base object metadata.</span></span>

### <a name="enumerating-property-names"></a><span data-ttu-id="a8f0c-138">Räknar upp egenskaps namn</span><span class="sxs-lookup"><span data-stu-id="a8f0c-138">Enumerating property names</span></span>

<span data-ttu-id="a8f0c-139">Ibland behöver du en lista över alla egenskaps namn för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-139">Sometimes you need a list of all the property names on an object.</span></span>

```powershell
$myObject | Get-Member -MemberType NoteProperty | Select -ExpandProperty Name
```

<span data-ttu-id="a8f0c-140">Vi kan även hämta samma lista av `psobject` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-140">We can get this same list off of the `psobject` property too.</span></span>

```powershell
$myobject.psobject.properties.name
```

### <a name="dynamically-accessing-properties"></a><span data-ttu-id="a8f0c-141">Dynamiskt åtkomst till egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8f0c-141">Dynamically accessing properties</span></span>

<span data-ttu-id="a8f0c-142">Jag har redan nämnt att du kan komma åt egenskaps värden direkt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-142">I already mentioned that you can access property values directly.</span></span>

```powershell
$myObject.Name
```

<span data-ttu-id="a8f0c-143">Du kan använda en sträng för egenskaps namnet och den fungerar fortfarande.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-143">You can use a string for the property name and it will still work.</span></span>

```powershell
$myObject.'Name'
```

<span data-ttu-id="a8f0c-144">Vi kan ta det här ett steg och använda en variabel för egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-144">We can take this one more step and use a variable for the property name.</span></span>

```powershell
$property = 'Name'
$myObject.$property
```

<span data-ttu-id="a8f0c-145">Jag vet att det ser konstigt ut, men det fungerar.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-145">I know that looks strange, but it works.</span></span>

### <a name="convert-pscustomboject-into-a-hashtable"></a><span data-ttu-id="a8f0c-146">Konvertera pscustomboject till en hash-form</span><span class="sxs-lookup"><span data-stu-id="a8f0c-146">Convert pscustomboject into a hashtable</span></span>

<span data-ttu-id="a8f0c-147">Om du vill fortsätta från det sista avsnittet kan du dynamiskt gå igenom egenskaperna och skapa en hash-grupp från dem.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-147">To continue on from the last section, you can dynamically walk the properties and create a hashtable from them.</span></span>

```powershell
$hashtable = @{}
foreach( $property in $myobject.psobject.properties.name )
{
    $hashtable[$property] = $myObject.$property
}
```

### <a name="testing-for-properties"></a><span data-ttu-id="a8f0c-148">Testa för egenskaper</span><span class="sxs-lookup"><span data-stu-id="a8f0c-148">Testing for properties</span></span>

<span data-ttu-id="a8f0c-149">Om du behöver veta om en egenskap finns kan du bara kontrol lera att egenskapen har ett värde.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-149">If you need to know if a property exists, you could just check for that property to have a value.</span></span>

```powershell
if( $null -ne $myObject.ID )
```

<span data-ttu-id="a8f0c-150">Men om värdet kan vara `$null` och du fortfarande behöver söka efter det kan du kontrol lera det `psobject.properties` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-150">But if the value could be `$null` and you still need to check for it, you can check the `psobject.properties` for it.</span></span>

```powershell
if( $myobject.psobject.properties.match('ID') )
```

## <a name="adding-object-methods"></a><span data-ttu-id="a8f0c-151">Lägga till objekt metoder</span><span class="sxs-lookup"><span data-stu-id="a8f0c-151">Adding object methods</span></span>

<span data-ttu-id="a8f0c-152">Om du behöver lägga till en skript metod i ett objekt kan du göra det med `Add-Member` och en `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-152">If you need to add a script method to an object, you can do it with `Add-Member` and a `ScriptBlock`.</span></span> <span data-ttu-id="a8f0c-153">Du måste använda den `this` automatiska variabeln Reference för det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-153">You have to use the `this` automatic variable reference the current object.</span></span> <span data-ttu-id="a8f0c-154">Här är en `scriptblock` för att omvandla ett objekt till en hash-objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-154">Here is a `scriptblock` to turn an object into a hashtable.</span></span> <span data-ttu-id="a8f0c-155">(samma kod bildar det sista exemplet)</span><span class="sxs-lookup"><span data-stu-id="a8f0c-155">(same code form the last example)</span></span>

```powershell
$ScriptBlock = {
    $hashtable = @{}
    foreach( $property in $this.psobject.properties.name )
    {
        $hashtable[$property] = $this.$property
    }
    return $hashtable
}
```

<span data-ttu-id="a8f0c-156">Sedan lägger vi till den till vårt objekt som en skript egenskap.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-156">Then we add it to our object as a script property.</span></span>

```powershell
$memberParam = @{
    MemberType = "ScriptMethod"
    InputObject = $myobject
    Name = "ToHashtable"
    Value = $scriptBlock
}
Add-Member @memberParam
```

<span data-ttu-id="a8f0c-157">Sedan kan vi anropa vår funktion så här:</span><span class="sxs-lookup"><span data-stu-id="a8f0c-157">Then we can call our function like this:</span></span>

```powershell
$myObject.ToHashtable()
```

### <a name="objects-vs-value-types"></a><span data-ttu-id="a8f0c-158">Objekt vs värde typer</span><span class="sxs-lookup"><span data-stu-id="a8f0c-158">Objects vs Value types</span></span>

<span data-ttu-id="a8f0c-159">Objekt och värde typer hanterar inte variabel tilldelningar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-159">Objects and value types don't handle variable assignments the same way.</span></span> <span data-ttu-id="a8f0c-160">Om du tilldelar värde typer till varandra kopieras bara värdet till den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-160">If you assign value types to each other, only the value get copied to the new variable.</span></span>

```powershell
$first = 1
$second = $first
$second = 2
```

<span data-ttu-id="a8f0c-161">I det här fallet `$first` är 1 och `$second` är 2.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-161">In this case, `$first` is 1 and `$second` is 2.</span></span>

<span data-ttu-id="a8f0c-162">Objektvariabler innehåller en referens till det faktiska objektet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-162">Object variables hold a reference to the actual object.</span></span> <span data-ttu-id="a8f0c-163">När du tilldelar ett objekt till en ny variabel refererar de fortfarande till samma objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-163">When you assign one object to a new variable, they still reference the same object.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third
$fourth.Key = 4
```

<span data-ttu-id="a8f0c-164">Eftersom `$third` och `$fourth` refererar samma instans av ett objekt, både `$third.key` och `$fourth.Key` är 4.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-164">Because `$third` and `$fourth` reference the same instance of an object, both `$third.key` and `$fourth.Key` are 4.</span></span>

### <a name="psobjectcopy"></a><span data-ttu-id="a8f0c-165">psobject. Copy ()</span><span class="sxs-lookup"><span data-stu-id="a8f0c-165">psobject.copy()</span></span>

<span data-ttu-id="a8f0c-166">Om du behöver en äkta kopia av ett objekt kan du klona det.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-166">If you need a true copy of an object, you can clone it.</span></span>

```powershell
$third = [PSCustomObject]@{Key=3}
$fourth = $third.psobject.copy()
$fourth.Key = 4
```

<span data-ttu-id="a8f0c-167">Klona skapar en ytlig kopia av objektet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-167">Clone creates a shallow copy of the object.</span></span> <span data-ttu-id="a8f0c-168">De har olika instanser nu och `$third.key` är 3 och `$fourth.Key` 4 i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-168">They have different instances now and `$third.key` is 3 and `$fourth.Key` is 4 in this example.</span></span>

<span data-ttu-id="a8f0c-169">Jag kallar en ytlig kopia eftersom du har kapslade objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-169">I call this a shallow copy because if you have nested objects.</span></span> <span data-ttu-id="a8f0c-170">(där egenskaperna innehåller andra objekt).</span><span class="sxs-lookup"><span data-stu-id="a8f0c-170">(where the properties contain other objects).</span></span> <span data-ttu-id="a8f0c-171">Endast värdena på den översta nivån kopieras.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-171">Only the top-level values are copied.</span></span> <span data-ttu-id="a8f0c-172">De underordnade objekten kommer att referera till varandra.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-172">The child objects will reference each other.</span></span>

### <a name="pstypename-for-custom-object-types"></a><span data-ttu-id="a8f0c-173">PSTypeName för anpassade objekt typer</span><span class="sxs-lookup"><span data-stu-id="a8f0c-173">PSTypeName for custom object types</span></span>

<span data-ttu-id="a8f0c-174">Nu när vi har ett-objekt finns det några saker som vi kan göra med det som kanske inte är nästan uppenbart.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-174">Now that we have an object, there are a few more things we can do with it that may not be nearly as obvious.</span></span> <span data-ttu-id="a8f0c-175">Det första du behöver göra är att ge det ett `PSTypeName` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-175">First thing we need to do is give it a `PSTypeName`.</span></span> <span data-ttu-id="a8f0c-176">Det här är det vanligaste sättet att se vad de gör:</span><span class="sxs-lookup"><span data-stu-id="a8f0c-176">This is the most common way I see people do it:</span></span>

```powershell
$myObject.PSObject.TypeNames.Insert(0,"My.Object")
```

<span data-ttu-id="a8f0c-177">Jag har nyligen identifierat ett annat sätt att göra detta från det här [inlägget av/u/markekraus][].</span><span class="sxs-lookup"><span data-stu-id="a8f0c-177">I recently discovered another way to do this from this [post by /u/markekraus][].</span></span> <span data-ttu-id="a8f0c-178">Jag gjorde ett litet utforska och fler inlägg om idén från [Adam Bertram][] och [Mike Shepard][] där de pratar om den här metoden som gör det möjligt att definiera den infogade.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-178">I did a little digging and more posts about the idea from [Adam Bertram][] and [Mike Shepard][] where they talk about this approach that allows you to define it inline.</span></span>

```powershell
$myObject = [PSCustomObject]@{
    PSTypeName = 'My.Object'
    Name       = 'Kevin'
    Language   = 'PowerShell'
    State      = 'Texas'
}
```

<span data-ttu-id="a8f0c-179">Jag älskar hur bra det här passar in i språket.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-179">I love how nicely this just fits into the language.</span></span> <span data-ttu-id="a8f0c-180">Nu när vi har ett objekt med rätt typ namn kan vi göra några fler saker.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-180">Now that we have an object with a proper type name, we can do some more things.</span></span>

## <a name="using-defaultpropertyset-the-long-way"></a><span data-ttu-id="a8f0c-181">Använda DefaultPropertySet (det långa sättet)</span><span class="sxs-lookup"><span data-stu-id="a8f0c-181">Using DefaultPropertySet (the long way)</span></span>

<span data-ttu-id="a8f0c-182">PowerShell bestämmer för oss vilka egenskaper som ska visas som standard.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-182">PowerShell decides for us what properties to display by default.</span></span> <span data-ttu-id="a8f0c-183">Många av de inbyggda kommandona har en `.ps1xml` [formateringsinformation][] som gör all tungbar.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-183">A lot of the native commands have a `.ps1xml` [formatting file][] that does all the heavy lifting.</span></span> <span data-ttu-id="a8f0c-184">Från det här [inlägget av BOE Prox][]finns det ett annat sätt för oss att göra detta på vårt anpassade objekt med bara PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-184">From this [post by Boe Prox][], there's another way for us to do this on our custom object using just PowerShell.</span></span> <span data-ttu-id="a8f0c-185">Vi kan ge den en `MemberSet` för IT-användning.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-185">We can give it a `MemberSet` for it to use.</span></span>

```powershell
$defaultDisplaySet = 'Name','Language'
$defaultDisplayPropertySet = New-Object System.Management.Automation.PSPropertySet(‘DefaultDisplayPropertySet’,[string[]]$defaultDisplaySet)
$PSStandardMembers = [System.Management.Automation.PSMemberInfo[]]@($defaultDisplayPropertySet)
$MyObject | Add-Member MemberSet PSStandardMembers $PSStandardMembers
```

<span data-ttu-id="a8f0c-186">Nu när mitt objekt bara hamnar på gränssnittet visas endast dessa egenskaper som standard.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-186">Now when my object just falls to the shell, it will only show those properties by default.</span></span>

### <a name="update-typedata-with-defaultpropertyset"></a><span data-ttu-id="a8f0c-187">Uppdatera-TypeData med DefaultPropertySet</span><span class="sxs-lookup"><span data-stu-id="a8f0c-187">Update-TypeData with DefaultPropertySet</span></span>

<span data-ttu-id="a8f0c-188">Det här är bra men jag har nyligen sett ett bättre sätt att titta [på PowerShell unplugged 2016 med Jeffrey Snover & Dan Jones][psunplugged].</span><span class="sxs-lookup"><span data-stu-id="a8f0c-188">This is nice but I recently saw a better way when watching [PowerShell unplugged 2016 with Jeffrey Snover & Don Jones][psunplugged].</span></span> <span data-ttu-id="a8f0c-189">Jeffrey använde [Update-TypeData][] för att ange standard egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-189">Jeffrey was using [Update-TypeData][] to specify the default properties.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    DefaultDisplayPropertySet = 'Name','Language'
}
Update-TypeData @TypeData
```

<span data-ttu-id="a8f0c-190">Det är så enkelt att jag skulle kunna komma ihåg det om jag inte har det här inlägget som en snabb referens.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-190">That is simple enough that I could almost remember it if I didn't have this post as a quick reference.</span></span> <span data-ttu-id="a8f0c-191">Nu kan jag enkelt skapa objekt med massor av egenskaper och samtidigt ge det ett snyggt visnings läge när du tittar på det från gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-191">Now I can easily create objects with lots of properties and still give it a nice clean view when looking at it from the shell.</span></span> <span data-ttu-id="a8f0c-192">Om jag behöver åtkomst till eller se de andra egenskaperna finns de fortfarande där.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-192">If I need to access or see those other properties, they're still there.</span></span>

```powershell
$myObject | Format-List *
```

### <a name="update-typedata-with-scriptproperty"></a><span data-ttu-id="a8f0c-193">Uppdatera-TypeData med ScriptProperty</span><span class="sxs-lookup"><span data-stu-id="a8f0c-193">Update-TypeData with ScriptProperty</span></span>

<span data-ttu-id="a8f0c-194">Något annat jag fick från den videon skapade skript egenskaper för dina objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-194">Something else I got out of that video was creating script properties for your objects.</span></span> <span data-ttu-id="a8f0c-195">Det kan vara en lämplig stund att peka på att det här fungerar för befintliga objekt.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-195">This would be a good time to point out that this works for existing objects too.</span></span>

```powershell
$TypeData = @{
    TypeName = 'My.Object'
    MemberType = 'ScriptProperty'
    MemberName = 'UpperCaseName'
    Value = {$this.Name.toUpper()}
}
Update-TypeData @TypeData
```

<span data-ttu-id="a8f0c-196">Du kan göra detta innan objektet skapas eller efter och det fungerar fortfarande.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-196">You can do this before your object is created or after and it will still work.</span></span> <span data-ttu-id="a8f0c-197">Detta är vad som gör detta annorlunda och använder `Add-Member` med en skript egenskap.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-197">This is what makes this different then using `Add-Member` with a script property.</span></span> <span data-ttu-id="a8f0c-198">När du använder `Add-Member` det som refereras tidigare finns det bara på den aktuella instansen av objektet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-198">When you use `Add-Member` the way I referenced earlier, it only exists on that specific instance of the object.</span></span> <span data-ttu-id="a8f0c-199">Den här gäller för alla objekt med detta `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-199">This one applies to all objects with this `TypeName`.</span></span>

## <a name="function-parameters"></a><span data-ttu-id="a8f0c-200">Funktions parametrar</span><span class="sxs-lookup"><span data-stu-id="a8f0c-200">Function parameters</span></span>

<span data-ttu-id="a8f0c-201">Du kan nu använda de här anpassade typerna för parametrar i dina funktioner och skript.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-201">You can now use these custom types for parameters in your functions and scripts.</span></span> <span data-ttu-id="a8f0c-202">Du kan använda en funktion för att skapa dessa anpassade objekt och sedan skicka dem till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-202">You can have one function create these custom objects and then pass them into other functions.</span></span>

```powershell
param( [PSTypeName('My.Object')]$Data )
```

<span data-ttu-id="a8f0c-203">PowerShell kräver att objektet är av den typ som du har angett.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-203">PowerShell requires that the object is the type you specified.</span></span> <span data-ttu-id="a8f0c-204">Ett verifierings fel genereras om typen inte matchar automatiskt för att spara ditt steg för att testa det i din kod.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-204">It throws a validation error if the type doesn't match automatically to save you the step of testing for it in your code.</span></span> <span data-ttu-id="a8f0c-205">Ett bra exempel på att låta PowerShell göra det bäst.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-205">A great example of letting PowerShell do what it does best.</span></span>

### <a name="function-outputtype"></a><span data-ttu-id="a8f0c-206">Funktions OutputType</span><span class="sxs-lookup"><span data-stu-id="a8f0c-206">Function OutputType</span></span>

<span data-ttu-id="a8f0c-207">Du kan också definiera en `OutputType` för dina avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-207">You can also define an `OutputType` for your advanced functions.</span></span>

```powershell
function Get-MyObject
{
    [OutputType('My.Object')]
    [CmdletBinding()]
        param
        (
            ...
```

<span data-ttu-id="a8f0c-208">Värdet för **OutputType** -attributet är bara en dokumentations anteckning.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-208">The **OutputType** attribute value is only a documentation note.</span></span> <span data-ttu-id="a8f0c-209">Den är inte härledd från funktions koden eller jämförs med själva funktionen utdata.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-209">It isn't derived from the function code or compared to the actual function output.</span></span>

<span data-ttu-id="a8f0c-210">Den främsta anledningen till att du använder en utdatatyp är så att meta-information om din funktion motsvarar dina avsikter.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-210">The main reason you would use an output type is so that meta information about your function reflects your intentions.</span></span> <span data-ttu-id="a8f0c-211">Saker som `Get-Command` och `Get-Help` som din utvecklings miljö kan dra nytta av.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-211">Things like `Get-Command` and `Get-Help` that your development environment can take advantage of.</span></span> <span data-ttu-id="a8f0c-212">Om du vill ha mer information kan du ta en titt på hjälpen: [about_Functions_OutputTypeAttribute][].</span><span class="sxs-lookup"><span data-stu-id="a8f0c-212">If you want more information, then take a look at the help for it: [about_Functions_OutputTypeAttribute][].</span></span>

<span data-ttu-id="a8f0c-213">Om du använder pester för att testa dina funktioner, är det en bra idé att verifiera objekten som matchar din **OutputType**.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-213">With that said, if you're using Pester to unit test your functions then it would be a good idea to validate the output objects match your **OutputType**.</span></span> <span data-ttu-id="a8f0c-214">Detta kan fånga variabler som bara faller på röret när de inte borde det.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-214">This could catch variables that just fall to the pipe when they shouldn't.</span></span>

## <a name="closing-thoughts"></a><span data-ttu-id="a8f0c-215">Stänga idéer</span><span class="sxs-lookup"><span data-stu-id="a8f0c-215">Closing thoughts</span></span>

<span data-ttu-id="a8f0c-216">Kontexten för detta var allt om `[PSCustomObject]` , men en stor del av den här informationen gäller för objekt i allmänhet.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-216">The context of this was all about `[PSCustomObject]`, but a lot of this information applies to objects in general.</span></span>

<span data-ttu-id="a8f0c-217">Jag har sett de flesta av de här funktionerna i överföring innan, men såg aldrig ut dem som en samling information på `PSCustomObject` .</span><span class="sxs-lookup"><span data-stu-id="a8f0c-217">I have seen most of these features in passing before but never saw them presented as a collection of information on `PSCustomObject`.</span></span> <span data-ttu-id="a8f0c-218">Precis den senaste veckan jag stumbled en annan och var förvånad att jag inte hade sett det tidigare.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-218">Just this last week I stumbled upon another one and was surprised that I had not seen it before.</span></span> <span data-ttu-id="a8f0c-219">Jag ville hämta alla dessa idéer, så du kan förhoppnings vis se den större bilden och vara medveten om dem när du har möjlighet att använda dem.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-219">I wanted to pull all these ideas together so you can hopefully see the bigger picture and be aware of them when you have an opportunity to use them.</span></span> <span data-ttu-id="a8f0c-220">Jag hoppas att du har lärt dig något och kan hitta ett sätt att arbeta med dina skript.</span><span class="sxs-lookup"><span data-stu-id="a8f0c-220">I hope you learned something and can find a way to work this into your scripts.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[original version]: https://powershellexplained.com/2016-10-28-powershell-everything-you-wanted-to-know-about-pscustomobject/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[publicera efter BOE prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[post by Boe Prox]: https://learn-PowerShell.net/2013/08/03/quick-hits-set-the-default-property-display-in-PowerShell-on-custom-objects/
[formaterar fil]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[formatting file]: https://mcpmag.com/articles/2014/05/13/PowerShell-properties-part-3.aspx
[about_Functions_OutputTypeAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_outputtypeattribute
[Många sätt att läsa och skriva till filer]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[The many ways to read and write to files]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files
[publicera efter/u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[post by /u/markekraus]: https://www.reddit.com/r/PowerShell/comments/590awc/is_it_possible_to_initialize_a_pscustoobject_with/
[Adam-Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Adam Bertram]: http://www.adamtheautomator.com/building-custom-object-types-PowerShell-pstypename/
[Mike Shepard]: https://powershellstation.com/2016/05/22/custom-objects-and-pstypename/
[psunplugged]: https://www.youtube.com/watch?v=Ab46gHXNm8Q
[Uppdatera – TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
[Update-TypeData]: /powershell/module/microsoft.powershell.utility/update-typedata
