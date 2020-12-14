---
description: Beskriver variabler som lagrar Tillståndsinformation för PowerShell. Dessa variabler skapas och underhålls av PowerShell.
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 134649405c05e527039694d7c4fdf38d3c64b79e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710698"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="639af-104">Om automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="639af-104">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="639af-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="639af-105">Short description</span></span>

<span data-ttu-id="639af-106">Beskriver variabler som lagrar Tillståndsinformation för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="639af-106">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="639af-107">Dessa variabler skapas och underhålls av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="639af-107">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="639af-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="639af-108">Long description</span></span>

<span data-ttu-id="639af-109">Dessa variabler anses konceptuellt vara skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="639af-109">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="639af-110">Även om de **kan** skrivas till **bör de inte** skrivas för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="639af-110">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="639af-111">Här är en lista över de automatiska variablerna i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="639af-111">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="639af-112">Innehåller den sista token i den sista raden som togs emot av sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-112">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="639af-113">$?</span><span class="sxs-lookup"><span data-stu-id="639af-113">$?</span></span>

<span data-ttu-id="639af-114">Innehåller körnings status för det sista kommandot.</span><span class="sxs-lookup"><span data-stu-id="639af-114">Contains the execution status of the last command.</span></span> <span data-ttu-id="639af-115">Det innehåller **Sant** om det sista kommandot lyckades och **falskt** om det misslyckades.</span><span class="sxs-lookup"><span data-stu-id="639af-115">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="639af-116">För cmdlets och avancerade funktioner som körs i flera steg i en pipeline, t. ex. i både `process` och `end` block, som anropar `this.WriteError()` eller `$PSCmdlet.WriteError()` på någon punkt, anges `$?` till **falskt**, som `this.ThrowTerminatingError()` och `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="639af-116">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False**, as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="639af-117">`Write-Error`Cmdleten anges alltid `$?` till **false** omedelbart efter att den körts, men är inte inställd `$?` på **false** för en funktion som anropar den:</span><span class="sxs-lookup"><span data-stu-id="639af-117">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="639af-118">För det senare ändamålet `$PSCmdlet.WriteError()` ska du i stället använda.</span><span class="sxs-lookup"><span data-stu-id="639af-118">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="639af-119">För inbyggda kommandon (körbara filer) `$?` anges till **Sant** när `$LASTEXITCODE` är 0 och anges till **falskt** om `$LASTEXITCODE` är ett annat värde.</span><span class="sxs-lookup"><span data-stu-id="639af-119">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="639af-120">Fram till PowerShell 7, som innehåller en instruktion inom parentes `(...)` , återställs inte syntaxen för under uttryck `$(...)` eller mat ris uttryck `@(...)` `$?` till **True**, så att `(Write-Error)` visas `$?` som **Sant**.</span><span class="sxs-lookup"><span data-stu-id="639af-120">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True**, so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="639af-121">Detta har ändrats i PowerShell 7, så det `$?` visar alltid det faktiska resultatet för det sista kommandot som körs i dessa uttryck.</span><span class="sxs-lookup"><span data-stu-id="639af-121">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="639af-122">Innehåller den första token i den sista raden som togs emot av sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-122">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="639af-123">$_</span><span class="sxs-lookup"><span data-stu-id="639af-123">$_</span></span>

<span data-ttu-id="639af-124">Samma som `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="639af-124">Same as `$PSItem`.</span></span> <span data-ttu-id="639af-125">Innehåller det aktuella objektet i pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="639af-125">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="639af-126">Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="639af-126">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="639af-127">$args</span><span class="sxs-lookup"><span data-stu-id="639af-127">$args</span></span>

<span data-ttu-id="639af-128">Innehåller en matris med värden för parametrar som inte har deklarerats som skickas till en funktion, ett skript eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="639af-128">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="639af-129">När du skapar en funktion kan du deklarera parametrarna med hjälp av `param` nyckelordet eller genom att lägga till en kommaavgränsad lista med parametrar inom parentes efter funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="639af-129">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="639af-130">I en händelse åtgärd `$Args` innehåller variabeln objekt som representerar händelse argumenten för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="639af-130">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="639af-131">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="639af-131">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="639af-132">Värdet för den här variabeln finns också i egenskapen **SourceArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="639af-132">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="639af-133">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="639af-133">$ConsoleFileName</span></span>

<span data-ttu-id="639af-134">Innehåller sökvägen till konsol filen ( `.psc1` ) som senast användes i sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-134">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="639af-135">Den här variabeln fylls när du startar PowerShell med parametern **PSConsoleFile** eller när du använder `Export-Console` cmdleten för att exportera snapin-namn till en konsol fil.</span><span class="sxs-lookup"><span data-stu-id="639af-135">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="639af-136">När du använder `Export-Console` cmdleten utan parametrar uppdaterar den automatiskt konsol filen som användes senast i sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-136">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="639af-137">Du kan använda den här automatiska variabeln för att avgöra vilken fil som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="639af-137">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="639af-138">$Error</span><span class="sxs-lookup"><span data-stu-id="639af-138">$Error</span></span>

<span data-ttu-id="639af-139">Innehåller en matris med fel objekt som representerar de senaste felen.</span><span class="sxs-lookup"><span data-stu-id="639af-139">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="639af-140">Det senaste felet är det första fel objektet i matrisen `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="639af-140">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="639af-141">Om du vill förhindra att ett fel läggs till i `$Error` matrisen använder du parametern **ErrorAction** common med värdet **Ignore**.</span><span class="sxs-lookup"><span data-stu-id="639af-141">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="639af-142">Mer information finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="639af-142">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="639af-143">$Event</span><span class="sxs-lookup"><span data-stu-id="639af-143">$Event</span></span>

<span data-ttu-id="639af-144">Innehåller ett **PSEventArgs** -objekt som representerar den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="639af-144">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="639af-145">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando, till exempel `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="639af-145">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="639af-146">Värdet för den här variabeln är samma objekt som `Get-Event` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="639af-146">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="639af-147">Därför kan du använda egenskaperna för `Event` variabeln, till exempel `$Event.TimeGenerated` i ett- `Action` skript block.</span><span class="sxs-lookup"><span data-stu-id="639af-147">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="639af-148">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="639af-148">$EventArgs</span></span>

