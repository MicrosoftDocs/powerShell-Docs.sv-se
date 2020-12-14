---
description: Förklarar hur du lägger till parametrar till avancerade funktioner.
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: da21f6fb7d19fa2ffcd9cd6c5eea217792937ae4
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708522"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="b9b7f-103">Om functions avancerade parametrar</span><span class="sxs-lookup"><span data-stu-id="b9b7f-103">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="b9b7f-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b9b7f-104">Short description</span></span>

<span data-ttu-id="b9b7f-105">Förklarar hur du lägger till parametrar till avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-105">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="b9b7f-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b9b7f-106">Long description</span></span>

<span data-ttu-id="b9b7f-107">Du kan lägga till parametrar till de avancerade funktioner som du skriver och använda parametriserade och-argument för att begränsa de parameter värden som användarna skickar med parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-107">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="b9b7f-108">De parametrar som du lägger till i din funktion är tillgängliga för användare utöver de vanliga parametrarna som PowerShell automatiskt lägger till i alla cmdletar och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-108">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="b9b7f-109">Mer information om de gemensamma PowerShell-parametrarna finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-109">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="b9b7f-110">Från och med PowerShell 3,0 kan du använda ihopbuntning med `@Args` för att representera parametrarna i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-110">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="b9b7f-111">Ihopbuntning är giltig för enkla och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-111">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="b9b7f-112">Mer information finns i [about_Functions](about_Functions.md) och [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-112">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="b9b7f-113">Typ konvertering av parameter värden</span><span class="sxs-lookup"><span data-stu-id="b9b7f-113">Type conversion of parameter values</span></span>

<span data-ttu-id="b9b7f-114">När du anger strängar som argument för parametrar som förväntar sig en annan typ, konverterar PowerShell implicit strängarna till parameter måltypen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-114">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="b9b7f-115">Avancerade funktioner utför konstruktor-invariant-parsning av parameter värden.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-115">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="b9b7f-116">En kultur känslig konvertering utförs däremot under parameter bindning för kompilerade cmdlets.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-116">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="b9b7f-117">I det här exemplet skapar vi en cmdlet och en skript funktion som tar en `[datetime]` parameter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-117">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="b9b7f-118">Den aktuella kulturen ändras till att använda tyska inställningar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-118">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="b9b7f-119">Ett tyskt formaterat datum skickas till parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-119">A German-formatted date is passed to the parameter.</span></span>

```powershell
# Create a cmdlet that accepts a [datetime] argument.
Add-Type @'
  using System;
  using System.Management.Automation;
  [Cmdlet("Get", "Date_Cmdlet")]
  public class GetFooCmdlet : Cmdlet {

    [Parameter(Position=0)]
    public DateTime Date { get; set; }

    protected override void ProcessRecord() {
      WriteObject(Date);
    }
  }
'@ -PassThru | % Assembly | Import-Module

[cultureinfo]::CurrentCulture = 'de-DE'
$dateStr = '19-06-2018'

Get-Date_Cmdlet $dateStr
```

```Output
Dienstag, 19. Juni 2018 00:00:00
```

<span data-ttu-id="b9b7f-120">Som du ser ovan använder cmdlet: en kultur känslig parsning för att konvertera strängen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-120">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

```powershell
# Define an equivalent function.
function Get-Date_Func {
  param(
    [DateTime] $Date
  )
  process {
    $Date
  }
}

[cultureinfo]::CurrentCulture = 'de-DE'

# This German-format date string doesn't work with the invariant culture.
# E.g., [datetime] '19-06-2018' breaks.
$dateStr = '19-06-2018'

Get-Date_Func $dateStr
```

