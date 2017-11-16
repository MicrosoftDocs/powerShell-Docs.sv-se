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
# <a name="the-iseeditor-object"></a>Objektet ISEEditor
  En **ISEEditor** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEEditor. Konsolfönstret är en **ISEEditor** objekt. Varje [ISEFile](The-ISEFile-Object.md) objekt har en associerad **ISEEditor** objekt. I styckena nedan listas de metoder och egenskaper i en **ISEEditor** objekt.

## <a name="methods"></a>Metoder

### <a name="clear"></a>Rensa\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Rensar du texten i redigeraren.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Rullar redigeraren så att raden som som motsvarar det angivna **lineNumber** parametervärdet är synligt. Den genererar ett undantag om det angivna radnumret är utanför intervallet för 1, senaste radnumret, som definierar giltiga radnummer.

 **lineNumber** antalet rader som ska visas.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view. 
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Fokus\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Anger fokus i redigeringsprogrammet.

```powershell
# Sets focus to the Console pane. 
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Hämtar radlängden som ett heltal för den rad som anges av radnumret.

 **lineNumber** antalet rader att hämta längden.

 **Returnerar** radlängden för raden i det angivna radnumret.

```powershell
# Gets the length of the first line in the text of the Command pane. 
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Flyttar hatt matchande tecken till om de **CanGoToMatch** egenskap i objektet editor är **$true**, som uppstår när hatt omedelbart före en vänsterparentes, hakparenteser och klammerparentesen - \(,\[, {- eller omedelbart efter en avslutande parentes, hakparenteser och klammerparentesen - \),\],}.  Hatt är placerad före ett inledande tecken eller efter ett avslutande tecken. Om den **CanGoToMatch** egenskapen är **$false**, och sedan på den här metoden händer ingenting.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace.
```

### <a name="inserttext-text-"></a>InsertText\( text\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Ersätter markeringen med text eller infogar text i den aktuella hatt positionen.

 **text** -sträng text som ska infogas.

 Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Välj\( startLine startColumn, endLine, ska endColumn\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Markerar text från den **startLine**, **startColumn**, **endLine**, och **ska endColumn** parametrar.

 **startLine** -heltal raden där markeringen startar.

 **startColumn** -heltal kolumn i raden start där markeringen startar.

 **endLine** -heltal raden där markeringen slutar.

 **ska endColumn** -heltal kolumnen i slutet raden där markeringen slutar.

 Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.

### <a name="selectcaretline"></a>SelectCaretLine\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Markerar text som innehåller hatt hela raden.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1) 
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber antal_kolumner anger\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Anger hatt radnumret och kolumnnumret. Den genererar ett undantag om radnumret hatt eller kolumnnumret hatt ligger utanför deras respektive giltiga intervall.

 **lineNumber** -heltal hatt numret.

 **antal_kolumner anger** -heltal hatt kolumnnumret.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Gör alla dispositionsavsnitt visa eller dölja.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Egenskaper

### <a name="cangotomatch"></a>CanGoToMatch
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Skrivskyddad booleskt egenskapen för att ange om hatt är bredvid en parentes, hakparenteser och klammerparentesen - \( \), \[ \], {}. Om hatt är omedelbart före det inledande tecknet eller omedelbart efter avslutande tecken i ett par, så det här egenskapsvärdet **$true**. Annars är **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar kolumnnumret som motsvarar positionen för hatt.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar antalet rader som innehåller hatt.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar fullständig rad som innehåller hatt.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar rader räknas från redigeraren.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.

 Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.

### <a name="text"></a>Text
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Egenskapen för läsning och skrivning som hämtar eller anger texten i redigeraren.

 Finns det [Scripting exempel](#scripting-example) senare i det här avsnittet.

## <a name="scripting-example"></a>Exempel-skript

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

## <a name="see-also"></a>Se även
- [Objektet ISEFile](The-ISEFile-Object.md) 
- [Objektet PowerShellTab](The-PowerShellTab-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md)

  
