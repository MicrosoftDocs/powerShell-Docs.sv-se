---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 890088b91bd0d6e66e12cc5236272eeab842ed38
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710141"
---
# <span data-ttu-id="7e51f-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="7e51f-102">Get-Random</span></span>

## <span data-ttu-id="7e51f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7e51f-103">SYNOPSIS</span></span>
<span data-ttu-id="7e51f-104">Hämtar ett slumpmässigt tal eller väljer objekt slumpmässigt från en samling.</span><span class="sxs-lookup"><span data-stu-id="7e51f-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="7e51f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e51f-105">SYNTAX</span></span>

### <span data-ttu-id="7e51f-106">RandomNumberParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="7e51f-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="7e51f-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="7e51f-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="7e51f-108">ShuffleParameterSet</span><span class="sxs-lookup"><span data-stu-id="7e51f-108">ShuffleParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## <span data-ttu-id="7e51f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7e51f-109">DESCRIPTION</span></span>

<span data-ttu-id="7e51f-110">`Get-Random`Cmdleten hämtar ett slumpmässigt valt nummer.</span><span class="sxs-lookup"><span data-stu-id="7e51f-110">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="7e51f-111">Om du skickar en samling objekt till `Get-Random` hämtas ett eller flera slumpmässigt valda objekt från samlingen.</span><span class="sxs-lookup"><span data-stu-id="7e51f-111">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="7e51f-112">Utan parametrar eller Indatatyp `Get-Random` returnerar ett kommando ett slumpmässigt valt 32-bitars heltal utan tecken mellan 0 (noll) och **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="7e51f-112">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="7e51f-113">Du kan använda parametrarna för `Get-Random` för att ange ett start nummer, lägsta och högsta värde, antalet objekt som returneras från en inskickad samling och hela samlingen i en slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="7e51f-113">You can use the parameters of `Get-Random` to specify a seed number, minimum and maximum values, the number of objects returned from a submitted collection, and the entire collection in a random order.</span></span>

## <span data-ttu-id="7e51f-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7e51f-114">EXAMPLES</span></span>

### <span data-ttu-id="7e51f-115">Exempel 1: Hämta ett slumpmässigt heltal</span><span class="sxs-lookup"><span data-stu-id="7e51f-115">Example 1: Get a random integer</span></span>

<span data-ttu-id="7e51f-116">Det här kommandot hämtar ett slumpmässigt heltal mellan 0 (noll) och **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-116">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="7e51f-117">Exempel 2: Hämta ett slumpmässigt heltal mellan 0 och 99</span><span class="sxs-lookup"><span data-stu-id="7e51f-117">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="7e51f-118">Exempel 3: Hämta ett slumpmässigt heltal mellan-100 och 99</span><span class="sxs-lookup"><span data-stu-id="7e51f-118">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="7e51f-119">Exempel 4: Hämta ett slumpmässigt flytt ALS nummer</span><span class="sxs-lookup"><span data-stu-id="7e51f-119">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="7e51f-120">Det här kommandot hämtar ett slumpmässigt flytt ALS nummer som är större än eller lika med 10,7 och mindre än 20,92.</span><span class="sxs-lookup"><span data-stu-id="7e51f-120">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="7e51f-121">Exempel 5: Hämta ett slumpmässigt heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="7e51f-121">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="7e51f-122">Det här kommandot hämtar ett slumpmässigt valt nummer från den angivna matrisen.</span><span class="sxs-lookup"><span data-stu-id="7e51f-122">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="7e51f-123">Exempel 6: få flera slumpmässiga heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="7e51f-123">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="7e51f-124">Det här kommandot hämtar tre slumpmässigt markerade siffror i slumpmässig ordning från en matris.</span><span class="sxs-lookup"><span data-stu-id="7e51f-124">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="7e51f-125">Exempel 7: Slumpa en hel samling</span><span class="sxs-lookup"><span data-stu-id="7e51f-125">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="7e51f-126">Från och med PowerShell 7,1 kan du använda parametern **blanda** för att returnera hela samlingen i slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="7e51f-126">Starting in PowerShell 7.1, you can use the **Shuffle** parameter to return the entire collection in a random order.</span></span>

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