<span data-ttu-id="b9b7f-121">Avancerade funktioner använder kulturen-invariant-parsning, vilket resulterar i följande fel.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-121">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func: Cannot process argument transformation on parameter 'Date'.
Cannot convert value "19-06-2018" to type "System.DateTime". Error: "String
'19-06-2018' was not recognized as a valid DateTime."
```

## <a name="static-parameters"></a><span data-ttu-id="b9b7f-122">Statiska parametrar</span><span class="sxs-lookup"><span data-stu-id="b9b7f-122">Static parameters</span></span>

<span data-ttu-id="b9b7f-123">Statiska parametrar är parametrar som alltid är tillgängliga i funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-123">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="b9b7f-124">De flesta parametrar i PowerShell-cmdletar och skript är statiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-124">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="b9b7f-125">I följande exempel visas en deklaration av en **computername** -parameter med följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-125">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="b9b7f-126">Det är obligatoriskt (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-126">It's mandatory (required).</span></span>
- <span data-ttu-id="b9b7f-127">Det tar emot inmatade från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-127">It takes input from the pipeline.</span></span>
- <span data-ttu-id="b9b7f-128">Det tar en matris med strängar som inmatade.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-128">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="b9b7f-129">Attribut för parametrar</span><span class="sxs-lookup"><span data-stu-id="b9b7f-129">Attributes of parameters</span></span>

<span data-ttu-id="b9b7f-130">I det här avsnittet beskrivs de attribut som du kan lägga till i funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-130">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="b9b7f-131">Alla attribut är valfria.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-131">All attributes are optional.</span></span> <span data-ttu-id="b9b7f-132">Men om du utelämnar attributet **CmdletBinding** , och sedan ska identifieras som en avancerad funktion, måste funktionen innehålla attributet- **parameter** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-132">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="b9b7f-133">Du kan lägga till ett eller flera attribut i varje parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-133">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="b9b7f-134">Det finns ingen gräns för antalet attribut som du kan lägga till i en parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-134">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="b9b7f-135">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-135">Parameter attribute</span></span>

<span data-ttu-id="b9b7f-136">Attributet **parameter** används för att deklarera attributen för funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-136">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="b9b7f-137">Attributet **parameter** är valfritt och du kan utelämna det om ingen av parametrarna för dina funktioner behöver attribut.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-137">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="b9b7f-138">Men för att kunna identifieras som en avancerad funktion, i stället för en enkel funktion, måste en funktion ha antingen attributet **CmdletBinding** eller attributet **parameter** eller båda.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-138">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="b9b7f-139">Attributet **parameter** innehåller argument som definierar parameterns egenskaper, till exempel om parametern är obligatorisk eller valfri.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-139">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="b9b7f-140">Använd följande syntax för att deklarera **parameter** -attributet, ett argument och ett argument värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-140">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="b9b7f-141">De parenteser som omger argumentet och dess värde måste följa **parametern** utan något mellanliggande blank steg.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-141">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="b9b7f-142">Använd kommatecken för att avgränsa argument inom parentes.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-142">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="b9b7f-143">Använd följande syntax för att deklarera två argument för attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-143">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="b9b7f-144">De booleska argument typerna för **parametern** attribut är **false** när de utelämnas från attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-144">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="b9b7f-145">Ange värdet för argumentet till `$true` eller bara lista argumentet efter namn.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-145">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="b9b7f-146">Följande **parameter** -attribut är till exempel likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-146">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="b9b7f-147">Om du använder **parameter** -attributet utan argument, som ett alternativ till att använda attributet **CmdletBinding** , krävs fortfarande de parenteser som följer attributnamnet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-147">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="b9b7f-148">Obligatoriskt argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-148">Mandatory argument</span></span>

<span data-ttu-id="b9b7f-149">`Mandatory`Argumentet anger att parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-149">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="b9b7f-150">Om det här argumentet inte anges är parametern valfri.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-150">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="b9b7f-151">I följande exempel deklareras parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-151">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="b9b7f-152">`Mandatory`Argumentet används för att göra parametern obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-152">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="b9b7f-153">Positions argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-153">Position argument</span></span>

<span data-ttu-id="b9b7f-154">`Position`Argumentet avgör om parameter namnet krävs när parametern används i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-154">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="b9b7f-155">När en parameter deklaration innehåller `Position` argumentet, kan parameter namnet utelämnas och PowerShell identifierar det namnlösa parametervärdet med dess position, eller ordning, i listan över namnlösa parameter värden i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-155">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="b9b7f-156">Om `Position` argumentet inte anges måste parameter namnet eller ett alias eller en förkortning för parameter namn föregå parametervärdet när parametern används i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-156">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="b9b7f-157">Som standard är alla funktions parametrar placerade i position.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-157">By default, all function parameters are positional.</span></span> <span data-ttu-id="b9b7f-158">PowerShell tilldelar positions nummer till parametrar i den ordning som parametrarna deklareras i funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-158">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="b9b7f-159">Om du vill inaktivera den här funktionen ställer du in värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** till `$False` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-159">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="b9b7f-160">`Position`Argumentet prioriteras över värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-160">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="b9b7f-161">Mer information finns `PositionalBinding` i i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-161">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="b9b7f-162">Värdet för `Position` argumentet anges som ett heltal.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-162">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="b9b7f-163">Position svärdet **0** representerar den första positionen i kommandot, ett positions värde på **1** representerar den andra positionen i kommandot och så vidare.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-163">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="b9b7f-164">Om en funktion inte har några positions parametrar tilldelar PowerShell positioner till varje parameter baserat på i vilken ordning parametrarna deklareras.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-164">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="b9b7f-165">Vi rekommenderar dock inte att du använder den här tilldelningen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-165">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="b9b7f-166">Använd argumentet om du vill att parametrar ska placeras i position `Position` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-166">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="b9b7f-167">I följande exempel deklareras parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-167">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="b9b7f-168">`Position`Argumentet använder argumentet med värdet **0**.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-168">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="b9b7f-169">Det innebär att när `-ComputerName` har utelämnats från kommandot måste dess värde vara det första eller det enda parameter värde som inte är namn i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-169">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="b9b7f-170">ParameterSetName-argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-170">ParameterSetName argument</span></span>

<span data-ttu-id="b9b7f-171">`ParameterSetName`Argumentet anger den parameter som en parameter tillhör.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-171">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="b9b7f-172">Om ingen parameter uppsättning anges, tillhör parametern alla parameter uppsättningar som definieras av funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-172">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="b9b7f-173">För att vara unik måste därför varje parameter uppsättning ha minst en parameter som inte är medlem i någon annan parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-173">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="b9b7f-174">För en cmdlet eller funktion finns det en gräns på 32 parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-174">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="b9b7f-175">I följande exempel deklareras en **computername** -parameter i `Computer` parameter uppsättningen, en **username** -parameter i `User` parameter uppsättningen och en **sammanfattnings** parameter i båda parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-175">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false)]
    [Switch]
    $Summary
)
```

