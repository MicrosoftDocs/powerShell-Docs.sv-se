---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Format-Table
ms.openlocfilehash: 2db0a8abe8fbd87b077e40655a06a1db45482ebc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708670"
---
# <span data-ttu-id="2e09b-102">Format-Table</span><span class="sxs-lookup"><span data-stu-id="2e09b-102">Format-Table</span></span>

## <span data-ttu-id="2e09b-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2e09b-103">SYNOPSIS</span></span>
<span data-ttu-id="2e09b-104">Formaterar utdata som en tabell.</span><span class="sxs-lookup"><span data-stu-id="2e09b-104">Formats the output as a table.</span></span>

## <span data-ttu-id="2e09b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2e09b-105">SYNTAX</span></span>

### <span data-ttu-id="2e09b-106">Alla</span><span class="sxs-lookup"><span data-stu-id="2e09b-106">All</span></span>

```
Format-Table [-AutoSize] [-RepeatHeader] [-HideTableHeaders] [-Wrap] [[-Property] <Object[]>]
 [-GroupBy <Object>] [-View <String>] [-ShowError] [-DisplayError] [-Force] [-Expand <String>]
 [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="2e09b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2e09b-107">DESCRIPTION</span></span>

<span data-ttu-id="2e09b-108">`Format-Table`Cmdleten formaterar utdata från ett kommando som en tabell med de valda egenskaperna för objektet i varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-108">The `Format-Table` cmdlet formats the output of a command as a table with the selected properties of the object in each column.</span></span> <span data-ttu-id="2e09b-109">Objekt typen bestämmer standardlayouten och egenskaperna som visas i varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-109">The object type determines the default layout and properties that are displayed in each column.</span></span> <span data-ttu-id="2e09b-110">Du kan använda **egenskaps** parametern för att välja de egenskaper som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="2e09b-110">You can use the **Property** parameter to select the properties that you want to display.</span></span>

<span data-ttu-id="2e09b-111">PowerShell använder standardformat för att definiera hur objekt typer visas.</span><span class="sxs-lookup"><span data-stu-id="2e09b-111">PowerShell uses default formatters to define how object types are displayed.</span></span> <span data-ttu-id="2e09b-112">Du kan använda `.ps1xml` filer för att skapa anpassade vyer som visar en utgående tabell med angivna egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2e09b-112">You can use `.ps1xml` files to create custom views that display an output table with specified properties.</span></span> <span data-ttu-id="2e09b-113">När en anpassad vy har skapats använder du parametern **View** för att visa tabellen med din anpassade vy.</span><span class="sxs-lookup"><span data-stu-id="2e09b-113">After a custom view is created, use the **View** parameter to display the table with your custom view.</span></span> <span data-ttu-id="2e09b-114">Mer information om vyer finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e09b-114">For more information about views, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="2e09b-115">Du kan använda en hash-tabell för att lägga till beräknade egenskaper till ett objekt innan du visar det och för att ange kolumn rubrikerna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-115">You can use a hash table to add calculated properties to an object before displaying it and to specify the column headings in the table.</span></span> <span data-ttu-id="2e09b-116">Använd **egenskapen** eller **groupby** -parametern om du vill lägga till en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-116">To add a calculated property, use the **Property** or **GroupBy** parameter.</span></span> <span data-ttu-id="2e09b-117">Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="2e09b-117">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

## <span data-ttu-id="2e09b-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2e09b-118">EXAMPLES</span></span>

### <span data-ttu-id="2e09b-119">Exempel 1: formatera PowerShell-värd</span><span class="sxs-lookup"><span data-stu-id="2e09b-119">Example 1: Format PowerShell host</span></span>

<span data-ttu-id="2e09b-120">I det här exemplet visas information om värd programmet för PowerShell i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2e09b-120">This example displays information about the host program for PowerShell in a table.</span></span>

```powershell
Get-Host | Format-Table -AutoSize
```

<span data-ttu-id="2e09b-121">`Get-Host`Cmdleten hämtar **system. Management. Automation. Internal. Host. InternalHost** -objekt som representerar värden.</span><span class="sxs-lookup"><span data-stu-id="2e09b-121">The `Get-Host` cmdlet gets **System.Management.Automation.Internal.Host.InternalHost** objects that represent the host.</span></span> <span data-ttu-id="2e09b-122">Objekten skickas ned pipelinen till `Format-Table` och visas i en tabell.</span><span class="sxs-lookup"><span data-stu-id="2e09b-122">The objects are sent down the pipeline to `Format-Table` and displayed in a table.</span></span> <span data-ttu-id="2e09b-123">Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.</span><span class="sxs-lookup"><span data-stu-id="2e09b-123">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

### <span data-ttu-id="2e09b-124">Exempel 2: formatera processer efter BasePriority</span><span class="sxs-lookup"><span data-stu-id="2e09b-124">Example 2: Format processes by BasePriority</span></span>

<span data-ttu-id="2e09b-125">I det här exemplet visas processer i grupper som har samma **BasePriority** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-125">In this example, processes are displayed in groups that have the same **BasePriority** property.</span></span>

```powershell
Get-Process | Sort-Object -Property BasePriority | Format-Table -GroupBy BasePriority -Wrap
```

<span data-ttu-id="2e09b-126">`Get-Process`Cmdleten hämtar objekt som representerar varje process på datorn och skickar dem nedåt i pipeline till `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-126">The `Get-Process` cmdlet gets objects that represent each process on the computer and sends them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="2e09b-127">Objekten sorteras i ordningen för deras **BasePriority** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-127">The objects are sorted in the order of their **BasePriority** property.</span></span>

