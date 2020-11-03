---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 4b1d1fc9961f453c43981c7c81c7de5f059a790e
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/25/2020
ms.locfileid: "93269595"
---
# <span data-ttu-id="39f64-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="39f64-103">Select-Object</span></span>

## <span data-ttu-id="39f64-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="39f64-104">SYNOPSIS</span></span>
<span data-ttu-id="39f64-105">Markerar objekt eller objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="39f64-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="39f64-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="39f64-106">SYNTAX</span></span>

### <span data-ttu-id="39f64-107">DefaultParameter (standard)</span><span class="sxs-lookup"><span data-stu-id="39f64-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="39f64-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="39f64-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="39f64-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="39f64-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="39f64-110">SkipIndexParameter</span><span class="sxs-lookup"><span data-stu-id="39f64-110">SkipIndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-SkipIndex <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="39f64-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="39f64-111">DESCRIPTION</span></span>

<span data-ttu-id="39f64-112">`Select-Object`Cmdleten väljer angivna egenskaper för ett objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-112">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="39f64-113">Det kan också välja unika objekt, ett angivet antal objekt eller objekt på en angiven position i en matris.</span><span class="sxs-lookup"><span data-stu-id="39f64-113">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="39f64-114">Om du vill välja objekt från en samling använder du parametrarna **First** , **Last** , **Unique** , **Skip** och **index** .</span><span class="sxs-lookup"><span data-stu-id="39f64-114">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="39f64-115">Om du vill välja objekt egenskaper använder du **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="39f64-115">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="39f64-116">När du väljer Egenskaper `Select-Object` returnerar nya objekt som bara har de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="39f64-116">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="39f64-117">Från och med Windows PowerShell 3,0 `Select-Object` innehåller en optimerings funktion som förhindrar att kommandon skapar och bearbetar objekt som inte används.</span><span class="sxs-lookup"><span data-stu-id="39f64-117">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="39f64-118">När du inkluderar ett `Select-Object` kommando med de **första** parametrarna eller **index** parametrarna i en kommando pipeline, stoppar PowerShell kommandot som genererar objekten så snart det valda antalet objekt genereras, även när kommandot som genererar objekten visas före `Select-Object` kommandot i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="39f64-118">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="39f64-119">Om du vill inaktivera optimerings beteendet använder du parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="39f64-119">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="39f64-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="39f64-120">EXAMPLES</span></span>

### <span data-ttu-id="39f64-121">Exempel 1: Välj objekt efter egenskap</span><span class="sxs-lookup"><span data-stu-id="39f64-121">Example 1: Select objects by property</span></span>

<span data-ttu-id="39f64-122">I det här exemplet skapas objekt som har egenskaper för **namn** , **ID** och arbets minne ( **WS** ) för process objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-122">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="39f64-123">Exempel 2: Välj objekt efter egenskap och formatera resultaten</span><span class="sxs-lookup"><span data-stu-id="39f64-123">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="39f64-124">I det här exemplet får du information om de moduler som används av processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="39f64-124">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="39f64-125">Den använder `Get-Process` cmdleten för att hämta processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="39f64-125">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="39f64-126">Den använder `Select-Object` cmdleten för att mata ut en matris med `[System.Diagnostics.ProcessModule]` instanser som finns i egenskapen **modules** för varje `System.Diagnostics.Process` instans som matas ut av `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="39f64-126">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="39f64-127">**Egenskaps** parametern för `Select-Object` cmdleten väljer process namnen.</span><span class="sxs-lookup"><span data-stu-id="39f64-127">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="39f64-128">Detta lägger till en `ProcessName` **NoteProperty** till varje `[System.Diagnostics.ProcessModule]` instans och fyller den med värdet för den aktuella processens **processname** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="39f64-128">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="39f64-129">Slutligen `Format-List` används cmdleten för att visa namn och moduler för varje process i en lista.</span><span class="sxs-lookup"><span data-stu-id="39f64-129">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

```powershell
Get-Process Explorer | Select-Object -Property ProcessName -ExpandProperty Modules | Format-List
```

