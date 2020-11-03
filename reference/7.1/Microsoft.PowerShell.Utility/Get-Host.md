---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Host
ms.openlocfilehash: 45a7a8a44bdb116e2e7d9327fd23972cb7af1246
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261674"
---
# <span data-ttu-id="1a538-103">Get-Host</span><span class="sxs-lookup"><span data-stu-id="1a538-103">Get-Host</span></span>

## <span data-ttu-id="1a538-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1a538-104">SYNOPSIS</span></span>
<span data-ttu-id="1a538-105">Hämtar ett objekt som representerar det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="1a538-105">Gets an object that represents the current host program.</span></span>

## <span data-ttu-id="1a538-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1a538-106">SYNTAX</span></span>

```
Get-Host [<CommonParameters>]
```

## <span data-ttu-id="1a538-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1a538-107">DESCRIPTION</span></span>

<span data-ttu-id="1a538-108">`Get-Host`Cmdleten hämtar ett objekt som representerar det program som är värd för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a538-108">The `Get-Host` cmdlet gets an object that represents the program that is hosting Windows PowerShell.</span></span>

<span data-ttu-id="1a538-109">Standard visningen innehåller Windows PowerShell-versions numret och den aktuella region och de språk inställningar som värden använder, men värd-objektet innehåller en mängd information, inklusive detaljerad information om den version av Windows PowerShell som för närvarande körs och den aktuella kulturen och användar gränssnitts kulturen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a538-109">The default display includes the Windows PowerShell version number and the current region and language settings that the host is using, but the host object contains a wealth of information, including detailed information about the version of Windows PowerShell that is currently running and the current culture and UI culture of Windows PowerShell.</span></span> <span data-ttu-id="1a538-110">Du kan också använda denna cmdlet för att anpassa funktioner i värd programmets användar gränssnitt, till exempel text-och bakgrunds färger.</span><span class="sxs-lookup"><span data-stu-id="1a538-110">You can also use this cmdlet to customize features of the host program user interface, such as the text and background colors.</span></span>

## <span data-ttu-id="1a538-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1a538-111">EXAMPLES</span></span>

### <span data-ttu-id="1a538-112">Exempel 1: Hämta information om PowerShell-konsolens värd</span><span class="sxs-lookup"><span data-stu-id="1a538-112">Example 1: Get information about the PowerShell console host</span></span>

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

<span data-ttu-id="1a538-113">Det här kommandot visar information om Windows PowerShell-konsolen, som är det aktuella värd programmet för Windows PowerShell i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="1a538-113">This command displays information about the Windows PowerShell console, which is the current host program for Windows PowerShell in this example.</span></span> <span data-ttu-id="1a538-114">Den innehåller namnet på värden, den version av Windows PowerShell som körs på värden och aktuell kultur och användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="1a538-114">It includes the name of the host, the version of Windows PowerShell that is running in the host, and current culture and UI culture.</span></span>

<span data-ttu-id="1a538-115">Egenskaperna version, UI, CurrentCulture, CurrentUICulture, PrivateData och körnings utrymme innehåller ett objekt med mycket användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a538-115">The Version, UI, CurrentCulture, CurrentUICulture, PrivateData, and Runspace properties each contain an object with very useful properties.</span></span> <span data-ttu-id="1a538-116">I senare exempel går du igenom dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a538-116">Later examples examine these properties.</span></span>

### <span data-ttu-id="1a538-117">Exempel 2: ändra storlek på PowerShell-fönstret</span><span class="sxs-lookup"><span data-stu-id="1a538-117">Example 2: Resize the PowerShell window</span></span>

```powershell
PS C:\> $H = Get-Host
PS C:\> $Win = $H.UI.RawUI.WindowSize
PS C:\> $Win.Height = 10
PS C:\> $Win.Width  = 10
PS C:\> $H.UI.RawUI.Set_WindowSize($Win)
```

