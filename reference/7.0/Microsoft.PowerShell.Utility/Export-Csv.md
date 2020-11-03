---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: cb58276c8582f9cd1f88a114baae2ce5d0039f45
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262899"
---
# <span data-ttu-id="5e2a9-103">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="5e2a9-103">Export-Csv</span></span>

## <span data-ttu-id="5e2a9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5e2a9-104">SYNOPSIS</span></span>
<span data-ttu-id="5e2a9-105">Konverterar objekt till en serie med kommaavgränsade värde strängar (CSV) och sparar strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-105">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="5e2a9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e2a9-106">SYNTAX</span></span>

### <span data-ttu-id="5e2a9-107">Avgränsare (standard)</span><span class="sxs-lookup"><span data-stu-id="5e2a9-107">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="5e2a9-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="5e2a9-108">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5e2a9-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5e2a9-109">DESCRIPTION</span></span>

<span data-ttu-id="5e2a9-110">`Export-CSV`Cmdleten skapar en CSV-fil med de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-110">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="5e2a9-111">Varje objekt är en rad som innehåller en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-111">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="5e2a9-112">Du kan använda `Export-CSV` cmdleten för att skapa kalkyl blad och dela data med program som accepterar CSV-filer som indata.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-112">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="5e2a9-113">Formatera inte objekt innan du skickar dem till- `Export-CSV` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-113">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="5e2a9-114">Om `Export-CSV` tar emot formaterade objekt, innehåller CSV-filen format egenskaper i stället för objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-114">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="5e2a9-115">Om du bara vill exportera markerade egenskaper för ett objekt använder du `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-115">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="5e2a9-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5e2a9-116">EXAMPLES</span></span>

### <span data-ttu-id="5e2a9-117">Exempel 1: Exportera process egenskaper till en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="5e2a9-117">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="5e2a9-118">I det här exemplet väljs **bearbeta** objekt med vissa egenskaper, och objekten exporteras till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-118">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

```powershell
Get-Process -Name WmiPrvSE | Select-Object -Property BasePriority,Id,SessionId,WorkingSet |
  Export-Csv -Path .\WmiData.csv -NoTypeInformation
Import-Csv -Path .\WmiData.csv
```

```Output
BasePriority Id    SessionId WorkingSet
------------ --    --------- ----------
8            976   0         20267008
8            2292  0         36786176
8            3816  0         30351360
8            8604  0         15011840
8            10008 0         8830976
8            11764 0         14237696
8            54632 0         9502720
```

<span data-ttu-id="5e2a9-119">`Get-Process`Cmdlet: en hämtar **process** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-119">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="5e2a9-120">Parametern **Name** filtrerar utdata så att endast process objekt för Wmiprvse tas med.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-120">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="5e2a9-121">Process objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-121">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="5e2a9-122">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av process objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-122">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="5e2a9-123">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-123">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-124">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-124">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="5e2a9-125">Parametern **Path** anger att WmiData.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-125">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-126">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-126">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-127">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-127">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-128">Exempel 2: exportera processer till en kommaavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="5e2a9-128">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="5e2a9-129">Det här exemplet **hämtar objekt och exporterar objekten till** en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-129">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="5e2a9-130">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-130">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="5e2a9-131">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-131">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-132">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-132">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="5e2a9-133">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-133">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-134">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-134">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-135">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-135">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-136">Exempel 3: exportera processer till en semikolonavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="5e2a9-136">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="5e2a9-137">Det här exemplet **hämtar objekt och exporterar objekten till** en fil med semikolon avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-137">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="5e2a9-138">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-138">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="5e2a9-139">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-139">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-140">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-140">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="5e2a9-141">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-141">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-142">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-142">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="5e2a9-143">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-143">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-144">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-144">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-145">Exempel 4: exportera processer med nuvarande kulturs List avgränsare</span><span class="sxs-lookup"><span data-stu-id="5e2a9-145">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="5e2a9-146">Det här exemplet **hämtar objekt och exporterar objekten till** en fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-146">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="5e2a9-147">Avgränsaren är den aktuella kulturen List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-147">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="5e2a9-148">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-148">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="5e2a9-149">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-149">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="5e2a9-150">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-150">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-151">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-151">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="5e2a9-152">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-152">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-153">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-153">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="5e2a9-154">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-154">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-155">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-155">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-156">Exempel 5: exportera processer med typ information</span><span class="sxs-lookup"><span data-stu-id="5e2a9-156">Example 5: Export processes with type information</span></span>

