---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: fee53cd5d241b04b85bc994476d26808b3975bb9
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261542"
---
# Get-Host

## SAMMANFATTNING
Hämtar ett objekt som representerar det aktuella värd programmet.

## SYNTAX

```
Get-Host [<CommonParameters>]
```

## BESKRIVNING

`Get-Host`Cmdleten hämtar ett objekt som representerar det program som är värd för Windows PowerShell.

Standard visningen innehåller Windows PowerShell-versions numret och den aktuella region och de språk inställningar som värden använder, men värd-objektet innehåller en mängd information, inklusive detaljerad information om den version av Windows PowerShell som för närvarande körs och den aktuella kulturen och användar gränssnitts kulturen för Windows PowerShell. Du kan också använda denna cmdlet för att anpassa funktioner i värd programmets användar gränssnitt, till exempel text-och bakgrunds färger.

## EXEMPEL

### Exempel 1: Hämta information om PowerShell-konsolens värd

```
PS C:\> Get-Host
Name             : ConsoleHost
Version          : 2.0
InstanceId       : e4e0ab54-cc5e-4261-9117-4081f20ce7a2
UI               : System.Management.Automation.Internal.Host.InternalHostUserInterface
CurrentCulture   : en-US
CurrentUICulture : en-US
PrivateData      : Microsoft.PowerShell.ConsoleHost+ConsoleColorProxy
IsRunspacePushed : False
Runspace         : System.Management.Automation.Runspaces.LocalRunspace
```

Det här kommandot visar information om Windows PowerShell-konsolen, som är det aktuella värd programmet för Windows PowerShell i det här exemplet. Den innehåller namnet på värden, den version av Windows PowerShell som körs på värden och aktuell kultur och användar gränssnitts kultur.

Egenskaperna version, UI, CurrentCulture, CurrentUICulture, PrivateData och körnings utrymme innehåller ett objekt med mycket användbara egenskaper. I senare exempel går du igenom dessa egenskaper.

### Exempel 2: ändra storlek på PowerShell-fönstret

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

Det här kommandot ändrar storlek på Windows PowerShell-fönstret till 10 bild punkter med 10 bild punkter.

### Exempel 3: Hämta PowerShell-versionen för värden

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

Det här kommandot hämtar detaljerad information om den version av Windows PowerShell som körs på värden.
Du kan visa, men inte ändra, dessa värden.

Egenskapen version för `Get-Host` innehåller ett **system. version** -objekt. Det här kommandot använder en pipeline-operator (|) för att skicka versions objekt till `Format-List` cmdleten. `Format-List`Kommandot använder *egenskaps* parametern med värdet alla (*) för att visa alla egenskaper och egenskaps värden för objektet version.

### Exempel 4: hämta den aktuella kulturen för värden

