---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Csv
ms.openlocfilehash: 17c3ef3046ba8f0cca9a85cf41aaf683212a58e9
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913350"
---
# <span data-ttu-id="c0da8-102">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="c0da8-102">Export-Csv</span></span>

## <span data-ttu-id="c0da8-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c0da8-103">SYNOPSIS</span></span>
<span data-ttu-id="c0da8-104">Konverterar objekt till en serie med kommaavgränsade värde strängar (CSV) och sparar strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-104">Converts objects into a series of comma-separated value (CSV) strings and saves the strings to a file.</span></span>

## <span data-ttu-id="c0da8-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0da8-105">SYNTAX</span></span>

### <span data-ttu-id="c0da8-106">Avgränsare (standard)</span><span class="sxs-lookup"><span data-stu-id="c0da8-106">Delimiter (Default)</span></span>

```
Export-Csv [[-Path] <string>] [[-Delimiter] <char>] -InputObject <psobject> [-LiteralPath <string>]
 [-Force] [-NoClobber] [-Encoding <string>] [-Append] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="c0da8-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="c0da8-107">UseCulture</span></span>

```
Export-Csv [[-Path] <string>] -InputObject <psobject> [-LiteralPath <string>] [-Force] [-NoClobber]
 [-Encoding <string>] [-Append] [-UseCulture] [-NoTypeInformation] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="c0da8-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c0da8-108">DESCRIPTION</span></span>

<span data-ttu-id="c0da8-109">`Export-CSV`Cmdleten skapar en CSV-fil med de objekt som du skickar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-109">The `Export-CSV` cmdlet creates a CSV file of the objects that you submit.</span></span> <span data-ttu-id="c0da8-110">Varje objekt är en rad som innehåller en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c0da8-110">Each object is a row that includes a comma-separated list of the object's property values.</span></span> <span data-ttu-id="c0da8-111">Du kan använda `Export-CSV` cmdleten för att skapa kalkyl blad och dela data med program som accepterar CSV-filer som indata.</span><span class="sxs-lookup"><span data-stu-id="c0da8-111">You can use the `Export-CSV` cmdlet to create spreadsheets and share data with programs that accept CSV files as input.</span></span>

<span data-ttu-id="c0da8-112">Formatera inte objekt innan du skickar dem till- `Export-CSV` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-112">Do not format objects before sending them to the `Export-CSV` cmdlet.</span></span> <span data-ttu-id="c0da8-113">Om `Export-CSV` tar emot formaterade objekt, innehåller CSV-filen format egenskaper i stället för objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-113">If `Export-CSV` receives formatted objects the CSV file contains the format properties rather than the object properties.</span></span> <span data-ttu-id="c0da8-114">Om du bara vill exportera markerade egenskaper för ett objekt använder du `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-114">To export only selected properties of an object, use the `Select-Object` cmdlet.</span></span>

## <span data-ttu-id="c0da8-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c0da8-115">EXAMPLES</span></span>

### <span data-ttu-id="c0da8-116">Exempel 1: Exportera process egenskaper till en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="c0da8-116">Example 1: Export process properties to a CSV file</span></span>

<span data-ttu-id="c0da8-117">I det här exemplet väljs **bearbeta** objekt med vissa egenskaper, och objekten exporteras till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-117">This example selects **Process** objects with specific properties, exports the objects to a CSV file.</span></span>

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

<span data-ttu-id="c0da8-118">`Get-Process`Cmdlet: en hämtar **process** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-118">The `Get-Process` cmdlet gets the **Process** objects.</span></span> <span data-ttu-id="c0da8-119">Parametern **Name** filtrerar utdata så att endast process objekt för Wmiprvse tas med.</span><span class="sxs-lookup"><span data-stu-id="c0da8-119">The **Name** parameter filters the output to include only the WmiPrvSE process objects.</span></span> <span data-ttu-id="c0da8-120">Process objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-120">The process objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="c0da8-121">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av process objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-121">`Select-Object` uses the **Property** parameter to select a subset of process object properties.</span></span> <span data-ttu-id="c0da8-122">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-122">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-123">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-123">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="c0da8-124">Parametern **Path** anger att WmiData.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-124">The **Path** parameter specifies that the WmiData.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-125">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-125">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-126">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-126">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-127">Exempel 2: exportera processer till en kommaavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="c0da8-127">Example 2: Export processes to a comma-delimited file</span></span>

<span data-ttu-id="c0da8-128">Det här exemplet **hämtar objekt och exporterar objekten till** en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-128">This example gets **Process** objects and exports the objects to a CSV file.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="c0da8-129">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-129">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="c0da8-130">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-130">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-131">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-131">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="c0da8-132">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-132">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-133">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-133">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-134">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-134">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-135">Exempel 3: exportera processer till en semikolonavgränsad fil</span><span class="sxs-lookup"><span data-stu-id="c0da8-135">Example 3: Export processes to a semicolon delimited file</span></span>

<span data-ttu-id="c0da8-136">Det här exemplet **hämtar objekt och exporterar objekten till** en fil med semikolon avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c0da8-136">This example gets **Process** objects and exports the objects to a file with a semicolon delimiter.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv -Delimiter ';' -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name";"SI";"Handles";"VM";"WS";"PM";"NPM";"Path";"Parent";"Company";"CPU";"FileVersion"; ...
"ApplicationFrameHost";"4";"509";"2203595321344";"34807808";"21770240";"29504"; ...
```