<span data-ttu-id="b9b7f-176">Du kan bara ange ett `ParameterSetName` värde i varje argument och bara ett `ParameterSetName` argument i varje **parameter** -attribut.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-176">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="b9b7f-177">Om du vill ange att en parameter visas i mer än en parameter uppsättning lägger du till ytterligare **parameter** -attribut.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-177">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="b9b7f-178">I följande exempel lägger du uttryckligen till **sammanfattnings** parametern `Computer` i `User` parameter uppsättningarna och.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-178">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="b9b7f-179">**Sammanfattnings** parametern är valfri i `Computer` parameter uppsättningen och obligatorisk i `User` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-179">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ParameterSetName="Computer")]
    [String[]]
    $ComputerName,

    [Parameter(Mandatory=$true,
    ParameterSetName="User")]
    [String[]]
    $UserName,

    [Parameter(Mandatory=$false, ParameterSetName="Computer")]
    [Parameter(Mandatory=$true, ParameterSetName="User")]
    [Switch]
    $Summary
)
```

<span data-ttu-id="b9b7f-180">Mer information om parameter uppsättningar finns i [About parameter set](about_parameter_sets.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-180">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="b9b7f-181">ValueFromPipeline-argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-181">ValueFromPipeline argument</span></span>

<span data-ttu-id="b9b7f-182">`ValueFromPipeline`Argumentet anger att parametern accepterar inmatade objekt från ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-182">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="b9b7f-183">Ange det här argumentet om funktionen accepterar hela objektet, inte bara en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-183">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="b9b7f-184">I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar ett objekt som skickas till funktionen från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-184">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="b9b7f-185">ValueFromPipelineByPropertyName-argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-185">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="b9b7f-186">`ValueFromPipelineByPropertyName`Argumentet anger att parametern accepterar inmatade objekt från en egenskap i ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-186">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="b9b7f-187">Objekt egenskapen måste ha samma namn eller alias som parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-187">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="b9b7f-188">Om funktionen till exempel har en **computername** -parameter och skickas-objektet har egenskapen **computername** , tilldelas värdet för egenskapen **computername** till funktionens **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-188">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="b9b7f-189">I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar indatamängden från objektets **computername** -egenskap som skickas till funktionen via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-189">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="b9b7f-190">En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken _Delay-bind_ i parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-190">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="b9b7f-191">Skript blocket _Delay-bind_ körs automatiskt under **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-191">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="b9b7f-192">Resultatet är kopplat till parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-192">The result is bound to the parameter.</span></span> <span data-ttu-id="b9b7f-193">Fördröjd bindning fungerar inte för parametrar som definierats som typ `ScriptBlock` eller `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-193">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="b9b7f-194">Skript blocket skickas genom _utan_ att anropas.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-194">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="b9b7f-195">Du kan läsa mer om _fördröjning – binda_ skript block här [about_Script_Blocks. MD](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-195">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="b9b7f-196">ValueFromRemainingArguments-argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-196">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="b9b7f-197">`ValueFromRemainingArguments`Argumentet anger att parametern accepterar alla parameter värden i kommandot som inte har tilldelats andra parametrar för funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-197">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="b9b7f-198">I följande exempel deklareras en **värde** parameter som är obligatorisk och en **återstående** parameter som accepterar alla återstående parameter värden som skickas till funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-198">The following example declares a **Value** parameter that's mandatory and a **Remaining** parameter that accepts all the remaining parameter values that are submitted to the function.</span></span>

```powershell
function Test-Remainder
{
     param(
         [string]
         [Parameter(Mandatory = $true, Position=0)]
         $Value,
         [string[]]
         [Parameter(Position=1, ValueFromRemainingArguments)]
         $Remaining)
     "Found $($Remaining.Count) elements"
     for ($i = 0; $i -lt $Remaining.Count; $i++)
     {
        "${i}: $($Remaining[$i])"
     }
}
Test-Remainder first one,two
```

```Output
Found 2 elements
0: one
1: two
```

> [!NOTE]
> <span data-ttu-id="b9b7f-199">Före PowerShell 6,2 anslöts **ValueFromRemainingArguments** -samlingen som en enskild enhet under index **0**.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-199">Prior to PowerShell 6.2, the **ValueFromRemainingArguments** collection was joined as single entity under index **0**.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="b9b7f-200">HelpMessage-argument</span><span class="sxs-lookup"><span data-stu-id="b9b7f-200">HelpMessage argument</span></span>

<span data-ttu-id="b9b7f-201">`HelpMessage`Argumentet anger en sträng som innehåller en kort beskrivning av parametern eller dess värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-201">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="b9b7f-202">PowerShell visar det här meddelandet i den prompt som visas när ett nödvändigt parameter värde saknas i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-202">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="b9b7f-203">Det här argumentet har ingen påverkan på valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-203">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="b9b7f-204">I följande exempel deklareras en obligatorisk **computername** -parameter och ett hjälp meddelande som förklarar det förväntade parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-204">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="b9b7f-205">Om det inte finns någon annan [kommenterings-baserad hjälpfil](./about_comment_based_help.md) för funktionen (till exempel `.SYNOPSIS` ) visas även det här meddelandet i `Get-Help` utdata.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-205">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="b9b7f-206">Alias-attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-206">Alias attribute</span></span>

<span data-ttu-id="b9b7f-207">Attributet **alias** upprättar ett alternativt namn för parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-207">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="b9b7f-208">Det finns ingen gräns för antalet alias som du kan tilldela till en parameter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-208">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="b9b7f-209">I följande exempel visas en parameter deklaration som lägger till **CN** -och **MachineName** -alias till den obligatoriska **computername** -parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-209">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="b9b7f-210">SupportsWildcards-attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-210">SupportsWildcards attribute</span></span>

<span data-ttu-id="b9b7f-211">Attributet **SupportsWildcards** används för att indikera att parametern accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-211">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="b9b7f-212">I följande exempel visas en parameter deklaration för en obligatorisk **Sök vägs** parameter som stöder jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-212">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="b9b7f-213">Om du använder det här attributet aktive ras inte stöd för jokertecken automatiskt.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-213">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="b9b7f-214">Cmdlet-utvecklaren måste implementera koden för att hantera jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-214">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="b9b7f-215">Vilka jokertecken som stöds kan variera beroende på underliggande API eller PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-215">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="b9b7f-216">Mer information finns i [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-216">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="b9b7f-217">Attribut för parameter-och variabel verifiering</span><span class="sxs-lookup"><span data-stu-id="b9b7f-217">Parameter and variable validation attributes</span></span>

<span data-ttu-id="b9b7f-218">Validera attribut Direct PowerShell för att testa de parameter värden som användarna skickar när de anropar funktionen Advanced.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-218">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="b9b7f-219">Om parameter värden inte fungerar som testet, genereras ett fel och funktionen anropas inte.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-219">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="b9b7f-220">Parameter verifiering tillämpas endast på angivna indata och andra värden som standardvärden är inte verifierade.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-220">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="b9b7f-221">Du kan också använda verifierings-attributen för att begränsa de värden som användarna kan ange för variabler.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-221">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="b9b7f-222">När du använder en typ konverterare tillsammans med ett verifierings attribut måste typ konverteraren definieras före-attributet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-222">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="b9b7f-223">AllowNull-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-223">AllowNull validation attribute</span></span>

<span data-ttu-id="b9b7f-224">Attributet **AllowNull** tillåter att värdet för en obligatorisk parameter ska vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-224">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="b9b7f-225">I följande exempel deklareras en hash- **ComputerInfo** -parameter som kan ha ett **Null** -värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-225">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="b9b7f-226">Attributet **AllowNull** fungerar inte om typ konverteraren är inställd på sträng eftersom sträng typen inte accepterar ett null-värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-226">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="b9b7f-227">Du kan använda attributet **AllowEmptyString** för det här scenariot.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-227">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="b9b7f-228">AllowEmptyString-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-228">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="b9b7f-229">Attributet **AllowEmptyString** tillåter att värdet för en obligatorisk parameter är en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-229">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="b9b7f-230">I följande exempel deklareras en **computername** -parameter som kan ha ett tomt sträng värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-230">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="b9b7f-231">AllowEmptyCollection-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-231">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="b9b7f-232">Attributet **AllowEmptyCollection** tillåter att värdet för en obligatorisk parameter är en tom samling `@()` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-232">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="b9b7f-233">I följande exempel deklareras en **computername** -parameter som kan ha ett tomt samlings värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-233">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="b9b7f-234">ValidateCount-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-234">ValidateCount validation attribute</span></span>

<span data-ttu-id="b9b7f-235">Attributet **ValidateCount** anger det lägsta och högsta antalet parameter värden som en parameter accepterar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-235">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="b9b7f-236">PowerShell genererar ett fel om antalet parameter värden i kommandot som anropar funktionen ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-236">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="b9b7f-237">Följande parameter deklaration skapar en **computername** -parameter som tar en till fem parameter värden.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-237">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="b9b7f-238">ValidateLength-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-238">ValidateLength validation attribute</span></span>

<span data-ttu-id="b9b7f-239">Attributet **ValidateLength** anger det lägsta och högsta antalet tecken i en parameter eller ett variabel värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-239">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="b9b7f-240">PowerShell genererar ett fel om längden på ett värde som har angetts för en parameter eller en variabel ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-240">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="b9b7f-241">I följande exempel måste varje dator namn ha ett till tio tecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-241">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="b9b7f-242">I följande exempel måste värdet för variabeln `$number` vara minst ett tecken långt och högst tio tecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-242">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="b9b7f-243">I det här exemplet är värdet för `01` inkapslat i enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-243">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="b9b7f-244">**ValidateLength** -attributet accepterar inte ett tal utan att de omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-244">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="b9b7f-245">ValidatePattern-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-245">ValidatePattern validation attribute</span></span>

<span data-ttu-id="b9b7f-246">Attributet **ValidatePattern** anger ett reguljärt uttryck som jämförs med parametern eller variabeln värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-246">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="b9b7f-247">PowerShell genererar ett fel om värdet inte matchar mönstret för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-247">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="b9b7f-248">I följande exempel måste parametervärdet innehålla ett fyrsiffrigt tal och varje siffra måste vara ett tal mellan noll och nio.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-248">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="b9b7f-249">I följande exempel måste värdet för variabeln `$number` vara exakt ett fyrsiffrigt tal och varje siffra måste vara ett tal från noll till nio.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-249">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="b9b7f-250">ValidateRange-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-250">ValidateRange validation attribute</span></span>

<span data-ttu-id="b9b7f-251">Attributet **ValidateRange** anger ett numeriskt intervall eller ett **ValidateRangeKind** Enum-värde för varje parameter eller variabel värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-251">The **ValidateRange** attribute specifies a numeric range or a **ValidateRangeKind** enum value for each parameter or variable value.</span></span>
<span data-ttu-id="b9b7f-252">PowerShell genererar ett fel om ett värde ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-252">PowerShell generates an error if any value is outside that range.</span></span>

<span data-ttu-id="b9b7f-253">**ValidateRangeKind** -uppräkningen tillåter följande värden:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-253">The **ValidateRangeKind** enum allows for the following values:</span></span>

- <span data-ttu-id="b9b7f-254">**Positivt** – ett tal som är större än noll.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-254">**Positive** - A number greater than zero.</span></span>
- <span data-ttu-id="b9b7f-255">**Negativt** – ett tal som är mindre än noll.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-255">**Negative** - A number less than zero.</span></span>
- <span data-ttu-id="b9b7f-256">Ej **positivt** -ett tal som är mindre än eller lika med noll.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-256">**NonPositive** - A number less than or equal to zero.</span></span>
- <span data-ttu-id="b9b7f-257">Icke- **negativt** – ett tal som är större än eller lika med noll.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-257">**NonNegative** - A number greater than or equal to zero.</span></span>

<span data-ttu-id="b9b7f-258">I följande exempel måste värdet **för parametern** Parameters vara mellan noll och tio.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-258">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="b9b7f-259">I följande exempel måste värdet för variabeln `$number` vara mellan noll och tio.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-259">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

<span data-ttu-id="b9b7f-260">I följande exempel måste värdet för variabeln `$number` vara större än noll.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-260">In the following example, the value of the variable `$number` must be greater than zero.</span></span>

```powershell
[Int32][ValidateRange("Positive")]$number = 1
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="b9b7f-261">ValidateScript-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-261">ValidateScript validation attribute</span></span>

<span data-ttu-id="b9b7f-262">Attributet **ValidateScript** anger ett skript som används för att validera en parameter eller ett variabel värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-262">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="b9b7f-263">PowerShell rör värdet i skriptet och genererar ett fel om skriptet returnerar `$false` eller om skriptet genererar ett undantag.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-263">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="b9b7f-264">När du använder attributet **ValidateScript** mappas värdet som verifieras till `$_` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-264">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="b9b7f-265">Du kan använda `$_` variabeln för att referera till värdet i skriptet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-265">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="b9b7f-266">I följande exempel måste värdet för parametern **EventDate** vara större än eller lika med det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-266">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="b9b7f-267">I följande exempel måste värdet för variabeln `$date` vara större än eller lika med aktuellt datum och tid.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-267">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="b9b7f-268">Om du använder **ValidateScript** kan du inte skicka ett `$null` värde till parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-268">If you use **ValidateScript**, you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="b9b7f-269">När du skickar ett null-värde kan **ValidateScript** inte validera argumentet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-269">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="b9b7f-270">ValidateSet-attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-270">ValidateSet attribute</span></span>

<span data-ttu-id="b9b7f-271">Attributet **ValidateSet** anger en uppsättning giltiga värden för en parameter eller en variabel och möjliggör slut för ande av tabbar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-271">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="b9b7f-272">PowerShell genererar ett fel om en parameter eller ett variabel värde inte matchar ett värde i mängden.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-272">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="b9b7f-273">I följande exempel kan värdet för **detalj** parametern endast vara låg, genomsnitt eller hög.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-273">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="b9b7f-274">I följande exempel måste värdet för variabeln `$flavor` vara choklad, Strawberry eller vanilj.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-274">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="b9b7f-275">Verifieringen sker när variabeln tilldelas även inom skriptet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-275">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="b9b7f-276">Följande resulterar exempelvis i ett fel vid körning:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-276">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

#### <a name="dynamic-validateset-values"></a><span data-ttu-id="b9b7f-277">Dynamiska validateSet-värden</span><span class="sxs-lookup"><span data-stu-id="b9b7f-277">Dynamic validateSet values</span></span>

<span data-ttu-id="b9b7f-278">Du kan använda en **klass** för att dynamiskt generera värden för **ValidateSet** vid körning.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-278">You can use a **Class** to dynamically generate the values for **ValidateSet** at runtime.</span></span> <span data-ttu-id="b9b7f-279">I följande exempel genereras giltiga värden för variabeln `$Sound` via en **klass** med namnet **SoundNames** som kontrollerar tre fil Systems sökvägar för tillgängliga ljudfiler:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-279">In the following example, the valid values for the variable `$Sound` are generated via a **Class** named **SoundNames** that checks three filesystem paths for available sound files:</span></span>

```powershell
Class SoundNames : System.Management.Automation.IValidateSetValuesGenerator {
    [String[]] GetValidValues() {
        $SoundPaths = '/System/Library/Sounds/',
            '/Library/Sounds','~/Library/Sounds'
        $SoundNames = ForEach ($SoundPath in $SoundPaths) {
            If (Test-Path $SoundPath) {
                (Get-ChildItem $SoundPath).BaseName
            }
        }
        return [String[]] $SoundNames
    }
}
```

<span data-ttu-id="b9b7f-280">`[SoundNames]`Klassen implementeras sedan som ett dynamiskt **ValidateSet** -värde enligt följande:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-280">The `[SoundNames]` class is then implemented as a dynamic **ValidateSet** value as follows:</span></span>

```powershell
Param(
    [ValidateSet([SoundNames])]
    [String]$Sound
)
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="b9b7f-281">ValidateNotNull-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-281">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="b9b7f-282">Attributet **ValidateNotNull** anger att parametervärdet får inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-282">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="b9b7f-283">PowerShell genererar ett fel om parametervärdet är `$null` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-283">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="b9b7f-284">Attributet **ValidateNotNull** är utformat för användning när parametern är valfri och typen är odefinierad eller har en typ konverterare som inte kan implicit konvertera ett null-värde som- **objekt**.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-284">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="b9b7f-285">Om du anger en typ som implicit ska konvertera ett null-värde, till exempel en **sträng**, konverteras värdet null till en tom sträng även när du använder attributet **ValidateNotNull** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-285">If you specify a type that that will implicitly convert a null value such as a **string**, the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="b9b7f-286">För det här scenariot använder du **ValidateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="b9b7f-286">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="b9b7f-287">I följande exempel kan värdet för **ID-** parametern inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-287">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="b9b7f-288">ValidateNotNullOrEmpty-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-288">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="b9b7f-289">Attributet **ValidateNotNullOrEmpty** anger att parametervärdet får inte vara `$null` en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-289">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="b9b7f-290">PowerShell genererar ett fel om parametern används i ett funktions anrop, men dess värde är `$null` en tom sträng ( `""` ) eller en tom matris `@()` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-290">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="b9b7f-291">ValidateDrive-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-291">ValidateDrive validation attribute</span></span>

<span data-ttu-id="b9b7f-292">Attributet **ValidateDrive** anger att parametervärdet måste representera sökvägen, som bara refererar till tillåtna enheter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-292">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="b9b7f-293">PowerShell genererar ett fel om parametervärdet refererar till andra enheter än vad som tillåts.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-293">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="b9b7f-294">Förekomsten av sökvägen, förutom själva enheten, är inte verifierad.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-294">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="b9b7f-295">Om du använder en relativ sökväg måste den aktuella enheten finnas i listan över tillåtna enheter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-295">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="b9b7f-296">ValidateUserDrive-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-296">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="b9b7f-297">Attributet **ValidateUserDrive** anger att parametervärdet måste representera sökvägen som refererar till `User` enheten.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-297">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="b9b7f-298">PowerShell genererar ett fel om sökvägen refererar till en annan enhet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-298">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="b9b7f-299">Verifierings attributet testar bara för att det finns en enhets del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-299">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="b9b7f-300">Om du använder relativ sökväg måste den aktuella enheten vara `User` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-300">If you use relative path, the current drive must be `User`.</span></span>

```powershell
function Test-UserDrivePath{
    [OutputType([bool])]
    Param(
      [Parameter(Mandatory=, Position=0)][ValidateUserDrive()][String]$Path
      )
    $True
}

Test-UserDrivePath -Path C:\
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. The path
argument drive C does not belong to the set of approved drives: User.
Supply a path argument with an approved drive.
```

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
Test-UserDrivePath: Cannot validate argument on parameter 'Path'. Cannot
find drive. A drive with the name 'User' does not exist.
```

<span data-ttu-id="b9b7f-301">Du kan definiera `User` enhet i Jea-sessionsinställningar (bara för administration).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-301">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="b9b7f-302">I det här exemplet skapar vi användaren: enhet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-302">For this example, we create the User: drive.</span></span>

```powershell
New-PSDrive -Name 'User' -PSProvider FileSystem -Root $env:HOMEPATH
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
User               75.76         24.24 FileSystem    C:\Users\ExampleUser

```powershell
Test-UserDrivePath -Path 'User:\A_folder_that_does_not_exist'
```

```Output
True
```

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="b9b7f-303">ValidateTrustedData-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-303">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="b9b7f-304">Det här attributet lades till i PowerShell-startattributet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-304">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="b9b7f-305">För tillfället används attributet internt av PowerShell och är inte avsett för extern användning.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-305">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="b9b7f-306">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="b9b7f-306">Dynamic parameters</span></span>

<span data-ttu-id="b9b7f-307">Dynamiska parametrar är parametrar för en cmdlet, funktion eller ett skript som endast är tillgängliga under vissa förhållanden.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-307">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="b9b7f-308">Till exempel har flera Provider-cmdlets parametrar som endast är tillgängliga när cmdleten används i leverantörs enheten, eller i en viss sökväg för providerns enhet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-308">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="b9b7f-309">Till exempel är **encoding** -parametern endast tillgänglig på `Add-Content` `Get-Content` cmdletarna, och `Set-Content` när den används i en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-309">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="b9b7f-310">Du kan också skapa en parameter som bara visas när en annan parameter används i funktions kommandot eller när en annan parameter har ett visst värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-310">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="b9b7f-311">Dynamiska parametrar kan vara användbara, men Använd dem bara när det behövs, eftersom det kan vara svårt för användarna att identifiera sig.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-311">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="b9b7f-312">Om du vill hitta en dynamisk parameter måste användaren finnas i providerns sökväg, använda parametern **argument List** i `Get-Command` cmdleten eller använda parametern **Path** i `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-312">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="b9b7f-313">Om du vill skapa en dynamisk parameter för en funktion eller ett skript använder du `DynamicParam` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-313">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="b9b7f-314">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-314">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="b9b7f-315">Använd en instruktion i instruktions listan `If` för att ange de villkor under vilka parametern är tillgänglig i funktionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-315">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="b9b7f-316">Använd `New-Object` cmdleten för att skapa ett **system. Management. Automation. RuntimeDefinedParameter** -objekt för att representera parametern och ange dess namn.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-316">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="b9b7f-317">Du kan använda ett `New-Object` kommando för att skapa ett **system. Management. Automation. ParameterAttribute** -objekt som representerar attribut för parametern, till exempel **obligatorisk**, **position** eller **ValueFromPipeline** eller dess parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-317">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory**, **Position**, or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="b9b7f-318">I följande exempel visas en exempel funktion med standard parametrar med namnet **Name** och **Path**, och en valfri dynamisk parameter med namnet **DP1**.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-318">The following example shows a sample function with standard parameters named **Name** and **Path**, and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="b9b7f-319">Parametern **DP1** är i `PSet1` parameter uppsättningen och har en typ av `Int32` .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-319">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="b9b7f-320">Parametern **DP1** är endast tillgänglig i `Get-Sample` funktionen när värdet för **Sök vägs** parametern börjar med `HKLM:` , vilket anger att den används i `HKEY_LOCAL_MACHINE` register enheten.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-320">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

```powershell
function Get-Sample {
  [CmdletBinding()]
  Param([String]$Name, [String]$Path)

  DynamicParam
  {
    if ($Path.StartsWith("HKLM:"))
    {
      $attributes = New-Object -Type `
        System.Management.Automation.ParameterAttribute
      $attributes.ParameterSetName = "PSet1"
      $attributes.Mandatory = $false
      $attributeCollection = New-Object `
        -Type System.Collections.ObjectModel.Collection[System.Attribute]
      $attributeCollection.Add($attributes)

      $dynParam1 = New-Object -Type `
        System.Management.Automation.RuntimeDefinedParameter("DP1", [Int32],
          $attributeCollection)

      $paramDictionary = New-Object `
        -Type System.Management.Automation.RuntimeDefinedParameterDictionary
      $paramDictionary.Add("DP1", $dynParam1)
      return $paramDictionary
    }
  }
}
```

<span data-ttu-id="b9b7f-321">Mer information finns i [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-321">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="b9b7f-322">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="b9b7f-322">Switch parameters</span></span>

<span data-ttu-id="b9b7f-323">Växlings parametrar är parametrar utan parameter värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-323">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="b9b7f-324">De är bara effektiva när de används och har bara en effekt.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-324">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="b9b7f-325">Till exempel är parametern **noprofile** i **powershell.exe** en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-325">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="b9b7f-326">Om du vill skapa en växel parameter i en funktion anger du `Switch` typen i parameter definitionen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-326">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="b9b7f-327">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-327">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="b9b7f-328">Eller så kan du använda en annan metod:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-328">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="b9b7f-329">Växlings parametrar är enkla att använda och föredras över booleska parametrar som har en mer svår syntax.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-329">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="b9b7f-330">Om du till exempel vill använda en växlings parameter skriver användaren parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-330">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="b9b7f-331">Om du vill använda en boolesk parameter skriver användaren parametern och ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-331">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="b9b7f-332">När du skapar växlings parametrar väljer du parameter namnet noggrant.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-332">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="b9b7f-333">Se till att parameter namnet meddelar användaren om parameterns resultat.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-333">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="b9b7f-334">Undvik tvetydiga termer, till exempel **filter** eller **maximum** som kan innebära att ett värde krävs.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-334">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="b9b7f-335">ArgumentCompleter-attribut</span><span class="sxs-lookup"><span data-stu-id="b9b7f-335">ArgumentCompleter attribute</span></span>

<span data-ttu-id="b9b7f-336">Med attributet **ArgumentCompleter** kan du lägga till TABB-slutförande-värden till en speciell parameter.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-336">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="b9b7f-337">Ett **ArgumentCompleter** -attribut måste definieras för varje parameter som kräver TABB-slutförande.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-337">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="b9b7f-338">Precis som med **DynamicParameters** beräknas de tillgängliga värdena vid körning när användaren trycker på <kbd>TABB</kbd> efter parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-338">Similar to **DynamicParameters**, the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="b9b7f-339">Om du vill lägga till ett **ArgumentCompleter** -attribut måste du definiera ett skript block som bestämmer värdena.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-339">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="b9b7f-340">Skript blocket måste ha följande parametrar i den ordning som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-340">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="b9b7f-341">Parameterns namn spelar ingen roll när värdena anges i position.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-341">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="b9b7f-342">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-342">The syntax is as follows:</span></span>

```powershell
Param(
    [Parameter(Mandatory)]
    [ArgumentCompleter({
        param ( $commandName,
                $parameterName,
                $wordToComplete,
                $commandAst,
                $fakeBoundParameters )
        # Perform calculation of tab completed values here.
    })]
)
```

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="b9b7f-343">ArgumentCompleter-skript block</span><span class="sxs-lookup"><span data-stu-id="b9b7f-343">ArgumentCompleter script block</span></span>

<span data-ttu-id="b9b7f-344">Skript block parametrarna har angetts till följande värden:</span><span class="sxs-lookup"><span data-stu-id="b9b7f-344">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="b9b7f-345">`$commandName` (Position 0) – den här parametern anges till namnet på det kommando som skript blocket tillhandahåller för att slutföra tabben.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-345">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="b9b7f-346">`$parameterName` (Position 1) – den här parametern har angetts till den parameter vars värde kräver att tabbtangenten slutförs.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-346">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="b9b7f-347">`$wordToComplete` (Position 2) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-347">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="b9b7f-348">`$commandAst` (Position 3) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-348">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="b9b7f-349">Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-349">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="b9b7f-350">`$fakeBoundParameters` (Position 4) – den här parametern anges till en hash-text som innehåller `$PSBoundParameters` för cmdleten innan användaren tryckte på <kbd>fliken</kbd>. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="b9b7f-350">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="b9b7f-351">**ArgumentCompleter** -skript blocket måste avregistrera värdena med hjälp av pipelinen, till exempel, `ForEach-Object` `Where-Object` eller någon annan lämplig metod.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-351">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="b9b7f-352">Om du returnerar en matris med värden kan PowerShell behandla hela matrisen som **ett** värde för sista tabb.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-352">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="b9b7f-353">I följande exempel läggs TABB-slutförande till **Value** -parametern.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-353">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="b9b7f-354">Om bara **värde** parametern anges visas alla möjliga värden eller argument för **värdet** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-354">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="b9b7f-355">När **typ** parametern anges visar **värde** parametern bara möjliga värden för den typen.</span><span class="sxs-lookup"><span data-stu-id="b9b7f-355">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="b9b7f-356">Dessutom `-like` säkerställer operatorn att om användaren skriver följande kommando och använder <kbd>TABB</kbd> -slutförande, returneras bara **Apple** .</span><span class="sxs-lookup"><span data-stu-id="b9b7f-356">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

`Test-ArgumentCompleter -Type Fruits -Value A`

```powershell
function Test-ArgumentCompleter {
[CmdletBinding()]
 param (
        [Parameter(Mandatory=$true)]
        [ValidateSet('Fruits', 'Vegetables')]
        $Type,
        [Parameter(Mandatory=$true)]
        [ArgumentCompleter( {
            param ( $commandName,
                    $parameterName,
                    $wordToComplete,
                    $commandAst,
                    $fakeBoundParameters )

            $possibleValues = @{
                Fruits = @('Apple', 'Orange', 'Banana')
                Vegetables = @('Tomato', 'Squash', 'Corn')
            }
            if ($fakeBoundParameters.ContainsKey('Type'))
            {
                $possibleValues[$fakeBoundParameters.Type] | Where-Object {
                    $_ -like "$wordToComplete*"
                }
            }
            else
            {
                $possibleValues.Values | ForEach-Object {$_}
            }
        } )]
        $Value
      )
}
```

## <a name="see-also"></a><span data-ttu-id="b9b7f-357">Se även</span><span class="sxs-lookup"><span data-stu-id="b9b7f-357">See also</span></span>

[<span data-ttu-id="b9b7f-358">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="b9b7f-358">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="b9b7f-359">about_Functions</span><span class="sxs-lookup"><span data-stu-id="b9b7f-359">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="b9b7f-360">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="b9b7f-360">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="b9b7f-361">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="b9b7f-361">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="b9b7f-362">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="b9b7f-362">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="b9b7f-363">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="b9b7f-363">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
