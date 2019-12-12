---
title: Så här skriver du en PowerShell-modul för skript | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: 7742eedd67283535b9e5898adc74d0d48faf68fe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416272"
---
# <a name="how-to-write-a-powershell-script-module"></a>Skriva en PowerShell-skriptmodul

En skript-modul är ett giltigt PowerShell-skript som sparats i ett `.psm1`-tillägg. Med det här tillägget kan PowerShell-motorn använda regler och moduler-cmdletar i filen. De flesta av dessa funktioner kan hjälpa dig att installera din kod på andra system, samt hantera omfattning. Du kan också använda en modul manifest fil som beskriver mer komplexa installationer och lösningar.

## <a name="writing-a-powershell-script-module"></a>Skriva en PowerShell-modul för skript

Om du vill skapa en-skript-modul sparar du ett giltigt PowerShell-skript i en `.psm1`-fil. Skriptet och katalogen där det lagras måste använda samma namn. Till exempel lagras ett skript med namnet `MyPsScript.psm1` i en katalog med namnet `MyPsScript`.

Modulens katalog måste vara i en sökväg som anges i `$env:PSModulePath`. Modulens katalog kan innehålla alla resurser som behövs för att köra skriptet och en modul manifest fil som beskriver hur modulen fungerar.

## <a name="create-a-basic-powershell-module"></a>Skapa en grundläggande PowerShell-modul

Följande steg beskriver hur du skapar en PowerShell-modul.

1. Spara ett PowerShell-skript med ett `.psm1`-tillägg. Använd samma namn för skriptet och katalogen där skriptet sparas.

   Om du sparar ett skript med tillägget `.psm1` kan du använda cmdlets för moduler, till exempel [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module). Cmdlets för moduler finns främst så att du kan importera och exportera koden till andra användares system. Den alternativa lösningen är att läsa in din kod på andra system och sedan punkt-källa den i aktivt minne, vilket inte är en skalbar lösning. Mer information finns i [förstå en Windows PowerShell-modul](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).
   Som standard är alla funktioner i skriptet tillgängliga, när användarna importerar `.psm1`-filen, men variablerna är inte.

   Ett exempel på PowerShell-skript, berättigade `Show-Calendar`, finns i slutet av den här artikeln.

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

2. Anropa [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) i slutet av skriptet för att kontrol lera användarens åtkomst till vissa funktioner eller variabler.

   I exempel koden längst ned i artikeln finns bara en funktion som som standard visas. Vi rekommenderar dock att du uttryckligen anropar vilka funktioner du vill visa, enligt beskrivningen i följande kod:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Du kan begränsa vad som importeras med ett modul manifest. Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md) och [skriva ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).

3. Om du har moduler som din egen modul behöver läsa in, kan du använda `Import-Module`överst i modulen.

   `Import-Module` cmdlet importerar en riktad modul till ett system och kan användas vid ett senare tillfälle i proceduren för att installera en egen modul. Exempel koden längst ned i den här artikeln använder inte några import-moduler. Men om det gjorde det skulle de visas överst i filen, som du ser i följande kod:

   ```powershell
   Import-Module GenericModule
   ```

4. Om du vill beskriva modulen för PowerShell-hjälpen kan du antingen använda standard hjälp kommentarer i filen eller skapa en ytterligare hjälp fil.

   Kod exemplet längst ned i den här artikeln innehåller hjälp informationen i kommentarerna. Du kan också skriva utökade XML-filer som innehåller ytterligare hjälp innehåll. Mer information finns i [skriva hjälp för Windows PowerShell-moduler](./writing-help-for-windows-powershell-modules.md).

5. Om du har ytterligare moduler, XML-filer eller annat innehåll som du vill paketera med modulen kan du använda ett modul manifest.

   Ett modul manifest är en fil som innehåller namnen på andra moduler, katalogpartitioner, versions nummer, författar data och andra informations delar. PowerShell använder modul manifest filen för att organisera och distribuera din lösning. Mer information finns i [så här skriver du ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).

6. Om du vill installera och köra modulen sparar du modulen till någon av lämpliga PowerShell-sökvägar och använder `Import-Module`.

   Sök vägarna där du kan installera modulen finns i `$env:PSModulePath` globala variabeln. Till exempel är en gemensam sökväg för att spara en modul på ett system `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`. Se till att skapa en katalog för modulen som använder samma namn som-skript modulen, även om den bara är en enda `.psm1` fil. Om du inte sparade modulen på någon av dessa sökvägar måste du ange modulens plats i `Import-Module` kommandot. Annars skulle PowerShell inte kunna hitta modulen.

   Från och med PowerShell 3,0, om du har placerat modulen i någon av PowerShell-modulens sökvägar, behöver du inte uttryckligen importera den. Modulen läses in automatiskt när en användare anropar din funktion. Mer information om module-sökvägen finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md) och [ändra installations Sök vägen för PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Om du vill ta bort en modul från aktiv tjänst i den aktuella PowerShell-sessionen använder du [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   > [!NOTE]
   > `Remove-Module` tar bort en modul från den aktuella PowerShell-sessionen, men avinstallerar inte modulen eller tar bort modulens filer.

## <a name="show-calendar-code-example"></a>Visa – kalender kod exempel

Följande exempel är en-skript-modul som innehåller en enda funktion med namnet `Show-Calendar`. Den här funktionen visar en visuell representation av en kalender. Exemplet innehåller PowerShell-hjälp strängar för sammanfattning, beskrivning, parameter värden och kod. När modulen importeras säkerställer kommandot `Export-ModuleMember` att funktionen `Show-Calendar` exporteras som en modul medlem.

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