<span data-ttu-id="5e2a9-157">Det här exemplet förklarar hur du inkluderar **#TYPE** rubrik information i en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-157">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="5e2a9-158">**#TYPEs** huvudet är standardvärdet i tidigare versioner än PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-158">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="5e2a9-159">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-159">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="5e2a9-160">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-160">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-161">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-161">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="5e2a9-162">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-162">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-163">**IncludeTypeInformation** innehåller **#TYPE** informations rubriken i CSV-utdata.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-163">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="5e2a9-164">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-164">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-165">Exempel 6: exportera och lägga till objekt i en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="5e2a9-165">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="5e2a9-166">Det här exemplet beskriver hur du exporterar objekt till en CSV-fil och använder parametern **APPEND** för att lägga till objekt i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-166">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

```powershell
$AppService = (Get-Service -DisplayName *Application* | Select-Object -Property DisplayName, Status)
$AppService | Export-Csv -Path .\Services.Csv -NoTypeInformation
Get-Content -Path .\Services.Csv
$WinService = (Get-Service -DisplayName *Windows* | Select-Object -Property DisplayName, Status)
$WinService | Export-Csv -Path ./Services.csv -NoTypeInformation -Append
Get-Content -Path .\Services.Csv
```

```Output
"DisplayName","Status"
"Application Layer Gateway Service","Stopped"
"Application Identity","Running"
"Windows Audio Endpoint Builder","Running"
"Windows Audio","Running"
"Windows Event Log","Running"
```

<span data-ttu-id="5e2a9-167">`Get-Service`Cmdlet: en hämtar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-167">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="5e2a9-168">Parametern **DisplayName** returnerar tjänster som innehåller Word-programmet.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-168">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="5e2a9-169">Tjänst objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-169">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="5e2a9-170">`Select-Object` använder **egenskaps** parametern för att ange egenskaperna **DisplayName** och **status** .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-170">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="5e2a9-171">`$AppService`Variabeln lagrar objekten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-171">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="5e2a9-172">`$AppService`Objekten skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-172">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-173">`Export-Csv` konverterar tjänst objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-173">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="5e2a9-174">Parametern **Path** anger att Services.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-174">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-175">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-175">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-176">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-176">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="5e2a9-177">`Get-Service` `Select-Object` Cmdletarna och upprepas för tjänster som innehåller ordet Windows.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-177">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="5e2a9-178">`$WinService`Variabeln lagrar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-178">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="5e2a9-179">`Export-Csv`Cmdleten använder parametern **APPEND** för att ange att `$WinService` objekten läggs till i den befintliga Services.csvs filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-179">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="5e2a9-180">`Get-Content`Cmdleten upprepas för att visa den uppdaterade filen som innehåller de data som lagts till.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-180">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="5e2a9-181">Exempel 7: format-cmdleten i en pipeline skapar oväntade resultat</span><span class="sxs-lookup"><span data-stu-id="5e2a9-181">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="5e2a9-182">Det här exemplet visar varför det är viktigt att inte använda en format-cmdlet i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-182">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="5e2a9-183">Felsök pipeline-syntaxen när oväntade utdata tas emot.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-183">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

```powershell
Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\DateTime.csv -NoTypeInformation
Get-Content -Path .\DateTime.csv
```

```Output
"DateTime","Day","DayOfWeek","DayOfYear"
"Wednesday, January 2, 2019 14:59:34","2","Wednesday","2"
```

