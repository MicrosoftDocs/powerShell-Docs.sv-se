---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 0381b48097f75d3195a82a67225cd8d6759e7433
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709109"
---
# <span data-ttu-id="d1096-102">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="d1096-102">Clear-Variable</span></span>

## <span data-ttu-id="d1096-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d1096-103">SYNOPSIS</span></span>
<span data-ttu-id="d1096-104">Tar bort värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="d1096-104">Deletes the value of a variable.</span></span>

## <span data-ttu-id="d1096-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d1096-105">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d1096-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d1096-106">DESCRIPTION</span></span>

<span data-ttu-id="d1096-107">Cmdleten **Clear-Variable** tar bort data som lagras i en variabel, men den tar inte bort variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1096-107">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="d1096-108">Det innebär att variabelns värde är NULL (tomt).</span><span class="sxs-lookup"><span data-stu-id="d1096-108">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="d1096-109">Om variabeln har en angiven data-eller objekt typ, bevarar denna cmdlet den typ av objekt som lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1096-109">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="d1096-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d1096-110">EXAMPLES</span></span>

### <span data-ttu-id="d1096-111">Exempel 1: ta bort värdet för globala variabler som börjar med en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="d1096-111">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="d1096-112">Det här kommandot tar bort värdet för globala variabler som har namn som börjar med My.</span><span class="sxs-lookup"><span data-stu-id="d1096-112">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="d1096-113">Exempel 2: ta bort en variabel i ett underordnat område, men inte över överordnat område</span><span class="sxs-lookup"><span data-stu-id="d1096-113">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="d1096-114">De här kommandona visar att att rensa en variabel i ett underordnat omfång inte rensar värdet i det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="d1096-114">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="d1096-115">Det första kommandot ställer in värdet för variabeln $A till 3.</span><span class="sxs-lookup"><span data-stu-id="d1096-115">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="d1096-116">Det andra kommandot använder operatorn Invoke (&) för att köra kommandot **Clear-Variable** i ett nytt omfång.</span><span class="sxs-lookup"><span data-stu-id="d1096-116">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="d1096-117">Variabeln har rensats i det underordnade omfånget (även om den inte finns), men den har inte rensats i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="d1096-117">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="d1096-118">Det tredje kommandot, som hämtar värdet för $A, visar att värdet 3 inte påverkas.</span><span class="sxs-lookup"><span data-stu-id="d1096-118">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="d1096-119">Exempel 3: ta bort värdet för den angivna variabeln</span><span class="sxs-lookup"><span data-stu-id="d1096-119">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="d1096-120">Det här kommandot tar bort värdet för variabeln med namnet processs.</span><span class="sxs-lookup"><span data-stu-id="d1096-120">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="d1096-121">När cmdleten har slutfört åtgärden finns variabeln som heter processer fortfarande, men värdet är null.</span><span class="sxs-lookup"><span data-stu-id="d1096-121">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="d1096-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d1096-122">PARAMETERS</span></span>

### <span data-ttu-id="d1096-123">-Undanta</span><span class="sxs-lookup"><span data-stu-id="d1096-123">-Exclude</span></span>

<span data-ttu-id="d1096-124">Anger en matris med objekt som denna cmdlet utelämnar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d1096-124">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="d1096-125">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="d1096-125">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="d1096-126">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="d1096-126">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="d1096-127">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d1096-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="d1096-128">-Force</span><span class="sxs-lookup"><span data-stu-id="d1096-128">-Force</span></span>

<span data-ttu-id="d1096-129">Tillåter cmdleten att ta bort en variabel även om den är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="d1096-129">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="d1096-130">Cmdleten kan inte ta bort konstanter även om du använder Force-parametern.</span><span class="sxs-lookup"><span data-stu-id="d1096-130">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="d1096-131">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="d1096-131">-Include</span></span>

