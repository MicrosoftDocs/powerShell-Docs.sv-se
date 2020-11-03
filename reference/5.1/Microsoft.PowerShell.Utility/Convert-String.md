---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convert-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Convert-String
ms.openlocfilehash: 29ec9e21277bae02ab94ce5e862787c86a87b439
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265178"
---
# <span data-ttu-id="51523-103">Convert-String</span><span class="sxs-lookup"><span data-stu-id="51523-103">Convert-String</span></span>

## <span data-ttu-id="51523-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="51523-104">SYNOPSIS</span></span>
<span data-ttu-id="51523-105">Formaterar en sträng för att matcha exempel.</span><span class="sxs-lookup"><span data-stu-id="51523-105">Formats a string to match examples.</span></span>

## <span data-ttu-id="51523-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="51523-106">SYNTAX</span></span>

```
Convert-String [-Example <System.Collections.Generic.List`1[System.Management.Automation.PSObject]>]
 -InputObject <String> [<CommonParameters>]
```

## <span data-ttu-id="51523-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="51523-107">DESCRIPTION</span></span>

<span data-ttu-id="51523-108">Cmdleten **Convert-String** formaterar en sträng för att matcha formatet på exempel.</span><span class="sxs-lookup"><span data-stu-id="51523-108">The **Convert-String** cmdlet formats a string to match the format of examples.</span></span>

## <span data-ttu-id="51523-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="51523-109">EXAMPLES</span></span>

### <span data-ttu-id="51523-110">Exempel 1: konvertera format för en sträng</span><span class="sxs-lookup"><span data-stu-id="51523-110">Example 1: Convert format of a string</span></span>

```powershell
"Mu Han", "Jim Hance", "David Ahs", "Kim Akers" | Convert-String -Example "Ed Wilson=Wilson, E."
```

```output
Han, M.
Hance, J.
Ahs, D.
Akers, K.
```

<span data-ttu-id="51523-111">Det första kommandot skapar en matris som innehåller för-och efter namn.</span><span class="sxs-lookup"><span data-stu-id="51523-111">The first command creates an array that contains first and last names.</span></span>

<span data-ttu-id="51523-112">Det andra kommandot formaterar namnen enligt exemplet.</span><span class="sxs-lookup"><span data-stu-id="51523-112">The second command formats the names according to the example.</span></span>
<span data-ttu-id="51523-113">Förnamnet placeras först i utdata, följt av en initial.</span><span class="sxs-lookup"><span data-stu-id="51523-113">It puts the surname first in the output, followed by an initial.</span></span>

### <span data-ttu-id="51523-114">Exempel 2: förenkla format för en sträng</span><span class="sxs-lookup"><span data-stu-id="51523-114">Example 2: Simplify format of a string</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=last, first"
```

```output
Bach, Johann
Mozart, Wolfgang
Chopin, Frederic
Brahms, Johannes
```

<span data-ttu-id="51523-115">Det första kommandot skapar en matris som innehåller First-, mitten-och efter namn.</span><span class="sxs-lookup"><span data-stu-id="51523-115">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="51523-116">Observera att den sista posten inte har något mellan namn.</span><span class="sxs-lookup"><span data-stu-id="51523-116">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="51523-117">Det andra kommandot formaterar namnen enligt exemplet.</span><span class="sxs-lookup"><span data-stu-id="51523-117">The second command formats the names according to the example.</span></span>
<span data-ttu-id="51523-118">Det placerar efter namnet först i utdata, följt av det första namnet.</span><span class="sxs-lookup"><span data-stu-id="51523-118">It puts the last name first in the output, followed by the first name.</span></span>
<span data-ttu-id="51523-119">Alla mellan namn har tagits bort. posten utan mellan namn hanteras korrekt.</span><span class="sxs-lookup"><span data-stu-id="51523-119">All middle names removed; entry without middle name is handled correctly.</span></span>

### <span data-ttu-id="51523-120">Exempel 3: hantering av utdata när strängar inte matchar exemplet</span><span class="sxs-lookup"><span data-stu-id="51523-120">Example 3: Output management when strings don't match example</span></span>

```powershell
$composers = @("Johann Sebastian Bach", "Wolfgang Amadeus Mozart", "Frederic Francois Chopin", "Johannes Brahms")
$composers | Convert-String -Example "first middle last=middle, first"
```

```output
Sebastian, Johann
Amadeus, Wolfgang
Francois, Frederic
```

