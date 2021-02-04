---
description: Förklarar hur du använder `pwsh` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: 25ccb20a4c19a9519bf9d2a518ef6187c2327323
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692692"
---
# <a name="about-pwsh"></a><span data-ttu-id="6e13b-104">Om pwsh</span><span class="sxs-lookup"><span data-stu-id="6e13b-104">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="6e13b-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="6e13b-105">Short Description</span></span>
<span data-ttu-id="6e13b-106">Förklarar hur du använder `pwsh` kommando rads gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6e13b-106">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="6e13b-107">Visar kommando rads parametrarna och beskriver syntaxen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-107">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="6e13b-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="6e13b-108">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="6e13b-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e13b-109">Syntax</span></span>

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a><span data-ttu-id="6e13b-110">Parametrar</span><span class="sxs-lookup"><span data-stu-id="6e13b-110">Parameters</span></span>

<span data-ttu-id="6e13b-111">Alla parametrar är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="6e13b-111">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="6e13b-112">-Fil | -f</span><span class="sxs-lookup"><span data-stu-id="6e13b-112">-File | -f</span></span>

<span data-ttu-id="6e13b-113">Om värdet för `File` är `-` , läses kommando texten från standar din information.</span><span class="sxs-lookup"><span data-stu-id="6e13b-113">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="6e13b-114">Om du kör `pwsh -File -` utan omdirigerade standar ininformation startar en vanlig session.</span><span class="sxs-lookup"><span data-stu-id="6e13b-114">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="6e13b-115">Detta är detsamma som att inte ange `File` parametern alls.</span><span class="sxs-lookup"><span data-stu-id="6e13b-115">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="6e13b-116">Detta är standard parametern om inga parametrar finns, men värden finns på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6e13b-116">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="6e13b-117">Det angivna skriptet körs i det lokala omfånget ("punkt-källad"), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-117">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="6e13b-118">Ange sökvägen till skript filen och eventuella parametrar.</span><span class="sxs-lookup"><span data-stu-id="6e13b-118">Enter the script file path and any parameters.</span></span> <span data-ttu-id="6e13b-119">Filen måste vara den sista parametern i kommandot eftersom alla tecken som skrivs efter fil parameterns namn tolkas som skript filens sökväg följt av skript parametrarna.</span><span class="sxs-lookup"><span data-stu-id="6e13b-119">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="6e13b-120">Normalt ingår eller utelämnas växel parametrarna för ett skript.</span><span class="sxs-lookup"><span data-stu-id="6e13b-120">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="6e13b-121">Följande kommando använder till exempel parametern all i Get-Script.ps1-skript filen: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="6e13b-121">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="6e13b-122">I sällsynta fall kan du behöva ange ett **booleskt** värde för en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="6e13b-122">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="6e13b-123">Om du vill ange ett **booleskt** värde för en växel parameter i värdet för **fil** parametern använder du parametern som normalt följs omedelbart av ett kolon och det booleska värdet, till exempel följande: `-File .\Get-Script.ps1 -All:$False` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-123">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="6e13b-124">Parametrar som skickas till skriptet skickas som litterala strängar efter tolkning av det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6e13b-124">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="6e13b-125">Om du till exempel är i `cmd.exe` och vill skicka ett miljö variabel värde använder du `cmd.exe` syntaxen: `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="6e13b-125">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="6e13b-126">Däremot körs `pwsh -File .\test.ps1 -TestParam $env:windir` i `cmd.exe` resulterar i skriptet som tar emot en litteral sträng `$env:windir` eftersom det inte har någon speciell betydelse för det aktuella `cmd.exe` gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6e13b-126">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="6e13b-127">`$env:windir`Formatet för miljö variabel referens _kan_ användas i en **kommando** parameter, eftersom den tolkas som PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="6e13b-127">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="6e13b-128">Om du vill köra samma kommando från ett _kommando skript_ använder du `%~dp0` i stället för `.\` eller `$PSScriptRoot` för att representera den aktuella körnings katalogen: `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-128">Similarly, if you want to execute the same command from a _Batch script_, you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="6e13b-129">Om du i stället använde `.\test.ps1` , skulle PowerShell utlösa ett fel eftersom det inte går att hitta den litterala sökvägen `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="6e13b-129">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="6e13b-130">När skript filen slutar med ett `exit` kommando, anges process avslutnings koden till det numeriska argument som används med `exit` kommandot.</span><span class="sxs-lookup"><span data-stu-id="6e13b-130">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="6e13b-131">Vid normal avslutning är slut koden alltid `0` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-131">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="6e13b-132">Precis som `-Command` när ett skript avslutas, anges avslutnings koden till `1` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-132">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="6e13b-133">Men till skillnad från `-Command` , när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd> , är slut koden `0` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-133">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="6e13b-134">-Kommando | -c</span><span class="sxs-lookup"><span data-stu-id="6e13b-134">-Command | -c</span></span>

