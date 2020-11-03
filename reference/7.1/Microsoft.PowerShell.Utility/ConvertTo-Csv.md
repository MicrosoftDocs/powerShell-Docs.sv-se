---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: e4cc40e7a9a5fdcd12b6a787607e4979ddbb3273
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266487"
---
# <span data-ttu-id="663b2-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="663b2-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="663b2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="663b2-104">SYNOPSIS</span></span>
<span data-ttu-id="663b2-105">Konverterar .NET-objekt till en serie med strängar med Character-separerade värden (CSV).</span><span class="sxs-lookup"><span data-stu-id="663b2-105">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="663b2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="663b2-106">SYNTAX</span></span>

### <span data-ttu-id="663b2-107">Avgränsare</span><span class="sxs-lookup"><span data-stu-id="663b2-107">Delimiter</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="663b2-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="663b2-108">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="663b2-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="663b2-109">DESCRIPTION</span></span>

<span data-ttu-id="663b2-110">`ConvertTo-CSV`Cmdleten returnerar en serie kommaavgränsade värden (CSV) som representerar de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="663b2-110">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="663b2-111">Du kan sedan använda `ConvertFrom-Csv` cmdleten för att återskapa objekt från CSV-strängarna.</span><span class="sxs-lookup"><span data-stu-id="663b2-111">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="663b2-112">De objekt som konverteras från CSV är sträng värden för de ursprungliga objekt som innehåller egenskaps värden och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="663b2-112">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="663b2-113">Du kan använda `Export-Csv` cmdleten för att konvertera objekt till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-113">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="663b2-114">`Export-CSV` liknar `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="663b2-114">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="663b2-115">`ConvertTo-CSV`Cmdleten har parametrar för att ange en annan avgränsare än ett kommatecken eller använda den aktuella kulturen som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="663b2-115">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="663b2-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="663b2-116">EXAMPLES</span></span>

### <span data-ttu-id="663b2-117">Exempel 1: konvertera ett objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="663b2-117">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="663b2-118">I det här exemplet konverteras ett **process** objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="663b2-118">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="663b2-119">`Get-Process`Cmdleten hämtar objektet **process** och använder parametern **Name** för att ange PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="663b2-119">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="663b2-120">Processobjektet skickas till `ConvertTo-CSV` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="663b2-120">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="663b2-121">`ConvertTo-CSV`Cmdleten konverterar objektet till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-121">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="663b2-122">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="663b2-122">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="663b2-123">Exempel 2: konvertera ett DateTime-objekt till CSV</span><span class="sxs-lookup"><span data-stu-id="663b2-123">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="663b2-124">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="663b2-124">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="663b2-125">`Get-Date`Cmdleten hämtar **datetime** -objektet och sparar det i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="663b2-125">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="663b2-126">`ConvertTo-Csv`Cmdleten konverterar **datetime** -objektet till strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-126">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="663b2-127">Parametern **InputObject** använder **datetime** -objektet som lagras i `$Date` variabeln.</span><span class="sxs-lookup"><span data-stu-id="663b2-127">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="663b2-128">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="663b2-128">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="663b2-129">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="663b2-129">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="663b2-130">Exempel 3: konvertera PowerShell-händelseloggen till CSV</span><span class="sxs-lookup"><span data-stu-id="663b2-130">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="663b2-131">I det här exemplet konverteras Windows-händelseloggen för PowerShell till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-131">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="663b2-132">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="663b2-132">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="663b2-133">`Get-WinEvent`Cmdleten hämtar händelse loggs objekt och använder parametern **LogName** för att ange namnet på logg filen.</span><span class="sxs-lookup"><span data-stu-id="663b2-133">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="663b2-134">Händelse loggs objekt skickas ned pipelinen till `ConvertTo-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="663b2-134">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="663b2-135">`ConvertTo-Csv`Cmdleten konverterar händelse loggs objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-135">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="663b2-136">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="663b2-136">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="663b2-137">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="663b2-137">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="663b2-138">Exempel 4: konvertera till CSV med citat tecken runt två kolumner</span><span class="sxs-lookup"><span data-stu-id="663b2-138">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="663b2-139">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="663b2-139">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="663b2-140">Exempel 4: konvertera till CSV med enbart offerter vid behov</span><span class="sxs-lookup"><span data-stu-id="663b2-140">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="663b2-141">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="663b2-141">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="663b2-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="663b2-142">PARAMETERS</span></span>

### <span data-ttu-id="663b2-143">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="663b2-143">-Delimiter</span></span>

<span data-ttu-id="663b2-144">Anger avgränsaren för att avgränsa egenskaps värden i CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-144">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="663b2-145">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="663b2-145">The default is a comma (`,`).</span></span> <span data-ttu-id="663b2-146">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="663b2-146">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="663b2-147">Om du vill ange ett semikolon ( `;` ) omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="663b2-147">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="663b2-148">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="663b2-148">-IncludeTypeInformation</span></span>

