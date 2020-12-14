---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: b0e889b95d2724dfa395b1b4a00b5c9ea878cc82
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913193"
---
# <span data-ttu-id="654b6-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="654b6-102">Export-Csv</span></span>

## <span data-ttu-id="654b6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="654b6-103">SYNOPSIS</span></span>
<span data-ttu-id="654b6-104">Konverterar objekt till en serie med kommaavgränsade värde strängar (CSV) och sparar strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="654b6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="654b6-105">SYNTAX</span></span>

### <span data-ttu-id="654b6-106">Avgränsare (standard)</span><span class="sxs-lookup"><span data-stu-id="654b6-106">Delimiter (Default)</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="654b6-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="654b6-107">UseCulture</span></span>

```
Export-Csv -InputObject <PSObject> [[-Path] <String>] [-LiteralPath <String>] [-Force] [-NoClobber]
 [-Encoding <Encoding>] [-Append] [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="654b6-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="654b6-108">DESCRIPTION</span></span>

<span data-ttu-id="654b6-109">`Export-CSV`Cmdleten skapar en CSV-fil med de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="654b6-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="654b6-110">Varje objekt är en rad som innehåller en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="654b6-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="654b6-111">Du kan använda `Export-CSV` cmdleten för att skapa kalkyl blad och dela data med program som accepterar CSV-filer som indata.</span><span class="sxs-lookup"><span data-stu-id="654b6-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="654b6-112">Formatera inte objekt innan du skickar dem till- `Export-CSV` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="654b6-113">Om `Export-CSV` tar emot formaterade objekt, innehåller CSV-filen format egenskaper i stället för objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="654b6-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="654b6-114">Om du bara vill exportera markerade egenskaper för ett objekt använder du `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="654b6-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="654b6-115">EXAMPLES</span></span>

