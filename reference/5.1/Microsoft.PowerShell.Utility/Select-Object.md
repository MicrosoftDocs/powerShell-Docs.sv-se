---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Object
ms.openlocfilehash: 59cbba88e3c21d740b774d95e7c0e734cd8e3fdc
ms.sourcegitcommit: f9ae48d026d65833b9c8ca881058dda0bbd067b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/25/2020
ms.locfileid: "93269600"
---
# <span data-ttu-id="80732-103">Select-Object</span><span class="sxs-lookup"><span data-stu-id="80732-103">Select-Object</span></span>

## <span data-ttu-id="80732-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="80732-104">SYNOPSIS</span></span>
<span data-ttu-id="80732-105">Markerar objekt eller objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="80732-105">Selects objects or object properties.</span></span>

## <span data-ttu-id="80732-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="80732-106">SYNTAX</span></span>

### <span data-ttu-id="80732-107">DefaultParameter (standard)</span><span class="sxs-lookup"><span data-stu-id="80732-107">DefaultParameter (Default)</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-Last <Int32>] [-First <Int32>] [-Skip <Int32>] [-Wait]
 [<CommonParameters>]
```

### <span data-ttu-id="80732-108">SkipLastParameter</span><span class="sxs-lookup"><span data-stu-id="80732-108">SkipLastParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [[-Property] <Object[]>] [-ExcludeProperty <String[]>]
 [-ExpandProperty <String>] [-Unique] [-SkipLast <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="80732-109">IndexParameter</span><span class="sxs-lookup"><span data-stu-id="80732-109">IndexParameter</span></span>

```
Select-Object [-InputObject <PSObject>] [-Unique] [-Wait] [-Index <Int32[]>] [<CommonParameters>]
```

## <span data-ttu-id="80732-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="80732-110">DESCRIPTION</span></span>

<span data-ttu-id="80732-111">`Select-Object`Cmdleten väljer angivna egenskaper för ett objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-111">The `Select-Object` cmdlet selects specified properties of an object or set of objects.</span></span> <span data-ttu-id="80732-112">Det kan också välja unika objekt, ett angivet antal objekt eller objekt på en angiven position i en matris.</span><span class="sxs-lookup"><span data-stu-id="80732-112">It can also select unique objects, a specified number of objects, or objects in a specified position in an array.</span></span>

<span data-ttu-id="80732-113">Om du vill välja objekt från en samling använder du parametrarna **First** , **Last** , **Unique** , **Skip** och **index** .</span><span class="sxs-lookup"><span data-stu-id="80732-113">To select objects from a collection, use the **First** , **Last** , **Unique** , **Skip** , and **Index** parameters.</span></span> <span data-ttu-id="80732-114">Om du vill välja objekt egenskaper använder du **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="80732-114">To select object properties, use the **Property** parameter.</span></span> <span data-ttu-id="80732-115">När du väljer Egenskaper `Select-Object` returnerar nya objekt som bara har de angivna egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="80732-115">When you select properties, `Select-Object` returns new objects that have only the specified properties.</span></span>

<span data-ttu-id="80732-116">Från och med Windows PowerShell 3,0 `Select-Object` innehåller en optimerings funktion som förhindrar att kommandon skapar och bearbetar objekt som inte används.</span><span class="sxs-lookup"><span data-stu-id="80732-116">Beginning in Windows PowerShell 3.0, `Select-Object` includes an optimization feature that prevents commands from creating and processing objects that are not used.</span></span>

<span data-ttu-id="80732-117">När du inkluderar ett `Select-Object` kommando med de **första** parametrarna eller **index** parametrarna i en kommando pipeline, stoppar PowerShell kommandot som genererar objekten så snart det valda antalet objekt genereras, även när kommandot som genererar objekten visas före `Select-Object` kommandot i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="80732-117">When you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated, even when the command that generates the objects appears before the `Select-Object` command in the pipeline.</span></span> <span data-ttu-id="80732-118">Om du vill inaktivera optimerings beteendet använder du parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="80732-118">To turn off this optimizing behavior, use the **Wait** parameter.</span></span>

## <span data-ttu-id="80732-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="80732-119">EXAMPLES</span></span>

### <span data-ttu-id="80732-120">Exempel 1: Välj objekt efter egenskap</span><span class="sxs-lookup"><span data-stu-id="80732-120">Example 1: Select objects by property</span></span>

<span data-ttu-id="80732-121">I det här exemplet skapas objekt som har egenskaper för **namn** , **ID** och arbets minne ( **WS** ) för process objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-121">This example creates objects that have the **Name** , **ID** , and working set ( **WS** ) properties of process objects.</span></span>

```powershell
Get-Process | Select-Object -Property ProcessName, Id, WS
```

### <span data-ttu-id="80732-122">Exempel 2: Välj objekt efter egenskap och formatera resultaten</span><span class="sxs-lookup"><span data-stu-id="80732-122">Example 2: Select objects by property and format the results</span></span>

<span data-ttu-id="80732-123">I det här exemplet får du information om de moduler som används av processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="80732-123">This example gets information about the modules used by the processes on the computer.</span></span> <span data-ttu-id="80732-124">Den använder `Get-Process` cmdleten för att hämta processen på datorn.</span><span class="sxs-lookup"><span data-stu-id="80732-124">It uses `Get-Process` cmdlet to get the process on the computer.</span></span>

<span data-ttu-id="80732-125">Den använder `Select-Object` cmdleten för att mata ut en matris med `[System.Diagnostics.ProcessModule]` instanser som finns i egenskapen **modules** för varje `System.Diagnostics.Process` instans som matas ut av `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="80732-125">It uses the `Select-Object` cmdlet to output an array of `[System.Diagnostics.ProcessModule]` instances as contained in the **Modules** property of each `System.Diagnostics.Process` instance output by `Get-Process`.</span></span>

