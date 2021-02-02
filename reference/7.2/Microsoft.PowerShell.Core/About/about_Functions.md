---
description: Beskriver hur du skapar och använder funktioner i PowerShell.
Locale: en-US
ms.date: 02/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions
ms.openlocfilehash: d51c4d0bbf728bb23b4a5452d5192a262b722758
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710224"
---
# <a name="about-functions"></a><span data-ttu-id="e1b07-103">Om Functions</span><span class="sxs-lookup"><span data-stu-id="e1b07-103">About Functions</span></span>

## <a name="short-description"></a><span data-ttu-id="e1b07-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1b07-104">Short description</span></span>

<span data-ttu-id="e1b07-105">Beskriver hur du skapar och använder funktioner i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1b07-105">Describes how to create and use functions in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="e1b07-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e1b07-106">Long description</span></span>

<span data-ttu-id="e1b07-107">En funktion är en lista med PowerShell-instruktioner som har ett namn som du tilldelar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-107">A function is a list of PowerShell statements that has a name that you assign.</span></span> <span data-ttu-id="e1b07-108">När du kör en funktion skriver du funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-108">When you run a function, you type the function name.</span></span> <span data-ttu-id="e1b07-109">Instruktionerna i listan körs som om du hade skrivit dem i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="e1b07-109">The statements in the list run as if you had typed them at the command prompt.</span></span>

<span data-ttu-id="e1b07-110">Funktioner kan vara så enkla som möjligt:</span><span class="sxs-lookup"><span data-stu-id="e1b07-110">Functions can be as simple as:</span></span>

```powershell
function Get-PowerShellProcess { Get-Process PowerShell }
```

<span data-ttu-id="e1b07-111">En funktion kan också vara så komplex som en cmdlet eller ett program program.</span><span class="sxs-lookup"><span data-stu-id="e1b07-111">A function can also be as complex as a cmdlet or an application program.</span></span>

<span data-ttu-id="e1b07-112">Precis som-cmdlets kan funktioner ha parametrar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-112">Like cmdlets, functions can have parameters.</span></span> <span data-ttu-id="e1b07-113">Parametrarna kan vara namngivna, positions-, växlings-eller dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-113">The parameters can be named, positional, switch, or dynamic parameters.</span></span> <span data-ttu-id="e1b07-114">Funktions parametrar kan läsas från kommando raden eller från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-114">Function parameters can be read from the command line or from the pipeline.</span></span>

