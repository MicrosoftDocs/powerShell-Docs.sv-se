---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-date?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Date
ms.openlocfilehash: 8c0a1b7a14f5dfa071a85808f5d7dfba4d06048e
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514974"
---
# <span data-ttu-id="64e54-102">Get-Date</span><span class="sxs-lookup"><span data-stu-id="64e54-102">Get-Date</span></span>

## <span data-ttu-id="64e54-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="64e54-103">SYNOPSIS</span></span>
<span data-ttu-id="64e54-104">Hämtar aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-104">Gets the current date and time.</span></span>

## <span data-ttu-id="64e54-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64e54-105">SYNTAX</span></span>

### <span data-ttu-id="64e54-106">Datum (standard)</span><span class="sxs-lookup"><span data-stu-id="64e54-106">Date (Default)</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="64e54-107">DateUFormat</span><span class="sxs-lookup"><span data-stu-id="64e54-107">DateUFormat</span></span>

```
Get-Date [[-Date] <DateTime>] [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

### <span data-ttu-id="64e54-108">UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="64e54-108">UnixTimeSeconds</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 [-Format <String>] [-AsUTC] [<CommonParameters>]
```

### <span data-ttu-id="64e54-109">UnixTimeSecondsUFormat</span><span class="sxs-lookup"><span data-stu-id="64e54-109">UnixTimeSecondsUFormat</span></span>

```
Get-Date -UnixTimeSeconds <Int64> [-Year <Int32>] [-Month <Int32>] [-Day <Int32>] [-Hour <Int32>]
 [-Minute <Int32>] [-Second <Int32>] [-Millisecond <Int32>] [-DisplayHint <DisplayHintType>]
 -UFormat <String> [<CommonParameters>]
```

## <span data-ttu-id="64e54-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="64e54-110">DESCRIPTION</span></span>

<span data-ttu-id="64e54-111">`Get-Date`Cmdleten hämtar ett **datetime** -objekt som representerar det aktuella datumet eller ett datum som du anger.</span><span class="sxs-lookup"><span data-stu-id="64e54-111">The `Get-Date` cmdlet gets a **DateTime** object that represents the current date or a date that you specify.</span></span> <span data-ttu-id="64e54-112">`Get-Date` kan formatera datum och tid i flera .NET-och UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="64e54-112">`Get-Date` can format the date and time in several .NET and UNIX formats.</span></span> <span data-ttu-id="64e54-113">Du kan använda `Get-Date` för att generera en datum-eller tids tecken sträng och sedan skicka strängen till andra cmdletar eller program.</span><span class="sxs-lookup"><span data-stu-id="64e54-113">You can use `Get-Date` to generate a date or time character string, and then send the string to other cmdlets or programs.</span></span>

<span data-ttu-id="64e54-114">`Get-Date` använder datorns kultur inställningar för att avgöra hur utdata formateras.</span><span class="sxs-lookup"><span data-stu-id="64e54-114">`Get-Date` uses the computer's culture settings to determine how the output is formatted.</span></span> <span data-ttu-id="64e54-115">Använd om du vill visa datorns inställningar `(Get-Culture).DateTimeFormat` .</span><span class="sxs-lookup"><span data-stu-id="64e54-115">To view your computer's settings, use `(Get-Culture).DateTimeFormat`.</span></span>

## <span data-ttu-id="64e54-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="64e54-116">EXAMPLES</span></span>

### <span data-ttu-id="64e54-117">Exempel 1: Hämta aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="64e54-117">Example 1: Get the current date and time</span></span>

<span data-ttu-id="64e54-118">I det här exemplet `Get-Date` visas aktuellt system datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-118">In this example, `Get-Date` displays the current system date and time.</span></span> <span data-ttu-id="64e54-119">Utdata är i formatet för långt datum och långt klock slag.</span><span class="sxs-lookup"><span data-stu-id="64e54-119">The output is in the long-date and long-time formats.</span></span>

```powershell
Get-Date
```

```Output
Tuesday, June 25, 2019 14:53:32
```

### <span data-ttu-id="64e54-120">Exempel 2: Hämta element i aktuellt datum och tid</span><span class="sxs-lookup"><span data-stu-id="64e54-120">Example 2: Get elements of the current date and time</span></span>

<span data-ttu-id="64e54-121">Det här exemplet visar hur du kan använda `Get-Date` för att hämta antingen datum-eller tids element.</span><span class="sxs-lookup"><span data-stu-id="64e54-121">This example shows how to use `Get-Date` to get either the date or time element.</span></span> <span data-ttu-id="64e54-122">Parametern använder argumenten **date**, **Time** eller **datetime**.</span><span class="sxs-lookup"><span data-stu-id="64e54-122">The parameter uses the arguments **Date**, **Time**, or **DateTime**.</span></span>

```powershell
Get-Date -DisplayHint Date
```

```Output
Tuesday, June 25, 2019
```

<span data-ttu-id="64e54-123">`Get-Date` använder parametern **DisplayHint** med **datum** argumentet för att bara hämta datumet.</span><span class="sxs-lookup"><span data-stu-id="64e54-123">`Get-Date` uses the **DisplayHint** parameter with the **Date** argument to get only the date.</span></span>

### <span data-ttu-id="64e54-124">Exempel 3: Hämta datum och tid med en .NET-format specifikation</span><span class="sxs-lookup"><span data-stu-id="64e54-124">Example 3: Get the date and time with a .NET format specifier</span></span>

<span data-ttu-id="64e54-125">I det här exemplet används en .NET-format specifikation för att anpassa utdatatypens format.</span><span class="sxs-lookup"><span data-stu-id="64e54-125">In this example, a .NET format specifier is used to customize the output's format.</span></span> <span data-ttu-id="64e54-126">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-126">The output is a **String** object.</span></span>

```powershell
Get-Date -Format "dddd MM/dd/yyyy HH:mm K"
```

```Output
Tuesday 06/25/2019 16:17 -07:00
```

