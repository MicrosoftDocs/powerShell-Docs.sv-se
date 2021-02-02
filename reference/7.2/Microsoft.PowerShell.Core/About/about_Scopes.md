---
description: Förklarar begreppet omfång i PowerShell och visar hur du anger och ändrar elementets omfattning.
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: c9439412ab80eee4cedc1265a3927a274547d409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710962"
---
# <a name="about-scopes"></a><span data-ttu-id="2ef99-103">Om omfång</span><span class="sxs-lookup"><span data-stu-id="2ef99-103">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="2ef99-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ef99-104">Short description</span></span>
<span data-ttu-id="2ef99-105">Förklarar begreppet omfång i PowerShell och visar hur du anger och ändrar elementets omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-105">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="2ef99-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ef99-106">Long description</span></span>

<span data-ttu-id="2ef99-107">PowerShell skyddar åtkomsten till variabler, alias, funktioner och PowerShell-enheter (PSDrives) genom att begränsa var de kan läsas och ändras.</span><span class="sxs-lookup"><span data-stu-id="2ef99-107">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="2ef99-108">I PowerShell används omfattnings regler för att se till att du inte oavsiktligt ändrar ett objekt som inte ska ändras.</span><span class="sxs-lookup"><span data-stu-id="2ef99-108">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="2ef99-109">Följande är de grundläggande reglerna för omfattning:</span><span class="sxs-lookup"><span data-stu-id="2ef99-109">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="2ef99-110">Omfattningar kan kapslas.</span><span class="sxs-lookup"><span data-stu-id="2ef99-110">Scopes may nest.</span></span> <span data-ttu-id="2ef99-111">En yttre omfattning kallas för en överordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-111">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="2ef99-112">Alla kapslade omfång är underordnade omfång för den överordnade.</span><span class="sxs-lookup"><span data-stu-id="2ef99-112">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="2ef99-113">Ett objekt visas i den omfattning där det skapades och i alla underordnade omfattningar, om du inte uttryckligen gör det privat.</span><span class="sxs-lookup"><span data-stu-id="2ef99-113">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="2ef99-114">Du kan placera variabler, alias, funktioner eller PowerShell-enheter i ett eller flera omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-114">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="2ef99-115">Ett objekt som du har skapat i ett omfång kan bara ändras i det omfång som det skapades i, såvida du inte uttryckligen anger ett annat omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-115">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="2ef99-116">Om du skapar ett objekt i ett omfång och objektet delar sitt namn med ett objekt i ett annat omfång, kan det ursprungliga objektet vara dolt under det nya objektet, men det åsidosätts eller ändras inte.</span><span class="sxs-lookup"><span data-stu-id="2ef99-116">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="2ef99-117">PowerShell-scope</span><span class="sxs-lookup"><span data-stu-id="2ef99-117">PowerShell Scopes</span></span>

<span data-ttu-id="2ef99-118">PowerShell stöder följande omfång:</span><span class="sxs-lookup"><span data-stu-id="2ef99-118">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="2ef99-119">Global: det omfång som aktive ras när PowerShell startas eller när du skapar en ny session eller körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="2ef99-119">Global: The scope that is in effect when PowerShell starts or when you create a new session or runspace.</span></span> <span data-ttu-id="2ef99-120">Variabler och funktioner som förekommer när PowerShell startar har skapats i det globala omfånget, till exempel automatiska variabler och variabler.</span><span class="sxs-lookup"><span data-stu-id="2ef99-120">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="2ef99-121">Variablerna, aliasen och funktionerna i dina PowerShell-profiler skapas också i det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-121">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span> <span data-ttu-id="2ef99-122">Det globala omfånget är det överordnade rot omfånget i en session.</span><span class="sxs-lookup"><span data-stu-id="2ef99-122">The global scope is the root parent scope in a session.</span></span>

- <span data-ttu-id="2ef99-123">Lokal: det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-123">Local: The current scope.</span></span> <span data-ttu-id="2ef99-124">Det lokala omfånget kan vara det globala omfånget eller andra omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-124">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="2ef99-125">Skript: den omfattning som skapas när en skript fil körs.</span><span class="sxs-lookup"><span data-stu-id="2ef99-125">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="2ef99-126">Endast kommandona i skriptet körs i skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-126">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="2ef99-127">I kommandona i ett skript är skript omfånget det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-127">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="2ef99-128">**Private** är inte ett omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-128">**Private** is not a scope.</span></span> <span data-ttu-id="2ef99-129">Det är ett [alternativ](#private-option) som ändrar synligheten för ett objekt utanför omfånget där objektet definieras.</span><span class="sxs-lookup"><span data-stu-id="2ef99-129">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="2ef99-130">Överordnad och underordnad omfattning</span><span class="sxs-lookup"><span data-stu-id="2ef99-130">Parent and Child Scopes</span></span>