<span data-ttu-id="c0da8-137">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-137">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="c0da8-138">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-138">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-139">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-139">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="c0da8-140">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-140">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-141">Parametern **delimiter** anger ett semikolon för att avgränsa sträng värden.</span><span class="sxs-lookup"><span data-stu-id="c0da8-141">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="c0da8-142">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-142">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-143">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-143">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-144">Exempel 4: exportera processer med nuvarande kulturs List avgränsare</span><span class="sxs-lookup"><span data-stu-id="c0da8-144">Example 4: Export processes using the current culture's list separator</span></span>

<span data-ttu-id="c0da8-145">Det här exemplet **hämtar objekt och exporterar objekten till** en fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-145">This example gets **Process** objects and exports the objects to a file.</span></span> <span data-ttu-id="c0da8-146">Avgränsaren är den aktuella kulturen List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c0da8-146">The delimiter is the current culture's list separator.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-Process | Export-Csv -Path .\Processes.csv -UseCulture -NoTypeInformation
Get-Content -Path .\Processes.csv
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","511","2203597099008","35364864","21979136","30048", ...
```

<span data-ttu-id="c0da8-147">`Get-Culture`Cmdleten använder de kapslade egenskaperna **Textinfo** och **ListSeparator** och visar den aktuella kulturen som är standard för List avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c0da8-147">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="c0da8-148">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-148">The `Get-Process` cmdlet gets **Process** objects.</span></span>
<span data-ttu-id="c0da8-149">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-149">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-150">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-150">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="c0da8-151">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-151">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-152">Parametern **UseCulture** använder aktuell kulturs standard List avgränsare som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c0da8-152">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="c0da8-153">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-153">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-154">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-154">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-155">Exempel 5: exportera processer med typ information</span><span class="sxs-lookup"><span data-stu-id="c0da8-155">Example 5: Export processes with type information</span></span>

<span data-ttu-id="c0da8-156">Det här exemplet förklarar hur du inkluderar **#TYPE** rubrik information i en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-156">This example explains how to include the **#TYPE** header information in a CSV file.</span></span> <span data-ttu-id="c0da8-157">**#TYPEs** huvudet är standardvärdet i tidigare versioner än PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="c0da8-157">The **#TYPE** header is the default in versions prior to PowerShell 6.0.</span></span>

```powershell
Get-Process | Export-Csv -Path .\Processes.csv
Get-Content -Path .\Processes.csv
```

```Output
#TYPE System.Diagnostics.Process
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"ApplicationFrameHost","4","507","2203595001856","35139584","20934656","29504", ...
```

<span data-ttu-id="c0da8-158">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-158">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="c0da8-159">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-159">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-160">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-160">`Export-Csv` converts the process objects to a series of CSV strings.</span></span>
<span data-ttu-id="c0da8-161">Parametern **Path** anger att Processes.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-161">The **Path** parameter specifies that the Processes.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-162">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-162">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-163">Exempel 6: exportera och lägga till objekt i en CSV-fil</span><span class="sxs-lookup"><span data-stu-id="c0da8-163">Example 6: Export and append objects to a CSV file</span></span>

<span data-ttu-id="c0da8-164">Det här exemplet beskriver hur du exporterar objekt till en CSV-fil och använder parametern **APPEND** för att lägga till objekt i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-164">This example describes how to export objects to a CSV file and use the **Append** parameter to add objects to an existing file.</span></span>

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

<span data-ttu-id="c0da8-165">`Get-Service`Cmdlet: en hämtar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-165">The `Get-Service` cmdlet gets service objects.</span></span> <span data-ttu-id="c0da8-166">Parametern **DisplayName** returnerar tjänster som innehåller Word-programmet.</span><span class="sxs-lookup"><span data-stu-id="c0da8-166">The **DisplayName** parameter returns services that contain the word Application.</span></span> <span data-ttu-id="c0da8-167">Tjänst objekt skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-167">The service objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="c0da8-168">`Select-Object` använder **egenskaps** parametern för att ange egenskaperna **DisplayName** och **status** .</span><span class="sxs-lookup"><span data-stu-id="c0da8-168">`Select-Object` uses the **Property** parameter to specify the **DisplayName** and **Status** properties.</span></span> <span data-ttu-id="c0da8-169">`$AppService`Variabeln lagrar objekten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-169">The `$AppService` variable stores the objects.</span></span>

<span data-ttu-id="c0da8-170">`$AppService`Objekten skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-170">The `$AppService` objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-171">`Export-Csv` konverterar tjänst objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-171">`Export-Csv` converts the service objects to a series of CSV strings.</span></span> <span data-ttu-id="c0da8-172">Parametern **Path** anger att Services.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-172">The **Path** parameter specifies that the Services.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-173">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-173">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-174">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-174">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

<span data-ttu-id="c0da8-175">`Get-Service` `Select-Object` Cmdletarna och upprepas för tjänster som innehåller ordet Windows.</span><span class="sxs-lookup"><span data-stu-id="c0da8-175">The `Get-Service` and `Select-Object` cmdlets are repeated for services that contain the word Windows.</span></span> <span data-ttu-id="c0da8-176">`$WinService`Variabeln lagrar tjänst objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-176">The `$WinService` variable stores the service objects.</span></span> <span data-ttu-id="c0da8-177">`Export-Csv`Cmdleten använder parametern **APPEND** för att ange att `$WinService` objekten läggs till i den befintliga Services.csvs filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-177">The `Export-Csv` cmdlet uses the **Append** parameter to specify that the `$WinService` objects are added to the existing Services.csv file.</span></span> <span data-ttu-id="c0da8-178">`Get-Content`Cmdleten upprepas för att visa den uppdaterade filen som innehåller de data som lagts till.</span><span class="sxs-lookup"><span data-stu-id="c0da8-178">The `Get-Content` cmdlet is repeated to display the updated file that includes the appended data.</span></span>

### <span data-ttu-id="c0da8-179">Exempel 7: format-cmdleten i en pipeline skapar oväntade resultat</span><span class="sxs-lookup"><span data-stu-id="c0da8-179">Example 7: Format cmdlet within a pipeline creates unexpected results</span></span>

<span data-ttu-id="c0da8-180">Det här exemplet visar varför det är viktigt att inte använda en format-cmdlet i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="c0da8-180">This example shows why it is important not to use a format cmdlet within a pipeline.</span></span> <span data-ttu-id="c0da8-181">Felsök pipeline-syntaxen när oväntade utdata tas emot.</span><span class="sxs-lookup"><span data-stu-id="c0da8-181">When unexpected output is received, troubleshoot the pipeline syntax.</span></span>

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

<span data-ttu-id="c0da8-182">`Get-Date`Cmdlet: en hämtar **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="c0da8-182">The `Get-Date` cmdlet gets the **DateTime** object.</span></span> <span data-ttu-id="c0da8-183">Objektet skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-183">The object is sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="c0da8-184">`Select-Object` använder **egenskaps** parametern för att välja en delmängd av objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-184">`Select-Object` uses the **Property** parameter to select a subset of object properties.</span></span> <span data-ttu-id="c0da8-185">Objektet skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-185">The object is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-186">`Export-Csv` konverterar objektet till ett CSV-format.</span><span class="sxs-lookup"><span data-stu-id="c0da8-186">`Export-Csv` converts the object to a CSV format.</span></span> <span data-ttu-id="c0da8-187">Parametern **Path** anger att DateTime.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-187">The **Path** parameter specifies that the DateTime.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-188">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-188">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-189">`Get-Content`Cmdleten använder parametern **Path** för att Visa CSV-filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-189">The `Get-Content` cmdlet uses the **Path** parameter to display the CSV file located in the current directory.</span></span>

<span data-ttu-id="c0da8-190">När `Format-Table` cmdleten används i pipelinen för att välja egenskaper tas oväntade resultat emot.</span><span class="sxs-lookup"><span data-stu-id="c0da8-190">When the `Format-Table` cmdlet is used within the pipeline to select properties unexpected results are received.</span></span> <span data-ttu-id="c0da8-191">`Format-Table` skickar tabell formats objekt ned pipelinen till `Export-Csv` cmdleten i stället för **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="c0da8-191">`Format-Table` sends table format objects down the pipeline to the `Export-Csv` cmdlet rather than the **DateTime** object.</span></span> <span data-ttu-id="c0da8-192">`Export-Csv` konverterar tabell formats objekt till en serie CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-192">`Export-Csv` converts the table format objects to a series of CSV strings.</span></span> <span data-ttu-id="c0da8-193">`Get-Content`Cmdleten visar CSV-filen som innehåller tabell formats objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-193">The `Get-Content` cmdlet displays the CSV file which contains the table format objects.</span></span>

### <span data-ttu-id="c0da8-194">Exempel 8: använda Force-parametern för att skriva över skrivskyddade filer</span><span class="sxs-lookup"><span data-stu-id="c0da8-194">Example 8: Using the Force parameter to overwrite read-only files</span></span>

<span data-ttu-id="c0da8-195">Det här exemplet skapar en tom skrivskyddad fil och använder **Force** -parametern för att uppdatera filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-195">This example creates an empty, read-only file and uses the **Force** parameter to update the file.</span></span>

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

<span data-ttu-id="c0da8-196">`New-Item`Cmdleten använder parametrarna **Path** och **ItemType** för att skapa ReadOnly.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-196">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the ReadOnly.csv file in the current directory.</span></span> <span data-ttu-id="c0da8-197">`Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.</span><span class="sxs-lookup"><span data-stu-id="c0da8-197">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to true.</span></span> <span data-ttu-id="c0da8-198">`Get-Process`Cmdleten **bearbetar** objekt.</span><span class="sxs-lookup"><span data-stu-id="c0da8-198">The `Get-Process` cmdlet gets **Process** objects.</span></span> <span data-ttu-id="c0da8-199">Process objekt skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-199">The process objects are sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-200">`Export-Csv` konverterar process objekt till en serie med CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-200">`Export-Csv` converts the process objects to a series of CSV strings.</span></span> <span data-ttu-id="c0da8-201">Parametern **Path** anger att ReadOnly.csv-filen sparas i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-201">The **Path** parameter specifies that the ReadOnly.csv file is saved in the current directory.</span></span> <span data-ttu-id="c0da8-202">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-202">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span> <span data-ttu-id="c0da8-203">Utdata visar att filen inte har skrivits eftersom åtkomst nekas.</span><span class="sxs-lookup"><span data-stu-id="c0da8-203">The output shows that the file is not written because access is denied.</span></span>

