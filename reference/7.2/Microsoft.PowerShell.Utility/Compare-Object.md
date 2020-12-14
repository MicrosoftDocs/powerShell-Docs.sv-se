---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: 6bed0e8d13cb834fab97dc0265ef7d46a2caea97
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710812"
---
# <span data-ttu-id="61246-102">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="61246-102">Compare-Object</span></span>

## <span data-ttu-id="61246-103">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="61246-103">Synopsis</span></span>
<span data-ttu-id="61246-104">Jämför två objekt uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="61246-104">Compares two sets of objects.</span></span>

## <span data-ttu-id="61246-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="61246-105">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="61246-106">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="61246-106">Description</span></span>

<span data-ttu-id="61246-107">`Compare-Object`Cmdleten jämför två uppsättningar objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-107">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="61246-108">En uppsättning objekt är **referensen** och den andra uppsättningen objekt är **skillnaden**.</span><span class="sxs-lookup"><span data-stu-id="61246-108">One set of objects is the **reference**, and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="61246-109">`Compare-Object` söker efter tillgängliga metoder för att jämföra ett helt objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-109">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="61246-110">Om det inte går att hitta en lämplig metod anropar den **toString ()** -metoderna för objekten och jämför sträng resultatet.</span><span class="sxs-lookup"><span data-stu-id="61246-110">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="61246-111">Du kan ange en eller flera egenskaper som ska användas för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="61246-111">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="61246-112">När egenskaper anges jämför cmdleten bara värdena för dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="61246-112">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="61246-113">Resultatet av jämförelsen anger om ett egenskaps värde endast visas i **referens** -objektet ( `<=` ) eller endast i **Differens** -objektet ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="61246-113">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="61246-114">Om parametern **IncludeEqual** används, `==` anger () att värdet finns i båda objekten.</span><span class="sxs-lookup"><span data-stu-id="61246-114">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="61246-115">Om **referensen** eller **Differens** -objekten är null ( `$null` ) `Compare-Object` genererar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="61246-115">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="61246-116">Några exempel använder ihopbuntning för att minska rad längden för kod exemplen.</span><span class="sxs-lookup"><span data-stu-id="61246-116">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="61246-117">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="61246-117">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="61246-118">Exempel</span><span class="sxs-lookup"><span data-stu-id="61246-118">Examples</span></span>

### <span data-ttu-id="61246-119">Exempel 1 – Jämför innehållet i två textfiler</span><span class="sxs-lookup"><span data-stu-id="61246-119">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="61246-120">I det här exemplet jämförs innehållet i två textfiler.</span><span class="sxs-lookup"><span data-stu-id="61246-120">This example compares the contents of two text files.</span></span> <span data-ttu-id="61246-121">Exemplet använder följande två textfiler, med varje värde på en separat rad.</span><span class="sxs-lookup"><span data-stu-id="61246-121">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="61246-122">`Testfile1.txt` innehåller värdena: hund, Squirrel och fågel.</span><span class="sxs-lookup"><span data-stu-id="61246-122">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="61246-123">`Testfile2.txt` innehåller värdena: Cat, fågel och racoon.</span><span class="sxs-lookup"><span data-stu-id="61246-123">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="61246-124">Utdata visar bara de rader som skiljer sig åt mellan filerna.</span><span class="sxs-lookup"><span data-stu-id="61246-124">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="61246-125">`Testfile1.txt` är **referens** objekt ( `<=` ) och `Testfile2.txt` är **Differens** -objektet ( `=>` ).</span><span class="sxs-lookup"><span data-stu-id="61246-125">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="61246-126">Rader med innehåll som visas i båda filerna visas inte.</span><span class="sxs-lookup"><span data-stu-id="61246-126">Lines with content that appear in both files aren't displayed.</span></span>

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### <span data-ttu-id="61246-127">Exempel 2 – jämför varje rad med innehåll och exkluderar skillnaderna</span><span class="sxs-lookup"><span data-stu-id="61246-127">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="61246-128">I det här exemplet används parametern **ExcludeDifferent** för att jämföra varje innehålls rad i två textfiler.</span><span class="sxs-lookup"><span data-stu-id="61246-128">This example uses the **ExcludeDifferent** parameter to compare each line of content in two text files.</span></span>

