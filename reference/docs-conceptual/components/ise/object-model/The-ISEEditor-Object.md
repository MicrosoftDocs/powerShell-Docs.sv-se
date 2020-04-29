---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEEditor-objektet
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736197"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="7f177-103">ISEEditor-objektet</span><span class="sxs-lookup"><span data-stu-id="7f177-103">The ISEEditor Object</span></span>

<span data-ttu-id="7f177-104">Ett **ISEEditor** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="7f177-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="7f177-105">Konsol fönstret är ett **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7f177-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="7f177-106">Varje [ISEFile](The-ISEFile-Object.md) -objekt har ett associerat **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7f177-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="7f177-107">I följande avsnitt listas metoder och egenskaper för ett **ISEEditor** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7f177-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="7f177-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="7f177-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="7f177-109">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="7f177-109">Clear\(\)</span></span>

<span data-ttu-id="7f177-110">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-111">Tar bort texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="7f177-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="7f177-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="7f177-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="7f177-113">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-114">Rullar i redigeraren så att den rad som motsvarar det angivna värdet för parametern **lineNumber** är synlig.</span><span class="sxs-lookup"><span data-stu-id="7f177-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="7f177-115">Ett undantag genereras om det angivna rad numret ligger utanför intervallet 1, sista rad numret, som definierar giltiga rad nummer.</span><span class="sxs-lookup"><span data-stu-id="7f177-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="7f177-116">**lineNumber** Numret på raden som ska göras synlig.</span><span class="sxs-lookup"><span data-stu-id="7f177-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="7f177-117">Aktiv\(\)</span><span class="sxs-lookup"><span data-stu-id="7f177-117">Focus\(\)</span></span>

<span data-ttu-id="7f177-118">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-119">Ställer in fokus på redigeraren.</span><span class="sxs-lookup"><span data-stu-id="7f177-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="7f177-120">GetLineLength\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="7f177-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="7f177-121">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-122">Hämtar rad längden som ett heltal för raden som anges av rad numret.</span><span class="sxs-lookup"><span data-stu-id="7f177-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="7f177-123">**lineNumber** Numret på den linje som längden ska hämtas från.</span><span class="sxs-lookup"><span data-stu-id="7f177-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="7f177-124">**Returnerar** Rad längden för raden vid det angivna rad numret.</span><span class="sxs-lookup"><span data-stu-id="7f177-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="7f177-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="7f177-125">GoToMatch\(\)</span></span>

<span data-ttu-id="7f177-126">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="7f177-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7f177-127">Flyttar cirkumflexet till det matchande tecknet om egenskapen **CanGoToMatch** för Editor-objektet `$true`är, vilket inträffar när cirkumflexet är omedelbart före en inledande parentes, hak paren tes eller klammerparentes `(`,,`[`,`{` eller omedelbart efter en avslutande parentes, hak paren tes eller klammerparentes `)``]`,,,.`}`</span><span class="sxs-lookup"><span data-stu-id="7f177-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is `$true`, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - `(`,`[`,`{` - or immediately after a closing parenthesis, bracket, or brace - `)`,`]`,`}`.</span></span> <span data-ttu-id="7f177-128">Cirkumflexet placeras före ett inledande tecken eller efter ett avslutande tecken.</span><span class="sxs-lookup"><span data-stu-id="7f177-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="7f177-129">Om egenskapen **CanGoToMatch** är är `$false`den här metoden ingenting.</span><span class="sxs-lookup"><span data-stu-id="7f177-129">If the **CanGoToMatch** property is `$false`, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="7f177-130">InsertText\( -text\)</span><span class="sxs-lookup"><span data-stu-id="7f177-130">InsertText\( text \)</span></span>