```powershell
Get-Date | Format-Table -Property DateTime, Day, DayOfWeek, DayOfYear |
 Export-Csv -Path .\FTDateTime.csv -NoTypeInformation
Get-Content -Path .\FTDateTime.csv
```

```Output
"ClassId2e4f51ef21dd47e99d3c952918aff9cd","pageHeaderEntry","pageFooterEntry","autosizeInfo", ...
"033ecb2bc07a4d43b5ef94ed5a35d280",,,,"Microsoft.PowerShell.Commands.Internal.Format. ...
"9e210fe47d09416682b841769c78b8a3",,,,,
"27c87ef9bbda4f709f6b4002fa4af63c",,,,,
"4ec4f0187cb04f4cb6973460dfe252df",,,,,
"cf522b78d86c486691226b40aa69e95c",,,,,
```

<span data-ttu-id="5e2a9-184">`Get-Date`Cmdlet: en hämtar **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-184">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="5e2a9-185">Objektet skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-185">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="5e2a9-186">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-186">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="5e2a9-187">Objektet skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-187">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-188">`Export-Csv` konverterar objektet till ett CSV-format.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-188">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="5e2a9-189">Parametern **Path** anger att DateTime.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-189">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-190">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-190">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-191">`Get-Content`Cmdleten använder parametern **Path** för att Visa CSV-filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-191">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="5e2a9-192">När `Format-Table` cmdleten används i pipelinen för att välja egenskaper tas oväntade resultat emot.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-192">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="5e2a9-193">`Format-Table` skickar tabell formats objekt ned pipelinen till `Export-Csv` cmdleten i stället för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-193">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="5e2a9-194">`Export-Csv` konverterar tabell formats objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-194">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="5e2a9-195">`Get-Content`Cmdleten visar CSV-filen som innehåller tabell formats objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-195">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="5e2a9-196">Exempel 8: använda Force-parametern för att skriva över skrivskyddade filer</span><span class="sxs-lookup"><span data-stu-id="5e2a9-196">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="5e2a9-197">Det här exemplet skapar en tom skrivskyddad fil och använder **Force** -parametern för att uppdatera filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-197">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

```powershell
New-Item -Path .\ReadOnly.csv -ItemType File
Set-ItemProperty -Path .\ReadOnly.csv -Name IsReadOnly -Value $true
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
```

```Output
Export-Csv : Access to the path 'C:\ReadOnly.csv' is denied.
At line:1 char:15
+ Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation
+               ~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : OpenError: (:) [Export-Csv], UnauthorizedAccessException
+ FullyQualifiedErrorId : FileOpenFailure,Microsoft.PowerShell.Commands.ExportCsvCommand
```

```powershell
Get-Process | Export-Csv -Path .\ReadOnly.csv -NoTypeInformation -Force
Get-Content -Path .\ReadOnly.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="5e2a9-198">`New-Item`Cmdleten använder parametrarna **Path** och **ItemType** för att skapa ReadOnly.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-198">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="5e2a9-199">`Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-199">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="5e2a9-200">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-200">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="5e2a9-201">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-201">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-202">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-202">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="5e2a9-203">Parametern **Path** anger att ReadOnly.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-203">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="5e2a9-204">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-204">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="5e2a9-205">Utdata visar att filen inte har skrivits eftersom åtkomst nekas.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-205">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="5e2a9-206">Parametern **Force** läggs till i `Export-Csv` cmdleten för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-206">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="5e2a9-207">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-207">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-208">Exempel 9: använda Force-parametern med append</span><span class="sxs-lookup"><span data-stu-id="5e2a9-208">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="5e2a9-209">I det här exemplet visas hur du använder **Force** -och **APPEND** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-209">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="5e2a9-210">När dessa parametrar kombineras, kan avvikande objekt egenskaper skrivas till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-210">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

