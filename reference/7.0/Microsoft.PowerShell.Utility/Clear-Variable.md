---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: 6208e9c1b7124c8faec1e3e87a6e815540d2b962
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263168"
---
# <span data-ttu-id="5fa43-103">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="5fa43-103">Clear-Variable</span></span>

## <span data-ttu-id="5fa43-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5fa43-104">SYNOPSIS</span></span>
<span data-ttu-id="5fa43-105">Tar bort värdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="5fa43-105">Deletes the value of a variable.</span></span>

## <span data-ttu-id="5fa43-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5fa43-106">SYNTAX</span></span>

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="5fa43-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5fa43-107">DESCRIPTION</span></span>

<span data-ttu-id="5fa43-108">Cmdleten **Clear-Variable** tar bort data som lagras i en variabel, men den tar inte bort variabeln.</span><span class="sxs-lookup"><span data-stu-id="5fa43-108">The **Clear-Variable** cmdlet deletes the data stored in a variable, but it does not delete the variable.</span></span>
<span data-ttu-id="5fa43-109">Det innebär att variabelns värde är NULL (tomt).</span><span class="sxs-lookup"><span data-stu-id="5fa43-109">As a result, the value of the variable is NULL (empty).</span></span>
<span data-ttu-id="5fa43-110">Om variabeln har en angiven data-eller objekt typ, bevarar denna cmdlet den typ av objekt som lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="5fa43-110">If the variable has a specified data or object type, this cmdlet preserves the type of the object stored in the variable.</span></span>

## <span data-ttu-id="5fa43-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5fa43-111">EXAMPLES</span></span>

### <span data-ttu-id="5fa43-112">Exempel 1: ta bort värdet för globala variabler som börjar med en Sök sträng</span><span class="sxs-lookup"><span data-stu-id="5fa43-112">Example 1: Remove the value of global variables that begin with a search string</span></span>

```
PS C:\> Clear-Variable my* -Scope Global
```

<span data-ttu-id="5fa43-113">Det här kommandot tar bort värdet för globala variabler som har namn som börjar med My.</span><span class="sxs-lookup"><span data-stu-id="5fa43-113">This command removes the value of global variables that have names that begin with my.</span></span>

### <span data-ttu-id="5fa43-114">Exempel 2: ta bort en variabel i ett underordnat område, men inte över överordnat område</span><span class="sxs-lookup"><span data-stu-id="5fa43-114">Example 2: Clear a variable in a child scope but not the parent scope</span></span>

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

<span data-ttu-id="5fa43-115">De här kommandona visar att att rensa en variabel i ett underordnat omfång inte rensar värdet i det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="5fa43-115">These commands demonstrate that clearing a variable in a child scope does not clear the value in the parent scope.</span></span>
<span data-ttu-id="5fa43-116">Det första kommandot ställer in värdet för variabeln $A till 3.</span><span class="sxs-lookup"><span data-stu-id="5fa43-116">The first command sets the value of the variable $A to 3.</span></span>
<span data-ttu-id="5fa43-117">Det andra kommandot använder operatorn Invoke (&) för att köra kommandot **Clear-Variable** i ett nytt omfång.</span><span class="sxs-lookup"><span data-stu-id="5fa43-117">The second command uses the invoke operator (&) to run the **Clear-Variable** command in a new scope.</span></span>
<span data-ttu-id="5fa43-118">Variabeln har rensats i det underordnade omfånget (även om den inte finns), men den har inte rensats i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="5fa43-118">The variable is cleared in the child scope (although it did not exist), but it is not cleared in the local scope.</span></span>
<span data-ttu-id="5fa43-119">Det tredje kommandot, som hämtar värdet för $A, visar att värdet 3 inte påverkas.</span><span class="sxs-lookup"><span data-stu-id="5fa43-119">The third command, which gets the value of $A, shows that the value 3 is unaffected.</span></span>

### <span data-ttu-id="5fa43-120">Exempel 3: ta bort värdet för den angivna variabeln</span><span class="sxs-lookup"><span data-stu-id="5fa43-120">Example 3: Delete the value of the specified variable</span></span>

