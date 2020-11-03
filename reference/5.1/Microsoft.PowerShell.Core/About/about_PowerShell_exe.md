---
description: Förklarar hur du använder `powershell.exe` kommando rads gränssnittet. Visar kommando rads parametrarna och beskriver syntaxen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272024"
---
# <a name="about-powershellexe"></a><span data-ttu-id="52fb8-105">Om PowerShell.exe</span><span class="sxs-lookup"><span data-stu-id="52fb8-105">About PowerShell.exe</span></span>

## <a name="short-description"></a><span data-ttu-id="52fb8-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="52fb8-106">Short Description</span></span>
<span data-ttu-id="52fb8-107">Förklarar hur du använder `powershell.exe` kommando rads gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-107">Explains how to use the `powershell.exe` command-line interface.</span></span> <span data-ttu-id="52fb8-108">Visar kommando rads parametrarna och beskriver syntaxen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-108">Displays the command-line parameters and describes the syntax.</span></span>

## <a name="long-description"></a><span data-ttu-id="52fb8-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="52fb8-109">Long Description</span></span>

### <a name="syntax"></a><span data-ttu-id="52fb8-110">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52fb8-110">SYNTAX</span></span>

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a><span data-ttu-id="52fb8-111">Parametrar</span><span class="sxs-lookup"><span data-stu-id="52fb8-111">Parameters</span></span>

#### <a name="-psconsolefile-filepath"></a><span data-ttu-id="52fb8-112">-PSConsoleFile \<FilePath\></span><span class="sxs-lookup"><span data-stu-id="52fb8-112">-PSConsoleFile \<FilePath\></span></span>

<span data-ttu-id="52fb8-113">Läser in den angivna filen med PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-113">Loads the specified PowerShell console file.</span></span> <span data-ttu-id="52fb8-114">Ange sökvägen till och namnet på konsol filen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-114">Enter the path and name of the console file.</span></span> <span data-ttu-id="52fb8-115">Om du vill skapa en konsol fil använder du Export-Console cmdlet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52fb8-115">To create a console file, use the Export-Console cmdlet in PowerShell.</span></span>

#### <a name="-version-powershell-version"></a><span data-ttu-id="52fb8-116">-Version \<PowerShell Version\></span><span class="sxs-lookup"><span data-stu-id="52fb8-116">-Version \<PowerShell Version\></span></span>

<span data-ttu-id="52fb8-117">Startar den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52fb8-117">Starts the specified version of PowerShell.</span></span> <span data-ttu-id="52fb8-118">Giltiga värden är 2,0 och 3,0.</span><span class="sxs-lookup"><span data-stu-id="52fb8-118">Valid values are 2.0 and 3.0.</span></span> <span data-ttu-id="52fb8-119">Den version som du anger måste vara installerad i systemet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-119">The version that you specify must be installed on the system.</span></span> <span data-ttu-id="52fb8-120">Om Windows PowerShell 3,0 är installerat på datorn är "3,0" standard versionen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-120">If Windows PowerShell 3.0 is installed on the computer, "3.0" is the default version.</span></span>
<span data-ttu-id="52fb8-121">Annars är "2,0" standard versionen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-121">Otherwise, "2.0" is the default version.</span></span> <span data-ttu-id="52fb8-122">Mer information finns i [Installera PowerShell](/powershell/scripting/install/installing-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="52fb8-122">For more information, see [Installing PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

#### <a name="-nologo"></a><span data-ttu-id="52fb8-123">-Nologo typ</span><span class="sxs-lookup"><span data-stu-id="52fb8-123">-NoLogo</span></span>

<span data-ttu-id="52fb8-124">Döljer Copyright-banderollen vid start.</span><span class="sxs-lookup"><span data-stu-id="52fb8-124">Hides the copyright banner at startup.</span></span>

#### <a name="-noexit"></a><span data-ttu-id="52fb8-125">-Noexit</span><span class="sxs-lookup"><span data-stu-id="52fb8-125">-NoExit</span></span>

<span data-ttu-id="52fb8-126">Avslutas inte när du har kört Start kommandon.</span><span class="sxs-lookup"><span data-stu-id="52fb8-126">Does not exit after running startup commands.</span></span>

