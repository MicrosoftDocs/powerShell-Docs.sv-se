---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: f915a5741ed5c63206da3c35f5322508515bd566
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264309"
---
# <span data-ttu-id="42664-103">Invoke-Expression</span><span class="sxs-lookup"><span data-stu-id="42664-103">Invoke-Expression</span></span>

## <span data-ttu-id="42664-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="42664-104">SYNOPSIS</span></span>
<span data-ttu-id="42664-105">Kör kommandon eller uttryck på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="42664-105">Runs commands or expressions on the local computer.</span></span>

## <span data-ttu-id="42664-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42664-106">SYNTAX</span></span>

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## <span data-ttu-id="42664-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="42664-107">DESCRIPTION</span></span>

<span data-ttu-id="42664-108">`Invoke-Expression`Cmdleten utvärderar eller kör en angiven sträng som ett kommando och returnerar resultatet av uttrycket eller kommandot.</span><span class="sxs-lookup"><span data-stu-id="42664-108">The `Invoke-Expression` cmdlet evaluates or runs a specified string as a command and returns the results of the expression or command.</span></span> <span data-ttu-id="42664-109">Utan `Invoke-Expression` , returneras en sträng som skickats på kommando raden (avskärmad) oförändrad.</span><span class="sxs-lookup"><span data-stu-id="42664-109">Without `Invoke-Expression`, a string submitted at the command line is returned (echoed) unchanged.</span></span>

