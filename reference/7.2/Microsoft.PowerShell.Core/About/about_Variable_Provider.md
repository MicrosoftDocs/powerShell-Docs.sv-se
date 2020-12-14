---
description: Variabel
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabel leverantör
ms.openlocfilehash: f93e58c24fdfc085983459d214db931274e164e2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708838"
---
# <a name="variable-provider"></a><span data-ttu-id="fa11b-103">Variabel leverantör</span><span class="sxs-lookup"><span data-stu-id="fa11b-103">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="fa11b-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="fa11b-104">Provider name</span></span>
<span data-ttu-id="fa11b-105">Variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-105">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="fa11b-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="fa11b-106">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="fa11b-107">Funktioner</span><span class="sxs-lookup"><span data-stu-id="fa11b-107">Capabilities</span></span>

<span data-ttu-id="fa11b-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="fa11b-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="fa11b-109">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="fa11b-109">Short description</span></span>

<span data-ttu-id="fa11b-110">Ger åtkomst till PowerShell-variablerna och deras värden.</span><span class="sxs-lookup"><span data-stu-id="fa11b-110">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="fa11b-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="fa11b-111">Detailed description</span></span>

<span data-ttu-id="fa11b-112">Med PowerShell- **variabeln** Provider kan du hämta, lägga till, ändra, rensa och ta bort PowerShell-variabler i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-112">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="fa11b-113">PowerShell- **variabeln** provider stöder variabler som PowerShell skapar, inklusive automatiska variabler, inställningar för variabler och variabler som du skapar.</span><span class="sxs-lookup"><span data-stu-id="fa11b-113">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="fa11b-114">**Variabeln** Drive är en planad namnrymd som bara innehåller de variabla objekten.</span><span class="sxs-lookup"><span data-stu-id="fa11b-114">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="fa11b-115">Variablerna har inga underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="fa11b-115">The variables have no child items.</span></span>

<span data-ttu-id="fa11b-116">**Variabeln** provider stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="fa11b-116">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="fa11b-117">Get-location</span><span class="sxs-lookup"><span data-stu-id="fa11b-117">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="fa11b-118">Ange plats</span><span class="sxs-lookup"><span data-stu-id="fa11b-118">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="fa11b-119">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="fa11b-119">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="fa11b-120">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="fa11b-120">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="fa11b-121">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="fa11b-121">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="fa11b-122">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="fa11b-122">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="fa11b-123">PowerShell innehåller också en uppsättning cmdlets som utformats särskilt för att visa och ändra variabler.</span><span class="sxs-lookup"><span data-stu-id="fa11b-123">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="fa11b-124">När du använder **variabel** -cmdletar behöver du inte ange `Variable:` enheten i namnet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-124">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="fa11b-125">Den här artikeln beskriver inte hur du arbetar med **variabel** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="fa11b-125">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="fa11b-126">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="fa11b-126">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="fa11b-127">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-127">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="fa11b-128">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="fa11b-128">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="fa11b-129">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-129">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="fa11b-130">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="fa11b-130">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="fa11b-131">Du kan också använda PowerShell Expression parser för att skapa, Visa och ändra värdena för variabler utan att använda cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="fa11b-131">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="fa11b-132">När du arbetar med variabler direkt använder du ett dollar tecken ( `$` ) för att identifiera namnet som en variabel och tilldelnings operatorn ( `=` ) för att upprätta och ändra värdet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-132">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="fa11b-133">Till exempel `$p = Get-Process` skapar `p` variabeln och lagrar resultatet av ett `Get-Process` kommando i den.</span><span class="sxs-lookup"><span data-stu-id="fa11b-133">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="fa11b-134">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="fa11b-134">Types exposed by this provider</span></span>

