---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: c7710cb59785fbfd726ff0aabaf41c43a6966ee1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709756"
---
# <span data-ttu-id="a04cd-102">Out-String</span><span class="sxs-lookup"><span data-stu-id="a04cd-102">Out-String</span></span>

## <span data-ttu-id="a04cd-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a04cd-103">SYNOPSIS</span></span>
<span data-ttu-id="a04cd-104">Matar in indata-objekt som en sträng.</span><span class="sxs-lookup"><span data-stu-id="a04cd-104">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="a04cd-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a04cd-105">SYNTAX</span></span>

### <span data-ttu-id="a04cd-106">NoNewLineFormatting (standard)</span><span class="sxs-lookup"><span data-stu-id="a04cd-106">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="a04cd-107">StreamFormatting</span><span class="sxs-lookup"><span data-stu-id="a04cd-107">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="a04cd-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a04cd-108">DESCRIPTION</span></span>

<span data-ttu-id="a04cd-109">`Out-String`Cmdleten konverterar inmatade objekt till strängar.</span><span class="sxs-lookup"><span data-stu-id="a04cd-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="a04cd-110">Som standard `Out-String` ackumuleras strängarna och returneras som en enskild sträng, men du kan använda **Stream** -parametern för att dirigera `Out-String` för att returnera en rad i taget eller skapa en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="a04cd-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="a04cd-111">Med den här cmdleten kan du söka efter och manipulera sträng utdata som i traditionella skal när objekt manipulation är mindre användbart.</span><span class="sxs-lookup"><span data-stu-id="a04cd-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="a04cd-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a04cd-112">EXAMPLES</span></span>

### <span data-ttu-id="a04cd-113">Exempel 1: hämta den aktuella kulturen och konvertera data till strängar</span><span class="sxs-lookup"><span data-stu-id="a04cd-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="a04cd-114">Det här exemplet hämtar de nationella inställningarna för den aktuella användaren och konverterar objekt data till strängar.</span><span class="sxs-lookup"><span data-stu-id="a04cd-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
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
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="a04cd-115">`$C`Variabeln lagrar en **Selected.System. Globaliserings-. CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="a04cd-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="a04cd-116">Objektet är resultatet av `Get-Culture` att skicka utdata nedåt i pipeline till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="a04cd-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="a04cd-117">**Egenskaps** parametern använder en asterisk ( `*` ) som jokertecken för att ange alla egenskaper som finns i objektet.</span><span class="sxs-lookup"><span data-stu-id="a04cd-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="a04cd-118">`Out-String` använder parametern **InputObject** för att ange det **CultureInfo** -objekt som lagras i `$C` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a04cd-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="a04cd-119">Objekten i `$C` konverteras till en sträng.</span><span class="sxs-lookup"><span data-stu-id="a04cd-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="a04cd-120">Om du vill visa `Out-String` matrisen lagrar du utdata till en variabel och använder ett mat ris index för att Visa elementen.</span><span class="sxs-lookup"><span data-stu-id="a04cd-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="a04cd-121">Mer information om mat ris index finns [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a04cd-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="a04cd-122">Exempel 2: arbeta med objekt</span><span class="sxs-lookup"><span data-stu-id="a04cd-122">Example 2: Working with objects</span></span>

<span data-ttu-id="a04cd-123">Det här exemplet visar skillnaden mellan att arbeta med objekt och att arbeta med strängar.</span><span class="sxs-lookup"><span data-stu-id="a04cd-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="a04cd-124">Kommandot visar ett alias som innehåller texten **GCM**, alias för `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="a04cd-124">The command displays an alias that includes the text **gcm**, the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="a04cd-125">`Get-Alias` hämtar objekten **system. Management. Automation. AliasInfo** , ett för varje alias och skickar objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a04cd-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="a04cd-126">`Out-String` använder **Stream** -parametern för att konvertera varje objekt till en sträng, och sammanfogar alla objekt till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="a04cd-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="a04cd-127">**System. String** -objekten skickas ned pipelinen och `Select-String` använder **mönster** parametern för att hitta matchningar för texten **GCM**.</span><span class="sxs-lookup"><span data-stu-id="a04cd-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="a04cd-128">Om du utelämnar parametern **Stream** visar kommandot alla alias eftersom `Select-String` söker efter texten **GCM** i den enskilda strängen som `Out-String` returnerar.</span><span class="sxs-lookup"><span data-stu-id="a04cd-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="a04cd-129">Exempel 3: Använd parametern width för att förhindra trunkering.</span><span class="sxs-lookup"><span data-stu-id="a04cd-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="a04cd-130">Medan de flesta utdata från `Out-String` radbryts till nästa rad finns det scenarier där utdata trunkeras av formaterings systemet innan de skickas till `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="a04cd-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="a04cd-131">Du kan undvika trunkering med parametern **width** .</span><span class="sxs-lookup"><span data-stu-id="a04cd-131">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="a04cd-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a04cd-132">PARAMETERS</span></span>