<span data-ttu-id="42664-110">Uttryck utvärderas och körs i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="42664-110">Expressions are evaluated and run in the current scope.</span></span> <span data-ttu-id="42664-111">Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="42664-111">For more information, see [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="42664-112">Vidta rimliga försiktighets åtgärder när du använder `Invoke-Expression` cmdleten i skript.</span><span class="sxs-lookup"><span data-stu-id="42664-112">Take reasonable precautions when using the `Invoke-Expression` cmdlet in scripts.</span></span> <span data-ttu-id="42664-113">När `Invoke-Expression` du använder för att köra ett kommando som användaren anger, kontrollerar du att kommandot är säkert att köra innan du kör det.</span><span class="sxs-lookup"><span data-stu-id="42664-113">When using `Invoke-Expression` to run a command that the user enters, verify that the command is safe to run before running it.</span></span> <span data-ttu-id="42664-114">I allmänhet är det bäst att utforma ditt skript med fördefinierade ingångs alternativ i stället för att tillåta fri hands text.</span><span class="sxs-lookup"><span data-stu-id="42664-114">In general, it is best to design your script with predefined input options, rather than allowing freeform input.</span></span>

## <span data-ttu-id="42664-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="42664-115">EXAMPLES</span></span>

### <span data-ttu-id="42664-116">Exempel 1: utvärdera ett uttryck</span><span class="sxs-lookup"><span data-stu-id="42664-116">Example 1: Evaluate an expression</span></span>

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

<span data-ttu-id="42664-117">Det här exemplet demonstrerar användningen av `Invoke-Expression` för att utvärdera ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="42664-117">This example demonstrates the use of `Invoke-Expression` to evaluate an expression.</span></span> <span data-ttu-id="42664-118">Utan `Invoke-Expression` , skrivs uttrycket ut, men utvärderas inte.</span><span class="sxs-lookup"><span data-stu-id="42664-118">Without `Invoke-Expression`, the expression is printed, but not evaluated.</span></span>

<span data-ttu-id="42664-119">Det första kommandot tilldelar värdet `Get-Process` (en sträng) till `$Command` variabeln.</span><span class="sxs-lookup"><span data-stu-id="42664-119">The first command assigns a value of `Get-Process` (a string) to the `$Command` variable.</span></span>

<span data-ttu-id="42664-120">Det andra kommandot visar resultatet av att skriva variabel namnet på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="42664-120">The second command shows the effect of typing the variable name at the command line.</span></span> <span data-ttu-id="42664-121">PowerShell upprepar strängen.</span><span class="sxs-lookup"><span data-stu-id="42664-121">PowerShell echoes the string.</span></span>

<span data-ttu-id="42664-122">Det tredje kommandot använder `Invoke-Expression` för att utvärdera strängen.</span><span class="sxs-lookup"><span data-stu-id="42664-122">The third command uses `Invoke-Expression` to evaluate the string.</span></span>

### <span data-ttu-id="42664-123">Exempel 2: kör ett skript på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="42664-123">Example 2: Run a script on the local computer</span></span>

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

<span data-ttu-id="42664-124">Dessa kommandon används `Invoke-Expression` för att köra ett skript TestScript.ps1 på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="42664-124">These commands use `Invoke-Expression` to run a script, TestScript.ps1, on the local computer.</span></span> <span data-ttu-id="42664-125">De två kommandona är likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="42664-125">The two commands are equivalent.</span></span> <span data-ttu-id="42664-126">Först används **kommando** parametern för att ange kommandot som ska köras.</span><span class="sxs-lookup"><span data-stu-id="42664-126">The first uses the **Command** parameter to specify the command to run.</span></span>
<span data-ttu-id="42664-127">Den andra använder en pipeline-operator ( `|` ) för att skicka kommando strängen till `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="42664-127">The second uses a pipeline operator (`|`) to send the command string to `Invoke-Expression`.</span></span>

### <span data-ttu-id="42664-128">Exempel 3: köra ett kommando i en variabel</span><span class="sxs-lookup"><span data-stu-id="42664-128">Example 3: Run a command in a variable</span></span>

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

<span data-ttu-id="42664-129">I det här exemplet körs en kommando sträng som sparas i `$Command` variabeln.</span><span class="sxs-lookup"><span data-stu-id="42664-129">This example runs a command string that is saved in the `$Command` variable.</span></span>

<span data-ttu-id="42664-130">Kommando strängen omges av enkla citat tecken eftersom den innehåller en variabel, `$_` som representerar det aktuella objektet.</span><span class="sxs-lookup"><span data-stu-id="42664-130">The command string is enclosed in single quotation marks because it includes a variable, `$_`, which represents the current object.</span></span> <span data-ttu-id="42664-131">Om den omges av dubbla citat tecken `$_` skulle variabeln ersättas av sitt värde innan den sparades i `$Command` variabeln.</span><span class="sxs-lookup"><span data-stu-id="42664-131">If it were enclosed in double quotation marks, the `$_` variable would be replaced by its value before it was saved in the `$Command` variable.</span></span>

### <span data-ttu-id="42664-132">Exempel 4: Hämta och kör en cmdlet Help-exempel</span><span class="sxs-lookup"><span data-stu-id="42664-132">Example 4: Get and run a cmdlet Help example</span></span>

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

<span data-ttu-id="42664-133">Det här kommandot hämtar och kör det första exemplet i `Get-EventLog` Hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="42664-133">This command retrieves and runs the first example in the `Get-EventLog` cmdlet Help topic.</span></span>

<span data-ttu-id="42664-134">Om du vill köra ett exempel på en annan cmdlet ändrar du värdet för `$Cmdlet_name` variabeln till namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="42664-134">To run an example of a different cmdlet, change the value of the `$Cmdlet_name` variable to the name of the cmdlet.</span></span> <span data-ttu-id="42664-135">Och ändra `$Example_number` variabeln till det exempel nummer som du vill köra.</span><span class="sxs-lookup"><span data-stu-id="42664-135">And, change the `$Example_number` variable to the example number you want to run.</span></span> <span data-ttu-id="42664-136">Kommandot Miss lyckas om exempel numret inte är giltigt.</span><span class="sxs-lookup"><span data-stu-id="42664-136">The command fails if the example number is not valid.</span></span>

## <span data-ttu-id="42664-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="42664-137">PARAMETERS</span></span>

### <span data-ttu-id="42664-138">-Kommando</span><span class="sxs-lookup"><span data-stu-id="42664-138">-Command</span></span>

<span data-ttu-id="42664-139">Anger det kommando eller uttryck som ska köras.</span><span class="sxs-lookup"><span data-stu-id="42664-139">Specifies the command or expression to run.</span></span> <span data-ttu-id="42664-140">Skriv kommandot eller uttrycket eller ange en variabel som innehåller kommandot eller uttrycket.</span><span class="sxs-lookup"><span data-stu-id="42664-140">Type the command or expression or enter a variable that contains the command or expression.</span></span> <span data-ttu-id="42664-141">**Kommando** parametern måste anges.</span><span class="sxs-lookup"><span data-stu-id="42664-141">The **Command** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="42664-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42664-142">CommonParameters</span></span>

<span data-ttu-id="42664-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42664-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42664-144">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="42664-144">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="42664-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="42664-145">INPUTS</span></span>

### <span data-ttu-id="42664-146">System. String eller PSObject</span><span class="sxs-lookup"><span data-stu-id="42664-146">System.String or PSObject</span></span>

<span data-ttu-id="42664-147">Du kan skicka vidare ett objekt som representerar kommandot till `Invoke-Expression` .</span><span class="sxs-lookup"><span data-stu-id="42664-147">You can pipe an object that represents the command to `Invoke-Expression`.</span></span>
<span data-ttu-id="42664-148">Använd den `$Input` automatiska variabeln för att representera inobjekten i kommandot.</span><span class="sxs-lookup"><span data-stu-id="42664-148">Use the `$Input` automatic variable to represent the input objects in the command.</span></span>

## <span data-ttu-id="42664-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="42664-149">OUTPUTS</span></span>

### <span data-ttu-id="42664-150">PSObject</span><span class="sxs-lookup"><span data-stu-id="42664-150">PSObject</span></span>

<span data-ttu-id="42664-151">Returnerar utdata som genereras av det anropade kommandot (värdet för **kommando** parametern).</span><span class="sxs-lookup"><span data-stu-id="42664-151">Returns the output that is generated by the invoked command (the value of the **Command** parameter).</span></span>

## <span data-ttu-id="42664-152">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="42664-152">NOTES</span></span>

<span data-ttu-id="42664-153">I de flesta fall anropar du uttryck med PowerShell: s anrops operator och uppnår samma resultat.</span><span class="sxs-lookup"><span data-stu-id="42664-153">In most cases, you invoke expressions using PowerShell's call operator and achieve the same results.</span></span>
<span data-ttu-id="42664-154">Anrops operatorn är en säkrare metod.</span><span class="sxs-lookup"><span data-stu-id="42664-154">The call operator is a safer method.</span></span> <span data-ttu-id="42664-155">Mer information finns i [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span><span class="sxs-lookup"><span data-stu-id="42664-155">For more information, see [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).</span></span>

## <span data-ttu-id="42664-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="42664-156">RELATED LINKS</span></span>

[<span data-ttu-id="42664-157">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="42664-157">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="42664-158">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="42664-158">about_Scopes</span></span>](../Microsoft.PowerShell.Core/About/about_Scopes.md)

