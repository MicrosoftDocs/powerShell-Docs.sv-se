---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEOptions-objektet
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736955"
---
# <a name="the-iseoptions-object"></a>ISEOptions-objektet

Objektet **ISEOptions** representerar olika inställningar för Windows PowerShell ISE. Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEOptions** .

**ISEOptions** -objektet tillhandahåller följande metoder och egenskaper.

## <a name="methods"></a>Metoder

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Återställer standardvärdena för token-färgerna i konsol fönstret.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Återställer standardvärdena för alla alternativ inställningar i konsol fönstret. Den återställer också beteendet för olika varnings meddelanden som innehåller kryss rutan standard för att förhindra att meddelandet visas igen.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Återställer standardvärdena för token-färgerna i skript fönstret.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Återställer standardvärdena för token-färgerna för XML-element som visas i Windows PowerShell ISE. Se även [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Egenskaper

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger antalet minuter mellan automatiska sparade åtgärder för dina filer med Windows PowerShell ISE. Standardvärdet är 2 minuter. Värdet är ett heltal.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE. För senare versioner, se [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Anger bakgrunds färgen för kommando fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.

Anger om kommando fönstret finns ovanför fönstret utdata.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger bakgrunds färgen för konsol fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger förgrunds färgen för texten i konsol fönstret.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger bakgrunds färgen för texten i konsol fönstret.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger färgerna i IntelliSense-tokens i Windows PowerShell ISE konsol fönstret. Den här egenskapen är ett Dictionary-objekt som innehåller namn/värde-par av tokens och färger för konsol fönstret. Om du vill ändra färgerna i IntelliSense-tokens i skript fönstret, se [TokenColors](#tokencolors).
Information om hur du återställer färgerna till standardvärdena finns i [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).
Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, Okänd, variabel.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger bakgrunds färgen för fel söknings texten som visas i konsol fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger förgrunds färgen för fel söknings texten som visas i konsol fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Stöds i Windows PowerShell ISE 2,0 och senare.

En samling egenskaper som anger de standardvärden som ska användas när återställnings metoderna används.

```powershell
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions
```

```Output
SelectedScriptPaneState                   : Top
ShowDefaultSnippets                       : True
ShowToolBar                               : True
ShowOutlining                             : True
ShowLineNumbers                           : True
TokenColors                               : {[Attribute, #FF00BFFF], [Command, #FF0000FF], [CommandArgument, #FF8A2BE2], [CommandParameter, #FF000080]...}
ConsoleTokenColors                        : {[Attribute, #FFB0C4DE], [Command, #FFE0FFFF], [CommandArgument, #FFEE82EE], [CommandParameter, #FFFFE4B5]...}
XmlTokenColors                            : {[Comment, #FF006400], [CommentDelimiter, #FF008000], [ElementName, #FF8B0000], [MarkupExtension, #FFFF8C00]...}
DefaultOptions                            : Microsoft.PowerShell.Host.ISE.ISEOptions
FontSize                                  : 9
Zoom                                      : 100
FontName                                  : Lucida Console
ErrorForegroundColor                      : #FFFF0000
ErrorBackgroundColor                      : #00FFFFFF
WarningForegroundColor                    : #FFFF8C00
WarningBackgroundColor                    : #00FFFFFF
VerboseForegroundColor                    : #FF00FFFF
VerboseBackgroundColor                    : #00FFFFFF
DebugForegroundColor                      : #FF00FFFF
DebugBackgroundColor                      : #00FFFFFF
ConsolePaneBackgroundColor                : #FF012456
ConsolePaneTextBackgroundColor            : #FF012456
ConsolePaneForegroundColor                : #FFF5F5F5
ScriptPaneBackgroundColor                 : #FFFFFFFF
ScriptPaneForegroundColor                 : #FF000000
ShowWarningForDuplicateFiles              : True
ShowWarningBeforeSavingOnRun              : True
UseLocalHelp                              : True
AutoSaveMinuteInterval                    : 2
MruCount                                  : 10
ShowIntellisenseInConsolePane             : True
ShowIntellisenseInScriptPane              : True
UseEnterToSelectInConsolePaneIntellisense : True
UseEnterToSelectInScriptPaneIntellisense  : True
IntellisenseTimeoutInSeconds              : 3
```

### <a name="errorbackgroundcolor"></a>ErrorBackgroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger bakgrunds färgen för fel text som visas i konsol fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger förgrunds färgen för fel text som visas i konsol fönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>FontName

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger teckensnitts namnet som används i både skript fönstret och konsol fönstret.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger tecken storleken som ett heltal. Den används i skript fönstret, kommando fönstret och fönstret utdata. Det giltiga värde intervallet är 8 till 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger hur många sekunder som IntelliSense använder för att försöka lösa den text som är skriven för tillfället.
Efter det här antalet sekunder kan IntelliSense-tiden ta slut och du kan fortsätta att skriva. Standardvärdet är 3 sekunder. Värdet är ett heltal.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger antalet nyligen öppnade filer som Windows PowerShell ISE spårar och visas längst ned på menyn **Öppna** . Standardvärdet är 10. Värdet är ett heltal.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE. För senare versioner, se [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Egenskapen Läs/skriv som hämtar eller anger bakgrunds färgen för själva utdatafönstret. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE. För senare versioner, se [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

Egenskapen Läs/skriv som ändrar förgrunds färgen för texten i fönstret utdata i Windows PowerShell ISE 2,0.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE. För senare versioner, se [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

Egenskapen Läs/skriv som ändrar bakgrunds färgen för texten i fönstret utdata.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Egenskapen Läs/skriv som hämtar eller anger bakgrunds färgen för filer. Det är en instans av klassen **system. Windows. Media. Color** .

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Egenskapen Läs/skriv som hämtar eller anger förgrunds färgen för filer som inte är skriptfiler i skript fönstret.
Om du vill ange förgrunds färgen för skriptfiler använder du [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Stöds i Windows PowerShell ISE 2,0 och senare.

Egenskapen Läs/skriv som hämtar eller anger positionen för skript fönstret på skärmen. Strängen kan vara antingen "maximerad", "Top" eller "Right".

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om <kbd>CTRL</kbd>+<kbd>J</kbd> -listan över kodfragment innehåller den Start uppsättning som ingår i Windows PowerShell. När det är inställt på `$false`, visas bara användardefinierade kod avsnitt i den <kbd>CTRL</kbd>+<kbd>J</kbd> -listan.
Standardvärdet är `$true`.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om IntelliSense erbjuder syntax, parameter och värde förslag i konsol fönstret.
Standardvärdet är `$true`.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om IntelliSense erbjuder syntax, parameter och värde förslag i fönstret skript.
Standardvärdet är `$true`.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om fönstret skript visar rad nummer i vänstermarginalen. Standardvärdet är `$true`.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om skript fönstret visar expanderbara och komprimerbara hakparenteser bredvid avsnitt i kod i vänstermarginalen. När de visas kan du klicka på minus `-` ikonerna bredvid ett textblock för att komprimera den eller klicka på plus `+`-ikonen för att expandera ett textblock. Standardvärdet är `$true`.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger om ISE-verktygsfältet visas överst i Windows PowerShell ISEs fönstret. Standardvärdet är `$true`.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger om ett varnings meddelande visas när ett skript sparas automatiskt innan det körs.
Standardvärdet är `$true`.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger om ett varnings meddelande visas när samma fil öppnas i olika PowerShell-flikar. Om värdet är `$true`för att öppna samma fil på flera flikar visas följande meddelande: "en kopia av filen är öppen på en annan Windows PowerShell-flik. ändringar i den här filen kommer att påverka alla öppna kopior." Standardvärdet är `$true`.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger färgerna i IntelliSense-tokens i rutan Windows PowerShell ISE skript. Den här egenskapen är ett Dictionary-objekt som innehåller namn-/värdepar med token-typer och färger för skript fönstret. Om du vill ändra färgerna i IntelliSense-tokens i konsol fönstret, se [ConsoleTokenColors](#consoletokencolors).
Information om hur du återställer färgerna till standardvärdena finns i [RestoreDefaultTokenColors](#restoredefaulttokencolors).
Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, Okänd, variabel.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om du kan använda RETUR-tangenten för att välja ett IntelliSense-alternativ i konsol fönstret. Standardvärdet är `$true`.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om du kan använda RETUR-tangenten för att välja ett IntelliSense-alternativ i skript fönstret. Standardvärdet är `$true`.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger om den lokalt installerade hjälpen eller online TechNet Library-hjälpen visas när du trycker på <kbd>F1</kbd> med markören placerad i ett nyckelord. Om värdet är `$true`visar ett popup-fönster innehåll från den lokalt installerade hjälpen. Du kan installera hjälpfilerna genom att köra kommandot `Update-Help`. Om värdet är `$false`öppnas webbläsaren på en sida i TechNet-biblioteket.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger bakgrunds färgen för utförlig text som visas i konsol fönstret. Det är ett **system. Windows. Media. Color** -objekt.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger förgrunds färgen för utförlig text som visas i konsol fönstret. Det är ett **system. Windows. Media. Color** -objekt.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger bakgrunds färgen för varnings text som visas i konsol fönstret. Det är ett **system. Windows. Media. Color** -objekt.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Stöds i Windows PowerShell ISE 2,0 och senare.

Anger förgrunds färgen för varnings text som visas i fönstret utdata. Det är ett **system. Windows. Media. Color** -objekt.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger ett Dictionary-objekt som innehåller namn/värde-par av tokens och färger för XML-innehåll som visas i Windows PowerShell ISE. Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, Okänd, variabel. Se även [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zoom

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Anger den relativa storleken på text i både konsol-och skript fönstret. Standardvärdet är 100.
Mindre värden gör att texten i Windows PowerShell ISE visas mindre medan större tal gör att texten blir större. Värdet är ett heltal som sträcker sig från 20 till 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Se även

- [Syftet med Windows PowerShell ISE-skriptets objekt modell](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