### <span data-ttu-id="7e51f-127">Exempel 8: Hämta ett slumpmässigt icke-numeriskt värde</span><span class="sxs-lookup"><span data-stu-id="7e51f-127">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="7e51f-128">Det här kommandot returnerar ett slumpmässigt värde från en icke-numerisk samling.</span><span class="sxs-lookup"><span data-stu-id="7e51f-128">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="7e51f-129">Exempel 9: Använd parametern SetSeed</span><span class="sxs-lookup"><span data-stu-id="7e51f-129">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="7e51f-130">I det här exemplet visas effekterna av att använda parametern **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="7e51f-130">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="7e51f-131">Eftersom **SetSeed** genererar icke-slumpmässiga beteenden används vanligt vis endast för att återge resultat, till exempel vid fel sökning eller analys av ett skript.</span><span class="sxs-lookup"><span data-stu-id="7e51f-131">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="7e51f-132">Exempel 10: Hämta slumpmässiga filer</span><span class="sxs-lookup"><span data-stu-id="7e51f-132">Example 10: Get random files</span></span>

<span data-ttu-id="7e51f-133">Dessa kommandon får ett slumpmässigt valt exempel på 50 filer från den `C:` lokala datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="7e51f-133">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="7e51f-134">Exempel 11: sammanfatta verkliga tärningar</span><span class="sxs-lookup"><span data-stu-id="7e51f-134">Example 11: Roll fair dice</span></span>

<span data-ttu-id="7e51f-135">Det här exemplet rullar en rättvis Die 1200 gånger och räknar resultatet.</span><span class="sxs-lookup"><span data-stu-id="7e51f-135">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="7e51f-136">Det första kommandot `For-EachObject` upprepar anropet till `Get-Random` från skickas i siffror (1-6).</span><span class="sxs-lookup"><span data-stu-id="7e51f-136">The first command, `For-EachObject` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="7e51f-137">Resultaten grupperas efter deras värde med `Group-Object` och formaterats som en tabell med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-137">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

### <span data-ttu-id="7e51f-138">Exempel 12: Använd Count-parametern</span><span class="sxs-lookup"><span data-stu-id="7e51f-138">Example 12: Use the Count parameter</span></span>

<span data-ttu-id="7e51f-139">Du kan nu använda **Count** -parametern utan rör objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-139">You can now use the **Count** parameter without piping objects to `Get-Random`.</span></span>
<span data-ttu-id="7e51f-140">I följande exempel hämtas tre slumptal som är mindre än 10.</span><span class="sxs-lookup"><span data-stu-id="7e51f-140">The following example gets three random numbers less than 10.</span></span>

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### <span data-ttu-id="7e51f-141">Exempel 13: Använd parametern InputObject med en tom sträng eller $null</span><span class="sxs-lookup"><span data-stu-id="7e51f-141">Example 13: Use the InputObject parameter with an empty string or $null</span></span>

<span data-ttu-id="7e51f-142">I det här exemplet anger parametern **InputObject** en matris som innehåller en tom sträng ( `''` ) och `$null` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-142">In this example, the **InputObject** parameter specifies an array that contains an empty string (`''`) and `$null`.</span></span>

```powershell
Get-Random -InputObject @('a','',$null)
```

<span data-ttu-id="7e51f-143">`Get-Random` returnerar antingen en `a` tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-143">`Get-Random` will return either `a`, empty string, or `$null`.</span></span> <span data-ttu-id="7e51f-144">Den tomma STING visas som en tom rad och `$null` återgår till en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="7e51f-144">The empty sting displays as a blank line and `$null` returns to a PowerShell prompt.</span></span>

## <span data-ttu-id="7e51f-145">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7e51f-145">PARAMETERS</span></span>

### <span data-ttu-id="7e51f-146">-Antal</span><span class="sxs-lookup"><span data-stu-id="7e51f-146">-Count</span></span>

<span data-ttu-id="7e51f-147">Anger antalet slumpmässiga objekt eller tal som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="7e51f-147">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="7e51f-148">Standard är 1.</span><span class="sxs-lookup"><span data-stu-id="7e51f-148">The default is 1.</span></span>

<span data-ttu-id="7e51f-149">`InputObject`Om värdet för **Count** överskrider antalet objekt i samlingen `Get-Random` returneras alla objekt i slumpmässig ordning när det används med.</span><span class="sxs-lookup"><span data-stu-id="7e51f-149">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

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

### <span data-ttu-id="7e51f-150">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7e51f-150">-InputObject</span></span>

<span data-ttu-id="7e51f-151">Anger en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="7e51f-151">Specifies a collection of objects.</span></span> <span data-ttu-id="7e51f-152">`Get-Random` hämtar slumpmässigt valda objekt i slumpmässig ordning från samlingen upp till det antal som anges i **Count**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-152">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="7e51f-153">Ange objekten, en variabel som innehåller objekten, eller ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="7e51f-153">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="7e51f-154">Du kan också skicka en samling objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-154">You can also pipe a collection of objects to `Get-Random`.</span></span>

