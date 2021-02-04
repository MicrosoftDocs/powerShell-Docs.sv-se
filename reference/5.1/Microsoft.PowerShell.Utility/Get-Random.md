---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 97576832ea851f01b463f63948fbd80028c9a6fb
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2021
ms.locfileid: "99495850"
---
# <span data-ttu-id="314f5-102">Get-Random</span><span class="sxs-lookup"><span data-stu-id="314f5-102">Get-Random</span></span>

## <span data-ttu-id="314f5-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="314f5-103">SYNOPSIS</span></span>
<span data-ttu-id="314f5-104">Hämtar ett slumpmässigt tal eller väljer objekt slumpmässigt från en samling.</span><span class="sxs-lookup"><span data-stu-id="314f5-104">Gets a random number, or selects objects randomly from a collection.</span></span>

## <span data-ttu-id="314f5-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="314f5-105">SYNTAX</span></span>

### <span data-ttu-id="314f5-106">RandomNumberParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="314f5-106">RandomNumberParameterSet (Default)</span></span>

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [<CommonParameters>]
```

### <span data-ttu-id="314f5-107">RandomListItemParameterSet</span><span class="sxs-lookup"><span data-stu-id="314f5-107">RandomListItemParameterSet</span></span>

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="314f5-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="314f5-108">DESCRIPTION</span></span>

<span data-ttu-id="314f5-109">`Get-Random`Cmdleten hämtar ett slumpmässigt valt nummer.</span><span class="sxs-lookup"><span data-stu-id="314f5-109">The `Get-Random` cmdlet gets a randomly selected number.</span></span> <span data-ttu-id="314f5-110">Om du skickar en samling objekt till `Get-Random` hämtas ett eller flera slumpmässigt valda objekt från samlingen.</span><span class="sxs-lookup"><span data-stu-id="314f5-110">If you submit a collection of objects to `Get-Random`, it gets one or more randomly selected objects from the collection.</span></span>

<span data-ttu-id="314f5-111">Utan parametrar eller Indatatyp `Get-Random` returnerar ett kommando ett slumpmässigt valt 32-bitars heltal utan tecken mellan 0 (noll) och **Int32. MaxValue** ( `0x7FFFFFFF` , `2,147,483,647` ).</span><span class="sxs-lookup"><span data-stu-id="314f5-111">Without parameters or input, a `Get-Random` command returns a randomly selected 32-bit unsigned integer between 0 (zero) and **Int32.MaxValue** (`0x7FFFFFFF`, `2,147,483,647`).</span></span>

<span data-ttu-id="314f5-112">Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="314f5-112">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="314f5-113">Du kan använda parametrarna för `Get-Random` för att ange lägsta och högsta värden, antalet objekt som returneras från en samling eller ett start nummer.</span><span class="sxs-lookup"><span data-stu-id="314f5-113">You can use the parameters of `Get-Random` to specify the minimum and maximum values, the number of objects returned from a collection, or a seed number.</span></span>

> [!CAUTION]
> <span data-ttu-id="314f5-114">Att ställa in startvärdet för ett avsiktligt resultat i icke-slumpmässig, repeterbar funktion.</span><span class="sxs-lookup"><span data-stu-id="314f5-114">Setting the seed deliberately results in non-random, repeatable behavior.</span></span> <span data-ttu-id="314f5-115">Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="314f5-115">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="314f5-116">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="314f5-116">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="314f5-117">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="314f5-117">You can't reset the seed to its default value.</span></span>

## <span data-ttu-id="314f5-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="314f5-118">EXAMPLES</span></span>

### <span data-ttu-id="314f5-119">Exempel 1: Hämta ett slumpmässigt heltal</span><span class="sxs-lookup"><span data-stu-id="314f5-119">Example 1: Get a random integer</span></span>

<span data-ttu-id="314f5-120">Det här kommandot hämtar ett slumpmässigt heltal mellan 0 (noll) och **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="314f5-120">This command gets a random integer between 0 (zero) and **Int32.MaxValue**.</span></span>

```powershell
Get-Random
```

```Output
3951433
```

### <span data-ttu-id="314f5-121">Exempel 2: Hämta ett slumpmässigt heltal mellan 0 och 99</span><span class="sxs-lookup"><span data-stu-id="314f5-121">Example 2: Get a random integer between 0 and 99</span></span>

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### <span data-ttu-id="314f5-122">Exempel 3: Hämta ett slumpmässigt heltal mellan-100 och 99</span><span class="sxs-lookup"><span data-stu-id="314f5-122">Example 3: Get a random integer between -100 and 99</span></span>

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### <span data-ttu-id="314f5-123">Exempel 4: Hämta ett slumpmässigt flytt ALS nummer</span><span class="sxs-lookup"><span data-stu-id="314f5-123">Example 4: Get a random floating-point number</span></span>

<span data-ttu-id="314f5-124">Det här kommandot hämtar ett slumpmässigt flytt ALS nummer som är större än eller lika med 10,7 och mindre än 20,92.</span><span class="sxs-lookup"><span data-stu-id="314f5-124">This command gets a random floating-point number greater than or equal to 10.7 and less than 20.92.</span></span>

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### <span data-ttu-id="314f5-125">Exempel 5: Hämta ett slumpmässigt heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="314f5-125">Example 5: Get a random integer from an array</span></span>

<span data-ttu-id="314f5-126">Det här kommandot hämtar ett slumpmässigt valt nummer från den angivna matrisen.</span><span class="sxs-lookup"><span data-stu-id="314f5-126">This command gets a randomly selected number from the specified array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### <span data-ttu-id="314f5-127">Exempel 6: få flera slumpmässiga heltal från en matris</span><span class="sxs-lookup"><span data-stu-id="314f5-127">Example 6: Get several random integers from an array</span></span>

<span data-ttu-id="314f5-128">Det här kommandot hämtar tre slumpmässigt markerade siffror i slumpmässig ordning från en matris.</span><span class="sxs-lookup"><span data-stu-id="314f5-128">This command gets three randomly selected numbers in random order from an array.</span></span>

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### <span data-ttu-id="314f5-129">Exempel 7: Slumpa en hel samling</span><span class="sxs-lookup"><span data-stu-id="314f5-129">Example 7: Randomize an entire collection</span></span>

<span data-ttu-id="314f5-130">Det här kommandot returnerar hela samlingen i slumpmässig ordning.</span><span class="sxs-lookup"><span data-stu-id="314f5-130">This command returns the entire collection in random order.</span></span>

<span data-ttu-id="314f5-131">Värdet för **Count** -parametern är egenskapen **MaxValue** static för heltal.</span><span class="sxs-lookup"><span data-stu-id="314f5-131">The value of the **Count** parameter is the **MaxValue** static property of integers.</span></span>

<span data-ttu-id="314f5-132">Om du vill returnera en hel samling i slumpmässig ordning anger du ett tal som är större än eller lika med antalet objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="314f5-132">To return an entire collection in random order, enter any number that is greater than or equal to the number of objects in the collection.</span></span>

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

### <span data-ttu-id="314f5-133">Exempel 8: Hämta ett slumpmässigt icke-numeriskt värde</span><span class="sxs-lookup"><span data-stu-id="314f5-133">Example 8: Get a random non-numeric value</span></span>

<span data-ttu-id="314f5-134">Det här kommandot returnerar ett slumpmässigt värde från en icke-numerisk samling.</span><span class="sxs-lookup"><span data-stu-id="314f5-134">This command returns a random value from a non-numeric collection.</span></span>

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### <span data-ttu-id="314f5-135">Exempel 9: Använd parametern SetSeed</span><span class="sxs-lookup"><span data-stu-id="314f5-135">Example 9: Use the SetSeed parameter</span></span>

<span data-ttu-id="314f5-136">I det här exemplet visas effekterna av att använda parametern **SetSeed** .</span><span class="sxs-lookup"><span data-stu-id="314f5-136">This example shows the effect of using the **SetSeed** parameter.</span></span>

<span data-ttu-id="314f5-137">Eftersom **SetSeed** genererar icke-slumpmässiga beteenden används vanligt vis endast för att återge resultat, till exempel vid fel sökning eller analys av ett skript.</span><span class="sxs-lookup"><span data-stu-id="314f5-137">Because **SetSeed** produces non-random behavior, it's typically used only to reproduce results, such as when debugging or analyzing a script.</span></span>

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

### <span data-ttu-id="314f5-138">Exempel 10: Hämta slumpmässiga filer</span><span class="sxs-lookup"><span data-stu-id="314f5-138">Example 10: Get random files</span></span>

<span data-ttu-id="314f5-139">Dessa kommandon får ett slumpmässigt valt exempel på 50 filer från den `C:` lokala datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="314f5-139">These commands get a randomly selected sample of 50 files from the `C:` drive of the local computer.</span></span>

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### <span data-ttu-id="314f5-140">Exempel 11: sammanfatta verkliga tärningar</span><span class="sxs-lookup"><span data-stu-id="314f5-140">Example 11: Roll fair dice</span></span>

<span data-ttu-id="314f5-141">Det här exemplet rullar en rättvis Die 1200 gånger och räknar resultatet.</span><span class="sxs-lookup"><span data-stu-id="314f5-141">This example rolls a fair die 1200 times and counts the outcomes.</span></span> <span data-ttu-id="314f5-142">Det första kommandot `ForEach-Object` upprepar anropet till `Get-Random` från skickas i siffror (1-6).</span><span class="sxs-lookup"><span data-stu-id="314f5-142">The first command, `ForEach-Object` repeats the call to `Get-Random` from the piped in numbers (1-6).</span></span> <span data-ttu-id="314f5-143">Resultaten grupperas efter deras värde med `Group-Object` och formaterats som en tabell med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="314f5-143">The results are grouped by their value with `Group-Object` and formatted as a table with `Select-Object`.</span></span>

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

## <span data-ttu-id="314f5-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="314f5-144">PARAMETERS</span></span>

### <span data-ttu-id="314f5-145">-Antal</span><span class="sxs-lookup"><span data-stu-id="314f5-145">-Count</span></span>

<span data-ttu-id="314f5-146">Anger antalet slumpmässiga objekt eller tal som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="314f5-146">Specifies the number of random objects or numbers to return.</span></span> <span data-ttu-id="314f5-147">Standard är 1.</span><span class="sxs-lookup"><span data-stu-id="314f5-147">The default is 1.</span></span>

<span data-ttu-id="314f5-148">`InputObject`Om värdet för **Count** överskrider antalet objekt i samlingen `Get-Random` returneras alla objekt i slumpmässig ordning när det används med.</span><span class="sxs-lookup"><span data-stu-id="314f5-148">When used with `InputObject`, if the value of **Count** exceeds the number of objects in the collection, `Get-Random` returns all of the objects in random order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="314f5-149">– InputObject</span><span class="sxs-lookup"><span data-stu-id="314f5-149">-InputObject</span></span>

<span data-ttu-id="314f5-150">Anger en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="314f5-150">Specifies a collection of objects.</span></span> <span data-ttu-id="314f5-151">`Get-Random` hämtar slumpmässigt valda objekt i slumpmässig ordning från samlingen upp till det antal som anges i **Count**.</span><span class="sxs-lookup"><span data-stu-id="314f5-151">`Get-Random` gets randomly selected objects in random order from the collection up to the number specified by **Count**.</span></span> <span data-ttu-id="314f5-152">Ange objekten, en variabel som innehåller objekten, eller ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="314f5-152">Enter the objects, a variable that contains the objects, or a command or expression that gets the objects.</span></span> <span data-ttu-id="314f5-153">Du kan också skicka en samling objekt till `Get-Random` .</span><span class="sxs-lookup"><span data-stu-id="314f5-153">You can also pipe a collection of objects to `Get-Random`.</span></span>

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

### <span data-ttu-id="314f5-154">-Maximalt</span><span class="sxs-lookup"><span data-stu-id="314f5-154">-Maximum</span></span>

<span data-ttu-id="314f5-155">Anger ett max värde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="314f5-155">Specifies a maximum value for the random number.</span></span> <span data-ttu-id="314f5-156">`Get-Random` Returnerar ett värde som är mindre än det maximala värdet (inte lika med).</span><span class="sxs-lookup"><span data-stu-id="314f5-156">`Get-Random` returns a value that is less than the maximum (not equal).</span></span> <span data-ttu-id="314f5-157">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="314f5-157">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span>

<span data-ttu-id="314f5-158">Värdet för **maximum** måste vara större än (lika med) som **minimivärdet**.</span><span class="sxs-lookup"><span data-stu-id="314f5-158">The value of **Maximum** must be greater than (not equal to) the value of **Minimum**.</span></span> <span data-ttu-id="314f5-159">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="314f5-159">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

<span data-ttu-id="314f5-160">På en 64-bitars dator, om värdet för **minimum** är ett 32-bitars heltal **, är** standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="314f5-160">On a 64-bit computer, if the value of **Minimum** is a 32-bit integer, the default value of **Maximum** is **Int32.MaxValue**.</span></span>

<span data-ttu-id="314f5-161">Om **minimivärdet är ett** Double-värde (ett flytt ALS nummer) är standardvärdet **Max** **Double. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="314f5-161">If the value of **Minimum** is a double (a floating-point number), the default value of **Maximum** is **Double.MaxValue**.</span></span> <span data-ttu-id="314f5-162">Annars är standardvärdet **Int32. MaxValue**.</span><span class="sxs-lookup"><span data-stu-id="314f5-162">Otherwise, the default value is **Int32.MaxValue**.</span></span>

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

### <span data-ttu-id="314f5-163">-Minst</span><span class="sxs-lookup"><span data-stu-id="314f5-163">-Minimum</span></span>

<span data-ttu-id="314f5-164">Anger ett minimivärde för det slumpmässiga talet.</span><span class="sxs-lookup"><span data-stu-id="314f5-164">Specifies a minimum value for the random number.</span></span> <span data-ttu-id="314f5-165">Ange ett heltal, ett flyttal med dubbel precision eller ett objekt som kan konverteras till ett heltal eller dubbelt, till exempel en numerisk sträng ("100").</span><span class="sxs-lookup"><span data-stu-id="314f5-165">Enter an integer, a double-precision floating-point number, or an object that can be converted to an integer or double, such as a numeric string ("100").</span></span> <span data-ttu-id="314f5-166">Standardvärdet är 0 (noll).</span><span class="sxs-lookup"><span data-stu-id="314f5-166">The default value is 0 (zero).</span></span>

<span data-ttu-id="314f5-167">**Minimivärdet måste vara** mindre än (lika med) som **Max** värde.</span><span class="sxs-lookup"><span data-stu-id="314f5-167">The value of **Minimum** must be less than (not equal to) the value of **Maximum**.</span></span> <span data-ttu-id="314f5-168">Om värdet för **maximum** eller **minimum** är ett flytt ALS nummer `Get-Random` returnerar ett slumpmässigt valt flyttal.</span><span class="sxs-lookup"><span data-stu-id="314f5-168">If the value of **Maximum** or **Minimum** is a floating-point number, `Get-Random` returns a randomly selected floating-point number.</span></span>

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

### <span data-ttu-id="314f5-169">-SetSeed</span><span class="sxs-lookup"><span data-stu-id="314f5-169">-SetSeed</span></span>

<span data-ttu-id="314f5-170">Anger ett Seed-värde för slump tals generatorn.</span><span class="sxs-lookup"><span data-stu-id="314f5-170">Specifies a seed value for the random number generator.</span></span> <span data-ttu-id="314f5-171">När du använder **SetSeed** använder cmdlet: en [system. Random](/dotnet/api/system.random) -metod för att generera pseudorandom-nummer som inte är kryptografiskt säkra.</span><span class="sxs-lookup"><span data-stu-id="314f5-171">When you use **SetSeed**, the cmdlet uses the [System.Random](/dotnet/api/system.random) method to generate pseudorandom numbers, which is not cryptographically secure.</span></span>

> [!CAUTION]
> <span data-ttu-id="314f5-172">Inställning av Dirigerings resultat i icke-slumpmässiga beteenden.</span><span class="sxs-lookup"><span data-stu-id="314f5-172">Setting the seed results in non-random behavior.</span></span> <span data-ttu-id="314f5-173">Den bör endast användas när du försöker återskapa beteende, till exempel vid fel sökning eller analys av ett skript som innehåller `Get-Random` kommandon.</span><span class="sxs-lookup"><span data-stu-id="314f5-173">It should only be used when trying to reproduce behavior, such as when debugging or analyzing a script that includes `Get-Random` commands.</span></span>
>
> <span data-ttu-id="314f5-174">Det här dirigering svärdet används för det aktuella kommandot och för alla efterföljande `Get-Random` kommandon i den aktuella sessionen tills du använder **SetSeed** igen eller stänger sessionen.</span><span class="sxs-lookup"><span data-stu-id="314f5-174">This seed value is used for the current command and for all subsequent `Get-Random` commands in the current session until you use **SetSeed** again or close the session.</span></span> <span data-ttu-id="314f5-175">Du kan inte återställa startvärdet till dess standardvärde.</span><span class="sxs-lookup"><span data-stu-id="314f5-175">You can't reset the seed to its default value.</span></span>

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

### <span data-ttu-id="314f5-176">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="314f5-176">CommonParameters</span></span>

<span data-ttu-id="314f5-177">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="314f5-177">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="314f5-178">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="314f5-178">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="314f5-179">INDATA</span><span class="sxs-lookup"><span data-stu-id="314f5-179">INPUTS</span></span>

### <span data-ttu-id="314f5-180">System. Object</span><span class="sxs-lookup"><span data-stu-id="314f5-180">System.Object</span></span>

<span data-ttu-id="314f5-181">Du kan skicka ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="314f5-181">You can pipe one or more objects.</span></span> <span data-ttu-id="314f5-182">`Get-Random` väljer värden slumpmässigt från skickas-objekten.</span><span class="sxs-lookup"><span data-stu-id="314f5-182">`Get-Random` selects values randomly from the piped objects.</span></span>

## <span data-ttu-id="314f5-183">UTDATA</span><span class="sxs-lookup"><span data-stu-id="314f5-183">OUTPUTS</span></span>

### <span data-ttu-id="314f5-184">System. Int32, system. Int64, system. Double</span><span class="sxs-lookup"><span data-stu-id="314f5-184">System.Int32, System.Int64, System.Double</span></span>

<span data-ttu-id="314f5-185">`Get-Random` Returnerar ett heltals-eller flytt ALS nummer, eller ett objekt som marker ATS slumpvis från en skickad samling.</span><span class="sxs-lookup"><span data-stu-id="314f5-185">`Get-Random` returns an integer or floating-point number, or an object selected randomly from a submitted collection.</span></span>

## <span data-ttu-id="314f5-186">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="314f5-186">NOTES</span></span>

<span data-ttu-id="314f5-187">Som standard `Get-Random` genererar kryptografiskt säker slumpmässig het med klassen [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) .</span><span class="sxs-lookup"><span data-stu-id="314f5-187">By default, `Get-Random` generates cryptographically secure randomness using the [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) class.</span></span>

<span data-ttu-id="314f5-188">`Get-Random` returnerar inte alltid samma datatyp som indatavärdet.</span><span class="sxs-lookup"><span data-stu-id="314f5-188">`Get-Random` does not alway return the same data type as the input value.</span></span> <span data-ttu-id="314f5-189">I följande tabell visas utdatatypen för var och en av de numeriska inmatnings typerna.</span><span class="sxs-lookup"><span data-stu-id="314f5-189">The following table shows the output type for each of the numeric input types.</span></span>

| <span data-ttu-id="314f5-190">Indatatyp</span><span class="sxs-lookup"><span data-stu-id="314f5-190">Input Type</span></span> | <span data-ttu-id="314f5-191">Utdatatyp</span><span class="sxs-lookup"><span data-stu-id="314f5-191">Output Type</span></span> |
| :--------: | :---------: |
|   <span data-ttu-id="314f5-192">SByte</span><span class="sxs-lookup"><span data-stu-id="314f5-192">SByte</span></span>    |   <span data-ttu-id="314f5-193">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-193">Double</span></span>    |
|    <span data-ttu-id="314f5-194">Byte</span><span class="sxs-lookup"><span data-stu-id="314f5-194">Byte</span></span>    |   <span data-ttu-id="314f5-195">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-195">Double</span></span>    |
|   <span data-ttu-id="314f5-196">Int16</span><span class="sxs-lookup"><span data-stu-id="314f5-196">Int16</span></span>    |   <span data-ttu-id="314f5-197">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-197">Double</span></span>    |
|   <span data-ttu-id="314f5-198">UInt16</span><span class="sxs-lookup"><span data-stu-id="314f5-198">UInt16</span></span>   |   <span data-ttu-id="314f5-199">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-199">Double</span></span>    |
|   <span data-ttu-id="314f5-200">Int32</span><span class="sxs-lookup"><span data-stu-id="314f5-200">Int32</span></span>    |    <span data-ttu-id="314f5-201">Int32</span><span class="sxs-lookup"><span data-stu-id="314f5-201">Int32</span></span>    |
|   <span data-ttu-id="314f5-202">UInt32</span><span class="sxs-lookup"><span data-stu-id="314f5-202">UInt32</span></span>   |   <span data-ttu-id="314f5-203">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-203">Double</span></span>    |
|   <span data-ttu-id="314f5-204">Int64</span><span class="sxs-lookup"><span data-stu-id="314f5-204">Int64</span></span>    |    <span data-ttu-id="314f5-205">Int64</span><span class="sxs-lookup"><span data-stu-id="314f5-205">Int64</span></span>    |
|   <span data-ttu-id="314f5-206">UInt64</span><span class="sxs-lookup"><span data-stu-id="314f5-206">UInt64</span></span>   |   <span data-ttu-id="314f5-207">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-207">Double</span></span>    |
|   <span data-ttu-id="314f5-208">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-208">Double</span></span>   |   <span data-ttu-id="314f5-209">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-209">Double</span></span>    |
|   <span data-ttu-id="314f5-210">Enkel</span><span class="sxs-lookup"><span data-stu-id="314f5-210">Single</span></span>   |   <span data-ttu-id="314f5-211">Double</span><span class="sxs-lookup"><span data-stu-id="314f5-211">Double</span></span>    |

<span data-ttu-id="314f5-212">Från och med Windows PowerShell 3,0 `Get-Random` stöder 64-bitars heltal.</span><span class="sxs-lookup"><span data-stu-id="314f5-212">Beginning in Windows PowerShell 3.0, `Get-Random` supports 64-bit integers.</span></span> <span data-ttu-id="314f5-213">I Windows PowerShell 2,0 omvandlas alla värden till **system. Int32**.</span><span class="sxs-lookup"><span data-stu-id="314f5-213">In Windows PowerShell 2.0, all values are cast to **System.Int32**.</span></span>

## <span data-ttu-id="314f5-214">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="314f5-214">RELATED LINKS</span></span>

[<span data-ttu-id="314f5-215">System. Security. Cryptography. RandomNumberGenerator ()</span><span class="sxs-lookup"><span data-stu-id="314f5-215">System.Security.Cryptography.RandomNumberGenerator()</span></span>](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[<span data-ttu-id="314f5-216">System, slumpmässig</span><span class="sxs-lookup"><span data-stu-id="314f5-216">Sytem.Random</span></span>](/dotnet/api/system.random)
