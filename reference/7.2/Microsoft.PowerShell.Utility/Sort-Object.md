---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: fead3b3d109a79186bc82f3c9f212f11f7b0bc57
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709739"
---
# <span data-ttu-id="2c12e-102">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="2c12e-102">Sort-Object</span></span>

## <span data-ttu-id="2c12e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2c12e-103">SYNOPSIS</span></span>
<span data-ttu-id="2c12e-104">Sorterar objekt efter egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="2c12e-104">Sorts objects by property values.</span></span>

## <span data-ttu-id="2c12e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2c12e-105">SYNTAX</span></span>

### <span data-ttu-id="2c12e-106">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="2c12e-106">Default (Default)</span></span>

```
Sort-Object [-Stable] [-Descending] [-Unique] [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="2c12e-107">Överkant</span><span class="sxs-lookup"><span data-stu-id="2c12e-107">Top</span></span>

```
Sort-Object [-Descending] [-Unique] -Top <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

### <span data-ttu-id="2c12e-108">Nedre</span><span class="sxs-lookup"><span data-stu-id="2c12e-108">Bottom</span></span>

```
Sort-Object [-Descending] [-Unique] -Bottom <Int32> [-InputObject <PSObject>] [[-Property] <Object[]>]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="2c12e-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2c12e-109">DESCRIPTION</span></span>

<span data-ttu-id="2c12e-110">`Sort-Object`Cmdlet sorterar objekt i stigande eller fallande ordning baserat på objekt egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="2c12e-110">The `Sort-Object` cmdlet sorts objects in ascending or descending order based on object property values.</span></span> <span data-ttu-id="2c12e-111">Om sorterings egenskaper inte ingår i ett kommando använder PowerShell standard sorterings egenskaper för det första objektet.</span><span class="sxs-lookup"><span data-stu-id="2c12e-111">If sort properties are not included in a command, PowerShell uses default sort properties of the first input object.</span></span> <span data-ttu-id="2c12e-112">Om typen av inobjektet inte har några standard sorterings egenskaper försöker PowerShell att jämföra själva objekten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-112">If the type of the input object has no default sort properties, PowerShell attempts to compare the objects themselves.</span></span> <span data-ttu-id="2c12e-113">Mer information finns i avsnittet om [anteckningar](#notes) .</span><span class="sxs-lookup"><span data-stu-id="2c12e-113">For more information, see the [Notes](#notes) section.</span></span>

<span data-ttu-id="2c12e-114">Du kan sortera objekt efter en enskild egenskap eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2c12e-114">You can sort objects by a single property or multiple properties.</span></span> <span data-ttu-id="2c12e-115">Flera egenskaper använder hash-tabeller för att sortera i stigande ordning, fallande ordning eller en kombination av sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-115">Multiple properties use hash tables to sort in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="2c12e-116">Egenskaperna sorteras som Skift läges känsliga eller Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="2c12e-116">Properties are sorted as case-sensitive or case-insensitive.</span></span> <span data-ttu-id="2c12e-117">Använd den **unika** parametern för att eliminera dubbletter från utdata.</span><span class="sxs-lookup"><span data-stu-id="2c12e-117">Use the **Unique** parameter to eliminate duplicates from the output.</span></span>

## <span data-ttu-id="2c12e-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2c12e-118">EXAMPLES</span></span>

### <span data-ttu-id="2c12e-119">Exempel 1: sortera den aktuella katalogen efter namn</span><span class="sxs-lookup"><span data-stu-id="2c12e-119">Example 1: Sort the current directory by name</span></span>

<span data-ttu-id="2c12e-120">I det här exemplet sorteras filer och under kataloger i en katalog.</span><span class="sxs-lookup"><span data-stu-id="2c12e-120">This example sorts the files and subdirectories in a directory.</span></span>

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

<span data-ttu-id="2c12e-121">Cmdlet: en `Get-ChildItem` hämtar filer och under kataloger från katalogen som anges av **Sök vägs** parametern, **C:\test**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-121">The `Get-ChildItem` cmdlet gets the files and subdirectories from the directory specified by the **Path** parameter, **C:\Test**.</span></span> <span data-ttu-id="2c12e-122">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-122">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="2c12e-123">`Sort-Object` anger ingen egenskap så utdata sorteras efter standard sorterings egenskap, **namn**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-123">`Sort-Object` does not specify a property so the output is sorted by the default sort property, **Name**.</span></span>

### <span data-ttu-id="2c12e-124">Exempel 2: sortera den aktuella katalogen efter fil längd</span><span class="sxs-lookup"><span data-stu-id="2c12e-124">Example 2: Sort the current directory by file length</span></span>

<span data-ttu-id="2c12e-125">Det här kommandot visar filerna i den aktuella katalogen efter längd i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-125">This command displays the files in the current directory by length in ascending order.</span></span>

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

<span data-ttu-id="2c12e-126">`Get-ChildItem`Cmdlet: en hämtar filerna från katalogen som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2c12e-126">The `Get-ChildItem` cmdlet gets the files from the directory specified by the **Path** parameter.</span></span>
<span data-ttu-id="2c12e-127">Parametern **File** anger att `Get-ChildItem` endast fil objekt ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="2c12e-127">The **File** parameter specifies that `Get-ChildItem` only gets file objects.</span></span> <span data-ttu-id="2c12e-128">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-128">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-129">`Sort-Object` använder parametern **length** för att sortera filerna efter längd i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-129">`Sort-Object` uses the **Length** parameter to sort the files by length in ascending order.</span></span>

### <span data-ttu-id="2c12e-130">Exempel 3: sortera processer efter minnes användning</span><span class="sxs-lookup"><span data-stu-id="2c12e-130">Example 3: Sort processes by memory usage</span></span>

<span data-ttu-id="2c12e-131">I det här exemplet visas processer med högsta minnes användning baserat på storleken på deras arbets minne (WS).</span><span class="sxs-lookup"><span data-stu-id="2c12e-131">This example displays processes with the highest memory usage based on their working set (WS) size.</span></span>

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

<span data-ttu-id="2c12e-132">`Get-Process`Cmdleten hämtar listan över processer som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-132">The `Get-Process` cmdlet gets the list of processes running on the computer.</span></span> <span data-ttu-id="2c12e-133">Process objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-133">The process objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-134">`Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **WS**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-134">`Sort-Object` uses the **Property** parameter to sort the objects by **WS**.</span></span> <span data-ttu-id="2c12e-135">Objekten skickas ned pipelinen till `Select-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-135">The objects are sent down the pipeline to the `Select-Object` cmdlet.</span></span>
<span data-ttu-id="2c12e-136">`Select-Object` använder den **sista** parametern för att ange de sista fem objekten, som är de objekt som har högst **WS** -användning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-136">`Select-Object` uses the **Last** parameter to specify the last five objects, which are the objects with the highest **WS** usage.</span></span>