<span data-ttu-id="6e13b-135">Kör de angivna kommandona (och alla parametrar) som om de skrevs i PowerShell-Kommandotolken och sedan avslutas, om inte `NoExit` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="6e13b-135">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="6e13b-136">Värdet för **kommandot** kan vara `-` , ett skript block eller en sträng.</span><span class="sxs-lookup"><span data-stu-id="6e13b-136">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="6e13b-137">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="6e13b-137">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="6e13b-138">**Kommando** parametern accepterar bara ett-skript block för körning när det kan identifiera värdet som skickas till **kommandot** som en **script block** -typ.</span><span class="sxs-lookup"><span data-stu-id="6e13b-138">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="6e13b-139">Detta är _endast_ möjligt när du kör `pwsh` från en annan PowerShell-värd.</span><span class="sxs-lookup"><span data-stu-id="6e13b-139">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="6e13b-140">**Script block** -typen kan finnas i en befintlig variabel, returneras från ett uttryck eller parsas av PowerShell-värden som ett litteralt-skript block som omges av klammerparenteser ( `{}` ), innan de skickas till `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-140">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="6e13b-141">I finns `cmd.exe` det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng.</span><span class="sxs-lookup"><span data-stu-id="6e13b-141">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="6e13b-142">Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.</span><span class="sxs-lookup"><span data-stu-id="6e13b-142">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="6e13b-143">En sträng som skickas till **kommandot** körs fortfarande som PowerShell-kod, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-143">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="6e13b-144">Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="6e13b-144">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="6e13b-145">Om värdet för **kommandot** är en sträng måste **kommandot** vara den sista parametern för pwsh, eftersom alla argument som följer tolkas som en del av kommandot som ska köras.</span><span class="sxs-lookup"><span data-stu-id="6e13b-145">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="6e13b-146">När de anropas i en befintlig PowerShell-session returneras resultatet till det överordnade gränssnittet som avserialiserade XML-objekt, inte aktiva objekt.</span><span class="sxs-lookup"><span data-stu-id="6e13b-146">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="6e13b-147">För andra gränssnitt returneras resultaten som strängar.</span><span class="sxs-lookup"><span data-stu-id="6e13b-147">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="6e13b-148">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="6e13b-148">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="6e13b-149">Du måste omdirigera standar din information när du använder **kommando** parametern med standar din information.</span><span class="sxs-lookup"><span data-stu-id="6e13b-149">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="6e13b-150">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6e13b-150">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="6e13b-151">I det här exemplet skapas följande utdata:</span><span class="sxs-lookup"><span data-stu-id="6e13b-151">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="6e13b-152">Avslutnings koden för processen avgörs av status för det sista (körda) kommandot i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="6e13b-152">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="6e13b-153">Slut koden är `0` när `$?` är `$true` eller `1` när `$?` är `$false` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-153">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="6e13b-154">Om det sista kommandot är ett externt program eller ett PowerShell-skript som explicit anger en slut kod som `0` inte `1` är eller, konverteras slut koden till `1` för process avslutnings kod.</span><span class="sxs-lookup"><span data-stu-id="6e13b-154">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="6e13b-155">Om du vill bevara den angivna slut koden lägger du till den `exit $LASTEXITCODE` i kommando strängen eller skript blocket.</span><span class="sxs-lookup"><span data-stu-id="6e13b-155">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="6e13b-156">På samma sätt returneras värdet 1 när ett skript avslutas (körnings utrymme), till exempel ett `throw` eller `-ErrorAction Stop` , inträffar eller när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6e13b-156">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="6e13b-157">-ConfigurationName | – config</span><span class="sxs-lookup"><span data-stu-id="6e13b-157">-ConfigurationName | -config</span></span>

<span data-ttu-id="6e13b-158">Anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="6e13b-158">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="6e13b-159">Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="6e13b-159">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="6e13b-160">Exempel: `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="6e13b-160">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="6e13b-161">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="6e13b-161">-CustomPipeName</span></span>

