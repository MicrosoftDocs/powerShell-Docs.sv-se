---
title: Allt du ville veta om ShouldProcess
description: ShouldProcess är en viktig funktion som ofta är påslagen. Parametrarna WhatIf och Confirm gör det enkelt att lägga till dina funktioner.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 4f11ad84f5c89423fe56cfe438ed3cb1587ce59e
ms.sourcegitcommit: be1df0bf757d734975a9aa021727608a396059ee
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616054"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="4e69e-104">Allt du ville veta om ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="4e69e-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="4e69e-105">PowerShell-funktioner har flera funktioner som avsevärt förbättrar hur användare interagerar med dem.</span><span class="sxs-lookup"><span data-stu-id="4e69e-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="4e69e-106">En viktig funktion som ofta förbises är `-WhatIf` och `-Confirm` stöder och det är enkelt att lägga till funktioner.</span><span class="sxs-lookup"><span data-stu-id="4e69e-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="4e69e-107">I den här artikeln går vi djupare till hur du implementerar den här funktionen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="4e69e-108">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] .</span><span class="sxs-lookup"><span data-stu-id="4e69e-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="4e69e-109">PowerShell-teamet tackar för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="4e69e-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="4e69e-110">Ta en titt på hans blogg på [PowerShellExplained.com][].</span><span class="sxs-lookup"><span data-stu-id="4e69e-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="4e69e-111">Det här är en enkel funktion som du kan aktivera i dina funktioner för att tillhandahålla ett säkerhets nät för de användare som behöver det.</span><span class="sxs-lookup"><span data-stu-id="4e69e-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="4e69e-112">Det finns inget scarier än att köra ett kommando som du vet kan vara farligt för första gången.</span><span class="sxs-lookup"><span data-stu-id="4e69e-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="4e69e-113">Alternativet att köra det med `-WhatIf` kan göra stor skillnad.</span><span class="sxs-lookup"><span data-stu-id="4e69e-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="4e69e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e69e-114">CommonParameters</span></span>

<span data-ttu-id="4e69e-115">Innan vi tittar på implementering av de här [vanliga parametrarna][]vill jag ta en titt på hur de används.</span><span class="sxs-lookup"><span data-stu-id="4e69e-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="4e69e-116">Använda-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e69e-116">Using -WhatIf</span></span>

<span data-ttu-id="4e69e-117">När ett kommando stöder `-WhatIf` parametern kan du se hur kommandot skulle ha gjort i stället för att göra ändringar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="4e69e-118">Det är ett bra sätt att testa effekten av ett kommando, särskilt innan du gör något destruktivt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="4e69e-119">Om kommandot implementeras korrekt `ShouldProcess` bör du Visa alla ändringar som har gjorts.</span><span class="sxs-lookup"><span data-stu-id="4e69e-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="4e69e-120">Här är ett exempel som använder jokertecken för att ta bort flera filer.</span><span class="sxs-lookup"><span data-stu-id="4e69e-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="4e69e-121">Använder-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e69e-121">Using -Confirm</span></span>

