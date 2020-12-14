---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710783"
---
# <span data-ttu-id="2ebcb-102">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2ebcb-102">Set-PSBreakpoint</span></span>

## <span data-ttu-id="2ebcb-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2ebcb-103">SYNOPSIS</span></span>
<span data-ttu-id="2ebcb-104">Anger en Bryt punkt för en linje, ett kommando eller en variabel.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-104">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="2ebcb-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ebcb-105">SYNTAX</span></span>

### <span data-ttu-id="2ebcb-106">Rad (standard)</span><span class="sxs-lookup"><span data-stu-id="2ebcb-106">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="2ebcb-107">Kommando</span><span class="sxs-lookup"><span data-stu-id="2ebcb-107">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="2ebcb-108">Variabel</span><span class="sxs-lookup"><span data-stu-id="2ebcb-108">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="2ebcb-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ebcb-109">DESCRIPTION</span></span>

<span data-ttu-id="2ebcb-110">`Set-PSBreakpoint`Cmdleten anger en Bryt punkt i ett skript eller i alla kommando körningar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-110">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="2ebcb-111">Du kan använda `Set-PSBreakpoint` för att ange en Bryt punkt innan du kör ett skript eller kör ett kommando, eller under fel sökning när det stoppas vid en annan Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-111">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="2ebcb-112">`Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-112">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="2ebcb-113">Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-113">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="2ebcb-114">Varje `Set-PSBreakpoint` kommando skapar någon av följande tre typer av Bryt punkter:</span><span class="sxs-lookup"><span data-stu-id="2ebcb-114">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="2ebcb-115">Rad Bryt punkt – anger Bryt punkter vid särskilda rader och kolumn koordinater.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-115">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="2ebcb-116">Kommando Bryt punkt – anger Bryt punkter för kommandon och funktioner.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-116">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="2ebcb-117">Variabel Bryt punkt – anger Bryt punkter för variabler.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-117">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="2ebcb-118">Du kan ange en Bryt punkt för flera rader, kommandon eller variabler i ett enda `Set-PSBreakpoint` kommando, men varje `Set-PSBreakpoint` kommando anger bara en typ av Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-118">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="2ebcb-119">Vid en Bryt punkt slutar PowerShell tillfälligt att köra och ger kontroll till fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-119">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="2ebcb-120">Kommando tolken ändras till `DBG\>` och en uppsättning fel söknings kommandon blir tillgängliga för användning.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-120">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="2ebcb-121">Du kan dock använda **Åtgärds** parametern för att ange ett alternativt svar, till exempel villkor för Bryt punkten eller instruktionerna för att utföra ytterligare åtgärder, till exempel loggning eller diagnostik.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-121">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="2ebcb-122">`Set-PSBreakpoint`Cmdleten är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-122">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="2ebcb-123">Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-123">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="2ebcb-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2ebcb-124">EXAMPLES</span></span>

### <span data-ttu-id="2ebcb-125">Exempel 1: Ange en Bryt punkt på en linje</span><span class="sxs-lookup"><span data-stu-id="2ebcb-125">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="2ebcb-126">I det här exemplet anges en Bryt punkt på rad 5 i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-126">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="2ebcb-127">När skriptet körs stoppar körningen omedelbart innan rad 5 körs.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-127">When the script runs, execution stops immediately before line 5 would execute.</span></span>

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

<span data-ttu-id="2ebcb-128">När du anger en ny Bryt punkt per rad nummer `Set-PSBreakpoint` genererar cmdleten ett rad Bryt punkts objekt (**system. Management. Automation. LineBreakpoint**) som innehåller Bryt punkts-ID och antal träffar.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-128">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object (**System.Management.Automation.LineBreakpoint**) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="2ebcb-129">Exempel 2: Ange en Bryt punkt för en funktion</span><span class="sxs-lookup"><span data-stu-id="2ebcb-129">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="2ebcb-130">I det här exemplet skapas en kommando Bryt punkt för `Increment` funktionen i Sample.ps1 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-130">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="2ebcb-131">Skriptet slutar att köra omedelbart före varje anrop till den angivna funktionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-131">The script stops executing immediately before each call to the specified function.</span></span>

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

<span data-ttu-id="2ebcb-132">Resultatet är ett kommando Bryt punkts objekt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-132">The result is a command breakpoint object.</span></span> <span data-ttu-id="2ebcb-133">Innan skriptet körs är värdet för egenskapen **HitCount** 0.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-133">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="2ebcb-134">Exempel 3: Ange en Bryt punkt för en variabel</span><span class="sxs-lookup"><span data-stu-id="2ebcb-134">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="2ebcb-135">I det här exemplet anges en Bryt punkt för **Server** variabeln i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-135">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="2ebcb-136">Den använder parametern **mode** med värdet **readwrite** för att stoppa körningen när värdet för variabeln läses och precis innan värdet ändras.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-136">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="2ebcb-137">Exempel 4: Ange en Bryt punkt för varje kommando som börjar med angiven text</span><span class="sxs-lookup"><span data-stu-id="2ebcb-137">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="2ebcb-138">I det här exemplet anges en Bryt punkt för varje kommando i Sample.ps1-skriptet som börjar med "Write", till exempel `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="2ebcb-138">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="2ebcb-139">Exempel 5: Ange en Bryt punkt beroende på värdet för en variabel</span><span class="sxs-lookup"><span data-stu-id="2ebcb-139">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="2ebcb-140">I det här exemplet stoppas körningen i `DiskTest` funktionen i Test.ps1-skriptet endast när värdet för `$Disk` variabeln är större än 2.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-140">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="2ebcb-141">Värdet för **åtgärden** är ett skript block som testar värdet för `$Disk` variabeln i funktionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-141">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="2ebcb-142">Åtgärden använder `break` nyckelordet för att stoppa körningen om villkoret är uppfyllt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-142">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="2ebcb-143">Alternativet (och standard) är **fortfarande**.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-143">The alternative (and the default) is **Continue**.</span></span>

