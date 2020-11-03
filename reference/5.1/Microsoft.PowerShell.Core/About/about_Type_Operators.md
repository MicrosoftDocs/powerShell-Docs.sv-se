---
description: Beskriver de operatorer som fungerar med Microsoft .NET typer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6ea2ef2f61636d67a8bacf69ff577f477712a165
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272757"
---
# <a name="about-type-operators"></a><span data-ttu-id="9de06-104">Om typ operatorer</span><span class="sxs-lookup"><span data-stu-id="9de06-104">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="9de06-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9de06-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9de06-106">Beskriver de operatorer som fungerar med Microsoft .NET typer.</span><span class="sxs-lookup"><span data-stu-id="9de06-106">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="9de06-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9de06-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9de06-108">Operatorerna boolesk typ ( `-is` och `-isNot` ) avgör om ett objekt är en instans av en angiven .net-typ.</span><span class="sxs-lookup"><span data-stu-id="9de06-108">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="9de06-109">`-is`Operatorn returnerar värdet **True** om typen matchar och värdet **false** annars.</span><span class="sxs-lookup"><span data-stu-id="9de06-109">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="9de06-110">`-isNot`Operatorn returnerar värdet **false** om typen matchar och värdet **True** annars.</span><span class="sxs-lookup"><span data-stu-id="9de06-110">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="9de06-111">`-as`Operatorn försöker konvertera indatamängden till den angivna .net-typen.</span><span class="sxs-lookup"><span data-stu-id="9de06-111">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="9de06-112">Om det lyckas returneras det konverterade objektet.</span><span class="sxs-lookup"><span data-stu-id="9de06-112">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="9de06-113">Om det Miss lyckas returneras `$null` .</span><span class="sxs-lookup"><span data-stu-id="9de06-113">If it fails, it returns `$null`.</span></span> <span data-ttu-id="9de06-114">Det returnerar inget fel.</span><span class="sxs-lookup"><span data-stu-id="9de06-114">It does not return an error.</span></span>

<span data-ttu-id="9de06-115">I följande tabell visas typ operatorerna i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9de06-115">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="9de06-116">Operator</span><span class="sxs-lookup"><span data-stu-id="9de06-116">Operator</span></span>|<span data-ttu-id="9de06-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="9de06-117">Description</span></span>                |<span data-ttu-id="9de06-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="9de06-118">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="9de06-119">Returnerar sant när indatamängden</span><span class="sxs-lookup"><span data-stu-id="9de06-119">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="9de06-120">är en instans av</span><span class="sxs-lookup"><span data-stu-id="9de06-120">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="9de06-121">angiven .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="9de06-121">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="9de06-122">Returnerar sant när indatamängden</span><span class="sxs-lookup"><span data-stu-id="9de06-122">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="9de06-123">inte en instans av</span><span class="sxs-lookup"><span data-stu-id="9de06-123">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="9de06-124">specified.NET-typ.</span><span class="sxs-lookup"><span data-stu-id="9de06-124">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="9de06-125">Konverterar indatamängden till</span><span class="sxs-lookup"><span data-stu-id="9de06-125">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="9de06-126">angiven .NET-typ.</span><span class="sxs-lookup"><span data-stu-id="9de06-126">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="9de06-127">Syntaxen för typ operatörerna är följande:</span><span class="sxs-lookup"><span data-stu-id="9de06-127">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="9de06-128">Du kan också använda följande syntax:</span><span class="sxs-lookup"><span data-stu-id="9de06-128">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="9de06-129">.NET-typen kan skrivas som ett typnamn inom hakparenteser eller en sträng, till exempel `[DateTime]` eller `"DateTime"` för **system. DateTime**.</span><span class="sxs-lookup"><span data-stu-id="9de06-129">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime**.</span></span> <span data-ttu-id="9de06-130">Om typen inte finns i roten för system namn området anger du det fullständiga namnet på objekt typen.</span><span class="sxs-lookup"><span data-stu-id="9de06-130">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="9de06-131">Du kan utelämna "system.".</span><span class="sxs-lookup"><span data-stu-id="9de06-131">You can omit "System.".</span></span> <span data-ttu-id="9de06-132">Om du till exempel vill ange **system. Diagnostics. process** , anger du, `[System.Diagnostics.Process]` `[Diagnostics.Process]` eller `"Diagnostics.Process"` .</span><span class="sxs-lookup"><span data-stu-id="9de06-132">For example, to specify **System.Diagnostics.Process** , enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="9de06-133">Typ operatörerna används alltid som indatamängds objekt som helhet.</span><span class="sxs-lookup"><span data-stu-id="9de06-133">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="9de06-134">Det vill säga om inobjektet är en samling, är det den _samlings_ typ som testas, inte typerna för samlingens _element_.</span><span class="sxs-lookup"><span data-stu-id="9de06-134">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_.</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="9de06-135">– är/isNot-ansvariga</span><span class="sxs-lookup"><span data-stu-id="9de06-135">-is/isNot operators</span></span>

