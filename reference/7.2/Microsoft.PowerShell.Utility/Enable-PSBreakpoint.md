---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 28cda7a2fa4435092b647e43a250222a852114b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709804"
---
# <span data-ttu-id="b1fca-102">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b1fca-102">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="b1fca-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b1fca-103">SYNOPSIS</span></span>
<span data-ttu-id="b1fca-104">Aktiverar Bryt punkterna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="b1fca-104">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="b1fca-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b1fca-105">SYNTAX</span></span>

### <span data-ttu-id="b1fca-106">ID (standard)</span><span class="sxs-lookup"><span data-stu-id="b1fca-106">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="b1fca-107">Brytning</span><span class="sxs-lookup"><span data-stu-id="b1fca-107">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b1fca-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b1fca-108">DESCRIPTION</span></span>

<span data-ttu-id="b1fca-109">`Enable-PSBreakpoint`Cmdleten aktiverar inaktiverade Bryt punkter igen.</span><span class="sxs-lookup"><span data-stu-id="b1fca-109">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="b1fca-110">Du kan använda den för att aktivera alla Bryt punkter eller vissa Bryt punkter genom att tillhandahålla Bryt punkts objekt eller ID: n.</span><span class="sxs-lookup"><span data-stu-id="b1fca-110">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="b1fca-111">En Bryt punkt är en punkt i ett skript där körningen stoppas tillfälligt så att du kan granska status för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b1fca-111">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="b1fca-112">Nyligen skapade Bryt punkter aktive ras automatiskt, men kan inaktive ras med `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-112">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="b1fca-113">Den här cmdleten ändrar tekniskt värde för egenskapen **Enabled** för ett Bryt punkts objekt till **Sant**.</span><span class="sxs-lookup"><span data-stu-id="b1fca-113">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="b1fca-114">`Enable-PSBreakpoint` är en av flera cmdletar utformade för fel sökning av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="b1fca-114">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="b1fca-115">Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span><span class="sxs-lookup"><span data-stu-id="b1fca-115">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="b1fca-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b1fca-116">EXAMPLES</span></span>

### <span data-ttu-id="b1fca-117">Exempel 1: Aktivera alla Bryt punkter</span><span class="sxs-lookup"><span data-stu-id="b1fca-117">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="b1fca-118">Det här exemplet aktiverar alla Bryt punkter i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="b1fca-118">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="b1fca-119">Med hjälp av alias kan det här exemplet vara förkortat som `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-119">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="b1fca-120">Exempel 2: Aktivera Bryt punkter efter ID</span><span class="sxs-lookup"><span data-stu-id="b1fca-120">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="b1fca-121">Det här exemplet aktiverar flera Bryt punkter med deras Bryt punkts-ID.</span><span class="sxs-lookup"><span data-stu-id="b1fca-121">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="b1fca-122">Exempel 3: Aktivera en inaktive rad Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="b1fca-122">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="b1fca-123">I det här exemplet återaktiveras en Bryt punkt som har inaktiverats.</span><span class="sxs-lookup"><span data-stu-id="b1fca-123">This example re-enables a breakpoint that has been disabled.</span></span>

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

