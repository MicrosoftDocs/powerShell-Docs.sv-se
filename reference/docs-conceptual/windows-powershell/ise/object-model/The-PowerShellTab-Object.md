---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: PowerShellTab-objektet
ms.openlocfilehash: 55e3678a8285f0ec7e8131d98c87478216c26f37
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810913"
---
# <a name="the-powershelltab-object"></a>PowerShellTab-objektet

Objektet **PowerShellTab** representerar en miljö för Windows PowerShell-körningsmiljön.

## <a name="methods"></a>Metoder

### <a name="invoke-script-"></a>Anropa \( skript\)

Stöds i Windows PowerShell ISE 2,0 och senare.

Kör det aktuella skriptet på PowerShell-fliken.

> [!NOTE]
> Den här metoden fungerar bara på andra PowerShell-flikar, inte på PowerShell-fliken som den körs från. Det returnerar inga objekt eller värde. Om koden ändrar vilken variabel som helst, sparas ändringarna på fliken som kommandot anropades mot.

**Skript** -system. Management. Automation. script block eller en sträng som skript blocket ska köras.

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous- \( skript, \[ useNewScope \] , millisecondsTimeout\)

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Kör det aktuella skriptet på PowerShell-fliken.

> [!NOTE]
> Den här metoden fungerar bara på andra PowerShell-flikar, inte på PowerShell-fliken som den körs från. Skript blocket körs och alla värden som returneras från skriptet returneras till den körnings miljö från vilken du anropade kommandot. Om kommandot tar längre tid att köra än **millesecondsTimeout** -värdet anger, Miss lyckas kommandot med ett undantag: "åtgärden har nått sin tids gräns."

**Skript** -system. Management. Automation. script block eller en sträng som skript blocket ska köras.

** \[ useNewScope \] ** – valfritt booleskt värde som är standardvärdet `$true` om det är inställt på `$true` , skapas en ny omfattning i vilken kommandot ska köras. Den ändrar inte körnings miljön för PowerShell-fliken som anges av kommandot.

** \[ millisecondsTimeout \] ** -valfritt heltal som är som standard **500**.
Om kommandot inte slutförs inom den angivna tiden genererar kommandot en **TimeoutException** med meddelandet "åtgärden har nått sin tids gräns."

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

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar tilläggs menyn för PowerShell-fliken.

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

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade booleska egenskapen som returnerar ett `$true` värde om ett skript kan anropas med metoden [Invoke (skript)](#invoke-script-) .

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

### <a name="consolepane"></a>ConsolePane

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner. I Windows PowerShell ISE 2,0 heter **CommandPane**.

Den skrivskyddade egenskapen som hämtar konsol fönstrets [redigerings](The-ISEEditor-Object.md) objekt.

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a>DisplayName

Stöds i Windows PowerShell ISE 2,0 och senare.

Egenskapen Read-Write som hämtar eller anger den text som visas på PowerShell-fliken. Som standard heter flikarna "PowerShell #" där # representerar ett tal.

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a>ExpandedScript

Stöds i Windows PowerShell ISE 2,0 och senare.

Den Read-Write-booleska egenskap som avgör om skript fönstret är expanderat eller dolt.

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a>Filer

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar de [skriptfiler](The-ISEFileCollection-Object.md) som är öppna på PowerShell-fliken.

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Resultat

Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE. I senare versioner av Windows PowerShell ISE kan du använda **ConsolePane** -objektet för samma syfte.

Den skrivskyddade egenskapen som hämtar fönstret utdata i den aktuella [redigeraren](The-ISEEditor-Object.md).

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>Uppmaning

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar den aktuella meddelande texten. Obs: **prompt** -funktionen kan åsidosättas av användarens™ s-profil. Om resultatet skiljer sig från en enkel sträng returnerar den här egenskapen ingenting.

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Egenskapen Read-Write som anger om kommando fönstret visas för tillfället.

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a>Status text

Stöds i Windows PowerShell ISE 2,0 och senare.

Den skrivskyddade egenskapen som hämtar **PowerShellTab** status text.

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som anger om fönstret för horisontella tillägg är öppet.

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened

Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.

Den skrivskyddade egenskapen som anger om det lodräta tilläggets verktygs fönster är öppet.

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Se även

- [PowerShellTabCollection-objektet](The-PowerShellTabCollection-Object.md)
- [Användningsområden för Windows PowerShell ISE-skriptobjektmodellen](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Objekt modells-hierarkin för ISE](The-ISE-Object-Model-Hierarchy.md)
