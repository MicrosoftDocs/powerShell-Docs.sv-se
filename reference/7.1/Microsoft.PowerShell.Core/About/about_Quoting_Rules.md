---
description: Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: 8d09171a1459a8ad03b54f2a4ef7a81c5983f6b8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271707"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="ab17b-104">Om citat regler</span><span class="sxs-lookup"><span data-stu-id="ab17b-104">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="ab17b-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ab17b-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ab17b-106">Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab17b-106">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ab17b-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ab17b-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ab17b-108">Citat tecken används för att ange en tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="ab17b-108">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="ab17b-109">Du kan omge en sträng med enkla citat tecken ( `'` ) eller dubbla citat tecken ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="ab17b-109">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="ab17b-110">Citat tecken används också för att skapa en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="ab17b-110">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="ab17b-111">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="ab17b-111">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="ab17b-112">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="ab17b-112">A here-string can span multiple lines.</span></span> <span data-ttu-id="ab17b-113">Alla rader i en här-sträng tolkas som strängar, även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-113">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="ab17b-114">I kommandon till fjärrdatorer definierar citat tecken de delar av kommandot som körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ab17b-114">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="ab17b-115">I en fjärran sluten session avgör citat tecken också om variablerna i ett kommando tolkas först på den lokala datorn eller på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="ab17b-115">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="ab17b-116">STRÄNGAR MED ENKLA OCH DUBBLA CITAT TECKEN</span><span class="sxs-lookup"><span data-stu-id="ab17b-116">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="ab17b-117">När du omger en sträng med dubbla citat tecken (en dubbels omgiven sträng) ersätts variabel namn som föregås av ett dollar tecken ( `$` ) med variabelns värde innan strängen skickas till kommandot för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ab17b-117">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="ab17b-118">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="ab17b-119">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="ab17b-120">Dessutom utvärderas uttryck i en dubbelt Citerad sträng och resultatet infogas i strängen.</span><span class="sxs-lookup"><span data-stu-id="ab17b-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="ab17b-121">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="ab17b-122">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="ab17b-123">När du omger en sträng med enkla citat tecken (en sträng med en citat tecken) skickas strängen till kommandot exakt när du skriver den.</span><span class="sxs-lookup"><span data-stu-id="ab17b-123">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="ab17b-124">Ingen ersättning utförs.</span><span class="sxs-lookup"><span data-stu-id="ab17b-124">No substitution is performed.</span></span> <span data-ttu-id="ab17b-125">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-125">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="ab17b-126">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-126">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="ab17b-127">På samma sätt utvärderas inte uttryck i ensiffriga strängar.</span><span class="sxs-lookup"><span data-stu-id="ab17b-127">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="ab17b-128">De tolkas som litteraler.</span><span class="sxs-lookup"><span data-stu-id="ab17b-128">They are interpreted as literals.</span></span> <span data-ttu-id="ab17b-129">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-129">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="ab17b-130">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-130">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="ab17b-131">För att förhindra att ett variabel värde byts ut i en dubbel-Citerad sträng, använder du bakticket ( `` ` `` ) (ASCII 96), som är PowerShell-escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-131">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="ab17b-132">I följande exempel förhindrar det Baknings kort som föregår den första $i variabeln att PowerShell ersätter variabelns namn med värdet.</span><span class="sxs-lookup"><span data-stu-id="ab17b-132">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="ab17b-133">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-133">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="ab17b-134">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-134">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="ab17b-135">Om du vill att dubbla citat tecken ska visas i en sträng omger du hela strängen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-135">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="ab17b-136">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-136">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="ab17b-137">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-137">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="ab17b-138">Du kan också ange en ensiffrig sträng i en sträng med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-138">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="ab17b-139">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-139">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="ab17b-140">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-140">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="ab17b-141">Eller, dubbla citat tecknen runt en fras med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-141">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="ab17b-142">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-142">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="ab17b-143">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-143">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="ab17b-144">Om du vill inkludera ett enkelt citat tecken i en enciterad sträng använder du ett andra sammanhängande citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-144">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="ab17b-145">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-145">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="ab17b-146">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-146">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="ab17b-147">Om du vill tvinga PowerShell att tolka dubbla citat tecken bokstavligen använder du ett Baknings tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-147">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="ab17b-148">Detta förhindrar att PowerShell tolkar citat tecknet som en sträng avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ab17b-148">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="ab17b-149">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-149">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="ab17b-150">Eftersom innehållet i ensiffriga strängar tolkas bokstavligen, behandlas det som ett bokstavligt tecken och visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="ab17b-150">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="ab17b-151">HÄR – STRÄNGAR</span><span class="sxs-lookup"><span data-stu-id="ab17b-151">HERE-STRINGS</span></span>

