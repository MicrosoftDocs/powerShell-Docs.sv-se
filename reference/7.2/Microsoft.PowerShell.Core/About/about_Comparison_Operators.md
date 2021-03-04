---
description: Beskriver de operatorer som jämför värden i PowerShell.
Locale: en-US
ms.date: 02/19/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 73a83e1cd93c3467857d5eded8ad6c384e548937
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685302"
---
# <a name="about-comparison-operators"></a><span data-ttu-id="84b8f-103">Om jämförelse operatorer</span><span class="sxs-lookup"><span data-stu-id="84b8f-103">About Comparison Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="84b8f-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="84b8f-104">Short description</span></span>

<span data-ttu-id="84b8f-105">Jämförelse operatorerna i PowerShell kan antingen jämföra två värden eller filtrera element i en samling mot ett indatavärde.</span><span class="sxs-lookup"><span data-stu-id="84b8f-105">The comparison operators in PowerShell can either compare two values or filter elements of a collection against an input value.</span></span>

## <a name="long-description"></a><span data-ttu-id="84b8f-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="84b8f-106">Long description</span></span>

<span data-ttu-id="84b8f-107">Med jämförelse operatorer kan du jämföra värden eller hitta värden som matchar angivna mönster.</span><span class="sxs-lookup"><span data-stu-id="84b8f-107">Comparison operators let you compare values or finding values that match specified patterns.</span></span> <span data-ttu-id="84b8f-108">PowerShell innehåller följande jämförelse operatorer:</span><span class="sxs-lookup"><span data-stu-id="84b8f-108">PowerShell includes the following comparison operators:</span></span>

|    <span data-ttu-id="84b8f-109">Typ</span><span class="sxs-lookup"><span data-stu-id="84b8f-109">Type</span></span>     |   <span data-ttu-id="84b8f-110">Operator</span><span class="sxs-lookup"><span data-stu-id="84b8f-110">Operator</span></span>   |              <span data-ttu-id="84b8f-111">Jämförelse test</span><span class="sxs-lookup"><span data-stu-id="84b8f-111">Comparison test</span></span>              |
| ----------- | ------------ | ----------------------------------------- |
| <span data-ttu-id="84b8f-112">Likhet</span><span class="sxs-lookup"><span data-stu-id="84b8f-112">Equality</span></span>    | <span data-ttu-id="84b8f-113">-EQ</span><span class="sxs-lookup"><span data-stu-id="84b8f-113">-eq</span></span>          | <span data-ttu-id="84b8f-114">lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-114">equals</span></span>                                    |
|             | <span data-ttu-id="84b8f-115">-Ne</span><span class="sxs-lookup"><span data-stu-id="84b8f-115">-ne</span></span>          | <span data-ttu-id="84b8f-116">inte lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-116">not equals</span></span>                                |
|             | <span data-ttu-id="84b8f-117">-gt</span><span class="sxs-lookup"><span data-stu-id="84b8f-117">-gt</span></span>          | <span data-ttu-id="84b8f-118">större än</span><span class="sxs-lookup"><span data-stu-id="84b8f-118">greater than</span></span>                              |
|             | <span data-ttu-id="84b8f-119">-ge</span><span class="sxs-lookup"><span data-stu-id="84b8f-119">-ge</span></span>          | <span data-ttu-id="84b8f-120">större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-120">greater than or equal</span></span>                     |
|             | <span data-ttu-id="84b8f-121">-lt</span><span class="sxs-lookup"><span data-stu-id="84b8f-121">-lt</span></span>          | <span data-ttu-id="84b8f-122">mindre än</span><span class="sxs-lookup"><span data-stu-id="84b8f-122">less than</span></span>                                 |
|             | <span data-ttu-id="84b8f-123">-Le</span><span class="sxs-lookup"><span data-stu-id="84b8f-123">-le</span></span>          | <span data-ttu-id="84b8f-124">mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-124">less than or equal</span></span>                        |
| <span data-ttu-id="84b8f-125">Matching</span><span class="sxs-lookup"><span data-stu-id="84b8f-125">Matching</span></span>    | <span data-ttu-id="84b8f-126">– som</span><span class="sxs-lookup"><span data-stu-id="84b8f-126">-like</span></span>        | <span data-ttu-id="84b8f-127">sträng matchar mönster för jokertecken</span><span class="sxs-lookup"><span data-stu-id="84b8f-127">string matches wildcard pattern</span></span>           |
|             | <span data-ttu-id="84b8f-128">-notlike</span><span class="sxs-lookup"><span data-stu-id="84b8f-128">-notlike</span></span>     | <span data-ttu-id="84b8f-129">strängen matchar inte mönstret jokertecken</span><span class="sxs-lookup"><span data-stu-id="84b8f-129">string does not match wildcard pattern</span></span>    |
|             | <span data-ttu-id="84b8f-130">-matcha</span><span class="sxs-lookup"><span data-stu-id="84b8f-130">-match</span></span>       | <span data-ttu-id="84b8f-131">sträng matchar regex-mönster</span><span class="sxs-lookup"><span data-stu-id="84b8f-131">string matches regex pattern</span></span>              |
|             | <span data-ttu-id="84b8f-132">-notmatch</span><span class="sxs-lookup"><span data-stu-id="84b8f-132">-notmatch</span></span>    | <span data-ttu-id="84b8f-133">strängen matchar inte regex-mönstret</span><span class="sxs-lookup"><span data-stu-id="84b8f-133">string does not match regex pattern</span></span>       |
| <span data-ttu-id="84b8f-134">Ny funktion</span><span class="sxs-lookup"><span data-stu-id="84b8f-134">Replacement</span></span> | <span data-ttu-id="84b8f-135">-Ersätt</span><span class="sxs-lookup"><span data-stu-id="84b8f-135">-replace</span></span>     | <span data-ttu-id="84b8f-136">ersätter strängar som matchar ett regex-mönster</span><span class="sxs-lookup"><span data-stu-id="84b8f-136">replaces strings matching a regex pattern</span></span> |
| <span data-ttu-id="84b8f-137">Behållare</span><span class="sxs-lookup"><span data-stu-id="84b8f-137">Containment</span></span> | <span data-ttu-id="84b8f-138">– innehåller</span><span class="sxs-lookup"><span data-stu-id="84b8f-138">-contains</span></span>    | <span data-ttu-id="84b8f-139">samlingen innehåller ett värde</span><span class="sxs-lookup"><span data-stu-id="84b8f-139">collection contains a value</span></span>               |
|             | <span data-ttu-id="84b8f-140">-notcontains</span><span class="sxs-lookup"><span data-stu-id="84b8f-140">-notcontains</span></span> | <span data-ttu-id="84b8f-141">samlingen innehåller inget värde</span><span class="sxs-lookup"><span data-stu-id="84b8f-141">collection does not contain a value</span></span>       |
|             | <span data-ttu-id="84b8f-142">– in</span><span class="sxs-lookup"><span data-stu-id="84b8f-142">-in</span></span>          | <span data-ttu-id="84b8f-143">värdet finns i en samling</span><span class="sxs-lookup"><span data-stu-id="84b8f-143">value is in a collection</span></span>                  |
|             | <span data-ttu-id="84b8f-144">-notin</span><span class="sxs-lookup"><span data-stu-id="84b8f-144">-notin</span></span>       | <span data-ttu-id="84b8f-145">värdet finns inte i en samling</span><span class="sxs-lookup"><span data-stu-id="84b8f-145">value is not in a collection</span></span>              |
| <span data-ttu-id="84b8f-146">Typ</span><span class="sxs-lookup"><span data-stu-id="84b8f-146">Type</span></span>        | <span data-ttu-id="84b8f-147">-är</span><span class="sxs-lookup"><span data-stu-id="84b8f-147">-is</span></span>          | <span data-ttu-id="84b8f-148">båda objekten är av samma typ</span><span class="sxs-lookup"><span data-stu-id="84b8f-148">both objects are the same type</span></span>            |
|             | <span data-ttu-id="84b8f-149">– IsNot</span><span class="sxs-lookup"><span data-stu-id="84b8f-149">-isnot</span></span>       | <span data-ttu-id="84b8f-150">objekten är inte av samma typ</span><span class="sxs-lookup"><span data-stu-id="84b8f-150">the objects are not the same type</span></span>         |

