---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 83a8cb444c20db8f7dd2181cac13e56d54d5d986
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709817"
---
# <span data-ttu-id="2f79c-102">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="2f79c-102">ConvertTo-Json</span></span>

## <span data-ttu-id="2f79c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2f79c-103">SYNOPSIS</span></span>
<span data-ttu-id="2f79c-104">Konverterar ett objekt till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="2f79c-104">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="2f79c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f79c-105">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="2f79c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2f79c-106">DESCRIPTION</span></span>

<span data-ttu-id="2f79c-107">`ConvertTo-Json`Cmdleten konverterar alla .net-objekt till ett sträng i JavaScript Object Notation (JSON)-format.</span><span class="sxs-lookup"><span data-stu-id="2f79c-107">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="2f79c-108">Egenskaperna konverteras till fält namn, fältvärdena konverteras till egenskaps värden och metoderna tas bort.</span><span class="sxs-lookup"><span data-stu-id="2f79c-108">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="2f79c-109">Du kan sedan använda `ConvertFrom-Json` cmdleten för att konvertera en JSON-formaterad sträng till ett JSON-objekt, som är enkelt att hantera i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2f79c-109">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="2f79c-110">Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.</span><span class="sxs-lookup"><span data-stu-id="2f79c-110">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="2f79c-111">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2f79c-111">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="2f79c-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2f79c-112">EXAMPLES</span></span>

### <span data-ttu-id="2f79c-113">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="2f79c-113">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

<span data-ttu-id="2f79c-114">Det här kommandot använder `ConvertTo-Json` cmdleten för att konvertera ett GregorianCalendar-objekt till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="2f79c-114">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="2f79c-115">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="2f79c-115">Example 2</span></span>

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

<span data-ttu-id="2f79c-116">I det här exemplet visas utdata från `ConvertTo-Json` cmdlet med och utan växlings parametern för **ommatrisen** .</span><span class="sxs-lookup"><span data-stu-id="2f79c-116">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="2f79c-117">Du kan se att den andra delen av utdata är omsluten med vinkelparenteser.</span><span class="sxs-lookup"><span data-stu-id="2f79c-117">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="2f79c-118">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="2f79c-118">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="2f79c-119">Det här kommandot visar effekterna av att använda **komprimerings** parametern i `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f79c-119">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="2f79c-120">Komprimeringen påverkar bara utseendet på strängen, inte dess giltighet.</span><span class="sxs-lookup"><span data-stu-id="2f79c-120">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="2f79c-121">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="2f79c-121">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

<span data-ttu-id="2f79c-122">I det här exemplet används `ConvertTo-Json` cmdleten för att konvertera ett **system. DateTime** -objekt från `Get-Date` cmdlet till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="2f79c-122">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="2f79c-123">Kommandot använder `Select-Object` cmdleten för att hämta alla ( `*` ) för egenskaperna för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="2f79c-123">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="2f79c-124">Utdata visar den JSON-sträng som `ConvertTo-Json` returnerades.</span><span class="sxs-lookup"><span data-stu-id="2f79c-124">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="2f79c-125">Exempel 5</span><span class="sxs-lookup"><span data-stu-id="2f79c-125">Example 5</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

<span data-ttu-id="2f79c-126">Det här exemplet visar hur du använder- `ConvertTo-Json` och- `ConvertFrom-Json` cmdletarna för att konvertera ett objekt till en JSON-sträng och ett JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="2f79c-126">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="2f79c-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2f79c-127">PARAMETERS</span></span>

### <span data-ttu-id="2f79c-128">-Matris</span><span class="sxs-lookup"><span data-stu-id="2f79c-128">-AsArray</span></span>

<span data-ttu-id="2f79c-129">Matar ut objektet i vinkelparenteser, även om indatan är ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="2f79c-129">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="2f79c-130">– Komprimera</span><span class="sxs-lookup"><span data-stu-id="2f79c-130">-Compress</span></span>

<span data-ttu-id="2f79c-131">Utelämnar blank steg och formatering med indrag i den utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="2f79c-131">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="2f79c-132">-Djup</span><span class="sxs-lookup"><span data-stu-id="2f79c-132">-Depth</span></span>

<span data-ttu-id="2f79c-133">Anger hur många nivåer med objekt som ingår i JSON-representationen.</span><span class="sxs-lookup"><span data-stu-id="2f79c-133">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="2f79c-134">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="2f79c-134">The default value is 2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f79c-135">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="2f79c-135">-EnumsAsStrings</span></span>

<span data-ttu-id="2f79c-136">Tillhandahåller ett alternativt alternativ för serialisering som konverterar alla uppräkningar till deras sträng representation.</span><span class="sxs-lookup"><span data-stu-id="2f79c-136">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="2f79c-137">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="2f79c-137">-EscapeHandling</span></span>

<span data-ttu-id="2f79c-138">Styr hur vissa tecken är undantagna i det resulterande JSON-resultatet.</span><span class="sxs-lookup"><span data-stu-id="2f79c-138">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="2f79c-139">Som standard är endast kontroll tecken (t. ex. rad matning) som är undantagna.</span><span class="sxs-lookup"><span data-stu-id="2f79c-139">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="2f79c-140">Godkända värden är:</span><span class="sxs-lookup"><span data-stu-id="2f79c-140">Acceptable values are:</span></span>

- <span data-ttu-id="2f79c-141">Standard kontroll tecken är undantagna.</span><span class="sxs-lookup"><span data-stu-id="2f79c-141">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="2f79c-142">EscapeNonAscii-alla icke-ASCII-och kontroll tecken är undantagna.</span><span class="sxs-lookup"><span data-stu-id="2f79c-142">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="2f79c-143">EscapeHtml-HTML ( `<` ,,, `>` `&` `'` , `"` ) och kontroll tecken är undantagna.</span><span class="sxs-lookup"><span data-stu-id="2f79c-143">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="2f79c-144">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="2f79c-144">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f79c-145">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2f79c-145">-InputObject</span></span>

