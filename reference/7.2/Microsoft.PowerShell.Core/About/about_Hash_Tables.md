---
description: Beskriver hur du skapar, använder och sorterar hash-tabeller i PowerShell.
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: dec2683acfa4fcf79419beea9e0840387d3d43d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708514"
---
# <a name="about-hash-tables"></a><span data-ttu-id="c77de-103">Om hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="c77de-103">About Hash Tables</span></span>

## <a name="short-description"></a><span data-ttu-id="c77de-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c77de-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="c77de-105">Beskriver hur du skapar, använder och sorterar hash-tabeller i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c77de-105">Describes how to create, use, and sort hash tables in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="c77de-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c77de-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="c77de-107">En hash-tabell, som även kallas för ett lexikon eller en associativ matris, är en komprimerad data struktur som lagrar ett eller flera nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="c77de-107">A hash table, also known as a dictionary or associative array, is a compact data structure that stores one or more key/value pairs.</span></span> <span data-ttu-id="c77de-108">En hash-tabell kan till exempel innehålla en serie med IP-adresser och dator namn, där IP-adresserna är nycklarna och dator namnen är värdena eller vice versa.</span><span class="sxs-lookup"><span data-stu-id="c77de-108">For example, a hash table might contain a series of IP addresses and computer names, where the IP addresses are the keys and the computer names are the values, or vice versa.</span></span>

<span data-ttu-id="c77de-109">I PowerShell är varje hash-tabell ett hash-objekt (system. Collections. hash).</span><span class="sxs-lookup"><span data-stu-id="c77de-109">In PowerShell, each hash table is a Hashtable (System.Collections.Hashtable) object.</span></span> <span data-ttu-id="c77de-110">Du kan använda egenskaper och metoder för hash-objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c77de-110">You can use the properties and methods of Hashtable objects in PowerShell.</span></span>

<span data-ttu-id="c77de-111">Från och med PowerShell 3,0 kan du använda attributet [ordnat] för att skapa en ordnad ord lista (system. Collections. specialiserad. OrderedDictionary) i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c77de-111">Beginning in PowerShell 3.0, you can use the [ordered] attribute to create an ordered dictionary (System.Collections.Specialized.OrderedDictionary) in PowerShell.</span></span>

<span data-ttu-id="c77de-112">Ordnade ord listor skiljer sig från hash-tabeller i att nycklarna alltid visas i den ordning som du visar dem.</span><span class="sxs-lookup"><span data-stu-id="c77de-112">Ordered dictionaries differ from hash tables in that the keys always appear in the order in which you list them.</span></span> <span data-ttu-id="c77de-113">Ordningen på nycklarna i en hash-tabell har inte fastställts.</span><span class="sxs-lookup"><span data-stu-id="c77de-113">The order of keys in a hash table is not determined.</span></span>

<span data-ttu-id="c77de-114">Nycklarna och värdet i hash-tabeller är också .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="c77de-114">The keys and value in hash tables are also .NET objects.</span></span> <span data-ttu-id="c77de-115">De är oftast strängar eller heltal, men de kan ha valfri objekt typ.</span><span class="sxs-lookup"><span data-stu-id="c77de-115">They are most often strings or integers, but they can have any object type.</span></span> <span data-ttu-id="c77de-116">Du kan också skapa kapslade hash-tabeller där värdet för en nyckel är en annan hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-116">You can also create nested hash tables, in which the value of a key is another hash table.</span></span>

<span data-ttu-id="c77de-117">Hash-tabeller används ofta eftersom de är mycket effektiva för att hitta och hämta data.</span><span class="sxs-lookup"><span data-stu-id="c77de-117">Hash tables are frequently used because they are very efficient for finding and retrieving data.</span></span> <span data-ttu-id="c77de-118">Du kan använda hash-tabeller för att lagra listor och skapa beräknade egenskaper i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c77de-118">You can use hash tables to store lists and to create calculated properties in PowerShell.</span></span> <span data-ttu-id="c77de-119">Och PowerShell har en cmdlet, ConvertFrom-StringData, som konverterar strängar till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-119">And, PowerShell has a cmdlet, ConvertFrom-StringData, that converts strings to a hash table.</span></span>

