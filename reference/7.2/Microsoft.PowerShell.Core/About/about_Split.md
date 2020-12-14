---
description: Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.
Locale: en-US
ms.date: 03/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: c7944c710ae3b6803772de77f50b639de4953340
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710921"
---
# <a name="about-split"></a><span data-ttu-id="759a0-103">Om delning</span><span class="sxs-lookup"><span data-stu-id="759a0-103">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="759a0-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="759a0-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="759a0-105">Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-105">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="759a0-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="759a0-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="759a0-107">Operatorn Split delar en eller flera strängar i del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-107">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="759a0-108">Du kan ändra följande delar av delnings åtgärden:</span><span class="sxs-lookup"><span data-stu-id="759a0-108">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="759a0-109">Avgränsare.</span><span class="sxs-lookup"><span data-stu-id="759a0-109">Delimiter.</span></span> <span data-ttu-id="759a0-110">Standardvärdet är blank steg, men du kan ange tecken, strängar, mönster eller skript block som anger avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-110">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="759a0-111">Operatorn Split i PowerShell använder ett reguljärt uttryck i avgränsaren i stället för ett enkelt tecken.</span><span class="sxs-lookup"><span data-stu-id="759a0-111">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="759a0-112">Maximalt antal del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-112">Maximum number of substrings.</span></span> <span data-ttu-id="759a0-113">Standardvärdet är att returnera alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-113">The default is to return all substrings.</span></span> <span data-ttu-id="759a0-114">Om du anger ett tal som är mindre än antalet under strängar sammanfogas de återstående del strängarna i den sista del strängen.</span><span class="sxs-lookup"><span data-stu-id="759a0-114">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="759a0-115">Alternativ som anger de villkor under vilka avgränsaren matchas, till exempel SimpleMatch och Multiline.</span><span class="sxs-lookup"><span data-stu-id="759a0-115">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="759a0-116">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="759a0-116">SYNTAX</span></span>

<span data-ttu-id="759a0-117">Följande diagram visar syntaxen för operatorn-Split.</span><span class="sxs-lookup"><span data-stu-id="759a0-117">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="759a0-118">Parameter namnen visas inte i kommandot.</span><span class="sxs-lookup"><span data-stu-id="759a0-118">The parameter names do not appear in the command.</span></span> <span data-ttu-id="759a0-119">Inkludera endast parameter värden.</span><span class="sxs-lookup"><span data-stu-id="759a0-119">Include only the parameter values.</span></span> <span data-ttu-id="759a0-120">Värdena måste visas i den ordning som anges i syntax-diagrammet.</span><span class="sxs-lookup"><span data-stu-id="759a0-120">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="759a0-121">Du kan ersätta `-iSplit` eller `-cSplit` för `-split` i en binär delnings instruktion (en delad instruktion som innehåller en avgränsare eller ett skript block).</span><span class="sxs-lookup"><span data-stu-id="759a0-121">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="759a0-122">`-iSplit` `-split` Operatorerna och är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="759a0-122">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="759a0-123">`-cSplit`Operatorn är Skift läges känslig, vilket innebär att ärendet beaktas när reglerna för avgränsare används.</span><span class="sxs-lookup"><span data-stu-id="759a0-123">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="759a0-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="759a0-124">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="759a0-125">\<String\> eller \<String[]\></span><span class="sxs-lookup"><span data-stu-id="759a0-125">\<String\> or \<String[]\></span></span>

