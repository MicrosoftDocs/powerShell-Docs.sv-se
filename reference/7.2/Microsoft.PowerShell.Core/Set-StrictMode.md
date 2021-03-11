---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/10/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: 007c2cd044ac91a29b40f5a49e84482d7523d3ca
ms.sourcegitcommit: 925819a5ad5799650c14944bd3e50fb309a7e6c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/11/2021
ms.locfileid: "102771468"
---
# <span data-ttu-id="0460d-102">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="0460d-102">Set-StrictMode</span></span>

## <span data-ttu-id="0460d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0460d-103">SYNOPSIS</span></span>
<span data-ttu-id="0460d-104">Skapar och tillämpar kod regler i uttryck, skript och skript block.</span><span class="sxs-lookup"><span data-stu-id="0460d-104">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="0460d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0460d-105">SYNTAX</span></span>

### <span data-ttu-id="0460d-106">Version (standard)</span><span class="sxs-lookup"><span data-stu-id="0460d-106">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="0460d-107">Av</span><span class="sxs-lookup"><span data-stu-id="0460d-107">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="0460d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0460d-108">DESCRIPTION</span></span>

<span data-ttu-id="0460d-109">`Set-StrictMode`Cmdleten konfigurerar strikt läge för det aktuella omfånget och alla underordnade scope och aktiverar och inaktiverar den.</span><span class="sxs-lookup"><span data-stu-id="0460d-109">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="0460d-110">När strikt läge är på genererar PowerShell ett avslutande fel när innehållet i ett uttryck, skript eller skript block strider mot grundläggande kodnings regler för bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="0460d-110">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="0460d-111">Använd **versions** parametern för att avgöra vilka kodnings regler som tillämpas.</span><span class="sxs-lookup"><span data-stu-id="0460d-111">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="0460d-112">`Set-PSDebug -Strict` cmdlet aktiverar strikt läge för det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="0460d-112">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="0460d-113">`Set-StrictMode` påverkar endast det aktuella omfånget och dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="0460d-113">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="0460d-114">Därför kan du använda den i ett skript eller en funktion för att åsidosätta inställningen som ärvts från det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="0460d-114">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="0460d-115">När `Set-StrictMode` är inaktiverat har PowerShell följande beteenden:</span><span class="sxs-lookup"><span data-stu-id="0460d-115">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="0460d-116">Oinitierade variabler antas ha värdet 0 (noll) eller `$Null` , beroende på typ</span><span class="sxs-lookup"><span data-stu-id="0460d-116">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="0460d-117">Referenser till obefintliga egenskaper returnerar `$Null`</span><span class="sxs-lookup"><span data-stu-id="0460d-117">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="0460d-118">Resultatet av felaktig syntax i funktionen varierar med fel villkoren</span><span class="sxs-lookup"><span data-stu-id="0460d-118">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="0460d-119">Försök att hämta ett värde med ett ogiltigt index i en matris returneras `$Null`</span><span class="sxs-lookup"><span data-stu-id="0460d-119">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="0460d-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0460d-120">EXAMPLES</span></span>

### <span data-ttu-id="0460d-121">Exempel 1: Aktivera strikt läge som version 1,0</span><span class="sxs-lookup"><span data-stu-id="0460d-121">Example 1: Turn on strict mode as version 1.0</span></span>

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
InvalidOperation: The variable '$a' cannot be retrieved because it has not been set.
```

<span data-ttu-id="0460d-122">Med strikt läge inställt på version 1,0, försöker referera till variabler som inte initieras.</span><span class="sxs-lookup"><span data-stu-id="0460d-122">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="0460d-123">Exempel 2: Aktivera strikt läge som version 2,0</span><span class="sxs-lookup"><span data-stu-id="0460d-123">Example 2: Turn on strict mode as version 2.0</span></span>

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
InvalidOperation: The function or command was called as if it were a method. Parameters should be separated by spaces. For information about parameters, see the about_Parameters Help topic.
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$null -eq $string.Month
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$null -eq $string.Month
```

