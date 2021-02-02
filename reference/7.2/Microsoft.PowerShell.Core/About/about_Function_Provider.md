---
description: Funktion
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Funktions leverantör
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710615"
---
# <a name="function-provider"></a><span data-ttu-id="6fce9-103">Funktions leverantör</span><span class="sxs-lookup"><span data-stu-id="6fce9-103">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="6fce9-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="6fce9-104">Provider name</span></span>
<span data-ttu-id="6fce9-105">Funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-105">Function</span></span>

## <a name="drives"></a><span data-ttu-id="6fce9-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="6fce9-106">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="6fce9-107">Funktioner</span><span class="sxs-lookup"><span data-stu-id="6fce9-107">Capabilities</span></span>

<span data-ttu-id="6fce9-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="6fce9-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="6fce9-109">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="6fce9-109">Short description</span></span>

<span data-ttu-id="6fce9-110">Ger åtkomst till de funktioner som definierats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fce9-110">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="6fce9-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="6fce9-111">Detailed description</span></span>

<span data-ttu-id="6fce9-112">Med PowerShell **Function** -providern kan du hämta, lägga till, ändra, radera och ta bort funktioner och filter i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fce9-112">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="6fce9-113">En funktion är ett namngivet kodblock som utför en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="6fce9-113">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="6fce9-114">När du skriver in funktions namnet körs koden i funktionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-114">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="6fce9-115">Ett filter är ett namngivet kodblock som upprättar villkor för en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="6fce9-115">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="6fce9-116">Du kan ange namnet på filtret i stället för villkoret, t. ex. i ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="6fce9-116">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="6fce9-117">**Funktions** enheten är en planad namnrymd som bara innehåller funktionen och filtrerar objekt.</span><span class="sxs-lookup"><span data-stu-id="6fce9-117">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="6fce9-118">Varken Functions eller filter har underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="6fce9-118">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="6fce9-119">**Funktions** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="6fce9-119">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="6fce9-120">Get-location</span><span class="sxs-lookup"><span data-stu-id="6fce9-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="6fce9-121">Ange plats</span><span class="sxs-lookup"><span data-stu-id="6fce9-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="6fce9-122">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="6fce9-123">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="6fce9-124">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="6fce9-125">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="6fce9-126">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="6fce9-126">Types exposed by this provider</span></span>

