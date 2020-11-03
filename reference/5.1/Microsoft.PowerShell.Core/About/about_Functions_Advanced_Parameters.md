---
description: Förklarar hur du lägger till parametrar till avancerade funktioner.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Parameters
ms.openlocfilehash: 4123d71392f8b32df8d04033d85476cb18b39736
ms.sourcegitcommit: 3b1779890f828130a9d73aebf17ebffae511728f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/28/2020
ms.locfileid: "93273464"
---
# <a name="about-functions-advanced-parameters"></a><span data-ttu-id="5406c-104">Om functions avancerade parametrar</span><span class="sxs-lookup"><span data-stu-id="5406c-104">About Functions Advanced Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="5406c-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5406c-105">Short description</span></span>

<span data-ttu-id="5406c-106">Förklarar hur du lägger till parametrar till avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="5406c-106">Explains how to add parameters to advanced functions.</span></span>

## <a name="long-description"></a><span data-ttu-id="5406c-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="5406c-107">Long description</span></span>

<span data-ttu-id="5406c-108">Du kan lägga till parametrar till de avancerade funktioner som du skriver och använda parametriserade och-argument för att begränsa de parameter värden som användarna skickar med parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-108">You can add parameters to the advanced functions that you write, and use parameter attributes and arguments to limit the parameter values that function users submit with the parameter.</span></span>

