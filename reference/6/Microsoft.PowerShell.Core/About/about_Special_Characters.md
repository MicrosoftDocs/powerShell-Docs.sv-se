---
description: Beskriver de teckenkombinationer som styr hur PowerShell tolkar nästa tecken i sekvensen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_special_characters?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Special_Characters
ms.openlocfilehash: d9e09aa2800538beb363ccbcf2a193c727200869
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270386"
---
# <a name="about-special-characters"></a><span data-ttu-id="304b4-104">Om specialtecken</span><span class="sxs-lookup"><span data-stu-id="304b4-104">About Special Characters</span></span>

## <a name="short-description"></a><span data-ttu-id="304b4-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="304b4-105">Short description</span></span>

<span data-ttu-id="304b4-106">Beskriver de teckenkombinationer som styr hur PowerShell tolkar nästa tecken i sekvensen.</span><span class="sxs-lookup"><span data-stu-id="304b4-106">Describes the special character sequences that control how PowerShell interprets the next characters in the sequence.</span></span>

## <a name="long-description"></a><span data-ttu-id="304b4-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="304b4-107">Long description</span></span>

<span data-ttu-id="304b4-108">PowerShell stöder en uppsättning specialtecken som används för att representera tecken som inte ingår i standard teckenuppsättningen.</span><span class="sxs-lookup"><span data-stu-id="304b4-108">PowerShell supports a set of special character sequences that are used to represent characters that aren't part of the standard character set.</span></span> <span data-ttu-id="304b4-109">Sekvenserarna kallas ofta _escape-sekvenser_.</span><span class="sxs-lookup"><span data-stu-id="304b4-109">The sequences are commonly known as _escape sequences_.</span></span>

<span data-ttu-id="304b4-110">Escape-sekvenser börjar med snedstrecket, som kallas grav accent (ASCII 96) och är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="304b4-110">Escape sequences begin with the backtick character, known as the grave accent (ASCII 96), and are case-sensitive.</span></span> <span data-ttu-id="304b4-111">Det kan också kallas _escape-tecken_.</span><span class="sxs-lookup"><span data-stu-id="304b4-111">The backtick character can also be referred to as the _escape character_.</span></span>

<span data-ttu-id="304b4-112">Escape-sekvenser tolkas bara när de finns i strängar med dubbla citat tecken ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="304b4-112">Escape sequences are only interpreted when contained in double-quoted (`"`) strings.</span></span>

<span data-ttu-id="304b4-113">PowerShell känner igen följande escape-sekvenser:</span><span class="sxs-lookup"><span data-stu-id="304b4-113">PowerShell recognizes these escape sequences:</span></span>

|  <span data-ttu-id="304b4-114">Sequence</span><span class="sxs-lookup"><span data-stu-id="304b4-114">Sequence</span></span>   |       <span data-ttu-id="304b4-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="304b4-115">Description</span></span>       |
| ----------- | ----------------------- |
| `` `0 ``    | <span data-ttu-id="304b4-116">Null</span><span class="sxs-lookup"><span data-stu-id="304b4-116">Null</span></span>                    |
| `` `a ``    | <span data-ttu-id="304b4-117">Varning</span><span class="sxs-lookup"><span data-stu-id="304b4-117">Alert</span></span>                   |
| `` `b ``    | <span data-ttu-id="304b4-118">Backsteg</span><span class="sxs-lookup"><span data-stu-id="304b4-118">Backspace</span></span>               |
| `` `e ``    | <span data-ttu-id="304b4-119">Escape</span><span class="sxs-lookup"><span data-stu-id="304b4-119">Escape</span></span>                  |
| `` `f ``    | <span data-ttu-id="304b4-120">Formulär inmatning</span><span class="sxs-lookup"><span data-stu-id="304b4-120">Form feed</span></span>               |
| `` `n ``    | <span data-ttu-id="304b4-121">Ny rad</span><span class="sxs-lookup"><span data-stu-id="304b4-121">New line</span></span>                |
| `` `r ``    | <span data-ttu-id="304b4-122">Vagn retur</span><span class="sxs-lookup"><span data-stu-id="304b4-122">Carriage return</span></span>         |
| `` `t ``    | <span data-ttu-id="304b4-123">Vågrät TABB</span><span class="sxs-lookup"><span data-stu-id="304b4-123">Horizontal tab</span></span>          |
| `` `u{x} `` | <span data-ttu-id="304b4-124">Escape-sekvens för Unicode</span><span class="sxs-lookup"><span data-stu-id="304b4-124">Unicode escape sequence</span></span> |
| `` `v ``    | <span data-ttu-id="304b4-125">Lodrät TABB</span><span class="sxs-lookup"><span data-stu-id="304b4-125">Vertical tab</span></span>            |

