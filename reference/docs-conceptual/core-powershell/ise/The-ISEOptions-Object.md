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
# <a name="the-iseoptions-object"></a><span data-ttu-id="863f7-103">Objektet ISEOptions</span><span class="sxs-lookup"><span data-stu-id="863f7-103">The ISEOptions Object</span></span>
  <span data-ttu-id="863f7-104">Den **ISEOptions** -objektet representerar olika inställningar för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="863f7-105">Det är en instans av den **Microsoft.PowerShell.Host.ISE.ISEOptions** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

 <span data-ttu-id="863f7-106">Den **ISEOptions** objektet innehåller följande metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="863f7-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="863f7-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="863f7-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="863f7-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="863f7-108">RestoreDefaultConsoleTokenColors\(\)</span></span>
  <span data-ttu-id="863f7-109">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-110">Återställer standardvärdena för token färgerna i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-110">Restores the default values of the token colors in the Console pane.</span></span>

```
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = "red"
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="863f7-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="863f7-111">RestoreDefaults\(\)</span></span>
  <span data-ttu-id="863f7-112">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-113">Återställer standardvärdena för alla inställningarna i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="863f7-114">Också återställs beteendet för olika varningsmeddelanden som tillhandahåller standard kryssrutan för att förhindra att meddelandet visas igen.</span><span class="sxs-lookup"><span data-stu-id="863f7-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = "orange"
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="863f7-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="863f7-115">RestoreDefaultTokenColors\(\)</span></span>
  <span data-ttu-id="863f7-116">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-117">Återställer standardvärdena för token färgerna i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-117">Restores the default values of the token colors in the Script pane.</span></span>

```
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="863f7-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="863f7-118">RestoreDefaultXmlTokenColors\(\)</span></span>
  <span data-ttu-id="863f7-119">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-120">Återställer standardvärdena för token färger för XML-element som visas i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="863f7-121">Se även [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"]="red"
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="863f7-122">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="863f7-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="863f7-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="863f7-123">AutoSaveMinuteInterval</span></span>
  <span data-ttu-id="863f7-124">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-125">Anger antalet minuter mellan automatisk spara operations av dina filer med Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="863f7-126">Standardvärdet är 2 minuter.</span><span class="sxs-lookup"><span data-stu-id="863f7-126">The default value is 2 minutes.</span></span> <span data-ttu-id="863f7-127">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="863f7-127">The value is an integer.</span></span>

```
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="863f7-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-128">CommandPaneBackgroundColor</span></span>
  <span data-ttu-id="863f7-129">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="863f7-130">Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="863f7-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="863f7-131">Anger bakgrundsfärgen för kommando-fönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="863f7-132">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = "orange"
```

### <a name="commandpaneup"></a><span data-ttu-id="863f7-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="863f7-133">CommandPaneUp</span></span>
  <span data-ttu-id="863f7-134">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

 <span data-ttu-id="863f7-135">Anger om kommandot fönstret befinner sig ovanför utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="863f7-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true

```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="863f7-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-136">ConsolePaneBackgroundColor</span></span>
  <span data-ttu-id="863f7-137">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-138">Anger bakgrundsfärgen för konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="863f7-139">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = "red"
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="863f7-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-140">ConsolePaneForegroundColor</span></span>
  <span data-ttu-id="863f7-141">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-142">Anger förgrundsfärgen för texten i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-142">Specifies the foreground color of the text in the Console pane.</span></span>

```
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = "yellow"

