---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264890"
---
# <span data-ttu-id="ce91f-103">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ce91f-103">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="ce91f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ce91f-104">SYNOPSIS</span></span>
<span data-ttu-id="ce91f-105">Tar bort Bryt punkter från den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="ce91f-105">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="ce91f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ce91f-106">SYNTAX</span></span>

### <span data-ttu-id="ce91f-107">Bryt punkt (standard)</span><span class="sxs-lookup"><span data-stu-id="ce91f-107">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ce91f-108">Id</span><span class="sxs-lookup"><span data-stu-id="ce91f-108">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ce91f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ce91f-109">DESCRIPTION</span></span>
<span data-ttu-id="ce91f-110">Cmdlet: en **Remove-PSBreakpoint** tar bort en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="ce91f-110">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="ce91f-111">Ange ett Bryt punkts objekt eller ett Bryt punkts-ID.</span><span class="sxs-lookup"><span data-stu-id="ce91f-111">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="ce91f-112">När du tar bort en Bryt punkt är objektet Bryt punkten inte längre tillgängligt eller fungerar inte längre.</span><span class="sxs-lookup"><span data-stu-id="ce91f-112">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="ce91f-113">Om du har sparat ett Bryt punkts objekt i en variabel, finns referensen fortfarande, men Bryt punkten fungerar inte.</span><span class="sxs-lookup"><span data-stu-id="ce91f-113">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="ce91f-114">**Remove-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av Windows PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="ce91f-114">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts.</span></span>
<span data-ttu-id="ce91f-115">Mer information om Windows PowerShell-felsökaren finns about_Debuggers.</span><span class="sxs-lookup"><span data-stu-id="ce91f-115">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="ce91f-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ce91f-116">EXAMPLES</span></span>

### <span data-ttu-id="ce91f-117">Exempel 1: ta bort alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="ce91f-117">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="ce91f-118">Det här kommandot tar bort alla Bryt punkter i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="ce91f-118">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="ce91f-119">Exempel 2: ta bort en angiven Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="ce91f-119">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="ce91f-120">Det här kommandot tar bort en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="ce91f-120">This command deletes a breakpoint.</span></span>

<span data-ttu-id="ce91f-121">Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för variabeln Name i Sample.ps1-skriptet.</span><span class="sxs-lookup"><span data-stu-id="ce91f-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="ce91f-122">Sedan sparas objektet Bryt punkt i variabeln $B.</span><span class="sxs-lookup"><span data-stu-id="ce91f-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="ce91f-123">Det andra kommandot använder cmdleten **Remove-PSBreakpoint** för att ta bort den nya Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="ce91f-123">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="ce91f-124">En pipeline-operator (|) används för att skicka Bryt punkts objektet i $B-variabeln till cmdleten **Remove-PSBreakpoint** .</span><span class="sxs-lookup"><span data-stu-id="ce91f-124">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="ce91f-125">Om du kör skriptet körs det som ett resultat av det här kommandot utan att stoppa.</span><span class="sxs-lookup"><span data-stu-id="ce91f-125">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="ce91f-126">Dessutom returnerar cmdleten **Get-PSBreakpoint** inte den här Bryt punkten.</span><span class="sxs-lookup"><span data-stu-id="ce91f-126">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="ce91f-127">Exempel 3: ta bort en Bryt punkt per ID</span><span class="sxs-lookup"><span data-stu-id="ce91f-127">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="ce91f-128">Det här kommandot tar bort Bryt punkten med Bryt punkts-ID 2.</span><span class="sxs-lookup"><span data-stu-id="ce91f-128">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="ce91f-129">Exempel 4: Använd en funktion för att ta bort alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="ce91f-129">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="ce91f-130">Den här enkla funktionen tar bort alla Bryt punkter i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="ce91f-130">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="ce91f-131">Den använder Get-PSBreakpoint-cmdlet för att hämta Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="ce91f-131">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="ce91f-132">Sedan använder den en pipeline-operator (|) för att skicka Bryt punkterna till cmdleten **Remove-PSBreakpoint** , som tar bort dem.</span><span class="sxs-lookup"><span data-stu-id="ce91f-132">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="ce91f-133">Därför kan du skriva `del-psb` i stället för kommandot längre.</span><span class="sxs-lookup"><span data-stu-id="ce91f-133">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="ce91f-134">Om du vill spara funktionen lägger du till den i din Windows PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="ce91f-134">To save the function, add it to your Windows PowerShell profile.</span></span>

## <span data-ttu-id="ce91f-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ce91f-135">PARAMETERS</span></span>

### <span data-ttu-id="ce91f-136">– Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="ce91f-136">-Breakpoint</span></span>
<span data-ttu-id="ce91f-137">Anger de Bryt punkter som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="ce91f-137">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="ce91f-138">Ange en variabel som innehåller Bryt punkts objekt eller ett kommando som hämtar Bryt punkts objekt, till exempel ett **Get-PSBreakpoint** -kommando.</span><span class="sxs-lookup"><span data-stu-id="ce91f-138">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="ce91f-139">Du kan också skicka Bryt punkts objekt till **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="ce91f-139">You can also pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="ce91f-140">-ID</span><span class="sxs-lookup"><span data-stu-id="ce91f-140">-Id</span></span>
<span data-ttu-id="ce91f-141">Anger Bryt punkts-ID: n för vilka denna cmdlet tar bort Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="ce91f-141">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

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

### <span data-ttu-id="ce91f-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ce91f-142">-Confirm</span></span>
<span data-ttu-id="ce91f-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ce91f-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ce91f-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ce91f-144">-WhatIf</span></span>
<span data-ttu-id="ce91f-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ce91f-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ce91f-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ce91f-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ce91f-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce91f-147">CommonParameters</span></span>
<span data-ttu-id="ce91f-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce91f-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce91f-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ce91f-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ce91f-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="ce91f-150">INPUTS</span></span>

### <span data-ttu-id="ce91f-151">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="ce91f-151">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="ce91f-152">Du kan skicka Bryt punkts objekt till **Remove-PSBreakpoint**.</span><span class="sxs-lookup"><span data-stu-id="ce91f-152">You can pipe breakpoint objects to **Remove-PSBreakpoint**.</span></span>

## <span data-ttu-id="ce91f-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ce91f-153">OUTPUTS</span></span>

### <span data-ttu-id="ce91f-154">Inget</span><span class="sxs-lookup"><span data-stu-id="ce91f-154">None</span></span>
<span data-ttu-id="ce91f-155">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ce91f-155">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ce91f-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ce91f-156">NOTES</span></span>

## <span data-ttu-id="ce91f-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ce91f-157">RELATED LINKS</span></span>

[<span data-ttu-id="ce91f-158">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ce91f-158">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="ce91f-159">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ce91f-159">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="ce91f-160">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ce91f-160">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="ce91f-161">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="ce91f-161">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="ce91f-162">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="ce91f-162">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
