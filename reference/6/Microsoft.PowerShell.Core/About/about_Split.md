---
description: Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/20/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_split?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Split
ms.openlocfilehash: 520aac1fd1aae4f1f0f4a12a10bc4f5c7f258731
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270369"
---
# <a name="about-split"></a><span data-ttu-id="a35f5-104">Om delning</span><span class="sxs-lookup"><span data-stu-id="a35f5-104">About Split</span></span>

## <a name="short-description"></a><span data-ttu-id="a35f5-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a35f5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a35f5-106">Förklarar hur du använder Split-operatorn för att dela upp en eller flera strängar i del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-106">Explains how to use the Split operator to split one or more strings into substrings.</span></span>

## <a name="long-description"></a><span data-ttu-id="a35f5-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a35f5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a35f5-108">Operatorn Split delar en eller flera strängar i del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-108">The Split operator splits one or more strings into substrings.</span></span> <span data-ttu-id="a35f5-109">Du kan ändra följande delar av delnings åtgärden:</span><span class="sxs-lookup"><span data-stu-id="a35f5-109">You can change the following elements of the Split operation:</span></span>

- <span data-ttu-id="a35f5-110">Avgränsare.</span><span class="sxs-lookup"><span data-stu-id="a35f5-110">Delimiter.</span></span> <span data-ttu-id="a35f5-111">Standardvärdet är blank steg, men du kan ange tecken, strängar, mönster eller skript block som anger avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-111">The default is whitespace, but you can specify characters, strings, patterns, or script blocks that specify the delimiter.</span></span> <span data-ttu-id="a35f5-112">Operatorn Split i PowerShell använder ett reguljärt uttryck i avgränsaren i stället för ett enkelt tecken.</span><span class="sxs-lookup"><span data-stu-id="a35f5-112">The Split operator in PowerShell uses a regular expression in the delimiter, rather than a simple character.</span></span>
- <span data-ttu-id="a35f5-113">Maximalt antal del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-113">Maximum number of substrings.</span></span> <span data-ttu-id="a35f5-114">Standardvärdet är att returnera alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-114">The default is to return all substrings.</span></span> <span data-ttu-id="a35f5-115">Om du anger ett tal som är mindre än antalet under strängar sammanfogas de återstående del strängarna i den sista del strängen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-115">If you specify a number less than the number of substrings, the remaining substrings are concatenated in the last substring.</span></span>
- <span data-ttu-id="a35f5-116">Alternativ som anger de villkor under vilka avgränsaren matchas, till exempel SimpleMatch och Multiline.</span><span class="sxs-lookup"><span data-stu-id="a35f5-116">Options that specify the conditions under which the delimiter is matched, such as SimpleMatch and Multiline.</span></span>

## <a name="syntax"></a><span data-ttu-id="a35f5-117">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a35f5-117">SYNTAX</span></span>

<span data-ttu-id="a35f5-118">Följande diagram visar syntaxen för operatorn-Split.</span><span class="sxs-lookup"><span data-stu-id="a35f5-118">The following diagram shows the syntax for the -split operator.</span></span>

<span data-ttu-id="a35f5-119">Parameter namnen visas inte i kommandot.</span><span class="sxs-lookup"><span data-stu-id="a35f5-119">The parameter names do not appear in the command.</span></span> <span data-ttu-id="a35f5-120">Inkludera endast parameter värden.</span><span class="sxs-lookup"><span data-stu-id="a35f5-120">Include only the parameter values.</span></span> <span data-ttu-id="a35f5-121">Värdena måste visas i den ordning som anges i syntax-diagrammet.</span><span class="sxs-lookup"><span data-stu-id="a35f5-121">The values must appear in the order specified in the syntax diagram.</span></span>

```
-Split <String>
-Split (<String[]>)
<String> -Split <Delimiter>[,<Max-substrings>[,"<Options>"]]
<String> -Split {<ScriptBlock>} [,<Max-substrings>]
```