### <span data-ttu-id="2ebcb-144">Exempel 6: Ange en Bryt punkt för en funktion</span><span class="sxs-lookup"><span data-stu-id="2ebcb-144">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="2ebcb-145">I det här exemplet anges en Bryt punkt för `CheckLog` funktionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-145">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="2ebcb-146">Eftersom kommandot inte anger något skript, anges Bryt punkten för allt som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-146">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="2ebcb-147">Fel söknings verktyget bryts när funktionen anropas, inte när den har deklarerats.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-147">The debugger breaks when the function is called, not when it is declared.</span></span>

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

### <span data-ttu-id="2ebcb-148">Exempel 7: Ange Bryt punkter på flera rader</span><span class="sxs-lookup"><span data-stu-id="2ebcb-148">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="2ebcb-149">I det här exemplet anges tre rad Bryt punkter i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-149">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="2ebcb-150">Den anger en Bryt punkt i kolumn 2 på var och en av de rader som anges i skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-150">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="2ebcb-151">Den åtgärd som anges i parametern **åtgärd** gäller för alla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-151">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

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

## <span data-ttu-id="2ebcb-152">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2ebcb-152">PARAMETERS</span></span>

### <span data-ttu-id="2ebcb-153">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="2ebcb-153">-Action</span></span>

<span data-ttu-id="2ebcb-154">Anger kommandon som körs vid varje Bryt punkt i stället för att brytas.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-154">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="2ebcb-155">Ange ett skript block som innehåller kommandona.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-155">Enter a script block that contains the commands.</span></span> <span data-ttu-id="2ebcb-156">Du kan använda den här parametern för att ange villkorliga Bryt punkter eller utföra andra uppgifter, till exempel testning eller loggning.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-156">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="2ebcb-157">Om den här parametern utelämnas eller om ingen åtgärd anges, stoppas körningen vid Bryt punkten och fel söknings programmet startar.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-157">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="2ebcb-158">När **Åtgärds** parametern används körs åtgärds skript blocket vid varje Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-158">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="2ebcb-159">Körningen stoppas inte om inte skript blocket innehåller nyckelordet Break.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-159">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="2ebcb-160">Om du använder nyckelordet Continue i-skript blocket återupptas körningen tills nästa Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-160">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="2ebcb-161">Mer information finns i [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)och [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-161">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

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

