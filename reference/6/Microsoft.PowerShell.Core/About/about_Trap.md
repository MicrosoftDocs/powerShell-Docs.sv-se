---
description: Beskriver ett nyckelord som hanterar ett avslutande fel.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_trap?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Trap
ms.openlocfilehash: 88c16066b96912faf38fd48a3bd2f84572707e4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270350"
---
# <a name="about-trap"></a><span data-ttu-id="e8e14-104">Om trap</span><span class="sxs-lookup"><span data-stu-id="e8e14-104">About Trap</span></span>

## <a name="short-description"></a><span data-ttu-id="e8e14-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e8e14-105">Short description</span></span>

<span data-ttu-id="e8e14-106">Beskriver ett nyckelord som hanterar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-106">Describes a keyword that handles a terminating error.</span></span>

## <a name="long-description"></a><span data-ttu-id="e8e14-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e8e14-107">Long description</span></span>

<span data-ttu-id="e8e14-108">Ett avslutande fel stoppar en instruktion som körs.</span><span class="sxs-lookup"><span data-stu-id="e8e14-108">A terminating error stops a statement from running.</span></span> <span data-ttu-id="e8e14-109">Om PowerShell inte hanterar ett avbrotts fel på något sätt slutar PowerShell också att köra funktionen eller skriptet i den aktuella pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-109">If PowerShell does not handle a terminating error in some way, PowerShell also stops running the function or script in the current pipeline.</span></span> <span data-ttu-id="e8e14-110">På andra språk, till exempel C#, kallas fel för undantag.</span><span class="sxs-lookup"><span data-stu-id="e8e14-110">In other languages, such as C#, terminating errors are known as exceptions.</span></span>

<span data-ttu-id="e8e14-111">`trap`Nyckelordet anger en lista över instruktioner som ska köras när ett avslutande fel inträffar.</span><span class="sxs-lookup"><span data-stu-id="e8e14-111">The `trap` keyword specifies a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="e8e14-112">`trap` -uttryck hanterar de avslutande felen på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="e8e14-112">`trap` statements handle the terminating errors in the following ways:</span></span>

- <span data-ttu-id="e8e14-113">Visa felet efter bearbetning av `trap` instruktions blocket och fortsätta köra skriptet eller funktionen som innehåller `trap` .</span><span class="sxs-lookup"><span data-stu-id="e8e14-113">Display the error after processing the `trap` statement block and continuing execution of the script or function containing the `trap`.</span></span> <span data-ttu-id="e8e14-114">Det här är standardbeteendet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-114">This is the default behavior.</span></span>

- <span data-ttu-id="e8e14-115">Visa fel och Avbryt körningen av skriptet eller funktionen som innehåller `trap` using `break` i- `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-115">Display the error and abort execution of the script or function containing the `trap` using `break` in the `trap` statement.</span></span>

- <span data-ttu-id="e8e14-116">Dämpa felet, men fortsätt köra skriptet eller funktionen med `trap` hjälp av `continue` i `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-116">Silence the error, but continue execution of the script or function containing the `trap` by using `continue` in the `trap` statement.</span></span>

<span data-ttu-id="e8e14-117">Instruktions listan i `trap` kan innehålla flera villkor eller funktions anrop.</span><span class="sxs-lookup"><span data-stu-id="e8e14-117">The statement list of the `trap` can include multiple conditions or function calls.</span></span> <span data-ttu-id="e8e14-118">En `trap` kan skriva loggar, test villkor eller till och med köra ett annat program.</span><span class="sxs-lookup"><span data-stu-id="e8e14-118">A `trap` can write logs, test conditions, or even run another program.</span></span>

### <a name="syntax"></a><span data-ttu-id="e8e14-119">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8e14-119">Syntax</span></span>

<span data-ttu-id="e8e14-120">`trap`Instruktionen har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="e8e14-120">The `trap` statement has the following syntax:</span></span>

```powershell
trap [[<error type>]] {<statement list>}
```

<span data-ttu-id="e8e14-121">`trap`Instruktionen innehåller en lista över instruktioner som ska köras när ett avslutande fel inträffar.</span><span class="sxs-lookup"><span data-stu-id="e8e14-121">The `trap` statement includes a list of statements to run when a terminating error occurs.</span></span> <span data-ttu-id="e8e14-122">En `trap` instruktion består av `trap` nyckelordet, eventuellt följt av ett typ uttryck och instruktions blocket som innehåller listan över instruktioner som ska köras när ett fel har fångats.</span><span class="sxs-lookup"><span data-stu-id="e8e14-122">A `trap` statement consists of the `trap` keyword, optionally followed by a type expression, and the statement block containing the list of statements to run when an error is trapped.</span></span> <span data-ttu-id="e8e14-123">Typ uttrycket begränsar de typer av fel som `trap` fångas.</span><span class="sxs-lookup"><span data-stu-id="e8e14-123">The type expression refines the types of errors the `trap` catches.</span></span>

