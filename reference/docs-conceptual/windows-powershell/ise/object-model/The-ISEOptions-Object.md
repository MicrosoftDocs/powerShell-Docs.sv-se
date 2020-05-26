---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEOptions-objektet
ms.openlocfilehash: 9caa78a70cb837c755b2eff9af6ce0aa5dbb7452
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810101"
---
# <a name="the-iseoptions-object"></a><span data-ttu-id="71503-103">ISEOptions-objektet</span><span class="sxs-lookup"><span data-stu-id="71503-103">The ISEOptions Object</span></span>

<span data-ttu-id="71503-104">Objektet **ISEOptions** representerar olika inställningar för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-104">The **ISEOptions** object represents various settings for Windows PowerShell ISE.</span></span> <span data-ttu-id="71503-105">Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEOptions** .</span><span class="sxs-lookup"><span data-stu-id="71503-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEOptions** class.</span></span>

<span data-ttu-id="71503-106">**ISEOptions** -objektet tillhandahåller följande metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="71503-106">The **ISEOptions** object provides the following methods and properties.</span></span>

## <a name="methods"></a><span data-ttu-id="71503-107">Metoder</span><span class="sxs-lookup"><span data-stu-id="71503-107">Methods</span></span>

### <a name="restoredefaultconsoletokencolors"></a><span data-ttu-id="71503-108">RestoreDefaultConsoleTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="71503-108">RestoreDefaultConsoleTokenColors\(\)</span></span>

<span data-ttu-id="71503-109">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-110">Återställer standardvärdena för token-färgerna i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-110">Restores the default values of the token colors in the Console pane.</span></span>

```powershell
# Changes the color of the commands in the Console pane to red and then restores it to its default value.
$psISE.Options.ConsoleTokenColors["Command"] = 'red'
$psISE.Options.RestoreDefaultConsoleTokenColors()
```

### <a name="restoredefaults"></a><span data-ttu-id="71503-111">RestoreDefaults\(\)</span><span class="sxs-lookup"><span data-stu-id="71503-111">RestoreDefaults\(\)</span></span>

<span data-ttu-id="71503-112">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-112">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-113">Återställer standardvärdena för alla alternativ inställningar i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-113">Restores the default values of all options settings in the Console pane.</span></span> <span data-ttu-id="71503-114">Den återställer också beteendet för olika varnings meddelanden som innehåller kryss rutan standard för att förhindra att meddelandet visas igen.</span><span class="sxs-lookup"><span data-stu-id="71503-114">It also resets the behavior of various warning messages that provide the standard check box to prevent the message from being shown again.</span></span>

```powershell
# Changes the background color in the Console pane and then restores it to its default value.
$psISE.Options.ConsolePaneBackgroundColor = 'orange'
$psISE.Options.RestoreDefaults()
```

### <a name="restoredefaulttokencolors"></a><span data-ttu-id="71503-115">RestoreDefaultTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="71503-115">RestoreDefaultTokenColors\(\)</span></span>

<span data-ttu-id="71503-116">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-117">Återställer standardvärdena för token-färgerna i skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-117">Restores the default values of the token colors in the Script pane.</span></span>

```powershell
# Changes the color of the comments in the Script pane to red and then restores it to its default value.
$psISE.Options.TokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultTokenColors()
```

### <a name="restoredefaultxmltokencolors"></a><span data-ttu-id="71503-118">RestoreDefaultXmlTokenColors\(\)</span><span class="sxs-lookup"><span data-stu-id="71503-118">RestoreDefaultXmlTokenColors\(\)</span></span>

