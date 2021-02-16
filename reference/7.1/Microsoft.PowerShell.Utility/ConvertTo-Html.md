---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 1eade078765f93713da1f665e3ad6f062a1826d9
ms.sourcegitcommit: 9777152e026c47ba8d319593051416054cb62246
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/16/2021
ms.locfileid: "100529948"
---
# <span data-ttu-id="e6091-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="e6091-103">ConvertTo-Html</span></span>

## <span data-ttu-id="e6091-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e6091-104">SYNOPSIS</span></span>
<span data-ttu-id="e6091-105">Konverterar .NET-objekt till HTML som kan visas i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="e6091-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="e6091-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e6091-106">SYNTAX</span></span>

### <span data-ttu-id="e6091-107">Sida (standard)</span><span class="sxs-lookup"><span data-stu-id="e6091-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [-Meta <Hashtable>] [-Charset <String>] [-Transitional]
 [<CommonParameters>]
```

### <span data-ttu-id="e6091-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="e6091-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="e6091-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e6091-109">DESCRIPTION</span></span>

<span data-ttu-id="e6091-110">`ConvertTo-Html`Cmdleten konverterar .net-objekt till HTML som kan visas i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="e6091-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="e6091-111">Du kan använda den här cmdleten för att visa utdata från ett kommando på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="e6091-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="e6091-112">Du kan använda parametrarna för `ConvertTo-Html` för att välja objekt egenskaper, för att ange ett tabell-eller List format, för att ange HTML-sidans rubrik, lägga till text före och efter objektet och bara returnera tabellen eller List fragment, i stället för en strikt DTD-sida.</span><span class="sxs-lookup"><span data-stu-id="e6091-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="e6091-113">När du skickar flera objekt till `ConvertTo-Html` skapar PowerShell tabellen (eller listan) baserat på egenskaperna för det första objektet som du skickar.</span><span class="sxs-lookup"><span data-stu-id="e6091-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="e6091-114">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet en tom cell.</span><span class="sxs-lookup"><span data-stu-id="e6091-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="e6091-115">Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="e6091-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e6091-116">EXAMPLES</span></span>

### <span data-ttu-id="e6091-117">Exempel 1: skapa en webb sida för att visa datumet</span><span class="sxs-lookup"><span data-stu-id="e6091-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="e6091-118">Det här kommandot skapar en HTML-sida som visar egenskaperna för det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="e6091-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="e6091-119">Parametern **InputObject** används för att skicka resultatet av ett `Get-Date` kommando till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e6091-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="e6091-120">Exempel 2: skapa en webb sida för att Visa PowerShell-alias</span><span class="sxs-lookup"><span data-stu-id="e6091-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="e6091-121">Det här kommandot skapar en HTML-sida som visar PowerShell-alias i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="e6091-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="e6091-122">Kommandot använder `Get-Alias` cmdleten för att hämta alias.</span><span class="sxs-lookup"><span data-stu-id="e6091-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="e6091-123">Den använder pipeline-operatorn ( `|` ) för att skicka alias till `ConvertTo-Html` cmdleten, vilket skapar HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="e6091-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="e6091-124">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `aliases.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="e6091-125">Exempel 3: skapa en webb sida för att Visa PowerShell-händelser</span><span class="sxs-lookup"><span data-stu-id="e6091-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="e6091-126">Det här kommandot skapar en HTML-sida `pslog.htm` med namnet som visar händelserna i händelse loggen för Windows PowerShell på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e6091-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="e6091-127">Den använder `Get-EventLog` cmdleten för att hämta händelserna i Windows PowerShell-loggen och använder sedan pipeline-operatorn ( `|` ) för att skicka händelserna till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e6091-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="e6091-128">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="e6091-129">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="e6091-130">Exempel 4: skapa en webb sida för att visa processer</span><span class="sxs-lookup"><span data-stu-id="e6091-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="e6091-131">Dessa kommandon skapar och öppnar en HTML-sida som visar namn, sökväg och företag för processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="e6091-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="e6091-132">Det första kommandot använder `Get-Process` cmdleten för att hämta objekt som representerar de processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="e6091-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="e6091-133">Kommandot använder pipeline-operatorn ( `|` ) för att skicka process objekt till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e6091-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="e6091-134">Kommandot använder **egenskaps** parametern för att välja tre egenskaper för de process objekt som ska tas med i tabellen.</span><span class="sxs-lookup"><span data-stu-id="e6091-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="e6091-135">Kommandot använder **title** -parametern för att ange en rubrik för HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="e6091-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="e6091-136">Kommandot använder också `Out-File` cmdleten för att skicka den resulterande HTML-koden till en fil med namnet Proc.htm.</span><span class="sxs-lookup"><span data-stu-id="e6091-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="e6091-137">Det andra kommandot använder `Invoke-Item` cmdleten för att öppna `Proc.htm` i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="e6091-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="e6091-138">Exempel 5: skapa en webb sida för att Visa tjänst objekt</span><span class="sxs-lookup"><span data-stu-id="e6091-138">Example 5: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -CssUri "test.css"
```

```Output
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"  "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html>
<head>
<title>HTML TABLE</title>
<link rel="stylesheet" type="text/css" href="test.css" />
...
```

<span data-ttu-id="e6091-139">Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="e6091-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="e6091-140">Kommandot använder parametern **CssUri** för att ange en sammanhängande formatmall för HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="e6091-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="e6091-141">Parametern **CssUri** lägger till ytterligare en `<link rel="stylesheet" type="text/css" href="test.css">` tagg till den resulterande HTML-koden.</span><span class="sxs-lookup"><span data-stu-id="e6091-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="e6091-142">HREF-attributet i taggen innehåller namnet på format mal len.</span><span class="sxs-lookup"><span data-stu-id="e6091-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="e6091-143">Exempel 6: skapa en webb sida för att Visa tjänst objekt</span><span class="sxs-lookup"><span data-stu-id="e6091-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="e6091-144">Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="e6091-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="e6091-145">Kommandot använder parametern **as** för att ange ett List format.</span><span class="sxs-lookup"><span data-stu-id="e6091-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="e6091-146">Cmdleten `Out-File` skickar den resulterande HTML-koden till `Services.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="e6091-147">Exempel 7: skapa en webb tabell för det aktuella datumet</span><span class="sxs-lookup"><span data-stu-id="e6091-147">Example 7: Create a web table for the current date</span></span>