<span data-ttu-id="6e13b-162">Anger det namn som ska användas för ytterligare en IPC-Server (namngiven pipe) som används för fel sökning och annan Cross-process-kommunikation.</span><span class="sxs-lookup"><span data-stu-id="6e13b-162">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="6e13b-163">Detta erbjuder en förutsägbar mekanism för att ansluta till andra PowerShell-instanser.</span><span class="sxs-lookup"><span data-stu-id="6e13b-163">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="6e13b-164">Används vanligt vis med parametern **CustomPipeName** på `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-164">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="6e13b-165">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="6e13b-165">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="6e13b-166">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6e13b-166">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="6e13b-167">-EncodedCommand | -e | – EC</span><span class="sxs-lookup"><span data-stu-id="6e13b-167">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="6e13b-168">Accepterar en Base64-kodad sträng version av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="6e13b-168">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="6e13b-169">Använd den här parametern för att skicka kommandon till PowerShell som kräver komplex, kapslad citat tecken.</span><span class="sxs-lookup"><span data-stu-id="6e13b-169">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="6e13b-170">Base64-representationen måste vara en UTF-16LE-kodad sträng.</span><span class="sxs-lookup"><span data-stu-id="6e13b-170">The Base64 representation must be a UTF-16LE encoded string.</span></span>

<span data-ttu-id="6e13b-171">Exempel:</span><span class="sxs-lookup"><span data-stu-id="6e13b-171">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="6e13b-172">-ExecutionPolicy | – ex | -EP</span><span class="sxs-lookup"><span data-stu-id="6e13b-172">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="6e13b-173">Anger standard körnings principen för den aktuella sessionen och sparar den i `$env:PSExecutionPolicyPreference` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="6e13b-173">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="6e13b-174">Den här parametern ändrar inte permanent konfigurerade körnings principer.</span><span class="sxs-lookup"><span data-stu-id="6e13b-174">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="6e13b-175">Den här parametern gäller endast för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="6e13b-175">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="6e13b-176">`$env:PSExecutionPolicyPreference`Miljövariabeln finns inte på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="6e13b-176">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---inp---if"></a><span data-ttu-id="6e13b-177">-InputFormat | -INP | – om</span><span class="sxs-lookup"><span data-stu-id="6e13b-177">-InputFormat | -inp | -if</span></span>

<span data-ttu-id="6e13b-178">Beskriver formatet på data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e13b-178">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="6e13b-179">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="6e13b-179">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="6e13b-180">– Interaktiv | -i</span><span class="sxs-lookup"><span data-stu-id="6e13b-180">-Interactive | -i</span></span>

<span data-ttu-id="6e13b-181">Presentera en interaktiv prompt till användaren.</span><span class="sxs-lookup"><span data-stu-id="6e13b-181">Present an interactive prompt to the user.</span></span> <span data-ttu-id="6e13b-182">Invertering för en ej interaktiv parameter.</span><span class="sxs-lookup"><span data-stu-id="6e13b-182">Inverse for NonInteractive parameter.</span></span>

### <a name="-login---l"></a><span data-ttu-id="6e13b-183">-Inloggning | -l</span><span class="sxs-lookup"><span data-stu-id="6e13b-183">-Login | -l</span></span>

<span data-ttu-id="6e13b-184">På Linux och macOS startar PowerShell som ett inloggnings gränssnitt med hjälp av/bin/sh för att köra inloggnings profiler som/etc/profile och ~/.Profile.</span><span class="sxs-lookup"><span data-stu-id="6e13b-184">On Linux and macOS, starts PowerShell as a login shell, using /bin/sh to execute login profiles such as /etc/profile and ~/.profile.</span></span>
<span data-ttu-id="6e13b-185">I Windows gör den här växeln ingenting.</span><span class="sxs-lookup"><span data-stu-id="6e13b-185">On Windows, this switch does nothing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6e13b-186">Den här parametern måste komma först för att starta PowerShell som ett inloggnings gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="6e13b-186">This parameter must come first to start PowerShell as a login shell.</span></span>
> <span data-ttu-id="6e13b-187">Att skicka den här parametern i en annan position ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6e13b-187">Passing this parameter in another position will be ignored.</span></span>

<span data-ttu-id="6e13b-188">Så här konfigurerar du `pwsh` som inloggnings gränssnitt på UNIX-liknande operativ system:</span><span class="sxs-lookup"><span data-stu-id="6e13b-188">To set up `pwsh` as the login shell on UNIX-like operating systems:</span></span>

- <span data-ttu-id="6e13b-189">Kontrol lera att den fullständiga absoluta sökvägen till `pwsh` visas under `/etc/shells`</span><span class="sxs-lookup"><span data-stu-id="6e13b-189">Verify that the full absolute path to `pwsh` is listed under `/etc/shells`</span></span>
  - <span data-ttu-id="6e13b-190">Den här sökvägen är vanligt vis något som liknar `/usr/bin/pwsh` i Linux eller `/usr/local/bin/pwsh` MacOS</span><span class="sxs-lookup"><span data-stu-id="6e13b-190">This path is usually something like `/usr/bin/pwsh` on Linux or `/usr/local/bin/pwsh` on macOS</span></span>
  - <span data-ttu-id="6e13b-191">Med vissa installations metoder kommer den här posten att läggas till automatiskt vid installationen</span><span class="sxs-lookup"><span data-stu-id="6e13b-191">With some installation methods, this entry will be added automatically at installation time</span></span>
  - <span data-ttu-id="6e13b-192">Om `pwsh` inte finns i `/etc/shells` använder du en redigerare för att lägga till sökvägen till `pwsh` på den sista raden.</span><span class="sxs-lookup"><span data-stu-id="6e13b-192">If `pwsh` is not present in `/etc/shells`, use an editor to append the path to `pwsh` on the last line.</span></span> <span data-ttu-id="6e13b-193">Detta kräver förhöjd behörighet att redigera.</span><span class="sxs-lookup"><span data-stu-id="6e13b-193">This requires elevated privileges to edit.</span></span>
- <span data-ttu-id="6e13b-194">Använd [chsh](https://linux.die.net/man/1/chsh) -verktyget för att ange den aktuella användarens gränssnitt till `pwsh` :</span><span class="sxs-lookup"><span data-stu-id="6e13b-194">Use the [chsh](https://linux.die.net/man/1/chsh) utility to set your current user's shell to `pwsh`:</span></span>

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> <span data-ttu-id="6e13b-195">Inställningen `pwsh` som inloggnings gränssnitt stöds för närvarande inte i Windows-undersystemet för Linux (Wsl) och försöker ange `pwsh` som inloggnings gränssnitt. det kan leda till att det inte går att starta Wsl interaktivt.</span><span class="sxs-lookup"><span data-stu-id="6e13b-195">Setting `pwsh` as the login shell is currently not supported on Windows Subsystem for Linux (WSL), and attempting to set `pwsh` as the login shell there may lead to being unable to start WSL interactively.</span></span>

### <a name="-mta"></a><span data-ttu-id="6e13b-196">-MTA</span><span class="sxs-lookup"><span data-stu-id="6e13b-196">-MTA</span></span>

<span data-ttu-id="6e13b-197">Starta PowerShell med en flertrådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="6e13b-197">Start PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="6e13b-198">Den här växeln är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="6e13b-198">This switch is only available on Windows.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="6e13b-199">-Noexit | -noe</span><span class="sxs-lookup"><span data-stu-id="6e13b-199">-NoExit | -noe</span></span>

<span data-ttu-id="6e13b-200">Avslutas inte när du har kört Start kommandon.</span><span class="sxs-lookup"><span data-stu-id="6e13b-200">Does not exit after running startup commands.</span></span>

<span data-ttu-id="6e13b-201">Exempel: `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="6e13b-201">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="6e13b-202">-Nologo typ | -nol</span><span class="sxs-lookup"><span data-stu-id="6e13b-202">-NoLogo | -nol</span></span>

