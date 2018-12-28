---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: PowerShellTab-objektet
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 577e2aaaddf3071801816d9ae91dbf0006dd5072
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404865"
---
# <a name="the-powershelltab-object"></a>PowerShellTab-objektet

Den **PowerShellTab** -objektet representerar en Windows PowerShell-körningsmiljö.

## <a name="methods"></a>Metoder

### <a name="invoke-script-"></a>Anropa\( skript \)

Stöds i Windows PowerShell ISE 2.0 och senare.

Kör det angivna skriptet i PowerShell-flik.

> [!NOTE]
> Den här metoden fungerar bara på en annan PowerShell-flik inte fliken PowerShell där den körs. Den returnerar inte några objekt eller -värde. Om den ändrar alla variabler, spara dessa ändringar på fliken mot vilken kommandot anropades.

**Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( skriptet \[useNewScope\], millisecondsTimeout \)

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Kör det angivna skriptet i PowerShell-flik.

> [!NOTE]
> Den här metoden fungerar bara på en annan PowerShell-flik inte fliken PowerShell där den körs. Skriptblocket körs och ett värde som returneras från skriptet returneras till körningsmiljön varifrån du startade kommandot. Om kommandot tar längre tid än den **millesecondsTimeout** värdet anger sedan kommandot misslyckas med ett undantag: ”Åtgärden har nått tidsgränsen”.

**Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.

**\[useNewScope\]**  -valfritt booleskt som standard **$true** om inställd **$true**, skapas ett nytt scope som att köra kommandot. Den ändras inte körningsmiljö för tabellen PowerShell som anges av kommandot.

**\[millisecondsTimeout\]**  -valfritt heltal som standard **500**.
Om kommandot inte slutförs inom den angivna tiden så genererar kommandot ett **TimeoutException** med meddelandet ”åtgärden har nått tidsgränsen”.

```powershell
# Create a new PowerShell tab and then switch back to the first
$psISE.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0])

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1', $false)
# You can switch to the other tab and type '$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope)
# and returns it through the pipeline to this tab to store in $a
$a = $psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z')
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
Measure-Command {$psISE.PowerShellTabs[1].InvokeSynchronous('sleep 10', $false, 5000)}
```

## <a name="properties"></a>Egenskaper

### <a name="addonsmenu"></a>AddOnsMenu

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar menyn tillägg för PowerShell-flik.

```powershell
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade boolesk egenskap som returnerar en **$true** värde om ett skript som kan anropas med den [Invoke (skript)](#invoke-script-) metod.

```powershell
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab.
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psISE.PowerShellTabs[1]
$secondTab.CanInvoke
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke
```

### <a name="consolepane"></a>Consolepane

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.  I Windows PowerShell ISE 2.0 det hette **CommandPane**.

Skrivskyddad egenskap som hämtar konsolfönstret [redigeraren](The-ISEEditor-Object.md) objekt.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>Visningsnamn

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar eller anger texten som visas på fliken PowerShell. Som standard flikarna namnges ”PowerShell #”, där # motsvarar ett tal.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Stöds i Windows PowerShell ISE 2.0 och senare.

Läs-och boolesk egenskap som bestämmer om skriptfönstret är utökat eller döljs.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Filer

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar den [samling skriptfiler](The-ISEFileCollection-Object.md) som är öppna i PowerShell-flik.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Utdata

Den här funktionen har finns i Windows PowerShell ISE 2.0, men tagits bort eller byta namn i senare versioner av ISE.  I senare versioner av Windows PowerShell ISE kan du använda den **ConsolePane** objekt för samma ändamål.

Skrivskyddad egenskap som hämtar utdatafönstret för aktuellt [redigeraren](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Fråga

Stöds i Windows PowerShell ISE 2.0 och senare.

Den skrivskyddade egenskapen som hämtar den aktuella texten. Obs: den **fråga** funktion kan åsidosättas av användaren ”™ s profil. Om resultatet är än en enkel sträng, har den här egenskapen returnerar något.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Egenskapen Läs-och som indikerar om rutan kommandon som visas.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>StatusText

Stöds i Windows PowerShell ISE 2.0 och senare.

Skrivskyddad egenskap som hämtar den **PowerShellTab** statusText.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som anger om verktygsfönstret vågrät tillägg är öppen.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som anger om verktygsfönstret lodrät tillägg är öppen.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Se även

- [PowerShellTabCollection-objektet](The-PowerShellTabCollection-Object.md)
- [Syftet med den Windows PowerShell ISE-Skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)