<span data-ttu-id="d1096-132">Anger en matris med objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d1096-132">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="d1096-133">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="d1096-133">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="d1096-134">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="d1096-134">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="d1096-135">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d1096-135">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="d1096-136">-Name</span><span class="sxs-lookup"><span data-stu-id="d1096-136">-Name</span></span>

<span data-ttu-id="d1096-137">Anger namnet på den variabel som ska rensas.</span><span class="sxs-lookup"><span data-stu-id="d1096-137">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="d1096-138">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d1096-138">Wildcards are permitted.</span></span>
<span data-ttu-id="d1096-139">Den här parametern är obligatorisk, men parameter namnet ("name") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="d1096-139">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="d1096-140">– PassThru</span><span class="sxs-lookup"><span data-stu-id="d1096-140">-PassThru</span></span>

<span data-ttu-id="d1096-141">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="d1096-141">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="d1096-142">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d1096-142">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="d1096-143">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="d1096-143">-Scope</span></span>

<span data-ttu-id="d1096-144">Anger omfattningen som detta alias är giltigt i.</span><span class="sxs-lookup"><span data-stu-id="d1096-144">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="d1096-145">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="d1096-145">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d1096-146">Global</span><span class="sxs-lookup"><span data-stu-id="d1096-146">Global</span></span>
- <span data-ttu-id="d1096-147">Lokal</span><span class="sxs-lookup"><span data-stu-id="d1096-147">Local</span></span>
- <span data-ttu-id="d1096-148">Skript</span><span class="sxs-lookup"><span data-stu-id="d1096-148">Script</span></span>

<span data-ttu-id="d1096-149">Du kan också använda ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="d1096-149">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="d1096-150">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="d1096-150">Local is the default.</span></span>
<span data-ttu-id="d1096-151">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="d1096-151">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="d1096-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d1096-152">-Confirm</span></span>

<span data-ttu-id="d1096-153">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d1096-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d1096-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d1096-154">-WhatIf</span></span>

<span data-ttu-id="d1096-155">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="d1096-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d1096-156">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="d1096-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d1096-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1096-157">CommonParameters</span></span>

<span data-ttu-id="d1096-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1096-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1096-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d1096-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1096-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="d1096-160">INPUTS</span></span>

### <span data-ttu-id="d1096-161">Inga</span><span class="sxs-lookup"><span data-stu-id="d1096-161">None</span></span>

<span data-ttu-id="d1096-162">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1096-162">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="d1096-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d1096-163">OUTPUTS</span></span>

### <span data-ttu-id="d1096-164">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="d1096-164">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="d1096-165">När du använder parametern *Passthru* genererar denna cmdlet ett **system. Management. Automation. PSVariable** -objekt som representerar den rensade variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1096-165">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="d1096-166">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d1096-166">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="d1096-167">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d1096-167">NOTES</span></span>

* <span data-ttu-id="d1096-168">Om du vill ta bort en variabel, tillsammans med dess värde, använder du Remove-Variable eller ta bort objekt.</span><span class="sxs-lookup"><span data-stu-id="d1096-168">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="d1096-169">Den här cmdleten tar inte bort värdena för variabler som anges som konstanter eller ägs av systemet, även om du använder *Force* -parametern.</span><span class="sxs-lookup"><span data-stu-id="d1096-169">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="d1096-170">Om den variabel som du tar bort inte finns, har cmdleten ingen inverkan.</span><span class="sxs-lookup"><span data-stu-id="d1096-170">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="d1096-171">Den skapar inte en variabel med ett null-värde.</span><span class="sxs-lookup"><span data-stu-id="d1096-171">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="d1096-172">Du kan också referera till **Clear-Variable** med dess inbyggda alias, CLV.</span><span class="sxs-lookup"><span data-stu-id="d1096-172">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="d1096-173">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="d1096-173">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="d1096-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d1096-174">RELATED LINKS</span></span>

[<span data-ttu-id="d1096-175">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="d1096-175">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="d1096-176">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="d1096-176">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="d1096-177">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="d1096-177">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="d1096-178">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="d1096-178">Set-Variable</span></span>](Set-Variable.md)

