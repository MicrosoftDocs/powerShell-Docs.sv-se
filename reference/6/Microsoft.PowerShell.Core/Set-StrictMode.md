---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: d28ff57c864847658072c9b7a1979b2b513c04b3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267417"
---
# <span data-ttu-id="2fabe-103">Set-StrictMode</span><span class="sxs-lookup"><span data-stu-id="2fabe-103">Set-StrictMode</span></span>

## <span data-ttu-id="2fabe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2fabe-104">SYNOPSIS</span></span>
<span data-ttu-id="2fabe-105">Skapar och tillämpar kod regler i uttryck, skript och skript block.</span><span class="sxs-lookup"><span data-stu-id="2fabe-105">Establishes and enforces coding rules in expressions, scripts, and script blocks.</span></span>

## <span data-ttu-id="2fabe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2fabe-106">SYNTAX</span></span>

### <span data-ttu-id="2fabe-107">Version (standard)</span><span class="sxs-lookup"><span data-stu-id="2fabe-107">Version (Default)</span></span>

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### <span data-ttu-id="2fabe-108">Av</span><span class="sxs-lookup"><span data-stu-id="2fabe-108">Off</span></span>

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## <span data-ttu-id="2fabe-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2fabe-109">DESCRIPTION</span></span>

<span data-ttu-id="2fabe-110">`Set-StrictMode`Cmdleten konfigurerar strikt läge för det aktuella omfånget och alla underordnade scope och aktiverar och inaktiverar den.</span><span class="sxs-lookup"><span data-stu-id="2fabe-110">The `Set-StrictMode` cmdlet configures strict mode for the current scope and all child scopes, and turns it on and off.</span></span> <span data-ttu-id="2fabe-111">När strikt läge är på genererar PowerShell ett avslutande fel när innehållet i ett uttryck, skript eller skript block strider mot grundläggande kodnings regler för bästa praxis.</span><span class="sxs-lookup"><span data-stu-id="2fabe-111">When strict mode is on, PowerShell generates a terminating error when the content of an expression, script, or script block violates basic best-practice coding rules.</span></span>

<span data-ttu-id="2fabe-112">Använd **versions** parametern för att avgöra vilka kodnings regler som tillämpas.</span><span class="sxs-lookup"><span data-stu-id="2fabe-112">Use the **Version** parameter to determine which coding rules are enforced.</span></span>

<span data-ttu-id="2fabe-113">`Set-PSDebug -Strict` cmdlet aktiverar strikt läge för det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2fabe-113">`Set-PSDebug -Strict` cmdlet turns on strict mode for the global scope.</span></span> <span data-ttu-id="2fabe-114">`Set-StrictMode` påverkar endast det aktuella omfånget och dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="2fabe-114">`Set-StrictMode` affects only the current scope and its child scopes.</span></span> <span data-ttu-id="2fabe-115">Därför kan du använda den i ett skript eller en funktion för att åsidosätta inställningen som ärvts från det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2fabe-115">Therefore, you can use it in a script or function to override the setting inherited from the global scope.</span></span>

<span data-ttu-id="2fabe-116">När `Set-StrictMode` är inaktiverat har PowerShell följande beteenden:</span><span class="sxs-lookup"><span data-stu-id="2fabe-116">When `Set-StrictMode` is off, PowerShell has the following behaviors:</span></span>

- <span data-ttu-id="2fabe-117">Oinitierade variabler antas ha värdet 0 (noll) eller `$Null` , beroende på typ</span><span class="sxs-lookup"><span data-stu-id="2fabe-117">Uninitialized variables are assumed to have a value of 0 (zero) or `$Null`, depending on type</span></span>
- <span data-ttu-id="2fabe-118">Referenser till obefintliga egenskaper returnerar `$Null`</span><span class="sxs-lookup"><span data-stu-id="2fabe-118">References to non-existent properties return `$Null`</span></span>
- <span data-ttu-id="2fabe-119">Resultatet av felaktig syntax i funktionen varierar med fel villkoren</span><span class="sxs-lookup"><span data-stu-id="2fabe-119">Results of improper function syntax vary with the error conditions</span></span>
- <span data-ttu-id="2fabe-120">Försök att hämta ett värde med ett ogiltigt index i en matris returneras `$Null`</span><span class="sxs-lookup"><span data-stu-id="2fabe-120">Attempting to retrieve a value using an invalid index in an array returns `$Null`</span></span>

