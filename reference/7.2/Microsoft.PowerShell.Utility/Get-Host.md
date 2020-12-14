---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 0775940f210cb028d7a0919bb8e5ca9f256b70d8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708654"
---
# <span data-ttu-id="b9876-102">Get-Host</span><span class="sxs-lookup"><span data-stu-id="b9876-102">Get-Host</span></span>

## <span data-ttu-id="b9876-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b9876-103">SYNOPSIS</span></span>
<span data-ttu-id="b9876-104">Hämtar ett objekt som representerar det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="b9876-104">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="b9876-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9876-105">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="b9876-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b9876-106">DESCRIPTION</span></span>

<span data-ttu-id="b9876-107">`Get-Host`Cmdleten hämtar ett objekt som representerar det program som är värd för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9876-107">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="b9876-108">Standard visningen innehåller Windows PowerShell-versions numret och den aktuella region och de språk inställningar som värden använder, men värd-objektet innehåller en mängd information, inklusive detaljerad information om den version av Windows PowerShell som för närvarande körs och den aktuella kulturen och användar gränssnitts kulturen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9876-108">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="b9876-109">Du kan också använda denna cmdlet för att anpassa funktioner i värd programmets användar gränssnitt, till exempel text-och bakgrunds färger.</span><span class="sxs-lookup"><span data-stu-id="b9876-109">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="b9876-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b9876-110">EXAMPLES</span></span>

### <span data-ttu-id="b9876-111">Exempel 1: Hämta information om PowerShell-konsolens värd</span><span class="sxs-lookup"><span data-stu-id="b9876-111">Example 1: Get information about the PowerShell console host</span></span>

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

<span data-ttu-id="b9876-112">Det här kommandot visar information om Windows PowerShell-konsolen, som är det aktuella värd programmet för Windows PowerShell i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="b9876-112">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="b9876-113">Den innehåller namnet på värden, den version av Windows PowerShell som körs på värden och aktuell kultur och användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="b9876-113">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="b9876-114">Egenskaperna version, UI, CurrentCulture, CurrentUICulture, PrivateData och körnings utrymme innehåller ett objekt med mycket användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b9876-114">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="b9876-115">I senare exempel går du igenom dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b9876-115">Later examples examine these properties.</span></span>

### <span data-ttu-id="b9876-116">Exempel 2: ändra storlek på PowerShell-fönstret</span><span class="sxs-lookup"><span data-stu-id="b9876-116">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="b9876-117">Det här kommandot ändrar storlek på Windows PowerShell-fönstret till 10 bild punkter med 10 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="b9876-117">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="b9876-118">Exempel 3: Hämta PowerShell-versionen för värden</span><span class="sxs-lookup"><span data-stu-id="b9876-118">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="b9876-119">Det här kommandot hämtar detaljerad information om den version av Windows PowerShell som körs på värden.</span><span class="sxs-lookup"><span data-stu-id="b9876-119">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="b9876-120">Du kan visa, men inte ändra, dessa värden.</span><span class="sxs-lookup"><span data-stu-id="b9876-120">You can view, but not change, these values.</span></span>

<span data-ttu-id="b9876-121">Egenskapen version för `Get-Host` innehåller ett **system. version** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b9876-121">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="b9876-122">Det här kommandot använder en pipeline-operator (|) för att skicka versions objekt till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b9876-122">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="b9876-123">`Format-List`Kommandot använder *egenskaps* parametern med värdet alla (\*) för att visa alla egenskaper och egenskaps värden för objektet version.</span><span class="sxs-lookup"><span data-stu-id="b9876-123">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="b9876-124">Exempel 4: hämta den aktuella kulturen för värden</span><span class="sxs-lookup"><span data-stu-id="b9876-124">Example 4: Get the current culture for the host</span></span>

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

<span data-ttu-id="b9876-125">Det här kommandot hämtar detaljerad information om den aktuella kultur uppsättningen för Windows PowerShell som körs på värden.</span><span class="sxs-lookup"><span data-stu-id="b9876-125">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="b9876-126">Detta är samma information som returneras av `Get-Culture` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b9876-126">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="b9876-127">På samma sätt returnerar egenskapen **CurrentUICulture** samma objekt som `Get-UICulture` returnerar.</span><span class="sxs-lookup"><span data-stu-id="b9876-127">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="b9876-128">**CurrentCulture** -egenskapen för Host-objektet innehåller ett **system. globalisering. CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b9876-128">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="b9876-129">Det här kommandot använder en pipeline-operator (|) för att skicka **CultureInfo** -objektet till `Format-List` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b9876-129">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="b9876-130">`Format-List`Kommandot använder *egenskaps* parametern med värdet alla (\*) för att visa alla egenskaper och egenskaps värden för **CultureInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="b9876-130">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="b9876-131">Exempel 5: Hämta DateTimeFormat för den aktuella kulturen</span><span class="sxs-lookup"><span data-stu-id="b9876-131">Example 5: Get the DateTimeFormat for the current culture</span></span>

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