<span data-ttu-id="5406c-109">De parametrar som du lägger till i din funktion är tillgängliga för användare utöver de vanliga parametrarna som PowerShell automatiskt lägger till i alla cmdletar och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="5406c-109">The parameters that you add to your function are available to users in addition to the common parameters that PowerShell adds automatically to all cmdlets and advanced functions.</span></span> <span data-ttu-id="5406c-110">Mer information om de gemensamma PowerShell-parametrarna finns i [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-110">For more information about the PowerShell common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="5406c-111">Från och med PowerShell 3,0 kan du använda ihopbuntning med `@Args` för att representera parametrarna i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="5406c-111">Beginning in PowerShell 3.0, you can use splatting with `@Args` to represent the parameters in a command.</span></span> <span data-ttu-id="5406c-112">Ihopbuntning är giltig för enkla och avancerade funktioner.</span><span class="sxs-lookup"><span data-stu-id="5406c-112">Splatting is valid on simple and advanced functions.</span></span> <span data-ttu-id="5406c-113">Mer information finns i [about_Functions](about_Functions.md) och [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-113">For more information, see [about_Functions](about_Functions.md) and [about_Splatting](about_Splatting.md).</span></span>

## <a name="type-conversion-of-parameter-values"></a><span data-ttu-id="5406c-114">Typ konvertering av parameter värden</span><span class="sxs-lookup"><span data-stu-id="5406c-114">Type conversion of parameter values</span></span>

<span data-ttu-id="5406c-115">När du anger strängar som argument för parametrar som förväntar sig en annan typ, konverterar PowerShell implicit strängarna till parameter måltypen.</span><span class="sxs-lookup"><span data-stu-id="5406c-115">When you supply strings as arguments to parameters that expect a different type, PowerShell implicitly converts the strings to the parameter target type.</span></span>
<span data-ttu-id="5406c-116">Avancerade funktioner utför konstruktor-invariant-parsning av parameter värden.</span><span class="sxs-lookup"><span data-stu-id="5406c-116">Advanced functions perform culture-invariant parsing of parameter values.</span></span>

<span data-ttu-id="5406c-117">En kultur känslig konvertering utförs däremot under parameter bindning för kompilerade cmdlets.</span><span class="sxs-lookup"><span data-stu-id="5406c-117">By contrast, a culture-sensitive conversion is performed during parameter binding for compiled cmdlets.</span></span>

<span data-ttu-id="5406c-118">I det här exemplet skapar vi en cmdlet och en skript funktion som tar en `[datetime]` parameter.</span><span class="sxs-lookup"><span data-stu-id="5406c-118">In this example, we create a cmdlet and a script function that take a `[datetime]` parameter.</span></span> <span data-ttu-id="5406c-119">Den aktuella kulturen ändras till att använda tyska inställningar.</span><span class="sxs-lookup"><span data-stu-id="5406c-119">The current culture is changed to use German settings.</span></span>
<span data-ttu-id="5406c-120">Ett tyskt formaterat datum skickas till parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-120">A German-formatted date is passed to the parameter.</span></span>

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

<span data-ttu-id="5406c-121">Som du ser ovan använder cmdlet: en kultur känslig parsning för att konvertera strängen.</span><span class="sxs-lookup"><span data-stu-id="5406c-121">As shown above, cmdlets use culture-sensitive parsing to convert the string.</span></span>

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

<span data-ttu-id="5406c-122">Avancerade funktioner använder kulturen-invariant-parsning, vilket resulterar i följande fel.</span><span class="sxs-lookup"><span data-stu-id="5406c-122">Advanced functions use culture-invariant parsing, which results in the following error.</span></span>

```Output
Get-Date_Func : Cannot process argument transformation on parameter 'Date'. Cannot convert
 value "19-06-2018" to type "System.DateTime". Error: "String was not recognized as a valid
 DateTime."
At line:13 char:15
+ Get-Date_Func $dateStr
+               ~~~~~~~~
    + CategoryInfo          : InvalidData: (:) [Get-Date_Func], ParameterBindingArgumentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Get-Date_Func
```

## <a name="static-parameters"></a><span data-ttu-id="5406c-123">Statiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5406c-123">Static parameters</span></span>

<span data-ttu-id="5406c-124">Statiska parametrar är parametrar som alltid är tillgängliga i funktionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-124">Static parameters are parameters that are always available in the function.</span></span>
<span data-ttu-id="5406c-125">De flesta parametrar i PowerShell-cmdletar och skript är statiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="5406c-125">Most parameters in PowerShell cmdlets and scripts are static parameters.</span></span>

<span data-ttu-id="5406c-126">I följande exempel visas en deklaration av en **computername** -parameter med följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="5406c-126">The following example shows the declaration of a **ComputerName** parameter that has the following characteristics:</span></span>

- <span data-ttu-id="5406c-127">Det är obligatoriskt (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="5406c-127">It's mandatory (required).</span></span>
- <span data-ttu-id="5406c-128">Det tar emot inmatade från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5406c-128">It takes input from the pipeline.</span></span>
- <span data-ttu-id="5406c-129">Det tar en matris med strängar som inmatade.</span><span class="sxs-lookup"><span data-stu-id="5406c-129">It takes an array of strings as input.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

## <a name="attributes-of-parameters"></a><span data-ttu-id="5406c-130">Attribut för parametrar</span><span class="sxs-lookup"><span data-stu-id="5406c-130">Attributes of parameters</span></span>

<span data-ttu-id="5406c-131">I det här avsnittet beskrivs de attribut som du kan lägga till i funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="5406c-131">This section describes the attributes that you can add to function parameters.</span></span>

<span data-ttu-id="5406c-132">Alla attribut är valfria.</span><span class="sxs-lookup"><span data-stu-id="5406c-132">All attributes are optional.</span></span> <span data-ttu-id="5406c-133">Men om du utelämnar attributet **CmdletBinding** , och sedan ska identifieras som en avancerad funktion, måste funktionen innehålla attributet- **parameter** .</span><span class="sxs-lookup"><span data-stu-id="5406c-133">However, if you omit the **CmdletBinding** attribute, then to be recognized as an advanced function, the function must include the **Parameter** attribute.</span></span>

<span data-ttu-id="5406c-134">Du kan lägga till ett eller flera attribut i varje parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="5406c-134">You can add one or multiple attributes in each parameter declaration.</span></span> <span data-ttu-id="5406c-135">Det finns ingen gräns för antalet attribut som du kan lägga till i en parameter deklaration.</span><span class="sxs-lookup"><span data-stu-id="5406c-135">There's no limit to the number of attributes that you can add to a parameter declaration.</span></span>

### <a name="parameter-attribute"></a><span data-ttu-id="5406c-136">Parameter-attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-136">Parameter attribute</span></span>

<span data-ttu-id="5406c-137">Attributet **parameter** används för att deklarera attributen för funktions parametrar.</span><span class="sxs-lookup"><span data-stu-id="5406c-137">The **Parameter** attribute is used to declare the attributes of function parameters.</span></span>

<span data-ttu-id="5406c-138">Attributet **parameter** är valfritt och du kan utelämna det om ingen av parametrarna för dina funktioner behöver attribut.</span><span class="sxs-lookup"><span data-stu-id="5406c-138">The **Parameter** attribute is optional, and you can omit it if none of the parameters of your functions need attributes.</span></span> <span data-ttu-id="5406c-139">Men för att kunna identifieras som en avancerad funktion, i stället för en enkel funktion, måste en funktion ha antingen attributet **CmdletBinding** eller attributet **parameter** eller båda.</span><span class="sxs-lookup"><span data-stu-id="5406c-139">But, to be recognized as an advanced function, rather than a simple function, a function must have either the **CmdletBinding** attribute or the **Parameter** attribute, or both.</span></span>

<span data-ttu-id="5406c-140">Attributet **parameter** innehåller argument som definierar parameterns egenskaper, till exempel om parametern är obligatorisk eller valfri.</span><span class="sxs-lookup"><span data-stu-id="5406c-140">The **Parameter** attribute has arguments that define the characteristics of the parameter, such as whether the parameter is mandatory or optional.</span></span>

<span data-ttu-id="5406c-141">Använd följande syntax för att deklarera **parameter** -attributet, ett argument och ett argument värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-141">Use the following syntax to declare the **Parameter** attribute, an argument, and an argument value.</span></span> <span data-ttu-id="5406c-142">De parenteser som omger argumentet och dess värde måste följa **parametern** utan något mellanliggande blank steg.</span><span class="sxs-lookup"><span data-stu-id="5406c-142">The parentheses that enclose the argument and its value must follow **Parameter** with no intervening space.</span></span>

```powershell
Param(
    [Parameter(Argument=value)]
    $ParameterName
)
```

<span data-ttu-id="5406c-143">Använd kommatecken för att avgränsa argument inom parentes.</span><span class="sxs-lookup"><span data-stu-id="5406c-143">Use commas to separate arguments within the parentheses.</span></span> <span data-ttu-id="5406c-144">Använd följande syntax för att deklarera två argument för attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="5406c-144">Use the following syntax to declare two arguments of the **Parameter** attribute.</span></span>

```powershell
Param(
    [Parameter(Argument1=value1,
    Argument2=value2)]
)
```

<span data-ttu-id="5406c-145">De booleska argument typerna för **parametern** attribut är **false** när de utelämnas från attributet **parameter** .</span><span class="sxs-lookup"><span data-stu-id="5406c-145">The boolean argument types of the **Parameter** attribute default to **False** when omitted from the **Parameter** attribute.</span></span> <span data-ttu-id="5406c-146">Ange värdet för argumentet till `$true` eller bara lista argumentet efter namn.</span><span class="sxs-lookup"><span data-stu-id="5406c-146">Set the argument value to `$true` or just list the argument by name.</span></span> <span data-ttu-id="5406c-147">Följande **parameter** -attribut är till exempel likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="5406c-147">For example, the following **Parameter** attributes are equivalent.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
)

# Boolean arguments can be defined using this shorthand syntax

Param(
    [Parameter(Mandatory)]
)
```

<span data-ttu-id="5406c-148">Om du använder **parameter** -attributet utan argument, som ett alternativ till att använda attributet **CmdletBinding** , krävs fortfarande de parenteser som följer attributnamnet.</span><span class="sxs-lookup"><span data-stu-id="5406c-148">If you use the **Parameter** attribute without arguments, as an alternative to using the **CmdletBinding** attribute, the parentheses that follow the attribute name are still required.</span></span>

```powershell
Param(
    [Parameter()]
    $ParameterName
)
```

#### <a name="mandatory-argument"></a><span data-ttu-id="5406c-149">Obligatoriskt argument</span><span class="sxs-lookup"><span data-stu-id="5406c-149">Mandatory argument</span></span>

<span data-ttu-id="5406c-150">`Mandatory`Argumentet anger att parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5406c-150">The `Mandatory` argument indicates that the parameter is required.</span></span> <span data-ttu-id="5406c-151">Om det här argumentet inte anges är parametern valfri.</span><span class="sxs-lookup"><span data-stu-id="5406c-151">If this argument isn't specified, the parameter is optional.</span></span>

<span data-ttu-id="5406c-152">I följande exempel deklareras parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="5406c-152">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="5406c-153">`Mandatory`Argumentet används för att göra parametern obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5406c-153">It uses the `Mandatory` argument to make the parameter mandatory.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="position-argument"></a><span data-ttu-id="5406c-154">Positions argument</span><span class="sxs-lookup"><span data-stu-id="5406c-154">Position argument</span></span>

<span data-ttu-id="5406c-155">`Position`Argumentet avgör om parameter namnet krävs när parametern används i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="5406c-155">The `Position` argument determines whether the parameter name is required when the parameter is used in a command.</span></span> <span data-ttu-id="5406c-156">När en parameter deklaration innehåller `Position` argumentet, kan parameter namnet utelämnas och PowerShell identifierar det namnlösa parametervärdet med dess position, eller ordning, i listan över namnlösa parameter värden i kommandot.</span><span class="sxs-lookup"><span data-stu-id="5406c-156">When a parameter declaration includes the `Position` argument, the parameter name can be omitted and PowerShell identifies the unnamed parameter value by its position, or order, in the list of unnamed parameter values in the command.</span></span>

<span data-ttu-id="5406c-157">Om `Position` argumentet inte anges måste parameter namnet eller ett alias eller en förkortning för parameter namn föregå parametervärdet när parametern används i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="5406c-157">If the `Position` argument isn't specified, the parameter name, or a parameter name alias or abbreviation, must precede the parameter value whenever the parameter is used in a command.</span></span>

<span data-ttu-id="5406c-158">Som standard är alla funktions parametrar placerade i position.</span><span class="sxs-lookup"><span data-stu-id="5406c-158">By default, all function parameters are positional.</span></span> <span data-ttu-id="5406c-159">PowerShell tilldelar positions nummer till parametrar i den ordning som parametrarna deklareras i funktionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-159">PowerShell assigns position numbers to parameters in the order in which the parameters are declared in the function.</span></span> <span data-ttu-id="5406c-160">Om du vill inaktivera den här funktionen ställer du in värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** till `$False` .</span><span class="sxs-lookup"><span data-stu-id="5406c-160">To disable this feature, set the value of the `PositionalBinding` argument of the **CmdletBinding** attribute to `$False`.</span></span> <span data-ttu-id="5406c-161">`Position`Argumentet prioriteras över värdet för `PositionalBinding` argumentet för attributet **CmdletBinding** .</span><span class="sxs-lookup"><span data-stu-id="5406c-161">The `Position` argument takes precedence over the value of the `PositionalBinding` argument of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="5406c-162">Mer information finns `PositionalBinding` i i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-162">For more information, see `PositionalBinding` in [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>

<span data-ttu-id="5406c-163">Värdet för `Position` argumentet anges som ett heltal.</span><span class="sxs-lookup"><span data-stu-id="5406c-163">The value of the `Position` argument is specified as an integer.</span></span> <span data-ttu-id="5406c-164">Position svärdet **0** representerar den första positionen i kommandot, ett positions värde på **1** representerar den andra positionen i kommandot och så vidare.</span><span class="sxs-lookup"><span data-stu-id="5406c-164">A position value of **0** represents the first position in the command, a position value of **1** represents the second position in the command, and so on.</span></span>

<span data-ttu-id="5406c-165">Om en funktion inte har några positions parametrar tilldelar PowerShell positioner till varje parameter baserat på i vilken ordning parametrarna deklareras.</span><span class="sxs-lookup"><span data-stu-id="5406c-165">If a function has no positional parameters, PowerShell assigns positions to each parameter based on the order in which the parameters are declared.</span></span>
<span data-ttu-id="5406c-166">Vi rekommenderar dock inte att du använder den här tilldelningen.</span><span class="sxs-lookup"><span data-stu-id="5406c-166">However, as a best practice, don't rely on this assignment.</span></span> <span data-ttu-id="5406c-167">Använd argumentet om du vill att parametrar ska placeras i position `Position` .</span><span class="sxs-lookup"><span data-stu-id="5406c-167">When you want parameters to be positional, use the `Position` argument.</span></span>

<span data-ttu-id="5406c-168">I följande exempel deklareras parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="5406c-168">The following example declares the **ComputerName** parameter.</span></span> <span data-ttu-id="5406c-169">`Position`Argumentet använder argumentet med värdet **0**.</span><span class="sxs-lookup"><span data-stu-id="5406c-169">It uses the `Position` argument with a value of **0**.</span></span> <span data-ttu-id="5406c-170">Det innebär att när `-ComputerName` har utelämnats från kommandot måste dess värde vara det första eller det enda parameter värde som inte är namn i kommandot.</span><span class="sxs-lookup"><span data-stu-id="5406c-170">As a result, when `-ComputerName` is omitted from command, its value must be the first or only unnamed parameter value in the command.</span></span>

```powershell
Param(
    [Parameter(Position=0)]
    [String[]]
    $ComputerName
)
```

#### <a name="parametersetname-argument"></a><span data-ttu-id="5406c-171">ParameterSetName-argument</span><span class="sxs-lookup"><span data-stu-id="5406c-171">ParameterSetName argument</span></span>

<span data-ttu-id="5406c-172">`ParameterSetName`Argumentet anger den parameter som en parameter tillhör.</span><span class="sxs-lookup"><span data-stu-id="5406c-172">The `ParameterSetName` argument specifies the parameter set to which a parameter belongs.</span></span> <span data-ttu-id="5406c-173">Om ingen parameter uppsättning anges, tillhör parametern alla parameter uppsättningar som definieras av funktionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-173">If no parameter set is specified, the parameter belongs to all the parameter sets defined by the function.</span></span> <span data-ttu-id="5406c-174">För att vara unik måste därför varje parameter uppsättning ha minst en parameter som inte är medlem i någon annan parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="5406c-174">Therefore, to be unique, each parameter set must have at least one parameter that isn't a member of any other parameter set.</span></span>

> [!NOTE]
> <span data-ttu-id="5406c-175">För en cmdlet eller funktion finns det en gräns på 32 parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="5406c-175">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

<span data-ttu-id="5406c-176">I följande exempel deklareras en **computername** -parameter i `Computer` parameter uppsättningen, en **username** -parameter i `User` parameter uppsättningen och en **sammanfattnings** parameter i båda parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="5406c-176">The following example declares a **ComputerName** parameter in the `Computer` parameter set, a **UserName** parameter in the `User` parameter set, and a **Summary** parameter in both parameter sets.</span></span>

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

<span data-ttu-id="5406c-177">Du kan bara ange ett `ParameterSetName` värde i varje argument och bara ett `ParameterSetName` argument i varje **parameter** -attribut.</span><span class="sxs-lookup"><span data-stu-id="5406c-177">You can specify only one `ParameterSetName` value in each argument and only one `ParameterSetName` argument in each **Parameter** attribute.</span></span> <span data-ttu-id="5406c-178">Om du vill ange att en parameter visas i mer än en parameter uppsättning lägger du till ytterligare **parameter** -attribut.</span><span class="sxs-lookup"><span data-stu-id="5406c-178">To indicate that a parameter appears in more than one parameter set, add additional **Parameter** attributes.</span></span>

<span data-ttu-id="5406c-179">I följande exempel lägger du uttryckligen till **sammanfattnings** parametern `Computer` i `User` parameter uppsättningarna och.</span><span class="sxs-lookup"><span data-stu-id="5406c-179">The following example explicitly adds the **Summary** parameter to the `Computer` and `User` parameter sets.</span></span> <span data-ttu-id="5406c-180">**Sammanfattnings** parametern är valfri i `Computer` parameter uppsättningen och obligatorisk i `User` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5406c-180">The **Summary** parameter is optional in the `Computer` parameter set and mandatory in the `User` parameter set.</span></span>

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

<span data-ttu-id="5406c-181">Mer information om parameter uppsättningar finns i [About parameter set](about_parameter_sets.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-181">For more information about parameter sets, see [About Parameter Sets](about_parameter_sets.md).</span></span>

#### <a name="valuefrompipeline-argument"></a><span data-ttu-id="5406c-182">ValueFromPipeline-argument</span><span class="sxs-lookup"><span data-stu-id="5406c-182">ValueFromPipeline argument</span></span>

<span data-ttu-id="5406c-183">`ValueFromPipeline`Argumentet anger att parametern accepterar inmatade objekt från ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="5406c-183">The `ValueFromPipeline` argument indicates that the parameter accepts input from a pipeline object.</span></span> <span data-ttu-id="5406c-184">Ange det här argumentet om funktionen accepterar hela objektet, inte bara en egenskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="5406c-184">Specify this argument if the function accepts the entire object, not just a property of the object.</span></span>

<span data-ttu-id="5406c-185">I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar ett objekt som skickas till funktionen från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5406c-185">The following example declares a **ComputerName** parameter that's mandatory and accepts an object that's passed to the function from the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipeline=$true)]
    [String[]]
    $ComputerName
)
```

#### <a name="valuefrompipelinebypropertyname-argument"></a><span data-ttu-id="5406c-186">ValueFromPipelineByPropertyName-argument</span><span class="sxs-lookup"><span data-stu-id="5406c-186">ValueFromPipelineByPropertyName argument</span></span>

<span data-ttu-id="5406c-187">`ValueFromPipelineByPropertyName`Argumentet anger att parametern accepterar inmatade objekt från en egenskap i ett pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="5406c-187">The `ValueFromPipelineByPropertyName` argument indicates that the parameter accepts input from a property of a pipeline object.</span></span> <span data-ttu-id="5406c-188">Objekt egenskapen måste ha samma namn eller alias som parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-188">The object property must have the same name or alias as the parameter.</span></span>

<span data-ttu-id="5406c-189">Om funktionen till exempel har en **computername** -parameter och skickas-objektet har egenskapen **computername** , tilldelas värdet för egenskapen **computername** till funktionens **computername** -parameter.</span><span class="sxs-lookup"><span data-stu-id="5406c-189">For example, if the function has a **ComputerName** parameter, and the piped object has a **ComputerName** property, the value of the **ComputerName** property is assigned to the function's **ComputerName** parameter.</span></span>

<span data-ttu-id="5406c-190">I följande exempel deklareras en **computername** -parameter som är obligatorisk och accepterar indatamängden från objektets **computername** -egenskap som skickas till funktionen via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5406c-190">The following example declares a **ComputerName** parameter that's mandatory and accepts input from the object's **ComputerName** property that's passed to the function through the pipeline.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    ValueFromPipelineByPropertyName=$true)]
    [String[]]
    $ComputerName
)
```

> [!NOTE]
> <span data-ttu-id="5406c-191">En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken _Delay-bind_ i parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-191">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of _delay-bind_ script blocks on the parameter.</span></span>
>
> <span data-ttu-id="5406c-192">Skript blocket _Delay-bind_ körs automatiskt under **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="5406c-192">The _delay-bind_ script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="5406c-193">Resultatet är kopplat till parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-193">The result is bound to the parameter.</span></span> <span data-ttu-id="5406c-194">Fördröjd bindning fungerar inte för parametrar som definierats som typ `ScriptBlock` eller `System.Object` .</span><span class="sxs-lookup"><span data-stu-id="5406c-194">Delay binding does not work for parameters defined as type `ScriptBlock` or `System.Object`.</span></span> <span data-ttu-id="5406c-195">Skript blocket skickas genom _utan_ att anropas.</span><span class="sxs-lookup"><span data-stu-id="5406c-195">The script block is passed through _without_ being invoked.</span></span>
>
> <span data-ttu-id="5406c-196">Du kan läsa mer om _fördröjning – binda_ skript block här [about_Script_Blocks. MD](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-196">You can read about _delay-bind_ script blocks here [about_Script_Blocks.md](about_Script_Blocks.md).</span></span>

#### <a name="valuefromremainingarguments-argument"></a><span data-ttu-id="5406c-197">ValueFromRemainingArguments-argument</span><span class="sxs-lookup"><span data-stu-id="5406c-197">ValueFromRemainingArguments argument</span></span>

<span data-ttu-id="5406c-198">`ValueFromRemainingArguments`Argumentet anger att parametern accepterar alla parameter värden i kommandot som inte har tilldelats andra parametrar för funktionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-198">The `ValueFromRemainingArguments` argument indicates that the parameter accepts all the parameter's values in the command that aren't assigned to other parameters of the function.</span></span>

<span data-ttu-id="5406c-199">Det finns ett känt problem med att använda samlingar med **ValueFromRemainingArguments** där den överförda samlingen behandlas som ett enda element.</span><span class="sxs-lookup"><span data-stu-id="5406c-199">There's a known issue for using collections with **ValueFromRemainingArguments** where the passed-in collection is treated as a single element.</span></span>

<span data-ttu-id="5406c-200">Följande exempel visar det här kända problemet.</span><span class="sxs-lookup"><span data-stu-id="5406c-200">The following example demonstrates this known issue.</span></span> <span data-ttu-id="5406c-201">Den **återstående** parametern ska innehålla **en** vid **index 0** och **två** vid **index 1**.</span><span class="sxs-lookup"><span data-stu-id="5406c-201">The **Remaining** parameter should contain **one** at **index 0** and **two** at **index 1**.</span></span>
<span data-ttu-id="5406c-202">I stället kombineras båda elementen i en enda entitet.</span><span class="sxs-lookup"><span data-stu-id="5406c-202">Instead, both elements are combined into a single entity.</span></span>

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
Found 1 elements
0: one two
```

