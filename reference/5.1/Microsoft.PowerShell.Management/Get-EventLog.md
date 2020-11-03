---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266162"
---
# <span data-ttu-id="aecc0-103">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-103">Get-EventLog</span></span>

## <span data-ttu-id="aecc0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="aecc0-104">SYNOPSIS</span></span>
<span data-ttu-id="aecc0-105">Hämtar händelserna i en händelse logg eller en lista över händelse loggar på den lokala datorn eller fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-105">Gets the events in an event log, or a list of the event logs, on the local computer or remote computers.</span></span>

## <span data-ttu-id="aecc0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aecc0-106">SYNTAX</span></span>

### <span data-ttu-id="aecc0-107">LogName (standard)</span><span class="sxs-lookup"><span data-stu-id="aecc0-107">LogName (Default)</span></span>

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### <span data-ttu-id="aecc0-108">Lista</span><span class="sxs-lookup"><span data-stu-id="aecc0-108">List</span></span>

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## <span data-ttu-id="aecc0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="aecc0-109">DESCRIPTION</span></span>

<span data-ttu-id="aecc0-110">`Get-EventLog`Cmdleten hämtar händelser och händelse loggar från lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="aecc0-110">The `Get-EventLog` cmdlet gets events and event logs from local and remote computers.</span></span> <span data-ttu-id="aecc0-111">Som standard `Get-EventLog` hämtar loggar från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-111">By default, `Get-EventLog` gets logs from the local computer.</span></span> <span data-ttu-id="aecc0-112">Använd parametern **computername** för att hämta loggar från fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="aecc0-112">To get logs from remote computers, use the **ComputerName** parameter.</span></span>

<span data-ttu-id="aecc0-113">Du kan använda `Get-EventLog` parameter-och egenskaps värden för att söka efter händelser.</span><span class="sxs-lookup"><span data-stu-id="aecc0-113">You can use the `Get-EventLog` parameters and property values to search for events.</span></span> <span data-ttu-id="aecc0-114">Cmdleten hämtar händelser som matchar angivna egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="aecc0-114">The cmdlet gets events that match the specified property values.</span></span>

<span data-ttu-id="aecc0-115">PowerShell-cmdletar som innehåller `EventLog` Substantiv fungerar endast på Windows klassiska händelse loggar som program, system eller säkerhet.</span><span class="sxs-lookup"><span data-stu-id="aecc0-115">PowerShell cmdlets that contain the `EventLog` noun work only on Windows classic event logs such as Application, System, or Security.</span></span> <span data-ttu-id="aecc0-116">Använd för att hämta loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows `Get-WinEvent` .</span><span class="sxs-lookup"><span data-stu-id="aecc0-116">To get logs that use the Windows Event Log technology in Windows Vista and later Windows versions, use `Get-WinEvent`.</span></span>

> [!NOTE]
> <span data-ttu-id="aecc0-117">`Get-EventLog` använder ett Win32-API som är föråldrat.</span><span class="sxs-lookup"><span data-stu-id="aecc0-117">`Get-EventLog` uses a Win32 API that is deprecated.</span></span> <span data-ttu-id="aecc0-118">Resultatet kanske inte stämmer.</span><span class="sxs-lookup"><span data-stu-id="aecc0-118">The results may not be accurate.</span></span> <span data-ttu-id="aecc0-119">Använd `Get-WinEvent` cmdleten i stället.</span><span class="sxs-lookup"><span data-stu-id="aecc0-119">Use the `Get-WinEvent` cmdlet instead.</span></span>

## <span data-ttu-id="aecc0-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="aecc0-120">EXAMPLES</span></span>

### <span data-ttu-id="aecc0-121">Exempel 1: Hämta händelse loggar på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="aecc0-121">Example 1: Get event logs on the local computer</span></span>

