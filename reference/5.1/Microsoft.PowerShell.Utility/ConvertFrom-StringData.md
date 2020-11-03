---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/21/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-stringdata?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-StringData
ms.openlocfilehash: f4b58605059d85cd2a215969c13f9cc2e5262465
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265172"
---
# <span data-ttu-id="e3c76-103">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="e3c76-103">ConvertFrom-StringData</span></span>

## <span data-ttu-id="e3c76-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e3c76-104">SYNOPSIS</span></span>
<span data-ttu-id="e3c76-105">Konverterar en sträng som innehåller ett eller flera nyckel-och värdepar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e3c76-105">Converts a string containing one or more key and value pairs to a hash table.</span></span>

## <span data-ttu-id="e3c76-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e3c76-106">SYNTAX</span></span>

```
ConvertFrom-StringData [-StringData] <String> [<CommonParameters>]
```

## <span data-ttu-id="e3c76-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e3c76-107">DESCRIPTION</span></span>

<span data-ttu-id="e3c76-108">`ConvertFrom-StringData`Cmdleten konverterar en sträng som innehåller en eller flera nyckel-och värdepar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e3c76-108">The `ConvertFrom-StringData` cmdlet converts a string that contains one or more key and value pairs into a hash table.</span></span> <span data-ttu-id="e3c76-109">Eftersom varje nyckel/värde-par måste finnas på en separat rad används ofta följande strängar som indataformat.</span><span class="sxs-lookup"><span data-stu-id="e3c76-109">Because each key-value pair must be on a separate line, here-strings are often used as the input format.</span></span> <span data-ttu-id="e3c76-110">Som standard måste **nyckeln** skiljas från **värdet** med ett likhets tecken ( `=` ).</span><span class="sxs-lookup"><span data-stu-id="e3c76-110">By default, the **key** must be separated from the **value** by an equals sign (`=`) character.</span></span>

<span data-ttu-id="e3c76-111">`ConvertFrom-StringData`Cmdleten anses vara en säker cmdlet som kan användas i `DATA` avsnittet i ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="e3c76-111">The `ConvertFrom-StringData` cmdlet is considered to be a safe cmdlet that can be used in the `DATA` section of a script or function.</span></span> <span data-ttu-id="e3c76-112">När det används i ett `DATA` avsnitt måste innehållet i strängen följa reglerna för ett data avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e3c76-112">When used in a `DATA` section, the contents of the string must conform to the rules for a DATA section.</span></span> <span data-ttu-id="e3c76-113">Mer information finns i [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span><span class="sxs-lookup"><span data-stu-id="e3c76-113">For more information, see [about_Data_Sections](../Microsoft.PowerShell.Core/About/about_Data_Sections.md).</span></span>

