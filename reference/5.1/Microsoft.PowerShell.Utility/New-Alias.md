---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: 00ef887dc79e35a6dff299a37bfafa57aebc77db
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264939"
---
# <span data-ttu-id="b6820-103">New-Alias</span><span class="sxs-lookup"><span data-stu-id="b6820-103">New-Alias</span></span>

## <span data-ttu-id="b6820-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b6820-104">SYNOPSIS</span></span>
<span data-ttu-id="b6820-105">Skapar ett nytt alias.</span><span class="sxs-lookup"><span data-stu-id="b6820-105">Creates a new alias.</span></span>

## <span data-ttu-id="b6820-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6820-106">SYNTAX</span></span>

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b6820-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b6820-107">DESCRIPTION</span></span>
<span data-ttu-id="b6820-108">Cmdleten **New-aliase** skapar ett nytt alias i den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b6820-108">The **New-Alias** cmdlet creates a new alias in the current Windows PowerShell session.</span></span>
<span data-ttu-id="b6820-109">Alias som skapats med hjälp av **New-alias** sparas inte när du avslutar-sessionen eller stänger Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b6820-109">Aliases created by using **New-Alias** are not saved after you exit the session or close Windows PowerShell.</span></span>
<span data-ttu-id="b6820-110">Du kan använda Export-Alias-cmdlet: en för att spara Ali Aset information till en fil.</span><span class="sxs-lookup"><span data-stu-id="b6820-110">You can use the Export-Alias cmdlet to save your alias information to a file.</span></span>
<span data-ttu-id="b6820-111">Du kan senare använda **import-alias** för att hämta information om sparat alias.</span><span class="sxs-lookup"><span data-stu-id="b6820-111">You can later use **Import-Alias** to retrieve that saved alias information.</span></span>

## <span data-ttu-id="b6820-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b6820-112">EXAMPLES</span></span>

### <span data-ttu-id="b6820-113">Exempel 1: skapa ett alias för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6820-113">Example 1: Create an alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

<span data-ttu-id="b6820-114">Det här kommandot skapar en lista med namngivna alias som representerar Get-ChildItem-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6820-114">This command creates an alias named List to represent the Get-ChildItem cmdlet.</span></span>

### <span data-ttu-id="b6820-115">Exempel 2: skapa ett skrivskyddat alias för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="b6820-115">Example 2: Create a read-only alias for a cmdlet</span></span>

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

<span data-ttu-id="b6820-116">Det här kommandot skapar ett alias med namnet W för att representera Get-WmiObject-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6820-116">This command creates an alias named W to represent the Get-WmiObject cmdlet.</span></span>
<span data-ttu-id="b6820-117">Den skapar en beskrivning, ett snabb WMI-alias för aliaset och gör det skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="b6820-117">It creates a description, quick wmi alias, for the alias and makes it read-only.</span></span>
<span data-ttu-id="b6820-118">Den sista raden i kommandot använder Get-Alias för att hämta det nya aliaset och rör det för att Format-List för att visa all information om det.</span><span class="sxs-lookup"><span data-stu-id="b6820-118">The last line of the command uses Get-Alias to get the new alias and pipes it to Format-List to display all of the information about it.</span></span>

## <span data-ttu-id="b6820-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b6820-119">PARAMETERS</span></span>

### <span data-ttu-id="b6820-120">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b6820-120">-Description</span></span>
<span data-ttu-id="b6820-121">Anger en beskrivning av aliaset.</span><span class="sxs-lookup"><span data-stu-id="b6820-121">Specifies a description of the alias.</span></span>
<span data-ttu-id="b6820-122">Du kan ange valfri sträng.</span><span class="sxs-lookup"><span data-stu-id="b6820-122">You can type any string.</span></span>
<span data-ttu-id="b6820-123">Om beskrivningen innehåller blank steg, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b6820-123">If the description includes spaces, enclose it in quotation marks.</span></span>

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

### <span data-ttu-id="b6820-124">-Force</span><span class="sxs-lookup"><span data-stu-id="b6820-124">-Force</span></span>
<span data-ttu-id="b6820-125">Anger att cmdleten fungerar som Set-Alias om aliaset redan finns.</span><span class="sxs-lookup"><span data-stu-id="b6820-125">Indicates that the cmdlet acts like Set-Alias if the alias named already exists.</span></span>

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

### <span data-ttu-id="b6820-126">-Name</span><span class="sxs-lookup"><span data-stu-id="b6820-126">-Name</span></span>
<span data-ttu-id="b6820-127">Anger det nya aliaset.</span><span class="sxs-lookup"><span data-stu-id="b6820-127">Specifies the new alias.</span></span>
<span data-ttu-id="b6820-128">Du kan använda alla alfanumeriska tecken i ett alias, men det första tecknet får inte vara en siffra.</span><span class="sxs-lookup"><span data-stu-id="b6820-128">You can use any alphanumeric characters in an alias, but the first character cannot be a number.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b6820-129">-Alternativ</span><span class="sxs-lookup"><span data-stu-id="b6820-129">-Option</span></span>
<span data-ttu-id="b6820-130">Anger värdet för egenskapen **Options** för aliaset.</span><span class="sxs-lookup"><span data-stu-id="b6820-130">Specifies the value of the **Options** property of the alias.</span></span>
<span data-ttu-id="b6820-131">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="b6820-131">Valid values are:</span></span>