<span data-ttu-id="2f79c-146">Anger de objekt som ska konverteras till JSON-format.</span><span class="sxs-lookup"><span data-stu-id="2f79c-146">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="2f79c-147">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="2f79c-147">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="2f79c-148">Du kan också skicka ett objekt till `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f79c-148">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="2f79c-149">Parametern **InputObject** är obligatorisk, men dess värde kan vara null ( `$null` ) eller en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="2f79c-149">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="2f79c-150">När indata-objektet är `$null` , `ConvertTo-Json` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2f79c-150">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="2f79c-151">Returnerar en tom sträng när inobjektet är en tom sträng `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f79c-151">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2f79c-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f79c-152">CommonParameters</span></span>

<span data-ttu-id="2f79c-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f79c-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f79c-154">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2f79c-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2f79c-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="2f79c-155">INPUTS</span></span>

### <span data-ttu-id="2f79c-156">System. Object</span><span class="sxs-lookup"><span data-stu-id="2f79c-156">System.Object</span></span>

<span data-ttu-id="2f79c-157">Du kan skicka vidare alla objekt till `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f79c-157">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="2f79c-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2f79c-158">OUTPUTS</span></span>

### <span data-ttu-id="2f79c-159">System. String</span><span class="sxs-lookup"><span data-stu-id="2f79c-159">System.String</span></span>

## <span data-ttu-id="2f79c-160">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2f79c-160">NOTES</span></span>

<span data-ttu-id="2f79c-161">`ConvertTo-Json`Cmdleten implementeras med hjälp av [Newtonsoft JSON.net](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="2f79c-161">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="2f79c-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2f79c-162">RELATED LINKS</span></span>

<span data-ttu-id="2f79c-163">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="2f79c-163">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="2f79c-164">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="2f79c-164">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="2f79c-165">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="2f79c-165">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="2f79c-166">Get-värdet</span><span class="sxs-lookup"><span data-stu-id="2f79c-166">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="2f79c-167">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="2f79c-167">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="2f79c-168">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="2f79c-168">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="2f79c-169">NewtonSoft.Jspå. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="2f79c-169">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