> [!NOTE]
> <span data-ttu-id="5406c-203">Det här problemet har lösts i PowerShell 6,2.</span><span class="sxs-lookup"><span data-stu-id="5406c-203">This issue is resolved in PowerShell 6.2.</span></span>

#### <a name="helpmessage-argument"></a><span data-ttu-id="5406c-204">HelpMessage-argument</span><span class="sxs-lookup"><span data-stu-id="5406c-204">HelpMessage argument</span></span>

<span data-ttu-id="5406c-205">`HelpMessage`Argumentet anger en sträng som innehåller en kort beskrivning av parametern eller dess värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-205">The `HelpMessage` argument specifies a string that contains a brief description of the parameter or its value.</span></span> <span data-ttu-id="5406c-206">PowerShell visar det här meddelandet i den prompt som visas när ett nödvändigt parameter värde saknas i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="5406c-206">PowerShell displays this message in the prompt that appears when a mandatory parameter value is missing from a command.</span></span> <span data-ttu-id="5406c-207">Det här argumentet har ingen påverkan på valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="5406c-207">This argument has no effect on optional parameters.</span></span>

<span data-ttu-id="5406c-208">I följande exempel deklareras en obligatorisk **computername** -parameter och ett hjälp meddelande som förklarar det förväntade parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="5406c-208">The following example declares a mandatory **ComputerName** parameter and a help message that explains the expected parameter value.</span></span>