```Output
ProcessName       : explorer
ModuleName        : explorer.exe
FileName          : C:\WINDOWS\explorer.exe
BaseAddress       : 140697278152704
ModuleMemorySize  : 3919872
EntryPointAddress : 140697278841168
FileVersionInfo   : File:             C:\WINDOWS\explorer.exe
                    InternalName:     explorer
                    OriginalFilename: EXPLORER.EXE.MUI
                    FileVersion:      10.0.17134.1 (WinBuild.160101.0800)
                    FileDescription:  Windows Explorer
                    Product:          Microsoft Windows Operating System
                    ProductVersion:   10.0.17134.1
...
```

### <span data-ttu-id="39f64-130">Exempel 3: Välj processer som använder mest minne</span><span class="sxs-lookup"><span data-stu-id="39f64-130">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="39f64-131">Det här exemplet hämtar de fem processerna som använder mest minne.</span><span class="sxs-lookup"><span data-stu-id="39f64-131">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="39f64-132">`Get-Process`Cmdleten hämtar processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="39f64-132">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="39f64-133">`Sort-Object`Cmdleten sorterar processerna efter minnes användning (arbets minne) och- `Select-Object` cmdleten väljer bara de sista fem medlemmarna i den resulterande matrisen med objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-133">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="39f64-134">Parametern **wait** krävs inte i kommandon som innehåller `Sort-Object` cmdleten eftersom `Sort-Object` bearbetar alla objekt och returnerar sedan en samling.</span><span class="sxs-lookup"><span data-stu-id="39f64-134">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="39f64-135">`Select-Object`Optimeringen är endast tillgänglig för kommandon som returnerar objekt individuellt när de bearbetas.</span><span class="sxs-lookup"><span data-stu-id="39f64-135">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

```powershell
Get-Process | Sort-Object -Property WS | Select-Object -Last 5
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VS(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
2866     320       33432      45764   203   222.41   1292 svchost
577      17        23676      50516   265    50.58   4388 WINWORD
826      11        75448      76712   188    19.77   3780 Ps
1367     14        73152      88736   216    61.69    676 Ps
1612     44        66080      92780   380   900.59   6132 INFOPATH
```

### <span data-ttu-id="39f64-136">Exempel 4: Välj unika tecken från en matris</span><span class="sxs-lookup"><span data-stu-id="39f64-136">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="39f64-137">I det här exemplet används den **unika** parametern för `Select-Object` för att hämta unika tecken från en matris med tecken.</span><span class="sxs-lookup"><span data-stu-id="39f64-137">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="39f64-138">Exempel 5: Välj nyaste och äldsta händelser i händelse loggen</span><span class="sxs-lookup"><span data-stu-id="39f64-138">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="39f64-139">Det här exemplet hämtar de första (nyaste) och senaste (äldsta) händelserna i Windows PowerShell-händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="39f64-139">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="39f64-140">`Get-EventLog` hämtar alla händelser i Windows PowerShell-loggen och sparar dem i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39f64-140">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="39f64-141">Sedan `$a` är skickas till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39f64-141">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="39f64-142">`Select-Object`Kommandot använder parametern **index** för att välja händelser från händelsens matris i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="39f64-142">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="39f64-143">Indexet för den första händelsen är 0.</span><span class="sxs-lookup"><span data-stu-id="39f64-143">The index of the first event is 0.</span></span> <span data-ttu-id="39f64-144">Indexet för den sista händelsen är antalet objekt i `$a` minus 1.</span><span class="sxs-lookup"><span data-stu-id="39f64-144">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="39f64-145">Exempel 6: Markera alla utom det första objektet</span><span class="sxs-lookup"><span data-stu-id="39f64-145">Example 6: Select all but the first object</span></span>