<span data-ttu-id="71503-119">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-119">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-120">Återställer standardvärdena för token-färgerna för XML-element som visas i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-120">Restores the default values of the token colors for XML elements that are displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="71503-121">Se även [XmlTokenColors](#xmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-121">Also see [XmlTokenColors](#xmltokencolors).</span></span>

```powershell
# Changes the color of the comments in XML data to red and then restores it to its default value.
$psISE.Options.XmlTokenColors["Comment"] = 'red'
$psISE.Options.RestoreDefaultXmlTokenColors()
```

## <a name="properties"></a><span data-ttu-id="71503-122">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="71503-122">Properties</span></span>

### <a name="autosaveminuteinterval"></a><span data-ttu-id="71503-123">AutoSaveMinuteInterval</span><span class="sxs-lookup"><span data-stu-id="71503-123">AutoSaveMinuteInterval</span></span>

<span data-ttu-id="71503-124">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-125">Anger antalet minuter mellan automatiska sparade åtgärder för dina filer med Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-125">Specifies the number of minutes between automatic save operations of your files by Windows PowerShell ISE.</span></span> <span data-ttu-id="71503-126">Standardvärdet är 2 minuter.</span><span class="sxs-lookup"><span data-stu-id="71503-126">The default value is 2 minutes.</span></span> <span data-ttu-id="71503-127">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="71503-127">The value is an integer.</span></span>

```powershell
# Changes the number of minutes between automatic save operations to every 3 minutes.
$psISE.Options.AutoSaveMinuteInterval = 3
```

### <a name="commandpanebackgroundcolor"></a><span data-ttu-id="71503-128">CommandPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-128">CommandPaneBackgroundColor</span></span>

<span data-ttu-id="71503-129">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-129">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="71503-130">För senare versioner, se [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="71503-130">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="71503-131">Anger bakgrunds färgen för kommando fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-131">Specifies the background color for the Command pane.</span></span> <span data-ttu-id="71503-132">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-132">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Command pane to orange.
$psISE.Options.CommandPaneBackgroundColor = 'orange'
```

### <a name="commandpaneup"></a><span data-ttu-id="71503-133">CommandPaneUp</span><span class="sxs-lookup"><span data-stu-id="71503-133">CommandPaneUp</span></span>

<span data-ttu-id="71503-134">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-134">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>

<span data-ttu-id="71503-135">Anger om kommando fönstret finns ovanför fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="71503-135">Specifies whether the Command pane is located above the Output pane.</span></span>

```powershell
# Moves the Command pane to the top of the screen.
$psISE.Options.CommandPaneUp  = $true
```

### <a name="consolepanebackgroundcolor"></a><span data-ttu-id="71503-136">ConsolePaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-136">ConsolePaneBackgroundColor</span></span>

<span data-ttu-id="71503-137">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-137">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-138">Anger bakgrunds färgen för konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-138">Specifies the background color for the Console pane.</span></span> <span data-ttu-id="71503-139">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-139">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Console pane to red.
$psISE.Options.ConsolePaneBackgroundColor = 'red'
```

### <a name="consolepaneforegroundcolor"></a><span data-ttu-id="71503-140">ConsolePaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-140">ConsolePaneForegroundColor</span></span>

<span data-ttu-id="71503-141">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-141">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-142">Anger förgrunds färgen för texten i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-142">Specifies the foreground color of the text in the Console pane.</span></span>

```powershell
# Changes the foreground color of the text in the Console pane to yellow.
$psISE.Options.ConsolePaneForegroundColor  = 'yellow'
```

### <a name="consolepanetextbackgroundcolor"></a><span data-ttu-id="71503-143">ConsolePaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-143">ConsolePaneTextBackgroundColor</span></span>

<span data-ttu-id="71503-144">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-144">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-145">Anger bakgrunds färgen för texten i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-145">Specifies the background color of the text in the Console pane.</span></span>

```powershell
# Changes the background color of the Console pane text to pink.
$psISE.Options.ConsolePaneTextBackgroundColor = 'pink'
```

### <a name="consoletokencolors"></a><span data-ttu-id="71503-146">ConsoleTokenColors</span><span class="sxs-lookup"><span data-stu-id="71503-146">ConsoleTokenColors</span></span>

<span data-ttu-id="71503-147">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-147">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-148">Anger färgerna i IntelliSense-tokens i Windows PowerShell ISE konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-148">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Console pane.</span></span> <span data-ttu-id="71503-149">Den här egenskapen är ett Dictionary-objekt som innehåller namn/värde-par av tokens och färger för konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-149">This property is a dictionary object that contains name/value pairs of token types and colors for the Console pane.</span></span> <span data-ttu-id="71503-150">Om du vill ändra färgerna i IntelliSense-tokens i skript fönstret, se [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-150">To change the colors of the IntelliSense tokens in the Script pane, see [TokenColors](#tokencolors).</span></span>
<span data-ttu-id="71503-151">Information om hur du återställer färgerna till standardvärdena finns i [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-151">To reset the colors to the default values, see [RestoreDefaultConsoleTokenColors](#restoredefaultconsoletokencolors).</span></span>
<span data-ttu-id="71503-152">Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, okänd, variabel.</span><span class="sxs-lookup"><span data-stu-id="71503-152">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.ConsoleTokenColors["Command"] = 'green'
# Sets the color of keywords to magenta.
$psISE.Options.ConsoleTokenColors["Keyword"] = 'magenta'
```

### <a name="debugbackgroundcolor"></a><span data-ttu-id="71503-153">DebugBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-153">DebugBackgroundColor</span></span>

<span data-ttu-id="71503-154">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-154">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-155">Anger bakgrunds färgen för fel söknings texten som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-155">Specifies the background color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="71503-156">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-156">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the debug text that appears in the Console pane to blue.
$psISE.Options.DebugBackgroundColor = '#0000FF'
```

### <a name="debugforegroundcolor"></a><span data-ttu-id="71503-157">DebugForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-157">DebugForegroundColor</span></span>

<span data-ttu-id="71503-158">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-158">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-159">Anger förgrunds färgen för fel söknings texten som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-159">Specifies the foreground color for the debug text that appears in the Console pane.</span></span> <span data-ttu-id="71503-160">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-160">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the debug text that appears in the Console pane to yellow.
$psISE.Options.DebugForegroundColor = 'yellow'
```

### <a name="defaultoptions"></a><span data-ttu-id="71503-161">DefaultOptions</span><span class="sxs-lookup"><span data-stu-id="71503-161">DefaultOptions</span></span>

<span data-ttu-id="71503-162">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-162">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-163">En samling egenskaper som anger de standardvärden som ska användas när återställnings metoderna används.</span><span class="sxs-lookup"><span data-stu-id="71503-163">A collection of properties that specify the default values to be used when the Reset methods are used.</span></span>

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

### <a name="errorbackgroundcolor"></a><span data-ttu-id="71503-164">ErrorBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-164">ErrorBackgroundColor</span></span>

<span data-ttu-id="71503-165">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-165">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-166">Anger bakgrunds färgen för fel text som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-166">Specifies the background color for error text that appears in the Console pane.</span></span> <span data-ttu-id="71503-167">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-167">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color for the error text that appears in the Console pane to black.
$psISE.Options.ErrorBackgroundColor = 'black'
```

### <a name="errorforegroundcolor"></a><span data-ttu-id="71503-168">ErrorForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-168">ErrorForegroundColor</span></span>

<span data-ttu-id="71503-169">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-169">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-170">Anger förgrunds färgen för fel text som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-170">Specifies the foreground color for error text that appears in the Console pane.</span></span> <span data-ttu-id="71503-171">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-171">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the foreground color for the error text that appears in the console pane to green.
$psISE.Options.ErrorForegroundColor = 'green'
```

### <a name="fontname"></a><span data-ttu-id="71503-172">FontName</span><span class="sxs-lookup"><span data-stu-id="71503-172">FontName</span></span>

<span data-ttu-id="71503-173">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-173">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-174">Anger teckensnitts namnet som används i både skript fönstret och konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-174">Specifies the font name currently in use in both the Script pane and the Console pane.</span></span>

```powershell
# Changes the font used in both panes.
$psISE.Options.FontName = 'Courier New'
```

### <a name="fontsize"></a><span data-ttu-id="71503-175">FontSize</span><span class="sxs-lookup"><span data-stu-id="71503-175">FontSize</span></span>

<span data-ttu-id="71503-176">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-176">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-177">Anger tecken storleken som ett heltal.</span><span class="sxs-lookup"><span data-stu-id="71503-177">Specifies the font size as an integer.</span></span> <span data-ttu-id="71503-178">Den används i skript fönstret, kommando fönstret och fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="71503-178">It is used in the Script pane, the Command pane, and the Output pane.</span></span> <span data-ttu-id="71503-179">Det giltiga värde intervallet är 8 till 32.</span><span class="sxs-lookup"><span data-stu-id="71503-179">The valid range of values is 8 through 32.</span></span>

```powershell
# Changes the font size in all panes.
$psISE.Options.FontSize = 20
```

### <a name="intellisensetimeoutinseconds"></a><span data-ttu-id="71503-180">IntellisenseTimeoutInSeconds</span><span class="sxs-lookup"><span data-stu-id="71503-180">IntellisenseTimeoutInSeconds</span></span>

<span data-ttu-id="71503-181">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-181">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-182">Anger hur många sekunder som IntelliSense använder för att försöka lösa den text som är skriven för tillfället.</span><span class="sxs-lookup"><span data-stu-id="71503-182">Specifies the number of seconds that IntelliSense uses to try to resolve the currently typed text.</span></span>
<span data-ttu-id="71503-183">Efter det här antalet sekunder kan IntelliSense-tiden ta slut och du kan fortsätta att skriva.</span><span class="sxs-lookup"><span data-stu-id="71503-183">After this number of seconds, IntelliSense times out and enables you to continue typing.</span></span> <span data-ttu-id="71503-184">Standardvärdet är 3 sekunder.</span><span class="sxs-lookup"><span data-stu-id="71503-184">The default value is 3 seconds.</span></span> <span data-ttu-id="71503-185">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="71503-185">The value is an integer.</span></span>

```powershell
# Changes the number of seconds for IntelliSense syntax recognition to 5.
$psISE.Options.IntellisenseTimeoutInSeconds = 5
```

### <a name="mrucount"></a><span data-ttu-id="71503-186">MruCount</span><span class="sxs-lookup"><span data-stu-id="71503-186">MruCount</span></span>

<span data-ttu-id="71503-187">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-187">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-188">Anger antalet nyligen öppnade filer som Windows PowerShell ISE spårar och visas längst ned på menyn **Öppna** .</span><span class="sxs-lookup"><span data-stu-id="71503-188">Specifies the number of recently opened files that Windows PowerShell ISE tracks and displays at the bottom of the **File Open** menu.</span></span> <span data-ttu-id="71503-189">Standardvärdet är 10.</span><span class="sxs-lookup"><span data-stu-id="71503-189">The default value is 10.</span></span> <span data-ttu-id="71503-190">Värdet är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="71503-190">The value is an integer.</span></span>

```powershell
# Changes the number of recently used files that appear at the bottom of the File Open menu to 5.
$psISE.Options.MruCount = 5
```

### <a name="outputpanebackgroundcolor"></a><span data-ttu-id="71503-191">OutputPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-191">OutputPaneBackgroundColor</span></span>

<span data-ttu-id="71503-192">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-192">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="71503-193">För senare versioner, se [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="71503-193">For later versions, see [ConsolePaneBackgroundColor](#consolepanebackgroundcolor).</span></span>

<span data-ttu-id="71503-194">Egenskapen Läs/skriv som hämtar eller anger bakgrunds färgen för själva utdatafönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-194">The read/write property that gets or sets the background color for the Output pane itself.</span></span> <span data-ttu-id="71503-195">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-195">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Changes the background color of the Output pane to gold.
$psISE.Options.OutputPaneForegroundColor = 'gold'
```

### <a name="outputpanetextforegroundcolor"></a><span data-ttu-id="71503-196">OutputPaneTextForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-196">OutputPaneTextForegroundColor</span></span>

<span data-ttu-id="71503-197">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-197">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="71503-198">För senare versioner, se [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span><span class="sxs-lookup"><span data-stu-id="71503-198">For later versions, see [ConsolePaneForegroundColor](#consolepaneforegroundcolor).</span></span>

<span data-ttu-id="71503-199">Egenskapen Läs/skriv som ändrar förgrunds färgen för texten i fönstret utdata i Windows PowerShell ISE 2,0.</span><span class="sxs-lookup"><span data-stu-id="71503-199">The read/write property that changes the foreground color of the text in the Output pane in Windows PowerShell ISE 2.0.</span></span>

```powershell
# Changes the foreground color of the text in the Output Pane to blue.
$psISE.Options.OutputPaneTextForegroundColor  = 'blue'
```

### <a name="outputpanetextbackgroundcolor"></a><span data-ttu-id="71503-200">OutputPaneTextBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-200">OutputPaneTextBackgroundColor</span></span>

<span data-ttu-id="71503-201">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-201">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="71503-202">För senare versioner, se [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span><span class="sxs-lookup"><span data-stu-id="71503-202">For later versions, see [ConsolePaneTextBackgroundColor](#consolepanetextbackgroundcolor).</span></span>

<span data-ttu-id="71503-203">Egenskapen Läs/skriv som ändrar bakgrunds färgen för texten i fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="71503-203">The read/write property that changes the background color of the text in the Output pane.</span></span>

```powershell
# Changes the background color of the Output pane text to pink.
$psISE.Options.OutputPaneTextBackgroundColor = 'pink'
```

### <a name="scriptpanebackgroundcolor"></a><span data-ttu-id="71503-204">ScriptPaneBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-204">ScriptPaneBackgroundColor</span></span>

<span data-ttu-id="71503-205">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-205">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-206">Egenskapen Läs/skriv som hämtar eller anger bakgrunds färgen för filer.</span><span class="sxs-lookup"><span data-stu-id="71503-206">The read/write property that gets or sets the background color for files.</span></span> <span data-ttu-id="71503-207">Det är en instans av klassen **system. Windows. Media. Color** .</span><span class="sxs-lookup"><span data-stu-id="71503-207">It is an instance of the **System.Windows.Media.Color** class.</span></span>

```powershell
# Sets the color of the script pane background to yellow.
$psISE.Options.ScriptPaneBackgroundColor = 'yellow'
```

### <a name="scriptpaneforegroundcolor"></a><span data-ttu-id="71503-208">ScriptPaneForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-208">ScriptPaneForegroundColor</span></span>

<span data-ttu-id="71503-209">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-209">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-210">Egenskapen Läs/skriv som hämtar eller anger förgrunds färgen för filer som inte är skriptfiler i skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-210">The read/write property that gets or sets the foreground color for non-script files in the Script pane.</span></span>
<span data-ttu-id="71503-211">Om du vill ange förgrunds färgen för skriptfiler använder du [TokenColors](#tokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-211">To set the foreground color for script files, use the [TokenColors](#tokencolors).</span></span>

```powershell
# Sets the foreground to color of non-script files in the script pane to green.
$psISE.Options.ScriptPaneBackgroundColor = 'green'
```

### <a name="selectedscriptpanestate"></a><span data-ttu-id="71503-212">SelectedScriptPaneState</span><span class="sxs-lookup"><span data-stu-id="71503-212">SelectedScriptPaneState</span></span>

<span data-ttu-id="71503-213">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-213">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-214">Egenskapen Läs/skriv som hämtar eller anger positionen för skript fönstret på skärmen.</span><span class="sxs-lookup"><span data-stu-id="71503-214">The read/write property that gets or sets the position of the Script pane on the display.</span></span> <span data-ttu-id="71503-215">Strängen kan vara antingen "maximerad", "Top" eller "Right".</span><span class="sxs-lookup"><span data-stu-id="71503-215">The string can be either 'Maximized', 'Top', or 'Right'.</span></span>

```powershell
# Moves the Script Pane to the top.
$psISE.Options.SelectedScriptPaneState = 'Top'
# Moves the Script Pane to the right.
$psISE.Options.SelectedScriptPaneState = 'Right'
# Maximizes the Script Pane
$psISE.Options.SelectedScriptPaneState = 'Maximized'
```

### <a name="showdefaultsnippets"></a><span data-ttu-id="71503-216">ShowDefaultSnippets</span><span class="sxs-lookup"><span data-stu-id="71503-216">ShowDefaultSnippets</span></span>

<span data-ttu-id="71503-217">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-217">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-218">Anger om <kbd>CTRL</kbd> + <kbd>J</kbd> -listan över kodfragment innehåller den Start uppsättning som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="71503-218">Specifies whether the <kbd>CTRL</kbd>+<kbd>J</kbd> list of snippets includes the starter set that is included in Windows PowerShell.</span></span> <span data-ttu-id="71503-219">När det är inställt på `$false` visas bara användardefinierade kodfragment i <kbd>CTRL</kbd> + <kbd>J</kbd> -listan.</span><span class="sxs-lookup"><span data-stu-id="71503-219">When set to `$false`, only user-defined snippets appear in the <kbd>CTRL</kbd>+<kbd>J</kbd> list.</span></span>
<span data-ttu-id="71503-220">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-220">The default value is `$true`.</span></span>

```powershell
# Hide the default snippets from the CTRL+J list.
$psISE.Options.ShowDefaultSnippets = $false
```

### <a name="showintellisenseinconsolepane"></a><span data-ttu-id="71503-221">ShowIntellisenseInConsolePane</span><span class="sxs-lookup"><span data-stu-id="71503-221">ShowIntellisenseInConsolePane</span></span>

<span data-ttu-id="71503-222">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-222">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-223">Anger om IntelliSense erbjuder syntax, parameter och värde förslag i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-223">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Console pane.</span></span>
<span data-ttu-id="71503-224">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-224">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the console pane.
$psISE.Options.ShowIntellisenseInConsolePane = $false
```

### <a name="showintellisenseinscriptpane"></a><span data-ttu-id="71503-225">ShowIntellisenseInScriptPane</span><span class="sxs-lookup"><span data-stu-id="71503-225">ShowIntellisenseInScriptPane</span></span>

<span data-ttu-id="71503-226">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-226">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-227">Anger om IntelliSense erbjuder syntax, parameter och värde förslag i fönstret skript.</span><span class="sxs-lookup"><span data-stu-id="71503-227">Specifies whether IntelliSense offers syntax, parameter, and value suggestions in the Script pane.</span></span>
<span data-ttu-id="71503-228">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-228">The default value is `$true`.</span></span>

```powershell
# Turn off IntelliSense in the Script pane.
$psISE.Options.ShowIntellisenseInScriptPane = $false
```

### <a name="showlinenumbers"></a><span data-ttu-id="71503-229">ShowLineNumbers</span><span class="sxs-lookup"><span data-stu-id="71503-229">ShowLineNumbers</span></span>

<span data-ttu-id="71503-230">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-230">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-231">Anger om fönstret skript visar rad nummer i vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="71503-231">Specifies whether the Script pane displays line numbers in the left margin.</span></span> <span data-ttu-id="71503-232">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-232">The default value is `$true`.</span></span>

```powershell
# Turn off line numbers in the Script pane.
$psISE.Options.ShowLineNumbers = $false
```

### <a name="showoutlining"></a><span data-ttu-id="71503-233">ShowOutlining</span><span class="sxs-lookup"><span data-stu-id="71503-233">ShowOutlining</span></span>

<span data-ttu-id="71503-234">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-234">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-235">Anger om skript fönstret visar expanderbara och komprimerbara hakparenteser bredvid avsnitt i kod i vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="71503-235">Specifies whether the Script pane displays expandable and collapsible brackets next to sections of code in the left margin.</span></span> <span data-ttu-id="71503-236">När de visas kan du klicka på minus `-` ikonerna bredvid ett textblock för att komprimera det eller klicka på plus `+` ikonen för att expandera ett textblock.</span><span class="sxs-lookup"><span data-stu-id="71503-236">When they are displayed, you can click the minus `-` icons next to a block of text to collapse it or click the plus `+` icon to expand a block of text.</span></span> <span data-ttu-id="71503-237">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-237">The default value is `$true`.</span></span>

```powershell
# Turn off outlining in the Script pane.
$psISE.Options.ShowOutlining = $false
```

### <a name="showtoolbar"></a><span data-ttu-id="71503-238">ShowToolBar</span><span class="sxs-lookup"><span data-stu-id="71503-238">ShowToolBar</span></span>

<span data-ttu-id="71503-239">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-239">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-240">Anger om ISE-verktygsfältet visas överst i Windows PowerShell ISEs fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-240">Specifies whether the ISE toolbar appears at the top of the Windows PowerShell ISE window.</span></span> <span data-ttu-id="71503-241">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-241">The default value is `$true`.</span></span>

```powershell
# Show the toolbar.
$psISE.Options.ShowToolBar = $true
```

### <a name="showwarningbeforesavingonrun"></a><span data-ttu-id="71503-242">ShowWarningBeforeSavingOnRun</span><span class="sxs-lookup"><span data-stu-id="71503-242">ShowWarningBeforeSavingOnRun</span></span>

<span data-ttu-id="71503-243">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-243">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-244">Anger om ett varnings meddelande visas när ett skript sparas automatiskt innan det körs.</span><span class="sxs-lookup"><span data-stu-id="71503-244">Specifies whether a warning message appears when a script is saved automatically before it is run.</span></span>
<span data-ttu-id="71503-245">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-245">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when an attempt
# is made to run a script without saving it first.
$psISE.Options.ShowWarningBeforeSavingOnRun = $true
```

### <a name="showwarningforduplicatefiles"></a><span data-ttu-id="71503-246">ShowWarningForDuplicateFiles</span><span class="sxs-lookup"><span data-stu-id="71503-246">ShowWarningForDuplicateFiles</span></span>

<span data-ttu-id="71503-247">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-247">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-248">Anger om ett varnings meddelande visas när samma fil öppnas i olika PowerShell-flikar.</span><span class="sxs-lookup"><span data-stu-id="71503-248">Specifies whether a warning message appears when the same file is opened in different PowerShell tabs.</span></span> <span data-ttu-id="71503-249">Om det är inställt på `$true` , för att öppna samma fil på flera flikar visas följande meddelande: "en kopia av filen är öppen på en annan Windows PowerShell-flik. ändringar i den här filen kommer att påverka alla öppna kopior."</span><span class="sxs-lookup"><span data-stu-id="71503-249">If set to `$true`, to open the same file in multiple tabs displays this message: "A copy of this file is open in another Windows PowerShell tab. Changes made to this file will affect all open copies."</span></span> <span data-ttu-id="71503-250">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-250">The default value is `$true`.</span></span>

```powershell
# Enable the warning message when a file is
# opened in multiple PowerShell tabs.
$psISE.Options.ShowWarningForDuplicateFiles = $true
```

### <a name="tokencolors"></a><span data-ttu-id="71503-251">TokenColors</span><span class="sxs-lookup"><span data-stu-id="71503-251">TokenColors</span></span>

<span data-ttu-id="71503-252">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-252">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-253">Anger färgerna i IntelliSense-tokens i rutan Windows PowerShell ISE skript.</span><span class="sxs-lookup"><span data-stu-id="71503-253">Specifies the colors of the IntelliSense tokens in the Windows PowerShell ISE Script pane.</span></span> <span data-ttu-id="71503-254">Den här egenskapen är ett Dictionary-objekt som innehåller namn-/värdepar med token-typer och färger för skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-254">This property is a dictionary object that contains name/value pairs of token types and colors for the Script pane.</span></span> <span data-ttu-id="71503-255">Om du vill ändra färgerna i IntelliSense-tokens i konsol fönstret, se [ConsoleTokenColors](#consoletokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-255">To change the colors of the IntelliSense tokens in the Console pane, see [ConsoleTokenColors](#consoletokencolors).</span></span>
<span data-ttu-id="71503-256">Information om hur du återställer färgerna till standardvärdena finns i [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-256">To reset the colors to the default values, see [RestoreDefaultTokenColors](#restoredefaulttokencolors).</span></span>
<span data-ttu-id="71503-257">Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, okänd, variabel.</span><span class="sxs-lookup"><span data-stu-id="71503-257">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span>

```powershell
# Sets the color of commands to green.
$psISE.Options.TokenColors["Command"] = "green"
# Sets the color of keywords to magenta.
$psISE.Options.TokenColors["Keyword"] = "magenta"
```

### <a name="useentertoselectinconsolepaneintellisense"></a><span data-ttu-id="71503-258">UseEnterToSelectInConsolePaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="71503-258">UseEnterToSelectInConsolePaneIntellisense</span></span>

<span data-ttu-id="71503-259">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-259">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-260">Anger om du kan använda RETUR-tangenten för att välja ett IntelliSense-alternativ i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-260">Specifies whether you can use the Enter key to select an IntelliSense provided option in the Console pane.</span></span> <span data-ttu-id="71503-261">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-261">The default value is `$true`.</span></span>

```powershell
# Turn off using the ENTER key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $false
```

### <a name="useentertoselectinscriptpaneintellisense"></a><span data-ttu-id="71503-262">UseEnterToSelectInScriptPaneIntellisense</span><span class="sxs-lookup"><span data-stu-id="71503-262">UseEnterToSelectInScriptPaneIntellisense</span></span>

<span data-ttu-id="71503-263">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-263">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-264">Anger om du kan använda RETUR-tangenten för att välja ett IntelliSense-alternativ i skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-264">Specifies whether you can use the Enter key to select an IntelliSense-provided option in the Script pane.</span></span> <span data-ttu-id="71503-265">Standardvärdet är `$true`.</span><span class="sxs-lookup"><span data-stu-id="71503-265">The default value is `$true`.</span></span>

```powershell
# Turn on using the Enter key to select an IntelliSense provided option in the Console pane.
$psISE.Options.UseEnterToSelectInConsolePaneIntellisense = $true
```

### <a name="uselocalhelp"></a><span data-ttu-id="71503-266">UseLocalHelp</span><span class="sxs-lookup"><span data-stu-id="71503-266">UseLocalHelp</span></span>

<span data-ttu-id="71503-267">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-267">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-268">Anger om den lokalt installerade hjälpen eller online TechNet Library-hjälpen visas när du trycker på <kbd>F1</kbd> med markören placerad i ett nyckelord.</span><span class="sxs-lookup"><span data-stu-id="71503-268">Specifies whether the locally installed Help or the online TechNet Library Help appears when you press <kbd>F1</kbd> with the cursor positioned in a keyword.</span></span> <span data-ttu-id="71503-269">Om detta är inställt på `$true` visas innehållet från den lokalt installerade hjälpen i ett popup-fönster.</span><span class="sxs-lookup"><span data-stu-id="71503-269">If set to `$true`, then a pop-up window shows content from the locally installed Help.</span></span> <span data-ttu-id="71503-270">Du kan installera hjälpfilerna genom att köra `Update-Help` kommandot.</span><span class="sxs-lookup"><span data-stu-id="71503-270">You can install the Help files by running the `Update-Help` command.</span></span> <span data-ttu-id="71503-271">Om det är inställt på `$false` , öppnas webbläsaren på en sida i TechNet-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="71503-271">If set to `$false`, then your browser opens to a page in the TechNet Library.</span></span>

```powershell
# Sets the option for the online help to be displayed.
$psISE.Options.UseLocalHelp = $false
# Sets the option for the local Help to be displayed.
$psISE.Options.UseLocalHelp = $true
```

### <a name="verbosebackgroundcolor"></a><span data-ttu-id="71503-272">VerboseBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-272">VerboseBackgroundColor</span></span>

<span data-ttu-id="71503-273">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-273">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-274">Anger bakgrunds färgen för utförlig text som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-274">Specifies the background color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="71503-275">Det är ett **system. Windows. Media. Color** -objekt.</span><span class="sxs-lookup"><span data-stu-id="71503-275">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for verbose text to blue.
$psISE.Options.VerboseBackgroundColor ='#0000FF'
```

### <a name="verboseforegroundcolor"></a><span data-ttu-id="71503-276">VerboseForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-276">VerboseForegroundColor</span></span>

<span data-ttu-id="71503-277">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-277">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-278">Anger förgrunds färgen för utförlig text som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-278">Specifies the foreground color for verbose text that appears in the Console pane.</span></span> <span data-ttu-id="71503-279">Det är ett **system. Windows. Media. Color** -objekt.</span><span class="sxs-lookup"><span data-stu-id="71503-279">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for verbose text to yellow.
$psISE.Options.VerboseForegroundColor = 'yellow'
```

### <a name="warningbackgroundcolor"></a><span data-ttu-id="71503-280">WarningBackgroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-280">WarningBackgroundColor</span></span>

<span data-ttu-id="71503-281">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-281">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-282">Anger bakgrunds färgen för varnings text som visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-282">Specifies the background color for warning text that appears in the Console pane.</span></span> <span data-ttu-id="71503-283">Det är ett **system. Windows. Media. Color** -objekt.</span><span class="sxs-lookup"><span data-stu-id="71503-283">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the background color for warning text to blue.
$psISE.Options.WarningBackgroundColor = '#0000FF'
```

### <a name="warningforegroundcolor"></a><span data-ttu-id="71503-284">WarningForegroundColor</span><span class="sxs-lookup"><span data-stu-id="71503-284">WarningForegroundColor</span></span>

<span data-ttu-id="71503-285">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="71503-285">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="71503-286">Anger förgrunds färgen för varnings text som visas i fönstret utdata.</span><span class="sxs-lookup"><span data-stu-id="71503-286">Specifies the foreground color for warning text that appears in the Output pane.</span></span> <span data-ttu-id="71503-287">Det är ett **system. Windows. Media. Color** -objekt.</span><span class="sxs-lookup"><span data-stu-id="71503-287">It is a **System.Windows.Media.Color** object.</span></span>

```powershell
# Changes the foreground color for warning text to yellow.
$psISE.Options.WarningForegroundColor = 'yellow'
```

### <a name="xmltokencolors"></a><span data-ttu-id="71503-288">XmlTokenColors</span><span class="sxs-lookup"><span data-stu-id="71503-288">XmlTokenColors</span></span>

<span data-ttu-id="71503-289">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-289">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-290">Anger ett Dictionary-objekt som innehåller namn/värde-par av tokens och färger för XML-innehåll som visas i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="71503-290">Specifies a dictionary object that contains name/value pairs of token types and colors for XML content that is displayed in Windows PowerShell ISE.</span></span> <span data-ttu-id="71503-291">Token-färger kan anges för följande: attribut, kommando, CommandArgument, CommandParameter, comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, member, ny rad, Number, Operator, position, StatementSeparator, sträng, typ, okänd, variabel.</span><span class="sxs-lookup"><span data-stu-id="71503-291">Token colors can be set for the following: Attribute, Command, CommandArgument, CommandParameter, Comment, GroupEnd, GroupStart, Keyword, LineContinuation, LoopLabel, Member, NewLine, Number, Operator, Position, StatementSeparator, String, Type, Unknown, Variable.</span></span> <span data-ttu-id="71503-292">Se även [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span><span class="sxs-lookup"><span data-stu-id="71503-292">Also see [RestoreDefaultXmlTokenColors](#restoredefaultxmltokencolors).</span></span>

```powershell
# Sets the color of XML element names to green.
$psISE.Options.XmlTokenColors["ElementName"] = 'green'
# Sets the color of XML comments to magenta.
$psISE.Options.XmlTokenColors["Comment"] = 'magenta'
```

### <a name="zoom"></a><span data-ttu-id="71503-293">Zoom</span><span class="sxs-lookup"><span data-stu-id="71503-293">Zoom</span></span>

<span data-ttu-id="71503-294">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="71503-294">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="71503-295">Anger den relativa storleken på text i både konsol-och skript fönstret.</span><span class="sxs-lookup"><span data-stu-id="71503-295">Specifies the relative size of text in both the Console and Script panes.</span></span> <span data-ttu-id="71503-296">Standardvärdet är 100.</span><span class="sxs-lookup"><span data-stu-id="71503-296">The default value is 100.</span></span>
<span data-ttu-id="71503-297">Mindre värden gör att texten i Windows PowerShell ISE visas mindre medan större tal gör att texten blir större.</span><span class="sxs-lookup"><span data-stu-id="71503-297">Smaller values cause the text in Windows PowerShell ISE to appear smaller while larger numbers cause text to appear larger.</span></span> <span data-ttu-id="71503-298">Värdet är ett heltal som sträcker sig från 20 till 400.</span><span class="sxs-lookup"><span data-stu-id="71503-298">The value is an integer that ranges from 20 to 400.</span></span>

```powershell
# Changes the text in the Windows PowerShell ISE to be double its normal size.
$psISE.Options.Zoom = 200
```

## <a name="see-also"></a><span data-ttu-id="71503-299">Se även</span><span class="sxs-lookup"><span data-stu-id="71503-299">See Also</span></span>

- [<span data-ttu-id="71503-300">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="71503-300">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="71503-301">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="71503-301">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
