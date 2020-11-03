---
description: Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_splatting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Splatting
ms.openlocfilehash: 6918f6699f9da8a24b1284a06a5bb5b4454ca0d7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269931"
---
# <a name="about-splatting"></a><span data-ttu-id="82627-104">Om Ihopbuntning</span><span class="sxs-lookup"><span data-stu-id="82627-104">About Splatting</span></span>

## <a name="short-description"></a><span data-ttu-id="82627-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="82627-105">Short description</span></span>

<span data-ttu-id="82627-106">Beskriver hur du använder ihopbuntning för att skicka parametrar till kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="82627-106">Describes how to use splatting to pass parameters to commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="82627-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="82627-107">Long description</span></span>

<span data-ttu-id="82627-108">Ihopbuntning är en metod för att skicka en samling parameter värden till ett kommando som en enhet.</span><span class="sxs-lookup"><span data-stu-id="82627-108">Splatting is a method of passing a collection of parameter values to a command as a unit.</span></span> <span data-ttu-id="82627-109">PowerShell kopplar varje värde i samlingen med en kommando parameter.</span><span class="sxs-lookup"><span data-stu-id="82627-109">PowerShell associates each value in the collection with a command parameter.</span></span> <span data-ttu-id="82627-110">Splatted parameter värden lagras i namngivna ihopbuntning-variabler, som ser ut som standardvariabler, men börjar med en symbol ( `@` ) i stället för ett dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="82627-110">Splatted parameter values are stored in named splatting variables, which look like standard variables, but begin with an At symbol (`@`) instead of a dollar sign (`$`).</span></span> <span data-ttu-id="82627-111">Vid-symbolen visas PowerShell att du skickar en samling värden i stället för ett enda värde.</span><span class="sxs-lookup"><span data-stu-id="82627-111">The At symbol tells PowerShell that you are passing a collection of values, instead of a single value.</span></span>

<span data-ttu-id="82627-112">Ihopbuntning gör kommandona kortare och lättare att läsa.</span><span class="sxs-lookup"><span data-stu-id="82627-112">Splatting makes your commands shorter and easier to read.</span></span> <span data-ttu-id="82627-113">Du kan återanvända ihopbuntning-värden i olika kommando anrop och använda ihopbuntning för att skicka parameter värden från den `$PSBoundParameters` automatiska variabeln till andra skript och funktioner.</span><span class="sxs-lookup"><span data-stu-id="82627-113">You can reuse the splatting values in different command calls and use splatting to pass parameter values from the `$PSBoundParameters` automatic variable to other scripts and functions.</span></span>

<span data-ttu-id="82627-114">Från och med Windows PowerShell 3,0 kan du också använda ihopbuntning för att representera alla parametrar för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="82627-114">Beginning in Windows PowerShell 3.0, you can also use splatting to represent all parameters of a command.</span></span>

## <a name="syntax"></a><span data-ttu-id="82627-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="82627-115">Syntax</span></span>

```
<CommandName> <optional parameters> @<HashTable> <optional parameters>
<CommandName> <optional parameters> @<Array> <optional parameters>
```

<span data-ttu-id="82627-116">Använd mat ris syntaxen för att ange parameter värden för positions parametrar, där parameter namn inte krävs.</span><span class="sxs-lookup"><span data-stu-id="82627-116">To provide parameter values for positional parameters, in which parameter names are not required, use the array syntax.</span></span> <span data-ttu-id="82627-117">Använd syntaxen för hash-tabellen för att ange parameter namn och värdepar.</span><span class="sxs-lookup"><span data-stu-id="82627-117">To provide parameter name and value pairs, use the hash table syntax.</span></span> <span data-ttu-id="82627-118">Splatted-värdet kan finnas var som helst i parameter listan.</span><span class="sxs-lookup"><span data-stu-id="82627-118">The splatted value can appear anywhere in the parameter list.</span></span>

<span data-ttu-id="82627-119">När ihopbuntning inte behöver använda en hash-tabell eller en matris för att skicka alla parametrar.</span><span class="sxs-lookup"><span data-stu-id="82627-119">When splatting, you do not need to use a hash table or an array to pass all parameters.</span></span> <span data-ttu-id="82627-120">Du kan skicka vissa parametrar genom att använda ihopbuntning och skicka andra efter position eller parameter namn.</span><span class="sxs-lookup"><span data-stu-id="82627-120">You may pass some parameters by using splatting and pass others by position or by parameter name.</span></span> <span data-ttu-id="82627-121">Du kan också splat flera objekt i ett enda kommando så att du inte skickar fler än ett värde för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="82627-121">Also, you can splat multiple objects in a single command so you don't pass more than one value for each parameter.</span></span>

