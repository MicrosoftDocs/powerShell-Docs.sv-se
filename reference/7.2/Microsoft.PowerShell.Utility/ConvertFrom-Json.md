---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 525b123d48b0f88ca3eef85a3f95cc303a981ca3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709864"
---
# <span data-ttu-id="8fb86-102">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="8fb86-102">ConvertFrom-Json</span></span>

## <span data-ttu-id="8fb86-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8fb86-103">SYNOPSIS</span></span>
<span data-ttu-id="8fb86-104">Konverterar en JSON-formaterad sträng till ett anpassat objekt eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="8fb86-104">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="8fb86-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8fb86-105">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="8fb86-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8fb86-106">DESCRIPTION</span></span>

<span data-ttu-id="8fb86-107">`ConvertFrom-Json`Cmdleten konverterar en JavaScript Object Notation (JSON) formaterad sträng till ett anpassat **PSCustomObject** -objekt som har en egenskap för varje fält i JSON-strängen.</span><span class="sxs-lookup"><span data-stu-id="8fb86-107">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="8fb86-108">JSON används ofta av webbplatser för att tillhandahålla en text representation av objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-108">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="8fb86-109">JSON-standarden förhindrar inte användning som är förbjuden med en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="8fb86-109">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="8fb86-110">Om JSON-strängen t. ex. innehåller dubbla nycklar används bara den sista nyckeln av denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8fb86-110">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="8fb86-111">Se andra exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="8fb86-111">See other examples below.</span></span>

<span data-ttu-id="8fb86-112">Använd cmdleten om du vill generera en JSON-sträng från ett objekt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-112">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="8fb86-113">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8fb86-113">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="8fb86-114">Från och med PowerShell 6 stöder denna cmdlet JSON med kommentarer.</span><span class="sxs-lookup"><span data-stu-id="8fb86-114">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="8fb86-115">Accepterade kommentarer startas med två snedstreck ( `//` ).</span><span class="sxs-lookup"><span data-stu-id="8fb86-115">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="8fb86-116">Kommentaren visas inte i data och kan skrivas i filen utan att skada data eller orsaka ett fel som det gjorde i PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="8fb86-116">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="8fb86-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8fb86-117">EXAMPLES</span></span>

### <span data-ttu-id="8fb86-118">Exempel 1: konvertera ett DateTime-objekt till ett JSON-objekt</span><span class="sxs-lookup"><span data-stu-id="8fb86-118">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="8fb86-119">Detta kommando använder `ConvertTo-Json` `ConvertFrom-Json` cmdletarna och för att konvertera ett **datetime** -objekt från `Get-Date` cmdleten till ett JSON-objekt till en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="8fb86-119">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="8fb86-120">Exemplet använder `Select-Object` cmdleten för att hämta alla egenskaper för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="8fb86-120">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="8fb86-121">Den använder `ConvertTo-Json` cmdleten för att konvertera **datetime** -objektet till en sträng FORMATERAD som ett JSON-objekt och `ConvertFrom-Json` cmdleten för att konvertera den JSON-formaterade strängen till ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-121">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="8fb86-122">Exempel 2: Hämta JSON-strängar från en webb tjänst och konvertera dem till PowerShell-objekt</span><span class="sxs-lookup"><span data-stu-id="8fb86-122">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="8fb86-123">Detta kommando använder `Invoke-WebRequest` cmdleten för att hämta JSON-strängar från en webb tjänst och använder sedan `ConvertFrom-Json` cmdleten för att konvertera JSON-innehåll till objekt som kan hanteras i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8fb86-123">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="8fb86-124">Du kan också använda `Invoke-RestMethod` cmdleten, som automatiskt KONVERTERAR JSON-innehåll till objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-124">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="8fb86-125">Exempel 3: konvertera en JSON-sträng till ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="8fb86-125">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="8fb86-126">Det här exemplet visar hur du använder `ConvertFrom-Json` cmdleten för att konvertera en JSON-fil till ett anpassat PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-126">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="8fb86-127">Kommandot använder Get-Content cmdlet för att hämta strängarna i en JSON-fil.</span><span class="sxs-lookup"><span data-stu-id="8fb86-127">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="8fb86-128">Sedan använder den pipeline-operatorn för att skicka den avgränsade strängen till `ConvertFrom-Json` cmdleten, som konverterar den till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-128">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="8fb86-129">Exempel 4: konvertera en JSON-sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="8fb86-129">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="8fb86-130">Det här kommandot visar ett exempel där `-AsHashtable` växeln kan kringgå begränsningar för kommandot.</span><span class="sxs-lookup"><span data-stu-id="8fb86-130">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="8fb86-131">JSON-strängen innehåller två nyckel värde par med nycklar som bara skiljer sig i skift läge.</span><span class="sxs-lookup"><span data-stu-id="8fb86-131">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="8fb86-132">Utan växeln skulle kommandot ha utlöst ett fel.</span><span class="sxs-lookup"><span data-stu-id="8fb86-132">Without the switch, the command would have thrown an error.</span></span>