<span data-ttu-id="759a0-126">Anger en eller flera strängar som ska delas upp.</span><span class="sxs-lookup"><span data-stu-id="759a0-126">Specifies one or more strings to be split.</span></span> <span data-ttu-id="759a0-127">Om du skickar flera strängar delas alla strängar med samma regler för avgränsare.</span><span class="sxs-lookup"><span data-stu-id="759a0-127">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="759a0-128">Exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-128">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="759a0-129">De tecken som identifierar slutet av en under sträng.</span><span class="sxs-lookup"><span data-stu-id="759a0-129">The characters that identify the end of a substring.</span></span> <span data-ttu-id="759a0-130">Standard avgränsaren är blank steg, inklusive blank steg och tecken som inte kan skrivas ut, till exempel ny rad matning ( \` n) och TABB ( \` t).</span><span class="sxs-lookup"><span data-stu-id="759a0-130">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="759a0-131">När strängarna delas, utelämnas avgränsaren från alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-131">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="759a0-132">Exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-132">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="759a0-133">Som standard utelämnas avgränsaren från resultaten.</span><span class="sxs-lookup"><span data-stu-id="759a0-133">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="759a0-134">Om du vill bevara hela eller delar av avgränsaren omger du den del som du vill behålla.</span><span class="sxs-lookup"><span data-stu-id="759a0-134">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="759a0-135">Om \<Max-substrings\> parametern läggs till, prioriteras det när kommandot delar upp samlingen.</span><span class="sxs-lookup"><span data-stu-id="759a0-135">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="759a0-136">Om du väljer att ta med en avgränsare som en del av utdata returnerar kommandot avgränsaren som en del av utdata. men att dela strängen för att returnera avgränsaren som en del av utdata räknas inte som en delning.</span><span class="sxs-lookup"><span data-stu-id="759a0-136">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="759a0-137">Exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-137">Examples:</span></span>

```
"Lastname:FirstName:Address" -split "(:)"
Lastname
:
FirstName
:
Address

"Lastname/:/FirstName/:/Address" -split "/(:)/"
Lastname
:
FirstName
:
Address
```

<span data-ttu-id="759a0-138">I följande exempel \<Max-substrings\> är värdet 3.</span><span class="sxs-lookup"><span data-stu-id="759a0-138">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="759a0-139">Detta resulterar i tre delar av sträng värden, men totalt fem strängar i resultatet. avgränsaren ingår efter delningarna tills det maximala antalet under strängar har nåtts.</span><span class="sxs-lookup"><span data-stu-id="759a0-139">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="759a0-140">Ytterligare avgränsare i den sista del strängen blir del av under strängen.</span><span class="sxs-lookup"><span data-stu-id="759a0-140">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```Output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="759a0-141">Anger det maximala antalet gånger som en sträng är delad.</span><span class="sxs-lookup"><span data-stu-id="759a0-141">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="759a0-142">Standardvärdet är alla del strängar som delas av avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-142">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="759a0-143">Om det finns fler del strängar sammanfogas de till den slutliga del strängen.</span><span class="sxs-lookup"><span data-stu-id="759a0-143">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="759a0-144">Om det finns färre del strängar returneras alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-144">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="759a0-145">Värdet 0 returnerar alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-145">A value of 0 returns all the substrings.</span></span> <span data-ttu-id="759a0-146">Negativa värden returnerar mängden del strängar som begärs från slutet av Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="759a0-146">Negative values return the amount of substrings requested starting from the end of the input string.</span></span>

> [!NOTE]
> <span data-ttu-id="759a0-147">Stöd för negativa värden har lagts till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="759a0-147">Support for negative values was added in PowerShell 7.</span></span>

<span data-ttu-id="759a0-148">**Max-delsträngar** anger inte det maximala antalet objekt som returneras.</span><span class="sxs-lookup"><span data-stu-id="759a0-148">**Max-substrings** does not specify the maximum number of objects that are returned.</span></span> <span data-ttu-id="759a0-149">Värdet är lika med det maximala antalet gånger som en sträng är delad.</span><span class="sxs-lookup"><span data-stu-id="759a0-149">Its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="759a0-150">Om du skickar mer än en sträng (en sträng mat ris) till `-split` operatorn, används **Max-substring-** gränsen på varje sträng separat.</span><span class="sxs-lookup"><span data-stu-id="759a0-150">If you submit more than one string (an array of strings) to the `-split` operator, the **Max-substrings** limit is applied to each string separately.</span></span>

<span data-ttu-id="759a0-151">Exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-151">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```Output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", -5
```

```Output
Mercury,Venus,Earth,Mars
Jupiter
Saturn
Uranus
Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="759a0-152">Ett uttryck som anger regler för att tillämpa avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-152">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="759a0-153">Uttrycket måste utvärderas till $true eller $false.</span><span class="sxs-lookup"><span data-stu-id="759a0-153">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="759a0-154">Omge skript blocket med klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="759a0-154">Enclose the script block in braces.</span></span>