### <span data-ttu-id="654b6-116">Exempel 1: Exportera process egenskaper till en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="654b6-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="654b6-117">I det här exemplet väljs **bearbeta** objekt med vissa egenskaper, och objekten exporteras till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="654b6-118">`Get-Process`Cmdlet: en hämtar **process** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="654b6-119">Parametern **Name** filtrerar utdata så att endast process objekt för Wmiprvse tas med.</span><span class="sxs-lookup"><span data-stu-id="654b6-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="654b6-120">Process objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="654b6-121">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av process objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="654b6-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="654b6-122">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-123">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="654b6-124">Parametern **Path** anger att WmiData.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-125">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-126">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-127">Exempel 2: exportera processer till en kommaavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="654b6-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="654b6-128">Det här exemplet **hämtar objekt och exporterar objekten till** en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="654b6-129">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="654b6-130">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-131">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="654b6-132">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-133">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-134">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-135">Exempel 3: exportera processer till en semikolonavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="654b6-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="654b6-136">Det här exemplet **hämtar objekt och exporterar objekten till** en fil med semikolon avgränsare.</span><span class="sxs-lookup"><span data-stu-id="654b6-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="654b6-137">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="654b6-138">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-139">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="654b6-140">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-141">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="654b6-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="654b6-142">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-143">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-144">Exempel 4: exportera processer med nuvarande kulturs List avgränsare</span><span class="sxs-lookup"><span data-stu-id="654b6-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="654b6-145">Det här exemplet **hämtar objekt och exporterar objekten till** en fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="654b6-146">Avgränsaren är den aktuella kulturen List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="654b6-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="654b6-147">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="654b6-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="654b6-148">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="654b6-149">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-150">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="654b6-151">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-152">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="654b6-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="654b6-153">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-154">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-155">Exempel 5: exportera processer med typ information</span><span class="sxs-lookup"><span data-stu-id="654b6-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="654b6-156">Det här exemplet förklarar hur du inkluderar **#TYPE** rubrik information i en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="654b6-157">**#TYPEs** huvudet är standardvärdet i tidigare versioner än PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -IncludeTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="654b6-158">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="654b6-159">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-160">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="654b6-161">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-162">**IncludeTypeInformation** innehåller **#TYPE** informations rubriken i CSV-utdata.</span><span class="sxs-lookup"><span data-stu-id="654b6-162">The **IncludeTypeInformation** includes the **#TYPE** information header in the CSV output.</span></span> <span data-ttu-id="654b6-163">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-163">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-164">Exempel 6: exportera och lägga till objekt i en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="654b6-164">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="654b6-165">Det här exemplet beskriver hur du exporterar objekt till en CSV-fil och använder parametern **APPEND** för att lägga till objekt i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-165">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="654b6-166">`Get-Service`Cmdlet: en hämtar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-166">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="654b6-167">Parametern **DisplayName** returnerar tjänster som innehåller Word-programmet.</span><span class="sxs-lookup"><span data-stu-id="654b6-167">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="654b6-168">Tjänst objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-168">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="654b6-169">`Select-Object` använder **egenskaps** parametern för att ange egenskaperna **DisplayName** och **status** .</span><span class="sxs-lookup"><span data-stu-id="654b6-169">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="654b6-170">`$AppService`Variabeln lagrar objekten.</span><span class="sxs-lookup"><span data-stu-id="654b6-170">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="654b6-171">`$AppService`Objekten skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-171">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-172">`Export-Csv` konverterar tjänst objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-172">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="654b6-173">Parametern **Path** anger att Services.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-173">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-174">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-174">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-175">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-175">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="654b6-176">`Get-Service` `Select-Object` Cmdletarna och upprepas för tjänster som innehåller ordet Windows.</span><span class="sxs-lookup"><span data-stu-id="654b6-176">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="654b6-177">`$WinService`Variabeln lagrar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-177">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="654b6-178">`Export-Csv`Cmdleten använder parametern **APPEND** för att ange att `$WinService` objekten läggs till i den befintliga Services.csvs filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-178">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="654b6-179">`Get-Content`Cmdleten upprepas för att visa den uppdaterade filen som innehåller de data som lagts till.</span><span class="sxs-lookup"><span data-stu-id="654b6-179">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="654b6-180">Exempel 7: format-cmdleten i en pipeline skapar oväntade resultat</span><span class="sxs-lookup"><span data-stu-id="654b6-180">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="654b6-181">Det här exemplet visar varför det är viktigt att inte använda en format-cmdlet i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="654b6-181">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="654b6-182">Felsök pipeline-syntaxen när oväntade utdata tas emot.</span><span class="sxs-lookup"><span data-stu-id="654b6-182">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="654b6-183">`Get-Date`Cmdlet: en hämtar **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="654b6-183">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="654b6-184">Objektet skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-184">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="654b6-185">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="654b6-185">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="654b6-186">Objektet skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-186">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-187">`Export-Csv` konverterar objektet till ett CSV-format.</span><span class="sxs-lookup"><span data-stu-id="654b6-187">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="654b6-188">Parametern **Path** anger att DateTime.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-188">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-189">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-189">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-190">`Get-Content`Cmdleten använder parametern **Path** för att Visa CSV-filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-190">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="654b6-191">När `Format-Table` cmdleten används i pipelinen för att välja egenskaper tas oväntade resultat emot.</span><span class="sxs-lookup"><span data-stu-id="654b6-191">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="654b6-192">`Format-Table` skickar tabell formats objekt ned pipelinen till `Export-Csv` cmdleten i stället för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="654b6-192">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="654b6-193">`Export-Csv` konverterar tabell formats objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-193">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="654b6-194">`Get-Content`Cmdleten visar CSV-filen som innehåller tabell formats objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-194">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="654b6-195">Exempel 8: använda Force-parametern för att skriva över skrivskyddade filer</span><span class="sxs-lookup"><span data-stu-id="654b6-195">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="654b6-196">Det här exemplet skapar en tom skrivskyddad fil och använder **Force** -parametern för att uppdatera filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-196">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="654b6-197">`New-Item`Cmdleten använder parametrarna **Path** och **ItemType** för att skapa ReadOnly.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-197">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="654b6-198">`Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.</span><span class="sxs-lookup"><span data-stu-id="654b6-198">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="654b6-199">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="654b6-199">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="654b6-200">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-200">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-201">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-201">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="654b6-202">Parametern **Path** anger att ReadOnly.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-202">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="654b6-203">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-203">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="654b6-204">Utdata visar att filen inte har skrivits eftersom åtkomst nekas.</span><span class="sxs-lookup"><span data-stu-id="654b6-204">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="654b6-205">Parametern **Force** läggs till i `Export-Csv` cmdleten för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-205">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="654b6-206">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-206">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-207">Exempel 9: använda Force-parametern med append</span><span class="sxs-lookup"><span data-stu-id="654b6-207">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="654b6-208">I det här exemplet visas hur du använder **Force** -och **APPEND** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="654b6-208">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="654b6-209">När dessa parametrar kombineras, kan avvikande objekt egenskaper skrivas till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-209">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="654b6-210">Ett uttryck skapar **PSCustomObject** med **namn** och **versions** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="654b6-210">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="654b6-211">Värdena lagras i `$Content` variabeln.</span><span class="sxs-lookup"><span data-stu-id="654b6-211">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="654b6-212">`$Content`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-212">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-213">`Export-Csv` använder parametern **Path** och sparar ParmFile.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-213">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="654b6-214">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="654b6-214">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="654b6-215">Ett annat uttryck skapar en **PSCustomObject** med egenskaperna **namn** och **utgåva** .</span><span class="sxs-lookup"><span data-stu-id="654b6-215">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="654b6-216">Värdena lagras i `$AdditionalContent` variabeln.</span><span class="sxs-lookup"><span data-stu-id="654b6-216">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="654b6-217">`$AdditionalContent`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-217">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="654b6-218">Parametern **APPEND** används för att lägga till data i filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-218">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="654b6-219">Det går inte att lägga till eftersom det finns ett matchnings fel för egenskaps namn mellan **version** och **utgåva**.</span><span class="sxs-lookup"><span data-stu-id="654b6-219">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="654b6-220">`Export-Csv`Parametern cmdlet **Force** används för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-220">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="654b6-221">Egenskapen **Edition** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="654b6-221">The **Edition** property is discarded.</span></span> <span data-ttu-id="654b6-222">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="654b6-222">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="654b6-223">Exempel 10: exportera till CSV med citat runt två kolumner</span><span class="sxs-lookup"><span data-stu-id="654b6-223">Example 10: Export to CSV with quotes around two columns</span></span>

