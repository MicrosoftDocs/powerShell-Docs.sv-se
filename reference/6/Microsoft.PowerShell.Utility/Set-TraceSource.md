---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: e6acb18799646a2e238237d3879198e3a78e7f9a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266727"
---
# <span data-ttu-id="ae0cb-103">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="ae0cb-103">Set-TraceSource</span></span>

## <span data-ttu-id="ae0cb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ae0cb-104">SYNOPSIS</span></span>
<span data-ttu-id="ae0cb-105">Konfigurerar, startar och stoppar en spårning av PowerShell-komponenter.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-105">Configures, starts, and stops a trace of PowerShell components.</span></span>

## <span data-ttu-id="ae0cb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ae0cb-106">SYNTAX</span></span>

### <span data-ttu-id="ae0cb-107">optionsSet (standard)</span><span class="sxs-lookup"><span data-stu-id="ae0cb-107">optionsSet (Default)</span></span>

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="ae0cb-108">removeAllListenersSet</span><span class="sxs-lookup"><span data-stu-id="ae0cb-108">removeAllListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="ae0cb-109">removeFileListenersSet</span><span class="sxs-lookup"><span data-stu-id="ae0cb-109">removeFileListenersSet</span></span>

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="ae0cb-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ae0cb-110">DESCRIPTION</span></span>

<span data-ttu-id="ae0cb-111">Cmdleten **set-TraceSource** konfigurerar, startar och stoppar en spårning av en PowerShell-komponent.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-111">The **Set-TraceSource** cmdlet configures, starts, and stops a trace of a PowerShell component.</span></span>
<span data-ttu-id="ae0cb-112">Du kan använda den för att ange vilka komponenter som ska spåras och var spårnings resultatet skickas.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-112">You can use it to specify which components will be traced and where the tracing output is sent.</span></span>

## <span data-ttu-id="ae0cb-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ae0cb-113">EXAMPLES</span></span>

### <span data-ttu-id="ae0cb-114">Exempel 1: spåra ParameterBinding-komponenten</span><span class="sxs-lookup"><span data-stu-id="ae0cb-114">Example 1: Trace the ParameterBinding component</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

<span data-ttu-id="ae0cb-115">Det här kommandot startar spårning för ParameterBinding-komponenten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-115">This command starts tracing for the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="ae0cb-116">Parametern *Name* används för att ange spårnings källa, *alternativ* parametern för att välja ExecutionFlow spårnings händelser och parametern *PSHost* för att välja PowerShell-värdens lyssnare, som skickar utdata till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-116">It uses the *Name* parameter to specify the trace source, the *Option* parameter to select the ExecutionFlow trace events, and the *PSHost* parameter to select the PowerShell host listener, which sends the output to the console.</span></span>
<span data-ttu-id="ae0cb-117">Parametern *ListenerOption* lägger till ProcessID-och timestamp-värden i prefixet spåra meddelande.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-117">The *ListenerOption* parameter adds the ProcessID and TimeStamp values to the trace message prefix.</span></span>

### <span data-ttu-id="ae0cb-118">Exempel 2: stoppa en spårning</span><span class="sxs-lookup"><span data-stu-id="ae0cb-118">Example 2: Stop a trace</span></span>

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

<span data-ttu-id="ae0cb-119">Det här kommandot stoppar spårningen av ParameterBinding-komponenten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-119">This command stops the trace of the ParameterBinding component of PowerShell.</span></span>
<span data-ttu-id="ae0cb-120">Parametern *Name* används för att identifiera den komponent som spårades och *RemoveListener* -parametern för att identifiera spårnings lyssnaren.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-120">It uses the *Name* parameter to identify the component that was being traced and the *RemoveListener* parameter to identify the trace listener.</span></span>

## <span data-ttu-id="ae0cb-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ae0cb-121">PARAMETERS</span></span>

### <span data-ttu-id="ae0cb-122">– Fel sökning</span><span class="sxs-lookup"><span data-stu-id="ae0cb-122">-Debugger</span></span>

