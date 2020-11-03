---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: b91d3b7cbf86c7ea827539903b2e8373cdfdac72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265137"
---
# <span data-ttu-id="6b9c5-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="6b9c5-103">ConvertTo-Json</span></span>

## <span data-ttu-id="6b9c5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6b9c5-104">SYNOPSIS</span></span>
<span data-ttu-id="6b9c5-105">Konverterar ett objekt till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="6b9c5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6b9c5-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="6b9c5-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6b9c5-107">DESCRIPTION</span></span>

<span data-ttu-id="6b9c5-108">`ConvertTo-Json`Cmdleten konverterar alla .net-objekt till ett sträng i JavaScript Object Notation (JSON)-format.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="6b9c5-109">Egenskaperna konverteras till fält namn, fältvärdena konverteras till egenskaps värden och metoderna tas bort.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="6b9c5-110">Du kan sedan använda `ConvertFrom-Json` cmdleten för att konvertera en JSON-formaterad sträng till ett JSON-objekt, som är enkelt att hantera i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="6b9c5-111">Många webbplatser använder JSON i stället för XML för att serialisera data för kommunikation mellan servrar och webbaserade appar.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="6b9c5-112">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6b9c5-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6b9c5-113">EXAMPLES</span></span>

### <span data-ttu-id="6b9c5-114">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="6b9c5-114">Example 1</span></span>

```powershell
PS C:\> (Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

<span data-ttu-id="6b9c5-115">Det här kommandot använder `ConvertTo-Json` cmdleten för att konvertera ett GregorianCalendar-objekt till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="6b9c5-116">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="6b9c5-116">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="6b9c5-117">Det här kommandot visar effekterna av att använda **komprimerings** parametern i `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="6b9c5-117">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="6b9c5-118">Komprimeringen påverkar bara utseendet på strängen, inte dess giltighet.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-118">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="6b9c5-119">Exempel 3</span><span class="sxs-lookup"><span data-stu-id="6b9c5-119">Example 3</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

<span data-ttu-id="6b9c5-120">I det här exemplet används `ConvertTo-Json` cmdleten för att konvertera ett **system. DateTime** -objekt från `Get-Date` cmdlet till en JSON-formaterad sträng.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-120">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="6b9c5-121">Kommandot använder `Select-Object` cmdleten för att hämta alla ( `*` ) för egenskaperna för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-121">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="6b9c5-122">Utdata visar den JSON-sträng som `ConvertTo-Json` returnerades.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-122">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="6b9c5-123">Exempel 4</span><span class="sxs-lookup"><span data-stu-id="6b9c5-123">Example 4</span></span>

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

<span data-ttu-id="6b9c5-124">Det här exemplet visar hur du använder- `ConvertTo-Json` och- `ConvertFrom-Json` cmdletarna för att konvertera ett objekt till en JSON-sträng och ett JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-124">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="6b9c5-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6b9c5-125">PARAMETERS</span></span>

### <span data-ttu-id="6b9c5-126">– Komprimera</span><span class="sxs-lookup"><span data-stu-id="6b9c5-126">-Compress</span></span>

<span data-ttu-id="6b9c5-127">Utelämnar blank steg och formatering med indrag i den utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-127">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="6b9c5-128">-Djup</span><span class="sxs-lookup"><span data-stu-id="6b9c5-128">-Depth</span></span>

<span data-ttu-id="6b9c5-129">Anger hur många nivåer med objekt som ingår i JSON-representationen.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-129">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="6b9c5-130">Standardvärdet är 2.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-130">The default value is 2.</span></span>

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

### <span data-ttu-id="6b9c5-131">– InputObject</span><span class="sxs-lookup"><span data-stu-id="6b9c5-131">-InputObject</span></span>

<span data-ttu-id="6b9c5-132">Anger de objekt som ska konverteras till JSON-format.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-132">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="6b9c5-133">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-133">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="6b9c5-134">Du kan också skicka ett objekt till `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="6b9c5-134">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="6b9c5-135">Parametern **InputObject** är obligatorisk, men dess värde kan vara null ( `$null` ) eller en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-135">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="6b9c5-136">När indata-objektet är `$null` , `ConvertTo-Json` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-136">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="6b9c5-137">Returnerar en tom sträng när inobjektet är en tom sträng `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="6b9c5-137">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="6b9c5-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6b9c5-138">CommonParameters</span></span>

<span data-ttu-id="6b9c5-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6b9c5-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6b9c5-140">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="6b9c5-140">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="6b9c5-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="6b9c5-141">INPUTS</span></span>

### <span data-ttu-id="6b9c5-142">System. Object</span><span class="sxs-lookup"><span data-stu-id="6b9c5-142">System.Object</span></span>

<span data-ttu-id="6b9c5-143">Du kan skicka vidare alla objekt till `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="6b9c5-143">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="6b9c5-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6b9c5-144">OUTPUTS</span></span>

### <span data-ttu-id="6b9c5-145">System. String</span><span class="sxs-lookup"><span data-stu-id="6b9c5-145">System.String</span></span>

## <span data-ttu-id="6b9c5-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6b9c5-146">NOTES</span></span>

<span data-ttu-id="6b9c5-147">`ConvertTo-Json`Cmdleten implementeras med hjälp av [klassen JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="6b9c5-147">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="6b9c5-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6b9c5-148">RELATED LINKS</span></span>

<span data-ttu-id="6b9c5-149">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="6b9c5-149">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="6b9c5-150">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="6b9c5-150">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="6b9c5-151">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="6b9c5-151">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="6b9c5-152">Get-värdet</span><span class="sxs-lookup"><span data-stu-id="6b9c5-152">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="6b9c5-153">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="6b9c5-153">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="6b9c5-154">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="6b9c5-154">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
