---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadline
ms.date: 06/30/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlineoption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineOption
ms.openlocfilehash: 15295ffaac320d24a3c9c24c0419118ef2644f90
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273195"
---
# <span data-ttu-id="96e63-103">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="96e63-103">Set-PSReadLineOption</span></span>

## <span data-ttu-id="96e63-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="96e63-104">Synopsis</span></span>
<span data-ttu-id="96e63-105">Anpassar beteendet för kommando rads redigering i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="96e63-105">Customizes the behavior of command line editing in **PSReadLine**.</span></span>

## <span data-ttu-id="96e63-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="96e63-106">Syntax</span></span>

```
Set-PSReadLineOption [-EditMode <EditMode>] [-ContinuationPrompt <String>] [-HistoryNoDuplicates]
 [-AddToHistoryHandler <System.Func[System.String,System.Object]>]
 [-CommandValidationHandler <System.Action[System.Management.Automation.Language.CommandAst]>]
 [-HistorySearchCursorMovesToEnd] [-MaximumHistoryCount <Int32>] [-MaximumKillRingCount <Int32>]
 [-ShowToolTips] [-ExtraPromptLineCount <Int32>] [-DingTone <Int32>] [-DingDuration <Int32>]
 [-BellStyle <BellStyle>] [-CompletionQueryItems <Int32>] [-WordDelimiters <String>]
 [-HistorySearchCaseSensitive] [-HistorySaveStyle <HistorySaveStyle>] [-HistorySavePath <String>]
 [-AnsiEscapeTimeout <Int32>] [-PromptText <String[]>] [-ViModeIndicator <ViModeStyle>]
 [-ViModeChangeHandler <ScriptBlock>] [-Colors <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="96e63-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96e63-107">Description</span></span>

<span data-ttu-id="96e63-108">`Set-PSReadLineOption`Cmdleten anpassar beteendet för **PSReadLine** -modulen när du redigerar kommando raden.</span><span class="sxs-lookup"><span data-stu-id="96e63-108">The `Set-PSReadLineOption` cmdlet customizes the behavior of the **PSReadLine** module when you're editing the command line.</span></span> <span data-ttu-id="96e63-109">Använd om du vill visa **PSReadLine** -inställningarna `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="96e63-109">To view the **PSReadLine** settings, use `Get-PSReadLineOption`.</span></span>

## <span data-ttu-id="96e63-110">Exempel</span><span class="sxs-lookup"><span data-stu-id="96e63-110">Examples</span></span>

### <span data-ttu-id="96e63-111">Exempel 1: Ange förgrunds-och bakgrunds färger</span><span class="sxs-lookup"><span data-stu-id="96e63-111">Example 1: Set foreground and background colors</span></span>

<span data-ttu-id="96e63-112">I det här exemplet anges **PSReadLine** för att visa **kommentars** -token med grön förgrunds text på en grå bakgrund.</span><span class="sxs-lookup"><span data-stu-id="96e63-112">This example sets **PSReadLine** to display the **Comment** token with green foreground text on a gray background.</span></span> <span data-ttu-id="96e63-113">I Escape-sekvensen som används i exemplet representerar **32** förgrunds färgen och **47** representerar bakgrunds färgen.</span><span class="sxs-lookup"><span data-stu-id="96e63-113">In the escape sequence used in the example, **32** represents the foreground color and **47** represents the background color.</span></span>

```powershell
Set-PSReadLineOption -Colors @{ "Comment"="$([char]0x1b)[32;47m" }
```

