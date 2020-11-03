---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/measure-object?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Measure-Object
ms.openlocfilehash: a4d80876136ca2c5837be9288c22776dc5a6a6f2
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269048"
---
# <span data-ttu-id="5894a-103">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="5894a-103">Measure-Object</span></span>

## <span data-ttu-id="5894a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5894a-104">SYNOPSIS</span></span>
<span data-ttu-id="5894a-105">Beräknar numeriska egenskaper för objekt, samt tecken, ord och rader i sträng objekt, till exempel filer för text.</span><span class="sxs-lookup"><span data-stu-id="5894a-105">Calculates the numeric properties of objects, and the characters, words, and lines in string objects, such as files of text.</span></span>

## <span data-ttu-id="5894a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5894a-106">SYNTAX</span></span>

### <span data-ttu-id="5894a-107">GenericMeasure (standard)</span><span class="sxs-lookup"><span data-stu-id="5894a-107">GenericMeasure (Default)</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-StandardDeviation]
 [-Sum] [-AllStats] [-Average] [-Maximum] [-Minimum] [<CommonParameters>]
```

### <span data-ttu-id="5894a-108">TextMeasure</span><span class="sxs-lookup"><span data-stu-id="5894a-108">TextMeasure</span></span>

```
Measure-Object [[-Property] <PSPropertyExpression[]>] [-InputObject <PSObject>] [-Line] [-Word]
 [-Character] [-IgnoreWhiteSpace] [<CommonParameters>]
```

## <span data-ttu-id="5894a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5894a-109">DESCRIPTION</span></span>

<span data-ttu-id="5894a-110">`Measure-Object`Cmdleten beräknar egenskaps värden för vissa typer av objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-110">The `Measure-Object` cmdlet calculates the property values of certain types of object.</span></span>
<span data-ttu-id="5894a-111">`Measure-Object` utför tre typer av mätningar, beroende på parametrarna i kommandot.</span><span class="sxs-lookup"><span data-stu-id="5894a-111">`Measure-Object` performs three types of measurements, depending on the parameters in the command.</span></span>

<span data-ttu-id="5894a-112">`Measure-Object`Cmdlet: en utför beräkningar på objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="5894a-112">The `Measure-Object` cmdlet performs calculations on the property values of objects.</span></span> <span data-ttu-id="5894a-113">Du kan använda `Measure-Object` för att räkna objekt eller räkna objekt med en angiven **egenskap**.</span><span class="sxs-lookup"><span data-stu-id="5894a-113">You can use `Measure-Object` to count objects or count objects with a specified **Property**.</span></span> <span data-ttu-id="5894a-114">Du kan också använda `Measure-Object` för att beräkna **lägsta** , **högsta** , **Sum** , **StandardDeviation** och **medelvärde** för numeriska värden.</span><span class="sxs-lookup"><span data-stu-id="5894a-114">You can also use `Measure-Object` to calculate the **Minimum** , **Maximum** , **Sum** , **StandardDeviation** and **Average** of numeric values.</span></span> <span data-ttu-id="5894a-115">För **sträng** objekt kan du också använda `Measure-Object` för att räkna antalet rader, ord och tecken.</span><span class="sxs-lookup"><span data-stu-id="5894a-115">For **String** objects, you can also use `Measure-Object` to count the number of lines, words, and characters.</span></span>

## <span data-ttu-id="5894a-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5894a-116">EXAMPLES</span></span>

### <span data-ttu-id="5894a-117">Exempel 1: räkna filerna och mapparna i en katalog</span><span class="sxs-lookup"><span data-stu-id="5894a-117">Example 1: Count the files and folders in a directory</span></span>

<span data-ttu-id="5894a-118">Det här kommandot räknar filerna och mapparna i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5894a-118">This command counts the files and folders in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object
```

### <span data-ttu-id="5894a-119">Exempel 2: mäta filerna i en katalog</span><span class="sxs-lookup"><span data-stu-id="5894a-119">Example 2: Measure the files in a directory</span></span>

