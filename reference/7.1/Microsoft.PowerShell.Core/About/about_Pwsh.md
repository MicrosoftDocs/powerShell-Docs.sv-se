---
description: Förklarar hur du använder `pwsh` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.
keywords: powershell,cmdlet
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: c71848e327822f7cbc659310d3fa47a5a46a37a2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271718"
---
# <a name="about-pwsh"></a><span data-ttu-id="2b0c9-105">Om pwsh</span><span class="sxs-lookup"><span data-stu-id="2b0c9-105">About pwsh</span></span>

## <a name="short-description"></a><span data-ttu-id="2b0c9-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="2b0c9-106">Short Description</span></span>
<span data-ttu-id="2b0c9-107">Förklarar hur du använder `pwsh` kommando rads gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-107">Explains how to use the `pwsh` command-line interface.</span></span> <span data-ttu-id="2b0c9-108">Visar kommando rads parametrarna och beskriver syntaxen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="2b0c9-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="2b0c9-109">Long Description</span></span>

## <a name="syntax"></a><span data-ttu-id="2b0c9-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="2b0c9-110">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="2b0c9-111">Parametrar</span><span class="sxs-lookup"><span data-stu-id="2b0c9-111">Parameters</span></span>

<span data-ttu-id="2b0c9-112">Alla parametrar är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-112">All parameters are case-insensitive.</span></span>

### <a name="-file---f"></a><span data-ttu-id="2b0c9-113">-Fil | -f</span><span class="sxs-lookup"><span data-stu-id="2b0c9-113">-File | -f</span></span>

<span data-ttu-id="2b0c9-114">Om värdet för `File` är `-` , läses kommando texten från standar din information.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-114">If the value of `File` is `-`, the command text is read from standard input.</span></span>
<span data-ttu-id="2b0c9-115">Om du kör `pwsh -File -` utan omdirigerade standar ininformation startar en vanlig session.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-115">Running `pwsh -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="2b0c9-116">Detta är detsamma som att inte ange `File` parametern alls.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-116">This is the same as not specifying the `File` parameter at all.</span></span>

<span data-ttu-id="2b0c9-117">Detta är standard parametern om inga parametrar finns, men värden finns på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-117">This is the default parameter if no parameters are present but values are present in the command line.</span></span> <span data-ttu-id="2b0c9-118">Det angivna skriptet körs i det lokala omfånget ("punkt-källad"), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-118">The specified script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="2b0c9-119">Ange sökvägen till skript filen och eventuella parametrar.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-119">Enter the script file path and any parameters.</span></span> <span data-ttu-id="2b0c9-120">Filen måste vara den sista parametern i kommandot eftersom alla tecken som skrivs efter fil parameterns namn tolkas som skript filens sökväg följt av skript parametrarna.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-120">File must be the last parameter in the command, because all characters typed after the File parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="2b0c9-121">Normalt ingår eller utelämnas växel parametrarna för ett skript.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-121">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="2b0c9-122">Följande kommando använder till exempel parametern all i Get-Script.ps1-skript filen: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-122">For example, the following command uses the All parameter of the Get-Script.ps1 script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="2b0c9-123">I sällsynta fall kan du behöva ange ett **booleskt** värde för en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-123">In rare cases, you might need to provide a **Boolean** value for a switch parameter.</span></span> <span data-ttu-id="2b0c9-124">Om du vill ange ett **booleskt** värde för en växel parameter i värdet för **fil** parametern använder du parametern som normalt följs omedelbart av ett kolon och det booleska värdet, till exempel följande: `-File .\Get-Script.ps1 -All:$False` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-124">To provide a **Boolean** value for a switch parameter in the value of the **File** parameter, Use the parameter normally followed immediately by a colon and the boolean value, such as the following: `-File .\Get-Script.ps1 -All:$False`.</span></span>

