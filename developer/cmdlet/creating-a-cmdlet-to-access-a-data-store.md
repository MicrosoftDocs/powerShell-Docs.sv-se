---
title: Skapa en cmdlet för att komma åt ett datalager
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 7acccbd48dcfb654b11e448a1f24835ad3668fae
ms.sourcegitcommit: a02ccbeaa17c0e513d6c4a21b877c88ac7725458
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104467"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="e14e1-102">Skapa en cmdlet för att komma åt ett datalager</span><span class="sxs-lookup"><span data-stu-id="e14e1-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="e14e1-103">I det här avsnittet beskrivs hur du skapar en-cmdlet som använder lagrade data via en Windows PowerShell-Provider.</span><span class="sxs-lookup"><span data-stu-id="e14e1-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="e14e1-104">Den här typen av cmdlet använder Windows PowerShell-providerns infrastruktur i Windows PowerShell-körningsmiljön och därför måste cmdlet-klassen härledas från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="e14e1-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="e14e1-105">Cmdleten Select-Str som beskrivs här kan hitta och välja strängar i en fil eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="e14e1-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="e14e1-106">Mönstren som används för att identifiera strängen kan anges explicit genom `Path` parametern för cmdleten eller implicit `Script` via parametern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="e14e1-107">Cmdlet: en är utformad för att använda en Windows PowerShell-provider som är härledd från [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="e14e1-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="e14e1-108">Till exempel kan cmdleten ange fil Systems leverantören eller variabel leverantören som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e14e1-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="e14e1-109">Mer information aboutWindows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="e14e1-110">Definiera cmdlet-klassen</span><span class="sxs-lookup"><span data-stu-id="e14e1-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="e14e1-111">Det första steget i att skapa en cmdlet namnger alltid cmdleten och deklarerar den .NET-klass som implementerar cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="e14e1-112">Denna cmdlet identifierar vissa strängar, så verbet som väljs här är "Select", som definieras av klassen [system. Management. Automation. Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) .</span><span class="sxs-lookup"><span data-stu-id="e14e1-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="e14e1-113">Substantiv namnet "Str" används eftersom cmdleten fungerar på strängar.</span><span class="sxs-lookup"><span data-stu-id="e14e1-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="e14e1-114">I deklarationen nedan noterar du att cmdlet-verbet och Substantiv namnet visas i namnet på cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="e14e1-115">Mer information om godkända cmdlet-verb finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="e14e1-116">.NET-klassen för denna cmdlet måste vara härledd från Bask Lassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) , eftersom den ger support som krävs av Windows PowerShell-körningsmiljön för att exponera infrastrukturen för Windows PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="e14e1-117">Observera att denna cmdlet också använder .NET Framework reguljära uttryck klasser, till exempel [system. text. RegularExpressions. regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="e14e1-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="e14e1-118">Följande kod är klass definitionen för den här Select-Str-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="e14e1-119">Denna cmdlet definierar en standard parameter uppsättning genom att lägga `DefaultParameterSetName` till attributet nyckelord i klass deklarationen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="e14e1-120">Standard parameter uppsättningen `PatternParameterSet` används `Script` när parametern inte anges.</span><span class="sxs-lookup"><span data-stu-id="e14e1-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="e14e1-121">Mer information om den här parameter uppsättningen finns `Pattern` i diskussions parametern och `Script` i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e14e1-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="e14e1-122">Definiera parametrar för data åtkomst</span><span class="sxs-lookup"><span data-stu-id="e14e1-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="e14e1-123">Den här cmdleten definierar flera parametrar som ger användaren åtkomst till och undersöker lagrade data.</span><span class="sxs-lookup"><span data-stu-id="e14e1-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="e14e1-124">Dessa parametrar innehåller en `Path` parameter som anger platsen för data lagret, en `Pattern` parameter som anger det mönster som ska användas i sökningen och flera andra parametrar som stöder hur sökningen utförs.</span><span class="sxs-lookup"><span data-stu-id="e14e1-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="e14e1-125">Mer information om grunderna för att definiera parametrar finns i [lägga till parametrar som bearbetar kommando rads indata](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="e14e1-126">Att deklarera Sök vägs parametern</span><span class="sxs-lookup"><span data-stu-id="e14e1-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="e14e1-127">För att hitta data lagret måste denna cmdlet använda en Windows PowerShell-sökväg för att identifiera Windows PowerShell-providern som har utformats för att komma åt data lagret.</span><span class="sxs-lookup"><span data-stu-id="e14e1-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="e14e1-128">Därför definierar den en `Path` parameter av typen sträng mat ris för att ange var providern finns.</span><span class="sxs-lookup"><span data-stu-id="e14e1-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="e14e1-129">Observera att den här parametern tillhör två olika parameter uppsättningar och att den har ett alias.</span><span class="sxs-lookup"><span data-stu-id="e14e1-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="e14e1-130">Med två [system. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -attribut deklareras att `Path` `ScriptParameterSet` parametern tillhör och `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="e14e1-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="e14e1-131">Mer information om parameter uppsättningar finns i [lägga till parameter uppsättningar till en cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="e14e1-132">Attributet [system. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) deklarerar ett `PSPath` alias för `Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="e14e1-133">Att deklarera det här aliaset rekommenderas starkt för konsekvens med andra cmdletar som har åtkomst till Windows PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="e14e1-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="e14e1-134">Mer information aboutWindows PowerShell-sökvägar finns i "PowerShell Path Concepts" i [hur Windows PowerShell fungerar](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e14e1-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="e14e1-135">Att deklarera mönster parametern</span><span class="sxs-lookup"><span data-stu-id="e14e1-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="e14e1-136">För att ange mönster att söka efter, deklarerar denna cmdlet `Pattern` en parameter som är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="e14e1-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="e14e1-137">Ett positivt resultat returneras när något av mönstren hittas i data lagret.</span><span class="sxs-lookup"><span data-stu-id="e14e1-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="e14e1-138">Observera att dessa mönster kan kompileras i en matris med kompilerade reguljära uttryck eller en matris med jokertecken som används för litterala sökningar.</span><span class="sxs-lookup"><span data-stu-id="e14e1-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="e14e1-139">När den här parametern anges använder cmdleten standard parameter uppsättningen `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="e14e1-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="e14e1-140">I det här fallet använder cmdleten de mönster som anges här för att välja strängar.</span><span class="sxs-lookup"><span data-stu-id="e14e1-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="e14e1-141">Dessutom kan `Script` parametern även användas för att ange ett skript som innehåller mönstren.</span><span class="sxs-lookup"><span data-stu-id="e14e1-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="e14e1-142">Parametrarna `Script` och`Pattern` definierar två separata parameter uppsättningar, så de är ömsesidigt uteslutande.</span><span class="sxs-lookup"><span data-stu-id="e14e1-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="e14e1-143">Deklarera Sök support parametrar</span><span class="sxs-lookup"><span data-stu-id="e14e1-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="e14e1-144">Denna cmdlet definierar följande support parametrar som kan användas för att ändra Sök funktioner för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="e14e1-145">`Script` Parametern anger ett skript block som kan användas för att tillhandahålla en alternativ Sök funktion för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="e14e1-146">Skriptet måste innehålla de mönster som används för att matcha och returnera ett [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt.</span><span class="sxs-lookup"><span data-stu-id="e14e1-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="e14e1-147">Observera att den här parametern också är den unika parameter som identifierar `ScriptParameterSet` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="e14e1-148">När Windows PowerShell-körningsmiljön ser den här parametern används endast parametrar som tillhör `ScriptParameterSet` parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="e14e1-149">`SimpleMatch` Parametern är en switch-parameter som anger om cmdleten är att explicit matcha mönster när de anges.</span><span class="sxs-lookup"><span data-stu-id="e14e1-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="e14e1-150">När användaren anger parametern på kommando raden (`true`) använder cmdleten mönstren som de anges.</span><span class="sxs-lookup"><span data-stu-id="e14e1-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="e14e1-151">Om parametern inte anges (`false`) använder cmdleten reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="e14e1-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="e14e1-152">Standardvärdet för den här `false`parametern är.</span><span class="sxs-lookup"><span data-stu-id="e14e1-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="e14e1-153">`CaseSensitive` Parametern är en växel parameter som anger om en Skift läges känslig sökning utförs.</span><span class="sxs-lookup"><span data-stu-id="e14e1-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="e14e1-154">När användaren anger parametern på kommando raden (`true`) söker cmdleten efter versaler och gemener i tecknen när mönster jämförs.</span><span class="sxs-lookup"><span data-stu-id="e14e1-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="e14e1-155">Om parametern inte anges (`false`) särskiljer inte cmdleten mellan versaler och gemener.</span><span class="sxs-lookup"><span data-stu-id="e14e1-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="e14e1-156">Till exempel "min fil" och "min fil" skulle båda returneras som positiva träffar.</span><span class="sxs-lookup"><span data-stu-id="e14e1-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="e14e1-157">Standardvärdet för den här `false`parametern är.</span><span class="sxs-lookup"><span data-stu-id="e14e1-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="e14e1-158">Parametrarna `Exclude` och`Include` identifierar objekt som uttryckligen utesluts från eller ingår i sökningen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="e14e1-159">Som standard söker cmdleten igenom alla objekt i data lagret.</span><span class="sxs-lookup"><span data-stu-id="e14e1-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="e14e1-160">Men om du vill begränsa sökningen som utförs av cmdleten, kan dessa parametrar användas för att explicit ange objekt som ska inkluderas i sökningen eller utelämnas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="e14e1-161">Deklarera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="e14e1-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="e14e1-162">Denna cmdlet använder två parameter uppsättningar (`ScriptParameterSet` och `PatternParameterSet`standard) som namnen på två parameter uppsättningar som används i data åtkomst.</span><span class="sxs-lookup"><span data-stu-id="e14e1-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="e14e1-163">`PatternParameterSet`är standard parameter uppsättningen och används när `Pattern` parametern anges.</span><span class="sxs-lookup"><span data-stu-id="e14e1-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="e14e1-164">`ScriptParameterSet`används när användaren anger en alternativ Sök funktion via `Script` parametern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="e14e1-165">Mer information om parameter uppsättningar finns i [lägga till parameter uppsättningar till en cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="e14e1-166">Åsidosätta metoder för bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="e14e1-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="e14e1-167">Cmdletar måste åsidosätta en eller flera av metoderna för bearbetning av indata för klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="e14e1-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="e14e1-168">Mer information om metoder för att bearbeta indata finns i [skapa din första cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e14e1-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="e14e1-169">Denna cmdlet åsidosätter metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att bygga en matris med kompilerade reguljära uttryck vid start.</span><span class="sxs-lookup"><span data-stu-id="e14e1-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="e14e1-170">Detta ökar prestanda vid sökningar som inte använder enkel matchning.</span><span class="sxs-lookup"><span data-stu-id="e14e1-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="e14e1-171">Denna cmdlet åsidosätter också metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att bearbeta de sträng markeringar som användaren gör på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e14e1-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="e14e1-172">Det skriver resultatet av sträng urvalet i form av ett anpassat objekt genom att anropa en privat **MatchString** -metod.</span><span class="sxs-lookup"><span data-stu-id="e14e1-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="e14e1-173">Åtkomst till innehåll</span><span class="sxs-lookup"><span data-stu-id="e14e1-173">Accessing Content</span></span>

<span data-ttu-id="e14e1-174">Din cmdlet måste öppna den provider som anges av Windows PowerShell-sökvägen så att den kan komma åt data.</span><span class="sxs-lookup"><span data-stu-id="e14e1-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="e14e1-175">Objektet [system. Management. Automation. sessionState](/dotnet/api/System.Management.Automation.SessionState) för körnings utrymme används för åtkomst till providern, medan egenskapen [system. Management. Automation. PSCmdlet. Invokeprovider \*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) för cmdlet används för att öppna providern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="e14e1-176">Åtkomst till innehåll tillhandahålls genom hämtning av objektet [system. Management. Automation. Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) för den öppna providern.</span><span class="sxs-lookup"><span data-stu-id="e14e1-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="e14e1-177">Det här exemplet Select-Str cmdlet använder egenskapen [system. Management. Automation. Providerintrinsics. Content \*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) för att exponera det innehåll som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="e14e1-178">Sedan kan du anropa metoden [system. Management. Automation. Contentcmdletproviderintrinsics. Getreader \*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) genom att skicka den nödvändiga sökvägen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e14e1-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e14e1-179">Kod exempel</span><span class="sxs-lookup"><span data-stu-id="e14e1-179">Code Sample</span></span>

<span data-ttu-id="e14e1-180">Följande kod visar implementeringen av den här versionen av den här Select-Str-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="e14e1-181">Observera att den här koden innehåller cmdlet-klassen, privata metoder som används av cmdleten och Windows PowerShell snap-in-koden som används för att registrera cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="e14e1-182">Mer information om hur du registrerar cmdleten finns i [skapa cmdleten](#defining-the-cmdlet-class).</span><span class="sxs-lookup"><span data-stu-id="e14e1-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="e14e1-183">Skapa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e14e1-183">Building the Cmdlet</span></span>

<span data-ttu-id="e14e1-184">När du har implementerat en cmdlet måste du registrera den med Windows PowerShell via en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="e14e1-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="e14e1-185">Mer information om att registrera cmdlets finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="e14e1-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="e14e1-186">Testa cmdleten</span><span class="sxs-lookup"><span data-stu-id="e14e1-186">Testing the Cmdlet</span></span>

<span data-ttu-id="e14e1-187">När din cmdlet har registrerats med Windows PowerShell kan du testa den genom att köra den på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e14e1-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="e14e1-188">Följande procedur kan användas för att testa Sample Select-Str-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e14e1-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="e14e1-189">Starta Windows PowerShell och Sök efter förekomster av rader med uttrycket ".NET" i antecknings filen.</span><span class="sxs-lookup"><span data-stu-id="e14e1-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="e14e1-190">Observera att citat tecknen runt namnet på sökvägen endast krävs om sökvägen består av mer än ett ord.</span><span class="sxs-lookup"><span data-stu-id="e14e1-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="e14e1-191">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="e14e1-192">Sök i antecknings filen efter förekomster av rader med ordet "över", följt av annan text.</span><span class="sxs-lookup"><span data-stu-id="e14e1-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="e14e1-193">Parametern använder standardvärdet `false`. `SimpleMatch`</span><span class="sxs-lookup"><span data-stu-id="e14e1-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="e14e1-194">Sökningen är Skift läges okänslig eftersom `CaseSensitive` parametern har angetts till. `false`</span><span class="sxs-lookup"><span data-stu-id="e14e1-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="e14e1-195">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="e14e1-196">Sök i antecknings filen med ett reguljärt uttryck som mönster.</span><span class="sxs-lookup"><span data-stu-id="e14e1-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="e14e1-197">Cmdleten söker efter alfabetiska tecken och blank steg inom parentes.</span><span class="sxs-lookup"><span data-stu-id="e14e1-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="e14e1-198">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="e14e1-199">Utför en Skift läges känslig sökning av antecknings filen för förekomster av ordet "parameter".</span><span class="sxs-lookup"><span data-stu-id="e14e1-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="e14e1-200">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="e14e1-201">Sök i variabel leverantören som levererades med Windows PowerShell för variabler som har numeriska värden från 0 till 9.</span><span class="sxs-lookup"><span data-stu-id="e14e1-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="e14e1-202">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="e14e1-203">Använd ett-skript block för att söka i filen SelectStrCommandSample.cs efter strängen "POS".</span><span class="sxs-lookup"><span data-stu-id="e14e1-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="e14e1-204">**Cmatch** -funktionen för skriptet utför en Skift läges okänslig mönster matchning.</span><span class="sxs-lookup"><span data-stu-id="e14e1-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="e14e1-205">Följande utdata visas.</span><span class="sxs-lookup"><span data-stu-id="e14e1-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="e14e1-206">Se även</span><span class="sxs-lookup"><span data-stu-id="e14e1-206">See Also</span></span>

[<span data-ttu-id="e14e1-207">Så här skapar du en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e14e1-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="e14e1-208">Skapa din första cmdlet</span><span class="sxs-lookup"><span data-stu-id="e14e1-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="e14e1-209">Skapa en cmdlet som ändrar systemet</span><span class="sxs-lookup"><span data-stu-id="e14e1-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="e14e1-210">Utforma din Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="e14e1-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="e14e1-211">[Så här fungerar Windows PowerShell](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e14e1-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="e14e1-212">[Registrera cmdlets, providers och värd program](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="e14e1-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="e14e1-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e14e1-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
