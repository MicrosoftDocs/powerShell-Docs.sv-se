---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: f544a33a4d2aa2cabd330ce7cc30c5270eeff897
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264339"
---
# <span data-ttu-id="41cc3-103">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="41cc3-103">Get-Variable</span></span>

## <span data-ttu-id="41cc3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="41cc3-104">SYNOPSIS</span></span>
<span data-ttu-id="41cc3-105">Hämtar variablerna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="41cc3-105">Gets the variables in the current console.</span></span>

## <span data-ttu-id="41cc3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41cc3-106">SYNTAX</span></span>

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="41cc3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="41cc3-107">DESCRIPTION</span></span>

<span data-ttu-id="41cc3-108">`Get-Variable`Cmdlet: en hämtar PowerShell-variablerna i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="41cc3-108">The `Get-Variable` cmdlet gets the PowerShell variables in the current console.</span></span>
<span data-ttu-id="41cc3-109">Du kan bara hämta värdena för variablerna genom att ange parametern **ValueOnly** , och du kan filtrera variablerna som returneras efter namn.</span><span class="sxs-lookup"><span data-stu-id="41cc3-109">You can retrieve just the values of the variables by specifying the **ValueOnly** parameter, and you can filter the variables returned by name.</span></span>

## <span data-ttu-id="41cc3-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="41cc3-110">EXAMPLES</span></span>

### <span data-ttu-id="41cc3-111">Exempel 1: Hämta variabler per bokstav</span><span class="sxs-lookup"><span data-stu-id="41cc3-111">Example 1: Get variables by letter</span></span>

<span data-ttu-id="41cc3-112">Det här kommandot hämtar variabler med namn som börjar med bokstaven m.</span><span class="sxs-lookup"><span data-stu-id="41cc3-112">This command gets variables with names that begin with the letter m.</span></span>
<span data-ttu-id="41cc3-113">Kommandot hämtar också variablernas värde.</span><span class="sxs-lookup"><span data-stu-id="41cc3-113">The command also gets the value of the variables.</span></span>

```powershell
Get-Variable m*
```

### <span data-ttu-id="41cc3-114">Exempel 2: Hämta variabel värden efter bokstav</span><span class="sxs-lookup"><span data-stu-id="41cc3-114">Example 2: Get variable values by letter</span></span>

<span data-ttu-id="41cc3-115">Det här kommandot hämtar bara värdena för variabler som har namn som börjar med m.</span><span class="sxs-lookup"><span data-stu-id="41cc3-115">This command gets only the values of the variables that have names that begin with m.</span></span>

```powershell
Get-Variable m* -ValueOnly
```

### <span data-ttu-id="41cc3-116">Exempel 3: Hämta variabler med två bokstäver</span><span class="sxs-lookup"><span data-stu-id="41cc3-116">Example 3: Get variables by two letters</span></span>

<span data-ttu-id="41cc3-117">Det här kommandot hämtar information om variablerna som börjar med bokstaven M eller bokstaven P.</span><span class="sxs-lookup"><span data-stu-id="41cc3-117">This command gets information about the variables that begin with either the letter M or the letter P.</span></span>

```powershell
Get-Variable -Include M*,P*
```

### <span data-ttu-id="41cc3-118">Exempel 4: Hämta variabler efter omfång</span><span class="sxs-lookup"><span data-stu-id="41cc3-118">Example 4: Get variables by scope</span></span>

<span data-ttu-id="41cc3-119">Det första kommandot hämtar bara de variabler som har definierats i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="41cc3-119">The first command gets only the variables that are defined in the local scope.</span></span>
<span data-ttu-id="41cc3-120">Det motsvarar `Get-Variable -Scope Local` och kan förkortas som `gv -s 0` .</span><span class="sxs-lookup"><span data-stu-id="41cc3-120">It is equivalent to `Get-Variable -Scope Local` and can be abbreviated as `gv -s 0`.</span></span>

<span data-ttu-id="41cc3-121">Det andra kommandot använder `Compare-Object` cmdleten för att hitta variablerna som har definierats i det överordnade omfånget (område 1), men är bara synliga i det lokala omfånget (omfånget 0).</span><span class="sxs-lookup"><span data-stu-id="41cc3-121">The second command uses the `Compare-Object` cmdlet to find the variables that are defined in the parent scope (Scope 1) but are visible only in the local scope (Scope 0).</span></span>

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## <span data-ttu-id="41cc3-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="41cc3-122">PARAMETERS</span></span>

### <span data-ttu-id="41cc3-123">-Undanta</span><span class="sxs-lookup"><span data-stu-id="41cc3-123">-Exclude</span></span>

<span data-ttu-id="41cc3-124">Anger en matris med objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="41cc3-124">Specifies an array of items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="41cc3-125">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41cc3-125">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="41cc3-126">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="41cc3-126">-Include</span></span>

<span data-ttu-id="41cc3-127">Anger en matris med objekt som cmdleten ska fungera på, förutom alla andra.</span><span class="sxs-lookup"><span data-stu-id="41cc3-127">Specifies an array of items upon which the cmdlet will act, excluding all others.</span></span>
<span data-ttu-id="41cc3-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41cc3-128">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="41cc3-129">-Name</span><span class="sxs-lookup"><span data-stu-id="41cc3-129">-Name</span></span>

