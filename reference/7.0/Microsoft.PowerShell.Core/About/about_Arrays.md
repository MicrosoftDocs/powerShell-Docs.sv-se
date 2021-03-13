---
description: Beskriver matriser, som är data strukturer som är utformade för att lagra samlings objekt.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2febf96d49003263cbcfd3f605db60b6c1d2437b
ms.sourcegitcommit: 2560a122fe3a85ea762c3af6f1cba9e237512b2d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103412951"
---
# <a name="about-arrays"></a><span data-ttu-id="d90ac-103">Om matriser</span><span class="sxs-lookup"><span data-stu-id="d90ac-103">About Arrays</span></span>

## <a name="short-description"></a><span data-ttu-id="d90ac-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="d90ac-104">Short Description</span></span>
<span data-ttu-id="d90ac-105">Beskriver matriser, som är data strukturer som är utformade för att lagra samlings objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-105">Describes arrays, which are data structures designed to store collections of items.</span></span>

## <a name="long-description"></a><span data-ttu-id="d90ac-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="d90ac-106">Long Description</span></span>

<span data-ttu-id="d90ac-107">En matris är en data struktur som är utformad för att lagra en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-107">An array is a data structure that is designed to store a collection of items.</span></span>
<span data-ttu-id="d90ac-108">Objekten kan vara av samma typ eller olika typer.</span><span class="sxs-lookup"><span data-stu-id="d90ac-108">The items can be the same type or different types.</span></span>

<span data-ttu-id="d90ac-109">Från och med Windows PowerShell 3,0 har en samling med noll eller ett objekt vissa egenskaper för matriser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-109">Beginning in Windows PowerShell 3.0, a collection of zero or one object has some properties of arrays.</span></span>

## <a name="creating-and-initializing-an-array"></a><span data-ttu-id="d90ac-110">Skapa och initiera en matris</span><span class="sxs-lookup"><span data-stu-id="d90ac-110">Creating and initializing an array</span></span>

<span data-ttu-id="d90ac-111">Om du vill skapa och initiera en matris tilldelar du flera värden till en variabel.</span><span class="sxs-lookup"><span data-stu-id="d90ac-111">To create and initialize an array, assign multiple values to a variable.</span></span> <span data-ttu-id="d90ac-112">Värdena som lagras i matrisen avgränsas med kommatecken och skiljs från variabelns namn av tilldelnings operatorn ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="d90ac-112">The values stored in the array are delimited with a comma and separated from the variable name by the assignment operator (`=`).</span></span>

<span data-ttu-id="d90ac-113">Om du till exempel vill skapa en matris med namnet `$A` som innehåller de sju numeriska (int) värdena 22, 5, 10, 8, 12, 9 och 80 skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-113">For example, to create an array named `$A` that contains the seven numeric (int) values of 22, 5, 10, 8, 12, 9, and 80, type:</span></span>

```powershell
$A = 22,5,10,8,12,9,80
```

<span data-ttu-id="d90ac-114">Kommatecken kan också användas för att initiera ett enskilt objekts mat ris genom att placera kommatecknet före det enskilda objektet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-114">The comma can also be used to initialize a single item array by placing the comma before the single item.</span></span>

<span data-ttu-id="d90ac-115">Om du till exempel vill skapa en matris med ett enda objekt `$B` som innehåller det enskilda värdet 7 skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-115">For example, to create a single item array named `$B` containing the single value of 7, type:</span></span>

```powershell
$B = ,7
```

<span data-ttu-id="d90ac-116">Du kan också skapa och initiera en matris med hjälp av intervall operatorn ( `..` ).</span><span class="sxs-lookup"><span data-stu-id="d90ac-116">You can also create and initialize an array by using the range operator (`..`).</span></span>
<span data-ttu-id="d90ac-117">I följande exempel skapas en matris som innehåller värdena 5 till 8.</span><span class="sxs-lookup"><span data-stu-id="d90ac-117">The following example creates an array containing the values 5 through 8.</span></span>

```powershell
$C = 5..8
```

<span data-ttu-id="d90ac-118">Därför `$C` innehåller fyra värden: 5, 6, 7 och 8.</span><span class="sxs-lookup"><span data-stu-id="d90ac-118">As a result, `$C` contains four values: 5, 6, 7, and 8.</span></span>

<span data-ttu-id="d90ac-119">När ingen datatyp anges skapar PowerShell varje matris som en objekt mat ris (**system. Object []**).</span><span class="sxs-lookup"><span data-stu-id="d90ac-119">When no data type is specified, PowerShell creates each array as an object array (**System.Object[]**).</span></span> <span data-ttu-id="d90ac-120">Om du vill fastställa data typen för en matris använder du **gettype ()** -metoden.</span><span class="sxs-lookup"><span data-stu-id="d90ac-120">To determine the data type of an array, use the **GetType()** method.</span></span> <span data-ttu-id="d90ac-121">Om du till exempel vill fastställa data typen för `$A` matrisen skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-121">For example, to determine the data type of the `$A` array, type:</span></span>

```powershell
$A.GetType()
```

<span data-ttu-id="d90ac-122">För att skapa en starkt angiven matris, det vill säga en matris som bara kan innehålla värden av en viss typ, omvandla variabeln som en mat ris typ, till exempel **string []**, **lång []** eller **Int32 []**.</span><span class="sxs-lookup"><span data-stu-id="d90ac-122">To create a strongly typed array, that is, an array that can contain only values of a particular type, cast the variable as an array type, such as **string[]**, **long[]**, or **int32[]**.</span></span> <span data-ttu-id="d90ac-123">Om du vill omvandla en matris måste du före variabel namnet med en mat ris typ inom hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-123">To cast an array, precede the variable name with an array type enclosed in brackets.</span></span> <span data-ttu-id="d90ac-124">Om du till exempel vill skapa en 32-bitars heltals mat ris med namnet `$ia` som innehåller fyra heltal (1500, 2230, 3350 och 4000) skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-124">For example, to create a 32-bit integer array named `$ia` containing four integers (1500, 2230, 3350, and 4000), type:</span></span>

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

<span data-ttu-id="d90ac-125">Därför `$ia` kan matrisen bara innehålla heltal.</span><span class="sxs-lookup"><span data-stu-id="d90ac-125">As a result, the `$ia` array can contain only integers.</span></span>

