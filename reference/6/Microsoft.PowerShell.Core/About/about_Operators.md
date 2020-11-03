---
description: Beskriver de operatorer som stöds av PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/28/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operators
ms.openlocfilehash: 9668e635b17f8cbe9f6639e8a13b95d4b9387fbb
ms.sourcegitcommit: c1e4739f5d52282fb05a8cff92b0f5d10e2edac1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/29/2020
ms.locfileid: "93273506"
---
# <a name="about-operators"></a><span data-ttu-id="dc173-104">Om operatörer</span><span class="sxs-lookup"><span data-stu-id="dc173-104">About Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="dc173-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc173-105">Short description</span></span>
<span data-ttu-id="dc173-106">Beskriver de operatorer som stöds av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc173-106">Describes the operators that are supported by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="dc173-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc173-107">Long description</span></span>

<span data-ttu-id="dc173-108">En operator är ett språk element som du kan använda i ett kommando eller uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-108">An operator is a language element that you can use in a command or expression.</span></span>
<span data-ttu-id="dc173-109">PowerShell stöder flera typer av operatorer som hjälper dig att hantera värden.</span><span class="sxs-lookup"><span data-stu-id="dc173-109">PowerShell supports several types of operators to help you manipulate values.</span></span>

### <a name="arithmetic-operators"></a><span data-ttu-id="dc173-110">Aritmetiska operatorer</span><span class="sxs-lookup"><span data-stu-id="dc173-110">Arithmetic Operators</span></span>

<span data-ttu-id="dc173-111">Använd aritmetiska operatorer ( `+` , `-` ,, `*` `/` , `%` ) för att beräkna värden i ett kommando eller uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-111">Use arithmetic operators (`+`, `-`, `*`, `/`, `%`) to calculate values in a command or expression.</span></span> <span data-ttu-id="dc173-112">Med dessa operatörer kan du lägga till, subtrahera, multiplicera eller dividera värden och beräkna resten (Modulus) för en divisions åtgärd.</span><span class="sxs-lookup"><span data-stu-id="dc173-112">With these operators, you can add, subtract, multiply, or divide values, and calculate the remainder (modulus) of a division operation.</span></span>

<span data-ttu-id="dc173-113">Operatorn addition sammanfogar element.</span><span class="sxs-lookup"><span data-stu-id="dc173-113">The addition operator concatenates elements.</span></span> <span data-ttu-id="dc173-114">Operatorn multiplikation returnerar det angivna antalet kopior av varje element.</span><span class="sxs-lookup"><span data-stu-id="dc173-114">The multiplication operator returns the specified number of copies of each element.</span></span> <span data-ttu-id="dc173-115">Du kan använda aritmetiska operatorer på vilken .net-typ som helst som implementerar dem, till exempel: `Int` , `String` ,, `DateTime` `Hashtable` , och matriser.</span><span class="sxs-lookup"><span data-stu-id="dc173-115">You can use arithmetic operators on any .NET type that implements them, such as: `Int`, `String`, `DateTime`, `Hashtable`, and Arrays.</span></span>

<span data-ttu-id="dc173-116">Bitvisa operatorer (,,,, `-band` `-bor` `-bxor` `-bnot` `-shl` `-shr` ) ändrar bit mönstren i värden.</span><span class="sxs-lookup"><span data-stu-id="dc173-116">Bitwise operators (`-band`, `-bor`, `-bxor`, `-bnot`, `-shl`, `-shr`) manipulate the bit patterns in values.</span></span>