<span data-ttu-id="96e63-114">Du kan välja att bara ange en förgrunds text färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-114">You can choose to set only a foreground text color.</span></span> <span data-ttu-id="96e63-115">Till exempel en ljus grön förgrunds text färg för **kommentarens** token: `"Comment"="$([char]0x1b)[92m"` .</span><span class="sxs-lookup"><span data-stu-id="96e63-115">For example, a bright green foreground text color for the **Comment** token: `"Comment"="$([char]0x1b)[92m"`.</span></span>

### <span data-ttu-id="96e63-116">Exempel 2: Ange klock format</span><span class="sxs-lookup"><span data-stu-id="96e63-116">Example 2: Set bell style</span></span>

<span data-ttu-id="96e63-117">I det här exemplet kommer **PSReadLine** att svara på fel eller villkor som kräver åtgärder från användaren.</span><span class="sxs-lookup"><span data-stu-id="96e63-117">In this example, **PSReadLine** will respond to errors or conditions that require user attention.</span></span>
<span data-ttu-id="96e63-118">**BellStyle** har ställts in för att avge en ljud signal vid 1221 Hz för 60 MS.</span><span class="sxs-lookup"><span data-stu-id="96e63-118">The **BellStyle** is set to emit an audible beep at 1221 Hz for 60 ms.</span></span>

```powershell
Set-PSReadLineOption -BellStyle Audible -DingTone 1221 -DingDuration 60
```

> [!NOTE]
> <span data-ttu-id="96e63-119">Den här funktionen kanske inte fungerar på alla värdar på plattformar.</span><span class="sxs-lookup"><span data-stu-id="96e63-119">This feature may not work in all hosts on platforms.</span></span>

### <span data-ttu-id="96e63-120">Exempel 3: ange flera alternativ</span><span class="sxs-lookup"><span data-stu-id="96e63-120">Example 3: Set multiple options</span></span>

<span data-ttu-id="96e63-121">`Set-PSReadLineOption` kan ange flera alternativ med en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="96e63-121">`Set-PSReadLineOption` can set multiple options with a hash table.</span></span>

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

<span data-ttu-id="96e63-122">`$PSReadLineOptions`Hash-tabellen anger nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="96e63-122">The `$PSReadLineOptions` hash table sets the keys and values.</span></span> <span data-ttu-id="96e63-123">`Set-PSReadLineOption` använder nycklar och värden med `@PSReadLineOptions` för att uppdatera **PSReadLine** -alternativen.</span><span class="sxs-lookup"><span data-stu-id="96e63-123">`Set-PSReadLineOption` uses the keys and values with `@PSReadLineOptions` to update the **PSReadLine** options.</span></span>

<span data-ttu-id="96e63-124">Du kan visa nycklar och värden som anger namnet på hash-tabellen `$PSReadLineOptions` på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="96e63-124">You can view the keys and values entering the hash table name, `$PSReadLineOptions` on the PowerShell command line.</span></span>

### <span data-ttu-id="96e63-125">Exempel 4: ange flera färg alternativ</span><span class="sxs-lookup"><span data-stu-id="96e63-125">Example 4: Set multiple color options</span></span>

<span data-ttu-id="96e63-126">Det här exemplet visar hur du ställer in fler än ett färg värde i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="96e63-126">This example shows how to set more than one color value in a single command.</span></span>

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

### <span data-ttu-id="96e63-127">Exempel 5: Ange färg värden för flera typer</span><span class="sxs-lookup"><span data-stu-id="96e63-127">Example 5: Set color values for multiple types</span></span>

<span data-ttu-id="96e63-128">Det här exemplet visar tre olika metoder för hur du ställer in färgen på tokens som visas i **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="96e63-128">This example shows three different methods for how to set the color of tokens displayed in **PSReadLine**.</span></span>

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

### <span data-ttu-id="96e63-129">Exempel 6: Använd ViModeChangeHandler för att Visa läges ändringar i vi</span><span class="sxs-lookup"><span data-stu-id="96e63-129">Example 6: Use ViModeChangeHandler to display Vi mode changes</span></span>

<span data-ttu-id="96e63-130">Det här exemplet ger en markör ändring VT Escape som svar på en ändring i ändrings läget i **vi** .</span><span class="sxs-lookup"><span data-stu-id="96e63-130">This example emits a cursor change VT escape in response to a **Vi** mode change.</span></span>

```powershell
function OnViModeChange {
    if ($args[0] -eq 'Command') {
        # Set the cursor to a blinking block.
        Write-Host -NoNewLine "$([char]0x1b)[1 q"
    } else {
        # Set the cursor to a blinking line.
        Write-Host -NoNewLine "$([char]0x1b)[5 q"
    }
}
Set-PSReadLineOption -ViModeIndicator Script -ViModeChangeHandler $Function:OnViModeChange
```

<span data-ttu-id="96e63-131">Funktionen **OnViModeChange** anger markör alternativen **för lägen för** lägen: INSERT och Command.</span><span class="sxs-lookup"><span data-stu-id="96e63-131">The **OnViModeChange** function sets the cursor options for the **Vi** modes: insert and command.</span></span>
<span data-ttu-id="96e63-132">**ViModeChangeHandler** använder `Function:` providern för att referera till **OnViModeChange** som ett skript Blocks objekt.</span><span class="sxs-lookup"><span data-stu-id="96e63-132">**ViModeChangeHandler** uses the `Function:` provider to reference **OnViModeChange** as a script block object.</span></span>

<span data-ttu-id="96e63-133">Mer information finns i [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span><span class="sxs-lookup"><span data-stu-id="96e63-133">For more information, see [about_Providers](/powershell/module/microsoft.powershell.core/about/about_providers).</span></span>

## <span data-ttu-id="96e63-134">Parametrar</span><span class="sxs-lookup"><span data-stu-id="96e63-134">Parameters</span></span>

### <span data-ttu-id="96e63-135">-AddToHistoryHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-135">-AddToHistoryHandler</span></span>

<span data-ttu-id="96e63-136">Anger en **script block** som styr vilka kommandon som läggs till i **PSReadLine** -historiken.</span><span class="sxs-lookup"><span data-stu-id="96e63-136">Specifies a **ScriptBlock** that controls which commands get added to **PSReadLine** history.</span></span>

<span data-ttu-id="96e63-137">**Script block** tar emot kommando raden som inmatad.</span><span class="sxs-lookup"><span data-stu-id="96e63-137">The **ScriptBlock** receives the command line as input.</span></span> <span data-ttu-id="96e63-138">Om **script block** returnerar `$True` läggs kommando raden till i historiken.</span><span class="sxs-lookup"><span data-stu-id="96e63-138">If the **ScriptBlock** returns `$True`, the command line is added to the history.</span></span>

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

### <span data-ttu-id="96e63-139">-AnsiEscapeTimeout</span><span class="sxs-lookup"><span data-stu-id="96e63-139">-AnsiEscapeTimeout</span></span>

<span data-ttu-id="96e63-140">Det här alternativet är endast för Windows när indatatypen omdirigeras, till exempel när du kör under `tmux` eller `screen` .</span><span class="sxs-lookup"><span data-stu-id="96e63-140">This option is specific to Windows when input is redirected, for example, when running under `tmux` or `screen`.</span></span>

<span data-ttu-id="96e63-141">Vid Omdirigerad inaktivitet i Windows skickas många nycklar som en sekvens med tecken som börjar med Escape-tecknet.</span><span class="sxs-lookup"><span data-stu-id="96e63-141">With redirected input on Windows, many keys are sent as a sequence of characters starting with the escape character.</span></span> <span data-ttu-id="96e63-142">Det är omöjligt att skilja mellan ett enda escape-tecken följt av fler tecken och en giltig escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="96e63-142">It's impossible to distinguish between a single escape character followed by more characters and a valid escape sequence.</span></span>

<span data-ttu-id="96e63-143">Antagandet är att terminalen kan skicka tecknen snabbare än en användar typ.</span><span class="sxs-lookup"><span data-stu-id="96e63-143">The assumption is that the terminal can send the characters faster than a user types.</span></span> <span data-ttu-id="96e63-144">**PSReadLine** väntar för denna timeout innan den tar emot en komplett escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="96e63-144">**PSReadLine** waits for this timeout before concluding that it has received a complete escape sequence.</span></span>

<span data-ttu-id="96e63-145">Om du ser slumpmässiga eller oväntade tecken när du skriver kan du justera denna tids gräns.</span><span class="sxs-lookup"><span data-stu-id="96e63-145">If you see random or unexpected characters when you type, you can adjust this timeout.</span></span>

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

### <span data-ttu-id="96e63-146">-BellStyle</span><span class="sxs-lookup"><span data-stu-id="96e63-146">-BellStyle</span></span>

<span data-ttu-id="96e63-147">Anger hur **PSReadLine** reagerar på olika fel och tvetydiga villkor.</span><span class="sxs-lookup"><span data-stu-id="96e63-147">Specifies how **PSReadLine** responds to various error and ambiguous conditions.</span></span>

<span data-ttu-id="96e63-148">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="96e63-148">The valid values are as follows:</span></span>

- <span data-ttu-id="96e63-149">**Hörbar** : en kort signal.</span><span class="sxs-lookup"><span data-stu-id="96e63-149">**Audible** : A short beep.</span></span>
- <span data-ttu-id="96e63-150">**Visuellt** : text blinkar en kort stund.</span><span class="sxs-lookup"><span data-stu-id="96e63-150">**Visual** : Text flashes briefly.</span></span>
- <span data-ttu-id="96e63-151">**Ingen** : ingen feedback.</span><span class="sxs-lookup"><span data-stu-id="96e63-151">**None** : No feedback.</span></span>

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

### <span data-ttu-id="96e63-152">– Färger</span><span class="sxs-lookup"><span data-stu-id="96e63-152">-Colors</span></span>

<span data-ttu-id="96e63-153">Parametern **Colors** anger olika färger som används av **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="96e63-153">The **Colors** parameter specifies various colors used by **PSReadLine**.</span></span>

<span data-ttu-id="96e63-154">Argumentet är en hash-tabell där nycklarna anger vilka element och värden som anger färgen.</span><span class="sxs-lookup"><span data-stu-id="96e63-154">The argument is a hash table where the keys specify which element and the values specify the color.</span></span>
<span data-ttu-id="96e63-155">Mer information finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="96e63-155">For more information, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="96e63-156">Färger kan vara antingen ett värde från **ConsoleColor** , till exempel `[ConsoleColor]::Red` eller en giltig ANSI-escape-sekvens.</span><span class="sxs-lookup"><span data-stu-id="96e63-156">Colors can be either a value from **ConsoleColor** , for example `[ConsoleColor]::Red`, or a valid ANSI escape sequence.</span></span> <span data-ttu-id="96e63-157">Giltiga escape-sekvenser beror på terminalen.</span><span class="sxs-lookup"><span data-stu-id="96e63-157">Valid escape sequences depend on your terminal.</span></span> <span data-ttu-id="96e63-158">I PowerShell 5,0 är ett exempel på en escape-sekvens för röd text `$([char]0x1b)[91m` .</span><span class="sxs-lookup"><span data-stu-id="96e63-158">In PowerShell 5.0, an example escape sequence for red text is `$([char]0x1b)[91m`.</span></span> <span data-ttu-id="96e63-159">I PowerShell 6 och senare är samma escape-sekvens `` `e[91m`` .</span><span class="sxs-lookup"><span data-stu-id="96e63-159">In PowerShell 6 and above, the same escape sequence is `` `e[91m``.</span></span> <span data-ttu-id="96e63-160">Du kan ange andra escape-sekvenser, inklusive följande typer:</span><span class="sxs-lookup"><span data-stu-id="96e63-160">You can specify other escape sequences including the following types:</span></span>

- <span data-ttu-id="96e63-161">256-färg</span><span class="sxs-lookup"><span data-stu-id="96e63-161">256 color</span></span>
- <span data-ttu-id="96e63-162">24-bitars färg</span><span class="sxs-lookup"><span data-stu-id="96e63-162">24-bit color</span></span>
- <span data-ttu-id="96e63-163">Förgrund, bakgrund eller både och</span><span class="sxs-lookup"><span data-stu-id="96e63-163">Foreground, background, or both</span></span>
- <span data-ttu-id="96e63-164">Invertera, fet</span><span class="sxs-lookup"><span data-stu-id="96e63-164">Inverse, bold</span></span>

<span data-ttu-id="96e63-165">Mer information om ANSI Color-koder finns i [ANSI Escape Code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in wikipedia.</span><span class="sxs-lookup"><span data-stu-id="96e63-165">For more information about ANSI color codes, see [ANSI escape code](https://wikipedia.org/wiki/ANSI_escape_code#Colors_) in Wikipedia.</span></span>

<span data-ttu-id="96e63-166">Giltiga nycklar är:</span><span class="sxs-lookup"><span data-stu-id="96e63-166">The valid keys include:</span></span>

- <span data-ttu-id="96e63-167">**ContinuationPrompt** : färgen på fortsättnings frågan.</span><span class="sxs-lookup"><span data-stu-id="96e63-167">**ContinuationPrompt** : The color of the continuation prompt.</span></span>
- <span data-ttu-id="96e63-168">**Betoning** : betonings färgen.</span><span class="sxs-lookup"><span data-stu-id="96e63-168">**Emphasis** : The emphasis color.</span></span> <span data-ttu-id="96e63-169">Till exempel den matchande texten vid sökning efter historik.</span><span class="sxs-lookup"><span data-stu-id="96e63-169">For example, the matching text when searching history.</span></span>
- <span data-ttu-id="96e63-170">**Fel** : fel färgen.</span><span class="sxs-lookup"><span data-stu-id="96e63-170">**Error** : The error color.</span></span> <span data-ttu-id="96e63-171">Till exempel i prompten.</span><span class="sxs-lookup"><span data-stu-id="96e63-171">For example, in the prompt.</span></span>
- <span data-ttu-id="96e63-172">**Markering** : färgen för att markera meny markeringen eller den markerade texten.</span><span class="sxs-lookup"><span data-stu-id="96e63-172">**Selection** : The color to highlight the menu selection or selected text.</span></span>
- <span data-ttu-id="96e63-173">**Standard** : standardvärdet för token.</span><span class="sxs-lookup"><span data-stu-id="96e63-173">**Default** : The default token color.</span></span>
- <span data-ttu-id="96e63-174">**Comment** : kommentarens token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-174">**Comment** : The comment token color.</span></span>
- <span data-ttu-id="96e63-175">**Nyckelord** : token för nyckelord.</span><span class="sxs-lookup"><span data-stu-id="96e63-175">**Keyword** : The keyword token color.</span></span>
- <span data-ttu-id="96e63-176">**Sträng** : strängens token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-176">**String** : The string token color.</span></span>
- <span data-ttu-id="96e63-177">**Operator** : operatorns token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-177">**Operator** : The operator token color.</span></span>
- <span data-ttu-id="96e63-178">**Variabel** : variabelns token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-178">**Variable** : The variable token color.</span></span>
- <span data-ttu-id="96e63-179">**Kommando** : kommando-token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-179">**Command** : The command token color.</span></span>
- <span data-ttu-id="96e63-180">**Parameter** : parameterns token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-180">**Parameter** : The parameter token color.</span></span>
- <span data-ttu-id="96e63-181">**Skriv** : typens token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-181">**Type** : The type token color.</span></span>
- <span data-ttu-id="96e63-182">**Number** : standardvärdet för token.</span><span class="sxs-lookup"><span data-stu-id="96e63-182">**Number** : The number token color.</span></span>
- <span data-ttu-id="96e63-183">**Medlem** : medlems namnets token-färg.</span><span class="sxs-lookup"><span data-stu-id="96e63-183">**Member** : The member name token color.</span></span>

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

### <span data-ttu-id="96e63-184">-CommandValidationHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-184">-CommandValidationHandler</span></span>

<span data-ttu-id="96e63-185">Anger en **script block** som anropas från **ValidateAndAcceptLine**.</span><span class="sxs-lookup"><span data-stu-id="96e63-185">Specifies a **ScriptBlock** that is called from **ValidateAndAcceptLine**.</span></span> <span data-ttu-id="96e63-186">Om ett undantag genereras Miss lyckas valideringen och felet rapporteras.</span><span class="sxs-lookup"><span data-stu-id="96e63-186">If an exception is thrown, validation fails and the error is reported.</span></span>

<span data-ttu-id="96e63-187">Innan ett undantag utlöses kan validerings hanteraren placera markören vid fel punkten så att den blir lättare att åtgärda.</span><span class="sxs-lookup"><span data-stu-id="96e63-187">Before throwing an exception, the validation handler can place the cursor at the point of the error to make it easier to fix.</span></span> <span data-ttu-id="96e63-188">En verifierings hanterare kan också ändra kommando raden, till exempel för att korrigera vanliga typografiska fel.</span><span class="sxs-lookup"><span data-stu-id="96e63-188">A validation handler can also change the command line, such as to correct common typographical errors.</span></span>

<span data-ttu-id="96e63-189">**ValidateAndAcceptLine** används för att undvika att historiken rensas med kommandon som inte fungerar.</span><span class="sxs-lookup"><span data-stu-id="96e63-189">**ValidateAndAcceptLine** is used to avoid cluttering your history with commands that can't work.</span></span>

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

### <span data-ttu-id="96e63-190">-CompletionQueryItems</span><span class="sxs-lookup"><span data-stu-id="96e63-190">-CompletionQueryItems</span></span>

<span data-ttu-id="96e63-191">Anger det maximala antalet slutförda objekt som visas utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="96e63-191">Specifies the maximum number of completion items that are shown without prompting.</span></span>

<span data-ttu-id="96e63-192">Om antalet objekt som ska visas är större än det här värdet visas **PSReadLine** **Ja/Nej** innan slut för ande objekt visas.</span><span class="sxs-lookup"><span data-stu-id="96e63-192">If the number of items to show is greater than this value, **PSReadLine** prompts **yes/no** before displaying the completion items.</span></span>

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

### <span data-ttu-id="96e63-193">-ContinuationPrompt</span><span class="sxs-lookup"><span data-stu-id="96e63-193">-ContinuationPrompt</span></span>

<span data-ttu-id="96e63-194">Anger den sträng som visas i början av efterföljande rader när flera rader skrivs in.</span><span class="sxs-lookup"><span data-stu-id="96e63-194">Specifies the string displayed at the beginning of the subsequent lines when multi-line input is entered.</span></span> <span data-ttu-id="96e63-195">Standardvärdet är Double större än-tecken ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="96e63-195">The default is double greater-than signs (`>>`).</span></span> <span data-ttu-id="96e63-196">En tom sträng är giltig.</span><span class="sxs-lookup"><span data-stu-id="96e63-196">An empty string is valid.</span></span>

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

### <span data-ttu-id="96e63-197">-DingDuration</span><span class="sxs-lookup"><span data-stu-id="96e63-197">-DingDuration</span></span>

<span data-ttu-id="96e63-198">Anger längden på pip när **BellStyle** är inställd på **hörbar**.</span><span class="sxs-lookup"><span data-stu-id="96e63-198">Specifies the duration of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="96e63-199">-DingTone</span><span class="sxs-lookup"><span data-stu-id="96e63-199">-DingTone</span></span>

<span data-ttu-id="96e63-200">Anger tonen i Hertz (Hz) för pip när **BellStyle** är inställt på **hörbar**.</span><span class="sxs-lookup"><span data-stu-id="96e63-200">Specifies the tone in Hertz (Hz) of the beep when **BellStyle** is set to **Audible**.</span></span>

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

### <span data-ttu-id="96e63-201">– EditMode</span><span class="sxs-lookup"><span data-stu-id="96e63-201">-EditMode</span></span>

<span data-ttu-id="96e63-202">Anger kommando rads redigerings läge.</span><span class="sxs-lookup"><span data-stu-id="96e63-202">Specifies the command line editing mode.</span></span> <span data-ttu-id="96e63-203">Om du använder den här parametern återställs alla nyckel bindningar som anges av `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="96e63-203">Using this parameter resets any key bindings set by `Set-PSReadLineKeyHandler`.</span></span>

<span data-ttu-id="96e63-204">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="96e63-204">The valid values are as follows:</span></span>

- <span data-ttu-id="96e63-205">**Windows** : nyckel bindningar emulerar PowerShell, cmd och Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="96e63-205">**Windows** : Key bindings emulate PowerShell, cmd, and Visual Studio.</span></span>
- <span data-ttu-id="96e63-206">**Emacs** : nyckel bindningar emulerar bash eller emacs.</span><span class="sxs-lookup"><span data-stu-id="96e63-206">**Emacs** : Key bindings emulate Bash or Emacs.</span></span>
- <span data-ttu-id="96e63-207">**Vi** : nyckel bindningar emulerar vi.</span><span class="sxs-lookup"><span data-stu-id="96e63-207">**Vi** : Key bindings emulate Vi.</span></span>

<span data-ttu-id="96e63-208">Används `Get-PSReadLineKeyHandler` för att se nyckel bindningarna för den aktuella konfigurerade **EditMode**.</span><span class="sxs-lookup"><span data-stu-id="96e63-208">Use `Get-PSReadLineKeyHandler` to see the key bindings for the currently configured **EditMode**.</span></span>

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

### <span data-ttu-id="96e63-209">-ExtraPromptLineCount</span><span class="sxs-lookup"><span data-stu-id="96e63-209">-ExtraPromptLineCount</span></span>

<span data-ttu-id="96e63-210">Anger antalet extra rader.</span><span class="sxs-lookup"><span data-stu-id="96e63-210">Specifies the number of extra lines.</span></span>

<span data-ttu-id="96e63-211">Om din prompt omfattar fler än en rad anger du ett värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="96e63-211">If your prompt spans more than one line, specify a value for this parameter.</span></span> <span data-ttu-id="96e63-212">Använd det här alternativet om du vill att extra rader ska vara tillgängliga när **PSReadLine** visar frågan när du har visat några utdata.</span><span class="sxs-lookup"><span data-stu-id="96e63-212">Use this option when you want extra lines to be available when **PSReadLine** displays the prompt after showing some output.</span></span> <span data-ttu-id="96e63-213">**PSReadLine** returnerar till exempel en lista över slut för ande.</span><span class="sxs-lookup"><span data-stu-id="96e63-213">For example, **PSReadLine** returns a list of completions.</span></span>

<span data-ttu-id="96e63-214">Det här alternativet krävs mindre än i tidigare versioner av **PSReadLine** , men är användbart när `InvokePrompt` funktionen används.</span><span class="sxs-lookup"><span data-stu-id="96e63-214">This option is needed less than in previous versions of **PSReadLine** , but is useful when the `InvokePrompt` function is used.</span></span>

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

### <span data-ttu-id="96e63-215">-HistoryNoDuplicates</span><span class="sxs-lookup"><span data-stu-id="96e63-215">-HistoryNoDuplicates</span></span>

<span data-ttu-id="96e63-216">Det här alternativet styr återställnings beteendet.</span><span class="sxs-lookup"><span data-stu-id="96e63-216">This option controls the recall behavior.</span></span> <span data-ttu-id="96e63-217">Dubbla kommandon läggs fortfarande till i historik filen.</span><span class="sxs-lookup"><span data-stu-id="96e63-217">Duplicate commands are still added to the history file.</span></span>
<span data-ttu-id="96e63-218">När det här alternativet är inställt visas bara det senaste anropet när du anropar kommandon.</span><span class="sxs-lookup"><span data-stu-id="96e63-218">When this option is set, only the most recent invocation appears when recalling commands.</span></span> <span data-ttu-id="96e63-219">Upprepade kommandon läggs till i historiken för att bevara ordning under återkallning.</span><span class="sxs-lookup"><span data-stu-id="96e63-219">Repeated commands are added to history to preserve ordering during recall.</span></span> <span data-ttu-id="96e63-220">Du vill dock vanligt vis inte se kommandot flera gånger vid återanrop eller sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="96e63-220">However, you typically don't want to see the command multiple times when recalling or searching the history.</span></span>

<span data-ttu-id="96e63-221">Som standard är egenskapen **HistoryNoDuplicates** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-221">By default, the **HistoryNoDuplicates** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="96e63-222">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-222">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="96e63-223">Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistoryNoDuplicates:$False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-223">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-HistoryNoDuplicates:$False`.</span></span>

<span data-ttu-id="96e63-224">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="96e63-224">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="96e63-225">-HistorySavePath</span><span class="sxs-lookup"><span data-stu-id="96e63-225">-HistorySavePath</span></span>

<span data-ttu-id="96e63-226">Anger sökvägen till filen där historiken sparas.</span><span class="sxs-lookup"><span data-stu-id="96e63-226">Specifies the path to the file where history is saved.</span></span> <span data-ttu-id="96e63-227">Datorer som kör Windows-eller icke-Windows-plattformar lagrar filen på olika platser.</span><span class="sxs-lookup"><span data-stu-id="96e63-227">Computers running Windows or non-Windows platforms store the file in different locations.</span></span> <span data-ttu-id="96e63-228">Fil namnet lagras i en variabel `$($host.Name)_history.txt` , till exempel `ConsoleHost_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="96e63-228">The filename is stored in a variable `$($host.Name)_history.txt`, for example `ConsoleHost_history.txt`.</span></span>

<span data-ttu-id="96e63-229">Om du inte använder den här parametern är standard Sök vägen följande:</span><span class="sxs-lookup"><span data-stu-id="96e63-229">If you don't use this parameter, the default path is as follows:</span></span>

<span data-ttu-id="96e63-230">**Windows**</span><span class="sxs-lookup"><span data-stu-id="96e63-230">**Windows**</span></span>

`$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine\$($host.Name)_history.txt`

<span data-ttu-id="96e63-231">**icke-Windows**</span><span class="sxs-lookup"><span data-stu-id="96e63-231">**non-Windows**</span></span>

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

### <span data-ttu-id="96e63-232">-HistorySaveStyle</span><span class="sxs-lookup"><span data-stu-id="96e63-232">-HistorySaveStyle</span></span>

<span data-ttu-id="96e63-233">Anger hur **PSReadLine** sparas i historiken.</span><span class="sxs-lookup"><span data-stu-id="96e63-233">Specifies how **PSReadLine** saves history.</span></span>

<span data-ttu-id="96e63-234">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="96e63-234">Valid values are as follows:</span></span>

- <span data-ttu-id="96e63-235">**SaveIncrementally** : spara historik när varje kommando körs och delas över flera instanser av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e63-235">**SaveIncrementally** : Save history after each command is executed and share across multiple instances of PowerShell.</span></span>
- <span data-ttu-id="96e63-236">**SaveAtExit** : Lägg till historik fil när PowerShell avslutas.</span><span class="sxs-lookup"><span data-stu-id="96e63-236">**SaveAtExit** : Append history file when PowerShell exits.</span></span>
- <span data-ttu-id="96e63-237">**SaveNothing** : Använd inte en historik fil.</span><span class="sxs-lookup"><span data-stu-id="96e63-237">**SaveNothing** : Don't use a history file.</span></span>

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

### <span data-ttu-id="96e63-238">-HistorySearchCaseSensitive</span><span class="sxs-lookup"><span data-stu-id="96e63-238">-HistorySearchCaseSensitive</span></span>

<span data-ttu-id="96e63-239">Anger att historik sökning är Skift läges känsligt i funktioner som **ReverseSearchHistory** eller **HistorySearchBackward**.</span><span class="sxs-lookup"><span data-stu-id="96e63-239">Specifies that history searching is case-sensitive in functions like **ReverseSearchHistory** or **HistorySearchBackward**.</span></span>

<span data-ttu-id="96e63-240">Som standard är egenskapen **HistorySearchCaseSensitive** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-240">By default, the **HistorySearchCaseSensitive** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="96e63-241">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-241">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="96e63-242">Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCaseSensitive:$False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-242">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCaseSensitive:$False`.</span></span>

<span data-ttu-id="96e63-243">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="96e63-243">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="96e63-244">-HistorySearchCursorMovesToEnd</span><span class="sxs-lookup"><span data-stu-id="96e63-244">-HistorySearchCursorMovesToEnd</span></span>

<span data-ttu-id="96e63-245">Anger att markören flyttas till slutet av de kommandon som du läser in från historiken med hjälp av en sökning.</span><span class="sxs-lookup"><span data-stu-id="96e63-245">Indicates that the cursor moves to the end of commands that you load from history by using a search.</span></span>
<span data-ttu-id="96e63-246">När den här parametern är inställd på `$False` stannar markören kvar på den plats där du tryckte på uppåt-eller nedpilarna.</span><span class="sxs-lookup"><span data-stu-id="96e63-246">When this parameter is set to `$False`, the cursor remains at the position it was when you pressed the up or down arrows.</span></span>

<span data-ttu-id="96e63-247">Som standard är egenskapen **HistorySearchCursorMovesToEnd** för det globala **PSConsoleReadLineOptions** -objektet inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-247">By default, the **HistorySearchCursorMovesToEnd** property of the global **PSConsoleReadLineOptions** object is set to `False`.</span></span> <span data-ttu-id="96e63-248">Med den här **SwitchParameter** anger du egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-248">Using this **SwitchParameter** set the property value to `True`.</span></span> <span data-ttu-id="96e63-249">Om du vill ändra tillbaka egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-HistorySearchCursorMovesToEnd:$False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-249">To change the property value back, you must specify the value of the **SwitchParameter** as follows: `-HistorySearchCursorMovesToEnd:$False`.</span></span>

<span data-ttu-id="96e63-250">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="96e63-250">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="96e63-251">-MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="96e63-251">-MaximumHistoryCount</span></span>

<span data-ttu-id="96e63-252">Anger det maximala antalet kommandon som ska sparas i **PSReadLine** historik.</span><span class="sxs-lookup"><span data-stu-id="96e63-252">Specifies the maximum number of commands to save in **PSReadLine** history.</span></span>

<span data-ttu-id="96e63-253">**PSReadLine** -historiken är separat från PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="96e63-253">**PSReadLine** history is separate from PowerShell history.</span></span>

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

### <span data-ttu-id="96e63-254">-MaximumKillRingCount</span><span class="sxs-lookup"><span data-stu-id="96e63-254">-MaximumKillRingCount</span></span>

<span data-ttu-id="96e63-255">Anger det maximala antalet objekt som lagras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="96e63-255">Specifies the maximum number of items stored in the kill ring.</span></span>

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

### <span data-ttu-id="96e63-256">-PromptText</span><span class="sxs-lookup"><span data-stu-id="96e63-256">-PromptText</span></span>

<span data-ttu-id="96e63-257">När ett parsningsfel uppstår ändrar **PSReadLine** en del av meddelandet Red.</span><span class="sxs-lookup"><span data-stu-id="96e63-257">When there's a parse error, **PSReadLine** changes a part of the prompt red.</span></span> <span data-ttu-id="96e63-258">**PSReadLine** analyserar funktionen prompt för att bestämma hur du bara vill ändra färgen på en del av din prompt.</span><span class="sxs-lookup"><span data-stu-id="96e63-258">**PSReadLine** analyzes your prompt function to determine how to change only the color of part of your prompt.</span></span> <span data-ttu-id="96e63-259">Den här analysen är inte 100% tillförlitlig.</span><span class="sxs-lookup"><span data-stu-id="96e63-259">This analysis isn't 100% reliable.</span></span>

<span data-ttu-id="96e63-260">Använd det här alternativet om **PSReadLine** ändrar din prompt på oväntade sätt.</span><span class="sxs-lookup"><span data-stu-id="96e63-260">Use this option if **PSReadLine** is changing your prompt in unexpected ways.</span></span> <span data-ttu-id="96e63-261">Ta med eventuella avslutande blank steg.</span><span class="sxs-lookup"><span data-stu-id="96e63-261">Include any trailing whitespace.</span></span>

<span data-ttu-id="96e63-262">Exempel: om din prompt-funktion såg ut som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="96e63-262">For example, if your prompt function looked like the following example:</span></span>

`function prompt { Write-Host -NoNewLine -ForegroundColor Yellow "$pwd"; return "# " }`

<span data-ttu-id="96e63-263">Ange sedan:</span><span class="sxs-lookup"><span data-stu-id="96e63-263">Then set:</span></span>

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

### <span data-ttu-id="96e63-264">-ShowToolTips</span><span class="sxs-lookup"><span data-stu-id="96e63-264">-ShowToolTips</span></span>

<span data-ttu-id="96e63-265">När du visar möjliga kompletteringar visas knapp beskrivningar i listan med slutförda.</span><span class="sxs-lookup"><span data-stu-id="96e63-265">When displaying possible completions, tooltips are shown in the list of completions.</span></span>

<span data-ttu-id="96e63-266">Det här alternativet är aktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="96e63-266">This option is enabled by default.</span></span> <span data-ttu-id="96e63-267">Det här alternativet är inte aktiverat som standard i tidigare versioner av **PSReadLine**.</span><span class="sxs-lookup"><span data-stu-id="96e63-267">This option wasn't enabled by default in prior versions of **PSReadLine**.</span></span> <span data-ttu-id="96e63-268">Om du vill inaktivera aktiverar du det här alternativet `$False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-268">To disable, set this option to `$False`.</span></span>

<span data-ttu-id="96e63-269">Som standard är egenskapen **ShowToolTips** för det globala **PSConsoleReadLineOptions** -objektet inställt på `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-269">By default, the **ShowToolTips** property of the global **PSConsoleReadLineOptions** object is set to `True`.</span></span> <span data-ttu-id="96e63-270">Om du använder den här **SwitchParameter** anges egenskap svärdet till `True` .</span><span class="sxs-lookup"><span data-stu-id="96e63-270">Using this **SwitchParameter** sets the property value to `True`.</span></span> <span data-ttu-id="96e63-271">Om du vill ändra egenskap svärdet måste du ange värdet för **SwitchParameter** enligt följande: `-ShowToolTips:$False` .</span><span class="sxs-lookup"><span data-stu-id="96e63-271">To change the property value, you must specify the value of the **SwitchParameter** as follows: `-ShowToolTips:$False`.</span></span>

<span data-ttu-id="96e63-272">Med hjälp av följande kommando kan du ange egenskap svärdet direkt:</span><span class="sxs-lookup"><span data-stu-id="96e63-272">Using the following command, you can set the property value directly:</span></span>

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

### <span data-ttu-id="96e63-273">-ViModeChangeHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-273">-ViModeChangeHandler</span></span>

<span data-ttu-id="96e63-274">När **ViModeIndicator** är inställt på `Script` , anropas det angivna skript blocket varje gång läget ändras.</span><span class="sxs-lookup"><span data-stu-id="96e63-274">When the **ViModeIndicator** is set to `Script`, the script block provided will be invoked every time the mode changes.</span></span> <span data-ttu-id="96e63-275">Skript blocket anges med ett argument av typen `ViMode` .</span><span class="sxs-lookup"><span data-stu-id="96e63-275">The script block is provided one argument of type `ViMode`.</span></span>

<span data-ttu-id="96e63-276">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="96e63-276">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="96e63-277">-ViModeIndicator</span><span class="sxs-lookup"><span data-stu-id="96e63-277">-ViModeIndicator</span></span>

<span data-ttu-id="96e63-278">Det här alternativet anger den visuella indikationen för det aktuella läget i **vi** .</span><span class="sxs-lookup"><span data-stu-id="96e63-278">This option sets the visual indication for the current **Vi** mode.</span></span> <span data-ttu-id="96e63-279">Antingen infognings läge eller kommando läge.</span><span class="sxs-lookup"><span data-stu-id="96e63-279">Either insert mode or command mode.</span></span>

<span data-ttu-id="96e63-280">Giltiga värden är följande:</span><span class="sxs-lookup"><span data-stu-id="96e63-280">The valid values are as follows:</span></span>

- <span data-ttu-id="96e63-281">**Ingen** : det finns ingen indikation.</span><span class="sxs-lookup"><span data-stu-id="96e63-281">**None** : There's no indication.</span></span>
- <span data-ttu-id="96e63-282">**Prompt** : färg ändrings färgen visas.</span><span class="sxs-lookup"><span data-stu-id="96e63-282">**Prompt** : The prompt changes color.</span></span>
- <span data-ttu-id="96e63-283">**Markör** : markören ändrar storlek.</span><span class="sxs-lookup"><span data-stu-id="96e63-283">**Cursor** : The cursor changes size.</span></span>
- <span data-ttu-id="96e63-284">**Skript** : Användardefinierad text skrivs ut.</span><span class="sxs-lookup"><span data-stu-id="96e63-284">**Script** : User-specified text is printed.</span></span>

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

### <span data-ttu-id="96e63-285">-WordDelimiters</span><span class="sxs-lookup"><span data-stu-id="96e63-285">-WordDelimiters</span></span>

<span data-ttu-id="96e63-286">Anger tecken som begränsar ord för funktioner som **ForwardWord** eller **KillWord**.</span><span class="sxs-lookup"><span data-stu-id="96e63-286">Specifies the characters that delimit words for functions like **ForwardWord** or **KillWord**.</span></span>

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

### <span data-ttu-id="96e63-287">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96e63-287">CommonParameters</span></span>

<span data-ttu-id="96e63-288">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96e63-288">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96e63-289">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="96e63-289">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96e63-290">Indata</span><span class="sxs-lookup"><span data-stu-id="96e63-290">Inputs</span></span>

### <span data-ttu-id="96e63-291">Inget</span><span class="sxs-lookup"><span data-stu-id="96e63-291">None</span></span>

<span data-ttu-id="96e63-292">Du kan inte skicka pipe-objekt till `Set-PSReadLineOption.`</span><span class="sxs-lookup"><span data-stu-id="96e63-292">You cannot pipe objects to `Set-PSReadLineOption.`</span></span>

## <span data-ttu-id="96e63-293">Utdata</span><span class="sxs-lookup"><span data-stu-id="96e63-293">Outputs</span></span>

### <span data-ttu-id="96e63-294">Inget</span><span class="sxs-lookup"><span data-stu-id="96e63-294">None</span></span>

<span data-ttu-id="96e63-295">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="96e63-295">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="96e63-296">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="96e63-296">Notes</span></span>

## <span data-ttu-id="96e63-297">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="96e63-297">Related links</span></span>

[<span data-ttu-id="96e63-298">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="96e63-298">about_PSReadLine</span></span>](./About/about_PSReadLine.md)

[<span data-ttu-id="96e63-299">Get-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-299">Get-PSReadLineKeyHandler</span></span>](Get-PSReadLineKeyHandler.md)

[<span data-ttu-id="96e63-300">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="96e63-300">Get-PSReadLineOption</span></span>](Get-PSReadLineOption.md)

[<span data-ttu-id="96e63-301">Remove-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-301">Remove-PSReadLineKeyHandler</span></span>](Remove-PSReadLineKeyHandler.md)

[<span data-ttu-id="96e63-302">Set-PSReadLineKeyHandler</span><span class="sxs-lookup"><span data-stu-id="96e63-302">Set-PSReadLineKeyHandler</span></span>](Set-PSReadLineKeyHandler.md)