<span data-ttu-id="80732-126">**Egenskaps** parametern för `Select-Object` cmdleten väljer process namnen.</span><span class="sxs-lookup"><span data-stu-id="80732-126">The **Property** parameter of the `Select-Object` cmdlet selects the process names.</span></span> <span data-ttu-id="80732-127">Detta lägger till en `ProcessName` **NoteProperty** till varje `[System.Diagnostics.ProcessModule]` instans och fyller den med värdet för den aktuella processens **processname** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="80732-127">This adds a `ProcessName` **NoteProperty** to every `[System.Diagnostics.ProcessModule]` instance and populates it with the value of current process's **ProcessName** property.</span></span>

<span data-ttu-id="80732-128">Slutligen `Format-List` används cmdleten för att visa namn och moduler för varje process i en lista.</span><span class="sxs-lookup"><span data-stu-id="80732-128">Finally, `Format-List` cmdlet is used to display the name and modules of each process in a list.</span></span>

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

### <span data-ttu-id="80732-129">Exempel 3: Välj processer som använder mest minne</span><span class="sxs-lookup"><span data-stu-id="80732-129">Example 3: Select processes using the most memory</span></span>

<span data-ttu-id="80732-130">Det här exemplet hämtar de fem processerna som använder mest minne.</span><span class="sxs-lookup"><span data-stu-id="80732-130">This example gets the five processes that are using the most memory.</span></span> <span data-ttu-id="80732-131">`Get-Process`Cmdleten hämtar processerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="80732-131">The `Get-Process` cmdlet gets the processes on the computer.</span></span> <span data-ttu-id="80732-132">`Sort-Object`Cmdleten sorterar processerna efter minnes användning (arbets minne) och- `Select-Object` cmdleten väljer bara de sista fem medlemmarna i den resulterande matrisen med objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-132">The `Sort-Object` cmdlet sorts the processes according to memory (working set) usage, and the `Select-Object` cmdlet selects only the last five members of the resulting array of objects.</span></span>

<span data-ttu-id="80732-133">Parametern **wait** krävs inte i kommandon som innehåller `Sort-Object` cmdleten eftersom `Sort-Object` bearbetar alla objekt och returnerar sedan en samling.</span><span class="sxs-lookup"><span data-stu-id="80732-133">The **Wait** parameter is not required in commands that include the `Sort-Object` cmdlet because `Sort-Object` processes all objects and then returns a collection.</span></span> <span data-ttu-id="80732-134">`Select-Object`Optimeringen är endast tillgänglig för kommandon som returnerar objekt individuellt när de bearbetas.</span><span class="sxs-lookup"><span data-stu-id="80732-134">The `Select-Object` optimization is available only for commands that return objects individually as they are processed.</span></span>

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

