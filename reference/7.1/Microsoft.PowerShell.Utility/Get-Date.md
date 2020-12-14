---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 34b0d7833d858a8b71c28d0f872ddb9e4948b76d
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514991"
---
# <span data-ttu-id="6011a-103">Get-Date</span><span class="sxs-lookup"><span data-stu-id="6011a-103">Get-Date</span></span>

## <span data-ttu-id="6011a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6011a-104">SYNOPSIS</span></span>
<span data-ttu-id="6011a-105">Hämtar aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-105">Gets the current date and time.</span></span>

## <span data-ttu-id="6011a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6011a-106">SYNTAX</span></span>

### <span data-ttu-id="6011a-107">Datum (standard)</span><span class="sxs-lookup"><span data-stu-id="6011a-107">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="6011a-108">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="6011a-108">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="6011a-109">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="6011a-109">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="6011a-110">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="6011a-110">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="6011a-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6011a-111">DESCRIPTION</span></span>

<span data-ttu-id="6011a-112">`Get-Date`Cmdleten hämtar ett **datetime** -objekt som representerar det aktuella datumet eller ett datum som du anger.</span><span class="sxs-lookup"><span data-stu-id="6011a-112">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="6011a-113">`Get-Date` kan formatera datum och tid i flera .NET-och UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="6011a-113">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="6011a-114">Du kan använda `Get-Date` för att generera en datum-eller tids tecken sträng och sedan skicka strängen till andra cmdletar eller program.</span><span class="sxs-lookup"><span data-stu-id="6011a-114">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="6011a-115">`Get-Date` använder datorns kultur inställningar för att avgöra hur utdata formateras.</span><span class="sxs-lookup"><span data-stu-id="6011a-115">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="6011a-116">Använd om du vill visa datorns inställningar `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="6011a-116">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="6011a-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6011a-117">EXAMPLES</span></span>

### <span data-ttu-id="6011a-118">Exempel 1: Hämta aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="6011a-118">Example 1: Get the current date and time</span></span>

<span data-ttu-id="6011a-119">I det här exemplet `Get-Date` visas aktuellt system datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-119">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="6011a-120">Utdata är i formatet för långt datum och långt klock slag.</span><span class="sxs-lookup"><span data-stu-id="6011a-120">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="6011a-121">Exempel 2: Hämta element i aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="6011a-121">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="6011a-122">Det här exemplet visar hur du kan använda `Get-Date` för att hämta antingen datum-eller tids element.</span><span class="sxs-lookup"><span data-stu-id="6011a-122">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="6011a-123">Parametern använder argumenten **date**, **Time** eller **datetime**.</span><span class="sxs-lookup"><span data-stu-id="6011a-123">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="6011a-124">`Get-Date` använder parametern **DisplayHint** med **datum** argumentet för att bara hämta datumet.</span><span class="sxs-lookup"><span data-stu-id="6011a-124">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="6011a-125">Exempel 3: Hämta datum och tid med en .NET-format specifikation</span><span class="sxs-lookup"><span data-stu-id="6011a-125">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="6011a-126">I det här exemplet används en .NET-format specifikation för att anpassa utdatatypens format.</span><span class="sxs-lookup"><span data-stu-id="6011a-126">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="6011a-127">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-127">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="6011a-128">`Get-Date` använder **format** parametern för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="6011a-128">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="6011a-129">De .NET-format specificerare som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="6011a-129">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="6011a-130">Specificerare</span><span class="sxs-lookup"><span data-stu-id="6011a-130">Specifier</span></span> |                      <span data-ttu-id="6011a-131">Definition</span><span class="sxs-lookup"><span data-stu-id="6011a-131">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="6011a-132">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="6011a-132">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="6011a-133">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="6011a-133">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="6011a-134">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="6011a-134">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="6011a-135">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="6011a-135">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="6011a-136">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="6011a-136">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="6011a-137">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="6011a-137">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="6011a-138">Mer information om .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="6011a-138">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="6011a-139">Exempel 4: Hämta datum och tid med en UFormat-specificerare</span><span class="sxs-lookup"><span data-stu-id="6011a-139">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="6011a-140">I det här exemplet används flera **UFormat** format-specificerare för att anpassa utdatatypen.</span><span class="sxs-lookup"><span data-stu-id="6011a-140">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="6011a-141">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-141">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="6011a-142">`Get-Date` använder parametern **UFormat** för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="6011a-142">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="6011a-143">Det **UFormat** format som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="6011a-143">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="6011a-144">Specificerare</span><span class="sxs-lookup"><span data-stu-id="6011a-144">Specifier</span></span> |                      <span data-ttu-id="6011a-145">Definition</span><span class="sxs-lookup"><span data-stu-id="6011a-145">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="6011a-146">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="6011a-146">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="6011a-147">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="6011a-147">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="6011a-148">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="6011a-148">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="6011a-149">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="6011a-149">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="6011a-150">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="6011a-150">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="6011a-151">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="6011a-151">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="6011a-152">En lista över giltiga **UFormat** format-specificerare finns i avsnittet [Obs](#notes) !</span><span class="sxs-lookup"><span data-stu-id="6011a-152">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="6011a-153">Exempel 5: Hämta datumets dag på året</span><span class="sxs-lookup"><span data-stu-id="6011a-153">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="6011a-154">I det här exemplet används en egenskap för att hämta årets numeriska dag.</span><span class="sxs-lookup"><span data-stu-id="6011a-154">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="6011a-155">Den gregorianska kalendern har 365 dagar, med undantag för skottår som har 366 dagar.</span><span class="sxs-lookup"><span data-stu-id="6011a-155">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="6011a-156">Till exempel 31 december 2020 är dag 366.</span><span class="sxs-lookup"><span data-stu-id="6011a-156">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="6011a-157">`Get-Date` använder tre parametrar för att ange datum: **år**, **månad** och **dag**.</span><span class="sxs-lookup"><span data-stu-id="6011a-157">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="6011a-158">Kommandot omges av parenteser så att resultatet utvärderas av egenskapen **DayofYear** .</span><span class="sxs-lookup"><span data-stu-id="6011a-158">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="6011a-159">Exempel 6: kontrol lera om ett datum har justerats för sommar tid</span><span class="sxs-lookup"><span data-stu-id="6011a-159">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="6011a-160">I det här exemplet används en boolesk metod för att kontrol lera om ett datum justeras efter sommar tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-160">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="6011a-161">En variabel, `$DST` lagrar resultatet av `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="6011a-161">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="6011a-162">`$DST` använder metoden **IsDaylightSavingTime** för att testa om datumet justeras för sommar tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-162">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="6011a-163">Exempel 7: konvertera aktuell tid till UTC-tid</span><span class="sxs-lookup"><span data-stu-id="6011a-163">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="6011a-164">I det här exemplet konverteras den aktuella tiden till UTC-tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-164">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="6011a-165">UTC-förskjutningen för systemets nationella inställningar används för att konvertera tiden.</span><span class="sxs-lookup"><span data-stu-id="6011a-165">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="6011a-166">I en tabell i avsnittet [anteckningar](#notes) visas giltiga **UFormat** format-specifikationer.</span><span class="sxs-lookup"><span data-stu-id="6011a-166">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="6011a-167">`Get-Date` använder parametern **UFormat** med format specificerare för att visa aktuellt system datum och tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-167">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="6011a-168">Format specifikationen **% Z** representerar UTC-förskjutningen **-07**.</span><span class="sxs-lookup"><span data-stu-id="6011a-168">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="6011a-169">`$Time`Variabeln lagrar systemets aktuella datum och tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-169">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="6011a-170">`$Time` använder metoden **ToUniversalTime ()** för att konvertera tiden baserat på datorns UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="6011a-170">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="6011a-171">Exempel 8: skapa en tidsstämpel</span><span class="sxs-lookup"><span data-stu-id="6011a-171">Example 8: Create a timestamp</span></span>

<span data-ttu-id="6011a-172">I det här exemplet skapar en format specificerare ett **String** -objekt för tidsstämpel för ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="6011a-172">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="6011a-173">Tidsstämpeln innehåller datum, tid och UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="6011a-173">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="6011a-174">`$timestamp`Variabeln lagrar resultatet av ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="6011a-174">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="6011a-175">`Get-Date` använder **format** parametern med format specifikationen för gemener `o` för att skapa ett **String** -objekt med tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="6011a-175">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="6011a-176">Objektet skickas ned pipelinen till `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="6011a-176">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="6011a-177">En **script block** innehåller `$_` variabeln som representerar det aktuella pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="6011a-177">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="6011a-178">Tids stämplings strängen avgränsas med kolon som ersätts med punkter.</span><span class="sxs-lookup"><span data-stu-id="6011a-178">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="6011a-179">`New-Item` använder parametern **Path** för att ange platsen för en ny katalog.</span><span class="sxs-lookup"><span data-stu-id="6011a-179">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="6011a-180">Sökvägen innehåller `$timestamp` variabeln som katalog namn.</span><span class="sxs-lookup"><span data-stu-id="6011a-180">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="6011a-181">Parametern **Type** anger att en katalog har skapats.</span><span class="sxs-lookup"><span data-stu-id="6011a-181">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="6011a-182">Exempel 9: konvertera en Unix-tidsstämpel</span><span class="sxs-lookup"><span data-stu-id="6011a-182">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="6011a-183">I det här exemplet konverteras en UNIX-tid (som representeras av antalet sekunder sedan 1970-01-01 0:00:00) till DateTime.</span><span class="sxs-lookup"><span data-stu-id="6011a-183">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="6011a-184">Exempel 10: returnera ett datum värde som tolkas som UTC</span><span class="sxs-lookup"><span data-stu-id="6011a-184">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="6011a-185">Det här exemplet illustrerar hur du tolkar ett datum värde som dess UTC-motsvarighet.</span><span class="sxs-lookup"><span data-stu-id="6011a-185">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="6011a-186">I exemplet är den här datorn inställd på **Pacific, normal tid**.</span><span class="sxs-lookup"><span data-stu-id="6011a-186">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="6011a-187">Som standard `Get-Date` returnerar värden för den tids zonen.</span><span class="sxs-lookup"><span data-stu-id="6011a-187">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="6011a-188">Använd parametern **AsUTC** för att konvertera värdet till UTC-ekvivalent tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-188">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

```powershell
PS> Get-TimeZone

Id                         : Pacific Standard Time
DisplayName                : (UTC-08:00) Pacific Time (US & Canada)
StandardName               : Pacific Standard Time
DaylightName               : Pacific Daylight Time
BaseUtcOffset              : -08:00:00
SupportsDaylightSavingTime : True

PS> (Get-Date -Date "2020-01-01T00:00:00").Kind
Unspecified

PS> Get-Date -Date "2020-01-01T00:00:00"

Wednesday, January 1, 2020 12:00:00 AM

PS> (Get-Date -Date "2020-01-01T00:00:00" -AsUTC).Kind
Utc

PS> Get-Date -Date "2020-01-01T00:00:00" -AsUTC

Wednesday, January 1, 2020 8:00:00 AM
```

## <span data-ttu-id="6011a-189">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6011a-189">PARAMETERS</span></span>

### <span data-ttu-id="6011a-190">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="6011a-190">-AsUTC</span></span>

<span data-ttu-id="6011a-191">Konverterar datumvärdet till motsvarande tid i UTC.</span><span class="sxs-lookup"><span data-stu-id="6011a-191">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="6011a-192">Den här parametern introducerades i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="6011a-192">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6011a-193">-Datum</span><span class="sxs-lookup"><span data-stu-id="6011a-193">-Date</span></span>

<span data-ttu-id="6011a-194">Anger ett datum och en tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-194">Specifies a date and time.</span></span> <span data-ttu-id="6011a-195">Tiden är valfri och om det inte anges returneras 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="6011a-195">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="6011a-196">Ange datum och tid i ett format som är standard för system språket.</span><span class="sxs-lookup"><span data-stu-id="6011a-196">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="6011a-197">Till exempel på engelska (USA):</span><span class="sxs-lookup"><span data-stu-id="6011a-197">For example, in US English:</span></span>

<span data-ttu-id="6011a-198">`Get-Date -Date "6/25/2019 12:30:22"` Returnerar tisdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="6011a-198">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

```yaml
Type: System.DateTime
Parameter Sets: DateAndFormat, DateAndUFormat
Aliases: LastWriteTime

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6011a-199">– Dag</span><span class="sxs-lookup"><span data-stu-id="6011a-199">-Day</span></span>

<span data-ttu-id="6011a-200">Anger den dag i månaden som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-200">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="6011a-201">Ange ett värde från 1 till 31.</span><span class="sxs-lookup"><span data-stu-id="6011a-201">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="6011a-202">Om det angivna värdet är större än antalet dagar i månaden lägger PowerShell till antalet dagar i månaden.</span><span class="sxs-lookup"><span data-stu-id="6011a-202">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="6011a-203">Visar till exempel `Get-Date -Month 2 -Day 31` **3 mars**, inte **31 februari**.</span><span class="sxs-lookup"><span data-stu-id="6011a-203">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="6011a-204">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="6011a-204">-DisplayHint</span></span>

<span data-ttu-id="6011a-205">Anger vilka element i datum och tid som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-205">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="6011a-206">De godkända värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="6011a-206">The accepted values are as follows:</span></span>

- <span data-ttu-id="6011a-207">**Datum**: visar endast datumet</span><span class="sxs-lookup"><span data-stu-id="6011a-207">**Date**: displays only the date</span></span>
- <span data-ttu-id="6011a-208">**Tid**: visar endast tiden</span><span class="sxs-lookup"><span data-stu-id="6011a-208">**Time**: displays only the time</span></span>
- <span data-ttu-id="6011a-209">**Datetime**: visar datum och tid</span><span class="sxs-lookup"><span data-stu-id="6011a-209">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="6011a-210">– Format</span><span class="sxs-lookup"><span data-stu-id="6011a-210">-Format</span></span>

<span data-ttu-id="6011a-211">Visar datum och tid i det Microsoft .NET Framework-format som anges av format specifikationen.</span><span class="sxs-lookup"><span data-stu-id="6011a-211">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="6011a-212">**Format** parametern matar ut ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-212">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="6011a-213">En lista över tillgängliga .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="6011a-213">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="6011a-214">När **format** parametern används `Get-Date` får endast **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="6011a-214">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="6011a-215">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="6011a-215">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="6011a-216">Från och med PowerShell 5,0 kan du använda följande ytterligare format som värden för parametern **format** .</span><span class="sxs-lookup"><span data-stu-id="6011a-216">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="6011a-217">**Filedate**.</span><span class="sxs-lookup"><span data-stu-id="6011a-217">**FileDate**.</span></span> <span data-ttu-id="6011a-218">En fil eller Sök vägs vänlig representation av aktuellt datum i lokal tid.</span><span class="sxs-lookup"><span data-stu-id="6011a-218">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="6011a-219">Formatet är `yyyyMMdd` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad och en dag med två siffror).</span><span class="sxs-lookup"><span data-stu-id="6011a-219">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="6011a-220">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6011a-220">For example:</span></span>
  20190627.

- <span data-ttu-id="6011a-221">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="6011a-221">**FileDateUniversal**.</span></span> <span data-ttu-id="6011a-222">En fil eller Sök vägs vänlig representation av aktuellt datum i Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="6011a-222">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="6011a-223">Formatet är `yyyyMMddZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, en dag med en bokstav `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="6011a-223">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="6011a-224">Till exempel: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="6011a-224">For example: 20190627Z.</span></span>

- <span data-ttu-id="6011a-225">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="6011a-225">**FileDateTime**.</span></span> <span data-ttu-id="6011a-226">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="6011a-226">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="6011a-227">Formatet är `yyyyMMddTHHmmssffff` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund och 4-siffriga millisekunder).</span><span class="sxs-lookup"><span data-stu-id="6011a-227">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="6011a-228">Till exempel: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="6011a-228">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="6011a-229">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="6011a-229">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="6011a-230">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i Universal Time (UTC) i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="6011a-230">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="6011a-231">Formatet är `yyyyMMddTHHmmssffffZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund, 4-siffriga millisekunder och bokstaven `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="6011a-231">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="6011a-232">Till exempel: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="6011a-232">For example: 20190627T1540500718Z.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndFormat, UnixTimeSecondsAndFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6011a-233">– Timme</span><span class="sxs-lookup"><span data-stu-id="6011a-233">-Hour</span></span>

