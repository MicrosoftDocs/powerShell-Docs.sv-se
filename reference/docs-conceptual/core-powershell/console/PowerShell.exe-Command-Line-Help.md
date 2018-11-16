---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Kommandoradshjälp för PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 03c7672ee72698fe88a73e99702ceaadf87e702f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51691838"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="023eb-103">Kommandoradshjälp för PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="023eb-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="023eb-104">Du kan starta en PowerShell-session från kommandoraden för ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session.</span><span class="sxs-lookup"><span data-stu-id="023eb-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="023eb-105">Använda parametrar för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="023eb-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="023eb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="023eb-106">Syntax</span></span>

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="023eb-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="023eb-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="023eb-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="023eb-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="023eb-109">Accepterar en base-64-kodad strängversion av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="023eb-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="023eb-110">Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller av klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="023eb-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="023eb-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="023eb-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="023eb-112">Anger principen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="023eb-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="023eb-113">Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret.</span><span class="sxs-lookup"><span data-stu-id="023eb-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="023eb-114">Information om PowerShell-körningsprinciper, inklusive en lista över giltiga värden finns i [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="023eb-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="023eb-115">-Filen <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="023eb-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="023eb-116">Kör det angivna skriptet i det lokala scopet (”punkt källkod”), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="023eb-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="023eb-117">Ange sökväg till skriptfilen och parametrar.</span><span class="sxs-lookup"><span data-stu-id="023eb-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="023eb-118">**Filen** måste anges som sista parameter i kommandot.</span><span class="sxs-lookup"><span data-stu-id="023eb-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="023eb-119">Alla värden efter den **-filen** parametern tolkas som skriptet som sökväg och parametrar skickades till skriptet.</span><span class="sxs-lookup"><span data-stu-id="023eb-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="023eb-120">Parametrarna som skickades till skriptet skickas som literala strängar efter tolkning av den aktuella shell.</span><span class="sxs-lookup"><span data-stu-id="023eb-120">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="023eb-121">Om du är i cmd.exe och vill skicka ett miljövariabelvärde, skulle du till exempel använda cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="023eb-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="023eb-122">Kör däremot `powershell.exe -File .\test.ps1 -TestParam $env:windir` i cmd.exe resultaten i skriptet tar emot den exakta strängen `$env:windir` eftersom den har ingen särskild innebörd till aktuella cmd.exe-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="023eb-122">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in cmd.exe results in the script receiving the literal string `$env:windir` because it has no special meaning to the current cmd.exe shell.</span></span>
<span data-ttu-id="023eb-123">Den `$env:windir` formatet för variabeln miljöreferens _kan_ användas inuti en `-Command` parameter, eftersom det inte det tolkas som PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="023eb-123">The `$env:windir` style of environment variable reference _can_ be used inside a `-Command` parameter, since there it will be interpreted as PowerShell code.</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="023eb-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="023eb-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="023eb-125">Beskriver formatet för data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023eb-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="023eb-126">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="023eb-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="023eb-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="023eb-127">-Mta</span></span>

<span data-ttu-id="023eb-128">Startar PowerShell med hjälp av en.</span><span class="sxs-lookup"><span data-stu-id="023eb-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="023eb-129">Den här parametern introducerades i PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="023eb-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="023eb-130">I PowerShell 3.0 är single-threaded apartment (STA) standard.</span><span class="sxs-lookup"><span data-stu-id="023eb-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="023eb-131">I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.</span><span class="sxs-lookup"><span data-stu-id="023eb-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="023eb-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="023eb-132">-NoExit</span></span>

<span data-ttu-id="023eb-133">Inte avsluta när du har kört startkommandon.</span><span class="sxs-lookup"><span data-stu-id="023eb-133">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="023eb-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="023eb-134">-NoLogo</span></span>

<span data-ttu-id="023eb-135">Döljer copyright popup-meddelandet vid start.</span><span class="sxs-lookup"><span data-stu-id="023eb-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="023eb-136">-Icke-interaktiv</span><span class="sxs-lookup"><span data-stu-id="023eb-136">-NonInteractive</span></span>

<span data-ttu-id="023eb-137">Inte presentera en interaktiv prompt för användaren.</span><span class="sxs-lookup"><span data-stu-id="023eb-137">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="023eb-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="023eb-138">-NoProfile</span></span>

<span data-ttu-id="023eb-139">Inte läsa in PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="023eb-139">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="023eb-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="023eb-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="023eb-141">Anger hur utdata från PowerShell ska formateras.</span><span class="sxs-lookup"><span data-stu-id="023eb-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="023eb-142">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="023eb-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="023eb-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="023eb-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="023eb-144">Läser in den angivna filen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="023eb-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="023eb-145">Ange sökvägen och namnet på konsolfilen.</span><span class="sxs-lookup"><span data-stu-id="023eb-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="023eb-146">Du kan skapa en MMC-konsol med den [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023eb-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="023eb-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="023eb-147">-Sta</span></span>

<span data-ttu-id="023eb-148">Startar PowerShell med hjälp av en single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="023eb-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="023eb-149">I PowerShell 3.0 är single-threaded apartment (STA) standard.</span><span class="sxs-lookup"><span data-stu-id="023eb-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="023eb-150">I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.</span><span class="sxs-lookup"><span data-stu-id="023eb-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="023eb-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="023eb-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="023eb-152">Startar den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023eb-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="023eb-153">Den version som du anger måste installeras på systemet.</span><span class="sxs-lookup"><span data-stu-id="023eb-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="023eb-154">Om PowerShell 3.0 är installerad på datorn, är giltiga värden ”2.0” och ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="023eb-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="023eb-155">Standardvärdet är ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="023eb-155">The default value is "3.0".</span></span>

<span data-ttu-id="023eb-156">Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”.</span><span class="sxs-lookup"><span data-stu-id="023eb-156">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="023eb-157">Andra värden ignoreras.</span><span class="sxs-lookup"><span data-stu-id="023eb-157">Other values are ignored.</span></span>

<span data-ttu-id="023eb-158">Mer information finns i [installera Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="023eb-158">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="023eb-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="023eb-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="023eb-160">Anger formatmallen fönster för sessionen.</span><span class="sxs-lookup"><span data-stu-id="023eb-160">Sets the window style for the session.</span></span> <span data-ttu-id="023eb-161">Giltiga värden är Normal, minimerat, maximerat och dold.</span><span class="sxs-lookup"><span data-stu-id="023eb-161">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="023eb-162">-Kommandot</span><span class="sxs-lookup"><span data-stu-id="023eb-162">-Command</span></span>

<span data-ttu-id="023eb-163">Kör de angivna kommandon (med några parametrar) som om de har skrivits i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="023eb-163">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span>
<span data-ttu-id="023eb-164">Efter körning, PowerShell avslutas om inte den **NoExit** parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="023eb-164">After execution, PowerShell exits unless the **NoExit** parameter is specified.</span></span>
<span data-ttu-id="023eb-165">Text efter `-Command` skickas som en enda kommandorad till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="023eb-165">Any text after `-Command` is sent as a single command line to PowerShell.</span></span>
<span data-ttu-id="023eb-166">Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript.</span><span class="sxs-lookup"><span data-stu-id="023eb-166">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="023eb-167">Värdet för `-Command` kan vara ”-”, en sträng eller ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="023eb-167">The value of `-Command` can be "-", a string, or a script block.</span></span>
<span data-ttu-id="023eb-168">Resultatet av kommandot returneras till överordnade gränssnittet som avserialiserade XML-objekt, inte live-objekt.</span><span class="sxs-lookup"><span data-stu-id="023eb-168">The results of the command are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="023eb-169">Om värdet för `-Command` är ”-”, kommandotexten läses från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="023eb-169">If the value of `-Command` is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="023eb-170">När värdet för `-Command` är en sträng, **kommandot** _måste_ anges som sista parameter angetts eftersom några tecken har angett när kommandot tolkas som kommandoradsargument.</span><span class="sxs-lookup"><span data-stu-id="023eb-170">When the value of `-Command` is a string, **Command** _must_ be the last parameter specified because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="023eb-171">Den **kommandot** parametern accepterar endast ett skriptblock för körning när den kan identifiera värdet som skickas till `-Command` som en ScriptBlock typ.</span><span class="sxs-lookup"><span data-stu-id="023eb-171">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to `-Command` as a ScriptBlock type.</span></span>
<span data-ttu-id="023eb-172">Det här är _endast_ möjligt när du kör PowerShell.exe från en annan PowerShell-värd.</span><span class="sxs-lookup"><span data-stu-id="023eb-172">This is _only_ possible when running PowerShell.exe from another PowerShell host.</span></span>
<span data-ttu-id="023eb-173">ScriptBlock typ kan finnas i en befintlig variabel, returnerade från ett uttryck eller parsade genom PowerShell vara värd för som en literal skriptblock som omges av klammerparenteser `{}`, innan de skickas till PowerShell.exe.</span><span class="sxs-lookup"><span data-stu-id="023eb-173">The ScriptBlock type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to PowerShell.exe.</span></span>

<span data-ttu-id="023eb-174">I cmd.exe, det finns ingen sådan funktion som ett skriptblock (eller ScriptBlock typ) så värdet som skickas till **kommandot** kommer _alltid_ vara en sträng.</span><span class="sxs-lookup"><span data-stu-id="023eb-174">In cmd.exe, there is no such thing as a script block (or ScriptBlock type), so the value passed to **Command** will _always_ be a string.</span></span>
<span data-ttu-id="023eb-175">Du kan skriva ett skriptblock inuti strängen, men i stället för som körs den fungerar precis som om du har angett det i en typisk PowerShell-kommandotolk, skriva ut innehållet i skriptet blockerar tillbaka till dig.</span><span class="sxs-lookup"><span data-stu-id="023eb-175">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="023eb-176">En sträng som skickas till `-Command` fortfarande körs som PowerShell, så att skriptet block av klammerparenteser krävs ofta inte i första hand när du kör från cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="023eb-176">A string passed to `-Command` will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from cmd.exe.</span></span>
<span data-ttu-id="023eb-177">Att köra ett infogat-skriptblock som definierats i en sträng i [anrop operatorn](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` kan användas:</span><span class="sxs-lookup"><span data-stu-id="023eb-177">To execute an inline script block defined inside a string, the [call operator](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` can be used:</span></span>

```console
"& {<command>}"
```

### <a name="-help---"></a><span data-ttu-id="023eb-178">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="023eb-178">-Help, -?, /?</span></span>

<span data-ttu-id="023eb-179">Visar syntaxen för powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="023eb-179">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="023eb-180">Om du skriver ett PowerShell.exe-kommando i PowerShell, Lägg till åtkomstgruppen kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/).</span><span class="sxs-lookup"><span data-stu-id="023eb-180">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="023eb-181">Du kan använda ett bindestreck eller snedstreck i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="023eb-181">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="023eb-182">Felsökningsmeddelande: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="023eb-182">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="023eb-183">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="023eb-183">EXAMPLES</span></span>

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