<span data-ttu-id="ae0cb-123">Anger att cmdleten skickar spårningsutdata till fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-123">Indicates that the cmdlet sends the trace output to the debugger.</span></span>
<span data-ttu-id="ae0cb-124">Du kan visa utdata i valfri fel sökare för användarläge eller kernelläge eller i Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-124">You can view the output in any user-mode or kernel mode debugger or in Microsoft Visual Studio.</span></span>
<span data-ttu-id="ae0cb-125">Den här parametern väljer också standard spårnings lyssnaren.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-125">This parameter also selects the default trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-126">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="ae0cb-126">-FilePath</span></span>

<span data-ttu-id="ae0cb-127">Anger en fil som denna cmdlet skickar spårningsutdata till.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-127">Specifies a file that this cmdlet sends the trace output to.</span></span>
<span data-ttu-id="ae0cb-128">Den här parametern väljer också lyssnaren för fil spårning.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-128">This parameter also selects the file trace listener.</span></span>
<span data-ttu-id="ae0cb-129">Om du använder den här parametern för att starta spåret använder du parametern *RemoveFileListener* för att stoppa spårningen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-129">If you use this parameter to start the trace, use the *RemoveFileListener* parameter to stop the trace.</span></span>

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-130">-Force</span><span class="sxs-lookup"><span data-stu-id="ae0cb-130">-Force</span></span>

<span data-ttu-id="ae0cb-131">Anger att cmdleten skriver över en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-131">Indicates that the cmdlet overwrites a read-only file.</span></span>
<span data-ttu-id="ae0cb-132">Använd med parametern *sökväg* .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-132">Use with the *FilePath* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-133">-ListenerOption</span><span class="sxs-lookup"><span data-stu-id="ae0cb-133">-ListenerOption</span></span>

<span data-ttu-id="ae0cb-134">Anger valfria data till prefixet för varje spårnings meddelande i utdata.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-134">Specifies optional data to the prefix of each trace message in the output.</span></span>
<span data-ttu-id="ae0cb-135">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ae0cb-136">Inget</span><span class="sxs-lookup"><span data-stu-id="ae0cb-136">None</span></span>
- <span data-ttu-id="ae0cb-137">LogicalOperationStack</span><span class="sxs-lookup"><span data-stu-id="ae0cb-137">LogicalOperationStack</span></span>
- <span data-ttu-id="ae0cb-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="ae0cb-138">DateTime</span></span>
- <span data-ttu-id="ae0cb-139">Timestamp</span><span class="sxs-lookup"><span data-stu-id="ae0cb-139">Timestamp</span></span>
- <span data-ttu-id="ae0cb-140">ProcessId</span><span class="sxs-lookup"><span data-stu-id="ae0cb-140">ProcessId</span></span>
- <span data-ttu-id="ae0cb-141">ThreadId</span><span class="sxs-lookup"><span data-stu-id="ae0cb-141">ThreadId</span></span>
- <span data-ttu-id="ae0cb-142">Callstacken</span><span class="sxs-lookup"><span data-stu-id="ae0cb-142">Callstack</span></span>

<span data-ttu-id="ae0cb-143">Inget är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-143">None is the default.</span></span>

<span data-ttu-id="ae0cb-144">Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem med citat tecken, till exempel "ProcessID, ThreadID".</span><span class="sxs-lookup"><span data-stu-id="ae0cb-144">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "ProcessID,ThreadID".</span></span>

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-145">-Name</span><span class="sxs-lookup"><span data-stu-id="ae0cb-145">-Name</span></span>

<span data-ttu-id="ae0cb-146">Anger vilka komponenter som spåras.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-146">Specifies which components are traced.</span></span>
<span data-ttu-id="ae0cb-147">Ange namnet på spårnings källan för varje komponent.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-147">Enter the name of the trace source of each component.</span></span>
<span data-ttu-id="ae0cb-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-148">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ae0cb-149">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="ae0cb-149">-Option</span></span>

