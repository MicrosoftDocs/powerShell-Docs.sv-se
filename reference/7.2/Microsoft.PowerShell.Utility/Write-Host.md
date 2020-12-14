---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 01d045a6254b40161462bf36976fdbf57f205705
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709367"
---
# <span data-ttu-id="7cebb-102">Write-Host</span><span class="sxs-lookup"><span data-stu-id="7cebb-102">Write-Host</span></span>

## <span data-ttu-id="7cebb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7cebb-103">SYNOPSIS</span></span>

<span data-ttu-id="7cebb-104">Skriver anpassade utdata till en värd.</span><span class="sxs-lookup"><span data-stu-id="7cebb-104">Writes customized output to a host.</span></span>

## <span data-ttu-id="7cebb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7cebb-105">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="7cebb-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7cebb-106">DESCRIPTION</span></span>

<span data-ttu-id="7cebb-107">`Write-Host`Cmdletens primära syfte är att producera för-(värd) – endast visning av utdata, till exempel att skriva ut färgad text, t. ex. när användaren uppmanas att ange indata tillsammans med [Read-Host](Read-Host.md).</span><span class="sxs-lookup"><span data-stu-id="7cebb-107">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="7cebb-108">`Write-Host` använder metoden [toString ()](/dotnet/api/system.object.tostring) för att skriva utdata.</span><span class="sxs-lookup"><span data-stu-id="7cebb-108">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="7cebb-109">Om du däremot vill mata ut data till pipelinen kan du använda [Write-output](Write-Output.md) eller implicit utdata.</span><span class="sxs-lookup"><span data-stu-id="7cebb-109">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="7cebb-110">Du kan ange färg på text med hjälp av `ForegroundColor` parametern och du kan ange bakgrunds färgen med hjälp av `BackgroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="7cebb-110">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="7cebb-111">Med parametern avgränsning kan du ange en sträng som ska användas för att separera visade objekt.</span><span class="sxs-lookup"><span data-stu-id="7cebb-111">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="7cebb-112">Det specifika resultatet beror på vilket program som är värd för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7cebb-112">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="7cebb-113">Från och med Windows PowerShell 5,0 `Write-Host` är en omslutning som `Write-Information` gör att du kan använda `Write-Host` för att generera utdata till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="7cebb-113">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="7cebb-114">Detta gör det möjligt att **samla in** eller **undertrycka** data som skrivits med samtidigt som du `Write-Host` behåller bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="7cebb-114">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="7cebb-115">`$InformationPreference`Variabeln Preference och `InformationAction` common parameter påverkar inte `Write-Host` meddelanden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-115">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="7cebb-116">Undantaget till den här regeln är `-InformationAction Ignore` , vilket förhindrar `Write-Host` utdata.</span><span class="sxs-lookup"><span data-stu-id="7cebb-116">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="7cebb-117">(se "exempel 5")</span><span class="sxs-lookup"><span data-stu-id="7cebb-117">(see "Example 5")</span></span>

## <span data-ttu-id="7cebb-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7cebb-118">EXAMPLES</span></span>

### <span data-ttu-id="7cebb-119">Exempel 1: Skriv till konsolen utan att lägga till en ny rad</span><span class="sxs-lookup"><span data-stu-id="7cebb-119">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="7cebb-120">Det här kommandot visar strängen "inget rad matnings test" med `NoNewline` parametern.</span><span class="sxs-lookup"><span data-stu-id="7cebb-120">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="7cebb-121">En andra sträng skrivs, men den avslutas på samma rad som första gången på grund av att en ny rad avgränsar strängarna.</span><span class="sxs-lookup"><span data-stu-id="7cebb-121">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="7cebb-122">Exempel 2: Skriv till konsolen och ta med en avgränsare</span><span class="sxs-lookup"><span data-stu-id="7cebb-122">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Det här kommandot visar de jämna talen från två till tolv. <span data-ttu-id="7cebb-124">**Avgränsnings** parametern används för att lägga till strängen `, +2= ` (komma, blank steg,,,, `+` `2` `=` blank steg).</span><span class="sxs-lookup"><span data-stu-id="7cebb-124">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="7cebb-125">Exempel 3: skriva med olika text-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="7cebb-125">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="7cebb-126">Det här kommandot visar de jämna talen från två till tolv.</span><span class="sxs-lookup"><span data-stu-id="7cebb-126">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="7cebb-127">Den använder `ForegroundColor` parametern för att mata ut mörkt grönt text och `BackgroundColor` parametern för att visa en vit bakgrund.</span><span class="sxs-lookup"><span data-stu-id="7cebb-127">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="7cebb-128">Exempel 4: skriva med olika text-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="7cebb-128">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="7cebb-129">Det här kommandot visar strängen "röd på vit text".</span><span class="sxs-lookup"><span data-stu-id="7cebb-129">This command displays the string "Red on white text."</span></span> <span data-ttu-id="7cebb-130">Texten är röd, som definieras av `ForegroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="7cebb-130">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="7cebb-131">Bakgrunden är vit, som definieras av `BackgroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="7cebb-131">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="7cebb-132">Exempel 5: Ignorera utdata från Write-Host</span><span class="sxs-lookup"><span data-stu-id="7cebb-132">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="7cebb-133">Dessa kommandon undertrycker effektivt utdata från `Write-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7cebb-133">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="7cebb-134">Den första använder `InformationAction` parametern med `Ignore` värdet för att ignorera utdata till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="7cebb-134">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="7cebb-135">I det andra exemplet omdirigeras informations strömmen för kommandot till `$null` variabeln och därmed ignoreras den.</span><span class="sxs-lookup"><span data-stu-id="7cebb-135">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="7cebb-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7cebb-136">PARAMETERS</span></span>