<span data-ttu-id="2c12e-137">I PowerShell 6 `Sort-Object` är parametern **längst ned** ett alternativ till `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2c12e-137">In PowerShell 6, the `Sort-Object` parameter **Bottom** is an alternative to `Select-Object`.</span></span> <span data-ttu-id="2c12e-138">Ett exempel är `Get-Process | Sort-Object -Property WS -Bottom 5`.</span><span class="sxs-lookup"><span data-stu-id="2c12e-138">For example, `Get-Process | Sort-Object -Property WS -Bottom 5`.</span></span>

### <span data-ttu-id="2c12e-139">Exempel 4: sortera HistoryInfo-objekt efter ID</span><span class="sxs-lookup"><span data-stu-id="2c12e-139">Example 4: Sort HistoryInfo objects by Id</span></span>

<span data-ttu-id="2c12e-140">Det här kommandot sorterar PowerShell-sessionens **HistoryInfo** -objekt med egenskapen **ID** .</span><span class="sxs-lookup"><span data-stu-id="2c12e-140">This command sorts the PowerShell session's **HistoryInfo** objects using the **Id** property.</span></span> <span data-ttu-id="2c12e-141">Varje PowerShell-session har en egen kommando historik.</span><span class="sxs-lookup"><span data-stu-id="2c12e-141">Each PowerShell session has its own command history.</span></span>

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

<span data-ttu-id="2c12e-142">`Get-History`Cmdlet: en hämtar historik objekt från den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-142">The `Get-History` cmdlet gets the history objects from the current PowerShell session.</span></span> <span data-ttu-id="2c12e-143">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-143">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-144">`Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **ID**. Den **fallande** parametern sorterar kommando historiken från nyaste till äldsta.</span><span class="sxs-lookup"><span data-stu-id="2c12e-144">`Sort-Object` uses the **Property** parameter to sort the objects by **Id**. The **Descending** parameter sorts the command history from newest to oldest.</span></span>