<span data-ttu-id="759a0-155">Exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-155">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```Output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="759a0-156">Omge alternativets namn inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="759a0-156">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="759a0-157">Alternativen är endast giltiga när \<Max-substrings\> parametern används i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="759a0-157">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="759a0-158">Syntaxen för parametern options är:</span><span class="sxs-lookup"><span data-stu-id="759a0-158">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="759a0-159">Alternativen för SimpleMatch är:</span><span class="sxs-lookup"><span data-stu-id="759a0-159">The SimpleMatch options are:</span></span>

- <span data-ttu-id="759a0-160">**SimpleMatch**: Använd enkel sträng jämförelse när du utvärderar avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-160">**SimpleMatch**: Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="759a0-161">Kan inte användas med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="759a0-161">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="759a0-162">**IgnoreCase**: tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.</span><span class="sxs-lookup"><span data-stu-id="759a0-162">**IgnoreCase**: Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="759a0-163">Alternativen för RegexMatch är:</span><span class="sxs-lookup"><span data-stu-id="759a0-163">The RegexMatch options are:</span></span>

- <span data-ttu-id="759a0-164">**RegexMatch**: Använd reguljär uttrycks matchning för att utvärdera avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-164">**RegexMatch**: Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="759a0-165">Det här är standardbeteendet.</span><span class="sxs-lookup"><span data-stu-id="759a0-165">This is the default behavior.</span></span> <span data-ttu-id="759a0-166">Kan inte användas med SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="759a0-166">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="759a0-167">**IgnoreCase**: tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.</span><span class="sxs-lookup"><span data-stu-id="759a0-167">**IgnoreCase**: Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="759a0-168">**CultureInvariant**: ignorerar kultur skillnader i språk när evaluting avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-168">**CultureInvariant**: Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="759a0-169">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="759a0-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="759a0-170">**IgnorePatternWhitespace**: ignorerar ej Escaped blank steg och kommentarer som marker ATS med nummer tecknet (#).</span><span class="sxs-lookup"><span data-stu-id="759a0-170">**IgnorePatternWhitespace**: Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="759a0-171">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="759a0-171">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="759a0-172">Flera **rader**: Multiline-läge tvingar fram `^` och `$` matchar början av varje rad i stället för början och slutet av Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="759a0-172">**Multiline**: Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="759a0-173">**Singleline**: Singleline mode behandlar Indatasträngen som en *Singleline*.</span><span class="sxs-lookup"><span data-stu-id="759a0-173">**Singleline**: Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="759a0-174">Det tvingar `.` tecknet att matcha varje Character (inklusive newlines), i stället för att matcha alla bokstäver förutom rad matningen `\n` .</span><span class="sxs-lookup"><span data-stu-id="759a0-174">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="759a0-175">**ExplicitCapture**: ignorerar matchnings grupper som inte är namngivna så att endast explicita infångnings grupper returneras i resultat listan.</span><span class="sxs-lookup"><span data-stu-id="759a0-175">**ExplicitCapture**: Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="759a0-176">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="759a0-176">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="759a0-177">UNÄRA och binära delade OPERATORer</span><span class="sxs-lookup"><span data-stu-id="759a0-177">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="759a0-178">Den unära delnings operatorn ( `-split <string>` ) har högre prioritet än ett kommatecken.</span><span class="sxs-lookup"><span data-stu-id="759a0-178">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="759a0-179">Det innebär att om du skickar en kommaavgränsad lista med strängar till den unära delnings operatorn, är det bara den första strängen (före det första kommatecknet) som delas.</span><span class="sxs-lookup"><span data-stu-id="759a0-179">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="759a0-180">Använd något av följande mönster för att dela fler än en sträng:</span><span class="sxs-lookup"><span data-stu-id="759a0-180">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="759a0-181">Använd den binära delnings operatorn ( \<string[]\> -Split \<delimiter\> )</span><span class="sxs-lookup"><span data-stu-id="759a0-181">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="759a0-182">Omslut alla strängar inom parentes</span><span class="sxs-lookup"><span data-stu-id="759a0-182">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="759a0-183">Lagra strängarna i en variabel och skicka sedan variabeln till operatorn Split</span><span class="sxs-lookup"><span data-stu-id="759a0-183">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="759a0-184">Se följande exempel:</span><span class="sxs-lookup"><span data-stu-id="759a0-184">Consider the following example:</span></span>

```
PS> -split "1 2", "a b"
1
2
a b
```

```
PS> "1 2", "a b" -split " "
1
2
a
b
```

```
PS> -split ("1 2", "a b")
1
2
a
b
```

