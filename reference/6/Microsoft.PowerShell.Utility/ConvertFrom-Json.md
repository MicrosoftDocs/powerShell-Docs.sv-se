---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 0cf439651d3382ce5abf3e5de4812df92cb8492d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389852"
---
# <span data-ttu-id="24ebc-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="24ebc-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="24ebc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="24ebc-104">SYNOPSIS</span></span>
<span data-ttu-id="24ebc-105">Konverterar en JSON-formaterad sträng till ett anpassat objekt eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="24ebc-105">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="24ebc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="24ebc-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="24ebc-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="24ebc-107">DESCRIPTION</span></span>

<span data-ttu-id="24ebc-108">`ConvertFrom-Json`Cmdleten konverterar en JavaScript Object Notation (JSON) formaterad sträng till ett anpassat **PSCustomObject** -objekt som har en egenskap för varje fält i JSON-strängen.</span><span class="sxs-lookup"><span data-stu-id="24ebc-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="24ebc-109">JSON används ofta av webbplatser för att tillhandahålla en text representation av objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="24ebc-110">JSON-standarden förhindrar inte användning som är förbjuden med en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="24ebc-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="24ebc-111">Om JSON-strängen t. ex. innehåller dubbla nycklar används bara den sista nyckeln av denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="24ebc-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="24ebc-112">Se andra exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="24ebc-112">See other examples below.</span></span>

<span data-ttu-id="24ebc-113">Använd cmdleten om du vill generera en JSON-sträng från ett objekt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="24ebc-114">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="24ebc-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="24ebc-115">Från och med PowerShell 6 stöder denna cmdlet JSON med kommentarer.</span><span class="sxs-lookup"><span data-stu-id="24ebc-115">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="24ebc-116">Accepterade kommentarer startas med två snedstreck ( `//` ).</span><span class="sxs-lookup"><span data-stu-id="24ebc-116">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="24ebc-117">Kommentaren visas inte i data och kan skrivas i filen utan att skada data eller orsaka ett fel som det gjorde i PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="24ebc-117">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="24ebc-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="24ebc-118">EXAMPLES</span></span>

### <span data-ttu-id="24ebc-119">Exempel 1: konvertera ett DateTime-objekt till ett JSON-objekt</span><span class="sxs-lookup"><span data-stu-id="24ebc-119">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="24ebc-120">Detta kommando använder `ConvertTo-Json` `ConvertFrom-Json` cmdletarna och för att konvertera ett **datetime** -objekt från `Get-Date` cmdleten till ett JSON-objekt till en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="24ebc-120">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="24ebc-121">Exemplet använder `Select-Object` cmdleten för att hämta alla egenskaper för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="24ebc-121">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="24ebc-122">Den använder `ConvertTo-Json` cmdleten för att konvertera **datetime** -objektet till en sträng FORMATERAD som ett JSON-objekt och `ConvertFrom-Json` cmdleten för att konvertera den JSON-formaterade strängen till ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-122">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="24ebc-123">Exempel 2: Hämta JSON-strängar från en webb tjänst och konvertera dem till PowerShell-objekt</span><span class="sxs-lookup"><span data-stu-id="24ebc-123">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="24ebc-124">Detta kommando använder `Invoke-WebRequest` cmdleten för att hämta JSON-strängar från en webb tjänst och använder sedan `ConvertFrom-Json` cmdleten för att konvertera JSON-innehåll till objekt som kan hanteras i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24ebc-124">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="24ebc-125">Du kan också använda `Invoke-RestMethod` cmdleten, som automatiskt KONVERTERAR JSON-innehåll till objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-125">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="24ebc-126">Exempel 3: konvertera en JSON-sträng till ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="24ebc-126">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="24ebc-127">Det här exemplet visar hur du använder `ConvertFrom-Json` cmdleten för att konvertera en JSON-fil till ett anpassat PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-127">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="24ebc-128">Kommandot använder Get-Content cmdlet för att hämta strängarna i en JSON-fil.</span><span class="sxs-lookup"><span data-stu-id="24ebc-128">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="24ebc-129">Sedan använder den pipeline-operatorn för att skicka den avgränsade strängen till `ConvertFrom-Json` cmdleten, som konverterar den till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-129">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="24ebc-130">Exempel 4: konvertera en JSON-sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="24ebc-130">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="24ebc-131">Det här kommandot visar ett exempel där `-AsHashtable` växeln kan kringgå begränsningar för kommandot.</span><span class="sxs-lookup"><span data-stu-id="24ebc-131">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="24ebc-132">JSON-strängen innehåller två nyckel värde par med nycklar som bara skiljer sig i skift läge.</span><span class="sxs-lookup"><span data-stu-id="24ebc-132">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="24ebc-133">Utan växeln skulle kommandot ha utlöst ett fel.</span><span class="sxs-lookup"><span data-stu-id="24ebc-133">Without the switch, the command would have thrown an error.</span></span>

## <span data-ttu-id="24ebc-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="24ebc-134">PARAMETERS</span></span>