### <span data-ttu-id="80732-135">Exempel 4: Välj unika tecken från en matris</span><span class="sxs-lookup"><span data-stu-id="80732-135">Example 4: Select unique characters from an array</span></span>

<span data-ttu-id="80732-136">I det här exemplet används den **unika** parametern för `Select-Object` för att hämta unika tecken från en matris med tecken.</span><span class="sxs-lookup"><span data-stu-id="80732-136">This example uses the **Unique** parameter of `Select-Object` to get unique characters from an array of characters.</span></span>

```powershell
"a","b","c","a","a","a" | Select-Object -Unique
```

```Output
a
b
c
```

### <span data-ttu-id="80732-137">Exempel 5: Välj nyaste och äldsta händelser i händelse loggen</span><span class="sxs-lookup"><span data-stu-id="80732-137">Example 5: Select newest and oldest events in the event log</span></span>

<span data-ttu-id="80732-138">Det här exemplet hämtar de första (nyaste) och senaste (äldsta) händelserna i Windows PowerShell-händelseloggen.</span><span class="sxs-lookup"><span data-stu-id="80732-138">This example gets the first (newest) and last (oldest) events in the Windows PowerShell event log.</span></span>

<span data-ttu-id="80732-139">`Get-EventLog` hämtar alla händelser i Windows PowerShell-loggen och sparar dem i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="80732-139">`Get-EventLog` gets all events in the Windows PowerShell log and saves them in the `$a` variable.</span></span>
<span data-ttu-id="80732-140">Sedan `$a` är skickas till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80732-140">Then, `$a` is piped to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="80732-141">`Select-Object`Kommandot använder parametern **index** för att välja händelser från händelsens matris i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="80732-141">The `Select-Object` command uses the **Index** parameter to select events from the array of events in the `$a` variable.</span></span> <span data-ttu-id="80732-142">Indexet för den första händelsen är 0.</span><span class="sxs-lookup"><span data-stu-id="80732-142">The index of the first event is 0.</span></span> <span data-ttu-id="80732-143">Indexet för den sista händelsen är antalet objekt i `$a` minus 1.</span><span class="sxs-lookup"><span data-stu-id="80732-143">The index of the last event is the number of items in `$a` minus 1.</span></span>

```powershell
$a = Get-EventLog -LogName "Windows PowerShell"
$a | Select-Object -Index 0, ($A.count - 1)
```

### <span data-ttu-id="80732-144">Exempel 6: Markera alla utom det första objektet</span><span class="sxs-lookup"><span data-stu-id="80732-144">Example 6: Select all but the first object</span></span>

<span data-ttu-id="80732-145">I det här exemplet skapas en ny PSSession på var och en av de datorer som anges i Servers.txt-filer, förutom den första.</span><span class="sxs-lookup"><span data-stu-id="80732-145">This example creates a new PSSession on each of the computers listed in the Servers.txt files, except for the first one.</span></span>