<span data-ttu-id="2ef99-131">Du kan skapa ett nytt underordnat omfång genom att anropa ett skript eller en funktion.</span><span class="sxs-lookup"><span data-stu-id="2ef99-131">You can create a new child scope by calling a script or function.</span></span> <span data-ttu-id="2ef99-132">Det anropande omfånget är det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-132">The calling scope is the parent scope.</span></span> <span data-ttu-id="2ef99-133">Det anropade skriptet eller funktionen är underordnat omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-133">The called script or function is the child scope.</span></span>
<span data-ttu-id="2ef99-134">De funktioner eller skript som du anropar kan anropa andra funktioner, vilket skapar en hierarki med underordnade omfattningar vars rot omfång är global omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-134">The functions or scripts you call may call other functions, creating a hierarchy of child scopes whose root scope is the global scope.</span></span>

<span data-ttu-id="2ef99-135">Om du inte uttryckligen gör objekten privat är objekten i det överordnade omfånget tillgängliga för det underordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-135">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="2ef99-136">Objekt som du skapar och ändrar i det underordnade omfånget påverkar dock inte det överordnade omfånget, såvida du inte uttryckligen anger omfånget när du skapar objekten.</span><span class="sxs-lookup"><span data-stu-id="2ef99-136">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

> [!NOTE]
> <span data-ttu-id="2ef99-137">Funktioner från en modul körs inte i ett underordnat omfång för det anropande omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-137">Functions from a module do not run in a child scope of the calling scope.</span></span>
> <span data-ttu-id="2ef99-138">Moduler har sitt eget sessionstillstånd som är länkat till det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-138">Modules have their own session state that is linked to the global scope.</span></span>
> <span data-ttu-id="2ef99-139">All modul kod körs i en modul-bestämd hierarki med omfattningar som har sitt eget rot omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-139">All module code runs in a module-specific hierarchy of scopes that has its own root scope.</span></span>

## <a name="inheritance"></a><span data-ttu-id="2ef99-140">Arv</span><span class="sxs-lookup"><span data-stu-id="2ef99-140">Inheritance</span></span>

<span data-ttu-id="2ef99-141">En underordnad omfattning ärver inte variabler, alias och funktioner från det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-141">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="2ef99-142">Om ett objekt är privat kan det underordnade omfånget Visa objekten i det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-142">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="2ef99-143">Och kan ändra objekten genom att uttryckligen ange det överordnade omfånget, men objekten ingår inte i det underordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-143">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="2ef99-144">En underordnad omfattning skapas dock med en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="2ef99-144">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="2ef99-145">Normalt innehåller den alla alias som har alternativet **AllScope** .</span><span class="sxs-lookup"><span data-stu-id="2ef99-145">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="2ef99-146">Det här alternativet beskrivs längre fram i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-146">This option is discussed later in this article.</span></span> <span data-ttu-id="2ef99-147">Den innehåller alla variabler som har alternativet **AllScope** , plus några automatiska variabler.</span><span class="sxs-lookup"><span data-stu-id="2ef99-147">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="2ef99-148">Om du vill hitta objekt i ett visst omfång använder du omfattnings parametern för `Get-Variable` eller `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-148">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="2ef99-149">Om du till exempel vill hämta alla variabler i det lokala omfånget skriver du:</span><span class="sxs-lookup"><span data-stu-id="2ef99-149">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="2ef99-150">Om du vill hämta alla variabler i det globala omfånget skriver du:</span><span class="sxs-lookup"><span data-stu-id="2ef99-150">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="2ef99-151">Omfångs modifierare</span><span class="sxs-lookup"><span data-stu-id="2ef99-151">Scope Modifiers</span></span>

<span data-ttu-id="2ef99-152">En variabel, ett alias eller ett funktions namn kan innehålla någon av följande valfria omfångs modifierare:</span><span class="sxs-lookup"><span data-stu-id="2ef99-152">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="2ef99-153">`global:` -Anger att namnet finns i det **globala** omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-153">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="2ef99-154">`local:` -Anger att namnet finns i det **lokala** omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-154">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="2ef99-155">Det aktuella omfånget är alltid det **lokala** omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-155">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="2ef99-156">`private:` -Anger att namnet är **privat** och bara visas för det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-156">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="2ef99-157">`script:` -Anger att namnet finns i **skript** omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-157">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="2ef99-158">**Skript** omfattningen är den närmast överordnade skript filens omfattning eller **Global** om det inte finns någon närmast överordnade skript fil.</span><span class="sxs-lookup"><span data-stu-id="2ef99-158">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="2ef99-159">`using:` – Används för att komma åt variabler som definierats i ett annat omfång samtidigt som skript körs via cmdletar som `Start-Job` och `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-159">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="2ef99-160">`workflow:` -Anger att namnet finns i ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="2ef99-160">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="2ef99-161">Obs! arbets flöden stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="2ef99-161">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="2ef99-162">`<variable-namespace>` – En modifierare som skapats av en PowerShell PSDrive-Provider.</span><span class="sxs-lookup"><span data-stu-id="2ef99-162">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="2ef99-163">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ef99-163">For example:</span></span>

  |  <span data-ttu-id="2ef99-164">Namnområde</span><span class="sxs-lookup"><span data-stu-id="2ef99-164">Namespace</span></span>  |                    <span data-ttu-id="2ef99-165">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ef99-165">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="2ef99-166">Alias som definierats i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="2ef99-166">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="2ef99-167">Miljövariabler som definierats i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="2ef99-167">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="2ef99-168">Funktioner som definierats i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="2ef99-168">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="2ef99-169">Variabler som definierats i det aktuella omfånget</span><span class="sxs-lookup"><span data-stu-id="2ef99-169">Variables defined in the current scope</span></span>             |