<span data-ttu-id="5894a-120">Det här kommandot visar det **lägsta** , **högsta** och **summan** av storlekarna för alla filer i den aktuella katalogen och den genomsnittliga storleken på en fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="5894a-120">This command displays the **Minimum** , **Maximum** , and **Sum** of the sizes of all files in the current directory, and the average size of a file in the directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property length -Minimum -Maximum -Average
```

### <span data-ttu-id="5894a-121">Exempel 3: mäta text i en textfil</span><span class="sxs-lookup"><span data-stu-id="5894a-121">Example 3: Measure text in a text file</span></span>

<span data-ttu-id="5894a-122">Det här kommandot visar antalet tecken, ord och rader i Text.txts filen.</span><span class="sxs-lookup"><span data-stu-id="5894a-122">This command displays the number of characters, words, and lines in the Text.txt file.</span></span>
<span data-ttu-id="5894a-123">Utan den **obehandlade** parametern, `Get-Content` matas filen ut som en matris med rader.</span><span class="sxs-lookup"><span data-stu-id="5894a-123">Without the **Raw** parameter, `Get-Content` outputs the file as an array of lines.</span></span>

<span data-ttu-id="5894a-124">Det första kommandot använder `Set-Content` för att lägga till viss standard text i en fil.</span><span class="sxs-lookup"><span data-stu-id="5894a-124">The first command uses `Set-Content` to add some default text to a file.</span></span>

```powershell
"One", "Two", "Three", "Four" | Set-Content -Path C:\Temp\tmp.txt
Get-Content C:\Temp\tmp.txt | Measure-Object -Character -Line -Word
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    4     4         15
```

### <span data-ttu-id="5894a-125">Exempel 4: Mät objekt som innehåller en angiven egenskap</span><span class="sxs-lookup"><span data-stu-id="5894a-125">Example 4: Measure objects containing a specified Property</span></span>

<span data-ttu-id="5894a-126">Det här exemplet räknar antalet objekt som har egenskapen **DisplayName** .</span><span class="sxs-lookup"><span data-stu-id="5894a-126">This example counts the number of objects that have a **DisplayName** property.</span></span> <span data-ttu-id="5894a-127">De två första kommandona hämtar alla tjänster och processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5894a-127">The first two commands retrieve all the services and processes on the local machine.</span></span> <span data-ttu-id="5894a-128">Det tredje kommandot räknar det sammanlagda antalet tjänster och processer.</span><span class="sxs-lookup"><span data-stu-id="5894a-128">The third command counts the combined number of services and processes.</span></span> <span data-ttu-id="5894a-129">Det sista kommandot kombinerar de två samlingarna och slår resultatet till `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="5894a-129">The last command combines the two collections and pipes the result to `Measure-Object`.</span></span>

<span data-ttu-id="5894a-130">Objektet **system. Diagnostics. process** har ingen **DisplayName** -egenskap och lämnas utanför det slutliga antalet.</span><span class="sxs-lookup"><span data-stu-id="5894a-130">The **System.Diagnostics.Process** object does not have a **DisplayName** property, and is left out of the final count.</span></span>

```powershell
$services = Get-Service
$processes = Get-Process
$services + $processes | Measure-Object
$services + $processes | Measure-Object -Property DisplayName
```

```Output
Count    : 682
Average  :
Sum      :
Maximum  :
Minimum  :
Property :

Count    : 290
Average  :
Sum      :
Maximum  :
Minimum  :
Property : DisplayName
```

### <span data-ttu-id="5894a-131">Exempel 5: mäta innehållet i en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="5894a-131">Example 5: Measure the contents of a CSV file</span></span>

<span data-ttu-id="5894a-132">Det här kommandot beräknar det genomsnittliga året för de anställda i ett företag.</span><span class="sxs-lookup"><span data-stu-id="5894a-132">This command calculates the average years of service of the employees of a company.</span></span>

<span data-ttu-id="5894a-133">`ServiceYrs.csv`Filen är en CSV-fil som innehåller anställnings numret och varje anställds års tjänst.</span><span class="sxs-lookup"><span data-stu-id="5894a-133">The `ServiceYrs.csv` file is a CSV file that contains the employee number and years of service of each employee.</span></span> <span data-ttu-id="5894a-134">Den första raden i tabellen är en rubrik rad av **EmpNo** , **år**.</span><span class="sxs-lookup"><span data-stu-id="5894a-134">The first row in the table is a header row of **EmpNo** , **Years**.</span></span>

