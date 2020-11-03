---
description: Beskriver variabler som lagrar Tillståndsinformation för PowerShell. Dessa variabler skapas och underhålls av PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: d56e844bd10dfffabb1d2cfd75bcfe113724a334
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271640"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="d0053-105">Om automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="d0053-105">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="d0053-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="d0053-106">Short description</span></span>

<span data-ttu-id="d0053-107">Beskriver variabler som lagrar Tillståndsinformation för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0053-107">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="d0053-108">Dessa variabler skapas och underhålls av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0053-108">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="d0053-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="d0053-109">Long description</span></span>

<span data-ttu-id="d0053-110">Dessa variabler anses konceptuellt vara skrivskyddade.</span><span class="sxs-lookup"><span data-stu-id="d0053-110">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="d0053-111">Även om de **kan** skrivas till **bör de inte** skrivas för bakåtkompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="d0053-111">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="d0053-112">Här är en lista över de automatiska variablerna i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d0053-112">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="d0053-113">Innehåller den sista token i den sista raden som togs emot av sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-113">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="d0053-114">$?</span><span class="sxs-lookup"><span data-stu-id="d0053-114">$?</span></span>

<span data-ttu-id="d0053-115">Innehåller körnings status för det sista kommandot.</span><span class="sxs-lookup"><span data-stu-id="d0053-115">Contains the execution status of the last command.</span></span> <span data-ttu-id="d0053-116">Det innehåller **Sant** om det sista kommandot lyckades och **falskt** om det misslyckades.</span><span class="sxs-lookup"><span data-stu-id="d0053-116">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="d0053-117">För cmdlets och avancerade funktioner som körs i flera steg i en pipeline, t. ex. i både `process` och `end` block, som anropar `this.WriteError()` eller `$PSCmdlet.WriteError()` på någon punkt, anges `$?` till **falskt** , som `this.ThrowTerminatingError()` och `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="d0053-117">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False** , as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="d0053-118">`Write-Error`Cmdleten anges alltid `$?` till **false** omedelbart efter att den körts, men är inte inställd `$?` på **false** för en funktion som anropar den:</span><span class="sxs-lookup"><span data-stu-id="d0053-118">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="d0053-119">För det senare ändamålet `$PSCmdlet.WriteError()` ska du i stället använda.</span><span class="sxs-lookup"><span data-stu-id="d0053-119">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="d0053-120">För inbyggda kommandon (körbara filer) `$?` anges till **Sant** när `$LASTEXITCODE` är 0 och anges till **falskt** om `$LASTEXITCODE` är ett annat värde.</span><span class="sxs-lookup"><span data-stu-id="d0053-120">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="d0053-121">Fram till PowerShell 7, som innehåller en instruktion inom parentes `(...)` , återställs inte syntaxen för under uttryck `$(...)` eller mat ris uttryck `@(...)` `$?` till **True** , så att `(Write-Error)` visas `$?` som **Sant**.</span><span class="sxs-lookup"><span data-stu-id="d0053-121">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True** , so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="d0053-122">Detta har ändrats i PowerShell 7, så det `$?` visar alltid det faktiska resultatet för det sista kommandot som körs i dessa uttryck.</span><span class="sxs-lookup"><span data-stu-id="d0053-122">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="d0053-123">Innehåller den första token i den sista raden som togs emot av sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-123">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="d0053-124">$_</span><span class="sxs-lookup"><span data-stu-id="d0053-124">$_</span></span>

<span data-ttu-id="d0053-125">Samma som `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="d0053-125">Same as `$PSItem`.</span></span> <span data-ttu-id="d0053-126">Innehåller det aktuella objektet i pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="d0053-126">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="d0053-127">Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="d0053-127">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="d0053-128">$args</span><span class="sxs-lookup"><span data-stu-id="d0053-128">$args</span></span>

<span data-ttu-id="d0053-129">Innehåller en matris med värden för parametrar som inte har deklarerats som skickas till en funktion, ett skript eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="d0053-129">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="d0053-130">När du skapar en funktion kan du deklarera parametrarna med hjälp av `param` nyckelordet eller genom att lägga till en kommaavgränsad lista med parametrar inom parentes efter funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="d0053-130">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="d0053-131">I en händelse åtgärd `$Args` innehåller variabeln objekt som representerar händelse argumenten för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="d0053-131">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="d0053-132">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="d0053-132">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="d0053-133">Värdet för den här variabeln finns också i egenskapen **SourceArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="d0053-133">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="d0053-134">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="d0053-134">$ConsoleFileName</span></span>

<span data-ttu-id="d0053-135">Innehåller sökvägen till konsol filen ( `.psc1` ) som senast användes i sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-135">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="d0053-136">Den här variabeln fylls när du startar PowerShell med parametern **PSConsoleFile** eller när du använder `Export-Console` cmdleten för att exportera snapin-namn till en konsol fil.</span><span class="sxs-lookup"><span data-stu-id="d0053-136">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="d0053-137">När du använder `Export-Console` cmdleten utan parametrar uppdaterar den automatiskt konsol filen som användes senast i sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-137">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="d0053-138">Du kan använda den här automatiska variabeln för att avgöra vilken fil som ska uppdateras.</span><span class="sxs-lookup"><span data-stu-id="d0053-138">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="d0053-139">$Error</span><span class="sxs-lookup"><span data-stu-id="d0053-139">$Error</span></span>

