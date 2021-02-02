---
description: Definierar vad ett skript block är och förklarar hur du använder skript block i PowerShell-programmeringsspråket.
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: 1ba5e92bedc03a2d61d528715ab13c5d96eb3075
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710944"
---
# <a name="about-script-blocks"></a><span data-ttu-id="ffe50-103">Om skript block</span><span class="sxs-lookup"><span data-stu-id="ffe50-103">About Script Blocks</span></span>

## <a name="short-description"></a><span data-ttu-id="ffe50-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffe50-104">Short description</span></span>

<span data-ttu-id="ffe50-105">Definierar vad ett skript block är och förklarar hur du använder skript block i PowerShell-programmeringsspråket.</span><span class="sxs-lookup"><span data-stu-id="ffe50-105">Defines what a script block is and explains how to use script blocks in the PowerShell programming language.</span></span>

## <a name="long-description"></a><span data-ttu-id="ffe50-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="ffe50-106">Long description</span></span>

<span data-ttu-id="ffe50-107">I PowerShell-programmeringsspråket är ett skript block en samling med instruktioner eller uttryck som kan användas som en enda enhet.</span><span class="sxs-lookup"><span data-stu-id="ffe50-107">In the PowerShell programming language, a script block is a collection of statements or expressions that can be used as a single unit.</span></span>
<span data-ttu-id="ffe50-108">Ett skript block kan acceptera argument och returnerade värden.</span><span class="sxs-lookup"><span data-stu-id="ffe50-108">A script block can accept arguments and return values.</span></span>

<span data-ttu-id="ffe50-109">Ett skript block är syntaktiskt som en instruktions lista inom klammerparentes, som du ser i följande syntax:</span><span class="sxs-lookup"><span data-stu-id="ffe50-109">Syntactically, a script block is a statement list in braces, as shown in the following syntax:</span></span>

```
{<statement list>}
```

<span data-ttu-id="ffe50-110">Ett skript block returnerar utdata från alla kommandon i skript blocket, antingen som ett enskilt objekt eller som en matris.</span><span class="sxs-lookup"><span data-stu-id="ffe50-110">A script block returns the output of all the commands in the script block, either as a single object or as an array.</span></span>

<span data-ttu-id="ffe50-111">Du kan också ange ett retur värde med hjälp av `return` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="ffe50-111">You can also specify a return value using the `return` keyword.</span></span> <span data-ttu-id="ffe50-112">`return`Nyckelordet påverkar eller utelämnar inte andra utdata som returneras från skript blocket.</span><span class="sxs-lookup"><span data-stu-id="ffe50-112">The `return` keyword does not affect or suppress other output returned from your script block.</span></span> <span data-ttu-id="ffe50-113">`return`Nyckelordet avslutar dock skript blocket på raden.</span><span class="sxs-lookup"><span data-stu-id="ffe50-113">However, the `return` keyword exits the script block at that line.</span></span> <span data-ttu-id="ffe50-114">Mer information finns i [about_Return](about_Return.md).</span><span class="sxs-lookup"><span data-stu-id="ffe50-114">For more information, see [about_Return](about_Return.md).</span></span>

<span data-ttu-id="ffe50-115">Precis som funktioner kan ett skript block innehålla parametrar.</span><span class="sxs-lookup"><span data-stu-id="ffe50-115">Like functions, a script block can include parameters.</span></span> <span data-ttu-id="ffe50-116">Använd nyckelordet param för att tilldela namngivna parametrar, som du ser i följande syntax:</span><span class="sxs-lookup"><span data-stu-id="ffe50-116">Use the Param keyword to assign named parameters, as shown in the following syntax:</span></span>

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> <span data-ttu-id="ffe50-117">I ett-skript block kan du till skillnad från en funktion inte ange parametrar utanför klamrarna.</span><span class="sxs-lookup"><span data-stu-id="ffe50-117">In a script block, unlike a function, you cannot specify parameters outside the braces.</span></span>

<span data-ttu-id="ffe50-118">Precis som funktioner kan skript block innehålla `DynamicParam` `Begin` `Process` nyckelorden,, och `End` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-118">Like functions, script blocks can include the `DynamicParam`, `Begin`, `Process`, and `End` keywords.</span></span> <span data-ttu-id="ffe50-119">Mer information finns i [about_Functions](about_Functions.md) och [about_Functions_Advanced](about_Functions_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="ffe50-119">For more information, see [about_Functions](about_Functions.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

## <a name="using-script-blocks"></a><span data-ttu-id="ffe50-120">Använda skript block</span><span class="sxs-lookup"><span data-stu-id="ffe50-120">Using Script Blocks</span></span>