<span data-ttu-id="663b2-149">När den här parametern används, innehåller den första raden i utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="663b2-149">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="663b2-150">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="663b2-150">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="663b2-151">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="663b2-151">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="663b2-152">– InputObject</span><span class="sxs-lookup"><span data-stu-id="663b2-152">-InputObject</span></span>

<span data-ttu-id="663b2-153">Anger de objekt som konverteras till CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-153">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="663b2-154">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="663b2-154">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="663b2-155">Du kan också skicka pipe-objekt till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="663b2-155">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="663b2-156">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="663b2-156">-NoTypeInformation</span></span>

<span data-ttu-id="663b2-157">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="663b2-157">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="663b2-158">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="663b2-158">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="663b2-159">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="663b2-159">-UseCulture</span></span>

<span data-ttu-id="663b2-160">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="663b2-160">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="663b2-161">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="663b2-161">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="663b2-162">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="663b2-162">-QuoteFields</span></span>

<span data-ttu-id="663b2-163">Anger namnen på de kolumner som ska vara citerade.</span><span class="sxs-lookup"><span data-stu-id="663b2-163">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="663b2-164">När den här parametern används är de angivna kolumnerna citerade.</span><span class="sxs-lookup"><span data-stu-id="663b2-164">When this parameter is used only the specified columns are quoted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="663b2-165">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="663b2-165">-UseQuotes</span></span>

<span data-ttu-id="663b2-166">Anger när offerter används i CSV-filerna.</span><span class="sxs-lookup"><span data-stu-id="663b2-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="663b2-167">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="663b2-167">Possible values are:</span></span>

- <span data-ttu-id="663b2-168">Aldrig – citera ingenting</span><span class="sxs-lookup"><span data-stu-id="663b2-168">Never - don't quote anything</span></span>
- <span data-ttu-id="663b2-169">Always quote all (standard beteende)</span><span class="sxs-lookup"><span data-stu-id="663b2-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="663b2-170">Endast fält med en avgränsning som innehåller ett avgränsnings tecken</span><span class="sxs-lookup"><span data-stu-id="663b2-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="663b2-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="663b2-171">CommonParameters</span></span>

<span data-ttu-id="663b2-172">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="663b2-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="663b2-173">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="663b2-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="663b2-174">INDATA</span><span class="sxs-lookup"><span data-stu-id="663b2-174">INPUTS</span></span>

### <span data-ttu-id="663b2-175">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="663b2-175">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="663b2-176">Du kan skicka vidare alla objekt som har ett ETS-kort (Extended Type System) till `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="663b2-176">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="663b2-177">UTDATA</span><span class="sxs-lookup"><span data-stu-id="663b2-177">OUTPUTS</span></span>

### <span data-ttu-id="663b2-178">System. String</span><span class="sxs-lookup"><span data-stu-id="663b2-178">System.String</span></span>

<span data-ttu-id="663b2-179">CSV-utdata returneras som en samling med strängar.</span><span class="sxs-lookup"><span data-stu-id="663b2-179">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="663b2-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="663b2-180">NOTES</span></span>

<span data-ttu-id="663b2-181">I CSV-format representeras varje objekt av en kommaavgränsad lista över dess egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="663b2-181">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="663b2-182">Egenskaps värden konverteras till strängar med hjälp av objektets **toString ()-** metod.</span><span class="sxs-lookup"><span data-stu-id="663b2-182">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="663b2-183">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="663b2-183">The strings are represented by the property value name.</span></span> <span data-ttu-id="663b2-184">`ConvertTo-CSV` exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="663b2-184">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="663b2-185">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="663b2-185">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="663b2-186">Om **IncludeTypeInformation** används, består den första strängen av **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="663b2-186">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="663b2-187">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="663b2-187">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="663b2-188">Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="663b2-188">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="663b2-189">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="663b2-189">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="663b2-190">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="663b2-190">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="663b2-191">Från och med PowerShell 6,0 är standard beteendet för `ConvertTo-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd.</span><span class="sxs-lookup"><span data-stu-id="663b2-191">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="663b2-192">**IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `ConvertTo-CSV` före PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="663b2-192">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="663b2-193">När du skickar flera objekt till `ConvertTo-CSV` , `ConvertTo-CSV` sorterar strängarna efter egenskaperna för det första objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="663b2-193">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="663b2-194">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="663b2-194">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="663b2-195">Om de återstående objekten har ytterligare egenskaper ignoreras dessa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="663b2-195">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="663b2-196">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="663b2-196">RELATED LINKS</span></span>

[<span data-ttu-id="663b2-197">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="663b2-197">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="663b2-198">Exportera-CSV</span><span class="sxs-lookup"><span data-stu-id="663b2-198">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="663b2-199">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="663b2-199">Import-Csv</span></span>](Import-Csv.md)