## <a name="common-features"></a><span data-ttu-id="84b8f-151">Vanliga funktioner</span><span class="sxs-lookup"><span data-stu-id="84b8f-151">Common features</span></span>

<span data-ttu-id="84b8f-152">Som standard är alla jämförelse operatorer Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="84b8f-152">By default, all comparison operators are case-insensitive.</span></span> <span data-ttu-id="84b8f-153">Om du vill göra en jämförelse operator Skift läges känslig, lägger du till en `c` efter `-` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-153">To make a comparison operator case-sensitive, add a `c` after the `-`.</span></span> <span data-ttu-id="84b8f-154">Till exempel `-ceq` är den Skift läges känsliga versionen av `-eq` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-154">For example, `-ceq` is the case-sensitive version of `-eq`.</span></span> <span data-ttu-id="84b8f-155">Om du vill göra Skift läges känsligheten lägger du till ett `i` före `-` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-155">To make the case-insensitivity explicit, add an `i` before `-`.</span></span> <span data-ttu-id="84b8f-156">Till exempel `-ieq` är den uttryckligen Skift läges känsliga versionen av `-eq` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-156">For example, `-ieq` is the explicitly case-insensitive version of `-eq`.</span></span>

<span data-ttu-id="84b8f-157">När indatamängden för en operator är ett skalärt värde returnerar operatorn ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="84b8f-157">When the input of an operator is a scalar value, the operator returns a **Boolean** value.</span></span> <span data-ttu-id="84b8f-158">När indatatypen är en samling returnerar operatorn elementen i den samling som matchar det högra värdet för uttrycket.</span><span class="sxs-lookup"><span data-stu-id="84b8f-158">When the input is a collection, the operator returns the elements of the collection that match the right-hand value of the expression.</span></span>
<span data-ttu-id="84b8f-159">Om det inte finns några matchningar i samlingen returnerar jämförelse operatorer en tom matris.</span><span class="sxs-lookup"><span data-stu-id="84b8f-159">If there are no matches in the collection, comparison operators return an empty array.</span></span> <span data-ttu-id="84b8f-160">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-160">For example:</span></span>

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

<span data-ttu-id="84b8f-161">Det finns några undantag:</span><span class="sxs-lookup"><span data-stu-id="84b8f-161">There are a few exceptions:</span></span>

