---
description: Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.
Locale: en-US
ms.date: 08/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: e028f43828afd69d645591ab20795689cb115e12
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710915"
---
# <a name="about-splatting"></a><span data-ttu-id="361ce-103">Om Ihopbuntning</span><span class="sxs-lookup"><span data-stu-id="361ce-103">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="361ce-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="361ce-104">Short description</span></span>

<span data-ttu-id="361ce-105">Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="361ce-105">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="361ce-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="361ce-106">Long description</span></span>

<span data-ttu-id="361ce-107">Ihopbuntning är en metod för att skicka en samling parameter värden till ett kommando som en enhet.</span><span class="sxs-lookup"><span data-stu-id="361ce-107">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="361ce-108">PowerShell kopplar varje värde i samlingen med en kommando parameter.</span><span class="sxs-lookup"><span data-stu-id="361ce-108">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="361ce-109">Splatted parameter värden lagras i namngivna ihopbuntning-variabler, som ser ut som standardvariabler, men börjar med en symbol ( `@` ) i stället för ett dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="361ce-109">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="361ce-110">Vid-symbolen visas PowerShell att du skickar en samling värden i stället för ett enda värde.</span><span class="sxs-lookup"><span data-stu-id="361ce-110">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="361ce-111">Ihopbuntning gör kommandona kortare och lättare att läsa.</span><span class="sxs-lookup"><span data-stu-id="361ce-111">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="361ce-112">Du kan återanvända ihopbuntning-värden i olika kommando anrop och använda ihopbuntning för att skicka parameter värden från den `$PSBoundParameters` automatiska variabeln till andra skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="361ce-112">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="361ce-113">Från och med Windows PowerShell 3,0 kan du också använda ihopbuntning för att representera alla parametrar för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="361ce-113">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="361ce-114">Syntax</span><span class="sxs-lookup"><span data-stu-id="361ce-114">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="361ce-115">Använd mat ris syntaxen för att ange parameter värden för positions parametrar, där parameter namn inte krävs.</span><span class="sxs-lookup"><span data-stu-id="361ce-115">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="361ce-116">Använd syntaxen för hash-tabellen för att ange parameter namn och värdepar.</span><span class="sxs-lookup"><span data-stu-id="361ce-116">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="361ce-117">Splatted-värdet kan finnas var som helst i parameter listan.</span><span class="sxs-lookup"><span data-stu-id="361ce-117">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="361ce-118">När ihopbuntning inte behöver använda en hash-tabell eller en matris för att skicka alla parametrar.</span><span class="sxs-lookup"><span data-stu-id="361ce-118">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="361ce-119">Du kan skicka vissa parametrar genom att använda ihopbuntning och skicka andra efter position eller parameter namn.</span><span class="sxs-lookup"><span data-stu-id="361ce-119">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="361ce-120">Du kan också splat flera objekt i ett enda kommando så att du inte skickar fler än ett värde för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="361ce-120">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

<span data-ttu-id="361ce-121">Från och med PowerShell 7,1 kan du åsidosätta en splatted-parameter genom att uttryckligen definiera en parameter i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="361ce-121">As of PowerShell 7.1, you can override a splatted parameter by explicitly defining a parameter in a command.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="361ce-122">Ihopbuntning med hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="361ce-122">Splatting with hash tables</span></span>