<span data-ttu-id="2b0c9-125">Parametrar som skickas till skriptet skickas som litterala strängar efter tolkning av det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-125">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="2b0c9-126">Om du till exempel är i `cmd.exe` och vill skicka ett miljö variabel värde använder du `cmd.exe` syntaxen: `pwsh -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-126">For example, if you are in `cmd.exe` and want to pass an environment variable value, you would use the `cmd.exe` syntax: `pwsh -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="2b0c9-127">Däremot körs `pwsh -File .\test.ps1 -TestParam $env:windir` i `cmd.exe` resulterar i skriptet som tar emot en litteral sträng `$env:windir` eftersom det inte har någon speciell betydelse för det aktuella `cmd.exe` gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-127">In contrast, running `pwsh -File .\test.ps1 -TestParam $env:windir` in `cmd.exe` results in the script receiving the literal string `$env:windir` because it has no special meaning to the current `cmd.exe` shell.</span></span> <span data-ttu-id="2b0c9-128">`$env:windir`Formatet för miljö variabel referens _kan_ användas i en **kommando** parameter, eftersom den tolkas som PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-128">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it is interpreted as PowerShell code.</span></span>

<span data-ttu-id="2b0c9-129">Om du vill köra samma kommando från ett _kommando skript_ använder du `%~dp0` i stället för `.\` eller `$PSScriptRoot` för att representera den aktuella körnings katalogen: `pwsh -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-129">Similarly, if you want to execute the same command from a _Batch script_ , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `pwsh -File %~dp0test.ps1 -TestParam %windir%`.</span></span> <span data-ttu-id="2b0c9-130">Om du i stället använde `.\test.ps1` , skulle PowerShell utlösa ett fel eftersom det inte går att hitta den litterala sökvägen `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-130">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="2b0c9-131">När skript filen slutar med ett `exit` kommando, anges process avslutnings koden till det numeriska argument som används med `exit` kommandot.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-131">When the script file terminates with an `exit` command, the process exit code is set to the numeric argument used with the `exit` command.</span></span> <span data-ttu-id="2b0c9-132">Vid normal avslutning är slut koden alltid `0` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-132">With normal termination, the exit code is always `0`.</span></span>

<span data-ttu-id="2b0c9-133">Precis som `-Command` när ett skript avslutas, anges avslutnings koden till `1` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-133">Similar to `-Command`, when a script-terminating error occurs, the exit code is set to `1`.</span></span> <span data-ttu-id="2b0c9-134">Men till skillnad från `-Command` , när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd> , är slut koden `0` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-134">However, unlike with `-Command`, when the execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd> the exit code is `0`.</span></span>

### <a name="-command---c"></a><span data-ttu-id="2b0c9-135">-Kommando | -c</span><span class="sxs-lookup"><span data-stu-id="2b0c9-135">-Command | -c</span></span>

<span data-ttu-id="2b0c9-136">Kör de angivna kommandona (och alla parametrar) som om de skrevs i PowerShell-Kommandotolken och sedan avslutas, om inte `NoExit` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-136">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="2b0c9-137">Värdet för **kommandot** kan vara `-` , ett skript block eller en sträng.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-137">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="2b0c9-138">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-138">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="2b0c9-139">**Kommando** parametern accepterar bara ett-skript block för körning när det kan identifiera värdet som skickas till **kommandot** som en **script block** -typ.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-139">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="2b0c9-140">Detta är _endast_ möjligt när du kör `pwsh` från en annan PowerShell-värd.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-140">This is _only_ possible when running `pwsh` from another PowerShell host.</span></span> <span data-ttu-id="2b0c9-141">**Script block** -typen kan finnas i en befintlig variabel, returneras från ett uttryck eller parsas av PowerShell-värden som ett litteralt-skript block som omges av klammerparenteser ( `{}` ), innan de skickas till `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-141">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `pwsh`.</span></span>

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="2b0c9-142">I finns `cmd.exe` det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-142">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="2b0c9-143">Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-143">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="2b0c9-144">En sträng som skickas till **kommandot** körs fortfarande som PowerShell-kod, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-144">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="2b0c9-145">Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="2b0c9-145">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="2b0c9-146">Om värdet för **kommandot** är en sträng måste **kommandot** vara den sista parametern för pwsh, eftersom alla argument som följer tolkas som en del av kommandot som ska köras.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-146">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="2b0c9-147">När de anropas i en befintlig PowerShell-session returneras resultatet till det överordnade gränssnittet som avserialiserade XML-objekt, inte aktiva objekt.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-147">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="2b0c9-148">För andra gränssnitt returneras resultaten som strängar.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-148">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="2b0c9-149">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-149">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="2b0c9-150">Du måste omdirigera standar din information när du använder **kommando** parametern med standar din information.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-150">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="2b0c9-151">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="2b0c9-151">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="2b0c9-152">I det här exemplet skapas följande utdata:</span><span class="sxs-lookup"><span data-stu-id="2b0c9-152">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="2b0c9-153">Avslutnings koden för processen avgörs av status för det sista (körda) kommandot i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-153">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="2b0c9-154">Slut koden är `0` när `$?` är `$true` eller `1` när `$?` är `$false` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-154">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="2b0c9-155">Om det sista kommandot är ett externt program eller ett PowerShell-skript som explicit anger en slut kod som `0` inte `1` är eller, konverteras slut koden till `1` för process avslutnings kod.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-155">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="2b0c9-156">Om du vill bevara den angivna slut koden lägger du till den `exit $LASTEXITCODE` i kommando strängen eller skript blocket.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-156">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="2b0c9-157">På samma sätt returneras värdet 1 när ett skript avslutas (körnings utrymme), till exempel ett `throw` eller `-ErrorAction Stop` , inträffar eller när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-157">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