<span data-ttu-id="2e09b-128">De sorterade objekten skickas ned pipelinen till `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-128">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="2e09b-129">Parametern **groupby** ordnar process data i grupper baserat på deras värde för egenskapen **BasePriority** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-129">The **GroupBy** parameter arranges the process data into groups based on their **BasePriority** property's value.</span></span> <span data-ttu-id="2e09b-130">**Wrap** -parametern ser till att data inte trunkeras.</span><span class="sxs-lookup"><span data-stu-id="2e09b-130">The **Wrap** parameter ensures that data isn't truncated.</span></span>

### <span data-ttu-id="2e09b-131">Exempel 3: formatera processer efter start datum</span><span class="sxs-lookup"><span data-stu-id="2e09b-131">Example 3: Format processes by start date</span></span>

<span data-ttu-id="2e09b-132">I det här exemplet visas information om processerna som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-132">This example displays information about the processes running on the computer.</span></span> <span data-ttu-id="2e09b-133">Objekten sorteras och `Format-Table` använder en vy för att gruppera objekten efter deras start datum.</span><span class="sxs-lookup"><span data-stu-id="2e09b-133">The objects are sorted and `Format-Table` uses a view to group the objects by their start date.</span></span>

```powershell
Get-Process | Sort-Object StartTime | Format-Table -View StartTime
```

<span data-ttu-id="2e09b-134">`Get-Process` hämtar de **system. Diagnostics. process** -objekt som representerar processerna som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-134">`Get-Process` gets the **System.Diagnostics.Process** objects that represent the processes running on the computer.</span></span> <span data-ttu-id="2e09b-135">Objekten skickas ned till pipelinen till `Sort-Object` och sorteras baserat på egenskapen **StartTime** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-135">The objects are sent down the pipeline to `Sort-Object`, and are sorted based on the **StartTime** property.</span></span>

<span data-ttu-id="2e09b-136">De sorterade objekten skickas ned pipelinen till `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-136">The sorted objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="2e09b-137">Parametern **View** anger den **StartTime** -vy som definieras i PowerShell- `DotNetTypes.format.ps1xml` filen för **system. Diagnostics. process** -objekt.</span><span class="sxs-lookup"><span data-stu-id="2e09b-137">The **View** parameter specifies the **StartTime** view that's defined in the PowerShell `DotNetTypes.format.ps1xml` file for **System.Diagnostics.Process** objects.</span></span> <span data-ttu-id="2e09b-138">Vyn **StartTime** konverterar varje processs start tid till ett kort datum och grupperar sedan processerna efter start datum.</span><span class="sxs-lookup"><span data-stu-id="2e09b-138">The **StartTime** view converts each processes start time to a short date and then groups the processes by the start date.</span></span>

<span data-ttu-id="2e09b-139">`DotNetTypes.format.ps1xml`Filen innehåller en **prioritets** vy för processer.</span><span class="sxs-lookup"><span data-stu-id="2e09b-139">The `DotNetTypes.format.ps1xml` file contains a **Priority** view for processes.</span></span> <span data-ttu-id="2e09b-140">Du kan skapa egna `format.ps1xml` filer med anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="2e09b-140">You can create your own `format.ps1xml` files with customized views.</span></span>

