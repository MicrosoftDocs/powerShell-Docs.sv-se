---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 89880bc5ae45f442bea2d9c1f71d7df4cfa5e333
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269318"
---
# <span data-ttu-id="1cd9c-103">Select-String</span><span class="sxs-lookup"><span data-stu-id="1cd9c-103">Select-String</span></span>

## <span data-ttu-id="1cd9c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1cd9c-104">SYNOPSIS</span></span>
<span data-ttu-id="1cd9c-105">Söker efter text i strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-105">Finds text in strings and files.</span></span>

## <span data-ttu-id="1cd9c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1cd9c-106">SYNTAX</span></span>

### <span data-ttu-id="1cd9c-107">Fil (standard)</span><span class="sxs-lookup"><span data-stu-id="1cd9c-107">File (Default)</span></span>

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="1cd9c-108">Objekt</span><span class="sxs-lookup"><span data-stu-id="1cd9c-108">Object</span></span>

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="1cd9c-109">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="1cd9c-109">LiteralFile</span></span>

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="1cd9c-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1cd9c-110">DESCRIPTION</span></span>

<span data-ttu-id="1cd9c-111">`Select-String`Cmdleten söker efter text-och text mönster i inmatade strängar och filer.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-111">The `Select-String` cmdlet searches for text and text patterns in input strings and files.</span></span> <span data-ttu-id="1cd9c-112">Du kan använda `Select-String` liknande **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-112">You can use `Select-String` similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="1cd9c-113">`Select-String` baseras på text rader.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-113">`Select-String` is based on lines of text.</span></span> <span data-ttu-id="1cd9c-114">Som standard `Select-String` söker den första matchningen i varje rad, och för varje matchning visas fil namnet, rad numret och all text på raden som innehåller matchningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-114">By default, `Select-String` finds the first match in each line and, for each match, it displays the file name, line number, and all text in the line containing the match.</span></span> <span data-ttu-id="1cd9c-115">Du kan direkt `Select-String` hitta flera matchningar per rad, Visa text före och efter matchningen eller visa ett booleskt värde (sant eller falskt) som anger om en matchning hittas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-115">You can direct `Select-String` to find multiple matches per line, display text before and after the match, or display a Boolean value (True or False) that indicates whether a match is found.</span></span>

<span data-ttu-id="1cd9c-116">`Select-String` använder reguljär uttrycks matchning, men den kan också utföra en matchning som söker i indatamängden för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-116">`Select-String` uses regular expression matching, but it can also perform a match that searches the input for the text that you specify.</span></span>

<span data-ttu-id="1cd9c-117">`Select-String` kan visa alla text matchningar eller stoppa efter den första matchningen i varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-117">`Select-String` can display all the text matches or stop after the first match in each input file.</span></span>
<span data-ttu-id="1cd9c-118">`Select-String` kan användas för att visa all text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-118">`Select-String` can be used to display all text that doesn't match the specified pattern.</span></span>

<span data-ttu-id="1cd9c-119">Du kan också ange om `Select-String` du vill att en viss tecken kodning ska förväntas, till exempel när du söker filer med Unicode-text.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-119">You can also specify that `Select-String` should expect a particular character encoding, such as when you're searching files of Unicode text.</span></span> <span data-ttu-id="1cd9c-120">`Select-String` använder byte-order-markering (BOM) för att identifiera filens kodnings format.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-120">`Select-String` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="1cd9c-121">Om filen saknar struktur antas kodningen vara UTF8.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-121">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="1cd9c-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1cd9c-122">EXAMPLES</span></span>

### <span data-ttu-id="1cd9c-123">Exempel 1: hitta en Skift läges känslig matchning</span><span class="sxs-lookup"><span data-stu-id="1cd9c-123">Example 1: Find a case-sensitive match</span></span>

<span data-ttu-id="1cd9c-124">I det här exemplet är Skift läges känslig matchning av texten som skickades pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-124">This example does a case-sensitive match of the text that was sent down the pipeline to the `Select-String` cmdlet.</span></span>

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

<span data-ttu-id="1cd9c-125">Text strängarna **Hello** och **Hej** skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-125">The text strings **Hello** and **HELLO** are sent down the pipeline to the `Select-String` cmdlet.</span></span>
<span data-ttu-id="1cd9c-126">`Select-String` använder **Pattern** -parametern för att ange **Hej**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-126">`Select-String` uses the **Pattern** parameter to specify **HELLO**.</span></span> <span data-ttu-id="1cd9c-127">Parametern **caseSensitive** anger att Skift läget endast måste matcha versaler och gemener.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-127">The **CaseSensitive** parameter specifies that the case must match only the upper-case pattern.</span></span> <span data-ttu-id="1cd9c-128">**SimpleMatch** är en valfri parameter och anger att strängen i mönstret inte tolkas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-128">**SimpleMatch** is an optional parameter and specifies that the string in the pattern isn't interpreted as a regular expression.</span></span>
<span data-ttu-id="1cd9c-129">`Select-String` visar **Hello** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-129">`Select-String` displays **HELLO** in the PowerShell console.</span></span>

### <span data-ttu-id="1cd9c-130">Exempel 2: Sök efter matchningar i textfiler</span><span class="sxs-lookup"><span data-stu-id="1cd9c-130">Example 2: Find matches in text files</span></span>