### <a name="syntax"></a><span data-ttu-id="c77de-120">Syntax</span><span class="sxs-lookup"><span data-stu-id="c77de-120">Syntax</span></span>

<span data-ttu-id="c77de-121">Syntaxen för en hash-tabell är följande:</span><span class="sxs-lookup"><span data-stu-id="c77de-121">The syntax of a hash table is as follows:</span></span>

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="c77de-122">Syntaxen för en ordnad ord lista är följande:</span><span class="sxs-lookup"><span data-stu-id="c77de-122">The syntax of an ordered dictionary is as follows:</span></span>

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

<span data-ttu-id="c77de-123">Attributet [ordnat] introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c77de-123">The [ordered] attribute was introduced in PowerShell 3.0.</span></span>

### <a name="creating-hash-tables"></a><span data-ttu-id="c77de-124">Skapa hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="c77de-124">Creating Hash Tables</span></span>

<span data-ttu-id="c77de-125">Följ dessa rikt linjer om du vill skapa en hash-tabell:</span><span class="sxs-lookup"><span data-stu-id="c77de-125">To create a hash table, follow these guidelines:</span></span>

- <span data-ttu-id="c77de-126">Starta hash-tabellen med ett at-tecken (@).</span><span class="sxs-lookup"><span data-stu-id="c77de-126">Begin the hash table with an at sign (@).</span></span>
- <span data-ttu-id="c77de-127">Omge hash-tabellen med klammerparenteser ( {} ).</span><span class="sxs-lookup"><span data-stu-id="c77de-127">Enclose the hash table in braces ({}).</span></span>
- <span data-ttu-id="c77de-128">Ange ett eller flera nyckel/värde-par för innehållet i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c77de-128">Enter one or more key/value pairs for the content of the hash table.</span></span>
- <span data-ttu-id="c77de-129">Använd ett likhets tecken (=) för att avgränsa varje nyckel från värdet.</span><span class="sxs-lookup"><span data-stu-id="c77de-129">Use an equal sign (=) to separate each key from its value.</span></span>
- <span data-ttu-id="c77de-130">Använd ett semikolon (;) eller en rad brytning för att avgränsa nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="c77de-130">Use a semicolon (;) or a line break to separate the key/value pairs.</span></span>
- <span data-ttu-id="c77de-131">Den nyckel som innehåller blank steg måste stå inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c77de-131">Key that contains spaces must be enclosed in quotation marks.</span></span> <span data-ttu-id="c77de-132">Värdena måste vara giltiga PowerShell-uttryck.</span><span class="sxs-lookup"><span data-stu-id="c77de-132">Values must be valid PowerShell expressions.</span></span> <span data-ttu-id="c77de-133">Strängar måste omges av citat tecken, även om de inte innehåller blank steg.</span><span class="sxs-lookup"><span data-stu-id="c77de-133">Strings must appear in quotation marks, even if they do not include spaces.</span></span>
- <span data-ttu-id="c77de-134">Om du vill hantera hash-tabellen sparar du den i en variabel.</span><span class="sxs-lookup"><span data-stu-id="c77de-134">To manage the hash table, save it in a variable.</span></span>
- <span data-ttu-id="c77de-135">När du tilldelar en ordnad hash-tabell till en variabel placerar du attributet [ordnat] före symbolen "@".</span><span class="sxs-lookup"><span data-stu-id="c77de-135">When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol.</span></span> <span data-ttu-id="c77de-136">Kommandot Miss lyckas om du placerar det före variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="c77de-136">If you place it before the variable name, the command fails.</span></span>

<span data-ttu-id="c77de-137">Om du vill skapa en tom hash-tabell i värdet för $hash, skriver du:</span><span class="sxs-lookup"><span data-stu-id="c77de-137">To create an empty hash table in the value of $hash, type:</span></span>

```powershell
$hash = @{}
```