<span data-ttu-id="654b6-224">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="654b6-224">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -QuoteFields "DateTime","Date" -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="654b6-225">Exempel 11: exportera till CSV med enbart offerter vid behov</span><span class="sxs-lookup"><span data-stu-id="654b6-225">Example 11: Export to CSV with quotes only when needed</span></span>

<span data-ttu-id="654b6-226">I det här exemplet konverteras ett **datetime** -objekt till en CSV-sträng.</span><span class="sxs-lookup"><span data-stu-id="654b6-226">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | Export-Csv  -UseQuotes AsNeeded -Path .\FTDateTime.csv
Get-Content -Path .\FTDateTime.csv
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="654b6-227">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="654b6-227">PARAMETERS</span></span>

### <span data-ttu-id="654b6-228">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="654b6-228">-Append</span></span>

<span data-ttu-id="654b6-229">Använd den här parametern för att `Export-CSV` lägga till CSV-utdata i slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-229">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="654b6-230">Utan den här parametern `Export-CSV` ersätter filens innehåll utan varning.</span><span class="sxs-lookup"><span data-stu-id="654b6-230">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="654b6-231">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-231">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="654b6-232">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="654b6-232">-Delimiter</span></span>

<span data-ttu-id="654b6-233">Anger en avgränsare för att avgränsa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="654b6-233">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="654b6-234">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="654b6-234">The default is a comma (`,`).</span></span> <span data-ttu-id="654b6-235">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="654b6-235">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="654b6-236">Om du vill ange ett semikolon ( `;` ), omger du det med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="654b6-236">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="654b6-237">-Encoding</span><span class="sxs-lookup"><span data-stu-id="654b6-237">-Encoding</span></span>

<span data-ttu-id="654b6-238">Anger kodningen för den exporterade CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-238">Specifies the encoding for the exported CSV file.</span></span> <span data-ttu-id="654b6-239">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="654b6-239">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="654b6-240">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="654b6-240">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="654b6-241">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="654b6-241">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="654b6-242">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="654b6-242">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="654b6-243">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="654b6-243">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="654b6-244">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="654b6-244">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="654b6-245">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="654b6-245">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="654b6-246">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="654b6-246">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="654b6-247">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="654b6-247">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="654b6-248">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="654b6-248">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="654b6-249">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="654b6-249">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="654b6-250">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="654b6-250">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="654b6-251">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="654b6-251">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="654b6-252">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="654b6-252">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="654b6-253">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="654b6-253">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="654b6-254">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="654b6-254">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="654b6-255">-Force</span><span class="sxs-lookup"><span data-stu-id="654b6-255">-Force</span></span>