- <span data-ttu-id="b6820-132">Ingen: aliaset saknar begränsningar (standardvärde)</span><span class="sxs-lookup"><span data-stu-id="b6820-132">None: The alias has no constraints (default value)</span></span>
- <span data-ttu-id="b6820-133">ReadOnly: aliaset kan tas bort men kan inte ändras förutom med parametern **Force**</span><span class="sxs-lookup"><span data-stu-id="b6820-133">ReadOnly: The alias can be deleted but cannot be changed except by using the **Force** parameter</span></span>
- <span data-ttu-id="b6820-134">Konstant: aliaset kan inte tas bort eller ändras</span><span class="sxs-lookup"><span data-stu-id="b6820-134">Constant: The alias cannot be deleted or changed</span></span>
- <span data-ttu-id="b6820-135">Privat: aliaset är endast tillgängligt i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="b6820-135">Private: The alias is available only in the current scope</span></span>
- <span data-ttu-id="b6820-136">AllScope: aliaset kopieras till alla nya omfattningar som skapas</span><span class="sxs-lookup"><span data-stu-id="b6820-136">AllScope: The alias is copied to any new scopes that are created</span></span>
- <span data-ttu-id="b6820-137">Ospecificerad: inget alternativ har angetts</span><span class="sxs-lookup"><span data-stu-id="b6820-137">Unspecified: The option is not specified</span></span>

<span data-ttu-id="b6820-138">Om du vill se egenskapen **alternativ** för alla alias i sessionen skriver du `Get-Alias | Format-Table -Property Name, Options -AutoSize` .</span><span class="sxs-lookup"><span data-stu-id="b6820-138">To see the **Options** property of all aliases in the session, type `Get-Alias | Format-Table -Property Name, Options -AutoSize`.</span></span>

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6820-139">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b6820-139">-PassThru</span></span>
<span data-ttu-id="b6820-140">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="b6820-140">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="b6820-141">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b6820-141">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="b6820-142">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="b6820-142">-Scope</span></span>
<span data-ttu-id="b6820-143">Anger omfånget för det nya aliaset.</span><span class="sxs-lookup"><span data-stu-id="b6820-143">Specifies the scope of the new alias.</span></span>
<span data-ttu-id="b6820-144">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="b6820-144">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b6820-145">Global</span><span class="sxs-lookup"><span data-stu-id="b6820-145">Global</span></span>
- <span data-ttu-id="b6820-146">Lokal</span><span class="sxs-lookup"><span data-stu-id="b6820-146">Local</span></span>
- <span data-ttu-id="b6820-147">Skript</span><span class="sxs-lookup"><span data-stu-id="b6820-147">Script</span></span>
- <span data-ttu-id="b6820-148">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="b6820-148">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>

<span data-ttu-id="b6820-149">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="b6820-149">Local is the default.</span></span>
<span data-ttu-id="b6820-150">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="b6820-150">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="b6820-151">-Värde</span><span class="sxs-lookup"><span data-stu-id="b6820-151">-Value</span></span>
<span data-ttu-id="b6820-152">Anger namnet på den cmdlet eller det kommando element som har ett alias.</span><span class="sxs-lookup"><span data-stu-id="b6820-152">Specifies the name of the cmdlet or command element that is being aliased.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b6820-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b6820-153">-Confirm</span></span>
<span data-ttu-id="b6820-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6820-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b6820-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b6820-155">-WhatIf</span></span>
<span data-ttu-id="b6820-156">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b6820-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b6820-157">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b6820-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b6820-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6820-158">CommonParameters</span></span>
<span data-ttu-id="b6820-159">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6820-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6820-160">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b6820-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6820-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="b6820-161">INPUTS</span></span>

### <span data-ttu-id="b6820-162">Inget</span><span class="sxs-lookup"><span data-stu-id="b6820-162">None</span></span>
<span data-ttu-id="b6820-163">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6820-163">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b6820-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b6820-164">OUTPUTS</span></span>

### <span data-ttu-id="b6820-165">Ingen eller system. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="b6820-165">None or System.Management.Automation.AliasInfo</span></span>
<span data-ttu-id="b6820-166">När du använder parametern *Passthru* genererar **New-alias** ett **system. Management. Automation. AliasInfo** -objekt som representerar det nya aliaset.</span><span class="sxs-lookup"><span data-stu-id="b6820-166">When you use the *Passthru* parameter, **New-Alias** generates a **System.Management.Automation.AliasInfo** object representing the new alias.</span></span>
<span data-ttu-id="b6820-167">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b6820-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b6820-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b6820-168">NOTES</span></span>

* <span data-ttu-id="b6820-169">Om du vill skapa ett nytt alias använder Set-Alias eller New-alias.</span><span class="sxs-lookup"><span data-stu-id="b6820-169">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="b6820-170">Om du vill ändra ett alias använder du **set-alias**.</span><span class="sxs-lookup"><span data-stu-id="b6820-170">To change an alias, use **Set-Alias**.</span></span> <span data-ttu-id="b6820-171">Använd Remove-Item om du vill ta bort ett alias.</span><span class="sxs-lookup"><span data-stu-id="b6820-171">To delete an alias, use Remove-Item.</span></span>

*

## <span data-ttu-id="b6820-172">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b6820-172">RELATED LINKS</span></span>

[<span data-ttu-id="b6820-173">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="b6820-173">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="b6820-174">Get-alias</span><span class="sxs-lookup"><span data-stu-id="b6820-174">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="b6820-175">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="b6820-175">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="b6820-176">Set-alias</span><span class="sxs-lookup"><span data-stu-id="b6820-176">Set-Alias</span></span>](Set-Alias.md)