### <span data-ttu-id="2e09b-141">Exempel 4: Använd en anpassad vy för tabellens utdata</span><span class="sxs-lookup"><span data-stu-id="2e09b-141">Example 4: Use a custom view for table output</span></span>

<span data-ttu-id="2e09b-142">I det här exemplet visar en anpassad vy katalogens innehåll.</span><span class="sxs-lookup"><span data-stu-id="2e09b-142">In this example, a custom view displays a directory's contents.</span></span> <span data-ttu-id="2e09b-143">Den anpassade vyn lägger till kolumnen **CreationTime** i tabellen utdata för **system. io. DirectoryInfo** och **system. io. fileinfo** objekt som skapats av `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-143">The custom view adds the **CreationTime** column to the table output for **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span>

<span data-ttu-id="2e09b-144">Den anpassade vyn i det här exemplet skapades från vyn som definierats i PowerShell-källkod.</span><span class="sxs-lookup"><span data-stu-id="2e09b-144">The custom view in this example was created from the view defined in PowerShell source code.</span></span> <span data-ttu-id="2e09b-145">Mer information om vyer och koden som används för att skapa det här exemplets vy finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span><span class="sxs-lookup"><span data-stu-id="2e09b-145">For more information about views and the code used to create this example's view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md#sample-xml-for-a-format-table-custom-view).</span></span>

```powershell
Get-ChildItem  -Path C:\Test | Format-Table -View mygciview
```

```Output
    Directory: C:\Test

Mode                LastWriteTime              CreationTime         Length Name
----                -------------              ------------         ------ ----
d-----        11/4/2019     15:54       9/24/2019     15:54                Archives
d-----        8/27/2019     14:22       8/27/2019     14:22                Drawings
d-----       10/23/2019     09:38       2/25/2019     09:38                Files
-a----        11/7/2019     11:07       11/7/2019     11:07          11345 Alias.txt
-a----        2/27/2019     15:15       2/27/2019     15:15            258 alias_out.txt
-a----        2/27/2019     15:16       2/27/2019     15:16            258 alias_out2.txt
```

<span data-ttu-id="2e09b-146">`Get-ChildItem` hämtar innehållet i den aktuella katalogen `C:\Test` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-146">`Get-ChildItem` gets the contents of the current directory, `C:\Test`.</span></span> <span data-ttu-id="2e09b-147">**System. io. DirectoryInfo** och **system. io. fileinfo** -objekten skickas nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-147">The **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects are sent down the pipeline.</span></span>
<span data-ttu-id="2e09b-148">`Format-Table` använder parametern **View** för att ange den anpassade vyn **mygciview** som innehåller kolumnen **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-148">`Format-Table` uses the **View** parameter to specify the custom view **mygciview** that includes the **CreationTime** column.</span></span>

<span data-ttu-id="2e09b-149">Standardutdata `Format-Table` för `Get-ChildItem` inkluderar inte kolumnen **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-149">The default `Format-Table` output for `Get-ChildItem` doesn't include the **CreationTime** column.</span></span>

### <span data-ttu-id="2e09b-150">Exempel 5: Använd egenskaper för tabellens utdata</span><span class="sxs-lookup"><span data-stu-id="2e09b-150">Example 5: Use properties for table output</span></span>

<span data-ttu-id="2e09b-151">I det här exemplet används **egenskaps** parametern för att visa alla dator tjänster i en tabell med två kolumner som visar egenskaperna **Name** och **DependentServices**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-151">This example uses the **Property** parameter to display all the computer's services in a two-column table that shows the properties **Name** and **DependentServices**.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="2e09b-152">`Get-Service` hämtar alla tjänster på datorn och skickar **system. ServiceProcess. ServiceController** -objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-152">`Get-Service` gets all the services on the computer and sends the **System.ServiceProcess.ServiceController** objects down the pipeline.</span></span> <span data-ttu-id="2e09b-153">`Format-Table` använder **egenskaps** parametern för att ange att egenskaperna **namn** och **DependentServices** ska visas i tabellen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-153">`Format-Table` uses the **Property** parameter to specify that the **Name** and **DependentServices** properties are displayed in the table.</span></span>

<span data-ttu-id="2e09b-154">**Namn** -och **DependentServices** är två av objekt typens egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2e09b-154">**Name** and **DependentServices** are two of the object type's properties.</span></span> <span data-ttu-id="2e09b-155">Så här visar du alla egenskaper: `Get-Service | Get-Member -MemberType Properties` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-155">To view all the properties: `Get-Service | Get-Member -MemberType Properties`.</span></span>