<span data-ttu-id="51523-121">Det första kommandot skapar en matris som innehåller First-, mitten-och efter namn.</span><span class="sxs-lookup"><span data-stu-id="51523-121">The first command creates an array that contains first, middle and last names.</span></span>
<span data-ttu-id="51523-122">Observera att den sista posten inte har något mellan namn.</span><span class="sxs-lookup"><span data-stu-id="51523-122">Note that the last entry has no middle name.</span></span>

<span data-ttu-id="51523-123">Det andra kommandot formaterar namnen enligt exemplet.</span><span class="sxs-lookup"><span data-stu-id="51523-123">The second command formats the names according to the example.</span></span>
<span data-ttu-id="51523-124">Det placerar det **mittersta namnet** först i utdata, följt av det första namnet.</span><span class="sxs-lookup"><span data-stu-id="51523-124">It puts the **middle name** first in the output, followed by the first name.</span></span>
<span data-ttu-id="51523-125">Den sista posten i **$Composers** hoppas över eftersom den inte matchar exempel mönstret: det saknar mellan namn.</span><span class="sxs-lookup"><span data-stu-id="51523-125">The last entry in **$Composers** is skipped, because it doesn't match the sample pattern: it has no middle name.</span></span>

### <span data-ttu-id="51523-126">Exempel 4: försiktighet med skönhets utrymmen</span><span class="sxs-lookup"><span data-stu-id="51523-126">Example 4: Caution with beauty spaces</span></span>

```powershell
$composers = @("Antonio Vivaldi", "Richard Wagner ", "Franz Schubert", "Johannes Brahms ")
$composers | Convert-String -Example "Patti Fuller = Fuller, P."
```

```output
 Wagner, R.
 Brahms, J.
```

<span data-ttu-id="51523-127">Det första kommandot skapar en matris med för-och efter namn.</span><span class="sxs-lookup"><span data-stu-id="51523-127">The first command creates an array of first and last names.</span></span>
<span data-ttu-id="51523-128">Observera att andra och fjärde objekt har ett extra avslutande blank steg efter efter namn.</span><span class="sxs-lookup"><span data-stu-id="51523-128">Note that second and fourth items have an extra trailing space, after the last name.</span></span>

<span data-ttu-id="51523-129">Det andra kommandot konverterar alla strängar som matchar exempel mönstret: _ord, blank steg, ord och avslutande avslutande blank steg_ , allt detta före likhets tecknet.</span><span class="sxs-lookup"><span data-stu-id="51523-129">The second command converts all strings that match the sample pattern: _word, space, word, and final trailing space_ , all of this before the equal sign.</span></span>
<span data-ttu-id="51523-130">Observera också det inledande utrymmet i utdata.</span><span class="sxs-lookup"><span data-stu-id="51523-130">Also, note the leading space in the output.</span></span>

### <span data-ttu-id="51523-131">Exempel 5: formatera process information med flera mönster</span><span class="sxs-lookup"><span data-stu-id="51523-131">Example 5: Format process information with multiple patterns</span></span>

```powershell
$ExamplePatterns = @(
    @{before='"Hello","World"'; after='World: Hello'},
    @{before='"Hello","1"'; after='1: Hello'},
    @{before='"Hello-World","22"'; after='22: Hello-World'},
    @{before='"hello world","333"'; after='333: hello world'}
)
$Processes = Get-Process   | Select-Object -Property ProcessName, Id | ConvertTo-Csv -NoTypeInformation
$Processes | Convert-String -Example $ExamplePatterns
```

```output
Id: ProcessName
4368: AGSService
8896: Amazon Music Helper
4420: AppleMobileDeviceService
...
11140: git-bash
0: Idle
...
56: Secure System
...
13028: WmiPrvSE
2724: WUDFHost
2980: WUDFHost
3348: WUDFHost
```

<span data-ttu-id="51523-132">**$ExamplePatterns** definierar olika förväntade mönster i data med hjälp av exempel.</span><span class="sxs-lookup"><span data-stu-id="51523-132">**$ExamplePatterns** defines different expected patterns in the data, through examples.</span></span>