<span data-ttu-id="2ef99-170">Standard omfånget för skript är skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-170">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="2ef99-171">Standard omfånget för functions och alias är det lokala omfånget, även om de är definierade i ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ef99-171">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="2ef99-172">Använda omfångs modifierare</span><span class="sxs-lookup"><span data-stu-id="2ef99-172">Using scope modifiers</span></span>

<span data-ttu-id="2ef99-173">Om du vill ange omfånget för en ny variabel, ett alias eller en funktion använder du en omfattnings modifierare.</span><span class="sxs-lookup"><span data-stu-id="2ef99-173">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="2ef99-174">Syntaxen för en omfattnings modifierare i en variabel är:</span><span class="sxs-lookup"><span data-stu-id="2ef99-174">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="2ef99-175">Syntaxen för en omfattnings modifierare i en funktion är:</span><span class="sxs-lookup"><span data-stu-id="2ef99-175">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="2ef99-176">Följande kommando, som inte använder en omfångs modifierare, skapar en variabel i den aktuella eller **lokala** omfattningen:</span><span class="sxs-lookup"><span data-stu-id="2ef99-176">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="2ef99-177">Om du vill skapa samma variabel i det **globala** omfånget använder du omfångs `global:` modifieraren:</span><span class="sxs-lookup"><span data-stu-id="2ef99-177">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="2ef99-178">Om du vill skapa samma variabel i **skript** omfånget använder du `script:` omfångs modifieraren:</span><span class="sxs-lookup"><span data-stu-id="2ef99-178">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="2ef99-179">Du kan också använda en omfattnings modifierare med Functions.</span><span class="sxs-lookup"><span data-stu-id="2ef99-179">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="2ef99-180">Följande funktions definition skapar en funktion i det **globala** omfånget:</span><span class="sxs-lookup"><span data-stu-id="2ef99-180">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="2ef99-181">Du kan också använda omfattnings modifierare för att referera till en variabel i ett annat omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-181">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="2ef99-182">Följande kommando refererar till `$test` variabeln, först i det lokala området och sedan i det globala omfånget:</span><span class="sxs-lookup"><span data-stu-id="2ef99-182">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="2ef99-183">`Using:`Omfångs modifieraren</span><span class="sxs-lookup"><span data-stu-id="2ef99-183">The `Using:` scope modifier</span></span>