<span data-ttu-id="5406c-209">Om det inte finns någon annan [kommenterings-baserad hjälpfil](./about_comment_based_help.md) för funktionen (till exempel `.SYNOPSIS` ) visas även det här meddelandet i `Get-Help` utdata.</span><span class="sxs-lookup"><span data-stu-id="5406c-209">If there is no other [comment-based help](./about_comment_based_help.md) syntax for the function (for example, `.SYNOPSIS`) then this message also shows up in `Get-Help` output.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true,
    HelpMessage="Enter one or more computer names separated by commas.")]
    [String[]]
    $ComputerName
)
```

### <a name="alias-attribute"></a><span data-ttu-id="5406c-210">Alias-attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-210">Alias attribute</span></span>

<span data-ttu-id="5406c-211">Attributet **alias** upprättar ett alternativt namn för parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-211">The **Alias** attribute establishes an alternate name for the parameter.</span></span>
<span data-ttu-id="5406c-212">Det finns ingen gräns för antalet alias som du kan tilldela till en parameter.</span><span class="sxs-lookup"><span data-stu-id="5406c-212">There's no limit to the number of aliases that you can assign to a parameter.</span></span>

<span data-ttu-id="5406c-213">I följande exempel visas en parameter deklaration som lägger till **CN** -och **MachineName** -alias till den obligatoriska **computername** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-213">The following example shows a parameter declaration that adds the **CN** and **MachineName** aliases to the mandatory **ComputerName** parameter.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [Alias("CN","MachineName")]
    [String[]]
    $ComputerName
)
```

### <a name="supportswildcards-attribute"></a><span data-ttu-id="5406c-214">SupportsWildcards-attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-214">SupportsWildcards attribute</span></span>

<span data-ttu-id="5406c-215">Attributet **SupportsWildcards** används för att indikera att parametern accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-215">The **SupportsWildcards** attribute is used to indicate that the parameter accepts wildcard values.</span></span> <span data-ttu-id="5406c-216">I följande exempel visas en parameter deklaration för en obligatorisk **Sök vägs** parameter som stöder jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-216">The following example shows a parameter declaration for a mandatory **Path** parameter that supports wildcard values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [SupportsWildcards()]
    [String[]]
    $Path
)
```

<span data-ttu-id="5406c-217">Om du använder det här attributet aktive ras inte stöd för jokertecken automatiskt.</span><span class="sxs-lookup"><span data-stu-id="5406c-217">Using this attribute does not automatically enable wildcard support.</span></span> <span data-ttu-id="5406c-218">Cmdlet-utvecklaren måste implementera koden för att hantera jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-218">The cmdlet developer must implement the code to handle the wildcard input.</span></span> <span data-ttu-id="5406c-219">Vilka jokertecken som stöds kan variera beroende på underliggande API eller PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="5406c-219">The wildcards supported can vary according to the underlying API or PowerShell provider.</span></span> <span data-ttu-id="5406c-220">Mer information finns i [about_Wildcards](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-220">For more information, see [about_Wildcards](about_Wildcards.md).</span></span>

### <a name="parameter-and-variable-validation-attributes"></a><span data-ttu-id="5406c-221">Attribut för parameter-och variabel verifiering</span><span class="sxs-lookup"><span data-stu-id="5406c-221">Parameter and variable validation attributes</span></span>

<span data-ttu-id="5406c-222">Validera attribut Direct PowerShell för att testa de parameter värden som användarna skickar när de anropar funktionen Advanced.</span><span class="sxs-lookup"><span data-stu-id="5406c-222">Validation attributes direct PowerShell to test the parameter values that users submit when they call the advanced function.</span></span> <span data-ttu-id="5406c-223">Om parameter värden inte fungerar som testet, genereras ett fel och funktionen anropas inte.</span><span class="sxs-lookup"><span data-stu-id="5406c-223">If the parameter values fail the test, an error is generated and the function isn't called.</span></span> <span data-ttu-id="5406c-224">Parameter verifiering tillämpas endast på angivna indata och andra värden som standardvärden är inte verifierade.</span><span class="sxs-lookup"><span data-stu-id="5406c-224">Parameter validation is only applied to the input provided and any other values like default values are not validated.</span></span>

<span data-ttu-id="5406c-225">Du kan också använda verifierings-attributen för att begränsa de värden som användarna kan ange för variabler.</span><span class="sxs-lookup"><span data-stu-id="5406c-225">You can also use the validation attributes to restrict the values that users can specify for variables.</span></span> <span data-ttu-id="5406c-226">När du använder en typ konverterare tillsammans med ett verifierings attribut måste typ konverteraren definieras före-attributet.</span><span class="sxs-lookup"><span data-stu-id="5406c-226">When you use a type converter along with a validation attribute, the type converter has to be defined before the attribute.</span></span>

```powershell
[int32][AllowNull()] $number = 7
```

### <a name="allownull-validation-attribute"></a><span data-ttu-id="5406c-227">AllowNull-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-227">AllowNull validation attribute</span></span>

<span data-ttu-id="5406c-228">Attributet **AllowNull** tillåter att värdet för en obligatorisk parameter ska vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="5406c-228">The **AllowNull** attribute allows the value of a mandatory parameter to be `$null`.</span></span> <span data-ttu-id="5406c-229">I följande exempel deklareras en hash- **ComputerInfo** -parameter som kan ha ett **Null** -värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-229">The following example declares a hashtable **ComputerInfo** parameter that can have a **null** value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowNull()]
    [hashtable]
    $ComputerInfo
)
```

> [!NOTE]
> <span data-ttu-id="5406c-230">Attributet **AllowNull** fungerar inte om typ konverteraren är inställd på sträng eftersom sträng typen inte accepterar ett null-värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-230">The **AllowNull** attribute doesn't work if the type converter is set to string as the string type will not accept a null value.</span></span> <span data-ttu-id="5406c-231">Du kan använda attributet **AllowEmptyString** för det här scenariot.</span><span class="sxs-lookup"><span data-stu-id="5406c-231">You can use the **AllowEmptyString** attribute for this scenario.</span></span>

### <a name="allowemptystring-validation-attribute"></a><span data-ttu-id="5406c-232">AllowEmptyString-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-232">AllowEmptyString validation attribute</span></span>