<span data-ttu-id="6011a-234">Anger den timme som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-234">Specifies the hour that is displayed.</span></span> <span data-ttu-id="6011a-235">Ange ett värde mellan 0 och 23.</span><span class="sxs-lookup"><span data-stu-id="6011a-235">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="6011a-236">– Millisekunde</span><span class="sxs-lookup"><span data-stu-id="6011a-236">-Millisecond</span></span>

<span data-ttu-id="6011a-237">Anger millisekunderna i datumet.</span><span class="sxs-lookup"><span data-stu-id="6011a-237">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="6011a-238">Ange ett värde mellan 0 och 999.</span><span class="sxs-lookup"><span data-stu-id="6011a-238">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="6011a-239">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6011a-239">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6011a-240">-Minut</span><span class="sxs-lookup"><span data-stu-id="6011a-240">-Minute</span></span>

<span data-ttu-id="6011a-241">Anger minuten som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-241">Specifies the minute that is displayed.</span></span> <span data-ttu-id="6011a-242">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="6011a-242">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="6011a-243">– Månad</span><span class="sxs-lookup"><span data-stu-id="6011a-243">-Month</span></span>

<span data-ttu-id="6011a-244">Anger den månad som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-244">Specifies the month that is displayed.</span></span> <span data-ttu-id="6011a-245">Ange ett värde mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="6011a-245">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="6011a-246">– Sekund</span><span class="sxs-lookup"><span data-stu-id="6011a-246">-Second</span></span>