### <span data-ttu-id="2c12e-145">Exempel 5: Använd en hash-tabell för att sortera egenskaper i stigande och fallande ordning</span><span class="sxs-lookup"><span data-stu-id="2c12e-145">Example 5: Use a hash table to sort properties in ascending and descending order</span></span>

<span data-ttu-id="2c12e-146">I det här exemplet används två egenskaper för att sortera objekt, **status** och **DisplayName**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-146">This example uses two properties to sort the objects, **Status** and **DisplayName**.</span></span> <span data-ttu-id="2c12e-147">**Status** sorteras i fallande ordning och **DisplayName** sorteras i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-147">**Status** is sorted in descending order and **DisplayName** is sorted in ascending order.</span></span>

<span data-ttu-id="2c12e-148">En hash-tabell används för att ange **egenskaps** parameterns värde.</span><span class="sxs-lookup"><span data-stu-id="2c12e-148">A hash table is used to specify the **Property** parameter's value.</span></span> <span data-ttu-id="2c12e-149">Hash-tabellen använder ett uttryck för att ange egenskaps namn och sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-149">The hash table uses an expression to specify the property names and sort orders.</span></span> <span data-ttu-id="2c12e-150">Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span><span class="sxs-lookup"><span data-stu-id="2c12e-150">For more information about hash tables, see [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).</span></span>

<span data-ttu-id="2c12e-151">**Status** egenskapen som används i hash-tabellen är en uppräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2c12e-151">The **Status** property used in the hash table is an enumerated property.</span></span>
<span data-ttu-id="2c12e-152">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="2c12e-152">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

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

<span data-ttu-id="2c12e-153">`Get-Service`Cmdlet: en hämtar listan över tjänster på datorn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-153">The `Get-Service` cmdlet gets the list of services on the computer.</span></span> <span data-ttu-id="2c12e-154">Tjänst objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-154">The service objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-155">`Sort-Object` använder **egenskaps** parametern med en hash-tabell för att ange egenskaps namn och sorterings ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-155">`Sort-Object` uses the **Property** parameter with a hash table to specify the property names and sort orders.</span></span> <span data-ttu-id="2c12e-156">**Egenskaps** parametern sorteras efter två egenskaper, **status** i fallande ordning och **DisplayName** i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-156">The **Property** parameter is sorted by two properties, **Status** in descending order and **DisplayName** in ascending order.</span></span>

<span data-ttu-id="2c12e-157">**Status** är en uppräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2c12e-157">**Status** is an enumerated property.</span></span> <span data-ttu-id="2c12e-158">**Stoppad** har värdet **1** och **körs** har värdet **4**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-158">**Stopped** has a value of **1** and **Running** has a value of **4**.</span></span> <span data-ttu-id="2c12e-159">Den **fallande** parametern anges till `$True` så att processer som **körs** visas innan **stoppade** processer.</span><span class="sxs-lookup"><span data-stu-id="2c12e-159">The **Descending** parameter is set to `$True` so that **Running** processes are displayed before **Stopped** processes.</span></span> <span data-ttu-id="2c12e-160">**DisplayName** anger **fallande** parameter för `$False` att sortera visnings namnen i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-160">**DisplayName** sets the **Descending** parameter to `$False` to sort the display names in alphabetical order.</span></span>

### <span data-ttu-id="2c12e-161">Exempel 6: sortera textfiler efter tids period</span><span class="sxs-lookup"><span data-stu-id="2c12e-161">Example 6: Sort text files by time span</span></span>

<span data-ttu-id="2c12e-162">Det här kommandot sorterar textfiler i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-162">This command sorts text files in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

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