<span data-ttu-id="80732-146">`Select-Object` markerar alla utom den första datorn i en lista över dator namn.</span><span class="sxs-lookup"><span data-stu-id="80732-146">`Select-Object` selects all but the first computer in a list of computer names.</span></span> <span data-ttu-id="80732-147">Den resulterande listan med datorer anges som värde för parametern **computername** för `New-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="80732-147">The resulting list of computers is set as the value of the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

```powershell
New-PSSession -ComputerName (Get-Content Servers.txt | Select-Object -Skip 1)
```

### <span data-ttu-id="80732-148">Exempel 7: Byt namn på filer och välj flera för att granska</span><span class="sxs-lookup"><span data-stu-id="80732-148">Example 7: Rename files and select several to review</span></span>

<span data-ttu-id="80732-149">I det här exemplet läggs ett "-ro"-suffix till i grundnamnen på textfiler som har det skrivskyddade attributet och sedan visas de första fem filerna så att användaren kan se ett exempel på resultatet.</span><span class="sxs-lookup"><span data-stu-id="80732-149">This example adds a "-ro" suffix to the base names of text files that have the read-only attribute and then displays the first five files so the user can see a sample of the effect.</span></span>

<span data-ttu-id="80732-150">`Get-ChildItem` använder den **skrivskyddade** dynamiska parametern för att hämta skrivskyddade filer.</span><span class="sxs-lookup"><span data-stu-id="80732-150">`Get-ChildItem` uses the **ReadOnly** dynamic parameter to get read-only files.</span></span> <span data-ttu-id="80732-151">De resulterande filerna är skickas till `Rename-Item` cmdleten, som byter namn på filen.</span><span class="sxs-lookup"><span data-stu-id="80732-151">The resulting files are piped to the `Rename-Item` cmdlet, which renames the file.</span></span> <span data-ttu-id="80732-152">Den använder parametern **Passthru** för `Rename-Item` för att skicka de omdöpta filerna till `Select-Object` cmdleten, som väljer de första 5 för visning.</span><span class="sxs-lookup"><span data-stu-id="80732-152">It uses the **Passthru** parameter of `Rename-Item` to send the renamed files to the `Select-Object` cmdlet, which selects the first 5 for display.</span></span>

<span data-ttu-id="80732-153">Parametern **wait** i `Select-Object` förhindrar att PowerShell stoppar `Get-ChildItem` cmdleten när den får de första fem skrivskyddade textfilerna.</span><span class="sxs-lookup"><span data-stu-id="80732-153">The **Wait** parameter of `Select-Object` prevents PowerShell from stopping the `Get-ChildItem` cmdlet after it gets the first five read-only text files.</span></span> <span data-ttu-id="80732-154">Utan den här parametern får bara de fem första skrivskyddade filerna namnet.</span><span class="sxs-lookup"><span data-stu-id="80732-154">Without this parameter, only the first five read-only files would be renamed.</span></span>

```powershell
Get-ChildItem *.txt -ReadOnly |
    Rename-Item -NewName {$_.BaseName + "-ro.txt"} -PassThru |
    Select-Object -First 5 -Wait
