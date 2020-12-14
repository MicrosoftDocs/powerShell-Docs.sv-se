---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708634"
---
# <span data-ttu-id="4daa0-102">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-102">Get-PSBreakpoint</span></span>

## <span data-ttu-id="4daa0-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4daa0-103">SYNOPSIS</span></span>
<span data-ttu-id="4daa0-104">Hämtar de Bryt punkter som har angetts i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-104">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="4daa0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4daa0-105">SYNTAX</span></span>

### <span data-ttu-id="4daa0-106">Skript (standard)</span><span class="sxs-lookup"><span data-stu-id="4daa0-106">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4daa0-107">Variabel</span><span class="sxs-lookup"><span data-stu-id="4daa0-107">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="4daa0-108">Kommando</span><span class="sxs-lookup"><span data-stu-id="4daa0-108">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="4daa0-109">Typ</span><span class="sxs-lookup"><span data-stu-id="4daa0-109">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="4daa0-110">Id</span><span class="sxs-lookup"><span data-stu-id="4daa0-110">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="4daa0-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4daa0-111">DESCRIPTION</span></span>

<span data-ttu-id="4daa0-112">**Get-PSBreakPoint** -cmdlet: en hämtar de Bryt punkter som angetts i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-112">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="4daa0-113">Du kan använda cmdlet-parametrarna för att hämta vissa Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="4daa0-113">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="4daa0-114">En Bryt punkt är en punkt i ett kommando eller skript där körningen stoppas tillfälligt så att du kan granska instruktionerna.</span><span class="sxs-lookup"><span data-stu-id="4daa0-114">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="4daa0-115">**Get-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript och-kommandon.</span><span class="sxs-lookup"><span data-stu-id="4daa0-115">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="4daa0-116">Mer information om PowerShell-felsökaren finns i about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="4daa0-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="4daa0-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4daa0-117">EXAMPLES</span></span>

### <span data-ttu-id="4daa0-118">Exempel 1: Hämta alla Bryt punkter för alla skript och funktioner</span><span class="sxs-lookup"><span data-stu-id="4daa0-118">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="4daa0-119">Det här kommandot hämtar alla Bryt punkter som anges för alla skript och funktioner i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-119">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="4daa0-120">Exempel 2: Hämta Bryt punkter efter ID</span><span class="sxs-lookup"><span data-stu-id="4daa0-120">Example 2: Get breakpoints by ID</span></span>

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

<span data-ttu-id="4daa0-121">Det här kommandot hämtar Bryt punkten med Bryt punkts-ID 2.</span><span class="sxs-lookup"><span data-stu-id="4daa0-121">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="4daa0-122">Exempel 3: Skicka ett ID till Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-122">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="4daa0-123">Kommandona visar hur du får en Bryt punkt genom att skicka ett Bryt punkts-ID till **Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="4daa0-123">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="4daa0-124">Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för funktionen Increment i Sample.ps1 skriptet.</span><span class="sxs-lookup"><span data-stu-id="4daa0-124">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="4daa0-125">Det sparar objektet Bryt punkt i $B variabeln.</span><span class="sxs-lookup"><span data-stu-id="4daa0-125">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="4daa0-126">Det andra kommandot använder punkt operatorn (.) för att hämta egenskapen ID för objektet Bryt punkt i $B variabeln.</span><span class="sxs-lookup"><span data-stu-id="4daa0-126">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="4daa0-127">Den använder en pipeline-operator (|) för att skicka ID: t till **Get-PSBreakpoint** -cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="4daa0-127">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="4daa0-128">Resultatet blir att **Get-PSBreakpoint** hämtar Bryt punkten med angivet ID.</span><span class="sxs-lookup"><span data-stu-id="4daa0-128">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="4daa0-129">Exempel 4: Hämta Bryt punkter i angivna skriptfiler</span><span class="sxs-lookup"><span data-stu-id="4daa0-129">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="4daa0-130">Det här kommandot hämtar alla Bryt punkter i Sample.ps1 och SupportScript.ps1 filer.</span><span class="sxs-lookup"><span data-stu-id="4daa0-130">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="4daa0-131">Detta kommando hämtar inte andra Bryt punkter som kan anges i andra skript eller i-funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-131">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="4daa0-132">Exempel 5: Hämta Bryt punkter i angivna cmdlets</span><span class="sxs-lookup"><span data-stu-id="4daa0-132">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="4daa0-133">Det här kommandot hämtar alla kommando Bryt punkter som är inställda på Read-Host eller Write-Host kommandon i Sample.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-133">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="4daa0-134">Exempel 6: Hämta kommando Bryt punkter i en angiven fil</span><span class="sxs-lookup"><span data-stu-id="4daa0-134">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="4daa0-135">Det här kommandot hämtar alla kommando Bryt punkter i Sample.ps1s filen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-135">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="4daa0-136">Exempel 7: Hämta Bryt punkter per variabel</span><span class="sxs-lookup"><span data-stu-id="4daa0-136">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="4daa0-137">Detta kommando hämtar Bryt punkter som har angetts för $Index och $Swap variabler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-137">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="4daa0-138">Exempel 8: Hämta alla rad-och variabel Bryt punkter i en fil</span><span class="sxs-lookup"><span data-stu-id="4daa0-138">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="4daa0-139">Det här kommandot hämtar alla rad-och variabel Bryt punkter i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="4daa0-139">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="4daa0-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4daa0-140">PARAMETERS</span></span>

