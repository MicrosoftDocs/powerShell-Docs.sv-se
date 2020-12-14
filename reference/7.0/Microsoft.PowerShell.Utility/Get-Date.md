---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 4ae3734d0ce41ef2faa7bcf3e07f136b9e9916a2
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514967"
---
# <span data-ttu-id="8fb5d-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="8fb5d-103">Get-Date</span></span>

## <span data-ttu-id="8fb5d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8fb5d-104">SYNOPSIS</span></span>
<span data-ttu-id="8fb5d-105">Hämtar aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-105">Gets the current date and time.</span></span>

## <span data-ttu-id="8fb5d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8fb5d-106">SYNTAX</span></span>

### <span data-ttu-id="8fb5d-107">NET (standard)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-107">net (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [<CommonParameters>]
```

### <span data-ttu-id="8fb5d-108">UFormat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-108">UFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-UFormat <String>] [<CommonParameters>]
```

## <span data-ttu-id="8fb5d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8fb5d-109">DESCRIPTION</span></span>

<span data-ttu-id="8fb5d-110">`Get-Date`Cmdleten hämtar ett **datetime** -objekt som representerar det aktuella datumet eller ett datum som du anger.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-110">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="8fb5d-111">`Get-Date` kan formatera datum och tid i flera .NET-och UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-111">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="8fb5d-112">Du kan använda `Get-Date` för att generera en datum-eller tids tecken sträng och sedan skicka strängen till andra cmdletar eller program.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-112">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="8fb5d-113">`Get-Date` använder datorns kultur inställningar för att avgöra hur utdata formateras.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-113">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="8fb5d-114">Använd om du vill visa datorns inställningar `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-114">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="8fb5d-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8fb5d-115">EXAMPLES</span></span>

### <span data-ttu-id="8fb5d-116">Exempel 1: Hämta aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="8fb5d-116">Example 1: Get the current date and time</span></span>

<span data-ttu-id="8fb5d-117">I det här exemplet `Get-Date` visas aktuellt system datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-117">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="8fb5d-118">Utdata är i formatet för långt datum och långt klock slag.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-118">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="8fb5d-119">Exempel 2: Hämta element i aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="8fb5d-119">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="8fb5d-120">Det här exemplet visar hur du kan använda `Get-Date` för att hämta antingen datum-eller tids element.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-120">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="8fb5d-121">Parametern använder argumenten **date**, **Time** eller **datetime**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-121">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="8fb5d-122">`Get-Date` använder parametern **DisplayHint** med **datum** argumentet för att bara hämta datumet.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-122">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="8fb5d-123">Exempel 3: Hämta datum och tid med en .NET-format specifikation</span><span class="sxs-lookup"><span data-stu-id="8fb5d-123">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="8fb5d-124">I det här exemplet används en .NET-format specifikation för att anpassa utdatatypens format.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-124">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="8fb5d-125">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-125">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="8fb5d-126">`Get-Date` använder **format** parametern för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-126">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="8fb5d-127">De .NET-format specificerare som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8fb5d-127">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="8fb5d-128">Specificerare</span><span class="sxs-lookup"><span data-stu-id="8fb5d-128">Specifier</span></span> | <span data-ttu-id="8fb5d-129">Definition</span><span class="sxs-lookup"><span data-stu-id="8fb5d-129">Definition</span></span> |
| --- | --- |
| `dddd` | <span data-ttu-id="8fb5d-130">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="8fb5d-130">Day of the week - full name</span></span> |
| `MM` | <span data-ttu-id="8fb5d-131">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="8fb5d-131">Month number</span></span> |
| `dd` | <span data-ttu-id="8fb5d-132">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="8fb5d-132">Day of the month - 2 digits</span></span> |
| `yyyy` | <span data-ttu-id="8fb5d-133">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="8fb5d-133">Year in 4-digit format</span></span> |
| `HH:mm` | <span data-ttu-id="8fb5d-134">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="8fb5d-134">Time in 24-hour format -no seconds</span></span> |
| `K` | <span data-ttu-id="8fb5d-135">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-135">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="8fb5d-136">Mer information om .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-136">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="8fb5d-137">Exempel 4: Hämta datum och tid med en UFormat-specificerare</span><span class="sxs-lookup"><span data-stu-id="8fb5d-137">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="8fb5d-138">I det här exemplet används flera **UFormat** format-specificerare för att anpassa utdatatypen.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-138">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="8fb5d-139">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-139">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="8fb5d-140">`Get-Date` använder parametern **UFormat** för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-140">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="8fb5d-141">Det **UFormat** format som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="8fb5d-141">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="8fb5d-142">Specificerare</span><span class="sxs-lookup"><span data-stu-id="8fb5d-142">Specifier</span></span> | <span data-ttu-id="8fb5d-143">Definition</span><span class="sxs-lookup"><span data-stu-id="8fb5d-143">Definition</span></span> |
| --- | --- |
| `%A` | <span data-ttu-id="8fb5d-144">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="8fb5d-144">Day of the week - full name</span></span> |
| `%m` | <span data-ttu-id="8fb5d-145">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="8fb5d-145">Month number</span></span> |
| `%d` | <span data-ttu-id="8fb5d-146">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="8fb5d-146">Day of the month - 2 digits</span></span> |
| `%Y` | <span data-ttu-id="8fb5d-147">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="8fb5d-147">Year in 4-digit format</span></span> |
| `%R` | <span data-ttu-id="8fb5d-148">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="8fb5d-148">Time in 24-hour format -no seconds</span></span> |
| `%Z` | <span data-ttu-id="8fb5d-149">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-149">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="8fb5d-150">En lista över giltiga **UFormat** format-specificerare finns i avsnittet [Obs](#notes) !</span><span class="sxs-lookup"><span data-stu-id="8fb5d-150">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="8fb5d-151">Exempel 5: Hämta datumets dag på året</span><span class="sxs-lookup"><span data-stu-id="8fb5d-151">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="8fb5d-152">I det här exemplet används en egenskap för att hämta årets numeriska dag.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-152">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="8fb5d-153">Den gregorianska kalendern har 365 dagar, med undantag för skottår som har 366 dagar.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-153">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="8fb5d-154">Till exempel 31 december 2020 är dag 366.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-154">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="8fb5d-155">`Get-Date` använder tre parametrar för att ange datum: **år**, **månad** och **dag**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-155">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="8fb5d-156">Kommandot omges av parenteser så att resultatet utvärderas av egenskapen **DayofYear** .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-156">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="8fb5d-157">Exempel 6: kontrol lera om ett datum har justerats för sommar tid</span><span class="sxs-lookup"><span data-stu-id="8fb5d-157">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="8fb5d-158">I det här exemplet används en boolesk metod för att kontrol lera om ett datum justeras efter sommar tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-158">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="8fb5d-159">En variabel, `$DST` lagrar resultatet av `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-159">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="8fb5d-160">`$DST` använder metoden **IsDaylightSavingTime** för att testa om datumet justeras för sommar tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-160">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="8fb5d-161">Exempel 7: konvertera aktuell tid till UTC-tid</span><span class="sxs-lookup"><span data-stu-id="8fb5d-161">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="8fb5d-162">I det här exemplet konverteras den aktuella tiden till UTC-tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-162">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="8fb5d-163">UTC-förskjutningen för systemets nationella inställningar används för att konvertera tiden.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-163">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="8fb5d-164">I en tabell i avsnittet [anteckningar](#notes) visas giltiga **UFormat** format-specifikationer.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-164">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="8fb5d-165">`Get-Date` använder parametern **UFormat** med format specificerare för att visa aktuellt system datum och tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-165">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="8fb5d-166">Format specifikationen **% Z** representerar UTC-förskjutningen **-07**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-166">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="8fb5d-167">`$Time`Variabeln lagrar systemets aktuella datum och tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-167">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="8fb5d-168">`$Time` använder metoden **ToUniversalTime ()** för att konvertera tiden baserat på datorns UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-168">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="8fb5d-169">Exempel 8: skapa en tidsstämpel</span><span class="sxs-lookup"><span data-stu-id="8fb5d-169">Example 8: Create a timestamp</span></span>

<span data-ttu-id="8fb5d-170">I det här exemplet skapar en format specificerare ett **String** -objekt för tidsstämpel för ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-170">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="8fb5d-171">Tidsstämpeln innehåller datum, tid och UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-171">The timestamp includes the date, time, and UTC offset.</span></span>

```powershell
$timestamp = Get-Date -Format o | ForEach-Object { $_ -replace ":", "." }
New-Item -Path C:\Test\$timestamp -Type Directory
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         6/27/2019    07:59                2019-06-27T07.59.24.4603750-07.00
```

<span data-ttu-id="8fb5d-172">`$timestamp`Variabeln lagrar resultatet av ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-172">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="8fb5d-173">`Get-Date` använder **format** parametern med format specifikationen för gemener `o` för att skapa ett **String** -objekt med tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-173">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="8fb5d-174">Objektet skickas ned pipelinen till `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-174">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="8fb5d-175">En **script block** innehåller `$_` variabeln som representerar det aktuella pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-175">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="8fb5d-176">Tids stämplings strängen avgränsas med kolon som ersätts med punkter.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-176">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="8fb5d-177">`New-Item` använder parametern **Path** för att ange platsen för en ny katalog.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-177">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="8fb5d-178">Sökvägen innehåller `$timestamp` variabeln som katalog namn.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-178">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="8fb5d-179">Parametern **Type** anger att en katalog har skapats.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-179">The **Type** parameter specifies that a directory is created.</span></span>

## <span data-ttu-id="8fb5d-180">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8fb5d-180">PARAMETERS</span></span>

### <span data-ttu-id="8fb5d-181">-Datum</span><span class="sxs-lookup"><span data-stu-id="8fb5d-181">-Date</span></span>

<span data-ttu-id="8fb5d-182">Anger ett datum och en tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-182">Specifies a date and time.</span></span> <span data-ttu-id="8fb5d-183">Tiden är valfri och om det inte anges returneras 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-183">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="8fb5d-184">Ange datum och tid i ett format som är standard för system språket.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-184">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="8fb5d-185">Till exempel på engelska (USA):</span><span class="sxs-lookup"><span data-stu-id="8fb5d-185">For example, in US English:</span></span>

<span data-ttu-id="8fb5d-186">`Get-Date -Date "6/25/2019 12:30:22"` Returnerar tisdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="8fb5d-186">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8fb5d-187">– Dag</span><span class="sxs-lookup"><span data-stu-id="8fb5d-187">-Day</span></span>

<span data-ttu-id="8fb5d-188">Anger den dag i månaden som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-188">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="8fb5d-189">Ange ett värde från 1 till 31.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-189">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="8fb5d-190">Om det angivna värdet är större än antalet dagar i månaden lägger PowerShell till antalet dagar i månaden.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-190">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="8fb5d-191">Visar till exempel `Get-Date -Month 2 -Day 31` **3 mars**, inte **31 februari**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-191">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="8fb5d-192">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="8fb5d-192">-DisplayHint</span></span>

<span data-ttu-id="8fb5d-193">Anger vilka element i datum och tid som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-193">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="8fb5d-194">De godkända värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="8fb5d-194">The accepted values are as follows:</span></span>

- <span data-ttu-id="8fb5d-195">**Datum**: visar endast datumet</span><span class="sxs-lookup"><span data-stu-id="8fb5d-195">**Date**: displays only the date</span></span>
- <span data-ttu-id="8fb5d-196">**Tid**: visar endast tiden</span><span class="sxs-lookup"><span data-stu-id="8fb5d-196">**Time**: displays only the time</span></span>
- <span data-ttu-id="8fb5d-197">**Datetime**: visar datum och tid</span><span class="sxs-lookup"><span data-stu-id="8fb5d-197">**DateTime**: displays the date and time</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fb5d-198">– Format</span><span class="sxs-lookup"><span data-stu-id="8fb5d-198">-Format</span></span>

<span data-ttu-id="8fb5d-199">Visar datum och tid i det Microsoft .NET Framework-format som anges av format specifikationen.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-199">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="8fb5d-200">**Format** parametern matar ut ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-200">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="8fb5d-201">En lista över tillgängliga .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-201">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="8fb5d-202">När **format** parametern används `Get-Date` får endast **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-202">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="8fb5d-203">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-203">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="8fb5d-204">Från och med PowerShell 5,0 kan du använda följande ytterligare format som värden för parametern **format** .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-204">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="8fb5d-205">**Filedate**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-205">**FileDate**.</span></span> <span data-ttu-id="8fb5d-206">En fil eller Sök vägs vänlig representation av aktuellt datum i lokal tid.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-206">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="8fb5d-207">Formatet är `yyyyMMdd` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad och en dag med två siffror).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-207">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="8fb5d-208">Exempel:</span><span class="sxs-lookup"><span data-stu-id="8fb5d-208">For example:</span></span>
  20190627.

- <span data-ttu-id="8fb5d-209">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-209">**FileDateUniversal**.</span></span> <span data-ttu-id="8fb5d-210">En fil eller Sök vägs vänlig representation av aktuellt datum i Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-210">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="8fb5d-211">Formatet är `yyyyMMddZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, en dag med en bokstav `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-211">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="8fb5d-212">Till exempel: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-212">For example: 20190627Z.</span></span>

- <span data-ttu-id="8fb5d-213">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-213">**FileDateTime**.</span></span> <span data-ttu-id="8fb5d-214">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-214">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="8fb5d-215">Formatet är `yyyyMMddTHHmmssffff` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund och 4-siffriga millisekunder).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-215">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="8fb5d-216">Till exempel: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-216">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="8fb5d-217">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-217">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="8fb5d-218">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i Universal Time (UTC) i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-218">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="8fb5d-219">Formatet är `yyyyMMddTHHmmssffffZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund, 4-siffriga millisekunder och bokstaven `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-219">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="8fb5d-220">Till exempel: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-220">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: net
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fb5d-221">– Timme</span><span class="sxs-lookup"><span data-stu-id="8fb5d-221">-Hour</span></span>

<span data-ttu-id="8fb5d-222">Anger den timme som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-222">Specifies the hour that is displayed.</span></span> <span data-ttu-id="8fb5d-223">Ange ett värde mellan 0 och 23.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-223">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="8fb5d-224">– Millisekunde</span><span class="sxs-lookup"><span data-stu-id="8fb5d-224">-Millisecond</span></span>

<span data-ttu-id="8fb5d-225">Anger millisekunderna i datumet.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-225">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="8fb5d-226">Ange ett värde mellan 0 och 999.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-226">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="8fb5d-227">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8fb5d-228">-Minut</span><span class="sxs-lookup"><span data-stu-id="8fb5d-228">-Minute</span></span>

<span data-ttu-id="8fb5d-229">Anger minuten som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-229">Specifies the minute that is displayed.</span></span> <span data-ttu-id="8fb5d-230">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-230">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="8fb5d-231">– Månad</span><span class="sxs-lookup"><span data-stu-id="8fb5d-231">-Month</span></span>

<span data-ttu-id="8fb5d-232">Anger den månad som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-232">Specifies the month that is displayed.</span></span> <span data-ttu-id="8fb5d-233">Ange ett värde mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-233">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="8fb5d-234">– Sekund</span><span class="sxs-lookup"><span data-stu-id="8fb5d-234">-Second</span></span>

<span data-ttu-id="8fb5d-235">Anger det andra som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-235">Specifies the second that is displayed.</span></span> <span data-ttu-id="8fb5d-236">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-236">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="8fb5d-237">-UFormat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-237">-UFormat</span></span>

<span data-ttu-id="8fb5d-238">Visar datum och tid i UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-238">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="8fb5d-239">**UFormat** -parametern matar ut ett String-objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-239">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="8fb5d-240">**UFormat** -specificerarna föregås av ett procent tecken ( `%` ), till exempel, `%m` , `%d` och `%Y` .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-240">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="8fb5d-241">Avsnittet [anteckningar](#notes) innehåller en tabell med giltiga **UFormat-specificerare**.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-241">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="8fb5d-242">När parametern **UFormat** används `Get-Date` får bara **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-242">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="8fb5d-243">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-243">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: UFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fb5d-244">-År</span><span class="sxs-lookup"><span data-stu-id="8fb5d-244">-Year</span></span>

<span data-ttu-id="8fb5d-245">Anger året som visas.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-245">Specifies the year that is displayed.</span></span> <span data-ttu-id="8fb5d-246">Ange ett värde mellan 1 och 9999.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-246">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="8fb5d-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8fb5d-247">CommonParameters</span></span>

<span data-ttu-id="8fb5d-248">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8fb5d-249">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8fb5d-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8fb5d-250">INDATA</span><span class="sxs-lookup"><span data-stu-id="8fb5d-250">INPUTS</span></span>

### <span data-ttu-id="8fb5d-251">Pipeline-inmatade</span><span class="sxs-lookup"><span data-stu-id="8fb5d-251">Pipeline input</span></span>

<span data-ttu-id="8fb5d-252">`Get-Date` accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-252">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="8fb5d-253">Ett exempel är `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-253">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="8fb5d-254">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8fb5d-254">OUTPUTS</span></span>

### <span data-ttu-id="8fb5d-255">System. DateTime eller system. String</span><span class="sxs-lookup"><span data-stu-id="8fb5d-255">System.DateTime or System.String</span></span>

<span data-ttu-id="8fb5d-256">`Get-Date` Returnerar ett **datetime** -objekt utom när **format** -och **UFormat** -parametrarna används.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-256">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="8fb5d-257">**Format** -eller **UFormat** -parametrarna returnerar **sträng** objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-257">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="8fb5d-258">När ett **datetime** -objekt skickas ned pipelinen till en-cmdlet, till exempel `Add-Content` som förväntar sig sträng Indatatyp, konverterar PowerShell objektet till ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-258">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="8fb5d-259">Metoden `(Get-Date).ToString()` konverterar ett **datetime** -objekt till **ett String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-259">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="8fb5d-260">Om du vill visa ett objekts egenskaper och metoder skickar du objektet nedåt i pipeline till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="8fb5d-260">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="8fb5d-261">Ett exempel är `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-261">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="8fb5d-262">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8fb5d-262">NOTES</span></span>

<span data-ttu-id="8fb5d-263">**Datetime** -objekt är i långa och långa format för system språket.</span><span class="sxs-lookup"><span data-stu-id="8fb5d-263">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="8fb5d-264">Giltiga **UFormat-specificerare** visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="8fb5d-264">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="8fb5d-265">Format specificerare</span><span class="sxs-lookup"><span data-stu-id="8fb5d-265">Format specifier</span></span> |                                 <span data-ttu-id="8fb5d-266">Betydelse</span><span class="sxs-lookup"><span data-stu-id="8fb5d-266">Meaning</span></span>                     |         <span data-ttu-id="8fb5d-267">Exempel</span><span class="sxs-lookup"><span data-stu-id="8fb5d-267">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="8fb5d-268">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="8fb5d-268">Day of the week - full name</span></span>                                             | <span data-ttu-id="8fb5d-269">Måndag</span><span class="sxs-lookup"><span data-stu-id="8fb5d-269">Monday</span></span>                   |
| `%a` | <span data-ttu-id="8fb5d-270">Veckodag-förkortat namn</span><span class="sxs-lookup"><span data-stu-id="8fb5d-270">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="8fb5d-271">Mån</span><span class="sxs-lookup"><span data-stu-id="8fb5d-271">Mon</span></span>                      |
| `%B` | <span data-ttu-id="8fb5d-272">Månads namn – fullständig</span><span class="sxs-lookup"><span data-stu-id="8fb5d-272">Month name - full</span></span>                                                       | <span data-ttu-id="8fb5d-273">Januari</span><span class="sxs-lookup"><span data-stu-id="8fb5d-273">January</span></span>                  |
| `%b` | <span data-ttu-id="8fb5d-274">Månads namn – förkortat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-274">Month name - abbreviated</span></span>                                                | <span data-ttu-id="8fb5d-275">Jan</span><span class="sxs-lookup"><span data-stu-id="8fb5d-275">Jan</span></span>                      |
| `%C` | <span data-ttu-id="8fb5d-276">1900</span><span class="sxs-lookup"><span data-stu-id="8fb5d-276">Century</span></span>                                                                 | <span data-ttu-id="8fb5d-277">20 för 2019</span><span class="sxs-lookup"><span data-stu-id="8fb5d-277">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="8fb5d-278">Datum och tid – förkortat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-278">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="8fb5d-279">Tor Jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="8fb5d-279">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="8fb5d-280">Datum i formatet åååå-mm-dd</span><span class="sxs-lookup"><span data-stu-id="8fb5d-280">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="8fb5d-281">06/27/19</span><span class="sxs-lookup"><span data-stu-id="8fb5d-281">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="8fb5d-282">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="8fb5d-282">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="8fb5d-283">05</span><span class="sxs-lookup"><span data-stu-id="8fb5d-283">05</span></span>                       |
| `%e` | <span data-ttu-id="8fb5d-284">Dag i månaden – föregås av ett blank steg om bara en siffra</span><span class="sxs-lookup"><span data-stu-id="8fb5d-284">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="8fb5d-285">\<space\>5</span><span class="sxs-lookup"><span data-stu-id="8fb5d-285">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="8fb5d-286">Datum i åååå-mm-dd-format, motsvarar% Y-% m-% d (ISO 8601-datum format)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-286">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="8fb5d-287">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="8fb5d-287">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="8fb5d-288">Samma som "Y"</span><span class="sxs-lookup"><span data-stu-id="8fb5d-288">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="8fb5d-289">Samma som "y"</span><span class="sxs-lookup"><span data-stu-id="8fb5d-289">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="8fb5d-290">Timme i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-290">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="8fb5d-291">17</span><span class="sxs-lookup"><span data-stu-id="8fb5d-291">17</span></span>                       |
| `%h` | <span data-ttu-id="8fb5d-292">Samma som "b"</span><span class="sxs-lookup"><span data-stu-id="8fb5d-292">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="8fb5d-293">Timme i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-293">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="8fb5d-294">05</span><span class="sxs-lookup"><span data-stu-id="8fb5d-294">05</span></span>                       |
| `%j` | <span data-ttu-id="8fb5d-295">Dag på året</span><span class="sxs-lookup"><span data-stu-id="8fb5d-295">Day of the year</span></span>                                                         | <span data-ttu-id="8fb5d-296">1-366</span><span class="sxs-lookup"><span data-stu-id="8fb5d-296">1-366</span></span>                    |
| `%k` | <span data-ttu-id="8fb5d-297">Samma som "H"</span><span class="sxs-lookup"><span data-stu-id="8fb5d-297">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="8fb5d-298">Samma som "I" (versal I)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-298">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="8fb5d-299">05</span><span class="sxs-lookup"><span data-stu-id="8fb5d-299">05</span></span>                       |
| `%M` | <span data-ttu-id="8fb5d-300">Minuter</span><span class="sxs-lookup"><span data-stu-id="8fb5d-300">Minutes</span></span>                                                                 | <span data-ttu-id="8fb5d-301">35</span><span class="sxs-lookup"><span data-stu-id="8fb5d-301">35</span></span>                       |
| `%m` | <span data-ttu-id="8fb5d-302">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="8fb5d-302">Month number</span></span>                                                            | <span data-ttu-id="8fb5d-303">06</span><span class="sxs-lookup"><span data-stu-id="8fb5d-303">06</span></span>                       |
| `%n` | <span data-ttu-id="8fb5d-304">rad matnings tecknet</span><span class="sxs-lookup"><span data-stu-id="8fb5d-304">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="8fb5d-305">FM eller EM</span><span class="sxs-lookup"><span data-stu-id="8fb5d-305">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="8fb5d-306">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="8fb5d-306">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="8fb5d-307">17:45</span><span class="sxs-lookup"><span data-stu-id="8fb5d-307">17:45</span></span>                    |
| `%r` | <span data-ttu-id="8fb5d-308">Tid i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-308">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="8fb5d-309">09:15:36 AM</span><span class="sxs-lookup"><span data-stu-id="8fb5d-309">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="8fb5d-310">Sekunder</span><span class="sxs-lookup"><span data-stu-id="8fb5d-310">Seconds</span></span>                                                                 | <span data-ttu-id="8fb5d-311">05</span><span class="sxs-lookup"><span data-stu-id="8fb5d-311">05</span></span>                       |
| `%s` | <span data-ttu-id="8fb5d-312">Förflutna sekunder sedan den 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="8fb5d-312">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="8fb5d-313">1150451174</span><span class="sxs-lookup"><span data-stu-id="8fb5d-313">1150451174</span></span>               |
| `%t` | <span data-ttu-id="8fb5d-314">Vågrätt tabbtecken</span><span class="sxs-lookup"><span data-stu-id="8fb5d-314">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="8fb5d-315">Tid i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="8fb5d-315">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="8fb5d-316">17:45:52</span><span class="sxs-lookup"><span data-stu-id="8fb5d-316">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="8fb5d-317">Samma som "W"</span><span class="sxs-lookup"><span data-stu-id="8fb5d-317">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="8fb5d-318">Veckodag-nummer</span><span class="sxs-lookup"><span data-stu-id="8fb5d-318">Day of the week - number</span></span>                                                | <span data-ttu-id="8fb5d-319">Söndag = 0</span><span class="sxs-lookup"><span data-stu-id="8fb5d-319">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="8fb5d-320">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="8fb5d-320">Week of the year</span></span>                                                        | <span data-ttu-id="8fb5d-321">01-53</span><span class="sxs-lookup"><span data-stu-id="8fb5d-321">01-53</span></span>                    |
| `%w` | <span data-ttu-id="8fb5d-322">Samma som u</span><span class="sxs-lookup"><span data-stu-id="8fb5d-322">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="8fb5d-323">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="8fb5d-323">Week of the year</span></span>                                                        | <span data-ttu-id="8fb5d-324">00-52</span><span class="sxs-lookup"><span data-stu-id="8fb5d-324">00-52</span></span>                    |
| `%X` | <span data-ttu-id="8fb5d-325">Samma som t '</span><span class="sxs-lookup"><span data-stu-id="8fb5d-325">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="8fb5d-326">Datum i standardformat för språkvariant</span><span class="sxs-lookup"><span data-stu-id="8fb5d-326">Date in standard format for locale</span></span>                                      | <span data-ttu-id="8fb5d-327">06/27/19 för engelska – USA</span><span class="sxs-lookup"><span data-stu-id="8fb5d-327">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="8fb5d-328">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="8fb5d-328">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="8fb5d-329">2019</span><span class="sxs-lookup"><span data-stu-id="8fb5d-329">2019</span></span>                     |
| `%y` | <span data-ttu-id="8fb5d-330">År i 2-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="8fb5d-330">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="8fb5d-331">19</span><span class="sxs-lookup"><span data-stu-id="8fb5d-331">19</span></span>                       |
| `%Z` | <span data-ttu-id="8fb5d-332">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="8fb5d-332">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="8fb5d-333">-07</span><span class="sxs-lookup"><span data-stu-id="8fb5d-333">-07</span></span>                      |

## <span data-ttu-id="8fb5d-334">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8fb5d-334">RELATED LINKS</span></span>

[<span data-ttu-id="8fb5d-335">-Objekt</span><span class="sxs-lookup"><span data-stu-id="8fb5d-335">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="8fb5d-336">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="8fb5d-336">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="8fb5d-337">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="8fb5d-337">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="8fb5d-338">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="8fb5d-338">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="8fb5d-339">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8fb5d-339">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="8fb5d-340">Ange datum</span><span class="sxs-lookup"><span data-stu-id="8fb5d-340">Set-Date</span></span>](Set-Date.md)
