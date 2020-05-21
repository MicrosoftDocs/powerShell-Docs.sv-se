---
ms.date: 09/13/2019
title: Skapar Get-WinEvent-frågor med FilterHashtable
ms.openlocfilehash: 485b0cf05489d9add201c71c01fe2ed0c48db387
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563928"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="f34fb-102">Skapar Get-WinEvent-frågor med FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="f34fb-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="f34fb-103">Om du vill läsa det ursprungliga blogg inlägget 3 juni 2014 **Scripting Guy** , se [använda FilterHashTable för att filtrera händelse loggen med PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="f34fb-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="f34fb-104">Den här artikeln är ett utdrag från det ursprungliga blogg inlägget och förklarar hur du använder `Get-WinEvent` cmdletens **FilterHashtable** -parameter för att filtrera händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="f34fb-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="f34fb-105">PowerShell- `Get-WinEvent` cmdleten är en kraftfull metod för att filtrera Windows-händelser och diagnostikloggar.</span><span class="sxs-lookup"><span data-stu-id="f34fb-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="f34fb-106">Prestanda förbättras när en `Get-WinEvent` fråga använder parametern **FilterHashtable** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="f34fb-107">När du arbetar med stora händelse loggar är det inte effektivt att skicka objekt nedåt i pipelinen till ett `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="f34fb-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="f34fb-108">Innan PowerShell 6 `Get-EventLog` var cmdleten ett annat alternativ för att hämta loggdata.</span><span class="sxs-lookup"><span data-stu-id="f34fb-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="f34fb-109">Följande kommandon är till exempel ineffektiva för att filtrera **Microsoft-Windows-defrag-** loggar:</span><span class="sxs-lookup"><span data-stu-id="f34fb-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="f34fb-110">Följande kommando använder en hash-tabell som förbättrar prestandan:</span><span class="sxs-lookup"><span data-stu-id="f34fb-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="f34fb-111">Blogg inlägg om uppräkning</span><span class="sxs-lookup"><span data-stu-id="f34fb-111">Blog posts about enumeration</span></span>

<span data-ttu-id="f34fb-112">Den här artikeln visar information om hur du använder uppräknade värden i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="f34fb-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="f34fb-113">Om du vill ha mer information om uppräkning läser du dessa blogg inlägg i **skript Guy** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="f34fb-114">Information om hur du skapar en funktion som returnerar de uppräknade värdena finns i [uppräkningar och värden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="f34fb-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="f34fb-115">Mer information finns i [Scripting Guy-serien av blogg inlägg om uppräkning](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="f34fb-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="f34fb-116">Nyckel/värde-par för hash-tabell</span><span class="sxs-lookup"><span data-stu-id="f34fb-116">Hash table key-value pairs</span></span>

<span data-ttu-id="f34fb-117">Om du vill bygga effektiva frågor använder du `Get-WinEvent` cmdleten med parametern **FilterHashtable** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="f34fb-118">**FilterHashtable** accepterar en hash-tabell som ett filter för att hämta detaljerad information från händelse loggar i Windows.</span><span class="sxs-lookup"><span data-stu-id="f34fb-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="f34fb-119">En hash-tabell använder **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="f34fb-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="f34fb-120">Mer information om hash-tabeller finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="f34fb-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="f34fb-121">Om **nyckel-** värdeparen finns på samma rad måste de avgränsas med ett semikolon.</span><span class="sxs-lookup"><span data-stu-id="f34fb-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="f34fb-122">Om varje **nyckel/värde-** par finns på en separat rad behövs inte semikolonet.</span><span class="sxs-lookup"><span data-stu-id="f34fb-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="f34fb-123">I den här artikeln placeras till exempel **nyckel värdes** par på separata rader och använder inte semikolon.</span><span class="sxs-lookup"><span data-stu-id="f34fb-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="f34fb-124">I det här exemplet används flera av **FilterHashtable** -parameterns **nyckel/värde-** par.</span><span class="sxs-lookup"><span data-stu-id="f34fb-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="f34fb-125">Den slutförda frågan innehåller **LogName**, **ProviderName**, **keywords**, **ID**och **Level**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="f34fb-126">De accepterade **nyckel-** värdeparen visas i följande tabell och ingår i dokumentationen för parametern [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent) 
 **FilterHashtable** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="f34fb-127">I följande tabell visas nyckel namnen, data typerna och om jokertecken accepteras för ett data värde.</span><span class="sxs-lookup"><span data-stu-id="f34fb-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="f34fb-128">Nyckelnamn</span><span class="sxs-lookup"><span data-stu-id="f34fb-128">Key name</span></span>    | <span data-ttu-id="f34fb-129">Värde data typ</span><span class="sxs-lookup"><span data-stu-id="f34fb-129">Value data type</span></span> | <span data-ttu-id="f34fb-130">Accepterar jokertecken?</span><span class="sxs-lookup"><span data-stu-id="f34fb-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="f34fb-131">LogName</span><span class="sxs-lookup"><span data-stu-id="f34fb-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="f34fb-132">Ja</span><span class="sxs-lookup"><span data-stu-id="f34fb-132">Yes</span></span>                          |
| <span data-ttu-id="f34fb-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="f34fb-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="f34fb-134">Ja</span><span class="sxs-lookup"><span data-stu-id="f34fb-134">Yes</span></span>                          |
| <span data-ttu-id="f34fb-135">Sökväg</span><span class="sxs-lookup"><span data-stu-id="f34fb-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="f34fb-136">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-136">No</span></span>                           |
| <span data-ttu-id="f34fb-137">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="f34fb-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="f34fb-138">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-138">No</span></span>                           |
| <span data-ttu-id="f34fb-139">ID</span><span class="sxs-lookup"><span data-stu-id="f34fb-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="f34fb-140">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-140">No</span></span>                           |
| <span data-ttu-id="f34fb-141">Nivå</span><span class="sxs-lookup"><span data-stu-id="f34fb-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="f34fb-142">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-142">No</span></span>                           |
| <span data-ttu-id="f34fb-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="f34fb-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="f34fb-144">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-144">No</span></span>                           |
| <span data-ttu-id="f34fb-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="f34fb-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="f34fb-146">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-146">No</span></span>                           |
| <span data-ttu-id="f34fb-147">UserID</span><span class="sxs-lookup"><span data-stu-id="f34fb-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="f34fb-148">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-148">No</span></span>                           |
| <span data-ttu-id="f34fb-149">Data</span><span class="sxs-lookup"><span data-stu-id="f34fb-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="f34fb-150">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="f34fb-151">Nej</span><span class="sxs-lookup"><span data-stu-id="f34fb-151">No</span></span>                           |

<span data-ttu-id="f34fb-152">`<named-data>`Nyckeln representerar ett namngivet händelse data fält.</span><span class="sxs-lookup"><span data-stu-id="f34fb-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="f34fb-153">Till exempel kan Perflib Event 1008 innehålla följande händelse data:</span><span class="sxs-lookup"><span data-stu-id="f34fb-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="f34fb-154">Du kan fråga efter dessa händelser med hjälp av följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f34fb-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="f34fb-155">Möjligheten att fråga efter `<named-data>` har lagts till i PowerShell 6.</span><span class="sxs-lookup"><span data-stu-id="f34fb-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="f34fb-156">Skapa en fråga med en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="f34fb-156">Building a query with a hash table</span></span>

<span data-ttu-id="f34fb-157">Om du vill kontrol lera resultaten och felsöka problem kan du skapa hash-tabellen ett **nyckel/värde-** par i taget.</span><span class="sxs-lookup"><span data-stu-id="f34fb-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="f34fb-158">Frågan hämtar data från **program** loggen.</span><span class="sxs-lookup"><span data-stu-id="f34fb-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="f34fb-159">Hash-tabellen motsvarar `Get-WinEvent –LogName Application` .</span><span class="sxs-lookup"><span data-stu-id="f34fb-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="f34fb-160">Börja genom att skapa `Get-WinEvent` frågan.</span><span class="sxs-lookup"><span data-stu-id="f34fb-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="f34fb-161">Använd **FilterHashtable** -parameterns **nyckel/värde-** par med nyckeln, **LogName**och värdet, **programmet**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="f34fb-162">Fortsätt att skapa hash-tabellen med **ProviderName** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="f34fb-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="f34fb-163">**ProviderName** är det namn som visas i fältet **källa** i **Windows Loggboken**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="f34fb-164">Till exempel **.NET Runtime** på följande skärm bild:</span><span class="sxs-lookup"><span data-stu-id="f34fb-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Bild av Windows Loggboken-källor.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="f34fb-166">Uppdatera hash-tabellen och inkludera **nyckel värdes** paret med nyckeln, **ProviderName**och värdet **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-166">Update the hash table and include the **key-value** pair with the key, **ProviderName**, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="f34fb-167">Använd **Sök vägs** nyckeln om din fråga behöver hämta data från arkiverade händelse loggar.</span><span class="sxs-lookup"><span data-stu-id="f34fb-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="f34fb-168">Värdet **Path** anger den fullständiga sökvägen till logg filen.</span><span class="sxs-lookup"><span data-stu-id="f34fb-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="f34fb-169">Mer information finns i blogg inlägget **Scripting Guy** , [använda PowerShell för att analysera sparade händelse loggar för fel](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="f34fb-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="f34fb-170">Använda uppräknade värden i en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="f34fb-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="f34fb-171">**Nyckelord** är nästa nyckel i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="f34fb-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="f34fb-172">Data typen **keywords** är en matris av `[long]` värde typen som innehåller ett stort tal.</span><span class="sxs-lookup"><span data-stu-id="f34fb-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="f34fb-173">Använd följande kommando för att hitta det högsta värdet `[long]` :</span><span class="sxs-lookup"><span data-stu-id="f34fb-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="f34fb-174">För **nyckelords** nyckeln använder PowerShell ett nummer, inte en sträng som **säkerhet**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="f34fb-175">**Windows Loggboken** visar **nyckelorden** som strängar, men de är uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="f34fb-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="f34fb-176">Om du använder **nyckelords** nyckeln med ett sträng värde i hash-tabellen visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="f34fb-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="f34fb-177">Öppna **Windows Loggboken** och klicka på **Filtrera aktuell logg**i fönstret **åtgärder** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="f34fb-178">På den nedrullningsbara menyn **nyckelord** visas tillgängliga nyckelord, som du ser på följande skärm bild:</span><span class="sxs-lookup"><span data-stu-id="f34fb-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Bild av Windows Loggboken nyckelord.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="f34fb-180">Använd följande kommando för att visa `StandardEventKeywords` egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="f34fb-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="f34fb-181">De uppräknade värdena dokumenteras i **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="f34fb-182">Mer information finns i [StandardEventKeywords-uppräkning](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="f34fb-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="f34fb-183">**Nyckelords** namnen och de uppräknade värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="f34fb-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="f34fb-184">Name</span><span class="sxs-lookup"><span data-stu-id="f34fb-184">Name</span></span>             |  <span data-ttu-id="f34fb-185">Värde</span><span class="sxs-lookup"><span data-stu-id="f34fb-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="f34fb-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="f34fb-186">AuditFailure</span></span>     | <span data-ttu-id="f34fb-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="f34fb-187">4503599627370496</span></span>  |
| <span data-ttu-id="f34fb-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="f34fb-188">AuditSuccess</span></span>     | <span data-ttu-id="f34fb-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="f34fb-189">9007199254740992</span></span>  |
| <span data-ttu-id="f34fb-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="f34fb-190">CorrelationHint2</span></span> | <span data-ttu-id="f34fb-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="f34fb-191">18014398509481984</span></span> |
| <span data-ttu-id="f34fb-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="f34fb-192">EventLogClassic</span></span>  | <span data-ttu-id="f34fb-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="f34fb-193">36028797018963968</span></span> |
| <span data-ttu-id="f34fb-194">SQM</span><span class="sxs-lookup"><span data-stu-id="f34fb-194">Sqm</span></span>              | <span data-ttu-id="f34fb-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="f34fb-195">2251799813685248</span></span>  |
| <span data-ttu-id="f34fb-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="f34fb-196">WdiDiagnostic</span></span>    | <span data-ttu-id="f34fb-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="f34fb-197">1125899906842624</span></span>  |
| <span data-ttu-id="f34fb-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="f34fb-198">WdiContext</span></span>       | <span data-ttu-id="f34fb-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="f34fb-199">562949953421312</span></span>   |
| <span data-ttu-id="f34fb-200">SLA svarstid</span><span class="sxs-lookup"><span data-stu-id="f34fb-200">ResponseTime</span></span>     | <span data-ttu-id="f34fb-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="f34fb-201">281474976710656</span></span>   |
| <span data-ttu-id="f34fb-202">Inga</span><span class="sxs-lookup"><span data-stu-id="f34fb-202">None</span></span>             | <span data-ttu-id="f34fb-203">0</span><span class="sxs-lookup"><span data-stu-id="f34fb-203">0</span></span>                 |

<span data-ttu-id="f34fb-204">Uppdatera hash-tabellen och inkludera **nyckel/värde-** paret med nyckeln, **nyckelorden**och **EventLogClassic** -uppräkning svärdet **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="f34fb-205">Nyckelord statiskt egenskaps värde (valfritt)</span><span class="sxs-lookup"><span data-stu-id="f34fb-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="f34fb-206">**Nyckelords** nyckeln räknas upp, men du kan använda ett statiskt egenskaps namn i hash-tabellens fråga.</span><span class="sxs-lookup"><span data-stu-id="f34fb-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="f34fb-207">I stället för att använda den returnerade strängen måste egenskaps namnet konverteras till ett värde med egenskapen **Value__** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="f34fb-208">Följande skript använder till exempel egenskapen **Value__** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="f34fb-209">Filtrera efter händelse-ID</span><span class="sxs-lookup"><span data-stu-id="f34fb-209">Filtering by Event Id</span></span>

<span data-ttu-id="f34fb-210">För att få mer information, filtreras frågans resultat efter **händelse-ID**. **Händelse-ID: t** refereras i hash-tabellen som nyckel **-ID** och värdet är ett särskilt **händelse-ID**. **Windows-Loggboken** visar **händelse-ID: t**. I det här exemplet används **händelse-Id 1023**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="f34fb-211">Uppdatera hash-tabellen och inkludera **nyckel värdes** paret med nyckeln, **ID: t** och värdet **1023**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="f34fb-212">Filtrera efter nivå</span><span class="sxs-lookup"><span data-stu-id="f34fb-212">Filtering by Level</span></span>

<span data-ttu-id="f34fb-213">Om du vill förfina resultaten ytterligare och bara inkludera händelser som är fel använder du **nivå** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="f34fb-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="f34fb-214">**Windows Loggboken** visar **nivån** som sträng värden, men de är uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="f34fb-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="f34fb-215">Om du använder **nivå** nyckeln med ett sträng värde i hash-tabellen visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="f34fb-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="f34fb-216">**Nivån** har värden som **fel**, **Varning**eller **information**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="f34fb-217">Använd följande kommando för att visa `StandardEventLevel` egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="f34fb-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="f34fb-218">De uppräknade värdena dokumenteras i **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="f34fb-219">Mer information finns i [StandardEventLevel-uppräkning](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="f34fb-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="f34fb-220">**Nivå** nyckelns namn och uppräknade värden är följande:</span><span class="sxs-lookup"><span data-stu-id="f34fb-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="f34fb-221">Name</span><span class="sxs-lookup"><span data-stu-id="f34fb-221">Name</span></span>           | <span data-ttu-id="f34fb-222">Värde</span><span class="sxs-lookup"><span data-stu-id="f34fb-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="f34fb-223">Verbose</span><span class="sxs-lookup"><span data-stu-id="f34fb-223">Verbose</span></span>        |   <span data-ttu-id="f34fb-224">5</span><span class="sxs-lookup"><span data-stu-id="f34fb-224">5</span></span>   |
| <span data-ttu-id="f34fb-225">Information</span><span class="sxs-lookup"><span data-stu-id="f34fb-225">Informational</span></span>  |   <span data-ttu-id="f34fb-226">4</span><span class="sxs-lookup"><span data-stu-id="f34fb-226">4</span></span>   |
| <span data-ttu-id="f34fb-227">Varning</span><span class="sxs-lookup"><span data-stu-id="f34fb-227">Warning</span></span>        |   <span data-ttu-id="f34fb-228">3</span><span class="sxs-lookup"><span data-stu-id="f34fb-228">3</span></span>   |
| <span data-ttu-id="f34fb-229">Fel</span><span class="sxs-lookup"><span data-stu-id="f34fb-229">Error</span></span>          |   <span data-ttu-id="f34fb-230">2</span><span class="sxs-lookup"><span data-stu-id="f34fb-230">2</span></span>   |
| <span data-ttu-id="f34fb-231">Kritiskt</span><span class="sxs-lookup"><span data-stu-id="f34fb-231">Critical</span></span>       |   <span data-ttu-id="f34fb-232">1</span><span class="sxs-lookup"><span data-stu-id="f34fb-232">1</span></span>   |
| <span data-ttu-id="f34fb-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="f34fb-233">LogAlways</span></span>      |   <span data-ttu-id="f34fb-234">0</span><span class="sxs-lookup"><span data-stu-id="f34fb-234">0</span></span>   |

<span data-ttu-id="f34fb-235">Hash-tabellen för den slutförda frågan innehåller nyckeln, **nivån**och värdet, **2**.</span><span class="sxs-lookup"><span data-stu-id="f34fb-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="f34fb-236">Nivå statisk egenskap i uppräkning (valfritt)</span><span class="sxs-lookup"><span data-stu-id="f34fb-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="f34fb-237">**Nivå** nyckeln räknas upp, men du kan använda ett statiskt egenskaps namn i hash-tabellens fråga.</span><span class="sxs-lookup"><span data-stu-id="f34fb-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="f34fb-238">I stället för att använda den returnerade strängen måste egenskaps namnet konverteras till ett värde med egenskapen **Value__** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="f34fb-239">Följande skript använder till exempel egenskapen **Value__** .</span><span class="sxs-lookup"><span data-stu-id="f34fb-239">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```
