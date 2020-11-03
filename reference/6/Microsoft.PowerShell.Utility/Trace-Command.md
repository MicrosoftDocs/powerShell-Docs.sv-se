---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 9147be62c881e81a4ff1352a1b9fe7a34d2610cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266715"
---
# <span data-ttu-id="671c0-103">Trace-Command</span><span class="sxs-lookup"><span data-stu-id="671c0-103">Trace-Command</span></span>

## <span data-ttu-id="671c0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="671c0-104">SYNOPSIS</span></span>
<span data-ttu-id="671c0-105">Konfigurerar och startar en spårning av det angivna uttrycket eller kommandot.</span><span class="sxs-lookup"><span data-stu-id="671c0-105">Configures and starts a trace of the specified expression or command.</span></span>

## <span data-ttu-id="671c0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="671c0-106">SYNTAX</span></span>

### <span data-ttu-id="671c0-107">expressionSet (standard)</span><span class="sxs-lookup"><span data-stu-id="671c0-107">expressionSet (Default)</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### <span data-ttu-id="671c0-108">commandSet</span><span class="sxs-lookup"><span data-stu-id="671c0-108">commandSet</span></span>

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## <span data-ttu-id="671c0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="671c0-109">DESCRIPTION</span></span>
<span data-ttu-id="671c0-110">`Trace-Command`Cmdleten konfigurerar och startar en spårning av det angivna uttrycket eller kommandot.</span><span class="sxs-lookup"><span data-stu-id="671c0-110">The `Trace-Command` cmdlet configures and starts a trace of the specified expression or command.</span></span>
<span data-ttu-id="671c0-111">Den fungerar som set-TraceSource, förutom att den endast gäller för det angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="671c0-111">It works like Set-TraceSource, except that it applies only to the specified command.</span></span>

## <span data-ttu-id="671c0-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="671c0-112">EXAMPLES</span></span>

### <span data-ttu-id="671c0-113">Exempel 1: spåra metadata-bearbetning, parameter bindning och ett uttryck</span><span class="sxs-lookup"><span data-stu-id="671c0-113">Example 1: Trace metadata processing, parameter binding, and an expression</span></span>

<span data-ttu-id="671c0-114">I det här exemplet startas en spårning av metadata-bearbetning, parameter bindning och skapande och destruktion av uttrycket för cmdleten `Get-Process Notepad` .</span><span class="sxs-lookup"><span data-stu-id="671c0-114">This example starts a trace of metadata processing, parameter binding, and cmdlet creation and destruction of the `Get-Process Notepad` expression.</span></span>

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

<span data-ttu-id="671c0-115">Parametern **Name** används för att ange spårnings källorna, **uttrycks** parametern för att ange kommandot och parametern **PSHost** för att skicka utdata till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="671c0-115">It uses the **Name** parameter to specify the trace sources, the **Expression** parameter to specify the command, and the **PSHost** parameter to send the output to the console.</span></span> <span data-ttu-id="671c0-116">Eftersom det inte anger några spårnings alternativ eller lyssnar alternativ använder kommandot standardvärdena:</span><span class="sxs-lookup"><span data-stu-id="671c0-116">Because it does not specify any tracing options or listener options, the command uses the defaults:</span></span>

- <span data-ttu-id="671c0-117">Alla för spårnings alternativ</span><span class="sxs-lookup"><span data-stu-id="671c0-117">All for the tracing options</span></span>
- <span data-ttu-id="671c0-118">Ingen för alternativen för lyssnare</span><span class="sxs-lookup"><span data-stu-id="671c0-118">None for the listener options</span></span>

### <span data-ttu-id="671c0-119">Exempel 2: spåra åtgärder för ParameterBinding-åtgärder</span><span class="sxs-lookup"><span data-stu-id="671c0-119">Example 2: Trace the actions of ParameterBinding operations</span></span>

<span data-ttu-id="671c0-120">Det här exemplet spårar åtgärder för **ParameterBinding** -åtgärder för PowerShell medan den bearbetar ett `Get-Alias` uttryck som tar emot inmatade från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="671c0-120">This example traces the actions of the **ParameterBinding** operations of PowerShell while it processes a `Get-Alias` expression that takes input from the pipeline.</span></span>

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

<span data-ttu-id="671c0-121">I `Trace-Command` skickar **InputObject** -parametern ett objekt till det uttryck som bearbetas under spårningen.</span><span class="sxs-lookup"><span data-stu-id="671c0-121">In `Trace-Command`, the **InputObject** parameter passes an object to the expression that is being processed during the trace.</span></span>

