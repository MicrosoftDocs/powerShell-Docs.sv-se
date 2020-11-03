---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 644663c8871233bae84288f83492b518405d14ff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264362"
---
# <span data-ttu-id="f46d3-103">Get-Random</span><span class="sxs-lookup"><span data-stu-id="f46d3-103">Get-Random</span></span>

## <span data-ttu-id="f46d3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f46d3-104">SYNOPSIS</span></span>
<span data-ttu-id="f46d3-105">Hämtar ett slumpmässigt tal eller väljer objekt slumpmässigt från en samling.</span><span class="sxs-lookup"><span data-stu-id="f46d3-105">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="f46d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f46d3-106">SYNTAX</span></span>

### <span data-ttu-id="f46d3-107">RandomNumberParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f46d3-107">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="f46d3-108">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="f46d3-108">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="f46d3-109">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="f46d3-109">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="f46d3-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f46d3-110">DESCRIPTION</span></span>

<span data-ttu-id="f46d3-111">`Get-Random`Cmdleten hämtar ett slumpmässigt valt nummer.</span><span class="sxs-lookup"><span data-stu-id="f46d3-111">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="f46d3-112">Om du skickar en samling objekt till `Get-Random` hämtas ett eller flera slumpmässigt valda objekt från samlingen.</span><span class="sxs-lookup"><span data-stu-id="f46d3-112">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="f46d3-113">Utan parametrar eller Indatatyp `Get-Random` returnerar ett kommando ett slumpmässigt valt 32-bitars heltal utan tecken mellan 0 (noll) och **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="f46d3-113">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="f46d3-114">Du kan använda parametrarna för `Get-Random` för att ange ett start nummer, lägsta och högsta värde, antalet objekt som returneras från en inskickad samling och hela samlingen i en slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="f46d3-114">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, the number of objects returned from a submitted collection, and the entire collection in a random order.</span></span>

## <span data-ttu-id="f46d3-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f46d3-115">EXAMPLES</span></span>

### <span data-ttu-id="f46d3-116">Exempel 1: Hämta ett slumpmässigt heltal</span><span class="sxs-lookup"><span data-stu-id="f46d3-116">Example 1: Get a random integer</span></span>

<span data-ttu-id="f46d3-117">Det här kommandot hämtar ett slumpmässigt heltal mellan 0 (noll) och **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-117">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="f46d3-118">Exempel 2: Hämta ett slumpmässigt heltal mellan 0 och 99</span><span class="sxs-lookup"><span data-stu-id="f46d3-118">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="f46d3-119">Exempel 3: Hämta ett slumpmässigt heltal mellan-100 och 99</span><span class="sxs-lookup"><span data-stu-id="f46d3-119">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="f46d3-120">Exempel 4: Hämta ett slumpmässigt flytt ALS nummer</span><span class="sxs-lookup"><span data-stu-id="f46d3-120">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="f46d3-121">Det här kommandot hämtar ett slumpmässigt flytt ALS nummer som är större än eller lika med 10,7 och mindre än 20,92.</span><span class="sxs-lookup"><span data-stu-id="f46d3-121">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="f46d3-122">Exempel 5: Hämta ett slumpmässigt heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="f46d3-122">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="f46d3-123">Det här kommandot hämtar ett slumpmässigt valt nummer från den angivna matrisen.</span><span class="sxs-lookup"><span data-stu-id="f46d3-123">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="f46d3-124">Exempel 6: få flera slumpmässiga heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="f46d3-124">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="f46d3-125">Det här kommandot hämtar tre slumpmässigt markerade siffror i slumpmässig ordning från en matris.</span><span class="sxs-lookup"><span data-stu-id="f46d3-125">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="f46d3-126">Exempel 7: Slumpa en hel samling</span><span class="sxs-lookup"><span data-stu-id="f46d3-126">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="f46d3-127">Från och med PowerShell 7,1 kan du använda parametern **blanda** för att returnera hela samlingen i slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="f46d3-127">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### <span data-ttu-id="f46d3-128">Exempel 8: Hämta ett slumpmässigt icke-numeriskt värde</span><span class="sxs-lookup"><span data-stu-id="f46d3-128">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="f46d3-129">Det här kommandot returnerar ett slumpmässigt värde från en icke-numerisk samling.</span><span class="sxs-lookup"><span data-stu-id="f46d3-129">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="f46d3-130">Exempel 9: Använd parametern SetSeed</span><span class="sxs-lookup"><span data-stu-id="f46d3-130">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="f46d3-131">I det här exemplet visas effekterna av att använda parametern **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="f46d3-131">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="f46d3-132">Eftersom **SetSeed** genererar icke-slumpmässiga beteenden används vanligt vis endast för att återge resultat, till exempel vid fel sökning eller analys av ett skript.</span><span class="sxs-lookup"><span data-stu-id="f46d3-132">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="f46d3-133">Exempel 10: Hämta slumpmässiga filer</span><span class="sxs-lookup"><span data-stu-id="f46d3-133">Example 10: Get random files</span></span>

