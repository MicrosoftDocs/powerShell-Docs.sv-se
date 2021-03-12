---
description: Beskriver hur du använder operatörer för att tilldela värden till variabler.
Locale: en-US
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 73c8937c74971160a3a1c714131108c87f2fa848
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195903"
---
# <a name="about-assignment-operators"></a><span data-ttu-id="301b2-103">Om tilldelnings operatörer</span><span class="sxs-lookup"><span data-stu-id="301b2-103">About Assignment Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="301b2-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="301b2-104">Short description</span></span>
<span data-ttu-id="301b2-105">Beskriver hur du använder operatörer för att tilldela värden till variabler.</span><span class="sxs-lookup"><span data-stu-id="301b2-105">Describes how to use operators to assign values to variables.</span></span>

## <a name="long-description"></a><span data-ttu-id="301b2-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="301b2-106">Long description</span></span>

<span data-ttu-id="301b2-107">Tilldelnings operatörer tilldelar en eller flera värden till en variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-107">Assignment operators assign one or more values to a variable.</span></span> <span data-ttu-id="301b2-108">De kan utföra numeriska åtgärder på värdena innan tilldelningen.</span><span class="sxs-lookup"><span data-stu-id="301b2-108">They can perform numeric operations on the values before the assignment.</span></span>

<span data-ttu-id="301b2-109">PowerShell har stöd för följande tilldelnings operatorer.</span><span class="sxs-lookup"><span data-stu-id="301b2-109">PowerShell supports the following assignment operators.</span></span>

|<span data-ttu-id="301b2-110">Operator</span><span class="sxs-lookup"><span data-stu-id="301b2-110">Operator</span></span>|<span data-ttu-id="301b2-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="301b2-111">Description</span></span>                                                  |
|--------|-------------------------------------------------------------|
|=       |<span data-ttu-id="301b2-112">Ställer in värdet för en variabel till det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-112">Sets the value of a variable to the specified value.</span></span>         |
|+=      |<span data-ttu-id="301b2-113">Ökar värdet för en variabel med det angivna värdet, eller</span><span class="sxs-lookup"><span data-stu-id="301b2-113">Increases the value of a variable by the specified value, or</span></span> |
|        |<span data-ttu-id="301b2-114">lägger till det angivna värdet i det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-114">appends the specified value to the existing value.</span></span>           |
|-=      |<span data-ttu-id="301b2-115">Minskar värdet för en variabel med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-115">Decreases the value of a variable by the specified value.</span></span>    |
|*=      |<span data-ttu-id="301b2-116">Multiplicerar värdet för en variabel med det angivna värdet, eller</span><span class="sxs-lookup"><span data-stu-id="301b2-116">Multiplies the value of a variable by the specified value, or</span></span>|
|        |<span data-ttu-id="301b2-117">lägger till det angivna värdet i det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-117">appends the specified value to the existing value.</span></span>           |
|/=      |<span data-ttu-id="301b2-118">Dividerar värdet för en variabel med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-118">Divides the value of a variable by the specified value.</span></span>      |
|%=      |<span data-ttu-id="301b2-119">Dividerar värdet för en variabel med det angivna värdet och</span><span class="sxs-lookup"><span data-stu-id="301b2-119">Divides the value of a variable by the specified value and</span></span>   |
|        |<span data-ttu-id="301b2-120">tilldelar sedan resten (Modulus) till variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-120">then assigns the remainder (modulus) to the variable.</span></span>        |
|++      |<span data-ttu-id="301b2-121">Ökar värdet för en variabel, tilldelnings bara egenskap eller</span><span class="sxs-lookup"><span data-stu-id="301b2-121">Increases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="301b2-122">mat ris element med 1.</span><span class="sxs-lookup"><span data-stu-id="301b2-122">array element by 1.</span></span>                                          |
|--      |<span data-ttu-id="301b2-123">Minskar värdet för en variabel, tilldelnings bara egenskap eller</span><span class="sxs-lookup"><span data-stu-id="301b2-123">Decreases the value of a variable, assignable property, or</span></span>   |
|        |<span data-ttu-id="301b2-124">mat ris element med 1.</span><span class="sxs-lookup"><span data-stu-id="301b2-124">array element by 1.</span></span>                                          |

## <a name="syntax"></a><span data-ttu-id="301b2-125">Syntax</span><span class="sxs-lookup"><span data-stu-id="301b2-125">Syntax</span></span>

<span data-ttu-id="301b2-126">Syntaxen för tilldelnings operatörerna är följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-126">The syntax of the assignment operators is as follows:</span></span>

<span data-ttu-id="301b2-127">`<assignable-expression>` `<assignment-operator>` `<value>`</span><span class="sxs-lookup"><span data-stu-id="301b2-127">`<assignable-expression>` `<assignment-operator>` `<value>`</span></span>

<span data-ttu-id="301b2-128">Tilldelnings bara uttryck innehåller variabler och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="301b2-128">Assignable expressions include variables and properties.</span></span> <span data-ttu-id="301b2-129">Värdet kan vara ett enskilt värde, en matris med värden eller ett kommando, ett uttryck eller en instruktion.</span><span class="sxs-lookup"><span data-stu-id="301b2-129">The value can be a single value, an array of values, or a command, expression, or statement.</span></span>

<span data-ttu-id="301b2-130">Operatorerna öka och minska är unära operatorer.</span><span class="sxs-lookup"><span data-stu-id="301b2-130">The increment and decrement operators are unary operators.</span></span> <span data-ttu-id="301b2-131">Varje har prefix-och postfix-versioner.</span><span class="sxs-lookup"><span data-stu-id="301b2-131">Each has prefix and postfix versions.</span></span>

`<assignable-expression><operator>`
`<operator><assignable-expression>`

<span data-ttu-id="301b2-132">Det tilldelnings bara uttrycket måste vara ett tal eller konvertera det till ett tal.</span><span class="sxs-lookup"><span data-stu-id="301b2-132">The assignable expression must be a number or it must be convertible to a number.</span></span>

## <a name="assigning-values"></a><span data-ttu-id="301b2-133">Tilldela värden</span><span class="sxs-lookup"><span data-stu-id="301b2-133">Assigning values</span></span>