<span data-ttu-id="2ef99-184">Att använda är en särskild omfattnings modifierare som identifierar en lokal variabel i ett fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="2ef99-184">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="2ef99-185">Utan modifierare förväntar PowerShell variabler i fjärrkommandon som ska definieras i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-185">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="2ef99-186">`Using`Omfångs modifieraren introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ef99-186">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="2ef99-187">För alla skript eller kommandon som körs utanför sessionen behöver du `Using` omfångs modifieraren för att bädda in variabel värden från scopet för den anropande sessionen, så att det går att komma åt dem.</span><span class="sxs-lookup"><span data-stu-id="2ef99-187">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="2ef99-188">`Using`Omfångs modifieraren stöds i följande kontexter:</span><span class="sxs-lookup"><span data-stu-id="2ef99-188">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="2ef99-189">Fjärrkörning av kommandon, startade med `Invoke-Command` användning **av ComputerName**, **hostname**, **SSHConnection** eller **sessionstillstånd** (fjärrsession)</span><span class="sxs-lookup"><span data-stu-id="2ef99-189">Remotely executed commands, started with `Invoke-Command` using the **ComputerName**, **HostName**, **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="2ef99-190">Bakgrunds jobb, startade med `Start-Job` (out-of-process-session)</span><span class="sxs-lookup"><span data-stu-id="2ef99-190">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="2ef99-191">Tråd jobb, startade via `Start-ThreadJob` eller `ForEach-Object -Parallel` (separat trådpool)</span><span class="sxs-lookup"><span data-stu-id="2ef99-191">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="2ef99-192">Beroende på sammanhanget är inbäddade variabel värden antingen oberoende kopior av data i anroparens omfång eller referenser till den.</span><span class="sxs-lookup"><span data-stu-id="2ef99-192">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="2ef99-193">I fjärranslutna och inaktiva sessioner är de alltid oberoende kopior.</span><span class="sxs-lookup"><span data-stu-id="2ef99-193">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="2ef99-194">Mer information finns i [about_Remote_Variables](about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="2ef99-194">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="2ef99-195">De skickas som referens i Thread-sessioner.</span><span class="sxs-lookup"><span data-stu-id="2ef99-195">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="2ef99-196">Det innebär att det är möjligt att ändra variabler för anrops omfång i en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="2ef99-196">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="2ef99-197">För att på ett säkert sätt ändra variabler krävs Thread-synkronisering.</span><span class="sxs-lookup"><span data-stu-id="2ef99-197">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="2ef99-198">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="2ef99-198">For more information see:</span></span>

- [<span data-ttu-id="2ef99-199">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="2ef99-199">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)
- [<span data-ttu-id="2ef99-200">-Objekt</span><span class="sxs-lookup"><span data-stu-id="2ef99-200">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="2ef99-201">Serialisering av variabel värden</span><span class="sxs-lookup"><span data-stu-id="2ef99-201">Serialization of variable values</span></span>

<span data-ttu-id="2ef99-202">Fjärrkörning av kommandon och bakgrunds jobb körs utanför processen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-202">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="2ef99-203">Sessioner utanför processen använder XML-baserad serialisering och deserialisering för att göra värdena för variabler tillgängliga över process gränserna.</span><span class="sxs-lookup"><span data-stu-id="2ef99-203">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="2ef99-204">Serialiserings processen konverterar objekt till en **PSObject** som innehåller de ursprungliga objekt egenskaperna, men inte dess metoder.</span><span class="sxs-lookup"><span data-stu-id="2ef99-204">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="2ef99-205">För en begränsad uppsättning typer, deserialiserar objekt tillbaka till den ursprungliga typen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-205">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="2ef99-206">Det dehydratiserade objektet är en kopia av den ursprungliga objekt instansen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-206">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="2ef99-207">Den har typ egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="2ef99-207">It has the type properties and methods.</span></span> <span data-ttu-id="2ef99-208">För enkla typer, till exempel **system. version**, är kopian exakt.</span><span class="sxs-lookup"><span data-stu-id="2ef99-208">For simple types, such as **System.Version**, the copy is exact.</span></span> <span data-ttu-id="2ef99-209">För komplexa typer är kopian perfekt.</span><span class="sxs-lookup"><span data-stu-id="2ef99-209">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="2ef99-210">Till exempel innehåller inte rehydratiserade certifikat objekt den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-210">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="2ef99-211">Instanser av alla andra typer är **PSObject** -instanser.</span><span class="sxs-lookup"><span data-stu-id="2ef99-211">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="2ef99-212">Egenskapen **PSTypeNames** innehåller det ursprungliga typ namnet som föregås av **deserialiserad**, till exempel **Deserialized.System. Data. DataTable**</span><span class="sxs-lookup"><span data-stu-id="2ef99-212">The **PSTypeNames** property contains the original type name prefixed with **Deserialized**, for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="2ef99-213">Alternativet AllScope</span><span class="sxs-lookup"><span data-stu-id="2ef99-213">The AllScope Option</span></span>

<span data-ttu-id="2ef99-214">Variabler och alias har en **alternativ** egenskap som kan ha värdet **AllScope**.</span><span class="sxs-lookup"><span data-stu-id="2ef99-214">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="2ef99-215">Objekt som har egenskapen **AllScope** blir en del av alla underordnade omfång som du skapar, även om de inte retroaktivt ärvs av överordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-215">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="2ef99-216">Ett objekt som har egenskapen **AllScope** visas i det underordnade omfånget och ingår i det omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-216">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="2ef99-217">Ändringar i objektet i alla omfattningar påverkar alla omfattningar där variabeln definieras.</span><span class="sxs-lookup"><span data-stu-id="2ef99-217">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="2ef99-218">Hantera omfattning</span><span class="sxs-lookup"><span data-stu-id="2ef99-218">Managing Scope</span></span>

<span data-ttu-id="2ef99-219">Flera cmdlets har en **omfattnings** parameter som låter dig hämta eller ange (skapa och ändra) objekt i ett visst omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-219">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="2ef99-220">Använd följande kommando för att hitta alla cmdletar i sessionen som har en **omfattnings** parameter:</span><span class="sxs-lookup"><span data-stu-id="2ef99-220">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="2ef99-221">Om du vill hitta variablerna som är synliga i ett visst omfång använder du- `Scope` parametern för `Get-Variable` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-221">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="2ef99-222">De synliga variablerna inkluderar globala variabler, variabler i det överordnade omfånget och variabler i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-222">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="2ef99-223">Följande kommando hämtar till exempel variablerna som visas i det lokala omfånget:</span><span class="sxs-lookup"><span data-stu-id="2ef99-223">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="2ef99-224">Om du vill skapa en variabel i ett visst omfång använder du en omfångs modifierare eller **omfattnings** parametern för `Set-Variable` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-224">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="2ef99-225">Följande kommando skapar en variabel i det globala omfånget:</span><span class="sxs-lookup"><span data-stu-id="2ef99-225">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="2ef99-226">Du kan också använda omfattnings parametern för `New-Alias` `Set-Alias` cmdletarna, eller `Get-Alias` för att ange omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-226">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="2ef99-227">Följande kommando skapar ett alias i det globala omfånget:</span><span class="sxs-lookup"><span data-stu-id="2ef99-227">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="2ef99-228">Om du vill hämta funktionerna i ett visst omfång använder `Get-Item` du cmdleten när du befinner dig i omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-228">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="2ef99-229">`Get-Item`Cmdleten har ingen **omfattnings** parameter.</span><span class="sxs-lookup"><span data-stu-id="2ef99-229">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="2ef99-230">För de cmdletar som använder **omfattnings** parametern kan du också referera till omfång efter nummer.</span><span class="sxs-lookup"><span data-stu-id="2ef99-230">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="2ef99-231">Talet beskriver den relativa positionen för ett omfång till ett annat.</span><span class="sxs-lookup"><span data-stu-id="2ef99-231">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="2ef99-232">Omfattning 0 representerar den aktuella eller lokala omfattningen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-232">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="2ef99-233">Område 1 anger den direkta överordnade omfattningen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-233">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="2ef99-234">Omfattning 2 visar överordnad för det överordnade omfånget och så vidare.</span><span class="sxs-lookup"><span data-stu-id="2ef99-234">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="2ef99-235">Numrerade omfattningar är användbara om du har skapat många rekursiva omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-235">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="2ef99-236">Använda punkt käll notation med omfång</span><span class="sxs-lookup"><span data-stu-id="2ef99-236">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="2ef99-237">Skript och funktioner följer alla regler för omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-237">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="2ef99-238">Du skapar dem i ett visst omfång, och de påverkar bara det omfånget om du inte använder en cmdlet-parameter eller en omfångs modifierare för att ändra omfattningen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-238">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="2ef99-239">Men du kan lägga till ett skript eller en funktion i det aktuella omfånget med hjälp av punkt käll notation.</span><span class="sxs-lookup"><span data-stu-id="2ef99-239">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="2ef99-240">När ett skript körs i det aktuella omfånget är alla funktioner, alias och variabler som skriptet skapar tillgängliga i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-240">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="2ef99-241">Om du vill lägga till en funktion i det aktuella omfånget skriver du en punkt (.) och ett blank steg före sökvägen och namnet på funktionen i funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-241">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="2ef99-242">Om du till exempel vill köra Sample.ps1-skriptet från C:\Scripts-katalogen i skript omfånget (standard för skript) använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="2ef99-242">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="2ef99-243">Om du vill köra Sample.ps1 skriptet i det lokala omfånget använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="2ef99-243">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="2ef99-244">När du använder anrops operatorn (&) för att köra en funktion eller ett skript, läggs den inte till i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-244">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="2ef99-245">I följande exempel används anrops operatorn:</span><span class="sxs-lookup"><span data-stu-id="2ef99-245">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="2ef99-246">Du kan läsa mer om anrops operatorn i [about_operators](about_operators.md).</span><span class="sxs-lookup"><span data-stu-id="2ef99-246">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="2ef99-247">Alla alias, funktioner eller variabler som Sample.ps1 skriptet skapar är inte tillgängliga i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-247">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="2ef99-248">Begränsa utan omfång</span><span class="sxs-lookup"><span data-stu-id="2ef99-248">Restricting Without Scope</span></span>

<span data-ttu-id="2ef99-249">Några PowerShell-begrepp liknar omfång eller interagerar med omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-249">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="2ef99-250">Dessa begrepp kan vara förvirrande med omfång eller beteende för omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-250">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="2ef99-251">Sessioner, moduler och kapslade prompter är fristående miljöer, men de är inte underordnade omfång av det globala omfånget i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-251">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="2ef99-252">Sessioner</span><span class="sxs-lookup"><span data-stu-id="2ef99-252">Sessions</span></span>

<span data-ttu-id="2ef99-253">En session är en miljö där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="2ef99-253">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="2ef99-254">När du skapar en-session på en fjärrdator upprättar PowerShell en permanent anslutning till fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="2ef99-254">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="2ef99-255">Med den permanenta anslutningen kan du använda sessionen för flera relaterade kommandon.</span><span class="sxs-lookup"><span data-stu-id="2ef99-255">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="2ef99-256">Eftersom en session är en innesluten miljö har den ett eget omfång, men en session är inte ett underordnat omfång för den session där den skapades.</span><span class="sxs-lookup"><span data-stu-id="2ef99-256">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="2ef99-257">Sessionen börjar med en egen global omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-257">The session starts with its own global scope.</span></span> <span data-ttu-id="2ef99-258">Det här omfånget är oberoende av sessionens globala omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-258">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="2ef99-259">Du kan skapa underordnade scope i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-259">You can create child scopes in the session.</span></span> <span data-ttu-id="2ef99-260">Du kan till exempel köra ett skript för att skapa en underordnad omfattning i en session.</span><span class="sxs-lookup"><span data-stu-id="2ef99-260">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="2ef99-261">Moduler</span><span class="sxs-lookup"><span data-stu-id="2ef99-261">Modules</span></span>

<span data-ttu-id="2ef99-262">Du kan använda en PowerShell-modul för att dela och leverera PowerShell-verktyg.</span><span class="sxs-lookup"><span data-stu-id="2ef99-262">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="2ef99-263">En modul är en enhet som kan innehålla cmdlets, skript, funktioner, variabler, alias och andra användbara objekt.</span><span class="sxs-lookup"><span data-stu-id="2ef99-263">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="2ef99-264">Om inget annat uttryckligen anges går det inte att nå objekten i en modul utanför modulen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-264">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="2ef99-265">Därför kan du lägga till modulen i din session och använda de offentliga objekten utan att oroa dig för att de andra objekten kan åsidosätta cmdlets, skript, funktioner och andra objekt i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-265">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="2ef99-266">Som standard läses moduler in i den högsta nivån för det aktuella _sessionstillståndet_ , inte det aktuella _omfånget_.</span><span class="sxs-lookup"><span data-stu-id="2ef99-266">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="2ef99-267">Det aktuella sessionstillståndet kan vara en sessionstillstånd eller det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-267">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="2ef99-268">Om du lägger till en modul i en session ändras inte omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-268">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="2ef99-269">Om du befinner dig i det globala omfånget läses moduler in i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-269">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="2ef99-270">Alla exporter placeras i globala tabeller.</span><span class="sxs-lookup"><span data-stu-id="2ef99-270">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="2ef99-271">Om du läser in module2 _inifrån Module1 läses_ module2 in i sessionstillståndet för Module1 inte det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-271">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="2ef99-272">Alla exporter från module2 placeras överst i Module1-sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-272">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="2ef99-273">Om du använder `Import-Module -Scope local` placeras exporten i det aktuella omfångs objektet i stället för på den översta nivån.</span><span class="sxs-lookup"><span data-stu-id="2ef99-273">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="2ef99-274">Om du är _i en modul_ och använder `Import-Module -Scope global` (eller `Import-Module -Global` ) för att läsa in en annan modul, läses den modulen och den exporteras till det globala sessionstillståndet i stället för modulens lokala sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="2ef99-274">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="2ef99-275">Den här funktionen har utformats för att skriva modul som manipulerar moduler.</span><span class="sxs-lookup"><span data-stu-id="2ef99-275">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="2ef99-276">**WindowsCompatibility** -modulen gör detta för att importera proxy-moduler till läget för den globala sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-276">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="2ef99-277">I sessionstillstånd har moduler sin egen omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-277">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="2ef99-278">Överväg följande modul `C:\temp\mod1.psm1` :</span><span class="sxs-lookup"><span data-stu-id="2ef99-278">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="2ef99-279">Nu skapar vi en global variabel `$a` , ger den ett värde och anropar funktionen **foo**.</span><span class="sxs-lookup"><span data-stu-id="2ef99-279">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="2ef99-280">Modulen deklarerar variabeln `$a` i modulen scope, och funktionen **foo** matar sedan ut värdet för variabeln i båda omfattningarna.</span><span class="sxs-lookup"><span data-stu-id="2ef99-280">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="2ef99-281">Kapslade prompter</span><span class="sxs-lookup"><span data-stu-id="2ef99-281">Nested Prompts</span></span>

<span data-ttu-id="2ef99-282">Kapslade prompter har inget eget omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-282">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="2ef99-283">När du anger en kapslad prompt är den kapslade prompten en del av miljön.</span><span class="sxs-lookup"><span data-stu-id="2ef99-283">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="2ef99-284">Men du är kvar inom det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-284">But, you remain within the local scope.</span></span>

<span data-ttu-id="2ef99-285">Skript har sin egen omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-285">Scripts do have their own scope.</span></span> <span data-ttu-id="2ef99-286">Om du felsöker ett skript och du når en Bryt punkt i skriptet, anger du skriptets omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-286">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="2ef99-287">Privat alternativ</span><span class="sxs-lookup"><span data-stu-id="2ef99-287">Private Option</span></span>

<span data-ttu-id="2ef99-288">Alias och variabler har en **alternativ** egenskap som kan ta värdet **privat**.</span><span class="sxs-lookup"><span data-stu-id="2ef99-288">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="2ef99-289">Objekt som har alternativet **privat** kan visas och ändras i det omfång som de skapas i, men de kan inte visas eller ändras utanför det omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-289">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="2ef99-290">Om du till exempel skapar en variabel som har ett privat alternativ i det globala omfånget och sedan kör ett skript, `Get-Variable` visar kommandon i skriptet inte den privata variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-290">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="2ef99-291">Om du använder den globala omfångs modifieraren i den här instansen visas inte den privata variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-291">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="2ef99-292">Du kan använda alternativ parametern för `New-Variable` `Set-Variable` cmdletarna,, `New-Alias` och `Set-Alias` för att ställa in värdet för alternativ egenskapen på privat.</span><span class="sxs-lookup"><span data-stu-id="2ef99-292">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="2ef99-293">Visibility (Sikt)</span><span class="sxs-lookup"><span data-stu-id="2ef99-293">Visibility</span></span>

<span data-ttu-id="2ef99-294">Egenskapen **visibility** för en variabel eller ett alias bestämmer om du kan se objektet utanför behållaren där det skapades.</span><span class="sxs-lookup"><span data-stu-id="2ef99-294">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="2ef99-295">En behållare kan vara en modul, ett skript eller en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="2ef99-295">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="2ef99-296">Synligheten är utformad för behållare på samma sätt som **alternativ** egenskapens **privata** värde är utformat för omfattningar.</span><span class="sxs-lookup"><span data-stu-id="2ef99-296">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="2ef99-297">Egenskapen **visibility** tar de **offentliga** och **privata** värdena.</span><span class="sxs-lookup"><span data-stu-id="2ef99-297">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="2ef99-298">Objekt som har privat synlighet kan endast visas och ändras i den behållare där de skapades.</span><span class="sxs-lookup"><span data-stu-id="2ef99-298">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="2ef99-299">Om behållaren läggs till eller importeras går det inte att visa eller ändra objekt som har privat synlighet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-299">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="2ef99-300">Eftersom synligheten är utformad för behållare fungerar den på olika sätt i ett omfång.</span><span class="sxs-lookup"><span data-stu-id="2ef99-300">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="2ef99-301">Om du skapar ett objekt som har privat synlighet i det globala omfånget kan du inte Visa eller ändra objektet i någon omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-301">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="2ef99-302">Om du försöker visa eller ändra värdet för en variabel som har privat synlighet, returnerar PowerShell ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="2ef99-302">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="2ef99-303">Du kan använda `New-Variable` `Set-Variable` cmdletarna och för att skapa en variabel som har privat synlighet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-303">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="2ef99-304">Exempel</span><span class="sxs-lookup"><span data-stu-id="2ef99-304">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="2ef99-305">Exempel 1: ändra bara ett variabel värde i ett skript</span><span class="sxs-lookup"><span data-stu-id="2ef99-305">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="2ef99-306">Följande kommando ändrar värdet för `$ConfirmPreference` variabeln i ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ef99-306">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="2ef99-307">Ändringen påverkar inte det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-307">The change does not affect the global scope.</span></span>

<span data-ttu-id="2ef99-308">För att visa värdet för `$ConfirmPreference` variabeln i det lokala omfånget använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="2ef99-308">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="2ef99-309">Skapa ett Scope.ps1-skript som innehåller följande kommandon:</span><span class="sxs-lookup"><span data-stu-id="2ef99-309">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="2ef99-310">Kör skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ef99-310">Run the script.</span></span> <span data-ttu-id="2ef99-311">Skriptet ändrar värdet för `$ConfirmPreference` variabeln och rapporterar värdet i skript omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-311">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="2ef99-312">Utdata bör likna följande utdata:</span><span class="sxs-lookup"><span data-stu-id="2ef99-312">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="2ef99-313">Testa sedan det aktuella värdet för `$ConfirmPreference` variabeln i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-313">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="2ef99-314">Det här exemplet visar att ändringar av värdet för en variabel i skript omfattningen inte påverkar variabelns värde i det överordnade omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-314">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="2ef99-315">Exempel 2: Visa ett variabel värde i olika omfång</span><span class="sxs-lookup"><span data-stu-id="2ef99-315">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="2ef99-316">Du kan använda omfångs modifierare för att visa värdet för en variabel i det lokala området och i en överordnad omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ef99-316">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="2ef99-317">Definiera först en `$test` variabel i det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-317">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="2ef99-318">Skapa sedan ett Sample.ps1-skript som definierar `$test` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-318">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="2ef99-319">I skriptet använder du en omfattnings modifierare för att referera till antingen den globala eller lokala versionen av `$test` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-319">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="2ef99-320">I Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="2ef99-320">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="2ef99-321">När du kör Sample.ps1 bör utdata likna följande utdata:</span><span class="sxs-lookup"><span data-stu-id="2ef99-321">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="2ef99-322">När skriptet har slutförts definieras bara det globala värdet för `$test` i sessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-322">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="2ef99-323">Exempel 3: ändra värdet för en variabel i ett överordnat område</span><span class="sxs-lookup"><span data-stu-id="2ef99-323">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="2ef99-324">Om du inte skyddar ett objekt med hjälp av alternativet privat eller någon annan metod, kan du Visa och ändra värdet för en variabel i ett överordnat område.</span><span class="sxs-lookup"><span data-stu-id="2ef99-324">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="2ef99-325">Definiera först en `$test` variabel i det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-325">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="2ef99-326">Skapa sedan ett Sample.ps1-skript som definierar `$test` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-326">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="2ef99-327">I skriptet använder du en omfattnings modifierare för att referera till antingen den globala eller lokala versionen av `$test` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ef99-327">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="2ef99-328">I Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="2ef99-328">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="2ef99-329">När skriptet har slutförts ändras det globala värdet för `$test` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-329">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="2ef99-330">Exempel 4: skapa en privat variabel</span><span class="sxs-lookup"><span data-stu-id="2ef99-330">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="2ef99-331">En privat variabel är en variabel som har en **alternativ** egenskap som har värdet *privat*.</span><span class="sxs-lookup"><span data-stu-id="2ef99-331">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="2ef99-332">*Privata* variabler ärvs av det underordnade omfånget, men de kan bara visas eller ändras i den omfattning som de skapades i.</span><span class="sxs-lookup"><span data-stu-id="2ef99-332">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="2ef99-333">Följande kommando skapar en privat variabel som kallas `$ptest` i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-333">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="2ef99-334">Du kan visa och ändra värdet för `$ptest` i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="2ef99-334">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="2ef99-335">Skapa sedan ett Sample.ps1-skript som innehåller följande kommandon.</span><span class="sxs-lookup"><span data-stu-id="2ef99-335">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="2ef99-336">Kommandot försöker visa och ändra värdet för `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="2ef99-336">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="2ef99-337">I Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="2ef99-337">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="2ef99-338">`$ptest`Variabeln är inte synlig i skript omfånget, utdata är tom.</span><span class="sxs-lookup"><span data-stu-id="2ef99-338">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="2ef99-339">Exempel 5: använda en lokal variabel i ett fjärran slutet kommando</span><span class="sxs-lookup"><span data-stu-id="2ef99-339">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="2ef99-340">För variabler i ett fjärrkommando som skapats i den lokala sessionen använder du `Using` omfångs modifieraren.</span><span class="sxs-lookup"><span data-stu-id="2ef99-340">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="2ef99-341">PowerShell förutsätter att variablerna i fjärrkommandon har skapats i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="2ef99-341">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="2ef99-342">Syntax:</span><span class="sxs-lookup"><span data-stu-id="2ef99-342">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="2ef99-343">Följande kommandon skapar till exempel en `$Cred` variabel i den lokala sessionen och använder sedan `$Cred` variabeln i ett fjärran slutet kommando:</span><span class="sxs-lookup"><span data-stu-id="2ef99-343">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="2ef99-344">Användnings området introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ef99-344">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="2ef99-345">I PowerShell 2,0, för att ange att en variabel har skapats i den lokala sessionen, använder du följande kommando format.</span><span class="sxs-lookup"><span data-stu-id="2ef99-345">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="2ef99-346">Se även</span><span class="sxs-lookup"><span data-stu-id="2ef99-346">See also</span></span>

[<span data-ttu-id="2ef99-347">about_Variables</span><span class="sxs-lookup"><span data-stu-id="2ef99-347">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="2ef99-348">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="2ef99-348">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="2ef99-349">about_Functions</span><span class="sxs-lookup"><span data-stu-id="2ef99-349">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="2ef99-350">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="2ef99-350">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="2ef99-351">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="2ef99-351">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)