---
description: Beskriver PowerShell-felsökaren.
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 46914937cebdf8cf3559371f354bf14cd6706115
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710638"
---
# <a name="about-debuggers"></a><span data-ttu-id="fe303-103">Om fel söknings program</span><span class="sxs-lookup"><span data-stu-id="fe303-103">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="fe303-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fe303-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="fe303-105">Beskriver PowerShell-felsökaren.</span><span class="sxs-lookup"><span data-stu-id="fe303-105">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="fe303-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fe303-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="fe303-107">Fel sökning är en process för att undersöka ett skript när det körs för att identifiera och korrigera fel i skript instruktionerna.</span><span class="sxs-lookup"><span data-stu-id="fe303-107">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="fe303-108">PowerShell-felsökaren kan hjälpa dig att undersöka och identifiera fel och ineffektiv i skript, funktioner, kommandon, DSC-konfigurationer (Desired State Configuration) eller uttryck.</span><span class="sxs-lookup"><span data-stu-id="fe303-108">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="fe303-109">Från och med PowerShell 5,0 har PowerShell-felsökaren uppdaterats för att felsöka skript, funktioner, kommandon, konfigurationer eller uttryck som körs i antingen-konsolen eller Windows PowerShell ISE på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="fe303-109">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="fe303-110">Du kan köra `Enter-PSSession` för att starta en interaktiv fjärran sluten PowerShell-session där du kan ange Bryt punkter och felsöka skriptfiler och kommandon på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="fe303-110">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="fe303-111">`Enter-PSSession` funktionen har uppdaterats så att du kan återansluta till och ange en frånkopplad session som kör ett skript eller kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="fe303-111">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="fe303-112">Om skriptet som körs träffar en Bryt punkt startar klient sessionen automatiskt fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-112">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="fe303-113">Om den frånkopplade sessionen som kör ett skript redan har nått en Bryt punkt och har stoppats vid Bryt punkten, `Enter-PSSession` startar automatiskt kommando rads fel söknings programmet när du återansluter till sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-113">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="fe303-114">Du kan använda funktionerna i PowerShell-felsökaren för att undersöka ett PowerShell-skript, funktion, kommando eller uttryck när den körs.</span><span class="sxs-lookup"><span data-stu-id="fe303-114">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, or expression while it is running.</span></span> <span data-ttu-id="fe303-115">PowerShell-felsökaren innehåller en uppsättning cmdletar som gör att du kan ange Bryt punkter, hantera Bryt punkter och Visa anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="fe303-115">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="fe303-116">Fel söknings-cmdletar</span><span class="sxs-lookup"><span data-stu-id="fe303-116">Debugger Cmdlets</span></span>

<span data-ttu-id="fe303-117">PowerShell-felsökaren innehåller följande uppsättning cmdletar:</span><span class="sxs-lookup"><span data-stu-id="fe303-117">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="fe303-118">`Set-PSBreakpoint`: Anger Bryt punkter för linjer, variabler och kommandon.</span><span class="sxs-lookup"><span data-stu-id="fe303-118">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="fe303-119">`Get-PSBreakpoint`: Hämtar Bryt punkter i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-119">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="fe303-120">`Disable-PSBreakpoint`: Stänger av Bryt punkter i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-120">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="fe303-121">`Enable-PSBreakpoint`: Aktiverar Bryt punkter i den aktuella sessionen igen.</span><span class="sxs-lookup"><span data-stu-id="fe303-121">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="fe303-122">`Remove-PSBreakpoint`: Tar bort Bryt punkter från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-122">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="fe303-123">`Get-PSCallStack`: Visar den aktuella anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="fe303-123">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="fe303-124">Starta och stoppa fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="fe303-124">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="fe303-125">Ange en eller flera Bryt punkter för att starta fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-125">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="fe303-126">Kör sedan skriptet, kommandot eller funktionen som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="fe303-126">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="fe303-127">När du når en Bryt punkt, stoppas körningen och kontroll sker över till fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-127">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="fe303-128">Stoppa fel söknings programmet genom att köra skriptet, kommandot eller funktionen tills det är klart.</span><span class="sxs-lookup"><span data-stu-id="fe303-128">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="fe303-129">Eller Skriv `stop` eller `t` .</span><span class="sxs-lookup"><span data-stu-id="fe303-129">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="fe303-130">Fel söknings kommandon</span><span class="sxs-lookup"><span data-stu-id="fe303-130">Debugger Commands</span></span>

