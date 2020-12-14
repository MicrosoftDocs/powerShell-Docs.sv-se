---
description: Beskriver hur du arbetar med kommando parametrar i PowerShell.
Locale: en-US
ms.date: 02/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parameters
ms.openlocfilehash: c9d7ab62c13a7cafcf93103f9a70f6575d5dd7b8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710998"
---
# <a name="about-parameters"></a><span data-ttu-id="7be30-103">Om parametrar</span><span class="sxs-lookup"><span data-stu-id="7be30-103">About Parameters</span></span>

## <a name="short-description"></a><span data-ttu-id="7be30-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="7be30-104">Short description</span></span>
<span data-ttu-id="7be30-105">Beskriver hur du arbetar med kommando parametrar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7be30-105">Describes how to work with command parameters in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="7be30-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="7be30-106">Long description</span></span>

<span data-ttu-id="7be30-107">De flesta PowerShell-kommandon, till exempel cmdlets, Functions och scripts, förlitar sig på parametrar för att tillåta användare att välja alternativ eller ange information.</span><span class="sxs-lookup"><span data-stu-id="7be30-107">Most PowerShell commands, such as cmdlets, functions, and scripts, rely on parameters to allow users to select options or provide input.</span></span> <span data-ttu-id="7be30-108">Parametrarna följer kommando namnet och har följande format:</span><span class="sxs-lookup"><span data-stu-id="7be30-108">The parameters follow the command name and have the following form:</span></span>

```
-<parameter_name> <parameter_value>
-<parameter_name>:<parameter_value>
```

<span data-ttu-id="7be30-109">Namnet på parametern föregås av ett bindestreck (-), som signalerar till PowerShell att ordet efter bindestrecket är ett parameter namn.</span><span class="sxs-lookup"><span data-stu-id="7be30-109">The name of the parameter is preceded by a hyphen (-), which signals to PowerShell that the word following the hyphen is a parameter name.</span></span> <span data-ttu-id="7be30-110">Parameter namnet och värdet kan avgränsas med ett blank steg eller ett kolon.</span><span class="sxs-lookup"><span data-stu-id="7be30-110">The parameter name and value can be separated by a space or a colon character.</span></span> <span data-ttu-id="7be30-111">Vissa parametrar kräver inte eller accepterar inte ett parameter värde.</span><span class="sxs-lookup"><span data-stu-id="7be30-111">Some parameters do not require or accept a parameter value.</span></span> <span data-ttu-id="7be30-112">Andra parametrar kräver ett värde, men kräver inte parameter namnet i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-112">Other parameters require a value, but do not require the parameter name in the command.</span></span>