<span data-ttu-id="c0da8-204">Parametern **Force** läggs till i `Export-Csv` cmdleten för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-204">The **Force** parameter is added to the `Export-Csv` cmdlet to force the export to write to the file.</span></span> <span data-ttu-id="c0da8-205">`Get-Content`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-205">The `Get-Content` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

### <span data-ttu-id="c0da8-206">Exempel 9: använda Force-parametern med append</span><span class="sxs-lookup"><span data-stu-id="c0da8-206">Example 9: Using the Force parameter with Append</span></span>

<span data-ttu-id="c0da8-207">I det här exemplet visas hur du använder **Force** -och **APPEND** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-207">This example shows how to use the **Force** and **Append** parameters.</span></span> <span data-ttu-id="c0da8-208">När dessa parametrar kombineras, kan avvikande objekt egenskaper skrivas till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-208">When these parameters are combined, mismatched object properties can be written to a CSV file.</span></span>

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

<span data-ttu-id="c0da8-209">Ett uttryck skapar **PSCustomObject** med **namn** och **versions** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c0da8-209">An expression creates the **PSCustomObject** with **Name** and **Version** properties.</span></span> <span data-ttu-id="c0da8-210">Värdena lagras i `$Content` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0da8-210">The values are stored in the `$Content` variable.</span></span> <span data-ttu-id="c0da8-211">`$Content`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-211">The `$Content` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-212">`Export-Csv` använder parametern **Path** och sparar ParmFile.csv-filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-212">`Export-Csv` uses the **Path** parameter and saves the ParmFile.csv file in the current directory.</span></span> <span data-ttu-id="c0da8-213">Parametern **NoTypeInformation** tar bort **#TYPE** informations huvud från CSV-utdata och krävs inte i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="c0da8-213">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