<span data-ttu-id="61246-129">Från och med PowerShell 7,1, när du använder parametern **ExcludeDifferent** , härleds **IncludeEqual** och utdata bara innehåller rader i båda filerna, som visas i **SideIndicator** ( `==` ).</span><span class="sxs-lookup"><span data-stu-id="61246-129">As of PowerShell 7.1, when using the **ExcludeDifferent** parameter, **IncludeEqual** is inferred and the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="61246-130">Exempel 3 – Visa skillnaden när du använder parametern PassThru</span><span class="sxs-lookup"><span data-stu-id="61246-130">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="61246-131">Normalt `Compare-Object` returnerar en **PSCustomObject** -typ med följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="61246-131">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="61246-132">**InputObject** som jämförs</span><span class="sxs-lookup"><span data-stu-id="61246-132">The **InputObject** being compared</span></span>
- <span data-ttu-id="61246-133">Egenskapen **SideIndicator** visar vilket indata-objekt som utdata tillhör</span><span class="sxs-lookup"><span data-stu-id="61246-133">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="61246-134">När du använder parametern **Passthru** ändras inte objekt **typen** , men instansen för det returnerade objektet har en tillagd **NoteProperty** som heter **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="61246-134">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="61246-135">**SideIndicator** visar vilket indata-objekt som utdata tillhör.</span><span class="sxs-lookup"><span data-stu-id="61246-135">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="61246-136">I följande exempel visas olika typer av utdata.</span><span class="sxs-lookup"><span data-stu-id="61246-136">The following examples shows the different output types.</span></span>

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

<span data-ttu-id="61246-137">När du använder **Passthru** returneras den ursprungliga objekt typen (**system. Boolean**).</span><span class="sxs-lookup"><span data-stu-id="61246-137">When using **PassThru**, the original object type (**System.Boolean**) is returned.</span></span> <span data-ttu-id="61246-138">Observera hur utdata som visas i standardformatet för **system. Boolean** -objekt visar inte egenskapen **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="61246-138">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="61246-139">Men det returnerade **system. Boolean** -objektet har den tillagda **NoteProperty**.</span><span class="sxs-lookup"><span data-stu-id="61246-139">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="61246-140">Exempel 4 – jämför två enkla objekt med hjälp av egenskaper</span><span class="sxs-lookup"><span data-stu-id="61246-140">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="61246-141">I det här exemplet jämför vi två olika strängar som har samma längd.</span><span class="sxs-lookup"><span data-stu-id="61246-141">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="61246-142">Exempel 5 – jämföra komplexa objekt med egenskaper</span><span class="sxs-lookup"><span data-stu-id="61246-142">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="61246-143">Det här exemplet visar beteendet vid jämförelse av komplexa objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-143">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="61246-144">I det här exemplet lagrar vi två olika process objekt för olika instanser av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61246-144">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="61246-145">Båda variablerna innehåller process objekt med samma namn.</span><span class="sxs-lookup"><span data-stu-id="61246-145">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="61246-146">När objekten jämförs utan att ange **egenskaps** parametern, betraktar cmdleten objekten som ska vara lika.</span><span class="sxs-lookup"><span data-stu-id="61246-146">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="61246-147">Observera att värdet för **InputObject** är detsamma som resultatet av metoden **toString ()** .</span><span class="sxs-lookup"><span data-stu-id="61246-147">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="61246-148">Eftersom klassen **system. Diagnostics. process** inte har gränssnittet **IComparable** , konverterar cmdleten objekten till strängarna och jämför sedan resultaten.</span><span class="sxs-lookup"><span data-stu-id="61246-148">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