<span data-ttu-id="361ce-123">Använd en hash-tabell för att splat parameter namn och värdepar.</span><span class="sxs-lookup"><span data-stu-id="361ce-123">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="361ce-124">Du kan använda det här formatet för alla parameter typer, inklusive parametrar för position och växling.</span><span class="sxs-lookup"><span data-stu-id="361ce-124">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="361ce-125">Positions parametrar måste tilldelas med namn.</span><span class="sxs-lookup"><span data-stu-id="361ce-125">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="361ce-126">I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="361ce-126">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="361ce-127">I det första exemplet används det traditionella formatet där parameter namn ingår.</span><span class="sxs-lookup"><span data-stu-id="361ce-127">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="361ce-128">I det andra exemplet används hash-tabellens ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-128">The second example uses hash table splatting.</span></span> <span data-ttu-id="361ce-129">Det första kommandot skapar en hash-tabell med parameter namn och parameter-värdepar och lagrar den i `$HashArguments` variabeln.</span><span class="sxs-lookup"><span data-stu-id="361ce-129">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="361ce-130">Det andra kommandot använder `$HashArguments` variabeln i ett kommando med ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-130">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="361ce-131">Symbolen vid ( `@HashArguments` ) ersätter dollar tecknet ( `$HashArguments` ) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="361ce-131">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="361ce-132">Använd eller om du vill ange  ett värde för parametern whatIf `$True` switch `$False` .</span><span class="sxs-lookup"><span data-stu-id="361ce-132">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="361ce-133">I det första kommandot indikerar symbolen ( `@` ) en hash-tabell, inte ett splatted-värde.</span><span class="sxs-lookup"><span data-stu-id="361ce-133">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="361ce-134">Syntaxen för hash-tabeller i PowerShell är: `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="361ce-134">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="361ce-135">Ihopbuntning med matriser</span><span class="sxs-lookup"><span data-stu-id="361ce-135">Splatting with arrays</span></span>

<span data-ttu-id="361ce-136">Använd en matris för att splat värden för positions parametrar, vilket inte kräver parameter namn.</span><span class="sxs-lookup"><span data-stu-id="361ce-136">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="361ce-137">Värdena måste vara i positions nummer ordningen i matrisen.</span><span class="sxs-lookup"><span data-stu-id="361ce-137">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="361ce-138">I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="361ce-138">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="361ce-139">I det första exemplet används det traditionella formatet där parameter namn utelämnas.</span><span class="sxs-lookup"><span data-stu-id="361ce-139">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="361ce-140">Parameter värden visas i positions ordning i kommandot.</span><span class="sxs-lookup"><span data-stu-id="361ce-140">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="361ce-141">I det andra exemplet används matrisen ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-141">The second example uses array splatting.</span></span> <span data-ttu-id="361ce-142">Det första kommandot skapar en matris med parameter värden och lagrar den i `$ArrayArguments` variabeln.</span><span class="sxs-lookup"><span data-stu-id="361ce-142">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="361ce-143">Värdena är i positions ordning i matrisen.</span><span class="sxs-lookup"><span data-stu-id="361ce-143">The values are in position order in the array.</span></span> <span data-ttu-id="361ce-144">Det andra kommandot använder `$ArrayArguments` variabeln i ett kommando i ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-144">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="361ce-145">Symbolen vid ( `@ArrayArguments` ) ersätter dollar tecknet ( `$ArrayArguments` ) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="361ce-145">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="361ce-146">Använda parametern argument List</span><span class="sxs-lookup"><span data-stu-id="361ce-146">Using the ArgumentList parameter</span></span>

<span data-ttu-id="361ce-147">Flera cmdlets har en **argument List** -parameter som används för att skicka parameter värden till ett skript block som körs av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="361ce-147">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="361ce-148">Parametern **argument List** tar en matris med värden som skickas till-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="361ce-148">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="361ce-149">PowerShell använder i själva verket matris-ihopbuntning för att binda värdena till parametrarna i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="361ce-149">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="361ce-150">Om du behöver skicka en matris som ett enda objekt som är kopplat till en enskild parameter när du använder **argument List** måste du figursätta matrisen som det enda elementet i en annan matris.</span><span class="sxs-lookup"><span data-stu-id="361ce-150">When using **ArgumentList**, if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="361ce-151">I följande exempel finns ett skript block som använder en enda parameter som är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="361ce-151">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```
<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="361ce-152">I det här exemplet skickas endast det första objektet i `$array` till-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="361ce-152">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
```

<span data-ttu-id="361ce-153">I det här exemplet `$array` är omslutna i en matris så att hela matrisen skickas till-skript blocket som ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="361ce-153">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="361ce-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="361ce-154">Examples</span></span>

### <a name="example-1-reuse-splatted-parameters-in-different-commands"></a><span data-ttu-id="361ce-155">Exempel 1: Återanvänd splatted-parametrar i olika kommandon</span><span class="sxs-lookup"><span data-stu-id="361ce-155">Example 1: Reuse splatted parameters in different commands</span></span>

<span data-ttu-id="361ce-156">Det här exemplet visar hur du återanvänder splatted-värden i olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="361ce-156">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="361ce-157">Kommandona i det här exemplet använder `Write-Host` cmdleten för att skriva meddelanden till värd program konsolen.</span><span class="sxs-lookup"><span data-stu-id="361ce-157">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="361ce-158">Den använder ihopbuntning för att ange förgrunds-och bakgrunds färger.</span><span class="sxs-lookup"><span data-stu-id="361ce-158">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="361ce-159">Ändra värdet för variabeln om du vill ändra färgerna på alla kommandon `$Colors` .</span><span class="sxs-lookup"><span data-stu-id="361ce-159">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="361ce-160">Det första kommandot skapar en hash-tabell med parameter namn och värden och lagrar hash-tabellen i `$Colors` variabeln.</span><span class="sxs-lookup"><span data-stu-id="361ce-160">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="361ce-161">Det andra och tredje kommandot använder `$Colors` variabeln för ihopbuntning i ett `Write-Host` kommando.</span><span class="sxs-lookup"><span data-stu-id="361ce-161">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="361ce-162">Om du vill använda `$Colors variable` ersätter du dollar tecknet ( `$Colors` ) med en symbol ( `@Colors` ).</span><span class="sxs-lookup"><span data-stu-id="361ce-162">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

### <a name="example-2-forward-parameters-using-psboundparameters"></a><span data-ttu-id="361ce-163">Exempel 2: vidarebefordra parametrar med $PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="361ce-163">Example 2: Forward parameters using $PSBoundParameters</span></span>

<span data-ttu-id="361ce-164">Det här exemplet visar hur du vidarebefordrar sina parametrar till andra kommandon med hjälp av ihopbuntning och den `$PSBoundParameters` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="361ce-164">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="361ce-165">Den `$PSBoundParameters` automatiska variabeln är ett Dictionary-objekt (system. Collections. Generic. Dictionary) som innehåller alla parameter namn och värden som används när ett skript eller en funktion körs.</span><span class="sxs-lookup"><span data-stu-id="361ce-165">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="361ce-166">I följande exempel använder vi `$PSBoundParameters` variabeln för att vidarebefordra parameter värden som skickas till ett skript eller en funktion från `Test2` funktion till `Test1` funktionen.</span><span class="sxs-lookup"><span data-stu-id="361ce-166">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="361ce-167">Båda anropen till `Test1` funktionen från `Test2` använder ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-167">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

```powershell
function Test1
{
    param($a, $b, $c)

    $a
    $b
    $c
}