<span data-ttu-id="301b2-134">Variabler är namngivna minnes utrymmen som lagrar värden.</span><span class="sxs-lookup"><span data-stu-id="301b2-134">Variables are named memory spaces that store values.</span></span> <span data-ttu-id="301b2-135">Du lagrar värdena i variablerna med hjälp av tilldelnings operatorn `=` .</span><span class="sxs-lookup"><span data-stu-id="301b2-135">You store the values in variables by using the assignment operator `=`.</span></span> <span data-ttu-id="301b2-136">Det nya värdet kan ersätta det befintliga värdet för variabeln, eller så kan du lägga till ett nytt värde till det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-136">The new value can replace the existing value of the variable, or you can append a new value to the existing value.</span></span>

<span data-ttu-id="301b2-137">Den grundläggande tilldelnings operatorn är likhets tecknet `=` `(ASCII 61)` .</span><span class="sxs-lookup"><span data-stu-id="301b2-137">The basic assignment operator is the equal sign `=` `(ASCII 61)`.</span></span> <span data-ttu-id="301b2-138">Följande-sats tilldelar exempelvis värdet PowerShell till `$MyShell` variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-138">For example, the following statement assigns the value PowerShell to the `$MyShell` variable:</span></span>

```powershell
$MyShell = "PowerShell"
```

<span data-ttu-id="301b2-139">När du tilldelar ett värde till en variabel i PowerShell skapas variabeln om den inte redan finns.</span><span class="sxs-lookup"><span data-stu-id="301b2-139">When you assign a value to a variable in PowerShell, the variable is created if it did not already exist.</span></span> <span data-ttu-id="301b2-140">Till exempel skapar den första av följande två tilldelnings uttryck `$a` variabeln och tilldelar värdet 6 till `$a` .</span><span class="sxs-lookup"><span data-stu-id="301b2-140">For example, the first of the following two assignment statements creates the `$a` variable and assigns a value of 6 to `$a`.</span></span> <span data-ttu-id="301b2-141">Den andra tilldelnings instruktionen tilldelar värdet 12 till `$a` .</span><span class="sxs-lookup"><span data-stu-id="301b2-141">The second assignment statement assigns a value of 12 to `$a`.</span></span> <span data-ttu-id="301b2-142">Den första instruktionen skapar en ny variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-142">The first statement creates a new variable.</span></span> <span data-ttu-id="301b2-143">Den andra instruktionen ändrar bara dess värde:</span><span class="sxs-lookup"><span data-stu-id="301b2-143">The second statement changes only its value:</span></span>

```powershell
$a = 6
$a = 12
```

<span data-ttu-id="301b2-144">Variabler i PowerShell har inte någon speciell datatyp om du inte skickar dem.</span><span class="sxs-lookup"><span data-stu-id="301b2-144">Variables in PowerShell do not have a specific data type unless you cast them.</span></span>
<span data-ttu-id="301b2-145">När en variabel bara innehåller ett objekt, använder variabeln data typen för objektet.</span><span class="sxs-lookup"><span data-stu-id="301b2-145">When a variable contains only one object, the variable takes the data type of that object.</span></span> <span data-ttu-id="301b2-146">När en variabel innehåller en samling av objekt, har variabeln system. Object-datatyp.</span><span class="sxs-lookup"><span data-stu-id="301b2-146">When a variable contains a collection of objects, the variable has the System.Object data type.</span></span> <span data-ttu-id="301b2-147">Därför kan du tilldela valfri typ av objekt till samlingen.</span><span class="sxs-lookup"><span data-stu-id="301b2-147">Therefore, you can assign any type of object to the collection.</span></span> <span data-ttu-id="301b2-148">I följande exempel visas att du kan lägga till process objekt, service objekt, strängar och heltal till en variabel utan att generera ett fel:</span><span class="sxs-lookup"><span data-stu-id="301b2-148">The following example shows that you can add process objects, service objects, strings, and integers to a variable without generating an error:</span></span>

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

<span data-ttu-id="301b2-149">Eftersom tilldelnings operatorn `=` har lägre prioritet än pipeline-operatorn `|` , behöver parenteser inte tilldela resultatet av en kommando pipeline till en variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-149">Because the assignment operator `=` has a lower precedence than the pipeline operator `|`, parentheses are not required to assign the result of a command pipeline to a variable.</span></span> <span data-ttu-id="301b2-150">Följande kommando sorterar till exempel tjänsterna på datorn och tilldelar sedan de sorterade tjänsterna till `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-150">For example, the following command sorts the services on the computer and then assigns the sorted services to the `$a` variable:</span></span>

```powershell
$a = Get-Service | Sort-Object -Property name
```

<span data-ttu-id="301b2-151">Du kan också tilldela värdet som skapats av en instruktion till en variabel, som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="301b2-151">You can also assign the value created by a statement to a variable, as in the following example:</span></span>

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

<span data-ttu-id="301b2-152">I det här exemplet tilldelas `$a` variabeln noll till variabeln om värdet för `$b` är mindre än noll.</span><span class="sxs-lookup"><span data-stu-id="301b2-152">This example assigns zero to the `$a` variable if the value of `$b` is less than zero.</span></span> <span data-ttu-id="301b2-153">Det tilldelar värdet `$b` till `$a` om värdet `$b` inte är mindre än noll.</span><span class="sxs-lookup"><span data-stu-id="301b2-153">It assigns the value of `$b` to `$a` if the value of `$b` is not less than zero.</span></span>

### <a name="the-assignment-operator"></a><span data-ttu-id="301b2-154">Tilldelnings operatorn</span><span class="sxs-lookup"><span data-stu-id="301b2-154">The assignment operator</span></span>

<span data-ttu-id="301b2-155">Tilldelnings operatorn `=` tilldelar värden till variabler.</span><span class="sxs-lookup"><span data-stu-id="301b2-155">The assignment operator `=` assigns values to variables.</span></span> <span data-ttu-id="301b2-156">Om variabeln redan har ett värde ersätter tilldelnings operatorn `=` värdet utan varning.</span><span class="sxs-lookup"><span data-stu-id="301b2-156">If the variable already has a value, the assignment operator `=` replaces the value without warning.</span></span>