<span data-ttu-id="5894a-135">När du använder `Import-Csv` för att importera filen är resultatet en **PSCustomObject** med antecknings egenskaper för **EmpNo** och **år**.</span><span class="sxs-lookup"><span data-stu-id="5894a-135">When you use `Import-Csv` to import the file, the result is a **PSCustomObject** with note properties of **EmpNo** and **Years**.</span></span>
<span data-ttu-id="5894a-136">Du kan använda `Measure-Object` för att beräkna värdena för dessa egenskaper, precis som andra egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-136">You can use `Measure-Object` to calculate the values of these properties, just like any other property of an object.</span></span>

```powershell
Import-Csv d:\test\serviceyrs.csv | Measure-Object -Property years -Minimum -Maximum -Average
```

### <span data-ttu-id="5894a-137">Exempel 6: Mät booleska värden</span><span class="sxs-lookup"><span data-stu-id="5894a-137">Example 6: Measure Boolean values</span></span>

<span data-ttu-id="5894a-138">Det här exemplet visar hur `Measure-Object` kan mäta booleska värden.</span><span class="sxs-lookup"><span data-stu-id="5894a-138">This example demonstrates how the `Measure-Object` can measure Boolean values.</span></span>
<span data-ttu-id="5894a-139">I det här fallet använder den **Boolean** -egenskapen **PSIsContainer** för att mäta antalet mappar (vs. files) i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5894a-139">In this case, it uses the **PSIsContainer** **Boolean** property to measure the incidence of folders (vs. files) in the current directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Property psiscontainer -Maximum -Sum -Minimum -Average
```

```Output
Count             : 126
Average           : 0.0634920634920635
Sum               : 8
Maximum           : 1
Minimum           : 0
StandardDeviation :
Property          : PSIsContainer
```

### <span data-ttu-id="5894a-140">Exempel 7: Mät strängar</span><span class="sxs-lookup"><span data-stu-id="5894a-140">Example 7: Measure strings</span></span>

<span data-ttu-id="5894a-141">I följande exempel mäter antalet rader, först en sträng och sedan över flera strängar.</span><span class="sxs-lookup"><span data-stu-id="5894a-141">The following example measures the number of lines, first a single string, then across several strings.</span></span> <span data-ttu-id="5894a-142">Tecknet för ny rad <code>\`n</code> avgränsar strängar till flera rader.</span><span class="sxs-lookup"><span data-stu-id="5894a-142">The newline character <code>\`n</code> separates strings into multiple lines.</span></span>

```powershell
# The newline character `n separates the string into separate lines, as shown in the output.
"One`nTwo`nThree"
"One`nTwo`nThree" | Measure-Object -Line
```

```Output
One
Two
Three


Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The first string counts as a single line.
# The second string is separated into two lines by the newline character.
"One", "Two`nThree" | Measure-Object -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3
```

```powershell
# The Word switch counts the number of words in each InputObject
# Each InputObject is treated as a single line.
"One, Two", "Three", "Four Five" | Measure-Object -Word -Line
```

```Output
Lines Words Characters Property
----- ----- ---------- --------
    3     5
