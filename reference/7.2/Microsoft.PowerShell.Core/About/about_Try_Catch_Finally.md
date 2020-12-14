---
description: Beskriver hur du använder `Try` , `Catch` och `Finally` blockerar för att hantera avslutande fel.
Locale: en-US
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_try_catch_finally?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Try_Catch_Finally
ms.openlocfilehash: c93fa69e3badd7777950a850dfe81b79f9197f68
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709235"
---
# <a name="about-try-catch-finally"></a><span data-ttu-id="b9bcf-103">Om try catch finally</span><span class="sxs-lookup"><span data-stu-id="b9bcf-103">About Try Catch Finally</span></span>

## <a name="short-description"></a><span data-ttu-id="b9bcf-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b9bcf-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="b9bcf-105">Beskriver hur du använder `Try` , `Catch` och `Finally` blockerar för att hantera avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-105">Describes how to use the `Try`, `Catch`, and `Finally` blocks to handle terminating errors.</span></span>

## <a name="long-description"></a><span data-ttu-id="b9bcf-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b9bcf-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="b9bcf-107">Använd `Try` , `Catch` och `Finally` blockerar för att svara på eller hantera avslutande fel i skript.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-107">Use `Try`, `Catch`, and `Finally` blocks to respond to or handle terminating errors in scripts.</span></span> <span data-ttu-id="b9bcf-108">`Trap`Instruktionen kan också användas för att hantera avslutande fel i skript.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-108">The `Trap` statement can also be used to handle terminating errors in scripts.</span></span> <span data-ttu-id="b9bcf-109">Mer information finns i [about_Trap](about_Trap.md).</span><span class="sxs-lookup"><span data-stu-id="b9bcf-109">For more information, see [about_Trap](about_Trap.md).</span></span>

<span data-ttu-id="b9bcf-110">Ett avslutande fel stoppar en instruktion som körs.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-110">A terminating error stops a statement from running.</span></span> <span data-ttu-id="b9bcf-111">Om PowerShell inte hanterar ett avbrotts fel på något sätt slutar PowerShell också att köra funktionen eller skriptet med den aktuella pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-111">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script using the current pipeline.</span></span> <span data-ttu-id="b9bcf-112">På andra språk, t. ex. C \# , kallas att avsluta fel som undantag.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-112">In other languages, such as C\#, terminating errors are referred to as exceptions.</span></span>

<span data-ttu-id="b9bcf-113">Använd `Try` blocket för att definiera ett avsnitt i ett skript där du vill att PowerShell ska övervakas för fel.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-113">Use the `Try` block to define a section of a script in which you want PowerShell to monitor for errors.</span></span> <span data-ttu-id="b9bcf-114">När ett fel uppstår i `Try` blocket sparas felet först i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-114">When an error occurs within the `Try` block, the error is first saved to the `$Error` automatic variable.</span></span> <span data-ttu-id="b9bcf-115">PowerShell söker sedan efter ett `Catch` block för att hantera felet.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-115">PowerShell then searches for a `Catch` block to handle the error.</span></span> <span data-ttu-id="b9bcf-116">Om `Try` instruktionen inte har något matchande `Catch` block fortsätter PowerShell att söka efter ett lämpligt `Catch` block eller `Trap` en instruktion i de överordnade omfången.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-116">If the `Try` statement does not have a matching `Catch` block, PowerShell continues to search for an appropriate `Catch` block or `Trap` statement in the parent scopes.</span></span> <span data-ttu-id="b9bcf-117">När ett `Catch` block har slutförts eller om det inte finns något lämpligt `Catch` block eller en `Trap` instruktion, `Finally` körs blocket.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-117">After a `Catch` block is completed or if no appropriate `Catch` block or `Trap` statement is found, the `Finally` block is run.</span></span> <span data-ttu-id="b9bcf-118">Om felet inte kan hanteras skrivs felet till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-118">If the error cannot be handled, the error is written to the error stream.</span></span>

<span data-ttu-id="b9bcf-119">Ett `Catch` block kan innehålla kommandon för att spåra felet eller för att återskapa det förväntade flödet i skriptet.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-119">A `Catch` block can include commands for tracking the error or for recovering the expected flow of the script.</span></span> <span data-ttu-id="b9bcf-120">Ett `Catch` block kan ange vilka fel typer den fångar upp.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-120">A `Catch` block can specify which error types it catches.</span></span> <span data-ttu-id="b9bcf-121">En `Try` instruktion kan innehålla flera `Catch` block för olika typer av fel.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-121">A `Try` statement can include multiple `Catch` blocks for different kinds of errors.</span></span>

