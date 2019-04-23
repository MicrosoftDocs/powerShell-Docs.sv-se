---
ms.date: 3/18/2019
title: Skapar Get-WinEvent-frågor med FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: f4bd4e116e22c8b5bfcb61680a7c42e58b4da93e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59984229"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="567fe-102">Skapar Get-WinEvent-frågor med FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="567fe-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="567fe-103">Att läsa den ursprungliga juni 3 2014 **Scripting Guy** blogg post-, se [Använd FilterHashTable att filtrera händelseloggen med PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span><span class="sxs-lookup"><span data-stu-id="567fe-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="567fe-104">Den här artikeln är ett utdrag ur ursprungliga blogginlägget och förklarar hur du använder den `Get-WinEvent` cmdletens **FilterHashtable** parameter för att filtrera händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="567fe-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="567fe-105">PowerShell- `Get-WinEvent` cmdleten är en kraftfull metod för att filtrera Windows händelse- och diagnostikloggar.</span><span class="sxs-lookup"><span data-stu-id="567fe-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="567fe-106">Prestanda förbättras när en `Get-WinEvent` fråga använder den **FilterHashtable** parametern.</span><span class="sxs-lookup"><span data-stu-id="567fe-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="567fe-107">När du arbetar med stora händelseloggar, är det inte effektivt att skicka objekt att pipelinen en `Where-Object` kommando.</span><span class="sxs-lookup"><span data-stu-id="567fe-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="567fe-108">Innan du PowerShell 6, den `Get-EventLog` cmdlet har ett annat alternativ att hämta loggdata.</span><span class="sxs-lookup"><span data-stu-id="567fe-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="567fe-109">Till exempel följande kommandon är ineffektiv till filter på **Microsoft-Windows-defragmenterar** loggar:</span><span class="sxs-lookup"><span data-stu-id="567fe-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="567fe-110">Följande kommando använder en hash-tabell som förbättrar prestanda:</span><span class="sxs-lookup"><span data-stu-id="567fe-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="567fe-111">Blogginlägg om uppräkning</span><span class="sxs-lookup"><span data-stu-id="567fe-111">Blog posts about enumeration</span></span>

<span data-ttu-id="567fe-112">Den här artikeln innehåller information om hur du använder uppräknade värden i en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="567fe-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="567fe-113">Mer information om uppräkning Läs dessa **Scripting Guy** blogginlägg.</span><span class="sxs-lookup"><span data-stu-id="567fe-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="567fe-114">För att skapa en funktion som returnerar uppräknade värden, se [uppräkningar och värden](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span><span class="sxs-lookup"><span data-stu-id="567fe-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="567fe-115">Mer information finns i den [Scripting Guy serie blogg inlägg om uppräkningen](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="567fe-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="567fe-116">Hash-tabell nyckel/värde-par</span><span class="sxs-lookup"><span data-stu-id="567fe-116">Hash table key/value pairs</span></span>

<span data-ttu-id="567fe-117">För att skapa effektiva frågor, använda den `Get-WinEvent` cmdlet med den **FilterHashtable** parametern.</span><span class="sxs-lookup"><span data-stu-id="567fe-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="567fe-118">**FilterHashtable** accepterar en hash-tabell som ett filter för att få specifik information från Windows-händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="567fe-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="567fe-119">En hash-tabell använder **nyckel/värde** par.</span><span class="sxs-lookup"><span data-stu-id="567fe-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="567fe-120">Mer information om hash-tabeller finns i [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="567fe-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="567fe-121">Om den **nyckel/värde** par är på samma rad, de måste avgränsas med semikolon.</span><span class="sxs-lookup"><span data-stu-id="567fe-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="567fe-122">Om varje **nyckel/värde** par är på en separat rad, semikolon behövs inte.</span><span class="sxs-lookup"><span data-stu-id="567fe-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="567fe-123">Exempelvis kan den här artikeln placerar **nyckel/värde** kombinationer av på separata rader och inte använda semikolon.</span><span class="sxs-lookup"><span data-stu-id="567fe-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="567fe-124">Det här exemplet används flera av de **FilterHashtable** parameterns **nyckel/värde** par.</span><span class="sxs-lookup"><span data-stu-id="567fe-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="567fe-125">Slutförda frågan innehåller **loggnamn**, **ProviderName**, **nyckelord**, **ID**, och **nivå**.</span><span class="sxs-lookup"><span data-stu-id="567fe-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="567fe-126">Det godkända **nyckel/värde** par visas i följande tabell och ingår i dokumentationen för den [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span><span class="sxs-lookup"><span data-stu-id="567fe-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="567fe-127">I följande tabell visar namn, datatyper, och om jokertecken godkänns för värdet.</span><span class="sxs-lookup"><span data-stu-id="567fe-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="567fe-128">Nyckelnamn</span><span class="sxs-lookup"><span data-stu-id="567fe-128">Key name</span></span>     | <span data-ttu-id="567fe-129">Värdetyp för data</span><span class="sxs-lookup"><span data-stu-id="567fe-129">Value data type</span></span>    | <span data-ttu-id="567fe-130">Accepterar jokertecken?</span><span class="sxs-lookup"><span data-stu-id="567fe-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="567fe-131">Loggnamn</span><span class="sxs-lookup"><span data-stu-id="567fe-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="567fe-132">Ja</span><span class="sxs-lookup"><span data-stu-id="567fe-132">Yes</span></span> |
| <span data-ttu-id="567fe-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="567fe-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="567fe-134">Ja</span><span class="sxs-lookup"><span data-stu-id="567fe-134">Yes</span></span> |
| <span data-ttu-id="567fe-135">Sökväg</span><span class="sxs-lookup"><span data-stu-id="567fe-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="567fe-136">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-136">No</span></span>  |
| <span data-ttu-id="567fe-137">nyckelord</span><span class="sxs-lookup"><span data-stu-id="567fe-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="567fe-138">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-138">No</span></span>  |
| <span data-ttu-id="567fe-139">ID</span><span class="sxs-lookup"><span data-stu-id="567fe-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="567fe-140">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-140">No</span></span>  |
| <span data-ttu-id="567fe-141">Nivå</span><span class="sxs-lookup"><span data-stu-id="567fe-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="567fe-142">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-142">No</span></span>  |
| <span data-ttu-id="567fe-143">startTime</span><span class="sxs-lookup"><span data-stu-id="567fe-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="567fe-144">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-144">No</span></span>  |
| <span data-ttu-id="567fe-145">endTime</span><span class="sxs-lookup"><span data-stu-id="567fe-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="567fe-146">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-146">No</span></span>  |
| <span data-ttu-id="567fe-147">Användar-ID</span><span class="sxs-lookup"><span data-stu-id="567fe-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="567fe-148">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-148">No</span></span>  |
| <span data-ttu-id="567fe-149">Data</span><span class="sxs-lookup"><span data-stu-id="567fe-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="567fe-150">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="567fe-151">Nej</span><span class="sxs-lookup"><span data-stu-id="567fe-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="567fe-152">Att skapa en fråga med en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="567fe-152">Building a query with a hash table</span></span>

<span data-ttu-id="567fe-153">För att kontrollera resultaten och felsöka problem, det hjälper dig för att skapa en hash-tabellen **nyckel/värde** paret åt gången.</span><span class="sxs-lookup"><span data-stu-id="567fe-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="567fe-154">Frågan hämtar data från den **program** log.</span><span class="sxs-lookup"><span data-stu-id="567fe-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="567fe-155">Hash-tabellen motsvarar `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="567fe-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="567fe-156">Börja genom att skapa den `Get-WinEvent` fråga.</span><span class="sxs-lookup"><span data-stu-id="567fe-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="567fe-157">Använd den **FilterHashtable** parameterns **nyckel/värde** paras ihop med nyckeln, **loggnamn**, och värdet, **program**.</span><span class="sxs-lookup"><span data-stu-id="567fe-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="567fe-158">Fortsätt att skapa hash-tabellen med den **ProviderName** nyckel.</span><span class="sxs-lookup"><span data-stu-id="567fe-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="567fe-159">Den **ProviderName** är det namn som visas i den **källa** i den **Windows Loggboken**.</span><span class="sxs-lookup"><span data-stu-id="567fe-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="567fe-160">Till exempel **.NET Runtime** i följande skärmbild:</span><span class="sxs-lookup"><span data-stu-id="567fe-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Bild av Windows Loggboken källor.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="567fe-162">Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, \*\* ProviderName, och värdet, **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="567fe-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="567fe-163">Om din fråga måste hämta data från arkiverade händelseloggar, använder du den **sökväg** nyckel.</span><span class="sxs-lookup"><span data-stu-id="567fe-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="567fe-164">Den **sökväg** värdet anger den fullständiga sökvägen till loggfilen.</span><span class="sxs-lookup"><span data-stu-id="567fe-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="567fe-165">Mer information finns i den **Scripting Guy** blogginlägget [Använd PowerShell för att parsa sparade händelseloggarna för fel](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span><span class="sxs-lookup"><span data-stu-id="567fe-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="567fe-166">Använda uppräknade värden i en hash-tabell</span><span class="sxs-lookup"><span data-stu-id="567fe-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="567fe-167">**Nyckelord** är nästa nyckel i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="567fe-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="567fe-168">Den **nyckelord** datatyp är en matris med de `[long]` värdetyp som innehåller ett stort antal.</span><span class="sxs-lookup"><span data-stu-id="567fe-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="567fe-169">Använd följande kommando för att hitta det maximala värdet `[long]`:</span><span class="sxs-lookup"><span data-stu-id="567fe-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="567fe-170">För den **nyckelord** nyckel, PowerShell använder ett tal, inte en sträng som **Security**.</span><span class="sxs-lookup"><span data-stu-id="567fe-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="567fe-171">**Windows Loggboken** visar den **nyckelord** som strängar, men de är uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="567fe-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="567fe-172">I hashtabellen, om du använder den **nyckelord** nyckeln med ett strängvärde, visas ett felmeddelande.</span><span class="sxs-lookup"><span data-stu-id="567fe-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="567fe-173">Öppna den **Windows Loggboken** och från den **åtgärder** klickar du på på **Filtrera aktuell logg**.</span><span class="sxs-lookup"><span data-stu-id="567fe-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="567fe-174">Den **nyckelord** nedrullningsbara menyn visar tillgängliga nyckelord, enligt följande skärmbild:</span><span class="sxs-lookup"><span data-stu-id="567fe-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Bild av Windows Loggboken nyckelord.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="567fe-176">Använd följande kommando för att visa den `StandardEventKeywords` egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="567fe-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="567fe-177">Uppräknade värden är dokumenterade i den **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="567fe-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="567fe-178">Mer information finns i [StandardEventKeywords uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="567fe-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="567fe-179">Den **nyckelord** namn och uppräknade värden är följande:</span><span class="sxs-lookup"><span data-stu-id="567fe-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="567fe-180">Namn</span><span class="sxs-lookup"><span data-stu-id="567fe-180">Name</span></span>             |  <span data-ttu-id="567fe-181">Värde</span><span class="sxs-lookup"><span data-stu-id="567fe-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="567fe-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="567fe-182">AuditFailure</span></span>     | <span data-ttu-id="567fe-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="567fe-183">4503599627370496</span></span>  |
| <span data-ttu-id="567fe-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="567fe-184">AuditSuccess</span></span>     | <span data-ttu-id="567fe-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="567fe-185">9007199254740992</span></span>  |
| <span data-ttu-id="567fe-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="567fe-186">CorrelationHint2</span></span> | <span data-ttu-id="567fe-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="567fe-187">18014398509481984</span></span> |
| <span data-ttu-id="567fe-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="567fe-188">EventLogClassic</span></span>  | <span data-ttu-id="567fe-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="567fe-189">36028797018963968</span></span> |
| <span data-ttu-id="567fe-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="567fe-190">Sqm</span></span>              | <span data-ttu-id="567fe-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="567fe-191">2251799813685248</span></span>  |
| <span data-ttu-id="567fe-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="567fe-192">WdiDiagnostic</span></span>    | <span data-ttu-id="567fe-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="567fe-193">1125899906842624</span></span>  |
| <span data-ttu-id="567fe-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="567fe-194">WdiContext</span></span>       | <span data-ttu-id="567fe-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="567fe-195">562949953421312</span></span>   |
| <span data-ttu-id="567fe-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="567fe-196">ResponseTime</span></span>     | <span data-ttu-id="567fe-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="567fe-197">281474976710656</span></span>   |
| <span data-ttu-id="567fe-198">Inga</span><span class="sxs-lookup"><span data-stu-id="567fe-198">None</span></span>             | <span data-ttu-id="567fe-199">0</span><span class="sxs-lookup"><span data-stu-id="567fe-199">0</span></span>                 |

<span data-ttu-id="567fe-200">Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, **nyckelord**, och **EventLogClassic** uppräkningsvärdet **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="567fe-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="567fe-201">Nyckelord statiska egenskapsvärdet (valfritt)</span><span class="sxs-lookup"><span data-stu-id="567fe-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="567fe-202">Den **nyckelord** nyckel räknas, men du kan använda en statisk egenskapsnamn i frågan för hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="567fe-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="567fe-203">I stället för den returnerade strängen, egenskapsnamnet måste konverteras till ett värde med den **Value__** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="567fe-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="567fe-204">Till exempel följande skript använder den **Value__** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="567fe-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="567fe-205">Filtrering efter händelse-Id</span><span class="sxs-lookup"><span data-stu-id="567fe-205">Filtering by Event Id</span></span>

<span data-ttu-id="567fe-206">Om du vill ha mer specifika data, resultatet av frågan filtreras efter **händelse-Id**. Den **händelse-Id** refereras till i hash-tabell som nyckel **ID** och värdet är en specifik **händelse-Id**. Den **Windows Loggboken** visar den **händelse-Id**. Det här exemplet används **händelse-Id 1023**.</span><span class="sxs-lookup"><span data-stu-id="567fe-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="567fe-207">Uppdatera hash-tabellen och inkludera den **nyckel/värde** paras ihop med nyckeln, **ID** och värdet, **1023**.</span><span class="sxs-lookup"><span data-stu-id="567fe-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="567fe-208">Filtrera efter nivå</span><span class="sxs-lookup"><span data-stu-id="567fe-208">Filtering by Level</span></span>

<span data-ttu-id="567fe-209">För att ytterligare förfina resultaten och inkluderar endast de händelser som är fel, Använd den **nivå** nyckel.</span><span class="sxs-lookup"><span data-stu-id="567fe-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="567fe-210">**Windows Loggboken** visar den **nivå** som sträng värden, men de är uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="567fe-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="567fe-211">I hashtabellen, om du använder den **nivå** nyckeln med ett strängvärde, visas ett felmeddelande.</span><span class="sxs-lookup"><span data-stu-id="567fe-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="567fe-212">**Nivå** har värden som **fel**, **varning**, eller **information**.</span><span class="sxs-lookup"><span data-stu-id="567fe-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="567fe-213">Använd följande kommando för att visa den `StandardEventLevel` egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="567fe-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="567fe-214">Uppräknade värden är dokumenterade i den **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="567fe-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="567fe-215">Mer information finns i [StandardEventLevel uppräkning](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="567fe-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="567fe-216">Den **nivå** nyckelns namn och uppräknade värden är följande:</span><span class="sxs-lookup"><span data-stu-id="567fe-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="567fe-217">Namn</span><span class="sxs-lookup"><span data-stu-id="567fe-217">Name</span></span>           | <span data-ttu-id="567fe-218">Värde</span><span class="sxs-lookup"><span data-stu-id="567fe-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="567fe-219">Utförlig</span><span class="sxs-lookup"><span data-stu-id="567fe-219">Verbose</span></span>        |   <span data-ttu-id="567fe-220">5</span><span class="sxs-lookup"><span data-stu-id="567fe-220">5</span></span>   |
| <span data-ttu-id="567fe-221">Informativt</span><span class="sxs-lookup"><span data-stu-id="567fe-221">Informational</span></span>  |   <span data-ttu-id="567fe-222">4</span><span class="sxs-lookup"><span data-stu-id="567fe-222">4</span></span>   |
| <span data-ttu-id="567fe-223">Varning</span><span class="sxs-lookup"><span data-stu-id="567fe-223">Warning</span></span>        |   <span data-ttu-id="567fe-224">3</span><span class="sxs-lookup"><span data-stu-id="567fe-224">3</span></span>   |
| <span data-ttu-id="567fe-225">Fel</span><span class="sxs-lookup"><span data-stu-id="567fe-225">Error</span></span>          |   <span data-ttu-id="567fe-226">2</span><span class="sxs-lookup"><span data-stu-id="567fe-226">2</span></span>   |
| <span data-ttu-id="567fe-227">Kritiskt</span><span class="sxs-lookup"><span data-stu-id="567fe-227">Critical</span></span>       |   <span data-ttu-id="567fe-228">1</span><span class="sxs-lookup"><span data-stu-id="567fe-228">1</span></span>   |
| <span data-ttu-id="567fe-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="567fe-229">LogAlways</span></span>      |   <span data-ttu-id="567fe-230">0</span><span class="sxs-lookup"><span data-stu-id="567fe-230">0</span></span>   |

<span data-ttu-id="567fe-231">Hash-tabellen för slutförda frågan innehåller nyckeln, **nivå**, och värdet, **2**.</span><span class="sxs-lookup"><span data-stu-id="567fe-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="567fe-232">Nivån statisk egenskap i uppräkningen (valfritt)</span><span class="sxs-lookup"><span data-stu-id="567fe-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="567fe-233">Den **nivå** nyckel räknas, men du kan använda en statisk egenskapsnamn i frågan för hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="567fe-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="567fe-234">I stället för den returnerade strängen, egenskapsnamnet måste konverteras till ett värde med den **Value__** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="567fe-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="567fe-235">Till exempel följande skript använder den **Value__** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="567fe-235">For example, the following script uses the **Value__** property.</span></span>

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