### <span data-ttu-id="8fb86-133">Exempel 5: tur och retur i en enda element mat ris</span><span class="sxs-lookup"><span data-stu-id="8fb86-133">Example 5: Round-trip a single element array</span></span>

<span data-ttu-id="8fb86-134">Det här kommandot visar ett exempel där `-NoEnumerate` växeln används för att runda av en JSON-matris med ett enda element.</span><span class="sxs-lookup"><span data-stu-id="8fb86-134">This command shows an example where the `-NoEnumerate` switch is used to round-trip a single element JSON array.</span></span>

```powershell
Write-Output "With -NoEnumerate: $('[1]' | ConvertFrom-Json -NoEnumerate | ConvertTo-Json -Compress)"
Write-Output "Without -NoEnumerate: $('[1]' | ConvertFrom-Json | ConvertTo-Json -Compress)"
```

```Output
With -NoEnumerate: [1]
Without -NoEnumerate: 1
```

<span data-ttu-id="8fb86-135">JSON-strängen innehåller en matris med ett enda element.</span><span class="sxs-lookup"><span data-stu-id="8fb86-135">The JSON string contains an array with a single element.</span></span> <span data-ttu-id="8fb86-136">Utan växeln konverterar JSON till en PSObject och konverterar sedan tillbaka den med `ConvertTo-Json` kommandot till ett enda heltal.</span><span class="sxs-lookup"><span data-stu-id="8fb86-136">Without the switch, converting the JSON to a PSObject and then converting it back with the `ConvertTo-Json` command results in a single integer.</span></span>

## <span data-ttu-id="8fb86-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8fb86-137">PARAMETERS</span></span>

### <span data-ttu-id="8fb86-138">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="8fb86-138">-AsHashtable</span></span>

<span data-ttu-id="8fb86-139">Konverterar JSON till ett hash-tabell-objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-139">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="8fb86-140">Den här växeln introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="8fb86-140">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="8fb86-141">Det finns flera scenarier där den kan kringgå vissa begränsningar för `ConvertFrom-Json` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8fb86-141">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="8fb86-142">Om JSON innehåller en lista med nycklar som bara skiljer sig i skift läge.</span><span class="sxs-lookup"><span data-stu-id="8fb86-142">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="8fb86-143">Utan växeln visas nycklarna som identiska nycklar och det är därför bara den sista som används.</span><span class="sxs-lookup"><span data-stu-id="8fb86-143">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="8fb86-144">Om JSON innehåller en nyckel som är en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="8fb86-144">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="8fb86-145">Utan växeln skulle cmdleten utlösa ett fel eftersom en inte `PSCustomObject` tillåter att en hash-tabell gör det.</span><span class="sxs-lookup"><span data-stu-id="8fb86-145">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="8fb86-146">Ett exempel på användnings fall där detta kan inträffa är `project.lock.json` filer.</span><span class="sxs-lookup"><span data-stu-id="8fb86-146">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="8fb86-147">Hash-tabeller kan bearbetas snabbare för vissa data strukturer.</span><span class="sxs-lookup"><span data-stu-id="8fb86-147">Hash tables can be processed faster for certain data structures.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fb86-148">-Djup</span><span class="sxs-lookup"><span data-stu-id="8fb86-148">-Depth</span></span>

