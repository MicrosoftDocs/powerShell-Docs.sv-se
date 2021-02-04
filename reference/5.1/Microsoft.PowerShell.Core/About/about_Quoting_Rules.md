---
description: Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_quoting_rules?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Quoting_Rules
ms.openlocfilehash: b100ff8ab4be84b7117efc5724119221351ba4bf
ms.sourcegitcommit: 9a86cac80402d8193147058d4ba50e07b26059dd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97490679"
---
# <a name="about-quoting-rules"></a><span data-ttu-id="f14a9-103">Om citat regler</span><span class="sxs-lookup"><span data-stu-id="f14a9-103">About Quoting Rules</span></span>

## <a name="short-description"></a><span data-ttu-id="f14a9-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="f14a9-104">Short description</span></span>
<span data-ttu-id="f14a9-105">Beskriver regler för användning av enkla och dubbla citat tecken i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f14a9-105">Describes rules for using single and double quotation marks in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="f14a9-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="f14a9-106">Long description</span></span>

<span data-ttu-id="f14a9-107">Citat tecken används för att ange en tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="f14a9-107">Quotation marks are used to specify a literal string.</span></span> <span data-ttu-id="f14a9-108">Du kan omge en sträng med enkla citat tecken ( `'` ) eller dubbla citat tecken ( `"` ).</span><span class="sxs-lookup"><span data-stu-id="f14a9-108">You can enclose a string in single quotation marks (`'`) or double quotation marks (`"`).</span></span>

<span data-ttu-id="f14a9-109">Citat tecken används också för att skapa en _här-sträng_.</span><span class="sxs-lookup"><span data-stu-id="f14a9-109">Quotation marks are also used to create a _here-string_.</span></span> <span data-ttu-id="f14a9-110">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="f14a9-110">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="f14a9-111">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="f14a9-111">A here-string can span multiple lines.</span></span> <span data-ttu-id="f14a9-112">Alla rader i en här-sträng tolkas som strängar, även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-112">All the lines in a here-string are interpreted as strings, even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="f14a9-113">I kommandon till fjärrdatorer definierar citat tecken de delar av kommandot som körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f14a9-113">In commands to remote computers, quotation marks define the parts of the command that are run on the remote computer.</span></span> <span data-ttu-id="f14a9-114">I en fjärran sluten session avgör citat tecken också om variablerna i ett kommando tolkas först på den lokala datorn eller på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f14a9-114">In a remote session, quotation marks also determine whether the variables in a command are interpreted first on the local computer or on the remote computer.</span></span>

## <a name="single-and-double-quoted-strings"></a><span data-ttu-id="f14a9-115">Strängar med enkla och dubbla citat tecken</span><span class="sxs-lookup"><span data-stu-id="f14a9-115">Single and double-quoted strings</span></span>

<span data-ttu-id="f14a9-116">En sträng som omges av dubbla citat tecken är en _expanderbar_ sträng.</span><span class="sxs-lookup"><span data-stu-id="f14a9-116">A string enclosed in double quotation marks is an _expandable_ string.</span></span> <span data-ttu-id="f14a9-117">Variabel namn som föregås av ett dollar tecken ( `$` ) ersätts med variabelns värde innan strängen skickas till kommandot för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="f14a9-117">Variable names preceded by a dollar sign (`$`) are replaced with the variable's value before the string is passed to the command for processing.</span></span>

<span data-ttu-id="f14a9-118">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-118">For example:</span></span>

```powershell
$i = 5
"The value of $i is $i."
```

<span data-ttu-id="f14a9-119">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-119">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="f14a9-120">Dessutom utvärderas uttryck i en dubbelt Citerad sträng och resultatet infogas i strängen.</span><span class="sxs-lookup"><span data-stu-id="f14a9-120">Also, in a double-quoted string, expressions are evaluated, and the result is inserted in the string.</span></span> <span data-ttu-id="f14a9-121">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-121">For example:</span></span>

```powershell
"The value of $(2+3) is 5."
```

<span data-ttu-id="f14a9-122">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-122">The output of this command is:</span></span>

```Output
The value of 5 is 5.
```