### <a name="-configurationname---config"></a><span data-ttu-id="2b0c9-158">-ConfigurationName | – config</span><span class="sxs-lookup"><span data-stu-id="2b0c9-158">-ConfigurationName | -config</span></span>

<span data-ttu-id="2b0c9-159">Anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-159">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="2b0c9-160">Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-160">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

<span data-ttu-id="2b0c9-161">Exempel: `pwsh -ConfigurationName AdminRoles`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-161">Example: `pwsh -ConfigurationName AdminRoles`</span></span>

### <a name="-custompipename"></a><span data-ttu-id="2b0c9-162">-CustomPipeName</span><span class="sxs-lookup"><span data-stu-id="2b0c9-162">-CustomPipeName</span></span>

<span data-ttu-id="2b0c9-163">Anger det namn som ska användas för ytterligare en IPC-Server (namngiven pipe) som används för fel sökning och annan Cross-process-kommunikation.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-163">Specifies the name to use for an additional IPC server (named pipe) used for debugging and other cross-process communication.</span></span> <span data-ttu-id="2b0c9-164">Detta erbjuder en förutsägbar mekanism för att ansluta till andra PowerShell-instanser.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-164">This offers a predictable mechanism for connecting to other PowerShell instances.</span></span> <span data-ttu-id="2b0c9-165">Används vanligt vis med parametern **CustomPipeName** på `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-165">Typically used with the **CustomPipeName** parameter on `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="2b0c9-166">Den här parametern introducerades i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-166">This parameter was introduced in PowerShell 6.2.</span></span>

<span data-ttu-id="2b0c9-167">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="2b0c9-167">For example:</span></span>

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a><span data-ttu-id="2b0c9-168">-EncodedCommand | -e | – EC</span><span class="sxs-lookup"><span data-stu-id="2b0c9-168">-EncodedCommand | -e | -ec</span></span>

<span data-ttu-id="2b0c9-169">Accepterar en Base64-kodad sträng version av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-169">Accepts a Base64-encoded string version of a command.</span></span> <span data-ttu-id="2b0c9-170">Använd den här parametern för att skicka kommandon till PowerShell som kräver komplex, kapslad citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-170">Use this parameter to submit commands to PowerShell that require complex, nested quoting.</span></span> <span data-ttu-id="2b0c9-171">Den base64-representation måste vara en kodad UTF-16-sträng.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-171">The Base64 representation must be a UTF-16 encoded string.</span></span>

<span data-ttu-id="2b0c9-172">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="2b0c9-172">For example:</span></span>

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a><span data-ttu-id="2b0c9-173">-ExecutionPolicy | – ex | -EP</span><span class="sxs-lookup"><span data-stu-id="2b0c9-173">-ExecutionPolicy | -ex | -ep</span></span>

<span data-ttu-id="2b0c9-174">Anger standard körnings principen för den aktuella sessionen och sparar den i `$env:PSExecutionPolicyPreference` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-174">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="2b0c9-175">Den här parametern ändrar inte permanent konfigurerade körnings principer.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-175">This parameter does not change the persistently configured execution policies.</span></span>

<span data-ttu-id="2b0c9-176">Den här parametern gäller endast för Windows-datorer.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-176">This parameter only applies to Windows computers.</span></span> <span data-ttu-id="2b0c9-177">`$env:PSExecutionPolicyPreference`Miljövariabeln finns inte på plattformar som inte är Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-177">The `$env:PSExecutionPolicyPreference` environment variable does not exist on non-Windows platforms.</span></span>