```

### <span data-ttu-id="80732-155">Exempel 8: demonstrera erna för parametern-ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="80732-155">Example 8: Demonstrate the intricacies of the -ExpandProperty parameter</span></span>

<span data-ttu-id="80732-156">Det här exemplet demonstrerar erna för parametern **ExpandProperty** .</span><span class="sxs-lookup"><span data-stu-id="80732-156">This example demonstrates the intricacies of the **ExpandProperty** parameter.</span></span>

<span data-ttu-id="80732-157">Observera att de utdata som genereras var en matris med `[System.Int32]` instanser.</span><span class="sxs-lookup"><span data-stu-id="80732-157">Note that the output generated was an array of `[System.Int32]` instances.</span></span> <span data-ttu-id="80732-158">Instanserna följer standardformateringsregler i **vyn utdata**.</span><span class="sxs-lookup"><span data-stu-id="80732-158">The instances conform to standard formatting rules of the **Output View**.</span></span> <span data-ttu-id="80732-159">Detta gäller för alla *utökade* egenskaper.</span><span class="sxs-lookup"><span data-stu-id="80732-159">This is true for any *Expanded* properties.</span></span> <span data-ttu-id="80732-160">Om det finns ett standardformat för objekten i listan kanske den utökade egenskapen inte visas.</span><span class="sxs-lookup"><span data-stu-id="80732-160">If the outputted objects have a specific standard format, the expanded property might not be visible.</span></span>

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

### <span data-ttu-id="80732-161">Exempel 9: skapa anpassade egenskaper för objekt</span><span class="sxs-lookup"><span data-stu-id="80732-161">Example 9: Create custom properties on objects</span></span>

<span data-ttu-id="80732-162">I följande exempel visas hur `Select-Object` du lägger till en anpassad egenskap i alla objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-162">The following example demonstrates using `Select-Object` to add a custom property to any object.</span></span>
<span data-ttu-id="80732-163">När du anger ett egenskaps namn som inte finns `Select-Object` skapar den egenskapen som en **NoteProperty** för varje objekt som skickas.</span><span class="sxs-lookup"><span data-stu-id="80732-163">When you specify a property name that does not exist, `Select-Object` creates that property as a **NoteProperty** on each object passed.</span></span>

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

### <span data-ttu-id="80732-164">Exempel 10: skapa beräknade egenskaper för varje InputObject</span><span class="sxs-lookup"><span data-stu-id="80732-164">Example 10: Create calculated properties for each InputObject</span></span>

<span data-ttu-id="80732-165">I det här exemplet visas hur `Select-Object` du lägger till beräknade egenskaper i dina inaktuella inaktuella.</span><span class="sxs-lookup"><span data-stu-id="80732-165">This example demonstrates using `Select-Object` to add calculated properties to your input.</span></span> <span data-ttu-id="80732-166">Genom att skicka en **script block** till **egenskaps** parametern kan du `Select-Object` utvärdera uttrycket för varje objekt som skickas och lägga till resultaten i utdata.</span><span class="sxs-lookup"><span data-stu-id="80732-166">Passing a **ScriptBlock** to the **Property** parameter causes `Select-Object` to evaluate the expression on each object passed and add the results to the output.</span></span> <span data-ttu-id="80732-167">I **script block** kan du använda `$_` variabeln för att referera till det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="80732-167">Within the **ScriptBlock** , you can use the `$_` variable to reference the current object in the pipeline.</span></span>

<span data-ttu-id="80732-168">Som standard `Select-Object` använder **script block** -strängen som namn på egenskapen.</span><span class="sxs-lookup"><span data-stu-id="80732-168">By default, `Select-Object` will use the **ScriptBlock** string as the name of the property.</span></span> <span data-ttu-id="80732-169">Med hjälp av en **hash-hash** kan du märka utdata från din **script block** som en anpassad egenskap som har lagts till i varje objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-169">Using a **Hashtable** , you can label the output of your **ScriptBlock** as a custom property added to each object.</span></span> <span data-ttu-id="80732-170">Du kan lägga till flera beräknade egenskaper för varje objekt som skickas till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="80732-170">You can add multiple calculated properties to each object passed to `Select-Object`.</span></span>

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

## <span data-ttu-id="80732-171">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="80732-171">PARAMETERS</span></span>

### <span data-ttu-id="80732-172">-ExcludeProperty</span><span class="sxs-lookup"><span data-stu-id="80732-172">-ExcludeProperty</span></span>

<span data-ttu-id="80732-173">Anger egenskaperna som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="80732-173">Specifies the properties that this cmdlet excludes from the operation.</span></span> <span data-ttu-id="80732-174">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="80732-174">Wildcards are permitted.</span></span> <span data-ttu-id="80732-175">Den här parametern är endast effektiv när kommandot även innehåller **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="80732-175">This parameter is effective only when the command also includes the **Property** parameter.</span></span>

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

### <span data-ttu-id="80732-176">– ExpandProperty</span><span class="sxs-lookup"><span data-stu-id="80732-176">-ExpandProperty</span></span>

<span data-ttu-id="80732-177">Anger en egenskap som ska väljas och indikerar att ett försök ska göras för att expandera den egenskapen.</span><span class="sxs-lookup"><span data-stu-id="80732-177">Specifies a property to select, and indicates that an attempt should be made to expand that property.</span></span>

- <span data-ttu-id="80732-178">Om den angivna egenskapen är en matris ingår varje mat ris värde i utdata.</span><span class="sxs-lookup"><span data-stu-id="80732-178">If the specified property is an array, each value of the array is included in the output.</span></span>
- <span data-ttu-id="80732-179">Om den angivna egenskapen är ett objekt expanderas objekt egenskaperna för varje **InputObject**</span><span class="sxs-lookup"><span data-stu-id="80732-179">If the specified property is an object, the objects properties are expanded for every **InputObject**</span></span>

<span data-ttu-id="80732-180">I båda fallen matchar **typen** av objekt utdata den **typ** av utökad egenskap som visas.</span><span class="sxs-lookup"><span data-stu-id="80732-180">In either case, the **Type** of objects output will match the **Type** of the expanded property.</span></span>

<span data-ttu-id="80732-181">Om **egenskaps** parametern har angetts `Select-Object` försöker att lägga till varje vald egenskap som **NoteProperty** till varje utgivna objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-181">If the **Property** parameter is specified, `Select-Object` will attempt to add each selected property as a **NoteProperty** to every outputted object.</span></span>

> [!WARNING]
> <span data-ttu-id="80732-182">Om du får felet: SELECT: egenskapen kan inte bearbetas eftersom egenskapen `<PropertyName>` redan finns, Tänk på följande.</span><span class="sxs-lookup"><span data-stu-id="80732-182">If you receive the error: Select : Property cannot be processed because property `<PropertyName>` already exists, consider the following.</span></span>
> <span data-ttu-id="80732-183">Observera att när `-ExpandProperty` du använder, `Select-Object` inte kan ersätta en befintlig egenskap.</span><span class="sxs-lookup"><span data-stu-id="80732-183">Note that when using `-ExpandProperty`, `Select-Object` can not replace an existing property.</span></span>
> <span data-ttu-id="80732-184">Det innebär att du måste:</span><span class="sxs-lookup"><span data-stu-id="80732-184">This means:</span></span>
>
> - <span data-ttu-id="80732-185">Om det utökade objektet har en egenskap med samma namn, uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="80732-185">If the expanded object has a property of the same name, an error will occur.</span></span>
> - <span data-ttu-id="80732-186">Om det *valda* objektet har en egenskap med samma namn som en *utökad* objekt egenskap uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="80732-186">If the *Selected* object has a property of the same name as an *Expanded* objects property, an error will occur.</span></span>

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

### <span data-ttu-id="80732-187">– Första</span><span class="sxs-lookup"><span data-stu-id="80732-187">-First</span></span>

<span data-ttu-id="80732-188">Anger antalet objekt som ska väljas från början av en matris med inobjekt.</span><span class="sxs-lookup"><span data-stu-id="80732-188">Specifies the number of objects to select from the beginning of an array of input objects.</span></span>

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

### <span data-ttu-id="80732-189">-Index</span><span class="sxs-lookup"><span data-stu-id="80732-189">-Index</span></span>

<span data-ttu-id="80732-190">Väljer objekt från en matris baserat på deras index värden.</span><span class="sxs-lookup"><span data-stu-id="80732-190">Selects objects from an array based on their index values.</span></span> <span data-ttu-id="80732-191">Ange indexen i en kommaavgränsad lista.</span><span class="sxs-lookup"><span data-stu-id="80732-191">Enter the indexes in a comma-separated list.</span></span> <span data-ttu-id="80732-192">Index i en matris börjar med 0, där 0 representerar det första värdet och (n-1) representerar det sista värdet.</span><span class="sxs-lookup"><span data-stu-id="80732-192">Indexes in an array begin with 0, where 0 represents the first value and (n-1) represents the last value.</span></span>

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

### <span data-ttu-id="80732-193">– InputObject</span><span class="sxs-lookup"><span data-stu-id="80732-193">-InputObject</span></span>

<span data-ttu-id="80732-194">Anger objekt som ska skickas till cmdleten via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="80732-194">Specifies objects to send to the cmdlet through the pipeline.</span></span> <span data-ttu-id="80732-195">Med den här parametern kan du skicka pipe-objekt till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="80732-195">This parameter enables you to pipe objects to `Select-Object`.</span></span>

<span data-ttu-id="80732-196">När du skickar objekt till parametern **InputObject** , i stället för att använda pipelinen, `Select-Object` behandlar **InputObject** som ett enskilt objekt, även om värdet är en samling.</span><span class="sxs-lookup"><span data-stu-id="80732-196">When you pass objects to the **InputObject** parameter, instead of using the pipeline, `Select-Object` treats the **InputObject** as a single object, even if the value is a collection.</span></span> <span data-ttu-id="80732-197">Vi rekommenderar att du använder pipelinen när du skickar samlingar till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="80732-197">It is recommended that you use the pipeline when passing collections to `Select-Object`.</span></span>

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

### <span data-ttu-id="80732-198">-Senaste</span><span class="sxs-lookup"><span data-stu-id="80732-198">-Last</span></span>

<span data-ttu-id="80732-199">Anger antalet objekt som ska väljas från slutet av en matris med inobjekt.</span><span class="sxs-lookup"><span data-stu-id="80732-199">Specifies the number of objects to select from the end of an array of input objects.</span></span>

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

### <span data-ttu-id="80732-200">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="80732-200">-Property</span></span>

<span data-ttu-id="80732-201">Anger de egenskaper som ska väljas.</span><span class="sxs-lookup"><span data-stu-id="80732-201">Specifies the properties to select.</span></span> <span data-ttu-id="80732-202">De här egenskaperna läggs till som **NoteProperty** -medlemmar i objekten.</span><span class="sxs-lookup"><span data-stu-id="80732-202">These properties are added as **NoteProperty** members to the output objects.</span></span> <span data-ttu-id="80732-203">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="80732-203">Wildcards are permitted.</span></span>

<span data-ttu-id="80732-204">Värdet för **egenskaps** parametern kan vara en ny beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="80732-204">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="80732-205">Om du vill skapa en beräknad egenskap använder du en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="80732-205">To create a calculated, property, use a hash table.</span></span>

<span data-ttu-id="80732-206">Giltiga nycklar är:</span><span class="sxs-lookup"><span data-stu-id="80732-206">Valid keys are:</span></span>

- <span data-ttu-id="80732-207">Namn (eller etikett)- `<string>`</span><span class="sxs-lookup"><span data-stu-id="80732-207">Name (or Label) - `<string>`</span></span>
- <span data-ttu-id="80732-208">Uttryck- `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="80732-208">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="80732-209">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="80732-209">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="80732-210">-Hoppa över</span><span class="sxs-lookup"><span data-stu-id="80732-210">-Skip</span></span>