<span data-ttu-id="b9bcf-122">Ett `Finally` block kan användas för att frigöra de resurser som inte längre behövs i skriptet.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-122">A `Finally` block can be used to free any resources that are no longer needed by your script.</span></span>

<span data-ttu-id="b9bcf-123">`Try`, `Catch` , och `Finally` liknar `Try` `Catch` nyckelorden, och `Finally` som används i programmeringsspråket C \# .</span><span class="sxs-lookup"><span data-stu-id="b9bcf-123">`Try`, `Catch`, and `Finally` resemble the `Try`, `Catch`, and `Finally` keywords used in the C\# programming language.</span></span>

### <a name="syntax"></a><span data-ttu-id="b9bcf-124">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b9bcf-124">SYNTAX</span></span>

<span data-ttu-id="b9bcf-125">En `Try` instruktion innehåller ett `Try` block, noll eller flera `Catch` block och inget eller ett `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-125">A `Try` statement contains a `Try` block, zero or more `Catch` blocks, and zero or one `Finally` block.</span></span> <span data-ttu-id="b9bcf-126">En `Try` instruktion måste innehålla minst ett `Catch` block eller ett `Finally` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-126">A `Try` statement must have at least one `Catch` block or one `Finally` block.</span></span>

<span data-ttu-id="b9bcf-127">Följande visar `Try` syntaxen för blockering:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-127">The following shows the `Try` block syntax:</span></span>

```powershell
try {<statement list>}
```

<span data-ttu-id="b9bcf-128">`Try`Nyckelordet följs av en instruktions lista inom klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-128">The `Try` keyword is followed by a statement list in braces.</span></span> <span data-ttu-id="b9bcf-129">Om ett avslutande fel inträffar när instruktionerna i instruktions listan körs, skickar skriptet felobjektet från `Try` blocket till ett lämpligt `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-129">If a terminating error occurs while the statements in the statement list are being run, the script passes the error object from the `Try` block to an appropriate `Catch` block.</span></span>

<span data-ttu-id="b9bcf-130">Följande visar `Catch` syntaxen för blockering:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-130">The following shows the `Catch` block syntax:</span></span>

```powershell
catch [[<error type>][',' <error type>]*] {<statement list>}
```

<span data-ttu-id="b9bcf-131">Fel typer visas inom hak paren tes.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-131">Error types appear in brackets.</span></span> <span data-ttu-id="b9bcf-132">De yttersta hakparenteserna anger att elementet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-132">The outermost brackets indicate the element is optional.</span></span>

<span data-ttu-id="b9bcf-133">`Catch`Nyckelordet följs av en valfri lista med fel typs specifikationer och en instruktions lista.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-133">The `Catch` keyword is followed by an optional list of error type specifications and a statement list.</span></span> <span data-ttu-id="b9bcf-134">Om ett avslutande fel inträffar i `Try` blocket söker PowerShell efter ett lämpligt `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-134">If a terminating error occurs in the `Try` block, PowerShell searches for an appropriate `Catch` block.</span></span> <span data-ttu-id="b9bcf-135">Om det finns en sådan sådan körs instruktionerna i `Catch` blocket.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-135">If one is found, the statements in the `Catch` block are executed.</span></span>

<span data-ttu-id="b9bcf-136">`Catch`Blocket kan ange en eller flera fel typer.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-136">The `Catch` block can specify one or more error types.</span></span> <span data-ttu-id="b9bcf-137">En typ av fel är ett Microsoft .NET Framework-undantag eller ett undantag som härleds från ett .NET Framework undantag.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-137">An error type is a Microsoft .NET Framework exception or an exception that is derived from a .NET Framework exception.</span></span> <span data-ttu-id="b9bcf-138">Ett `Catch` block hanterar fel i den angivna .NET Framework undantags klassen eller klasser som härleds från den angivna klassen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-138">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span>

