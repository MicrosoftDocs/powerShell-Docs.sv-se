---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: c130feac876ff812a854d52961ba3141ba341af0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267038"
---
# <span data-ttu-id="48ad2-103">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-103">Get-PSBreakpoint</span></span>

## <span data-ttu-id="48ad2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="48ad2-104">SYNOPSIS</span></span>
<span data-ttu-id="48ad2-105">Hämtar de Bryt punkter som har angetts i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-105">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="48ad2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="48ad2-106">SYNTAX</span></span>

### <span data-ttu-id="48ad2-107">Skript (standard)</span><span class="sxs-lookup"><span data-stu-id="48ad2-107">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="48ad2-108">Variabel</span><span class="sxs-lookup"><span data-stu-id="48ad2-108">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="48ad2-109">Kommando</span><span class="sxs-lookup"><span data-stu-id="48ad2-109">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="48ad2-110">Typ</span><span class="sxs-lookup"><span data-stu-id="48ad2-110">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="48ad2-111">Id</span><span class="sxs-lookup"><span data-stu-id="48ad2-111">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="48ad2-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="48ad2-112">DESCRIPTION</span></span>

<span data-ttu-id="48ad2-113">**Get-PSBreakPoint** -cmdlet: en hämtar de Bryt punkter som angetts i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-113">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="48ad2-114">Du kan använda cmdlet-parametrarna för att hämta vissa Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="48ad2-114">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="48ad2-115">En Bryt punkt är en punkt i ett kommando eller skript där körningen stoppas tillfälligt så att du kan granska instruktionerna.</span><span class="sxs-lookup"><span data-stu-id="48ad2-115">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="48ad2-116">**Get-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript och-kommandon.</span><span class="sxs-lookup"><span data-stu-id="48ad2-116">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="48ad2-117">Mer information om PowerShell-felsökaren finns i about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="48ad2-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="48ad2-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="48ad2-118">EXAMPLES</span></span>

### <span data-ttu-id="48ad2-119">Exempel 1: Hämta alla Bryt punkter för alla skript och funktioner</span><span class="sxs-lookup"><span data-stu-id="48ad2-119">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="48ad2-120">Det här kommandot hämtar alla Bryt punkter som anges för alla skript och funktioner i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-120">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="48ad2-121">Exempel 2: Hämta Bryt punkter efter ID</span><span class="sxs-lookup"><span data-stu-id="48ad2-121">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="48ad2-122">Det här kommandot hämtar Bryt punkten med Bryt punkts-ID 2.</span><span class="sxs-lookup"><span data-stu-id="48ad2-122">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="48ad2-123">Exempel 3: Skicka ett ID till Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-123">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="48ad2-124">Kommandona visar hur du får en Bryt punkt genom att skicka ett Bryt punkts-ID till **Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="48ad2-124">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="48ad2-125">Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för funktionen Increment i Sample.ps1 skriptet.</span><span class="sxs-lookup"><span data-stu-id="48ad2-125">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="48ad2-126">Det sparar objektet Bryt punkt i $B variabeln.</span><span class="sxs-lookup"><span data-stu-id="48ad2-126">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="48ad2-127">Det andra kommandot använder punkt operatorn (.) för att hämta egenskapen ID för objektet Bryt punkt i $B variabeln.</span><span class="sxs-lookup"><span data-stu-id="48ad2-127">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="48ad2-128">Den använder en pipeline-operator (|) för att skicka ID: t till **Get-PSBreakpoint** -cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="48ad2-128">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="48ad2-129">Resultatet blir att **Get-PSBreakpoint** hämtar Bryt punkten med angivet ID.</span><span class="sxs-lookup"><span data-stu-id="48ad2-129">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="48ad2-130">Exempel 4: Hämta Bryt punkter i angivna skriptfiler</span><span class="sxs-lookup"><span data-stu-id="48ad2-130">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="48ad2-131">Det här kommandot hämtar alla Bryt punkter i Sample.ps1 och SupportScript.ps1 filer.</span><span class="sxs-lookup"><span data-stu-id="48ad2-131">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="48ad2-132">Detta kommando hämtar inte andra Bryt punkter som kan anges i andra skript eller i-funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-132">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="48ad2-133">Exempel 5: Hämta Bryt punkter i angivna cmdlets</span><span class="sxs-lookup"><span data-stu-id="48ad2-133">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="48ad2-134">Det här kommandot hämtar alla kommando Bryt punkter som är inställda på Read-Host eller Write-Host kommandon i Sample.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-134">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="48ad2-135">Exempel 6: Hämta kommando Bryt punkter i en angiven fil</span><span class="sxs-lookup"><span data-stu-id="48ad2-135">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="48ad2-136">Det här kommandot hämtar alla kommando Bryt punkter i Sample.ps1s filen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-136">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="48ad2-137">Exempel 7: Hämta Bryt punkter per variabel</span><span class="sxs-lookup"><span data-stu-id="48ad2-137">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="48ad2-138">Detta kommando hämtar Bryt punkter som har angetts för $Index och $Swap variabler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-138">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="48ad2-139">Exempel 8: Hämta alla rad-och variabel Bryt punkter i en fil</span><span class="sxs-lookup"><span data-stu-id="48ad2-139">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="48ad2-140">Det här kommandot hämtar alla rad-och variabel Bryt punkter i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="48ad2-140">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="48ad2-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="48ad2-141">PARAMETERS</span></span>

