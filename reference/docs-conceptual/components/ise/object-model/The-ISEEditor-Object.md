---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEEditor-objektet
ms.openlocfilehash: 2d4c3d941035384c591ca57e809c0e3a9b852f5c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686154"
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="cab57-103">ISEEditor-objektet</span><span class="sxs-lookup"><span data-stu-id="cab57-103">The ISEEditor Object</span></span>

<span data-ttu-id="cab57-104">En **ISEEditor** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="cab57-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="cab57-105">Konsolfönstret är en **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="cab57-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="cab57-106">Varje [ISEFile](The-ISEFile-Object.md) objekt har en tillhörande **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="cab57-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="cab57-107">I följande avsnitt listas de metoder och egenskaper för en **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="cab57-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="cab57-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="cab57-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="cab57-109">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="cab57-109">Clear\(\)</span></span>

<span data-ttu-id="cab57-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-111">Tar bort texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="cab57-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="cab57-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="cab57-112">EnsureVisible\(int lineNumber\)</span></span>

<span data-ttu-id="cab57-113">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-114">Rullar redigeraren så att raden som som motsvarar det angivna **lineNumber** parametervärdet är synliga.</span><span class="sxs-lookup"><span data-stu-id="cab57-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="cab57-115">Den genererar ett undantag om angivna radnumret är utanför intervallet för 1, senaste radnummer, som definierar giltiga radnumren.</span><span class="sxs-lookup"><span data-stu-id="cab57-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

<span data-ttu-id="cab57-116">**lineNumber** antalet rader som ska göras synliga.</span><span class="sxs-lookup"><span data-stu-id="cab57-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="cab57-117">Fokus\(\)</span><span class="sxs-lookup"><span data-stu-id="cab57-117">Focus\(\)</span></span>

<span data-ttu-id="cab57-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-119">Anger fokus till redigeraren.</span><span class="sxs-lookup"><span data-stu-id="cab57-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="cab57-120">GetLineLength\(int lineNumber \)</span><span class="sxs-lookup"><span data-stu-id="cab57-120">GetLineLength\(int lineNumber \)</span></span>

<span data-ttu-id="cab57-121">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-122">Hämtar radlängden som ett heltal för raden som anges av radnumret.</span><span class="sxs-lookup"><span data-stu-id="cab57-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

<span data-ttu-id="cab57-123">**lineNumber** antalet rader som längden ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="cab57-123">**lineNumber** The number of the line of which to get the length.</span></span>

<span data-ttu-id="cab57-124">**Returnerar** radlängden för raden i det angivna radnumret.</span><span class="sxs-lookup"><span data-stu-id="cab57-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="cab57-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="cab57-125">GoToMatch\(\)</span></span>

