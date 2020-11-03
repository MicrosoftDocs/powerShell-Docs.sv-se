---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: 214bdd9296dbdbec166e30ba1da0b7976a664ec8
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273596"
---
# Get-Culture

## SAMMANFATTNING
Hämtar den aktuella kulturen som angetts i operativ systemet.

## SYNTAX

```
Get-Culture [<CommonParameters>]
```

## BESKRIVNING

`Get-Culture`Cmdleten hämtar information om aktuella kultur inställningar. Detta omfattar information om aktuella språk inställningar i systemet, till exempel tangentbordslayouten och visnings formatet för objekt som tal, valuta och datum.

Du kan också använda `Get-UICulture` cmdleten, som hämtar den aktuella användar gränssnitts kulturen i systemet och cmdleten [set-Culture](/powershell/module/international/set-culture) i den internationella modulen. Kulturen för användar gränssnittet (UI) avgör vilka text strängar som används för användar gränssnitts element, till exempel menyer och meddelanden.

## EXEMPEL

### Exempel 1: Hämta inställningar för kultur

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

Det här kommandot visar information om de nationella inställningarna på datorn.

### Exempel 2: Formatera egenskaperna för ett kultur objekt

```powershell
PS C:\> $C = Get-Culture
PS C:\> $C | Format-List -Property *
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

PS C:\> $C.Calendar
MinSupportedDateTime : 1/1/0001 12:00:00 AM
MaxSupportedDateTime : 12/31/9999 11:59:59 PM
AlgorithmType        : SolarCalendar
CalendarType         : Localized
Eras                 : {1}
TwoDigitYearMax      : 2029
IsReadOnly           : False

PS C:\> $C.DateTimeFormat
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

PS C:\> $C.DateTimeFormat.FirstDayOfWeek
Sunday
```

Det här exemplet visar den stora mängden data i kultur-objektet. Det visar hur du visar egenskaperna och under egenskaperna för objektet.

Det första kommandot använder `Get-Culture` cmdleten för att hämta de aktuella kultur inställningarna på datorn.
Den lagrar det resulterande kultur objektet i `$C` variabeln.

Det andra kommandot visar alla egenskaper för kultur objekt. Den använder en pipeline-operator ( `|` ) för att skicka kultur objektet i `$C` till- `Format-List` cmdleten. Den använder **egenskaps** parametern för att visa alla ( `*` ) egenskaper för objektet. Det här kommandot kan förkortas som `$c | fl *` .

De återstående kommandona utforskar egenskaperna för kultur objekt med hjälp av punkt notation för att visa värdena för objekt egenskaperna. Du kan använda den här notationen för att visa värdet för en egenskap i objektet.

Det tredje kommandot använder punkt notation för att visa värdet för egenskapen **Calendar** i kultur-objektet.

Det fjärde kommandot använder punkt notation för att visa värdet för egenskapen **DataTimeFormat** för kultur-objektet.

Många objekt egenskaper har egenskaper. Det femte kommandot använder punkt notation för att visa värdet för egenskapen **firstdayofweek** för egenskapen **DateTimeFormat** .

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. globalisering. CultureInfo

`Get-Culture` Returnerar ett objekt som representerar den aktuella kulturen.

## ANTECKNINGAR

Du kan också använda `$PsCulture` `$PsUICulture` variablerna och. `$PsCulture`Variabeln lagrar namnet på den aktuella kulturen och `$PsUICulture` variabeln lagrar namnet på den aktuella kulturen för användar gränssnittet.

## RELATERADE LÄNKAR

[Ange kultur](/powershell/module/international/set-culture)

[Get-värdet](Get-UICulture.md)