<span data-ttu-id="7e51f-155">Från och med PowerShell 7 accepterar parametern **InputObject** matriser som kan innehålla en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-155">Beginning in PowerShell 7, the **InputObject** parameter accepts arrays that can contain an empty string or `$null`.</span></span> <span data-ttu-id="7e51f-156">Matrisen kan skickas nedåt i pipeline eller som ett **InputObject** -parameter värde.</span><span class="sxs-lookup"><span data-stu-id="7e51f-156">The array can be sent down the pipeline or as an **InputObject** parameter value.</span></span>

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

### <span data-ttu-id="7e51f-157">-Maximalt</span><span class="sxs-lookup"><span data-stu-id="7e51f-157">-Maximum</span></span>

<span data-ttu-id="7e51f-158">Anger ett max värde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="7e51f-158">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="7e51f-159">`Get-Random` Returnerar ett värde som är mindre än det maximala värdet (inte lika med).</span><span class="sxs-lookup"><span data-stu-id="7e51f-159">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="7e51f-160">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="7e51f-160">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="7e51f-161">Värdet för **maximum** måste vara större än (lika med) som **minimivärdet**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-161">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="7e51f-162">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="7e51f-162">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="7e51f-163">På en 64-bitars dator, om värdet för **minimum** är ett 32-bitars heltal **, är** standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-163">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="7e51f-164">Om **minimivärdet är ett** Double-värde (ett flytt ALS nummer) är standardvärdet **Max** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-164">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="7e51f-165">Annars är standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-165">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="7e51f-166">-Minst</span><span class="sxs-lookup"><span data-stu-id="7e51f-166">-Minimum</span></span>

<span data-ttu-id="7e51f-167">Anger ett minimivärde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="7e51f-167">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="7e51f-168">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="7e51f-168">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="7e51f-169">Standardvärdet är 0 (noll).</span><span class="sxs-lookup"><span data-stu-id="7e51f-169">The default value is 0 (zero).</span></span>

<span data-ttu-id="7e51f-170">**Minimivärdet måste vara** mindre än (lika med) som **Max** värde.</span><span class="sxs-lookup"><span data-stu-id="7e51f-170">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="7e51f-171">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="7e51f-171">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="7e51f-172">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="7e51f-172">-SetSeed</span></span>

<span data-ttu-id="7e51f-173">Anger ett Seed-värde för slump tals generatorn.</span><span class="sxs-lookup"><span data-stu-id="7e51f-173">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="7e51f-174">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="7e51f-174">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="7e51f-175">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7e51f-175">You can't reset the seed to its default value.</span></span>

<span data-ttu-id="7e51f-176">Parametern **SetSeed** är inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="7e51f-176">The **SetSeed** parameter is not required.</span></span> <span data-ttu-id="7e51f-177">Som standard `Get-Random` använder metoden [RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator) för att generera ett Seed-värde.</span><span class="sxs-lookup"><span data-stu-id="7e51f-177">By default, `Get-Random` uses the [RandomNumberGenerator()](/dotnet/api/system.security.cryptography.randomnumbergenerator) method to generate a seed value.</span></span> <span data-ttu-id="7e51f-178">Eftersom **SetSeed** resulterar i ett icke-slumpmässigt beteende används det vanligt vis bara när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="7e51f-178">Because **SetSeed** results in non-random behavior, it's typically used only when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>

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

### <span data-ttu-id="7e51f-179">– Blanda</span><span class="sxs-lookup"><span data-stu-id="7e51f-179">-Shuffle</span></span>

<span data-ttu-id="7e51f-180">Returnerar hela samlingen i en slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="7e51f-180">Returns the entire collection in a randomized order.</span></span>

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

### <span data-ttu-id="7e51f-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e51f-181">CommonParameters</span></span>

<span data-ttu-id="7e51f-182">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e51f-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e51f-183">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e51f-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e51f-184">INDATA</span><span class="sxs-lookup"><span data-stu-id="7e51f-184">INPUTS</span></span>

### <span data-ttu-id="7e51f-185">System. Object</span><span class="sxs-lookup"><span data-stu-id="7e51f-185">System.Object</span></span>

<span data-ttu-id="7e51f-186">Du kan skicka ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="7e51f-186">You can pipe one or more objects.</span></span> <span data-ttu-id="7e51f-187">`Get-Random` väljer värden slumpmässigt från skickas-objekten.</span><span class="sxs-lookup"><span data-stu-id="7e51f-187">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="7e51f-188">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7e51f-188">OUTPUTS</span></span>

### <span data-ttu-id="7e51f-189">System. Int32, system. Int64, system. Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-189">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="7e51f-190">`Get-Random` Returnerar ett heltals-eller flytt ALS nummer, eller ett objekt som marker ATS slumpvis från en skickad samling.</span><span class="sxs-lookup"><span data-stu-id="7e51f-190">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="7e51f-191">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7e51f-191">NOTES</span></span>