<span data-ttu-id="64e54-127">`Get-Date` använder **format** parametern för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="64e54-127">`Get-Date` uses the **Format** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="64e54-128">De .NET-format specificerare som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="64e54-128">The .NET format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="64e54-129">Specificerare</span><span class="sxs-lookup"><span data-stu-id="64e54-129">Specifier</span></span> |                      <span data-ttu-id="64e54-130">Definition</span><span class="sxs-lookup"><span data-stu-id="64e54-130">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `dddd`    | <span data-ttu-id="64e54-131">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="64e54-131">Day of the week - full name</span></span>                           |
| `MM`      | <span data-ttu-id="64e54-132">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="64e54-132">Month number</span></span>                                          |
| `dd`      | <span data-ttu-id="64e54-133">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="64e54-133">Day of the month - 2 digits</span></span>                           |
| `yyyy`    | <span data-ttu-id="64e54-134">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="64e54-134">Year in 4-digit format</span></span>                                |
| `HH:mm`   | <span data-ttu-id="64e54-135">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="64e54-135">Time in 24-hour format - no seconds</span></span>                    |
| `K`       | <span data-ttu-id="64e54-136">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="64e54-136">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="64e54-137">Mer information om .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="64e54-137">For more information about .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

### <span data-ttu-id="64e54-138">Exempel 4: Hämta datum och tid med en UFormat-specificerare</span><span class="sxs-lookup"><span data-stu-id="64e54-138">Example 4: Get the date and time with a UFormat specifier</span></span>

<span data-ttu-id="64e54-139">I det här exemplet används flera **UFormat** format-specificerare för att anpassa utdatatypen.</span><span class="sxs-lookup"><span data-stu-id="64e54-139">In this example, several **UFormat** format specifiers are used to customize the output's format.</span></span>
<span data-ttu-id="64e54-140">Utdata är ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-140">The output is a **String** object.</span></span>

```powershell
Get-Date -UFormat "%A %m/%d/%Y %R %Z"
```

```Output
Tuesday 06/25/2019 16:19 -07
```

<span data-ttu-id="64e54-141">`Get-Date` använder parametern **UFormat** för att ange flera format specificerare.</span><span class="sxs-lookup"><span data-stu-id="64e54-141">`Get-Date` uses the **UFormat** parameter to specify several format specifiers.</span></span>

<span data-ttu-id="64e54-142">Det **UFormat** format som används i det här exemplet definieras enligt följande:</span><span class="sxs-lookup"><span data-stu-id="64e54-142">The **UFormat** format specifiers used in this example are defined as follows:</span></span>

| <span data-ttu-id="64e54-143">Specificerare</span><span class="sxs-lookup"><span data-stu-id="64e54-143">Specifier</span></span> |                      <span data-ttu-id="64e54-144">Definition</span><span class="sxs-lookup"><span data-stu-id="64e54-144">Definition</span></span>                       |
| --------- | ----------------------------------------------------- |
| `%A`      | <span data-ttu-id="64e54-145">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="64e54-145">Day of the week - full name</span></span>                           |
| `%m`      | <span data-ttu-id="64e54-146">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="64e54-146">Month number</span></span>                                          |
| `%d`      | <span data-ttu-id="64e54-147">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="64e54-147">Day of the month - 2 digits</span></span>                           |
| `%Y`      | <span data-ttu-id="64e54-148">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="64e54-148">Year in 4-digit format</span></span>                                |
| `%R`      | <span data-ttu-id="64e54-149">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="64e54-149">Time in 24-hour format - no seconds</span></span>                    |
| `%Z`      | <span data-ttu-id="64e54-150">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="64e54-150">Time zone offset from Universal Time Coordinate (UTC)</span></span> |