<span data-ttu-id="4e69e-122">Kommandon som stöder stöder `-WhatIf` också `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="4e69e-123">Det ger dig en chans att bekräfta en åtgärd innan du utför den.</span><span class="sxs-lookup"><span data-stu-id="4e69e-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4e69e-124">I det här fallet har du flera alternativ som gör att du kan fortsätta, hoppa över en ändring eller stoppa skriptet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="4e69e-125">I hjälp avsnittet beskrivs var och en av dessa alternativ som detta.</span><span class="sxs-lookup"><span data-stu-id="4e69e-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="4e69e-126">Lokalisering</span><span class="sxs-lookup"><span data-stu-id="4e69e-126">Localization</span></span>

<span data-ttu-id="4e69e-127">Den här prompten lokaliseras i PowerShell så att språket ändras baserat på operativ systemets språk.</span><span class="sxs-lookup"><span data-stu-id="4e69e-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="4e69e-128">Detta är en mer precis som PowerShell hanterar för dig.</span><span class="sxs-lookup"><span data-stu-id="4e69e-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="4e69e-129">Växla parametrar</span><span class="sxs-lookup"><span data-stu-id="4e69e-129">Switch parameters</span></span>

<span data-ttu-id="4e69e-130">Låt oss ta en stund att titta på olika sätt att skicka ett värde till en switch-parameter.</span><span class="sxs-lookup"><span data-stu-id="4e69e-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="4e69e-131">Det främsta skälet till att jag kallar det här är att du ofta vill skicka parameter värden till de funktioner som du anropar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="4e69e-132">Den första metoden är en speciell parameter-syntax som kan användas för alla parametrar, men du kan se den som används för växlings parametrar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="4e69e-133">Du anger ett kolon för att bifoga ett värde till parametern.</span><span class="sxs-lookup"><span data-stu-id="4e69e-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="4e69e-134">Du kan göra samma sak med en variabel.</span><span class="sxs-lookup"><span data-stu-id="4e69e-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="4e69e-135">Den andra metoden är att använda en hash-hash för att splat värdet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="4e69e-136">Om du är nybörjare på hash eller ihopbuntning har jag en annan artikel som täcker [allt du ville veta om hash][].</span><span class="sxs-lookup"><span data-stu-id="4e69e-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="4e69e-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="4e69e-137">SupportsShouldProcess</span></span>

<span data-ttu-id="4e69e-138">Det första steget för att aktivera `-WhatIf` och `-Confirm` stödja är att ange `SupportsShouldProcess` i `CmdletBinding` din funktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="4e69e-139">Genom `SupportsShouldProcess` att ange på det här sättet kan vi nu anropa vår funktion med `-WhatIf` (eller `-Confirm` ).</span><span class="sxs-lookup"><span data-stu-id="4e69e-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="4e69e-140">Observera att jag inte har skapat någon parameter med namnet `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="4e69e-141">`SupportsShouldProcess`Om du anger det skapas det automatiskt för oss.</span><span class="sxs-lookup"><span data-stu-id="4e69e-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="4e69e-142">När vi anger `-WhatIf` parametern på `Test-ShouldProcess` , är vissa saker som vi kallar också `-WhatIf` bearbetning.</span><span class="sxs-lookup"><span data-stu-id="4e69e-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="4e69e-143">Förtroende men verifiera</span><span class="sxs-lookup"><span data-stu-id="4e69e-143">Trust but verify</span></span>

<span data-ttu-id="4e69e-144">Det finns viss risk för att lita på att allt du anropar ärver `-WhatIf` värden.</span><span class="sxs-lookup"><span data-stu-id="4e69e-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="4e69e-145">I resten av exemplen kommer jag att anta att det inte fungerar och är mycket explicit när du gör anrop till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="4e69e-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="4e69e-146">Jag rekommenderar att du gör samma sak.</span><span class="sxs-lookup"><span data-stu-id="4e69e-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIfPreference
}
```

<span data-ttu-id="4e69e-147">Jag kommer att gå tillbaka till olika delarna senare när du har en bättre förståelse för alla delar i spelet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="4e69e-148">$PSCmdlet. ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="4e69e-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="4e69e-149">Metoden som gör att du kan implementera `SupportsShouldProcess` är `$PSCmdlet.ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="4e69e-150">Du `$PSCmdlet.ShouldProcess(...)` kan ringa för att se om du bör bearbeta en del logik och PowerShell för att ta hand om resten.</span><span class="sxs-lookup"><span data-stu-id="4e69e-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="4e69e-151">Vi börjar med ett exempel:</span><span class="sxs-lookup"><span data-stu-id="4e69e-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="4e69e-152">Anropet `$PSCmdlet.ShouldProcess($file.name)` för att kontrol lera `-WhatIf` (och `-Confirm` parametern) hanterar sedan det därefter.</span><span class="sxs-lookup"><span data-stu-id="4e69e-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="4e69e-153">`-WhatIf`Orsakerna `ShouldProcess` till en beskrivning av ändringen och retur `$false` :</span><span class="sxs-lookup"><span data-stu-id="4e69e-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="4e69e-154">Ett anrop med `-Confirm` pausar skriptet och användaren uppmanas att välja att fortsätta.</span><span class="sxs-lookup"><span data-stu-id="4e69e-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="4e69e-155">Den returneras `$true` om användaren har valts `Y` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4e69e-156">En fantastisk funktion i `$PSCmdlet.ShouldProcess` är att den dubbleras som utförliga utdata.</span><span class="sxs-lookup"><span data-stu-id="4e69e-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="4e69e-157">Jag är beroende av detta ofta när de implementeras `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="4e69e-158">Överlagringar</span><span class="sxs-lookup"><span data-stu-id="4e69e-158">Overloads</span></span>

