---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEEditor
ms.openlocfilehash: c593eeebf0b9a94769841efd2aa78f84a3829ca5
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2017
---
# <a name="the-iseeditor-object"></a><span data-ttu-id="2ce08-103">Objektet ISEEditor</span><span class="sxs-lookup"><span data-stu-id="2ce08-103">The ISEEditor Object</span></span>
  <span data-ttu-id="2ce08-104">En **ISEEditor** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEEditor.</span><span class="sxs-lookup"><span data-stu-id="2ce08-104">An **ISEEditor** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEEditor class.</span></span> <span data-ttu-id="2ce08-105">Konsolfönstret är en **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-105">The Console pane is an **ISEEditor** object.</span></span> <span data-ttu-id="2ce08-106">Varje [ISEFile](The-ISEFile-Object.md) objekt har en associerad **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-106">Each [ISEFile](The-ISEFile-Object.md) object has an associated **ISEEditor** object.</span></span> <span data-ttu-id="2ce08-107">I styckena nedan listas de metoder och egenskaper i en **ISEEditor** objekt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-107">The following sections list the methods and properties of an **ISEEditor** object.</span></span>

## <a name="methods"></a><span data-ttu-id="2ce08-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="2ce08-108">Methods</span></span>

### <a name="clear"></a><span data-ttu-id="2ce08-109">Rensa\(\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-109">Clear\(\)</span></span>
  <span data-ttu-id="2ce08-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-111">Rensar du texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="2ce08-111">Clears the text in the editor.</span></span>

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a><span data-ttu-id="2ce08-112">EnsureVisible\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-112">EnsureVisible\(int lineNumber\)</span></span>
  <span data-ttu-id="2ce08-113">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-113">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-114">Rullar redigeraren så att raden som som motsvarar det angivna **lineNumber** parametervärdet är synligt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-114">Scrolls the editor so that the line that corresponds to the specified **lineNumber** parameter value is visible.</span></span> <span data-ttu-id="2ce08-115">Den genererar ett undantag om det angivna radnumret är utanför intervallet för 1, senaste radnumret, som definierar giltiga radnummer.</span><span class="sxs-lookup"><span data-stu-id="2ce08-115">It throws an exception if the specified line number is outside the range of 1,last line number, which defines the valid line numbers.</span></span>

 <span data-ttu-id="2ce08-116">**lineNumber** antalet rader som ska visas.</span><span class="sxs-lookup"><span data-stu-id="2ce08-116">**lineNumber** The number of the line that is to be made visible.</span></span>

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a><span data-ttu-id="2ce08-117">Fokus\(\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-117">Focus\(\)</span></span>
  <span data-ttu-id="2ce08-118">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-119">Anger fokus i redigeringsprogrammet.</span><span class="sxs-lookup"><span data-stu-id="2ce08-119">Sets the focus to the editor.</span></span>

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a><span data-ttu-id="2ce08-120">GetLineLength\(int lineNumber\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-120">GetLineLength\(int lineNumber \)</span></span>
  <span data-ttu-id="2ce08-121">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-121">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-122">Hämtar radlängden som ett heltal för den rad som anges av radnumret.</span><span class="sxs-lookup"><span data-stu-id="2ce08-122">Gets the line length as an integer for the line that is specified by the line number.</span></span>

 <span data-ttu-id="2ce08-123">**lineNumber** antalet rader att hämta längden.</span><span class="sxs-lookup"><span data-stu-id="2ce08-123">**lineNumber** The number of the line of which to get the length.</span></span>

 <span data-ttu-id="2ce08-124">**Returnerar** radlängden för raden i det angivna radnumret.</span><span class="sxs-lookup"><span data-stu-id="2ce08-124">**Returns** The line length for the line at the specified line number.</span></span>

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a><span data-ttu-id="2ce08-125">GoToMatch\(\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-125">GoToMatch\(\)</span></span>
  <span data-ttu-id="2ce08-126">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2ce08-126">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="2ce08-127">Flyttar hatt matchande tecken till om de **CanGoToMatch** egenskap i objektet editor är **$true**, som uppstår när hatt omedelbart före en vänsterparentes, hakparenteser och klammerparentesen - \(,\[, {- eller omedelbart efter en avslutande parentes, hakparenteser och klammerparentesen - \),\],}.</span><span class="sxs-lookup"><span data-stu-id="2ce08-127">Moves the caret to the matching character if the **CanGoToMatch** property of the editor object is **$true**, which occurs when the caret is immediately before an opening parenthesis, bracket, or brace - \(,\[,{ - or immediately after a closing parenthesis, bracket, or brace - \),\],}.</span></span>  <span data-ttu-id="2ce08-128">Hatt är placerad före ett inledande tecken eller efter ett avslutande tecken.</span><span class="sxs-lookup"><span data-stu-id="2ce08-128">The caret is placed before an opening character or after a closing character.</span></span> <span data-ttu-id="2ce08-129">Om den **CanGoToMatch** egenskapen är **$false**, och sedan på den här metoden händer ingenting.</span><span class="sxs-lookup"><span data-stu-id="2ce08-129">If the **CanGoToMatch** property is **$false**, then this method does nothing.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a><span data-ttu-id="2ce08-130">InsertText\( text\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-130">InsertText\( text \)</span></span>
  <span data-ttu-id="2ce08-131">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-131">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-132">Ersätter markeringen med text eller infogar text i den aktuella hatt positionen.</span><span class="sxs-lookup"><span data-stu-id="2ce08-132">Replaces the selection with text or inserts text at the current caret position.</span></span>

 <span data-ttu-id="2ce08-133">**text** -sträng text som ska infogas.</span><span class="sxs-lookup"><span data-stu-id="2ce08-133">**text** - String The text to insert.</span></span>

 <span data-ttu-id="2ce08-134">Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2ce08-134">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="select-startline-startcolumn-endline-endcolumn-"></a><span data-ttu-id="2ce08-135">Välj\( startLine startColumn, endLine, ska endColumn\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-135">Select\( startLine, startColumn, endLine, endColumn \)</span></span>
  <span data-ttu-id="2ce08-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-137">Markerar text från den **startLine**, **startColumn**, **endLine**, och **ska endColumn** parametrar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-137">Selects the text from the **startLine**, **startColumn**, **endLine**, and **endColumn** parameters.</span></span>

 <span data-ttu-id="2ce08-138">**startLine** -heltal raden där markeringen startar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-138">**startLine** - Integer The line where the selection starts.</span></span>

 <span data-ttu-id="2ce08-139">**startColumn** -heltal kolumn i raden start där markeringen startar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-139">**startColumn** - Integer The column within the start line where the selection starts.</span></span>

 <span data-ttu-id="2ce08-140">**endLine** -heltal raden där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-140">**endLine** - Integer The line where the selection ends.</span></span>

 <span data-ttu-id="2ce08-141">**ska endColumn** -heltal kolumnen i slutet raden där markeringen slutar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-141">**endColumn** - Integer The column within the end line where the selection ends.</span></span>

 <span data-ttu-id="2ce08-142">Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2ce08-142">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="selectcaretline"></a><span data-ttu-id="2ce08-143">SelectCaretLine\(\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-143">SelectCaretLine\(\)</span></span>
  <span data-ttu-id="2ce08-144">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-144">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-145">Markerar text som innehåller hatt hela raden.</span><span class="sxs-lookup"><span data-stu-id="2ce08-145">Selects the entire line of text that currently contains the caret.</span></span>

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a><span data-ttu-id="2ce08-146">SetCaretPosition\( lineNumber antal_kolumner anger\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-146">SetCaretPosition\( lineNumber, columnNumber \)</span></span>
  <span data-ttu-id="2ce08-147">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-147">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-148">Anger hatt radnumret och kolumnnumret.</span><span class="sxs-lookup"><span data-stu-id="2ce08-148">Sets the caret position at the line number and the column number.</span></span> <span data-ttu-id="2ce08-149">Den genererar ett undantag om radnumret hatt eller kolumnnumret hatt ligger utanför deras respektive giltiga intervall.</span><span class="sxs-lookup"><span data-stu-id="2ce08-149">It throws an exception if either the caret line number  or the caret column number  are out of their respective valid ranges.</span></span>

 <span data-ttu-id="2ce08-150">**lineNumber** -heltal hatt numret.</span><span class="sxs-lookup"><span data-stu-id="2ce08-150">**lineNumber** - Integer The caret line number.</span></span>

 <span data-ttu-id="2ce08-151">**antal_kolumner anger** -heltal hatt kolumnnumret.</span><span class="sxs-lookup"><span data-stu-id="2ce08-151">**columnNumber** - Integer The caret column number.</span></span>

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a><span data-ttu-id="2ce08-152">ToggleOutliningExpansion\(\)</span><span class="sxs-lookup"><span data-stu-id="2ce08-152">ToggleOutliningExpansion\(\)</span></span>
  <span data-ttu-id="2ce08-153">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2ce08-153">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="2ce08-154">Gör alla dispositionsavsnitt visa eller dölja.</span><span class="sxs-lookup"><span data-stu-id="2ce08-154">Causes all the outline sections to expand or collapse.</span></span>

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a><span data-ttu-id="2ce08-155">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2ce08-155">Properties</span></span>

### <a name="cangotomatch"></a><span data-ttu-id="2ce08-156">CanGoToMatch</span><span class="sxs-lookup"><span data-stu-id="2ce08-156">CanGoToMatch</span></span>
  <span data-ttu-id="2ce08-157">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="2ce08-157">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> 

 <span data-ttu-id="2ce08-158">Skrivskyddad booleskt egenskapen för att ange om hatt är bredvid en parentes, hakparenteser och klammerparentesen - \( \), \[ \], {}.</span><span class="sxs-lookup"><span data-stu-id="2ce08-158">The read-only Boolean property to indicate whether the caret is next to a parenthesis, bracket, or brace - \(\), \[\], {}.</span></span> <span data-ttu-id="2ce08-159">Om hatt är omedelbart före det inledande tecknet eller omedelbart efter avslutande tecken i ett par, så det här egenskapsvärdet **$true**.</span><span class="sxs-lookup"><span data-stu-id="2ce08-159">If the caret is immediately before the opening character or immediately after the closing character of a pair, then this property value is **$true**.</span></span> <span data-ttu-id="2ce08-160">Annars är **$false**.</span><span class="sxs-lookup"><span data-stu-id="2ce08-160">Otherwise, it is **$false**.</span></span>

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a><span data-ttu-id="2ce08-161">CaretColumn</span><span class="sxs-lookup"><span data-stu-id="2ce08-161">CaretColumn</span></span>
  <span data-ttu-id="2ce08-162">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-163">Skrivskyddad egenskap som hämtar kolumnnumret som motsvarar positionen för hatt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-163">The read-only property that gets the column number that corresponds to the position of the caret.</span></span>

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a><span data-ttu-id="2ce08-164">CaretLine</span><span class="sxs-lookup"><span data-stu-id="2ce08-164">CaretLine</span></span>
  <span data-ttu-id="2ce08-165">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-166">Skrivskyddad egenskap som hämtar antalet rader som innehåller hatt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-166">The read-only property that gets the number of the line that contains the caret.</span></span>

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a><span data-ttu-id="2ce08-167">CaretLineText</span><span class="sxs-lookup"><span data-stu-id="2ce08-167">CaretLineText</span></span>
  <span data-ttu-id="2ce08-168">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-168">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-169">Den skrivskyddade egenskapen som hämtar fullständig rad som innehåller hatt.</span><span class="sxs-lookup"><span data-stu-id="2ce08-169">The read-only property that gets the complete line of text that contains the caret.</span></span>

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a><span data-ttu-id="2ce08-170">LineCount</span><span class="sxs-lookup"><span data-stu-id="2ce08-170">LineCount</span></span>
  <span data-ttu-id="2ce08-171">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-171">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-172">Den skrivskyddade egenskapen som hämtar rader räknas från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="2ce08-172">The read-only property that gets the line count from the editor.</span></span>

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a><span data-ttu-id="2ce08-173">SelectedText</span><span class="sxs-lookup"><span data-stu-id="2ce08-173">SelectedText</span></span>
  <span data-ttu-id="2ce08-174">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-174">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-175">Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.</span><span class="sxs-lookup"><span data-stu-id="2ce08-175">The read-only property that gets the selected text from the editor.</span></span>

 <span data-ttu-id="2ce08-176">Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2ce08-176">See the  [Scripting Example](#scripting-example) later in this topic.</span></span>

### <a name="text"></a><span data-ttu-id="2ce08-177">Text</span><span class="sxs-lookup"><span data-stu-id="2ce08-177">Text</span></span>
  <span data-ttu-id="2ce08-178">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ce08-178">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="2ce08-179">Egenskapen för läsning och skrivning som hämtar eller anger texten i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="2ce08-179">The read/write property that gets or sets the text in the editor.</span></span>

 <span data-ttu-id="2ce08-180">Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="2ce08-180">See the [Scripting Example](#scripting-example) later in this topic.</span></span>

## <a name="scripting-example"></a><span data-ttu-id="2ce08-181">Exempel-skript</span><span class="sxs-lookup"><span data-stu-id="2ce08-181">Scripting Example</span></span>

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
$endColumn= $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1,1,3,$endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a><span data-ttu-id="2ce08-182">Se även</span><span class="sxs-lookup"><span data-stu-id="2ce08-182">See Also</span></span>
- [<span data-ttu-id="2ce08-183">Objektet ISEFile</span><span class="sxs-lookup"><span data-stu-id="2ce08-183">The ISEFile Object</span></span>](The-ISEFile-Object.md) 
- [<span data-ttu-id="2ce08-184">Objektet PowerShellTab</span><span class="sxs-lookup"><span data-stu-id="2ce08-184">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="2ce08-185">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="2ce08-185">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="2ce08-186">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="2ce08-186">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="2ce08-187">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="2ce08-187">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)

  