<span data-ttu-id="d0053-140">Innehåller en matris med fel objekt som representerar de senaste felen.</span><span class="sxs-lookup"><span data-stu-id="d0053-140">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="d0053-141">Det senaste felet är det första fel objektet i matrisen `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="d0053-141">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="d0053-142">Om du vill förhindra att ett fel läggs till i `$Error` matrisen använder du parametern **ErrorAction** common med värdet **Ignore**.</span><span class="sxs-lookup"><span data-stu-id="d0053-142">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="d0053-143">Mer information finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-143">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="d0053-144">$Event</span><span class="sxs-lookup"><span data-stu-id="d0053-144">$Event</span></span>

<span data-ttu-id="d0053-145">Innehåller ett **PSEventArgs** -objekt som representerar den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="d0053-145">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="d0053-146">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando, till exempel `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="d0053-146">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="d0053-147">Värdet för den här variabeln är samma objekt som `Get-Event` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="d0053-147">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="d0053-148">Därför kan du använda egenskaperna för `Event` variabeln, till exempel `$Event.TimeGenerated` i ett- `Action` skript block.</span><span class="sxs-lookup"><span data-stu-id="d0053-148">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="d0053-149">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="d0053-149">$EventArgs</span></span>

<span data-ttu-id="d0053-150">Innehåller ett objekt som representerar det första händelse argumentet som härleds från **EventArgs** för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="d0053-150">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="d0053-151">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="d0053-151">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="d0053-152">Värdet för den här variabeln finns också i egenskapen **SourceEventArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="d0053-152">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="d0053-153">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="d0053-153">$EventSubscriber</span></span>

<span data-ttu-id="d0053-154">Innehåller ett **PSEventSubscriber** -objekt som representerar händelse prenumeranten för den händelse som bearbetas.</span><span class="sxs-lookup"><span data-stu-id="d0053-154">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="d0053-155">Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="d0053-155">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="d0053-156">Värdet för den här variabeln är samma objekt som `Get-EventSubscriber` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="d0053-156">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="d0053-157">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="d0053-157">$ExecutionContext</span></span>

<span data-ttu-id="d0053-158">Innehåller ett **EngineIntrinsics** -objekt som representerar körnings kontexten för PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="d0053-158">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="d0053-159">Du kan använda den här variabeln för att hitta de körnings objekt som är tillgängliga för-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d0053-159">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="d0053-160">$false</span><span class="sxs-lookup"><span data-stu-id="d0053-160">$false</span></span>

<span data-ttu-id="d0053-161">Innehåller **falskt**.</span><span class="sxs-lookup"><span data-stu-id="d0053-161">Contains **False**.</span></span> <span data-ttu-id="d0053-162">Du kan använda den här variabeln för att representera **falskt** i kommandon och skript i stället för att använda strängen "false".</span><span class="sxs-lookup"><span data-stu-id="d0053-162">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="d0053-163">Strängen kan tolkas som **Sant** om den konverteras till en sträng som inte är tom eller till ett heltal som inte är noll.</span><span class="sxs-lookup"><span data-stu-id="d0053-163">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="d0053-164">$foreach</span><span class="sxs-lookup"><span data-stu-id="d0053-164">$foreach</span></span>

<span data-ttu-id="d0053-165">Innehåller uppräkna ren (inte de resulterande värdena) för en [förgrunds](about_ForEach.md) slinga.</span><span class="sxs-lookup"><span data-stu-id="d0053-165">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="d0053-166">`$ForEach`Variabeln finns bara medan `ForEach` loopen körs. den tas bort när loopen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="d0053-166">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="d0053-167">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="d0053-167">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="d0053-168">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="d0053-168">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="d0053-169">$HOME</span><span class="sxs-lookup"><span data-stu-id="d0053-169">$HOME</span></span>

<span data-ttu-id="d0053-170">Innehåller den fullständiga sökvägen till användarens Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="d0053-170">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="d0053-171">Den här variabeln motsvarar `"$env:homedrive$env:homepath"` Windows-miljövariablerna, vanligt vis `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="d0053-171">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="d0053-172">$Host</span><span class="sxs-lookup"><span data-stu-id="d0053-172">$Host</span></span>

<span data-ttu-id="d0053-173">Innehåller ett objekt som representerar det aktuella värd programmet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d0053-173">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="d0053-174">Du kan använda den här variabeln för att representera den aktuella värden i kommandon eller för att visa eller ändra egenskaperna för värden, till exempel `$Host.version` eller `$Host.CurrentCulture` , eller `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="d0053-174">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="d0053-175">$input</span><span class="sxs-lookup"><span data-stu-id="d0053-175">$input</span></span>

<span data-ttu-id="d0053-176">Innehåller en uppräknare som räknar upp alla indatatyper som skickas till en funktion.</span><span class="sxs-lookup"><span data-stu-id="d0053-176">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="d0053-177">`$input`Variabeln är endast tillgänglig för funktioner och skript block (som är ej namede funktioner).</span><span class="sxs-lookup"><span data-stu-id="d0053-177">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="d0053-178">I en funktion utan ett `Begin` , `Process` eller- `End` block, `$input` räknar variabeln upp indatamängden för funktionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-178">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="d0053-179">I `Begin` blocket `$input` innehåller variabeln inga data.</span><span class="sxs-lookup"><span data-stu-id="d0053-179">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="d0053-180">I `Process` blocket `$input` innehåller variabeln det objekt som för närvarande finns i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="d0053-180">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="d0053-181">I `End` blocket `$input` räknar variabeln upp indatamängden för funktionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-181">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d0053-182">Du kan inte använda `$input` variabeln i både process blocket och slut blocket i samma funktion eller i ett skript block.</span><span class="sxs-lookup"><span data-stu-id="d0053-182">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="d0053-183">Eftersom `$input` är en uppräknare kan åtkomst till någon av dess egenskaper `$input` inte längre vara tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="d0053-183">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="d0053-184">Du kan lagra `$input` i en annan variabel om du vill återanvända `$input` egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="d0053-184">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="d0053-185">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="d0053-185">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="d0053-186">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="d0053-186">For more information, see [Using Enumerators](#using-enumerators).</span></span>