```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="863f7-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-143">ConsolePaneTextBackgroundColor</span></span>
  <span data-ttu-id="863f7-144">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-145">Anger bakgrundsfärgen för texten i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-145">Specifies the background color of the text in the Console pane.</span></span>

```
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = "pink"
```

### <a name="consoletokencolors"></a><span data-ttu-id="863f7-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="863f7-146">ConsoleTokenColors</span></span>
  <span data-ttu-id="863f7-147">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-148">Anger färgen på IntelliSense-token i fönstret Windows PowerShell ISE-konsolen.</span><span class="sxs-lookup"><span data-stu-id="863f7-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="863f7-149">Den här egenskapen är ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="863f7-150">Om du vill ändra färger IntelliSense-token i skriptfönstret [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span> <span data-ttu-id="863f7-151">Om du vill återställa standardvärdena färger, se [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span> <span data-ttu-id="863f7-152">Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel.</span><span class="sxs-lookup"><span data-stu-id="863f7-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = "magenta"

```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="863f7-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-153">DebugBackgroundColor</span></span>
  <span data-ttu-id="863f7-154">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-155">Anger bakgrundsfärgen för debug-texten som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-156">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor ='#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="863f7-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-157">DebugForegroundColor</span></span>
  <span data-ttu-id="863f7-158">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-159">Anger förgrundsfärgen för debug-text som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-160">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor ="yellow"
```

### <a name="defaultoptions"></a><span data-ttu-id="863f7-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="863f7-161">DefaultOptions</span></span>
  <span data-ttu-id="863f7-162">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-163">En uppsättning egenskaper som anger standardvärden som ska användas vid återställning av-metoderna används.</span><span class="sxs-lookup"><span data-stu-id="863f7-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="863f7-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-164">ErrorBackgroundColor</span></span>
  <span data-ttu-id="863f7-165">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-166">Anger bakgrundsfärgen för feltext som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-167">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor="black"
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="863f7-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-168">ErrorForegroundColor</span></span>
  <span data-ttu-id="863f7-169">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-170">Anger förgrundsfärgen för feltext som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-171">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor ="green"
```

### <a name="fontname"></a><span data-ttu-id="863f7-172">Teckensnitt</span><span class="sxs-lookup"><span data-stu-id="863f7-172">FontName</span></span>
  <span data-ttu-id="863f7-173">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-174">Anger teckensnittet för närvarande används i både skriptfönstret och konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```
# Changes the font used in both panes.
$psISE.Options.FontName = "courier new"
```

### <a name="fontsize"></a><span data-ttu-id="863f7-175">Teckenstorlek</span><span class="sxs-lookup"><span data-stu-id="863f7-175">FontSize</span></span>
  <span data-ttu-id="863f7-176">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-177">Anger teckenstorleken som ett heltal.</span><span class="sxs-lookup"><span data-stu-id="863f7-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="863f7-178">Den används i skriptfönstret och fönstret kommandot utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="863f7-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="863f7-179">Det giltiga intervallet för värden är 8 till 32.</span><span class="sxs-lookup"><span data-stu-id="863f7-179">The valid range of values is 8 through 32.</span></span>

```
# Changes the font size in all panes.
$psISE.Options.FontSize = 20

```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="863f7-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="863f7-180">IntellisenseTimeoutInSeconds</span></span>
  <span data-ttu-id="863f7-181">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-182">Anger antalet sekunder som IntelliSense använder att lösa de för närvarande skriven texten.</span><span class="sxs-lookup"><span data-stu-id="863f7-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span> <span data-ttu-id="863f7-183">Efter detta antal sekunder IntelliSense timeout och du kan fortsätta att skriva.</span><span class="sxs-lookup"><span data-stu-id="863f7-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="863f7-184">Standardvärdet är 3 sekunder.</span><span class="sxs-lookup"><span data-stu-id="863f7-184">The default value is 3 seconds.</span></span> <span data-ttu-id="863f7-185">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="863f7-185">The value is an integer.</span></span>

```
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="863f7-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="863f7-186">MruCount</span></span>
  <span data-ttu-id="863f7-187">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-188">Anger antalet nyligen öppnade filer som Windows PowerShell ISE spårar och visar längst ned i den **öppna** menyn.</span><span class="sxs-lookup"><span data-stu-id="863f7-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="863f7-189">Standardvärdet är 10.</span><span class="sxs-lookup"><span data-stu-id="863f7-189">The default value is 10.</span></span> <span data-ttu-id="863f7-190">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="863f7-190">The value is an integer.</span></span>