<span data-ttu-id="671c0-122">Det första kommandot lagrar strängen `i*` i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="671c0-122">The first command stores the string `i*` in the `$A` variable.</span></span> <span data-ttu-id="671c0-123">Det andra kommandot använder `Trace-Command` cmdleten med ParameterBinding spårnings källa.</span><span class="sxs-lookup"><span data-stu-id="671c0-123">The second command uses the `Trace-Command` cmdlet with the ParameterBinding trace source.</span></span> <span data-ttu-id="671c0-124">Parametern **PSHost** skickar utdata till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="671c0-124">The **PSHost** parameter sends the output to the console.</span></span>

<span data-ttu-id="671c0-125">Uttrycket som bearbetas är `Get-Alias $Input` , där `$Input` variabeln är associerad med parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="671c0-125">The expression being processed is `Get-Alias $Input`, where the `$Input` variable is associated with the **InputObject** parameter.</span></span> <span data-ttu-id="671c0-126">Parametern **InputObject** skickar variabeln `$A` till uttrycket.</span><span class="sxs-lookup"><span data-stu-id="671c0-126">The **InputObject** parameter passes the variable `$A` to the expression.</span></span> <span data-ttu-id="671c0-127">I praktiken är kommandot som bearbetas under spårningen `Get-Alias -InputObject $A" or "$A | Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="671c0-127">In effect, the command being processed during the trace is `Get-Alias -InputObject $A" or "$A | Get-Alias`.</span></span>

## <span data-ttu-id="671c0-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="671c0-128">PARAMETERS</span></span>

### <span data-ttu-id="671c0-129">– Argument List</span><span class="sxs-lookup"><span data-stu-id="671c0-129">-ArgumentList</span></span>

<span data-ttu-id="671c0-130">Anger parametrar och parameter värden för det kommando som spåras.</span><span class="sxs-lookup"><span data-stu-id="671c0-130">Specifies the parameters and parameter values for the command being traced.</span></span> <span data-ttu-id="671c0-131">Aliaset för **argument List** är **argument**.</span><span class="sxs-lookup"><span data-stu-id="671c0-131">The alias for **ArgumentList** is **Args**.</span></span> <span data-ttu-id="671c0-132">Den här funktionen är särskilt användbar för fel sökning av dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="671c0-132">This feature is especially useful for debugging dynamic parameters.</span></span>

<span data-ttu-id="671c0-133">Mer information om beteendet för **argument List** finns [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="671c0-133">For more information about the behavior of **ArgumentList** , see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-134">-Kommando</span><span class="sxs-lookup"><span data-stu-id="671c0-134">-Command</span></span>

<span data-ttu-id="671c0-135">Anger ett kommando som bearbetas under spårningen.</span><span class="sxs-lookup"><span data-stu-id="671c0-135">Specifies a command that is being processed during the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-136">– Fel sökning</span><span class="sxs-lookup"><span data-stu-id="671c0-136">-Debugger</span></span>

<span data-ttu-id="671c0-137">Anger att cmdleten skickar spårningsutdata till fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="671c0-137">Indicates that the cmdlet sends the trace output to the debugger.</span></span> <span data-ttu-id="671c0-138">Du kan visa utdata i valfri fel sökare för användarläge eller kernelläge eller i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="671c0-138">You can view the output in any user-mode or kernel mode debugger or in Visual Studio.</span></span> <span data-ttu-id="671c0-139">Den här parametern väljer också standard spårnings lyssnaren.</span><span class="sxs-lookup"><span data-stu-id="671c0-139">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-140">– Uttryck</span><span class="sxs-lookup"><span data-stu-id="671c0-140">-Expression</span></span>

<span data-ttu-id="671c0-141">Anger det uttryck som bearbetas under spårningen.</span><span class="sxs-lookup"><span data-stu-id="671c0-141">Specifies the expression that is being processed during the trace.</span></span> <span data-ttu-id="671c0-142">Omge uttrycket med klammerparenteser ( `{}` ).</span><span class="sxs-lookup"><span data-stu-id="671c0-142">Enclose the expression in braces (`{}`).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-143">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="671c0-143">-FilePath</span></span>

<span data-ttu-id="671c0-144">Anger en fil som cmdleten skickar spårningsutdata till.</span><span class="sxs-lookup"><span data-stu-id="671c0-144">Specifies a file that the cmdlet sends the trace output to.</span></span> <span data-ttu-id="671c0-145">Den här parametern väljer också lyssnaren för fil spårning.</span><span class="sxs-lookup"><span data-stu-id="671c0-145">This parameter also selects the file trace listener.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-146">-Force</span><span class="sxs-lookup"><span data-stu-id="671c0-146">-Force</span></span>

<span data-ttu-id="671c0-147">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="671c0-147">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="671c0-148">Används med parametern **sökväg** .</span><span class="sxs-lookup"><span data-stu-id="671c0-148">Used with the **FilePath** parameter.</span></span> <span data-ttu-id="671c0-149">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="671c0-149">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-150">– InputObject</span><span class="sxs-lookup"><span data-stu-id="671c0-150">-InputObject</span></span>

<span data-ttu-id="671c0-151">Anger ininformation till det uttryck som bearbetas under spårningen.</span><span class="sxs-lookup"><span data-stu-id="671c0-151">Specifies input to the expression that is being processed during the trace.</span></span> <span data-ttu-id="671c0-152">Du kan ange en variabel som representerar inmatade uttryck eller skicka ett objekt via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="671c0-152">You can enter a variable that represents the input that the expression accepts, or pass an object through the pipeline.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-153">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="671c0-153">-ListenerOption</span></span>

<span data-ttu-id="671c0-154">Anger valfria data till prefixet för varje spårnings meddelande i utdata.</span><span class="sxs-lookup"><span data-stu-id="671c0-154">Specifies optional data to the prefix of each trace message in the output.</span></span> <span data-ttu-id="671c0-155">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="671c0-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="671c0-156">Inget</span><span class="sxs-lookup"><span data-stu-id="671c0-156">None</span></span>
- <span data-ttu-id="671c0-157">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="671c0-157">LogicalOperationStack</span></span>
- <span data-ttu-id="671c0-158">DateTime</span><span class="sxs-lookup"><span data-stu-id="671c0-158">DateTime</span></span>
- <span data-ttu-id="671c0-159">Timestamp</span><span class="sxs-lookup"><span data-stu-id="671c0-159">Timestamp</span></span>
- <span data-ttu-id="671c0-160">ProcessId</span><span class="sxs-lookup"><span data-stu-id="671c0-160">ProcessId</span></span>
- <span data-ttu-id="671c0-161">ThreadId</span><span class="sxs-lookup"><span data-stu-id="671c0-161">ThreadId</span></span>
- <span data-ttu-id="671c0-162">Callstacken</span><span class="sxs-lookup"><span data-stu-id="671c0-162">Callstack</span></span>

<span data-ttu-id="671c0-163">**Inget** är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="671c0-163">**None** is the default.</span></span>

<span data-ttu-id="671c0-164">Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem med citat tecken, till exempel "ProcessID, ThreadID".</span><span class="sxs-lookup"><span data-stu-id="671c0-164">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-165">-Name</span><span class="sxs-lookup"><span data-stu-id="671c0-165">-Name</span></span>

<span data-ttu-id="671c0-166">Anger en matris med PowerShell-komponenter som spåras.</span><span class="sxs-lookup"><span data-stu-id="671c0-166">Specifies an array of PowerShell components that are traced.</span></span> <span data-ttu-id="671c0-167">Ange namnet på spårnings källan för varje komponent.</span><span class="sxs-lookup"><span data-stu-id="671c0-167">Enter the name of the trace source of each component.</span></span> <span data-ttu-id="671c0-168">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="671c0-168">Wildcards are permitted.</span></span> <span data-ttu-id="671c0-169">Om du vill hitta spårnings källorna på datorn skriver du `Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="671c0-169">To find the trace sources on your computer, type `Get-TraceSource`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-170">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="671c0-170">-Option</span></span>

