---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-counter?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Counter
ms.openlocfilehash: 4aed8db557b2d623aba4cd7218524af9957674c9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708772"
---
# <span data-ttu-id="26043-102">Get-Counter</span><span class="sxs-lookup"><span data-stu-id="26043-102">Get-Counter</span></span>

## <span data-ttu-id="26043-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="26043-103">SYNOPSIS</span></span>
<span data-ttu-id="26043-104">Hämtar prestanda räknar data från lokala datorer och fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="26043-104">Gets performance counter data from local and remote computers.</span></span>

## <span data-ttu-id="26043-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26043-105">SYNTAX</span></span>

### <span data-ttu-id="26043-106">GetCounterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="26043-106">GetCounterSet (Default)</span></span>

```
Get-Counter [[-Counter] <String[]>] [-SampleInterval <Int32>] [-MaxSamples <Int64>] [-Continuous]
 [-ComputerName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="26043-107">ListSetSet</span><span class="sxs-lookup"><span data-stu-id="26043-107">ListSetSet</span></span>

```
Get-Counter [-ListSet] <String[]> [-ComputerName <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="26043-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="26043-108">DESCRIPTION</span></span>

<span data-ttu-id="26043-109">`Get-Counter`Cmdlet: en hämtar prestanda räknar data direkt från övervakningen av prestanda i Windows-serien med operativ system.</span><span class="sxs-lookup"><span data-stu-id="26043-109">The `Get-Counter` cmdlet gets performance counter data directly from the performance monitoring instrumentation in the Windows family of operating systems.</span></span> <span data-ttu-id="26043-110">`Get-Counter` hämtar prestanda data från en lokal dator eller fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="26043-110">`Get-Counter` gets performance data from a local computer or remote computers.</span></span>

<span data-ttu-id="26043-111">Du kan använda `Get-Counter` parametrarna för att ange en eller flera datorer, lista över prestanda räknar uppsättningar och de instanser som de innehåller, ange exempel intervall och ange maximalt antal exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-111">You can use the `Get-Counter` parameters to specify one or more computers, list the performance counter sets and the instances they contain, set the sample intervals, and specify the maximum number of samples.</span></span> <span data-ttu-id="26043-112">Utan parametrar `Get-Counter` hämtar prestanda räknar data för en uppsättning system räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-112">Without parameters, `Get-Counter` gets performance counter data for a set of system counters.</span></span>

<span data-ttu-id="26043-113">Många räknar uppsättningar skyddas av åtkomst kontrol listor (ACL).</span><span class="sxs-lookup"><span data-stu-id="26043-113">Many counter sets are protected by access control lists (ACL).</span></span> <span data-ttu-id="26043-114">Om du vill se alla räknar uppsättningar öppnar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="26043-114">To see all counter sets, open PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="26043-115">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="26043-115">This cmdlet was reintroduced in PowerShell 7.</span></span>

## <span data-ttu-id="26043-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="26043-116">EXAMPLES</span></span>

### <span data-ttu-id="26043-117">Exempel 1: hämta listan med räknar uppsättningar</span><span class="sxs-lookup"><span data-stu-id="26043-117">Example 1: Get the counter set list</span></span>

<span data-ttu-id="26043-118">Det här exemplet hämtar listan över räknar uppsättningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-118">This example gets the local computer's list of counter sets.</span></span>

```powershell
Get-Counter -ListSet *
```

```Output
CounterSetName     : Processor
MachineName        : .
CounterSetType     : MultiInstance
Description        : The Processor performance object consists of counters that measure aspects ...
                     computer that performs arithmetic and logical computations, initiates ...
                     computer can have multiple processors.  The processor object represents ...
Paths              : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
PathsWithInstances : {\Processor(0)\% Processor Time, \Processor(1)\% Processor Time, ...
Counter            : {\Processor(*)\% Processor Time, \Processor(*)\% User Time, ...
```

<span data-ttu-id="26043-119">`Get-Counter` använder parametern **ListSet** med en asterisk ( `*` ) för att hämta listan över räknar uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="26043-119">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get the list of counter sets.</span></span>
<span data-ttu-id="26043-120">Punkten ( `.` ) i kolumnen **MachineName** representerar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-120">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="26043-121">Exempel 2: Ange SampleInterval och MaxSamples</span><span class="sxs-lookup"><span data-stu-id="26043-121">Example 2: Specify the SampleInterval and MaxSamples</span></span>

<span data-ttu-id="26043-122">I det här exemplet hämtas räknar data för alla processorer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-122">This examples gets the counter data for all processors on the local computer.</span></span> <span data-ttu-id="26043-123">Data samlas in med två sekunders mellanrum tills det finns tre exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-123">Data is collected at two-second intervals until there are three samples.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -SampleInterval 2 -MaxSamples 3
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/18/2019 14:39:56        \\Computer01\processor(_total)\% processor time :
                          20.7144271584086

6/18/2019 14:39:58        \\Computer01\processor(_total)\% processor time :
                          10.4391790575511

6/18/2019 14:40:01        \\Computer01\processor(_total)\% processor time :
                          37.5968799396998
```

<span data-ttu-id="26043-124">`Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägen `\Processor(_Total)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="26043-124">`Get-Counter` uses the **Counter** parameter to specify the counter path `\Processor(_Total)\% Processor Time`.</span></span> <span data-ttu-id="26043-125">Parametern **SampleInterval** anger ett intervall på två sekunder för att kontrol lera räknaren.</span><span class="sxs-lookup"><span data-stu-id="26043-125">The **SampleInterval** parameter sets a two-second interval to check the counter.</span></span> <span data-ttu-id="26043-126">**MaxSamples** anger att tre är det maximala antalet gånger för att kontrol lera räknaren.</span><span class="sxs-lookup"><span data-stu-id="26043-126">**MaxSamples** determines that three is the maximum number of times to check the counter.</span></span>

### <span data-ttu-id="26043-127">Exempel 3: Hämta kontinuerliga exempel på en räknare</span><span class="sxs-lookup"><span data-stu-id="26043-127">Example 3: Get continuous samples of a counter</span></span>

<span data-ttu-id="26043-128">I det här exemplet hämtas kontinuerliga exempel för en räknare varje sekund.</span><span class="sxs-lookup"><span data-stu-id="26043-128">This examples gets continuous samples for a counter every second.</span></span> <span data-ttu-id="26043-129">Tryck på <kbd>CTRL</kbd>C om du vill stoppa kommandot + <kbd></kbd>.</span><span class="sxs-lookup"><span data-stu-id="26043-129">To stop the command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="26043-130">Om du vill ange ett längre intervall mellan exempel använder du parametern **SampleInterval** .</span><span class="sxs-lookup"><span data-stu-id="26043-130">To specify a longer interval between samples, use the **SampleInterval** parameter.</span></span>

```powershell
Get-Counter -Counter "\Processor(_Total)\% Processor Time" -Continuous
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 15:35:03        \\Computer01\processor(_total)\% processor time :
                          43.8522842937022

6/19/2019 15:35:04        \\Computer01\processor(_total)\% processor time :
                          29.7896844697383

6/19/2019 15:35:05        \\Computer01\processor(_total)\% processor time :
                          29.4962645638135

6/19/2019 15:35:06        \\Computer01\processor(_total)\% processor time :
                          25.5901500127408
```

<span data-ttu-id="26043-131">`Get-Counter` använder **Counter** -parametern för att ange `\Processor\% Processor Time` räknaren.</span><span class="sxs-lookup"><span data-stu-id="26043-131">`Get-Counter` uses the **Counter** parameter to specify the `\Processor\% Processor Time` counter.</span></span>
<span data-ttu-id="26043-132">Den **kontinuerliga** parametern anger för att hämta exempel varje sekund tills kommandot har stoppats med <kbd>CTRL</kbd> + <kbd>+ C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="26043-132">The **Continuous** parameter specifies to get samples every second until the command is stopped with <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <span data-ttu-id="26043-133">Exempel 4: alfabetisk lista över räknar uppsättningar</span><span class="sxs-lookup"><span data-stu-id="26043-133">Example 4: Alphabetical list of counter sets</span></span>

<span data-ttu-id="26043-134">I det här exemplet används pipelinen för att hämta räknar listan och sortera listan i alfabetisk ordning.</span><span class="sxs-lookup"><span data-stu-id="26043-134">This example uses the pipeline to get the counter list set and then sort the list in alphabetical order.</span></span>

```powershell
Get-Counter -ListSet * |
  Sort-Object -Property CounterSetName |
    Format-Table CounterSetName, CounterSetType -AutoSize
```

```Output
CounterSetName                        CounterSetType
--------------                        --------------
.NET CLR Data                         SingleInstance
.NET Data Provider for SqlServer      SingleInstance
AppV Client Streamed Data Percentage  SingleInstance
Authorization Manager Applications    SingleInstance
BitLocker                             MultiInstance
Bluetooth Device                      SingleInstance
Cache                                 SingleInstance
Client Side Caching                   SingleInstance
```

<span data-ttu-id="26043-135">`Get-Counter` använder parametern **ListSet** med en asterisk ( `*` ) för att få en fullständig lista över räknar uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="26043-135">`Get-Counter` uses the **ListSet** parameter with an asterisk (`*`) to get a complete list of counter sets.</span></span> <span data-ttu-id="26043-136">**CounterSet** -objekten skickas nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-136">The **CounterSet** objects are sent down the pipeline.</span></span> <span data-ttu-id="26043-137">`Sort-Object` använder **egenskaps** parametern för att ange att objekten sorteras efter **CounterSetName**.</span><span class="sxs-lookup"><span data-stu-id="26043-137">`Sort-Object` uses the **Property** parameter to specify that the objects are sorted by **CounterSetName**.</span></span> <span data-ttu-id="26043-138">Objekten skickas ned pipelinen till `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="26043-138">The objects are sent down the pipeline to `Format-Table`.</span></span> <span data-ttu-id="26043-139">Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.</span><span class="sxs-lookup"><span data-stu-id="26043-139">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

<span data-ttu-id="26043-140">Punkten ( `.` ) i kolumnen **MachineName** representerar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-140">The dot (`.`) in the **MachineName** column represents the local computer.</span></span>

### <span data-ttu-id="26043-141">Exempel 5: kör ett bakgrunds jobb för att hämta räknar data</span><span class="sxs-lookup"><span data-stu-id="26043-141">Example 5: Run a background job to get counter data</span></span>

<span data-ttu-id="26043-142">I det här exemplet `Start-Job` kör ett `Get-Counter` kommando som bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-142">In this example, `Start-Job` runs a `Get-Counter` command as a background job on the local computer.</span></span>
<span data-ttu-id="26043-143">Om du vill visa prestanda räknarens utdata från jobbet använder du `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="26043-143">To view the performance counter output from the job, use the `Receive-Job` cmdlet.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Counter -Counter "\LogicalDisk(_Total)\% Free Space" -MaxSamples 1000}
```

```Output
Id     Name  PSJobTypeName   State    HasMoreData  Location   Command
--     ----  -------------   -----    -----------  --------   -------
1      Job1  BackgroundJob   Running  True         localhost  Get-Counter -Counter
```

<span data-ttu-id="26043-144">`Start-Job` använder parametern **script block** för att köra ett `Get-Counter` kommando.</span><span class="sxs-lookup"><span data-stu-id="26043-144">`Start-Job` uses the **ScriptBlock** parameter to run a `Get-Counter` command.</span></span> <span data-ttu-id="26043-145">`Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägen `\LogicalDisk(_Total)\% Free Space` .</span><span class="sxs-lookup"><span data-stu-id="26043-145">`Get-Counter` uses the **Counter** parameter to specify the counter path `\LogicalDisk(_Total)\% Free Space`.</span></span> <span data-ttu-id="26043-146">Parametern **MaxSamples** anger för att hämta 1000-exempel av räknaren.</span><span class="sxs-lookup"><span data-stu-id="26043-146">The **MaxSamples** parameter specifies to get 1000 samples of the counter.</span></span>

### <span data-ttu-id="26043-147">Exempel 6: Hämta räknar data från flera datorer</span><span class="sxs-lookup"><span data-stu-id="26043-147">Example 6: Get counter data from multiple computers</span></span>

<span data-ttu-id="26043-148">I det här exemplet används en variabel för att hämta prestanda räknar data från två datorer.</span><span class="sxs-lookup"><span data-stu-id="26043-148">This example uses a variable to get performance counter data from two computers.</span></span>

```powershell
$DiskReads = "\LogicalDisk(C:)\Disk Reads/sec"
$DiskReads | Get-Counter -ComputerName Server01, Server02 -MaxSamples 10
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/21/2019 10:51:04        \\Server01\logicaldisk(c:)\disk reads/sec :
                          0

                          \\Server02\logicaldisk(c:)\disk reads/sec :
                          0.983050344269146
```

<span data-ttu-id="26043-149">`$DiskReads`Variabeln lagrar `\LogicalDisk(C:)\Disk Reads/sec` räknar Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="26043-149">The `$DiskReads` variable stores the `\LogicalDisk(C:)\Disk Reads/sec` counter path.</span></span> <span data-ttu-id="26043-150">`$DiskReads`Variabeln skickas ned pipelinen till `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="26043-150">The `$DiskReads` variable is sent down the pipeline to `Get-Counter`.</span></span> <span data-ttu-id="26043-151">**Counter** är den första positions parametern och accepterar sökvägen som lagras i `$DiskReads` .</span><span class="sxs-lookup"><span data-stu-id="26043-151">**Counter** is the first position parameter and accepts the path stored in `$DiskReads`.</span></span> <span data-ttu-id="26043-152">**Computername** anger de två datorerna och **MaxSamples** anger för att hämta 10 exempel från varje dator.</span><span class="sxs-lookup"><span data-stu-id="26043-152">**ComputerName** specifies the two computers and **MaxSamples** specifies to get 10 samples from each computer.</span></span>

### <span data-ttu-id="26043-153">Exempel 7: Hämta en räknares instans värden från flera slumpmässiga datorer</span><span class="sxs-lookup"><span data-stu-id="26043-153">Example 7: Get a counter's instance values from multiple random computers</span></span>

<span data-ttu-id="26043-154">I det här exemplet hämtas värdet för en prestanda räknare på 50 slumpmässiga, fjärrdatorer i företaget.</span><span class="sxs-lookup"><span data-stu-id="26043-154">This example gets the value of a performance counter on 50 random, remote computers in the enterprise.</span></span> <span data-ttu-id="26043-155">Parametern **computername** använder slumpmässiga dator namn som lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="26043-155">The **ComputerName** parameter uses random computer names stored in a variable.</span></span> <span data-ttu-id="26043-156">Skapa om variabeln om du vill uppdatera dator namnen i variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-156">To update the computer names in the variable, recreate the variable.</span></span>

<span data-ttu-id="26043-157">Ett alternativ för Server namnen i parametern **computername** är att använda en textfil.</span><span class="sxs-lookup"><span data-stu-id="26043-157">An alternative for the server names in the **ComputerName** parameter is to use a text file.</span></span> <span data-ttu-id="26043-158">Exempel:</span><span class="sxs-lookup"><span data-stu-id="26043-158">For example:</span></span>

`-ComputerName (Get-Random (Get-Content -Path C:\Servers.txt) -Count 50)`

<span data-ttu-id="26043-159">Räknar Sök vägen innehåller en asterisk ( `*` ) i instans namnet för att hämta data för var och en av datorns processorer.</span><span class="sxs-lookup"><span data-stu-id="26043-159">The counter path includes an asterisk (`*`) in the instance name to get the data for each of the remote computer's processors.</span></span>

```powershell
$Servers = Get-Random (Get-Content -Path C:\Servers.txt) -Count 50
$Counter = "\Processor(*)\% Processor Time"
Get-Counter -Counter $Counter -ComputerName $Servers
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/20/2019 12:20:35        \\Server01\processor(0)\% processor time :
                          6.52610319637854

                          \\Server01\processor(1)\% processor time :
                          3.41030663625782

                          \\Server01\processor(2)\% processor time :
                          9.64189975649925

                          \\Server01\processor(3)\% processor time :
                          1.85240835619747

                          \\Server01\processor(_total)\% processor time :
                          5.35768447160776
```

<span data-ttu-id="26043-160">`Get-Random`Cmdleten använder `Get-Content` för att välja 50 slumpmässiga dator namn från `Servers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="26043-160">The `Get-Random` cmdlet uses `Get-Content` to select 50 random computer names from the `Servers.txt` file.</span></span> <span data-ttu-id="26043-161">Fjärrdatorns namn lagras i `$Servers` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-161">The remote computer names are stored in the `$Servers` variable.</span></span> <span data-ttu-id="26043-162">`\Processor(*)\% Processor Time`Räknar Sök vägen lagras i `$Counter` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-162">The `\Processor(*)\% Processor Time` counter's path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="26043-163">`Get-Counter` använder **Counter** -parametern för att ange räknare i `$Counter` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-163">`Get-Counter` uses the **Counter** parameter to specify the counters in the `$Counter` variable.</span></span> <span data-ttu-id="26043-164">Parametern **computername** anger dator namnen i `$Servers` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-164">The **ComputerName** parameter specifies the computer names in the `$Servers` variable.</span></span>

### <span data-ttu-id="26043-165">Exempel 8: Använd egenskapen Path för att hämta formaterade Sök vägs namn</span><span class="sxs-lookup"><span data-stu-id="26043-165">Example 8: Use the Path property to get formatted path names</span></span>

<span data-ttu-id="26043-166">I det här exemplet används **Sök vägs** egenskapen för en räknare för att hitta de formaterade Sök vägs namnen för prestanda räknarna.</span><span class="sxs-lookup"><span data-stu-id="26043-166">This example uses the **Path** property of a counter set to find the formatted path names for the performance counters.</span></span>

<span data-ttu-id="26043-167">Pipelinen används med `Where-Object` cmdleten för att hitta en delmängd av Sök vägs namnen.</span><span class="sxs-lookup"><span data-stu-id="26043-167">The pipeline is used with the `Where-Object` cmdlet to find a subset of the path names.</span></span> <span data-ttu-id="26043-168">Om du vill söka efter en lista över räknar Sök vägar tar du bort pipelinen ( `|` ) och `Where-Object` kommandot.</span><span class="sxs-lookup"><span data-stu-id="26043-168">To find a counter sets complete list of counter paths, remove the pipeline (`|`) and `Where-Object` command.</span></span>

<span data-ttu-id="26043-169">`$_`Är en automatisk variabel för det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-169">The `$_` is an automatic variable for the current object in the pipeline.</span></span>
<span data-ttu-id="26043-170">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="26043-170">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

```powershell
(Get-Counter -ListSet Memory).Paths | Where-Object { $_ -like "*Cache*" }
```

```Output
\Memory\Cache Faults/sec
\Memory\Cache Bytes
\Memory\Cache Bytes Peak
\Memory\System Cache Resident Bytes
\Memory\Standby Cache Reserve Bytes
\Memory\Standby Cache Normal Priority Bytes
\Memory\Standby Cache Core Bytes
\Memory\Long-Term Average Standby Cache Lifetime (s)
```

<span data-ttu-id="26043-171">`Get-Counter` använder parametern **ListSet** för att ange **minnes** räknar uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="26043-171">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="26043-172">Kommandot omges av parenteser så att egenskapen **Paths** returnerar varje sökväg som en sträng.</span><span class="sxs-lookup"><span data-stu-id="26043-172">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="26043-173">Objekten skickas ned pipelinen till `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="26043-173">The objects are sent down the pipeline to `Where-Object`.</span></span> <span data-ttu-id="26043-174">`Where-Object` använder variabeln `$_` för att bearbeta varje objekt och använder `-like` operatorn för att hitta matchningar för strängen `*Cache*` .</span><span class="sxs-lookup"><span data-stu-id="26043-174">`Where-Object` uses the variable `$_` to process each object and uses the `-like` operator to find matches for the string `*Cache*`.</span></span> <span data-ttu-id="26043-175">Asteriskerna ( `*` ) är jokertecken för alla tecken.</span><span class="sxs-lookup"><span data-stu-id="26043-175">The asterisks (`*`) are wildcards for any characters.</span></span>

### <span data-ttu-id="26043-176">Exempel 9: Använd egenskapen PathsWithInstances för att hämta formaterade Sök vägs namn</span><span class="sxs-lookup"><span data-stu-id="26043-176">Example 9: Use the PathsWithInstances property to get formatted path names</span></span>

<span data-ttu-id="26043-177">I det här exemplet hämtas de formaterade Sök vägs namnen som innehåller instanserna för prestanda räknaren **fysisk disk** .</span><span class="sxs-lookup"><span data-stu-id="26043-177">This example gets the formatted path names that include the instances for the **PhysicalDisk** performance counters.</span></span>

```powershell
(Get-Counter -ListSet PhysicalDisk).PathsWithInstances
```

```Output
\PhysicalDisk(0 C:)\Current Disk Queue Length
\PhysicalDisk(_Total)\Current Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Time
\PhysicalDisk(_Total)\% Disk Time
\PhysicalDisk(0 C:)\Avg. Disk Queue Length
\PhysicalDisk(_Total)\Avg. Disk Queue Length
\PhysicalDisk(0 C:)\% Disk Read Time
\PhysicalDisk(_Total)\% Disk Read Time
```

<span data-ttu-id="26043-178">`Get-Counter` använder parametern **ListSet** för att ange **fysisk disk** uppsättning.</span><span class="sxs-lookup"><span data-stu-id="26043-178">`Get-Counter` uses the **ListSet** parameter to specify the **PhysicalDisk** counter set.</span></span> <span data-ttu-id="26043-179">Kommandot omges av parenteser så att egenskapen **PathsWithInstances** returnerar varje Sök vägs instans som en sträng.</span><span class="sxs-lookup"><span data-stu-id="26043-179">The command is enclosed in parentheses so that the **PathsWithInstances** property returns each path instance as a string.</span></span>

### <span data-ttu-id="26043-180">Exempel 10: Hämta ett enda värde för varje räknare i en räknar uppsättning</span><span class="sxs-lookup"><span data-stu-id="26043-180">Example 10: Get a single value for each counter in a counter set</span></span>

<span data-ttu-id="26043-181">I det här exemplet returneras ett enskilt värde för varje prestanda räknare i den lokala datorns **minnes** räknar uppsättning.</span><span class="sxs-lookup"><span data-stu-id="26043-181">In this example, a single value is returned for each performance counter in the local computer's **Memory** counter set.</span></span>

```powershell
$MemCounters = (Get-Counter -ListSet Memory).Paths
Get-Counter -Counter $MemCounters
```

```Output
Timestamp                 CounterSamples
---------                 --------------
6/19/2019 12:05:00        \\Computer01\memory\page faults/sec :
                          868.772077545597

                          \\Computer01\memory\available bytes :
                          9031176192

                          \\Computer01\memory\committed bytes :
                          8242982912

                          \\Computer01\memory\commit limit :
                          19603333120
```

<span data-ttu-id="26043-182">`Get-Counter` använder parametern **ListSet** för att ange **minnes** räknar uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="26043-182">`Get-Counter` uses the **ListSet** parameter to specify the **Memory** counter set.</span></span> <span data-ttu-id="26043-183">Kommandot omges av parenteser så att egenskapen **Paths** returnerar varje sökväg som en sträng.</span><span class="sxs-lookup"><span data-stu-id="26043-183">The command is enclosed in parentheses so that the **Paths** property returns each path as a string.</span></span> <span data-ttu-id="26043-184">Sök vägarna lagras i `$MemCounters` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-184">The paths are stored in the `$MemCounters` variable.</span></span> <span data-ttu-id="26043-185">`Get-Counter` använder **Counter** -parametern för att ange räknar Sök vägar i `$MemCounters` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-185">`Get-Counter` uses the **Counter** parameter to specify the counter paths in the `$MemCounters` variable.</span></span>

### <span data-ttu-id="26043-186">Exempel 11: Visa ett objekts egenskaps värden</span><span class="sxs-lookup"><span data-stu-id="26043-186">Example 11: Display an object's property values</span></span>

<span data-ttu-id="26043-187">Egenskaps värden i **PerformanceCounterSample** -objektet representerar varje data exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-187">The property values in the **PerformanceCounterSample** object represent each data sample.</span></span> <span data-ttu-id="26043-188">I det här exemplet använder vi egenskaperna för **CounterSamples** -objektet för att undersöka, välja, sortera och gruppera data.</span><span class="sxs-lookup"><span data-stu-id="26043-188">In this example we use the properties of the **CounterSamples** object to examine, select, sort, and group the data.</span></span>

```powershell
$Counter = "\\Server01\Process(Idle)\% Processor Time"
$Data = Get-Counter $Counter
$Data.CounterSamples | Format-List -Property *
```

```Output
Path             : \\Server01\process(idle)\% processor time
InstanceName     : idle
CookedValue      : 198.467899571389
RawValue         : 14329160321003
SecondValue      : 128606459528326201
MultipleCount    : 1
CounterType      : Timer100Ns
Timestamp        : 6/19/2019 12:20:49
Timestamp100NSec : 128606207528320000
Status           : 0
DefaultScale     : 0
TimeBase         : 10000000
```

<span data-ttu-id="26043-189">Räknar Sök vägen lagras i `$Counter` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-189">The counter path is stored in the `$Counter` variable.</span></span> <span data-ttu-id="26043-190">`Get-Counter` hämtar ett exempel på räknar värden och lagrar resultatet i `$Data` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-190">`Get-Counter` gets one sample of the counter values and stores the results in the `$Data` variable.</span></span> <span data-ttu-id="26043-191">`$Data`Variabeln använder egenskapen **CounterSamples** för att hämta objektets egenskaper.</span><span class="sxs-lookup"><span data-stu-id="26043-191">The `$Data` variable uses the **CounterSamples** property to get the object's properties.</span></span> <span data-ttu-id="26043-192">Objektet skickas ned pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="26043-192">The object is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="26043-193">**Egenskaps** parametern använder en asterisk ( `*` ) som jokertecken för att markera alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="26043-193">The **Property** parameter uses an asterisk (`*`) wildcard to select all the properties.</span></span>

### <span data-ttu-id="26043-194">Exempel 12: mat ris värden för prestanda räknare</span><span class="sxs-lookup"><span data-stu-id="26043-194">Example 12: Performance counter array values</span></span>

<span data-ttu-id="26043-195">I det här exemplet lagrar en variabel varje prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-195">In this example, a variable stores each performance counter.</span></span> <span data-ttu-id="26043-196">Egenskapen **CounterSamples** är en matris som kan visa vissa räknar värden.</span><span class="sxs-lookup"><span data-stu-id="26043-196">The **CounterSamples** property is an array that can display specific counter values.</span></span>

<span data-ttu-id="26043-197">Om du vill visa varje räknar exempel använder du `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="26043-197">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples[0]
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              1.33997091699662
```

<span data-ttu-id="26043-198">`Get-Counter` använder **Counter** -parametern för att ange räknaren `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="26043-198">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="26043-199">Värdena lagras i `$Counter` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-199">The values are stored in the `$Counter` variable.</span></span>
<span data-ttu-id="26043-200">`$Counter.CounterSamples[0]` visar mat ris värdet för det första räknarvärdet.</span><span class="sxs-lookup"><span data-stu-id="26043-200">`$Counter.CounterSamples[0]` displays the array value for the first counter value.</span></span>

### <span data-ttu-id="26043-201">Exempel 13: jämför prestanda räknar värden</span><span class="sxs-lookup"><span data-stu-id="26043-201">Example 13: Compare performance counter values</span></span>

<span data-ttu-id="26043-202">I det här exemplet hittar du mängden processor tid som används av varje processor på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-202">This example finds the amount of processor time used by each processor on the local computer.</span></span> <span data-ttu-id="26043-203">Egenskapen **CounterSamples** används för att jämföra räknar data med ett angivet värde.</span><span class="sxs-lookup"><span data-stu-id="26043-203">The **CounterSamples** property is used to compare the counter data against a specified value.</span></span>

<span data-ttu-id="26043-204">Om du vill visa varje räknar exempel använder du `$Counter.CounterSamples` .</span><span class="sxs-lookup"><span data-stu-id="26043-204">To display each counter sample, use `$Counter.CounterSamples`.</span></span>

```powershell
$Counter = Get-Counter -Counter "\Processor(*)\% Processor Time"
$Counter.CounterSamples | Where-Object { $_.CookedValue -lt "20" }
```

```Output
Path                                         InstanceName        CookedValue
----                                         ------------        -----------
\\Computer01\processor(0)\% processor time   0              12.6398025240208
\\Computer01\processor(1)\% processor time   1              15.7598095767344
```

<span data-ttu-id="26043-205">`Get-Counter` använder **Counter** -parametern för att ange räknaren `\Processor(*)\% Processor Time` .</span><span class="sxs-lookup"><span data-stu-id="26043-205">`Get-Counter` uses the **Counter** parameter to specify the counter `\Processor(*)\% Processor Time`.</span></span> <span data-ttu-id="26043-206">Värdena lagras i `$Counter` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-206">The values are stored in the `$Counter` variable.</span></span> <span data-ttu-id="26043-207">De objekt som lagras i `$Counter.CounterSamples` skickas till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-207">The objects stored in `$Counter.CounterSamples` are sent down the pipeline.</span></span> <span data-ttu-id="26043-208">`Where-Object` använder ett-skript block för att jämföra varje objekt värde mot ett angivet värde på 20.</span><span class="sxs-lookup"><span data-stu-id="26043-208">`Where-Object` uses a script block to compare each objects value against a specified value of 20.</span></span> <span data-ttu-id="26043-209">`$_.CookedValue`Är en variabel för det aktuella objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-209">The `$_.CookedValue` is a variable for the current object in the pipeline.</span></span> <span data-ttu-id="26043-210">Räknare med en **CookedValue** som är mindre än 20 visas.</span><span class="sxs-lookup"><span data-stu-id="26043-210">Counters with a **CookedValue** that is less than 20 are displayed.</span></span>

### <span data-ttu-id="26043-211">Exempel 14: sortera prestanda räknar data</span><span class="sxs-lookup"><span data-stu-id="26043-211">Example 14: Sort performance counter data</span></span>

<span data-ttu-id="26043-212">Det här exemplet visar hur du sorterar prestanda räknar data.</span><span class="sxs-lookup"><span data-stu-id="26043-212">This example shows how to sort performance counter data.</span></span> <span data-ttu-id="26043-213">Exemplet hittar processerna på datorn som använder den mest processor tiden under exemplet.</span><span class="sxs-lookup"><span data-stu-id="26043-213">The example finds the processes on the computer that are using the most processor time during the sample.</span></span>

```powershell
$Procs = Get-Counter -Counter "\Process(*)\% Processor Time"
$Procs.CounterSamples | Sort-Object -Property CookedValue -Descending |
   Format-Table -Property Path, InstanceName, CookedValue -AutoSize
```

```Output
Path                                                         InstanceName             CookedValue
----                                                         ------------             -----------
\\Computer01\process(_total)\% processor time                _total              395.464129650573
\\Computer01\process(idle)\% processor time                  idle                389.356575524695
\\Computer01\process(mssense)\% processor time               mssense             3.05377706293879
\\Computer01\process(csrss#1)\% processor time               csrss               1.52688853146939
\\Computer01\process(microsoftedgecp#10)\% processor time    microsoftedgecp     1.52688853146939
\\Computer01\process(runtimebroker#5)\% processor time       runtimebroker                      0
\\Computer01\process(settingsynchost)\% processor time       settingsynchost                    0
\\Computer01\process(microsoftedgecp#16)\% processor time    microsoftedgecp                    0
```

<span data-ttu-id="26043-214">`Get-Counter` använder **Counter** -parametern för att ange `\Process(*)\% Processor Time` räknaren för alla processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-214">`Get-Counter` uses the **Counter** parameter to specify the `\Process(*)\% Processor Time` counter for all the processes on the local computer.</span></span> <span data-ttu-id="26043-215">Resultatet lagras i `$Procs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="26043-215">The result is stored in the `$Procs` variable.</span></span> <span data-ttu-id="26043-216">`$Procs`Variabeln med egenskapen **CounterSamples** skickar **PerformanceCounterSample** -objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-216">The `$Procs` variable with the **CounterSamples** property sends the **PerformanceCounterSample** objects down the pipeline.</span></span> <span data-ttu-id="26043-217">`Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **CookedValue** i **fallande** ordning.</span><span class="sxs-lookup"><span data-stu-id="26043-217">`Sort-Object` uses the **Property** parameter to sort the objects by **CookedValue** in **Descending** order.</span></span> <span data-ttu-id="26043-218">`Format-Table` använder **egenskaps** parametern för att välja kolumner för utdata.</span><span class="sxs-lookup"><span data-stu-id="26043-218">`Format-Table` uses the **Property** parameter to select the columns for the output.</span></span> <span data-ttu-id="26043-219">Parametern **AutoSize** justerar kolumn bredderna för att minimera trunkering.</span><span class="sxs-lookup"><span data-stu-id="26043-219">The **AutoSize** parameter adjusts the column widths to minimize truncation.</span></span>

## <span data-ttu-id="26043-220">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="26043-220">PARAMETERS</span></span>

### <span data-ttu-id="26043-221">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="26043-221">-ComputerName</span></span>

<span data-ttu-id="26043-222">Anger ett dator namn eller en kommaavgränsad **matris med fjärrdatornamn.**</span><span class="sxs-lookup"><span data-stu-id="26043-222">Specifies one computer name or a comma-separated array of **remote** computer names.</span></span> <span data-ttu-id="26043-223">Använd NetBIOS-namnet, en IP-adress eller datorns fullständigt kvalificerade domän namn.</span><span class="sxs-lookup"><span data-stu-id="26043-223">Use the NetBIOS name, an IP address, or the computer's fully qualified domain name.</span></span>

<span data-ttu-id="26043-224">Om du vill hämta prestanda räknar data från den **lokala** datorn utesluter du parametern **computername** .</span><span class="sxs-lookup"><span data-stu-id="26043-224">To get performance counter data from the **local** computer, exclude the **ComputerName** parameter.</span></span>
<span data-ttu-id="26043-225">För utdata, till exempel en **ListSet** som innehåller kolumnen **MachineName** , visar en punkt ( `.` ) den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-225">For output such as a **ListSet** that contains the **MachineName** column, a dot (`.`) indicates the local computer.</span></span>

<span data-ttu-id="26043-226">`Get-Counter` förlitar sig inte på PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="26043-226">`Get-Counter` doesn't rely on PowerShell remoting.</span></span> <span data-ttu-id="26043-227">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="26043-227">You can use the **ComputerName** parameter even if your computer isn't configured to run remote commands.</span></span>

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

### <span data-ttu-id="26043-228">-Kontinuerlig</span><span class="sxs-lookup"><span data-stu-id="26043-228">-Continuous</span></span>

<span data-ttu-id="26043-229">När den **kontinuerliga** har angetts `Get-Counter` hämtar vi exempel tills du trycker på <kbd>CTRL</kbd> + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="26043-229">When the **Continuous** is specified, `Get-Counter` gets samples until you press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="26043-230">Exempel hämtas varje sekund för varje angiven prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-230">Samples are obtained every second for each specified performance counter.</span></span> <span data-ttu-id="26043-231">Använd parametern **SampleInterval** för att öka intervallet mellan kontinuerliga exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-231">Use the **SampleInterval** parameter to increase the interval between continuous samples.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26043-232">-Counter</span><span class="sxs-lookup"><span data-stu-id="26043-232">-Counter</span></span>

<span data-ttu-id="26043-233">Anger sökvägen till en eller flera räknar Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="26043-233">Specifies the path to one or more counter paths.</span></span> <span data-ttu-id="26043-234">Sökvägar är indata som en kommaavgränsad matris, en variabel eller värden från en textfil.</span><span class="sxs-lookup"><span data-stu-id="26043-234">Paths are input as a comma-separated array, a variable, or values from a text file.</span></span> <span data-ttu-id="26043-235">Du kan skicka räknar Sök vägs strängar nedåt i pipeline till `Get-Counter` .</span><span class="sxs-lookup"><span data-stu-id="26043-235">You can send counter path strings down the pipeline to `Get-Counter`.</span></span>

<span data-ttu-id="26043-236">Räknar Sök vägar använder följande syntax:</span><span class="sxs-lookup"><span data-stu-id="26043-236">Counter paths use the following syntax:</span></span>

`\\ComputerName\CounterSet(Instance)\CounterName`

`\CounterSet(Instance)\CounterName`

<span data-ttu-id="26043-237">Exempel:</span><span class="sxs-lookup"><span data-stu-id="26043-237">For example:</span></span>

`\\Server01\Processor(*)\% User Time`

`\Processor(*)\% User Time`

<span data-ttu-id="26043-238">`\\ComputerName`Är valfritt i en prestanda räknar Sök väg.</span><span class="sxs-lookup"><span data-stu-id="26043-238">The `\\ComputerName` is optional in a performance counter path.</span></span> <span data-ttu-id="26043-239">Om räknar Sök vägen inte innehåller dator namnet, `Get-Counter` använder den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26043-239">If the counter path doesn't include the computer name, `Get-Counter` uses the local computer.</span></span>

<span data-ttu-id="26043-240">En asterisk ( `*` ) i instansen är ett jokertecken för att hämta alla instanser av räknaren.</span><span class="sxs-lookup"><span data-stu-id="26043-240">An asterisk (`*`) in the instance is a wildcard character to get all instances of the counter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="26043-241">-ListSet</span><span class="sxs-lookup"><span data-stu-id="26043-241">-ListSet</span></span>

<span data-ttu-id="26043-242">Visar en lista över prestanda räknar uppsättningar på datorerna.</span><span class="sxs-lookup"><span data-stu-id="26043-242">Lists the performance counter sets on the computers.</span></span> <span data-ttu-id="26043-243">Använd en asterisk ( `*` ) för att ange alla räknar uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="26043-243">Use an asterisk (`*`) to specify all counter sets.</span></span> <span data-ttu-id="26043-244">Ange ett namn eller en kommaavgränsad sträng för räknar uppsättnings namn.</span><span class="sxs-lookup"><span data-stu-id="26043-244">Enter one name or a comma-separated string of counter set names.</span></span> <span data-ttu-id="26043-245">Du kan skicka räknar uppsättnings namn nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26043-245">You can send counter set names down the pipeline.</span></span>

<span data-ttu-id="26043-246">Om du vill hämta en räknare som anger formaterade räknar Sök vägar använder du parametern **ListSet** .</span><span class="sxs-lookup"><span data-stu-id="26043-246">To get a counter sets formatted counter paths, use the **ListSet** parameter.</span></span> <span data-ttu-id="26043-247">Egenskaperna för **Sök vägarna** och **PathsWithInstances** för varje räknare innehåller de enskilda räknar Sök vägarna formaterade som en sträng.</span><span class="sxs-lookup"><span data-stu-id="26043-247">The **Paths** and **PathsWithInstances** properties of each counter set contain the individual counter paths formatted as a string.</span></span>

<span data-ttu-id="26043-248">Du kan spara räknar Sök vägs strängarna i en variabel eller använda pipelinen för att skicka strängen till ett annat `Get-Counter` kommando.</span><span class="sxs-lookup"><span data-stu-id="26043-248">You can save the counter path strings in a variable or use the pipeline to send the string to another `Get-Counter` command.</span></span>

<span data-ttu-id="26043-249">Till exempel för att skicka varje **processors** räknar Sök väg till `Get-Counter` :</span><span class="sxs-lookup"><span data-stu-id="26043-249">For example to send each **Processor** counter path to `Get-Counter`:</span></span>

`Get-Counter -ListSet Processor | Get-Counter`

> [!NOTE]
> <span data-ttu-id="26043-250">Det `Get-Counter` går inte att hämta egenskapen **Description** för räknar uppsättningen i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="26043-250">In PowerShell 7, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="26043-251">**Beskrivningen** anges till `$null` .</span><span class="sxs-lookup"><span data-stu-id="26043-251">The **Description** is set to `$null`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ListSetSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="26043-252">-MaxSamples</span><span class="sxs-lookup"><span data-stu-id="26043-252">-MaxSamples</span></span>

<span data-ttu-id="26043-253">Anger antalet prover som ska hämtas från varje angiven prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-253">Specifies the number of samples to get from each specified performance counter.</span></span> <span data-ttu-id="26043-254">Om du vill hämta en konstant data ström med exempel använder du den **kontinuerliga** parametern.</span><span class="sxs-lookup"><span data-stu-id="26043-254">To get a constant stream of samples, use the **Continuous** parameter.</span></span>

<span data-ttu-id="26043-255">Om parametern **MaxSamples** inte anges `Get-Counter` hämtas bara ett sampel för varje angiven räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-255">If the **MaxSamples** parameter isn't specified, `Get-Counter` only gets one sample for each specified counter.</span></span>

<span data-ttu-id="26043-256">Om du vill samla in en stor data uppsättning kör du `Get-Counter` som ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="26043-256">To collect a large data set, run `Get-Counter` as a PowerShell background job.</span></span> <span data-ttu-id="26043-257">Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="26043-257">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

```yaml
Type: System.Int64
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26043-258">-SampleInterval</span><span class="sxs-lookup"><span data-stu-id="26043-258">-SampleInterval</span></span>

<span data-ttu-id="26043-259">Anger antalet sekunder mellan exempel för varje angiven prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-259">Specifies the number of seconds between samples for each specified performance counter.</span></span> <span data-ttu-id="26043-260">Om parametern **SampleInterval** inte anges `Get-Counter` används ett intervall på en sekund.</span><span class="sxs-lookup"><span data-stu-id="26043-260">If the **SampleInterval** parameter isn't specified, `Get-Counter` uses a one-second interval.</span></span>

```yaml
Type: System.Int32
Parameter Sets: GetCounterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="26043-261">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26043-261">CommonParameters</span></span>

<span data-ttu-id="26043-262">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="26043-262">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26043-263">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="26043-263">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26043-264">INDATA</span><span class="sxs-lookup"><span data-stu-id="26043-264">INPUTS</span></span>

### <span data-ttu-id="26043-265">System.String[]</span><span class="sxs-lookup"><span data-stu-id="26043-265">System.String[]</span></span>

<span data-ttu-id="26043-266">`Get-Counter` accepterar pipeline-inflöden för räknar Sök vägar och räknar uppsättnings namn.</span><span class="sxs-lookup"><span data-stu-id="26043-266">`Get-Counter` accepts pipeline input for counter paths and counter set names.</span></span>

## <span data-ttu-id="26043-267">UTDATA</span><span class="sxs-lookup"><span data-stu-id="26043-267">OUTPUTS</span></span>

### <span data-ttu-id="26043-268">Microsoft. PowerShell. commands. GetCounter. CounterSet, Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet, Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSample</span><span class="sxs-lookup"><span data-stu-id="26043-268">Microsoft.PowerShell.Commands.GetCounter.CounterSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet, Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample</span></span>

<span data-ttu-id="26043-269">Om du vill visa ett objekts egenskaper skickar du ut pipelinen till `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="26043-269">To view an object's properties, send the output down the pipeline to `Get-Member`.</span></span> <span data-ttu-id="26043-270">De objekt typer som ska matas ut är följande:</span><span class="sxs-lookup"><span data-stu-id="26043-270">The object types that are output are as follows:</span></span>

<span data-ttu-id="26043-271">**ListSet** -parameter: **Microsoft. PowerShell. commands. GetCounter. CounterSet**</span><span class="sxs-lookup"><span data-stu-id="26043-271">**ListSet** parameter: **Microsoft.PowerShell.Commands.GetCounter.CounterSet**</span></span>

<span data-ttu-id="26043-272">**Räknar** parameter: **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSampleSet**</span><span class="sxs-lookup"><span data-stu-id="26043-272">**Counter** parameter: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSampleSet**</span></span>

<span data-ttu-id="26043-273">**CounterSamples** -egenskap: **Microsoft. PowerShell. commands. GetCounter. PerformanceCounterSample**</span><span class="sxs-lookup"><span data-stu-id="26043-273">**CounterSamples** property: **Microsoft.PowerShell.Commands.GetCounter.PerformanceCounterSample**</span></span>

## <span data-ttu-id="26043-274">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="26043-274">NOTES</span></span>

<span data-ttu-id="26043-275">Om inga parametrar har angetts `Get-Counter` hämtas ett exempel för varje angiven prestanda räknare.</span><span class="sxs-lookup"><span data-stu-id="26043-275">If no parameters are specified, `Get-Counter` gets one sample for each specified performance counter.</span></span> <span data-ttu-id="26043-276">Använd parametrarna **MaxSamples** och **kontinuerlig** för att få fler exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-276">Use the **MaxSamples** and **Continuous** parameters to get more samples.</span></span>

<span data-ttu-id="26043-277">`Get-Counter` använder ett intervall på en sekund mellan exempel.</span><span class="sxs-lookup"><span data-stu-id="26043-277">`Get-Counter` uses a one-second interval between samples.</span></span> <span data-ttu-id="26043-278">Använd parametern **SampleInterval** för att öka intervallet.</span><span class="sxs-lookup"><span data-stu-id="26043-278">Use the **SampleInterval** parameter to increase the interval.</span></span>

<span data-ttu-id="26043-279">Värdena för **MaxSamples** och **SampleInterval** gäller för alla räknare på varje dator i kommandot.</span><span class="sxs-lookup"><span data-stu-id="26043-279">The **MaxSamples** and **SampleInterval** values apply to all the counters on each computer in the command.</span></span> <span data-ttu-id="26043-280">Ange olika värden för olika räknare genom att ange separata `Get-Counter` kommandon.</span><span class="sxs-lookup"><span data-stu-id="26043-280">To set different values for different counters, enter separate `Get-Counter` commands.</span></span>

<span data-ttu-id="26043-281">När du använder parametern **ListSet** i PowerShell 7 `Get-Counter` kan inte hämta egenskapen **Description** för räknar uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="26043-281">In PowerShell 7, when using the **ListSet** parameter, `Get-Counter` can't retrieve the **Description** property of the counter set.</span></span> <span data-ttu-id="26043-282">**Beskrivningen** anges till `$null` .</span><span class="sxs-lookup"><span data-stu-id="26043-282">The **Description** is set to `$null`.</span></span>

## <span data-ttu-id="26043-283">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="26043-283">RELATED LINKS</span></span>

[<span data-ttu-id="26043-284">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="26043-284">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="26043-285">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="26043-285">about_Jobs</span></span>](../Microsoft.PowerShell.Core/About/about_Jobs.md)

[<span data-ttu-id="26043-286">Format-List</span><span class="sxs-lookup"><span data-stu-id="26043-286">Format-List</span></span>](../Microsoft.PowerShell.Utility/Format-List.md)

[<span data-ttu-id="26043-287">Format-Table</span><span class="sxs-lookup"><span data-stu-id="26043-287">Format-Table</span></span>](../Microsoft.PowerShell.Utility/Format-Table.md)

[<span data-ttu-id="26043-288">Hämta medlem</span><span class="sxs-lookup"><span data-stu-id="26043-288">Get-Member</span></span>](../Microsoft.PowerShell.Utility/Get-Member.md)

[<span data-ttu-id="26043-289">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="26043-289">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)

[<span data-ttu-id="26043-290">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="26043-290">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="26043-291">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="26043-291">Where-Object</span></span>](..//Microsoft.PowerShell.Core/Where-Object.md)

