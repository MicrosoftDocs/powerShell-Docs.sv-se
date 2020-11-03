---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 3f6720ee2235438a3f71c4efd6fb4083360bd520
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266732"
---
# <span data-ttu-id="92665-103">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="92665-103">Set-PSBreakpoint</span></span>

## <span data-ttu-id="92665-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="92665-104">SYNOPSIS</span></span>
<span data-ttu-id="92665-105">Anger en Bryt punkt för en linje, ett kommando eller en variabel.</span><span class="sxs-lookup"><span data-stu-id="92665-105">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="92665-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92665-106">SYNTAX</span></span>

### <span data-ttu-id="92665-107">Rad (standard)</span><span class="sxs-lookup"><span data-stu-id="92665-107">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="92665-108">Kommando</span><span class="sxs-lookup"><span data-stu-id="92665-108">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="92665-109">Variabel</span><span class="sxs-lookup"><span data-stu-id="92665-109">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="92665-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="92665-110">DESCRIPTION</span></span>

<span data-ttu-id="92665-111">`Set-PSBreakpoint`Cmdleten anger en Bryt punkt i ett skript eller i alla kommando körningar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="92665-111">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="92665-112">Du kan använda `Set-PSBreakpoint` för att ange en Bryt punkt innan du kör ett skript eller kör ett kommando, eller under fel sökning när det stoppas vid en annan Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-112">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="92665-113">`Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="92665-113">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="92665-114">Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.</span><span class="sxs-lookup"><span data-stu-id="92665-114">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="92665-115">Varje `Set-PSBreakpoint` kommando skapar någon av följande tre typer av Bryt punkter:</span><span class="sxs-lookup"><span data-stu-id="92665-115">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="92665-116">Rad Bryt punkt – anger Bryt punkter vid särskilda rader och kolumn koordinater.</span><span class="sxs-lookup"><span data-stu-id="92665-116">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="92665-117">Kommando Bryt punkt – anger Bryt punkter för kommandon och funktioner.</span><span class="sxs-lookup"><span data-stu-id="92665-117">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="92665-118">Variabel Bryt punkt – anger Bryt punkter för variabler.</span><span class="sxs-lookup"><span data-stu-id="92665-118">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="92665-119">Du kan ange en Bryt punkt för flera rader, kommandon eller variabler i ett enda `Set-PSBreakpoint` kommando, men varje `Set-PSBreakpoint` kommando anger bara en typ av Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-119">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="92665-120">Vid en Bryt punkt slutar PowerShell tillfälligt att köra och ger kontroll till fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="92665-120">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="92665-121">Kommando tolken ändras till `DBG\>` och en uppsättning fel söknings kommandon blir tillgängliga för användning.</span><span class="sxs-lookup"><span data-stu-id="92665-121">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="92665-122">Du kan dock använda **Åtgärds** parametern för att ange ett alternativt svar, till exempel villkor för Bryt punkten eller instruktionerna för att utföra ytterligare åtgärder, till exempel loggning eller diagnostik.</span><span class="sxs-lookup"><span data-stu-id="92665-122">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="92665-123">`Set-PSBreakpoint`Cmdleten är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="92665-123">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="92665-124">Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="92665-124">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="92665-125">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="92665-125">EXAMPLES</span></span>

