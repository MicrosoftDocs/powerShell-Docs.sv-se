---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: PowerShellTab-objektet
ms.assetid: a9b58556-951b-4f48-b3ae-b351b7564360
ms.openlocfilehash: c10f9106e31bb05828f1e76554ebe40ddb778340
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30952519"
---
# <a name="the-powershelltab-object"></a><span data-ttu-id="236d6-103">PowerShellTab-objektet</span><span class="sxs-lookup"><span data-stu-id="236d6-103">The PowerShellTab Object</span></span>

<span data-ttu-id="236d6-104">Den **PowerShellTab** -objektet representerar en körningsmiljö för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="236d6-104">The **PowerShellTab** object represents a Windows PowerShell runtime environment.</span></span>

## <a name="methods"></a><span data-ttu-id="236d6-105">Metoder</span><span class="sxs-lookup"><span data-stu-id="236d6-105">Methods</span></span>

### <a name="invoke-script-"></a><span data-ttu-id="236d6-106">Anropa\( skript \)</span><span class="sxs-lookup"><span data-stu-id="236d6-106">Invoke\( Script \)</span></span>

<span data-ttu-id="236d6-107">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-107">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-108">Kör det angivna skriptet på fliken PowerShell.</span><span class="sxs-lookup"><span data-stu-id="236d6-108">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="236d6-109">Den här metoden fungerar bara på andra flikar i PowerShell, inte fliken PowerShell där den körs.</span><span class="sxs-lookup"><span data-stu-id="236d6-109">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="236d6-110">Den returnerar inte några objekt eller -värde.</span><span class="sxs-lookup"><span data-stu-id="236d6-110">It does not return any object or value.</span></span> <span data-ttu-id="236d6-111">Om den ändrar alla variabler, spara ändringarna på fliken mot vilken kommandot anropades.</span><span class="sxs-lookup"><span data-stu-id="236d6-111">If the code modifies any variable, then those changes persist on the tab against which the command was invoked.</span></span>

<span data-ttu-id="236d6-112">**Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.</span><span class="sxs-lookup"><span data-stu-id="236d6-112">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

```powershell
# Manually create a second PowerShell tab before running this script.
# Return to the first PowerShell tab and type the following command
$psISE.PowerShellTabs[1].Invoke({dir})
```

### <a name="invokesynchronous-script-usenewscope-millisecondstimeout-"></a><span data-ttu-id="236d6-113">InvokeSynchronous\( skript \[useNewScope\], millisecondsTimeout \)</span><span class="sxs-lookup"><span data-stu-id="236d6-113">InvokeSynchronous\( Script, \[useNewScope\], millisecondsTimeout \)</span></span>

<span data-ttu-id="236d6-114">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="236d6-114">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="236d6-115">Kör det angivna skriptet på fliken PowerShell.</span><span class="sxs-lookup"><span data-stu-id="236d6-115">Runs the given script in the PowerShell tab.</span></span>

> [!NOTE]
> <span data-ttu-id="236d6-116">Den här metoden fungerar bara på andra flikar i PowerShell, inte fliken PowerShell där den körs.</span><span class="sxs-lookup"><span data-stu-id="236d6-116">This method only works on other PowerShell tabs, not the PowerShell tab from which it is run.</span></span> <span data-ttu-id="236d6-117">Skriptblocket körs och returneras ett värde som returneras från skriptet kör miljön som du startade kommandot.</span><span class="sxs-lookup"><span data-stu-id="236d6-117">The script block is run and any value that is returned from the script is returned to the run environment from which you invoked the command.</span></span> <span data-ttu-id="236d6-118">Om kommandot tar längre tid att köra än den **millesecondsTimeout** värdet anger sedan kommandot misslyckas med ett undantag: ”åtgärden tog för lång”.</span><span class="sxs-lookup"><span data-stu-id="236d6-118">If the command takes longer to run than the **millesecondsTimeout** value specifies, then the command fails with an exception: "The operation has timed out."</span></span>