<span data-ttu-id="ae0cb-150">Anger vilken typ av händelser som spåras.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-150">Specifies the type of events that are traced.</span></span>
<span data-ttu-id="ae0cb-151">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-151">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="ae0cb-152">Inget</span><span class="sxs-lookup"><span data-stu-id="ae0cb-152">None</span></span>
- <span data-ttu-id="ae0cb-153">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="ae0cb-153">Constructor</span></span>
- <span data-ttu-id="ae0cb-154">Ta bort</span><span class="sxs-lookup"><span data-stu-id="ae0cb-154">Dispose</span></span>
- <span data-ttu-id="ae0cb-155">Finaliserare</span><span class="sxs-lookup"><span data-stu-id="ae0cb-155">Finalizer</span></span>
- <span data-ttu-id="ae0cb-156">Metod</span><span class="sxs-lookup"><span data-stu-id="ae0cb-156">Method</span></span>
- <span data-ttu-id="ae0cb-157">Egenskap</span><span class="sxs-lookup"><span data-stu-id="ae0cb-157">Property</span></span>
- <span data-ttu-id="ae0cb-158">Delegeringar</span><span class="sxs-lookup"><span data-stu-id="ae0cb-158">Delegates</span></span>
- <span data-ttu-id="ae0cb-159">Händelser</span><span class="sxs-lookup"><span data-stu-id="ae0cb-159">Events</span></span>
- <span data-ttu-id="ae0cb-160">Undantag</span><span class="sxs-lookup"><span data-stu-id="ae0cb-160">Exception</span></span>
- <span data-ttu-id="ae0cb-161">Låsa</span><span class="sxs-lookup"><span data-stu-id="ae0cb-161">Lock</span></span>
- <span data-ttu-id="ae0cb-162">Fel</span><span class="sxs-lookup"><span data-stu-id="ae0cb-162">Error</span></span>
- <span data-ttu-id="ae0cb-163">Fel</span><span class="sxs-lookup"><span data-stu-id="ae0cb-163">Errors</span></span>
- <span data-ttu-id="ae0cb-164">Varning</span><span class="sxs-lookup"><span data-stu-id="ae0cb-164">Warning</span></span>
- <span data-ttu-id="ae0cb-165">Verbose</span><span class="sxs-lookup"><span data-stu-id="ae0cb-165">Verbose</span></span>
- <span data-ttu-id="ae0cb-166">WriteLine</span><span class="sxs-lookup"><span data-stu-id="ae0cb-166">WriteLine</span></span>
- <span data-ttu-id="ae0cb-167">Data</span><span class="sxs-lookup"><span data-stu-id="ae0cb-167">Data</span></span>
- <span data-ttu-id="ae0cb-168">Omfång</span><span class="sxs-lookup"><span data-stu-id="ae0cb-168">Scope</span></span>
- <span data-ttu-id="ae0cb-169">ExecutionFlow</span><span class="sxs-lookup"><span data-stu-id="ae0cb-169">ExecutionFlow</span></span>
- <span data-ttu-id="ae0cb-170">Assert</span><span class="sxs-lookup"><span data-stu-id="ae0cb-170">Assert</span></span>
- <span data-ttu-id="ae0cb-171">Alla</span><span class="sxs-lookup"><span data-stu-id="ae0cb-171">All</span></span>

<span data-ttu-id="ae0cb-172">All är standard.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-172">All is the default.</span></span>

<span data-ttu-id="ae0cb-173">Följande värden är kombinationer av andra värden:</span><span class="sxs-lookup"><span data-stu-id="ae0cb-173">The following values are combinations of other values:</span></span>

- <span data-ttu-id="ae0cb-174">ExecutionFlow: (konstruktör, dispose, slut för ande, metod, ombud, händelser och omfång)</span><span class="sxs-lookup"><span data-stu-id="ae0cb-174">ExecutionFlow: (Constructor, Dispose, Finalizer, Method, Delegates, Events, and Scope)</span></span>
- <span data-ttu-id="ae0cb-175">Data: (konstruktor, dispose, slutförd, egenskap, utförlig och WriteLine)</span><span class="sxs-lookup"><span data-stu-id="ae0cb-175">Data: (Constructor, Dispose, Finalizer, Property, Verbose, and WriteLine)</span></span>
- <span data-ttu-id="ae0cb-176">Fel: (fel och undantag).</span><span class="sxs-lookup"><span data-stu-id="ae0cb-176">Errors: (Error and Exception).</span></span>

<span data-ttu-id="ae0cb-177">Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem inom citat tecken, till exempel "konstruktor, dispose".</span><span class="sxs-lookup"><span data-stu-id="ae0cb-177">To specify multiple options, separate them with commas, but with no spaces, and enclose them in quotation marks, such as "Constructor,Dispose".</span></span>

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-178">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ae0cb-178">-PassThru</span></span>

<span data-ttu-id="ae0cb-179">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="ae0cb-180">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-181">-PSHost</span><span class="sxs-lookup"><span data-stu-id="ae0cb-181">-PSHost</span></span>