<span data-ttu-id="61246-149">När du anger vilka egenskaper som ska jämföras, visar cmdleten skillnaderna.</span><span class="sxs-lookup"><span data-stu-id="61246-149">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="61246-150">Exempel 6 – jämföra komplexa objekt som implementerar IComparable</span><span class="sxs-lookup"><span data-stu-id="61246-150">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="61246-151">Om objektet implementerar **IComparable** söker cmdleten efter sätt att jämföra objekten. Om objekten är olika typer, konverteras **Differens** -objektet till **ReferenceObject** typ och jämförs sedan.</span><span class="sxs-lookup"><span data-stu-id="61246-151">If the object implements **IComparable**, the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="61246-152">I det här exemplet jämför vi en sträng med ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-152">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="61246-153">I det första fallet konverteras strängen till ett **TimeSpan** så att objekten är lika.</span><span class="sxs-lookup"><span data-stu-id="61246-153">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

<span data-ttu-id="61246-154">I det andra fallet konverteras **TimeSpan** till en sträng så att objektet skiljer sig åt.</span><span class="sxs-lookup"><span data-stu-id="61246-154">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="61246-155">Parameters (Parametrar)</span><span class="sxs-lookup"><span data-stu-id="61246-155">Parameters</span></span>

### <span data-ttu-id="61246-156">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="61246-156">-CaseSensitive</span></span>

<span data-ttu-id="61246-157">Anger att jämförelser ska vara Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="61246-157">Indicates that comparisons should be case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-158">– Kultur</span><span class="sxs-lookup"><span data-stu-id="61246-158">-Culture</span></span>

<span data-ttu-id="61246-159">Anger kulturen som ska användas för jämförelser.</span><span class="sxs-lookup"><span data-stu-id="61246-159">Specifies the culture to use for comparisons.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-160">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="61246-160">-DifferenceObject</span></span>

<span data-ttu-id="61246-161">Anger de objekt som jämförs med **referens** objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-161">Specifies the objects that are compared to the **reference** objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="61246-162">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="61246-162">-ExcludeDifferent</span></span>

<span data-ttu-id="61246-163">Anger att denna cmdlet endast visar egenskaperna för jämförda objekt som är lika.</span><span class="sxs-lookup"><span data-stu-id="61246-163">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="61246-164">Skillnaderna mellan objekten ignoreras.</span><span class="sxs-lookup"><span data-stu-id="61246-164">The differences between the objects are discarded.</span></span>

<span data-ttu-id="61246-165">Använd **ExcludeDifferent** med **IncludeEqual** för att visa endast de rader som matchar mellan **referens** -och **skillnads** objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-165">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="61246-166">Om **ExcludeDifferent** anges utan **IncludeEqual**, finns det inga utdata.</span><span class="sxs-lookup"><span data-stu-id="61246-166">If **ExcludeDifferent** is specified without **IncludeEqual**, there's no output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-167">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="61246-167">-IncludeEqual</span></span>

<span data-ttu-id="61246-168">**IncludeEqual** visar matchningarna mellan **referens** -och **skillnads** objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-168">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="61246-169">Som standard innehåller utdata även skillnaderna mellan **referens** -och **skillnads** objekt.</span><span class="sxs-lookup"><span data-stu-id="61246-169">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-170">– PassThru</span><span class="sxs-lookup"><span data-stu-id="61246-170">-PassThru</span></span>

<span data-ttu-id="61246-171">När du använder parametern **Passthru** `Compare-Object` utelämnar **PSCustomObject** -omslutningen runt de jämförda objekten och returnerar olika objekt, oförändrade.</span><span class="sxs-lookup"><span data-stu-id="61246-171">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-172">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="61246-172">-Property</span></span>

<span data-ttu-id="61246-173">Anger en matris med egenskaper för **referens** -och **skillnads** objekt som ska jämföras.</span><span class="sxs-lookup"><span data-stu-id="61246-173">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="61246-174">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="61246-174">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="61246-175">Den beräknade egenskapen kan vara ett skript block eller en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="61246-175">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="61246-176">Giltiga nyckel/värde-par är:</span><span class="sxs-lookup"><span data-stu-id="61246-176">Valid key-value pairs are:</span></span>

