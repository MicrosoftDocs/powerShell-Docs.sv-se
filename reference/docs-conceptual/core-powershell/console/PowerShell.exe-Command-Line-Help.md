---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "PowerShell.exe hjälpen för kommandoraden"
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 262c21e44e509746314ed44d91bb3de16a4b854b
ms.sourcegitcommit: 4807ab554d55fdee499980835bcc279368b1df68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2017
---
# <a name="powershellexe-command-line-help"></a><span data-ttu-id="e43c6-103">PowerShell.exe hjälp</span><span class="sxs-lookup"><span data-stu-id="e43c6-103">PowerShell.exe Command-Line Help</span></span>
<span data-ttu-id="e43c6-104">Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-104">a Windows PowerShell session.</span></span> <span data-ttu-id="e43c6-105">Du kan starta en PowerShell-session från kommandoraden av ett annat verktyg, till exempel Cmd.exe, med hjälp av PowerShell.exe eller använda den på PowerShell-kommandoraden för att starta en ny session.</span><span class="sxs-lookup"><span data-stu-id="e43c6-105">You can use PowerShell.exe to start a PowerShell session from the command line of another tool, such as Cmd.exe, or use it at the PowerShell command line to start a new session.</span></span> <span data-ttu-id="e43c6-106">Använda parametrar för att anpassa sessionen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-106">Use the parameters to customize the session.</span></span>

## <a name="syntax"></a><span data-ttu-id="e43c6-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e43c6-107">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e43c6-108">Parametrar</span><span class="sxs-lookup"><span data-stu-id="e43c6-108">Parameters</span></span>

### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="e43c6-109">-EncodedCommand<Base64EncodedCommand></span><span class="sxs-lookup"><span data-stu-id="e43c6-109">-EncodedCommand <Base64EncodedCommand></span></span>
<span data-ttu-id="e43c6-110">Accepterar en base-64-kodad strängversion av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="e43c6-110">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="e43c6-111">Använd den här parametern om du vill skicka till PowerShell-kommandon som kräver komplexa citattecken eller klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="e43c6-111">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span>

### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="e43c6-112">-ExecutionPolicy<ExecutionPolicy></span><span class="sxs-lookup"><span data-stu-id="e43c6-112">-ExecutionPolicy <ExecutionPolicy></span></span>
<span data-ttu-id="e43c6-113">Anger standardprincipen för körning för den aktuella sessionen och sparar den i $env: PSExecutionPolicyPreference miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="e43c6-113">Sets the default execution policy for the current session and saves it in the $env:PSExecutionPolicyPreference environment variable.</span></span> <span data-ttu-id="e43c6-114">Den här parametern ändras inte PowerShell-körningsprincipen som anges i registret.</span><span class="sxs-lookup"><span data-stu-id="e43c6-114">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="e43c6-115">Mer information om principer för körning av PowerShell, inklusive en lista över giltiga värden finns about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span><span class="sxs-lookup"><span data-stu-id="e43c6-115">For information about PowerShell execution policies, including a list of valid values, see about_Execution_Policies (http://go.microsoft.com/fwlink/?LinkID=135170).</span></span>

### <a name="-file-filepath-parameters"></a><span data-ttu-id="e43c6-116">-Filen <FilePath> \[ <Parameters>]</span><span class="sxs-lookup"><span data-stu-id="e43c6-116">-File <FilePath> \[<Parameters>]</span></span>
<span data-ttu-id="e43c6-117">Kör det angivna skriptet i den lokala omfattningen (”punkt-källkod”), så att de funktioner och variabler som skapas är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-117">Runs the specified script in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="e43c6-118">Ange sökväg till skriptfilen och eventuella parametrar.</span><span class="sxs-lookup"><span data-stu-id="e43c6-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="e43c6-119">**Filen** måste vara den sista parametern i kommandot, eftersom alla tecken skrev efter den **filen** parameternamnet tolkas som sökväg till skriptfilen följt av skriptparametrarna och deras värden.</span><span class="sxs-lookup"><span data-stu-id="e43c6-119">**File** must be the last parameter in the command, because all characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters and their values.</span></span>

<span data-ttu-id="e43c6-120">Du kan inkludera parametrarna för ett skript och parametervärden, i värdet för den **filen** parameter.</span><span class="sxs-lookup"><span data-stu-id="e43c6-120">You can include the parameters of a script, and parameter values, in the value of the **File** parameter.</span></span> <span data-ttu-id="e43c6-121">Till exempel: `-File .\Get-Script.ps1 -Domain Central` Observera att parametrar som skickas till skriptet skickas som literal strängar (efter tolkning av den aktuella shell).</span><span class="sxs-lookup"><span data-stu-id="e43c6-121">For example: `-File .\Get-Script.ps1 -Domain Central` Note that parameters passed to the script are passed as literal strings (after interpretation by the current shell).</span></span>
<span data-ttu-id="e43c6-122">Till exempel om du är i cmd.exe och vill skicka ett miljövariabelvärde du skulle använda cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` om du skulle använda PowerShell-syntax och sedan i det här exemplet i skriptet kan få literalen ”$env: windir” och inte värdet för som miljövariabeln:`powershell -File .\test.ps1 -Sample $env:windir`</span><span class="sxs-lookup"><span data-stu-id="e43c6-122">For example, if you are in cmd.exe and want to pass an environment variable value, you would use the cmd.exe syntax: `powershell -File .\test.ps1 -Sample %windir%` If you were to use PowerShell syntax, then in this example your script would receive the literal "$env:windir" and not the value of that environmental variable: `powershell -File .\test.ps1 -Sample $env:windir`</span></span>

<span data-ttu-id="e43c6-123">Normalt är parametrarna växel för ett skript ingår eller utelämnas.</span><span class="sxs-lookup"><span data-stu-id="e43c6-123">Typically, the switch parameters of a script are either included or omitted.</span></span> <span data-ttu-id="e43c6-124">Till exempel följande kommando använder den **alla** parametern i Get-Script.ps1 skriptfil:`-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="e43c6-124">For example, the following command uses the **All** parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

### <a name="-inputformat-text--xml"></a><span data-ttu-id="e43c6-125">\-InputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e43c6-125">\-InputFormat {Text | XML}</span></span>
<span data-ttu-id="e43c6-126">Beskriver formatet för data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e43c6-126">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="e43c6-127">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="e43c6-127">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-mta"></a><span data-ttu-id="e43c6-128">-Mta</span><span class="sxs-lookup"><span data-stu-id="e43c6-128">-Mta</span></span>
<span data-ttu-id="e43c6-129">Startar PowerShell med hjälp av en flertrådad inneslutning.</span><span class="sxs-lookup"><span data-stu-id="e43c6-129">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="e43c6-130">Den här parametern introduceras i PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="e43c6-130">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e43c6-131">I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="e43c6-131">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e43c6-132">I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.</span><span class="sxs-lookup"><span data-stu-id="e43c6-132">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-noexit"></a><span data-ttu-id="e43c6-133">-NoExit</span><span class="sxs-lookup"><span data-stu-id="e43c6-133">-NoExit</span></span>
<span data-ttu-id="e43c6-134">Inte avslutas när du har kört startkommandon.</span><span class="sxs-lookup"><span data-stu-id="e43c6-134">Does not exit after running startup commands.</span></span>

### <a name="-nologo"></a><span data-ttu-id="e43c6-135">-NoLogo</span><span class="sxs-lookup"><span data-stu-id="e43c6-135">-NoLogo</span></span>
<span data-ttu-id="e43c6-136">Döljer copyright banderoll vid start.</span><span class="sxs-lookup"><span data-stu-id="e43c6-136">Hides the copyright banner at startup.</span></span>

### <a name="-noninteractive"></a><span data-ttu-id="e43c6-137">-Icke-interaktiv</span><span class="sxs-lookup"><span data-stu-id="e43c6-137">-NonInteractive</span></span>
<span data-ttu-id="e43c6-138">Inte innebär en interaktiv prompt för användaren.</span><span class="sxs-lookup"><span data-stu-id="e43c6-138">Does not present an interactive prompt to the user.</span></span>

### <a name="-noprofile"></a><span data-ttu-id="e43c6-139">-NoProfile</span><span class="sxs-lookup"><span data-stu-id="e43c6-139">-NoProfile</span></span>
<span data-ttu-id="e43c6-140">Inte att läsa in PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="e43c6-140">Does not load the PowerShell profile.</span></span>

### <a name="-outputformat-text--xml"></a><span data-ttu-id="e43c6-141">-OutputFormat {Text | XML}</span><span class="sxs-lookup"><span data-stu-id="e43c6-141">-OutputFormat {Text | XML}</span></span>
<span data-ttu-id="e43c6-142">Avgör hur utdata från PowerShell är formaterad.</span><span class="sxs-lookup"><span data-stu-id="e43c6-142">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="e43c6-143">Giltiga värden är ”Text” (textsträngar) eller ”XML” (serialiserade CLIXML format).</span><span class="sxs-lookup"><span data-stu-id="e43c6-143">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-psconsolefile-filepath"></a><span data-ttu-id="e43c6-144">-PSConsoleFile<FilePath></span><span class="sxs-lookup"><span data-stu-id="e43c6-144">-PSConsoleFile <FilePath></span></span>
<span data-ttu-id="e43c6-145">Läser in den angivna filen i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-145">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="e43c6-146">Ange sökvägen och filnamnet för konsolen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-146">Enter the path and name of the console file.</span></span> <span data-ttu-id="e43c6-147">Så här skapar du en MMC-konsol på [Export konsolen](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e43c6-147">To create a console file, use the [Export-Console](https://technet.microsoft.com/en-us/library/4bab1c02-9e61-4aaf-9957-11d1934ef4ef) cmdlet in PowerShell.</span></span>

### <a name="-sta"></a><span data-ttu-id="e43c6-148">-Sta</span><span class="sxs-lookup"><span data-stu-id="e43c6-148">-Sta</span></span>
<span data-ttu-id="e43c6-149">Startar PowerShell med hjälp av en enkeltrådad inneslutning.</span><span class="sxs-lookup"><span data-stu-id="e43c6-149">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="e43c6-150">I PowerShell 3.0 används enkeltrådad inneslutning (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="e43c6-150">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span> <span data-ttu-id="e43c6-151">I PowerShell 2.0 används inneslutning för flera trådar (MTA) som standard.</span><span class="sxs-lookup"><span data-stu-id="e43c6-151">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span>

### <a name="-version-powershell-version"></a><span data-ttu-id="e43c6-152">-Version<PowerShell Version></span><span class="sxs-lookup"><span data-stu-id="e43c6-152">-Version <PowerShell Version></span></span>
<span data-ttu-id="e43c6-153">Startar den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e43c6-153">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="e43c6-154">Den version som du anger måste installeras på datorn.</span><span class="sxs-lookup"><span data-stu-id="e43c6-154">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="e43c6-155">Om PowerShell 3.0 är installerat på datorn, är giltiga värden ”2.0” och ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="e43c6-155">If PowerShell 3.0 is installed on the computer, valid values are "2.0" and "3.0".</span></span> <span data-ttu-id="e43c6-156">Standardvärdet är ”3.0”.</span><span class="sxs-lookup"><span data-stu-id="e43c6-156">The default value is "3.0".</span></span>

<span data-ttu-id="e43c6-157">Om PowerShell 3.0 inte är installerad, är det enda giltiga värdet ”2.0”.</span><span class="sxs-lookup"><span data-stu-id="e43c6-157">If PowerShell 3.0 is not installed, the only valid value is "2.0".</span></span> <span data-ttu-id="e43c6-158">Andra värden ignoreras.</span><span class="sxs-lookup"><span data-stu-id="e43c6-158">Other values are ignored.</span></span>

<span data-ttu-id="e43c6-159">Mer information finns i ”installera PowerShell” i den [komma igång med PowerShell [gamla MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span><span class="sxs-lookup"><span data-stu-id="e43c6-159">For more information, see "Installing PowerShell" in the [Getting Started with PowerShell [OLD MSDN]](https://technet.microsoft.com/en-us/library/69555d95-b481-43e1-86e7-b46d68b3e2dd).</span></span>

### <a name="-windowstyle-window-style"></a><span data-ttu-id="e43c6-160">-WindowStyle<Window style></span><span class="sxs-lookup"><span data-stu-id="e43c6-160">-WindowStyle <Window style></span></span>
<span data-ttu-id="e43c6-161">Anger fönsterformatet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="e43c6-161">Sets the window style for the session.</span></span> <span data-ttu-id="e43c6-162">Giltiga värden är Normal, minimerat, maximerat och dold.</span><span class="sxs-lookup"><span data-stu-id="e43c6-162">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-command"></a><span data-ttu-id="e43c6-163">-Kommandot</span><span class="sxs-lookup"><span data-stu-id="e43c6-163">-Command</span></span>
<span data-ttu-id="e43c6-164">Kör angivet kommando (och eventuella parametrar) som om de har skrivits i PowerShell-Kommandotolken och sedan avslutas, såvida inte parametern NoExit har angetts.</span><span class="sxs-lookup"><span data-stu-id="e43c6-164">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the NoExit parameter is specified.</span></span>
<span data-ttu-id="e43c6-165">I princip alla text efter `-Command` skickas som en enda kommandorad till PowerShell (Detta skiljer sig från hur `-File` hanterar parametrar som skickas till ett skript).</span><span class="sxs-lookup"><span data-stu-id="e43c6-165">Essentially, any text after `-Command` is sent as a single command line to PowerShell (this is different from how `-File` handles parameters sent to a script).</span></span>

<span data-ttu-id="e43c6-166">Värdet för kommandot kan vara ”-”, en sträng.</span><span class="sxs-lookup"><span data-stu-id="e43c6-166">The value of Command can be "-", a string.</span></span> <span data-ttu-id="e43c6-167">eller ett skriptblock.</span><span class="sxs-lookup"><span data-stu-id="e43c6-167">or a script block.</span></span> <span data-ttu-id="e43c6-168">Om värdet för kommandot är ”-”, kommandotexten läses från standardindata.</span><span class="sxs-lookup"><span data-stu-id="e43c6-168">If the value of Command is "-", the command text is read from standard input.</span></span>

<span data-ttu-id="e43c6-169">Skriptblocken måste stå inom klamrar ({}).</span><span class="sxs-lookup"><span data-stu-id="e43c6-169">Script blocks must be enclosed in braces ({}).</span></span> <span data-ttu-id="e43c6-170">Du kan ange ett skriptblock bara när du kör PowerShell.exe i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e43c6-170">You can specify a script block only when running PowerShell.exe in PowerShell.</span></span> <span data-ttu-id="e43c6-171">Resultaten av skriptet returneras till överordnade shell som avserialiserat XML-objekt, inte live-objekt.</span><span class="sxs-lookup"><span data-stu-id="e43c6-171">The results of the script are returned to the parent shell as deserialized XML objects, not live objects.</span></span>

<span data-ttu-id="e43c6-172">Om värdet för kommandot är en sträng, **kommandot** måste vara den sista parametern i kommandot, eftersom alla tecken angav efter kommandot tolkas som kommandoargument.</span><span class="sxs-lookup"><span data-stu-id="e43c6-172">If the value of Command is a string, **Command** must be the last parameter in the command, because any characters typed after the command are interpreted as the command arguments.</span></span>

<span data-ttu-id="e43c6-173">Använd format för att skriva en sträng som kör ett PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="e43c6-173">To write a string that runs a PowerShell command, use the format:</span></span>

```
"& {<command>}"
```

<span data-ttu-id="e43c6-174">där citattecken anger att en sträng och invoke-operatorn (&) gör att kommandot ska köras.</span><span class="sxs-lookup"><span data-stu-id="e43c6-174">where the quotation marks indicate a string and the invoke operator (&) causes the command to be executed.</span></span>

### <a name="-help---"></a><span data-ttu-id="e43c6-175">-Help-,?, /?</span><span class="sxs-lookup"><span data-stu-id="e43c6-175">-Help, -?, /?</span></span>
<span data-ttu-id="e43c6-176">Visar det här meddelandet.</span><span class="sxs-lookup"><span data-stu-id="e43c6-176">Shows this message.</span></span> <span data-ttu-id="e43c6-177">Om du skriver kommandot PowerShell.exe i PowerShell lägga kommandoparametrarna med ett bindestreck (-), inte ett snedstreck (/).</span><span class="sxs-lookup"><span data-stu-id="e43c6-177">If you are typing a PowerShell.exe command in PowerShell, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="e43c6-178">Du kan använda ett bindestreck eller snedstreck i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="e43c6-178">You can use either a hyphen or forward slash in Cmd.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="e43c6-179">Felsökningsanteckning: I PowerShell 2.0, starta vissa program i Windows PowerShell konsolen inte med en LastExitCode av 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="e43c6-179">Troubleshooting Note: In PowerShell 2.0, starting some programs in the Windows PowerShell console fails with a LastExitCode of 0xc0000142.</span></span>

## <a name="examples"></a><span data-ttu-id="e43c6-180">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e43c6-180">EXAMPLES</span></span>

```
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a Powerhell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate wayh to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```