### <span data-ttu-id="2e09b-156">Exempel 6: formatera en process och beräkna dess kör tid</span><span class="sxs-lookup"><span data-stu-id="2e09b-156">Example 6: Format a process and calculate its running time</span></span>

<span data-ttu-id="2e09b-157">I det här exemplet visas en tabell med process namnet och den totala körnings tiden för den lokala datorns **anteckningar** -processer.</span><span class="sxs-lookup"><span data-stu-id="2e09b-157">This example displays a table with the process name and total running time for the local computer's **notepad** processes.</span></span> <span data-ttu-id="2e09b-158">Den totala körnings tiden beräknas genom att subtrahera start tiden för varje process från den aktuella tiden.</span><span class="sxs-lookup"><span data-stu-id="2e09b-158">The total running time is calculated by subtracting the start time of each process from the current time.</span></span>

```powershell
Get-Process notepad |
  Format-Table ProcessName, @{Label="TotalRunningTime"; Expression={(Get-Date) - $_.StartTime}}
```

```Output
ProcessName TotalRunningTime
----------- ----------------
notepad     03:20:00.2751767
notepad     00:00:16.7710520
```

<span data-ttu-id="2e09b-159">`Get-Process` hämtar alla **anteckningar** från den lokala datorn och skickar dem nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-159">`Get-Process` gets all the local computer's **notepad** processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="2e09b-160">`Format-Table` visar en tabell med två kolumner: **processname**, en `Get-Process` egenskap och **TotalRunningTime**, en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-160">`Format-Table` displays a table with two columns: **ProcessName**, a `Get-Process` property, and **TotalRunningTime**, a calculated property.</span></span>

<span data-ttu-id="2e09b-161">Egenskapen **TotalRunningTime** anges av en hash-tabell med två nycklar, **etikett** och **uttryck**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-161">The **TotalRunningTime** property is specified by a hash table with two keys, **Label** and **Expression**.</span></span> <span data-ttu-id="2e09b-162">**Etikett** nyckeln anger egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="2e09b-162">The **Label** key specifies the property name.</span></span> <span data-ttu-id="2e09b-163">**Uttrycks** nyckeln anger beräkningen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-163">The **Expression** key specifies the calculation.</span></span> <span data-ttu-id="2e09b-164">Uttrycket hämtar egenskapen **StartTime** för varje process objekt och subtraherar den från resultatet av ett `Get-Date` kommando, som hämtar aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="2e09b-164">The expression gets the **StartTime** property of each process object and subtracts it from the result of a `Get-Date` command, which gets the current date and time.</span></span>

### <span data-ttu-id="2e09b-165">Exempel 7: formatera anteckningar-processer</span><span class="sxs-lookup"><span data-stu-id="2e09b-165">Example 7: Format Notepad processes</span></span>

<span data-ttu-id="2e09b-166">I det här exemplet används för `Get-CimInstance` att hämta körnings tiden för alla **anteckningar** -processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-166">This example uses `Get-CimInstance` to get the running time for all **notepad** processes on the local computer.</span></span> <span data-ttu-id="2e09b-167">Du kan använda `Get-CimInstance` med parametern **computername** för att hämta information från fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="2e09b-167">You can use `Get-CimInstance` with the **ComputerName** parameter to get information from remote computers.</span></span>

```powershell
$Processes = Get-CimInstance -Class win32_process -Filter "name='notepad.exe'"
$Processes | Format-Table ProcessName, @{ Label = "Total Running Time"; Expression={(Get-Date) - $_.CreationDate}}
```

```Output
ProcessName Total Running Time
----------- ------------------
notepad.exe 03:39:39.6260693
notepad.exe 00:19:56.1376922
```

<span data-ttu-id="2e09b-168">`Get-CimInstance` hämtar instanser av WMI- **Win32_Process** -klassen som beskriver alla de lokala dator processerna som heter **notepad.exe**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-168">`Get-CimInstance` gets instances of the WMI **Win32_Process** class that describes all the local computer's processes named **notepad.exe**.</span></span> <span data-ttu-id="2e09b-169">Process objekt lagras i `$Processes` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2e09b-169">The process objects are stored in the `$Processes` variable.</span></span>

<span data-ttu-id="2e09b-170">Process objekt i `$Processes` variabeln skickas ned till pipelinen till `Format-Table` , som visar egenskapen **processname** och en ny beräknad egenskap, **sammanlagd kör tid**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-170">The process objects in the `$Processes` variable are sent down the pipeline to `Format-Table`, which displays the **ProcessName** property and a new calculated property, **Total Running Time**.</span></span>

