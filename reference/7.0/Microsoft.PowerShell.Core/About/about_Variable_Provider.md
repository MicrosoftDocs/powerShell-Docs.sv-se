---
description: Variabel
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Variabel leverantör
ms.openlocfilehash: cae9a100b9e0a8fd044ec87d1541e1fe2bf440c8
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271322"
---
# <a name="variable-provider"></a><span data-ttu-id="22fd9-104">Variabel leverantör</span><span class="sxs-lookup"><span data-stu-id="22fd9-104">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="22fd9-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="22fd9-105">Provider name</span></span>
<span data-ttu-id="22fd9-106">Variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-106">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="22fd9-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="22fd9-107">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="22fd9-108">Funktioner</span><span class="sxs-lookup"><span data-stu-id="22fd9-108">Capabilities</span></span>

<span data-ttu-id="22fd9-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="22fd9-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="22fd9-110">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="22fd9-110">Short description</span></span>

<span data-ttu-id="22fd9-111">Ger åtkomst till PowerShell-variablerna och deras värden.</span><span class="sxs-lookup"><span data-stu-id="22fd9-111">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="22fd9-112">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="22fd9-112">Detailed description</span></span>

<span data-ttu-id="22fd9-113">Med PowerShell- **variabeln** Provider kan du hämta, lägga till, ändra, rensa och ta bort PowerShell-variabler i den aktuella konsolen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-113">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="22fd9-114">PowerShell- **variabeln** provider stöder variabler som PowerShell skapar, inklusive automatiska variabler, inställningar för variabler och variabler som du skapar.</span><span class="sxs-lookup"><span data-stu-id="22fd9-114">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="22fd9-115">**Variabeln** Drive är en planad namnrymd som bara innehåller de variabla objekten.</span><span class="sxs-lookup"><span data-stu-id="22fd9-115">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="22fd9-116">Variablerna har inga underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="22fd9-116">The variables have no child items.</span></span>

<span data-ttu-id="22fd9-117">**Variabeln** provider stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="22fd9-117">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="22fd9-118">Get-location</span><span class="sxs-lookup"><span data-stu-id="22fd9-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="22fd9-119">Ange plats</span><span class="sxs-lookup"><span data-stu-id="22fd9-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="22fd9-120">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="22fd9-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="22fd9-121">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="22fd9-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="22fd9-122">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="22fd9-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="22fd9-123">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="22fd9-123">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="22fd9-124">PowerShell innehåller också en uppsättning cmdlets som utformats särskilt för att visa och ändra variabler.</span><span class="sxs-lookup"><span data-stu-id="22fd9-124">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="22fd9-125">När du använder **variabel** -cmdletar behöver du inte ange `Variable:` enheten i namnet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-125">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="22fd9-126">Den här artikeln beskriver inte hur du arbetar med **variabel** -cmdletar.</span><span class="sxs-lookup"><span data-stu-id="22fd9-126">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="22fd9-127">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="22fd9-127">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="22fd9-128">Ny variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-128">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="22fd9-129">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="22fd9-129">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="22fd9-130">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-130">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="22fd9-131">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="22fd9-131">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="22fd9-132">Du kan också använda PowerShell Expression parser för att skapa, Visa och ändra värdena för variabler utan att använda cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="22fd9-132">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="22fd9-133">När du arbetar med variabler direkt använder du ett dollar tecken ( `$` ) för att identifiera namnet som en variabel och tilldelnings operatorn ( `=` ) för att upprätta och ändra värdet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-133">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="22fd9-134">Till exempel `$p = Get-Process` skapar `p` variabeln och lagrar resultatet av ett `Get-Process` kommando i den.</span><span class="sxs-lookup"><span data-stu-id="22fd9-134">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="22fd9-135">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="22fd9-135">Types exposed by this provider</span></span>

