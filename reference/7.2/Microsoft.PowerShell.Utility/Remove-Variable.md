---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: 6b9d351b5092d96d7698a28d3de63a493d566c6d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710345"
---
# <span data-ttu-id="e65b0-102">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="e65b0-102">Remove-Variable</span></span>

## <span data-ttu-id="e65b0-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e65b0-103">SYNOPSIS</span></span>
<span data-ttu-id="e65b0-104">Tar bort en variabel och dess värde.</span><span class="sxs-lookup"><span data-stu-id="e65b0-104">Deletes a variable and its value.</span></span>

## <span data-ttu-id="e65b0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e65b0-105">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e65b0-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e65b0-106">DESCRIPTION</span></span>

<span data-ttu-id="e65b0-107">`Remove-Variable`Cmdleten tar bort en variabel och dess värde från omfånget som den definieras i, till exempel den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e65b0-107">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="e65b0-108">Du kan inte använda denna cmdlet för att ta bort variabler som har angetts som konstanter eller som ägs av systemet.</span><span class="sxs-lookup"><span data-stu-id="e65b0-108">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="e65b0-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e65b0-109">EXAMPLES</span></span>

### <span data-ttu-id="e65b0-110">Exempel 1: ta bort en variabel</span><span class="sxs-lookup"><span data-stu-id="e65b0-110">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="e65b0-111">Det här kommandot tar bort `$Smp` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e65b0-111">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="e65b0-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e65b0-112">PARAMETERS</span></span>

### <span data-ttu-id="e65b0-113">-Undanta</span><span class="sxs-lookup"><span data-stu-id="e65b0-113">-Exclude</span></span>

<span data-ttu-id="e65b0-114">Anger en matris med objekt som denna cmdlet utelämnar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e65b0-114">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="e65b0-115">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="e65b0-115">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e65b0-116">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="e65b0-116">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="e65b0-117">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e65b0-117">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e65b0-118">-Force</span><span class="sxs-lookup"><span data-stu-id="e65b0-118">-Force</span></span>

<span data-ttu-id="e65b0-119">Anger att cmdleten tar bort en variabel även om den är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="e65b0-119">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="e65b0-120">Även om du använder **Force** -parametern kan cmdleten inte ta bort en konstant.</span><span class="sxs-lookup"><span data-stu-id="e65b0-120">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="e65b0-121">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="e65b0-121">-Include</span></span>

<span data-ttu-id="e65b0-122">Anger en matris med objekt som denna cmdlet tar bort i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e65b0-122">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="e65b0-123">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="e65b0-123">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e65b0-124">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="e65b0-124">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="e65b0-125">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e65b0-125">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e65b0-126">-Name</span><span class="sxs-lookup"><span data-stu-id="e65b0-126">-Name</span></span>

<span data-ttu-id="e65b0-127">Anger namnet på den variabel som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="e65b0-127">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="e65b0-128">Parameter namnet (**namn**) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="e65b0-128">The parameter name (**Name**) is optional.</span></span>
<span data-ttu-id="e65b0-129">Jokertecken tillåts</span><span class="sxs-lookup"><span data-stu-id="e65b0-129">Wildcards are permitted</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="e65b0-130">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="e65b0-130">-Scope</span></span>

<span data-ttu-id="e65b0-131">Hämtar endast variablerna i det angivna omfånget.</span><span class="sxs-lookup"><span data-stu-id="e65b0-131">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="e65b0-132">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="e65b0-132">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e65b0-133">Global</span><span class="sxs-lookup"><span data-stu-id="e65b0-133">Global</span></span>
- <span data-ttu-id="e65b0-134">Lokal</span><span class="sxs-lookup"><span data-stu-id="e65b0-134">Local</span></span>
- <span data-ttu-id="e65b0-135">Skript</span><span class="sxs-lookup"><span data-stu-id="e65b0-135">Script</span></span>
- <span data-ttu-id="e65b0-136">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="e65b0-136">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="e65b0-137">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="e65b0-137">Local is the default.</span></span> <span data-ttu-id="e65b0-138">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e65b0-138">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e65b0-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e65b0-139">-Confirm</span></span>

<span data-ttu-id="e65b0-140">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e65b0-140">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e65b0-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e65b0-141">-WhatIf</span></span>

<span data-ttu-id="e65b0-142">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e65b0-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e65b0-143">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e65b0-143">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e65b0-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e65b0-144">CommonParameters</span></span>

<span data-ttu-id="e65b0-145">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e65b0-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e65b0-146">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e65b0-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e65b0-147">INDATA</span><span class="sxs-lookup"><span data-stu-id="e65b0-147">INPUTS</span></span>

### <span data-ttu-id="e65b0-148">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="e65b0-148">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="e65b0-149">Du kan skicka vidare ett variabel objekt till `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="e65b0-149">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="e65b0-150">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e65b0-150">OUTPUTS</span></span>

### <span data-ttu-id="e65b0-151">Inga</span><span class="sxs-lookup"><span data-stu-id="e65b0-151">None</span></span>

<span data-ttu-id="e65b0-152">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e65b0-152">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="e65b0-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e65b0-153">NOTES</span></span>

- <span data-ttu-id="e65b0-154">Ändringarna påverkar bara det aktuella omfånget, till exempel en session.</span><span class="sxs-lookup"><span data-stu-id="e65b0-154">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="e65b0-155">Om du vill ta bort en variabel från alla sessioner lägger du till ett `Remove-Variable` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="e65b0-155">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="e65b0-156">Du kan också referera till `Remove-Variable` med dess inbyggda alias `rv` .</span><span class="sxs-lookup"><span data-stu-id="e65b0-156">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="e65b0-157">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="e65b0-157">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="e65b0-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e65b0-158">RELATED LINKS</span></span>

[<span data-ttu-id="e65b0-159">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="e65b0-159">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="e65b0-160">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="e65b0-160">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="e65b0-161">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="e65b0-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="e65b0-162">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="e65b0-162">Set-Variable</span></span>](Set-Variable.md)