<span data-ttu-id="1a538-118">Det här kommandot ändrar storlek på Windows PowerShell-fönstret till 10 bild punkter med 10 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="1a538-118">This command resizes the Windows PowerShell window to 10 pixels by 10 pixels.</span></span>

### <span data-ttu-id="1a538-119">Exempel 3: Hämta PowerShell-versionen för värden</span><span class="sxs-lookup"><span data-stu-id="1a538-119">Example 3: Get the PowerShell version for the host</span></span>

```powershell
PS C:\> (Get-Host).Version | Format-List -Property *
Major         : 2
Minor         : 0
Build         : -1
Revision      : -1
MajorRevision : -1
MinorRevision : -1
```

<span data-ttu-id="1a538-120">Det här kommandot hämtar detaljerad information om den version av Windows PowerShell som körs på värden.</span><span class="sxs-lookup"><span data-stu-id="1a538-120">This command gets detailed information about the version of Windows PowerShell running in the host.</span></span>
<span data-ttu-id="1a538-121">Du kan visa, men inte ändra, dessa värden.</span><span class="sxs-lookup"><span data-stu-id="1a538-121">You can view, but not change, these values.</span></span>

<span data-ttu-id="1a538-122">Egenskapen version för `Get-Host` innehåller ett **system. version** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1a538-122">The Version property of `Get-Host` contains a **System.Version** object.</span></span> <span data-ttu-id="1a538-123">Det här kommandot använder en pipeline-operator (|) för att skicka versions objekt till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a538-123">This command uses a pipeline operator (|) to send the version object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1a538-124">`Format-List`Kommandot använder *egenskaps* parametern med värdet alla (\*) för att visa alla egenskaper och egenskaps värden för objektet version.</span><span class="sxs-lookup"><span data-stu-id="1a538-124">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the version object.</span></span>

### <span data-ttu-id="1a538-125">Exempel 4: hämta den aktuella kulturen för värden</span><span class="sxs-lookup"><span data-stu-id="1a538-125">Example 4: Get the current culture for the host</span></span>

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

<span data-ttu-id="1a538-126">Det här kommandot hämtar detaljerad information om den aktuella kultur uppsättningen för Windows PowerShell som körs på värden.</span><span class="sxs-lookup"><span data-stu-id="1a538-126">This command gets detailed information about the current culture set for Windows PowerShell running in the host.</span></span> <span data-ttu-id="1a538-127">Detta är samma information som returneras av `Get-Culture` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1a538-127">This is the same information that is returned by the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="1a538-128">På samma sätt returnerar egenskapen **CurrentUICulture** samma objekt som `Get-UICulture` returnerar.</span><span class="sxs-lookup"><span data-stu-id="1a538-128">Similarly, the **CurrentUICulture** property returns the same object that `Get-UICulture` returns.</span></span>

<span data-ttu-id="1a538-129">**CurrentCulture** -egenskapen för Host-objektet innehåller ett **system. globalisering. CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1a538-129">The **CurrentCulture** property of the host object contains a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="1a538-130">Det här kommandot använder en pipeline-operator (|) för att skicka **CultureInfo** -objektet till `Format-List` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="1a538-130">This command uses a pipeline operator (|) to send the **CultureInfo** object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="1a538-131">`Format-List`Kommandot använder *egenskaps* parametern med värdet alla (\*) för att visa alla egenskaper och egenskaps värden för **CultureInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="1a538-131">The `Format-List` command uses the *Property* parameter with a value of all (\*) to display all of the properties and property values of the **CultureInfo** object.</span></span>

### <span data-ttu-id="1a538-132">Exempel 5: Hämta DateTimeFormat för den aktuella kulturen</span><span class="sxs-lookup"><span data-stu-id="1a538-132">Example 5: Get the DateTimeFormat for the current culture</span></span>

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