- <span data-ttu-id="84b8f-162">Operatorerna inne och Type returnerar alltid ett **booleskt** värde</span><span class="sxs-lookup"><span data-stu-id="84b8f-162">The containment and type operators always return a **Boolean** value</span></span>
- <span data-ttu-id="84b8f-163">`-replace`Operatorn returnerar ersättnings resultatet</span><span class="sxs-lookup"><span data-stu-id="84b8f-163">The `-replace` operator returns the replacement result</span></span>
- <span data-ttu-id="84b8f-164">`-match` `-notmatch` Operatorerna och fyller även i den `$Matches` automatiska variabeln</span><span class="sxs-lookup"><span data-stu-id="84b8f-164">The `-match` and `-notmatch` operators also populate the `$Matches` automatic variable</span></span>

## <a name="equality-operators"></a><span data-ttu-id="84b8f-165">Likhetsoperatorer</span><span class="sxs-lookup"><span data-stu-id="84b8f-165">Equality operators</span></span>

### <a name="-eq-and--ne"></a><span data-ttu-id="84b8f-166">-EQ och-Ne</span><span class="sxs-lookup"><span data-stu-id="84b8f-166">-eq and -ne</span></span>

<span data-ttu-id="84b8f-167">När den vänstra sidan är skalär `-eq` returnerar **True** om den högra sidan är en exakt matchning, annars `-eq` returnerar **false**.</span><span class="sxs-lookup"><span data-stu-id="84b8f-167">When the left-hand side is scalar, `-eq` returns **True** if the right-hand side is an exact match, otherwise, `-eq` returns **False**.</span></span> <span data-ttu-id="84b8f-168">`-ne` är motsatt; den returnerar **falskt** när båda sidorna matchar; annars `-ne` returnerar true.</span><span class="sxs-lookup"><span data-stu-id="84b8f-168">`-ne` does the opposite; it returns **False** when both sides match; otherwise, `-ne` returns True.</span></span>

<span data-ttu-id="84b8f-169">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-169">Example:</span></span>

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

<span data-ttu-id="84b8f-170">När den vänstra sidan är en samling `-eq` returnerar de medlemmar som matchar den högra sidan, medan `-ne` filtrerar dem.</span><span class="sxs-lookup"><span data-stu-id="84b8f-170">When the left-hand side is a collection, `-eq` returns those members that match the right-hand side, while `-ne` filters them out.</span></span>

<span data-ttu-id="84b8f-171">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-171">Example:</span></span>

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

<span data-ttu-id="84b8f-172">Dessa operatorer bearbetar alla element i samlingen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-172">These operators process all elements of the collection.</span></span> <span data-ttu-id="84b8f-173">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-173">Example:</span></span>

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

<span data-ttu-id="84b8f-174">Likhets operatorerna accepterar två objekt, inte bara en skalär eller samling.</span><span class="sxs-lookup"><span data-stu-id="84b8f-174">The equality operators accept any two objects, not just a scalar or collection.</span></span>
<span data-ttu-id="84b8f-175">Men jämförelse resultatet är inte garanterat meningsfullt för slutanvändaren.</span><span class="sxs-lookup"><span data-stu-id="84b8f-175">But the comparison result is not guaranteed to be meaningful for the end-user.</span></span>
<span data-ttu-id="84b8f-176">I följande exempel demonstreras problemet.</span><span class="sxs-lookup"><span data-stu-id="84b8f-176">The following example demonstrates the issue.</span></span>

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

<span data-ttu-id="84b8f-177">I det här exemplet har vi skapat två objekt med identiska egenskaper.</span><span class="sxs-lookup"><span data-stu-id="84b8f-177">In this example, we created two objects with identical properties.</span></span> <span data-ttu-id="84b8f-178">Men resultatet av likhets testet är **falskt** eftersom det är olika objekt.</span><span class="sxs-lookup"><span data-stu-id="84b8f-178">Yet, the equality test result is **False** because they are different objects.</span></span> <span data-ttu-id="84b8f-179">Om du vill skapa jämförbara klasser måste du implementera [system. IEquatable \<T> ][2] i din-klass.</span><span class="sxs-lookup"><span data-stu-id="84b8f-179">To create comparable classes, you need to implement [System.IEquatable\<T>][2] in your class.</span></span> <span data-ttu-id="84b8f-180">I följande exempel demonstreras den partiella implementeringen av en **MyFileInfoSet** -klass som implementerar [system. \<T> IEquatable][2] och har två egenskaper, **fil** och **storlek**.</span><span class="sxs-lookup"><span data-stu-id="84b8f-180">The following example demonstrates the partial implementation of a **MyFileInfoSet** class that implements [System.IEquatable\<T>][2] and has two properties, **File** and **Size**.</span></span> <span data-ttu-id="84b8f-181">`Equals()`Metoden returnerar true om fil-och storleks egenskaperna för två **MyFileInfoSet** -objekt är desamma.</span><span class="sxs-lookup"><span data-stu-id="84b8f-181">The `Equals()` method returns True if the File and Size properties of two **MyFileInfoSet** objects are the same.</span></span>

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

<span data-ttu-id="84b8f-182">Ett framträdande exempel på att jämföra valfria objekt är att ta reda på om de är null.</span><span class="sxs-lookup"><span data-stu-id="84b8f-182">A prominent example of comparing arbitrary objects is to find out if they are null.</span></span> <span data-ttu-id="84b8f-183">Men om du behöver avgöra om en variabel är måste `$null` du ange till `$null` vänster i likhets operatorn.</span><span class="sxs-lookup"><span data-stu-id="84b8f-183">But if you need to determine whether a variable is `$null`, you must put `$null` on the left-hand side of the equality operator.</span></span> <span data-ttu-id="84b8f-184">Det är inte det du förväntar dig att placera det på den högra sidan.</span><span class="sxs-lookup"><span data-stu-id="84b8f-184">Putting it on the right-hand side does not do what you expect.</span></span>