```powershell
Get-Date | ConvertTo-Html -Fragment
```

```Output
<table>
<colgroup>...</colgroup>
<tr><th>DisplayHint</th><th>DateTime</th><th>Date</th><th>Day</th><th>DayOfWeek</th><th>DayOfYear</th><th>Hour</th>
<th>Kind</th><th>Millisecond</th><th>Minute</th><th>Month</th><th>Second</th><th>Ticks</th><th>TimeOfDay</th><th>Year</th></tr>
<tr><td>DateTime</td><td>Monday, May 05, 2008 10:40:04 AM</td><td>5/5/2008 12:00:00 AM</td><td>5</td><td>Monday</td>
<td>126</td><td>10</td><td>Local</td><td>123</td><td>40</td><td>5</td><td>4</td><td>633455808041237213</td><td>10:40:04.12
37213</td><td>2008</td></tr>
</table>
```

<span data-ttu-id="e6091-148">Det här kommandot använder `ConvertTo-Html` för att generera en HTML-tabell för det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="e6091-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="e6091-149">Kommandot använder `Get-Date` cmdleten för att hämta det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="e6091-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="e6091-150">Den använder en pipeline-operator (|) för att skicka resultaten till- `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e6091-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="e6091-151">`ConvertTo-Html`Kommandot innehåller parametern **fragment** , som begränsar utdata till en HTML-tabell.</span><span class="sxs-lookup"><span data-stu-id="e6091-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="e6091-152">Därför utelämnas andra element på en HTML-sida, t `<HEAD>` `<BODY>` . ex. taggarna och.</span><span class="sxs-lookup"><span data-stu-id="e6091-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="e6091-153">Exempel 8: skapa en webb sida för att Visa PowerShell-händelser</span><span class="sxs-lookup"><span data-stu-id="e6091-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="e6091-154">Det här kommandot använder `Get-EventLog` cmdleten för att hämta händelser från händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6091-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="e6091-155">En pipeline-operator () används `|` för att skicka händelserna till `ConvertTo-Html` cmdleten, som konverterar händelserna till HTML-format.</span><span class="sxs-lookup"><span data-stu-id="e6091-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="e6091-156">`ConvertTo-Html`Kommandot använder **egenskaps** parametern för att endast välja **ID**, **nivå** och **aktivitets** egenskaper för händelsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID**, **Level**, and **Task** properties of the event.</span></span>

### <span data-ttu-id="e6091-157">Exempel 9: skapa en webb sida för att Visa angivna tjänster</span><span class="sxs-lookup"><span data-stu-id="e6091-157">Example 9: Create a web page to display specified services</span></span>

```powershell
$htmlParams = @{
  Title = "Windows Services: Server01"
  Body = Get-Date
  PreContent = "<P>Generated by Corporate IT</P>"
  PostContent = "For details, contact Corporate IT."
}
Get-Service A* |
  ConvertTo-Html @htmlParams |
    Out-File Services.htm