<span data-ttu-id="c0da8-214">Ett annat uttryck skapar en **PSCustomObject** med egenskaperna **namn** och **utgåva** .</span><span class="sxs-lookup"><span data-stu-id="c0da8-214">Another expression creates a **PSCustomObject** with the **Name** and **Edition** properties.</span></span> <span data-ttu-id="c0da8-215">Värdena lagras i `$AdditionalContent` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0da8-215">The values are stored in the `$AdditionalContent` variable.</span></span> <span data-ttu-id="c0da8-216">`$AdditionalContent`Variabeln skickas ned pipelinen till `Export-Csv` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-216">The `$AdditionalContent` variable is sent down the pipeline to the `Export-Csv` cmdlet.</span></span> <span data-ttu-id="c0da8-217">Parametern **APPEND** används för att lägga till data i filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-217">The **Append** parameter is used to add the data to the file.</span></span> <span data-ttu-id="c0da8-218">Det går inte att lägga till eftersom det finns ett matchnings fel för egenskaps namn mellan **version** och **utgåva**.</span><span class="sxs-lookup"><span data-stu-id="c0da8-218">The append fails because there is a property name mismatch between **Version** and **Edition**.</span></span>

<span data-ttu-id="c0da8-219">`Export-Csv`Parametern cmdlet **Force** används för att tvinga exporten att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-219">The `Export-Csv` cmdlet **Force** parameter is used to force the export to write to the file.</span></span> <span data-ttu-id="c0da8-220">Egenskapen **Edition** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="c0da8-220">The **Edition** property is discarded.</span></span> <span data-ttu-id="c0da8-221">`Import-Csv`Cmdleten använder parametern **Path** för att visa filen som finns i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-221">The `Import-Csv` cmdlet uses the **Path** parameter to display the file located in the current directory.</span></span>