<span data-ttu-id="84b8f-185">Låt oss till exempel `$a` vara en matris som innehåller null-element:</span><span class="sxs-lookup"><span data-stu-id="84b8f-185">For example, let `$a` be an array containing null elements:</span></span>

```powershell
$a = 1, 2, $null, 4, $null, 6
```

<span data-ttu-id="84b8f-186">Följande test som `$a` inte är null.</span><span class="sxs-lookup"><span data-stu-id="84b8f-186">The following tests that `$a` is not null.</span></span>

```powershell
$null -ne $a
```

```output
True
```

<span data-ttu-id="84b8f-187">Följande är en fil som delar ut alla null-element från `$a` :</span><span class="sxs-lookup"><span data-stu-id="84b8f-187">The following, however, filers out all null elements from `$a`:</span></span>

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a><span data-ttu-id="84b8f-188">-gt,-ge,-lt och-Le</span><span class="sxs-lookup"><span data-stu-id="84b8f-188">-gt, -ge, -lt, and -le</span></span>

<span data-ttu-id="84b8f-189">`-gt`, `-ge` , `-lt` , och `-le` beter sig på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="84b8f-189">`-gt`, `-ge`, `-lt`, and `-le` behave very similarly.</span></span> <span data-ttu-id="84b8f-190">När båda sidorna är skalära returneras **True** eller **false** beroende på hur två sidor jämför:</span><span class="sxs-lookup"><span data-stu-id="84b8f-190">When both sides are scalar they return **True** or **False** depending on how the two sides compare:</span></span>

| <span data-ttu-id="84b8f-191">Operator</span><span class="sxs-lookup"><span data-stu-id="84b8f-191">Operator</span></span> | <span data-ttu-id="84b8f-192">Returnerar sant när...</span><span class="sxs-lookup"><span data-stu-id="84b8f-192">Returns True when...</span></span>                   |
| -------- | -------------------------------------- |
| <span data-ttu-id="84b8f-193">-gt</span><span class="sxs-lookup"><span data-stu-id="84b8f-193">-gt</span></span>      | <span data-ttu-id="84b8f-194">Den vänstra sidan är större</span><span class="sxs-lookup"><span data-stu-id="84b8f-194">The left-hand side is greater</span></span>          |
| <span data-ttu-id="84b8f-195">-ge</span><span class="sxs-lookup"><span data-stu-id="84b8f-195">-ge</span></span>      | <span data-ttu-id="84b8f-196">Den vänstra sidan är större än eller lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-196">The left-hand side is greater or equal</span></span> |
| <span data-ttu-id="84b8f-197">-lt</span><span class="sxs-lookup"><span data-stu-id="84b8f-197">-lt</span></span>      | <span data-ttu-id="84b8f-198">Den vänstra sidan är mindre</span><span class="sxs-lookup"><span data-stu-id="84b8f-198">The left-hand side is smaller</span></span>          |
| <span data-ttu-id="84b8f-199">-Le</span><span class="sxs-lookup"><span data-stu-id="84b8f-199">-le</span></span>      | <span data-ttu-id="84b8f-200">Den vänstra sidan är mindre än eller lika med</span><span class="sxs-lookup"><span data-stu-id="84b8f-200">The left-hand side is smaller or equal</span></span> |

<span data-ttu-id="84b8f-201">I följande exempel returnerar alla satser True.</span><span class="sxs-lookup"><span data-stu-id="84b8f-201">In the following examples, all statements return True.</span></span>

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> <span data-ttu-id="84b8f-202">I de flesta programmeringsspråk är större än-operatorn större än `>` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-202">In most programming languages the greater-than operator is `>`.</span></span> <span data-ttu-id="84b8f-203">I PowerShell används det här specialtecknet för omdirigering.</span><span class="sxs-lookup"><span data-stu-id="84b8f-203">In PowerShell, this character is used for redirection.</span></span> <span data-ttu-id="84b8f-204">Mer information finns i [about_Redirection][3].</span><span class="sxs-lookup"><span data-stu-id="84b8f-204">For details, see [about_Redirection][3].</span></span>

<span data-ttu-id="84b8f-205">När den vänstra sidan är en samling, jämför dessa operatörer varje medlem i samlingen med den högra sidan.</span><span class="sxs-lookup"><span data-stu-id="84b8f-205">When the left-hand side is a collection, these operators compare each member of the collection with the right-hand side.</span></span> <span data-ttu-id="84b8f-206">Beroende på deras logik, behåller de antingen eller ignorerar medlemmen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-206">Depending on their logic, they either keep or discard the member.</span></span>

<span data-ttu-id="84b8f-207">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-207">Example:</span></span>

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

<span data-ttu-id="84b8f-208">Dessa operatörer fungerar med alla klasser som implementerar [system. IComparable][1].</span><span class="sxs-lookup"><span data-stu-id="84b8f-208">These operators work with any class that implements [System.IComparable][1].</span></span>

<span data-ttu-id="84b8f-209">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-209">Examples:</span></span>

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