## <span data-ttu-id="2fabe-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2fabe-121">EXAMPLES</span></span>

### <span data-ttu-id="2fabe-122">Exempel 1: Aktivera strikt läge som version 1,0</span><span class="sxs-lookup"><span data-stu-id="2fabe-122">Example 1: Turn on strict mode as version 1.0</span></span>

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
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

<span data-ttu-id="2fabe-123">Med strikt läge inställt på version 1,0, försöker referera till variabler som inte initieras.</span><span class="sxs-lookup"><span data-stu-id="2fabe-123">With strict mode set to version 1.0, attempts to reference variables that are not initialized fail.</span></span>

### <span data-ttu-id="2fabe-124">Exempel 2: Aktivera strikt läge som version 2,0</span><span class="sxs-lookup"><span data-stu-id="2fabe-124">Example 2: Turn on strict mode as version 2.0</span></span>

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
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

<span data-ttu-id="2fabe-125">Det här kommandot aktiverar strikt läge på och anger det till version 2,0.</span><span class="sxs-lookup"><span data-stu-id="2fabe-125">This command turns strict mode on and sets it to version 2.0.</span></span> <span data-ttu-id="2fabe-126">Det innebär att PowerShell returnerar ett fel om du använder Method syntax, som använder parenteser och kommatecken, för ett funktions anrop eller referera till oinitierade variabler eller obefintliga egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2fabe-126">As a result, PowerShell returns an error if you use method syntax, which uses parentheses and commas, for a function call or reference uninitialized variables or non-existent properties.</span></span>

<span data-ttu-id="2fabe-127">Exempel resultatet visar effekterna av strikt läge för version 2,0.</span><span class="sxs-lookup"><span data-stu-id="2fabe-127">The sample output shows the effect of version 2.0 strict mode.</span></span>

<span data-ttu-id="2fabe-128">Utan version 2,0 strikt läge tolkas "(3, 4)"-värdet som ett enskilt Array-objekt som inget läggs till i.</span><span class="sxs-lookup"><span data-stu-id="2fabe-128">Without version 2.0 strict mode, the "(3,4)" value is interpreted as a single array object to which nothing is added.</span></span> <span data-ttu-id="2fabe-129">Genom att använda version 2,0 strikt läge tolkas det korrekt som felaktig syntax för att skicka två värden.</span><span class="sxs-lookup"><span data-stu-id="2fabe-129">By using version 2.0 strict mode, it is correctly interpreted as faulty syntax for submitting two values.</span></span>

<span data-ttu-id="2fabe-130">Utan version 2,0 returnerar referensen till den icke-befintliga **månads** egenskapen för en sträng `$Null` .</span><span class="sxs-lookup"><span data-stu-id="2fabe-130">Without version 2.0, the reference to the non-existent **Month** property of a string returns only `$Null`.</span></span> <span data-ttu-id="2fabe-131">Genom att använda version 2,0 tolkas den korrekt som ett referens fel.</span><span class="sxs-lookup"><span data-stu-id="2fabe-131">By using version 2.0, it is interpreted correctly as a reference error.</span></span>

### <span data-ttu-id="2fabe-132">Exempel 3: Aktivera strikt läge som version 3,0</span><span class="sxs-lookup"><span data-stu-id="2fabe-132">Example 3: Turn on strict mode as version 3.0</span></span>