<span data-ttu-id="4e69e-159">Det finns några olika överlagringar för `$PSCmdlet.ShouldProcess` med olika parametrar för att anpassa meddelande tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e69e-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="4e69e-160">Vi såg redan den första i exemplet ovan.</span><span class="sxs-lookup"><span data-stu-id="4e69e-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="4e69e-161">Låt oss ta en närmare titt på den.</span><span class="sxs-lookup"><span data-stu-id="4e69e-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="4e69e-162">Detta ger utdata som innehåller både funktions namnet och målet (värdet för parametern).</span><span class="sxs-lookup"><span data-stu-id="4e69e-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="4e69e-163">Om du anger en andra parameter som åtgärd används åtgärd svärdet i stället för funktions namnet i meddelandet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="4e69e-164">Nästa alternativ är att ange tre parametrar för att helt anpassa meddelandet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="4e69e-165">När tre parametrar används, är det första meddelandet.</span><span class="sxs-lookup"><span data-stu-id="4e69e-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="4e69e-166">De andra två parametrarna används fortfarande i `-Confirm` meddelandets utdata.</span><span class="sxs-lookup"><span data-stu-id="4e69e-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="4e69e-167">Snabb parameter referens</span><span class="sxs-lookup"><span data-stu-id="4e69e-167">Quick parameter reference</span></span>

<span data-ttu-id="4e69e-168">Om du bara kommer hit för att ta reda på vilka parametrar du ska använda, är det en snabb referens som visar hur parametrarna ändrar meddelandet i olika `-WhatIf` scenarier.</span><span class="sxs-lookup"><span data-stu-id="4e69e-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="4e69e-169">Jag brukar använda den med två parametrar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="4e69e-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="4e69e-170">ShouldProcessReason</span></span>

<span data-ttu-id="4e69e-171">Vi har en fjärde överlagring som är mer avancerad än de andra.</span><span class="sxs-lookup"><span data-stu-id="4e69e-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="4e69e-172">Det gör att du kan få orsaken till att du `ShouldProcess` har körts.</span><span class="sxs-lookup"><span data-stu-id="4e69e-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="4e69e-173">Jag lägger bara till detta för fullständighet eftersom vi bara kan kontrol lera om `$WhatIfPreference` är `$true` i stället.</span><span class="sxs-lookup"><span data-stu-id="4e69e-173">I'm only adding this here for completeness because we can just check if `$WhatIfPreference` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="4e69e-174">Vi måste skicka `$reason` variabeln till den fjärde parametern som en referens variabel med `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="4e69e-175">`ShouldProcess` fylls `$reason` med värdet `None` eller `WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="4e69e-176">Jag säger inte att detta var användbart och jag har inte haft någon anledning att någonsin använda det.</span><span class="sxs-lookup"><span data-stu-id="4e69e-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="4e69e-177">Var du ska placera den</span><span class="sxs-lookup"><span data-stu-id="4e69e-177">Where to place it</span></span>

<span data-ttu-id="4e69e-178">Du använder `ShouldProcess` för att göra skripten säkrare.</span><span class="sxs-lookup"><span data-stu-id="4e69e-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="4e69e-179">Så du använder det när dina skript gör ändringar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="4e69e-180">Jag vill placera `$PSCmdlet.ShouldProcess` anropet så nära ändringen som möjligt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="4e69e-181">Om jag bearbetar en samling objekt anropas den för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="4e69e-182">Anropet placeras i den förgrunds slingan.</span><span class="sxs-lookup"><span data-stu-id="4e69e-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="4e69e-183">Anledningen till varför jag `ShouldProcess` är nära ändringen, är att jag vill att så mycket kod som helst ska köras när `-WhatIf` har angetts.</span><span class="sxs-lookup"><span data-stu-id="4e69e-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="4e69e-184">Jag vill att installationen och verifieringen ska köras om möjligt så att användaren kan se dessa fel.</span><span class="sxs-lookup"><span data-stu-id="4e69e-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="4e69e-185">Jag vill också använda detta i mina pester-test som validerar mina projekt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="4e69e-186">Om jag har en del av logiken som är svår att modellera i pester kan jag ofta figursätta den i `ShouldProcess` och anropa den med `-WhatIf` i mina tester.</span><span class="sxs-lookup"><span data-stu-id="4e69e-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="4e69e-187">Det är bättre att testa en del av din kod än någon.</span><span class="sxs-lookup"><span data-stu-id="4e69e-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="4e69e-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="4e69e-188">$WhatIfPreference</span></span>