<span data-ttu-id="1a538-133">Det här kommandot returnerar detaljerad information om DateTimeFormat för den aktuella kultur som används för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1a538-133">This command returns detailed information about the DateTimeFormat of the current culture that is being used for Windows PowerShell.</span></span>

<span data-ttu-id="1a538-134">**CurrentCulture** -egenskapen för Host-objektet innehåller ett **CultureInfo** -objekt som i sin tur har många användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a538-134">The **CurrentCulture** property of the host object contains a **CultureInfo** object that, in turn, has many useful properties.</span></span> <span data-ttu-id="1a538-135">**DateTimeFormat** -egenskapen innehåller bland annat ett **DateTimeFormatInfo** -objekt med många användbara egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a538-135">Among them, the **DateTimeFormat** property contains a **DateTimeFormatInfo** object with many useful properties.</span></span>

<span data-ttu-id="1a538-136">Använd cmdleten för att hitta typen av objekt som lagras i en objekt egenskap `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="1a538-136">To find the type of an object that is stored in an object property, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="1a538-137">Använd cmdleten om du vill visa egenskaps värden för objektet `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="1a538-137">To display the property values of the object, use the `Format-List` cmdlet.</span></span>

### <span data-ttu-id="1a538-138">Exempel 6: hämta egenskapen RawUI för värden</span><span class="sxs-lookup"><span data-stu-id="1a538-138">Example 6: Get the RawUI property for the host</span></span>

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

<span data-ttu-id="1a538-139">Det här kommandot visar egenskaperna för **RawUI** -egenskapen för objektet Host.</span><span class="sxs-lookup"><span data-stu-id="1a538-139">This command displays the properties of the **RawUI** property of the host object.</span></span> <span data-ttu-id="1a538-140">Genom att ändra dessa värden kan du ändra värd programmets utseende.</span><span class="sxs-lookup"><span data-stu-id="1a538-140">By changing these values, you can change the appearance of the host program.</span></span>

### <span data-ttu-id="1a538-141">Exempel 7: Ange bakgrunds färgen för PowerShell-konsolen</span><span class="sxs-lookup"><span data-stu-id="1a538-141">Example 7: Set the background color for the PowerShell console</span></span>

```powershell
PS C:\> (Get-Host).UI.RawUI.BackgroundColor = "Black"
PS C:\> cls
```

<span data-ttu-id="1a538-142">De här kommandona ändrar bakgrunds färgen i Windows PowerShell-konsolen till svart.</span><span class="sxs-lookup"><span data-stu-id="1a538-142">These commands change the background color of the Windows PowerShell console to black.</span></span> <span data-ttu-id="1a538-143">Kommandot **CLS** är ett alias för `Clear-Host` funktionen som rensar skärmen och ändrar hela skärmen till den nya färgen.</span><span class="sxs-lookup"><span data-stu-id="1a538-143">The **cls** command is an alias for the `Clear-Host` function, which clears the screen and changes the whole screen to the new color.</span></span>

<span data-ttu-id="1a538-144">Den här ändringen gäller endast för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1a538-144">This change is effective only in the current session.</span></span> <span data-ttu-id="1a538-145">Om du vill ändra bakgrunds färgen för-konsolen för alla sessioner lägger du till kommandot i Windows PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="1a538-145">To change the background color of the console for all sessions, add the command to your Windows PowerShell profile.</span></span>

### <span data-ttu-id="1a538-146">Exempel 8: Ange bakgrunds färgen för fel meddelanden</span><span class="sxs-lookup"><span data-stu-id="1a538-146">Example 8: Set the background color for error messages</span></span>

```
PS C:\> $Host.PrivateData.ErrorBackgroundColor = "white"
```

<span data-ttu-id="1a538-147">Det här kommandot ändrar bakgrunds färgen för fel meddelanden till vitt.</span><span class="sxs-lookup"><span data-stu-id="1a538-147">This command changes the background color of error messages to white.</span></span>

