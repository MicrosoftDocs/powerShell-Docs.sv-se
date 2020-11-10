---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: e1bab9250269dadf0d899f9e172e8a4a8387271d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388135"
---
# <span data-ttu-id="3a46e-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="3a46e-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="3a46e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3a46e-104">SYNOPSIS</span></span>
<span data-ttu-id="3a46e-105">Konverterar en JSON-formaterad sträng till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-105">Converts a JSON-formatted string to a custom object.</span></span>

## <span data-ttu-id="3a46e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3a46e-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="3a46e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3a46e-107">DESCRIPTION</span></span>

<span data-ttu-id="3a46e-108">`ConvertFrom-Json`Cmdleten konverterar en JavaScript Object Notation (JSON) formaterad sträng till ett anpassat **PSCustomObject** -objekt som har en egenskap för varje fält i JSON-strängen.</span><span class="sxs-lookup"><span data-stu-id="3a46e-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="3a46e-109">JSON används ofta av webbplatser för att tillhandahålla en text representation av objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="3a46e-110">JSON-standarden förhindrar inte användning som är förbjuden med en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="3a46e-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="3a46e-111">Om JSON-strängen t. ex. innehåller dubbla nycklar används bara den sista nyckeln av denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3a46e-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="3a46e-112">Se andra exempel nedan.</span><span class="sxs-lookup"><span data-stu-id="3a46e-112">See other examples below.</span></span>

<span data-ttu-id="3a46e-113">Använd cmdleten om du vill generera en JSON-sträng från ett objekt `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="3a46e-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="3a46e-114">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3a46e-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="3a46e-115">Denna cmdlet stöder inte JSON med kommentarer.</span><span class="sxs-lookup"><span data-stu-id="3a46e-115">This cmdlet doesn't support JSON with comments.</span></span>

## <span data-ttu-id="3a46e-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3a46e-116">EXAMPLES</span></span>

### <span data-ttu-id="3a46e-117">Exempel 1: konvertera ett DateTime-objekt till ett JSON-objekt</span><span class="sxs-lookup"><span data-stu-id="3a46e-117">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="3a46e-118">Detta kommando använder `ConvertTo-Json` `ConvertFrom-Json` cmdletarna och för att konvertera ett **datetime** -objekt från `Get-Date` cmdleten till ett JSON-objekt till en **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="3a46e-118">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="3a46e-119">Exemplet använder `Select-Object` cmdleten för att hämta alla egenskaper för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="3a46e-119">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="3a46e-120">Den använder `ConvertTo-Json` cmdleten för att konvertera **datetime** -objektet till en sträng FORMATERAD som ett JSON-objekt och `ConvertFrom-Json` cmdleten för att konvertera den JSON-formaterade strängen till ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-120">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="3a46e-121">Exempel 2: Hämta JSON-strängar från en webb tjänst och konvertera dem till PowerShell-objekt</span><span class="sxs-lookup"><span data-stu-id="3a46e-121">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="3a46e-122">Detta kommando använder `Invoke-WebRequest` cmdleten för att hämta JSON-strängar från en webb tjänst och använder sedan `ConvertFrom-Json` cmdleten för att konvertera JSON-innehåll till objekt som kan hanteras i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3a46e-122">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="3a46e-123">Du kan också använda `Invoke-RestMethod` cmdleten, som automatiskt KONVERTERAR JSON-innehåll till objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-123">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="3a46e-124">Exempel 3: konvertera en JSON-sträng till ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="3a46e-124">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="3a46e-125">Det här exemplet visar hur du använder `ConvertFrom-Json` cmdleten för att konvertera en JSON-fil till ett anpassat PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-125">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="3a46e-126">Kommandot använder Get-Content cmdlet för att hämta strängarna i en JSON-fil.</span><span class="sxs-lookup"><span data-stu-id="3a46e-126">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="3a46e-127">Sedan använder den pipeline-operatorn för att skicka den avgränsade strängen till `ConvertFrom-Json` cmdleten, som konverterar den till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-127">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

## <span data-ttu-id="3a46e-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3a46e-128">PARAMETERS</span></span>

### <span data-ttu-id="3a46e-129">– InputObject</span><span class="sxs-lookup"><span data-stu-id="3a46e-129">-InputObject</span></span>

<span data-ttu-id="3a46e-130">Anger JSON-strängarna som ska konverteras till JSON-objekt.</span><span class="sxs-lookup"><span data-stu-id="3a46e-130">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="3a46e-131">Ange en variabel som innehåller strängen eller Skriv ett kommando eller uttryck som hämtar strängen.</span><span class="sxs-lookup"><span data-stu-id="3a46e-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="3a46e-132">Du kan också skicka en sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="3a46e-132">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="3a46e-133">Parametern **InputObject** är obligatorisk, men dess värde kan vara en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="3a46e-133">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="3a46e-134">När indata-objektet är en tom sträng `ConvertFrom-Json` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3a46e-134">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="3a46e-135">Värdet för **InputObject** får inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="3a46e-135">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="3a46e-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3a46e-136">CommonParameters</span></span>

<span data-ttu-id="3a46e-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3a46e-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3a46e-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3a46e-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3a46e-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="3a46e-139">INPUTS</span></span>

### <span data-ttu-id="3a46e-140">System. String</span><span class="sxs-lookup"><span data-stu-id="3a46e-140">System.String</span></span>

<span data-ttu-id="3a46e-141">Du kan skicka vidare en JSON-sträng till `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="3a46e-141">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="3a46e-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3a46e-142">OUTPUTS</span></span>

### <span data-ttu-id="3a46e-143">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="3a46e-143">PSCustomObject</span></span>

## <span data-ttu-id="3a46e-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3a46e-144">NOTES</span></span>

<span data-ttu-id="3a46e-145">`ConvertFrom-Json`Cmdleten implementeras med hjälp av [klassen JavaScriptSerializer](/dotnet/api/system.web.script.serialization.javascriptserializer).</span><span class="sxs-lookup"><span data-stu-id="3a46e-145">The `ConvertFrom-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="3a46e-146">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3a46e-146">RELATED LINKS</span></span>

<span data-ttu-id="3a46e-147">[En introduktion till JavaScript Object Notation (JSON) i Java Script och .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="3a46e-147">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="3a46e-148">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="3a46e-148">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="3a46e-149">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="3a46e-149">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="3a46e-150">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="3a46e-150">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