<span data-ttu-id="8fb86-149">Hämtar eller anger det maximala djup som JSON-indatatypen får ha.</span><span class="sxs-lookup"><span data-stu-id="8fb86-149">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="8fb86-150">Som standard är det 1024.</span><span class="sxs-lookup"><span data-stu-id="8fb86-150">By default, it is 1024.</span></span>

<span data-ttu-id="8fb86-151">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="8fb86-151">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="8fb86-152">– InputObject</span><span class="sxs-lookup"><span data-stu-id="8fb86-152">-InputObject</span></span>

<span data-ttu-id="8fb86-153">Anger JSON-strängarna som ska konverteras till JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="8fb86-153">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="8fb86-154">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="8fb86-154">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="8fb86-155">Du kan också skicka en sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-155">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="8fb86-156">Parametern **InputObject** är obligatorisk, men dess värde kan vara en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="8fb86-156">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="8fb86-157">När indata-objektet är en tom sträng `ConvertFrom-Json` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="8fb86-157">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="8fb86-158">Värdet för **InputObject** får inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-158">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8fb86-159">-Noenumeration</span><span class="sxs-lookup"><span data-stu-id="8fb86-159">-NoEnumerate</span></span>

<span data-ttu-id="8fb86-160">Anger att utdata inte räknas upp.</span><span class="sxs-lookup"><span data-stu-id="8fb86-160">Specifies that output is not enumerated.</span></span>

<span data-ttu-id="8fb86-161">Om du anger den här parametern skickas matriser som ett enda objekt i stället för att varje element skickas separat.</span><span class="sxs-lookup"><span data-stu-id="8fb86-161">Setting this parameter causes arrays to be sent as a single object instead of sending every element separately.</span></span> <span data-ttu-id="8fb86-162">Detta garanterar att JSON kan vara Round-utlöst via `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-162">This guarantees that JSON can be round-tripped via `ConvertTo-Json`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8fb86-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8fb86-163">CommonParameters</span></span>

<span data-ttu-id="8fb86-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8fb86-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8fb86-165">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8fb86-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8fb86-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="8fb86-166">INPUTS</span></span>

### <span data-ttu-id="8fb86-167">System. String</span><span class="sxs-lookup"><span data-stu-id="8fb86-167">System.String</span></span>

<span data-ttu-id="8fb86-168">Du kan skicka vidare en JSON-sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-168">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="8fb86-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8fb86-169">OUTPUTS</span></span>

### <span data-ttu-id="8fb86-170">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="8fb86-170">PSCustomObject</span></span>

### <span data-ttu-id="8fb86-171">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="8fb86-171">System.Collections.Hashtable</span></span>

## <span data-ttu-id="8fb86-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8fb86-172">NOTES</span></span>

<span data-ttu-id="8fb86-173">Denna cmdlet implementeras med hjälp av [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="8fb86-173">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="8fb86-174">Från och med PowerShell 6 `ConvertTo-Json` försöker konvertera strängar som formaterats som tidsstämplar till **datetime** -värden.</span><span class="sxs-lookup"><span data-stu-id="8fb86-174">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="8fb86-175">Det konverterade värdet är en `[datetime]` instans med en `Kind` egenskaps uppsättning som följer:</span><span class="sxs-lookup"><span data-stu-id="8fb86-175">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="8fb86-176">`Unspecified`, om det inte finns någon tids zons information i Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="8fb86-176">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="8fb86-177">`Utc`, om tids zons informationen är ett avslutande `Z` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-177">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="8fb86-178">`Local`, om tids zons informationen anges som en avslutande UTC- _förskjutning_ som `+02:00` .</span><span class="sxs-lookup"><span data-stu-id="8fb86-178">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="8fb86-179">Förskjutningen konverteras korrekt till anroparens konfigurerade tidszon.</span><span class="sxs-lookup"><span data-stu-id="8fb86-179">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="8fb86-180">Standardformateringen för utdata indikerar inte den ursprungliga tids zons förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="8fb86-180">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="8fb86-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8fb86-181">RELATED LINKS</span></span>

<span data-ttu-id="8fb86-182">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="8fb86-182">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="8fb86-183">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="8fb86-183">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="8fb86-184">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="8fb86-184">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="8fb86-185">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="8fb86-185">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