<span data-ttu-id="301b2-157">Följande instruktion tilldelar heltal svärdet 6 till `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-157">The following statement assigns the integer value 6 to the `$a` variable:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="301b2-158">Om du vill tilldela ett sträng värde till en variabel, omger du strängvärdet med citat tecken enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-158">To assign a string value to a variable, enclose the string value in quotation marks, as follows:</span></span>

```powershell
$a = "baseball"
```

<span data-ttu-id="301b2-159">Om du vill tilldela en matris (flera värden) till en variabel separerar du värdena med kommatecken enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-159">To assign an array (multiple values) to a variable, separate the values with commas, as follows:</span></span>

```powershell
$a = "apple", "orange", "lemon", "grape"
```

<span data-ttu-id="301b2-160">Om du vill tilldela en hash-tabell till en variabel använder du standard-hash-format i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="301b2-160">To assign a hash table to a variable, use the standard hash table notation in PowerShell.</span></span> <span data-ttu-id="301b2-161">Skriv ett at-tecken `@` följt av nyckel/värde-par som skiljs åt av semikolon `;` och omges av klammerparenteser `{ }` .</span><span class="sxs-lookup"><span data-stu-id="301b2-161">Type an at sign `@` followed by key/value pairs that are separated by semicolons `;` and enclosed in braces `{ }`.</span></span> <span data-ttu-id="301b2-162">Om du till exempel vill tilldela en hash-tabell till `$a` variabeln skriver du:</span><span class="sxs-lookup"><span data-stu-id="301b2-162">For example, to assign a hash table to the `$a` variable, type:</span></span>

```powershell
$a = @{one=1; two=2; three=3}
```

<span data-ttu-id="301b2-163">Om du vill tilldela hexadecimala värden till en variabel, skriver du in före värdet med `0x` .</span><span class="sxs-lookup"><span data-stu-id="301b2-163">To assign hexadecimal values to a variable, precede the value with `0x`.</span></span>
<span data-ttu-id="301b2-164">PowerShell konverterar det hexadecimala värdet (0x10) till ett Decimal värde (i det här fallet 16) och tilldelar värdet till `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-164">PowerShell converts the hexadecimal value (0x10) to a decimal value (in this case, 16) and assigns that value to the `$a` variable.</span></span> <span data-ttu-id="301b2-165">Om du till exempel vill tilldela värdet 0x10 till `$a` variabeln skriver du:</span><span class="sxs-lookup"><span data-stu-id="301b2-165">For example, to assign a value of 0x10 to the `$a` variable, type:</span></span>

```powershell
$a = 0x10
```

<span data-ttu-id="301b2-166">Om du vill tilldela en variabel ett exponentiellt värde anger du rot numret, bokstaven `e` och ett tal som representerar en multipel av 10.</span><span class="sxs-lookup"><span data-stu-id="301b2-166">To assign an exponential value to a variable, type the root number, the letter `e`, and a number that represents a multiple of 10.</span></span> <span data-ttu-id="301b2-167">Om du till exempel vill tilldela värdet 3,1415 till kraften hos 1 000 till `$a` variabeln skriver du:</span><span class="sxs-lookup"><span data-stu-id="301b2-167">For example, to assign a value of 3.1415 to the power of 1,000 to the `$a` variable, type:</span></span>

```powershell
$a = 3.1415e3
```

<span data-ttu-id="301b2-168">PowerShell kan också konvertera kilobyte `KB` , megabyte `MB` och gigabyte `GB` i byte.</span><span class="sxs-lookup"><span data-stu-id="301b2-168">PowerShell can also convert kilobytes `KB`, megabytes `MB`, and gigabytes `GB` into bytes.</span></span> <span data-ttu-id="301b2-169">Om du till exempel vill tilldela värdet 10 kilobyte till `$a` variabeln, skriver du:</span><span class="sxs-lookup"><span data-stu-id="301b2-169">For example, to assign a value of 10 kilobytes to the `$a` variable, type:</span></span>

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a><span data-ttu-id="301b2-170">Operatorn tilldelning efter tillägg</span><span class="sxs-lookup"><span data-stu-id="301b2-170">The assignment by addition operator</span></span>

<span data-ttu-id="301b2-171">Operatorn för tilldelning efter addition `+=` ökar antingen värdet för en variabel eller lägger till det angivna värdet i det befintliga värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-171">The assignment by addition operator `+=` either increments the value of a variable or appends the specified value to the existing value.</span></span> <span data-ttu-id="301b2-172">Åtgärden beror på om variabeln har en numerisk typ eller sträng typ och om variabeln innehåller ett enda värde (en skalär) eller flera värden (en samling).</span><span class="sxs-lookup"><span data-stu-id="301b2-172">The action depends on whether the variable has a numeric or string type and whether the variable contains a single value (a scalar) or multiple values (a collection).</span></span>

<span data-ttu-id="301b2-173">`+=`Operatorn kombinerar två åtgärder.</span><span class="sxs-lookup"><span data-stu-id="301b2-173">The `+=` operator combines two operations.</span></span> <span data-ttu-id="301b2-174">Först läggs den till och tilldelas sedan.</span><span class="sxs-lookup"><span data-stu-id="301b2-174">First, it adds, and then it assigns.</span></span>
<span data-ttu-id="301b2-175">Därför är följande uttryck likvärdiga:</span><span class="sxs-lookup"><span data-stu-id="301b2-175">Therefore, the following statements are equivalent:</span></span>

```powershell
$a += 2
$a = ($a + 2)
```

<span data-ttu-id="301b2-176">När variabeln innehåller ett enkelt numeriskt värde `+=` ökar operatorn det befintliga värdet med summan till höger om operatorn.</span><span class="sxs-lookup"><span data-stu-id="301b2-176">When the variable contains a single numeric value, the `+=` operator increments the existing value by the amount on the right side of the operator.</span></span> <span data-ttu-id="301b2-177">Sedan tilldelar operatorn resultatvärdet värdet till variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-177">Then, the operator assigns the resulting value to the variable.</span></span> <span data-ttu-id="301b2-178">I följande exempel visas hur du använder `+=` operatorn för att öka värdet för en variabel:</span><span class="sxs-lookup"><span data-stu-id="301b2-178">The following example shows how to use the `+=` operator to increase the value of a variable:</span></span>

```powershell
$a = 4
$a += 2
$a
```

```
6
```

<span data-ttu-id="301b2-179">När värdet för variabeln är en sträng, läggs värdet på höger sida av operatorn till i strängen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-179">When the value of the variable is a string, the value on the right side of the operator is appended to the string, as follows:</span></span>

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