<span data-ttu-id="671c0-171">Bestämmer vilken typ av händelser som spåras.</span><span class="sxs-lookup"><span data-stu-id="671c0-171">Determines the type of events that are traced.</span></span> <span data-ttu-id="671c0-172">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="671c0-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="671c0-173">Inget</span><span class="sxs-lookup"><span data-stu-id="671c0-173">None</span></span>
- <span data-ttu-id="671c0-174">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="671c0-174">Constructor</span></span>
- <span data-ttu-id="671c0-175">Ta bort</span><span class="sxs-lookup"><span data-stu-id="671c0-175">Dispose</span></span>
- <span data-ttu-id="671c0-176">Finaliserare</span><span class="sxs-lookup"><span data-stu-id="671c0-176">Finalizer</span></span>
- <span data-ttu-id="671c0-177">Metod</span><span class="sxs-lookup"><span data-stu-id="671c0-177">Method</span></span>
- <span data-ttu-id="671c0-178">Egenskap</span><span class="sxs-lookup"><span data-stu-id="671c0-178">Property</span></span>
- <span data-ttu-id="671c0-179">Delegeringar</span><span class="sxs-lookup"><span data-stu-id="671c0-179">Delegates</span></span>
- <span data-ttu-id="671c0-180">Händelser</span><span class="sxs-lookup"><span data-stu-id="671c0-180">Events</span></span>
- <span data-ttu-id="671c0-181">Undantag</span><span class="sxs-lookup"><span data-stu-id="671c0-181">Exception</span></span>
- <span data-ttu-id="671c0-182">Låsa</span><span class="sxs-lookup"><span data-stu-id="671c0-182">Lock</span></span>
- <span data-ttu-id="671c0-183">Fel</span><span class="sxs-lookup"><span data-stu-id="671c0-183">Error</span></span>
- <span data-ttu-id="671c0-184">Fel</span><span class="sxs-lookup"><span data-stu-id="671c0-184">Errors</span></span>
- <span data-ttu-id="671c0-185">Varning</span><span class="sxs-lookup"><span data-stu-id="671c0-185">Warning</span></span>
- <span data-ttu-id="671c0-186">Verbose</span><span class="sxs-lookup"><span data-stu-id="671c0-186">Verbose</span></span>
- <span data-ttu-id="671c0-187">WriteLine</span><span class="sxs-lookup"><span data-stu-id="671c0-187">WriteLine</span></span>
- <span data-ttu-id="671c0-188">Data</span><span class="sxs-lookup"><span data-stu-id="671c0-188">Data</span></span>
- <span data-ttu-id="671c0-189">Omfång</span><span class="sxs-lookup"><span data-stu-id="671c0-189">Scope</span></span>
- <span data-ttu-id="671c0-190">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="671c0-190">ExecutionFlow</span></span>
- <span data-ttu-id="671c0-191">Assert</span><span class="sxs-lookup"><span data-stu-id="671c0-191">Assert</span></span>
- <span data-ttu-id="671c0-192">Alla</span><span class="sxs-lookup"><span data-stu-id="671c0-192">All</span></span>