<span data-ttu-id="e1b07-115">Funktioner kan returnera värden som kan visas, tilldelas variabler eller skickas till andra funktioner eller cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-115">Functions can return values that can be displayed, assigned to variables, or passed to other functions or cmdlets.</span></span> <span data-ttu-id="e1b07-116">Du kan också ange ett retur värde med hjälp av `return` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-116">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="e1b07-117">`return`Nyckelordet påverkar eller utelämnar inte andra utdata som returneras från din funktion.</span><span class="sxs-lookup"><span data-stu-id="e1b07-117">The `return` keyword does not affect or suppress other output returned from your function.</span></span> <span data-ttu-id="e1b07-118">`return`Nyckelordet avslutar dock funktionen på raden.</span><span class="sxs-lookup"><span data-stu-id="e1b07-118">However, the `return` keyword exits the function at that line.</span></span> <span data-ttu-id="e1b07-119">Mer information finns i [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-119">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="e1b07-120">Funktionens instruktions lista kan innehålla olika typer av uttrycks listor med nyckelorden `Begin` , `Process` och `End` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-120">The function's statement list can contain different types of statement lists with the keywords `Begin`, `Process`, and `End`.</span></span> <span data-ttu-id="e1b07-121">De här instruktions listorna hanterar inmatade från pipelinen på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="e1b07-121">These statement lists handle input from the pipeline differently.</span></span>

<span data-ttu-id="e1b07-122">Ett filter är en särskild typ av funktion som använder `Filter` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-122">A filter is a special kind of function that uses the `Filter` keyword.</span></span>

<span data-ttu-id="e1b07-123">Funktioner kan också fungera som cmdlets.</span><span class="sxs-lookup"><span data-stu-id="e1b07-123">Functions can also act like cmdlets.</span></span> <span data-ttu-id="e1b07-124">Du kan skapa en funktion som fungerar precis som en cmdlet utan att använda `C#` programmering.</span><span class="sxs-lookup"><span data-stu-id="e1b07-124">You can create a function that works just like a cmdlet without using `C#` programming.</span></span> <span data-ttu-id="e1b07-125">Mer information finns i [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-125">For more information, see [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="e1b07-126">Syntax</span><span class="sxs-lookup"><span data-stu-id="e1b07-126">Syntax</span></span>

<span data-ttu-id="e1b07-127">Följande är syntaxen för en funktion:</span><span class="sxs-lookup"><span data-stu-id="e1b07-127">The following is the syntax for a function:</span></span>

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

<span data-ttu-id="e1b07-128">En funktion innehåller följande objekt:</span><span class="sxs-lookup"><span data-stu-id="e1b07-128">A function includes the following items:</span></span>

- <span data-ttu-id="e1b07-129">Ett `Function` nyckelord</span><span class="sxs-lookup"><span data-stu-id="e1b07-129">A `Function` keyword</span></span>
- <span data-ttu-id="e1b07-130">Ett omfång (valfritt)</span><span class="sxs-lookup"><span data-stu-id="e1b07-130">A scope (optional)</span></span>
- <span data-ttu-id="e1b07-131">Ett namn som du väljer</span><span class="sxs-lookup"><span data-stu-id="e1b07-131">A name that you select</span></span>
- <span data-ttu-id="e1b07-132">Valfritt antal namngivna parametrar (valfritt)</span><span class="sxs-lookup"><span data-stu-id="e1b07-132">Any number of named parameters (optional)</span></span>
- <span data-ttu-id="e1b07-133">Ett eller flera PowerShell-kommandon inom klammerparentes `{}`</span><span class="sxs-lookup"><span data-stu-id="e1b07-133">One or more PowerShell commands enclosed in braces `{}`</span></span>

<span data-ttu-id="e1b07-134">Mer information om `Dynamicparam` nyckelordet och dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-134">For more information about the `Dynamicparam` keyword and dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

## <a name="simple-functions"></a><span data-ttu-id="e1b07-135">Enkla funktioner</span><span class="sxs-lookup"><span data-stu-id="e1b07-135">Simple Functions</span></span>

<span data-ttu-id="e1b07-136">Funktionerna behöver inte vara komplicerade för att vara användbara.</span><span class="sxs-lookup"><span data-stu-id="e1b07-136">Functions do not have to be complicated to be useful.</span></span> <span data-ttu-id="e1b07-137">De enklaste funktionerna har följande format:</span><span class="sxs-lookup"><span data-stu-id="e1b07-137">The simplest functions have the following format:</span></span>

```
function <function-name> {statements}
```

<span data-ttu-id="e1b07-138">Följande funktion startar till exempel PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="e1b07-138">For example, the following function starts PowerShell with the Run as Administrator option.</span></span>

```powershell
function Start-PSAdmin {Start-Process PowerShell -Verb RunAs}
```

<span data-ttu-id="e1b07-139">Om du vill använda funktionen skriver du: `Start-PSAdmin`</span><span class="sxs-lookup"><span data-stu-id="e1b07-139">To use the function, type: `Start-PSAdmin`</span></span>

<span data-ttu-id="e1b07-140">Om du vill lägga till instruktioner till funktionen skriver du varje instruktion på en separat rad eller använder ett semikolon `;` för att avgränsa satserna.</span><span class="sxs-lookup"><span data-stu-id="e1b07-140">To add statements to the function, type each statement on a separate line, or use a semi-colon `;` to separate the statements.</span></span>

<span data-ttu-id="e1b07-141">Följande funktion hittar till exempel alla `.jpg` filer i den aktuella användarens kataloger som har ändrats efter start datumet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-141">For example, the following function finds all `.jpg` files in the current user's directories that were changed after the start date.</span></span>

```powershell
function Get-NewPix
{
  $start = Get-Date -Month 1 -Day 1 -Year 2010
  $allpix = Get-ChildItem -Path $env:UserProfile\*.jpg -Recurse
  $allpix | Where-Object {$_.LastWriteTime -gt $Start}
}
```

<span data-ttu-id="e1b07-142">Du kan skapa en verktygs låda med användbara små funktioner.</span><span class="sxs-lookup"><span data-stu-id="e1b07-142">You can create a toolbox of useful small functions.</span></span> <span data-ttu-id="e1b07-143">Lägg till dessa funktioner i din PowerShell-profil, enligt beskrivningen i [about_Profiles](about_Profiles.md) och senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-143">Add these functions to your PowerShell profile, as described in [about_Profiles](about_Profiles.md) and later in this topic.</span></span>

## <a name="function-names"></a><span data-ttu-id="e1b07-144">Funktions namn</span><span class="sxs-lookup"><span data-stu-id="e1b07-144">Function Names</span></span>

<span data-ttu-id="e1b07-145">Du kan tilldela ett namn till en funktion, men funktioner som du delar med andra bör följa de namngivnings regler som har upprättats för alla PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="e1b07-145">You can assign any name to a function, but functions that you share with others should follow the naming rules that have been established for all PowerShell commands.</span></span>

<span data-ttu-id="e1b07-146">Funktions namn ska bestå av ett verb-Substantiv-par där verbet identifierar den åtgärd som funktionen utför och Substantiv identifierar objektet som cmdleten utför åtgärden på.</span><span class="sxs-lookup"><span data-stu-id="e1b07-146">Functions names should consist of a verb-noun pair in which the verb identifies the action that the function performs and the noun identifies the item on which the cmdlet performs its action.</span></span>

<span data-ttu-id="e1b07-147">Funktioner bör använda standardverb som har godkänts för alla PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="e1b07-147">Functions should use the standard verbs that have been approved for all PowerShell commands.</span></span> <span data-ttu-id="e1b07-148">De här verben hjälper oss att hålla våra kommando namn enkla, konsekventa och enkla för användare att förstå.</span><span class="sxs-lookup"><span data-stu-id="e1b07-148">These verbs help us to keep our command names simple, consistent, and easy for users to understand.</span></span>

<span data-ttu-id="e1b07-149">Mer information om standard PowerShell-verben finns i [godkända verb](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="e1b07-149">For more information about the standard PowerShell verbs, see [Approved Verbs](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands) in the Microsoft Docs.</span></span>

## <a name="functions-with-parameters"></a><span data-ttu-id="e1b07-150">Funktioner med parametrar</span><span class="sxs-lookup"><span data-stu-id="e1b07-150">Functions with Parameters</span></span>

<span data-ttu-id="e1b07-151">Du kan använda parametrar med Functions, inklusive namngivna parametrar, positions parametrar, växel parametrar och dynamiska parametrar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-151">You can use parameters with functions, including named parameters, positional parameters, switch parameters, and dynamic parameters.</span></span> <span data-ttu-id="e1b07-152">Mer information om dynamiska parametrar i functions finns [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-152">For more information about dynamic parameters in functions, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="named-parameters"></a><span data-ttu-id="e1b07-153">Namngivna parametrar</span><span class="sxs-lookup"><span data-stu-id="e1b07-153">Named Parameters</span></span>

<span data-ttu-id="e1b07-154">Du kan definiera valfritt antal namngivna parametrar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-154">You can define any number of named parameters.</span></span> <span data-ttu-id="e1b07-155">Du kan inkludera ett standardvärde för namngivna parametrar, enligt beskrivningen längre fram i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-155">You can include a default value for named parameters, as described later in this topic.</span></span>

<span data-ttu-id="e1b07-156">Du kan definiera parametrar inom klammerparenteserna med hjälp av `Param` nyckelordet, som du ser i följande exempel-syntax:</span><span class="sxs-lookup"><span data-stu-id="e1b07-156">You can define parameters inside the braces using the `Param` keyword, as shown in the following sample syntax:</span></span>

```
function <name> {
  param ([type]$parameter1[,[type]$parameter2])
  <statement list>
}
```

<span data-ttu-id="e1b07-157">Du kan också definiera parametrar utanför klamrarna utan `Param` nyckelord, som du ser i följande exempel-syntax:</span><span class="sxs-lookup"><span data-stu-id="e1b07-157">You can also define parameters outside the braces without the `Param` keyword, as shown in the following sample syntax:</span></span>

```powershell
function <name> [([type]$parameter1[,[type]$parameter2])] {
  <statement list>
}
```

<span data-ttu-id="e1b07-158">Nedan visas ett exempel på den här alternativa syntaxen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-158">Below is an example of this alternative syntax.</span></span>

```powershell
Function Add-Numbers($one, $two) {
    $one + $two
}
```

<span data-ttu-id="e1b07-159">Den första metoden är att föredra, men det finns ingen skillnad mellan dessa två metoder.</span><span class="sxs-lookup"><span data-stu-id="e1b07-159">While the first method is preferred, there is no difference between these two methods.</span></span>

<span data-ttu-id="e1b07-160">När du kör funktionen tilldelas värdet som du anger för en parameter en variabel som innehåller parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-160">When you run the function, the value you supply for a parameter is assigned to a variable that contains the parameter name.</span></span> <span data-ttu-id="e1b07-161">Värdet för variabeln kan användas i-funktionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-161">The value of that variable can be used in the function.</span></span>

<span data-ttu-id="e1b07-162">Följande exempel är en funktion som kallas `Get-SmallFiles` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-162">The following example is a function called `Get-SmallFiles`.</span></span> <span data-ttu-id="e1b07-163">Den här funktionen har en `$Size` parameter.</span><span class="sxs-lookup"><span data-stu-id="e1b07-163">This function has a `$Size` parameter.</span></span> <span data-ttu-id="e1b07-164">Funktionen visar alla filer som är mindre än värdet för `$Size` parametern och undantar kataloger:</span><span class="sxs-lookup"><span data-stu-id="e1b07-164">The function displays all the files that are smaller than the value of the `$Size` parameter, and it excludes directories:</span></span>

```powershell
function Get-SmallFiles {
  Param($Size)
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="e1b07-165">I funktionen kan du använda `$Size` variabeln, som är det namn som definierats för parametern.</span><span class="sxs-lookup"><span data-stu-id="e1b07-165">In the function, you can use the `$Size` variable, which is the name defined for the parameter.</span></span>

<span data-ttu-id="e1b07-166">Om du vill använda den här funktionen skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="e1b07-166">To use this function, type the following command:</span></span>

```powershell
Get-SmallFiles -Size 50
```

<span data-ttu-id="e1b07-167">Du kan också ange ett värde för en namngiven parameter utan parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-167">You can also enter a value for a named parameter without the parameter name.</span></span>
<span data-ttu-id="e1b07-168">Till exempel ger följande kommando samma resultat som ett kommando som namnger **storleks** parametern:</span><span class="sxs-lookup"><span data-stu-id="e1b07-168">For example, the following command gives the same result as a command that names the **Size** parameter:</span></span>

```powershell
Get-SmallFiles 50
```

<span data-ttu-id="e1b07-169">Om du vill definiera ett standardvärde för en parameter skriver du ett likhets tecken och värdet efter parameter namnet, som du ser i följande variant av `Get-SmallFiles` exemplet:</span><span class="sxs-lookup"><span data-stu-id="e1b07-169">To define a default value for a parameter, type an equal sign and the value after the parameter name, as shown in the following variation of the `Get-SmallFiles` example:</span></span>

```powershell
function Get-SmallFiles ($Size = 100) {
  Get-ChildItem $HOME | Where-Object {
    $_.Length -lt $Size -and !$_.PSIsContainer
  }
}
```

<span data-ttu-id="e1b07-170">Om du skriver `Get-SmallFiles` utan ett värde tilldelar funktionen 100 till `$size` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-170">If you type `Get-SmallFiles` without a value, the function assigns 100 to `$size`.</span></span> <span data-ttu-id="e1b07-171">Om du anger ett värde använder funktionen det värdet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-171">If you provide a value, the function uses that value.</span></span>

<span data-ttu-id="e1b07-172">Alternativt kan du ange en kort hjälp sträng som beskriver standardvärdet för din parameter genom att lägga till attributet **PSDefaultValue** i beskrivningen av parametern och ange egenskapen **Help** för **PSDefaultValue**.</span><span class="sxs-lookup"><span data-stu-id="e1b07-172">Optionally, you can provide a brief help string that describes the default value of your parameter, by adding the **PSDefaultValue** attribute to the description of your parameter, and specifying the **Help** property of **PSDefaultValue**.</span></span> <span data-ttu-id="e1b07-173">Om du vill ange en hjälp sträng som beskriver standardvärdet (100) för **storleks** parametern i `Get-SmallFiles` funktionen, lägger du till attributet **PSDefaultValue** som visas i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="e1b07-173">To provide a help string that describes the default value (100) of the **Size** parameter in the `Get-SmallFiles` function, add the **PSDefaultValue** attribute as shown in the following example.</span></span>

```powershell
function Get-SmallFiles {
  param (
      [PSDefaultValue(Help = '100')]
      $Size = 100
  )
}
```

<span data-ttu-id="e1b07-174">Mer information om klassen **PSDefaultValue** finns i [PSDefaultValue-attribut medlemmar](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span><span class="sxs-lookup"><span data-stu-id="e1b07-174">For more information about the **PSDefaultValue** attribute class, see [PSDefaultValue Attribute Members](/dotnet/api/system.management.automation.psdefaultvalueattribute).</span></span>

### <a name="positional-parameters"></a><span data-ttu-id="e1b07-175">Positions parametrar</span><span class="sxs-lookup"><span data-stu-id="e1b07-175">Positional Parameters</span></span>

<span data-ttu-id="e1b07-176">En positions parameter är en parameter utan parameter namn.</span><span class="sxs-lookup"><span data-stu-id="e1b07-176">A positional parameter is a parameter without a parameter name.</span></span> <span data-ttu-id="e1b07-177">PowerShell använder parameter värde ordningen för att koppla varje parameter värde till en parameter i funktionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-177">PowerShell uses the parameter value order to associate each parameter value with a parameter in the function.</span></span>

<span data-ttu-id="e1b07-178">När du använder positions parametrar, anger du ett eller flera värden efter funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-178">When you use positional parameters, type one or more values after the function name.</span></span> <span data-ttu-id="e1b07-179">Positions parameter värden tilldelas till `$args` mat ris variabeln.</span><span class="sxs-lookup"><span data-stu-id="e1b07-179">Positional parameter values are assigned to the `$args` array variable.</span></span>
<span data-ttu-id="e1b07-180">Värdet som följer funktions namnet tilldelas till den första positionen i `$args` matrisen `$args[0]` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-180">The value that follows the function name is assigned to the first position in the `$args` array, `$args[0]`.</span></span>

<span data-ttu-id="e1b07-181">Följande `Get-Extension` funktion lägger till `.txt` fil namns tillägget i ett fil namn som du anger:</span><span class="sxs-lookup"><span data-stu-id="e1b07-181">The following `Get-Extension` function adds the `.txt` file name extension to a file name that you supply:</span></span>

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

### <a name="switch-parameters"></a><span data-ttu-id="e1b07-182">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="e1b07-182">Switch Parameters</span></span>

<span data-ttu-id="e1b07-183">En växel är en parameter som inte kräver något värde.</span><span class="sxs-lookup"><span data-stu-id="e1b07-183">A switch is a parameter that does not require a value.</span></span> <span data-ttu-id="e1b07-184">I stället skriver du funktions namnet följt av namnet på växel parametern.</span><span class="sxs-lookup"><span data-stu-id="e1b07-184">Instead, you type the function name followed by the name of the switch parameter.</span></span>

<span data-ttu-id="e1b07-185">Definiera en växlings parameter genom att ange typen `[switch]` före parameter namnet, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e1b07-185">To define a switch parameter, specify the type `[switch]` before the parameter name, as shown in the following example:</span></span>

```powershell
function Switch-Item {
  param ([switch]$on)
  if ($on) { "Switch on" }
  else { "Switch off" }
}
```

<span data-ttu-id="e1b07-186">När du skriver `On` parametern switch efter funktions namnet visar funktionen "växla på".</span><span class="sxs-lookup"><span data-stu-id="e1b07-186">When you type the `On` switch parameter after the function name, the function displays "Switch on".</span></span> <span data-ttu-id="e1b07-187">Utan parametern switch visas "Inaktivera".</span><span class="sxs-lookup"><span data-stu-id="e1b07-187">Without the switch parameter, it displays "Switch off".</span></span>

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

<span data-ttu-id="e1b07-188">Du kan också tilldela ett **booleskt** värde till en växel när du kör funktionen, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e1b07-188">You can also assign a **Boolean** value to a switch when you run the function, as shown in the following example:</span></span>

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

## <a name="using-splatting-to-represent-command-parameters"></a><span data-ttu-id="e1b07-189">Använda Ihopbuntning för att representera kommando parametrar</span><span class="sxs-lookup"><span data-stu-id="e1b07-189">Using Splatting to Represent Command Parameters</span></span>

<span data-ttu-id="e1b07-190">Du kan använda ihopbuntning för att representera parametrarna för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="e1b07-190">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="e1b07-191">Den här funktionen introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e1b07-191">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="e1b07-192">Använd den här metoden i functions som anropar kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-192">Use this technique in functions that call commands in the session.</span></span> <span data-ttu-id="e1b07-193">Du behöver inte deklarera eller räkna upp kommando parametrarna eller ändra funktionen när kommando parametrar ändras.</span><span class="sxs-lookup"><span data-stu-id="e1b07-193">You do not need to declare or enumerate the command parameters, or change the function when command parameters change.</span></span>

<span data-ttu-id="e1b07-194">Följande exempel funktion anropar `Get-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e1b07-194">The following sample function calls the `Get-Command` cmdlet.</span></span> <span data-ttu-id="e1b07-195">Kommandot används `@Args` för att representera parametrarna för `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-195">The command uses `@Args` to represent the parameters of `Get-Command`.</span></span>

```powershell
function Get-MyCommand { Get-Command @Args }
```

<span data-ttu-id="e1b07-196">Du kan använda alla parametrar `Get-Command` när du anropar `Get-MyCommand` funktionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-196">You can use all of the parameters of `Get-Command` when you call the `Get-MyCommand` function.</span></span> <span data-ttu-id="e1b07-197">Parametrar och parameter värden skickas till kommandot med hjälp av `@Args` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-197">The parameters and parameter values are passed to the command using `@Args`.</span></span>

```powershell
Get-MyCommand -Name Get-ChildItem
```

```Output
CommandType     Name                ModuleName
-----------     ----                ----------
Cmdlet          Get-ChildItem       Microsoft.PowerShell.Management
```

<span data-ttu-id="e1b07-198">`@Args`Funktionen använder den `$Args` automatiska parametern som representerar odeklarerade cmdlet-parametrar och värden från återstående argument.</span><span class="sxs-lookup"><span data-stu-id="e1b07-198">The `@Args` feature uses the `$Args` automatic parameter, which represents undeclared cmdlet parameters and values from remaining arguments.</span></span>

<span data-ttu-id="e1b07-199">Mer information om ihopbuntning finns i [about_Splatting](about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-199">For more information about splatting, see [about_Splatting](about_Splatting.md).</span></span>

## <a name="piping-objects-to-functions"></a><span data-ttu-id="e1b07-200">Rör objekt till Functions</span><span class="sxs-lookup"><span data-stu-id="e1b07-200">Piping Objects to Functions</span></span>

<span data-ttu-id="e1b07-201">Alla funktioner kan ta inmatade från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-201">Any function can take input from the pipeline.</span></span> <span data-ttu-id="e1b07-202">Du kan styra hur en funktion bearbetar inmatade värden från pipelinen med hjälp av `Begin` , `Process` och `End` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-202">You can control how a function processes input from the pipeline using `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="e1b07-203">Följande exempel-syntax visar de tre nyckelorden:</span><span class="sxs-lookup"><span data-stu-id="e1b07-203">The following sample syntax shows the three keywords:</span></span>

```
function <name> {
  begin {<statement list>}
  process {<statement list>}
  end {<statement list>}
}
```

<span data-ttu-id="e1b07-204">`Begin`Instruktions listan körs bara en gång, i början av funktionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-204">The `Begin` statement list runs one time only, at the beginning of the function.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1b07-205">Om din funktion definierar ett `Begin` , `Process` eller ett `End` block, måste all kod finnas inuti dessa block.</span><span class="sxs-lookup"><span data-stu-id="e1b07-205">If your function defines a `Begin`, `Process` or `End` block, all of your code must reside inside those blocks.</span></span> <span data-ttu-id="e1b07-206">Ingen kod kommer att identifieras utanför blocken om *något* av blocken har definierats.</span><span class="sxs-lookup"><span data-stu-id="e1b07-206">No code will be recognized outside the blocks if *any* of the blocks are defined.</span></span>

<span data-ttu-id="e1b07-207">`Process`Instruktions listan körs en gången för varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-207">The `Process` statement list runs one time for each object in the pipeline.</span></span>
<span data-ttu-id="e1b07-208">Även om `Process` blocket körs, tilldelas varje pipeline-objekt den `$_` automatiska variabeln, ett pipeline-objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="e1b07-208">While the `Process` block is running, each pipeline object is assigned to the `$_` automatic variable, one pipeline object at a time.</span></span>

<span data-ttu-id="e1b07-209">När funktionen tar emot alla objekt i pipelinen `End` körs instruktions listan en enda gången.</span><span class="sxs-lookup"><span data-stu-id="e1b07-209">After the function receives all the objects in the pipeline, the `End` statement list runs one time.</span></span> <span data-ttu-id="e1b07-210">Om nej `Begin` , `Process` eller `End` nyckelord används, behandlas alla instruktioner som en `End` instruktions lista.</span><span class="sxs-lookup"><span data-stu-id="e1b07-210">If no `Begin`, `Process`, or `End` keywords are used, all the statements are treated like an `End` statement list.</span></span>

<span data-ttu-id="e1b07-211">Följande funktion använder `Process` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-211">The following function uses the `Process` keyword.</span></span> <span data-ttu-id="e1b07-212">Funktionen visar exempel från pipelinen:</span><span class="sxs-lookup"><span data-stu-id="e1b07-212">The function displays examples from the pipeline:</span></span>

```powershell
function Get-Pipeline
{
  process {"The value is: $_"}
}
```

<span data-ttu-id="e1b07-213">Visa den här funktionen genom att ange en lista med siffror avgränsade med kommatecken, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e1b07-213">To demonstrate this function, enter an list of numbers separated by commas, as shown in the following example:</span></span>

```powershell
1,2,4 | Get-Pipeline
```

```Output
The value is: 1
The value is: 2
The value is: 4
```

<span data-ttu-id="e1b07-214">När du använder en funktion i en pipeline, tilldelas de objekt som skickas till funktionen den `$input` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="e1b07-214">When you use a function in a pipeline, the objects piped to the function are assigned to the `$input` automatic variable.</span></span> <span data-ttu-id="e1b07-215">Funktionen kör instruktioner med `Begin` nyckelordet innan några objekt kommer från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-215">The function runs statements with the `Begin` keyword before any objects come from the pipeline.</span></span> <span data-ttu-id="e1b07-216">Funktionen kör instruktioner med `End` nyckelordet när alla objekt har tagits emot från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-216">The function runs statements with the `End` keyword after all the objects have been received from the pipeline.</span></span>

<span data-ttu-id="e1b07-217">I följande exempel visas den `$input` automatiska variabeln med `Begin` och `End` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="e1b07-217">The following example shows the `$input` automatic variable with `Begin` and `End` keywords.</span></span>

```powershell
function Get-PipelineBeginEnd
{
  begin {"Begin: The input is $input"}
  end {"End:   The input is $input" }
}
```

<span data-ttu-id="e1b07-218">Om den här funktionen körs med hjälp av pipelinen visas följande resultat:</span><span class="sxs-lookup"><span data-stu-id="e1b07-218">If this function is run by using the pipeline, it displays the following results:</span></span>

```powershell
1,2,4 | Get-PipelineBeginEnd
```

```Output
Begin: The input is
End:   The input is 1 2 4
```

<span data-ttu-id="e1b07-219">När `Begin` instruktionen körs har funktionen inte inmatade värden från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-219">When the `Begin` statement runs, the function does not have the input from the pipeline.</span></span> <span data-ttu-id="e1b07-220">`End`Instruktionen körs när funktionen har värden.</span><span class="sxs-lookup"><span data-stu-id="e1b07-220">The `End` statement runs after the function has the values.</span></span>

<span data-ttu-id="e1b07-221">Om funktionen har ett `Process` nyckelord tas varje objekt i som `$input` tas bort från `$input` och tilldelas `$_` .</span><span class="sxs-lookup"><span data-stu-id="e1b07-221">If the function has a `Process` keyword, each object in `$input` is removed from `$input` and assigned to `$_`.</span></span> <span data-ttu-id="e1b07-222">I följande exempel finns en `Process` instruktions lista:</span><span class="sxs-lookup"><span data-stu-id="e1b07-222">The following example has a `Process` statement list:</span></span>

```powershell
function Get-PipelineInput
{
  process {"Processing:  $_ " }
  end {"End:   The input is: $input" }
}
```

<span data-ttu-id="e1b07-223">I det här exemplet skickas varje objekt som är skickas till funktionen till `Process` instruktions listan.</span><span class="sxs-lookup"><span data-stu-id="e1b07-223">In this example, each object that is piped to the function is sent to the `Process` statement list.</span></span> <span data-ttu-id="e1b07-224">De `Process` instruktioner som körs för varje objekt, ett objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="e1b07-224">The `Process` statements run on each object, one object at a time.</span></span> <span data-ttu-id="e1b07-225">Den `$input` automatiska variabeln är tom när funktionen når `End` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-225">The `$input` automatic variable is empty when the function reaches the `End` keyword.</span></span>

```powershell
1,2,4 | Get-PipelineInput
```

```Output
Processing:  1
Processing:  2
Processing:  4
End:   The input is:
```

<span data-ttu-id="e1b07-226">Mer information finns i [använda uppräknare](about_Automatic_Variables.md#using-enumerators)</span><span class="sxs-lookup"><span data-stu-id="e1b07-226">For more information, see [Using Enumerators](about_Automatic_Variables.md#using-enumerators)</span></span>

## <a name="filters"></a><span data-ttu-id="e1b07-227">Filter</span><span class="sxs-lookup"><span data-stu-id="e1b07-227">Filters</span></span>

<span data-ttu-id="e1b07-228">Ett filter är en typ av funktion som körs på varje objekt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-228">A filter is a type of function that runs on each object in the pipeline.</span></span> <span data-ttu-id="e1b07-229">Ett filter liknar en funktion med alla dess uttryck i ett `Process` block.</span><span class="sxs-lookup"><span data-stu-id="e1b07-229">A filter resembles a function with all its statements in a `Process` block.</span></span>

<span data-ttu-id="e1b07-230">Syntaxen för ett filter är följande:</span><span class="sxs-lookup"><span data-stu-id="e1b07-230">The syntax of a filter is as follows:</span></span>

```
filter [<scope:>]<name> {<statement list>}
```

<span data-ttu-id="e1b07-231">Följande filter använder logg poster från pipelinen och visar sedan antingen hela posten eller bara meddelande delen av posten:</span><span class="sxs-lookup"><span data-stu-id="e1b07-231">The following filter takes log entries from the pipeline and then displays either the whole entry or only the message portion of the entry:</span></span>

```powershell
filter Get-ErrorLog ([switch]$message)
{
  if ($message) { Out-Host -InputObject $_.Message }
  else { $_ }
}
```

## <a name="function-scope"></a><span data-ttu-id="e1b07-232">Funktions omfång</span><span class="sxs-lookup"><span data-stu-id="e1b07-232">Function Scope</span></span>

<span data-ttu-id="e1b07-233">Det finns en funktion i omfånget som den skapades i.</span><span class="sxs-lookup"><span data-stu-id="e1b07-233">A function exists in the scope in which it was created.</span></span>

<span data-ttu-id="e1b07-234">Om en funktion är en del av ett skript är funktionen tillgänglig för instruktioner i skriptet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-234">If a function is part of a script, the function is available to statements within that script.</span></span> <span data-ttu-id="e1b07-235">Som standard är en funktion i ett skript inte tillgänglig i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="e1b07-235">By default, a function in a script is not available at the command prompt.</span></span>

<span data-ttu-id="e1b07-236">Du kan ange omfattningen för en funktion.</span><span class="sxs-lookup"><span data-stu-id="e1b07-236">You can specify the scope of a function.</span></span> <span data-ttu-id="e1b07-237">Funktionen läggs till exempel till i det globala omfånget i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="e1b07-237">For example, the function is added to the global scope in the following example:</span></span>

```powershell
function global:Get-DependentSvs {
  Get-Service | Where-Object {$_.DependentServices}
}
```

<span data-ttu-id="e1b07-238">När en funktion finns i det globala omfånget kan du använda funktionen i skript, i functions och på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e1b07-238">When a function is in the global scope, you can use the function in scripts, in functions, and at the command line.</span></span>

<span data-ttu-id="e1b07-239">Functions skapar vanligt vis ett definitions område.</span><span class="sxs-lookup"><span data-stu-id="e1b07-239">Functions normally create a scope.</span></span> <span data-ttu-id="e1b07-240">De objekt som skapas i en funktion, till exempel variabler, finns bara i funktions omfånget.</span><span class="sxs-lookup"><span data-stu-id="e1b07-240">The items created in a function, such as variables, exist only in the function scope.</span></span>

<span data-ttu-id="e1b07-241">Mer information om omfång i PowerShell finns [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-241">For more information about scope in PowerShell, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="finding-and-managing-functions-using-the-function-drive"></a><span data-ttu-id="e1b07-242">Hitta och hantera funktioner med funktionen: enhet</span><span class="sxs-lookup"><span data-stu-id="e1b07-242">Finding and Managing Functions Using the Function: Drive</span></span>

<span data-ttu-id="e1b07-243">Alla funktioner och filter i PowerShell lagras automatiskt i `Function:` enheten.</span><span class="sxs-lookup"><span data-stu-id="e1b07-243">All the functions and filters in PowerShell are automatically stored in the `Function:` drive.</span></span> <span data-ttu-id="e1b07-244">Enheten exponeras av PowerShell- **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="e1b07-244">This drive is exposed by the PowerShell **Function** provider.</span></span>

<span data-ttu-id="e1b07-245">När du refererar till `Function:` enheten skriver du ett kolon efter- **funktionen**, precis som du skulle göra när du refererar `C` till `D` en dators eller datorns enhet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-245">When referring to the `Function:` drive, type a colon after **Function**, just as you would do when referencing the `C` or `D` drive of a computer.</span></span>

<span data-ttu-id="e1b07-246">Följande kommando visar alla funktioner i den aktuella sessionen av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e1b07-246">The following command displays all the functions in the current session of PowerShell:</span></span>

```powershell
Get-ChildItem function:
```

<span data-ttu-id="e1b07-247">Kommandona i funktionen lagras som ett skript block i funktionens definitions egenskap.</span><span class="sxs-lookup"><span data-stu-id="e1b07-247">The commands in the function are stored as a script block in the definition property of the function.</span></span> <span data-ttu-id="e1b07-248">Om du till exempel vill visa kommandona i Hjälp funktionen som medföljer PowerShell, skriver du:</span><span class="sxs-lookup"><span data-stu-id="e1b07-248">For example, to display the commands in the Help function that comes with PowerShell, type:</span></span>

```powershell
(Get-ChildItem function:help).Definition
```

<span data-ttu-id="e1b07-249">Du kan också använda följande syntax.</span><span class="sxs-lookup"><span data-stu-id="e1b07-249">You can also use the following syntax.</span></span>

```powershell
$function:help
```

<span data-ttu-id="e1b07-250">Mer information om `Function:` enheten finns i hjälp avsnittet för **funktions** leverantören.</span><span class="sxs-lookup"><span data-stu-id="e1b07-250">For more information about the `Function:` drive, see the help topic for the **Function** provider.</span></span> <span data-ttu-id="e1b07-251">Skriv `Get-Help Function`.</span><span class="sxs-lookup"><span data-stu-id="e1b07-251">Type `Get-Help Function`.</span></span>

## <a name="reusing-functions-in-new-sessions"></a><span data-ttu-id="e1b07-252">Återanvända funktioner i nya sessioner</span><span class="sxs-lookup"><span data-stu-id="e1b07-252">Reusing Functions in New Sessions</span></span>

<span data-ttu-id="e1b07-253">När du skriver en funktion i PowerShell-Kommandotolken blir funktionen en del av den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-253">When you type a function at the PowerShell command prompt, the function becomes part of the current session.</span></span> <span data-ttu-id="e1b07-254">Den är tillgänglig tills sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="e1b07-254">It is available until the session ends.</span></span>

<span data-ttu-id="e1b07-255">Om du vill använda din funktion i alla PowerShell-sessioner lägger du till funktionen i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="e1b07-255">To use your function in all PowerShell sessions, add the function to your PowerShell profile.</span></span> <span data-ttu-id="e1b07-256">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-256">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="e1b07-257">Du kan också spara din funktion i en PowerShell-skriptfil.</span><span class="sxs-lookup"><span data-stu-id="e1b07-257">You can also save your function in a PowerShell script file.</span></span> <span data-ttu-id="e1b07-258">Skriv din funktion i en textfil och spara sedan filen med `.ps1` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="e1b07-258">Type your function in a text file, and then save the file with the `.ps1` file name extension.</span></span>

## <a name="writing-help-for-functions"></a><span data-ttu-id="e1b07-259">Skriver hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="e1b07-259">Writing Help for Functions</span></span>

<span data-ttu-id="e1b07-260">Cmdlet: en `Get-Help` får hjälp för funktioner, samt för cmdlets, providers och skript.</span><span class="sxs-lookup"><span data-stu-id="e1b07-260">The `Get-Help` cmdlet gets help for functions, as well as for cmdlets, providers, and scripts.</span></span> <span data-ttu-id="e1b07-261">Om du vill ha hjälp med en funktion skriver du `Get-Help` följt av funktions namnet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-261">To get help for a function, type `Get-Help` followed by the function name.</span></span>

<span data-ttu-id="e1b07-262">Om du till exempel vill få hjälp med `Get-MyDisks` funktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="e1b07-262">For example, to get help for the `Get-MyDisks` function, type:</span></span>

```powershell
Get-Help Get-MyDisks
```

<span data-ttu-id="e1b07-263">Du kan skriva hjälp för en funktion med någon av följande två metoder:</span><span class="sxs-lookup"><span data-stu-id="e1b07-263">You can write help for a function by using either of the two following methods:</span></span>

- <span data-ttu-id="e1b07-264">Comment-Based hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="e1b07-264">Comment-Based Help for Functions</span></span>

  <span data-ttu-id="e1b07-265">Skapa ett hjälp avsnitt genom att använda särskilda nyckelord i kommentarerna.</span><span class="sxs-lookup"><span data-stu-id="e1b07-265">Create a help topic by using special keywords in the comments.</span></span> <span data-ttu-id="e1b07-266">Om du vill skapa en kommenterad hjälp för en funktion måste kommentarerna placeras i början eller slutet av funktions texten eller på de rader som föregår nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="e1b07-266">To create comment-based help for a function, the comments must be placed at the beginning or end of the function body or on the lines preceding the function keyword.</span></span> <span data-ttu-id="e1b07-267">Mer information om kommenterad hjälp finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-267">For more information about comment-based help, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span>

- <span data-ttu-id="e1b07-268">XML-Based hjälp för functions</span><span class="sxs-lookup"><span data-stu-id="e1b07-268">XML-Based Help for Functions</span></span>

  <span data-ttu-id="e1b07-269">Skapa ett XML-baserat hjälp avsnitt, till exempel den typ som vanligt vis skapas för cmdletar.</span><span class="sxs-lookup"><span data-stu-id="e1b07-269">Create an XML-based help topic, such as the type that is typically created for cmdlets.</span></span> <span data-ttu-id="e1b07-270">XML-baserad hjälp krävs om du lokaliserar hjälp ämnen till flera språk.</span><span class="sxs-lookup"><span data-stu-id="e1b07-270">XML-based help is required if you are localizing help topics into multiple languages.</span></span>

  <span data-ttu-id="e1b07-271">Om du vill associera funktionen med det XML-baserade hjälp avsnittet använder du det `.ExternalHelp` kommenterings-baserade hjälp nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e1b07-271">To associate the function with the XML-based help topic, use the `.ExternalHelp` comment-based help keyword.</span></span> <span data-ttu-id="e1b07-272">Utan det här nyckelordet `Get-Help` kan du inte hitta funktions hjälp avsnittet och anropar till `Get-Help` för funktionen returnera endast den automatiskt genererade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="e1b07-272">Without this keyword, `Get-Help` cannot find the function help topic and calls to `Get-Help` for the function return only auto-generated help.</span></span>

  <span data-ttu-id="e1b07-273">Mer information om `ExternalHelp` nyckelordet finns [about_Comment_Based_Help](about_Comment_Based_Help.md).</span><span class="sxs-lookup"><span data-stu-id="e1b07-273">For more information about the `ExternalHelp` keyword, see [about_Comment_Based_Help](about_Comment_Based_Help.md).</span></span> <span data-ttu-id="e1b07-274">Mer information om XML-baserad hjälp finns i [så här skriver du cmdlet-hjälpen](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span><span class="sxs-lookup"><span data-stu-id="e1b07-274">For more information about XML-based help, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="see-also"></a><span data-ttu-id="e1b07-275">Se även</span><span class="sxs-lookup"><span data-stu-id="e1b07-275">See also</span></span>

[<span data-ttu-id="e1b07-276">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e1b07-276">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="e1b07-277">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="e1b07-277">about_Comment_Based_Help</span></span>](about_Comment_Based_Help.md)

[<span data-ttu-id="e1b07-278">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="e1b07-278">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="e1b07-279">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="e1b07-279">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="e1b07-280">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="e1b07-280">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="e1b07-281">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="e1b07-281">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="e1b07-282">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e1b07-282">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="e1b07-283">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="e1b07-283">about_Parameters</span></span>](about_Parameters.md)

[<span data-ttu-id="e1b07-284">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="e1b07-284">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="e1b07-285">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e1b07-285">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e1b07-286">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="e1b07-286">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="e1b07-287">about_Function_provider</span><span class="sxs-lookup"><span data-stu-id="e1b07-287">about_Function_provider</span></span>](about_Function_provider.md)