<span data-ttu-id="d90ac-126">Du kan skapa matriser som har omvandlats till en typ som stöds i Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d90ac-126">You can create arrays that are cast to any supported type in the Microsoft .NET Framework.</span></span> <span data-ttu-id="d90ac-127">Till exempel är de objekt som `Get-Process` hämtar för att representera processer av typen **system. Diagnostics. process** .</span><span class="sxs-lookup"><span data-stu-id="d90ac-127">For example, the objects that `Get-Process` retrieves to represent processes are of the **System.Diagnostics.Process** type.</span></span> <span data-ttu-id="d90ac-128">Ange följande kommando för att skapa en strikt skriven matris med process objekt:</span><span class="sxs-lookup"><span data-stu-id="d90ac-128">To create a strongly typed array of process objects, enter the following command:</span></span>

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a><span data-ttu-id="d90ac-129">Operatorn för under uttryck för matris</span><span class="sxs-lookup"><span data-stu-id="d90ac-129">The array sub-expression operator</span></span>

<span data-ttu-id="d90ac-130">Operatorn array-underuttryck skapar en matris från instruktionerna inuti den.</span><span class="sxs-lookup"><span data-stu-id="d90ac-130">The array sub-expression operator creates an array from the statements inside it.</span></span> <span data-ttu-id="d90ac-131">Oavsett vilken instruktion som ingår i operatorn kommer operatorn att placera den i en matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-131">Whatever the statement inside the operator produces, the operator will place it in an array.</span></span> <span data-ttu-id="d90ac-132">Även om det finns noll eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-132">Even if there is zero or one object.</span></span>

<span data-ttu-id="d90ac-133">Mat ris operatorns syntax är följande:</span><span class="sxs-lookup"><span data-stu-id="d90ac-133">The syntax of the array operator is as follows:</span></span>

```syntax
@( ... )
```

<span data-ttu-id="d90ac-134">Du kan använda array-operatorn för att skapa en matris med noll eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-134">You can use the array operator to create an array of zero or one object.</span></span> <span data-ttu-id="d90ac-135">Exempel:</span><span class="sxs-lookup"><span data-stu-id="d90ac-135">For example:</span></span>

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

<span data-ttu-id="d90ac-136">Mat ris operatorn är användbar i skript när du hämtar objekt, men vet inte hur många objekt du får.</span><span class="sxs-lookup"><span data-stu-id="d90ac-136">The array operator is useful in scripts when you are getting objects, but do not know how many objects you get.</span></span> <span data-ttu-id="d90ac-137">Exempel:</span><span class="sxs-lookup"><span data-stu-id="d90ac-137">For example:</span></span>

```powershell
$p = @(Get-Process Notepad)
```

