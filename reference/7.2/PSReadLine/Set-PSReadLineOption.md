---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: cac2c2bb8ce1f3a28c0d91c7503b3ac4d038ccad
ms.sourcegitcommit: 077488408c820c860131382324bdd576d0edf52a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95514950"
---
# <span data-ttu-id="81bed-102">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="81bed-102">Set-PSReadLineOption</span></span>

## <span data-ttu-id="81bed-103">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="81bed-103">Synopsis</span></span>
<span data-ttu-id="81bed-104">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="81bed-104">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="81bed-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="81bed-105">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func`2[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action`1[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-PredictionSource <PredictionSource>]
 [-PredictionViewStyle <PredictionViewStyle>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="81bed-106">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="81bed-106">Description</span></span>

<span data-ttu-id="81bed-107">`Set-PSReadLineOption`Cmdleten anpassar beteendet för **PSReadLine** -modulen när du redigerar kommando raden.</span><span class="sxs-lookup"><span data-stu-id="81bed-107">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="81bed-108">Använd om du vill visa **PSReadLine** -inställningarna `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="81bed-108">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="81bed-109">Exempel</span><span class="sxs-lookup"><span data-stu-id="81bed-109">Examples</span></span>

### <span data-ttu-id="81bed-110">Exempel 1: Ange förgrunds-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="81bed-110">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="81bed-111">I det här exemplet anges **PSReadLine** för att visa **kommentars** -token med grön förgrunds text på en grå bakgrund.</span><span class="sxs-lookup"><span data-stu-id="81bed-111">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="81bed-112">I Escape-sekvensen som används i exemplet representerar **32** förgrunds färgen och **47** representerar bakgrunds färgen.</span><span class="sxs-lookup"><span data-stu-id="81bed-112">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="`e[32;47m" }
```

<span data-ttu-id="81bed-113">Du kan välja att bara ange en förgrunds text färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-113">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="81bed-114">Till exempel en ljus grön förgrunds text färg för **kommentarens** token: ``"Comment"="`e[92m"`` .</span><span class="sxs-lookup"><span data-stu-id="81bed-114">For example, a bright green foreground text color for the **Comment** token: ``"Comment"="`e[92m"``.</span></span>

### <span data-ttu-id="81bed-115">Exempel 2: Ange klock format</span><span class="sxs-lookup"><span data-stu-id="81bed-115">Example 2: Set bell style</span></span>

<span data-ttu-id="81bed-116">I det här exemplet kommer **PSReadLine** att svara på fel eller villkor som kräver åtgärder från användaren.</span><span class="sxs-lookup"><span data-stu-id="81bed-116">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="81bed-117">**BellStyle** har ställts in för att avge en ljud signal vid 1221 Hz för 60 MS.</span><span class="sxs-lookup"><span data-stu-id="81bed-117">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="81bed-118">Den här funktionen kanske inte fungerar på alla värdar på plattformar.</span><span class="sxs-lookup"><span data-stu-id="81bed-118">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="81bed-119">Exempel 3: ange flera alternativ</span><span class="sxs-lookup"><span data-stu-id="81bed-119">Example 3: Set multiple options</span></span>

<span data-ttu-id="81bed-120">`Set-PSReadLineOption` kan ange flera alternativ med en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="81bed-120">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

```powershell
$PSReadLineOptions = @{
    EditMode = "Emacs"
    HistoryNoDuplicates = $true
    HistorySearchCursorMovesToEnd = $true
    Colors = @{
        "Command" = "#8181f7"
    }
}
Set-PSReadLineOption @PSReadLineOptions
```

<span data-ttu-id="81bed-121">`$PSReadLineOptions`Hash-tabellen anger nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="81bed-121">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="81bed-122">`Set-PSReadLineOption` använder nycklar och värden med `@PSReadLineOptions` för att uppdatera **PSReadLine** -alternativen.</span><span class="sxs-lookup"><span data-stu-id="81bed-122">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="81bed-123">Du kan visa nycklar och värden som anger namnet på hash-tabellen `$PSReadLineOptions` på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="81bed-123">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="81bed-124">Exempel 4: ange flera färg alternativ</span><span class="sxs-lookup"><span data-stu-id="81bed-124">Example 4: Set multiple color options</span></span>

<span data-ttu-id="81bed-125">Det här exemplet visar hur du ställer in fler än ett färg värde i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="81bed-125">This example shows how to set more than one color value in a single command.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
  Command            = 'Magenta'
  Number             = 'DarkGray'
  Member             = 'DarkGray'
  Operator           = 'DarkGray'
  Type               = 'DarkGray'
  Variable           = 'DarkGreen'
  Parameter          = 'DarkGreen'
  ContinuationPrompt = 'DarkGray'
  Default            = 'DarkGray'
}
```

### <span data-ttu-id="81bed-126">Exempel 5: Ange färg värden för flera typer</span><span class="sxs-lookup"><span data-stu-id="81bed-126">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="81bed-127">Det här exemplet visar tre olika metoder för hur du ställer in färgen på tokens som visas i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="81bed-127">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

```powershell
Set-PSReadLineOption -Colors @{
 # Use a ConsoleColor enum
 "Error" = [ConsoleColor]::DarkRed

 # 24 bit color escape sequence
 "String" = "$([char]0x1b)[38;5;100m"

 # RGB value
 "Command" = "#8181f7"
}
```

### <span data-ttu-id="81bed-128">Exempel 6: Använd ViModeChangeHandler för att Visa läges ändringar i vi</span><span class="sxs-lookup"><span data-stu-id="81bed-128">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="81bed-129">Det här exemplet ger en markör ändring VT Escape som svar på en ändring i ändrings läget i **vi** .</span><span class="sxs-lookup"><span data-stu-id="81bed-129">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "`e[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "`e[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="81bed-130">Funktionen **OnViModeChange** anger markör alternativen **för lägen för** lägen: INSERT och Command.</span><span class="sxs-lookup"><span data-stu-id="81bed-130">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="81bed-131">**ViModeChangeHandler** använder `Function:` providern för att referera till **OnViModeChange** som ett skript Blocks objekt.</span><span class="sxs-lookup"><span data-stu-id="81bed-131">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="81bed-132">Mer information finns i [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span><span class="sxs-lookup"><span data-stu-id="81bed-132">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="81bed-133">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="81bed-133">Parameters</span></span>

### <span data-ttu-id="81bed-134">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-134">-AddToHistoryHandler</span></span>

<span data-ttu-id="81bed-135">Anger en **script block** som styr vilka kommandon som läggs till i **PSReadLine** -historiken.</span><span class="sxs-lookup"><span data-stu-id="81bed-135">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="81bed-136">**Script block** tar emot kommando raden som inmatad.</span><span class="sxs-lookup"><span data-stu-id="81bed-136">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="81bed-137">Om **script block** returnerar `$True` läggs kommando raden till i historiken.</span><span class="sxs-lookup"><span data-stu-id="81bed-137">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

```yaml
Type: System.Func`2[System.String,System.Object]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-138">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="81bed-138">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="81bed-139">Det här alternativet är endast för Windows när indatatypen omdirigeras, till exempel när du kör under `tmux` eller `screen` .</span><span class="sxs-lookup"><span data-stu-id="81bed-139">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="81bed-140">Vid Omdirigerad inaktivitet i Windows skickas många nycklar som en sekvens med tecken som börjar med Escape-tecknet.</span><span class="sxs-lookup"><span data-stu-id="81bed-140">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="81bed-141">Det är omöjligt att skilja mellan ett enda escape-tecken följt av fler tecken och en giltig escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="81bed-141">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="81bed-142">Antagandet är att terminalen kan skicka tecknen snabbare än en användar typ.</span><span class="sxs-lookup"><span data-stu-id="81bed-142">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="81bed-143">**PSReadLine** väntar för denna timeout innan den tar emot en komplett escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="81bed-143">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="81bed-144">Om du ser slumpmässiga eller oväntade tecken när du skriver kan du justera denna tids gräns.</span><span class="sxs-lookup"><span data-stu-id="81bed-144">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-145">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="81bed-145">-BellStyle</span></span>

<span data-ttu-id="81bed-146">Anger hur **PSReadLine** reagerar på olika fel och tvetydiga villkor.</span><span class="sxs-lookup"><span data-stu-id="81bed-146">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="81bed-147">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="81bed-147">The valid values are as follows:</span></span>

- <span data-ttu-id="81bed-148">**Hörbar**: en kort signal.</span><span class="sxs-lookup"><span data-stu-id="81bed-148">**Audible**: A short beep.</span></span>
- <span data-ttu-id="81bed-149">**Visuellt**: text blinkar en kort stund.</span><span class="sxs-lookup"><span data-stu-id="81bed-149">**Visual**: Text flashes briefly.</span></span>
- <span data-ttu-id="81bed-150">**Ingen**: ingen feedback.</span><span class="sxs-lookup"><span data-stu-id="81bed-150">**None**: No feedback.</span></span>

```yaml
Type: Microsoft.PowerShell.BellStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Audible
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-151">– Färger</span><span class="sxs-lookup"><span data-stu-id="81bed-151">-Colors</span></span>

<span data-ttu-id="81bed-152">Parametern **Colors** anger olika färger som används av **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="81bed-152">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="81bed-153">Argumentet är en hash-tabell där nycklarna anger vilka element och värden som anger färgen.</span><span class="sxs-lookup"><span data-stu-id="81bed-153">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="81bed-154">Mer information finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="81bed-154">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="81bed-155">Färger kan vara antingen ett värde från **ConsoleColor**, till exempel `[ConsoleColor]::Red` eller en giltig ANSI-escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="81bed-155">Colors can be either a value from **ConsoleColor**, for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="81bed-156">Giltiga escape-sekvenser beror på terminalen.</span><span class="sxs-lookup"><span data-stu-id="81bed-156">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="81bed-157">I PowerShell 5,0 är ett exempel på en escape-sekvens för röd text `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="81bed-157">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="81bed-158">I PowerShell 6 och senare är samma escape-sekvens `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="81bed-158">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="81bed-159">Du kan ange andra escape-sekvenser, inklusive följande typer:</span><span class="sxs-lookup"><span data-stu-id="81bed-159">You can specify other escape sequences including the following types:</span></span>

<span data-ttu-id="81bed-160">Två färg inställningar har lagts till för att stödja anpassning av `ListView` PSReadLine-2.2.0:</span><span class="sxs-lookup"><span data-stu-id="81bed-160">Two color settings were added to support customization of the `ListView` in PSReadLine 2.2.0:</span></span>

- <span data-ttu-id="81bed-161">**ListPredictionColor** – Ange färg för det inledande `>` tecknet och det efterföljande käll namnet, t. ex. `[History]` .</span><span class="sxs-lookup"><span data-stu-id="81bed-161">**ListPredictionColor** - set color for the leading `>` character and the trailing source name, e.g. `[History]`.</span></span> <span data-ttu-id="81bed-162">Som standard används den `DarkYellow` som förgrunds färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-162">By default, it uses `DarkYellow` as the foreground color.</span></span>
- <span data-ttu-id="81bed-163">**ListPredictionSelectedColor** – Ange färg för att indikera att ett List objekt är markerat.</span><span class="sxs-lookup"><span data-stu-id="81bed-163">**ListPredictionSelectedColor** - set color for indicating a list item is selected.</span></span> <span data-ttu-id="81bed-164">Som standard används den `DarkBlack` som bakgrunds färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-164">By default, it uses `DarkBlack` as the background color.</span></span>

- <span data-ttu-id="81bed-165">256-färg</span><span class="sxs-lookup"><span data-stu-id="81bed-165">256 color</span></span>
- <span data-ttu-id="81bed-166">24-bitars färg</span><span class="sxs-lookup"><span data-stu-id="81bed-166">24-bit color</span></span>
- <span data-ttu-id="81bed-167">Förgrund, bakgrund eller både och</span><span class="sxs-lookup"><span data-stu-id="81bed-167">Foreground, background, or both</span></span>
- <span data-ttu-id="81bed-168">Invertera, fet</span><span class="sxs-lookup"><span data-stu-id="81bed-168">Inverse, bold</span></span>

<span data-ttu-id="81bed-169">Mer information om ANSI Color-koder finns i [ANSI Escape Code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in wikipedia.</span><span class="sxs-lookup"><span data-stu-id="81bed-169">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="81bed-170">Giltiga nycklar är:</span><span class="sxs-lookup"><span data-stu-id="81bed-170">The valid keys include:</span></span>

- <span data-ttu-id="81bed-171">**ContinuationPrompt**: färgen på fortsättnings frågan.</span><span class="sxs-lookup"><span data-stu-id="81bed-171">**ContinuationPrompt**: The color of the continuation prompt.</span></span>
- <span data-ttu-id="81bed-172">**Betoning**: betonings färgen.</span><span class="sxs-lookup"><span data-stu-id="81bed-172">**Emphasis**: The emphasis color.</span></span> <span data-ttu-id="81bed-173">Till exempel den matchande texten vid sökning efter historik.</span><span class="sxs-lookup"><span data-stu-id="81bed-173">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="81bed-174">**Fel**: fel färgen.</span><span class="sxs-lookup"><span data-stu-id="81bed-174">**Error**: The error color.</span></span> <span data-ttu-id="81bed-175">Till exempel i prompten.</span><span class="sxs-lookup"><span data-stu-id="81bed-175">For example, in the prompt.</span></span>
- <span data-ttu-id="81bed-176">**Markering**: färgen för att markera meny markeringen eller den markerade texten.</span><span class="sxs-lookup"><span data-stu-id="81bed-176">**Selection**: The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="81bed-177">**Standard**: standardvärdet för token.</span><span class="sxs-lookup"><span data-stu-id="81bed-177">**Default**: The default token color.</span></span>
- <span data-ttu-id="81bed-178">**Comment**: kommentarens token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-178">**Comment**: The comment token color.</span></span>
- <span data-ttu-id="81bed-179">**Nyckelord**: token för nyckelord.</span><span class="sxs-lookup"><span data-stu-id="81bed-179">**Keyword**: The keyword token color.</span></span>
- <span data-ttu-id="81bed-180">**Sträng**: strängens token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-180">**String**: The string token color.</span></span>
- <span data-ttu-id="81bed-181">**Operator**: operatorns token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-181">**Operator**: The operator token color.</span></span>
- <span data-ttu-id="81bed-182">**Variabel**: variabelns token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-182">**Variable**: The variable token color.</span></span>
- <span data-ttu-id="81bed-183">**Kommando**: kommando-token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-183">**Command**: The command token color.</span></span>
- <span data-ttu-id="81bed-184">**Parameter**: parameterns token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-184">**Parameter**: The parameter token color.</span></span>
- <span data-ttu-id="81bed-185">**Skriv**: typens token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-185">**Type**: The type token color.</span></span>
- <span data-ttu-id="81bed-186">**Number**: standardvärdet för token.</span><span class="sxs-lookup"><span data-stu-id="81bed-186">**Number**: The number token color.</span></span>
- <span data-ttu-id="81bed-187">**Medlem**: medlems namnets token-färg.</span><span class="sxs-lookup"><span data-stu-id="81bed-187">**Member**: The member name token color.</span></span>
- <span data-ttu-id="81bed-188">**InlinePrediction**: färgen på den infogade vyn för det förutsägande förslaget.</span><span class="sxs-lookup"><span data-stu-id="81bed-188">**InlinePrediction**: The color for the inline view of the predictive suggestion.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-189">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-189">-CommandValidationHandler</span></span>

<span data-ttu-id="81bed-190">Anger en **script block** som anropas från **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="81bed-190">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="81bed-191">Om ett undantag genereras Miss lyckas valideringen och felet rapporteras.</span><span class="sxs-lookup"><span data-stu-id="81bed-191">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="81bed-192">Innan ett undantag utlöses kan validerings hanteraren placera markören vid fel punkten så att den blir lättare att åtgärda.</span><span class="sxs-lookup"><span data-stu-id="81bed-192">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="81bed-193">En verifierings hanterare kan också ändra kommando raden, till exempel för att korrigera vanliga typografiska fel.</span><span class="sxs-lookup"><span data-stu-id="81bed-193">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="81bed-194">**ValidateAndAcceptLine** används för att undvika att historiken rensas med kommandon som inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="81bed-194">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

```yaml
Type: System.Action`1[System.Management.Automation.Language.CommandAst]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-195">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="81bed-195">-CompletionQueryItems</span></span>

<span data-ttu-id="81bed-196">Anger det maximala antalet slutförda objekt som visas utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="81bed-196">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="81bed-197">Om antalet objekt som ska visas är större än det här värdet visas **PSReadLine** **Ja/Nej** innan slut för ande objekt visas.</span><span class="sxs-lookup"><span data-stu-id="81bed-197">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 100
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-198">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="81bed-198">-ContinuationPrompt</span></span>

<span data-ttu-id="81bed-199">Anger den sträng som visas i början av efterföljande rader när flera rader skrivs in.</span><span class="sxs-lookup"><span data-stu-id="81bed-199">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="81bed-200">Standardvärdet är Double större än-tecken ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="81bed-200">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="81bed-201">En tom sträng är giltig.</span><span class="sxs-lookup"><span data-stu-id="81bed-201">An empty string is valid.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-202">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="81bed-202">-DingDuration</span></span>

<span data-ttu-id="81bed-203">Anger längden på pip när **BellStyle** är inställd på **hörbar**.</span><span class="sxs-lookup"><span data-stu-id="81bed-203">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 50ms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-204">-DingTone</span><span class="sxs-lookup"><span data-stu-id="81bed-204">-DingTone</span></span>

<span data-ttu-id="81bed-205">Anger tonen i Hertz (Hz) för pip när **BellStyle** är inställt på **hörbar**.</span><span class="sxs-lookup"><span data-stu-id="81bed-205">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1221
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-206">– EditMode</span><span class="sxs-lookup"><span data-stu-id="81bed-206">-EditMode</span></span>

<span data-ttu-id="81bed-207">Anger kommando rads redigerings läge.</span><span class="sxs-lookup"><span data-stu-id="81bed-207">Specifies the command line editing mode.</span></span> <span data-ttu-id="81bed-208">Om du använder den här parametern återställs alla nyckel bindningar som anges av `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="81bed-208">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="81bed-209">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="81bed-209">The valid values are as follows:</span></span>

- <span data-ttu-id="81bed-210">**Windows**: nyckel bindningar emulerar PowerShell, cmd och Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81bed-210">**Windows**: Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="81bed-211">**Emacs**: nyckel bindningar emulerar bash eller emacs.</span><span class="sxs-lookup"><span data-stu-id="81bed-211">**Emacs**: Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="81bed-212">**Vi**: nyckel bindningar emulerar vi.</span><span class="sxs-lookup"><span data-stu-id="81bed-212">**Vi**: Key bindings emulate Vi.</span></span>

<span data-ttu-id="81bed-213">Används `Get-PSReadLineKeyHandler` för att se nyckel bindningarna för den aktuella konfigurerade **EditMode**.</span><span class="sxs-lookup"><span data-stu-id="81bed-213">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

```yaml
Type: Microsoft.PowerShell.EditMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-214">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="81bed-214">-ExtraPromptLineCount</span></span>

<span data-ttu-id="81bed-215">Anger antalet extra rader.</span><span class="sxs-lookup"><span data-stu-id="81bed-215">Specifies the number of extra lines.</span></span>

<span data-ttu-id="81bed-216">Om din prompt omfattar fler än en rad anger du ett värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="81bed-216">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="81bed-217">Använd det här alternativet om du vill att extra rader ska vara tillgängliga när **PSReadLine** visar frågan när du har visat några utdata.</span><span class="sxs-lookup"><span data-stu-id="81bed-217">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="81bed-218">**PSReadLine** returnerar till exempel en lista över slut för ande.</span><span class="sxs-lookup"><span data-stu-id="81bed-218">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="81bed-219">Det här alternativet krävs mindre än i tidigare versioner av **PSReadLine**, men är användbart när `InvokePrompt` funktionen används.</span><span class="sxs-lookup"><span data-stu-id="81bed-219">This option is needed less than in previous versions of **PSReadLine**, but is useful when the `InvokePrompt` function is used.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-220">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="81bed-220">-HistoryNoDuplicates</span></span>

<span data-ttu-id="81bed-221">Det här alternativet styr återställnings beteendet.</span><span class="sxs-lookup"><span data-stu-id="81bed-221">This option controls the recall behavior.</span></span> <span data-ttu-id="81bed-222">Dubbla kommandon läggs fortfarande till i historik filen.</span><span class="sxs-lookup"><span data-stu-id="81bed-222">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="81bed-223">När det här alternativet är inställt visas bara det senaste anropet när du anropar kommandon.</span><span class="sxs-lookup"><span data-stu-id="81bed-223">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="81bed-224">Upprepade kommandon läggs till i historiken för att bevara ordning under återkallning.</span><span class="sxs-lookup"><span data-stu-id="81bed-224">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="81bed-225">Du vill dock vanligt vis inte se kommandot flera gånger vid återanrop eller sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="81bed-225">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="81bed-226">Som standard är egenskapen **HistoryNoDuplicates** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-226">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="81bed-227">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-227">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="81bed-228">Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-228">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="81bed-229">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="81bed-229">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistoryNoDuplicates = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-230">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="81bed-230">-HistorySavePath</span></span>

<span data-ttu-id="81bed-231">Anger sökvägen till filen där historiken sparas.</span><span class="sxs-lookup"><span data-stu-id="81bed-231">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="81bed-232">Datorer som kör Windows-eller icke-Windows-plattformar lagrar filen på olika platser.</span><span class="sxs-lookup"><span data-stu-id="81bed-232">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="81bed-233">Fil namnet lagras i en variabel `$($host.Name)_history.txt` , till exempel `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="81bed-233">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="81bed-234">Om du inte använder den här parametern är standard Sök vägen följande:</span><span class="sxs-lookup"><span data-stu-id="81bed-234">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="81bed-235">**Windows**</span><span class="sxs-lookup"><span data-stu-id="81bed-235">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="81bed-236">**icke-Windows**</span><span class="sxs-lookup"><span data-stu-id="81bed-236">**non-Windows**</span></span>

`$env:XDG_DATA_HOME/powershell/PSReadLine\$($host.Name)_history.txt`

`$env:HOME/.local/share/powershell/PSReadLine\$($host.Name)_history.txt`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: A file named $($host.Name)_history.txt in $env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine on Windows and $env:XDG_DATA_HOME/powershell/PSReadLine or $env:HOME/.local/share/powershell/PSReadLine on non-Windows platforms
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-237">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="81bed-237">-HistorySaveStyle</span></span>

<span data-ttu-id="81bed-238">Anger hur **PSReadLine** sparas i historiken.</span><span class="sxs-lookup"><span data-stu-id="81bed-238">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="81bed-239">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="81bed-239">Valid values are as follows:</span></span>

- <span data-ttu-id="81bed-240">**SaveIncrementally**: spara historik när varje kommando körs och delas över flera instanser av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81bed-240">**SaveIncrementally**: Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="81bed-241">**SaveAtExit**: Lägg till historik fil när PowerShell avslutas.</span><span class="sxs-lookup"><span data-stu-id="81bed-241">**SaveAtExit**: Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="81bed-242">**SaveNothing**: Använd inte en historik fil.</span><span class="sxs-lookup"><span data-stu-id="81bed-242">**SaveNothing**: Don't use a history file.</span></span>

```yaml
Type: Microsoft.PowerShell.HistorySaveStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SaveIncrementally
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-243">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="81bed-243">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="81bed-244">Anger att historik sökning är Skift läges känsligt i funktioner som **ReverseSearchHistory** eller **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="81bed-244">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="81bed-245">Som standard är egenskapen **HistorySearchCaseSensitive** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-245">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="81bed-246">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-246">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="81bed-247">Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-247">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="81bed-248">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="81bed-248">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCaseSensitive = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-249">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="81bed-249">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="81bed-250">Anger att markören flyttas till slutet av de kommandon som du läser in från historiken med hjälp av en sökning.</span><span class="sxs-lookup"><span data-stu-id="81bed-250">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="81bed-251">När den här parametern är inställd på `$False` stannar markören kvar på den plats där du tryckte på uppåt-eller nedpilarna.</span><span class="sxs-lookup"><span data-stu-id="81bed-251">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="81bed-252">Som standard är egenskapen **HistorySearchCursorMovesToEnd** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-252">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="81bed-253">Med den här **SwitchParameter** anger du egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-253">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="81bed-254">Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-254">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="81bed-255">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="81bed-255">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).HistorySearchCursorMovesToEnd = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-256">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="81bed-256">-MaximumHistoryCount</span></span>

<span data-ttu-id="81bed-257">Anger det maximala antalet kommandon som ska sparas i **PSReadLine** historik.</span><span class="sxs-lookup"><span data-stu-id="81bed-257">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="81bed-258">**PSReadLine** -historiken är separat från PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="81bed-258">**PSReadLine** history is separate from PowerShell history.</span></span>

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

### <span data-ttu-id="81bed-259">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="81bed-259">-MaximumKillRingCount</span></span>

<span data-ttu-id="81bed-260">Anger det maximala antalet objekt som lagras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="81bed-260">Specifies the maximum number of items stored in the kill ring.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-261">-PromptText</span><span class="sxs-lookup"><span data-stu-id="81bed-261">-PromptText</span></span>

<span data-ttu-id="81bed-262">När ett parsningsfel uppstår ändrar **PSReadLine** en del av meddelandet Red.</span><span class="sxs-lookup"><span data-stu-id="81bed-262">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="81bed-263">**PSReadLine** analyserar funktionen prompt för att bestämma hur du bara vill ändra färgen på en del av din prompt.</span><span class="sxs-lookup"><span data-stu-id="81bed-263">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="81bed-264">Den här analysen är inte 100% tillförlitlig.</span><span class="sxs-lookup"><span data-stu-id="81bed-264">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="81bed-265">Använd det här alternativet om **PSReadLine** ändrar din prompt på oväntade sätt.</span><span class="sxs-lookup"><span data-stu-id="81bed-265">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="81bed-266">Ta med eventuella avslutande blank steg.</span><span class="sxs-lookup"><span data-stu-id="81bed-266">Include any trailing whitespace.</span></span>

<span data-ttu-id="81bed-267">Exempel: om din prompt-funktion såg ut som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="81bed-267">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="81bed-268">Ange sedan:</span><span class="sxs-lookup"><span data-stu-id="81bed-268">Then set:</span></span>

`Set-PSReadLineOption -PromptText "# "`

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: >
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-269">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="81bed-269">-ShowToolTips</span></span>

<span data-ttu-id="81bed-270">När du visar möjliga kompletteringar visas knapp beskrivningar i listan med slutförda.</span><span class="sxs-lookup"><span data-stu-id="81bed-270">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="81bed-271">Det här alternativet är aktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="81bed-271">This option is enabled by default.</span></span> <span data-ttu-id="81bed-272">Det här alternativet är inte aktiverat som standard i tidigare versioner av **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="81bed-272">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="81bed-273">Om du vill inaktivera aktiverar du det här alternativet `$False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-273">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="81bed-274">Som standard är egenskapen **ShowToolTips** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-274">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="81bed-275">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="81bed-275">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="81bed-276">Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="81bed-276">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="81bed-277">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="81bed-277">Using the following command, you can set the property value directly:</span></span>

`(Get-PSReadLineOption).ShowToolTips = $False`

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-278">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-278">-ViModeChangeHandler</span></span>

<span data-ttu-id="81bed-279">När **ViModeIndicator** är inställt på `Script` , anropas det angivna skript blocket varje gång läget ändras.</span><span class="sxs-lookup"><span data-stu-id="81bed-279">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="81bed-280">Skript blocket anges med ett argument av typen `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="81bed-280">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="81bed-281">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="81bed-281">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-282">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="81bed-282">-ViModeIndicator</span></span>

<span data-ttu-id="81bed-283">Det här alternativet anger den visuella indikationen för det aktuella läget i **vi** .</span><span class="sxs-lookup"><span data-stu-id="81bed-283">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="81bed-284">Antingen infognings läge eller kommando läge.</span><span class="sxs-lookup"><span data-stu-id="81bed-284">Either insert mode or command mode.</span></span>

<span data-ttu-id="81bed-285">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="81bed-285">The valid values are as follows:</span></span>

- <span data-ttu-id="81bed-286">**Ingen**: det finns ingen indikation.</span><span class="sxs-lookup"><span data-stu-id="81bed-286">**None**: There's no indication.</span></span>
- <span data-ttu-id="81bed-287">**Prompt**: färg ändrings färgen visas.</span><span class="sxs-lookup"><span data-stu-id="81bed-287">**Prompt**: The prompt changes color.</span></span>
- <span data-ttu-id="81bed-288">**Markör**: markören ändrar storlek.</span><span class="sxs-lookup"><span data-stu-id="81bed-288">**Cursor**: The cursor changes size.</span></span>
- <span data-ttu-id="81bed-289">**Skript**: Användardefinierad text skrivs ut.</span><span class="sxs-lookup"><span data-stu-id="81bed-289">**Script**: User-specified text is printed.</span></span>

```yaml
Type: Microsoft.PowerShell.ViModeStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-290">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="81bed-290">-WordDelimiters</span></span>

<span data-ttu-id="81bed-291">Anger tecken som begränsar ord för funktioner som **ForwardWord** eller **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="81bed-291">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: ;:,.[]{}()/\|^&*-=+'"---
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-292">-PredictionSource</span><span class="sxs-lookup"><span data-stu-id="81bed-292">-PredictionSource</span></span>

<span data-ttu-id="81bed-293">Anger källan för PSReadLine för att få förutsägelse förslag.</span><span class="sxs-lookup"><span data-stu-id="81bed-293">Specifies the source for PSReadLine to get predictive suggestions.</span></span>

<span data-ttu-id="81bed-294">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="81bed-294">Valid values are:</span></span>

- <span data-ttu-id="81bed-295">**Ingen** – inaktivera förutsägande IntelliSense-funktionen (standard).</span><span class="sxs-lookup"><span data-stu-id="81bed-295">**None** - disable the predictive IntelliSense feature (default).</span></span>
<span data-ttu-id="81bed-296">-\`**Historik** – aktivera den förutsägande IntelliSense-funktionen och Använd PSReadLine-historiken som den enda källan.</span><span class="sxs-lookup"><span data-stu-id="81bed-296">-\`**History** - enable the predictive IntelliSense feature and use the PSReadLine history as the only source.</span></span>
- <span data-ttu-id="81bed-297">**Plugin-program** – aktivera den förutsägande IntelliSense-funktionen och Använd plugin-programmet ( `CommandPrediction` ) som den enda källan.</span><span class="sxs-lookup"><span data-stu-id="81bed-297">**Plugin** - enable the predictive IntelliSense feature and use the plugins (`CommandPrediction`) as the only source.</span></span> <span data-ttu-id="81bed-298">Det här värdet lades till i PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="81bed-298">This value was added in PSReadLine 2.2.0</span></span>
- <span data-ttu-id="81bed-299">**HistoryAndPlugin** – aktivera funktionen för förutsägelse IntelliSense och Använd både historik och plugin-program som källor.</span><span class="sxs-lookup"><span data-stu-id="81bed-299">**HistoryAndPlugin** - enable the predictive IntelliSense feature and use both history and plugin as the sources.</span></span> <span data-ttu-id="81bed-300">Det här värdet lades till i PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="81bed-300">This value was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionSource
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-301">-PredictionViewStyle</span><span class="sxs-lookup"><span data-stu-id="81bed-301">-PredictionViewStyle</span></span>

<span data-ttu-id="81bed-302">Anger formatet för visning av förutsägelse text.</span><span class="sxs-lookup"><span data-stu-id="81bed-302">Sets the style for the display of the predictive text.</span></span> <span data-ttu-id="81bed-303">Standardvärdet är **InlineView**.</span><span class="sxs-lookup"><span data-stu-id="81bed-303">The default is **InlineView**.</span></span>

- <span data-ttu-id="81bed-304">**InlineView** – formatet som befintliga idag, på samma sätt som i fiskeri-och zsh.</span><span class="sxs-lookup"><span data-stu-id="81bed-304">**InlineView** - the style as existing today, similar as in fish shell and zsh.</span></span> <span data-ttu-id="81bed-305">(standard)</span><span class="sxs-lookup"><span data-stu-id="81bed-305">(default)</span></span>
- <span data-ttu-id="81bed-306">**ListView** – förslag återges i en nedrullningsbar listruta och användare kan välja att använda <kbd>uppilen</kbd> och <kbd>NEDPIL</kbd>.</span><span class="sxs-lookup"><span data-stu-id="81bed-306">**ListView** - suggestions are rendered in a drop down list, and users can select using <kbd>UpArrow</kbd> and <kbd>DownArrow</kbd>.</span></span>

<span data-ttu-id="81bed-307">Den här parametern har lagts till i PSReadLine 2.2.0</span><span class="sxs-lookup"><span data-stu-id="81bed-307">This parameter was added in PSReadLine 2.2.0</span></span>

```yaml
Type: Microsoft.PowerShell.PredictionViewStyle
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: InlineView
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="81bed-308">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="81bed-308">CommonParameters</span></span>

<span data-ttu-id="81bed-309">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="81bed-309">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="81bed-310">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="81bed-310">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="81bed-311">Indata</span><span class="sxs-lookup"><span data-stu-id="81bed-311">Inputs</span></span>

### <span data-ttu-id="81bed-312">Inga</span><span class="sxs-lookup"><span data-stu-id="81bed-312">None</span></span>

<span data-ttu-id="81bed-313">Du kan inte skicka pipe-objekt till `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="81bed-313">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="81bed-314">Outputs (Utdata)</span><span class="sxs-lookup"><span data-stu-id="81bed-314">Outputs</span></span>

### <span data-ttu-id="81bed-315">Inga</span><span class="sxs-lookup"><span data-stu-id="81bed-315">None</span></span>

<span data-ttu-id="81bed-316">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="81bed-316">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="81bed-317">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="81bed-317">Notes</span></span>

## <span data-ttu-id="81bed-318">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="81bed-318">Related links</span></span>

[<span data-ttu-id="81bed-319">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="81bed-319">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="81bed-320">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-320">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="81bed-321">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="81bed-321">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="81bed-322">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-322">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="81bed-323">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="81bed-323">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