## <a name="splatting-with-hash-tables"></a><span data-ttu-id="82627-122">Ihopbuntning med hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="82627-122">Splatting with hash tables</span></span>

<span data-ttu-id="82627-123">Använd en hash-tabell för att splat parameter namn och värdepar.</span><span class="sxs-lookup"><span data-stu-id="82627-123">Use a hash table to splat parameter name and value pairs.</span></span> <span data-ttu-id="82627-124">Du kan använda det här formatet för alla parameter typer, inklusive parametrar för position och växling.</span><span class="sxs-lookup"><span data-stu-id="82627-124">You can use this format for all parameter types, including positional and switch parameters.</span></span>
<span data-ttu-id="82627-125">Positions parametrar måste tilldelas med namn.</span><span class="sxs-lookup"><span data-stu-id="82627-125">Positional parameters must be assigned by name.</span></span>

<span data-ttu-id="82627-126">I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="82627-126">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="82627-127">I det första exemplet används det traditionella formatet där parameter namn ingår.</span><span class="sxs-lookup"><span data-stu-id="82627-127">The first example uses the traditional format in which parameter names are included.</span></span>

```powershell
Copy-Item -Path "test.txt" -Destination "test2.txt" -WhatIf
```

<span data-ttu-id="82627-128">I det andra exemplet används hash-tabellens ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-128">The second example uses hash table splatting.</span></span> <span data-ttu-id="82627-129">Det första kommandot skapar en hash-tabell med parameter namn och parameter-värdepar och lagrar den i `$HashArguments` variabeln.</span><span class="sxs-lookup"><span data-stu-id="82627-129">The first command creates a hash table of parameter-name and parameter-value pairs and stores it in the `$HashArguments` variable.</span></span> <span data-ttu-id="82627-130">Det andra kommandot använder `$HashArguments` variabeln i ett kommando med ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-130">The second command uses the `$HashArguments` variable in a command with splatting.</span></span> <span data-ttu-id="82627-131">Symbolen vid ( `@HashArguments` ) ersätter dollar tecknet ( `$HashArguments` ) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82627-131">The At symbol (`@HashArguments`) replaces the dollar sign (`$HashArguments`) in the command.</span></span>

<span data-ttu-id="82627-132">Använd eller om du vill ange **WhatIf** ett värde för parametern whatIf `$True` switch `$False` .</span><span class="sxs-lookup"><span data-stu-id="82627-132">To provide a value for the **WhatIf** switch parameter, use `$True` or `$False`.</span></span>

```powershell
$HashArguments = @{
  Path = "test.txt"
  Destination = "test2.txt"
  WhatIf = $true
}
Copy-Item @HashArguments
```

> [!NOTE]
> <span data-ttu-id="82627-133">I det första kommandot indikerar symbolen ( `@` ) en hash-tabell, inte ett splatted-värde.</span><span class="sxs-lookup"><span data-stu-id="82627-133">In the first command, the At symbol (`@`) indicates a hash table, not a splatted value.</span></span> <span data-ttu-id="82627-134">Syntaxen för hash-tabeller i PowerShell är: `@{<name>=<value>; <name>=<value>; ...}`</span><span class="sxs-lookup"><span data-stu-id="82627-134">The syntax for hash tables in PowerShell is: `@{<name>=<value>; <name>=<value>; ...}`</span></span>

## <a name="splatting-with-arrays"></a><span data-ttu-id="82627-135">Ihopbuntning med matriser</span><span class="sxs-lookup"><span data-stu-id="82627-135">Splatting with arrays</span></span>

<span data-ttu-id="82627-136">Använd en matris för att splat värden för positions parametrar, vilket inte kräver parameter namn.</span><span class="sxs-lookup"><span data-stu-id="82627-136">Use an array to splat values for positional parameters, which do not require parameter names.</span></span> <span data-ttu-id="82627-137">Värdena måste vara i positions nummer ordningen i matrisen.</span><span class="sxs-lookup"><span data-stu-id="82627-137">The values must be in position-number order in the array.</span></span>