<span data-ttu-id="22fd9-136">Variabler kan vara en av flera olika typer.</span><span class="sxs-lookup"><span data-stu-id="22fd9-136">Variables can be one of several different types.</span></span> <span data-ttu-id="22fd9-137">De flesta variabler är instanser av `PSVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-137">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="22fd9-138">Andra variabler och deras typer visas nedan.</span><span class="sxs-lookup"><span data-stu-id="22fd9-138">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="22fd9-139">`?`Variabeln är en instans av `QuestionMarkVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-139">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="22fd9-140">`null`Variabeln är en instans av `NullVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-140">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="22fd9-141">Variablerna för maximalt antal är instanser av `SessionStateCapacityVariable` klassen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-141">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="22fd9-142">`LocalVariable` instanser innehåller information om aktuell körning, till exempel:</span><span class="sxs-lookup"><span data-stu-id="22fd9-142">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="22fd9-143">Navigera mellan variabla enheter</span><span class="sxs-lookup"><span data-stu-id="22fd9-143">Navigating the Variable drives</span></span>

<span data-ttu-id="22fd9-144">**Variabeln** Provider visar data lagret i `Variable:` enheten.</span><span class="sxs-lookup"><span data-stu-id="22fd9-144">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="22fd9-145">Om du vill arbeta med variabler kan du ändra din plats till `Variable:` enheten ( `Set-Location Variable:` ) eller så kan du arbeta från en annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-145">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="22fd9-146">Om du vill referera till en variabel från en annan plats använder du enhets namnet ( `Variable:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-146">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="22fd9-147">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="22fd9-147">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="22fd9-148">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="22fd9-148">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="22fd9-149">Du kan också arbeta med den **variabla** providern från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="22fd9-149">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="22fd9-150">Om du vill referera till en variabel från en annan plats använder du enhets namnet `Variable:` i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-150">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="22fd9-151">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="22fd9-151">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="22fd9-152">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="22fd9-152">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="22fd9-153">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="22fd9-153">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="22fd9-154">Visar värdet för variabler</span><span class="sxs-lookup"><span data-stu-id="22fd9-154">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="22fd9-155">Hämta alla variabler i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="22fd9-155">Get all variables in the current session</span></span>

<span data-ttu-id="22fd9-156">Det här kommandot hämtar listan över alla variabler och deras värden i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-156">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="22fd9-157">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-157">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="22fd9-158">Hämta en variabel med dess Provider-sökväg</span><span class="sxs-lookup"><span data-stu-id="22fd9-158">Get a variable using its provider path</span></span>

<span data-ttu-id="22fd9-159">Det här kommandot hämtar ett variabel värde med hjälp av dess Provider-sökväg som föregås av dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="22fd9-159">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="22fd9-160">Detta har samma resultat som när du reparerar variabelns namn med dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="22fd9-160">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="22fd9-161">Hämta variabler med jokertecken</span><span class="sxs-lookup"><span data-stu-id="22fd9-161">Get variables using wildcards</span></span>

<span data-ttu-id="22fd9-162">Det här kommandot hämtar variablerna med namn som börjar med "Max".</span><span class="sxs-lookup"><span data-stu-id="22fd9-162">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="22fd9-163">Du kan använda det här kommandot från valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-163">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="22fd9-164">Hämta värdet för?</span><span class="sxs-lookup"><span data-stu-id="22fd9-164">Get the value of the ?</span></span> <span data-ttu-id="22fd9-165">variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-165">variable</span></span>

<span data-ttu-id="22fd9-166">Det här kommandot använder `-LiteralPath` parametern för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) för att hämta värdet för `?` variabeln i `Variable:` enheten.</span><span class="sxs-lookup"><span data-stu-id="22fd9-166">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="22fd9-167">`?`Är ett jokertecken i sökvägar, men `Get-ChildItem` försöker inte matcha jokertecken i värdena för `-LiteralPath` parametern.</span><span class="sxs-lookup"><span data-stu-id="22fd9-167">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="22fd9-168">Hämta ReadOnly och konstanta variabler</span><span class="sxs-lookup"><span data-stu-id="22fd9-168">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="22fd9-169">Det här kommandot hämtar de variabler som har värdet `ReadOnly` eller `Constant` för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="22fd9-169">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="22fd9-170">Skapa variabler</span><span class="sxs-lookup"><span data-stu-id="22fd9-170">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="22fd9-171">Skapa en ny variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-171">Create a new variable</span></span>