### <span data-ttu-id="2ebcb-162">-Kolumn</span><span class="sxs-lookup"><span data-stu-id="2ebcb-162">-Column</span></span>

<span data-ttu-id="2ebcb-163">Anger kolumn numret för kolumnen i skript filen där körningen stoppas.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-163">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="2ebcb-164">Ange endast ett kolumn nummer.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-164">Enter only one column number.</span></span> <span data-ttu-id="2ebcb-165">Standardvärdet är kolumn 1.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-165">The default is column 1.</span></span>

<span data-ttu-id="2ebcb-166">Kolumnvärdet används med värdet för **rad** parametern för att ange Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-166">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="2ebcb-167">Om **rad** parametern anger flera rader, anger **kolumn** parametern en Bryt punkt i den angivna kolumnen på var och en av de angivna raderna.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-167">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="2ebcb-168">PowerShell slutar att köra före instruktionen eller uttrycket som innehåller tecknen vid den angivna rad-och kolumn positionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-168">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="2ebcb-169">Kolumner räknas från den övre vänstra marginalen med början på kolumn nummer 1 (inte 0).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-169">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="2ebcb-170">Om du anger en kolumn som inte finns i skriptet, deklareras inte ett fel, men Bryt punkten körs aldrig.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-170">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

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

### <span data-ttu-id="2ebcb-171">-Kommando</span><span class="sxs-lookup"><span data-stu-id="2ebcb-171">-Command</span></span>

<span data-ttu-id="2ebcb-172">Anger en kommando Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-172">Sets a command breakpoint.</span></span> <span data-ttu-id="2ebcb-173">Ange namn på cmdlets, till exempel `Get-Process` eller funktions namn.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-173">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="2ebcb-174">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-174">Wildcards are permitted.</span></span>

<span data-ttu-id="2ebcb-175">Körningen stoppas precis innan varje instans av varje kommando körs.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-175">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="2ebcb-176">Om kommandot är en funktion stoppas körningen varje gång funktionen anropas och vid varje BEGIN-, PROCESS-och END-avsnitt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-176">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

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

### <span data-ttu-id="2ebcb-177">-Rad</span><span class="sxs-lookup"><span data-stu-id="2ebcb-177">-Line</span></span>

<span data-ttu-id="2ebcb-178">Anger en rad Bryt punkt i ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-178">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="2ebcb-179">Ange ett eller flera rad nummer, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-179">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="2ebcb-180">PowerShell stoppas omedelbart innan instruktionen som börjar på var och en av de angivna raderna körs.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-180">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="2ebcb-181">Rader räknas från den övre vänstra marginalen för skript filen som börjar med rad nummer 1 (inte 0).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-181">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="2ebcb-182">Om du anger en tom rad stoppas körningen före nästa icke-tomma rad.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-182">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="2ebcb-183">Om raden är utanför intervallet når Bryt punkten aldrig.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-183">If the line is out of range, the breakpoint is never hit.</span></span>

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

### <span data-ttu-id="2ebcb-184">– Läge</span><span class="sxs-lookup"><span data-stu-id="2ebcb-184">-Mode</span></span>

<span data-ttu-id="2ebcb-185">Anger det åtkomst läge som utlöser variabla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-185">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="2ebcb-186">Standardvärdet är **Write**.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-186">The default is **Write**.</span></span>

<span data-ttu-id="2ebcb-187">Den här parametern är endast giltig när **variabel** parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-187">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="2ebcb-188">Läget gäller för alla Bryt punkter som anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-188">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="2ebcb-189">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="2ebcb-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="2ebcb-190">**Write** -stoppar körningen omedelbart innan ett nytt värde skrivs till variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-190">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="2ebcb-191">**Read** -stoppa körning när variabeln läses, det vill säga när dess värde har använts, antingen för att tilldelas, visas eller användas.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-191">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="2ebcb-192">I läsläge stoppas inte körningen när värdet på variabeln ändras.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-192">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="2ebcb-193">**Readwrite** – stoppar körningen när variabeln läses eller skrivs.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-193">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

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

