---
ms.date: 11/21/2019
ms.topic: reference
title: Skriva en PowerShell-skriptmodul
description: Skriva en PowerShell-skriptmodul
ms.openlocfilehash: c44b09a915501fb10773ab11cf13136d5035ba69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649143"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="945e7-103">Skriva en PowerShell-skriptmodul</span><span class="sxs-lookup"><span data-stu-id="945e7-103">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="945e7-104">En skript-modul är ett giltigt PowerShell-skript som sparats i ett `.psm1` tillägg.</span><span class="sxs-lookup"><span data-stu-id="945e7-104">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="945e7-105">Med det här tillägget kan PowerShell-motorn använda regler och moduler-cmdletar i filen.</span><span class="sxs-lookup"><span data-stu-id="945e7-105">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="945e7-106">De flesta av dessa funktioner kan hjälpa dig att installera din kod på andra system, samt hantera omfattning.</span><span class="sxs-lookup"><span data-stu-id="945e7-106">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="945e7-107">Du kan också använda en modul manifest fil som beskriver mer komplexa installationer och lösningar.</span><span class="sxs-lookup"><span data-stu-id="945e7-107">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="945e7-108">Skriva en PowerShell-modul för skript</span><span class="sxs-lookup"><span data-stu-id="945e7-108">Writing a PowerShell script module</span></span>

