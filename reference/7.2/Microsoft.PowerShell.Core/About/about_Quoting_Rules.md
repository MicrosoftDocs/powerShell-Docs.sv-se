---
description: Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: fcb4bff0ca27ad0bc4e3b4c74e58e9fefa8cac7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709690"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="16a75-103">Om citat regler</span><span class="sxs-lookup"><span data-stu-id="16a75-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="16a75-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="16a75-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="16a75-105">Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="16a75-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="16a75-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="16a75-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="16a75-107">Citat tecken används för att ange en tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="16a75-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="16a75-108">Du kan omge en sträng med enkla citat tecken ( `'` ) eller dubbla citat tecken ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="16a75-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="16a75-109">Citat tecken används också för att skapa en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="16a75-109">Quotation marks are also used to create a here-string.</span></span> <span data-ttu-id="16a75-110">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="16a75-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="16a75-111">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="16a75-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="16a75-112">Alla rader i en här-sträng tolkas som strängar, även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="16a75-113">I kommandon till fjärrdatorer definierar citat tecken de delar av kommandot som körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="16a75-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="16a75-114">I en fjärran sluten session avgör citat tecken också om variablerna i ett kommando tolkas först på den lokala datorn eller på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="16a75-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

### <a name="single-and-double-quoted-strings"></a><span data-ttu-id="16a75-115">STRÄNGAR MED ENKLA OCH DUBBLA CITAT TECKEN</span><span class="sxs-lookup"><span data-stu-id="16a75-115">SINGLE AND DOUBLE-QUOTED STRINGS</span></span>

<span data-ttu-id="16a75-116">När du omger en sträng med dubbla citat tecken (en dubbels omgiven sträng) ersätts variabel namn som föregås av ett dollar tecken ( `$` ) med variabelns värde innan strängen skickas till kommandot för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="16a75-116">When you enclose a string in double quotation marks (a double-quoted string), variable names that are preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="16a75-117">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-117">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="16a75-118">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-118">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="16a75-119">Dessutom utvärderas uttryck i en dubbelt Citerad sträng och resultatet infogas i strängen.</span><span class="sxs-lookup"><span data-stu-id="16a75-119">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="16a75-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-120">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="16a75-121">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-121">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="16a75-122">När du omger en sträng med enkla citat tecken (en sträng med en citat tecken) skickas strängen till kommandot exakt när du skriver den.</span><span class="sxs-lookup"><span data-stu-id="16a75-122">When you enclose a string in single-quotation marks (a single-quoted string), the string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="16a75-123">Ingen ersättning utförs.</span><span class="sxs-lookup"><span data-stu-id="16a75-123">No substitution is performed.</span></span> <span data-ttu-id="16a75-124">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-124">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="16a75-125">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-125">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="16a75-126">På samma sätt utvärderas inte uttryck i ensiffriga strängar.</span><span class="sxs-lookup"><span data-stu-id="16a75-126">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="16a75-127">De tolkas som litteraler.</span><span class="sxs-lookup"><span data-stu-id="16a75-127">They are interpreted as literals.</span></span> <span data-ttu-id="16a75-128">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-128">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="16a75-129">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-129">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="16a75-130">För att förhindra att ett variabel värde byts ut i en dubbel-Citerad sträng, använder du bakticket ( `` ` `` ) (ASCII 96), som är PowerShell-escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-130">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="16a75-131">I följande exempel förhindrar det Baknings kort som föregår den första $i variabeln att PowerShell ersätter variabelns namn med värdet.</span><span class="sxs-lookup"><span data-stu-id="16a75-131">In the following example, the backtick character that precedes the first $i variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="16a75-132">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-132">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="16a75-133">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-133">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="16a75-134">Om du vill att dubbla citat tecken ska visas i en sträng omger du hela strängen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-134">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="16a75-135">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-135">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="16a75-136">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-136">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="16a75-137">Du kan också ange en ensiffrig sträng i en sträng med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-137">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="16a75-138">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-138">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="16a75-139">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-139">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="16a75-140">Eller, dubbla citat tecknen runt en fras med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-140">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="16a75-141">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-141">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="16a75-142">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-142">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="16a75-143">Om du vill inkludera ett enkelt citat tecken i en enciterad sträng använder du ett andra sammanhängande citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-143">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="16a75-144">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-144">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="16a75-145">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-145">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="16a75-146">Om du vill tvinga PowerShell att tolka dubbla citat tecken bokstavligen använder du ett Baknings tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-146">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="16a75-147">Detta förhindrar att PowerShell tolkar citat tecknet som en sträng avgränsare.</span><span class="sxs-lookup"><span data-stu-id="16a75-147">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="16a75-148">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-148">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="16a75-149">Eftersom innehållet i ensiffriga strängar tolkas bokstavligen, behandlas det som ett bokstavligt tecken och visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="16a75-149">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

