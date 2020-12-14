---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: be590368539f396f0aac694e9565674393543f2c
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913210"
---
# <span data-ttu-id="7d4fc-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="7d4fc-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="7d4fc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7d4fc-103">SYNOPSIS</span></span>
<span data-ttu-id="7d4fc-104">Konverterar .NET-objekt till en serie kommaavgränsade värde strängar (CSV).</span><span class="sxs-lookup"><span data-stu-id="7d4fc-104">Converts .NET objects into a series of comma-separated value (CSV) strings.</span></span>

## <span data-ttu-id="7d4fc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7d4fc-105">SYNTAX</span></span>

### <span data-ttu-id="7d4fc-106">Avgränsare (standard)</span><span class="sxs-lookup"><span data-stu-id="7d4fc-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="7d4fc-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="7d4fc-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## <span data-ttu-id="7d4fc-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7d4fc-108">DESCRIPTION</span></span>

<span data-ttu-id="7d4fc-109">`ConvertTo-CSV`Cmdleten returnerar en serie kommaavgränsade värden (CSV) som representerar de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="7d4fc-110">Du kan sedan använda `ConvertFrom-Csv` cmdleten för att återskapa objekt från CSV-strängarna.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="7d4fc-111">De objekt som konverteras från CSV är sträng värden för de ursprungliga objekt som innehåller egenskaps värden och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="7d4fc-112">Du kan använda `Export-Csv` cmdleten för att konvertera objekt till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="7d4fc-113">`Export-CSV` liknar `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="7d4fc-114">`ConvertTo-CSV`Cmdleten har parametrar för att ange en annan avgränsare än ett kommatecken eller använda den aktuella kulturen som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="7d4fc-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7d4fc-115">EXAMPLES</span></span>

### <span data-ttu-id="7d4fc-116">Exempel 1: konvertera ett objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="7d4fc-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="7d4fc-117">I det här exemplet konverteras ett **process** objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

<span data-ttu-id="7d4fc-118">`Get-Process`Cmdleten hämtar objektet **process** och använder parametern **Name** för att ange PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="7d4fc-119">Processobjektet skickas till `ConvertTo-CSV` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="7d4fc-120">`ConvertTo-CSV`Cmdleten konverterar objektet till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="7d4fc-121">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="7d4fc-122">Exempel 2: konvertera ett DateTime-objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="7d4fc-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="7d4fc-123">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="7d4fc-124">`Get-Date`Cmdleten hämtar **datetime** -objektet och sparar det i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="7d4fc-125">`ConvertTo-Csv`Cmdleten konverterar **datetime** -objektet till strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="7d4fc-126">Parametern **InputObject** använder **datetime** -objektet som lagras i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="7d4fc-127">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="7d4fc-128">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="7d4fc-129">Exempel 3: konvertera PowerShell-händelseloggen till CSV</span><span class="sxs-lookup"><span data-stu-id="7d4fc-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="7d4fc-130">I det här exemplet konverteras Windows-händelseloggen för PowerShell till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

<span data-ttu-id="7d4fc-131">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="7d4fc-132">`Get-WinEvent`Cmdleten hämtar händelse loggs objekt och använder parametern **LogName** för att ange namnet på logg filen.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="7d4fc-133">Händelse loggs objekt skickas ned pipelinen till `ConvertTo-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="7d4fc-134">`ConvertTo-Csv`Cmdleten konverterar händelse loggs objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="7d4fc-135">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="7d4fc-136">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvudet från CSV-utdata.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

## <span data-ttu-id="7d4fc-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7d4fc-137">PARAMETERS</span></span>

### <span data-ttu-id="7d4fc-138">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="7d4fc-138">-Delimiter</span></span>

<span data-ttu-id="7d4fc-139">Anger avgränsaren för att avgränsa egenskaps värden i CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-139">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="7d4fc-140">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="7d4fc-140">The default is a comma (`,`).</span></span> <span data-ttu-id="7d4fc-141">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="7d4fc-141">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="7d4fc-142">Om du vill ange ett semikolon ( `;` ) omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-142">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d4fc-143">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7d4fc-143">-InputObject</span></span>

<span data-ttu-id="7d4fc-144">Anger de objekt som konverteras till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-144">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="7d4fc-145">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-145">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="7d4fc-146">Du kan också skicka pipe-objekt till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="7d4fc-146">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7d4fc-147">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="7d4fc-147">-NoTypeInformation</span></span>

<span data-ttu-id="7d4fc-148">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-148">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="7d4fc-149">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-149">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d4fc-150">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="7d4fc-150">-UseCulture</span></span>

<span data-ttu-id="7d4fc-151">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-151">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="7d4fc-152">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="7d4fc-152">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7d4fc-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d4fc-153">CommonParameters</span></span>

<span data-ttu-id="7d4fc-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7d4fc-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7d4fc-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7d4fc-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="7d4fc-156">INPUTS</span></span>

### <span data-ttu-id="7d4fc-157">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7d4fc-157">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7d4fc-158">Du kan skicka vidare alla objekt som har ett ETS-kort (Extended Type System) till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="7d4fc-158">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="7d4fc-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7d4fc-159">OUTPUTS</span></span>

### <span data-ttu-id="7d4fc-160">System. String</span><span class="sxs-lookup"><span data-stu-id="7d4fc-160">System.String</span></span>

<span data-ttu-id="7d4fc-161">CSV-utdata returneras som en samling med strängar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-161">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="7d4fc-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7d4fc-162">NOTES</span></span>

<span data-ttu-id="7d4fc-163">I CSV-format representeras varje objekt av en kommaavgränsad lista över dess egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-163">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="7d4fc-164">Egenskaps värden konverteras till strängar med hjälp av objektets **toString ()-** metod.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-164">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="7d4fc-165">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-165">The strings are represented by the property value name.</span></span> <span data-ttu-id="7d4fc-166">`ConvertTo-CSV` exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-166">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="7d4fc-167">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7d4fc-167">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="7d4fc-168">Den första strängen innehåller som standard den **#TYPE** informations rubriken följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-168">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="7d4fc-169">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-169">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="7d4fc-170">Om **NoTypeInformation** används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-170">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="7d4fc-171">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-171">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="7d4fc-172">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-172">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="7d4fc-173">När du skickar flera objekt till `ConvertTo-CSV` , `ConvertTo-CSV` sorterar strängarna efter egenskaperna för det första objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-173">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="7d4fc-174">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-174">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="7d4fc-175">Om de återstående objekten har ytterligare egenskaper ignoreras dessa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="7d4fc-175">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="7d4fc-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7d4fc-176">RELATED LINKS</span></span>

[<span data-ttu-id="7d4fc-177">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="7d4fc-177">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="7d4fc-178">Exportera-CSV</span><span class="sxs-lookup"><span data-stu-id="7d4fc-178">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="7d4fc-179">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="7d4fc-179">Import-Csv</span></span>](Import-Csv.md)
