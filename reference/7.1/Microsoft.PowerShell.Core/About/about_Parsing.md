---
description: Beskriver hur PowerShell tolkar kommandon.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_parsing?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Parsing
ms.openlocfilehash: 7f68a1f29ecb6a4562ae9f9a024365a2b1744a79
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271286"
---
# <a name="about-parsing"></a><span data-ttu-id="bab59-104">Om parsning</span><span class="sxs-lookup"><span data-stu-id="bab59-104">About Parsing</span></span>

## <a name="short-description"></a><span data-ttu-id="bab59-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bab59-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bab59-106">Beskriver hur PowerShell tolkar kommandon.</span><span class="sxs-lookup"><span data-stu-id="bab59-106">Describes how PowerShell parses commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="bab59-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bab59-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="bab59-108">När du anger ett kommando i kommando tolken, avbryter PowerShell kommando texten till en serie segment som kallas _tokens_ och avgör sedan hur varje token ska tolkas.</span><span class="sxs-lookup"><span data-stu-id="bab59-108">When you enter a command at the command prompt, PowerShell breaks the command text into a series of segments called _tokens_ and then determines how to interpret each token.</span></span>

<span data-ttu-id="bab59-109">Om du till exempel skriver:</span><span class="sxs-lookup"><span data-stu-id="bab59-109">For example, if you type:</span></span>

```powershell
Write-Host book
```

<span data-ttu-id="bab59-110">PowerShell delar upp kommandot i två tokens `Write-Host` och `book` tolkar varje token oberoende av varandra med ett av två huvud tolknings lägen: uttrycks läge och argument läge.</span><span class="sxs-lookup"><span data-stu-id="bab59-110">PowerShell breaks the command into two tokens, `Write-Host` and `book`, and interprets each token independently using one of two major parsing modes: expression mode and argument mode.</span></span>