### <a name="here-strings"></a><span data-ttu-id="16a75-150">HÄR – STRÄNGAR</span><span class="sxs-lookup"><span data-stu-id="16a75-150">HERE-STRINGS</span></span>

<span data-ttu-id="16a75-151">Offert reglerna för här – strängarna är något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="16a75-151">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="16a75-152">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="16a75-152">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="16a75-153">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="16a75-153">A here-string can span multiple lines.</span></span> <span data-ttu-id="16a75-154">Alla rader i en här-sträng tolkas som strängar även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-154">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="16a75-155">Precis som med vanliga strängar ersätts variablerna med deras värden i dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="16a75-155">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="16a75-156">I ensiffriga här – strängar ersätts inte variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="16a75-156">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="16a75-157">Du kan använda här – strängar för valfri text, men de är särskilt användbara för följande typer av text:</span><span class="sxs-lookup"><span data-stu-id="16a75-157">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="16a75-158">Text som innehåller litterala citat tecken</span><span class="sxs-lookup"><span data-stu-id="16a75-158">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="16a75-159">Flera rader med text, till exempel texten i en HTML-eller XML-fil</span><span class="sxs-lookup"><span data-stu-id="16a75-159">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="16a75-160">Hjälp texten för ett skript eller funktions dokument</span><span class="sxs-lookup"><span data-stu-id="16a75-160">The Help text for a script or function document</span></span>

<span data-ttu-id="16a75-161">En här-sträng kan ha något av följande format, där `<Enter>` representerar rad matnings tecken eller sid matnings tecken som läggs till när du trycker på <kbd>RETUR</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="16a75-161">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="16a75-162">Dubbla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="16a75-162">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="16a75-163">Enkla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="16a75-163">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="16a75-164">I båda formaten måste det avslutande citat tecknet vara det första tecknet på raden.</span><span class="sxs-lookup"><span data-stu-id="16a75-164">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="16a75-165">En här-sträng innehåller all text mellan de två dolda tecknen.</span><span class="sxs-lookup"><span data-stu-id="16a75-165">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="16a75-166">I den här strängen tolkas alla citat tecken bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="16a75-166">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="16a75-167">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-167">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="16a75-168">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-168">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="16a75-169">Om du använder en här-sträng kan du förenkla användningen av en sträng i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="16a75-169">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="16a75-170">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-170">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="16a75-171">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-171">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="16a75-172">I ensiffriga här – strängar tolkas variablerna i bokstavligen och reproduceras exakt.</span><span class="sxs-lookup"><span data-stu-id="16a75-172">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="16a75-173">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-173">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="16a75-174">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-174">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="16a75-175">I Double-citerade här – strängar ersätts variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="16a75-175">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="16a75-176">Exempel:</span><span class="sxs-lookup"><span data-stu-id="16a75-176">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="16a75-177">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="16a75-177">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="16a75-178">Här – strängarna används vanligt vis för att tilldela flera rader till en variabel.</span><span class="sxs-lookup"><span data-stu-id="16a75-178">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="16a75-179">Följande – sträng tilldelar till exempel en sida med XML till variabeln $page.</span><span class="sxs-lookup"><span data-stu-id="16a75-179">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

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

<span data-ttu-id="16a75-180">Här – strängarna är också ett bekvämt format för inmatade `ConvertFrom-StringData` cmdlet, som konverterar hit-strängar till hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="16a75-180">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="16a75-181">Mer information finns i `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="16a75-181">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="16a75-182">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="16a75-182">SEE ALSO</span></span>

[<span data-ttu-id="16a75-183">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="16a75-183">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="16a75-184">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="16a75-184">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