```
PS> $a = "1 2", "a b"
PS> -split $a
1
2
a
b
```

## <a name="examples"></a><span data-ttu-id="759a0-185">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="759a0-185">EXAMPLES</span></span>

<span data-ttu-id="759a0-186">Följande instruktion delar upp strängen vid blank steg.</span><span class="sxs-lookup"><span data-stu-id="759a0-186">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```Output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="759a0-187">Följande instruktion delar upp strängen vid valfritt kommatecken.</span><span class="sxs-lookup"><span data-stu-id="759a0-187">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```Output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="759a0-188">Följande instruktion delar upp strängen i mönstret "er".</span><span class="sxs-lookup"><span data-stu-id="759a0-188">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```Output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="759a0-189">Följande instruktion utför en Skift läges känslig delning vid bokstaven "N".</span><span class="sxs-lookup"><span data-stu-id="759a0-189">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```Output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="759a0-190">Följande instruktion delar upp strängen i "e" och "t".</span><span class="sxs-lookup"><span data-stu-id="759a0-190">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```Output
M
rcury,V
nus,
ar
h,Mars,Jupi

r,Sa
urn,Uranus,N
p
un
```

<span data-ttu-id="759a0-191">Följande instruktion delar upp strängen i "e" och "r", men begränsar de resulterande del strängarna till sex del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-191">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```Output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="759a0-192">Följande instruktion delar upp en sträng i tre del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-192">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```Output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="759a0-193">Följande instruktion delar upp en sträng i tre del strängar som börjar från slutet av strängen.</span><span class="sxs-lookup"><span data-stu-id="759a0-193">The following statement splits a string into three substrings starting from the end of the string.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", -3
```

```Output
a,b,c,d,e,f
g
h
```

<span data-ttu-id="759a0-194">Följande instruktion delar upp två strängar i tre del strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-194">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="759a0-195">(Gränsen tillämpas på varje sträng oberoende av varandra.)</span><span class="sxs-lookup"><span data-stu-id="759a0-195">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```Output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="759a0-196">Följande instruktion delar upp varje rad i den här-strängen vid den första siffran.</span><span class="sxs-lookup"><span data-stu-id="759a0-196">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="759a0-197">Alternativet för flera rader används för att identifiera början av varje rad och sträng.</span><span class="sxs-lookup"><span data-stu-id="759a0-197">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="759a0-198">0 representerar värdet "returnera alla" för parametern för max-under strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-198">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="759a0-199">Du kan använda alternativ, till exempel flera rader, endast när värdet för max-under strängar har angetts.</span><span class="sxs-lookup"><span data-stu-id="759a0-199">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```Output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="759a0-200">I följande instruktion används omvänt snedstreck för att undvika punkt (.)-avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-200">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="759a0-201">Med standardvärdet, RegexMatch, kommer punkten inom citat tecken (".") att tolkas för att matcha alla tecken utom ett rad matnings tecken.</span><span class="sxs-lookup"><span data-stu-id="759a0-201">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="759a0-202">Därför returnerar delnings instruktionen en tom rad för varje tecken förutom ny rad.</span><span class="sxs-lookup"><span data-stu-id="759a0-202">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```Output
This
is
a
test
```

<span data-ttu-id="759a0-203">I följande instruktion används alternativet SimpleMatch för att dirigera operatorn-Split för att tolka punkt (.)-avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="759a0-203">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="759a0-204">0 representerar värdet "returnera alla" för parametern för max-under strängar.</span><span class="sxs-lookup"><span data-stu-id="759a0-204">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="759a0-205">Du kan använda alternativ, till exempel SimpleMatch, endast när värdet för max-under strängar har angetts.</span><span class="sxs-lookup"><span data-stu-id="759a0-205">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```Output
This
is
a
test
```

<span data-ttu-id="759a0-206">Följande instruktion delar upp strängen på en av två avgränsare, beroende på värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="759a0-206">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```Output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="759a0-207">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="759a0-207">SEE ALSO</span></span>

[<span data-ttu-id="759a0-208">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="759a0-208">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="759a0-209">about_Operators</span><span class="sxs-lookup"><span data-stu-id="759a0-209">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="759a0-210">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="759a0-210">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="759a0-211">about_Join</span><span class="sxs-lookup"><span data-stu-id="759a0-211">about_Join</span></span>](about_Join.md)