```Output
PropertyNotFoundException: The property 'Month' cannot be found on this object. Verify that the property exists.
```

<span data-ttu-id="0460d-124">Det här kommandot aktiverar strikt läge på och anger det till version 2,0.</span><span class="sxs-lookup"><span data-stu-id="0460d-124">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="0460d-125">Det innebär att PowerShell returnerar ett fel om du använder Method syntax, som använder parenteser och kommatecken, för ett funktions anrop eller referera till oinitierade variabler eller obefintliga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="0460d-125">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="0460d-126">Exempel resultatet visar effekterna av strikt läge för version 2,0.</span><span class="sxs-lookup"><span data-stu-id="0460d-126">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="0460d-127">Utan version 2,0 strikt läge tolkas "(3, 4)"-värdet som ett enskilt Array-objekt som inget läggs till i.</span><span class="sxs-lookup"><span data-stu-id="0460d-127">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="0460d-128">Genom att använda version 2,0 strikt läge tolkas det korrekt som felaktig syntax för att skicka två värden.</span><span class="sxs-lookup"><span data-stu-id="0460d-128">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="0460d-129">Utan version 2,0 returnerar referensen till den icke-befintliga **månads** egenskapen för en sträng `$Null` .</span><span class="sxs-lookup"><span data-stu-id="0460d-129">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="0460d-130">Genom att använda version 2,0 tolkas den korrekt som ett referens fel.</span><span class="sxs-lookup"><span data-stu-id="0460d-130">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="0460d-131">Exempel 3: Aktivera strikt läge som version 3,0</span><span class="sxs-lookup"><span data-stu-id="0460d-131">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="0460d-132">Med strikt läge inställt på **av**, ogiltigt eller utanför intervall index resulterar resultatet av null-värden.</span><span class="sxs-lookup"><span data-stu-id="0460d-132">With strict mode set to **Off**, invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$null -eq $a[2]
$null -eq $a['abc']
```

```Output
OperationStopped: Index was outside the bounds of the array.