<span data-ttu-id="6e13b-203">Döljer Copyright-banderollen vid start av interaktiva sessioner.</span><span class="sxs-lookup"><span data-stu-id="6e13b-203">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="6e13b-204">-Ej interaktiv | -noni</span><span class="sxs-lookup"><span data-stu-id="6e13b-204">-NonInteractive | -noni</span></span>

<span data-ttu-id="6e13b-205">Visar inte en interaktiv prompt till användaren.</span><span class="sxs-lookup"><span data-stu-id="6e13b-205">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="6e13b-206">Alla försök att använda interaktiva funktioner, t `Read-Host` . ex. bekräftelser, resulterar i instruktionen-avslutar fel.</span><span class="sxs-lookup"><span data-stu-id="6e13b-206">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="6e13b-207">-Noprofil | – NOP</span><span class="sxs-lookup"><span data-stu-id="6e13b-207">-NoProfile | -nop</span></span>

<span data-ttu-id="6e13b-208">Läser inte in PowerShell-profilerna.</span><span class="sxs-lookup"><span data-stu-id="6e13b-208">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="6e13b-209">-OutputFormat | -o | – av</span><span class="sxs-lookup"><span data-stu-id="6e13b-209">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="6e13b-210">Anger hur utdata från PowerShell formateras.</span><span class="sxs-lookup"><span data-stu-id="6e13b-210">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="6e13b-211">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="6e13b-211">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="6e13b-212">Exempel: `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="6e13b-212">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="6e13b-213">När du anropar med en PowerShell-session får du avserialiserade objekt som utdata i stället för vanliga strängar.</span><span class="sxs-lookup"><span data-stu-id="6e13b-213">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="6e13b-214">Vid anrop från andra gränssnitt är utdata sträng data formaterade som CLIXML text.</span><span class="sxs-lookup"><span data-stu-id="6e13b-214">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="6e13b-215">-SettingsFile | – inställningar</span><span class="sxs-lookup"><span data-stu-id="6e13b-215">-SettingsFile | -settings</span></span>

<span data-ttu-id="6e13b-216">Åsidosätter den systemomfattande `powershell.config.json` inställnings filen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-216">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="6e13b-217">Som standard läses systemtäckande inställningar från `powershell.config.json` i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-217">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="6e13b-218">Observera att de här inställningarna inte används av slut punkten som anges av `-ConfigurationName` argumentet.</span><span class="sxs-lookup"><span data-stu-id="6e13b-218">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="6e13b-219">Exempel: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="6e13b-219">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="6e13b-220">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="6e13b-220">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="6e13b-221">Används i sshd_config för att köra PowerShell som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="6e13b-221">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="6e13b-222">Den är inte avsedd eller stöds inte för någon annan användning.</span><span class="sxs-lookup"><span data-stu-id="6e13b-222">It is not intended or supported for any other use.</span></span>

### <a name="-sta"></a><span data-ttu-id="6e13b-223">– STA</span><span class="sxs-lookup"><span data-stu-id="6e13b-223">-STA</span></span>

<span data-ttu-id="6e13b-224">Starta PowerShell med en enkel trådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="6e13b-224">Start PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="6e13b-225">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-225">This is the default.</span></span> <span data-ttu-id="6e13b-226">Den här växeln är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="6e13b-226">This switch is only available on Windows.</span></span>

### <a name="-version---v"></a><span data-ttu-id="6e13b-227">-Version | -v</span><span class="sxs-lookup"><span data-stu-id="6e13b-227">-Version | -v</span></span>

<span data-ttu-id="6e13b-228">Visar versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6e13b-228">Displays the version of PowerShell.</span></span> <span data-ttu-id="6e13b-229">Ytterligare parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6e13b-229">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="6e13b-230">-WindowStyle | – w</span><span class="sxs-lookup"><span data-stu-id="6e13b-230">-WindowStyle | -w</span></span>

<span data-ttu-id="6e13b-231">Anger fönster formatet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6e13b-231">Sets the window style for the session.</span></span> <span data-ttu-id="6e13b-232">Giltiga värden är normal, minimerat, maximerat och dolt.</span><span class="sxs-lookup"><span data-stu-id="6e13b-232">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="6e13b-233">-WorkingDirectory | -WD</span><span class="sxs-lookup"><span data-stu-id="6e13b-233">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="6e13b-234">Anger den inledande arbets katalogen genom att köra vid start.</span><span class="sxs-lookup"><span data-stu-id="6e13b-234">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="6e13b-235">En giltig sökväg till PowerShell-filen stöds.</span><span class="sxs-lookup"><span data-stu-id="6e13b-235">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="6e13b-236">Om du vill starta PowerShell i din arbets katalog använder du: `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="6e13b-236">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="6e13b-237">– Hjälp,-?,/?</span><span class="sxs-lookup"><span data-stu-id="6e13b-237">-Help, -?, /?</span></span>

<span data-ttu-id="6e13b-238">Visar hjälp för `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="6e13b-238">Displays help for `pwsh`.</span></span> <span data-ttu-id="6e13b-239">Om du skriver ett pwsh-kommando i PowerShell lägga kommando parametrarna med bindestreck ( `-` ), inte ett snedstreck ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="6e13b-239">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
