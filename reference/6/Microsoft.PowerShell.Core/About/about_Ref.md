---
description: Beskriver hur du skapar och använder en variabel av typen referens. Du kan använda variabler för referens typ för att tillåta en funktion att ändra värdet för en variabel som skickas till den.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: fefc0f002db0b9591b2d23e148db381f7413871f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270518"
---
# <a name="about-ref"></a><span data-ttu-id="87898-105">Om Ref</span><span class="sxs-lookup"><span data-stu-id="87898-105">About Ref</span></span>

## <a name="short-description"></a><span data-ttu-id="87898-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="87898-106">Short description</span></span>
<span data-ttu-id="87898-107">Beskriver hur du skapar och använder en variabel av typen referens.</span><span class="sxs-lookup"><span data-stu-id="87898-107">Describes how to create and use a reference type variable.</span></span> <span data-ttu-id="87898-108">Du kan använda variabler för referens typ för att tillåta en funktion att ändra värdet för en variabel som skickas till den.</span><span class="sxs-lookup"><span data-stu-id="87898-108">You can use reference type variables to permit a function to change the value of a variable that is passed to it.</span></span>

## <a name="long-description"></a><span data-ttu-id="87898-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="87898-109">Long description</span></span>

<span data-ttu-id="87898-110">Du kan skicka variabler till funktioner *efter referens* eller *värde*.</span><span class="sxs-lookup"><span data-stu-id="87898-110">You can pass variables to functions *by reference* or *by value*.</span></span>

<span data-ttu-id="87898-111">När du skickar en variabel *efter värde* skickar du en kopia av data.</span><span class="sxs-lookup"><span data-stu-id="87898-111">When you pass a variable *by value* , you are passing a copy of the data.</span></span>

<span data-ttu-id="87898-112">I följande exempel ändrar funktionen värdet för variabeln som skickas till den.</span><span class="sxs-lookup"><span data-stu-id="87898-112">In the following example, the function changes the value of the variable passed to it.</span></span> <span data-ttu-id="87898-113">I PowerShell är heltal värde typer, så de skickas med värdet.</span><span class="sxs-lookup"><span data-stu-id="87898-113">In PowerShell, integers are value types so they are passed by value.</span></span>
<span data-ttu-id="87898-114">Värdet för `$var` är därför oförändrat utanför omfånget för funktionen.</span><span class="sxs-lookup"><span data-stu-id="87898-114">Therefore, the value of `$var` is unchanged outside the scope of the function.</span></span>

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

<span data-ttu-id="87898-115">I följande exempel skickas en variabel som innehåller en `Hashtable` funktion till en funktion.</span><span class="sxs-lookup"><span data-stu-id="87898-115">In the following example, a variable containing a `Hashtable` is passed to a function.</span></span> <span data-ttu-id="87898-116">`Hashtable` är en objekt typ som standard skickas den till funktionen *efter referens*.</span><span class="sxs-lookup"><span data-stu-id="87898-116">`Hashtable` is an object type so by default it is passed to the function *by reference*.</span></span>

<span data-ttu-id="87898-117">När en variabel skickas *efter referens* kan funktionen ändra data och ändringen fortsätter när funktionen har körts.</span><span class="sxs-lookup"><span data-stu-id="87898-117">When passing a variable *by reference* , the function can change the data and that change persists after the function executes.</span></span>

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

<span data-ttu-id="87898-118">Funktionen lägger till ett nytt nyckel/värde-par som finns kvar utanför funktionens omfång.</span><span class="sxs-lookup"><span data-stu-id="87898-118">The function adds a new key-value pair that persists outside of the function's scope.</span></span>

### <a name="writing-functions-to-accept-reference-parameters"></a><span data-ttu-id="87898-119">Skriva funktioner för att acceptera referens parametrar</span><span class="sxs-lookup"><span data-stu-id="87898-119">Writing functions to accept reference parameters</span></span>