<span data-ttu-id="64e54-151">En lista över giltiga **UFormat** format-specificerare finns i avsnittet [Obs](#notes) !</span><span class="sxs-lookup"><span data-stu-id="64e54-151">For a list of valid **UFormat** format specifiers, see the [Notes](#notes) section.</span></span>

### <span data-ttu-id="64e54-152">Exempel 5: Hämta datumets dag på året</span><span class="sxs-lookup"><span data-stu-id="64e54-152">Example 5: Get a date's day of the year</span></span>

<span data-ttu-id="64e54-153">I det här exemplet används en egenskap för att hämta årets numeriska dag.</span><span class="sxs-lookup"><span data-stu-id="64e54-153">In this example, a property is used to get the numeric day of the year.</span></span>

<span data-ttu-id="64e54-154">Den gregorianska kalendern har 365 dagar, med undantag för skottår som har 366 dagar.</span><span class="sxs-lookup"><span data-stu-id="64e54-154">The Gregorian calendar has 365 days, except for leap years that have 366 days.</span></span> <span data-ttu-id="64e54-155">Till exempel 31 december 2020 är dag 366.</span><span class="sxs-lookup"><span data-stu-id="64e54-155">For example, December 31, 2020 is day 366.</span></span>

```powershell
(Get-Date -Year 2020 -Month 12 -Day 31).DayOfYear
```

```Output
366
```

<span data-ttu-id="64e54-156">`Get-Date` använder tre parametrar för att ange datum: **år**, **månad** och **dag**.</span><span class="sxs-lookup"><span data-stu-id="64e54-156">`Get-Date` uses three parameters to specify the date: **Year**, **Month**, and **Day**.</span></span> <span data-ttu-id="64e54-157">Kommandot omges av parenteser så att resultatet utvärderas av egenskapen **DayofYear** .</span><span class="sxs-lookup"><span data-stu-id="64e54-157">The command is wrapped with parentheses so that the result is evaluated by the **DayofYear** property.</span></span>

### <span data-ttu-id="64e54-158">Exempel 6: kontrol lera om ett datum har justerats för sommar tid</span><span class="sxs-lookup"><span data-stu-id="64e54-158">Example 6: Check if a date is adjusted for daylight savings time</span></span>

<span data-ttu-id="64e54-159">I det här exemplet används en boolesk metod för att kontrol lera om ett datum justeras efter sommar tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-159">This example uses a boolean method to verify if a date is adjusted by daylight savings time.</span></span>

```powershell
$DST = Get-Date
$DST.IsDaylightSavingTime()
```

```Output
True
```

<span data-ttu-id="64e54-160">En variabel, `$DST` lagrar resultatet av `Get-Date` .</span><span class="sxs-lookup"><span data-stu-id="64e54-160">A variable, `$DST` stores the result of `Get-Date`.</span></span> <span data-ttu-id="64e54-161">`$DST` använder metoden **IsDaylightSavingTime** för att testa om datumet justeras för sommar tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-161">`$DST` uses the **IsDaylightSavingTime** method to test if the date is adjusted for daylight savings time.</span></span>

### <span data-ttu-id="64e54-162">Exempel 7: konvertera aktuell tid till UTC-tid</span><span class="sxs-lookup"><span data-stu-id="64e54-162">Example 7: Convert the current time to UTC time</span></span>

<span data-ttu-id="64e54-163">I det här exemplet konverteras den aktuella tiden till UTC-tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-163">In this example, the current time is converted to UTC time.</span></span> <span data-ttu-id="64e54-164">UTC-förskjutningen för systemets nationella inställningar används för att konvertera tiden.</span><span class="sxs-lookup"><span data-stu-id="64e54-164">The UTC offset for the system's locale is used to convert the time.</span></span> <span data-ttu-id="64e54-165">I en tabell i avsnittet [anteckningar](#notes) visas giltiga **UFormat** format-specifikationer.</span><span class="sxs-lookup"><span data-stu-id="64e54-165">A table in the [Notes](#notes) section lists the valid **UFormat** format specifiers.</span></span>

```powershell
Get-Date -UFormat "%A %B/%d/%Y %T %Z"
$Time = Get-Date
$Time.ToUniversalTime()
```

```Output
Wednesday June/26/2019 10:45:26 -07

Wednesday, June 26, 2019 17:45:26
```

<span data-ttu-id="64e54-166">`Get-Date` använder parametern **UFormat** med format specificerare för att visa aktuellt system datum och tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-166">`Get-Date` uses the **UFormat** parameter with format specifiers to display the current system date and time.</span></span> <span data-ttu-id="64e54-167">Format specifikationen **% Z** representerar UTC-förskjutningen **-07**.</span><span class="sxs-lookup"><span data-stu-id="64e54-167">The format specifier **%Z** represents the UTC offset of **-07**.</span></span>

<span data-ttu-id="64e54-168">`$Time`Variabeln lagrar systemets aktuella datum och tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-168">The `$Time` variable stores the current system date and time.</span></span> <span data-ttu-id="64e54-169">`$Time` använder metoden **ToUniversalTime ()** för att konvertera tiden baserat på datorns UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="64e54-169">`$Time` uses the **ToUniversalTime()** method to convert the time based on the computer's UTC offset.</span></span>

### <span data-ttu-id="64e54-170">Exempel 8: skapa en tidsstämpel</span><span class="sxs-lookup"><span data-stu-id="64e54-170">Example 8: Create a timestamp</span></span>

<span data-ttu-id="64e54-171">I det här exemplet skapar en format specificerare ett **String** -objekt för tidsstämpel för ett katalog namn.</span><span class="sxs-lookup"><span data-stu-id="64e54-171">In this example, a format specifier creates a timestamp **String** object for a directory name.</span></span> <span data-ttu-id="64e54-172">Tidsstämpeln innehåller datum, tid och UTC-förskjutning.</span><span class="sxs-lookup"><span data-stu-id="64e54-172">The timestamp includes the date, time, and UTC offset.</span></span>

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

<span data-ttu-id="64e54-173">`$timestamp`Variabeln lagrar resultatet av ett `Get-Date` kommando.</span><span class="sxs-lookup"><span data-stu-id="64e54-173">The `$timestamp` variable stores the results of a `Get-Date` command.</span></span> <span data-ttu-id="64e54-174">`Get-Date` använder **format** parametern med format specifikationen för gemener `o` för att skapa ett **String** -objekt med tidsstämpel.</span><span class="sxs-lookup"><span data-stu-id="64e54-174">`Get-Date` uses the **Format** parameter with the format specifier of lowercase `o` to create a timestamp **String** object.</span></span> <span data-ttu-id="64e54-175">Objektet skickas ned pipelinen till `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="64e54-175">The object is sent down the pipeline to `ForEach-Object`.</span></span> <span data-ttu-id="64e54-176">En **script block** innehåller `$_` variabeln som representerar det aktuella pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="64e54-176">A **ScriptBlock** contains the `$_` variable that represents the current pipeline object.</span></span> <span data-ttu-id="64e54-177">Tids stämplings strängen avgränsas med kolon som ersätts med punkter.</span><span class="sxs-lookup"><span data-stu-id="64e54-177">The timestamp string is delimited by colons that are replaced by periods.</span></span>

<span data-ttu-id="64e54-178">`New-Item` använder parametern **Path** för att ange platsen för en ny katalog.</span><span class="sxs-lookup"><span data-stu-id="64e54-178">`New-Item` uses the **Path** parameter to specify the location for a new directory.</span></span> <span data-ttu-id="64e54-179">Sökvägen innehåller `$timestamp` variabeln som katalog namn.</span><span class="sxs-lookup"><span data-stu-id="64e54-179">The path includes the `$timestamp` variable as the directory name.</span></span> <span data-ttu-id="64e54-180">Parametern **Type** anger att en katalog har skapats.</span><span class="sxs-lookup"><span data-stu-id="64e54-180">The **Type** parameter specifies that a directory is created.</span></span>

### <span data-ttu-id="64e54-181">Exempel 9: konvertera en Unix-tidsstämpel</span><span class="sxs-lookup"><span data-stu-id="64e54-181">Example 9: Convert a Unix timestamp</span></span>

<span data-ttu-id="64e54-182">I det här exemplet konverteras en UNIX-tid (som representeras av antalet sekunder sedan 1970-01-01 0:00:00) till DateTime.</span><span class="sxs-lookup"><span data-stu-id="64e54-182">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

```powershell
Get-Date -UnixTimeSeconds 1577836800
```

```Output
Wednesday, January 01, 2020 12:00:00 AM
```

### <span data-ttu-id="64e54-183">Exempel 10: returnera ett datum värde som tolkas som UTC</span><span class="sxs-lookup"><span data-stu-id="64e54-183">Example 10: Return a date value interpreted as UTC</span></span>

<span data-ttu-id="64e54-184">Det här exemplet illustrerar hur du tolkar ett datum värde som dess UTC-motsvarighet.</span><span class="sxs-lookup"><span data-stu-id="64e54-184">This example shows how to interpret a date value as its UTC equivalent.</span></span> <span data-ttu-id="64e54-185">I exemplet är den här datorn inställd på **Pacific, normal tid**.</span><span class="sxs-lookup"><span data-stu-id="64e54-185">For the example, this machine is set to **Pacific Standard Time**.</span></span> <span data-ttu-id="64e54-186">Som standard `Get-Date` returnerar värden för den tids zonen.</span><span class="sxs-lookup"><span data-stu-id="64e54-186">By default, `Get-Date` returns values for that timezone.</span></span> <span data-ttu-id="64e54-187">Använd parametern **AsUTC** för att konvertera värdet till UTC-ekvivalent tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-187">Use the **AsUTC** parameter to convert the value to the UTC equivalent time.</span></span>

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

## <span data-ttu-id="64e54-188">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="64e54-188">PARAMETERS</span></span>

### <span data-ttu-id="64e54-189">-AsUTC</span><span class="sxs-lookup"><span data-stu-id="64e54-189">-AsUTC</span></span>

<span data-ttu-id="64e54-190">Konverterar datumvärdet till motsvarande tid i UTC.</span><span class="sxs-lookup"><span data-stu-id="64e54-190">Converts the date value to the equivalent time in UTC.</span></span>

<span data-ttu-id="64e54-191">Den här parametern introducerades i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="64e54-191">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="64e54-192">-Datum</span><span class="sxs-lookup"><span data-stu-id="64e54-192">-Date</span></span>

<span data-ttu-id="64e54-193">Anger ett datum och en tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-193">Specifies a date and time.</span></span> <span data-ttu-id="64e54-194">Tiden är valfri och om det inte anges returneras 00:00:00.</span><span class="sxs-lookup"><span data-stu-id="64e54-194">Time is optional and if not specified, returns 00:00:00.</span></span>

<span data-ttu-id="64e54-195">Ange datum och tid i ett format som är standard för system språket.</span><span class="sxs-lookup"><span data-stu-id="64e54-195">Enter the date and time in a format that is standard for the system locale.</span></span>

<span data-ttu-id="64e54-196">Till exempel på engelska (USA):</span><span class="sxs-lookup"><span data-stu-id="64e54-196">For example, in US English:</span></span>

<span data-ttu-id="64e54-197">`Get-Date -Date "6/25/2019 12:30:22"` Returnerar tisdag, 25 juni 2019 12:30:22</span><span class="sxs-lookup"><span data-stu-id="64e54-197">`Get-Date -Date "6/25/2019 12:30:22"` returns Tuesday, June 25, 2019 12:30:22</span></span>

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

### <span data-ttu-id="64e54-198">– Dag</span><span class="sxs-lookup"><span data-stu-id="64e54-198">-Day</span></span>

<span data-ttu-id="64e54-199">Anger den dag i månaden som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-199">Specifies the day of the month that is displayed.</span></span> <span data-ttu-id="64e54-200">Ange ett värde från 1 till 31.</span><span class="sxs-lookup"><span data-stu-id="64e54-200">Enter a value from 1 to 31.</span></span>

<span data-ttu-id="64e54-201">Om det angivna värdet är större än antalet dagar i månaden lägger PowerShell till antalet dagar i månaden.</span><span class="sxs-lookup"><span data-stu-id="64e54-201">If the specified value is greater than the number of days in a month, PowerShell adds the number of days to the month.</span></span> <span data-ttu-id="64e54-202">Visar till exempel `Get-Date -Month 2 -Day 31` **3 mars**, inte **31 februari**.</span><span class="sxs-lookup"><span data-stu-id="64e54-202">For example, `Get-Date -Month 2 -Day 31` displays **March 3**, not **February 31**.</span></span>

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

### <span data-ttu-id="64e54-203">-DisplayHint</span><span class="sxs-lookup"><span data-stu-id="64e54-203">-DisplayHint</span></span>

<span data-ttu-id="64e54-204">Anger vilka element i datum och tid som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-204">Determines which elements of the date and time are displayed.</span></span>

<span data-ttu-id="64e54-205">De godkända värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="64e54-205">The accepted values are as follows:</span></span>

- <span data-ttu-id="64e54-206">**Datum**: visar endast datumet</span><span class="sxs-lookup"><span data-stu-id="64e54-206">**Date**: displays only the date</span></span>
- <span data-ttu-id="64e54-207">**Tid**: visar endast tiden</span><span class="sxs-lookup"><span data-stu-id="64e54-207">**Time**: displays only the time</span></span>
- <span data-ttu-id="64e54-208">**Datetime**: visar datum och tid</span><span class="sxs-lookup"><span data-stu-id="64e54-208">**DateTime**: displays the date and time</span></span>

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

### <span data-ttu-id="64e54-209">– Format</span><span class="sxs-lookup"><span data-stu-id="64e54-209">-Format</span></span>

<span data-ttu-id="64e54-210">Visar datum och tid i det Microsoft .NET Framework-format som anges av format specifikationen.</span><span class="sxs-lookup"><span data-stu-id="64e54-210">Displays the date and time in the Microsoft .NET Framework format indicated by the format specifier.</span></span>
<span data-ttu-id="64e54-211">**Format** parametern matar ut ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-211">The **Format** parameter outputs a **String** object.</span></span>

<span data-ttu-id="64e54-212">En lista över tillgängliga .NET-format specificerare finns i [anpassade datum-och tids format strängar](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span><span class="sxs-lookup"><span data-stu-id="64e54-212">For a list of available .NET format specifiers, see [Custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings?view=netframework-4.8).</span></span>

<span data-ttu-id="64e54-213">När **format** parametern används `Get-Date` får endast **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="64e54-213">When the **Format** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="64e54-214">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="64e54-214">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

<span data-ttu-id="64e54-215">Från och med PowerShell 5,0 kan du använda följande ytterligare format som värden för parametern **format** .</span><span class="sxs-lookup"><span data-stu-id="64e54-215">Starting in PowerShell 5.0, you can use the following additional formats as values for the **Format** parameter.</span></span>

- <span data-ttu-id="64e54-216">**Filedate**.</span><span class="sxs-lookup"><span data-stu-id="64e54-216">**FileDate**.</span></span> <span data-ttu-id="64e54-217">En fil eller Sök vägs vänlig representation av aktuellt datum i lokal tid.</span><span class="sxs-lookup"><span data-stu-id="64e54-217">A file or path-friendly representation of the current date in local time.</span></span> <span data-ttu-id="64e54-218">Formatet är `yyyyMMdd` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad och en dag med två siffror).</span><span class="sxs-lookup"><span data-stu-id="64e54-218">The format is `yyyyMMdd` (case-sensitive, using a 4-digit year, 2-digit month, and 2-digit day).</span></span> <span data-ttu-id="64e54-219">Exempel:</span><span class="sxs-lookup"><span data-stu-id="64e54-219">For example:</span></span>
  20190627.

- <span data-ttu-id="64e54-220">**FileDateUniversal**.</span><span class="sxs-lookup"><span data-stu-id="64e54-220">**FileDateUniversal**.</span></span> <span data-ttu-id="64e54-221">En fil eller Sök vägs vänlig representation av aktuellt datum i Universal Time (UTC).</span><span class="sxs-lookup"><span data-stu-id="64e54-221">A file or path-friendly representation of the current date in universal time (UTC).</span></span> <span data-ttu-id="64e54-222">Formatet är `yyyyMMddZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, en dag med en bokstav `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="64e54-222">The format is `yyyyMMddZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="64e54-223">Till exempel: 20190627Z.</span><span class="sxs-lookup"><span data-stu-id="64e54-223">For example: 20190627Z.</span></span>

- <span data-ttu-id="64e54-224">**FileDateTime**.</span><span class="sxs-lookup"><span data-stu-id="64e54-224">**FileDateTime**.</span></span> <span data-ttu-id="64e54-225">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="64e54-225">A file or path-friendly representation of the current date and time in local time, in 24-hour format.</span></span> <span data-ttu-id="64e54-226">Formatet är `yyyyMMddTHHmmssffff` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund och 4-siffriga millisekunder).</span><span class="sxs-lookup"><span data-stu-id="64e54-226">The format is `yyyyMMddTHHmmssffff` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, and 4-digit millisecond).</span></span> <span data-ttu-id="64e54-227">Till exempel: 20190627T0840107271.</span><span class="sxs-lookup"><span data-stu-id="64e54-227">For example: 20190627T0840107271.</span></span>

