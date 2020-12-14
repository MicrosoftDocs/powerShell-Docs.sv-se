---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2bd1a48d2075950cdb337063a100bf31534ac6fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709805"
---
# <span data-ttu-id="95887-102">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="95887-102">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="95887-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="95887-103">SYNOPSIS</span></span>
<span data-ttu-id="95887-104">Inaktiverar Bryt punkterna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="95887-104">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="95887-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95887-105">SYNTAX</span></span>

### <span data-ttu-id="95887-106">Bryt punkt (standard)</span><span class="sxs-lookup"><span data-stu-id="95887-106">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="95887-107">Id</span><span class="sxs-lookup"><span data-stu-id="95887-107">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="95887-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="95887-108">DESCRIPTION</span></span>

<span data-ttu-id="95887-109">Cmdlet: en **disable-PSBreakpoint** inaktiverar Bryt punkter, vilket säkerställer att de inte är identiska när skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="95887-109">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="95887-110">Du kan använda den för att inaktivera alla Bryt punkter, eller så kan du ange Bryt punkter genom att skicka Bryt punkts objekt eller Bryt punkts-ID: n.</span><span class="sxs-lookup"><span data-stu-id="95887-110">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="95887-111">Den här cmdleten ändrar tekniskt värdet för egenskapen Enabled för ett Bryt punkts objekt till falskt.</span><span class="sxs-lookup"><span data-stu-id="95887-111">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="95887-112">Använd Enable-PSBreakpoint-cmdleten om du vill återaktivera en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="95887-112">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="95887-113">Bryt punkter aktive ras som standard när du skapar dem med hjälp av Set-PSBreakpoint-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="95887-113">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="95887-114">En Bryt punkt är en punkt i ett skript där körningen stoppas tillfälligt så att du kan granska instruktionerna i skriptet.</span><span class="sxs-lookup"><span data-stu-id="95887-114">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="95887-115">**Disable-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="95887-115">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="95887-116">Mer information om PowerShell-felsökaren finns i about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="95887-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="95887-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="95887-117">EXAMPLES</span></span>

### <span data-ttu-id="95887-118">Exempel 1: Ange en Bryt punkt och inaktivera den</span><span class="sxs-lookup"><span data-stu-id="95887-118">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="95887-119">Dessa kommandon inaktiverar en nyligen skapad Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="95887-119">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="95887-120">Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för variabeln *Name* i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="95887-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="95887-121">Sedan sparas objektet Bryt punkt i variabeln $B.</span><span class="sxs-lookup"><span data-stu-id="95887-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="95887-122">Det andra kommandot använder cmdleten **disable-PSBreakpoint** för att inaktivera den nya Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="95887-122">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="95887-123">En pipeline-operator (|) används för att skicka Bryt punkts objektet i $B till cmdleten **disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="95887-123">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="95887-124">Resultatet av det här kommandot är att värdet för egenskapen Enabled för objektet Bryt punkt i $B är falskt.</span><span class="sxs-lookup"><span data-stu-id="95887-124">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="95887-125">Exempel 2: inaktivera en Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="95887-125">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="95887-126">Detta kommando inaktiverar Bryt punkten med Bryt punkts-ID 0.</span><span class="sxs-lookup"><span data-stu-id="95887-126">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="95887-127">Exempel 3: skapa en inaktive rad Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="95887-127">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="95887-128">Det här kommandot skapar en ny Bryt punkt som är inaktive rad tills du aktiverar den.</span><span class="sxs-lookup"><span data-stu-id="95887-128">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="95887-129">Den använder cmdleten **disable-PSBreakpoint** för att inaktivera Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="95887-129">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="95887-130">Värdet för parametern *Bryt punkt* är ett Set-PSBreakpoint-kommando som anger en ny Bryt punkt, genererar ett Bryt punkts objekt och sparar objektet i $B-variabeln.</span><span class="sxs-lookup"><span data-stu-id="95887-130">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="95887-131">Cmdlet-parametrar som tar objekt som värden kan acceptera en variabel som innehåller objektet eller ett kommando som hämtar eller genererar objektet.</span><span class="sxs-lookup"><span data-stu-id="95887-131">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="95887-132">I det här fallet, eftersom **set-PSBreakpoint** genererar ett Bryt punkts objekt, kan det användas som värde för *Bryt punkts* parametern.</span><span class="sxs-lookup"><span data-stu-id="95887-132">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="95887-133">Det andra kommandot visar objektet Bryt punkt i värdet för variabeln $B.</span><span class="sxs-lookup"><span data-stu-id="95887-133">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="95887-134">Exempel 4: inaktivera alla Bryt punkter i den aktuella konsolen</span><span class="sxs-lookup"><span data-stu-id="95887-134">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="95887-135">Detta kommando inaktiverar alla Bryt punkter i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="95887-135">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="95887-136">Du kan förkorta det här kommandot som: "GBP | dbp".</span><span class="sxs-lookup"><span data-stu-id="95887-136">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="95887-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="95887-137">PARAMETERS</span></span>

