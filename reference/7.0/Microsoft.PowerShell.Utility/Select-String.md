---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 7c614314eb13ea484f5a0a5ade36aabdd6afdf58
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269264"
---
# <span data-ttu-id="17854-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="17854-103">Select-String</span></span>

## <span data-ttu-id="17854-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="17854-104">SYNOPSIS</span></span>
<span data-ttu-id="17854-105">Söker efter text i strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="17854-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="17854-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17854-106">SYNTAX</span></span>

### <span data-ttu-id="17854-107">Fil (standard)</span><span class="sxs-lookup"><span data-stu-id="17854-107">File (Default)</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17854-108">ObjectRaw</span><span class="sxs-lookup"><span data-stu-id="17854-108">ObjectRaw</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17854-109">Objekt</span><span class="sxs-lookup"><span data-stu-id="17854-109">Object</span></span>

```
Select-String [-Culture <String>] -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17854-110">FileRaw</span><span class="sxs-lookup"><span data-stu-id="17854-110">FileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> [-Path] <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17854-111">LiteralFileRaw</span><span class="sxs-lookup"><span data-stu-id="17854-111">LiteralFileRaw</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> -Raw [-SimpleMatch]
 [-CaseSensitive] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch]
 [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="17854-112">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="17854-112">LiteralFile</span></span>

```
Select-String [-Culture <String>] [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch]
 [-CaseSensitive] [-Quiet] [-List] [-NoEmphasis] [-Include <String[]>] [-Exclude <String[]>]
 [-NotMatch] [-AllMatches] [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="17854-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="17854-113">DESCRIPTION</span></span>

<span data-ttu-id="17854-114">`Select-String`Cmdleten söker efter text-och text mönster i inmatade strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="17854-114">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="17854-115">Du kan använda `Select-String` liknande **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="17854-115">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="17854-116">`Select-String` baseras på text rader.</span><span class="sxs-lookup"><span data-stu-id="17854-116">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="17854-117">Som standard `Select-String` söker den första matchningen i varje rad, och för varje matchning visas fil namnet, rad numret och all text på raden som innehåller matchningen.</span><span class="sxs-lookup"><span data-stu-id="17854-117">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="17854-118">Du kan direkt `Select-String` hitta flera matchningar per rad, Visa text före och efter matchningen eller visa ett booleskt värde (sant eller falskt) som anger om en matchning hittas.</span><span class="sxs-lookup"><span data-stu-id="17854-118">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="17854-119">`Select-String` använder reguljär uttrycks matchning, men den kan också utföra en matchning som söker i indatamängden för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="17854-119">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="17854-120">`Select-String` kan visa alla text matchningar eller stoppa efter den första matchningen i varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="17854-120">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="17854-121">`Select-String` kan användas för att visa all text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-121">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="17854-122">Du kan också ange om `Select-String` du vill att en viss tecken kodning ska förväntas, till exempel när du söker filer med Unicode-text.</span><span class="sxs-lookup"><span data-stu-id="17854-122">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="17854-123">`Select-String` använder byte-order-markering (BOM) för att identifiera filens kodnings format.</span><span class="sxs-lookup"><span data-stu-id="17854-123">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="17854-124">Om filen saknar struktur antas kodningen vara UTF8.</span><span class="sxs-lookup"><span data-stu-id="17854-124">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="17854-125">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="17854-125">EXAMPLES</span></span>

### <span data-ttu-id="17854-126">Exempel 1: hitta en Skift läges känslig matchning</span><span class="sxs-lookup"><span data-stu-id="17854-126">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="17854-127">I det här exemplet är Skift läges känslig matchning av texten som skickades pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17854-127">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="17854-128">Text strängarna **Hello** och **Hej** skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17854-128">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="17854-129">`Select-String` använder **Pattern** -parametern för att ange **Hej**.</span><span class="sxs-lookup"><span data-stu-id="17854-129">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="17854-130">Parametern **caseSensitive** anger att Skift läget endast måste matcha versaler och gemener.</span><span class="sxs-lookup"><span data-stu-id="17854-130">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="17854-131">**SimpleMatch** är en valfri parameter och anger att strängen i mönstret inte tolkas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="17854-131">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="17854-132">`Select-String` visar **Hello** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-132">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="17854-133">Exempel 2: Sök efter matchningar i textfiler</span><span class="sxs-lookup"><span data-stu-id="17854-133">Example 2: Find matches in text files</span></span>

<span data-ttu-id="17854-134">Det här kommandot söker igenom alla filer med `.txt` fil namns tillägget i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-134">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="17854-135">I utdata visas raderna i de filer som innehåller den angivna strängen.</span><span class="sxs-lookup"><span data-stu-id="17854-135">The output displays the lines in those files that include the specified string.</span></span>

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

<span data-ttu-id="17854-136">I det här exemplet `Get-Alias` och `Get-Command` används med `Out-File` cmdleten för att skapa två textfiler i den aktuella katalogen **Alias.txt** och **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="17854-136">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="17854-137">`Select-String` använder parametern **Path** med jokertecknet asterisk ( `*` ) för att söka igenom alla filer i den aktuella katalogen med fil namns tillägget `.txt` .</span><span class="sxs-lookup"><span data-stu-id="17854-137">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="17854-138">Parametern **Pattern** anger texten som ska matcha **Get-**.</span><span class="sxs-lookup"><span data-stu-id="17854-138">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="17854-139">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-139">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="17854-140">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="17854-140">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="17854-141">Exempel 3: hitta en mönster matchning</span><span class="sxs-lookup"><span data-stu-id="17854-141">Example 3: Find a pattern match</span></span>

<span data-ttu-id="17854-142">I det här exemplet genomsöks flera filer för att hitta matchningar för det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-142">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="17854-143">Mönstret använder en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="17854-143">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="17854-144">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17854-144">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="17854-145">`Select-String`Cmdleten använder två parametrar, **sökväg** och **mönster**.</span><span class="sxs-lookup"><span data-stu-id="17854-145">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="17854-146">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-146">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="17854-147">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-147">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="17854-148">**Pattern** -parametern anger att matchar ett frågetecken ( `?` ) i varje fil.</span><span class="sxs-lookup"><span data-stu-id="17854-148">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="17854-149">Ett omvänt snedstreck ( `\` ) används som ett escape-tecken och är nödvändigt eftersom frågetecknet ( `?` ) är en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="17854-149">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="17854-150">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-150">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="17854-151">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="17854-151">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="17854-152">Exempel 4: Använd Select-String i en funktion</span><span class="sxs-lookup"><span data-stu-id="17854-152">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="17854-153">I det här exemplet skapas en funktion för att söka efter ett mönster i PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="17854-153">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="17854-154">I det här exemplet finns bara funktionen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="17854-154">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="17854-155">När PowerShell-sessionen stängs tas funktionen bort.</span><span class="sxs-lookup"><span data-stu-id="17854-155">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="17854-156">Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="17854-156">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

<span data-ttu-id="17854-157">Funktionen skapas på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="17854-157">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="17854-158">`Function`Kommandot använder namns **ökning-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="17854-158">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="17854-159">Tryck på **RETUR** för att börja lägga till instruktioner till funktionen.</span><span class="sxs-lookup"><span data-stu-id="17854-159">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="17854-160">I `>>` prompten lägger du till varje instruktion och trycker på **RETUR** som visas i exemplet.</span><span class="sxs-lookup"><span data-stu-id="17854-160">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="17854-161">När du har lagt till en avslutande hak paren tes returneras en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="17854-161">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="17854-162">Funktionen innehåller två kommandon.</span><span class="sxs-lookup"><span data-stu-id="17854-162">The function contains two commands.</span></span> <span data-ttu-id="17854-163">`$PSHelp`Variabeln lagrar sökvägen till PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="17854-163">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="17854-164">`$PSHOME` är PowerShell-installationsmappen med under katalogen **en-US** som anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-164">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="17854-165">`Select-String`Kommandot i funktionen använder parametrarna **Path** och **pattern** .</span><span class="sxs-lookup"><span data-stu-id="17854-165">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="17854-166">Parametern **Path** använder `$PSHelp` variabeln för att hämta sökvägen.</span><span class="sxs-lookup"><span data-stu-id="17854-166">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="17854-167">Parametern **Pattern** använder sträng **About_** som Sök villkor.</span><span class="sxs-lookup"><span data-stu-id="17854-167">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="17854-168">Om du vill köra funktionen skriver du `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="17854-168">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="17854-169">Funktionens `Select-String` kommando visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-169">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="17854-170">Exempel 5: Sök efter en sträng i en händelse logg i Windows</span><span class="sxs-lookup"><span data-stu-id="17854-170">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="17854-171">Det här exemplet söker efter en sträng i en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="17854-171">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="17854-172">Variabeln `$_` representerar det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="17854-172">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="17854-173">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="17854-173">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="17854-174">`Get-WinEvent`Cmdleten använder parametern **LogName** för att ange program loggen.</span><span class="sxs-lookup"><span data-stu-id="17854-174">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="17854-175">Parametern **MaxEvents** hämtar de senaste 50 händelserna från loggen.</span><span class="sxs-lookup"><span data-stu-id="17854-175">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="17854-176">Logg innehållet lagras i variabeln med namnet `$Events` .</span><span class="sxs-lookup"><span data-stu-id="17854-176">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="17854-177">`$Events`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17854-177">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="17854-178">`Select-String` använder parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="17854-178">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="17854-179">`$_`Variabeln representerar det aktuella objektet och `message` är en egenskap för händelsen.</span><span class="sxs-lookup"><span data-stu-id="17854-179">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="17854-180">**Pattern** -parametern anger att strängen **misslyckades** och söker efter matchningar i `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="17854-180">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="17854-181">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-181">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="17854-182">Exempel 6: hitta en sträng i under kataloger</span><span class="sxs-lookup"><span data-stu-id="17854-182">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="17854-183">I det här exemplet genomsöks en katalog och alla dess under kataloger för en speciell text sträng.</span><span class="sxs-lookup"><span data-stu-id="17854-183">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="17854-184">`Get-ChildItem` använder parametern **Path** för att ange **C:\Windows\System32 \* . txt**.</span><span class="sxs-lookup"><span data-stu-id="17854-184">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="17854-185">Parametern **rekursivt** innehåller under kataloger.</span><span class="sxs-lookup"><span data-stu-id="17854-185">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="17854-186">Objekten skickas ned pipelinen till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="17854-186">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="17854-187">`Select-String` använder **mönster** parametern och anger strängen **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="17854-187">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="17854-188">Parametern **caseSensitive** används för att matcha det exakta Skift läget för strängen.</span><span class="sxs-lookup"><span data-stu-id="17854-188">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="17854-189">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="17854-189">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="17854-190">Beroende på dina behörigheter kan du se **åtkomst nekade** meddelanden i utdata.</span><span class="sxs-lookup"><span data-stu-id="17854-190">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="17854-191">Exempel 7: hitta strängar som inte matchar ett mönster</span><span class="sxs-lookup"><span data-stu-id="17854-191">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="17854-192">Det här exemplet visar hur du kan utesluta rader med data som inte matchar ett mönster.</span><span class="sxs-lookup"><span data-stu-id="17854-192">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="17854-193">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-193">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="17854-194">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="17854-194">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="17854-195">Parametern **Pattern** anger **Get** och **set** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="17854-195">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="17854-196">**NotMatch** -parametern utesluter **Get** och **set** från resultaten.</span><span class="sxs-lookup"><span data-stu-id="17854-196">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="17854-197">`Select-String` visar utdata i PowerShell-konsolen som inte innehåller **Get** eller **set**.</span><span class="sxs-lookup"><span data-stu-id="17854-197">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="17854-198">Exempel 8: Hitta rader före och efter en matchning</span><span class="sxs-lookup"><span data-stu-id="17854-198">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="17854-199">Det här exemplet visar hur du hämtar raderna före och efter det matchade mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-199">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

<span data-ttu-id="17854-200">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-200">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="17854-201">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="17854-201">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="17854-202">Parametern **Pattern** anger **Get-Computer** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="17854-202">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="17854-203">**Kontext** parametern använder två värden, före och efter, och markerar mönster matchningar i utdata med en vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="17854-203">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="17854-204">**Kontext** parametern matar ut de två raderna före den första mönster matchningen och tre rader efter den sista mönster matchningen.</span><span class="sxs-lookup"><span data-stu-id="17854-204">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="17854-205">Exempel 9: Sök efter alla mönster matchningar</span><span class="sxs-lookup"><span data-stu-id="17854-205">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="17854-206">I det här exemplet visas hur **AllMatches** -parametern hittar varje mönster matchning i en rad med text.</span><span class="sxs-lookup"><span data-stu-id="17854-206">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="17854-207">Som standard `Select-String` söker bara den första förekomsten av ett mönster i en textrad.</span><span class="sxs-lookup"><span data-stu-id="17854-207">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="17854-208">I det här exemplet används objekt egenskaper som hittas med `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17854-208">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

<span data-ttu-id="17854-209">`Get-ChildItem`Cmdleten använder parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="17854-209">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="17854-210">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-210">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="17854-211">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-211">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="17854-212">`Get-ChildItem`Objekten lagras i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="17854-212">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="17854-213">`$A`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="17854-213">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="17854-214">`Select-String` använder **Pattern** -parametern för att söka igenom varje fil för sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="17854-214">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="17854-215">På kommando raden för PowerShell `$A` visas variabel innehållet.</span><span class="sxs-lookup"><span data-stu-id="17854-215">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="17854-216">Det finns en rad som innehåller två förekomster av sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="17854-216">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="17854-217">`$A.Matches`Egenskapen visar den första förekomsten av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="17854-217">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="17854-218">`$A.Matches.Length`Egenskapen räknar den första förekomsten av mönstret **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="17854-218">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="17854-219">`$B`Variabeln använder samma `Get-ChildItem` `Select-String` cmdletar, men lägger till parametern **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="17854-219">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="17854-220">**AllMatches** hittar varje förekomst av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="17854-220">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="17854-221">De objekt som lagras i `$A` `$B` variablerna och är identiska.</span><span class="sxs-lookup"><span data-stu-id="17854-221">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="17854-222">`$B.Matches.Length`Egenskapen ökar eftersom alla förekomster av mönstret **PowerShell** räknas för varje rad.</span><span class="sxs-lookup"><span data-stu-id="17854-222">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="17854-223">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="17854-223">PARAMETERS</span></span>

### <span data-ttu-id="17854-224">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="17854-224">-AllMatches</span></span>

<span data-ttu-id="17854-225">Anger att cmdleten söker efter fler än en matchning i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="17854-225">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="17854-226">Utan den här parametern `Select-String` hittar bara den första matchningen i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="17854-226">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="17854-227">När `Select-String` söker efter fler än en matchning i en rad med text, genererar den fortfarande bara ett **MatchInfo** -objekt för raden, men egenskapen **matchar** för objektet innehåller alla matchningar.</span><span class="sxs-lookup"><span data-stu-id="17854-227">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="17854-228">Den här parametern ignoreras när den används i kombination med parametern **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="17854-228">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="17854-229">Om du vill returnera alla matchningar och mönstret som du söker efter innehåller tecken för reguljära uttryck, måste du undanta dessa tecken i stället för att använda **SimpleMatch**.</span><span class="sxs-lookup"><span data-stu-id="17854-229">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="17854-230">Mer information om hur du hoppar över reguljära uttryck finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="17854-230">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="17854-231">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="17854-231">-CaseSensitive</span></span>

<span data-ttu-id="17854-232">Anger att cmdleten matchar är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="17854-232">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="17854-233">Som standard är matchningar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="17854-233">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="17854-234">– Kontext</span><span class="sxs-lookup"><span data-stu-id="17854-234">-Context</span></span>

<span data-ttu-id="17854-235">Fångar upp det angivna antalet rader före och efter den rad som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-235">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="17854-236">Om du anger ett tal som värde för den här parametern, bestämmer den siffran antalet rader som fångats före och efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="17854-236">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="17854-237">Om du anger två tal som värde bestämmer det första talet antalet rader före matchningen och det andra talet bestämmer antalet rader efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="17854-237">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="17854-238">Till exempel `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="17854-238">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="17854-239">I standard visningen visas rader med en matchning med en höger vinkel paren tes ( `>` ) (ASCII 62) i den första kolumnen i visningen.</span><span class="sxs-lookup"><span data-stu-id="17854-239">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="17854-240">Omarkerade rader är kontexten.</span><span class="sxs-lookup"><span data-stu-id="17854-240">Unmarked lines are the context.</span></span>

<span data-ttu-id="17854-241">**Kontext** parametern ändrar inte antalet objekt som genereras av `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="17854-241">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="17854-242">`Select-String` genererar ett [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -objekt för varje matchning.</span><span class="sxs-lookup"><span data-stu-id="17854-242">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="17854-243">Kontexten lagras som en sträng mat ris i objektets **kontext** egenskap.</span><span class="sxs-lookup"><span data-stu-id="17854-243">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="17854-244">När utdata från ett `Select-String` kommando skickas ned pipelinen till ett annat `Select-String` kommando, söker kommandot ta emot bara texten på den matchade raden.</span><span class="sxs-lookup"><span data-stu-id="17854-244">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="17854-245">Den matchade raden är värdet för egenskapen **line** för **MatchInfo** -objektet, inte texten i Sammanhangs linjerna.</span><span class="sxs-lookup"><span data-stu-id="17854-245">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="17854-246">Därför är **kontext** parametern inte giltig i mottagnings `Select-String` kommandot.</span><span class="sxs-lookup"><span data-stu-id="17854-246">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="17854-247">När kontexten innehåller en matchning inkluderar **MatchInfo** -objektet för varje matchning alla kontext linjer, men de överlappande linjerna visas bara en gång i visningen.</span><span class="sxs-lookup"><span data-stu-id="17854-247">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-248">– Kultur</span><span class="sxs-lookup"><span data-stu-id="17854-248">-Culture</span></span>

<span data-ttu-id="17854-249">Anger ett kultur namn som matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-249">Specifies a culture name to match the specified pattern.</span></span> <span data-ttu-id="17854-250">**Kultur** parametern måste användas med parametern **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="17854-250">The **Culture** parameter must be used with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="17854-251">Standard beteendet använder kulturen för den aktuella PowerShell-körnings utrymme (session).</span><span class="sxs-lookup"><span data-stu-id="17854-251">The default behavior uses the culture of the current PowerShell runspace (session).</span></span>

<span data-ttu-id="17854-252">Om du vill hämta en lista över alla kulturer som stöds använder du `Get-Culture -ListAvailable` kommandot.</span><span class="sxs-lookup"><span data-stu-id="17854-252">To get a list of all supported cultures, use `Get-Culture -ListAvailable` command.</span></span>

<span data-ttu-id="17854-253">Dessutom accepterar den här parametern följande argument:</span><span class="sxs-lookup"><span data-stu-id="17854-253">In addition, this parameter accepts the following arguments:</span></span>

- <span data-ttu-id="17854-254">CurrentCulture, som är standard.</span><span class="sxs-lookup"><span data-stu-id="17854-254">CurrentCulture, that is default;</span></span>
- <span data-ttu-id="17854-255">Ordnings tal, som är icke-språklig binär jämförelse;</span><span class="sxs-lookup"><span data-stu-id="17854-255">Ordinal, that is non-linguistic binary comparison;</span></span>
- <span data-ttu-id="17854-256">Invariant, som är kultur oberoende jämförelse.</span><span class="sxs-lookup"><span data-stu-id="17854-256">Invariant, that is culture independent comparison.</span></span>

<span data-ttu-id="17854-257">Med `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` kommandot får du snabbast binär jämförelse.</span><span class="sxs-lookup"><span data-stu-id="17854-257">With `Select-String -Culture Ordinal -CaseSensitive -SimpleMatch` command you gets fastest binary comparison.</span></span>

<span data-ttu-id="17854-258">**Kultur** parametern använder tabbtangenten för att bläddra igenom listan med argument som anger tillgängliga kulturer.</span><span class="sxs-lookup"><span data-stu-id="17854-258">The **Culture** parameter uses tab completion to scroll through the list of arguments that specify the available cultures.</span></span> <span data-ttu-id="17854-259">Om du vill visa alla tillgängliga argument använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="17854-259">To list all available arguments, use the following command:</span></span>

`(Get-Command Select-String).Parameters.Culture.Attributes.ValidValues`

<span data-ttu-id="17854-260">Mer information om .NET CultureInfo.Name-egenskapen finns i [CultureInfo.name](/dotnet/api//system.globalization.cultureinfo.name).</span><span class="sxs-lookup"><span data-stu-id="17854-260">For more information about .NET CultureInfo.Name property, see [CultureInfo.Name](/dotnet/api//system.globalization.cultureinfo.name).</span></span>

<span data-ttu-id="17854-261">**Kultur** parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="17854-261">The **Culture** parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Culture of the current PowerShell session
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-262">-Encoding</span><span class="sxs-lookup"><span data-stu-id="17854-262">-Encoding</span></span>

<span data-ttu-id="17854-263">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="17854-263">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="17854-264">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="17854-264">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="17854-265">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="17854-265">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="17854-266">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="17854-266">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="17854-267">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="17854-267">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="17854-268">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="17854-268">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="17854-269">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="17854-269">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="17854-270">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="17854-270">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="17854-271">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="17854-271">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="17854-272">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="17854-272">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="17854-273">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="17854-273">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="17854-274">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="17854-274">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="17854-275">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="17854-275">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="17854-276">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="17854-276">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-277">-Undanta</span><span class="sxs-lookup"><span data-stu-id="17854-277">-Exclude</span></span>

<span data-ttu-id="17854-278">Uteslut de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="17854-278">Exclude the specified items.</span></span> <span data-ttu-id="17854-279">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="17854-279">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="17854-280">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="17854-280">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="17854-281">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="17854-281">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17854-282">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="17854-282">-Include</span></span>

<span data-ttu-id="17854-283">Innehåller de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="17854-283">Includes the specified items.</span></span> <span data-ttu-id="17854-284">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="17854-284">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="17854-285">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="17854-285">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="17854-286">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="17854-286">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17854-287">– InputObject</span><span class="sxs-lookup"><span data-stu-id="17854-287">-InputObject</span></span>

<span data-ttu-id="17854-288">Anger den text som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="17854-288">Specifies the text to be searched.</span></span> <span data-ttu-id="17854-289">Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar texten.</span><span class="sxs-lookup"><span data-stu-id="17854-289">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="17854-290">Att använda parametern **InputObject** är inte detsamma som att skicka strängar nedåt i pipeline till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="17854-290">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="17854-291">När du rör fler än en sträng till `Select-String` cmdleten söker den efter den angivna texten i varje sträng och returnerar varje sträng som innehåller Sök texten.</span><span class="sxs-lookup"><span data-stu-id="17854-291">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="17854-292">När du använder parametern **InputObject** för att skicka en samling med strängar, `Select-String` behandlar samlingen som en enda kombinerad sträng.</span><span class="sxs-lookup"><span data-stu-id="17854-292">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="17854-293">`Select-String` Returnerar strängarna som en enhet om Sök texten hittas i en sträng.</span><span class="sxs-lookup"><span data-stu-id="17854-293">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ObjectRaw, Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17854-294">– Lista</span><span class="sxs-lookup"><span data-stu-id="17854-294">-List</span></span>

<span data-ttu-id="17854-295">Endast den första instansen av matchande text returneras från varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="17854-295">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="17854-296">Detta är det mest effektiva sättet att hämta en lista över filer som har innehåll som matchar det reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="17854-296">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="17854-297">Som standard `Select-String` returnerar ett **MatchInfo** -objekt för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="17854-297">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="17854-298">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="17854-298">-LiteralPath</span></span>

<span data-ttu-id="17854-299">Anger sökvägen till de filer som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="17854-299">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="17854-300">Värdet för parametern **LiteralPath** används exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="17854-300">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="17854-301">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="17854-301">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="17854-302">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="17854-302">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="17854-303">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="17854-303">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="17854-304">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="17854-304">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFileRaw, LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="17854-305">-Nobetoning</span><span class="sxs-lookup"><span data-stu-id="17854-305">-NoEmphasis</span></span>

<span data-ttu-id="17854-306">Som standard `Select-String` markeras den sträng som matchar det mönster du sökte efter med **Pattern** -parametern.</span><span class="sxs-lookup"><span data-stu-id="17854-306">By default, `Select-String` highlights the string that matches the pattern you searched for with the **Pattern** parameter.</span></span> <span data-ttu-id="17854-307">Parametern **nobetoning** inaktiverar markeringen.</span><span class="sxs-lookup"><span data-stu-id="17854-307">The **NoEmphasis** parameter disables the highlighting.</span></span>

<span data-ttu-id="17854-308">Betoningen använder negativa färger baserat på PowerShell-bakgrunden och text färgerna.</span><span class="sxs-lookup"><span data-stu-id="17854-308">The emphasis uses negative colors based on your PowerShell background and text colors.</span></span> <span data-ttu-id="17854-309">Om dina PowerShell-färger till exempel är svarta bakgrunder med vit text.</span><span class="sxs-lookup"><span data-stu-id="17854-309">For example, if your PowerShell colors are a black background with white text.</span></span> <span data-ttu-id="17854-310">Betoningen är en vit bakgrund med svart text.</span><span class="sxs-lookup"><span data-stu-id="17854-310">The emphasis is a white background with black text.</span></span>

<span data-ttu-id="17854-311">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="17854-311">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="17854-312">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="17854-312">-NotMatch</span></span>

<span data-ttu-id="17854-313">Parametern **NotMatch** söker efter text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-313">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="17854-314">-Path</span><span class="sxs-lookup"><span data-stu-id="17854-314">-Path</span></span>

<span data-ttu-id="17854-315">Anger sökvägen till filerna som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="17854-315">Specifies the path to the files to search.</span></span> <span data-ttu-id="17854-316">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="17854-316">Wildcards are permitted.</span></span> <span data-ttu-id="17854-317">Standard platsen är den lokala katalogen.</span><span class="sxs-lookup"><span data-stu-id="17854-317">The default location is the local directory.</span></span>

<span data-ttu-id="17854-318">Ange filer i katalogen, till exempel `log1.txt` , `*.doc` eller `*.*` .</span><span class="sxs-lookup"><span data-stu-id="17854-318">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="17854-319">Om du bara anger en katalog Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="17854-319">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File, FileRaw
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="17854-320">– Mönster</span><span class="sxs-lookup"><span data-stu-id="17854-320">-Pattern</span></span>

<span data-ttu-id="17854-321">Anger vilken text som ska finnas på varje rad.</span><span class="sxs-lookup"><span data-stu-id="17854-321">Specifies the text to find on each line.</span></span> <span data-ttu-id="17854-322">Pattern-värdet behandlas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="17854-322">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="17854-323">Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17854-323">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-324">– Tyst</span><span class="sxs-lookup"><span data-stu-id="17854-324">-Quiet</span></span>

<span data-ttu-id="17854-325">Anger att cmdleten returnerar ett booleskt värde (sant eller falskt) i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="17854-325">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="17854-326">Värdet är true om mönstret hittas. annars är värdet FALSKT.</span><span class="sxs-lookup"><span data-stu-id="17854-326">The value is True if the pattern is found; otherwise the value is False.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File, Object, LiteralFile
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-327">– RAW</span><span class="sxs-lookup"><span data-stu-id="17854-327">-Raw</span></span>

<span data-ttu-id="17854-328">Gör att cmdleten bara matar ut de matchande strängarna, i stället för **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="17854-328">Causes the cmdlet to output only the matching strings, rather than **MatchInfo** objects.</span></span> <span data-ttu-id="17854-329">Detta är resultatet som är mest likt Unix **grep** -eller Windows **findstr.exe** -kommandon.</span><span class="sxs-lookup"><span data-stu-id="17854-329">This is the results in behavior that's the most similar to the Unix **grep** or Windows **findstr.exe** commands.</span></span>

<span data-ttu-id="17854-330">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="17854-330">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ObjectRaw, FileRaw, LiteralFileRaw
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="17854-331">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="17854-331">-SimpleMatch</span></span>

<span data-ttu-id="17854-332">Anger att cmdleten använder en enkel matchning i stället för en reguljär uttrycks matchning.</span><span class="sxs-lookup"><span data-stu-id="17854-332">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="17854-333">I en enkel matchning `Select-String` söker efter texten i **mönster** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="17854-333">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="17854-334">Den tolkar inte värdet för **Pattern** -parametern som en reguljär uttrycks instruktion.</span><span class="sxs-lookup"><span data-stu-id="17854-334">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="17854-335">Även om **SimpleMatch** används är egenskapen **matchar** för det **MatchInfo** -objekt som returnerades tomt.</span><span class="sxs-lookup"><span data-stu-id="17854-335">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="17854-336">När den här parametern används med parametern **AllMatches** ignoreras **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="17854-336">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="17854-337">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17854-337">CommonParameters</span></span>

<span data-ttu-id="17854-338">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17854-338">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17854-339">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="17854-339">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17854-340">INDATA</span><span class="sxs-lookup"><span data-stu-id="17854-340">INPUTS</span></span>

### <span data-ttu-id="17854-341">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="17854-341">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="17854-342">Du kan skicka vidare alla objekt som har en **toString** -Metod till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="17854-342">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="17854-343">UTDATA</span><span class="sxs-lookup"><span data-stu-id="17854-343">OUTPUTS</span></span>

### <span data-ttu-id="17854-344">Microsoft. PowerShell. commands. MatchInfo, system. Boolean, system. String</span><span class="sxs-lookup"><span data-stu-id="17854-344">Microsoft.PowerShell.Commands.MatchInfo, System.Boolean, System.String</span></span>

<span data-ttu-id="17854-345">Som standard är utdata en uppsättning **MatchInfo** -objekt med en för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="17854-345">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="17854-346">Om du använder parametern **quiet** är utdata ett **booleskt** värde som anger om mönstret hittades.</span><span class="sxs-lookup"><span data-stu-id="17854-346">If you use the **Quiet** parameter, the output is a **Boolean** value indicating whether the pattern was found.</span></span>
<span data-ttu-id="17854-347">Om du använder en **RAW** -parameter är utdata en uppsättning **sträng** objekt som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="17854-347">If you use the **Raw** parameter, the output is a set of **String** objects that match the pattern.</span></span>

## <span data-ttu-id="17854-348">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="17854-348">NOTES</span></span>

<span data-ttu-id="17854-349">`Select-String` liknar **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="17854-349">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="17854-350">**SLS** -aliaset för `Select-String` cmdleten introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="17854-350">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="17854-351">Enligt [godkända verb för PowerShell-kommandon](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)är det officiella aliaset för `Select-*` cmdlets `sc` , inte `sl` .</span><span class="sxs-lookup"><span data-stu-id="17854-351">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="17854-352">Därför bör rätt alias för `Select-String` vara `scs` , inte `sls` .</span><span class="sxs-lookup"><span data-stu-id="17854-352">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="17854-353">Detta är ett undantag till den här regeln.</span><span class="sxs-lookup"><span data-stu-id="17854-353">This is an exception to this rule.</span></span>

<span data-ttu-id="17854-354">Om du vill använda `Select-String` anger du den text som du vill hitta som värde för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="17854-354">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="17854-355">Om du vill ange vilken text som ska genomsökas använder du följande kriterier:</span><span class="sxs-lookup"><span data-stu-id="17854-355">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="17854-356">Skriv texten i en Citerad sträng och koppla den sedan till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="17854-356">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="17854-357">Lagra en text sträng i en variabel och ange sedan variabeln som värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="17854-357">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="17854-358">Om texten lagras i filer använder du parametern **Path** för att ange sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="17854-358">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="17854-359">Som standard `Select-String` tolkar värdet för **Pattern** -parametern som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="17854-359">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="17854-360">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="17854-360">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="17854-361">Du kan använda parametern **SimpleMatch** för att åsidosätta den reguljära uttrycks matchningen.</span><span class="sxs-lookup"><span data-stu-id="17854-361">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="17854-362">Parametern **SimpleMatch** hittar förekomster av värdet för **Pattern** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="17854-362">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="17854-363">Standardutdata för `Select-String` är ett **MatchInfo** -objekt, som innehåller detaljerad information om matchningarna.</span><span class="sxs-lookup"><span data-stu-id="17854-363">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="17854-364">Informationen i objektet är användbar när du söker efter text i filer, eftersom **MatchInfo** -objekt har egenskaper som **fil namn** och **rad**.</span><span class="sxs-lookup"><span data-stu-id="17854-364">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="17854-365">När indata inte är från filen är värdet för dessa parametrar **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="17854-365">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="17854-366">Om du inte behöver informationen i **MatchInfo** -objektet använder du parametern **quiet** .</span><span class="sxs-lookup"><span data-stu-id="17854-366">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="17854-367">Parametern **quiet** returnerar ett booleskt värde (sant eller falskt) för att indikera om en matchning hittades i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="17854-367">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="17854-368">När du matchar fraser `Select-String` använder den aktuella kulturen som har angetts för systemet.</span><span class="sxs-lookup"><span data-stu-id="17854-368">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="17854-369">Använd cmdleten för att hitta den aktuella kulturen `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="17854-369">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="17854-370">Om du vill hitta egenskaperna för ett **MatchInfo** -objekt skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="17854-370">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="17854-371">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="17854-371">RELATED LINKS</span></span>

[<span data-ttu-id="17854-372">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="17854-372">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="17854-373">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="17854-373">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="17854-374">about_Functions</span><span class="sxs-lookup"><span data-stu-id="17854-374">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="17854-375">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="17854-375">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="17854-376">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="17854-376">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="17854-377">Get-alias</span><span class="sxs-lookup"><span data-stu-id="17854-377">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="17854-378">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="17854-378">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="17854-379">Get-Command</span><span class="sxs-lookup"><span data-stu-id="17854-379">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="17854-380">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="17854-380">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="17854-381">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="17854-381">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="17854-382">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="17854-382">Out-File</span></span>](Out-File.md)