<span data-ttu-id="671c0-193">All är standard.</span><span class="sxs-lookup"><span data-stu-id="671c0-193">All is the default.</span></span>

<span data-ttu-id="671c0-194">Följande värden är kombinationer av andra värden:</span><span class="sxs-lookup"><span data-stu-id="671c0-194">The following values are combinations of other values:</span></span>

- <span data-ttu-id="671c0-195">ExecutionFlow: (konstruktör, dispose, slut för ande, metod, ombud, händelser och omfång)</span><span class="sxs-lookup"><span data-stu-id="671c0-195">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="671c0-196">Data: (konstruktor, dispose, slutförd, egenskap, utförlig och WriteLine)</span><span class="sxs-lookup"><span data-stu-id="671c0-196">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="671c0-197">Fel: (fel och undantag).</span><span class="sxs-lookup"><span data-stu-id="671c0-197">Errors: (Error and Exception).</span></span>

<span data-ttu-id="671c0-198">Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem inom citat tecken, till exempel "konstruktor, dispose".</span><span class="sxs-lookup"><span data-stu-id="671c0-198">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-199">-PSHost</span><span class="sxs-lookup"><span data-stu-id="671c0-199">-PSHost</span></span>

<span data-ttu-id="671c0-200">Anger att cmdleten skickar spårningsutdata till PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="671c0-200">Indicates that the cmdlet sends the trace output to the PowerShell host.</span></span> <span data-ttu-id="671c0-201">Den här parametern väljer också spårnings lyssnaren PSHost.</span><span class="sxs-lookup"><span data-stu-id="671c0-201">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="671c0-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="671c0-202">CommonParameters</span></span>

<span data-ttu-id="671c0-203">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="671c0-203">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="671c0-204">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="671c0-204">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="671c0-205">INDATA</span><span class="sxs-lookup"><span data-stu-id="671c0-205">INPUTS</span></span>

### <span data-ttu-id="671c0-206">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="671c0-206">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="671c0-207">Du kan skicka pipe-objekt som representerar inmatade uttryck till `Trace-Command` .</span><span class="sxs-lookup"><span data-stu-id="671c0-207">You can pipe objects that represent input to the expression to `Trace-Command`.</span></span>

