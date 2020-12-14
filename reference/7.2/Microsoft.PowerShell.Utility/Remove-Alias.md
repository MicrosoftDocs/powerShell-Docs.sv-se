---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 0ce13bef77e9ef9647809336aed650833dab51f3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708358"
---
# <span data-ttu-id="e7dc4-102">Remove-Alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-102">Remove-Alias</span></span>

## <span data-ttu-id="e7dc4-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e7dc4-103">SYNOPSIS</span></span>
<span data-ttu-id="e7dc4-104">Ta bort ett alias från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-104">Remove an alias from the current session.</span></span>

## <span data-ttu-id="e7dc4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e7dc4-105">SYNTAX</span></span>

### <span data-ttu-id="e7dc4-106">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="e7dc4-106">Default (Default)</span></span>

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="e7dc4-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e7dc4-107">DESCRIPTION</span></span>

<span data-ttu-id="e7dc4-108">`Remove-Alias`Cmdleten tar bort ett alias från den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-108">The `Remove-Alias` cmdlet removes an alias from the current PowerShell session.</span></span> <span data-ttu-id="e7dc4-109">Använd parametern **Force** om du vill ta bort ett alias med **alternativ** egenskapen inställd på **skrivskyddad**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-109">To remove an alias with the **Option** property set to **ReadOnly**, use the **Force** parameter.</span></span>

<span data-ttu-id="e7dc4-110">`Remove-Alias`Cmdleten introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-110">The `Remove-Alias` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="e7dc4-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e7dc4-111">EXAMPLES</span></span>

### <span data-ttu-id="e7dc4-112">Exempel 1 – ta bort ett alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-112">Example 1 - Remove an alias</span></span>

<span data-ttu-id="e7dc4-113">I det här exemplet tas ett alias `del` som heter som representerar `Remove-Item` cmdleten bort.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-113">This example removes an alias named `del` that represents the `Remove-Item` cmdlet.</span></span>

```powershell
Remove-Alias -Name del
```

### <span data-ttu-id="e7dc4-114">Exempel 2 – ta bort alla icke-konstanta alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-114">Example 2 - Remove all non-Constant aliases</span></span>

<span data-ttu-id="e7dc4-115">I det här exemplet tas alla alias från den aktuella PowerShell-sessionen bort, förutom alias med egenskapen **alternativ** inställd på **konstant**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-115">This example removes all aliases from the current PowerShell session, except for aliases with the **Options** property set to **Constant**.</span></span> <span data-ttu-id="e7dc4-116">När kommandot har körts är aliasen tillgängliga i andra PowerShell-sessioner eller nya PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-116">After the command is run, the aliases are available in other PowerShell sessions or new PowerShell sessions.</span></span>

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

<span data-ttu-id="e7dc4-117">`Get-Alias` hämtar alla alias i PowerShell-sessionen och skickar objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-117">`Get-Alias` gets all the aliases in the PowerShell session and sends the objects down the pipeline.</span></span>
<span data-ttu-id="e7dc4-118">`Where-Object` använder ett-skript block och egenskapen automatisk variabel ( `$_` ) och **alternativ** representerar det aktuella pipeline-objektet.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-118">`Where-Object` uses a script block, and the automatic variable (`$_`) and **Options** property represent the current pipeline object.</span></span> <span data-ttu-id="e7dc4-119">Parametern **Ne** (inte lika med) väljer objekt som inte har något **alternativ** värde inställt på **konstant**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-119">The parameter **NE** (not equal), selects objects that don't have an **Options** value set to **Constant**.</span></span> <span data-ttu-id="e7dc4-120">`Remove-Alias` använder **Force** -parametern för att ta bort alias, inklusive skrivskyddade alias, från PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-120">`Remove-Alias` uses the **Force** parameter to remove aliases, including read-only aliases, from the PowerShell session.</span></span>

## <span data-ttu-id="e7dc4-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e7dc4-121">PARAMETERS</span></span>

