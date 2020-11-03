---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 9c1edd90757017c679516553d376d4cd4e552875
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263258"
---
# <span data-ttu-id="dabe0-103">Remove-PSDrive</span><span class="sxs-lookup"><span data-stu-id="dabe0-103">Remove-PSDrive</span></span>

## <span data-ttu-id="dabe0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dabe0-104">SYNOPSIS</span></span>
<span data-ttu-id="dabe0-105">Tar bort tillfälliga PowerShell-enheter och kopplar från mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="dabe0-105">Deletes temporary PowerShell drives and disconnects mapped network drives.</span></span>

## <span data-ttu-id="dabe0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dabe0-106">SYNTAX</span></span>

### <span data-ttu-id="dabe0-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="dabe0-107">Name (Default)</span></span>

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dabe0-108">LiteralName</span><span class="sxs-lookup"><span data-stu-id="dabe0-108">LiteralName</span></span>

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dabe0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dabe0-109">DESCRIPTION</span></span>

<span data-ttu-id="dabe0-110">`Remove-PSDrive`Cmdleten tar bort temporära PowerShell-enheter som har skapats med hjälp av `New-PSDrive` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-110">The `Remove-PSDrive` cmdlet deletes temporary PowerShell drives that were created by using the `New-PSDrive` cmdlet.</span></span>