<span data-ttu-id="1cd9c-131">Det här kommandot söker igenom alla filer med `.txt` fil namns tillägget i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-131">This command searches all files with the `.txt` file name extension in the current directory.</span></span> <span data-ttu-id="1cd9c-132">I utdata visas raderna i de filer som innehåller den angivna strängen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-132">The output displays the lines in those files that include the specified string.</span></span>

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

<span data-ttu-id="1cd9c-133">I det här exemplet `Get-Alias` och `Get-Command` används med `Out-File` cmdleten för att skapa två textfiler i den aktuella katalogen **Alias.txt** och **Command.txt**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-133">In this example, `Get-Alias` and `Get-Command` are used with the `Out-File` cmdlet to create two text files in the current directory, **Alias.txt** and **Command.txt**.</span></span>

<span data-ttu-id="1cd9c-134">`Select-String` använder parametern **Path** med jokertecknet asterisk ( `*` ) för att söka igenom alla filer i den aktuella katalogen med fil namns tillägget `.txt` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-134">`Select-String` uses the **Path** parameter with the asterisk (`*`) wildcard to search all files in the current directory with the file name extension `.txt`.</span></span> <span data-ttu-id="1cd9c-135">Parametern **Pattern** anger texten som ska matcha **Get-**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-135">The **Pattern** parameter specifies the text to match **Get-**.</span></span> <span data-ttu-id="1cd9c-136">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-136">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="1cd9c-137">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-137">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="1cd9c-138">Exempel 3: hitta en mönster matchning</span><span class="sxs-lookup"><span data-stu-id="1cd9c-138">Example 3: Find a pattern match</span></span>

<span data-ttu-id="1cd9c-139">I det här exemplet genomsöks flera filer för att hitta matchningar för det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-139">In this example, multiple files are searched to find matches for the specified pattern.</span></span> <span data-ttu-id="1cd9c-140">Mönstret använder en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-140">The pattern uses a regular expression quantifier.</span></span> <span data-ttu-id="1cd9c-141">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-141">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md).</span></span>

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