<span data-ttu-id="f14a9-123">En sträng som omges av enkla citat tecken är en _orda Grant_ sträng.</span><span class="sxs-lookup"><span data-stu-id="f14a9-123">A string enclosed in single-quotation marks is a _verbatim_ string.</span></span> <span data-ttu-id="f14a9-124">Strängen skickas till kommandot exakt när du skriver den.</span><span class="sxs-lookup"><span data-stu-id="f14a9-124">The string is passed to the command exactly as you type it.</span></span> <span data-ttu-id="f14a9-125">Ingen ersättning utförs.</span><span class="sxs-lookup"><span data-stu-id="f14a9-125">No substitution is performed.</span></span>
<span data-ttu-id="f14a9-126">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-126">For example:</span></span>

```powershell
$i = 5
'The value of $i is $i.'
```

<span data-ttu-id="f14a9-127">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-127">The output of this command is:</span></span>

```Output
The value $i is $i.
```

<span data-ttu-id="f14a9-128">På samma sätt utvärderas inte uttryck i ensiffriga strängar.</span><span class="sxs-lookup"><span data-stu-id="f14a9-128">Similarly, expressions in single-quoted strings are not evaluated.</span></span> <span data-ttu-id="f14a9-129">De tolkas som litteraler.</span><span class="sxs-lookup"><span data-stu-id="f14a9-129">They are interpreted as literals.</span></span> <span data-ttu-id="f14a9-130">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-130">For example:</span></span>

```powershell
'The value of $(2+3) is 5.'
```

<span data-ttu-id="f14a9-131">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-131">The output of this command is:</span></span>

```Output
The value of $(2+3) is 5.
```

<span data-ttu-id="f14a9-132">För att förhindra att ett variabel värde byts ut i en dubbel-Citerad sträng, använder du bakticket ( `` ` `` ) (ASCII 96), som är PowerShell-escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-132">To prevent the substitution of a variable value in a double-quoted string, use the backtick character (`` ` ``)(ASCII 96), which is the PowerShell escape character.</span></span>

<span data-ttu-id="f14a9-133">I följande exempel hindrar det Baknings kort som föregår den första `$i` variabeln till att PowerShell ersätter variabelns namn med värdet.</span><span class="sxs-lookup"><span data-stu-id="f14a9-133">In the following example, the backtick character that precedes the first `$i` variable prevents PowerShell from replacing the variable name with its value.</span></span>
<span data-ttu-id="f14a9-134">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-134">For example:</span></span>