<span data-ttu-id="c77de-138">Du kan också lägga till nycklar och värden i en hash-tabell när du skapar den.</span><span class="sxs-lookup"><span data-stu-id="c77de-138">You can also add keys and values to a hash table when you create it.</span></span> <span data-ttu-id="c77de-139">Till exempel skapar följande instruktion en hash-tabell med tre nycklar.</span><span class="sxs-lookup"><span data-stu-id="c77de-139">For example, the following statement creates a hash table with three keys.</span></span>

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a><span data-ttu-id="c77de-140">Skapa beställda ord listor</span><span class="sxs-lookup"><span data-stu-id="c77de-140">Creating Ordered Dictionaries</span></span>

<span data-ttu-id="c77de-141">Du kan skapa en ordnad ord lista genom att lägga till ett objekt av typen OrderedDictionary, men det enklaste sättet att skapa en ordnad ord lista använder attributet [ordnat].</span><span class="sxs-lookup"><span data-stu-id="c77de-141">You can create an ordered dictionary by adding an object of the OrderedDictionary type, but the easiest way to create an ordered dictionary is use the [Ordered] attribute.</span></span>

<span data-ttu-id="c77de-142">Attributet [ordnat] introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c77de-142">The [ordered] attribute is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="c77de-143">Placera attributet omedelbart före symbolen "@".</span><span class="sxs-lookup"><span data-stu-id="c77de-143">Place the attribute immediately before the "@" symbol.</span></span>

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

<span data-ttu-id="c77de-144">Du kan använda beställda ord listor på samma sätt som du använder hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="c77de-144">You can use ordered dictionaries in the same way that you use hash tables.</span></span>
<span data-ttu-id="c77de-145">Antingen kan typen användas som värde för parametrar som tar en hash-tabell eller-ord lista (iDictionary).</span><span class="sxs-lookup"><span data-stu-id="c77de-145">Either type can be used as the value of parameters that take a hash table or dictionary (iDictionary).</span></span>

<span data-ttu-id="c77de-146">Du kan inte använda attributet [ordnat] för att konvertera eller omvandla en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-146">You cannot use the [ordered] attribute to convert or cast a hash table.</span></span> <span data-ttu-id="c77de-147">Om du placerar det beställda attributet före variabelns namn, Miss lyckas kommandot med följande fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="c77de-147">If you place the ordered attribute before the variable name, the command fails with the following error message.</span></span>

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

<span data-ttu-id="c77de-148">Om du vill korrigera uttrycket flyttar du attributet [ordnat].</span><span class="sxs-lookup"><span data-stu-id="c77de-148">To correct the expression, move the [ordered] attribute.</span></span>

```powershell
PS C:\> $hash = [ordered]@{}
```

<span data-ttu-id="c77de-149">Du kan omvandla en ordnad ord lista till en hash-tabell, men du kan inte återställa det beställda attributet, även om du rensar variabeln och anger nya värden.</span><span class="sxs-lookup"><span data-stu-id="c77de-149">You can cast an ordered dictionary to a hash table, but you cannot recover the ordered attribute, even if you clear the variable and enter new values.</span></span> <span data-ttu-id="c77de-150">För att återupprätta ordningen måste du ta bort och återskapa variabeln.</span><span class="sxs-lookup"><span data-stu-id="c77de-150">To re-establish the order, you must remove and recreate the variable.</span></span>

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a><span data-ttu-id="c77de-151">Visa hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="c77de-151">Displaying Hash Tables</span></span>

<span data-ttu-id="c77de-152">Om du vill visa en hash-tabell som har sparats i en variabel skriver du variabelns namn.</span><span class="sxs-lookup"><span data-stu-id="c77de-152">To display a hash table that is saved in a variable, type the variable name.</span></span>
<span data-ttu-id="c77de-153">Som standard visas hash-tabeller som en tabell med en kolumn för nycklar och en för-värden.</span><span class="sxs-lookup"><span data-stu-id="c77de-153">By default, a hash tables is displayed as a table with one column for keys and one for values.</span></span>

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

