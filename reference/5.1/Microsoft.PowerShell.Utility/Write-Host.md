---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Host
ms.openlocfilehash: 7991d28e1136eb7f578cdd559f96d4c795c147a0
ms.sourcegitcommit: 758e6dbb428295698d4852b3e19f5d03deade037
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/15/2020
ms.locfileid: "93269492"
---
# <span data-ttu-id="48116-103">Write-Host</span><span class="sxs-lookup"><span data-stu-id="48116-103">Write-Host</span></span>

## <span data-ttu-id="48116-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="48116-104">SYNOPSIS</span></span>

<span data-ttu-id="48116-105">Skriver anpassade utdata till en värd.</span><span class="sxs-lookup"><span data-stu-id="48116-105">Writes customized output to a host.</span></span>

## <span data-ttu-id="48116-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="48116-106">SYNTAX</span></span>

```
Write-Host [[-Object] <Object>] [-NoNewline] [-Separator <Object>] [-ForegroundColor <ConsoleColor>]
 [-BackgroundColor <ConsoleColor>] [<CommonParameters>]
```

## <span data-ttu-id="48116-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="48116-107">DESCRIPTION</span></span>

<span data-ttu-id="48116-108">`Write-Host`Cmdletens primära syfte är att producera för-(värd) – endast visning av utdata, till exempel att skriva ut färgad text, t. ex. när användaren uppmanas att ange indata tillsammans med [Read-Host](Read-Host.md).</span><span class="sxs-lookup"><span data-stu-id="48116-108">The `Write-Host` cmdlet's primary purpose is to produce for-(host)-display-only output, such as printing colored text like when prompting the user for input in conjunction with [Read-Host](Read-Host.md).</span></span>
<span data-ttu-id="48116-109">`Write-Host` använder metoden [toString ()](/dotnet/api/system.object.tostring) för att skriva utdata.</span><span class="sxs-lookup"><span data-stu-id="48116-109">`Write-Host` uses the [ToString()](/dotnet/api/system.object.tostring) method to write the output.</span></span> <span data-ttu-id="48116-110">Om du däremot vill mata ut data till pipelinen kan du använda [Write-output](Write-Output.md) eller implicit utdata.</span><span class="sxs-lookup"><span data-stu-id="48116-110">By contrast, to output data to the pipeline, use [Write-Output](Write-Output.md) or implicit output.</span></span>

<span data-ttu-id="48116-111">Du kan ange färg på text med hjälp av `ForegroundColor` parametern och du kan ange bakgrunds färgen med hjälp av `BackgroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="48116-111">You can specify the color of text by using the `ForegroundColor` parameter, and you can specify the background color by using the `BackgroundColor` parameter.</span></span> <span data-ttu-id="48116-112">Med parametern avgränsning kan du ange en sträng som ska användas för att separera visade objekt.</span><span class="sxs-lookup"><span data-stu-id="48116-112">The Separator parameter lets you specify a string to use to separate displayed objects.</span></span> <span data-ttu-id="48116-113">Det specifika resultatet beror på vilket program som är värd för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48116-113">The particular result depends on the program that is hosting PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="48116-114">Från och med Windows PowerShell 5,0 `Write-Host` är en omslutning som `Write-Information` gör att du kan använda `Write-Host` för att generera utdata till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="48116-114">Starting in Windows PowerShell 5.0, `Write-Host` is a wrapper for `Write-Information` This allows you to use `Write-Host` to emit output to the information stream.</span></span> <span data-ttu-id="48116-115">Detta gör det möjligt att **samla in** eller **undertrycka** data som skrivits med samtidigt som du `Write-Host` behåller bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="48116-115">This enables the **capture** or **suppression** of data written using `Write-Host` while preserving backwards compatibility.</span></span>
>
> <span data-ttu-id="48116-116">`$InformationPreference`Variabeln Preference och `InformationAction` common parameter påverkar inte `Write-Host` meddelanden.</span><span class="sxs-lookup"><span data-stu-id="48116-116">The `$InformationPreference` preference variable and `InformationAction` common parameter do not affect `Write-Host` messages.</span></span> <span data-ttu-id="48116-117">Undantaget till den här regeln är `-InformationAction Ignore` , vilket förhindrar `Write-Host` utdata.</span><span class="sxs-lookup"><span data-stu-id="48116-117">The exception to this rule is `-InformationAction Ignore`, which effectively suppresses `Write-Host` output.</span></span> <span data-ttu-id="48116-118">(se "exempel 5")</span><span class="sxs-lookup"><span data-stu-id="48116-118">(see "Example 5")</span></span>

## <span data-ttu-id="48116-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="48116-119">EXAMPLES</span></span>

### <span data-ttu-id="48116-120">Exempel 1: Skriv till konsolen utan att lägga till en ny rad</span><span class="sxs-lookup"><span data-stu-id="48116-120">Example 1: Write to the console without adding a new line</span></span>

```powershell
Write-Host "no newline test " -NoNewline
Write-Host "second string"
```

```output
no newline test second string
```

<span data-ttu-id="48116-121">Det här kommandot visar strängen "inget rad matnings test" med `NoNewline` parametern.</span><span class="sxs-lookup"><span data-stu-id="48116-121">This command displays the string 'no newline test' with the `NoNewline` parameter.</span></span>

<span data-ttu-id="48116-122">En andra sträng skrivs, men den avslutas på samma rad som första gången på grund av att en ny rad avgränsar strängarna.</span><span class="sxs-lookup"><span data-stu-id="48116-122">A second string is written, but it ends up on the same line as the first due to the absence of a newline separating the strings.</span></span>

### <span data-ttu-id="48116-123">Exempel 2: Skriv till konsolen och ta med en avgränsare</span><span class="sxs-lookup"><span data-stu-id="48116-123">Example 2: Write to the console and include a separator</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", +2= "
```

