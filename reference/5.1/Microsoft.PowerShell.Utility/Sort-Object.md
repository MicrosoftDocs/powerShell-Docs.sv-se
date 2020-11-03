---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 1d27641f94d82b85bab694b392c0f09bb3265517
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93268964"
---
# <span data-ttu-id="a0014-103">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="a0014-103">Sort-Object</span></span>

## <span data-ttu-id="a0014-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a0014-104">SYNOPSIS</span></span>
<span data-ttu-id="a0014-105">Sorterar objekt efter egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a0014-105">Sorts objects by property values.</span></span>

## <span data-ttu-id="a0014-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a0014-106">SYNTAX</span></span>

### <span data-ttu-id="a0014-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="a0014-107">Default (Default)</span></span>

```
Sort-Object [[-Property] <Object[]>] [-Descending] [-Unique] [-InputObject <psobject>]
 [-Culture <string>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="a0014-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a0014-108">DESCRIPTION</span></span>

<span data-ttu-id="a0014-109">`Sort-Object`Cmdlet sorterar objekt i stigande eller fallande ordning baserat på objekt egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a0014-109">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="a0014-110">Om sorterings egenskaper inte ingår i ett kommando använder PowerShell standard sorterings egenskaper för det första objektet.</span><span class="sxs-lookup"><span data-stu-id="a0014-110">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="a0014-111">Om typen av inobjektet inte har några standard sorterings egenskaper försöker PowerShell att jämföra själva objekten.</span><span class="sxs-lookup"><span data-stu-id="a0014-111">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="a0014-112">Mer information finns i avsnittet om [anteckningar](#notes) .</span><span class="sxs-lookup"><span data-stu-id="a0014-112">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="a0014-113">Du kan sortera objekt efter en enskild egenskap eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a0014-113">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="a0014-114">Flera egenskaper använder hash-tabeller för att sortera i stigande ordning, fallande ordning eller en kombination av sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-114">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="a0014-115">Egenskaperna sorteras som Skift läges känsliga eller Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a0014-115">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="a0014-116">Använd den **unika** parametern för att eliminera dubbletter från utdata.</span><span class="sxs-lookup"><span data-stu-id="a0014-116">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="a0014-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a0014-117">EXAMPLES</span></span>

### <span data-ttu-id="a0014-118">Exempel 1: sortera den aktuella katalogen efter namn</span><span class="sxs-lookup"><span data-stu-id="a0014-118">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="a0014-119">Det här kommandot sorterar filer och under kataloger i en katalog.</span><span class="sxs-lookup"><span data-stu-id="a0014-119">This command sorts the files and subdirectories in a directory.</span></span>

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

<span data-ttu-id="a0014-120">Cmdlet: en `Get-ChildItem` hämtar filer och under kataloger från katalogen som anges av **Sök vägs** parametern, **C:\test**.</span><span class="sxs-lookup"><span data-stu-id="a0014-120">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test**.</span></span> <span data-ttu-id="a0014-121">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-121">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="a0014-122">`Sort-Object` anger ingen egenskap så utdata sorteras efter standard sorterings egenskap, **namn**.</span><span class="sxs-lookup"><span data-stu-id="a0014-122">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name**.</span></span>

### <span data-ttu-id="a0014-123">Exempel 2: sortera den aktuella katalogen efter fil längd</span><span class="sxs-lookup"><span data-stu-id="a0014-123">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="a0014-124">Det här kommandot visar filerna i den aktuella katalogen efter längd i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-124">This command displays the files in the current directory by length in ascending order.</span></span>

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

<span data-ttu-id="a0014-125">`Get-ChildItem`Cmdlet: en hämtar filerna från katalogen som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a0014-125">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="a0014-126">Parametern **File** anger att `Get-ChildItem` endast fil objekt ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="a0014-126">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="a0014-127">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-127">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-128">`Sort-Object` använder parametern **length** för att sortera filerna efter längd i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-128">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="a0014-129">Exempel 3: sortera processer efter minnes användning</span><span class="sxs-lookup"><span data-stu-id="a0014-129">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="a0014-130">I det här exemplet visas processer med högsta minnes användning baserat på storleken på deras arbets minne (WS).</span><span class="sxs-lookup"><span data-stu-id="a0014-130">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

<span data-ttu-id="a0014-131">`Get-Process`Cmdleten hämtar listan över processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="a0014-131">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="a0014-132">Process objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-132">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-133">`Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **WS**.</span><span class="sxs-lookup"><span data-stu-id="a0014-133">`Sort-Object` uses the **Property** parameter to sort the objects by **WS**.</span></span> <span data-ttu-id="a0014-134">Objekten skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-134">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="a0014-135">`Select-Object` använder den **sista** parametern för att ange de sista fem objekten, som är de objekt som har högst **WS** -användning.</span><span class="sxs-lookup"><span data-stu-id="a0014-135">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