<span data-ttu-id="4e69e-189">Den första preferens variabeln som vi har är `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="4e69e-190">Detta är `$false` som standard.</span><span class="sxs-lookup"><span data-stu-id="4e69e-190">This is `$false` by default.</span></span> <span data-ttu-id="4e69e-191">Om du ställer in den på så `$true` körs funktionen som om du har angett `-WhatIf` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="4e69e-192">Om du ställer in detta i din session utför alla kommandon `-WhatIf` körning.</span><span class="sxs-lookup"><span data-stu-id="4e69e-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="4e69e-193">När du anropar en funktion med `-WhatIf` är värdet för `$WhatIfPreference` inställt på `$true` inom omfånget för din funktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="4e69e-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="4e69e-194">ConfirmImpact</span></span>

<span data-ttu-id="4e69e-195">De flesta av mina exempel är för, `-WhatIf` men allt så att allt så långt kan också användas för `-Confirm` att uppmana användaren att göra det.</span><span class="sxs-lookup"><span data-stu-id="4e69e-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="4e69e-196">Du kan ställa in `ConfirmImpact` funktionen på hög och uppmanas användaren som om den anropades med `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="4e69e-197">Detta anrop till `Test-ShouldProcess` utför åtgärden på `-Confirm` grund av `High` påverkan.</span><span class="sxs-lookup"><span data-stu-id="4e69e-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="4e69e-198">Det uppenbara problemet är att nu är det svårare att använda i andra skript utan att användaren tillfrågas.</span><span class="sxs-lookup"><span data-stu-id="4e69e-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="4e69e-199">I det här fallet kan vi skicka en `$false` till `-Confirm` för att förhindra prompten.</span><span class="sxs-lookup"><span data-stu-id="4e69e-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="4e69e-200">Jag lär dig hur du lägger till `-Force` stöd i ett senare avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="4e69e-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="4e69e-201">$ConfirmPreference</span></span>