Invoke-Item Services.htm
```

<span data-ttu-id="e6091-158">Det här kommandot skapar och öppnar en webb sida som visar de tjänster på datorn som börjar med en. I används **title**-, **Body**-, **precontent**-och **PostContent** -parametrarna för `ConvertTo-Html` för att anpassa utdata.</span><span class="sxs-lookup"><span data-stu-id="e6091-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title**, **Body**, **PreContent**, and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="e6091-159">Den första delen av kommandot använder `Get-Service` cmdleten för att hämta tjänsterna på datorn som börjar med en. Kommandot använder en pipeline-operator ( `|` ) för att skicka resultaten till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e6091-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="e6091-160">Kommandot använder också `Out-File` cmdleten för att skicka utdata till Services.htm-filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="e6091-161">Ett semikolon ( `;` ) avslutar det första kommandot och startar ett andra kommando, som använder `Invoke-Item` cmdleten för att öppna `Services.htm` filen i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="e6091-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

### <span data-ttu-id="e6091-162">Exempel 10: Ange meta-egenskaperna och HTML-teckenuppsättningen</span><span class="sxs-lookup"><span data-stu-id="e6091-162">Example 10: Set the Meta properties and Charset of the HTML</span></span>

```powershell
Get-Service | ConvertTo-HTML -Meta @{
  refresh=10
  author="Author's Name"
  keywords="PowerShell, HTML, ConvertTo-HTML"
} -Charset "UTF-8"
```

<span data-ttu-id="e6091-163">Det här kommandot skapar HTML för en webb sida med metataggarna för uppdatering, författare och nyckelord.</span><span class="sxs-lookup"><span data-stu-id="e6091-163">This command creates the HTML for a webpage with the meta tags for refresh, author, and keywords.</span></span>
<span data-ttu-id="e6091-164">Teckenuppsättningen för sidan är inställd på UTF-8</span><span class="sxs-lookup"><span data-stu-id="e6091-164">The charset for the page is set to UTF-8</span></span>

### <span data-ttu-id="e6091-165">Exempel 11: Ange HTML till XHTML-över gångs-DTD</span><span class="sxs-lookup"><span data-stu-id="e6091-165">Example 11: Set the HTML to XHTML Transitional DTD</span></span>

```powershell
Get-Service | ConvertTo-HTML -Transitional
```

<span data-ttu-id="e6091-166">Det här kommandot anger DOCTYPE för den returnerade HTML-filen till XHTML-över gångs-DTD</span><span class="sxs-lookup"><span data-stu-id="e6091-166">This command sets the DOCTYPE of the returned HTML to XHTML Transitional DTD</span></span>

## <span data-ttu-id="e6091-167">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e6091-167">PARAMETERS</span></span>

### <span data-ttu-id="e6091-168">– Som</span><span class="sxs-lookup"><span data-stu-id="e6091-168">-As</span></span>

<span data-ttu-id="e6091-169">Anger om objektet är formaterat som en tabell eller en lista.</span><span class="sxs-lookup"><span data-stu-id="e6091-169">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="e6091-170">Giltiga värden är **Table** och **list**.</span><span class="sxs-lookup"><span data-stu-id="e6091-170">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="e6091-171">Standardvärdet är **Table**.</span><span class="sxs-lookup"><span data-stu-id="e6091-171">The default value is **Table**.</span></span>

<span data-ttu-id="e6091-172">**Table** -värdet genererar en HTML-tabell som liknar PowerShell-tabellens format.</span><span class="sxs-lookup"><span data-stu-id="e6091-172">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="e6091-173">Rubrik raden visar egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="e6091-173">The header row displays the property names.</span></span> <span data-ttu-id="e6091-174">Varje tabell rad representerar ett objekt och visar objektets värden för varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="e6091-174">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="e6091-175">**List** svärdet genererar en HTML-tabell med två kolumner för varje objekt som liknar PowerShell-List formatet.</span><span class="sxs-lookup"><span data-stu-id="e6091-175">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="e6091-176">Den första kolumnen visar egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="e6091-176">The first column displays the property name.</span></span> <span data-ttu-id="e6091-177">Den andra kolumnen visar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="e6091-177">The second column displays the property value.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Table, List

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-178">-Body</span><span class="sxs-lookup"><span data-stu-id="e6091-178">-Body</span></span>

<span data-ttu-id="e6091-179">Anger den text som ska läggas till efter den inledande `<BODY>` taggen.</span><span class="sxs-lookup"><span data-stu-id="e6091-179">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="e6091-180">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-180">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-181">-Teckenuppsättning</span><span class="sxs-lookup"><span data-stu-id="e6091-181">-Charset</span></span>

<span data-ttu-id="e6091-182">Anger text som ska läggas till i öppnings `<charset>` tag gen.</span><span class="sxs-lookup"><span data-stu-id="e6091-182">Specifies text to add to the opening `<charset>` tag.</span></span> <span data-ttu-id="e6091-183">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-183">By default, there is no text in that position.</span></span>

<span data-ttu-id="e6091-184">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e6091-184">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-185">-CssUri</span><span class="sxs-lookup"><span data-stu-id="e6091-185">-CssUri</span></span>

<span data-ttu-id="e6091-186">Anger Uniform Resource Identifier (URI) för det sammanhängande format bladet (CSS) som tillämpas på HTML-filen.</span><span class="sxs-lookup"><span data-stu-id="e6091-186">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="e6091-187">URI: n tas med i en Formatmallslänkar i utdata.</span><span class="sxs-lookup"><span data-stu-id="e6091-187">The URI is included in a style sheet link in the output.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Page
Aliases: cu, uri

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-188">– Fragment</span><span class="sxs-lookup"><span data-stu-id="e6091-188">-Fragment</span></span>

<span data-ttu-id="e6091-189">Genererar endast en HTML-tabell.</span><span class="sxs-lookup"><span data-stu-id="e6091-189">Generates only an HTML table.</span></span> <span data-ttu-id="e6091-190">Taggarna HTML, HEAD, TITLE och BODY utelämnas.</span><span class="sxs-lookup"><span data-stu-id="e6091-190">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Fragment
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-191">-Head</span><span class="sxs-lookup"><span data-stu-id="e6091-191">-Head</span></span>

<span data-ttu-id="e6091-192">Anger `<HEAD>` taggens innehåll.</span><span class="sxs-lookup"><span data-stu-id="e6091-192">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="e6091-193">Standardvärdet är `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="e6091-193">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="e6091-194">Om du använder **Head** -parametern ignoreras **title** -parametern.</span><span class="sxs-lookup"><span data-stu-id="e6091-194">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Page
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-195">– InputObject</span><span class="sxs-lookup"><span data-stu-id="e6091-195">-InputObject</span></span>