<span data-ttu-id="7be30-113">Typ av parametrar och kraven för dessa parametrar varierar.</span><span class="sxs-lookup"><span data-stu-id="7be30-113">The type of parameters and the requirements for those parameters vary.</span></span> <span data-ttu-id="7be30-114">Använd cmdleten för att hitta information om parametrarna för ett kommando `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="7be30-114">To find information about the parameters of a command, use the `Get-Help` cmdlet.</span></span> <span data-ttu-id="7be30-115">Om du till exempel vill hitta information om parametrarna för `Get-ChildItem` cmdleten skriver du:</span><span class="sxs-lookup"><span data-stu-id="7be30-115">For example, to find information about the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="7be30-116">Om du vill hitta information om parametrarna för ett skript använder du den fullständiga sökvägen till skript filen.</span><span class="sxs-lookup"><span data-stu-id="7be30-116">To find information about the parameters of a script, use the full path to the script file.</span></span> <span data-ttu-id="7be30-117">Exempel:</span><span class="sxs-lookup"><span data-stu-id="7be30-117">For example:</span></span>

```powershell
Get-Help $home\Documents\Scripts\Get-Function.ps1
```

<span data-ttu-id="7be30-118">`Get-Help`Cmdleten returnerar olika uppgifter om kommandot, inklusive en beskrivning, kommandosyntaxen, information om parametrarna och exempel som visar hur du använder parametrarna i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="7be30-118">The `Get-Help` cmdlet returns various details about the command, including a description, the command syntax, information about the parameters, and examples showing how to use the parameters in a command.</span></span>

<span data-ttu-id="7be30-119">Du kan också använda parametern parameter för `Get-Help` cmdlet: en för att hitta information om en viss parameter.</span><span class="sxs-lookup"><span data-stu-id="7be30-119">You can also use the Parameter parameter of the `Get-Help` cmdlet to find information about a particular parameter.</span></span> <span data-ttu-id="7be30-120">Eller så kan du använda **parameter** parametern med värdet jokertecken ( `*` ) för att hitta information om alla parametrar för kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-120">Or, you can use the **Parameter** parameter with the wildcard character ( `*` ) value to find information about all parameters of the command.</span></span> <span data-ttu-id="7be30-121">Följande kommando hämtar till exempel information om alla parametrar för `Get-Member` cmdleten:</span><span class="sxs-lookup"><span data-stu-id="7be30-121">For example, the following command gets information about all parameters of the `Get-Member` cmdlet:</span></span>

```powershell
Get-Help Get-Member -Parameter *
```

### <a name="default-parameter-values"></a><span data-ttu-id="7be30-122">Standard parameter värden</span><span class="sxs-lookup"><span data-stu-id="7be30-122">Default parameter values</span></span>

<span data-ttu-id="7be30-123">Valfria parametrar har ett standardvärde, vilket är det värde som används eller antas när parametern inte anges i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-123">Optional parameters have a default value, which is the value that is used or assumed when the parameter is not specified in the command.</span></span>

<span data-ttu-id="7be30-124">Standardvärdet för parametern **computername** för många cmdletar är till exempel namnet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="7be30-124">For example, the default value of the **ComputerName** parameter of many cmdlets is the name of the local computer.</span></span> <span data-ttu-id="7be30-125">Därför används namnet på den lokala datorn i kommandot om inte parametern **computername** anges.</span><span class="sxs-lookup"><span data-stu-id="7be30-125">As a result, the local computer name is used in the command unless the **ComputerName** parameter is specified.</span></span>

<span data-ttu-id="7be30-126">Du hittar standardvärdet för parametern i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7be30-126">To find the default parameter value, see help topic for the cmdlet.</span></span> <span data-ttu-id="7be30-127">Parameter beskrivningen ska innehålla standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="7be30-127">The parameter description should include the default value.</span></span>

<span data-ttu-id="7be30-128">Du kan också ange ett anpassat standardvärde för vilken parameter som helst av en cmdlet eller en avancerad funktion.</span><span class="sxs-lookup"><span data-stu-id="7be30-128">You can also set a custom default value for any parameter of a cmdlet or advanced function.</span></span> <span data-ttu-id="7be30-129">Information om hur du ställer in anpassade standardvärden finns [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span><span class="sxs-lookup"><span data-stu-id="7be30-129">For information about setting custom default values, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="7be30-130">Parameter egenskaps tabell</span><span class="sxs-lookup"><span data-stu-id="7be30-130">Parameter attribute table</span></span>

<span data-ttu-id="7be30-131">När du använder parametrarna **fullständig**, **parameter** eller **online** i `Get-Help` cmdleten, `Get-Help` visar en tabell med parameter-attribut med detaljerad information om parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-131">When you use the **Full**, **Parameter**, or **Online** parameters of the `Get-Help` cmdlet, `Get-Help` displays a parameter attribute table with detailed information about the parameter.</span></span>

<span data-ttu-id="7be30-132">Den här informationen innehåller information som du behöver känna till när du använder-parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-132">This information includes the details you need to know to use the parameter.</span></span>
<span data-ttu-id="7be30-133">Till exempel innehåller hjälp avsnittet för `Get-ChildItem` cmdleten följande information om dess Sök vägs parameter:</span><span class="sxs-lookup"><span data-stu-id="7be30-133">For example, the help topic for the `Get-ChildItem` cmdlet includes the following details about its Path parameter:</span></span>

```
-path <string[]>
    Specifies a path of one or more locations. Wildcard characters are
    permitted. The default location is the current directory (.).