<span data-ttu-id="301b2-180">När värdet för variabeln är en matris, `+=` lägger operatorn till värdena på höger sida av operatorn i matrisen.</span><span class="sxs-lookup"><span data-stu-id="301b2-180">When the value of the variable is an array, the `+=` operator appends the values on the right side of the operator to the array.</span></span> <span data-ttu-id="301b2-181">Om inte matrisen anges explicit genom databyte, kan du lägga till valfri typ av värde i matrisen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-181">Unless the array is explicitly typed by casting, you can append any type of value to the array, as follows:</span></span>

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

<span data-ttu-id="301b2-182">och</span><span class="sxs-lookup"><span data-stu-id="301b2-182">and</span></span>

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

<span data-ttu-id="301b2-183">När värdet för en variabel är en hash-tabell, `+=` lägger operatorn till värdet på höger sida av operatorn i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="301b2-183">When the value of a variable is a hash table, the `+=` operator appends the value on the right side of the operator to the hash table.</span></span> <span data-ttu-id="301b2-184">Men eftersom den enda typ som du kan lägga till i en hash-tabell är en annan hash-tabell, så går det inte att utföra andra tilldelningar.</span><span class="sxs-lookup"><span data-stu-id="301b2-184">However, because the only type that you can add to a hash table is another hash table, all other assignments fail.</span></span>