<span data-ttu-id="e8e14-124">Ett skript eller kommando kan ha flera `trap` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="e8e14-124">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="e8e14-125">`trap` instruktioner kan visas var som helst i skriptet eller kommandot.</span><span class="sxs-lookup"><span data-stu-id="e8e14-125">`trap` statements can appear anywhere in the script or command.</span></span>

### <a name="trapping-all-terminating-errors"></a><span data-ttu-id="e8e14-126">Svällning av alla avslutande fel</span><span class="sxs-lookup"><span data-stu-id="e8e14-126">Trapping all terminating errors</span></span>

<span data-ttu-id="e8e14-127">När ett avslutande fel inträffar som inte hanteras på ett annat sätt i ett skript eller kommando, kontrollerar PowerShell om det finns en `trap` instruktion som hanterar felet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-127">When a terminating error occurs that is not handled in another way in a script or command, PowerShell checks for a `trap` statement that handles the error.</span></span> <span data-ttu-id="e8e14-128">Om det finns en `trap` instruktion fortsätter PowerShell att köra skriptet eller kommandot i `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-128">If a `trap` statement is present, PowerShell continues running the script or command in the `trap` statement.</span></span>

<span data-ttu-id="e8e14-129">Följande exempel är ett väldigt enkelt `trap` uttryck:</span><span class="sxs-lookup"><span data-stu-id="e8e14-129">The following example is a very simple `trap` statement:</span></span>

```powershell
trap {"Error found."}
```

<span data-ttu-id="e8e14-130">Den här `trap` instruktionen påfäller eventuella avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-130">This `trap` statement traps any terminating error.</span></span>

<span data-ttu-id="e8e14-131">I följande exempel innehåller funktionen en InSense-sträng som orsakar ett körnings fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-131">In the following example, the function includes a nonsense string that causes a runtime error.</span></span>

```powershell
function TrapTest {
    trap {"Error found."}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="e8e14-132">När den här funktionen körs returneras följande:</span><span class="sxs-lookup"><span data-stu-id="e8e14-132">Running this function returns the following:</span></span>

```Output
Error found.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="e8e14-133">Följande exempel innehåller en `trap` instruktion som visar felet med hjälp av den `$_` automatiska variabeln:</span><span class="sxs-lookup"><span data-stu-id="e8e14-133">The following example includes a `trap` statement that displays the error by using the `$_` automatic variable:</span></span>

```powershell
function TrapTest {
    trap {"Error found: $_"}
    nonsenseString
}

TrapTest
```

<span data-ttu-id="e8e14-134">Om du kör den här versionen av funktionen returneras följande:</span><span class="sxs-lookup"><span data-stu-id="e8e14-134">Running this version of the function returns the following:</span></span>