### <span data-ttu-id="a0014-136">Exempel 4: sortera HistoryInfo-objekt efter ID</span><span class="sxs-lookup"><span data-stu-id="a0014-136">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="a0014-137">Det här kommandot sorterar PowerShell-sessionens **HistoryInfo** -objekt med egenskapen **ID** .</span><span class="sxs-lookup"><span data-stu-id="a0014-137">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="a0014-138">Varje PowerShell-session har en egen kommando historik.</span><span class="sxs-lookup"><span data-stu-id="a0014-138">Each PowerShell session has its own command history.</span></span>

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

<span data-ttu-id="a0014-139">`Get-History`Cmdlet: en hämtar historik objekt från den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a0014-139">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="a0014-140">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-140">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-141">`Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **ID**. Den **fallande** parametern sorterar kommando historiken från nyaste till äldsta.</span><span class="sxs-lookup"><span data-stu-id="a0014-141">`Sort-Object` uses the **Property** parameter to sort the objects by **Id**. The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="a0014-142">Exempel 5: Använd en hash-tabell för att sortera egenskaper i stigande och fallande ordning</span><span class="sxs-lookup"><span data-stu-id="a0014-142">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="a0014-143">Det här kommandot använder två egenskaper för att sortera objekt, **status** och **DisplayName**.</span><span class="sxs-lookup"><span data-stu-id="a0014-143">This command uses two properties to sort the objects, **Status** and **DisplayName**.</span></span> <span data-ttu-id="a0014-144">**Status** sorteras i fallande ordning och **DisplayName** sorteras i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-144">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="a0014-145">En hash-tabell används för att ange **egenskaps** parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="a0014-145">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="a0014-146">Hash-tabellen använder ett uttryck för att ange egenskaps namn och sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-146">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="a0014-147">Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="a0014-147">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="a0014-148">**Status** egenskapen som används i hash-tabellen är en uppräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="a0014-148">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="a0014-149">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="a0014-149">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

<span data-ttu-id="a0014-150">`Get-Service`Cmdlet: en hämtar listan över tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="a0014-150">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="a0014-151">Tjänst objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-151">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-152">`Sort-Object` använder **egenskaps** parametern med en hash-tabell för att ange egenskaps namn och sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-152">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="a0014-153">**Egenskaps** parametern sorteras efter två egenskaper, **status** i fallande ordning och **DisplayName** i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-153">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="a0014-154">**Status** är en uppräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="a0014-154">**Status** is an enumerated property.</span></span> <span data-ttu-id="a0014-155">**Stoppad** har värdet **1** och **körs** har värdet **4**.</span><span class="sxs-lookup"><span data-stu-id="a0014-155">**Stopped** has a value of **1** and **Running** has a value of **4**.</span></span> <span data-ttu-id="a0014-156">Den **fallande** parametern anges till `$True` så att processer som **körs** visas innan **stoppade** processer.</span><span class="sxs-lookup"><span data-stu-id="a0014-156">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="a0014-157">**DisplayName** anger **fallande** parameter för `$False` att sortera visnings namnen i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-157">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="a0014-158">Exempel 6: sortera textfiler efter tids period</span><span class="sxs-lookup"><span data-stu-id="a0014-158">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="a0014-159">Det här kommandot sorterar textfiler i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="a0014-159">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt

```

<span data-ttu-id="a0014-160">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen **C:\test** och alla `*.txt` filer.</span><span class="sxs-lookup"><span data-stu-id="a0014-160">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="a0014-161">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-161">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="a0014-162">`Sort-Object` använder **egenskaps** parametern med en hash-tabell för att avgöra varje fil intervall mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="a0014-162">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime**.</span></span> <span data-ttu-id="a0014-163">Parametern **fallande** är inställd på `$False` att sortera i ordningen längst till kortast tids period.</span><span class="sxs-lookup"><span data-stu-id="a0014-163">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="a0014-164">Exempel 7: Sortera namn i en textfil</span><span class="sxs-lookup"><span data-stu-id="a0014-164">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="a0014-165">Det här exemplet visar hur du sorterar en lista från en textfil.</span><span class="sxs-lookup"><span data-stu-id="a0014-165">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="a0014-166">Den ursprungliga filen visas som en osorterad lista.</span><span class="sxs-lookup"><span data-stu-id="a0014-166">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="a0014-167">`Sort-Object` sorterar innehållet och sorterar innehållet med den **unika** parameter som tar bort dubbletter.</span><span class="sxs-lookup"><span data-stu-id="a0014-167">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

<span data-ttu-id="a0014-168">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-168">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="a0014-169">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-169">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="a0014-170">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-170">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="a0014-171">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-171">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="a0014-172">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-172">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-173">`Sort-Object` sorterar listan i standard ordningen, stigande.</span><span class="sxs-lookup"><span data-stu-id="a0014-173">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="a0014-174">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-174">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="a0014-175">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-175">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="a0014-176">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-176">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-177">`Sort-Object` använder den **unika** parametern för att ta bort dubbla dator namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-177">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="a0014-178">Listan sorteras i standard ordningen, stigande.</span><span class="sxs-lookup"><span data-stu-id="a0014-178">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="a0014-179">Exempel 8: sortera en sträng som ett heltal</span><span class="sxs-lookup"><span data-stu-id="a0014-179">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="a0014-180">Det här exemplet visar hur du sorterar en textfil som innehåller sträng objekt som heltal.</span><span class="sxs-lookup"><span data-stu-id="a0014-180">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="a0014-181">Du kan skicka varje kommando nedåt i pipeline till `Get-Member` och kontrol lera att objekten är strängar i stället för heltal.</span><span class="sxs-lookup"><span data-stu-id="a0014-181">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="a0014-182">I de här exemplen `ProductId.txt` innehåller filen en osorterad lista med produkt nummer.</span><span class="sxs-lookup"><span data-stu-id="a0014-182">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="a0014-183">I det första exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-183">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-184">`Sort-Object` sorterar sträng objekt i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-184">`Sort-Object` sorts the string objects in ascending order.</span></span>

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

<span data-ttu-id="a0014-185">I det andra exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-185">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-186">`Sort-Object` använder ett-skript block för att konvertera strängarna till heltal.</span><span class="sxs-lookup"><span data-stu-id="a0014-186">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="a0014-187">I exempel koden `[int]` konverterar strängen till ett heltal och `$_` representerar varje sträng som den kommer nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a0014-187">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="a0014-188">Heltals objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-188">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="a0014-189">`Sort-Object` sorterar heltals objekt i numerisk ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-189">`Sort-Object` sorts the integer objects in numeric order.</span></span>

<span data-ttu-id="a0014-190">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="a0014-190">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="a0014-191">Filen **ProductId.txt** innehåller en osorterad lista med produkt nummer.</span><span class="sxs-lookup"><span data-stu-id="a0014-191">The file **ProductId.txt** contains an unsorted list of product numbers.</span></span> <span data-ttu-id="a0014-192">String-objekten skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-192">The string objects are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="a0014-193">`ForEach-Object` använder ett-skript block för att konvertera strängarna till heltal.</span><span class="sxs-lookup"><span data-stu-id="a0014-193">`ForEach-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="a0014-194">I exempel koden `[int]` konverterar strängen till ett heltal och `$_` representerar varje sträng som den kommer nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a0014-194">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="a0014-195">Heltals objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a0014-195">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="a0014-196">`Sort-Object` sorterar heltals objekt i numerisk ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-196">`Sort-Object` sorts the integer objects in numeric order.</span></span>
## <span data-ttu-id="a0014-197">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a0014-197">PARAMETERS</span></span>