<span data-ttu-id="39f64-146">I det här exemplet skapas en ny PSSession på var och en av de datorer som anges i Servers.txt-filer, förutom den första.</span><span class="sxs-lookup"><span data-stu-id="39f64-146">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="39f64-147">`Select-Object` markerar alla utom den första datorn i en lista över dator namn.</span><span class="sxs-lookup"><span data-stu-id="39f64-147">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="39f64-148">Den resulterande listan med datorer anges som värde för parametern **computername** för `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="39f64-148">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="39f64-149">Exempel 7: Byt namn på filer och välj flera för att granska</span><span class="sxs-lookup"><span data-stu-id="39f64-149">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="39f64-150">I det här exemplet läggs ett "-ro"-suffix till i grundnamnen på textfiler som har det skrivskyddade attributet och sedan visas de första fem filerna så att användaren kan se ett exempel på resultatet.</span><span class="sxs-lookup"><span data-stu-id="39f64-150">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="39f64-151">`Get-ChildItem` använder den **skrivskyddade** dynamiska parametern för att hämta skrivskyddade filer.</span><span class="sxs-lookup"><span data-stu-id="39f64-151">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="39f64-152">De resulterande filerna är skickas till `Rename-Item` cmdleten, som byter namn på filen.</span><span class="sxs-lookup"><span data-stu-id="39f64-152">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="39f64-153">Den använder parametern **Passthru** för `Rename-Item` för att skicka de omdöpta filerna till `Select-Object` cmdleten, som väljer de första 5 för visning.</span><span class="sxs-lookup"><span data-stu-id="39f64-153">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="39f64-154">Parametern **wait** i `Select-Object` förhindrar att PowerShell stoppar `Get-ChildItem` cmdleten när den får de första fem skrivskyddade textfilerna.</span><span class="sxs-lookup"><span data-stu-id="39f64-154">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="39f64-155">Utan den här parametern får bara de fem första skrivskyddade filerna namnet.</span><span class="sxs-lookup"><span data-stu-id="39f64-155">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="39f64-156">Exempel 8: demonstrera erna för parametern-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="39f64-156">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="39f64-157">Det här exemplet demonstrerar erna för parametern **ExpandProperty** .</span><span class="sxs-lookup"><span data-stu-id="39f64-157">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="39f64-158">Observera att de utdata som genereras var en matris med `[System.Int32]` instanser.</span><span class="sxs-lookup"><span data-stu-id="39f64-158">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="39f64-159">Instanserna följer standardformateringsregler i **vyn utdata**.</span><span class="sxs-lookup"><span data-stu-id="39f64-159">The instances conform to standard formatting rules of the **Output View**.</span></span> <span data-ttu-id="39f64-160">Detta gäller för alla *utökade* egenskaper.</span><span class="sxs-lookup"><span data-stu-id="39f64-160">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="39f64-161">Om det finns ett standardformat för objekten i listan kanske den utökade egenskapen inte visas.</span><span class="sxs-lookup"><span data-stu-id="39f64-161">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

```powershell
# Create a custom object to use for the Select-Object example.
$object = [pscustomobject]@{Name="CustomObject";Expand=@(1,2,3,4,5)}
# Use the ExpandProperty parameter to Expand the property.
$object | Select-Object -ExpandProperty Expand -Property Name
```

```Output
1
2
3
4
5
```

```powershell
# The output did not contain the Name property, but it was added successfully.
# Use Get-Member to confirm the Name property was added and populated.
$object | Select-Object -ExpandProperty Expand -Property Name | Get-Member
```

```Output
   TypeName: System.Int32