<span data-ttu-id="b9bcf-139">Om ett `Catch` block anger en typ av fel, `Catch` hanterar blocket den typen av fel.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-139">If a `Catch` block specifies an error type, that `Catch` block handles that type of error.</span></span> <span data-ttu-id="b9bcf-140">Om ett `Catch` block inte anger någon typ av fel, `Catch` hanterar blocket ett fel som påträffas i `Try` blocket.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-140">If a `Catch` block does not specify an error type, that `Catch` block handles any error encountered in the `Try` block.</span></span> <span data-ttu-id="b9bcf-141">En `Try` instruktion kan innehålla flera `Catch` block för de olika angivna fel typerna.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-141">A `Try` statement can include multiple `Catch` blocks for the different specified error types.</span></span>

<span data-ttu-id="b9bcf-142">Följande visar `Finally` syntaxen för blockering:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-142">The following shows the `Finally` block syntax:</span></span>

```powershell
finally {<statement list>}
```

<span data-ttu-id="b9bcf-143">`Finally`Nyckelordet följs av en instruktions lista som körs varje gång skriptet körs, även om `Try` instruktionen kördes utan fel eller om ett fel har uppstått i en `Catch` instruktion.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-143">The `Finally` keyword is followed by a statement list that runs every time the script is run, even if the `Try` statement ran without error or an error was caught in a `Catch` statement.</span></span>

<span data-ttu-id="b9bcf-144">Observera att genom att trycka på <kbd>CTRL</kbd> + <kbd>C</kbd> stoppas pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-144">Note that pressing <kbd>CTRL</kbd>+<kbd>C</kbd> stops the pipeline.</span></span> <span data-ttu-id="b9bcf-145">Objekt som skickas till pipelinen visas inte som utdata.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-145">Objects that are sent to the pipeline will not be displayed as output.</span></span> <span data-ttu-id="b9bcf-146">Om du lägger till en instruktion som ska visas, t. ex. "finally block" har körts, visas det inte när du har tryckt på <kbd>CTRL</kbd> + <kbd>C</kbd>, även om `Finally` blocket kördes.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-146">Therefore, if you include a statement to be displayed, such as "Finally block has run", it will not be displayed after you press <kbd>CTRL</kbd>+<kbd>C</kbd>, even if the `Finally` block ran.</span></span>

### <a name="catching-errors"></a><span data-ttu-id="b9bcf-147">FÅNGA FEL</span><span class="sxs-lookup"><span data-stu-id="b9bcf-147">CATCHING ERRORS</span></span>

<span data-ttu-id="b9bcf-148">Följande exempel skript visar ett `Try` block med ett `Catch` block:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-148">The following sample script shows a `Try` block with a `Catch` block:</span></span>

```powershell
try { NonsenseString }
catch { "An error occurred." }
```

<span data-ttu-id="b9bcf-149">`Catch`Nyckelordet måste omedelbart följa `Try` blocket eller ett annat `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-149">The `Catch` keyword must immediately follow the `Try` block or another `Catch` block.</span></span>

<span data-ttu-id="b9bcf-150">PowerShell känner inte igen "NonsenseString" som en cmdlet eller något annat objekt.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-150">PowerShell does not recognize "NonsenseString" as a cmdlet or other item.</span></span>
<span data-ttu-id="b9bcf-151">När skriptet körs returneras följande resultat:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-151">Running this script returns the following result:</span></span>

```powershell
An error occurred.
```

<span data-ttu-id="b9bcf-152">När skriptet påträffar "NonsenseString" orsakar det ett avslutande fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-152">When the script encounters "NonsenseString", it causes a terminating error.</span></span> <span data-ttu-id="b9bcf-153">`Catch`Blocket hanterar felet genom att köra instruktions listan inuti blocket.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-153">The `Catch` block handles the error by running the statement list inside the block.</span></span>

### <a name="using-multiple-catch-statements"></a><span data-ttu-id="b9bcf-154">ANVÄNDA FLERA CATCH-INSTRUKTIONER</span><span class="sxs-lookup"><span data-stu-id="b9bcf-154">USING MULTIPLE CATCH STATEMENTS</span></span>

<span data-ttu-id="b9bcf-155">En `Try` instruktion kan ha valfritt antal `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-155">A `Try` statement can have any number of `Catch` blocks.</span></span> <span data-ttu-id="b9bcf-156">Följande skript har till exempel ett `Try` block som laddas ned `MyDoc.doc` och innehåller två `Catch` block:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-156">For example, the following script has a `Try` block that downloads `MyDoc.doc`, and it contains two `Catch` blocks:</span></span>