### <span data-ttu-id="e7dc4-122">-Force</span><span class="sxs-lookup"><span data-stu-id="e7dc4-122">-Force</span></span>

<span data-ttu-id="e7dc4-123">Anger att cmdleten tar bort ett alias, inklusive alias med **alternativ** egenskapen inställd på **skrivskyddad**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-123">Indicates that the cmdlet removes an alias, including aliases with the **Option** property set to **ReadOnly**.</span></span> <span data-ttu-id="e7dc4-124">Parametern **Force** kan inte ta bort ett alias med en **alternativ** egenskap inställd på **konstant**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-124">The **Force** parameter can't remove an alias with an **Option** property set to **Constant**.</span></span>

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

### <span data-ttu-id="e7dc4-125">-Name</span><span class="sxs-lookup"><span data-stu-id="e7dc4-125">-Name</span></span>

<span data-ttu-id="e7dc4-126">Anger namnet på det alias som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-126">Specifies the name of the alias to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e7dc4-127">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="e7dc4-127">-Scope</span></span>

<span data-ttu-id="e7dc4-128">Påverkar endast alias i det angivna omfånget.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-128">Affects only the aliases in the specified scope.</span></span> <span data-ttu-id="e7dc4-129">Standard omfånget är **lokalt**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-129">The default scope is **Local**.</span></span> <span data-ttu-id="e7dc4-130">Mer information finns i [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e7dc4-130">For more information, see [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).</span></span>

<span data-ttu-id="e7dc4-131">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="e7dc4-131">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e7dc4-132">Global</span><span class="sxs-lookup"><span data-stu-id="e7dc4-132">Global</span></span>
- <span data-ttu-id="e7dc4-133">Lokal</span><span class="sxs-lookup"><span data-stu-id="e7dc4-133">Local</span></span>
- <span data-ttu-id="e7dc4-134">Skript</span><span class="sxs-lookup"><span data-stu-id="e7dc4-134">Script</span></span>
- <span data-ttu-id="e7dc4-135">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="e7dc4-135">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e7dc4-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e7dc4-136">CommonParameters</span></span>

<span data-ttu-id="e7dc4-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e7dc4-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e7dc4-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e7dc4-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="e7dc4-139">INPUTS</span></span>

### <span data-ttu-id="e7dc4-140">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e7dc4-140">System.String[]</span></span>

<span data-ttu-id="e7dc4-141">Du kan skicka ett aliasresurspost till **Remove-alias**.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-141">You can pipe an alias object to **Remove-Alias**.</span></span>

## <span data-ttu-id="e7dc4-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e7dc4-142">OUTPUTS</span></span>

### <span data-ttu-id="e7dc4-143">Inga</span><span class="sxs-lookup"><span data-stu-id="e7dc4-143">None</span></span>

<span data-ttu-id="e7dc4-144">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-144">This cmdlet doesn't return any output.</span></span>

## <span data-ttu-id="e7dc4-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e7dc4-145">NOTES</span></span>

<span data-ttu-id="e7dc4-146">Ändringarna påverkar bara det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-146">Changes only affect the current scope.</span></span> <span data-ttu-id="e7dc4-147">Om du vill ta bort ett alias från alla sessioner lägger du till kommandot **Remove-alias** i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="e7dc4-147">To remove an alias from all sessions, add a **Remove-Alias** command to your PowerShell profile.</span></span>

<span data-ttu-id="e7dc4-148">Mer information finns i [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span><span class="sxs-lookup"><span data-stu-id="e7dc4-148">For more information, see [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).</span></span>

## <span data-ttu-id="e7dc4-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e7dc4-149">RELATED LINKS</span></span>

[<span data-ttu-id="e7dc4-150">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e7dc4-150">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="e7dc4-151">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-151">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="e7dc4-152">Get-alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-152">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="e7dc4-153">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-153">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="e7dc4-154">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-154">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="e7dc4-155">Set-alias</span><span class="sxs-lookup"><span data-stu-id="e7dc4-155">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="e7dc4-156">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="e7dc4-156">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

