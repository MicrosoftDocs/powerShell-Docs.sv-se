---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Kommandoradshjälp för PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: c7f35511e876e8e5189d8a2b949555603d43f731
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133849"
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="4e831-103">Kommandoradshjälp för PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="4e831-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="4e831-104">Du kan starta en PowerShell-session från kommandoraden för ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session.</span><span class="sxs-lookup"><span data-stu-id="4e831-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="4e831-105">Använda parametrar för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e831-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e831-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e831-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="4e831-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="4e831-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="4e831-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="4e831-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="4e831-109">Accepterar en base-64-kodad strängversion av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="4e831-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="4e831-110">Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller av klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="4e831-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="4e831-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="4e831-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="4e831-112">Anger principen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="4e831-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="4e831-113">Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret.</span><span class="sxs-lookup"><span data-stu-id="4e831-113">This parameter doesn't change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="4e831-114">Information om PowerShell-körningsprinciper, inklusive en lista över giltiga värden finns i [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="4e831-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="4e831-115">-Filen <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="4e831-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="4e831-116">Kör det angivna skriptet i det lokala scopet (”punkt källkod”), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e831-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="4e831-117">Ange sökväg till skriptfilen och parametrar.</span><span class="sxs-lookup"><span data-stu-id="4e831-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="4e831-118">**Filen** måste anges som sista parameter i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4e831-118">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="4e831-119">Alla värden efter den **-filen** parametern tolkas som skriptet som sökväg och parametrar skickades till skriptet.</span><span class="sxs-lookup"><span data-stu-id="4e831-119">All values typed after the **-File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="4e831-120">Parametrarna som skickades till skriptet skickas som literala strängar (efter tolkning av den aktuella shell).</span><span class="sxs-lookup"><span data-stu-id="4e831-120">Parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span> <span data-ttu-id="4e831-121">Om du är i cmd.exe och vill skicka ett miljövariabelvärde du exempelvis använder du cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` skriptet i det här exemplet tar emot den exakta strängen `$env:windir` och inte värdet för den i miljövariabeln: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="4e831-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` In this example, the script receives the literal string `$env:windir` and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="4e831-122">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="4e831-122">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="4e831-123">Beskriver formatet för data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e831-123">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="4e831-124">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="4e831-124">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="4e831-125">-Mta</span><span class="sxs-lookup"><span data-stu-id="4e831-125">-Mta</span></span>

<span data-ttu-id="4e831-126">Startar PowerShell med hjälp av en.</span><span class="sxs-lookup"><span data-stu-id="4e831-126">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="4e831-127">Den här parametern introducerades i PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="4e831-127">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="4e831-128">I PowerShell 3.0 är single-threaded apartment (STA) standard.</span><span class="sxs-lookup"><span data-stu-id="4e831-128">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="4e831-129">I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.</span><span class="sxs-lookup"><span data-stu-id="4e831-129">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="4e831-130">-NoExit</span><span class="sxs-lookup"><span data-stu-id="4e831-130">-NoExit</span></span>

<span data-ttu-id="4e831-131">Inte avsluta när du har kört startkommandon.</span><span class="sxs-lookup"><span data-stu-id="4e831-131">Doesn't exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="4e831-132">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="4e831-132">-NoLogo</span></span>

<span data-ttu-id="4e831-133">Döljer copyright popup-meddelandet vid start.</span><span class="sxs-lookup"><span data-stu-id="4e831-133">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="4e831-134">-Icke-interaktiv</span><span class="sxs-lookup"><span data-stu-id="4e831-134">-NonInteractive</span></span>

<span data-ttu-id="4e831-135">Inte presentera en interaktiv prompt för användaren.</span><span class="sxs-lookup"><span data-stu-id="4e831-135">Doesn't present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="4e831-136">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="4e831-136">-NoProfile</span></span>

<span data-ttu-id="4e831-137">Inte läsa in PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="4e831-137">Doesn't load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="4e831-138">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="4e831-138">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="4e831-139">Anger hur utdata från PowerShell ska formateras.</span><span class="sxs-lookup"><span data-stu-id="4e831-139">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="4e831-140">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="4e831-140">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="4e831-141">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="4e831-141">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="4e831-142">Läser in den angivna filen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4e831-142">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="4e831-143">Ange sökvägen och namnet på konsolfilen.</span><span class="sxs-lookup"><span data-stu-id="4e831-143">Enter the path and name of the console file.</span></span> <span data-ttu-id="4e831-144">Du kan skapa en MMC-konsol med den [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e831-144">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="4e831-145">-Sta</span><span class="sxs-lookup"><span data-stu-id="4e831-145">-Sta</span></span>

<span data-ttu-id="4e831-146">Startar PowerShell med hjälp av en single-threaded apartment.</span><span class="sxs-lookup"><span data-stu-id="4e831-146">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="4e831-147">I PowerShell 3.0 är single-threaded apartment (STA) standard.</span><span class="sxs-lookup"><span data-stu-id="4e831-147">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="4e831-148">I PowerShell 2.0 är inneslutning för flera trådar (MTA) standard.</span><span class="sxs-lookup"><span data-stu-id="4e831-148">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="4e831-149">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="4e831-149">-Version <PowerShell Version></span></span>

<span data-ttu-id="4e831-150">Startar den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e831-150">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="4e831-151">Den version som du anger måste installeras på systemet.</span><span class="sxs-lookup"><span data-stu-id="4e831-151">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="4e831-152">Om PowerShell 3.0 är installerad på datorn, är giltiga värden ”2.0” och ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="4e831-152">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="4e831-153">Standardvärdet är ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="4e831-153">The default value is "3.0".</span></span>

<span data-ttu-id="4e831-154">Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”.</span><span class="sxs-lookup"><span data-stu-id="4e831-154">If PowerShell 3.0 isn't installed, the only valid value is "2.0".</span></span> <span data-ttu-id="4e831-155">Andra värden ignoreras.</span><span class="sxs-lookup"><span data-stu-id="4e831-155">Other values are ignored.</span></span>

<span data-ttu-id="4e831-156">Mer information finns i [installera Windows PowerShell](../../setup/installing-windows-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="4e831-156">For more information, see [Installing Windows PowerShell](../../setup/installing-windows-powershell.md).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="4e831-157">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="4e831-157">-WindowStyle <Window style></span></span>

<span data-ttu-id="4e831-158">Anger formatmallen fönster för sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e831-158">Sets the window style for the session.</span></span> <span data-ttu-id="4e831-159">Giltiga värden är Normal, minimerat, maximerat och dold.</span><span class="sxs-lookup"><span data-stu-id="4e831-159">Valid values are Normal, Minimized, Maximized, and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="4e831-160">-Kommandot</span><span class="sxs-lookup"><span data-stu-id="4e831-160">-Command</span></span>

<span data-ttu-id="4e831-161">Kör de angivna kommandon (med några parametrar) som om de har skrivits i PowerShell-Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="4e831-161">Executes the specified commands (with any parameters) as though they were typed at the PowerShell command prompt.</span></span> <span data-ttu-id="4e831-162">Efter körning, PowerShell avslutas om inte den `-NoExit` parameter har angetts.</span><span class="sxs-lookup"><span data-stu-id="4e831-162">After execution, PowerShell exits unless the `-NoExit` parameter is specified.</span></span>
<span data-ttu-id="4e831-163">Text efter `-Command` skickas som en enda kommandorad till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e831-163">Any text after `-Command` is sent as a single command line to PowerShell.</span></span> <span data-ttu-id="4e831-164">Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript.</span><span class="sxs-lookup"><span data-stu-id="4e831-164">This is different from how `-File` handles parameters sent to a script.</span></span>

<span data-ttu-id="4e831-165">Värdet för kommandot kan vara ”-”, en sträng.</span><span class="sxs-lookup"><span data-stu-id="4e831-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="4e831-166">eller ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="4e831-166">or a script block.</span></span> <span data-ttu-id="4e831-167">Om värdet för kommandot är ”-”, kommandotexten läses från kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="4e831-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="4e831-168">Skriptblocken måste stå inom klamrar ({}).</span><span class="sxs-lookup"><span data-stu-id="4e831-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="4e831-169">Du kan ange ett skriptblock endast när du kör PowerShell.exe i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e831-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="4e831-170">Resultatet av skriptet returneras till överordnade gränssnittet som avserialiserade XML-objekt, inte live-objekt.</span><span class="sxs-lookup"><span data-stu-id="4e831-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="4e831-171">Om värdet för kommandot är en sträng **kommandot** måste anges som sista parameter i kommandot eftersom några tecken har angett när kommandot tolkas som kommandoradsargument.</span><span class="sxs-lookup"><span data-stu-id="4e831-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="4e831-172">Använd format för att skriva en sträng som kör ett PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="4e831-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="4e831-173">Citattecken anger en sträng och invoke-operatorn (&) gör att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="4e831-173">The quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="4e831-174">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="4e831-174">-Help, -?, /?</span></span>

<span data-ttu-id="4e831-175">Visar syntaxen för powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="4e831-175">Shows the syntax of powershell.exe.</span></span> <span data-ttu-id="4e831-176">Om du skriver ett PowerShell.exe-kommando i PowerShell, Lägg till åtkomstgruppen kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/).</span><span class="sxs-lookup"><span data-stu-id="4e831-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="4e831-177">Du kan använda ett bindestreck eller snedstreck i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="4e831-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="4e831-178">Felsökningsmeddelande: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="4e831-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="4e831-179">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4e831-179">EXAMPLES</span></span>

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