<span data-ttu-id="304b4-126">PowerShell har också en speciell token för att markera var du vill att parsningen ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="304b4-126">PowerShell also has a special token to mark where you want parsing to stop.</span></span> <span data-ttu-id="304b4-127">Alla tecken som följer denna token används som litterala värden som inte tolkas.</span><span class="sxs-lookup"><span data-stu-id="304b4-127">All characters that follow this token are used as literal values that aren't interpreted.</span></span>

<span data-ttu-id="304b4-128">Särskild tolknings-token:</span><span class="sxs-lookup"><span data-stu-id="304b4-128">Special parsing token:</span></span>

| <span data-ttu-id="304b4-129">Sequence</span><span class="sxs-lookup"><span data-stu-id="304b4-129">Sequence</span></span> |            <span data-ttu-id="304b4-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="304b4-130">Description</span></span>             |
| -------- | ---------------------------------- |
| `--%`    | <span data-ttu-id="304b4-131">Sluta parsa något som följer</span><span class="sxs-lookup"><span data-stu-id="304b4-131">Stop parsing anything that follows</span></span> |

## <a name="null-0"></a><span data-ttu-id="304b4-132">Null (' 0)</span><span class="sxs-lookup"><span data-stu-id="304b4-132">Null (\`0)</span></span>

<span data-ttu-id="304b4-133">Null- `` `0 `` tecken () visas som ett tomt utrymme i PowerShell-utdata.</span><span class="sxs-lookup"><span data-stu-id="304b4-133">The null (`` `0 ``) character appears as an empty space in PowerShell output.</span></span>
<span data-ttu-id="304b4-134">Med den här funktionen kan du använda PowerShell för att läsa och bearbeta textfiler som använder null-tecken, t. ex. sträng avslutning eller post avslutnings indikatorer.</span><span class="sxs-lookup"><span data-stu-id="304b4-134">This functionality allows you to use PowerShell to read and process text files that use null characters, such as string termination or record termination indicators.</span></span> <span data-ttu-id="304b4-135">Det särskilda null-värdet är inte detsamma som `$null` variabeln som lagrar ett **Null** -värde.</span><span class="sxs-lookup"><span data-stu-id="304b4-135">The null special character isn't equivalent to the `$null` variable, which stores a **null** value.</span></span>

## <a name="alert-a"></a><span data-ttu-id="304b4-136">Varning (' a)</span><span class="sxs-lookup"><span data-stu-id="304b4-136">Alert (\`a)</span></span>

<span data-ttu-id="304b4-137">Varning ( `` `a `` )-symbolen skickar en signal signal till datorns högtalare.</span><span class="sxs-lookup"><span data-stu-id="304b4-137">The alert (`` `a ``) character sends a beep signal to the computer's speaker.</span></span>
<span data-ttu-id="304b4-138">Du kan använda det här alternativet för att varna en användare om en förestående åtgärd.</span><span class="sxs-lookup"><span data-stu-id="304b4-138">You can use this character to warn a user about an impending action.</span></span> <span data-ttu-id="304b4-139">I följande exempel skickas två pip signaler till den lokala datorns högtalare.</span><span class="sxs-lookup"><span data-stu-id="304b4-139">The following example sends two beep signals to the local computer's speaker.</span></span>