## <span data-ttu-id="c0da8-222">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c0da8-222">PARAMETERS</span></span>

### <span data-ttu-id="c0da8-223">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="c0da8-223">-Append</span></span>

<span data-ttu-id="c0da8-224">Använd den här parametern för att `Export-CSV` lägga till CSV-utdata i slutet av den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-224">Use this parameter so that `Export-CSV` adds CSV output to the end of the specified file.</span></span> <span data-ttu-id="c0da8-225">Utan den här parametern `Export-CSV` ersätter filens innehåll utan varning.</span><span class="sxs-lookup"><span data-stu-id="c0da8-225">Without this parameter, `Export-CSV` replaces the file contents without warning.</span></span>

<span data-ttu-id="c0da8-226">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0da8-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0da8-227">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="c0da8-227">-Delimiter</span></span>

<span data-ttu-id="c0da8-228">Anger en avgränsare för att avgränsa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c0da8-228">Specifies a delimiter to separate the property values.</span></span> <span data-ttu-id="c0da8-229">Standardvärdet är ett kommatecken ( `,` ).</span><span class="sxs-lookup"><span data-stu-id="c0da8-229">The default is a comma (`,`).</span></span> <span data-ttu-id="c0da8-230">Ange ett tecken, till exempel ett kolon ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="c0da8-230">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="c0da8-231">Om du vill ange ett semikolon ( `;` ), omger du det med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c0da8-231">To specify a semicolon (`;`), enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="c0da8-232">-Encoding</span><span class="sxs-lookup"><span data-stu-id="c0da8-232">-Encoding</span></span>