```output
2, +2= 4, +2= 6, +2= 8, +2= 10, +2= 12
```

Det här kommandot visar de jämna talen från två till tolv. <span data-ttu-id="48116-125">**Avgränsnings** parametern används för att lägga till strängen `, +2= ` (komma, blank steg,,,, `+` `2` `=` blank steg).</span><span class="sxs-lookup"><span data-stu-id="48116-125">The **Separator** parameter is used to add the string `, +2= ` (comma, space, `+`, `2`, `=`, space).</span></span>

### <span data-ttu-id="48116-126">Exempel 3: skriva med olika text-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="48116-126">Example 3: Write with different text and background colors</span></span>

```powershell
Write-Host (2,4,6,8,10,12) -Separator ", -> " -ForegroundColor DarkGreen -BackgroundColor White
```

```output
2, -> 4, -> 6, -> 8, -> 10, -> 12
```

<span data-ttu-id="48116-127">Det här kommandot visar de jämna talen från två till tolv.</span><span class="sxs-lookup"><span data-stu-id="48116-127">This command displays the even numbers from two through twelve.</span></span> <span data-ttu-id="48116-128">Den använder `ForegroundColor` parametern för att mata ut mörkt grönt text och `BackgroundColor` parametern för att visa en vit bakgrund.</span><span class="sxs-lookup"><span data-stu-id="48116-128">It uses the `ForegroundColor` parameter to output dark green text and the `BackgroundColor` parameter to display a white background.</span></span>

### <span data-ttu-id="48116-129">Exempel 4: skriva med olika text-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="48116-129">Example 4: Write with different text and background colors</span></span>

```powershell
Write-Host "Red on white text." -ForegroundColor red -BackgroundColor white
```

```output
Red on white text.
```

<span data-ttu-id="48116-130">Det här kommandot visar strängen "röd på vit text".</span><span class="sxs-lookup"><span data-stu-id="48116-130">This command displays the string "Red on white text."</span></span> <span data-ttu-id="48116-131">Texten är röd, som definieras av `ForegroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="48116-131">The text is red, as defined by the `ForegroundColor` parameter.</span></span> <span data-ttu-id="48116-132">Bakgrunden är vit, som definieras av `BackgroundColor` parametern.</span><span class="sxs-lookup"><span data-stu-id="48116-132">The background is white, as defined by the `BackgroundColor` parameter.</span></span>

### <span data-ttu-id="48116-133">Exempel 5: Ignorera utdata från Write-Host</span><span class="sxs-lookup"><span data-stu-id="48116-133">Example 5: Suppress output from Write-Host</span></span>

```powershell
# The following two statements can be used to effectively suppress output from Write-Host
Write-Host "I won't print" -InformationAction Ignore
Write-Host "I won't print" 6>$null
```

```output