### <span data-ttu-id="92665-126">Exempel 1: Ange en Bryt punkt på en linje</span><span class="sxs-lookup"><span data-stu-id="92665-126">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="92665-127">I det här exemplet anges en Bryt punkt på rad 5 i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="92665-127">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="92665-128">När skriptet körs stoppar körningen omedelbart innan rad 5 körs.</span><span class="sxs-lookup"><span data-stu-id="92665-128">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="92665-129">När du anger en ny Bryt punkt per rad nummer `Set-PSBreakpoint` genererar cmdleten ett rad Bryt punkts objekt ( **system. Management. Automation. LineBreakpoint** ) som innehåller Bryt punkts-ID och antal träffar.</span><span class="sxs-lookup"><span data-stu-id="92665-129">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object ( **System.Management.Automation.LineBreakpoint** ) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="92665-130">Exempel 2: Ange en Bryt punkt för en funktion</span><span class="sxs-lookup"><span data-stu-id="92665-130">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="92665-131">I det här exemplet skapas en kommando Bryt punkt för `Increment` funktionen i Sample.ps1 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92665-131">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="92665-132">Skriptet slutar att köra omedelbart före varje anrop till den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="92665-132">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="92665-133">Resultatet är ett kommando Bryt punkts objekt.</span><span class="sxs-lookup"><span data-stu-id="92665-133">The result is a command breakpoint object.</span></span> <span data-ttu-id="92665-134">Innan skriptet körs är värdet för egenskapen **HitCount** 0.</span><span class="sxs-lookup"><span data-stu-id="92665-134">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="92665-135">Exempel 3: Ange en Bryt punkt för en variabel</span><span class="sxs-lookup"><span data-stu-id="92665-135">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="92665-136">I det här exemplet anges en Bryt punkt för **Server** variabeln i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="92665-136">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="92665-137">Den använder parametern **mode** med värdet **readwrite** för att stoppa körningen när värdet för variabeln läses och precis innan värdet ändras.</span><span class="sxs-lookup"><span data-stu-id="92665-137">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="92665-138">Exempel 4: Ange en Bryt punkt för varje kommando som börjar med angiven text</span><span class="sxs-lookup"><span data-stu-id="92665-138">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="92665-139">I det här exemplet anges en Bryt punkt för varje kommando i Sample.ps1-skriptet som börjar med "Write", till exempel `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="92665-139">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="92665-140">Exempel 5: Ange en Bryt punkt beroende på värdet för en variabel</span><span class="sxs-lookup"><span data-stu-id="92665-140">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="92665-141">I det här exemplet stoppas körningen i `DiskTest` funktionen i Test.ps1-skriptet endast när värdet för `$Disk` variabeln är större än 2.</span><span class="sxs-lookup"><span data-stu-id="92665-141">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="92665-142">Värdet för **åtgärden** är ett skript block som testar värdet för `$Disk` variabeln i funktionen.</span><span class="sxs-lookup"><span data-stu-id="92665-142">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="92665-143">Åtgärden använder `break` nyckelordet för att stoppa körningen om villkoret är uppfyllt.</span><span class="sxs-lookup"><span data-stu-id="92665-143">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="92665-144">Alternativet (och standard) är **fortfarande**.</span><span class="sxs-lookup"><span data-stu-id="92665-144">The alternative (and the default) is **Continue**.</span></span>

### <span data-ttu-id="92665-145">Exempel 6: Ange en Bryt punkt för en funktion</span><span class="sxs-lookup"><span data-stu-id="92665-145">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="92665-146">I det här exemplet anges en Bryt punkt för `CheckLog` funktionen.</span><span class="sxs-lookup"><span data-stu-id="92665-146">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="92665-147">Eftersom kommandot inte anger något skript, anges Bryt punkten för allt som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="92665-147">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="92665-148">Fel söknings verktyget bryts när funktionen anropas, inte när den har deklarerats.</span><span class="sxs-lookup"><span data-stu-id="92665-148">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="92665-149">Exempel 7: Ange Bryt punkter på flera rader</span><span class="sxs-lookup"><span data-stu-id="92665-149">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="92665-150">I det här exemplet anges tre rad Bryt punkter i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="92665-150">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="92665-151">Den anger en Bryt punkt i kolumn 2 på var och en av de rader som anges i skriptet.</span><span class="sxs-lookup"><span data-stu-id="92665-151">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="92665-152">Den åtgärd som anges i parametern **åtgärd** gäller för alla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="92665-152">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="92665-153">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="92665-153">PARAMETERS</span></span>

### <span data-ttu-id="92665-154">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="92665-154">-Action</span></span>