<span data-ttu-id="51523-133">Det första mönstret, `@{before='"Hello","World"'; after='World: Hello'}` , läst på följande sätt: _förväntar sig att strängar där ett ord omges av dubbla citat tecken, ett kommatecken_ 
 _och sedan det andra och sista ordet inom citat tecken._ 
 _utan blank steg i strängen. På utdata: Placera andra ordet först,_ 
 _utan citat tecken, ett enda blank steg och sedan det första ordet, utan citat tecken._</span><span class="sxs-lookup"><span data-stu-id="51523-133">The first pattern, `@{before='"Hello","World"'; after='World: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then the second, and last, word enclosed in quotes;_
_with no spaces in the string. On the output: place second word first,_
_without quotes, then a single space, and then the first word, without quotes._</span></span>

<span data-ttu-id="51523-134">Det andra mönstret, `@{before='"Hello","1"'; after='1: Hello'}` , läses på följande sätt: _förväntar sig strängar där ett ord omges av dubbla citat tecken, ett kommatecken_ 
 _och sedan ett tal inom citat tecken._ 
 _utan blank steg i strängen. På utdata: placera talet först,_ 
 _utan citat tecken, ett enda blank steg och sedan ordet utan citat tecken._</span><span class="sxs-lookup"><span data-stu-id="51523-134">The second pattern, `@{before='"Hello","1"'; after='1: Hello'}`, reads as follows: _expect strings where a word comes enclosed in double quotes, then a comma,_
_and then a number enclosed in quotes;_
_with no spaces in the string. On the output: place the number first,_
_without quotes, then a single space, and then the word, without quotes._</span></span>

<span data-ttu-id="51523-135">Det tredje mönstret, `@{before='"Hello-World","22"'; after='22: Hello-World'}` , läser följande: _förväntar sig strängar där två ord med ett bindestreck mellan omges av_ 
 _dubbla citat tecken, ett kommatecken och sedan ett tal inom citat tecken._ 
 _utan blank steg mellan kommatecken och det tredje dubbla citat tecknet._ 
 _På utdata: placera talet först, utan citat tecken, sedan ett enda blank steg,_ 
 _och sedan avstavade ord, utan citat tecken._</span><span class="sxs-lookup"><span data-stu-id="51523-135">The third pattern, `@{before='"Hello-World","22"'; after='22: Hello-World'}`, reads as follows: _expect strings where two words with a hyphen in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the hyphenated words, without quotes._</span></span>

<span data-ttu-id="51523-136">Det fjärde och slutgiltiga mönstret, läser följande `@{before='"hello world","333"'; after='333: hello world'}` : _förväntar sig att strängar där två ord med ett blank steg omges av_ 
 _dubbla citat tecken, ett kommatecken och sedan ett tal inom citat tecken._ 
 _utan blank steg mellan kommatecken och det tredje dubbla citat tecknet._ 
 _På utdata: placera talet först, utan citat tecken, sedan ett enda blank steg,_ 
 _och sedan orden med blank steg mellan, utan citat tecken._</span><span class="sxs-lookup"><span data-stu-id="51523-136">The fourth, and final, pattern, `@{before='"hello world","333"'; after='333: hello world'}`, reads as follows: _expect strings where two words with a space in between come enclosed in_
_double quotes, then a comma, and then a number enclosed in quotes;_
_with no spaces between the comma and the third double quote._
_On the output: place the number first, without quotes, then a single space,_
_and then the words with the space in between, without quotes._</span></span>

<span data-ttu-id="51523-137">Det första kommandot hämtar alla processer med hjälp av Get-Process-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="51523-137">The first command gets all processes by using the Get-Process cmdlet.</span></span>
<span data-ttu-id="51523-138">Kommandot skickar dem till Select-Object-cmdlet, som väljer processens namn och process-ID.</span><span class="sxs-lookup"><span data-stu-id="51523-138">The command passes them to the Select-Object cmdlet, which selects the process name and process ID.</span></span> <span data-ttu-id="51523-139">I slutet av pipelinen konverterar kommandot utdata till kommaavgränsade värden, utan typ information med hjälp av ConvertTo-Csv cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51523-139">At the end of the pipeline, the command converts the output to comma separated values, without type information, by using the ConvertTo-Csv cmdlet.</span></span>
<span data-ttu-id="51523-140">Kommandot lagrar resultaten i variabeln **$Processes** .</span><span class="sxs-lookup"><span data-stu-id="51523-140">The command stores the results in the **$Processes** variable.</span></span>
<span data-ttu-id="51523-141">**$Processes** innehåller nu process namn och PID.</span><span class="sxs-lookup"><span data-stu-id="51523-141">**$Processes** now contains process names and PID.</span></span>

<span data-ttu-id="51523-142">Det andra kommandot anger en exempel variabel som ändrar ordningen på inobjekten.</span><span class="sxs-lookup"><span data-stu-id="51523-142">The second command specifies an example variable that changes the order of the input items.</span></span>
<span data-ttu-id="51523-143">Kommandot behandlar varje sträng i **$Processes**.</span><span class="sxs-lookup"><span data-stu-id="51523-143">The command coverts each string in **$Processes**.</span></span>

><span data-ttu-id="51523-144">**Obs!** Det fjärde mönstret säger implicit att två eller flera ord avgränsade med blank steg matchas.</span><span class="sxs-lookup"><span data-stu-id="51523-144">**Note** The fourth pattern implicitly says that two or more words separated by spaces are matched.</span></span>
>
><span data-ttu-id="51523-145">Utan det fjärde mönstret matchas bara det första ordet i strängen som omges av dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="51523-145">Without the fourth pattern, only the first word of the string enclosed in double quotes is matched.</span></span>

## <span data-ttu-id="51523-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="51523-146">PARAMETERS</span></span>

### <span data-ttu-id="51523-147">– Exempel</span><span class="sxs-lookup"><span data-stu-id="51523-147">-Example</span></span>

<span data-ttu-id="51523-148">Anger en lista med exempel på mål formatet.</span><span class="sxs-lookup"><span data-stu-id="51523-148">Specifies a list of examples of the target format.</span></span>
<span data-ttu-id="51523-149">Ange par avgränsade med likhets tecknet (=) med käll mönstret till vänster och mål mönstret till höger, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="51523-149">Specify pairs separated by the equal (=) sign, with the source pattern on the left and the target pattern on the right, as in the following examples:</span></span>

* `-Example "Hello World=World, Hello"`
* `-Example "Hello World=World: Hello",'"Hello","1"=1: Hello'`

><span data-ttu-id="51523-150">**Obs!** I det andra exemplet används en lista över mönster</span><span class="sxs-lookup"><span data-stu-id="51523-150">**Note** The second example uses a list of patterns</span></span>

<span data-ttu-id="51523-151">Alternativt kan du ange en lista över hash-tabeller som innehåller **före** och **efter** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="51523-151">Alternatively, specify a list of hash tables that contain **Before** and **After** properties.</span></span>

* `-Example @{before='"Hello","World"'; after='World: Hello'}, @{before='"Hello","1"'; after='1: Hello'}`

><span data-ttu-id="51523-152">**Varning** Undvik att använda blank steg runt likhets tecknet eftersom de behandlas som en del av mönstret.</span><span class="sxs-lookup"><span data-stu-id="51523-152">**Caution** Avoid using spaces around the equal sign, as they are treated as part of the pattern.</span></span>

```yaml
Type: System.Collections.Generic.List`1[System.Management.Automation.PSObject]
Parameter Sets: (All)
Aliases: E

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="51523-153">– InputObject</span><span class="sxs-lookup"><span data-stu-id="51523-153">-InputObject</span></span>

<span data-ttu-id="51523-154">Anger en sträng som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="51523-154">Specifies a string to format.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="51523-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="51523-155">CommonParameters</span></span>

<span data-ttu-id="51523-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="51523-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="51523-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="51523-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="51523-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="51523-158">INPUTS</span></span>

### <span data-ttu-id="51523-159">Sträng</span><span class="sxs-lookup"><span data-stu-id="51523-159">String</span></span>

<span data-ttu-id="51523-160">Du kan skicka vidare strängar till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51523-160">You can pipe strings to this cmdlet.</span></span>

## <span data-ttu-id="51523-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="51523-161">OUTPUTS</span></span>

### <span data-ttu-id="51523-162">Sträng</span><span class="sxs-lookup"><span data-stu-id="51523-162">String</span></span>

<span data-ttu-id="51523-163">Den här cmdleten returnerar en sträng.</span><span class="sxs-lookup"><span data-stu-id="51523-163">This cmdlet returns a string.</span></span>

## <span data-ttu-id="51523-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="51523-164">NOTES</span></span>

## <span data-ttu-id="51523-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="51523-165">RELATED LINKS</span></span>

[<span data-ttu-id="51523-166">ConvertFrom-sträng</span><span class="sxs-lookup"><span data-stu-id="51523-166">ConvertFrom-String</span></span>](ConvertFrom-String.md)

[<span data-ttu-id="51523-167">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="51523-167">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="51523-168">Hämta process</span><span class="sxs-lookup"><span data-stu-id="51523-168">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="51523-169">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="51523-169">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="51523-170">Select-Object</span><span class="sxs-lookup"><span data-stu-id="51523-170">Select-Object</span></span>](Select-Object.md)
