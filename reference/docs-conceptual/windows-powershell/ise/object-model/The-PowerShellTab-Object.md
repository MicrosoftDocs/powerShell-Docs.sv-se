---
ms.date: 06/05/2017
title: PowerShellTab-objektet
description: Objektet PowerShellTab representerar en miljö för Windows PowerShell-körningsmiljön.
ms.openlocfilehash: ac89875e408a41a92d7e3d1a83a849466296c3c6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663393"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="d9a61-103">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="d9a61-103">The PowerShellTab Object</span></span>

<span data-ttu-id="d9a61-104">Objektet **PowerShellTab** representerar en miljö för Windows PowerShell-körningsmiljön.</span><span class="sxs-lookup"><span data-stu-id="d9a61-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="d9a61-105">Metoder</span><span class="sxs-lookup"><span data-stu-id="d9a61-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="d9a61-106">Anropa \( skript \)</span><span class="sxs-lookup"><span data-stu-id="d9a61-106">Invoke\( Script \)</span></span>

<span data-ttu-id="d9a61-107">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-108">Kör det aktuella skriptet på PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="d9a61-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="d9a61-109">Den här metoden fungerar bara på andra PowerShell-flikar, inte på PowerShell-fliken som den körs från.</span><span class="sxs-lookup"><span data-stu-id="d9a61-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="d9a61-110">Det returnerar inga objekt eller värde.</span><span class="sxs-lookup"><span data-stu-id="d9a61-110">It does not return any object or value.</span></span> <span data-ttu-id="d9a61-111">Om koden ändrar vilken variabel som helst, sparas ändringarna på fliken som kommandot anropades mot.</span><span class="sxs-lookup"><span data-stu-id="d9a61-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="d9a61-112">**Skript** -system. Management. Automation. script block eller en sträng som skript blocket ska köras.</span><span class="sxs-lookup"><span data-stu-id="d9a61-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="d9a61-113">InvokeSynchronous- \( skript, \[ useNewScope \] , millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="d9a61-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="d9a61-114">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d9a61-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9a61-115">Kör det aktuella skriptet på PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="d9a61-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="d9a61-116">Den här metoden fungerar bara på andra PowerShell-flikar, inte på PowerShell-fliken som den körs från.</span><span class="sxs-lookup"><span data-stu-id="d9a61-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="d9a61-117">Skript blocket körs och alla värden som returneras från skriptet returneras till den körnings miljö från vilken du anropade kommandot.</span><span class="sxs-lookup"><span data-stu-id="d9a61-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="d9a61-118">Om kommandot tar längre tid att köra än **millesecondsTimeout** -värdet anger, Miss lyckas kommandot med ett undantag: "åtgärden har nått sin tids gräns."</span><span class="sxs-lookup"><span data-stu-id="d9a61-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="d9a61-119">**Skript** -system. Management. Automation. script block eller en sträng som skript blocket ska köras.</span><span class="sxs-lookup"><span data-stu-id="d9a61-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="d9a61-120">**\[ useNewScope \]** – valfritt booleskt värde som är standardvärdet `$true` om det är inställt på `$true` , skapas en ny omfattning i vilken kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="d9a61-120">**\[useNewScope\]** -  Optional Boolean that defaults to `$true` If set to `$true`, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="d9a61-121">Den ändrar inte körnings miljön för PowerShell-fliken som anges av kommandot.</span><span class="sxs-lookup"><span data-stu-id="d9a61-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="d9a61-122">**\[ millisecondsTimeout \]** -valfritt heltal som är som standard **500** .</span><span class="sxs-lookup"><span data-stu-id="d9a61-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500** .</span></span>
<span data-ttu-id="d9a61-123">Om kommandot inte slutförs inom den angivna tiden genererar kommandot en **TimeoutException** med meddelandet "åtgärden har nått sin tids gräns."</span><span class="sxs-lookup"><span data-stu-id="d9a61-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="d9a61-124">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d9a61-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="d9a61-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="d9a61-125">AddOnsMenu</span></span>

<span data-ttu-id="d9a61-126">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-127">Den skrivskyddade egenskapen som hämtar tilläggs menyn för PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="d9a61-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="d9a61-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="d9a61-128">CanInvoke</span></span>

<span data-ttu-id="d9a61-129">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-130">Den skrivskyddade booleska egenskapen som returnerar ett `$true` värde om ett skript kan anropas med metoden [Invoke (skript)](#invoke-script-) .</span><span class="sxs-lookup"><span data-stu-id="d9a61-130">The read-only Boolean property that returns a `$true` value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="d9a61-131">ConsolePane</span><span class="sxs-lookup"><span data-stu-id="d9a61-131">ConsolePane</span></span>