<span data-ttu-id="b9876-132">Det här kommandot returnerar detaljerad information om DateTimeFormat för den aktuella kultur som används för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9876-132">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="b9876-133">**CurrentCulture** -egenskapen för Host-objektet innehåller ett **CultureInfo** -objekt som i sin tur har många användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b9876-133">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="b9876-134">**DateTimeFormat** -egenskapen innehåller bland annat ett **DateTimeFormatInfo** -objekt med många användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b9876-134">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="b9876-135">Använd cmdleten för att hitta typen av objekt som lagras i en objekt egenskap `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="b9876-135">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="b9876-136">Använd cmdleten om du vill visa egenskaps värden för objektet `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="b9876-136">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="b9876-137">Exempel 6: hämta egenskapen RawUI för värden</span><span class="sxs-lookup"><span data-stu-id="b9876-137">Example 6: Get the RawUI property for the host</span></span>

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

<span data-ttu-id="b9876-138">Det här kommandot visar egenskaperna för **RawUI** -egenskapen för objektet Host.</span><span class="sxs-lookup"><span data-stu-id="b9876-138">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="b9876-139">Genom att ändra dessa värden kan du ändra värd programmets utseende.</span><span class="sxs-lookup"><span data-stu-id="b9876-139">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="b9876-140">Exempel 7: Ange bakgrunds färgen för PowerShell-konsolen</span><span class="sxs-lookup"><span data-stu-id="b9876-140">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="b9876-141">De här kommandona ändrar bakgrunds färgen i Windows PowerShell-konsolen till svart.</span><span class="sxs-lookup"><span data-stu-id="b9876-141">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="b9876-142">Kommandot **CLS** är ett alias för `Clear-Host` funktionen som rensar skärmen och ändrar hela skärmen till den nya färgen.</span><span class="sxs-lookup"><span data-stu-id="b9876-142">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="b9876-143">Den här ändringen gäller endast för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b9876-143">This change is effective only in the current session.</span></span> <span data-ttu-id="b9876-144">Om du vill ändra bakgrunds färgen för-konsolen för alla sessioner lägger du till kommandot i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="b9876-144">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="b9876-145">Exempel 8: Ange bakgrunds färgen för fel meddelanden</span><span class="sxs-lookup"><span data-stu-id="b9876-145">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="b9876-146">Det här kommandot ändrar bakgrunds färgen för fel meddelanden till vitt.</span><span class="sxs-lookup"><span data-stu-id="b9876-146">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="b9876-147">Det här kommandot använder den `$Host` automatiska variabeln, som innehåller värd objektet för det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="b9876-147">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="b9876-148">`Get-Host` returnerar samma objekt som `$Host` innehåller, så att du kan använda dem interväxlade.</span><span class="sxs-lookup"><span data-stu-id="b9876-148">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="b9876-149">Det här kommandot använder egenskapen **PrivateData** för egenskapen `$Host` ErrorBackgroundColor.</span><span class="sxs-lookup"><span data-stu-id="b9876-149">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="b9876-150">Om du vill se alla egenskaper för objektet i `$Host` . PrivateData-egenskap skriver du `$host.privatedata | format-list *` .</span><span class="sxs-lookup"><span data-stu-id="b9876-150">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="b9876-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b9876-151">PARAMETERS</span></span>

### <span data-ttu-id="b9876-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b9876-152">CommonParameters</span></span>

<span data-ttu-id="b9876-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b9876-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b9876-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b9876-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b9876-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="b9876-155">INPUTS</span></span>

### <span data-ttu-id="b9876-156">Inga</span><span class="sxs-lookup"><span data-stu-id="b9876-156">None</span></span>
<span data-ttu-id="b9876-157">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9876-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b9876-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b9876-158">OUTPUTS</span></span>

### <span data-ttu-id="b9876-159">System. Management. Automation. Internal. Host. InternalHost</span><span class="sxs-lookup"><span data-stu-id="b9876-159">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="b9876-160">`Get-Host` Returnerar ett objekt av **system. Management. Automation. Internal. Host. InternalHost** .</span><span class="sxs-lookup"><span data-stu-id="b9876-160">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="b9876-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b9876-161">NOTES</span></span>

<span data-ttu-id="b9876-162">Den `$Host` automatiska variabeln innehåller samma objekt som `Get-Host` returnerar, och du kan använda det på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="b9876-162">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="b9876-163">På samma sätt `$PSCulture` innehåller och `$PSUICulture` Automatiska variabler samma objekt som egenskaperna CurrentCulture och CurrentUICulture för värd objektet innehåller.</span><span class="sxs-lookup"><span data-stu-id="b9876-163">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="b9876-164">Du kan använda dessa funktioner utbytbara.</span><span class="sxs-lookup"><span data-stu-id="b9876-164">You can use these features interchangeably.</span></span>

<span data-ttu-id="b9876-165">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b9876-165">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="b9876-166">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b9876-166">RELATED LINKS</span></span>

[<span data-ttu-id="b9876-167">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="b9876-167">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="b9876-168">Read-Host</span><span class="sxs-lookup"><span data-stu-id="b9876-168">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="b9876-169">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="b9876-169">Write-Host</span></span>](Write-Host.md)