```
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="863f7-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-191">OutputPaneBackgroundColor</span></span>
  <span data-ttu-id="863f7-192">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="863f7-193">Senare versioner finns [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="863f7-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

 <span data-ttu-id="863f7-194">Egenskapen för läsning och skrivning som hämtar eller anger bakgrundsfärgen för fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="863f7-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="863f7-195">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = "gold"

```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="863f7-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-196">OutputPaneTextForegroundColor</span></span>
  <span data-ttu-id="863f7-197">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="863f7-198">Senare versioner finns [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="863f7-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

 <span data-ttu-id="863f7-199">Egenskapen för läsning och skrivning som ändrar förgrundsfärgen för texten i fönstret utdata i Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="863f7-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = "blue"

```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="863f7-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-200">OutputPaneTextBackgroundColor</span></span>
  <span data-ttu-id="863f7-201">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="863f7-202">Senare versioner finns [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="863f7-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

 <span data-ttu-id="863f7-203">Egenskapen för läsning och skrivning som ändrar bakgrundsfärgen för texten i utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="863f7-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = "pink"
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="863f7-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-204">ScriptPaneBackgroundColor</span></span>
  <span data-ttu-id="863f7-205">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-206">Egenskapen för läsning och skrivning som hämtar eller anger bakgrundsfärgen för filer.</span><span class="sxs-lookup"><span data-stu-id="863f7-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="863f7-207">Det är en instans av den **System.Windows.Media.Color** klass.</span><span class="sxs-lookup"><span data-stu-id="863f7-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```

# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'

```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="863f7-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-208">ScriptPaneForegroundColor</span></span>
  <span data-ttu-id="863f7-209">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-210">Egenskapen för läsning och skrivning som hämtar eller anger förgrundsfärgen för icke-skriptfiler i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="863f7-211">Förgrundsfärgen för skriptfiler, använder den [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = "green"

```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="863f7-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="863f7-212">SelectedScriptPaneState</span></span>
  <span data-ttu-id="863f7-213">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-214">Egenskapen för läsning och skrivning som hämtar eller anger placeringen av skriptfönstret på skärmen.</span><span class="sxs-lookup"><span data-stu-id="863f7-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="863f7-215">Strängen kan vara antingen ”maximerat”, ”Top” eller ”höger”.</span><span class="sxs-lookup"><span data-stu-id="863f7-215">The string can be either "Maximized", "Top", or "Right".</span></span>

```
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = "Top"
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = "Right"
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = "Maximized"

```

### <a name="showdefaultsnippets"></a><span data-ttu-id="863f7-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="863f7-216">ShowDefaultSnippets</span></span>
  <span data-ttu-id="863f7-217">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-218">Anger om den **CTRL + J** lista med kodavsnitt inkluderar starter som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="863f7-218">Specifies whether the **CTRL+J** list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="863f7-219">Om värdet är **$false**, användardefinierade kodavsnitt som visas i den **CTRL + J** lista.</span><span class="sxs-lookup"><span data-stu-id="863f7-219">When set to **$false**, only user-defined snippets appear in the **CTRL+J** list.</span></span> <span data-ttu-id="863f7-220">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-220">The default value is **$true**.</span></span>

```
# Hide the default snippets from the CTRL+J list.
$psISe.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="863f7-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="863f7-221">ShowIntellisenseInConsolePane</span></span>
  <span data-ttu-id="863f7-222">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-223">Anger om IntelliSense erbjuder syntax och parametern förslag för värde i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span> <span data-ttu-id="863f7-224">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-224">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the console pane.
$psISe.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="863f7-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="863f7-225">ShowIntellisenseInScriptPane</span></span>
  <span data-ttu-id="863f7-226">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-227">Anger om IntelliSense erbjuder syntax och parametern förslag för värde i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span> <span data-ttu-id="863f7-228">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-228">The default value is **$true**.</span></span>

```
# Turn off IntelliSense in the Script pane.
$psISe.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="863f7-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="863f7-229">ShowLineNumbers</span></span>
  <span data-ttu-id="863f7-230">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-231">Anger om skriptfönstret Visar radnummer i vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="863f7-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="863f7-232">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-232">The default value is **$true**.</span></span>

```
# Turn off line numbers in the Script pane.
$psISe.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="863f7-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="863f7-233">ShowOutlining</span></span>
  <span data-ttu-id="863f7-234">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-235">Anger om skriptfönstret visar expanderas och döljas hakparenteser bredvid kodavsnitt i vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="863f7-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="863f7-236">När de visas, du kan klicka på Minuset \( - \) ikoner bredvid ett textblock minimera den eller klicka på plustecknet \( + \) ikon för att expandera ett block med text.</span><span class="sxs-lookup"><span data-stu-id="863f7-236">When they are displayed, you can click the minus \(-\) icons next to a block of text to collapse it or click the plus \(+\) icon to expand a block of text.</span></span> <span data-ttu-id="863f7-237">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-237">The default value is **$true**.</span></span>

```
# Turn off outlining in the Script pane.
$psISe.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="863f7-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="863f7-238">ShowToolBar</span></span>
  <span data-ttu-id="863f7-239">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-240">Anger om verktygsfältet ISE visas överst i fönstret Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="863f7-241">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-241">The default value is **$true**.</span></span>

```
# Show the toolbar.
$psISe.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="863f7-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="863f7-242">ShowWarningBeforeSavingOnRun</span></span>
  <span data-ttu-id="863f7-243">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-244">Anger om ett varningsmeddelande visas när ett skript sparas automatiskt innan den körs.</span><span class="sxs-lookup"><span data-stu-id="863f7-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span> <span data-ttu-id="863f7-245">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-245">The default value is **$true**.</span></span>

```
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun=$true

```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="863f7-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="863f7-246">ShowWarningForDuplicateFiles</span></span>
  <span data-ttu-id="863f7-247">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-248">Anger om ett varningsmeddelande visas när samma fil öppnas i olika PowerShell flikar.</span><span class="sxs-lookup"><span data-stu-id="863f7-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="863f7-249">Om värdet **$true**, för att öppna samma fil i flera flikar visas det här meddelandet: ”en kopia av den här filen är öppen i en annan flik i Windows PowerShell. Ändringar som gjorts i den här filen tas bort påverkas alla öppna kopior ”.</span><span class="sxs-lookup"><span data-stu-id="863f7-249">If set to **$true**, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="863f7-250">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-250">The default value is **$true**.</span></span>

```
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true

```

### <a name="tokencolors"></a><span data-ttu-id="863f7-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="863f7-251">TokenColors</span></span>
  <span data-ttu-id="863f7-252">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-253">Anger färgen på IntelliSense-token i fönstret Windows PowerShell ISE-skript.</span><span class="sxs-lookup"><span data-stu-id="863f7-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="863f7-254">Den här egenskapen är ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="863f7-255">Om du vill ändra färger IntelliSense-token i konsolfönstret [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span> <span data-ttu-id="863f7-256">Om du vill återställa standardvärdena färger, se [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span> <span data-ttu-id="863f7-257">Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel.</span><span class="sxs-lookup"><span data-stu-id="863f7-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"

```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="863f7-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="863f7-258">UseEnterToSelectInConsolePaneIntellisense</span></span>
  <span data-ttu-id="863f7-259">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-260">Anger om du använder RETUR-tangenten för att välja en IntelliSense tillhandahålls alternativet i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="863f7-261">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-261">The default value is **$true**.</span></span>

```
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$false

```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="863f7-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="863f7-262">UseEnterToSelectInScriptPaneIntellisense</span></span>
  <span data-ttu-id="863f7-263">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-264">Anger om du kan använda RETUR-tangenten för att välja ett alternativ för angivna IntelliSense i skriptfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="863f7-265">Standardvärdet är **$true**.</span><span class="sxs-lookup"><span data-stu-id="863f7-265">The default value is **$true**.</span></span>

```
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense=$true

```

### <a name="uselocalhelp"></a><span data-ttu-id="863f7-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="863f7-266">UseLocalHelp</span></span>
  <span data-ttu-id="863f7-267">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-268">Anger om lokalt installerade hjälp eller den TechNet Library onlinehjälp visas när du trycker på F1 med markören placeras i ett nyckelord.</span><span class="sxs-lookup"><span data-stu-id="863f7-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press F1 with the cursor positioned in a keyword.</span></span> <span data-ttu-id="863f7-269">Om värdet **$true**, och sedan ett popup-fönster visar innehåll från lokalt installerade hjälp.</span><span class="sxs-lookup"><span data-stu-id="863f7-269">If set to **$true**, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="863f7-270">Du kan installera hjälpfiler genom att köra den `Update-Help` kommando.</span><span class="sxs-lookup"><span data-stu-id="863f7-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="863f7-271">Om värdet **$false**, webbläsaren öppnas på en sida i TechNet-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="863f7-271">If set to **$false**, then your browser opens to a page in the TechNet Library.</span></span>

```
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp=$false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp=$true

```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="863f7-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-272">VerboseBackgroundColor</span></span>
  <span data-ttu-id="863f7-273">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-274">Anger bakgrundsfärgen för utförlig text som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-275">Det är en **System.Windows.Media.Color** objekt.</span><span class="sxs-lookup"><span data-stu-id="863f7-275">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="863f7-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-276">VerboseForegroundColor</span></span>
  <span data-ttu-id="863f7-277">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-278">Anger förgrundsfärgen för utförlig text som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-279">Det är en **System.Windows.Media.Color** objekt.</span><span class="sxs-lookup"><span data-stu-id="863f7-279">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor ='yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="863f7-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-280">WarningBackgroundColor</span></span>
  <span data-ttu-id="863f7-281">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-282">Anger bakgrundsfärgen för varningstext som visas i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="863f7-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="863f7-283">Det är en **System.Windows.Media.Color** objekt.</span><span class="sxs-lookup"><span data-stu-id="863f7-283">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor ='#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="863f7-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="863f7-284">WarningForegroundColor</span></span>
  <span data-ttu-id="863f7-285">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="863f7-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="863f7-286">Anger förgrundsfärgen för varningstext som visas i utdatarutan.</span><span class="sxs-lookup"><span data-stu-id="863f7-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="863f7-287">Det är en **System.Windows.Media.Color** objekt.</span><span class="sxs-lookup"><span data-stu-id="863f7-287">It is a **System.Windows.Media.Color** object.</span></span>

```
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor ='yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="863f7-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="863f7-288">XmlTokenColors</span></span>
  <span data-ttu-id="863f7-289">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-290">Anger ett katalogobjekt som innehåller namn/värde-par av tokentyper och färger för XML-innehåll som visas i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="863f7-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="863f7-291">Token färger kan anges för följande: attributet, kommandot, CommandArgument, CommandParameter, kommentar, GroupEnd, GroupStart, nyckelord, LineContinuation, LoopLabel, medlem, ny rad, antalet, Operator, Position, StatementSeparator, sträng, typ, Okänd variabel.</span><span class="sxs-lookup"><span data-stu-id="863f7-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="863f7-292">Se även [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="863f7-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = "green"
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = "magenta"

```

### <a name="zoom"></a><span data-ttu-id="863f7-293">Zooma</span><span class="sxs-lookup"><span data-stu-id="863f7-293">Zoom</span></span>
  <span data-ttu-id="863f7-294">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="863f7-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

 <span data-ttu-id="863f7-295">Anger den relativa storleken på texten i både konsolen och skript.</span><span class="sxs-lookup"><span data-stu-id="863f7-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="863f7-296">Standardvärdet är 100.</span><span class="sxs-lookup"><span data-stu-id="863f7-296">The default value is 100.</span></span> <span data-ttu-id="863f7-297">Lägre värden orsaka texten i Windows PowerShell ISE ska vara mindre medan större tal orsakar text ska visas större.</span><span class="sxs-lookup"><span data-stu-id="863f7-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="863f7-298">Värdet är ett heltal som sträcker sig från 20 till 400.</span><span class="sxs-lookup"><span data-stu-id="863f7-298">The value is an integer that ranges from 20 to 400.</span></span>

```
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="863f7-299">Se även</span><span class="sxs-lookup"><span data-stu-id="863f7-299">See Also</span></span>
- [<span data-ttu-id="863f7-300">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="863f7-300">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="863f7-301">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="863f7-301">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)

