---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 547739d6482e86bc558245bc5c5f04eddcfe9614
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266445"
---
# <span data-ttu-id="323ac-103">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="323ac-103">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="323ac-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="323ac-104">SYNOPSIS</span></span>
<span data-ttu-id="323ac-105">Aktiverar Bryt punkterna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="323ac-105">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="323ac-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="323ac-106">SYNTAX</span></span>

### <span data-ttu-id="323ac-107">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="323ac-107">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="323ac-108">Brytning</span><span class="sxs-lookup"><span data-stu-id="323ac-108">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="323ac-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="323ac-109">DESCRIPTION</span></span>

<span data-ttu-id="323ac-110">`Enable-PSBreakpoint`Cmdleten aktiverar inaktiverade Bryt punkter igen.</span><span class="sxs-lookup"><span data-stu-id="323ac-110">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="323ac-111">Du kan använda den för att aktivera alla Bryt punkter eller vissa Bryt punkter genom att tillhandahålla Bryt punkts objekt eller ID: n.</span><span class="sxs-lookup"><span data-stu-id="323ac-111">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="323ac-112">En Bryt punkt är en punkt i ett skript där körningen stoppas tillfälligt så att du kan granska status för skriptet.</span><span class="sxs-lookup"><span data-stu-id="323ac-112">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="323ac-113">Nyligen skapade Bryt punkter aktive ras automatiskt, men kan inaktive ras med `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-113">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="323ac-114">Den här cmdleten ändrar tekniskt värde för egenskapen **Enabled** för ett Bryt punkts objekt till **Sant**.</span><span class="sxs-lookup"><span data-stu-id="323ac-114">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="323ac-115">`Enable-PSBreakpoint` är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="323ac-115">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="323ac-116">Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="323ac-116">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="323ac-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="323ac-117">EXAMPLES</span></span>

### <span data-ttu-id="323ac-118">Exempel 1: Aktivera alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="323ac-118">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="323ac-119">Det här exemplet aktiverar alla Bryt punkter i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="323ac-119">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="323ac-120">Med hjälp av alias kan det här exemplet vara förkortat som `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="323ac-120">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="323ac-121">Exempel 2: Aktivera Bryt punkter efter ID</span><span class="sxs-lookup"><span data-stu-id="323ac-121">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="323ac-122">Det här exemplet aktiverar flera Bryt punkter med deras Bryt punkts-ID.</span><span class="sxs-lookup"><span data-stu-id="323ac-122">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="323ac-123">Exempel 3: Aktivera en inaktive rad Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="323ac-123">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="323ac-124">I det här exemplet återaktiveras en Bryt punkt som har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="323ac-124">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="323ac-125">`Set-PSBreakpoint` skapar en Bryt punkt för **Name** -variabeln i `Sample.ps1` skriptet som sparar objektet Bryt punkt i `$B` variabeln.</span><span class="sxs-lookup"><span data-stu-id="323ac-125">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="323ac-126">Parametern **Passthru** visar värdet för egenskapen **Enabled** för Bryt punkten som **false**.</span><span class="sxs-lookup"><span data-stu-id="323ac-126">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="323ac-127">`Enable-PSBreakpoint` aktiverar Bryt punkten igen.</span><span class="sxs-lookup"><span data-stu-id="323ac-127">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="323ac-128">Igen, med parametern **Passthru** , ser vi att värdet för egenskapen **Enabled** är **True**.</span><span class="sxs-lookup"><span data-stu-id="323ac-128">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="323ac-129">Exempel 4: Aktivera Bryt punkter med en variabel</span><span class="sxs-lookup"><span data-stu-id="323ac-129">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="323ac-130">Det här exemplet aktiverar en uppsättning Bryt punkter med hjälp av Bryt punkts objekt.</span><span class="sxs-lookup"><span data-stu-id="323ac-130">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="323ac-131">`Get-PSBreakpoint` hämtar Bryt punkterna och sparar dem i `$B` variabeln.</span><span class="sxs-lookup"><span data-stu-id="323ac-131">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="323ac-132">Med hjälp av **Bryt punkts** parametern kan `Enable-PSBreakpoint` du aktivera Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="323ac-132">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="323ac-133">Det här exemplet motsvarar att köra `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="323ac-133">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="323ac-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="323ac-134">PARAMETERS</span></span>

### <span data-ttu-id="323ac-135">– Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="323ac-135">-Breakpoint</span></span>

<span data-ttu-id="323ac-136">Anger Bryt punkter som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="323ac-136">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="323ac-137">Ange en variabel som innehåller Bryt punkter eller ett kommando som hämtar Bryt punkts objekt, till exempel `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-137">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="323ac-138">Du kan också skicka Bryt punkts objekt till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-138">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="323ac-139">-ID</span><span class="sxs-lookup"><span data-stu-id="323ac-139">-Id</span></span>

<span data-ttu-id="323ac-140">Anger **ID-** numren för de Bryt punkter som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="323ac-140">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="323ac-141">Standardvärdet är alla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="323ac-141">The default value is all breakpoints.</span></span>
<span data-ttu-id="323ac-142">Ange **ID: t** efter nummer eller i en variabel.</span><span class="sxs-lookup"><span data-stu-id="323ac-142">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="323ac-143">Du kan inte skicka pipe **-ID-** nummer till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-143">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="323ac-144">Använd cmdleten för att hitta **ID: t** för en Bryt punkt `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-144">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="323ac-145">– PassThru</span><span class="sxs-lookup"><span data-stu-id="323ac-145">-PassThru</span></span>

<span data-ttu-id="323ac-146">Returnerar ett objekt som representerar den Bryt punkt som Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="323ac-146">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="323ac-147">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="323ac-147">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="323ac-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="323ac-148">-Confirm</span></span>

<span data-ttu-id="323ac-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="323ac-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="323ac-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="323ac-150">-WhatIf</span></span>

<span data-ttu-id="323ac-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="323ac-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="323ac-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="323ac-152">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="323ac-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="323ac-153">CommonParameters</span></span>

<span data-ttu-id="323ac-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="323ac-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="323ac-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="323ac-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="323ac-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="323ac-156">INPUTS</span></span>

### <span data-ttu-id="323ac-157">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="323ac-157">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="323ac-158">Du kan skicka ett Bryt punkts objekt till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="323ac-158">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="323ac-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="323ac-159">OUTPUTS</span></span>

### <span data-ttu-id="323ac-160">Ingen eller system. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="323ac-160">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="323ac-161">När du använder parametern **Passthru** `Enable-PSBreakpoint` returnerar ett Bryt punkts objekt som representerar den Bryt punkten som har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="323ac-161">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="323ac-162">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="323ac-162">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="323ac-163">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="323ac-163">NOTES</span></span>

- <span data-ttu-id="323ac-164">`Enable-PSBreakpoint`Cmdleten genererar inget fel om du försöker aktivera en Bryt punkt som redan är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="323ac-164">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="323ac-165">Det innebär att du kan aktivera alla Bryt punkter utan fel, även när bara några är inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="323ac-165">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="323ac-166">Bryt punkter aktive ras när du skapar dem med hjälp av `Set-PSBreakpoint` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="323ac-166">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="323ac-167">Du behöver inte aktivera nyligen skapade Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="323ac-167">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="323ac-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="323ac-168">RELATED LINKS</span></span>

[<span data-ttu-id="323ac-169">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="323ac-169">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="323ac-170">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="323ac-170">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="323ac-171">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="323ac-171">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="323ac-172">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="323ac-172">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="323ac-173">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="323ac-173">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