<span data-ttu-id="5406c-233">Attributet **AllowEmptyString** tillåter att värdet för en obligatorisk parameter är en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="5406c-233">The **AllowEmptyString** attribute allows the value of a mandatory parameter to be an empty string (`""`).</span></span> <span data-ttu-id="5406c-234">I följande exempel deklareras en **computername** -parameter som kan ha ett tomt sträng värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-234">The following example declares a **ComputerName** parameter that can have an empty string value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyString()]
    [String]
    $ComputerName
)
```

### <a name="allowemptycollection-validation-attribute"></a><span data-ttu-id="5406c-235">AllowEmptyCollection-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-235">AllowEmptyCollection validation attribute</span></span>

<span data-ttu-id="5406c-236">Attributet **AllowEmptyCollection** tillåter att värdet för en obligatorisk parameter är en tom samling `@()` .</span><span class="sxs-lookup"><span data-stu-id="5406c-236">The **AllowEmptyCollection** attribute allows the value of a mandatory parameter to be an empty collection `@()`.</span></span> <span data-ttu-id="5406c-237">I följande exempel deklareras en **computername** -parameter som kan ha ett tomt samlings värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-237">The following example declares a **ComputerName** parameter that can have an empty collection value.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [AllowEmptyCollection()]
    [String[]]
    $ComputerName
)
```

### <a name="validatecount-validation-attribute"></a><span data-ttu-id="5406c-238">ValidateCount-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-238">ValidateCount validation attribute</span></span>

<span data-ttu-id="5406c-239">Attributet **ValidateCount** anger det lägsta och högsta antalet parameter värden som en parameter accepterar.</span><span class="sxs-lookup"><span data-stu-id="5406c-239">The **ValidateCount** attribute specifies the minimum and maximum number of parameter values that a parameter accepts.</span></span> <span data-ttu-id="5406c-240">PowerShell genererar ett fel om antalet parameter värden i kommandot som anropar funktionen ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="5406c-240">PowerShell generates an error if the number of parameter values in the command that calls the function is outside that range.</span></span>

<span data-ttu-id="5406c-241">Följande parameter deklaration skapar en **computername** -parameter som tar en till fem parameter värden.</span><span class="sxs-lookup"><span data-stu-id="5406c-241">The following parameter declaration creates a **ComputerName** parameter that takes one to five parameter values.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateCount(1,5)]
    [String[]]
    $ComputerName
)
```

### <a name="validatelength-validation-attribute"></a><span data-ttu-id="5406c-242">ValidateLength-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-242">ValidateLength validation attribute</span></span>

<span data-ttu-id="5406c-243">Attributet **ValidateLength** anger det lägsta och högsta antalet tecken i en parameter eller ett variabel värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-243">The **ValidateLength** attribute specifies the minimum and maximum number of characters in a parameter or variable value.</span></span> <span data-ttu-id="5406c-244">PowerShell genererar ett fel om längden på ett värde som har angetts för en parameter eller en variabel ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="5406c-244">PowerShell generates an error if the length of a value specified for a parameter or a variable is outside of the range.</span></span>

<span data-ttu-id="5406c-245">I följande exempel måste varje dator namn ha ett till tio tecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-245">In the following example, each computer name must have one to ten characters.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateLength(1,10)]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="5406c-246">I följande exempel måste värdet för variabeln `$number` vara minst ett tecken långt och högst tio tecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-246">In the following example, the value of the variable `$number` must be a minimum of one character in length, and a maximum of ten characters.</span></span>

```powershell
[Int32][ValidateLength(1,10)]$number = '01'
```

> [!NOTE]
> <span data-ttu-id="5406c-247">I det här exemplet är värdet för `01` inkapslat i enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-247">In this example, the value of `01` is wrapped in single quotes.</span></span> <span data-ttu-id="5406c-248">**ValidateLength** -attributet accepterar inte ett tal utan att de omges av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5406c-248">The **ValidateLength** attribute won't accept a number without being wrapped in quotes.</span></span>

### <a name="validatepattern-validation-attribute"></a><span data-ttu-id="5406c-249">ValidatePattern-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-249">ValidatePattern validation attribute</span></span>

<span data-ttu-id="5406c-250">Attributet **ValidatePattern** anger ett reguljärt uttryck som jämförs med parametern eller variabeln värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-250">The **ValidatePattern** attribute specifies a regular expression that's compared to the parameter or variable value.</span></span> <span data-ttu-id="5406c-251">PowerShell genererar ett fel om värdet inte matchar mönstret för reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="5406c-251">PowerShell generates an error if the value doesn't match the regular expression pattern.</span></span>

<span data-ttu-id="5406c-252">I följande exempel måste parametervärdet innehålla ett fyrsiffrigt tal och varje siffra måste vara ett tal mellan noll och nio.</span><span class="sxs-lookup"><span data-stu-id="5406c-252">In the following example, the parameter value must contain a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidatePattern("[0-9][0-9][0-9][0-9]")]
    [String[]]
    $ComputerName
)
```

<span data-ttu-id="5406c-253">I följande exempel måste värdet för variabeln `$number` vara exakt ett fyrsiffrigt tal och varje siffra måste vara ett tal från noll till nio.</span><span class="sxs-lookup"><span data-stu-id="5406c-253">In the following example, the value of the variable `$number` must be exactly a four-digit number, and each digit must be a number zero to nine.</span></span>

```powershell
[Int32][ValidatePattern("^[0-9][0-9][0-9][0-9]$")]$number = 1111
```

### <a name="validaterange-validation-attribute"></a><span data-ttu-id="5406c-254">ValidateRange-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-254">ValidateRange validation attribute</span></span>

<span data-ttu-id="5406c-255">Attributet **ValidateRange** anger ett numeriskt intervall för varje parameter eller variabel värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-255">The **ValidateRange** attribute specifies a numeric range for each parameter or variable value.</span></span> <span data-ttu-id="5406c-256">PowerShell genererar ett fel om ett värde ligger utanför intervallet.</span><span class="sxs-lookup"><span data-stu-id="5406c-256">PowerShell generates an error if any value is outside that range.</span></span> <span data-ttu-id="5406c-257">I följande exempel måste värdet **för parametern** Parameters vara mellan noll och tio.</span><span class="sxs-lookup"><span data-stu-id="5406c-257">In the following example, the value of the **Attempts** parameter must be between zero and ten.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateRange(0,10)]
    [Int]
    $Attempts
)
```

<span data-ttu-id="5406c-258">I följande exempel måste värdet för variabeln `$number` vara mellan noll och tio.</span><span class="sxs-lookup"><span data-stu-id="5406c-258">In the following example, the value of the variable `$number` must be between zero and ten.</span></span>

```powershell
[Int32][ValidateRange(0,10)]$number = 5
```

### <a name="validatescript-validation-attribute"></a><span data-ttu-id="5406c-259">ValidateScript-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-259">ValidateScript validation attribute</span></span>

<span data-ttu-id="5406c-260">Attributet **ValidateScript** anger ett skript som används för att validera en parameter eller ett variabel värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-260">The **ValidateScript** attribute specifies a script that is used to validate a parameter or variable value.</span></span> <span data-ttu-id="5406c-261">PowerShell rör värdet i skriptet och genererar ett fel om skriptet returnerar `$false` eller om skriptet genererar ett undantag.</span><span class="sxs-lookup"><span data-stu-id="5406c-261">PowerShell pipes the value to the script, and generates an error if the script returns `$false` or if the script throws an exception.</span></span>

<span data-ttu-id="5406c-262">När du använder attributet **ValidateScript** mappas värdet som verifieras till `$_` variabeln.</span><span class="sxs-lookup"><span data-stu-id="5406c-262">When you use the **ValidateScript** attribute, the value that's being validated is mapped to the `$_` variable.</span></span> <span data-ttu-id="5406c-263">Du kan använda `$_` variabeln för att referera till värdet i skriptet.</span><span class="sxs-lookup"><span data-stu-id="5406c-263">You can use the `$_` variable to refer to the value in the script.</span></span>

<span data-ttu-id="5406c-264">I följande exempel måste värdet för parametern **EventDate** vara större än eller lika med det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="5406c-264">In the following example, the value of the **EventDate** parameter must be greater than or equal to the current date.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateScript({$_ -ge (Get-Date)})]
    [DateTime]
    $EventDate
)
```

<span data-ttu-id="5406c-265">I följande exempel måste värdet för variabeln `$date` vara större än eller lika med aktuellt datum och tid.</span><span class="sxs-lookup"><span data-stu-id="5406c-265">In the following example, the value of the variable `$date` must be greater than or equal to the current date and time.</span></span>