<span data-ttu-id="dc173-117">Mer information finns i [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-117">For more information, see [about_Arithmetic_Operators](about_Arithmetic_Operators.md).</span></span>

### <a name="assignment-operators"></a><span data-ttu-id="dc173-118">Tilldelnings operatörer</span><span class="sxs-lookup"><span data-stu-id="dc173-118">Assignment Operators</span></span>

<span data-ttu-id="dc173-119">Använd tilldelnings operatörer ( `=` ,,,, `+=` `-=` `*=` `/=` `%=` ) för att tilldela, ändra eller lägga till värden för variabler.</span><span class="sxs-lookup"><span data-stu-id="dc173-119">Use assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`) to assign, change, or append values to variables.</span></span> <span data-ttu-id="dc173-120">Du kan kombinera aritmetiska operatorer med tilldelning för att tilldela resultatet av den aritmetiska åtgärden till en variabel.</span><span class="sxs-lookup"><span data-stu-id="dc173-120">You can combine arithmetic operators with assignment to assign the result of the arithmetic operation to a variable.</span></span>

<span data-ttu-id="dc173-121">Mer information finns i [about_Assignment_Operators](about_Assignment_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-121">For more information, see [about_Assignment_Operators](about_Assignment_Operators.md).</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="dc173-122">Jämförelseoperatorer</span><span class="sxs-lookup"><span data-stu-id="dc173-122">Comparison Operators</span></span>

<span data-ttu-id="dc173-123">Använd jämförelse operatorer ( `-eq` ,,,, `-ne` `-gt` `-lt` `-le` `-ge` ) för att jämföra värden och test villkor.</span><span class="sxs-lookup"><span data-stu-id="dc173-123">Use comparison operators (`-eq`, `-ne`, `-gt`, `-lt`, `-le`, `-ge`) to compare values and test conditions.</span></span> <span data-ttu-id="dc173-124">Du kan till exempel jämföra två sträng värden för att avgöra om de är lika.</span><span class="sxs-lookup"><span data-stu-id="dc173-124">For example, you can compare two string values to determine whether they are equal.</span></span>

<span data-ttu-id="dc173-125">Jämförelse operatorerna innehåller också operatorer som söker efter eller ersätter mönster i text.</span><span class="sxs-lookup"><span data-stu-id="dc173-125">The comparison operators also include operators that find or replace patterns in text.</span></span> <span data-ttu-id="dc173-126">`-match` `-notmatch` Operatorerna (,, `-replace` ) använder reguljära uttryck och ( `-like` , `-notlike` ) använder jokertecken `*` .</span><span class="sxs-lookup"><span data-stu-id="dc173-126">The (`-match`, `-notmatch`, `-replace`) operators use regular expressions, and (`-like`, `-notlike`) use wildcards `*`.</span></span>

<span data-ttu-id="dc173-127">Jämförelse operatorer för inne slutning avgör om ett testvärde visas i en referens uppsättning ( `-in` ,, `-notin` `-contains` , `-notcontains` ).</span><span class="sxs-lookup"><span data-stu-id="dc173-127">Containment comparison operators determine whether a test value appears in a reference set (`-in`, `-notin`, `-contains`, `-notcontains`).</span></span>

<span data-ttu-id="dc173-128">Skriv jämförelse operatorer ( `-is` , `-isnot` ) för att avgöra om ett objekt är av en specifik typ.</span><span class="sxs-lookup"><span data-stu-id="dc173-128">Type comparison operators (`-is`, `-isnot`) determine whether an object is of a given type.</span></span>

<span data-ttu-id="dc173-129">Mer information finns i [about_Comparison_Operators](about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-129">For more information, see [about_Comparison_Operators](about_Comparison_Operators.md).</span></span>

### <a name="logical-operators"></a><span data-ttu-id="dc173-130">Logiska operatorer</span><span class="sxs-lookup"><span data-stu-id="dc173-130">Logical Operators</span></span>

<span data-ttu-id="dc173-131">Använd logiska operatorer (,,, `-and` `-or` `-xor` `-not` , `!` ) för att ansluta villkorliga uttryck till ett enda komplext villkor.</span><span class="sxs-lookup"><span data-stu-id="dc173-131">Use logical operators (`-and`, `-or`, `-xor`, `-not`, `!`) to connect conditional statements into a single complex conditional.</span></span> <span data-ttu-id="dc173-132">Du kan till exempel använda en logisk `-and` operator för att skapa ett objekt filter med två olika villkor.</span><span class="sxs-lookup"><span data-stu-id="dc173-132">For example, you can use a logical `-and` operator to create an object filter with two different conditions.</span></span>

<span data-ttu-id="dc173-133">Mer information finns i [about_Logical_Operators](about_logical_operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-133">For more information, see [about_Logical_Operators](about_logical_operators.md).</span></span>

### <a name="redirection-operators"></a><span data-ttu-id="dc173-134">Operatorer för omdirigering</span><span class="sxs-lookup"><span data-stu-id="dc173-134">Redirection Operators</span></span>

<span data-ttu-id="dc173-135">Använd omdirigerings operatorer (,,, `>` `>>` `2>` `2>>` och `2>&1` ) för att skicka utdata från ett kommando eller uttryck till en textfil.</span><span class="sxs-lookup"><span data-stu-id="dc173-135">Use redirection operators (`>`, `>>`, `2>`, `2>>`, and `2>&1`) to send the output of a command or expression to a text file.</span></span> <span data-ttu-id="dc173-136">Operatorerna för omdirigering fungerar som `Out-File` cmdlet (utan parametrar), men de låter dig också omdirigera fel utdata till angivna filer.</span><span class="sxs-lookup"><span data-stu-id="dc173-136">The redirection operators work like the `Out-File` cmdlet (without parameters) but they also let you redirect error output to specified files.</span></span> <span data-ttu-id="dc173-137">Du kan också använda `Tee-Object` cmdleten för att dirigera om utdata.</span><span class="sxs-lookup"><span data-stu-id="dc173-137">You can also use the `Tee-Object` cmdlet to redirect output.</span></span>

<span data-ttu-id="dc173-138">Mer information finns i [about_Redirection](about_Redirection.md)</span><span class="sxs-lookup"><span data-stu-id="dc173-138">For more information, see [about_Redirection](about_Redirection.md)</span></span>

### <a name="split-and-join-operators"></a><span data-ttu-id="dc173-139">Dela och koppla operatörer</span><span class="sxs-lookup"><span data-stu-id="dc173-139">Split and Join Operators</span></span>

<span data-ttu-id="dc173-140">`-split` `-join` Operatorerna och delar upp och kombinerar del strängar.</span><span class="sxs-lookup"><span data-stu-id="dc173-140">The `-split` and `-join` operators divide and combine substrings.</span></span> <span data-ttu-id="dc173-141">`-split`Operatorn delar en sträng i del strängar.</span><span class="sxs-lookup"><span data-stu-id="dc173-141">The `-split` operator splits a string into substrings.</span></span> <span data-ttu-id="dc173-142">`-join`Operatorn sammanfogar flera strängar till en enda sträng.</span><span class="sxs-lookup"><span data-stu-id="dc173-142">The `-join` operator concatenates multiple strings into a single string.</span></span>

<span data-ttu-id="dc173-143">Mer information finns i [about_Split](about_Split.md) och [about_Join](about_Join.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-143">For more information, see [about_Split](about_Split.md) and [about_Join](about_Join.md).</span></span>

### <a name="type-operators"></a><span data-ttu-id="dc173-144">Typ operatörer</span><span class="sxs-lookup"><span data-stu-id="dc173-144">Type Operators</span></span>

<span data-ttu-id="dc173-145">Använd typ operatorer ( `-is` , `-isnot` , `-as` ) för att söka efter eller ändra .NET Framework typ för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="dc173-145">Use the type operators (`-is`, `-isnot`, `-as`) to find or change the .NET Framework type of an object.</span></span>

<span data-ttu-id="dc173-146">Mer information finns i [about_Type_Operators](about_Type_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-146">For more information, see [about_Type_Operators](about_Type_Operators.md).</span></span>

### <a name="unary-operators"></a><span data-ttu-id="dc173-147">Unära operatorer</span><span class="sxs-lookup"><span data-stu-id="dc173-147">Unary Operators</span></span>

<span data-ttu-id="dc173-148">Använd unära operatorer för att öka eller minska variabler eller objekt egenskaper och ange heltal till positiva eller negativa tal.</span><span class="sxs-lookup"><span data-stu-id="dc173-148">Use unary operators to increment or decrement variables or object properties and to set integers to positive or negative numbers.</span></span> <span data-ttu-id="dc173-149">Om du till exempel vill öka variabeln `$a` från `9` till `10` skriver du `$a++` .</span><span class="sxs-lookup"><span data-stu-id="dc173-149">For example, to increment the variable `$a` from `9` to `10`, you type `$a++`.</span></span>

### <a name="special-operators"></a><span data-ttu-id="dc173-150">Särskilda operatörer</span><span class="sxs-lookup"><span data-stu-id="dc173-150">Special Operators</span></span>

<span data-ttu-id="dc173-151">Särskilda operatörer har specifika användnings fall som inte passar in i någon annan operator grupp.</span><span class="sxs-lookup"><span data-stu-id="dc173-151">Special operators have specific use-cases that do not fit into any other operator group.</span></span> <span data-ttu-id="dc173-152">Med särskilda operatorer kan du till exempel köra kommandon, ändra värdens datatyp eller hämta element från en matris.</span><span class="sxs-lookup"><span data-stu-id="dc173-152">For example, special operators allow you to run commands, change a value's data type, or retrieve elements from an array.</span></span>

#### <a name="grouping-operator--"></a><span data-ttu-id="dc173-153">Grupp operator `( )`</span><span class="sxs-lookup"><span data-stu-id="dc173-153">Grouping operator `( )`</span></span>

<span data-ttu-id="dc173-154">Precis som på andra språk, kan det `(...)` vara så att operator prioriteten åsidosätts i uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-154">As in other languages, `(...)` serves to override operator precedence in expressions.</span></span> <span data-ttu-id="dc173-155">Exempelvis: `(1 + 2) / 3`</span><span class="sxs-lookup"><span data-stu-id="dc173-155">For example: `(1 + 2) / 3`</span></span>

<span data-ttu-id="dc173-156">I PowerShell finns det dock ytterligare beteenden.</span><span class="sxs-lookup"><span data-stu-id="dc173-156">However, in PowerShell, there are additional behaviors.</span></span>

- <span data-ttu-id="dc173-157">`(...)` gör att du kan låta utdata från ett _kommando_ delta i ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-157">`(...)` allows you to let output from a _command_ participate in an expression.</span></span> <span data-ttu-id="dc173-158">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="dc173-158">For example:</span></span>

  ```powershell
  PS> (Get-Item *.txt).Count -gt 10
  True
  ```

- <span data-ttu-id="dc173-159">När det används som det första segmentet i en pipeline, kan ett kommando eller uttryck i parentes orsaka _uppräkning_ av uttryck resultatet.</span><span class="sxs-lookup"><span data-stu-id="dc173-159">When used as the first segment of a pipeline, wrapping a command or expression in parentheses invariably causes _enumeration_ of the expression result.</span></span> <span data-ttu-id="dc173-160">Om parentesen radbryter ett _kommando_ körs det för att slutföras med alla utdata _som samlats in i minnet_ innan resultatet skickas via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="dc173-160">If the parentheses wrap a _command_ , it is run to completion with all output _collected in memory_ before the results are sent through the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="dc173-161">Att omsluta ett kommando inom parenteser gör att den automatiska variabeln `$?` ställs in på `$true` , även när själva kommandot är inställt `$?` på `$false` .</span><span class="sxs-lookup"><span data-stu-id="dc173-161">Wrapping a command in parentheses causes the automatic variable `$?` to be set to `$true`, even when the enclosed command itself set `$?` to `$false`.</span></span>
> <span data-ttu-id="dc173-162">Till exempel `(Get-Item /Nosuch); $?` ger den oväntade avkastningen **True**.</span><span class="sxs-lookup"><span data-stu-id="dc173-162">For example, `(Get-Item /Nosuch); $?` unexpectedly yields **True**.</span></span> <span data-ttu-id="dc173-163">Mer information om `$?` finns i [about_Automatic_Variables](about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-163">For more information about `$?`, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

#### <a name="subexpression-operator--"></a><span data-ttu-id="dc173-164">Operator för under uttryck `$( )`</span><span class="sxs-lookup"><span data-stu-id="dc173-164">Subexpression operator `$( )`</span></span>

<span data-ttu-id="dc173-165">Returnerar resultatet av en eller flera instruktioner.</span><span class="sxs-lookup"><span data-stu-id="dc173-165">Returns the result of one or more statements.</span></span> <span data-ttu-id="dc173-166">Returnerar en skalär för ett enda resultat.</span><span class="sxs-lookup"><span data-stu-id="dc173-166">For a single result, returns a scalar.</span></span> <span data-ttu-id="dc173-167">Returnerar en matris för flera resultat.</span><span class="sxs-lookup"><span data-stu-id="dc173-167">For multiple results, returns an array.</span></span> <span data-ttu-id="dc173-168">Använd det här när du vill använda ett uttryck i ett annat uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-168">Use this when you want to use an expression within another expression.</span></span> <span data-ttu-id="dc173-169">Till exempel för att bädda in resultatet av kommandot i ett sträng uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-169">For example, to embed the results of command in a string expression.</span></span>

```powershell
PS> "Today is $(Get-Date)"
Today is 12/02/2019 13:15:20

PS> "Folder list: $((dir c:\ -dir).Name -join ', ')"
Folder list: Program Files, Program Files (x86), Users, Windows
```

#### <a name="array-subexpression-operator--"></a><span data-ttu-id="dc173-170">Array-underexpress operator `@( )`</span><span class="sxs-lookup"><span data-stu-id="dc173-170">Array subexpression operator `@( )`</span></span>

<span data-ttu-id="dc173-171">Returnerar resultatet av en eller flera uttryck som en matris.</span><span class="sxs-lookup"><span data-stu-id="dc173-171">Returns the result of one or more statements as an array.</span></span> <span data-ttu-id="dc173-172">Om det bara finns ett objekt har matrisen bara en medlem.</span><span class="sxs-lookup"><span data-stu-id="dc173-172">If there is only one item, the array has only one member.</span></span>

```powershell
@(Get-CimInstance win32_logicalDisk)
```

#### <a name="call-operator-"></a><span data-ttu-id="dc173-173">Anrops operator `&`</span><span class="sxs-lookup"><span data-stu-id="dc173-173">Call operator `&`</span></span>

<span data-ttu-id="dc173-174">Kör ett kommando, ett skript eller ett skript block.</span><span class="sxs-lookup"><span data-stu-id="dc173-174">Runs a command, script, or script block.</span></span> <span data-ttu-id="dc173-175">Anrops operatorn, som även kallas "anrops operatorn", gör att du kan köra kommandon som lagras i variabler och som representeras av strängar eller skript block.</span><span class="sxs-lookup"><span data-stu-id="dc173-175">The call operator, also known as the "invocation operator", lets you run commands that are stored in variables and represented by strings or script blocks.</span></span> <span data-ttu-id="dc173-176">Anrops operatorn körs i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="dc173-176">The call operator executes in a child scope.</span></span> <span data-ttu-id="dc173-177">Mer information om omfattningar finns [about_Scopes](about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-177">For more about scopes, see [about_Scopes](about_Scopes.md).</span></span>

<span data-ttu-id="dc173-178">Det här exemplet lagrar ett kommando i en sträng och kör det med hjälp av anrops operatorn.</span><span class="sxs-lookup"><span data-stu-id="dc173-178">This example stores a command in a string and executes it using the call operator.</span></span>

```
PS> $c = "get-executionpolicy"
PS> $c
get-executionpolicy
PS> & $c
AllSigned
```

<span data-ttu-id="dc173-179">Anrops operatorn tolkar inte strängar.</span><span class="sxs-lookup"><span data-stu-id="dc173-179">The call operator does not parse strings.</span></span> <span data-ttu-id="dc173-180">Det innebär att du inte kan använda kommando parametrar i en sträng när du använder anrops operatorn.</span><span class="sxs-lookup"><span data-stu-id="dc173-180">This means that you cannot use command parameters within a string when you use the call operator.</span></span>

```
PS> $c = "Get-Service -Name Spooler"
PS> $c
Get-Service -Name Spooler
PS> & $c
& : The term 'Get-Service -Name Spooler' is not recognized as the name of a
cmdlet, function, script file, or operable program. Check the spelling of
the name, or if a path was included, verify that the path is correct and
try again.
At line:1 char:2
+ & $c
+  ~~
    + CategoryInfo          : ObjectNotFound: (Get-Service -Name Spooler:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

<span data-ttu-id="dc173-181">Cmdleten [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) kan köra kod som orsakar tolkning av fel när anrops operatorn används.</span><span class="sxs-lookup"><span data-stu-id="dc173-181">The [Invoke-Expression](xref:Microsoft.PowerShell.Utility.Invoke-Expression) cmdlet can execute code that causes parsing errors when using the call operator.</span></span>

```
PS> & "1+1"
& : The term '1+1' is not recognized as the name of a cmdlet, function, script
file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:2
+ & "1+1"
+  ~~~~~
    + CategoryInfo          : ObjectNotFound: (1+1:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
PS> Invoke-Expression "1+1"
2
```

<span data-ttu-id="dc173-182">Du kan använda anrops operatorn för att köra skript med sina fil namn.</span><span class="sxs-lookup"><span data-stu-id="dc173-182">You can use the call operator to execute scripts using their filenames.</span></span> <span data-ttu-id="dc173-183">I exemplet nedan visas ett skript fil namn som innehåller blank steg.</span><span class="sxs-lookup"><span data-stu-id="dc173-183">The example below shows a script filename that contains spaces.</span></span> <span data-ttu-id="dc173-184">När du försöker köra skriptet visar PowerShell i stället innehållet i den citerade strängen som innehåller fil namnet.</span><span class="sxs-lookup"><span data-stu-id="dc173-184">When you try to execute the script, PowerShell instead displays the contents of the quoted string containing the filename.</span></span> <span data-ttu-id="dc173-185">Med anrops operatorn kan du köra innehållet i strängen som innehåller fil namnet.</span><span class="sxs-lookup"><span data-stu-id="dc173-185">The call operator allows you to execute the contents of the string containing the filename.</span></span>

```
PS C:\Scripts> Get-ChildItem

    Directory: C:\Scripts


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        8/28/2018   1:36 PM             58 script name with spaces.ps1

PS C:\Scripts> ".\script name with spaces.ps1"
.\script name with spaces.ps1
PS C:\Scripts> & ".\script name with spaces.ps1"
Hello World!
```

<span data-ttu-id="dc173-186">Mer information om skript block finns [about_Script_Blocks](about_Script_Blocks.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-186">For more about script blocks, see [about_Script_Blocks](about_Script_Blocks.md).</span></span>

#### <a name="background-operator-"></a><span data-ttu-id="dc173-187">Bakgrunds operator `&`</span><span class="sxs-lookup"><span data-stu-id="dc173-187">Background operator `&`</span></span>

<span data-ttu-id="dc173-188">Kör pipelinen före den i bakgrunden i ett PowerShell-jobb.</span><span class="sxs-lookup"><span data-stu-id="dc173-188">Runs the pipeline before it in the background, in a PowerShell job.</span></span> <span data-ttu-id="dc173-189">Den här operatorn fungerar på samma sätt som UNIX-kontrollens et-tecken ( `&` ), som kör kommandot innan det asynkront i undergränssnittet som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="dc173-189">This operator acts similarly to the UNIX control operator ampersand (`&`), which runs the command before it asynchronously in subshell as a job.</span></span>

<span data-ttu-id="dc173-190">Den här operatorn är funktions motsvarighet till `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dc173-190">This operator is functionally equivalent to `Start-Job`.</span></span> <span data-ttu-id="dc173-191">Följande exempel visar grundläggande användning av bakgrunds jobb operatören.</span><span class="sxs-lookup"><span data-stu-id="dc173-191">The following example demonstrates basic usage of the background job operator.</span></span>

```powershell
Get-Process -Name pwsh &
```

<span data-ttu-id="dc173-192">Kommandot fungerar som likvärdigt med följande användning av `Start-Job` :</span><span class="sxs-lookup"><span data-stu-id="dc173-192">That command is functionally equivalent to the following usage of `Start-Job`:</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process -Name pwsh}
```

<span data-ttu-id="dc173-193">Precis som `Start-Job` måste `&` bakgrunds operatorn returnera ett `Job` objekt.</span><span class="sxs-lookup"><span data-stu-id="dc173-193">Just like `Start-Job`, the `&` background operator returns a `Job` object.</span></span> <span data-ttu-id="dc173-194">Det här objektet kan användas med `Receive-Job` och `Remove-Job` , precis som om du hade använt `Start-Job` för att starta jobbet.</span><span class="sxs-lookup"><span data-stu-id="dc173-194">This object can be used with `Receive-Job` and `Remove-Job`, just as if you had used `Start-Job` to start the job.</span></span>

```powershell
$job = Get-Process -Name pwsh &
Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

```powershell
Remove-Job $job
```

<span data-ttu-id="dc173-195">`&`Bakgrunds operatorn är också en avslutnings instruktion, precis som UNIX-kontrollens et-tecken ( `&` ).</span><span class="sxs-lookup"><span data-stu-id="dc173-195">The `&` background operator is also a statement terminator, just like the UNIX control operator ampersand (`&`).</span></span> <span data-ttu-id="dc173-196">På så sätt kan du anropa ytterligare kommandon efter `&` bakgrunds operatorn.</span><span class="sxs-lookup"><span data-stu-id="dc173-196">This allows you to invoke additional commands after the `&` background operator.</span></span> <span data-ttu-id="dc173-197">I följande exempel demonstreras anropet av ytterligare kommandon efter `&` bakgrunds operatorn.</span><span class="sxs-lookup"><span data-stu-id="dc173-197">The following example demonstrates the invocation of additional commands after the `&` background operator.</span></span>

```powershell
$job = Get-Process -Name pwsh & Receive-Job $job -Wait
```

```Output

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
      0     0.00     221.16      25.90    6988 988 pwsh
      0     0.00     140.12      29.87   14845 845 pwsh
      0     0.00      85.51       0.91   19639 988 pwsh

```

<span data-ttu-id="dc173-198">Detta motsvarar följande skript:</span><span class="sxs-lookup"><span data-stu-id="dc173-198">This is equivalent to the following script:</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process -Name pwsh}
Receive-Job $job -Wait
```

<span data-ttu-id="dc173-199">Om du vill köra flera kommandon, var och en i sin egen bakgrunds process men på en rad, placerar du bara `&` mellan och efter vart och ett av kommandona.</span><span class="sxs-lookup"><span data-stu-id="dc173-199">If you want to run multiple commands, each in their own background process but all on one line, simply place `&` between and after each of the commands.</span></span>

```powershell
Get-Process -Name pwsh & Get-Service -Name BITS & Get-CimInstance -ClassName Win32_ComputerSystem &
```

<span data-ttu-id="dc173-200">Mer information om PowerShell-jobb finns [about_Jobs](about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-200">For more information on PowerShell jobs, see [about_Jobs](about_Jobs.md).</span></span>

#### <a name="cast-operator--"></a><span data-ttu-id="dc173-201">Omvandlings operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="dc173-201">Cast operator `[ ]`</span></span>

<span data-ttu-id="dc173-202">Konverterar eller begränsar objekt till den angivna typen.</span><span class="sxs-lookup"><span data-stu-id="dc173-202">Converts or limits objects to the specified type.</span></span> <span data-ttu-id="dc173-203">Om objekten inte kan konverteras genererar PowerShell ett fel.</span><span class="sxs-lookup"><span data-stu-id="dc173-203">If the objects cannot be converted, PowerShell generates an error.</span></span>

```powershell
[DateTime]"2/20/88" - [DateTime]"1/20/88"
[Int] (7/2)
[String] 1 + 0
[Int] '1' + 0
```

<span data-ttu-id="dc173-204">En omvandling kan också utföras när en variabel tilldelas till att använda [Cast notation](about_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dc173-204">A cast can also be performed when a variable is assigned to using [cast notation](about_Variables.md).</span></span>

#### <a name="comma-operator-"></a><span data-ttu-id="dc173-205">Komma-operator `,`</span><span class="sxs-lookup"><span data-stu-id="dc173-205">Comma operator `,`</span></span>

<span data-ttu-id="dc173-206">Som en binär operator skapar kommatecknet en matris eller lägger till i matrisen som skapas.</span><span class="sxs-lookup"><span data-stu-id="dc173-206">As a binary operator, the comma creates an array or appends to the array being created.</span></span> <span data-ttu-id="dc173-207">I uttrycks läge, som en unär operator, skapar kommatecknet en matris med bara en medlem.</span><span class="sxs-lookup"><span data-stu-id="dc173-207">In expression mode, as a unary operator, the comma creates an array with just one member.</span></span> <span data-ttu-id="dc173-208">Placera kommatecknet före medlemmen.</span><span class="sxs-lookup"><span data-stu-id="dc173-208">Place the comma before the member.</span></span>

```powershell
$myArray = 1,2,3
$SingleArray = ,1
Write-Output (,1)
```

<span data-ttu-id="dc173-209">Eftersom `Write-Object` ett argument förväntas måste du ange uttrycket inom parentes.</span><span class="sxs-lookup"><span data-stu-id="dc173-209">Since `Write-Object` expects an argument, you must put the expression in parentheses.</span></span>

#### <a name="dot-sourcing-operator-"></a><span data-ttu-id="dc173-210">Punkt källa-operator `.`</span><span class="sxs-lookup"><span data-stu-id="dc173-210">Dot sourcing operator `.`</span></span>

<span data-ttu-id="dc173-211">Kör ett skript i det aktuella omfånget så att alla funktioner, alias och variabler som skriptet skapar läggs till i det aktuella omfånget, vilket åsidosätter befintliga.</span><span class="sxs-lookup"><span data-stu-id="dc173-211">Runs a script in the current scope so that any functions, aliases, and variables that the script creates are added to the current scope, overriding existing ones.</span></span> <span data-ttu-id="dc173-212">Parametrar som deklareras av skriptet blir variabler.</span><span class="sxs-lookup"><span data-stu-id="dc173-212">Parameters declared by the script become variables.</span></span> <span data-ttu-id="dc173-213">Parametrar för vilka inget värde har angetts blir variabler utan värde.</span><span class="sxs-lookup"><span data-stu-id="dc173-213">Parameters for which no value has been given become variables with no value.</span></span> <span data-ttu-id="dc173-214">Den automatiska variabeln `$args` bevaras dock.</span><span class="sxs-lookup"><span data-stu-id="dc173-214">However, the automatic variable `$args` is preserved.</span></span>

```powershell
. c:\scripts\sample.ps1 1 2 -Also:3
```

> [!NOTE]
> <span data-ttu-id="dc173-215">Operatorn punkt källa följs av ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="dc173-215">The dot sourcing operator is followed by a space.</span></span> <span data-ttu-id="dc173-216">Använd utrymmet för att skilja pricken från den punkt ( `.` ) symbol som representerar den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="dc173-216">Use the space to distinguish the dot from the dot (`.`) symbol that represents the current directory.</span></span>
>
> <span data-ttu-id="dc173-217">I följande exempel körs Sample.ps1-skriptet i den aktuella katalogen i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="dc173-217">In the following example, the Sample.ps1 script in the current directory is run in the current scope.</span></span>
>
> ```powershell
> . .\sample.ps1
> ```

#### <a name="format-operator--f"></a><span data-ttu-id="dc173-218">Format operator `-f`</span><span class="sxs-lookup"><span data-stu-id="dc173-218">Format operator `-f`</span></span>

<span data-ttu-id="dc173-219">Formaterar strängar med hjälp av metoden format för sträng objekt.</span><span class="sxs-lookup"><span data-stu-id="dc173-219">Formats strings by using the format method of string objects.</span></span> <span data-ttu-id="dc173-220">Ange format strängen på vänster sida av operatorn och de objekt som ska formateras på höger sida av operatorn.</span><span class="sxs-lookup"><span data-stu-id="dc173-220">Enter the format string on the left side of the operator and the objects to be formatted on the right side of the operator.</span></span>

```powershell
"{0} {1,-10} {2:N}" -f 1,"hello",[math]::pi
```

```output
1 hello      3.14
```

<span data-ttu-id="dc173-221">Om du behöver behålla klammerparenteserna ( `{}` ) i den formaterade strängen kan du kringgå dem genom att dubblera klammerparenteserna.</span><span class="sxs-lookup"><span data-stu-id="dc173-221">If you need to keep the curly braces (`{}`) in the formatted string, you can escape them by doubling the curly braces.</span></span>

```powershell
"{0} vs. {{0}}" -f 'foo'
```

```Output
foo vs. {0}
```

<span data-ttu-id="dc173-222">Mer information finns i metoden [String. format](/dotnet/api/system.string.format) och [sammansatt formatering](/dotnet/standard/base-types/composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="dc173-222">For more information, see the [String.Format](/dotnet/api/system.string.format) method and [Composite Formatting](/dotnet/standard/base-types/composite-formatting).</span></span>

#### <a name="index-operator--"></a><span data-ttu-id="dc173-223">Index operator `[ ]`</span><span class="sxs-lookup"><span data-stu-id="dc173-223">Index operator `[ ]`</span></span>

<span data-ttu-id="dc173-224">Väljer objekt från indexerade samlingar, till exempel matriser och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="dc173-224">Selects objects from indexed collections, such as arrays and hash tables.</span></span> <span data-ttu-id="dc173-225">Mat ris index är noll-baserade, så det första objektet indexeras som `[0]` .</span><span class="sxs-lookup"><span data-stu-id="dc173-225">Array indexes are zero-based, so the first object is indexed as `[0]`.</span></span> <span data-ttu-id="dc173-226">För matriser (endast) kan du också använda negativa index för att hämta de sista värdena.</span><span class="sxs-lookup"><span data-stu-id="dc173-226">For arrays (only), you can also use negative indexes to get the last values.</span></span> <span data-ttu-id="dc173-227">Hash-tabeller indexeras efter nyckel värde.</span><span class="sxs-lookup"><span data-stu-id="dc173-227">Hash tables are indexed by key value.</span></span>

```
PS> $a = 1, 2, 3
PS> $a[0]
1
PS> $a[-1]
3
```

```powershell
(Get-HotFix | Sort-Object installedOn)[-1]
```

```powershell
$h = @{key="value"; name="PowerShell"; version="2.0"}
$h["name"]
```

```output
PowerShell
```

```powershell
$x = [xml]"<doc><intro>Once upon a time...</intro></doc>"
$x["doc"]
```

```output
intro
-----
Once upon a time...
```

#### <a name="pipeline-operator-"></a><span data-ttu-id="dc173-228">Pipeline-operator `|`</span><span class="sxs-lookup"><span data-stu-id="dc173-228">Pipeline operator `|`</span></span>

<span data-ttu-id="dc173-229">Skickar ("pipes") utdata från kommandot som föregår det till kommandot som följer.</span><span class="sxs-lookup"><span data-stu-id="dc173-229">Sends ("pipes") the output of the command that precedes it to the command that follows it.</span></span> <span data-ttu-id="dc173-230">När utdata innehåller fler än ett objekt (en "samling") skickar pipeline-operatorn objektet en i taget.</span><span class="sxs-lookup"><span data-stu-id="dc173-230">When the output includes more than one object (a "collection"), the pipeline operator sends the objects one at a time.</span></span>

```powershell
Get-Process | Get-Member
Get-Service | Where-Object {$_.StartType -eq 'Automatic'}
```

#### <a name="range-operator-"></a><span data-ttu-id="dc173-231">Intervall operator `..`</span><span class="sxs-lookup"><span data-stu-id="dc173-231">Range operator `..`</span></span>

<span data-ttu-id="dc173-232">Representerar sekventiella heltal i en heltals mat ris, med en övre och nedre gränser.</span><span class="sxs-lookup"><span data-stu-id="dc173-232">Represents the sequential integers in an integer array, given an upper, and lower boundary.</span></span>

```powershell
1..10
foreach ($a in 1..$max) {Write-Host $a}
```

<span data-ttu-id="dc173-233">Du kan också skapa intervall i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="dc173-233">You can also create ranges in reverse order.</span></span>

```powershell
10..1
5..-5 | ForEach-Object {Write-Output $_}
```

<span data-ttu-id="dc173-234">Från och med PowerShell 6 fungerar intervall operatorn med **tecken** samt **heltal**.</span><span class="sxs-lookup"><span data-stu-id="dc173-234">Beginning in PowerShell 6, the range operator works with **Characters** as well as **Integers**.</span></span>

<span data-ttu-id="dc173-235">Om du vill skapa ett tecken intervall omger du gräns värdena med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="dc173-235">To create a range of characters, enclose the boundary characters in quotes.</span></span>

```powershell
PS> 'a'..'f'
a
b
c
d
e
f
```

```powershell
PS> 'F'..'A'
F
E
D
C
B
A
```

#### <a name="member-access-operator-"></a><span data-ttu-id="dc173-236">Ansvarig för medlems åtkomst `.`</span><span class="sxs-lookup"><span data-stu-id="dc173-236">Member access operator `.`</span></span>

<span data-ttu-id="dc173-237">Ansluter till egenskaper och metoder för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="dc173-237">Accesses the properties and methods of an object.</span></span> <span data-ttu-id="dc173-238">Medlems namnet kan vara ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-238">The member name may be an expression.</span></span>

```powershell
$myProcess.peakWorkingSet
(Get-Process PowerShell).kill()
'OS', 'Platform' | Foreach-Object { $PSVersionTable. $_ }
```

#### <a name="static-member-operator-"></a><span data-ttu-id="dc173-239">Statisk medlems operator `::`</span><span class="sxs-lookup"><span data-stu-id="dc173-239">Static member operator `::`</span></span>

<span data-ttu-id="dc173-240">Anropar statiska egenskaper och metoder för en .NET Framework-klass.</span><span class="sxs-lookup"><span data-stu-id="dc173-240">Calls the static properties and methods of a .NET Framework class.</span></span> <span data-ttu-id="dc173-241">Om du vill hitta statiska egenskaper och metoder för ett objekt använder du cmdletens statiska parameter `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="dc173-241">To find the static properties and methods of an object, use the Static parameter of the `Get-Member` cmdlet.</span></span>  <span data-ttu-id="dc173-242">Medlems namnet kan vara ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="dc173-242">The member name may be an expression.</span></span>

```powershell
[datetime]::Now
'MinValue', 'MaxValue' | Foreach-Object { [int]:: $_ }
```

## <a name="see-also"></a><span data-ttu-id="dc173-243">Se även</span><span class="sxs-lookup"><span data-stu-id="dc173-243">See also</span></span>

[<span data-ttu-id="dc173-244">about_Arithmetic_Operators</span><span class="sxs-lookup"><span data-stu-id="dc173-244">about_Arithmetic_Operators</span></span>](about_Arithmetic_Operators.md)

[<span data-ttu-id="dc173-245">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="dc173-245">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="dc173-246">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="dc173-246">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="dc173-247">about_Logical_Operators</span><span class="sxs-lookup"><span data-stu-id="dc173-247">about_Logical_Operators</span></span>](about_logical_operators.md)

[<span data-ttu-id="dc173-248">about_Operator_Precedence</span><span class="sxs-lookup"><span data-stu-id="dc173-248">about_Operator_Precedence</span></span>](about_operator_precedence.md)

[<span data-ttu-id="dc173-249">about_Type_Operators</span><span class="sxs-lookup"><span data-stu-id="dc173-249">about_Type_Operators</span></span>](about_Type_Operators.md)

[<span data-ttu-id="dc173-250">about_Split</span><span class="sxs-lookup"><span data-stu-id="dc173-250">about_Split</span></span>](about_Split.md)

[<span data-ttu-id="dc173-251">about_Join</span><span class="sxs-lookup"><span data-stu-id="dc173-251">about_Join</span></span>](about_Join.md)

[<span data-ttu-id="dc173-252">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="dc173-252">about_Redirection</span></span>](about_Redirection.md)
