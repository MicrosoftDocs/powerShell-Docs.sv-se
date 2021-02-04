---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 007f8f2e377af0620d439f5a35be51aace032dc1
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2021
ms.locfileid: "99496068"
---
# <span data-ttu-id="a7129-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="a7129-102">Get-Random</span></span>

## <span data-ttu-id="a7129-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a7129-103">SYNOPSIS</span></span>
<span data-ttu-id="a7129-104">Hämtar ett slumpmässigt tal eller väljer objekt slumpmässigt från en samling.</span><span class="sxs-lookup"><span data-stu-id="a7129-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="a7129-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7129-105">SYNTAX</span></span>

### <span data-ttu-id="a7129-106">RandomNumberParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="a7129-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="a7129-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="a7129-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="a7129-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a7129-108">DESCRIPTION</span></span>

<span data-ttu-id="a7129-109">`Get-Random`Cmdleten hämtar ett slumpmässigt valt nummer.</span><span class="sxs-lookup"><span data-stu-id="a7129-109">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="a7129-110">Om du skickar en samling objekt till `Get-Random` hämtas ett eller flera slumpmässigt valda objekt från samlingen.</span><span class="sxs-lookup"><span data-stu-id="a7129-110">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="a7129-111">Utan parametrar eller Indatatyp `Get-Random` returnerar ett kommando ett slumpmässigt valt 32-bitars heltal utan tecken mellan 0 (noll) och **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="a7129-111">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="a7129-112">Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="a7129-112">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="a7129-113">Du kan använda parametrarna för `Get-Random` för att ange lägsta och högsta värden, antalet objekt som returneras från en samling eller ett start nummer.</span><span class="sxs-lookup"><span data-stu-id="a7129-113">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="a7129-114">Att ställa in startvärdet för ett avsiktligt resultat i icke-slumpmässig, repeterbar funktion.</span><span class="sxs-lookup"><span data-stu-id="a7129-114">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="a7129-115">Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="a7129-115">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="a7129-116">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="a7129-116">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="a7129-117">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="a7129-117">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="a7129-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a7129-118">EXAMPLES</span></span>

### <span data-ttu-id="a7129-119">Exempel 1: Hämta ett slumpmässigt heltal</span><span class="sxs-lookup"><span data-stu-id="a7129-119">Example 1: Get a random integer</span></span>

<span data-ttu-id="a7129-120">Det här kommandot hämtar ett slumpmässigt heltal mellan 0 (noll) och **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="a7129-120">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="a7129-121">Exempel 2: Hämta ett slumpmässigt heltal mellan 0 och 99</span><span class="sxs-lookup"><span data-stu-id="a7129-121">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="a7129-122">Exempel 3: Hämta ett slumpmässigt heltal mellan-100 och 99</span><span class="sxs-lookup"><span data-stu-id="a7129-122">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="a7129-123">Exempel 4: Hämta ett slumpmässigt flytt ALS nummer</span><span class="sxs-lookup"><span data-stu-id="a7129-123">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="a7129-124">Det här kommandot hämtar ett slumpmässigt flytt ALS nummer som är större än eller lika med 10,7 och mindre än 20,92.</span><span class="sxs-lookup"><span data-stu-id="a7129-124">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="a7129-125">Exempel 5: Hämta ett slumpmässigt heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="a7129-125">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="a7129-126">Det här kommandot hämtar ett slumpmässigt valt nummer från den angivna matrisen.</span><span class="sxs-lookup"><span data-stu-id="a7129-126">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="a7129-127">Exempel 6: få flera slumpmässiga heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="a7129-127">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="a7129-128">Det här kommandot hämtar tre slumpmässigt markerade siffror i slumpmässig ordning från en matris.</span><span class="sxs-lookup"><span data-stu-id="a7129-128">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="a7129-129">Exempel 7: Slumpa en hel samling</span><span class="sxs-lookup"><span data-stu-id="a7129-129">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="a7129-130">Det här kommandot returnerar hela samlingen i slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="a7129-130">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="a7129-131">Värdet för **Count** -parametern är egenskapen **MaxValue** static för heltal.</span><span class="sxs-lookup"><span data-stu-id="a7129-131">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="a7129-132">Om du vill returnera en hel samling i slumpmässig ordning anger du ett tal som är större än eller lika med antalet objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="a7129-132">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count ([int]::MaxValue)
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="a7129-133">Exempel 8: Hämta ett slumpmässigt icke-numeriskt värde</span><span class="sxs-lookup"><span data-stu-id="a7129-133">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="a7129-134">Det här kommandot returnerar ett slumpmässigt värde från en icke-numerisk samling.</span><span class="sxs-lookup"><span data-stu-id="a7129-134">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="a7129-135">Exempel 9: Använd parametern SetSeed</span><span class="sxs-lookup"><span data-stu-id="a7129-135">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="a7129-136">I det här exemplet visas effekterna av att använda parametern **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="a7129-136">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="a7129-137">Eftersom **SetSeed** genererar icke-slumpmässiga beteenden används vanligt vis endast för att återge resultat, till exempel vid fel sökning eller analys av ett skript.</span><span class="sxs-lookup"><span data-stu-id="a7129-137">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### <span data-ttu-id="a7129-138">Exempel 10: Hämta slumpmässiga filer</span><span class="sxs-lookup"><span data-stu-id="a7129-138">Example 10: Get random files</span></span>