<span data-ttu-id="c0da8-233">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-233">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="c0da8-234">Standardvärdet är `ASCII`.</span><span class="sxs-lookup"><span data-stu-id="c0da8-234">The default value is `ASCII`.</span></span>

<span data-ttu-id="c0da8-235">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="c0da8-235">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="c0da8-236">`ASCII` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="c0da8-236">`ASCII` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="c0da8-237">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-237">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="c0da8-238">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="c0da8-238">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="c0da8-239">`OEM` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="c0da8-239">`OEM` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="c0da8-240">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="c0da8-240">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="c0da8-241">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="c0da8-241">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="c0da8-242">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c0da8-242">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="c0da8-243">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="c0da8-243">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: ASCII
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0da8-244">-Force</span><span class="sxs-lookup"><span data-stu-id="c0da8-244">-Force</span></span>

<span data-ttu-id="c0da8-245">Med den här parametern kan `Export-Csv` du skriva över filer med **skrivskyddat** attribut.</span><span class="sxs-lookup"><span data-stu-id="c0da8-245">This parameter allows `Export-Csv` to overwrite files with the **Read Only** attribute.</span></span>

<span data-ttu-id="c0da8-246">När **tvinga** -och **tilläggs** parametrar kombineras, kan objekt som innehåller felmatchade egenskaper SKRIVAs till en CSV-fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-246">When **Force** and **Append** parameters are combined, objects that contain mismatched properties can be written to a CSV file.</span></span> <span data-ttu-id="c0da8-247">Endast egenskaper som matchar skrivs till filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-247">Only the properties that match are written to the file.</span></span> <span data-ttu-id="c0da8-248">De egenskaper som matchar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="c0da8-248">The mismatched properties are discarded.</span></span>

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

### <span data-ttu-id="c0da8-249">– InputObject</span><span class="sxs-lookup"><span data-stu-id="c0da8-249">-InputObject</span></span>

<span data-ttu-id="c0da8-250">Anger de objekt som ska exporteras som CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-250">Specifies the objects to export as CSV strings.</span></span> <span data-ttu-id="c0da8-251">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-251">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="c0da8-252">Du kan också skicka pipe-objekt till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="c0da8-252">You can also pipe objects to `Export-CSV`.</span></span>

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

### <span data-ttu-id="c0da8-253">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0da8-253">-LiteralPath</span></span>

<span data-ttu-id="c0da8-254">Anger sökvägen till CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-254">Specifies the path to the CSV output file.</span></span> <span data-ttu-id="c0da8-255">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c0da8-255">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="c0da8-256">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c0da8-256">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c0da8-257">Om sökvägen innehåller escape-tecken använder du enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c0da8-257">If the path includes escape characters, use single quotation marks.</span></span> <span data-ttu-id="c0da8-258">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="c0da8-258">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c0da8-259">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="c0da8-259">-NoClobber</span></span>