<span data-ttu-id="639af-149">Innehåller ett objekt som representerar det första händelse argumentet som härleds från **EventArgs** för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="639af-149">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="639af-150">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="639af-150">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="639af-151">Värdet för den här variabeln finns också i egenskapen **SourceEventArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="639af-151">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="639af-152">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="639af-152">$EventSubscriber</span></span>

<span data-ttu-id="639af-153">Innehåller ett **PSEventSubscriber** -objekt som representerar händelse prenumeranten för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="639af-153">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="639af-154">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="639af-154">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="639af-155">Värdet för den här variabeln är samma objekt som `Get-EventSubscriber` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="639af-155">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="639af-156">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="639af-156">$ExecutionContext</span></span>

<span data-ttu-id="639af-157">Innehåller ett **EngineIntrinsics** -objekt som representerar körnings kontexten för PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="639af-157">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="639af-158">Du kan använda den här variabeln för att hitta de körnings objekt som är tillgängliga för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="639af-158">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="639af-159">$false</span><span class="sxs-lookup"><span data-stu-id="639af-159">$false</span></span>

<span data-ttu-id="639af-160">Innehåller **falskt**.</span><span class="sxs-lookup"><span data-stu-id="639af-160">Contains **False**.</span></span> <span data-ttu-id="639af-161">Du kan använda den här variabeln för att representera **falskt** i kommandon och skript i stället för att använda strängen "false".</span><span class="sxs-lookup"><span data-stu-id="639af-161">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="639af-162">Strängen kan tolkas som **Sant** om den konverteras till en sträng som inte är tom eller till ett heltal som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="639af-162">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="639af-163">$foreach</span><span class="sxs-lookup"><span data-stu-id="639af-163">$foreach</span></span>

<span data-ttu-id="639af-164">Innehåller uppräkna ren (inte de resulterande värdena) för en [förgrunds](about_ForEach.md) slinga.</span><span class="sxs-lookup"><span data-stu-id="639af-164">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="639af-165">`$ForEach`Variabeln finns bara medan `ForEach` loopen körs. den tas bort när loopen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="639af-165">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="639af-166">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="639af-166">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="639af-167">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="639af-167">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="639af-168">$HOME</span><span class="sxs-lookup"><span data-stu-id="639af-168">$HOME</span></span>

<span data-ttu-id="639af-169">Innehåller den fullständiga sökvägen till användarens Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="639af-169">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="639af-170">Den här variabeln motsvarar `"$env:homedrive$env:homepath"` Windows-miljövariablerna, vanligt vis `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="639af-170">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="639af-171">$Host</span><span class="sxs-lookup"><span data-stu-id="639af-171">$Host</span></span>

<span data-ttu-id="639af-172">Innehåller ett objekt som representerar det aktuella värd programmet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="639af-172">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="639af-173">Du kan använda den här variabeln för att representera den aktuella värden i kommandon eller för att visa eller ändra egenskaperna för värden, till exempel `$Host.version` eller `$Host.CurrentCulture` , eller `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="639af-173">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="639af-174">$input</span><span class="sxs-lookup"><span data-stu-id="639af-174">$input</span></span>

<span data-ttu-id="639af-175">Innehåller en uppräknare som räknar upp alla indatatyper som skickas till en funktion.</span><span class="sxs-lookup"><span data-stu-id="639af-175">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="639af-176">`$input`Variabeln är endast tillgänglig för funktioner och skript block (som är ej namede funktioner).</span><span class="sxs-lookup"><span data-stu-id="639af-176">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="639af-177">I en funktion utan ett `Begin` , `Process` eller- `End` block, `$input` räknar variabeln upp indatamängden för funktionen.</span><span class="sxs-lookup"><span data-stu-id="639af-177">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="639af-178">I `Begin` blocket `$input` innehåller variabeln inga data.</span><span class="sxs-lookup"><span data-stu-id="639af-178">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="639af-179">I `Process` blocket `$input` innehåller variabeln det objekt som för närvarande finns i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="639af-179">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="639af-180">I `End` blocket `$input` räknar variabeln upp indatamängden för funktionen.</span><span class="sxs-lookup"><span data-stu-id="639af-180">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="639af-181">Du kan inte använda `$input` variabeln i både process blocket och slut blocket i samma funktion eller i ett skript block.</span><span class="sxs-lookup"><span data-stu-id="639af-181">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="639af-182">Eftersom `$input` är en uppräknare kan åtkomst till någon av dess egenskaper `$input` inte längre vara tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="639af-182">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="639af-183">Du kan lagra `$input` i en annan variabel om du vill återanvända `$input` egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="639af-183">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="639af-184">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="639af-184">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="639af-185">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="639af-185">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="iscoreclr"></a><span data-ttu-id="639af-186">$IsCoreCLR</span><span class="sxs-lookup"><span data-stu-id="639af-186">$IsCoreCLR</span></span>

<span data-ttu-id="639af-187">Innehåller `$True` om den aktuella sessionen körs på .net Core Runtime (CoreCLR).</span><span class="sxs-lookup"><span data-stu-id="639af-187">Contains `$True` if the current session is running on the .NET Core Runtime (CoreCLR).</span></span> <span data-ttu-id="639af-188">Innehåller annars `$False` .</span><span class="sxs-lookup"><span data-stu-id="639af-188">Otherwise contains `$False`.</span></span>

### <a name="islinux"></a><span data-ttu-id="639af-189">$IsLinux</span><span class="sxs-lookup"><span data-stu-id="639af-189">$IsLinux</span></span>