### <span data-ttu-id="a04cd-133">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a04cd-133">-InputObject</span></span>

<span data-ttu-id="a04cd-134">Anger de objekt som ska skrivas till en sträng.</span><span class="sxs-lookup"><span data-stu-id="a04cd-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="a04cd-135">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="a04cd-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a04cd-136">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="a04cd-136">-NoNewline</span></span>

<span data-ttu-id="a04cd-137">Tar bort alla newlines från utdata som genereras av PowerShell-formateraren.</span><span class="sxs-lookup"><span data-stu-id="a04cd-137">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="a04cd-138">Newlines som är en del av String-objekten bevaras.</span><span class="sxs-lookup"><span data-stu-id="a04cd-138">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="a04cd-139">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="a04cd-139">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a04cd-140">-Stream</span><span class="sxs-lookup"><span data-stu-id="a04cd-140">-Stream</span></span>

<span data-ttu-id="a04cd-141">Anger att cmdleten skickar en separat sträng för varje rad i ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="a04cd-141">Indicates that the cmdlet sends a separate string for each line of an input object.</span></span> <span data-ttu-id="a04cd-142">Som standard samlas strängarna för varje objekt in och skickas som en enskild sträng.</span><span class="sxs-lookup"><span data-stu-id="a04cd-142">By default, the strings for each object are accumulated and sent as a single string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a04cd-143">-Bredd</span><span class="sxs-lookup"><span data-stu-id="a04cd-143">-Width</span></span>

<span data-ttu-id="a04cd-144">Anger antalet tecken i varje rad utdata.</span><span class="sxs-lookup"><span data-stu-id="a04cd-144">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="a04cd-145">Eventuella ytterligare tecken radbryts till nästa rad eller trunkeras beroende på vilken cmdlet som används.</span><span class="sxs-lookup"><span data-stu-id="a04cd-145">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="a04cd-146">Parametern **width** gäller bara för objekt som formateras.</span><span class="sxs-lookup"><span data-stu-id="a04cd-146">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="a04cd-147">Om du utelämnar den här parametern bestäms bredden av egenskaperna för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="a04cd-147">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="a04cd-148">I Terminal-fönster (konsol) används den aktuella fönster bredden som standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="a04cd-148">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="a04cd-149">PowerShell-konsolens fönster är standard bredden på 80 tecken vid installation.</span><span class="sxs-lookup"><span data-stu-id="a04cd-149">PowerShell console windows default to a width of 80 characters on installation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a04cd-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a04cd-150">CommonParameters</span></span>

<span data-ttu-id="a04cd-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a04cd-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a04cd-152">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a04cd-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a04cd-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="a04cd-153">INPUTS</span></span>

### <span data-ttu-id="a04cd-154">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a04cd-154">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a04cd-155">Du kan skicka objekt nedåt i pipelinen till `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="a04cd-155">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="a04cd-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a04cd-156">OUTPUTS</span></span>

### <span data-ttu-id="a04cd-157">System. String</span><span class="sxs-lookup"><span data-stu-id="a04cd-157">System.String</span></span>

<span data-ttu-id="a04cd-158">`Out-String` Returnerar den sträng som skapas från det inmatade objektet.</span><span class="sxs-lookup"><span data-stu-id="a04cd-158">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="a04cd-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a04cd-159">NOTES</span></span>

<span data-ttu-id="a04cd-160">De cmdletar som innehåller `Out` verbet formaterar inte objekt.</span><span class="sxs-lookup"><span data-stu-id="a04cd-160">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="a04cd-161">`Out`Cmdletarna skickar objekt till Formatter för det angivna visnings målet.</span><span class="sxs-lookup"><span data-stu-id="a04cd-161">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="a04cd-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a04cd-162">RELATED LINKS</span></span>

[<span data-ttu-id="a04cd-163">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="a04cd-163">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="a04cd-164">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="a04cd-164">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="a04cd-165">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="a04cd-165">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="a04cd-166">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="a04cd-166">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="a04cd-167">Ut-null</span><span class="sxs-lookup"><span data-stu-id="a04cd-167">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="a04cd-168">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="a04cd-168">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="a04cd-169">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="a04cd-169">Out-Printer</span></span>](Out-Printer.md)