### <span data-ttu-id="7cebb-137">– BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="7cebb-137">-BackgroundColor</span></span>

<span data-ttu-id="7cebb-138">Anger bakgrunds färgen.</span><span class="sxs-lookup"><span data-stu-id="7cebb-138">Specifies the background color.</span></span> <span data-ttu-id="7cebb-139">Det finns inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7cebb-139">There is no default.</span></span> <span data-ttu-id="7cebb-140">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="7cebb-140">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7cebb-141">Svart</span><span class="sxs-lookup"><span data-stu-id="7cebb-141">Black</span></span>
- <span data-ttu-id="7cebb-142">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="7cebb-142">DarkBlue</span></span>
- <span data-ttu-id="7cebb-143">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="7cebb-143">DarkGreen</span></span>
- <span data-ttu-id="7cebb-144">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="7cebb-144">DarkCyan</span></span>
- <span data-ttu-id="7cebb-145">DarkRed</span><span class="sxs-lookup"><span data-stu-id="7cebb-145">DarkRed</span></span>
- <span data-ttu-id="7cebb-146">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="7cebb-146">DarkMagenta</span></span>
- <span data-ttu-id="7cebb-147">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="7cebb-147">DarkYellow</span></span>
- <span data-ttu-id="7cebb-148">Mörkgrå</span><span class="sxs-lookup"><span data-stu-id="7cebb-148">Gray</span></span>
- <span data-ttu-id="7cebb-149">DarkGray</span><span class="sxs-lookup"><span data-stu-id="7cebb-149">DarkGray</span></span>
- <span data-ttu-id="7cebb-150">Blå</span><span class="sxs-lookup"><span data-stu-id="7cebb-150">Blue</span></span>
- <span data-ttu-id="7cebb-151">Green</span><span class="sxs-lookup"><span data-stu-id="7cebb-151">Green</span></span>
- <span data-ttu-id="7cebb-152">Cyan</span><span class="sxs-lookup"><span data-stu-id="7cebb-152">Cyan</span></span>
- <span data-ttu-id="7cebb-153">Röd</span><span class="sxs-lookup"><span data-stu-id="7cebb-153">Red</span></span>
- <span data-ttu-id="7cebb-154">Röda</span><span class="sxs-lookup"><span data-stu-id="7cebb-154">Magenta</span></span>
- <span data-ttu-id="7cebb-155">Gul</span><span class="sxs-lookup"><span data-stu-id="7cebb-155">Yellow</span></span>
- <span data-ttu-id="7cebb-156">Vit</span><span class="sxs-lookup"><span data-stu-id="7cebb-156">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cebb-157">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="7cebb-157">-ForegroundColor</span></span>

