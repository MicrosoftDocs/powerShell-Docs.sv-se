---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEOptions
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: 5e04adeebacfb9214bf39d9ec9c5f0e01f5729ee
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-iseoptions-object"></a>Objektet ISEOptions
  Den **ISEOptions** -objektet representerar olika inställningar för Windows PowerShell ISE. Det är en instans av den **Microsoft.PowerShell.Host.ISE.ISEOptions** klass.

 Den **ISEOptions** objektet innehåller följande metoder och egenskaper.

## <a name="methods"></a>Metoder

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Återställer standardvärdena för token färgerna i konsolfönstret.

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Återställer standardvärdena för alla inställningarna i konsolfönstret. Också återställs beteendet för olika varningsmeddelanden som tillhandahåller standard kryssrutan för att förhindra att meddelandet visas igen.

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Återställer standardvärdena för token färgerna i skriptfönstret.

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Återställer standardvärdena för token färger för XML-element som visas i Windows PowerShell ISE. Se även [XmlTokenColors](#xmltokencolors).

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Egenskaper

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger antalet minuter mellan automatisk spara operations av dina filer med Windows PowerShell ISE. Standardvärdet är 2 minuter. Värdet är ett heltal.

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

 Anger bakgrundsfärgen för kommando-fönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a>CommandPaneUp
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.

 Anger om kommandot fönstret befinner sig ovanför utdatarutan.

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger bakgrundsfärgen för konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger förgrundsfärgen för texten i konsolfönstret.

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger bakgrundsfärgen för texten i konsolfönstret.

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a>ConsoleTokenColors
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger färgen på IntelliSense-token i fönstret Windows PowerShell ISE-konsolen. Den här egenskapen är ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för konsolfönstret. Om du vill ändra färger IntelliSense-token i skriptfönstret [TokenColors](#tokencolors). Om du vill återställa standardvärdena färger, se [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel.

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger bakgrundsfärgen för debug-texten som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger förgrundsfärgen för debug-text som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a>DefaultOptions
  Stöds i Windows PowerShell ISE 2.0 och senare.

 En uppsättning egenskaper som anger standardvärden som ska användas vid återställning av-metoderna används.

```
# Displays the name of the default options. This example is from ISE 4.0.
$psISE.Options.DefaultOptions

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
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger bakgrundsfärgen för feltext som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger förgrundsfärgen för feltext som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a>Teckensnitt
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger teckensnittet för närvarande används i både skriptfönstret och konsolfönstret.

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a>Teckenstorlek
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger teckenstorleken som ett heltal. Den används i skriptfönstret och fönstret kommandot utdatarutan. Det giltiga intervallet för värden är 8 till 32.

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger antalet sekunder som IntelliSense använder att lösa de för närvarande skriven texten. Efter detta antal sekunder IntelliSense timeout och du kan fortsätta att skriva. Standardvärdet är 3 sekunder. Värdet är ett heltal.

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger antalet nyligen öppnade filer som Windows PowerShell ISE spårar och visar längst ned i den **öppna** menyn. Standardvärdet är 10. Värdet är ett heltal.

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

 Egenskapen för läsning och skrivning som hämtar eller anger bakgrundsfärgen för fönstret utdata. Det är en instans av den **System.Windows.Media.Color** klass.

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

 Egenskapen för läsning och skrivning som ändrar förgrundsfärgen för texten i fönstret utdata i Windows PowerShell ISE 2.0.

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

 Egenskapen för läsning och skrivning som ändrar bakgrundsfärgen för texten i utdatarutan.

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Egenskapen för läsning och skrivning som hämtar eller anger bakgrundsfärgen för filer. Det är en instans av den **System.Windows.Media.Color** klass.

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Egenskapen för läsning och skrivning som hämtar eller anger förgrundsfärgen för icke-skriptfiler i skriptfönstret.
Förgrundsfärgen för skriptfiler, använder den [TokenColors](#tokencolors).

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Egenskapen för läsning och skrivning som hämtar eller anger placeringen av skriptfönstret på skärmen. Strängen kan vara antingen ”maximerat”, ”Top” eller ”höger”.

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om den **CTRL + J** lista med kodavsnitt inkluderar starter som ingår i Windows PowerShell. Om värdet är **$false**, användardefinierade kodavsnitt som visas i den **CTRL + J** lista. Standardvärdet är **$true**.

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om IntelliSense erbjuder syntax och parametern förslag för värde i konsolfönstret. Standardvärdet är **$true**.

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om IntelliSense erbjuder syntax och parametern förslag för värde i skriptfönstret. Standardvärdet är **$true**.

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om skriptfönstret Visar radnummer i vänster marginal. Standardvärdet är **$true**.

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om skriptfönstret visar expanderas och döljas hakparenteser bredvid kodavsnitt i vänster marginal. När de visas, du kan klicka på Minuset \( - \) ikoner bredvid ett textblock minimera den eller klicka på plustecknet \( + \) ikon för att expandera ett block med text. Standardvärdet är **$true**.

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger om verktygsfältet ISE visas överst i fönstret Windows PowerShell ISE. Standardvärdet är **$true**.

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger om ett varningsmeddelande visas när ett skript sparas automatiskt innan den körs. Standardvärdet är **$true**.

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger om ett varningsmeddelande visas när samma fil öppnas i olika PowerShell flikar. Om värdet **$true**, för att öppna samma fil i flera flikar visas det här meddelandet: ”en kopia av den här filen är öppen i en annan flik i Windows PowerShell. Ändringar som gjorts i den här filen tas bort påverkas alla öppna kopior ”. Standardvärdet är **$true**.

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a>TokenColors
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger färgen på IntelliSense-token i fönstret Windows PowerShell ISE-skript. Den här egenskapen är ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för skriptfönstret. Om du vill ändra färger IntelliSense-token i konsolfönstret [ConsoleTokenColors](#consoletokencolors). Om du vill återställa standardvärdena färger, se [RestoreDefaultTokenColors](#restoredefaulttokencolors). Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel.

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om du använder RETUR-tangenten för att välja en IntelliSense tillhandahålls alternativet i konsolfönstret. Standardvärdet är **$true**.

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om du kan använda RETUR-tangenten för att välja ett alternativ för angivna IntelliSense i skriptfönstret. Standardvärdet är **$true**.

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a>UseLocalHelp
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger om lokalt installerade hjälp eller den TechNet Library onlinehjälp visas när du trycker på F1 med markören placeras i ett nyckelord. Om värdet **$true**, och sedan ett popup-fönster visar innehåll från lokalt installerade hjälp. Du kan installera hjälpfiler genom att köra den `Update-Help` kommando. Om värdet **$false**, webbläsaren öppnas på en sida i TechNet-biblioteket.

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger bakgrundsfärgen för utförlig text som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger förgrundsfärgen för utförlig text som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger bakgrundsfärgen för varningstext som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor
  Stöds i Windows PowerShell ISE 2.0 och senare.

 Anger förgrundsfärgen för varningstext som visas i utdatarutan. Det är en **System.Windows.Media.Color** objekt.

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för XML-innehåll som visas i Windows PowerShell ISE. Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel. Se även [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a>Zooma
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

 Anger den relativa storleken på texten i både konsolen och skript. Standardvärdet är 100. Lägre värden orsaka texten i Windows PowerShell ISE ska vara mindre medan större tal orsakar text ska visas större. Värdet är ett heltal som sträcker sig från 20 till 400.

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Se även
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md)