## <span data-ttu-id="671c0-208">UTDATA</span><span class="sxs-lookup"><span data-stu-id="671c0-208">OUTPUTS</span></span>

### <span data-ttu-id="671c0-209">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="671c0-209">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="671c0-210">Returnerar kommando spårningen i fel söknings data strömmen.</span><span class="sxs-lookup"><span data-stu-id="671c0-210">Returns the command trace in the debug stream.</span></span>

## <span data-ttu-id="671c0-211">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="671c0-211">NOTES</span></span>

- <span data-ttu-id="671c0-212">Spårning är en metod som utvecklare använder för att felsöka och förfina program.</span><span class="sxs-lookup"><span data-stu-id="671c0-212">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="671c0-213">När du spårar genererar programmet detaljerade meddelanden om varje steg i den interna bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="671c0-213">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

- <span data-ttu-id="671c0-214">Cmdletarna för PowerShell-spårning är utformade för att hjälpa PowerShell-utvecklare, men de är tillgängliga för alla användare.</span><span class="sxs-lookup"><span data-stu-id="671c0-214">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span> <span data-ttu-id="671c0-215">De gör det möjligt för dig att övervaka nästan varje aspekt av funktionerna i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="671c0-215">They let you monitor nearly every aspect of the functionality of the shell.</span></span>

- <span data-ttu-id="671c0-216">Om du vill hitta de PowerShell-komponenter som är aktiverade för spårning skriver du `Get-Help Get-TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="671c0-216">To find the PowerShell components that are enabled for tracing, type `Get-Help Get-TraceSource`.</span></span>

  <span data-ttu-id="671c0-217">En spårnings källa är en del av varje PowerShell-komponent som hanterar spårning och genererar spårnings meddelanden för komponenten.</span><span class="sxs-lookup"><span data-stu-id="671c0-217">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span> <span data-ttu-id="671c0-218">Om du vill spåra en komponent identifierar du dess spårnings källa.</span><span class="sxs-lookup"><span data-stu-id="671c0-218">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="671c0-219">En spårnings lyssnare tar emot utdata från spårningen och visar den för användaren.</span><span class="sxs-lookup"><span data-stu-id="671c0-219">A trace listener receives the output of the trace and displays it to the user.</span></span> <span data-ttu-id="671c0-220">Du kan välja att skicka spårnings data till en användar-eller kernelläge, till värden eller konsolen, till en fil eller till en anpassad lyssnare som härletts från klassen **system. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="671c0-220">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the host or console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

- <span data-ttu-id="671c0-221">När du använder parameter uppsättningen commandSet, bearbetar PowerShell kommandot precis som det skulle bearbetas i en pipeline.</span><span class="sxs-lookup"><span data-stu-id="671c0-221">When you use the commandSet parameter set, PowerShell processes the command just as it would be processed in a pipeline.</span></span> <span data-ttu-id="671c0-222">Till exempel upprepas inte kommando identifiering för varje inkommande objekt.</span><span class="sxs-lookup"><span data-stu-id="671c0-222">For example, command discovery is not repeated for each incoming object.</span></span>

- <span data-ttu-id="671c0-223">Namnen på **namn** , **uttryck** , **alternativ** och **kommando** parametrar är valfria.</span><span class="sxs-lookup"><span data-stu-id="671c0-223">The names of the **Name** , **Expression** , **Option** , and **Command** parameters are optional.</span></span> <span data-ttu-id="671c0-224">Om du utelämnar parameter namnen måste de parameter värden som inte är namngivna visas i den här ordningen: **namn** , **uttryck** , **alternativ** eller **namn** , **kommando** , **alternativ**.</span><span class="sxs-lookup"><span data-stu-id="671c0-224">If you omit the parameter names, the unnamed parameter values must appear in this order: **Name** , **Expression** , **Option** or **Name** , **Command** , **Option**.</span></span> <span data-ttu-id="671c0-225">Om du inkluderar parameter namnen kan parametrarna visas i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="671c0-225">If you include the parameter names, the parameters can appear in any order.</span></span>

## <span data-ttu-id="671c0-226">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="671c0-226">RELATED LINKS</span></span>

[<span data-ttu-id="671c0-227">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="671c0-227">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="671c0-228">Measure-Command</span><span class="sxs-lookup"><span data-stu-id="671c0-228">Measure-Command</span></span>](Measure-Command.md)

[<span data-ttu-id="671c0-229">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="671c0-229">Set-TraceSource</span></span>](Set-TraceSource.md)