<span data-ttu-id="a7129-139">Dessa kommandon får ett slumpmässigt valt exempel på 50 filer från den `C:` lokala datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="a7129-139">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="a7129-140">Exempel 11: sammanfatta verkliga tärningar</span><span class="sxs-lookup"><span data-stu-id="a7129-140">Example 11: Roll fair dice</span></span>

<span data-ttu-id="a7129-141">Det här exemplet rullar en rättvis Die 1200 gånger och räknar resultatet.</span><span class="sxs-lookup"><span data-stu-id="a7129-141">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="a7129-142">Det första kommandot `ForEach-Object` upprepar anropet till `Get-Random` från skickas i siffror (1-6).</span><span class="sxs-lookup"><span data-stu-id="a7129-142">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="a7129-143">Resultaten grupperas efter deras värde med `Group-Object` och formaterats som en tabell med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="a7129-143">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### <span data-ttu-id="a7129-144">Exempel 12: Använd Count-parametern</span><span class="sxs-lookup"><span data-stu-id="a7129-144">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="a7129-145">Du kan nu använda **Count** -parametern utan rör objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="a7129-145">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="a7129-146">I följande exempel hämtas tre slumptal som är mindre än 10.</span><span class="sxs-lookup"><span data-stu-id="a7129-146">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="a7129-147">Exempel 13: Använd parametern InputObject med en tom sträng eller $null</span><span class="sxs-lookup"><span data-stu-id="a7129-147">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="a7129-148">I det här exemplet anger parametern **InputObject** en matris som innehåller en tom sträng ( `''` ) och `$null` .</span><span class="sxs-lookup"><span data-stu-id="a7129-148">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="a7129-149">`Get-Random` returnerar antingen en `a` tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="a7129-149">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="a7129-150">Den tomma STING visas som en tom rad och `$null` återgår till en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="a7129-150">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="a7129-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a7129-151">PARAMETERS</span></span>

### <span data-ttu-id="a7129-152">-Antal</span><span class="sxs-lookup"><span data-stu-id="a7129-152">-Count</span></span>

<span data-ttu-id="a7129-153">Anger antalet slumpmässiga objekt eller tal som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="a7129-153">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="a7129-154">Standard är 1.</span><span class="sxs-lookup"><span data-stu-id="a7129-154">The default is 1.</span></span>

<span data-ttu-id="a7129-155">`InputObject`Om värdet för **Count** överskrider antalet objekt i samlingen `Get-Random` returneras alla objekt i slumpmässig ordning när det används med.</span><span class="sxs-lookup"><span data-stu-id="a7129-155">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7129-156">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a7129-156">-InputObject</span></span>