```

<span data-ttu-id="48116-134">Dessa kommandon undertrycker effektivt utdata från `Write-Host` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="48116-134">These commands effectively suppress output of the `Write-Host` cmdlet.</span></span> <span data-ttu-id="48116-135">Den första använder `InformationAction` parametern med `Ignore` värdet för att ignorera utdata till informations strömmen.</span><span class="sxs-lookup"><span data-stu-id="48116-135">The first one uses the `InformationAction` parameter with the `Ignore` Value to suppress output to the information stream.</span></span>
<span data-ttu-id="48116-136">I det andra exemplet omdirigeras informations strömmen för kommandot till `$null` variabeln och därmed ignoreras den.</span><span class="sxs-lookup"><span data-stu-id="48116-136">The second example redirects the information stream of the command to the `$null` variable and thereby suppresses it.</span></span>

## <span data-ttu-id="48116-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="48116-137">PARAMETERS</span></span>

### <span data-ttu-id="48116-138">– BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="48116-138">-BackgroundColor</span></span>

<span data-ttu-id="48116-139">Anger bakgrunds färgen.</span><span class="sxs-lookup"><span data-stu-id="48116-139">Specifies the background color.</span></span> <span data-ttu-id="48116-140">Det finns inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="48116-140">There is no default.</span></span> <span data-ttu-id="48116-141">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="48116-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="48116-142">Svart</span><span class="sxs-lookup"><span data-stu-id="48116-142">Black</span></span>
- <span data-ttu-id="48116-143">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="48116-143">DarkBlue</span></span>
- <span data-ttu-id="48116-144">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="48116-144">DarkGreen</span></span>
- <span data-ttu-id="48116-145">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="48116-145">DarkCyan</span></span>
- <span data-ttu-id="48116-146">DarkRed</span><span class="sxs-lookup"><span data-stu-id="48116-146">DarkRed</span></span>
- <span data-ttu-id="48116-147">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="48116-147">DarkMagenta</span></span>
- <span data-ttu-id="48116-148">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="48116-148">DarkYellow</span></span>
- <span data-ttu-id="48116-149">Mörkgrå</span><span class="sxs-lookup"><span data-stu-id="48116-149">Gray</span></span>
- <span data-ttu-id="48116-150">DarkGray</span><span class="sxs-lookup"><span data-stu-id="48116-150">DarkGray</span></span>
- <span data-ttu-id="48116-151">Blå</span><span class="sxs-lookup"><span data-stu-id="48116-151">Blue</span></span>
- <span data-ttu-id="48116-152">Green</span><span class="sxs-lookup"><span data-stu-id="48116-152">Green</span></span>
- <span data-ttu-id="48116-153">Cyan</span><span class="sxs-lookup"><span data-stu-id="48116-153">Cyan</span></span>
- <span data-ttu-id="48116-154">Röd</span><span class="sxs-lookup"><span data-stu-id="48116-154">Red</span></span>
- <span data-ttu-id="48116-155">Röda</span><span class="sxs-lookup"><span data-stu-id="48116-155">Magenta</span></span>
- <span data-ttu-id="48116-156">Gul</span><span class="sxs-lookup"><span data-stu-id="48116-156">Yellow</span></span>
- <span data-ttu-id="48116-157">Vit</span><span class="sxs-lookup"><span data-stu-id="48116-157">White</span></span>

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

### <span data-ttu-id="48116-158">-ForegroundColor</span><span class="sxs-lookup"><span data-stu-id="48116-158">-ForegroundColor</span></span>

<span data-ttu-id="48116-159">Anger text färgen.</span><span class="sxs-lookup"><span data-stu-id="48116-159">Specifies the text color.</span></span> <span data-ttu-id="48116-160">Det finns inget standardvärde.</span><span class="sxs-lookup"><span data-stu-id="48116-160">There is no default.</span></span> <span data-ttu-id="48116-161">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="48116-161">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="48116-162">Svart</span><span class="sxs-lookup"><span data-stu-id="48116-162">Black</span></span>
- <span data-ttu-id="48116-163">DarkBlue</span><span class="sxs-lookup"><span data-stu-id="48116-163">DarkBlue</span></span>
- <span data-ttu-id="48116-164">DarkGreen</span><span class="sxs-lookup"><span data-stu-id="48116-164">DarkGreen</span></span>
- <span data-ttu-id="48116-165">DarkCyan</span><span class="sxs-lookup"><span data-stu-id="48116-165">DarkCyan</span></span>
- <span data-ttu-id="48116-166">DarkRed</span><span class="sxs-lookup"><span data-stu-id="48116-166">DarkRed</span></span>
- <span data-ttu-id="48116-167">DarkMagenta</span><span class="sxs-lookup"><span data-stu-id="48116-167">DarkMagenta</span></span>
- <span data-ttu-id="48116-168">DarkYellow</span><span class="sxs-lookup"><span data-stu-id="48116-168">DarkYellow</span></span>
- <span data-ttu-id="48116-169">Mörkgrå</span><span class="sxs-lookup"><span data-stu-id="48116-169">Gray</span></span>
- <span data-ttu-id="48116-170">DarkGray</span><span class="sxs-lookup"><span data-stu-id="48116-170">DarkGray</span></span>
- <span data-ttu-id="48116-171">Blå</span><span class="sxs-lookup"><span data-stu-id="48116-171">Blue</span></span>
- <span data-ttu-id="48116-172">Green</span><span class="sxs-lookup"><span data-stu-id="48116-172">Green</span></span>
- <span data-ttu-id="48116-173">Cyan</span><span class="sxs-lookup"><span data-stu-id="48116-173">Cyan</span></span>
- <span data-ttu-id="48116-174">Röd</span><span class="sxs-lookup"><span data-stu-id="48116-174">Red</span></span>
- <span data-ttu-id="48116-175">Röda</span><span class="sxs-lookup"><span data-stu-id="48116-175">Magenta</span></span>
- <span data-ttu-id="48116-176">Gul</span><span class="sxs-lookup"><span data-stu-id="48116-176">Yellow</span></span>
- <span data-ttu-id="48116-177">Vit</span><span class="sxs-lookup"><span data-stu-id="48116-177">White</span></span>

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

### <span data-ttu-id="48116-178">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="48116-178">-NoNewline</span></span>

<span data-ttu-id="48116-179">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="48116-179">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="48116-180">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="48116-180">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="48116-181">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="48116-181">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="48116-182">– Objekt</span><span class="sxs-lookup"><span data-stu-id="48116-182">-Object</span></span>

<span data-ttu-id="48116-183">Objekt som ska visas på värden.</span><span class="sxs-lookup"><span data-stu-id="48116-183">Objects to display in the host.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48116-184">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="48116-184">-Separator</span></span>

<span data-ttu-id="48116-185">Anger en avgränsnings sträng som ska infogas mellan objekt som visas av värden.</span><span class="sxs-lookup"><span data-stu-id="48116-185">Specifies a separator string to insert between objects displayed by the host.</span></span>

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

### <span data-ttu-id="48116-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48116-186">CommonParameters</span></span>
<span data-ttu-id="48116-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48116-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48116-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48116-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48116-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="48116-189">INPUTS</span></span>

### <span data-ttu-id="48116-190">System. Object</span><span class="sxs-lookup"><span data-stu-id="48116-190">System.Object</span></span>

<span data-ttu-id="48116-191">Du kan skicka pipe-objekt som ska skrivas till värden.</span><span class="sxs-lookup"><span data-stu-id="48116-191">You can pipe objects to be written to the host.</span></span>

## <span data-ttu-id="48116-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="48116-192">OUTPUTS</span></span>

### <span data-ttu-id="48116-193">Inget</span><span class="sxs-lookup"><span data-stu-id="48116-193">None</span></span>

<span data-ttu-id="48116-194">`Write-Host` skickar objekten till värden.</span><span class="sxs-lookup"><span data-stu-id="48116-194">`Write-Host` sends the objects to the host.</span></span> <span data-ttu-id="48116-195">Det returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="48116-195">It does not return any objects.</span></span> <span data-ttu-id="48116-196">Värden visar dock de objekt som `Write-Host` skickar till den.</span><span class="sxs-lookup"><span data-stu-id="48116-196">However, the host displays the objects that `Write-Host` sends to it.</span></span>

## <span data-ttu-id="48116-197">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="48116-197">NOTES</span></span>

- <span data-ttu-id="48116-198">När en samling skrivs till värden skrivs elementen i samlingen ut på samma rad, separerade med ett enda blank steg.</span><span class="sxs-lookup"><span data-stu-id="48116-198">When writing a collection to the host, elements of the collection are printed on the same line separated by a single space.</span></span> <span data-ttu-id="48116-199">Detta kan åsidosättas med **avgränsnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="48116-199">This can be overridden with the **Separator** parameter.</span></span>

- <span data-ttu-id="48116-200">Icke-primitiva data typer, till exempel objekt med egenskaper kan orsaka oväntade resultat och ger inte meningsfulla utdata.</span><span class="sxs-lookup"><span data-stu-id="48116-200">Non-primitive data types such as objects with properties can cause unexpected results and not provide meaningful output.</span></span> <span data-ttu-id="48116-201">Skrivs till exempel `Write-Host @{a = 1; b = 2}` `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` till värden.</span><span class="sxs-lookup"><span data-stu-id="48116-201">For example, `Write-Host @{a = 1; b = 2}` will print `System.Collections.DictionaryEntry System.Collections.DictionaryEntry` to the host.</span></span>

## <span data-ttu-id="48116-202">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="48116-202">RELATED LINKS</span></span>

[<span data-ttu-id="48116-203">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="48116-203">Clear-Host</span></span>](../Microsoft.PowerShell.Core/Clear-Host.md)

[<span data-ttu-id="48116-204">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="48116-204">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="48116-205">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="48116-205">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="48116-206">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="48116-206">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="48116-207">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="48116-207">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="48116-208">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="48116-208">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="48116-209">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="48116-209">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="48116-210">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="48116-210">Write-Warning</span></span>](Write-Warning.md)
