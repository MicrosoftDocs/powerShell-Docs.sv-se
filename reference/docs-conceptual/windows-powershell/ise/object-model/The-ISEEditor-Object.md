---
ms.date: 12/31/2019
title: ISEEditor-objektet
description: Ett ISEEditor-objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEEditor. Konsol fönstret är ett ISEEditor-objekt.
ms.openlocfilehash: ffcb6e35e1160beab6efb29cc84847fa9ffd012b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92654059"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="95c20-104">ISEEditor-objektet</span><span class="sxs-lookup"><span data-stu-id="95c20-104">The ISEEditor Object</span></span>

<span data-ttu-id="95c20-105">Ett **ISEEditor** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="95c20-105">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="95c20-106">Konsol fönstret är ett **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="95c20-106">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="95c20-107">Varje [ISEFile](The-ISEFile-Object.md) -objekt har ett associerat **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="95c20-107">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="95c20-108">I följande avsnitt listas metoder och egenskaper för ett **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="95c20-108">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="95c20-109">Metoder</span><span class="sxs-lookup"><span data-stu-id="95c20-109">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="95c20-110">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="95c20-110">Clear\(\)</span></span>

<span data-ttu-id="95c20-111">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-112">Tar bort texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="95c20-112">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="95c20-113">EnsureVisible \( int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="95c20-113">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="95c20-114">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-115">Rullar i redigeraren så att den rad som motsvarar det angivna värdet för parametern **lineNumber** är synlig.</span><span class="sxs-lookup"><span data-stu-id="95c20-115">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="95c20-116">Ett undantag genereras om det angivna rad numret ligger utanför intervallet 1, sista rad numret, som definierar giltiga rad nummer.</span><span class="sxs-lookup"><span data-stu-id="95c20-116">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="95c20-117">**lineNumber** Numret på raden som ska göras synlig.</span><span class="sxs-lookup"><span data-stu-id="95c20-117">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="95c20-118">Aktiv\(\)</span><span class="sxs-lookup"><span data-stu-id="95c20-118">Focus\(\)</span></span>