### <span data-ttu-id="4daa0-141">-Kommando</span><span class="sxs-lookup"><span data-stu-id="4daa0-141">-Command</span></span>

<span data-ttu-id="4daa0-142">Anger en matris med kommando Bryt punkter som anges för de angivna kommando namnen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-142">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="4daa0-143">Ange kommando namnen, till exempel namnet på en cmdlet eller funktion.</span><span class="sxs-lookup"><span data-stu-id="4daa0-143">Enter the command names, such as the name of a cmdlet or function.</span></span>

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

### <span data-ttu-id="4daa0-144">-ID</span><span class="sxs-lookup"><span data-stu-id="4daa0-144">-Id</span></span>

<span data-ttu-id="4daa0-145">Anger de Bryt punkts-ID: n som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="4daa0-145">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="4daa0-146">Ange ID i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="4daa0-146">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="4daa0-147">Du kan också skicka Bryt punkts-ID: n till **Get-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="4daa0-147">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="4daa0-148">– Skript</span><span class="sxs-lookup"><span data-stu-id="4daa0-148">-Script</span></span>

<span data-ttu-id="4daa0-149">Anger en matris med skript som innehåller Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="4daa0-149">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="4daa0-150">Ange sökvägen (valfritt) och namn på en eller flera skriptfiler.</span><span class="sxs-lookup"><span data-stu-id="4daa0-150">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="4daa0-151">Om du utelämnar sökvägen är standard platsen den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-151">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="4daa0-152">-Typ</span><span class="sxs-lookup"><span data-stu-id="4daa0-152">-Type</span></span>

<span data-ttu-id="4daa0-153">Anger en matris med Bryt punkts typer som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="4daa0-153">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="4daa0-154">Ange en eller flera typer.</span><span class="sxs-lookup"><span data-stu-id="4daa0-154">Enter one or more types.</span></span>
<span data-ttu-id="4daa0-155">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4daa0-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4daa0-156">Linje</span><span class="sxs-lookup"><span data-stu-id="4daa0-156">Line</span></span>
- <span data-ttu-id="4daa0-157">Kommando</span><span class="sxs-lookup"><span data-stu-id="4daa0-157">Command</span></span>
- <span data-ttu-id="4daa0-158">Variabel</span><span class="sxs-lookup"><span data-stu-id="4daa0-158">Variable</span></span>

<span data-ttu-id="4daa0-159">Du kan också komma åt Bryt punkts typer för att **få-PSBreakPoint**.</span><span class="sxs-lookup"><span data-stu-id="4daa0-159">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

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

### <span data-ttu-id="4daa0-160">– Variabel</span><span class="sxs-lookup"><span data-stu-id="4daa0-160">-Variable</span></span>

<span data-ttu-id="4daa0-161">Anger en matris med variabla Bryt punkter som anges för de angivna variabel namnen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-161">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="4daa0-162">Ange variabel namnen utan dollar tecken.</span><span class="sxs-lookup"><span data-stu-id="4daa0-162">Enter the variable names without dollar signs.</span></span>

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

### <span data-ttu-id="4daa0-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4daa0-163">CommonParameters</span></span>

<span data-ttu-id="4daa0-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4daa0-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4daa0-165">Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .</span><span class="sxs-lookup"><span data-stu-id="4daa0-165">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4daa0-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="4daa0-166">INPUTS</span></span>

### <span data-ttu-id="4daa0-167">System. Int32, Microsoft. PowerShell. commands. BreakpointType</span><span class="sxs-lookup"><span data-stu-id="4daa0-167">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="4daa0-168">Du kan skicka Bryt punkts-ID: n och Bryt punkts typer för att **få-PSBreakPoint**</span><span class="sxs-lookup"><span data-stu-id="4daa0-168">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="4daa0-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4daa0-169">OUTPUTS</span></span>

### <span data-ttu-id="4daa0-170">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="4daa0-170">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="4daa0-171">**Get-PSBreakPoint** returnerar objekt som representerar Bryt punkterna i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4daa0-171">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="4daa0-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4daa0-172">NOTES</span></span>

* <span data-ttu-id="4daa0-173">Du kan använda **Get-PSBreakpoint** eller dess alias, "GBP".</span><span class="sxs-lookup"><span data-stu-id="4daa0-173">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="4daa0-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4daa0-174">RELATED LINKS</span></span>

[<span data-ttu-id="4daa0-175">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-175">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="4daa0-176">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-176">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="4daa0-177">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="4daa0-177">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="4daa0-178">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-178">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="4daa0-179">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="4daa0-179">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