### <span data-ttu-id="48ad2-142">-Kommando</span><span class="sxs-lookup"><span data-stu-id="48ad2-142">-Command</span></span>

<span data-ttu-id="48ad2-143">Anger en matris med kommando Bryt punkter som anges för de angivna kommando namnen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-143">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="48ad2-144">Ange kommando namnen, till exempel namnet på en cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="48ad2-144">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48ad2-145">-ID</span><span class="sxs-lookup"><span data-stu-id="48ad2-145">-Id</span></span>

<span data-ttu-id="48ad2-146">Anger de Bryt punkts-ID: n som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="48ad2-146">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="48ad2-147">Ange ID i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="48ad2-147">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="48ad2-148">Du kan också skicka Bryt punkts-ID: n till **Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="48ad2-148">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48ad2-149">– Skript</span><span class="sxs-lookup"><span data-stu-id="48ad2-149">-Script</span></span>

<span data-ttu-id="48ad2-150">Anger en matris med skript som innehåller Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="48ad2-150">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="48ad2-151">Ange sökvägen (valfritt) och namn på en eller flera skriptfiler.</span><span class="sxs-lookup"><span data-stu-id="48ad2-151">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="48ad2-152">Om du utelämnar sökvägen är standard platsen den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-152">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48ad2-153">-Typ</span><span class="sxs-lookup"><span data-stu-id="48ad2-153">-Type</span></span>

<span data-ttu-id="48ad2-154">Anger en matris med Bryt punkts typer som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="48ad2-154">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="48ad2-155">Ange en eller flera typer.</span><span class="sxs-lookup"><span data-stu-id="48ad2-155">Enter one or more types.</span></span>
<span data-ttu-id="48ad2-156">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="48ad2-156">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="48ad2-157">Linje</span><span class="sxs-lookup"><span data-stu-id="48ad2-157">Line</span></span>
- <span data-ttu-id="48ad2-158">Kommando</span><span class="sxs-lookup"><span data-stu-id="48ad2-158">Command</span></span>
- <span data-ttu-id="48ad2-159">Variabel</span><span class="sxs-lookup"><span data-stu-id="48ad2-159">Variable</span></span>

<span data-ttu-id="48ad2-160">Du kan också komma åt Bryt punkts typer för att **få-PSBreakPoint**.</span><span class="sxs-lookup"><span data-stu-id="48ad2-160">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="48ad2-161">– Variabel</span><span class="sxs-lookup"><span data-stu-id="48ad2-161">-Variable</span></span>

<span data-ttu-id="48ad2-162">Anger en matris med variabla Bryt punkter som anges för de angivna variabel namnen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-162">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="48ad2-163">Ange variabel namnen utan dollar tecken.</span><span class="sxs-lookup"><span data-stu-id="48ad2-163">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48ad2-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48ad2-164">CommonParameters</span></span>

<span data-ttu-id="48ad2-165">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48ad2-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48ad2-166">Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="48ad2-166">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48ad2-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="48ad2-167">INPUTS</span></span>

### <span data-ttu-id="48ad2-168">System. Int32, Microsoft. PowerShell. commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="48ad2-168">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="48ad2-169">Du kan skicka Bryt punkts-ID: n och Bryt punkts typer för att **få-PSBreakPoint**</span><span class="sxs-lookup"><span data-stu-id="48ad2-169">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="48ad2-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="48ad2-170">OUTPUTS</span></span>

### <span data-ttu-id="48ad2-171">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="48ad2-171">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="48ad2-172">**Get-PSBreakPoint** returnerar objekt som representerar Bryt punkterna i sessionen.</span><span class="sxs-lookup"><span data-stu-id="48ad2-172">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="48ad2-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="48ad2-173">NOTES</span></span>

* <span data-ttu-id="48ad2-174">Du kan använda **Get-PSBreakpoint** eller dess alias, "GBP".</span><span class="sxs-lookup"><span data-stu-id="48ad2-174">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="48ad2-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="48ad2-175">RELATED LINKS</span></span>

[<span data-ttu-id="48ad2-176">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-176">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="48ad2-177">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-177">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="48ad2-178">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="48ad2-178">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="48ad2-179">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-179">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="48ad2-180">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="48ad2-180">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