<span data-ttu-id="301b2-185">Följande kommando tilldelar till exempel en hash-tabell till `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-185">For example, the following command assigns a hash table to the `$a` variable.</span></span>
<span data-ttu-id="301b2-186">Sedan använder den `+=` operatorn för att lägga till en annan hash-tabell i den befintliga hash-tabellen, vilket effektivt lägger till ett nytt nyckel/värde-par i den befintliga hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="301b2-186">Then, it uses the `+=` operator to append another hash table to the existing hash table, effectively adding a new key/value pair to the existing hash table.</span></span>
<span data-ttu-id="301b2-187">Det här kommandot slutförs, som visas i utdata:</span><span class="sxs-lookup"><span data-stu-id="301b2-187">This command succeeds, as shown in the output:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

<span data-ttu-id="301b2-188">Följande kommando försöker lägga till ett heltal "1" till hash-tabellen i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-188">The following command attempts to append an integer "1" to the hash table in the `$a` variable.</span></span> <span data-ttu-id="301b2-189">Detta kommando Miss lyckas:</span><span class="sxs-lookup"><span data-stu-id="301b2-189">This command fails:</span></span>

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a><span data-ttu-id="301b2-190">Tilldelningen efter subtraktion-operator</span><span class="sxs-lookup"><span data-stu-id="301b2-190">The assignment by subtraction operator</span></span>

<span data-ttu-id="301b2-191">Tilldelningen av subtraktion-operatorn `-=` utvärderar värdet för en variabel med det värde som anges på höger sida av operatorn.</span><span class="sxs-lookup"><span data-stu-id="301b2-191">The assignment by subtraction operator `-=` decrements the value of a variable by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="301b2-192">Det går inte att använda den här operatorn med String-variabler och den kan inte användas för att ta bort ett element från en samling.</span><span class="sxs-lookup"><span data-stu-id="301b2-192">This operator cannot be used with string variables, and it cannot be used to remove an element from a collection.</span></span>

<span data-ttu-id="301b2-193">`-=`Operatorn kombinerar två åtgärder.</span><span class="sxs-lookup"><span data-stu-id="301b2-193">The `-=` operator combines two operations.</span></span> <span data-ttu-id="301b2-194">Först subtraheras den och tilldelas sedan.</span><span class="sxs-lookup"><span data-stu-id="301b2-194">First, it subtracts, and then it assigns.</span></span> <span data-ttu-id="301b2-195">Därför är följande uttryck likvärdiga:</span><span class="sxs-lookup"><span data-stu-id="301b2-195">Therefore, the following statements are equivalent:</span></span>

```powershell
$a -= 2
$a = ($a - 2)
```

<span data-ttu-id="301b2-196">I följande exempel visas hur du använder `-=` operatorn för att minska värdet för en variabel:</span><span class="sxs-lookup"><span data-stu-id="301b2-196">The following example shows how to use of the `-=` operator to decrease the value of a variable:</span></span>

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

<span data-ttu-id="301b2-197">Du kan också använda `-=` operatorn tilldelning för att minska värdet för en medlem i en numerisk matris.</span><span class="sxs-lookup"><span data-stu-id="301b2-197">You can also use the `-=` assignment operator to decrease the value of a member of a numeric array.</span></span> <span data-ttu-id="301b2-198">Det gör du genom att ange indexet för det mat ris element som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="301b2-198">To do this, specify the index of the array element that you want to change.</span></span> <span data-ttu-id="301b2-199">I följande exempel minskas värdet för det tredje elementet i en matris (element 2) med 1:</span><span class="sxs-lookup"><span data-stu-id="301b2-199">In the following example, the value of the third element of an array (element 2) is decreased by 1:</span></span>

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

<span data-ttu-id="301b2-200">Du kan inte använda `-=` operatorn för att ta bort värdena för en variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-200">You cannot use the `-=` operator to delete the values of a variable.</span></span> <span data-ttu-id="301b2-201">Om du vill ta bort alla värden som har tilldelats en variabel använder du cmdletarna [Clear-item](xref:Microsoft.PowerShell.Management.Clear-Item) eller [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) för att tilldela värdet `$null` eller `""` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-201">To delete all the values that are assigned to a variable, use the [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item) or [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) cmdlets to assign a value of `$null` or `""` to the variable.</span></span>

```powershell
$a = $null
```

<span data-ttu-id="301b2-202">Om du vill ta bort ett visst värde från en matris använder du Array-notation för att tilldela ett värde `$null` till ett visst objekt.</span><span class="sxs-lookup"><span data-stu-id="301b2-202">To delete a particular value from an array, use array notation to assign a value of `$null` to the particular item.</span></span> <span data-ttu-id="301b2-203">Följande uttryck tar till exempel bort det andra värdet (index position 1) från en matris:</span><span class="sxs-lookup"><span data-stu-id="301b2-203">For example, the following statement deletes the second value (index position 1) from an array:</span></span>

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

<span data-ttu-id="301b2-204">Om du vill ta bort en variabel använder du cmdleten [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) .</span><span class="sxs-lookup"><span data-stu-id="301b2-204">To delete a variable, use the [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) cmdlet.</span></span> <span data-ttu-id="301b2-205">Den här metoden är användbar när variabeln uttryckligen omvandlas till en viss datatyp och du vill ha en variabel som inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="301b2-205">This method is useful when the variable is explicitly cast to a particular data type, and you want an untyped variable.</span></span> <span data-ttu-id="301b2-206">Följande kommando tar bort `$a` variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-206">The following command deletes the `$a` variable:</span></span>

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a><span data-ttu-id="301b2-207">Operatorn tilldelning efter multiplikation</span><span class="sxs-lookup"><span data-stu-id="301b2-207">The assignment by multiplication operator</span></span>

<span data-ttu-id="301b2-208">Operatorn tilldelning av multiplikation `*=` multiplicerar ett numeriskt värde eller lägger till det angivna antalet kopior av strängvärdet för en variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-208">The assignment by multiplication operator `*=` multiplies a numeric value or appends the specified number of copies of the string value of a variable.</span></span>

<span data-ttu-id="301b2-209">När en variabel innehåller ett enkelt numeriskt värde multipliceras värdet med värdet till höger om operatorn.</span><span class="sxs-lookup"><span data-stu-id="301b2-209">When a variable contains a single numeric value, that value is multiplied by the value on the right side of the operator.</span></span> <span data-ttu-id="301b2-210">I följande exempel visas exempelvis hur du använder `*=` operatorn för att multiplicera värdet för en variabel:</span><span class="sxs-lookup"><span data-stu-id="301b2-210">For example, the following example shows how to use the `*=` operator to multiply the value of a variable:</span></span>

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

<span data-ttu-id="301b2-211">I det här fallet `*=` kombinerar operatorn två åtgärder.</span><span class="sxs-lookup"><span data-stu-id="301b2-211">In this case, the `*=` operator combines two operations.</span></span> <span data-ttu-id="301b2-212">Först, den multipliceras och tilldelas sedan.</span><span class="sxs-lookup"><span data-stu-id="301b2-212">First, it multiplies, and then it assigns.</span></span> <span data-ttu-id="301b2-213">Därför är följande uttryck likvärdiga:</span><span class="sxs-lookup"><span data-stu-id="301b2-213">Therefore, the following statements are equivalent:</span></span>

```powershell
$a *= 2
$a = ($a * 2)
```

<span data-ttu-id="301b2-214">När en variabel innehåller ett sträng värde lägger PowerShell till det angivna antalet strängar till värdet enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-214">When a variable contains a string value, PowerShell appends the specified number of strings to the value, as follows:</span></span>

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

<span data-ttu-id="301b2-215">Om du vill multiplicera ett element i en matris använder du ett index för att identifiera det element som du vill multiplicera.</span><span class="sxs-lookup"><span data-stu-id="301b2-215">To multiply an element of an array, use an index to identify the element that you want to multiply.</span></span> <span data-ttu-id="301b2-216">Följande kommando multiplicerar exempelvis det första elementet i matrisen (index position 0) med 2:</span><span class="sxs-lookup"><span data-stu-id="301b2-216">For example, the following command multiplies the first element in the array (index position 0) by 2:</span></span>

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a><span data-ttu-id="301b2-217">Operatorn tilldelning efter avdelning</span><span class="sxs-lookup"><span data-stu-id="301b2-217">The assignment by division operator</span></span>

<span data-ttu-id="301b2-218">Operatorn tilldelning efter Division `/=` delar ett numeriskt värde med det värde som anges på höger sida av operatorn.</span><span class="sxs-lookup"><span data-stu-id="301b2-218">The assignment by division operator `/=` divides a numeric value by the value that is specified on the right side of the operator.</span></span> <span data-ttu-id="301b2-219">Det går inte att använda operatorn med String-variabler.</span><span class="sxs-lookup"><span data-stu-id="301b2-219">The operator cannot be used with string variables.</span></span>

<span data-ttu-id="301b2-220">`/=`Operatorn kombinerar två åtgärder.</span><span class="sxs-lookup"><span data-stu-id="301b2-220">The `/=` operator combines two operations.</span></span> <span data-ttu-id="301b2-221">Först delas den upp och tilldelas sedan.</span><span class="sxs-lookup"><span data-stu-id="301b2-221">First, it divides, and then it assigns.</span></span> <span data-ttu-id="301b2-222">Därför är följande två uttryck likvärdiga:</span><span class="sxs-lookup"><span data-stu-id="301b2-222">Therefore, the following two statements are equivalent:</span></span>

```powershell
$a /= 2
$a = ($a / 2)
```

<span data-ttu-id="301b2-223">Följande kommando använder exempelvis `/=` operatorn för att dividera värdet för en variabel:</span><span class="sxs-lookup"><span data-stu-id="301b2-223">For example, the following command uses the `/=` operator to divide the value of a variable:</span></span>

```powershell
$a = 8
$a /=2
$a
```

```
4
```

<span data-ttu-id="301b2-224">Om du vill dela upp ett element i en matris använder du ett index för att identifiera det element som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="301b2-224">To divide an element of an array, use an index to identify the element that you want to change.</span></span> <span data-ttu-id="301b2-225">Följande kommando delar till exempel det andra elementet i matrisen (index position 1) med 2:</span><span class="sxs-lookup"><span data-stu-id="301b2-225">For example, the following command divides the second element in the array (index position 1) by 2:</span></span>

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a><span data-ttu-id="301b2-226">Operatorn tilldelning efter modul</span><span class="sxs-lookup"><span data-stu-id="301b2-226">The assignment by modulus operator</span></span>

<span data-ttu-id="301b2-227">Operatorn tilldelning efter modul `%=` delar värdet för en variabel med värdet till höger om operatorn.</span><span class="sxs-lookup"><span data-stu-id="301b2-227">The assignment by modulus operator `%=` divides the value of a variable by the value on the right side of the operator.</span></span> <span data-ttu-id="301b2-228">Sedan `%=` tilldelar operatorn resten (kallas Modulus) till variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-228">Then, the `%=` operator assigns the remainder (known as the modulus) to the variable.</span></span> <span data-ttu-id="301b2-229">Du kan bara använda den här operatorn när en variabel innehåller ett enkelt numeriskt värde.</span><span class="sxs-lookup"><span data-stu-id="301b2-229">You can use this operator only when a variable contains a single numeric value.</span></span> <span data-ttu-id="301b2-230">Du kan inte använda den här operatorn när en variabel innehåller en sträng variabel eller en matris.</span><span class="sxs-lookup"><span data-stu-id="301b2-230">You cannot use this operator when a variable contains a string variable or an array.</span></span>

<span data-ttu-id="301b2-231">`%=`Operatorn kombinerar två åtgärder.</span><span class="sxs-lookup"><span data-stu-id="301b2-231">The `%=` operator combines two operations.</span></span> <span data-ttu-id="301b2-232">Först delar den upp och avgör resten och tilldelar sedan resten till variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-232">First, it divides and determines the remainder, and then it assigns the remainder to the variable.</span></span> <span data-ttu-id="301b2-233">Därför är följande uttryck likvärdiga:</span><span class="sxs-lookup"><span data-stu-id="301b2-233">Therefore, the following statements are equivalent:</span></span>

```powershell
$a %= 2
$a = ($a % 2)
```

<span data-ttu-id="301b2-234">I följande exempel visas hur du använder `%=` operatorn för att spara Modulus av en kvot:</span><span class="sxs-lookup"><span data-stu-id="301b2-234">The following example shows how to use the `%=` operator to save the modulus of a quotient:</span></span>

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a><span data-ttu-id="301b2-235">Operatorerna öka och minska</span><span class="sxs-lookup"><span data-stu-id="301b2-235">The increment and decrement operators</span></span>

<span data-ttu-id="301b2-236">Operatorn Increment `++` ökar värdet för en variabel med 1.</span><span class="sxs-lookup"><span data-stu-id="301b2-236">The increment operator `++` increases the value of a variable by 1.</span></span> <span data-ttu-id="301b2-237">När du använder operatorn Increment i en enkel instruktion returneras inget värde.</span><span class="sxs-lookup"><span data-stu-id="301b2-237">When you use the increment operator in a simple statement, no value is returned.</span></span> <span data-ttu-id="301b2-238">Visa resultatet genom att visa värdet för variabeln enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-238">To view the result, display the value of the variable, as follows:</span></span>

```powershell
$a = 7
++$a
$a
```

```
8
```

<span data-ttu-id="301b2-239">Om du vill tvinga fram ett värde som ska returneras omger du variabeln och operatorn inom parentes enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-239">To force a value to be returned, enclose the variable and the operator in parentheses, as follows:</span></span>

```powershell
$a = 7
(++$a)
```

```
8
```

<span data-ttu-id="301b2-240">Operatorn Increment kan placeras före (prefix) eller efter (postfix) en variabel.</span><span class="sxs-lookup"><span data-stu-id="301b2-240">The increment operator can be placed before (prefix) or after (postfix) a variable.</span></span> <span data-ttu-id="301b2-241">Prefixlängden för operatorn ökar en variabel innan dess värde används i instruktionen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-241">The prefix version of the operator increments a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

<span data-ttu-id="301b2-242">Postfix-versionen av operatorn ökar en variabel när dess värde används i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="301b2-242">The postfix version of the operator increments a variable after its value is used in the statement.</span></span> <span data-ttu-id="301b2-243">I följande exempel `$c` `$a` har variablerna och samma värden, eftersom värdet tilldelas `$c` innan `$a` ändringar:</span><span class="sxs-lookup"><span data-stu-id="301b2-243">In the following example, the `$c` and `$a` variables have different values because the value is assigned to `$c` before `$a` changes:</span></span>

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

<span data-ttu-id="301b2-244">Operatorn minska `--` minskar värdet för en variabel med 1.</span><span class="sxs-lookup"><span data-stu-id="301b2-244">The decrement operator `--` decreases the value of a variable by 1.</span></span> <span data-ttu-id="301b2-245">Precis som med operatorn Increment returneras inget värde när du använder operatorn i en enkel instruktion.</span><span class="sxs-lookup"><span data-stu-id="301b2-245">As with the increment operator, no value is returned when you use the operator in a simple statement.</span></span> <span data-ttu-id="301b2-246">Använd parenteser för att returnera ett värde enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-246">Use parentheses to return a value, as follows:</span></span>

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

<span data-ttu-id="301b2-247">Prefixlängden för operatorn minskar en variabel innan dess värde används i instruktionen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-247">The prefix version of the operator decrements a variable before its value is used in the statement, as follows:</span></span>

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

<span data-ttu-id="301b2-248">Postfix-versionen av operatorn minskar en variabel när dess värde används i instruktionen.</span><span class="sxs-lookup"><span data-stu-id="301b2-248">The postfix version of the operator decrements a variable after its value is used in the statement.</span></span> <span data-ttu-id="301b2-249">I följande exempel `$d` `$a` har variablerna och samma värden, eftersom värdet tilldelas `$d` innan `$a` ändringar:</span><span class="sxs-lookup"><span data-stu-id="301b2-249">In the following example, the `$d` and `$a` variables have different values because the value is assigned to `$d` before `$a` changes:</span></span>

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a><span data-ttu-id="301b2-250">Microsoft .NET Ramverks typer</span><span class="sxs-lookup"><span data-stu-id="301b2-250">Microsoft .NET Framework types</span></span>

<span data-ttu-id="301b2-251">Som standard när en variabel bara har ett värde, bestämmer värdet som tilldelas variabeln data typen för variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-251">By default, when a variable has only one value, the value that is assigned to the variable determines the data type of the variable.</span></span> <span data-ttu-id="301b2-252">Följande kommando skapar till exempel en variabel som har typen "Integer" (system. Int32):</span><span class="sxs-lookup"><span data-stu-id="301b2-252">For example, the following command creates a variable that has the "Integer" (System.Int32) type:</span></span>

```powershell
$a = 6
```

<span data-ttu-id="301b2-253">Om du vill hitta .NET Framework typen för en variabel använder du **gettype** -metoden och dess **FullName** -egenskap enligt följande.</span><span class="sxs-lookup"><span data-stu-id="301b2-253">To find the .NET Framework type of a variable, use the **GetType** method and its **FullName** property, as follows.</span></span> <span data-ttu-id="301b2-254">Se till att ta med parenteserna efter namnet på **gettype** -metoden, även om metod anropet inte har några argument:</span><span class="sxs-lookup"><span data-stu-id="301b2-254">Be sure to include the parentheses after the **GetType** method name, even though the method call has no arguments:</span></span>

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

<span data-ttu-id="301b2-255">Om du vill skapa en variabel som innehåller en sträng tilldelar du ett sträng värde till variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-255">To create a variable that contains a string, assign a string value to the variable.</span></span> <span data-ttu-id="301b2-256">Om du vill ange att värdet är en sträng omger du det med citat tecken enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-256">To indicate that the value is a string, enclose it in quotation marks, as follows:</span></span>

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

<span data-ttu-id="301b2-257">Om det första värdet som är kopplat till variabeln är en sträng behandlar PowerShell alla åtgärder som sträng åtgärder och skickar nya värden till strängar.</span><span class="sxs-lookup"><span data-stu-id="301b2-257">If the first value that is assigned to the variable is a string, PowerShell treats all operations as string operations and casts new values to strings.</span></span>
<span data-ttu-id="301b2-258">Detta inträffar i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="301b2-258">This occurs in the following example:</span></span>

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

<span data-ttu-id="301b2-259">Om det första värdet är ett heltal behandlar PowerShell alla åtgärder som heltals åtgärder och skickar nya värden till heltal.</span><span class="sxs-lookup"><span data-stu-id="301b2-259">If the first value is an integer, PowerShell treats all operations as integer operations and casts new values to integers.</span></span> <span data-ttu-id="301b2-260">Detta inträffar i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="301b2-260">This occurs in the following example:</span></span>

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

<span data-ttu-id="301b2-261">Du kan omvandla en ny skalär variabel som vilken .NET Framework typ som helst genom att placera namnet inom hak paren tes före antingen variabel namnet eller det första tilldelning svärdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-261">You can cast a new scalar variable as any .NET Framework type by placing the type name in brackets that precede either the variable name or the first assignment value.</span></span> <span data-ttu-id="301b2-262">När du kastar en variabel kan du bestämma vilka typer av data som kan lagras i variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-262">When you cast a variable, you can determine the types of data that can be stored in the variable.</span></span> <span data-ttu-id="301b2-263">Du kan också bestämma hur variabeln beter sig när du ändrar den.</span><span class="sxs-lookup"><span data-stu-id="301b2-263">And, you can determine how the variable behaves when you manipulate it.</span></span>

<span data-ttu-id="301b2-264">Följande kommando skickar exempelvis variabeln som en sträng typ:</span><span class="sxs-lookup"><span data-stu-id="301b2-264">For example, the following command casts the variable as a string type:</span></span>

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

<span data-ttu-id="301b2-265">I följande exempel skickas det första värdet i stället för att omvandla variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-265">The following example casts the first value, instead of casting the variable:</span></span>

```powershell
$a = [string]27
```

<span data-ttu-id="301b2-266">När du skickar en variabel till en speciell typ är den gemensamma konventionen att omvandla variabeln, inte värdet.</span><span class="sxs-lookup"><span data-stu-id="301b2-266">When you cast a variable to a specific type, the common convention is to cast the variable, not the value.</span></span> <span data-ttu-id="301b2-267">Du kan dock inte omkonvertera data typen för en befintlig variabel om dess värde inte kan konverteras till den nya data typen.</span><span class="sxs-lookup"><span data-stu-id="301b2-267">However, you cannot recast the data type of an existing variable if its value cannot be converted to the new data type.</span></span> <span data-ttu-id="301b2-268">Om du vill ändra data typen måste du ersätta dess värde enligt följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-268">To change the data type, you must replace its value, as follows:</span></span>

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

<span data-ttu-id="301b2-269">När du föregår ett variabel namn med en datatyp är typen av variabeln låst, såvida du inte uttryckligen åsidosätter typen genom att ange en annan datatyp.</span><span class="sxs-lookup"><span data-stu-id="301b2-269">In addition, when you precede a variable name with a data type, the type of that variable is locked unless you explicitly override the type by specifying another data type.</span></span> <span data-ttu-id="301b2-270">Om du försöker tilldela ett värde som är inkompatibelt med den befintliga typen, och du inte uttryckligen åsidosätter typen, visar PowerShell ett fel som visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="301b2-270">If you try to assign a value that is incompatible with the existing type, and you do not explicitly override the type, PowerShell displays an error, as shown in the following example:</span></span>

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

<span data-ttu-id="301b2-271">I PowerShell hanteras data typerna för variabler som innehåller flera objekt i en matris på olika sätt från data typerna för variabler som innehåller ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="301b2-271">In PowerShell, the data types of variables that contain multiple items in an array are handled differently from the data types of variables that contain a single item.</span></span> <span data-ttu-id="301b2-272">Om inte en datatyp specifikt tilldelas en mat ris variabel är data typen alltid `System.Object []` .</span><span class="sxs-lookup"><span data-stu-id="301b2-272">Unless a data type is specifically assigned to an array variable, the data type is always `System.Object []`.</span></span> <span data-ttu-id="301b2-273">Den här data typen är speciell för matriser.</span><span class="sxs-lookup"><span data-stu-id="301b2-273">This data type is specific to arrays.</span></span>

<span data-ttu-id="301b2-274">Ibland kan du åsidosätta standard typen genom att ange en annan typ.</span><span class="sxs-lookup"><span data-stu-id="301b2-274">Sometimes, you can override the default type by specifying another type.</span></span> <span data-ttu-id="301b2-275">Följande kommando skickar exempelvis variabeln som en `string []` mat ris typ:</span><span class="sxs-lookup"><span data-stu-id="301b2-275">For example, the following command casts the variable as a `string []` array type:</span></span>

```powershell
[string []] $a = "one", "two", "three"
```

<span data-ttu-id="301b2-276">PowerShell-variabler kan vara valfria .NET Framework-datatyp.</span><span class="sxs-lookup"><span data-stu-id="301b2-276">PowerShell variables can be any .NET Framework data type.</span></span> <span data-ttu-id="301b2-277">Dessutom kan du tilldela en fullständigt kvalificerad .NET Framework-datatyp som är tillgänglig i den aktuella processen.</span><span class="sxs-lookup"><span data-stu-id="301b2-277">In addition, you can assign any fully qualified .NET Framework data type that is available in the current process.</span></span> <span data-ttu-id="301b2-278">Följande kommando anger till exempel en `System.DateTime` datatyp:</span><span class="sxs-lookup"><span data-stu-id="301b2-278">For example, the following command specifies a `System.DateTime` data type:</span></span>

```powershell
[System.DateTime]$a = "5/31/2005"
```

<span data-ttu-id="301b2-279">Variabeln tilldelas ett värde som överensstämmer med `System.DateTime` data typen.</span><span class="sxs-lookup"><span data-stu-id="301b2-279">The variable will be assigned a value that conforms to the `System.DateTime` data type.</span></span> <span data-ttu-id="301b2-280">Värdet för `$a` variabeln skulle vara följande:</span><span class="sxs-lookup"><span data-stu-id="301b2-280">The value of the `$a` variable would be the following:</span></span>

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a><span data-ttu-id="301b2-281">Tilldela flera variabler</span><span class="sxs-lookup"><span data-stu-id="301b2-281">Assigning multiple variables</span></span>

<span data-ttu-id="301b2-282">I PowerShell kan du tilldela värden till flera variabler genom att använda ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="301b2-282">In PowerShell, you can assign values to multiple variables by using a single command.</span></span> <span data-ttu-id="301b2-283">Det första elementet i tilldelning svärdet tilldelas den första variabeln, det andra elementet tilldelas till den andra variabeln, det tredje elementet till den tredje variabeln och så vidare.</span><span class="sxs-lookup"><span data-stu-id="301b2-283">The first element of the assignment value is assigned to the first variable, the second element is assigned to the second variable, the third element to the third variable, and so on.</span></span> <span data-ttu-id="301b2-284">Följande kommando tilldelar till exempel värdet 1 till `$a` variabeln, värdet 2 till `$b` variabeln och värdet 3 till `$c` variabeln:</span><span class="sxs-lookup"><span data-stu-id="301b2-284">For example, the following command assigns the value 1 to the `$a` variable, the value 2 to the `$b` variable, and the value 3 to the `$c` variable:</span></span>

```powershell
$a, $b, $c = 1, 2, 3
```

<span data-ttu-id="301b2-285">Om tilldelning svärdet innehåller fler element än variabler, tilldelas alla återstående värden den sista variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-285">If the assignment value contains more elements than variables, all the remaining values are assigned to the last variable.</span></span> <span data-ttu-id="301b2-286">Följande kommando innehåller till exempel tre variabler och fem värden:</span><span class="sxs-lookup"><span data-stu-id="301b2-286">For example, the following command contains three variables and five values:</span></span>

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

<span data-ttu-id="301b2-287">Därför tilldelar PowerShell värdet 1 till `$a` variabeln och värdet 2 till `$b` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-287">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="301b2-288">De tilldelar värdena 3, 4 och 5 till `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-288">It assigns the values 3, 4, and 5 to the `$c` variable.</span></span>
<span data-ttu-id="301b2-289">Om du vill tilldela värden i `$c` variabeln till tre andra variabler använder du följande format:</span><span class="sxs-lookup"><span data-stu-id="301b2-289">To assign the values in the `$c` variable to three other variables, use the following format:</span></span>