Required?                    false
Position?                    0
Default value                Current directory
Accept pipeline input?       true (ByValue, ByPropertyName)
Accept wildcard characters?  true
```

<span data-ttu-id="7be30-134">Parameter informationen innehåller parameter-syntaxen, en beskrivning av parametern och attributen för parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-134">The parameter information includes the parameter syntax, a description of the parameter, and the parameter attributes.</span></span> <span data-ttu-id="7be30-135">I följande avsnitt beskrivs attributen för parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-135">The following sections describe the parameter attributes.</span></span>

#### <a name="parameter-required"></a><span data-ttu-id="7be30-136">Parameter krävs</span><span class="sxs-lookup"><span data-stu-id="7be30-136">Parameter Required</span></span>

<span data-ttu-id="7be30-137">Den här inställningen anger om parametern är obligatorisk, det vill säga om alla kommandon som använder denna cmdlet måste innehålla denna parameter.</span><span class="sxs-lookup"><span data-stu-id="7be30-137">This setting indicates whether the parameter is mandatory, that is, whether all commands that use this cmdlet must include this parameter.</span></span> <span data-ttu-id="7be30-138">När värdet är **True** och parametern saknas i kommandot, uppmanas du att ange ett värde för parametern i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7be30-138">When the value is **True** and the parameter is missing from the command, PowerShell prompts you for a value for the parameter.</span></span>

#### <a name="parameter-position"></a><span data-ttu-id="7be30-139">Parameter position</span><span class="sxs-lookup"><span data-stu-id="7be30-139">Parameter Position</span></span>

<span data-ttu-id="7be30-140">Om `Position` inställningen har angetts till ett positivt heltal, krävs inte parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="7be30-140">If the `Position` setting is set to a positive integer, the parameter name is not required.</span></span> <span data-ttu-id="7be30-141">Den här typen av parameter kallas för en positions parameter och siffran anger den position där parametern måste visas i förhållande till andra positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="7be30-141">This type of parameter is referred to as a positional parameter, and the number indicates the position in which the parameter must appear in relation to other positional parameters.</span></span> <span data-ttu-id="7be30-142">En namngiven parameter kan anges i valfri position efter cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="7be30-142">A named parameter can be listed in any position after the cmdlet name.</span></span> <span data-ttu-id="7be30-143">Om du inkluderar parameter namnet för en positions parameter, kan parametern anges i valfri position efter cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="7be30-143">If you include the parameter name for a positional parameter, the parameter can be listed in any position after the cmdlet name.</span></span>

<span data-ttu-id="7be30-144">Till exempel `Get-ChildItem` har cmdleten sökväg och exkludera parametrar.</span><span class="sxs-lookup"><span data-stu-id="7be30-144">For example, the `Get-ChildItem` cmdlet has Path and Exclude parameters.</span></span> <span data-ttu-id="7be30-145">`Position`Inställningen för **sökväg** är **0**, vilket innebär att den är en positions parameter.</span><span class="sxs-lookup"><span data-stu-id="7be30-145">The `Position` setting for **Path** is **0**, which means that it is a positional parameter.</span></span> <span data-ttu-id="7be30-146">`Position`Inställningen för **exclude** kallas .</span><span class="sxs-lookup"><span data-stu-id="7be30-146">The `Position` setting for **Exclude** is **named**.</span></span>

<span data-ttu-id="7be30-147">Det innebär att **sökvägen** inte kräver parameter namnet, men dess parameter värde måste vara det första eller enda parameter värde som inte är namn i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-147">This means that **Path** does not require the parameter name, but its parameter value must be the first or only unnamed parameter value in the command.</span></span>
<span data-ttu-id="7be30-148">Men eftersom parametern exclude är en namngiven parameter, kan du placera den i valfri position i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-148">However, because the Exclude parameter is a named parameter, you can place it in any position in the command.</span></span>

<span data-ttu-id="7be30-149">Som ett resultat av `Position` inställningarna för dessa två parametrar kan du använda något av följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="7be30-149">As a result of the `Position` settings for these two parameters, you can use any of the following commands:</span></span>

```powershell
Get-ChildItem -Path c:\techdocs -Exclude *.ppt
Get-ChildItem c:\techdocs -Exclude *.ppt
Get-ChildItem -Exclude *.ppt -Path c:\techdocs
Get-ChildItem -Exclude *.ppt c:\techdocs
```

<span data-ttu-id="7be30-150">Om du vill inkludera en annan positions parameter utan att inkludera parameter namnet, måste den parametern placeras i den ordning som anges av `Position` inställningen.</span><span class="sxs-lookup"><span data-stu-id="7be30-150">If you were to include another positional parameter without including the parameter name, that parameter must be placed in the order specified by the `Position` setting.</span></span>

#### <a name="parameter-type"></a><span data-ttu-id="7be30-151">Parameter typ</span><span class="sxs-lookup"><span data-stu-id="7be30-151">Parameter Type</span></span>

<span data-ttu-id="7be30-152">Den här inställningen anger parameter värdets Microsoft .NET Framework-typ.</span><span class="sxs-lookup"><span data-stu-id="7be30-152">This setting specifies the Microsoft .NET Framework type of the parameter value.</span></span> <span data-ttu-id="7be30-153">Om typen till exempel är **Int32**, måste parametervärdet vara ett heltal.</span><span class="sxs-lookup"><span data-stu-id="7be30-153">For example, if the type is **Int32**, the parameter value must be an integer.</span></span> <span data-ttu-id="7be30-154">Om typen är sträng måste parametervärdet vara en tecken sträng.</span><span class="sxs-lookup"><span data-stu-id="7be30-154">If the type is string, the parameter value must be a character string.</span></span> <span data-ttu-id="7be30-155">Om strängen innehåller blank steg måste värdet stå inom citat tecken, eller så måste blank stegen föregås av Escape-tecknet (").</span><span class="sxs-lookup"><span data-stu-id="7be30-155">If the string contains spaces, the value must be enclosed in quotation marks, or the spaces must be preceded by the escape character ( \` ).</span></span>

#### <a name="default-value"></a><span data-ttu-id="7be30-156">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="7be30-156">Default Value</span></span>

<span data-ttu-id="7be30-157">Den här inställningen anger värdet som parametern kommer att anta om inget annat värde anges.</span><span class="sxs-lookup"><span data-stu-id="7be30-157">This setting specifies the value that the parameter will assume if no other value is provided.</span></span> <span data-ttu-id="7be30-158">Till exempel är standardvärdet för Sök vägs parametern ofta den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="7be30-158">For example, the default value of the Path parameter is often the current directory.</span></span> <span data-ttu-id="7be30-159">De obligatoriska parametrarna har aldrig ett standardvärde.</span><span class="sxs-lookup"><span data-stu-id="7be30-159">Required parameters never have a default value.</span></span>
<span data-ttu-id="7be30-160">För många valfria parametrar finns det inget standardvärde eftersom parametern inte har någon inverkan om den inte används.</span><span class="sxs-lookup"><span data-stu-id="7be30-160">For many optional parameters, there is no default because the parameter has no effect if it is not used.</span></span>

#### <a name="accepts-multiple-values"></a><span data-ttu-id="7be30-161">Accepterar flera värden</span><span class="sxs-lookup"><span data-stu-id="7be30-161">Accepts Multiple Values</span></span>

<span data-ttu-id="7be30-162">Den här inställningen anger om en parameter accepterar flera parameter värden.</span><span class="sxs-lookup"><span data-stu-id="7be30-162">This setting indicates whether a parameter accepts multiple parameter values.</span></span>
<span data-ttu-id="7be30-163">När en parameter accepterar flera värden kan du skriva en kommaavgränsad lista som värde för parametern i kommandot eller spara en kommaavgränsad lista (en matris) i en variabel och sedan ange variabeln som parameter värde.</span><span class="sxs-lookup"><span data-stu-id="7be30-163">When a parameter accepts multiple values, you can type a comma-separated list as the value of the parameter in the command, or save a comma-separated list (an array) in a variable, and then specify the variable as the parameter value.</span></span>

<span data-ttu-id="7be30-164">Till exempel accepterar ServiceName-parametern för `Get-Service` cmdleten flera värden.</span><span class="sxs-lookup"><span data-stu-id="7be30-164">For example, the ServiceName parameter of the `Get-Service` cmdlet accepts multiple values.</span></span> <span data-ttu-id="7be30-165">Följande kommandon är både giltiga:</span><span class="sxs-lookup"><span data-stu-id="7be30-165">The following commands are both valid:</span></span>

```powershell
Get-Service -servicename winrm, netlogon
```

```powershell
$s = "winrm", "netlogon"
Get-Service -servicename $s
```

#### <a name="accepts-pipeline-input"></a><span data-ttu-id="7be30-166">Accepterar inmatade pipelines</span><span class="sxs-lookup"><span data-stu-id="7be30-166">Accepts Pipeline Input</span></span>

<span data-ttu-id="7be30-167">Den här inställningen anger om du kan använda pipeline-operatorn ( `|` ) för att skicka ett värde till parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-167">This setting indicates whether you can use the pipeline operator ( `|` ) to send a value to the parameter.</span></span>

```
Value                    Description
-----                    -----------
False                    Indicates that you cannot pipe a value to the
                         parameter.