### <span data-ttu-id="2ebcb-194">– Skript</span><span class="sxs-lookup"><span data-stu-id="2ebcb-194">-Script</span></span>

<span data-ttu-id="2ebcb-195">Anger en matris med skriptfiler som denna cmdlet anger en Bryt punkt i.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-195">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="2ebcb-196">Ange sökvägar och fil namn för en eller flera skriptfiler.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-196">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="2ebcb-197">Om filerna finns i den aktuella katalogen kan du utelämna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-197">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="2ebcb-198">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-198">Wildcards are permitted.</span></span>

<span data-ttu-id="2ebcb-199">Som standard anges variabla Bryt punkter och kommando Bryt punkter för alla kommandon som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-199">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="2ebcb-200">Den här parametern krävs endast när du anger en rad Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-200">This parameter is required only when setting a line breakpoint.</span></span>

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

### <span data-ttu-id="2ebcb-201">– Variabel</span><span class="sxs-lookup"><span data-stu-id="2ebcb-201">-Variable</span></span>

<span data-ttu-id="2ebcb-202">Anger en matris med variabler som denna cmdlet anger Bryt punkter för.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-202">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="2ebcb-203">Ange en kommaavgränsad lista med variabler utan dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-203">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="2ebcb-204">Använd parametern **mode** för att fastställa åtkomst läget som utlöser Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-204">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="2ebcb-205">Standard läget, Write, stoppar körningen precis innan ett nytt värde skrivs till variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-205">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

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

### <span data-ttu-id="2ebcb-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ebcb-206">CommonParameters</span></span>

<span data-ttu-id="2ebcb-207">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ebcb-208">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2ebcb-208">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ebcb-209">INDATA</span><span class="sxs-lookup"><span data-stu-id="2ebcb-209">INPUTS</span></span>

### <span data-ttu-id="2ebcb-210">Inga</span><span class="sxs-lookup"><span data-stu-id="2ebcb-210">None</span></span>
<span data-ttu-id="2ebcb-211">Du kan inte skicka pipe-ininformation till `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="2ebcb-211">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="2ebcb-212">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2ebcb-212">OUTPUTS</span></span>

### <span data-ttu-id="2ebcb-213">Bryt punkts objekt (system. Management. Automation. LineBreakpoint, system. Management. Automation. VariableBreakpoint, system. Management. Automation. CommandBreakpoint)</span><span class="sxs-lookup"><span data-stu-id="2ebcb-213">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="2ebcb-214">`Set-PSBreakpoint` Returnerar ett objekt som representerar varje Bryt punkt som den anger.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-214">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="2ebcb-215">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2ebcb-215">NOTES</span></span>

- <span data-ttu-id="2ebcb-216">`Set-PSBreakpoint` Det går inte att ange en Bryt punkt på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-216">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="2ebcb-217">Om du vill felsöka ett skript på en fjärrdator, kopiera skriptet till den lokala datorn och Felsök det lokalt.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-217">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="2ebcb-218">När du ställer in en Bryt punkt på fler än en rad, ett kommando eller `Set-PSBreakpoint` en variabel, genererar ett Bryt punkts objekt för varje post.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-218">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="2ebcb-219">När du anger en Bryt punkt för en funktion eller variabel i kommando tolken kan du ange Bryt punkten före eller efter att du har skapat funktionen eller variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ebcb-219">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="2ebcb-220">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2ebcb-220">RELATED LINKS</span></span>

[<span data-ttu-id="2ebcb-221">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2ebcb-221">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="2ebcb-222">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2ebcb-222">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="2ebcb-223">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2ebcb-223">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="2ebcb-224">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="2ebcb-224">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="2ebcb-225">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2ebcb-225">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