- <span data-ttu-id="64e54-228">**FileDateTimeUniversal**.</span><span class="sxs-lookup"><span data-stu-id="64e54-228">**FileDateTimeUniversal**.</span></span> <span data-ttu-id="64e54-229">En fil eller Sök vägs vänlig representation av aktuellt datum och tid i Universal Time (UTC) i 24-timmarsformat.</span><span class="sxs-lookup"><span data-stu-id="64e54-229">A file or path-friendly representation of the current date and time in universal time (UTC), in 24-hour format.</span></span> <span data-ttu-id="64e54-230">Formatet är `yyyyMMddTHHmmssffffZ` (Skift läges känsligt, med ett fyrsiffrigt år, 2-siffrig månad, 2-siffrig dag, bokstaven `T` som en tids avgränsare, 2-siffrig timme, 2-siffrig minut, 2-siffrig sekund, 4-siffriga millisekunder och bokstaven `Z` som UTC-indikator).</span><span class="sxs-lookup"><span data-stu-id="64e54-230">The format is `yyyyMMddTHHmmssffffZ` (case-sensitive, using a 4-digit year, 2-digit month, 2-digit day, the letter `T` as a time separator, 2-digit hour, 2-digit minute, 2-digit second, 4-digit millisecond, and the letter `Z` as the UTC indicator).</span></span> <span data-ttu-id="64e54-231">Till exempel: 20190627T1540500718Z.</span><span class="sxs-lookup"><span data-stu-id="64e54-231">For example: 20190627T1540500718Z.</span></span>

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