True (by Value)          Indicates that you can pipe any value to the
                         parameter, just so the value has the .NET
                         Framework type specified for the parameter or the
                         value can be converted to the specified .NET
                         Framework type.
```

<span data-ttu-id="7be30-168">När en parameter är "sant (efter värde)" försöker PowerShell associera alla skickas-värden med den parametern innan den försöker med andra metoder för att tolka kommandot.</span><span class="sxs-lookup"><span data-stu-id="7be30-168">When a parameter is "True (by Value)", PowerShell tries to associate any piped values with that parameter before it tries other methods to interpret the command.</span></span>

```
True (by Property Name)  Indicates that you can pipe a value to the
                         parameter, but the .NET Framework type of the
                         parameter must include a property with the same
                         name as the parameter.
```

<span data-ttu-id="7be30-169">Du kan till exempel skicka ett värde till en **namn** parameter endast när värdet har en egenskap som heter **Name**.</span><span class="sxs-lookup"><span data-stu-id="7be30-169">For example, you can pipe a value to a **Name** parameter only when the value has a property called **Name**.</span></span>

> [!NOTE]
> <span data-ttu-id="7be30-170">En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken **Delay-bind** i parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-170">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
>
> <span data-ttu-id="7be30-171">Skript blocket **Delay-bind** körs automatiskt under **ParameterBinding**.</span><span class="sxs-lookup"><span data-stu-id="7be30-171">The **delay-bind** script block is run automatically during **ParameterBinding**.</span></span> <span data-ttu-id="7be30-172">Resultatet är kopplat till parametern.</span><span class="sxs-lookup"><span data-stu-id="7be30-172">The result is bound to the parameter.</span></span> <span data-ttu-id="7be30-173">Fördröjd bindning fungerar **inte** för parametrar som har definierats som typ `ScriptBlock` eller `System.Object` , skript blocket skickas genom **utan** att anropas.</span><span class="sxs-lookup"><span data-stu-id="7be30-173">Delay binding does **not** work for parameters defined as type `ScriptBlock` or `System.Object`, the script block is passed through **without** being invoked.</span></span>
>
> <span data-ttu-id="7be30-174">Du kan läsa mer om **fördröjning – binda** skript block här [about_Script_Blocks. MD](about_Script_Blocks.md)</span><span class="sxs-lookup"><span data-stu-id="7be30-174">You can read about **delay-bind** script blocks here [about_Script_Blocks.md](about_Script_Blocks.md)</span></span>

#### <a name="accepts-wildcard-characters"></a><span data-ttu-id="7be30-175">Accepterar jokertecken</span><span class="sxs-lookup"><span data-stu-id="7be30-175">Accepts Wildcard Characters</span></span>

<span data-ttu-id="7be30-176">Den här inställningen anger om parameterns värde kan innehålla jokertecken så att parametervärdet kan matchas mot fler än ett befintligt objekt i mål behållaren.</span><span class="sxs-lookup"><span data-stu-id="7be30-176">This setting indicates whether the parameter's value can contain wildcard characters so that the parameter value can be matched to more than one existing item in the target container.</span></span>

#### <a name="common-parameters"></a><span data-ttu-id="7be30-177">Vanliga parametrar</span><span class="sxs-lookup"><span data-stu-id="7be30-177">Common Parameters</span></span>

<span data-ttu-id="7be30-178">Vanliga parametrar är parametrar som du kan använda med valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7be30-178">Common parameters are parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="7be30-179">Mer information om vanliga parametrar finns [about_CommonParameters](about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7be30-179">For more information about common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7be30-180">Se även</span><span class="sxs-lookup"><span data-stu-id="7be30-180">See also</span></span>

[<span data-ttu-id="7be30-181">about_Command_syntax</span><span class="sxs-lookup"><span data-stu-id="7be30-181">about_Command_syntax</span></span>](about_Command_syntax.md)

[<span data-ttu-id="7be30-182">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="7be30-182">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="7be30-183">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="7be30-183">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="7be30-184">about_Parameters_Default_Values</span><span class="sxs-lookup"><span data-stu-id="7be30-184">about_Parameters_Default_Values</span></span>](about_Parameters_Default_Values.md)

[<span data-ttu-id="7be30-185">about_Pipelines</span><span class="sxs-lookup"><span data-stu-id="7be30-185">about_Pipelines</span></span>](about_Pipelines.md)

[<span data-ttu-id="7be30-186">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="7be30-186">about_Wildcards</span></span>](about_Wildcards.md)