<span data-ttu-id="2e09b-171">Kommandot tilldelar namnet på den nya beräknade egenskapen, den **totala körnings tiden**, till **etikett** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="2e09b-171">The command assigns the name of the new calculated property, **Total Running Time**, to the **Label** key.</span></span> <span data-ttu-id="2e09b-172">**Uttrycks** nyckelns skript block beräknar hur lång tid processen har körts genom att subtrahera processernas skapande datum från det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="2e09b-172">The **Expression** key's script block calculates how long the process has been running by subtracting the processes creation date from the current date.</span></span> <span data-ttu-id="2e09b-173">`Get-Date`Cmdleten hämtar det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="2e09b-173">The `Get-Date` cmdlet gets the current date.</span></span> <span data-ttu-id="2e09b-174">Skapande datumet subtraheras från det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="2e09b-174">The creation date is subtracted from the current date.</span></span> <span data-ttu-id="2e09b-175">Resultatet är värdet av den **totala kör tiden**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-175">The result is the value of **Total Running Time**.</span></span>

### <span data-ttu-id="2e09b-176">Exempel 8: fel sökning av format fel</span><span class="sxs-lookup"><span data-stu-id="2e09b-176">Example 8: Troubleshooting format errors</span></span>

<span data-ttu-id="2e09b-177">I följande exempel visas resultatet av att lägga till **DisplayError** -eller **ShowError** -parametrarna med ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="2e09b-177">The following examples show the results of adding the **DisplayError** or **ShowError** parameters with an expression.</span></span>

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -DisplayError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday #ERR
```

```powershell
Get-Date | Format-Table DayOfWeek,{ $_ / $null } -ShowError
```

```Output
DayOfWeek  $_ / $null
--------- ------------
Wednesday

InvalidArgument: Failed to evaluate expression " $_ / $null ".
```

## <span data-ttu-id="2e09b-178">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2e09b-178">PARAMETERS</span></span>

### <span data-ttu-id="2e09b-179">-AutoSize</span><span class="sxs-lookup"><span data-stu-id="2e09b-179">-AutoSize</span></span>

<span data-ttu-id="2e09b-180">Anger att cmdleten justerar kolumn storleken och antalet kolumner baserat på data bredden.</span><span class="sxs-lookup"><span data-stu-id="2e09b-180">Indicates that the cmdlet adjusts the column size and number of columns based on the width of the data.</span></span> <span data-ttu-id="2e09b-181">Som standard bestäms kolumn storleken och antalet av vyn.</span><span class="sxs-lookup"><span data-stu-id="2e09b-181">By default, the column size and number are determined by the view.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-182">– DisplayError</span><span class="sxs-lookup"><span data-stu-id="2e09b-182">-DisplayError</span></span>

<span data-ttu-id="2e09b-183">Anger att cmdleten visar fel på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="2e09b-183">Indicates that the cmdlet displays errors on the command line.</span></span> <span data-ttu-id="2e09b-184">Den här parametern kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Table` kommando och behöver felsöka uttrycken.</span><span class="sxs-lookup"><span data-stu-id="2e09b-184">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-185">– Expandera</span><span class="sxs-lookup"><span data-stu-id="2e09b-185">-Expand</span></span>

<span data-ttu-id="2e09b-186">Anger formatet för samlings objekt och objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-186">Specifies the format of the collection object and the objects in the collection.</span></span> <span data-ttu-id="2e09b-187">Den här parametern är utformad för att formatera objekt som har stöd för [ICollection](/dotnet/api/system.collections.icollection) -gränssnittet ([system. Collection](/dotnet/api/system.collections)).</span><span class="sxs-lookup"><span data-stu-id="2e09b-187">This parameter is designed to format objects that support the [ICollection](/dotnet/api/system.collections.icollection) ([System.Collections](/dotnet/api/system.collections)) interface.</span></span> <span data-ttu-id="2e09b-188">Standardvärdet är **EnumOnly**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-188">The default value is **EnumOnly**.</span></span>
<span data-ttu-id="2e09b-189">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="2e09b-189">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2e09b-190">**EnumOnly**: visar egenskaperna för objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-190">**EnumOnly**: Displays the properties of the objects in the collection.</span></span>
- <span data-ttu-id="2e09b-191">**CoreOnly**: visar egenskaperna för objektet samling.</span><span class="sxs-lookup"><span data-stu-id="2e09b-191">**CoreOnly**: Displays the properties of the collection object.</span></span>
- <span data-ttu-id="2e09b-192">**Båda**: visar egenskaperna för Collection-objektet och egenskaperna för objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-192">**Both**: Displays the properties of the collection object and the properties of objects in the collection.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CoreOnly, EnumOnly, Both

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-193">-Force</span><span class="sxs-lookup"><span data-stu-id="2e09b-193">-Force</span></span>