### <span data-ttu-id="64e54-232">– Timme</span><span class="sxs-lookup"><span data-stu-id="64e54-232">-Hour</span></span>

<span data-ttu-id="64e54-233">Anger den timme som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-233">Specifies the hour that is displayed.</span></span> <span data-ttu-id="64e54-234">Ange ett värde mellan 0 och 23.</span><span class="sxs-lookup"><span data-stu-id="64e54-234">Enter a value from 0 to 23.</span></span>

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

### <span data-ttu-id="64e54-235">– Millisekunde</span><span class="sxs-lookup"><span data-stu-id="64e54-235">-Millisecond</span></span>

<span data-ttu-id="64e54-236">Anger millisekunderna i datumet.</span><span class="sxs-lookup"><span data-stu-id="64e54-236">Specifies the milliseconds in the date.</span></span> <span data-ttu-id="64e54-237">Ange ett värde mellan 0 och 999.</span><span class="sxs-lookup"><span data-stu-id="64e54-237">Enter a value from 0 to 999.</span></span>

<span data-ttu-id="64e54-238">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="64e54-238">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="64e54-239">-Minut</span><span class="sxs-lookup"><span data-stu-id="64e54-239">-Minute</span></span>

<span data-ttu-id="64e54-240">Anger minuten som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-240">Specifies the minute that is displayed.</span></span> <span data-ttu-id="64e54-241">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="64e54-241">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="64e54-242">– Månad</span><span class="sxs-lookup"><span data-stu-id="64e54-242">-Month</span></span>

<span data-ttu-id="64e54-243">Anger den månad som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-243">Specifies the month that is displayed.</span></span> <span data-ttu-id="64e54-244">Ange ett värde mellan 1 och 12.</span><span class="sxs-lookup"><span data-stu-id="64e54-244">Enter a value from 1 to 12.</span></span>

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

### <span data-ttu-id="64e54-245">– Sekund</span><span class="sxs-lookup"><span data-stu-id="64e54-245">-Second</span></span>

<span data-ttu-id="64e54-246">Anger det andra som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-246">Specifies the second that is displayed.</span></span> <span data-ttu-id="64e54-247">Ange ett värde mellan 0 och 59.</span><span class="sxs-lookup"><span data-stu-id="64e54-247">Enter a value from 0 to 59.</span></span>

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

### <span data-ttu-id="64e54-248">-UFormat</span><span class="sxs-lookup"><span data-stu-id="64e54-248">-UFormat</span></span>

<span data-ttu-id="64e54-249">Visar datum och tid i UNIX-format.</span><span class="sxs-lookup"><span data-stu-id="64e54-249">Displays the date and time in UNIX format.</span></span> <span data-ttu-id="64e54-250">**UFormat** -parametern matar ut ett String-objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-250">The **UFormat** parameter outputs a string object.</span></span>