```

### <span data-ttu-id="5894a-143">Exempel 8: mäta alla värden</span><span class="sxs-lookup"><span data-stu-id="5894a-143">Example 8: Measure all the values</span></span>

<span data-ttu-id="5894a-144">Från och med PowerShell 6 **AllStats** `Measure-Object` kan du mäta all statistik tillsammans med AllStats-parametern.</span><span class="sxs-lookup"><span data-stu-id="5894a-144">Beginning in PowerShell 6, the **AllStats** parameter of `Measure-Object` allows you to measure all the statistics together.</span></span>

```powershell
1..5 | Measure-Object -AllStats
```

```output
Count             : 5
Average           : 3
Sum               : 15
Maximum           : 5
Minimum           : 1
StandardDeviation : 1.58113883008419
Property          :
```

### <span data-ttu-id="5894a-145">Exempel 9: mått med script block-egenskaper</span><span class="sxs-lookup"><span data-stu-id="5894a-145">Example 9: Measure using scriptblock properties</span></span>

<span data-ttu-id="5894a-146">Från och med PowerShell 6 `Measure-Object` stöder **script block** -egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5894a-146">Beginning in PowerShell 6, `Measure-Object` supports **ScriptBlock** properties.</span></span> <span data-ttu-id="5894a-147">Följande exempel visar hur du använder en **script block** -egenskap för att fastställa storleken, i megabyte, för alla filer i en katalog.</span><span class="sxs-lookup"><span data-stu-id="5894a-147">The following example demonstrates how to use a **ScriptBlock** property to determine the size, in MegaBytes, of all the files in a directory.</span></span>

```powershell
Get-ChildItem | Measure-Object -Sum {$_.Length/1MB}
```

### <span data-ttu-id="5894a-148">Exempel 10: mått hash</span><span class="sxs-lookup"><span data-stu-id="5894a-148">Example 10: Measure hashtables</span></span>

<span data-ttu-id="5894a-149">Från och med PowerShell 6 `Measure-Object` stöder mätning av **datahash** -ingångar.</span><span class="sxs-lookup"><span data-stu-id="5894a-149">Beginning in PowerShell 6, `Measure-Object` supports measurement of **hashtable** input.</span></span> <span data-ttu-id="5894a-150">I följande exempel bestäms det största värdet för `num` nyckeln för 3 **hash** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-150">The following example determines the largest value for the `num` key of 3 **hashtable** objects.</span></span>

```powershell
@{num=3}, @{num=4}, @{num=5} | Measure-Object -Maximum Num
```

```output
Count             : 3
Average           :
Sum               :
Maximum           : 5
Minimum           :
StandardDeviation :
Property          : num
```

### <span data-ttu-id="5894a-151">Exempel 11: Mät standard avvikelsen</span><span class="sxs-lookup"><span data-stu-id="5894a-151">Example 11: Measure the Standard Deviation</span></span>

<span data-ttu-id="5894a-152">Från och med PowerShell 6 `Measure-Object` stöder `-StandardDeviation` parametern.</span><span class="sxs-lookup"><span data-stu-id="5894a-152">Beginning in PowerShell 6, `Measure-Object` supports the `-StandardDeviation` parameter.</span></span> <span data-ttu-id="5894a-153">I följande exempel bestäms *standard avvikelsen* för den CPU som används av alla processer.</span><span class="sxs-lookup"><span data-stu-id="5894a-153">The following example determines the *standard deviation* for the CPU used by all processes.</span></span> <span data-ttu-id="5894a-154">En stor avvikelse indikerar ett litet antal processer som förbrukar mest processor kraft.</span><span class="sxs-lookup"><span data-stu-id="5894a-154">A large deviation would indicate a small number of processes consuming the most CPU.</span></span>

```powershell
Get-Process | Measure-Object -Average -StandardDeviation CPU
```

```output
Count             : 303
Average           : 163.032384488449
Sum               :
Maximum           :
Minimum           :
StandardDeviation : 859.444048419069
Property          : CPU
```

### <span data-ttu-id="5894a-155">Exempel 12: mäta med jokertecken</span><span class="sxs-lookup"><span data-stu-id="5894a-155">Example 12: Measure using wildcards</span></span>

<span data-ttu-id="5894a-156">Från och med PowerShell 6 `Measure-Object` stöder mätning av objekt med jokertecken i egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="5894a-156">Beginning in PowerShell 6, `Measure-Object` supports measurement of objects by using wildcards in property names.</span></span> <span data-ttu-id="5894a-157">I följande exempel bestäms det högsta av alla typer av växlings Bart minne mellan en uppsättning processer.</span><span class="sxs-lookup"><span data-stu-id="5894a-157">The following example determines the maximum of any type of paged memory usage among a set of processes.</span></span>

```powershell
Get-Process | Measure-Object -Maximum *paged*memory*size
```

```output
Count             : 303
Average           :
Sum               :
Maximum           : 735784
Minimum           :
StandardDeviation :
Property          : NonpagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 352104448
Minimum           :
StandardDeviation :
Property          : PagedMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 2201968
Minimum           :
StandardDeviation :
Property          : PagedSystemMemorySize