<span data-ttu-id="6fce9-127">Varje funktion är en instans av klassen [system. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) .</span><span class="sxs-lookup"><span data-stu-id="6fce9-127">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="6fce9-128">Varje filter är en instans av klassen [system. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .</span><span class="sxs-lookup"><span data-stu-id="6fce9-128">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="6fce9-129">Navigera i funktions enheten</span><span class="sxs-lookup"><span data-stu-id="6fce9-129">Navigating the Function drive</span></span>

<span data-ttu-id="6fce9-130">**Funktions** leverantören visar dess data lager på `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-130">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="6fce9-131">Om du vill arbeta med funktioner kan du ändra platsen till `Function:` enheten ( `Set-Location Function:` ).</span><span class="sxs-lookup"><span data-stu-id="6fce9-131">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="6fce9-132">Eller så kan du arbeta från en annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-132">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="6fce9-133">Om du vill referera till en funktion från en annan plats använder du enhets namnet ( `Function:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-133">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="6fce9-134">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="6fce9-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="6fce9-135">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="6fce9-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="6fce9-136">Du kan också arbeta med **funktions** leverantören från någon annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-136">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="6fce9-137">Om du vill referera till en funktion från en annan plats använder du enhets namnet `Function:` i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-137">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="6fce9-138">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="6fce9-138">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="6fce9-139">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="6fce9-139">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="6fce9-140">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="6fce9-140">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="6fce9-141">Hämta funktioner</span><span class="sxs-lookup"><span data-stu-id="6fce9-141">Getting functions</span></span>

<span data-ttu-id="6fce9-142">Det här kommandot hämtar listan över alla funktioner i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-142">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="6fce9-143">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-143">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="6fce9-144">Funktions leverantören har inga behållare, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-144">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="6fce9-145">Du kan hämta en funktions definition genom att komma åt **definitions** egenskapen, som du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="6fce9-145">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="6fce9-146">Du kan också hämta en funktions definition med hjälp av dess Provider-sökväg som föregås av dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="6fce9-146">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="6fce9-147">Hämtar markerade funktioner</span><span class="sxs-lookup"><span data-stu-id="6fce9-147">Getting selected functions</span></span>

<span data-ttu-id="6fce9-148">Detta kommando hämtar `man` funktionen från `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-148">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="6fce9-149">Den använder `Get-Item` cmdleten för att hämta funktionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-149">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="6fce9-150">Pipeline-operatorn ( `|` ) skickar resultatet till `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-150">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="6fce9-151">`-Wrap`Parametern dirigerar text som inte får plats på raden till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="6fce9-151">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="6fce9-152">`-Autosize`Parametern ändrar storlek på tabell kolumnerna för att rymma texten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-152">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="6fce9-153">Arbeta med sökvägar för funktions leverantörer</span><span class="sxs-lookup"><span data-stu-id="6fce9-153">Working with Function provider paths</span></span>

<span data-ttu-id="6fce9-154">De här kommandona hämtar funktionen med namnet `c:` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-154">These commands both get the function named `c:`.</span></span> <span data-ttu-id="6fce9-155">Det första kommandot kan användas i vilken enhet som helst.</span><span class="sxs-lookup"><span data-stu-id="6fce9-155">The first command can be used in any drive.</span></span> <span data-ttu-id="6fce9-156">Det andra kommandot används i `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-156">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="6fce9-157">Eftersom namnet slutar i ett kolon, vilket är syntaxen för en enhet, måste du kvalificera sökvägen med enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-157">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="6fce9-158">I `Function:` enheten kan du använda något av formaten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-158">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="6fce9-159">I det andra kommandot representerar punkten ( `.` ) den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-159">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="6fce9-160">Skapa en funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-160">Creating a function</span></span>

<span data-ttu-id="6fce9-161">Detta kommando använder `New-Item` cmdleten för att skapa en funktion som kallas `Win32:` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-161">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="6fce9-162">Uttrycket i klamrar är det skript block som representeras av funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-162">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="6fce9-163">Du kan också skapa en funktion genom att skriva den på PowerShell-kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="6fce9-163">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="6fce9-164">Till exempel TPE `Function:Win32: {Set-Location C:\Windows\System32}` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-164">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="6fce9-165">Om du är i `Function:` enheten kan du utelämna enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-165">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="6fce9-166">Ta bort en funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-166">Deleting a function</span></span>

<span data-ttu-id="6fce9-167">Det här kommandot tar bort `more:` funktionen från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-167">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="6fce9-168">Ändra en funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-168">Changing a function</span></span>

<span data-ttu-id="6fce9-169">Detta kommando använder `Set-Item` cmdleten för att ändra `prompt` funktionen så att den visar tiden före sökvägen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-169">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="6fce9-170">Byta namn på en funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-170">Rename a function</span></span>

<span data-ttu-id="6fce9-171">Detta kommando använder `Rename-Item` cmdleten för att ändra namnet på `help` funktionen till `gh` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-171">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="6fce9-172">Kopiera en funktion</span><span class="sxs-lookup"><span data-stu-id="6fce9-172">Copying a function</span></span>

<span data-ttu-id="6fce9-173">Detta kommando kopierar `prompt` funktionen till `oldPrompt` , och skapar ett nytt namn för skript blocket som är associerat med prompt-funktionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-173">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="6fce9-174">Du kan använda detta för att spara den ursprungliga prompt-funktionen om du planerar att ändra den.</span><span class="sxs-lookup"><span data-stu-id="6fce9-174">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="6fce9-175">Egenskapen **Options** för den nya funktionen har värdet `None` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-175">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="6fce9-176">Om du vill ändra värdet för egenskapen **alternativ** använder du `Set-Item` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-176">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="6fce9-177">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="6fce9-177">Dynamic parameters</span></span>

<span data-ttu-id="6fce9-178">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="6fce9-178">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="6fce9-179">Alternativ < [system. Management. Automation. ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="6fce9-179">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="6fce9-180">Anger värdet för egenskapen **Options** för en funktion.</span><span class="sxs-lookup"><span data-stu-id="6fce9-180">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="6fce9-181">`None`: Inga alternativ.</span><span class="sxs-lookup"><span data-stu-id="6fce9-181">`None`: No options.</span></span> <span data-ttu-id="6fce9-182">`None` används som standard.</span><span class="sxs-lookup"><span data-stu-id="6fce9-182">`None` is the default.</span></span>
- <span data-ttu-id="6fce9-183">`Constant`: Det går inte att ta bort funktionen och dess egenskaper kan inte ändras.</span><span class="sxs-lookup"><span data-stu-id="6fce9-183">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="6fce9-184">`Constant` är bara tillgängligt när du skapar en funktion.</span><span class="sxs-lookup"><span data-stu-id="6fce9-184">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="6fce9-185">Du kan inte ändra alternativet för en befintlig funktion till `Constant` .</span><span class="sxs-lookup"><span data-stu-id="6fce9-185">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="6fce9-186">`Private`: Funktionen är endast synlig i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="6fce9-186">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="6fce9-187">(inte i underordnade omfång).</span><span class="sxs-lookup"><span data-stu-id="6fce9-187">(not in child scopes).</span></span>
- <span data-ttu-id="6fce9-188">`ReadOnly`: Det går inte att ändra egenskaperna för funktionen, förutom med `-Force` parametern.</span><span class="sxs-lookup"><span data-stu-id="6fce9-188">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="6fce9-189">Du kan använda `Remove-Item` för att ta bort funktionen.</span><span class="sxs-lookup"><span data-stu-id="6fce9-189">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="6fce9-190">`AllScope`: Funktionen kopieras till alla nya omfattningar som skapas.</span><span class="sxs-lookup"><span data-stu-id="6fce9-190">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="6fce9-191">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="6fce9-191">Cmdlets supported</span></span>

- [<span data-ttu-id="6fce9-192">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-192">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="6fce9-193">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="6fce9-193">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="6fce9-194">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="6fce9-194">Using the pipeline</span></span>

<span data-ttu-id="6fce9-195">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="6fce9-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="6fce9-196">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6fce9-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="6fce9-197">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="6fce9-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="6fce9-198">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="6fce9-198">Getting help</span></span>

<span data-ttu-id="6fce9-199">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="6fce9-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="6fce9-200">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="6fce9-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="6fce9-201">Se även</span><span class="sxs-lookup"><span data-stu-id="6fce9-201">See also</span></span>

[<span data-ttu-id="6fce9-202">about_Functions</span><span class="sxs-lookup"><span data-stu-id="6fce9-202">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="6fce9-203">about_Providers</span><span class="sxs-lookup"><span data-stu-id="6fce9-203">about_Providers</span></span>](../About/about_Providers.md)