<span data-ttu-id="236d6-119">**Skriptet** -System.Management.Automation.ScriptBlock eller sträng skriptblocket ska köras.</span><span class="sxs-lookup"><span data-stu-id="236d6-119">**Script** - System.Management.Automation.ScriptBlock or String The script block to run.</span></span>

<span data-ttu-id="236d6-120">**\[useNewScope\]**  -valfritt booleskt som används som standard till **$true** om inställd på **$true**, skapas ett nytt scope att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="236d6-120">**\[useNewScope\]** -  Optional Boolean that defaults to **$true** If set to **$true**, then a new scope is created within which to run the command.</span></span> <span data-ttu-id="236d6-121">Den ändrar inte körningsmiljön på fliken PowerShell som anges av kommandot.</span><span class="sxs-lookup"><span data-stu-id="236d6-121">It does not modify the runtime environment of the PowerShell tab that is specified by the command.</span></span>

<span data-ttu-id="236d6-122">**\[millisecondsTimeout\]**  -valfritt heltal som standard **500**.</span><span class="sxs-lookup"><span data-stu-id="236d6-122">**\[millisecondsTimeout\]** -  Optional integer that defaults to **500**.</span></span>
<span data-ttu-id="236d6-123">Om kommandot inte slutförs inom den angivna tiden och sedan kommandot skapar en **TimeoutException** med meddelandet ”åtgärden tog för lång”.</span><span class="sxs-lookup"><span data-stu-id="236d6-123">If the command does not finish within the specified time, then the command generates a **TimeoutException** with the message "The operation has timed out."</span></span>

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

## <a name="properties"></a><span data-ttu-id="236d6-124">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="236d6-124">Properties</span></span>

### <a name="addonsmenu"></a><span data-ttu-id="236d6-125">AddOnsMenu</span><span class="sxs-lookup"><span data-stu-id="236d6-125">AddOnsMenu</span></span>

<span data-ttu-id="236d6-126">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-126">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-127">Den skrivskyddade egenskapen som hämtar menyn tillägg för PowerShell-fliken.</span><span class="sxs-lookup"><span data-stu-id="236d6-127">The read-only property that gets the Add-ons menu for the PowerShell tab.</span></span>

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

### <a name="caninvoke"></a><span data-ttu-id="236d6-128">CanInvoke</span><span class="sxs-lookup"><span data-stu-id="236d6-128">CanInvoke</span></span>