Name        MemberType   Definition
----        ----------   ----------
CompareTo   Method       int CompareTo(System.Object value), int CompareTo(int value), int IComparable.CompareTo(System.Object obj)...
Equals      Method       bool Equals(System.Object obj), bool Equals(int obj), bool IEquatable[int].Equals(int other)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
GetTypeCode Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean   Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte      Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar      Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime  Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal   Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble    Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16     Method       int16 IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32     Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64     Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte     Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle    Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString    Method       string ToString(), string ToString(string format), string ToString(System.IFormatProvider provider)...
ToType      Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16    Method       uint16 IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32    Method       uint32 IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64    Method       uint64 IConvertible.ToUInt64(System.IFormatProvider provider)
Name        NoteProperty string Name=CustomObject
```

### <span data-ttu-id="39f64-162">Exempel 9: skapa anpassade egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="39f64-162">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="39f64-163">I följande exempel visas hur `Select-Object` du lägger till en anpassad egenskap i alla objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-163">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="39f64-164">När du anger ett egenskaps namn som inte finns `Select-Object` skapar den egenskapen som en **NoteProperty** för varje objekt som skickas.</span><span class="sxs-lookup"><span data-stu-id="39f64-164">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

```powershell
$customObject = 1 | Select-Object -Property MyCustomProperty
$customObject.MyCustomProperty = "New Custom Property"
$customObject
```

```Output
MyCustomProperty
----------------
New Custom Property
```

### <span data-ttu-id="39f64-165">Exempel 10: skapa beräknade egenskaper för varje InputObject</span><span class="sxs-lookup"><span data-stu-id="39f64-165">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="39f64-166">I det här exemplet visas hur `Select-Object` du lägger till beräknade egenskaper i dina inaktuella inaktuella.</span><span class="sxs-lookup"><span data-stu-id="39f64-166">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="39f64-167">Genom att skicka en **script block** till **egenskaps** parametern kan du `Select-Object` utvärdera uttrycket för varje objekt som skickas och lägga till resultaten i utdata.</span><span class="sxs-lookup"><span data-stu-id="39f64-167">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="39f64-168">I **script block** kan du använda `$_` variabeln för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="39f64-168">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="39f64-169">Som standard `Select-Object` använder **script block** -strängen som namn på egenskapen.</span><span class="sxs-lookup"><span data-stu-id="39f64-169">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="39f64-170">Med hjälp av en **hash-hash** kan du märka utdata från din **script block** som en anpassad egenskap som har lagts till i varje objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-170">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="39f64-171">Du kan lägga till flera beräknade egenskaper för varje objekt som skickas till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="39f64-171">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

```powershell
# Create a calculated property called $_.StartTime.DayOfWeek
Get-Process | Select-Object -Property ProcessName,{$_.StartTime.DayOfWeek}
```

```Output
ProcessName  $_.StartTime.DayOfWeek
----         ----------------------
alg                       Wednesday
ati2evxx                  Wednesday
ati2evxx                   Thursday
...
```

```powershell
# Add a custom property to calculate the size in KiloBytes of each FileInfo object you pass in.
# Use the pipeline variable to divide each file's length by 1 KiloBytes
$size = @{label="Size(KB)";expression={$_.length/1KB}}
# Create an additional calculated property with the number of Days since the file was last accessed.
# You can also shorten the key names to be 'l', and 'e', or use Name instead of Label.
$days = @{l="Days";e={((Get-Date) - $_.LastAccessTime).Days}}
# You can also shorten the name of your label key to 'l' and your expression key to 'e'.
Get-ChildItem $PSHOME -File | Select-Object Name, $size, $days
```

```Output
Name                        Size(KB)        Days
----                        --------        ----
Certificate.format.ps1xml   12.5244140625   223
Diagnostics.Format.ps1xml   4.955078125     223
DotNetTypes.format.ps1xml   134.9833984375  223
```

## <span data-ttu-id="39f64-172">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="39f64-172">PARAMETERS</span></span>

### <span data-ttu-id="39f64-173">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="39f64-173">-ExcludeProperty</span></span>

<span data-ttu-id="39f64-174">Anger egenskaperna som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="39f64-174">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="39f64-175">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="39f64-175">Wildcards are permitted.</span></span>

<span data-ttu-id="39f64-176">Från och med PowerShell 6 behöver du inte längre inkludera **egenskaps** parametern för att **ExcludeProperty** ska fungera.</span><span class="sxs-lookup"><span data-stu-id="39f64-176">Beginning in PowerShell 6, it is no longer required to include the **Property** parameter for **ExcludeProperty** to work.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="39f64-177">– ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="39f64-177">-ExpandProperty</span></span>

<span data-ttu-id="39f64-178">Anger en egenskap som ska väljas och indikerar att ett försök ska göras för att expandera den egenskapen.</span><span class="sxs-lookup"><span data-stu-id="39f64-178">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="39f64-179">Om den angivna egenskapen är en matris ingår varje mat ris värde i utdata.</span><span class="sxs-lookup"><span data-stu-id="39f64-179">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="39f64-180">Om den angivna egenskapen är ett objekt expanderas objekt egenskaperna för varje **InputObject**</span><span class="sxs-lookup"><span data-stu-id="39f64-180">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="39f64-181">I båda fallen matchar **typen** av objekt utdata den **typ** av utökad egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="39f64-181">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="39f64-182">Om **egenskaps** parametern har angetts `Select-Object` försöker att lägga till varje vald egenskap som **NoteProperty** till varje utgivna objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-182">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="39f64-183">Om du får felet: SELECT: egenskapen kan inte bearbetas eftersom egenskapen `<PropertyName>` redan finns, Tänk på följande.</span><span class="sxs-lookup"><span data-stu-id="39f64-183">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="39f64-184">Observera att när `-ExpandProperty` du använder, `Select-Object` inte kan ersätta en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="39f64-184">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="39f64-185">Det innebär att du måste:</span><span class="sxs-lookup"><span data-stu-id="39f64-185">This means:</span></span>
>
> - <span data-ttu-id="39f64-186">Om det utökade objektet har en egenskap med samma namn, uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="39f64-186">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="39f64-187">Om det *valda* objektet har en egenskap med samma namn som en *utökad* objekt egenskap uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="39f64-187">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

```yaml
Type: System.String
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-188">– Första</span><span class="sxs-lookup"><span data-stu-id="39f64-188">-First</span></span>