<span data-ttu-id="80732-211">Hoppar över (väljer inte) det angivna antalet objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-211">Skips (does not select) the specified number of items.</span></span> <span data-ttu-id="80732-212">Som standard räknas **Skip** -parametern från början av matrisen eller listan över objekt, men om kommandot använder den **sista** parametern räknas det från slutet av listan eller matrisen.</span><span class="sxs-lookup"><span data-stu-id="80732-212">By default, the **Skip** parameter counts from the beginning of the array or list of objects, but if the command uses the **Last** parameter, it counts from the end of the list or array.</span></span>

<span data-ttu-id="80732-213">Till skillnad från parametern **index** , som börjar räkna vid 0, börjar **Skip** -parametern vid 1.</span><span class="sxs-lookup"><span data-stu-id="80732-213">Unlike the **Index** parameter, which starts counting at 0, the **Skip** parameter begins at 1.</span></span>

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

### <span data-ttu-id="80732-214">-SkipLast</span><span class="sxs-lookup"><span data-stu-id="80732-214">-SkipLast</span></span>

<span data-ttu-id="80732-215">Hoppar över (väljer inte) det angivna antalet objekt från slutet av listan eller matrisen.</span><span class="sxs-lookup"><span data-stu-id="80732-215">Skips (does not select) the specified number of items from the end of the list or array.</span></span> <span data-ttu-id="80732-216">Fungerar på samma sätt som att använda **Skip** tillsammans med den **sista** parametern.</span><span class="sxs-lookup"><span data-stu-id="80732-216">Works in the same way as using **Skip** together with **Last** parameter.</span></span>