<span data-ttu-id="639af-190">Innehåller `$True` om den aktuella sessionen körs på ett Linux-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="639af-190">Contains `$True` if the current session is running on a Linux operating system.</span></span>
<span data-ttu-id="639af-191">Innehåller annars `$False` .</span><span class="sxs-lookup"><span data-stu-id="639af-191">Otherwise contains `$False`.</span></span>

### <a name="ismacos"></a><span data-ttu-id="639af-192">$IsMacOS</span><span class="sxs-lookup"><span data-stu-id="639af-192">$IsMacOS</span></span>

<span data-ttu-id="639af-193">Innehåller `$True` om den aktuella sessionen körs på ett MacOS-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="639af-193">Contains `$True` if the current session is running on a MacOS operating system.</span></span>
<span data-ttu-id="639af-194">Innehåller annars `$False` .</span><span class="sxs-lookup"><span data-stu-id="639af-194">Otherwise contains `$False`.</span></span>

### <a name="iswindows"></a><span data-ttu-id="639af-195">$IsWindows</span><span class="sxs-lookup"><span data-stu-id="639af-195">$IsWindows</span></span>

<span data-ttu-id="639af-196">Innehåller `$TRUE` om den aktuella sessionen körs på ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="639af-196">Contains `$TRUE` if the current session is running on a Windows operating system.</span></span> <span data-ttu-id="639af-197">Innehåller annars `$FALSE` .</span><span class="sxs-lookup"><span data-stu-id="639af-197">Otherwise contains `$FALSE`.</span></span>

### <a name="lastexitcode"></a><span data-ttu-id="639af-198">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="639af-198">$LastExitCode</span></span>

<span data-ttu-id="639af-199">Innehåller avslutnings koden för det senaste Windows-baserade program som kördes.</span><span class="sxs-lookup"><span data-stu-id="639af-199">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="639af-200">$Matches</span><span class="sxs-lookup"><span data-stu-id="639af-200">$Matches</span></span>