<span data-ttu-id="64e54-251">**UFormat** -specificerarna föregås av ett procent tecken ( `%` ), till exempel, `%m` , `%d` och `%Y` .</span><span class="sxs-lookup"><span data-stu-id="64e54-251">**UFormat** specifiers are preceded by a percent sign (`%`), for example, `%m`, `%d`, and `%Y`.</span></span> <span data-ttu-id="64e54-252">Avsnittet [anteckningar](#notes) innehåller en tabell med giltiga **UFormat-specificerare**.</span><span class="sxs-lookup"><span data-stu-id="64e54-252">The [Notes](#notes) section contains a table of valid **UFormat specifiers**.</span></span>

<span data-ttu-id="64e54-253">När parametern **UFormat** används `Get-Date` får bara **datetime** -objektets egenskaper som krävs för att visa datumet.</span><span class="sxs-lookup"><span data-stu-id="64e54-253">When the **UFormat** parameter is used, `Get-Date` only gets the **DateTime** object's properties necessary to display the date.</span></span> <span data-ttu-id="64e54-254">Därför kanske vissa av egenskaperna och metoderna för **datetime** -objekt inte är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="64e54-254">As a result, some of the properties and methods of **DateTime** objects might not be available.</span></span>

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

### <span data-ttu-id="64e54-255">-UnixTimeSeconds</span><span class="sxs-lookup"><span data-stu-id="64e54-255">-UnixTimeSeconds</span></span>

<span data-ttu-id="64e54-256">Datum och tid som representeras i sekunder sedan 1 januari 1970, 0:00:00.</span><span class="sxs-lookup"><span data-stu-id="64e54-256">Date and time represented in seconds since January 1, 1970, 0:00:00.</span></span>

<span data-ttu-id="64e54-257">Den här parametern introducerades i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="64e54-257">This parameter was introduced in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="64e54-258">-År</span><span class="sxs-lookup"><span data-stu-id="64e54-258">-Year</span></span>

<span data-ttu-id="64e54-259">Anger året som visas.</span><span class="sxs-lookup"><span data-stu-id="64e54-259">Specifies the year that is displayed.</span></span> <span data-ttu-id="64e54-260">Ange ett värde mellan 1 och 9999.</span><span class="sxs-lookup"><span data-stu-id="64e54-260">Enter a value from 1 to 9999.</span></span>

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

### <span data-ttu-id="64e54-261">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64e54-261">CommonParameters</span></span>

<span data-ttu-id="64e54-262">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="64e54-262">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64e54-263">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="64e54-263">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64e54-264">INDATA</span><span class="sxs-lookup"><span data-stu-id="64e54-264">INPUTS</span></span>

### <span data-ttu-id="64e54-265">Pipeline-inmatade</span><span class="sxs-lookup"><span data-stu-id="64e54-265">Pipeline input</span></span>

<span data-ttu-id="64e54-266">`Get-Date` accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="64e54-266">`Get-Date` accepts pipeline input.</span></span> <span data-ttu-id="64e54-267">Ett exempel är `Get-ChildItem | Get-Date`.</span><span class="sxs-lookup"><span data-stu-id="64e54-267">For example, `Get-ChildItem | Get-Date`.</span></span>

## <span data-ttu-id="64e54-268">UTDATA</span><span class="sxs-lookup"><span data-stu-id="64e54-268">OUTPUTS</span></span>

### <span data-ttu-id="64e54-269">System. DateTime eller system. String</span><span class="sxs-lookup"><span data-stu-id="64e54-269">System.DateTime or System.String</span></span>

<span data-ttu-id="64e54-270">`Get-Date` Returnerar ett **datetime** -objekt utom när **format** -och **UFormat** -parametrarna används.</span><span class="sxs-lookup"><span data-stu-id="64e54-270">`Get-Date` returns a **DateTime** object except when the **Format** and **UFormat** parameters are used.</span></span> <span data-ttu-id="64e54-271">**Format** -eller **UFormat** -parametrarna returnerar **sträng** objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-271">The **Format** or **UFormat** parameters return **String** objects.</span></span>

<span data-ttu-id="64e54-272">När ett **datetime** -objekt skickas ned pipelinen till en-cmdlet, till exempel `Add-Content` som förväntar sig sträng Indatatyp, konverterar PowerShell objektet till ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-272">When a **DateTime** object is sent down the pipeline to a cmdlet such as `Add-Content` that expects string input, PowerShell converts the object to a **String** object.</span></span>

<span data-ttu-id="64e54-273">Metoden `(Get-Date).ToString()` konverterar ett **datetime** -objekt till **ett String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="64e54-273">The method `(Get-Date).ToString()` converts a **DateTime** object a **String** object.</span></span>

<span data-ttu-id="64e54-274">Om du vill visa ett objekts egenskaper och metoder skickar du objektet nedåt i pipeline till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="64e54-274">To display an object's properties and methods, send the object down the pipeline to `Get-Member`.</span></span>
<span data-ttu-id="64e54-275">Ett exempel är `Get-Date | Get-Member`.</span><span class="sxs-lookup"><span data-stu-id="64e54-275">For example, `Get-Date | Get-Member`.</span></span>

## <span data-ttu-id="64e54-276">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="64e54-276">NOTES</span></span>

<span data-ttu-id="64e54-277">**Datetime** -objekt är i långa och långa format för system språket.</span><span class="sxs-lookup"><span data-stu-id="64e54-277">**DateTime** objects are in long-date and long-time formats for the system locale.</span></span>

<span data-ttu-id="64e54-278">Giltiga **UFormat-specificerare** visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="64e54-278">The valid **UFormat specifiers** are displayed in the following table:</span></span>

| <span data-ttu-id="64e54-279">Format specificerare</span><span class="sxs-lookup"><span data-stu-id="64e54-279">Format specifier</span></span> |                                 <span data-ttu-id="64e54-280">Betydelse</span><span class="sxs-lookup"><span data-stu-id="64e54-280">Meaning</span></span>                     |         <span data-ttu-id="64e54-281">Exempel</span><span class="sxs-lookup"><span data-stu-id="64e54-281">Example</span></span>          |
| ---- | ----------------------------------------------------------------------- | ------------------------ |
| `%A` | <span data-ttu-id="64e54-282">Veckodag-fullständigt namn</span><span class="sxs-lookup"><span data-stu-id="64e54-282">Day of the week - full name</span></span>                                             | <span data-ttu-id="64e54-283">Måndag</span><span class="sxs-lookup"><span data-stu-id="64e54-283">Monday</span></span>                   |
| `%a` | <span data-ttu-id="64e54-284">Veckodag-förkortat namn</span><span class="sxs-lookup"><span data-stu-id="64e54-284">Day of the week - abbreviated name</span></span>                                      | <span data-ttu-id="64e54-285">Mån</span><span class="sxs-lookup"><span data-stu-id="64e54-285">Mon</span></span>                      |
| `%B` | <span data-ttu-id="64e54-286">Månads namn – fullständig</span><span class="sxs-lookup"><span data-stu-id="64e54-286">Month name - full</span></span>                                                       | <span data-ttu-id="64e54-287">Januari</span><span class="sxs-lookup"><span data-stu-id="64e54-287">January</span></span>                  |
| `%b` | <span data-ttu-id="64e54-288">Månads namn – förkortat</span><span class="sxs-lookup"><span data-stu-id="64e54-288">Month name - abbreviated</span></span>                                                | <span data-ttu-id="64e54-289">Jan</span><span class="sxs-lookup"><span data-stu-id="64e54-289">Jan</span></span>                      |
| `%C` | <span data-ttu-id="64e54-290">1900</span><span class="sxs-lookup"><span data-stu-id="64e54-290">Century</span></span>                                                                 | <span data-ttu-id="64e54-291">20 för 2019</span><span class="sxs-lookup"><span data-stu-id="64e54-291">20 for 2019</span></span>              |
| `%c` | <span data-ttu-id="64e54-292">Datum och tid – förkortat</span><span class="sxs-lookup"><span data-stu-id="64e54-292">Date and time - abbreviated</span></span>                                             | <span data-ttu-id="64e54-293">Tor Jun 27 08:44:18 2019</span><span class="sxs-lookup"><span data-stu-id="64e54-293">Thu Jun 27 08:44:18 2019</span></span> |
| `%D` | <span data-ttu-id="64e54-294">Datum i formatet åååå-mm-dd</span><span class="sxs-lookup"><span data-stu-id="64e54-294">Date in mm/dd/yy format</span></span>                                                 | <span data-ttu-id="64e54-295">06/27/19</span><span class="sxs-lookup"><span data-stu-id="64e54-295">06/27/19</span></span>                 |
| `%d` | <span data-ttu-id="64e54-296">Dag i månaden – 2 siffror</span><span class="sxs-lookup"><span data-stu-id="64e54-296">Day of the month - 2 digits</span></span>                                             | <span data-ttu-id="64e54-297">05</span><span class="sxs-lookup"><span data-stu-id="64e54-297">05</span></span>                       |
| `%e` | <span data-ttu-id="64e54-298">Dag i månaden – föregås av ett blank steg om bara en siffra</span><span class="sxs-lookup"><span data-stu-id="64e54-298">Day of the month - preceded by a space if only a single digit</span></span>           | <span data-ttu-id="64e54-299">\<space\>5</span><span class="sxs-lookup"><span data-stu-id="64e54-299">\<space\>5</span></span>               |
| `%F` | <span data-ttu-id="64e54-300">Datum i åååå-mm-dd-format, motsvarar% Y-% m-% d (ISO 8601-datum format)</span><span class="sxs-lookup"><span data-stu-id="64e54-300">Date in YYYY-mm-dd format, equal to %Y-%m-%d (the ISO 8601 date format)</span></span> | <span data-ttu-id="64e54-301">2019-06-27</span><span class="sxs-lookup"><span data-stu-id="64e54-301">2019-06-27</span></span>               |
| `%G` | <span data-ttu-id="64e54-302">Samma som "Y"</span><span class="sxs-lookup"><span data-stu-id="64e54-302">Same as 'Y'</span></span>                                                             |                          |
| `%g` | <span data-ttu-id="64e54-303">Samma som "y"</span><span class="sxs-lookup"><span data-stu-id="64e54-303">Same as 'y'</span></span>                                                             |                          |
| `%H` | <span data-ttu-id="64e54-304">Timme i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="64e54-304">Hour in 24-hour format</span></span>                                                  | <span data-ttu-id="64e54-305">17</span><span class="sxs-lookup"><span data-stu-id="64e54-305">17</span></span>                       |
| `%h` | <span data-ttu-id="64e54-306">Samma som "b"</span><span class="sxs-lookup"><span data-stu-id="64e54-306">Same as 'b'</span></span>                                                             |                          |
| `%I` | <span data-ttu-id="64e54-307">Timme i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="64e54-307">Hour in 12-hour format</span></span>                                                  | <span data-ttu-id="64e54-308">05</span><span class="sxs-lookup"><span data-stu-id="64e54-308">05</span></span>                       |
| `%j` | <span data-ttu-id="64e54-309">Dag på året</span><span class="sxs-lookup"><span data-stu-id="64e54-309">Day of the year</span></span>                                                         | <span data-ttu-id="64e54-310">1-366</span><span class="sxs-lookup"><span data-stu-id="64e54-310">1-366</span></span>                    |
| `%k` | <span data-ttu-id="64e54-311">Samma som "H"</span><span class="sxs-lookup"><span data-stu-id="64e54-311">Same as 'H'</span></span>                                                             |                          |
| `%l` | <span data-ttu-id="64e54-312">Samma som "I" (versal I)</span><span class="sxs-lookup"><span data-stu-id="64e54-312">Same as 'I' (Upper-case I)</span></span>                                              | <span data-ttu-id="64e54-313">05</span><span class="sxs-lookup"><span data-stu-id="64e54-313">05</span></span>                       |
| `%M` | <span data-ttu-id="64e54-314">Minuter</span><span class="sxs-lookup"><span data-stu-id="64e54-314">Minutes</span></span>                                                                 | <span data-ttu-id="64e54-315">35</span><span class="sxs-lookup"><span data-stu-id="64e54-315">35</span></span>                       |
| `%m` | <span data-ttu-id="64e54-316">Månadsnummer</span><span class="sxs-lookup"><span data-stu-id="64e54-316">Month number</span></span>                                                            | <span data-ttu-id="64e54-317">06</span><span class="sxs-lookup"><span data-stu-id="64e54-317">06</span></span>                       |
| `%n` | <span data-ttu-id="64e54-318">rad matnings tecknet</span><span class="sxs-lookup"><span data-stu-id="64e54-318">newline character</span></span>                                                       |                          |
| `%p` | <span data-ttu-id="64e54-319">FM eller EM</span><span class="sxs-lookup"><span data-stu-id="64e54-319">AM or PM</span></span>                                                                |                          |
| `%R` | <span data-ttu-id="64e54-320">Tid i 24-timmarsformat – inga sekunder</span><span class="sxs-lookup"><span data-stu-id="64e54-320">Time in 24-hour format -no seconds</span></span>                                      | <span data-ttu-id="64e54-321">17:45</span><span class="sxs-lookup"><span data-stu-id="64e54-321">17:45</span></span>                    |
| `%r` | <span data-ttu-id="64e54-322">Tid i 12-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="64e54-322">Time in 12-hour format</span></span>                                                  | <span data-ttu-id="64e54-323">09:15:36 AM</span><span class="sxs-lookup"><span data-stu-id="64e54-323">09:15:36 AM</span></span>              |
| `%S` | <span data-ttu-id="64e54-324">Sekunder</span><span class="sxs-lookup"><span data-stu-id="64e54-324">Seconds</span></span>                                                                 | <span data-ttu-id="64e54-325">05</span><span class="sxs-lookup"><span data-stu-id="64e54-325">05</span></span>                       |
| `%s` | <span data-ttu-id="64e54-326">Förflutna sekunder sedan den 1 januari 1970 00:00:00</span><span class="sxs-lookup"><span data-stu-id="64e54-326">Seconds elapsed since January 1, 1970 00:00:00</span></span>                          | <span data-ttu-id="64e54-327">1150451174</span><span class="sxs-lookup"><span data-stu-id="64e54-327">1150451174</span></span>               |
| `%t` | <span data-ttu-id="64e54-328">Vågrätt tabbtecken</span><span class="sxs-lookup"><span data-stu-id="64e54-328">Horizontal tab character</span></span>                                                |                          |
| `%T` | <span data-ttu-id="64e54-329">Tid i 24-timmarsformat</span><span class="sxs-lookup"><span data-stu-id="64e54-329">Time in 24-hour format</span></span>                                                  | <span data-ttu-id="64e54-330">17:45:52</span><span class="sxs-lookup"><span data-stu-id="64e54-330">17:45:52</span></span>                 |
| `%U` | <span data-ttu-id="64e54-331">Samma som "W"</span><span class="sxs-lookup"><span data-stu-id="64e54-331">Same as 'W'</span></span>                                                             |                          |
| `%u` | <span data-ttu-id="64e54-332">Veckodag-nummer</span><span class="sxs-lookup"><span data-stu-id="64e54-332">Day of the week - number</span></span>                                                | <span data-ttu-id="64e54-333">Söndag = 0</span><span class="sxs-lookup"><span data-stu-id="64e54-333">Sunday = 0</span></span>               |
| `%V` | <span data-ttu-id="64e54-334">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="64e54-334">Week of the year</span></span>                                                        | <span data-ttu-id="64e54-335">01-53</span><span class="sxs-lookup"><span data-stu-id="64e54-335">01-53</span></span>                    |
| `%w` | <span data-ttu-id="64e54-336">Samma som u</span><span class="sxs-lookup"><span data-stu-id="64e54-336">Same as 'u'</span></span>                                                             |                          |
| `%W` | <span data-ttu-id="64e54-337">Vecka på året</span><span class="sxs-lookup"><span data-stu-id="64e54-337">Week of the year</span></span>                                                        | <span data-ttu-id="64e54-338">00-52</span><span class="sxs-lookup"><span data-stu-id="64e54-338">00-52</span></span>                    |
| `%X` | <span data-ttu-id="64e54-339">Samma som t '</span><span class="sxs-lookup"><span data-stu-id="64e54-339">Same as 'T'</span></span>                                                             |                          |
| `%x` | <span data-ttu-id="64e54-340">Datum i standardformat för språkvariant</span><span class="sxs-lookup"><span data-stu-id="64e54-340">Date in standard format for locale</span></span>                                      | <span data-ttu-id="64e54-341">06/27/19 för engelska – USA</span><span class="sxs-lookup"><span data-stu-id="64e54-341">06/27/19 for English-US</span></span>  |
| `%Y` | <span data-ttu-id="64e54-342">År i 4-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="64e54-342">Year in 4-digit format</span></span>                                                  | <span data-ttu-id="64e54-343">2019</span><span class="sxs-lookup"><span data-stu-id="64e54-343">2019</span></span>                     |
| `%y` | <span data-ttu-id="64e54-344">År i 2-siffrigt format</span><span class="sxs-lookup"><span data-stu-id="64e54-344">Year in 2-digit format</span></span>                                                  | <span data-ttu-id="64e54-345">19</span><span class="sxs-lookup"><span data-stu-id="64e54-345">19</span></span>                       |
| `%Z` | <span data-ttu-id="64e54-346">Tids zons förskjutning från Universal Time Coordinator (UTC)</span><span class="sxs-lookup"><span data-stu-id="64e54-346">Time zone offset from Universal Time Coordinate (UTC)</span></span>                   | <span data-ttu-id="64e54-347">-07</span><span class="sxs-lookup"><span data-stu-id="64e54-347">-07</span></span>                      |

## <span data-ttu-id="64e54-348">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="64e54-348">RELATED LINKS</span></span>

[<span data-ttu-id="64e54-349">-Objekt</span><span class="sxs-lookup"><span data-stu-id="64e54-349">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="64e54-350">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="64e54-350">Get-Culture</span></span>](Get-Culture.md)

[<span data-ttu-id="64e54-351">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="64e54-351">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="64e54-352">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="64e54-352">New-Item</span></span>](../Microsoft.PowerShell.Management/New-Item.md)

[<span data-ttu-id="64e54-353">New-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="64e54-353">New-TimeSpan</span></span>](New-TimeSpan.md)

[<span data-ttu-id="64e54-354">Ange datum</span><span class="sxs-lookup"><span data-stu-id="64e54-354">Set-Date</span></span>](Set-Date.md)