<span data-ttu-id="7f177-131">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-132">Ersätter markeringen med text eller infogar text vid den aktuella cirkumflexens position.</span><span class="sxs-lookup"><span data-stu-id="7f177-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="7f177-133">**text** – sträng texten som ska infogas.</span><span class="sxs-lookup"><span data-stu-id="7f177-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="7f177-134">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="7f177-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="7f177-135">Välj\( StartLine, StartColumn, SourceLocation, endColumn\)</span><span class="sxs-lookup"><span data-stu-id="7f177-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="7f177-136">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-137">Markerar texten från parametrarna **startline**, **startColumn**, **SourceLocation**och **endColumn** .</span><span class="sxs-lookup"><span data-stu-id="7f177-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="7f177-138">**startline** – heltals linjen där valet börjar.</span><span class="sxs-lookup"><span data-stu-id="7f177-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="7f177-139">**startColumn** – Integer kolumnen i Start raden där markeringen börjar.</span><span class="sxs-lookup"><span data-stu-id="7f177-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="7f177-140">**SourceLocation** – heltals linjen där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="7f177-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="7f177-141">**endColumn** – Markera kolumnen i slut raden där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="7f177-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="7f177-142">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="7f177-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="7f177-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="7f177-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="7f177-144">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-145">Markerar hela text raden som för närvarande innehåller cirkumflex.</span><span class="sxs-lookup"><span data-stu-id="7f177-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="7f177-146">SetCaretPosition\( LineNumber, columnNumber\)</span><span class="sxs-lookup"><span data-stu-id="7f177-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="7f177-147">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-148">Anger cirkumflexens position i rad numret och kolumn numret.</span><span class="sxs-lookup"><span data-stu-id="7f177-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="7f177-149">Ett undantag utlöses om antingen cirkumflexets rad nummer eller cirkumflex kolumn numret inte är av respektive giltiga intervall.</span><span class="sxs-lookup"><span data-stu-id="7f177-149">It throws an exception if either the caret line number or the caret column number are out of their respective valid ranges.</span></span>

<span data-ttu-id="7f177-150">**lineNumber** – heltals markörens rad nummer.</span><span class="sxs-lookup"><span data-stu-id="7f177-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="7f177-151">**columnNumber** – heltal för kolumn numret i cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="7f177-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="7f177-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="7f177-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="7f177-153">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="7f177-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7f177-154">Gör så att alla dispositions avsnitt expanderas eller komprimeras.</span><span class="sxs-lookup"><span data-stu-id="7f177-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="7f177-155">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7f177-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="7f177-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="7f177-156">CanGoToMatch</span></span>

<span data-ttu-id="7f177-157">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="7f177-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="7f177-158">Den skrivskyddade booleska egenskapen som anger om cirkumflexet infaller vid en parentes, hak paren tes eller klammerparentes `()`, `[]`,, `{}`.</span><span class="sxs-lookup"><span data-stu-id="7f177-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - `()`, `[]`, `{}`.</span></span> <span data-ttu-id="7f177-159">Om cirkumflexet är omedelbart före det inledande tecknet eller omedelbart efter det avslutande tecknet i ett par, är `$true`det här egenskap svärdet.</span><span class="sxs-lookup"><span data-stu-id="7f177-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is `$true`.</span></span> <span data-ttu-id="7f177-160">Annars är `$false`det.</span><span class="sxs-lookup"><span data-stu-id="7f177-160">Otherwise, it is `$false`.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="7f177-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="7f177-161">CaretColumn</span></span>

<span data-ttu-id="7f177-162">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-163">Den skrivskyddade egenskapen som hämtar kolumn numret som motsvarar cirkumflexens position.</span><span class="sxs-lookup"><span data-stu-id="7f177-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="7f177-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="7f177-164">CaretLine</span></span>

<span data-ttu-id="7f177-165">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-166">Den skrivskyddade egenskapen som hämtar numret på den rad som innehåller cirkumflexen.</span><span class="sxs-lookup"><span data-stu-id="7f177-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="7f177-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="7f177-167">CaretLineText</span></span>

<span data-ttu-id="7f177-168">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-169">Den skrivskyddade egenskapen som hämtar den fullständiga text raden som innehåller cirkumflex.</span><span class="sxs-lookup"><span data-stu-id="7f177-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="7f177-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="7f177-170">LineCount</span></span>

<span data-ttu-id="7f177-171">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-172">Den skrivskyddade egenskapen som hämtar rad antalet från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="7f177-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="7f177-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="7f177-173">SelectedText</span></span>

<span data-ttu-id="7f177-174">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-175">Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="7f177-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="7f177-176">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="7f177-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="7f177-177">Text</span><span class="sxs-lookup"><span data-stu-id="7f177-177">Text</span></span>

<span data-ttu-id="7f177-178">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="7f177-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="7f177-179">Egenskapen Läs/skriv som hämtar eller anger texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="7f177-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="7f177-180">Se [skript exemplet](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="7f177-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="7f177-181">Skript exempel</span><span class="sxs-lookup"><span data-stu-id="7f177-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7f177-182">Se även</span><span class="sxs-lookup"><span data-stu-id="7f177-182">See Also</span></span>

- [<span data-ttu-id="7f177-183">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="7f177-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="7f177-184">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="7f177-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="7f177-185">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="7f177-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="7f177-186">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="7f177-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