<span data-ttu-id="39f64-189">Anger antalet objekt som ska väljas från början av en matris med inobjekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-189">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-190">-Index</span><span class="sxs-lookup"><span data-stu-id="39f64-190">-Index</span></span>

<span data-ttu-id="39f64-191">Väljer objekt från en matris baserat på deras index värden.</span><span class="sxs-lookup"><span data-stu-id="39f64-191">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="39f64-192">Ange indexen i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="39f64-192">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="39f64-193">Index i en matris börjar med 0, där 0 representerar det första värdet och (n-1) representerar det sista värdet.</span><span class="sxs-lookup"><span data-stu-id="39f64-193">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-194">– InputObject</span><span class="sxs-lookup"><span data-stu-id="39f64-194">-InputObject</span></span>

<span data-ttu-id="39f64-195">Anger objekt som ska skickas till cmdleten via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="39f64-195">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="39f64-196">Med den här parametern kan du skicka pipe-objekt till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="39f64-196">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="39f64-197">När du skickar objekt till parametern **InputObject** , i stället för att använda pipelinen, `Select-Object` behandlar **InputObject** som ett enskilt objekt, även om värdet är en samling.</span><span class="sxs-lookup"><span data-stu-id="39f64-197">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="39f64-198">Vi rekommenderar att du använder pipelinen när du skickar samlingar till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="39f64-198">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-199">-Senaste</span><span class="sxs-lookup"><span data-stu-id="39f64-199">-Last</span></span>

<span data-ttu-id="39f64-200">Anger antalet objekt som ska väljas från slutet av en matris med inobjekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-200">Specifies the number of objects to select from the end of an array of input objects.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-201">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="39f64-201">-Property</span></span>

<span data-ttu-id="39f64-202">Anger de egenskaper som ska väljas.</span><span class="sxs-lookup"><span data-stu-id="39f64-202">Specifies the properties to select.</span></span> <span data-ttu-id="39f64-203">De här egenskaperna läggs till som **NoteProperty** -medlemmar i objekten.</span><span class="sxs-lookup"><span data-stu-id="39f64-203">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="39f64-204">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="39f64-204">Wildcards are permitted.</span></span>

<span data-ttu-id="39f64-205">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="39f64-205">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="39f64-206">Om du vill skapa en beräknad egenskap använder du en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="39f64-206">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="39f64-207">Giltiga nycklar är:</span><span class="sxs-lookup"><span data-stu-id="39f64-207">Valid keys are:</span></span>

- <span data-ttu-id="39f64-208">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="39f64-208">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="39f64-209">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="39f64-209">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="39f64-210">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="39f64-210">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: DefaultParameter, SkipLastParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="39f64-211">-Hoppa över</span><span class="sxs-lookup"><span data-stu-id="39f64-211">-Skip</span></span>

<span data-ttu-id="39f64-212">Hoppar över (väljer inte) det angivna antalet objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-212">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="39f64-213">Som standard räknas **Skip** -parametern från början av matrisen eller listan över objekt, men om kommandot använder den **sista** parametern räknas det från slutet av listan eller matrisen.</span><span class="sxs-lookup"><span data-stu-id="39f64-213">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="39f64-214">Till skillnad från parametern **index** , som börjar räkna vid 0, börjar **Skip** -parametern vid 1.</span><span class="sxs-lookup"><span data-stu-id="39f64-214">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefaultParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-215">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="39f64-215">-SkipLast</span></span>