- <span data-ttu-id="61246-177">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="61246-177">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="61246-178">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="61246-178">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-179">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="61246-179">-ReferenceObject</span></span>

<span data-ttu-id="61246-180">Anger en matris med objekt som används som referens för jämförelse.</span><span class="sxs-lookup"><span data-stu-id="61246-180">Specifies an array of objects used as a reference for comparison.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-181">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="61246-181">-SyncWindow</span></span>

<span data-ttu-id="61246-182">Anger antalet intilliggande objekt som `Compare-Object` inspecar och söker efter en matchning i en objekt samling.</span><span class="sxs-lookup"><span data-stu-id="61246-182">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="61246-183">`Compare-Object` granskar intilliggande objekt när det inte går att hitta objektet på samma plats i en samling.</span><span class="sxs-lookup"><span data-stu-id="61246-183">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="61246-184">Standardvärdet är `[Int32]::MaxValue` , vilket innebär att `Compare-Object` hela objekt samlingen genomsöks.</span><span class="sxs-lookup"><span data-stu-id="61246-184">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="61246-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="61246-185">CommonParameters</span></span>

<span data-ttu-id="61246-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="61246-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="61246-187">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="61246-187">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="61246-188">Indata</span><span class="sxs-lookup"><span data-stu-id="61246-188">Inputs</span></span>

### <span data-ttu-id="61246-189">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="61246-189">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="61246-190">Du kan skicka ett objekt nedåt i pipelinen till **DifferenceObject** -parametern.</span><span class="sxs-lookup"><span data-stu-id="61246-190">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="61246-191">Outputs (Utdata)</span><span class="sxs-lookup"><span data-stu-id="61246-191">Outputs</span></span>

### <span data-ttu-id="61246-192">Inga</span><span class="sxs-lookup"><span data-stu-id="61246-192">None</span></span>

<span data-ttu-id="61246-193">Om **referens** -och **Differens** -objektet är samma, finns det inga utdata, om du inte använder parametern **IncludeEqual** .</span><span class="sxs-lookup"><span data-stu-id="61246-193">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="61246-194">System. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="61246-194">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="61246-195">Om objekten skiljer `Compare-Object` sig från varandra radbryts de olika objekten i en omslutning `PSCustomObject` med en **SideIndicator** -egenskap som refererar till skillnaderna.</span><span class="sxs-lookup"><span data-stu-id="61246-195">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="61246-196">När du använder parametern **Passthru** ändras inte objekt **typen** , men instansen för det returnerade objektet har en tillagd **NoteProperty** som heter **SideIndicator**.</span><span class="sxs-lookup"><span data-stu-id="61246-196">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="61246-197">**SideIndicator** visar vilket indata-objekt som utdata tillhör.</span><span class="sxs-lookup"><span data-stu-id="61246-197">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="61246-198">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="61246-198">Notes</span></span>

<span data-ttu-id="61246-199">När du använder parametern **Passthru** får inte de utdata som visas i-konsolen innehålla egenskapen **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="61246-199">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="61246-200">Standardvyn av för objekt typen utdata av innehåller `Compare-Object` inte egenskapen **SideIndicator** .</span><span class="sxs-lookup"><span data-stu-id="61246-200">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="61246-201">Mer information finns i [exempel 3](#ex3) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="61246-201">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="61246-202">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="61246-202">Related links</span></span>

[<span data-ttu-id="61246-203">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="61246-203">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="61246-204">-Objekt</span><span class="sxs-lookup"><span data-stu-id="61246-204">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="61246-205">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="61246-205">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="61246-206">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="61246-206">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="61246-207">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="61246-207">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="61246-208">Select-Object</span><span class="sxs-lookup"><span data-stu-id="61246-208">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="61246-209">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="61246-209">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="61246-210">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="61246-210">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="61246-211">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="61246-211">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="61246-212">Hämta process</span><span class="sxs-lookup"><span data-stu-id="61246-212">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