<span data-ttu-id="e6091-196">Anger de objekt som ska visas i HTML.</span><span class="sxs-lookup"><span data-stu-id="e6091-196">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="e6091-197">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="e6091-197">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="e6091-198">Om du använder den här parametern för att skicka flera objekt, till exempel alla tjänster på en dator, `ConvertTo-Html` skapar en tabell som visar egenskaperna för en samling eller en objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="e6091-198">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="e6091-199">Om du vill skapa en tabell med de enskilda objekten använder du pipeline-operatorn för att skicka objekten till `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="e6091-199">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-200">-Meta</span><span class="sxs-lookup"><span data-stu-id="e6091-200">-Meta</span></span>

<span data-ttu-id="e6091-201">Anger text som ska läggas till i öppnings `<meta>` tag gen.</span><span class="sxs-lookup"><span data-stu-id="e6091-201">Specifies text to add to the opening `<meta>` tag.</span></span> <span data-ttu-id="e6091-202">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-202">By default, there is no text in that position.</span></span>

<span data-ttu-id="e6091-203">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e6091-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-204">-PostContent</span><span class="sxs-lookup"><span data-stu-id="e6091-204">-PostContent</span></span>

<span data-ttu-id="e6091-205">Anger text som ska läggas till efter den avslutande `</TABLE>` taggen.</span><span class="sxs-lookup"><span data-stu-id="e6091-205">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="e6091-206">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-206">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-207">-För-innehåll</span><span class="sxs-lookup"><span data-stu-id="e6091-207">-PreContent</span></span>

<span data-ttu-id="e6091-208">Anger text som ska läggas till före öppnings `<TABLE>` tag gen.</span><span class="sxs-lookup"><span data-stu-id="e6091-208">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="e6091-209">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="e6091-209">By default, there is no text in that position.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-210">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="e6091-210">-Property</span></span>

<span data-ttu-id="e6091-211">Innehåller de angivna egenskaperna för objekten i HTML-koden.</span><span class="sxs-lookup"><span data-stu-id="e6091-211">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="e6091-212">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="e6091-212">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="e6091-213">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e6091-213">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="e6091-214">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="e6091-214">Valid key-value pairs are:</span></span>

- <span data-ttu-id="e6091-215">Namn (eller etikett) – `<string>` (lades till i PowerShell 6. x)</span><span class="sxs-lookup"><span data-stu-id="e6091-215">Name (or label) - `<string>` (added in PowerShell 6.x)</span></span>
- <span data-ttu-id="e6091-216">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="e6091-216">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="e6091-217">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="e6091-217">FormatString - `<string>`</span></span>
- <span data-ttu-id="e6091-218">Width- `<int32>` -måste vara större än `0`</span><span class="sxs-lookup"><span data-stu-id="e6091-218">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="e6091-219">Justering-värdet kan vara `Left` , `Center` eller `Right`</span><span class="sxs-lookup"><span data-stu-id="e6091-219">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="e6091-220">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="e6091-220">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-221">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="e6091-221">-Title</span></span>

<span data-ttu-id="e6091-222">Anger en rubrik för HTML-filen, det vill säga texten som visas mellan `<TITLE>` taggarna.</span><span class="sxs-lookup"><span data-stu-id="e6091-222">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

```yaml
Type: System.String
Parameter Sets: Page
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-223">– Över gång</span><span class="sxs-lookup"><span data-stu-id="e6091-223">-Transitional</span></span>