<span data-ttu-id="4e69e-202">`$ConfirmPreference` är en automatisk variabel som styr när `ConfirmImpact` du uppmanas att bekräfta körning.</span><span class="sxs-lookup"><span data-stu-id="4e69e-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="4e69e-203">Här följer de möjliga värdena för både `$ConfirmPreference` och `ConfirmImpact` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="4e69e-204">Med dessa värden kan du ange olika effekt nivåer för varje funktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="4e69e-205">Om du har `$ConfirmPreference` angett ett värde som är högre än `ConfirmImpact` , uppmanas du inte att bekräfta körningen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="4e69e-206">Som standard `$ConfirmPreference` är anges till `High` och `ConfirmImpact` `Medium` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="4e69e-207">Om du vill att din funktion automatiskt ska ställa in användaren, ställer du in `ConfirmImpact` på `High` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="4e69e-208">Annars ställer du in den på `Medium` om den är förstörande och används `Low` om kommandot alltid är säkert körs i produktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="4e69e-209">Om du ställer in den som `none` fråga visas den inte även om `-Confirm` har angetts (men det ger fortfarande `-WhatIf` support).</span><span class="sxs-lookup"><span data-stu-id="4e69e-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="4e69e-210">När du anropar en funktion med `-Confirm` är värdet för `$ConfirmPreference` inställt på `Low` inom omfånget för din funktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="4e69e-211">Ignorera inkapslade bekräftelse meddelanden</span><span class="sxs-lookup"><span data-stu-id="4e69e-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="4e69e-212">De `$ConfirmPreference` kan hämtas av funktioner som du anropar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="4e69e-213">Detta kan skapa scenarier där du lägger till en bekräfta-prompt och funktionen som du anropar även efterfrågar användaren.</span><span class="sxs-lookup"><span data-stu-id="4e69e-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="4e69e-214">Vad jag brukar göra är att ange `-Confirm:$false` på de kommandon som jag anropar när jag redan har hanterat frågan.</span><span class="sxs-lookup"><span data-stu-id="4e69e-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="4e69e-215">Detta gör att vi återgår till en tidigare varning: det finns olika delarna när `-WhatIf` inte skickas till en funktion och skickas `-Confirm` till en funktion.</span><span class="sxs-lookup"><span data-stu-id="4e69e-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="4e69e-216">Jag lovar att jag kommer tillbaka till detta senare.</span><span class="sxs-lookup"><span data-stu-id="4e69e-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="4e69e-217">$PSCmdlet. ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="4e69e-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="4e69e-218">Om du behöver mer kontroll än `ShouldProcess` tillhandahåller kan du utlösa prompten direkt med `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="4e69e-219">`ShouldContinue` ignorerar,,, och, om det `$ConfirmPreference` `ConfirmImpact` `-Confirm` `$WhatIfPreference` `-WhatIf` sker varje gång det körs.</span><span class="sxs-lookup"><span data-stu-id="4e69e-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="4e69e-220">Det är enkelt att förväxla `ShouldProcess` och `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="4e69e-221">Jag brukar komma ihåg att använda `ShouldProcess` eftersom parametern anropas `SupportsShouldProcess` i `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="4e69e-222">Du bör använda `ShouldProcess` i nästan alla scenarier.</span><span class="sxs-lookup"><span data-stu-id="4e69e-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="4e69e-223">Det är därför jag täckte den metoden först.</span><span class="sxs-lookup"><span data-stu-id="4e69e-223">That is why I covered that method first.</span></span>

<span data-ttu-id="4e69e-224">Låt oss ta en titt på `ShouldContinue` åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4e69e-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="4e69e-225">Det ger oss en enklare prompt med färre alternativ.</span><span class="sxs-lookup"><span data-stu-id="4e69e-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="4e69e-226">Det största problemet med `ShouldContinue` är att användaren måste köra den interaktivt eftersom den alltid efterfrågar användaren.</span><span class="sxs-lookup"><span data-stu-id="4e69e-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="4e69e-227">Du bör alltid skapa verktyg som kan användas av andra skript.</span><span class="sxs-lookup"><span data-stu-id="4e69e-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="4e69e-228">På det sätt som du gör är det att implementera `-Force` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="4e69e-229">Jag går tillbaka till den här idén senare.</span><span class="sxs-lookup"><span data-stu-id="4e69e-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="4e69e-230">Ja till alla</span><span class="sxs-lookup"><span data-stu-id="4e69e-230">Yes to all</span></span>

<span data-ttu-id="4e69e-231">Detta hanteras automatiskt med `ShouldProcess` men vi måste göra lite mer arbete för `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="4e69e-232">Det finns en andra metod för överbelastning där vi måste skicka in några värden med hjälp av referens för att kontrol lera logiken.</span><span class="sxs-lookup"><span data-stu-id="4e69e-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="4e69e-233">Jag har lagt till en `foreach` loop och en samling för att visa att den fungerar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="4e69e-234">Jag hämtade `ShouldContinue` anropet från `if` instruktionen för att göra det lättare att läsa.</span><span class="sxs-lookup"><span data-stu-id="4e69e-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="4e69e-235">Att anropa en metod med fyra parametrar börjar få en liten fula, men jag försökte göra det så att det ser ut så rensat som jag kunde.</span><span class="sxs-lookup"><span data-stu-id="4e69e-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="4e69e-236">Implementera-Force</span><span class="sxs-lookup"><span data-stu-id="4e69e-236">Implementing -Force</span></span>

<span data-ttu-id="4e69e-237">`ShouldProcess` och `ShouldContinue` måste implementera `-Force` på olika sätt.</span><span class="sxs-lookup"><span data-stu-id="4e69e-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="4e69e-238">Sticket till dessa implementeringar är att `ShouldProcess` alltid ska köras, men `ShouldContinue` ska inte köras om `-Force` har angetts.</span><span class="sxs-lookup"><span data-stu-id="4e69e-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="4e69e-239">ShouldProcess – Force</span><span class="sxs-lookup"><span data-stu-id="4e69e-239">ShouldProcess -Force</span></span>