<span data-ttu-id="6011a-247">Anger det andra som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-247">Specifies the second that is displayed.</span></span> <span data-ttu-id="6011a-248">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="6011a-248">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="6011a-249">-UFormat</span><span class="sxs-lookup"><span data-stu-id="6011a-249">-UFormat</span></span>

<span data-ttu-id="6011a-250">Visar datum och tid i UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="6011a-250">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="6011a-251">**UFormat** -parametern matar ut ett String-objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-251">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="6011a-252">**UFormat** -specificerarna föregås av ett procent tecken ( `%` ), till exempel, `%m` , `%d` och `%Y` .</span><span class="sxs-lookup"><span data-stu-id="6011a-252">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="6011a-253">Avsnittet [anteckningar](#notes) innehåller en tabell med giltiga **UFormat-specificerare**.</span><span class="sxs-lookup"><span data-stu-id="6011a-253">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="6011a-254">När parametern **UFormat** används `Get-Date` får bara **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="6011a-254">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="6011a-255">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="6011a-255">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

```yaml
Type: System.String
Parameter Sets: DateAndUFormat, UnixTimeSecondsAndUFormat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6011a-256">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="6011a-256">-UnixTimeSeconds</span></span>

<span data-ttu-id="6011a-257">Datum och tid som representeras i sekunder sedan 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="6011a-257">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="6011a-258">Den här parametern introducerades i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="6011a-258">This parameter was introduced in PowerShell 7.1.</span></span>

```yaml
Type: System.Int64
Parameter Sets: UnixTimeSecondsAndFormat, UnixTimeSecondsAndUFormat
Aliases: UnixTime

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6011a-259">-År</span><span class="sxs-lookup"><span data-stu-id="6011a-259">-Year</span></span>