```powershell
$d, $e, $f = $c
```

<span data-ttu-id="301b2-290">Det här kommandot tilldelar värdet 3 till `$d` variabeln, värdet 4 till `$e` variabeln och värdet 5 till `$f` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-290">This command assigns the value 3 to the `$d` variable, the value 4 to the `$e` variable, and the value 5 to the `$f` variable.</span></span>

<span data-ttu-id="301b2-291">Om tilldelning svärdet innehåller färre element än variabler, tilldelas inte alla återstående variabler i slutet några värden.</span><span class="sxs-lookup"><span data-stu-id="301b2-291">If the assignment value contains less elements than variables, all the remaining variables at the end are not assigned any values.</span></span> <span data-ttu-id="301b2-292">Följande kommando innehåller till exempel tre variabler och två värden:</span><span class="sxs-lookup"><span data-stu-id="301b2-292">For example, the following command contains three variables and two values:</span></span>

```powershell
$a, $b, $c = 1, 2
```

<span data-ttu-id="301b2-293">Därför tilldelar PowerShell värdet 1 till `$a` variabeln och värdet 2 till `$b` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-293">Therefore, PowerShell assigns the value 1 to the `$a` variable and the value 2 to the `$b` variable.</span></span> <span data-ttu-id="301b2-294">Det tilldelar inget värde till `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-294">It will not assign any value to the `$c` variable.</span></span>