<span data-ttu-id="1a538-148">Det här kommandot använder den `$Host` automatiska variabeln, som innehåller värd objektet för det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="1a538-148">This command uses the `$Host` automatic variable, which contains the host object for the current host program.</span></span> <span data-ttu-id="1a538-149">`Get-Host` returnerar samma objekt som `$Host` innehåller, så att du kan använda dem interväxlade.</span><span class="sxs-lookup"><span data-stu-id="1a538-149">`Get-Host` returns the same object that `$Host` contains, so you can use them interchangeably.</span></span>

<span data-ttu-id="1a538-150">Det här kommandot använder egenskapen **PrivateData** för egenskapen `$Host` ErrorBackgroundColor.</span><span class="sxs-lookup"><span data-stu-id="1a538-150">This command uses the **PrivateData** property of `$Host` as its ErrorBackgroundColor property.</span></span> <span data-ttu-id="1a538-151">Om du vill se alla egenskaper för objektet i `$Host` . PrivateData-egenskap skriver du `$host.privatedata | format-list *` .</span><span class="sxs-lookup"><span data-stu-id="1a538-151">To see all of the properties of the object in the `$Host`.PrivateData property, type `$host.privatedata | format-list *`.</span></span>

## <span data-ttu-id="1a538-152">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1a538-152">PARAMETERS</span></span>

### <span data-ttu-id="1a538-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1a538-153">CommonParameters</span></span>

<span data-ttu-id="1a538-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1a538-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1a538-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1a538-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1a538-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="1a538-156">INPUTS</span></span>

### <span data-ttu-id="1a538-157">Inget</span><span class="sxs-lookup"><span data-stu-id="1a538-157">None</span></span>
<span data-ttu-id="1a538-158">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1a538-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="1a538-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1a538-159">OUTPUTS</span></span>

### <span data-ttu-id="1a538-160">System. Management. Automation. Internal. Host. InternalHost</span><span class="sxs-lookup"><span data-stu-id="1a538-160">System.Management.Automation.Internal.Host.InternalHost</span></span>

<span data-ttu-id="1a538-161">`Get-Host` Returnerar ett objekt av **system. Management. Automation. Internal. Host. InternalHost** .</span><span class="sxs-lookup"><span data-stu-id="1a538-161">`Get-Host` returns a **System.Management.Automation.Internal.Host.InternalHost** object.</span></span>

## <span data-ttu-id="1a538-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1a538-162">NOTES</span></span>

<span data-ttu-id="1a538-163">Den `$Host` automatiska variabeln innehåller samma objekt som `Get-Host` returnerar, och du kan använda det på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="1a538-163">The `$Host` automatic variable contains the same object that `Get-Host` returns, and you can use it in the same way.</span></span> <span data-ttu-id="1a538-164">På samma sätt `$PSCulture` innehåller och `$PSUICulture` Automatiska variabler samma objekt som egenskaperna CurrentCulture och CurrentUICulture för värd objektet innehåller.</span><span class="sxs-lookup"><span data-stu-id="1a538-164">Similarly, the `$PSCulture` and `$PSUICulture` automatic variables contain the same objects that the CurrentCulture and CurrentUICulture properties of the host object contain.</span></span> <span data-ttu-id="1a538-165">Du kan använda dessa funktioner utbytbara.</span><span class="sxs-lookup"><span data-stu-id="1a538-165">You can use these features interchangeably.</span></span>

<span data-ttu-id="1a538-166">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1a538-166">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

## <span data-ttu-id="1a538-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1a538-167">RELATED LINKS</span></span>

[<span data-ttu-id="1a538-168">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="1a538-168">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="1a538-169">Read-Host</span><span class="sxs-lookup"><span data-stu-id="1a538-169">Read-Host</span></span>](Read-Host.md)

[<span data-ttu-id="1a538-170">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="1a538-170">Write-Host</span></span>](Write-Host.md)