<span data-ttu-id="41cc3-130">Anger namnet på variabeln.</span><span class="sxs-lookup"><span data-stu-id="41cc3-130">Specifies the name of the variable.</span></span>
<span data-ttu-id="41cc3-131">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="41cc3-131">Wildcards are permitted.</span></span>
<span data-ttu-id="41cc3-132">Du kan också skicka ett variabel namn till `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="41cc3-132">You can also pipe a variable name to `Get-Variable`.</span></span>

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

### <span data-ttu-id="41cc3-133">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="41cc3-133">-Scope</span></span>

<span data-ttu-id="41cc3-134">Anger variablerna i omfånget. De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="41cc3-134">Specifies the variables in the scope.The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41cc3-135">**Global**</span><span class="sxs-lookup"><span data-stu-id="41cc3-135">**Global**</span></span>
- <span data-ttu-id="41cc3-136">**Inställningar**</span><span class="sxs-lookup"><span data-stu-id="41cc3-136">**Local**</span></span>
- <span data-ttu-id="41cc3-137">**Över**</span><span class="sxs-lookup"><span data-stu-id="41cc3-137">**Script**</span></span>
- <span data-ttu-id="41cc3-138">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="41cc3-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="41cc3-139">**Lokalt** är standard.</span><span class="sxs-lookup"><span data-stu-id="41cc3-139">**Local** is the default.</span></span>
<span data-ttu-id="41cc3-140">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="41cc3-140">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

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

### <span data-ttu-id="41cc3-141">-ValueOnly</span><span class="sxs-lookup"><span data-stu-id="41cc3-141">-ValueOnly</span></span>

<span data-ttu-id="41cc3-142">Anger att denna cmdlet endast hämtar värdet för variabeln.</span><span class="sxs-lookup"><span data-stu-id="41cc3-142">Indicates that this cmdlet gets only the value of the variable.</span></span>

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

### <span data-ttu-id="41cc3-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41cc3-143">CommonParameters</span></span>

<span data-ttu-id="41cc3-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41cc3-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41cc3-145">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="41cc3-145">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="41cc3-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="41cc3-146">INPUTS</span></span>

### <span data-ttu-id="41cc3-147">System. String</span><span class="sxs-lookup"><span data-stu-id="41cc3-147">System.String</span></span>

<span data-ttu-id="41cc3-148">Du kan skicka vidare en sträng som innehåller variabel namnet till `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="41cc3-148">You can pipe a string that contains the variable name to `Get-Variable`.</span></span>

## <span data-ttu-id="41cc3-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="41cc3-149">OUTPUTS</span></span>

### <span data-ttu-id="41cc3-150">System. Management. Automation. PSVariable</span><span class="sxs-lookup"><span data-stu-id="41cc3-150">System.Management.Automation.PSVariable</span></span>

<span data-ttu-id="41cc3-151">Denna cmdlet returnerar ett **system. Management. AutomationPSVariable** -objekt för varje variabel som det får.</span><span class="sxs-lookup"><span data-stu-id="41cc3-151">This cmdlet returns a **System.Management.AutomationPSVariable** object for each variable that it gets.</span></span> <span data-ttu-id="41cc3-152">Objekt typen är beroende av variabeln.</span><span class="sxs-lookup"><span data-stu-id="41cc3-152">The object type depends on the variable.</span></span>

### <span data-ttu-id="41cc3-153">System. Object []</span><span class="sxs-lookup"><span data-stu-id="41cc3-153">System.Object[]</span></span>

<span data-ttu-id="41cc3-154">När du anger parametern **ValueOnly** , om den angivna variabelns värde är en samling, `Get-Variable` returnerar en `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="41cc3-154">When you specify the **ValueOnly** parameter, if the specified variable's value is a collection, `Get-Variable` returns a `[System.Object[]]`.</span></span> <span data-ttu-id="41cc3-155">Det här beteendet förhindrar normal pipeline-åtgärd från att bearbeta variabelns värden en i taget.</span><span class="sxs-lookup"><span data-stu-id="41cc3-155">This behavior prevents normal pipeline operation from processing the variable's values one at a time.</span></span> <span data-ttu-id="41cc3-156">En lösning för att tvinga samlings uppräkning är att omge `Get-Variable` kommandot med parentes.</span><span class="sxs-lookup"><span data-stu-id="41cc3-156">A workaround to force collection enumeration is to enclose the `Get-Variable` command in parenthesis.</span></span>

## <span data-ttu-id="41cc3-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="41cc3-157">NOTES</span></span>

- <span data-ttu-id="41cc3-158">Denna cmdlet hanterar inte miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="41cc3-158">This cmdlet does not manage environment variables.</span></span> <span data-ttu-id="41cc3-159">Om du vill hantera miljövariabler kan du använda miljövariabeln Provider.</span><span class="sxs-lookup"><span data-stu-id="41cc3-159">To manage environment variables, you can use the environment variable provider.</span></span>

## <span data-ttu-id="41cc3-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="41cc3-160">RELATED LINKS</span></span>

[<span data-ttu-id="41cc3-161">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="41cc3-161">Clear-Variable</span></span>](Clear-Variable.md)

[<span data-ttu-id="41cc3-162">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="41cc3-162">New-Variable</span></span>](New-Variable.md)

[<span data-ttu-id="41cc3-163">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="41cc3-163">Remove-Variable</span></span>](Remove-Variable.md)

[<span data-ttu-id="41cc3-164">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="41cc3-164">Set-Variable</span></span>](Set-Variable.md)