<span data-ttu-id="84b8f-210">Följande exempel visar att det inte finns någon symbol på ett amerikanskt QWERTY-tangentbord som sorteras efter "a".</span><span class="sxs-lookup"><span data-stu-id="84b8f-210">The following example demonstrates that there is no symbol on an American QWERTY keyboard that gets sorted after 'a'.</span></span> <span data-ttu-id="84b8f-211">Den matas en uppsättning som innehåller alla sådana symboler till `-gt` operatorn för att jämföra dem mot "a".</span><span class="sxs-lookup"><span data-stu-id="84b8f-211">It feeds a set containing all such symbols to the `-gt` operator to compare them against 'a'.</span></span> <span data-ttu-id="84b8f-212">Utdata är en tom matris.</span><span class="sxs-lookup"><span data-stu-id="84b8f-212">The output is an empty array.</span></span>

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

<span data-ttu-id="84b8f-213">Om de två sidorna av operatörerna inte är rimligen jämförbara, genererar dessa operatörer ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="84b8f-213">If the two sides of the operators are not reasonably comparable, these operators raise a non-terminating error.</span></span>

## <a name="matching-operators"></a><span data-ttu-id="84b8f-214">Matchande operatorer</span><span class="sxs-lookup"><span data-stu-id="84b8f-214">Matching operators</span></span>

<span data-ttu-id="84b8f-215">Matchande operatorer ( `-like` , `-notlike` , `-match` och `-notmatch` ) hittar element som matchar eller inte matchar ett angivet mönster.</span><span class="sxs-lookup"><span data-stu-id="84b8f-215">The matching operators (`-like`, `-notlike`, `-match`, and `-notmatch`) find elements that match or do not match a specified pattern.</span></span> <span data-ttu-id="84b8f-216">Mönstret för `-like` och `-notlike` är ett jokertecken (som innehåller `*` , `?` , och `[ ]` ), `-match` och `-notmatch` accepterar ett reguljärt uttryck (regex).</span><span class="sxs-lookup"><span data-stu-id="84b8f-216">The pattern for `-like` and `-notlike` is a wildcard expression (containing `*`, `?`, and `[ ]`), while `-match` and `-notmatch` accept a regular expression (Regex).</span></span>

<span data-ttu-id="84b8f-217">Syntax:</span><span class="sxs-lookup"><span data-stu-id="84b8f-217">The syntax is:</span></span>

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

<span data-ttu-id="84b8f-218">När inmatade operatorer är ett skalärt värde returnerar de ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="84b8f-218">When the input of these operators is a scalar value, they return a **Boolean** value.</span></span> <span data-ttu-id="84b8f-219">När indatatypen är en samling med värden returnerar operatörerna alla matchande medlemmar.</span><span class="sxs-lookup"><span data-stu-id="84b8f-219">When the input is a collection of values, the operators return any matching members.</span></span> <span data-ttu-id="84b8f-220">Om det inte finns några matchningar i en samling returnerar operatörerna en tom matris.</span><span class="sxs-lookup"><span data-stu-id="84b8f-220">If there are no matches in a collection, the operators return an empty array.</span></span>

### <a name="-like-and--notlike"></a><span data-ttu-id="84b8f-221">-like och-notlike</span><span class="sxs-lookup"><span data-stu-id="84b8f-221">-like and -notlike</span></span>