<span data-ttu-id="ffe50-121">Ett skript block är en instans av en Microsoft .NET Framework-typ `System.Management.Automation.ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-121">A script block is an instance of a Microsoft .NET Framework type `System.Management.Automation.ScriptBlock`.</span></span> <span data-ttu-id="ffe50-122">Kommandon kan innehålla parameter värden för skript block.</span><span class="sxs-lookup"><span data-stu-id="ffe50-122">Commands can have script block parameter values.</span></span> <span data-ttu-id="ffe50-123">Till exempel `Invoke-Command` har cmdleten en `ScriptBlock` parameter som tar ett skript block värde, som du ser i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="ffe50-123">For example, the `Invoke-Command` cmdlet has a `ScriptBlock` parameter that takes a script block value, as shown in this example:</span></span>

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

<span data-ttu-id="ffe50-124">`Invoke-Command` kan också köra skript block som har parameter block.</span><span class="sxs-lookup"><span data-stu-id="ffe50-124">`Invoke-Command` can also execute script blocks that have parameter blocks.</span></span>
<span data-ttu-id="ffe50-125">Parametrar tilldelas enligt position med parametern **argument List** .</span><span class="sxs-lookup"><span data-stu-id="ffe50-125">Parameters are assigned by position using the **ArgumentList** parameter.</span></span>

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

<span data-ttu-id="ffe50-126">Skript blocket i föregående exempel använder `param` nyckelordet för att skapa en parameter `$p1` och `$p2` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-126">The script block in the preceding example uses the `param` keyword to create a parameters `$p1` and `$p2`.</span></span> <span data-ttu-id="ffe50-127">Strängen "First" är kopplad till den första parametern ( `$p1` ) och "sekund" är kopplad till ( `$p2` ).</span><span class="sxs-lookup"><span data-stu-id="ffe50-127">The string "First" is bound to the first parameter (`$p1`) and "Second" is bound to (`$p2`).</span></span>

<span data-ttu-id="ffe50-128">Mer information om beteendet för **argument List** finns [about_Splatting](about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="ffe50-128">For more information about the behavior of **ArgumentList**, see [about_Splatting](about_Splatting.md#splatting-with-arrays).</span></span>

<span data-ttu-id="ffe50-129">Du kan använda variabler för att lagra och köra skript block.</span><span class="sxs-lookup"><span data-stu-id="ffe50-129">You can use variables to store and execute script blocks.</span></span> <span data-ttu-id="ffe50-130">Exemplet nedan lagrar ett skript block i en variabel och skickar det till `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-130">The example below stores a script block in a variable and passes it to `Invoke-Command`.</span></span>

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="ffe50-131">Anrops operatorn är ett annat sätt att köra skript block som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="ffe50-131">The call operator is another way to execute script blocks stored in a variable.</span></span>
<span data-ttu-id="ffe50-132">Till exempel `Invoke-Command` Kör anrops operatorn skript blocket i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="ffe50-132">Like `Invoke-Command`, the call operator executes the script block in a child scope.</span></span> <span data-ttu-id="ffe50-133">Anrops operatorn kan göra det enklare för dig att använda parametrar med skript block.</span><span class="sxs-lookup"><span data-stu-id="ffe50-133">The call operator can make it easier for you to use parameters with your script blocks.</span></span>

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

<span data-ttu-id="ffe50-134">Du kan lagra utdata från skript block i en variabel som använder tilldelning.</span><span class="sxs-lookup"><span data-stu-id="ffe50-134">You can store the output from your script blocks in a variable using assignment.</span></span>

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

<span data-ttu-id="ffe50-135">Mer information om samtals operatören finns [about_Operators](about_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="ffe50-135">For more information about the call operator, see [about_Operators](about_Operators.md).</span></span>

## <a name="using-delay-bind-script-blocks-with-parameters"></a><span data-ttu-id="ffe50-136">Använder skript block med fördröjnings bindning med parametrar</span><span class="sxs-lookup"><span data-stu-id="ffe50-136">Using delay-bind script blocks with parameters</span></span>

<span data-ttu-id="ffe50-137">En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken **Delay-bind** i parametern.</span><span class="sxs-lookup"><span data-stu-id="ffe50-137">A typed parameter that accepts pipeline input (`by Value`) or (`by PropertyName`) enables use of **delay-bind** script blocks on the parameter.</span></span>
<span data-ttu-id="ffe50-138">I skript blocket **Delay-bind** kan du referera till skickas i-objekt med hjälp av pipeline-variabeln `$_` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-138">Within the **delay-bind** script block, you can reference the piped in object using the pipeline variable `$_`.</span></span>

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

<span data-ttu-id="ffe50-139">I mer komplexa cmdletar kan fördröjning – binda skript block tillåta åter användning av en skickas i objekt för att fylla i andra parametrar.</span><span class="sxs-lookup"><span data-stu-id="ffe50-139">In more complex cmdlets, delay-bind script blocks allow the reuse of one piped in object to populate other parameters.</span></span>

<span data-ttu-id="ffe50-140">Anmärkningar om **Delay-bind** skript block som parametrar:</span><span class="sxs-lookup"><span data-stu-id="ffe50-140">Notes on **delay-bind** script blocks as parameters:</span></span>

- <span data-ttu-id="ffe50-141">Du måste uttryckligen ange eventuella parameter namn som du använder med **Delay-bind-** skript block.</span><span class="sxs-lookup"><span data-stu-id="ffe50-141">You must explicitly specify any parameter names you use with **delay-bind** script blocks.</span></span>
- <span data-ttu-id="ffe50-142">Parametern får inte vara avskriven och parameterns typ får inte vara `[scriptblock]` eller `[object]` .</span><span class="sxs-lookup"><span data-stu-id="ffe50-142">The parameter must not be untyped, and the parameter's type cannot be `[scriptblock]` or `[object]`.</span></span>
- <span data-ttu-id="ffe50-143">Du får ett fel meddelande om du använder ett **Delay-bind-** skript block utan att tillhandahålla pipeline-inflöden.</span><span class="sxs-lookup"><span data-stu-id="ffe50-143">You receive an error if you use a **delay-bind** script block without providing pipeline input.</span></span>

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a><span data-ttu-id="ffe50-144">Se även</span><span class="sxs-lookup"><span data-stu-id="ffe50-144">See Also</span></span>

[<span data-ttu-id="ffe50-145">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ffe50-145">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="ffe50-146">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="ffe50-146">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="ffe50-147">about_Operators</span><span class="sxs-lookup"><span data-stu-id="ffe50-147">about_Operators</span></span>](about_Operators.md)
