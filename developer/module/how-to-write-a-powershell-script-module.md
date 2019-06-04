---
title: Hur du skriver en PowerShell-skript-modul | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470795"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="2d86a-102">Skriva en PowerShell-skriptmodul</span><span class="sxs-lookup"><span data-stu-id="2d86a-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="2d86a-103">En skriptmodul är i stort sett alla giltiga PowerShell.skript sparas i en .psm1-tillägget.</span><span class="sxs-lookup"><span data-stu-id="2d86a-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="2d86a-104">Det här tillägget kan PowerShell-motorn att använda ett antal regler och cmdletar på din fil.</span><span class="sxs-lookup"><span data-stu-id="2d86a-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="2d86a-105">De flesta av dessa funktioner är det hjälpa dig att installera din kod på andra system, samt hantera omfång.</span><span class="sxs-lookup"><span data-stu-id="2d86a-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="2d86a-106">Du kan också använda en modul-manifestfil, vilket kan beskriva ännu mer komplexa installationer och lösningar.</span><span class="sxs-lookup"><span data-stu-id="2d86a-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="2d86a-107">Skriva en PowerShell-skript-modul</span><span class="sxs-lookup"><span data-stu-id="2d86a-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="2d86a-108">Du kan skapa en skriptmodul genom att spara ett giltigt PowerShell-skript till en .psm1-fil och sedan spara filen i en katalog där PowerShell kan hitta den.</span><span class="sxs-lookup"><span data-stu-id="2d86a-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="2d86a-109">I den mapp som du kan också placera alla resurser som du behöver för att köra skriptet, samt en manifestfil beskriver som till PowerShell hur din modul fungerar.</span><span class="sxs-lookup"><span data-stu-id="2d86a-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="2d86a-110">Skapa en grundläggande PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="2d86a-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="2d86a-111">Ta ett befintligt PowerShell.skript och spara skriptet med ett .psm1-tillägg.</span><span class="sxs-lookup"><span data-stu-id="2d86a-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="2d86a-112">Spara skriptet med .psm1 tillägget innebär att du kan använda modulen-cmdlets som [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), på den.</span><span class="sxs-lookup"><span data-stu-id="2d86a-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="2d86a-113">Dessa cmdletar finns främst så att du enkelt kan importera och exportera din kod till andra användares system.</span><span class="sxs-lookup"><span data-stu-id="2d86a-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="2d86a-114">(Den alternativa lösningen skulle vara att ladda upp din kod på andra system och källkod punkt i active minnet, vilket inte är en mycket skalbar lösning.) Mer information finns i den **modul-cmdlet: ar och variabler** i avsnittet [Windows PowerShell-moduler](./understanding-a-windows-powershell-module.md) Observera som alla funktioner i ditt skript som standard är tillgänglig för användare som importerar .psm1-fil men egenskaper visas inte.</span><span class="sxs-lookup"><span data-stu-id="2d86a-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="2d86a-115">Ett exempel PowerShell-skriptet berättigade `Show-Calendar`, finns i slutet av det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2d86a-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="2d86a-116">För att styra användarnas åtkomst till vissa funktioner eller egenskaper, anropa [Export ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) i slutet av skriptet.</span><span class="sxs-lookup"><span data-stu-id="2d86a-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="2d86a-117">Exempelkoden längst ned på sidan har en enda funktion, vilket som standard skulle exponeras.</span><span class="sxs-lookup"><span data-stu-id="2d86a-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="2d86a-118">Vi rekommenderar dock att du explicit anropa reda på vilka funktioner du vill exponera, enligt beskrivningen i följande kod:</span><span class="sxs-lookup"><span data-stu-id="2d86a-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="2d86a-119">Du kan även begränsa vad importeras med hjälp av ett modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="2d86a-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="2d86a-120">Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md) och [hur du skriver en PowerShell-modulen Manifest](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2d86a-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="2d86a-121">Om du har moduler som krävs för en egen modul har lästs in kan du använda dem med ett anrop till `Import-Module`, högst upp på en egen modul.</span><span class="sxs-lookup"><span data-stu-id="2d86a-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="2d86a-122">`Import-Module` är en cmdlet som importerar en modul som är riktade till ett system.</span><span class="sxs-lookup"><span data-stu-id="2d86a-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="2d86a-123">Därför används den också vid en senare tidpunkt i procedur för att installera en egen modul samt.</span><span class="sxs-lookup"><span data-stu-id="2d86a-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="2d86a-124">Exempelkoden längst ned i den här sidan använder inte alla importera moduler.</span><span class="sxs-lookup"><span data-stu-id="2d86a-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="2d86a-125">Om den hade gjort, men skulle de visas överst i filen, enligt beskrivningen i följande kod:</span><span class="sxs-lookup"><span data-stu-id="2d86a-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="2d86a-126">För att beskriva din modul till PowerShell-hjälpen, kan du antingen använda hjälp standard kommentarer i filen eller skapa en ytterligare hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="2d86a-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="2d86a-127">Kodexemplet längst ned i det här avsnittet innehåller hjälpinformationen i kommentarerna.</span><span class="sxs-lookup"><span data-stu-id="2d86a-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="2d86a-128">Du kan också skriva utökade XML-filer som innehåller ytterligare hjälpinnehållet.</span><span class="sxs-lookup"><span data-stu-id="2d86a-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="2d86a-129">Mer information finns i [skriva hjälp för Windows PowerShell-moduler](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="2d86a-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="2d86a-130">Om du har ytterligare moduler, XML-filer eller annat innehåll som du vill packa upp med modulen kan göra du det med ett modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="2d86a-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="2d86a-131">Ett modulmanifest är en fil som innehåller namnen på andra moduler, katalogstrukturer, versionshantering nummer, författare data och andra typer av information.</span><span class="sxs-lookup"><span data-stu-id="2d86a-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="2d86a-132">PowerShell använder manifest-filen för modulen för att organisera och distribuera din lösning.</span><span class="sxs-lookup"><span data-stu-id="2d86a-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="2d86a-133">Men på grund av den relativt enkla natur i det här exemplet, var en manifestfil inte nödvändig.</span><span class="sxs-lookup"><span data-stu-id="2d86a-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="2d86a-134">Mer information finns i [modulen manifest](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2d86a-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="2d86a-135">Om du vill installera och köra din modul, spara modulen till en lämplig PowerShell-sökvägar och göra ett anrop till `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="2d86a-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="2d86a-136">Sökvägar där du kan installera din modul finns i den `$env:PSModulePath` global variabel.</span><span class="sxs-lookup"><span data-stu-id="2d86a-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="2d86a-137">Till exempel en sökväg till att spara en modul i ett system är `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="2d86a-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="2d86a-138">Glöm inte att skapa en mapp för din modul finns i, även om det är bara en enda .psm1-fil.</span><span class="sxs-lookup"><span data-stu-id="2d86a-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="2d86a-139">Om du inte sparade din modul till en av dessa sökvägar, skulle du behöva skicka in platsen för din modul i anropet till `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="2d86a-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="2d86a-140">(Annars PowerShell skulle inte att hitta det.) Från och med PowerShell 3.0, om du har placerat modulens i en av de PowerShell-modul sökvägarna, behöver du inte uttryckligen importera den.</span><span class="sxs-lookup"><span data-stu-id="2d86a-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="2d86a-141">Du modulen läses in automatiskt när en användare anropar funktionen.</span><span class="sxs-lookup"><span data-stu-id="2d86a-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="2d86a-142">Läs mer på modul-sökväg, [importera en PowerShell-modul](./importing-a-powershell-module.md) och [PSModulePath miljövariabel](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="2d86a-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="2d86a-143">Ta bort en modul från aktiva tjänsten genom att göra ett anrop till [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="2d86a-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="2d86a-144">Observera att [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) tar bort din modul från aktiva minne – det faktiskt raderas den inte från där du sparade filerna för modulen.</span><span class="sxs-lookup"><span data-stu-id="2d86a-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="2d86a-145">Visa kalender-kodexempel</span><span class="sxs-lookup"><span data-stu-id="2d86a-145">Show-Calendar code example</span></span>

<span data-ttu-id="2d86a-146">I följande exempel är ett enkelt skript-modul som innehåller en funktion med namnet `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="2d86a-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="2d86a-147">Den här funktionen visar en visuell representation av en kalender.</span><span class="sxs-lookup"><span data-stu-id="2d86a-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="2d86a-148">Exemplet innehåller dessutom PowerShell-hjälpen-strängar för sammanfattning, beskrivning, parametervärden och exempel.</span><span class="sxs-lookup"><span data-stu-id="2d86a-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="2d86a-149">Observera att den sista raden med kod säkerställer att den `Show-Calendar` funktionen exporteras som en modul medlem när modulen har importerats.</span><span class="sxs-lookup"><span data-stu-id="2d86a-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
