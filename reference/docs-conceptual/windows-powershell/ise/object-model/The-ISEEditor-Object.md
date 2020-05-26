---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEEditor-objektet
ms.openlocfilehash: cb63acebc1a8bb9fa6cc07199088ae0d5441bc91
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811018"
---
# <a name="the-iseeditor-object"></a>ISEEditor-objektet

Ett **ISEEditor** -objekt är en instans av klassen Microsoft. PowerShell. Host. ISE. ISEEditor. Konsol fönstret är ett **ISEEditor** -objekt. Varje [ISEFile](The-ISEFile-Object.md) -objekt har ett associerat **ISEEditor** -objekt. I följande avsnitt listas metoder och egenskaper för ett **ISEEditor** -objekt.

## <a name="methods"></a>Metoder

### <a name="clear"></a>Rensa\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Tar bort texten i redigeraren.

```powershell
# Clears the text in the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Clear()
```

### <a name="ensurevisibleint-linenumber"></a>EnsureVisible \( int lineNumber\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Rullar i redigeraren så att den rad som motsvarar det angivna värdet för parametern **lineNumber** är synlig. Ett undantag genereras om det angivna rad numret ligger utanför intervallet 1, sista rad numret, som definierar giltiga rad nummer.

**lineNumber** Numret på raden som ska göras synlig.

```powershell
# Scrolls the text in the Script pane so that the fifth line is in view.
$psISE.CurrentFile.Editor.EnsureVisible(5)
```

### <a name="focus"></a>Aktiv\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Ställer in fokus på redigeraren.

```powershell
# Sets focus to the Console pane.
$psISE.CurrentPowerShellTab.ConsolePane.Focus()
```

### <a name="getlinelengthint-linenumber-"></a>GetLineLength \( int lineNumber\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Hämtar rad längden som ett heltal för raden som anges av rad numret.

**lineNumber** Numret på den linje som längden ska hämtas från.

**Returnerar** Rad längden för raden vid det angivna rad numret.

```powershell
# Gets the length of the first line in the text of the Command pane.
$psISE.CurrentPowerShellTab.ConsolePane.GetLineLength(1)
```

### <a name="gotomatch"></a>GoToMatch\(\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Flyttar cirkumflexet till det matchande tecknet om egenskapen **CanGoToMatch** för Editor-objektet är `$true` , vilket inträffar när cirkumflexet är omedelbart före en inledande parentes, hak paren tes eller klammerparentes,, `(` `[` , `{` eller omedelbart efter en avslutande parentes, hak `)` `]` `}` paren tes eller klammerparentes,,,. Cirkumflexet placeras före ett inledande tecken eller efter ett avslutande tecken. Om egenskapen **CanGoToMatch** är är `$false` den här metoden ingenting.

```powershell
# Goes to the matching character if CanGoToMatch() is $true
$psISE.CurrentPowerShellTab.ConsolePane.GoToMatch()
```

### <a name="inserttext-text-"></a>InsertText- \( text\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Ersätter markeringen med text eller infogar text vid den aktuella cirkumflexens position.

**text** – sträng texten som ska infogas.

Se [skript exemplet](#scripting-example) senare i det här avsnittet.

### <a name="select-startline-startcolumn-endline-endcolumn-"></a>Välj \( startline, startColumn, SourceLocation, endColumn\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Markerar texten från parametrarna **startline**, **startColumn**, **SourceLocation**och **endColumn** .

**startline** – heltals linjen där valet börjar.

**startColumn** – Integer kolumnen i Start raden där markeringen börjar.

**SourceLocation** – heltals linjen där markeringen slutar.

**endColumn** – Markera kolumnen i slut raden där markeringen slutar.

Se [skript exemplet](#scripting-example) senare i det här avsnittet.

### <a name="selectcaretline"></a>SelectCaretLine\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Markerar hela text raden som för närvarande innehåller cirkumflex.

```powershell
# First, set the caret position on line 5.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
# Now select that entire line of text
$psISE.CurrentFile.Editor.SelectCaretLine()
```

### <a name="setcaretposition-linenumber-columnnumber-"></a>SetCaretPosition \( lineNumber, columnNumber\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger cirkumflexens position i rad numret och kolumn numret. Ett undantag utlöses om antingen cirkumflexets rad nummer eller cirkumflex kolumn numret inte är av respektive giltiga intervall.

**lineNumber** – heltals markörens rad nummer.

**columnNumber** – heltal för kolumn numret i cirkumflexet.

```powershell
# Set the CaretPosition.
$psISE.CurrentFile.Editor.SetCaretPosition(5,1)
```

### <a name="toggleoutliningexpansion"></a>ToggleOutliningExpansion\(\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Gör så att alla dispositions avsnitt expanderas eller komprimeras.

```powershell
# Toggle the outlining expansion
$psISE.CurrentFile.Editor.ToggleOutliningExpansion()
```

## <a name="properties"></a>Egenskaper

### <a name="cangotomatch"></a>CanGoToMatch

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade booleska egenskapen som anger om cirkumflexet infaller vid en parentes, hak paren tes eller klammerparentes, `()` `[]` ,, `{}` . Om cirkumflexet är omedelbart före det inledande tecknet eller omedelbart efter det avslutande tecknet i ett par, är det här egenskap svärdet `$true` . Annars är det `$false` .

```powershell
# Test to see if the caret is next to a parenthesis, bracket, or brace
$psISE.CurrentFile.Editor.CanGoToMatch
```

### <a name="caretcolumn"></a>CaretColumn

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar kolumn numret som motsvarar cirkumflexens position.

```powershell
# Get the CaretColumn.
$psISE.CurrentFile.Editor.CaretColumn
```

### <a name="caretline"></a>CaretLine

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar numret på den rad som innehåller cirkumflexen.

```powershell
# Get the CaretLine.
$psISE.CurrentFile.Editor.CaretLine
```

### <a name="caretlinetext"></a>CaretLineText

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den fullständiga text raden som innehåller cirkumflex.

```powershell
# Get all of the text on the line that contains the caret.
$psISE.CurrentFile.Editor.CaretLineText
```

### <a name="linecount"></a>LineCount

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar rad antalet från redigeraren.

```powershell
# Get the LineCount.
$psISE.CurrentFile.Editor.LineCount
```

### <a name="selectedtext"></a>SelectedText

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den markerade texten från redigeraren.

Se [skript exemplet](#scripting-example) senare i det här avsnittet.

### <a name="text"></a>Text

Stöds i Windows PowerShell ISE 2,0 och senare.

Egenskapen Läs/skriv som hämtar eller anger texten i redigeraren.

Se [skript exemplet](#scripting-example) senare i det här avsnittet.

## <a name="scripting-example"></a>Skript exempel

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

- [ISEFile-objektet](The-ISEFile-Object.md)
- [PowerShellTab-objektet](The-PowerShellTab-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