### <a name="-inputformat---inp---if"></a><span data-ttu-id="2b0c9-178">-InputFormat | -INP | – om</span><span class="sxs-lookup"><span data-stu-id="2b0c9-178">-InputFormat | -inp | -if</span></span>

<span data-ttu-id="2b0c9-179">Beskriver formatet på data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-179">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="2b0c9-180">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="2b0c9-180">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

### <a name="-interactive---i"></a><span data-ttu-id="2b0c9-181">– Interaktiv | -i</span><span class="sxs-lookup"><span data-stu-id="2b0c9-181">-Interactive | -i</span></span>

<span data-ttu-id="2b0c9-182">Presentera en interaktiv prompt till användaren.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-182">Present an interactive prompt to the user.</span></span> <span data-ttu-id="2b0c9-183">Invertering för en ej interaktiv parameter.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-183">Inverse for NonInteractive parameter.</span></span>

### <a name="-login---l"></a><span data-ttu-id="2b0c9-184">-Inloggning | -l</span><span class="sxs-lookup"><span data-stu-id="2b0c9-184">-Login | -l</span></span>

<span data-ttu-id="2b0c9-185">På Linux och macOS startar PowerShell som ett inloggnings gränssnitt med hjälp av/bin/sh för att köra inloggnings profiler som/etc/profile och ~/.Profile.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-185">On Linux and macOS, starts PowerShell as a login shell, using /bin/sh to execute login profiles such as /etc/profile and ~/.profile.</span></span>
<span data-ttu-id="2b0c9-186">I Windows gör den här växeln ingenting.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-186">On Windows, this switch does nothing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2b0c9-187">Den här parametern måste komma först för att starta PowerShell som ett inloggnings gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-187">This parameter must come first to start PowerShell as a login shell.</span></span>
> <span data-ttu-id="2b0c9-188">Att skicka den här parametern i en annan position ignoreras.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-188">Passing this parameter in another position will be ignored.</span></span>

<span data-ttu-id="2b0c9-189">Så här konfigurerar du `pwsh` som inloggnings gränssnitt på UNIX-liknande operativ system:</span><span class="sxs-lookup"><span data-stu-id="2b0c9-189">To set up `pwsh` as the login shell on UNIX-like operating systems:</span></span>

- <span data-ttu-id="2b0c9-190">Kontrol lera att den fullständiga absoluta sökvägen till `pwsh` visas under `/etc/shells`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-190">Verify that the full absolute path to `pwsh` is listed under `/etc/shells`</span></span>
  - <span data-ttu-id="2b0c9-191">Den här sökvägen är vanligt vis något som liknar `/usr/bin/pwsh` i Linux eller `/usr/local/bin/pwsh` MacOS</span><span class="sxs-lookup"><span data-stu-id="2b0c9-191">This path is usually something like `/usr/bin/pwsh` on Linux or `/usr/local/bin/pwsh` on macOS</span></span>
  - <span data-ttu-id="2b0c9-192">Med vissa installations metoder kommer den här posten att läggas till automatiskt vid installationen</span><span class="sxs-lookup"><span data-stu-id="2b0c9-192">With some installation methods, this entry will be added automatically at installation time</span></span>
  - <span data-ttu-id="2b0c9-193">Om `pwsh` inte finns i `/etc/shells` använder du en redigerare för att lägga till sökvägen till `pwsh` på den sista raden.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-193">If `pwsh` is not present in `/etc/shells`, use an editor to append the path to `pwsh` on the last line.</span></span> <span data-ttu-id="2b0c9-194">Detta kräver förhöjd behörighet att redigera.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-194">This requires elevated privileges to edit.</span></span>
