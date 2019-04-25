---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEOptions-objektet
ms.assetid: 75e2a76f-f3d1-490b-ad5d-e3829946aabb
ms.openlocfilehash: e756da21aaa5465f7fa6a90563b4180f0c89e87b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057782"
---
# <a name="the-iseoptions-object"></a>ISEOptions-objektet

Den **ISEOptions** -objektet representerar olika inställningar för Windows PowerShell ISE. Det är en instans av den **Microsoft.PowerShell.Host.ISE.ISEOptions** klass.

Den **ISEOptions** objektet innehåller följande metoder och egenskaper.

## <a name="methods"></a>Metoder

### <a name="restoredefaultconsoletokencolors"></a>RestoreDefaultConsoleTokenColors\(\)

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Återställer standardvärdena för token färger i konsolfönstret.

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a>RestoreDefaults\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Återställer standardvärdena för alla inställningar i konsolfönstret. Också återställs beteendet för olika varningsmeddelanden som tillhandahåller kryssrutan standard för att förhindra att meddelandet visas igen.

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a>RestoreDefaultTokenColors\(\)

Stöds i Windows PowerShell ISE 2.0 och senare.

Återställer standardvärdena för token färgerna i skriptfönstret.

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a>RestoreDefaultXmlTokenColors\(\)

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Återställer standardvärdena för token färgerna för XML-element som visas i Windows PowerShell ISE. Se även [XmlTokenColors](#xmltokencolors).

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a>Egenskaper

### <a name="autosaveminuteinterval"></a>AutoSaveMinuteInterval

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger antalet minuter mellan Spara automatiskt driften av dina filer genom att Windows PowerShell ISE. Standardvärdet är 2 minuter. Värdet är ett heltal.

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a>CommandPaneBackgroundColor

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Anger bakgrundsfärgen för kommando-fönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a>CommandPaneUp

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.

Anger om fönstret kommando befinner sig ovanför utdatarutan.

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a>ConsolePaneBackgroundColor

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger bakgrundsfärgen för konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a>ConsolePaneForegroundColor

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger förgrundsfärgen för texten i konsolfönstret.

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a>ConsolePaneTextBackgroundColor

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger bakgrundsfärgen för texten i konsolfönstret.

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a>ConsoleTokenColors

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger färgerna för token som IntelliSense i fönstret Windows PowerShell ISE-konsolen. Den här egenskapen är en Ordlisteobjekt som innehåller namn/värde-par av tokentyper och färger för konsolfönstret. Om du vill ändra färger IntelliSense token i skriptfönstret [TokenColors](#tokencolors). Om du vill återställa färgerna standardvärdena, se [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors). Token färger kan anges för följande: Attribut, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, tal, Operator, Position, StatementSeparator, sträng, typ, Okänd, variabel.

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a>DebugBackgroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger bakgrundsfärgen för den debug-text som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a>DebugForegroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger förgrundsfärgen för debug-text som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a>DefaultOptions

Stöds i Windows PowerShell ISE 2.0 och senare.

En uppsättning egenskaper som anger standardvärden som ska användas vid återställning av-metoderna används.

```powershell
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

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a>ErrorForegroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger förgrundsfärgen för feltext som visas i konsolfönstret. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a>Teckensnitt

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger namn på för närvarande används i både skriptfönstret och konsolfönstret.

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a>FontSize

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger teckenstorleken som ett heltal. Den används i skriptfönstret och fönstret kommando utdatarutan. Det giltiga värdeintervallet är 8 till 32.

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a>IntellisenseTimeoutInSeconds

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger antalet sekunder som IntelliSense använder för att försöka lösa för närvarande skrivna texten. Efter det här antalet sekunder, IntelliSense tidsgränsen och gör att du kan fortsätta att skriva. Standardvärdet är 3 sekunder. Värdet är ett heltal.

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a>MruCount

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger hur många nyligen öppnade filer som Windows PowerShell ISE spårar och visas längst ned på den **öppna** menyn. Standardvärdet är 10. Värdet är ett heltal.

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a>OutputPaneBackgroundColor

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).

Läs/Skriv-egenskapen som hämtar eller anger bakgrundsfärgen för fönstret utdata. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a>OutputPaneTextForegroundColor

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneForegroundColor](#consolepaneforegroundcolor).

Läs/Skriv-egenskap som ändras förgrundsfärgen för texten i utdatafönstret i Windows PowerShell ISE 2.0.

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a>OutputPaneTextBackgroundColor

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.  Senare versioner finns [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).

Läs/Skriv-egenskap som ändrar bakgrundsfärgen för texten i utdatarutan.

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a>ScriptPaneBackgroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Läs/Skriv-egenskapen som hämtar eller anger bakgrundsfärgen för filer. Det är en instans av den **System.Windows.Media.Color** klass.

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a>ScriptPaneForegroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Läs/Skriv-egenskapen som hämtar eller anger förgrundsfärgen för icke-skriptfiler i skriptfönstret.
Ange förgrundsfärgen för skriptfiler och den [TokenColors](#tokencolors).

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a>SelectedScriptPaneState

Stöds i Windows PowerShell ISE 2.0 och senare.

Läs/Skriv-egenskapen som hämtar eller anger positionen för skriptfönstret på skärmen. Strängen kan vara antingen ”maximerat”, ”Top” eller ”höger”.

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a>ShowDefaultSnippets

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om den **CTRL + J** lista med kodavsnitt omfattar starter-grupp som ingår i Windows PowerShell. När värdet **$false**, en användardefinierad kodavsnitt visas i den **CTRL + J** lista. Standardvärdet är **$true**.

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a>ShowIntellisenseInConsolePane

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om IntelliSense erbjuder syntax, parametern och värdet förslag i konsolfönstret. Standardvärdet är **$true**.

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a>ShowIntellisenseInScriptPane

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om IntelliSense erbjuder syntax, parametern och värdet förslag i skriptfönstret. Standardvärdet är **$true**.

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a>ShowLineNumbers

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om skriptfönstret visa radnummer i vänster marginal. Standardvärdet är **$true**.

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a>ShowOutlining

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om skriptfönstret visar expanderas och döljas hakparenteserna bredvid kodavsnitt i vänster marginal. När de visas, kan du klicka på minustecknet \( - \) ikoner bredvid ett block med text för att minimera den eller klicka på plustecknet \( + \) ikonen för att expandera ett block med text. Standardvärdet är **$true**.

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a>ShowToolBar

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger om verktygsfältet ISE visas överst i fönstret Windows PowerShell ISE. Standardvärdet är **$true**.

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a>ShowWarningBeforeSavingOnRun

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger om ett varningsmeddelande visas när ett skript sparas automatiskt innan den körs. Standardvärdet är **$true**.

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a>ShowWarningForDuplicateFiles

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger om ett varningsmeddelande visas när samma fil öppnas på olika flikar i PowerShell. Om inställd **$true**, för att öppna samma fil i flera flikar visar det här meddelandet: ”En kopia av den här filen är öppen i ett annat Windows PowerShell-flik. Ändringar som gjorts i den här filen påverkar alla öppna kopior ”. Standardvärdet är **$true**.

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a>TokenColors

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger färgerna för token som IntelliSense i fönstret Windows PowerShell ISE-skript. Den här egenskapen är en Ordlisteobjekt som innehåller namn/värde-par av tokentyper och färger för skriptfönstret. Om du vill ändra färger i token som IntelliSense i konsolfönstret, se [ConsoleTokenColors](#consoletokencolors). Om du vill återställa färgerna standardvärdena, se [RestoreDefaultTokenColors](#restoredefaulttokencolors). Token färger kan anges för följande: Attribut, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, tal, Operator, Position, StatementSeparator, sträng, typ, Okänd, variabel.

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a>UseEnterToSelectInConsolePaneIntellisense

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om du kan använda RETUR-tangenten för att välja en IntelliSense tillhandahålls alternativet i konsolfönstret. Standardvärdet är **$true**.

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a>UseEnterToSelectInScriptPaneIntellisense

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om du kan använda RETUR-tangenten för att välja ett alternativ för angivna IntelliSense i skriptfönstret. Standardvärdet är **$true**.

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a>UseLocalHelp

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger om den lokalt installerade hjälpen eller i TechNet-biblioteket onlinehjälp visas när du trycker på F1 med markören placeras i ett nyckelord. Om inställd **$true**, och sedan ett popup-fönster visar innehåll från den lokalt installerade hjälpen. Du kan installera hjälpfilerna genom att köra den `Update-Help` kommando. Om inställd **$false**, och sedan webbläsaren öppnas på en sida i TechNet-biblioteket.

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a>VerboseBackgroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger bakgrundsfärgen för utförlig text som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a>VerboseForegroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger förgrundsfärgen för utförlig text som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a>WarningBackgroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger bakgrundsfärgen för varningstext som visas i konsolfönstret. Det är en **System.Windows.Media.Color** objekt.

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a>WarningForegroundColor

Stöds i Windows PowerShell ISE 2.0 och senare.

Anger förgrundsfärgen för varningstext som visas i utdatarutan. Det är en **System.Windows.Media.Color** objekt.

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a>XmlTokenColors

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger en Ordlisteobjekt som innehåller namn/värde-par av tokentyper och färger för XML-innehåll som visas i Windows PowerShell ISE. Token färger kan anges för följande: Attribut, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, tal, Operator, Position, StatementSeparator, sträng, typ, Okänd, variabel. Se även [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a>Zooma

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Anger den relativa storleken på texten i både konsolen och skript. Standardvärdet är 100. Lägre värden orsaka texten i Windows PowerShell ISE visas mindre när fler skalningsinstanser orsaka text ska visas större. Värdet är ett heltal mellan 20 och 400.

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a>Se även

- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)