<span data-ttu-id="2c12e-163">`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen **C:\test** och alla `*.txt` filer.</span><span class="sxs-lookup"><span data-stu-id="2c12e-163">The `Get-ChildItem` cmdlet uses the **Path** parameter to specify the directory **C:\Test** and all of the `*.txt` files.</span></span> <span data-ttu-id="2c12e-164">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-164">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="2c12e-165">`Sort-Object` använder **egenskaps** parametern med en hash-tabell för att avgöra varje fil intervall mellan **CreationTime** och **LastWriteTime**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-165">`Sort-Object` uses the **Property** parameter with a hash table to determine each files time span between **CreationTime** and **LastWriteTime**.</span></span> <span data-ttu-id="2c12e-166">Parametern **fallande** är inställd på `$False` att sortera i ordningen längst till kortast tids period.</span><span class="sxs-lookup"><span data-stu-id="2c12e-166">The **Descending** parameter is set to `$False` to sort in the order of longest to shortest time span.</span></span>

### <span data-ttu-id="2c12e-167">Exempel 7: Sortera namn i en textfil</span><span class="sxs-lookup"><span data-stu-id="2c12e-167">Example 7: Sort names in a text file</span></span>

<span data-ttu-id="2c12e-168">Det här exemplet visar hur du sorterar en lista från en textfil.</span><span class="sxs-lookup"><span data-stu-id="2c12e-168">This example shows how to sort a list from a text file.</span></span> <span data-ttu-id="2c12e-169">Den ursprungliga filen visas som en osorterad lista.</span><span class="sxs-lookup"><span data-stu-id="2c12e-169">The original file is displayed as an unsorted list.</span></span> <span data-ttu-id="2c12e-170">`Sort-Object` sorterar innehållet och sorterar innehållet med den **unika** parameter som tar bort dubbletter.</span><span class="sxs-lookup"><span data-stu-id="2c12e-170">`Sort-Object` sorts the contents and then sorts the contents with the **Unique** parameter that removes duplicates.</span></span>

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

<span data-ttu-id="2c12e-171">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-171">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="2c12e-172">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-172">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span>

<span data-ttu-id="2c12e-173">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-173">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="2c12e-174">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-174">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="2c12e-175">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-175">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-176">`Sort-Object` sorterar listan i standard ordningen, stigande.</span><span class="sxs-lookup"><span data-stu-id="2c12e-176">`Sort-Object` sorts the list in the default order, ascending.</span></span>

<span data-ttu-id="2c12e-177">`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-177">The `Get-Content` cmdlet uses the **Path** parameter to specify the directory and file name.</span></span> <span data-ttu-id="2c12e-178">Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-178">The file **ServerNames.txt** contains an unsorted list of computer names.</span></span> <span data-ttu-id="2c12e-179">Objekten skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-179">The objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-180">`Sort-Object` använder den **unika** parametern för att ta bort dubbla dator namn.</span><span class="sxs-lookup"><span data-stu-id="2c12e-180">`Sort-Object` uses the **Unique** parameter to remove duplicate computer names.</span></span> <span data-ttu-id="2c12e-181">Listan sorteras i standard ordningen, stigande.</span><span class="sxs-lookup"><span data-stu-id="2c12e-181">The list is sorted in the default order, ascending.</span></span>

### <span data-ttu-id="2c12e-182">Exempel 8: sortera en sträng som ett heltal</span><span class="sxs-lookup"><span data-stu-id="2c12e-182">Example 8: Sort a string as an integer</span></span>

<span data-ttu-id="2c12e-183">Det här exemplet visar hur du sorterar en textfil som innehåller sträng objekt som heltal.</span><span class="sxs-lookup"><span data-stu-id="2c12e-183">This example shows how to sort a text file that contains string objects as integers.</span></span> <span data-ttu-id="2c12e-184">Du kan skicka varje kommando nedåt i pipeline till `Get-Member` och kontrol lera att objekten är strängar i stället för heltal.</span><span class="sxs-lookup"><span data-stu-id="2c12e-184">You can send each command down the pipeline to `Get-Member` and verify that the objects are strings instead of integers.</span></span> <span data-ttu-id="2c12e-185">I de här exemplen `ProductId.txt` innehåller filen en osorterad lista med produkt nummer.</span><span class="sxs-lookup"><span data-stu-id="2c12e-185">For these examples, the `ProductId.txt` file contains an unsorted list of product numbers.</span></span>

<span data-ttu-id="2c12e-186">I det första exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-186">In the first example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-187">`Sort-Object` sorterar sträng objekt i stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-187">`Sort-Object` sorts the string objects in ascending order.</span></span>

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