- <span data-ttu-id="2b0c9-195">Använd [chsh](https://linux.die.net/man/1/chsh) -verktyget för att ange den aktuella användarens gränssnitt till `pwsh` :</span><span class="sxs-lookup"><span data-stu-id="2b0c9-195">Use the [chsh](https://linux.die.net/man/1/chsh) utility to set your current user's shell to `pwsh`:</span></span>

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> <span data-ttu-id="2b0c9-196">Inställningen `pwsh` som inloggnings gränssnitt stöds för närvarande inte i Windows-undersystemet för Linux (Wsl) och försöker ange `pwsh` som inloggnings gränssnitt. det kan leda till att det inte går att starta Wsl interaktivt.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-196">Setting `pwsh` as the login shell is currently not supported on Windows Subsystem for Linux (WSL), and attempting to set `pwsh` as the login shell there may lead to being unable to start WSL interactively.</span></span>

### <a name="-mta"></a><span data-ttu-id="2b0c9-197">-MTA</span><span class="sxs-lookup"><span data-stu-id="2b0c9-197">-MTA</span></span>

<span data-ttu-id="2b0c9-198">Starta PowerShell med en flertrådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-198">Start PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="2b0c9-199">Den här växeln är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-199">This switch is only available on Windows.</span></span>

### <a name="-noexit---noe"></a><span data-ttu-id="2b0c9-200">-Noexit | -noe</span><span class="sxs-lookup"><span data-stu-id="2b0c9-200">-NoExit | -noe</span></span>

<span data-ttu-id="2b0c9-201">Avslutas inte när du har kört Start kommandon.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-201">Does not exit after running startup commands.</span></span>

<span data-ttu-id="2b0c9-202">Exempel: `pwsh -NoExit -Command Get-Date`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-202">Example: `pwsh -NoExit -Command Get-Date`</span></span>

### <a name="-nologo---nol"></a><span data-ttu-id="2b0c9-203">-Nologo typ | -nol</span><span class="sxs-lookup"><span data-stu-id="2b0c9-203">-NoLogo | -nol</span></span>

<span data-ttu-id="2b0c9-204">Döljer Copyright-banderollen vid start av interaktiva sessioner.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-204">Hides the copyright banner at startup of interactive sessions.</span></span>

### <a name="-noninteractive---noni"></a><span data-ttu-id="2b0c9-205">-Ej interaktiv | -noni</span><span class="sxs-lookup"><span data-stu-id="2b0c9-205">-NonInteractive | -noni</span></span>

<span data-ttu-id="2b0c9-206">Visar inte en interaktiv prompt till användaren.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-206">Does not present an interactive prompt to the user.</span></span> <span data-ttu-id="2b0c9-207">Alla försök att använda interaktiva funktioner, t `Read-Host` . ex. bekräftelser, resulterar i instruktionen-avslutar fel.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-207">Any attempts to use interactive features, like `Read-Host` or confirmation prompts, result in statement-terminating errors.</span></span>

### <a name="-noprofile---nop"></a><span data-ttu-id="2b0c9-208">-Noprofil | – NOP</span><span class="sxs-lookup"><span data-stu-id="2b0c9-208">-NoProfile | -nop</span></span>

<span data-ttu-id="2b0c9-209">Läser inte in PowerShell-profilerna.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-209">Does not load the PowerShell profiles.</span></span>

### <a name="-outputformat---o---of"></a><span data-ttu-id="2b0c9-210">-OutputFormat | -o | – av</span><span class="sxs-lookup"><span data-stu-id="2b0c9-210">-OutputFormat | -o | -of</span></span>

<span data-ttu-id="2b0c9-211">Anger hur utdata från PowerShell formateras.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-211">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="2b0c9-212">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="2b0c9-212">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

<span data-ttu-id="2b0c9-213">Exempel: `pwsh -o XML -c Get-Date`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-213">Example: `pwsh -o XML -c Get-Date`</span></span>

<span data-ttu-id="2b0c9-214">När du anropar med en PowerShell-session får du avserialiserade objekt som utdata i stället för vanliga strängar.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-214">When called withing a PowerShell session, you get deserialized objects as output rather plain strings.</span></span> <span data-ttu-id="2b0c9-215">Vid anrop från andra gränssnitt är utdata sträng data formaterade som CLIXML text.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-215">When called from other shells, the output is string data formatted as CLIXML text.</span></span>

### <a name="-settingsfile---settings"></a><span data-ttu-id="2b0c9-216">-SettingsFile | – inställningar</span><span class="sxs-lookup"><span data-stu-id="2b0c9-216">-SettingsFile | -settings</span></span>

<span data-ttu-id="2b0c9-217">Åsidosätter den systemomfattande `powershell.config.json` inställnings filen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-217">Overrides the system-wide `powershell.config.json` settings file for the session.</span></span> <span data-ttu-id="2b0c9-218">Som standard läses systemtäckande inställningar från `powershell.config.json` i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-218">By default, system-wide settings are read from the `powershell.config.json` in the `$PSHOME` directory.</span></span>

<span data-ttu-id="2b0c9-219">Observera att de här inställningarna inte används av slut punkten som anges av `-ConfigurationName` argumentet.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-219">Note that these settings are not used by the endpoint specified by the `-ConfigurationName` argument.</span></span>

<span data-ttu-id="2b0c9-220">Exempel: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-220">Example: `pwsh -SettingsFile c:\myproject\powershell.config.json`</span></span>

### <a name="-sshservermode---sshs"></a><span data-ttu-id="2b0c9-221">-SSHServerMode | -sshs</span><span class="sxs-lookup"><span data-stu-id="2b0c9-221">-SSHServerMode | -sshs</span></span>

<span data-ttu-id="2b0c9-222">Används i sshd_config för att köra PowerShell som ett SSH-undersystem.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-222">Used in sshd_config for running PowerShell as an SSH subsystem.</span></span> <span data-ttu-id="2b0c9-223">Den är inte avsedd eller stöds inte för någon annan användning.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-223">It is not intended or supported for any other use.</span></span>

### <a name="-sta"></a><span data-ttu-id="2b0c9-224">– STA</span><span class="sxs-lookup"><span data-stu-id="2b0c9-224">-STA</span></span>

<span data-ttu-id="2b0c9-225">Starta PowerShell med en enkel trådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-225">Start PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="2b0c9-226">Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-226">This is the default.</span></span> <span data-ttu-id="2b0c9-227">Den här växeln är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-227">This switch is only available on Windows.</span></span>

### <a name="-version---v"></a><span data-ttu-id="2b0c9-228">-Version | -v</span><span class="sxs-lookup"><span data-stu-id="2b0c9-228">-Version | -v</span></span>

<span data-ttu-id="2b0c9-229">Visar versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-229">Displays the version of PowerShell.</span></span> <span data-ttu-id="2b0c9-230">Ytterligare parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-230">Additional parameters are ignored.</span></span>

### <a name="-windowstyle---w"></a><span data-ttu-id="2b0c9-231">-WindowStyle | – w</span><span class="sxs-lookup"><span data-stu-id="2b0c9-231">-WindowStyle | -w</span></span>

<span data-ttu-id="2b0c9-232">Anger fönster formatet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-232">Sets the window style for the session.</span></span> <span data-ttu-id="2b0c9-233">Giltiga värden är normal, minimerat, maximerat och dolt.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-233">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

### <a name="-workingdirectory---wd"></a><span data-ttu-id="2b0c9-234">-WorkingDirectory | -WD</span><span class="sxs-lookup"><span data-stu-id="2b0c9-234">-WorkingDirectory | -wd</span></span>

<span data-ttu-id="2b0c9-235">Anger den inledande arbets katalogen genom att köra vid start.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-235">Sets the initial working directory by executing at startup.</span></span> <span data-ttu-id="2b0c9-236">En giltig sökväg till PowerShell-filen stöds.</span><span class="sxs-lookup"><span data-stu-id="2b0c9-236">Any valid PowerShell file path is supported.</span></span>

<span data-ttu-id="2b0c9-237">Om du vill starta PowerShell i din arbets katalog använder du: `pwsh -WorkingDirectory ~`</span><span class="sxs-lookup"><span data-stu-id="2b0c9-237">To start PowerShell in your home directory, use: `pwsh -WorkingDirectory ~`</span></span>

### <a name="-help---"></a><span data-ttu-id="2b0c9-238">– Hjälp,-?,/?</span><span class="sxs-lookup"><span data-stu-id="2b0c9-238">-Help, -?, /?</span></span>

<span data-ttu-id="2b0c9-239">Visar hjälp för `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="2b0c9-239">Displays help for `pwsh`.</span></span> <span data-ttu-id="2b0c9-240">Om du skriver ett pwsh-kommando i PowerShell lägga kommando parametrarna med bindestreck ( `-` ), inte ett snedstreck ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="2b0c9-240">If you are typing a pwsh command in PowerShell, prepend the command parameters with a hyphen (`-`), not a forward slash (`/`).</span></span>