<span data-ttu-id="aecc0-122">I det här exemplet visas en lista över händelse loggar som är tillgängliga på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-122">This example displays the list of event logs that are available on the local computer.</span></span> <span data-ttu-id="aecc0-123">Namnen i kolumnen logg används med parametern **LogName** för att ange vilken logg som söks efter händelser.</span><span class="sxs-lookup"><span data-stu-id="aecc0-123">The names in the Log column are used with the **LogName** parameter to specify which log is searched for events.</span></span>

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

<span data-ttu-id="aecc0-124">`Get-EventLog`Cmdleten använder **list** parametern för att visa tillgängliga loggar.</span><span class="sxs-lookup"><span data-stu-id="aecc0-124">The `Get-EventLog` cmdlet uses the **List** parameter to display the available logs.</span></span>

### <span data-ttu-id="aecc0-125">Exempel 2: Hämta nya poster från en händelse logg på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="aecc0-125">Example 2: Get recent entries from an event log on the local computer</span></span>

<span data-ttu-id="aecc0-126">I det här exemplet hämtas de senaste posterna från system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-126">This example gets recent entries from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

<span data-ttu-id="aecc0-127">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-127">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="aecc0-128">Den **nyaste** parametern returnerar de fem senaste händelserna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-128">The **Newest** parameter returns the five most recent events.</span></span>

### <span data-ttu-id="aecc0-129">Exempel 3: Sök efter alla källor för ett angivet antal poster i en händelse logg</span><span class="sxs-lookup"><span data-stu-id="aecc0-129">Example 3: Find all sources for a specific number of entries in an event log</span></span>

<span data-ttu-id="aecc0-130">Det här exemplet visar hur du hittar alla källor som ingår i de 1000 senaste posterna i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-130">This example shows how to find all of the sources that are included in the 1000 most recent entries in the System event log.</span></span>

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

<span data-ttu-id="aecc0-131">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-131">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-132">Den **nyaste** parametern väljer de 1000 senaste händelserna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-132">The **Newest** parameter selects the 1000 most recent events.</span></span> <span data-ttu-id="aecc0-133">Händelse objekt lagras i `$Events` variabeln.</span><span class="sxs-lookup"><span data-stu-id="aecc0-133">The event objects are stored in the `$Events` variable.</span></span> <span data-ttu-id="aecc0-134">`$Events`Objekten skickas ned pipelinen till `Group-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-134">The `$Events` objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span>
<span data-ttu-id="aecc0-135">`Group-Object` använder **egenskaps** parametern för att gruppera objekten efter källa och räknar antalet objekt för varje källa.</span><span class="sxs-lookup"><span data-stu-id="aecc0-135">`Group-Object` uses the **Property** parameter to group the objects by source and counts the number of objects for each source.</span></span> <span data-ttu-id="aecc0-136">Parametern **noelement** tar bort grupp medlemmar från utdata.</span><span class="sxs-lookup"><span data-stu-id="aecc0-136">The **NoElement** parameter removes the group members from the output.</span></span>
<span data-ttu-id="aecc0-137">`Sort-Object`Cmdleten använder **egenskaps** parametern för att sortera efter antalet käll namn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-137">The `Sort-Object` cmdlet uses the **Property** parameter to sort by the count of each source name.</span></span>
<span data-ttu-id="aecc0-138">Parametern **fallande** sorterar listan i ordning efter antal från högst till lägsta.</span><span class="sxs-lookup"><span data-stu-id="aecc0-138">The **Descending** parameter sorts the list in order by count from highest to lowest.</span></span>

### <span data-ttu-id="aecc0-139">Exempel 4: Hämta fel händelser från en speciell händelse logg</span><span class="sxs-lookup"><span data-stu-id="aecc0-139">Example 4: Get error events from a specific event log</span></span>

<span data-ttu-id="aecc0-140">Det här exemplet hämtar fel händelser från system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-140">This example gets error events from the System event log.</span></span>

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

<span data-ttu-id="aecc0-141">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-141">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-142">Parametern **EntryType** filtrerar händelser så att endast fel händelser visas.</span><span class="sxs-lookup"><span data-stu-id="aecc0-142">The **EntryType** parameter filters the events to show only Error events.</span></span>