```
PS C:\> Clear-Variable -Name "Processes"
```

<span data-ttu-id="5fa43-121">Det här kommandot tar bort värdet för variabeln med namnet processs.</span><span class="sxs-lookup"><span data-stu-id="5fa43-121">This command deletes the value of the variable named Processes.</span></span>
<span data-ttu-id="5fa43-122">När cmdleten har slutfört åtgärden finns variabeln som heter processer fortfarande, men värdet är null.</span><span class="sxs-lookup"><span data-stu-id="5fa43-122">After the cmdlet completes the operation, the variable named Processes still exists, but the value is null.</span></span>

## <span data-ttu-id="5fa43-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5fa43-123">PARAMETERS</span></span>

### <span data-ttu-id="5fa43-124">-Undanta</span><span class="sxs-lookup"><span data-stu-id="5fa43-124">-Exclude</span></span>

<span data-ttu-id="5fa43-125">Anger en matris med objekt som denna cmdlet utelämnar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5fa43-125">Specifies an array of items that this cmdlet omits in the operation.</span></span>
<span data-ttu-id="5fa43-126">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="5fa43-126">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="5fa43-127">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="5fa43-127">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="5fa43-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5fa43-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="5fa43-129">-Force</span><span class="sxs-lookup"><span data-stu-id="5fa43-129">-Force</span></span>

<span data-ttu-id="5fa43-130">Tillåter cmdleten att ta bort en variabel även om den är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="5fa43-130">Allows the cmdlet to clear a variable even if it is read-only.</span></span>
<span data-ttu-id="5fa43-131">Cmdleten kan inte ta bort konstanter även om du använder Force-parametern.</span><span class="sxs-lookup"><span data-stu-id="5fa43-131">Even using the Force parameter, the cmdlet cannot clear constants.</span></span>

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

### <span data-ttu-id="5fa43-132">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="5fa43-132">-Include</span></span>

<span data-ttu-id="5fa43-133">Anger en matris med objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="5fa43-133">Specifies an array of items that this cmdlet includes in the operation.</span></span>
<span data-ttu-id="5fa43-134">Värdet för den här parametern kvalificerar parametern *Name* .</span><span class="sxs-lookup"><span data-stu-id="5fa43-134">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="5fa43-135">Ange ett namn element eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="5fa43-135">Enter a name element or pattern, such as "s\*".</span></span>
<span data-ttu-id="5fa43-136">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5fa43-136">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="5fa43-137">-Name</span><span class="sxs-lookup"><span data-stu-id="5fa43-137">-Name</span></span>

<span data-ttu-id="5fa43-138">Anger namnet på den variabel som ska rensas.</span><span class="sxs-lookup"><span data-stu-id="5fa43-138">Specifies the name of the variable to be cleared.</span></span>
<span data-ttu-id="5fa43-139">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5fa43-139">Wildcards are permitted.</span></span>
<span data-ttu-id="5fa43-140">Den här parametern är obligatorisk, men parameter namnet ("name") är valfritt.</span><span class="sxs-lookup"><span data-stu-id="5fa43-140">This parameter is required, but the parameter name ("Name") is optional.</span></span>

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

### <span data-ttu-id="5fa43-141">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5fa43-141">-PassThru</span></span>

<span data-ttu-id="5fa43-142">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="5fa43-142">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="5fa43-143">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5fa43-143">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5fa43-144">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="5fa43-144">-Scope</span></span>

<span data-ttu-id="5fa43-145">Anger omfattningen som detta alias är giltigt i.</span><span class="sxs-lookup"><span data-stu-id="5fa43-145">Specifies the scope in which this alias is valid.</span></span>

<span data-ttu-id="5fa43-146">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5fa43-146">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5fa43-147">Global</span><span class="sxs-lookup"><span data-stu-id="5fa43-147">Global</span></span>
- <span data-ttu-id="5fa43-148">Lokal</span><span class="sxs-lookup"><span data-stu-id="5fa43-148">Local</span></span>
- <span data-ttu-id="5fa43-149">Skript</span><span class="sxs-lookup"><span data-stu-id="5fa43-149">Script</span></span>