<span data-ttu-id="2c12e-188">I det andra exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-188">In the second example, `Get-Content` gets the contents of the file and pipes lines to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="2c12e-189">`Sort-Object` använder ett-skript block för att konvertera strängarna till heltal.</span><span class="sxs-lookup"><span data-stu-id="2c12e-189">`Sort-Object` uses a script block to convert the strings to integers.</span></span> <span data-ttu-id="2c12e-190">I exempel koden `[int]` konverterar strängen till ett heltal och `$_` representerar varje sträng som den kommer nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-190">In the sample code, `[int]` converts the string to an integer and `$_` represents each string as it comes down the pipeline.</span></span> <span data-ttu-id="2c12e-191">Heltals objekt skickas ned pipelinen till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-191">The integer objects are sent down the pipeline to the `Sort-Object` cmdlet.</span></span>
<span data-ttu-id="2c12e-192">`Sort-Object` sorterar heltals objekt i numerisk ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-192">`Sort-Object` sorts the integer objects in numeric order.</span></span>

### <span data-ttu-id="2c12e-193">Exempel 9: använda stabila sorteringar</span><span class="sxs-lookup"><span data-stu-id="2c12e-193">Example 9: Using stable sorts</span></span>

<span data-ttu-id="2c12e-194">När du använder de **översta**, **lägsta** eller **stabila** parametrarna levereras de sorterade objekten i den ordning som de togs emot av `Sort-Object` när sorterings villkoren är lika.</span><span class="sxs-lookup"><span data-stu-id="2c12e-194">When you use the **Top**, **Bottom**, or **Stable** parameters, the sorted objects are delivered in the order they were received by `Sort-Object` when the sort criteria are equal.</span></span> <span data-ttu-id="2c12e-195">I det här exemplet sorterar vi siffrorna ett till 20 efter deras värde ' modulo 3 '.</span><span class="sxs-lookup"><span data-stu-id="2c12e-195">In this example, we are sorting the numbers one through 20 by the their value 'modulo 3'.</span></span> <span data-ttu-id="2c12e-196">Modulo-värdet sträcker sig från noll till två.</span><span class="sxs-lookup"><span data-stu-id="2c12e-196">The modulo value ranges from zero to two.</span></span>

```powershell
PS> 1..20 |Sort-Object {$_ % 3}
18
3
15
6
12
9
1
16
13
10
7
4
19
11
8
14
5
17
2
20

PS> 1..20 |Sort-Object {$_ % 3} -Stable
3
6
9
12
15
18
1
4
7
10
13
16
19
2
5
8
11
14
17
20
```

<span data-ttu-id="2c12e-197">Utdata från den första sorteringen grupperas korrekt efter Modulus-värdet, men de enskilda objekten sorteras inte inom Modulus-intervallet.</span><span class="sxs-lookup"><span data-stu-id="2c12e-197">The output from the first sort is correctly grouped by the modulus value but the individual items are not sorted within the modulus range.</span></span> <span data-ttu-id="2c12e-198">Den andra sorteringen använder alternativet **stabil** för att returnera en stabil sortering.</span><span class="sxs-lookup"><span data-stu-id="2c12e-198">The second sort uses the **Stable** option to return a stable sort.</span></span>

## <span data-ttu-id="2c12e-199">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2c12e-199">PARAMETERS</span></span>

### <span data-ttu-id="2c12e-200">-Nederkant</span><span class="sxs-lookup"><span data-stu-id="2c12e-200">-Bottom</span></span>

<span data-ttu-id="2c12e-201">Anger antalet objekt som ska hämtas från slutet av en sorterad objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="2c12e-201">Specifies the number of objects to get from the end of a sorted object array.</span></span> <span data-ttu-id="2c12e-202">Detta resulterar i en stabil sortering.</span><span class="sxs-lookup"><span data-stu-id="2c12e-202">This results in a stable sort.</span></span>

<span data-ttu-id="2c12e-203">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2c12e-203">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Bottom
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c12e-204">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="2c12e-204">-CaseSensitive</span></span>

<span data-ttu-id="2c12e-205">Anger att sorteringen är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="2c12e-205">Indicates that the sort is case-sensitive.</span></span> <span data-ttu-id="2c12e-206">Som standard är sorteringar inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="2c12e-206">By default, sorts are not case-sensitive.</span></span>

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

### <span data-ttu-id="2c12e-207">– Kultur</span><span class="sxs-lookup"><span data-stu-id="2c12e-207">-Culture</span></span>

<span data-ttu-id="2c12e-208">Anger den kulturella konfiguration som ska användas för sortering.</span><span class="sxs-lookup"><span data-stu-id="2c12e-208">Specifies the cultural configuration to use for sorts.</span></span> <span data-ttu-id="2c12e-209">Används `Get-Culture` för att Visa systemets kultur konfiguration.</span><span class="sxs-lookup"><span data-stu-id="2c12e-209">Use `Get-Culture` to display the system's culture configuration.</span></span>

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