> [!NOTE]
> <span data-ttu-id="bab59-111">Som PowerShell parsar kommando inmatat det försöker matcha kommando namn med cmdletar eller interna körbara filer.</span><span class="sxs-lookup"><span data-stu-id="bab59-111">As PowerShell parses command input it tries to resolve the command names to cmdlets or native executables.</span></span> <span data-ttu-id="bab59-112">Om ett kommando namn inte har en exakt matchning, är PowerShell-prepends `Get-` till kommandot som standardverb.</span><span class="sxs-lookup"><span data-stu-id="bab59-112">If a command name does not have an exact match, PowerShell prepends `Get-` to the command as a default verb.</span></span> <span data-ttu-id="bab59-113">Till exempel tolkar PowerShell `Process` som `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="bab59-113">For example, PowerShell parses `Process` as `Get-Process`.</span></span> <span data-ttu-id="bab59-114">Vi rekommenderar inte att du använder den här funktionen av följande orsaker:</span><span class="sxs-lookup"><span data-stu-id="bab59-114">It's not recommended to use this feature for the following reasons:</span></span>
>
> - <span data-ttu-id="bab59-115">Det är ineffektivt.</span><span class="sxs-lookup"><span data-stu-id="bab59-115">It's inefficient.</span></span> <span data-ttu-id="bab59-116">Detta gör att PowerShell söker flera gånger.</span><span class="sxs-lookup"><span data-stu-id="bab59-116">This causes PowerShell to search multiple times.</span></span>
> - <span data-ttu-id="bab59-117">Externa program med samma namn löses först, så du kan inte köra avsedd cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bab59-117">External programs with the same name are resolved first, so you may not execute intended cmdlet.</span></span>
> - <span data-ttu-id="bab59-118">`Get-Help` och `Get-Command` känner inte igen verb-mindre namn.</span><span class="sxs-lookup"><span data-stu-id="bab59-118">`Get-Help` and `Get-Command` don't recognize verb-less names.</span></span>

### <a name="expression-mode"></a><span data-ttu-id="bab59-119">Uttrycks läge</span><span class="sxs-lookup"><span data-stu-id="bab59-119">Expression mode</span></span>

<span data-ttu-id="bab59-120">Uttrycks läget är avsett för att kombinera uttryck som krävs för värde manipulation i ett skript språk.</span><span class="sxs-lookup"><span data-stu-id="bab59-120">Expression mode is intended for combining expressions, required for value manipulation in a scripting language.</span></span> <span data-ttu-id="bab59-121">Uttryck är representationer av värden i PowerShell-syntax och kan vara enkla eller sammansatta, till exempel:</span><span class="sxs-lookup"><span data-stu-id="bab59-121">Expressions are representations of values in PowerShell syntax, and can be simple or composite, for example:</span></span>

<span data-ttu-id="bab59-122">Literala uttryck är direkt representationer av deras värden:</span><span class="sxs-lookup"><span data-stu-id="bab59-122">Literal expressions are direct representations of their values:</span></span> 

```powershell
'hello', 32
```

<span data-ttu-id="bab59-123">Variabel uttryck bär värdet för variabeln som de refererar till:</span><span class="sxs-lookup"><span data-stu-id="bab59-123">Variable expressions carry the value of the variable they reference:</span></span> 

```powershell
$x, $script:path
```
<span data-ttu-id="bab59-124">Operatorer kombinerar andra uttryck för utvärdering:</span><span class="sxs-lookup"><span data-stu-id="bab59-124">Operators combine other expressions for evaluation:</span></span> 

```powershell
- 12, -not $Quiet, 3 + 7, $input.Length -gt 1
```

- <span data-ttu-id="bab59-125">_Tecken Strängs litteraler_ måste finnas inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="bab59-125">_Character string literals_ must be contained in quotation marks.</span></span>
- <span data-ttu-id="bab59-126">_Siffror_ behandlas som numeriska värden i stället för en serie med tecken (om inte escapeas).</span><span class="sxs-lookup"><span data-stu-id="bab59-126">_Numbers_ are treated as numerical values rather than as a series of characters (unless escaped).</span></span>
- <span data-ttu-id="bab59-127">_Operatorer_ , inklusive unära operatorer som `-` och `-not` binära operatorer som `+` och `-gt` , tolkas som operatorer och tillämpar deras respektive åtgärder på argumenten (operander).</span><span class="sxs-lookup"><span data-stu-id="bab59-127">_Operators_ , including unary operators like `-` and `-not` and binary operators like `+` and `-gt`, are interpreted as operators and apply their respective operations on their arguments (operands).</span></span>
- <span data-ttu-id="bab59-128">_Attribut och konverterings uttryck_ tolkas som uttryck och tillämpas på underordnade uttryck, t. ex. `[int] '7'` .</span><span class="sxs-lookup"><span data-stu-id="bab59-128">_Attribute and conversion expressions_ are parsed as expressions and applied to subordinate expressions, e.g. `[int] '7'`.</span></span>
- <span data-ttu-id="bab59-129">_Variabel referenser_ utvärderas till sina värden, men _ihopbuntning_ (d.v.s. inklistring av förifyllda parameter uppsättningar) är förbjuden och orsakar ett parsningsfel.</span><span class="sxs-lookup"><span data-stu-id="bab59-129">_Variable references_ are evaluated to their values but _splatting_ (i.e. pasting prefilled parameter sets) is forbidden and causes a parser error.</span></span>
- <span data-ttu-id="bab59-130">Allt annat kommer att behandlas som ett kommando som ska anropas.</span><span class="sxs-lookup"><span data-stu-id="bab59-130">Anything else will be treated as a command to be invoked.</span></span>

### <a name="argument-mode"></a><span data-ttu-id="bab59-131">Argument läge</span><span class="sxs-lookup"><span data-stu-id="bab59-131">Argument mode</span></span>

<span data-ttu-id="bab59-132">Vid parsningen ser PowerShell först till att tolka inmatade som ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="bab59-132">When parsing, PowerShell first looks to interpret input as an expression.</span></span> <span data-ttu-id="bab59-133">Men när ett kommando anrop påträffas fortsätter parsningen i argument läge.</span><span class="sxs-lookup"><span data-stu-id="bab59-133">But when a command invocation is encountered, parsing continues in argument mode.</span></span>

<span data-ttu-id="bab59-134">Argument läget är utformat för att parsa argument och parametrar för kommandon i en gränssnitts miljö.</span><span class="sxs-lookup"><span data-stu-id="bab59-134">Argument mode is designed for parsing arguments and parameters for commands in a shell environment.</span></span> <span data-ttu-id="bab59-135">Alla inmatade värden behandlas som en expanderbar sträng om den inte använder någon av följande syntaxer:</span><span class="sxs-lookup"><span data-stu-id="bab59-135">All input is treated as an expandable string unless it uses one of the following syntaxes:</span></span>

- <span data-ttu-id="bab59-136">Dollar tecken ( `$` ) startar en variabel referens (endast om det följs av ett giltigt variabel namn, annars tolkas det som en del av den expanderbara strängen).</span><span class="sxs-lookup"><span data-stu-id="bab59-136">Dollar sign (`$`) begins a variable reference (only if it is followed by a valid variable name, otherwise it is interpreted as part of the expandable string).</span></span>
- <span data-ttu-id="bab59-137">Citat tecken ( `'` och `"` ) inleder sträng värden</span><span class="sxs-lookup"><span data-stu-id="bab59-137">Quotation marks (`'` and `"`) begin string values</span></span>
- <span data-ttu-id="bab59-138">Parenteser ( `(` och `)` ) avgränsning av nya uttryck.</span><span class="sxs-lookup"><span data-stu-id="bab59-138">Parentheses (`(` and `)`) demarcate new expressions.</span></span>
- <span data-ttu-id="bab59-139">Operatorn för under uttryck ( `$(` ... `)` ) avgränsnings av inbäddade uttryck.</span><span class="sxs-lookup"><span data-stu-id="bab59-139">Subexpression operator (`$(`…`)`) demarcates embedded expressions.</span></span>
- <span data-ttu-id="bab59-140">Klammerparenteser ( `{` och `}` ) avgränsning av nya skript block.</span><span class="sxs-lookup"><span data-stu-id="bab59-140">Braces (`{` and `}`) demarcate new script blocks.</span></span>
- <span data-ttu-id="bab59-141">Initialt vid inloggning ( `@` ) börjar uttrycks syntaxer som ihopbuntning ( `@args` ), matriser ( `@(1,2,3)` ) och hash-tabeller ( `@{a=1;b=2}` ).</span><span class="sxs-lookup"><span data-stu-id="bab59-141">Initial at sign (`@`) begins expression syntaxes such as splatting (`@args`), arrays (`@(1,2,3)`) and hash tables (`@{a=1;b=2}`).</span></span>
- <span data-ttu-id="bab59-142">Kommatecken ( `,` ) introducera listor som skickats som matriser, förutom när kommandot som ska anropas är ett internt program, i vilket fall de tolkas som en del av den expanderbara strängen.</span><span class="sxs-lookup"><span data-stu-id="bab59-142">Commas (`,`) introduce lists passed as arrays, except when the command to be called is a native application, in which case they are interpreted as part of the expandable string.</span></span> <span data-ttu-id="bab59-143">Inledande, efterföljande eller efterföljande kommatecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="bab59-143">Initial, consecutive or trailing commas are not supported.</span></span>

