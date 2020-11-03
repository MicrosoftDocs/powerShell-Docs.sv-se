---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-html?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Html
ms.openlocfilehash: 618308bb03f47659b8fa932ac0bb029972546755
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93268952"
---
# <span data-ttu-id="7f15a-103">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="7f15a-103">ConvertTo-Html</span></span>

## <span data-ttu-id="7f15a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7f15a-104">SYNOPSIS</span></span>
<span data-ttu-id="7f15a-105">Konverterar .NET-objekt till HTML som kan visas i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="7f15a-105">Converts .NET objects into HTML that can be displayed in a Web browser.</span></span>

## <span data-ttu-id="7f15a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f15a-106">SYNTAX</span></span>

### <span data-ttu-id="7f15a-107">Sida (standard)</span><span class="sxs-lookup"><span data-stu-id="7f15a-107">Page (Default)</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [[-Body] <String[]>]
 [[-Head] <String[]>] [[-Title] <String>] [-As <String>] [-CssUri <Uri>] [-PostContent <String[]>]
 [-PreContent <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="7f15a-108">Fragment</span><span class="sxs-lookup"><span data-stu-id="7f15a-108">Fragment</span></span>

```
ConvertTo-Html [-InputObject <PSObject>] [[-Property] <Object[]>] [-As <String>] [-Fragment]
 [-PostContent <String[]>] [-PreContent <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7f15a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7f15a-109">DESCRIPTION</span></span>

<span data-ttu-id="7f15a-110">`ConvertTo-Html`Cmdleten konverterar .net-objekt till HTML som kan visas i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="7f15a-110">The `ConvertTo-Html` cmdlet converts .NET objects into HTML that can be displayed in a Web browser.</span></span> <span data-ttu-id="7f15a-111">Du kan använda den här cmdleten för att visa utdata från ett kommando på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="7f15a-111">You can use this cmdlet to display the output of a command in a Web page.</span></span>

<span data-ttu-id="7f15a-112">Du kan använda parametrarna för `ConvertTo-Html` för att välja objekt egenskaper, för att ange ett tabell-eller List format, för att ange HTML-sidans rubrik, lägga till text före och efter objektet och bara returnera tabellen eller List fragment, i stället för en strikt DTD-sida.</span><span class="sxs-lookup"><span data-stu-id="7f15a-112">You can use the parameters of `ConvertTo-Html` to select object properties, to specify a table or list format, to specify the HTML page title, to add text before and after the object, and to return only the table or list fragment, instead of a strict DTD page.</span></span>

<span data-ttu-id="7f15a-113">När du skickar flera objekt till `ConvertTo-Html` skapar PowerShell tabellen (eller listan) baserat på egenskaperna för det första objektet som du skickar.</span><span class="sxs-lookup"><span data-stu-id="7f15a-113">When you submit multiple objects to `ConvertTo-Html`, PowerShell creates the table (or list) based on the properties of the first object that you submit.</span></span> <span data-ttu-id="7f15a-114">Om de återstående objekten inte har en av de angivna egenskaperna, är egenskap svärdet för objektet en tom cell.</span><span class="sxs-lookup"><span data-stu-id="7f15a-114">If the remaining objects do not have one of the specified properties, the property value of that object is an empty cell.</span></span> <span data-ttu-id="7f15a-115">Om de återstående objekten har ytterligare egenskaper inkluderas inte dessa egenskaps värden i filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-115">If the remaining objects have additional properties, those property values are not included in the file.</span></span>

## <span data-ttu-id="7f15a-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7f15a-116">EXAMPLES</span></span>

### <span data-ttu-id="7f15a-117">Exempel 1: skapa en webb sida för att visa datumet</span><span class="sxs-lookup"><span data-stu-id="7f15a-117">Example 1: Create a web page to display the date</span></span>

```powershell
ConvertTo-Html -InputObject (Get-Date)
```

<span data-ttu-id="7f15a-118">Det här kommandot skapar en HTML-sida som visar egenskaperna för det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-118">This command creates an HTML page that displays the properties of the current date.</span></span> <span data-ttu-id="7f15a-119">Parametern **InputObject** används för att skicka resultatet av ett `Get-Date` kommando till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-119">It uses the **InputObject** parameter to submit the results of a `Get-Date` command to the `ConvertTo-Html` cmdlet.</span></span>

### <span data-ttu-id="7f15a-120">Exempel 2: skapa en webb sida för att Visa PowerShell-alias</span><span class="sxs-lookup"><span data-stu-id="7f15a-120">Example 2: Create a web page to display PowerShell aliases</span></span>

```powershell
Get-Alias | ConvertTo-Html | Out-File aliases.htm
Invoke-Item aliases.htm
```

<span data-ttu-id="7f15a-121">Det här kommandot skapar en HTML-sida som visar PowerShell-alias i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-121">This command creates an HTML page that lists the PowerShell aliases in the current console.</span></span>

<span data-ttu-id="7f15a-122">Kommandot använder `Get-Alias` cmdleten för att hämta alias.</span><span class="sxs-lookup"><span data-stu-id="7f15a-122">The command uses the `Get-Alias` cmdlet to get the aliases.</span></span> <span data-ttu-id="7f15a-123">Den använder pipeline-operatorn ( `|` ) för att skicka alias till `ConvertTo-Html` cmdleten, vilket skapar HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="7f15a-123">It uses the pipeline operator (`|`) to send the aliases to the `ConvertTo-Html` cmdlet, which creates the HTML page.</span></span> <span data-ttu-id="7f15a-124">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `aliases.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-124">The command also uses the `Out-File` cmdlet to send the HTML code to the `aliases.htm` file.</span></span>

### <span data-ttu-id="7f15a-125">Exempel 3: skapa en webb sida för att Visa PowerShell-händelser</span><span class="sxs-lookup"><span data-stu-id="7f15a-125">Example 3: Create a web page to display PowerShell events</span></span>

```powershell
`Get-EventLog` -LogName "Windows PowerShell" | ConvertTo-Html | Out-File pslog.htm
```

<span data-ttu-id="7f15a-126">Det här kommandot skapar en HTML-sida `pslog.htm` med namnet som visar händelserna i händelse loggen för Windows PowerShell på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7f15a-126">This command creates an HTML page called `pslog.htm` that displays the events in the Windows PowerShell event log on the local computer.</span></span>

<span data-ttu-id="7f15a-127">Den använder `Get-EventLog` cmdleten för att hämta händelserna i Windows PowerShell-loggen och använder sedan pipeline-operatorn ( `|` ) för att skicka händelserna till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-127">It uses the `Get-EventLog` cmdlet to get the events in the Windows PowerShell log and then uses the pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="7f15a-128">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-128">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

<span data-ttu-id="7f15a-129">Kommandot använder också `Out-File` cmdleten för att skicka HTML-koden till `pslog.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-129">The command also uses the `Out-File` cmdlet to send the HTML code to the `pslog.htm` file.</span></span>

### <span data-ttu-id="7f15a-130">Exempel 4: skapa en webb sida för att visa processer</span><span class="sxs-lookup"><span data-stu-id="7f15a-130">Example 4: Create a web page to display processes</span></span>

```powershell
Get-Process |
  ConvertTo-Html -Property Name, Path, Company -Title "Process Information" |
    Out-File proc.htm
Invoke-Item proc.htm
```

<span data-ttu-id="7f15a-131">Dessa kommandon skapar och öppnar en HTML-sida som visar namn, sökväg och företag för processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7f15a-131">These commands create and open an HTML page that lists the name, path, and company of the processes on the local computer.</span></span>

<span data-ttu-id="7f15a-132">Det första kommandot använder `Get-Process` cmdleten för att hämta objekt som representerar de processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="7f15a-132">The first command uses the `Get-Process` cmdlet to get objects that represent the processes running on the computer.</span></span> <span data-ttu-id="7f15a-133">Kommandot använder pipeline-operatorn ( `|` ) för att skicka process objekt till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-133">The command uses the pipeline operator (`|`) to send the process objects to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="7f15a-134">Kommandot använder **egenskaps** parametern för att välja tre egenskaper för de process objekt som ska tas med i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-134">The command uses the **Property** parameter to select three properties of the process objects to be included in the table.</span></span> <span data-ttu-id="7f15a-135">Kommandot använder **title** -parametern för att ange en rubrik för HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="7f15a-135">The command uses the **Title** parameter to specify a title for the HTML page.</span></span> <span data-ttu-id="7f15a-136">Kommandot använder också `Out-File` cmdleten för att skicka den resulterande HTML-koden till en fil med namnet Proc.htm.</span><span class="sxs-lookup"><span data-stu-id="7f15a-136">The command also uses the `Out-File` cmdlet to send the resulting HTML to a file named Proc.htm.</span></span>

<span data-ttu-id="7f15a-137">Det andra kommandot använder `Invoke-Item` cmdleten för att öppna `Proc.htm` i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="7f15a-137">The second command uses the `Invoke-Item` cmdlet to open the `Proc.htm` in the default browser.</span></span>

### <span data-ttu-id="7f15a-138">Exempel 5: skapa en webb sida för att Visa tjänst objekt</span><span class="sxs-lookup"><span data-stu-id="7f15a-138">Example 5: Create a web page to display service objects</span></span>

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

<span data-ttu-id="7f15a-139">Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="7f15a-139">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="7f15a-140">Kommandot använder parametern **CssUri** för att ange en sammanhängande formatmall för HTML-sidan.</span><span class="sxs-lookup"><span data-stu-id="7f15a-140">The command uses the **CssUri** parameter to specify a cascading style sheet for the HTML page.</span></span>

<span data-ttu-id="7f15a-141">Parametern **CssUri** lägger till ytterligare en `<link rel="stylesheet" type="text/css" href="test.css">` tagg till den resulterande HTML-koden.</span><span class="sxs-lookup"><span data-stu-id="7f15a-141">The **CssUri** parameter adds an additional `<link rel="stylesheet" type="text/css" href="test.css">` tag to the resulting HTML.</span></span> <span data-ttu-id="7f15a-142">HREF-attributet i taggen innehåller namnet på format mal len.</span><span class="sxs-lookup"><span data-stu-id="7f15a-142">The HREF attribute in the tag contains the name of the style sheet.</span></span>

### <span data-ttu-id="7f15a-143">Exempel 6: skapa en webb sida för att Visa tjänst objekt</span><span class="sxs-lookup"><span data-stu-id="7f15a-143">Example 6: Create a web page to display service objects</span></span>

```powershell
Get-Service | ConvertTo-Html -As LIST | Out-File services.htm
```

<span data-ttu-id="7f15a-144">Det här kommandot skapar en HTML-sida för de tjänst objekt som `Get-Service` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="7f15a-144">This command creates an HTML page of the service objects that the `Get-Service` cmdlet returns.</span></span> <span data-ttu-id="7f15a-145">Kommandot använder parametern **as** för att ange ett List format.</span><span class="sxs-lookup"><span data-stu-id="7f15a-145">The command uses the **As** parameter to specify a list format.</span></span> <span data-ttu-id="7f15a-146">Cmdleten `Out-File` skickar den resulterande HTML-koden till `Services.htm` filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-146">The cmdlet `Out-File` sends the resulting HTML to the `Services.htm` file.</span></span>

### <span data-ttu-id="7f15a-147">Exempel 7: skapa en webb tabell för det aktuella datumet</span><span class="sxs-lookup"><span data-stu-id="7f15a-147">Example 7: Create a web table for the current date</span></span>

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

<span data-ttu-id="7f15a-148">Det här kommandot använder `ConvertTo-Html` för att generera en HTML-tabell för det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-148">This command uses `ConvertTo-Html` to generate an HTML table of the current date.</span></span> <span data-ttu-id="7f15a-149">Kommandot använder `Get-Date` cmdleten för att hämta det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-149">The command uses the `Get-Date` cmdlet to get the current date.</span></span> <span data-ttu-id="7f15a-150">Den använder en pipeline-operator (|) för att skicka resultaten till- `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-150">It uses a pipeline operator (|) to send the results to the `ConvertTo-Html` cmdlet.</span></span>

<span data-ttu-id="7f15a-151">`ConvertTo-Html`Kommandot innehåller parametern **fragment** , som begränsar utdata till en HTML-tabell.</span><span class="sxs-lookup"><span data-stu-id="7f15a-151">The `ConvertTo-Html` command includes the **Fragment** parameter, which limits the output to an HTML table.</span></span> <span data-ttu-id="7f15a-152">Därför utelämnas andra element på en HTML-sida, t `<HEAD>` `<BODY>` . ex. taggarna och.</span><span class="sxs-lookup"><span data-stu-id="7f15a-152">As a result, the other elements of an HTML page, such as the `<HEAD>` and `<BODY>` tags, are omitted.</span></span>

### <span data-ttu-id="7f15a-153">Exempel 8: skapa en webb sida för att Visa PowerShell-händelser</span><span class="sxs-lookup"><span data-stu-id="7f15a-153">Example 8: Create a web page to display PowerShell events</span></span>

```powershell
Get-EventLog -Log "Windows PowerShell" | ConvertTo-Html -Property id, level, task
```

<span data-ttu-id="7f15a-154">Det här kommandot använder `Get-EventLog` cmdleten för att hämta händelser från händelse loggen i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7f15a-154">This command uses the `Get-EventLog` cmdlet to get events from the Windows PowerShell event log.</span></span>

<span data-ttu-id="7f15a-155">En pipeline-operator () används `|` för att skicka händelserna till `ConvertTo-Html` cmdleten, som konverterar händelserna till HTML-format.</span><span class="sxs-lookup"><span data-stu-id="7f15a-155">It uses a pipeline operator (`|`) to send the events to the `ConvertTo-Html` cmdlet, which converts the events to HTML format.</span></span>

<span data-ttu-id="7f15a-156">`ConvertTo-Html`Kommandot använder **egenskaps** parametern för att endast välja **ID** , **nivå** och **aktivitets** egenskaper för händelsen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-156">The `ConvertTo-Html` command uses the **Property** parameter to select only the **ID** , **Level** , and **Task** properties of the event.</span></span>

### <span data-ttu-id="7f15a-157">Exempel 9: skapa en webb sida för att Visa angivna tjänster</span><span class="sxs-lookup"><span data-stu-id="7f15a-157">Example 9: Create a web page to display specified services</span></span>

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

<span data-ttu-id="7f15a-158">Det här kommandot skapar och öppnar en webb sida som visar de tjänster på datorn som börjar med en. I används **title** -, **Body** -, **precontent** -och **PostContent** -parametrarna för `ConvertTo-Html` för att anpassa utdata.</span><span class="sxs-lookup"><span data-stu-id="7f15a-158">This command creates and opens a Web page that displays the services on the computer that begin with A. It uses the **Title** , **Body** , **PreContent** , and **PostContent** parameters of `ConvertTo-Html` to customize the output.</span></span>

<span data-ttu-id="7f15a-159">Den första delen av kommandot använder `Get-Service` cmdleten för att hämta tjänsterna på datorn som börjar med en. Kommandot använder en pipeline-operator ( `|` ) för att skicka resultaten till `ConvertTo-Html` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-159">The first part of the command uses the `Get-Service` cmdlet to get the services on the computer that begin with A. The command uses a pipeline operator (`|`) to send the results to the `ConvertTo-Html` cmdlet.</span></span> <span data-ttu-id="7f15a-160">Kommandot använder också `Out-File` cmdleten för att skicka utdata till Services.htm-filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-160">The command also uses the `Out-File` cmdlet to send the output to the Services.htm file.</span></span>

<span data-ttu-id="7f15a-161">Ett semikolon ( `;` ) avslutar det första kommandot och startar ett andra kommando, som använder `Invoke-Item` cmdleten för att öppna `Services.htm` filen i standard webbläsaren.</span><span class="sxs-lookup"><span data-stu-id="7f15a-161">A semicolon (`;`) ends the first command and starts a second command, which uses the `Invoke-Item` cmdlet to open the `Services.htm` file in the default browser.</span></span>

## <span data-ttu-id="7f15a-162">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7f15a-162">PARAMETERS</span></span>

### <span data-ttu-id="7f15a-163">– Som</span><span class="sxs-lookup"><span data-stu-id="7f15a-163">-As</span></span>

<span data-ttu-id="7f15a-164">Anger om objektet är formaterat som en tabell eller en lista.</span><span class="sxs-lookup"><span data-stu-id="7f15a-164">Determines whether the object is formatted as a table or a list.</span></span> <span data-ttu-id="7f15a-165">Giltiga värden är **Table** och **list**.</span><span class="sxs-lookup"><span data-stu-id="7f15a-165">Valid values are **Table** and **List**.</span></span> <span data-ttu-id="7f15a-166">Standardvärdet är **Table**.</span><span class="sxs-lookup"><span data-stu-id="7f15a-166">The default value is **Table**.</span></span>

<span data-ttu-id="7f15a-167">**Table** -värdet genererar en HTML-tabell som liknar PowerShell-tabellens format.</span><span class="sxs-lookup"><span data-stu-id="7f15a-167">The **Table** value generates an HTML table that resembles the PowerShell table format.</span></span> <span data-ttu-id="7f15a-168">Rubrik raden visar egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-168">The header row displays the property names.</span></span> <span data-ttu-id="7f15a-169">Varje tabell rad representerar ett objekt och visar objektets värden för varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="7f15a-169">Each table row represents an object and displays the object's values for each property.</span></span>

<span data-ttu-id="7f15a-170">**List** svärdet genererar en HTML-tabell med två kolumner för varje objekt som liknar PowerShell-List formatet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-170">The **List** value generates a two-column HTML table for each object that resembles the PowerShell list format.</span></span> <span data-ttu-id="7f15a-171">Den första kolumnen visar egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-171">The first column displays the property name.</span></span> <span data-ttu-id="7f15a-172">Den andra kolumnen visar egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-172">The second column displays the property value.</span></span>

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

### <span data-ttu-id="7f15a-173">-Body</span><span class="sxs-lookup"><span data-stu-id="7f15a-173">-Body</span></span>

<span data-ttu-id="7f15a-174">Anger den text som ska läggas till efter den inledande `<BODY>` taggen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-174">Specifies the text to add after the opening `<BODY>` tag.</span></span> <span data-ttu-id="7f15a-175">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-175">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="7f15a-176">-CssUri</span><span class="sxs-lookup"><span data-stu-id="7f15a-176">-CssUri</span></span>

<span data-ttu-id="7f15a-177">Anger Uniform Resource Identifier (URI) för det sammanhängande format bladet (CSS) som tillämpas på HTML-filen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-177">Specifies the Uniform Resource Identifier (URI) of the cascading style sheet (CSS) that is applied to the HTML file.</span></span> <span data-ttu-id="7f15a-178">URI: n tas med i en Formatmallslänkar i utdata.</span><span class="sxs-lookup"><span data-stu-id="7f15a-178">The URI is included in a style sheet link in the output.</span></span>

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

### <span data-ttu-id="7f15a-179">– Fragment</span><span class="sxs-lookup"><span data-stu-id="7f15a-179">-Fragment</span></span>

<span data-ttu-id="7f15a-180">Genererar endast en HTML-tabell.</span><span class="sxs-lookup"><span data-stu-id="7f15a-180">Generates only an HTML table.</span></span> <span data-ttu-id="7f15a-181">Taggarna HTML, HEAD, TITLE och BODY utelämnas.</span><span class="sxs-lookup"><span data-stu-id="7f15a-181">The HTML, HEAD, TITLE, and BODY tags are omitted.</span></span>

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

### <span data-ttu-id="7f15a-182">-Head</span><span class="sxs-lookup"><span data-stu-id="7f15a-182">-Head</span></span>

<span data-ttu-id="7f15a-183">Anger `<HEAD>` taggens innehåll.</span><span class="sxs-lookup"><span data-stu-id="7f15a-183">Specifies the content of the `<HEAD>` tag.</span></span> <span data-ttu-id="7f15a-184">Standardvärdet är `<title\>HTML TABLE</title>`.</span><span class="sxs-lookup"><span data-stu-id="7f15a-184">The default is `<title\>HTML TABLE</title>`.</span></span> <span data-ttu-id="7f15a-185">Om du använder **Head** -parametern ignoreras **title** -parametern.</span><span class="sxs-lookup"><span data-stu-id="7f15a-185">If you use the **Head** parameter, the **Title** parameter is ignored.</span></span>

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

### <span data-ttu-id="7f15a-186">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7f15a-186">-InputObject</span></span>

<span data-ttu-id="7f15a-187">Anger de objekt som ska visas i HTML.</span><span class="sxs-lookup"><span data-stu-id="7f15a-187">Specifies the objects to be represented in HTML.</span></span> <span data-ttu-id="7f15a-188">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-188">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="7f15a-189">Om du använder den här parametern för att skicka flera objekt, till exempel alla tjänster på en dator, `ConvertTo-Html` skapar en tabell som visar egenskaperna för en samling eller en objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="7f15a-189">If you use this parameter to submit multiple objects, such as all of the services on a computer, `ConvertTo-Html` creates a table that displays the properties of a collection or of an array of objects.</span></span> <span data-ttu-id="7f15a-190">Om du vill skapa en tabell med de enskilda objekten använder du pipeline-operatorn för att skicka objekten till `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="7f15a-190">To create a table of the individual objects, use the pipeline operator to pipe the objects to `ConvertTo-Html`.</span></span>

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

### <span data-ttu-id="7f15a-191">-PostContent</span><span class="sxs-lookup"><span data-stu-id="7f15a-191">-PostContent</span></span>

<span data-ttu-id="7f15a-192">Anger text som ska läggas till efter den avslutande `</TABLE>` taggen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-192">Specifies text to add after the closing `</TABLE>` tag.</span></span> <span data-ttu-id="7f15a-193">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-193">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="7f15a-194">-För-innehåll</span><span class="sxs-lookup"><span data-stu-id="7f15a-194">-PreContent</span></span>

<span data-ttu-id="7f15a-195">Anger text som ska läggas till före öppnings `<TABLE>` tag gen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-195">Specifies text to add before the opening `<TABLE>` tag.</span></span> <span data-ttu-id="7f15a-196">Som standard finns det ingen text på den platsen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-196">By default, there is no text in that position.</span></span>

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

### <span data-ttu-id="7f15a-197">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="7f15a-197">-Property</span></span>

<span data-ttu-id="7f15a-198">Innehåller de angivna egenskaperna för objekten i HTML-koden.</span><span class="sxs-lookup"><span data-stu-id="7f15a-198">Includes the specified properties of the objects in the HTML.</span></span> <span data-ttu-id="7f15a-199">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="7f15a-199">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="7f15a-200">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="7f15a-200">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="7f15a-201">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="7f15a-201">Valid key-value pairs are:</span></span>

- <span data-ttu-id="7f15a-202">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="7f15a-202">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="7f15a-203">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="7f15a-203">FormatString - `<string>`</span></span>
- <span data-ttu-id="7f15a-204">Width- `<int32>` -måste vara större än `0`</span><span class="sxs-lookup"><span data-stu-id="7f15a-204">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="7f15a-205">Justering-värdet kan vara `Left` , `Center` eller `Right`</span><span class="sxs-lookup"><span data-stu-id="7f15a-205">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="7f15a-206">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="7f15a-206">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="7f15a-207">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="7f15a-207">-Title</span></span>

<span data-ttu-id="7f15a-208">Anger en rubrik för HTML-filen, det vill säga texten som visas mellan `<TITLE>` taggarna.</span><span class="sxs-lookup"><span data-stu-id="7f15a-208">Specifies a title for the HTML file, that is, the text that appears between the `<TITLE>` tags.</span></span>

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

### <span data-ttu-id="7f15a-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f15a-209">CommonParameters</span></span>

<span data-ttu-id="7f15a-210">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f15a-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f15a-211">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7f15a-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f15a-212">INDATA</span><span class="sxs-lookup"><span data-stu-id="7f15a-212">INPUTS</span></span>

### <span data-ttu-id="7f15a-213">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7f15a-213">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7f15a-214">Du kan skicka alla .NET-objekt till `ConvertTo-Html` .</span><span class="sxs-lookup"><span data-stu-id="7f15a-214">You can pipe any .NET object to `ConvertTo-Html`.</span></span>

## <span data-ttu-id="7f15a-215">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7f15a-215">OUTPUTS</span></span>

### <span data-ttu-id="7f15a-216">System. String eller System.Xml.Xmldokument</span><span class="sxs-lookup"><span data-stu-id="7f15a-216">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="7f15a-217">`ConvertTo-Html` Returnerar en serie med strängar som utgör giltig HTML.</span><span class="sxs-lookup"><span data-stu-id="7f15a-217">`ConvertTo-Html` returns series of strings that comprise valid HTML.</span></span>

## <span data-ttu-id="7f15a-218">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7f15a-218">NOTES</span></span>

<span data-ttu-id="7f15a-219">Om du vill använda den här cmdleten, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet.</span><span class="sxs-lookup"><span data-stu-id="7f15a-219">To use this cmdlet, pipe one or more objects to the cmdlet or use the **InputObject** parameter to specify the object.</span></span> <span data-ttu-id="7f15a-220">När indatan består av flera objekt är resultatet av dessa två metoder ganska annorlunda.</span><span class="sxs-lookup"><span data-stu-id="7f15a-220">When the input consists of multiple objects, the output of these two methods is quite different.</span></span>

- <span data-ttu-id="7f15a-221">När du rör flera objekt till en cmdlet skickar PowerShell objekten till cmdleten en i taget.</span><span class="sxs-lookup"><span data-stu-id="7f15a-221">When you pipe multiple objects to a cmdlet, PowerShell sends the objects to the cmdlet one at a time.</span></span> <span data-ttu-id="7f15a-222">Därför `ConvertTo-Html` skapar en tabell som visar de enskilda objekten.</span><span class="sxs-lookup"><span data-stu-id="7f15a-222">As a result, `ConvertTo-Html` creates a table that displays the individual objects.</span></span> <span data-ttu-id="7f15a-223">Om du till exempel rör processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen alla processer.</span><span class="sxs-lookup"><span data-stu-id="7f15a-223">For example, if you pipe the processes on a computer to `ConvertTo-Html`, the resulting table displays all of the processes.</span></span>

- <span data-ttu-id="7f15a-224">När du använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Html` tar emot dessa objekt som en samling eller som en matris.</span><span class="sxs-lookup"><span data-stu-id="7f15a-224">When you use the **InputObject** parameter to submit multiple objects, `ConvertTo-Html` receives these objects as a collection or as an array.</span></span> <span data-ttu-id="7f15a-225">Därför skapas en tabell som visar matrisen och dess egenskaper, inte objekten i matrisen.</span><span class="sxs-lookup"><span data-stu-id="7f15a-225">As a result, it creates a table that displays the array and its properties, not the items in the array.</span></span> <span data-ttu-id="7f15a-226">Om du till exempel använder **InputObject** för att skicka processerna på en dator till `ConvertTo-Html` , visar den resulterande tabellen en objekt mat ris och dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="7f15a-226">For example, if you use **InputObject** to submit the processes on a computer to `ConvertTo-Html`, the resulting table displays an object array and its properties.</span></span>

  <span data-ttu-id="7f15a-227">För att följa den strikta XHTML DTD-koden ändras DOCTYPE-taggen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="7f15a-227">To comply with the XHTML Strict DTD, the DOCTYPE tag is modified accordingly:</span></span>

   `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"   "https://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"\>`

## <span data-ttu-id="7f15a-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7f15a-228">RELATED LINKS</span></span>

[<span data-ttu-id="7f15a-229">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="7f15a-229">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="7f15a-230">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="7f15a-230">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="7f15a-231">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="7f15a-231">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="7f15a-232">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="7f15a-232">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)

[<span data-ttu-id="7f15a-233">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="7f15a-233">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="7f15a-234">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="7f15a-234">Import-Clixml</span></span>](Import-Clixml.md)