<span data-ttu-id="4e69e-240">Om du väljer `ConfirmImpact` att göra `high` det är det första som användarna kommer att försöka att förhindra det med `-Force` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="4e69e-241">Det är det första jag gör.</span><span class="sxs-lookup"><span data-stu-id="4e69e-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="4e69e-242">Om du återkallar från `ConfirmImpact` avsnittet måste du faktiskt anropa det så här:</span><span class="sxs-lookup"><span data-stu-id="4e69e-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="4e69e-243">Alla inser att de inte behöver göra det och `-Force` utelämna dem inte `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-243">Not everyone realizes they need to do that and `-Force` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="4e69e-244">Vi bör därför implementera `-Force` för Sanity av våra användare.</span><span class="sxs-lookup"><span data-stu-id="4e69e-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="4e69e-245">Ta en titt på det här fullständiga exemplet här:</span><span class="sxs-lookup"><span data-stu-id="4e69e-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="4e69e-246">Vi lägger till vår egna `-Force` växel som en parameter.</span><span class="sxs-lookup"><span data-stu-id="4e69e-246">We add our own `-Force` switch as a parameter.</span></span> <span data-ttu-id="4e69e-247">`-Confirm`Parametern läggs automatiskt till när du använder `SupportsShouldProcess` i `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-247">The `-Confirm` parameter is automatically added when using `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="4e69e-248">Fokusera på `-Force` logiken här:</span><span class="sxs-lookup"><span data-stu-id="4e69e-248">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="4e69e-249">Om användaren anger `-Force` vill vi ignorera bekräftelse uppmaningen om de inte också anges `-Confirm` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-249">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="4e69e-250">Detta gör att en användare kan tvinga fram en ändring men fortfarande bekräfta ändringen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-250">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="4e69e-251">Sedan anger vi `$ConfirmPreference` i det lokala omfånget.</span><span class="sxs-lookup"><span data-stu-id="4e69e-251">Then we set `$ConfirmPreference` in the local scope.</span></span> <span data-ttu-id="4e69e-252">Nu `-Force` ställer parametern `$ConfirmPreference` till none in på none, så att du inaktiverar frågan om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="4e69e-252">Now, using the `-Force` parameter temporarily sets the `$ConfirmPreference` to none, disabling prompt for confirmation.</span></span>

```powershell
if ($Force -or $PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="4e69e-253">Om någon anger både `-Force` och `-WhatIf` , `-WhatIf` måste du prioritera.</span><span class="sxs-lookup"><span data-stu-id="4e69e-253">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="4e69e-254">Den här metoden bevarar `-WhatIf` bearbetningen eftersom `ShouldProcess` alltid körs.</span><span class="sxs-lookup"><span data-stu-id="4e69e-254">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="4e69e-255">Lägg inte till en kontroll för `$Force` värdet i `if` instruktionen med `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-255">Do not add a check for the `$Force` value inside the `if` statement with the `ShouldProcess`.</span></span> <span data-ttu-id="4e69e-256">Det är ett anti-mönster för det här scenariot, även om det är det som visas i nästa avsnitt för `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-256">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="4e69e-257">ShouldContinue – Force</span><span class="sxs-lookup"><span data-stu-id="4e69e-257">ShouldContinue -Force</span></span>

<span data-ttu-id="4e69e-258">Detta är det korrekta sättet att implementera `-Force` med `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-258">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="4e69e-259">Genom att placera `$Force` till vänster om `-or` operatorn utvärderas det först.</span><span class="sxs-lookup"><span data-stu-id="4e69e-259">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="4e69e-260">Om du skriver på det sättet kortas körningen av `if` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-260">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="4e69e-261">Om `$force` är `$true` , `ShouldContinue` körs inte.</span><span class="sxs-lookup"><span data-stu-id="4e69e-261">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="4e69e-262">Vi behöver inte bekymra dig om `-Confirm` eller `-WhatIf` i det här scenariot eftersom de inte stöds av `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-262">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="4e69e-263">Det är därför det måste hanteras på ett annat sätt än `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-263">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="4e69e-264">Omfattnings problem</span><span class="sxs-lookup"><span data-stu-id="4e69e-264">Scope issues</span></span>