<span data-ttu-id="b1fca-124">`Set-PSBreakpoint` skapar en Bryt punkt för **Name** -variabeln i `Sample.ps1` skriptet som sparar objektet Bryt punkt i `$B` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b1fca-124">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="b1fca-125">Parametern **Passthru** visar värdet för egenskapen **Enabled** för Bryt punkten som **false**.</span><span class="sxs-lookup"><span data-stu-id="b1fca-125">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="b1fca-126">`Enable-PSBreakpoint` aktiverar Bryt punkten igen.</span><span class="sxs-lookup"><span data-stu-id="b1fca-126">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="b1fca-127">Igen, med parametern **Passthru** , ser vi att värdet för egenskapen **Enabled** är **True**.</span><span class="sxs-lookup"><span data-stu-id="b1fca-127">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="b1fca-128">Exempel 4: Aktivera Bryt punkter med en variabel</span><span class="sxs-lookup"><span data-stu-id="b1fca-128">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="b1fca-129">Det här exemplet aktiverar en uppsättning Bryt punkter med hjälp av Bryt punkts objekt.</span><span class="sxs-lookup"><span data-stu-id="b1fca-129">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="b1fca-130">`Get-PSBreakpoint` hämtar Bryt punkterna och sparar dem i `$B` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b1fca-130">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="b1fca-131">Med hjälp av **Bryt punkts** parametern kan `Enable-PSBreakpoint` du aktivera Bryt punkterna.</span><span class="sxs-lookup"><span data-stu-id="b1fca-131">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="b1fca-132">Det här exemplet motsvarar att köra `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-132">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="b1fca-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b1fca-133">PARAMETERS</span></span>

### <span data-ttu-id="b1fca-134">– Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="b1fca-134">-Breakpoint</span></span>

<span data-ttu-id="b1fca-135">Anger Bryt punkter som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="b1fca-135">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="b1fca-136">Ange en variabel som innehåller Bryt punkter eller ett kommando som hämtar Bryt punkts objekt, till exempel `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-136">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="b1fca-137">Du kan också skicka Bryt punkts objekt till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-137">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="b1fca-138">-ID</span><span class="sxs-lookup"><span data-stu-id="b1fca-138">-Id</span></span>

<span data-ttu-id="b1fca-139">Anger **ID-** numren för de Bryt punkter som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="b1fca-139">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="b1fca-140">Standardvärdet är alla Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="b1fca-140">The default value is all breakpoints.</span></span>
<span data-ttu-id="b1fca-141">Ange **ID: t** efter nummer eller i en variabel.</span><span class="sxs-lookup"><span data-stu-id="b1fca-141">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="b1fca-142">Du kan inte skicka pipe **-ID-** nummer till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-142">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="b1fca-143">Använd cmdleten för att hitta **ID: t** för en Bryt punkt `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-143">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="b1fca-144">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b1fca-144">-PassThru</span></span>

<span data-ttu-id="b1fca-145">Returnerar ett objekt som representerar den Bryt punkt som Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="b1fca-145">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="b1fca-146">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b1fca-146">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="b1fca-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b1fca-147">-Confirm</span></span>

<span data-ttu-id="b1fca-148">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b1fca-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b1fca-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b1fca-149">-WhatIf</span></span>

<span data-ttu-id="b1fca-150">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b1fca-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b1fca-151">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b1fca-151">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="b1fca-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1fca-152">CommonParameters</span></span>

<span data-ttu-id="b1fca-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1fca-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1fca-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b1fca-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1fca-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="b1fca-155">INPUTS</span></span>

### <span data-ttu-id="b1fca-156">System. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="b1fca-156">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="b1fca-157">Du kan skicka ett Bryt punkts objekt till `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b1fca-157">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="b1fca-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b1fca-158">OUTPUTS</span></span>

### <span data-ttu-id="b1fca-159">Ingen eller system. Management. Automation. Bryt punkt</span><span class="sxs-lookup"><span data-stu-id="b1fca-159">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="b1fca-160">När du använder parametern **Passthru** `Enable-PSBreakpoint` returnerar ett Bryt punkts objekt som representerar den Bryt punkten som har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="b1fca-160">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="b1fca-161">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b1fca-161">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="b1fca-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b1fca-162">NOTES</span></span>

- <span data-ttu-id="b1fca-163">`Enable-PSBreakpoint`Cmdleten genererar inget fel om du försöker aktivera en Bryt punkt som redan är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="b1fca-163">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="b1fca-164">Det innebär att du kan aktivera alla Bryt punkter utan fel, även när bara några är inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="b1fca-164">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="b1fca-165">Bryt punkter aktive ras när du skapar dem med hjälp av `Set-PSBreakpoint` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b1fca-165">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="b1fca-166">Du behöver inte aktivera nyligen skapade Bryt punkter.</span><span class="sxs-lookup"><span data-stu-id="b1fca-166">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="b1fca-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b1fca-167">RELATED LINKS</span></span>

[<span data-ttu-id="b1fca-168">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b1fca-168">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="b1fca-169">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b1fca-169">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="b1fca-170">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="b1fca-170">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="b1fca-171">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b1fca-171">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="b1fca-172">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="b1fca-172">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