```powershell
[DateTime][ValidateScript({$_ -ge (Get-Date)})]$date = (Get-Date)
```

> [!NOTE]
> <span data-ttu-id="5406c-266">Om du använder **ValidateScript** kan du inte skicka ett `$null` värde till parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-266">If you use **ValidateScript** , you cannot pass a `$null` value to the parameter.</span></span> <span data-ttu-id="5406c-267">När du skickar ett null-värde kan **ValidateScript** inte validera argumentet.</span><span class="sxs-lookup"><span data-stu-id="5406c-267">When you pass a null value **ValidateScript** can't validate the argument.</span></span>

### <a name="validateset-attribute"></a><span data-ttu-id="5406c-268">ValidateSet-attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-268">ValidateSet attribute</span></span>

<span data-ttu-id="5406c-269">Attributet **ValidateSet** anger en uppsättning giltiga värden för en parameter eller en variabel och möjliggör slut för ande av tabbar.</span><span class="sxs-lookup"><span data-stu-id="5406c-269">The **ValidateSet** attribute specifies a set of valid values for a parameter or variable and enables tab completion.</span></span> <span data-ttu-id="5406c-270">PowerShell genererar ett fel om en parameter eller ett variabel värde inte matchar ett värde i mängden.</span><span class="sxs-lookup"><span data-stu-id="5406c-270">PowerShell generates an error if a parameter or variable value doesn't match a value in the set.</span></span> <span data-ttu-id="5406c-271">I följande exempel kan värdet för **detalj** parametern endast vara låg, genomsnitt eller hög.</span><span class="sxs-lookup"><span data-stu-id="5406c-271">In the following example, the value of the **Detail** parameter can only be Low, Average, or High.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateSet("Low", "Average", "High")]
    [String[]]
    $Detail
)
```

<span data-ttu-id="5406c-272">I följande exempel måste värdet för variabeln `$flavor` vara choklad, Strawberry eller vanilj.</span><span class="sxs-lookup"><span data-stu-id="5406c-272">In the following example, the value of the variable `$flavor` must be either Chocolate, Strawberry, or Vanilla.</span></span>

```powershell
[ValidateSet("Chocolate", "Strawberry", "Vanilla")]
[String]$flavor = "Strawberry"
```

<span data-ttu-id="5406c-273">Verifieringen sker när variabeln tilldelas även inom skriptet.</span><span class="sxs-lookup"><span data-stu-id="5406c-273">The validation occurs whenever that variable is assigned even within the script.</span></span> <span data-ttu-id="5406c-274">Följande resulterar exempelvis i ett fel vid körning:</span><span class="sxs-lookup"><span data-stu-id="5406c-274">For example, the following results in an error at runtime:</span></span>

```powershell
Param(
    [ValidateSet("hello", "world")]
    [String]$Message
)

$Message = "bye"
```

### <a name="validatenotnull-validation-attribute"></a><span data-ttu-id="5406c-275">ValidateNotNull-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-275">ValidateNotNull validation attribute</span></span>

<span data-ttu-id="5406c-276">Attributet **ValidateNotNull** anger att parametervärdet får inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="5406c-276">The **ValidateNotNull** attribute specifies that the parameter value can't be `$null`.</span></span> <span data-ttu-id="5406c-277">PowerShell genererar ett fel om parametervärdet är `$null` .</span><span class="sxs-lookup"><span data-stu-id="5406c-277">PowerShell generates an error if the parameter value is `$null`.</span></span>

<span data-ttu-id="5406c-278">Attributet **ValidateNotNull** är utformat för användning när parametern är valfri och typen är odefinierad eller har en typ konverterare som inte kan implicit konvertera ett null-värde som- **objekt**.</span><span class="sxs-lookup"><span data-stu-id="5406c-278">The **ValidateNotNull** attribute is designed to be used when the parameter is optional and the type is undefined or has a type converter that can't implicitly convert a null value like **object**.</span></span> <span data-ttu-id="5406c-279">Om du anger en typ som implicit ska konvertera ett null-värde, till exempel en **sträng** , konverteras värdet null till en tom sträng även när du använder attributet **ValidateNotNull** .</span><span class="sxs-lookup"><span data-stu-id="5406c-279">If you specify a type that that will implicitly convert a null value such as a **string** , the null value is converted to an empty string even when using the **ValidateNotNull** attribute.</span></span> <span data-ttu-id="5406c-280">För det här scenariot använder du **ValidateNotNullOrEmpty**</span><span class="sxs-lookup"><span data-stu-id="5406c-280">For this scenario use the **ValidateNotNullOrEmpty**</span></span>

<span data-ttu-id="5406c-281">I följande exempel kan värdet för **ID-** parametern inte vara `$null` .</span><span class="sxs-lookup"><span data-stu-id="5406c-281">In the following example, the value of the **ID** parameter can't be `$null`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [ValidateNotNull()]
    $ID
)
```

### <a name="validatenotnullorempty-validation-attribute"></a><span data-ttu-id="5406c-282">ValidateNotNullOrEmpty-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-282">ValidateNotNullOrEmpty validation attribute</span></span>

<span data-ttu-id="5406c-283">Attributet **ValidateNotNullOrEmpty** anger att parametervärdet får inte vara `$null` en tom sträng ( `""` ).</span><span class="sxs-lookup"><span data-stu-id="5406c-283">The **ValidateNotNullOrEmpty** attribute specifies that the parameter value can't be `$null` and can't be an empty string (`""`).</span></span> <span data-ttu-id="5406c-284">PowerShell genererar ett fel om parametern används i ett funktions anrop, men dess värde är `$null` en tom sträng ( `""` ) eller en tom matris `@()` .</span><span class="sxs-lookup"><span data-stu-id="5406c-284">PowerShell generates an error if the parameter is used in a function call, but its value is `$null`, an empty string (`""`), or an empty array `@()`.</span></span>

```powershell
Param(
    [Parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [String[]]
    $UserName
)
```

### <a name="validatedrive-validation-attribute"></a><span data-ttu-id="5406c-285">ValidateDrive-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-285">ValidateDrive validation attribute</span></span>

<span data-ttu-id="5406c-286">Attributet **ValidateDrive** anger att parametervärdet måste representera sökvägen, som bara refererar till tillåtna enheter.</span><span class="sxs-lookup"><span data-stu-id="5406c-286">The **ValidateDrive** attribute specifies that the parameter value must represent the path, that's referring to allowed drives only.</span></span> <span data-ttu-id="5406c-287">PowerShell genererar ett fel om parametervärdet refererar till andra enheter än vad som tillåts.</span><span class="sxs-lookup"><span data-stu-id="5406c-287">PowerShell generates an error if the parameter value refers to drives other than the allowed.</span></span> <span data-ttu-id="5406c-288">Förekomsten av sökvägen, förutom själva enheten, är inte verifierad.</span><span class="sxs-lookup"><span data-stu-id="5406c-288">Existence of the path, except for the drive itself, isn't verified.</span></span>

<span data-ttu-id="5406c-289">Om du använder en relativ sökväg måste den aktuella enheten finnas i listan över tillåtna enheter.</span><span class="sxs-lookup"><span data-stu-id="5406c-289">If you use relative path, the current drive must be in the allowed drive list.</span></span>

```powershell
Param(
    [ValidateDrive("C", "D", "Variable", "Function")]
    [String]$Path
)
```

### <a name="validateuserdrive-validation-attribute"></a><span data-ttu-id="5406c-290">ValidateUserDrive-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-290">ValidateUserDrive validation attribute</span></span>

<span data-ttu-id="5406c-291">Attributet **ValidateUserDrive** anger att parametervärdet måste representera sökvägen som refererar till `User` enheten.</span><span class="sxs-lookup"><span data-stu-id="5406c-291">The **ValidateUserDrive** attribute specifies that the parameter value must represent the path, that is referring to `User` drive.</span></span> <span data-ttu-id="5406c-292">PowerShell genererar ett fel om sökvägen refererar till en annan enhet.</span><span class="sxs-lookup"><span data-stu-id="5406c-292">PowerShell generates an error if the path refers to a different drive.</span></span> <span data-ttu-id="5406c-293">Verifierings attributet testar bara för att det finns en enhets del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="5406c-293">The validation attribute only tests for the existence of the drive portion of the path.</span></span>

<span data-ttu-id="5406c-294">Om du använder relativ sökväg måste den aktuella enheten vara `User` .</span><span class="sxs-lookup"><span data-stu-id="5406c-294">If you use relative path, the current drive must be `User`.</span></span>

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