<span data-ttu-id="7cebb-158">Anger text färgen.</span><span class="sxs-lookup"><span data-stu-id="7cebb-158">Specifies the text color.</span></span> <span data-ttu-id="7cebb-159">Det finns inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7cebb-159">There is no default.</span></span> <span data-ttu-id="7cebb-160">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="7cebb-160">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="7cebb-161">Svart</span><span class="sxs-lookup"><span data-stu-id="7cebb-161">Black</span></span>
- <span data-ttu-id="7cebb-162">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="7cebb-162">DarkBlue</span></span>
- <span data-ttu-id="7cebb-163">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="7cebb-163">DarkGreen</span></span>
- <span data-ttu-id="7cebb-164">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="7cebb-164">DarkCyan</span></span>
- <span data-ttu-id="7cebb-165">DarkRed</span><span class="sxs-lookup"><span data-stu-id="7cebb-165">DarkRed</span></span>
- <span data-ttu-id="7cebb-166">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="7cebb-166">DarkMagenta</span></span>
- <span data-ttu-id="7cebb-167">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="7cebb-167">DarkYellow</span></span>
- <span data-ttu-id="7cebb-168">Mörkgrå</span><span class="sxs-lookup"><span data-stu-id="7cebb-168">Gray</span></span>
- <span data-ttu-id="7cebb-169">DarkGray</span><span class="sxs-lookup"><span data-stu-id="7cebb-169">DarkGray</span></span>
- <span data-ttu-id="7cebb-170">Blå</span><span class="sxs-lookup"><span data-stu-id="7cebb-170">Blue</span></span>
- <span data-ttu-id="7cebb-171">Green</span><span class="sxs-lookup"><span data-stu-id="7cebb-171">Green</span></span>
- <span data-ttu-id="7cebb-172">Cyan</span><span class="sxs-lookup"><span data-stu-id="7cebb-172">Cyan</span></span>
- <span data-ttu-id="7cebb-173">Röd</span><span class="sxs-lookup"><span data-stu-id="7cebb-173">Red</span></span>
- <span data-ttu-id="7cebb-174">Röda</span><span class="sxs-lookup"><span data-stu-id="7cebb-174">Magenta</span></span>
- <span data-ttu-id="7cebb-175">Gul</span><span class="sxs-lookup"><span data-stu-id="7cebb-175">Yellow</span></span>
- <span data-ttu-id="7cebb-176">Vit</span><span class="sxs-lookup"><span data-stu-id="7cebb-176">White</span></span>

```yaml
Type: System.ConsoleColor
Parameter Sets: (All)
Aliases:
Accepted values: Black, DarkBlue, DarkGreen, DarkCyan, DarkRed, DarkMagenta, DarkYellow, Gray, DarkGray, Blue, Green, Cyan, Red, Magenta, Yellow, White

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cebb-177">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="7cebb-177">-NoNewline</span></span>

<span data-ttu-id="7cebb-178">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="7cebb-178">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="7cebb-179">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="7cebb-179">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="7cebb-180">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="7cebb-180">No newline is added after the last output string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cebb-181">– Objekt</span><span class="sxs-lookup"><span data-stu-id="7cebb-181">-Object</span></span>

<span data-ttu-id="7cebb-182">Objekt som ska visas på värden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-182">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Msg, Message

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7cebb-183">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="7cebb-183">-Separator</span></span>

<span data-ttu-id="7cebb-184">Anger en avgränsnings sträng som ska infogas mellan objekt som visas av värden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-184">Specifies a separator string to insert between objects displayed by the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7cebb-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7cebb-185">CommonParameters</span></span>
<span data-ttu-id="7cebb-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7cebb-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7cebb-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7cebb-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7cebb-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="7cebb-188">INPUTS</span></span>

### <span data-ttu-id="7cebb-189">System. Object</span><span class="sxs-lookup"><span data-stu-id="7cebb-189">System.Object</span></span>

<span data-ttu-id="7cebb-190">Du kan skicka pipe-objekt som ska skrivas till värden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-190">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="7cebb-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7cebb-191">OUTPUTS</span></span>

### <span data-ttu-id="7cebb-192">Inga</span><span class="sxs-lookup"><span data-stu-id="7cebb-192">None</span></span>

<span data-ttu-id="7cebb-193">`Write-Host` skickar objekten till värden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-193">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="7cebb-194">Det returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="7cebb-194">It does not return any objects.</span></span> <span data-ttu-id="7cebb-195">Värden visar dock de objekt som `Write-Host` skickar till den.</span><span class="sxs-lookup"><span data-stu-id="7cebb-195">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="7cebb-196">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7cebb-196">NOTES</span></span>

- <span data-ttu-id="7cebb-197">När en samling skrivs till värden skrivs elementen i samlingen ut på samma rad, separerade med ett enda blank steg.</span><span class="sxs-lookup"><span data-stu-id="7cebb-197">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="7cebb-198">Detta kan åsidosättas med **avgränsnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="7cebb-198">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="7cebb-199">Icke-primitiva data typer, till exempel objekt med egenskaper kan orsaka oväntade resultat och ger inte meningsfulla utdata.</span><span class="sxs-lookup"><span data-stu-id="7cebb-199">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="7cebb-200">Skrivs till exempel `Write-Host @{a = 1; b = 2}` `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` till värden.</span><span class="sxs-lookup"><span data-stu-id="7cebb-200">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="7cebb-201">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7cebb-201">RELATED LINKS</span></span>

[<span data-ttu-id="7cebb-202">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="7cebb-202">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="7cebb-203">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="7cebb-203">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="7cebb-204">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="7cebb-204">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="7cebb-205">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="7cebb-205">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="7cebb-206">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="7cebb-206">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="7cebb-207">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="7cebb-207">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="7cebb-208">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="7cebb-208">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="7cebb-209">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="7cebb-209">Write-Warning</span></span>](Write-Warning.md)