<span data-ttu-id="a35f5-122">Du kan ersätta `-iSplit` eller `-cSplit` för `-split` i en binär delnings instruktion (en delad instruktion som innehåller en avgränsare eller ett skript block).</span><span class="sxs-lookup"><span data-stu-id="a35f5-122">You can substitute `-iSplit` or `-cSplit` for `-split` in any binary Split statement (a Split statement that includes a delimiter or script block).</span></span> <span data-ttu-id="a35f5-123">`-iSplit` `-split` Operatorerna och är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a35f5-123">The `-iSplit` and `-split` operators are case-insensitive.</span></span> <span data-ttu-id="a35f5-124">`-cSplit`Operatorn är Skift läges känslig, vilket innebär att ärendet beaktas när reglerna för avgränsare används.</span><span class="sxs-lookup"><span data-stu-id="a35f5-124">The `-cSplit` operator is case-sensitive, meaning that case is considered when the delimiter rules are applied.</span></span>

## <a name="parameters"></a><span data-ttu-id="a35f5-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a35f5-125">PARAMETERS</span></span>

### <a name="string-or-string"></a><span data-ttu-id="a35f5-126">\<String\> eller \<String[]\></span><span class="sxs-lookup"><span data-stu-id="a35f5-126">\<String\> or \<String[]\></span></span>

<span data-ttu-id="a35f5-127">Anger en eller flera strängar som ska delas upp.</span><span class="sxs-lookup"><span data-stu-id="a35f5-127">Specifies one or more strings to be split.</span></span> <span data-ttu-id="a35f5-128">Om du skickar flera strängar delas alla strängar med samma regler för avgränsare.</span><span class="sxs-lookup"><span data-stu-id="a35f5-128">If you submit multiple strings, all the strings are split using the same delimiter rules.</span></span>

<span data-ttu-id="a35f5-129">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-129">Example:</span></span>

```
-split "red yellow blue green"
red
yellow
blue
green
```

### \<Delimiter\>