### <span data-ttu-id="a0014-198">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="a0014-198">-CaseSensitive</span></span>

<span data-ttu-id="a0014-199">Anger att sorteringen är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="a0014-199">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="a0014-200">Som standard är sorteringar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a0014-200">By default, sorts are not case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0014-201">– Kultur</span><span class="sxs-lookup"><span data-stu-id="a0014-201">-Culture</span></span>

<span data-ttu-id="a0014-202">Anger den kulturella konfiguration som ska användas för sortering.</span><span class="sxs-lookup"><span data-stu-id="a0014-202">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="a0014-203">Används `Get-Culture` för att Visa systemets kultur konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a0014-203">Use `Get-Culture` to display the system's culture configuration.</span></span>

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

### <span data-ttu-id="a0014-204">-Fallande</span><span class="sxs-lookup"><span data-stu-id="a0014-204">-Descending</span></span>

<span data-ttu-id="a0014-205">Anger att `Sort-Object` objekten sorteras i fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-205">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="a0014-206">Standardvärdet är stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-206">The default is ascending order.</span></span>

<span data-ttu-id="a0014-207">Om du vill sortera flera egenskaper med olika sorterings ordning använder du en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="a0014-207">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="a0014-208">Med en hash-tabell kan du till exempel sortera en egenskap i stigande ordning och en annan egenskap i fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="a0014-208">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0014-209">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a0014-209">-InputObject</span></span>

<span data-ttu-id="a0014-210">Om du vill sortera objekt kan du skicka dem nedåt i pipeline till `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="a0014-210">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="a0014-211">Om du använder parametern **InputObject** för att skicka en samling objekt, `Sort-Object` tar emot ett objekt som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="a0014-211">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="a0014-212">Eftersom ett objekt inte kan sorteras, `Sort-Object` returnerar hela samlingen oförändrad.</span><span class="sxs-lookup"><span data-stu-id="a0014-212">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

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

### <span data-ttu-id="a0014-213">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="a0014-213">-Property</span></span>

<span data-ttu-id="a0014-214">Anger de egenskaps namn som `Sort-Object` används för att sortera objekten.</span><span class="sxs-lookup"><span data-stu-id="a0014-214">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="a0014-215">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a0014-215">Wildcards are permitted.</span></span>
<span data-ttu-id="a0014-216">Objekten sorteras baserat på egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a0014-216">Objects are sorted based on the property values.</span></span> <span data-ttu-id="a0014-217">Om du inte anger någon egenskap, `Sort-Object` sorteras baserat på standard egenskaper för objekt typen eller själva objekten.</span><span class="sxs-lookup"><span data-stu-id="a0014-217">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="a0014-218">Flera egenskaper kan sorteras i stigande ordning, fallande ordning eller en kombination av sorterings ordningar.</span><span class="sxs-lookup"><span data-stu-id="a0014-218">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="a0014-219">När du anger flera egenskaper sorteras objekten efter den första egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a0014-219">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="a0014-220">Om flera objekt har samma värde för den första egenskapen, sorteras dessa objekt efter den andra egenskapen.</span><span class="sxs-lookup"><span data-stu-id="a0014-220">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="a0014-221">Den här processen fortsätter tills det inte finns några fler angivna egenskaper eller inga grupper av objekt.</span><span class="sxs-lookup"><span data-stu-id="a0014-221">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="a0014-222">**Egenskaps** parameterns värde kan vara en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="a0014-222">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="a0014-223">Använd en hash-tabell om du vill skapa en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="a0014-223">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="a0014-224">Giltiga nycklar för en hash-tabell är följande:</span><span class="sxs-lookup"><span data-stu-id="a0014-224">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="a0014-225">`expression` - `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="a0014-225">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="a0014-226">`ascending` eller `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="a0014-226">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="a0014-227">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="a0014-227">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="a0014-228">– Unik</span><span class="sxs-lookup"><span data-stu-id="a0014-228">-Unique</span></span>

<span data-ttu-id="a0014-229">Anger att `Sort-Object` tar bort dubbletter och returnerar bara de unika medlemmarna i samlingen.</span><span class="sxs-lookup"><span data-stu-id="a0014-229">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="a0014-230">Den första instansen av ett unikt värde ingår i de sorterade utdata.</span><span class="sxs-lookup"><span data-stu-id="a0014-230">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="a0014-231">**Unique** är Skift läges okänsligt.</span><span class="sxs-lookup"><span data-stu-id="a0014-231">**Unique** is case-insensitive.</span></span> <span data-ttu-id="a0014-232">Strängar som endast skiljer sig från versaler anses vara identiska.</span><span class="sxs-lookup"><span data-stu-id="a0014-232">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="a0014-233">Till exempel, Character och CHARACTER.</span><span class="sxs-lookup"><span data-stu-id="a0014-233">For example, character and CHARACTER.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a0014-234">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a0014-234">CommonParameters</span></span>

<span data-ttu-id="a0014-235">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a0014-235">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a0014-236">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a0014-236">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a0014-237">INDATA</span><span class="sxs-lookup"><span data-stu-id="a0014-237">INPUTS</span></span>

### <span data-ttu-id="a0014-238">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a0014-238">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a0014-239">Du kan skicka vidare de objekt som ska sorteras till `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="a0014-239">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="a0014-240">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a0014-240">OUTPUTS</span></span>