<span data-ttu-id="84b8f-222">`-like` och `-notlike` beter sig på samma sätt som `-eq` och `-ne` , men den högra sidan kan vara en sträng som innehåller [jokertecken](about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="84b8f-222">`-like` and `-notlike` behave similarly to `-eq` and `-ne`, but the right-hand side could be a string containing [wildcards](about_Wildcards.md).</span></span>

<span data-ttu-id="84b8f-223">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-223">Example:</span></span>

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a><span data-ttu-id="84b8f-224">-match och-notmatch</span><span class="sxs-lookup"><span data-stu-id="84b8f-224">-match and -notmatch</span></span>

<span data-ttu-id="84b8f-225">`-match` och `-notmatch` Använd reguljära uttryck för att söka efter mönster i värdena för den vänstra sidan.</span><span class="sxs-lookup"><span data-stu-id="84b8f-225">`-match` and `-notmatch` use regular expressions to search for pattern in the left-hand side values.</span></span> <span data-ttu-id="84b8f-226">Reguljära uttryck kan matcha komplexa mönster som e-postadresser, UNC-sökvägar eller formaterade telefonnummer.</span><span class="sxs-lookup"><span data-stu-id="84b8f-226">Regular expressions can match complex patterns like email addresses, UNC paths, or formatted phone numbers.</span></span> <span data-ttu-id="84b8f-227">Den högra strängen måste följa reglerna för [reguljära uttryck](about_Regular_Expressions.md) .</span><span class="sxs-lookup"><span data-stu-id="84b8f-227">The right-hand side string must adhere to the [regular expressions](about_Regular_Expressions.md) rules.</span></span>

<span data-ttu-id="84b8f-228">Skalära exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-228">Scalar examples:</span></span>

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

<span data-ttu-id="84b8f-229">Om indatamängden är en samling returnerar operatorerna de matchande medlemmarna i samlingen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-229">If the input is a collection, the operators return the matching members of that collection.</span></span>

<span data-ttu-id="84b8f-230">Samlings exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-230">Collection examples:</span></span>

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

<span data-ttu-id="84b8f-231">`-match` och `-notmatch` stöder regex-infångnings grupper.</span><span class="sxs-lookup"><span data-stu-id="84b8f-231">`-match` and `-notmatch` support regex capture groups.</span></span> <span data-ttu-id="84b8f-232">Varje gången de körs skrivs den `$Matches` automatiska variabeln över.</span><span class="sxs-lookup"><span data-stu-id="84b8f-232">Each time they run, they overwrite the `$Matches` automatic variable.</span></span> <span data-ttu-id="84b8f-233">När `<input>` är en samling `$Matches` är variabeln `$null` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-233">When `<input>` is a collection the `$Matches` variable is `$null`.</span></span> <span data-ttu-id="84b8f-234">`$Matches` är en **hash** som alltid har en nyckel med namnet "0" som lagrar hela matchningen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-234">`$Matches` is a **Hashtable** that always has a key named '0', which stores the entire match.</span></span> <span data-ttu-id="84b8f-235">Om det reguljära uttrycket innehåller infångnings grupper `$Matches` innehåller ytterligare nycklar för varje grupp.</span><span class="sxs-lookup"><span data-stu-id="84b8f-235">If the regular expression contains capture groups, the `$Matches` contains additional keys for each group.</span></span>

<span data-ttu-id="84b8f-236">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-236">Example:</span></span>

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

<span data-ttu-id="84b8f-237">Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="84b8f-237">For details, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

## <a name="replacement-operator"></a><span data-ttu-id="84b8f-238">Ersättnings operatör</span><span class="sxs-lookup"><span data-stu-id="84b8f-238">Replacement operator</span></span>

### <a name="replacement-with-regular-expressions"></a><span data-ttu-id="84b8f-239">Ersätta med reguljära uttryck</span><span class="sxs-lookup"><span data-stu-id="84b8f-239">Replacement with regular expressions</span></span>

<span data-ttu-id="84b8f-240">`-match`På samma sätt `-replace` använder operatorn reguljära uttryck för att hitta det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="84b8f-240">Like `-match`, the `-replace` operator uses regular expressions to find the specified pattern.</span></span> <span data-ttu-id="84b8f-241">Men till skillnad från `-match` ersätter den matchningen med ett annat angivet värde.</span><span class="sxs-lookup"><span data-stu-id="84b8f-241">But unlike `-match`, it replaces the matches with another specified value.</span></span>

<span data-ttu-id="84b8f-242">Syntax:</span><span class="sxs-lookup"><span data-stu-id="84b8f-242">Syntax:</span></span>

```
<input> -replace <regular-expression>, <substitute>
```

<span data-ttu-id="84b8f-243">Operatorn ersätter hela eller delar av ett värde med det angivna värdet med hjälp av reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="84b8f-243">The operator replaces all or part of a value with the specified value using regular expressions.</span></span> <span data-ttu-id="84b8f-244">Du kan använda operatorn för många administrativa uppgifter, till exempel att byta namn på filer.</span><span class="sxs-lookup"><span data-stu-id="84b8f-244">You can use the operator for many administrative tasks, such as renaming files.</span></span> <span data-ttu-id="84b8f-245">Följande kommando ändrar till exempel fil namns tilläggen för alla `.txt` filer till `.log` :</span><span class="sxs-lookup"><span data-stu-id="84b8f-245">For example, the following command changes the file name extensions of all `.txt` files to `.log`:</span></span>

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

<span data-ttu-id="84b8f-246">Som standard `-replace` är operatorn Skift läges okänslig.</span><span class="sxs-lookup"><span data-stu-id="84b8f-246">By default, the `-replace` operator is case-insensitive.</span></span> <span data-ttu-id="84b8f-247">Använd för att göra det Skift läges känsligt `-creplace` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-247">To make it case sensitive, use `-creplace`.</span></span> <span data-ttu-id="84b8f-248">Använd om du vill göra det uttryckligen Skift läges okänsligt `-ireplace` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-248">To make it explicitly case-insensitive, use `-ireplace`.</span></span>

<span data-ttu-id="84b8f-249">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-249">Examples:</span></span>

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a><span data-ttu-id="84b8f-250">Reguljära uttryck ersättningar</span><span class="sxs-lookup"><span data-stu-id="84b8f-250">Regular expressions substitutions</span></span>

<span data-ttu-id="84b8f-251">Det går också att använda reguljära uttryck för att dynamiskt ersätta text med hjälp av insamlings grupper och ersättningar.</span><span class="sxs-lookup"><span data-stu-id="84b8f-251">It is also possible to use regular expressions to dynamically replace text using capturing groups, and substitutions.</span></span> <span data-ttu-id="84b8f-252">Det går att referera till infångnings grupper i `<substitute>` strängen med dollar tecknet ( `$` ) före grupp-ID: n.</span><span class="sxs-lookup"><span data-stu-id="84b8f-252">Capture groups can be referenced in the `<substitute>` string using the dollar sign (`$`) character before the group identifier.</span></span>

<span data-ttu-id="84b8f-253">I följande exempel `-replace` accepterar operatorn ett användar namn i formatet `DomainName\Username` och konverteras till `Username@DomainName` formatet:</span><span class="sxs-lookup"><span data-stu-id="84b8f-253">In the following example, the `-replace` operator accepts a username in the form of `DomainName\Username` and converts to the `Username@DomainName` format:</span></span>

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> <span data-ttu-id="84b8f-254">`$`Specialtecknet har syntatic-roller i både PowerShell-och reguljära uttryck:</span><span class="sxs-lookup"><span data-stu-id="84b8f-254">The `$` character has syntatic roles in both PowerShell and regular expressions:</span></span>
>
> - <span data-ttu-id="84b8f-255">I PowerShell, mellan dubbla citat tecken, anger den variabler och fungerar som en under Express operator.</span><span class="sxs-lookup"><span data-stu-id="84b8f-255">In PowerShell, between double quotation marks, it designates variables and acts as a subexpression operator.</span></span>
> - <span data-ttu-id="84b8f-256">I regex Sök strängar betecknar det slutet av raden</span><span class="sxs-lookup"><span data-stu-id="84b8f-256">In Regex search strings, it denotes end of the line</span></span>
> - <span data-ttu-id="84b8f-257">I regex-substitutions strängar anger den fångade grupper. Se till att antingen placera dina reguljära uttryck mellan enkla citat tecken eller infoga ett baktick ( `` ` `` )-tecken före.</span><span class="sxs-lookup"><span data-stu-id="84b8f-257">In Regex substitution strings, it denotes captured groups.Be sure to either put your regular expressions between single quotation marks or insert a backtick (`` ` ``) character before them.</span></span>

<span data-ttu-id="84b8f-258">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-258">For example:</span></span>

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

<span data-ttu-id="84b8f-259">`$$` i regex anger en literal `$` .</span><span class="sxs-lookup"><span data-stu-id="84b8f-259">`$$` in Regex denotes a literal `$`.</span></span> <span data-ttu-id="84b8f-260">Detta `$$` i ersättnings strängen som innehåller en litteral `$` i den resulterande ersättningen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-260">This `$$` in the substitution string to include a literal `$` in the resulting replacement.</span></span> <span data-ttu-id="84b8f-261">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-261">For example:</span></span>

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

<span data-ttu-id="84b8f-262">Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md) och [ersättningar i reguljära uttryck][4].</span><span class="sxs-lookup"><span data-stu-id="84b8f-262">To learn more, see [about_Regular_Expressions](about_Regular_Expressions.md) and [Substitutions in Regular Expressions][4].</span></span>