function Test2
{
    param($a, $b, $c)

    #Call the Test1 function with $a, $b, and $c.
    Test1 @PsBoundParameters

    #Call the Test1 function with $b and $c, but not with $a
    $LimitedParameters = $PSBoundParameters
    $LimitedParameters.Remove("a") | Out-Null
    Test1 @LimitedParameters
}
```

```Output
Test2 -a 1 -b 2 -c 3
1
2
3
2
3
```

### <a name="example-3-override-splatted-parameters-with-explicitly-defined-parameters"></a><span data-ttu-id="361ce-168">Exempel 3: Åsidosätt splatted-parametrar med explicit definierade parametrar</span><span class="sxs-lookup"><span data-stu-id="361ce-168">Example 3: Override splatted parameters with explicitly defined parameters</span></span>

<span data-ttu-id="361ce-169">I det här exemplet visas hur du åsidosätter en splatted-parameter med explicit definierade parametrar.</span><span class="sxs-lookup"><span data-stu-id="361ce-169">This example shows how to override a splatted parameter using explicitly defined parameters.</span></span> <span data-ttu-id="361ce-170">Detta är användbart när du inte vill bygga en ny hash-hash eller ändra ett värde i den hash-tabellen som du använder för att splat.</span><span class="sxs-lookup"><span data-stu-id="361ce-170">This is useful when you don't want to build a new hashtable or change a value in the hashtable you are using to splat.</span></span>

<span data-ttu-id="361ce-171">`$commonParams`Variabeln lagrar parametrarna för att skapa virtuella datorer på `East US` platsen.</span><span class="sxs-lookup"><span data-stu-id="361ce-171">The `$commonParams` variable stores the parameters to create virtual machines in the `East US` location.</span></span> <span data-ttu-id="361ce-172">`$allVms`Variabeln är en lista över virtuella datorer som ska skapas.</span><span class="sxs-lookup"><span data-stu-id="361ce-172">The `$allVms` variable is a list of virtual machines to create.</span></span> <span data-ttu-id="361ce-173">Vi går igenom listan och använder `$commonParams` för att splat parametrarna för att skapa varje virtuell dator.</span><span class="sxs-lookup"><span data-stu-id="361ce-173">We loop through the list and use `$commonParams` to splat the parameters to create each virtual machine.</span></span> <span data-ttu-id="361ce-174">Vi vill dock `myVM2` skapa i en annan region än de andra virtuella datorerna.</span><span class="sxs-lookup"><span data-stu-id="361ce-174">However, we want `myVM2` to be created in a different region than the other virtual machines.</span></span> <span data-ttu-id="361ce-175">I stället för att justera `$commonParams` hash-tabellen kan du uttryckligen definiera **plats** parametern i `New-AzVm` som ersätter värdet för `Location` nyckeln i `$commonParams` .</span><span class="sxs-lookup"><span data-stu-id="361ce-175">Instead of adjusting the `$commonParams` hashtable, you can explicitly define the **Location** parameter in `New-AzVm` to supersede the value of the `Location` key in `$commonParams`.</span></span>

```powershell
$commonParams = @{
    ResourceGroupName = "myResourceGroup"
    Location = "East US"
    VirtualNetworkName = "myVnet"
    SubnetName = "mySubnet"
    SecurityGroupName = "myNetworkSecurityGroup"
    PublicIpAddressName = "myPublicIpAddress"
}