<span data-ttu-id="fe303-131">När du använder fel sökaren i PowerShell-konsolen, använder du följande kommandon för att kontrol lera körningen.</span><span class="sxs-lookup"><span data-stu-id="fe303-131">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="fe303-132">I Windows PowerShell ISE använder du kommandon på fel söknings menyn.</span><span class="sxs-lookup"><span data-stu-id="fe303-132">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="fe303-133">Obs! information om hur du använder fel sökaren i andra värd program finns i dokumentationen för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-133">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="fe303-134">`s`, `StepInto` : Kör nästa instruktion och stoppar sedan.</span><span class="sxs-lookup"><span data-stu-id="fe303-134">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="fe303-135">`v`, `StepOver` : Kör nästa instruktion, men hoppar över funktioner och anrop.</span><span class="sxs-lookup"><span data-stu-id="fe303-135">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="fe303-136">De överhoppade instruktionerna körs, men är inte stegvisa.</span><span class="sxs-lookup"><span data-stu-id="fe303-136">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="fe303-137">`Ctrl+Break`: (Break all i ISE) bryts i ett skript som körs antingen i PowerShell-konsolen eller Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fe303-137">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="fe303-138">Observera att <kbd>CTRL</kbd> + <kbd>Break</kbd> i Windows PowerShell 2,0, 3,0 och 4,0 stänger programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-138">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="fe303-139">Bryt alla arbeten på både lokala och fjärranslutna skript som körs interaktivt.</span><span class="sxs-lookup"><span data-stu-id="fe303-139">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="fe303-140">`o`, `StepOut` : Steg ut ur den aktuella funktionen, upp till en nivå om den är kapslad.</span><span class="sxs-lookup"><span data-stu-id="fe303-140">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="fe303-141">Om den finns i huvud texten fortsätter den till slutet eller nästa Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="fe303-141">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="fe303-142">De överhoppade instruktionerna körs, men är inte stegvisa.</span><span class="sxs-lookup"><span data-stu-id="fe303-142">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="fe303-143">`c`, `Continue` : Fortsätter att köras tills skriptet har slutförts eller tills nästa Bryt punkt har nåtts.</span><span class="sxs-lookup"><span data-stu-id="fe303-143">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="fe303-144">De överhoppade instruktionerna körs, men är inte stegvisa.</span><span class="sxs-lookup"><span data-stu-id="fe303-144">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="fe303-145">`l`, `List` : Visar den del av skriptet som körs.</span><span class="sxs-lookup"><span data-stu-id="fe303-145">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="fe303-146">Som standard visas den aktuella raden, fem föregående rader och 10 efterföljande rader.</span><span class="sxs-lookup"><span data-stu-id="fe303-146">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="fe303-147">Tryck på RETUR för att fortsätta att lista skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-147">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="fe303-148">`l <m>`, `List` : Visar 16 rader i skriptet som börjar med rad numret som anges av `<m>` .</span><span class="sxs-lookup"><span data-stu-id="fe303-148">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="fe303-149">`l <m> <n>`, `List` : Visar `<n>` rader i skriptet, som börjar med rad numret som anges av `<m>` .</span><span class="sxs-lookup"><span data-stu-id="fe303-149">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="fe303-150">`q`, `Stop` , `Exit` : Stoppar körningen av skriptet och avslutar fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-150">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="fe303-151">Om du felsöker ett jobb genom att köra `Debug-Job` cmdleten `Exit` kopplar kommandot av fel söknings programmet och gör att jobbet kan fortsätta att köras.</span><span class="sxs-lookup"><span data-stu-id="fe303-151">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="fe303-152">`k`, `Get-PsCallStack` : Visar den aktuella anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="fe303-152">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="fe303-153">`<Enter>`: Upprepar det senaste kommandot om det var steg, StepOver (v) eller List (l).</span><span class="sxs-lookup"><span data-stu-id="fe303-153">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="fe303-154">Annars representerar en skicka-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="fe303-154">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="fe303-155">`?`, `h` : Visar hjälp om fel söknings kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe303-155">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="fe303-156">Om du vill avsluta fel söknings programmet kan du använda stop (q).</span><span class="sxs-lookup"><span data-stu-id="fe303-156">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="fe303-157">Från och med PowerShell 5,0 kan du köra Exit-kommandot för att avsluta en kapslad felsökningssession som du startade genom att köra antingen `Debug-Job` eller `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="fe303-157">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="fe303-158">Genom att använda de här fel söknings kommandona kan du köra ett skript, stoppa en viss angelägenhet, undersöka värdena för variabler och systemets tillstånd och fortsätta köra skriptet tills du har identifierat ett problem.</span><span class="sxs-lookup"><span data-stu-id="fe303-158">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="fe303-159">Obs! Om du stegar i en instruktion med en omdirigerings Operator, t. ex. ">", PowerShell fel söknings stegen över alla återstående instruktioner i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-159">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="fe303-160">Visar värdena för skript-variabler</span><span class="sxs-lookup"><span data-stu-id="fe303-160">Displaying the Values of script Variables</span></span>

<span data-ttu-id="fe303-161">Medan du är i fel söknings programmet kan du också ange kommandon, Visa värdet för variabler, använda cmdlets och köra skript på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="fe303-161">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="fe303-162">Du kan visa det aktuella värdet för alla variabler i skriptet som felsöks, förutom följande automatiska variabler:</span><span class="sxs-lookup"><span data-stu-id="fe303-162">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="fe303-163">Om du försöker visa värdet för någon av dessa variabler får du värdet för den variabeln för i en intern pipeline som fel sökaren använder, inte värdet för variabeln i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-163">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="fe303-164">Om du vill visa värdet för de variabler som ska felsökas i skriptet, tilldelar du värdet för den automatiska variabeln till en ny variabel i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-164">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="fe303-165">Sedan kan du Visa värdet för den nya variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-165">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="fe303-166">Exempel:</span><span class="sxs-lookup"><span data-stu-id="fe303-166">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="fe303-167">I exemplet i det här avsnittet `$MyInvocation` omtilldelas värdet för variabeln enligt följande:</span><span class="sxs-lookup"><span data-stu-id="fe303-167">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="fe303-168">Fel söknings miljön</span><span class="sxs-lookup"><span data-stu-id="fe303-168">The Debugger Environment</span></span>

<span data-ttu-id="fe303-169">När du når en Bryt punkt anger du fel söknings miljön.</span><span class="sxs-lookup"><span data-stu-id="fe303-169">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="fe303-170">Kommando tolken ändras så att den börjar med "[DBG]:".</span><span class="sxs-lookup"><span data-stu-id="fe303-170">The command prompt changes so that it begins with "[DBG]:".</span></span>

<span data-ttu-id="fe303-171">Mer information om hur du anpassar meddelandet finns i [about_Prompts](about_prompts.md).</span><span class="sxs-lookup"><span data-stu-id="fe303-171">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="fe303-172">I vissa värd program, t. ex. PowerShell-konsolen, (men inte i Windows PowerShell Integrated Scripting Environment [ISE]) öppnas en kapslad prompt för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="fe303-172">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="fe303-173">Du kan identifiera den kapslade frågan genom att upprepa större än-tecken (ASCII 62) som visas i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="fe303-173">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="fe303-174">Följande är till exempel standard fel söknings frågan i PowerShell-konsolen:</span><span class="sxs-lookup"><span data-stu-id="fe303-174">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="fe303-175">Du kan hitta kapslings nivån genom att använda den `$NestedPromptLevel` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-175">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="fe303-176">Dessutom definieras en automatisk variabel, `$PSDebugContext` , i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="fe303-176">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="fe303-177">Du kan använda `$PsDebugContext` variabeln för att avgöra om du befinner dig i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-177">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="fe303-178">Exempel:</span><span class="sxs-lookup"><span data-stu-id="fe303-178">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="fe303-179">Du kan använda värdet för `$PSDebugContext` variabeln i fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="fe303-179">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="fe303-180">Fel sökning och omfång</span><span class="sxs-lookup"><span data-stu-id="fe303-180">Debugging and Scope</span></span>

<span data-ttu-id="fe303-181">Om du bryter ned i fel söknings programmet ändras inte omfattningen som du arbetar i, men när du når en Bryt punkt i ett skript, flyttas du till skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="fe303-181">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="fe303-182">Skript omfånget är underordnat det omfång i vilket du körde fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-182">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="fe303-183">Om du vill hitta variabler och alias som har definierats i skript omfånget använder du omfattnings parametern `Get-Alias` för `Get-Variable` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="fe303-183">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="fe303-184">Följande kommando hämtar till exempel variablerna i den lokala (skript) omfattningen:</span><span class="sxs-lookup"><span data-stu-id="fe303-184">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="fe303-185">Du kan förkorta kommandot som:</span><span class="sxs-lookup"><span data-stu-id="fe303-185">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="fe303-186">Det här är ett användbart sätt att bara se de variabler som du har definierat i skriptet och som du definierade vid fel sökning.</span><span class="sxs-lookup"><span data-stu-id="fe303-186">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="fe303-187">Fel sökning på kommando raden</span><span class="sxs-lookup"><span data-stu-id="fe303-187">Debugging at the Command Line</span></span>

<span data-ttu-id="fe303-188">När du anger en variabel Bryt punkt eller en kommando Bryt punkt kan du bara ange Bryt punkten i en skript fil.</span><span class="sxs-lookup"><span data-stu-id="fe303-188">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="fe303-189">Som standard anges Bryt punkten för allt som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-189">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="fe303-190">Om du till exempel ställer in en Bryt punkt på `$name` variabeln, bryts fel söknings verktyget på valfri `$name` variabel i skript, kommando, funktion, skript-cmdlet eller uttryck som du kör tills du inaktiverar eller tar bort Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="fe303-190">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="fe303-191">På så sätt kan du felsöka skript i en mer realistisk kontext där de kan påverkas av funktioner, variabler och andra skript i sessionen och i användarens profil.</span><span class="sxs-lookup"><span data-stu-id="fe303-191">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="fe303-192">Rad Bryt punkter är specifika för skriptfiler, så de anges bara i skriptfiler.</span><span class="sxs-lookup"><span data-stu-id="fe303-192">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-functions"></a><span data-ttu-id="fe303-193">Fel söknings funktioner</span><span class="sxs-lookup"><span data-stu-id="fe303-193">Debugging Functions</span></span>

<span data-ttu-id="fe303-194">När du anger en Bryt punkt för en funktion som har `Begin` , `Process` , och `End` avsnitt, bryts fel söknings verktyget på den första raden i varje avsnitt.</span><span class="sxs-lookup"><span data-stu-id="fe303-194">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="fe303-195">Exempel:</span><span class="sxs-lookup"><span data-stu-id="fe303-195">For example:</span></span>

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a><span data-ttu-id="fe303-196">Felsöka fjärrskript</span><span class="sxs-lookup"><span data-stu-id="fe303-196">Debugging Remote Scripts</span></span>

<span data-ttu-id="fe303-197">Från och med PowerShell 5,0 kan du köra PowerShell-felsökning i en fjärrsession, antingen i-konsolen eller Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fe303-197">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="fe303-198">`Enter-PSSession` funktionen har uppdaterats så att du kan återansluta till och ange en frånkopplad session som körs på en fjärrdator och som kör ett skript.</span><span class="sxs-lookup"><span data-stu-id="fe303-198">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="fe303-199">Om skriptet som körs träffar en Bryt punkt startar klient sessionen automatiskt fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-199">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="fe303-200">Följande är ett exempel som visar hur det fungerar, med Bryt punkter som anges i ett skript på rad 6, 11, 22 och 25.</span><span class="sxs-lookup"><span data-stu-id="fe303-200">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="fe303-201">Observera att i exemplet, när fel söknings programmet startar, finns det två identifierande prompter: namnet på den dator där sessionen körs och DBG-prompten där du vet att du är i fel söknings läge.</span><span class="sxs-lookup"><span data-stu-id="fe303-201">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a><span data-ttu-id="fe303-202">Exempel</span><span class="sxs-lookup"><span data-stu-id="fe303-202">Examples</span></span>

<span data-ttu-id="fe303-203">Det här test skriptet identifierar operativ systemets version och visar ett system-lämpligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="fe303-203">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="fe303-204">Den innehåller en funktion, ett funktions anrop och en variabel.</span><span class="sxs-lookup"><span data-stu-id="fe303-204">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="fe303-205">Följande kommando visar innehållet i test skript filen:</span><span class="sxs-lookup"><span data-stu-id="fe303-205">The following command displays the contents of the test script file:</span></span>

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

<span data-ttu-id="fe303-206">Starta genom att ange en Bryt punkt i en orienterings punkt i skriptet, till exempel en linje, ett kommando, en variabel eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="fe303-206">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="fe303-207">Börja med att skapa en rad Bryt punkt på den första raden i Test.ps1-skriptet i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="fe303-207">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="fe303-208">Du kan förkorta det här kommandot som:</span><span class="sxs-lookup"><span data-stu-id="fe303-208">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="fe303-209">Kommandot returnerar ett rad brytnings objekt (**system. Management. Automation. LineBreakpoint**).</span><span class="sxs-lookup"><span data-stu-id="fe303-209">The command returns a line-breakpoint object (**System.Management.Automation.LineBreakpoint**).</span></span>

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

<span data-ttu-id="fe303-210">Starta nu skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-210">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="fe303-211">När skriptet når den första Bryt punkten, anger Bryt punkts meddelandet att fel söknings programmet är aktivt.</span><span class="sxs-lookup"><span data-stu-id="fe303-211">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="fe303-212">Den beskriver Bryt punkten och för hands versionerna av den första raden i skriptet, som är en funktions deklaration.</span><span class="sxs-lookup"><span data-stu-id="fe303-212">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="fe303-213">Kommando tolken ändras också för att indikera att fel söknings programmet har kontroll.</span><span class="sxs-lookup"><span data-stu-id="fe303-213">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="fe303-214">För hands versions raden ingår skript namnet och rad numret för det förvisade kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe303-214">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="fe303-215">Använd steg-kommandona för att köra den första instruktionen i skriptet och för att förhandsgranska nästa instruktion.</span><span class="sxs-lookup"><span data-stu-id="fe303-215">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="fe303-216">I nästa instruktion används den `$MyInvocation` automatiska variabeln för att ange värdet för `$scriptName` variabeln till sökvägen och fil namnet för skript filen.</span><span class="sxs-lookup"><span data-stu-id="fe303-216">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="fe303-217">`$scriptName`Variabeln är nu inte ifylld, men du kan kontrol lera värdet för variabeln genom att visa dess värde.</span><span class="sxs-lookup"><span data-stu-id="fe303-217">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="fe303-218">I det här fallet är värdet `$null` .</span><span class="sxs-lookup"><span data-stu-id="fe303-218">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="fe303-219">Använd ett annat steg för att köra den aktuella instruktionen och för att förhandsgranska nästa instruktion i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-219">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="fe303-220">Next-instruktionen anropar funktionen PsVersion.</span><span class="sxs-lookup"><span data-stu-id="fe303-220">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="fe303-221">I det här läget `$scriptName` fylls variabeln i, men du verifierar värdet för variabeln genom att visa dess värde.</span><span class="sxs-lookup"><span data-stu-id="fe303-221">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="fe303-222">I det här fallet anges värdet för skript Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="fe303-222">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="fe303-223">Använd ett annat steg-kommando för att köra funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="fe303-223">Use another Step command to execute the function call.</span></span> <span data-ttu-id="fe303-224">Tryck på RETUR eller skriv "s" för steg.</span><span class="sxs-lookup"><span data-stu-id="fe303-224">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="fe303-225">Fel söknings meddelandet innehåller en förhands granskning av instruktionen i funktionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-225">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="fe303-226">Om du vill köra den här instruktionen och för att förhandsgranska nästa instruktion i funktionen kan du använda ett `Step` kommando.</span><span class="sxs-lookup"><span data-stu-id="fe303-226">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="fe303-227">Men i det här fallet använder du ett utgångs kommando (o).</span><span class="sxs-lookup"><span data-stu-id="fe303-227">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="fe303-228">Körningen av funktionen slutförs (såvida den inte når en Bryt punkt) och steg till nästa instruktion i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-228">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="fe303-229">Eftersom vi är på den sista instruktionen i skriptet, har steget, steget och kommandot Continue samma resultat.</span><span class="sxs-lookup"><span data-stu-id="fe303-229">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="fe303-230">I det här fallet använder du stega (o).</span><span class="sxs-lookup"><span data-stu-id="fe303-230">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="fe303-231">Kommandot stega kör det sista kommandot.</span><span class="sxs-lookup"><span data-stu-id="fe303-231">The StepOut command executes the last command.</span></span> <span data-ttu-id="fe303-232">Standard kommando tolken anger att fel söknings programmet har avslutat och returnerat kontroll till kommando processorn.</span><span class="sxs-lookup"><span data-stu-id="fe303-232">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="fe303-233">Kör nu fel söknings programmet igen.</span><span class="sxs-lookup"><span data-stu-id="fe303-233">Now, run the debugger again.</span></span> <span data-ttu-id="fe303-234">Ta först bort den aktuella Bryt punkten genom att använda `Get-PsBreakpoint` `Remove-PsBreakpoint` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="fe303-234">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="fe303-235">(Om du tror att du kan återanvända Bryt punkten använder du `Disable-PsBreakpoint` cmdleten i stället för `Remove-PsBreakpoint` .)</span><span class="sxs-lookup"><span data-stu-id="fe303-235">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="fe303-236">Du kan förkorta det här kommandot som:</span><span class="sxs-lookup"><span data-stu-id="fe303-236">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="fe303-237">Eller kör kommandot genom att skriva en funktion, till exempel följande funktion:</span><span class="sxs-lookup"><span data-stu-id="fe303-237">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="fe303-238">Nu ska du skapa en Bryt punkt för `$scriptname` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-238">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="fe303-239">Du kan förkorta kommandot som:</span><span class="sxs-lookup"><span data-stu-id="fe303-239">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="fe303-240">Starta nu skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-240">Now, start the script.</span></span> <span data-ttu-id="fe303-241">Skriptet når den variabla Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="fe303-241">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="fe303-242">Standard läget är Write, så körningen stoppas precis innan instruktionen som ändrar värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-242">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="fe303-243">Visar det aktuella värdet för `$scriptName` variabeln, som är `$null` .</span><span class="sxs-lookup"><span data-stu-id="fe303-243">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="fe303-244">Använd ett eller flera steg för att köra instruktionen som fyller på variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-244">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="fe303-245">Sedan visar du det nya värdet för `$scriptName` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fe303-245">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="fe303-246">Next-instruktionen är ett anrop till funktionen PsVersion.</span><span class="sxs-lookup"><span data-stu-id="fe303-246">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="fe303-247">Om du vill hoppa över funktionen men ändå köra den, använder du ett StepOver-kommando (v).</span><span class="sxs-lookup"><span data-stu-id="fe303-247">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="fe303-248">Om du redan har använt funktionen StepOver är det inte effektivt.</span><span class="sxs-lookup"><span data-stu-id="fe303-248">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="fe303-249">Funktions anropet visas, men det körs inte.</span><span class="sxs-lookup"><span data-stu-id="fe303-249">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="fe303-250">StepOver-kommandot kör funktionen och för hands Grans kar nästa instruktion i skriptet som skriver ut den sista raden.</span><span class="sxs-lookup"><span data-stu-id="fe303-250">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="fe303-251">Använd ett stopp kommando (t) för att avsluta fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="fe303-251">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="fe303-252">Kommando tolken återgår till standard kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="fe303-252">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="fe303-253">Om du vill ta bort Bryt punkterna använder `Get-PsBreakpoint` du `Remove-PsBreakpoint` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="fe303-253">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="fe303-254">Skapa en ny kommando Bryt punkt för funktionen PsVersion.</span><span class="sxs-lookup"><span data-stu-id="fe303-254">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="fe303-255">Du kan förkorta det här kommandot för att:</span><span class="sxs-lookup"><span data-stu-id="fe303-255">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="fe303-256">Kör nu skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-256">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="fe303-257">Skriptet når Bryt punkten vid funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="fe303-257">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="fe303-258">I det här läget har funktionen inte anropats än.</span><span class="sxs-lookup"><span data-stu-id="fe303-258">At this point, the function has not yet been called.</span></span> <span data-ttu-id="fe303-259">Det ger dig möjlighet att använda åtgärds parametern för `Set-PSBreakpoint` för att ange villkor för körning av Bryt punkten eller för att utföra förberedande eller diagnostiska uppgifter, till exempel starta en logg eller anropa ett diagnostik-eller säkerhets skript.</span><span class="sxs-lookup"><span data-stu-id="fe303-259">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="fe303-260">Ange en åtgärd genom att använda ett Continue-kommando (c) för att avsluta skriptet och ett `Remove-PsBreakpoint` kommando för att ta bort den aktuella Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="fe303-260">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="fe303-261">(Bryt punkter är skrivskyddade, så du kan inte lägga till en åtgärd i den aktuella Bryt punkten.)</span><span class="sxs-lookup"><span data-stu-id="fe303-261">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="fe303-262">Nu skapar du en ny kommando Bryt punkt med en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="fe303-262">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="fe303-263">Följande kommando anger en kommando Bryt punkt med en åtgärd som loggar värdet för `$scriptName` variabeln när funktionen anropas.</span><span class="sxs-lookup"><span data-stu-id="fe303-263">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="fe303-264">Eftersom Break-nyckelordet inte används i åtgärden stoppas inte körningen.</span><span class="sxs-lookup"><span data-stu-id="fe303-264">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="fe303-265">("Bakticket (") är ett linje fortsättnings kort.)</span><span class="sxs-lookup"><span data-stu-id="fe303-265">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="fe303-266">Du kan också lägga till åtgärder som anger villkor för Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="fe303-266">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="fe303-267">I följande kommando körs kommando Bryt punkten endast om körnings principen är inställd på RemoteSigned, den mest restriktiva principen som fortfarande tillåter att du kör skript.</span><span class="sxs-lookup"><span data-stu-id="fe303-267">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="fe303-268">("Bakticket (") är det fortsättnings tecknen.)</span><span class="sxs-lookup"><span data-stu-id="fe303-268">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="fe303-269">Nyckelordet Break i åtgärden styr fel söknings verktyget att köra Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="fe303-269">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="fe303-270">Du kan också använda nyckelordet Continue för att direkt köra fel söknings programmet utan att behöva bryta.</span><span class="sxs-lookup"><span data-stu-id="fe303-270">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="fe303-271">Eftersom nyckelordet default är Continue måste du ange Break för att stoppa körningen.</span><span class="sxs-lookup"><span data-stu-id="fe303-271">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="fe303-272">Kör nu skriptet.</span><span class="sxs-lookup"><span data-stu-id="fe303-272">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="fe303-273">Eftersom körnings principen är inställd på **RemoteSigned**, stoppas körningen vid funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="fe303-273">Because the execution policy is set to **RemoteSigned**, execution stops at the function call.</span></span>

<span data-ttu-id="fe303-274">I det här läget kanske du vill kontrol lera anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="fe303-274">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="fe303-275">Använd `Get-PsCallStack` cmdleten eller `Get-PsCallStack` fel söknings kommandot (k).</span><span class="sxs-lookup"><span data-stu-id="fe303-275">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="fe303-276">Följande kommando hämtar den aktuella anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="fe303-276">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="fe303-277">Det här exemplet visar bara några av många sätt att använda PowerShell-felsökaren.</span><span class="sxs-lookup"><span data-stu-id="fe303-277">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="fe303-278">Om du vill ha mer information om fel söknings-cmdletar skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="fe303-278">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="fe303-279">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="fe303-279">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="fe303-280">Andra fel söknings funktioner i PowerShell</span><span class="sxs-lookup"><span data-stu-id="fe303-280">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="fe303-281">Förutom PowerShell-felsökaren innehåller PowerShell flera andra funktioner som du kan använda för att felsöka skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="fe303-281">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="fe303-282">Windows PowerShell ISE innehåller en interaktiv grafisk fel sökare.</span><span class="sxs-lookup"><span data-stu-id="fe303-282">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="fe303-283">Om du vill ha mer information startar du Windows PowerShell ISE och trycker på F1.</span><span class="sxs-lookup"><span data-stu-id="fe303-283">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="fe303-284">`Set-PSDebug`Cmdleten erbjuder mycket grundläggande skript fel söknings funktioner, inklusive steging och spårning.</span><span class="sxs-lookup"><span data-stu-id="fe303-284">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="fe303-285">Använd `Set-StrictMode` cmdleten för att identifiera referenser till oinitierade variabler, referera till obefintliga egenskaper för ett objekt och för att visa syntaxen som inte är giltig.</span><span class="sxs-lookup"><span data-stu-id="fe303-285">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="fe303-286">Lägg till diagnostiska uttryck i ett skript, till exempel instruktioner som visar värdet för variabler, instruktioner som läser ininformation från kommando raden eller instruktioner som rapporterar den aktuella instruktionen.</span><span class="sxs-lookup"><span data-stu-id="fe303-286">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="fe303-287">Använd de cmdlets som innehåller Skriv verbet för uppgiften, till exempel, `Write-Host` , `Write-Debug` `Write-Warning` och `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="fe303-287">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe303-288">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="fe303-288">SEE ALSO</span></span>

- [<span data-ttu-id="fe303-289">Disable-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe303-289">Disable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="fe303-290">Aktivera – PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe303-290">Enable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="fe303-291">Get-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe303-291">Get-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="fe303-292">Get-PsCallStack</span><span class="sxs-lookup"><span data-stu-id="fe303-292">Get-PsCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="fe303-293">Remove-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe303-293">Remove-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="fe303-294">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fe303-294">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="fe303-295">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="fe303-295">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="fe303-296">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="fe303-296">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)