<span data-ttu-id="f46d3-134">Dessa kommandon får ett slumpmässigt valt exempel på 50 filer från den `C:` lokala datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="f46d3-134">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="f46d3-135">Exempel 11: sammanfatta verkliga tärningar</span><span class="sxs-lookup"><span data-stu-id="f46d3-135">Example 11: Roll fair dice</span></span>

<span data-ttu-id="f46d3-136">Det här exemplet rullar en rättvis Die 1200 gånger och räknar resultatet.</span><span class="sxs-lookup"><span data-stu-id="f46d3-136">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="f46d3-137">Det första kommandot `For-EachObject` upprepar anropet till `Get-Random` från skickas i siffror (1-6).</span><span class="sxs-lookup"><span data-stu-id="f46d3-137">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="f46d3-138">Resultaten grupperas efter deras värde med `Group-Object` och formaterats som en tabell med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-138">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="f46d3-139">Exempel 12: Använd Count-parametern</span><span class="sxs-lookup"><span data-stu-id="f46d3-139">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="f46d3-140">Du kan nu använda **Count** -parametern utan rör objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-140">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="f46d3-141">I följande exempel hämtas tre slumptal som är mindre än 10.</span><span class="sxs-lookup"><span data-stu-id="f46d3-141">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="f46d3-142">Exempel 13: Använd parametern InputObject med en tom sträng eller $null</span><span class="sxs-lookup"><span data-stu-id="f46d3-142">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="f46d3-143">I det här exemplet anger parametern **InputObject** en matris som innehåller en tom sträng ( `''` ) och `$null` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-143">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="f46d3-144">`Get-Random` returnerar antingen en `a` tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-144">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="f46d3-145">Den tomma STING visas som en tom rad och `$null` återgår till en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="f46d3-145">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="f46d3-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f46d3-146">PARAMETERS</span></span>

### <span data-ttu-id="f46d3-147">-Antal</span><span class="sxs-lookup"><span data-stu-id="f46d3-147">-Count</span></span>

<span data-ttu-id="f46d3-148">Anger antalet slumpmässiga objekt eller tal som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="f46d3-148">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="f46d3-149">Standard är 1.</span><span class="sxs-lookup"><span data-stu-id="f46d3-149">The default is 1.</span></span>

<span data-ttu-id="f46d3-150">`InputObject`Om värdet för **Count** överskrider antalet objekt i samlingen `Get-Random` returneras alla objekt i slumpmässig ordning när det används med.</span><span class="sxs-lookup"><span data-stu-id="f46d3-150">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f46d3-151">– InputObject</span><span class="sxs-lookup"><span data-stu-id="f46d3-151">-InputObject</span></span>

<span data-ttu-id="f46d3-152">Anger en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="f46d3-152">Specifies a collection of objects.</span></span> <span data-ttu-id="f46d3-153">`Get-Random` hämtar slumpmässigt valda objekt i slumpmässig ordning från samlingen upp till det antal som anges i **Count**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-153">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="f46d3-154">Ange objekten, en variabel som innehåller objekten, eller ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="f46d3-154">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="f46d3-155">Du kan också skicka en samling objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-155">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="f46d3-156">Från och med PowerShell 7 accepterar parametern **InputObject** matriser som kan innehålla en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-156">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="f46d3-157">Matrisen kan skickas nedåt i pipeline eller som ett **InputObject** -parameter värde.</span><span class="sxs-lookup"><span data-stu-id="f46d3-157">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f46d3-158">-Maximalt</span><span class="sxs-lookup"><span data-stu-id="f46d3-158">-Maximum</span></span>