### <a name="substituting-in-a-collection"></a><span data-ttu-id="84b8f-263">Ersätta i en samling</span><span class="sxs-lookup"><span data-stu-id="84b8f-263">Substituting in a collection</span></span>

<span data-ttu-id="84b8f-264">När `<input>` `-replace` operatorn till är en samling, tillämpar PowerShell ersättningen på alla värden i samlingen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-264">When the `<input>` to the `-replace` operator is a collection, PowerShell applies the replacement to every value in the collection.</span></span> <span data-ttu-id="84b8f-265">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-265">For example:</span></span>

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a><span data-ttu-id="84b8f-266">Ersätta med ett skript block</span><span class="sxs-lookup"><span data-stu-id="84b8f-266">Replacement with a script block</span></span>

<span data-ttu-id="84b8f-267">I PowerShell 6 och senare, `-replace` accepterar operatorn också ett skript block som utför ersättningen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-267">In PowerShell 6 and later, the `-replace` operator also accepts a script block that performs the replacement.</span></span> <span data-ttu-id="84b8f-268">Skript blocket körs en gång för varje matchning.</span><span class="sxs-lookup"><span data-stu-id="84b8f-268">The script block runs once for every match.</span></span>

<span data-ttu-id="84b8f-269">Syntax:</span><span class="sxs-lookup"><span data-stu-id="84b8f-269">Syntax:</span></span>

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

<span data-ttu-id="84b8f-270">I-skript blocket använder du den `$_` automatiska variabeln för att få åtkomst till den inmatade text som ersätts och annan användbar information.</span><span class="sxs-lookup"><span data-stu-id="84b8f-270">Within the script block, use the `$_` automatic variable to access the input text being replaced and other useful information.</span></span> <span data-ttu-id="84b8f-271">Den här variabelns klass typ är [system. text. RegularExpressions. match][2].</span><span class="sxs-lookup"><span data-stu-id="84b8f-271">This variable's class type is [System.Text.RegularExpressions.Match][2].</span></span>

<span data-ttu-id="84b8f-272">I följande exempel ersätts varje sekvens med tre siffror med motsvarande tecken.</span><span class="sxs-lookup"><span data-stu-id="84b8f-272">The following example replaces each sequence of three digits with the character equivalents.</span></span> <span data-ttu-id="84b8f-273">Skript blocket körs för varje uppsättning av tre siffror som måste ersättas.</span><span class="sxs-lookup"><span data-stu-id="84b8f-273">The script block runs for each set of three digits that needs to be replaced.</span></span>

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a><span data-ttu-id="84b8f-274">Inne slutnings operatorer</span><span class="sxs-lookup"><span data-stu-id="84b8f-274">Containment operators</span></span>

<span data-ttu-id="84b8f-275">Inne slutnings operatorerna ( `-contains` , `-notcontains` , `-in` och `-notin` ) liknar likhets operatorerna, förutom att de alltid returnerar ett **booleskt** värde, även när indatatypen är en samling.</span><span class="sxs-lookup"><span data-stu-id="84b8f-275">The containment operators (`-contains`, `-notcontains`, `-in`, and `-notin`) are similar to the equality operators, except that they always return a **Boolean** value, even when the input is a collection.</span></span> <span data-ttu-id="84b8f-276">Dessa operatorer slutar att jämföra så fort de identifierar den första matchningen, medan likhets operatorerna utvärderar alla ingående medlemmar.</span><span class="sxs-lookup"><span data-stu-id="84b8f-276">These operators stop comparing as soon as they detect the first match, whereas the equality operators evaluate all input members.</span></span> <span data-ttu-id="84b8f-277">I en mycket stor samling returnerar de här operatorerna snabbare än likhets operatorerna.</span><span class="sxs-lookup"><span data-stu-id="84b8f-277">In a very large collection, these operators return quicker than the equality operators.</span></span>