<span data-ttu-id="5fa43-150">Du kan också använda ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).</span><span class="sxs-lookup"><span data-stu-id="5fa43-150">You can also use a number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent).</span></span>
<span data-ttu-id="5fa43-151">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="5fa43-151">Local is the default.</span></span>
<span data-ttu-id="5fa43-152">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="5fa43-152">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="5fa43-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5fa43-153">-Confirm</span></span>

<span data-ttu-id="5fa43-154">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5fa43-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5fa43-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5fa43-155">-WhatIf</span></span>

<span data-ttu-id="5fa43-156">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5fa43-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5fa43-157">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5fa43-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5fa43-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5fa43-158">CommonParameters</span></span>

<span data-ttu-id="5fa43-159">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5fa43-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5fa43-160">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5fa43-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5fa43-161">INDATA</span><span class="sxs-lookup"><span data-stu-id="5fa43-161">INPUTS</span></span>

### <span data-ttu-id="5fa43-162">Inget</span><span class="sxs-lookup"><span data-stu-id="5fa43-162">None</span></span>

<span data-ttu-id="5fa43-163">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5fa43-163">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="5fa43-164">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5fa43-164">OUTPUTS</span></span>

### <span data-ttu-id="5fa43-165">Ingen eller system. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="5fa43-165">None or System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="5fa43-166">När du använder parametern *Passthru* genererar denna cmdlet ett **system. Management. Automation. PSVariable** -objekt som representerar den rensade variabeln.</span><span class="sxs-lookup"><span data-stu-id="5fa43-166">When you use the *PassThru* parameter, this cmdlet generates a **System.Management.Automation.PSVariable** object representing the cleared variable.</span></span>
<span data-ttu-id="5fa43-167">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5fa43-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5fa43-168">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5fa43-168">NOTES</span></span>

* <span data-ttu-id="5fa43-169">Om du vill ta bort en variabel, tillsammans med dess värde, använder du Remove-Variable eller ta bort objekt.</span><span class="sxs-lookup"><span data-stu-id="5fa43-169">To delete a variable, along with its value, use Remove-Variable or Remove-Item.</span></span>

  <span data-ttu-id="5fa43-170">Den här cmdleten tar inte bort värdena för variabler som anges som konstanter eller ägs av systemet, även om du använder *Force* -parametern.</span><span class="sxs-lookup"><span data-stu-id="5fa43-170">This cmdlet does not delete the values of variables that are set as constants or owned by the system, even if you use the *Force* parameter.</span></span>

  <span data-ttu-id="5fa43-171">Om den variabel som du tar bort inte finns, har cmdleten ingen inverkan.</span><span class="sxs-lookup"><span data-stu-id="5fa43-171">If the variable that you are clearing does not exist, the cmdlet has no effect.</span></span>
<span data-ttu-id="5fa43-172">Den skapar inte en variabel med ett null-värde.</span><span class="sxs-lookup"><span data-stu-id="5fa43-172">It does not create a variable with a null value.</span></span>

  <span data-ttu-id="5fa43-173">Du kan också referera till **Clear-Variable** med dess inbyggda alias, CLV.</span><span class="sxs-lookup"><span data-stu-id="5fa43-173">You can also refer to **Clear-Variable** by its built-in alias, clv.</span></span>
<span data-ttu-id="5fa43-174">Mer information finns i about_Aliases.</span><span class="sxs-lookup"><span data-stu-id="5fa43-174">For more information, see about_Aliases.</span></span>

*

## <span data-ttu-id="5fa43-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5fa43-175">RELATED LINKS</span></span>

[<span data-ttu-id="5fa43-176">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="5fa43-176">Get-Variable</span></span>](Get-Variable.md)

[<span data-ttu-id="5fa43-177">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="5fa43-177">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="5fa43-178">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="5fa43-178">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="5fa43-179">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="5fa43-179">Set-Variable</span></span>](Set-Variable.md)
