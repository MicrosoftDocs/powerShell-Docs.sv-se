---
description: Beskriver reguljära uttryck i PowerShell.
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 4dc6ac670a31cbea4c35ee6540ce3368ad9b02ca
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708439"
---
# <a name="about-regular-expressions"></a><span data-ttu-id="7060b-103">Om reguljära uttryck</span><span class="sxs-lookup"><span data-stu-id="7060b-103">About Regular Expressions</span></span>

## <a name="short-description"></a><span data-ttu-id="7060b-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="7060b-104">Short description</span></span>
<span data-ttu-id="7060b-105">Beskriver reguljära uttryck i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7060b-105">Describes regular expressions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7060b-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="7060b-106">Long description</span></span>

> [!NOTE]
> <span data-ttu-id="7060b-107">Den här artikeln visar syntax och metoder för att använda reguljära uttryck i PowerShell, men all syntax diskuteras inte.</span><span class="sxs-lookup"><span data-stu-id="7060b-107">This article will show you the syntax and methods for using regular expressions in PowerShell, not all syntax is discussed.</span></span> <span data-ttu-id="7060b-108">En mer fullständig referens finns i [snabb referens för reguljära uttryck](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="7060b-108">For a more complete reference, see the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

<span data-ttu-id="7060b-109">Ett reguljärt uttryck är ett mönster som används för att matcha text.</span><span class="sxs-lookup"><span data-stu-id="7060b-109">A regular expression is a pattern used to match text.</span></span> <span data-ttu-id="7060b-110">Det kan bestå av litterala tecken, operatorer och andra konstruktioner.</span><span class="sxs-lookup"><span data-stu-id="7060b-110">It can be made up of literal characters, operators, and other constructs.</span></span>

<span data-ttu-id="7060b-111">Den här artikeln visar syntaxen för reguljära uttryck i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7060b-111">This article demonstrates regular expression syntax in PowerShell.</span></span> <span data-ttu-id="7060b-112">PowerShell har flera operatorer och cmdlets som använder reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="7060b-112">PowerShell has several operators and cmdlets that use regular expressions.</span></span> <span data-ttu-id="7060b-113">Du kan läsa mer om deras syntax och användning på länkarna nedan.</span><span class="sxs-lookup"><span data-stu-id="7060b-113">You can read more about their syntax and usage at the links below.</span></span>

- [<span data-ttu-id="7060b-114">Select-String</span><span class="sxs-lookup"><span data-stu-id="7060b-114">Select-String</span></span>](xref:Microsoft.PowerShell.Utility.Select-String)
- [<span data-ttu-id="7060b-115">– matcha och-ersätt operatörer</span><span class="sxs-lookup"><span data-stu-id="7060b-115">-match and -replace operators</span></span>](about_Comparison_Operators.md)
- [<span data-ttu-id="7060b-116">– Dela</span><span class="sxs-lookup"><span data-stu-id="7060b-116">-split</span></span>](about_Split.md)
- [<span data-ttu-id="7060b-117">Switch-instruktion med alternativet-regex</span><span class="sxs-lookup"><span data-stu-id="7060b-117">switch statement with -regex option</span></span>](about_Switch.md)

<span data-ttu-id="7060b-118">Reguljära uttryck i PowerShell är Skift läges känsliga som standard.</span><span class="sxs-lookup"><span data-stu-id="7060b-118">PowerShell regular expressions are case-insensitive by default.</span></span> <span data-ttu-id="7060b-119">Varje metod som visas ovan har ett annat sätt att framtvinga Skift läges känslighet.</span><span class="sxs-lookup"><span data-stu-id="7060b-119">Each method shown above has a different way to force case sensitivity.</span></span>

|       <span data-ttu-id="7060b-120">Metod</span><span class="sxs-lookup"><span data-stu-id="7060b-120">Method</span></span>       |                      <span data-ttu-id="7060b-121">Skift läges känslighet</span><span class="sxs-lookup"><span data-stu-id="7060b-121">Case Sensitivity</span></span>                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | <span data-ttu-id="7060b-122">Använd `-CaseSensitive` switch</span><span class="sxs-lookup"><span data-stu-id="7060b-122">use `-CaseSensitive` switch</span></span>                                |
| <span data-ttu-id="7060b-123">`switch` Sekretesspolicy</span><span class="sxs-lookup"><span data-stu-id="7060b-123">`switch` statement</span></span> | <span data-ttu-id="7060b-124">Använd `-casesensitive` alternativet</span><span class="sxs-lookup"><span data-stu-id="7060b-124">use the `-casesensitive` option</span></span>                            |
| <span data-ttu-id="7060b-125">operatorer</span><span class="sxs-lookup"><span data-stu-id="7060b-125">operators</span></span>          | <span data-ttu-id="7060b-126">prefix med **"c"** ( `-cmatch` , `-csplit` eller `-creplace` )</span><span class="sxs-lookup"><span data-stu-id="7060b-126">prefix with **'c'** (`-cmatch`, `-csplit`, or `-creplace`)</span></span> |

### <a name="character-literals"></a><span data-ttu-id="7060b-127">Tecken strängar</span><span class="sxs-lookup"><span data-stu-id="7060b-127">Character literals</span></span>

<span data-ttu-id="7060b-128">Ett reguljärt uttryck kan vara ett tecken eller en sträng.</span><span class="sxs-lookup"><span data-stu-id="7060b-128">A regular expression can be a literal character or a string.</span></span> <span data-ttu-id="7060b-129">Uttrycket gör att motorn matchar texten som anges exakt.</span><span class="sxs-lookup"><span data-stu-id="7060b-129">The expression causes the engine to match the text specified exactly.</span></span>

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a><span data-ttu-id="7060b-130">Character-klasser</span><span class="sxs-lookup"><span data-stu-id="7060b-130">Character classes</span></span>

<span data-ttu-id="7060b-131">Tecken strängar fungerar om du känner till det exakta mönstret, men med tecken klasser kan du vara mindre specifika.</span><span class="sxs-lookup"><span data-stu-id="7060b-131">While character literals work if you know the exact pattern, character classes allow you to be less specific.</span></span>

#### <a name="character-groups"></a><span data-ttu-id="7060b-132">Character-grupper</span><span class="sxs-lookup"><span data-stu-id="7060b-132">Character groups</span></span>

<span data-ttu-id="7060b-133">`[character group]` gör att du kan matcha valfritt antal tecken en enda stund och `[^character group]` bara matcha tecken som inte finns i gruppen.</span><span class="sxs-lookup"><span data-stu-id="7060b-133">`[character group]` allows you to match any number of characters one time, while `[^character group]` only matches characters NOT in the group.</span></span>

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

<span data-ttu-id="7060b-134">Om listan över tecken som ska matchas innehåller bindestreck ( `-` ) måste den finnas i början eller slutet av listan för att skilja den från ett tecken intervall uttryck.</span><span class="sxs-lookup"><span data-stu-id="7060b-134">If your list of characters to match includes the hyphen character (`-`), it must be at the beginning or end of the list to distinguish it from a character range expression.</span></span>

#### <a name="character-ranges"></a><span data-ttu-id="7060b-135">Character-intervall</span><span class="sxs-lookup"><span data-stu-id="7060b-135">Character ranges</span></span>

<span data-ttu-id="7060b-136">Ett mönster kan också vara ett tecken intervall.</span><span class="sxs-lookup"><span data-stu-id="7060b-136">A pattern can also be a range of characters.</span></span> <span data-ttu-id="7060b-137">Tecknen kan vara alfabetiska `[A-Z]` , numeriska `[0-9]` eller jämna ASCII-baserade `[ -~]` (alla tecken som kan skrivas ut).</span><span class="sxs-lookup"><span data-stu-id="7060b-137">The characters can be alphabetic `[A-Z]`, numeric `[0-9]`, or even ASCII-based `[ -~]` (all printable characters).</span></span>

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a><span data-ttu-id="7060b-138">Tal</span><span class="sxs-lookup"><span data-stu-id="7060b-138">Numbers</span></span>

<span data-ttu-id="7060b-139">`\d`Tecken klassen matchar alla decimal siffror.</span><span class="sxs-lookup"><span data-stu-id="7060b-139">The `\d` character class will match any decimal digit.</span></span> <span data-ttu-id="7060b-140">Omvänt `\D` kommer att matcha alla siffror som inte är decimaler.</span><span class="sxs-lookup"><span data-stu-id="7060b-140">Conversely, `\D` will match any non-decimal digit.</span></span>

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a><span data-ttu-id="7060b-141">Ord tecken</span><span class="sxs-lookup"><span data-stu-id="7060b-141">Word characters</span></span>

<span data-ttu-id="7060b-142">`\w`Klassen Character matchar valfritt ord `[a-zA-Z_0-9]` .</span><span class="sxs-lookup"><span data-stu-id="7060b-142">The `\w` character class will match any word character `[a-zA-Z_0-9]`.</span></span> <span data-ttu-id="7060b-143">Använd om du vill matcha ord som inte är ord `\W` .</span><span class="sxs-lookup"><span data-stu-id="7060b-143">To match any non-word character, use `\W`.</span></span>

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a><span data-ttu-id="7060b-144">Jokertecken</span><span class="sxs-lookup"><span data-stu-id="7060b-144">Wildcards</span></span>

<span data-ttu-id="7060b-145">Punkten ( `.` ) är ett jokertecken i reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="7060b-145">The period (`.`) is a wildcard character in regular expressions.</span></span> <span data-ttu-id="7060b-146">Det matchar alla bokstäver utom en ny rad ( `\n` ).</span><span class="sxs-lookup"><span data-stu-id="7060b-146">It will match any character except a newline (`\n`).</span></span>

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a><span data-ttu-id="7060b-147">Blanksteg</span><span class="sxs-lookup"><span data-stu-id="7060b-147">Whitespace</span></span>

<span data-ttu-id="7060b-148">Blank steg matchas med `\s` klassen Character.</span><span class="sxs-lookup"><span data-stu-id="7060b-148">Whitespace is matched using the `\s` character class.</span></span> <span data-ttu-id="7060b-149">Tecken som inte är blank steg matchas med `\S` .</span><span class="sxs-lookup"><span data-stu-id="7060b-149">Any non-whitespace character is matched using `\S`.</span></span> <span data-ttu-id="7060b-150">Tecken för tecken avstånd `' '` kan också användas.</span><span class="sxs-lookup"><span data-stu-id="7060b-150">Literal space characters `' '` can also be used.</span></span>

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a><span data-ttu-id="7060b-151">Kvantifierare</span><span class="sxs-lookup"><span data-stu-id="7060b-151">Quantifiers</span></span>

<span data-ttu-id="7060b-152">Kvantifierare styr hur många instanser av varje element som ska finnas i Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="7060b-152">Quantifiers control how many instances of each element should be present in the input string.</span></span>

<span data-ttu-id="7060b-153">Följande är några av de kvantifierare som är tillgängliga i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7060b-153">The following are a few of the quantifiers available in PowerShell:</span></span>

| <span data-ttu-id="7060b-154">Kvantifieraren</span><span class="sxs-lookup"><span data-stu-id="7060b-154">Quantifier</span></span> |                <span data-ttu-id="7060b-155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7060b-155">Description</span></span>                |
| ---------- | ----------------------------------------- |
| `*`        | <span data-ttu-id="7060b-156">Noll eller flera gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-156">Zero or more times.</span></span>                       |
| `+`        | <span data-ttu-id="7060b-157">En eller flera gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-157">One or more times.</span></span>                        |
| `?`        | <span data-ttu-id="7060b-158">Noll eller en tid.</span><span class="sxs-lookup"><span data-stu-id="7060b-158">Zero or one time.</span></span>                         |
| `{n,m}`    | <span data-ttu-id="7060b-159">Minst `n` , men inte mer än `m` gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-159">At least `n`, but no more than `m` times.</span></span> |

<span data-ttu-id="7060b-160">Asterisken ( `*` ) matchar föregående element noll eller flera gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-160">The asterisk (`*`) matches the previous element zero or more times.</span></span> <span data-ttu-id="7060b-161">Resultatet är att även en indatasträng utan element skulle vara en matchning.</span><span class="sxs-lookup"><span data-stu-id="7060b-161">The result is that even an input string without the element would be a match.</span></span>

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

<span data-ttu-id="7060b-162">Plus tecknet ( `+` ) matchar det föregående elementet en eller flera gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-162">The plus sign (`+`) matches the previous element one or more times.</span></span>

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

<span data-ttu-id="7060b-163">Frågetecknet `?` matchar föregående element noll eller en tid.</span><span class="sxs-lookup"><span data-stu-id="7060b-163">The question mark `?` matches the previous element zero or one time.</span></span> <span data-ttu-id="7060b-164">Precis som asterisk `*` , matchar den även strängar där elementet saknas.</span><span class="sxs-lookup"><span data-stu-id="7060b-164">Like asterisk `*`, it will even match strings where the element is absent.</span></span>

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

<span data-ttu-id="7060b-165">`{n, m}`Kvantifieraren kan användas på flera olika sätt för att tillåta detaljerad kontroll över Kvantifieraren.</span><span class="sxs-lookup"><span data-stu-id="7060b-165">The `{n, m}` quantifier can be used several different ways to allow granular control over the quantifier.</span></span> <span data-ttu-id="7060b-166">Det andra elementet `m` och kommatecken `,` är valfria.</span><span class="sxs-lookup"><span data-stu-id="7060b-166">The second element `m` and the comma `,` are optional.</span></span>

| <span data-ttu-id="7060b-167">Kvantifieraren</span><span class="sxs-lookup"><span data-stu-id="7060b-167">Quantifier</span></span> |                <span data-ttu-id="7060b-168">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7060b-168">Description</span></span>                 |
| ---------- | ------------------------------------------ |
| `{n}`      | <span data-ttu-id="7060b-169">Matcha exakt `n` antal gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-169">Match EXACTLY `n` number of times.</span></span>         |
| `{n,}`     | <span data-ttu-id="7060b-170">Matcha minst `n` antal gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-170">Match at LEAST `n` number of times.</span></span>        |
| `{n,m}`    | <span data-ttu-id="7060b-171">Matcha mellan `n` och `m` antal gånger.</span><span class="sxs-lookup"><span data-stu-id="7060b-171">Match between `n` and `m` number of times.</span></span> |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a><span data-ttu-id="7060b-172">Ankare</span><span class="sxs-lookup"><span data-stu-id="7060b-172">Anchors</span></span>

<span data-ttu-id="7060b-173">Med ankare kan du göra så att en matchning lyckas eller Miss lyckas baserat på matchnings positionen i Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="7060b-173">Anchors allow you to cause a match to succeed or fail based on the matches position within the input string.</span></span>

<span data-ttu-id="7060b-174">De två ofta använda ankarena är `^` och `$` .</span><span class="sxs-lookup"><span data-stu-id="7060b-174">The two commonly used anchors are `^` and `$`.</span></span> <span data-ttu-id="7060b-175">Cirkumflexet `^` matchar början av en sträng och `$` , som matchar slutet på en sträng.</span><span class="sxs-lookup"><span data-stu-id="7060b-175">The caret `^` matches the start of a string, and `$`, which matches the end of a string.</span></span> <span data-ttu-id="7060b-176">Med ankarena kan du matcha din text vid en speciell position medan du också tar bort oönskade tecken.</span><span class="sxs-lookup"><span data-stu-id="7060b-176">The anchors allow you to match your text at a specific position while also discarding unwanted characters.</span></span>

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> <span data-ttu-id="7060b-177">När du definierar ett regex som innehåller ett `$` ankare måste du omsluta regex med enkla citat tecken ( `'` ) i stället för dubbla citat tecken ( `"` ) eller PowerShell för att expandera uttrycket som en variabel.</span><span class="sxs-lookup"><span data-stu-id="7060b-177">When defining a regex containing an `$` anchor, be sure to enclose the regex using single quotes (`'`) instead of double quotes (`"`) or PowerShell will expand the expression as a variable.</span></span>

<span data-ttu-id="7060b-178">När du använder ankare i PowerShell bör du förstå skillnaden mellan **Singleline** och alternativ för reguljära uttryck i **flera rader** .</span><span class="sxs-lookup"><span data-stu-id="7060b-178">When using anchors in PowerShell, you should understand the difference between **Singleline** and **Multiline** regular expression options.</span></span>

- <span data-ttu-id="7060b-179">Flera **rader**: Multiline-läge tvingar fram `^` och `$` matchar början av varje rad i stället för början och slutet av Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="7060b-179">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every LINE instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="7060b-180">**Singleline**: Singleline mode behandlar Indatasträngen som en **Singleline**.</span><span class="sxs-lookup"><span data-stu-id="7060b-180">**Singleline**: Singleline mode treats the input string as a **SingleLine**.</span></span>
  <span data-ttu-id="7060b-181">Det tvingar `.` tecknet att matcha varje Character (inklusive newlines), i stället för att matcha alla bokstäver förutom rad matningen `\n` .</span><span class="sxs-lookup"><span data-stu-id="7060b-181">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>

<span data-ttu-id="7060b-182">Om du vill läsa mer om de här alternativen och hur du använder dem går du till [snabb referens för det reguljära uttrycks språket](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span><span class="sxs-lookup"><span data-stu-id="7060b-182">To read more about these options and how to use them, visit the [Regular Expression Language - Quick Reference](/dotnet/standard/base-types/regular-expression-language-quick-reference).</span></span>

### <a name="escaping-characters"></a><span data-ttu-id="7060b-183">Undantagna tecken</span><span class="sxs-lookup"><span data-stu-id="7060b-183">Escaping characters</span></span>

<span data-ttu-id="7060b-184">Omvänt snedstreck ( `\` ) används för att undanta tecken så att de inte tolkas av motorn för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="7060b-184">The backslash (`\`) is used to escape characters so they aren't parsed by the regular expression engine.</span></span>

<span data-ttu-id="7060b-185">Följande tecken är reserverade: `[]().\^$|?*+{}` .</span><span class="sxs-lookup"><span data-stu-id="7060b-185">The following characters are reserved: `[]().\^$|?*+{}`.</span></span>

<span data-ttu-id="7060b-186">Du måste undanta dessa tecken i mönstren för att matcha dem i dina indatatyper.</span><span class="sxs-lookup"><span data-stu-id="7060b-186">You'll need to escape these characters in your patterns to match them in your input strings.</span></span>

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

<span data-ttu-id="7060b-187">Det finns en statisk metod för regex-klassen som kan kringgå text åt dig.</span><span class="sxs-lookup"><span data-stu-id="7060b-187">There\`s a static method of the regex class that can escape text for you.</span></span>

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> <span data-ttu-id="7060b-188">Detta utrymningr alla reserverade tecken i reguljära uttryck, inklusive befintliga omvända snedstreck som används i tecken klasser.</span><span class="sxs-lookup"><span data-stu-id="7060b-188">This escapes all reserved regular expression characters, including existing backslashes used in character classes.</span></span> <span data-ttu-id="7060b-189">Se till att du bara använder den i den del av ditt mönster som du behöver undanta.</span><span class="sxs-lookup"><span data-stu-id="7060b-189">Be sure to only use it on the portion of your pattern that you need to escape.</span></span>

#### <a name="other-character-escapes"></a><span data-ttu-id="7060b-190">Andra tecken Escape</span><span class="sxs-lookup"><span data-stu-id="7060b-190">Other character escapes</span></span>

<span data-ttu-id="7060b-191">Det finns också reserverade escape-tecken som du kan använda för att matcha särskilda tecken typer.</span><span class="sxs-lookup"><span data-stu-id="7060b-191">There are also reserved character escapes that you can use to match special character types.</span></span>

<span data-ttu-id="7060b-192">Här följer några vanliga escape-tecken:</span><span class="sxs-lookup"><span data-stu-id="7060b-192">The following are a few commonly used character escapes:</span></span>

|<span data-ttu-id="7060b-193">Tecken Escape</span><span class="sxs-lookup"><span data-stu-id="7060b-193">Character Escape</span></span>  |<span data-ttu-id="7060b-194">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7060b-194">Description</span></span>  |
|---------|---------|
|`\t`|<span data-ttu-id="7060b-195">Matchar en flik</span><span class="sxs-lookup"><span data-stu-id="7060b-195">Matches a tab</span></span>|
|`\n`|<span data-ttu-id="7060b-196">Matchar en ny rad</span><span class="sxs-lookup"><span data-stu-id="7060b-196">Matches a newline</span></span>|
|`\r`|<span data-ttu-id="7060b-197">Matchar en vagn retur</span><span class="sxs-lookup"><span data-stu-id="7060b-197">Matches a carriage return</span></span>|

### <a name="groups-captures-and-substitutions"></a><span data-ttu-id="7060b-198">Grupper, avbildningar och ersättningar</span><span class="sxs-lookup"><span data-stu-id="7060b-198">Groups, Captures, and Substitutions</span></span>

<span data-ttu-id="7060b-199">Gruppering av konstruktion separerar en indatasträng i del strängar som kan fångas eller ignoreras.</span><span class="sxs-lookup"><span data-stu-id="7060b-199">Grouping constructs separate an input string into substrings that can be captured or ignored.</span></span> <span data-ttu-id="7060b-200">Grupperade del strängar kallas under uttryck.</span><span class="sxs-lookup"><span data-stu-id="7060b-200">Grouped substrings are called subexpressions.</span></span> <span data-ttu-id="7060b-201">Som standard registreras under uttryck i numrerade grupper, men du kan även tilldela dem namn.</span><span class="sxs-lookup"><span data-stu-id="7060b-201">By default subexpressions are captured in numbered groups, though you can assign names to them as well.</span></span>

<span data-ttu-id="7060b-202">En grupperings-konstruktion är ett reguljärt uttryck som omges av parenteser.</span><span class="sxs-lookup"><span data-stu-id="7060b-202">A grouping construct is a regular expression surrounded by parentheses.</span></span> <span data-ttu-id="7060b-203">All text som matchas av det omslutna reguljära uttrycket fångas.</span><span class="sxs-lookup"><span data-stu-id="7060b-203">Any text matched by the enclosed regular expression is captured.</span></span> <span data-ttu-id="7060b-204">I följande exempel bryts inmatad text i två hämtade grupper.</span><span class="sxs-lookup"><span data-stu-id="7060b-204">The following example will break the input text into two capturing groups.</span></span>

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

<span data-ttu-id="7060b-205">Använd den `$Matches` automatiska variabeln **hash** för att hämta insamlad text.</span><span class="sxs-lookup"><span data-stu-id="7060b-205">Use the `$Matches` **Hashtable** automatic variable to retrieve captured text.</span></span>
<span data-ttu-id="7060b-206">Texten som representerar hela matchningen lagras i nyckeln `0` .</span><span class="sxs-lookup"><span data-stu-id="7060b-206">The text representing the entire match is stored at key `0`.</span></span>

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

<span data-ttu-id="7060b-207">Avbildningar lagras i numeriska **heltals** nycklar som ökar från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="7060b-207">Captures are stored in numeric **Integer** keys that increase from left to right.</span></span> <span data-ttu-id="7060b-208">Capture `1` innehåller all text tills användar namnet, avbildningen `2` innehåller bara användar namnet.</span><span class="sxs-lookup"><span data-stu-id="7060b-208">Capture `1` contains all the text until the username, capture `2` contains just the username.</span></span>

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> <span data-ttu-id="7060b-209">`0`Nyckeln är ett **heltal**.</span><span class="sxs-lookup"><span data-stu-id="7060b-209">The `0` key is an **Integer**.</span></span> <span data-ttu-id="7060b-210">Du kan använda valfri **hash** -Metod för att komma åt värdet som lagras.</span><span class="sxs-lookup"><span data-stu-id="7060b-210">You can use any **Hashtable** method to access the value stored.</span></span>
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a><span data-ttu-id="7060b-211">Namngivna insamlingar</span><span class="sxs-lookup"><span data-stu-id="7060b-211">Named Captures</span></span>

<span data-ttu-id="7060b-212">Som standard lagras avbildningar i stigande numerisk ordning, från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="7060b-212">By default, captures are stored in ascending numeric order, from left to right.</span></span>
<span data-ttu-id="7060b-213">Du kan också tilldela ett **namn** till en samlad grupp.</span><span class="sxs-lookup"><span data-stu-id="7060b-213">You can also assign a **name** to a capturing group.</span></span> <span data-ttu-id="7060b-214">Det här **namnet** blir en nyckel på den `$Matches` automatiska variabeln **hash** .</span><span class="sxs-lookup"><span data-stu-id="7060b-214">This **name** becomes a key on the `$Matches` **Hashtable** automatic variable.</span></span>

<span data-ttu-id="7060b-215">I en insamlings grupp använder `?<keyname>` du för att lagra insamlade data under en namngiven nyckel.</span><span class="sxs-lookup"><span data-stu-id="7060b-215">Inside a capturing group, use `?<keyname>` to store captured data under a named key.</span></span>

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

<span data-ttu-id="7060b-216">I följande exempel lagras den senaste logg posten i säkerhets loggen i Windows.</span><span class="sxs-lookup"><span data-stu-id="7060b-216">The following example stores the newest log entry in the Windows Security Log.</span></span>
<span data-ttu-id="7060b-217">Det angivna reguljära uttrycket extraherar användar namnet och domänen från meddelandet och lagrar dem under nycklarna:**N** för namn och **D** för domän.</span><span class="sxs-lookup"><span data-stu-id="7060b-217">The provided regular expression extracts the username and domain from the message and stores them under the keys:**N** for name and **D** for domain.</span></span>

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

<span data-ttu-id="7060b-218">Mer information finns i [gruppera konstruktioner i reguljära uttryck](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span><span class="sxs-lookup"><span data-stu-id="7060b-218">For more information, see [Grouping Constructs in Regular Expressions](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).</span></span>

#### <a name="substitutions-in-regular-expressions"></a><span data-ttu-id="7060b-219">Ersättningar i reguljära uttryck</span><span class="sxs-lookup"><span data-stu-id="7060b-219">Substitutions in Regular Expressions</span></span>

<span data-ttu-id="7060b-220">Med hjälp av de reguljära uttrycken med `-replace` operatorn kan du ersätta text dynamiskt med hjälp av insamlad text.</span><span class="sxs-lookup"><span data-stu-id="7060b-220">Using the regular expressions with the `-replace` operator allows you to dynamically replace text using captured text.</span></span>

`<input> -replace <original>, <substitute>`

- <span data-ttu-id="7060b-221">`<input>`: Strängen som ska genomsökas</span><span class="sxs-lookup"><span data-stu-id="7060b-221">`<input>`: The string to be searched</span></span>
- <span data-ttu-id="7060b-222">`<original>`: Ett reguljärt uttryck som används för att söka i Indatasträngen</span><span class="sxs-lookup"><span data-stu-id="7060b-222">`<original>`: A regular expression used to search the input string</span></span>
- <span data-ttu-id="7060b-223">`<substitute>`: Ett uttryck för vanlig uttrycks ersättning som ersätter matchningar som finns i Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="7060b-223">`<substitute>`: A regular expression substitution expression to replace matches found in the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="7060b-224">`<original>` `<substitute>` Operanderna och omfattas av regler för den reguljära uttrycks motorn, till exempel tecken undantag.</span><span class="sxs-lookup"><span data-stu-id="7060b-224">The `<original>` and `<substitute>` operands are subject to rules of the regular expression engine such as character escaping.</span></span>

<span data-ttu-id="7060b-225">Det går att referera till hämtade grupper i `<substitute>` strängen.</span><span class="sxs-lookup"><span data-stu-id="7060b-225">Capturing groups can be referenced in the `<substitute>` string.</span></span> <span data-ttu-id="7060b-226">Ersättningen görs med hjälp av ett `$` tecken före grupp-ID: n.</span><span class="sxs-lookup"><span data-stu-id="7060b-226">The substitution is done by using the `$` character before the group identifier.</span></span>

<span data-ttu-id="7060b-227">Det finns två sätt att referera till infångade grupper med hjälp av **nummer** och efter **namn**.</span><span class="sxs-lookup"><span data-stu-id="7060b-227">Two ways to reference capturing groups are by **Number** and by **Name**.</span></span>

- <span data-ttu-id="7060b-228">Per **nummer** – fångar grupper numreras från vänster till höger.</span><span class="sxs-lookup"><span data-stu-id="7060b-228">By **Number** - Capturing Groups are numbered from left to right.</span></span>

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- <span data-ttu-id="7060b-229">Efter **namn** -hämtade grupper kan också refereras till med hjälp av namn.</span><span class="sxs-lookup"><span data-stu-id="7060b-229">By **Name** - Capturing Groups can also be referenced by name.</span></span>

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

<span data-ttu-id="7060b-230">`$&`Uttrycket representerar all matchad text.</span><span class="sxs-lookup"><span data-stu-id="7060b-230">The `$&` expression represents all the text matched.</span></span>

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> <span data-ttu-id="7060b-231">Eftersom det `$` används i sträng expansion måste du använda litterala strängar med ersättning eller Escape- `$` tecken när du använder dubbla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="7060b-231">Since the `$` character is used in string expansion, you'll need to use literal strings with substitution, or escape the `$` character when using double quotes.</span></span>
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> <span data-ttu-id="7060b-232">Om du vill `$` använda som ett litteralt tecken ska du använda `$$` i stället för vanliga escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="7060b-232">Additionally, if you want to have the `$` as a literal character, use `$$` instead of the normal escape characters.</span></span> <span data-ttu-id="7060b-233">När du använder dubbla citat tecken kan du fortfarande kringgå alla instanser av `$` för att undvika felaktig ersättning.</span><span class="sxs-lookup"><span data-stu-id="7060b-233">When using double quotes, still escape all instances of `$` to avoid incorrect substitution.</span></span>
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

<span data-ttu-id="7060b-234">Mer information finns i [ersättningar i reguljära uttryck](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span><span class="sxs-lookup"><span data-stu-id="7060b-234">For more information, see [Substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).</span></span>

## <a name="see-also"></a><span data-ttu-id="7060b-235">Se även</span><span class="sxs-lookup"><span data-stu-id="7060b-235">See also</span></span>

[<span data-ttu-id="7060b-236">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="7060b-236">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="7060b-237">about_Operators</span><span class="sxs-lookup"><span data-stu-id="7060b-237">about_Operators</span></span>](about_Operators.md)