<span data-ttu-id="87898-120">Du kan koda dina funktioner för att ta en parameter som en referens, oavsett vilken typ av data som skickas.</span><span class="sxs-lookup"><span data-stu-id="87898-120">You can code your functions to take a parameter as a reference, regardless of the type of data passed.</span></span> <span data-ttu-id="87898-121">Detta kräver att du anger parametrarna typ som `System.Management.Automation.PSReference` eller `[ref]` .</span><span class="sxs-lookup"><span data-stu-id="87898-121">This requires that you specify the parameters type as `System.Management.Automation.PSReference`, or `[ref]`.</span></span>

<span data-ttu-id="87898-122">När du använder referenser måste du använda `Value` egenskap av `System.Management.Automation.PSReference` typ för att komma åt dina data.</span><span class="sxs-lookup"><span data-stu-id="87898-122">When using references, you must use the `Value` property of the `System.Management.Automation.PSReference` type to access your data.</span></span>

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

<span data-ttu-id="87898-123">Om du vill skicka en variabel till en parameter som förväntar sig en referens måste du skriva omvandla variabeln som en referens.</span><span class="sxs-lookup"><span data-stu-id="87898-123">To pass a variable to a parameter that expects a reference, you must type cast your variable as a reference.</span></span>

> [!NOTE]
> <span data-ttu-id="87898-124">Hakparenteser och parenteser är båda obligatoriska.</span><span class="sxs-lookup"><span data-stu-id="87898-124">The brackets and parenthesis are BOTH required.</span></span>

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a><span data-ttu-id="87898-125">Skicka referenser till .NET-metoder</span><span class="sxs-lookup"><span data-stu-id="87898-125">Passing references to .NET methods</span></span>

<span data-ttu-id="87898-126">Vissa .NET-metoder kan kräva att du skickar en variabel som referens.</span><span class="sxs-lookup"><span data-stu-id="87898-126">Some .NET methods may require you to pass a variable as a reference.</span></span> <span data-ttu-id="87898-127">När metodens definition använder nyckelorden `in` , `out` eller `ref` på en parameter, förväntas en referens.</span><span class="sxs-lookup"><span data-stu-id="87898-127">When the method's definition uses the keywords `in`, `out`, or `ref` on a parameter, it expects a reference.</span></span>

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

<span data-ttu-id="87898-128">`TryParse`Metoden försöker parsa en sträng som ett heltal.</span><span class="sxs-lookup"><span data-stu-id="87898-128">The `TryParse` method attempts to parse a string as an integer.</span></span> <span data-ttu-id="87898-129">Om metoden lyckas returneras `$true` och resultatet lagras i variabeln som du skickade **med referens**.</span><span class="sxs-lookup"><span data-stu-id="87898-129">If the method succeeds, it returns `$true`, and the result is stored in the variable you passed **by reference**.</span></span>

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a><span data-ttu-id="87898-130">Referenser och omfattningar</span><span class="sxs-lookup"><span data-stu-id="87898-130">References and scopes</span></span>

<span data-ttu-id="87898-131">Referenser tillåter att värdet för en variabel i det överordnade omfånget ändras inom ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="87898-131">References allow the value of a variable in the parent scope to be changed within a child scope.</span></span>

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

<span data-ttu-id="87898-132">Endast variabeln av referens typen ändrades.</span><span class="sxs-lookup"><span data-stu-id="87898-132">Only the reference type's variable was changed.</span></span>

## <a name="see-also"></a><span data-ttu-id="87898-133">Se även</span><span class="sxs-lookup"><span data-stu-id="87898-133">See also</span></span>

[<span data-ttu-id="87898-134">about_Variables</span><span class="sxs-lookup"><span data-stu-id="87898-134">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="87898-135">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="87898-135">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="87898-136">about_Functions</span><span class="sxs-lookup"><span data-stu-id="87898-136">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="87898-137">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="87898-137">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="87898-138">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="87898-138">about_Scopes</span></span>](about_scopes.md)
