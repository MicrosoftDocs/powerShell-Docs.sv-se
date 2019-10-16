---
title: Så här skriver du en PowerShell-modul för skript | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352901"
---
# <a name="how-to-write-a-powershell-script-module"></a>Skriva en PowerShell-skriptmodul

En skriptbaserad modul är i grunden ett giltigt PowerShell-skript som sparats i ett. psm1-tillägg. Med det här tillägget kan PowerShell-motorn använda ett antal regler och cmdlets i filen. De flesta av dessa funktioner kan hjälpa dig att installera din kod på andra system, samt hantera omfattning. Du kan också använda en modul manifest fil som kan beskriva ännu mer komplexa installationer och lösningar.

## <a name="writing-a-powershell-script-module"></a>Skriva en PowerShell-modul för skript

Du skapar en-skript-modul genom att spara ett giltigt PowerShell-skript i en. psm1-fil och sedan spara filen i en katalog som finns där PowerShell kan hitta den. I den mappen kan du också placera alla resurser som du behöver för att köra skriptet, samt en manifest fil som beskriver hur modulen fungerar.

#### <a name="to-create-a-basic-powershell-module"></a>Så här skapar du en grundläggande PowerShell-modul

1. Ta ett befintligt PowerShell-skript och Spara skriptet med fil namns tillägget. psm1.

   Att spara ett skript med tillägget. psm1 innebär att du kan använda cmdlets för moduler, till exempel [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), på den. Dessa cmdletar finns främst så att du enkelt kan importera och exportera koden till andra användares system. (Den alternativa lösningen skulle vara att ladda upp din kod på andra system och sedan använda den i aktivt minne, vilket inte är en särskilt skalbar lösning.) Mer information finns i avsnittet **moduler cmdlets och variabler** i [Windows PowerShell-moduler](./understanding-a-windows-powershell-module.md) Observera att som standard är alla funktioner i skriptet tillgängliga för användare som importerar din. psm1-fil, men egenskaperna är inte.

   Ett exempel på PowerShell-skript, berättigade `Show-Calendar`, är tillgängligt i slutet av det här avsnittet.

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

2. Anropa [export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) i slutet av skriptet om du vill kontrol lera användar åtkomst till vissa funktioner eller egenskaper.

   Exempel koden längst ned på sidan har bara en funktion, vilken som standard visas. Vi rekommenderar dock att du uttryckligen anropar vilka funktioner du vill visa, enligt beskrivningen i följande kod:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Du kan också begränsa vad som importeras med ett modul manifest. Mer information finns i [Importera en PowerShell-modul](./importing-a-powershell-module.md) och [skriva ett manifest för PowerShell-modul](./how-to-write-a-powershell-module-manifest.md).

3. Om du har moduler som din egen modul behöver läsa in, kan du använda dem med ett anrop till `Import-Module`, överst i din egen modul.

   `Import-Module` är en cmdlet som importerar en riktad modul till ett system. Därför används den också vid ett senare tillfälle i proceduren för att installera en egen modul också. Exempel koden längst ned på den här sidan använder inte några import-moduler. Om det gjorde det visas de dock överst i filen, enligt beskrivningen i följande kod:

   ```powershell
   Import-Module GenericModule
   ```

4. Om du vill beskriva modulen för PowerShell-hjälpen kan du antingen använda standard hjälp kommentarer i filen eller skapa en ytterligare hjälp fil.

   Kod exemplet längst ned i det här avsnittet innehåller hjälp informationen i kommentarerna. Du kan också skriva utökade XML-filer som innehåller ytterligare hjälp innehåll. Mer information finns i [skriva hjälp för Windows PowerShell-moduler](./writing-help-for-windows-powershell-modules.md).

5. Om du har ytterligare moduler, XML-filer eller annat innehåll som du vill paketera med modulen kan du göra det med ett modul manifest.

   Ett modul manifest är en fil som innehåller namnen på andra moduler, katalogpartitioner, versions nummer, författar data och andra informations delar. PowerShell använder modul manifest filen för att organisera och distribuera din lösning. Men på grund av den relativt enkla typen av det här exemplet behövde inte en manifest fil. Mer information finns i [modul manifest](./how-to-write-a-powershell-module-manifest.md).

6. Om du vill installera och köra modulen sparar du modulen till någon av lämpliga PowerShell-sökvägar och gör ett anrop till `Import-Module`.

   Sök vägarna där du kan installera modulen finns i den globala variabeln `$env:PSModulePath`. En gemensam sökväg för att spara en modul på ett system skulle till exempel vara `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Se till att skapa en mapp för modulen som ska finnas i, även om den bara är en enskild. psm1-fil. Om du inte sparade modulen på någon av dessa sökvägar skulle du behöva gå igenom platsen för modulen i anropet till `Import-Module`. (Annars skulle PowerShell inte kunna hitta den.) Från och med PowerShell 3,0 behöver du inte importera den explicit om du har placerat modulen i en av PowerShell-modulens sökvägar. Du läser in modulen automatiskt när en användare anropar din funktion.
   Mer information om module-sökvägen finns i [Importera en PowerShell-modul och en](./importing-a-powershell-module.md) PSModulePath- [miljö variabel](./modifying-the-psmodulepath-installation-path.md).

7. Om du vill ta bort en modul från den aktiva tjänsten gör du ett anrop till [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Observera att [Remove-module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) tar bort modulen från det aktiva minnet – den tas inte bort från den plats där du sparade modulens filer.

### <a name="show-calendar-code-example"></a>Visa – kalender kod exempel

Följande exempel är en enkel skript-modul som innehåller en enda funktion med namnet `Show-Calendar`.
Den här funktionen visar en visuell representation av en kalender. Dessutom innehåller exemplet PowerShell-hjälp strängar för sammanfattning, beskrivning, parameter värden och exempel. Observera att den sista raden med kod säkerställer att funktionen `Show-Calendar` exporteras som en modul medlem när modulen importeras.

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
