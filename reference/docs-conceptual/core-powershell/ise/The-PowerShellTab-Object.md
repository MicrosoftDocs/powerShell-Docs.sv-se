---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet PowerShellTab
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: 15d9a7474e4c2cf2a9ff8edb88802106489cdba1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-powershelltab-object"></a>Objektet PowerShellTab
  Den **PowerShellTab** -objektet representerar en körningsmiljö för Windows PowerShell.

## <a name="methods"></a>Metoder

### <a name="invoke-script-"></a>Anropa\( skript\)
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Kör det angivna skriptet på fliken PowerShell.

> [!NOTE]
> Den här metoden fungerar bara på andra flikar i PowerShell, inte fliken PowerShell där den körs. Den returnerar inte några objekt eller -värde. Om den ändrar alla variabler, spara ändringarna på fliken mot vilken kommandot anropades.

 **Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.

```
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psise.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a>InvokeSynchronous\( skript \[useNewScope\], millisecondsTimeout\)
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Kör det angivna skriptet på fliken PowerShell.

> [!NOTE]
> Den här metoden fungerar bara på andra flikar i PowerShell, inte fliken PowerShell där den körs. Skriptblocket körs och returneras ett värde som returneras från skriptet kör miljön som du startade kommandot. Om kommandot tar längre tid att köra än den **millesecondsTimeout** värdet anger sedan kommandot misslyckas med ett undantag: ”åtgärden tog för lång”.

 **Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.

 **\[useNewScope\]**  -valfritt booleskt som används som standard till **$true** om inställd på **$true**, skapas ett nytt scope att köra kommandot. Den ändrar inte körningsmiljön på fliken PowerShell som anges av kommandot.

 **\[millisecondsTimeout\]**  -valfritt heltal som standard **500**.
Om kommandot inte slutförs inom den angivna tiden och sedan kommandot skapar en **TimeoutException** med meddelandet ”åtgärden tog för lång”.

```
# create a new PowerShell tab and then switch back to the first
$PSise.PowerShellTabs.Add()
$psISE.PowerShellTabs.SetSelectedPowerShellTab($psISE.PowerShellTabs[0]) 

# Invoke a simple command on the other tab, in its own scope
$psISE.PowerShellTabs[1].InvokeSynchronous('$x=1',$false)
# You can switch to the other tab and type 'œ$x' to see that the value is saved there.

# This example sets a value in the other tab (in a different scope) 
# and returns it through the pipeline to this tab to store in $a
$a=$psISE.PowerShellTabs[1].InvokeSynchronous('$z=3;$z') 
$a

# This example runs a command that takes longer than the allowed timeout value
# and measures how long it runs so that you can see the impact
measure-command {$psISE.PowerShellTabs[1].InvokeSynchronous("sleep 10",$false,5000)}

```

## <a name="properties"></a>Egenskaper

### <a name="addonsmenu"></a>AddOnsMenu
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar menyn tillägg för PowerShell-fliken.

```
# Clear the Add-ons menu if one exists.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
# Create an AddOns menu with an accessor.
# Note the use of "_"  as opposed to the "&" for mapping to the fast key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P") 
# Add a nested menu. 
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("Parent",$null,$null) 
$parentAdded.SubMenus.Add("_Dir",{dir},"Alt+D")
# Show the Add-ons menu on the current PowerShell tab.
$psISE.CurrentPowerShellTab.AddOnsMenu
```

### <a name="caninvoke"></a>CanInvoke
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade boolesk egenskap som returnerar en **$true** värde om ett skript som kan anropas med de [Invoke (skript)](#invoke-script-) metod.

```
# CanInvoke will be false if the PowerShell
# tab is running a script that takes a while, and you
# check its properties from another PowerShell tab. It is
# always false if checked on the current PowerShell tab. 
# Manually create a second PowerShell tab before running this script.
# Return to the first tab and type
$secondTab = $psise.PowerShellTabs[1] 
$secondTab.CanInvoke 
$secondTab.Invoke({sleep 20})
$secondTab.CanInvoke

```

### <a name="consolepane"></a>Consolepane
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.  I Windows PowerShell ISE 2.0 detta hette **CommandPane**.

 Skrivskyddad egenskap som hämtar konsolfönstret [editor](../ise/The-ISEEditor-Object.md) objekt.

```
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane

```

### <a name="displayname"></a>Visningsnamn
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Egenskapen skrivskyddad som hämtar eller anger texten som visas på fliken PowerShell. Som standard flikar namnet ”PowerShell #”, där # motsvarar ett tal.

```
$newTab = $psise.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="Brand New Tab"
```

### <a name="expandedscript"></a>ExpandedScript
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Läsa / skriva boolesk egenskap som bestämmer om skriptfönstret visas eller döljs.

```
# Toggle the expanded script property to see its effect.
$PSise.CurrentPowerShellTab.ExpandedScript=!$PSise.CurrentPowerShellTab.ExpandedScript

```

### <a name="files"></a>Filer
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar den [samling skriptfiler](../ise/The-ISEFileCollection-Object.md) som är öppna på fliken PowerShell.

```
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb" 
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a>Utdata
  Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.  I senare versioner av Windows PowerShell ISE kan du använda den **ConsolePane** objekt för samma ändamål.

 Skrivskyddad egenskap som hämtar fönstret utdata i aktuellt [editor](../ise/The-ISEEditor-Object.md).

```
# Clears the text in the Output pane.
$psise.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a>kommandotolk
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Den skrivskyddade egenskapen som hämtar den aktuella texten. Obs: den **fråga** funktion kan åsidosättas av användaren ”™ s profil. Om resultatet är en sträng, har den här egenskapen returnerar något.

```
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a>ShowCommands
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Egenskapen skrivskyddad som anger om kommandorutan visas för närvarande.

```
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $True
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands=$True}
```

### <a name="statustext"></a>StatusTex
  Stöds i Windows PowerShell ISE 2.0 och senare. 

 Skrivskyddad egenskap som hämtar den **PowerShellTab** statustexten.

```
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a>HorizontalAddOnToolsPaneOpened
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Den skrivskyddade egenskapen som anger om verktygsfönstret vågräta tilläggskomponenter är öppen.

```
# Gets the current state of the horizontal Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a>VerticalAddOnToolsPaneOpened
  Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner. 

 Den skrivskyddade egenskapen som anger om lodräta tillägg verktygsfönstret är öppen.

```
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands=$True
# Gets the current state of the vertical Add-ons tool pane. 
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a>Se även
- [Objektet PowerShellTabCollection](The-PowerShellTabCollection-Object.md) 
- [Windows PowerShell ISE Scripting Object Model](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Windows PowerShell ISE objektreferens modellen](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Modellen objekthierarkin ISE](../ise/The-ISE-Object-Model-Hierarchy.md)

  