<span data-ttu-id="92665-155">Anger kommandon som körs vid varje Bryt punkt i stället för att brytas.</span><span class="sxs-lookup"><span data-stu-id="92665-155">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="92665-156">Ange ett skript block som innehåller kommandona.</span><span class="sxs-lookup"><span data-stu-id="92665-156">Enter a script block that contains the commands.</span></span> <span data-ttu-id="92665-157">Du kan använda den här parametern för att ange villkorliga Bryt punkter eller utföra andra uppgifter, till exempel testning eller loggning.</span><span class="sxs-lookup"><span data-stu-id="92665-157">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="92665-158">Om den här parametern utelämnas eller om ingen åtgärd anges, stoppas körningen vid Bryt punkten och fel söknings programmet startar.</span><span class="sxs-lookup"><span data-stu-id="92665-158">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="92665-159">När **Åtgärds** parametern används körs åtgärds skript blocket vid varje Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-159">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="92665-160">Körningen stoppas inte om inte skript blocket innehåller nyckelordet Break.</span><span class="sxs-lookup"><span data-stu-id="92665-160">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="92665-161">Om du använder nyckelordet Continue i-skript blocket återupptas körningen tills nästa Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-161">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="92665-162">Mer information finns i [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)och [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span><span class="sxs-lookup"><span data-stu-id="92665-162">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-163">-Kolumn</span><span class="sxs-lookup"><span data-stu-id="92665-163">-Column</span></span>

<span data-ttu-id="92665-164">Anger kolumn numret för kolumnen i skript filen där körningen stoppas.</span><span class="sxs-lookup"><span data-stu-id="92665-164">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="92665-165">Ange endast ett kolumn nummer.</span><span class="sxs-lookup"><span data-stu-id="92665-165">Enter only one column number.</span></span> <span data-ttu-id="92665-166">Standardvärdet är kolumn 1.</span><span class="sxs-lookup"><span data-stu-id="92665-166">The default is column 1.</span></span>

<span data-ttu-id="92665-167">Kolumnvärdet används med värdet för **rad** parametern för att ange Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="92665-167">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="92665-168">Om **rad** parametern anger flera rader, anger **kolumn** parametern en Bryt punkt i den angivna kolumnen på var och en av de angivna raderna.</span><span class="sxs-lookup"><span data-stu-id="92665-168">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="92665-169">PowerShell slutar att köra före instruktionen eller uttrycket som innehåller tecknen vid den angivna rad-och kolumn positionen.</span><span class="sxs-lookup"><span data-stu-id="92665-169">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="92665-170">Kolumner räknas från den övre vänstra marginalen med början på kolumn nummer 1 (inte 0).</span><span class="sxs-lookup"><span data-stu-id="92665-170">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="92665-171">Om du anger en kolumn som inte finns i skriptet, deklareras inte ett fel, men Bryt punkten körs aldrig.</span><span class="sxs-lookup"><span data-stu-id="92665-171">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-172">-Kommando</span><span class="sxs-lookup"><span data-stu-id="92665-172">-Command</span></span>

<span data-ttu-id="92665-173">Anger en kommando Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-173">Sets a command breakpoint.</span></span> <span data-ttu-id="92665-174">Ange namn på cmdlets, till exempel `Get-Process` eller funktions namn.</span><span class="sxs-lookup"><span data-stu-id="92665-174">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="92665-175">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="92665-175">Wildcards are permitted.</span></span>

<span data-ttu-id="92665-176">Körningen stoppas precis innan varje instans av varje kommando körs.</span><span class="sxs-lookup"><span data-stu-id="92665-176">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="92665-177">Om kommandot är en funktion stoppas körningen varje gång funktionen anropas och vid varje BEGIN-, PROCESS-och END-avsnitt.</span><span class="sxs-lookup"><span data-stu-id="92665-177">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="92665-178">-Rad</span><span class="sxs-lookup"><span data-stu-id="92665-178">-Line</span></span>

<span data-ttu-id="92665-179">Anger en rad Bryt punkt i ett skript.</span><span class="sxs-lookup"><span data-stu-id="92665-179">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="92665-180">Ange ett eller flera rad nummer, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="92665-180">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="92665-181">PowerShell stoppas omedelbart innan instruktionen som börjar på var och en av de angivna raderna körs.</span><span class="sxs-lookup"><span data-stu-id="92665-181">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="92665-182">Rader räknas från den övre vänstra marginalen för skript filen som börjar med rad nummer 1 (inte 0).</span><span class="sxs-lookup"><span data-stu-id="92665-182">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="92665-183">Om du anger en tom rad stoppas körningen före nästa icke-tomma rad.</span><span class="sxs-lookup"><span data-stu-id="92665-183">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="92665-184">Om raden är utanför intervallet når Bryt punkten aldrig.</span><span class="sxs-lookup"><span data-stu-id="92665-184">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-185">– Läge</span><span class="sxs-lookup"><span data-stu-id="92665-185">-Mode</span></span>

<span data-ttu-id="92665-186">Anger det åtkomst läge som utlöser variabla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="92665-186">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="92665-187">Standardvärdet är **Write**.</span><span class="sxs-lookup"><span data-stu-id="92665-187">The default is **Write**.</span></span>

<span data-ttu-id="92665-188">Den här parametern är endast giltig när **variabel** parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="92665-188">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="92665-189">Läget gäller för alla Bryt punkter som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="92665-189">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="92665-190">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="92665-190">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="92665-191">**Write** -stoppar körningen omedelbart innan ett nytt värde skrivs till variabeln.</span><span class="sxs-lookup"><span data-stu-id="92665-191">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="92665-192">**Read** -stoppa körning när variabeln läses, det vill säga när dess värde har använts, antingen för att tilldelas, visas eller användas.</span><span class="sxs-lookup"><span data-stu-id="92665-192">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="92665-193">I läsläge stoppas inte körningen när värdet på variabeln ändras.</span><span class="sxs-lookup"><span data-stu-id="92665-193">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="92665-194">**Readwrite** – stoppar körningen när variabeln läses eller skrivs.</span><span class="sxs-lookup"><span data-stu-id="92665-194">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-195">– Skript</span><span class="sxs-lookup"><span data-stu-id="92665-195">-Script</span></span>

<span data-ttu-id="92665-196">Anger en matris med skriptfiler som denna cmdlet anger en Bryt punkt i.</span><span class="sxs-lookup"><span data-stu-id="92665-196">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="92665-197">Ange sökvägar och fil namn för en eller flera skriptfiler.</span><span class="sxs-lookup"><span data-stu-id="92665-197">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="92665-198">Om filerna finns i den aktuella katalogen kan du utelämna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="92665-198">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="92665-199">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="92665-199">Wildcards are permitted.</span></span>

<span data-ttu-id="92665-200">Som standard anges variabla Bryt punkter och kommando Bryt punkter för alla kommandon som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="92665-200">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="92665-201">Den här parametern krävs endast när du anger en rad Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="92665-201">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-202">– Variabel</span><span class="sxs-lookup"><span data-stu-id="92665-202">-Variable</span></span>

<span data-ttu-id="92665-203">Anger en matris med variabler som denna cmdlet anger Bryt punkter för.</span><span class="sxs-lookup"><span data-stu-id="92665-203">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="92665-204">Ange en kommaavgränsad lista med variabler utan dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="92665-204">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="92665-205">Använd parametern **mode** för att fastställa åtkomst läget som utlöser Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="92665-205">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="92665-206">Standard läget, Write, stoppar körningen precis innan ett nytt värde skrivs till variabeln.</span><span class="sxs-lookup"><span data-stu-id="92665-206">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92665-207">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92665-207">CommonParameters</span></span>

<span data-ttu-id="92665-208">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92665-208">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92665-209">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="92665-209">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92665-210">INDATA</span><span class="sxs-lookup"><span data-stu-id="92665-210">INPUTS</span></span>

### <span data-ttu-id="92665-211">Inget</span><span class="sxs-lookup"><span data-stu-id="92665-211">None</span></span>
<span data-ttu-id="92665-212">Du kan inte skicka pipe-ininformation till `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="92665-212">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="92665-213">UTDATA</span><span class="sxs-lookup"><span data-stu-id="92665-213">OUTPUTS</span></span>

### <span data-ttu-id="92665-214">Bryt punkts objekt (system. Management. Automation. LineBreakpoint, system. Management. Automation. VariableBreakpoint, system. Management. Automation. CommandBreakpoint)</span><span class="sxs-lookup"><span data-stu-id="92665-214">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="92665-215">`Set-PSBreakpoint` Returnerar ett objekt som representerar varje Bryt punkt som den anger.</span><span class="sxs-lookup"><span data-stu-id="92665-215">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="92665-216">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="92665-216">NOTES</span></span>

- <span data-ttu-id="92665-217">`Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="92665-217">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="92665-218">Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.</span><span class="sxs-lookup"><span data-stu-id="92665-218">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="92665-219">När du ställer in en Bryt punkt på fler än en rad, ett kommando eller `Set-PSBreakpoint` en variabel, genererar ett Bryt punkts objekt för varje post.</span><span class="sxs-lookup"><span data-stu-id="92665-219">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="92665-220">När du anger en Bryt punkt för en funktion eller variabel i kommando tolken kan du ange Bryt punkten före eller efter att du har skapat funktionen eller variabeln.</span><span class="sxs-lookup"><span data-stu-id="92665-220">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="92665-221">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="92665-221">RELATED LINKS</span></span>

[<span data-ttu-id="92665-222">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="92665-222">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="92665-223">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="92665-223">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="92665-224">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="92665-224">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="92665-225">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="92665-225">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="92665-226">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="92665-226">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)