InvalidArgument: Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
```

<span data-ttu-id="0460d-133">Med strikt läge inställt på version 3 eller högre, är ogiltiga eller utanför gräns index resulterar i fel.</span><span class="sxs-lookup"><span data-stu-id="0460d-133">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="0460d-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0460d-134">PARAMETERS</span></span>

### <span data-ttu-id="0460d-135">-Av</span><span class="sxs-lookup"><span data-stu-id="0460d-135">-Off</span></span>

<span data-ttu-id="0460d-136">Anger att den här cmdleten inaktiverar strikt läge för det aktuella omfånget och alla underordnade scope.</span><span class="sxs-lookup"><span data-stu-id="0460d-136">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0460d-137">-Version</span><span class="sxs-lookup"><span data-stu-id="0460d-137">-Version</span></span>

<span data-ttu-id="0460d-138">Anger de villkor som orsakar ett fel i strikt läge.</span><span class="sxs-lookup"><span data-stu-id="0460d-138">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="0460d-139">Den här parametern accepterar ett giltigt PowerShell-versions nummer.</span><span class="sxs-lookup"><span data-stu-id="0460d-139">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="0460d-140">Alla tal som är större än 3 behandlas som **senaste**.</span><span class="sxs-lookup"><span data-stu-id="0460d-140">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="0460d-141">De effektiva värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="0460d-141">The effective values for this parameter are:</span></span>

- <span data-ttu-id="0460d-142">1.0</span><span class="sxs-lookup"><span data-stu-id="0460d-142">1.0</span></span>
  - <span data-ttu-id="0460d-143">Förhindrar referenser till oinitierade variabler, förutom oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="0460d-143">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="0460d-144">2.0</span><span class="sxs-lookup"><span data-stu-id="0460d-144">2.0</span></span>
  - <span data-ttu-id="0460d-145">Förhindrar referenser till oinitierade variabler.</span><span class="sxs-lookup"><span data-stu-id="0460d-145">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="0460d-146">Detta inkluderar oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="0460d-146">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="0460d-147">Förhindrar referenser till obefintliga egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="0460d-147">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="0460d-148">Förhindrar funktions anrop som använder syntaxen för att anropa metoder.</span><span class="sxs-lookup"><span data-stu-id="0460d-148">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="0460d-149">3.0</span><span class="sxs-lookup"><span data-stu-id="0460d-149">3.0</span></span>
  - <span data-ttu-id="0460d-150">Förhindrar referenser till oinitierade variabler.</span><span class="sxs-lookup"><span data-stu-id="0460d-150">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="0460d-151">Detta inkluderar oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="0460d-151">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="0460d-152">Förhindrar referenser till obefintliga egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="0460d-152">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="0460d-153">Förhindrar funktions anrop som använder syntaxen för att anropa metoder.</span><span class="sxs-lookup"><span data-stu-id="0460d-153">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="0460d-154">Förhindra att matriser utanför gränser eller inte går att matcha.</span><span class="sxs-lookup"><span data-stu-id="0460d-154">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="0460d-155">Senast</span><span class="sxs-lookup"><span data-stu-id="0460d-155">Latest</span></span>
  - <span data-ttu-id="0460d-156">Väljer den senaste versionen som är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="0460d-156">Selects the latest version available.</span></span> <span data-ttu-id="0460d-157">Den senaste versionen är den mest strikta.</span><span class="sxs-lookup"><span data-stu-id="0460d-157">The latest version is the most strict.</span></span> <span data-ttu-id="0460d-158">Använd det här värdet för att kontrol lera att skript använder den striktaste tillgängliga versionen, även när nya versioner läggs till i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0460d-158">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="0460d-159">Använda en **version** av de **senaste** i skripten.</span><span class="sxs-lookup"><span data-stu-id="0460d-159">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="0460d-160">Betydelsen av **senaste** kan ändra i nya versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0460d-160">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="0460d-161">Ett skript som skrivits för en äldre version av PowerShell som använder omfattas därför av `Set-StrictMode -Version Latest` mer restriktiva regler när de körs i en senare version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0460d-161">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0460d-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0460d-162">CommonParameters</span></span>

<span data-ttu-id="0460d-163">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0460d-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0460d-164">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0460d-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0460d-165">INDATA</span><span class="sxs-lookup"><span data-stu-id="0460d-165">INPUTS</span></span>

### <span data-ttu-id="0460d-166">Inget</span><span class="sxs-lookup"><span data-stu-id="0460d-166">None</span></span>

<span data-ttu-id="0460d-167">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0460d-167">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0460d-168">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0460d-168">OUTPUTS</span></span>

### <span data-ttu-id="0460d-169">Inget</span><span class="sxs-lookup"><span data-stu-id="0460d-169">None</span></span>

<span data-ttu-id="0460d-170">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0460d-170">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="0460d-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0460d-171">NOTES</span></span>

<span data-ttu-id="0460d-172">Medan `Set-StrictMode` **versions** parametern accepterar värden som är större än `3.0` , finns det inga ytterligare regler definierade för något högre än `3.0` .</span><span class="sxs-lookup"><span data-stu-id="0460d-172">While `Set-StrictMode` **Version** parameter will accept values greater than `3.0`, currently there are no additional rules defined for anything higher than `3.0`.</span></span>

<span data-ttu-id="0460d-173">`Set-StrictMode` är endast effektivt i det omfång där det har angetts och i dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="0460d-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="0460d-174">Mer information om omfång i PowerShell finns [about_Scopes](about/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="0460d-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="0460d-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0460d-175">RELATED LINKS</span></span>

[<span data-ttu-id="0460d-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="0460d-176">Set-PSDebug</span></span>](Set-PSDebug.md)