<span data-ttu-id="5406c-295">Du kan definiera `User` enhet i Jea-sessionsinställningar (bara för administration).</span><span class="sxs-lookup"><span data-stu-id="5406c-295">You can define `User` drive in Just Enough Administration (JEA) session configurations.</span></span> <span data-ttu-id="5406c-296">I det här exemplet skapar vi användaren: enhet.</span><span class="sxs-lookup"><span data-stu-id="5406c-296">For this example, we create the User: drive.</span></span>

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

### <a name="validatetrusteddata-validation-attribute"></a><span data-ttu-id="5406c-297">ValidateTrustedData-verifierings attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-297">ValidateTrustedData validation attribute</span></span>

<span data-ttu-id="5406c-298">Det här attributet lades till i PowerShell-startattributet.</span><span class="sxs-lookup"><span data-stu-id="5406c-298">This attribute was added in PowerShell 6.1.1.</span></span>

<span data-ttu-id="5406c-299">För tillfället används attributet internt av PowerShell och är inte avsett för extern användning.</span><span class="sxs-lookup"><span data-stu-id="5406c-299">At this time, the attribute is used internally by PowerShell itself and is not intended for external usage.</span></span>

## <a name="dynamic-parameters"></a><span data-ttu-id="5406c-300">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="5406c-300">Dynamic parameters</span></span>

<span data-ttu-id="5406c-301">Dynamiska parametrar är parametrar för en cmdlet, funktion eller ett skript som endast är tillgängliga under vissa förhållanden.</span><span class="sxs-lookup"><span data-stu-id="5406c-301">Dynamic parameters are parameters of a cmdlet, function, or script that are available only under certain conditions.</span></span>

<span data-ttu-id="5406c-302">Till exempel har flera Provider-cmdlets parametrar som endast är tillgängliga när cmdleten används i leverantörs enheten, eller i en viss sökväg för providerns enhet.</span><span class="sxs-lookup"><span data-stu-id="5406c-302">For example, several provider cmdlets have parameters that are available only when the cmdlet is used in the provider drive, or in a particular path of the provider drive.</span></span> <span data-ttu-id="5406c-303">Till exempel är **encoding** -parametern endast tillgänglig på `Add-Content` `Get-Content` cmdletarna, och `Set-Content` när den används i en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="5406c-303">For example, the **Encoding** parameter is available on the `Add-Content`, `Get-Content`, and `Set-Content` cmdlets only when it's used in a file system drive.</span></span>

<span data-ttu-id="5406c-304">Du kan också skapa en parameter som bara visas när en annan parameter används i funktions kommandot eller när en annan parameter har ett visst värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-304">You can also create a parameter that appears only when another parameter is used in the function command or when another parameter has a certain value.</span></span>

