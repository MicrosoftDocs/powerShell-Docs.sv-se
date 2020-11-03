---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: a5f65a70ccb97db5338456cca50309b593b900c1
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262803"
---
# <span data-ttu-id="fbae5-103">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="fbae5-103">ConvertFrom-StringData</span></span>

## <span data-ttu-id="fbae5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fbae5-104">SYNOPSIS</span></span>
<span data-ttu-id="fbae5-105">Konverterar en sträng som innehåller ett eller flera nyckel-och värdepar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="fbae5-105">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="fbae5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fbae5-106">SYNTAX</span></span>

### <span data-ttu-id="fbae5-107">Alla</span><span class="sxs-lookup"><span data-stu-id="fbae5-107">All</span></span>

```
ConvertFrom-StringData [-StringData] <String> [[-Delimiter] <Char>] [<CommonParameters>]
```

## <span data-ttu-id="fbae5-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fbae5-108">DESCRIPTION</span></span>

<span data-ttu-id="fbae5-109">`ConvertFrom-StringData`Cmdleten konverterar en sträng som innehåller en eller flera nyckel-och värdepar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="fbae5-109">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="fbae5-110">Eftersom varje nyckel/värde-par måste finnas på en separat rad används ofta följande strängar som indataformat.</span><span class="sxs-lookup"><span data-stu-id="fbae5-110">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="fbae5-111">Som standard måste **nyckeln** skiljas från **värdet** med ett likhets tecken ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="fbae5-111">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="fbae5-112">`ConvertFrom-StringData`Cmdleten anses vara en säker cmdlet som kan användas i `DATA` avsnittet i ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="fbae5-112">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="fbae5-113">När det används i ett `DATA` avsnitt måste innehållet i strängen följa reglerna för ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fbae5-113">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="fbae5-114">Mer information finns i [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span><span class="sxs-lookup"><span data-stu-id="fbae5-114">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="fbae5-115">`ConvertFrom-StringData` stöder escape-tecken som tillåts av konventionella verktyg för maskin översättning.</span><span class="sxs-lookup"><span data-stu-id="fbae5-115">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="fbae5-116">Det vill säga att cmdleten kan tolka omvända snedstreck ( `\` ) som escape-tecken i sträng data med hjälp av [regex. unescape-metoden](/dotnet/api/system.text.regularexpressions.regex.unescape)i stället för PowerShell-tecknet ( \` ) som normalt signalerar slutet på en rad i ett skript.</span><span class="sxs-lookup"><span data-stu-id="fbae5-116">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="fbae5-117">Inuti denna-sträng fungerar inte autoskalning-tecken.</span><span class="sxs-lookup"><span data-stu-id="fbae5-117">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="fbae5-118">Du kan också bevara ett omvänt snedstreck i resultatet genom att använda ett föregående omvänt snedstreck, t. ex `\\` .:.</span><span class="sxs-lookup"><span data-stu-id="fbae5-118">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="fbae5-119">Avvisade omvända snedstreck, till exempel de som ofta används i fil Sök vägar, kan återges som otillåtna escape-sekvenser i resultatet.</span><span class="sxs-lookup"><span data-stu-id="fbae5-119">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

<span data-ttu-id="fbae5-120">PowerShell 7 lägger till **avgränsnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="fbae5-120">PowerShell 7 adds the **Delimiter** parameter.</span></span>

## <span data-ttu-id="fbae5-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fbae5-121">EXAMPLES</span></span>