<span data-ttu-id="301b2-295">Du kan också tilldela ett enskilt värde till flera variabler genom att länka variablerna.</span><span class="sxs-lookup"><span data-stu-id="301b2-295">You can also assign a single value to multiple variables by chaining the variables.</span></span> <span data-ttu-id="301b2-296">Följande kommando tilldelar till exempel värdet "tre" till alla fyra variabler:</span><span class="sxs-lookup"><span data-stu-id="301b2-296">For example, the following command assigns a value of "three" to all four variables:</span></span>

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a><span data-ttu-id="301b2-297">Variabla-relaterade cmdletar</span><span class="sxs-lookup"><span data-stu-id="301b2-297">Variable-related cmdlets</span></span>

<span data-ttu-id="301b2-298">Förutom att använda en tilldelnings åtgärd för att ange ett variabel värde kan du också använda cmdleten [set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) .</span><span class="sxs-lookup"><span data-stu-id="301b2-298">In addition to using an assignment operation to set a variable value, you can also use the [Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) cmdlet.</span></span> <span data-ttu-id="301b2-299">Följande kommando använder `Set-Variable` till exempel för att tilldela en matris med 1, 2, 3 till `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="301b2-299">For example, the following command uses `Set-Variable` to assign an array of 1, 2, 3 to the `$a` variable.</span></span>

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a><span data-ttu-id="301b2-300">Se även</span><span class="sxs-lookup"><span data-stu-id="301b2-300">See also</span></span>

[<span data-ttu-id="301b2-301">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="301b2-301">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="301b2-302">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="301b2-302">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="301b2-303">about_Variables</span><span class="sxs-lookup"><span data-stu-id="301b2-303">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="301b2-304">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="301b2-304">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[<span data-ttu-id="301b2-305">Ta bort variabel</span><span class="sxs-lookup"><span data-stu-id="301b2-305">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[<span data-ttu-id="301b2-306">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="301b2-306">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)