<span data-ttu-id="6011a-260">Anger året som visas.</span><span class="sxs-lookup"><span data-stu-id="6011a-260">Specifies the year that is displayed.</span></span> <span data-ttu-id="6011a-261">Ange ett värde mellan 1 och 9999.</span><span class="sxs-lookup"><span data-stu-id="6011a-261">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="6011a-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6011a-262">CommonParameters</span></span>

<span data-ttu-id="6011a-263">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6011a-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6011a-264">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6011a-264">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6011a-265">INDATA</span><span class="sxs-lookup"><span data-stu-id="6011a-265">INPUTS</span></span>

### <span data-ttu-id="6011a-266">Pipeline-inmatade</span><span class="sxs-lookup"><span data-stu-id="6011a-266">Pipeline input</span></span>

<span data-ttu-id="6011a-267">`Get-Date` accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="6011a-267">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="6011a-268">Ett exempel är `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="6011a-268">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="6011a-269">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6011a-269">OUTPUTS</span></span>

### <span data-ttu-id="6011a-270">System. DateTime eller system. String</span><span class="sxs-lookup"><span data-stu-id="6011a-270">System.DateTime or System.String</span></span>

<span data-ttu-id="6011a-271">`Get-Date` Returnerar ett **datetime** -objekt utom när **format** -och **UFormat** -parametrarna används.</span><span class="sxs-lookup"><span data-stu-id="6011a-271">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="6011a-272">**Format** -eller **UFormat** -parametrarna returnerar **sträng** objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-272">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="6011a-273">När ett **datetime** -objekt skickas ned pipelinen till en-cmdlet, till exempel `Add-Content` som förväntar sig sträng Indatatyp, konverterar PowerShell objektet till ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-273">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="6011a-274">Metoden `(Get-Date).ToString()` konverterar ett **datetime** -objekt till **ett String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="6011a-274">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="6011a-275">Om du vill visa ett objekts egenskaper och metoder skickar du objektet nedåt i pipeline till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="6011a-275">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="6011a-276">Ett exempel är `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="6011a-276">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="6011a-277">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6011a-277">NOTES</span></span>