### <span data-ttu-id="fbae5-122">Exempel 1: konvertera en a-citerad hit-sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="fbae5-122">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="fbae5-123">I det här exemplet konverteras en a-sträng med användar meddelanden till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="fbae5-123">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="fbae5-124">I en sträng med en citat tecken ersätts inte värdena för variabler och uttryck utvärderas inte.</span><span class="sxs-lookup"><span data-stu-id="fbae5-124">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="fbae5-125">`ConvertFrom-StringData`Cmdleten konverterar värdet i `$Here` variabeln till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="fbae5-125">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
ConvertFrom-StringData -StringData $Here
```

```Output
Name                           Value
----                           -----
Msg3                           The specified variable does not exist.
Msg2                           Credentials are required for this command.
Msg1                           The string parameter is required.
```

### <span data-ttu-id="fbae5-126">Exempel 2: konvertera sträng data med hjälp av en annan avgränsare</span><span class="sxs-lookup"><span data-stu-id="fbae5-126">Example 2: Convert string data using a different delimiter</span></span>

<span data-ttu-id="fbae5-127">Det här exemplet visar hur du konverterar sträng data som använder ett annat tecken som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="fbae5-127">This example shows how to convert string data that uses a different character as a delimiter.</span></span> <span data-ttu-id="fbae5-128">I det här exemplet använder sträng data pipe-tecknet ( `|` ) som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="fbae5-128">In this example the string data is using the pipe character (`|`) as the delimiter.</span></span>

```powershell
$StringData = @'
color|red
model|coupe
year|1965
condition|mint
'@
$carData = ConvertFrom-StringData -StringData $StringData -Delimiter '|'
$carData
```

```Output
Name                           Value
----                           -----
condition                      mint
model                          coupe
color                          red
year                           1965
```

### <span data-ttu-id="fbae5-129">Exempel 3: konvertera en här-sträng som innehåller en kommentar</span><span class="sxs-lookup"><span data-stu-id="fbae5-129">Example 3: Convert a here-string containing a comment</span></span>

<span data-ttu-id="fbae5-130">I det här exemplet konverteras en här-sträng som innehåller en kommentar och flera nyckel/värde-par till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="fbae5-130">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

```powershell
ConvertFrom-StringData -StringData @'
Name = Disks.ps1

# Category is optional.

Category = Storage
Cost = Free
'@
```

```Output
Name                           Value
----                           -----
Cost                           Free
Category                       Storage
Name                           Disks.ps1
```

<span data-ttu-id="fbae5-131">Värdet för parametern **StringData** är en här-sträng, i stället för en variabel som innehåller en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="fbae5-131">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="fbae5-132">Båda formaten är giltiga.</span><span class="sxs-lookup"><span data-stu-id="fbae5-132">Either format is valid.</span></span> <span data-ttu-id="fbae5-133">Denna-sträng innehåller en kommentar om en av strängarna.</span><span class="sxs-lookup"><span data-stu-id="fbae5-133">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="fbae5-134">`ConvertFrom-StringData` ignorerar kommentarer på en rad, men det `#` måste vara det första icke-blank tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="fbae5-134">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="fbae5-135">Alla tecken på raden efter `#` ignoreras.</span><span class="sxs-lookup"><span data-stu-id="fbae5-135">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="fbae5-136">Exempel 4: konvertera en sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="fbae5-136">Example 4: Convert a string to a hash table</span></span>

<span data-ttu-id="fbae5-137">I det här exemplet konverteras en vanlig sträng med dubbla citat tecken (inte en här sträng) till en hash-tabell och sparas i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fbae5-137">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

