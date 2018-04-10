---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Kommandoradshjälp för PowerShell.exe
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 60b6a7e310821a4092b0972b7abbdae0e2d5f738
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="f722b-103">PowerShell.exe hjälp</span><span class="sxs-lookup"><span data-stu-id="f722b-103">PowerShell.exe Command-Line Help</span></span>

<span data-ttu-id="f722b-104">Du kan starta en PowerShell-session från kommandoraden av ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session.</span><span class="sxs-lookup"><span data-stu-id="f722b-104">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="f722b-105">Använda parametrar för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="f722b-105">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="f722b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f722b-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="f722b-107">Parametrar</span><span class="sxs-lookup"><span data-stu-id="f722b-107">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="f722b-108">-EncodedCommand <Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="f722b-108">-EncodedCommand <Base64EncodedCommand></span></span>

<span data-ttu-id="f722b-109">Accepterar en base-64-kodad strängversion av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="f722b-109">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="f722b-110">Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="f722b-110">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="f722b-111">-ExecutionPolicy <ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="f722b-111">-ExecutionPolicy <ExecutionPolicy></span></span>

<span data-ttu-id="f722b-112">Anger standardprincipen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="f722b-112">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="f722b-113">Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret.</span><span class="sxs-lookup"><span data-stu-id="f722b-113">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="f722b-114">Information om principer för körning av PowerShell, inklusive en lista över giltiga värden finns [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="f722b-114">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="f722b-115">-Filen <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="f722b-115">-File <FilePath> \[<Parameters>]</span></span>

<span data-ttu-id="f722b-116">Kör det angivna skriptet i den lokala omfattningen (”punkt-källkod”), så att de funktioner och variabler som skapas är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f722b-116">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="f722b-117">Ange sökväg till skriptfilen och eventuella parametrar.</span><span class="sxs-lookup"><span data-stu-id="f722b-117">Enter the script file path and any parameters.</span></span> <span data-ttu-id="f722b-118">**Filen** måste vara den sista parametern i kommandot, eftersom alla tecken skrev efter den **filen** parameternamnet tolkas som sökväg till skriptfilen följt av skriptparametrarna och deras värden.</span><span class="sxs-lookup"><span data-stu-id="f722b-118">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="f722b-119">Du kan inkludera parametrarna för ett skript och parametervärden, i värdet för den **filen** parameter.</span><span class="sxs-lookup"><span data-stu-id="f722b-119">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="f722b-120">Till exempel: `-File .\Get-Script.ps1 -Domain Central` Observera att parametrar som skickas till skriptet skickas som literal strängar (efter tolkning av den aktuella shell).</span><span class="sxs-lookup"><span data-stu-id="f722b-120">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="f722b-121">Till exempel om du är i cmd.exe och vill skicka ett miljövariabelvärde du skulle använda cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` om du skulle använda PowerShell-syntax och sedan i det här exemplet i skriptet kan få literalen ”$env: windir” och inte värdet för som miljövariabeln: `powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="f722b-121">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="f722b-122">Normalt är parametrarna växel för ett skript ingår eller utelämnas.</span><span class="sxs-lookup"><span data-stu-id="f722b-122">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="f722b-123">Till exempel följande kommando använder den **alla** parametern i Get-Script.ps1 skriptfil: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="f722b-123">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="f722b-124">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="f722b-124">\-InputFormat {Text | XML}</span></span>

<span data-ttu-id="f722b-125">Beskriver formatet för data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f722b-125">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="f722b-126">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="f722b-126">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="f722b-127">-Mta</span><span class="sxs-lookup"><span data-stu-id="f722b-127">-Mta</span></span>

<span data-ttu-id="f722b-128">Startar PowerShell med hjälp av en flertrådad inneslutning.</span><span class="sxs-lookup"><span data-stu-id="f722b-128">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="f722b-129">Den här parametern introduceras i PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="f722b-129">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="f722b-130">I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="f722b-130">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="f722b-131">I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.</span><span class="sxs-lookup"><span data-stu-id="f722b-131">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="f722b-132">-NoExit</span><span class="sxs-lookup"><span data-stu-id="f722b-132">-NoExit</span></span>

<span data-ttu-id="f722b-133">Inte avslutas när du har kört startkommandon.</span><span class="sxs-lookup"><span data-stu-id="f722b-133">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="f722b-134">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="f722b-134">-NoLogo</span></span>

<span data-ttu-id="f722b-135">Döljer copyright banderoll vid start.</span><span class="sxs-lookup"><span data-stu-id="f722b-135">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="f722b-136">-NonInteractive</span><span class="sxs-lookup"><span data-stu-id="f722b-136">-NonInteractive</span></span>

<span data-ttu-id="f722b-137">Inte innebär en interaktiv prompt för användaren.</span><span class="sxs-lookup"><span data-stu-id="f722b-137">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="f722b-138">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="f722b-138">-NoProfile</span></span>

<span data-ttu-id="f722b-139">Inte att läsa in PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="f722b-139">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="f722b-140">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="f722b-140">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="f722b-141">Avgör hur utdata från PowerShell är formaterad.</span><span class="sxs-lookup"><span data-stu-id="f722b-141">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="f722b-142">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="f722b-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="f722b-143">-PSConsoleFile <FilePath></span><span class="sxs-lookup"><span data-stu-id="f722b-143">-PSConsoleFile <FilePath></span></span>

<span data-ttu-id="f722b-144">Läser in den angivna filen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f722b-144">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="f722b-145">Ange sökvägen och filnamnet för konsolen.</span><span class="sxs-lookup"><span data-stu-id="f722b-145">Enter the path and name of the console file.</span></span> <span data-ttu-id="f722b-146">Så här skapar du en MMC-konsol på [ `Export-Console` ](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f722b-146">To create a console file, use the [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="f722b-147">-Sta</span><span class="sxs-lookup"><span data-stu-id="f722b-147">-Sta</span></span>

<span data-ttu-id="f722b-148">Startar PowerShell med hjälp av en enkeltrådad inneslutning.</span><span class="sxs-lookup"><span data-stu-id="f722b-148">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="f722b-149">I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="f722b-149">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="f722b-150">I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.</span><span class="sxs-lookup"><span data-stu-id="f722b-150">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="f722b-151">-Version <PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="f722b-151">-Version <PowerShell Version></span></span>

<span data-ttu-id="f722b-152">Startar den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f722b-152">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="f722b-153">Den version som du anger måste installeras på datorn.</span><span class="sxs-lookup"><span data-stu-id="f722b-153">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="f722b-154">Om PowerShell 3.0 är installerat på datorn, är giltiga värden ”2.0” och ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="f722b-154">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="f722b-155">Standardvärdet är ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="f722b-155">The default value is "3.0".</span></span>

<span data-ttu-id="f722b-156">Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”.</span><span class="sxs-lookup"><span data-stu-id="f722b-156">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="f722b-157">Andra värden ignoreras.</span><span class="sxs-lookup"><span data-stu-id="f722b-157">Other values are ignored.</span></span>

<span data-ttu-id="f722b-158">Mer information finns i ”[installera Windows PowerShell](../../setup/installing-windows-powershell.md)”.</span><span class="sxs-lookup"><span data-stu-id="f722b-158">For more information, see "[Installing Windows PowerShell](../../setup/installing-windows-powershell.md)".</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="f722b-159">-WindowStyle <Window style></span><span class="sxs-lookup"><span data-stu-id="f722b-159">-WindowStyle <Window style></span></span>

<span data-ttu-id="f722b-160">Anger fönsterformatet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="f722b-160">Sets the window style for the session.</span></span> <span data-ttu-id="f722b-161">Giltiga värden är Normal, minimerat, maximerat och dold.</span><span class="sxs-lookup"><span data-stu-id="f722b-161">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="f722b-162">-Kommandot</span><span class="sxs-lookup"><span data-stu-id="f722b-162">-Command</span></span>

<span data-ttu-id="f722b-163">Kör angivet kommando (och eventuella parametrar) som om de har skrivits i PowerShell-Kommandotolken och sedan avslutas, såvida inte parametern NoExit har angetts.</span><span class="sxs-lookup"><span data-stu-id="f722b-163">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="f722b-164">I princip alla text efter `-Command` skickas som en enda kommandorad till PowerShell (Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript).</span><span class="sxs-lookup"><span data-stu-id="f722b-164">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="f722b-165">Värdet för kommandot kan vara ”-”, en sträng.</span><span class="sxs-lookup"><span data-stu-id="f722b-165">The value of Command can be "-", a string.</span></span> <span data-ttu-id="f722b-166">eller ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="f722b-166">or a script block.</span></span> <span data-ttu-id="f722b-167">Om värdet för kommandot är ”-”, kommandotexten läses från standardindata.</span><span class="sxs-lookup"><span data-stu-id="f722b-167">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="f722b-168">Skriptblocken måste stå inom klamrar ({}).</span><span class="sxs-lookup"><span data-stu-id="f722b-168">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="f722b-169">Du kan ange ett skriptblock bara när du kör PowerShell.exe i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f722b-169">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="f722b-170">Resultaten av skriptet returneras till överordnade shell som avserialiserat XML-objekt, inte live-objekt.</span><span class="sxs-lookup"><span data-stu-id="f722b-170">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="f722b-171">Om värdet för kommandot är en sträng, **kommandot** måste vara den sista parametern i kommandot, eftersom alla tecken angav efter kommandot tolkas som kommandoargument.</span><span class="sxs-lookup"><span data-stu-id="f722b-171">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="f722b-172">Använd format för att skriva en sträng som kör ett PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="f722b-172">To write a string that runs a PowerShell command, use the format:</span></span>

```powershell
"& {<command>}"
```

<span data-ttu-id="f722b-173">där citattecken anger att en sträng och invoke-operatorn (&) gör att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="f722b-173">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="f722b-174">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="f722b-174">-Help, -?, /?</span></span>

<span data-ttu-id="f722b-175">Visar det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="f722b-175">Shows this message.</span></span> <span data-ttu-id="f722b-176">Om du skriver kommandot PowerShell.exe i PowerShell lägga kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/).</span><span class="sxs-lookup"><span data-stu-id="f722b-176">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="f722b-177">Du kan använda ett bindestreck eller snedstreck i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="f722b-177">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="f722b-178">Felsökningsanteckning: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="f722b-178">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="f722b-179">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f722b-179">EXAMPLES</span></span>

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