<span data-ttu-id="a7129-157">Anger en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="a7129-157">Specifies a collection of objects.</span></span> <span data-ttu-id="a7129-158">`Get-Random` hämtar slumpmässigt valda objekt i slumpmässig ordning från samlingen upp till det antal som anges i **Count**.</span><span class="sxs-lookup"><span data-stu-id="a7129-158">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="a7129-159">Ange objekten, en variabel som innehåller objekten, eller ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="a7129-159">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="a7129-160">Du kan också skicka en samling objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="a7129-160">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="a7129-161">Från och med PowerShell 7 accepterar parametern **InputObject** matriser som kan innehålla en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="a7129-161">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="a7129-162">Matrisen kan skickas nedåt i pipeline eller som ett **InputObject** -parameter värde.</span><span class="sxs-lookup"><span data-stu-id="a7129-162">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a7129-163">-Maximalt</span><span class="sxs-lookup"><span data-stu-id="a7129-163">-Maximum</span></span>

<span data-ttu-id="a7129-164">Anger ett max värde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="a7129-164">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="a7129-165">`Get-Random` Returnerar ett värde som är mindre än det maximala värdet (inte lika med).</span><span class="sxs-lookup"><span data-stu-id="a7129-165">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="a7129-166">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="a7129-166">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="a7129-167">Värdet för **maximum** måste vara större än (lika med) som **minimivärdet**.</span><span class="sxs-lookup"><span data-stu-id="a7129-167">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="a7129-168">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="a7129-168">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="a7129-169">På en 64-bitars dator, om värdet för **minimum** är ett 32-bitars heltal **, är** standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="a7129-169">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="a7129-170">Om **minimivärdet är ett** Double-värde (ett flytt ALS nummer) är standardvärdet **Max** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="a7129-170">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="a7129-171">Annars är standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="a7129-171">Otherwise, the default value is **Int32.MaxValue**.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7129-172">-Minst</span><span class="sxs-lookup"><span data-stu-id="a7129-172">-Minimum</span></span>

<span data-ttu-id="a7129-173">Anger ett minimivärde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="a7129-173">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="a7129-174">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="a7129-174">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="a7129-175">Standardvärdet är 0 (noll).</span><span class="sxs-lookup"><span data-stu-id="a7129-175">The default value is 0 (zero).</span></span>

<span data-ttu-id="a7129-176">**Minimivärdet måste vara** mindre än (lika med) som **Max** värde.</span><span class="sxs-lookup"><span data-stu-id="a7129-176">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="a7129-177">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="a7129-177">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7129-178">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="a7129-178">-SetSeed</span></span>

<span data-ttu-id="a7129-179">Anger ett Seed-värde för slump tals generatorn.</span><span class="sxs-lookup"><span data-stu-id="a7129-179">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="a7129-180">När du använder **SetSeed** använder cmdlet: en [system. Random](/dotnet/api/system.random) -metod för att generera pseudorandom-nummer som inte är kryptografiskt säkra.</span><span class="sxs-lookup"><span data-stu-id="a7129-180">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="a7129-181">Inställning av Dirigerings resultat i icke-slumpmässiga beteenden.</span><span class="sxs-lookup"><span data-stu-id="a7129-181">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="a7129-182">Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="a7129-182">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="a7129-183">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="a7129-183">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="a7129-184">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="a7129-184">You can't reset the seed to its default value.</span></span>

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7129-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7129-185">CommonParameters</span></span>

<span data-ttu-id="a7129-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7129-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7129-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a7129-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7129-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="a7129-188">INPUTS</span></span>

### <span data-ttu-id="a7129-189">System. Object</span><span class="sxs-lookup"><span data-stu-id="a7129-189">System.Object</span></span>

<span data-ttu-id="a7129-190">Du kan skicka ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="a7129-190">You can pipe one or more objects.</span></span> <span data-ttu-id="a7129-191">`Get-Random` väljer värden slumpmässigt från skickas-objekten.</span><span class="sxs-lookup"><span data-stu-id="a7129-191">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="a7129-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a7129-192">OUTPUTS</span></span>

### <span data-ttu-id="a7129-193">System. Int32, system. Int64, system. Double</span><span class="sxs-lookup"><span data-stu-id="a7129-193">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="a7129-194">`Get-Random` Returnerar ett heltals-eller flytt ALS nummer, eller ett objekt som marker ATS slumpvis från en skickad samling.</span><span class="sxs-lookup"><span data-stu-id="a7129-194">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="a7129-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a7129-195">NOTES</span></span>