Count             : 303
Average           :
Sum               :
Maximum           : 719032320
Minimum           :
StandardDeviation :
Property          : PeakPagedMemorySize
```

## <span data-ttu-id="5894a-158">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5894a-158">PARAMETERS</span></span>

### <span data-ttu-id="5894a-159">– Genomsnittlig</span><span class="sxs-lookup"><span data-stu-id="5894a-159">-Average</span></span>

<span data-ttu-id="5894a-160">Anger att cmdleten visar genomsnitts värdet för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-160">Indicates that the cmdlet displays the average value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-161">– Character</span><span class="sxs-lookup"><span data-stu-id="5894a-161">-Character</span></span>

<span data-ttu-id="5894a-162">Anger att cmdleten räknar antalet tecken i objekten.</span><span class="sxs-lookup"><span data-stu-id="5894a-162">Indicates that the cmdlet counts the number of characters in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5894a-163">**Ord** , **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-163">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5894a-164">Se exempel 7.</span><span class="sxs-lookup"><span data-stu-id="5894a-164">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-165">-IgnoreWhiteSpace</span><span class="sxs-lookup"><span data-stu-id="5894a-165">-IgnoreWhiteSpace</span></span>

<span data-ttu-id="5894a-166">Anger att cmdleten ignorerar blank steg i antal tecken.</span><span class="sxs-lookup"><span data-stu-id="5894a-166">Indicates that the cmdlet ignores white space in character counts.</span></span>
<span data-ttu-id="5894a-167">Som standard ignoreras inte blank steg.</span><span class="sxs-lookup"><span data-stu-id="5894a-167">By default, white space is not ignored.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-168">– InputObject</span><span class="sxs-lookup"><span data-stu-id="5894a-168">-InputObject</span></span>

<span data-ttu-id="5894a-169">Anger de objekt som ska mätas.</span><span class="sxs-lookup"><span data-stu-id="5894a-169">Specifies the objects to be measured.</span></span>
<span data-ttu-id="5894a-170">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="5894a-170">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="5894a-171">När du använder parametern **InputObject** i `Measure-Object` , i stället för Skicka kommando resultat till `Measure-Object` , behandlas **InputObject** -värdet som ett enskilt objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-171">When you use the **InputObject** parameter with `Measure-Object`, instead of piping command results to `Measure-Object`, the **InputObject** value is treated as a single object.</span></span>

<span data-ttu-id="5894a-172">Vi rekommenderar att du använder `Measure-Object` i pipelinen om du vill mäta en samling objekt baserat på om objekten har angivna värden i definierade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5894a-172">It is recommended that you use `Measure-Object` in the pipeline if you want to measure a collection of objects based on whether the objects have specific values in defined properties.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-173">-Rad</span><span class="sxs-lookup"><span data-stu-id="5894a-173">-Line</span></span>

<span data-ttu-id="5894a-174">Anger att cmdleten räknar antalet rader i objekten.</span><span class="sxs-lookup"><span data-stu-id="5894a-174">Indicates that the cmdlet counts the number of lines in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5894a-175">**Ord** , **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-175">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5894a-176">Se exempel 7.</span><span class="sxs-lookup"><span data-stu-id="5894a-176">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-177">-Maximalt</span><span class="sxs-lookup"><span data-stu-id="5894a-177">-Maximum</span></span>

<span data-ttu-id="5894a-178">Anger att cmdleten visar det maximala värdet för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-178">Indicates that the cmdlet displays the maximum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-179">-Minst</span><span class="sxs-lookup"><span data-stu-id="5894a-179">-Minimum</span></span>

<span data-ttu-id="5894a-180">Anger att cmdleten visar det minsta värdet för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-180">Indicates that the cmdlet displays the minimum value of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-181">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="5894a-181">-Property</span></span>

<span data-ttu-id="5894a-182">Anger en eller flera egenskaper som ska mätas.</span><span class="sxs-lookup"><span data-stu-id="5894a-182">Specifies one or more properties to measure.</span></span> <span data-ttu-id="5894a-183">Om du inte anger några andra mått `Measure-Object` räknar de objekt som har de egenskaper som du anger.</span><span class="sxs-lookup"><span data-stu-id="5894a-183">If you do not specify any other measures, `Measure-Object` counts the objects that have the properties you specify.</span></span>

<span data-ttu-id="5894a-184">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="5894a-184">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="5894a-185">Den beräknade egenskapen måste vara ett skript block.</span><span class="sxs-lookup"><span data-stu-id="5894a-185">The calculated property must be a script block.</span></span> <span data-ttu-id="5894a-186">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="5894a-186">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5894a-187">-StandardDeviation</span><span class="sxs-lookup"><span data-stu-id="5894a-187">-StandardDeviation</span></span>

<span data-ttu-id="5894a-188">Anger att cmdleten visar standard avvikelsen för värdena för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-188">Indicates that the cmdlet displays the standard deviation of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-189">-Sum</span><span class="sxs-lookup"><span data-stu-id="5894a-189">-Sum</span></span>

<span data-ttu-id="5894a-190">Anger att cmdleten visar summan av värdena för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-190">Indicates that the cmdlet displays the sum of the values of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-191">-AllStats</span><span class="sxs-lookup"><span data-stu-id="5894a-191">-AllStats</span></span>

<span data-ttu-id="5894a-192">Anger att cmdleten visar all statistik för de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5894a-192">Indicates that the cmdlet displays all the statistics of the specified properties.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GenericMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-193">– Ord</span><span class="sxs-lookup"><span data-stu-id="5894a-193">-Word</span></span>

<span data-ttu-id="5894a-194">Anger att cmdleten räknar antalet ord i objekten.</span><span class="sxs-lookup"><span data-stu-id="5894a-194">Indicates that the cmdlet counts the number of words in the input objects.</span></span>

> [!NOTE]
> <span data-ttu-id="5894a-195">**Ord** , **char** och **linje** växlar räknas *i* varje inobjekt, samt *över* inobjekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-195">The **Word** , **Char** and **Line** switches count *inside* each input object, as well as *across* input objects.</span></span> <span data-ttu-id="5894a-196">Se exempel 7.</span><span class="sxs-lookup"><span data-stu-id="5894a-196">See Example 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TextMeasure
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5894a-197">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5894a-197">CommonParameters</span></span>

<span data-ttu-id="5894a-198">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5894a-198">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5894a-199">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5894a-199">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5894a-200">INDATA</span><span class="sxs-lookup"><span data-stu-id="5894a-200">INPUTS</span></span>

### <span data-ttu-id="5894a-201">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="5894a-201">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5894a-202">Du kan skicka pipe-objekt till `Measure-Object` .</span><span class="sxs-lookup"><span data-stu-id="5894a-202">You can pipe objects to `Measure-Object`.</span></span>

## <span data-ttu-id="5894a-203">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5894a-203">OUTPUTS</span></span>

### <span data-ttu-id="5894a-204">Microsoft. PowerShell. commands. GenericMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="5894a-204">Microsoft.PowerShell.Commands.GenericMeasureInfo</span></span>

### <span data-ttu-id="5894a-205">Microsoft. PowerShell. commands. TextMeasureInfo</span><span class="sxs-lookup"><span data-stu-id="5894a-205">Microsoft.PowerShell.Commands.TextMeasureInfo</span></span>

<span data-ttu-id="5894a-206">Om du använder parametern **Word** `Measure-Object` returnerar ett **TextMeasureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-206">If you use the **Word** parameter, `Measure-Object` returns a **TextMeasureInfo** object.</span></span>
<span data-ttu-id="5894a-207">Annars returnerar den ett **GenericMeasureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5894a-207">Otherwise, it returns a **GenericMeasureInfo** object.</span></span>

## <span data-ttu-id="5894a-208">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5894a-208">NOTES</span></span>

## <span data-ttu-id="5894a-209">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5894a-209">RELATED LINKS</span></span>

[<span data-ttu-id="5894a-210">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="5894a-210">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="5894a-211">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-211">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="5894a-212">-Objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-212">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="5894a-213">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-213">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="5894a-214">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-214">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="5894a-215">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5894a-215">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="5894a-216">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-216">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="5894a-217">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-217">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="5894a-218">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="5894a-218">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