```powershell
$Content = [PSCustomObject]@{Name = 'PowerShell Core'; Version = '6.0'}
$Content | Export-Csv -Path .\ParmFile.csv -NoTypeInformation
$AdditionalContent = [PSCustomObject]@{Name = 'Windows PowerShell'; Edition = 'Desktop'}
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
```

```Output
Export-Csv : Cannot append CSV content to the following file: ParmFile.csv.
The appended object does not have a property that corresponds to the following column:
Version. To continue with mismatched properties, add the -Force parameter, and then retry
 the command.
At line:1 char:22
+ $AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append
+                      ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (Version:String) [Export-Csv], InvalidOperationException
+ FullyQualifiedErrorId : CannotAppendCsvWithMismatchedPropertyNames,Microsoft.PowerShell. ...
```

```powershell
$AdditionalContent | Export-Csv -Path .\ParmFile.csv -NoTypeInformation -Append -Force
Import-Csv -Path .\ParmFile.csv
```

```Output
Name               Version
----               -------
PowerShell Core    6.0
Windows PowerShell
```

<span data-ttu-id="5e2a9-211">Ett uttryck skapar **PSCustomObject** med **namn** och **versions** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-211">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="5e2a9-212">Värdena lagras i `$Content` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-212">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="5e2a9-213">`$Content`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-213">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-214">`Export-Csv` använder parametern **Path** och sparar ParmFile.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-214">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="5e2a9-215">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-215">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="5e2a9-216">Ett annat uttryck skapar en **PSCustomObject** med egenskaperna **namn** och **utgåva** .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-216">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="5e2a9-217">Värdena lagras i `$AdditionalContent` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-217">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="5e2a9-218">`$AdditionalContent`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-218">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="5e2a9-219">Parametern **APPEND** används för att lägga till data i filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-219">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="5e2a9-220">Det går inte att lägga till eftersom det finns ett matchnings fel för egenskaps namn mellan **version** och **utgåva**.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-220">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="5e2a9-221">`Export-Csv`Parametern cmdlet **Force** används för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-221">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="5e2a9-222">Egenskapen **Edition** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-222">The **Edition** property is discarded.</span></span> <span data-ttu-id="5e2a9-223">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-223">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="5e2a9-224">Exempel 10: exportera till CSV med citat runt två kolumner</span><span class="sxs-lookup"><span data-stu-id="5e2a9-224">Example 10: Export to CSV with quotes around two columns</span></span>

<span data-ttu-id="5e2a9-225">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-225">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="5e2a9-226">Exempel 11: exportera till CSV med enbart offerter vid behov</span><span class="sxs-lookup"><span data-stu-id="5e2a9-226">Example 11: Export to CSV with quotes only when needed</span></span>

<span data-ttu-id="5e2a9-227">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-227">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="5e2a9-228">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5e2a9-228">PARAMETERS</span></span>

### <span data-ttu-id="5e2a9-229">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="5e2a9-229">-Append</span></span>

<span data-ttu-id="5e2a9-230">Använd den här parametern för att `Export-CSV` lägga till CSV-utdata i slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-230">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="5e2a9-231">Utan den här parametern `Export-CSV` ersätter filens innehåll utan varning.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-231">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="5e2a9-232">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-232">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="5e2a9-233">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="5e2a9-233">-Delimiter</span></span>

<span data-ttu-id="5e2a9-234">Anger en avgränsare för att avgränsa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-234">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="5e2a9-235">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-235">The default is a comma (`,`).</span></span> <span data-ttu-id="5e2a9-236">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-236">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="5e2a9-237">Om du vill ange ett semikolon ( `;` ), omger du det med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-237">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="5e2a9-238">-Encoding</span><span class="sxs-lookup"><span data-stu-id="5e2a9-238">-Encoding</span></span>