<span data-ttu-id="e3c76-114">`ConvertFrom-StringData` stöder escape-tecken som tillåts av konventionella verktyg för maskin översättning.</span><span class="sxs-lookup"><span data-stu-id="e3c76-114">`ConvertFrom-StringData` supports escape character sequences that are allowed by conventional machine translation tools.</span></span> <span data-ttu-id="e3c76-115">Det vill säga att cmdleten kan tolka omvända snedstreck ( `\` ) som escape-tecken i sträng data med hjälp av [regex. unescape-metoden](/dotnet/api/system.text.regularexpressions.regex.unescape)i stället för PowerShell-tecknet ( \` ) som normalt signalerar slutet på en rad i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e3c76-115">That is, the cmdlet can interpret backslashes (`\`) as escape characters in the string data by using the [Regex.Unescape Method](/dotnet/api/system.text.regularexpressions.regex.unescape), instead of the PowerShell backtick character (\`) that would normally signal the end of a line in a script.</span></span> <span data-ttu-id="e3c76-116">Inuti denna-sträng fungerar inte autoskalning-tecken.</span><span class="sxs-lookup"><span data-stu-id="e3c76-116">Inside the here-string, the backtick character does not work.</span></span> <span data-ttu-id="e3c76-117">Du kan också bevara ett omvänt snedstreck i resultatet genom att använda ett föregående omvänt snedstreck, t. ex `\\` .:.</span><span class="sxs-lookup"><span data-stu-id="e3c76-117">You can also preserve a literal backslash in your results by escaping it with a preceding backslash, like this: `\\`.</span></span> <span data-ttu-id="e3c76-118">Avvisade omvända snedstreck, till exempel de som ofta används i fil Sök vägar, kan återges som otillåtna escape-sekvenser i resultatet.</span><span class="sxs-lookup"><span data-stu-id="e3c76-118">Unescaped backslash characters, such as those that are commonly used in file paths, can render as illegal escape sequences in your results.</span></span>

## <span data-ttu-id="e3c76-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e3c76-119">EXAMPLES</span></span>

### <span data-ttu-id="e3c76-120">Exempel 1: konvertera en a-citerad hit-sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="e3c76-120">Example 1: Convert a single-quoted here-string to a hash table</span></span>

<span data-ttu-id="e3c76-121">I det här exemplet konverteras en a-sträng med användar meddelanden till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e3c76-121">This example converts a single-quoted here-string of user messages into a hash table.</span></span> <span data-ttu-id="e3c76-122">I en sträng med en citat tecken ersätts inte värdena för variabler och uttryck utvärderas inte.</span><span class="sxs-lookup"><span data-stu-id="e3c76-122">In a single-quoted string, values are not substituted for variables and expressions are not evaluated.</span></span>
<span data-ttu-id="e3c76-123">`ConvertFrom-StringData`Cmdleten konverterar värdet i `$Here` variabeln till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e3c76-123">The `ConvertFrom-StringData` cmdlet converts the value in the `$Here` variable to a hash table.</span></span>

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

### <span data-ttu-id="e3c76-124">Exempel 2: konvertera en här-sträng som innehåller en kommentar</span><span class="sxs-lookup"><span data-stu-id="e3c76-124">Example 2: Convert a here-string containing a comment</span></span>

<span data-ttu-id="e3c76-125">I det här exemplet konverteras en här-sträng som innehåller en kommentar och flera nyckel/värde-par till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="e3c76-125">This example converts a here-string that contains a comment and multiple key-value pairs into a hash table.</span></span>

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

<span data-ttu-id="e3c76-126">Värdet för parametern **StringData** är en här-sträng, i stället för en variabel som innehåller en här-sträng.</span><span class="sxs-lookup"><span data-stu-id="e3c76-126">The value of the **StringData** parameter is a here-string, instead of a variable that contains a here-string.</span></span> <span data-ttu-id="e3c76-127">Båda formaten är giltiga.</span><span class="sxs-lookup"><span data-stu-id="e3c76-127">Either format is valid.</span></span> <span data-ttu-id="e3c76-128">Denna-sträng innehåller en kommentar om en av strängarna.</span><span class="sxs-lookup"><span data-stu-id="e3c76-128">The here-string includes a comment about one of the strings.</span></span>
<span data-ttu-id="e3c76-129">`ConvertFrom-StringData` ignorerar kommentarer på en rad, men det `#` måste vara det första icke-blank tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="e3c76-129">`ConvertFrom-StringData` ignores single-line comments, but the `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="e3c76-130">Alla tecken på raden efter `#` ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e3c76-130">All characters on the line after the `#` are ignored.</span></span>

### <span data-ttu-id="e3c76-131">Exempel 3: konvertera en sträng till en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="e3c76-131">Example 3: Convert a string to a hash table</span></span>

<span data-ttu-id="e3c76-132">I det här exemplet konverteras en vanlig sträng med dubbla citat tecken (inte en här sträng) till en hash-tabell och sparas i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e3c76-132">This example converts a regular double-quoted string (not a here-string) into a hash table and saves it in the `$A` variable.</span></span>

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

<span data-ttu-id="e3c76-133">För att uppfylla villkoret att varje nyckel/värde-par måste finnas på en separat rad, använder strängen PowerShell-starttecknet ( \` n) för att avgränsa paren.</span><span class="sxs-lookup"><span data-stu-id="e3c76-133">To satisfy the condition that each key-value pair must be on a separate line, the string uses the PowerShell newline character (\`n) to separate the pairs.</span></span>

### <span data-ttu-id="e3c76-134">Exempel 4: Använd ConvertFrom-StringData i DATA avsnittet i ett skript</span><span class="sxs-lookup"><span data-stu-id="e3c76-134">Example 4: Use ConvertFrom-StringData in the DATA section of a script</span></span>

<span data-ttu-id="e3c76-135">I det här exemplet visas ett `ConvertFrom-StringData` kommando som används i data avsnittet i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e3c76-135">This example shows a `ConvertFrom-StringData` command used in the DATA section of a script.</span></span>
<span data-ttu-id="e3c76-136">I instruktionerna under DATA avsnittet visas texten för användaren.</span><span class="sxs-lookup"><span data-stu-id="e3c76-136">The statements below the DATA section display the text to the user.</span></span>

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

<span data-ttu-id="e3c76-137">Eftersom texten innehåller variabel namn måste den omges av en sträng med en citat tecken så att variabler tolkas bokstavligen och inte expanderas.</span><span class="sxs-lookup"><span data-stu-id="e3c76-137">Because the text includes variable names, it must be enclosed in a single-quoted string so that the variables are interpreted literally and not expanded.</span></span> <span data-ttu-id="e3c76-138">Variabler är inte tillåtna i **data** -avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e3c76-138">Variables are not permitted in the **DATA** section.</span></span>

### <span data-ttu-id="e3c76-139">Exempel 5: Använd pipeline-operatorn för att skicka en sträng</span><span class="sxs-lookup"><span data-stu-id="e3c76-139">Example 5: Use the pipeline operator to pass a string</span></span>

<span data-ttu-id="e3c76-140">Det här exemplet visar att du kan använda en pipeline-operator ( `|` ) för att skicka en sträng till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="e3c76-140">This example shows that you can use a pipeline operator (`|`) to send a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="e3c76-141">Värdet för `$Here` variabeln är skickas `ConvertFrom-StringData` och resultatet i `$Hash` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e3c76-141">The the value of the `$Here` variable is piped to `ConvertFrom-StringData` and the result in the `$Hash` variable.</span></span>

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

### <span data-ttu-id="e3c76-142">Exempel 6: Använd escape-tecken för att lägga till nya rader och retur tecken</span><span class="sxs-lookup"><span data-stu-id="e3c76-142">Example 6: Use escape characters to add new lines and return characters</span></span>

<span data-ttu-id="e3c76-143">Det här exemplet visar hur du använder escape-tecken för att skapa nya rader och returnera tecken i källdata.</span><span class="sxs-lookup"><span data-stu-id="e3c76-143">This example shows the use of escape characters to create new lines and return characters in source data.</span></span> <span data-ttu-id="e3c76-144">Escape-sekvensen `\n` används för att skapa nya rader i ett block med text som är associerat med ett namn eller ett objekt i den resulterande hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="e3c76-144">The escape sequence `\n` is used to create new lines within a block of text that is associated with a name or item in the resulting hash table.</span></span>

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

### <span data-ttu-id="e3c76-145">Exempel 7: Använd omvänt snedstreck escape-tecken för att rendera en fil Sök väg korrekt</span><span class="sxs-lookup"><span data-stu-id="e3c76-145">Example 7: Use backslash escape character to correctly render a file path</span></span>

<span data-ttu-id="e3c76-146">Det här exemplet visar hur du använder ett omvänt snedstreck i sträng data för att tillåta att en fil Sök väg återges korrekt i den resulterande `ConvertFrom-StringData` hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="e3c76-146">This example shows how to use of the backslash escape character in the string data to allow a file path to render correctly in the resulting `ConvertFrom-StringData` hash table.</span></span> <span data-ttu-id="e3c76-147">Det dubbla omvända snedstrecket garanterar att tecknen för litteral omvänt snedstreck återges korrekt i utdata för hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="e3c76-147">The double backslash ensures that the literal backslash characters render correctly in the hash table output.</span></span>

```powershell
ConvertFrom-StringData "Message=Look in c:\\Windows\\System32"
```

```Output
Name                           Value
----                           -----
Message                        Look in c:\Windows\System32
```

## <span data-ttu-id="e3c76-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e3c76-148">PARAMETERS</span></span>

### <span data-ttu-id="e3c76-149">-StringData</span><span class="sxs-lookup"><span data-stu-id="e3c76-149">-StringData</span></span>

<span data-ttu-id="e3c76-150">Anger den sträng som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="e3c76-150">Specifies the string to be converted.</span></span> <span data-ttu-id="e3c76-151">Du kan använda den här parametern eller skicka en sträng till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="e3c76-151">You can use this parameter or pipe a string to `ConvertFrom-StringData`.</span></span> <span data-ttu-id="e3c76-152">Parameter namnet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e3c76-152">The parameter name is optional.</span></span>

<span data-ttu-id="e3c76-153">Värdet för den här parametern måste vara en sträng som innehåller ett eller flera nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="e3c76-153">The value of this parameter must be a string that contains one or more key-value pairs.</span></span> <span data-ttu-id="e3c76-154">Varje nyckel/värde-par måste finnas på en separat rad, eller varje par måste avgränsas med rad matnings tecken ( \` n).</span><span class="sxs-lookup"><span data-stu-id="e3c76-154">Each key-value pair must be on a separate line, or each pair must be separated by newline characters (\`n).</span></span>

<span data-ttu-id="e3c76-155">Du kan inkludera kommentarer i strängen, men kommentarerna får inte finnas på samma rad som ett nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="e3c76-155">You can include comments in the string, but the comments cannot be on the same line as a key-value pair.</span></span> <span data-ttu-id="e3c76-156">`ConvertFrom-StringData` ignorerar kommentarer på en rad.</span><span class="sxs-lookup"><span data-stu-id="e3c76-156">`ConvertFrom-StringData` ignores single-line comments.</span></span> <span data-ttu-id="e3c76-157">`#`Specialtecknet måste vara det första icke-blank tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="e3c76-157">The `#` character must be the first non-whitespace character on the line.</span></span> <span data-ttu-id="e3c76-158">Alla tecken på raden efter `#` ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e3c76-158">All characters on the line after the `#` are ignored.</span></span> <span data-ttu-id="e3c76-159">Kommentarerna ingår inte i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="e3c76-159">The comments are not included in the hash table.</span></span>

<span data-ttu-id="e3c76-160">En här-sträng är en sträng som består av en eller flera rader.</span><span class="sxs-lookup"><span data-stu-id="e3c76-160">A here-string is a string consisting of one or more lines.</span></span> <span data-ttu-id="e3c76-161">Citat tecken inom denna-sträng tolkas bokstavligen som en del av sträng data.</span><span class="sxs-lookup"><span data-stu-id="e3c76-161">Quotation marks within the here-string are interpreted literally as part of the string data.</span></span> <span data-ttu-id="e3c76-162">Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="e3c76-162">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="e3c76-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e3c76-163">CommonParameters</span></span>

<span data-ttu-id="e3c76-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e3c76-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e3c76-165">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="e3c76-165">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="e3c76-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="e3c76-166">INPUTS</span></span>

### <span data-ttu-id="e3c76-167">System. String</span><span class="sxs-lookup"><span data-stu-id="e3c76-167">System.String</span></span>

<span data-ttu-id="e3c76-168">Du kan skicka vidare en sträng som innehåller ett nyckel/värde-par till `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="e3c76-168">You can pipe a string containing a key-value pair to `ConvertFrom-StringData`.</span></span>

## <span data-ttu-id="e3c76-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e3c76-169">OUTPUTS</span></span>

### <span data-ttu-id="e3c76-170">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="e3c76-170">System.Collections.Hashtable</span></span>

<span data-ttu-id="e3c76-171">Denna cmdlet returnerar en hash-tabell som den skapar från nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="e3c76-171">This cmdlet returns a hash table that it creates from the key-value pairs.</span></span>

## <span data-ttu-id="e3c76-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e3c76-172">NOTES</span></span>

<span data-ttu-id="e3c76-173">En här-sträng är en sträng som består av en eller flera rader inom vilka citat tecken tolkas bokstavligen.</span><span class="sxs-lookup"><span data-stu-id="e3c76-173">A here-string is a string consisting of one or more lines within which quotation marks are interpreted literally.</span></span>

<span data-ttu-id="e3c76-174">Denna cmdlet kan vara användbar i skript som visar användar meddelanden på flera talade språk.</span><span class="sxs-lookup"><span data-stu-id="e3c76-174">This cmdlet can be useful in scripts that display user messages in multiple spoken languages.</span></span> <span data-ttu-id="e3c76-175">Du kan använda hash-tabeller i lexikonet för att isolera text strängar från kod, till exempel i resursfiler, och för att formatera text strängarna för användning i översättnings verktyg.</span><span class="sxs-lookup"><span data-stu-id="e3c76-175">You can use the dictionary-style hash tables to isolate text strings from code, such as in resource files, and to format the text strings for use in translation tools.</span></span>

## <span data-ttu-id="e3c76-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e3c76-176">RELATED LINKS</span></span>
