---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: c6347ea9ca2169c6379871131bc98001bcdb5d25
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268700"
---
# <span data-ttu-id="fb437-103">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="fb437-103">Remove-Variable</span></span>

## <span data-ttu-id="fb437-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fb437-104">SYNOPSIS</span></span>
<span data-ttu-id="fb437-105">Tar bort en variabel och dess värde.</span><span class="sxs-lookup"><span data-stu-id="fb437-105">Deletes a variable and its value.</span></span>

## <span data-ttu-id="fb437-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb437-106">SYNTAX</span></span>

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="fb437-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fb437-107">DESCRIPTION</span></span>

<span data-ttu-id="fb437-108">`Remove-Variable`Cmdleten tar bort en variabel och dess värde från omfånget som den definieras i, till exempel den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb437-108">The `Remove-Variable` cmdlet deletes a variable and its value from the scope in which it is defined, such as the current session.</span></span> <span data-ttu-id="fb437-109">Du kan inte använda denna cmdlet för att ta bort variabler som har angetts som konstanter eller som ägs av systemet.</span><span class="sxs-lookup"><span data-stu-id="fb437-109">You cannot use this cmdlet to delete variables that are set as constants or those that are owned by the system.</span></span>

## <span data-ttu-id="fb437-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fb437-110">EXAMPLES</span></span>

### <span data-ttu-id="fb437-111">Exempel 1: ta bort en variabel</span><span class="sxs-lookup"><span data-stu-id="fb437-111">Example 1: Remove a variable</span></span>

```powershell
Remove-Variable Smp
```

<span data-ttu-id="fb437-112">Det här kommandot tar bort `$Smp` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fb437-112">This command deletes the `$Smp` variable.</span></span>

## <span data-ttu-id="fb437-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fb437-113">PARAMETERS</span></span>

### <span data-ttu-id="fb437-114">-Undanta</span><span class="sxs-lookup"><span data-stu-id="fb437-114">-Exclude</span></span>

<span data-ttu-id="fb437-115">Anger en matris med objekt som denna cmdlet utelämnar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fb437-115">Specifies an array of items that this cmdlet omits from the operation.</span></span> <span data-ttu-id="fb437-116">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="fb437-116">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="fb437-117">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="fb437-117">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="fb437-118">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="fb437-118">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="fb437-119">-Force</span><span class="sxs-lookup"><span data-stu-id="fb437-119">-Force</span></span>

<span data-ttu-id="fb437-120">Anger att cmdleten tar bort en variabel även om den är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="fb437-120">Indicates that the cmdlet removes a variable even if it is read-only.</span></span> <span data-ttu-id="fb437-121">Även om du använder **Force** -parametern kan cmdleten inte ta bort en konstant.</span><span class="sxs-lookup"><span data-stu-id="fb437-121">Even using the **Force** parameter, the cmdlet cannot remove a constant.</span></span>

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

### <span data-ttu-id="fb437-122">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="fb437-122">-Include</span></span>

<span data-ttu-id="fb437-123">Anger en matris med objekt som denna cmdlet tar bort i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="fb437-123">Specifies an array of items that this cmdlet deletes in the operation.</span></span> <span data-ttu-id="fb437-124">Värdet för den här parametern kvalificerar parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="fb437-124">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="fb437-125">Ange ett namn element eller ett mönster, till exempel s \*.</span><span class="sxs-lookup"><span data-stu-id="fb437-125">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="fb437-126">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="fb437-126">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="fb437-127">-Name</span><span class="sxs-lookup"><span data-stu-id="fb437-127">-Name</span></span>

<span data-ttu-id="fb437-128">Anger namnet på den variabel som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="fb437-128">Specifies the name of the variable to be removed.</span></span> <span data-ttu-id="fb437-129">Parameter namnet ( **namn** ) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="fb437-129">The parameter name ( **Name** ) is optional.</span></span>
<span data-ttu-id="fb437-130">Jokertecken tillåts</span><span class="sxs-lookup"><span data-stu-id="fb437-130">Wildcards are permitted</span></span>

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

### <span data-ttu-id="fb437-131">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="fb437-131">-Scope</span></span>

<span data-ttu-id="fb437-132">Hämtar endast variablerna i det angivna omfånget.</span><span class="sxs-lookup"><span data-stu-id="fb437-132">Gets only the variables in the specified scope.</span></span> <span data-ttu-id="fb437-133">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="fb437-133">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="fb437-134">Global</span><span class="sxs-lookup"><span data-stu-id="fb437-134">Global</span></span>
- <span data-ttu-id="fb437-135">Lokal</span><span class="sxs-lookup"><span data-stu-id="fb437-135">Local</span></span>
- <span data-ttu-id="fb437-136">Skript</span><span class="sxs-lookup"><span data-stu-id="fb437-136">Script</span></span>
- <span data-ttu-id="fb437-137">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="fb437-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="fb437-138">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="fb437-138">Local is the default.</span></span> <span data-ttu-id="fb437-139">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="fb437-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="fb437-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="fb437-140">-Confirm</span></span>

<span data-ttu-id="fb437-141">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="fb437-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="fb437-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="fb437-142">-WhatIf</span></span>

<span data-ttu-id="fb437-143">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="fb437-143">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="fb437-144">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="fb437-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="fb437-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb437-145">CommonParameters</span></span>

<span data-ttu-id="fb437-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb437-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb437-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fb437-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb437-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="fb437-148">INPUTS</span></span>

### <span data-ttu-id="fb437-149">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="fb437-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="fb437-150">Du kan skicka vidare ett variabel objekt till `Remove-Variable` .</span><span class="sxs-lookup"><span data-stu-id="fb437-150">You can pipe a variable object to `Remove-Variable`.</span></span>

## <span data-ttu-id="fb437-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fb437-151">OUTPUTS</span></span>

### <span data-ttu-id="fb437-152">Inget</span><span class="sxs-lookup"><span data-stu-id="fb437-152">None</span></span>

<span data-ttu-id="fb437-153">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="fb437-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="fb437-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fb437-154">NOTES</span></span>

- <span data-ttu-id="fb437-155">Ändringarna påverkar bara det aktuella omfånget, till exempel en session.</span><span class="sxs-lookup"><span data-stu-id="fb437-155">Changes affect only the current scope, such as a session.</span></span> <span data-ttu-id="fb437-156">Om du vill ta bort en variabel från alla sessioner lägger du till ett `Remove-Variable` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="fb437-156">To delete a variable from all sessions, add a `Remove-Variable` command to your PowerShell profile.</span></span>

- <span data-ttu-id="fb437-157">Du kan också referera till `Remove-Variable` med dess inbyggda alias `rv` .</span><span class="sxs-lookup"><span data-stu-id="fb437-157">You can also refer to `Remove-Variable` by its built-in alias, `rv`.</span></span> <span data-ttu-id="fb437-158">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="fb437-158">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

## <span data-ttu-id="fb437-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fb437-159">RELATED LINKS</span></span>

[<span data-ttu-id="fb437-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="fb437-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="fb437-161">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="fb437-161">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="fb437-162">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="fb437-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="fb437-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="fb437-163">Set-Variable</span></span>](Set-Variable.md)