### <span data-ttu-id="aecc0-143">Exempel 5: Hämta händelser från en händelse logg med ett InstanceId-och käll värde</span><span class="sxs-lookup"><span data-stu-id="aecc0-143">Example 5: Get events from an event log with an InstanceId and Source value</span></span>

<span data-ttu-id="aecc0-144">I det här exemplet hämtas händelser från system loggen för ett särskilt InstanceId och en källa.</span><span class="sxs-lookup"><span data-stu-id="aecc0-144">This example gets events from the System log for a specific InstanceId and Source.</span></span>

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

<span data-ttu-id="aecc0-145">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-145">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-146">Parametern **InstanceID** väljer händelser med angivet instans-ID.</span><span class="sxs-lookup"><span data-stu-id="aecc0-146">The **InstanceID** parameter selects the events with the specified Instance ID.</span></span> <span data-ttu-id="aecc0-147">Parametern **Source** anger händelse egenskapen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-147">The **Source** parameter specifies the event property.</span></span>

### <span data-ttu-id="aecc0-148">Exempel 6: Hämta händelser från flera datorer</span><span class="sxs-lookup"><span data-stu-id="aecc0-148">Example 6: Get events from multiple computers</span></span>

<span data-ttu-id="aecc0-149">Det här kommandot hämtar händelserna från system händelse loggen på tre datorer: Server01, Server02 och Server03.</span><span class="sxs-lookup"><span data-stu-id="aecc0-149">This command gets the events from the System event log on three computers: Server01, Server02, and Server03.</span></span>

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="aecc0-150">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-150">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-151">Parametern **computername** använder en kommaavgränsad sträng för att visa en lista över de datorer som du vill hämta händelse loggarna från.</span><span class="sxs-lookup"><span data-stu-id="aecc0-151">The **ComputerName** parameter uses a comma-separated string to list the computers from which you want to get the event logs.</span></span>

### <span data-ttu-id="aecc0-152">Exempel 7: Hämta alla händelser som innehåller ett särskilt ord i meddelandet</span><span class="sxs-lookup"><span data-stu-id="aecc0-152">Example 7: Get all events that include a specific word in the message</span></span>

<span data-ttu-id="aecc0-153">Det här kommandot hämtar alla händelser i system händelse loggen som innehåller ett särskilt ord i händelsens meddelande.</span><span class="sxs-lookup"><span data-stu-id="aecc0-153">This command gets all the events in the System event log that contain a specific word in the event's message.</span></span> <span data-ttu-id="aecc0-154">Det är möjligt att den angivna **meddelande** parameterns värde ingår i meddelandets innehåll men inte visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-154">It's possible that your specified **Message** parameter's value is included in the message's content but isn't displayed on the PowerShell console.</span></span>

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

<span data-ttu-id="aecc0-155">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-155">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="aecc0-156">Parametern **Message** anger ett ord att söka efter i meddelande fältet för varje händelse.</span><span class="sxs-lookup"><span data-stu-id="aecc0-156">The **Message** parameter specifies a word to search for in the message field of each event.</span></span>

### <span data-ttu-id="aecc0-157">Exempel 8: Visa egenskaps värden för en händelse</span><span class="sxs-lookup"><span data-stu-id="aecc0-157">Example 8: Display the property values of an event</span></span>

<span data-ttu-id="aecc0-158">Det här exemplet visar hur du visar alla egenskaper och värden för en händelse.</span><span class="sxs-lookup"><span data-stu-id="aecc0-158">This example shows how to display all of an event's properties and values.</span></span>

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