<span data-ttu-id="d90ac-138">Mer information om operatorn array under uttryck finns [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="d90ac-138">For more information about the array sub-expression operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="accessing-and-using-array-elements"></a><span data-ttu-id="d90ac-139">Komma åt och använda mat ris element</span><span class="sxs-lookup"><span data-stu-id="d90ac-139">Accessing and using array elements</span></span>

### <a name="reading-an-array"></a><span data-ttu-id="d90ac-140">Läser en matris</span><span class="sxs-lookup"><span data-stu-id="d90ac-140">Reading an array</span></span>

<span data-ttu-id="d90ac-141">Du kan referera till en matris med hjälp av dess variabel namn.</span><span class="sxs-lookup"><span data-stu-id="d90ac-141">You can refer to an array by using its variable name.</span></span> <span data-ttu-id="d90ac-142">Om du vill visa alla element i matrisen skriver du mat ris namnet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-142">To display all the elements in the array, type the array name.</span></span> <span data-ttu-id="d90ac-143">Anta till exempel `$a` att en matris innehåller heltal som är 0, 1, 2 till och med 9; skriva:</span><span class="sxs-lookup"><span data-stu-id="d90ac-143">For example, assuming `$a` is an array containing integers 0, 1, 2, until 9; typing:</span></span>

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="d90ac-144">Du kan referera till elementen i en matris med hjälp av ett index, med början vid position 0.</span><span class="sxs-lookup"><span data-stu-id="d90ac-144">You can refer to the elements in an array by using an index, beginning at position 0.</span></span> <span data-ttu-id="d90ac-145">Omge indexet med hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-145">Enclose the index number in brackets.</span></span> <span data-ttu-id="d90ac-146">Om du till exempel vill visa det första elementet i `$a` matrisen skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-146">For example, to display the first element in the `$a` array, type:</span></span>

```powershell
$a[0]
```

```Output
0
```

<span data-ttu-id="d90ac-147">Om du vill visa det tredje elementet i `$a` matrisen skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-147">To display the third element in the `$a` array, type:</span></span>

```powershell
$a[2]
```

```Output
2
```

<span data-ttu-id="d90ac-148">Du kan hämta en del av matrisen med en intervall operator för indexet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-148">You can retrieve part of the array using a range operator for the index.</span></span> <span data-ttu-id="d90ac-149">Om du till exempel vill hämta det andra till femte element i matrisen skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-149">For example, to retrieve the second to fifth elements of the array, you would type:</span></span>

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

<span data-ttu-id="d90ac-150">Antalet negativa tal från slutet av matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-150">Negative numbers count from the end of the array.</span></span> <span data-ttu-id="d90ac-151">Till exempel refererar "-1" till det sista elementet i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-151">For example, "-1" refers to the last element of the array.</span></span> <span data-ttu-id="d90ac-152">Om du vill visa de sista tre elementen i matrisen skriver du följande i index, stigande ordning:</span><span class="sxs-lookup"><span data-stu-id="d90ac-152">To display the last three elements of the array, in index ascending order, type:</span></span>

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

<span data-ttu-id="d90ac-153">Om du skriver negativa index i fallande ordning ändras utdata.</span><span class="sxs-lookup"><span data-stu-id="d90ac-153">If you type negative indexes in descending order, your output changes.</span></span>

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

<span data-ttu-id="d90ac-154">Men var försiktig när du använder den här notationen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-154">However, be cautious when using this notation.</span></span> <span data-ttu-id="d90ac-155">Notationen går från slut kanten till början av matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-155">The notation cycles from the end boundary to the beginning of the array.</span></span>

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

<span data-ttu-id="d90ac-156">Ett vanligt misstag är att anta `$a[0..-2]` att avser alla element i matrisen, förutom den sista.</span><span class="sxs-lookup"><span data-stu-id="d90ac-156">Also, one common mistake is to assume `$a[0..-2]` refers to all the elements of the array, except for the last one.</span></span> <span data-ttu-id="d90ac-157">Den refererar till de första, sista och andra-till-sista elementen i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-157">It refers to the first, last, and second-to-last elements in the array.</span></span>

<span data-ttu-id="d90ac-158">Du kan använda plus operatorn ( `+` ) för att kombinera ett intervall med en lista med element i en matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-158">You can use the plus operator (`+`) to combine a ranges with a list of elements in an array.</span></span> <span data-ttu-id="d90ac-159">Om du till exempel vill visa elementen vid index positionerna 0, 2 och 4 till 6, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-159">For example, to display the elements at index positions 0, 2, and 4 through 6, type:</span></span>

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

<span data-ttu-id="d90ac-160">För att visa flera områden och enskilda element kan du också använda plus-operatorn.</span><span class="sxs-lookup"><span data-stu-id="d90ac-160">Also, to list multiple ranges and individual elements you can use the plus operator.</span></span> <span data-ttu-id="d90ac-161">Om du till exempel vill lista elementen noll till två, fyra till sex och elementet med åttonde positions typ:</span><span class="sxs-lookup"><span data-stu-id="d90ac-161">For example, to list elements zero to two, four to six, and the element at eighth positional type:</span></span>

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a><span data-ttu-id="d90ac-162">Iterationer över mat ris element</span><span class="sxs-lookup"><span data-stu-id="d90ac-162">Iterations over array elements</span></span>

<span data-ttu-id="d90ac-163">Du kan också använda loop-konstruktioner, t. ex., och while-slingor för att referera till elementen i en matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-163">You can also use looping constructs, such as ForEach, For, and While loops, to refer to the elements in an array.</span></span> <span data-ttu-id="d90ac-164">Om du till exempel vill använda en förgrunds slinga för att Visa elementen i `$a` matrisen skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-164">For example, to use a ForEach loop to display the elements in the `$a` array, type:</span></span>

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

<span data-ttu-id="d90ac-165">Förgrunds-loopen upprepas genom matrisen och returnerar varje värde i matrisen tills den når slutet av matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-165">The Foreach loop iterates through the array and returns each value in the array until reaching the end of the array.</span></span>

<span data-ttu-id="d90ac-166">For-slingan är användbar när du ökar räknare och undersöker elementen i en matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-166">The For loop is useful when you are incrementing counters while examining the elements in an array.</span></span> <span data-ttu-id="d90ac-167">Om du till exempel vill använda en for-slinga för att returnera varannan värde i en matris, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-167">For example, to use a For loop to return every other value in an array, type:</span></span>

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

<span data-ttu-id="d90ac-168">Du kan använda en while-slinga för att visa element i en matris tills ett definierat villkor inte längre är sant.</span><span class="sxs-lookup"><span data-stu-id="d90ac-168">You can use a While loop to display the elements in an array until a defined condition is no longer true.</span></span> <span data-ttu-id="d90ac-169">Om du till exempel vill visa elementen i `$a` matrisen medan mat ris indexet är mindre än 4 skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-169">For example, to display the elements in the `$a` array while the array index is less than 4, type:</span></span>

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a><span data-ttu-id="d90ac-170">Egenskaper för matriser</span><span class="sxs-lookup"><span data-stu-id="d90ac-170">Properties of arrays</span></span>

### <a name="count-or-length-or-longlength"></a><span data-ttu-id="d90ac-171">Antal eller längd eller LongLength</span><span class="sxs-lookup"><span data-stu-id="d90ac-171">Count or Length or LongLength</span></span>

<span data-ttu-id="d90ac-172">Om du vill ta reda på hur många objekt som finns i en matris använder du `Length` egenskapen eller dess `Count` alias.</span><span class="sxs-lookup"><span data-stu-id="d90ac-172">To determine how many items are in an array, use the `Length` property or its `Count` alias.</span></span> <span data-ttu-id="d90ac-173">`Longlength` är användbart om matrisen innehåller fler än 2 147 483 647 element.</span><span class="sxs-lookup"><span data-stu-id="d90ac-173">`Longlength` is useful if the array contains more than 2,147,483,647 elements.</span></span>

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a><span data-ttu-id="d90ac-174">Rangordning</span><span class="sxs-lookup"><span data-stu-id="d90ac-174">Rank</span></span>

<span data-ttu-id="d90ac-175">Returnerar antalet dimensioner i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-175">Returns the number of dimensions in the array.</span></span> <span data-ttu-id="d90ac-176">De flesta matriser i PowerShell har en dimension.</span><span class="sxs-lookup"><span data-stu-id="d90ac-176">Most arrays in PowerShell have one dimension, only.</span></span> <span data-ttu-id="d90ac-177">Även om du tror att du bygger en flerdimensionell matris som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="d90ac-177">Even when you think you are building a multidimensional array like the following example:</span></span>

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

"`$a rank: $($a.Rank)"
"`$a length: $($a.Length)"
"`$a length: $($a.Length)"
"Process `$a[2][1]: $($a[2][1].ProcessName)"
```

<span data-ttu-id="d90ac-178">I det här exemplet skapar du en endimensionell matris som innehåller andra matriser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-178">In this example, you are creating a single-dimensional array that contains other arrays.</span></span> <span data-ttu-id="d90ac-179">Detta kallas även för en _Taggad matris_.</span><span class="sxs-lookup"><span data-stu-id="d90ac-179">This is also known as a _jagged array_.</span></span> <span data-ttu-id="d90ac-180">Egenskapen **rang** visar att det är en enkel dimension.</span><span class="sxs-lookup"><span data-stu-id="d90ac-180">The **Rank** property proved that this is single-dimensional.</span></span> <span data-ttu-id="d90ac-181">För att få åtkomst till objekt i en taggad matris måste indexen vara i separata hakparenteser ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="d90ac-181">To access items in a jagged array, the indexes must be in separate brackets (`[]`).</span></span>

```Output
$a rank: 1
$a length: 3
$a[2] length: 348
Process $a[2][1]: AcroRd32
```

<span data-ttu-id="d90ac-182">Flerdimensionella matriser lagras i [rad huvud ordning](https://wikipedia.org/wiki/Row-_and_column-major_order).</span><span class="sxs-lookup"><span data-stu-id="d90ac-182">Multidimensional arrays are stored in [row-major order](https://wikipedia.org/wiki/Row-_and_column-major_order).</span></span> <span data-ttu-id="d90ac-183">I följande exempel visas hur du skapar en faktiskt flerdimensionell matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-183">The following example shows how to create a truly multidimensional array.</span></span>

```powershell
[string[,]]$rank2 = [string[,]]::New(3,2)
$rank2.rank
$rank2.Length
$rank2[0,0] = 'a'
$rank2[0,1] = 'b'
$rank2[1,0] = 'c'
$rank2[1,1] = 'd'
$rank2[2,0] = 'e'
$rank2[2,1] = 'f'
$rank2[1,1]
```

```Output
2
6
d
```

<span data-ttu-id="d90ac-184">För att få åtkomst till objekt i en flerdimensionell matris, separera indexen med kommatecken ( `,` ) inom en enda uppsättning hakparenteser ( `[]` ).</span><span class="sxs-lookup"><span data-stu-id="d90ac-184">To access items in a multidimensional array, separate the indexes using a comma (`,`) within a single set of brackets (`[]`).</span></span>

<span data-ttu-id="d90ac-185">Vissa åtgärder på en flerdimensionell matris, till exempel replikering och sammanfogning, kräver att matrisen är tilldelad.</span><span class="sxs-lookup"><span data-stu-id="d90ac-185">Some operations on a multidimensional array, such as replication and concatenation, require that array to be flattened.</span></span> <span data-ttu-id="d90ac-186">Förenkling vänder matrisen till en endimensionell matris av en obegränsad typ.</span><span class="sxs-lookup"><span data-stu-id="d90ac-186">Flattening turns the array into a 1-dimensional array of unconstrained type.</span></span> <span data-ttu-id="d90ac-187">Den resulterande matrisen tar på alla element i rad-huvud ordningen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-187">The resulting array takes on all the elements in row-major order.</span></span> <span data-ttu-id="d90ac-188">Se följande exempel:</span><span class="sxs-lookup"><span data-stu-id="d90ac-188">Consider the following example:</span></span>

```powershell
$a = "red",$true
$b = (New-Object 'int[,]' 2,2)
$b[0,0] = 10
$b[0,1] = 20
$b[1,0] = 30
$b[1,1] = 40
$c = $a + $b
$a.GetType().Name
$b.GetType().Name
$c.GetType().Name
$c
```

<span data-ttu-id="d90ac-189">Utdata visar att `$c` är en endimensionell matris som innehåller objekten från `$a` och `$b` i rad-huvud ordning.</span><span class="sxs-lookup"><span data-stu-id="d90ac-189">The output shows that `$c` is a 1-dimensional array containing the items from `$a` and `$b` in row-major order.</span></span>

```output
Object[]
Int32[,]
Object[]
red
True
10
20
30
40
```

## <a name="methods-of-arrays"></a><span data-ttu-id="d90ac-190">Metoder för matriser</span><span class="sxs-lookup"><span data-stu-id="d90ac-190">Methods of arrays</span></span>

### <a name="clear"></a><span data-ttu-id="d90ac-191">Rensa</span><span class="sxs-lookup"><span data-stu-id="d90ac-191">Clear</span></span>

<span data-ttu-id="d90ac-192">Anger alla element värden till _standardvärdet_ för matrisens element typ.</span><span class="sxs-lookup"><span data-stu-id="d90ac-192">Sets all element values to the _default value_ of the array's element type.</span></span>
<span data-ttu-id="d90ac-193">Metoden clear () återställer inte storleken på matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-193">The Clear() method does not reset the size of the array.</span></span>

<span data-ttu-id="d90ac-194">I följande exempel `$a` är en matris med objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-194">In the following example `$a` is an array of objects.</span></span>

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

<span data-ttu-id="d90ac-195">I det här exemplet har `$intA` explicit angetts som innehåller heltal.</span><span class="sxs-lookup"><span data-stu-id="d90ac-195">In this example, `$intA` is explicitly typed to contain integers.</span></span>

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a><span data-ttu-id="d90ac-196">ForEach</span><span class="sxs-lookup"><span data-stu-id="d90ac-196">ForEach</span></span>

<span data-ttu-id="d90ac-197">Gör det möjligt att iterera över alla element i matrisen och utföra en specifik åtgärd för varje element i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-197">Allows to iterate over all elements in the array and perform a given operation for each element of the array.</span></span>

<span data-ttu-id="d90ac-198">Den förgrunds metoden har flera överlagringar som utför olika åtgärder.</span><span class="sxs-lookup"><span data-stu-id="d90ac-198">The ForEach method has several overloads that perform different operations.</span></span>

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a><span data-ttu-id="d90ac-199">Solredovisning (script block-uttryck)</span><span class="sxs-lookup"><span data-stu-id="d90ac-199">ForEach(scriptblock expression)</span></span>

#### <a name="foreachscriptblock-expression-object-arguments"></a><span data-ttu-id="d90ac-200">(Script block-uttryck, objekt [] argument)</span><span class="sxs-lookup"><span data-stu-id="d90ac-200">ForEach(scriptblock expression, object[] arguments)</span></span>

<span data-ttu-id="d90ac-201">Den här metoden har lagts till i PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="d90ac-201">This method was added in PowerShell v4.</span></span>

> [!NOTE]
> <span data-ttu-id="d90ac-202">Syntaxen kräver att ett skript block används.</span><span class="sxs-lookup"><span data-stu-id="d90ac-202">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="d90ac-203">Parenteser är valfria om script block är den enda parametern.</span><span class="sxs-lookup"><span data-stu-id="d90ac-203">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="d90ac-204">Det får inte finnas något blank steg mellan metoden och den inledande parentesen eller klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-204">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="d90ac-205">I följande exempel visas hur du använder den förgrunds metoden.</span><span class="sxs-lookup"><span data-stu-id="d90ac-205">The following example shows how use the foreach method.</span></span> <span data-ttu-id="d90ac-206">I det här fallet är avsikten att generera det fyrkantiga värdet för elementen i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-206">In this case the intent is to generate the square value of the elements in the array.</span></span>

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

<span data-ttu-id="d90ac-207">Precis som `-ArgumentList` parametern för `ForEach-Object` , `arguments` tillåter parametern att en matris med argument skickas till ett skript block som kon figurer ATS för att godkänna dem.</span><span class="sxs-lookup"><span data-stu-id="d90ac-207">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

<span data-ttu-id="d90ac-208">Mer information om beteendet för **argument List** finns [about_Splatting](about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="d90ac-208">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

#### <a name="foreachtype-converttotype"></a><span data-ttu-id="d90ac-209">(Typ convertToType)</span><span class="sxs-lookup"><span data-stu-id="d90ac-209">ForEach(type convertToType)</span></span>

<span data-ttu-id="d90ac-210">`ForEach`Metoden kan användas för att snabbt omvandla elementen till en annan typ. i följande exempel visas hur du konverterar en lista med sträng datum som ska `[DateTime]` skrivas.</span><span class="sxs-lookup"><span data-stu-id="d90ac-210">The `ForEach` method can be used to swiftly cast the elements to a different type; the following example shows how to convert a list of string dates to `[DateTime]` type.</span></span>

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a><span data-ttu-id="d90ac-211">(String propertyName)</span><span class="sxs-lookup"><span data-stu-id="d90ac-211">ForEach(string propertyName)</span></span>

#### <a name="foreachstring-propertyname-object-newvalue"></a><span data-ttu-id="d90ac-212">(String propertyName, objekt [] newValue)</span><span class="sxs-lookup"><span data-stu-id="d90ac-212">ForEach(string propertyName, object[] newValue)</span></span>

<span data-ttu-id="d90ac-213">`ForEach`Metoden kan också användas för att snabbt hämta eller ange egenskaps värden för varje objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-213">The `ForEach` method can also be used to quickly retrieve, or set property values for every item in the collection.</span></span>

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a><span data-ttu-id="d90ac-214">(Sträng methodName)</span><span class="sxs-lookup"><span data-stu-id="d90ac-214">ForEach(string methodName)</span></span>

#### <a name="foreachstring-methodname-object-arguments"></a><span data-ttu-id="d90ac-215">Sol(sträng methodName, objekt [] argument)</span><span class="sxs-lookup"><span data-stu-id="d90ac-215">ForEach(string methodName, object[] arguments)</span></span>

<span data-ttu-id="d90ac-216">Slutligen `ForEach` kan metoder användas för att köra en metod på alla objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-216">Lastly, `ForEach` methods can be used to execute a method on every item in the collection.</span></span>

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

<span data-ttu-id="d90ac-217">Precis som `-ArgumentList` parametern för `ForEach-Object` , `arguments` tillåter parametern att en matris med argument skickas till ett skript block som kon figurer ATS för att godkänna dem.</span><span class="sxs-lookup"><span data-stu-id="d90ac-217">Just like the `-ArgumentList` parameter of `ForEach-Object`, the `arguments` parameter allows the passing of an array of arguments to a script block configured to accept them.</span></span>

> [!NOTE]
> <span data-ttu-id="d90ac-218">Från och med Windows PowerShell 3,0 att hämta egenskaper och köra metoder för varje objekt i en samling kan också utföras med hjälp av "metoder för skalära objekt och samlingar" du kan läsa mer om det här [about_Methods](about_methods.md).</span><span class="sxs-lookup"><span data-stu-id="d90ac-218">Starting in Windows PowerShell 3.0 retrieving properties and executing methods for each item in a collection can also be accomplished using "Methods of scalar objects and collections" You can read more about that here [about_methods](about_methods.md).</span></span>

### <a name="where"></a><span data-ttu-id="d90ac-219">Var</span><span class="sxs-lookup"><span data-stu-id="d90ac-219">Where</span></span>

<span data-ttu-id="d90ac-220">Tillåter att filtrera eller välja element i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-220">Allows to filter or select the elements of the array.</span></span> <span data-ttu-id="d90ac-221">Skriptet måste utvärderas till något annat än: noll (0), tom sträng `$false` eller `$null` element som ska visas efter `Where`</span><span class="sxs-lookup"><span data-stu-id="d90ac-221">The script must evaluate to anything different than: zero (0), empty string, `$false` or `$null` for the element to show after the `Where`</span></span>

<span data-ttu-id="d90ac-222">Det finns en definition för `Where` metoden.</span><span class="sxs-lookup"><span data-stu-id="d90ac-222">There is one definition for the `Where` method.</span></span>

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> <span data-ttu-id="d90ac-223">Syntaxen kräver att ett skript block används.</span><span class="sxs-lookup"><span data-stu-id="d90ac-223">The syntax requires the usage of a script block.</span></span> <span data-ttu-id="d90ac-224">Parenteser är valfria om script block är den enda parametern.</span><span class="sxs-lookup"><span data-stu-id="d90ac-224">Parentheses are optional if the scriptblock is the only parameter.</span></span> <span data-ttu-id="d90ac-225">Det får inte finnas något blank steg mellan metoden och den inledande parentesen eller klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-225">Also, there must not be a space between the method and the opening parenthesis or brace.</span></span>

<span data-ttu-id="d90ac-226">`Expression`Är script block som krävs för filtrering, det `mode` valfria argumentet tillåter ytterligare markerings funktioner och det `numberToReturn` valfria argumentet ger möjlighet att begränsa hur många objekt som returneras från filtret.</span><span class="sxs-lookup"><span data-stu-id="d90ac-226">The `Expression` is scriptblock that is required for filtering, the `mode` optional argument allows additional selection capabilities, and the `numberToReturn` optional argument allows the ability to limit how many items are returned from the filter.</span></span>

<span data-ttu-id="d90ac-227">Godkända värden för `mode` är:</span><span class="sxs-lookup"><span data-stu-id="d90ac-227">The acceptable values for `mode` are:</span></span>

- <span data-ttu-id="d90ac-228">Standard (0) – returnera alla objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-228">Default (0) - Return all items</span></span>
- <span data-ttu-id="d90ac-229">Första (1) – returnera det första objektet</span><span class="sxs-lookup"><span data-stu-id="d90ac-229">First (1) - Return the first item</span></span>
- <span data-ttu-id="d90ac-230">Senaste (2) – returnera det sista objektet</span><span class="sxs-lookup"><span data-stu-id="d90ac-230">Last (2) - Return the last item</span></span>
- <span data-ttu-id="d90ac-231">SkipUntil (3) – hoppa över objekt tills villkoret är sant, returnera återstående objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-231">SkipUntil (3) - Skip items until condition is true, the return the remaining items</span></span>
- <span data-ttu-id="d90ac-232">Till (4) – returnera alla objekt tills villkoret är sant</span><span class="sxs-lookup"><span data-stu-id="d90ac-232">Until (4) - Return all items until condition is true</span></span>
- <span data-ttu-id="d90ac-233">Split (5) – returnera en matris med två element</span><span class="sxs-lookup"><span data-stu-id="d90ac-233">Split (5) - Return an array of two elements</span></span>
  - <span data-ttu-id="d90ac-234">Det första elementet innehåller matchande objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-234">The first element contains matching items</span></span>
  - <span data-ttu-id="d90ac-235">Det andra elementet innehåller återstående objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-235">The second element contains the remaining items</span></span>

<span data-ttu-id="d90ac-236">I följande exempel visas hur du markerar alla udda tal från matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-236">The following example shows how to select all odd numbers from the array.</span></span>

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

<span data-ttu-id="d90ac-237">Det här exemplet visar hur du väljer de strängar som inte är tomma.</span><span class="sxs-lookup"><span data-stu-id="d90ac-237">This example show how to select the strings that are not empty.</span></span>

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a><span data-ttu-id="d90ac-238">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="d90ac-238">Default</span></span>

<span data-ttu-id="d90ac-239">`Default`Läget filtrerar objekt med hjälp av `Expression` script block.</span><span class="sxs-lookup"><span data-stu-id="d90ac-239">The `Default` mode filters items using the `Expression` scriptblock.</span></span>

<span data-ttu-id="d90ac-240">Om en anges anges det `numberToReturn` maximala antalet objekt som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="d90ac-240">If a `numberToReturn` is provided, it specifies the maximum number of items to return.</span></span>

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> <span data-ttu-id="d90ac-241">Både `Default` läge och `First` läge returnerar de första ( `numberToReturn` ) objekten och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="d90ac-241">Both the `Default` mode and `First` mode return the first (`numberToReturn`) items, and can be used interchangeably.</span></span>

#### <a name="last"></a><span data-ttu-id="d90ac-242">Sista</span><span class="sxs-lookup"><span data-stu-id="d90ac-242">Last</span></span>

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a><span data-ttu-id="d90ac-243">SkipUntil</span><span class="sxs-lookup"><span data-stu-id="d90ac-243">SkipUntil</span></span>

<span data-ttu-id="d90ac-244">`SkipUntil`Läget hoppar över alla objekt i en samling tills ett objekt klarar filtret för skript block uttryck.</span><span class="sxs-lookup"><span data-stu-id="d90ac-244">The `SkipUntil` mode skips all objects in a collection until an object passes the script block expression filter.</span></span> <span data-ttu-id="d90ac-245">Den returnerar sedan **alla** återstående samlings objekt utan att testa dem.</span><span class="sxs-lookup"><span data-stu-id="d90ac-245">It then returns **ALL** remaining collection items without testing them.</span></span> <span data-ttu-id="d90ac-246">_Endast ett överförings objekt testas_.</span><span class="sxs-lookup"><span data-stu-id="d90ac-246">_Only one passing item is tested_.</span></span>

<span data-ttu-id="d90ac-247">Det innebär att den returnerade samlingen innehåller både _överförda_ och _icke-godkända_ objekt som inte har testats.</span><span class="sxs-lookup"><span data-stu-id="d90ac-247">This means the returned collection contains both _passing_ and _non-passing_ items that have NOT been tested.</span></span>

<span data-ttu-id="d90ac-248">Antalet returnerade objekt kan begränsas genom att ett värde skickas till `numberToReturn` argumentet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-248">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a><span data-ttu-id="d90ac-249">Tills</span><span class="sxs-lookup"><span data-stu-id="d90ac-249">Until</span></span>

<span data-ttu-id="d90ac-250">`Until`Läget inverterar `SkipUntil` läget.</span><span class="sxs-lookup"><span data-stu-id="d90ac-250">The `Until` mode inverts the `SkipUntil` mode.</span></span>  <span data-ttu-id="d90ac-251">Den returnerar **alla** objekt i en samling tills ett objekt skickar skript Blocks uttrycket.</span><span class="sxs-lookup"><span data-stu-id="d90ac-251">It returns **ALL** items in a collection until an item passes the script block expression.</span></span> <span data-ttu-id="d90ac-252">När ett objekt _passerar_ script block-uttrycket `Where` slutar metoden att bearbeta objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-252">Once an item _passes_ the scriptblock expression, the `Where` method stops processing items.</span></span>

<span data-ttu-id="d90ac-253">Det innebär att du får den första uppsättningen _icke-överförda_ objekt från- `Where` metoden.</span><span class="sxs-lookup"><span data-stu-id="d90ac-253">This means that you receive the first set of _non-passing_ items from the `Where` method.</span></span> <span data-ttu-id="d90ac-254">_När_ ett objekt har passerat testas inte resten eller returneras.</span><span class="sxs-lookup"><span data-stu-id="d90ac-254">_After_ one item passes, the rest are NOT tested or returned.</span></span>

<span data-ttu-id="d90ac-255">Antalet returnerade objekt kan begränsas genom att ett värde skickas till `numberToReturn` argumentet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-255">The number of items returned can be limited by passing a value to the `numberToReturn` argument.</span></span>

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> <span data-ttu-id="d90ac-256">Både `Until` och används `SkipUntil` under den plats där ingen grupp objekt testas.</span><span class="sxs-lookup"><span data-stu-id="d90ac-256">Both `Until` and `SkipUntil` operate under the premise of NOT testing a batch of items.</span></span>
>
> <span data-ttu-id="d90ac-257">`Until` Returnerar objekten **före** det första _passet_.</span><span class="sxs-lookup"><span data-stu-id="d90ac-257">`Until` returns the items **BEFORE** the first _pass_.</span></span>
>
> <span data-ttu-id="d90ac-258">`SkipUntil` returnerar alla objekt **efter** det första steget, inklusive det första _passet_.</span><span class="sxs-lookup"><span data-stu-id="d90ac-258">`SkipUntil` returns all the items **AFTER** the first _pass_, including the first passing item.</span></span>

#### <a name="split"></a><span data-ttu-id="d90ac-259">Dela</span><span class="sxs-lookup"><span data-stu-id="d90ac-259">Split</span></span>

<span data-ttu-id="d90ac-260">`Split`Läget delas eller grupperar samlings objekt i två separata samlingar.</span><span class="sxs-lookup"><span data-stu-id="d90ac-260">The `Split` mode splits, or groups collection items into two separate collections.</span></span> <span data-ttu-id="d90ac-261">De som skickar script block-uttrycket och de som inte gör det.</span><span class="sxs-lookup"><span data-stu-id="d90ac-261">Those that pass the scriptblock expression, and those that do not.</span></span>

<span data-ttu-id="d90ac-262">Om en `numberToReturn` har angetts innehåller den första samlingen de _överförda_ objekten, inte större än det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-262">If a `numberToReturn` is specified, the first collection, contains the _passing_ items, not to exceed the value specified.</span></span>

<span data-ttu-id="d90ac-263">Återstående objekt, även de som **skickar** uttrycks filtret, returneras i den andra samlingen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-263">The remaining objects, even those that **PASS** the expression filter, are returned in the second collection.</span></span>

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a><span data-ttu-id="d90ac-264">Hämta medlemmarna i en matris</span><span class="sxs-lookup"><span data-stu-id="d90ac-264">Get the members of an array</span></span>

<span data-ttu-id="d90ac-265">Om du vill hämta egenskaper och metoder för en matris, till exempel egenskapen längd och metoden **SetValue** , använder du parametern **InputObject** för `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d90ac-265">To get the properties and methods of an array, such as the Length property and the **SetValue** method, use the **InputObject** parameter of the `Get-Member` cmdlet.</span></span>

<span data-ttu-id="d90ac-266">När du skickar en matris till `Get-Member` skickar PowerShell objekten en i taget och `Get-Member` returnerar typen för varje objekt i matrisen (ignorerar dubbletter).</span><span class="sxs-lookup"><span data-stu-id="d90ac-266">When you pipe an array to `Get-Member`, PowerShell sends the items one at a time and `Get-Member` returns the type of each item in the array (ignoring duplicates).</span></span>

<span data-ttu-id="d90ac-267">När du använder parametern **InputObject** `Get-Member` returneras medlemmarna i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-267">When you use the **InputObject** parameter, `Get-Member` returns the members of the array.</span></span>

<span data-ttu-id="d90ac-268">Följande kommando hämtar till exempel medlemmarna i `$a` mat ris variabeln.</span><span class="sxs-lookup"><span data-stu-id="d90ac-268">For example, the following command gets the members of the `$a` array variable.</span></span>

```powershell
Get-Member -InputObject $a
```

<span data-ttu-id="d90ac-269">Du kan också hämta medlemmarna i en matris genom att skriva ett kommatecken (,) före det värde som är skickas till `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d90ac-269">You can also get the members of an array by typing a comma (,) before the value that is piped to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="d90ac-270">Kommatecknet gör matrisen till det andra objektet i en matris med matriser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-270">The comma makes the array the second item in an array of arrays.</span></span> <span data-ttu-id="d90ac-271">PowerShell flyttar matriserna en i taget och `Get-Member` returnerar medlemmarna i matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-271">PowerShell pipes the arrays one at a time and `Get-Member` returns the members of the array.</span></span> <span data-ttu-id="d90ac-272">Precis som i de följande två exemplen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-272">Like the next two examples.</span></span>

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a><span data-ttu-id="d90ac-273">Ändra en matris</span><span class="sxs-lookup"><span data-stu-id="d90ac-273">Manipulating an array</span></span>

<span data-ttu-id="d90ac-274">Du kan ändra elementen i en matris, lägga till ett element i en matris och kombinera värdena från två matriser till en tredje matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-274">You can change the elements in an array, add an element to an array, and combine the values from two arrays into a third array.</span></span>

<span data-ttu-id="d90ac-275">Om du vill ändra värdet för ett visst element i en matris anger du mat ris namnet och indexet för det element som du vill ändra och använder sedan tilldelnings operatorn ( `=` ) för att ange ett nytt värde för elementet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-275">To change the value of a particular element in an array, specify the array name and the index of the element that you want to change, and then use the assignment operator (`=`) to specify a new value for the element.</span></span> <span data-ttu-id="d90ac-276">Om du till exempel vill ändra värdet för det andra objektet i `$a` matrisen (index position 1) till 10, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-276">For example, to change the value of the second item in the `$a` array (index position 1) to 10, type:</span></span>

```powershell
$a[1] = 10
```

<span data-ttu-id="d90ac-277">Du kan också använda metoden **SetValue** i en matris för att ändra ett värde.</span><span class="sxs-lookup"><span data-stu-id="d90ac-277">You can also use the **SetValue** method of an array to change a value.</span></span> <span data-ttu-id="d90ac-278">I följande exempel ändras det andra värdet (index position 1) för `$a` matrisen till 500:</span><span class="sxs-lookup"><span data-stu-id="d90ac-278">The following example changes the second value (index position 1) of the `$a` array to 500:</span></span>

```powershell
$a.SetValue(500,1)
```

<span data-ttu-id="d90ac-279">Du kan använda `+=` operatorn för att lägga till ett element i en matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-279">You can use the `+=` operator to add an element to an array.</span></span> <span data-ttu-id="d90ac-280">I följande exempel visas hur du lägger till ett-element i `$a` matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-280">The following example shows how to add an element to the `$a` array.</span></span>

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> <span data-ttu-id="d90ac-281">När du använder `+=` operatorn skapar PowerShell faktiskt en ny matris med värdena för den ursprungliga matrisen och det tillagda värdet.</span><span class="sxs-lookup"><span data-stu-id="d90ac-281">When you use the `+=` operator, PowerShell actually creates a new array with the values of the original array and the added value.</span></span> <span data-ttu-id="d90ac-282">Detta kan orsaka prestanda problem om åtgärden upprepas flera gånger eller om storleken på matrisen är för stor.</span><span class="sxs-lookup"><span data-stu-id="d90ac-282">This might cause performance issues if the operation is repeated several times or the size of the array is too big.</span></span>

<span data-ttu-id="d90ac-283">Det är inte enkelt att ta bort element från en matris, men du kan skapa en ny matris som bara innehåller valda element i en befintlig matris.</span><span class="sxs-lookup"><span data-stu-id="d90ac-283">It is not easy to delete elements from an array, but you can create a new array that contains only selected elements of an existing array.</span></span> <span data-ttu-id="d90ac-284">Om du till exempel vill skapa `$t` matrisen med alla element i `$a` matrisen, förutom värdet vid index position 2, skriver du:</span><span class="sxs-lookup"><span data-stu-id="d90ac-284">For example, to create the `$t` array with all the elements in the `$a` array except for the value at index position 2, type:</span></span>

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

<span data-ttu-id="d90ac-285">Om du vill kombinera två matriser i en enda matris använder du plus operatorn ( `+` ).</span><span class="sxs-lookup"><span data-stu-id="d90ac-285">To combine two arrays into a single array, use the plus operator (`+`).</span></span> <span data-ttu-id="d90ac-286">I följande exempel skapas två matriser, kombinerar dem och sedan visas den resulterande kombinerade matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-286">The following example creates two arrays, combines them, and then displays the resulting combined array.</span></span>

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

<span data-ttu-id="d90ac-287">Därför `$z` innehåller matrisen 1, 3, 5 och 9.</span><span class="sxs-lookup"><span data-stu-id="d90ac-287">As a result, the `$z` array contains 1, 3, 5, and 9.</span></span>

<span data-ttu-id="d90ac-288">Om du vill ta bort en matris tilldelar `$null` du värdet till matrisen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-288">To delete an array, assign a value of `$null` to the array.</span></span> <span data-ttu-id="d90ac-289">Följande kommando tar bort matrisen i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d90ac-289">The following command deletes the array in the `$a` variable.</span></span>

`$a = $null`

<span data-ttu-id="d90ac-290">Du kan också använda `Remove-Item` cmdleten, men tilldelning av värdet `$null` är snabbare, särskilt för stora matriser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-290">You can also use the `Remove-Item` cmdlet, but assigning a value of `$null` is faster, especially for large arrays.</span></span>

## <a name="arrays-of-zero-or-one"></a><span data-ttu-id="d90ac-291">Matriser med noll eller ett</span><span class="sxs-lookup"><span data-stu-id="d90ac-291">Arrays of zero or one</span></span>

<span data-ttu-id="d90ac-292">Från och med Windows PowerShell 3,0 har en samling med noll eller ett objekt värdet count och length.</span><span class="sxs-lookup"><span data-stu-id="d90ac-292">Beginning in Windows PowerShell 3.0, a collection of zero or one object has the Count and Length property.</span></span> <span data-ttu-id="d90ac-293">Du kan också indexera i en matris med ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-293">Also, you can index into an array of one object.</span></span> <span data-ttu-id="d90ac-294">Den här funktionen hjälper dig att undvika skript fel som uppstår när ett kommando som förväntar en samling får färre än två objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-294">This feature helps you to avoid scripting errors that occur when a command that expects a collection gets fewer than two items.</span></span>

<span data-ttu-id="d90ac-295">I följande exempel demonstreras den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="d90ac-295">The following examples demonstrate this feature.</span></span>

### <a name="zero-objects"></a><span data-ttu-id="d90ac-296">Noll objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-296">Zero objects</span></span>

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a><span data-ttu-id="d90ac-297">Ett objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-297">One object</span></span>

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a><span data-ttu-id="d90ac-298">Indexerings stöd för system. tuple-objekt</span><span class="sxs-lookup"><span data-stu-id="d90ac-298">Indexing support for System.Tuple objects</span></span>

<span data-ttu-id="d90ac-299">PowerShell 6,1 har lagt till stöd för indexerad åtkomst till **tuple** -objekt, ungefär som matriser.</span><span class="sxs-lookup"><span data-stu-id="d90ac-299">PowerShell 6.1 added the support for indexed access of **Tuple** objects, similar to arrays.</span></span>
<span data-ttu-id="d90ac-300">Exempel:</span><span class="sxs-lookup"><span data-stu-id="d90ac-300">For example:</span></span>

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

<span data-ttu-id="d90ac-301">Till skillnad från matriser och andra samlings objekt behandlas **tuple** -objekt som ett enda objekt när de skickas genom pipelinen eller med parametrar som stöder matriser med objekt.</span><span class="sxs-lookup"><span data-stu-id="d90ac-301">Unlike arrays and other collection objects, **Tuple** objects are treated as a single object when passed through the pipeline or by parameters that support arrays of objects.</span></span>

<span data-ttu-id="d90ac-302">Mer information finns i [system. tuple](/dotnet/api/system.tuple).</span><span class="sxs-lookup"><span data-stu-id="d90ac-302">For more information, see [System.Tuple](/dotnet/api/system.tuple).</span></span>

## <a name="see-also"></a><span data-ttu-id="d90ac-303">Se även</span><span class="sxs-lookup"><span data-stu-id="d90ac-303">See also</span></span>

- [<span data-ttu-id="d90ac-304">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="d90ac-304">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)
- [<span data-ttu-id="d90ac-305">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="d90ac-305">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="d90ac-306">about_Operators</span><span class="sxs-lookup"><span data-stu-id="d90ac-306">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="d90ac-307">about_For</span><span class="sxs-lookup"><span data-stu-id="d90ac-307">about_For</span></span>](about_For.md)
- [<span data-ttu-id="d90ac-308">about_Foreach</span><span class="sxs-lookup"><span data-stu-id="d90ac-308">about_Foreach</span></span>](about_Foreach.md)
- [<span data-ttu-id="d90ac-309">about_While</span><span class="sxs-lookup"><span data-stu-id="d90ac-309">about_While</span></span>](about_While.md)
