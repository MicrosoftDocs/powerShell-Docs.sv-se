---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 6cd7a4611f6118ed1f0846d9c11a8fe8edc69ef0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709091"
---
# <span data-ttu-id="4811b-102">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="4811b-102">Get-Variable</span></span>

## <span data-ttu-id="4811b-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4811b-103">SYNOPSIS</span></span>
<span data-ttu-id="4811b-104">Hämtar variablerna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="4811b-104">Gets the variables in the current console.</span></span>

## <span data-ttu-id="4811b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4811b-105">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="4811b-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4811b-106">DESCRIPTION</span></span>

<span data-ttu-id="4811b-107">`Get-Variable`Cmdlet: en hämtar PowerShell-variablerna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="4811b-107">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="4811b-108">Du kan bara hämta värdena för variablerna genom att ange parametern **ValueOnly** , och du kan filtrera variablerna som returneras efter namn.</span><span class="sxs-lookup"><span data-stu-id="4811b-108">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="4811b-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4811b-109">EXAMPLES</span></span>

### <span data-ttu-id="4811b-110">Exempel 1: Hämta variabler per bokstav</span><span class="sxs-lookup"><span data-stu-id="4811b-110">Example 1: Get variables by letter</span></span>

<span data-ttu-id="4811b-111">Det här kommandot hämtar variabler med namn som börjar med bokstaven m.</span><span class="sxs-lookup"><span data-stu-id="4811b-111">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="4811b-112">Kommandot hämtar också variablernas värde.</span><span class="sxs-lookup"><span data-stu-id="4811b-112">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="4811b-113">Exempel 2: Hämta variabel värden efter bokstav</span><span class="sxs-lookup"><span data-stu-id="4811b-113">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="4811b-114">Det här kommandot hämtar bara värdena för variabler som har namn som börjar med m.</span><span class="sxs-lookup"><span data-stu-id="4811b-114">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="4811b-115">Exempel 3: Hämta variabler med två bokstäver</span><span class="sxs-lookup"><span data-stu-id="4811b-115">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="4811b-116">Det här kommandot hämtar information om variablerna som börjar med bokstaven M eller bokstaven P.</span><span class="sxs-lookup"><span data-stu-id="4811b-116">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="4811b-117">Exempel 4: Hämta variabler efter omfång</span><span class="sxs-lookup"><span data-stu-id="4811b-117">Example 4: Get variables by scope</span></span>

<span data-ttu-id="4811b-118">Det första kommandot hämtar bara de variabler som har definierats i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="4811b-118">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="4811b-119">Det motsvarar `Get-Variable -Scope Local` och kan förkortas som `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="4811b-119">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="4811b-120">Det andra kommandot använder `Compare-Object` cmdleten för att hitta variablerna som har definierats i det överordnade omfånget (område 1), men är bara synliga i det lokala omfånget (omfånget 0).</span><span class="sxs-lookup"><span data-stu-id="4811b-120">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="4811b-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4811b-121">PARAMETERS</span></span>

### <span data-ttu-id="4811b-122">-Undanta</span><span class="sxs-lookup"><span data-stu-id="4811b-122">-Exclude</span></span>

<span data-ttu-id="4811b-123">Anger en matris med objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4811b-123">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="4811b-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4811b-124">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4811b-125">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="4811b-125">-Include</span></span>

<span data-ttu-id="4811b-126">Anger en matris med objekt som cmdleten ska fungera på, förutom alla andra.</span><span class="sxs-lookup"><span data-stu-id="4811b-126">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="4811b-127">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4811b-127">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="4811b-128">-Name</span><span class="sxs-lookup"><span data-stu-id="4811b-128">-Name</span></span>

<span data-ttu-id="4811b-129">Anger namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="4811b-129">Specifies the name of the variable.</span></span>
<span data-ttu-id="4811b-130">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="4811b-130">Wildcards are permitted.</span></span>
<span data-ttu-id="4811b-131">Du kan också skicka ett variabel namn till `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="4811b-131">You can also pipe a variable name to `Get-Variable`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="4811b-132">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="4811b-132">-Scope</span></span>

<span data-ttu-id="4811b-133">Anger variablerna i omfånget. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4811b-133">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4811b-134">**Global**</span><span class="sxs-lookup"><span data-stu-id="4811b-134">**Global**</span></span>
- <span data-ttu-id="4811b-135">**Inställningar**</span><span class="sxs-lookup"><span data-stu-id="4811b-135">**Local**</span></span>
- <span data-ttu-id="4811b-136">**Över**</span><span class="sxs-lookup"><span data-stu-id="4811b-136">**Script**</span></span>
- <span data-ttu-id="4811b-137">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="4811b-137">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="4811b-138">**Lokalt** är standard.</span><span class="sxs-lookup"><span data-stu-id="4811b-138">**Local** is the default.</span></span>
<span data-ttu-id="4811b-139">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="4811b-139">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="4811b-140">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="4811b-140">-ValueOnly</span></span>

<span data-ttu-id="4811b-141">Anger att denna cmdlet endast hämtar värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="4811b-141">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="4811b-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4811b-142">CommonParameters</span></span>

<span data-ttu-id="4811b-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4811b-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4811b-144">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="4811b-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="4811b-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="4811b-145">INPUTS</span></span>

### <span data-ttu-id="4811b-146">System. String</span><span class="sxs-lookup"><span data-stu-id="4811b-146">System.String</span></span>

<span data-ttu-id="4811b-147">Du kan skicka vidare en sträng som innehåller variabel namnet till `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="4811b-147">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="4811b-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4811b-148">OUTPUTS</span></span>

### <span data-ttu-id="4811b-149">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="4811b-149">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="4811b-150">Denna cmdlet returnerar ett **system. Management. AutomationPSVariable** -objekt för varje variabel som det får.</span><span class="sxs-lookup"><span data-stu-id="4811b-150">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="4811b-151">Objekt typen är beroende av variabeln.</span><span class="sxs-lookup"><span data-stu-id="4811b-151">The object type depends on the variable.</span></span>

### <span data-ttu-id="4811b-152">System. Object []</span><span class="sxs-lookup"><span data-stu-id="4811b-152">System.Object[]</span></span>

<span data-ttu-id="4811b-153">När du anger parametern **ValueOnly** , om den angivna variabelns värde är en samling, `Get-Variable` returnerar en `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="4811b-153">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="4811b-154">Det här beteendet förhindrar normal pipeline-åtgärd från att bearbeta variabelns värden en i taget.</span><span class="sxs-lookup"><span data-stu-id="4811b-154">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="4811b-155">En lösning för att tvinga samlings uppräkning är att omge `Get-Variable` kommandot med parentes.</span><span class="sxs-lookup"><span data-stu-id="4811b-155">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="4811b-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4811b-156">NOTES</span></span>

- <span data-ttu-id="4811b-157">Denna cmdlet hanterar inte miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="4811b-157">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="4811b-158">Om du vill hantera miljövariabler kan du använda miljövariabeln Provider.</span><span class="sxs-lookup"><span data-stu-id="4811b-158">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="4811b-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4811b-159">RELATED LINKS</span></span>

[<span data-ttu-id="4811b-160">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="4811b-160">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="4811b-161">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="4811b-161">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="4811b-162">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="4811b-162">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="4811b-163">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="4811b-163">Set-Variable</span></span>](Set-Variable.md)