<span data-ttu-id="4e69e-265">Använder `-WhatIf` och ska `-Confirm` användas för allt i funktionerna och allt de kallar.</span><span class="sxs-lookup"><span data-stu-id="4e69e-265">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="4e69e-266">De gör detta genom att ställa in `$WhatIfPreference` till `$true` eller ställa in `$ConfirmPreference` till `Low` i det lokala omfånget för funktionen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-266">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="4e69e-267">Anrop att använda dessa värden när du anropar en annan funktion `ShouldProcess` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-267">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="4e69e-268">Detta fungerar faktiskt för det mesta av tiden.</span><span class="sxs-lookup"><span data-stu-id="4e69e-268">This actually works correctly most of the time.</span></span> <span data-ttu-id="4e69e-269">När du anropar en inbyggd cmdlet eller en funktion i samma omfång, fungerar den som den ska.</span><span class="sxs-lookup"><span data-stu-id="4e69e-269">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="4e69e-270">Det fungerar också när du anropar ett skript eller en funktion i en skript-modul från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4e69e-270">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="4e69e-271">Den enda plats där det inte fungerar är när ett skript eller en skript-modul anropar en funktion i en annan modul.</span><span class="sxs-lookup"><span data-stu-id="4e69e-271">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="4e69e-272">Detta kanske inte kan likna ett stort problem, men de flesta moduler som du skapar eller hämtar från PSGallery är skript moduler.</span><span class="sxs-lookup"><span data-stu-id="4e69e-272">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="4e69e-273">Kärn problemet är att skriptfilerna inte ärver värdena för `$WhatIfPreference` eller `$ConfirmPreference` (och flera andra) när de anropas från funktioner i andra skript moduler.</span><span class="sxs-lookup"><span data-stu-id="4e69e-273">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="4e69e-274">Det bästa sättet att sammanfatta detta som en allmän regel är att det fungerar korrekt för binära moduler och aldrig litar på att det fungerar för skript moduler.</span><span class="sxs-lookup"><span data-stu-id="4e69e-274">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="4e69e-275">Om du inte är säker kan du antingen testa det eller bara anta att det inte fungerar som det ska.</span><span class="sxs-lookup"><span data-stu-id="4e69e-275">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="4e69e-276">Jag tycker att det är mycket farligt eftersom det skapar scenarier där du lägger till `-WhatIf` stöd för flera moduler som fungerar korrekt i isolering, men som inte fungerar korrekt när de anropar varandra.</span><span class="sxs-lookup"><span data-stu-id="4e69e-276">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="4e69e-277">Vi har en GitHub-RFC som fungerar för att få det här problemet åtgärdat.</span><span class="sxs-lookup"><span data-stu-id="4e69e-277">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="4e69e-278">Mer information finns i avsnittet om att [sprida körnings inställningar utöver skript modulens omfång][RFC] .</span><span class="sxs-lookup"><span data-stu-id="4e69e-278">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="4e69e-279">I stängning</span><span class="sxs-lookup"><span data-stu-id="4e69e-279">In closing</span></span>

<span data-ttu-id="4e69e-280">Jag måste leta upp hur man använder `ShouldProcess` varje gång jag behöver använda det.</span><span class="sxs-lookup"><span data-stu-id="4e69e-280">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="4e69e-281">Det tog lång tid att skilja `ShouldProcess` från `ShouldContinue` .</span><span class="sxs-lookup"><span data-stu-id="4e69e-281">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="4e69e-282">Jag behöver nästan alltid se vilka parametrar som ska användas.</span><span class="sxs-lookup"><span data-stu-id="4e69e-282">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="4e69e-283">Du behöver inte oroa dig om du fortfarande kan växla från tid till gång.</span><span class="sxs-lookup"><span data-stu-id="4e69e-283">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="4e69e-284">Den här artikeln är här när du behöver den.</span><span class="sxs-lookup"><span data-stu-id="4e69e-284">This article will be here when you need it.</span></span> <span data-ttu-id="4e69e-285">Jag är säker på att jag ska referera till det ofta.</span><span class="sxs-lookup"><span data-stu-id="4e69e-285">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="4e69e-286">Om du gillade det här inlägget kan du dela dina tankar med mig på Twitter med hjälp av länken nedan.</span><span class="sxs-lookup"><span data-stu-id="4e69e-286">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="4e69e-287">Jag vill alltid höra från personer som får värde från mitt innehåll.</span><span class="sxs-lookup"><span data-stu-id="4e69e-287">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[vanliga parametrar]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[allt du ville veta om hash]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