<span data-ttu-id="5e2a9-239">Anger kodningen för den exporterade CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-239">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="5e2a9-240">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-240">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="5e2a9-241">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="5e2a9-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="5e2a9-242">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-242">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="5e2a9-243">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-243">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="5e2a9-244">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-244">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="5e2a9-245">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-245">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="5e2a9-246">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-246">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="5e2a9-247">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-247">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="5e2a9-248">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5e2a9-248">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5e2a9-249">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="5e2a9-249">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="5e2a9-250">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-250">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="5e2a9-251">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-251">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="5e2a9-252">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-252">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-253">-Force</span><span class="sxs-lookup"><span data-stu-id="5e2a9-253">-Force</span></span>

<span data-ttu-id="5e2a9-254">Med den här parametern kan `Export-Csv` du skriva över filer med **skrivskyddat** attribut.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-254">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="5e2a9-255">När **tvinga** -och **tilläggs** parametrar kombineras, kan objekt som innehåller felmatchade egenskaper SKRIVAs till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-255">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="5e2a9-256">Endast egenskaper som matchar skrivs till filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-256">Only the properties that match are written to the file.</span></span> <span data-ttu-id="5e2a9-257">De egenskaper som matchar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-257">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="5e2a9-258">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="5e2a9-258">-IncludeTypeInformation</span></span>

<span data-ttu-id="5e2a9-259">När den här parametern används, innehåller den första raden i CSV-utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-259">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="5e2a9-260">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-260">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="5e2a9-261">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-261">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="5e2a9-262">– InputObject</span><span class="sxs-lookup"><span data-stu-id="5e2a9-262">-InputObject</span></span>

<span data-ttu-id="5e2a9-263">Anger de objekt som ska exporteras som CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-263">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="5e2a9-264">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-264">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="5e2a9-265">Du kan också skicka pipe-objekt till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-265">You can also pipe objects to `Export-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-266">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5e2a9-266">-LiteralPath</span></span>

<span data-ttu-id="5e2a9-267">Anger sökvägen till CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-267">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="5e2a9-268">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-268">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="5e2a9-269">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-269">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5e2a9-270">Om sökvägen innehåller escape-tecken använder du enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-270">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="5e2a9-271">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-271">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-272">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="5e2a9-272">-NoClobber</span></span>

<span data-ttu-id="5e2a9-273">Använd den här parametern så att `Export-CSV` ingen befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-273">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="5e2a9-274">Om filen finns på den angivna sökvägen `Export-CSV` skrivs filen som standard utan varning.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-274">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-275">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="5e2a9-275">-NoTypeInformation</span></span>

<span data-ttu-id="5e2a9-276">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-276">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="5e2a9-277">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-277">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="5e2a9-278">-Path</span><span class="sxs-lookup"><span data-stu-id="5e2a9-278">-Path</span></span>

<span data-ttu-id="5e2a9-279">En obligatorisk parameter som anger den plats där du vill spara CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-279">A required parameter that specifies the location to save the CSV output file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-280">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="5e2a9-280">-UseCulture</span></span>

<span data-ttu-id="5e2a9-281">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-281">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="5e2a9-282">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-282">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="5e2a9-283">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5e2a9-283">-Confirm</span></span>

<span data-ttu-id="5e2a9-284">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-284">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-285">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5e2a9-285">-WhatIf</span></span>

<span data-ttu-id="5e2a9-286">Förhindrar att cmdleten bearbetas eller gör ändringar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-286">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="5e2a9-287">Utdata visar vad som händer om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-287">The output shows what would happen if the cmdlet were run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e2a9-288">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="5e2a9-288">-QuoteFields</span></span>

<span data-ttu-id="5e2a9-289">Anger namnen på de kolumner som ska vara citerade.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-289">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="5e2a9-290">När den här parametern används är bara de angivna kolumnerna citerade.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-290">When this parameter is used, only the specified columns are quoted.</span></span>

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

### <span data-ttu-id="5e2a9-291">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="5e2a9-291">-UseQuotes</span></span>

<span data-ttu-id="5e2a9-292">Anger när offerter används i CSV-filerna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-292">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="5e2a9-293">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="5e2a9-293">Possible values are:</span></span>