<span data-ttu-id="2e09b-194">Anger att cmdleten dirigerar cmdleten för att visa all fel information.</span><span class="sxs-lookup"><span data-stu-id="2e09b-194">Indicates that the cmdlet directs the cmdlet to display all the error information.</span></span> <span data-ttu-id="2e09b-195">Används med parametern **DisplayError** eller **ShowError** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-195">Use with the **DisplayError** or **ShowError** parameter.</span></span> <span data-ttu-id="2e09b-196">Som standard visas endast en del fel information när ett fel objekt skrivs till fel-eller visnings strömmar.</span><span class="sxs-lookup"><span data-stu-id="2e09b-196">By default, when an error object is written to the error or display streams, only some of the error information is displayed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-197">– GroupBy</span><span class="sxs-lookup"><span data-stu-id="2e09b-197">-GroupBy</span></span>

<span data-ttu-id="2e09b-198">Anger sorterade utdata i separata tabeller baserat på ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="2e09b-198">Specifies sorted output in separate tables based on a property value.</span></span> <span data-ttu-id="2e09b-199">Du kan till exempel använda **groupby** för att visa en lista över tjänster i separata tabeller baserat på deras status.</span><span class="sxs-lookup"><span data-stu-id="2e09b-199">For example, you can use **GroupBy** to list services in separate tables based on their status.</span></span>

<span data-ttu-id="2e09b-200">Ange ett uttryck eller en egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-200">Enter an expression or a property.</span></span> <span data-ttu-id="2e09b-201">Parametern **groupby** förväntar sig att objekten sorteras.</span><span class="sxs-lookup"><span data-stu-id="2e09b-201">The **GroupBy** parameter expects that the objects are sorted.</span></span>
<span data-ttu-id="2e09b-202">Använd `Sort-Object` cmdleten innan `Format-Table` du använder för att gruppera objekten.</span><span class="sxs-lookup"><span data-stu-id="2e09b-202">Use the `Sort-Object` cmdlet before using `Format-Table` to group the objects.</span></span>

<span data-ttu-id="2e09b-203">Värdet för **groupby** -parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-203">The value of the **GroupBy** parameter can be a new calculated property.</span></span> <span data-ttu-id="2e09b-204">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="2e09b-204">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2e09b-205">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="2e09b-205">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2e09b-206">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-206">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="2e09b-207">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-207">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2e09b-208">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-208">FormatString - `<string>`</span></span>

<span data-ttu-id="2e09b-209">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="2e09b-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-210">-HideTableHeaders</span><span class="sxs-lookup"><span data-stu-id="2e09b-210">-HideTableHeaders</span></span>

<span data-ttu-id="2e09b-211">Utelämnar kolumn rubrikerna från tabellen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-211">Omits the column headings from the table.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-212">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2e09b-212">-InputObject</span></span>

<span data-ttu-id="2e09b-213">Anger de objekt som ska formateras.</span><span class="sxs-lookup"><span data-stu-id="2e09b-213">Specifies the objects to format.</span></span> <span data-ttu-id="2e09b-214">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="2e09b-214">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="2e09b-215">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="2e09b-215">-Property</span></span>

<span data-ttu-id="2e09b-216">Anger objekt egenskaperna som visas i visningen och i vilken ordning de visas.</span><span class="sxs-lookup"><span data-stu-id="2e09b-216">Specifies the object properties that appear in the display and the order in which they appear.</span></span> <span data-ttu-id="2e09b-217">Ange ett eller flera egenskaps namn, avgränsade med kommatecken eller Använd en hash-tabell för att visa en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-217">Type one or more property names, separated by commas, or use a hash table to display a calculated property.</span></span> <span data-ttu-id="2e09b-218">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2e09b-218">Wildcards are permitted.</span></span>

