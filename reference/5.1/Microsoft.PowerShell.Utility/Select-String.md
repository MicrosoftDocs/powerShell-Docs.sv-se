---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 95601a4f5f42700c4de7d6ad721ee898b22bab84
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269265"
---
# <span data-ttu-id="1ef85-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="1ef85-103">Select-String</span></span>

## <span data-ttu-id="1ef85-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1ef85-104">SYNOPSIS</span></span>
<span data-ttu-id="1ef85-105">Söker efter text i strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="1ef85-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="1ef85-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ef85-106">SYNTAX</span></span>

### <span data-ttu-id="1ef85-107">Fil (standard)</span><span class="sxs-lookup"><span data-stu-id="1ef85-107">File (Default)</span></span>

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="1ef85-108">Objekt</span><span class="sxs-lookup"><span data-stu-id="1ef85-108">Object</span></span>

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="1ef85-109">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="1ef85-109">LiteralFile</span></span>

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches] [-Encoding <String>]
 [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="1ef85-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1ef85-110">DESCRIPTION</span></span>

<span data-ttu-id="1ef85-111">`Select-String`Cmdleten söker efter text-och text mönster i inmatade strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="1ef85-111">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="1ef85-112">Du kan använda `Select-String` liknande **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="1ef85-112">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="1ef85-113">`Select-String` baseras på text rader.</span><span class="sxs-lookup"><span data-stu-id="1ef85-113">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="1ef85-114">Som standard `Select-String` söker den första matchningen i varje rad, och för varje matchning visas fil namnet, rad numret och all text på raden som innehåller matchningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-114">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="1ef85-115">Du kan direkt `Select-String` hitta flera matchningar per rad, Visa text före och efter matchningen eller visa ett booleskt värde (sant eller falskt) som anger om en matchning hittas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-115">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="1ef85-116">`Select-String` använder reguljär uttrycks matchning, men den kan också utföra en matchning som söker i indatamängden för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="1ef85-116">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="1ef85-117">`Select-String` kan visa alla text matchningar eller stoppa efter den första matchningen i varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="1ef85-117">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="1ef85-118">`Select-String` kan användas för att visa all text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1ef85-118">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="1ef85-119">Du kan också ange om `Select-String` du vill att en viss tecken kodning ska förväntas, till exempel när du söker filer med Unicode-text.</span><span class="sxs-lookup"><span data-stu-id="1ef85-119">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="1ef85-120">`Select-String` använder byte-order-markering (BOM) för att identifiera filens kodnings format.</span><span class="sxs-lookup"><span data-stu-id="1ef85-120">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="1ef85-121">Om filen saknar struktur antas kodningen vara UTF8.</span><span class="sxs-lookup"><span data-stu-id="1ef85-121">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="1ef85-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1ef85-122">EXAMPLES</span></span>

### <span data-ttu-id="1ef85-123">Exempel 1: hitta en Skift läges känslig matchning</span><span class="sxs-lookup"><span data-stu-id="1ef85-123">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="1ef85-124">I det här exemplet är Skift läges känslig matchning av texten som skickades pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-124">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="1ef85-125">Text strängarna **Hello** och **Hej** skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-125">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="1ef85-126">`Select-String` använder **Pattern** -parametern för att ange **Hej**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-126">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="1ef85-127">Parametern **caseSensitive** anger att Skift läget endast måste matcha versaler och gemener.</span><span class="sxs-lookup"><span data-stu-id="1ef85-127">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="1ef85-128">**SimpleMatch** är en valfri parameter och anger att strängen i mönstret inte tolkas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1ef85-128">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="1ef85-129">`Select-String` visar **Hello** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-129">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="1ef85-130">Exempel 2: Sök efter matchningar i textfiler</span><span class="sxs-lookup"><span data-stu-id="1ef85-130">Example 2: Find matches in text files</span></span>

<span data-ttu-id="1ef85-131">Det här kommandot söker igenom alla filer med `.txt` fil namns tillägget i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-131">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="1ef85-132">I utdata visas raderna i de filer som innehåller den angivna strängen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-132">The output displays the lines in those files that include the specified string.</span></span>

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

<span data-ttu-id="1ef85-133">I det här exemplet `Get-Alias` och `Get-Command` används med `Out-File` cmdleten för att skapa två textfiler i den aktuella katalogen **Alias.txt** och **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-133">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="1ef85-134">`Select-String` använder parametern **Path** med jokertecknet asterisk ( `*` ) för att söka igenom alla filer i den aktuella katalogen med fil namns tillägget `.txt` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-134">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="1ef85-135">Parametern **Pattern** anger texten som ska matcha **Get-**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-135">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="1ef85-136">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-136">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="1ef85-137">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1ef85-137">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="1ef85-138">Exempel 3: hitta en mönster matchning</span><span class="sxs-lookup"><span data-stu-id="1ef85-138">Example 3: Find a pattern match</span></span>

<span data-ttu-id="1ef85-139">I det här exemplet genomsöks flera filer för att hitta matchningar för det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1ef85-139">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="1ef85-140">Mönstret använder en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="1ef85-140">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="1ef85-141">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-141">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="1ef85-142">`Select-String`Cmdleten använder två parametrar, **sökväg** och **mönster**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-142">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="1ef85-143">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-143">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="1ef85-144">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-144">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="1ef85-145">**Pattern** -parametern anger att matchar ett frågetecken ( `?` ) i varje fil.</span><span class="sxs-lookup"><span data-stu-id="1ef85-145">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="1ef85-146">Ett omvänt snedstreck ( `\` ) används som ett escape-tecken och är nödvändigt eftersom frågetecknet ( `?` ) är en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="1ef85-146">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="1ef85-147">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-147">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="1ef85-148">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1ef85-148">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="1ef85-149">Exempel 4: Använd Select-String i en funktion</span><span class="sxs-lookup"><span data-stu-id="1ef85-149">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="1ef85-150">I det här exemplet skapas en funktion för att söka efter ett mönster i PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-150">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="1ef85-151">I det här exemplet finns bara funktionen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-151">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="1ef85-152">När PowerShell-sessionen stängs tas funktionen bort.</span><span class="sxs-lookup"><span data-stu-id="1ef85-152">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="1ef85-153">Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-153">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:2:   about_ActivityCommonParameters
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:31:  see about_WorkflowCommonParameters.
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:33:  about_CommonParameters.
```

<span data-ttu-id="1ef85-154">Funktionen skapas på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="1ef85-154">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="1ef85-155">`Function`Kommandot använder namns **ökning-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-155">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="1ef85-156">Tryck på **RETUR** för att börja lägga till instruktioner till funktionen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-156">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="1ef85-157">I `>>` prompten lägger du till varje instruktion och trycker på **RETUR** som visas i exemplet.</span><span class="sxs-lookup"><span data-stu-id="1ef85-157">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="1ef85-158">När du har lagt till en avslutande hak paren tes returneras en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="1ef85-158">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="1ef85-159">Funktionen innehåller två kommandon.</span><span class="sxs-lookup"><span data-stu-id="1ef85-159">The function contains two commands.</span></span> <span data-ttu-id="1ef85-160">`$PSHelp`Variabeln lagrar sökvägen till PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-160">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="1ef85-161">`$PSHOME` är PowerShell-installationsmappen med under katalogen **en-US** som anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-161">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="1ef85-162">`Select-String`Kommandot i funktionen använder parametrarna **Path** och **pattern** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-162">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="1ef85-163">Parametern **Path** använder `$PSHelp` variabeln för att hämta sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-163">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="1ef85-164">Parametern **Pattern** använder sträng **About_** som Sök villkor.</span><span class="sxs-lookup"><span data-stu-id="1ef85-164">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="1ef85-165">Om du vill köra funktionen skriver du `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-165">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="1ef85-166">Funktionens `Select-String` kommando visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-166">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="1ef85-167">Exempel 5: Sök efter en sträng i en händelse logg i Windows</span><span class="sxs-lookup"><span data-stu-id="1ef85-167">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="1ef85-168">Det här exemplet söker efter en sträng i en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="1ef85-168">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="1ef85-169">Variabeln `$_` representerar det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-169">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="1ef85-170">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="1ef85-171">`Get-WinEvent`Cmdleten använder parametern **LogName** för att ange program loggen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-171">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="1ef85-172">Parametern **MaxEvents** hämtar de senaste 50 händelserna från loggen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-172">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="1ef85-173">Logg innehållet lagras i variabeln med namnet `$Events` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-173">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="1ef85-174">`$Events`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-174">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="1ef85-175">`Select-String` använder parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-175">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="1ef85-176">`$_`Variabeln representerar det aktuella objektet och `message` är en egenskap för händelsen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-176">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="1ef85-177">**Pattern** -parametern anger att strängen **misslyckades** och söker efter matchningar i `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-177">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="1ef85-178">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-178">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="1ef85-179">Exempel 6: hitta en sträng i under kataloger</span><span class="sxs-lookup"><span data-stu-id="1ef85-179">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="1ef85-180">I det här exemplet genomsöks en katalog och alla dess under kataloger för en speciell text sträng.</span><span class="sxs-lookup"><span data-stu-id="1ef85-180">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="1ef85-181">`Get-ChildItem` använder parametern **Path** för att ange **C:\Windows\System32 \* . txt**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-181">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="1ef85-182">Parametern **rekursivt** innehåller under kataloger.</span><span class="sxs-lookup"><span data-stu-id="1ef85-182">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="1ef85-183">Objekten skickas ned pipelinen till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-183">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="1ef85-184">`Select-String` använder **mönster** parametern och anger strängen **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-184">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="1ef85-185">Parametern **caseSensitive** används för att matcha det exakta Skift läget för strängen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-185">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="1ef85-186">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-186">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="1ef85-187">Beroende på dina behörigheter kan du se **åtkomst nekade** meddelanden i utdata.</span><span class="sxs-lookup"><span data-stu-id="1ef85-187">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="1ef85-188">Exempel 7: hitta strängar som inte matchar ett mönster</span><span class="sxs-lookup"><span data-stu-id="1ef85-188">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="1ef85-189">Det här exemplet visar hur du kan utesluta rader med data som inte matchar ett mönster.</span><span class="sxs-lookup"><span data-stu-id="1ef85-189">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="1ef85-190">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-190">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="1ef85-191">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-191">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="1ef85-192">Parametern **Pattern** anger **Get** och **set** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="1ef85-192">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="1ef85-193">**NotMatch** -parametern utesluter **Get** och **set** från resultaten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-193">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="1ef85-194">`Select-String` visar utdata i PowerShell-konsolen som inte innehåller **Get** eller **set**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-194">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="1ef85-195">Exempel 8: Hitta rader före och efter en matchning</span><span class="sxs-lookup"><span data-stu-id="1ef85-195">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="1ef85-196">Det här exemplet visar hur du hämtar raderna före och efter det matchade mönstret.</span><span class="sxs-lookup"><span data-stu-id="1ef85-196">This example shows how to get the lines before and after the matched pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:1186:Cmdlet          Get-CmsMessage            3.0.0.0    Microsoft.PowerShell.Security
  Command.txt:1187:Cmdlet          Get-Command               3.0.0.0    Microsoft.PowerShell.Core
> Command.txt:1188:Cmdlet          Get-ComputerInfo          3.1.0.0    Microsoft.PowerShell.Management
> Command.txt:1189:Cmdlet          Get-ComputerRestorePoint  3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1190:Cmdlet          Get-Content               3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1191:Cmdlet          Get-ControlPanelItem      3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:1192:Cmdlet          Get-Counter               3.0.0.0    Microsoft.PowerShell.Diagnostics
```

<span data-ttu-id="1ef85-197">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-197">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="1ef85-198">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-198">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="1ef85-199">Parametern **Pattern** anger **Get-Computer** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="1ef85-199">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="1ef85-200">**Kontext** parametern använder två värden, före och efter, och markerar mönster matchningar i utdata med en vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="1ef85-200">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="1ef85-201">**Kontext** parametern matar ut de två raderna före den första mönster matchningen och tre rader efter den sista mönster matchningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-201">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="1ef85-202">Exempel 9: Sök efter alla mönster matchningar</span><span class="sxs-lookup"><span data-stu-id="1ef85-202">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="1ef85-203">I det här exemplet visas hur **AllMatches** -parametern hittar varje mönster matchning i en rad med text.</span><span class="sxs-lookup"><span data-stu-id="1ef85-203">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="1ef85-204">Som standard `Select-String` söker bara den första förekomsten av ett mönster i en textrad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-204">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="1ef85-205">I det här exemplet används objekt egenskaper som hittas med `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-205">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:5:    Describes the parameters that Windows PowerShell
C:\Windows\System32\WindowsPowerShell\v1.0\en-US\about_ActivityCommonParameters.help.txt:9:    Windows PowerShell Workflow adds the activity common

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

2073

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

2200
```

<span data-ttu-id="1ef85-206">`Get-ChildItem`Cmdleten använder parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-206">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="1ef85-207">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-207">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="1ef85-208">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-208">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="1ef85-209">`Get-ChildItem`Objekten lagras i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1ef85-209">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="1ef85-210">`$A`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-210">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="1ef85-211">`Select-String` använder **Pattern** -parametern för att söka igenom varje fil för sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-211">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="1ef85-212">På kommando raden för PowerShell `$A` visas variabel innehållet.</span><span class="sxs-lookup"><span data-stu-id="1ef85-212">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="1ef85-213">Det finns en rad som innehåller två förekomster av sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-213">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="1ef85-214">`$A.Matches`Egenskapen visar den första förekomsten av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-214">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="1ef85-215">`$A.Matches.Length`Egenskapen räknar den första förekomsten av mönstret **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-215">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="1ef85-216">`$B`Variabeln använder samma `Get-ChildItem` `Select-String` cmdletar, men lägger till parametern **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-216">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="1ef85-217">**AllMatches** hittar varje förekomst av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-217">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="1ef85-218">De objekt som lagras i `$A` `$B` variablerna och är identiska.</span><span class="sxs-lookup"><span data-stu-id="1ef85-218">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="1ef85-219">`$B.Matches.Length`Egenskapen ökar eftersom alla förekomster av mönstret **PowerShell** räknas för varje rad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-219">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="1ef85-220">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1ef85-220">PARAMETERS</span></span>

### <span data-ttu-id="1ef85-221">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="1ef85-221">-AllMatches</span></span>

<span data-ttu-id="1ef85-222">Anger att cmdleten söker efter fler än en matchning i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-222">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="1ef85-223">Utan den här parametern `Select-String` hittar bara den första matchningen i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-223">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="1ef85-224">När `Select-String` söker efter fler än en matchning i en rad med text, genererar den fortfarande bara ett **MatchInfo** -objekt för raden, men egenskapen **matchar** för objektet innehåller alla matchningar.</span><span class="sxs-lookup"><span data-stu-id="1ef85-224">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="1ef85-225">Den här parametern ignoreras när den används i kombination med parametern **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-225">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="1ef85-226">Om du vill returnera alla matchningar och mönstret som du söker efter innehåller tecken för reguljära uttryck, måste du undanta dessa tecken i stället för att använda **SimpleMatch**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-226">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="1ef85-227">Mer information om hur du hoppar över reguljära uttryck finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="1ef85-227">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="1ef85-228">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="1ef85-228">-CaseSensitive</span></span>

<span data-ttu-id="1ef85-229">Anger att cmdleten matchar är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="1ef85-229">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="1ef85-230">Som standard är matchningar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="1ef85-230">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="1ef85-231">– Kontext</span><span class="sxs-lookup"><span data-stu-id="1ef85-231">-Context</span></span>

<span data-ttu-id="1ef85-232">Fångar upp det angivna antalet rader före och efter den rad som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="1ef85-232">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="1ef85-233">Om du anger ett tal som värde för den här parametern, bestämmer den siffran antalet rader som fångats före och efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-233">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="1ef85-234">Om du anger två tal som värde bestämmer det första talet antalet rader före matchningen och det andra talet bestämmer antalet rader efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-234">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="1ef85-235">Till exempel `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="1ef85-235">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="1ef85-236">I standard visningen visas rader med en matchning med en höger vinkel paren tes ( `>` ) (ASCII 62) i den första kolumnen i visningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-236">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="1ef85-237">Omarkerade rader är kontexten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-237">Unmarked lines are the context.</span></span>

<span data-ttu-id="1ef85-238">**Kontext** parametern ändrar inte antalet objekt som genereras av `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-238">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="1ef85-239">`Select-String` genererar ett [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -objekt för varje matchning.</span><span class="sxs-lookup"><span data-stu-id="1ef85-239">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="1ef85-240">Kontexten lagras som en sträng mat ris i objektets **kontext** egenskap.</span><span class="sxs-lookup"><span data-stu-id="1ef85-240">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="1ef85-241">När utdata från ett `Select-String` kommando skickas ned pipelinen till ett annat `Select-String` kommando, söker kommandot ta emot bara texten på den matchade raden.</span><span class="sxs-lookup"><span data-stu-id="1ef85-241">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="1ef85-242">Den matchade raden är värdet för egenskapen **line** för **MatchInfo** -objektet, inte texten i Sammanhangs linjerna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-242">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="1ef85-243">Därför är **kontext** parametern inte giltig i mottagnings `Select-String` kommandot.</span><span class="sxs-lookup"><span data-stu-id="1ef85-243">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="1ef85-244">När kontexten innehåller en matchning inkluderar **MatchInfo** -objektet för varje matchning alla kontext linjer, men de överlappande linjerna visas bara en gång i visningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-244">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

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

### <span data-ttu-id="1ef85-245">-Encoding</span><span class="sxs-lookup"><span data-stu-id="1ef85-245">-Encoding</span></span>

<span data-ttu-id="1ef85-246">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-246">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="1ef85-247">Standardvärdet är `default`.</span><span class="sxs-lookup"><span data-stu-id="1ef85-247">The default value is `default`.</span></span>

<span data-ttu-id="1ef85-248">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1ef85-248">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1ef85-249">`ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="1ef85-249">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="1ef85-250">`bigendianunicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-250">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="1ef85-251">`default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="1ef85-251">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="1ef85-252">`oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="1ef85-252">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="1ef85-253">`unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="1ef85-253">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="1ef85-254">`utf7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="1ef85-254">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="1ef85-255">`utf8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="1ef85-255">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="1ef85-256">`utf32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="1ef85-256">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, Unicode, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ef85-257">-Undanta</span><span class="sxs-lookup"><span data-stu-id="1ef85-257">-Exclude</span></span>

<span data-ttu-id="1ef85-258">Uteslut de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-258">Exclude the specified items.</span></span> <span data-ttu-id="1ef85-259">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-259">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1ef85-260">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-260">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1ef85-261">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-261">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1ef85-262">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="1ef85-262">-Include</span></span>

<span data-ttu-id="1ef85-263">Innehåller de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-263">Includes the specified items.</span></span> <span data-ttu-id="1ef85-264">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-264">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1ef85-265">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-265">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1ef85-266">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-266">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1ef85-267">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1ef85-267">-InputObject</span></span>

<span data-ttu-id="1ef85-268">Anger den text som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-268">Specifies the text to be searched.</span></span> <span data-ttu-id="1ef85-269">Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar texten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-269">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="1ef85-270">Att använda parametern **InputObject** är inte detsamma som att skicka strängar nedåt i pipeline till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-270">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="1ef85-271">När du rör fler än en sträng till `Select-String` cmdleten söker den efter den angivna texten i varje sträng och returnerar varje sträng som innehåller Sök texten.</span><span class="sxs-lookup"><span data-stu-id="1ef85-271">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="1ef85-272">När du använder parametern **InputObject** för att skicka en samling med strängar, `Select-String` behandlar samlingen som en enda kombinerad sträng.</span><span class="sxs-lookup"><span data-stu-id="1ef85-272">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="1ef85-273">`Select-String` Returnerar strängarna som en enhet om Sök texten hittas i en sträng.</span><span class="sxs-lookup"><span data-stu-id="1ef85-273">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1ef85-274">– Lista</span><span class="sxs-lookup"><span data-stu-id="1ef85-274">-List</span></span>

<span data-ttu-id="1ef85-275">Endast den första instansen av matchande text returneras från varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="1ef85-275">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="1ef85-276">Detta är det mest effektiva sättet att hämta en lista över filer som har innehåll som matchar det reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="1ef85-276">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="1ef85-277">Som standard `Select-String` returnerar ett **MatchInfo** -objekt för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-277">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="1ef85-278">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1ef85-278">-LiteralPath</span></span>

<span data-ttu-id="1ef85-279">Anger sökvägen till de filer som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-279">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="1ef85-280">Värdet för parametern **LiteralPath** används exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="1ef85-280">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="1ef85-281">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1ef85-281">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1ef85-282">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="1ef85-282">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1ef85-283">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="1ef85-283">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="1ef85-284">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-284">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1ef85-285">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="1ef85-285">-NotMatch</span></span>

<span data-ttu-id="1ef85-286">Parametern **NotMatch** söker efter text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1ef85-286">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="1ef85-287">-Path</span><span class="sxs-lookup"><span data-stu-id="1ef85-287">-Path</span></span>

<span data-ttu-id="1ef85-288">Anger sökvägen till filerna som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-288">Specifies the path to the files to search.</span></span> <span data-ttu-id="1ef85-289">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-289">Wildcards are permitted.</span></span> <span data-ttu-id="1ef85-290">Standard platsen är den lokala katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-290">The default location is the local directory.</span></span>

<span data-ttu-id="1ef85-291">Ange filer i katalogen, till exempel `log1.txt` , `*.doc` eller `*.*` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-291">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="1ef85-292">Om du bara anger en katalog Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="1ef85-292">If you specify only a directory, the command fails.</span></span>

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="1ef85-293">– Mönster</span><span class="sxs-lookup"><span data-stu-id="1ef85-293">-Pattern</span></span>

<span data-ttu-id="1ef85-294">Anger vilken text som ska finnas på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1ef85-294">Specifies the text to find on each line.</span></span> <span data-ttu-id="1ef85-295">Pattern-värdet behandlas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1ef85-295">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="1ef85-296">Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-296">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

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

### <span data-ttu-id="1ef85-297">– Tyst</span><span class="sxs-lookup"><span data-stu-id="1ef85-297">-Quiet</span></span>

<span data-ttu-id="1ef85-298">Anger att cmdleten returnerar ett booleskt värde (sant eller falskt) i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1ef85-298">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="1ef85-299">Värdet är true om mönstret hittas. annars är värdet FALSKT.</span><span class="sxs-lookup"><span data-stu-id="1ef85-299">The value is True if the pattern is found; otherwise the value is False.</span></span>

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

### <span data-ttu-id="1ef85-300">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="1ef85-300">-SimpleMatch</span></span>

<span data-ttu-id="1ef85-301">Anger att cmdleten använder en enkel matchning i stället för en reguljär uttrycks matchning.</span><span class="sxs-lookup"><span data-stu-id="1ef85-301">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="1ef85-302">I en enkel matchning `Select-String` söker efter texten i **mönster** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1ef85-302">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="1ef85-303">Den tolkar inte värdet för **Pattern** -parametern som en reguljär uttrycks instruktion.</span><span class="sxs-lookup"><span data-stu-id="1ef85-303">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="1ef85-304">Även om **SimpleMatch** används är egenskapen **matchar** för det **MatchInfo** -objekt som returnerades tomt.</span><span class="sxs-lookup"><span data-stu-id="1ef85-304">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="1ef85-305">När den här parametern används med parametern **AllMatches** ignoreras **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-305">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="1ef85-306">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ef85-306">CommonParameters</span></span>

<span data-ttu-id="1ef85-307">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1ef85-307">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ef85-308">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1ef85-308">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ef85-309">INDATA</span><span class="sxs-lookup"><span data-stu-id="1ef85-309">INPUTS</span></span>

### <span data-ttu-id="1ef85-310">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="1ef85-310">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1ef85-311">Du kan skicka vidare alla objekt som har en **toString** -Metod till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-311">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="1ef85-312">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1ef85-312">OUTPUTS</span></span>

### <span data-ttu-id="1ef85-313">Microsoft. PowerShell. commands. MatchInfo eller system. Boolean</span><span class="sxs-lookup"><span data-stu-id="1ef85-313">Microsoft.PowerShell.Commands.MatchInfo or System.Boolean</span></span>

<span data-ttu-id="1ef85-314">Som standard är utdata en uppsättning **MatchInfo** -objekt med en för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="1ef85-314">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="1ef85-315">Om du använder parametern **quiet** är utdata ett booleskt värde som anger om mönstret hittades.</span><span class="sxs-lookup"><span data-stu-id="1ef85-315">If you use the **Quiet** parameter, the output is a Boolean value indicating whether the pattern was found.</span></span>

## <span data-ttu-id="1ef85-316">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1ef85-316">NOTES</span></span>

<span data-ttu-id="1ef85-317">`Select-String` liknar **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="1ef85-317">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="1ef85-318">**SLS** -aliaset för `Select-String` cmdleten introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1ef85-318">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="1ef85-319">Enligt [godkända verb för PowerShell-kommandon](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)är det officiella aliaset för `Select-*` cmdlets `sc` , inte `sl` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-319">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="1ef85-320">Därför bör rätt alias för `Select-String` vara `scs` , inte `sls` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-320">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="1ef85-321">Detta är ett undantag till den här regeln.</span><span class="sxs-lookup"><span data-stu-id="1ef85-321">This is an exception to this rule.</span></span>

<span data-ttu-id="1ef85-322">Om du vill använda `Select-String` anger du den text som du vill hitta som värde för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1ef85-322">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="1ef85-323">Om du vill ange vilken text som ska genomsökas använder du följande kriterier:</span><span class="sxs-lookup"><span data-stu-id="1ef85-323">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="1ef85-324">Skriv texten i en Citerad sträng och koppla den sedan till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-324">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="1ef85-325">Lagra en text sträng i en variabel och ange sedan variabeln som värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-325">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="1ef85-326">Om texten lagras i filer använder du parametern **Path** för att ange sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-326">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="1ef85-327">Som standard `Select-String` tolkar värdet för **Pattern** -parametern som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1ef85-327">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="1ef85-328">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1ef85-328">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="1ef85-329">Du kan använda parametern **SimpleMatch** för att åsidosätta den reguljära uttrycks matchningen.</span><span class="sxs-lookup"><span data-stu-id="1ef85-329">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="1ef85-330">Parametern **SimpleMatch** hittar förekomster av värdet för **Pattern** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1ef85-330">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="1ef85-331">Standardutdata för `Select-String` är ett **MatchInfo** -objekt, som innehåller detaljerad information om matchningarna.</span><span class="sxs-lookup"><span data-stu-id="1ef85-331">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="1ef85-332">Informationen i objektet är användbar när du söker efter text i filer, eftersom **MatchInfo** -objekt har egenskaper som **fil namn** och **rad**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-332">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="1ef85-333">När indata inte är från filen är värdet för dessa parametrar **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="1ef85-333">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="1ef85-334">Om du inte behöver informationen i **MatchInfo** -objektet använder du parametern **quiet** .</span><span class="sxs-lookup"><span data-stu-id="1ef85-334">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="1ef85-335">Parametern **quiet** returnerar ett booleskt värde (sant eller falskt) för att indikera om en matchning hittades i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1ef85-335">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="1ef85-336">När du matchar fraser `Select-String` använder den aktuella kulturen som har angetts för systemet.</span><span class="sxs-lookup"><span data-stu-id="1ef85-336">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="1ef85-337">Använd cmdleten för att hitta den aktuella kulturen `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="1ef85-337">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="1ef85-338">Om du vill hitta egenskaperna för ett **MatchInfo** -objekt skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1ef85-338">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="1ef85-339">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1ef85-339">RELATED LINKS</span></span>

[<span data-ttu-id="1ef85-340">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1ef85-340">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="1ef85-341">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="1ef85-341">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="1ef85-342">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1ef85-342">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="1ef85-343">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1ef85-343">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="1ef85-344">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="1ef85-344">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="1ef85-345">Get-alias</span><span class="sxs-lookup"><span data-stu-id="1ef85-345">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="1ef85-346">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1ef85-346">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="1ef85-347">Get-Command</span><span class="sxs-lookup"><span data-stu-id="1ef85-347">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="1ef85-348">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="1ef85-348">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="1ef85-349">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1ef85-349">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="1ef85-350">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="1ef85-350">Out-File</span></span>](Out-File.md)