- <span data-ttu-id="5e2a9-294">Aldrig – citera ingenting</span><span class="sxs-lookup"><span data-stu-id="5e2a9-294">Never - don't quote anything</span></span>
- <span data-ttu-id="5e2a9-295">Always quote all (standard beteende)</span><span class="sxs-lookup"><span data-stu-id="5e2a9-295">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="5e2a9-296">Endast fält med en avgränsning som innehåller ett avgränsnings tecken</span><span class="sxs-lookup"><span data-stu-id="5e2a9-296">AsNeeded - only quote fields that contain a delimiter character</span></span>

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

### <span data-ttu-id="5e2a9-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e2a9-297">CommonParameters</span></span>

<span data-ttu-id="5e2a9-298">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e2a9-299">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e2a9-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e2a9-300">INDATA</span><span class="sxs-lookup"><span data-stu-id="5e2a9-300">INPUTS</span></span>

### <span data-ttu-id="5e2a9-301">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="5e2a9-301">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="5e2a9-302">Du kan skicka ett objekt med ett ETS-kort (Extended Type System) till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-302">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="5e2a9-303">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5e2a9-303">OUTPUTS</span></span>

### <span data-ttu-id="5e2a9-304">System. String</span><span class="sxs-lookup"><span data-stu-id="5e2a9-304">System.String</span></span>

<span data-ttu-id="5e2a9-305">CSV-listan skickas till den fil som anges i parametern Path.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-305">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="5e2a9-306">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5e2a9-306">NOTES</span></span>

<span data-ttu-id="5e2a9-307">`Export-CSV`Cmdleten konverterar de objekt som du skickar till en serie med CSV-strängar och sparar dem i den angivna text filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-307">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="5e2a9-308">Du kan använda `Export-CSV -IncludeTypeInformation` för att spara objekt i en CSV-fil och sedan använda `Import-Csv` cmdleten för att skapa objekt från texten i CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-308">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="5e2a9-309">I CSV-filen representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-309">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="5e2a9-310">Egenskaps värden konverteras till strängar med hjälp av metoden **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="5e2a9-310">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="5e2a9-311">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-311">The strings are represented by the property value name.</span></span> <span data-ttu-id="5e2a9-312">`Export-CSV -IncludeTypeInformation` exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-312">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="5e2a9-313">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="5e2a9-313">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="5e2a9-314">Om **IncludeTypeInformation** används, innehåller den första strängen **#TYPE** informations huvud följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-314">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="5e2a9-315">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-315">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="5e2a9-316">Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-316">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="5e2a9-317">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-317">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="5e2a9-318">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-318">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="5e2a9-319">Från och med PowerShell 6,0 är standard beteendet för `Export-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-319">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="5e2a9-320">**IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `Export-CSV` före PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-320">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="5e2a9-321">När du skickar flera objekt till `Export-CSV` `Export-CSV` ordnas filen baserat på egenskaperna för det första objektet som du skickar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-321">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="5e2a9-322">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-322">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="5e2a9-323">Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-323">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="5e2a9-324">Du kan använda `Import-Csv` cmdleten för att återskapa objekt från CSV-strängarna i filerna.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-324">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="5e2a9-325">De resulterande objekten är CSV-versioner av de ursprungliga objekten som består av sträng representationer av egenskapsvärdena och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-325">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="5e2a9-326">`ConvertTo-Csv` `ConvertFrom-Csv` Cmdletarna och konverterar objekt till CSV-strängar och från CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-326">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="5e2a9-327">`Export-CSV` är detsamma som `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="5e2a9-327">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="5e2a9-328">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5e2a9-328">RELATED LINKS</span></span>

[<span data-ttu-id="5e2a9-329">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="5e2a9-329">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="5e2a9-330">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="5e2a9-330">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="5e2a9-331">Format-Table</span><span class="sxs-lookup"><span data-stu-id="5e2a9-331">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="5e2a9-332">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="5e2a9-332">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="5e2a9-333">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5e2a9-333">Select-Object</span></span>](Select-Object.md)