<span data-ttu-id="aecc0-159">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-159">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System event log.</span></span> <span data-ttu-id="aecc0-160">Den **nyaste** parametern väljer det senaste händelse objekt.</span><span class="sxs-lookup"><span data-stu-id="aecc0-160">The **Newest** parameter selects the most recent event object.</span></span> <span data-ttu-id="aecc0-161">Objektet lagras i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="aecc0-161">The object is stored in the `$A` variable.</span></span> <span data-ttu-id="aecc0-162">Objektet i `$A` variabeln skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-162">The object in the `$A` variable is sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="aecc0-163">`Select-Object` använder **egenskaps** parametern med en asterisk ( `*` ) för att markera alla objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="aecc0-163">`Select-Object` uses the **Property** parameter with an asterisk (`*`) to select all of the object's properties.</span></span>

### <span data-ttu-id="aecc0-164">Exempel 9: Hämta händelser från en händelse logg med ett käll-och händelse-ID</span><span class="sxs-lookup"><span data-stu-id="aecc0-164">Example 9: Get events from an event log using a source and event ID</span></span>

<span data-ttu-id="aecc0-165">I det här exemplet hämtas händelser för ett angivet käll-och händelse-ID.</span><span class="sxs-lookup"><span data-stu-id="aecc0-165">This example gets events for a specified Source and Event ID.</span></span>

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

<span data-ttu-id="aecc0-166">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange program händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-166">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the Application event log.</span></span> <span data-ttu-id="aecc0-167">Parametern **Source** anger program namnet, Outlook.</span><span class="sxs-lookup"><span data-stu-id="aecc0-167">The **Source** parameter specifies the application name, Outlook.</span></span> <span data-ttu-id="aecc0-168">Objekten skickas ned pipelinen till `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-168">The objects are sent down the pipeline to the `Where-Object` cmdlet.</span></span> <span data-ttu-id="aecc0-169">För varje objekt i pipelinen `Where-Object` använder cmdleten variabeln `$_.EventID` för att jämföra händelse-ID-egenskapen med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="aecc0-169">For each object in the pipeline, the `Where-Object` cmdlet uses the variable `$_.EventID` to compare the Event ID property to the specified value.</span></span> <span data-ttu-id="aecc0-170">Objekten skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-170">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span> <span data-ttu-id="aecc0-171">`Select-Object` använder **egenskaps** parametern för att välja de egenskaper som ska visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-171">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="aecc0-172">Exempel 10: Hämta händelser och grupper efter en egenskap</span><span class="sxs-lookup"><span data-stu-id="aecc0-172">Example 10: Get events and group by a property</span></span>

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