<span data-ttu-id="82627-138">I följande exempel jämförs två `Copy-Item` kommandon som kopierar Test.txt-filen till Test2.txt-filen i samma katalog.</span><span class="sxs-lookup"><span data-stu-id="82627-138">The following examples compare two `Copy-Item` commands that copy the Test.txt file to the Test2.txt file in the same directory.</span></span>

<span data-ttu-id="82627-139">I det första exemplet används det traditionella formatet där parameter namn utelämnas.</span><span class="sxs-lookup"><span data-stu-id="82627-139">The first example uses the traditional format in which parameter names are omitted.</span></span> <span data-ttu-id="82627-140">Parameter värden visas i positions ordning i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82627-140">The parameter values appear in position order in the command.</span></span>

```powershell
Copy-Item "test.txt" "test2.txt" -WhatIf
```

<span data-ttu-id="82627-141">I det andra exemplet används matrisen ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-141">The second example uses array splatting.</span></span> <span data-ttu-id="82627-142">Det första kommandot skapar en matris med parameter värden och lagrar den i `$ArrayArguments` variabeln.</span><span class="sxs-lookup"><span data-stu-id="82627-142">The first command creates an array of the parameter values and stores it in the `$ArrayArguments` variable.</span></span> <span data-ttu-id="82627-143">Värdena är i positions ordning i matrisen.</span><span class="sxs-lookup"><span data-stu-id="82627-143">The values are in position order in the array.</span></span> <span data-ttu-id="82627-144">Det andra kommandot använder `$ArrayArguments` variabeln i ett kommando i ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-144">The second command uses the `$ArrayArguments` variable in a command in splatting.</span></span> <span data-ttu-id="82627-145">Symbolen vid ( `@ArrayArguments` ) ersätter dollar tecknet ( `$ArrayArguments` ) i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82627-145">The At symbol (`@ArrayArguments`) replaces the dollar sign (`$ArrayArguments`) in the command.</span></span>

```powershell
$ArrayArguments = "test.txt", "test2.txt"
Copy-Item @ArrayArguments -WhatIf
```

### <a name="using-the-argumentlist-parameter"></a><span data-ttu-id="82627-146">Använda parametern argument List</span><span class="sxs-lookup"><span data-stu-id="82627-146">Using the ArgumentList parameter</span></span>

<span data-ttu-id="82627-147">Flera cmdlets har en **argument List** -parameter som används för att skicka parameter värden till ett skript block som körs av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82627-147">Several cmdlets have an **ArgumentList** parameter that is used to pass parameter values to a script block that is executed by the cmdlet.</span></span> <span data-ttu-id="82627-148">Parametern **argument List** tar en matris med värden som skickas till-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="82627-148">The **ArgumentList** parameter takes an array of values that is passed to the script block.</span></span> <span data-ttu-id="82627-149">PowerShell använder i själva verket matris-ihopbuntning för att binda värdena till parametrarna i skript blocket.</span><span class="sxs-lookup"><span data-stu-id="82627-149">PowerShell is effectively using array splatting to bind the values to the parameters of the script block.</span></span> <span data-ttu-id="82627-150">Om du behöver skicka en matris som ett enda objekt som är kopplat till en enskild parameter när du använder **argument List** måste du figursätta matrisen som det enda elementet i en annan matris.</span><span class="sxs-lookup"><span data-stu-id="82627-150">When using **ArgumentList** , if you need to pass an array as a single object bound to a single parameter, you must wrap the array as the only element of another array.</span></span>

<span data-ttu-id="82627-151">I följande exempel finns ett skript block som använder en enda parameter som är en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="82627-151">The following example has a script block that takes a single parameter that is an array of strings.</span></span>

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
  } -ArgumentList $array
```

<span data-ttu-id="82627-152">I det här exemplet skickas endast det första objektet i `$array` till-skript blocket.</span><span class="sxs-lookup"><span data-stu-id="82627-152">In this example, only the first item in `$array` is passed to the script block.</span></span>

```Output
Hello
```

```powershell
$array = 'Hello', 'World!'
Invoke-Command -ScriptBlock {
  param([string[]]$words) $words -join ' '
} -ArgumentList (,$array)
````

<span data-ttu-id="82627-153">I det här exemplet `$array` är omslutna i en matris så att hela matrisen skickas till-skript blocket som ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="82627-153">In this example, `$array` is wrapped in an array so that the entire array is passed to the script block as a single object.</span></span>

```Output
Hello World!
```