```Output
Error found: The term 'nonsenseString' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of the
name, or if a path was included, verify that the path is correct and try again.
nonsenseString:
Line |
   3 |      nonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

> [!IMPORTANT]
> <span data-ttu-id="e8e14-135">`trap` -instruktioner kan definieras var som helst inom ett angivet omfång, men gäller alltid alla-instruktioner i det omfånget.</span><span class="sxs-lookup"><span data-stu-id="e8e14-135">`trap` statements may be defined anywhere within a given scope, but always apply to all statements in that scope.</span></span> <span data-ttu-id="e8e14-136">Vid körning `trap` definieras instruktioner i ett block innan andra instruktioner körs.</span><span class="sxs-lookup"><span data-stu-id="e8e14-136">At runtime, `trap` statements in a block are defined before any other statements are executed.</span></span> <span data-ttu-id="e8e14-137">I Java Script kallas detta för att [lyfta](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span><span class="sxs-lookup"><span data-stu-id="e8e14-137">In JavaScript, this is known as [hoisting](https://wikipedia.org/wiki/JavaScript_syntax#hoisting).</span></span> <span data-ttu-id="e8e14-138">Detta innebär att `trap` instruktioner gäller för alla instruktioner i det här blocket även om körningen inte har varit avancerad efter den tidpunkt då de har definierats.</span><span class="sxs-lookup"><span data-stu-id="e8e14-138">This means that `trap` statements apply to all statements in that block even if execution has not advanced past the point at which they are defined.</span></span> <span data-ttu-id="e8e14-139">Om du till exempel definierar en i `trap` slutet av ett skript och utlöser ett fel i den första instruktionen utlöses fortfarande `trap` .</span><span class="sxs-lookup"><span data-stu-id="e8e14-139">For example, defining a `trap` at the end of a script and throwing an error in the first statement still triggers that `trap`.</span></span>

### <a name="trapping-specific-errors"></a><span data-ttu-id="e8e14-140">Trap-vissa fel</span><span class="sxs-lookup"><span data-stu-id="e8e14-140">Trapping specific errors</span></span>

<span data-ttu-id="e8e14-141">Ett skript eller kommando kan ha flera `trap` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="e8e14-141">A script or command can have multiple `trap` statements.</span></span> <span data-ttu-id="e8e14-142">En `trap` kan definieras för att hantera vissa fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-142">A `trap` can be defined to handle specific errors.</span></span>

<span data-ttu-id="e8e14-143">Följande exempel är en `trap` instruktion som fäller in det angivna felet **CommandNotFoundException** :</span><span class="sxs-lookup"><span data-stu-id="e8e14-143">The following example is a `trap` statement that traps the specific error **CommandNotFoundException** :</span></span>

```powershell
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
```

<span data-ttu-id="e8e14-144">När en funktion eller ett skript påträffar en sträng som inte matchar ett känt kommando, visar den här `trap` instruktionen strängen "kommando fel som fångats".</span><span class="sxs-lookup"><span data-stu-id="e8e14-144">When a function or script encounters a string that does not match a known command, this `trap` statement displays the "Command error trapped" string.</span></span>
<span data-ttu-id="e8e14-145">När du `trap` har kört instruktions listan skriver PowerShell felobjektet till fel strömmen och fortsätter sedan med skriptet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-145">After running the `trap` statement list, PowerShell writes the error object to the error stream and then continues the script.</span></span>

<span data-ttu-id="e8e14-146">PowerShell använder .NET-undantags typer.</span><span class="sxs-lookup"><span data-stu-id="e8e14-146">PowerShell uses .NET exception types.</span></span> <span data-ttu-id="e8e14-147">I följande exempel anges fel typen **system. Exception** :</span><span class="sxs-lookup"><span data-stu-id="e8e14-147">The following example specifies the **System.Exception** error type:</span></span>

```powershell
trap [System.Exception] {"An error trapped"}
```

<span data-ttu-id="e8e14-148">Fel typen **CommandNotFoundException** ärver från **system. Exception** -typen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-148">The **CommandNotFoundException** error type inherits from the **System.Exception** type.</span></span> <span data-ttu-id="e8e14-149">Den här instruktionen påfäller ett fel som skapats av ett okänt kommando.</span><span class="sxs-lookup"><span data-stu-id="e8e14-149">This statement traps an error that is created by an unknown command.</span></span> <span data-ttu-id="e8e14-150">Den sväller också andra fel typer.</span><span class="sxs-lookup"><span data-stu-id="e8e14-150">It also traps other error types.</span></span>

<span data-ttu-id="e8e14-151">Du kan ha mer än en `trap` instruktion i ett skript.</span><span class="sxs-lookup"><span data-stu-id="e8e14-151">You can have more than one `trap` statement in a script.</span></span> <span data-ttu-id="e8e14-152">Varje typ av fel kan bara fångas av en `trap` instruktion.</span><span class="sxs-lookup"><span data-stu-id="e8e14-152">Each error type can be trapped by only one `trap` statement.</span></span> <span data-ttu-id="e8e14-153">När ett avbrotts fel inträffar söker PowerShell efter den `trap` mest exakta matchningen med början i det aktuella körnings omfånget.</span><span class="sxs-lookup"><span data-stu-id="e8e14-153">When a terminating error occurs, PowerShell searches for the `trap` with the most specific match, starting in the current scope of execution.</span></span>

<span data-ttu-id="e8e14-154">Följande skript exempel innehåller ett fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-154">The following script example contains an error.</span></span> <span data-ttu-id="e8e14-155">Skriptet innehåller en allmän `trap` instruktion som avbryter eventuella avslutande fel och en speciell `trap` instruktion som anger typen av **CommandNotFoundException** .</span><span class="sxs-lookup"><span data-stu-id="e8e14-155">The script includes a general `trap` statement that traps any terminating error and a specific `trap` statement that specifies the **CommandNotFoundException** type.</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException] {
  "Command error trapped"
}
nonsenseString
```