<span data-ttu-id="aecc0-173">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-173">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-174">Parametern **username** innehåller jokertecknet asterisk ( `*` ) för att ange en del av användar namnet.</span><span class="sxs-lookup"><span data-stu-id="aecc0-174">The **UserName** parameter includes the asterisk (`*`) wildcard to specify a portion of the user name.</span></span> <span data-ttu-id="aecc0-175">Händelse objekten skickas ned pipelinen till `Group-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-175">The event objects are sent down the pipeline to the `Group-Object` cmdlet.</span></span> <span data-ttu-id="aecc0-176">`Group-Object` använder **egenskaps** parametern för att ange att egenskapen **username** används för att gruppera objekten och räknar antalet objekt för varje användar namn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-176">`Group-Object` uses the **Property** parameter to specify that the **UserName** property is used to group the objects and count the number of objects for each user name.</span></span> <span data-ttu-id="aecc0-177">Parametern **noelement** tar bort grupp medlemmar från utdata.</span><span class="sxs-lookup"><span data-stu-id="aecc0-177">The **NoElement** parameter removes the group members from the output.</span></span> <span data-ttu-id="aecc0-178">Objekten skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-178">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="aecc0-179">`Select-Object` använder **egenskaps** parametern för att välja de egenskaper som ska visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-179">`Select-Object` uses the **Property** parameter to select the properties to display in the PowerShell console.</span></span>

### <span data-ttu-id="aecc0-180">Exempel 11: Hämta händelser som inträffat under ett visst datum-och tidsintervall</span><span class="sxs-lookup"><span data-stu-id="aecc0-180">Example 11: Get events that occurred during a specific date and time range</span></span>

<span data-ttu-id="aecc0-181">Det här exemplet hämtar fel händelser från system händelse loggen för ett angivet datum-och tidsintervall.</span><span class="sxs-lookup"><span data-stu-id="aecc0-181">This example gets Error events from the System event log for a specified date and time range.</span></span> <span data-ttu-id="aecc0-182">Parametrarna **före** och **efter** anger datum-och tidsintervallet, men exkluderas från utdata.</span><span class="sxs-lookup"><span data-stu-id="aecc0-182">The **Before** and **After** parameters set the date and time range but are excluded from the output.</span></span>

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

<span data-ttu-id="aecc0-183">`Get-Date`Cmdleten använder parametern **date** för att ange ett datum och en tid.</span><span class="sxs-lookup"><span data-stu-id="aecc0-183">The `Get-Date` cmdlet uses the **Date** parameter to specify a date and time.</span></span> <span data-ttu-id="aecc0-184">**Datetime** -objekten lagras i `$Begin` `$End` variablerna och.</span><span class="sxs-lookup"><span data-stu-id="aecc0-184">The **DateTime** objects are stored in the `$Begin` and `$End` variables.</span></span> <span data-ttu-id="aecc0-185">`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-185">The `Get-EventLog` cmdlet uses the **LogName** parameter to specify the System log.</span></span> <span data-ttu-id="aecc0-186">Parametern **EntryType** anger fel händelse typ.</span><span class="sxs-lookup"><span data-stu-id="aecc0-186">The **EntryType** parameter specifies the Error event type.</span></span> <span data-ttu-id="aecc0-187">Datum-och tidsintervallet anges av **efter** -parametern och `$Begin` variabeln och **före** -parametern och `$End` variabeln.</span><span class="sxs-lookup"><span data-stu-id="aecc0-187">The date and time range is set by the **After** parameter and `$Begin` variable and the **Before** parameter and `$End` variable.</span></span>

## <span data-ttu-id="aecc0-188">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="aecc0-188">PARAMETERS</span></span>

### <span data-ttu-id="aecc0-189">– Efter</span><span class="sxs-lookup"><span data-stu-id="aecc0-189">-After</span></span>

<span data-ttu-id="aecc0-190">Hämtar händelser som inträffat efter ett angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="aecc0-190">Gets events that occurred after a specified date and time.</span></span> <span data-ttu-id="aecc0-191">Datum och tid för parametern **efter** tas inte med i utdata.</span><span class="sxs-lookup"><span data-stu-id="aecc0-191">The **After** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="aecc0-192">Ange ett **datetime** -objekt, till exempel det värde som returneras av `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-192">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-193">-AsBaseObject</span><span class="sxs-lookup"><span data-stu-id="aecc0-193">-AsBaseObject</span></span>

<span data-ttu-id="aecc0-194">Anger att denna cmdlet returnerar ett standard **system. Diagnostics. EventLogEntry** -objekt för varje händelse.</span><span class="sxs-lookup"><span data-stu-id="aecc0-194">Indicates that this cmdlet returns a standard **System.Diagnostics.EventLogEntry** object for each event.</span></span> <span data-ttu-id="aecc0-195">Utan den här parametern `Get-EventLog` returnerar ett utökat **PSObject** -objekt med ytterligare egenskaper för **EventLogName** , **Source** och **InstanceID** .</span><span class="sxs-lookup"><span data-stu-id="aecc0-195">Without this parameter, `Get-EventLog` returns an extended **PSObject** object with additional **EventLogName** , **Source** , and **InstanceId** properties.</span></span>

<span data-ttu-id="aecc0-196">Om du vill se resultatet av den här parametern kan du skicka vidare händelserna till cmdlet: en `Get-Member` och granska värdet **TypeName** i resultatet.</span><span class="sxs-lookup"><span data-stu-id="aecc0-196">To see the effect of this parameter, pipe the events to the `Get-Member` cmdlet and examine the **TypeName** value in the result.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-197">-Uppsträng</span><span class="sxs-lookup"><span data-stu-id="aecc0-197">-AsString</span></span>

<span data-ttu-id="aecc0-198">Anger att denna cmdlet returnerar utdata som strängar, i stället för objekt.</span><span class="sxs-lookup"><span data-stu-id="aecc0-198">Indicates that this cmdlet returns the output as strings, instead of objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-199">– Före</span><span class="sxs-lookup"><span data-stu-id="aecc0-199">-Before</span></span>

<span data-ttu-id="aecc0-200">Hämtar händelser som inträffat före ett angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="aecc0-200">Gets events that occurred before a specified date and time.</span></span> <span data-ttu-id="aecc0-201">**Innan** parameterns datum och tid undantas från utdata.</span><span class="sxs-lookup"><span data-stu-id="aecc0-201">The **Before** parameter date and time are excluded from the output.</span></span> <span data-ttu-id="aecc0-202">Ange ett **datetime** -objekt, till exempel det värde som returneras av `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aecc0-202">Enter a **DateTime** object, such as the value returned by the `Get-Date` cmdlet.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-203">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="aecc0-203">-ComputerName</span></span>