### <span data-ttu-id="2c12e-210">-Fallande</span><span class="sxs-lookup"><span data-stu-id="2c12e-210">-Descending</span></span>

<span data-ttu-id="2c12e-211">Anger att `Sort-Object` objekten sorteras i fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-211">Indicates that `Sort-Object` sorts the objects in descending order.</span></span> <span data-ttu-id="2c12e-212">Standardvärdet är stigande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-212">The default is ascending order.</span></span>

<span data-ttu-id="2c12e-213">Om du vill sortera flera egenskaper med olika sorterings ordning använder du en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="2c12e-213">To sort multiple properties with different sort orders, use a hash table.</span></span> <span data-ttu-id="2c12e-214">Med en hash-tabell kan du till exempel sortera en egenskap i stigande ordning och en annan egenskap i fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="2c12e-214">For example, with a hash table you can sort one property in ascending order and another property in descending order.</span></span>

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

### <span data-ttu-id="2c12e-215">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2c12e-215">-InputObject</span></span>

<span data-ttu-id="2c12e-216">Om du vill sortera objekt kan du skicka dem nedåt i pipeline till `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="2c12e-216">To sort objects, send them down the pipeline to `Sort-Object`.</span></span> <span data-ttu-id="2c12e-217">Om du använder parametern **InputObject** för att skicka en samling objekt, `Sort-Object` tar emot ett objekt som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-217">If you use the **InputObject** parameter to submit a collection of items, `Sort-Object` receives one object that represents the collection.</span></span> <span data-ttu-id="2c12e-218">Eftersom ett objekt inte kan sorteras, `Sort-Object` returnerar hela samlingen oförändrad.</span><span class="sxs-lookup"><span data-stu-id="2c12e-218">Because one object cannot be sorted, `Sort-Object` returns the entire collection unchanged.</span></span>

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

### <span data-ttu-id="2c12e-219">– Egenskap</span><span class="sxs-lookup"><span data-stu-id="2c12e-219">-Property</span></span>

<span data-ttu-id="2c12e-220">Anger de egenskaps namn som `Sort-Object` används för att sortera objekten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-220">Specifies the property names that `Sort-Object` uses to sort the objects.</span></span> <span data-ttu-id="2c12e-221">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2c12e-221">Wildcards are permitted.</span></span>
<span data-ttu-id="2c12e-222">Objekten sorteras baserat på egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="2c12e-222">Objects are sorted based on the property values.</span></span> <span data-ttu-id="2c12e-223">Om du inte anger någon egenskap, `Sort-Object` sorteras baserat på standard egenskaper för objekt typen eller själva objekten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-223">If you do not specify a property, `Sort-Object` sorts based on default properties for the object type or the objects themselves.</span></span>

<span data-ttu-id="2c12e-224">Flera egenskaper kan sorteras i stigande ordning, fallande ordning eller en kombination av sorterings ordningar.</span><span class="sxs-lookup"><span data-stu-id="2c12e-224">Multiple properties can be sorted in ascending order, descending order, or a combination of sort orders.</span></span> <span data-ttu-id="2c12e-225">När du anger flera egenskaper sorteras objekten efter den första egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-225">When you specify multiple properties, the objects are sorted by the first property.</span></span> <span data-ttu-id="2c12e-226">Om flera objekt har samma värde för den första egenskapen, sorteras dessa objekt efter den andra egenskapen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-226">If multiple objects have the same value for the first property, those objects are sorted by the second property.</span></span> <span data-ttu-id="2c12e-227">Den här processen fortsätter tills det inte finns några fler angivna egenskaper eller inga grupper av objekt.</span><span class="sxs-lookup"><span data-stu-id="2c12e-227">This process continues until there are no more specified properties or no groups of objects.</span></span>

<span data-ttu-id="2c12e-228">**Egenskaps** parameterns värde kan vara en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2c12e-228">The **Property** parameter's value can be a calculated property.</span></span> <span data-ttu-id="2c12e-229">Använd en hash-tabell om du vill skapa en beräknad egenskap.</span><span class="sxs-lookup"><span data-stu-id="2c12e-229">To create a calculated property, use a hash table.</span></span>

<span data-ttu-id="2c12e-230">Giltiga nycklar för en hash-tabell är följande:</span><span class="sxs-lookup"><span data-stu-id="2c12e-230">Valid keys for a hash table are as follows:</span></span>

- <span data-ttu-id="2c12e-231">`expression` - `<string>` eller `<script block>`</span><span class="sxs-lookup"><span data-stu-id="2c12e-231">`expression` - `<string>` or `<script block>`</span></span>
- <span data-ttu-id="2c12e-232">`ascending` eller `descending` - `<boolean>`</span><span class="sxs-lookup"><span data-stu-id="2c12e-232">`ascending` or `descending` - `<boolean>`</span></span>

<span data-ttu-id="2c12e-233">Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span><span class="sxs-lookup"><span data-stu-id="2c12e-233">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

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

### <span data-ttu-id="2c12e-234">– Överst</span><span class="sxs-lookup"><span data-stu-id="2c12e-234">-Top</span></span>

<span data-ttu-id="2c12e-235">Anger antalet objekt som ska hämtas från början av en sorterad objekt mat ris.</span><span class="sxs-lookup"><span data-stu-id="2c12e-235">Specifies the number of objects to get from the start of a sorted object array.</span></span> <span data-ttu-id="2c12e-236">Detta resulterar i en stabil sortering.</span><span class="sxs-lookup"><span data-stu-id="2c12e-236">This results in a stable sort.</span></span>

<span data-ttu-id="2c12e-237">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2c12e-237">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Top
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c12e-238">– Unik</span><span class="sxs-lookup"><span data-stu-id="2c12e-238">-Unique</span></span>

<span data-ttu-id="2c12e-239">Anger att `Sort-Object` tar bort dubbletter och returnerar bara de unika medlemmarna i samlingen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-239">Indicates that `Sort-Object` eliminates duplicates and returns only the unique members of the collection.</span></span> <span data-ttu-id="2c12e-240">Den första instansen av ett unikt värde ingår i de sorterade utdata.</span><span class="sxs-lookup"><span data-stu-id="2c12e-240">The first instance of a unique value is included in the sorted output.</span></span>

<span data-ttu-id="2c12e-241">**Unique** är Skift läges okänsligt.</span><span class="sxs-lookup"><span data-stu-id="2c12e-241">**Unique** is case-insensitive.</span></span> <span data-ttu-id="2c12e-242">Strängar som endast skiljer sig från versaler anses vara identiska.</span><span class="sxs-lookup"><span data-stu-id="2c12e-242">Strings that only differ by character case are considered the same.</span></span>
<span data-ttu-id="2c12e-243">Till exempel, Character och CHARACTER.</span><span class="sxs-lookup"><span data-stu-id="2c12e-243">For example, character and CHARACTER.</span></span>

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

### <span data-ttu-id="2c12e-244">– Stabil</span><span class="sxs-lookup"><span data-stu-id="2c12e-244">-Stable</span></span>

<span data-ttu-id="2c12e-245">De sorterade objekten levereras i den ordning som de togs emot när sorterings villkoren är lika.</span><span class="sxs-lookup"><span data-stu-id="2c12e-245">The sorted objects are delivered in the order they were received when the sort criteria are equal.</span></span>

<span data-ttu-id="2c12e-246">Den här parametern lades till i PowerShell v-6.2.0.</span><span class="sxs-lookup"><span data-stu-id="2c12e-246">This parameter was added in PowerShell v6.2.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2c12e-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2c12e-247">CommonParameters</span></span>

<span data-ttu-id="2c12e-248">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2c12e-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2c12e-249">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2c12e-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2c12e-250">INDATA</span><span class="sxs-lookup"><span data-stu-id="2c12e-250">INPUTS</span></span>

### <span data-ttu-id="2c12e-251">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2c12e-251">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2c12e-252">Du kan skicka vidare de objekt som ska sorteras till `Sort-Object` .</span><span class="sxs-lookup"><span data-stu-id="2c12e-252">You can pipe the objects to be sorted to `Sort-Object`.</span></span>

## <span data-ttu-id="2c12e-253">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2c12e-253">OUTPUTS</span></span>

### <span data-ttu-id="2c12e-254">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2c12e-254">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2c12e-255">`Sort-Object` Returnerar de sorterade objekten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-255">`Sort-Object` returns the sorted objects.</span></span>

## <span data-ttu-id="2c12e-256">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2c12e-256">NOTES</span></span>

<span data-ttu-id="2c12e-257">`Sort-Object`Cmdlet sorterar objekt baserat på egenskaper som anges i kommandot eller standard sorterings egenskaperna för objekt typen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-257">The `Sort-Object` cmdlet sorts objects based on properties specified in the command or the default sort properties for the object type.</span></span> <span data-ttu-id="2c12e-258">Standard sorterings egenskaper definieras med hjälp av `PropertySet` namnet `DefaultKeyPropertySet` i en `types.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="2c12e-258">Default sort properties are defined using the `PropertySet` named `DefaultKeyPropertySet` in a `types.ps1xml` file.</span></span> <span data-ttu-id="2c12e-259">Mer information finns i [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="2c12e-259">For more information, see [about_Types.ps1xml](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).</span></span>

<span data-ttu-id="2c12e-260">Om ett objekt inte har någon av de angivna egenskaperna tolkas egenskap svärdet för objektet med `Sort-Object` **Null** och placeras i slutet av sorterings ordningen.</span><span class="sxs-lookup"><span data-stu-id="2c12e-260">If an object does not have one of the specified properties, the property value for that object is interpreted by `Sort-Object` as **Null** and placed at the end of the sort order.</span></span>

<span data-ttu-id="2c12e-261">När inga sorterings egenskaper är tillgängliga försöker PowerShell att jämföra själva objekten.</span><span class="sxs-lookup"><span data-stu-id="2c12e-261">When no sort properties are available, PowerShell attempts to compare the objects themselves.</span></span>
<span data-ttu-id="2c12e-262">`Sort-Object` använder metoden **compare** för varje egenskap.</span><span class="sxs-lookup"><span data-stu-id="2c12e-262">`Sort-Object` uses the **Compare** method for each property.</span></span> <span data-ttu-id="2c12e-263">Om en egenskap inte implementerar **IComparable**, konverterar cmdleten egenskap svärdet till en sträng och använder metoden **compare** för **system. String**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-263">If a property does not implement **IComparable**, the cmdlet converts the property value to a string and uses the **Compare** method for **System.String**.</span></span> <span data-ttu-id="2c12e-264">Mer information finns i [metoden PSObject. CompareTo (Object)](/dotnet/api/system.management.automation.psobject.compareto).</span><span class="sxs-lookup"><span data-stu-id="2c12e-264">For more information, see [PSObject.CompareTo(Object) Method](/dotnet/api/system.management.automation.psobject.compareto).</span></span>

<span data-ttu-id="2c12e-265">Om du sorterar efter en uppräknad egenskap, till exempel **status**, `Sort-Object` sorteras efter uppräknings värden.</span><span class="sxs-lookup"><span data-stu-id="2c12e-265">If you sort on an enumerated property such as **Status**, `Sort-Object` sorts by the enumeration values.</span></span> <span data-ttu-id="2c12e-266">För Windows-tjänster har **stoppat** värdet **1** och **körs** har värdet **4**.</span><span class="sxs-lookup"><span data-stu-id="2c12e-266">For Windows services, **Stopped** has a value of **1** and **Running** has a value of **4**.</span></span>
<span data-ttu-id="2c12e-267">**Stoppad** sorteras före **körning** på grund av uppräknade värden.</span><span class="sxs-lookup"><span data-stu-id="2c12e-267">**Stopped** is sorted before **Running** because of the enumerated values.</span></span> <span data-ttu-id="2c12e-268">Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span><span class="sxs-lookup"><span data-stu-id="2c12e-268">For more information, see [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).</span></span>

<span data-ttu-id="2c12e-269">Prestanda för sorterings algoritmen är långsammare vid en stabil sortering.</span><span class="sxs-lookup"><span data-stu-id="2c12e-269">The performance of the sorting algorithm is slower when doing a stable sort.</span></span>

## <span data-ttu-id="2c12e-270">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2c12e-270">RELATED LINKS</span></span>

[<span data-ttu-id="2c12e-271">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="2c12e-271">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="2c12e-272">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="2c12e-272">about_Hash_Tables</span></span>](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[<span data-ttu-id="2c12e-273">about_Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="2c12e-273">about_Types.ps1xml</span></span>](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[<span data-ttu-id="2c12e-274">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-274">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="2c12e-275">-Objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-275">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="2c12e-276">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-276">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="2c12e-277">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-277">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="2c12e-278">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-278">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="2c12e-279">Select-Object</span><span class="sxs-lookup"><span data-stu-id="2c12e-279">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="2c12e-280">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="2c12e-280">Tee-Object</span></span>](Tee-Object.md)