<span data-ttu-id="e8e14-156">Att köra det här skriptet ger följande resultat:</span><span class="sxs-lookup"><span data-stu-id="e8e14-156">Running this script produces the following result:</span></span>

```Output
Command error trapped
nonsenseString:
Line |
   5 |  nonsenseString
     |  ~~~~~~~~~~~~~~
     | The term 'nonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="e8e14-157">Eftersom PowerShell inte känner igen "nonsenseString" som en cmdlet eller något annat objekt, returnerar den ett **CommandNotFoundException** -fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-157">Because PowerShell does not recognize "nonsenseString" as a cmdlet or other item, it returns a **CommandNotFoundException** error.</span></span> <span data-ttu-id="e8e14-158">Detta avslutande fel har fångats upp av den speciella `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-158">This terminating error is trapped by the specific `trap` statement.</span></span>

<span data-ttu-id="e8e14-159">Följande skript exempel innehåller samma `trap` uttryck med ett annat fel:</span><span class="sxs-lookup"><span data-stu-id="e8e14-159">The following script example contains the same `trap` statements with a different error:</span></span>

```powershell
trap {"Other terminating error trapped" }
trap [System.Management.Automation.CommandNotFoundException]
    {"Command error trapped"}
1/$null
```

<span data-ttu-id="e8e14-160">Att köra det här skriptet ger följande resultat:</span><span class="sxs-lookup"><span data-stu-id="e8e14-160">Running this script produces the following result:</span></span>

```Output
Other terminating error trapped
RuntimeException:
Line |
   4 |  1/$null
     |  ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="e8e14-161">Försöket att dividera med noll skapar inte ett **CommandNotFoundException** -fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-161">The attempt to divide by zero does not create a **CommandNotFoundException** error.</span></span> <span data-ttu-id="e8e14-162">I stället svälls det här felet av den andra `trap` instruktionen, vilket sväller eventuella avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-162">Instead, that error is trapped by the other `trap` statement, which traps any terminating error.</span></span>

### <a name="trapping-errors-and-scope"></a><span data-ttu-id="e8e14-163">Trap-fel och omfattning</span><span class="sxs-lookup"><span data-stu-id="e8e14-163">Trapping errors and scope</span></span>

<span data-ttu-id="e8e14-164">Om ett avslutande fel inträffar i samma omfång som `trap` instruktionen kör PowerShell listan över instruktioner som definierats av `trap` .</span><span class="sxs-lookup"><span data-stu-id="e8e14-164">If a terminating error occurs in the same scope as the `trap` statement, PowerShell runs the list of statements defined by the `trap`.</span></span> <span data-ttu-id="e8e14-165">Körningen fortsätter vid instruktionen efter felet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-165">Execution continues at the statement after the error.</span></span> <span data-ttu-id="e8e14-166">Om `trap` instruktionen är i ett annat omfång från felet fortsätter körningen vid nästa instruktion som är i samma omfång som `trap` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-166">If the `trap` statement is in a different scope from the error, execution continues at the next statement that is in the same scope as the `trap` statement.</span></span>

<span data-ttu-id="e8e14-167">Om ett fel exempelvis inträffar i en funktion och `trap` instruktionen är i funktionen, fortsätter skriptet vid nästa instruktion.</span><span class="sxs-lookup"><span data-stu-id="e8e14-167">For example, if an error occurs in a function, and the `trap` statement is in the function, the script continues at the next statement.</span></span> <span data-ttu-id="e8e14-168">Följande skript innehåller ett fel och en `trap` instruktion:</span><span class="sxs-lookup"><span data-stu-id="e8e14-168">The following script contains an error and a `trap` statement:</span></span>

```powershell
function function1 {
    trap { "An error: " }
    NonsenseString
    "function1 was completed"
}

function1
```

<span data-ttu-id="e8e14-169">Att köra det här skriptet ger följande resultat:</span><span class="sxs-lookup"><span data-stu-id="e8e14-169">Running this script produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   3 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
function1 was completed
```

<span data-ttu-id="e8e14-170">`trap`Instruktionen i funktionen traps-felet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-170">The `trap` statement in the function traps the error.</span></span> <span data-ttu-id="e8e14-171">När meddelandet har visats fortsätter PowerShell att köra funktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-171">After displaying the message, PowerShell resumes running the function.</span></span> <span data-ttu-id="e8e14-172">Obs! `Function1` har slutförts.</span><span class="sxs-lookup"><span data-stu-id="e8e14-172">Note that `Function1` was completed.</span></span>