<span data-ttu-id="80732-217">Till skillnad från parametern **index** , som börjar räkna med 0, börjar **SkipLast** -parametern på 1.</span><span class="sxs-lookup"><span data-stu-id="80732-217">Unlike the **Index** parameter, which starts counting at 0, the **SkipLast** parameter begins at 1.</span></span>

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

### <span data-ttu-id="80732-218">– Unik</span><span class="sxs-lookup"><span data-stu-id="80732-218">-Unique</span></span>

<span data-ttu-id="80732-219">Anger att om en delmängd av inobjekten har identiska egenskaper och värden, väljs bara en enskild medlem i del mängden.</span><span class="sxs-lookup"><span data-stu-id="80732-219">Specifies that if a subset of the input objects has identical properties and values, only a single member of the subset will be selected.</span></span>

<span data-ttu-id="80732-220">Den här parametern är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="80732-220">This parameter is case-sensitive.</span></span> <span data-ttu-id="80732-221">Det innebär att strängar som bara skiljer sig i gemener och versaler anses vara unika.</span><span class="sxs-lookup"><span data-stu-id="80732-221">As a result, strings that differ only in character casing are considered to be unique.</span></span>

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

### <span data-ttu-id="80732-222">– Vänta</span><span class="sxs-lookup"><span data-stu-id="80732-222">-Wait</span></span>