<span data-ttu-id="a7129-196">Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="a7129-196">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="a7129-197">`Get-Random` returnerar inte alltid samma datatyp som indatavärdet.</span><span class="sxs-lookup"><span data-stu-id="a7129-197">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="a7129-198">I följande tabell visas utdatatypen för var och en av de numeriska inmatnings typerna.</span><span class="sxs-lookup"><span data-stu-id="a7129-198">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="a7129-199">Indatatyp</span><span class="sxs-lookup"><span data-stu-id="a7129-199">Input Type</span></span> | <span data-ttu-id="a7129-200">Utdatatyp</span><span class="sxs-lookup"><span data-stu-id="a7129-200">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="a7129-201">SByte</span><span class="sxs-lookup"><span data-stu-id="a7129-201">SByte</span></span>    |   <span data-ttu-id="a7129-202">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-202">Double</span></span>    |
|    <span data-ttu-id="a7129-203">Byte</span><span class="sxs-lookup"><span data-stu-id="a7129-203">Byte</span></span>    |   <span data-ttu-id="a7129-204">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-204">Double</span></span>    |
|   <span data-ttu-id="a7129-205">Int16</span><span class="sxs-lookup"><span data-stu-id="a7129-205">Int16</span></span>    |   <span data-ttu-id="a7129-206">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-206">Double</span></span>    |
|   <span data-ttu-id="a7129-207">UInt16</span><span class="sxs-lookup"><span data-stu-id="a7129-207">UInt16</span></span>   |   <span data-ttu-id="a7129-208">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-208">Double</span></span>    |
|   <span data-ttu-id="a7129-209">Int32</span><span class="sxs-lookup"><span data-stu-id="a7129-209">Int32</span></span>    |    <span data-ttu-id="a7129-210">Int32</span><span class="sxs-lookup"><span data-stu-id="a7129-210">Int32</span></span>    |
|   <span data-ttu-id="a7129-211">UInt32</span><span class="sxs-lookup"><span data-stu-id="a7129-211">UInt32</span></span>   |   <span data-ttu-id="a7129-212">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-212">Double</span></span>    |
|   <span data-ttu-id="a7129-213">Int64</span><span class="sxs-lookup"><span data-stu-id="a7129-213">Int64</span></span>    |    <span data-ttu-id="a7129-214">Int64</span><span class="sxs-lookup"><span data-stu-id="a7129-214">Int64</span></span>    |
|   <span data-ttu-id="a7129-215">UInt64</span><span class="sxs-lookup"><span data-stu-id="a7129-215">UInt64</span></span>   |   <span data-ttu-id="a7129-216">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-216">Double</span></span>    |
|   <span data-ttu-id="a7129-217">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-217">Double</span></span>   |   <span data-ttu-id="a7129-218">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-218">Double</span></span>    |
|   <span data-ttu-id="a7129-219">Enkel</span><span class="sxs-lookup"><span data-stu-id="a7129-219">Single</span></span>   |   <span data-ttu-id="a7129-220">Double</span><span class="sxs-lookup"><span data-stu-id="a7129-220">Double</span></span>    |

<span data-ttu-id="a7129-221">Från och med Windows PowerShell 3,0 `Get-Random` stöder 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="a7129-221">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="a7129-222">I Windows PowerShell 2,0 omvandlas alla värden till **system. Int32**.</span><span class="sxs-lookup"><span data-stu-id="a7129-222">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="a7129-223">Från och med PowerShell 7, **InputObject** -parametern i **RandomListItemParameterSet** -parameter uppsättningen, accepterar matriser som innehåller en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="a7129-223">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="a7129-224">I tidigare PowerShell-versioner godkändes bara den **maximala** parametern i **RandomNumberParameterSet** -parametern som en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="a7129-224">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="a7129-225">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a7129-225">RELATED LINKS</span></span>

[<span data-ttu-id="a7129-226">System. Security. Cryptography. RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="a7129-226">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="a7129-227">System, slumpmässig</span><span class="sxs-lookup"><span data-stu-id="a7129-227">Sytem.Random</span></span>](/dotnet/api/system.random)