```powershell
$A = ConvertFrom-StringData -StringData "Top = Red `n Bottom = Blue"
$A
```

```Output
Name             Value
----             -----
Bottom           Blue
Top              Red
```

<span data-ttu-id="fbae5-138">För att uppfylla villkoret att varje nyckel/värde-par måste finnas på en separat rad, använder strängen PowerShell-starttecknet ( \` n) för att avgränsa paren.</span><span class="sxs-lookup"><span data-stu-id="fbae5-138">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="fbae5-139">Exempel 5: använda ConvertFrom-StringData i DATA avsnittet i ett skript</span><span class="sxs-lookup"><span data-stu-id="fbae5-139">Example 5: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="fbae5-140">I det här exemplet visas ett `ConvertFrom-StringData` kommando som används i data avsnittet i ett skript.</span><span class="sxs-lookup"><span data-stu-id="fbae5-140">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="fbae5-141">I instruktionerna under DATA avsnittet visas texten för användaren.</span><span class="sxs-lookup"><span data-stu-id="fbae5-141">The statements below the DATA section display the text to the user.</span></span>

```powershell
$TextMsgs = DATA {
ConvertFrom-StringData @'
Text001 = The $Notebook variable contains the name of the user's system notebook.
Text002 = The $MyNotebook variable contains the name of the user's private notebook.
'@
}
$TextMsgs
```

```Output
Name             Value
----             -----
Text001          The $Notebook variable contains the name of the user's system notebook.
Text002          The $MyNotebook variable contains the name of the user's private notebook.
```

<span data-ttu-id="fbae5-142">Eftersom texten innehåller variabel namn måste den omges av en sträng med en citat tecken så att variabler tolkas bokstavligen och inte expanderas.</span><span class="sxs-lookup"><span data-stu-id="fbae5-142">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="fbae5-143">Variabler är inte tillåtna i **data** -avsnittet.</span><span class="sxs-lookup"><span data-stu-id="fbae5-143">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="fbae5-144">Exempel 6: Använd pipeline-operatorn för att skicka en sträng</span><span class="sxs-lookup"><span data-stu-id="fbae5-144">Example 6: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="fbae5-145">Det här exemplet visar att du kan använda en pipeline-operator ( `|` ) för att skicka en sträng till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="fbae5-145">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="fbae5-146">Värdet för `$Here` variabeln är skickas `ConvertFrom-StringData` och resultatet i `$Hash` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fbae5-146">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

```powershell
$Here = @'
Msg1 = The string parameter is required.
Msg2 = Credentials are required for this command.
Msg3 = The specified variable does not exist.
'@
$Hash = $Here | ConvertFrom-StringData
$Hash
```

```Output
Name     Value
----     -----
Msg3     The specified variable does not exist.
Msg2     Credentials are required for this command.
Msg1     The string parameter is required.
```

### <span data-ttu-id="fbae5-147">Exempel 7: Använd escape-tecken för att lägga till nya rader och retur tecken</span><span class="sxs-lookup"><span data-stu-id="fbae5-147">Example 7: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="fbae5-148">Det här exemplet visar hur du använder escape-tecken för att skapa nya rader och returnera tecken i källdata.</span><span class="sxs-lookup"><span data-stu-id="fbae5-148">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="fbae5-149">Escape-sekvensen `\n` används för att skapa nya rader i ett block med text som är associerat med ett namn eller ett objekt i den resulterande hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fbae5-149">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

```powershell
ConvertFrom-StringData @"
Vincentio = Heaven doth with us as we with torches do,\nNot light them for themselves; for if our virtues\nDid not go forth of us, 'twere all alike\nAs if we had them not.
Angelo = Let there be some more test made of my metal,\nBefore so noble and so great a figure\nBe stamp'd upon it.
"@ | Format-List
```

```Output
Name  : Angelo
Value : Let there be some more test made of my metal,
        Before so noble and so great a figure
        Be stamp'd upon it.

Name  : Vincentio
Value : Heaven doth with us as we with torches do,
        Not light them for themselves; for if our virtues
        Did not go forth of us, 'twere all alike
        As if we had them not.