<span data-ttu-id="95c20-119">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-119">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-120">Ställer in fokus på redigeraren.</span><span class="sxs-lookup"><span data-stu-id="95c20-120">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="95c20-121">GetLineLength \( int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="95c20-121">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="95c20-122">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-123">Hämtar rad längden som ett heltal för raden som anges av rad numret.</span><span class="sxs-lookup"><span data-stu-id="95c20-123">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="95c20-124">**lineNumber** Numret på den linje som längden ska hämtas från.</span><span class="sxs-lookup"><span data-stu-id="95c20-124">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="95c20-125">**Returnerar** Rad längden för raden vid det angivna rad numret.</span><span class="sxs-lookup"><span data-stu-id="95c20-125">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="95c20-126">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="95c20-126">GoToMatch\(\)</span></span>

<span data-ttu-id="95c20-127">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="95c20-127">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="95c20-128">Flyttar cirkumflexet till det matchande tecknet om egenskapen **CanGoToMatch** för Editor-objektet är `$true` , vilket inträffar när cirkumflexet är omedelbart före en inledande parentes, hak paren tes eller klammerparentes,, `(` `[` , `{` eller omedelbart efter en avslutande parentes, hak `)` `]` `}` paren tes eller klammerparentes,,,.</span><span class="sxs-lookup"><span data-stu-id="95c20-128">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="95c20-129">Cirkumflexet placeras före ett inledande tecken eller efter ett avslutande tecken.</span><span class="sxs-lookup"><span data-stu-id="95c20-129">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="95c20-130">Om egenskapen **CanGoToMatch** är är `$false` den här metoden ingenting.</span><span class="sxs-lookup"><span data-stu-id="95c20-130">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="95c20-131">InsertText- \( text \)</span><span class="sxs-lookup"><span data-stu-id="95c20-131">InsertText\( text \)</span></span>

<span data-ttu-id="95c20-132">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-132">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-133">Ersätter markeringen med text eller infogar text vid den aktuella cirkumflexens position.</span><span class="sxs-lookup"><span data-stu-id="95c20-133">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="95c20-134">**text** – sträng texten som ska infogas.</span><span class="sxs-lookup"><span data-stu-id="95c20-134">**text** - String The text to insert.</span></span>

<span data-ttu-id="95c20-135">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="95c20-135">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="95c20-136">Välj \( startline, startColumn, SourceLocation, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="95c20-136">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="95c20-137">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-137">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-138">Markerar texten från parametrarna **startline** , **startColumn** , **SourceLocation** och **endColumn** .</span><span class="sxs-lookup"><span data-stu-id="95c20-138">Selects the text from the **startLine** , **startColumn** , **endLine** , and **endColumn** parameters.</span></span>

<span data-ttu-id="95c20-139">**startline** – heltals linjen där valet börjar.</span><span class="sxs-lookup"><span data-stu-id="95c20-139">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="95c20-140">**startColumn** – Integer kolumnen i Start raden där markeringen börjar.</span><span class="sxs-lookup"><span data-stu-id="95c20-140">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="95c20-141">**SourceLocation** – heltals linjen där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="95c20-141">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="95c20-142">**endColumn** – Markera kolumnen i slut raden där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="95c20-142">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="95c20-143">Se  [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="95c20-143">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="95c20-144">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="95c20-144">SelectCaretLine\(\)</span></span>

<span data-ttu-id="95c20-145">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-145">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-146">Markerar hela text raden som för närvarande innehåller cirkumflex.</span><span class="sxs-lookup"><span data-stu-id="95c20-146">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="95c20-147">SetCaretPosition \( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="95c20-147">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="95c20-148">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-148">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-149">Anger cirkumflexens position i rad numret och kolumn numret.</span><span class="sxs-lookup"><span data-stu-id="95c20-149">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="95c20-150">Ett undantag utlöses om antingen cirkumflexets rad nummer eller cirkumflex kolumn numret inte är av respektive giltiga intervall.</span><span class="sxs-lookup"><span data-stu-id="95c20-150">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="95c20-151">**lineNumber** – heltals markörens rad nummer.</span><span class="sxs-lookup"><span data-stu-id="95c20-151">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="95c20-152">**columnNumber** – heltal för kolumn numret i cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="95c20-152">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="95c20-153">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="95c20-153">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="95c20-154">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="95c20-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="95c20-155">Gör så att alla dispositions avsnitt expanderas eller komprimeras.</span><span class="sxs-lookup"><span data-stu-id="95c20-155">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="95c20-156">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="95c20-156">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="95c20-157">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="95c20-157">CanGoToMatch</span></span>

<span data-ttu-id="95c20-158">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="95c20-158">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="95c20-159">Den skrivskyddade booleska egenskapen som anger om cirkumflexet infaller vid en parentes, hak paren tes eller klammerparentes, `()` `[]` ,, `{}` .</span><span class="sxs-lookup"><span data-stu-id="95c20-159">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="95c20-160">Om cirkumflexet är omedelbart före det inledande tecknet eller omedelbart efter det avslutande tecknet i ett par, är det här egenskap svärdet `$true` .</span><span class="sxs-lookup"><span data-stu-id="95c20-160">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="95c20-161">Annars är det `$false` .</span><span class="sxs-lookup"><span data-stu-id="95c20-161">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="95c20-162">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="95c20-162">CaretColumn</span></span>

<span data-ttu-id="95c20-163">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-163">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-164">Den skrivskyddade egenskapen som hämtar kolumn numret som motsvarar cirkumflexens position.</span><span class="sxs-lookup"><span data-stu-id="95c20-164">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="95c20-165">CaretLine</span><span class="sxs-lookup"><span data-stu-id="95c20-165">CaretLine</span></span>

<span data-ttu-id="95c20-166">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-166">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-167">Den skrivskyddade egenskapen som hämtar numret på den rad som innehåller cirkumflexen.</span><span class="sxs-lookup"><span data-stu-id="95c20-167">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="95c20-168">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="95c20-168">CaretLineText</span></span>

<span data-ttu-id="95c20-169">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-170">Den skrivskyddade egenskapen som hämtar den fullständiga text raden som innehåller cirkumflex.</span><span class="sxs-lookup"><span data-stu-id="95c20-170">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="95c20-171">LineCount</span><span class="sxs-lookup"><span data-stu-id="95c20-171">LineCount</span></span>

<span data-ttu-id="95c20-172">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-172">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-173">Den skrivskyddade egenskapen som hämtar rad antalet från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="95c20-173">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="95c20-174">SelectedText</span><span class="sxs-lookup"><span data-stu-id="95c20-174">SelectedText</span></span>

<span data-ttu-id="95c20-175">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-175">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-176">Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="95c20-176">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="95c20-177">Se  [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="95c20-177">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="95c20-178">Text</span><span class="sxs-lookup"><span data-stu-id="95c20-178">Text</span></span>

<span data-ttu-id="95c20-179">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="95c20-179">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="95c20-180">Egenskapen Läs/skriv som hämtar eller anger texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="95c20-180">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="95c20-181">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="95c20-181">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="95c20-182">Skript exempel</span><span class="sxs-lookup"><span data-stu-id="95c20-182">Scripting Example</span></span>

```powershell
# This illustrates how you can use the length of a line to
# select the entire line and shows how you can make it lowercase.
# You must run this in the Console pane. It will not run in the Script pane.
# Begin by getting a variable that points to the editor.
$myEditor = $psISE.CurrentFile.Editor
# Clear the text in the current file editor.
$myEditor.Clear()

# Make sure the file has five lines of text.
$myEditor.InsertText("LINE1 `n")
$myEditor.InsertText("LINE2 `n")
$myEditor.InsertText("LINE3 `n")
$myEditor.InsertText("LINE4 `n")
$myEditor.InsertText("LINE5 `n")

# Use the GetLineLength method to get the length of the third line.
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="95c20-183">Se även</span><span class="sxs-lookup"><span data-stu-id="95c20-183">See Also</span></span>

- [<span data-ttu-id="95c20-184">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="95c20-184">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="95c20-185">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="95c20-185">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="95c20-186">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="95c20-186">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="95c20-187">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="95c20-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