#### <a name="-sta"></a><span data-ttu-id="52fb8-127">– Sta</span><span class="sxs-lookup"><span data-stu-id="52fb8-127">-Sta</span></span>

<span data-ttu-id="52fb8-128">Startar PowerShell med en enkel trådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="52fb8-128">Starts PowerShell using a single-threaded apartment.</span></span> <span data-ttu-id="52fb8-129">I Windows PowerShell 2,0 är flertrådad inne slutning standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-129">In Windows PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="52fb8-130">I Windows PowerShell 3,0 är en enkel trådad Apartment (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="52fb8-130">In Windows PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-mta"></a><span data-ttu-id="52fb8-131">-Mta</span><span class="sxs-lookup"><span data-stu-id="52fb8-131">-Mta</span></span>

<span data-ttu-id="52fb8-132">Startar PowerShell med en flertrådad inne slutning.</span><span class="sxs-lookup"><span data-stu-id="52fb8-132">Starts PowerShell using a multi-threaded apartment.</span></span> <span data-ttu-id="52fb8-133">Den här parametern introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="52fb8-133">This parameter is introduced in PowerShell 3.0.</span></span> <span data-ttu-id="52fb8-134">I PowerShell 2,0 är flertrådad inne slutning standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-134">In PowerShell 2.0, multi-threaded apartment (MTA) is the default.</span></span> <span data-ttu-id="52fb8-135">I PowerShell 3,0 är en enkel trådad Apartment (STA) som standard.</span><span class="sxs-lookup"><span data-stu-id="52fb8-135">In PowerShell 3.0, single-threaded apartment (STA) is the default.</span></span>

#### <a name="-noprofile"></a><span data-ttu-id="52fb8-136">-Noprofil</span><span class="sxs-lookup"><span data-stu-id="52fb8-136">-NoProfile</span></span>

<span data-ttu-id="52fb8-137">Läser inte in PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-137">Does not load the PowerShell profile.</span></span>

#### <a name="-noninteractive"></a><span data-ttu-id="52fb8-138">-Ej interaktiv</span><span class="sxs-lookup"><span data-stu-id="52fb8-138">-NonInteractive</span></span>

<span data-ttu-id="52fb8-139">Visar inte en interaktiv prompt till användaren.</span><span class="sxs-lookup"><span data-stu-id="52fb8-139">Does not present an interactive prompt to the user.</span></span>

#### <a name="-inputformat-text--xml"></a><span data-ttu-id="52fb8-140">-InputFormat {text | FIL</span><span class="sxs-lookup"><span data-stu-id="52fb8-140">-InputFormat {Text | XML}</span></span>