<span data-ttu-id="ab17b-152">Offert reglerna för här – strängarna är något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="ab17b-152">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="ab17b-153">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="ab17b-153">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="ab17b-154">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="ab17b-154">A here-string can span multiple lines.</span></span> <span data-ttu-id="ab17b-155">Alla rader i en här-sträng tolkas som strängar även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-155">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="ab17b-156">Precis som med vanliga strängar ersätts variablerna med deras värden i dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab17b-156">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="ab17b-157">I ensiffriga här – strängar ersätts inte variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="ab17b-157">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="ab17b-158">Du kan använda här – strängar för valfri text, men de är särskilt användbara för följande typer av text:</span><span class="sxs-lookup"><span data-stu-id="ab17b-158">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="ab17b-159">Text som innehåller litterala citat tecken</span><span class="sxs-lookup"><span data-stu-id="ab17b-159">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="ab17b-160">Flera rader med text, till exempel texten i en HTML-eller XML-fil</span><span class="sxs-lookup"><span data-stu-id="ab17b-160">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="ab17b-161">Hjälp texten för ett skript eller funktions dokument</span><span class="sxs-lookup"><span data-stu-id="ab17b-161">The Help text for a script or function document</span></span>

<span data-ttu-id="ab17b-162">En här-sträng kan ha något av följande format, där `<Enter>` representerar rad matnings tecken eller sid matnings tecken som läggs till när du trycker på <kbd>RETUR</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="ab17b-162">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="ab17b-163">Dubbla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="ab17b-163">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="ab17b-164">Enkla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="ab17b-164">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="ab17b-165">I båda formaten måste det avslutande citat tecknet vara det första tecknet på raden.</span><span class="sxs-lookup"><span data-stu-id="ab17b-165">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="ab17b-166">En här-sträng innehåller all text mellan de två dolda tecknen.</span><span class="sxs-lookup"><span data-stu-id="ab17b-166">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="ab17b-167">I den här strängen tolkas alla citat tecken bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="ab17b-167">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="ab17b-168">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-168">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="ab17b-169">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-169">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="ab17b-170">Om du använder en här-sträng kan du förenkla användningen av en sträng i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="ab17b-170">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="ab17b-171">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-171">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="ab17b-172">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-172">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="ab17b-173">I ensiffriga här – strängar tolkas variablerna i bokstavligen och reproduceras exakt.</span><span class="sxs-lookup"><span data-stu-id="ab17b-173">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="ab17b-174">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-174">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="ab17b-175">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-175">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="ab17b-176">I Double-citerade här – strängar ersätts variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="ab17b-176">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="ab17b-177">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ab17b-177">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="ab17b-178">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="ab17b-178">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="ab17b-179">Här – strängarna används vanligt vis för att tilldela flera rader till en variabel.</span><span class="sxs-lookup"><span data-stu-id="ab17b-179">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="ab17b-180">Följande – sträng tilldelar till exempel en sida med XML till variabeln $page.</span><span class="sxs-lookup"><span data-stu-id="ab17b-180">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

```powershell
$page = [XML] @"
<command:command xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
<command:details>
        <command:name>
               Format-Table
        </command:name>
        <maml:description>
            <maml:para>Formats the output as a table.</maml:para>
        </maml:description>
        <command:verb>format</command:verb>
        <command:noun>table</command:noun>
        <dev:version></dev:version>
</command:details>
...
</command:command>
"@
```

<span data-ttu-id="ab17b-181">Här – strängarna är också ett bekvämt format för inmatade `ConvertFrom-StringData` cmdlet, som konverterar hit-strängar till hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="ab17b-181">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="ab17b-182">Mer information finns i `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="ab17b-182">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab17b-183">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ab17b-183">SEE ALSO</span></span>

[<span data-ttu-id="ab17b-184">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="ab17b-184">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="ab17b-185">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="ab17b-185">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