<span data-ttu-id="e8e14-173">Jämför detta med följande exempel, som har samma fel och `trap` instruktion.</span><span class="sxs-lookup"><span data-stu-id="e8e14-173">Compare this with the following example, which has the same error and `trap` statement.</span></span> <span data-ttu-id="e8e14-174">I det här exemplet `trap` inträffar instruktionen utanför funktionen:</span><span class="sxs-lookup"><span data-stu-id="e8e14-174">In this example, the `trap` statement occurs outside the function:</span></span>

```powershell
function function2 {
    NonsenseString
    "function2 was completed"
}

trap { "An error: " }

function2
```

<span data-ttu-id="e8e14-175">Att köra `Function2` funktionen ger följande resultat:</span><span class="sxs-lookup"><span data-stu-id="e8e14-175">Running the `Function2` function produces the following result:</span></span>

```Output
An error:
NonsenseString:
Line |
   2 |      NonsenseString
     |      ~~~~~~~~~~~~~~
     | The term 'NonsenseString' is not recognized as the name of a cmdlet,
function, script file, or operable program. Check the spelling of the name, or
if a path was included, verify that the path is correct and try again.
```

<span data-ttu-id="e8e14-176">I det här exemplet kördes inte kommandot "function2 har slutförts".</span><span class="sxs-lookup"><span data-stu-id="e8e14-176">In this example, the "function2 was completed" command was not run.</span></span> <span data-ttu-id="e8e14-177">I båda exemplen inträffar det avslutande felet i funktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-177">In both examples, the terminating error occurs within the function.</span></span> <span data-ttu-id="e8e14-178">I det här exemplet `trap` finns dock instruktionen utanför funktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-178">In this example, however, the `trap` statement is outside the function.</span></span> <span data-ttu-id="e8e14-179">PowerShell går inte tillbaka till funktionen när `trap` instruktionen har körts.</span><span class="sxs-lookup"><span data-stu-id="e8e14-179">PowerShell does not go back into the function after the `trap` statement runs.</span></span>

> [!CAUTION]
> <span data-ttu-id="e8e14-180">När flera traps har definierats för samma fel villkor används den första `trap` definierade (högst i definitions området).</span><span class="sxs-lookup"><span data-stu-id="e8e14-180">When multiple traps are defined for the same error condition, the first `trap` defined lexically (highest in the scope) is used.</span></span>

<span data-ttu-id="e8e14-181">I följande exempel `trap` körs bara med "Whoops 1".</span><span class="sxs-lookup"><span data-stu-id="e8e14-181">In the following example, only the `trap` with "whoops 1" is run.</span></span>

```powershell
Remove-Item -ErrorAction Stop ThisFileDoesNotExist
trap { "whoops 1"; continue }
trap { "whoops 2"; continue }
```

> [!IMPORTANT]
> <span data-ttu-id="e8e14-182">En trap-instruktion är begränsad till den plats där den kompileras.</span><span class="sxs-lookup"><span data-stu-id="e8e14-182">A Trap statement is scoped to where it compiles.</span></span> <span data-ttu-id="e8e14-183">Om du har en `trap` instruktion inuti ett skript med en funktion eller ett punkts källa, `trap` tas alla instruktioner i bort när skriptet avslutas.</span><span class="sxs-lookup"><span data-stu-id="e8e14-183">If you have a `trap` statement inside a function or dot sourced script, when the function or dot sourced script exits, all `trap` statements inside are removed.</span></span>

### <a name="using-the-break-and-continue-keywords"></a><span data-ttu-id="e8e14-184">Använda nyckelorden Break och Continue</span><span class="sxs-lookup"><span data-stu-id="e8e14-184">Using the break and continue keywords</span></span>

<span data-ttu-id="e8e14-185">Du kan använda `break` `continue` nyckelorden och i en- `trap` instruktion för att avgöra om ett skript eller kommando fortsätter att köras efter ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e8e14-185">You can use the `break` and `continue` keywords in a `trap` statement to determine whether a script or command continues to run after a terminating error.</span></span>

<span data-ttu-id="e8e14-186">Om du inkluderar en `break` instruktion i en `trap` instruktions lista, stoppar PowerShell funktionen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="e8e14-186">If you include a `break` statement in a `trap` statement list, PowerShell stops the function or script.</span></span> <span data-ttu-id="e8e14-187">Följande exempel funktion använder `break` nyckelordet i en `trap` instruktion:</span><span class="sxs-lookup"><span data-stu-id="e8e14-187">The following sample function uses the `break` keyword in a `trap` statement:</span></span>