<span data-ttu-id="52fb8-141">Beskriver formatet på data som skickas till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52fb8-141">Describes the format of data sent to PowerShell.</span></span> <span data-ttu-id="52fb8-142">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="52fb8-142">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-outputformat-text--xml"></a><span data-ttu-id="52fb8-143">-OutputFormat {text | FIL</span><span class="sxs-lookup"><span data-stu-id="52fb8-143">-OutputFormat {Text | XML}</span></span>

<span data-ttu-id="52fb8-144">Anger hur utdata från PowerShell formateras.</span><span class="sxs-lookup"><span data-stu-id="52fb8-144">Determines how output from PowerShell is formatted.</span></span> <span data-ttu-id="52fb8-145">Giltiga värden är "text" (text strängar) eller "XML" (serialiserat CLIXML-format).</span><span class="sxs-lookup"><span data-stu-id="52fb8-145">Valid values are "Text" (text strings) or "XML" (serialized CLIXML format).</span></span>

#### <a name="-windowstyle-window-style"></a><span data-ttu-id="52fb8-146">– WindowStyle \<Window style\></span><span class="sxs-lookup"><span data-stu-id="52fb8-146">-WindowStyle \<Window style\></span></span>

<span data-ttu-id="52fb8-147">Anger fönster formatet för sessionen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-147">Sets the window style for the session.</span></span> <span data-ttu-id="52fb8-148">Giltiga värden är normal, minimerat, maximerat och dolt.</span><span class="sxs-lookup"><span data-stu-id="52fb8-148">Valid values are Normal, Minimized, Maximized and Hidden.</span></span>

#### <a name="-encodedcommand-base64encodedcommand"></a><span data-ttu-id="52fb8-149">-EncodedCommand \<Base64EncodedCommand\></span><span class="sxs-lookup"><span data-stu-id="52fb8-149">-EncodedCommand \<Base64EncodedCommand\></span></span>

<span data-ttu-id="52fb8-150">Accepterar en Base-64-kodad sträng version av ett kommando.</span><span class="sxs-lookup"><span data-stu-id="52fb8-150">Accepts a base-64-encoded string version of a command.</span></span> <span data-ttu-id="52fb8-151">Använd den här parametern för att skicka kommandon till PowerShell som kräver komplexa citat tecken eller klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="52fb8-151">Use this parameter to submit commands to PowerShell that require complex quotation marks or curly braces.</span></span> <span data-ttu-id="52fb8-152">Strängen måste vara formaterad med UTF-16LE tecken kodning.</span><span class="sxs-lookup"><span data-stu-id="52fb8-152">The string must be formatted using UTF-16LE character encoding.</span></span>

#### <a name="-configurationname-string"></a><span data-ttu-id="52fb8-153">– ConfigurationName \<string\></span><span class="sxs-lookup"><span data-stu-id="52fb8-153">-ConfigurationName \<string\></span></span>

<span data-ttu-id="52fb8-154">Anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="52fb8-154">Specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="52fb8-155">Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="52fb8-155">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

#### <a name="-file----filepath-args"></a><span data-ttu-id="52fb8-156">-Fil-| \<filePath\>\<args\></span><span class="sxs-lookup"><span data-stu-id="52fb8-156">-File - | \<filePath\> \<args\></span></span>

<span data-ttu-id="52fb8-157">Om värdet för **filen** är "-" läses kommando texten in från standar din data.</span><span class="sxs-lookup"><span data-stu-id="52fb8-157">If the value of **File** is "-", the command text is read from standard input.</span></span>
<span data-ttu-id="52fb8-158">Om du kör `powershell -File -` utan omdirigerade standar ininformation startar en vanlig session.</span><span class="sxs-lookup"><span data-stu-id="52fb8-158">Running `powershell -File -` without redirected standard input starts a regular session.</span></span> <span data-ttu-id="52fb8-159">Detta är detsamma som att inte ange **fil** parametern alls.</span><span class="sxs-lookup"><span data-stu-id="52fb8-159">This is the same as not specifying the **File** parameter at all.</span></span>

<span data-ttu-id="52fb8-160">Om **filens** värde är en fil Sök väg körs skriptet i det lokala omfånget ("punkt-källad"), så att de funktioner och variabler som skriptet skapar är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="52fb8-160">If the value of **File** is a file path, the script runs in the local scope ("dot-sourced"), so that the functions and variables that the script creates are available in the current session.</span></span> <span data-ttu-id="52fb8-161">Ange sökvägen till skript filen och eventuella parametrar.</span><span class="sxs-lookup"><span data-stu-id="52fb8-161">Enter the script file path and any parameters.</span></span> <span data-ttu-id="52fb8-162">**Filen** måste vara den sista parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="52fb8-162">**File** must be the last parameter in the command.</span></span> <span data-ttu-id="52fb8-163">Alla värden som skrivs efter **fil** parametern tolkas som skript filens sökväg och parametrar som skickas till skriptet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-163">All values typed after the **File** parameter are interpreted as the script file path and parameters passed to that script.</span></span>

<span data-ttu-id="52fb8-164">Parametrar som skickas till skriptet skickas som litterala strängar efter tolkning av det aktuella gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-164">Parameters passed to the script are passed as literal strings, after interpretation by the current shell.</span></span> <span data-ttu-id="52fb8-165">Om du till exempel är i **cmd.exe** och vill skicka ett miljö variabel värde, använder du **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span><span class="sxs-lookup"><span data-stu-id="52fb8-165">For example, if you are in **cmd.exe** and want to pass an environment variable value, you would use the **cmd.exe** syntax: `powershell.exe -File .\test.ps1 -TestParam %windir%`</span></span>

<span data-ttu-id="52fb8-166">I motsats, som körs `powershell.exe -File .\test.ps1 -TestParam $env:windir` i **cmd.exe** , resulterar i att skriptet tar emot en litteral sträng `$env:windir` , eftersom det inte har någon särskild betydelse för det aktuella **cmd.exe** gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-166">In contrast, running `powershell.exe -File .\test.ps1 -TestParam $env:windir` in **cmd.exe** results in the script receiving the literal string `$env:windir` because it has no special meaning to the current **cmd.exe** shell.</span></span> <span data-ttu-id="52fb8-167">`$env:windir`Formatet för miljö variabel referens _kan_ användas i en **kommando** parameter, eftersom den tolkas som PowerShell-kod.</span><span class="sxs-lookup"><span data-stu-id="52fb8-167">The `$env:windir` style of environment variable reference _can_ be used inside a **Command** parameter, since there it will be interpreted as PowerShell code.</span></span>

<span data-ttu-id="52fb8-168">Om du vill köra samma kommando från ett **kommando skript** använder du `%~dp0` i stället för `.\` eller `$PSScriptRoot` för att representera den aktuella körnings katalogen: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .</span><span class="sxs-lookup"><span data-stu-id="52fb8-168">Similarly, if you want to execute the same command from a **Batch script** , you would use `%~dp0` instead of `.\` or `$PSScriptRoot` to represent the current execution directory: `powershell.exe -File %~dp0test.ps1 -TestParam %windir%`.</span></span>
<span data-ttu-id="52fb8-169">Om du i stället använde `.\test.ps1` , skulle PowerShell utlösa ett fel eftersom det inte går att hitta den litterala sökvägen `.\test.ps1`</span><span class="sxs-lookup"><span data-stu-id="52fb8-169">If you instead used `.\test.ps1`, PowerShell would throw an error because it cannot find the literal path `.\test.ps1`</span></span>

<span data-ttu-id="52fb8-170">När **filens värde är en** fil Sök väg måste **filen** _must_ vara den sista parametern i kommandot eftersom eventuella tecken som skrivs efter **fil** parameterns namn tolkas som skript filens sökväg följt av skript parametrarna.</span><span class="sxs-lookup"><span data-stu-id="52fb8-170">When the value of **File** is a file path, **File** _must_ be the last parameter in the command because any characters typed after the **File** parameter name are interpreted as the script file path followed by the script parameters.</span></span>

<span data-ttu-id="52fb8-171">Du kan inkludera skript parametrar och värden i värdet för **fil** parametern.</span><span class="sxs-lookup"><span data-stu-id="52fb8-171">You can include the script parameters and values in the value of the **File** parameter.</span></span> <span data-ttu-id="52fb8-172">Exempelvis: `-File .\Get-Script.ps1 -Domain Central`</span><span class="sxs-lookup"><span data-stu-id="52fb8-172">For example: `-File .\Get-Script.ps1 -Domain Central`</span></span>

<span data-ttu-id="52fb8-173">Normalt ingår eller utelämnas växel parametrarna för ett skript.</span><span class="sxs-lookup"><span data-stu-id="52fb8-173">Typically, the switch parameters of a script are either included or omitted.</span></span>
<span data-ttu-id="52fb8-174">Följande kommando använder till exempel parametern **all** i `Get-Script.ps1` skript filen: `-File .\Get-Script.ps1 -All`</span><span class="sxs-lookup"><span data-stu-id="52fb8-174">For example, the following command uses the **All** parameter of the `Get-Script.ps1` script file: `-File .\Get-Script.ps1 -All`</span></span>

<span data-ttu-id="52fb8-175">I sällsynta fall kan du behöva ange ett **booleskt** värde för en parameter.</span><span class="sxs-lookup"><span data-stu-id="52fb8-175">In rare cases, you might need to provide a **Boolean** value for a parameter.</span></span>
<span data-ttu-id="52fb8-176">Det går inte att skicka ett explicit booleskt värde för en växel parameter när ett skript körs på det här sättet.</span><span class="sxs-lookup"><span data-stu-id="52fb8-176">It is not possible to pass an explicit boolean value for a switch parameter when running a script in this way.</span></span> <span data-ttu-id="52fb8-177">Den här begränsningen har tagits bort i PowerShell 6 ( `pwsh.exe` ).</span><span class="sxs-lookup"><span data-stu-id="52fb8-177">This limitation was removed in PowerShell 6 (`pwsh.exe`).</span></span>

#### <a name="-executionpolicy-executionpolicy"></a><span data-ttu-id="52fb8-178">– ExecutionPolicy \<ExecutionPolicy\></span><span class="sxs-lookup"><span data-stu-id="52fb8-178">-ExecutionPolicy \<ExecutionPolicy\></span></span>

<span data-ttu-id="52fb8-179">Anger standard körnings principen för den aktuella sessionen och sparar den i `$env:PSExecutionPolicyPreference` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="52fb8-179">Sets the default execution policy for the current session and saves it in the `$env:PSExecutionPolicyPreference` environment variable.</span></span> <span data-ttu-id="52fb8-180">Den här parametern ändrar inte den körnings princip för PowerShell som anges i registret.</span><span class="sxs-lookup"><span data-stu-id="52fb8-180">This parameter does not change the PowerShell execution policy that is set in the registry.</span></span> <span data-ttu-id="52fb8-181">Information om körnings principer för PowerShell, inklusive en lista över giltiga värden, finns [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="52fb8-181">For information about PowerShell execution policies, including a list of valid values, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

#### <a name="-command"></a><span data-ttu-id="52fb8-182">-Kommando</span><span class="sxs-lookup"><span data-stu-id="52fb8-182">-Command</span></span>

<span data-ttu-id="52fb8-183">Kör de angivna kommandona (och alla parametrar) som om de skrevs i PowerShell-Kommandotolken och sedan avslutas, om inte `NoExit` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="52fb8-183">Executes the specified commands (and any parameters) as though they were typed at the PowerShell command prompt, and then exits, unless the `NoExit` parameter is specified.</span></span>

<span data-ttu-id="52fb8-184">Värdet för **kommandot** kan vara `-` , ett skript block eller en sträng.</span><span class="sxs-lookup"><span data-stu-id="52fb8-184">The value of **Command** can be `-`, a script block, or a string.</span></span> <span data-ttu-id="52fb8-185">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="52fb8-185">If the value of **Command** is `-`, the command text is read from standard input.</span></span>

<span data-ttu-id="52fb8-186">**Kommando** parametern accepterar bara ett-skript block för körning när det kan identifiera värdet som skickas till **kommandot** som en **script block** -typ.</span><span class="sxs-lookup"><span data-stu-id="52fb8-186">The **Command** parameter only accepts a script block for execution when it can recognize the value passed to **Command** as a **ScriptBlock** type.</span></span> <span data-ttu-id="52fb8-187">Detta är _endast_ möjligt när du kör `powershell.exe` från en annan PowerShell-värd.</span><span class="sxs-lookup"><span data-stu-id="52fb8-187">This is _only_ possible when running `powershell.exe` from another PowerShell host.</span></span> <span data-ttu-id="52fb8-188">**Script block** -typen kan finnas i en befintlig variabel, returneras från ett uttryck eller parsas av PowerShell-värden som ett litteralt-skript block som omges av klammerparenteser ( `{}` ), innan de skickas till `powershell.exe` .</span><span class="sxs-lookup"><span data-stu-id="52fb8-188">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces (`{}`), before being passed to `powershell.exe`.</span></span>

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

<span data-ttu-id="52fb8-189">I finns `cmd.exe` det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng.</span><span class="sxs-lookup"><span data-stu-id="52fb8-189">In `cmd.exe`, there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="52fb8-190">Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.</span><span class="sxs-lookup"><span data-stu-id="52fb8-190">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="52fb8-191">En sträng som skickas till **kommandot** körs fortfarande som PowerShell-kod, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="52fb8-191">A string passed to **Command** is still executed as PowerShell code, so the script block curly braces are often not required in the first place when running from `cmd.exe`.</span></span> <span data-ttu-id="52fb8-192">Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) `&` :</span><span class="sxs-lookup"><span data-stu-id="52fb8-192">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators) `&` can be used:</span></span>

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

<span data-ttu-id="52fb8-193">Om värdet för **kommandot** är en sträng måste **kommandot** vara den sista parametern för pwsh, eftersom alla argument som följer tolkas som en del av kommandot som ska köras.</span><span class="sxs-lookup"><span data-stu-id="52fb8-193">If the value of **Command** is a string, **Command** must be the last parameter for pwsh, because all arguments following it are interpreted as part of the command to execute.</span></span>

<span data-ttu-id="52fb8-194">När de anropas i en befintlig PowerShell-session returneras resultatet till det överordnade gränssnittet som avserialiserade XML-objekt, inte aktiva objekt.</span><span class="sxs-lookup"><span data-stu-id="52fb8-194">When called from within an existing PowerShell session, the results are returned to the parent shell as deserialized XML objects, not live objects.</span></span> <span data-ttu-id="52fb8-195">För andra gränssnitt returneras resultaten som strängar.</span><span class="sxs-lookup"><span data-stu-id="52fb8-195">For other shells, the results are returned as strings.</span></span>

<span data-ttu-id="52fb8-196">Om **kommandots** värde är `-` läses kommando texten in från standar din information.</span><span class="sxs-lookup"><span data-stu-id="52fb8-196">If the value of **Command** is `-`, the command text is read from standard input.</span></span> <span data-ttu-id="52fb8-197">Du måste omdirigera standar din information när du använder **kommando** parametern med standar din information.</span><span class="sxs-lookup"><span data-stu-id="52fb8-197">You must redirect standard input when using the **Command** parameter with standard input.</span></span> <span data-ttu-id="52fb8-198">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="52fb8-198">For example:</span></span>

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

<span data-ttu-id="52fb8-199">I det här exemplet skapas följande utdata:</span><span class="sxs-lookup"><span data-stu-id="52fb8-199">This example produces the following output:</span></span>

```Output
in
hi there
out
```

<span data-ttu-id="52fb8-200">Avslutnings koden för processen avgörs av status för det sista (körda) kommandot i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="52fb8-200">The process exit code is determined by status of the last (executed) command within the script block.</span></span> <span data-ttu-id="52fb8-201">Slut koden är `0` när `$?` är `$true` eller `1` när `$?` är `$false` .</span><span class="sxs-lookup"><span data-stu-id="52fb8-201">The exit code is `0` when `$?` is `$true` or `1` when `$?` is `$false`.</span></span> <span data-ttu-id="52fb8-202">Om det sista kommandot är ett externt program eller ett PowerShell-skript som explicit anger en slut kod som `0` inte `1` är eller, konverteras slut koden till `1` för process avslutnings kod.</span><span class="sxs-lookup"><span data-stu-id="52fb8-202">If the last command is an external program or a PowerShell script that explicitly sets an exit code other than `0` or `1`, that exit code is converted to `1` for process exit code.</span></span> <span data-ttu-id="52fb8-203">Om du vill bevara den angivna slut koden lägger du till den `exit $LASTEXITCODE` i kommando strängen eller skript blocket.</span><span class="sxs-lookup"><span data-stu-id="52fb8-203">To preserve the specific exit code, add `exit $LASTEXITCODE` to your command string or script block.</span></span>

<span data-ttu-id="52fb8-204">På samma sätt returneras värdet 1 när ett skript avslutas (körnings utrymme), till exempel ett `throw` eller `-ErrorAction Stop` , inträffar eller när körningen avbryts med <kbd>CTRL</kbd> - <kbd>+ C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="52fb8-204">Similarly, the value 1 is returned when a script-terminating (runspace-terminating) error, such as a `throw` or `-ErrorAction Stop`, occurs or when execution is interrupted with <kbd>Ctrl</kbd>-<kbd>C</kbd>.</span></span>

<span data-ttu-id="52fb8-205">Det går _bara_ att köra **PowerShell.exe** från en annan PowerShell-värd.</span><span class="sxs-lookup"><span data-stu-id="52fb8-205">_only_ possible when running **PowerShell.exe** from another PowerShell host.</span></span>
<span data-ttu-id="52fb8-206">**Script block** -typen kan finnas i en befintlig variabel, returnerad från ett uttryck eller parsas av PowerShell-värden som ett litteralt skript block inom klammerparenteser `{}` innan de skickas till **PowerShell.exe**.</span><span class="sxs-lookup"><span data-stu-id="52fb8-206">The **ScriptBlock** type may be contained in an existing variable, returned from an expression, or parsed by the PowerShell host as a literal script block enclosed in curly braces `{}`, before being passed to **PowerShell.exe**.</span></span>

<span data-ttu-id="52fb8-207">I **cmd.exe** finns det inget som ett skript block (eller **script block** -typ), så det värde som skickas till **kommandot** är _alltid_ en sträng.</span><span class="sxs-lookup"><span data-stu-id="52fb8-207">In **cmd.exe** , there is no such thing as a script block (or **ScriptBlock** type), so the value passed to **Command** will _always_ be a string.</span></span> <span data-ttu-id="52fb8-208">Du kan skriva ett skript block inuti strängen, men i stället för att utföra det fungerar det exakt som om du har angett det i en typisk PowerShell-prompt och skriver ut innehållet i skript blocket till dig.</span><span class="sxs-lookup"><span data-stu-id="52fb8-208">You can write a script block inside the string, but instead of being executed it will behave exactly as though you typed it at a typical PowerShell prompt, printing the contents of the script block back out to you.</span></span>

<span data-ttu-id="52fb8-209">En sträng som skickas till **kommandot** körs fortfarande som PowerShell, så att skript blockets klammerparenteser ofta inte krävs på den första platsen när du kör från **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="52fb8-209">A string passed to **Command** will still be executed as PowerShell, so the script block curly braces are often not required in the first place when running from **cmd.exe**.</span></span> <span data-ttu-id="52fb8-210">Om du vill köra ett infogat skript block som definierats inuti en sträng kan du använda [anrops operatorn](about_operators.md#special-operators) 
 `&` :</span><span class="sxs-lookup"><span data-stu-id="52fb8-210">To execute an inline script block defined inside a string, the [call operator](about_operators.md#special-operators)
`&` can be used:</span></span>

```console
"& {<command>}"
```

#### <a name="-help---"></a><span data-ttu-id="52fb8-211">– Hjälp,-?,/?</span><span class="sxs-lookup"><span data-stu-id="52fb8-211">-Help, -?, /?</span></span>

<span data-ttu-id="52fb8-212">Visar hjälp för **PowerShell.exe**.</span><span class="sxs-lookup"><span data-stu-id="52fb8-212">Displays help for **PowerShell.exe**.</span></span> <span data-ttu-id="52fb8-213">Om du skriver ett **PowerShell.exe** kommando i en PowerShell-session, lägga kommando parametrarna med bindestreck (-), inte ett snedstreck (/).</span><span class="sxs-lookup"><span data-stu-id="52fb8-213">If you are typing a **PowerShell.exe** command in a PowerShell session, prepend the command parameters with a hyphen (-), not a forward slash (/).</span></span> <span data-ttu-id="52fb8-214">Du kan använda antingen bindestreck eller snedstreck i **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="52fb8-214">You can use either a hyphen or forward slash in **cmd.exe**.</span></span>

### <a name="remarks"></a><span data-ttu-id="52fb8-215">REMARKS</span><span class="sxs-lookup"><span data-stu-id="52fb8-215">REMARKS</span></span>

<span data-ttu-id="52fb8-216">Fel söknings meddelande: i PowerShell 2,0 går det inte att starta vissa program från PowerShell-konsolen med en **LastExitCode** av 0xc0000142.</span><span class="sxs-lookup"><span data-stu-id="52fb8-216">Troubleshooting note: In PowerShell 2.0, starting some programs from the PowerShell console fails with a **LastExitCode** of 0xc0000142.</span></span>

### <a name="examples"></a><span data-ttu-id="52fb8-217">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52fb8-217">EXAMPLES</span></span>

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