<span data-ttu-id="fa11b-135">Variabler kan vara en av flera olika typer.</span><span class="sxs-lookup"><span data-stu-id="fa11b-135">Variables can be one of several different types.</span></span> <span data-ttu-id="fa11b-136">De flesta variabler är instanser av `PSVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-136">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="fa11b-137">Andra variabler och deras typer visas nedan.</span><span class="sxs-lookup"><span data-stu-id="fa11b-137">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="fa11b-138">`?`Variabeln är en instans av `QuestionMarkVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-138">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="fa11b-139">`null`Variabeln är en instans av `NullVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-139">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="fa11b-140">Variablerna för maximalt antal är instanser av `SessionStateCapacityVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-140">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="fa11b-141">`LocalVariable` instanser innehåller information om aktuell körning, till exempel:</span><span class="sxs-lookup"><span data-stu-id="fa11b-141">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="fa11b-142">Navigera mellan variabla enheter</span><span class="sxs-lookup"><span data-stu-id="fa11b-142">Navigating the Variable drives</span></span>

<span data-ttu-id="fa11b-143">**Variabeln** Provider visar data lagret i `Variable:` enheten.</span><span class="sxs-lookup"><span data-stu-id="fa11b-143">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="fa11b-144">Om du vill arbeta med variabler kan du ändra din plats till `Variable:` enheten ( `Set-Location Variable:` ) eller så kan du arbeta från en annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-144">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="fa11b-145">Om du vill referera till en variabel från en annan plats använder du enhets namnet ( `Variable:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-145">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="fa11b-146">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="fa11b-146">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="fa11b-147">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="fa11b-147">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="fa11b-148">Du kan också arbeta med den **variabla** providern från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="fa11b-148">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="fa11b-149">Om du vill referera till en variabel från en annan plats använder du enhets namnet `Variable:` i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-149">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="fa11b-150">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="fa11b-150">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="fa11b-151">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="fa11b-151">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="fa11b-152">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="fa11b-152">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="fa11b-153">Visar värdet för variabler</span><span class="sxs-lookup"><span data-stu-id="fa11b-153">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="fa11b-154">Hämta alla variabler i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="fa11b-154">Get all variables in the current session</span></span>

<span data-ttu-id="fa11b-155">Det här kommandot hämtar listan över alla variabler och deras värden i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-155">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="fa11b-156">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-156">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="fa11b-157">Hämta en variabel med dess Provider-sökväg</span><span class="sxs-lookup"><span data-stu-id="fa11b-157">Get a variable using its provider path</span></span>

<span data-ttu-id="fa11b-158">Det här kommandot hämtar ett variabel värde med hjälp av dess Provider-sökväg som föregås av dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="fa11b-158">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="fa11b-159">Detta har samma resultat som när du reparerar variabelns namn med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="fa11b-159">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="fa11b-160">Hämta variabler med jokertecken</span><span class="sxs-lookup"><span data-stu-id="fa11b-160">Get variables using wildcards</span></span>

<span data-ttu-id="fa11b-161">Det här kommandot hämtar variablerna med namn som börjar med "Max".</span><span class="sxs-lookup"><span data-stu-id="fa11b-161">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="fa11b-162">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-162">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="fa11b-163">Hämta värdet för?</span><span class="sxs-lookup"><span data-stu-id="fa11b-163">Get the value of the ?</span></span> <span data-ttu-id="fa11b-164">variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-164">variable</span></span>

<span data-ttu-id="fa11b-165">Det här kommandot använder `-LiteralPath` parametern för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) för att hämta värdet för `?` variabeln i `Variable:` enheten.</span><span class="sxs-lookup"><span data-stu-id="fa11b-165">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="fa11b-166">`?`Är ett jokertecken i sökvägar, men `Get-ChildItem` försöker inte matcha jokertecken i värdena för `-LiteralPath` parametern.</span><span class="sxs-lookup"><span data-stu-id="fa11b-166">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="fa11b-167">Hämta ReadOnly och konstanta variabler</span><span class="sxs-lookup"><span data-stu-id="fa11b-167">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="fa11b-168">Det här kommandot hämtar de variabler som har värdet `ReadOnly` eller `Constant` för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="fa11b-168">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="fa11b-169">Skapa variabler</span><span class="sxs-lookup"><span data-stu-id="fa11b-169">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="fa11b-170">Skapa en ny variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-170">Create a new variable</span></span>