$allVms = @('myVM1','myVM2','myVM3',)

foreach ($vm in $allVms)
{
    if ($vm -eq 'myVM2')
    {
        New-AzVm @commonParams -Name $vm -Location "West US"
    }
    else
    {
        New-AzVm @commonParams -Name $vm
    }
}
```

## <a name="splatting-command-parameters"></a><span data-ttu-id="361ce-176">Ihopbuntning kommando parametrar</span><span class="sxs-lookup"><span data-stu-id="361ce-176">Splatting command parameters</span></span>

<span data-ttu-id="361ce-177">Du kan använda ihopbuntning för att representera parametrarna för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="361ce-177">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="361ce-178">Den här metoden är användbar när du skapar en proxy-funktion, det vill säga en funktion som anropar ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="361ce-178">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="361ce-179">Den här funktionen introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="361ce-179">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="361ce-180">Om du vill splat parametrar för ett kommando använder `@Args` du för att representera kommando parametrarna.</span><span class="sxs-lookup"><span data-stu-id="361ce-180">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="361ce-181">Den här metoden är enklare än att räkna upp kommando parametrar och det fungerar utan att göra ändringar även om parametrarna för den anropade kommando ändringen.</span><span class="sxs-lookup"><span data-stu-id="361ce-181">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="361ce-182">Funktionen använder den `$Args` automatiska variabeln som innehåller alla otilldelade parameter värden.</span><span class="sxs-lookup"><span data-stu-id="361ce-182">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="361ce-183">Följande funktion anropar exempelvis `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="361ce-183">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="361ce-184">I den här funktionen `@Args` representerar alla parametrar för `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="361ce-184">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="361ce-185">När du använder `Get-MyProcess` funktionen skickas alla otilldelade parametrar och parameter värden till `@Args` , som du ser i följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="361ce-185">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

```powershell
Get-MyProcess -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    463      46   225484     237196   719    15.86   3228 powershell
```

```powershell
Get-MyProcess -Name PowerShell_Ise -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.2.9200.16384   6.2.9200.1638... C:\Windows\system32\WindowsPowerShell\...
```

<span data-ttu-id="361ce-186">Du kan använda `@Args` i en funktion som har explicit deklarerade parametrar.</span><span class="sxs-lookup"><span data-stu-id="361ce-186">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="361ce-187">Du kan använda det mer än en gång i en funktion, men alla parametrar som du anger skickas till alla instanser av `@Args` , som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="361ce-187">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

```powershell
function Get-MyCommand
{
    Param ([switch]$P, [switch]$C)
    if ($P) { Get-Process @Args }
    if ($C) { Get-Command @Args }
}