<!--
01234567890123456789012345678901234567890123456789012345678901234567890123456789
-->
<span data-ttu-id="bab59-144">Värdena för inbäddade uttryck konverteras till strängar.</span><span class="sxs-lookup"><span data-stu-id="bab59-144">Values of embedded expressions are converted to strings.</span></span>

<span data-ttu-id="bab59-145">Följande tabell innehåller flera exempel på värden som bearbetas i uttrycks läge och argument läge och utvärderingen av dessa värden.</span><span class="sxs-lookup"><span data-stu-id="bab59-145">The following table provides several examples of values processed in expression mode and argument mode and the evaluation of those values.</span></span> <span data-ttu-id="bab59-146">Vi antar att värdet för variabeln `a` är `4` .</span><span class="sxs-lookup"><span data-stu-id="bab59-146">We assume that the value of the variable `a` is `4`.</span></span>

|       <span data-ttu-id="bab59-147">Exempel</span><span class="sxs-lookup"><span data-stu-id="bab59-147">Example</span></span>        |    <span data-ttu-id="bab59-148">Läge</span><span class="sxs-lookup"><span data-stu-id="bab59-148">Mode</span></span>    |      <span data-ttu-id="bab59-149">Resultat</span><span class="sxs-lookup"><span data-stu-id="bab59-149">Result</span></span>       |
| -------------------- | ---------- | ----------------- |
| `2`                  | <span data-ttu-id="bab59-150">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-150">Expression</span></span> | <span data-ttu-id="bab59-151">2 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-151">2 (integer)</span></span>       |
| `` `2``              | <span data-ttu-id="bab59-152">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-152">Expression</span></span> | <span data-ttu-id="bab59-153">"2" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-153">"2" (command)</span></span>     |
| `echo 2`             | <span data-ttu-id="bab59-154">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-154">Expression</span></span> | <span data-ttu-id="bab59-155">2 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-155">2 (integer)</span></span>       |
| `2+2`                | <span data-ttu-id="bab59-156">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-156">Expression</span></span> | <span data-ttu-id="bab59-157">4 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-157">4 (integer)</span></span>       |
| `echo 2+2`           | <span data-ttu-id="bab59-158">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-158">Argument</span></span>   | <span data-ttu-id="bab59-159">"2 + 2" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-159">"2+2" (string)</span></span>    |
| `echo(2+2)`          | <span data-ttu-id="bab59-160">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-160">Expression</span></span> | <span data-ttu-id="bab59-161">4 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-161">4 (integer)</span></span>       |
| `$a`                 | <span data-ttu-id="bab59-162">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-162">Expression</span></span> | <span data-ttu-id="bab59-163">4 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-163">4 (integer)</span></span>       |
| `echo $a`            | <span data-ttu-id="bab59-164">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-164">Expression</span></span> | <span data-ttu-id="bab59-165">4 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-165">4 (integer)</span></span>       |
| `$a+2`               | <span data-ttu-id="bab59-166">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-166">Expression</span></span> | <span data-ttu-id="bab59-167">6 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-167">6 (integer)</span></span>       |
| `echo $a+2`          | <span data-ttu-id="bab59-168">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-168">Argument</span></span>   | <span data-ttu-id="bab59-169">4 + 2 (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-169">4+2 (string)</span></span>      |
| `$-`                 | <span data-ttu-id="bab59-170">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-170">Argument</span></span>   | <span data-ttu-id="bab59-171">"$-" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-171">"$-" (command)</span></span>    |
| `echo $-`            | <span data-ttu-id="bab59-172">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-172">Argument</span></span>   | <span data-ttu-id="bab59-173">"$-" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-173">"$-" (string)</span></span>     |
| `a$a`                | <span data-ttu-id="bab59-174">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-174">Expression</span></span> | <span data-ttu-id="bab59-175">"a $ a" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-175">"a$a" (command)</span></span>   |
| `echo a$a`           | <span data-ttu-id="bab59-176">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-176">Argument</span></span>   | <span data-ttu-id="bab59-177">"A4" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-177">"a4" (string)</span></span>     |
| `a'$a'`              | <span data-ttu-id="bab59-178">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-178">Expression</span></span> | <span data-ttu-id="bab59-179">"a $ a" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-179">"a$a" (command)</span></span>   |
| `echo a'$a'`         | <span data-ttu-id="bab59-180">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-180">Argument</span></span>   | <span data-ttu-id="bab59-181">"a $ a" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-181">"a$a" (string)</span></span>    |
| `a"$a"`              | <span data-ttu-id="bab59-182">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-182">Expression</span></span> | <span data-ttu-id="bab59-183">"a $ a" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-183">"a$a" (command)</span></span>   |
| `echo a"$a"`         | <span data-ttu-id="bab59-184">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-184">Argument</span></span>   | <span data-ttu-id="bab59-185">"A4" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-185">"a4" (string)</span></span>     |
| `a$(2)`              | <span data-ttu-id="bab59-186">Uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-186">Expression</span></span> | <span data-ttu-id="bab59-187">"a $ (2)" (kommando)</span><span class="sxs-lookup"><span data-stu-id="bab59-187">"a$(2)" (command)</span></span> |
| `echo a$(2)`         | <span data-ttu-id="bab59-188">Argument</span><span class="sxs-lookup"><span data-stu-id="bab59-188">Argument</span></span>   | <span data-ttu-id="bab59-189">"a2" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-189">"a2" (string)</span></span>     |

<span data-ttu-id="bab59-190">Varje token kan tolkas som en typ av objekt typ, till exempel Boolean eller String.</span><span class="sxs-lookup"><span data-stu-id="bab59-190">Every token can be interpreted as some kind of object type, such as Boolean or string.</span></span> <span data-ttu-id="bab59-191">PowerShell försöker fastställa objekt typen från uttrycket.</span><span class="sxs-lookup"><span data-stu-id="bab59-191">PowerShell attempts to determine the object type from the expression.</span></span>
<span data-ttu-id="bab59-192">Objekt typen beror på vilken typ av parameter ett kommando förväntar sig och på om PowerShell vet hur argumentet ska konverteras till rätt typ.</span><span class="sxs-lookup"><span data-stu-id="bab59-192">The object type depends on the type of parameter a command expects and on whether PowerShell knows how to convert the argument to the correct type.</span></span> <span data-ttu-id="bab59-193">I följande tabell visas flera exempel på de typer som tilldelats värden som returneras av uttrycken.</span><span class="sxs-lookup"><span data-stu-id="bab59-193">The following table shows several examples of the types assigned to values returned by the expressions.</span></span>

|       <span data-ttu-id="bab59-194">Exempel</span><span class="sxs-lookup"><span data-stu-id="bab59-194">Example</span></span>          |    <span data-ttu-id="bab59-195">Läge</span><span class="sxs-lookup"><span data-stu-id="bab59-195">Mode</span></span>    |     <span data-ttu-id="bab59-196">Resultat</span><span class="sxs-lookup"><span data-stu-id="bab59-196">Result</span></span>      |
| ---------------------- | ---------- | --------------- |
| `Write-Output !1`      | <span data-ttu-id="bab59-197">-argument</span><span class="sxs-lookup"><span data-stu-id="bab59-197">argument</span></span>   | <span data-ttu-id="bab59-198">"! 1" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-198">"!1" (string)</span></span>   |
| `Write-Output (!1)`    | <span data-ttu-id="bab59-199">uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-199">expression</span></span> | <span data-ttu-id="bab59-200">Falskt (boolesk)</span><span class="sxs-lookup"><span data-stu-id="bab59-200">False (Boolean)</span></span> |
| `Write-Output (2)`     | <span data-ttu-id="bab59-201">uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-201">expression</span></span> | <span data-ttu-id="bab59-202">2 (heltal)</span><span class="sxs-lookup"><span data-stu-id="bab59-202">2 (integer)</span></span>     |
| `Set-Variable AB A,B`  | <span data-ttu-id="bab59-203">-argument</span><span class="sxs-lookup"><span data-stu-id="bab59-203">argument</span></span>   | <span data-ttu-id="bab59-204">"A", "B" (matris)</span><span class="sxs-lookup"><span data-stu-id="bab59-204">'A','B' (array)</span></span> |
| `CMD /CECHO A,B`       | <span data-ttu-id="bab59-205">-argument</span><span class="sxs-lookup"><span data-stu-id="bab59-205">argument</span></span>   | <span data-ttu-id="bab59-206">"A, B" (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-206">'A,B' (string)</span></span>  |
| `CMD /CECHO $AB`       | <span data-ttu-id="bab59-207">uttryck</span><span class="sxs-lookup"><span data-stu-id="bab59-207">expression</span></span> | <span data-ttu-id="bab59-208">"A", "B" (matris)</span><span class="sxs-lookup"><span data-stu-id="bab59-208">'A','B' (array)</span></span> |
| `CMD /CECHO :$AB`      | <span data-ttu-id="bab59-209">-argument</span><span class="sxs-lookup"><span data-stu-id="bab59-209">argument</span></span>   | <span data-ttu-id="bab59-210">': A B ' (sträng)</span><span class="sxs-lookup"><span data-stu-id="bab59-210">':A B' (string)</span></span> |

<span data-ttu-id="bab59-211">Med stop parser-symbolen ( `--%` ) som introducerades i powershell 3,0, använder PowerShell för att undvika att tolka ininformation som PowerShell-kommandon eller uttryck.</span><span class="sxs-lookup"><span data-stu-id="bab59-211">The stop-parsing symbol (`--%`), introduced in PowerShell 3.0, directs PowerShell to refrain from interpreting input as PowerShell commands or expressions.</span></span>

<span data-ttu-id="bab59-212">När du anropar ett körbart program i PowerShell ska du placera stop-parser-symbolen före program argumenten.</span><span class="sxs-lookup"><span data-stu-id="bab59-212">When calling an executable program in PowerShell, place the stop-parsing symbol before the program arguments.</span></span> <span data-ttu-id="bab59-213">Den här metoden är mycket enklare än att använda escape-tecken för att förhindra feltolkning.</span><span class="sxs-lookup"><span data-stu-id="bab59-213">This technique is much easier than using escape characters to prevent misinterpretation.</span></span>

<span data-ttu-id="bab59-214">När den påträffar en stopp tolknings symbol behandlar PowerShell de återstående tecknen på raden som en litteral.</span><span class="sxs-lookup"><span data-stu-id="bab59-214">When it encounters a stop-parsing symbol, PowerShell treats the remaining characters in the line as a literal.</span></span> <span data-ttu-id="bab59-215">Den enda tolkning som det utför är att ersätta värden för miljövariabler som använder standard Windows-notation, t `%USERPROFILE%` . ex..</span><span class="sxs-lookup"><span data-stu-id="bab59-215">The only interpretation it performs is to substitute values for environment variables that use standard Windows notation, such as `%USERPROFILE%`.</span></span>

<span data-ttu-id="bab59-216">Den avparsande symbolen börjar bara gälla fram till nästa rad matning eller pipeline-tecken.</span><span class="sxs-lookup"><span data-stu-id="bab59-216">The stop-parsing symbol is effective only until the next newline or pipeline character.</span></span> <span data-ttu-id="bab59-217">Du kan inte använda ett fortsättnings tecken ( `` ` `` ) för att utöka dess inverkan eller använda en kommando avgränsare ( `;` ) för att avsluta dess funktion.</span><span class="sxs-lookup"><span data-stu-id="bab59-217">You cannot use a continuation character (`` ` ``) to extend its effect or use a command delimiter (`;`) to terminate its effect.</span></span>

<span data-ttu-id="bab59-218">Till exempel anropar följande kommando **icacls** -programmet.</span><span class="sxs-lookup"><span data-stu-id="bab59-218">For example, the following command calls the **Icacls** program.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="bab59-219">Om du vill köra det här kommandot i PowerShell 2,0 måste du använda escape-tecken för att förhindra att PowerShell tolkar en parentes.</span><span class="sxs-lookup"><span data-stu-id="bab59-219">To run this command in PowerShell 2.0, you must use escape characters to prevent PowerShell from misinterpreting the parentheses.</span></span>

```powershell
icacls X:\VMS /grant Dom\HVAdmin:`(CI`)`(OI`)F
```

<span data-ttu-id="bab59-220">Från och med PowerShell 3,0 kan du använda Stop-parser-symbolen.</span><span class="sxs-lookup"><span data-stu-id="bab59-220">Beginning in PowerShell 3.0, you can use the stop-parsing symbol.</span></span>

```powershell
icacls X:\VMS --% /grant Dom\HVAdmin:(CI)(OI)F
```

<span data-ttu-id="bab59-221">PowerShell skickar följande kommando sträng till **icacls** -programmet:</span><span class="sxs-lookup"><span data-stu-id="bab59-221">PowerShell sends the following command string to the **Icacls** program:</span></span>

`X:\VMS /grant Dom\HVAdmin:(CI)(OI)F`

> [!NOTE]
> <span data-ttu-id="bab59-222">Avtolknings symbolen är endast avsedd för användning på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="bab59-222">The stop-parsing symbol only intended for use on Windows platforms.</span></span>

## <a name="see-also"></a><span data-ttu-id="bab59-223">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="bab59-223">SEE ALSO</span></span>

[<span data-ttu-id="bab59-224">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="bab59-224">about_Command_Syntax</span></span>](about_Command_Syntax.md)