### <a name="lastexitcode"></a><span data-ttu-id="d0053-187">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="d0053-187">$LastExitCode</span></span>

<span data-ttu-id="d0053-188">Innehåller avslutnings koden för det senaste Windows-baserade program som kördes.</span><span class="sxs-lookup"><span data-stu-id="d0053-188">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="d0053-189">$Matches</span><span class="sxs-lookup"><span data-stu-id="d0053-189">$Matches</span></span>

<span data-ttu-id="d0053-190">`Matches`Variabeln fungerar med `-match` `-notmatch` operatorerna och.</span><span class="sxs-lookup"><span data-stu-id="d0053-190">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="d0053-191">När du skickar skalära indatatyper till `-match` `-notmatch` operatorn eller, och antingen identifierar en matchning, returnerar de ett booleskt värde och fyller den `$Matches` automatiska variabeln med en hash-tabell för alla sträng värden som matchades.</span><span class="sxs-lookup"><span data-stu-id="d0053-191">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="d0053-192">`$Matches`Hash-tabellen kan också fyllas i med insamlingar när du använder reguljära uttryck med `-match` operatorn.</span><span class="sxs-lookup"><span data-stu-id="d0053-192">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="d0053-193">Mer information om `-match` operatorn finns i [about_Comparison_Operators](about_comparison_operators.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-193">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="d0053-194">Mer information om reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-194">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="d0053-195">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="d0053-195">$MyInvocation</span></span>

<span data-ttu-id="d0053-196">Innehåller information om det aktuella kommandot, till exempel namn, parametrar, parameter värden och information om hur kommandot startades, anropades eller anropades, till exempel namnet på det skript som anropade det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="d0053-196">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="d0053-197">`$MyInvocation` är endast ifyllt för skript, funktions-och skript block.</span><span class="sxs-lookup"><span data-stu-id="d0053-197">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="d0053-198">Du kan använda informationen i objektet **system. Management. Automation. InvocationInfo** som `$MyInvocation` returneras i det aktuella skriptet, t. ex. sökvägen och fil namnet för skriptet ( `$MyInvocation.MyCommand.Path` ) eller namnet på en funktion ( `$MyInvocation.MyCommand.Name` ) för att identifiera det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="d0053-198">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="d0053-199">Detta är särskilt användbart för att hitta namnet på det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="d0053-199">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="d0053-200">Från och med PowerShell 3,0, `MyInvocation` har följande nya egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d0053-200">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="d0053-201">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d0053-201">Property</span></span>      | <span data-ttu-id="d0053-202">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d0053-202">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="d0053-203">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="d0053-203">**PSScriptRoot**</span></span>  | <span data-ttu-id="d0053-204">Innehåller den fullständiga sökvägen till skriptet som anropades</span><span class="sxs-lookup"><span data-stu-id="d0053-204">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="d0053-205">det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="d0053-205">the current command.</span></span> <span data-ttu-id="d0053-206">Värdet för den här egenskapen är</span><span class="sxs-lookup"><span data-stu-id="d0053-206">The value of this property is</span></span>  |
|               | <span data-ttu-id="d0053-207">fylls bara i när anroparen är ett skript.</span><span class="sxs-lookup"><span data-stu-id="d0053-207">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="d0053-208">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="d0053-208">**PSCommandPath**</span></span> | <span data-ttu-id="d0053-209">Innehåller den fullständiga sökvägen till och fil namnet på skriptet</span><span class="sxs-lookup"><span data-stu-id="d0053-209">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="d0053-210">som anropade det aktuella kommandot.</span><span class="sxs-lookup"><span data-stu-id="d0053-210">that invoked the current command.</span></span> <span data-ttu-id="d0053-211">Värdet för det här</span><span class="sxs-lookup"><span data-stu-id="d0053-211">The value of this</span></span> |
|               | <span data-ttu-id="d0053-212">Egenskapen fylls bara när anroparen är en</span><span class="sxs-lookup"><span data-stu-id="d0053-212">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="d0053-213">över.</span><span class="sxs-lookup"><span data-stu-id="d0053-213">script.</span></span>                                             |

<span data-ttu-id="d0053-214">Till skillnad från `$PSScriptRoot` de `$PSCommandPath` automatiska variablerna innehåller egenskaperna **PSScriptRoot** och **PSCommandPath** för den `$MyInvocation` automatiska variabeln information om anroparen eller anropet till skriptet, inte det aktuella skriptet.</span><span class="sxs-lookup"><span data-stu-id="d0053-214">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="d0053-215">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="d0053-215">$NestedPromptLevel</span></span>

<span data-ttu-id="d0053-216">Innehåller den aktuella LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="d0053-216">Contains the current prompt level.</span></span> <span data-ttu-id="d0053-217">Värdet 0 anger den ursprungliga LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="d0053-217">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="d0053-218">Värdet ökar när du anger en kapslad nivå och när du avslutar det.</span><span class="sxs-lookup"><span data-stu-id="d0053-218">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="d0053-219">PowerShell visar till exempel en kapslad kommando tolk när du använder- `$Host.EnterNestedPrompt` metoden.</span><span class="sxs-lookup"><span data-stu-id="d0053-219">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="d0053-220">PowerShell visar också en kapslad kommando tolk när du når en Bryt punkt i PowerShell-felsökaren.</span><span class="sxs-lookup"><span data-stu-id="d0053-220">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="d0053-221">När du anger en kapslad prompt pausar PowerShell det aktuella kommandot, sparar körnings kontexten och ökar värdet för `$NestedPromptLevel` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d0053-221">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="d0053-222">Om du vill skapa ytterligare kapslade kommando prompter (upp till 128 nivåer) eller återgå till den ursprungliga kommando tolken, slutför du kommandot eller Skriv `exit` .</span><span class="sxs-lookup"><span data-stu-id="d0053-222">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="d0053-223">`$NestedPromptLevel`Variabeln hjälper dig att spåra LED text nivån.</span><span class="sxs-lookup"><span data-stu-id="d0053-223">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="d0053-224">Du kan skapa en alternativ kommando tolk för PowerShell som innehåller det här värdet så att det alltid är synligt.</span><span class="sxs-lookup"><span data-stu-id="d0053-224">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="d0053-225">$null</span><span class="sxs-lookup"><span data-stu-id="d0053-225">$null</span></span>

<span data-ttu-id="d0053-226">`$null` är en automatisk variabel som innehåller ett **Null** -värde eller ett tomt värde.</span><span class="sxs-lookup"><span data-stu-id="d0053-226">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="d0053-227">Du kan använda den här variabeln för att representera ett frånvarande eller odefinierat värde i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="d0053-227">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="d0053-228">PowerShell behandlar `$null` som ett objekt med ett värde, det vill säga som en explicit plats hållare, så att du kan använda `$null` för att representera ett tomt värde i en serie med värden.</span><span class="sxs-lookup"><span data-stu-id="d0053-228">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="d0053-229">När `$null` ingår i en samling räknas den till exempel som ett av objekten.</span><span class="sxs-lookup"><span data-stu-id="d0053-229">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="d0053-230">Om du rör `$null` variabeln till `ForEach-Object` cmdleten genererar den ett värde för `$null` , precis som för de andra objekten</span><span class="sxs-lookup"><span data-stu-id="d0053-230">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="d0053-231">Det innebär att du inte kan använda `$null` till att betyda ett **parameter värde**.</span><span class="sxs-lookup"><span data-stu-id="d0053-231">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="d0053-232">Ett parameter värde för `$null` åsidosätter standard parameter värde.</span><span class="sxs-lookup"><span data-stu-id="d0053-232">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="d0053-233">Men eftersom PowerShell behandlar `$null` variabeln som en plats hållare kan du använda den i skript som följande, som inte fungerar om `$null` ignorerades.</span><span class="sxs-lookup"><span data-stu-id="d0053-233">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

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

### <a name="pid"></a><span data-ttu-id="d0053-234">$PID</span><span class="sxs-lookup"><span data-stu-id="d0053-234">$PID</span></span>

<span data-ttu-id="d0053-235">Innehåller process identifieraren (PID) för processen som är värd för den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-235">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="d0053-236">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="d0053-236">$PROFILE</span></span>

<span data-ttu-id="d0053-237">Innehåller den fullständiga sökvägen till PowerShell-profilen för den aktuella användaren och det aktuella värd programmet.</span><span class="sxs-lookup"><span data-stu-id="d0053-237">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="d0053-238">Du kan använda den här variabeln för att representera profilen i kommandon.</span><span class="sxs-lookup"><span data-stu-id="d0053-238">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="d0053-239">Du kan till exempel använda den i ett kommando för att avgöra om en profil har skapats:</span><span class="sxs-lookup"><span data-stu-id="d0053-239">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="d0053-240">Eller så kan du använda den i ett kommando för att skapa en profil:</span><span class="sxs-lookup"><span data-stu-id="d0053-240">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="d0053-241">Du kan använda den i ett kommando för att öppna profilen i **notepad.exe** :</span><span class="sxs-lookup"><span data-stu-id="d0053-241">You can use it in a command to open the profile in **notepad.exe** :</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="d0053-242">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="d0053-242">$PSBoundParameters</span></span>

<span data-ttu-id="d0053-243">Innehåller en lista över parametrar som skickas till ett skript eller en funktion och deras aktuella värden.</span><span class="sxs-lookup"><span data-stu-id="d0053-243">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="d0053-244">Den här variabeln har ett värde endast i ett omfång där parametrar deklareras, till exempel ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="d0053-244">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="d0053-245">Du kan använda den för att visa eller ändra aktuella värden för parametrar eller skicka parameter värden till ett annat skript eller en annan funktion.</span><span class="sxs-lookup"><span data-stu-id="d0053-245">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="d0053-246">I det här exemplet skickar funktionen **TEST2** `$PSBoundParameters` till **test1** -funktionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-246">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="d0053-247">`$PSBoundParameters`Visas i formatet för **nyckel** och **värde**.</span><span class="sxs-lookup"><span data-stu-id="d0053-247">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

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

### <a name="pscmdlet"></a><span data-ttu-id="d0053-248">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="d0053-248">$PSCmdlet</span></span>

<span data-ttu-id="d0053-249">Innehåller ett objekt som representerar den cmdlet eller avancerad funktion som körs.</span><span class="sxs-lookup"><span data-stu-id="d0053-249">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="d0053-250">Du kan använda egenskaperna och metoderna för objektet i din cmdlet eller funktions kod för att svara på användnings villkoren.</span><span class="sxs-lookup"><span data-stu-id="d0053-250">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="d0053-251">Till exempel innehåller egenskapen **ParameterSetName** namnet på den parameter uppsättning som används och **ShouldProcess** -metoden lägger till **whatIf** -och **Confirm** -parametrarna i cmdleten dynamiskt.</span><span class="sxs-lookup"><span data-stu-id="d0053-251">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="d0053-252">Mer information om den `$PSCmdlet` automatiska variabeln finns i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) och [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-252">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="d0053-253">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="d0053-253">$PSCommandPath</span></span>

<span data-ttu-id="d0053-254">Innehåller den fullständiga sökvägen och fil namnet för det skript som körs.</span><span class="sxs-lookup"><span data-stu-id="d0053-254">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="d0053-255">Den här variabeln är giltig i alla skript.</span><span class="sxs-lookup"><span data-stu-id="d0053-255">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="d0053-256">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="d0053-256">$PSCulture</span></span>

<span data-ttu-id="d0053-257">Innehåller namnet på kulturen som används i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="d0053-257">Contains the name of the culture currently in use in the operating system.</span></span> <span data-ttu-id="d0053-258">Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum och lagras i ett **system. globalisering. CultureInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d0053-258">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="d0053-259">Används `Get-Culture` för att Visa datorns kultur.</span><span class="sxs-lookup"><span data-stu-id="d0053-259">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="d0053-260">`$PSCulture` innehåller värde för egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="d0053-260">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="d0053-261">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="d0053-261">$PSDebugContext</span></span>

<span data-ttu-id="d0053-262">Vid fel sökning innehåller den här variabeln information om fel söknings miljön.</span><span class="sxs-lookup"><span data-stu-id="d0053-262">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="d0053-263">Annars innehåller den ett **Null** -värde.</span><span class="sxs-lookup"><span data-stu-id="d0053-263">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="d0053-264">Därför kan du använda den för att ange om fel söknings programmet har kontroll.</span><span class="sxs-lookup"><span data-stu-id="d0053-264">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="d0053-265">När den har fyllts i innehåller den ett **PsDebugContext** -objekt som har **Bryt punkter** och **InvocationInfo** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="d0053-265">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="d0053-266">Egenskapen **InvocationInfo** har flera användbara egenskaper, inklusive egenskapen **location** .</span><span class="sxs-lookup"><span data-stu-id="d0053-266">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="d0053-267">Egenskapen **location** anger sökvägen till skriptet som felsöks.</span><span class="sxs-lookup"><span data-stu-id="d0053-267">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="d0053-268">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="d0053-268">$PSHOME</span></span>

<span data-ttu-id="d0053-269">Innehåller den fullständiga sökvägen till installations katalogen för PowerShell, vanligt vis `$env:windir\System32\PowerShell\v1.0` i Windows-system.</span><span class="sxs-lookup"><span data-stu-id="d0053-269">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="d0053-270">Du kan använda den här variabeln i sökvägar för PowerShell-filer.</span><span class="sxs-lookup"><span data-stu-id="d0053-270">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="d0053-271">Till exempel söker följande kommando efter ordet **variabel** i de konceptuella hjälp avsnitten:</span><span class="sxs-lookup"><span data-stu-id="d0053-271">For example, the following command searches the conceptual Help topics for the word **variable** :</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="d0053-272">$PSItem</span><span class="sxs-lookup"><span data-stu-id="d0053-272">$PSItem</span></span>

<span data-ttu-id="d0053-273">Samma som `$_` .</span><span class="sxs-lookup"><span data-stu-id="d0053-273">Same as `$_`.</span></span> <span data-ttu-id="d0053-274">Innehåller det aktuella objektet i pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="d0053-274">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="d0053-275">Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="d0053-275">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="d0053-276">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="d0053-276">$PSScriptRoot</span></span>

<span data-ttu-id="d0053-277">Innehåller den katalog som ett skript körs från.</span><span class="sxs-lookup"><span data-stu-id="d0053-277">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="d0053-278">I PowerShell 2,0 är den här variabeln endast giltig i script modules ( `.psm1` ).</span><span class="sxs-lookup"><span data-stu-id="d0053-278">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="d0053-279">Från och med PowerShell 3,0 är det giltigt i alla skript.</span><span class="sxs-lookup"><span data-stu-id="d0053-279">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="d0053-280">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="d0053-280">$PSSenderInfo</span></span>

<span data-ttu-id="d0053-281">Innehåller information om den användare som startade PSSession, inklusive användar identitet och tidszon på den ursprungliga datorn.</span><span class="sxs-lookup"><span data-stu-id="d0053-281">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="d0053-282">Den här variabeln är endast tillgänglig i PSSessions.</span><span class="sxs-lookup"><span data-stu-id="d0053-282">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="d0053-283">`$PSSenderInfo`Variabeln innehåller en egenskap som kan konfigureras av användaren, **ApplicationArguments** , som standard bara innehåller `$PSVersionTable` från den ursprungliga sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-283">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments** , that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="d0053-284">Om du vill lägga till data i egenskapen **ApplicationArguments** använder du parametern **ApplicationArguments** för `New-PSSessionOption` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d0053-284">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="d0053-285">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="d0053-285">$PSUICulture</span></span>

<span data-ttu-id="d0053-286">Innehåller namnet på användar gränssnitts kulturen (UI) som används i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="d0053-286">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="d0053-287">ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.</span><span class="sxs-lookup"><span data-stu-id="d0053-287">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="d0053-288">Detta är värdet för systemets **system.Globalization.CultureInfo.CurrentUICulture.name** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="d0053-288">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="d0053-289">Använd cmdleten för att hämta objektet **system. globalisering. CultureInfo** för systemet `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="d0053-289">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="d0053-290">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="d0053-290">$PSVersionTable</span></span>

<span data-ttu-id="d0053-291">Innehåller en skrivskyddad hash-tabell som visar information om den version av PowerShell som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-291">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="d0053-292">Tabellen innehåller följande objekt:</span><span class="sxs-lookup"><span data-stu-id="d0053-292">The table includes the following items:</span></span>

| <span data-ttu-id="d0053-293">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d0053-293">Property</span></span>                  | <span data-ttu-id="d0053-294">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d0053-294">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="d0053-295">**BuildVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-295">**BuildVersion**</span></span>          | <span data-ttu-id="d0053-296">Versions numret för den aktuella versionen</span><span class="sxs-lookup"><span data-stu-id="d0053-296">The build number of the current version</span></span>       |
| <span data-ttu-id="d0053-297">**CLRVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-297">**CLRVersion**</span></span>            | <span data-ttu-id="d0053-298">Versionen av Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="d0053-298">The version of the common language runtime</span></span>    |
|                           | <span data-ttu-id="d0053-299">CLR</span><span class="sxs-lookup"><span data-stu-id="d0053-299">(CLR)</span></span>                                         |
| <span data-ttu-id="d0053-300">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="d0053-300">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="d0053-301">Versioner av PowerShell som är kompatibla</span><span class="sxs-lookup"><span data-stu-id="d0053-301">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="d0053-302">med den aktuella versionen</span><span class="sxs-lookup"><span data-stu-id="d0053-302">with the current version</span></span>                      |
| <span data-ttu-id="d0053-303">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="d0053-303">**PSEdition**</span></span>             | <span data-ttu-id="d0053-304">Den här egenskapen har värdet "Desktop", för</span><span class="sxs-lookup"><span data-stu-id="d0053-304">This property has the value of 'Desktop', for</span></span> |
|                           | <span data-ttu-id="d0053-305">Windows Server-och Windows-klient versioner.</span><span class="sxs-lookup"><span data-stu-id="d0053-305">Windows Server and Windows client versions.</span></span>   |
|                           | <span data-ttu-id="d0053-306">Den här egenskapen har värdet "Core" för</span><span class="sxs-lookup"><span data-stu-id="d0053-306">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="d0053-307">PowerShell som körs under Nano Server eller</span><span class="sxs-lookup"><span data-stu-id="d0053-307">PowerShell running under Nano Server or</span></span>       |
|                           | <span data-ttu-id="d0053-308">Windows IOT.</span><span class="sxs-lookup"><span data-stu-id="d0053-308">Windows IOT.</span></span>                                  |
| <span data-ttu-id="d0053-309">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-309">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="d0053-310">Versionen av PowerShell-fjärrservern</span><span class="sxs-lookup"><span data-stu-id="d0053-310">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="d0053-311">hanterings protokoll.</span><span class="sxs-lookup"><span data-stu-id="d0053-311">management protocol.</span></span>                          |
| <span data-ttu-id="d0053-312">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-312">**PSVersion**</span></span>             | <span data-ttu-id="d0053-313">PowerShell-versions numret</span><span class="sxs-lookup"><span data-stu-id="d0053-313">The PowerShell version number</span></span>                 |
| <span data-ttu-id="d0053-314">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-314">**SerializationVersion**</span></span>  | <span data-ttu-id="d0053-315">Versionen av serialiserings metoden</span><span class="sxs-lookup"><span data-stu-id="d0053-315">The version of the serialization method</span></span>       |
| <span data-ttu-id="d0053-316">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="d0053-316">**WSManStackVersion**</span></span>     | <span data-ttu-id="d0053-317">WS-Management stackens versions nummer</span><span class="sxs-lookup"><span data-stu-id="d0053-317">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="d0053-318">$PWD</span><span class="sxs-lookup"><span data-stu-id="d0053-318">$PWD</span></span>

<span data-ttu-id="d0053-319">Innehåller ett Sök vägs objekt som representerar den fullständiga sökvägen till den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="d0053-319">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="d0053-320">$Sender</span><span class="sxs-lookup"><span data-stu-id="d0053-320">$Sender</span></span>

<span data-ttu-id="d0053-321">Innehåller objektet som skapade den här händelsen.</span><span class="sxs-lookup"><span data-stu-id="d0053-321">Contains the object that generated this event.</span></span> <span data-ttu-id="d0053-322">Den här variabeln fylls bara i åtgärds blocket för ett händelse registrerings kommando.</span><span class="sxs-lookup"><span data-stu-id="d0053-322">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="d0053-323">Värdet för den här variabeln finns också i egenskapen Sender för **PSEventArgs** -objektet som `Get-Event` returnerar.</span><span class="sxs-lookup"><span data-stu-id="d0053-323">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="d0053-324">$ShellId</span><span class="sxs-lookup"><span data-stu-id="d0053-324">$ShellId</span></span>

<span data-ttu-id="d0053-325">Innehåller identifieraren för det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d0053-325">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="d0053-326">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="d0053-326">$StackTrace</span></span>

<span data-ttu-id="d0053-327">Innehåller en stack spårning för det senaste felet.</span><span class="sxs-lookup"><span data-stu-id="d0053-327">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="d0053-328">$switch</span><span class="sxs-lookup"><span data-stu-id="d0053-328">$switch</span></span>

<span data-ttu-id="d0053-329">Innehåller uppräkna ren inte resulterande värden för en `Switch` instruktion.</span><span class="sxs-lookup"><span data-stu-id="d0053-329">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="d0053-330">`$switch`Variabeln finns bara medan `Switch` instruktionen körs. den tas bort när `switch` instruktionen Slutför körningen.</span><span class="sxs-lookup"><span data-stu-id="d0053-330">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="d0053-331">Mer information finns i [about_Switch](about_Switch.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-331">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="d0053-332">Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen.</span><span class="sxs-lookup"><span data-stu-id="d0053-332">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="d0053-333">Mer information finns i [använda uppräknare](#using-enumerators).</span><span class="sxs-lookup"><span data-stu-id="d0053-333">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="d0053-334">$this</span><span class="sxs-lookup"><span data-stu-id="d0053-334">$this</span></span>

<span data-ttu-id="d0053-335">I ett skript block som definierar en skript egenskap eller skript metod `$this` refererar variabeln till det objekt som ska utökas.</span><span class="sxs-lookup"><span data-stu-id="d0053-335">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="d0053-336">I en anpassad klass `$this` refererar variabeln till själva klassobjektet som ger åtkomst till egenskaper och metoder som definierats i klassen.</span><span class="sxs-lookup"><span data-stu-id="d0053-336">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="d0053-337">$true</span><span class="sxs-lookup"><span data-stu-id="d0053-337">$true</span></span>

<span data-ttu-id="d0053-338">Innehåller **Sant**.</span><span class="sxs-lookup"><span data-stu-id="d0053-338">Contains **True**.</span></span> <span data-ttu-id="d0053-339">Du kan använda den här variabeln för att representera **Sant** i kommandon och skript.</span><span class="sxs-lookup"><span data-stu-id="d0053-339">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="d0053-340">Använda uppräknare</span><span class="sxs-lookup"><span data-stu-id="d0053-340">Using Enumerators</span></span>

<span data-ttu-id="d0053-341">`$input` `$foreach` Variablerna, och `$switch` är alla uppräknare som används för att iterera genom de värden som bearbetas av deras inneslutna kodblock.</span><span class="sxs-lookup"><span data-stu-id="d0053-341">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="d0053-342">En uppräknare innehåller egenskaper och metoder som du kan använda för att fortsätta eller återställa iteration eller hämta upprepnings värden.</span><span class="sxs-lookup"><span data-stu-id="d0053-342">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="d0053-343">Att direkt manipulera uppräknare anses inte vara bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="d0053-343">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="d0053-344">I slingor, flödes kontrollens nyckelord [bryts](about_Break.md) och [Fortsätt](about_Continue.md) bör föredras.</span><span class="sxs-lookup"><span data-stu-id="d0053-344">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="d0053-345">I funktioner som accepterar pipeline-inflöde är det bäst att använda parametrar med **ValueFromPipeline** -eller **ValueFromPipelineByPropertyName** -attributen.</span><span class="sxs-lookup"><span data-stu-id="d0053-345">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="d0053-346">Mer information finns i [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d0053-346">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="d0053-347">Anropa</span><span class="sxs-lookup"><span data-stu-id="d0053-347">MoveNext</span></span>

<span data-ttu-id="d0053-348">Metoden [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) flyttar uppräkna ren till nästa element i mängden.</span><span class="sxs-lookup"><span data-stu-id="d0053-348">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="d0053-349">**MoveNext** returnerar **True** om uppräkna ren lyckades, **falskt** om uppräkna ren har passerat slutet av samlingen.</span><span class="sxs-lookup"><span data-stu-id="d0053-349">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="d0053-350">Det **booleska** värdet som returnerade min **MoveNext** skickas till utdataströmmen.</span><span class="sxs-lookup"><span data-stu-id="d0053-350">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="d0053-351">Du kan ignorera utdata genom att Typecasting den `[void]` eller skicka den till [out-null](xref:Microsoft.PowerShell.Core.Out-Null).</span><span class="sxs-lookup"><span data-stu-id="d0053-351">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="d0053-352">Återställ</span><span class="sxs-lookup"><span data-stu-id="d0053-352">Reset</span></span>

<span data-ttu-id="d0053-353">Metoden [Reset](/dotnet/api/system.collections.ienumerator.reset) anger uppräkna ren till den ursprungliga positionen, som är **före** det första elementet i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d0053-353">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="d0053-354">Aktuellt</span><span class="sxs-lookup"><span data-stu-id="d0053-354">Current</span></span>

<span data-ttu-id="d0053-355">Den [aktuella](/dotnet/api/system.collections.ienumerator.current) egenskapen hämtar elementet i samlingen eller pipelinen vid den aktuella positionen för uppräkna ren.</span><span class="sxs-lookup"><span data-stu-id="d0053-355">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="d0053-356">Den **aktuella** egenskapen fortsätter att returnera samma egenskap tills **MoveNext** anropas.</span><span class="sxs-lookup"><span data-stu-id="d0053-356">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="d0053-357">Exempel</span><span class="sxs-lookup"><span data-stu-id="d0053-357">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="d0053-358">Exempel 1: använda variabeln $input</span><span class="sxs-lookup"><span data-stu-id="d0053-358">Example 1: Using the $input variable</span></span>

<span data-ttu-id="d0053-359">I följande exempel `$input` rensar Access variabeln variabeln tills nästa gång process blocket körs.</span><span class="sxs-lookup"><span data-stu-id="d0053-359">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="d0053-360">Om du använder **Reset** -metoden återställs `$input` variabeln till det aktuella pipeline-värdet.</span><span class="sxs-lookup"><span data-stu-id="d0053-360">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

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

<span data-ttu-id="d0053-361">Process blocket flyttar automatiskt `$input` variabeln även om du inte har åtkomst till den.</span><span class="sxs-lookup"><span data-stu-id="d0053-361">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

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

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="d0053-362">Exempel 2: använda $input utanför process blocket</span><span class="sxs-lookup"><span data-stu-id="d0053-362">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="d0053-363">Utanför process blocket `$input` representerar variabeln alla värden som skickas i funktionen.</span><span class="sxs-lookup"><span data-stu-id="d0053-363">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="d0053-364">Vid åtkomst till `$input` variabeln rensas alla värden.</span><span class="sxs-lookup"><span data-stu-id="d0053-364">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="d0053-365">**Reset** -metoden återställer hela samlingen.</span><span class="sxs-lookup"><span data-stu-id="d0053-365">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="d0053-366">Den **aktuella** egenskapen fylls aldrig i.</span><span class="sxs-lookup"><span data-stu-id="d0053-366">The **Current** property is never populated.</span></span>
- <span data-ttu-id="d0053-367">Metoden **MoveNext** returnerar false eftersom samlingen inte kan vara avancerad.</span><span class="sxs-lookup"><span data-stu-id="d0053-367">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="d0053-368">Anrop av **MoveNext** rensar bort `$input` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d0053-368">Calling **MoveNext** clears out the `$input` variable.</span></span>

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

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="d0053-369">Exempel 3: använda $input. Aktuell egenskap</span><span class="sxs-lookup"><span data-stu-id="d0053-369">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="d0053-370">Genom att använda den **aktuella** egenskapen kan det aktuella pipeline-värdet nås flera gånger utan att använda metoden **Reset** .</span><span class="sxs-lookup"><span data-stu-id="d0053-370">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="d0053-371">Process blocket anropar inte metoden **MoveNext** automatiskt.</span><span class="sxs-lookup"><span data-stu-id="d0053-371">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="d0053-372">Den **aktuella** egenskapen kommer aldrig att fyllas i om du inte uttryckligen anropar **MoveNext**.</span><span class="sxs-lookup"><span data-stu-id="d0053-372">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="d0053-373">Den **aktuella** egenskapen kan nås flera gånger i process blocket utan att värdet rensas.</span><span class="sxs-lookup"><span data-stu-id="d0053-373">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

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

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="d0053-374">Exempel 4: använda variabeln $foreach</span><span class="sxs-lookup"><span data-stu-id="d0053-374">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="d0053-375">Till skillnad från `$input` variabeln `$foreach` representerar variabeln alltid alla objekt i samlingen när de nås direkt.</span><span class="sxs-lookup"><span data-stu-id="d0053-375">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="d0053-376">Använd den **aktuella** egenskapen för att komma åt det aktuella samlings elementet och metoderna **Reset** och **MoveNext** för att ändra dess värde.</span><span class="sxs-lookup"><span data-stu-id="d0053-376">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="d0053-377">Varje iteration av `foreach` slingen anropar automatiskt **MoveNext** -metoden.</span><span class="sxs-lookup"><span data-stu-id="d0053-377">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="d0053-378">Följande slinga körs bara två gånger.</span><span class="sxs-lookup"><span data-stu-id="d0053-378">The following loop only executes twice.</span></span> <span data-ttu-id="d0053-379">I den andra iterationen flyttas samlingen till det tredje elementet innan iterationen är klar.</span><span class="sxs-lookup"><span data-stu-id="d0053-379">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="d0053-380">Efter den andra iterationen finns det nu inga fler värden att iterera, och loopen avslutas.</span><span class="sxs-lookup"><span data-stu-id="d0053-380">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="d0053-381">Egenskapen **MoveNext** påverkar inte den variabel som valts för att iterera igenom samlingen ( `$Num` ).</span><span class="sxs-lookup"><span data-stu-id="d0053-381">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

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

<span data-ttu-id="d0053-382">Om du använder **Reset** -metoden återställs det aktuella elementet i samlingen.</span><span class="sxs-lookup"><span data-stu-id="d0053-382">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="d0053-383">I följande exempel upprepas de två första elementen **två gånger** eftersom **återställnings** metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="d0053-383">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="d0053-384">Efter de två första slingorna `if` Miss lyckas instruktionen och loopen upprepas genom alla tre elementen normalt.</span><span class="sxs-lookup"><span data-stu-id="d0053-384">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d0053-385">Detta kan resultera i en oändlig loop.</span><span class="sxs-lookup"><span data-stu-id="d0053-385">This could result in an infinite loop.</span></span>

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

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="d0053-386">Exempel 5: använda variabeln $switch</span><span class="sxs-lookup"><span data-stu-id="d0053-386">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="d0053-387">`$switch`Variabeln har exakt samma regler som `$foreach` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d0053-387">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="d0053-388">Följande exempel visar alla koncept för uppräknare.</span><span class="sxs-lookup"><span data-stu-id="d0053-388">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="d0053-389">Observera att **NotEvaluated** -fallet aldrig körs, även om det inte finns någon `break` instruktion efter **MoveNext** -metoden.</span><span class="sxs-lookup"><span data-stu-id="d0053-389">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d0053-390">Se även</span><span class="sxs-lookup"><span data-stu-id="d0053-390">See also</span></span>

[<span data-ttu-id="d0053-391">about_Functions</span><span class="sxs-lookup"><span data-stu-id="d0053-391">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="d0053-392">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="d0053-392">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="d0053-393">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="d0053-393">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="d0053-394">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="d0053-394">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="d0053-395">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="d0053-395">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="d0053-396">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="d0053-396">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="d0053-397">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="d0053-397">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="d0053-398">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="d0053-398">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="d0053-399">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="d0053-399">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="d0053-400">about_Variables</span><span class="sxs-lookup"><span data-stu-id="d0053-400">about_Variables</span></span>](about_Variables.md)