<span data-ttu-id="d9a61-132">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d9a61-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span> <span data-ttu-id="d9a61-133">I Windows PowerShell ISE 2,0 heter **CommandPane** .</span><span class="sxs-lookup"><span data-stu-id="d9a61-133">In Windows PowerShell ISE 2.0 this was named **CommandPane** .</span></span>

<span data-ttu-id="d9a61-134">Den skrivskyddade egenskapen som hämtar konsol fönstrets [redigerings](The-ISEEditor-Object.md) objekt.</span><span class="sxs-lookup"><span data-stu-id="d9a61-134">The read-only property that gets the Console pane [editor](The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="d9a61-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d9a61-135">DisplayName</span></span>

<span data-ttu-id="d9a61-136">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-137">Egenskapen Read-Write som hämtar eller anger den text som visas på PowerShell-fliken. Som standard heter flikarna "PowerShell #" där # representerar ett tal.</span><span class="sxs-lookup"><span data-stu-id="d9a61-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="d9a61-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="d9a61-138">ExpandedScript</span></span>

<span data-ttu-id="d9a61-139">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-140">Den Read-Write-booleska egenskap som avgör om skript fönstret är expanderat eller dolt.</span><span class="sxs-lookup"><span data-stu-id="d9a61-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="d9a61-141">Files</span><span class="sxs-lookup"><span data-stu-id="d9a61-141">Files</span></span>

<span data-ttu-id="d9a61-142">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-143">Den skrivskyddade egenskapen som hämtar de [skriptfiler](The-ISEFileCollection-Object.md) som är öppna på PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="d9a61-143">The read-only property that gets the [collection of script files](The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="d9a61-144">Utdata</span><span class="sxs-lookup"><span data-stu-id="d9a61-144">Output</span></span>

<span data-ttu-id="d9a61-145">Den här funktionen finns i Windows PowerShell ISE 2,0, men har tagits bort eller bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="d9a61-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span> <span data-ttu-id="d9a61-146">I senare versioner av Windows PowerShell ISE kan du använda **ConsolePane** -objektet för samma syfte.</span><span class="sxs-lookup"><span data-stu-id="d9a61-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="d9a61-147">Den skrivskyddade egenskapen som hämtar fönstret utdata i den aktuella [redigeraren](The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="d9a61-147">The read-only property that gets the Output pane of the current [editor](The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="d9a61-148">Prompt</span><span class="sxs-lookup"><span data-stu-id="d9a61-148">Prompt</span></span>

<span data-ttu-id="d9a61-149">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-150">Den skrivskyddade egenskapen som hämtar den aktuella meddelande texten.</span><span class="sxs-lookup"><span data-stu-id="d9a61-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="d9a61-151">Obs: **prompt** -funktionen kan åsidosättas av användarens &trade; profil.</span><span class="sxs-lookup"><span data-stu-id="d9a61-151">Note: the **Prompt** function can be overridden by the user'&trade;s profile.</span></span> <span data-ttu-id="d9a61-152">Om resultatet skiljer sig från en enkel sträng returnerar den här egenskapen ingenting.</span><span class="sxs-lookup"><span data-stu-id="d9a61-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="d9a61-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="d9a61-153">ShowCommands</span></span>

<span data-ttu-id="d9a61-154">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d9a61-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9a61-155">Egenskapen Read-Write som anger om kommando fönstret visas för tillfället.</span><span class="sxs-lookup"><span data-stu-id="d9a61-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="d9a61-156">Status text</span><span class="sxs-lookup"><span data-stu-id="d9a61-156">StatusText</span></span>

<span data-ttu-id="d9a61-157">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d9a61-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="d9a61-158">Den skrivskyddade egenskapen som hämtar **PowerShellTab** status text.</span><span class="sxs-lookup"><span data-stu-id="d9a61-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="d9a61-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="d9a61-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="d9a61-160">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d9a61-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9a61-161">Den skrivskyddade egenskapen som anger om det vågräta Add-Ons verktygs fönstret är öppet.</span><span class="sxs-lookup"><span data-stu-id="d9a61-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="d9a61-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="d9a61-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="d9a61-163">Stöds i Windows PowerShell ISE 3,0 och senare, och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="d9a61-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d9a61-164">Den skrivskyddade egenskapen som anger om den lodräta Add-Ons verktygs fönstret är öppet.</span><span class="sxs-lookup"><span data-stu-id="d9a61-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="d9a61-165">Se även</span><span class="sxs-lookup"><span data-stu-id="d9a61-165">See Also</span></span>

- [<span data-ttu-id="d9a61-166">PowerShellTabCollection-objektet</span><span class="sxs-lookup"><span data-stu-id="d9a61-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="d9a61-167">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="d9a61-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d9a61-168">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="d9a61-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
