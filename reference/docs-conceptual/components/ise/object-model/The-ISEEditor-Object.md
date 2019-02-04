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
# <a name="the-iseeditor-object"></a>ISEEditor-objektet

En **ISEEditor** objekt är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEEditor. Konsolfönstret är en **ISEEditor** objekt. Varje [ISEFile](The-ISEFile-Object.md) objekt har en tillhörande **ISEEditor** objekt. I följande avsnitt listas de metoder och egenskaper för en **ISEEditor** objekt.

## <a name="methods"></a>Metoder

### <a name="clear"></a>Rensa\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Tar bort texten i redigeraren.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible\(int lineNumber\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Rullar redigeraren så att raden som som motsvarar det angivna **lineNumber** parametervärdet är synliga. Den genererar ett undantag om angivna radnumret är utanför intervallet för 1, senaste radnummer, som definierar giltiga radnumren.

**lineNumber** antalet rader som ska göras synliga.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Fokus\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger fokus till redigeraren.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength\(int lineNumber \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Hämtar radlängden som ett heltal för raden som anges av radnumret.

**lineNumber** antalet rader som längden ska hämtas.

**Returnerar** radlängden för raden i det angivna radnumret.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Flyttar av cirkumflexet matchande tecken till om den **CanGoToMatch** egenskapen för redigeraren-objektet är **$true**, som uppstår när av cirkumflexet är omedelbart före en vänsterparentes eller hakparentes klammerparentes - \(,\[, {- eller omedelbart efter att en avslutande parentes, hakparenteser och klammerparentes - \),\],}.  Av cirkumflexet är placerad före ett inledande tecken eller efter ett avslutande tecken. Om den **CanGoToMatch** egenskapen är **$false**, och sedan på den här metoden gör ingenting.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText\( text \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Ersätter markeringen med text eller infogar text i den aktuella hatt positionen.

**text** -sträng texten som ska infogas.

Se den [skript exempel](#scripting-example) senare i det här avsnittet.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Välj\( startLine, startColumn, endLine, endColumn \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Markerar text från den **startLine**, **startColumn**, **endLine**, och **endColumn** parametrar.

**startLine** -heltal den rad där valet startar.

**startColumn** -heltal kolumnen i raden start där valet startar.

**endLine** -heltal den rad där markeringen slutar.

**endColumn** -heltal kolumnen i raden slutet där markeringen slutar.

Se den [skript exempel](#scripting-example) senare i det här avsnittet.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Markerar text som innehåller för närvarande av cirkumflexet hela raden.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition\( lineNumber, columnNumber \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger hatt radnumret och kolumnnumret. Den genererar ett undantag om radnumret hatt eller hatt kolumnnummer utanför deras respektive giltiga intervall.

**lineNumber** -heltal radnumret cirkumflexet.

**antal_kolumner anger** -heltal kolumnnummer cirkumflexet.

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

Skrivskyddad boolesk egenskap att indikera om av cirkumflexet är bredvid en parentes, hakparenteser och klammerparentes - \( \), \[ \], {}. Om av cirkumflexet är omedelbart före det inledande tecknet eller direkt efter det avslutande tecknet i ett par så att den här egenskapens värde är **$true**. Annars är **$false**.

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar kolumnnummer som motsvarar positionen för av cirkumflexet.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar antalet rader som innehåller av cirkumflexet.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som får fullständig rad med text som innehåller av cirkumflexet.

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

Se den [skript exempel](#scripting-example) senare i det här avsnittet.

### <a name="text"></a>Text

Stöds i Windows PowerShell ISE 2.0 och senare.

Läs/Skriv-egenskapen som hämtar eller anger texten i redigeraren.

Se den [skript exempel](#scripting-example) senare i det här avsnittet.

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
$endColumn = $myEditor.GetLineLength(3)
# Select the text in the first three lines.
$myEditor.Select(1, 1, 3, $endColumn + 1)
$selection = $myEditor.SelectedText
# Clear all the text in the editor.
$myEditor.Clear()
# Add the selected text back, but in lower case.
$myEditor.InsertText($selection.ToLower())
```

## <a name="see-also"></a>Se även

- [The ISEFile Object](The-ISEFile-Object.md)
- [The PowerShellTab Object](The-PowerShellTab-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)