<span data-ttu-id="22fd9-172">Det här kommandot skapar `services` variabeln och lagrar resultatet av ett `Get-Service` kommando i det.</span><span class="sxs-lookup"><span data-stu-id="22fd9-172">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="22fd9-173">Eftersom den aktuella platsen finns i `Variable:` enheten är värdet för `-Path` parametern en punkt ( `.` ) som representerar den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-173">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="22fd9-174">Parenteserna runt `Get-Service` kommandot ser till att kommandot utförs innan variabeln skapas.</span><span class="sxs-lookup"><span data-stu-id="22fd9-174">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="22fd9-175">Utan parenteser är värdet för den nya variabeln en "Get-service"-sträng.</span><span class="sxs-lookup"><span data-stu-id="22fd9-175">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="22fd9-176">Skapa en variabel med en absolut sökväg</span><span class="sxs-lookup"><span data-stu-id="22fd9-176">Create a variable using an absolute path</span></span>

<span data-ttu-id="22fd9-177">Det här kommandot skapar en `services` variabel och lagrar resultatet av ett `Get-Service` kommando i det.</span><span class="sxs-lookup"><span data-stu-id="22fd9-177">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="22fd9-178">Om du vill skapa en variabel utan värde utelämnar du tilldelnings operatorn.</span><span class="sxs-lookup"><span data-stu-id="22fd9-178">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="22fd9-179">Ändra variabler</span><span class="sxs-lookup"><span data-stu-id="22fd9-179">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="22fd9-180">Byta namn på en variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-180">Rename a variable</span></span>

<span data-ttu-id="22fd9-181">Det här kommandot använder `Rename-Item` cmdleten för att ändra namnet på `a` variabeln till `processes` .</span><span class="sxs-lookup"><span data-stu-id="22fd9-181">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="22fd9-182">Ändra värdet för en variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-182">Change the value of a variable</span></span>

<span data-ttu-id="22fd9-183">Det här kommandot använder `Set-Item` cmdleten för att ändra värdet för `ErrorActionPreference` variabeln till "stoppa".</span><span class="sxs-lookup"><span data-stu-id="22fd9-183">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="22fd9-184">Kopiera en variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-184">Copy a variable</span></span>

<span data-ttu-id="22fd9-185">Det här kommandot använder `Copy-Item` cmdleten för att kopiera `processes` variabeln till `old_processes` .</span><span class="sxs-lookup"><span data-stu-id="22fd9-185">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="22fd9-186">Detta skapar en ny variabel med namnet `old_processes` som har samma värde som `processes` variabeln.</span><span class="sxs-lookup"><span data-stu-id="22fd9-186">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="22fd9-187">Ta bort en variabel</span><span class="sxs-lookup"><span data-stu-id="22fd9-187">Delete a variable</span></span>

<span data-ttu-id="22fd9-188">Det här kommandot tar bort `serv` variabeln från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="22fd9-188">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="22fd9-189">Du kan använda det här kommandot i valfri PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-189">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="22fd9-190">Ta bort variabler med parametern-Force</span><span class="sxs-lookup"><span data-stu-id="22fd9-190">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="22fd9-191">Det här kommandot tar bort alla variabler från den aktuella sessionen, förutom variabler vars **alternativ** -egenskap har värdet `Constant` .</span><span class="sxs-lookup"><span data-stu-id="22fd9-191">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="22fd9-192">Utan `-Force` parametern tar kommandot inte bort variabler vars **alternativ** egenskap har värdet `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="22fd9-192">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="22fd9-193">Ange värdet för en variabel till NULL</span><span class="sxs-lookup"><span data-stu-id="22fd9-193">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="22fd9-194">Det här kommandot använder `Clear-Item` cmdleten för att ändra värdet för `processes` variabeln till null.</span><span class="sxs-lookup"><span data-stu-id="22fd9-194">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="22fd9-195">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="22fd9-195">Using the pipeline</span></span>

<span data-ttu-id="22fd9-196">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="22fd9-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="22fd9-197">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="22fd9-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="22fd9-198">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="22fd9-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="22fd9-199">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="22fd9-199">Getting help</span></span>

<span data-ttu-id="22fd9-200">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="22fd9-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="22fd9-201">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="22fd9-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="22fd9-202">Se även</span><span class="sxs-lookup"><span data-stu-id="22fd9-202">See also</span></span>

[<span data-ttu-id="22fd9-203">about_Variables</span><span class="sxs-lookup"><span data-stu-id="22fd9-203">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="22fd9-204">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="22fd9-204">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="22fd9-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="22fd9-205">about_Providers</span></span>](../About/about_Providers.md)