<span data-ttu-id="2e09b-219">Om du utelämnar den här parametern beror egenskaperna som visas i vyn på det första objektets egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2e09b-219">If you omit this parameter, the properties that appear in the display depend on the first object's properties.</span></span> <span data-ttu-id="2e09b-220">Om det första objektet till exempel har **egenskapen** in och **PropertyB** men efterföljande objekt har **egenskapen** in, **PropertyB** och **PropertyC**, visas bara rubrikerna **propertya** och **PropertyB** .</span><span class="sxs-lookup"><span data-stu-id="2e09b-220">For example, if the first object has **PropertyA** and **PropertyB** but subsequent objects have **PropertyA**, **PropertyB**, and **PropertyC**, then only the **PropertyA** and **PropertyB** headers will display.</span></span>

<span data-ttu-id="2e09b-221">**Egenskaps** parametern är valfri.</span><span class="sxs-lookup"><span data-stu-id="2e09b-221">The **Property** parameter is optional.</span></span> <span data-ttu-id="2e09b-222">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="2e09b-222">You can't use the **Property** and **View** parameters in the same command.</span></span>

<span data-ttu-id="2e09b-223">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2e09b-223">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="2e09b-224">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="2e09b-224">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="2e09b-225">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="2e09b-225">Valid key-value pairs are:</span></span>

- <span data-ttu-id="2e09b-226">Namn (eller etikett) `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-226">Name (or Label) `<string>`</span></span>
- <span data-ttu-id="2e09b-227">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-227">Expression - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2e09b-228">FormatString `<string>`</span><span class="sxs-lookup"><span data-stu-id="2e09b-228">FormatString - `<string>`</span></span>
- <span data-ttu-id="2e09b-229">Width- `<int32>` -måste vara större än `0`</span><span class="sxs-lookup"><span data-stu-id="2e09b-229">Width - `<int32>` - must be greater than `0`</span></span>
- <span data-ttu-id="2e09b-230">Justering-värdet kan vara `Left` , `Center` eller `Right`</span><span class="sxs-lookup"><span data-stu-id="2e09b-230">Alignment - value can be `Left`, `Center`, or `Right`</span></span>

<span data-ttu-id="2e09b-231">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="2e09b-231">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2e09b-232">-RepeatHeader</span><span class="sxs-lookup"><span data-stu-id="2e09b-232">-RepeatHeader</span></span>

<span data-ttu-id="2e09b-233">Upprepar visar rubriken för en tabell när varje skärm är full.</span><span class="sxs-lookup"><span data-stu-id="2e09b-233">Repeats displaying the header of a table after every screen full.</span></span> <span data-ttu-id="2e09b-234">Den upprepade rubriken är användbar när utdata är skickas till en pager som `less` eller `more` eller sid indelning med en skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="2e09b-234">The repeated header is useful when the output is piped to a pager such as `less` or `more` or paging with a screen reader.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-235">– ShowError</span><span class="sxs-lookup"><span data-stu-id="2e09b-235">-ShowError</span></span>

<span data-ttu-id="2e09b-236">Den här parametern skickar fel via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-236">This parameter sends errors through the pipeline.</span></span> <span data-ttu-id="2e09b-237">Den här parametern kan användas som ett fel söknings stöd när du formaterar uttryck i ett `Format-Table` kommando och behöver felsöka uttrycken.</span><span class="sxs-lookup"><span data-stu-id="2e09b-237">This parameter can be used as a debugging aid when you're formatting expressions in a `Format-Table` command and need to troubleshoot the expressions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-238">– Visa</span><span class="sxs-lookup"><span data-stu-id="2e09b-238">-View</span></span>

<span data-ttu-id="2e09b-239">Från och med PowerShell 6 definieras standardvyerna i PowerShell- `C#` källkod.</span><span class="sxs-lookup"><span data-stu-id="2e09b-239">Beginning in PowerShell 6, the default views are defined in PowerShell `C#` source code.</span></span> <span data-ttu-id="2e09b-240">`*.format.ps1xml`Filerna från powershell 5,1 och tidigare versioner finns inte i PowerShell 6 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="2e09b-240">The `*.format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="2e09b-241">Med parametern **Visa** kan du ange ett alternativt format eller en anpassad vy för tabellen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-241">The **View** parameter lets you specify an alternate format or custom view for the table.</span></span> <span data-ttu-id="2e09b-242">Du kan använda standard-PowerShell-vyer eller skapa anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="2e09b-242">You can use the default PowerShell views or create custom views.</span></span> <span data-ttu-id="2e09b-243">Mer information om hur du skapar en anpassad vy finns i [about_Format.ps1XML](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="2e09b-243">For more information about how to create a custom view, see [about_Format.ps1xml](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md).</span></span>