### <span data-ttu-id="a0014-241">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="a0014-241">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="a0014-242">`Sort-Object` Returnerar de sorterade objekten.</span><span class="sxs-lookup"><span data-stu-id="a0014-242">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="a0014-243">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a0014-243">NOTES</span></span>

<span data-ttu-id="a0014-244">`Sort-Object`Cmdlet sorterar objekt baserat på egenskaper som anges i kommandot eller standard sorterings egenskaperna för objekt typen.</span><span class="sxs-lookup"><span data-stu-id="a0014-244">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="a0014-245">Standard sorterings egenskaper definieras med hjälp av `PropertySet` namnet `DefaultKeyPropertySet` i en `types.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="a0014-245">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="a0014-246">Mer information finns i [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="a0014-246">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="a0014-247">Om ett objekt inte har någon av de angivna egenskaperna tolkas egenskap svärdet för objektet med `Sort-Object` **Null** och placeras i slutet av sorterings ordningen.</span><span class="sxs-lookup"><span data-stu-id="a0014-247">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="a0014-248">När inga sorterings egenskaper är tillgängliga försöker PowerShell att jämföra själva objekten.</span><span class="sxs-lookup"><span data-stu-id="a0014-248">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="a0014-249">`Sort-Object` använder metoden **compare** för varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="a0014-249">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="a0014-250">Om en egenskap inte implementerar **IComparable** , konverterar cmdleten egenskap svärdet till en sträng och använder metoden **compare** för **system. String**.</span><span class="sxs-lookup"><span data-stu-id="a0014-250">If a property does not implement **IComparable** , the cmdlet converts the property value to a string and uses the **Compare** method for **System.String**.</span></span> <span data-ttu-id="a0014-251">Mer information finns i [metoden PSObject. CompareTo (Object)](/dotnet/api/system.management.automation.psobject.compareto).</span><span class="sxs-lookup"><span data-stu-id="a0014-251">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="a0014-252">Om du sorterar efter en uppräknad egenskap, till exempel **status** , `Sort-Object` sorteras efter uppräknings värden.</span><span class="sxs-lookup"><span data-stu-id="a0014-252">If you sort on an enumerated property such as **Status** , `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="a0014-253">För Windows-tjänster har **stoppat** värdet **1** och **körs** har värdet **4**.</span><span class="sxs-lookup"><span data-stu-id="a0014-253">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4**.</span></span>
<span data-ttu-id="a0014-254">**Stoppad** sorteras före **körning** på grund av uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="a0014-254">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="a0014-255">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="a0014-255">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

## <span data-ttu-id="a0014-256">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a0014-256">RELATED LINKS</span></span>

[<span data-ttu-id="a0014-257">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="a0014-257">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="a0014-258">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a0014-258">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="a0014-259">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="a0014-259">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="a0014-260">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-260">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="a0014-261">-Objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-261">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="a0014-262">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-262">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="a0014-263">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-263">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="a0014-264">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-264">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="a0014-265">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a0014-265">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="a0014-266">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="a0014-266">Tee-Object</span></span>](Tee-Object.md)