<span data-ttu-id="84b8f-278">Syntax:</span><span class="sxs-lookup"><span data-stu-id="84b8f-278">Syntax:</span></span>

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a><span data-ttu-id="84b8f-279">-innehåller och-notcontains</span><span class="sxs-lookup"><span data-stu-id="84b8f-279">-contains and -notcontains</span></span>

<span data-ttu-id="84b8f-280">Dessa operatorer anger om en mängd innehåller ett visst element.</span><span class="sxs-lookup"><span data-stu-id="84b8f-280">These operators tell whether a set includes a certain element.</span></span> <span data-ttu-id="84b8f-281">`-contains` returnerar true när den högra sidan (test objekt) matchar ett av elementen i mängden.</span><span class="sxs-lookup"><span data-stu-id="84b8f-281">`-contains` returns True when the right-hand side (test object) matches one of the elements in the set.</span></span> <span data-ttu-id="84b8f-282">`-notcontains` returnerar falskt i stället.</span><span class="sxs-lookup"><span data-stu-id="84b8f-282">`-notcontains` returns False instead.</span></span> <span data-ttu-id="84b8f-283">När test-objektet är en samling använder dessa operatorer referens likhet, d.v.s. de kontrollerar om en av uppsättningens element är samma instans av test-objektet.</span><span class="sxs-lookup"><span data-stu-id="84b8f-283">When the test object is a collection, these operators use reference equality, i.e. they check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="84b8f-284">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-284">Examples:</span></span>

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

<span data-ttu-id="84b8f-285">Mer komplexa exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-285">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a><span data-ttu-id="84b8f-286">-in-och-notin</span><span class="sxs-lookup"><span data-stu-id="84b8f-286">-in and -notin</span></span>

<span data-ttu-id="84b8f-287">`-in` `notin` Operatorerna och har introducerats i PowerShell 3 som omvänt i `contains` och med `-notcontain` operatorerna och.</span><span class="sxs-lookup"><span data-stu-id="84b8f-287">The `-in` and -`notin` operators were introduced in PowerShell 3 as the syntactic reverse of the of `contains` and `-notcontain` operators.</span></span> <span data-ttu-id="84b8f-288">`-in` Returnerar **True** när den vänstra sidan `<test-object>` matchar ett av elementen i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="84b8f-288">`-in` returns **True** when the left-hand side `<test-object>` matches one of the elements in the set.</span></span> <span data-ttu-id="84b8f-289">`-notin` Returnerar **falskt** i stället.</span><span class="sxs-lookup"><span data-stu-id="84b8f-289">`-notin` returns **False** instead.</span></span> <span data-ttu-id="84b8f-290">När test-objektet är en uppsättning använder dessa operatorer referens likhet för att kontrol lera om en av uppsättningens element är samma instans av test-objektet.</span><span class="sxs-lookup"><span data-stu-id="84b8f-290">When the test object is a set, these operators use reference equality to check whether one of the set's elements is the same instance of the test object.</span></span>

<span data-ttu-id="84b8f-291">Följande exempel gör samma sak som exemplen för `-contain` och `-notcontain` gör, men de skrivs med `-in` och `-notin` i stället.</span><span class="sxs-lookup"><span data-stu-id="84b8f-291">The following examples do the same thing that the examples for `-contain` and `-notcontain` do, but they are written with `-in` and `-notin` instead.</span></span>

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

<span data-ttu-id="84b8f-292">Mer komplexa exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-292">More complex examples:</span></span>

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a><span data-ttu-id="84b8f-293">Typ jämförelse</span><span class="sxs-lookup"><span data-stu-id="84b8f-293">Type comparison</span></span>

<span data-ttu-id="84b8f-294">Typ jämförelse operatorer ( `-is` och `-isnot` ) används för att avgöra om ett objekt är en speciell typ.</span><span class="sxs-lookup"><span data-stu-id="84b8f-294">The type comparison operators (`-is` and `-isnot`) are used to determine if an object is a specific type.</span></span>

<span data-ttu-id="84b8f-295">Syntax:</span><span class="sxs-lookup"><span data-stu-id="84b8f-295">Syntax:</span></span>

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

<span data-ttu-id="84b8f-296">Exempel:</span><span class="sxs-lookup"><span data-stu-id="84b8f-296">Example:</span></span>

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a><span data-ttu-id="84b8f-297">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="84b8f-297">SEE ALSO</span></span>

- [<span data-ttu-id="84b8f-298">about_Operators</span><span class="sxs-lookup"><span data-stu-id="84b8f-298">about_Operators</span></span>](about_Operators.md)
- [<span data-ttu-id="84b8f-299">about_Regular_Expressions</span><span class="sxs-lookup"><span data-stu-id="84b8f-299">about_Regular_Expressions</span></span>](about_Regular_Expressions.md)
- [<span data-ttu-id="84b8f-300">about_Wildcards</span><span class="sxs-lookup"><span data-stu-id="84b8f-300">about_Wildcards</span></span>](about_Wildcards.md)
- [<span data-ttu-id="84b8f-301">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="84b8f-301">Compare-Object</span></span>](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [<span data-ttu-id="84b8f-302">-Objekt</span><span class="sxs-lookup"><span data-stu-id="84b8f-302">Foreach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [<span data-ttu-id="84b8f-303">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="84b8f-303">Where-Object</span></span>](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