<span data-ttu-id="6011a-278">**Datetime** -objekt är i långa och långa format för system språket.</span><span class="sxs-lookup"><span data-stu-id="6011a-278">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="6011a-279">Giltiga **UFormat-specificerare** visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="6011a-279">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="6011a-280">Format specificerare</span><span class="sxs-lookup"><span data-stu-id="6011a-280">Format specifier</span></span> |                                 <span data-ttu-id="6011a-281">Betydelse</span><span class="sxs-lookup"><span data-stu-id="6011a-281">Meaning</span></span>                     |         <span data-ttu-id="6011a-282">Exempel</span><span class="sxs-lookup"><span data-stu-id="6011a-282">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="6011a-283">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="6011a-283">Day of the week - full name</span></span>                                             | <span data-ttu-id="6011a-284">Måndag</span><span class="sxs-lookup"><span data-stu-id="6011a-284">Monday</span></span>                   |
| `%a` | <span data-ttu-id="6011a-285">Veckodag-förkortat namn</span><span class="sxs-lookup"><span data-stu-id="6011a-285">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="6011a-286">Mån</span><span class="sxs-lookup"><span data-stu-id="6011a-286">Mon</span></span>                      |
| `%B` | <span data-ttu-id="6011a-287">Månads namn – fullständig</span><span class="sxs-lookup"><span data-stu-id="6011a-287">Month name - full</span></span>                                                       | <span data-ttu-id="6011a-288">Januari</span><span class="sxs-lookup"><span data-stu-id="6011a-288">January</span></span>                  |
| `%b` | <span data-ttu-id="6011a-289">Månads namn – förkortat</span><span class="sxs-lookup"><span data-stu-id="6011a-289">Month name - abbreviated</span></span>                                                | <span data-ttu-id="6011a-290">Jan</span><span class="sxs-lookup"><span data-stu-id="6011a-290">Jan</span></span>                      |
| `%C` | <span data-ttu-id="6011a-291">1900</span><span class="sxs-lookup"><span data-stu-id="6011a-291">Century</span></span>                                                                 | <span data-ttu-id="6011a-292">20 för 2019</span><span class="sxs-lookup"><span data-stu-id="6011a-292">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="6011a-293">Datum och tid – förkortat</span><span class="sxs-lookup"><span data-stu-id="6011a-293">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="6011a-294">Tor Jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="6011a-294">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="6011a-295">Datum i formatet åååå-mm-dd</span><span class="sxs-lookup"><span data-stu-id="6011a-295">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="6011a-296">06/27/19</span><span class="sxs-lookup"><span data-stu-id="6011a-296">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="6011a-297">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="6011a-297">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="6011a-298">05</span><span class="sxs-lookup"><span data-stu-id="6011a-298">05</span></span>                       |
| `%e` | <span data-ttu-id="6011a-299">Dag i månaden – föregås av ett blank steg om bara en siffra</span><span class="sxs-lookup"><span data-stu-id="6011a-299">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="6011a-300">\<space\>5</span><span class="sxs-lookup"><span data-stu-id="6011a-300">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="6011a-301">Datum i åååå-mm-dd-format, motsvarar% Y-% m-% d (ISO 8601-datum format)</span><span class="sxs-lookup"><span data-stu-id="6011a-301">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="6011a-302">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="6011a-302">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="6011a-303">Samma som "Y"</span><span class="sxs-lookup"><span data-stu-id="6011a-303">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="6011a-304">Samma som "y"</span><span class="sxs-lookup"><span data-stu-id="6011a-304">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="6011a-305">Timme i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="6011a-305">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="6011a-306">17</span><span class="sxs-lookup"><span data-stu-id="6011a-306">17</span></span>                       |
| `%h` | <span data-ttu-id="6011a-307">Samma som "b"</span><span class="sxs-lookup"><span data-stu-id="6011a-307">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="6011a-308">Timme i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="6011a-308">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="6011a-309">05</span><span class="sxs-lookup"><span data-stu-id="6011a-309">05</span></span>                       |
| `%j` | <span data-ttu-id="6011a-310">Dag på året</span><span class="sxs-lookup"><span data-stu-id="6011a-310">Day of the year</span></span>                                                         | <span data-ttu-id="6011a-311">1-366</span><span class="sxs-lookup"><span data-stu-id="6011a-311">1-366</span></span>                    |
| `%k` | <span data-ttu-id="6011a-312">Samma som "H"</span><span class="sxs-lookup"><span data-stu-id="6011a-312">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="6011a-313">Samma som "I" (versal I)</span><span class="sxs-lookup"><span data-stu-id="6011a-313">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="6011a-314">05</span><span class="sxs-lookup"><span data-stu-id="6011a-314">05</span></span>                       |
| `%M` | <span data-ttu-id="6011a-315">Minuter</span><span class="sxs-lookup"><span data-stu-id="6011a-315">Minutes</span></span>                                                                 | <span data-ttu-id="6011a-316">35</span><span class="sxs-lookup"><span data-stu-id="6011a-316">35</span></span>                       |
| `%m` | <span data-ttu-id="6011a-317">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="6011a-317">Month number</span></span>                                                            | <span data-ttu-id="6011a-318">06</span><span class="sxs-lookup"><span data-stu-id="6011a-318">06</span></span>                       |
| `%n` | <span data-ttu-id="6011a-319">rad matnings tecknet</span><span class="sxs-lookup"><span data-stu-id="6011a-319">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="6011a-320">FM eller EM</span><span class="sxs-lookup"><span data-stu-id="6011a-320">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="6011a-321">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="6011a-321">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="6011a-322">17:45</span><span class="sxs-lookup"><span data-stu-id="6011a-322">17:45</span></span>                    |
| `%r` | <span data-ttu-id="6011a-323">Tid i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="6011a-323">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="6011a-324">09:15:36 AM</span><span class="sxs-lookup"><span data-stu-id="6011a-324">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="6011a-325">Sekunder</span><span class="sxs-lookup"><span data-stu-id="6011a-325">Seconds</span></span>                                                                 | <span data-ttu-id="6011a-326">05</span><span class="sxs-lookup"><span data-stu-id="6011a-326">05</span></span>                       |
| `%s` | <span data-ttu-id="6011a-327">Förflutna sekunder sedan den 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="6011a-327">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="6011a-328">1150451174</span><span class="sxs-lookup"><span data-stu-id="6011a-328">1150451174</span></span>               |
| `%t` | <span data-ttu-id="6011a-329">Vågrätt tabbtecken</span><span class="sxs-lookup"><span data-stu-id="6011a-329">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="6011a-330">Tid i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="6011a-330">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="6011a-331">17:45:52</span><span class="sxs-lookup"><span data-stu-id="6011a-331">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="6011a-332">Samma som "W"</span><span class="sxs-lookup"><span data-stu-id="6011a-332">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="6011a-333">Veckodag-nummer</span><span class="sxs-lookup"><span data-stu-id="6011a-333">Day of the week - number</span></span>                                                | <span data-ttu-id="6011a-334">Söndag = 0</span><span class="sxs-lookup"><span data-stu-id="6011a-334">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="6011a-335">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="6011a-335">Week of the year</span></span>                                                        | <span data-ttu-id="6011a-336">01-53</span><span class="sxs-lookup"><span data-stu-id="6011a-336">01-53</span></span>                    |
| `%w` | <span data-ttu-id="6011a-337">Samma som u</span><span class="sxs-lookup"><span data-stu-id="6011a-337">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="6011a-338">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="6011a-338">Week of the year</span></span>                                                        | <span data-ttu-id="6011a-339">00-52</span><span class="sxs-lookup"><span data-stu-id="6011a-339">00-52</span></span>                    |
| `%X` | <span data-ttu-id="6011a-340">Samma som t '</span><span class="sxs-lookup"><span data-stu-id="6011a-340">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="6011a-341">Datum i standardformat för språkvariant</span><span class="sxs-lookup"><span data-stu-id="6011a-341">Date in standard format for locale</span></span>                                      | <span data-ttu-id="6011a-342">06/27/19 för engelska – USA</span><span class="sxs-lookup"><span data-stu-id="6011a-342">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="6011a-343">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="6011a-343">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="6011a-344">2019</span><span class="sxs-lookup"><span data-stu-id="6011a-344">2019</span></span>                     |
| `%y` | <span data-ttu-id="6011a-345">År i 2-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="6011a-345">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="6011a-346">19</span><span class="sxs-lookup"><span data-stu-id="6011a-346">19</span></span>                       |
| `%Z` | <span data-ttu-id="6011a-347">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="6011a-347">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="6011a-348">-07</span><span class="sxs-lookup"><span data-stu-id="6011a-348">-07</span></span>                      |

## <span data-ttu-id="6011a-349">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6011a-349">RELATED LINKS</span></span>

[<span data-ttu-id="6011a-350">-Objekt</span><span class="sxs-lookup"><span data-stu-id="6011a-350">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="6011a-351">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="6011a-351">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="6011a-352">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="6011a-352">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="6011a-353">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="6011a-353">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="6011a-354">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6011a-354">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="6011a-355">Ange datum</span><span class="sxs-lookup"><span data-stu-id="6011a-355">Set-Date</span></span>](Set-Date.md)