<span data-ttu-id="1cd9c-142">`Select-String`Cmdleten använder två parametrar, **sökväg** och **mönster**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-142">The `Select-String` cmdlet uses two parameters, **Path** and **Pattern**.</span></span> <span data-ttu-id="1cd9c-143">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-143">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="1cd9c-144">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-144">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="1cd9c-145">**Pattern** -parametern anger att matchar ett frågetecken ( `?` ) i varje fil.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-145">The **Pattern** parameter specifies to match a question mark (`?`) in each file.</span></span> <span data-ttu-id="1cd9c-146">Ett omvänt snedstreck ( `\` ) används som ett escape-tecken och är nödvändigt eftersom frågetecknet ( `?` ) är en kvantifierare för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-146">A backslash (`\`) is used as an escape character and is necessary because the question mark (`?`) is a regular expression quantifier.</span></span> <span data-ttu-id="1cd9c-147">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-147">`Select-String` displays the output in the PowerShell console.</span></span> <span data-ttu-id="1cd9c-148">Fil namnet och rad numret före varje rad med innehåll som innehåller en matchning för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-148">The file name and line number precede each line of content that contains a match for the **Pattern** parameter.</span></span>

### <span data-ttu-id="1cd9c-149">Exempel 4: Använd Select-String i en funktion</span><span class="sxs-lookup"><span data-stu-id="1cd9c-149">Example 4: Use Select-String in a function</span></span>

<span data-ttu-id="1cd9c-150">I det här exemplet skapas en funktion för att söka efter ett mönster i PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-150">This example creates a function to search for a pattern in the PowerShell help files.</span></span> <span data-ttu-id="1cd9c-151">I det här exemplet finns bara funktionen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-151">For this example, the function only exists in the PowerShell session.</span></span> <span data-ttu-id="1cd9c-152">När PowerShell-sessionen stängs tas funktionen bort.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-152">When the PowerShell session is closed, the function is deleted.</span></span> <span data-ttu-id="1cd9c-153">Mer information finns i [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-153">For more information, see [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md).</span></span>

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

<span data-ttu-id="1cd9c-154">Funktionen skapas på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-154">The function is created on the PowerShell command line.</span></span> <span data-ttu-id="1cd9c-155">`Function`Kommandot använder namns **ökning-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-155">The `Function` command uses the name **Search-Help**.</span></span> <span data-ttu-id="1cd9c-156">Tryck på **RETUR** för att börja lägga till instruktioner till funktionen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-156">Press **Enter** to begin adding statements to the function.</span></span> <span data-ttu-id="1cd9c-157">I `>>` prompten lägger du till varje instruktion och trycker på **RETUR** som visas i exemplet.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-157">From the `>>` prompt, add each statement and press **Enter** as shown in the example.</span></span> <span data-ttu-id="1cd9c-158">När du har lagt till en avslutande hak paren tes returneras en PowerShell-prompt.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-158">After the closing bracket is added, you're returned to a PowerShell prompt.</span></span>

<span data-ttu-id="1cd9c-159">Funktionen innehåller två kommandon.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-159">The function contains two commands.</span></span> <span data-ttu-id="1cd9c-160">`$PSHelp`Variabeln lagrar sökvägen till PowerShell-hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-160">The `$PSHelp` variable stores the path to the PowerShell help files.</span></span> <span data-ttu-id="1cd9c-161">`$PSHOME` är PowerShell-installationsmappen med under katalogen **en-US** som anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-161">`$PSHOME` is the PowerShell installation directory with the subdirectory **en-US** that specifies each `*.txt` file in the directory.</span></span>

<span data-ttu-id="1cd9c-162">`Select-String`Kommandot i funktionen använder parametrarna **Path** och **pattern** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-162">The `Select-String` command in the function uses the **Path** and **Pattern** parameters.</span></span> <span data-ttu-id="1cd9c-163">Parametern **Path** använder `$PSHelp` variabeln för att hämta sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-163">The **Path** parameter uses the `$PSHelp` variable to get the path.</span></span> <span data-ttu-id="1cd9c-164">Parametern **Pattern** använder sträng **About_** som Sök villkor.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-164">The **Pattern** parameter uses the string **About_** as the search criteria.</span></span>

<span data-ttu-id="1cd9c-165">Om du vill köra funktionen skriver du `Search-Help` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-165">To run the function, type `Search-Help`.</span></span> <span data-ttu-id="1cd9c-166">Funktionens `Select-String` kommando visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-166">The function's `Select-String` command displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="1cd9c-167">Exempel 5: Sök efter en sträng i en händelse logg i Windows</span><span class="sxs-lookup"><span data-stu-id="1cd9c-167">Example 5: Search for a string in a Windows event log</span></span>

<span data-ttu-id="1cd9c-168">Det här exemplet söker efter en sträng i en händelse logg i Windows.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-168">This example searches for a string in a Windows event log.</span></span> <span data-ttu-id="1cd9c-169">Variabeln `$_` representerar det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-169">The variable `$_` represents the current object in the pipeline.</span></span> <span data-ttu-id="1cd9c-170">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

<span data-ttu-id="1cd9c-171">`Get-WinEvent`Cmdleten använder parametern **LogName** för att ange program loggen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-171">The `Get-WinEvent` cmdlet uses the **LogName** parameter to specify the Application log.</span></span> <span data-ttu-id="1cd9c-172">Parametern **MaxEvents** hämtar de senaste 50 händelserna från loggen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-172">The **MaxEvents** parameter gets the 50 most recent events from the log.</span></span> <span data-ttu-id="1cd9c-173">Logg innehållet lagras i variabeln med namnet `$Events` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-173">The log content is stored in the variable named `$Events`.</span></span>

<span data-ttu-id="1cd9c-174">`$Events`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-174">The `$Events` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="1cd9c-175">`Select-String` använder parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-175">`Select-String` uses the **InputObject** parameter.</span></span> <span data-ttu-id="1cd9c-176">`$_`Variabeln representerar det aktuella objektet och `message` är en egenskap för händelsen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-176">The `$_` variable represents the current object and `message` is a property of the event.</span></span> <span data-ttu-id="1cd9c-177">**Pattern** -parametern anger att strängen **misslyckades** och söker efter matchningar i `$_.message` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-177">The **Pattern** parameter species the string **Failed** and searches for matches in `$_.message`.</span></span> <span data-ttu-id="1cd9c-178">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-178">`Select-String` displays the output in the PowerShell console.</span></span>

### <span data-ttu-id="1cd9c-179">Exempel 6: hitta en sträng i under kataloger</span><span class="sxs-lookup"><span data-stu-id="1cd9c-179">Example 6: Find a string in subdirectories</span></span>

<span data-ttu-id="1cd9c-180">I det här exemplet genomsöks en katalog och alla dess under kataloger för en speciell text sträng.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-180">This example searches a directory and all of its subdirectories for a specific text string.</span></span>

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

<span data-ttu-id="1cd9c-181">`Get-ChildItem` använder parametern **Path** för att ange **C:\Windows\System32 \* . txt**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-181">`Get-ChildItem` uses the **Path** parameter to specify **C:\Windows\System32\*.txt**.</span></span> <span data-ttu-id="1cd9c-182">Parametern **rekursivt** innehåller under kataloger.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-182">The **Recurse** parameter includes the subdirectories.</span></span> <span data-ttu-id="1cd9c-183">Objekten skickas ned pipelinen till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-183">The objects are sent down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="1cd9c-184">`Select-String` använder **mönster** parametern och anger strängen **Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-184">`Select-String` uses the **Pattern** parameter and specifies the string **Microsoft**.</span></span> <span data-ttu-id="1cd9c-185">Parametern **caseSensitive** används för att matcha det exakta Skift läget för strängen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-185">The **CaseSensitive** parameter is used to match the exact case of the string.</span></span> <span data-ttu-id="1cd9c-186">`Select-String` visar utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-186">`Select-String` displays the output in the PowerShell console.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd9c-187">Beroende på dina behörigheter kan du se **åtkomst nekade** meddelanden i utdata.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-187">Dependent upon your permissions, you might see **Access denied** messages in the output.</span></span>

### <span data-ttu-id="1cd9c-188">Exempel 7: hitta strängar som inte matchar ett mönster</span><span class="sxs-lookup"><span data-stu-id="1cd9c-188">Example 7: Find strings that do not match a pattern</span></span>

<span data-ttu-id="1cd9c-189">Det här exemplet visar hur du kan utesluta rader med data som inte matchar ett mönster.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-189">This example shows how to exclude lines of data that don't match a pattern.</span></span>

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

<span data-ttu-id="1cd9c-190">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-190">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="1cd9c-191">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-191">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="1cd9c-192">Parametern **Pattern** anger **Get** och **set** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-192">The **Pattern** parameter specifies **Get** and **Set** as the search pattern.</span></span> <span data-ttu-id="1cd9c-193">**NotMatch** -parametern utesluter **Get** och **set** från resultaten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-193">The **NotMatch** parameter excludes **Get** and **Set** from the results.</span></span>
<span data-ttu-id="1cd9c-194">`Select-String` visar utdata i PowerShell-konsolen som inte innehåller **Get** eller **set**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-194">`Select-String` displays the output in the PowerShell console that doesn't include **Get** or **Set**.</span></span>

### <span data-ttu-id="1cd9c-195">Exempel 8: Hitta rader före och efter en matchning</span><span class="sxs-lookup"><span data-stu-id="1cd9c-195">Example 8: Find lines before and after a match</span></span>

<span data-ttu-id="1cd9c-196">Det här exemplet visar hur du hämtar raderna före och efter det matchade mönstret.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-196">This example shows how to get the lines before and after the matched pattern.</span></span>

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

<span data-ttu-id="1cd9c-197">`Get-Command`Cmdleten skickar ett objekt nedåt i pipeline till `Out-File` för att skapa **Command.txt** -filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-197">The `Get-Command` cmdlet sends objects down the pipeline to the `Out-File` to create the **Command.txt** file in the current directory.</span></span> <span data-ttu-id="1cd9c-198">`Select-String` använder parametern **Path** för att ange **Command.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-198">`Select-String` uses the **Path** parameter to specify the **Command.txt** file.</span></span> <span data-ttu-id="1cd9c-199">Parametern **Pattern** anger **Get-Computer** som Sök mönster.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-199">The **Pattern** parameter specifies **Get-Computer** as the search pattern.</span></span> <span data-ttu-id="1cd9c-200">**Kontext** parametern använder två värden, före och efter, och markerar mönster matchningar i utdata med en vinkel paren tes ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-200">The **Context** parameter uses two values, before and after, and marks pattern matches in the output with an angle bracket (`>`).</span></span> <span data-ttu-id="1cd9c-201">**Kontext** parametern matar ut de två raderna före den första mönster matchningen och tre rader efter den sista mönster matchningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-201">The **Context** parameter outputs the two lines before the first pattern match and three lines after the last pattern match.</span></span>

### <span data-ttu-id="1cd9c-202">Exempel 9: Sök efter alla mönster matchningar</span><span class="sxs-lookup"><span data-stu-id="1cd9c-202">Example 9: Find all pattern matches</span></span>

<span data-ttu-id="1cd9c-203">I det här exemplet visas hur **AllMatches** -parametern hittar varje mönster matchning i en rad med text.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-203">This example shows how the **AllMatches** parameter finds each pattern match in a line of text.</span></span> <span data-ttu-id="1cd9c-204">Som standard `Select-String` söker bara den första förekomsten av ett mönster i en textrad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-204">By default, `Select-String` only finds the first occurrence of a pattern in a line of text.</span></span> <span data-ttu-id="1cd9c-205">I det här exemplet används objekt egenskaper som hittas med `Get-Member` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-205">This example uses object properties that are found with the `Get-Member` cmdlet.</span></span>

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

<span data-ttu-id="1cd9c-206">`Get-ChildItem`Cmdleten använder parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-206">The `Get-ChildItem` cmdlet uses the **Path** parameter.</span></span> <span data-ttu-id="1cd9c-207">Parametern **Path** använder variabeln `$PSHOME` som anger PowerShell-katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-207">The **Path** parameter uses the variable `$PSHOME` that specifies the PowerShell directory.</span></span> <span data-ttu-id="1cd9c-208">Resten av sökvägen innehåller under katalogen **en-US** och anger varje `*.txt` fil i katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-208">The remainder of the path includes the subdirectory **en-US** and specifies each `*.txt` file in the directory.</span></span> <span data-ttu-id="1cd9c-209">`Get-ChildItem`Objekten lagras i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-209">The `Get-ChildItem` objects are stored in the `$A` variable.</span></span> <span data-ttu-id="1cd9c-210">`$A`Variabeln skickas ned pipelinen till `Select-String` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-210">The `$A` variable is sent down the pipeline to the `Select-String` cmdlet.</span></span> <span data-ttu-id="1cd9c-211">`Select-String` använder **Pattern** -parametern för att söka igenom varje fil för sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-211">`Select-String` uses the **Pattern** parameter to search each file for the string **PowerShell**.</span></span>

<span data-ttu-id="1cd9c-212">På kommando raden för PowerShell `$A` visas variabel innehållet.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-212">From the PowerShell command line, the `$A` variable contents are displayed.</span></span> <span data-ttu-id="1cd9c-213">Det finns en rad som innehåller två förekomster av sträng **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-213">There's a line that contains two occurrences of the string **PowerShell**.</span></span>

<span data-ttu-id="1cd9c-214">`$A.Matches`Egenskapen visar den första förekomsten av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-214">The `$A.Matches` property lists the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="1cd9c-215">`$A.Matches.Length`Egenskapen räknar den första förekomsten av mönstret **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-215">The `$A.Matches.Length` property counts the first occurrence of the pattern **PowerShell** on each line.</span></span>

<span data-ttu-id="1cd9c-216">`$B`Variabeln använder samma `Get-ChildItem` `Select-String` cmdletar, men lägger till parametern **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-216">The `$B` variable uses the same `Get-ChildItem` and `Select-String` cmdlets, but adds the **AllMatches** parameter.</span></span> <span data-ttu-id="1cd9c-217">**AllMatches** hittar varje förekomst av Pattern **PowerShell** på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-217">**AllMatches** finds each occurrence of the pattern **PowerShell** on each line.</span></span> <span data-ttu-id="1cd9c-218">De objekt som lagras i `$A` `$B` variablerna och är identiska.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-218">The objects stored in the `$A` and `$B` variables are identical.</span></span>

<span data-ttu-id="1cd9c-219">`$B.Matches.Length`Egenskapen ökar eftersom alla förekomster av mönstret **PowerShell** räknas för varje rad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-219">The `$B.Matches.Length` property increases because for each line, every occurrence of the pattern **PowerShell** is counted.</span></span>

## <span data-ttu-id="1cd9c-220">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1cd9c-220">PARAMETERS</span></span>

### <span data-ttu-id="1cd9c-221">-AllMatches</span><span class="sxs-lookup"><span data-stu-id="1cd9c-221">-AllMatches</span></span>

<span data-ttu-id="1cd9c-222">Anger att cmdleten söker efter fler än en matchning i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-222">Indicates that the cmdlet searches for more than one match in each line of text.</span></span> <span data-ttu-id="1cd9c-223">Utan den här parametern `Select-String` hittar bara den första matchningen i varje textrad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-223">Without this parameter, `Select-String` finds only the first match in each line of text.</span></span>

<span data-ttu-id="1cd9c-224">När `Select-String` söker efter fler än en matchning i en rad med text, genererar den fortfarande bara ett **MatchInfo** -objekt för raden, men egenskapen **matchar** för objektet innehåller alla matchningar.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-224">When `Select-String` finds more than one match in a line of text, it still emits only one **MatchInfo** object for the line, but the **Matches** property of the object contains all the matches.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd9c-225">Den här parametern ignoreras när den används i kombination med parametern **SimpleMatch** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-225">This parameter is ignored when used in combination with the **SimpleMatch** parameter.</span></span> <span data-ttu-id="1cd9c-226">Om du vill returnera alla matchningar och mönstret som du söker efter innehåller tecken för reguljära uttryck, måste du undanta dessa tecken i stället för att använda **SimpleMatch**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-226">If you wish to return all matches and the pattern that you are searching for contains regular expression characters, you must escape those characters rather than using **SimpleMatch**.</span></span> <span data-ttu-id="1cd9c-227">Mer information om hur du hoppar över reguljära uttryck finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-227">See [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) for more information about escaping regular expressions.</span></span>

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

### <span data-ttu-id="1cd9c-228">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="1cd9c-228">-CaseSensitive</span></span>

<span data-ttu-id="1cd9c-229">Anger att cmdleten matchar är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-229">Indicates that the cmdlet matches are case-sensitive.</span></span> <span data-ttu-id="1cd9c-230">Som standard är matchningar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-230">By default, matches aren't case-sensitive.</span></span>

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

### <span data-ttu-id="1cd9c-231">– Kontext</span><span class="sxs-lookup"><span data-stu-id="1cd9c-231">-Context</span></span>

<span data-ttu-id="1cd9c-232">Fångar upp det angivna antalet rader före och efter den rad som matchar mönstret.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-232">Captures the specified number of lines before and after the line that matches the pattern.</span></span>

<span data-ttu-id="1cd9c-233">Om du anger ett tal som värde för den här parametern, bestämmer den siffran antalet rader som fångats före och efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-233">If you enter one number as the value of this parameter, that number determines the number of lines captured before and after the match.</span></span> <span data-ttu-id="1cd9c-234">Om du anger två tal som värde bestämmer det första talet antalet rader före matchningen och det andra talet bestämmer antalet rader efter matchningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-234">If you enter two numbers as the value, the first number determines the number of lines before the match and the second number determines the number of lines after the match.</span></span> <span data-ttu-id="1cd9c-235">Till exempel `-Context 2,3`.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-235">For example, `-Context 2,3`.</span></span>

<span data-ttu-id="1cd9c-236">I standard visningen visas rader med en matchning med en höger vinkel paren tes ( `>` ) (ASCII 62) i den första kolumnen i visningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-236">In the default display, lines with a match are indicated by a right angle bracket (`>`) (ASCII 62) in the first column of the display.</span></span> <span data-ttu-id="1cd9c-237">Omarkerade rader är kontexten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-237">Unmarked lines are the context.</span></span>

<span data-ttu-id="1cd9c-238">**Kontext** parametern ändrar inte antalet objekt som genereras av `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-238">The **Context** parameter doesn't change the number of objects generated by `Select-String`.</span></span>
<span data-ttu-id="1cd9c-239">`Select-String` genererar ett [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) -objekt för varje matchning.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-239">`Select-String` generates one [MatchInfo](/dotnet/api/microsoft.powershell.commands.matchinfo) object for each match.</span></span> <span data-ttu-id="1cd9c-240">Kontexten lagras som en sträng mat ris i objektets **kontext** egenskap.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-240">The context is stored as an array of strings in the **Context** property of the object.</span></span>

<span data-ttu-id="1cd9c-241">När utdata från ett `Select-String` kommando skickas ned pipelinen till ett annat `Select-String` kommando, söker kommandot ta emot bara texten på den matchade raden.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-241">When the output of a `Select-String` command is sent down the pipeline to another `Select-String` command, the receiving command searches only the text in the matched line.</span></span> <span data-ttu-id="1cd9c-242">Den matchade raden är värdet för egenskapen **line** för **MatchInfo** -objektet, inte texten i Sammanhangs linjerna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-242">The matched line is the value of the **Line** property of the **MatchInfo** object, not the text in the context lines.</span></span> <span data-ttu-id="1cd9c-243">Därför är **kontext** parametern inte giltig i mottagnings `Select-String` kommandot.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-243">As a result, the **Context** parameter isn't valid on the receiving `Select-String` command.</span></span>

<span data-ttu-id="1cd9c-244">När kontexten innehåller en matchning inkluderar **MatchInfo** -objektet för varje matchning alla kontext linjer, men de överlappande linjerna visas bara en gång i visningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-244">When the context includes a match, the **MatchInfo** object for each match includes all the context lines, but the overlapping lines appear only once in the display.</span></span>

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

### <span data-ttu-id="1cd9c-245">-Encoding</span><span class="sxs-lookup"><span data-stu-id="1cd9c-245">-Encoding</span></span>

<span data-ttu-id="1cd9c-246">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-246">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="1cd9c-247">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-247">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="1cd9c-248">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1cd9c-248">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1cd9c-249">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-249">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="1cd9c-250">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-250">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="1cd9c-251">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-251">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="1cd9c-252">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-252">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="1cd9c-253">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-253">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="1cd9c-254">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-254">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="1cd9c-255">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="1cd9c-255">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="1cd9c-256">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="1cd9c-256">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="1cd9c-257">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-257">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="1cd9c-258">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-258">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="1cd9c-259">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-259">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

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

### <span data-ttu-id="1cd9c-260">-Undanta</span><span class="sxs-lookup"><span data-stu-id="1cd9c-260">-Exclude</span></span>

<span data-ttu-id="1cd9c-261">Uteslut de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-261">Exclude the specified items.</span></span> <span data-ttu-id="1cd9c-262">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-262">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1cd9c-263">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-263">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1cd9c-264">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-264">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1cd9c-265">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="1cd9c-265">-Include</span></span>

<span data-ttu-id="1cd9c-266">Innehåller de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-266">Includes the specified items.</span></span> <span data-ttu-id="1cd9c-267">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-267">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="1cd9c-268">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-268">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="1cd9c-269">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-269">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="1cd9c-270">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1cd9c-270">-InputObject</span></span>

<span data-ttu-id="1cd9c-271">Anger den text som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-271">Specifies the text to be searched.</span></span> <span data-ttu-id="1cd9c-272">Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar texten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-272">Enter a variable that contains the text, or type a command or expression that gets the text.</span></span>

<span data-ttu-id="1cd9c-273">Att använda parametern **InputObject** är inte detsamma som att skicka strängar nedåt i pipeline till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-273">Using the **InputObject** parameter isn't the same as sending strings down the pipeline to `Select-String`.</span></span>

<span data-ttu-id="1cd9c-274">När du rör fler än en sträng till `Select-String` cmdleten söker den efter den angivna texten i varje sträng och returnerar varje sträng som innehåller Sök texten.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-274">When you pipe more than one string to the `Select-String` cmdlet, it searches for the specified text in each string and returns each string that contains the search text.</span></span>

<span data-ttu-id="1cd9c-275">När du använder parametern **InputObject** för att skicka en samling med strängar, `Select-String` behandlar samlingen som en enda kombinerad sträng.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-275">When you use the **InputObject** parameter to submit a collection of strings, `Select-String` treats the collection as a single combined string.</span></span> <span data-ttu-id="1cd9c-276">`Select-String` Returnerar strängarna som en enhet om Sök texten hittas i en sträng.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-276">`Select-String` returns the strings as a unit if it finds the search text in any string.</span></span>

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

### <span data-ttu-id="1cd9c-277">– Lista</span><span class="sxs-lookup"><span data-stu-id="1cd9c-277">-List</span></span>

<span data-ttu-id="1cd9c-278">Endast den första instansen av matchande text returneras från varje indatafil.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-278">Only the first instance of matching text is returned from each input file.</span></span> <span data-ttu-id="1cd9c-279">Detta är det mest effektiva sättet att hämta en lista över filer som har innehåll som matchar det reguljära uttrycket.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-279">This is the most efficient way to retrieve a list of files that have contents matching the regular expression.</span></span>

<span data-ttu-id="1cd9c-280">Som standard `Select-String` returnerar ett **MatchInfo** -objekt för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-280">By default, `Select-String` returns a **MatchInfo** object for each match it finds.</span></span>

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

### <span data-ttu-id="1cd9c-281">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="1cd9c-281">-LiteralPath</span></span>

<span data-ttu-id="1cd9c-282">Anger sökvägen till de filer som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-282">Specifies the path to the files to be searched.</span></span> <span data-ttu-id="1cd9c-283">Värdet för parametern **LiteralPath** används exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-283">The value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="1cd9c-284">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-284">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="1cd9c-285">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-285">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="1cd9c-286">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-286">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="1cd9c-287">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-287">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="1cd9c-288">-NotMatch</span><span class="sxs-lookup"><span data-stu-id="1cd9c-288">-NotMatch</span></span>

<span data-ttu-id="1cd9c-289">Parametern **NotMatch** söker efter text som inte matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-289">The **NotMatch** parameter finds text that doesn't match the specified pattern.</span></span>

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

### <span data-ttu-id="1cd9c-290">-Path</span><span class="sxs-lookup"><span data-stu-id="1cd9c-290">-Path</span></span>

<span data-ttu-id="1cd9c-291">Anger sökvägen till filerna som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-291">Specifies the path to the files to search.</span></span> <span data-ttu-id="1cd9c-292">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-292">Wildcards are permitted.</span></span> <span data-ttu-id="1cd9c-293">Standard platsen är den lokala katalogen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-293">The default location is the local directory.</span></span>

<span data-ttu-id="1cd9c-294">Ange filer i katalogen, till exempel `log1.txt` , `*.doc` eller `*.*` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-294">Specify files in the directory, such as `log1.txt`, `*.doc`, or `*.*`.</span></span> <span data-ttu-id="1cd9c-295">Om du bara anger en katalog Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-295">If you specify only a directory, the command fails.</span></span>

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

### <span data-ttu-id="1cd9c-296">– Mönster</span><span class="sxs-lookup"><span data-stu-id="1cd9c-296">-Pattern</span></span>

<span data-ttu-id="1cd9c-297">Anger vilken text som ska finnas på varje rad.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-297">Specifies the text to find on each line.</span></span> <span data-ttu-id="1cd9c-298">Pattern-värdet behandlas som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-298">The pattern value is treated as a regular expression.</span></span>

<span data-ttu-id="1cd9c-299">Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-299">To learn about regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

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

### <span data-ttu-id="1cd9c-300">– Tyst</span><span class="sxs-lookup"><span data-stu-id="1cd9c-300">-Quiet</span></span>

<span data-ttu-id="1cd9c-301">Anger att cmdleten returnerar ett booleskt värde (sant eller falskt) i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-301">Indicates that the cmdlet returns a Boolean value (True or False), instead of a **MatchInfo** object.</span></span> <span data-ttu-id="1cd9c-302">Värdet är true om mönstret hittas. annars är värdet FALSKT.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-302">The value is True if the pattern is found; otherwise the value is False.</span></span>

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

### <span data-ttu-id="1cd9c-303">-SimpleMatch</span><span class="sxs-lookup"><span data-stu-id="1cd9c-303">-SimpleMatch</span></span>

<span data-ttu-id="1cd9c-304">Anger att cmdleten använder en enkel matchning i stället för en reguljär uttrycks matchning.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-304">Indicates that the cmdlet uses a simple match rather than a regular expression match.</span></span> <span data-ttu-id="1cd9c-305">I en enkel matchning `Select-String` söker efter texten i **mönster** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-305">In a simple match, `Select-String` searches the input for the text in the **Pattern** parameter.</span></span> <span data-ttu-id="1cd9c-306">Den tolkar inte värdet för **Pattern** -parametern som en reguljär uttrycks instruktion.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-306">It doesn't interpret the value of the **Pattern** parameter as a regular expression statement.</span></span>

<span data-ttu-id="1cd9c-307">Även om **SimpleMatch** används är egenskapen **matchar** för det **MatchInfo** -objekt som returnerades tomt.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-307">Also, when **SimpleMatch** is used, the **Matches** property of the **MatchInfo** object returned is empty.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd9c-308">När den här parametern används med parametern **AllMatches** ignoreras **AllMatches** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-308">When this parameter is used with the **AllMatches** parameter, the **AllMatches** is ignored.</span></span>

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

### <span data-ttu-id="1cd9c-309">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1cd9c-309">CommonParameters</span></span>

<span data-ttu-id="1cd9c-310">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-310">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1cd9c-311">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-311">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1cd9c-312">INDATA</span><span class="sxs-lookup"><span data-stu-id="1cd9c-312">INPUTS</span></span>

### <span data-ttu-id="1cd9c-313">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="1cd9c-313">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1cd9c-314">Du kan skicka vidare alla objekt som har en **toString** -Metod till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-314">You can pipe any object that has a **ToString** method to `Select-String`.</span></span>

## <span data-ttu-id="1cd9c-315">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1cd9c-315">OUTPUTS</span></span>

### <span data-ttu-id="1cd9c-316">Microsoft. PowerShell. commands. MatchInfo eller system. Boolean</span><span class="sxs-lookup"><span data-stu-id="1cd9c-316">Microsoft.PowerShell.Commands.MatchInfo or System.Boolean</span></span>

<span data-ttu-id="1cd9c-317">Som standard är utdata en uppsättning **MatchInfo** -objekt med en för varje matchning som hittas.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-317">By default, the output is a set of **MatchInfo** objects with one for each match found.</span></span> <span data-ttu-id="1cd9c-318">Om du använder parametern **quiet** är utdata ett booleskt värde som anger om mönstret hittades.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-318">If you use the **Quiet** parameter, the output is a Boolean value indicating whether the pattern was found.</span></span>

## <span data-ttu-id="1cd9c-319">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1cd9c-319">NOTES</span></span>

<span data-ttu-id="1cd9c-320">`Select-String` liknar **grep** i UNIX eller **findstr.exe** i Windows.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-320">`Select-String` is similar to **grep** in UNIX or **findstr.exe** in Windows.</span></span>

<span data-ttu-id="1cd9c-321">**SLS** -aliaset för `Select-String` cmdleten introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-321">The **sls** alias for the `Select-String` cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="1cd9c-322">Enligt [godkända verb för PowerShell-kommandon](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)är det officiella aliaset för `Select-*` cmdlets `sc` , inte `sl` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-322">According to [Approved Verbs for PowerShell Commands](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands), the official alias prefix for `Select-*` cmdlets is `sc`, not `sl`.</span></span> <span data-ttu-id="1cd9c-323">Därför bör rätt alias för `Select-String` vara `scs` , inte `sls` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-323">Therefore, the proper alias for `Select-String` should be `scs`, not `sls`.</span></span> <span data-ttu-id="1cd9c-324">Detta är ett undantag till den här regeln.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-324">This is an exception to this rule.</span></span>

<span data-ttu-id="1cd9c-325">Om du vill använda `Select-String` anger du den text som du vill hitta som värde för **mönster** parametern.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-325">To use `Select-String`, type the text that you want to find as the value of the **Pattern** parameter.</span></span> <span data-ttu-id="1cd9c-326">Om du vill ange vilken text som ska genomsökas använder du följande kriterier:</span><span class="sxs-lookup"><span data-stu-id="1cd9c-326">To specify the text to be searched, use the following criteria:</span></span>

- <span data-ttu-id="1cd9c-327">Skriv texten i en Citerad sträng och koppla den sedan till `Select-String` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-327">Type the text in a quoted string, and then pipe it to `Select-String`.</span></span>
- <span data-ttu-id="1cd9c-328">Lagra en text sträng i en variabel och ange sedan variabeln som värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-328">Store a text string in a variable, and then specify the variable as the value of the **InputObject** parameter.</span></span>
- <span data-ttu-id="1cd9c-329">Om texten lagras i filer använder du parametern **Path** för att ange sökvägen till filerna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-329">If the text is stored in files, use the **Path** parameter to specify the path to the files.</span></span>

<span data-ttu-id="1cd9c-330">Som standard `Select-String` tolkar värdet för **Pattern** -parametern som ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-330">By default, `Select-String` interprets the value of the **Pattern** parameter as a regular expression.</span></span> <span data-ttu-id="1cd9c-331">Mer information finns i [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="1cd9c-331">For more information, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span> <span data-ttu-id="1cd9c-332">Du kan använda parametern **SimpleMatch** för att åsidosätta den reguljära uttrycks matchningen.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-332">You can use the **SimpleMatch** parameter to override the regular expression matching.</span></span> <span data-ttu-id="1cd9c-333">Parametern **SimpleMatch** hittar förekomster av värdet för **Pattern** -parametern i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-333">The **SimpleMatch** parameter finds instances of the value of the **Pattern** parameter in the input.</span></span>

<span data-ttu-id="1cd9c-334">Standardutdata för `Select-String` är ett **MatchInfo** -objekt, som innehåller detaljerad information om matchningarna.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-334">The default output of `Select-String` is a **MatchInfo** object, which includes detailed information about the matches.</span></span> <span data-ttu-id="1cd9c-335">Informationen i objektet är användbar när du söker efter text i filer, eftersom **MatchInfo** -objekt har egenskaper som **fil namn** och **rad**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-335">The information in the object is useful when you're searching for text in files, because **MatchInfo** objects have properties such as **Filename** and **Line**.</span></span> <span data-ttu-id="1cd9c-336">När indata inte är från filen är värdet för dessa parametrar **InputStream**.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-336">When the input isn't from the file, the value of these parameters is **InputStream**.</span></span>

<span data-ttu-id="1cd9c-337">Om du inte behöver informationen i **MatchInfo** -objektet använder du parametern **quiet** .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-337">If you don't need the information in the **MatchInfo** object, use the **Quiet** parameter.</span></span> <span data-ttu-id="1cd9c-338">Parametern **quiet** returnerar ett booleskt värde (sant eller falskt) för att indikera om en matchning hittades i stället för ett **MatchInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-338">The **Quiet** parameter returns a Boolean value (True or False) to indicate whether it found a match, instead of a **MatchInfo** object.</span></span>

<span data-ttu-id="1cd9c-339">När du matchar fraser `Select-String` använder den aktuella kulturen som har angetts för systemet.</span><span class="sxs-lookup"><span data-stu-id="1cd9c-339">When matching phrases, `Select-String` uses the current culture that is set for the system.</span></span> <span data-ttu-id="1cd9c-340">Använd cmdleten för att hitta den aktuella kulturen `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="1cd9c-340">To find the current culture, use the `Get-Culture` cmdlet.</span></span>

<span data-ttu-id="1cd9c-341">Om du vill hitta egenskaperna för ett **MatchInfo** -objekt skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="1cd9c-341">To find the properties of a **MatchInfo** object, type the following command:</span></span>

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## <span data-ttu-id="1cd9c-342">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1cd9c-342">RELATED LINKS</span></span>

[<span data-ttu-id="1cd9c-343">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="1cd9c-343">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="1cd9c-344">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="1cd9c-344">about_Comparison_Operators</span></span>](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[<span data-ttu-id="1cd9c-345">about_Functions</span><span class="sxs-lookup"><span data-stu-id="1cd9c-345">about_Functions</span></span>](../Microsoft.PowerShell.Core/About/about_Functions.md)

[<span data-ttu-id="1cd9c-346">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="1cd9c-346">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="1cd9c-347">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="1cd9c-347">about_Regular_Expressions</span></span>](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[<span data-ttu-id="1cd9c-348">Get-alias</span><span class="sxs-lookup"><span data-stu-id="1cd9c-348">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="1cd9c-349">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1cd9c-349">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="1cd9c-350">Get-Command</span><span class="sxs-lookup"><span data-stu-id="1cd9c-350">Get-Command</span></span>](../Microsoft.PowerShell.Core/Get-Command.md)

[<span data-ttu-id="1cd9c-351">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="1cd9c-351">Get-Member</span></span>](Get-Member.md)

[<span data-ttu-id="1cd9c-352">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="1cd9c-352">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="1cd9c-353">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="1cd9c-353">Out-File</span></span>](Out-File.md)
