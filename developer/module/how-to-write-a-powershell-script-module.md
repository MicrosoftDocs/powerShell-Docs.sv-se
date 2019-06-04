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
# <a name="how-to-write-a-powershell-script-module"></a>Skriva en PowerShell-skriptmodul

En skriptmodul är i stort sett alla giltiga PowerShell.skript sparas i en .psm1-tillägget. Det här tillägget kan PowerShell-motorn att använda ett antal regler och cmdletar på din fil. De flesta av dessa funktioner är det hjälpa dig att installera din kod på andra system, samt hantera omfång. Du kan också använda en modul-manifestfil, vilket kan beskriva ännu mer komplexa installationer och lösningar.

## <a name="writing-a-powershell-script-module"></a>Skriva en PowerShell-skript-modul

Du kan skapa en skriptmodul genom att spara ett giltigt PowerShell-skript till en .psm1-fil och sedan spara filen i en katalog där PowerShell kan hitta den. I den mapp som du kan också placera alla resurser som du behöver för att köra skriptet, samt en manifestfil beskriver som till PowerShell hur din modul fungerar.

#### <a name="to-create-a-basic-powershell-module"></a>Skapa en grundläggande PowerShell-modul

1. Ta ett befintligt PowerShell.skript och spara skriptet med ett .psm1-tillägg.

   Spara skriptet med .psm1 tillägget innebär att du kan använda modulen-cmdlets som [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), på den. Dessa cmdletar finns främst så att du enkelt kan importera och exportera din kod till andra användares system. (Den alternativa lösningen skulle vara att ladda upp din kod på andra system och källkod punkt i active minnet, vilket inte är en mycket skalbar lösning.) Mer information finns i den **modul-cmdlet: ar och variabler** i avsnittet [Windows PowerShell-moduler](./understanding-a-windows-powershell-module.md) Observera som alla funktioner i ditt skript som standard är tillgänglig för användare som importerar .psm1-fil men egenskaper visas inte.

   Ett exempel PowerShell-skriptet berättigade `Show-Calendar`, finns i slutet av det här avsnittet.

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

2. För att styra användarnas åtkomst till vissa funktioner eller egenskaper, anropa [Export ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) i slutet av skriptet.

   Exempelkoden längst ned på sidan har en enda funktion, vilket som standard skulle exponeras. Vi rekommenderar dock att du explicit anropa reda på vilka funktioner du vill exponera, enligt beskrivningen i följande kod:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   Du kan även begränsa vad importeras med hjälp av ett modulmanifest. Mer information finns i [importera en PowerShell-modul](./importing-a-powershell-module.md) och [hur du skriver en PowerShell-modulen Manifest](./how-to-write-a-powershell-module-manifest.md).

3. Om du har moduler som krävs för en egen modul har lästs in kan du använda dem med ett anrop till `Import-Module`, högst upp på en egen modul.

   `Import-Module` är en cmdlet som importerar en modul som är riktade till ett system. Därför används den också vid en senare tidpunkt i procedur för att installera en egen modul samt. Exempelkoden längst ned i den här sidan använder inte alla importera moduler. Om den hade gjort, men skulle de visas överst i filen, enligt beskrivningen i följande kod:

   ```powershell
   Import-Module GenericModule
   ```

4. För att beskriva din modul till PowerShell-hjälpen, kan du antingen använda hjälp standard kommentarer i filen eller skapa en ytterligare hjälpfilen.

   Kodexemplet längst ned i det här avsnittet innehåller hjälpinformationen i kommentarerna. Du kan också skriva utökade XML-filer som innehåller ytterligare hjälpinnehållet. Mer information finns i [skriva hjälp för Windows PowerShell-moduler](./writing-help-for-windows-powershell-modules.md).

5. Om du har ytterligare moduler, XML-filer eller annat innehåll som du vill packa upp med modulen kan göra du det med ett modulmanifest.

   Ett modulmanifest är en fil som innehåller namnen på andra moduler, katalogstrukturer, versionshantering nummer, författare data och andra typer av information. PowerShell använder manifest-filen för modulen för att organisera och distribuera din lösning. Men på grund av den relativt enkla natur i det här exemplet, var en manifestfil inte nödvändig. Mer information finns i [modulen manifest](./how-to-write-a-powershell-module-manifest.md).

6. Om du vill installera och köra din modul, spara modulen till en lämplig PowerShell-sökvägar och göra ett anrop till `Import-Module`.

   Sökvägar där du kan installera din modul finns i den `$env:PSModulePath` global variabel. Till exempel en sökväg till att spara en modul i ett system är `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Glöm inte att skapa en mapp för din modul finns i, även om det är bara en enda .psm1-fil. Om du inte sparade din modul till en av dessa sökvägar, skulle du behöva skicka in platsen för din modul i anropet till `Import-Module`. (Annars PowerShell skulle inte att hitta det.) Från och med PowerShell 3.0, om du har placerat modulens i en av de PowerShell-modul sökvägarna, behöver du inte uttryckligen importera den. Du modulen läses in automatiskt när en användare anropar funktionen.
   Läs mer på modul-sökväg, [importera en PowerShell-modul](./importing-a-powershell-module.md) och [PSModulePath miljövariabel](./modifying-the-psmodulepath-installation-path.md).

7. Ta bort en modul från aktiva tjänsten genom att göra ett anrop till [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Observera att [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) tar bort din modul från aktiva minne – det faktiskt raderas den inte från där du sparade filerna för modulen.

### <a name="show-calendar-code-example"></a>Visa kalender-kodexempel

I följande exempel är ett enkelt skript-modul som innehåller en funktion med namnet `Show-Calendar`.
Den här funktionen visar en visuell representation av en kalender. Exemplet innehåller dessutom PowerShell-hjälpen-strängar för sammanfattning, beskrivning, parametervärden och exempel. Observera att den sista raden med kod säkerställer att den `Show-Calendar` funktionen exporteras som en modul medlem när modulen har importerats.

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
