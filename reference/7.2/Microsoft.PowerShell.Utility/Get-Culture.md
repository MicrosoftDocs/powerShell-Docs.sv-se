---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/01/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-culture?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Culture
ms.openlocfilehash: dc49f153adc22b7c2c943a4cc529ac155561228a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709781"
---
# <span data-ttu-id="5c206-102">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="5c206-102">Get-Culture</span></span>

## <span data-ttu-id="5c206-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5c206-103">SYNOPSIS</span></span>
<span data-ttu-id="5c206-104">Hämtar den aktuella kulturen som angetts i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="5c206-104">Gets the current culture set in the operating system.</span></span>

## <span data-ttu-id="5c206-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5c206-105">SYNTAX</span></span>

### <span data-ttu-id="5c206-106">CurrentCulture (standard)</span><span class="sxs-lookup"><span data-stu-id="5c206-106">CurrentCulture (Default)</span></span>

```
Get-Culture [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="5c206-107">Namn</span><span class="sxs-lookup"><span data-stu-id="5c206-107">Name</span></span>

```
Get-Culture [-Name <String[]>] [-NoUserOverrides] [<CommonParameters>]
```

### <span data-ttu-id="5c206-108">ListAvailable</span><span class="sxs-lookup"><span data-stu-id="5c206-108">ListAvailable</span></span>

```
Get-Culture [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="5c206-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5c206-109">DESCRIPTION</span></span>

<span data-ttu-id="5c206-110">`Get-Culture`Cmdleten hämtar information om aktuella kultur inställningar.</span><span class="sxs-lookup"><span data-stu-id="5c206-110">The `Get-Culture` cmdlet gets information about the current culture settings.</span></span> <span data-ttu-id="5c206-111">Detta omfattar information om aktuella språk inställningar i systemet, till exempel tangentbordslayouten och visnings formatet för objekt som tal, valuta och datum.</span><span class="sxs-lookup"><span data-stu-id="5c206-111">This includes information about the current language settings on the system, such as the keyboard layout, and the display format of items such as numbers, currency, and dates.</span></span>

<span data-ttu-id="5c206-112">Du kan också använda `Get-UICulture` cmdleten, som hämtar den aktuella användar gränssnitts kulturen i systemet och cmdleten [set-Culture](/powershell/module/international/set-culture) i den internationella modulen.</span><span class="sxs-lookup"><span data-stu-id="5c206-112">You can also use the `Get-UICulture` cmdlet, which gets the current user interface culture on the system, and the [Set-Culture](/powershell/module/international/set-culture) cmdlet in the International module.</span></span> <span data-ttu-id="5c206-113">Kulturen för användar gränssnittet (UI) avgör vilka text strängar som används för användar gränssnitts element, till exempel menyer och meddelanden.</span><span class="sxs-lookup"><span data-stu-id="5c206-113">The user-interface (UI) culture determines which text strings are used for user interface elements, such as menus and messages.</span></span>

## <span data-ttu-id="5c206-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5c206-114">EXAMPLES</span></span>

### <span data-ttu-id="5c206-115">Exempel 1: Hämta inställningar för kultur</span><span class="sxs-lookup"><span data-stu-id="5c206-115">Example 1: Get culture settings</span></span>

```powershell
Get-Culture
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="5c206-116">Det här kommandot visar information om de nationella inställningarna på datorn.</span><span class="sxs-lookup"><span data-stu-id="5c206-116">This command displays information about the regional settings on the computer.</span></span>

### <span data-ttu-id="5c206-117">Exempel 2: Formatera egenskaperna för ett kultur objekt</span><span class="sxs-lookup"><span data-stu-id="5c206-117">Example 2: Format the properties of a culture object</span></span>

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

<span data-ttu-id="5c206-118">Det här exemplet visar den stora mängden data i kultur-objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-118">This example demonstrates the vast amount of data in the culture object.</span></span> <span data-ttu-id="5c206-119">Det visar hur du visar egenskaperna och under egenskaperna för objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-119">It shows how to display the properties and sub-properties of the object.</span></span>

<span data-ttu-id="5c206-120">Det första kommandot använder `Get-Culture` cmdleten för att hämta de aktuella kultur inställningarna på datorn.</span><span class="sxs-lookup"><span data-stu-id="5c206-120">The first command uses the `Get-Culture` cmdlet to get the current culture settings on the computer.</span></span>
<span data-ttu-id="5c206-121">Den lagrar det resulterande kultur objektet i `$C` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5c206-121">It stores the resulting culture object in the `$C` variable.</span></span>

<span data-ttu-id="5c206-122">Det andra kommandot visar alla egenskaper för kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="5c206-122">The second command displays all of the properties of the culture object.</span></span> <span data-ttu-id="5c206-123">Den använder en pipeline-operator ( `|` ) för att skicka kultur objektet i `$C` till- `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5c206-123">It uses a pipeline operator (`|`) to send the culture object in `$C` to the `Format-List` cmdlet.</span></span> <span data-ttu-id="5c206-124">Den använder **egenskaps** parametern för att visa alla ( `*` ) egenskaper för objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-124">It uses the **Property** parameter to display all (`*`) properties of the object.</span></span> <span data-ttu-id="5c206-125">Det här kommandot kan förkortas som `$c | fl *` .</span><span class="sxs-lookup"><span data-stu-id="5c206-125">This command can be abbreviated as `$c | fl *`.</span></span>

<span data-ttu-id="5c206-126">De återstående kommandona utforskar egenskaperna för kultur objekt med hjälp av punkt notation för att visa värdena för objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="5c206-126">The remaining commands explore the properties of the culture object by using dot notation to display the values of the object properties.</span></span> <span data-ttu-id="5c206-127">Du kan använda den här notationen för att visa värdet för en egenskap i objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-127">You can use this notation to display the value of any property of the object.</span></span>

<span data-ttu-id="5c206-128">Det tredje kommandot använder punkt notation för att visa värdet för egenskapen **Calendar** i kultur-objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-128">The third command uses dot notation to display the value of the **Calendar** property of the culture object.</span></span>

<span data-ttu-id="5c206-129">Det fjärde kommandot använder punkt notation för att visa värdet för egenskapen **DataTimeFormat** för kultur-objektet.</span><span class="sxs-lookup"><span data-stu-id="5c206-129">The fourth command uses dot notation to display the value of the **DataTimeFormat** property of the culture object.</span></span>

<span data-ttu-id="5c206-130">Många objekt egenskaper har egenskaper.</span><span class="sxs-lookup"><span data-stu-id="5c206-130">Many object properties have properties.</span></span> <span data-ttu-id="5c206-131">Det femte kommandot använder punkt notation för att visa värdet för egenskapen **firstdayofweek** för egenskapen **DateTimeFormat** .</span><span class="sxs-lookup"><span data-stu-id="5c206-131">The fifth command uses dot notation to display the value of the **FirstDayOfWeek** property of the **DateTimeFormat** property.</span></span>

### <span data-ttu-id="5c206-132">Exempel 3: Hämta en speciell kultur</span><span class="sxs-lookup"><span data-stu-id="5c206-132">Example 3: Get a specific culture</span></span>

<span data-ttu-id="5c206-133">Hämta CultureInfo-objektet för franska i Frankrike.</span><span class="sxs-lookup"><span data-stu-id="5c206-133">Get the CultureInfo object for French in France.</span></span>

```powershell
Get-Culture -Name fr-FR
```

```Output
LCID             Name             DisplayName
----             ----             -----------
1036             fr-FR            French (France)
```

## <span data-ttu-id="5c206-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5c206-134">PARAMETERS</span></span>

### <span data-ttu-id="5c206-135">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="5c206-135">-ListAvailable</span></span>

<span data-ttu-id="5c206-136">Hämtar alla kulturer som stöds av det aktuella operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="5c206-136">Retrieves all cultures supported by the current operating system.</span></span>

<span data-ttu-id="5c206-137">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5c206-137">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c206-138">-Name</span><span class="sxs-lookup"><span data-stu-id="5c206-138">-Name</span></span>

<span data-ttu-id="5c206-139">Hämta en speciell kultur baserat på namnet.</span><span class="sxs-lookup"><span data-stu-id="5c206-139">Retrieve a specific culture based on the name.</span></span>

<span data-ttu-id="5c206-140">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5c206-140">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5c206-141">-NoUserOverrides</span><span class="sxs-lookup"><span data-stu-id="5c206-141">-NoUserOverrides</span></span>

<span data-ttu-id="5c206-142">Ignorera användar ändringar för aktuell kultur.</span><span class="sxs-lookup"><span data-stu-id="5c206-142">Ignore user changes for current culture.</span></span>

<span data-ttu-id="5c206-143">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5c206-143">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: CurrentCulture, Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5c206-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5c206-144">CommonParameters</span></span>

<span data-ttu-id="5c206-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5c206-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5c206-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5c206-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5c206-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="5c206-147">INPUTS</span></span>

### <span data-ttu-id="5c206-148">Inga</span><span class="sxs-lookup"><span data-stu-id="5c206-148">None</span></span>

<span data-ttu-id="5c206-149">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5c206-149">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5c206-150">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5c206-150">OUTPUTS</span></span>

### <span data-ttu-id="5c206-151">System. globalisering. CultureInfo</span><span class="sxs-lookup"><span data-stu-id="5c206-151">System.Globalization.CultureInfo</span></span>

<span data-ttu-id="5c206-152">`Get-Culture` Returnerar ett objekt som representerar den aktuella kulturen.</span><span class="sxs-lookup"><span data-stu-id="5c206-152">`Get-Culture` returns an object that represents the current culture.</span></span>

## <span data-ttu-id="5c206-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5c206-153">NOTES</span></span>

<span data-ttu-id="5c206-154">Du kan också använda `$PsCulture` `$PsUICulture` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="5c206-154">You can also use the `$PsCulture` and `$PsUICulture` variables.</span></span> <span data-ttu-id="5c206-155">`$PsCulture`Variabeln lagrar namnet på den aktuella kulturen och `$PsUICulture` variabeln lagrar namnet på den aktuella kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="5c206-155">The `$PsCulture` variable stores the name of the current culture and the `$PsUICulture` variable stores the name of the current UI culture.</span></span>

## <span data-ttu-id="5c206-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5c206-156">RELATED LINKS</span></span>

[<span data-ttu-id="5c206-157">Ange kultur</span><span class="sxs-lookup"><span data-stu-id="5c206-157">Set-Culture</span></span>](/powershell/module/international/set-culture)

[<span data-ttu-id="5c206-158">Get-värdet</span><span class="sxs-lookup"><span data-stu-id="5c206-158">Get-UICulture</span></span>](Get-UICulture.md)