<span data-ttu-id="e6091-224">Ändrar **doctype** till **XHTML-över gångs-DTD**, standard- **doctype** är en **XHTML Strict DTD**.</span><span class="sxs-lookup"><span data-stu-id="e6091-224">Changes the **DOCTYPE** to **XHTML Transitional DTD**, Default **DOCTYPE** is **XHTML Strict DTD**.</span></span>

<span data-ttu-id="e6091-225">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e6091-225">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Page
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e6091-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e6091-226">CommonParameters</span></span>

<span data-ttu-id="e6091-227">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e6091-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e6091-228">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e6091-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e6091-229">INDATA</span><span class="sxs-lookup"><span data-stu-id="e6091-229">INPUTS</span></span>

### <span data-ttu-id="e6091-230">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e6091-230">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="e6091-231">Du kan skicka alla .NET-objekt till `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="e6091-231">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="e6091-232">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e6091-232">OUTPUTS</span></span>

### <span data-ttu-id="e6091-233">System. String eller System.Xml.Xmldokument</span><span class="sxs-lookup"><span data-stu-id="e6091-233">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="e6091-234">`ConvertTo-Html` Returnerar en serie med strängar som utgör giltig HTML.</span><span class="sxs-lookup"><span data-stu-id="e6091-234">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="e6091-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e6091-235">NOTES</span></span>

<span data-ttu-id="e6091-236">Om du vill använda den här cmdleten, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet.</span><span class="sxs-lookup"><span data-stu-id="e6091-236">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="e6091-237">När indatan består av flera objekt är resultatet av dessa två metoder ganska annorlunda.</span><span class="sxs-lookup"><span data-stu-id="e6091-237">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="e6091-238">När du rör flera objekt till en cmdlet skickar PowerShell objekten till cmdleten en i taget.</span><span class="sxs-lookup"><span data-stu-id="e6091-238">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="e6091-239">Därför `ConvertTo-Html` skapar en tabell som visar de enskilda objekten.</span><span class="sxs-lookup"><span data-stu-id="e6091-239">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="e6091-240">Om du till exempel rör processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen alla processer.</span><span class="sxs-lookup"><span data-stu-id="e6091-240">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="e6091-241">När du använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Html` tar emot dessa objekt som en samling eller som en matris.</span><span class="sxs-lookup"><span data-stu-id="e6091-241">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="e6091-242">Därför skapas en tabell som visar matrisen och dess egenskaper, inte objekten i matrisen.</span><span class="sxs-lookup"><span data-stu-id="e6091-242">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="e6091-243">Om du till exempel använder **InputObject** för att skicka processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen en objekt mat ris och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="e6091-243">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="e6091-244">För att följa den strikta XHTML DTD-koden ändras DOCTYPE-taggen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="e6091-244">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="e6091-245">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e6091-245">RELATED LINKS</span></span>

[<span data-ttu-id="e6091-246">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="e6091-246">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="e6091-247">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="e6091-247">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="e6091-248">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="e6091-248">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="e6091-249">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="e6091-249">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="e6091-250">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="e6091-250">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="e6091-251">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="e6091-251">Import-Clixml</span></span>](Import-Clixml.md)