<span data-ttu-id="dabe0-111">Från och med Windows PowerShell 3,0 `Remove-PSDrive` kopplar även mappade nätverks enheter, inklusive, men inte begränsat till, enheter som skapats med hjälp av `Persist` parametern för `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="dabe0-111">Beginning in Windows PowerShell 3.0, `Remove-PSDrive` also disconnects mapped network drives, including, but not limited to, drives created by using the `Persist` parameter of `New-PSDrive`.</span></span>

<span data-ttu-id="dabe0-112">`Remove-PSDrive` Det går inte att ta bort fysiska eller logiska enheter i Windows.</span><span class="sxs-lookup"><span data-stu-id="dabe0-112">`Remove-PSDrive` cannot delete Windows physical or logical drives.</span></span>

<span data-ttu-id="dabe0-113">Från och med Windows PowerShell 3,0 lägger PowerShell automatiskt till en PSDrive i fil systemet som representerar den nya enheten när en extern enhet ansluts till datorn.</span><span class="sxs-lookup"><span data-stu-id="dabe0-113">Beginning in Windows PowerShell 3.0, when an external drive is connected to the computer, PowerShell automatically adds a PSDrive to the file system that represents the new drive.</span></span>
<span data-ttu-id="dabe0-114">Du behöver inte starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dabe0-114">You do not need to restart PowerShell.</span></span>
<span data-ttu-id="dabe0-115">När en extern enhet kopplas bort från datorn tar PowerShell automatiskt bort den PSDrive som representerar den borttagna enheten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-115">Similarly, when an external drive is disconnected from the computer, PowerShell automatically deletes the PSDrive that represents the removed drive.</span></span>

## <span data-ttu-id="dabe0-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dabe0-116">EXAMPLES</span></span>

### <span data-ttu-id="dabe0-117">Exempel 1: ta bort en fil system enhet</span><span class="sxs-lookup"><span data-stu-id="dabe0-117">Example 1: Remove a file system drive</span></span>

<span data-ttu-id="dabe0-118">Det här kommandot tar bort en temporär fil system enhet med namnet "SMP".</span><span class="sxs-lookup"><span data-stu-id="dabe0-118">This command removes a temporary file system drive named "smp".</span></span>

```powershell
Remove-PSDrive -Name smp
```

### <span data-ttu-id="dabe0-119">Exempel 2: ta bort mappade nätverks enheter</span><span class="sxs-lookup"><span data-stu-id="dabe0-119">Example 2: Remove mapped network drives</span></span>

<span data-ttu-id="dabe0-120">Det här kommandot använder `Remove-PSDrive` för att koppla från X: och S: mappade nätverks enheter.</span><span class="sxs-lookup"><span data-stu-id="dabe0-120">This command uses `Remove-PSDrive` to disconnect the X: and S: mapped network drives.</span></span>

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## <span data-ttu-id="dabe0-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dabe0-121">PARAMETERS</span></span>

### <span data-ttu-id="dabe0-122">-Force</span><span class="sxs-lookup"><span data-stu-id="dabe0-122">-Force</span></span>

<span data-ttu-id="dabe0-123">Tar bort den aktuella PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-123">Removes the current PowerShell drive.</span></span>

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

### <span data-ttu-id="dabe0-124">-LiteralName</span><span class="sxs-lookup"><span data-stu-id="dabe0-124">-LiteralName</span></span>

<span data-ttu-id="dabe0-125">Anger namnet på enheten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-125">Specifies the name of the drive.</span></span>

<span data-ttu-id="dabe0-126">Värdet för **LiteralName** används precis som skrivet.</span><span class="sxs-lookup"><span data-stu-id="dabe0-126">The value of **LiteralName** is used exactly as typed.</span></span>
<span data-ttu-id="dabe0-127">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="dabe0-127">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="dabe0-128">Om namnet innehåller escape-tecken omger du det med enkla citat tecken (').</span><span class="sxs-lookup"><span data-stu-id="dabe0-128">If the name includes escape characters, enclose it in single quotation marks (').</span></span>
<span data-ttu-id="dabe0-129">Enkla citat tecken instruerar PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="dabe0-129">Single quotation marks instruct PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="dabe0-130">-Name</span><span class="sxs-lookup"><span data-stu-id="dabe0-130">-Name</span></span>

<span data-ttu-id="dabe0-131">Anger namnen på de enheter som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="dabe0-131">Specifies the names of the drives to remove.</span></span>
<span data-ttu-id="dabe0-132">Skriv inget kolon (:) efter enhets namnet.</span><span class="sxs-lookup"><span data-stu-id="dabe0-132">Do not type a colon (:) after the drive name.</span></span>

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

### <span data-ttu-id="dabe0-133">-PSProvider</span><span class="sxs-lookup"><span data-stu-id="dabe0-133">-PSProvider</span></span>

<span data-ttu-id="dabe0-134">Anger en matris med **PSProvider** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dabe0-134">Specifies an array of **PSProvider** objects.</span></span>
<span data-ttu-id="dabe0-135">Den här cmdleten tar bort och kopplar från alla enheter som är associerade med den angivna PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="dabe0-135">This cmdlet removes and disconnects all of the drives associated with the specified PowerShell provider.</span></span>

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

### <span data-ttu-id="dabe0-136">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="dabe0-136">-Scope</span></span>

<span data-ttu-id="dabe0-137">Anger ett omfång för enheten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-137">Specifies a scope for the drive.</span></span>
<span data-ttu-id="dabe0-138">De acceptabla värdena för den här parametern är: globalt, lokalt och skript, eller ett tal i förhållande till det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="dabe0-138">The acceptable values for this parameter are: Global, Local, and Script, or a number relative to the current scope.</span></span> <span data-ttu-id="dabe0-139">Omfattnings nummer 0 till och med antalet omfattningar.</span><span class="sxs-lookup"><span data-stu-id="dabe0-139">Scopes number 0 through the number of scopes.</span></span> <span data-ttu-id="dabe0-140">Det aktuella omfångs numret är 0 och dess överordnade är 1.</span><span class="sxs-lookup"><span data-stu-id="dabe0-140">The current scope number is 0 and its parent is 1.</span></span>
<span data-ttu-id="dabe0-141">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="dabe0-141">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="dabe0-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dabe0-142">-Confirm</span></span>

<span data-ttu-id="dabe0-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dabe0-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dabe0-144">-WhatIf</span></span>

<span data-ttu-id="dabe0-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="dabe0-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="dabe0-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="dabe0-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dabe0-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dabe0-147">CommonParameters</span></span>

<span data-ttu-id="dabe0-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dabe0-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dabe0-149">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="dabe0-149">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="dabe0-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="dabe0-150">INPUTS</span></span>

### <span data-ttu-id="dabe0-151">System.Management.Automation.PSDriveInfo</span><span class="sxs-lookup"><span data-stu-id="dabe0-151">System.Management.Automation.PSDriveInfo</span></span>

<span data-ttu-id="dabe0-152">Du kan skicka vidare ett enhets objekt, till exempel ett från `Get-PSDrive` cmdlet: en, till `Remove-PSDrive` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="dabe0-152">You can pipe a drive object, such as one from the `Get-PSDrive` cmdlet, to the `Remove-PSDrive` cmdlet.</span></span>

## <span data-ttu-id="dabe0-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dabe0-153">OUTPUTS</span></span>

### <span data-ttu-id="dabe0-154">Inget</span><span class="sxs-lookup"><span data-stu-id="dabe0-154">None</span></span>

<span data-ttu-id="dabe0-155">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="dabe0-155">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="dabe0-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dabe0-156">NOTES</span></span>

- <span data-ttu-id="dabe0-157">`Remove-PSDrive`Cmdleten är utformad för att fungera med data som exponeras av en PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="dabe0-157">The `Remove-PSDrive` cmdlet is designed to work with the data exposed by any PowerShell provider.</span></span> <span data-ttu-id="dabe0-158">Om du vill visa en lista över providers i sessionen använder du `Get-PSProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dabe0-158">To list the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="dabe0-159">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="dabe0-159">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="dabe0-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dabe0-160">RELATED LINKS</span></span>

[<span data-ttu-id="dabe0-161">Get-PSDrive</span><span class="sxs-lookup"><span data-stu-id="dabe0-161">Get-PSDrive</span></span>](Get-PSDrive.md)

[<span data-ttu-id="dabe0-162">New-PSDrive</span><span class="sxs-lookup"><span data-stu-id="dabe0-162">New-PSDrive</span></span>](New-PSDrive.md)

[<span data-ttu-id="dabe0-163">about_Providers</span><span class="sxs-lookup"><span data-stu-id="dabe0-163">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