<span data-ttu-id="a35f5-130">De tecken som identifierar slutet av en under sträng.</span><span class="sxs-lookup"><span data-stu-id="a35f5-130">The characters that identify the end of a substring.</span></span> <span data-ttu-id="a35f5-131">Standard avgränsaren är blank steg, inklusive blank steg och tecken som inte kan skrivas ut, till exempel ny rad matning ( \` n) och TABB ( \` t).</span><span class="sxs-lookup"><span data-stu-id="a35f5-131">The default delimiter is whitespace, including spaces and non-printable characters, such as newline (\`n) and tab (\`t).</span></span> <span data-ttu-id="a35f5-132">När strängarna delas, utelämnas avgränsaren från alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-132">When the strings are split, the delimiter is omitted from all the substrings.</span></span> <span data-ttu-id="a35f5-133">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-133">Example:</span></span>

```
"Lastname:FirstName:Address" -split ":"
Lastname
FirstName
Address
```

<span data-ttu-id="a35f5-134">Som standard utelämnas avgränsaren från resultaten.</span><span class="sxs-lookup"><span data-stu-id="a35f5-134">By default, the delimiter is omitted from the results.</span></span> <span data-ttu-id="a35f5-135">Om du vill bevara hela eller delar av avgränsaren omger du den del som du vill behålla.</span><span class="sxs-lookup"><span data-stu-id="a35f5-135">To preserve all or part of the delimiter, enclose in parentheses the part that you want to preserve.</span></span>
<span data-ttu-id="a35f5-136">Om \<Max-substrings\> parametern läggs till, prioriteras det när kommandot delar upp samlingen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-136">If the \<Max-substrings\> parameter is added, this takes precedence when your command splits up the collection.</span></span> <span data-ttu-id="a35f5-137">Om du väljer att ta med en avgränsare som en del av utdata returnerar kommandot avgränsaren som en del av utdata. men att dela strängen för att returnera avgränsaren som en del av utdata räknas inte som en delning.</span><span class="sxs-lookup"><span data-stu-id="a35f5-137">If you opt to include a delimiter as part of the output, the command returns the delimiter as part of the output; however, splitting the string to return the delimiter as part of output does not count as a split.</span></span>

<span data-ttu-id="a35f5-138">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-138">Examples:</span></span>

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

<span data-ttu-id="a35f5-139">I följande exempel \<Max-substrings\> är värdet 3.</span><span class="sxs-lookup"><span data-stu-id="a35f5-139">In the following example, \<Max-substrings\> is set to 3.</span></span> <span data-ttu-id="a35f5-140">Detta resulterar i tre delar av sträng värden, men totalt fem strängar i resultatet. avgränsaren ingår efter delningarna tills det maximala antalet under strängar har nåtts.</span><span class="sxs-lookup"><span data-stu-id="a35f5-140">This results in three splits of the string values, but a total of five strings in the resulting output; the delimiter is included after the splits, until the maximum of three substrings is reached.</span></span> <span data-ttu-id="a35f5-141">Ytterligare avgränsare i den sista del strängen blir del av under strängen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-141">Additional delimiters in the final substring become part of the substring.</span></span>

```powershell
'Chocolate-Vanilla-Strawberry-Blueberry' -split '(-)', 3
```

```output
Chocolate
-
Vanilla
-
Strawberry-Blueberry
```

### \<Max-substrings\>

<span data-ttu-id="a35f5-142">Anger det maximala antalet gånger som en sträng är delad.</span><span class="sxs-lookup"><span data-stu-id="a35f5-142">Specifies the maximum number of times that a string is split.</span></span> <span data-ttu-id="a35f5-143">Standardvärdet är alla del strängar som delas av avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-143">The default is all the substrings split by the delimiter.</span></span> <span data-ttu-id="a35f5-144">Om det finns fler del strängar sammanfogas de till den slutliga del strängen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-144">If there are more substrings, they are concatenated to the final substring.</span></span> <span data-ttu-id="a35f5-145">Om det finns färre del strängar returneras alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-145">If there are fewer substrings, all the substrings are returned.</span></span> <span data-ttu-id="a35f5-146">Värdet 0 och negativa värden returnerar alla del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-146">A value of 0 and negative values return all the substrings.</span></span>

<span data-ttu-id="a35f5-147">Max-delsträngar anger inte det maximala antalet objekt som returneras. värdet är lika med det maximala antalet gånger som en sträng är delad.</span><span class="sxs-lookup"><span data-stu-id="a35f5-147">Max-substrings does not specify the maximum number of objects that are returned; its value equals the maximum number of times that a string is split.</span></span>
<span data-ttu-id="a35f5-148">Om du skickar mer än en sträng (en sträng mat ris) till delnings operatorn, används Max-substring-gränsen på varje sträng separat.</span><span class="sxs-lookup"><span data-stu-id="a35f5-148">If you submit more than one string (an array of strings) to the Split operator , the Max-substrings limit is applied to each string separately.</span></span>

<span data-ttu-id="a35f5-149">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-149">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split ",", 5
```

```output
Mercury
Venus
Earth
Mars
Jupiter,Saturn,Uranus,Neptune
```

### \<ScriptBlock\>

<span data-ttu-id="a35f5-150">Ett uttryck som anger regler för att tillämpa avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-150">An expression that specifies rules for applying the delimiter.</span></span> <span data-ttu-id="a35f5-151">Uttrycket måste utvärderas till $true eller $false.</span><span class="sxs-lookup"><span data-stu-id="a35f5-151">The expression must evaluate to $true or $false.</span></span> <span data-ttu-id="a35f5-152">Omge skript blocket med klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="a35f5-152">Enclose the script block in braces.</span></span>

<span data-ttu-id="a35f5-153">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-153">Example:</span></span>

```powershell
$c = "Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune"
$c -split {$_ -eq "e" -or $_ -eq "p"}
```

```output
M
rcury,V
nus,
arth,Mars,Ju
it
r,Saturn,Uranus,N

tun
```

### \<Options\>

<span data-ttu-id="a35f5-154">Omge alternativets namn inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a35f5-154">Enclose the option name in quotation marks.</span></span> <span data-ttu-id="a35f5-155">Alternativen är endast giltiga när \<Max-substrings\> parametern används i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-155">Options are valid only when the \<Max-substrings\> parameter is used in the statement.</span></span>

<span data-ttu-id="a35f5-156">Syntaxen för parametern options är:</span><span class="sxs-lookup"><span data-stu-id="a35f5-156">The syntax for the Options parameter is:</span></span>

```
"SimpleMatch [,IgnoreCase]"

"[RegexMatch] [,IgnoreCase] [,CultureInvariant]
[,IgnorePatternWhitespace] [,ExplicitCapture]
[,Singleline | ,Multiline]"
```

<span data-ttu-id="a35f5-157">Alternativen för SimpleMatch är:</span><span class="sxs-lookup"><span data-stu-id="a35f5-157">The SimpleMatch options are:</span></span>

- <span data-ttu-id="a35f5-158">**SimpleMatch** : Använd enkel sträng jämförelse när du utvärderar avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-158">**SimpleMatch** : Use simple string comparison when evaluating the delimiter.</span></span> <span data-ttu-id="a35f5-159">Kan inte användas med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="a35f5-159">Cannot be used with RegexMatch.</span></span>
- <span data-ttu-id="a35f5-160">**IgnoreCase** : tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.</span><span class="sxs-lookup"><span data-stu-id="a35f5-160">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>

<span data-ttu-id="a35f5-161">Alternativen för RegexMatch är:</span><span class="sxs-lookup"><span data-stu-id="a35f5-161">The RegexMatch options are:</span></span>

- <span data-ttu-id="a35f5-162">**RegexMatch** : Använd reguljär uttrycks matchning för att utvärdera avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-162">**RegexMatch** : Use regular expression matching to evaluate the delimiter.</span></span> <span data-ttu-id="a35f5-163">Det här är standardbeteendet.</span><span class="sxs-lookup"><span data-stu-id="a35f5-163">This is the default behavior.</span></span> <span data-ttu-id="a35f5-164">Kan inte användas med SimpleMatch.</span><span class="sxs-lookup"><span data-stu-id="a35f5-164">Cannot be used with SimpleMatch.</span></span>
- <span data-ttu-id="a35f5-165">**IgnoreCase** : tvingar Skift läges okänslig matchning, även om operatorn-cSplit har angetts.</span><span class="sxs-lookup"><span data-stu-id="a35f5-165">**IgnoreCase** : Forces case-insensitive matching, even if the -cSplit operator is specified.</span></span>
- <span data-ttu-id="a35f5-166">**CultureInvariant** : ignorerar kultur skillnader i språk när evaluting avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-166">**CultureInvariant** : Ignores cultural differences in language when evaluting the delimiter.</span></span> <span data-ttu-id="a35f5-167">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="a35f5-167">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="a35f5-168">**IgnorePatternWhitespace** : ignorerar ej Escaped blank steg och kommentarer som marker ATS med nummer tecknet (#).</span><span class="sxs-lookup"><span data-stu-id="a35f5-168">**IgnorePatternWhitespace** : Ignores unescaped whitespace and comments marked with the number sign (#).</span></span> <span data-ttu-id="a35f5-169">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="a35f5-169">Valid only with RegexMatch.</span></span>
- <span data-ttu-id="a35f5-170">Flera **rader** : Multiline-läge tvingar fram `^` och `$` matchar början av varje rad i stället för början och slutet av Indatasträngen.</span><span class="sxs-lookup"><span data-stu-id="a35f5-170">**Multiline** : Multiline mode forces `^` and `$` to match the beginning end of every line instead of the beginning and end of the input string.</span></span>
- <span data-ttu-id="a35f5-171">**Singleline** : Singleline mode behandlar Indatasträngen som en *Singleline*.</span><span class="sxs-lookup"><span data-stu-id="a35f5-171">**Singleline** : Singleline mode treats the input string as a *SingleLine*.</span></span>
  <span data-ttu-id="a35f5-172">Det tvingar `.` tecknet att matcha varje Character (inklusive newlines), i stället för att matcha alla bokstäver förutom rad matningen `\n` .</span><span class="sxs-lookup"><span data-stu-id="a35f5-172">It forces the `.` character to match every character (including newlines), instead of matching every character EXCEPT the newline `\n`.</span></span>
- <span data-ttu-id="a35f5-173">**ExplicitCapture** : ignorerar matchnings grupper som inte är namngivna så att endast explicita infångnings grupper returneras i resultat listan.</span><span class="sxs-lookup"><span data-stu-id="a35f5-173">**ExplicitCapture** : Ignores non-named match groups so that only explicit capture groups are returned in the result list.</span></span> <span data-ttu-id="a35f5-174">Endast giltig med RegexMatch.</span><span class="sxs-lookup"><span data-stu-id="a35f5-174">Valid only with RegexMatch.</span></span>

## <a name="unary-and-binary-split-operators"></a><span data-ttu-id="a35f5-175">UNÄRA och binära delade OPERATORer</span><span class="sxs-lookup"><span data-stu-id="a35f5-175">UNARY and BINARY SPLIT OPERATORS</span></span>

<span data-ttu-id="a35f5-176">Den unära delnings operatorn ( `-split <string>` ) har högre prioritet än ett kommatecken.</span><span class="sxs-lookup"><span data-stu-id="a35f5-176">The unary split operator (`-split <string>`) has higher precedence than a comma.</span></span> <span data-ttu-id="a35f5-177">Det innebär att om du skickar en kommaavgränsad lista med strängar till den unära delnings operatorn, är det bara den första strängen (före det första kommatecknet) som delas.</span><span class="sxs-lookup"><span data-stu-id="a35f5-177">As a result, if you submit a comma-separated list of strings to the unary split operator, only the first string (before the first comma) is split.</span></span>

<span data-ttu-id="a35f5-178">Använd något av följande mönster för att dela fler än en sträng:</span><span class="sxs-lookup"><span data-stu-id="a35f5-178">Use one of the following patterns to split more than one string:</span></span>

- <span data-ttu-id="a35f5-179">Använd den binära delnings operatorn ( \<string[]\> -Split \<delimiter\> )</span><span class="sxs-lookup"><span data-stu-id="a35f5-179">Use the binary split operator (\<string[]\> -split \<delimiter\>)</span></span>
- <span data-ttu-id="a35f5-180">Omslut alla strängar inom parentes</span><span class="sxs-lookup"><span data-stu-id="a35f5-180">Enclose all the strings in parentheses</span></span>
- <span data-ttu-id="a35f5-181">Lagra strängarna i en variabel och skicka sedan variabeln till operatorn Split</span><span class="sxs-lookup"><span data-stu-id="a35f5-181">Store the strings in a variable then submit the variable to the split operator</span></span>

<span data-ttu-id="a35f5-182">Se följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a35f5-182">Consider the following example:</span></span>

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

## <a name="examples"></a><span data-ttu-id="a35f5-183">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a35f5-183">EXAMPLES</span></span>

<span data-ttu-id="a35f5-184">Följande instruktion delar upp strängen vid blank steg.</span><span class="sxs-lookup"><span data-stu-id="a35f5-184">The following statement splits the string at whitespace.</span></span>

```powershell
-split "Windows PowerShell 2.0`nWindows PowerShell with remoting"
```

```output

Windows
PowerShell
2.0
Windows
PowerShell
with
remoting
```

<span data-ttu-id="a35f5-185">Följande instruktion delar upp strängen vid valfritt kommatecken.</span><span class="sxs-lookup"><span data-stu-id="a35f5-185">The following statement splits the string at any comma.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split ','
```

```output
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

<span data-ttu-id="a35f5-186">Följande instruktion delar upp strängen i mönstret "er".</span><span class="sxs-lookup"><span data-stu-id="a35f5-186">The following statement splits the string at the pattern "er".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split 'er'
```

```output
M
cury,Venus,Earth,Mars,Jupit
,Saturn,Uranus,Neptune
```

<span data-ttu-id="a35f5-187">Följande instruktion utför en Skift läges känslig delning vid bokstaven "N".</span><span class="sxs-lookup"><span data-stu-id="a35f5-187">The following statement performs a case-sensitive split at the letter "N".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -cSplit 'N'
```

```output
Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,
eptune
```

<span data-ttu-id="a35f5-188">Följande instruktion delar upp strängen i "e" och "t".</span><span class="sxs-lookup"><span data-stu-id="a35f5-188">The following statement splits the string at "e" and "t".</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[et]'
```

```output
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

<span data-ttu-id="a35f5-189">Följande instruktion delar upp strängen i "e" och "r", men begränsar de resulterande del strängarna till sex del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-189">The following statement splits the string at "e" and "r", but limits the resulting substrings to six substrings.</span></span>

```powershell
"Mercury,Venus,Earth,Mars,Jupiter,Saturn,Uranus,Neptune" -split '[er]', 6
```

```output
M

cu
y,V
nus,
arth,Mars,Jupiter,Saturn,Uranus,Neptune
```

<span data-ttu-id="a35f5-190">Följande instruktion delar upp en sträng i tre del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-190">The following statement splits a string into three substrings.</span></span>

```powershell
"a,b,c,d,e,f,g,h" -split ",", 3
```

```output
a
b
c,d,e,f,g,h
```

<span data-ttu-id="a35f5-191">Följande instruktion delar upp två strängar i tre del strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-191">The following statement splits two strings into three substrings.</span></span>
<span data-ttu-id="a35f5-192">(Gränsen tillämpas på varje sträng oberoende av varandra.)</span><span class="sxs-lookup"><span data-stu-id="a35f5-192">(The limit is applied to each string independently.)</span></span>

```powershell
"a,b,c,d", "e,f,g,h" -split ",", 3
```

```output
a
b
c,d
e
f
g,h
```

<span data-ttu-id="a35f5-193">Följande instruktion delar upp varje rad i den här-strängen vid den första siffran.</span><span class="sxs-lookup"><span data-stu-id="a35f5-193">The following statement splits each line in the here-string at the first digit.</span></span> <span data-ttu-id="a35f5-194">Alternativet för flera rader används för att identifiera början av varje rad och sträng.</span><span class="sxs-lookup"><span data-stu-id="a35f5-194">It uses the Multiline option to recognize the beginning of each line and string.</span></span>

<span data-ttu-id="a35f5-195">0 representerar värdet "returnera alla" för parametern för max-under strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-195">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="a35f5-196">Du kan använda alternativ, till exempel flera rader, endast när värdet för max-under strängar har angetts.</span><span class="sxs-lookup"><span data-stu-id="a35f5-196">You can use options, such as Multiline, only when the Max-substrings value is specified.</span></span>

```powershell
$a = @'
1The first line.
2The second line.
3The third of three lines.
'@
$a -split "^\d", 0, "multiline"
```

```output

The first line.

The second line.

The third of three lines.
```

<span data-ttu-id="a35f5-197">I följande instruktion används omvänt snedstreck för att undvika punkt (.)-avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-197">The following statement uses the backslash character to escape the dot (.) delimiter.</span></span>

<span data-ttu-id="a35f5-198">Med standardvärdet, RegexMatch, kommer punkten inom citat tecken (".") att tolkas för att matcha alla tecken utom ett rad matnings tecken.</span><span class="sxs-lookup"><span data-stu-id="a35f5-198">With the default, RegexMatch, the dot enclosed in quotation marks (".") is interpreted to match any character except for a newline character.</span></span> <span data-ttu-id="a35f5-199">Därför returnerar delnings instruktionen en tom rad för varje tecken förutom ny rad.</span><span class="sxs-lookup"><span data-stu-id="a35f5-199">As a result, the Split statement returns a blank line for every character except newline.</span></span>

```powershell
"This.is.a.test" -split "\."
```

```output
This
is
a
test
```

<span data-ttu-id="a35f5-200">I följande instruktion används alternativet SimpleMatch för att dirigera operatorn-Split för att tolka punkt (.)-avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="a35f5-200">The following statement uses the SimpleMatch option to direct the -split operator to interpret the dot (.) delimiter literally.</span></span>

<span data-ttu-id="a35f5-201">0 representerar värdet "returnera alla" för parametern för max-under strängar.</span><span class="sxs-lookup"><span data-stu-id="a35f5-201">The 0 represents the "return all" value of the Max-substrings parameter.</span></span> <span data-ttu-id="a35f5-202">Du kan använda alternativ, till exempel SimpleMatch, endast när värdet för max-under strängar har angetts.</span><span class="sxs-lookup"><span data-stu-id="a35f5-202">You can use options, such as SimpleMatch, only when the Max-substrings value is specified.</span></span>

```powershell
"This.is.a.test" -split ".", 0, "simplematch"
```

```output
This
is
a
test
```

<span data-ttu-id="a35f5-203">Följande instruktion delar upp strängen på en av två avgränsare, beroende på värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="a35f5-203">The following statement splits the string at one of two delimiters, depending on the value of a variable.</span></span>

```powershell
$i = 1
$c = "LastName, FirstName; Address, City, State, Zip"
$c -split $(if ($i -lt 1) {","} else {";"})
```

```output
LastName, FirstName
 Address, City, State, Zip
```

## <a name="see-also"></a><span data-ttu-id="a35f5-204">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a35f5-204">SEE ALSO</span></span>

[<span data-ttu-id="a35f5-205">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="a35f5-205">Split-Path</span></span>](xref:Microsoft.PowerShell.Management.Split-Path)

[<span data-ttu-id="a35f5-206">about_Operators</span><span class="sxs-lookup"><span data-stu-id="a35f5-206">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="a35f5-207">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="a35f5-207">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="a35f5-208">about_Join</span><span class="sxs-lookup"><span data-stu-id="a35f5-208">about_Join</span></span>](about_Join.md)