<span data-ttu-id="39f64-216">Hoppar över (väljer inte) det angivna antalet objekt från slutet av listan eller matrisen.</span><span class="sxs-lookup"><span data-stu-id="39f64-216">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="39f64-217">Fungerar på samma sätt som att använda **Skip** tillsammans med den **sista** parametern.</span><span class="sxs-lookup"><span data-stu-id="39f64-217">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="39f64-218">Till skillnad från parametern **index** , som börjar räkna med 0, börjar **SkipLast** -parametern på 1.</span><span class="sxs-lookup"><span data-stu-id="39f64-218">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SkipLastParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-219">– Unik</span><span class="sxs-lookup"><span data-stu-id="39f64-219">-Unique</span></span>

<span data-ttu-id="39f64-220">Anger att om en delmängd av inobjekten har identiska egenskaper och värden, väljs bara en enskild medlem i del mängden.</span><span class="sxs-lookup"><span data-stu-id="39f64-220">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="39f64-221">Den här parametern är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="39f64-221">This parameter is case-sensitive.</span></span> <span data-ttu-id="39f64-222">Det innebär att strängar som bara skiljer sig i gemener och versaler anses vara unika.</span><span class="sxs-lookup"><span data-stu-id="39f64-222">As a result, strings that differ only in character casing are considered to be unique.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-223">– Vänta</span><span class="sxs-lookup"><span data-stu-id="39f64-223">-Wait</span></span>

<span data-ttu-id="39f64-224">Anger att-cmdleten inaktiverar optimering.</span><span class="sxs-lookup"><span data-stu-id="39f64-224">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="39f64-225">PowerShell kör kommandon i den ordning som de visas i kommandot pipeliner och låter dem generera alla objekt.</span><span class="sxs-lookup"><span data-stu-id="39f64-225">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="39f64-226">Om du inkluderar ett `Select-Object` kommando med de **första** eller **index** parametrarna i en kommando pipeline, stoppar PowerShell som standard kommandot som genererar objekten så fort det valda antalet objekt genereras.</span><span class="sxs-lookup"><span data-stu-id="39f64-226">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="39f64-227">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="39f64-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultParameter, IndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-228">-SkipIndex</span><span class="sxs-lookup"><span data-stu-id="39f64-228">-SkipIndex</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SkipIndexParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="39f64-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="39f64-229">CommonParameters</span></span>

<span data-ttu-id="39f64-230">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="39f64-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="39f64-231">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="39f64-231">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="39f64-232">INDATA</span><span class="sxs-lookup"><span data-stu-id="39f64-232">INPUTS</span></span>

### <span data-ttu-id="39f64-233">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="39f64-233">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="39f64-234">Du kan skicka vidare alla objekt till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="39f64-234">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="39f64-235">UTDATA</span><span class="sxs-lookup"><span data-stu-id="39f64-235">OUTPUTS</span></span>

### <span data-ttu-id="39f64-236">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="39f64-236">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="39f64-237">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="39f64-237">NOTES</span></span>

- <span data-ttu-id="39f64-238">Du kan också referera till `Select-Object` cmdleten med dess inbyggda alias `select` .</span><span class="sxs-lookup"><span data-stu-id="39f64-238">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="39f64-239">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="39f64-239">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="39f64-240">Optimerings funktionen i `Select-Object` är bara tillgänglig för kommandon som skriver objekt till pipelinen när de bearbetas.</span><span class="sxs-lookup"><span data-stu-id="39f64-240">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="39f64-241">Den har ingen påverkan på kommandon som buffrar bearbetade objekt och skriver dem som en samling.</span><span class="sxs-lookup"><span data-stu-id="39f64-241">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="39f64-242">Att skriva objekt direkt är en bästa praxis för cmdlet-design.</span><span class="sxs-lookup"><span data-stu-id="39f64-242">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="39f64-243">Mer information finns i _skriva enstaka poster till pipelinen i den_ [starkt uppmuntrande utvecklings rikt linjerna](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="39f64-243">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="39f64-244">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="39f64-244">RELATED LINKS</span></span>

[<span data-ttu-id="39f64-245">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="39f64-245">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="39f64-246">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="39f64-246">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="39f64-247">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="39f64-247">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="39f64-248">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="39f64-248">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