## <a name="examples"></a><span data-ttu-id="82627-154">Exempel</span><span class="sxs-lookup"><span data-stu-id="82627-154">Examples</span></span>

<span data-ttu-id="82627-155">Det här exemplet visar hur du återanvänder splatted-värden i olika kommandon.</span><span class="sxs-lookup"><span data-stu-id="82627-155">This example shows how to reuse splatted values in different commands.</span></span> <span data-ttu-id="82627-156">Kommandona i det här exemplet använder `Write-Host` cmdleten för att skriva meddelanden till värd program konsolen.</span><span class="sxs-lookup"><span data-stu-id="82627-156">The commands in this example use the `Write-Host` cmdlet to write messages to the host program console.</span></span> <span data-ttu-id="82627-157">Den använder ihopbuntning för att ange förgrunds-och bakgrunds färger.</span><span class="sxs-lookup"><span data-stu-id="82627-157">It uses splatting to specify the foreground and background colors.</span></span>

<span data-ttu-id="82627-158">Ändra värdet för variabeln om du vill ändra färgerna på alla kommandon `$Colors` .</span><span class="sxs-lookup"><span data-stu-id="82627-158">To change the colors of all commands, just change the value of the `$Colors` variable.</span></span>

<span data-ttu-id="82627-159">Det första kommandot skapar en hash-tabell med parameter namn och värden och lagrar hash-tabellen i `$Colors` variabeln.</span><span class="sxs-lookup"><span data-stu-id="82627-159">The first command creates a hash table of parameter names and values and stores the hash table in the `$Colors` variable.</span></span>

```powershell
$Colors = @{ForegroundColor = "black"; BackgroundColor = "white"}
```

<span data-ttu-id="82627-160">Det andra och tredje kommandot använder `$Colors` variabeln för ihopbuntning i ett `Write-Host` kommando.</span><span class="sxs-lookup"><span data-stu-id="82627-160">The second and third commands use the `$Colors` variable for splatting in a `Write-Host` command.</span></span> <span data-ttu-id="82627-161">Om du vill använda `$Colors variable` ersätter du dollar tecknet ( `$Colors` ) med en symbol ( `@Colors` ).</span><span class="sxs-lookup"><span data-stu-id="82627-161">To use the `$Colors variable`, replace the dollar sign (`$Colors`) with an At symbol (`@Colors`).</span></span>

```powershell
#Write a message with the colors in $Colors
Write-Host "This is a test." @Colors

#Write second message with same colors. The position of splatted
#hash table does not matter.
Write-Host @Colors "This is another test."
```

<span data-ttu-id="82627-162">Det här exemplet visar hur du vidarebefordrar sina parametrar till andra kommandon med hjälp av ihopbuntning och den `$PSBoundParameters` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="82627-162">This example shows how to forward their parameters to other commands by using splatting and the `$PSBoundParameters` automatic variable.</span></span>

<span data-ttu-id="82627-163">Den `$PSBoundParameters` automatiska variabeln är ett Dictionary-objekt (system. Collections. Generic. Dictionary) som innehåller alla parameter namn och värden som används när ett skript eller en funktion körs.</span><span class="sxs-lookup"><span data-stu-id="82627-163">The `$PSBoundParameters` automatic variable is a dictionary object (System.Collections.Generic.Dictionary) that contains all the parameter names and values that are used when a script or function is run.</span></span>

<span data-ttu-id="82627-164">I följande exempel använder vi `$PSBoundParameters` variabeln för att vidarebefordra parameter värden som skickas till ett skript eller en funktion från `Test2` funktion till `Test1` funktionen.</span><span class="sxs-lookup"><span data-stu-id="82627-164">In the following example, we use the `$PSBoundParameters` variable to forward the parameters values passed to a script or function from `Test2` function to the `Test1` function.</span></span> <span data-ttu-id="82627-165">Båda anropen till `Test1` funktionen från `Test2` använder ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-165">Both calls to the `Test1` function from `Test2` use splatting.</span></span>

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

## <a name="splatting-command-parameters"></a><span data-ttu-id="82627-166">Ihopbuntning kommando parametrar</span><span class="sxs-lookup"><span data-stu-id="82627-166">Splatting command parameters</span></span>