<span data-ttu-id="c77de-154">Hash-tabeller har nycklar och värden egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c77de-154">Hash tables have Keys and Values properties.</span></span> <span data-ttu-id="c77de-155">Använd punkt notation för att visa alla nycklar eller alla värden.</span><span class="sxs-lookup"><span data-stu-id="c77de-155">Use dot notation to display all of the keys or all of the values.</span></span>

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

<span data-ttu-id="c77de-156">Varje nyckel namn är också en egenskap för hash-tabellen och dess värde är värdet för nyckel namns egenskapen.</span><span class="sxs-lookup"><span data-stu-id="c77de-156">Each key name is also a property of the hash table, and its value is the value of the key-name property.</span></span> <span data-ttu-id="c77de-157">Använd följande format för att Visa egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c77de-157">Use the following format to display the property values.</span></span>

```powershell
$hashtable.<key>
<value>
```

<span data-ttu-id="c77de-158">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c77de-158">For example:</span></span>

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

<span data-ttu-id="c77de-159">Om nyckel namnet kolliderar med ett av egenskaps namnen för typ av hash-typ, kan du använda `PSBase` för att få åtkomst till dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c77de-159">If the key name collides with one of the property names of the HashTable type, you can use `PSBase` to access those properties.</span></span> <span data-ttu-id="c77de-160">Om nyckel namnet till exempel är `keys` och du vill returnera en samling nycklar använder du följande syntax:</span><span class="sxs-lookup"><span data-stu-id="c77de-160">For example, if the key name is `keys` and you want to return the collection of Keys, use this syntax:</span></span>

```powershell
$hashtable.PSBase.Keys
```

<span data-ttu-id="c77de-161">Hash-tabeller har en Count-egenskap som anger antalet nyckel/värde-par i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c77de-161">Hash tables have a Count property that indicates the number of key-value pairs in the hash table.</span></span>

```powershell
C:\PS> $hash.count
3
```

<span data-ttu-id="c77de-162">Hash-tabellens tabeller är inte matriser, så du kan inte använda ett heltal som ett index i hash-tabellen, men du kan använda ett nyckel namn för att indexera till hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c77de-162">Hash table tables are not arrays, so you cannot use an integer as an index into the hash table, but you can use a key name to index into the hash table.</span></span>
<span data-ttu-id="c77de-163">Om nyckeln är ett sträng värde omger du nyckel namnet med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c77de-163">If the key is a string value, enclose the key name in quotation marks.</span></span>

<span data-ttu-id="c77de-164">Exempel:</span><span class="sxs-lookup"><span data-stu-id="c77de-164">For example:</span></span>

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a><span data-ttu-id="c77de-165">Lägga till och ta bort nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c77de-165">Adding and Removing Keys and Values</span></span>

<span data-ttu-id="c77de-166">Använd följande kommando format om du vill lägga till nycklar och värden i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-166">To add keys and values to a hash table, use the following command format.</span></span>

```powershell
$hash["<key>"] = "<value>"
```

