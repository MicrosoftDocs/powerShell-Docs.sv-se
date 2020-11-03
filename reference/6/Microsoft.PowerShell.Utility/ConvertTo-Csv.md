---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 5de6a3bd28b850d3fc1632e26998986f302b78f8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267164"
---
# <span data-ttu-id="718dd-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="718dd-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="718dd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="718dd-104">SYNOPSIS</span></span>
<span data-ttu-id="718dd-105">Konverterar .NET-objekt till en serie med strängar med Character-separerade värden (CSV).</span><span class="sxs-lookup"><span data-stu-id="718dd-105">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="718dd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="718dd-106">SYNTAX</span></span>

### <span data-ttu-id="718dd-107">DelimiterPath (standard)</span><span class="sxs-lookup"><span data-stu-id="718dd-107">DelimiterPath (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="718dd-108">Avgränsare</span><span class="sxs-lookup"><span data-stu-id="718dd-108">Delimiter</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [<CommonParameters>]
```

### <span data-ttu-id="718dd-109">UseCulture</span><span class="sxs-lookup"><span data-stu-id="718dd-109">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [<CommonParameters>]
```

## <span data-ttu-id="718dd-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="718dd-110">DESCRIPTION</span></span>

<span data-ttu-id="718dd-111">`ConvertTo-CSV`Cmdleten returnerar en serie kommaavgränsade värden (CSV) som representerar de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="718dd-111">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="718dd-112">Du kan sedan använda `ConvertFrom-Csv` cmdleten för att återskapa objekt från CSV-strängarna.</span><span class="sxs-lookup"><span data-stu-id="718dd-112">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="718dd-113">De objekt som konverteras från CSV är sträng värden för de ursprungliga objekt som innehåller egenskaps värden och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="718dd-113">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="718dd-114">Du kan använda `Export-Csv` cmdleten för att konvertera objekt till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-114">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="718dd-115">`Export-CSV` liknar `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="718dd-115">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="718dd-116">`ConvertTo-CSV`Cmdleten har parametrar för att ange en annan avgränsare än ett kommatecken eller använda den aktuella kulturen som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="718dd-116">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="718dd-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="718dd-117">EXAMPLES</span></span>

### <span data-ttu-id="718dd-118">Exempel 1: konvertera ett objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="718dd-118">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="718dd-119">I det här exemplet konverteras ett **process** objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="718dd-119">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="718dd-120">`Get-Process`Cmdleten hämtar objektet **process** och använder parametern **Name** för att ange PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="718dd-120">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="718dd-121">Processobjektet skickas till `ConvertTo-CSV` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="718dd-121">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="718dd-122">`ConvertTo-CSV`Cmdleten konverterar objektet till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-122">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="718dd-123">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="718dd-123">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="718dd-124">Exempel 2: konvertera ett DateTime-objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="718dd-124">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="718dd-125">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="718dd-125">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="718dd-126">`Get-Date`Cmdleten hämtar **datetime** -objektet och sparar det i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="718dd-126">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="718dd-127">`ConvertTo-Csv`Cmdleten konverterar **datetime** -objektet till strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-127">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="718dd-128">Parametern **InputObject** använder **datetime** -objektet som lagras i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="718dd-128">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="718dd-129">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="718dd-129">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="718dd-130">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="718dd-130">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="718dd-131">Exempel 3: konvertera PowerShell-händelseloggen till CSV</span><span class="sxs-lookup"><span data-stu-id="718dd-131">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="718dd-132">I det här exemplet konverteras Windows-händelseloggen för PowerShell till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-132">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="718dd-133">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="718dd-133">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="718dd-134">`Get-WinEvent`Cmdleten hämtar händelse loggs objekt och använder parametern **LogName** för att ange namnet på logg filen.</span><span class="sxs-lookup"><span data-stu-id="718dd-134">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="718dd-135">Händelse loggs objekt skickas ned pipelinen till `ConvertTo-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="718dd-135">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="718dd-136">`ConvertTo-Csv`Cmdleten konverterar händelse loggs objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-136">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="718dd-137">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="718dd-137">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="718dd-138">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="718dd-138">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

## <span data-ttu-id="718dd-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="718dd-139">PARAMETERS</span></span>