```powershell
try {
   $wc = new-object System.Net.WebClient
   $wc.DownloadFile("http://www.contoso.com/MyDoc.doc","c:\temp\MyDoc.doc")
}
catch [System.Net.WebException],[System.IO.IOException] {
    "Unable to download MyDoc.doc from http://www.contoso.com."
}
catch {
    "An error occurred that could not be resolved."
}

```

<span data-ttu-id="b9bcf-157">Det första `Catch` blocket hanterar fel i typerna **system .net. WebException** och **system. io. IOException** .</span><span class="sxs-lookup"><span data-stu-id="b9bcf-157">The first `Catch` block handles errors of the **System.Net.WebException** and **System.IO.IOException** types.</span></span> <span data-ttu-id="b9bcf-158">Det andra `Catch` blocket anger ingen feltyp.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-158">The second `Catch` block does not specify an error type.</span></span> <span data-ttu-id="b9bcf-159">Det andra `Catch` blocket hanterar alla andra avslutande fel som inträffar.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-159">The second `Catch` block handles any other terminating errors that occur.</span></span>

<span data-ttu-id="b9bcf-160">PowerShell matchar fel typer genom arv.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-160">PowerShell matches error types by inheritance.</span></span> <span data-ttu-id="b9bcf-161">Ett `Catch` block hanterar fel i den angivna .NET Framework undantags klassen eller klasser som härleds från den angivna klassen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-161">A `Catch` block handles errors of the specified .NET Framework exception class or of any class that derives from the specified class.</span></span> <span data-ttu-id="b9bcf-162">Följande exempel innehåller ett `Catch` block som fångar fel meddelandet "kommandot hittades inte":</span><span class="sxs-lookup"><span data-stu-id="b9bcf-162">The following example contains a `Catch` block that catches a "Command Not Found" error:</span></span>

```powershell
catch [System.Management.Automation.CommandNotFoundException]
{"Inherited Exception" }
```

<span data-ttu-id="b9bcf-163">Den angivna feltypen, **CommandNotFoundException**, ärver från **System.SystemException** -typen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-163">The specified error type, **CommandNotFoundException**, inherits from the **System.SystemException** type.</span></span> <span data-ttu-id="b9bcf-164">Följande exempel fångar också upp ett kommando som inte hittas:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-164">The following example also catches a Command Not Found error:</span></span>

```powershell
catch [System.SystemException] {"Base Exception" }
```

<span data-ttu-id="b9bcf-165">Det här `Catch` blocket hanterar felet "kommandot hittades inte" och andra fel som ärver från **SystemException** -typen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-165">This `Catch` block handles the "Command Not Found" error and other errors that inherit from the **SystemException** type.</span></span>

<span data-ttu-id="b9bcf-166">Om du anger en felklass och en av dess härledda klasser, placerar du `Catch` blocket för den härledda klassen före `Catch` blocket för den allmänna klassen.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-166">If you specify an error class and one of its derived classes, place the `Catch` block for the derived class before the `Catch` block for the general class.</span></span>

### <a name="using-traps-in-a-try-catch"></a><span data-ttu-id="b9bcf-167">Använda traps i en try-catch</span><span class="sxs-lookup"><span data-stu-id="b9bcf-167">Using Traps in a Try Catch</span></span>

<span data-ttu-id="b9bcf-168">När ett avbrotts fel inträffar i ett `Try` block med en `Trap` definierad i `Try` blocket, även om det finns ett matchande `Catch` block, `Trap` tar instruktionen kontroll.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-168">When a terminating error occurs in a `Try` block with a `Trap` defined within the `Try` block, even if there is a matching `Catch` block, the `Trap` statement takes control.</span></span>