<span data-ttu-id="f46d3-159">Anger ett max värde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="f46d3-159">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="f46d3-160">`Get-Random` Returnerar ett värde som är mindre än det maximala värdet (inte lika med).</span><span class="sxs-lookup"><span data-stu-id="f46d3-160">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="f46d3-161">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="f46d3-161">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="f46d3-162">Värdet för **maximum** måste vara större än (lika med) som **minimivärdet**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-162">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="f46d3-163">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="f46d3-163">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="f46d3-164">På en 64-bitars dator, om värdet för **minimum** är ett 32-bitars heltal **, är** standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-164">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="f46d3-165">Om **minimivärdet är ett** Double-värde (ett flytt ALS nummer) är standardvärdet **Max** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-165">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="f46d3-166">Annars är standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-166">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="f46d3-167">-Minst</span><span class="sxs-lookup"><span data-stu-id="f46d3-167">-Minimum</span></span>

<span data-ttu-id="f46d3-168">Anger ett minimivärde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="f46d3-168">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="f46d3-169">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="f46d3-169">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="f46d3-170">Standardvärdet är 0 (noll).</span><span class="sxs-lookup"><span data-stu-id="f46d3-170">The default value is 0 (zero).</span></span>

<span data-ttu-id="f46d3-171">**Minimivärdet måste vara** mindre än (lika med) som **Max** värde.</span><span class="sxs-lookup"><span data-stu-id="f46d3-171">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="f46d3-172">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="f46d3-172">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="f46d3-173">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="f46d3-173">-SetSeed</span></span>

<span data-ttu-id="f46d3-174">Anger ett Seed-värde för slump tals generatorn.</span><span class="sxs-lookup"><span data-stu-id="f46d3-174">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="f46d3-175">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="f46d3-175">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="f46d3-176">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="f46d3-176">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="f46d3-177">Parametern **SetSeed** är inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="f46d3-177">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="f46d3-178">Som standard `Get-Random` använder metoden [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) för att generera ett Seed-värde.</span><span class="sxs-lookup"><span data-stu-id="f46d3-178">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="f46d3-179">Eftersom **SetSeed** resulterar i ett icke-slumpmässigt beteende används det vanligt vis bara när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="f46d3-179">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

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

### <span data-ttu-id="f46d3-180">– Blanda</span><span class="sxs-lookup"><span data-stu-id="f46d3-180">-Shuffle</span></span>

<span data-ttu-id="f46d3-181">Returnerar hela samlingen i en slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="f46d3-181">Returns the entire collection in a randomized order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f46d3-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f46d3-182">CommonParameters</span></span>

<span data-ttu-id="f46d3-183">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f46d3-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f46d3-184">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f46d3-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f46d3-185">INDATA</span><span class="sxs-lookup"><span data-stu-id="f46d3-185">INPUTS</span></span>

### <span data-ttu-id="f46d3-186">System. Object</span><span class="sxs-lookup"><span data-stu-id="f46d3-186">System.Object</span></span>

<span data-ttu-id="f46d3-187">Du kan skicka ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="f46d3-187">You can pipe one or more objects.</span></span> <span data-ttu-id="f46d3-188">`Get-Random` väljer värden slumpmässigt från skickas-objekten.</span><span class="sxs-lookup"><span data-stu-id="f46d3-188">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="f46d3-189">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f46d3-189">OUTPUTS</span></span>

### <span data-ttu-id="f46d3-190">System. Int32, system. Int64, system. Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-190">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="f46d3-191">`Get-Random` Returnerar ett heltals-eller flytt ALS nummer, eller ett objekt som marker ATS slumpvis från en skickad samling.</span><span class="sxs-lookup"><span data-stu-id="f46d3-191">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="f46d3-192">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f46d3-192">NOTES</span></span>