```powershell
function break_example {
    trap {
        "Error trapped"
        break
    }
    1/$null
    "Function completed."
}

break_example
```

```Output
Error trapped
ParentContainsErrorRecordException:
Line |
   6 |      1/$null
     |      ~~~~~~~
     | Attempted to divide by zero.
```

<span data-ttu-id="e8e14-188">Eftersom `trap` instruktionen innehöll `break` nyckelordet, fortsätter inte funktionen att köras och raden "funktion slutförd" körs inte.</span><span class="sxs-lookup"><span data-stu-id="e8e14-188">Because the `trap` statement included the `break` keyword, the function does not continue to run, and the "Function completed" line is not run.</span></span>

<span data-ttu-id="e8e14-189">Om du inkluderar ett `continue` nyckelord i en `trap` instruktion, återupptar PowerShell efter instruktionen som orsakade felet, precis som det skulle utan `break` eller `continue` .</span><span class="sxs-lookup"><span data-stu-id="e8e14-189">If you include a `continue` keyword in a `trap` statement, PowerShell resumes after the statement that caused the error, just as it would without `break` or `continue`.</span></span> <span data-ttu-id="e8e14-190">Med `continue` nyckelordet, skriver PowerShell dock inte ett fel till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-190">With the `continue` keyword, however, PowerShell does not write an error to the error stream.</span></span>

<span data-ttu-id="e8e14-191">Följande exempel funktion använder `continue` nyckelordet i en `trap` instruktion:</span><span class="sxs-lookup"><span data-stu-id="e8e14-191">The following sample function uses the `continue` keyword in a `trap` statement:</span></span>

```powershell
function continue_example {
    trap {
        "Error trapped"
        continue
    }
    1/$null
    "Function completed."
}

continue_example
```

```Output
Error trapped
Function completed.
```

<span data-ttu-id="e8e14-192">Funktionen återupptas när felet har fångats och instruktionen "Function Completed" körs.</span><span class="sxs-lookup"><span data-stu-id="e8e14-192">The function resumes after the error is trapped, and the "Function completed" statement runs.</span></span> <span data-ttu-id="e8e14-193">Inget fel har skrivits till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-193">No error is written to the error stream.</span></span>

## <a name="notes"></a><span data-ttu-id="e8e14-194">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e8e14-194">Notes</span></span>

<span data-ttu-id="e8e14-195">`trap` -instruktioner ger ett enkelt sätt att se till att alla avslutande fel i ett omfång hanteras.</span><span class="sxs-lookup"><span data-stu-id="e8e14-195">`trap` statements provide a simple way to broadly ensure all terminating errors within a scope are handled.</span></span> <span data-ttu-id="e8e14-196">För mer detaljerad fel hantering använder du `try` / `catch` block där traps har definierats med hjälp av `catch` instruktioner.</span><span class="sxs-lookup"><span data-stu-id="e8e14-196">For more finer-grained error handling, use `try`/`catch` blocks where traps are defined using `catch` statements.</span></span> <span data-ttu-id="e8e14-197">`catch`Instruktionerna gäller endast koden i den associerade `try` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="e8e14-197">The `catch` statements only apply to the code inside the associated `try` statement.</span></span> <span data-ttu-id="e8e14-198">Mer information finns i [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span><span class="sxs-lookup"><span data-stu-id="e8e14-198">For more information, see [about_Try_Catch_Finally](about_Try_Catch_Finally.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8e14-199">Se även</span><span class="sxs-lookup"><span data-stu-id="e8e14-199">See also</span></span>

[<span data-ttu-id="e8e14-200">about_Break</span><span class="sxs-lookup"><span data-stu-id="e8e14-200">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="e8e14-201">about_Continue</span><span class="sxs-lookup"><span data-stu-id="e8e14-201">about_Continue</span></span>](about_Continue.md)

[<span data-ttu-id="e8e14-202">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="e8e14-202">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="e8e14-203">about_Throw</span><span class="sxs-lookup"><span data-stu-id="e8e14-203">about_Throw</span></span>](about_Throw.md)

[<span data-ttu-id="e8e14-204">about_Try_Catch_Finally</span><span class="sxs-lookup"><span data-stu-id="e8e14-204">about_Try_Catch_Finally</span></span>](about_Try_Catch_Finally.md)