<span data-ttu-id="2fabe-133">Med strikt läge inställt på **av** , ogiltigt eller utanför intervall index resulterar resultatet av null-värden.</span><span class="sxs-lookup"><span data-stu-id="2fabe-133">With strict mode set to **Off** , invalid or out of bounds indexes result return null values.</span></span>

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

<span data-ttu-id="2fabe-134">Med strikt läge inställt på version 3 eller högre, är ogiltiga eller utanför gräns index resulterar i fel.</span><span class="sxs-lookup"><span data-stu-id="2fabe-134">With strict mode set to version 3 or higher, invalid or out of bounds indexes result in errors.</span></span>

## <span data-ttu-id="2fabe-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2fabe-135">PARAMETERS</span></span>

### <span data-ttu-id="2fabe-136">-Av</span><span class="sxs-lookup"><span data-stu-id="2fabe-136">-Off</span></span>

<span data-ttu-id="2fabe-137">Anger att den här cmdleten inaktiverar strikt läge för det aktuella omfånget och alla underordnade scope.</span><span class="sxs-lookup"><span data-stu-id="2fabe-137">Indicates that this cmdlet turns strict mode off for the current scope and all child scopes.</span></span>

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

### <span data-ttu-id="2fabe-138">-Version</span><span class="sxs-lookup"><span data-stu-id="2fabe-138">-Version</span></span>

<span data-ttu-id="2fabe-139">Anger de villkor som orsakar ett fel i strikt läge.</span><span class="sxs-lookup"><span data-stu-id="2fabe-139">Specifies the conditions that cause an error in strict mode.</span></span> <span data-ttu-id="2fabe-140">Den här parametern accepterar ett giltigt PowerShell-versions nummer.</span><span class="sxs-lookup"><span data-stu-id="2fabe-140">This parameter accepts any valid PowerShell version number.</span></span> <span data-ttu-id="2fabe-141">Alla tal som är större än 3 behandlas som **senaste**.</span><span class="sxs-lookup"><span data-stu-id="2fabe-141">Any number higher than 3 is treated as **Latest**.</span></span>

<span data-ttu-id="2fabe-142">De effektiva värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="2fabe-142">The effective values for this parameter are:</span></span>

- <span data-ttu-id="2fabe-143">1,0</span><span class="sxs-lookup"><span data-stu-id="2fabe-143">1.0</span></span>
  - <span data-ttu-id="2fabe-144">Förhindrar referenser till oinitierade variabler, förutom oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="2fabe-144">Prohibits references to uninitialized variables, except for uninitialized variables in strings.</span></span>
- <span data-ttu-id="2fabe-145">2.0</span><span class="sxs-lookup"><span data-stu-id="2fabe-145">2.0</span></span>
  - <span data-ttu-id="2fabe-146">Förhindrar referenser till oinitierade variabler.</span><span class="sxs-lookup"><span data-stu-id="2fabe-146">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="2fabe-147">Detta inkluderar oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="2fabe-147">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="2fabe-148">Förhindrar referenser till obefintliga egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="2fabe-148">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="2fabe-149">Förhindrar funktions anrop som använder syntaxen för att anropa metoder.</span><span class="sxs-lookup"><span data-stu-id="2fabe-149">Prohibits function calls that use the syntax for calling methods.</span></span>