<span data-ttu-id="aecc0-204">Den här parametern anger en fjärrdators NetBIOS-namn, Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN).</span><span class="sxs-lookup"><span data-stu-id="aecc0-204">This parameter specifies a remote computer's NetBIOS name, Internet Protocol (IP) address, or a fully qualified domain name (FQDN).</span></span>

<span data-ttu-id="aecc0-205">Om parametern **computername** inte anges används `Get-EventLog` standardvärdet för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-205">If the **ComputerName** parameter isn't specified, `Get-EventLog` defaults to the local computer.</span></span> <span data-ttu-id="aecc0-206">Parametern accepterar också en punkt ( `.` ) för att ange den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-206">The parameter also accepts a dot (`.`) to specify the local computer.</span></span>

<span data-ttu-id="aecc0-207">Parametern **computername** är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="aecc0-207">The **ComputerName** parameter doesn't rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="aecc0-208">Du kan använda `Get-EventLog` med parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="aecc0-208">You can use `Get-EventLog` with the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-209">– EntryType</span><span class="sxs-lookup"><span data-stu-id="aecc0-209">-EntryType</span></span>

<span data-ttu-id="aecc0-210">Anger, som en sträng mat ris, post typen för de händelser som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="aecc0-210">Specifies, as a string array, the entry type of the events that this cmdlet gets.</span></span>

<span data-ttu-id="aecc0-211">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="aecc0-211">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="aecc0-212">Fel</span><span class="sxs-lookup"><span data-stu-id="aecc0-212">Error</span></span>
- <span data-ttu-id="aecc0-213">Information</span><span class="sxs-lookup"><span data-stu-id="aecc0-213">Information</span></span>
- <span data-ttu-id="aecc0-214">FailureAudit</span><span class="sxs-lookup"><span data-stu-id="aecc0-214">FailureAudit</span></span>
- <span data-ttu-id="aecc0-215">SuccessAudit</span><span class="sxs-lookup"><span data-stu-id="aecc0-215">SuccessAudit</span></span>
- <span data-ttu-id="aecc0-216">Varning</span><span class="sxs-lookup"><span data-stu-id="aecc0-216">Warning</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-217">-Index</span><span class="sxs-lookup"><span data-stu-id="aecc0-217">-Index</span></span>

<span data-ttu-id="aecc0-218">Anger de index värden som ska hämtas från händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-218">Specifies the index values to get from the event log.</span></span> <span data-ttu-id="aecc0-219">Parametern accepterar en kommaavgränsad sträng med värden.</span><span class="sxs-lookup"><span data-stu-id="aecc0-219">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-220">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="aecc0-220">-InstanceId</span></span>

