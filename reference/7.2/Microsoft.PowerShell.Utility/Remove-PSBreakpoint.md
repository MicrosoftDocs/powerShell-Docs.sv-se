---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: a56b9041c0ae70def7df619f2a4d265cb631fe7b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708378"
---
# <span data-ttu-id="2fada-102">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2fada-102">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="2fada-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2fada-103">SYNOPSIS</span></span>
<span data-ttu-id="2fada-104">Tar bort Bryt punkter från den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="2fada-104">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="2fada-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2fada-105">SYNTAX</span></span>

### <span data-ttu-id="2fada-106">Bryt punkt (standard)</span><span class="sxs-lookup"><span data-stu-id="2fada-106">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="2fada-107">Id</span><span class="sxs-lookup"><span data-stu-id="2fada-107">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="2fada-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2fada-108">DESCRIPTION</span></span>
<span data-ttu-id="2fada-109">Cmdlet: en **Remove-PSBreakpoint** tar bort en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2fada-109">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="2fada-110">Ange ett Bryt punkts objekt eller ett Bryt punkts-ID.</span><span class="sxs-lookup"><span data-stu-id="2fada-110">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="2fada-111">När du tar bort en Bryt punkt är objektet Bryt punkten inte längre tillgängligt eller fungerar inte längre.</span><span class="sxs-lookup"><span data-stu-id="2fada-111">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="2fada-112">Om du har sparat ett Bryt punkts objekt i en variabel, finns referensen fortfarande, men Bryt punkten fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="2fada-112">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="2fada-113">**Remove-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="2fada-113">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="2fada-114">Mer information om PowerShell-felsökaren finns i about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="2fada-114">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="2fada-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2fada-115">EXAMPLES</span></span>

### <span data-ttu-id="2fada-116">Exempel 1: ta bort alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="2fada-116">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="2fada-117">Det här kommandot tar bort alla Bryt punkter i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="2fada-117">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="2fada-118">Exempel 2: ta bort en angiven Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="2fada-118">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="2fada-119">Det här kommandot tar bort en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="2fada-119">This command deletes a breakpoint.</span></span>

<span data-ttu-id="2fada-120">Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för variabeln Name i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="2fada-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="2fada-121">Sedan sparas objektet Bryt punkt i variabeln $B.</span><span class="sxs-lookup"><span data-stu-id="2fada-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="2fada-122">Det andra kommandot använder cmdleten **Remove-PSBreakpoint** för att ta bort den nya Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="2fada-122">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="2fada-123">En pipeline-operator (|) används för att skicka Bryt punkts objektet i $B-variabeln till cmdleten **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="2fada-123">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="2fada-124">Om du kör skriptet körs det som ett resultat av det här kommandot utan att stoppa.</span><span class="sxs-lookup"><span data-stu-id="2fada-124">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="2fada-125">Dessutom returnerar cmdleten **Get-PSBreakpoint** inte den här Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="2fada-125">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="2fada-126">Exempel 3: ta bort en Bryt punkt per ID</span><span class="sxs-lookup"><span data-stu-id="2fada-126">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="2fada-127">Det här kommandot tar bort Bryt punkten med Bryt punkts-ID 2.</span><span class="sxs-lookup"><span data-stu-id="2fada-127">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="2fada-128">Exempel 4: Använd en funktion för att ta bort alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="2fada-128">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="2fada-129">Den här enkla funktionen tar bort alla Bryt punkter i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="2fada-129">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="2fada-130">Den använder Get-PSBreakpoint-cmdlet för att hämta Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="2fada-130">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="2fada-131">Sedan använder den en pipeline-operator (|) för att skicka Bryt punkterna till cmdleten **Remove-PSBreakpoint** , som tar bort dem.</span><span class="sxs-lookup"><span data-stu-id="2fada-131">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="2fada-132">Därför kan du skriva `del-psb` i stället för kommandot längre.</span><span class="sxs-lookup"><span data-stu-id="2fada-132">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="2fada-133">Om du vill spara funktionen lägger du till den i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="2fada-133">To save the function, add it to your PowerShell profile.</span></span>

## <span data-ttu-id="2fada-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2fada-134">PARAMETERS</span></span>

### <span data-ttu-id="2fada-135">– Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="2fada-135">-Breakpoint</span></span>
<span data-ttu-id="2fada-136">Anger de Bryt punkter som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="2fada-136">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="2fada-137">Ange en variabel som innehåller Bryt punkts objekt eller ett kommando som hämtar Bryt punkts objekt, till exempel ett **Get-PSBreakpoint** -kommando.</span><span class="sxs-lookup"><span data-stu-id="2fada-137">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="2fada-138">Du kan också skicka Bryt punkts objekt till **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="2fada-138">You can also pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="2fada-139">-ID</span><span class="sxs-lookup"><span data-stu-id="2fada-139">-Id</span></span>
<span data-ttu-id="2fada-140">Anger Bryt punkts-ID: n för vilka denna cmdlet tar bort Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="2fada-140">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

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

### <span data-ttu-id="2fada-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2fada-141">-Confirm</span></span>
<span data-ttu-id="2fada-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2fada-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2fada-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2fada-143">-WhatIf</span></span>
<span data-ttu-id="2fada-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2fada-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2fada-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2fada-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2fada-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2fada-146">CommonParameters</span></span>
<span data-ttu-id="2fada-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2fada-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2fada-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2fada-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2fada-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="2fada-149">INPUTS</span></span>

### <span data-ttu-id="2fada-150">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="2fada-150">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="2fada-151">Du kan skicka Bryt punkts objekt till **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="2fada-151">You can pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

## <span data-ttu-id="2fada-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2fada-152">OUTPUTS</span></span>

### <span data-ttu-id="2fada-153">Inga</span><span class="sxs-lookup"><span data-stu-id="2fada-153">None</span></span>
<span data-ttu-id="2fada-154">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2fada-154">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2fada-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2fada-155">NOTES</span></span>

## <span data-ttu-id="2fada-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2fada-156">RELATED LINKS</span></span>

[<span data-ttu-id="2fada-157">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2fada-157">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="2fada-158">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2fada-158">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="2fada-159">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2fada-159">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="2fada-160">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="2fada-160">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="2fada-161">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2fada-161">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