<span data-ttu-id="82627-167">Du kan använda ihopbuntning för att representera parametrarna för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="82627-167">You can use splatting to represent the parameters of a command.</span></span> <span data-ttu-id="82627-168">Den här metoden är användbar när du skapar en proxy-funktion, det vill säga en funktion som anropar ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="82627-168">This technique is useful when you are creating a proxy function, that is, a function that calls another command.</span></span> <span data-ttu-id="82627-169">Den här funktionen introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="82627-169">This feature is introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="82627-170">Om du vill splat parametrar för ett kommando använder `@Args` du för att representera kommando parametrarna.</span><span class="sxs-lookup"><span data-stu-id="82627-170">To splat the parameters of a command, use `@Args` to represent the command parameters.</span></span> <span data-ttu-id="82627-171">Den här metoden är enklare än att räkna upp kommando parametrar och det fungerar utan att göra ändringar även om parametrarna för den anropade kommando ändringen.</span><span class="sxs-lookup"><span data-stu-id="82627-171">This technique is easier than enumerating command parameters and it works without revision even if the parameters of the called command change.</span></span>

<span data-ttu-id="82627-172">Funktionen använder den `$Args` automatiska variabeln som innehåller alla otilldelade parameter värden.</span><span class="sxs-lookup"><span data-stu-id="82627-172">The feature uses the `$Args` automatic variable, which contains all unassigned parameter values.</span></span>

<span data-ttu-id="82627-173">Följande funktion anropar exempelvis `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82627-173">For example, the following function calls the `Get-Process` cmdlet.</span></span> <span data-ttu-id="82627-174">I den här funktionen `@Args` representerar alla parametrar för `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82627-174">In this function, `@Args` represents all the parameters of the `Get-Process` cmdlet.</span></span>

```powershell
function Get-MyProcess { Get-Process @Args }
```

<span data-ttu-id="82627-175">När du använder `Get-MyProcess` funktionen skickas alla otilldelade parametrar och parameter värden till `@Args` , som du ser i följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="82627-175">When you use the `Get-MyProcess` function, all unassigned parameters and parameter values are passed to `@Args`, as shown in the following commands.</span></span>

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

<span data-ttu-id="82627-176">Du kan använda `@Args` i en funktion som har explicit deklarerade parametrar.</span><span class="sxs-lookup"><span data-stu-id="82627-176">You can use `@Args` in a function that has explicitly declared parameters.</span></span> <span data-ttu-id="82627-177">Du kan använda det mer än en gång i en funktion, men alla parametrar som du anger skickas till alla instanser av `@Args` , som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="82627-177">You can use it more than once in a function, but all parameters that you enter are passed to all instances of `@Args`, as shown in the following example.</span></span>

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

## <a name="notes"></a><span data-ttu-id="82627-178">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="82627-178">Notes</span></span>

<span data-ttu-id="82627-179">Om du gör en funktion i en avancerad funktion med antingen **CmdletBinding** -eller- **parametervärdena** är den `$args` automatiska variabeln inte längre tillgänglig i funktionen.</span><span class="sxs-lookup"><span data-stu-id="82627-179">If you make a function into an advanced function by using either the **CmdletBinding** or **Parameter** attributes, the `$args` automatic variable is no longer available in the function.</span></span> <span data-ttu-id="82627-180">Avancerade funktioner kräver explicit parameter definition.</span><span class="sxs-lookup"><span data-stu-id="82627-180">Advanced functions require explicit parameter definition.</span></span>

<span data-ttu-id="82627-181">PowerShell Desired State Configuration (DSC) har inte utformats för att använda ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="82627-181">PowerShell Desired State Configuration (DSC) was not designed to use splatting.</span></span>
<span data-ttu-id="82627-182">Du kan inte använda ihopbuntning för att skicka värden till en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="82627-182">You cannot use splatting to pass values into a DSC resource.</span></span> <span data-ttu-id="82627-183">Mer information finns i artikeln [pseudo-IHOPBUNTNING DSC-resurser](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/)för Gael-Colas.</span><span class="sxs-lookup"><span data-stu-id="82627-183">For more information, see Gael Colas' article [Pseudo-Splatting DSC Resources](https://gaelcolas.com/2017/11/05/pseudo-splatting-dsc-resources/).</span></span>

## <a name="see-also"></a><span data-ttu-id="82627-184">Se även</span><span class="sxs-lookup"><span data-stu-id="82627-184">See also</span></span>

[<span data-ttu-id="82627-185">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="82627-185">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="82627-186">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="82627-186">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="82627-187">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="82627-187">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="82627-188">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="82627-188">about_Parameters</span></span>](about_Parameters.md)