<span data-ttu-id="aecc0-221">Anger de instans-ID: n som ska hämtas från händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="aecc0-221">Specifies the Instance IDs to get from the event log.</span></span> <span data-ttu-id="aecc0-222">Parametern accepterar en kommaavgränsad sträng med värden.</span><span class="sxs-lookup"><span data-stu-id="aecc0-222">The parameter accepts a comma-separated string of values.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-223">– Lista</span><span class="sxs-lookup"><span data-stu-id="aecc0-223">-List</span></span>

<span data-ttu-id="aecc0-224">Visar en lista över händelse loggar på datorn.</span><span class="sxs-lookup"><span data-stu-id="aecc0-224">Displays the list of event logs on the computer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-225">-LogName</span><span class="sxs-lookup"><span data-stu-id="aecc0-225">-LogName</span></span>

<span data-ttu-id="aecc0-226">Anger namnet på en händelse logg.</span><span class="sxs-lookup"><span data-stu-id="aecc0-226">Specifies the name of one event log.</span></span> <span data-ttu-id="aecc0-227">För att hitta de logg namn som ska användas `Get-EventLog -List` .</span><span class="sxs-lookup"><span data-stu-id="aecc0-227">To find the log names use `Get-EventLog -List`.</span></span> <span data-ttu-id="aecc0-228">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-228">Wildcard characters are permitted.</span></span> <span data-ttu-id="aecc0-229">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="aecc0-229">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aecc0-230">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="aecc0-230">-Message</span></span>

<span data-ttu-id="aecc0-231">Anger en sträng i händelse meddelandet.</span><span class="sxs-lookup"><span data-stu-id="aecc0-231">Specifies a string in the event message.</span></span> <span data-ttu-id="aecc0-232">Du kan använda den här parametern för att söka efter meddelanden som innehåller vissa ord eller fraser.</span><span class="sxs-lookup"><span data-stu-id="aecc0-232">You can use this parameter to search for messages that contain certain words or phrases.</span></span> <span data-ttu-id="aecc0-233">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-233">Wildcards are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aecc0-234">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="aecc0-234">-Newest</span></span>

<span data-ttu-id="aecc0-235">Börjar med de senaste händelserna och hämtar det angivna antalet händelser.</span><span class="sxs-lookup"><span data-stu-id="aecc0-235">Begins with the newest events and gets the specified number of events.</span></span> <span data-ttu-id="aecc0-236">Antalet händelser krävs, till exempel `-Newest 100` .</span><span class="sxs-lookup"><span data-stu-id="aecc0-236">The number of events is required, for example `-Newest 100`.</span></span> <span data-ttu-id="aecc0-237">Anger det maximala antalet händelser som returneras.</span><span class="sxs-lookup"><span data-stu-id="aecc0-237">Specifies the maximum number of events that are returned.</span></span>

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="aecc0-238">-Source</span><span class="sxs-lookup"><span data-stu-id="aecc0-238">-Source</span></span>

<span data-ttu-id="aecc0-239">Anger, som en sträng mat ris, källor som skrevs till loggen som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="aecc0-239">Specifies, as a string array, sources that were written to the log that this cmdlet gets.</span></span> <span data-ttu-id="aecc0-240">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-240">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aecc0-241">-UserName</span><span class="sxs-lookup"><span data-stu-id="aecc0-241">-UserName</span></span>

<span data-ttu-id="aecc0-242">Anger, som en sträng mat ris, användar namn som är associerade med händelser.</span><span class="sxs-lookup"><span data-stu-id="aecc0-242">Specifies, as a string array, user names that are associated with events.</span></span> <span data-ttu-id="aecc0-243">Ange namn eller namn mönster, till exempel `User01` , `User*` eller `Domain01\User*` .</span><span class="sxs-lookup"><span data-stu-id="aecc0-243">Enter names or name patterns, such as `User01`, `User*`, or `Domain01\User*`.</span></span> <span data-ttu-id="aecc0-244">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="aecc0-244">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="aecc0-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aecc0-245">CommonParameters</span></span>