<span data-ttu-id="ae0cb-182">ndicates att den här cmdleten skickar spårningsutdata till PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-182">ndicates that this cmdlet sends the trace output to the PowerShell host.</span></span>
<span data-ttu-id="ae0cb-183">Den här parametern väljer också spårnings lyssnaren PSHost.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-183">This parameter also selects the PSHost trace listener.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-184">-RemoveFileListener</span><span class="sxs-lookup"><span data-stu-id="ae0cb-184">-RemoveFileListener</span></span>

<span data-ttu-id="ae0cb-185">Stoppar spårningen genom att ta bort den lyssnare för fil spårning som är associerad med den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-185">Stops the trace by removing the file trace listener associated with the specified file.</span></span>
<span data-ttu-id="ae0cb-186">Ange sökvägen till och fil namnet på filen med spårnings utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-186">Enter the path and file name of the trace output file.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-187">-RemoveListener</span><span class="sxs-lookup"><span data-stu-id="ae0cb-187">-RemoveListener</span></span>

<span data-ttu-id="ae0cb-188">Stoppar spårningen genom att ta bort spårnings lyssnaren.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-188">Stops the trace by removing the trace listener.</span></span>

<span data-ttu-id="ae0cb-189">Använd följande värden med *RemoveListener* :</span><span class="sxs-lookup"><span data-stu-id="ae0cb-189">Use the following values with *RemoveListener* :</span></span>

- <span data-ttu-id="ae0cb-190">Om du vill ta bort PSHost (konsol) skriver du `Host` .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-190">To remove PSHost (console), type `Host`.</span></span>
- <span data-ttu-id="ae0cb-191">Om du vill ta bort fel sökare skriver du `Debug` .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-191">To remove Debugger, type `Debug`.</span></span>
- <span data-ttu-id="ae0cb-192">Om du vill ta bort alla spårnings lyssnare skriver du `*` .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-192">To remove all trace listeners, type `*`.</span></span>

<span data-ttu-id="ae0cb-193">Om du vill ta bort fil spårnings lyssnaren använder du parametern *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-193">To remove the file trace listener, use the *RemoveFileListener* parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ae0cb-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ae0cb-194">CommonParameters</span></span>

<span data-ttu-id="ae0cb-195">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ae0cb-196">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ae0cb-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ae0cb-197">INDATA</span><span class="sxs-lookup"><span data-stu-id="ae0cb-197">INPUTS</span></span>

### <span data-ttu-id="ae0cb-198">System. String</span><span class="sxs-lookup"><span data-stu-id="ae0cb-198">System.String</span></span>

<span data-ttu-id="ae0cb-199">Du kan skicka en sträng som innehåller ett namn till **set-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-199">You can pipe a string that contains a name to **Set-TraceSource**.</span></span>

## <span data-ttu-id="ae0cb-200">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ae0cb-200">OUTPUTS</span></span>

### <span data-ttu-id="ae0cb-201">Ingen eller system. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="ae0cb-201">None or System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="ae0cb-202">När du använder parametern *Passthru* genererar **set-TraceSource** ett **system. Management. Automation. PSTraceSource** -objekt som representerar spårningssessionen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-202">When you use the *PassThru* parameter, **Set-TraceSource** generates a **System.Management.Automation.PSTraceSource** object representing the trace session.</span></span>
<span data-ttu-id="ae0cb-203">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ae0cb-204">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ae0cb-204">NOTES</span></span>

* <span data-ttu-id="ae0cb-205">Spårning är en metod som utvecklare använder för att felsöka och förfina program.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-205">Tracing is a method that developers use to debug and refine programs.</span></span> <span data-ttu-id="ae0cb-206">När du spårar genererar programmet detaljerade meddelanden om varje steg i den interna bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-206">When tracing, the program generates detailed messages about each step in its internal processing.</span></span>

  <span data-ttu-id="ae0cb-207">Cmdletarna för PowerShell-spårning är utformade för att hjälpa PowerShell-utvecklare, men de är tillgängliga för alla användare.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-207">The PowerShell tracing cmdlets are designed to help PowerShell developers, but they are available to all users.</span></span>