- <span data-ttu-id="2fabe-150">3.0</span><span class="sxs-lookup"><span data-stu-id="2fabe-150">3.0</span></span>
  - <span data-ttu-id="2fabe-151">Förhindrar referenser till oinitierade variabler.</span><span class="sxs-lookup"><span data-stu-id="2fabe-151">Prohibits references to uninitialized variables.</span></span> <span data-ttu-id="2fabe-152">Detta inkluderar oinitierade variabler i strängar.</span><span class="sxs-lookup"><span data-stu-id="2fabe-152">This includes uninitialized variables in strings.</span></span>
  - <span data-ttu-id="2fabe-153">Förhindrar referenser till obefintliga egenskaper för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="2fabe-153">Prohibits references to non-existent properties of an object.</span></span>
  - <span data-ttu-id="2fabe-154">Förhindrar funktions anrop som använder syntaxen för att anropa metoder.</span><span class="sxs-lookup"><span data-stu-id="2fabe-154">Prohibits function calls that use the syntax for calling methods.</span></span>
  - <span data-ttu-id="2fabe-155">Förhindra att matriser utanför gränser eller inte går att matcha.</span><span class="sxs-lookup"><span data-stu-id="2fabe-155">Prohibit out of bounds or unresolvable array indexes.</span></span>
- <span data-ttu-id="2fabe-156">Senast</span><span class="sxs-lookup"><span data-stu-id="2fabe-156">Latest</span></span>
  - <span data-ttu-id="2fabe-157">Väljer den senaste versionen som är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="2fabe-157">Selects the latest version available.</span></span> <span data-ttu-id="2fabe-158">Den senaste versionen är den mest strikta.</span><span class="sxs-lookup"><span data-stu-id="2fabe-158">The latest version is the most strict.</span></span> <span data-ttu-id="2fabe-159">Använd det här värdet för att kontrol lera att skript använder den striktaste tillgängliga versionen, även när nya versioner läggs till i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fabe-159">Use this value to make sure that scripts use the strictest available version, even when new versions are added to PowerShell.</span></span>

> [!CAUTION]
> <span data-ttu-id="2fabe-160">Använda en **version** av de **senaste** i skripten.</span><span class="sxs-lookup"><span data-stu-id="2fabe-160">Using a **Version** of **Latest** in scripts.</span></span> <span data-ttu-id="2fabe-161">Betydelsen av **senaste** kan ändra i nya versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fabe-161">The meaning of **Latest** can change in new releases of PowerShell.</span></span> <span data-ttu-id="2fabe-162">Ett skript som skrivits för en äldre version av PowerShell som använder omfattas därför av `Set-StrictMode -Version Latest` mer restriktiva regler när de körs i en senare version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2fabe-162">Therefore, a script written for an older version of PowerShell that uses `Set-StrictMode -Version Latest` is subject to more restrictive rules when run in a newer version of PowerShell.</span></span>

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

### <span data-ttu-id="2fabe-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2fabe-163">CommonParameters</span></span>

<span data-ttu-id="2fabe-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2fabe-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2fabe-165">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2fabe-165">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2fabe-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="2fabe-166">INPUTS</span></span>

### <span data-ttu-id="2fabe-167">Inget</span><span class="sxs-lookup"><span data-stu-id="2fabe-167">None</span></span>

<span data-ttu-id="2fabe-168">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2fabe-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="2fabe-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2fabe-169">OUTPUTS</span></span>

### <span data-ttu-id="2fabe-170">Inget</span><span class="sxs-lookup"><span data-stu-id="2fabe-170">None</span></span>

<span data-ttu-id="2fabe-171">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2fabe-171">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="2fabe-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2fabe-172">NOTES</span></span>

<span data-ttu-id="2fabe-173">`Set-StrictMode` är endast effektivt i det omfång där det har angetts och i dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="2fabe-173">`Set-StrictMode` is effective only in the scope in which it is set and in its child scopes.</span></span> <span data-ttu-id="2fabe-174">Mer information om omfång i PowerShell finns [about_Scopes](about/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="2fabe-174">For more information about scopes in PowerShell, see [about_Scopes](about/about_Scopes.md).</span></span>

## <span data-ttu-id="2fabe-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2fabe-175">RELATED LINKS</span></span>

[<span data-ttu-id="2fabe-176">Set-PSDebug</span><span class="sxs-lookup"><span data-stu-id="2fabe-176">Set-PSDebug</span></span>](Set-PSDebug.md)