<span data-ttu-id="80732-223">Anger att-cmdleten inaktiverar optimering.</span><span class="sxs-lookup"><span data-stu-id="80732-223">Indicates that the cmdlet turns off optimization.</span></span> <span data-ttu-id="80732-224">PowerShell kör kommandon i den ordning som de visas i kommandot pipeliner och låter dem generera alla objekt.</span><span class="sxs-lookup"><span data-stu-id="80732-224">PowerShell runs commands in the order that they appear in the command pipeline and lets them generate all objects.</span></span> <span data-ttu-id="80732-225">Om du inkluderar ett `Select-Object` kommando med de **första** eller **index** parametrarna i en kommando pipeline, stoppar PowerShell som standard kommandot som genererar objekten så fort det valda antalet objekt genereras.</span><span class="sxs-lookup"><span data-stu-id="80732-225">By default, if you include a `Select-Object` command with the **First** or **Index** parameters in a command pipeline, PowerShell stops the command that generates the objects as soon as the selected number of objects is generated.</span></span>

<span data-ttu-id="80732-226">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="80732-226">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="80732-227">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="80732-227">CommonParameters</span></span>

<span data-ttu-id="80732-228">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="80732-228">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="80732-229">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="80732-229">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="80732-230">INDATA</span><span class="sxs-lookup"><span data-stu-id="80732-230">INPUTS</span></span>

### <span data-ttu-id="80732-231">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="80732-231">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="80732-232">Du kan skicka vidare alla objekt till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="80732-232">You can pipe any object to `Select-Object`.</span></span>

## <span data-ttu-id="80732-233">UTDATA</span><span class="sxs-lookup"><span data-stu-id="80732-233">OUTPUTS</span></span>

### <span data-ttu-id="80732-234">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="80732-234">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="80732-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="80732-235">NOTES</span></span>

- <span data-ttu-id="80732-236">Du kan också referera till `Select-Object` cmdleten med dess inbyggda alias `select` .</span><span class="sxs-lookup"><span data-stu-id="80732-236">You can also refer to the `Select-Object` cmdlet by its built-in alias, `select`.</span></span> <span data-ttu-id="80732-237">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="80732-237">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

- <span data-ttu-id="80732-238">Optimerings funktionen i `Select-Object` är bara tillgänglig för kommandon som skriver objekt till pipelinen när de bearbetas.</span><span class="sxs-lookup"><span data-stu-id="80732-238">The optimization feature of `Select-Object` is available only for commands that write objects to the pipeline as they are processed.</span></span> <span data-ttu-id="80732-239">Den har ingen påverkan på kommandon som buffrar bearbetade objekt och skriver dem som en samling.</span><span class="sxs-lookup"><span data-stu-id="80732-239">It has no effect on commands that buffer processed objects and write them as a collection.</span></span> <span data-ttu-id="80732-240">Att skriva objekt direkt är en bästa praxis för cmdlet-design.</span><span class="sxs-lookup"><span data-stu-id="80732-240">Writing objects immediately is a cmdlet design best practice.</span></span> <span data-ttu-id="80732-241">Mer information finns i _skriva enstaka poster till pipelinen i den_ [starkt uppmuntrande utvecklings rikt linjerna](/powershell/scripting/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="80732-241">For more information, see _Write Single Records to the Pipeline_ in [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/windows-powershell).</span></span>

## <span data-ttu-id="80732-242">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="80732-242">RELATED LINKS</span></span>

[<span data-ttu-id="80732-243">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="80732-243">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="80732-244">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="80732-244">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="80732-245">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="80732-245">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="80732-246">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="80732-246">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)