<span data-ttu-id="945e7-109">Om du vill skapa en-skript-modul sparar du ett giltigt PowerShell-skript i en `.psm1` fil.</span><span class="sxs-lookup"><span data-stu-id="945e7-109">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="945e7-110">Skriptet och katalogen där det lagras måste använda samma namn.</span><span class="sxs-lookup"><span data-stu-id="945e7-110">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="945e7-111">Till exempel lagras ett skript med namnet `MyPsScript.psm1` i en katalog med namnet `MyPsScript` .</span><span class="sxs-lookup"><span data-stu-id="945e7-111">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="945e7-112">Modulens katalog måste vara i en sökväg som anges i `$env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="945e7-112">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="945e7-113">Modulens katalog kan innehålla alla resurser som behövs för att köra skriptet och en modul manifest fil som beskriver hur modulen fungerar.</span><span class="sxs-lookup"><span data-stu-id="945e7-113">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="945e7-114">Skapa en grundläggande PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="945e7-114">Create a basic PowerShell module</span></span>

<span data-ttu-id="945e7-115">Följande steg beskriver hur du skapar en PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="945e7-115">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="945e7-116">Spara ett PowerShell-skript med ett `.psm1` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="945e7-116">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="945e7-117">Använd samma namn för skriptet och katalogen där skriptet sparas.</span><span class="sxs-lookup"><span data-stu-id="945e7-117">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="945e7-118">Att spara ett skript med `.psm1` tillägget innebär att du kan använda cmdlets för moduler, till exempel [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="945e7-118">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="945e7-119">Cmdlets för moduler finns främst så att du kan importera och exportera koden till andra användares system.</span><span class="sxs-lookup"><span data-stu-id="945e7-119">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="945e7-120">Den alternativa lösningen är att läsa in din kod på andra system och sedan punkt-källa den i aktivt minne, vilket inte är en skalbar lösning.</span><span class="sxs-lookup"><span data-stu-id="945e7-120">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="945e7-121">Mer information finns i [förstå en Windows PowerShell-modul](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span><span class="sxs-lookup"><span data-stu-id="945e7-121">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="945e7-122">Som standard `.psm1` är alla funktioner i skriptet tillgängliga, men variabler är inte tillgängliga när användarna importerar filen.</span><span class="sxs-lookup"><span data-stu-id="945e7-122">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="945e7-123">Ett exempel på PowerShell-skript, `Show-Calendar` som är berättigat, är tillgängligt i slutet av den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="945e7-123">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

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

2. <span data-ttu-id="945e7-124">Anropa [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) i slutet av skriptet för att kontrol lera användarens åtkomst till vissa funktioner eller variabler.</span><span class="sxs-lookup"><span data-stu-id="945e7-124">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="945e7-125">I exempel koden längst ned i artikeln finns bara en funktion som som standard visas.</span><span class="sxs-lookup"><span data-stu-id="945e7-125">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="945e7-126">Vi rekommenderar dock att du uttryckligen anropar vilka funktioner du vill visa, enligt beskrivningen i följande kod:</span><span class="sxs-lookup"><span data-stu-id="945e7-126">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="945e7-127">Du kan begränsa vad som importeras med ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="945e7-127">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="945e7-128">Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md) och [skriva ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="945e7-128">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="945e7-129">Om du har moduler som din egen modul behöver läsa in, kan du använda `Import-Module` , överst i modulen.</span><span class="sxs-lookup"><span data-stu-id="945e7-129">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="945e7-130">`Import-Module`Cmdleten importerar en riktad modul till ett system och kan användas vid ett senare tillfälle i proceduren för att installera en egen modul.</span><span class="sxs-lookup"><span data-stu-id="945e7-130">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="945e7-131">Exempel koden längst ned i den här artikeln använder inte några import-moduler.</span><span class="sxs-lookup"><span data-stu-id="945e7-131">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="945e7-132">Men om det gjorde det skulle de visas överst i filen, som du ser i följande kod:</span><span class="sxs-lookup"><span data-stu-id="945e7-132">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="945e7-133">Om du vill beskriva modulen för PowerShell-hjälpen kan du antingen använda standard hjälp kommentarer i filen eller skapa en ytterligare hjälp fil.</span><span class="sxs-lookup"><span data-stu-id="945e7-133">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="945e7-134">Kod exemplet längst ned i den här artikeln innehåller hjälp informationen i kommentarerna.</span><span class="sxs-lookup"><span data-stu-id="945e7-134">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="945e7-135">Du kan också skriva utökade XML-filer som innehåller ytterligare hjälp innehåll.</span><span class="sxs-lookup"><span data-stu-id="945e7-135">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="945e7-136">Mer information finns i [skriva hjälp för Windows PowerShell-moduler](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="945e7-136">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="945e7-137">Om du har ytterligare moduler, XML-filer eller annat innehåll som du vill paketera med modulen kan du använda ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="945e7-137">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="945e7-138">Ett modul manifest är en fil som innehåller namnen på andra moduler, katalogpartitioner, versions nummer, författar data och andra informations delar.</span><span class="sxs-lookup"><span data-stu-id="945e7-138">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="945e7-139">PowerShell använder modul manifest filen för att organisera och distribuera din lösning.</span><span class="sxs-lookup"><span data-stu-id="945e7-139">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="945e7-140">Mer information finns i [så här skriver du ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="945e7-140">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="945e7-141">Om du vill installera och köra modulen sparar du modulen till någon av lämpliga PowerShell-sökvägar och använder `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="945e7-141">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="945e7-142">Sök vägarna där du kan installera modulen finns i den `$env:PSModulePath` globala variabeln.</span><span class="sxs-lookup"><span data-stu-id="945e7-142">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="945e7-143">En gemensam sökväg för att spara en modul på ett system är till exempel `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>` .</span><span class="sxs-lookup"><span data-stu-id="945e7-143">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="945e7-144">Se till att skapa en katalog för modulen som använder samma namn som-skript modulen, även om den bara är en enda `.psm1` fil.</span><span class="sxs-lookup"><span data-stu-id="945e7-144">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="945e7-145">Om du inte sparade modulen på någon av dessa sökvägar måste du ange modulens plats i `Import-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="945e7-145">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="945e7-146">Annars skulle PowerShell inte kunna hitta modulen.</span><span class="sxs-lookup"><span data-stu-id="945e7-146">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="945e7-147">Från och med PowerShell 3,0, om du har placerat modulen i någon av PowerShell-modulens sökvägar, behöver du inte uttryckligen importera den.</span><span class="sxs-lookup"><span data-stu-id="945e7-147">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="945e7-148">Modulen läses in automatiskt när en användare anropar din funktion.</span><span class="sxs-lookup"><span data-stu-id="945e7-148">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="945e7-149">Mer information om module-sökvägen finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md) och [ändra installations Sök vägen för PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="945e7-149">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="945e7-150">Om du vill ta bort en modul från aktiv tjänst i den aktuella PowerShell-sessionen använder du [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="945e7-150">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="945e7-151">`Remove-Module` tar bort en modul från den aktuella PowerShell-sessionen, men avinstallerar inte modulen eller tar bort modulens filer.</span><span class="sxs-lookup"><span data-stu-id="945e7-151">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="945e7-152">Exempel på Show-Calendar kod</span><span class="sxs-lookup"><span data-stu-id="945e7-152">Show-Calendar code example</span></span>

<span data-ttu-id="945e7-153">Följande exempel är en skript-modul som innehåller en enda funktion med namnet `Show-Calendar` .</span><span class="sxs-lookup"><span data-stu-id="945e7-153">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="945e7-154">Den här funktionen visar en visuell representation av en kalender.</span><span class="sxs-lookup"><span data-stu-id="945e7-154">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="945e7-155">Exemplet innehåller PowerShell-hjälp strängar för sammanfattning, beskrivning, parameter värden och kod.</span><span class="sxs-lookup"><span data-stu-id="945e7-155">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="945e7-156">När modulen importeras `Export-ModuleMember` ser kommandot till att `Show-Calendar` funktionen exporteras som en modul medlem.</span><span class="sxs-lookup"><span data-stu-id="945e7-156">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

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