<span data-ttu-id="b9bcf-169">Om det `Trap` finns ett högre block än `Try` , och det inte finns något matchande `Catch` block inom det aktuella omfånget, `Trap` kommer kontrollen att ta kontroll, även om ett överordnat omfång har ett matchande `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-169">If a `Trap` exists at a higher block than the `Try`, and there is no matching `Catch` block within the current scope, the `Trap` will take control, even if any parent scope has a matching `Catch` block.</span></span>

### <a name="accessing-exception-information"></a><span data-ttu-id="b9bcf-170">ÅTKOMST TILL UNDANTAGS INFORMATION</span><span class="sxs-lookup"><span data-stu-id="b9bcf-170">ACCESSING EXCEPTION INFORMATION</span></span>

<span data-ttu-id="b9bcf-171">I ett `Catch` block kan du komma åt det aktuella felet med `$_` , vilket även kallas `$PSItem` .</span><span class="sxs-lookup"><span data-stu-id="b9bcf-171">Within a `Catch` block, the current error can be accessed using `$_`, which is also known as `$PSItem`.</span></span> <span data-ttu-id="b9bcf-172">Objektet är av typen **ErrorRecord**.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-172">The object is of type **ErrorRecord**.</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_
}
```

<span data-ttu-id="b9bcf-173">När skriptet körs returneras följande resultat:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-173">Running this script returns the following result:</span></span>

```Output
An Error occurred:
The term 'NonsenseString' is not recognized as the name of a cmdlet, function,
script file, or operable program. Check the spelling of the name, or if a path
was included, verify that the path is correct and try again.
```

<span data-ttu-id="b9bcf-174">Det finns ytterligare egenskaper som kan nås, till exempel **ScriptStackTrace**, **undantag** och **ErrorDetails**.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-174">There are additional properties that can be accessed, such as **ScriptStackTrace**, **Exception**, and **ErrorDetails**.</span></span>  <span data-ttu-id="b9bcf-175">Om vi till exempel ändrar skriptet till följande:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-175">For example, if we change the script to the following:</span></span>

```powershell
try { NonsenseString }
catch {
  Write-Host "An error occurred:"
  Write-Host $_.ScriptStackTrace
}
```

<span data-ttu-id="b9bcf-176">Resultatet ser ut ungefär så här:</span><span class="sxs-lookup"><span data-stu-id="b9bcf-176">The result will be similar to:</span></span>

```
An Error occurred:
at <ScriptBlock>, <No file>: line 2
```

### <a name="freeing-resources-by-using-finally"></a><span data-ttu-id="b9bcf-177">FRIGÖRA RESURSER MED FINALLY</span><span class="sxs-lookup"><span data-stu-id="b9bcf-177">FREEING RESOURCES BY USING FINALLY</span></span>

<span data-ttu-id="b9bcf-178">Om du vill frigöra resurser som används av ett skript lägger du till ett `Finally` block efter- `Try` och- `Catch` blocken.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-178">To free resources used by a script, add a `Finally` block after the `Try` and `Catch` blocks.</span></span> <span data-ttu-id="b9bcf-179">`Finally`Block satserna körs oavsett om `Try` blocket påträffar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-179">The `Finally` block statements run regardless of whether the `Try` block encounters a terminating error.</span></span> <span data-ttu-id="b9bcf-180">PowerShell kör `Finally` blocket innan skriptet avslutas eller innan det aktuella blocket hamnar utanför omfånget.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-180">PowerShell runs the `Finally` block before the script terminates or before the current block goes out of scope.</span></span>

<span data-ttu-id="b9bcf-181">Ett `Finally` block körs även om du använder <kbd>CTRL</kbd> + <kbd>C</kbd> för att stoppa skriptet.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-181">A `Finally` block runs even if you use <kbd>CTRL</kbd>+<kbd>C</kbd> to stop the script.</span></span> <span data-ttu-id="b9bcf-182">Ett `Finally` block körs också om ett avslutnings nyckelord stoppar skriptet inifrån ett `Catch` block.</span><span class="sxs-lookup"><span data-stu-id="b9bcf-182">A `Finally` block also runs if an Exit keyword stops the script from within a `Catch` block.</span></span>

### <a name="see-also"></a><span data-ttu-id="b9bcf-183">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="b9bcf-183">SEE ALSO</span></span>

[<span data-ttu-id="b9bcf-184">about_Break</span><span class="sxs-lookup"><span data-stu-id="b9bcf-184">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="b9bcf-185">about_Continue</span><span class="sxs-lookup"><span data-stu-id="b9bcf-185">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="b9bcf-186">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="b9bcf-186">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="b9bcf-187">about_Throw</span><span class="sxs-lookup"><span data-stu-id="b9bcf-187">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="b9bcf-188">about_Trap</span><span class="sxs-lookup"><span data-stu-id="b9bcf-188">about_Trap</span></span>](about_Trap.md)