```

### <span data-ttu-id="fbae5-150">Exempel 8: Använd omvänt snedstreck escape-tecken för att rendera en fil Sök väg korrekt</span><span class="sxs-lookup"><span data-stu-id="fbae5-150">Example 8: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="fbae5-151">Det här exemplet visar hur du använder ett omvänt snedstreck i sträng data för att tillåta att en fil Sök väg återges korrekt i den resulterande `ConvertFrom-StringData` hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fbae5-151">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="fbae5-152">Det dubbla omvända snedstrecket garanterar att tecknen för litteral omvänt snedstreck återges korrekt i utdata för hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fbae5-152">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="fbae5-153">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fbae5-153">PARAMETERS</span></span>

### <span data-ttu-id="fbae5-154">-StringData</span><span class="sxs-lookup"><span data-stu-id="fbae5-154">-StringData</span></span>

<span data-ttu-id="fbae5-155">Anger den sträng som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="fbae5-155">Specifies the string to be converted.</span></span> <span data-ttu-id="fbae5-156">Du kan använda den här parametern eller skicka en sträng till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="fbae5-156">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="fbae5-157">Parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="fbae5-157">The parameter name is optional.</span></span>

<span data-ttu-id="fbae5-158">Värdet för den här parametern måste vara en sträng som innehåller ett eller flera nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="fbae5-158">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="fbae5-159">Varje nyckel/värde-par måste finnas på en separat rad, eller varje par måste avgränsas med rad matnings tecken ( \` n).</span><span class="sxs-lookup"><span data-stu-id="fbae5-159">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="fbae5-160">Du kan inkludera kommentarer i strängen, men kommentarerna får inte finnas på samma rad som ett nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="fbae5-160">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="fbae5-161">`ConvertFrom-StringData` ignorerar kommentarer på en rad.</span><span class="sxs-lookup"><span data-stu-id="fbae5-161">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="fbae5-162">`#`Specialtecknet måste vara det första icke-blank tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="fbae5-162">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="fbae5-163">Alla tecken på raden efter `#` ignoreras.</span><span class="sxs-lookup"><span data-stu-id="fbae5-163">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="fbae5-164">Kommentarerna ingår inte i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="fbae5-164">The comments are not included in the hash table.</span></span>

<span data-ttu-id="fbae5-165">En här-sträng är en sträng som består av en eller flera rader.</span><span class="sxs-lookup"><span data-stu-id="fbae5-165">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="fbae5-166">Citat tecken inom denna-sträng tolkas bokstavligen som en del av sträng data.</span><span class="sxs-lookup"><span data-stu-id="fbae5-166">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="fbae5-167">Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="fbae5-167">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="fbae5-168">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="fbae5-168">-Delimiter</span></span>

<span data-ttu-id="fbae5-169">Det tecken som används för att avgränsa **nyckeln** från **värde** data i strängen som konverteras.</span><span class="sxs-lookup"><span data-stu-id="fbae5-169">The character used to separate the **key** from the **value** data in the string being converted.</span></span>
<span data-ttu-id="fbae5-170">Standard avgränsaren är likhets tecknet ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="fbae5-170">The default delimiter is the equals sign (`=`) character.</span></span> <span data-ttu-id="fbae5-171">Den här parametern lades till i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="fbae5-171">This parameter was added in PowerShell 7.</span></span>

```yaml
Type: System.Char
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: '='
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fbae5-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fbae5-172">CommonParameters</span></span>

<span data-ttu-id="fbae5-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fbae5-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fbae5-174">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="fbae5-174">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="fbae5-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="fbae5-175">INPUTS</span></span>

### <span data-ttu-id="fbae5-176">System. String</span><span class="sxs-lookup"><span data-stu-id="fbae5-176">System.String</span></span>

<span data-ttu-id="fbae5-177">Du kan skicka vidare en sträng som innehåller ett nyckel/värde-par till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="fbae5-177">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="fbae5-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fbae5-178">OUTPUTS</span></span>

### <span data-ttu-id="fbae5-179">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="fbae5-179">System.Collections.Hashtable</span></span>

<span data-ttu-id="fbae5-180">Denna cmdlet returnerar en hash-tabell som den skapar från nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="fbae5-180">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="fbae5-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fbae5-181">NOTES</span></span>

<span data-ttu-id="fbae5-182">En här-sträng är en sträng som består av en eller flera rader inom vilka citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="fbae5-182">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="fbae5-183">Denna cmdlet kan vara användbar i skript som visar användar meddelanden på flera talade språk.</span><span class="sxs-lookup"><span data-stu-id="fbae5-183">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="fbae5-184">Du kan använda hash-tabeller i lexikonet för att isolera text strängar från kod, till exempel i resursfiler, och för att formatera text strängarna för användning i översättnings verktyg.</span><span class="sxs-lookup"><span data-stu-id="fbae5-184">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="fbae5-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fbae5-185">RELATED LINKS</span></span>