<span data-ttu-id="236d6-129">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-129">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-130">Den skrivskyddade boolesk egenskap som returnerar en **$true** värde om ett skript som kan anropas med de [Invoke (skript)](#invoke-script-) metod.</span><span class="sxs-lookup"><span data-stu-id="236d6-130">The read-only Boolean property that returns a **$true** value if a script can be invoked with the [Invoke( Script )](#invoke-script-) method.</span></span>

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

### <a name="consolepane"></a><span data-ttu-id="236d6-131">Consolepane</span><span class="sxs-lookup"><span data-stu-id="236d6-131">Consolepane</span></span>

<span data-ttu-id="236d6-132">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="236d6-132">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>  <span data-ttu-id="236d6-133">I Windows PowerShell ISE 2.0 detta hette **CommandPane**.</span><span class="sxs-lookup"><span data-stu-id="236d6-133">In Windows PowerShell ISE 2.0 this was named **CommandPane**.</span></span>

<span data-ttu-id="236d6-134">Skrivskyddad egenskap som hämtar konsolfönstret [editor](../ise/The-ISEEditor-Object.md) objekt.</span><span class="sxs-lookup"><span data-stu-id="236d6-134">The read-only property that gets the Console pane [editor](../ise/The-ISEEditor-Object.md) object.</span></span>

```powershell
# Gets the Console Pane editor.
$psISE.CurrentPowerShellTab.ConsolePane
```

### <a name="displayname"></a><span data-ttu-id="236d6-135">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="236d6-135">DisplayName</span></span>

<span data-ttu-id="236d6-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-137">Egenskapen skrivskyddad som hämtar eller anger texten som visas på fliken PowerShell. Som standard flikar namnet ”PowerShell #”, där # motsvarar ett tal.</span><span class="sxs-lookup"><span data-stu-id="236d6-137">The read-write property that gets or sets the text that is displayed on the PowerShell tab. By default, tabs are named "PowerShell #", where the # represents a number.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="expandedscript"></a><span data-ttu-id="236d6-138">ExpandedScript</span><span class="sxs-lookup"><span data-stu-id="236d6-138">ExpandedScript</span></span>

<span data-ttu-id="236d6-139">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-139">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-140">Läsa / skriva boolesk egenskap som bestämmer om skriptfönstret visas eller döljs.</span><span class="sxs-lookup"><span data-stu-id="236d6-140">The read-write Boolean property that determines whether the Script pane is expanded or hidden.</span></span>

```powershell
# Toggle the expanded script property to see its effect.
$psISE.CurrentPowerShellTab.ExpandedScript = !$psISE.CurrentPowerShellTab.ExpandedScript
```

### <a name="files"></a><span data-ttu-id="236d6-141">Filer</span><span class="sxs-lookup"><span data-stu-id="236d6-141">Files</span></span>

<span data-ttu-id="236d6-142">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-142">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-143">Skrivskyddad egenskap som hämtar den [samling skriptfiler](../ise/The-ISEFileCollection-Object.md) som är öppna på fliken PowerShell.</span><span class="sxs-lookup"><span data-stu-id="236d6-143">The read-only property that gets the [collection of script files](../ise/The-ISEFileCollection-Object.md) that are open in the PowerShell tab.</span></span>

```powershell
$newFile = $psISE.CurrentPowerShellTab.Files.Add()
$newFile.Editor.Text = "a`r`nb"
# Gets the line count
$newFile.Editor.LineCount
```

### <a name="output"></a><span data-ttu-id="236d6-144">Utdata</span><span class="sxs-lookup"><span data-stu-id="236d6-144">Output</span></span>

<span data-ttu-id="236d6-145">Funktionen har finns i Windows PowerShell ISE 2.0 men tagits bort eller har bytt namn i senare versioner av ISE.</span><span class="sxs-lookup"><span data-stu-id="236d6-145">This feature is present in Windows PowerShell ISE 2.0, but was removed or renamed in later versions of the ISE.</span></span>  <span data-ttu-id="236d6-146">I senare versioner av Windows PowerShell ISE kan du använda den **ConsolePane** objekt för samma ändamål.</span><span class="sxs-lookup"><span data-stu-id="236d6-146">In later versions of Windows PowerShell ISE, you can use the **ConsolePane** object for the same purposes.</span></span>

<span data-ttu-id="236d6-147">Skrivskyddad egenskap som hämtar fönstret utdata i aktuellt [editor](../ise/The-ISEEditor-Object.md).</span><span class="sxs-lookup"><span data-stu-id="236d6-147">The read-only property that gets the Output pane of the current [editor](../ise/The-ISEEditor-Object.md).</span></span>

```powershell
# Clears the text in the Output pane.
$psISE.CurrentPowerShellTab.output.clear()
```

### <a name="prompt"></a><span data-ttu-id="236d6-148">kommandotolk</span><span class="sxs-lookup"><span data-stu-id="236d6-148">Prompt</span></span>

<span data-ttu-id="236d6-149">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-149">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-150">Den skrivskyddade egenskapen som hämtar den aktuella texten.</span><span class="sxs-lookup"><span data-stu-id="236d6-150">The read-only property that gets the current prompt text.</span></span> <span data-ttu-id="236d6-151">Obs: den **fråga** funktion kan åsidosättas av användaren ”™ s profil.</span><span class="sxs-lookup"><span data-stu-id="236d6-151">Note: the **Prompt** function can be overridden by the user'™s profile.</span></span> <span data-ttu-id="236d6-152">Om resultatet är en sträng, har den här egenskapen returnerar något.</span><span class="sxs-lookup"><span data-stu-id="236d6-152">If the result is other than a simple string, then this property returns nothing.</span></span>

```powershell
# Gets the current prompt text.
$psISE.CurrentPowerShellTab.Prompt
```

### <a name="showcommands"></a><span data-ttu-id="236d6-153">ShowCommands</span><span class="sxs-lookup"><span data-stu-id="236d6-153">ShowCommands</span></span>

<span data-ttu-id="236d6-154">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="236d6-154">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="236d6-155">Egenskapen skrivskyddad som anger om kommandorutan visas för närvarande.</span><span class="sxs-lookup"><span data-stu-id="236d6-155">The read-write property that indicates if the Commands pane is currently displayed.</span></span>

```powershell
# Gets the current status of the Commands pane and stores it in the $a variable
$a = $psISE.CurrentPowerShellTab.ShowCommands
# if $a is $false, then turn the Commands pane on by changing the value to $true
if (!$a) {$psISE.CurrentPowerShellTab.ShowCommands = $true}
```

### <a name="statustext"></a><span data-ttu-id="236d6-156">StatusTex</span><span class="sxs-lookup"><span data-stu-id="236d6-156">StatusText</span></span>

<span data-ttu-id="236d6-157">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="236d6-157">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="236d6-158">Skrivskyddad egenskap som hämtar den **PowerShellTab** statustexten.</span><span class="sxs-lookup"><span data-stu-id="236d6-158">The read-only property that gets the **PowerShellTab** status text.</span></span>

```powershell
# Gets the current status text,
$psISE.CurrentPowerShellTab.StatusText
```

### <a name="horizontaladdontoolspaneopened"></a><span data-ttu-id="236d6-159">HorizontalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="236d6-159">HorizontalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="236d6-160">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="236d6-160">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="236d6-161">Den skrivskyddade egenskapen som anger om verktygsfönstret vågräta tilläggskomponenter är öppen.</span><span class="sxs-lookup"><span data-stu-id="236d6-161">The read-only property that indicates whether the horizontal Add-Ons tool pane is currently open.</span></span>

```powershell
# Gets the current state of the horizontal Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

### <a name="verticaladdontoolspaneopened"></a><span data-ttu-id="236d6-162">VerticalAddOnToolsPaneOpened</span><span class="sxs-lookup"><span data-stu-id="236d6-162">VerticalAddOnToolsPaneOpened</span></span>

<span data-ttu-id="236d6-163">Stöds i Windows PowerShell ISE 3.0 och senare och finns inte i tidigare versioner.</span><span class="sxs-lookup"><span data-stu-id="236d6-163">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="236d6-164">Den skrivskyddade egenskapen som anger om lodräta tillägg verktygsfönstret är öppen.</span><span class="sxs-lookup"><span data-stu-id="236d6-164">The read-only property that indicates whether the vertical Add-Ons tool pane is currently open.</span></span>

```powershell
# Turns on the Commands pane
$psISE.CurrentPowerShellTab.ShowCommands = $true
# Gets the current state of the vertical Add-ons tool pane.
$psISE.CurrentPowerShellTab.HorizontalAddOnToolsPaneOpened
```

## <a name="see-also"></a><span data-ttu-id="236d6-165">Se även</span><span class="sxs-lookup"><span data-stu-id="236d6-165">See Also</span></span>

- [<span data-ttu-id="236d6-166">Objektet PowerShellTabCollection</span><span class="sxs-lookup"><span data-stu-id="236d6-166">The PowerShellTabCollection Object</span></span>](The-PowerShellTabCollection-Object.md)
- [<span data-ttu-id="236d6-167">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="236d6-167">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="236d6-168">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="236d6-168">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)