<span data-ttu-id="cab57-126">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="cab57-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cab57-127">Flyttar av cirkumflexet matchande tecken till om den **CanGoToMatch** egenskapen för redigeraren-objektet är **$true**, som uppstår när av cirkumflexet är omedelbart före en vänsterparentes eller hakparentes klammerparentes - \(,\[, {- eller omedelbart efter att en avslutande parentes, hakparenteser och klammerparentes - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="cab57-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="cab57-128">Av cirkumflexet är placerad före ett inledande tecken eller efter ett avslutande tecken.</span><span class="sxs-lookup"><span data-stu-id="cab57-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="cab57-129">Om den **CanGoToMatch** egenskapen är **$false**, och sedan på den här metoden gör ingenting.</span><span class="sxs-lookup"><span data-stu-id="cab57-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a><span data-ttu-id="cab57-130">InsertText\( text \)</span><span class="sxs-lookup"><span data-stu-id="cab57-130">InsertText\( text \)</span></span>

<span data-ttu-id="cab57-131">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-132">Ersätter markeringen med text eller infogar text i den aktuella hatt positionen.</span><span class="sxs-lookup"><span data-stu-id="cab57-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

<span data-ttu-id="cab57-133">**text** -sträng texten som ska infogas.</span><span class="sxs-lookup"><span data-stu-id="cab57-133">**text** - String The text to insert.</span></span>

<span data-ttu-id="cab57-134">Se den [skript exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="cab57-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="cab57-135">Välj\( startLine, startColumn, endLine, endColumn \)</span><span class="sxs-lookup"><span data-stu-id="cab57-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>

<span data-ttu-id="cab57-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-137">Markerar text från den **startLine**, **startColumn**, **endLine**, och **endColumn** parametrar.</span><span class="sxs-lookup"><span data-stu-id="cab57-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

<span data-ttu-id="cab57-138">**startLine** -heltal den rad där valet startar.</span><span class="sxs-lookup"><span data-stu-id="cab57-138">**startLine** - Integer The line where the selection starts.</span></span>

<span data-ttu-id="cab57-139">**startColumn** -heltal kolumnen i raden start där valet startar.</span><span class="sxs-lookup"><span data-stu-id="cab57-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

<span data-ttu-id="cab57-140">**endLine** -heltal den rad där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="cab57-140">**endLine** - Integer The line where the selection ends.</span></span>

<span data-ttu-id="cab57-141">**endColumn** -heltal kolumnen i raden slutet där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="cab57-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

<span data-ttu-id="cab57-142">Se den [skript exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="cab57-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="cab57-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="cab57-143">SelectCaretLine\(\)</span></span>

<span data-ttu-id="cab57-144">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-145">Markerar text som innehåller för närvarande av cirkumflexet hela raden.</span><span class="sxs-lookup"><span data-stu-id="cab57-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="cab57-146">SetCaretPosition\( lineNumber, columnNumber \)</span><span class="sxs-lookup"><span data-stu-id="cab57-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>

<span data-ttu-id="cab57-147">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-148">Anger hatt radnumret och kolumnnumret.</span><span class="sxs-lookup"><span data-stu-id="cab57-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="cab57-149">Den genererar ett undantag om radnumret hatt eller hatt kolumnnummer utanför deras respektive giltiga intervall.</span><span class="sxs-lookup"><span data-stu-id="cab57-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

<span data-ttu-id="cab57-150">**lineNumber** -heltal radnumret cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="cab57-150">**lineNumber** - Integer The caret line number.</span></span>

<span data-ttu-id="cab57-151">**antal_kolumner anger** -heltal kolumnnummer cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="cab57-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="cab57-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="cab57-152">ToggleOutliningExpansion\(\)</span></span>

<span data-ttu-id="cab57-153">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="cab57-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cab57-154">Gör alla dispositionsavsnitt visa eller dölja.</span><span class="sxs-lookup"><span data-stu-id="cab57-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="cab57-155">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="cab57-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="cab57-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="cab57-156">CanGoToMatch</span></span>

<span data-ttu-id="cab57-157">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="cab57-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="cab57-158">Skrivskyddad boolesk egenskap att indikera om av cirkumflexet är bredvid en parentes, hakparenteser och klammerparentes - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="cab57-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="cab57-159">Om av cirkumflexet är omedelbart före det inledande tecknet eller direkt efter det avslutande tecknet i ett par så att den här egenskapens värde är **$true**.</span><span class="sxs-lookup"><span data-stu-id="cab57-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="cab57-160">Annars är **$false**.</span><span class="sxs-lookup"><span data-stu-id="cab57-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="cab57-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="cab57-161">CaretColumn</span></span>

<span data-ttu-id="cab57-162">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-163">Skrivskyddad egenskap som hämtar kolumnnummer som motsvarar positionen för av cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="cab57-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="cab57-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="cab57-164">CaretLine</span></span>

<span data-ttu-id="cab57-165">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-166">Skrivskyddad egenskap som hämtar antalet rader som innehåller av cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="cab57-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="cab57-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="cab57-167">CaretLineText</span></span>

<span data-ttu-id="cab57-168">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-169">Den skrivskyddade egenskapen som får fullständig rad med text som innehåller av cirkumflexet.</span><span class="sxs-lookup"><span data-stu-id="cab57-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="cab57-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="cab57-170">LineCount</span></span>

<span data-ttu-id="cab57-171">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-172">Den skrivskyddade egenskapen som hämtar rader räknas från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="cab57-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="cab57-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="cab57-173">SelectedText</span></span>

<span data-ttu-id="cab57-174">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-175">Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="cab57-175">The read-only property that gets the selected text from the editor.</span></span>

<span data-ttu-id="cab57-176">Se den [skript exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="cab57-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="cab57-177">Text</span><span class="sxs-lookup"><span data-stu-id="cab57-177">Text</span></span>

<span data-ttu-id="cab57-178">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="cab57-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cab57-179">Läs/Skriv-egenskapen som hämtar eller anger texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="cab57-179">The read/write property that gets or sets the text in the editor.</span></span>

<span data-ttu-id="cab57-180">Se den [skript exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="cab57-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="cab57-181">Exempel-skript</span><span class="sxs-lookup"><span data-stu-id="cab57-181">Scripting Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cab57-182">Se även</span><span class="sxs-lookup"><span data-stu-id="cab57-182">See Also</span></span>

- [<span data-ttu-id="cab57-183">The ISEFile Object</span><span class="sxs-lookup"><span data-stu-id="cab57-183">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="cab57-184">The PowerShellTab Object</span><span class="sxs-lookup"><span data-stu-id="cab57-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="cab57-185">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="cab57-185">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cab57-186">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="cab57-186">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)