<span data-ttu-id="5406c-305">Dynamiska parametrar kan vara användbara, men Använd dem bara när det behövs, eftersom det kan vara svårt för användarna att identifiera sig.</span><span class="sxs-lookup"><span data-stu-id="5406c-305">Dynamic parameters can be useful, but use them only when necessary, because they can be difficult for users to discover.</span></span> <span data-ttu-id="5406c-306">Om du vill hitta en dynamisk parameter måste användaren finnas i providerns sökväg, använda parametern **argument List** i `Get-Command` cmdleten eller använda parametern **Path** i `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="5406c-306">To find a dynamic parameter, the user must be in the provider path, use the **ArgumentList** parameter of the `Get-Command` cmdlet, or use the **Path** parameter of `Get-Help`.</span></span>

<span data-ttu-id="5406c-307">Om du vill skapa en dynamisk parameter för en funktion eller ett skript använder du `DynamicParam` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="5406c-307">To create a dynamic parameter for a function or script, use the `DynamicParam` keyword.</span></span>

<span data-ttu-id="5406c-308">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="5406c-308">The syntax is as follows:</span></span>

`DynamicParam {<statement-list>}`

<span data-ttu-id="5406c-309">Använd en instruktion i instruktions listan `If` för att ange de villkor under vilka parametern är tillgänglig i funktionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-309">In the statement list, use an `If` statement to specify the conditions under which the parameter is available in the function.</span></span>

<span data-ttu-id="5406c-310">Använd `New-Object` cmdleten för att skapa ett **system. Management. Automation. RuntimeDefinedParameter** -objekt för att representera parametern och ange dess namn.</span><span class="sxs-lookup"><span data-stu-id="5406c-310">Use the `New-Object` cmdlet to create a **System.Management.Automation.RuntimeDefinedParameter** object to represent the parameter and specify its name.</span></span>

<span data-ttu-id="5406c-311">Du kan använda ett `New-Object` kommando för att skapa ett **system. Management. Automation. ParameterAttribute** -objekt som representerar attribut för parametern, till exempel **obligatorisk** , **position** eller **ValueFromPipeline** eller dess parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="5406c-311">You can use a `New-Object` command to create a **System.Management.Automation.ParameterAttribute** object to represent attributes of the parameter, such as **Mandatory** , **Position** , or **ValueFromPipeline** or its parameter set.</span></span>

<span data-ttu-id="5406c-312">I följande exempel visas en exempel funktion med standard parametrar med namnet **Name** och **Path** , och en valfri dynamisk parameter med namnet **DP1**.</span><span class="sxs-lookup"><span data-stu-id="5406c-312">The following example shows a sample function with standard parameters named **Name** and **Path** , and an optional dynamic parameter named **DP1**.</span></span> <span data-ttu-id="5406c-313">Parametern **DP1** är i `PSet1` parameter uppsättningen och har en typ av `Int32` .</span><span class="sxs-lookup"><span data-stu-id="5406c-313">The **DP1** parameter is in the `PSet1` parameter set and has a type of `Int32`.</span></span>
<span data-ttu-id="5406c-314">Parametern **DP1** är endast tillgänglig i `Get-Sample` funktionen när värdet för **Sök vägs** parametern börjar med `HKLM:` , vilket anger att den används i `HKEY_LOCAL_MACHINE` register enheten.</span><span class="sxs-lookup"><span data-stu-id="5406c-314">The **DP1** parameter is available in the `Get-Sample` function only when the value of the **Path** parameter starts with `HKLM:`, indicating that it's being used in the `HKEY_LOCAL_MACHINE` registry drive.</span></span>

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

<span data-ttu-id="5406c-315">Mer information finns i [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span><span class="sxs-lookup"><span data-stu-id="5406c-315">For more information, see [RuntimeDefinedParameter](/dotnet/api/system.management.automation.runtimedefinedparameter).</span></span>

## <a name="switch-parameters"></a><span data-ttu-id="5406c-316">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="5406c-316">Switch parameters</span></span>

<span data-ttu-id="5406c-317">Växlings parametrar är parametrar utan parameter värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-317">Switch parameters are parameters with no parameter value.</span></span> <span data-ttu-id="5406c-318">De är bara effektiva när de används och har bara en effekt.</span><span class="sxs-lookup"><span data-stu-id="5406c-318">They're effective only when they're used and have only one effect.</span></span>

<span data-ttu-id="5406c-319">Till exempel är parametern **noprofile** i **powershell.exe** en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="5406c-319">For example, the **NoProfile** parameter of **powershell.exe** is a switch parameter.</span></span>

<span data-ttu-id="5406c-320">Om du vill skapa en växel parameter i en funktion anger du `Switch` typen i parameter definitionen.</span><span class="sxs-lookup"><span data-stu-id="5406c-320">To create a switch parameter in a function, specify the `Switch` type in the parameter definition.</span></span>

<span data-ttu-id="5406c-321">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="5406c-321">For example:</span></span>

```powershell
Param([Switch]<ParameterName>)
```

<span data-ttu-id="5406c-322">Eller så kan du använda en annan metod:</span><span class="sxs-lookup"><span data-stu-id="5406c-322">Or, you can use an another method:</span></span>

```powershell
Param(
    [Parameter(Mandatory=$false)]
    [Switch]
    $<ParameterName>
)
```

<span data-ttu-id="5406c-323">Växlings parametrar är enkla att använda och föredras över booleska parametrar som har en mer svår syntax.</span><span class="sxs-lookup"><span data-stu-id="5406c-323">Switch parameters are easy to use and are preferred over Boolean parameters, which have a more difficult syntax.</span></span>

<span data-ttu-id="5406c-324">Om du till exempel vill använda en växlings parameter skriver användaren parametern i kommandot.</span><span class="sxs-lookup"><span data-stu-id="5406c-324">For example, to use a switch parameter, the user types the parameter in the command.</span></span>

`-IncludeAll`

<span data-ttu-id="5406c-325">Om du vill använda en boolesk parameter skriver användaren parametern och ett booleskt värde.</span><span class="sxs-lookup"><span data-stu-id="5406c-325">To use a Boolean parameter, the user types the parameter and a Boolean value.</span></span>

`-IncludeAll:$true`

<span data-ttu-id="5406c-326">När du skapar växlings parametrar väljer du parameter namnet noggrant.</span><span class="sxs-lookup"><span data-stu-id="5406c-326">When creating switch parameters, choose the parameter name carefully.</span></span> <span data-ttu-id="5406c-327">Se till att parameter namnet meddelar användaren om parameterns resultat.</span><span class="sxs-lookup"><span data-stu-id="5406c-327">Be sure that the parameter name communicates the effect of the parameter to the user.</span></span>
<span data-ttu-id="5406c-328">Undvik tvetydiga termer, till exempel **filter** eller **maximum** som kan innebära att ett värde krävs.</span><span class="sxs-lookup"><span data-stu-id="5406c-328">Avoid ambiguous terms, such as **Filter** or **Maximum** that might imply a value is required.</span></span>

## <a name="argumentcompleter-attribute"></a><span data-ttu-id="5406c-329">ArgumentCompleter-attribut</span><span class="sxs-lookup"><span data-stu-id="5406c-329">ArgumentCompleter attribute</span></span>

<span data-ttu-id="5406c-330">Med attributet **ArgumentCompleter** kan du lägga till TABB-slutförande-värden till en speciell parameter.</span><span class="sxs-lookup"><span data-stu-id="5406c-330">The **ArgumentCompleter** attribute allows you to add tab completion values to a specific parameter.</span></span> <span data-ttu-id="5406c-331">Ett **ArgumentCompleter** -attribut måste definieras för varje parameter som kräver TABB-slutförande.</span><span class="sxs-lookup"><span data-stu-id="5406c-331">An **ArgumentCompleter** attribute must be defined for each parameter that needs tab completion.</span></span> <span data-ttu-id="5406c-332">Precis som med **DynamicParameters** beräknas de tillgängliga värdena vid körning när användaren trycker på <kbd>TABB</kbd> efter parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="5406c-332">Similar to **DynamicParameters** , the available values are calculated at runtime when the user presses <kbd>Tab</kbd> after the parameter name.</span></span>

<span data-ttu-id="5406c-333">Om du vill lägga till ett **ArgumentCompleter** -attribut måste du definiera ett skript block som bestämmer värdena.</span><span class="sxs-lookup"><span data-stu-id="5406c-333">To add an **ArgumentCompleter** attribute, you need to define a script block that determines the values.</span></span> <span data-ttu-id="5406c-334">Skript blocket måste ha följande parametrar i den ordning som anges nedan.</span><span class="sxs-lookup"><span data-stu-id="5406c-334">The script block must take the following parameters in the order specified below.</span></span> <span data-ttu-id="5406c-335">Parameterns namn spelar ingen roll när värdena anges i position.</span><span class="sxs-lookup"><span data-stu-id="5406c-335">The parameter's names don't matter as the values are provided positionally.</span></span>

<span data-ttu-id="5406c-336">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="5406c-336">The syntax is as follows:</span></span>

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

### <a name="argumentcompleter-script-block"></a><span data-ttu-id="5406c-337">ArgumentCompleter-skript block</span><span class="sxs-lookup"><span data-stu-id="5406c-337">ArgumentCompleter script block</span></span>

<span data-ttu-id="5406c-338">Skript block parametrarna har angetts till följande värden:</span><span class="sxs-lookup"><span data-stu-id="5406c-338">The script block parameters are set to the following values:</span></span>

- <span data-ttu-id="5406c-339">`$commandName` (Position 0) – den här parametern anges till namnet på det kommando som skript blocket tillhandahåller för att slutföra tabben.</span><span class="sxs-lookup"><span data-stu-id="5406c-339">`$commandName` (Position 0) - This parameter is set to the name of the command for which the script block is providing tab completion.</span></span>
- <span data-ttu-id="5406c-340">`$parameterName` (Position 1) – den här parametern har angetts till den parameter vars värde kräver att tabbtangenten slutförs.</span><span class="sxs-lookup"><span data-stu-id="5406c-340">`$parameterName` (Position 1) - This parameter is set to the parameter whose value requires tab completion.</span></span>
- <span data-ttu-id="5406c-341">`$wordToComplete` (Position 2) – den här parametern är inställd på värde som användaren har angett innan de tryckte på <kbd>fliken</kbd>. Skript blocket ska använda det här värdet för att fastställa värden för tabbar.</span><span class="sxs-lookup"><span data-stu-id="5406c-341">`$wordToComplete` (Position 2) - This parameter is set to value the user has provided before they pressed <kbd>Tab</kbd>. Your script block should use this value to determine tab completion values.</span></span>
- <span data-ttu-id="5406c-342">`$commandAst` (Position 3) – den här parametern har angetts till det abstrakta Syntaxs trädet (AST) för den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="5406c-342">`$commandAst` (Position 3) - This parameter is set to the Abstract Syntax Tree (AST) for the current input line.</span></span> <span data-ttu-id="5406c-343">Mer information finns i [AST-klass](/dotnet/api/system.management.automation.language.ast).</span><span class="sxs-lookup"><span data-stu-id="5406c-343">For more information, see [Ast Class](/dotnet/api/system.management.automation.language.ast).</span></span>
- <span data-ttu-id="5406c-344">`$fakeBoundParameters` (Position 4) – den här parametern anges till en hash-text som innehåller `$PSBoundParameters` för cmdleten innan användaren tryckte på <kbd>fliken</kbd>. Mer information finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="5406c-344">`$fakeBoundParameters` (Position 4) - This parameter is set to a hashtable containing the `$PSBoundParameters` for the cmdlet, before the user pressed <kbd>Tab</kbd>. For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="5406c-345">**ArgumentCompleter** -skript blocket måste avregistrera värdena med hjälp av pipelinen, till exempel, `ForEach-Object` `Where-Object` eller någon annan lämplig metod.</span><span class="sxs-lookup"><span data-stu-id="5406c-345">The **ArgumentCompleter** script block must unroll the values using the pipeline, such as `ForEach-Object`, `Where-Object`, or another suitable method.</span></span>
<span data-ttu-id="5406c-346">Om du returnerar en matris med värden kan PowerShell behandla hela matrisen som **ett** värde för sista tabb.</span><span class="sxs-lookup"><span data-stu-id="5406c-346">Returning an array of values causes PowerShell to treat the entire array as **one** tab completion value.</span></span>

<span data-ttu-id="5406c-347">I följande exempel läggs TABB-slutförande till **Value** -parametern.</span><span class="sxs-lookup"><span data-stu-id="5406c-347">The following example adds tab completion to the **Value** parameter.</span></span> <span data-ttu-id="5406c-348">Om bara **värde** parametern anges visas alla möjliga värden eller argument för **värdet** .</span><span class="sxs-lookup"><span data-stu-id="5406c-348">If only the **Value** parameter is specified, all possible values, or arguments, for **Value** are displayed.</span></span> <span data-ttu-id="5406c-349">När **typ** parametern anges visar **värde** parametern bara möjliga värden för den typen.</span><span class="sxs-lookup"><span data-stu-id="5406c-349">When the **Type** parameter is specified, the **Value** parameter only displays the possible values for that type.</span></span>

<span data-ttu-id="5406c-350">Dessutom `-like` säkerställer operatorn att om användaren skriver följande kommando och använder <kbd>TABB</kbd> -slutförande, returneras bara **Apple** .</span><span class="sxs-lookup"><span data-stu-id="5406c-350">In addition, the `-like` operator ensures that if the user types the following command and uses <kbd>Tab</kbd> completion, only **Apple** is returned.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5406c-351">Se även</span><span class="sxs-lookup"><span data-stu-id="5406c-351">See also</span></span>

[<span data-ttu-id="5406c-352">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="5406c-352">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="5406c-353">about_Functions</span><span class="sxs-lookup"><span data-stu-id="5406c-353">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="5406c-354">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="5406c-354">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="5406c-355">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="5406c-355">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="5406c-356">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="5406c-356">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="5406c-357">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="5406c-357">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)