<span data-ttu-id="654b6-256">Med den här parametern kan `Export-Csv` du skriva över filer med **skrivskyddat** attribut.</span><span class="sxs-lookup"><span data-stu-id="654b6-256">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="654b6-257">När **tvinga** -och **tilläggs** parametrar kombineras, kan objekt som innehåller felmatchade egenskaper SKRIVAs till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-257">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="654b6-258">Endast egenskaper som matchar skrivs till filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-258">Only the properties that match are written to the file.</span></span> <span data-ttu-id="654b6-259">De egenskaper som matchar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="654b6-259">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="654b6-260">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="654b6-260">-IncludeTypeInformation</span></span>

<span data-ttu-id="654b6-261">När den här parametern används, innehåller den första raden i CSV-utdata **#TYPE** följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="654b6-261">When this parameter is used the first line of the CSV output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="654b6-262">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="654b6-262">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="654b6-263">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-263">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="654b6-264">– InputObject</span><span class="sxs-lookup"><span data-stu-id="654b6-264">-InputObject</span></span>

<span data-ttu-id="654b6-265">Anger de objekt som ska exporteras som CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-265">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="654b6-266">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="654b6-266">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="654b6-267">Du kan också skicka pipe-objekt till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="654b6-267">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="654b6-268">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="654b6-268">-LiteralPath</span></span>

<span data-ttu-id="654b6-269">Anger sökvägen till CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="654b6-269">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="654b6-270">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="654b6-270">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="654b6-271">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="654b6-271">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="654b6-272">Om sökvägen innehåller escape-tecken använder du enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="654b6-272">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="654b6-273">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="654b6-273">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="654b6-274">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="654b6-274">-NoClobber</span></span>

<span data-ttu-id="654b6-275">Använd den här parametern så att `Export-CSV` ingen befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="654b6-275">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="654b6-276">Om filen finns på den angivna sökvägen `Export-CSV` skrivs filen som standard utan varning.</span><span class="sxs-lookup"><span data-stu-id="654b6-276">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="654b6-277">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="654b6-277">-NoTypeInformation</span></span>

<span data-ttu-id="654b6-278">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="654b6-278">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="654b6-279">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="654b6-279">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="654b6-280">-Path</span><span class="sxs-lookup"><span data-stu-id="654b6-280">-Path</span></span>

<span data-ttu-id="654b6-281">En obligatorisk parameter som anger den plats där du vill spara CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="654b6-281">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="654b6-282">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="654b6-282">-UseCulture</span></span>

<span data-ttu-id="654b6-283">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="654b6-283">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="654b6-284">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="654b6-284">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="654b6-285">-Confirm</span><span class="sxs-lookup"><span data-stu-id="654b6-285">-Confirm</span></span>

<span data-ttu-id="654b6-286">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="654b6-286">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="654b6-287">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="654b6-287">-WhatIf</span></span>

<span data-ttu-id="654b6-288">Förhindrar att cmdleten bearbetas eller gör ändringar.</span><span class="sxs-lookup"><span data-stu-id="654b6-288">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="654b6-289">Utdata visar vad som händer om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="654b6-289">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="654b6-290">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="654b6-290">-QuoteFields</span></span>

<span data-ttu-id="654b6-291">Anger namnen på de kolumner som ska vara citerade.</span><span class="sxs-lookup"><span data-stu-id="654b6-291">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="654b6-292">När den här parametern används är bara de angivna kolumnerna citerade.</span><span class="sxs-lookup"><span data-stu-id="654b6-292">When this parameter is used, only the specified columns are quoted.</span></span> <span data-ttu-id="654b6-293">Den här parametern lades till i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-293">This parameter was added in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="654b6-294">-UseQuotes</span><span class="sxs-lookup"><span data-stu-id="654b6-294">-UseQuotes</span></span>

<span data-ttu-id="654b6-295">Anger när offerter används i CSV-filerna.</span><span class="sxs-lookup"><span data-stu-id="654b6-295">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="654b6-296">Möjliga värden:</span><span class="sxs-lookup"><span data-stu-id="654b6-296">Possible values are:</span></span>

- <span data-ttu-id="654b6-297">Aldrig – citera ingenting</span><span class="sxs-lookup"><span data-stu-id="654b6-297">Never - don't quote anything</span></span>
- <span data-ttu-id="654b6-298">Always quote all (standard beteende)</span><span class="sxs-lookup"><span data-stu-id="654b6-298">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="654b6-299">Endast fält med en avgränsning som innehåller ett avgränsnings tecken</span><span class="sxs-lookup"><span data-stu-id="654b6-299">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="654b6-300">Den här parametern lades till i PowerShell 7,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-300">This parameter was added in PowerShell 7.0.</span></span>

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