### <span data-ttu-id="95887-138">– Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="95887-138">-Breakpoint</span></span>

<span data-ttu-id="95887-139">Anger Bryt punkterna som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="95887-139">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="95887-140">Ange en variabel som innehåller Bryt punkts objekt eller ett kommando som hämtar Bryt punkts objekt, till exempel ett Get-PSBreakpoint-kommando.</span><span class="sxs-lookup"><span data-stu-id="95887-140">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="95887-141">Du kan också skicka Bryt punkts objekt till cmdlet: en **disable-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="95887-141">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="95887-142">-ID</span><span class="sxs-lookup"><span data-stu-id="95887-142">-Id</span></span>

<span data-ttu-id="95887-143">Inaktiverar Bryt punkterna med de angivna Bryt punkts-ID: na.</span><span class="sxs-lookup"><span data-stu-id="95887-143">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="95887-144">Ange de ID: n eller en variabel som innehåller ID: n.</span><span class="sxs-lookup"><span data-stu-id="95887-144">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="95887-145">Du kan inte skicka pipe-ID: n för att **inaktivera-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="95887-145">You cannot pipe IDs to **Disable-PSBreakpoint**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="95887-146">– PassThru</span><span class="sxs-lookup"><span data-stu-id="95887-146">-PassThru</span></span>

<span data-ttu-id="95887-147">Returnerar ett objekt som representerar de aktiverade Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="95887-147">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="95887-148">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="95887-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="95887-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="95887-149">-Confirm</span></span>

<span data-ttu-id="95887-150">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="95887-150">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95887-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="95887-151">-WhatIf</span></span>

<span data-ttu-id="95887-152">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="95887-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="95887-153">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="95887-153">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95887-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95887-154">CommonParameters</span></span>

<span data-ttu-id="95887-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="95887-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95887-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="95887-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95887-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="95887-157">INPUTS</span></span>

### <span data-ttu-id="95887-158">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="95887-158">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="95887-159">Du kan skicka ett Bryt punkts objekt till **disable-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="95887-159">You can pipe a breakpoint object to **Disable-PSBreakpoint**.</span></span>

## <span data-ttu-id="95887-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="95887-160">OUTPUTS</span></span>

### <span data-ttu-id="95887-161">Ingen eller system. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="95887-161">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="95887-162">När du använder parametern *Passthru* returnerar **disable-PSBreakpoint** ett objekt som representerar den inaktiverade Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="95887-162">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="95887-163">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="95887-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="95887-164">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="95887-164">NOTES</span></span>

## <span data-ttu-id="95887-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="95887-165">RELATED LINKS</span></span>

[<span data-ttu-id="95887-166">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="95887-166">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="95887-167">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="95887-167">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="95887-168">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="95887-168">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="95887-169">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="95887-169">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="95887-170">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="95887-170">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