### <span data-ttu-id="718dd-140">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="718dd-140">-Delimiter</span></span>

<span data-ttu-id="718dd-141">Anger avgränsaren för att avgränsa egenskaps värden i CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-141">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="718dd-142">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="718dd-142">The default is a comma (`,`).</span></span> <span data-ttu-id="718dd-143">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="718dd-143">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="718dd-144">Om du vill ange ett semikolon ( `;` ) omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="718dd-144">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="718dd-145">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="718dd-145">-IncludeTypeInformation</span></span>

<span data-ttu-id="718dd-146">När den här parametern används, innehåller den första raden i utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="718dd-146">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="718dd-147">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="718dd-147">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="718dd-148">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="718dd-148">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="718dd-149">– InputObject</span><span class="sxs-lookup"><span data-stu-id="718dd-149">-InputObject</span></span>

<span data-ttu-id="718dd-150">Anger de objekt som konverteras till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-150">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="718dd-151">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="718dd-151">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="718dd-152">Du kan också skicka pipe-objekt till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="718dd-152">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="718dd-153">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="718dd-153">-NoTypeInformation</span></span>

<span data-ttu-id="718dd-154">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="718dd-154">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="718dd-155">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="718dd-155">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="718dd-156">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="718dd-156">-UseCulture</span></span>

<span data-ttu-id="718dd-157">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="718dd-157">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="718dd-158">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="718dd-158">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="718dd-159">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="718dd-159">CommonParameters</span></span>

<span data-ttu-id="718dd-160">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="718dd-160">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="718dd-161">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="718dd-161">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="718dd-162">INDATA</span><span class="sxs-lookup"><span data-stu-id="718dd-162">INPUTS</span></span>

### <span data-ttu-id="718dd-163">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="718dd-163">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="718dd-164">Du kan skicka vidare alla objekt som har ett ETS-kort (Extended Type System) till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="718dd-164">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="718dd-165">UTDATA</span><span class="sxs-lookup"><span data-stu-id="718dd-165">OUTPUTS</span></span>

### <span data-ttu-id="718dd-166">System. String</span><span class="sxs-lookup"><span data-stu-id="718dd-166">System.String</span></span>

<span data-ttu-id="718dd-167">CSV-utdata returneras som en samling med strängar.</span><span class="sxs-lookup"><span data-stu-id="718dd-167">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="718dd-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="718dd-168">NOTES</span></span>

<span data-ttu-id="718dd-169">I CSV-format representeras varje objekt av en kommaavgränsad lista över dess egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="718dd-169">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="718dd-170">Egenskaps värden konverteras till strängar med hjälp av objektets **toString ()-** metod.</span><span class="sxs-lookup"><span data-stu-id="718dd-170">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="718dd-171">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="718dd-171">The strings are represented by the property value name.</span></span> <span data-ttu-id="718dd-172">`ConvertTo-CSV` exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="718dd-172">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="718dd-173">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="718dd-173">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="718dd-174">Om **IncludeTypeInformation** används, består den första strängen av **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="718dd-174">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="718dd-175">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="718dd-175">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="718dd-176">Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="718dd-176">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="718dd-177">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="718dd-177">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="718dd-178">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="718dd-178">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="718dd-179">Från och med PowerShell 6,0 är standard beteendet för `ConvertTo-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd.</span><span class="sxs-lookup"><span data-stu-id="718dd-179">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="718dd-180">**IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `ConvertTo-CSV` före PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="718dd-180">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="718dd-181">När du skickar flera objekt till `ConvertTo-CSV` , `ConvertTo-CSV` sorterar strängarna efter egenskaperna för det första objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="718dd-181">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="718dd-182">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="718dd-182">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="718dd-183">Om de återstående objekten har ytterligare egenskaper ignoreras dessa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="718dd-183">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="718dd-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="718dd-184">RELATED LINKS</span></span>

[<span data-ttu-id="718dd-185">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="718dd-185">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="718dd-186">Exportera-CSV</span><span class="sxs-lookup"><span data-stu-id="718dd-186">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="718dd-187">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="718dd-187">Import-Csv</span></span>](Import-Csv.md)