### <span data-ttu-id="24ebc-135">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="24ebc-135">-AsHashtable</span></span>

<span data-ttu-id="24ebc-136">Konverterar JSON till ett hash-tabell-objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-136">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="24ebc-137">Den här växeln introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="24ebc-137">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="24ebc-138">Det finns flera scenarier där den kan kringgå vissa begränsningar för `ConvertFrom-Json` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="24ebc-138">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="24ebc-139">Om JSON innehåller en lista med nycklar som bara skiljer sig i skift läge.</span><span class="sxs-lookup"><span data-stu-id="24ebc-139">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="24ebc-140">Utan växeln visas nycklarna som identiska nycklar och det är därför bara den sista som används.</span><span class="sxs-lookup"><span data-stu-id="24ebc-140">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="24ebc-141">Om JSON innehåller en nyckel som är en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="24ebc-141">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="24ebc-142">Utan växeln skulle cmdleten utlösa ett fel eftersom en inte `PSCustomObject` tillåter att en hash-tabell gör det.</span><span class="sxs-lookup"><span data-stu-id="24ebc-142">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="24ebc-143">Ett exempel på användnings fall där detta kan inträffa är `project.lock.json` filer.</span><span class="sxs-lookup"><span data-stu-id="24ebc-143">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="24ebc-144">Hash-tabeller kan bearbetas snabbare för vissa data strukturer.</span><span class="sxs-lookup"><span data-stu-id="24ebc-144">Hash tables can be processed faster for certain data structures.</span></span>

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

### <span data-ttu-id="24ebc-145">-Djup</span><span class="sxs-lookup"><span data-stu-id="24ebc-145">-Depth</span></span>

<span data-ttu-id="24ebc-146">Hämtar eller anger det maximala djup som JSON-indatatypen får ha.</span><span class="sxs-lookup"><span data-stu-id="24ebc-146">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="24ebc-147">Som standard är det 1024.</span><span class="sxs-lookup"><span data-stu-id="24ebc-147">By default, it is 1024.</span></span>

<span data-ttu-id="24ebc-148">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="24ebc-148">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="24ebc-149">– InputObject</span><span class="sxs-lookup"><span data-stu-id="24ebc-149">-InputObject</span></span>

<span data-ttu-id="24ebc-150">Anger JSON-strängarna som ska konverteras till JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="24ebc-150">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="24ebc-151">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="24ebc-151">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="24ebc-152">Du kan också skicka en sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-152">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="24ebc-153">Parametern **InputObject** är obligatorisk, men dess värde kan vara en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="24ebc-153">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="24ebc-154">När indata-objektet är en tom sträng `ConvertFrom-Json` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="24ebc-154">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="24ebc-155">Värdet för **InputObject** får inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-155">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="24ebc-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="24ebc-156">CommonParameters</span></span>

<span data-ttu-id="24ebc-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="24ebc-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="24ebc-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="24ebc-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="24ebc-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="24ebc-159">INPUTS</span></span>

### <span data-ttu-id="24ebc-160">System. String</span><span class="sxs-lookup"><span data-stu-id="24ebc-160">System.String</span></span>

<span data-ttu-id="24ebc-161">Du kan skicka vidare en JSON-sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-161">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="24ebc-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="24ebc-162">OUTPUTS</span></span>

### <span data-ttu-id="24ebc-163">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="24ebc-163">PSCustomObject</span></span>

### <span data-ttu-id="24ebc-164">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="24ebc-164">System.Collections.Hashtable</span></span>

## <span data-ttu-id="24ebc-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="24ebc-165">NOTES</span></span>

<span data-ttu-id="24ebc-166">Denna cmdlet implementeras med hjälp av [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="24ebc-166">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="24ebc-167">Från och med PowerShell 6 `ConvertTo-Json` försöker konvertera strängar som formaterats som tidsstämplar till **datetime** -värden.</span><span class="sxs-lookup"><span data-stu-id="24ebc-167">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="24ebc-168">Det konverterade värdet är en `[datetime]` instans med en `Kind` egenskaps uppsättning som följer:</span><span class="sxs-lookup"><span data-stu-id="24ebc-168">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="24ebc-169">`Unspecified`, om det inte finns någon tids zons information i Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="24ebc-169">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="24ebc-170">`Utc`, om tids zons informationen är ett avslutande `Z` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-170">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="24ebc-171">`Local`, om tids zons informationen anges som en avslutande UTC- _förskjutning_ som `+02:00` .</span><span class="sxs-lookup"><span data-stu-id="24ebc-171">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="24ebc-172">Förskjutningen konverteras korrekt till anroparens konfigurerade tidszon.</span><span class="sxs-lookup"><span data-stu-id="24ebc-172">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="24ebc-173">Standardformateringen för utdata indikerar inte den ursprungliga tids zons förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="24ebc-173">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="24ebc-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="24ebc-174">RELATED LINKS</span></span>

<span data-ttu-id="24ebc-175">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="24ebc-175">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="24ebc-176">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="24ebc-176">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="24ebc-177">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="24ebc-177">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="24ebc-178">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="24ebc-178">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