<span data-ttu-id="aecc0-246">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aecc0-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aecc0-247">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="aecc0-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aecc0-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="aecc0-248">INPUTS</span></span>

### <span data-ttu-id="aecc0-249">Inget</span><span class="sxs-lookup"><span data-stu-id="aecc0-249">None</span></span>

<span data-ttu-id="aecc0-250">Du kan inte skicka pipe-ininformation till `Get-EventLog` .</span><span class="sxs-lookup"><span data-stu-id="aecc0-250">You cannot pipe input to `Get-EventLog`.</span></span>

## <span data-ttu-id="aecc0-251">UTDATA</span><span class="sxs-lookup"><span data-stu-id="aecc0-251">OUTPUTS</span></span>

### <span data-ttu-id="aecc0-252">System. Diagnostics. EventLogEntry.</span><span class="sxs-lookup"><span data-stu-id="aecc0-252">System.Diagnostics.EventLogEntry.</span></span> <span data-ttu-id="aecc0-253">System. Diagnostics. EventLog.</span><span class="sxs-lookup"><span data-stu-id="aecc0-253">System.Diagnostics.EventLog.</span></span> <span data-ttu-id="aecc0-254">System. String</span><span class="sxs-lookup"><span data-stu-id="aecc0-254">System.String</span></span>

<span data-ttu-id="aecc0-255">Om parametern **LogName** anges är utdata en samling **system. Diagnostics. EventLogEntry** -objekt.</span><span class="sxs-lookup"><span data-stu-id="aecc0-255">If the **LogName** parameter is specified, the output is a collection of **System.Diagnostics.EventLogEntry** objects.</span></span>

<span data-ttu-id="aecc0-256">Om endast **list** parametern anges är utdata en samling **system. Diagnostics. EventLog** -objekt.</span><span class="sxs-lookup"><span data-stu-id="aecc0-256">If only the **List** parameter is specified, the output is a collection of **System.Diagnostics.EventLog** objects.</span></span>

<span data-ttu-id="aecc0-257">Om både **listan** och dess **sträng** parametrar anges, är utdata en samling **system. String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="aecc0-257">If both the **List** and **AsString** parameters are specified, the output is a collection of **System.String** objects.</span></span>

## <span data-ttu-id="aecc0-258">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="aecc0-258">NOTES</span></span>

<span data-ttu-id="aecc0-259">Cmdlets `Get-EventLog` och `Get-WinEvent` stöds inte i Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="aecc0-259">The cmdlets `Get-EventLog` and `Get-WinEvent` are not supported in the Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="aecc0-260">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="aecc0-260">RELATED LINKS</span></span>

[<span data-ttu-id="aecc0-261">Rensa-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-261">Clear-EventLog</span></span>](Clear-EventLog.md)

[<span data-ttu-id="aecc0-262">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="aecc0-262">Get-WinEvent</span></span>](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[<span data-ttu-id="aecc0-263">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="aecc0-263">Group-Object</span></span>](../Microsoft.PowerShell.Utility/Group-Object.md)

[<span data-ttu-id="aecc0-264">Begränsning-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-264">Limit-EventLog</span></span>](Limit-EventLog.md)

[<span data-ttu-id="aecc0-265">Ny-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-265">New-EventLog</span></span>](New-EventLog.md)

[<span data-ttu-id="aecc0-266">Ta bort-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-266">Remove-EventLog</span></span>](Remove-EventLog.md)

[<span data-ttu-id="aecc0-267">Select-Object</span><span class="sxs-lookup"><span data-stu-id="aecc0-267">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="aecc0-268">Visa-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-268">Show-EventLog</span></span>](Show-EventLog.md)

[<span data-ttu-id="aecc0-269">Skriv-EventLog</span><span class="sxs-lookup"><span data-stu-id="aecc0-269">Write-EventLog</span></span>](Write-EventLog.md)