<span data-ttu-id="fa11b-171">Det här kommandot skapar `services` variabeln och lagrar resultatet av ett `Get-Service` kommando i det.</span><span class="sxs-lookup"><span data-stu-id="fa11b-171">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="fa11b-172">Eftersom den aktuella platsen finns i `Variable:` enheten är värdet för `-Path` parametern en punkt ( `.` ) som representerar den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-172">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="fa11b-173">Parenteserna runt `Get-Service` kommandot ser till att kommandot utförs innan variabeln skapas.</span><span class="sxs-lookup"><span data-stu-id="fa11b-173">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="fa11b-174">Utan parenteser är värdet för den nya variabeln en "Get-service"-sträng.</span><span class="sxs-lookup"><span data-stu-id="fa11b-174">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="fa11b-175">Skapa en variabel med en absolut sökväg</span><span class="sxs-lookup"><span data-stu-id="fa11b-175">Create a variable using an absolute path</span></span>

<span data-ttu-id="fa11b-176">Det här kommandot skapar en `services` variabel och lagrar resultatet av ett `Get-Service` kommando i det.</span><span class="sxs-lookup"><span data-stu-id="fa11b-176">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="fa11b-177">Om du vill skapa en variabel utan värde utelämnar du tilldelnings operatorn.</span><span class="sxs-lookup"><span data-stu-id="fa11b-177">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="fa11b-178">Ändra variabler</span><span class="sxs-lookup"><span data-stu-id="fa11b-178">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="fa11b-179">Byta namn på en variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-179">Rename a variable</span></span>

<span data-ttu-id="fa11b-180">Det här kommandot använder `Rename-Item` cmdleten för att ändra namnet på `a` variabeln till `processes` .</span><span class="sxs-lookup"><span data-stu-id="fa11b-180">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="fa11b-181">Ändra värdet för en variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-181">Change the value of a variable</span></span>

<span data-ttu-id="fa11b-182">Det här kommandot använder `Set-Item` cmdleten för att ändra värdet för `ErrorActionPreference` variabeln till "stoppa".</span><span class="sxs-lookup"><span data-stu-id="fa11b-182">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="fa11b-183">Kopiera en variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-183">Copy a variable</span></span>

<span data-ttu-id="fa11b-184">Det här kommandot använder `Copy-Item` cmdleten för att kopiera `processes` variabeln till `old_processes` .</span><span class="sxs-lookup"><span data-stu-id="fa11b-184">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="fa11b-185">Detta skapar en ny variabel med namnet `old_processes` som har samma värde som `processes` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fa11b-185">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="fa11b-186">Ta bort en variabel</span><span class="sxs-lookup"><span data-stu-id="fa11b-186">Delete a variable</span></span>

<span data-ttu-id="fa11b-187">Det här kommandot tar bort `serv` variabeln från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fa11b-187">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="fa11b-188">Du kan använda det här kommandot i valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-188">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="fa11b-189">Ta bort variabler med parametern-Force</span><span class="sxs-lookup"><span data-stu-id="fa11b-189">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="fa11b-190">Det här kommandot tar bort alla variabler från den aktuella sessionen, förutom variabler vars **alternativ** -egenskap har värdet `Constant` .</span><span class="sxs-lookup"><span data-stu-id="fa11b-190">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="fa11b-191">Utan `-Force` parametern tar kommandot inte bort variabler vars **alternativ** egenskap har värdet `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="fa11b-191">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="fa11b-192">Ange värdet för en variabel till NULL</span><span class="sxs-lookup"><span data-stu-id="fa11b-192">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="fa11b-193">Det här kommandot använder `Clear-Item` cmdleten för att ändra värdet för `processes` variabeln till null.</span><span class="sxs-lookup"><span data-stu-id="fa11b-193">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="fa11b-194">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="fa11b-194">Using the pipeline</span></span>

<span data-ttu-id="fa11b-195">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="fa11b-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="fa11b-196">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa11b-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="fa11b-197">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="fa11b-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="fa11b-198">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="fa11b-198">Getting help</span></span>

<span data-ttu-id="fa11b-199">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="fa11b-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="fa11b-200">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="fa11b-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="fa11b-201">Se även</span><span class="sxs-lookup"><span data-stu-id="fa11b-201">See also</span></span>

[<span data-ttu-id="fa11b-202">about_Variables</span><span class="sxs-lookup"><span data-stu-id="fa11b-202">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="fa11b-203">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="fa11b-203">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="fa11b-204">about_Providers</span><span class="sxs-lookup"><span data-stu-id="fa11b-204">about_Providers</span></span>](../About/about_Providers.md)