<span data-ttu-id="7e51f-192">`Get-Random` ställer in ett standard-Seed för varje session baserat på system klockan när sessionen startar.</span><span class="sxs-lookup"><span data-stu-id="7e51f-192">`Get-Random` sets a default seed for each session based on the system time clock when the session starts.</span></span>

<span data-ttu-id="7e51f-193">`Get-Random` returnerar inte alltid samma datatyp som indatavärdet.</span><span class="sxs-lookup"><span data-stu-id="7e51f-193">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="7e51f-194">I följande tabell visas utdatatypen för var och en av de numeriska inmatnings typerna.</span><span class="sxs-lookup"><span data-stu-id="7e51f-194">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="7e51f-195">Indatatyp</span><span class="sxs-lookup"><span data-stu-id="7e51f-195">Input Type</span></span> | <span data-ttu-id="7e51f-196">Utdatatyp</span><span class="sxs-lookup"><span data-stu-id="7e51f-196">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="7e51f-197">SByte</span><span class="sxs-lookup"><span data-stu-id="7e51f-197">SByte</span></span>    |   <span data-ttu-id="7e51f-198">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-198">Double</span></span>    |
|    <span data-ttu-id="7e51f-199">Byte</span><span class="sxs-lookup"><span data-stu-id="7e51f-199">Byte</span></span>    |   <span data-ttu-id="7e51f-200">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-200">Double</span></span>    |
|   <span data-ttu-id="7e51f-201">Int16</span><span class="sxs-lookup"><span data-stu-id="7e51f-201">Int16</span></span>    |   <span data-ttu-id="7e51f-202">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-202">Double</span></span>    |
|   <span data-ttu-id="7e51f-203">UInt16</span><span class="sxs-lookup"><span data-stu-id="7e51f-203">UInt16</span></span>   |   <span data-ttu-id="7e51f-204">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-204">Double</span></span>    |
|   <span data-ttu-id="7e51f-205">Int32</span><span class="sxs-lookup"><span data-stu-id="7e51f-205">Int32</span></span>    |    <span data-ttu-id="7e51f-206">Int32</span><span class="sxs-lookup"><span data-stu-id="7e51f-206">Int32</span></span>    |
|   <span data-ttu-id="7e51f-207">UInt32</span><span class="sxs-lookup"><span data-stu-id="7e51f-207">UInt32</span></span>   |   <span data-ttu-id="7e51f-208">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-208">Double</span></span>    |
|   <span data-ttu-id="7e51f-209">Int64</span><span class="sxs-lookup"><span data-stu-id="7e51f-209">Int64</span></span>    |    <span data-ttu-id="7e51f-210">Int64</span><span class="sxs-lookup"><span data-stu-id="7e51f-210">Int64</span></span>    |
|   <span data-ttu-id="7e51f-211">UInt64</span><span class="sxs-lookup"><span data-stu-id="7e51f-211">UInt64</span></span>   |   <span data-ttu-id="7e51f-212">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-212">Double</span></span>    |
|   <span data-ttu-id="7e51f-213">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-213">Double</span></span>   |   <span data-ttu-id="7e51f-214">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-214">Double</span></span>    |
|   <span data-ttu-id="7e51f-215">Enskilt</span><span class="sxs-lookup"><span data-stu-id="7e51f-215">Single</span></span>   |   <span data-ttu-id="7e51f-216">Double</span><span class="sxs-lookup"><span data-stu-id="7e51f-216">Double</span></span>    |

<span data-ttu-id="7e51f-217">Från och med Windows PowerShell 3,0 `Get-Random` stöder 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="7e51f-217">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="7e51f-218">I Windows PowerShell 2,0 omvandlas alla värden till **system. Int32**.</span><span class="sxs-lookup"><span data-stu-id="7e51f-218">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

<span data-ttu-id="7e51f-219">Från och med PowerShell 7, **InputObject** -parametern i **RandomListItemParameterSet** -parameter uppsättningen, accepterar matriser som innehåller en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-219">Beginning in PowerShell 7, the **InputObject** parameter in the **RandomListItemParameterSet** parameter set accepts arrays that contain an empty string or `$null`.</span></span> <span data-ttu-id="7e51f-220">I tidigare PowerShell-versioner godkändes bara den **maximala** parametern i **RandomNumberParameterSet** -parametern som en tom sträng eller `$null` .</span><span class="sxs-lookup"><span data-stu-id="7e51f-220">In earlier PowerShell versions, only the **Maximum** parameter in the **RandomNumberParameterSet** parameter set accepted an empty string or `$null`.</span></span>

## <span data-ttu-id="7e51f-221">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7e51f-221">RELATED LINKS</span></span>