```powershell
$i = 5
"The value of `$i is $i."
```

<span data-ttu-id="f14a9-135">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-135">The output of this command is:</span></span>

```Output
The value $i is 5.
```

<span data-ttu-id="f14a9-136">Om du vill att dubbla citat tecken ska visas i en sträng omger du hela strängen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-136">To make double-quotation marks appear in a string, enclose the entire string in single quotation marks.</span></span> <span data-ttu-id="f14a9-137">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-137">For example:</span></span>

```powershell
'As they say, "live and learn."'
```

<span data-ttu-id="f14a9-138">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-138">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="f14a9-139">Du kan också ange en ensiffrig sträng i en sträng med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-139">You can also enclose a single-quoted string in a double-quoted string.</span></span> <span data-ttu-id="f14a9-140">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-140">For example:</span></span>

```powershell
"As they say, 'live and learn.'"
```

<span data-ttu-id="f14a9-141">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-141">The output of this command is:</span></span>

```Output
As they say, 'live and learn.'
```

<span data-ttu-id="f14a9-142">Eller, dubbla citat tecknen runt en fras med dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-142">Or, double the quotation marks around a double-quoted phrase.</span></span> <span data-ttu-id="f14a9-143">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-143">For example:</span></span>

```powershell
"As they say, ""live and learn."""
```

<span data-ttu-id="f14a9-144">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-144">The output of this command is:</span></span>

```Output
As they say, "live and learn."
```

<span data-ttu-id="f14a9-145">Om du vill inkludera ett enkelt citat tecken i en enciterad sträng använder du ett andra sammanhängande citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-145">To include a single quotation mark in a single-quoted string, use a second consecutive single quote.</span></span> <span data-ttu-id="f14a9-146">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-146">For example:</span></span>

```powershell
'don''t'
```

<span data-ttu-id="f14a9-147">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-147">The output of this command is:</span></span>

```Output
don't
```

<span data-ttu-id="f14a9-148">Om du vill tvinga PowerShell att tolka dubbla citat tecken bokstavligen använder du ett Baknings tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-148">To force PowerShell to interpret a double quotation mark literally, use a backtick character.</span></span> <span data-ttu-id="f14a9-149">Detta förhindrar att PowerShell tolkar citat tecknet som en sträng avgränsare.</span><span class="sxs-lookup"><span data-stu-id="f14a9-149">This prevents PowerShell from interpreting the quotation mark as a string delimiter.</span></span> <span data-ttu-id="f14a9-150">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-150">For example:</span></span>

```powershell
PS> "Use a quotation mark (`") to begin a string."
Use a quotation mark (") to begin a string.
PS> 'Use a quotation mark (`") to begin a string.'
Use a quotation mark (`") to begin a string.
```

<span data-ttu-id="f14a9-151">Eftersom innehållet i ensiffriga strängar tolkas bokstavligen, behandlas det som ett bokstavligt tecken och visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="f14a9-151">Because the contents of single-quoted strings are interpreted literally, you the backtick character is treated as a literal character and displayed in the output.</span></span>

## <a name="here-strings"></a><span data-ttu-id="f14a9-152">Här – strängar</span><span class="sxs-lookup"><span data-stu-id="f14a9-152">Here-strings</span></span>

<span data-ttu-id="f14a9-153">Offert reglerna för här – strängarna är något annorlunda.</span><span class="sxs-lookup"><span data-stu-id="f14a9-153">The quotation rules for here-strings are slightly different.</span></span>

<span data-ttu-id="f14a9-154">En här-sträng är en enciterad eller dubbels omgiven sträng där citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="f14a9-154">A here-string is a single-quoted or double-quoted string in which quotation marks are interpreted literally.</span></span> <span data-ttu-id="f14a9-155">En här-sträng kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="f14a9-155">A here-string can span multiple lines.</span></span> <span data-ttu-id="f14a9-156">Alla rader i en här-sträng tolkas som strängar även om de inte omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-156">All the lines in a here-string are interpreted as strings even though they are not enclosed in quotation marks.</span></span>

<span data-ttu-id="f14a9-157">Precis som med vanliga strängar ersätts variablerna med deras värden i dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f14a9-157">Like regular strings, variables are replaced by their values in double-quoted here-strings.</span></span> <span data-ttu-id="f14a9-158">I ensiffriga här – strängar ersätts inte variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="f14a9-158">In single-quoted here-strings, variables are not replaced by their values.</span></span>

<span data-ttu-id="f14a9-159">Du kan använda här – strängar för valfri text, men de är särskilt användbara för följande typer av text:</span><span class="sxs-lookup"><span data-stu-id="f14a9-159">You can use here-strings for any text, but they are particularly useful for the following kinds of text:</span></span>

- <span data-ttu-id="f14a9-160">Text som innehåller litterala citat tecken</span><span class="sxs-lookup"><span data-stu-id="f14a9-160">Text that contains literal quotation marks</span></span>
- <span data-ttu-id="f14a9-161">Flera rader med text, till exempel texten i en HTML-eller XML-fil</span><span class="sxs-lookup"><span data-stu-id="f14a9-161">Multiple lines of text, such as the text in an HTML or XML</span></span>
- <span data-ttu-id="f14a9-162">Hjälp texten för ett skript eller funktions dokument</span><span class="sxs-lookup"><span data-stu-id="f14a9-162">The Help text for a script or function document</span></span>

<span data-ttu-id="f14a9-163">En här-sträng kan ha något av följande format, där `<Enter>` representerar rad matnings tecken eller sid matnings tecken som läggs till när du trycker på <kbd>RETUR</kbd> -tangenten.</span><span class="sxs-lookup"><span data-stu-id="f14a9-163">A here-string can have either of the following formats, where `<Enter>` represents the linefeed or newline hidden character that is added when you press the <kbd>ENTER</kbd> key.</span></span>

<span data-ttu-id="f14a9-164">Dubbla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="f14a9-164">Double-quotes:</span></span>

```
@"<Enter>
<string> [string] ...<Enter>
"@
```

<span data-ttu-id="f14a9-165">Enkla citat tecken:</span><span class="sxs-lookup"><span data-stu-id="f14a9-165">Single-quotes:</span></span>

```
@'<Enter>
<string> [string] ...<Enter>
'@
```

<span data-ttu-id="f14a9-166">I båda formaten måste det avslutande citat tecknet vara det första tecknet på raden.</span><span class="sxs-lookup"><span data-stu-id="f14a9-166">In either format, the closing quotation mark must be the first character in the line.</span></span>

<span data-ttu-id="f14a9-167">En här-sträng innehåller all text mellan de två dolda tecknen.</span><span class="sxs-lookup"><span data-stu-id="f14a9-167">A here-string contains all the text between the two hidden characters.</span></span> <span data-ttu-id="f14a9-168">I den här strängen tolkas alla citat tecken bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="f14a9-168">In the here-string, all quotation marks are interpreted literally.</span></span> <span data-ttu-id="f14a9-169">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-169">For example:</span></span>

```powershell
@"
For help, type "get-help"
"@
```

<span data-ttu-id="f14a9-170">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-170">The output of this command is:</span></span>

```Output
For help, type "get-help"
```

<span data-ttu-id="f14a9-171">Om du använder en här-sträng kan du förenkla användningen av en sträng i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="f14a9-171">Using a here-string can simplify using a string in a command.</span></span> <span data-ttu-id="f14a9-172">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-172">For example:</span></span>

```powershell
@"
Use a quotation mark (') to begin a string.
"@
```

<span data-ttu-id="f14a9-173">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-173">The output of this command is:</span></span>

```Output
Use a quotation mark (') to begin a string.
```

<span data-ttu-id="f14a9-174">I ensiffriga här – strängar tolkas variablerna i bokstavligen och reproduceras exakt.</span><span class="sxs-lookup"><span data-stu-id="f14a9-174">In single-quoted here-strings, variables are interpreted literally and reproduced exactly.</span></span> <span data-ttu-id="f14a9-175">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-175">For example:</span></span>

```powershell
@'
The $profile variable contains the path
of your PowerShell profile.
'@
```

<span data-ttu-id="f14a9-176">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-176">The output of this command is:</span></span>

```Output
The $profile variable contains the path
of your PowerShell profile.
```

<span data-ttu-id="f14a9-177">I Double-citerade här – strängar ersätts variablerna med deras värden.</span><span class="sxs-lookup"><span data-stu-id="f14a9-177">In double-quoted here-strings, variables are replaced by their values.</span></span> <span data-ttu-id="f14a9-178">Exempel:</span><span class="sxs-lookup"><span data-stu-id="f14a9-178">For example:</span></span>

```powershell
@"
Even if you have not created a profile,
the path of the profile file is:
$profile.
"@
```

<span data-ttu-id="f14a9-179">Utdata från det här kommandot är:</span><span class="sxs-lookup"><span data-stu-id="f14a9-179">The output of this command is:</span></span>

```Output
Even if you have not created a profile,
the path of the profile file is:
C:\Users\User1\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1.
```

<span data-ttu-id="f14a9-180">Här – strängarna används vanligt vis för att tilldela flera rader till en variabel.</span><span class="sxs-lookup"><span data-stu-id="f14a9-180">Here-strings are typically used to assign multiple lines to a variable.</span></span> <span data-ttu-id="f14a9-181">Följande – sträng tilldelar till exempel en sida med XML till variabeln $page.</span><span class="sxs-lookup"><span data-stu-id="f14a9-181">For example, the following here-string assigns a page of XML to the $page variable.</span></span>

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

<span data-ttu-id="f14a9-182">Här – strängarna är också ett bekvämt format för inmatade `ConvertFrom-StringData` cmdlet, som konverterar hit-strängar till hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="f14a9-182">Here-strings are also a convenient format for input to the `ConvertFrom-StringData` cmdlet, which converts here-strings to hash tables.</span></span>
<span data-ttu-id="f14a9-183">Mer information finns i `ConvertFrom-StringData`.</span><span class="sxs-lookup"><span data-stu-id="f14a9-183">For more information, see `ConvertFrom-StringData`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f14a9-184">Se även</span><span class="sxs-lookup"><span data-stu-id="f14a9-184">See also</span></span>

[<span data-ttu-id="f14a9-185">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="f14a9-185">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="f14a9-186">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="f14a9-186">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