Get-MyCommand -P -C -Name PowerShell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
408      28    75568      83176   620     1.33   1692 powershell

Path               : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Extension          : .exe
Definition         : C:\Windows\System32\WindowsPowerShell\v1.0\powershell.e
Visibility         : Public
OutputType         : {System.String}
Name               : powershell.exe
CommandType        : Application
ModuleName         :
Module             :
RemotingCapability : PowerShell
Parameters         :
ParameterSets      :
HelpUri            :
FileVersionInfo    : File:             C:\Windows\System32\WindowsPowerShell
                     \v1.0\powershell.exe
                     InternalName:     POWERSHELL
                     OriginalFilename: PowerShell.EXE.MUI
                     FileVersion:      10.0.14393.0 (rs1_release.160715-1616
                     FileDescription:  Windows PowerShell
                     Product:          Microsoft Windows Operating System
                     ProductVersion:   10.0.14393.0
                     Debug:            False
                     Patched:          False
                     PreRelease:       False
                     PrivateBuild:     False
                     SpecialBuild:     False
                     Language:         English (United States)
```

## <a name="notes"></a><span data-ttu-id="361ce-188">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="361ce-188">Notes</span></span>

<span data-ttu-id="361ce-189">Om du gör en funktion i en avancerad funktion med antingen **CmdletBinding** -eller- **parametervärdena** är den `$args` automatiska variabeln inte längre tillgänglig i funktionen.</span><span class="sxs-lookup"><span data-stu-id="361ce-189">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="361ce-190">Avancerade funktioner kräver explicit parameter definition.</span><span class="sxs-lookup"><span data-stu-id="361ce-190">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="361ce-191">PowerShell Desired State Configuration (DSC) har inte utformats för att använda ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="361ce-191">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="361ce-192">Du kan inte använda ihopbuntning för att skicka värden till en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="361ce-192">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="361ce-193">Mer information finns i artikeln [pseudo-IHOPBUNTNING DSC-resurser](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)för Gael-Colas.</span><span class="sxs-lookup"><span data-stu-id="361ce-193">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="361ce-194">Se även</span><span class="sxs-lookup"><span data-stu-id="361ce-194">See also</span></span>

[<span data-ttu-id="361ce-195">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="361ce-195">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="361ce-196">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="361ce-196">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="361ce-197">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="361ce-197">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="361ce-198">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="361ce-198">about_Parameters</span></span>](about_Parameters.md)