<span data-ttu-id="639af-201">`Matches`Variabeln fungerar med `-match` `-notmatch` operatorerna och.</span><span class="sxs-lookup"><span data-stu-id="639af-201">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="639af-202">När du skickar skalära indatatyper till `-match` `-notmatch` operatorn eller, och antingen identifierar en matchning, returnerar de ett booleskt värde och fyller den `$Matches` automatiska variabeln med en hash-tabell för alla sträng värden som matchades.</span><span class="sxs-lookup"><span data-stu-id="639af-202">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="639af-203">`$Matches`Hash-tabellen kan också fyllas i med insamlingar när du använder reguljära uttryck med `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="639af-203">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="639af-204">Mer information om `-match` operatorn finns i [about_Comparison_Operators](about_comparison_operators.md).</span><span class="sxs-lookup"><span data-stu-id="639af-204">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="639af-205">Mer information om reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="639af-205">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="639af-206">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="639af-206">$MyInvocation</span></span>

<span data-ttu-id="639af-207">Innehåller information om det aktuella kommandot, till exempel namn, parametrar, parameter värden och information om hur kommandot startades, anropades eller anropades, till exempel namnet på det skript som anropade det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="639af-207">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="639af-208">`$MyInvocation` är endast ifyllt för skript, funktions-och skript block.</span><span class="sxs-lookup"><span data-stu-id="639af-208">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="639af-209">Du kan använda informationen i objektet **system. Management. Automation. InvocationInfo** som `$MyInvocation` returneras i det aktuella skriptet, t. ex. sökvägen och fil namnet för skriptet ( `$MyInvocation.MyCommand.Path` ) eller namnet på en funktion ( `$MyInvocation.MyCommand.Name` ) för att identifiera det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="639af-209">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="639af-210">Detta är särskilt användbart för att hitta namnet på det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="639af-210">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="639af-211">Från och med PowerShell 3,0, `MyInvocation` har följande nya egenskaper.</span><span class="sxs-lookup"><span data-stu-id="639af-211">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="639af-212">Egenskap</span><span class="sxs-lookup"><span data-stu-id="639af-212">Property</span></span>      | <span data-ttu-id="639af-213">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="639af-213">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="639af-214">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="639af-214">**PSScriptRoot**</span></span>  | <span data-ttu-id="639af-215">Innehåller den fullständiga sökvägen till skriptet som anropades</span><span class="sxs-lookup"><span data-stu-id="639af-215">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="639af-216">det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="639af-216">the current command.</span></span> <span data-ttu-id="639af-217">Värdet för den här egenskapen är</span><span class="sxs-lookup"><span data-stu-id="639af-217">The value of this property is</span></span>  |
|               | <span data-ttu-id="639af-218">fylls bara i när anroparen är ett skript.</span><span class="sxs-lookup"><span data-stu-id="639af-218">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="639af-219">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="639af-219">**PSCommandPath**</span></span> | <span data-ttu-id="639af-220">Innehåller den fullständiga sökvägen till och fil namnet på skriptet</span><span class="sxs-lookup"><span data-stu-id="639af-220">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="639af-221">som anropade det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="639af-221">that invoked the current command.</span></span> <span data-ttu-id="639af-222">Värdet för det här</span><span class="sxs-lookup"><span data-stu-id="639af-222">The value of this</span></span> |
|               | <span data-ttu-id="639af-223">Egenskapen fylls bara när anroparen är en</span><span class="sxs-lookup"><span data-stu-id="639af-223">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="639af-224">över.</span><span class="sxs-lookup"><span data-stu-id="639af-224">script.</span></span>                                             |

<span data-ttu-id="639af-225">Till skillnad från `$PSScriptRoot` de `$PSCommandPath` automatiska variablerna innehåller egenskaperna **PSScriptRoot** och **PSCommandPath** för den `$MyInvocation` automatiska variabeln information om anroparen eller anropet till skriptet, inte det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="639af-225">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="639af-226">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="639af-226">$NestedPromptLevel</span></span>

<span data-ttu-id="639af-227">Innehåller den aktuella LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="639af-227">Contains the current prompt level.</span></span> <span data-ttu-id="639af-228">Värdet 0 anger den ursprungliga LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="639af-228">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="639af-229">Värdet ökar när du anger en kapslad nivå och när du avslutar det.</span><span class="sxs-lookup"><span data-stu-id="639af-229">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="639af-230">PowerShell visar till exempel en kapslad kommando tolk när du använder- `$Host.EnterNestedPrompt` metoden.</span><span class="sxs-lookup"><span data-stu-id="639af-230">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="639af-231">PowerShell visar också en kapslad kommando tolk när du når en Bryt punkt i PowerShell-felsökaren.</span><span class="sxs-lookup"><span data-stu-id="639af-231">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="639af-232">När du anger en kapslad prompt pausar PowerShell det aktuella kommandot, sparar körnings kontexten och ökar värdet för `$NestedPromptLevel` variabeln.</span><span class="sxs-lookup"><span data-stu-id="639af-232">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="639af-233">Om du vill skapa ytterligare kapslade kommando prompter (upp till 128 nivåer) eller återgå till den ursprungliga kommando tolken, slutför du kommandot eller Skriv `exit` .</span><span class="sxs-lookup"><span data-stu-id="639af-233">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="639af-234">`$NestedPromptLevel`Variabeln hjälper dig att spåra LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="639af-234">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="639af-235">Du kan skapa en alternativ kommando tolk för PowerShell som innehåller det här värdet så att det alltid är synligt.</span><span class="sxs-lookup"><span data-stu-id="639af-235">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="639af-236">$null</span><span class="sxs-lookup"><span data-stu-id="639af-236">$null</span></span>

<span data-ttu-id="639af-237">`$null` är en automatisk variabel som innehåller ett **Null** -värde eller ett tomt värde.</span><span class="sxs-lookup"><span data-stu-id="639af-237">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="639af-238">Du kan använda den här variabeln för att representera ett frånvarande eller odefinierat värde i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="639af-238">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="639af-239">PowerShell behandlar `$null` som ett objekt med ett värde, det vill säga som en explicit plats hållare, så att du kan använda `$null` för att representera ett tomt värde i en serie med värden.</span><span class="sxs-lookup"><span data-stu-id="639af-239">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="639af-240">När `$null` ingår i en samling räknas den till exempel som ett av objekten.</span><span class="sxs-lookup"><span data-stu-id="639af-240">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="639af-241">Om du rör `$null` variabeln till `ForEach-Object` cmdleten genererar den ett värde för `$null` , precis som för de andra objekten</span><span class="sxs-lookup"><span data-stu-id="639af-241">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="639af-242">Det innebär att du inte kan använda `$null` till att betyda ett **parameter värde**.</span><span class="sxs-lookup"><span data-stu-id="639af-242">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="639af-243">Ett parameter värde för `$null` åsidosätter standard parameter värde.</span><span class="sxs-lookup"><span data-stu-id="639af-243">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="639af-244">Men eftersom PowerShell behandlar `$null` variabeln som en plats hållare kan du använda den i skript som följande, som inte fungerar om `$null` ignorerades.</span><span class="sxs-lookup"><span data-stu-id="639af-244">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="639af-245">$PID</span><span class="sxs-lookup"><span data-stu-id="639af-245">$PID</span></span>

<span data-ttu-id="639af-246">Innehåller process identifieraren (PID) för processen som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-246">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="639af-247">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="639af-247">$PROFILE</span></span>

<span data-ttu-id="639af-248">Innehåller den fullständiga sökvägen till PowerShell-profilen för den aktuella användaren och det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="639af-248">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="639af-249">Du kan använda den här variabeln för att representera profilen i kommandon.</span><span class="sxs-lookup"><span data-stu-id="639af-249">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="639af-250">Du kan till exempel använda den i ett kommando för att avgöra om en profil har skapats:</span><span class="sxs-lookup"><span data-stu-id="639af-250">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="639af-251">Eller så kan du använda den i ett kommando för att skapa en profil:</span><span class="sxs-lookup"><span data-stu-id="639af-251">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="639af-252">Du kan använda den i ett kommando för att öppna profilen i **notepad.exe**:</span><span class="sxs-lookup"><span data-stu-id="639af-252">You can use it in a command to open the profile in **notepad.exe**:</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="639af-253">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="639af-253">$PSBoundParameters</span></span>

<span data-ttu-id="639af-254">Innehåller en lista över parametrar som skickas till ett skript eller en funktion och deras aktuella värden.</span><span class="sxs-lookup"><span data-stu-id="639af-254">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="639af-255">Den här variabeln har ett värde endast i ett omfång där parametrar deklareras, till exempel ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="639af-255">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="639af-256">Du kan använda den för att visa eller ändra aktuella värden för parametrar eller skicka parameter värden till ett annat skript eller en annan funktion.</span><span class="sxs-lookup"><span data-stu-id="639af-256">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="639af-257">I det här exemplet skickar funktionen **TEST2** `$PSBoundParameters` till **test1** -funktionen.</span><span class="sxs-lookup"><span data-stu-id="639af-257">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="639af-258">`$PSBoundParameters`Visas i formatet för **nyckel** och **värde**.</span><span class="sxs-lookup"><span data-stu-id="639af-258">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="639af-259">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="639af-259">$PSCmdlet</span></span>

<span data-ttu-id="639af-260">Innehåller ett objekt som representerar den cmdlet eller avancerad funktion som körs.</span><span class="sxs-lookup"><span data-stu-id="639af-260">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="639af-261">Du kan använda egenskaperna och metoderna för objektet i din cmdlet eller funktions kod för att svara på användnings villkoren.</span><span class="sxs-lookup"><span data-stu-id="639af-261">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="639af-262">Till exempel innehåller egenskapen **ParameterSetName** namnet på den parameter uppsättning som används och **ShouldProcess** -metoden lägger till **whatIf** -och **Confirm** -parametrarna i cmdleten dynamiskt.</span><span class="sxs-lookup"><span data-stu-id="639af-262">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="639af-263">Mer information om den `$PSCmdlet` automatiska variabeln finns i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) och [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="639af-263">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="639af-264">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="639af-264">$PSCommandPath</span></span>

<span data-ttu-id="639af-265">Innehåller den fullständiga sökvägen och fil namnet för det skript som körs.</span><span class="sxs-lookup"><span data-stu-id="639af-265">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="639af-266">Den här variabeln är giltig i alla skript.</span><span class="sxs-lookup"><span data-stu-id="639af-266">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="639af-267">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="639af-267">$PSCulture</span></span>

<span data-ttu-id="639af-268">Från och med PowerShell 7 `$PSCulture` återspeglar kulturen för den aktuella PowerShell-körnings utrymme (session).</span><span class="sxs-lookup"><span data-stu-id="639af-268">Beginning in PowerShell 7, `$PSCulture` reflects the culture of the current PowerShell runspace (session).</span></span> <span data-ttu-id="639af-269">Om kulturen ändras i en PowerShell-körnings utrymme `$PSCulture` uppdateras värdet för körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="639af-269">If the culture is changed in a PowerShell runspace, the `$PSCulture` value for that runspace is updated.</span></span>

<span data-ttu-id="639af-270">Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum och lagras i ett **system. globalisering. CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="639af-270">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="639af-271">Används `Get-Culture` för att Visa datorns kultur.</span><span class="sxs-lookup"><span data-stu-id="639af-271">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="639af-272">`$PSCulture` innehåller värde för egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="639af-272">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="639af-273">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="639af-273">$PSDebugContext</span></span>

<span data-ttu-id="639af-274">Vid fel sökning innehåller den här variabeln information om fel söknings miljön.</span><span class="sxs-lookup"><span data-stu-id="639af-274">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="639af-275">Annars innehåller den ett **Null** -värde.</span><span class="sxs-lookup"><span data-stu-id="639af-275">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="639af-276">Därför kan du använda den för att ange om fel söknings programmet har kontroll.</span><span class="sxs-lookup"><span data-stu-id="639af-276">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="639af-277">När den har fyllts i innehåller den ett **PsDebugContext** -objekt som har **Bryt punkter** och **InvocationInfo** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="639af-277">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="639af-278">Egenskapen **InvocationInfo** har flera användbara egenskaper, inklusive egenskapen **location** .</span><span class="sxs-lookup"><span data-stu-id="639af-278">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="639af-279">Egenskapen **location** anger sökvägen till skriptet som felsöks.</span><span class="sxs-lookup"><span data-stu-id="639af-279">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="639af-280">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="639af-280">$PSHOME</span></span>

<span data-ttu-id="639af-281">Innehåller den fullständiga sökvägen till installations katalogen för PowerShell, vanligt vis `$env:windir\System32\PowerShell\v1.0` i Windows-system.</span><span class="sxs-lookup"><span data-stu-id="639af-281">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="639af-282">Du kan använda den här variabeln i sökvägar för PowerShell-filer.</span><span class="sxs-lookup"><span data-stu-id="639af-282">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="639af-283">Till exempel söker följande kommando efter ordet **variabel** i de konceptuella hjälp avsnitten:</span><span class="sxs-lookup"><span data-stu-id="639af-283">For example, the following command searches the conceptual Help topics for the word **variable**:</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="639af-284">$PSItem</span><span class="sxs-lookup"><span data-stu-id="639af-284">$PSItem</span></span>

<span data-ttu-id="639af-285">Samma som `$_` .</span><span class="sxs-lookup"><span data-stu-id="639af-285">Same as `$_`.</span></span> <span data-ttu-id="639af-286">Innehåller det aktuella objektet i pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="639af-286">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="639af-287">Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="639af-287">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="639af-288">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="639af-288">$PSScriptRoot</span></span>

<span data-ttu-id="639af-289">Innehåller den katalog som ett skript körs från.</span><span class="sxs-lookup"><span data-stu-id="639af-289">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="639af-290">I PowerShell 2,0 är den här variabeln endast giltig i script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="639af-290">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="639af-291">Från och med PowerShell 3,0 är det giltigt i alla skript.</span><span class="sxs-lookup"><span data-stu-id="639af-291">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="639af-292">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="639af-292">$PSSenderInfo</span></span>

<span data-ttu-id="639af-293">Innehåller information om den användare som startade PSSession, inklusive användar identitet och tidszon på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="639af-293">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="639af-294">Den här variabeln är endast tillgänglig i PSSessions.</span><span class="sxs-lookup"><span data-stu-id="639af-294">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="639af-295">`$PSSenderInfo`Variabeln innehåller en egenskap som kan konfigureras av användaren, **ApplicationArguments**, som standard bara innehåller `$PSVersionTable` från den ursprungliga sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-295">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments**, that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="639af-296">Om du vill lägga till data i egenskapen **ApplicationArguments** använder du parametern **ApplicationArguments** för `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="639af-296">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="639af-297">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="639af-297">$PSUICulture</span></span>