<span data-ttu-id="c0da8-260">Använd den här parametern så att `Export-CSV` ingen befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="c0da8-260">Use this parameter so that `Export-CSV` does not overwrite an existing file.</span></span> <span data-ttu-id="c0da8-261">Om filen finns på den angivna sökvägen `Export-CSV` skrivs filen som standard utan varning.</span><span class="sxs-lookup"><span data-stu-id="c0da8-261">By default, if the file exists in the specified path, `Export-CSV` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="c0da8-262">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="c0da8-262">-NoTypeInformation</span></span>

<span data-ttu-id="c0da8-263">Tar bort **#TYPE** informations huvud från utdata.</span><span class="sxs-lookup"><span data-stu-id="c0da8-263">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="c0da8-264">Den här parametern blev standard i PowerShell 6,0 och ingår för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="c0da8-264">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="c0da8-265">-Path</span><span class="sxs-lookup"><span data-stu-id="c0da8-265">-Path</span></span>

<span data-ttu-id="c0da8-266">En obligatorisk parameter som anger den plats där du vill spara CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-266">A required parameter that specifies the location to save the CSV output file.</span></span>

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

### <span data-ttu-id="c0da8-267">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="c0da8-267">-UseCulture</span></span>

<span data-ttu-id="c0da8-268">Använder list avgränsaren för den aktuella kulturen som objekt avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c0da8-268">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="c0da8-269">Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .</span><span class="sxs-lookup"><span data-stu-id="c0da8-269">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="c0da8-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c0da8-270">-Confirm</span></span>

<span data-ttu-id="c0da8-271">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0da8-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="c0da8-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c0da8-272">-WhatIf</span></span>

<span data-ttu-id="c0da8-273">Förhindrar att cmdleten bearbetas eller gör ändringar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-273">Prevents the cmdlet from being processed or making changes.</span></span> <span data-ttu-id="c0da8-274">Utdata visar vad som händer om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="c0da8-274">The output shows what would happen if the cmdlet were run.</span></span>

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

### <span data-ttu-id="c0da8-275">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0da8-275">CommonParameters</span></span>

<span data-ttu-id="c0da8-276">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0da8-276">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0da8-277">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0da8-277">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0da8-278">INDATA</span><span class="sxs-lookup"><span data-stu-id="c0da8-278">INPUTS</span></span>

### <span data-ttu-id="c0da8-279">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="c0da8-279">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c0da8-280">Du kan skicka ett objekt med ett ETS-kort (Extended Type System) till `Export-CSV` .</span><span class="sxs-lookup"><span data-stu-id="c0da8-280">You can pipe any object with an Extended Type System (ETS) adapter to `Export-CSV`.</span></span>

## <span data-ttu-id="c0da8-281">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c0da8-281">OUTPUTS</span></span>

### <span data-ttu-id="c0da8-282">System. String</span><span class="sxs-lookup"><span data-stu-id="c0da8-282">System.String</span></span>

<span data-ttu-id="c0da8-283">CSV-listan skickas till den fil som anges i parametern Path.</span><span class="sxs-lookup"><span data-stu-id="c0da8-283">The CSV list is sent to the file designated in the Path parameter.</span></span>

## <span data-ttu-id="c0da8-284">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c0da8-284">NOTES</span></span>

<span data-ttu-id="c0da8-285">`Export-CSV`Cmdleten konverterar de objekt som du skickar till en serie med CSV-strängar och sparar dem i den angivna text filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-285">The `Export-CSV` cmdlet converts the objects that you submit into a series of CSV strings and saves them in the specified text file.</span></span> <span data-ttu-id="c0da8-286">Du kan använda `Export-CSV` för att spara objekt i en CSV-fil och sedan använda `Import-Csv` cmdleten för att skapa objekt från CSV-filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-286">You can use `Export-CSV` to save objects in a CSV file and then use the `Import-Csv` cmdlet to create objects from the CSV file.</span></span>