<span data-ttu-id="2e09b-244">De alternativa och anpassade vyerna för parametern **View** måste använda tabell formatet, annars `Format-Table` Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="2e09b-244">The alternate and custom views for the **View** parameter must use the table format, otherwise, `Format-Table` fails.</span></span> <span data-ttu-id="2e09b-245">Om den alternativa vyn är en lista använder du `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2e09b-245">If the alternate view is a list, use the `Format-List` cmdlet.</span></span> <span data-ttu-id="2e09b-246">Om den alternativa vyn inte är en lista eller en tabell använder du `Format-Custom` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2e09b-246">If the alternate view isn't a list or a table, use the `Format-Custom` cmdlet.</span></span>

<span data-ttu-id="2e09b-247">Du kan inte använda **egenskapen** och **Visa** parametrar i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="2e09b-247">You can't use the **Property** and **View** parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-248">– Radbryt</span><span class="sxs-lookup"><span data-stu-id="2e09b-248">-Wrap</span></span>

<span data-ttu-id="2e09b-249">Visar text som överskrider kolumn bredden på nästa rad.</span><span class="sxs-lookup"><span data-stu-id="2e09b-249">Displays text that exceeds the column width on the next line.</span></span> <span data-ttu-id="2e09b-250">Som standard är text som överskrider kolumn bredden trunkerad.</span><span class="sxs-lookup"><span data-stu-id="2e09b-250">By default, text that exceeds the column width is truncated.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2e09b-251">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2e09b-251">CommonParameters</span></span>

<span data-ttu-id="2e09b-252">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2e09b-252">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2e09b-253">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2e09b-253">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2e09b-254">INDATA</span><span class="sxs-lookup"><span data-stu-id="2e09b-254">INPUTS</span></span>

### <span data-ttu-id="2e09b-255">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2e09b-255">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2e09b-256">Du kan skicka valfritt objekt nedåt i pipeline till `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="2e09b-256">You can send any object down the pipeline to `Format-Table`.</span></span>

## <span data-ttu-id="2e09b-257">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2e09b-257">OUTPUTS</span></span>

### <span data-ttu-id="2e09b-258">Microsoft. PowerShell. commands. Internal. format</span><span class="sxs-lookup"><span data-stu-id="2e09b-258">Microsoft.PowerShell.Commands.Internal.Format</span></span>

<span data-ttu-id="2e09b-259">`Format-Table` Returnerar format objekt som representerar tabellen.</span><span class="sxs-lookup"><span data-stu-id="2e09b-259">`Format-Table` returns format objects that represent the table.</span></span>

## <span data-ttu-id="2e09b-260">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2e09b-260">NOTES</span></span>

## <span data-ttu-id="2e09b-261">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2e09b-261">RELATED LINKS</span></span>

[<span data-ttu-id="2e09b-262">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="2e09b-262">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="2e09b-263">about_Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="2e09b-263">about_Format.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="2e09b-264">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="2e09b-264">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="2e09b-265">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="2e09b-265">Export-FormatData</span></span>](Export-FormatData.md)

[<span data-ttu-id="2e09b-266">Format-Custom</span><span class="sxs-lookup"><span data-stu-id="2e09b-266">Format-Custom</span></span>](Format-Custom.md)

[<span data-ttu-id="2e09b-267">Format-Hex</span><span class="sxs-lookup"><span data-stu-id="2e09b-267">Format-Hex</span></span>](Format-Hex.md)

[<span data-ttu-id="2e09b-268">Format-List</span><span class="sxs-lookup"><span data-stu-id="2e09b-268">Format-List</span></span>](Format-List.md)

[<span data-ttu-id="2e09b-269">Format-Wide</span><span class="sxs-lookup"><span data-stu-id="2e09b-269">Format-Wide</span></span>](Format-Wide.md)

[<span data-ttu-id="2e09b-270">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="2e09b-270">Get-FormatData</span></span>](Get-FormatData.md)

[<span data-ttu-id="2e09b-271">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="2e09b-271">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="2e09b-272">Get-CimInstance</span><span class="sxs-lookup"><span data-stu-id="2e09b-272">Get-CimInstance</span></span>](../CimCmdlets/Get-CimInstance.md)

[<span data-ttu-id="2e09b-273">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="2e09b-273">Update-FormatData</span></span>](Update-FormatData.md)