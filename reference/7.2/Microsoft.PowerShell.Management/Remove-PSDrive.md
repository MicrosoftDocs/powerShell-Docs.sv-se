---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: d20a348f3f5ba193eb85e0f9d0e2cc11ad083b47
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709972"
---
# <span data-ttu-id="0baa7-102">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0baa7-102">Remove-PSDrive</span></span>

## <span data-ttu-id="0baa7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0baa7-103">SYNOPSIS</span></span>
<span data-ttu-id="0baa7-104">Tar bort tillfälliga PowerShell-enheter och kopplar från mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="0baa7-104">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="0baa7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0baa7-105">SYNTAX</span></span>

### <span data-ttu-id="0baa7-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="0baa7-106">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0baa7-107">LiteralName</span><span class="sxs-lookup"><span data-stu-id="0baa7-107">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0baa7-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0baa7-108">DESCRIPTION</span></span>

<span data-ttu-id="0baa7-109">`Remove-PSDrive`Cmdleten tar bort temporära PowerShell-enheter som har skapats med hjälp av `New-PSDrive` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-109">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="0baa7-110">Från och med Windows PowerShell 3,0 `Remove-PSDrive` kopplar även mappade nätverks enheter, inklusive, men inte begränsat till, enheter som skapats med hjälp av `Persist` parametern för `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="0baa7-110">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="0baa7-111">`Remove-PSDrive` Det går inte att ta bort fysiska eller logiska enheter i Windows.</span><span class="sxs-lookup"><span data-stu-id="0baa7-111">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="0baa7-112">Från och med Windows PowerShell 3,0 lägger PowerShell automatiskt till en PSDrive i fil systemet som representerar den nya enheten när en extern enhet ansluts till datorn.</span><span class="sxs-lookup"><span data-stu-id="0baa7-112">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="0baa7-113">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0baa7-113">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="0baa7-114">När en extern enhet kopplas bort från datorn tar PowerShell automatiskt bort den PSDrive som representerar den borttagna enheten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-114">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="0baa7-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0baa7-115">EXAMPLES</span></span>

### <span data-ttu-id="0baa7-116">Exempel 1: ta bort en fil system enhet</span><span class="sxs-lookup"><span data-stu-id="0baa7-116">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="0baa7-117">Det här kommandot tar bort en temporär fil system enhet med namnet "SMP".</span><span class="sxs-lookup"><span data-stu-id="0baa7-117">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="0baa7-118">Exempel 2: ta bort mappade nätverks enheter</span><span class="sxs-lookup"><span data-stu-id="0baa7-118">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="0baa7-119">Det här kommandot använder `Remove-PSDrive` för att koppla från X: och S: mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="0baa7-119">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="0baa7-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0baa7-120">PARAMETERS</span></span>

### <span data-ttu-id="0baa7-121">-Force</span><span class="sxs-lookup"><span data-stu-id="0baa7-121">-Force</span></span>

<span data-ttu-id="0baa7-122">Tar bort den aktuella PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-122">Removes the current PowerShell drive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0baa7-123">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="0baa7-123">-LiteralName</span></span>

<span data-ttu-id="0baa7-124">Anger namnet på enheten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-124">Specifies the name of the drive.</span></span>

<span data-ttu-id="0baa7-125">Värdet för **LiteralName** används precis som skrivet.</span><span class="sxs-lookup"><span data-stu-id="0baa7-125">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="0baa7-126">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0baa7-126">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="0baa7-127">Om namnet innehåller escape-tecken omger du det med enkla citat tecken (').</span><span class="sxs-lookup"><span data-stu-id="0baa7-127">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="0baa7-128">Enkla citat tecken instruerar PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="0baa7-128">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0baa7-129">-Name</span><span class="sxs-lookup"><span data-stu-id="0baa7-129">-Name</span></span>

<span data-ttu-id="0baa7-130">Anger namnen på de enheter som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="0baa7-130">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="0baa7-131">Skriv inget kolon (:) efter enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="0baa7-131">Do not type a colon (:) after the drive name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="0baa7-132">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="0baa7-132">-PSProvider</span></span>

<span data-ttu-id="0baa7-133">Anger en matris med **PSProvider** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0baa7-133">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="0baa7-134">Den här cmdleten tar bort och kopplar från alla enheter som är associerade med den angivna PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="0baa7-134">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0baa7-135">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="0baa7-135">-Scope</span></span>

<span data-ttu-id="0baa7-136">Anger ett omfång för enheten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-136">Specifies a scope for the drive.</span></span>
<span data-ttu-id="0baa7-137">De acceptabla värdena för den här parametern är: globalt, lokalt och skript, eller ett tal i förhållande till det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="0baa7-137">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="0baa7-138">Omfattnings nummer 0 till och med antalet omfattningar.</span><span class="sxs-lookup"><span data-stu-id="0baa7-138">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="0baa7-139">Det aktuella omfångs numret är 0 och dess överordnade är 1.</span><span class="sxs-lookup"><span data-stu-id="0baa7-139">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="0baa7-140">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="0baa7-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0baa7-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0baa7-141">-Confirm</span></span>

<span data-ttu-id="0baa7-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0baa7-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0baa7-143">-WhatIf</span></span>

<span data-ttu-id="0baa7-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="0baa7-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0baa7-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0baa7-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0baa7-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0baa7-146">CommonParameters</span></span>

<span data-ttu-id="0baa7-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0baa7-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0baa7-148">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="0baa7-148">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="0baa7-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="0baa7-149">INPUTS</span></span>

### <span data-ttu-id="0baa7-150">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="0baa7-150">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="0baa7-151">Du kan skicka vidare ett enhets objekt, till exempel ett från `Get-PSDrive` cmdlet: en, till `Remove-PSDrive` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="0baa7-151">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="0baa7-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0baa7-152">OUTPUTS</span></span>

### <span data-ttu-id="0baa7-153">Inga</span><span class="sxs-lookup"><span data-stu-id="0baa7-153">None</span></span>

<span data-ttu-id="0baa7-154">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0baa7-154">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="0baa7-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0baa7-155">NOTES</span></span>

- <span data-ttu-id="0baa7-156">`Remove-PSDrive`Cmdleten är utformad för att fungera med data som exponeras av en PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="0baa7-156">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="0baa7-157">Om du vill visa en lista över providers i sessionen använder du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0baa7-157">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="0baa7-158">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="0baa7-158">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="0baa7-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0baa7-159">RELATED LINKS</span></span>

[<span data-ttu-id="0baa7-160">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0baa7-160">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="0baa7-161">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="0baa7-161">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="0baa7-162">about_Providers</span><span class="sxs-lookup"><span data-stu-id="0baa7-162">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