<span data-ttu-id="ae0cb-208">De låter dig övervaka nästan alla aspekter av funktionerna i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-208">They let you monitor nearly every aspect of the functionality of PowerShell.</span></span>

  <span data-ttu-id="ae0cb-209">En spårnings källa är en del av varje PowerShell-komponent som hanterar spårning och genererar spårnings meddelanden för komponenten.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-209">A trace source is the part of each PowerShell component that manages tracing and generates trace messages for the component.</span></span>
<span data-ttu-id="ae0cb-210">Om du vill spåra en komponent identifierar du dess spårnings källa.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-210">To trace a component, you identify its trace source.</span></span>

  <span data-ttu-id="ae0cb-211">En spårnings lyssnare tar emot utdata från spårningen och visar den för användaren.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-211">A trace listener receives the output of the trace and displays it to the user.</span></span>
<span data-ttu-id="ae0cb-212">Du kan välja att skicka spårnings data till en användar-eller kernelläge, till-konsolen, till en fil eller till en anpassad lyssnare som härletts från klassen **system. Diagnostics. TraceListener** .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-212">You can elect to send the trace data to a user-mode or kernel-mode debugger, to the console, to a file, or to a custom listener derived from the **System.Diagnostics.TraceListener** class.</span></span>

* <span data-ttu-id="ae0cb-213">Om du vill starta en spårning använder du parametern *Name* för att ange en spårnings källa och *sökvägen* , *fel sökaren* eller *PSHost* -parametrarna för att ange en lyssnare (ett mål för utdata).</span><span class="sxs-lookup"><span data-stu-id="ae0cb-213">To start a trace, use the *Name* parameter to specify a trace source and the *FilePath* , *Debugger* , or *PSHost* parameters to specify a listener (a destination for the output).</span></span> <span data-ttu-id="ae0cb-214">Använd *alternativ* parametern för att bestämma vilka typer av händelser som spåras och parametern *ListenerOption* för att konfigurera spårningsutdata.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-214">Use the *Options* parameter to determine the types of events that are traced and the *ListenerOption* parameter to configure the trace output.</span></span>
* <span data-ttu-id="ae0cb-215">Om du vill ändra konfigurationen för en spårning anger du ett **set-TraceSource-** kommando som du skulle starta en spårning.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-215">To change the configuration of a trace, enter a **Set-TraceSource** command as you would to start a trace.</span></span> <span data-ttu-id="ae0cb-216">PowerShell känner av att spårnings källan redan spåras.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-216">PowerShell recognizes that the trace source is already being traced.</span></span> <span data-ttu-id="ae0cb-217">Den stoppar spårningen, lägger till den nya konfigurationen och startar eller startar om spårningen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-217">It stops the trace, adds the new configuration, and starts or restarts the trace.</span></span>
* <span data-ttu-id="ae0cb-218">Om du vill stoppa en spårning använder du parametern *RemoveListener* .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-218">To stop a trace, use the *RemoveListener* parameter.</span></span> <span data-ttu-id="ae0cb-219">Om du vill stoppa en spårning som använder fil lyssnaren (en spårning som har startats med hjälp av parametern *sökväg* ) använder du parametern *RemoveFileListener* .</span><span class="sxs-lookup"><span data-stu-id="ae0cb-219">To stop a trace that uses the file listener (a trace started by using the *FilePath* parameter), use the *RemoveFileListener* parameter.</span></span> <span data-ttu-id="ae0cb-220">När du tar bort lyssnaren stoppas spårningen.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-220">When you remove the listener, the trace stops.</span></span>
* <span data-ttu-id="ae0cb-221">Använd Get-TraceSource för att avgöra vilka komponenter som kan spåras.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-221">To determine which components can be traced, use Get-TraceSource.</span></span> <span data-ttu-id="ae0cb-222">Spårnings källorna för varje modul läses in automatiskt när komponenten används och de visas i resultatet av **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="ae0cb-222">The trace sources for each module are loaded automatically when the component is in use, and they appear in the output of **Get-TraceSource**.</span></span>

## <span data-ttu-id="ae0cb-223">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ae0cb-223">RELATED LINKS</span></span>

[<span data-ttu-id="ae0cb-224">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="ae0cb-224">Get-TraceSource</span></span>](Get-TraceSource.md)

[<span data-ttu-id="ae0cb-225">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="ae0cb-225">Trace-Command</span></span>](Trace-Command.md)