<span data-ttu-id="639af-298">Innehåller namnet på användar gränssnitts kulturen (UI) som används i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="639af-298">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="639af-299">ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.</span><span class="sxs-lookup"><span data-stu-id="639af-299">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="639af-300">Detta är värdet för systemets **system.Globalization.CultureInfo.CurrentUICulture.name** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="639af-300">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="639af-301">Använd cmdleten för att hämta objektet **system. globalisering. CultureInfo** för systemet `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="639af-301">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="639af-302">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="639af-302">$PSVersionTable</span></span>

<span data-ttu-id="639af-303">Innehåller en skrivskyddad hash-tabell som visar information om den version av PowerShell som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="639af-303">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="639af-304">Tabellen innehåller följande objekt:</span><span class="sxs-lookup"><span data-stu-id="639af-304">The table includes the following items:</span></span>

| <span data-ttu-id="639af-305">Egenskap</span><span class="sxs-lookup"><span data-stu-id="639af-305">Property</span></span>                  | <span data-ttu-id="639af-306">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="639af-306">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="639af-307">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="639af-307">**PSVersion**</span></span>             | <span data-ttu-id="639af-308">PowerShell-versions numret</span><span class="sxs-lookup"><span data-stu-id="639af-308">The PowerShell version number</span></span>                 |
| <span data-ttu-id="639af-309">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="639af-309">**PSEdition**</span></span>             | <span data-ttu-id="639af-310">Den här egenskapen har värdet ' Desktop ' för</span><span class="sxs-lookup"><span data-stu-id="639af-310">This property has the value of 'Desktop' for</span></span>  |
|                           | <span data-ttu-id="639af-311">PowerShell 4 och lägre, samt PowerShell</span><span class="sxs-lookup"><span data-stu-id="639af-311">PowerShell 4 and below as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="639af-312">5,1 på kompletta Windows-versioner.</span><span class="sxs-lookup"><span data-stu-id="639af-312">5.1 on full-featured Windows editions.</span></span>        |
|                           | <span data-ttu-id="639af-313">Den här egenskapen har värdet "Core" för</span><span class="sxs-lookup"><span data-stu-id="639af-313">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="639af-314">PowerShell 6 och senare samt PowerShell</span><span class="sxs-lookup"><span data-stu-id="639af-314">PowerShell 6 and above as well as PowerShell</span></span>  |
|                           | <span data-ttu-id="639af-315">PowerShell 5,1 på versioner med nedsatt storlek</span><span class="sxs-lookup"><span data-stu-id="639af-315">PowerShell 5.1 on reduced-footprint editions</span></span>  |
|                           | <span data-ttu-id="639af-316">som Windows Nano Server eller Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="639af-316">like Windows Nano Server or Windows IoT.</span></span>      |
| <span data-ttu-id="639af-317">**GitCommitId**</span><span class="sxs-lookup"><span data-stu-id="639af-317">**GitCommitId**</span></span>           | <span data-ttu-id="639af-318">Inchecknings-ID: t för källfilerna, i GitHub</span><span class="sxs-lookup"><span data-stu-id="639af-318">The commit Id of the source files, in GitHub,</span></span> |
| <span data-ttu-id="639af-319">**Operativsystem**</span><span class="sxs-lookup"><span data-stu-id="639af-319">**OS**</span></span>                    | <span data-ttu-id="639af-320">Beskrivning av det operativ system som</span><span class="sxs-lookup"><span data-stu-id="639af-320">Description of the operating system that</span></span>      |
|                           | <span data-ttu-id="639af-321">PowerShell körs på.</span><span class="sxs-lookup"><span data-stu-id="639af-321">PowerShell is running on.</span></span>                     |
| <span data-ttu-id="639af-322">**Plattform**</span><span class="sxs-lookup"><span data-stu-id="639af-322">**Platform**</span></span>              | <span data-ttu-id="639af-323">Plattform som operativ systemet körs på</span><span class="sxs-lookup"><span data-stu-id="639af-323">Platform that the operating system is running</span></span> |
|                           | <span data-ttu-id="639af-324">för.</span><span class="sxs-lookup"><span data-stu-id="639af-324">on.</span></span> <span data-ttu-id="639af-325">Värdet på Linux och macOS är **UNIX**.</span><span class="sxs-lookup"><span data-stu-id="639af-325">The value on Linux and macOS is **Unix**.</span></span> |
|                           | <span data-ttu-id="639af-326">Se `$IsMacOs` och `$IsLinux` .</span><span class="sxs-lookup"><span data-stu-id="639af-326">See `$IsMacOs` and `$IsLinux`.</span></span>                |
| <span data-ttu-id="639af-327">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="639af-327">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="639af-328">Versioner av PowerShell som är kompatibla</span><span class="sxs-lookup"><span data-stu-id="639af-328">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="639af-329">med den aktuella versionen</span><span class="sxs-lookup"><span data-stu-id="639af-329">with the current version</span></span>                      |
| <span data-ttu-id="639af-330">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="639af-330">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="639af-331">Versionen av PowerShell-fjärrservern</span><span class="sxs-lookup"><span data-stu-id="639af-331">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="639af-332">hanterings protokoll.</span><span class="sxs-lookup"><span data-stu-id="639af-332">management protocol.</span></span>                          |
| <span data-ttu-id="639af-333">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="639af-333">**SerializationVersion**</span></span>  | <span data-ttu-id="639af-334">Versionen av serialiserings metoden</span><span class="sxs-lookup"><span data-stu-id="639af-334">The version of the serialization method</span></span>       |
| <span data-ttu-id="639af-335">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="639af-335">**WSManStackVersion**</span></span>     | <span data-ttu-id="639af-336">WS-Management stackens versions nummer</span><span class="sxs-lookup"><span data-stu-id="639af-336">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="639af-337">$PWD</span><span class="sxs-lookup"><span data-stu-id="639af-337">$PWD</span></span>

<span data-ttu-id="639af-338">Innehåller ett Sök vägs objekt som representerar den fullständiga sökvägen till den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="639af-338">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="639af-339">$Sender</span><span class="sxs-lookup"><span data-stu-id="639af-339">$Sender</span></span>

<span data-ttu-id="639af-340">Innehåller objektet som skapade den här händelsen.</span><span class="sxs-lookup"><span data-stu-id="639af-340">Contains the object that generated this event.</span></span> <span data-ttu-id="639af-341">Den här variabeln fylls bara i åtgärds blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="639af-341">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="639af-342">Värdet för den här variabeln finns också i egenskapen Sender för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="639af-342">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="639af-343">$ShellId</span><span class="sxs-lookup"><span data-stu-id="639af-343">$ShellId</span></span>

<span data-ttu-id="639af-344">Innehåller identifieraren för det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="639af-344">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="639af-345">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="639af-345">$StackTrace</span></span>

<span data-ttu-id="639af-346">Innehåller en stack spårning för det senaste felet.</span><span class="sxs-lookup"><span data-stu-id="639af-346">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="639af-347">$switch</span><span class="sxs-lookup"><span data-stu-id="639af-347">$switch</span></span>

<span data-ttu-id="639af-348">Innehåller uppräkna ren inte resulterande värden för en `Switch` instruktion.</span><span class="sxs-lookup"><span data-stu-id="639af-348">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="639af-349">`$switch`Variabeln finns bara medan `Switch` instruktionen körs. den tas bort när `switch` instruktionen Slutför körningen.</span><span class="sxs-lookup"><span data-stu-id="639af-349">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="639af-350">Mer information finns i [about_Switch](about_Switch.md).</span><span class="sxs-lookup"><span data-stu-id="639af-350">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="639af-351">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="639af-351">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="639af-352">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="639af-352">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="639af-353">$this</span><span class="sxs-lookup"><span data-stu-id="639af-353">$this</span></span>

<span data-ttu-id="639af-354">I ett skript block som definierar en skript egenskap eller skript metod `$this` refererar variabeln till det objekt som ska utökas.</span><span class="sxs-lookup"><span data-stu-id="639af-354">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="639af-355">I en anpassad klass `$this` refererar variabeln till själva klassobjektet som ger åtkomst till egenskaper och metoder som definierats i klassen.</span><span class="sxs-lookup"><span data-stu-id="639af-355">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="639af-356">$true</span><span class="sxs-lookup"><span data-stu-id="639af-356">$true</span></span>

<span data-ttu-id="639af-357">Innehåller **Sant**.</span><span class="sxs-lookup"><span data-stu-id="639af-357">Contains **True**.</span></span> <span data-ttu-id="639af-358">Du kan använda den här variabeln för att representera **Sant** i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="639af-358">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="639af-359">Använda uppräknare</span><span class="sxs-lookup"><span data-stu-id="639af-359">Using Enumerators</span></span>

<span data-ttu-id="639af-360">`$input` `$foreach` Variablerna, och `$switch` är alla uppräknare som används för att iterera genom de värden som bearbetas av deras inneslutna kodblock.</span><span class="sxs-lookup"><span data-stu-id="639af-360">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="639af-361">En uppräknare innehåller egenskaper och metoder som du kan använda för att fortsätta eller återställa iteration eller hämta upprepnings värden.</span><span class="sxs-lookup"><span data-stu-id="639af-361">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="639af-362">Att direkt manipulera uppräknare anses inte vara bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="639af-362">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="639af-363">I slingor, flödes kontrollens nyckelord [bryts](about_Break.md) och [Fortsätt](about_Continue.md) bör föredras.</span><span class="sxs-lookup"><span data-stu-id="639af-363">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="639af-364">I funktioner som accepterar pipeline-inflöde är det bäst att använda parametrar med **ValueFromPipeline** -eller **ValueFromPipelineByPropertyName** -attributen.</span><span class="sxs-lookup"><span data-stu-id="639af-364">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="639af-365">Mer information finns i [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="639af-365">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="639af-366">Anropa</span><span class="sxs-lookup"><span data-stu-id="639af-366">MoveNext</span></span>

<span data-ttu-id="639af-367">Metoden [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) flyttar uppräkna ren till nästa element i mängden.</span><span class="sxs-lookup"><span data-stu-id="639af-367">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="639af-368">**MoveNext** returnerar **True** om uppräkna ren lyckades, **falskt** om uppräkna ren har passerat slutet av samlingen.</span><span class="sxs-lookup"><span data-stu-id="639af-368">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="639af-369">Det **booleska** värdet som returnerade min **MoveNext** skickas till utdataströmmen.</span><span class="sxs-lookup"><span data-stu-id="639af-369">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="639af-370">Du kan ignorera utdata genom att Typecasting den `[void]` eller skicka den till [out-null](xref:Microsoft.PowerShell.Core.Out-Null).</span><span class="sxs-lookup"><span data-stu-id="639af-370">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="639af-371">Återställ</span><span class="sxs-lookup"><span data-stu-id="639af-371">Reset</span></span>

<span data-ttu-id="639af-372">Metoden [Reset](/dotnet/api/system.collections.ienumerator.reset) anger uppräkna ren till den ursprungliga positionen, som är **före** det första elementet i samlingen.</span><span class="sxs-lookup"><span data-stu-id="639af-372">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="639af-373">Aktuellt</span><span class="sxs-lookup"><span data-stu-id="639af-373">Current</span></span>

<span data-ttu-id="639af-374">Den [aktuella](/dotnet/api/system.collections.ienumerator.current) egenskapen hämtar elementet i samlingen eller pipelinen vid den aktuella positionen för uppräkna ren.</span><span class="sxs-lookup"><span data-stu-id="639af-374">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="639af-375">Den **aktuella** egenskapen fortsätter att returnera samma egenskap tills **MoveNext** anropas.</span><span class="sxs-lookup"><span data-stu-id="639af-375">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="639af-376">Exempel</span><span class="sxs-lookup"><span data-stu-id="639af-376">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="639af-377">Exempel 1: använda variabeln $input</span><span class="sxs-lookup"><span data-stu-id="639af-377">Example 1: Using the $input variable</span></span>

<span data-ttu-id="639af-378">I följande exempel `$input` rensar Access variabeln variabeln tills nästa gång process blocket körs.</span><span class="sxs-lookup"><span data-stu-id="639af-378">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="639af-379">Om du använder **Reset** -metoden återställs `$input` variabeln till det aktuella pipeline-värdet.</span><span class="sxs-lookup"><span data-stu-id="639af-379">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="639af-380">Process blocket flyttar automatiskt `$input` variabeln även om du inte har åtkomst till den.</span><span class="sxs-lookup"><span data-stu-id="639af-380">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="639af-381">Exempel 2: använda $input utanför process blocket</span><span class="sxs-lookup"><span data-stu-id="639af-381">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="639af-382">Utanför process blocket `$input` representerar variabeln alla värden som skickas i funktionen.</span><span class="sxs-lookup"><span data-stu-id="639af-382">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="639af-383">Vid åtkomst till `$input` variabeln rensas alla värden.</span><span class="sxs-lookup"><span data-stu-id="639af-383">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="639af-384">**Reset** -metoden återställer hela samlingen.</span><span class="sxs-lookup"><span data-stu-id="639af-384">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="639af-385">Den **aktuella** egenskapen fylls aldrig i.</span><span class="sxs-lookup"><span data-stu-id="639af-385">The **Current** property is never populated.</span></span>
- <span data-ttu-id="639af-386">Metoden **MoveNext** returnerar false eftersom samlingen inte kan vara avancerad.</span><span class="sxs-lookup"><span data-stu-id="639af-386">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="639af-387">Anrop av **MoveNext** rensar bort `$input` variabeln.</span><span class="sxs-lookup"><span data-stu-id="639af-387">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="639af-388">Exempel 3: använda $input. Aktuell egenskap</span><span class="sxs-lookup"><span data-stu-id="639af-388">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="639af-389">Genom att använda den **aktuella** egenskapen kan det aktuella pipeline-värdet nås flera gånger utan att använda metoden **Reset** .</span><span class="sxs-lookup"><span data-stu-id="639af-389">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="639af-390">Process blocket anropar inte metoden **MoveNext** automatiskt.</span><span class="sxs-lookup"><span data-stu-id="639af-390">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="639af-391">Den **aktuella** egenskapen kommer aldrig att fyllas i om du inte uttryckligen anropar **MoveNext**.</span><span class="sxs-lookup"><span data-stu-id="639af-391">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="639af-392">Den **aktuella** egenskapen kan nås flera gånger i process blocket utan att värdet rensas.</span><span class="sxs-lookup"><span data-stu-id="639af-392">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="639af-393">Exempel 4: använda variabeln $foreach</span><span class="sxs-lookup"><span data-stu-id="639af-393">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="639af-394">Till skillnad från `$input` variabeln `$foreach` representerar variabeln alltid alla objekt i samlingen när de nås direkt.</span><span class="sxs-lookup"><span data-stu-id="639af-394">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="639af-395">Använd den **aktuella** egenskapen för att komma åt det aktuella samlings elementet och metoderna **Reset** och **MoveNext** för att ändra dess värde.</span><span class="sxs-lookup"><span data-stu-id="639af-395">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="639af-396">Varje iteration av `foreach` slingen anropar automatiskt **MoveNext** -metoden.</span><span class="sxs-lookup"><span data-stu-id="639af-396">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="639af-397">Följande slinga körs bara två gånger.</span><span class="sxs-lookup"><span data-stu-id="639af-397">The following loop only executes twice.</span></span> <span data-ttu-id="639af-398">I den andra iterationen flyttas samlingen till det tredje elementet innan iterationen är klar.</span><span class="sxs-lookup"><span data-stu-id="639af-398">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="639af-399">Efter den andra iterationen finns det nu inga fler värden att iterera, och loopen avslutas.</span><span class="sxs-lookup"><span data-stu-id="639af-399">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="639af-400">Egenskapen **MoveNext** påverkar inte den variabel som valts för att iterera igenom samlingen ( `$Num` ).</span><span class="sxs-lookup"><span data-stu-id="639af-400">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="639af-401">Om du använder **Reset** -metoden återställs det aktuella elementet i samlingen.</span><span class="sxs-lookup"><span data-stu-id="639af-401">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="639af-402">I följande exempel upprepas de två första elementen **två gånger** eftersom **återställnings** metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="639af-402">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="639af-403">Efter de två första slingorna `if` Miss lyckas instruktionen och loopen upprepas genom alla tre elementen normalt.</span><span class="sxs-lookup"><span data-stu-id="639af-403">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="639af-404">Detta kan resultera i en oändlig loop.</span><span class="sxs-lookup"><span data-stu-id="639af-404">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="639af-405">Exempel 5: använda variabeln $switch</span><span class="sxs-lookup"><span data-stu-id="639af-405">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="639af-406">`$switch`Variabeln har exakt samma regler som `$foreach` variabeln.</span><span class="sxs-lookup"><span data-stu-id="639af-406">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="639af-407">Följande exempel visar alla koncept för uppräknare.</span><span class="sxs-lookup"><span data-stu-id="639af-407">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="639af-408">Observera att **NotEvaluated** -fallet aldrig körs, även om det inte finns någon `break` instruktion efter **MoveNext** -metoden.</span><span class="sxs-lookup"><span data-stu-id="639af-408">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="639af-409">Se även</span><span class="sxs-lookup"><span data-stu-id="639af-409">See also</span></span>

[<span data-ttu-id="639af-410">about_Functions</span><span class="sxs-lookup"><span data-stu-id="639af-410">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="639af-411">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="639af-411">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="639af-412">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="639af-412">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="639af-413">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="639af-413">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="639af-414">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="639af-414">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="639af-415">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="639af-415">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="639af-416">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="639af-416">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="639af-417">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="639af-417">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="639af-418">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="639af-418">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="639af-419">about_Variables</span><span class="sxs-lookup"><span data-stu-id="639af-419">about_Variables</span></span>](about_Variables.md)