### <span data-ttu-id="654b6-301">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="654b6-301">CommonParameters</span></span>

<span data-ttu-id="654b6-302">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="654b6-302">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="654b6-303">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="654b6-303">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="654b6-304">INDATA</span><span class="sxs-lookup"><span data-stu-id="654b6-304">INPUTS</span></span>

### <span data-ttu-id="654b6-305">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="654b6-305">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="654b6-306">Du kan skicka ett objekt med ett ETS-kort (Extended Type System) till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="654b6-306">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="654b6-307">UTDATA</span><span class="sxs-lookup"><span data-stu-id="654b6-307">OUTPUTS</span></span>

### <span data-ttu-id="654b6-308">System. String</span><span class="sxs-lookup"><span data-stu-id="654b6-308">System.String</span></span>

<span data-ttu-id="654b6-309">CSV-listan skickas till den fil som anges i parametern Path.</span><span class="sxs-lookup"><span data-stu-id="654b6-309">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="654b6-310">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="654b6-310">NOTES</span></span>

<span data-ttu-id="654b6-311">`Export-CSV`Cmdleten konverterar de objekt som du skickar till en serie med CSV-strängar och sparar dem i den angivna text filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-311">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="654b6-312">Du kan använda `Export-CSV -IncludeTypeInformation` för att spara objekt i en CSV-fil och sedan använda `Import-Csv` cmdleten för att skapa objekt från texten i CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-312">You can use `Export-CSV -IncludeTypeInformation` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the text in the CSV file.</span></span>

<span data-ttu-id="654b6-313">I CSV-filen representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="654b6-313">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="654b6-314">Egenskaps värden konverteras till strängar med hjälp av metoden **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="654b6-314">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="654b6-315">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="654b6-315">The strings are represented by the property value name.</span></span> <span data-ttu-id="654b6-316">`Export-CSV -IncludeTypeInformation` exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="654b6-316">`Export-CSV -IncludeTypeInformation` does not export the methods of the object.</span></span>

<span data-ttu-id="654b6-317">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="654b6-317">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="654b6-318">Om **IncludeTypeInformation** används, innehåller den första strängen **#TYPE** informations huvud följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="654b6-318">If **IncludeTypeInformation** is used, the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span>
  <span data-ttu-id="654b6-319">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="654b6-319">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="654b6-320">Om **IncludeTypeInformation** inte används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="654b6-320">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="654b6-321">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="654b6-321">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="654b6-322">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="654b6-322">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="654b6-323">Från och med PowerShell 6,0 är standard beteendet för `Export-CSV` att inte inkludera **#TYPE** information i CSV-och **NoTypeInformation** är underförstådd.</span><span class="sxs-lookup"><span data-stu-id="654b6-323">Beginning with PowerShell 6.0 the default behavior of `Export-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="654b6-324">**IncludeTypeInformation** kan användas för att inkludera **#TYPE** information och emulera standard beteendet för `Export-CSV` före PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="654b6-324">**IncludeTypeInformation** can be used to include the **#TYPE** Information and emulate the default behavior of `Export-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="654b6-325">När du skickar flera objekt till `Export-CSV` `Export-CSV` ordnas filen baserat på egenskaperna för det första objektet som du skickar.</span><span class="sxs-lookup"><span data-stu-id="654b6-325">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="654b6-326">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="654b6-326">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="654b6-327">Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.</span><span class="sxs-lookup"><span data-stu-id="654b6-327">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="654b6-328">Du kan använda `Import-Csv` cmdleten för att återskapa objekt från CSV-strängarna i filerna.</span><span class="sxs-lookup"><span data-stu-id="654b6-328">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="654b6-329">De resulterande objekten är CSV-versioner av de ursprungliga objekten som består av sträng representationer av egenskapsvärdena och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="654b6-329">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="654b6-330">`ConvertTo-Csv` `ConvertFrom-Csv` Cmdletarna och konverterar objekt till CSV-strängar och från CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="654b6-330">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="654b6-331">`Export-CSV` är detsamma som `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="654b6-331">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="654b6-332">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="654b6-332">RELATED LINKS</span></span>

[<span data-ttu-id="654b6-333">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="654b6-333">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="654b6-334">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="654b6-334">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="654b6-335">Format-Table</span><span class="sxs-lookup"><span data-stu-id="654b6-335">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="654b6-336">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="654b6-336">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="654b6-337">Select-Object</span><span class="sxs-lookup"><span data-stu-id="654b6-337">Select-Object</span></span>](Select-Object.md)