<span data-ttu-id="f46d3-193">`Get-Random` ställer in ett standard-Seed för varje session baserat på system klockan när sessionen startar.</span><span class="sxs-lookup"><span data-stu-id="f46d3-193">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="f46d3-194">`Get-Random` returnerar inte alltid samma datatyp som indatavärdet.</span><span class="sxs-lookup"><span data-stu-id="f46d3-194">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="f46d3-195">I följande tabell visas utdatatypen för var och en av de numeriska inmatnings typerna.</span><span class="sxs-lookup"><span data-stu-id="f46d3-195">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="f46d3-196">Indatatyp</span><span class="sxs-lookup"><span data-stu-id="f46d3-196">Input Type</span></span> | <span data-ttu-id="f46d3-197">Utdatatyp</span><span class="sxs-lookup"><span data-stu-id="f46d3-197">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="f46d3-198">SByte</span><span class="sxs-lookup"><span data-stu-id="f46d3-198">SByte</span></span>    |   <span data-ttu-id="f46d3-199">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-199">Double</span></span>    |
|    <span data-ttu-id="f46d3-200">Byte</span><span class="sxs-lookup"><span data-stu-id="f46d3-200">Byte</span></span>    |   <span data-ttu-id="f46d3-201">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-201">Double</span></span>    |
|   <span data-ttu-id="f46d3-202">Int16</span><span class="sxs-lookup"><span data-stu-id="f46d3-202">Int16</span></span>    |   <span data-ttu-id="f46d3-203">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-203">Double</span></span>    |
|   <span data-ttu-id="f46d3-204">UInt16</span><span class="sxs-lookup"><span data-stu-id="f46d3-204">UInt16</span></span>   |   <span data-ttu-id="f46d3-205">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-205">Double</span></span>    |
|   <span data-ttu-id="f46d3-206">Int32</span><span class="sxs-lookup"><span data-stu-id="f46d3-206">Int32</span></span>    |    <span data-ttu-id="f46d3-207">Int32</span><span class="sxs-lookup"><span data-stu-id="f46d3-207">Int32</span></span>    |
|   <span data-ttu-id="f46d3-208">UInt32</span><span class="sxs-lookup"><span data-stu-id="f46d3-208">UInt32</span></span>   |   <span data-ttu-id="f46d3-209">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-209">Double</span></span>    |
|   <span data-ttu-id="f46d3-210">Int64</span><span class="sxs-lookup"><span data-stu-id="f46d3-210">Int64</span></span>    |    <span data-ttu-id="f46d3-211">Int64</span><span class="sxs-lookup"><span data-stu-id="f46d3-211">Int64</span></span>    |
|   <span data-ttu-id="f46d3-212">UInt64</span><span class="sxs-lookup"><span data-stu-id="f46d3-212">UInt64</span></span>   |   <span data-ttu-id="f46d3-213">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-213">Double</span></span>    |
|   <span data-ttu-id="f46d3-214">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-214">Double</span></span>   |   <span data-ttu-id="f46d3-215">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-215">Double</span></span>    |
|   <span data-ttu-id="f46d3-216">Enkel</span><span class="sxs-lookup"><span data-stu-id="f46d3-216">Single</span></span>   |   <span data-ttu-id="f46d3-217">Double</span><span class="sxs-lookup"><span data-stu-id="f46d3-217">Double</span></span>    |

<span data-ttu-id="f46d3-218">Från och med Windows PowerShell 3,0 `Get-Random` stöder 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="f46d3-218">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="f46d3-219">I Windows PowerShell 2,0 omvandlas alla värden till **system. Int32**.</span><span class="sxs-lookup"><span data-stu-id="f46d3-219">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="f46d3-220">Från och med PowerShell 7, **InputObject** -parametern i **RandomListItemParameterSet** -parameter uppsättningen, accepterar matriser som innehåller en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-220">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="f46d3-221">I tidigare PowerShell-versioner godkändes bara den **maximala** parametern i **RandomNumberParameterSet** -parametern som en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="f46d3-221">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="f46d3-222">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f46d3-222">RELATED LINKS</span></span>