<span data-ttu-id="c0da8-287">I CSV-filen representeras varje objekt av en kommaavgränsad lista med objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c0da8-287">In the CSV file, each object is represented by a comma-separated list of the property values of the object.</span></span> <span data-ttu-id="c0da8-288">Egenskaps värden konverteras till strängar med hjälp av metoden **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="c0da8-288">The property values are converted to strings using the **ToString()** method.</span></span> <span data-ttu-id="c0da8-289">Strängarna representeras av egenskaps värde namnet.</span><span class="sxs-lookup"><span data-stu-id="c0da8-289">The strings are represented by the property value name.</span></span> <span data-ttu-id="c0da8-290">' Exportera-CSV exporterar inte objektets metoder.</span><span class="sxs-lookup"><span data-stu-id="c0da8-290">\`Export-CSV does not export the methods of the object.</span></span>

<span data-ttu-id="c0da8-291">CSV-strängarna matas ut enligt följande:</span><span class="sxs-lookup"><span data-stu-id="c0da8-291">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="c0da8-292">Den första strängen innehåller som standard den **#TYPE** informations rubriken följt av objekt typens fullständigt kvalificerade namn.</span><span class="sxs-lookup"><span data-stu-id="c0da8-292">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="c0da8-293">Till exempel **#TYPE system. Diagnostics. process**.</span><span class="sxs-lookup"><span data-stu-id="c0da8-293">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="c0da8-294">Om **NoTypeInformation** används, innehåller den första strängen kolumn rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-294">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="c0da8-295">Rubrikerna innehåller det första objektets egenskaps namn som en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="c0da8-295">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="c0da8-296">De återstående strängarna innehåller kommaavgränsade listor över varje objekts egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c0da8-296">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="c0da8-297">När du skickar flera objekt till `Export-CSV` `Export-CSV` ordnas filen baserat på egenskaperna för det första objektet som du skickar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-297">When you submit multiple objects to `Export-CSV`, `Export-CSV` organizes the file based on the properties of the first object that you submit.</span></span> <span data-ttu-id="c0da8-298">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet null, som representeras av två kommatecken i följd.</span><span class="sxs-lookup"><span data-stu-id="c0da8-298">If the remaining objects do not have one of the specified properties, the property value of that object is null, as represented by two consecutive commas.</span></span> <span data-ttu-id="c0da8-299">Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.</span><span class="sxs-lookup"><span data-stu-id="c0da8-299">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

<span data-ttu-id="c0da8-300">Du kan använda `Import-Csv` cmdleten för att återskapa objekt från CSV-strängarna i filerna.</span><span class="sxs-lookup"><span data-stu-id="c0da8-300">You can use the `Import-Csv` cmdlet to recreate objects from the CSV strings in the files.</span></span> <span data-ttu-id="c0da8-301">De resulterande objekten är CSV-versioner av de ursprungliga objekten som består av sträng representationer av egenskapsvärdena och inga metoder.</span><span class="sxs-lookup"><span data-stu-id="c0da8-301">The resulting objects are CSV versions of the original objects that consist of string representations of the property values and no methods.</span></span>

<span data-ttu-id="c0da8-302">`ConvertTo-Csv` `ConvertFrom-Csv` Cmdletarna och konverterar objekt till CSV-strängar och från CSV-strängar.</span><span class="sxs-lookup"><span data-stu-id="c0da8-302">The `ConvertTo-Csv` and `ConvertFrom-Csv` cmdlets convert objects to CSV strings and from CSV strings.</span></span> <span data-ttu-id="c0da8-303">`Export-CSV` är detsamma som `ConvertTo-CSV` , förutom att det sparar CSV-strängarna i en fil.</span><span class="sxs-lookup"><span data-stu-id="c0da8-303">`Export-CSV` is the same as `ConvertTo-CSV`, except that it saves the CSV strings in a file.</span></span>

## <span data-ttu-id="c0da8-304">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c0da8-304">RELATED LINKS</span></span>

[<span data-ttu-id="c0da8-305">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="c0da8-305">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="c0da8-306">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="c0da8-306">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="c0da8-307">Format-Table</span><span class="sxs-lookup"><span data-stu-id="c0da8-307">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="c0da8-308">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="c0da8-308">Import-Csv</span></span>](Import-Csv.md)

[<span data-ttu-id="c0da8-309">Select-Object</span><span class="sxs-lookup"><span data-stu-id="c0da8-309">Select-Object</span></span>](Select-Object.md)