<span data-ttu-id="c77de-167">Om du till exempel vill lägga till en "Time"-nyckel med värdet "Now" i hash-tabellen använder du följande uttryck.</span><span class="sxs-lookup"><span data-stu-id="c77de-167">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash["Time"] = "Now"
```

<span data-ttu-id="c77de-168">Du kan också lägga till nycklar och värden i en hash-tabell med hjälp av metoden Add i objektet system. Collections. hash.</span><span class="sxs-lookup"><span data-stu-id="c77de-168">You can also add keys and values to a hash table by using the Add method of the System.Collections.Hashtable object.</span></span> <span data-ttu-id="c77de-169">Metoden Add har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="c77de-169">The Add method has the following syntax:</span></span>

```powershell
Add(Key, Value)
```

<span data-ttu-id="c77de-170">Om du till exempel vill lägga till en "Time"-nyckel med värdet "Now" i hash-tabellen använder du följande uttryck.</span><span class="sxs-lookup"><span data-stu-id="c77de-170">For example, to add a "Time" key with a value of "Now" to the hash table, use the following statement format.</span></span>

```powershell
$hash.Add("Time", "Now")
```

<span data-ttu-id="c77de-171">Du kan också lägga till nycklar och värden i en hash-tabell med hjälp av additionsoperatorn (+) för att lägga till en hash-tabell i en befintlig hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-171">And, you can add keys and values to a hash table by using the addition operator (+) to add a hash table to an existing hash table.</span></span> <span data-ttu-id="c77de-172">Följande uttryck lägger till exempel till en "Time"-nyckel med värdet "Now" i hash-tabellen i $hash variabeln.</span><span class="sxs-lookup"><span data-stu-id="c77de-172">For example, the following statement adds a "Time" key with a value of "Now" to the hash table in the $hash variable.</span></span>

```powershell
$hash = $hash + @{Time="Now"}
```

<span data-ttu-id="c77de-173">Du kan också lägga till värden som lagras i variabler.</span><span class="sxs-lookup"><span data-stu-id="c77de-173">You can also add values that are stored in variables.</span></span>

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

<span data-ttu-id="c77de-174">Du kan inte använda en subtraktion-operator för att ta bort ett nyckel/värde-par från en hash-tabell, men du kan använda metoden Remove för objektet hash-objekt.</span><span class="sxs-lookup"><span data-stu-id="c77de-174">You cannot use a subtraction operator to remove a key/value pair from a hash table, but you can use the Remove method of the Hashtable object.</span></span> <span data-ttu-id="c77de-175">Metoden Remove tar nyckeln som värde.</span><span class="sxs-lookup"><span data-stu-id="c77de-175">The Remove method takes the key as its value.</span></span>

<span data-ttu-id="c77de-176">Metoden Remove har följande syntax:</span><span class="sxs-lookup"><span data-stu-id="c77de-176">The Remove method has the following syntax:</span></span>

```
Remove(Key)
```

<span data-ttu-id="c77de-177">Om du till exempel vill ta bort tid = nu nyckel/värde-paret från hash-tabellen i värdet för variabeln $hash, skriver du:</span><span class="sxs-lookup"><span data-stu-id="c77de-177">For example, to remove the Time=Now key/value pair from the hash table in the value of the $hash variable, type:</span></span>

```powershell
$hash.Remove("Time")
```

<span data-ttu-id="c77de-178">Du kan använda alla egenskaper och metoder för hash-objekt i PowerShell, inklusive innehåller, rensa, klona och CopyTo.</span><span class="sxs-lookup"><span data-stu-id="c77de-178">You can use all of the properties and methods of Hashtable objects in PowerShell, including Contains, Clear, Clone, and CopyTo.</span></span> <span data-ttu-id="c77de-179">Mer information om hash-objekt finns i [system. Collections. hash](/dotnet/api/system.collections.hashtable).</span><span class="sxs-lookup"><span data-stu-id="c77de-179">For more information about Hashtable objects, see [System.Collections.Hashtable](/dotnet/api/system.collections.hashtable).</span></span>

### <a name="object-types-in-hashtables"></a><span data-ttu-id="c77de-180">Objekt typer i hash</span><span class="sxs-lookup"><span data-stu-id="c77de-180">Object Types in HashTables</span></span>

<span data-ttu-id="c77de-181">Nycklar och värden i en hash-tabell kan ha vilken .NET-objekt typ som helst, och en enda hash-tabell kan ha nycklar och värden av flera typer.</span><span class="sxs-lookup"><span data-stu-id="c77de-181">The keys and values in a hash table can have any .NET object type, and a single hash table can have keys and values of multiple types.</span></span>

<span data-ttu-id="c77de-182">Följande instruktion skapar en hash-tabell med process namns strängar och bearbetar objekt värden och sparar dem i `$p` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c77de-182">The following statement creates a hash table of process name strings and process object values and saves it in the `$p` variable.</span></span>

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

<span data-ttu-id="c77de-183">Du kan visa hash-tabellen i `$p` och använda nyckel namns egenskaperna för att visa värdena.</span><span class="sxs-lookup"><span data-stu-id="c77de-183">You can display the hash table in `$p` and use the key-name properties to display the values.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

<span data-ttu-id="c77de-184">Nycklarna i en hash-tabell kan också vara vilken .NET-typ som helst.</span><span class="sxs-lookup"><span data-stu-id="c77de-184">The keys in a hash table can also be any .NET type.</span></span> <span data-ttu-id="c77de-185">Följande instruktion lägger till ett nyckel/värde-par till hash-tabellen i `$p` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c77de-185">The following statement adds a key/value pair to the hash table in the `$p` variable.</span></span> <span data-ttu-id="c77de-186">Nyckeln är ett tjänst objekt som representerar WinRM-tjänsten och värdet är tjänstens aktuella status.</span><span class="sxs-lookup"><span data-stu-id="c77de-186">The key is a Service object that represents the WinRM service, and the value is the current status of the service.</span></span>

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

<span data-ttu-id="c77de-187">Du kan visa och komma åt det nya nyckel/värde-paret genom att använda samma metoder som du använder för andra par i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="c77de-187">You can display and access the new key/value pair by using the same methods that you use for other pairs in the hash table.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

<span data-ttu-id="c77de-188">Nycklar och värden i en hash-tabell kan också vara hash-objekt.</span><span class="sxs-lookup"><span data-stu-id="c77de-188">The keys and values in a hash table can also be Hashtable objects.</span></span> <span data-ttu-id="c77de-189">Följande uttryck lägger till nyckel/värde-par till hash-tabellen i `$p` variabeln som nyckeln är en sträng, Hash2 och värdet är en hash-tabell med tre nyckel/värde-par.</span><span class="sxs-lookup"><span data-stu-id="c77de-189">The following statement adds key/value pair to the hash table in the `$p` variable in which the key is a string, Hash2, and the value is a hash table with three key/value pairs.</span></span>

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

<span data-ttu-id="c77de-190">Du kan visa och komma åt de nya värdena med samma metoder.</span><span class="sxs-lookup"><span data-stu-id="c77de-190">You can display and access the new values by using the same methods.</span></span>

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a><span data-ttu-id="c77de-191">Sortera nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c77de-191">Sorting Keys and Values</span></span>

<span data-ttu-id="c77de-192">Objekten i en hash-tabell är osorterade i ordningsföljd.</span><span class="sxs-lookup"><span data-stu-id="c77de-192">The items in a hash table are intrinsically unordered.</span></span> <span data-ttu-id="c77de-193">Nyckel-/värdeparen kan visas i en annan ordning varje gången du visar dem.</span><span class="sxs-lookup"><span data-stu-id="c77de-193">The key/value pairs might appear in a different order each time that you display them.</span></span>

<span data-ttu-id="c77de-194">Även om du inte kan sortera en hash-tabell kan du använda GetEnumerator-metoden för hash-tabeller för att räkna upp nycklar och värden, och sedan använda cmdleten Sort-Object för att sortera uppräknade värden för visning.</span><span class="sxs-lookup"><span data-stu-id="c77de-194">Although you cannot sort a hash table, you can use the GetEnumerator method of hash tables to enumerate the keys and values, and then use the Sort-Object cmdlet to sort the enumerated values for display.</span></span>

<span data-ttu-id="c77de-195">Följande kommandon räknar exempelvis upp nycklar och värden i hash-tabellen i `$p` variabeln och sorterar sedan nycklarna i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="c77de-195">For example, the following commands enumerate the keys and values in the hash table in the `$p` variable and then sort the keys in alphabetical order.</span></span>

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

<span data-ttu-id="c77de-196">Följande kommando använder samma procedur för att sortera hash-värden i fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="c77de-196">The following command uses the same procedure to sort the hash values in descending order.</span></span>

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a><span data-ttu-id="c77de-197">Skapa objekt från hash-tabeller</span><span class="sxs-lookup"><span data-stu-id="c77de-197">Creating Objects from Hash Tables</span></span>

<span data-ttu-id="c77de-198">Från och med PowerShell 3,0 kan du skapa ett objekt från en hash-tabell med egenskaper och egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="c77de-198">Beginning in PowerShell 3.0, you can create an object from a hash table of properties and property values.</span></span>

<span data-ttu-id="c77de-199">Syntaxen ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="c77de-199">The syntax is as follows:</span></span>

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

<span data-ttu-id="c77de-200">Den här metoden fungerar bara för klasser som har en konstruktor som är null, det vill säga en konstruktor som inte har några parametrar.</span><span class="sxs-lookup"><span data-stu-id="c77de-200">This method works only for classes that have a null constructor, that is, a constructor that has no parameters.</span></span> <span data-ttu-id="c77de-201">Objekt egenskaperna måste vara offentliga och kan anges.</span><span class="sxs-lookup"><span data-stu-id="c77de-201">The object properties must be public and settable.</span></span>

<span data-ttu-id="c77de-202">Mer information finns i [about_Object_Creation](about_Object_Creation.md).</span><span class="sxs-lookup"><span data-stu-id="c77de-202">For more information, see [about_Object_Creation](about_Object_Creation.md).</span></span>

### <a name="convertfrom-stringdata"></a><span data-ttu-id="c77de-203">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="c77de-203">ConvertFrom-StringData</span></span>

<span data-ttu-id="c77de-204">`ConvertFrom-StringData`Cmdleten konverterar en sträng eller en här-sträng med nyckel/värde-par till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-204">The `ConvertFrom-StringData` cmdlet converts a string or a here-string of key/value pairs into a hash table.</span></span> <span data-ttu-id="c77de-205">Du kan använda `ConvertFrom-StringData` cmdleten på ett säkert sätt i avsnittet data i ett skript, och du kan använda den med- `Import-LocalizedData` cmdleten för att Visa användar meddelanden i användar gränssnitts kulturen (UI) för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c77de-205">You can use the `ConvertFrom-StringData` cmdlet safely in the Data section of a script, and you can use it with the `Import-LocalizedData` cmdlet to display user messages in the user-interface (UI) culture of the current user.</span></span>

<span data-ttu-id="c77de-206">Här – strängarna är särskilt användbara när värdena i hash-tabellen innehåller citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c77de-206">Here-strings are especially useful when the values in the hash table include quotation marks.</span></span> <span data-ttu-id="c77de-207">Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c77de-207">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

<span data-ttu-id="c77de-208">I följande exempel visas hur du skapar en här-sträng av användar meddelandena i föregående exempel och hur du använder `ConvertFrom-StringData` för att konvertera dem från en sträng till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-208">The following example shows how to create a here-string of the user messages in the previous example and how to use `ConvertFrom-StringData` to convert them from a string into a hash table.</span></span>

<span data-ttu-id="c77de-209">Följande kommando skapar en här-sträng för nyckel/värde-par och sparar det i \$ variabeln String.</span><span class="sxs-lookup"><span data-stu-id="c77de-209">The following command creates a here-string of the key/value pairs and then saves it in the \$string variable.</span></span>

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

<span data-ttu-id="c77de-210">Det här kommandot använder cmdleten ConvertFrom-StringData för att konvertera denna-sträng till en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c77de-210">This command uses the ConvertFrom-StringData cmdlet to convert the here-string into a hash table.</span></span>

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

<span data-ttu-id="c77de-211">Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="c77de-211">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c77de-212">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="c77de-212">SEE ALSO</span></span>

[<span data-ttu-id="c77de-213">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="c77de-213">about_Arrays</span></span>](about_Arrays.md)

[<span data-ttu-id="c77de-214">about_Object_Creation</span><span class="sxs-lookup"><span data-stu-id="c77de-214">about_Object_Creation</span></span>](about_Object_Creation.md)

[<span data-ttu-id="c77de-215">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="c77de-215">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="c77de-216">about_Script_Internationalization</span><span class="sxs-lookup"><span data-stu-id="c77de-216">about_Script_Internationalization</span></span>](about_Script_Internationalization.md)

[<span data-ttu-id="c77de-217">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="c77de-217">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[<span data-ttu-id="c77de-218">Importera – LocalizedData</span><span class="sxs-lookup"><span data-stu-id="c77de-218">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[<span data-ttu-id="c77de-219">System. Collections. hash</span><span class="sxs-lookup"><span data-stu-id="c77de-219">System.Collections.Hashtable</span></span>](/dotnet/api/system.collections.hashtable)
