---
description: Beskriver hur du skapar och använder funktioner i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 2/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: 25ef4d3f12752bfabc47d6519988d0da3d5ab0db
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270032"
---
# <a name="about-functions"></a><span data-ttu-id="a7008-104">Om Functions</span><span class="sxs-lookup"><span data-stu-id="a7008-104">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="a7008-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="a7008-105">Short description</span></span>

<span data-ttu-id="a7008-106">Beskriver hur du skapar och använder funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a7008-106">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="a7008-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="a7008-107">Long description</span></span>

<span data-ttu-id="a7008-108">En funktion är en lista med PowerShell-instruktioner som har ett namn som du tilldelar.</span><span class="sxs-lookup"><span data-stu-id="a7008-108">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="a7008-109">När du kör en funktion skriver du funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="a7008-109">When you run a function, you type the function name.</span></span> <span data-ttu-id="a7008-110">Instruktionerna i listan körs som om du hade skrivit dem i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="a7008-110">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="a7008-111">Funktioner kan vara så enkla som möjligt:</span><span class="sxs-lookup"><span data-stu-id="a7008-111">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="a7008-112">En funktion kan också vara så komplex som en cmdlet eller ett program program.</span><span class="sxs-lookup"><span data-stu-id="a7008-112">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="a7008-113">Precis som-cmdlets kan funktioner ha parametrar.</span><span class="sxs-lookup"><span data-stu-id="a7008-113">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="a7008-114">Parametrarna kan vara namngivna, positions-, växlings-eller dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="a7008-114">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="a7008-115">Funktions parametrar kan läsas från kommando raden eller från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-115">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="a7008-116">Funktioner kan returnera värden som kan visas, tilldelas variabler eller skickas till andra funktioner eller cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a7008-116">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="a7008-117">Du kan också ange ett retur värde med hjälp av `return` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a7008-117">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="a7008-118">`return`Nyckelordet påverkar eller utelämnar inte andra utdata som returneras från din funktion.</span><span class="sxs-lookup"><span data-stu-id="a7008-118">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="a7008-119">`return`Nyckelordet avslutar dock funktionen på raden.</span><span class="sxs-lookup"><span data-stu-id="a7008-119">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="a7008-120">Mer information finns i [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-120">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="a7008-121">Funktionens instruktions lista kan innehålla olika typer av uttrycks listor med nyckelorden `Begin` , `Process` och `End` .</span><span class="sxs-lookup"><span data-stu-id="a7008-121">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="a7008-122">De här instruktions listorna hanterar inmatade från pipelinen på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="a7008-122">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="a7008-123">Ett filter är en särskild typ av funktion som använder `Filter` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a7008-123">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="a7008-124">Funktioner kan också fungera som cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a7008-124">Functions can also act like cmdlets.</span></span> <span data-ttu-id="a7008-125">Du kan skapa en funktion som fungerar precis som en cmdlet utan att använda `C#` programmering.</span><span class="sxs-lookup"><span data-stu-id="a7008-125">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="a7008-126">Mer information finns i [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-126">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="a7008-127">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7008-127">Syntax</span></span>

<span data-ttu-id="a7008-128">Följande är syntaxen för en funktion:</span><span class="sxs-lookup"><span data-stu-id="a7008-128">The following is the syntax for a function:</span></span>

```
function [<scope:>]<name> [([type]$parameter1[,[type]$parameter2])]
{
  param([type]$parameter1 [,[type]$parameter2])
  dynamicparam {<statement list>}
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="a7008-129">En funktion innehåller följande objekt:</span><span class="sxs-lookup"><span data-stu-id="a7008-129">A function includes the following items:</span></span>

- <span data-ttu-id="a7008-130">Ett `Function` nyckelord</span><span class="sxs-lookup"><span data-stu-id="a7008-130">A `Function` keyword</span></span>
- <span data-ttu-id="a7008-131">Ett omfång (valfritt)</span><span class="sxs-lookup"><span data-stu-id="a7008-131">A scope (optional)</span></span>
- <span data-ttu-id="a7008-132">Ett namn som du väljer</span><span class="sxs-lookup"><span data-stu-id="a7008-132">A name that you select</span></span>
- <span data-ttu-id="a7008-133">Valfritt antal namngivna parametrar (valfritt)</span><span class="sxs-lookup"><span data-stu-id="a7008-133">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="a7008-134">Ett eller flera PowerShell-kommandon inom klammerparentes `{}`</span><span class="sxs-lookup"><span data-stu-id="a7008-134">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="a7008-135">Mer information om `Dynamicparam` nyckelordet och dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-135">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="a7008-136">Enkla funktioner</span><span class="sxs-lookup"><span data-stu-id="a7008-136">Simple Functions</span></span>

<span data-ttu-id="a7008-137">Funktionerna behöver inte vara komplicerade för att vara användbara.</span><span class="sxs-lookup"><span data-stu-id="a7008-137">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="a7008-138">De enklaste funktionerna har följande format:</span><span class="sxs-lookup"><span data-stu-id="a7008-138">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="a7008-139">Följande funktion startar till exempel PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="a7008-139">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="a7008-140">Om du vill använda funktionen skriver du: `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="a7008-140">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="a7008-141">Om du vill lägga till instruktioner till funktionen skriver du varje instruktion på en separat rad eller använder ett semikolon `;` för att avgränsa satserna.</span><span class="sxs-lookup"><span data-stu-id="a7008-141">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="a7008-142">Följande funktion hittar till exempel alla `.jpg` filer i den aktuella användarens kataloger som har ändrats efter start datumet.</span><span class="sxs-lookup"><span data-stu-id="a7008-142">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="a7008-143">Du kan skapa en verktygs låda med användbara små funktioner.</span><span class="sxs-lookup"><span data-stu-id="a7008-143">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="a7008-144">Lägg till dessa funktioner i din PowerShell-profil, enligt beskrivningen i [about_Profiles](about_Profiles.md) och senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a7008-144">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="a7008-145">Funktions namn</span><span class="sxs-lookup"><span data-stu-id="a7008-145">Function Names</span></span>

<span data-ttu-id="a7008-146">Du kan tilldela ett namn till en funktion, men funktioner som du delar med andra bör följa de namngivnings regler som har upprättats för alla PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="a7008-146">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="a7008-147">Funktions namn ska bestå av ett verb-Substantiv-par där verbet identifierar den åtgärd som funktionen utför och Substantiv identifierar objektet som cmdleten utför åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="a7008-147">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="a7008-148">Funktioner bör använda standardverb som har godkänts för alla PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="a7008-148">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="a7008-149">De här verben hjälper oss att hålla våra kommando namn enkla, konsekventa och enkla för användare att förstå.</span><span class="sxs-lookup"><span data-stu-id="a7008-149">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="a7008-150">Mer information om standard PowerShell-verben finns i [godkända verb](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="a7008-150">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="a7008-151">Funktioner med parametrar</span><span class="sxs-lookup"><span data-stu-id="a7008-151">Functions with Parameters</span></span>

<span data-ttu-id="a7008-152">Du kan använda parametrar med Functions, inklusive namngivna parametrar, positions parametrar, växel parametrar och dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="a7008-152">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="a7008-153">Mer information om dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-153">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="a7008-154">Namngivna parametrar</span><span class="sxs-lookup"><span data-stu-id="a7008-154">Named Parameters</span></span>

<span data-ttu-id="a7008-155">Du kan definiera valfritt antal namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="a7008-155">You can define any number of named parameters.</span></span> <span data-ttu-id="a7008-156">Du kan inkludera ett standardvärde för namngivna parametrar, enligt beskrivningen längre fram i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a7008-156">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="a7008-157">Du kan definiera parametrar inom klammerparenteserna med hjälp av `Param` nyckelordet, som du ser i följande exempel-syntax:</span><span class="sxs-lookup"><span data-stu-id="a7008-157">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="a7008-158">Du kan också definiera parametrar utanför klamrarna utan `Param` nyckelord, som du ser i följande exempel-syntax:</span><span class="sxs-lookup"><span data-stu-id="a7008-158">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="a7008-159">Nedan visas ett exempel på den här alternativa syntaxen.</span><span class="sxs-lookup"><span data-stu-id="a7008-159">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="a7008-160">Den första metoden är att föredra, men det finns ingen skillnad mellan dessa två metoder.</span><span class="sxs-lookup"><span data-stu-id="a7008-160">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="a7008-161">När du kör funktionen tilldelas värdet som du anger för en parameter en variabel som innehåller parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="a7008-161">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="a7008-162">Värdet för variabeln kan användas i-funktionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-162">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="a7008-163">Följande exempel är en funktion som kallas `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="a7008-163">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="a7008-164">Den här funktionen har en `$Size` parameter.</span><span class="sxs-lookup"><span data-stu-id="a7008-164">This function has a `$Size` parameter.</span></span> <span data-ttu-id="a7008-165">Funktionen visar alla filer som är mindre än värdet för `$Size` parametern och undantar kataloger:</span><span class="sxs-lookup"><span data-stu-id="a7008-165">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="a7008-166">I funktionen kan du använda `$Size` variabeln, som är det namn som definierats för parametern.</span><span class="sxs-lookup"><span data-stu-id="a7008-166">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="a7008-167">Om du vill använda den här funktionen skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a7008-167">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="a7008-168">Du kan också ange ett värde för en namngiven parameter utan parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="a7008-168">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="a7008-169">Till exempel ger följande kommando samma resultat som ett kommando som namnger **storleks** parametern:</span><span class="sxs-lookup"><span data-stu-id="a7008-169">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="a7008-170">Om du vill definiera ett standardvärde för en parameter skriver du ett likhets tecken och värdet efter parameter namnet, som du ser i följande variant av `Get-SmallFiles` exemplet:</span><span class="sxs-lookup"><span data-stu-id="a7008-170">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="a7008-171">Om du skriver `Get-SmallFiles` utan ett värde tilldelar funktionen 100 till `$size` .</span><span class="sxs-lookup"><span data-stu-id="a7008-171">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="a7008-172">Om du anger ett värde använder funktionen det värdet.</span><span class="sxs-lookup"><span data-stu-id="a7008-172">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="a7008-173">Alternativt kan du ange en kort hjälp sträng som beskriver standardvärdet för din parameter genom att lägga till attributet **PSDefaultValue** i beskrivningen av parametern och ange egenskapen **Help** för **PSDefaultValue**.</span><span class="sxs-lookup"><span data-stu-id="a7008-173">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="a7008-174">Om du vill ange en hjälp sträng som beskriver standardvärdet (100) för **storleks** parametern i `Get-SmallFiles` funktionen, lägger du till attributet **PSDefaultValue** som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="a7008-174">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="a7008-175">Mer information om klassen **PSDefaultValue** finns i [PSDefaultValue-attribut medlemmar](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span><span class="sxs-lookup"><span data-stu-id="a7008-175">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="a7008-176">Positions parametrar</span><span class="sxs-lookup"><span data-stu-id="a7008-176">Positional Parameters</span></span>

<span data-ttu-id="a7008-177">En positions parameter är en parameter utan parameter namn.</span><span class="sxs-lookup"><span data-stu-id="a7008-177">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="a7008-178">PowerShell använder parameter värde ordningen för att koppla varje parameter värde till en parameter i funktionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-178">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="a7008-179">När du använder positions parametrar, anger du ett eller flera värden efter funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="a7008-179">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="a7008-180">Positions parameter värden tilldelas till `$args` mat ris variabeln.</span><span class="sxs-lookup"><span data-stu-id="a7008-180">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="a7008-181">Värdet som följer funktions namnet tilldelas till den första positionen i `$args` matrisen `$args[0]` .</span><span class="sxs-lookup"><span data-stu-id="a7008-181">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="a7008-182">Följande `Get-Extension` funktion lägger till `.txt` fil namns tillägget i ett fil namn som du anger:</span><span class="sxs-lookup"><span data-stu-id="a7008-182">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

```powershell
function Get-Extension {
  $name = $args[0] + ".txt"
  $name
}
```

```powershell
Get-Extension myTextFile
```

```Output
myTextFile.txt
```

### <a name="switch-parameters"></a><span data-ttu-id="a7008-183">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="a7008-183">Switch Parameters</span></span>

<span data-ttu-id="a7008-184">En växel är en parameter som inte kräver något värde.</span><span class="sxs-lookup"><span data-stu-id="a7008-184">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="a7008-185">I stället skriver du funktions namnet följt av namnet på växel parametern.</span><span class="sxs-lookup"><span data-stu-id="a7008-185">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="a7008-186">Definiera en växlings parameter genom att ange typen `[switch]` före parameter namnet, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a7008-186">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="a7008-187">När du skriver `On` parametern switch efter funktions namnet visar funktionen "växla på".</span><span class="sxs-lookup"><span data-stu-id="a7008-187">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="a7008-188">Utan parametern switch visas "Inaktivera".</span><span class="sxs-lookup"><span data-stu-id="a7008-188">Without the switch parameter, it displays "Switch off".</span></span>

```powershell
Switch-Item -on
```

```Output
Switch on
```

```powershell
Switch-Item
```

```Output
Switch off
```

<span data-ttu-id="a7008-189">Du kan också tilldela ett **booleskt** värde till en växel när du kör funktionen, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a7008-189">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

```powershell
Switch-Item -on:$true
```

```Output
Switch on
```

```powershell
Switch-Item -on:$false
```

```Output
Switch off
```

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="a7008-190">Använda Ihopbuntning för att representera kommando parametrar</span><span class="sxs-lookup"><span data-stu-id="a7008-190">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="a7008-191">Du kan använda ihopbuntning för att representera parametrarna för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="a7008-191">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="a7008-192">Den här funktionen introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a7008-192">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="a7008-193">Använd den här metoden i functions som anropar kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-193">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="a7008-194">Du behöver inte deklarera eller räkna upp kommando parametrarna eller ändra funktionen när kommando parametrar ändras.</span><span class="sxs-lookup"><span data-stu-id="a7008-194">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="a7008-195">Följande exempel funktion anropar `Get-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a7008-195">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="a7008-196">Kommandot används `@Args` för att representera parametrarna för `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="a7008-196">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="a7008-197">Du kan använda alla parametrar `Get-Command` när du anropar `Get-MyCommand` funktionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-197">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="a7008-198">Parametrar och parameter värden skickas till kommandot med hjälp av `@Args` .</span><span class="sxs-lookup"><span data-stu-id="a7008-198">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="a7008-199">`@Args`Funktionen använder den `$Args` automatiska parametern som representerar odeklarerade cmdlet-parametrar och värden från återstående argument.</span><span class="sxs-lookup"><span data-stu-id="a7008-199">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="a7008-200">Mer information om ihopbuntning finns i [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-200">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="a7008-201">Rör objekt till Functions</span><span class="sxs-lookup"><span data-stu-id="a7008-201">Piping Objects to Functions</span></span>

<span data-ttu-id="a7008-202">Alla funktioner kan ta inmatade från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-202">Any function can take input from the pipeline.</span></span> <span data-ttu-id="a7008-203">Du kan styra hur en funktion bearbetar inmatade värden från pipelinen med hjälp av `Begin` , `Process` och `End` .</span><span class="sxs-lookup"><span data-stu-id="a7008-203">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="a7008-204">Följande exempel-syntax visar de tre nyckelorden:</span><span class="sxs-lookup"><span data-stu-id="a7008-204">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="a7008-205">`Begin`Instruktions listan körs bara en gång, i början av funktionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-205">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a7008-206">Om din funktion definierar ett `Begin` , `Process` eller ett `End` block, måste all kod finnas inuti dessa block.</span><span class="sxs-lookup"><span data-stu-id="a7008-206">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="a7008-207">Ingen kod kommer att identifieras utanför blocken om *något* av blocken har definierats.</span><span class="sxs-lookup"><span data-stu-id="a7008-207">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="a7008-208">`Process`Instruktions listan körs en gången för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-208">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="a7008-209">Även om `Process` blocket körs, tilldelas varje pipeline-objekt den `$_` automatiska variabeln, ett pipeline-objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="a7008-209">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="a7008-210">När funktionen tar emot alla objekt i pipelinen `End` körs instruktions listan en enda gången.</span><span class="sxs-lookup"><span data-stu-id="a7008-210">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="a7008-211">Om nej `Begin` , `Process` eller `End` nyckelord används, behandlas alla instruktioner som en `End` instruktions lista.</span><span class="sxs-lookup"><span data-stu-id="a7008-211">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="a7008-212">Följande funktion använder `Process` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a7008-212">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="a7008-213">Funktionen visar exempel från pipelinen:</span><span class="sxs-lookup"><span data-stu-id="a7008-213">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="a7008-214">Visa den här funktionen genom att ange en lista med siffror avgränsade med kommatecken, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a7008-214">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="a7008-215">När du använder en funktion i en pipeline, tilldelas de objekt som skickas till funktionen den `$input` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="a7008-215">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="a7008-216">Funktionen kör instruktioner med `Begin` nyckelordet innan några objekt kommer från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-216">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="a7008-217">Funktionen kör instruktioner med `End` nyckelordet när alla objekt har tagits emot från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-217">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="a7008-218">I följande exempel visas den `$input` automatiska variabeln med `Begin` och `End` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a7008-218">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="a7008-219">Om den här funktionen körs med hjälp av pipelinen visas följande resultat:</span><span class="sxs-lookup"><span data-stu-id="a7008-219">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="a7008-220">När `Begin` instruktionen körs har funktionen inte inmatade värden från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-220">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="a7008-221">`End`Instruktionen körs när funktionen har värden.</span><span class="sxs-lookup"><span data-stu-id="a7008-221">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="a7008-222">Om funktionen har ett `Process` nyckelord tas varje objekt i som `$input` tas bort från `$input` och tilldelas `$_` .</span><span class="sxs-lookup"><span data-stu-id="a7008-222">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="a7008-223">I följande exempel finns en `Process` instruktions lista:</span><span class="sxs-lookup"><span data-stu-id="a7008-223">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="a7008-224">I det här exemplet skickas varje objekt som är skickas till funktionen till `Process` instruktions listan.</span><span class="sxs-lookup"><span data-stu-id="a7008-224">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="a7008-225">De `Process` instruktioner som körs för varje objekt, ett objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="a7008-225">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="a7008-226">Den `$input` automatiska variabeln är tom när funktionen når `End` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a7008-226">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="a7008-227">Mer information finns i [använda uppräknare](about_Automatic_Variables.md#using-enumerators)</span><span class="sxs-lookup"><span data-stu-id="a7008-227">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="a7008-228">Filter</span><span class="sxs-lookup"><span data-stu-id="a7008-228">Filters</span></span>

<span data-ttu-id="a7008-229">Ett filter är en typ av funktion som körs på varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a7008-229">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="a7008-230">Ett filter liknar en funktion med alla dess uttryck i ett `Process` block.</span><span class="sxs-lookup"><span data-stu-id="a7008-230">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="a7008-231">Syntaxen för ett filter är följande:</span><span class="sxs-lookup"><span data-stu-id="a7008-231">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="a7008-232">Följande filter använder logg poster från pipelinen och visar sedan antingen hela posten eller bara meddelande delen av posten:</span><span class="sxs-lookup"><span data-stu-id="a7008-232">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="a7008-233">Funktions omfång</span><span class="sxs-lookup"><span data-stu-id="a7008-233">Function Scope</span></span>

<span data-ttu-id="a7008-234">Det finns en funktion i omfånget som den skapades i.</span><span class="sxs-lookup"><span data-stu-id="a7008-234">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="a7008-235">Om en funktion är en del av ett skript är funktionen tillgänglig för instruktioner i skriptet.</span><span class="sxs-lookup"><span data-stu-id="a7008-235">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="a7008-236">Som standard är en funktion i ett skript inte tillgänglig i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="a7008-236">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="a7008-237">Du kan ange omfattningen för en funktion.</span><span class="sxs-lookup"><span data-stu-id="a7008-237">You can specify the scope of a function.</span></span> <span data-ttu-id="a7008-238">Funktionen läggs till exempel till i det globala omfånget i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="a7008-238">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="a7008-239">När en funktion finns i det globala omfånget kan du använda funktionen i skript, i functions och på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="a7008-239">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="a7008-240">Functions skapar vanligt vis ett definitions område.</span><span class="sxs-lookup"><span data-stu-id="a7008-240">Functions normally create a scope.</span></span> <span data-ttu-id="a7008-241">De objekt som skapas i en funktion, till exempel variabler, finns bara i funktions omfånget.</span><span class="sxs-lookup"><span data-stu-id="a7008-241">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="a7008-242">Mer information om omfång i PowerShell finns [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-242">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="a7008-243">Hitta och hantera funktioner med funktionen: enhet</span><span class="sxs-lookup"><span data-stu-id="a7008-243">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="a7008-244">Alla funktioner och filter i PowerShell lagras automatiskt i `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="a7008-244">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="a7008-245">Enheten exponeras av PowerShell- **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="a7008-245">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="a7008-246">När du refererar till `Function:` enheten skriver du ett kolon efter- **funktionen** , precis som du skulle göra när du refererar `C` till `D` en dators eller datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="a7008-246">When referring to the `Function:` drive, type a colon after **Function** , just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="a7008-247">Följande kommando visar alla funktioner i den aktuella sessionen av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a7008-247">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="a7008-248">Kommandona i funktionen lagras som ett skript block i funktionens definitions egenskap.</span><span class="sxs-lookup"><span data-stu-id="a7008-248">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="a7008-249">Om du till exempel vill visa kommandona i Hjälp funktionen som medföljer PowerShell, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a7008-249">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="a7008-250">Du kan också använda följande syntax.</span><span class="sxs-lookup"><span data-stu-id="a7008-250">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="a7008-251">Mer information om `Function:` enheten finns i hjälp avsnittet för **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="a7008-251">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="a7008-252">Skriv `Get-Help Function`.</span><span class="sxs-lookup"><span data-stu-id="a7008-252">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="a7008-253">Återanvända funktioner i nya sessioner</span><span class="sxs-lookup"><span data-stu-id="a7008-253">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="a7008-254">När du skriver en funktion i PowerShell-Kommandotolken blir funktionen en del av den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a7008-254">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="a7008-255">Den är tillgänglig tills sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="a7008-255">It is available until the session ends.</span></span>

<span data-ttu-id="a7008-256">Om du vill använda din funktion i alla PowerShell-sessioner lägger du till funktionen i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="a7008-256">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="a7008-257">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-257">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="a7008-258">Du kan också spara din funktion i en PowerShell-skriptfil.</span><span class="sxs-lookup"><span data-stu-id="a7008-258">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="a7008-259">Skriv din funktion i en textfil och spara sedan filen med `.ps1` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="a7008-259">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="a7008-260">Skriver hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="a7008-260">Writing Help for Functions</span></span>

<span data-ttu-id="a7008-261">Cmdlet: en `Get-Help` får hjälp för funktioner, samt för cmdlets, providers och skript.</span><span class="sxs-lookup"><span data-stu-id="a7008-261">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="a7008-262">Om du vill ha hjälp med en funktion skriver du `Get-Help` följt av funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="a7008-262">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="a7008-263">Om du till exempel vill få hjälp med `Get-MyDisks` funktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="a7008-263">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="a7008-264">Du kan skriva hjälp för en funktion med någon av följande två metoder:</span><span class="sxs-lookup"><span data-stu-id="a7008-264">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="a7008-265">Comment-Based hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="a7008-265">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="a7008-266">Skapa ett hjälp avsnitt genom att använda särskilda nyckelord i kommentarerna.</span><span class="sxs-lookup"><span data-stu-id="a7008-266">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="a7008-267">Om du vill skapa en kommenterad hjälp för en funktion måste kommentarerna placeras i början eller slutet av funktions texten eller på de rader som föregår nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="a7008-267">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="a7008-268">Mer information om kommenterad hjälp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-268">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="a7008-269">XML-Based hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="a7008-269">XML-Based Help for Functions</span></span>

  <span data-ttu-id="a7008-270">Skapa ett XML-baserat hjälp avsnitt, till exempel den typ som vanligt vis skapas för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="a7008-270">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="a7008-271">XML-baserad hjälp krävs om du lokaliserar hjälp ämnen till flera språk.</span><span class="sxs-lookup"><span data-stu-id="a7008-271">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="a7008-272">Om du vill associera funktionen med det XML-baserade hjälp avsnittet använder du det `.ExternalHelp` kommenterings-baserade hjälp nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="a7008-272">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="a7008-273">Utan det här nyckelordet `Get-Help` kan du inte hitta funktions hjälp avsnittet och anropar till `Get-Help` för funktionen returnera endast den automatiskt genererade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="a7008-273">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="a7008-274">Mer information om `ExternalHelp` nyckelordet finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-274">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="a7008-275">Mer information om XML-baserad hjälp finns i [så här skriver du cmdlet-hjälpen](https://go.microsoft.com/fwlink/?LinkID=123415) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="a7008-275">For more information about XML-based help, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7008-276">Se även</span><span class="sxs-lookup"><span data-stu-id="a7008-276">See also</span></span>

[<span data-ttu-id="a7008-277">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a7008-277">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="a7008-278">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="a7008-278">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="a7008-279">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="a7008-279">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="a7008-280">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="a7008-280">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="a7008-281">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="a7008-281">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="a7008-282">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="a7008-282">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="a7008-283">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="a7008-283">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="a7008-284">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="a7008-284">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="a7008-285">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="a7008-285">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="a7008-286">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="a7008-286">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="a7008-287">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="a7008-287">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="a7008-288">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="a7008-288">about_Function_provider</span></span>](about_Function_provider.md)