<span data-ttu-id="9de06-136">Operatorerna **boolesk** typ ( `-is` och `-isNot` ) returnerar alltid ett **booleskt** värde, även om indatatypen är en samling objekt.</span><span class="sxs-lookup"><span data-stu-id="9de06-136">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="9de06-137">Om `<input>` är en typ som är samma som eller _härleds_ från .net-typen `-is` returneras operatorn `$True` .</span><span class="sxs-lookup"><span data-stu-id="9de06-137">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="9de06-138">Till exempel härleds **DirectoryInfo** -typen från **FileSystemInfo** -typen.</span><span class="sxs-lookup"><span data-stu-id="9de06-138">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="9de06-139">Därför returnerar båda dessa exempel **Sant**.</span><span class="sxs-lookup"><span data-stu-id="9de06-139">Therefore, both of these examples return **True**.</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="9de06-140">`-is`Operatören kan också matcha gränssnitt om det `<input>` implementerar gränssnittet i jämförelsen.</span><span class="sxs-lookup"><span data-stu-id="9de06-140">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="9de06-141">I det här exemplet är indatamängden en matris.</span><span class="sxs-lookup"><span data-stu-id="9de06-141">In this example, the input is an array.</span></span> <span data-ttu-id="9de06-142">Matriser implementerar gränssnittet **system. Collections. ilist** .</span><span class="sxs-lookup"><span data-stu-id="9de06-142">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="9de06-143">-as-operator</span><span class="sxs-lookup"><span data-stu-id="9de06-143">-as operator</span></span>

<span data-ttu-id="9de06-144">`-as`Operatorn försöker konvertera indatamängden till den angivna .net-typen.</span><span class="sxs-lookup"><span data-stu-id="9de06-144">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="9de06-145">Om det lyckas returneras det konverterade objektet.</span><span class="sxs-lookup"><span data-stu-id="9de06-145">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="9de06-146">Om det Miss lyckas returneras det `$null` .</span><span class="sxs-lookup"><span data-stu-id="9de06-146">It if fails, it returns `$null`.</span></span> <span data-ttu-id="9de06-147">Det returnerar inget fel.</span><span class="sxs-lookup"><span data-stu-id="9de06-147">It does not return an error.</span></span>

<span data-ttu-id="9de06-148">Om `<input>` är en typ som _härleds_ från .net-typen `-as` _skickas genom_ returnerat indatamängds objekt oförändrad.</span><span class="sxs-lookup"><span data-stu-id="9de06-148">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="9de06-149">Till exempel härleds **DirectoryInfo** -typen från **FileSystemInfo** -typen.</span><span class="sxs-lookup"><span data-stu-id="9de06-149">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="9de06-150">Objekt typen är därför oförändrad i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="9de06-150">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="9de06-151">Konvertering av DateTime-typen är kultur känslig</span><span class="sxs-lookup"><span data-stu-id="9de06-151">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="9de06-152">Till skillnad från typ data typs byte fungerar konverteringen till `[DateTime]` typ med `-as` operatorn endast med strängar som är formaterade enligt reglerna för den aktuella kulturen.</span><span class="sxs-lookup"><span data-stu-id="9de06-152">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

<span data-ttu-id="9de06-153">Använd cmdleten för att hitta .NET-typen för ett objekt `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="9de06-153">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="9de06-154">Du kan också använda **gettype** -metoden för alla objekt tillsammans med egenskapen **FullName** för den här metoden.</span><span class="sxs-lookup"><span data-stu-id="9de06-154">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="9de06-155">Följande uttryck hämtar t. ex. typen av retur värde för ett `Get-Culture` kommando:</span><span class="sxs-lookup"><span data-stu-id="9de06-155">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="9de06-156">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9de06-156">EXAMPLES</span></span>

<span data-ttu-id="9de06-157">I följande exempel visas några användnings områden av typen operatorer:</span><span class="sxs-lookup"><span data-stu-id="9de06-157">The following examples show some uses of the Type operators:</span></span>

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

<span data-ttu-id="9de06-158">I följande exempel visas att när indatatypen är en samling objekt, är den matchande typen .NET-typen för samlingen, inte typen för de enskilda objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="9de06-158">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="9de06-159">I det här exemplet, även om `Get-Culture` både `Get-UICulture` cmdletarna och returnerar **system. globalisering. CultureInfo** -objekt, är en samling av dessa objekt en system. Object-matris.</span><span class="sxs-lookup"><span data-stu-id="9de06-159">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

<span data-ttu-id="9de06-160">I följande exempel visas hur du använder `-as` operatorn.</span><span class="sxs-lookup"><span data-stu-id="9de06-160">The following examples show how to use the `-as` operator.</span></span>

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

<span data-ttu-id="9de06-161">Följande exempel visar att när `-as` operatorn inte kan konvertera inobjektet till .net-typen returneras `$null` .</span><span class="sxs-lookup"><span data-stu-id="9de06-161">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="9de06-162">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="9de06-162">SEE ALSO</span></span>

[<span data-ttu-id="9de06-163">about_Operators</span><span class="sxs-lookup"><span data-stu-id="9de06-163">about_Operators</span></span>](about_Operators.md)