```powershell
for ($i = 0; $i -le 1; $i++){"`a"}
```

## <a name="backspace-b"></a><span data-ttu-id="304b4-140">Backsteg (' b)</span><span class="sxs-lookup"><span data-stu-id="304b4-140">Backspace (\`b)</span></span>

<span data-ttu-id="304b4-141">Tecknet Backsteg ( `` `b `` ) flyttar tillbaka markören ett tecken, men tar inte bort några tecken.</span><span class="sxs-lookup"><span data-stu-id="304b4-141">The backspace (`` `b ``) character moves the cursor back one character, but it doesn't delete any characters.</span></span>

<span data-ttu-id="304b4-142">Exemplet skriver **säkerhets kopian** av ordet och flyttar sedan tillbaka markören två gånger.</span><span class="sxs-lookup"><span data-stu-id="304b4-142">The example writes the word **backup** and then moves the cursor back twice.</span></span>
<span data-ttu-id="304b4-143">Sedan skriver du ett blank steg följt av ordet **ut** på den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="304b4-143">Then, at the new position, writes a space followed by the word **out**.</span></span>

```powershell
"backup`b`b out"
```

```Output
back out
```

## <a name="escape-e"></a><span data-ttu-id="304b4-144">Escape (' e)</span><span class="sxs-lookup"><span data-stu-id="304b4-144">Escape (\`e)</span></span>

<span data-ttu-id="304b4-145">Tecknet Escape ( `` `e `` ) används oftast för att ange en virtuell terminal-sekvens (ANSI escape-sekvens) som ändrar färgen på text och andra textattribut, till exempel fetstil och understrykning.</span><span class="sxs-lookup"><span data-stu-id="304b4-145">The escape (`` `e ``) character is most commonly used to specify a virtual terminal sequence (ANSI escape sequence) that modifies the color of text and other text attributes such as bolding and underlining.</span></span> <span data-ttu-id="304b4-146">Dessa sekvenser kan också användas för markör placering och rullning.</span><span class="sxs-lookup"><span data-stu-id="304b4-146">These sequences can also be used for cursor positioning and scrolling.</span></span> <span data-ttu-id="304b4-147">PowerShell-värden måste ha stöd för virtuella Terminal-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="304b4-147">The PowerShell host must support virtual terminal sequences.</span></span> <span data-ttu-id="304b4-148">Du kan kontrol lera det booleska värdet för `$Host.UI.SupportsVirtualTerminal` för att avgöra om dessa ANSI-sekvenser stöds.</span><span class="sxs-lookup"><span data-stu-id="304b4-148">You can check the boolean value of `$Host.UI.SupportsVirtualTerminal` to determine if these ANSI sequences are supported.</span></span>

<span data-ttu-id="304b4-149">Mer information om ANSI escape-sekvenser finns [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span><span class="sxs-lookup"><span data-stu-id="304b4-149">For more information about ANSI escape sequences, see [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).</span></span>

<span data-ttu-id="304b4-150">I följande exempel matas texten med en grön förgrunds färg.</span><span class="sxs-lookup"><span data-stu-id="304b4-150">The following example outputs text with a green foreground color.</span></span>

```powershell
$fgColor = 32 # green
"`e[${fgColor}mGreen text`e[0m"
```

```Output
Green text
```

## <a name="form-feed-f"></a><span data-ttu-id="304b4-151">Formulär flöde (' f)</span><span class="sxs-lookup"><span data-stu-id="304b4-151">Form feed (\`f)</span></span>

<span data-ttu-id="304b4-152">Tecken formatet form ( `` `f `` ) är en utskrifts instruktion som matar ut den aktuella sidan och fortsätter att skriva ut på nästa sida.</span><span class="sxs-lookup"><span data-stu-id="304b4-152">The form feed (`` `f ``) character is a print instruction that ejects the current page and continues printing on the next page.</span></span> <span data-ttu-id="304b4-153">Formulärets matnings tecken påverkar endast utskrivna dokument.</span><span class="sxs-lookup"><span data-stu-id="304b4-153">The form feed character only affects printed documents.</span></span> <span data-ttu-id="304b4-154">Det påverkar inte skärmens utdata.</span><span class="sxs-lookup"><span data-stu-id="304b4-154">It doesn't affect screen output.</span></span>

## <a name="new-line-n"></a><span data-ttu-id="304b4-155">Ny rad (' n)</span><span class="sxs-lookup"><span data-stu-id="304b4-155">New line (\`n)</span></span>

<span data-ttu-id="304b4-156">Det nya Line ( `` `n `` )-symbolen infogar en rad brytning direkt efter specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="304b4-156">The new line (`` `n ``) character inserts a line break immediately after the character.</span></span>

<span data-ttu-id="304b4-157">Det här exemplet visar hur du använder det nya rad brytnings alternativet för att skapa rad brytningar i ett `Write-Host` kommando.</span><span class="sxs-lookup"><span data-stu-id="304b4-157">This example shows how to use the new line character to create line breaks in a `Write-Host` command.</span></span>

```powershell
"There are two line breaks to create a blank line`n`nbetween the words."
```

```Output
There are two line breaks to create a blank line

between the words.
```

## <a name="carriage-return-r"></a><span data-ttu-id="304b4-158">Vagn retur (' r)</span><span class="sxs-lookup"><span data-stu-id="304b4-158">Carriage return (\`r)</span></span>

<span data-ttu-id="304b4-159">Tecken för vagn retur ( `` `r `` ) flyttar utmatnings markören till början av den aktuella raden och fortsätter skriva.</span><span class="sxs-lookup"><span data-stu-id="304b4-159">The carriage return (`` `r ``) character moves the output cursor to the beginning of the current line and continues writing.</span></span> <span data-ttu-id="304b4-160">Alla tecken på den aktuella raden skrivs över.</span><span class="sxs-lookup"><span data-stu-id="304b4-160">Any characters on the current line are overwritten.</span></span>

<span data-ttu-id="304b4-161">I det här exemplet skrivs texten före vagn returen över.</span><span class="sxs-lookup"><span data-stu-id="304b4-161">In this example, the text before the carriage return is overwritten.</span></span>

```powershell
Write-Host "These characters are overwritten.`rI want this text instead "
```

<span data-ttu-id="304b4-162">Observera att texten innan `` `r `` specialtecknet tas bort skrivs över.</span><span class="sxs-lookup"><span data-stu-id="304b4-162">Notice that the text before the `` `r `` character is not deleted, it is overwritten.</span></span>

```Output
I want this text instead written.
```

## <a name="horizontal-tab-t"></a><span data-ttu-id="304b4-163">Vågrät TABB (ej)</span><span class="sxs-lookup"><span data-stu-id="304b4-163">Horizontal tab (\`t)</span></span>

<span data-ttu-id="304b4-164">Den vågräta tabben ( `` `t `` )-tecken går vidare till nästa tabbstopp och fortsätter att skriva vid den punkten.</span><span class="sxs-lookup"><span data-stu-id="304b4-164">The horizontal tab (`` `t ``) character advances to the next tab stop and continues writing at that point.</span></span> <span data-ttu-id="304b4-165">Som standard har PowerShell-konsolen ett tabbstopp med var åttonde plats.</span><span class="sxs-lookup"><span data-stu-id="304b4-165">By default, the PowerShell console has a tab stop at every eighth space.</span></span>

<span data-ttu-id="304b4-166">I det här exemplet infogas två flikar mellan varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="304b4-166">This example inserts two tabs between each column.</span></span>

```powershell
"Column1`t`tColumn2`t`tColumn3"
```

```Output
Column1         Column2         Column3
```

## <a name="unicode-character-ux"></a><span data-ttu-id="304b4-167">Unicode-tecken (' u {x})</span><span class="sxs-lookup"><span data-stu-id="304b4-167">Unicode character (\`u{x})</span></span>

<span data-ttu-id="304b4-168">Med Unicode Escape Sequence ( `` `u{x} `` ) kan du ange valfritt Unicode-tecken genom den hexadecimala representationen av dess kod punkt.</span><span class="sxs-lookup"><span data-stu-id="304b4-168">The Unicode escape sequence (`` `u{x} ``) allows you to specify any Unicode character by the hexadecimal representation of its code point.</span></span> <span data-ttu-id="304b4-169">Detta inkluderar Unicode-tecken ovanför det grundläggande flerspråkiga planet (> `0xFFFF` ) som innehåller Emoji-tecken, till exempel tangenterna **tummen up** ( `` `u{1F44D} `` ).</span><span class="sxs-lookup"><span data-stu-id="304b4-169">This includes Unicode characters above the Basic Multilingual Plane (> `0xFFFF`) which includes emoji characters such as the **thumbs up** (`` `u{1F44D} ``) character.</span></span> <span data-ttu-id="304b4-170">Unicode Escape-sekvensen kräver minst en hexadecimal siffra och har stöd för upp till sex hexadecimala siffror.</span><span class="sxs-lookup"><span data-stu-id="304b4-170">The Unicode escape sequence requires at least one hexadecimal digit and supports up to six hexadecimal digits.</span></span> <span data-ttu-id="304b4-171">Det maximala hexadecimala värdet för sekvensen är `10FFFF` .</span><span class="sxs-lookup"><span data-stu-id="304b4-171">The maximum hexadecimal value for the sequence is `10FFFF`.</span></span>

<span data-ttu-id="304b4-172">I det här exemplet visas en **UPPIL** (&#x2195;) symbol.</span><span class="sxs-lookup"><span data-stu-id="304b4-172">This example outputs the **up down arrow** (&#x2195;) symbol.</span></span>

```powershell
"`u{2195}"
```

## <a name="vertical-tab-v"></a><span data-ttu-id="304b4-173">Lodrät TABB (' v)</span><span class="sxs-lookup"><span data-stu-id="304b4-173">Vertical tab (\`v)</span></span>

<span data-ttu-id="304b4-174">Den vågräta tabben ( `` `v `` )-tecken går vidare till nästa lodräta TABB och skriver återstående utdata vid den punkten.</span><span class="sxs-lookup"><span data-stu-id="304b4-174">The horizontal tab (`` `v ``) character advances to the next vertical tab stop and writes the remaining output at that point.</span></span> <span data-ttu-id="304b4-175">Detta har ingen påverkan i standard konsolen för Windows.</span><span class="sxs-lookup"><span data-stu-id="304b4-175">This has no effect in the default Windows console.</span></span>

```powershell
Write-Host "There is a vertical tab`vbetween the words."
```

<span data-ttu-id="304b4-176">I följande exempel visas de utdata som du skulle få på en skrivare eller en annan konsol värd.</span><span class="sxs-lookup"><span data-stu-id="304b4-176">The following example shows the output you would get on a printer or in a different console host.</span></span>

```Output
There is a vertical tab
                       between the words.
```

## <a name="stop-parsing-token---"></a><span data-ttu-id="304b4-177">Stoppa-parsing-token (--%)</span><span class="sxs-lookup"><span data-stu-id="304b4-177">Stop-parsing token (--%)</span></span>

<span data-ttu-id="304b4-178">Token för Stop parsning ( `--%` ) förhindrar att PowerShell tolkar strängar som PowerShell-kommandon och uttryck.</span><span class="sxs-lookup"><span data-stu-id="304b4-178">The stop-parsing (`--%`) token prevents PowerShell from interpreting strings as PowerShell commands and expressions.</span></span> <span data-ttu-id="304b4-179">Detta gör att dessa strängar kan skickas till andra program för tolkning.</span><span class="sxs-lookup"><span data-stu-id="304b4-179">This allows those strings to be passed to other programs for interpretation.</span></span>

<span data-ttu-id="304b4-180">Placera token för att parsa efter program namn och före program argument som kan orsaka fel.</span><span class="sxs-lookup"><span data-stu-id="304b4-180">Place the stop-parsing token after the program name and before program arguments that might cause errors.</span></span>

<span data-ttu-id="304b4-181">I det här exemplet `Icacls` använder kommandot Stop-parsing-token.</span><span class="sxs-lookup"><span data-stu-id="304b4-181">In this example, the `Icacls` command uses the stop-parsing token.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="304b4-182">PowerShell skickar följande sträng till `Icacls` .</span><span class="sxs-lookup"><span data-stu-id="304b4-182">PowerShell sends the following string to `Icacls`.</span></span>

```
X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="304b4-183">Här är ett annat exempel.</span><span class="sxs-lookup"><span data-stu-id="304b4-183">Here is another example.</span></span> <span data-ttu-id="304b4-184">Funktionen **showArgs** matar ut värdena som skickas till den.</span><span class="sxs-lookup"><span data-stu-id="304b4-184">The **showArgs** function outputs the values passed to it.</span></span> <span data-ttu-id="304b4-185">I det här exemplet skickar vi variabeln med namnet `$HOME` till funktionen två gånger.</span><span class="sxs-lookup"><span data-stu-id="304b4-185">In this example, we pass the variable named `$HOME` to the function twice.</span></span>

```powershell
function showArgs {
  "`$args = " + ($args -join '|')
}

showArgs $HOME --% $HOME
```

Du kan se i utdata som för den första parametern `$HOME` tolkas variabeln av PowerShell så att värdet för variabeln skickas till funktionen. <span data-ttu-id="304b4-187">Den andra användningen av `$HOME` kommer efter att token för att tolkas, så strängen "$Home" skickas till funktionen utan tolkning.</span><span class="sxs-lookup"><span data-stu-id="304b4-187">The second use of `$HOME` comes after the stop-parsing token, so the string "$HOME" is passed to the function without interpretation.</span></span>

```Output
$args = C:\Users\username|--%|$HOME
```

<span data-ttu-id="304b4-188">Mer information om stoppa-parsing-token finns [about_Parsing](about_Parsing.md).</span><span class="sxs-lookup"><span data-stu-id="304b4-188">For more information about the stop-parsing token, see [about_Parsing](about_Parsing.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="304b4-189">Se även</span><span class="sxs-lookup"><span data-stu-id="304b4-189">See also</span></span>

[<span data-ttu-id="304b4-190">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="304b4-190">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