```powershell
PS C:\> (Get-Host).CurrentCulture | Format-List -Property *
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - 1033
TextInfo                       : TextInfo - 1033
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar, System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

Det här kommandot hämtar detaljerad information om den aktuella kultur uppsättningen för Windows PowerShell som körs på värden. Detta är samma information som returneras av `Get-Culture` cmdleten.

På samma sätt returnerar egenskapen **CurrentUICulture** samma objekt som `Get-UICulture` returnerar.

**CurrentCulture** -egenskapen för Host-objektet innehåller ett **system. globalisering. CultureInfo** -objekt. Det här kommandot använder en pipeline-operator (|) för att skicka **CultureInfo** -objektet till `Format-List` cmdlet: en. `Format-List`Kommandot använder *egenskaps* parametern med värdet alla (*) för att visa alla egenskaper och egenskaps värden för **CultureInfo** -objektet.

### Exempel 5: Hämta DateTimeFormat för den aktuella kulturen

```powershell
PS C:\> (Get-Host).CurrentCulture.DateTimeFormat | Format-List -Property *
AMDesignator                     : AM
Calendar                         : System.Globalization.GregorianCalendar
DateSeparator                    : /
FirstDayOfWeek                   : Sunday
CalendarWeekRule                 : FirstDay
FullDateTimePattern              : dddd, MMMM dd, yyyy h:mm:ss tt
LongDatePattern                  : dddd, MMMM dd, yyyy
LongTimePattern                  : h:mm:ss tt
MonthDayPattern                  : MMMM dd
PMDesignator                     : PM
RFC1123Pattern                   : ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
ShortDatePattern                 : M/d/yyyy
ShortTimePattern                 : h:mm tt
SortableDateTimePattern          : yyyy'-'MM'-'dd'T'HH':'mm':'ss
TimeSeparator                    : :
UniversalSortableDateTimePattern : yyyy'-'MM'-'dd HH':'mm':'ss'Z'
YearMonthPattern                 : MMMM, yyyy
AbbreviatedDayNames              : {Sun, Mon, Tue, Wed...}
ShortestDayNames                 : {Su, Mo, Tu, We...}
DayNames                         : {Sunday, Monday, Tuesday, Wednesday...}
AbbreviatedMonthNames            : {Jan, Feb, Mar, Apr...}
MonthNames                       : {January, February, March, April...}
IsReadOnly                       : False
NativeCalendarName               : Gregorian Calendar
AbbreviatedMonthGenitiveNames    : {Jan, Feb, Mar, Apr...}
MonthGenitiveNames               : {January, February, March, April...}
```

Det här kommandot returnerar detaljerad information om DateTimeFormat för den aktuella kultur som används för Windows PowerShell.

**CurrentCulture** -egenskapen för Host-objektet innehåller ett **CultureInfo** -objekt som i sin tur har många användbara egenskaper. **DateTimeFormat** -egenskapen innehåller bland annat ett **DateTimeFormatInfo** -objekt med många användbara egenskaper.

Använd cmdleten för att hitta typen av objekt som lagras i en objekt egenskap `Get-Member` . Använd cmdleten om du vill visa egenskaps värden för objektet `Format-List` .

### Exempel 6: hämta egenskapen RawUI för värden

```
PS C:\> (Get-Host).UI.RawUI | Format-List -Property *
ForegroundColor       : DarkYellow
BackgroundColor       : DarkBlue
CursorPosition        : 0,390
WindowPosition        : 0,341
CursorSize            : 25
BufferSize            : 120,3000
WindowSize            : 120,50
MaxWindowSize         : 120,81
MaxPhysicalWindowSize : 182,81
KeyAvailable          : False
WindowTitle           : Windows PowerShell 2.0 (04/11/2008 00:08:14)
```

Det här kommandot visar egenskaperna för **RawUI** -egenskapen för objektet Host. Genom att ändra dessa värden kan du ändra värd programmets utseende.

### Exempel 7: Ange bakgrunds färgen för PowerShell-konsolen

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

De här kommandona ändrar bakgrunds färgen i Windows PowerShell-konsolen till svart. Kommandot **CLS** är ett alias för `Clear-Host` funktionen som rensar skärmen och ändrar hela skärmen till den nya färgen.

Den här ändringen gäller endast för den aktuella sessionen. Om du vill ändra bakgrunds färgen för-konsolen för alla sessioner lägger du till kommandot i Windows PowerShell-profilen.

### Exempel 8: Ange bakgrunds färgen för fel meddelanden

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

Det här kommandot ändrar bakgrunds färgen för fel meddelanden till vitt.

Det här kommandot använder den `$Host` automatiska variabeln, som innehåller värd objektet för det aktuella värd programmet. `Get-Host` returnerar samma objekt som `$Host` innehåller, så att du kan använda dem interväxlade.

Det här kommandot använder egenskapen **PrivateData** för egenskapen `$Host` ErrorBackgroundColor. Om du vill se alla egenskaper för objektet i `$Host` . PrivateData-egenskap skriver du `$host.privatedata | format-list *` .

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. Internal. Host. InternalHost

`Get-Host` Returnerar ett objekt av **system. Management. Automation. Internal. Host. InternalHost** .

## ANTECKNINGAR

Den `$Host` automatiska variabeln innehåller samma objekt som `Get-Host` returnerar, och du kan använda det på samma sätt. På samma sätt `$PSCulture` innehåller och `$PSUICulture` Automatiska variabler samma objekt som egenskaperna CurrentCulture och CurrentUICulture för värd objektet innehåller. Du kan använda dessa funktioner utbytbara.

Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).

## RELATERADE LÄNKAR

[Rensa värd](../Microsoft.PowerShell.Core/Clear-Host.md)

[Read-Host](Read-Host.md)

[Skriv värd](Write-Host.md)
